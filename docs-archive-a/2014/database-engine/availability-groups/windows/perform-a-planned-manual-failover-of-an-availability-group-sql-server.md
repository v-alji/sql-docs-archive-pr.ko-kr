---
title: 가용성 그룹의 계획된 수동 장애 조치(Failover) 수행(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c62942eaa8f4ab4472bca5c7123e5999eb069216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734472"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a><span data-ttu-id="7cad7-102">가용성 그룹의 계획된 수동 장애 조치(Failover) 수행(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7cad7-102">Perform a Planned Manual Failover of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="7cad7-103"> 이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 데이터 손실 없이 수동 장애 조치(Failover)를 수행하는 방법(*계획된 수동 장애 조치(Failover)*)에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-103">This topic describes how to perform a manual failover without data loss (a *planned manual failover*) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7cad7-104">가용성 그룹은 가용성 복제본의 수준에서 장애 조치(Failover)됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="7cad7-105">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 장애 조치(failover)와 같은 계획 수동 장애 조치(failover)를 수행하면 보조 복제본이 주 역할로 전환되며 동시에 이전 주 복제본은 보조 역할로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-105">A planned manual failover, like any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] failover, transitions a secondary replica to primary role and, concurrently, transitions the former primary replica to the secondary role.</span></span>  
  
 <span data-ttu-id="7cad7-106">주 복제본과 대상 보조 복제본이 동기-커밋 모드에서 실행 중이고 현재 동기화된 경우에만 지원되는 계획 수동 장애 조치(failover)는 대상 보조 복제본의 가용성 그룹에 조인되는 보조 데이터베이스에서 모든 데이터를 보존합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-106">A planned manual failover, which is supported only when the primary replica and the target secondary replica are running in synchronous-commit mode and are currently synchronized, preserves all the data in the secondary databases that are joined to the availability group on the target secondary replica.</span></span> <span data-ttu-id="7cad7-107">이전 주 복제본이 보조 역할로 전환되면 해당 데이터베이스는 보조 데이터베이스가 되고 새로운 주 데이터베이스와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-107">Once the former primary replica transitions to the secondary role, its databases become secondary databases and begin synchronizing with the new primary databases.</span></span> <span data-ttu-id="7cad7-108">데이터베이스가 모두 SYNCHRONIZED 상태로 전환된 후 새로운 보조 복제본은 향후 계획 수동 장애 조치(failover)의 대상 역할을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-108">After they all transition into the SYNCHRONIZED state, the new secondary replica becomes eligible to serve as the target of a future planned manual failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7cad7-109">보조 복제본과 주 복제본이 모두 자동 장애 조치(failover) 모드에 대해 구성된 경우 보조 복제본이 동기화되면 자동 장애 조치(failover)의 대상 역할도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-109">If the secondary and primary replicas are both configured for automatic failover mode, once the secondary replica is synchronized, it can also serve as the target for an automatic failover.</span></span> <span data-ttu-id="7cad7-110">자세한 내용은 [가용성 모드&#40;AlwaysOn 가용성 그룹&#41;](availability-modes-always-on-availability-groups.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cad7-110">For more information, see [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7cad7-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7cad7-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7cad7-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cad7-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7cad7-113">장애 조치 명령은 대상 복제본에서 명령을 수락하는 즉시 반환하지만</span><span class="sxs-lookup"><span data-stu-id="7cad7-113">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="7cad7-114">데이터베이스 복구는 가용성 그룹의 장애 조치가 끝난 후 비동기로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-114">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="7cad7-115">장애 조치 시 가용성 그룹 내에서 데이터베이스 간 일관성은 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-115">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7cad7-116">데이터베이스 간 트랜잭션 또는 분산 트랜잭션은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-116">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="7cad7-117">자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cad7-117">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="7cad7-118">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cad7-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="7cad7-119">대상 보조 복제본과 주 복제본이 모두 동기-커밋 가용성 모드에서 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-119">The target secondary replica and the primary replica must both be running in synchronous-commit availability mode.</span></span>  
  
-   <span data-ttu-id="7cad7-120">대상 보조 복제본이 주 복제본과 현재 동기화되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-120">The target secondary replica must currently be synchronized with the primary replica.</span></span> <span data-ttu-id="7cad7-121">이렇게 하려면 보조 복제본에 있는 모든 보조 데이터베이스가 가용성 그룹에 조인되어 있어야 하며 해당 주 데이터베이스와 동기화되어 있어야 합니다. 즉, 로컬 보조 데이터베이스가 SYNCHRONIZED 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-121">This requires that all the secondary databases on this secondary replica must have been joined to the availability group and be synchronized with their corresponding primary databases (that is, the local secondary databases must be SYNCHRONIZED).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="7cad7-122">보조 복제본의 장애 조치(failover) 준비를 확인하려면 [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) 동적 관리 뷰에서 **is_failover_ready** 열을 쿼리하거나 [AlwaysOn 그룹 대시보드](use-the-always-on-dashboard-sql-server-management-studio.md)에서 **장애 조치(Failover) 준비** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-122">To determine the failover readiness of an secondary replica, query the **is_failover_ready** column in the [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) dynamic management view, or look at the **Failover Readiness** column of the [AlwaysOn Group Dashboard](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="7cad7-123">이 태스크는 대상 보조 복제본에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-123">This task is supported only on the target secondary replica.</span></span> <span data-ttu-id="7cad7-124">대상 보조 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-124">You must be connected to the server instance that hosts the target secondary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7cad7-125">보안</span><span class="sxs-lookup"><span data-stu-id="7cad7-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7cad7-126">권한</span><span class="sxs-lookup"><span data-stu-id="7cad7-126">Permissions</span></span>  
 <span data-ttu-id="7cad7-127">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-127">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7cad7-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7cad7-128">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7cad7-129">**가용성 그룹을 수동으로 장애 조치하려면**</span><span class="sxs-lookup"><span data-stu-id="7cad7-129">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="7cad7-130">개체 탐색기에서 장애 조치해야 할 가용성 그룹의 보조 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-130">In Object Explorer, connect to a server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7cad7-131">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-131">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="7cad7-132">장애 조치할 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **장애 조치(Failover)** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-132">Right-click the availability group to be failed over, and select the **Failover** command.</span></span>  
  
4.  <span data-ttu-id="7cad7-133">그러면 가용성 그룹 장애 조치(failover) 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-133">This launches the Failover Availability Group Wizard.</span></span> <span data-ttu-id="7cad7-134">자세한 내용은 [가용성 그룹 장애 조치(failover) 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cad7-134">For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7cad7-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7cad7-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="7cad7-136">**가용성 그룹을 수동으로 장애 조치하려면**</span><span class="sxs-lookup"><span data-stu-id="7cad7-136">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="7cad7-137">대상 보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-137">Connect to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="7cad7-138">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="7cad7-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span><span class="sxs-lookup"><span data-stu-id="7cad7-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span></span>  
  
     <span data-ttu-id="7cad7-140">여기서 *group_name* 은 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-140">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="7cad7-141">다음 예에서는 *MyAg* 가용성 그룹을 연결된 보조 복제본으로 수동으로 장애 조치합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-141">The following example manually fails over the *MyAg* availability group to the connected secondary replica.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="7cad7-142">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="7cad7-142">Using PowerShell</span></span>  
 <span data-ttu-id="7cad7-143">**가용성 그룹을 수동으로 장애 조치하려면**</span><span class="sxs-lookup"><span data-stu-id="7cad7-143">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="7cad7-144">대상 보조 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-144">Change directory (`cd`) to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="7cad7-145">`Switch-SqlAvailabilityGroup` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-145">Use the `Switch-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7cad7-146">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="7cad7-147">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cad7-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
     <span data-ttu-id="7cad7-148">다음 예에서는 지정 된 경로를 사용 하 여 *Myag* 가용성 그룹을 보조 복제본으로 수동으로 장애 조치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-148">The following example manually fails over the *MyAg* availability group to the secondary replica with the specified path.</span></span>  
  
    ```powershell
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 <span data-ttu-id="7cad7-149">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="7cad7-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="7cad7-150">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="7cad7-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="7cad7-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cad7-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="follow-up-after-manually-failing-over-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="7cad7-152">후속 작업: 가용성 그룹을 수동으로 장애 조치 (failover) 한 후</span><span class="sxs-lookup"><span data-stu-id="7cad7-152">Follow Up: After Manually Failing Over an Availability Group</span></span>  
 <span data-ttu-id="7cad7-153">가용성 그룹의 [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] 외부로 장애 조치한 경우 새로운 가용성 그룹 구성을 반영하도록 WSFC 노드의 쿼럼 투표를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cad7-153">If you failed over outside of the [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] of the availability group, adjust the quorum votes of the WSFC nodes to reflect your new availability group configuration.</span></span> <span data-ttu-id="7cad7-154">자세한 내용은 [Windows Server 장애 조치 (Failover) 클러스터링 &#40;WSFC&#41; SQL Server를](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cad7-154">For more information, see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cad7-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7cad7-155">See Also</span></span>  
 <span data-ttu-id="7cad7-156">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7cad7-156">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="7cad7-157">[장애 조치 (failover) 및 장애 조치 (failover) 모드 &#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="7cad7-157">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="7cad7-158">가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7cad7-158">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
