---
title: 구독, 배포자에서 구독자로의 연결 기록(트랜잭션 구독) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.disttosub.f1
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5cb9d708b75a9414725907530c7454cdba26d135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740799"
---
# <a name="subscription-distributor-to-subscriber-history-transactional-subscription"></a><span data-ttu-id="27c97-102">구독, 배포자에서 구독자로의 연결 기록(트랜잭션 구독)</span><span class="sxs-lookup"><span data-stu-id="27c97-102">Subscription, Distributor to Subscriber History (Transactional Subscription)</span></span>
  <span data-ttu-id="27c97-103">**배포자에서 구독자로의 연결 기록** 탭은 상태, 기록, 정보 메시지, 모든 오류 메시지 등 배포 에이전트에 대한 자세한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-103">The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27c97-104">옵션</span><span class="sxs-lookup"><span data-stu-id="27c97-104">Options</span></span>  
 <span data-ttu-id="27c97-105">**보기** 메뉴에서 보려는 배포 에이전트 세션을 선택한 다음 **배포 에이전트의 세션**표에서 특정 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-105">Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**.</span></span> <span data-ttu-id="27c97-106">**선택한 세션의 동작**표에 이 세션에 대한 자세한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="27c97-107">선택한 세션이 오류로 인해 종료될 경우 **선택한 세션에 대한 오류 정보 또는 메시지** 라는 텍스트 영역 또한 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="27c97-108">**보기**</span><span class="sxs-lookup"><span data-stu-id="27c97-108">**View**</span></span>  
 <span data-ttu-id="27c97-109">확인할 배포 에이전트 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-109">Select which Distribution Agent sessions to view.</span></span> <span data-ttu-id="27c97-110">배포 에이전트는 일반적으로 계속 실행되므로 확인할 세션이 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-110">The Distribution Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="27c97-111">**상태**</span><span class="sxs-lookup"><span data-stu-id="27c97-111">**Status**</span></span>  
 <span data-ttu-id="27c97-112">배포 에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-112">The status of the Distribution Agent.</span></span> <span data-ttu-id="27c97-113">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="27c97-114">오류</span><span class="sxs-lookup"><span data-stu-id="27c97-114">Error</span></span>  
  
-   <span data-ttu-id="27c97-115">Completed</span><span class="sxs-lookup"><span data-stu-id="27c97-115">Completed</span></span>  
  
-   <span data-ttu-id="27c97-116">다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="27c97-116">Retrying</span></span>  
  
-   <span data-ttu-id="27c97-117">실행 중</span><span class="sxs-lookup"><span data-stu-id="27c97-117">Running</span></span>  
  
 <span data-ttu-id="27c97-118">**시작 시간**</span><span class="sxs-lookup"><span data-stu-id="27c97-118">**Start Time**</span></span>  
 <span data-ttu-id="27c97-119">세션의 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="27c97-120">**종료 시간**</span><span class="sxs-lookup"><span data-stu-id="27c97-120">**End Time**</span></span>  
 <span data-ttu-id="27c97-121">세션의 종료 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-121">The end time of the session.</span></span> <span data-ttu-id="27c97-122">에이전트가 중지되지 않은 경우 이 필드는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="27c97-123">**기간**</span><span class="sxs-lookup"><span data-stu-id="27c97-123">**Duration**</span></span>  
 <span data-ttu-id="27c97-124">이 세션에서 배포 에이전트가 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-124">The amount of time the Distribution Agent has run in this session.</span></span> <span data-ttu-id="27c97-125">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트 세션이 종료된 경우에는 총 세션 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="27c97-126">**오류 메시지**</span><span class="sxs-lookup"><span data-stu-id="27c97-126">**Error Message**</span></span>  
 <span data-ttu-id="27c97-127">세션이 오류로 인해 종료된 경우 이 필드는 배포 에이전트가 기록한 마지막 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-127">If a session ended in an error, this field displays the last error message logged by the Distribution Agent.</span></span> <span data-ttu-id="27c97-128">세션이 오류 없이 종료된 경우에는 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="27c97-129">**동작 메시지**</span><span class="sxs-lookup"><span data-stu-id="27c97-129">**Action Message**</span></span>  
 <span data-ttu-id="27c97-130">선택한 세션 중에 배포 에이전트가 기록한 모든 정보 메시지 및 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-130">All informational messages and error messages that the Distribution Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="27c97-131">**동작 시간**</span><span class="sxs-lookup"><span data-stu-id="27c97-131">**Action Time**</span></span>  
 <span data-ttu-id="27c97-132">**동작 메시지** 열에서 설명한 동작이 수행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="27c97-133">**선택한 세션에 대한 오류 정보 또는 메시지**</span><span class="sxs-lookup"><span data-stu-id="27c97-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="27c97-134">선택한 세션의 **상태** 열에 **오류** 값이 표시되는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="27c97-135">이 텍스트 영역은 오류 발생 시 시도한 명령과 자세한 오류 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="27c97-136">오류와 관련된 추가 내용으로 연결되는 링크도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27c97-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c97-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27c97-137">See Also</span></span>  
 <span data-ttu-id="27c97-138">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="27c97-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="27c97-139">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="27c97-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="27c97-140">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="27c97-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="27c97-141">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="27c97-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
