---
title: SQL Server Profiler를 사용하여 추적 보기 및 분석 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e848fe9a07d838631eef1737c2a7679b67e649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648722"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a><span data-ttu-id="f4159-102">SQL Server Profiler를 사용하여 추적 보기 및 분석</span><span class="sxs-lookup"><span data-stu-id="f4159-102">View and Analyze Traces with SQL Server Profiler</span></span>
  <span data-ttu-id="f4159-103">추적에서 캡처한 이벤트를 보려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to view captured event data in a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f4159-104">는 정의된 추적 속성을 기반으로 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-104">displays data based on defined trace properties.</span></span> <span data-ttu-id="f4159-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터를 분석하는 한 가지 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 같은 다른 프로그램으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-105">One way to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is to copy the data to another program, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span> [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="f4159-106">튜닝 관리자는 **Text** 데이터 열이 추적에 포함되어 있는 경우 SQL 일괄 처리와 RPC(원격 프로시저 호출) 이벤트가 있는 추적 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-106">Tuning Advisor can use a trace file that contains SQL batch and remote procedure call (RPC) events if the **Text** data column is included in the trace.</span></span> <span data-ttu-id="f4159-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에 사용할 수 있도록 올바른 이벤트와 열이 캡처되었는지 확인하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-107">To make sure that the correct events and columns are captured for use with [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, use the predefined Tuning template that is supplied with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="f4159-108">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적을 열 때 추적 파일이 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 또는 SQL 추적 시스템 저장 프로시저로 생성된 경우 추적 파일에 .trc 파일 확장명이 없어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-108">When you open a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the trace file does not need to have the .trc file extension if the file was created by either [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or SQL Trace system stored procedures.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<span data-ttu-id="f4159-109">는 SQL 추적 .log 파일 및 일반 SQL 스크립트 파일도 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-109">can also read SQL Trace .log files and generic SQL script files.</span></span> <span data-ttu-id="f4159-110">trace.txt와 같이 .log 파일 확장명을 가지지 않은 SQL 추적 .log 파일을 열 때는 **SQLTrace_Log** 를 파일 형식으로 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="f4159-110">When opening a SQL Trace .log file that does not have a .log file extension, such as trace.txt, specify **SQLTrace_Log** as the file format.</span></span>  
  
 <span data-ttu-id="f4159-111">추적 분석에 유용한 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 날짜 및 시간 표시 형식을 구성하여 추적 분석을 도울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-111">You can configure the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] date and time display format to assist in trace analysis.</span></span>  
  
## <a name="troubleshooting-data"></a><span data-ttu-id="f4159-112">데이터 문제 해결</span><span class="sxs-lookup"><span data-stu-id="f4159-112">Troubleshooting Data</span></span>  
 <span data-ttu-id="f4159-113">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하면 **Duration**, **CPU**, **Reads**또는 **Writes** 데이터 열로 추적 또는 추적 파일을 그룹화하여 데이터의 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-113">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can troubleshoot data by grouping traces or trace files by the **Duration**, **CPU**, **Reads**, or **Writes** data columns.</span></span> <span data-ttu-id="f4159-114">예를 들어 잘 수행되지 않는 쿼리 또는 논리적 읽기 작업의 수가 비정상적으로 많은 쿼리 등의 데이터 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-114">Examples of data you might troubleshoot are queries that perform poorly or that have exceptionally high numbers of logical read operations.</span></span>  
  
 <span data-ttu-id="f4159-115">추적을 테이블에 저장하고 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 이벤트 데이터를 쿼리하면 추가 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-115">Additional information can be found by saving traces to tables and using [!INCLUDE[tsql](../../includes/tsql-md.md)] to query the event data.</span></span> <span data-ttu-id="f4159-116">예를 들어 어떤 **SQL:BatchCompleted** 이벤트의 대기 시간이 가장 긴지 확인하려면 다음을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-116">For example, to determine which **SQL:BatchCompleted** events had excessive wait time, execute the following:</span></span>  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f4159-117">서버는 이벤트 기간을 마이크로초(1초의 1/1000000, 즉 10<sup>-6</sup>) 단위로 보고하고 이벤트에 사용되는 CPU 시간량을 밀리초(1초의 1/1000, 즉 10<sup>-3</sup>) 단위로 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-117">The server reports the duration of an event in microseconds (one millionth, or 10<sup>-6</sup>, of a second) and the amount of CPU time used by the event in milliseconds (one thousandth, or 10<sup>-3</sup>, of a second).</span></span> <span data-ttu-id="f4159-118">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 그래픽 사용자 인터페이스는 기본적으로 **Duration** 열을 밀리초 단위로 표시하지만 추적을 파일이나 데이터베이스 테이블에 저장하면 **Duration** 열 값이 마이크로초 단위로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-118">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface displays the **Duration** column in milliseconds by default, but when a trace is saved to either a file or a database table, the **Duration** column value is written in microseconds.</span></span>  
  
## <a name="displaying-object-names-when-viewing-traces"></a><span data-ttu-id="f4159-119">추적을 볼 때 개체 이름 표시</span><span class="sxs-lookup"><span data-stu-id="f4159-119">Displaying Object Names When Viewing Traces</span></span>  
 <span data-ttu-id="f4159-120">개체 식별자(**개체 ID**)보다는 개체 이름을 표시하려면 **서버 이름** 및 **데이터베이스 ID** 데이터 열을 **개체 이름** 데이터 열과 함께 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-120">If you wish to display the name of an object rather than the object identifier (**Object ID**), you must capture the **Server Name** and **Database ID** data columns along with the **Object Name** data column.</span></span>  
  
 <span data-ttu-id="f4159-121">**개체 ID** 데이터 열로 그룹화하도록 선택한 경우 **서버 이름** 및 **데이터베이스 ID** 데이터 열로 먼저 그룹화하고 **개체 ID** 데이터 열로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-121">If you choose to group by the **Object ID** data column, make sure you group by the **Server Name** and **Database ID** data columns first, and then by the **Object ID** data column.</span></span> <span data-ttu-id="f4159-122">마찬가지로 **인덱스 ID** 데이터 열로 그룹화하도록 선택한 경우 **서버 이름**, **데이터베이스 ID**및 **개체 ID** 데이터 열로 그룹화한 다음 **인덱스 ID** 데이터 열로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-122">Similarly, if you choose to group by the **Index ID** data column, make sure you group by the **Server Name**, **Database ID**, and **Object ID** data columns first, and then by the **Index ID** data columns.</span></span> <span data-ttu-id="f4159-123">개체 및 인덱스 ID가 서버와 데이터베이스 간에 그리고 인덱스 ID에 대한 개체 간에 고유하지 않기 때문에 이러한 순서로 그룹화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-123">You must group in this order because object and index IDs are not unique among servers and databases (and among objects for index IDs).</span></span>  
  
## <a name="finding-specific-events-within-a-trace"></a><span data-ttu-id="f4159-124">추적에서 특정 이벤트 찾기</span><span class="sxs-lookup"><span data-stu-id="f4159-124">Finding Specific Events Within a Trace</span></span>  
 <span data-ttu-id="f4159-125">추적에서 이벤트를 찾아 그룹화하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-125">To find and group events in a trace, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f4159-126">추적을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-126">Create your trace.</span></span>  
  
    -   <span data-ttu-id="f4159-127">추적을 정의할 때 캡처하려고 하는 다른 데이터 열과 함께 **Event Class**, **ClientProcessID**및 **Start Time** 데이터 열을 캡처하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-127">When defining the trace, capture the **Event Class**, **ClientProcessID**, and **Start Time** data columns in addition to any other data columns you want to capture.</span></span> <span data-ttu-id="f4159-128">자세한 내용은 [추적 만들기&#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4159-128">For more information, see [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="f4159-129">캡처한 데이터를 **Event Class**데이터 열로 그룹화하고 추적을 파일이나 테이블에 캡처하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-129">Group the captured data by the **Event Class**data column, and capture the trace to a file or table.</span></span> <span data-ttu-id="f4159-130">캡처된 데이터를 그룹화하려면 추적 속성 대화 상자의 **이벤트 선택** 탭에서 **열 구성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-130">To group the captured data, click **Organize Columns** on the **Events Selection** tab of the Trace Properties dialog box.</span></span> <span data-ttu-id="f4159-131">자세한 내용은 [표시된 열 추적으로 구성&#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4159-131">For more information, see [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="f4159-132">추적을 시작한 다음 적절한 시간이 경과했거나 적절한 수의 이벤트가 캡처된 후에 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-132">Start the trace and stop it after the appropriate time has passed or number of events have been captured.</span></span>  
  
2.  <span data-ttu-id="f4159-133">대상 이벤트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-133">Find the target events.</span></span>  
  
    -   <span data-ttu-id="f4159-134">추적 파일이나 테이블을 열고 **Deadlock Chain**과 같은 원하는 이벤트 클래스의 노드를 확장하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-134">Open the trace file or table, and expand the node of the desired event class; for example, **Deadlock Chain**.</span></span> <span data-ttu-id="f4159-135">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-135">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="f4159-136">확인할 이벤트를 찾을 때까지 추적 데이터를 검색합니다. **에서** 편집 **메뉴의** 찾기 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 명령을 사용하면 추적에서 값을 찾는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-136">Search through the trace data until you find the events for which you are looking (use the **Find** command on the **Edit** menu of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to help you find values in the trace).</span></span> <span data-ttu-id="f4159-137">추적하는 이벤트의 **ClientProcessID** 및 **Start Time** 데이터 열 값을 메모하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-137">Note the values in the **ClientProcessID** and **Start Time** data columns of the events you trace.</span></span>  
  
3.  <span data-ttu-id="f4159-138">이벤트를 컨텍스트에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-138">Display the events in context.</span></span>  
  
    -   <span data-ttu-id="f4159-139">추적 속성을 표시하고 **ClientProcessID**ClientProcessID **Event Class** 데이터 열과 함께 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-139">Display the trace properties, and group by the **ClientProcessID**data column rather than by the **Event Class** data column.</span></span>  
  
    -   <span data-ttu-id="f4159-140">보려고 하는 각 연결 ID의 노드를 확장하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-140">Expand the nodes of each client process ID you want to view.</span></span> <span data-ttu-id="f4159-141">추적을 수동으로 검색하거나 **에서** 를 사용하여 이전에 메모한 대상 이벤트의 **Start Time**값을 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="f4159-141">Search through the trace manually, or use **Find** until you find the previously noted **Start Time**values of the target events.</span></span> <span data-ttu-id="f4159-142">이벤트는 선택한 각 클라이언트 프로세스 ID에 속하는 다른 이벤트와 함께 시간 순서대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-142">The events are displayed in chronological order with the other events that belong to each selected client process ID.</span></span> <span data-ttu-id="f4159-143">예를 들어 추적에 캡처된 **Deadlock** 및 **Deadlock Chain**이벤트는 확장 클라이언트 프로세스 ID 내의 **SQL:BatchStarting**events within the exp및ed client process ID.</span><span class="sxs-lookup"><span data-stu-id="f4159-143">For example, the **Deadlock** and **Deadlock Chain**events, captured within the trace, appear immediately after the **SQL:BatchStarting**events within the expanded client process ID.</span></span>  
  
 <span data-ttu-id="f4159-144">동일한 방법을 사용하여 그룹화된 이벤트를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-144">The same technique can be used to find any grouped events.</span></span> <span data-ttu-id="f4159-145">찾던 이벤트를 발견하면 **ClientProcessID**, **ApplicationName**또는 다른 이벤트 클래스로 해당 이벤트를 그룹화하여 시간 순서대로 관련 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f4159-145">Once you have found the events you seek, group them by **ClientProcessID**, **ApplicationName**, or another event class to view related activity in chronological order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4159-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4159-146">See Also</span></span>  
 <span data-ttu-id="f4159-147">[저장된 추적 보기&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f4159-147">[View a Saved Trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span></span>  
 <span data-ttu-id="f4159-148">[sys.fn_trace_getinfo&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f4159-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 <span data-ttu-id="f4159-149">[필터 정보 보기&#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f4159-149">[View Filter Information &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="f4159-150">[필터 정보 보기&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f4159-150">[View Filter Information &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span></span>  
 <span data-ttu-id="f4159-151">[추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f4159-151">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="f4159-152">추적 테이블 열기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="f4159-152">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](open-a-trace-table-sql-server-profiler.md)  
  
  
