---
title: MSSQL_ENG014150 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c926d05be9613ff559f119484fa5e238d71d861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646359"
---
# <a name="mssql_eng014150"></a><span data-ttu-id="6f4c5-102">MSSQL_ENG014150</span><span class="sxs-lookup"><span data-stu-id="6f4c5-102">MSSQL_ENG014150</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6f4c5-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="6f4c5-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f4c5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6f4c5-104">Product Name</span></span>|<span data-ttu-id="6f4c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6f4c5-105">SQL Server</span></span>|  
|<span data-ttu-id="6f4c5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6f4c5-106">Event ID</span></span>|<span data-ttu-id="6f4c5-107">14150</span><span class="sxs-lookup"><span data-stu-id="6f4c5-107">14150</span></span>|  
|<span data-ttu-id="6f4c5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6f4c5-108">Event Source</span></span>|<span data-ttu-id="6f4c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6f4c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6f4c5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6f4c5-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6f4c5-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6f4c5-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6f4c5-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-112">Message Text</span></span>|<span data-ttu-id="6f4c5-113">복제-%s: 에이전트 %s이(가) 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-113">Replication-%s: agent %s succeeded.</span></span> <span data-ttu-id="6f4c5-114">%s</span><span class="sxs-lookup"><span data-stu-id="6f4c5-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6f4c5-115">설명</span><span class="sxs-lookup"><span data-stu-id="6f4c5-115">Explanation</span></span>  
 <span data-ttu-id="6f4c5-116">이 메시지는 복제 에이전트가 성공적으로 실행되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-116">This message indicates that a replication agent has successfully finished running.</span></span> <span data-ttu-id="6f4c5-117">복제는 다음 에이전트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-117">Replication uses the following agents:</span></span>  
  
-   <span data-ttu-id="6f4c5-118">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-118">The Snapshot Agent.</span></span> <span data-ttu-id="6f4c5-119">이 에이전트는 모든 게시에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-119">This agent is used by all publications.</span></span>  
  
-   <span data-ttu-id="6f4c5-120">로그 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-120">The Log Reader Agent.</span></span> <span data-ttu-id="6f4c5-121">이 에이전트는 모든 트랜잭션 게시에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-121">This agent is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="6f4c5-122">큐 판독기 에이전트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-122">The Queue Reader Agent.</span></span> <span data-ttu-id="6f4c5-123">이 에이전트는 지연 업데이트 구독이 활성화된 트랜잭션 게시에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-123">This agent is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="6f4c5-124">배포 에이전트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-124">The Distribution Agent.</span></span> <span data-ttu-id="6f4c5-125">이 에이전트는 구독을 트랜잭션 및 스냅샷 게시와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-125">This agent synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="6f4c5-126">병합 에이전트</span><span class="sxs-lookup"><span data-stu-id="6f4c5-126">The Merge Agent.</span></span> <span data-ttu-id="6f4c5-127">이 에이전트는 구독을 병합 게시와 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-127">This agent synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="6f4c5-128">복제 유지 관리 작업</span><span class="sxs-lookup"><span data-stu-id="6f4c5-128">Replication maintenance jobs.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6f4c5-129">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6f4c5-129">User Action</span></span>  
 <span data-ttu-id="6f4c5-130">다른 에이전트가 요청 시 또는 예약 시에 실행되는 반면 로그 판독기 에이전트, 큐 판독기 에이전트 및 배포 에이전트는 일반적으로 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-130">The Log Reader Agent, Queue Reader Agent, and Distribution Agent typically run continuously, whereas the other agents typically run on demand or on a schedule.</span></span> <span data-ttu-id="6f4c5-131">에이전트의 실행을 완료하지 않도록 하려면 에이전트의 상태를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-131">If you do not expect an agent to have completed a run, check the status of the agent.</span></span> <span data-ttu-id="6f4c5-132">자세한 내용은 [Monitor Replication Agents](agents/replication-agents-overview.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f4c5-132">For more information, see [Monitor Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4c5-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f4c5-133">See Also</span></span>  
 <span data-ttu-id="6f4c5-134">[복제 에이전트 관리](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-134">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="6f4c5-135">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-135">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="6f4c5-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="6f4c5-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="6f4c5-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="6f4c5-139">[복제 큐 판독기 에이전트](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="6f4c5-139">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="6f4c5-140">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="6f4c5-140">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
