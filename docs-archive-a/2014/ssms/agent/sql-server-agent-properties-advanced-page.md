---
title: SQL Server 에이전트 속성(고급 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659780"
---
# <a name="sql-server-agent-properties-advanced-page"></a><span data-ttu-id="464d3-102">SQL Server 에이전트 속성(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="464d3-102">SQL Server Agent Properties (Advanced Page)</span></span>
  <span data-ttu-id="464d3-103">이 페이지를 사용 하 여 에이전트 서비스의 고급 속성을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-103">Use this page to view and modify advanced properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="464d3-104">옵션</span><span class="sxs-lookup"><span data-stu-id="464d3-104">Options</span></span>  
 <span data-ttu-id="464d3-105">**SQL Server 이벤트 전달**</span><span class="sxs-lookup"><span data-stu-id="464d3-105">**SQL Server event forwarding**</span></span>  
 <span data-ttu-id="464d3-106">이 범주의 옵션은 이벤트 전달을 활성화하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-106">The options in this category activate and configure event forwarding.</span></span>  
  
 <span data-ttu-id="464d3-107">**다른 서버로 이벤트 전달**</span><span class="sxs-lookup"><span data-stu-id="464d3-107">**Forward events to a different server**</span></span>  
 <span data-ttu-id="464d3-108">다른 서버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-108">Forwards [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events to a different server.</span></span>  
  
 <span data-ttu-id="464d3-109">**Server**</span><span class="sxs-lookup"><span data-stu-id="464d3-109">**Server**</span></span>  
 <span data-ttu-id="464d3-110">이벤트가 전달될 서버 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-110">Select the name of the server to forward events to.</span></span>  
  
 <span data-ttu-id="464d3-111">**처리되지 않은 이벤트**</span><span class="sxs-lookup"><span data-stu-id="464d3-111">**Unhandled events**</span></span>  
 <span data-ttu-id="464d3-112">지정한 서버로 처리되지 않은 이벤트만 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-112">Forwards only unhandled events to the specified server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="464d3-113">에이전트에서는 응답하는 경고가 없는 이벤트만 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-113">Agent forwards only events that no alert responds to.</span></span>  
  
 <span data-ttu-id="464d3-114">**모든 이벤트**</span><span class="sxs-lookup"><span data-stu-id="464d3-114">**All events**</span></span>  
 <span data-ttu-id="464d3-115">모든 이벤트를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-115">Forwards all events.</span></span> <span data-ttu-id="464d3-116">로컬 인스턴스의 경고가 이벤트에 응답하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서는 이벤트를 전달할 뿐 아니라 경고를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-116">When an alert in the local instance responds to the event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent will both forward the event and process the alert.</span></span>  
  
 <span data-ttu-id="464d3-117">**이벤트의 심각도가 다음 이상인 경우**</span><span class="sxs-lookup"><span data-stu-id="464d3-117">**If event has severity at or above**</span></span>  
 <span data-ttu-id="464d3-118">심각도가 지정한 수준 이상인 이벤트만 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-118">Forwards only events with a severity level at or above the level specified.</span></span>  
  
 <span data-ttu-id="464d3-119">**CPU 유휴 상태 판단 기준**</span><span class="sxs-lookup"><span data-stu-id="464d3-119">**Idle CPU Condition**</span></span>  
 <span data-ttu-id="464d3-120">이 범주의 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU 유휴 일정에 실행하도록 예약된 작업을 실행하는 기준을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-120">The options in this category define the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs scheduled to run on the Idle CPU schedule.</span></span>  
  
 <span data-ttu-id="464d3-121">**CPU 유휴 상태 판단 기준 정의**</span><span class="sxs-lookup"><span data-stu-id="464d3-121">**Define idle CPU condition**</span></span>  
 <span data-ttu-id="464d3-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU가 유휴 상태인 것으로 간주하는 기준을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-122">Defines the conditions under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considers the CPU to be idle.</span></span>  
  
 <span data-ttu-id="464d3-123">**평균 CPU 사용량이 다음 미만인 경우**</span><span class="sxs-lookup"><span data-stu-id="464d3-123">**Average CPU usage falls below**</span></span>  
 <span data-ttu-id="464d3-124">미만인 경우 CPU가 유휴 상태인 것으로 간주하는 CPU 사용량의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-124">Percentage of CPU usage below which the CPU is considered to be idle.</span></span>  
  
 <span data-ttu-id="464d3-125">**다음 시간 미만인 경우**</span><span class="sxs-lookup"><span data-stu-id="464d3-125">**And remains below this level for**</span></span>  
 <span data-ttu-id="464d3-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU 유휴 일정에 작업을 실행하기 전에 평균 CPU가 지정한 수준 미만이어야 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="464d3-126">Amount of time that the average CPU must below the level specified before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs jobs on the Idle CPU schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464d3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="464d3-127">See Also</span></span>  
 <span data-ttu-id="464d3-128">[일정을 만들고 작업에 연결](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="464d3-128">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 [<span data-ttu-id="464d3-129">이벤트 관리</span><span class="sxs-lookup"><span data-stu-id="464d3-129">Manage Events</span></span>](manage-events.md)  
  
  
