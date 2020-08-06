---
title: 게시 정보, 에이전트(트랜잭션 게시) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a3d50da15ea653a7911e65ad888d5997f47a3f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646339"
---
# <a name="publication-information-agents-transactional-publication"></a><span data-ttu-id="120ac-102">게시 정보, 에이전트(트랜잭션 게시)</span><span class="sxs-lookup"><span data-stu-id="120ac-102">Publication Information, Agents (Transactional Publication)</span></span>
  <span data-ttu-id="120ac-103">**에이전트** 탭은 선택한 게시에 대한 에이전트의 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-103">The **Agents** tab displays summary information on the agents for the selected publication.</span></span> <span data-ttu-id="120ac-104">스냅샷 에이전트 및 로그 판독기 에이전트에 대한 정보는 모든 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-104">Information on the Snapshot Agent and Log Reader Agent is displayed for all transactional publications.</span></span> <span data-ttu-id="120ac-105">큐 판독기 에이전트에 대한 정보는 지연 업데이트 구독이 설정된 트랜잭션 게시에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-105">Information on the Queue Reader Agent is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="120ac-106">옵션</span><span class="sxs-lookup"><span data-stu-id="120ac-106">Options</span></span>  
 <span data-ttu-id="120ac-107">에이전트 관련 태스크와 자세한 정보를 보려면 해당 에이전트에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-107">For more detailed information and tasks related to an agent, right-click the row for that agent, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="120ac-108">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-108">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="120ac-109">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-109">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="120ac-110">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-110">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="120ac-111">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-111">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="120ac-112">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-112">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="120ac-113">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-113">Filter settings are specific to each grid.</span></span> <span data-ttu-id="120ac-114">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-114">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="120ac-115">**상태**</span><span class="sxs-lookup"><span data-stu-id="120ac-115">**Status**</span></span>  
 <span data-ttu-id="120ac-116">게시와 연결된 각 복제 에이전트의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-116">The status of each replication agent associated with the publication.</span></span> <span data-ttu-id="120ac-117">다음 목록에서는 가능한 상태 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-117">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="120ac-118">오류</span><span class="sxs-lookup"><span data-stu-id="120ac-118">Error</span></span>  
  
-   <span data-ttu-id="120ac-119">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="120ac-119">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="120ac-120">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="120ac-120">Not running</span></span>  
  
-   <span data-ttu-id="120ac-121">실행 중</span><span class="sxs-lookup"><span data-stu-id="120ac-121">Running</span></span>  
  
-   <span data-ttu-id="120ac-122">Completed</span><span class="sxs-lookup"><span data-stu-id="120ac-122">Completed</span></span>  
  
 <span data-ttu-id="120ac-123">**에이전트**</span><span class="sxs-lookup"><span data-stu-id="120ac-123">**Agent**</span></span>  
 <span data-ttu-id="120ac-124">게시와 연결된 각 복제 에이전트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-124">The name of each replication agent associated with the publication.</span></span> <span data-ttu-id="120ac-125">배포 에이전트는 이 게시에 대한 구독과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-125">The Distribution Agent is associated with subscriptions to this publication.</span></span> <span data-ttu-id="120ac-126">자세한 내용은 [복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="120ac-126">For more information, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="120ac-127">**마지막 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="120ac-127">**Last Start Time**</span></span>  
 <span data-ttu-id="120ac-128">마지막으로 에이전트가 시작된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-128">The last time the agent started.</span></span>  
  
 <span data-ttu-id="120ac-129">**기간**</span><span class="sxs-lookup"><span data-stu-id="120ac-129">**Duration**</span></span>  
 <span data-ttu-id="120ac-130">에이전트가 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-130">The amount of time the agent has run.</span></span> <span data-ttu-id="120ac-131">에이전트가 현재 실행되고 있는 경우 이 시간은 경과된 시간을 나타내고 에이전트가 이전에 실행된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-131">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="120ac-132">**마지막 동작**</span><span class="sxs-lookup"><span data-stu-id="120ac-132">**Last Action**</span></span>  
 <span data-ttu-id="120ac-133">가장 최근의 에이전트 실행에서 수행된 마지막 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="120ac-133">The last action performed during the most recent run of the agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120ac-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="120ac-134">See Also</span></span>  
 <span data-ttu-id="120ac-135">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="120ac-135">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="120ac-136">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="120ac-136">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="120ac-137">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="120ac-137">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
