---
title: 동기화 일정 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d752817f7d620b2c6e5fdc5eeb2178c50c42040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738193"
---
# <a name="specify-synchronization-schedules"></a><span data-ttu-id="b780c-102">동기화 일정 지정</span><span class="sxs-lookup"><span data-stu-id="b780c-102">Specify Synchronization Schedules</span></span>
  <span data-ttu-id="b780c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 동기화 일정을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-103">This topic describes how to specify synchronization schedules in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="b780c-104">구독을 만드는 경우 구독에 대한 복제 에이전트를 실행하는 시기를 제어하는 동기화 일정을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-104">When you create a subscription, you can define a synchronization schedule that controls when the replication agent for the subscription will run.</span></span> <span data-ttu-id="b780c-105">일정 매개 변수를 지정하지 않으면 기본 일정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-105">If you do not specify scheduling parameters, the subscription will use the default schedule.</span></span>  
  
 <span data-ttu-id="b780c-106">구독은 배포 에이전트(스냅샷 및 트랜잭션 복제의 경우) 또는 병합 에이전트(병합 복제의 경우)에 의해 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-106">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="b780c-107">에이전트는 지속적으로 실행하거나 수요에 따라 실행하거나 일정에 따라 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-107">Agents can run continuously, run on demand, or run on a schedule.</span></span>  
  
 <span data-ttu-id="b780c-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b780c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b780c-109">**다음을 사용하여 동기화 일정을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="b780c-109">**To specify synchronization schedules, using:**</span></span>  
  
     [<span data-ttu-id="b780c-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b780c-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b780c-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b780c-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b780c-112">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="b780c-112">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b780c-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b780c-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b780c-114">새 구독 마법사의 **동기화 일정** 페이지에서 동기화 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-114">Specify synchronization schedules on the **Synchronization Schedule** page of the New Subscription Wizard.</span></span> <span data-ttu-id="b780c-115">이 마법사의 액세스 방법은 [Create a Push Subscription](create-a-push-subscription.md) 및 [Create a Pull Subscription](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-115">For more information about accessing this wizard, see [Create a Push Subscription](create-a-push-subscription.md) and [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="b780c-116">**작업 일정 속성** 대화 상자에서 동기화 일정을 수정합니다. 이 대화 상자는 **의** 작업 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 폴더와 복제 모니터의 에이전트 세부 정보 창에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-116">Modify synchronization schedules in the **Job Schedule Properties** dialog box, which is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and from the agent details windows in Replication Monitor.</span></span> <span data-ttu-id="b780c-117">복제 모니터를 시작하는 방법은 [복제 모니터 시작](monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-117">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="b780c-118">**작업** 폴더에서 일정을 지정하는 경우에는 다음 표를 사용하여 에이전트 작업 이름을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-118">If you specify schedules from the **Jobs** folder, use the following table to determine the agent job name.</span></span>  
  
|<span data-ttu-id="b780c-119">에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-119">Agent</span></span>|<span data-ttu-id="b780c-120">작업 이름</span><span class="sxs-lookup"><span data-stu-id="b780c-120">Job name</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="b780c-121">끌어오기 구독에 대한 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-121">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|<span data-ttu-id="b780c-122">밀어넣기 구독에 대한 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-122">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|<span data-ttu-id="b780c-123">밀어넣기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-123">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="b780c-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b780c-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|  
|<span data-ttu-id="b780c-125">끌어오기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-125">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="b780c-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b780c-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|  
|<span data-ttu-id="b780c-127">SQL Server 이외 구독자의 밀어넣기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="b780c-127">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
  
 <span data-ttu-id="b780c-128"><sup>1</sup> Oracle 게시에 대한 밀어넣기 구독의 경우 **\<Publisher>-\<PublicationDatabase>** 가 아닌 \*\*\<Publisher>-\<Publisher**>입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-128"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="b780c-129"><sup>2</sup> Oracle 게시에 대한 끌어오기 구독의 경우, **\<Publisher>-\<PublicationDatabase>** 가 아닌 \*\*\<Publisher>-\<DistributionDatabase**>입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-129"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
#### <a name="to-specify-synchronization-schedules"></a><span data-ttu-id="b780c-130">동기화 일정을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-130">To specify synchronization schedules</span></span>  
  
1.  <span data-ttu-id="b780c-131">새 구독 마법사의 **SynchronizationSchedule** 페이지에 있는 **에이전트 일정** 드롭다운 목록에서 만들려는 각 구독에 대해 다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-131">On the **SynchronizationSchedule** page of the New Subscription Wizard, select one of the following values from the **Agent Schedule** drop-down list for each subscription you are creating:</span></span>  
  
    -   <span data-ttu-id="b780c-132">**계속 실행**</span><span class="sxs-lookup"><span data-stu-id="b780c-132">**Run continuously**</span></span>  
  
    -   <span data-ttu-id="b780c-133">**요청 시에만 실행**</span><span class="sxs-lookup"><span data-stu-id="b780c-133">**Run on demand only**</span></span>  
  
    -   **\<Define Schedule...>**  
  
2.  <span data-ttu-id="b780c-134">**\<Define Schedule...>** 를 선택하면 **작업 일정 속성** 대화 상자에서 일정을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-134">If you select **\<Define Schedule...>**, specify a schedule in the **Job Schedule Properties** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b780c-135">마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-135">Complete the wizard.</span></span>  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a><span data-ttu-id="b780c-136">복제 모니터에서 밀어넣기 구독에 대한 동기화 일정을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-136">To modify a synchronization schedule for a push subscription in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="b780c-137">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-137">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="b780c-138">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-138">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="b780c-139">구독을 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-139">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="b780c-140">\*\* \< SubscriptionName> 구독\*\* 창에서 **작업**을 클릭 한 다음 \*\* \<AgentName> 작업 속성\*\*을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-140">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="b780c-141">**작업 속성 - \<JobName>** 대화 상자의 **일정** 페이지에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-141">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
6.  <span data-ttu-id="b780c-142">**작업 일정 속성** 대화 상자의 **일정 유형** 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-142">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="b780c-143">에이전트가 계속 실행되도록 지정하려면 **SQL Server 에이전트가 시작될 때 자동으로 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-143">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="b780c-144">에이전트가 일정대로 실행되도록 지정하려면 **되풀이**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-144">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="b780c-145">에이전트가 요청 시 실행되도록 지정하려면 **한 번**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-145">To specify that the agent should run on demand, select **One time**.</span></span>  
  
7.  <span data-ttu-id="b780c-146">**되풀이**를 선택할 경우에는 에이전트의 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-146">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a><span data-ttu-id="b780c-147">Management Studio에서 밀어넣기 구독에 대한 동기화 일정을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-147">To modify a synchronization schedule for a push subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="b780c-148">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-148">Connect to the Distributor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="b780c-149">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-149">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="b780c-150">구독과 연결된 배포 에이전트 또는 병합 에이전트의 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-150">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b780c-151">**작업 속성 - \<JobName>** 대화 상자의 **일정** 페이지에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-151">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="b780c-152">**작업 일정 속성** 대화 상자의 **일정 유형** 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-152">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="b780c-153">에이전트가 계속 실행되도록 지정하려면 **SQL Server 에이전트가 시작될 때 자동으로 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-153">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="b780c-154">에이전트가 일정대로 실행되도록 지정하려면 **되풀이**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-154">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="b780c-155">에이전트가 요청 시 실행되도록 지정하려면 **한 번**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-155">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="b780c-156">**되풀이**를 선택할 경우에는 에이전트의 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-156">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a><span data-ttu-id="b780c-157">Management Studio에서 끌어오기 구독에 대한 동기화 일정을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-157">To modify a synchronization schedule for a pull subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="b780c-158">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-158">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="b780c-159">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-159">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="b780c-160">구독과 연결된 배포 에이전트 또는 병합 에이전트의 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-160">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b780c-161">**작업 속성 - \<JobName>** 대화 상자의 **일정** 페이지에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-161">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="b780c-162">**작업 일정 속성** 대화 상자의 **일정 유형** 드롭다운 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-162">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="b780c-163">에이전트가 계속 실행되도록 지정하려면 **SQL Server 에이전트가 시작될 때 자동으로 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-163">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="b780c-164">에이전트가 일정대로 실행되도록 지정하려면 **되풀이**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-164">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="b780c-165">에이전트가 요청 시 실행되도록 지정하려면 **한 번**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-165">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="b780c-166">**되풀이**를 선택할 경우에는 에이전트의 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-166">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b780c-167">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b780c-167">Using Transact-SQL</span></span>  
 <span data-ttu-id="b780c-168">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 동기화 일정을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-168">You can define synchronization schedules programmatically using replication stored procedures.</span></span> <span data-ttu-id="b780c-169">사용되는 저장 프로시저는 복제 유형 및 구독 유형(끌어오기 또는 밀어넣기)에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-169">The stored procedures that you use depend on the type of replication and the type of subscription (pull or push).</span></span>  
  
 <span data-ttu-id="b780c-170">일정은 다음 일정 매개 변수로 정의되며 해당 동작은 [sp_add_schedule&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-170">A schedule is defined by the following scheduling parameters, the behaviors of which are inherited from [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql):</span></span>  
  
-   <span data-ttu-id="b780c-171">**@frequency_type**-에이전트를 예약할 때 사용 되는 빈도 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-171">**@frequency_type** - the type of frequency used when scheduling the agent.</span></span>  
  
-   <span data-ttu-id="b780c-172">**@frequency_interval**-에이전트가 실행 되는 요일입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-172">**@frequency_interval** - the day of the week when an agent runs.</span></span>  
  
-   <span data-ttu-id="b780c-173">**@frequency_relative_interval**-지정 된 월에서 에이전트가 매월 실행 되도록 예약 된 주입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-173">**@frequency_relative_interval** - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
-   <span data-ttu-id="b780c-174">**@frequency_recurrence_factor**-동기화 사이에 발생 하는 빈도 유형 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-174">**@frequency_recurrence_factor** - the number of frequency-type units that occur between synchronizations.</span></span>  
  
-   <span data-ttu-id="b780c-175">**@frequency_subday**-에이전트가 하루에 두 번 이상 실행 되는 빈도 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-175">**@frequency_subday** - the frequency unit when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="b780c-176">**@frequency_subday_interval**-에이전트가 하루에 두 번 이상 실행 될 때 실행 간의 빈도 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-176">**@frequency_subday_interval** - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="b780c-177">**@active_start_time_of_day**-지정 된 날짜에서 에이전트가 실행 되기 시작 하는 가장 빠른 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-177">**@active_start_time_of_day** - the earliest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="b780c-178">**@active_end_time_of_day**-지정 된 날짜에서 에이전트가 실행 되는 마지막 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-178">**@active_end_time_of_day** - the latest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="b780c-179">**@active_start_date**-에이전트 예약이 처음 적용 되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-179">**@active_start_date** - the first day that the agent schedule will be in effect.</span></span>  
  
-   <span data-ttu-id="b780c-180">**@active_end_date**-에이전트 예약이 마지막으로 적용 되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-180">**@active_end_date** - the last day that the agent schedule will be in effect.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="b780c-181">트랜잭션 게시에 대한 끌어오기 구독의 동기화 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-181">To define the synchronization schedule for a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="b780c-182">트랜잭션 게시에 대한 새 끌어오기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-182">Create a new pull subscription to a transactional publication.</span></span> <span data-ttu-id="b780c-183">자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-183">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-184">구독자에서 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-184">At the Subscriber, execute [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b780c-185">,,를 지정 하 고 **@publisher** **@publisher_db** **@publication** [!INCLUDE[msCoName](../../includes/msconame-md.md)] 및에 구독자에서 배포 에이전트 실행 되는 Windows 자격 증명 **@job_name** **@password** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-185">Specify **@publisher**, **@publisher_db**, **@publication**, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="b780c-186">구독을 동기화하는 배포 에이전트 작업 일정을 정의하는 동기화 매개 변수(위에서 자세히 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-186">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="b780c-187">트랜잭션 게시에 대한 밀어넣기 구독의 동기화 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-187">To define the synchronization schedule for a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="b780c-188">트랜잭션 게시에 대한 새 밀어넣기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-188">Create a new push subscription to a transactional publication.</span></span> <span data-ttu-id="b780c-189">자세한 내용은 [밀어넣기 구독 만들기](create-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-189">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-190">구독자에서 [sp_addpushsubscription_agent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-190">At the Subscriber, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b780c-191">,,를 지정 하 고 **@subscriber** **@subscriber_db** **@publication** 및에 구독자에서 배포 에이전트 실행 되는 Windows 자격 증명 **@job_name** 을 지정 합니다 **@password** .</span><span class="sxs-lookup"><span data-stu-id="b780c-191">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="b780c-192">구독을 동기화하는 배포 에이전트 작업 일정을 정의하는 동기화 매개 변수(위에서 자세히 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-192">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="b780c-193">병합 게시에 대한 끌어오기 구독의 동기화 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-193">To define the synchronization schedule for a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b780c-194">병합 게시에 대한 새 끌어오기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-194">Create a new pull subscription to a merge publication.</span></span> <span data-ttu-id="b780c-195">자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-195">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-196">구독자에서 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-196">At the Subscriber, execute [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b780c-197">,,를 지정 하 고 **@publisher** **@publisher_db** **@publication** 및에 구독자에서 병합 에이전트 실행 되는 Windows 자격 증명 **@job_name** 을 지정 합니다 **@password** .</span><span class="sxs-lookup"><span data-stu-id="b780c-197">Specify **@publisher**, **@publisher_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="b780c-198">구독을 동기화하는 병합 에이전트 작업 일정을 정의하는 동기화 매개 변수(위에서 자세히 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-198">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="b780c-199">병합 게시에 대한 밀어넣기 구독의 동기화 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-199">To define the synchronization schedule for a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b780c-200">병합 게시에 대한 새 밀어넣기 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-200">Create a new push subscription to a merge publication.</span></span> <span data-ttu-id="b780c-201">자세한 내용은 [밀어넣기 구독 만들기](create-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-201">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-202">구독자에서 [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-202">At the Subscriber, execute [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="b780c-203">,,를 지정 하 고 **@subscriber** **@subscriber_db** **@publication** 및에 구독자에서 병합 에이전트 실행 되는 Windows 자격 증명 **@job_name** 을 지정 합니다 **@password** .</span><span class="sxs-lookup"><span data-stu-id="b780c-203">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="b780c-204">구독을 동기화하는 병합 에이전트 작업 일정을 정의하는 동기화 매개 변수(위에서 자세히 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-204">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="b780c-205">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="b780c-205">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="b780c-206">복제에서는 SQL Server 에이전트를 사용하여 스냅샷 생성이나 구독 동기화와 같이 정기적으로 수행하는 작업의 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-206">Replication uses the SQL Server Agent to schedule jobs for activities that occur periodically, such as snapshot generation and subscription synchronization.</span></span> <span data-ttu-id="b780c-207">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 복제 에이전트 작업의 일정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-207">You can use Replication Management Objects (RMO) programmatically to specify schedules for replication agent jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b780c-208">구독을 만들고 `false`에 `CreateSyncAgentByDefault` 값을 지정하면(끌어오기 구독에 대한 기본 동작) 에이전트 작업은 생성되지 않으며 일정 속성은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-208">When you create a subscription and specify a value `false` for `CreateSyncAgentByDefault` (the default behavior for pull subscriptions) the agent job is not created and scheduling properties are ignored.</span></span> <span data-ttu-id="b780c-209">이 경우에는 애플리케이션에서 동기화 일정을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-209">In this case, the synchronization schedule must be determined by the application.</span></span> <span data-ttu-id="b780c-210">자세한 내용은 [Create a Pull Subscription](create-a-pull-subscription.md) 및 [Create a Push Subscription](create-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-210">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="b780c-211">트랜잭션 게시에 대한 밀어넣기 구독을 만들 때 복제 에이전트 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-211">To define a replication agent schedule when you create a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="b780c-212">만들려는 구독에 대해 <xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-212">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="b780c-213">자세한 내용은 [밀어넣기 구독 만들기](create-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-213">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-214"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>를 호출하기 전에 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 속성의 다음 필드 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-214">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="b780c-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 에이전트를 예약할 때 사용하는 빈도 유형(예: 매일 또는 매주)입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="b780c-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 에이전트가 실행하는 요일입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="b780c-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 지정된 월에서 에이전트가 월별로 실행되도록 예약된 주입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="b780c-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 동기화 사이에 발생하는 frequency-type 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="b780c-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 빈도 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 실행 간의 빈도 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 지정된 날짜에서 에이전트가 실행되는 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 지정된 날짜에서 에이전트가 실행되는 마지막 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 에이전트 예약이 처음 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="b780c-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 에이전트 예약이 마지막으로 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b780c-225">이러한 속성 중 하나를 지정하지 않으면 기본값이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-225">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="b780c-226"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드를 호출하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-226">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="b780c-227">트랜잭션 게시에 대한 끌어오기 구독을 만들 때 복제 에이전트 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-227">To define a replication agent schedule when you create a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="b780c-228">만들려는 구독에 대해 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="b780c-229">자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-229">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-230"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>를 호출하기 전에 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 속성의 다음 필드 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-230">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="b780c-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 에이전트를 예약할 때 사용하는 빈도 유형(예: 매일 또는 매주)입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="b780c-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 에이전트가 실행하는 요일입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="b780c-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 지정된 월에서 에이전트가 월별로 실행되도록 예약된 주입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="b780c-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 동기화 사이에 발생하는 frequency-type 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="b780c-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 빈도 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 실행 간의 빈도 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 지정된 날짜에서 에이전트가 실행되는 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 지정된 날짜에서 에이전트가 실행되는 마지막 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 에이전트 예약이 처음 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="b780c-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 에이전트 예약이 마지막으로 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b780c-241">이러한 속성 중 하나를 지정하지 않으면 기본값이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-241">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="b780c-242"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 메서드를 호출하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-242">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="b780c-243">병합 게시에 대한 끌어오기 구독을 만들 때 복제 에이전트 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-243">To define a replication agent schedule when you create a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b780c-244">만들려는 구독에 대해 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-244">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="b780c-245">자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-245">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-246"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>를 호출하기 전에 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 속성의 다음 필드 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-246">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="b780c-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 에이전트를 예약할 때 사용하는 빈도 유형(예: 매일 또는 매주)입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="b780c-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 에이전트가 실행하는 요일입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="b780c-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 지정된 월에서 에이전트가 월별로 실행되도록 예약된 주입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="b780c-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 동기화 사이에 발생하는 frequency-type 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="b780c-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 빈도 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 실행 간의 빈도 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 지정된 날짜에서 에이전트가 실행되는 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 지정된 날짜에서 에이전트가 실행되는 마지막 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 에이전트 예약이 처음 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="b780c-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 에이전트 예약이 마지막으로 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b780c-257">이러한 속성 중 하나를 지정하지 않으면 기본값이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-257">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="b780c-258"><xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 메서드를 호출하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-258">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="b780c-259">병합 게시에 대한 밀어넣기 구독을 만들 때 복제 에이전트 일정을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="b780c-259">To define a replication agent schedule when you create a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b780c-260">만들려는 구독에 대해 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-260">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="b780c-261">자세한 내용은 [밀어넣기 구독 만들기](create-a-push-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b780c-261">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="b780c-262"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>를 호출하기 전에 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 속성의 다음 필드 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-262">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="b780c-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 에이전트를 예약할 때 사용하는 빈도 유형(예: 매일 또는 매주)입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="b780c-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 에이전트가 실행하는 요일입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="b780c-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 지정된 월에서 에이전트가 월별로 실행되도록 예약된 주입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="b780c-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 동기화 사이에 발생하는 frequency-type 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="b780c-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 빈도 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 에이전트가 하루에 두 번 이상 실행할 경우 실행 간의 빈도 단위 수입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="b780c-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 지정된 날짜에서 에이전트가 실행되는 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 지정된 날짜에서 에이전트가 실행되는 마지막 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="b780c-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 에이전트 예약이 처음 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="b780c-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 에이전트 예약이 마지막으로 적용되는 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b780c-273">이러한 속성 중 하나를 지정하지 않으면 기본값이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-273">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="b780c-274"><xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 메서드를 호출하여 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-274">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="b780c-275">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="b780c-275">Example (RMO)</span></span>  
 <span data-ttu-id="b780c-276">이 예에서는 병합 계시에 대한 밀어넣기 구독을 만들고 구독의 동기화 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b780c-276">This example creates a push subscription to a merge publication and specifies the schedule on which the subscription is synchronized.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="b780c-277">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b780c-277">See Also</span></span>  
 <span data-ttu-id="b780c-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="b780c-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="b780c-279">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="b780c-279">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="b780c-280">[밀어넣기 구독 동기화](synchronize-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="b780c-280">[Synchronize a Push Subscription](synchronize-a-push-subscription.md) </span></span>  
 <span data-ttu-id="b780c-281">[끌어오기 구독 동기화](synchronize-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="b780c-281">[Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="b780c-282">데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="b780c-282">Synchronize Data</span></span>](synchronize-data.md)  
  
  
