---
title: 복제 토폴로지 정지(복제 Transact-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12f0fb8ee3a6118e03799d17836573fb5c733df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736249"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a><span data-ttu-id="0778d-102">복제 토폴로지 정지(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="0778d-102">Quiesce a Replication Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="0778d-103"> 시스템 *정지* 과정에서는 모든 노드에서 게시된 테이블에 대한 작업을 중지하고 각 노드가 다른 모든 노드의 변경 내용을 받았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-103">*Quiescing* a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="0778d-104">이 항목에서는 여러 가지 관리 태스크에 필요한 복제 토폴로지 정지 방법과 노드가 다른 노드의 변경 내용을 모두 받았는지 확인하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-104">This topic explains how to quiesce a replication topology, which is required for a number of administrative tasks, and how to ensure that a node has received all changes from other nodes.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a><span data-ttu-id="0778d-105">읽기 전용 구독이 포함된 트랜잭션 복제 토폴로지를 정지하려면</span><span class="sxs-lookup"><span data-stu-id="0778d-105">To quiesce a transactional replication topology with read-only subscriptions</span></span>  
  
1.  <span data-ttu-id="0778d-106">게시자에서 게시된 모든 테이블에 대한 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-106">Stop activity on all published tables at the Publisher.</span></span>  
  
2.  <span data-ttu-id="0778d-107">게시 데이터베이스의 게시자에서 [sp_posttracertoken&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-107">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
3.  <span data-ttu-id="0778d-108">게시 데이터베이스의 게시자에서 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-108">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
4.  <span data-ttu-id="0778d-109">각 구독자가 추적 프로그램 토큰을 받았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-109">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a><span data-ttu-id="0778d-110">업데이트 가능 구독이 포함된 트랜잭션 복제 토폴로지를 정지하려면</span><span class="sxs-lookup"><span data-stu-id="0778d-110">To quiesce a transactional replication topology with updatable subscriptions</span></span>  
  
1.  <span data-ttu-id="0778d-111">게시자 및 모든 구독자에서 게시된 모든 테이블에 대한 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-111">Stop activity on all published tables at the Publisher and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="0778d-112">구독자가 지연 업데이트 구독을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="0778d-112">If any Subscribers use queued updating subscriptions:</span></span>  
  
    1.  <span data-ttu-id="0778d-113">큐 판독기 에이전트가 연속 모드로 실행되지 않는 경우 해당 에이전트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-113">If the Queue Reader Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="0778d-114">에이전트 실행에 대한 자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) 또는 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0778d-114">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    2.  <span data-ttu-id="0778d-115">큐가 비어 있는지 확인하려면 각 구독자에서 [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-115">To verify that the queue is empty, execute [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) at each Subscriber.</span></span>  
  
3.  <span data-ttu-id="0778d-116">게시 데이터베이스의 게시자에서 [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-116">At the Publisher on the publication database, execute [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
4.  <span data-ttu-id="0778d-117">게시 데이터베이스의 게시자에서 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-117">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
5.  <span data-ttu-id="0778d-118">각 구독자가 추적 프로그램 토큰을 받았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-118">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a><span data-ttu-id="0778d-119">피어 투 피어 트랜잭션 복제 토폴로지를 정지하려면</span><span class="sxs-lookup"><span data-stu-id="0778d-119">To quiesce a peer-to-peer transactional replication topology</span></span>  
  
1.  <span data-ttu-id="0778d-120">모든 노드에서 게시된 모든 테이블에 대한 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-120">Stop activity on all published tables at all nodes.</span></span>  
  
2.  <span data-ttu-id="0778d-121">토폴로지의 각 게시 데이터베이스에서 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-121">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on each publication database in the topology.</span></span>  
  
3.  <span data-ttu-id="0778d-122">로그 판독기 에이전트 또는 배포 에이전트가 연속 모드로 실행되지 않는 경우 해당 에이전트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-122">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="0778d-123">로그 판독기 에이전트는 배포 에이전트보다 먼저 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-123">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="0778d-124">에이전트 실행에 대한 자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) 또는 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0778d-124">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
4.  <span data-ttu-id="0778d-125">토폴로지의 각 게시 데이터베이스에서 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-125">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on each publication database in the topology.</span></span> <span data-ttu-id="0778d-126">결과 집합에 각각의 다른 노드에서 받은 응답이 들어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-126">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a><span data-ttu-id="0778d-127">피어 투 피어 노드가 이전의 모든 변경 내용을 받았는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="0778d-127">To ensure a peer-to-peer node has received all prior changes</span></span>  
  
1.  <span data-ttu-id="0778d-128">확인할 노드의 게시 데이터베이스에서 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-128">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on the publication database at the node you are checking.</span></span>  
  
2.  <span data-ttu-id="0778d-129">로그 판독기 에이전트 또는 배포 에이전트가 연속 모드로 실행되지 않는 경우 해당 에이전트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-129">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="0778d-130">로그 판독기 에이전트는 배포 에이전트보다 먼저 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-130">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="0778d-131">에이전트 실행에 대한 자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) 또는 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0778d-131">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="0778d-132">확인할 노드의 게시 데이터베이스에서 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-132">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on the publication database at the node you are checking.</span></span> <span data-ttu-id="0778d-133">결과 집합에 각각의 다른 노드에서 받은 응답이 들어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-133">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-quiesce-a-merge-replication-topology"></a><span data-ttu-id="0778d-134">병합 복제 토폴로지를 정지하려면</span><span class="sxs-lookup"><span data-stu-id="0778d-134">To quiesce a merge replication topology</span></span>  
  
1.  <span data-ttu-id="0778d-135">게시자 및 모든 구독자에서 게시된 모든 테이블에 대한 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-135">Stop activity on all published tables at the Publisher and at all Subscribers.</span></span>  
  
2.  <span data-ttu-id="0778d-136">각 구독에 대해 병합 에이전트를 두 번 실행합니다. 첫 번째 실행에서는 모든 구독을 동기화하고 두 번째 실행에서는 각 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-136">Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time.</span></span> <span data-ttu-id="0778d-137">이렇게 하면 모든 변경 내용이 모든 노드에 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-137">This ensures that all changes are replicated to all nodes.</span></span> <span data-ttu-id="0778d-138">에이전트 실행에 대한 자세한 내용은 [복제 에이전트 실행 파일 개념](../concepts/replication-agent-executables-concepts.md) 또는 [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0778d-138">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0778d-139">동기화 중 충돌이 발생하면 병합 에이전트를 두 번 실행한 후 충돌 해결에 필요한 변경 내용이 모든 노드에 전파되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0778d-139">If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0778d-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0778d-140">See Also</span></span>  
 <span data-ttu-id="0778d-141">[피어 투 피어 토폴로지 관리&#40;복제 Transact-SQL 프로그래밍&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="0778d-141">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="0778d-142">트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="0778d-142">Measure Latency and Validate Connections for Transactional Replication</span></span>](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
