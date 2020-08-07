---
title: 이벤트 카운터 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f540f39176ec638cdc9236b315e306ecebfdcb1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732951"
---
# <a name="event-counter-target"></a><span data-ttu-id="ed9f3-102">이벤트 카운터 대상</span><span class="sxs-lookup"><span data-stu-id="ed9f3-102">Event Counter Target</span></span>
  <span data-ttu-id="ed9f3-103">이벤트 카운터 대상은 확장 이벤트 세션 동안 발생하는 모든 이벤트를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-103">The event counter target counts all events that occur during an Extended Events session.</span></span> <span data-ttu-id="ed9f3-104">이벤트 카운터 대상을 사용하면 전체 이벤트 컬렉션의 오버헤드를 추가하지 않고도 작업 특성에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-104">By using the event counter target, you can obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="ed9f3-105">이 대상에는 사용자 지정할 수 있는 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-105">This target has no customizable parameters.</span></span>  
  
## <a name="adding-the-target-to-a-session"></a><span data-ttu-id="ed9f3-106">세션에 대상 추가</span><span class="sxs-lookup"><span data-stu-id="ed9f3-106">Adding the Target to a Session</span></span>  
 <span data-ttu-id="ed9f3-107">확장 이벤트 세션에 이벤트 카운터 대상을 추가하려면 이벤트 세션을 만들거나 변경할 때 다음 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-107">To add the event counter target to an Extended Events session, you must include the following statement when you create or alter an event session:</span></span>  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a><span data-ttu-id="ed9f3-108">대상 출력 검토</span><span class="sxs-lookup"><span data-stu-id="ed9f3-108">Reviewing the Target Output</span></span>  
 <span data-ttu-id="ed9f3-109">다음 쿼리를 사용하여 이벤트 카운터 대상의 출력을 검토할 수 있습니다. 쿼리에서 *session_name* 을 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-109">To review the output from the event counter target, you can use the following query, replacing *session_name* with the name of the event session:</span></span>  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 <span data-ttu-id="ed9f3-110">다음 예에서는 이벤트 카운터 대상의 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed9f3-110">The following example shows the event counter target output format.</span></span>  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed9f3-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed9f3-111">See Also</span></span>  
 <span data-ttu-id="ed9f3-112">[SQL Server 확장 이벤트 대상](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="ed9f3-112">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="ed9f3-113">[sys.dm_xe_session_targets&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed9f3-113">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="ed9f3-114">[CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed9f3-114">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="ed9f3-115">ALTER EVENT SESSION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ed9f3-115">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
