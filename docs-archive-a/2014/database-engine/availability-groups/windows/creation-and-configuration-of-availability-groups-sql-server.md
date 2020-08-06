---
title: 가용성 그룹 만들기 및 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc33da393527c19985f5e7b214ba4bc02dc2f3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743444"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a><span data-ttu-id="06f2d-102">가용성 그룹의 생성 및 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06f2d-102">Creation and Configuration of Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="06f2d-103">이 섹션의 항목에서는 단일 WSFC 장애 조치(Failover) 클러스터 내의 여러 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인스턴스에 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 구현을 배포하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06f2d-103">The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] that reside on different Windows Server Failover Clustering (WSFC) nodes within a single WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="06f2d-104">첫 번째 가용성 그룹을 만들기 전에 다음 항목의 정보를 숙지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="06f2d-104">Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:</span></span>  
  
 [<span data-ttu-id="06f2d-105">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-105">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
 <span data-ttu-id="06f2d-106">이 항목에서는 컴퓨터의 사전 요구 사항, 제한 사항 및 권장 사항과 WSFC 노드, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스, 가용성 그룹, 복제본 및 데이터베이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06f2d-106">This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; availability groups, replicas, and databases.</span></span> <span data-ttu-id="06f2d-107">이 항목에는 보안 고려 사항에 대한 정보도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06f2d-107">This topic also contains information about security considerations.</span></span>  
  
 [<span data-ttu-id="06f2d-108">AlwaysOn 가용성 그룹 &#40;SQL Server 시작 하기&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-108">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="06f2d-109">서버 인스턴스 구성, 가용성 그룹 만들기, 클라이언트 연결을 위한 가용성 그룹 구성, 가용성 그룹 관리 및 가용성 그룹 모니터링 단계에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="06f2d-109">Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="06f2d-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="06f2d-110">Related Tasks</span></span>  
 <span data-ttu-id="06f2d-111">**다음에 대한 서버 인스턴스를 구성하려면 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="06f2d-111">**To configure a server instance for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span></span>  
  
-   [<span data-ttu-id="06f2d-112">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-112">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-113">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-113">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="06f2d-114">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-114">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="06f2d-115">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-115">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 <span data-ttu-id="06f2d-116">**AlwaysOn 가용성 그룹 구성을 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="06f2d-116">**To get started with configuring AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="06f2d-117">AlwaysOn 가용성 그룹 &#40;SQL Server 시작 하기&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-117">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="06f2d-118">**새 가용성 그룹을 만들고 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="06f2d-118">**To create and configure a new availability group**</span></span>  
  
-   [<span data-ttu-id="06f2d-119">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-119">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="06f2d-120">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-120">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="06f2d-121">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-121">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="06f2d-122">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-122">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="06f2d-123">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-123">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="06f2d-124">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-124">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-125">유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치의 상태 제어(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="06f2d-125">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="06f2d-126">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-127">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-127">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-128">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-128">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-129">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-129">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-130">AlwaysOn 보조 데이터베이스에서 데이터 이동을 시작 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-130">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-131">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-131">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-132">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-132">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-133">가용성 그룹의 데이터베이스에 대한 로그인 및 작업 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-133">Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;</span></span>](../../logins-and-jobs-for-availability-group-databases.md)  
  
 <span data-ttu-id="06f2d-134">**문제를 해결 하려면**</span><span class="sxs-lookup"><span data-stu-id="06f2d-134">**To troubleshoot**</span></span>  
  
-   [<span data-ttu-id="06f2d-135">삭제 된 SQL Server (AlwaysOn 가용성 그룹 구성) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="06f2d-135">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="06f2d-136">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="06f2d-136">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="06f2d-137">관련 내용</span><span class="sxs-lookup"><span data-stu-id="06f2d-137">Related Content</span></span>  
  
-   <span data-ttu-id="06f2d-138">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="06f2d-138">**Blogs:**</span></span>  
  
     [<span data-ttu-id="06f2d-139">AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용</span><span class="sxs-lookup"><span data-stu-id="06f2d-139">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="06f2d-140">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="06f2d-140">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="06f2d-141">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="06f2d-141">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="06f2d-142">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="06f2d-142">**Videos:**</span></span>  
  
     [<span data-ttu-id="06f2d-143">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="06f2d-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="06f2d-144">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="06f2d-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="06f2d-145">**백서:**</span><span class="sxs-lookup"><span data-stu-id="06f2d-145">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="06f2d-146">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="06f2d-146">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="06f2d-147">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="06f2d-147">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="06f2d-148">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="06f2d-148">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="06f2d-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06f2d-149">See Also</span></span>  
 <span data-ttu-id="06f2d-150">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06f2d-150">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="06f2d-151">[가용성 그룹 관리 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06f2d-151">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="06f2d-152">[AlwaysOn 가용성 그룹의 작업 문제에 대 한 AlwaysOn 정책 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="06f2d-152">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="06f2d-153">[가용성 그룹 모니터링&#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06f2d-153">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="06f2d-154">AlwaysOn 가용성 그룹: 상호 운용성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06f2d-154">AlwaysOn Availability Groups: Interoperability (SQL Server)</span></span>](always-on-availability-groups-interoperability-sql-server.md)  
  
