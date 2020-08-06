---
title: 추적 만들기(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], example
- traces [SQL Server], creating
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 35644891b2dca8359d6dc68fbddb67288d241cb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652046"
---
# <a name="create-a-trace-transact-sql"></a><span data-ttu-id="d40e4-102">추적 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d40e4-102">Create a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="d40e4-103">이 항목에서는 저장 프로시저를 사용하여 추적을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-103">This topic describes how to use stored procedures to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="d40e4-104">추적 만들기</span><span class="sxs-lookup"><span data-stu-id="d40e4-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="d40e4-105">새 추적을 만드는 데 필요한 매개 변수를 사용하여 **sp_trace_create** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-105">Execute **sp_trace_create** with the required parameters to create a new trace.</span></span> <span data-ttu-id="d40e4-106">새 추적은 중지된 상태(*status* = **0**)입니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-106">The new trace will be in a stopped state (*status* is **0**).</span></span>  
  
2.  <span data-ttu-id="d40e4-107">추적할 이벤트 및 열을 선택하는 데 필요한 매개 변수를 실행하여 **sp_trace_setevent** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-107">Execute **sp_trace_setevent** with the required parameters to select the events and columns to trace.</span></span>  
  
3.  <span data-ttu-id="d40e4-108">또는 **sp_trace_setfilter** 를 실행하여 필터 또는 필터 조합을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-108">Optionally, execute **sp_trace_setfilter** to set any or a combination of filters.</span></span>  
  
     <span data-ttu-id="d40e4-109">**sp_trace_setevent** 및 **sp_trace_setfilter** 는 중지된 기존 추적에서만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-109">**sp_trace_setevent** and **sp_trace_setfilter** can be executed only on existing traces that are stopped.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d40e4-110">일반적인 저장 프로시저와 달리 모든 SQL Server Profiler 저장 프로시저의 매개 변수(<strong>sp_trace_*xx*</strong>)는 정확하게 입력해야 하며 데이터 형식 자동 변환을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-110">Unlike regular stored procedures, parameters of all SQL Server Profiler stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="d40e4-111">이러한 매개 변수를 인수 설명에 지정된 올바른 입력 매개 변수 데이터 형식으로 호출하지 않으면 저장 프로시저가 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-111">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d40e4-112">예제</span><span class="sxs-lookup"><span data-stu-id="d40e4-112">Example</span></span>  
 <span data-ttu-id="d40e4-113">다음 코드에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 추적을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-113">The following code demonstrates creating a trace using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d40e4-114">이 코드는 추적 만들기, 추적 파일 채우기 및 추적 중지의 세 가지 섹션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-114">It is in three sections: creating the trace, populating the trace file, and stopping the trace.</span></span> <span data-ttu-id="d40e4-115">추적하려는 이벤트를 추가하여 추적을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-115">Customize the trace by adding the events that you want to trace.</span></span> <span data-ttu-id="d40e4-116">이벤트 및 열 목록에 대한 자세한 내용은 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)을 사용하여 추적을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-116">For the list of events and columns, see [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).</span></span>  
  
 <span data-ttu-id="d40e4-117">다음 코드에서는 추적을 만들고 추적에 이벤트를 추가한 다음 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-117">The following code creates a trace, adds events to the trace, and then starts the trace:</span></span>  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="d40e4-118">예제</span><span class="sxs-lookup"><span data-stu-id="d40e4-118">Example</span></span>  
 <span data-ttu-id="d40e4-119">추적을 만들어 시작했으므로 이제 다음 코드를 실행하여 작업으로 추적을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-119">Now that the trace has been created and started, execute the following code to populate the trace with activity.</span></span>  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="d40e4-120">예제</span><span class="sxs-lookup"><span data-stu-id="d40e4-120">Example</span></span>  
 <span data-ttu-id="d40e4-121">추적은 언제든지 중지 및 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-121">The trace can be stopped and restarted at any time.</span></span> <span data-ttu-id="d40e4-122">이 예에서는 다음 코드를 실행하여 추적을 중지하고 추적을 닫고 추적 정의를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-122">In this example, execute the following code to stop the trace, close the trace, and delete the trace definition.</span></span>  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## <a name="example"></a><span data-ttu-id="d40e4-123">예제</span><span class="sxs-lookup"><span data-stu-id="d40e4-123">Example</span></span>  
 <span data-ttu-id="d40e4-124">추적 파일을 검사하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 SampleTrace.trc 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d40e4-124">To examine the trace file, open the SampleTrace.trc file using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40e4-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d40e4-125">See Also</span></span>  
 <span data-ttu-id="d40e4-126">[SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d40e4-126">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="d40e4-127">[sp_trace_create&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d40e4-127">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="d40e4-128">[sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d40e4-128">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="d40e4-129">sp_trace_setfilter&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d40e4-129">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)  
  
  
