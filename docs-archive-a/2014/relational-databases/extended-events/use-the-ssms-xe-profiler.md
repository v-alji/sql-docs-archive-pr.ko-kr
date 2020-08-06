---
title: system_health 세션 사용 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
ms.openlocfilehash: 86c3221fb4c0ea0690b369888ac8f2f9f82d6ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646449"
---
# <a name="use-the-system_health-session"></a><span data-ttu-id="a1068-102">system_health 세션 사용</span><span class="sxs-lookup"><span data-stu-id="a1068-102">Use the system_health Session</span></span>
  <span data-ttu-id="a1068-103">system_health 세션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 기본적으로 포함된 확장 이벤트 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-103">The system_health session is an Extended Events session that is included by default with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a1068-104">이 세션은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 시작될 때 자동으로 시작되며 성능에 별다른 영향을 주지 않고 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-104">This session starts automatically when the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, and runs without any noticeable performance effects.</span></span> <span data-ttu-id="a1068-105">이 세션은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 성능 문제를 해결하는 데 사용할 수 있는 시스템 데이터를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-105">The session collects system data that you can use to help troubleshoot performance issues in the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="a1068-106">따라서 이 세션은 중지하거나 삭제하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-106">Therefore, we recommend that you do not stop or delete the session.</span></span>  
  
 <span data-ttu-id="a1068-107">이 세션에서 수집하는 정보는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-107">The session collects information that includes the following:</span></span>  
  
-   <span data-ttu-id="a1068-108">심각도가 20보다 높거나 같은 오류가 발생한 모든 세션의 sql_text 및 session_id</span><span class="sxs-lookup"><span data-stu-id="a1068-108">The sql_text and session_id for any sessions that encounter an error that has a severity >=20.</span></span>  
  
-   <span data-ttu-id="a1068-109">메모리 관련 오류가 발생한 모든 세션의 sql_text 및 session_id.</span><span class="sxs-lookup"><span data-stu-id="a1068-109">The sql_text and session_id for any sessions that encounter a memory-related error.</span></span> <span data-ttu-id="a1068-110">이러한 오류에는 17803, 701, 802, 8645, 8651, 8657 및 8902가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-110">The errors include 17803, 701, 802, 8645, 8651, 8657 and 8902.</span></span>  
  
-   <span data-ttu-id="a1068-111">잠긴 스케줄러 문제에 대한 기록.</span><span class="sxs-lookup"><span data-stu-id="a1068-111">A record of any non-yielding scheduler problems.</span></span> <span data-ttu-id="a1068-112">이러한 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에서 오류 17883으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-112">(These appear in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log as error 17883.)</span></span>  
  
-   <span data-ttu-id="a1068-113">발견된 교착 상태</span><span class="sxs-lookup"><span data-stu-id="a1068-113">Any deadlocks that are detected.</span></span>  
  
-   <span data-ttu-id="a1068-114">래치(또는 사용하려는 다른 리소스)로 인해 15초 이상 대기한 모든 세션의 callstack, sql_text 및 session_id</span><span class="sxs-lookup"><span data-stu-id="a1068-114">The callstack, sql_text, and session_id for any sessions that have waited on latches (or other interesting resources) for > 15 seconds.</span></span>  
  
-   <span data-ttu-id="a1068-115">잠금으로 인해 30초 이상 대기한 모든 세션의 callstack, sql_text 및 session_id</span><span class="sxs-lookup"><span data-stu-id="a1068-115">The callstack, sql_text, and session_id for any sessions that have waited on locks for > 30 seconds.</span></span>  
  
-   <span data-ttu-id="a1068-116">선점형 대기로 인해 오래 동안 대기한 모든 세션의 callstack, sql_text 및 session_id.</span><span class="sxs-lookup"><span data-stu-id="a1068-116">The callstack, sql_text, and session_id for any sessions that have waited for a long time for preemptive waits.</span></span> <span data-ttu-id="a1068-117">기간은 대기 유형마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-117">The duration varies by wait type.</span></span> <span data-ttu-id="a1068-118">선점형 대기는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 외부 API 호출을 대기하는 상황입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-118">A preemptive wait is where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for external API calls.</span></span>  
  
-   <span data-ttu-id="a1068-119">CLR 할당 및 가상 할당 오류의 session_id 및 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-119">The callstack and session_id for CLR allocation and virtual allocation failures.</span></span>  
  
-   <span data-ttu-id="a1068-120">메모리 브로커, 스케줄러 모니터, 메모리 노드 OOM, 보안 및 연결용 ring_buffer 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-120">The ring_buffer events for the memory broker, scheduler monitor, memory node OOM, security, and connectivity.</span></span>  
  
-   <span data-ttu-id="a1068-121">sp_server_diagnostics의 시스템 구성 요소 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-121">System component results from sp_server_diagnostics.</span></span>  
  
-   <span data-ttu-id="a1068-122">scheduler_monitor_system_health_ring_buffer_recorded에 의해 수집되는 인스턴스 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-122">Instance health collected by scheduler_monitor_system_health_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="a1068-123">CLR 할당 실패</span><span class="sxs-lookup"><span data-stu-id="a1068-123">CLR Allocation failures.</span></span>  
  
-   <span data-ttu-id="a1068-124">connectivity_ring_buffer_recorded를 사용하는 동안 연결 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-124">Connectivity errors using connectivity_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="a1068-125">security_error_ring_buffer_recorded를 사용하는 동안 보안 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-125">Security errors using security_error_ring_buffer_recorded.</span></span>  
  
## <a name="viewing-the-session-data"></a><span data-ttu-id="a1068-126">세션 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="a1068-126">Viewing the Session Data</span></span>  
 <span data-ttu-id="a1068-127">이 세션에서는 링 버퍼 대상을 사용하여 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-127">The session uses the ring buffer target to store the data.</span></span> <span data-ttu-id="a1068-128">세션 데이터를 보려면 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-128">To view the session data, use the following query:</span></span>  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 <span data-ttu-id="a1068-129">이벤트 파일의 세션 데이터를 보려면 Management Studio에서 사용할 수 있는 확장 이벤트 사용자 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-129">To view the session data from the event file, use the Extended Events user interface available in Management Studio.</span></span> <span data-ttu-id="a1068-130">자세한 내용은 [View Event Session Data](../../database-engine/view-event-session-data.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1068-130">See [View Event Session Data](../../database-engine/view-event-session-data.md) for more information.</span></span>  
  
## <a name="restoring-the-system_health-session"></a><span data-ttu-id="a1068-131">system_health 세션 복원</span><span class="sxs-lookup"><span data-stu-id="a1068-131">Restoring the system_health Session</span></span>  
 <span data-ttu-id="a1068-132">system_health 세션을 삭제한 경우 쿼리 편집기에서 **u_tables.sql** 파일을 실행하여 세션을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-132">If you delete the system_health session, you can restore it by executing the **u_tables.sql** file in Query Editor.</span></span> <span data-ttu-id="a1068-133">이 파일은 다음 폴더에 있으며 여기서 C:는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로그램 파일을 설치한 드라이브를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-133">This file is located in the following folder, where C: represents the drive where you installed the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files:</span></span>  
  
 <span data-ttu-id="a1068-134">C:\Program Files\Microsoft SQL Server\MSSQL12. \<*instanceid*> \MSSQL\Install</span><span class="sxs-lookup"><span data-stu-id="a1068-134">C:\Program Files\Microsoft SQL Server\MSSQL12.\<*instanceid*>\MSSQL\Install</span></span>  
  
 <span data-ttu-id="a1068-135">세션을 복원한 후에는 ALTER EVENT SESSION 문을 사용하거나 개체 탐색기에서 **확장 이벤트** 노드를 사용하여 세션을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-135">Be aware that after you restore the session, you must start the session by using the ALTER EVENT SESSION statement or by using the **Extended Events** node in Object Explorer.</span></span> <span data-ttu-id="a1068-136">그렇지 않으면 다음에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작할 때 세션이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1068-136">Otherwise, the session starts automatically the next time that you restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1068-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1068-137">See Also</span></span>  
 [<span data-ttu-id="a1068-138">확장 이벤트 도구</span><span class="sxs-lookup"><span data-stu-id="a1068-138">Extended Events Tools</span></span>](extended-events-tools.md)  
  
  
