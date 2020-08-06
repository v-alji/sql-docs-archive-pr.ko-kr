---
title: 구독 다시 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f751928c05caa5c4acdcc6c667dc59bb7824021b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741772"
---
# <a name="reinitialize-a-subscription"></a><span data-ttu-id="e20f8-102">구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="e20f8-102">Reinitialize a Subscription</span></span>
  <span data-ttu-id="e20f8-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 구독을 다시 초기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-103">This topic describes how to reinitialize a subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="e20f8-104">각 게시를 다시 초기화하도록 표시하여 다음 동기화 중에 새 스냅샷을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-104">Individual subscriptions can be marked for reinitialization so that a new snapshot is applied during the next synchronization.</span></span>  
  
 <span data-ttu-id="e20f8-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e20f8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e20f8-106">**다음을 사용하여 구독을 다시 초기화하려면**</span><span class="sxs-lookup"><span data-stu-id="e20f8-106">**To reinitialize a subscription, using:**</span></span>  
  
     [<span data-ttu-id="e20f8-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e20f8-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e20f8-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e20f8-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e20f8-109">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="e20f8-109">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e20f8-110">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e20f8-110">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e20f8-111">구독을 다시 초기화하는 프로세스는 두 부분으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-111">Reinitializing a subscription is a two-part process:</span></span>  
  
1.  <span data-ttu-id="e20f8-112">게시에 대한 단일 구독이나 모든 구독을 다시 초기화하도록 *표시* 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-112">A single subscription or all subscriptions to a publication are *marked* for reinitialization.</span></span> <span data-ttu-id="e20f8-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **로컬 게시** 폴더와 **로컬 구독** 폴더에서 사용할 수 있는 **구독 다시 초기화** 대화 상자에서 다시 초기화할 구독을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-113">Mark subscriptions for reinitialization in the **Reinitialize Subscription(s)** dialog box, which is available from the **Local Publications** folder and the **Local Subscriptions** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e20f8-114">또한 **모든 구독** 탭 및 복제 모니터의 게시 노드에서 구독을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-114">You can also mark subscriptions from the **All Subscriptions** tab and the publications node in Replication Monitor.</span></span> <span data-ttu-id="e20f8-115">복제 모니터를 시작하는 방법은 [복제 모니터 시작](monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-115">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="e20f8-116">구독을 다시 초기화하도록 표시할 때는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-116">When you mark a subscription for reinitialization, you have the following options:</span></span>  
  
     <span data-ttu-id="e20f8-117">**현재 스냅샷 사용**</span><span class="sxs-lookup"><span data-stu-id="e20f8-117">**Use the current snapshot**</span></span>  
     <span data-ttu-id="e20f8-118">다음에 배포 에이전트 또는 병합 에이전트가 실행될 때 현재 스냅샷을 구독자에 적용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-118">Select to apply the current snapshot to the Subscriber the next time the Distribution Agent or Merge Agent runs.</span></span> <span data-ttu-id="e20f8-119">유효한 스냅샷이 없으면 이 옵션을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-119">If there is no valid snapshot available, this option cannot be selected.</span></span>  
  
     <span data-ttu-id="e20f8-120">**새 스냅샷 사용**</span><span class="sxs-lookup"><span data-stu-id="e20f8-120">**Use a new snapshot**</span></span>  
     <span data-ttu-id="e20f8-121">새 스냅샷으로 구독을 다시 초기화하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-121">Select to reinitialize the subscription with a new snapshot.</span></span> <span data-ttu-id="e20f8-122">스냅샷 에이전트에 의해 스냅샷이 생성된 후에만 스냅샷을 구독자에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-122">The snapshot can be applied to the Subscriber only after it has been generated by the Snapshot Agent.</span></span> <span data-ttu-id="e20f8-123">스냅샷 에이전트가 예약 실행되도록 설정한 경우에는 예약된 다음 스냅샷 에이전트가 실행될 때까지 구독이 다시 초기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-123">If the Snapshot Agent is set to run on a schedule, the subscription is not reinitialized until after the next scheduled Snapshot Agent run.</span></span> <span data-ttu-id="e20f8-124">스냅샷 에이전트를 바로 시작하려면 **지금 새 스냅샷 생성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-124">Select **Generate the new snapshot now** to start the Snapshot Agent immediately.</span></span>  
  
     <span data-ttu-id="e20f8-125">**다시 초기화하기 전에 동기화되지 않은 변경 내용 업로드**</span><span class="sxs-lookup"><span data-stu-id="e20f8-125">**Upload unsynchronized changes before reinitialization**</span></span>  
     <span data-ttu-id="e20f8-126">병합 복제에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-126">Merge replication only.</span></span> <span data-ttu-id="e20f8-127">구독자의 데이터를 스냅샷으로 덮어쓰기 전에 보류 중인 구독 데이터베이스의 변경 내용을 업로드하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-127">Select to upload any pending changes from the subscription database before the data at the Subscriber is overwritten with a snapshot.</span></span>  
  
     <span data-ttu-id="e20f8-128">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-128">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e20f8-129">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-129">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e20f8-130">구독이 다음에 동기화될 때 다시 초기화됩니다. 배포 에이전트(트랜잭션 복제의 경우) 또는 병합 에이전트(병합 복제의 경우)는 최신 스냅샷을 다시 초기화하도록 표시된 구독이 있는 각 구독자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-130">A subscription is reinitialized the next time it is synchronized: the Distribution Agent (for transactional replication) or Merge Agent (for merge replication) applies the most recent snapshot to each Subscriber that has a subscription marked for reinitialization.</span></span> <span data-ttu-id="e20f8-131">구독 동기화 방법은 [Synchronize a Push Subscription](synchronize-a-push-subscription.md) 및 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)대화 상자에서 다시 초기화할 구독을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-131">For more information about synchronizing subscriptions, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a><span data-ttu-id="e20f8-132">Management Studio에서 단일 밀어넣기 또는 끌어오기 구독을 다시 초기화하도록 표시하려면(게시자)</span><span class="sxs-lookup"><span data-stu-id="e20f8-132">To mark a single push or pull subscription for reinitialization in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="e20f8-133">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e20f8-134">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e20f8-135">다시 초기화할 구독이 있는 게시를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-135">Expand the publication that has the subscription you want to reinitialize.</span></span>  
  
4.  <span data-ttu-id="e20f8-136">구독을 마우스 오른쪽 단추로 클릭한 다음 **다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-136">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
5.  <span data-ttu-id="e20f8-137">**구독 다시 초기화** 대화 상자에서 옵션을 선택한 다음 **다시 초기화 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-137">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a><span data-ttu-id="e20f8-138">Management Studio에서 단일 끌어오기 구독을 다시 초기화하도록 표시하려면(구독자)</span><span class="sxs-lookup"><span data-stu-id="e20f8-138">To mark a single pull subscription for reinitialization in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="e20f8-139">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-139">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e20f8-140">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-140">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="e20f8-141">구독을 마우스 오른쪽 단추로 클릭한 다음 **다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-141">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
4.  <span data-ttu-id="e20f8-142">확인 대화 상자가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-142">In the confirmation dialog box that is displayed, click **Yes**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a><span data-ttu-id="e20f8-143">Management Studio에서 모든 구독을 다시 초기화하도록 표시하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-143">To mark all subscriptions for reinitialization in Management Studio</span></span>  
  
1.  <span data-ttu-id="e20f8-144">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-144">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="e20f8-145">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-145">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="e20f8-146">다시 초기화할 구독이 있는 게시를 마우스 오른쪽 단추로 클릭한 다음 **모든 구독 다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-146">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
4.  <span data-ttu-id="e20f8-147">**구독 다시 초기화** 대화 상자에서 옵션을 선택한 다음 **다시 초기화 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-147">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="e20f8-148">복제 모니터에서 단일 밀어넣기 또는 끌어오기 구독을 다시 초기화하도록 표시하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-148">To mark a single push or pull subscription for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="e20f8-149">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-149">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="e20f8-150">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="e20f8-151">다시 초기화할 구독을 마우스 오른쪽 단추로 클릭한 다음 **구독 다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-151">Right-click the subscription you want to reinitialize, and then click **Reinitialize Subscription**.</span></span>  
  
4.  <span data-ttu-id="e20f8-152">**구독 다시 초기화** 대화 상자에서 옵션을 선택한 다음 **다시 초기화 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-152">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="e20f8-153">복제 모니터에서 모든 구독을 다시 초기화하도록 표시하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-153">To mark all subscriptions for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="e20f8-154">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장한 다음 게시자를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-154">In Replication Monitor, expand a Publisher group in the left pane, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="e20f8-155">다시 초기화할 구독이 있는 게시를 마우스 오른쪽 단추로 클릭한 다음 **모든 구독 다시 초기화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-155">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="e20f8-156">**구독 다시 초기화** 대화 상자에서 옵션을 선택한 다음 **다시 초기화 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-156">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e20f8-157">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e20f8-157">Using Transact-SQL</span></span>  
 <span data-ttu-id="e20f8-158">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 게시를 다시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-158">Subscriptions can be reinitialized programmatically using replication stored procedures.</span></span> <span data-ttu-id="e20f8-159">사용되는 저장 프로시저는 구독의 유형(밀어넣기 또는 끌어오기) 및 구독이 속한 게시의 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-159">The stored procedure that is used depends on the type of subscription (push or pull) and the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="e20f8-160">트랜잭션 게시에 대한 끌어오기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-160">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e20f8-161">구독 데이터베이스의 구독자에서 [sp_reinitpullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-161">At the Subscriber on the subscription database, execute [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql).</span></span> <span data-ttu-id="e20f8-162">**@publisher**, **@publisher_db** 및를 지정 **@publication** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-162">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="e20f8-163">이렇게 하면 다음 배포 에이전트 실행 시 구독을 다시 초기화하도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-163">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="e20f8-164">필요에 따라 구독자에서 배포 에이전트를 시작하여 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-164">(Optional) Start the Distribution Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="e20f8-165">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-165">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="e20f8-166">트랜잭션 게시에 대한 밀어넣기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-166">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e20f8-167">게시자에서 [sp_reinitsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-167">At the Publisher, execute [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql).</span></span> <span data-ttu-id="e20f8-168">**@publication**, **@subscriber** 및를 지정 **@destination_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-168">Specify **@publication**, **@subscriber**, and **@destination_db**.</span></span> <span data-ttu-id="e20f8-169">이렇게 하면 다음 배포 에이전트 실행 시 구독을 다시 초기화하도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-169">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="e20f8-170">필요에 따라 배포자에서 배포 에이전트를 시작하여 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-170">(Optional) Start the Distribution Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="e20f8-171">자세한 내용은 [밀어넣기 구독 동기화](synchronize-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-171">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="e20f8-172">병합 게시에 대한 끌어오기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-172">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-173">구독 데이터베이스의 구독자에서 [sp_reinitmergepullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-173">At the Subscriber on the subscription database, execute [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="e20f8-174">**@publisher**, **@publisher_db** 및를 지정 **@publication** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-174">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="e20f8-175">다시 초기화 하기 전에 구독자에서 변경 내용을 업로드 하려면에 값을 지정 `true` **@upload_first** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-175">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="e20f8-176">이렇게 하면 다음 병합 에이전트 실행 시 구독을 다시 초기화하도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-176">This marks the subscription for reinitialization the next time the Merge Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e20f8-177">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-177">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e20f8-178">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-178">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e20f8-179">필요에 따라 구독자에서 병합 에이전트를 시작하여 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-179">(Optional) Start the Merge Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="e20f8-180">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-180">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="e20f8-181">병합 게시에 대한 밀어넣기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-181">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-182">게시자에서 [sp_reinitmergesubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-182">At the Publisher, execute [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql).</span></span> <span data-ttu-id="e20f8-183">**@publication**, **@subscriber** 및를 지정 **@subscriber_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-183">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="e20f8-184">다시 초기화 하기 전에 구독자에서 변경 내용을 업로드 하려면에 값을 지정 `true` **@upload_first** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-184">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="e20f8-185">이렇게 하면 다음 배포 에이전트 실행 시 구독을 다시 초기화하도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-185">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e20f8-186">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-186">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e20f8-187">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-187">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="e20f8-188">필요에 따라 배포자에서 병합 에이전트를 시작하여 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-188">(Optional) Start the Merge Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="e20f8-189">자세한 내용은 [밀어넣기 구독 동기화](synchronize-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-189">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a><span data-ttu-id="e20f8-190">새 병합 게시를 만들 때 다시 초기화 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-190">To set the reinitialization policy when creating a new merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-191">게시 데이터베이스의 게시자에서 [@automatic_reinitialization_policy](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)에 다음 중 한 가지 값을 지정하고 **@automatic_reinitialization_policy**을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-191">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying one of the following values for **@automatic_reinitialization_policy**:</span></span>  
  
    -   <span data-ttu-id="e20f8-192">**1** - 게시의 변경으로 의해 구독이 자동으로 다시 초기화되기 전에 구독자의 변경 내용이 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-192">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="e20f8-193">**0** - 게시의 변경으로 인해 구독이 자동으로 다시 초기화될 때 구독자의 변경 내용이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-193">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e20f8-194">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-194">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e20f8-195">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-195">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="e20f8-196">자세한 내용은 [게시 만들기](publish/create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-196">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a><span data-ttu-id="e20f8-197">기존 병합 게시에 대한 다시 초기화 정책을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-197">To change the reinitialization policy for an existing merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-198">게시 데이터베이스의 게시자에서 [@property](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)에 **automatic_reinitialization_policy** @upload_first **@property** 에는 다음 값 중 하나를 지정하여 **@value**을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-198">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **automatic_reinitialization_policy** for **@property** and one of the following values for **@value**:</span></span>  
  
    -   <span data-ttu-id="e20f8-199">**1** - 게시의 변경으로 의해 구독이 자동으로 다시 초기화되기 전에 구독자의 변경 내용이 업로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-199">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="e20f8-200">**0** - 게시의 변경으로 인해 구독이 자동으로 다시 초기화될 때 구독자의 변경 내용이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-200">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e20f8-201">매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-201">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="e20f8-202">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-202">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="e20f8-203">자세한 내용은 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-203">For more information, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="e20f8-204">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="e20f8-204">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="e20f8-205">각 게시를 다시 초기화하도록 표시하여 다음 동기화 중에 새 스냅샷을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-205">Individual subscriptions can be marked for reinitialization so that during the next synchronization, a new snapshot is applied.</span></span> <span data-ttu-id="e20f8-206">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 구독을 다시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-206">Subscriptions can be reinitialized programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="e20f8-207">사용되는 클래스는 구독이 속한 게시의 유형과 구독의 유형(밀어넣기 또는 끌어오기 구독)에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-207">The classes you use depend on the type of publication to which the subscription belongs and the type of subscription (that is, a push or pull subscription).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="e20f8-208">트랜잭션 게시에 대한 끌어오기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-208">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e20f8-209"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-209">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e20f8-210"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스의 인스턴스를 만들고, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-210">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e20f8-211"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-211">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-212">이 메서드가 `false`를 반환하는 경우 2단계에서 구독 속성이 올바르게 정의되지 않았거나 끌어오기 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-212">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e20f8-213"><xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-213">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e20f8-214">이 메서드는 구독을 다시 초기화하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-214">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="e20f8-215">끌어오기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-215">Synchronize the pull subscription.</span></span> <span data-ttu-id="e20f8-216">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-216">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="e20f8-217">트랜잭션 게시에 대한 밀어넣기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-217">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="e20f8-218"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-218">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e20f8-219"><xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스의 인스턴스를 만들고, <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-219">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e20f8-220"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-220">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-221">이 메서드가 `false`를 반환하는 경우 2단계에서 구독 속성이 올바르게 정의되지 않았거나 밀어넣기 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-221">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e20f8-222"><xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-222">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e20f8-223">이 메서드는 구독을 다시 초기화하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-223">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="e20f8-224">밀어넣기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-224">Synchronize the push subscription.</span></span> <span data-ttu-id="e20f8-225">자세한 내용은 [밀어넣기 구독 동기화](synchronize-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-225">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="e20f8-226">병합 게시에 대한 끌어오기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-226">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-227"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-227">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e20f8-228"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스의 인스턴스를 만들고, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e20f8-229"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-229">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-230">이 메서드가 `false`를 반환하는 경우 2단계에서 구독 속성이 올바르게 정의되지 않았거나 끌어오기 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-230">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e20f8-231"><xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-231">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e20f8-232">다시 초기화하기 전에 구독자의 변경 내용을 업로드하려면 `true` 값을 전달하고, 다시 초기화할 때 보류 중인 모든 변경 내용을 무시하려면 `false`를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-232">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="e20f8-233">이 메서드는 구독을 다시 초기화하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-233">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-234">구독이 만료되면 변경 내용을 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-234">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="e20f8-235">자세한 내용은 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-235">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="e20f8-236">끌어오기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-236">Synchronize the pull subscription.</span></span> <span data-ttu-id="e20f8-237">자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-237">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="e20f8-238">병합 게시에 대한 밀어넣기 구독을 다시 초기화하려면</span><span class="sxs-lookup"><span data-stu-id="e20f8-238">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="e20f8-239"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-239">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="e20f8-240"><xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스의 인스턴스를 만들고, <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>에 대해 1단계에서 만든 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-240">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="e20f8-241"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-241">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-242">이 메서드가 `false`를 반환하는 경우 2단계에서 구독 속성이 올바르게 정의되지 않았거나 밀어넣기 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-242">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="e20f8-243"><xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-243">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="e20f8-244">다시 초기화하기 전에 구독자의 변경 내용을 업로드하려면 `true` 값을 전달하고, 다시 초기화할 때 보류 중인 모든 변경 내용을 무시하려면 `false`를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-244">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="e20f8-245">이 메서드는 구독을 다시 초기화하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-245">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e20f8-246">구독이 만료되면 변경 내용을 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-246">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="e20f8-247">자세한 내용은 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-247">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="e20f8-248">밀어넣기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-248">Synchronize the push subscription.</span></span> <span data-ttu-id="e20f8-249">자세한 내용은 [밀어넣기 구독 동기화](synchronize-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e20f8-249">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="e20f8-250">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="e20f8-250">Examples (RMO)</span></span>  
 <span data-ttu-id="e20f8-251">다음 예에서는 트랜잭션 게시에 대한 끌어오기 구독을 다시 초기합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-251">This example reinitializes a pull subscription to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 <span data-ttu-id="e20f8-252">다음 예에서는 구독자에서 보류 중인 변경 내용을 먼저 업로드한 다음 병합 게시에 대한 끌어오기 구독을 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e20f8-252">This example reinitializes a pull subscription to a merge publication after first uploading pending changes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a><span data-ttu-id="e20f8-253">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e20f8-253">See Also</span></span>  
 <span data-ttu-id="e20f8-254">[구독 다시 초기화](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="e20f8-254">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="e20f8-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="e20f8-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="e20f8-256">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="e20f8-256">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
