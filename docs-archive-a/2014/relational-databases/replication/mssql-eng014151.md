---
title: MSSQL_ENG014151 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2796451f6f681cfb0ce529ed44a946c34135649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646353"
---
# <a name="mssql_eng014151"></a><span data-ttu-id="3e9b2-102">MSSQL_ENG014151</span><span class="sxs-lookup"><span data-stu-id="3e9b2-102">MSSQL_ENG014151</span></span>
    
## <a name="message-details"></a><span data-ttu-id="3e9b2-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="3e9b2-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e9b2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3e9b2-104">Product Name</span></span>|<span data-ttu-id="3e9b2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3e9b2-105">SQL Server</span></span>|  
|<span data-ttu-id="3e9b2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3e9b2-106">Event ID</span></span>|<span data-ttu-id="3e9b2-107">14151</span><span class="sxs-lookup"><span data-stu-id="3e9b2-107">14151</span></span>|  
|<span data-ttu-id="3e9b2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3e9b2-108">Event Source</span></span>|<span data-ttu-id="3e9b2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3e9b2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3e9b2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3e9b2-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="3e9b2-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3e9b2-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3e9b2-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3e9b2-112">Message Text</span></span>|<span data-ttu-id="3e9b2-113">복제-%s: 에이전트 %s이(가) 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-113">Replication-%s: agent %s failed.</span></span> <span data-ttu-id="3e9b2-114">%s</span><span class="sxs-lookup"><span data-stu-id="3e9b2-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3e9b2-115">설명</span><span class="sxs-lookup"><span data-stu-id="3e9b2-115">Explanation</span></span>  
 <span data-ttu-id="3e9b2-116">이 오류는 복제 에이전트 실패 시 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-116">This error is raised for any replication agent failure.</span></span> <span data-ttu-id="3e9b2-117">메시지 끝의 텍스트는 실패 컨텍스트에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-117">The text at the end of the message depends on the context of the failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3e9b2-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3e9b2-118">User Action</span></span>  
 <span data-ttu-id="3e9b2-119">여러 상황에서 이러한 오류가 발생할 수 있으므로 필요에 따라 다음 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-119">This error can occur in a number of situations; use the following approaches as necessary:</span></span>  
  
-   <span data-ttu-id="3e9b2-120">실패한 에이전트가 이제 실패 없이 실행되는지 알아보려면 해당 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-120">Restart the failed agent to see if it will now run without failures.</span></span> <span data-ttu-id="3e9b2-121">자세한 내용은 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 및 [복제 에이전트 실행 파일 개념](concepts/replication-agent-executables-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-121">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="3e9b2-122">에이전트 기록과 작업 기록에서 같은 시간대에 발생한 다른 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-122">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="3e9b2-123">복제 모니터에서 에이전트 상태 및 오류 정보를 보는 방법에 대한 자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 작업 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="3e9b2-124">에이전트에서 액세스하는 컴퓨터 사이에 기본 연결이 제대로 작동하는지 확인한 다음 [sqlcmd Utility](../../tools/sqlcmd-utility.md)와 같은 유틸리티를 사용하여 각 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-124">Verify that basic connectivity is working between the computers accessed by the agent, and then connect to each computer with a utility like the [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="3e9b2-125">각 컴퓨터에 연결할 때는 에이전트 연결 시 사용하는 계정과 같은 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-125">When connecting, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="3e9b2-126">각 에이전트 계정에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](security/replication-agent-security-model.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-126">For more information about the permissions required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="3e9b2-127">스냅샷을 만들거나 적용하는 동안 오류가 발생하면 스냅샷 디렉터리의 파일에서 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-127">If the error occurs while creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="3e9b2-128">오류가 계속 발생하면 에이전트의 로깅을 늘리고 해당 로그의 출력 파일을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-128">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="3e9b2-129">오류의 컨텍스트에 따라 이러한 작업을 수행하면 오류 및/또는 추가 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9b2-129">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9b2-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e9b2-130">See Also</span></span>  
 <span data-ttu-id="3e9b2-131">[복제 에이전트 관리](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-131">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="3e9b2-132">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-132">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="3e9b2-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="3e9b2-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="3e9b2-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="3e9b2-136">[복제 큐 판독기 에이전트](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b2-136">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="3e9b2-137">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="3e9b2-137">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
