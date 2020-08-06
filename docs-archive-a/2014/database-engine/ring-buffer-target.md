---
title: 링 버퍼 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 186e847bb9f9b621543119c25510dc5d6107e274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659622"
---
# <a name="ring-buffer-target"></a><span data-ttu-id="9ac09-102">링 버퍼 대상</span><span class="sxs-lookup"><span data-stu-id="9ac09-102">Ring Buffer Target</span></span>
  <span data-ttu-id="9ac09-103">간단히 말해 링 버퍼 대상은 메모리에 이벤트 데이터를 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-103">The ring buffer target briefly holds event data in memory.</span></span> <span data-ttu-id="9ac09-104">이 대상은 다음 두 모드 중 하나로 이벤트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-104">This target can manage events in one of two modes.</span></span>  
  
-   <span data-ttu-id="9ac09-105">첫째 모드는 엄격한 FIFO(선입선출) 모드로서 대상에 할당된 모든 메모리가 사용되면 가장 오래된 이벤트가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-105">The first mode is strict first-in first-out (FIFO), where the oldest event is discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="9ac09-106">기본 모드인 이 모드에서는 occurrence_number 옵션이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-106">In this mode (the default), the occurrence_number option is set to 0.</span></span>  
  
-   <span data-ttu-id="9ac09-107">둘째 모드는 이벤트별 FIFO 모드로서 각 유형별로 지정된 이벤트 수가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-107">The second mode is per-event FIFO, where a specified number of events of each type is kept.</span></span> <span data-ttu-id="9ac09-108">이 모드에서는 대상에 할당 된 모든 메모리를 사용 하는 경우 각 유형의 가장 오래 된 이벤트가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-108">In this mode, the oldest events of each type are discarded when all the memory allocated to the target is used.</span></span> <span data-ttu-id="9ac09-109">occurrence_number 옵션을 구성하여 각 유형별로 보존할 이벤트 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-109">You can configure the occurrence_number option to specify the number of events of each type to keep.</span></span>  
  
 <span data-ttu-id="9ac09-110">다음 표에서는 링 버퍼 대상을 구성하는 데 사용할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-110">The following table describes the available options for configuring the ring buffer target.</span></span>  
  
|<span data-ttu-id="9ac09-111">옵션</span><span class="sxs-lookup"><span data-stu-id="9ac09-111">Option</span></span>|<span data-ttu-id="9ac09-112">허용되는 값</span><span class="sxs-lookup"><span data-stu-id="9ac09-112">Allowed values</span></span>|<span data-ttu-id="9ac09-113">Description</span><span class="sxs-lookup"><span data-stu-id="9ac09-113">Description</span></span>|  
|------------|--------------------|-----------------|  
|<span data-ttu-id="9ac09-114">max_memory</span><span class="sxs-lookup"><span data-stu-id="9ac09-114">max_memory</span></span>|<span data-ttu-id="9ac09-115">모든 32 비트 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-115">Any 32-bit integer.</span></span> <span data-ttu-id="9ac09-116">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-116">This value is optional.</span></span>|<span data-ttu-id="9ac09-117">사용 가능한 최대 메모리 크기(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-117">The maximum amount of memory in kilobytes (KB) to use.</span></span> <span data-ttu-id="9ac09-118">기존 이벤트는 처음 도달한 제한인 max_event_limit 또는 max_memory에 따라 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-118">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="9ac09-119">최대값은 4194303 KB입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-119">The maximum value is 4194303 KB.</span></span> <span data-ttu-id="9ac09-120">에서 다른 메모리 소비자에 게 영향을 줄 수 있으므로 링 버퍼 크기를 GB 범위에 대 한 제한으로 설정 하기 전에 신중 하 게 고려해 야 합니다 SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ac09-120">A careful consideration should be made before setting the ring buffer size to limits in the GB range as it may impact other memory consumers in SQL Server</span></span>|  
|<span data-ttu-id="9ac09-121">max_event_limit</span><span class="sxs-lookup"><span data-stu-id="9ac09-121">max_event_limit</span></span>|<span data-ttu-id="9ac09-122">모든 32 비트 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-122">Any 32-bit integer.</span></span> <span data-ttu-id="9ac09-123">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-123">This value is optional.</span></span>|<span data-ttu-id="9ac09-124">ring_buffer에 보관되는 최대 이벤트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-124">The maximum number of events kept in the ring_buffer.</span></span> <span data-ttu-id="9ac09-125">기존 이벤트는 처음 도달한 제한인 max_event_limit 또는 max_memory에 따라 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-125">Existing events are dropped based on the limit that is first reached: max_event_limit or max_memory.</span></span> <span data-ttu-id="9ac09-126">기본값 = 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-126">Default = 1000.</span></span>|  
|<span data-ttu-id="9ac09-127">occurrence_number</span><span class="sxs-lookup"><span data-stu-id="9ac09-127">occurrence_number</span></span>|<span data-ttu-id="9ac09-128">다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-128">One of the following values:</span></span><br /><br /> <span data-ttu-id="9ac09-129">0(기본값) = 대상에 할당된 모든 메모리가 사용되면 가장 오래된 이벤트가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-129">0 (the default) = Oldest event is discarded when all the memory allocated to the target is used.</span></span><br /><br /> <span data-ttu-id="9ac09-130">모든 32 비트 정수 = 이벤트 FIFO 기준에 따라 삭제 되기 전에 유지할 각 유형의 이벤트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-130">Any 32-bit integer = The number of events of each type to keep before being discarded on a per-event FIFO basis.</span></span><br /><br /> <br /><br /> <span data-ttu-id="9ac09-131">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-131">This value is optional.</span></span>|<span data-ttu-id="9ac09-132">사용할 FIFO 모드 및 각 유형별로 버퍼에 기본적으로 보존할 이벤트의 수(0보다 큰 값을 설정한 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-132">The FIFO mode to use, and, if set to a value greater than 0, the preferred number of events of each type to keep in the buffer.</span></span>|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="9ac09-133">세션에 대상 추가</span><span class="sxs-lookup"><span data-stu-id="9ac09-133">Adding the Target to a Session</span></span>  
 <span data-ttu-id="9ac09-134">확장 이벤트 세션에 링 버퍼 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 다음 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-134">To add the ring buffer target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="9ac09-135">대상 출력 검토</span><span class="sxs-lookup"><span data-stu-id="9ac09-135">Reviewing the Target Output</span></span>  
 <span data-ttu-id="9ac09-136">링 버퍼 대상의 출력을 검토하려면 다음 쿼리를 사용합니다. 쿼리에서 *session_name* 을 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-136">To review the output from the ring buffer target, you can use the following query, replacing *session_name* with the name of the event session.</span></span>  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="9ac09-137">다음 예에서는 링 버퍼 대상의 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ac09-137">The following example shows the ring buffer target output format.</span></span>  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a><span data-ttu-id="9ac09-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ac09-138">See Also</span></span>

- [<span data-ttu-id="9ac09-139">SQL Server 확장 이벤트 대상</span><span class="sxs-lookup"><span data-stu-id="9ac09-139">SQL Server Extended Events Targets</span></span>](../../2014/database-engine/sql-server-extended-events-targets.md)
- [<span data-ttu-id="9ac09-140">sys.dm_xe_session_targets&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ac09-140">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="9ac09-141">CREATE EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ac09-141">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [<span data-ttu-id="9ac09-142">ALTER EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ac09-142">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

