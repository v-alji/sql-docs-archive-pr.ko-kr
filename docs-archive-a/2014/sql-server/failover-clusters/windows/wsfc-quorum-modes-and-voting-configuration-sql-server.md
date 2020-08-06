---
title: WSFC 쿼럼 모드 및 투표 구성(SQL Server) | Microsoft 문서
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
ms.assetid: ca0d59ef-25f0-4047-9130-e2282d058283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1d5ad992c59f252f485f2d65451a72f150bef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650547"
---
# <a name="wsfc-quorum-modes-and-voting-configuration-sql-server"></a><span data-ttu-id="13895-102">WSFC 쿼럼 모드 및 투표 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="13895-102">WSFC Quorum Modes and Voting Configuration (SQL Server)</span></span>
  <span data-ttu-id="13895-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 및 AlwaysOn FCI(장애 조치(Failover) 클러스터 인스턴스)는 모두 WSFC(Windows Server 장애 조치(Failover) 클러스터링)를 플랫폼 기술로 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-103">Both [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and AlwaysOn Failover Cluster Instances (FCI) take advantage of Windows Server Failover Clustering (WSFC) as a platform technology.</span></span>  <span data-ttu-id="13895-104">WSFC는 쿼럼 기반 방식을 사용하여 전반적인 클러스터 상태를 모니터링하고 노드 수준의 내결함성을 극대화합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-104">WSFC uses a quorum-based approach to monitoring overall cluster health and maximize node-level fault tolerance.</span></span> <span data-ttu-id="13895-105">AlwaysOn 고가용성 및 재해 복구 솔루션을 디자인하고 운영하고 문제를 해결하기 위해서는 WSFC 쿼럼 모드 및 노드 투표 구성의 기초를 이해하는 것이 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-105">A fundamental understanding of WSFC quorum modes and node voting configuration is very important to designing, operating, and troubleshooting your AlwaysOn high availability and disaster recovery solution.</span></span>  
  
 <span data-ttu-id="13895-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="13895-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="13895-107">쿼럼을 기준으로 클러스터 상태 검색</span><span class="sxs-lookup"><span data-stu-id="13895-107">Cluster Health Detection by Quorum</span></span>](#ClusterHealthDetectionbyQuorum)  
  
-   [<span data-ttu-id="13895-108">쿼럼 모드</span><span class="sxs-lookup"><span data-stu-id="13895-108">Quorum Modes</span></span>](#QuorumModes)  
  
-   [<span data-ttu-id="13895-109">투표 및 비투표 노드</span><span class="sxs-lookup"><span data-stu-id="13895-109">Voting and Non-Voting Nodes</span></span>](#VotingandNonVotingNodes)  
  
-   [<span data-ttu-id="13895-110">쿼럼 투표에 권장되는 조정</span><span class="sxs-lookup"><span data-stu-id="13895-110">Recommended Adjustments to Quorum Voting</span></span>](#RecommendedAdjustmentstoQuorumVoting)  
  
-   [<span data-ttu-id="13895-111">관련 작업</span><span class="sxs-lookup"><span data-stu-id="13895-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="13895-112">관련 내용</span><span class="sxs-lookup"><span data-stu-id="13895-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="cluster-health-detection-by-quorum"></a><a name="ClusterHealthDetectionbyQuorum"></a><span data-ttu-id="13895-113">쿼럼 별 클러스터 상태 검색</span><span class="sxs-lookup"><span data-stu-id="13895-113">Cluster Health Detection by Quorum</span></span>  
 <span data-ttu-id="13895-114">WSFC 클러스터의 각 노드는 주기적 하트비트 통신에 참여하여 노드의 상태를 다른 노드와 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-114">Each node in a WSFC cluster participates in periodic heartbeat communication to share the node's health status with the other nodes.</span></span> <span data-ttu-id="13895-115">응답하지 않는 노드는 오류 상태에 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-115">Unresponsive nodes are considered to be in a failed state.</span></span>  
  
 <span data-ttu-id="13895-116">WSFC 클러스터에서 *쿼럼* 노드 집합은 대부분의 투표 노드 및 미러링 모니터입니다.</span><span class="sxs-lookup"><span data-stu-id="13895-116">A *quorum* node set is a majority of the voting nodes and witnesses in the WSFC cluster.</span></span> <span data-ttu-id="13895-117">WSFC 클러스터의 전반적인 상태는 주기적 *쿼럼 득표*에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-117">The overall health and status of a WSFC cluster is determined by a periodic *quorum vote*.</span></span>  <span data-ttu-id="13895-118">쿼럼이 있으면 클러스터가 양호한 상태이고 노드 수준의 내결함성을 제공할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-118">The presence of a quorum means that the cluster is healthy and able to provide node-level fault tolerance.</span></span>  
  
 <span data-ttu-id="13895-119">쿼럼이 없으면 클러스터 상태가 정상이 아님을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-119">The absence of a quorum indicates that the cluster is not healthy.</span></span>  <span data-ttu-id="13895-120">장애 조치(failover)를 수행하는 주 노드에 대해 정상 상태의 보조 노드를 사용할 수 있는지 확인하려면 전반적인 WSFC 클러스터 상태가 유지 관리되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-120">Overall WSFC cluster health must be maintained in order to ensure that healthy secondary nodes are available for primary nodes to fail over to.</span></span>  <span data-ttu-id="13895-121">쿼럼 득표에 실패하면 WSFC 클러스터가 예방 조치로 오프라인으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-121">If the quorum vote fails, the WSFC cluster will be set offline as a precautionary measure.</span></span>  <span data-ttu-id="13895-122">이 경우 클러스터에 등록된 모든 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 중지될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-122">This will also cause all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instances registered with the cluster to be stopped.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13895-123">쿼럼 실패로 인해 WSFC 클러스터가 오프라인으로 설정된 경우 다시 온라인으로 설정하려면 수동으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-123">If a WSFC cluster is set offline because of quorum failure, manual intervention is required to bring it back online.</span></span>  
>   
>  <span data-ttu-id="13895-124">자세한 내용은 [강제 쿼럼을 통해 WSFC 재해 복구&#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-124">For more information, see: [WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).</span></span>  
  
##  <a name="quorum-modes"></a><a name="QuorumModes"></a><span data-ttu-id="13895-125">쿼럼 모드</span><span class="sxs-lookup"><span data-stu-id="13895-125">Quorum Modes</span></span>  
 <span data-ttu-id="13895-126">*쿼럼 모드* 는 쿼럼 투표에 사용되는 방법을 지시하는 WSFC 클러스터 수준에서 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-126">A *quorum mode* is configured at the WSFC cluster level that dictates the methodology used for quorum voting.</span></span>  <span data-ttu-id="13895-127">장애 조치(Failover) 클러스터 관리자 유틸리티는 클러스터의 노드 수에 따라 쿼럼 모드를 추천합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-127">The Failover Cluster Manager utility will recommend a quorum mode based on the number of nodes in the cluster.</span></span>  
  
 <span data-ttu-id="13895-128">다음 쿼럼 모드는 득표 쿼럼을 구성하는 요소를 결정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-128">The following quorum modes can be used to determine what constitutes a quorum of votes:</span></span>  
  
-   <span data-ttu-id="13895-129">**노드 과반수.**</span><span class="sxs-lookup"><span data-stu-id="13895-129">**Node Majority.**</span></span> <span data-ttu-id="13895-130">클러스터의 상태가 정상이 되려면 클러스터에 있는 투표 노드의 절반 이상이 찬성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-130">More than one-half of the voting nodes in the cluster must vote affirmatively for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="13895-131">**노드 및 파일 공유 과반수.**</span><span class="sxs-lookup"><span data-stu-id="13895-131">**Node and File Share Majority.**</span></span> <span data-ttu-id="13895-132">노드 과반수 쿼럼 모드와 유사하지만 원격 파일 공유도 투표 미러링 모니터로 구성되며 노드에서 해당 공유로의 연결도 찬성으로 계산된다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="13895-132">Similar to Node Majority quorum mode, except that a remote file share is also configured as a voting witness, and connectivity from any node to that share is also counted as an affirmative vote.</span></span>  <span data-ttu-id="13895-133">클러스터의 상태가 정상이 되려면 가능한 투표 수의 절반 이상이 찬성이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-133">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
     <span data-ttu-id="13895-134">미러링 모니터 파일 공유는 클러스터의 노드에 있지 않고 클러스터의 모든 노드에 표시되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-134">As a best practice, the witness file share should not reside on any node in the cluster, and it should be visible to all nodes in the cluster.</span></span>  
  
-   <span data-ttu-id="13895-135">**노드 및 디스크 과반수.**</span><span class="sxs-lookup"><span data-stu-id="13895-135">**Node and Disk Majority.**</span></span> <span data-ttu-id="13895-136">노드 과반수 쿼럼 모드와 유사하지만 공유 디스크 클러스터 리소스도 투표 미러링 모니터로 지정되며 노드에서 해당 공유 디스크로의 연결도 찬성으로 계산된다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="13895-136">Similar to Node Majority quorum mode, except that a shared disk cluster resource is also designated as a voting witness, and connectivity from any node to that shared disk is also counted as an affirmative vote.</span></span>  <span data-ttu-id="13895-137">클러스터의 상태가 정상이 되려면 가능한 투표 수의 절반 이상이 찬성이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-137">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="13895-138">**디스크만**</span><span class="sxs-lookup"><span data-stu-id="13895-138">**Disk Only.**</span></span> <span data-ttu-id="13895-139">공유 디스크 클러스터 리소스가 미러링 모니터로 지정되며 노드에서 해당 공유 디스크로의 연결이 찬성으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-139">A shared disk cluster resource is designated as a witness, and connectivity by any node to that shared disk is counted as an affirmative vote.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="13895-140">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 대해 비대칭 스토리지 구성을 사용할 때는 일반적으로 투표 노드의 수가 홀수인 경우 노드 과반수 쿼럼 모드를 사용하고 투표 노드의 수가 짝수인 경우 노드 및 파일 공유 과반수 쿼럼 모드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-140">When using an asymmetric storage configuration for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], you should generally use the Node Majority quorum mode when you have an odd number of voting nodes, or the Node and File Share Majority quorum mode when you have an even number of voting nodes.</span></span>  
  
##  <a name="voting-and-non-voting-nodes"></a><a name="VotingandNonVotingNodes"></a><span data-ttu-id="13895-141">투표 및 비 투표 노드</span><span class="sxs-lookup"><span data-stu-id="13895-141">Voting and Non-Voting Nodes</span></span>  
 <span data-ttu-id="13895-142">기본적으로 WSFC 클러스터의 각 노드는 클러스터 쿼럼의 멤버로 포함됩니다. 각 노드는 전반적인 클러스터 상태를 결정하는 데 하나의 투표권이 있으며 지속적으로 쿼럼을 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-142">By default, each node in the WSFC cluster is included as a member of the cluster quorum; each node has a single vote in determining the overall cluster health, and each node will continuously attempt to establish a quorum.</span></span>  <span data-ttu-id="13895-143">이 시점까지 쿼럼 토론은 클러스터 상태에 대해 투표하는 WSFC 클러스터 노드 집합을 *투표 노드*로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-143">The quorum discussion to this point has carefully qualified the set of WSFC cluster nodes that vote on cluster health as *voting nodes*.</span></span>  
  
 <span data-ttu-id="13895-144">WSFC 클러스터에는 전체 클러스터가 정상 상태인지 아닌지를 명확하게 결정할 수 있는 개별 노드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-144">No individual node in a WSFC cluster can definitively determine that the cluster as a whole is healthy or unhealthy.</span></span>  <span data-ttu-id="13895-145">모든 지정된 시점에서 다른 일부 노드는 각 노드의 큐브 뷰에서 오프라인으로 표시되거나, 장애 조치(failover)가 진행 중인 것으로 표시되거나, 네트워크 통신 오류로 인해 응답하지 않는 것으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-145">At any given moment, from the perspective of each node, some of the other nodes may appear to be offline, or appear to be in the process of failover, or appear unresponsive due to a network communication failure.</span></span>  <span data-ttu-id="13895-146">쿼럼 투표의 주요 기능은 WSFC 클러스터의 각 노드 표시 상태가 해당 노드의 실제 상태인지 여부를 결정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13895-146">A key function of the quorum vote is to determine whether the apparent state of each of node in the WSFC cluster is indeed that actual state of those nodes.</span></span>  
  
 <span data-ttu-id="13895-147">'디스크에만 해당'을 제외한 모든 쿼럼 모델의 경우 쿼럼 투표의 효과는 클러스터의 모든 투표 노드 간 안정적인 통신에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="13895-147">For all of the quorum models except 'Disk Only', the effectiveness of a quorum vote depends on reliable communications between all of the voting nodes in the cluster.</span></span> <span data-ttu-id="13895-148">동일한 물리적 서브넷에 있는 노드 간 네트워크 통신은 안정적인 것으로 간주되어야 하며 쿼럼 투표를 신뢰할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-148">Network communications between nodes on the same physical subnet should be considered reliable; the quorum vote should be trusted.</span></span>  
  
 <span data-ttu-id="13895-149">그러나 다른 서브넷에 있는 노드가 쿼럼 투표에 응답하지 않는 것으로 표시되지만 실제로 온라인 상태이고 정상 상태이면 이는 서브넷 사이에 네트워크 통신 오류가 발생했기 때문일 확률이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-149">However, if a node on another subnet is seen as non-responsive in a quorum vote, but it is actually online and otherwise healthy, that is most likely due to a network communications failure between subnets.</span></span>  <span data-ttu-id="13895-150">클러스터 토폴로지, 쿼럼 모드 및 장애 조치(Failover) 정책 구성에 따라 해당 네트워크 통신 오류는 사실상 두 개 이상의 투표 노드 집합(또는 하위 집합)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-150">Depending upon the cluster topology, quorum mode, and failover policy configuration, that network communications failure may effectively create more than one set (or subset) of voting nodes.</span></span>  
  
 <span data-ttu-id="13895-151">두 개 이상의 투표 노드 하위 집합이 자체적으로 쿼럼을 설정할 수 있는 경우 이를 *분리 장애(split-brain) 시나리오*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-151">When more than one subset of voting nodes is able to establish a quorum on its own, that is known as a *split-brain scenario*.</span></span>  <span data-ttu-id="13895-152">이러한 시나리오에서는 별도의 쿼럼에 있는 노드가 다른 노드와 다르게 동작하고 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-152">In such a scenario, the nodes in the separate quorums may behave differently, and in conflict with one another.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13895-153">분리 장애(split-brain) 시나리오는 시스템 관리자가 수동으로 쿼럼 작업이나 흔치 않게 장애 조치(Failover)를 강제로 수행하여 쿼럼 노드 집합을 명시적으로 분할하는 경우에만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-153">The split-brain scenario is only possible when a system administrator manually performs a forced quorum operation, or in very rare circumstances, a forced failover; explicitly subdividing the quorum node set.</span></span>  
  
 <span data-ttu-id="13895-154">쿼럼 구성을 단순화 하 고 시간을 늘리기 위해 노드의 응답이 쿼럼에 계산 되지 않도록 각 노드의 *Nodeweight* 설정을 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-154">In order to simplify your quorum configuration and increase up-time, you may want to adjust each node's *NodeWeight* setting so that the node's vote is not counted towards the quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13895-155">NodeWeight 설정을 사용하려면 WSFC 클러스터의 모든 서버에 다음 핫픽스를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-155">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="13895-156">[KB2494036](https://support.microsoft.com/kb/2494036): 및에서 쿼럼 응답이 없는 클러스터 노드를 구성 하는 데 사용할 수 있는 핫픽스 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)][!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13895-156">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
##  <a name="recommended-adjustments-to-quorum-voting"></a><a name="RecommendedAdjustmentstoQuorumVoting"></a><span data-ttu-id="13895-157">쿼럼 투표에 권장 되는 조정</span><span class="sxs-lookup"><span data-stu-id="13895-157">Recommended Adjustments to Quorum Voting</span></span>  
 <span data-ttu-id="13895-158">지정된 WSFC 노드의 투표를 사용하거나 사용하지 않도록 설정하는 경우 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="13895-158">When enabling or disabling a given WSFC node's vote, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="13895-159">**기본적으로 투표가 없습니다.**</span><span class="sxs-lookup"><span data-stu-id="13895-159">**No vote by default.**</span></span> <span data-ttu-id="13895-160">각 노드에서 명시적인 이유 없이 투표하지 않는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-160">Assume that each node should not vote without explicit justification.</span></span>  
  
-   <span data-ttu-id="13895-161">**모든 주 복제본을 포함합니다.**</span><span class="sxs-lookup"><span data-stu-id="13895-161">**Include all primary replicas.**</span></span> <span data-ttu-id="13895-162">가용성 그룹 주 복제본을 호스팅하거나 FCI의 기본 설정 소유자인 각 WSFC 노드에는 투표가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-162">Each WSFC node that hosts an availability group primary replica or is the preferred owner of an FCI should have a vote.</span></span>  
  
-   <span data-ttu-id="13895-163">**가능한 자동 장애 조치(Failover) 소유자를 포함합니다.**</span><span class="sxs-lookup"><span data-stu-id="13895-163">**Include possible automatic failover owners.**</span></span> <span data-ttu-id="13895-164">자동 가용성 그룹 장애 조치(Failover) 또는 FCI 장애 조치(Failover)로 인해 주 복제본을 호스팅할 수 있었던 각 노드에는 투표가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-164">Each node that could host a primary replica, as the result of an automatic availability group failover or FCI failover, should have a vote.</span></span> <span data-ttu-id="13895-165">WSFC 클러스터에 가용성 그룹이 하나만 있고 가용성 복제본이 독립 실행형 인스턴스에서만 호스팅되는 경우 이 규칙에는 자동 장애 조치(Failover) 대상인 보조 복제본만 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-165">If there is only one availability group in the WSFC cluster and availability replicas are hosted only by standalone instances, this rule includes only the secondary replica that is the automatic failover target.</span></span>  
  
-   <span data-ttu-id="13895-166">**보조 사이트 노드를 제외합니다.**</span><span class="sxs-lookup"><span data-stu-id="13895-166">**Exclude secondary site nodes.**</span></span> <span data-ttu-id="13895-167">일반적으로 보조 재해 복구 사이트에 있는 WSFC 노드에는 투표를 제공하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="13895-167">In general, do not give votes to WSFC nodes that reside at a secondary disaster recovery site.</span></span>  <span data-ttu-id="13895-168">주 사이트에 아무런 문제가 없는 경우 보조 사이트의 노드가 클러스터를 오프라인으로 전환하는 의사 결정에 영향을 주어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-168">You do not want nodes in the secondary site to contribute to a decision to take the cluster offline when there is nothing wrong with the primary site.</span></span>  
  
-   <span data-ttu-id="13895-169">**홀수 투표 수**</span><span class="sxs-lookup"><span data-stu-id="13895-169">**Odd number of votes.**</span></span> <span data-ttu-id="13895-170">필요한 경우 미러링 모니터 파일 공유, 미러링 모니터 노드 또는 미러링 모니터 디스크를 클러스터에 추가하고 쿼럼 투표가 동률이 되지 않도록 쿼럼 모드를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-170">If necessary, add a witness file share, a witness node, or a witness disk to the cluster and adjust the quorum mode to prevent possible ties in the quorum vote.</span></span>  
  
-   <span data-ttu-id="13895-171">**투표 할당 사후 장애 조치(Post-failover)를 다시 평가합니다.**</span><span class="sxs-lookup"><span data-stu-id="13895-171">**Re-assess vote assignments post-failover.**</span></span> <span data-ttu-id="13895-172">정상 상태의 쿼럼을 지원하지 않는 클러스터 구성에 대해 장애 조치(Failover)를 수행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-172">You do not want to fail over into a cluster configuration that does not support a healthy quorum.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13895-173">WSFC 쿼럼 득표 구성의 유효성을 검사할 때 다음 조건 중 하나가 충족되는 경우 AlwaysOn 가용성 그룹 마법사에 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13895-173">When validating WSFC quorum vote configuration, the AlwaysOn Availability Group Wizard shows a warning if any of the following conditions are true:</span></span>  
> 
>  -   <span data-ttu-id="13895-174">주 복제본을 호스팅하는 클러스터 노드에 투표가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-174">The cluster node that hosts the primary replica does not have a vote</span></span>  
> -   <span data-ttu-id="13895-175">보조 복제본이 자동 장애 조치(Failover)용으로 구성되고 해당 클러스터 노드에 투표가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-175">A secondary replica is configured for automatic failover and its cluster node does not have a vote.</span></span>  
> -   <span data-ttu-id="13895-176">가용성 복제본을 호스팅하는 모든 클러스터 노드에[KB2494036](https://support.microsoft.com/kb/2494036) 이 설치되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-176">[KB2494036](https://support.microsoft.com/kb/2494036) is not installed on all cluster nodes that host availability replicas.</span></span> <span data-ttu-id="13895-177">멀티 사이트 배포에 클러스터 노드에 대한 투표를 추가하거나 제거하려면 이 패치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-177">This patch is required to add or remove votes for cluster nodes in multi-site deployments.</span></span> <span data-ttu-id="13895-178">그러나 단일 사이트 배포에서는 주로 요구되지 않으며 경고를 무시해도 괜찮습니다.</span><span class="sxs-lookup"><span data-stu-id="13895-178">However, in single-site deployments, it is usually not required and you may safely ignore the warning.</span></span>  
> 
> [!TIP]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="13895-179">에서는 WSFC 클러스터 구성 및 노드 쿼럼 투표에 관련된 설정을 관리하는 데 도움이 되는 몇 가지 시스템 DMV(동적 관리 뷰)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13895-179">exposes several system dynamic management views (DMVs) that can help you manage settings related WSFC cluster configuration and node quorum voting.</span></span>  
> 
>  <span data-ttu-id="13895-180">자세한 내용은  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13895-180">For more information, see:  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="13895-181">관련 작업</span><span class="sxs-lookup"><span data-stu-id="13895-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="13895-182">클러스터 쿼럼 NodeWeight 설정 보기</span><span class="sxs-lookup"><span data-stu-id="13895-182">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="13895-183">클러스터 쿼럼 NodeWeight 설정 구성</span><span class="sxs-lookup"><span data-stu-id="13895-183">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="13895-184">관련 내용</span><span class="sxs-lookup"><span data-stu-id="13895-184">Related Content</span></span>  
  
-   [<span data-ttu-id="13895-185">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="13895-185">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="13895-186">AlwaysOn 가용성 그룹 마법사의 쿼럼 투표 구성 검사</span><span class="sxs-lookup"><span data-stu-id="13895-186">Quorum vote configuration check in AlwaysOn Availability Group Wizards</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/03/13/quorum-vote-configuration-check-in-alwayson-availability-group-wizards-andy-jing.aspx)  
  
-   <span data-ttu-id="13895-187">[Windows Server 기술: 장애 조치(failover) 클러스터](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="13895-187">[Windows Server Technologies:  Failover Clusters](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span></span>  
  
-   <span data-ttu-id="13895-188">[장애 조치(Failover) 클러스터 단계별 가이드: 장애 조치 클러스터에서 쿼럼 구성](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="13895-188">[Failover Cluster Step-by-Step Guide: Configuring the Quorum in a Failover Cluster](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13895-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13895-189">See Also</span></span>  
 <span data-ttu-id="13895-190">[강제 쿼럼을 통해 WSFC 재해 복구 &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="13895-190">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 [<span data-ttu-id="13895-191">SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;</span><span class="sxs-lookup"><span data-stu-id="13895-191">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
