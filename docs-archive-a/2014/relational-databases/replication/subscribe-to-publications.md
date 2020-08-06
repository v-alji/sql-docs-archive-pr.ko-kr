---
title: 게시 구독 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c565aae26c6d549eb67043168797d5fb059c8e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646306"
---
# <a name="subscribe-to-publications"></a><span data-ttu-id="b4a01-102">게시 구독</span><span class="sxs-lookup"><span data-stu-id="b4a01-102">Subscribe to Publications</span></span>
  <span data-ttu-id="b4a01-103">구독은 게시에 있는 데이터 및 데이터베이스 개체 복사본에 대한 요청입니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-103">A subscription is a request for a copy of the data and database objects in a publication.</span></span> <span data-ttu-id="b4a01-104">구독은 어떤 게시를 언제 어디서 받을 것인지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-104">A subscription defines which publication will be received, and where and when it will be received.</span></span> <span data-ttu-id="b4a01-105">구독을 계획하는 경우 에이전트 처리를 수행할 위치를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-105">When planning for subscriptions, consider where you want agent processing to occur.</span></span> <span data-ttu-id="b4a01-106">선택한 구독 유형에 따라 에이전트가 실행되는 위치가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-106">The type of subscription you choose controls where the agent runs.</span></span> <span data-ttu-id="b4a01-107">밀어넣기 구독을 사용하면 병합 에이전트 또는 배포 에이전트가 배포자에서 실행되고 끌어오기 구독을 사용하면 에이전트가 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-107">With a push subscription, the Merge Agent or Distribution Agent runs at the Distributor, whereas with a pull subscription, agents run at the Subscribers.</span></span> <span data-ttu-id="b4a01-108">구독을 만든 후에는 해당 유형을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-108">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
|<span data-ttu-id="b4a01-109">Subscription</span><span class="sxs-lookup"><span data-stu-id="b4a01-109">Subscription</span></span>|<span data-ttu-id="b4a01-110">특징</span><span class="sxs-lookup"><span data-stu-id="b4a01-110">Characteristics</span></span>|<span data-ttu-id="b4a01-111">사용 시기</span><span class="sxs-lookup"><span data-stu-id="b4a01-111">Use When</span></span>|  
|------------------|---------------------|--------------|  
|<span data-ttu-id="b4a01-112">밀어넣기 구독</span><span class="sxs-lookup"><span data-stu-id="b4a01-112">Push Subscription</span></span>|<span data-ttu-id="b4a01-113">밀어넣기 구독의 경우 게시자는 구독자의 요청 없이 변경 내용을 구독자로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-113">With a push subscription, the Publisher propagates changes to a Subscriber without a request from the Subscriber.</span></span> <span data-ttu-id="b4a01-114">변경 내용은 요청 시나 계속적으로 또는 일정에 따라 구독자로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-114">Changes can be pushed to Subscribers on demand, continuously, or on a scheduled basis.</span></span> <span data-ttu-id="b4a01-115">배포 에이전트 또는 병합 에이전트는 배포자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-115">The Distribution Agent or Merge Agent runs at the Distributor.</span></span>|<span data-ttu-id="b4a01-116">데이터가 일반적으로 계속 또는 정기적으로 자주 동기화되는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-116">Data will typically be synchronized continuously or on a frequently recurring schedule.</span></span><br /><br /> <span data-ttu-id="b4a01-117">게시가 실시간에 가까운 데이터 이동을 요구하는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-117">Publications require near real-time movement of data.</span></span><br /><br /> <span data-ttu-id="b4a01-118">배포자에서 프로세서 오버헤드가 증가해도 성능에 영향을 주지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-118">The higher processor overhead at the Distributor does not affect performance.</span></span><br /><br /> <span data-ttu-id="b4a01-119">스냅샷과 트랜잭션 복제에 가장 많이 사용되는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-119">Most often used with snapshot and transactional replication.</span></span>|  
|<span data-ttu-id="b4a01-120">끌어오기 구독</span><span class="sxs-lookup"><span data-stu-id="b4a01-120">Pull Subscription</span></span>|<span data-ttu-id="b4a01-121">끌어오기 구독의 경우 구독자는 게시자의 변경 내용을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-121">With a pull subscription, the Subscriber requests changes made at the Publisher.</span></span> <span data-ttu-id="b4a01-122">끌어오기 구독을 사용하면 구독자에 있는 사용자가 데이터 변경 내용의 동기화 시기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-122">Pull subscriptions allow the user at the Subscriber to determine when the data changes are synchronized.</span></span> <span data-ttu-id="b4a01-123">배포 에이전트 또는 병합 에이전트는 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-123">The Distribution Agent or the Merge Agent runs at the Subscriber.</span></span>|<span data-ttu-id="b4a01-124">데이터는 일반적으로 계속 동기화되지 않고 요청 시 또는 일정에 따라 동기화되는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-124">Data will typically be synchronized on demand or on a schedule rather than continuously.</span></span><br /><br /> <span data-ttu-id="b4a01-125">게시에 많은 구독자가 있으며 배포자에서 모든 에이전트를 실행하는 데 너무 많은 리소스가 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-125">The publication has a large number of Subscribers, and/or it would be too resource-intensive to run all the agents at the Distributor.</span></span><br /><br /> <span data-ttu-id="b4a01-126">구독자가 자치적이거나, 연결이 끊어졌거나 이동 중인 경우.</span><span class="sxs-lookup"><span data-stu-id="b4a01-126">Subscribers are autonomous, disconnected, and/or mobile.</span></span> <span data-ttu-id="b4a01-127">구독자는 언제 연결하여 변경 내용을 동기화할 것인지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-127">Subscribers will determine when they will connect and synchronize changes.</span></span><br /><br /> <span data-ttu-id="b4a01-128">병합 복제에 가장 많이 사용되는 경우</span><span class="sxs-lookup"><span data-stu-id="b4a01-128">Most often used with merge replication.</span></span>|  
  
## <a name="merge-replication-subscription-types"></a><span data-ttu-id="b4a01-129">병합 복제 구독 유형</span><span class="sxs-lookup"><span data-stu-id="b4a01-129">Merge Replication Subscription Types</span></span>  
 <span data-ttu-id="b4a01-130">모든 복제 유형은 밀어넣기 및 끌어오기 구독을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-130">All replication types allow push and pull subscriptions.</span></span> <span data-ttu-id="b4a01-131">병합 복제는 클라이언트 구독과 서버 구독이라는 두 개의 추가 용어를 사용하여 구독을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-131">Merge replication uses two additional terms to distinguish subscriptions: client subscriptions and server subscriptions.</span></span> <span data-ttu-id="b4a01-132">클라이언트 구독 유형과 서버 구독 유형은 모두 밀어넣기 및 끌어오기 구독에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-132">Both client and server subscription types can be used with push and pull subscriptions.</span></span> <span data-ttu-id="b4a01-133">클라이언트 구독은 대부분의 구독자에 적합한 반면 서버 구독은 일반적으로 데이터를 다른 구독자에게 다시 게시하는 구독자에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-133">Client subscriptions are appropriate for most Subscribers, whereas server subscriptions are typically used for Subscribers that republish data to other Subscribers.</span></span> <span data-ttu-id="b4a01-134">선택한 구독 유형은 충돌 해결에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-134">Subscription choice also affects conflict resolution.</span></span>  
  
## <a name="non-sql-server-subscribers"></a><span data-ttu-id="b4a01-135">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="b4a01-135">Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="b4a01-136">Oracle 및 IBM DB2는 밀어넣기 구독을 사용하여 스냅샷 및 트랜잭션 게시를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-136">Oracle and IBM DB2 can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="b4a01-137">자세한 내용은 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4a01-137">For more information, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
## <a name="creating-subscriptions"></a><span data-ttu-id="b4a01-138">구독 만들기</span><span class="sxs-lookup"><span data-stu-id="b4a01-138">Creating Subscriptions</span></span>  
 <span data-ttu-id="b4a01-139">구독을 만들려면 다음 정보를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4a01-139">To create a subscription, you supply the following information:</span></span>  
  
-   <span data-ttu-id="b4a01-140">게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-140">The name of the publication.</span></span>  
  
-   <span data-ttu-id="b4a01-141">구독자 및 구독 데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="b4a01-141">The name of the Subscriber and the subscription database.</span></span>  
  
-   <span data-ttu-id="b4a01-142">배포 에이전트 또는 병합 에이전트가 배포자 또는 구독자에서 실행되는지의 여부</span><span class="sxs-lookup"><span data-stu-id="b4a01-142">Whether the Distribution Agent or Merge Agent runs at the Distributor or at the Subscriber.</span></span>  
  
-   <span data-ttu-id="b4a01-143">배포 에이전트 또는 병합 에이전트가 계속 실행되는지, 일정에 따라 또는 요청 시에만 실행되는지의 여부</span><span class="sxs-lookup"><span data-stu-id="b4a01-143">Whether the Distribution Agent or Merge Agent runs continuously, on a scheduled basis, or on demand only.</span></span>  
  
-   <span data-ttu-id="b4a01-144">스냅샷 에이전트에서 구독에 대한 초기 스냅샷을 만들어야 하는지, 배포 에이전트 또는 병합 에이전트가 해당 스냅샷을 구독자에서 적용해야 하는지의 여부</span><span class="sxs-lookup"><span data-stu-id="b4a01-144">Whether the Snapshot Agent should create an initial snapshot for the subscription and whether the Distribution Agent or Merge Agent should apply that snapshot at the Subscriber.</span></span>  
  
-   <span data-ttu-id="b4a01-145">배포 에이전트 또는 병합 에이전트가 실행될 계정</span><span class="sxs-lookup"><span data-stu-id="b4a01-145">Accounts under which the Distribution Agent or Merge Agent will run.</span></span>  
  
-   <span data-ttu-id="b4a01-146">병합 복제의 경우 구독 유형은 서버 및 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-146">For merge replication, the type of subscription: server or client.</span></span>  
  
 <span data-ttu-id="b4a01-147">**밀어넣기 구독을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-147">**To create a push subscription**</span></span>  
  
 [<span data-ttu-id="b4a01-148">밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="b4a01-148">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
 <span data-ttu-id="b4a01-149">**밀어넣기 구독 속성을 보거나 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-149">**To view or modify push subscription properties**</span></span>  
  
 [<span data-ttu-id="b4a01-150">밀어넣기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="b4a01-150">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)  
  
 <span data-ttu-id="b4a01-151">**밀어넣기 구독을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-151">**To delete a push subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="b4a01-152">: [밀어넣기 구독 삭제](delete-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="b4a01-152">: [Delete a Push Subscription](delete-a-push-subscription.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4a01-153">구독을 삭제해도 게시된 개체가 구독자에서 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4a01-153">Deleting a subscription does not remove published objects from the Subscriber.</span></span>  
  
 <span data-ttu-id="b4a01-154">**끌어오기 구독을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-154">**To create a pull subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="b4a01-155">: [끌어오기 구독 만들기](create-a-pull-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="b4a01-155">: [Create a Pull Subscription](create-a-pull-subscription.md)</span></span>  
  
 <span data-ttu-id="b4a01-156">**끌어오기 구독 속성을 보거나 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-156">**To view or modify pull subscription properties**</span></span>  
  
 [<span data-ttu-id="b4a01-157">끌어오기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="b4a01-157">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)  
  
 <span data-ttu-id="b4a01-158">**끌어오기 구독을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="b4a01-158">**To delete a pull subscription**</span></span>  
  
 [<span data-ttu-id="b4a01-159">끌어오기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="b4a01-159">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4a01-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4a01-160">See Also</span></span>  
 <span data-ttu-id="b4a01-161">[구독자 보안 설정](security/secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="b4a01-161">[Secure the Subscriber](security/secure-the-subscriber.md) </span></span>  
 [<span data-ttu-id="b4a01-162">구독 만료 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="b4a01-162">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
