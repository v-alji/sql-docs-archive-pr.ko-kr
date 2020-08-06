---
title: 히스토그램 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bucketing target [SQL Server extended events]
- event bucketing target
- targets [SQL Server extended events], bucketing
ms.assetid: 2ea39141-7eb0-4c74-abf8-114c2c106a19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: acb124ef949849561a6bca0ba4016b40c1343384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732011"
---
# <a name="histogram-target"></a><span data-ttu-id="57300-102">히스토그램 대상</span><span class="sxs-lookup"><span data-stu-id="57300-102">Histogram Target</span></span>
  <span data-ttu-id="57300-103">히스토그램 대상은 이벤트 데이터를 기준으로 특정 이벤트 유형의 항목을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-103">The histogram target groups occurrences of a specific event type based on event data.</span></span> <span data-ttu-id="57300-104">이벤트 그룹화는 지정된 이벤트 열 또는 동작을 기준으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-104">The groupings of events are counted based on a specified event column or action.</span></span> <span data-ttu-id="57300-105">히스토그램 대상을 사용하여 성능 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-105">You can use the histogram target to troubleshoot performance issues.</span></span> <span data-ttu-id="57300-106">가장 자주 발생하는 이벤트가 무엇인지 확인하면 성능 문제의 원인이 될 수 있는 "핫스폿"을 찾아낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-106">By identifying which events are occurring most frequently, you can find "hotspots" that indicate a potential cause of a performance problem.</span></span>  
  
 <span data-ttu-id="57300-107">다음 표에서는 히스토그램 대상을 구성하는 데 사용할 수 있는 옵션을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-107">The following table describes the options that can be used to configure the histogram target.</span></span>  
  
|<span data-ttu-id="57300-108">옵션</span><span class="sxs-lookup"><span data-stu-id="57300-108">Option</span></span>|<span data-ttu-id="57300-109">허용되는 값</span><span class="sxs-lookup"><span data-stu-id="57300-109">Allowed values</span></span>|<span data-ttu-id="57300-110">Description</span><span class="sxs-lookup"><span data-stu-id="57300-110">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="57300-111">slots</span><span class="sxs-lookup"><span data-stu-id="57300-111">slots</span></span>|<span data-ttu-id="57300-112">임의의 정수 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-112">Any integer value.</span></span> <span data-ttu-id="57300-113">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-113">This value is optional.</span></span>|<span data-ttu-id="57300-114">유지할 최대 그룹화 수를 나타내는 사용자 지정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-114">A user-specified value indicating the maximum number of groupings to retain.</span></span> <span data-ttu-id="57300-115">이 값에 도달하면 기존 그룹에 속하지 않는 새 이벤트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-115">When this value is reached, new events that do not belong to the existing groups are ignored.</span></span><br /><br /> <span data-ttu-id="57300-116">성능 향상을 위해 슬롯 번호는 2의 다음 거듭제곱으로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-116">Note that to improve performance, the slot number is rounded up to the next power of 2.</span></span>|  
|<span data-ttu-id="57300-117">filtering_event_name</span><span class="sxs-lookup"><span data-stu-id="57300-117">filtering_event_name</span></span>|<span data-ttu-id="57300-118">확장 이벤트 세션에 있는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-118">Any event present in the Extended Events session.</span></span> <span data-ttu-id="57300-119">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-119">This value is optional.</span></span>|<span data-ttu-id="57300-120">이벤트의 클래스를 식별하는 데 사용되는 사용자 지정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-120">A user-specified value that is used to identify a class of events.</span></span> <span data-ttu-id="57300-121">지정된 이벤트의 인스턴스만 버킷팅되고</span><span class="sxs-lookup"><span data-stu-id="57300-121">Only instances of the specified event are bucketed.</span></span> <span data-ttu-id="57300-122">다른 이벤트는 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-122">All other events are ignored.</span></span><br /><br /> <span data-ttu-id="57300-123">이 값을 지정하는 경우 *package_name*.*event_name*형식을 사용해야 합니다(예: `'sqlserver.checkpoint_end'`).</span><span class="sxs-lookup"><span data-stu-id="57300-123">If you specify this value, you must use the format: *package_name*.*event_name*, for example `'sqlserver.checkpoint_end'`.</span></span> <span data-ttu-id="57300-124">다음 쿼리를 사용하여 패키지 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-124">You can identify the package name by using the following query:</span></span><br /><br /> <span data-ttu-id="57300-125">P.name, se event_name를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-125">SELECT p.name, se.event_name</span></span><br /><span data-ttu-id="57300-126">Sys. dm_xe_session_events se</span><span class="sxs-lookup"><span data-stu-id="57300-126">FROM sys.dm_xe_session_events se</span></span><br /><span data-ttu-id="57300-127">Dm_xe_packages p를 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-127">JOIN sys.dm_xe_packages p</span></span><br /><span data-ttu-id="57300-128">ON se_event_package_guid = p. guid</span><span class="sxs-lookup"><span data-stu-id="57300-128">ON se_event_package_guid = p.guid</span></span><br /><span data-ttu-id="57300-129">ORDER BY p.name, se. event_name</span><span class="sxs-lookup"><span data-stu-id="57300-129">ORDER BY p.name, se.event_name</span></span><br /><br /> <br /><br /> <span data-ttu-id="57300-130">filtering_event_name 값을 지정하지 않는 경우 source_type을 기본값인 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-130">If you do not specify the filtering_event_name value, source_type must be set to 1 (the default).</span></span>|  
|<span data-ttu-id="57300-131">source_type</span><span class="sxs-lookup"><span data-stu-id="57300-131">source_type</span></span>|<span data-ttu-id="57300-132">버킷의 기반이 되는 개체의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-132">The type of object that the bucket is based on.</span></span> <span data-ttu-id="57300-133">이 값은 선택 사항이고 지정되지 않은 경우 기본값이 1입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-133">This value is optional and if not specified has a default value of 1.</span></span>|<span data-ttu-id="57300-134">다음 값 중 하나가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-134">Can have one of the following values:</span></span><br /><br /> <span data-ttu-id="57300-135">0 = 이벤트</span><span class="sxs-lookup"><span data-stu-id="57300-135">0 for an event</span></span><br /><br /> <span data-ttu-id="57300-136">1 = 동작</span><span class="sxs-lookup"><span data-stu-id="57300-136">1 for an action</span></span>|  
|<span data-ttu-id="57300-137">source</span><span class="sxs-lookup"><span data-stu-id="57300-137">source</span></span>|<span data-ttu-id="57300-138">이벤트 열 또는 동작의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-138">Event column or action name.</span></span>|<span data-ttu-id="57300-139">데이터 원본으로 사용되는 이벤트 열 또는 동작 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="57300-139">The event column or action name that is used as the data source.</span></span><br /><br /> <span data-ttu-id="57300-140">원본에 대한 이벤트 열을 지정하는 경우 filtering_event_name 값에 사용되는 이벤트의 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-140">When you specify an event column for source, you must specify a column from the event that is used for the filtering_event_name value.</span></span> <span data-ttu-id="57300-141">다음 쿼리를 사용하여 후보 열을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-141">You can identify the potential columns by using the following query:</span></span><br /><br /> <span data-ttu-id="57300-142">Sys. dm_xe_object_columns에서 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-142">SELECT name FROM sys.dm_xe_object_columns</span></span><br /><span data-ttu-id="57300-143">WHERE object_name = ' \<eventname> '</span><span class="sxs-lookup"><span data-stu-id="57300-143">WHERE object_name = '\<eventname>'</span></span><br /><span data-ttu-id="57300-144">및 column_type! = ' readonly '</span><span class="sxs-lookup"><span data-stu-id="57300-144">AND column_type != 'readonly'</span></span><br /><br /> <span data-ttu-id="57300-145">원본에 대한 이벤트 열을 지정할 때는 원본 값에 패키지 이름을 포함할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-145">When you specify an event column for source, you do not have to include the package name in the source value.</span></span><br /><br /> <span data-ttu-id="57300-146">원본에 대한 동작 이름을 지정하는 경우 이 대상이 사용되고 있는 이벤트 세션의 컬렉션을 위해 구성된 동작 중 하나를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-146">When you specify an action name for source, you must use one of the actions that is configured for collection in the event session for which this target is being used.</span></span> <span data-ttu-id="57300-147">sys.dm_xe_sesssion_event_actions view의 action_name 열을 쿼리하면 동작 이름의 후보 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-147">To find potential values for the action name, you can query the action_name column of the sys.dm_xe_sesssion_event_actions view.</span></span><br /><br /> <span data-ttu-id="57300-148">동작 이름을 데이터 원본으로 사용하고 있는 경우 *package_name*.*action_name*형식을 사용하여 원본 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-148">If you are using an action name as the data source, you must specify the source value by using the format: *package_name*.*action_name*.</span></span>|  
  
 <span data-ttu-id="57300-149">다음 예에서는 히스토그램 대상이 데이터를 수집하는 방식을 높은 수준에서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="57300-149">The following example illustrates at a high level how the histogram target collects data.</span></span> <span data-ttu-id="57300-150">이 예에서 히스토그램 대상을 사용하여 각 대기 유형의 대기 횟수가 몇 번인지 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-150">In this example, you want to use the histogram target to count how many waits of each wait type occurred.</span></span> <span data-ttu-id="57300-151">이를 계산하려면 히스토그램 대상을 정의할 때 다음 옵션을 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-151">To do this, you would specify the following options when you define the histogram target:</span></span>  
  
-   <span data-ttu-id="57300-152">filtering_event_name = 'wait_info'</span><span class="sxs-lookup"><span data-stu-id="57300-152">filtering_event_name = 'wait_info'</span></span>  
  
-   <span data-ttu-id="57300-153">source = 'wait_type'</span><span class="sxs-lookup"><span data-stu-id="57300-153">source = 'wait_type'</span></span>  
  
-   <span data-ttu-id="57300-154">source_type = 0(wait_type이 이벤트 열이므로)</span><span class="sxs-lookup"><span data-stu-id="57300-154">source_type = 0 (because wait_type is an event column)</span></span>  
  
 <span data-ttu-id="57300-155">예제 시나리오에서는 wait_type 원본에 대해 다음 데이터가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-155">In the example scenario, the following data is recorded for the wait_type source.</span></span>  
  
|<span data-ttu-id="57300-156">필터링 이벤트 이름</span><span class="sxs-lookup"><span data-stu-id="57300-156">Filtering event name</span></span>|<span data-ttu-id="57300-157">원본 열 값</span><span class="sxs-lookup"><span data-stu-id="57300-157">Source column value</span></span>|  
|--------------------------|-------------------------|  
|<span data-ttu-id="57300-158">wait_info</span><span class="sxs-lookup"><span data-stu-id="57300-158">wait_info</span></span>|<span data-ttu-id="57300-159">file_io</span><span class="sxs-lookup"><span data-stu-id="57300-159">file_io</span></span>|  
|<span data-ttu-id="57300-160">wait_info</span><span class="sxs-lookup"><span data-stu-id="57300-160">wait_info</span></span>|<span data-ttu-id="57300-161">file_io</span><span class="sxs-lookup"><span data-stu-id="57300-161">file_io</span></span>|  
|<span data-ttu-id="57300-162">wait_info</span><span class="sxs-lookup"><span data-stu-id="57300-162">wait_info</span></span>|<span data-ttu-id="57300-163">network</span><span class="sxs-lookup"><span data-stu-id="57300-163">network</span></span>|  
|<span data-ttu-id="57300-164">wait_info</span><span class="sxs-lookup"><span data-stu-id="57300-164">wait_info</span></span>|<span data-ttu-id="57300-165">network</span><span class="sxs-lookup"><span data-stu-id="57300-165">network</span></span>|  
|<span data-ttu-id="57300-166">wait_info</span><span class="sxs-lookup"><span data-stu-id="57300-166">wait_info</span></span>|<span data-ttu-id="57300-167">sleep</span><span class="sxs-lookup"><span data-stu-id="57300-167">sleep</span></span>|  
  
 <span data-ttu-id="57300-168">대기 유형 값은 세 개의 슬롯으로 분류되고 각각의 값 및 슬롯 개수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-168">The wait type values would be categorized into three slots, with the following values and slot counts:</span></span>  
  
|<span data-ttu-id="57300-169">값</span><span class="sxs-lookup"><span data-stu-id="57300-169">Value</span></span>|<span data-ttu-id="57300-170">슬롯 개수</span><span class="sxs-lookup"><span data-stu-id="57300-170">Slot count</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="57300-171">file_io</span><span class="sxs-lookup"><span data-stu-id="57300-171">file_io</span></span>|<span data-ttu-id="57300-172">2</span><span class="sxs-lookup"><span data-stu-id="57300-172">2</span></span>|  
|<span data-ttu-id="57300-173">network</span><span class="sxs-lookup"><span data-stu-id="57300-173">network</span></span>|<span data-ttu-id="57300-174">2</span><span class="sxs-lookup"><span data-stu-id="57300-174">2</span></span>|  
|<span data-ttu-id="57300-175">sleep</span><span class="sxs-lookup"><span data-stu-id="57300-175">sleep</span></span>|<span data-ttu-id="57300-176">1</span><span class="sxs-lookup"><span data-stu-id="57300-176">1</span></span>|  
  
 <span data-ttu-id="57300-177">히스토그램 대상은 지정된 원본에 대한 이벤트 데이터만 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-177">The histogram target only retains event data for the specified source.</span></span> <span data-ttu-id="57300-178">이벤트 데이터가 너무 커서 모두 유지할 수 없는 경우에는 데이터가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="57300-178">In some cases the event data may be too large to retain completely, in which case the data is truncated.</span></span> <span data-ttu-id="57300-179">이벤트 데이터가 잘리면 바이트 수가 기록되고 XML 출력으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57300-179">When event data is truncated, the number of bytes is recorded and displayed as XML output.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="57300-180">세션에 대상 추가</span><span class="sxs-lookup"><span data-stu-id="57300-180">Adding the Target to a Session</span></span>  
 <span data-ttu-id="57300-181">확장 이벤트 세션에 히스토그램 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 추가할 대상 유형에 따라 다음 문 중 하나를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-181">To add the histogram target to an Extended Events session, you must include either of the following statements when you create or alter an event session, depending on the desired target type:</span></span>  
  
```  
ADD TARGET package0.histogram  
```  
  
 <span data-ttu-id="57300-182">SET 문을 사용하여 다양한 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-182">You can use the SET statement to set the various options.</span></span> <span data-ttu-id="57300-183">다음 예제에서는 sqlserver.checkpoint_end 이벤트의 데이터가 수집되는 히스토그램 대상을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="57300-183">The following example shows the addition of the histogram target, where data for the sqlserver.checkpoint_end event is collected.</span></span>  
  
```  
ADD TARGET package0.histogram  
(SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id')  
```  
  
 <span data-ttu-id="57300-184">자세한 내용은 [가장 많은 잠금이 발생한 개체 찾기](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)및 [확장 이벤트를 사용하여 시스템 작업 모니터링](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57300-184">For more information, see [Find the Objects That Have the Most Locks Taken on Them](../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md), and [Monitor System Activity Using Extended Events](../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).</span></span>  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="57300-185">대상 출력 검토</span><span class="sxs-lookup"><span data-stu-id="57300-185">Reviewing the Target Output</span></span>  
 <span data-ttu-id="57300-186">히스토그램 대상은 데이터를 XML 형식으로 직렬화하여 호출 프로그램 또는 프로시저에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="57300-186">The histogram target serializes data to a calling program or procedure in XML format.</span></span> <span data-ttu-id="57300-187">대상 출력은 어떤 스키마도 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57300-187">The target output does not conform to any schema.</span></span>  
  
 <span data-ttu-id="57300-188">다음 쿼리를 사용하여 히스토그램 대상의 출력을 검토할 수 있습니다. 쿼리에서 *session_name* 을 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="57300-188">To review the output from the histogram target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="57300-189">다음 예에서는 히스토그램 대상의 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="57300-189">The following example illustrates histogram target output format.</span></span>  
  
```  
<Slots truncated = "0" buckets=[count]>  
    <Slot count=[count] trunc=[truncated bytes]>  
        <value>  
        </value>  
    </Slot>  
</Slots>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57300-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57300-190">See Also</span></span>  
 <span data-ttu-id="57300-191">[SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="57300-191">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="57300-192">[sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57300-192">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="57300-193">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57300-193">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="57300-194">ALTER EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57300-194">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
