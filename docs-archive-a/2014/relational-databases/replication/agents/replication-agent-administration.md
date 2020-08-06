---
title: 복제 에이전트 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, administering
- Log Reader Agent, administering
- Queue Reader Agent, administering
- shared agents [SQL Server replication]
- Merge Agent, administering
- Distribution Agent, administering
- agents [SQL Server replication], administering
- replication cleanup jobs [SQL Server]
- administering replication, agents
- replication [SQL Server], administering
- independent agents [SQL Server replication]
ms.assetid: f27186b8-b1b2-4da0-8b2b-91f632c2ab7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99cf9be6b31310e5ae0ebac3c096851ac4f63452
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648956"
---
# <a name="replication-agent-administration"></a><span data-ttu-id="7ba5e-102">복제 에이전트 관리</span><span class="sxs-lookup"><span data-stu-id="7ba5e-102">Replication Agent Administration</span></span>
  <span data-ttu-id="7ba5e-103">복제 에이전트는 스키마와 데이터의 복사본 만들기, 게시자 또는 구독자에서 업데이트 검색, 서버 간에 변경 내용 전파 등 복제와 관련된 많은 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-103">Replication agents carry out many of the tasks associated with replication, including creating copies of schema and data, detecting updates at the Publisher or Subscriber, and propagating changes between servers.</span></span> <span data-ttu-id="7ba5e-104">기본적으로 복제 에이전트는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업 단계에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-104">By default, replication agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="7ba5e-105">에이전트는 단순히 실행 파일이므로 명령줄 및 일괄 처리 스크립트에서 직접 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-105">The agents are simply executables, so they can also be called directly from the command line and from batch scripts.</span></span> <span data-ttu-id="7ba5e-106">각 응용 프로그램 에이전트는 실행 방식을 제어하는 데 사용되는 일련의 런타임 매개 변수를 지원합니다. 이러한 매개 변수는 에이전트 프로필 또는 명령줄에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-106">Each replication agent supports a set of run-time parameters used to control how it runs; these parameters are specified in an agent profile or on the command line.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ba5e-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 설치될 때 사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 서비스를 자동으로 시작하도록 명시적으로 선택하지 않으면 기본적으로 이 서비스는 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-107">By default, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is disabled when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed unless you explicitly choose to autostart the service during installation.</span></span>  
  
 <span data-ttu-id="7ba5e-108">복제 에이전트 파일은 [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-108">Replication agent files are located under [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM.</span></span> <span data-ttu-id="7ba5e-109">다음 표에서는 복제 실행 파일과 파일 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-109">The following table lists the replication executable names and file names.</span></span> <span data-ttu-id="7ba5e-110">에이전트에 대한 링크를 클릭하면 해당 매개 변수 참조가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-110">Click the link for an agent to view its parameter reference.</span></span>  
  
|<span data-ttu-id="7ba5e-111">에이전트 실행 파일</span><span class="sxs-lookup"><span data-stu-id="7ba5e-111">Agent Executable</span></span>|<span data-ttu-id="7ba5e-112">파일 이름</span><span class="sxs-lookup"><span data-stu-id="7ba5e-112">File Name</span></span>|  
|----------------------|---------------|  
|[<span data-ttu-id="7ba5e-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="7ba5e-113">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|<span data-ttu-id="7ba5e-114">snapshot.exe</span><span class="sxs-lookup"><span data-stu-id="7ba5e-114">snapshot.exe</span></span>|  
|[<span data-ttu-id="7ba5e-115">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="7ba5e-115">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|<span data-ttu-id="7ba5e-116">distrib.exe</span><span class="sxs-lookup"><span data-stu-id="7ba5e-116">distrib.exe</span></span>|  
|[<span data-ttu-id="7ba5e-117">복제 로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-117">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|<span data-ttu-id="7ba5e-118">logread.exe</span><span class="sxs-lookup"><span data-stu-id="7ba5e-118">logread.exe</span></span>|  
|[<span data-ttu-id="7ba5e-119">Replication Queue Reader Agent</span><span class="sxs-lookup"><span data-stu-id="7ba5e-119">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|<span data-ttu-id="7ba5e-120">qrdrsvc.exe</span><span class="sxs-lookup"><span data-stu-id="7ba5e-120">qrdrsvc.exe</span></span>|  
|[<span data-ttu-id="7ba5e-121">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="7ba5e-121">Replication Merge Agent</span></span>](replication-merge-agent.md)|<span data-ttu-id="7ba5e-122">replmerg.exe</span><span class="sxs-lookup"><span data-stu-id="7ba5e-122">replmerg.exe</span></span>|  
  
 <span data-ttu-id="7ba5e-123">복제 에이전트뿐만 아니라 복제에서도 여러 작업을 통해 예약 유지 관리와 요청 시 유지 관리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-123">In addition to replication agents, replication has a number of jobs that perform scheduled and on-demand maintenance.</span></span>  
  
 <span data-ttu-id="7ba5e-124">**에이전트 및 유지 관리 작업을 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="7ba5e-124">**To run agents and maintenance jobs**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="7ba5e-125">및 복제 모니터: [복제 에이전트를 시작 및 중지 &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7ba5e-125">and Replication Monitor: [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="7ba5e-126">복제 프로그래밍: [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span><span class="sxs-lookup"><span data-stu-id="7ba5e-126">Replication programming: [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)</span></span>  
  
## <a name="agent-profiles"></a><span data-ttu-id="7ba5e-127">에이전트 프로필</span><span class="sxs-lookup"><span data-stu-id="7ba5e-127">Agent Profiles</span></span>  
 <span data-ttu-id="7ba5e-128">복제가 구성되면 에이전트 프로필 집합이 배포자에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-128">When replication is configured, a set of agent profiles is installed on the Distributor.</span></span> <span data-ttu-id="7ba5e-129">에이전트 프로필에는 에이전트가 실행될 때마다 사용할 매개 변수 집합이 포함됩니다. 각 에이전트는 시작 과정 중에 배포자로 로그인하여 해당 프로필의 매개 변수에 대해 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-129">An agent profile contains a set of parameters that are used each time an agent runs: each agent logs in to the Distributor during its startup process and queries for the parameters in its profile.</span></span> <span data-ttu-id="7ba5e-130">복제는 각 에이전트에 대한 기본 프로필과 로그 판독기 에이전트, 배포 에이전트 및 병합 에이전트에 대한 미리 정의된 추가 프로필을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-130">Replication provides a default profile for each agent and additional predefined profiles for the Log Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="7ba5e-131">제공된 프로필뿐 아니라 애플리케이션 요구 사항에 찾는 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-131">In addition to the profiles provided, you can create profiles suited to your application requirements.</span></span> <span data-ttu-id="7ba5e-132">자세한 내용은 [Replication Agent Profiles](replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-132">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="7ba5e-133">명령줄 매개 변수를 직접 지정하는 방법은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-133">For information about specifying command line parameters directly, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="monitoring-replication-agents"></a><span data-ttu-id="7ba5e-134">복제 에이전트 모니터링</span><span class="sxs-lookup"><span data-stu-id="7ba5e-134">Monitoring Replication Agents</span></span>  
 <span data-ttu-id="7ba5e-135">복제 모니터를 사용하여 복제 에이전트에 대한 정보를 보고 복제 에이전트와 연결된 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-135">Replication Monitor allows you to view information and perform tasks associated with each replication agent.</span></span> <span data-ttu-id="7ba5e-136">다음 목록에는 각 에이전트, 에이전트를 찾을 수 있는 복제 모니터의 탭 및 이러한 탭에 액세스하는 방법을 설명하는 항목에 대한 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-136">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="7ba5e-137">다음 에이전트는 복제 모니터에서 게시와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-137">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="7ba5e-138">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-138">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="7ba5e-139">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-139">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="7ba5e-140">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-140">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="7ba5e-141">**에이전트** 탭을 통해 이러한 에이전트와 관련 된 정보 및 태스크에 액세스 합니다. 자세한 내용은 [복제 모니터를 사용 하 여 정보 보기 및 태스크 수행](../monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-141">Access information and tasks associated with these agents through the **Agents** tab. For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="7ba5e-142">다음 에이전트는 복제 모니터에서 구독과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-142">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="7ba5e-143">배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-143">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="7ba5e-144">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-144">Merge Agent</span></span>  
  
     <span data-ttu-id="7ba5e-145">이러한 에이전트와 연결된 정보 및 작업은 **구독 조사 목록**(각 게시자에 대해 사용 가능) 또는 **모든 구독** 탭(각 게시에 대해 사용 가능)을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-145">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="7ba5e-146">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](../monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-146">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="independent-and-shared-agents"></a><span data-ttu-id="7ba5e-147">독립 및 공유 에이전트</span><span class="sxs-lookup"><span data-stu-id="7ba5e-147">Independent and Shared Agents</span></span>  
 <span data-ttu-id="7ba5e-148">독립 에이전트는 한 구독에 사용되는 에이전트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-148">An independent agent is an agent that services one subscription.</span></span> <span data-ttu-id="7ba5e-149">공유 에이전트는 여러 구독을 제공합니다. 동일한 공유 에이전트를 사용하는 여러 구독을 동기화해야 할 경우 기본적으로 여러 구독은 큐에서 대기하고 공유 에이전트가 한 번에 하나씩 구독을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-149">A shared agent services multiple subscriptions; if multiple subscriptions using the same shared agent need to synchronize, by default they wait in a queue, and the shared agent services them one at a time.</span></span> <span data-ttu-id="7ba5e-150">독립 에이전트는 구독에 동기화가 필요할 때마다 준비가 되어 있기 때문에 이를 사용하면 대기 시간이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-150">Latency is reduced when using independent agents because the agent is ready whenever the subscription needs to be synchronized.</span></span> <span data-ttu-id="7ba5e-151">병합 복제는 항상 독립 에이전트를 사용하고 트랜잭션 복제는 새 게시 마법사에서 만든 게시에 대해 기본적으로 독립 에이전트를 사용합니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 트랜잭션 복제가 기본적으로 공유 에이전트를 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-151">Merge replication always uses independent agents, and transactional replication uses independent agents by default for publications created in the New Publication Wizard (in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], transactional replication used shared agents by default).</span></span>  
  
## <a name="replication-maintenance-jobs"></a><span data-ttu-id="7ba5e-152">복제 유지 관리 작업</span><span class="sxs-lookup"><span data-stu-id="7ba5e-152">Replication Maintenance Jobs</span></span>  
 <span data-ttu-id="7ba5e-153">복제는 다음 작업을 통해 예약 유지 관리와 요청 시 유지 관리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-153">Replication uses the following jobs to perform scheduled and on-demand maintenance.</span></span>  
  
|<span data-ttu-id="7ba5e-154">작업 정리</span><span class="sxs-lookup"><span data-stu-id="7ba5e-154">Clean up job</span></span>|<span data-ttu-id="7ba5e-155">Description</span><span class="sxs-lookup"><span data-stu-id="7ba5e-155">Description</span></span>|<span data-ttu-id="7ba5e-156">기본 일정</span><span class="sxs-lookup"><span data-stu-id="7ba5e-156">Default schedule</span></span>|  
|------------------|-----------------|----------------------|  
|<span data-ttu-id="7ba5e-157">에이전트 기록 정리: 배포</span><span class="sxs-lookup"><span data-stu-id="7ba5e-157">Agent History Clean Up: Distribution</span></span>|<span data-ttu-id="7ba5e-158">배포 데이터베이스에서 복제 에이전트 기록을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-158">Removes replication agent history from the distribution database.</span></span>|<span data-ttu-id="7ba5e-159">10분마다 실행</span><span class="sxs-lookup"><span data-stu-id="7ba5e-159">Runs every ten minutes</span></span>|  
|<span data-ttu-id="7ba5e-160">배포 정리: 배포</span><span class="sxs-lookup"><span data-stu-id="7ba5e-160">Distribution Clean Up: Distribution</span></span>|<span data-ttu-id="7ba5e-161">배포 데이터베이스에서 복제된 트랜잭션을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-161">Removes replicated transactions from the distribution database.</span></span> <span data-ttu-id="7ba5e-162">최대 배포 보존 기간 내에 동기화되지 않은 구독을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-162">Deactivates subscriptions that have not been synchronized within the maximum distribution retention period.</span></span>|<span data-ttu-id="7ba5e-163">10분마다 실행</span><span class="sxs-lookup"><span data-stu-id="7ba5e-163">Runs every ten minutes</span></span>|  
|<span data-ttu-id="7ba5e-164">만료된 구독 정리</span><span class="sxs-lookup"><span data-stu-id="7ba5e-164">Expired Subscription Clean Up</span></span>|<span data-ttu-id="7ba5e-165">게시 데이터베이스에서 만료된 구독을 검색하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-165">Detects and removes expired subscriptions from publication databases.</span></span>|<span data-ttu-id="7ba5e-166">매일 오전 1시에 실행</span><span class="sxs-lookup"><span data-stu-id="7ba5e-166">Runs every day at 1:00 A.M.</span></span>|  
|<span data-ttu-id="7ba5e-167">데이터 유효성 검사에 실패한 구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="7ba5e-167">Reinitialize Subscriptions Having Data Validation Failures</span></span>|<span data-ttu-id="7ba5e-168">데이터 유효성 검사에 실패한 모든 구독을 검색한 다음 다시 초기화하도록 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-168">Detects all subscriptions that have data validation failures and marks them for reinitialization.</span></span> <span data-ttu-id="7ba5e-169">다음에 병합 에이전트 또는 배포 에이전트가 실행될 때 새 스냅샷이 구독자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-169">The next time the Merge Agent or Distribution Agent runs, a new snapshot will be applied at the Subscribers.</span></span>|<span data-ttu-id="7ba5e-170">기본 일정 없음(기본적으로 사용되지 않음)</span><span class="sxs-lookup"><span data-stu-id="7ba5e-170">No default schedule (not enabled by default).</span></span>|  
|<span data-ttu-id="7ba5e-171">복제 에이전트 점검</span><span class="sxs-lookup"><span data-stu-id="7ba5e-171">Replication Agents Checkup</span></span>|<span data-ttu-id="7ba5e-172">기록을 로깅하지 않는 복제 에이전트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-172">Detects replication agents that are not actively logging history.</span></span> <span data-ttu-id="7ba5e-173">작업 단계가 실패하면 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 이벤트 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-173">It writes to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows event log if a job step fails.</span></span>|<span data-ttu-id="7ba5e-174">10분마다 실행</span><span class="sxs-lookup"><span data-stu-id="7ba5e-174">Runs every ten minutes.</span></span>|  
|<span data-ttu-id="7ba5e-175">배포에 대한 복제 모니터링 리프레셔</span><span class="sxs-lookup"><span data-stu-id="7ba5e-175">Replication monitoring refresher for distribution</span></span>|<span data-ttu-id="7ba5e-176">복제 모니터에서 사용한 캐시된 쿼리를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba5e-176">Refreshes cached queries used by Replication Monitor..</span></span>|<span data-ttu-id="7ba5e-177">계속 실행</span><span class="sxs-lookup"><span data-stu-id="7ba5e-177">Runs continuously.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ba5e-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ba5e-178">See Also</span></span>  
 [<span data-ttu-id="7ba5e-179">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="7ba5e-179">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
