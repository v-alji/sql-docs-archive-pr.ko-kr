---
title: 쿼리 편집기를 사용 하 여 확장 이벤트 세션 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- create extended events session
- extended events [SQL Server], create session
ms.assetid: cba0e02b-b201-4863-bf1b-9164e68e5fa8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 648370ecdd2938b6fb425955dc02da8960f884c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651256"
---
# <a name="create-an-extended-events-session-using-query-editor"></a><span data-ttu-id="ab4a5-102">쿼리 편집기를 사용하여 확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="ab4a5-102">Create an Extended Events Session Using Query Editor</span></span>
  <span data-ttu-id="ab4a5-103">쿼리 편집기를 사용하거나 개체 탐색기에서 확장 이벤트 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-103">You can create an Extended Events session by using the Query Editor, or you can create a session in Object Explorer.</span></span> <span data-ttu-id="ab4a5-104">개체 탐색기 확장 이벤트는 이벤트 세션 데이터를 생성, 수정 및 보는 데 사용할 수 있는 두 가지 사용자 인터페이스를 제공 합니다. 마법사는 이벤트 세션 만들기 프로세스를 안내 하는 마법사와 고급 구성 옵션을 제공 하는 새 세션 UI를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-104">In Object Explorer, Extended Events provides two user interfaces you can use to create, modify, and view event session data - a wizard that guides you through the event session creation process, and a New Session UI that provides more advanced configuration options.</span></span> <span data-ttu-id="ab4a5-105">확장 이벤트 세션을 만들어 SQL Server 추적을 진단하면 다음과 같은 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-105">You can create Extended Events sessions to diagnose SQL Server tracing, which enables you to resolve issues such as the following:</span></span>  
  
-   <span data-ttu-id="ab4a5-106">가장 비용이 많이 드는 쿼리 찾기</span><span class="sxs-lookup"><span data-stu-id="ab4a5-106">Find your most expensive queries</span></span>  
  
-   <span data-ttu-id="ab4a5-107">래치 경합의 근본 원인 찾기</span><span class="sxs-lookup"><span data-stu-id="ab4a5-107">Find root causes of latch contention</span></span>  
  
-   <span data-ttu-id="ab4a5-108">다른 쿼리를 차단하는 쿼리 찾기</span><span class="sxs-lookup"><span data-stu-id="ab4a5-108">Find a query that is blocking other queries</span></span>  
  
-   <span data-ttu-id="ab4a5-109">쿼리 재컴파일에 의해 발생하는 과도한 CPU 사용 문제 해결</span><span class="sxs-lookup"><span data-stu-id="ab4a5-109">Troubleshoot excessive CPU usage caused by query recompilation</span></span>  
  
-   <span data-ttu-id="ab4a5-110">교착 상태 해결</span><span class="sxs-lookup"><span data-stu-id="ab4a5-110">Troubleshoot deadlocks</span></span>  
  
 <span data-ttu-id="ab4a5-111">새 세션 마법사를 사용하여 확장 이벤트 세션을 만드는 방법은 [마법사를 사용하여 확장 이벤트 세션 만들기&#40;개체 탐색기&#41;](../ssms/object/object-explorer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-111">For information about how to create an Extended Events session using the New Session Wizard, see [Create an Extended Events Session Using the Wizard &#40;Object Explorer&#41;](../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="ab4a5-112">새 세션 UI를 사용하여 확장 이벤트 세션을 만드는 방법은 [새 세션 대화 상자를 사용하여 확장 이벤트 세션 만들기](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-112">For information about how to create an Extended Events session using the New Session UI, see [Create an Extended Events Session Using the New Session Dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md).</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab4a5-113">권한</span><span class="sxs-lookup"><span data-stu-id="ab4a5-113">Permissions</span></span>  
 <span data-ttu-id="ab4a5-114">확장 이벤트 세션을 만들려면 ALTER ANY EVENT SESSION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-114">To create an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="creating-an-extended-events-session-using-query-editor"></a><span data-ttu-id="ab4a5-115">쿼리 편집기를 사용하여 확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="ab4a5-115">Creating an Extended Events session using Query Editor</span></span>  
  
#### <a name="to-create-an-extended-events-session"></a><span data-ttu-id="ab4a5-116">확장 이벤트 세션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ab4a5-116">To create an Extended Events session</span></span>  
  
1.  <span data-ttu-id="ab4a5-117">다음 절차에서는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 편집기를 사용하여 확장 이벤트 세션을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-117">The following procedure shows how to create an Extended Events session by using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="ab4a5-118">세션에 사용할 이벤트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-118">Determine which events that you want to use in the session.</span></span> <span data-ttu-id="ab4a5-119">사용 가능한 모든 이벤트와 키워드 및 채널을 함께 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-119">To see all the events that are available, together with the keyword and channel, use the following query:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab4a5-120">키워드 및 채널에 대한 자세한 내용은 [SQL Server 확장 이벤트 패키지](../relational-databases/extended-events/sql-server-extended-events-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-120">For information about keywords and channels, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
    ```  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
       (  
       SELECT event_package = o.package_guid, o.description,   
       event=c.object_name, channel = v.map_value  
       FROM sys.dm_xe_objects o  
       LEFT JOIN sys.dm_xe_object_columns c ON o.name = c.object_name  
       INNER JOIN sys.dm_xe_map_values v ON c.type_name = v.name   
       AND c.column_value = cast(v.map_key AS nvarchar)  
       WHERE object_type = 'event' AND (c.name = 'CHANNEL' or c.name IS NULL)  
       ) c LEFT JOIN   
       (  
       SELECT event_package = c.object_package_guid, event = c.object_name,   
       keyword = v.map_value  
       FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
       ON c.type_name = v.name AND c.column_value = v.map_key   
       AND c.type_package_guid = v.object_package_guid  
       INNER JOIN sys.dm_xe_objects o ON o.name = c.object_name   
       AND o.package_guid = c.object_package_guid  
       WHERE object_type = 'event' AND c.name = 'KEYWORD'   
       ) k  
       ON  
       k.event_package = c.event_package AND (k.event=c.event or k.event IS NULL)  
       INNER JOIN sys.dm_xe_packages p ON p.guid = c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
2.  <span data-ttu-id="ab4a5-121">새 쿼리 창에서 다음 문을 추가하여 이벤트 세션을 만듭니다. *session_name* 은 사용할 세션 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-121">In a new query window, add the following statements to create an event session, replacing *session_name* with the session name that you want to use:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ab4a5-122">이 절차의 2~6단계에서는 이벤트 세션 정의의 각 섹션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-122">Steps 2 through 6 of this procedure describe each section of the event session definition.</span></span> <span data-ttu-id="ab4a5-123">모든 문은 단일 쿼리 창에 추가한 후에 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-123">You would add all the statements to a single query window before executing.</span></span> <span data-ttu-id="ab4a5-124">전체 예를 보려면 이 항목의 "예" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-124">For a full example, see the Example section of this topic.</span></span>  
  
    ```  
    CREATE EVENT SESSION session_name   
    ON SERVER  
    ```  
  
3.  <span data-ttu-id="ab4a5-125">모니터링할 이벤트를 *package_name*.*event_name*형식으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-125">Add the events that you want to monitor, in the format *package_name*.*event_name*.</span></span> <span data-ttu-id="ab4a5-126">각 이벤트에 대해 다음과 같은 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-126">For each event, add a line similar to the following:</span></span>  
  
    ```  
    ADD EVENT package_name.event_name  
    ```  
  
     <span data-ttu-id="ab4a5-127">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-127">For example:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed,  
    ADD EVENT sqlserver.file_write_completed  
    ```  
  
4.  <span data-ttu-id="ab4a5-128">(선택 사항) 이벤트를 추가한 후 필요한 동작을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-128">(Optional) After you add an event, you can add actions to take.</span></span> <span data-ttu-id="ab4a5-129">조건자를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-129">You can also add predicates.</span></span> <span data-ttu-id="ab4a5-130">조건자는 대상에서 이벤트 정보를 사용해야 하는 경우에 대한 조건을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-130">Predicates are used to establish criteria for when the event information should be consumed by the target.</span></span> <span data-ttu-id="ab4a5-131">동작은 ACTION 절을 사용하여 추가하고 조건자는 WHERE 절을 사용하여 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-131">Actions are added by using an ACTION clause, and predicates are added by using a WHERE clause.</span></span> <span data-ttu-id="ab4a5-132">예를 들어 파일 ID가 1인 경우 이벤트에 대해 [!INCLUDE[tsql](../includes/tsql-md.md)] 텍스트를 캡처하는 동작 및 조건자를 추가하려면 다음 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-132">For example, to add an action and predicate where the [!INCLUDE[tsql](../includes/tsql-md.md)] text is captured for the sqlserver.file_read_completed event, where the file ID equals 1, you would include the following statement:</span></span>  
  
    ```  
    ADD EVENT sqlserver.file_read_completed  
       (ACTION (sqlserver.sql_text)  
       WHERE file_id = 1),  
    ```  
  
    -   <span data-ttu-id="ab4a5-133">사용할 수 있는 동작을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-133">To view which actions are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS 'package_name', xo.name AS 'action_name', xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'action'  
        AND (xo.capabilities & 1 = 0   
        OR xo.capabilities IS NULL)  
        ORDER BY p.name, xo.name  
        ```  
  
    -   <span data-ttu-id="ab4a5-134">이벤트에 사용할 수 있는 조건자를 보려면 다음 쿼리를 사용합니다. *event_name* 은 조건자를 추가할 이벤트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-134">To view which predicates are available for an event, use the following query, replacing *event_name* with the name of the event for which you want to add a predicate:</span></span>  
  
        ```  
        SELECT *  
        FROM sys.dm_xe_object_columns  
        WHERE object_name = 'event_name'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="ab4a5-135">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-135">For example:</span></span>  
  
        ```  
        SELECT *   
        FROM sys.dm_xe_object_columns   
        WHERE object_name = 'file_read_completed'  
        AND column_type = 'data'  
        ```  
  
         <span data-ttu-id="ab4a5-136">전역 조건자 원본을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-136">Be aware that you can also add global predicate sources.</span></span> <span data-ttu-id="ab4a5-137">모든 조건자 식에 전역 조건자 원본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-137">A global predicate source can be used in any predicate expression.</span></span> <span data-ttu-id="ab4a5-138">사용할 수 있는 전역 조건자 원본을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-138">To view which global predicate sources are available, use the following query:</span></span>  
  
        ```  
        SELECT p.name AS package_name, xo.name AS predicate_name  
           , xo.description, xo.object_type  
        FROM sys.dm_xe_objects AS xo  
        JOIN sys.dm_xe_packages AS p  
           ON xo.package_guid = p.guid  
        WHERE xo.object_type = 'pred_source'  
        ORDER BY p.name, xo.name  
        ```  
  
         <span data-ttu-id="ab4a5-139">예를 들어 다음 조건자 식을 사용하여 이벤트가 발생하는 처음 다섯 번만 이벤트에 대한 데이터를 수집하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-139">For example, you could use the following predicate expression to specify that data should only be collected for an event the first five times that an event occurs.</span></span>  
  
        ```  
        WHERE package0.counter <= 5  
        ```  
  
5.  <span data-ttu-id="ab4a5-140">이벤트 데이터가 처리되고 사용될 원하는 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-140">Add the desired target, where the event data will be processed and consumed.</span></span> <span data-ttu-id="ab4a5-141">이때 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-141">Use the following format:</span></span>  
  
    ```  
    ADD TARGET package_name.target_name  
    ```  
  
     <span data-ttu-id="ab4a5-142">다음 예에서는 비동기 파일 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-142">The following example adds the asynchronous file target:</span></span>  
  
    ```  
    ADD TARGET package0.asynchronous_file_target  
       (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
    ```  
  
     <span data-ttu-id="ab4a5-143">사용 가능한 대상 목록을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-143">To view the list of available targets, use the following query:</span></span>  
  
    ```  
    SELECT p.name AS 'package_name', xo.name AS 'target_name'  
       , xo.description, xo.object_type   
    FROM sys.dm_xe_objects AS xo  
    JOIN sys.dm_xe_packages AS p  
       ON xo.package_guid = p.guid  
    WHERE xo.object_type = 'target'  
    AND (xo.capabilities & 1 = 0  
    OR xo.capabilities IS NULL)  
    ORDER BY p.name, xo.name  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab4a5-144">다양한 대상 유형에 대한 자세한 내용은 [SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-144">For information about the different target types, see [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).</span></span>  
  
6.  <span data-ttu-id="ab4a5-145">추가 구성 옵션을 검토하고 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-145">Review and add any additional configuration options.</span></span> <span data-ttu-id="ab4a5-146">예를 들어 이벤트 보존 모드, 이벤트가 메모리에 버퍼링되는 시간, 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 시작 시 이벤트 세션을 자동으로 시작할지 여부 등의 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-146">For example, you can configure options such as the event retention mode, how long events are buffered in memory, or whether the event session should start automatically when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="ab4a5-147">이 옵션은 [ALTER EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) 항목에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-147">The options are described in the topic [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql).</span></span> <span data-ttu-id="ab4a5-148">이러한 옵션을 지정하지 않은 경우 기본값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-148">Be aware that default values are assigned if these options are not specified.</span></span>  
  
7.  <span data-ttu-id="ab4a5-149">세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-149">Start the session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab4a5-150">세션 결과를 보는 방법은 온라인 설명서의 [SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) 노드에서 사용한 대상 유형에 해당하는 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-150">For more information about how to view the session results, see the corresponding topic for the target type that you used in the [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) node of Books Online.</span></span>  
  
 <span data-ttu-id="ab4a5-151">아래 예에서는 다음 정보를 캡처하는 IOActivity라는 확장 이벤트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-151">The following example creates an Extended Events session named IOActivity that captures the following information:</span></span>  
  
-   <span data-ttu-id="ab4a5-152">완료된 파일 읽기에 대한 이벤트 데이터(파일 ID가 1인 경우 파일 읽기를 위한 관련 [!INCLUDE[tsql](../includes/tsql-md.md)] 텍스트 포함)</span><span class="sxs-lookup"><span data-stu-id="ab4a5-152">Event data for completed file reads, including the associated [!INCLUDE[tsql](../includes/tsql-md.md)] text for file reads where the file ID is equal to 1.</span></span>  
  
-   <span data-ttu-id="ab4a5-153">완료된 파일 쓰기에 대한 이벤트 데이터</span><span class="sxs-lookup"><span data-stu-id="ab4a5-153">Event data for completed file writes.</span></span>  
  
-   <span data-ttu-id="ab4a5-154">로그 캐시의 데이터가 물리적 로그 파일에 기록될 때의 이벤트 데이터</span><span class="sxs-lookup"><span data-stu-id="ab4a5-154">Event data for when data is written from the log cache to the physical log file.</span></span>  
  
 <span data-ttu-id="ab4a5-155">이 세션에서는 출력을 파일 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ab4a5-155">The session sends the output to a file target.</span></span>  
  
```  
CREATE EVENT SESSION IOActivity  
ON SERVER  
  
ADD EVENT sqlserver.file_read_completed  
   (  
   ACTION (sqlserver.sql_text)  
   WHERE file_id = 1),  
ADD EVENT sqlserver.file_write_completed,  
ADD EVENT sqlserver.databases_log_flush  
  
ADD TARGET package0.asynchronous_file_target   
   (SET filename = 'c:\temp\xelog.xel', metadatafile = 'c:\temp\xelog.xem')  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab4a5-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab4a5-156">See Also</span></span>  
 <span data-ttu-id="ab4a5-157">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab4a5-157">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="ab4a5-158">[SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="ab4a5-158">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 [<span data-ttu-id="ab4a5-159">SQL Server 확장 이벤트 패키지</span><span class="sxs-lookup"><span data-stu-id="ab4a5-159">SQL Server Extended Events Packages</span></span>](../relational-databases/extended-events/sql-server-extended-events-packages.md)  
  
  
