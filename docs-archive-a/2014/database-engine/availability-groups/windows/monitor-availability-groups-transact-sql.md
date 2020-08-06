---
title: 가용성 그룹 모니터링(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- dynamic management views [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], databases
- catalog views [SQL Server], AlwaysOn Availability Groups
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 103dd8eef782dfa7a4d13929b0b832dba9bc46e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649184"
---
# <a name="monitor-availability-groups-transact-sql"></a><span data-ttu-id="bb174-102">가용성 그룹 모니터링(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bb174-102">Monitor Availability Groups (Transact-SQL)</span></span>
  <span data-ttu-id="bb174-103">[!INCLUDE[tsql](../../../includes/tsql-md.md)]에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하여 가용성 그룹, 복제본 및 연결된 데이터베이스를 모니터링할 수 있도록 여러 카탈로그 및 동적 관리 뷰와 서버 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-103">For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] provides a set of catalog and dynamic management views and server properties.</span></span> <span data-ttu-id="bb174-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 문을 사용하여 뷰를 통해 가용성 그룹과 해당 복제본 및 데이터베이스를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-104">Using [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases.</span></span> <span data-ttu-id="bb174-105">지정된 가용성 그룹에 대해 반환되는 정보는 연결된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 주 복제본을 호스팅 중인지 아니면 보조 복제본을 호스팅 중인지에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-105">The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the primary replica or a secondary replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="bb174-106">ID 열로 뷰를 조인하여 한 번의 쿼리로 여러 뷰에서 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-106">Many of these views can be joined using their ID columns to return information from multiple views in a single query.</span></span>  
  
 
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bb174-107">권한</span><span class="sxs-lookup"><span data-stu-id="bb174-107">Permissions</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="bb174-108">카탈로그 뷰를 사용하려면 서버 인스턴스에 대한 모든 정의 보기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-108">catalog views require VIEW ANY DEFINITION permission on the server instance.</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="bb174-109">동적 관리 뷰를 사용하려면 서버에 대한 서버 상태 보기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-109">dynamic management views require VIEW SERVER STATE permission on the server.</span></span>  
  
##  <a name="monitoring-the-alwayson-availability-groups-feature-on-a-server-instance"></a><a name="AoAgFeatureOnSI"></a><span data-ttu-id="bb174-110">서버 인스턴스에서 AlwaysOn 가용성 그룹 기능 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-110">Monitoring the AlwaysOn Availability Groups Feature on a Server Instance</span></span>  
 <span data-ttu-id="bb174-111">서버 인스턴스의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 기능을 모니터링하려면 다음 기본 제공 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-111">To monitor the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on a server instance, use the following built-in function:</span></span>  
  
 <span data-ttu-id="bb174-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 함수</span><span class="sxs-lookup"><span data-stu-id="bb174-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) function</span></span>  
 <span data-ttu-id="bb174-113">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용할지 여부와 사용할 경우 서버 인스턴스에서 시작되었는지 여부에 대한 서버 속성 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-113">Returns server property information about whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled and, if so, whether it has started on the server instance.</span></span>  
  
 <span data-ttu-id="bb174-114">**열 이름:** IsHadrEnabled, HadrManagerStatus</span><span class="sxs-lookup"><span data-stu-id="bb174-114">**Column names:** IsHadrEnabled, HadrManagerStatus</span></span>  
  
##  <a name="monitoring-availability-groups-on-the-wsfc-cluster"></a><a name="WSFC"></a><span data-ttu-id="bb174-115">WSFC 클러스터의 가용성 그룹 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-115">Monitoring Availability Groups on the WSFC Cluster</span></span>  
 <span data-ttu-id="bb174-116">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 사용되는 로컬 서버 인스턴스를 호스팅하는 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터를 모니터링하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-116">To monitor the Windows Server Failover Clustering (WSFC) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], use the following views:</span></span>  
  
 [<span data-ttu-id="bb174-117">sys.dm_hadr_cluster</span><span class="sxs-lookup"><span data-stu-id="bb174-117">sys.dm_hadr_cluster</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
 <span data-ttu-id="bb174-118">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하여 SQL Server 인스턴스를 호스트하는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에 WSFC 쿼럼이 있는 경우 **sys.dm_hadr_cluster** 는 쿼럼에 대한 클러스터 이름과 정보를 표시하는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-118">If the Windows Server Failover Clustering (WSFC) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled has WSFC quorum, **sys.dm_hadr_cluster** returns a row that exposes the cluster name and information about the quorum.</span></span> <span data-ttu-id="bb174-119">WSFC 노드에 쿼럼이 없으면 반환되는 행이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-119">If the WSFC node has no quorum, no rows are returned.</span></span>  
  
 <span data-ttu-id="bb174-120">**열 이름:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-120">**Column names:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc</span></span>  
  
 [<span data-ttu-id="bb174-121">sys.dm_hadr_cluster_members</span><span class="sxs-lookup"><span data-stu-id="bb174-121">sys.dm_hadr_cluster_members</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
 <span data-ttu-id="bb174-122">SQL Server의 로컬 AlwaysOn 사용 인스턴스를 호스팅하는 WSFC 노드에 WSFC 쿼럼이 있는 경우 쿼럼을 구성하는 각 멤버에 대한 행과 각 멤버의 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-122">If the WSFC node that hosts the local AlwaysOn-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.</span></span>  
  
 <span data-ttu-id="bb174-123">**열 이름:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes</span><span class="sxs-lookup"><span data-stu-id="bb174-123">**Column names:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes</span></span>  
  
 [<span data-ttu-id="bb174-124">sys.dm_hadr_cluster_networks</span><span class="sxs-lookup"><span data-stu-id="bb174-124">sys.dm_hadr_cluster_networks</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
 <span data-ttu-id="bb174-125">가용성 그룹의 서브넷 구성에 참여하는 모든 멤버에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-125">Returns a row for every member that is participating in an availability group's subnet configuration.</span></span> <span data-ttu-id="bb174-126">이 동적 관리 뷰를 사용하여 각 가용성 복제본에 대해 구성된 네트워크 가상 IP의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-126">You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.</span></span>  
  
 <span data-ttu-id="bb174-127">**열 이름:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4</span><span class="sxs-lookup"><span data-stu-id="bb174-127">**Column names:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4</span></span>  
  
 <span data-ttu-id="bb174-128">**기본 키:** member_name + network_subnet_IP + network_subnet_prefix_length</span><span class="sxs-lookup"><span data-stu-id="bb174-128">**Primary key:** member_name + network_subnet_IP + network_subnet_prefix_length</span></span>  
  
 [<span data-ttu-id="bb174-129">sys.dm_hadr_instance_node_map</span><span class="sxs-lookup"><span data-stu-id="bb174-129">sys.dm_hadr_instance_node_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
 <span data-ttu-id="bb174-130">AlwaysOn 가용성 그룹에 조인된 가용성 복제본을 호스팅하는 SQL Server의 모든 인스턴스에 대해 서버 인스턴스를 호스팅하는 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-130">For every instance of SQL Server that hosts an availability replica that is joined to its AlwaysOn availability group, returns the name of the Windows Server Failover Clustering (WSFC) node that hosts the server instance.</span></span> <span data-ttu-id="bb174-131">이러한 동적 관리 뷰는 다음과 같이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-131">This dynamic management view has the following uses:</span></span>  
  
-   <span data-ttu-id="bb174-132">이 동적 관리 뷰는 동일한 WSFC 노드에서 호스팅되는 여러 가용성 복제본이 포함된 가용성 그룹을 검색하는 데 유용합니다. 이러한 구성은 가용성 그룹이 잘못 구성된 경우 FCI 장애 조치(failover) 이후 발생 가능한 지원되지 않는 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-132">This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.</span></span>  
  
-   <span data-ttu-id="bb174-133">여러 SQL Server 인스턴스가 동일한 WSFC 노드에 호스팅되는 경우 리소스 DLL이 이 동적 관리 뷰를 사용하여 연결할 SQL Server의 인스턴스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-133">When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.</span></span>  
  
 <span data-ttu-id="bb174-134">**열 이름:** ag_resource_id, instance_name, node_name</span><span class="sxs-lookup"><span data-stu-id="bb174-134">**Column names:** ag_resource_id, instance_name, node_name</span></span>  
  
 [<span data-ttu-id="bb174-135">sys.dm_hadr_name_id_map</span><span class="sxs-lookup"><span data-stu-id="bb174-135">sys.dm_hadr_name_id_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
 <span data-ttu-id="bb174-136">현재 SQL Server 인스턴스가 세 가지 고유한 ID인 가용성 그룹 ID, WSFC 리소스 ID 및 WSFC 그룹 ID에 조인된 AlwaysOn 가용성 그룹의 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-136">Shows the mapping of AlwaysOn availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID.</span></span> <span data-ttu-id="bb174-137">이 매핑의 목적은 WSFC 리소스/그룹의 이름이 바뀐 시나리오를 처리하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-137">The purpose of this mapping is to handle the scenario in which the WSFC resource/group is renamed.</span></span>  
  
 <span data-ttu-id="bb174-138">**열 이름:** ag_name, ag_id, ag_resource_id, ag_group_id</span><span class="sxs-lookup"><span data-stu-id="bb174-138">**Column names:** ag_name, ag_id, ag_resource_id, ag_group_id</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb174-139">또한 나중에 이 항목에 있는 [가용성 복제본 모니터링](#AvReplicas) 섹션에서 **sys.dm_hadr_availability_replica_cluster_nodes** 및 **sys.dm_hadr_availability_replica_cluster_states**를 참조하고 [가용성 데이터베이스 모니터링](#AvDbs) 섹션에서 **sys.availability_databases_cluster** 및 **sys.dm_hadr_database_replica_cluster_states**를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-139">Also see **sys.dm_hadr_availability_replica_cluster_nodes** and **sys.dm_hadr_availability_replica_cluster_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability_databases_cluster** and **sys.dm_hadr_database_replica_cluster_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.</span></span>  
  
 <span data-ttu-id="bb174-140">WSFC 클러스터 및에 대 한 자세한 내용은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] [Windows Server 장애 조치 (Failover) 클러스터링 &#40;wsfc&#41; SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) 및 [장애 조치 (failover) 클러스터링 및 AlwaysOn 가용성 그룹 &#40;](failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-140">For information about WSFC clusters and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) and [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="monitoring-availability-groups"></a><a name="AvGroups"></a> <span data-ttu-id="bb174-141">Monitoring Availability Groups</span><span class="sxs-lookup"><span data-stu-id="bb174-141">Monitoring Availability Groups</span></span>  
 <span data-ttu-id="bb174-142">서버 인스턴스가 가용성 복제본을 호스팅하는 가용성 그룹을 모니터링하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-142">To monitor the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="bb174-143">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="bb174-143">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="bb174-144">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에서 가용성 복제본을 호스팅하는 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-144">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="bb174-145">각 행에는 가용성 그룹 메타데이터의 캐시된 복사본이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-145">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="bb174-146">**열 이름:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-146">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="bb174-147">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="bb174-147">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="bb174-148">WSFC 클러스터의 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-148">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="bb174-149">각 행에는 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터의 가용성 그룹 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-149">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="bb174-150">**열 이름:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-150">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="bb174-151">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="bb174-151">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="bb174-152">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 로컬 인스턴스에 가용성 복제본이 있는 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-152">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bb174-153">각 행에는 지정된 가용성 그룹의 상태를 정의하는 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-153">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="bb174-154">**열 이름:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-154">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  
##  <a name="monitoring-availability-replicas"></a><a name="AvReplicas"></a><span data-ttu-id="bb174-155">가용성 복제본 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-155">Monitoring Availability Replicas</span></span>  
 <span data-ttu-id="bb174-156">가용성 복제본을 모니터링하려면 다음 뷰와 시스템 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-156">To monitor availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="bb174-157">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="bb174-157">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="bb174-158">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에서 가용성 복제본을 호스팅하는 각 가용성 그룹의 모든 가용성 복제본에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-158">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="bb174-159">**열 이름:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="bb174-159">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="bb174-160">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="bb174-160">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="bb174-161">WSFC 장애 조치(Failover) 클러스터의 AlwaysOn 가용성 그룹에서 각각의 가용성 복제본의 읽기 전용 라우팅 목록에 대한 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-161">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="bb174-162">**열 이름:** replica_id, routing_priority, read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="bb174-162">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="bb174-163">가용성 복제본 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-163">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="bb174-164">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 있는 AlwaysOn 가용성 그룹의 모든 가용성 복제본(조인 상태에 상관없음)에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-164">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="bb174-165">**열 이름:** group_name, replica_server_name, node_name</span><span class="sxs-lookup"><span data-stu-id="bb174-165">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="bb174-166">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="bb174-166">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="bb174-167">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 있는 모든 AlwaysOn 가용성 그룹(복제본 위치에 상관없음)의 각 복제본(조인 상태에 상관없음)에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-167">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="bb174-168">**열 이름:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-168">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="bb174-169">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="bb174-169">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="bb174-170">각 로컬 가용성 복제본의 상태를 보여 주는 행과 동일한 가용성 그룹의 각 원격 가용성 복제본에 대한 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-170">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="bb174-171">**열 이름:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="bb174-171">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="bb174-172">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="bb174-172">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="bb174-173">현재 복제본이 기본 백업 복제본인지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-173">Determines whether the current replica is the preferred backup replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb174-174">가용성 복제본의 성능 카운터( **SQLServer:가용성 복제본**  성능 개체)에 대한 자세한 내용은 [SQL Server, 가용성 복제본](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-174">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="monitoring-availability-databases"></a><a name="AvDbs"></a><span data-ttu-id="bb174-175">가용성 데이터베이스 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-175">Monitoring Availability Databases</span></span>  
 <span data-ttu-id="bb174-176">가용성 데이터베이스를 모니터링하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-176">To monitor availability databases, use the following views:</span></span>  
  
 [<span data-ttu-id="bb174-177">가용성 데이터베이스 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-177">sys.availability_databases_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
 <span data-ttu-id="bb174-178">로컬 복사본 데이터베이스가 가용성 그룹에 조인되어 있는지 여부에 상관없이 클러스터의 모든 AlwaysOn 가용성 그룹의 일부인 SQL Server 인스턴스의 데이터베이스별로 하나의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-178">Contains one row for each database on the instance of SQL Server that are part of all AlwaysOn Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb174-179">데이터베이스가 가용성 그룹에 추가되면 주 데이터베이스가 그룹에 자동으로 조인됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-179">When a database is added to an availability group, the primary database is automatically joined to the group.</span></span> <span data-ttu-id="bb174-180">보조 데이터베이스를 가용성 그룹에 조인하려면 각 보조 복제본에서 보조 데이터베이스를 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-180">Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.</span></span>  
  
 <span data-ttu-id="bb174-181">**열 이름:** group_id, group_database_id, database_name</span><span class="sxs-lookup"><span data-stu-id="bb174-181">**Column names:** group_id, group_database_id, database_name</span></span>  
  
 [<span data-ttu-id="bb174-182">sys.databases</span><span class="sxs-lookup"><span data-stu-id="bb174-182">sys.databases</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
 <span data-ttu-id="bb174-183">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스의 각 데이터베이스당 한 개의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-183">Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bb174-184">데이터베이스가 가용성 복제본에 속하는 경우 해당 데이터베이스의 행에 복제본의 GUID와 가용성 그룹 내의 데이터베이스에 대한 고유 식별자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-184">If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.</span></span>  
  
 <span data-ttu-id="bb174-185">\*\* [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 열 이름:\*\* replica_id, group_database_id</span><span class="sxs-lookup"><span data-stu-id="bb174-185">**[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] column names:** replica_id, group_database_id</span></span>  
  
 [<span data-ttu-id="bb174-186">sys.dm_hadr_auto_page_repair</span><span class="sxs-lookup"><span data-stu-id="bb174-186">sys.dm_hadr_auto_page_repair</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
 <span data-ttu-id="bb174-187">서버 인스턴스가 모든 가용성 그룹에 대해 호스팅하는 가용성 복제본의 모든 가용성 데이터베이스에 대해 수행하는 자동 페이지 복구 시도당 한 개의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-187">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span> <span data-ttu-id="bb174-188">이 뷰에는 지정된 주 데이터베이스 또는 보조 데이터베이스의 최신 자동 페이지 복구 시도에 대한 행이 포함됩니다(데이터베이스당 최대 100개 행).</span><span class="sxs-lookup"><span data-stu-id="bb174-188">This view contains rows for the latest automatic page-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database.</span></span> <span data-ttu-id="bb174-189">데이터베이스가 최대값에 도달하는 즉시 다음 자동 페이지 복구 시도에 대한 행이 기존 항목 중 하나를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-189">As soon as a database reaches the maximum, the row for its next automatic page-repair attempt replaces one of the existing entries.</span></span>  
  
 <span data-ttu-id="bb174-190">**열 이름:** database_id, file_id, page_id, error_type, page_status, modification_time</span><span class="sxs-lookup"><span data-stu-id="bb174-190">**Column names:** database_id, file_id, page_id, error_type, page_status, modification_time</span></span>  
  
 [<span data-ttu-id="bb174-191">sys.dm_hadr_database_replica_states</span><span class="sxs-lookup"><span data-stu-id="bb174-191">sys.dm_hadr_database_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
 <span data-ttu-id="bb174-192">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스가 가용성 복제본을 호스팅 중인 모든 가용성 그룹에 참여하는 각 데이터베이스에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-192">Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is hosting an availability replica.</span></span>  
  
 <span data-ttu-id="bb174-193">**열 이름:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts</span><span class="sxs-lookup"><span data-stu-id="bb174-193">**Column names:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts</span></span>  
  
 [<span data-ttu-id="bb174-194">sys.availability_databases_cluster</span><span class="sxs-lookup"><span data-stu-id="bb174-194">sys.dm_hadr_database_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
 <span data-ttu-id="bb174-195">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터의 각 가용성 그룹에 있는 가용성 데이터베이스의 상태를 파악하는 데 필요한 정보가 들어 있는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-195">Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="bb174-196">이 동적 관리 뷰는 장애 조치(failover)를 계획 또는 이에 응답하거나 지정된 주 데이터베이스의 로그 잘림을 보유 중인 가용성 그룹의 보조 복제본을 검색하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-196">This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.</span></span>  
  
 <span data-ttu-id="bb174-197">**열 이름:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn</span><span class="sxs-lookup"><span data-stu-id="bb174-197">**Column names:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb174-198">주 복제본 위치는 가용성 그룹의 권한이 있는 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-198">The primary replica location is the authoritative source for an availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb174-199">가용성 데이터베이스의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 성능 카운터( **SQLServer:Database Replica** 성능 개체)에 대한 자세한 내용은 [SQL Server, 데이터베이스 복제본](../../../relational-databases/performance-monitor/sql-server-database-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-199">For information about the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] performance counters for availability databases (the **SQLServer:Database Replica** performance object), see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span> <span data-ttu-id="bb174-200">또한 가용성 데이터베이스에서 트랜잭션 로그 작업을 모니터링 하려면 **SQLServer: databases** 성능 개체의 **Log Flush Write Time (ms)**, **log Flush/Sec**, **log pool Cache 누락/sec**, Log Pool **Disk Reads/sec**및 **log pool Requests/sec**카운터를 사용 합니다. 자세한 내용은 [SQL Server, Databases 개체](../../../relational-databases/performance-monitor/sql-server-databases-object.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-200">Also, to monitor transaction-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**. For more information, see [SQL Server, Databases Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md).</span></span>  
  
##  <a name="monitoring-availability-group-listeners"></a><a name="AGlisteners"></a><span data-ttu-id="bb174-201">가용성 그룹 수신기 모니터링</span><span class="sxs-lookup"><span data-stu-id="bb174-201">Monitoring Availability Group Listeners</span></span>  
 <span data-ttu-id="bb174-202">WSFC 클러스터의 서브넷에서 가용성 그룹 수신기를 모니터링하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-202">To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:</span></span>  
  
 [<span data-ttu-id="bb174-203">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="bb174-203">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="bb174-204">가용성 그룹 수신기에 대해 현재 온라인인 규칙에 부합하는 모든 가상 IP 주소에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-204">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="bb174-205">**열 이름:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span><span class="sxs-lookup"><span data-stu-id="bb174-205">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="bb174-206">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="bb174-206">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="bb174-207">지정된 가용성 그룹에 대해 0개의 행을 반환하여 가용성 그룹에 연결된 네트워크 이름이 없음을 나타내거나 WSFC 클러스터의 각 가용성 그룹 수신기 구성에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-207">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="bb174-208">**열 이름:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="bb174-208">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="bb174-209">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="bb174-209">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="bb174-210">각 TCP 수신기에 대한 동적 상태 정보를 포함하는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb174-210">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="bb174-211">**열 이름:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span><span class="sxs-lookup"><span data-stu-id="bb174-211">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
 <span data-ttu-id="bb174-212">**기본 키:** listener_id</span><span class="sxs-lookup"><span data-stu-id="bb174-212">**Primary key:** listener_id</span></span>  
  
 <span data-ttu-id="bb174-213">가용성 그룹 수신기에 대한 자세한 내용은 [가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb174-213">For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bb174-214">관련 작업</span><span class="sxs-lookup"><span data-stu-id="bb174-214">Related Tasks</span></span>  
 <span data-ttu-id="bb174-215">**AlwaysOn 가용성 그룹 모니터링 태스크:**</span><span class="sxs-lookup"><span data-stu-id="bb174-215">**AlwaysOn Availability Groups monitoring tasks:**</span></span>  
  
-   [<span data-ttu-id="bb174-216">개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-216">Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;</span></span>](use-object-explorer-details-to-monitor-availability-groups.md)  
  
-   [<span data-ttu-id="bb174-217">가용성 그룹 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-217">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="bb174-218">가용성 복제본 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-218">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="bb174-219">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-219">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
 <span data-ttu-id="bb174-220">**AlwaysOn 가용성 그룹 모니터링 참조(Transact-SQL):**</span><span class="sxs-lookup"><span data-stu-id="bb174-220">**AlwaysOn Availability Groups monitoring reference (Transact-SQL):**</span></span>  
  
-   [<span data-ttu-id="bb174-221">SERVERPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
-   [<span data-ttu-id="bb174-222">sys.availability_group_listener_ip_addresses&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
  
-   [<span data-ttu-id="bb174-223">sys.availability_group_listeners&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
  
-   [<span data-ttu-id="bb174-224">sys.availability_databases_cluster&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
  
-   [<span data-ttu-id="bb174-225">sys.availability_groups&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-225">sys.availability_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
  
-   [<span data-ttu-id="bb174-226">sys.availability_read_only_routing_lists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [<span data-ttu-id="bb174-227">sys.availability_replicas&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-227">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
  
-   [<span data-ttu-id="bb174-228">sys.dm_hadr_availability_replica_cluster_nodes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
  
-   [<span data-ttu-id="bb174-229">sys.dm_hadr_availability_replica_cluster_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-230">sys.database_mirroring_endpoints&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
-   [<span data-ttu-id="bb174-231">sys.dm_hadr_auto_page_repair&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
-   [<span data-ttu-id="bb174-232">sys.dm_hadr_availability_group_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-233">sys.dm_hadr_availability_replica_cluster_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-234">sys.dm_hadr_availability_replica_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-234">sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-235">sys.dm_hadr_database_replica_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-236">sys.dm_hadr_database_replica_cluster_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-237">sys.dm_hadr_cluster&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
  
-   [<span data-ttu-id="bb174-238">sys.dm_hadr_cluster_members&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
  
-   [<span data-ttu-id="bb174-239">sys.dm_hadr_cluster_networks&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
  
-   [<span data-ttu-id="bb174-240">sys.dm_hadr_database_replica_cluster_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-241">sys.dm_hadr_database_replica_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-242">sys.dm_hadr_instance_node_map&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
  
-   [<span data-ttu-id="bb174-243">sys.dm_hadr_name_id_map&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
  
-   [<span data-ttu-id="bb174-244">sys.dm_os_performance_counters&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
-   [<span data-ttu-id="bb174-245">sys.dm_tcp_listener_states&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
  
-   [<span data-ttu-id="bb174-246">sys.fn_hadr_backup_is_preferred_replica&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-246">sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="bb174-247">**AlwaysOn 성능 카운터:**</span><span class="sxs-lookup"><span data-stu-id="bb174-247">**AlwaysOn performance counters:**</span></span>  
  
-   [<span data-ttu-id="bb174-248">SQL Server, 가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="bb174-248">SQL Server, Availability Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)  
  
-   [<span data-ttu-id="bb174-249">SQL Server, 데이터베이스 복제본</span><span class="sxs-lookup"><span data-stu-id="bb174-249">SQL Server, Database Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-database-replica.md)  
  
-   [<span data-ttu-id="bb174-250">SQL Server, Databases 개체</span><span class="sxs-lookup"><span data-stu-id="bb174-250">SQL Server, Databases Object</span></span>](../../../relational-databases/performance-monitor/sql-server-databases-object.md)  
  
 <span data-ttu-id="bb174-251">**AlwaysOn 가용성 그룹에 대한 정책 기반 관리**</span><span class="sxs-lookup"><span data-stu-id="bb174-251">**Policy-based management for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="bb174-252">AlwaysOn 정책을 사용 하 여 가용성 그룹 &#40;SQL Server 상태를 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-252">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="bb174-253">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-253">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb174-254">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb174-254">See Also</span></span>  
 <span data-ttu-id="bb174-255">[AlwaysOn 가용성 그룹 (SQL Server)](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bb174-255">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="bb174-256">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bb174-256">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="bb174-257">가용성 그룹 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb174-257">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
