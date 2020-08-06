---
title: 기존 SQL 추적 스크립트를 확장 이벤트 세션으로 변환 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, convert script to extended events
- extended events [SQL Server], convert SQL Trace script
ms.assetid: 4c8f29e6-0a37-490f-88b3-33493871b3f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e5b0d0e20fbf4fd55398c130abf6cfff128ebe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653399"
---
# <a name="convert-an-existing-sql-trace-script-to-an-extended-events-session"></a><span data-ttu-id="e681e-102">기존 SQL 추적 스크립트를 확장 이벤트 세션으로 변환</span><span class="sxs-lookup"><span data-stu-id="e681e-102">Convert an Existing SQL Trace Script to an Extended Events Session</span></span>
  <span data-ttu-id="e681e-103">확장 이벤트 세션으로 변환할 기존 SQL 추적 스크립트가 있는 경우 이 항목의 절차를 따라 해당하는 확장 이벤트 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-103">If you have an existing SQL Trace script that you want to convert to an Extended Events session, you can use the procedures in this topic to create an equivalent Extended Events session.</span></span> <span data-ttu-id="e681e-104">trace_xe_action_map 및 trace_xe_event_map 시스템 테이블의 정보를 사용하여 변환을 수행하는 데 필요한 정보를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-104">By using the information in the trace_xe_action_map and trace_xe_event_map system tables, you can collect the information that you must have to do the conversion.</span></span>  
  
 <span data-ttu-id="e681e-105">단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-105">The steps include the following:</span></span>  
  
1.  <span data-ttu-id="e681e-106">기존 스크립트를 실행하여 SQL 추적 세션을 만든 다음 추적 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-106">Execute the existing script to create a SQL Trace session, and then obtain the ID of the trace.</span></span>  
  
2.  <span data-ttu-id="e681e-107">fn_trace_geteventinfo 함수를 사용하는 쿼리를 실행하여 각 SQL 추적 이벤트 클래스와 관련 열에 해당하는 확장 이벤트의 이벤트 및 동작을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-107">Run a query that uses the fn_trace_geteventinfo function to find the equivalent Extended Events events and actions for each SQL Trace event class and its associated columns.</span></span>  
  
3.  <span data-ttu-id="e681e-108">fn_trace_getfilterinfo 함수를 사용하여 사용할 필터와 해당하는 확장 이벤트 동작을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-108">Use the fn_trace_getfilterinfo function to list the filters and the equivalent Extended Events actions to use.</span></span>  
  
4.  <span data-ttu-id="e681e-109">해당하는 확장 이벤트의 이벤트, 동작 및 조건자(필터)를 사용하여 확장 이벤트 세션을 수동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-109">Manually create an Extended Events session, using the equivalent Extended Events events, actions, and predicates (filters).</span></span>  
  
## <a name="to-obtain-the-trace-id"></a><span data-ttu-id="e681e-110">추적 ID를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="e681e-110">To obtain the trace ID</span></span>  
  
1.  <span data-ttu-id="e681e-111">쿼리 편집기에서 SQL 추적 스크립트를 연 다음 실행하여 추적 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-111">Open the SQL Trace script in Query Editor, and then execute the script to create the trace session.</span></span> <span data-ttu-id="e681e-112">이 절차를 완료하기 위해 추적 세션을 실행하고 있을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-112">Note that the trace session does not need to be running to complete this procedure.</span></span>  
  
2.  <span data-ttu-id="e681e-113">추적 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-113">Obtain the ID of the trace.</span></span> <span data-ttu-id="e681e-114">이렇게 하려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-114">To do this, use the following query:</span></span>  
  
    ```sql
    SELECT * FROM sys.traces;  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e681e-115">추적 ID 1은 일반적으로 기본 추적을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-115">Trace ID 1 typically indicates the default trace.</span></span>  
  
## <a name="to-determine-the-extended-events-equivalents"></a><span data-ttu-id="e681e-116">확장 이벤트의 해당 항목을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="e681e-116">To determine the Extended Events equivalents</span></span>  
  
1.  <span data-ttu-id="e681e-117">해당하는 확장 이벤트의 이벤트 및 동작을 확인하려면 다음 쿼리를 실행합니다. 여기서 *trace_id* 는 이전 절차에서 확인한 추적 ID 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-117">To determine the equivalent Extended Events events and actions, run the following query, where *trace_id* is set to the value of the trace ID that you obtained in the previous procedure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e681e-118">이 예에서는 기본 추적의 추적 ID(1)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-118">In this example, the trace ID for the default trace (1) is used.</span></span>  
  
    ```sql
    USE MASTER;  
    GO  
    DECLARE @trace_id int;  
    SET @trace_id = 1;  
    SELECT DISTINCT el.eventid, em.package_name, em.xe_event_name AS 'event'  
       , el.columnid, ec.xe_action_name AS 'action'  
    FROM (sys.fn_trace_geteventinfo(@trace_id) AS el  
       LEFT OUTER JOIN sys.trace_xe_event_map AS em  
          ON el.eventid = em.trace_event_id)  
    LEFT OUTER JOIN sys.trace_xe_action_map AS ec  
       ON el.columnid = ec.trace_column_id  
    WHERE em.xe_event_name IS NOT NULL AND ec.xe_action_name IS NOT NULL;  
    ```  
  
     <span data-ttu-id="e681e-119">해당하는 확장 이벤트의 이벤트 ID, 패키지 이름, 이벤트 이름, 열 ID 및 동작 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-119">The equivalent Extended Events event ID, package name, event name, column ID and action name are returned.</span></span> <span data-ttu-id="e681e-120">이 출력은 이 항목 뒷부분의 "확장 이벤트 세션을 만들려면" 절차에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-120">You will use this output in the procedure "To create the Extended Events session" later in this topic.</span></span>  
  
     <span data-ttu-id="e681e-121">필터링된 열이 확장 이벤트의 이벤트에 기본적으로 포함되는 이벤트 데이터 필드에 매핑되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-121">In some cases, the filtered column maps to an event data field that is included by default in the Extended Events event.</span></span> <span data-ttu-id="e681e-122">따라서 "Extended_Events_action_name" 열은 NULL이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-122">Therefore, the "Extended_Events_action_name" column will be NULL.</span></span> <span data-ttu-id="e681e-123">이 경우 다음을 수행하여 필터링된 열에 해당하는 데이터 필드를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-123">If this occurs, you must do the following to determine which data field is equivalent to the filtered column:</span></span>  
  
    1.  <span data-ttu-id="e681e-124">NULL을 반환하는 동작의 경우 스크립트에서 필터링되는 열을 포함하는 SQL 추적 이벤트 클래스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-124">For the actions that return NULL, identify which SQL Trace event classes in the script contain the column that is being filtered.</span></span>  
  
         <span data-ttu-id="e681e-125">예를 들어 SP:StmtCompleted 이벤트 클래스를 사용하고 Duration 추적 열 이름(SQL 추적 이벤트 클래스 ID 45 및 SQL 추적 열 ID 13)에 필터를 지정했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-125">For example, you may have used the SP:StmtCompleted event class, and specified a filter on the Duration trace column name (SQL Trace event class ID 45, and SQL Trace column ID 13).</span></span> <span data-ttu-id="e681e-126">이 경우 동작 이름이 쿼리 결과에 NULL로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-126">In this case, the action name will appear as NULL in the query results.</span></span>  
  
    2.  <span data-ttu-id="e681e-127">이전 단계에서 확인한 각 SQL 추적 이벤트 클래스에 대해 해당하는 확장 이벤트의 이벤트 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-127">For each SQL Trace event class that you identified in the previous step, find the equivalent Extended Events event name.</span></span> <span data-ttu-id="e681e-128">해당하는 이벤트 이름을 모르면 [SQL 추적 이벤트 클래스에 해당하는 확장 이벤트 항목 확인](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)항목에 나오는 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-128">(If you are not sure of the equivalent event name, use the query in the topic [View the Extended Events Equivalents to SQL Trace Event Classes](view-the-extended-events-equivalents-to-sql-trace-event-classes.md).)</span></span>  
  
    3.  <span data-ttu-id="e681e-129">다음 쿼리를 사용하여 이전 단계에서 확인한 이벤트에 사용할 올바른 데이터 필드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-129">Use the following query to identify the correct data fields to use for the events that you identified in the previous step.</span></span> <span data-ttu-id="e681e-130">이 쿼리는 확장 이벤트 데이터 필드를 "event_field" 열에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-130">The query shows the Extended Events data fields in the "event_field" column.</span></span> <span data-ttu-id="e681e-131">쿼리에서 *<event_name>* 을 이전 단계에서 지정한 이벤트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-131">In the query, replace *<event_name>* with the name of an event that you specified in the previous step.</span></span>  
  
        ```sql
        SELECT xp.name package_name, xe.name event_name  
           ,xc.name event_field, xc.description  
        FROM sys.trace_xe_event_map AS em  
        INNER JOIN sys.dm_xe_objects AS xe  
           ON em.xe_event_name = xe.name  
        INNER JOIN sys.dm_xe_packages AS xp  
           ON xe.package_guid = xp.guid AND em.package_name = xp.name  
        INNER JOIN sys.dm_xe_object_columns AS xc  
           ON xe.name = xc.object_name  
        WHERE xe.object_type = 'event' AND xc.column_type <> 'readonly'  
           AND em.xe_event_name = '<event_name>';  
        ```  
  
         <span data-ttu-id="e681e-132">예를 들어 SP:StmtCompleted 이벤트 클래스는 확장 이벤트의 sp_statement_completed 이벤트에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-132">For example, the SP:StmtCompleted event class maps to the sp_statement_completed Extended Events event.</span></span> <span data-ttu-id="e681e-133">쿼리에서 sp_statement_completed를 이벤트 이름으로 지정하면 "event_field" 열에는 기본적으로 이벤트와 함께 포함되는 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-133">If you specify sp_statement_completed as the event name in the query, the "event_field" column shows the fields that are included by default with the event.</span></span> <span data-ttu-id="e681e-134">이러한 필드를 보고 "duration" 필드가 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-134">Looking at the fields, you can see that there is a "duration" field.</span></span> <span data-ttu-id="e681e-135">해당하는 확장 이벤트 세션에 필터를 만들려면 "WHERE duration > 0"과 같은 조건자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-135">To create the filter in the equivalent Extended Events session, you would add a predicate such as "WHERE duration > 0".</span></span> <span data-ttu-id="e681e-136">예를 보려면 이 항목의 "확장 이벤트 세션을 만들려면" 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e681e-136">For an example, see the "To create the Extended Events session" procedure in this topic.</span></span>  
  
## <a name="to-create-the-extended-events-session"></a><span data-ttu-id="e681e-137">확장 이벤트 세션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e681e-137">To create the Extended Events session</span></span>  
 <span data-ttu-id="e681e-138">쿼리 편집기를 사용하여 확장 이벤트 세션을 만들고 출력을 파일 대상에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-138">Use Query Editor to create the Extended Events session, and to write the output to a file target.</span></span> <span data-ttu-id="e681e-139">다음 단계에서는 단일 쿼리를 설명하고 쿼리 작성 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-139">The following steps describe a single query, with explanations to show you how to build the query.</span></span> <span data-ttu-id="e681e-140">전체 쿼리 예를 보려면 이 항목의 "예" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e681e-140">For the full query example, see the "Example" section of this topic.</span></span>  
  
1.  <span data-ttu-id="e681e-141">다음과 같이 이벤트 세션을 만드는 문을 추가합니다.*session_name* 을 확장 이벤트 세션에 사용할 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-141">Add statements to create the event session, replacing s*ession_name* with the name that you want to use for the Extended Events session.</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [Session_Name] ON SERVER;  
    CREATE EVENT SESSION [Session_Name]  
    ON SERVER;  
    ```  
  
2.  <span data-ttu-id="e681e-142">"확장 이벤트의 해당 항목을 확인하려면" 절차에서 출력으로 반환된 확장 이벤트의 이벤트 및 동작을 추가하고 "스크립트에 사용된 필터를 확인하려면" 절차에서 확인한 조건자(필터)를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-142">Add the Extended Events events and actions that were returned as output in the procedure "Determine the Extended Events equivalents", and add the predicates (filters) that you identified in the procedure "To determine the filters that were used in the script".</span></span>  
  
     <span data-ttu-id="e681e-143">다음 예제에서는 SQL:StmtStarting 및 SP:StmtCompleted 이벤트 클래스와 세션 ID 및 기간에 대한 필터를 포함하는 SQL 추적 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-143">The following example uses a SQL Trace script that includes the SQL:StmtStarting and SP:StmtCompleted event classes, with filters for session ID and duration.</span></span> <span data-ttu-id="e681e-144">"확장 이벤트의 해당 항목을 확인하려면" 절차의 쿼리를 통해 반환되는 결과 집합의 예제 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-144">Sample output for the query in the "Determine the Extended Events equivalents" procedure returned the following result set:</span></span>  
  
    ```  
    Eventid  package_name  event                   columnid  action  
    44       sqlserver     sp_statement_starting   6         nt_username  
    44       sqlserver     sp_statement_starting   9         client_pid  
    44       sqlserver     sp_statement_starting   10        client_app_name  
    44       sqlserver     sp_statement_starting   11        server_principal_name  
    44       sqlserver     sp_statement_starting   12        session_id  
    45       sqlserver     sp_statement_completed  6         nt_username  
    45       sqlserver     sp_statement_completed  9         client_pid  
    45       sqlserver     sp_statement_completed  10        client_app_name  
    45       sqlserver     sp_statement_completed  11        server_principal_name  
    45       sqlserver     sp_statement_completed  12        session_id  
    ```  
  
     <span data-ttu-id="e681e-145">이 결과 집합을 확장 이벤트의 해당 항목으로 변환하기 위해 동작 목록과 함께 sqlserver.sp_statement_starting 및 sqlserver.sp_statement_completed 이벤트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-145">To convert this to the Extended Events equivalent, the sqlserver.sp_statement_starting and the sqlserver.sp_statement_completed events are added, with a list of actions.</span></span> <span data-ttu-id="e681e-146">조건자 문은 WHERE 절로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-146">Predicate statements are included as WHERE clauses.</span></span>  
  
    ```sql
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
          (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
          )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       )  
    ```  
  
3.  <span data-ttu-id="e681e-147">다음과 같이 비동기 파일 대상을 추가합니다. 파일 경로는 출력을 저장할 위치로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-147">Add the asynchronous file target, replacing the file paths with the location where you want to save the output.</span></span> <span data-ttu-id="e681e-148">파일 대상을 지정할 때는 로그 파일 및 메타데이터 파일 경로를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-148">When specifying the file target, you must include a log file and metadata file path file.</span></span>  
  
    ```sql
    ADD TARGET package0.asynchronous_file_target(  
       SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="to-view-the-results"></a><span data-ttu-id="e681e-149">결과를 보려면</span><span class="sxs-lookup"><span data-stu-id="e681e-149">To view the results</span></span>  
  
1.  <span data-ttu-id="e681e-150">sys.fn_xe_file_target_read_file 함수를 사용하여 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-150">You can use the sys.fn_xe_file_target_read_file function to view the output.</span></span> <span data-ttu-id="e681e-151">이렇게 하려면 다음 쿼리를 실행합니다. 파일 경로는 지정한 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-151">To do this, run the following query, replacing the file paths with the paths that you specified:</span></span>  
  
    ```sql
    SELECT *, CAST(event_data as XML) AS 'event_data_XML'  
    FROM sys.fn_xe_file_target_read_file('c:\temp\ExtendedEventsStoredProcs*.xel', 'c:\temp\ExtendedEventsStoredProcs*.xem', NULL, NULL);  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e681e-152">이벤트 데이터를 XML로 캐스팅하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e681e-152">Casting the event data as XML is optional.</span></span>  
  
     <span data-ttu-id="e681e-153">sys.fn_xe_file_target_read_file 함수에 대한 자세한 내용은 [sys.fn_xe_file_target_read_file&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e681e-153">For more information about the sys.fn_xe_file_target_read_file function, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
    ```sql
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
       DROP EVENT SESSION [session_name] ON SERVER;  
    CREATE EVENT SESSION [session_name]  
    ON SERVER  
  
    ADD EVENT sqlserver.sp_statement_starting  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59   
       ),  
  
    ADD EVENT sqlserver.sp_statement_completed  
       (ACTION  
       (  
          sqlserver.nt_username,  
          sqlserver.client_pid,  
          sqlserver.client_app_name,  
          sqlserver.server_principal_name,  
          sqlserver.session_id  
       )  
       WHERE sqlserver.session_id = 59 AND duration > 0  
       );  
  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
    ```  
  
## <a name="example"></a><span data-ttu-id="e681e-154">예제</span><span class="sxs-lookup"><span data-stu-id="e681e-154">Example</span></span>  
  
```sql
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='session_name')  
   DROP EVENT SESSION [session_name] ON SERVER;  
CREATE EVENT SESSION [session_name]  
ON SERVER  
  
ADD EVENT sqlserver.sp_statement_starting  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59   
   ),  
  
ADD EVENT sqlserver.sp_statement_completed  
   (ACTION  
   (  
      sqlserver.nt_username,  
      sqlserver.client_pid,  
      sqlserver.client_app_name,  
      sqlserver.server_principal_name,  
      sqlserver.session_id  
   )  
   WHERE sqlserver.session_id = 59 AND duration > 0  
   )  
  
ADD TARGET package0.asynchronous_file_target  
   (SET filename='c:\temp\ExtendedEventsStoredProcs.xel', metadatafile='c:\temp\ExtendedEventsStoredProcs.xem');  
```  
  
## <a name="see-also"></a><span data-ttu-id="e681e-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e681e-155">See Also</span></span>  
 [<span data-ttu-id="e681e-156">SQL 추적 이벤트 클래스에 해당하는 확장 이벤트 항목 확인</span><span class="sxs-lookup"><span data-stu-id="e681e-156">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>](view-the-extended-events-equivalents-to-sql-trace-event-classes.md)  
  
  
