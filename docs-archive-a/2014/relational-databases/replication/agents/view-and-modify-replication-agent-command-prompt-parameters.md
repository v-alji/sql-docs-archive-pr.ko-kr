---
title: 복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 752f674c21bb66c7b64e399e30e4917512431195
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646944"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a><span data-ttu-id="1afaf-102">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1afaf-102">View and Modify Replication Agent Command Prompt Parameters (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1afaf-103">복제 에이전트는 명령줄 매개 변수를 받는 실행 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-103">Replication agents are executables that accept command line parameters.</span></span> <span data-ttu-id="1afaf-104">기본적으로 에이전트는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업 단계에서 실행되므로 **작업 속성 - \<Job>** 대화 상자를 사용하여 이러한 매개 변수를 확인한 다음 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-104">By default, agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps, so these parameters can be viewed and modified using the **Job Properties - \<Job>** dialog box.</span></span> <span data-ttu-id="1afaf-105">이 대화 상자는 **의** 작업 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 폴더 및 복제 모니터의 **에이전트** 탭에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-105">This dialog box is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="1afaf-106">복제 모니터를 시작하는 방법은 [복제 모니터 시작](../monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1afaf-106">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1afaf-107">에이전트 매개 변수에 대한 변경 사항은 다음에 에이전트가 시작될 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-107">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="1afaf-108">에이전트가 연속적으로 실행되는 경우에는 에이전트를 중단했다가 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-108">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
 <span data-ttu-id="1afaf-109">매개 변수를 직접 수정할 수도 있지만 에이전트 프로필을 통해 수정하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-109">Although parameters can be modified directly, it is more common to modify them through an agent profile.</span></span> <span data-ttu-id="1afaf-110">자세한 내용은 [Replication Agent Profiles](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1afaf-110">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="1afaf-111">**작업** 폴더에서 에이전트 작업에 액세스할 경우 다음 표를 사용하여 에이전트 작업 이름 및 각 에이전트에 사용 가능한 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-111">If you access agent jobs from the **Jobs** folder, use the following table to determine the agent job name and the parameters available for each agent.</span></span>  
  
|<span data-ttu-id="1afaf-112">에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-112">Agent</span></span>|<span data-ttu-id="1afaf-113">작업 이름</span><span class="sxs-lookup"><span data-stu-id="1afaf-113">Job name</span></span>|<span data-ttu-id="1afaf-114">매개 변수 목록은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1afaf-114">For a list of parameters, see...</span></span>|  
|-----------|--------------|------------------------------------|  
|<span data-ttu-id="1afaf-115">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-115">Snapshot Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[<span data-ttu-id="1afaf-116">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-116">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="1afaf-117">병합 게시 파티션에 대한 스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-117">Snapshot Agent for a merge publication partition</span></span>|<span data-ttu-id="1afaf-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span><span class="sxs-lookup"><span data-stu-id="1afaf-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span></span>|[<span data-ttu-id="1afaf-119">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-119">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="1afaf-120">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-120">Log Reader Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[<span data-ttu-id="1afaf-121">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-121">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|  
|<span data-ttu-id="1afaf-122">끌어오기 구독에 대한 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-122">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[<span data-ttu-id="1afaf-123">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-123">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="1afaf-124">밀어넣기 구독에 대한 병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-124">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="1afaf-125">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-125">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="1afaf-126">밀어넣기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-126">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="1afaf-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1afaf-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|[<span data-ttu-id="1afaf-128">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-128">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="1afaf-129">끌어오기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-129">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="1afaf-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="1afaf-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|[<span data-ttu-id="1afaf-131">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-131">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="1afaf-132">SQL Server 이외 구독자의 밀어넣기 구독에 대한 배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-132">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="1afaf-133">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-133">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="1afaf-134">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="1afaf-134">Queue Reader Agent</span></span>|<span data-ttu-id="1afaf-135">**[\<Distributor>].\<integer>**</span><span class="sxs-lookup"><span data-stu-id="1afaf-135">**[\<Distributor>].\<integer>**</span></span>|[<span data-ttu-id="1afaf-136">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="1afaf-136">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|  
  
 <span data-ttu-id="1afaf-137"><sup>1</sup> Oracle 게시에 대한 밀어넣기 구독의 경우 **\<Publisher>-\<PublicationDatabase>** 가 아닌 \*\*\<Publisher>-\<Publisher**>입니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-137"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="1afaf-138"><sup>2</sup> Oracle 게시에 대한 끌어오기 구독의 경우, **\<Publisher>-\<PublicationDatabase>** 가 아닌 \*\*\<Publisher>-\<DistributionDatabase**>입니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-138"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a><span data-ttu-id="1afaf-139">Management Studio에서 복제 에이전트 명령줄 매개 변수를 확인한 다음 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1afaf-139">To view and modify replication agent command line parameters from Management Studio</span></span>  
  
1.  <span data-ttu-id="1afaf-140">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 적절한 컴퓨터에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-140">Connect to the appropriate computer in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="1afaf-141">끌어오기 구독에 대한 배포 에이전트 및 병합 에이전트의 경우 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-141">For the Distribution Agent and Merge Agent for pull subscriptions, connect to the Subscriber.</span></span>  
  
    -   <span data-ttu-id="1afaf-142">그 외의 모든 에이전트의 경우 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-142">For all other agents, connect to the Distributor.</span></span>  
  
2.  <span data-ttu-id="1afaf-143">**SQL Server 에이전트** 폴더를 확장한 다음 **작업** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-143">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="1afaf-144">작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-144">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1afaf-145">**작업 속성 - \<Job>** 대화 상자의 **단계** 페이지에서 **에이전트 실행** 단계를 선택한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-145">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="1afaf-146">**작업 단계 속성 - 에이전트를 실행합니다** 대화 상자에서 **명령** 필드를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-146">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="1afaf-147">두 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-147">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="1afaf-148">복제 모니터에서 배포 에이전트 및 병합 에이전트 명령줄 매개 변수를 확인한 다음 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1afaf-148">To view and modify Distribution Agent and Merge Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1afaf-149">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-149">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="1afaf-150">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="1afaf-151">구독을 마우스 오른쪽 단추로 클릭한 다음 **자세히 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-151">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="1afaf-152">\*\* \< SubscriptionName> 구독\*\* 창에서 **작업**을 클릭 한 다음 \*\* \<AgentName> 작업 속성\*\*을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-152">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="1afaf-153">**작업 속성 - \<Job>** 대화 상자의 **단계** 페이지에서 **에이전트 실행** 단계를 선택한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-153">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="1afaf-154">**작업 단계 속성 - 에이전트를 실행합니다** 대화 상자에서 **명령** 필드를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-154">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
7.  <span data-ttu-id="1afaf-155">두 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-155">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="1afaf-156">복제 모니터에서 스냅샷 에이전트, 로그 판독기 에이전트 및 큐 판독기 에이전트 명령줄 매개 변수를 확인한 다음 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1afaf-156">To view and modify Snapshot Agent, Log Reader Agent, and Queue Reader Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1afaf-157">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-157">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="1afaf-158">**에이전트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-158">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="1afaf-159">표에서 에이전트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-159">Right-click an agent in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1afaf-160">**작업 속성 - \<Job>** 대화 상자의 **단계** 페이지에서 **에이전트 실행** 단계를 선택한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-160">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="1afaf-161">**작업 단계 속성 - 에이전트를 실행합니다** 대화 상자에서 **명령** 필드를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-161">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="1afaf-162">두 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1afaf-162">Click **OK** on both dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afaf-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1afaf-163">See Also</span></span>  
 <span data-ttu-id="1afaf-164">[복제 에이전트 관리](replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="1afaf-164">[Replication Agent Administration](replication-agent-administration.md) </span></span>  
 <span data-ttu-id="1afaf-165">[복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1afaf-165">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="1afaf-166">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="1afaf-166">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
