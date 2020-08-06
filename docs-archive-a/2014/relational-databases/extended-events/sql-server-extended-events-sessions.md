---
title: SQL Server 확장 이벤트 세션 | Microsoft 문서
ms.custom: ''
ms.date: 05/26/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- sessions
- extend events [SQL Server]
ms.assetid: c3c92544-351a-4bce-a06a-1f2a47e494e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3aab8c57a578ea60829514b575e168bc5a1dd8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646451"
---
# <a name="sql-server-extended-events-sessions"></a><span data-ttu-id="b9b75-102">SQL Server Extended Events Sessions</span><span class="sxs-lookup"><span data-stu-id="b9b75-102">SQL Server Extended Events Sessions</span></span>
  <span data-ttu-id="b9b75-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 확장 이벤트 세션은 확장 이벤트 엔진을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-103">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events session is created in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process hosting the Extended Events engine.</span></span> <span data-ttu-id="b9b75-104">확장 이벤트 세션의 다음과 같은 요소는 확장 이벤트 인프라 및 일반적인 프로세스를 파악할 수 있는 컨텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-104">The following aspects of an Extended Events session provide a context for understanding the Extended Events infrastructure and the general processing that takes place:</span></span>  
  
-   <span data-ttu-id="b9b75-105">세션 상태.</span><span class="sxs-lookup"><span data-stu-id="b9b75-105">Session states.</span></span> <span data-ttu-id="b9b75-106">CREATE EVENT SESSION 및 ALTER EVENT SESSION 문이 실행될 때 확장 이벤트 세션의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-106">The different states that an Extended Events session is in when CREATE EVENT SESSION and ALTER EVENT SESSION statements are executed.</span></span>  
  
-   <span data-ttu-id="b9b75-107">세션 내용 및 특징.</span><span class="sxs-lookup"><span data-stu-id="b9b75-107">Session content and characteristics.</span></span> <span data-ttu-id="b9b75-108">대상 및 이벤트 같은 확장 이벤트 세션의 내용과 이러한 개체가 단일 세션에서 또는 여러 세션 간에 상호 관련되는 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-108">The content of an Extended Events session, such as targets and events, and how these objects are related in a session or between sessions.</span></span>  
  
## <a name="session-states"></a><span data-ttu-id="b9b75-109">세션 상태</span><span class="sxs-lookup"><span data-stu-id="b9b75-109">Session States</span></span>  
 <span data-ttu-id="b9b75-110">다음 그림에서는 확장 이벤트 세션의 다양한 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-110">The following illustration shows the various states of an Extended Events session.</span></span>  

<span data-ttu-id="b9b75-111">![확장 이벤트 세션 상태](../../database-engine/media/xesessionstate.png "확장 이벤트 세션 상태")</span><span class="sxs-lookup"><span data-stu-id="b9b75-111">![Extended event session state](../../database-engine/media/xesessionstate.png "Extended event session state")</span></span>

 <span data-ttu-id="b9b75-112">위 그림을 보면 이벤트 세션에 대해 다른 DDL 명령이 실행됨에 따라 세션 상태가 바뀜을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-112">Referring to the preceding figure, note that session state changes as the different DDL commands are issued for an event session.</span></span> <span data-ttu-id="b9b75-113">다음 표에서는 이러한 상태 변경을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-113">The following table describes these changes in state.</span></span>  
  
|<span data-ttu-id="b9b75-114">그림 레이블</span><span class="sxs-lookup"><span data-stu-id="b9b75-114">Illustration label</span></span>|<span data-ttu-id="b9b75-115">DDL 문</span><span class="sxs-lookup"><span data-stu-id="b9b75-115">DDL statement</span></span>|<span data-ttu-id="b9b75-116">설명</span><span class="sxs-lookup"><span data-stu-id="b9b75-116">Description</span></span>|  
|------------------------|-------------------|-----------------|  
|<span data-ttu-id="b9b75-117">생성</span><span class="sxs-lookup"><span data-stu-id="b9b75-117">Create</span></span>|<span data-ttu-id="b9b75-118">CREATE EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="b9b75-118">CREATE EVENT SESSION</span></span>|<span data-ttu-id="b9b75-119">호스트 프로세스는 CREATE EVENT SESSION 문에서 제공된 메타데이터가 포함된 세션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-119">The host process creates a session object that contains the metadata provided by CREATE EVENT SESSION.</span></span> <span data-ttu-id="b9b75-120">호스트 프로세스는 세션 정의 및 사용자 권한 수준을 검사하고 master 데이터베이스에 메타데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-120">The host process validates the session definition, validates the user permission level, and stores the metadata in the master database.</span></span> <span data-ttu-id="b9b75-121">이 시점에서 세션은 활성 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-121">At this point the session is not active.</span></span>|  
|<span data-ttu-id="b9b75-122">변경</span><span class="sxs-lookup"><span data-stu-id="b9b75-122">Alter</span></span>|<span data-ttu-id="b9b75-123">ALTER EVENT SESSION, STATE=START</span><span class="sxs-lookup"><span data-stu-id="b9b75-123">ALTER EVENT SESSION, STATE=START</span></span>|<span data-ttu-id="b9b75-124">호스트 프로세스가 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-124">The host process starts the session.</span></span> <span data-ttu-id="b9b75-125">호스트 프로세스는 저장된 메타데이터를 읽고 세션 정의를 검사하며 사용자 권한 수준을 확인하고 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-125">The host process reads the stored metadata, validates the session definition, verifies the level of user permission level, and creates the session.</span></span> <span data-ttu-id="b9b75-126">이벤트 및 대상과 같은 세션 개체가 로드되며 이벤트 처리는 활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-126">Session objects, such as events and targets, are loaded and event handling is active.</span></span>|  
|<span data-ttu-id="b9b75-127">변경</span><span class="sxs-lookup"><span data-stu-id="b9b75-127">Alter</span></span>|<span data-ttu-id="b9b75-128">ALTER EVENT SESSION, STATE=STOP</span><span class="sxs-lookup"><span data-stu-id="b9b75-128">ALTER EVENT SESSION, STATE=STOP</span></span>|<span data-ttu-id="b9b75-129">호스트 프로세스가 활성 세션을 중지하지만 메타데이터는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-129">The host process stops the active session but retains the metadata.</span></span>|  
|<span data-ttu-id="b9b75-130">드롭</span><span class="sxs-lookup"><span data-stu-id="b9b75-130">Drop</span></span>|<span data-ttu-id="b9b75-131">DROP EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="b9b75-131">DROP EVENT SESSION</span></span>|<span data-ttu-id="b9b75-132">세션이 활성 상태인지 여부에 따라 Drop(DROP SESSION)은 메타데이터를 삭제하고 활성 세션을 종료하거나 세션 메타데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-132">Depending on whether or not the session is active, Drop (DROP SESSION) will delete the metadata and close the active session, or delete the session metadata.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b9b75-133">ALTER EVENT SESSION과 DROP EVENT SESSION 두 가지 모두 메타데이터에 적용되거나 활성 세션과 메타데이터에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-133">Both ALTER EVENT SESSION and DROP EVENT SESSION can be applied to the metadata or to an active session and the metadata.</span></span>  
  
## <a name="session-content-and-characteristics"></a><span data-ttu-id="b9b75-134">세션 내용 및 특징</span><span class="sxs-lookup"><span data-stu-id="b9b75-134">Session Content and Characteristics</span></span>  
 <span data-ttu-id="b9b75-135">확장 이벤트 세션에는 암시적인 경계가 있어 한 세션의 구성으로 인해 다른 세션의 구성이 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-135">Extended Event sessions have implied boundaries in that the configuration of one session does not change the configuration of another session.</span></span> <span data-ttu-id="b9b75-136">그러나 이러한 경계는 이벤트 또는 대상이 두 개 이상의 세션에서 사용되는 것을 차단하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-136">However, these boundaries do not prevent an event or target from being used in more than one session.</span></span>  
  
 <span data-ttu-id="b9b75-137">다음 그림에서는 세션 내용, 그리고 패키지와 세션 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-137">The following illustration shows session content and the relationship between packages and sessions.</span></span>  
  
 <span data-ttu-id="b9b75-138">![세션에서의 개체 공존 및 공유](../../database-engine/media/xesessions.gif "세션에서의 개체 공존 및 공유")</span><span class="sxs-lookup"><span data-stu-id="b9b75-138">![Object co-existance and sharing in sessions.](../../database-engine/media/xesessions.gif "Object co-existance and sharing in sessions.")</span></span>  
  
 <span data-ttu-id="b9b75-139">위 그림을 보면 다음과 같은 사실을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-139">Referring to the preceding illustration, note that:</span></span>  
  
-   <span data-ttu-id="b9b75-140">패키지 개체와 세션 간의 매핑은 다 대 다이며, 이는 하나의 개체가 여러 세션에서 나타나고 하나의 세션에 여러 개체가 포함될 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-140">The mapping between package objects and sessions is many to many, which means that an object can appear in several sessions, and a session can contain several objects.</span></span>  
  
-   <span data-ttu-id="b9b75-141">동일한 이벤트(Event 1) 또는 대상(Target 1)이 두 개 이상의 세션에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-141">The same event (Event 1) or target (Target 1) can be enabled in more than one session.</span></span>  
  
 <span data-ttu-id="b9b75-142">세션의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-142">Sessions have the following characteristics:</span></span>  
  
-   <span data-ttu-id="b9b75-143">동작과 조건자는 세션별로 이벤트에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-143">Actions and predicates are bound to events on a per-session basis.</span></span> <span data-ttu-id="b9b75-144">Session A에 Action 1, Predicate Z와 함께 Event 1이 있어도 Session B에 조건자 없이 Action 2, Action 3과 함께 Event 1이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-144">If you have Event 1 in Session A with Action 1 and Predicate Z, this will not in any way affect having Event 1 in Session B with Action 2 and Action 3 with no predicate.</span></span>  
  
-   <span data-ttu-id="b9b75-145">정책이 세션에 연결되어 버퍼링과 디스패치, 인과 관계 추적을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-145">Policies are attached to sessions to handle buffering and dispatch, and causality tracking.</span></span>  
  
 <span data-ttu-id="b9b75-146">**버퍼링 및 디스패치**</span><span class="sxs-lookup"><span data-stu-id="b9b75-146">**Buffering and dispatch**</span></span>  
  
 <span data-ttu-id="b9b75-147">버퍼링은 이벤트 세션이 실행되는 동안 이벤트 데이터가 저장되는 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-147">Buffering refers to how event data is stored while an event session is running.</span></span>  <span data-ttu-id="b9b75-148">버퍼링 정책은 이벤트 데이터에 사용할 메모리 크기와 이벤트에 대한 손실 정책을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-148">Buffering policies specify how much memory to use for event data, and the loss policy for the events.</span></span> <span data-ttu-id="b9b75-149">디스패치는 이벤트를 처리하기 위해 대상에 전달하기 전에 버퍼에 유지하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-149">Dispatch refers to the amount of time events will stay in buffers before being served to targets for processing.</span></span>  
  
 <span data-ttu-id="b9b75-150">**인과 관계 추적**</span><span class="sxs-lookup"><span data-stu-id="b9b75-150">**Causality tracking**</span></span>  
  
 <span data-ttu-id="b9b75-151">인과 관계 추적은 여러 태스크에 걸쳐 작업을 추적할 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-151">Causality tracking provides the ability to track work across multiple tasks.</span></span> <span data-ttu-id="b9b75-152">인과 관계 추적을 사용하면 각 발생 이벤트는 시스템 전체에서 고유한 작업 ID를 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-152">When causality tracking is enabled, each event fired has a unique activity ID across the system.</span></span> <span data-ttu-id="b9b75-153">작업 ID는 태스크에 대한 모든 이벤트에서 일관적으로 유지되는 GUID 값과 이벤트가 발생할 때마다 증가하는 시퀀스 번호의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-153">The activity ID is a combination of a GUID value that remains constant across all events for a task, and a sequence number that is incremented each time an event is fired.</span></span> <span data-ttu-id="b9b75-154">한 태스크가 다른 태스크의 작업 수행을 유발하면 부모 태스크의 작업 ID가 자식 태스크로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-154">When one task causes work to be done on another, the activity ID of the parent is sent to the child task.</span></span> <span data-ttu-id="b9b75-155">자식 태스크는 처음 이벤트를 발생시킬 때 부모의 작업 ID를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-155">The child task outputs the parent's activity ID the first time it fires an event.</span></span>  
  
 <span data-ttu-id="b9b75-156">확장 이벤트 아키텍처는 다양한 개체를 함께 사용하여 특정 문제를 처리할 수 있는 유연한 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9b75-156">The Extended Events architecture provides a flexible system that allows a variety of objects to be used together to solve specific problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b75-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9b75-157">See Also</span></span>  
 [<span data-ttu-id="b9b75-158">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="b9b75-158">Extended Events</span></span>](extended-events.md)  
  
  
