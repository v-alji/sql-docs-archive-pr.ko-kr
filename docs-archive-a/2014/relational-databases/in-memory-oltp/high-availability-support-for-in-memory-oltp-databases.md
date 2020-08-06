---
title: 메모리 내 OLTP 데이터베이스에 대한 고가용성 지원 | Microsoft 문서
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 092f2b8158bb35286a09103ea645b2aeb1374fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738391"
---
# <a name="high-availability-support-for-in-memory-oltp-databases"></a><span data-ttu-id="aae48-102">메모리 내 OLTP 데이터베이스에 대한 고가용성 지원</span><span class="sxs-lookup"><span data-stu-id="aae48-102">High Availability Support for In-Memory OLTP databases</span></span>
  <span data-ttu-id="aae48-103">원시 컴파일 저장 프로시저가 있거나 없이 메모리 최적화 테이블을 포함하는 데이터베이스는 AlwaysOn 가용성 그룹에서 완전히 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-103">Databases containing memory-optimized tables, with or without native compiled stored procedures, are fully supported with AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="aae48-104">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 개체를 포함하는 데이터베이스의 구성과 지원 방식은 이러한 개체를 포함하지 않는 데이터베이스의 경우와 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-104">There is no difference in the configuration and support for databases which contain [!INCLUDE[hek_2](../../includes/hek-2-md.md)] objects as compared to those without,</span></span>  
  
## <a name="alwayson-availability-groups-and-in-memory-oltp-databases"></a><span data-ttu-id="aae48-105">AlwaysOn 가용성 그룹 및 메모리 내 OLTP 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="aae48-105">AlwaysOn Availability Groups and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="aae48-106">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 구성 요소를 통한 데이터베이스 구성에는 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-106">Configuring databases with [!INCLUDE[hek_2](../../includes/hek-2-md.md)] components provides the following:</span></span>  
  
-   <span data-ttu-id="aae48-107">**완전 통합 환경** </span><span class="sxs-lookup"><span data-stu-id="aae48-107">**A fully integrated experience** </span></span>  
    <span data-ttu-id="aae48-108">동기 및 비동기 보조 복제본에 대해 동일한 지원 수준으로 동일한 마법사를 사용하여 메모리 최적화 테이블을 포함하는 데이터베이스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-108">You can configure your databases containing memory-optimized tables using the same wizard with the same level of support for both synchronous and asynchronous secondary replicas.</span></span> <span data-ttu-id="aae48-109">또한 SQL Server Management Studio의 친숙한 AlwaysOn 대시보드를 사용하여 상태 모니터링이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-109">Additionally, health monitoring is provided using the familiar AlwaysOn dashboard in SQL Server Management Studio.</span></span>  
  
-   <span data-ttu-id="aae48-110">**동등한 장애 조치(failover) 시간** </span><span class="sxs-lookup"><span data-stu-id="aae48-110">**Comparable Failover time** </span></span>  
    <span data-ttu-id="aae48-111">보조 복제본은 메모리 최적화 지속형 테이블의 메모리 내 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-111">Secondary replicas maintain the in-memory state of the durable memory-optimized tables.</span></span> <span data-ttu-id="aae48-112">복구가 필요하지 않으므로, 자동 또는 강제 장애 조치 발생 시 새로운 주 항목으로의 페일오버 시간이 디스크 기반 테이블과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-112">In the event of automatic or forced failover, the time to failover to the new primary is comparable to disk-bases tables as no recovery is needed.</span></span> <span data-ttu-id="aae48-113">SCHEMA_ONLY로 생성되는 메모리 액세스에 최적화된 테이블이 이 구성에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-113">Memory-optimized tables created as SCHEMA_ONLY are supported in this configuration.</span></span> <span data-ttu-id="aae48-114">그러나 이러한 테이블에 대한 변경 사항은 기록되지 않으므로 보조 복제본의 이 테이블에는 데이터가 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-114">However changes to these tables are not logged and therefore no data will exist in these tables on the secondary replica.</span></span>  
  
-   <span data-ttu-id="aae48-115">**읽기용 보조** </span><span class="sxs-lookup"><span data-stu-id="aae48-115">**Readable Secondary** </span></span>  
    <span data-ttu-id="aae48-116">읽기용으로 구성된 경우 보조 복제본의 메모리 최적화 테이블을 액세스 및 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-116">You can access and query memory-optimized tables on the secondary replica if it has been configured for read access.</span></span> <span data-ttu-id="aae48-117">자세한 내용은 [활성 보조: 읽기 가능한 보조 복제본(AlwaysOn 가용성 그룹)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aae48-117">For more information see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="failover-clustering-instance-fci-and-in-memory-oltp-databases"></a><span data-ttu-id="aae48-118">장애 조치 클러스터링 인스턴스(FCI) 및 메모리 내 OLTP 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="aae48-118">Failover Clustering Instance (FCI) and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="aae48-119">공유 스토리지 구성에서 고가용성을 달성하기 위해, 메모리 최적화 테이블이 포함된 하나 이상의 데이터베이스를 통해 인스턴스에서 장애 조치(failover) 클러스터링을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-119">To achieve high-availability in a shared-storage configuration, you can setup failover clustering on instances with one or more database with memory-optimized tables.</span></span> <span data-ttu-id="aae48-120">FCI는 설정의 일부로 다음과 같은 요소를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-120">You need to consider the following factors as part of setting up an FCI.</span></span>  
  
-   <span data-ttu-id="aae48-121">**복구 시간 목표** </span><span class="sxs-lookup"><span data-stu-id="aae48-121">**Recovery Time Objective** </span></span>  
    <span data-ttu-id="aae48-122">메모리 최적화 테이블을 메모리에 로드해야 데이터베이스를 사용할 수 있으므로 장애 조치(failover) 시간이 더 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-122">Failover time will likely to be higher as the memory-optimized tables must be loaded into memory before the database is made available.</span></span>  
  
-   <span data-ttu-id="aae48-123">**SCHEMA_ONLY 테이블** </span><span class="sxs-lookup"><span data-stu-id="aae48-123">**SCHEMA_ONLY tables** </span></span>  
    <span data-ttu-id="aae48-124">장애 조치(failover) 후 SCHEMA_ONLY 테이블은 행 없이 비어 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-124">Be aware that SCHEMA_ONLY tables will be empty with no rows after the failover.</span></span> <span data-ttu-id="aae48-125">이것이 애플리케이션에서 설계 및 정의한 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-125">This is as designed and defined by the application.</span></span> <span data-ttu-id="aae48-126">하나 이상의 SCHEMA_ONLY 테이블이 있는 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 데이터베이스를 다시 시작할 때도 똑같이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-126">This is exactly the same behavior when you restart an [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database with one or more SCHEMA_ONLY tables.</span></span>  
  
## <a name="support-for-transaction-replication-in-in-memory-oltp"></a><span data-ttu-id="aae48-127">메모리 내 OLTP에서 트랜잭션 복제 지원</span><span class="sxs-lookup"><span data-stu-id="aae48-127">Support for transaction replication in In-Memory OLTP</span></span>  
 <span data-ttu-id="aae48-128">피어 투 피어 트랜잭션 복제를 제외하고 트랜잭션 복제 구독자 역할을 수행하는 테이블은 메모리 최적화 테이블로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-128">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="aae48-129">다른 복제 구성은 메모리 최적화 테이블과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aae48-129">Other replication configurations are not compatible with memory-optimized tables.</span></span>  <span data-ttu-id="aae48-130">자세한 내용은 [메모리 액세스에 최적화된 테이블 구독자로 복제](../replication/replication-to-memory-optimized-table-subscribers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aae48-130">For more information see [Replication to Memory-Optimized Table Subscribers](../replication/replication-to-memory-optimized-table-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae48-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aae48-131">See Also</span></span>  
 <span data-ttu-id="aae48-132">[AlwaysOn 가용성 그룹 (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aae48-132">[AlwaysOn Availability Groups (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="aae48-133">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aae48-133">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="aae48-134">[활성 보조: 읽기 가능한 보조 복제본 &#40;AlwaysOn 가용성 그룹&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="aae48-134">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="aae48-135">메모리 액세스에 최적화된 테이블 구독자로 복제</span><span class="sxs-lookup"><span data-stu-id="aae48-135">Replication to Memory-Optimized Table Subscribers</span></span>](../replication/replication-to-memory-optimized-table-subscribers.md)  
  
  
