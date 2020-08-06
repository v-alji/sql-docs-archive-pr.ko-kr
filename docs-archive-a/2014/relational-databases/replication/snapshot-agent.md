---
title: 스냅샷 에이전트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.snapshotagent.f1
helpviewer_keywords:
- Snapshot Agent dialog box
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 925f2d3841b5dded6c8504a4a05dc60e61024161
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661007"
---
# <a name="snapshot-agent"></a><span data-ttu-id="af7cd-102">스냅샷 에이전트</span><span class="sxs-lookup"><span data-stu-id="af7cd-102">Snapshot Agent</span></span>
  <span data-ttu-id="af7cd-103">**스냅샷 에이전트** 대화 상자는 상태, 기록, 정보 메시지, 모든 오류 메시지 등 스냅샷 에이전트에 대한 자세한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-103">The **Snapshot Agent** dialog box displays detailed information on the Snapshot Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="af7cd-104">옵션</span><span class="sxs-lookup"><span data-stu-id="af7cd-104">Options</span></span>  
 <span data-ttu-id="af7cd-105">**보기** 메뉴에서 보려는 스냅샷 에이전트 세션을 선택한 다음 **스냅샷 에이전트의 세션**표에서 특정 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-105">Select which Snapshot Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Snapshot Agent**.</span></span> <span data-ttu-id="af7cd-106">**선택한 세션의 동작**표에 이 세션에 대한 자세한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="af7cd-107">선택한 세션이 오류로 인해 종료될 경우 **선택한 세션에 대한 오류 정보 또는 메시지** 라는 텍스트 영역 또한 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="af7cd-108">**보기**</span><span class="sxs-lookup"><span data-stu-id="af7cd-108">**View**</span></span>  
 <span data-ttu-id="af7cd-109">확인할 스냅샷 에이전트 세션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-109">Select which Snapshot Agent sessions to view.</span></span>  
  
 <span data-ttu-id="af7cd-110">**상태**</span><span class="sxs-lookup"><span data-stu-id="af7cd-110">**Status**</span></span>  
 <span data-ttu-id="af7cd-111">스냅샷 에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-111">The status of the Snapshot Agent.</span></span> <span data-ttu-id="af7cd-112">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="af7cd-113">Error</span><span class="sxs-lookup"><span data-stu-id="af7cd-113">Error</span></span>  
  
-   <span data-ttu-id="af7cd-114">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="af7cd-114">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="af7cd-115">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="af7cd-115">Not running</span></span>  
  
-   <span data-ttu-id="af7cd-116">Completed</span><span class="sxs-lookup"><span data-stu-id="af7cd-116">Completed</span></span>  
  
 <span data-ttu-id="af7cd-117">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="af7cd-117">**Start Time**</span></span>  
 <span data-ttu-id="af7cd-118">세션의 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="af7cd-119">**종료 시간**</span><span class="sxs-lookup"><span data-stu-id="af7cd-119">**End Time**</span></span>  
 <span data-ttu-id="af7cd-120">세션의 종료 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-120">The end time of the session.</span></span> <span data-ttu-id="af7cd-121">에이전트가 중지되지 않은 경우 이 필드는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="af7cd-122">**Duration**</span><span class="sxs-lookup"><span data-stu-id="af7cd-122">**Duration**</span></span>  
 <span data-ttu-id="af7cd-123">이 세션에서 스냅샷 에이전트가 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-123">The amount of time the Snapshot Agent has run in this session.</span></span> <span data-ttu-id="af7cd-124">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트 세션이 종료된 경우에는 총 세션 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="af7cd-125">**오류 메시지**</span><span class="sxs-lookup"><span data-stu-id="af7cd-125">**Error Message**</span></span>  
 <span data-ttu-id="af7cd-126">세션이 오류로 인해 종료된 경우 이 필드는 스냅샷 에이전트가 기록한 마지막 오류 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-126">If a session ended in an error, this field displays the last error message logged by the Snapshot Agent.</span></span> <span data-ttu-id="af7cd-127">세션이 오류 없이 종료된 경우에는 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="af7cd-128">**동작 메시지**</span><span class="sxs-lookup"><span data-stu-id="af7cd-128">**Action Message**</span></span>  
 <span data-ttu-id="af7cd-129">선택한 세션 중에 스냅샷 에이전트가 기록한 모든 정보 메시지 및 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-129">All informational messages and error messages that the Snapshot Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="af7cd-130">**동작 시간**</span><span class="sxs-lookup"><span data-stu-id="af7cd-130">**Action Time**</span></span>  
 <span data-ttu-id="af7cd-131">**동작 메시지** 열에서 설명한 동작이 수행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="af7cd-132">**선택한 세션에 대한 오류 정보 또는 메시지**</span><span class="sxs-lookup"><span data-stu-id="af7cd-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="af7cd-133">선택한 세션의 **상태** 열에 **오류** 값이 표시되는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-133">Is displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="af7cd-134">이 텍스트 영역은 오류 발생 시 시도한 명령과 자세한 오류 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="af7cd-135">오류와 관련된 추가 내용으로 연결되는 링크도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af7cd-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7cd-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af7cd-136">See Also</span></span>  
 <span data-ttu-id="af7cd-137">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="af7cd-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="af7cd-138">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="af7cd-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="af7cd-139">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="af7cd-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="af7cd-140">복제 에이전트 개요</span><span class="sxs-lookup"><span data-stu-id="af7cd-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
