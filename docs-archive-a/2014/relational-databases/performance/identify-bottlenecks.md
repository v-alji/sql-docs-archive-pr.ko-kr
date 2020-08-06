---
title: 병목 상태 식별 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e941b3f4a1185177cef007eb6a02a71ae1adece7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729383"
---
# <a name="identify-bottlenecks"></a><span data-ttu-id="bffaf-102">병목 상태 식별</span><span class="sxs-lookup"><span data-stu-id="bffaf-102">Identify Bottlenecks</span></span>
  <span data-ttu-id="bffaf-103">공유 리소스를 동시에 액세스하는 경우 병목 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-103">Simultaneous access to shared resources causes bottlenecks.</span></span> <span data-ttu-id="bffaf-104">일반적으로 병목 상태는 모든 소프트웨어 시스템에서 필연적으로 나타나지만</span><span class="sxs-lookup"><span data-stu-id="bffaf-104">In general, bottlenecks are present in every software system and are inevitable.</span></span> <span data-ttu-id="bffaf-105">공유 리소스에 대한 과도한 요구는 응답 시간을 현저히 늦추는 원인이므로 반드시 확인하고 적절하게 튜닝해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-105">However, excessive demands on shared resources cause poor response time and must be identified and tuned.</span></span>  
  
 <span data-ttu-id="bffaf-106">병목 상태의 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-106">Causes of bottlenecks include:</span></span>  
  
-   <span data-ttu-id="bffaf-107">리소스가 부족하여 구성 요소 추가나 업그레이드가 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="bffaf-107">Insufficient resources, requiring additional or upgraded components.</span></span>  
  
-   <span data-ttu-id="bffaf-108">같은 유형의 리소스에 작업이 골고루 분산되지 않은 경우 (예를 들어 하나의 디스크가 독점된 경우)</span><span class="sxs-lookup"><span data-stu-id="bffaf-108">Resources of the same type among which workloads are not distributed evenly; for example, one disk is being monopolized.</span></span>  
  
-   <span data-ttu-id="bffaf-109">리소스가 잘못 동작하는 경우</span><span class="sxs-lookup"><span data-stu-id="bffaf-109">Malfunctioning resources.</span></span>  
  
-   <span data-ttu-id="bffaf-110">리소스가 잘못 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="bffaf-110">Incorrectly configured resources.</span></span>  
  
## <a name="analyzing-bottlenecks"></a><span data-ttu-id="bffaf-111">병목 상태 분석</span><span class="sxs-lookup"><span data-stu-id="bffaf-111">Analyzing Bottlenecks</span></span>  
 <span data-ttu-id="bffaf-112">다양한 이벤트에서 과도하게 시간이 소요되면 튜닝할 수 있는 병목 상태가 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-112">Excessive durations for various events are indicators of bottlenecks that can be tuned.</span></span>  
  
 <span data-ttu-id="bffaf-113">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-113">For example:</span></span>  
  
-   <span data-ttu-id="bffaf-114">다른 구성 요소로 인해 이 구성 요소에 로드가 도달하지 못해 로드를 완료하기까지의 시간이 길어지는 경우</span><span class="sxs-lookup"><span data-stu-id="bffaf-114">Some other component may prevent the load from reaching this component thereby increasing the time to complete the load.</span></span>  
  
-   <span data-ttu-id="bffaf-115">네트워크 정체로 인해 클라이언트 요청에 소요되는 시간이 길어지는 경우</span><span class="sxs-lookup"><span data-stu-id="bffaf-115">Client requests may take longer due to network congestion.</span></span>  
  
 <span data-ttu-id="bffaf-116">다음은 서버 성능을 추적하고 병목 상태를 확인할 때 모니터링하는 5개의 중요 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-116">Following are five key areas to monitor when tracking server performance to identify bottlenecks.</span></span>  
  
|<span data-ttu-id="bffaf-117">병목 상태가 발생할 수 있는 영역</span><span class="sxs-lookup"><span data-stu-id="bffaf-117">Possible bottleneck area</span></span>|<span data-ttu-id="bffaf-118">서버에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="bffaf-118">Effects on the server</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="bffaf-119">메모리 사용량</span><span class="sxs-lookup"><span data-stu-id="bffaf-119">Memory usage</span></span>|<span data-ttu-id="bffaf-120">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 할당된 메모리나 사용할 수 있는 메모리가 부족하면 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-120">Insufficient memory allocated or available to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] degrades performance.</span></span> <span data-ttu-id="bffaf-121">이 경우 데이터를 데이터 캐시에서 직접 읽지 못하고 디스크에서 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-121">Data must be read from the disk rather than directly from the data cache.</span></span> <span data-ttu-id="bffaf-122">또한 Microsoft Windows 운영 체제에서 페이지가 필요할 때마다 디스크와 데이터를 스왑하면서 페이징을 과도하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-122">Microsoft Windows operating systems perform excessive paging by swapping data to and from the disk as the pages are needed.</span></span>|  
|<span data-ttu-id="bffaf-123">CPU 사용률</span><span class="sxs-lookup"><span data-stu-id="bffaf-123">CPU utilization</span></span>|<span data-ttu-id="bffaf-124">CPU 사용량이 장기간 높은 상태로 유지되면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 튜닝이나 CPU 업그레이드가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-124">A chronically high CPU utilization rate may indicate that [!INCLUDE[tsql](../../includes/tsql-md.md)] queries need to be tuned or that a CPU upgrade is needed.</span></span>|  
|<span data-ttu-id="bffaf-125">디스크 I/O(입/출력)</span><span class="sxs-lookup"><span data-stu-id="bffaf-125">Disk input/output (I/O)</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="bffaf-126">인덱스를 사용하는 등의 방법으로 쿼리를 튜닝하여 불필요한 I/O를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-126">queries can be tuned to reduce unnecessary I/O; for example, by employing indexes.</span></span>|  
|<span data-ttu-id="bffaf-127">사용자 연결</span><span class="sxs-lookup"><span data-stu-id="bffaf-127">User connections</span></span>|<span data-ttu-id="bffaf-128">너무 많은 사용자가 동시에 서버에 액세스하는 경우 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-128">Too many users may be accessing the server simultaneously causing performance degradation.</span></span>|  
|<span data-ttu-id="bffaf-129">차단 잠금</span><span class="sxs-lookup"><span data-stu-id="bffaf-129">Blocking locks</span></span>|<span data-ttu-id="bffaf-130">잘못 설계된 애플리케이션은 잠금을 일으키고 동시성을 제한하여 결과적으로 응답 시간을 길어지고 트랜잭션 처리율이 낮아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bffaf-130">Incorrectly designed applications can cause locks and hamper concurrency, thus causing longer response times and lower transaction throughput rates.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bffaf-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bffaf-131">See Also</span></span>  
 <span data-ttu-id="bffaf-132">[CPU 사용량 모니터링](../performance-monitor/monitor-cpu-usage.md) </span><span class="sxs-lookup"><span data-stu-id="bffaf-132">[Monitor CPU Usage](../performance-monitor/monitor-cpu-usage.md) </span></span>  
 <span data-ttu-id="bffaf-133">[디스크 사용량 모니터링](../performance-monitor/monitor-disk-usage.md) </span><span class="sxs-lookup"><span data-stu-id="bffaf-133">[Monitor Disk Usage](../performance-monitor/monitor-disk-usage.md) </span></span>  
 <span data-ttu-id="bffaf-134">[메모리 사용량 모니터링](../performance-monitor/monitor-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="bffaf-134">[Monitor Memory Usage](../performance-monitor/monitor-memory-usage.md) </span></span>  
 <span data-ttu-id="bffaf-135">[SQL Server, General Statistics 개체](../performance-monitor/sql-server-general-statistics-object.md) </span><span class="sxs-lookup"><span data-stu-id="bffaf-135">[SQL Server, General Statistics Object](../performance-monitor/sql-server-general-statistics-object.md) </span></span>  
 [<span data-ttu-id="bffaf-136">SQL Server, Locks 개체</span><span class="sxs-lookup"><span data-stu-id="bffaf-136">SQL Server, Locks Object</span></span>](../performance-monitor/sql-server-locks-object.md)  
  
  
