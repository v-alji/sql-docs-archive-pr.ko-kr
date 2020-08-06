---
title: 'Always On 가용성 그룹: 상호 운용성(SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647250"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a><span data-ttu-id="3dbf6-102">Always On 가용성 그룹: 상호 운용성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3dbf6-102">Always On Availability Groups: Interoperability (SQL Server)</span></span>
  <span data-ttu-id="3dbf6-103">이 항목에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 다른 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]기능과의 상호 운용성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-103">This topic documents interoperability of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] with other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a><span data-ttu-id="3dbf6-104">AlwaysOn 가용성 그룹와 상호 운용 하는 기능</span><span class="sxs-lookup"><span data-stu-id="3dbf6-104">Features That Interoperate with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="3dbf6-105">다음 표에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 과 상호 운용하는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]기능이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-105">The following table lists [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features that interoperate with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3dbf6-106">**추가 정보** 열의 링크는 해당 기능에 대해 상호 운용성 고려 사항이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-106">A link in the **More Information** column indicates that interoperability considerations exist for a given feature.</span></span>  
  
|<span data-ttu-id="3dbf6-107">기능</span><span class="sxs-lookup"><span data-stu-id="3dbf6-107">Feature</span></span>|<span data-ttu-id="3dbf6-108">추가 정보</span><span class="sxs-lookup"><span data-stu-id="3dbf6-108">More Information</span></span>|  
|-------------|----------------------|  
|<span data-ttu-id="3dbf6-109">변경 데이터 캡처</span><span class="sxs-lookup"><span data-stu-id="3dbf6-109">Change data capture</span></span>|[<span data-ttu-id="3dbf6-110">복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-110">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="3dbf6-111">Change tracking</span><span class="sxs-lookup"><span data-stu-id="3dbf6-111">Change tracking</span></span>|[<span data-ttu-id="3dbf6-112">복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-112">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="3dbf6-113">포함된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="3dbf6-113">Contained databases</span></span>|[<span data-ttu-id="3dbf6-114">AlwaysOn 가용성 그룹에 포함된 데이터베이스(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3dbf6-114">Contained Databases with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-115">데이터베이스 암호화</span><span class="sxs-lookup"><span data-stu-id="3dbf6-115">Database encryption</span></span>|[<span data-ttu-id="3dbf6-116">AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하는 암호화 된 데이터베이스&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-116">Encrypted Databases with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-117">데이터베이스 스냅샷</span><span class="sxs-lookup"><span data-stu-id="3dbf6-117">Database snapshots</span></span>|[<span data-ttu-id="3dbf6-118">AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하는 데이터베이스 스냅숏&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-118">Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-119">FILESTREAM 및 FileTable</span><span class="sxs-lookup"><span data-stu-id="3dbf6-119">FILESTREAM and FileTable</span></span>|[<span data-ttu-id="3dbf6-120">AlwaysOn 가용성 그룹 &#40;SQL Server FILESTREAM 및 FileTable&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-120">FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-121">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="3dbf6-121">Full-text search</span></span>|<span data-ttu-id="3dbf6-122">참고: 전체 텍스트 인덱스는 AlwaysOn 보조 데이터베이스와 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-122">Note: Full-Text indexes are synchronized with AlwaysOn secondary databases.</span></span>|  
|<span data-ttu-id="3dbf6-123">로그 전달</span><span class="sxs-lookup"><span data-stu-id="3dbf6-123">Log shipping</span></span>|[<span data-ttu-id="3dbf6-124">로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server로 마이그레이션하기 위한 필수 구성 요소&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-124">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|<span data-ttu-id="3dbf6-125">RBS(Remote Blob Store)</span><span class="sxs-lookup"><span data-stu-id="3dbf6-125">Remote Blob Store (RBS)</span></span>|[<span data-ttu-id="3dbf6-126">RBS&#41; 및 AlwaysOn 가용성 그룹 &#40;SQL Server &#40;Remote Blob Store</span><span class="sxs-lookup"><span data-stu-id="3dbf6-126">Remote Blob Store &#40;RBS&#41; and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-127">복제에서[AlwaysOn 가용성 그룹에 대 한 복제 구성 (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="3dbf6-127">Replication[Configure Replication for AlwaysOn Availability Groups (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span></span><br /><br /> [<span data-ttu-id="3dbf6-128">AlwaysOn 게시 데이터베이스를 유지 관리 하는 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-128">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [<span data-ttu-id="3dbf6-129">복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-129">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [<span data-ttu-id="3dbf6-130">복제 구독자 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-130">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-131">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="3dbf6-131">Analysis Services</span></span>|[<span data-ttu-id="3dbf6-132">AlwaysOn 가용성 그룹이 포함된 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="3dbf6-132">Analysis Services with AlwaysOn Availability Groups</span></span>](analysis-services-with-always-on-availability-groups.md)|  
|<span data-ttu-id="3dbf6-133">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="3dbf6-133">Reporting Services</span></span>|<span data-ttu-id="3dbf6-134">읽기 전용 보조 복제본을 보고 데이터 원본으로 사용하고 주 읽기/쓰기 주 복제본에 대한 부하를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-134">Utilize read only secondary replicas as a reporting data source and reduce the load on your primary read-write replica.</span></span><br /><br /> [<span data-ttu-id="3dbf6-135">AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하 여 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-135">Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-136">Service Broker</span><span class="sxs-lookup"><span data-stu-id="3dbf6-136">Service Broker</span></span>|[<span data-ttu-id="3dbf6-137">AlwaysOn 가용성 그룹 &#40;SQL Server를 사용 하 여 Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-137">Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](service-broker-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="3dbf6-138">SQL Server 에이전트</span><span class="sxs-lookup"><span data-stu-id="3dbf6-138">SQL Server Agent</span></span>||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a><span data-ttu-id="3dbf6-139">AlwaysOn 가용성 그룹와 상호 운용 되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="3dbf6-139">Features that Do Not Interoperate with AlwaysOn Availability Groups</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="3dbf6-140">은 다음 기능과 상호 운용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-140">does not interoperate with the following features:</span></span>  
  
-   <span data-ttu-id="3dbf6-141">데이터베이스 간 트랜잭션/분산 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="3dbf6-141">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="3dbf6-142">해당 트랜잭션이 지원되지 않는 이유에 대한 자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3dbf6-142">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="3dbf6-143">데이터베이스 미러링</span><span class="sxs-lookup"><span data-stu-id="3dbf6-143">Database mirroring</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="3dbf6-144">관련 내용</span><span class="sxs-lookup"><span data-stu-id="3dbf6-144">Related Content</span></span>  
  
-   <span data-ttu-id="3dbf6-145">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="3dbf6-145">**Blogs:**</span></span>  
  
     [<span data-ttu-id="3dbf6-146">마이그레이션 가이드: 이전 클러스터링 및 미러링 배포에서 SQL Server 2012 장애 조치(Failover) 클러스터링 및 가용성 그룹으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="3dbf6-146">Migration Guide: Migrating to SQL Server 2012 Failover Clustering and Availability Groups from Prior Clustering and Mirroring Deployments</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [<span data-ttu-id="3dbf6-147">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="3dbf6-147">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="3dbf6-148">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="3dbf6-148">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="3dbf6-149">**백서:**</span><span class="sxs-lookup"><span data-stu-id="3dbf6-149">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="3dbf6-150">마이그레이션 가이드: 데이터베이스 미러링 및 로그 전달을 조합하는 이전 배포에서 AlwaysOn 가용성 그룹으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="3dbf6-150">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="3dbf6-151">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="3dbf6-151">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="3dbf6-152">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="3dbf6-152">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="3dbf6-153">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="3dbf6-153">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="3dbf6-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3dbf6-154">See Also</span></span>  
 <span data-ttu-id="3dbf6-155">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3dbf6-155">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3dbf6-156">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="3dbf6-156">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
