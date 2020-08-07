---
title: 이벤트 페어링 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- pairing target [SQL Server extended events]
- event pairing target
- targets [SQL Server extended events], pairing target
ms.assetid: 3c87dcfb-543a-4bd8-a73d-1390bdf4ffa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a1a6beb1c6996e6e12f16c4555fd9dfcab97617d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732943"
---
# <a name="event-pairing-target"></a><span data-ttu-id="3e584-102">이벤트 쌍 대상</span><span class="sxs-lookup"><span data-stu-id="3e584-102">Event Pairing Target</span></span>
  <span data-ttu-id="3e584-103">이벤트 쌍 대상은 각 이벤트에 있는 하나 이상의 데이터 열을 사용하여 두 이벤트를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-103">The event pairing target matches two events using one or more columns of data that are present in each event.</span></span> <span data-ttu-id="3e584-104">잠금 획득과 잠금 해제 등 많은 이벤트가 쌍을 이루게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-104">Many events come in pairs, for example, lock acquires and lock releases.</span></span> <span data-ttu-id="3e584-105">이벤트 시퀀스가 쌍을 이루면 두 이벤트는 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-105">After an event sequence is paired, both events are discarded.</span></span> <span data-ttu-id="3e584-106">일치하는 집합을 삭제하면 해제되지 않은 잠금 획득을 쉽게 찾아낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-106">Discarding matched sets allows for easy detection of lock acquisitions that have not been released.</span></span>  
  
 <span data-ttu-id="3e584-107">이벤트 수준 필터를 사용하여 이벤트 쌍 대상이 사전 설정된 기준에 일치하지 않는 이벤트만 캡처하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-107">By using event-level filters, the pairing target can be used to only capture events that do not match pre-set criteria.</span></span>  
  
 <span data-ttu-id="3e584-108">이벤트 쌍 대상을 사용하면 연결 작업을 수행할 열 시퀀스와 연결할 두 이벤트를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-108">When you use the event pairing target, you can choose two events that will be matched, together with a sequence of columns to perform the matching on.</span></span> <span data-ttu-id="3e584-109">이 시퀀스의 모든 열은 같은 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-109">All the columns in this sequence must be of the same type.</span></span>  
  
 <span data-ttu-id="3e584-110">다음 표에는 이벤트 쌍을 구성하는 데 사용할 수 있는 옵션이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-110">The following table describes the available options for configuring event pairing.</span></span>  
  
|<span data-ttu-id="3e584-111">옵션</span><span class="sxs-lookup"><span data-stu-id="3e584-111">Option</span></span>|<span data-ttu-id="3e584-112">허용되는 값</span><span class="sxs-lookup"><span data-stu-id="3e584-112">Allowed values</span></span>|<span data-ttu-id="3e584-113">Description</span><span class="sxs-lookup"><span data-stu-id="3e584-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="3e584-114">begin_event</span><span class="sxs-lookup"><span data-stu-id="3e584-114">begin_event</span></span>|<span data-ttu-id="3e584-115">현재 세션에 있는 이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-115">Any event name that is present in the current session.</span></span>|<span data-ttu-id="3e584-116">시퀀스 쌍의 시작 이벤트를 지정하는 이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-116">The event name specifying the beginning event in a paired sequence.</span></span>|  
|<span data-ttu-id="3e584-117">end_event</span><span class="sxs-lookup"><span data-stu-id="3e584-117">end_event</span></span>|<span data-ttu-id="3e584-118">현재 세션에 있는 이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-118">Any event name that is present in the current session.</span></span>|<span data-ttu-id="3e584-119">시퀀스 쌍의 종료 이벤트를 나타내는 이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-119">The event name specifying the ending event in a paired sequence.</span></span>|  
|<span data-ttu-id="3e584-120">begin_matching_columns</span><span class="sxs-lookup"><span data-stu-id="3e584-120">begin_matching_columns</span></span>|<span data-ttu-id="3e584-121">쉼표로 구분하여 순서대로 나열된 열 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-121">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="3e584-122">연결 작업을 수행할 열입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-122">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="3e584-123">end_matching_columns</span><span class="sxs-lookup"><span data-stu-id="3e584-123">end_matching_columns</span></span>|<span data-ttu-id="3e584-124">쉼표로 구분하여 순서대로 나열된 열 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-124">A comma-delimited, ordered list of column names.</span></span>|<span data-ttu-id="3e584-125">연결 작업을 수행할 열입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-125">The columns to perform matching on.</span></span>|  
|<span data-ttu-id="3e584-126">begin_matching_actions</span><span class="sxs-lookup"><span data-stu-id="3e584-126">begin_matching_actions</span></span>|<span data-ttu-id="3e584-127">쉼표로 구분하여 순서대로 나열한 동작 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-127">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="3e584-128">연결 작업을 수행할 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-128">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="3e584-129">end_matching_actions</span><span class="sxs-lookup"><span data-stu-id="3e584-129">end_matching_actions</span></span>|<span data-ttu-id="3e584-130">쉼표로 구분하여 순서대로 나열한 동작 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-130">A comma-delimited, ordered list of actions.</span></span>|<span data-ttu-id="3e584-131">연결 작업을 수행할 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-131">The actions to perform matching on.</span></span>|  
|<span data-ttu-id="3e584-132">respond_to_memory_pressure</span><span class="sxs-lookup"><span data-stu-id="3e584-132">respond_to_memory_pressure</span></span>|<span data-ttu-id="3e584-133">다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-133">One of the following values:</span></span><br /><br /> <span data-ttu-id="3e584-134">0 = 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-134">0 = Do not respond.</span></span><br /><br /> <span data-ttu-id="3e584-135">1 = 메모리가 부족하면 목록에 새 고아를 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-135">1 = Stop adding new orphans to the list when there is memory pressure.</span></span>|<span data-ttu-id="3e584-136">대상이 메모리 이벤트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-136">The target response to memory events.</span></span> <span data-ttu-id="3e584-137">1로 설정되어 있고 서버에 메모리가 부족하면 유지되고 있는 짝이 없는 정보가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-137">If set to 1 and the server is low on memory, unpaired information that is being maintained is removed.</span></span>|  
|<span data-ttu-id="3e584-138">max_orphans</span><span class="sxs-lookup"><span data-stu-id="3e584-138">max_orphans</span></span>||<span data-ttu-id="3e584-139">대상에 수집되는 쌍을 이루지 않는 이벤트의 총 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-139">Specifies the total number of unpaired events that will be collected in the target.</span></span> <span data-ttu-id="3e584-140">한도에 도달하면 쌍을 이루지 않는 이벤트가 FIFO(선입선출) 기준에 따라 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-140">Once the limit is reached, unpaired events are removed on a first-in, first-out (FIFO) basis.</span></span> <span data-ttu-id="3e584-141">기본값 = 10,000</span><span class="sxs-lookup"><span data-stu-id="3e584-141">Default = 10,000.</span></span>|  
  
 <span data-ttu-id="3e584-142">이벤트와 연결된 모든 데이터는 캡처된 후 나중에 쌍을 이루기 위해 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-142">All the data associated with an event is captured and stored for future pairing.</span></span> <span data-ttu-id="3e584-143">또한 동작에 의해 추가된 데이터도 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-143">In addition, data added by actions is also collected.</span></span> <span data-ttu-id="3e584-144">수집된 이벤트 데이터는 메모리에 저장되므로 일정한 제한이 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-144">The collected event data is stored in memory, and therefore has a finite limit.</span></span> <span data-ttu-id="3e584-145">이러한 제한은 시스템 용량 및 활동에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-145">This limit is based on system capacity and activity.</span></span> <span data-ttu-id="3e584-146">사용 가능한 시스템 리소스의 기준은 매개 변수로 사용 가능한 최대 메모리 양이 아니라 사용된 메모리 양이며</span><span class="sxs-lookup"><span data-stu-id="3e584-146">Instead of taking the maximum amount of memory to be used as a parameter, the amount of memory used will be based on available system resources.</span></span> <span data-ttu-id="3e584-147">시스템 리소스를 사용할 수 없는 경우 저장된 짝이 없는 이벤트가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-147">When these are not available, unpaired events that have been retained will be dropped.</span></span> <span data-ttu-id="3e584-148">이벤트가 짝이 없어 삭제된 경우 연결 이벤트는 짝이 없는 이벤트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-148">If an event has not been paired and is dropped, the matching event will appear as an unpaired event.</span></span>  
  
 <span data-ttu-id="3e584-149">이벤트 쌍 대상은 짝이 없는 이벤트를 XML 형식으로 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-149">The pairing target serializes unpaired events to an XML format.</span></span> <span data-ttu-id="3e584-150">이 형식은 어떤 스키마도 따르지 않으며</span><span class="sxs-lookup"><span data-stu-id="3e584-150">This format does not conform to any schema.</span></span> <span data-ttu-id="3e584-151">두 요소 유형만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-151">The format only contains two element types.</span></span> <span data-ttu-id="3e584-152">**\<unpaired>** 요소는 루트이 고 그 다음에 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-152">The **\<unpaired>** element is the root, followed by one.</span></span> <span data-ttu-id="3e584-153">**\<event>** 현재 추적 되 고 있는 짝이 없는 이벤트에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-153">**\<event>** element for each unpaired event that is currently being tracked.</span></span> <span data-ttu-id="3e584-154">요소에는 **\<event>** 짝이 없는 이벤트의 이름을 포함 하는 특성이 하나 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-154">The **\<event>** element contains one attribute that contains the name of the unpaired event.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="3e584-155">세션에 대상 추가</span><span class="sxs-lookup"><span data-stu-id="3e584-155">Adding the Target to a Session</span></span>  
 <span data-ttu-id="3e584-156">확장 이벤트 세션에 쌍 일치 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 다음 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-156">To add the pair matching target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.pair_matching   
```  
  
 <span data-ttu-id="3e584-157">이 문 다음에 시작 이벤트와 종료 이벤트 및 일치시킬 동작이나 열을 정의하는 SET 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-157">You would follow this with a SET statement, to define the beginning and ending events, and which actions or columns to match.</span></span> <span data-ttu-id="3e584-158">다음 예제에서는 sqlserver.lock_acquired 및 sqlserver.lock_released 이벤트의 쌍 일치를 위한 예제 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-158">The following example shows sample syntax for pair matching the sqlserver.lock_acquired and sqlserver.lock_released events.</span></span>  
  
```  
   ( SET begin_event = 'sqlserver.lock_acquired',  
      begin_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
      end_event = 'sqlserver.lock_released',  
      end_matching_columns = 'database_id, resource_0, resource_1, resource_2, transaction_id, mode',  
   respond_to_memory_pressure = 1)  
```  
  
 <span data-ttu-id="3e584-159">자세한 내용은 [잠금을 보유한 쿼리 파악](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e584-159">For more information, see [Determine Which Queries Are Holding Locks](../relational-databases/extended-events/determine-which-queries-are-holding-locks.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="3e584-160">대상 출력 검토</span><span class="sxs-lookup"><span data-stu-id="3e584-160">Reviewing the Target Output</span></span>  
 <span data-ttu-id="3e584-161">다음 쿼리를 사용하여 쌍 일치 대상의 출력을 검토할 수 있습니다. 쿼리에서 *session_name* 을 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-161">To review the output for the pair matching target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="3e584-162">다음 예에서는 쌍 대상의 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e584-162">The following example shows the pairing target output format.</span></span>  
  
```  
<unpaired truncated = "0" matchedCount = "[matched count]" memoryPressureDroppedCount = " [lost count]">  
    <event name  = "[event name]" package = "[package]" id= "[event ID value]" version = "[event version]">  
    <data name = "[column name]">   
    <type name = "[column type]" package = "[type package]" />   
    <value>[column value]</value>  
    <text value>[text value]</text>>  
        </data>  
    </event>  
</unpaired>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e584-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e584-163">See Also</span></span>  
 <span data-ttu-id="3e584-164">[SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="3e584-164">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="3e584-165">[sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e584-165">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="3e584-166">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e584-166">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="3e584-167">ALTER EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3e584-167">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
