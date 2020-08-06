---
title: 데이터 동기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c92cc4d1ae8e836f169a731ecf3c37c81f3dbf10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732551"
---
# <a name="synchronize-data"></a><span data-ttu-id="9ceb4-102">데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="9ceb4-102">Synchronize Data</span></span>
  <span data-ttu-id="9ceb4-103">데이터 동기화란 초기 스냅샷이 구독자에 적용된 후 게시자와 구독자 간에 데이터 및 스키마 변경 내용이 전파되는 프로세스를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-103">Synchronizing data refers to the process of data and schema changes being propagated between the Publisher and Subscribers after the initial snapshot has been applied at the Subscriber.</span></span> <span data-ttu-id="9ceb4-104">동기화는 다음과 같은 방식으로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-104">Synchronization can occur:</span></span>  
  
-   <span data-ttu-id="9ceb4-105">계속 - 트랜잭션 복제에 일반적임</span><span class="sxs-lookup"><span data-stu-id="9ceb4-105">Continuously, which is typical for transactional replication.</span></span>  
  
-   <span data-ttu-id="9ceb4-106">요청 시 - 병합 복제에 일반적임</span><span class="sxs-lookup"><span data-stu-id="9ceb4-106">On demand, which is typical for merge replication.</span></span>  
  
-   <span data-ttu-id="9ceb4-107">일정대로 - 스냅샷 복제에 일반적임</span><span class="sxs-lookup"><span data-stu-id="9ceb4-107">On a schedule, which is typical for snapshot replication.</span></span>  
  
 <span data-ttu-id="9ceb4-108">구독이 동기화되면 사용하는 복제 유형에 따라 다른 프로세스가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-108">When a subscription is synchronized, different processes occur based on the type of replication you are using:</span></span>  
  
-   <span data-ttu-id="9ceb4-109">스냅샷 복제.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-109">Snapshot replication.</span></span> <span data-ttu-id="9ceb4-110">동기화란 배포 에이전트가 구독 데이터베이스의 스키마와 데이터가 게시 데이터베이스와 일치하도록 구독자에 스냅샷을 다시 적용하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-110">Synchronization means that the Distribution Agent reapplies the snapshot at the Subscriber so that schema and data at the subscription database is consistent with the publication database.</span></span>  
  
     <span data-ttu-id="9ceb4-111">게시자에서 데이터와 스키마를 수정한 경우 수정 내용을 구독자에 전파하려면 새 스냅샷을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-111">If modifications to data or schema have been made at the Publisher, a new snapshot must be generated in order to propagate modifications to the Subscriber.</span></span>  
  
-   <span data-ttu-id="9ceb4-112">트랜잭션 복제.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-112">Transactional replication.</span></span> <span data-ttu-id="9ceb4-113">동기화란 배포 에이전트가 업데이트, 삽입, 삭제 및 기타 변경 내용을 배포 데이터베이스에서 구독자로 전송하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-113">Synchronization means that the Distribution Agent transfers updates, inserts, deletes, and any other changes from the distribution database to the Subscriber.</span></span>  
  
-   <span data-ttu-id="9ceb4-114">병합 복제.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-114">Merge replication.</span></span> <span data-ttu-id="9ceb4-115">동기화란 병합 에이전트가 변경 내용을 구독자에서 게시자로 업로드한 다음 게시자에서 구독자로 변경 내용을 다운로드하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-115">Synchronization means that the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="9ceb4-116">충돌이 발생할 경우 이를 감지하여 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-116">Conflicts, if any, are detected and resolved.</span></span> <span data-ttu-id="9ceb4-117">데이터는 일치되고 게시자와 모든 구독자는 결국 같은 데이터 값을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-117">Data is converged, and the Publisher and all Subscribers eventually end up with the same data values.</span></span> <span data-ttu-id="9ceb4-118">충돌이 감지되고 해결될 때 일부 사용자가 커밋한 작업은 사용자가 정의한 정책에 따라 충돌을 해결하도록 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-118">If conflicts were detected and resolved, work that was committed by some of the users is changed to resolve the conflict according to policies you define.</span></span>  
  
 <span data-ttu-id="9ceb4-119">스냅샷 게시는 동기화가 발생할 때마다 구독자에서 스키마를 완전히 새로 고치므로 모든 스키마 변경 내용이 구독자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-119">Snapshot publications completely refresh the schema at the Subscriber every time synchronization occurs, so all schema changes are applied to the Subscriber.</span></span> <span data-ttu-id="9ceb4-120">트랜잭션 복제 및 병합 복제 또한 가장 일반적인 스키마 변경을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-120">Transactional replication and merge replication also support the most common schema changes.</span></span> <span data-ttu-id="9ceb4-121">자세한 내용은 [게시 데이터베이스의 스키마 변경](publish/make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-121">For more information, see [Make Schema Changes on Publication Databases](publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="9ceb4-122">밀어넣기 구독을 동기화하려면 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-122">To synchronize a push subscription, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="9ceb4-123">끌어오기 구독을 동기화하려면 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-123">To synchronize a pull subscription, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="9ceb4-124">동기화 일정을 설정하려면 [Specify Synchronization Schedules](specify-synchronization-schedules.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-124">To set synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="9ceb4-125">**동기화 충돌을 보고 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="9ceb4-125">**To view and resolve synchronization conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="9ceb4-126">: [병합 게시에 대한 데이터 충돌 보기 및 해결&#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="9ceb4-126">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="9ceb4-127">: [트랜잭션 게시의 데이터 충돌 확인&#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="9ceb4-127">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
## <a name="executing-code-during-synchronization"></a><span data-ttu-id="9ceb4-128">동기화 중 코드 실행</span><span class="sxs-lookup"><span data-stu-id="9ceb4-128">Executing Code During Synchronization</span></span>  
 <span data-ttu-id="9ceb4-129">복제는 동기화하는 동안 코드를 실행하는 두 가지 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-129">Replication supports two methods of executing code during synchronization</span></span>  
  
-   <span data-ttu-id="9ceb4-130">요청 시 스크립트 실행은 트랜잭션 복제와 병합 복제에 대해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-130">On demand script execution is supported for transactional replication and merge replication.</span></span> <span data-ttu-id="9ceb4-131">요청 시 스크립트 실행을 사용하면 동기화하는 동안 SQL 스크립트가 실행되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-131">Using on demand script execution you can specify a SQL script to run during synchronization.</span></span> <span data-ttu-id="9ceb4-132">스크립트는 구독자에 복사된 다음 동기화 프로세스 시작 시 **sqlcmd** 를 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-132">The script is copied to the Subscriber and executed using **sqlcmd** at the beginning of the synchronization process.</span></span> <span data-ttu-id="9ceb4-133">복제된 변경 내용이 구독자에 적용될 때 스크립트를 통해 이러한 변경 내용에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-133">The script does not have access to the replicated changes as they are applied to the Subscriber.</span></span> <span data-ttu-id="9ceb4-134">자세한 내용은 [동기화 중 스크립트 실행&#40;복제 Transact-SQL 프로그래밍&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-134">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="9ceb4-135">비즈니스 논리 처리기는 병합 복제에 대해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-135">Business logic handlers are supported for merge replication.</span></span> <span data-ttu-id="9ceb4-136">비즈니스 논리 처리기 프레임워크를 사용하면 병합 동기화 과정 동안 호출되는 관리 코드 어셈블리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-136">Using the business logic handler framework you can write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="9ceb4-137">이 어셈블리에는 동기화 중 데이터 변경, 충돌, 오류 등의 여러 상황에 응답할 수 있는 비즈니스 논리가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-137">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="9ceb4-138">자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](merge/execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ceb4-138">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ceb4-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ceb4-139">See Also</span></span>  
 [<span data-ttu-id="9ceb4-140">병합 복제 충돌 감지 및 해결</span><span class="sxs-lookup"><span data-stu-id="9ceb4-140">Detect and Resolve Merge Replication Conflicts</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
