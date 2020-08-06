---
title: 확장 이벤트를 사용하여 시스템 작업 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: rothja
ms.author: jroth
ms.openlocfilehash: d847d156d8244ede533e684c9e6b753d7d7b5047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646461"
---
# <a name="monitor-system-activity-using-extended-events"></a><span data-ttu-id="367c4-102">확장 이벤트를 사용하여 시스템 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="367c4-102">Monitor System Activity Using Extended Events</span></span>
  <span data-ttu-id="367c4-103">이 절차는 확장 이벤트를 ETW(Windows용 이벤트 추적)와 함께 사용하여 시스템 작업을 모니터링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-103">This procedure illustrates how Extended Events can be used with Event Tracing for Windows (ETW) to monitor system activity.</span></span> <span data-ttu-id="367c4-104">또한 CREATE EVENT SESSION, ALTER EVENT SESSION 및 DROP EVENT SESSION 문을 사용하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-104">The procedure also shows how the CREATE EVENT SESSION, ALTER EVENT SESSION, and DROP EVENT SESSION statements are used.</span></span>  
  
 <span data-ttu-id="367c4-105">이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-105">Accomplishing these tasks involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span> <span data-ttu-id="367c4-106">또한 명령 프롬프트를 사용하여 ETW 명령도 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-106">The procedure also requires using the command prompt to run ETW commands.</span></span>  
  
### <a name="to-monitor-system-activity-using-extended-events"></a><span data-ttu-id="367c4-107">확장 이벤트를 사용하여 시스템 작업을 모니터링하려면</span><span class="sxs-lookup"><span data-stu-id="367c4-107">To monitor system activity using Extended Events</span></span>  
  
1.  <span data-ttu-id="367c4-108">쿼리 편집기에서 다음 문을 실행하여 이벤트 세션을 만들고 두 개의 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-108">In Query Editor, issue the following statements to create an event session and add two events.</span></span> <span data-ttu-id="367c4-109">checkpoint_begin 및 checkpoint_end 이벤트는 데이터베이스 검사점이 시작될 때와 끝날 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-109">These events, checkpoint_begin and checkpoint_end, fire at the beginning and end of a database checkpoint.</span></span>  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  <span data-ttu-id="367c4-110">버킷이 32개인 버킷팅 대상을 추가하여 데이터베이스 ID를 기준으로 검사점 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-110">Add the bucketing target with 32 buckets to count the number of checkpoints based on the database ID.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  <span data-ttu-id="367c4-111">다음 문을 실행하여 ETW 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-111">Issue the following statements to add the ETW target.</span></span> <span data-ttu-id="367c4-112">그러면 검사점의 소요 시간을 확인하는 데 사용할 수 있는 시작 및 끝 이벤트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-112">This will enable you to see the begin and end events, which is used to determine how long the checkpoint takes.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  <span data-ttu-id="367c4-113">다음 문을 실행하여 세션 및 이벤트 수집을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-113">Issue the following statements to start the session and begin event collection.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  <span data-ttu-id="367c4-114">다음 문을 실행하여 세 이벤트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-114">Issue the following statements to cause three events to fire.</span></span>  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  <span data-ttu-id="367c4-115">다음 문을 실행하여 이벤트 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-115">Issue the following statements to view the event counts.</span></span>  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  <span data-ttu-id="367c4-116">명령 프롬프트에서 다음 명령을 실행하여 ETW 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-116">At the command prompt, issue the following commands to view the ETW data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="367c4-117">**tracerpt** 명령에 대한 도움말을 보려면 명령 프롬프트에서 `tracerpt /?`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="367c4-117">To get help for the **tracerpt** command, at the command prompt, enter `tracerpt /?`.</span></span>  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  <span data-ttu-id="367c4-118">다음 문을 실행하여 이벤트 세션을 중지하고 서버에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="367c4-118">Issue the following statements to stop the event session and remove it from the server.</span></span>  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="367c4-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="367c4-119">See Also</span></span>  
 <span data-ttu-id="367c4-120">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="367c4-120">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="367c4-121">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="367c4-121">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="367c4-122">[DROP EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="367c4-122">[DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="367c4-123">확장 이벤트 카탈로그 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="367c4-123">Extended Events Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 <span data-ttu-id="367c4-124">[확장 이벤트 동적 관리 뷰](../views/views.md) </span><span class="sxs-lookup"><span data-stu-id="367c4-124">[Extended Events Dynamic Management Views](../views/views.md) </span></span>  
 [<span data-ttu-id="367c4-125">SQL Server 확장 이벤트 대상</span><span class="sxs-lookup"><span data-stu-id="367c4-125">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
