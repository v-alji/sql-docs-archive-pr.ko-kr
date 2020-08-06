---
title: 쿼럼 강제를 통해 WSFC 재해 복구(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c9399472c6e67c9e2121a008f9283ba05943da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650548"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a><span data-ttu-id="2abb1-102">강제 쿼럼을 통해 WSFC 재해 복구(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2abb1-102">WSFC Disaster Recovery through Forced Quorum (SQL Server)</span></span>
  <span data-ttu-id="2abb1-103">쿼럼 실패는 일반적으로 시스템 관련 재해나, 지속적인 통신 오류 또는 WSFC 클러스터의 여러 노드와 관련된 잘못된 구성으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-103">Quorum failure is usually caused by a systemic disaster, or a persistent communications failure, or a misconfiguration involving several nodes in the WSFC cluster.</span></span>  <span data-ttu-id="2abb1-104">쿼럼 실패에서 복구하려면 수동 개입이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-104">Manual intervention is required to recovery from a quorum failure.</span></span>  
  
-   <span data-ttu-id="2abb1-105">**시작하기 전 주의 사항:**  [필수 구성 요소](#Prerequisites), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="2abb1-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="2abb1-106">**강제 쿼럼 절차를 통해 WSFC 재해 복구** [강제 쿼럼 절차를 통해 WSFC 재해 복구](#Main)</span><span class="sxs-lookup"><span data-stu-id="2abb1-106">**WSFC Disaster Recovery through the Forced Quorum Procedure** [WSFC Disaster Recovery through the Forced Quorum Procedure](#Main)</span></span>  
  
-   [<span data-ttu-id="2abb1-107">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2abb1-107">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="2abb1-108">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2abb1-108">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2abb1-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2abb1-109">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="2abb1-110">필수 조건</span><span class="sxs-lookup"><span data-stu-id="2abb1-110">Prerequisites</span></span>  
 <span data-ttu-id="2abb1-111">강제 쿼럼 절차는 쿼럼 실패 전에 정상 상태의 쿼럼이 있었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-111">The Forced Quorum Procedure assumes that a healthy quorum existed before the quorum failure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2abb1-112">사용자는 Windows Server 장애 조치(Failover) 클러스터링, WSFC 쿼럼 모델, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]및 환경의 특정 배포 구성에 대한 개념 및 상호 작용에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-112">The user should be well-informed on the concepts and interactions of Windows Server Failover Clustering, WSFC Quorum Models, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the environment's specific deployment configuration.</span></span>  
>   
>  <span data-ttu-id="2abb1-113">자세한 내용은  [SQL Server의 WSFC(Windows Server 장애 조치(failover) 클러스터링)](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC 쿼럼 모드 및 투표 구성(SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2abb1-113">For more information, see:  [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC Quorum Modes and Voting Configuration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2abb1-114">보안</span><span class="sxs-lookup"><span data-stu-id="2abb1-114">Security</span></span>  
 <span data-ttu-id="2abb1-115">사용자는 WSFC 클러스터의 각 노드에 대한 로컬 Administrators 그룹의 멤버인 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="wsfc-disaster-recovery-through-the-forced-quorum-procedure"></a><a name="Main"></a> <span data-ttu-id="2abb1-116">강제 쿼럼 절차를 통해 WSFC 재해 복구</span><span class="sxs-lookup"><span data-stu-id="2abb1-116">WSFC Disaster Recovery through the Forced Quorum Procedure</span></span>  
 <span data-ttu-id="2abb1-117">클러스터는 그 구성에 따라 노드 수준의 내결함성을 보장할 수 없기 때문에 쿼럼 실패가 발생하면 WSFC 클러스터의 클러스터형 서비스, SQL Server 인스턴스 및 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]이 모두 오프라인 상태로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-117">Remember that quorum failure will cause all clustered services, SQL Server instances, and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], in the WSFC cluster to be set offline, because the cluster, as configured, cannot ensure node-level fault tolerance.</span></span>  <span data-ttu-id="2abb1-118">쿼럼 실패란 WSFC 클러스터의 정상적인 투표 노드가 더 이상 쿼럼 모델을 충족하지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-118">A quorum failure means that healthy voting nodes in the WSFC cluster no longer satisfy the quorum model.</span></span> <span data-ttu-id="2abb1-119">일부 노드는 완전히 실패했을 수 있고 나머지 일부 노드는 WSFC 서비스만 종료했으며 쿼럼과의 통신 기능이 손실되었다는 점을 제외하고는 정상일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-119">Some nodes may have failed completely, and some may have just shut down the WSFC service and are otherwise healthy, except for the loss of the ability to communicate with a quorum.</span></span>  
  
 <span data-ttu-id="2abb1-120">WSFC 클러스터를 다시 온라인 상태로 전환하려면 기존 구성에서 쿼럼 실패의 근본 원인을 해결하고 필요한 경우 영향을 받은 데이터베이스를 복구해야 하며 실패에서 살아남은 클러스터 토폴로지를 반영하도록 WSFC 클러스터의 나머지 노드를 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-120">To bring the WSFC cluster back online, you must correct the root cause of the quorum failure under the existing configuration, recover the affected databases as needed, and you may want to reconfigure the remaining nodes in the WSFC cluster to reflect the surviving cluster topology.</span></span>  
  
 <span data-ttu-id="2abb1-121">클러스터를 오프라인 상태로 전환한 보안 장치를 무시하기 위해 WSFC 클러스터 노드에서 *강제 쿼럼* 절차를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-121">You can use the *forced quorum* procedure on a WSFC cluster node to override the safety controls that took the cluster offline.</span></span>  <span data-ttu-id="2abb1-122">이 경우 클러스터에서 쿼럼 투표 검사가 일시 중지되어 클러스터의 모든 노드에서 WSFC 클러스터 리소스 및 SQL Server를 다시 온라인 상태로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-122">This effectively tells the cluster to suspend the quorum voting checks, and lets you bring the WSFC cluster resources and SQL Server back online on any of the nodes in the cluster.</span></span>  
  
 <span data-ttu-id="2abb1-123">이 유형의 재해 복구 프로세스에는 다음 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-123">This type of disaster recovery process should include the following steps:</span></span>  
  
#### <a name="to-recover-from-quorum-failure"></a><span data-ttu-id="2abb1-124">쿼럼 실패에서 복구하려면</span><span class="sxs-lookup"><span data-stu-id="2abb1-124">To Recover from Quorum Failure:</span></span>  
  
1.  <span data-ttu-id="2abb1-125">**실패의 범위 확인.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-125">**Determine the scope of the failure.**</span></span> <span data-ttu-id="2abb1-126">응답하지 않는 가용성 그룹 또는 SQL Server 인스턴스, 온라인 상태이며 재해 발생 후 사용이 가능한 클러스터 노드를 식별하고 Windows 이벤트 로그와 SQL Server 시스템 로그를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-126">Identify which availability groups or SQL Server instances are non-responsive, which cluster nodes are online and available for post-disaster use, and examine the Windows event logs and the SQL Server system logs.</span></span>  <span data-ttu-id="2abb1-127">필요한 경우 향후 분석을 위해 조사한 데이터와 시스템 로그를 보존해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-127">Where practical, you should preserve forensic data and system logs for later analysis.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2abb1-128">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 응답 인스턴스에서는 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) DMV(동적 관리 뷰)를 쿼리하여 로컬 서버 인스턴스에서 가용성 복제본을 처리하는 가용성 그룹의 상태 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-128">On a responsive instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can obtain information about the health of availability groups that possess an availability replica on the local server instance by querying the [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) dynamic management view (DMV).</span></span>  
  
2.  <span data-ttu-id="2abb1-129">**단일 노드에서 강제 쿼럼을 수행하여 WSFC 클러스터 시작.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-129">**Start the WSFC cluster by using forced quorum on a single node.**</span></span> <span data-ttu-id="2abb1-130">WSFC 클러스터 서비스가 종료된 노드 이외의 노드 중에서 구성 요소 오류 수가 가장 적은 노드를 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-130">Identify a node with a minimal number of component failures, other than that the WSFC cluster service was shut down.</span></span>  <span data-ttu-id="2abb1-131">이 노드가 대부분의 다른 노드와 통신할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-131">Verify that this node can communicate with a majority of the other nodes.</span></span>  
  
     <span data-ttu-id="2abb1-132">이 노드에서 강제 쿼럼 절차를 수행하여 수동으로 클러스터를 온라인 상태로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-132">On this node, manually force the cluster to come online using the forced quorum procedure.</span></span>  <span data-ttu-id="2abb1-133">데이터 손실 위험을 최소화하려면 가용성 그룹 주 복제본을 마지막으로 호스팅한 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-133">To minimize potential data loss, select a node that was last hosting an availability group primary replica.</span></span>  
  
     <span data-ttu-id="2abb1-134">자세한 내용은  [쿼럼 없이 WSFC 클러스터 강제 시작](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2abb1-134">For more information, see:  [Force a WSFC Cluster to Start Without a Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2abb1-135">강제 쿼럼 설정은 클러스터 전반에 영향을 주어 논리적 WSFC 클러스터가 과반수의 투표를 확보하고 자동으로 정상 쿼럼 작업 모드로 전환될 때까지 쿼럼 검사를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-135">The forced quorum setting has a cluster-wide affect to block quorum checks until the logical WSFC cluster achieves a majority of votes and automatically transitions to a regular quorum mode of operation.</span></span>  
  
3.  <span data-ttu-id="2abb1-136">**각 정상 노드에서 한 번에 하나씩 WSFC 서비스 시작.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-136">**Start the WSFC service normally on each otherwise healthy node, one at a time.**</span></span> <span data-ttu-id="2abb1-137">다른 노드에서 클러스터 서비스를 시작할 때는 강제 쿼럼 옵션을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-137">You do not have to specify the forced quorum option when you start the cluster service on the other nodes.</span></span>  
  
     <span data-ttu-id="2abb1-138">각 노드에서 WSFC 서비스가 온라인 상태로 전환되면 서비스는 다른 정상 노드와 협상하여 새 클러스터 구성 상태를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-138">As the WSFC service on each node comes back online, it negotiates with the other healthy nodes to synchronize the new cluster configuration state.</span></span>  <span data-ttu-id="2abb1-139">이 작업은 마지막으로 알려진 클러스터 상태 해결과 관련된 경합 상태를 방지하기 위해 한 번에 한 노드에서 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-139">Remember to do this one node at a time to prevent potential race conditions in resolving the last known state of the cluster.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2abb1-140">시작하는 각 노드가 새로 온라인 상태로 전환된 다른 노드와 통신할 수 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2abb1-140">Ensure that each node that you start can communicate with the other newly online nodes.</span></span>  <span data-ttu-id="2abb1-141">다른 노드에서 WSFC 서비스를 비활성화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-141">Consider disabling the WSFC service on the other nodes.</span></span>  <span data-ttu-id="2abb1-142">그렇지 않으면 쿼럼 노드 집합이 둘 이상 만들어져 분리 장애(split-brain) 시나리오가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-142">Otherwise,  you run the risk of creating more than one quorum node set; that is a split-brain scenario.</span></span> <span data-ttu-id="2abb1-143">1단계에서 조사한 내용이 정확하면 이러한 일이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-143">If your findings in step 1 were accurate, this should not occur.</span></span>  
  
4.  <span data-ttu-id="2abb1-144">**새 쿼럼 모드 및 노드 투표 구성 적용.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-144">**Apply new quorum mode and node vote configuration.**</span></span> <span data-ttu-id="2abb1-145">쿼럼을 강제로 실행하여 클러스터의 모든 노드를 성공적으로 다시 시작했으며 쿼럼 실패의 근본 원인을 해결한 경우 원래 쿼럼 모드 및 노드 투표 구성을 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-145">If forcing quorum successfully restarted all the nodes in the cluster and the root cause of the quorum failure has been corrected, changes to the original quorum mode and node vote configuration are unnecessary.</span></span>  
  
     <span data-ttu-id="2abb1-146">그렇지 않은 경우에는 새로 복구한 클러스터 노드와 가용성 복제본 토폴로지를 평가하여 각 노드의 쿼럼 모드 및 투표 수 할당을 적절히 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-146">Otherwise, you should evaluate the newly recovered cluster node and availability replica topology, and change the quorum mode and vote assignments for each node as appropriate.</span></span> <span data-ttu-id="2abb1-147">복구되지 않은 노드의 경우 오프라인으로 설정하거나 해당 노드의 투표 수를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-147">Un-recovered nodes should be set offline or have their node votes set to zero.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2abb1-148">이때 클러스터의 노드 및 SQL Server 인스턴스 수는 정상 작동할 때의 수로 복원된 것으로 나타나지만</span><span class="sxs-lookup"><span data-stu-id="2abb1-148">At this point, the nodes and SQL Server instances in the cluster may appear to be restored back to regular operation.</span></span>  <span data-ttu-id="2abb1-149">정상 상태의 쿼럼은 아직 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-149">However, a healthy quorum may still not exist.</span></span>  <span data-ttu-id="2abb1-150">장애 조치(Failover) 클러스터 관리자, SQL Server Management Studio의 AlwaysOn 대시보드 또는 적절한 DMV를 사용하여 쿼럼이 복원되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2abb1-150">Using the Failover Cluster Manager, or the AlwaysOn Dashboard within SQL Server Management Studio, or the appropriate DMVs, verify that a quorum has been restored.</span></span>  
  
5.  <span data-ttu-id="2abb1-151">**필요한 경우 가용성 그룹 데이터베이스 복제본 복구.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-151">**Recover availability group database replicas as needed.**</span></span> <span data-ttu-id="2abb1-152">가용성 그룹 데이터베이스 이외 데이터베이스는 일반 SQL Server 시작 프로세스의 일부로 자체적으로 복구되고 온라인 상태로 전환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-152">Non-availability group databases should recover and come back online on their own as part of the regular SQL Server startup process.</span></span>  
  
     <span data-ttu-id="2abb1-153">주 복제본, 동기 보조 복제본, 비동기 보조 복제본의 순서로 가용성 그룹 복제본을 다시 온라인 상태로 전환하여 데이터 손실 위험 및 복구 시간을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-153">You can minimize potential data loss and recovery time for the availability group replicas by bringing them back online in this sequence:  primary replica, synchronous secondary replicas, asynchronous secondary replicas.</span></span>  
  
6.  <span data-ttu-id="2abb1-154">**실패한 구성 요소 복구 또는 교체 후 클러스터에 대해 유효성 검사 다시 수행.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-154">**Repair or replace failed components and re-validate cluster.**</span></span> <span data-ttu-id="2abb1-155">이제 초기 재해 및 쿼럼 실패에서 복구했으므로 실패한 노드를 복구 또는 교체하고 관련 WSFC 및 AlwaysOn 구성을 적절히 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-155">Now that you have recovered from the initial disaster and quorum failure, you should repair or replace the failed nodes and adjust related WSFC and AlwaysOn configurations accordingly.</span></span>  <span data-ttu-id="2abb1-156">여기에는 가용성 그룹 복제본을 삭제하고, 노드를 클러스터에서 제거하고, 노드에서 소프트웨어를 정리하고 다시 설치하는 작업이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-156">This can include dropping availability group replicas, evicting nodes from the cluster, or flattening and re-installing software on a node.</span></span>  
  
     <span data-ttu-id="2abb1-157">실패한 가용성 복제본을 모두 복구하거나 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-157">You must repair or remove all failed availability replicas.</span></span>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="2abb1-158">는 가용성 복제본의 마지막으로 알려진 가장 오래된 시점 이후의 트랜잭션 로그를 자르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-158">will not truncate the transaction log past the last known point of the farthest behind availability replica.</span></span>   <span data-ttu-id="2abb1-159">실패한 복제본을 복구하거나 가용성 그룹에서 제거하지 않으면 트랜잭션 로그 크기가 계속 증가하여 다른 복제본의 트랜잭션 로그 공간이 부족해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-159">If a failed replica is not repaired or removed from the availability group, the transaction logs will grow and you will run the risk of running out of transaction log space on the other replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2abb1-160">가용성 그룹 수신기가 WSFC 클러스터에 있을 때 WSFC 구성 유효성 검사 마법사를 실행하면 마법사가 다음과 같이 잘못된 경고 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-160">If you run the WSFC Validate a Configuration Wizard when an availability group listener exists on the WSFC cluster, the wizard generates the following incorrect warning message:</span></span>  
    >   
    >  <span data-ttu-id="2abb1-161">“네트워크 이름 'Name:<network_name>'의 RegisterAllProviderIP 속성이 1로 설정되어 있습니다. 현재 클러스터 구성에서는 이 값을 0으로 설정해야 합니다.”</span><span class="sxs-lookup"><span data-stu-id="2abb1-161">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="2abb1-162">이 메시지는 무시하세요.</span><span class="sxs-lookup"><span data-stu-id="2abb1-162">Please ignore this message.</span></span>  
  
7.  <span data-ttu-id="2abb1-163">**필요한 경우 4단계 반복.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-163">**Repeat step 4 as needed.**</span></span> <span data-ttu-id="2abb1-164">이 작업의 목표는 정상적인 작동을 위해 적절한 수준의 내결함성 및 고가용성을 다시 설정하는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-164">The goal is to re-establish the appropriate level of fault tolerance and high availability for healthy operations.</span></span>  
  
8.  <span data-ttu-id="2abb1-165">**RPO/RTO 분석 실시.**</span><span class="sxs-lookup"><span data-stu-id="2abb1-165">**Conduct RPO/RTO analysis.**</span></span> <span data-ttu-id="2abb1-166">SQL Server 시스템 로그, 데이터베이스 타임스탬프 및 Windows 이벤트 로그를 분석하여 실패의 근본 원인을 파악하고 실제 복구 지점 및 복구 시간 방법을 문서화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2abb1-166">You should analyze SQL Server system logs, database timestamps, and Windows event logs to determine root cause of the failure, and to document actual recovery point and recovery time experiences.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2abb1-167">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2abb1-167">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2abb1-168">쿼럼 없이 WSFC 클러스터 강제 시작</span><span class="sxs-lookup"><span data-stu-id="2abb1-168">Force a WSFC Cluster to Start Without a Quorum</span></span>](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [<span data-ttu-id="2abb1-169">가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2abb1-169">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="2abb1-170">클러스터 쿼럼 NodeWeight 설정 보기</span><span class="sxs-lookup"><span data-stu-id="2abb1-170">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="2abb1-171">클러스터 쿼럼 NodeWeight 설정 구성</span><span class="sxs-lookup"><span data-stu-id="2abb1-171">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="2abb1-172">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2abb1-172">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="2abb1-173">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2abb1-173">Related Content</span></span>  
  
-   <span data-ttu-id="2abb1-174">[장애 조치(Failover) 클러스터에 대한 이벤트 및 로그 보기](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2abb1-174">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="2abb1-175">Get-ClusterLog 장애 조치(Failover) 클러스터 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2abb1-175">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="2abb1-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2abb1-176">See Also</span></span>  
 [<span data-ttu-id="2abb1-177">SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;</span><span class="sxs-lookup"><span data-stu-id="2abb1-177">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
