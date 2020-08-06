---
title: SQL 추적 이벤트 클래스에 해당하는 확장 이벤트 항목 확인(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: rothja
ms.author: jroth
ms.openlocfilehash: 37459359f9f6cb7e3951b705c4007477ec43e36a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728243"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a><span data-ttu-id="b2d86-102">SQL 추적 이벤트 클래스에 해당하는 확장 이벤트 항목 확인</span><span class="sxs-lookup"><span data-stu-id="b2d86-102">View the Extended Events Equivalents to SQL Trace Event Classes</span></span>
  <span data-ttu-id="b2d86-103">확장 이벤트를 사용하여 SQL 추적 이벤트 클래스 및 열에 해당하는 이벤트 데이터를 수집하려는 경우 SQL 추적 이벤트가 확장 이벤트의 이벤트 및 동작에 매핑되는 방식을 이해하고 있으면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-103">If you want to use Extended Events to collect event data that is equivalent to SQL Trace event classes and columns, it is useful to understand how the SQL Trace events map to Extended Events events and actions.</span></span>  
  
 <span data-ttu-id="b2d86-104">다음 절차에 따라 각 SQL 추적 이벤트 및 관련 열에 해당하는 확장 이벤트의 이벤트 및 동작을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-104">You can use the following procedure to view the Extended Events events and actions that are equivalent to each SQL Trace event and its associated columns.</span></span>  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a><span data-ttu-id="b2d86-105">쿼리 편집기를 사용하여 SQL 추적 이벤트에 해당하는 확장 이벤트를 보려면</span><span class="sxs-lookup"><span data-stu-id="b2d86-105">To view the Extended Events equivalents to SQL Trace events using Query Editor</span></span>  
  
-   <span data-ttu-id="b2d86-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기에서 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-106">From Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], run the following query:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 <span data-ttu-id="b2d86-107">결과를 확인할 때는 다음에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b2d86-107">When you view the results, note the following:</span></span>  
  
-   <span data-ttu-id="b2d86-108">이벤트 클래스 열을 제외한 모든 열에서 NULL이 반환되었으면 이벤트 클래스가 SQL 추적에서 마이그레이션되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-108">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="b2d86-109">확장 이벤트 동작 열의 값만 NULL이면 다음 경우 중 하나에 해당함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-109">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="b2d86-110">SQL 추적 열이 확장 이벤트의 이벤트와 관련된 데이터 필드 중 하나에 매핑되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-110">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b2d86-111">확장 이벤트의 각 이벤트에는 결과 집합에 자동으로 포함되는 기본 데이터 필드 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-111">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="b2d86-112">동작 열에 의미 있는 확장 이벤트 해당 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-112">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="b2d86-113">예를 들어 SQL 추적의 EventClass 열이 이러한 경우에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-113">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="b2d86-114">이벤트 이름이 동일한 용도로 사용되므로 이 열은 확장 이벤트에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-114">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="b2d86-115">사용자가 구성할 수 있는 SQL 추적 이벤트 클래스(UserConfigurable:1 ~ UserConfigurable:9)의 경우 확장 이벤트에서는 단일 이벤트를 사용하여 이러한 이벤트 클래스를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-115">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="b2d86-116">이 이벤트의 이름은 user_event입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-116">The event is named user_event.</span></span> <span data-ttu-id="b2d86-117">이 이벤트는 SQL 추적에서 사용되는 것과 동일한 sp_trace_generateevent 저장 프로시저를 사용하여 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-117">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="b2d86-118">user_event 이벤트는 저장 프로시저에 전달된 이벤트 ID에 관계없이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-118">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="b2d86-119">그러나 event_id 필드는 이벤트 데이터의 일부로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-119">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="b2d86-120">이 필드를 사용하여 이벤트 ID를 기반으로 하는 조건자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-120">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="b2d86-121">예를 들어 코드에 UserConfigurable:0(event ID = 82)을 사용하는 경우 세션에 user_event 이벤트를 추가하고 'event_id = 82'라는 조건자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-121">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="b2d86-122">그에 따라 sp_trace_generateevent 저장 프로시저에서 확장 이벤트의 user_event 이벤트와 해당하는 SQL 추적 이벤트 클래스를 생성하므로 코드를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-122">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
-   <span data-ttu-id="b2d86-123">이벤트 클래스 열을 제외한 모든 열에서 NULL이 반환되었으면 이벤트 클래스가 SQL 추적에서 마이그레이션되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-123">If all columns return NULL except for the Event Class column, this indicates that the event class was not migrated from SQL Trace.</span></span>  
  
-   <span data-ttu-id="b2d86-124">확장 이벤트 동작 열의 값만 NULL이면 다음 경우 중 하나에 해당함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-124">If only the value in the Extended Events action column is NULL, this indicates that either of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="b2d86-125">SQL 추적 열이 확장 이벤트의 이벤트와 관련된 데이터 필드 중 하나에 매핑되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-125">The SQL Trace column maps to one of the data fields that is associated with the Extended Events event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b2d86-126">확장 이벤트의 각 이벤트에는 결과 집합에 자동으로 포함되는 기본 데이터 필드 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-126">Each Extended Events event has a default set of data fields that are automatically included in the result set.</span></span>  
  
    -   <span data-ttu-id="b2d86-127">동작 열에 의미 있는 확장 이벤트 해당 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-127">The action column does not have a meaningful Extended Events equivalent.</span></span> <span data-ttu-id="b2d86-128">예를 들어 SQL 추적의 EventClass 열이 이러한 경우에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-128">An example of this is the EventClass column in SQL Trace.</span></span> <span data-ttu-id="b2d86-129">이벤트 이름이 동일한 용도로 사용되므로 이 열은 확장 이벤트에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-129">This column is not needed in Extended Events because the event name serves the same purpose.</span></span>  
  
-   <span data-ttu-id="b2d86-130">사용자가 구성할 수 있는 SQL 추적 이벤트 클래스(UserConfigurable:1 ~ UserConfigurable:9)의 경우 확장 이벤트에서는 단일 이벤트를 사용하여 이러한 이벤트 클래스를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-130">For user configurable SQL Trace event classes (UserConfigurable:1 through UserConfigurable:9), Extended Events uses a single event to replace these.</span></span> <span data-ttu-id="b2d86-131">이 이벤트의 이름은 user_event입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-131">The event is named user_event.</span></span> <span data-ttu-id="b2d86-132">이 이벤트는 SQL 추적에서 사용되는 것과 동일한 sp_trace_generateevent 저장 프로시저를 사용하여 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-132">This event is raised by using sp_trace_generateevent, which is the same stored procedure that is used by SQL Trace.</span></span> <span data-ttu-id="b2d86-133">user_event 이벤트는 저장 프로시저에 전달된 이벤트 ID에 관계없이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-133">The user_event event is returned regardless of which event ID is passed to the stored procedure.</span></span> <span data-ttu-id="b2d86-134">그러나 event_id 필드는 이벤트 데이터의 일부로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-134">However, an event_id field is returned as part of the event data.</span></span> <span data-ttu-id="b2d86-135">이 필드를 사용하여 이벤트 ID를 기반으로 하는 조건자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-135">This enables you to build a predicate that is based on the event ID.</span></span> <span data-ttu-id="b2d86-136">예를 들어 코드에 UserConfigurable:0(event ID = 82)을 사용하는 경우 세션에 user_event 이벤트를 추가하고 'event_id = 82'라는 조건자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-136">For example, if you use UserConfigurable:0 (event ID = 82) in the code, you can add the user_event event to the session, and specify a predicate of 'event_id = 82'.</span></span> <span data-ttu-id="b2d86-137">그에 따라 sp_trace_generateevent 저장 프로시저에서 확장 이벤트의 user_event 이벤트와 해당하는 SQL 추적 이벤트 클래스를 생성하므로 코드를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d86-137">Therefore, you do not have to change the code because the sp_trace_generateevent stored procedure generates the Extended Events user_event event, and the equivalent SQL Trace event class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d86-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2d86-138">See Also</span></span>  
 [<span data-ttu-id="b2d86-139">sp_trace_generateevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b2d86-139">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)  
  
  
