---
title: SQL Server, Workload Group Stats 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb363803c562b305687e78e1315f1c4255041b1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649018"
---
# <a name="sql-server-workload-group-stats-object"></a><span data-ttu-id="25c06-102">SQL Server, Workload Group Stats 개체</span><span class="sxs-lookup"><span data-stu-id="25c06-102">SQL Server, Workload Group Stats Object</span></span>
  <span data-ttu-id="25c06-103">SQLServer:Workload Group Stats 개체는 리소스 관리자 작업 그룹 통계에 대한 정보를 보고하는 성능 카운터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-103">The SQLServer:Workload Group Stats object contains performance counters that report information about Resource Governor workload group statistics.</span></span>  
  
 <span data-ttu-id="25c06-104">각 활성 작업 그룹은 리소스 관리자 작업 그룹 이름과 동일한 인스턴스 이름으로 SQLServer:Workload Group Stats 성능 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-104">Each active workload group creates an instance of the SQLServer:Workload Group Stats performance object that has the same instance name as the Resource Governor workload group name.</span></span> <span data-ttu-id="25c06-105">다음 표에서는 이 인스턴스에서 지원하는 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-105">The following table describes counters supported on this instance.</span></span>  
  
|<span data-ttu-id="25c06-106">카운터 이름</span><span class="sxs-lookup"><span data-stu-id="25c06-106">Counter name</span></span>|<span data-ttu-id="25c06-107">Description</span><span class="sxs-lookup"><span data-stu-id="25c06-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="25c06-108">Queued requests</span><span class="sxs-lookup"><span data-stu-id="25c06-108">Queued requests</span></span>|<span data-ttu-id="25c06-109">선택을 기다리면서 큐에 대기 중인 요청의 현재 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-109">The current number of queued requests that is waiting to be picked up.</span></span> <span data-ttu-id="25c06-110">GROUP_MAX_REQUESTS 한도에 도달한 후 스로틀이 발생할 경우 이 카운트는 0일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-110">This count can be non-zero if throttling occurs after the GROUP_MAX_REQUESTS limit is reached.</span></span>|  
|<span data-ttu-id="25c06-111">Active requests</span><span class="sxs-lookup"><span data-stu-id="25c06-111">Active requests</span></span>|<span data-ttu-id="25c06-112">현재 작업 그룹에서 현재 실행 중인 요청 수로,</span><span class="sxs-lookup"><span data-stu-id="25c06-112">The number of requests that are currently running in this workload group.</span></span> <span data-ttu-id="25c06-113">그룹 ID로 필터링된 sys.dm_exec_requests의 행 개수와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-113">This should be equivalent to the count of rows from sys.dm_exec_requests filtered by group ID.</span></span>|  
|<span data-ttu-id="25c06-114">Requests completed/sec</span><span class="sxs-lookup"><span data-stu-id="25c06-114">Requests completed/sec</span></span>|<span data-ttu-id="25c06-115">현재 작업 그룹에서 완료된 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-115">The number of requests that have completed in this workload group.</span></span> <span data-ttu-id="25c06-116">이 숫자는 누적됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-116">This number is cumulative.</span></span>|  
|<span data-ttu-id="25c06-117">CPU usage %</span><span class="sxs-lookup"><span data-stu-id="25c06-117">CPU usage %</span></span>|<span data-ttu-id="25c06-118">현재 작업 그룹에 있는 모든 요청에 의한 CPU 대역폭 사용량으로, 컴퓨터를 기준으로 측정되고 시스템에 있는 모든 CPU를 기준으로 평균화됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-118">The CPU bandwidth usage by all requests in this workload group measured relative to the computer and normalized to all the CPUs on the system.</span></span> <span data-ttu-id="25c06-119">이 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 사용할 수 있는 CPU 양이 변경되면 그에 따라 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-119">This value will change as the amount of CPU available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process changes.</span></span> <span data-ttu-id="25c06-120">이 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 전달되는 CPU를 기준으로는 평균화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-120">It is not normalized to what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process receives.</span></span>|  
|<span data-ttu-id="25c06-121">Max request CPU time (ms)</span><span class="sxs-lookup"><span data-stu-id="25c06-121">Max request CPU time (ms)</span></span>|<span data-ttu-id="25c06-122">작업 그룹에서 현재 실행 중인 요청에 의해 사용되는 최대 CPU 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-122">The maximum CPU time, in milliseconds, used by a request currently running in the workload group.</span></span>|  
|<span data-ttu-id="25c06-123">Blocked requests</span><span class="sxs-lookup"><span data-stu-id="25c06-123">Blocked requests</span></span>|<span data-ttu-id="25c06-124">현재 작업 그룹에 있는 차단된 요청의 현재 수로,</span><span class="sxs-lookup"><span data-stu-id="25c06-124">The current number of blocked requests in the workload group.</span></span> <span data-ttu-id="25c06-125">작업 특성을 결정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-125">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="25c06-126">Reduced memory grants/sec</span><span class="sxs-lookup"><span data-stu-id="25c06-126">Reduced memory grants/sec</span></span>|<span data-ttu-id="25c06-127">이상적인 초당 메모리 부여 양보다 줄어든 쿼리 수입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-127">The number of queries that are getting less than ideal amount of memory grants per second.</span></span>|  
|<span data-ttu-id="25c06-128">Max request memory grant (KB)</span><span class="sxs-lookup"><span data-stu-id="25c06-128">Max request memory grant (KB)</span></span>|<span data-ttu-id="25c06-129">쿼리를 위한 최대 메모리 부여 값(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-129">The maximum value of memory grant, in kilobytes (KB), for a query.</span></span>|  
|<span data-ttu-id="25c06-130">Query optimizations/sec</span><span class="sxs-lookup"><span data-stu-id="25c06-130">Query optimizations/sec</span></span>|<span data-ttu-id="25c06-131">현재 작업 그룹에서 초당 발생한 쿼리 최적화의 수로,</span><span class="sxs-lookup"><span data-stu-id="25c06-131">The number of query optimizations that have happened in this workload group per second.</span></span> <span data-ttu-id="25c06-132">작업 특성을 결정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-132">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="25c06-133">Suboptimal plans/sec</span><span class="sxs-lookup"><span data-stu-id="25c06-133">Suboptimal plans/sec</span></span>|<span data-ttu-id="25c06-134">현재 작업 그룹에서 초당 생성되는 만족스럽지 못한 계획의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-134">The number of suboptimal plans that are generated in this workload group per second.</span></span>|  
|<span data-ttu-id="25c06-135">Active parallel threads</span><span class="sxs-lookup"><span data-stu-id="25c06-135">Active parallel threads</span></span>|<span data-ttu-id="25c06-136">병렬 스레드 사용량의 현재 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="25c06-136">The current count of parallel threads usage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25c06-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25c06-137">See Also</span></span>  
 <span data-ttu-id="25c06-138">[리소스 사용 모니터링&#40;시스템 모니터&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="25c06-138">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="25c06-139">[SQLServer, Resource Pool Stats 개체](sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="25c06-139">[SQL Server, Resource Pool Stats Object](sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="25c06-140">리소스 관리자</span><span class="sxs-lookup"><span data-stu-id="25c06-140">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
