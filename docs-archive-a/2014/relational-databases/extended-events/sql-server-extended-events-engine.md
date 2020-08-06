---
title: SQL Server 확장 이벤트 엔진 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
author: rothja
ms.author: jroth
ms.openlocfilehash: ef11ac8e2cfaf39d2bca90f1d5d52439989ee327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646455"
---
# <a name="sql-server-extended-events-engine"></a><span data-ttu-id="afa83-102">SQL Server 확장 이벤트 엔진</span><span class="sxs-lookup"><span data-stu-id="afa83-102">SQL Server Extended Events Engine</span></span>
  <span data-ttu-id="afa83-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 확장 이벤트 엔진은 다음과 같은 역할을 하는 서비스 및 개체의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events engine is a collection of services and objects that:</span></span>  
  
-   <span data-ttu-id="afa83-104">이벤트를 정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-104">Enable the definition of events.</span></span>  
  
-   <span data-ttu-id="afa83-105">이벤트 데이터를 처리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-105">Enable processing event data.</span></span>  
  
-   <span data-ttu-id="afa83-106">시스템의 확장 이벤트 서비스 및 개체를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-106">Manage Extended Events services and objects in the system.</span></span>  
  
-   <span data-ttu-id="afa83-107">확장 이벤트 세션의 목록을 유지 관리하고 이 목록에 대한 액세스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-107">Maintain a list of Extended Events sessions and manage access to that list.</span></span>  
  
 <span data-ttu-id="afa83-108">확장 이벤트 엔진 자체는 이벤트가 발생할 때 실행할 이벤트 또는 동작을 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-108">The Extended Events engine itself does not provide any events or actions to take when an event fires.</span></span> <span data-ttu-id="afa83-109">대신 확장 이벤트 엔진을 사용하는 프로세스가 엔진과의 상호 작용을 정의하며</span><span class="sxs-lookup"><span data-stu-id="afa83-109">The processes that use the Extended Events engine define interaction with the engine.</span></span> <span data-ttu-id="afa83-110">이벤트 지점을 추가하고 이벤트 발생에 대한 응답으로 실행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-110">These processes add event points and supply the actions to take in response to event firing.</span></span>  
  
 <span data-ttu-id="afa83-111">다음 그림은 확장 이벤트 세션을 간략히 요약하여 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-111">The following illustration shows a simplified view of an Extended Events session.</span></span> <span data-ttu-id="afa83-112">자세한 내용은 [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afa83-112">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
 <span data-ttu-id="afa83-113">![자세한 확장 이벤트 아키텍처](../../database-engine/media/xearchitecturedetailed.gif "자세한 확장 이벤트 아키텍처")</span><span class="sxs-lookup"><span data-stu-id="afa83-113">![Detailed extended events architecture](../../database-engine/media/xearchitecturedetailed.gif "Detailed extended events architecture")</span></span>  
  
 <span data-ttu-id="afa83-114">다음 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="afa83-114">Note the following:</span></span>  
  
-   <span data-ttu-id="afa83-115">각 Windows 프로세스에는 하나 이상의 모듈(**Win32 프로세스**, **Win32 모듈**)이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-115">Each Windows process can have one or more modules (**Win32 process**, **Win32 module**).</span></span> <span data-ttu-id="afa83-116">이를 *바이너리* 또는 *실행 모듈*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-116">These are also known as *binaries* or *executable modules*.</span></span>  
  
-   <span data-ttu-id="afa83-117">각 Windows 프로세스 모듈은 하나 이상의 확장 이벤트 개체(**Type**,**Target**, **Action**, **Map**, **Predicate**및 **Event**)가 포함된 확장 이벤트 패키지( **Package**)를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-117">Each of the Windows process modules can contain one or more Extended Events packages (**Package**), which contain one or more Extended Events objects (**Type**, **Target**, **Action**, **Map**, **Predicate**, and **Event**).</span></span>  
  
-   <span data-ttu-id="afa83-118">호스트 프로세스 내부에는 다음과 같은 역할을 하는 확장 이벤트 엔진(**Extended event engine**)의 인스턴스가 하나만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-118">Inside a host process there can only be one instance of the Extended Events engine (**Extended event engine**), which:</span></span>  
  
    -   <span data-ttu-id="afa83-119">세션 열거와 같은 세션의 일부 기능을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-119">Manages some aspects of the session (for example, enumerating sessions).</span></span>  
  
    -   <span data-ttu-id="afa83-120">디스패치(**Dispatcher**)를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-120">Handles dispatching (**Dispatcher**).</span></span> <span data-ttu-id="afa83-121">이는 스레드 풀과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-121">This is similar to a thread pool.</span></span>  
  
    -   <span data-ttu-id="afa83-122">이벤트를 위한 메모리 버퍼(**Buffer**)를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-122">Handles memory buffers (**Buffer**) for events.</span></span> <span data-ttu-id="afa83-123">버퍼가 가득 차면 대상으로 디스패치됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-123">When buffers are filled, the buffers are dispatched to targets.</span></span>  
  
-   <span data-ttu-id="afa83-124">세션이 생성되고 이벤트가 선택적으로 세션(**Session context**)에 바인딩된 후 다음이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-124">After a session is created and events are optionally bound to the session (**Session context**):</span></span>  
  
    -   <span data-ttu-id="afa83-125">대상의 인스턴스(**Target instance**)가 생성되어 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-125">Instances of targets (**Target instance**) may be also be created and added to the session.</span></span>  
  
    -   <span data-ttu-id="afa83-126">버퍼가 가득 차면 해당 버퍼가 대상으로 디스패치됩니다.</span><span class="sxs-lookup"><span data-stu-id="afa83-126">When buffers are filled, those buffers are dispatched to targets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa83-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="afa83-127">See Also</span></span>  
 [<span data-ttu-id="afa83-128">확장 이벤트</span><span class="sxs-lookup"><span data-stu-id="afa83-128">Extended Events</span></span>](extended-events.md)  
  
  
