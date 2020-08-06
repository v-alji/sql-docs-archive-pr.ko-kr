---
title: 쿼럼 없이 WSFC 클러스터 강제 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: 4a121375-7424-4444-b876-baefa8fe9015
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6f2110b706de015d0c7b19475b335908c118267
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650556"
---
# <a name="force-a-wsfc-cluster-to-start-without-a-quorum"></a><span data-ttu-id="bbfe1-102">쿼럼 없이 WSFC 클러스터 강제 시작</span><span class="sxs-lookup"><span data-stu-id="bbfe1-102">Force a WSFC Cluster to Start Without a Quorum</span></span>
  <span data-ttu-id="bbfe1-103">이 항목에서는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 클러스터 노드를 쿼럼 없이 강제로 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-103">This topic describes how to force a Windows Server Failover Clustering (WSFC) cluster node to start without a quorum.</span></span>  <span data-ttu-id="bbfe1-104">이 기능은 재해 복구 및 다중 서브넷 시나리오에서 데이터를 복구하고 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스의 고가용성을 완전히 다시 설정하는 데 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-104">This may be required in disaster recovery and multi-subnet scenarios to recover data and fully re-establish high-availability for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="bbfe1-105">**시작하기 전 주의 사항:**  [권장 사항](#Recommendations), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-105">**Before you start:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="bbfe1-106">**다음을 사용하여 쿼럼 없이 클러스터를 강제 시작하려면**  [장애 조치(Failover) 클러스터 관리자 사용](#FailoverClusterManagerProcedure), [Powershell 사용](#PowerShellProcedure), [Net.exe 사용](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-106">**To force a cluster to start without a quorum using:**  [Using Failover Cluster Manager](#FailoverClusterManagerProcedure), [Using Powershell](#PowerShellProcedure), [Using Net.exe](#CommandPromptProcedure)</span></span>  
  
-   <span data-ttu-id="bbfe1-107">**후속 작업:**  [후속 작업: 쿼럼 없이 클러스터를 강제로 시작한 후의 작업](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-107">**Follow up:**  [Follow Up: After Forcing Cluster to Start without a Quorum](#FollowUp)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bbfe1-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bbfe1-108">Before You Start</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="bbfe1-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="bbfe1-109">Recommendations</span></span>  
 <span data-ttu-id="bbfe1-110">명시적으로 지정된 경우를 제외하고 이 항목의 절차는 WSFC 클러스터의 노드에서 실행할 경우에 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-110">Except where explicitly directed, the procedures in this topic should work if you execute them from any node in the WSFC cluster.</span></span>  <span data-ttu-id="bbfe1-111">그러나 쿼럼 없이 강제로 시작할 노드에서 이러한 단계를 실행하면 보다 나은 결과를 얻고 네트워킹 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-111">However, you may obtain better results, and avoid networking issues, by executing these steps from the node that you intend to force to start without a quorum.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bbfe1-112">보안</span><span class="sxs-lookup"><span data-stu-id="bbfe1-112">Security</span></span>  
 <span data-ttu-id="bbfe1-113">사용자는 WSFC 클러스터의 각 노드에 대한 로컬 Administrators 그룹의 멤버인 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-113">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-failover-cluster-manager"></a><a name="FailoverClusterManagerProcedure"></a> <span data-ttu-id="bbfe1-114">장애 조치(Failover) 클러스터 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="bbfe1-114">Using Failover Cluster Manager</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="bbfe1-115">쿼럼 없이 클러스터를 강제로 시작하려면</span><span class="sxs-lookup"><span data-stu-id="bbfe1-115">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="bbfe1-116">장애 조치(Failover) 클러스터 관리자를 열고 온라인으로 강제 전환할 클러스터 노드에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-116">Open a Failover Cluster Manager and connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="bbfe1-117">**작업** 창에서 **클러스터 강제 시작**을 클릭 하 고 **예. 클러스터를 강제로 시작**합니다 .를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-117">In the **Actions** pane, click **Force Cluster Start**, and then click **Yes - Force my cluster to start**.</span></span>  
  
3.  <span data-ttu-id="bbfe1-118">왼쪽 창의 **장애 조치(Failover) 클러스터 관리자** 트리에서 클러스터 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-118">In the left pane, in the **Failover Cluster Manager** tree, click the cluster name.</span></span>  
  
4.  <span data-ttu-id="bbfe1-119">요약 창에서 현재 **쿼럼 구성** 값이  **경고: 클러스터가 ForceQuorum 상태에서 실행 중입니다.** 인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-119">In the summary pane, confirm that the current **Quorum Configuration** value is:  **Warning: Cluster is running in ForceQuorum state**.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="bbfe1-120">Powershell 사용</span><span class="sxs-lookup"><span data-stu-id="bbfe1-120">Using Powershell</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="bbfe1-121">쿼럼 없이 클러스터를 강제로 시작하려면</span><span class="sxs-lookup"><span data-stu-id="bbfe1-121">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="bbfe1-122">**관리자 권한으로 실행**을 통해 승격된 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-122">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="bbfe1-123">클러스터 commandlet을 사용할 수 있도록 `FailoverClusters` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-123">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="bbfe1-124">`Stop-ClusterNode` 를 사용하여 클러스터 서비스가 중지되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-124">Use `Stop-ClusterNode` to make sure that the cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="bbfe1-125">`Start-ClusterNode` 와 `-FixQuorum` 을 사용하여 클러스터 서비스를 강제로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-125">Use `Start-ClusterNode` with `-FixQuorum` to force the cluster service to start.</span></span>  
  
5.  <span data-ttu-id="bbfe1-126">`Get-ClusterNode` 와 `-Propery NodeWieght = 1` 을 사용하여 노드가 쿼럼의 투표 멤버가 되도록 하는 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-126">Use `Get-ClusterNode` with `-Propery NodeWieght = 1` to set the value the guarantees that the node is a voting member of the quorum.</span></span>  
  
6.  <span data-ttu-id="bbfe1-127">클러스터 노드 속성을 읽기 가능한 형식으로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-127">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="bbfe1-128">예(Powershell)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-128">Example (Powershell)</span></span>  
 <span data-ttu-id="bbfe1-129">다음 예에서는 쿼럼 없이 AlwaysOnSrv02 노드 클러스터 서비스를 강제로 시작하고 `NodeWeight = 1`로 설정한 다음 새 강제 시작 노드의 클러스터 노드 상태를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-129">The following example forces the AlwaysOnSrv02 node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv02"  
Stop-ClusterNode -Name $node  
Start-ClusterNode -Name $node -FixQuorum  
  
(Get-ClusterNode $node).NodeWeight = 1  
  
$nodes = Get-ClusterNode -Cluster $node  
$nodes | Format-Table -property NodeName, State, NodeWeight
```  
  
##  <a name="using-netexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="bbfe1-130">Net.exe 사용</span><span class="sxs-lookup"><span data-stu-id="bbfe1-130">Using Net.exe</span></span>  
  
### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="bbfe1-131">쿼럼 없이 클러스터를 강제로 시작하려면</span><span class="sxs-lookup"><span data-stu-id="bbfe1-131">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="bbfe1-132">원격 데스크톱을 사용하여 온라인으로 강제 전환할 클러스터 노드에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-132">Use Remote Desktop to connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="bbfe1-133">**관리자 권한으로 실행**을 통해 승격된 명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-133">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
3.  <span data-ttu-id="bbfe1-134">**net.exe** 를 사용하여 로컬 클러스터 서비스가 중지되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-134">Use **net.exe** to make sure that the local cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="bbfe1-135">**net.exe** 와 `/forcequorum` 을 사용하여 로컬 클러스터 서비스를 강제로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-135">Use **net.exe** with `/forcequorum` to force the local cluster service to start.</span></span>  
  
### <a name="example-netexe"></a><span data-ttu-id="bbfe1-136">예(Net.exe)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-136">Example (Net.exe)</span></span>  
 <span data-ttu-id="bbfe1-137">다음 예에서는 쿼럼 없이 노드 클러스터 서비스를 강제로 시작하고 `NodeWeight = 1`로 설정한 다음 새 강제 시작 노드의 클러스터 노드 상태를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-137">The following example forces a node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```cmd
net.exe stop clussvc  
net.exe start clussvc /forcequorum  
```  
  
##  <a name="follow-up-after-forcing-cluster-to-start-without-a-quorum"></a><a name="FollowUp"></a><span data-ttu-id="bbfe1-138">후속 작업: 쿼럼 없이 클러스터를 강제로 시작한 후의 작업</span><span class="sxs-lookup"><span data-stu-id="bbfe1-138">Follow Up: After Forcing Cluster to Start without a Quorum</span></span>  
  
-   <span data-ttu-id="bbfe1-139">다른 노드를 다시 온라인으로 전환하려면 먼저 NodeWeight 값을 다시 계산하고 다시 구성하여 새 쿼럼을 올바르게 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-139">You must re-evaluate and reconfigure NodeWeight values to correctly construct a new quorum before bringing other nodes back online.</span></span> <span data-ttu-id="bbfe1-140">그러지 않으면 클러스터가 다시 오프라인으로 전환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-140">Otherwise, the cluster may go back offline again.</span></span>  
  
     <span data-ttu-id="bbfe1-141">자세한 내용은 [WSFC 쿼럼 모드 및 투표 구성&#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-141">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="bbfe1-142">이 항목의 절차에서는 계획되지 않은 쿼럼 오류가 발생한 경우 WSFC 클러스터를 다시 온라인으로 전환하는 단계만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-142">The procedures in this topic are only one step in bringing the WSFC cluster back online if an un-planned quorum failure were to occur.</span></span>  <span data-ttu-id="bbfe1-143">추가 단계를 통해 다른 WSFC 클러스터 노드가 새 쿼럼 구성에 방해가 되지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-143">You may also want to take additional steps to prevent other WSFC cluster nodes from interfering with the new quorum configuration.</span></span>  
  
-   <span data-ttu-id="bbfe1-144">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , 데이터베이스 미러링, 로그 전달 등의 다른 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]기능에는 데이터를 복구하고 고가용성을 완전히 다시 설정하기 위한 후속 동작도 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbfe1-144">Other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features such as [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], database mirroring, and log shipping may also require subsequent actions to recover data and to fully re-establish high-availability.</span></span>  
  
     <span data-ttu-id="bbfe1-145">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="bbfe1-145">**For more information:**</span></span>  
  
     [<span data-ttu-id="bbfe1-146">가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bbfe1-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
     [<span data-ttu-id="bbfe1-147">데이터베이스 미러링 세션에 서비스 강제 수행&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bbfe1-147">Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](../../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
  
     [<span data-ttu-id="bbfe1-148">로그 전달 보조 데이터베이스로 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bbfe1-148">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="bbfe1-149">관련 내용</span><span class="sxs-lookup"><span data-stu-id="bbfe1-149">Related Content</span></span>  
  
-   <span data-ttu-id="bbfe1-150">[장애 조치(Failover) 클러스터에 대한 이벤트 및 로그 보기](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="bbfe1-150">[View Events and Logs for a Failover Cluster](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span></span>  
  
-   [<span data-ttu-id="bbfe1-151">Get-ClusterLog 장애 조치(Failover) 클러스터 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bbfe1-151">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="bbfe1-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbfe1-152">See Also</span></span>  
 <span data-ttu-id="bbfe1-153">[강제 쿼럼을 통해 WSFC 재해 복구 &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bbfe1-153">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 <span data-ttu-id="bbfe1-154">[클러스터 쿼럼 NodeWeight 설정 구성](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="bbfe1-154">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="bbfe1-155">[태스크 기준으로 나열된 Windows PowerShell의 장애 조치(failover) 클러스터 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bbfe1-155">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
