---
title: 가용성 복제본 속성 보기(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ca7b0508907b4d86c9ee627438a3f18e1b01fdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733148"
---
# <a name="view-availability-replica-properties-sql-server"></a><span data-ttu-id="a4554-102">가용성 복제본 속성 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a4554-102">View Availability Replica Properties (SQL Server)</span></span>
  <span data-ttu-id="a4554-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]를 사용하여 AlwaysOn 가용성 그룹에 대한 가용성 복제본 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-103">This topic describes how to view the properties of an availability replica for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a4554-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a4554-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a4554-105">**가용성 복제본의 속성을 보고 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="a4554-105">**To view and change properties an availability replica**</span></span>  
  
1.  <span data-ttu-id="a4554-106">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a4554-107">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="a4554-108">가용성 복제본이 속하는 가용성 그룹을 확장하고 **가용성 복제본** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-108">Expand the availability group to which the availability replica belongs, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="a4554-109">속성을 보려는 가용성 복제본을 마우스 오른쪽 단추로 클릭하고 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-109">Right-click the availability replica whose properties you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="a4554-110">**가용성 복제본 속성** 대화 상자에서 **일반** 페이지를 사용하여 이 복제본의 속성을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-110">In the **Availability Replica Properties** dialog box, use the **General** page to view the properties of this replica.</span></span> <span data-ttu-id="a4554-111">주 복제본에 연결된 경우 가용성 모드, 장애 조치(failover) 모드, 주 역할에 대한 연결 액세스, 보조 역할에 대한 읽기 액세스(읽기 가능 보조), 세션 제한 시간 값 등의 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-111">If you are connected to the primary replica, you can change the following properties: availability mode, failover mode, connection access for the primary role, read-access for the secondary role (readable-secondary), and the session-timeout value.</span></span> <span data-ttu-id="a4554-112">자세한 내용은 [가용성 복제본 속성 &#40;일반 페이지&#41;](availability-replica-properties-general-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4554-112">For more information, see  [Availability Replica Properties &#40;General Page&#41;](availability-replica-properties-general-page.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a4554-113">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a4554-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="a4554-114">**가용성 복제본의 속성 및 상태를 보려면**</span><span class="sxs-lookup"><span data-stu-id="a4554-114">**To view properties and states of availability replicas**</span></span>  
  
 <span data-ttu-id="a4554-115">가용성 복제본의 속성 및 상태를 보려면 다음 뷰와 시스템 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-115">To view the properties and states of availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="a4554-116">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="a4554-116">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="a4554-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에서 가용성 복제본을 호스팅하는 각 가용성 그룹의 모든 가용성 복제본에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-117">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="a4554-118">**열 이름:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="a4554-118">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="a4554-119">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="a4554-119">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="a4554-120">WSFC 장애 조치(Failover) 클러스터의 AlwaysOn 가용성 그룹에서 각각의 가용성 복제본의 읽기 전용 라우팅 목록에 대한 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-120">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="a4554-121">**열 이름:** replica_id, routing_priority, read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="a4554-121">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="a4554-122">가용성 복제본 모니터링</span><span class="sxs-lookup"><span data-stu-id="a4554-122">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="a4554-123">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 있는 AlwaysOn 가용성 그룹의 모든 가용성 복제본(조인 상태에 상관없음)에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-123">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a4554-124">**열 이름:** group_name, replica_server_name, node_name</span><span class="sxs-lookup"><span data-stu-id="a4554-124">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="a4554-125">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="a4554-125">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="a4554-126">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 있는 모든 AlwaysOn 가용성 그룹(복제본 위치에 상관없음)의 각 복제본(조인 상태에 상관없음)에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-126">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a4554-127">**열 이름:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span><span class="sxs-lookup"><span data-stu-id="a4554-127">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="a4554-128">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="a4554-128">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="a4554-129">각 로컬 가용성 복제본의 상태를 보여 주는 행과 동일한 가용성 그룹의 각 원격 가용성 복제본에 대한 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-129">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="a4554-130">**열 이름:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="a4554-130">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="a4554-131">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="a4554-131">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="a4554-132">현재 복제본이 기본 백업 복제본인지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-132">Determines whether the current replica is the preferred backup replica.</span></span> <span data-ttu-id="a4554-133">현재 서버 인스턴스의 데이터베이스가 기본 복제본이면 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-133">Returns 1 if the database on the current server instance is the preferred replica.</span></span> <span data-ttu-id="a4554-134">그렇지 않으면 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4554-134">Otherwise, it returns 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4554-135">가용성 복제본의 성능 카운터( **SQLServer:가용성 복제본**  성능 개체)에 대한 자세한 내용은 [SQL Server, 가용성 복제본](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4554-135">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a4554-136">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a4554-136">Related Tasks</span></span>  
 <span data-ttu-id="a4554-137">**가용성 그룹에 대한 자세한 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="a4554-137">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="a4554-138">가용성 그룹 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-138">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="a4554-139">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-139">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="a4554-140">AlwaysOn 가용성 그룹 &#40;SQL Server의 운영 문제에 대 한 AlwaysOn 정책&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-140">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="a4554-141">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a4554-142">가용성 그룹 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-142">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="a4554-143">**가용성 복제본을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="a4554-143">**To manage availability replicas**</span></span>  
  
-   [<span data-ttu-id="a4554-144">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-144">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a4554-145">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-145">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a4554-146">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-146">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a4554-147">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-147">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a4554-148">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-148">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a4554-149">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-149">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a4554-150">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-150">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="a4554-151">**가용성 데이터베이스를 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="a4554-151">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="a4554-152">가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-152">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="a4554-153">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-153">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a4554-154">가용성 데이터베이스 일시 중지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-154">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="a4554-155">가용성 데이터베이스 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-155">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="a4554-156">가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-156">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a4554-157">가용성 그룹에서 주 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-157">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="a4554-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4554-158">See Also</span></span>  
 <span data-ttu-id="a4554-159">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a4554-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a4554-160">[Transact-sql&#41;&#40;가용성 그룹 모니터링](monitor-availability-groups-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="a4554-160">[Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) </span></span>  
 <span data-ttu-id="a4554-161">[AlwaysOn 가용성 그룹 &#40;SQL Server의 운영 문제에 대 한 AlwaysOn 정책&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="a4554-161">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 [<span data-ttu-id="a4554-162">가용성 그룹 관리 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4554-162">Administration of an Availability Group &#40;SQL Server&#41;</span></span>](administration-of-an-availability-group-sql-server.md)  
  
  
