---
title: MSSQL_ENG020554 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b48714f19fdec520c7bd20e4d8598d491f6e1908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733948"
---
# <a name="mssql_eng020554"></a><span data-ttu-id="31ae5-102">MSSQL_ENG020554</span><span class="sxs-lookup"><span data-stu-id="31ae5-102">MSSQL_ENG020554</span></span>
    
## <a name="message-details"></a><span data-ttu-id="31ae5-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="31ae5-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31ae5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="31ae5-104">Product Name</span></span>|<span data-ttu-id="31ae5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="31ae5-105">SQL Server</span></span>|  
|<span data-ttu-id="31ae5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="31ae5-106">Event ID</span></span>|<span data-ttu-id="31ae5-107">20554</span><span class="sxs-lookup"><span data-stu-id="31ae5-107">20554</span></span>|  
|<span data-ttu-id="31ae5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="31ae5-108">Event Source</span></span>|<span data-ttu-id="31ae5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="31ae5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="31ae5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="31ae5-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="31ae5-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="31ae5-111">Symbolic Name</span></span>||  
|<span data-ttu-id="31ae5-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="31ae5-112">Message Text</span></span>|<span data-ttu-id="31ae5-113">복제 에이전트가 %ld분 동안 진행률 메시지를 로깅하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-113">The replication agent has not logged a progress message in %ld minutes.</span></span> <span data-ttu-id="31ae5-114">이것은 에이전트가 응답하지 않거나 시스템 작업이 많음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-114">This might indicate an unresponsive agent or high system activity.</span></span> <span data-ttu-id="31ae5-115">레코드가 대상으로 복제되고 구독자, 게시자 및 배포자에 대한 연결이 여전히 활성 상태인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="31ae5-115">Verify that records are being replicated to the destination and that connections to the Subscriber, Publisher, and Distributor are still active.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="31ae5-116">설명</span><span class="sxs-lookup"><span data-stu-id="31ae5-116">Explanation</span></span>  
 <span data-ttu-id="31ae5-117">**복제 에이전트 점검** 작업은 지정된 간격(기본값: 10분)으로 실행되어 각 복제 에이전트의 상태를 점검합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-117">The **Replication agents checkup** job runs at a specified interval (10 minutes by default) to check on the status of each replication agent.</span></span> <span data-ttu-id="31ae5-118">에이전트 점검 작업이 마지막으로 실행된 후 에이전트가 진행 메시지를 기록하지 않은 경우 MSSQL_ENG020554 오류가 발생될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-118">If an agent has not logged any progress messages since the last time the agent checkup job ran, error MSSQL_ENG020554 can be raised.</span></span> <span data-ttu-id="31ae5-119">다른 복제 작업이 일어나지 않아도 에이전트에서는 최소한 기록 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-119">The agent is expected at least to log history messages even if no other replication activity is occurring.</span></span> <span data-ttu-id="31ae5-120">복제 에이전트가 예상대로 응답하지 않는다고 반드시 중지하거나 실패하지는 않습니다. 에이전트가 실패한 경우에는 MSSQL_ENG020536 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-120">Although the replication agent is not responding as expected, it has not necessarily stopped or failed (if an agent has failed, error MSSQL_ENG020536 should be raised).</span></span>  
  
 <span data-ttu-id="31ae5-121">다음 문제로 인해 MSSQL_ENG020554 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-121">The following issues can cause error MSSQL_ENG020554 to be raised:</span></span>  
  
-   <span data-ttu-id="31ae5-122">에이전트에서 너무 많은 작업이 수행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-122">The agent is busy.</span></span>  
  
     <span data-ttu-id="31ae5-123">에이전트 점검 작업으로 폴링할 때 에이전트에서 너무 많은 작업이 수행되고 있어 응답할 수 없으면 에이전트 점검 작업은 복제 에이전트가 제대로 작동하고 있는지 보고할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-123">If the agent is too busy to respond when polled by the agent checkup job, the agent checkup job cannot report whether the replication agent is functioning properly.</span></span> <span data-ttu-id="31ae5-124">복제 중인 데이터가 많거나 애플리케이션 디자인 또는 구성 문제로 인해 프로세스가 장시간 실행하게 되는 등 여러 가지 이유로 인해 복제 에이전트에서 많은 작업이 수행되고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-124">There are a number of reasons why the replication agent could be busy: there might be a lot of data being replicated, or there might be application design or configuration issues that result in processes that run for a long time.</span></span>  
  
-   <span data-ttu-id="31ae5-125">에이전트가 토폴로지의 한 컴퓨터에 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-125">The agent cannot log in to one of the computers in the topology.</span></span>  
  
     <span data-ttu-id="31ae5-126">모든 에이전트에는 **-LoginTimeOut** 매개 변수(15초로 기본 설정되어 있음)가 있습니다. 이 매개 변수는 게시자에 로그인하는 병합 에이전트의 경우와 같이 에이전트가 복제 노드에 로그인을 시도하는 기간을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-126">All agents have a parameter **-LoginTimeOut** (set to 15 seconds by default), which governs how long an agent attempts to log in to a replication node, such as a Merge Agent logging in to the Publisher.</span></span> <span data-ttu-id="31ae5-127">**-LoginTimeOut** 값이 복제 에이전트 점검 작업이 실행되는 간격보다 크게 설정되어 있으면 로그인 문제가 이 오류의 근본 원인일 수 있습니다. 에이전트가 더 구체적인 오류를 발생시키기 전에 MSSQL_ENG020554 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-127">If the **-LoginTimeOut** value is set higher than the interval at which the replication agent checkup job runs, a login problem could be the root cause of the error: error MSSQL_ENG020554 is raised before the agent is able to raise a more specific error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="31ae5-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="31ae5-128">User Action</span></span>  
 <span data-ttu-id="31ae5-129">필요한 동작은 오류의 원인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-129">The action required depends on the cause of the error:</span></span>  
  
-   <span data-ttu-id="31ae5-130">이 오류가 발생된 모든 경우</span><span class="sxs-lookup"><span data-stu-id="31ae5-130">For all cases in which this error is raised:</span></span>  
  
     <span data-ttu-id="31ae5-131">복제 모니터에서 오류 정보를 확인한 다음 중지된 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-131">Check the error details in Replication Monitor, and then restart the agent if it has stopped.</span></span> <span data-ttu-id="31ae5-132">오류 정보에는 에이전트가 제대로 실행되지 않는 원인에 대한 추가 정보가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-132">The error details might provide additional information on why the agent was not running properly.</span></span> <span data-ttu-id="31ae5-133">에이전트가 실행 중이면 에이전트를 중지했다가 다시 시작하지 마십시오. 이렇게 하면 문제를 악화시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-133">If the agent is running, do not stop and restart the agent, because that can exacerbate the problem.</span></span> <span data-ttu-id="31ae5-134">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31ae5-134">For information about viewing agent status and error details in Replication Monitor, see the following topics:</span></span>  
  
    -   <span data-ttu-id="31ae5-135">스냅숏 에이전트, 로그 판독기 에이전트 및 큐 판독기 에이전트는 [복제 모니터를 사용 하 여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31ae5-135">For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
    -   <span data-ttu-id="31ae5-136">배포 에이전트 및 병합 에이전트는 [복제 모니터를 사용 하 여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31ae5-136">For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="31ae5-137">에이전트에서 많은 작업이 수행되고 있어 이 오류가 자주 발생하는 경우</span><span class="sxs-lookup"><span data-stu-id="31ae5-137">If this error is raised frequently because the agent is busy:</span></span>  
  
     <span data-ttu-id="31ae5-138">에이전트에서의 처리 시간을 줄이도록 애플리케이션을 다시 설계해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-138">You might need to redesign your application so that the agent spends less time processing.</span></span>  
  
     <span data-ttu-id="31ae5-139">**작업 속성** 대화 상자를 사용하여 에이전트 상태의 점검 간격을 늘일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-139">You can increase the interval at which agent status is checked using the **Job Properties** dialog box.</span></span> <span data-ttu-id="31ae5-140">복제 작업에 대 한이 대화 상자에 액세스 하는 방법은 [정보 보기 및 복제 모니터를 사용 하 여 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31ae5-140">For information about accessing this dialog box for replication jobs, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="31ae5-141">에이전트가 토폴로지의 한 컴퓨터에 로그인할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="31ae5-141">If an agent cannot log in to one of the computers in the topology:</span></span>  
  
     <span data-ttu-id="31ae5-142">**-LoginTimeOut** 값을 복제 에이전트 점검 작업이 실행되는 간격보다 작게 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-142">We recommend that the **-LoginTimeOut** value be set lower than the interval at which the replication agent checkup job runs.</span></span> <span data-ttu-id="31ae5-143">경우에 따라서는 로그인 제한 시간을 초과하게 하는 네트워크 문제 때문에 **-LoginTimeOut** 의 값이 높게 설정될 수 있습니다. **-LoginTimeOut** 이 작게 설정되면 복제에서 더 구체적인 오류를 보고할 수 있으므로 권한, 네트워크 문제 또는 다른 문제로 인해 일어날 수 있는 로그인 문제를 해결하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-143">In some cases, the value for **-LoginTimeOut** is set higher because of network issues that cause logins to time out. If the **-LoginTimeOut** is set lower, replication can report more specific errors, allowing you to troubleshoot login problems that could be caused by permissions, network problems, or other issues.</span></span> <span data-ttu-id="31ae5-144">에이전트 프로필 및 명령줄에서 에이전트 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-144">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="31ae5-145">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31ae5-145">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="31ae5-146">복제 에이전트 프로필 작업</span><span class="sxs-lookup"><span data-stu-id="31ae5-146">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="31ae5-147">복제 에이전트의 명령 프롬프트 매개 변수 보기 및 수정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="31ae5-147">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="31ae5-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)에 할당될 최소 및 최대 메모리 양을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="31ae5-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ae5-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31ae5-149">See Also</span></span>  
 <span data-ttu-id="31ae5-150">[복제 에이전트 관리](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-150">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="31ae5-151">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-151">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="31ae5-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="31ae5-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="31ae5-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="31ae5-155">[복제 큐 판독기 에이전트](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="31ae5-155">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="31ae5-156">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="31ae5-156">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
