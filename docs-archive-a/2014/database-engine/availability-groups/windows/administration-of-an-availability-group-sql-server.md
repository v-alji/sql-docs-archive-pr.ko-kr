---
title: 가용성 그룹 관리(SQL Server) | Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2cac9a34fe71c11f71ec47bbb6d690199869fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647252"
---
# <a name="administration-of-an-availability-group-sql-server"></a><span data-ttu-id="40bbc-102">가용성 그룹 관리(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40bbc-102">Administration of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="40bbc-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 의 기존 AlwaysOn 가용성 그룹 관리에는 다음 태스크 중 하나 이상이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40bbc-103">Managing an existing AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] involves one or more of the following tasks:</span></span>  
  
-   <span data-ttu-id="40bbc-104">기존 가용성 그룹 복제본의 속성 변경(예: 읽기 가능한 보조 복제본 구성을 위한 클라이언트 연결 액세스 변경용), 장애 조치(failover) 모드, 가용성 모드 또는 세션 제한 시간 설정 변경</span><span class="sxs-lookup"><span data-stu-id="40bbc-104">Altering the properties of an existing availability replica, for example to change client connection access (for configuring readable secondary replicas), changing its failover mode, availability mode, or session timeout setting.</span></span>  
  
-   <span data-ttu-id="40bbc-105">보조 복제본 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="40bbc-105">Adding or removing secondary replicas.</span></span>  
  
-   <span data-ttu-id="40bbc-106">데이터베이스 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="40bbc-106">Adding or removing a database.</span></span>  
  
-   <span data-ttu-id="40bbc-107">데이터베이스 일시 중단 또는 다시 시작</span><span class="sxs-lookup"><span data-stu-id="40bbc-107">Suspending or resuming a database.</span></span>  
  
-   <span data-ttu-id="40bbc-108">계획된 수동 장애 조치(failover)( *수동 장애 조치(failover)*) 또는 강제 수동 장애 조치(failover)( *강제 장애 조치(failover)*) 수행</span><span class="sxs-lookup"><span data-stu-id="40bbc-108">Performing a planned manual failover (a *manual failover*) or a forced manual failover (a *forced failover*).</span></span>  
  
-   <span data-ttu-id="40bbc-109">가용성 그룹 수신기 만들기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="40bbc-109">Creating or configuring an availability group listener.</span></span>  
  
-   <span data-ttu-id="40bbc-110">지정된 가용성 그룹에 대한 [읽기 가능한 보조 복제본](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) 관리</span><span class="sxs-lookup"><span data-stu-id="40bbc-110">Managing [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="40bbc-111">이 태스크에는 보조 역할로 실행하고 읽기 전용 라우팅을 구성할 때 읽기 전용으로 액세스할 하나 이상의 복제본을 구성하는 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40bbc-111">This involves configuring one or more replicas to read-only access when running under the secondary role, and configuring read-only routing.</span></span>  
  
-   <span data-ttu-id="40bbc-112">지정된 가용성 그룹에 대한 [보조 복제본에서의 백업](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 관리.</span><span class="sxs-lookup"><span data-stu-id="40bbc-112">Managing [backups on secondary replicas](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="40bbc-113">이 태스크에는 백업 작업을 실행할 기본 위치를 구성한 다음 백업 작업을 스크립팅하여 백업 기본 설정을 구현하는 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="40bbc-113">This involves configuring where you prefer that backup jobs run and then scripting backup jobs to implement your backup preference.</span></span> <span data-ttu-id="40bbc-114">가용성 복제본을 호스팅하는 모든 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 가용성 그룹의 모든 데이터베이스에 대한 백업 작업을 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40bbc-114">you need to script backup jobs for every database in the availability group on every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica.</span></span>  
  
-   <span data-ttu-id="40bbc-115">가용성 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="40bbc-115">Deleting an availability group.</span></span>  
  
-   <span data-ttu-id="40bbc-116">OS 업그레이드를 위한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="40bbc-116">Cross-cluster migration of AlwaysOn Availability Groups for OS upgrade</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="40bbc-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="40bbc-117">Related Tasks</span></span>  
 <span data-ttu-id="40bbc-118">**기존 가용성 그룹을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-118">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="40bbc-119">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-119">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-120">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-120">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-121">가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-121">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="40bbc-122">가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-122">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-123">가용성 그룹에서 주 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-123">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-124">유연한 장애 조치 (failover) 정책을 구성 하 여 자동 장애 조치 (Failover) &#40;AlwaysOn 가용성 그룹의 조건을 제어&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-124">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;AlwaysOn Availability Groups&#41;</span></span>](configure-flexible-automatic-failover-policy.md)  
  
 <span data-ttu-id="40bbc-125">**가용성 그룹을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-125">**To manage an availability group**</span></span>  
  
-   [<span data-ttu-id="40bbc-126">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-127">가용성 그룹의 계획된 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-127">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-128">가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-128">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-129">가용성 그룹 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-129">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="40bbc-130">**가용성 복제본을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-130">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="40bbc-131">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-131">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-132">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-132">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-133">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-133">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-134">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-134">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-135">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-135">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-136">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-136">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-137">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-137">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-138">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-138">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-139">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-139">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="40bbc-140">**가용성 데이터베이스를 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-140">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="40bbc-141">가용성 그룹에 데이터베이스 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-141">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="40bbc-142">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-142">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-143">가용성 그룹에서 주 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-143">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-144">가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-144">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-145">가용성 데이터베이스 일시 중지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-145">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-146">가용성 데이터베이스 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-146">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
 <span data-ttu-id="40bbc-147">**가용성 그룹을 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-147">**To monitor an availability group**</span></span>  
  
-   [<span data-ttu-id="40bbc-148">가용성 그룹 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-148">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
 <span data-ttu-id="40bbc-149">**새 WSFC 클러스터로 가용성 그룹 마이그레이션(클러스터 간 마이그레이션)을 지원하려면**</span><span class="sxs-lookup"><span data-stu-id="40bbc-149">**To support migrating availability groups to a new WSFC cluster (cross-cluster migration)**</span></span>  
  
-   [<span data-ttu-id="40bbc-150">서버 인스턴스의 HADR 클러스터 컨텍스트 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-150">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [<span data-ttu-id="40bbc-151">가용성 그룹을 오프라인 상태로 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-151">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="40bbc-152">관련 내용</span><span class="sxs-lookup"><span data-stu-id="40bbc-152">Related Content</span></span>  
  
-   <span data-ttu-id="40bbc-153">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="40bbc-153">**Blogs:**</span></span>  
  
     [<span data-ttu-id="40bbc-154">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="40bbc-154">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="40bbc-155">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="40bbc-155">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="40bbc-156">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="40bbc-156">**Videos:**</span></span>  
  
     [<span data-ttu-id="40bbc-157">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="40bbc-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="40bbc-158">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="40bbc-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="40bbc-159">**백서:**</span><span class="sxs-lookup"><span data-stu-id="40bbc-159">**White papers:**</span></span>  
  
     [<span data-ttu-id="40bbc-160">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="40bbc-160">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="40bbc-161">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="40bbc-161">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
  
## <a name="see-also"></a><span data-ttu-id="40bbc-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40bbc-162">See Also</span></span>  
 <span data-ttu-id="40bbc-163">[AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-163">[AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="40bbc-164">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-164">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="40bbc-165">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 서버 인스턴스 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-165">Configuration of a Server Instance for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="40bbc-166">[가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-166">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="40bbc-167">[활성 보조: 읽기 가능한 보조 복제본 &#40;AlwaysOn 가용성 그룹&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-167">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="40bbc-168">활성 보조: 보조 복제본에 대 한 백업 &#40;AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-168">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 <span data-ttu-id="40bbc-169">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-169">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="40bbc-170">[AlwaysOn 가용성 그룹 &#40;SQL Server의 운영 문제에 대 한 AlwaysOn 정책&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-170">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="40bbc-171">[가용성 그룹 모니터링&#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-171">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="40bbc-172">[AlwaysOn 가용성 그룹: &#40;SQL Server 상호 운용성&#41;](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-172">[AlwaysOn Availability Groups: Interoperability &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="40bbc-173">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 Transact-sql 문 개요&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="40bbc-173">[Overview of Transact-SQL Statements for AlwaysOn Availability Groups &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="40bbc-174">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 PowerShell Cmdlet 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="40bbc-174">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
