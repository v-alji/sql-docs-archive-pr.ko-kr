---
title: 지연 업데이트 충돌 감지 및 해결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- viewing queued updating conflicts
- conflict resolution [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
- articles [SQL Server replication], conflict resolution
ms.assetid: 084ac587-25e7-4bd0-a385-556bbe07d02f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c4608347ab119e25caa45b0ee4a592a953e34a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661001"
---
# <a name="queued-updating-conflict-detection-and-resolution"></a><span data-ttu-id="222e8-102">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="222e8-102">Queued Updating Conflict Detection and Resolution</span></span>
  <span data-ttu-id="222e8-103">지연 업데이트 구독으로 여러 위치에서 같은 데이터를 수정할 수 있기 때문에 데이터를 게시자에 동기화할 때 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-103">Because queued updating subscriptions allow modifications to the same data at multiple locations, there may be conflicts when data is synchronized at the Publisher.</span></span> <span data-ttu-id="222e8-104">복제는 변경 내용이 게시자와 동기화될 때 충돌을 감지하고 게시를 만들 때 선택한 해결 정책을 사용하여 이러한 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-104">Replication detects any conflicts when changes are synchronized with the Publisher and resolves those conflicts using the resolution policy you selected when creating the publication.</span></span> <span data-ttu-id="222e8-105">다음과 같은 두 가지 충돌이 일어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-105">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="222e8-106">업데이트 및 삽입 충돌.</span><span class="sxs-lookup"><span data-stu-id="222e8-106">Update and insert conflicts.</span></span> <span data-ttu-id="222e8-107">이러한 충돌은 같은 데이터를 두 위치에서 변경할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-107">This conflict happens when the same data is changed at two locations.</span></span> <span data-ttu-id="222e8-108">이 경우 한 가지 변경 내용만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-108">One change wins, and the other one loses.</span></span>  
  
-   <span data-ttu-id="222e8-109">삭제 충돌.</span><span class="sxs-lookup"><span data-stu-id="222e8-109">Delete conflicts.</span></span> <span data-ttu-id="222e8-110">삭제 충돌은 한 위치에서 행을 삭제하고 다른 위치에서 같은 행을 변경할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-110">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="222e8-111">충돌 감지와 해결에는 많은 시간과 리소스가 필요하기 때문에 각 구독자가 서로 다른 데이터 하위 집합을 수정하도록 데이터 파티션을 만들어 애플리케이션에서 충돌을 최소화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-111">Conflict detection and resolution can be a time-consuming and resource-intensive process; therefore, it is best to minimize conflicts in the application by creating data partitions so that different Subscribers modify different subsets of data.</span></span>  
  
## <a name="detecting-conflicts"></a><span data-ttu-id="222e8-112">충돌 감지</span><span class="sxs-lookup"><span data-stu-id="222e8-112">Detecting Conflicts</span></span>  
 <span data-ttu-id="222e8-113">게시를 만들고 지연 업데이트를 설정하면 복제는 기본 테이블에 기본값이 **newid()** 인**uniqueidentifier**열( **msrepl_tran_version** )을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-113">When creating a publication and enabling queued updating, replication adds a **uniqueidentifier** column (**msrepl_tran_version**) with the default of **newid()** to the underlying table.</span></span> <span data-ttu-id="222e8-114">게시자 또는 구독자에서 게시된 데이터가 변경되면 행은 새로운 GUID(Globally Unique Identifier)를 받아 새로운 행 버전이 있음을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-114">When published data is changed at either the Publisher or the Subscriber, the row receives a new globally unique identifier (GUID) to indicate that a new row version exists.</span></span> <span data-ttu-id="222e8-115">큐 판독기 에이전트는 충돌이 있는지 확인하기 위해 동기화 중 이 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-115">The Queue Reader Agent uses this column during synchronization to determine if a conflict exists.</span></span>  
  
 <span data-ttu-id="222e8-116">큐에서 트랜잭션은 이전 행 버전 값과 새로운 행 버전 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-116">A transaction in a queue maintains the old and new row version values.</span></span> <span data-ttu-id="222e8-117">게시자에서 트랜잭션이 적용되면 트랜잭션에서의 GUID와 게시에 있는 GUID가 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-117">When the transaction is applied at the Publisher, the GUIDs from the transaction and the GUID in the publication are compared.</span></span> <span data-ttu-id="222e8-118">트랜잭션에 저장된 이전 GUID가 게시에 있는 GUID와 일치하면 게시는 업데이트되고 구독자가 생성한 새 GUID를 행에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-118">If the old GUID stored in the transaction matches the GUID in the publication, the publication is updated and the row is assigned the new GUID that was generated by the Subscriber.</span></span> <span data-ttu-id="222e8-119">트랜잭션에서 GUID와 함께 게시를 업데이트하면 게시 및 트랜잭션에 일치하는 행 버전을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-119">By updating the publication with the GUID from the transaction, you have matching row versions in the publication and in the transaction.</span></span>  
  
 <span data-ttu-id="222e8-120">트랜잭션에 저장된 이전 GUID가 게시에 있는 GUID와 일치하지 않으면 충돌이 감지됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-120">If the old GUID stored in the transaction does not match the GUID in the publication, a conflict is detected.</span></span> <span data-ttu-id="222e8-121">게시에 있는 새 GUID는 두 개의 다른 행 버전이 있음을 표시하는데 이 중 하나는 구독자가 제출하는 트랜잭션에 있고 최근의 다른 하나는 게시자에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-121">The new GUID in the publication indicates that two different row versions exist: one in the transaction being submitted by the Subscriber and a newer one that exists on the Publisher.</span></span> <span data-ttu-id="222e8-122">이 경우 구독자 트랜잭션을 동기화하기 전 다른 구독자 또는 게시자가 게시에서 같은 행을 업데이트한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-122">In this case, another Subscriber or the Publisher updated the same row in the publication before this Subscriber transaction was synchronized.</span></span>  
  
 <span data-ttu-id="222e8-123">병합 복제와 달리 GUID는 행 자체를 식별하는 데 사용되지 않고 행이 변경되었는지를 검사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-123">Unlike merge replication, the use of a GUID column is not used to identify the row itself, but is used to check if the row has changed.</span></span>  
  
## <a name="resolving-conflicts"></a><span data-ttu-id="222e8-124">충돌 해결</span><span class="sxs-lookup"><span data-stu-id="222e8-124">Resolving Conflicts</span></span>  
 <span data-ttu-id="222e8-125">지연 업데이트를 사용하여 게시를 만드는 경우 충돌이 감지되면 사용할 충돌 해결 프로그램을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-125">When you create a publication using queued updating, you select a conflict resolver to be used if any conflicts are detected.</span></span> <span data-ttu-id="222e8-126">충돌 해결 프로그램은 큐 판독기 에이전트에서 동기화 중에 발생한 동일한 행의 여러 버전을 처리하는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-126">The conflict resolver governs how the Queue Reader Agent handles different versions of the same row encountered during synchronization.</span></span> <span data-ttu-id="222e8-127">게시에 대한 구독이 없을 경우에 한해서 게시를 만든 후 충돌 해결 정책을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-127">You can change the conflict resolution policy after the publication is created as long as there are no subscriptions to the publication.</span></span> <span data-ttu-id="222e8-128">다음의 충돌 해결 프로그램을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-128">The conflict resolver choices are the following:</span></span>  
  
-   <span data-ttu-id="222e8-129">게시자 내용 적용(기본값)</span><span class="sxs-lookup"><span data-stu-id="222e8-129">Publisher wins (the default)</span></span>  
  
-   <span data-ttu-id="222e8-130">게시자 내용을 적용하고 구독을 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="222e8-130">Publisher wins and the subscription is reinitialized</span></span>  
  
-   <span data-ttu-id="222e8-131">구독자 내용 적용</span><span class="sxs-lookup"><span data-stu-id="222e8-131">Subscriber wins</span></span>  
  
 <span data-ttu-id="222e8-132">충돌을 기록하고 충돌 뷰어를 사용해서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-132">Conflicts are recorded and can be viewed using the Conflict Viewer.</span></span>  
  
 <span data-ttu-id="222e8-133">**지연 업데이트 충돌 해결 정책을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="222e8-133">**To set the queued updating conflict resolution policy**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="222e8-134">: [지연 업데이트 충돌 해결 옵션 설정&#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="222e8-134">: [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="222e8-135">복제 Transact-SQL 프로그래밍: [트랜잭션 게시에 대해 업데이트할 수 있는 구독 설정](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span><span class="sxs-lookup"><span data-stu-id="222e8-135">Replication Transact-SQL programming: [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="222e8-136">**데이터 충돌을 보려면**</span><span class="sxs-lookup"><span data-stu-id="222e8-136">**To view data conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="222e8-137">: [트랜잭션 게시의 데이터 충돌 확인&#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="222e8-137">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
### <a name="publisher-wins"></a><span data-ttu-id="222e8-138">게시자 내용 적용</span><span class="sxs-lookup"><span data-stu-id="222e8-138">Publisher Wins</span></span>  
 <span data-ttu-id="222e8-139">충돌 해결 시 게시자 내용이 적용되도록 설정하면 게시자에 있는 데이터를 기준으로 트랜잭션 일관성을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-139">When the conflict resolution is set to the Publisher wins, transactional consistency is maintained based on the data at the Publisher.</span></span> <span data-ttu-id="222e8-140">충돌 트랜잭션은 트랜잭션을 처음에 초기화한 구독자로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-140">The conflicting transaction is rolled back at the Subscriber that initiated it.</span></span>  
  
 <span data-ttu-id="222e8-141">큐 판독기 에이전트가 충돌을 감지하고 보상 명령이 생성되며 배포 데이터베이스에서 게시함으로써 생성된 보상 명령을 구독자로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-141">The Queue Reader Agent detects a conflict and compensating commands are generated and propagated to the Subscriber by posting them in the distribution database.</span></span> <span data-ttu-id="222e8-142">그 다음 배포 에이전트는 보상 명령을 충돌 트랜잭션이 시작된 구독자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-142">The Distribution Agent then applies the compensating commands to the Subscriber that originated the conflicting transaction.</span></span> <span data-ttu-id="222e8-143">보정 동작은 게시자에 있는 행과 일치하도록 구독자에서 행을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-143">The compensating actions update the rows on the Subscriber to match the rows on the Publisher.</span></span>  
  
 <span data-ttu-id="222e8-144">보상 명령이 적용될 때까지 실행하여 구독자에서 롤백할 트랜잭션 결과를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-144">Until the compensating commands are applied, it is possible to read the results of a transaction that will eventually be rolled back at the Subscriber.</span></span> <span data-ttu-id="222e8-145">이는 커밋되지 않은 데이터 읽기(커밋되지 않은 격리 수준 읽기)에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-145">This is equivalent to a dirty read (read uncommitted isolation level).</span></span> <span data-ttu-id="222e8-146">발생할 수 있는 후속 종속 트랜잭션에 대해서는 보상이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-146">There is no compensation for the subsequent dependent transactions that can occur.</span></span> <span data-ttu-id="222e8-147">그러나 트랜잭션 경계는 유지되고 트랜잭션의 모든 동작은 커밋되거나 충돌이 있을 경우 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-147">However, transaction boundaries are honored and all the actions within a transaction are either committed, or in the case of a conflict, rolled back.</span></span>  
  
### <a name="publisher-wins-and-the-subscription-is-reinitialized"></a><span data-ttu-id="222e8-148">게시자 내용을 적용하고 구독을 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="222e8-148">Publisher Wins and the Subscription Is Reinitialized</span></span>  
 <span data-ttu-id="222e8-149">구독자를 다시 초기화하여 충돌을 해결하면 구독자에서 엄격한 트랜잭션 일관성이 유지되지만 게시에 많은 양의 데이터가 포함되어 있을 경우 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-149">Reinitializing the Subscriber to resolve conflicts maintains strict transactional consistency at the Subscriber, but it can be time consuming if the publication contains large amounts of data.</span></span>  
  
 <span data-ttu-id="222e8-150">큐 판독기 에이전트가 충돌을 감지하면 큐에 남은 모든 트랜잭션(충돌한 트랜잭션을 포함)은 거부되고 구독자는 다시 초기화하도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-150">When the Queue Reader Agent detects a conflict, all remaining transactions in the queue (including the transaction in conflict) are rejected, and the Subscriber is marked for reinitialization.</span></span> <span data-ttu-id="222e8-151">배포 에이전트는 게시에 대해 생성된 다음 스냅샷을 구독자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-151">The next snapshot generated for the publication is applied by the Distribution Agent to the Subscriber.</span></span>  
  
### <a name="subscriber-wins"></a><span data-ttu-id="222e8-152">구독자 내용 적용</span><span class="sxs-lookup"><span data-stu-id="222e8-152">Subscriber Wins</span></span>  
 <span data-ttu-id="222e8-153">구독자 변경 내용 적용 정책에서 충돌 감지는 게시자 변경 내용 적용 항목을 업데이트하는 마지막 구독자 트랜잭션을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-153">Conflict detection under the Subscriber wins policy means the last Subscriber transaction to update the Publisher wins.</span></span> <span data-ttu-id="222e8-154">이 경우 충돌이 감지되면 구독자가 보낸 트랜잭션이 계속 사용되고 게시자가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-154">In this case, when a conflict is detected, the transaction sent by the Subscriber is still used and the Publisher is updated.</span></span> <span data-ttu-id="222e8-155">이 정책은 이러한 변경 내용이 데이터 무결성을 손상하지 않은 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="222e8-155">This policy is suitable for applications where such changes do not compromise data integrity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222e8-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="222e8-156">See Also</span></span>  
 [<span data-ttu-id="222e8-157">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="222e8-157">Updatable Subscriptions for Transactional Replication</span></span>](updatable-subscriptions-for-transactional-replication.md)  
  
  
