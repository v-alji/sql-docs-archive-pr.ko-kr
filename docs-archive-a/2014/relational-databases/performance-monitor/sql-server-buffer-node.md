---
title: SQL Server:Buffer Node | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14659e4c1191e2260bccdbcd612f510770913629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653812"
---
# <a name="sql-serverbuffer-node"></a><span data-ttu-id="6ba89-102">SQL Server:Buffer Node</span><span class="sxs-lookup"><span data-stu-id="6ba89-102">SQL Server:Buffer Node</span></span>
  <span data-ttu-id="6ba89-103">**Buffer Node** 개체는 **Buffer Manager** 개체가 제공하는 카운터를 보완하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-103">The **Buffer Node** object provides counters that complement counters provided by the **Buffer Manager** object.</span></span> <span data-ttu-id="6ba89-104">이 카운터를 사용하여 각 NUMA(Non-Uniform Memory Access) 노드에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버퍼 풀 페이지 배포를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-104">It allows you to monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool page distribution for each non-uniform memory access (NUMA) node.</span></span> <span data-ttu-id="6ba89-105">사용 중인 각 NUMA 노드에 대해 하나의 **Buffer Node** 개체 인스턴스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-105">There is an instance of the **Buffer Node** object for each NUMA node in use.</span></span> <span data-ttu-id="6ba89-106">비-NUMA 아키텍처에는 단일 **Buffer Node** 개체 인스턴스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-106">On non-NUMA architecture, there will be a single instance of the **Buffer Node** object.</span></span>  
  
## <a name="buffer-node-performance-objects"></a><span data-ttu-id="6ba89-107">Buffer Node 성능 개체</span><span class="sxs-lookup"><span data-stu-id="6ba89-107">Buffer Node Performance Objects</span></span>  
 <span data-ttu-id="6ba89-108">이 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** 성능 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** performance objects.</span></span>  
  
|<span data-ttu-id="6ba89-109">SQL Server Buffer Node 카운터</span><span class="sxs-lookup"><span data-stu-id="6ba89-109">SQL Server Buffer Node counters</span></span>|<span data-ttu-id="6ba89-110">Description</span><span class="sxs-lookup"><span data-stu-id="6ba89-110">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="6ba89-111">**Database pages**</span><span class="sxs-lookup"><span data-stu-id="6ba89-111">**Database pages**</span></span>|<span data-ttu-id="6ba89-112">이 노드의 버퍼 풀에서 데이터베이스 내용이 있는 페이지 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-112">Indicates the number of pages in the buffer pool on this node with database content.</span></span>|  
|<span data-ttu-id="6ba89-113">**Page life expectancy**</span><span class="sxs-lookup"><span data-stu-id="6ba89-113">**Page life expectancy**</span></span>|<span data-ttu-id="6ba89-114">페이지가 참조 없이 이 노드의 버퍼 풀에 남아 있는 최소 시간(초)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-114">Indicates the minimum number of seconds a page will stay in the buffer pool on this node without references.</span></span>|  
|<span data-ttu-id="6ba89-115">**Local Node page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="6ba89-115">**Local Node page lookups/sec**</span></span>|<span data-ttu-id="6ba89-116">이 노드에서 충족된 조회 요청 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-116">Indicates the number of lookup requests from this node which were satisfied from this node.</span></span>|  
|<span data-ttu-id="6ba89-117">**Remote Note page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="6ba89-117">**Remote Note page lookups/sec**</span></span>|<span data-ttu-id="6ba89-118">다른 노드에서 충족된 이 노드의 조회 요청 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-118">Indicates the number of lookup requests from this node which were satisfied from other nodes.</span></span>|  
  
 <span data-ttu-id="6ba89-119">비-NUMA 하드웨어에서 SQL Server를 실행하는 경우 **Buffer Node** 및 **Buffer Manager** 개체의 카운터가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-119">If SQL Server is running on non-NUMA hardware, the counters of **Buffer Node** and **Buffer Manager** objects should match.</span></span>  
  
 <span data-ttu-id="6ba89-120">NUMA 하드웨어에서 모든 **Buffer Nodes** 의 각 카운터 합계는 **Buffer Manager**의 해당 합계와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-120">On NUMA hardware, sums of respective counters of all **Buffer Nodes** should match their counterparts of **Buffer Manager**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ba89-121">카운터의 동적 특성과 샘플링 정확도 때문에 카운터 값과 합계가 정확하게 일치하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba89-121">The counter values and sums may not match precisely due to the dynamic nature of the counters and the sampling accuracy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba89-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ba89-122">See Also</span></span>  
 <span data-ttu-id="6ba89-123">[SQL Server, Buffer Manager 개체](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="6ba89-123">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 <span data-ttu-id="6ba89-124">[서버 메모리 서버 구성 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="6ba89-124">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="6ba89-125">[리소스 사용 모니터링&#40;시스템 모니터&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6ba89-125">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="6ba89-126">sys.dm_os_performance_counters&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6ba89-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
