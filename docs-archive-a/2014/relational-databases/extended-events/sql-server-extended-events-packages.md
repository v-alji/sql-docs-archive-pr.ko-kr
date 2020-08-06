---
title: SQL Server 확장 이벤트 패키지 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], packages
- xe
ms.assetid: 6bcb04fc-ca04-48f4-b96a-20b604973447
author: rothja
ms.author: jroth
ms.openlocfilehash: 45c452300c008d486bd1f4ab4c92b5f76b96ecd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646453"
---
# <a name="sql-server-extended-events-packages"></a><span data-ttu-id="1ba50-102">SQL Server 확장 이벤트 패키지</span><span class="sxs-lookup"><span data-stu-id="1ba50-102">SQL Server Extended Events Packages</span></span>
  <span data-ttu-id="1ba50-103">패키지는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 확장 이벤트 개체를 위한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-103">A package is a container for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events objects.</span></span> <span data-ttu-id="1ba50-104">확장 이벤트 패키지에는 다음과 같은 세 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-104">There are three kinds of Extended Events packages, which include the following:</span></span>  
  
-   <span data-ttu-id="1ba50-105">package0 - 확장 이벤트 시스템 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-105">package0 - Extended Events system objects.</span></span> <span data-ttu-id="1ba50-106">기본 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-106">This is the default package.</span></span>  
  
-   <span data-ttu-id="1ba50-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 관련 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] related objects.</span></span>  
  
-   <span data-ttu-id="1ba50-108">sqlos - SQLOS( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 운영 체제) 관련 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Operating System (SQLOS) related objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ba50-109">SecAudit 패키지는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 감사에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-109">The SecAudit package is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.</span></span> <span data-ttu-id="1ba50-110">이 패키지의 개체는 확장 이벤트 DDL(데이터 정의 언어)을 통해 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-110">None of the objects in the package are available through the Extended Events data definition language (DDL).</span></span>  
  
 <span data-ttu-id="1ba50-111">패키지는 이름, GUID 및 패키지가 들어 있는 바이너리 모듈로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-111">Packages are identified by a name, a GUID, and the binary module that contains the package.</span></span> <span data-ttu-id="1ba50-112">자세한 내용은 [sys.dm_xe_packages&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba50-112">For more information, see [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql).</span></span>  
  
 <span data-ttu-id="1ba50-113">패키지에는 다음과 같은 개체 전체 또는 일부가 포함될 수 있습니다. 각 개체에 대해서는 이 항목의 뒷부분에서 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-113">A package can contain any or all of the following objects, which are discussed in greater detail later in this topic:</span></span>  
  
-   <span data-ttu-id="1ba50-114">이벤트</span><span class="sxs-lookup"><span data-stu-id="1ba50-114">Events</span></span>  
  
-   <span data-ttu-id="1ba50-115">대상</span><span class="sxs-lookup"><span data-stu-id="1ba50-115">Targets</span></span>  
  
-   <span data-ttu-id="1ba50-116">작업</span><span class="sxs-lookup"><span data-stu-id="1ba50-116">Actions</span></span>  
  
-   <span data-ttu-id="1ba50-117">유형</span><span class="sxs-lookup"><span data-stu-id="1ba50-117">Types</span></span>  
  
-   <span data-ttu-id="1ba50-118">조건자</span><span class="sxs-lookup"><span data-stu-id="1ba50-118">Predicates</span></span>  
  
-   <span data-ttu-id="1ba50-119">지도</span><span class="sxs-lookup"><span data-stu-id="1ba50-119">Maps</span></span>  
  
 <span data-ttu-id="1ba50-120">서로 다른 패키지의 개체를 혼합하여 하나의 이벤트 세션에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-120">Objects from different packages can be mixed in an event session.</span></span> <span data-ttu-id="1ba50-121">자세한 내용은 [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba50-121">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
## <a name="package-contents"></a><span data-ttu-id="1ba50-122">패키지 내용</span><span class="sxs-lookup"><span data-stu-id="1ba50-122">Package Contents</span></span>  
 <span data-ttu-id="1ba50-123">다음 그림에서는 패키지에 포함될 수 있는 개체를 보여 줍니다. 패키지는 모듈에 포함되며</span><span class="sxs-lookup"><span data-stu-id="1ba50-123">The following illustration shows the objects that can exist in packages, which are contained in a module.</span></span> <span data-ttu-id="1ba50-124">모듈은 실행 파일 또는 동적 연결 라이브러리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-124">A module can be an executable or a dynamic link library.</span></span>  
  
 <span data-ttu-id="1ba50-125">![모듈, 패키지 및 개체의 관계](../../database-engine/media/xepackagesobjects.gif "모듈, 패키지 및 개체의 관계")</span><span class="sxs-lookup"><span data-stu-id="1ba50-125">![The relationship of a module, packages, and object](../../database-engine/media/xepackagesobjects.gif "The relationship of a module, packages, and object")</span></span>  
  
### <a name="events"></a><span data-ttu-id="1ba50-126">이벤트</span><span class="sxs-lookup"><span data-stu-id="1ba50-126">Events</span></span>  
 <span data-ttu-id="1ba50-127">이벤트는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]같은 프로그램의 실행 경로 내에서 특정 지점을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-127">Events are monitoring points of interest in the execution path of a program, such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ba50-128">이벤트의 발생은 이러한 관심 지점에 도달했다는 사실을 알림과 동시에 이벤트가 발생한 시점의 상태 정보를 제공하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-128">An event firing carries with it the fact that the point of interest was reached, and state information from the time the event was fired.</span></span>  
  
 <span data-ttu-id="1ba50-129">이벤트는 추적이나 동작 트리거를 위해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-129">Events can be used solely for tracing purposes or for triggering actions.</span></span> <span data-ttu-id="1ba50-130">이러한 동작은 동기적이거나 비동기적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-130">These actions can either be synchronous or asynchronous.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ba50-131">이벤트에는 이벤트 발생에 대한 응답으로 트리거할 수 있는 동작에 대한 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-131">An event does not have any knowledge of the actions that may be triggered in response to the event firing.</span></span>  
  
 <span data-ttu-id="1ba50-132">패키지를 확장 이벤트에 등록한 후에는 패키지의 이벤트 집합을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-132">A set of events in a package cannot change after the package is registered with Extended Events.</span></span>  
  
 <span data-ttu-id="1ba50-133">모든 이벤트에는 내용을 정의하는 버전이 지정된 스키마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-133">All events have a versioned schema which defines their contents.</span></span> <span data-ttu-id="1ba50-134">이러한 스키마는 잘 정의된 형식의 이벤트 열로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-134">This schema is composed of event columns with well defined types.</span></span> <span data-ttu-id="1ba50-135">특정 형식의 이벤트는 항상 스키마에 지정된 순서대로 정확하게 데이터를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-135">An event of a specific type must always provide its data in exactly the same order that is specified in the schema.</span></span> <span data-ttu-id="1ba50-136">하지만 이벤트 대상이 제공된 모든 데이터를 소비할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-136">However, an event target does not have to consume all the data that is provided.</span></span>  
  
#### <a name="event-categorization"></a><span data-ttu-id="1ba50-137">이벤트 범주 분류</span><span class="sxs-lookup"><span data-stu-id="1ba50-137">Event Categorization</span></span>  
 <span data-ttu-id="1ba50-138">확장 이벤트는 ETW(Windows용 이벤트 추적)와 유사한 이벤트 범주 분류 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-138">Extended Events uses an event categorization model similar to Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="1ba50-139">범주 분류에는 채널 및 키워드라는 두 가지 이벤트 속성이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-139">Two event properties are used for categorization, channel and keyword.</span></span> <span data-ttu-id="1ba50-140">이러한 속성을 사용하여 확장 이벤트를 ETW 및 그 도구와 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-140">Using these properties supports the integration of Extended Events with ETW and its tools.</span></span>  
  
 <span data-ttu-id="1ba50-141">**채널**</span><span class="sxs-lookup"><span data-stu-id="1ba50-141">**Channel**</span></span>  
  
 <span data-ttu-id="1ba50-142">채널은 이벤트의 대상을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-142">A channel identifies the audience for an event.</span></span> <span data-ttu-id="1ba50-143">다음 표에서는 이러한 채널에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-143">These channels are described in the following table.</span></span>  
  
|<span data-ttu-id="1ba50-144">용어</span><span class="sxs-lookup"><span data-stu-id="1ba50-144">Term</span></span>|<span data-ttu-id="1ba50-145">정의</span><span class="sxs-lookup"><span data-stu-id="1ba50-145">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="1ba50-146">Admin</span><span class="sxs-lookup"><span data-stu-id="1ba50-146">Admin</span></span>|<span data-ttu-id="1ba50-147">Admin 이벤트는 주로 최종 사용자, 관리자 및 지원 담당자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-147">Admin events are primarily targeted to the end users, administrators, and support.</span></span> <span data-ttu-id="1ba50-148">Admin 채널의 이벤트는 관리자가 대처할 수 있는 잘 정의된 솔루션이 마련된 문제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-148">The events that are found in the admin channels indicate a problem with a well-defined solution that an administrator can act on.</span></span> <span data-ttu-id="1ba50-149">Admin 이벤트의 예로 애플리케이션에서 프린터를 연결하는 데 실패한 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-149">An example of an admin event is when an application fails to connect to a printer.</span></span> <span data-ttu-id="1ba50-150">이러한 이벤트는 문제를 해결하기 위해 수행할 작업을 사용자에게 알려 주는 적절한 문서나 메시지와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-150">These events are either well-documented or have a message associated with them that tells the reader what to do to rectify the problem.</span></span>|  
|<span data-ttu-id="1ba50-151">작동</span><span class="sxs-lookup"><span data-stu-id="1ba50-151">Operational</span></span>|<span data-ttu-id="1ba50-152">Operational 이벤트는 문제 또는 발생을 분석 및 진단하는 데 사용되며</span><span class="sxs-lookup"><span data-stu-id="1ba50-152">Operational events are used for analyzing and diagnosing a problem or occurrence.</span></span> <span data-ttu-id="1ba50-153">이러한 이벤트를 사용하여 문제 또는 항목에 따라 도구 또는 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-153">They can be used to trigger tools or tasks based on the problem or occurrence.</span></span> <span data-ttu-id="1ba50-154">Operational 이벤트의 예로는 시스템에서 프린터를 추가 또는 제거하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-154">An example of an operational event is when a printer is added or removed from a system.</span></span>|  
|<span data-ttu-id="1ba50-155">Analytic</span><span class="sxs-lookup"><span data-stu-id="1ba50-155">Analytic</span></span>|<span data-ttu-id="1ba50-156">Analytic 이벤트는 고용량으로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-156">Analytic events are published in high volume.</span></span> <span data-ttu-id="1ba50-157">이러한 이벤트는 프로그램 작업을 나타내며 일반적으로 성능 검사에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-157">They describe program operation and are typically used in performance investigations.</span></span>|  
|<span data-ttu-id="1ba50-158">디버그</span><span class="sxs-lookup"><span data-stu-id="1ba50-158">Debug</span></span>|<span data-ttu-id="1ba50-159">Debug 이벤트는 디버깅을 위해 문제를 진단하는 개발자에 의해서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-159">Debug events are used solely by developers to diagnose a problem for debugging.</span></span><br /><br /> <span data-ttu-id="1ba50-160">참고: 디버그 채널의 이벤트는 내부 구현과 관련 된 상태 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-160">Note: Events in the Debug channel return internal implementation-specific state data.</span></span> <span data-ttu-id="1ba50-161">이벤트가 반환하는 스키마와 데이터는 변경되거나 이후 SQL Server 버전에서 유효하지 않게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-161">The schemas and data that the events return may change or become invalid in future versions of SQL Server.</span></span> <span data-ttu-id="1ba50-162">따라서 이후 버전의 SQL Server에서는 예고 없이 디버그 채널의 이벤트가 변경되거나 제거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-162">Therefore, events in the Debug channel may change or be removed in future versions of SQL Server without notice.</span></span>|  
  
 <span data-ttu-id="1ba50-163">**키워드**</span><span class="sxs-lookup"><span data-stu-id="1ba50-163">**Keyword**</span></span>  
  
 <span data-ttu-id="1ba50-164">키워드는 애플리케이션마다 다르게 사용되며 관련된 이벤트를 보다 세부적으로 그룹화할 수 있으므로 세션에서 사용할 이벤트를 더욱 쉽게 지정하고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-164">A keyword is application specific and enables a finer-grained grouping of related events, which makes it easier for you to specify and retrieve an event that you want to use in a session.</span></span> <span data-ttu-id="1ba50-165">다음 쿼리를 사용하여 키워드 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-165">You can use the following query to obtain keyword information.</span></span>  
  
```  
select map_value Keyword from sys.dm_xe_map_values  
where name = 'keyword_map'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1ba50-166">키워드는 SQL 추적 이벤트의 현재 그룹화와 밀접하게 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-166">Keywords map closely to the current grouping of SQL Trace events.</span></span>  
  
### <a name="targets"></a><span data-ttu-id="1ba50-167">대상</span><span class="sxs-lookup"><span data-stu-id="1ba50-167">Targets</span></span>  
 <span data-ttu-id="1ba50-168">대상은 이벤트의 소비자입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-168">Targets are event consumers.</span></span> <span data-ttu-id="1ba50-169">대상은 이벤트가 발생하는 스레드에서 동기적으로 이벤트를 처리하거나 시스템을 통해 제공되는 스레드에서 비동기적으로 이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-169">Targets process events, either synchronously on the thread that fires the event or asynchronously on a system provided thread.</span></span> <span data-ttu-id="1ba50-170">확장 이벤트는 이벤트 출력을 전송하는 데 적합하게 사용할 수 있는 여러 대상을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-170">Extended Events provides several targets that you can use as appropriate for directing event output.</span></span> <span data-ttu-id="1ba50-171">자세한 내용은 [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba50-171">For more information, see [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md).</span></span>  
  
### <a name="actions"></a><span data-ttu-id="1ba50-172">작업</span><span class="sxs-lookup"><span data-stu-id="1ba50-172">Actions</span></span>  
 <span data-ttu-id="1ba50-173">동작은 이벤트에 대한 한 차례 또는 일련의 프로그래밍 방식 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-173">An action is a programmatic response or series of responses to an event.</span></span> <span data-ttu-id="1ba50-174">동작은 이벤트에 바인딩되며 각 이벤트에는 일련의 고유한 동작이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-174">Actions are bound to an event, and each event may have a unique set of actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ba50-175">특정 이벤트 집합을 위해 사용되는 동작은 알 수 없는 이벤트에 바인딩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-175">Actions that are intended for a specific set of events cannot bind to unknown events.</span></span>  
  
 <span data-ttu-id="1ba50-176">이벤트에 바인딩된 동작은 이벤트가 발생한 스레드에서 동기적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-176">An action bound to an event is invoked synchronously on the thread that fired the event.</span></span> <span data-ttu-id="1ba50-177">다양한 유형의 동작이 있으며 기능도 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-177">There are many types of actions and they have a wide range of capabilities.</span></span> <span data-ttu-id="1ba50-178">동작의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-178">Actions can:</span></span>  
  
-   <span data-ttu-id="1ba50-179">스택 덤프를 캡처하고 데이터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-179">Capture a stack dump and inspect data.</span></span>  
  
-   <span data-ttu-id="1ba50-180">변수 스토리지를 사용하여 상태 정보를 로컬 컨텍스트로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-180">Store state information in a local context using variable storage.</span></span>  
  
-   <span data-ttu-id="1ba50-181">이벤트 데이터를 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-181">Aggregate event data.</span></span>  
  
-   <span data-ttu-id="1ba50-182">이벤트 데이터에 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-182">Append data to event data.</span></span>  
  
 <span data-ttu-id="1ba50-183">일반적이고 잘 알려진 동작의 예를 몇 가지 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-183">Some typical and well known examples of actions are:</span></span>  
  
-   <span data-ttu-id="1ba50-184">스택 덤퍼</span><span class="sxs-lookup"><span data-stu-id="1ba50-184">Stack dumper</span></span>  
  
-   <span data-ttu-id="1ba50-185">실행 계획 감지([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에만 해당)</span><span class="sxs-lookup"><span data-stu-id="1ba50-185">Execution plan detection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1ba50-186">스택 컬렉션([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에만 해당)</span><span class="sxs-lookup"><span data-stu-id="1ba50-186">stack collection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   <span data-ttu-id="1ba50-187">런타임 통계 계산</span><span class="sxs-lookup"><span data-stu-id="1ba50-187">Run time statistics calculation</span></span>  
  
-   <span data-ttu-id="1ba50-188">예외 시 사용자 입력 수집</span><span class="sxs-lookup"><span data-stu-id="1ba50-188">Gather user input on exception</span></span>  
  
### <a name="predicates"></a><span data-ttu-id="1ba50-189">조건자</span><span class="sxs-lookup"><span data-stu-id="1ba50-189">Predicates</span></span>  
 <span data-ttu-id="1ba50-190">조건자는 이벤트를 처리할 때 이벤트를 평가하는 데 사용되는 논리적 규칙의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-190">Predicates are a set of logical rules that are used to evaluate events when they are processed.</span></span> <span data-ttu-id="1ba50-191">확장 이벤트 사용자는 조건자를 사용하여 특정 기준에 맞는 이벤트 데이터를 선별적으로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-191">This enables the Extended Events user to selectively capture event data based on specific criteria.</span></span>  
  
 <span data-ttu-id="1ba50-192">조건자는 데이터를 로컬 컨텍스트에 저장하여 이벤트가 발생하는 *n* 분 또는 *n* 번마다 true를 한 번만 반환하는 조건자를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-192">Predicates can store data in a local context that can be used for creating predicates that return true once every *n* minutes or every *n* times that an event fires.</span></span> <span data-ttu-id="1ba50-193">이 로컬 컨텍스트 스토리지를 사용하면 조건자를 동적으로 업데이트함으로써 나중에 발생한 이벤트에 전과 유사한 데이터가 있는 경우 이를 생략하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-193">This local context storage can also be used to dynamically update the predicate, thereby suppressing future event firing if the events contain similar data.</span></span>  
  
 <span data-ttu-id="1ba50-194">조건자는 이벤트별 데이터와 스레드 ID 등의 컨텍스트 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-194">Predicates have the ability to retrieve context information, such as the thread ID, as well as event specific data.</span></span> <span data-ttu-id="1ba50-195">조건자는 완전한 부울 식으로 평가될 수 있으며 처음으로 전체 식이 false가 될 때 단락(short circuit)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-195">Predicates are evaluated as full Boolean expressions, and support short circuiting at the first point where the entire expression is found to be false.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ba50-196">이전 조건자 검사에 실패한 경우 부작용이 있는 조건자는 평가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-196">Predicates with side effects may not be evaluated if an earlier predicate check fails.</span></span>  
  
### <a name="types"></a><span data-ttu-id="1ba50-197">유형</span><span class="sxs-lookup"><span data-stu-id="1ba50-197">Types</span></span>  
 <span data-ttu-id="1ba50-198">데이터는 연결된 바이트의 집합이므로 데이터를 해석하려면 바이트 집합의 길이 및 특성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-198">Because data is a collection of bytes strung together, the length and characteristics of the byte collection are required in order to interpret the data.</span></span> <span data-ttu-id="1ba50-199">이 정보는 Type 개체에 캡슐화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-199">This information is encapsulated in the Type object.</span></span> <span data-ttu-id="1ba50-200">패키지 개체에 제공되는 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-200">The following types are provided for package objects:</span></span>  
  
-   <span data-ttu-id="1ba50-201">event</span><span class="sxs-lookup"><span data-stu-id="1ba50-201">event</span></span>  
  
-   <span data-ttu-id="1ba50-202">action</span><span class="sxs-lookup"><span data-stu-id="1ba50-202">action</span></span>  
  
-   <span data-ttu-id="1ba50-203">대상</span><span class="sxs-lookup"><span data-stu-id="1ba50-203">target</span></span>  
  
-   <span data-ttu-id="1ba50-204">pred_source</span><span class="sxs-lookup"><span data-stu-id="1ba50-204">pred_source</span></span>  
  
-   <span data-ttu-id="1ba50-205">pred_compare</span><span class="sxs-lookup"><span data-stu-id="1ba50-205">pred_compare</span></span>  
  
-   <span data-ttu-id="1ba50-206">형식</span><span class="sxs-lookup"><span data-stu-id="1ba50-206">type</span></span>  
  
 <span data-ttu-id="1ba50-207">자세한 내용은 [sys.dm_xe_objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba50-207">For more information, see [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql).</span></span>  
  
### <a name="maps"></a><span data-ttu-id="1ba50-208">지도</span><span class="sxs-lookup"><span data-stu-id="1ba50-208">Maps</span></span>  
 <span data-ttu-id="1ba50-209">맵 테이블은 내부 값을 문자열에 매핑함으로써 값이 무엇을 나타내는지 사용자에게 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-209">A map table maps an internal value to a string, which enables a user to know what the value represents.</span></span> <span data-ttu-id="1ba50-210">사용자는 숫자 값뿐만 아니라 내부 값의 의미를 나타내는 설명도 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-210">Instead of only being able to obtain a numeric value, a user can get a meaningful description of the internal value.</span></span> <span data-ttu-id="1ba50-211">다음 쿼리에서는 맵 값을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-211">The following query shows how to obtain map values.</span></span>  
  
```  
select map_key, map_value from sys.dm_xe_map_values  
where name = 'lock_mode'  
```  
  
 <span data-ttu-id="1ba50-212">위 쿼리에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-212">The preceding query produces the following output.</span></span>  
  
 `map_key     map_value`  
  
 `---------------------`  
  
 `0           NL`  
  
 `1           SCH_S`  
  
 `2           SCH_M`  
  
 `3           S`  
  
 `4           U`  
  
 `5           X`  
  
 `6           IS`  
  
 `7           IU`  
  
 `8           IX`  
  
 `9           SIU`  
  
 `10          SIX`  
  
 `11          UIX`  
  
 `12          BU`  
  
 `13          RS_S`  
  
 `14          RS_U`  
  
 `15          RI_NL`  
  
 `16          RI_S`  
  
 `17          RI_U`  
  
 `18          RI_X`  
  
 `19          RX_S`  
  
 `20          RX_U`  
  
 `21          RX_X`  
  
 `21          RX_X`  
  
 <span data-ttu-id="1ba50-213">이 표의 경우 mode라는 열이 있고 값이 5라고 가정하면</span><span class="sxs-lookup"><span data-stu-id="1ba50-213">Using this table as an example, assume that you have a column named mode, and its value is 5.</span></span> <span data-ttu-id="1ba50-214">표에서 5가 X에 매핑되므로 잠금 유형은 배타입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba50-214">The table indicates that 5 maps to X, which means the lock type is Exclusive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba50-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ba50-215">See Also</span></span>  
 <span data-ttu-id="1ba50-216">[확장 이벤트 세션 SQL Server](sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="1ba50-216">[SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md) </span></span>  
 <span data-ttu-id="1ba50-217">[SQL Server 확장 이벤트 엔진](sql-server-extended-events-engine.md) </span><span class="sxs-lookup"><span data-stu-id="1ba50-217">[SQL Server Extended Events Engine](sql-server-extended-events-engine.md) </span></span>  
 [<span data-ttu-id="1ba50-218">SQL Server 확장 이벤트 대상</span><span class="sxs-lookup"><span data-stu-id="1ba50-218">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
