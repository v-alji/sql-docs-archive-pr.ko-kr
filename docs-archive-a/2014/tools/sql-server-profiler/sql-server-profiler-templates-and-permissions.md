---
title: SQL Server Profiler 템플릿 및 권한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f3e3bc180db4e59def5af7eae39d8f177c93268
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647408"
---
# <a name="sql-server-profiler-templates-and-permissions"></a><span data-ttu-id="a6fe5-102">SQL Server Profiler 템플릿 및 권한</span><span class="sxs-lookup"><span data-stu-id="a6fe5-102">SQL Server Profiler Templates and Permissions</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a6fe5-103">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 내부적으로 쿼리를 해결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-103">shows how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resolves queries internally.</span></span> <span data-ttu-id="a6fe5-104">이를 통해 관리자는 어떤 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 다차원 식이 서버에 전송되고 해당 서버에서 어떻게 데이터베이스 또는 큐브에 액세스하여 결과 집합을 반환하는지를 정확히 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-104">This allows administrators to see exactly what [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or Multi-Dimensional Expressions are submitted to the server and how the server accesses the database or cube to return result sets.</span></span>  
  
 <span data-ttu-id="a6fe5-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can do the following:</span></span>  
  
-   <span data-ttu-id="a6fe5-106">재사용 가능한 템플릿을 기반으로 한 추적을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-106">Create a trace that is based on a reusable template</span></span>  
  
-   <span data-ttu-id="a6fe5-107">추적이 실행됨에 따라 추적 결과를 감시합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-107">Watch the trace results as the trace runs</span></span>  
  
-   <span data-ttu-id="a6fe5-108">추적 결과를 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-108">Store the trace results in a table</span></span>  
  
-   <span data-ttu-id="a6fe5-109">필요에 따라 추적 결과를 시작, 중지, 일시 중지 및 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-109">Start, stop, pause, and modify the trace results as necessary</span></span>  
  
-   <span data-ttu-id="a6fe5-110">추적 결과를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-110">Replay the trace results</span></span>  
  
 <span data-ttu-id="a6fe5-111">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 필요한 이벤트만 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-111">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor only the events in which you are interested.</span></span> <span data-ttu-id="a6fe5-112">추적 내용이 너무 크면 원하는 정보별로 필터링하여 이벤트 데이터의 하위 집합을 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-112">If traces are becoming too large, you can filter them based on the information you want, so that only a subset of the event data is collected.</span></span> <span data-ttu-id="a6fe5-113">너무 많은 이벤트를 모니터링하면 서버와 모니터링 프로세스에 오버헤드가 추가되어 특히 장기간 동안 모니터링할 때는 추적 파일이나 추적 테이블이 너무 커질 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-113">Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6fe5-114">1GB보다 큰 추적 열 값은 오류를 반환하며 추적 출력에서 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-114">Trace column values greater than 1 GB return an error and are truncated in the trace output.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6fe5-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a6fe5-115">In This Section</span></span>  
  
|<span data-ttu-id="a6fe5-116">항목</span><span class="sxs-lookup"><span data-stu-id="a6fe5-116">Topic</span></span>|<span data-ttu-id="a6fe5-117">Description</span><span class="sxs-lookup"><span data-stu-id="a6fe5-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a6fe5-118">SQL Server Profiler 템플릿</span><span class="sxs-lookup"><span data-stu-id="a6fe5-118">SQL Server Profiler Templates</span></span>](sql-server-profiler-templates.md)|<span data-ttu-id="a6fe5-119">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]와 함께 제공되는 미리 정의된 추적 템플릿에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-119">Contains information about the predefined trace templates that ship with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="a6fe5-120">SQL Server 프로파일러 실행에 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="a6fe5-120">Permissions Required to Run SQL Server Profiler</span></span>](permissions-required-to-run-sql-server-profiler.md)|<span data-ttu-id="a6fe5-121">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]실행에 필요한 사용 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-121">Contains information about the permissions that are required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="a6fe5-122">추적 및 추적 템플릿 저장</span><span class="sxs-lookup"><span data-stu-id="a6fe5-122">Save Traces and Trace Templates</span></span>](save-traces-and-trace-templates.md)|<span data-ttu-id="a6fe5-123">추적 출력을 저장하고 추적 정의를 템플릿에 저장하는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-123">Contains information about saving trace output and about saving trace definitions into a template.</span></span>|  
|[<span data-ttu-id="a6fe5-124">추적 템플릿 수정</span><span class="sxs-lookup"><span data-stu-id="a6fe5-124">Modify Trace Templates</span></span>](modify-trace-templates.md)|<span data-ttu-id="a6fe5-125">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 추적 템플릿을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-125">Contains information about modifying trace templates by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
|[<span data-ttu-id="a6fe5-126">추적 시작</span><span class="sxs-lookup"><span data-stu-id="a6fe5-126">Start a Trace</span></span>](start-a-trace.md)|<span data-ttu-id="a6fe5-127">추적을 시작, 일시 중지 또는 중지할 때 발생하는 사항에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-127">Contains information about what happens when you start, pause, or stop a trace.</span></span>|  
|[<span data-ttu-id="a6fe5-128">Windows 성능 로그 데이터와 추적의 상관 관계 지정</span><span class="sxs-lookup"><span data-stu-id="a6fe5-128">Correlate a Trace with Windows Performance Log Data</span></span>](correlate-a-trace-with-windows-performance-log-data.md)|<span data-ttu-id="a6fe5-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler를 사용하여 Windows 성능 로그 데이터와 추적의 상관 관계를 지정하는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-129">Contains information about correlating Windows performance log data with a trace by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span>|  
|[<span data-ttu-id="a6fe5-130">SQL Server Profiler를 사용하여 추적 보기 및 분석</span><span class="sxs-lookup"><span data-stu-id="a6fe5-130">View and Analyze Traces with SQL Server Profiler</span></span>](view-and-analyze-traces-with-sql-server-profiler.md)|<span data-ttu-id="a6fe5-131">추적을 사용하여 데이터의 문제를 해결하고 개체 이름을 추적에 표시하며 추적에서 이벤트를 찾는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-131">Contains information about using traces to troubleshoot data, displaying object names in a trace, and finding events in a trace.</span></span>|  
|[<span data-ttu-id="a6fe5-132">SQL Server Profiler를 사용하여 교착 상태 분석</span><span class="sxs-lookup"><span data-stu-id="a6fe5-132">Analyze Deadlocks with SQL Server Profiler</span></span>](analyze-deadlocks-with-sql-server-profiler.md)|<span data-ttu-id="a6fe5-133">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 교착 상태의 원인을 확인하는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-133">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span>|  
|[<span data-ttu-id="a6fe5-134">SQL Server Profiler에서 SHOWPLAN 결과로 쿼리 분석</span><span class="sxs-lookup"><span data-stu-id="a6fe5-134">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|<span data-ttu-id="a6fe5-135">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 실행 계획 및 실행 계획 통계 결과를 수집하여 표시하는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-135">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to collect and display Showplan and Showplan Statistics results.</span></span>|  
|[<span data-ttu-id="a6fe5-136">SQL Server Profiler로 추적 필터링</span><span class="sxs-lookup"><span data-stu-id="a6fe5-136">Filter Traces with SQL Server Profiler</span></span>](filter-traces-with-sql-server-profiler.md)|<span data-ttu-id="a6fe5-137">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 출력을 필터링하도록 데이터 열에 필터를 설정하는 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-137">Contains information about setting filters on data columns to filter trace output by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="a6fe5-138">추적 재생</span><span class="sxs-lookup"><span data-stu-id="a6fe5-138">Replay Traces</span></span>](replay-traces.md)|<span data-ttu-id="a6fe5-139">추적 재생의 의미와 추적 재생에 필요한 사항을 설명하는 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6fe5-139">Contains information that explains what replaying a trace means and what is required to replay a trace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6fe5-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6fe5-140">See Also</span></span>  
 <span data-ttu-id="a6fe5-141">[SQL Server 프로파일러](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="a6fe5-141">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="a6fe5-142">SQL Server Profiler 시작</span><span class="sxs-lookup"><span data-stu-id="a6fe5-142">Start SQL Server Profiler</span></span>](start-sql-server-profiler.md)  
  
  
