---
title: 가용성 그룹 속성 보기(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d1f57a9bd29b6c65160ec9a163bc77dfca48b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649178"
---
# <a name="view-availability-group-properties-sql-server"></a><span data-ttu-id="ea6b6-102">가용성 그룹 속성 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ea6b6-102">View Availability Group Properties (SQL Server)</span></span>
  <span data-ttu-id="ea6b6-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]를 사용하여 AlwaysOn 가용성 그룹에 대한 가용성 그룹 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-103">This topic describes how to view the properties of an availability group for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ea6b6-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ea6b6-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ea6b6-105">**가용성 그룹의 속성을 보고 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="ea6b6-105">**To view and change the properties an availability group**</span></span>  
  
1.  <span data-ttu-id="ea6b6-106">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ea6b6-107">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="ea6b6-108">속성을 보려는 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-108">Right-click the availability group whose properties you want to view, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="ea6b6-109">**가용성 그룹 속성** 대화 상자에서 **일반** 및 **백업 기본 설정** 페이지를 사용하여 선택한 가용성 그룹의 속성을 보고 필요한 경우 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-109">In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group.</span></span> <span data-ttu-id="ea6b6-110">자세한 내용은 [가용성 그룹 속성 및 새 가용성 그룹&#40;일반 페이지&#41;](availability-group-properties-new-availability-group-general-page.md) 및 [가용성 그룹 속성: 새 가용성 그룹&#40;백업 기본 설정 페이지&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-110">For more information, see [Availability Group Properties and New Availability Group &#40;General Page&#41;](availability-group-properties-new-availability-group-general-page.md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
     <span data-ttu-id="ea6b6-111">**사용 권한** 페이지를 사용하여 가용성 그룹과 연결된 현재 로그인, 역할 및 명시적 권한을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-111">Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group.</span></span> <span data-ttu-id="ea6b6-112">자세한 내용은 [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-112">For more information, see [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ea6b6-113">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ea6b6-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="ea6b6-114">**가용성 그룹의 속성 및 상태를 보려면**</span><span class="sxs-lookup"><span data-stu-id="ea6b6-114">**To view the properties and state of an availability group**</span></span>  
  
 <span data-ttu-id="ea6b6-115">서버 인스턴스가 가용성 복제본을 호스팅하는 가용성 그룹의 속성 및 상태를 쿼리하려면 다음 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-115">To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="ea6b6-116">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="ea6b6-116">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="ea6b6-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에서 가용성 복제본을 호스팅하는 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-117">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="ea6b6-118">각 행에는 가용성 그룹 메타데이터의 캐시된 복사본이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-118">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="ea6b6-119">**열 이름:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="ea6b6-119">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="ea6b6-120">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="ea6b6-120">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="ea6b6-121">WSFC 클러스터의 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-121">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="ea6b6-122">각 행에는 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터의 가용성 그룹 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-122">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="ea6b6-123">**열 이름:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="ea6b6-123">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="ea6b6-124">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="ea6b6-124">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="ea6b6-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 로컬 인스턴스에 가용성 복제본이 있는 각 가용성 그룹에 대해 하나의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-125">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ea6b6-126">각 행에는 지정된 가용성 그룹의 상태를 정의하는 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea6b6-126">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="ea6b6-127">**열 이름:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="ea6b6-127">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ea6b6-128">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ea6b6-128">Related Tasks</span></span>  
 <span data-ttu-id="ea6b6-129">**가용성 그룹에 대한 자세한 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="ea6b6-129">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="ea6b6-130">가용성 복제본 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-130">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-131">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-131">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-132">AlwaysOn 가용성 그룹 &#40;SQL Server의 운영 문제에 대 한 AlwaysOn 정책&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-132">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="ea6b6-133">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-133">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="ea6b6-134">가용성 그룹 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-134">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="ea6b6-135">**기존 가용성 그룹을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="ea6b6-135">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="ea6b6-136">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-136">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-137">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-137">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-138">가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-138">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="ea6b6-139">가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-139">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-140">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-140">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-141">가용성 그룹 수신기 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-141">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-142">가용성 그룹에서 주 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-142">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-143">가용성 그룹 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-143">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="ea6b6-144">**가용성 그룹을 수동으로 장애 조치하려면**</span><span class="sxs-lookup"><span data-stu-id="ea6b6-144">**To manually fail over an availability group**</span></span>  
  
-   [<span data-ttu-id="ea6b6-145">가용성 그룹의 계획된 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-145">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ea6b6-146">가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="ea6b6-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea6b6-147">See Also</span></span>  
 <span data-ttu-id="ea6b6-148">&#40;&#41;AlwaysOn 가용성 그룹의 [운영 문제에 대 한 transact-sql &#40;AlwaysOn 정책](always-on-policies-for-operational-issues-always-on-availability.md) [SQL Server 가용성 그룹을 모니터링](monitor-availability-groups-transact-sql.md) 하 [는 AlwaysOn 가용성 그룹 &#40;&#41;SQL Server의 개요](overview-of-always-on-availability-groups-sql-server.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="ea6b6-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span></span> 
  
  
