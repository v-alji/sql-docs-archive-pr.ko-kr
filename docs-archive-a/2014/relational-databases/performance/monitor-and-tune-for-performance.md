---
title: 성능 모니터링 및 튜닝 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe07bdf01df6c4b61a64c6ee78de313a21d62f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649017"
---
# <a name="monitor-and-tune-for-performance"></a><span data-ttu-id="05274-102">성능 모니터링 및 튜닝</span><span class="sxs-lookup"><span data-stu-id="05274-102">Monitor and Tune for Performance</span></span>
  <span data-ttu-id="05274-103">데이터베이스 모니터링의 목표는 서버의 성능을 평가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="05274-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="05274-104">효과적인 모니터링을 위해서는 현재 성능에 대한 스냅샷을 정기적으로 만들어 문제를 일으키는 프로세스를 격리하고 데이터를 지속적으로 수집하여 성능 경향을 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span>  
  
 <span data-ttu-id="05274-105">지속적인 데이터베이스 성능 평가를 수행하면 응답 시간을 최소화하고 처리량을 최대화할 수 있으므로 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="05274-105">Ongoing evaluation of the database performance helps you minimize response times and maximize throughput, yielding optimal performance.</span></span> <span data-ttu-id="05274-106">효율적인 네트워크 소통량, 디스크 I/O 및 CPU 사용량을 통해 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-106">Efficient network traffic, disk I/O, and CPU usage are key to peak performance.</span></span> <span data-ttu-id="05274-107">애플리케이션 요구 사항을 완벽하게 분석하고, 데이터의 논리적 및 물리적 구조를 이해하고, 데이터베이스 사용량을 평가하고, OLTP(온라인 트랜잭션 처리) 및 의사 결정 지원과 같이 서로 상충되는 상황인 경우 타협점을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-107">You need to thoroughly analyze the application requirements, understand the logical and physical structure of the data, assess database usage, and negotiate tradeoffs between conflicting uses such as online transaction processing (OLTP) versus decision support.</span></span>  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a><span data-ttu-id="05274-108">데이터베이스 성능 모니터링 및 튜닝의 이점</span><span class="sxs-lookup"><span data-stu-id="05274-108">Benefits of Monitoring and Tuning Databases for Performance</span></span>  
 <span data-ttu-id="05274-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Microsoft Windows 운영 체제에서는 데이터베이스의 현재 상태를 확인하고 상태 변화에 따른 성능을 추적할 수 있는 유틸리티를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system provide utilities that allow you to view the current condition of the database and to track performance as conditions change.</span></span> <span data-ttu-id="05274-110">를 모니터링 하는 데 사용할 수 있는 다양 한 도구와 기술이 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="05274-110">There are a variety of tools and techniques that can be used to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05274-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 모니터링하는 방법을 알면 다음 작업을 수행하는 데 도움을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-111">Understanding how to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can help you:</span></span>  
  
-   <span data-ttu-id="05274-112">성능을 향상시킬 수 있는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-112">Determine whether you can improve performance.</span></span> <span data-ttu-id="05274-113">예를 들어 자주 사용하는 쿼리의 응답 시간을 모니터링하면 테이블에 있는 쿼리나 인덱스에 대한 변경이 필요한지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-113">For example, by monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables are required.</span></span>  
  
-   <span data-ttu-id="05274-114">사용자 작업을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-114">Evaluate user activity.</span></span> <span data-ttu-id="05274-115">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결을 시도하는 사용자를 모니터링하여 보안 설정이 적당한지 확인하고 애플리케이션이나 개발 시스템을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-115">For example, by monitoring users trying to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span> <span data-ttu-id="05274-116">예를 들어 SQL 쿼리의 실행을 모니터링하면 쿼리가 올바르게 작성되었는지, 결과를 제대로 생성하는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-116">For example, by monitoring SQL queries as they are executed, you can determine whether they are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="05274-117">문제를 해결하거나 저장 프로시저와 같은 애플리케이션 구성 요소를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-117">Troubleshoot any problems or debug application components, such as stored procedures.</span></span>  
  
### <a name="monitoring-in-a-dynamic-environment"></a><span data-ttu-id="05274-118">동적 환경의 모니터링</span><span class="sxs-lookup"><span data-stu-id="05274-118">Monitoring in a Dynamic Environment</span></span>  
 <span data-ttu-id="05274-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 동적 환경에서 서비스를 제공하기 때문에 모니터링이 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-119">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="05274-120">조건을 변경하면 성능이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="05274-120">Changing conditions result in changing performance.</span></span> <span data-ttu-id="05274-121">평가를 통해 사용자 수 증가, 사용자 액세스 및 연결 방법 변경, 데이터베이스 내용 증가, 클라이언트 애플리케이션 변경, 애플리케이션의 데이터 변경, 쿼리 복잡성 증가, 네트워크 소통량 증가 등에 따라 성능이 바뀌는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-121">In your evaluations, you can see performance changes as the number of users increases, user access and connection methods change, database contents grow, client applications change, data in the applications changes, queries become more complex, and network traffic rises.</span></span> <span data-ttu-id="05274-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도구를 사용하여 성능을 모니터링하면 변경된 조건 및 복잡한 쿼리에 일부 성능 변경 내용을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-122">By using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools to monitor performance, you can associate some changes in performance with changing conditions and complex queries.</span></span> <span data-ttu-id="05274-123">다음 시나리오는 이에 대한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05274-123">The following scenarios provide examples:</span></span>  
  
-   <span data-ttu-id="05274-124">자주 사용하는 쿼리의 응답 시간을 모니터링하면 쿼리를 실행할 테이블에 있는 쿼리나 인덱스 변경이 필요한지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-124">By monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables where the queries execute are required.</span></span>  
  
-   <span data-ttu-id="05274-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 실행할 때 모니터링하면 쿼리가 올바르게 작성되며 결과가 예상대로 나타나는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-125">By monitoring [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as they are executed, you can determine whether the queries are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="05274-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결을 시도하는 사용자를 모니터링하면 보안 설정이 적절한지 여부를 확인하고 애플리케이션이나 개발 시스템을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05274-126">By monitoring users that try to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span>  
  
 <span data-ttu-id="05274-127">응답 시간이란 쿼리가 처리됨을 시각적 확인 형식으로 사용자에게 반환하기 위해 설정된 결과의 첫 행에 필요한 시간의 길이를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-127">Response time is the length of time required for the first row of the result set to be returned to the user in the form of visual confirmation that a query is being processed.</span></span> <span data-ttu-id="05274-128">처리량이란 지정한 시간 동안 서버에서 처리한 총 쿼리 수를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-128">Throughput is the total number of queries handled by the server during a specified period of time.</span></span>  
  
 <span data-ttu-id="05274-129">사용자 수가 증가하면 서버 리소스에 대한 경쟁도 증가하여 응답 시간은 증가하고 전체 처리량은 감소됩니다.</span><span class="sxs-lookup"><span data-stu-id="05274-129">As the number of users increases, so does the competition for a server's resources, which in turn increases response time and decreases overall throughput.</span></span>  
  
## <a name="monitoring-and-tuning-performance-tasks"></a><span data-ttu-id="05274-130">성능 모니터링 및 튜닝 태스크</span><span class="sxs-lookup"><span data-stu-id="05274-130">Monitoring and Tuning Performance Tasks</span></span>  
  
|<span data-ttu-id="05274-131">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="05274-131">Task Description</span></span>|<span data-ttu-id="05274-132">항목</span><span class="sxs-lookup"><span data-stu-id="05274-132">Topic</span></span>|  
|----------------------|-----------|  
|[<span data-ttu-id="05274-133">SQL Server 구성 요소 모니터링</span><span class="sxs-lookup"><span data-stu-id="05274-133">Monitor SQL Server Components</span></span>](monitor-sql-server-components.md)|<span data-ttu-id="05274-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 구성 요소를 효과적으로 모니터링하는 데 필요한 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-134">Provides the necessary steps required to effectively monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="05274-135">성능 모니터링 및 튜닝 도구</span><span class="sxs-lookup"><span data-stu-id="05274-135">Performance Monitoring and Tuning Tools</span></span>](performance-monitoring-and-tuning-tools.md)|<span data-ttu-id="05274-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 모니터링 및 튜닝 도구를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-136">Lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring and tuning tools.</span></span>|  
|[<span data-ttu-id="05274-137">성능 기준선 설정</span><span class="sxs-lookup"><span data-stu-id="05274-137">Establish a Performance Baseline</span></span>](establish-a-performance-baseline.md)|<span data-ttu-id="05274-138">성능 기준선을 설정하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-138">Provides information about how to establish a performance baseline.</span></span>|  
|[<span data-ttu-id="05274-139">성능 문제 격리</span><span class="sxs-lookup"><span data-stu-id="05274-139">Isolate Performance Problems</span></span>](isolate-performance-problems.md)|<span data-ttu-id="05274-140">데이터베이스 성능 문제를 격리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-140">Describes how to isolate database performance problems.</span></span>|  
|[<span data-ttu-id="05274-141">병목 상태 식별</span><span class="sxs-lookup"><span data-stu-id="05274-141">Identify Bottlenecks</span></span>](identify-bottlenecks.md)|<span data-ttu-id="05274-142">서버 성능을 모니터링하고 추적하여 병목 상태를 식별하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-142">Describes how to monitor and track server performance to identify bottlenecks.</span></span>|  
|[<span data-ttu-id="05274-143">서버 성능 및 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="05274-143">Server Performance and Activity Monitoring</span></span>](server-performance-and-activity-monitoring.md)|<span data-ttu-id="05274-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 Windows 성능 및 활동 모니터링 도구를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-144">Describes how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span>|  
|[<span data-ttu-id="05274-145">실행 계획 표시 및 저장</span><span class="sxs-lookup"><span data-stu-id="05274-145">Display and Save Execution Plans</span></span>](display-and-save-execution-plans.md)|<span data-ttu-id="05274-146">실행 계획을 XML 형식으로 파일에 표시하고 저장하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-146">Describes how to display and save execution plans to a file in XML format.</span></span>|  
|[<span data-ttu-id="05274-147">쿼리 저장소를 사용하여 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="05274-147">Monitoring Performance By Using the Query Store</span></span>](monitoring-performance-by-using-the-query-store.md)|<span data-ttu-id="05274-148">쿼리 저장소는 쿼리, 계획 및 런타임 통계의 기록을 자동으로 캡처하고 사용자 검토를 위해 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="05274-148">The Query Store automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05274-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05274-149">See Also</span></span>  
 <span data-ttu-id="05274-150">[기업 내 관리 자동화](../../ssms/agent/automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="05274-150">[Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="05274-151">[데이터베이스 엔진 튜닝 관리자](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="05274-151">[Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="05274-152">[리소스 사용 모니터링&#40;시스템 모니터&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="05274-152">[Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="05274-153">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="05274-153">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
