---
title: SQL Server (Always On 가용성 그룹)에 대 한 서버 인스턴스 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3392e6189b687516e627d847acceedb165141117
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741315"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="4efbd-102">Always On 가용성 그룹에 대한 서버 인스턴스 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4efbd-102">Configuration of a Server Instance for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="4efbd-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 를 지원할 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]인스턴스 구성 요구 사항에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-103">This topic contains information about the requirements for configuring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4efbd-104">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 필수 조건 및 제한 사항에 대한 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4efbd-104">For essential information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites and restrictions for Windows Server Failover Clustering (WSFC) nodes and for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="4efbd-105">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="4efbd-105">Terms and Definitions</span></span>  
  
 <span data-ttu-id="4efbd-106">데이터베이스 미러링에 대한 엔터프라이즈 수준의 대안을 제공하는 고가용성 및 재해 복구 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-106">A high-availability and disaster-recovery solution that provides an enterprise-level replacement for database mirroring.</span></span> <span data-ttu-id="4efbd-107">*가용성 그룹* 은 함께 장애 조치 (failover) 되는 사용자 데이터베이스의 불연속 집합 ( *가용성 데이터베이스*라고 함)에 대 한 장애 조치 (failover) 환경을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-107">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="4efbd-108">가용성 복제본</span><span class="sxs-lookup"><span data-stu-id="4efbd-108">availability replica</span></span>  
 <span data-ttu-id="4efbd-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 특정 인스턴스에 의해 호스팅되고 가용성 그룹에 속하는 각 가용성 데이터베이스의 로컬 복사본을 유지 관리하는 가용성 그룹 인스턴스화입니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-109">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and that maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="4efbd-110">가용성 복제본에는 *주 복제본* 과 1-4개의 *보조 복제본*이라는 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-110">Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*.</span></span> <span data-ttu-id="4efbd-111">지정된 가용성 그룹에 대한 가용성 복제본을 호스팅하는 서버 인스턴스는 단일 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터의 다른 노드에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-111">The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 [<span data-ttu-id="4efbd-112">데이터베이스 미러링 끝점</span><span class="sxs-lookup"><span data-stu-id="4efbd-112">database mirroring endpoint</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 <span data-ttu-id="4efbd-113">SQL Server는 SQL Server 개체인 엔드포인트를 사용하여 네트워크를 통해 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-113">An endpoint is a SQL Server object that enables SQL Server to communicate over the network.</span></span> <span data-ttu-id="4efbd-114">데이터베이스 미러링 및/또는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 참여하려면 서버 인스턴스에 특수 전용 엔드포인트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-114">To participate in database mirroring and/or [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] a server instance requires a special, dedicated endpoint.</span></span> <span data-ttu-id="4efbd-115">서버 인스턴스의 모든 미러링 및 가용성 그룹 연결은 동일한 데이터베이스 미러링 엔드포인트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-115">All mirroring and availability group connections on a server instance use the same database mirroring endpoint.</span></span> <span data-ttu-id="4efbd-116">데이터베이스 미러링 엔드포인트는 다른 서버 인스턴스로부터 이러한 연결을 받는 데만 사용되는 특별한 용도의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-116">This endpoint is a special-purpose endpoint used exclusively to receive these connections from other server instances.</span></span>  
  
##  <a name="to-configure-a-server-instance-to-support-alwayson-availability-groups"></a><a name="ConfigSI"></a><span data-ttu-id="4efbd-117">AlwaysOn 가용성 그룹을 지원 하도록 서버 인스턴스를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="4efbd-117">To Configure a Server Instance to Support AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="4efbd-118">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원하려면 서버 인스턴스가 가용성 그룹을 호스팅하는 WSFC 장애 조치(Failover) 클러스터의 노드에 있어야 하고, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]이 설정되어 있어야 하며, 데이터베이스 미러링 엔드포인트를 보유하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-118">To support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a server instance must reside on a node in the WSFC failover cluster that hosts the availability group, be [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled, and possess a database mirroring endpoint.</span></span>  
  
1.  <span data-ttu-id="4efbd-119">하나 이상의 가용성 그룹에 참여할 모든 서버 인스턴스에서 AlwaysOn 가용성 그룹 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-119">Enable the AlwaysOn Availability Groups feature on every server instance that is to participate in one or more availability groups.</span></span> <span data-ttu-id="4efbd-120">특정 서버 인스턴스에서는 특정 가용성 그룹에 대한 단일 가용성 복제본만 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-120">A given server instance can host only a single availability replica for a given availability group.</span></span>  
  
2.  <span data-ttu-id="4efbd-121">서버 인스턴스에 데이터베이스 미러링 엔드포인트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4efbd-121">Ensure that the server instance possesses a database mirroring endpoint.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4efbd-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4efbd-122">Related Tasks</span></span>  
 <span data-ttu-id="4efbd-123">**AlwaysOn 가용성 그룹을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="4efbd-123">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="4efbd-124">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4efbd-124">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="4efbd-125">**데이터베이스 미러링 엔드포인트가 있는지 여부를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="4efbd-125">**To determine whether a database mirroring endpoint exists**</span></span>  
  
-   [<span data-ttu-id="4efbd-126">sys.database_mirroring_endpoints&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4efbd-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="4efbd-127">**데이터베이스 미러링 엔드포인트를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="4efbd-127">**To create a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="4efbd-128">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="4efbd-128">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="4efbd-129">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4efbd-129">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="4efbd-130">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4efbd-130">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="4efbd-131">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4efbd-131">Related Content</span></span>  
  
-   <span data-ttu-id="4efbd-132">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="4efbd-132">**Blogs:**</span></span>  
  
     [<span data-ttu-id="4efbd-133">AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용</span><span class="sxs-lookup"><span data-stu-id="4efbd-133">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="4efbd-134">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="4efbd-134">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="4efbd-135">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="4efbd-135">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="4efbd-136">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="4efbd-136">**Videos:**</span></span>  
  
     [<span data-ttu-id="4efbd-137">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="4efbd-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="4efbd-138">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="4efbd-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="4efbd-139">**백서:**</span><span class="sxs-lookup"><span data-stu-id="4efbd-139">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="4efbd-140">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="4efbd-140">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="4efbd-141">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="4efbd-141">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="4efbd-142">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="4efbd-142">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="4efbd-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4efbd-143">See Also</span></span>  
 <span data-ttu-id="4efbd-144">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-144">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="4efbd-145">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-145">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="4efbd-146">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-146">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="4efbd-147">[AlwaysOn 가용성 그룹: 상호 운용성 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-147">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="4efbd-148">[장애 조치 (Failover) 클러스터링 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-148">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="4efbd-149">[SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4efbd-149">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="4efbd-150">AlwaysOn 장애 조치 (Failover) 클러스터 인스턴스</span><span class="sxs-lookup"><span data-stu-id="4efbd-150">AlwaysOn Failover Cluster Instances</span></span>](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
