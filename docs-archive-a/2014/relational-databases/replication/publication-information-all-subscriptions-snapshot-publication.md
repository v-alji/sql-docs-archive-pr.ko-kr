---
title: 게시 정보, 모든 구독(스냅샷 게시) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75eb85adae46481ddd4360f095c00060af5677fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651651"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a><span data-ttu-id="53fdf-102">게시 정보, 모든 구독(스냅샷 게시)</span><span class="sxs-lookup"><span data-stu-id="53fdf-102">Publication Information, All Subscriptions (Snapshot Publication)</span></span>
  <span data-ttu-id="53fdf-103">**모든 구독** 탭은 선택한 스냅샷 게시의 모든 구독에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-103">The **All Subscriptions** tab displays information on all subscriptions to the selected snapshot publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="53fdf-104">옵션</span><span class="sxs-lookup"><span data-stu-id="53fdf-104">Options</span></span>  
 <span data-ttu-id="53fdf-105">자세한 내용 및 구독과 관련된 태스크를 보려면 해당 구독에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="53fdf-106">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="53fdf-107">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="53fdf-108">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="53fdf-109">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="53fdf-110">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="53fdf-111">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="53fdf-112">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="53fdf-113">**표시**</span><span class="sxs-lookup"><span data-stu-id="53fdf-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="53fdf-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="53fdf-115">선택한 구독 유형에 대해 표시할 구독 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="53fdf-116">예를 들어 오류가 있는 구독만 표시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="53fdf-117">**상태**</span><span class="sxs-lookup"><span data-stu-id="53fdf-117">**Status**</span></span>  
 <span data-ttu-id="53fdf-118">스냅샷 에이전트 또는 배포 에이전트의 상태에 따라 결정되는 각 구독의 상태입니다. 우선 순위가 높은 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-118">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="53fdf-119">기본적으로 구독 정보가 포함된 표는 **상태** 열을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-119">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="53fdf-120">다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="53fdf-121">오류</span><span class="sxs-lookup"><span data-stu-id="53fdf-121">Error</span></span>  
  
-   <span data-ttu-id="53fdf-122">곧 만료됨/만료됨([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)</span><span class="sxs-lookup"><span data-stu-id="53fdf-122">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="53fdf-123">초기화되지 않은 구독([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)</span><span class="sxs-lookup"><span data-stu-id="53fdf-123">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="53fdf-124">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="53fdf-124">Retrying failed command</span></span>  
  
-   <span data-ttu-id="53fdf-125">동기화 중</span><span class="sxs-lookup"><span data-stu-id="53fdf-125">Synchronizing</span></span>  
  
-   <span data-ttu-id="53fdf-126">비동기화 중</span><span class="sxs-lookup"><span data-stu-id="53fdf-126">Not synchronizing</span></span>  
  
 <span data-ttu-id="53fdf-127">정렬 순서는 지정한 구독의 상태가 두 가지 이상일 경우에 표시할 값도 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-127">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="53fdf-128">예를 들어 구독에 오류가 있고 곧 만료될 예정이면 **상태** 열에 **오류**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-128">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="53fdf-129">**곧 만료됨/만료됨** 및 **초기화되지 않은 구독** 상태 값은 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-129">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="53fdf-130">경고를 표시할 때 **상태** 열은 에이전트가 실행 중인지 여부도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-130">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="53fdf-131">예를 들어 상태가 **실행 중, 곧 만료됨/만료됨**과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-131">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="53fdf-132">**곧 만료됨/만료됨** 상태 값은 임계값을 설정한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-132">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="53fdf-133">임계값 설정에 대한 자세한 내용은 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53fdf-133">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="53fdf-134">**구독**</span><span class="sxs-lookup"><span data-stu-id="53fdf-134">**Subscription**</span></span>  
 <span data-ttu-id="53fdf-135">각 구독의 이름으로 *SubscriberName: SubscriptionDatabaseName*형식입니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-135">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="53fdf-136">**마지막 동기화**</span><span class="sxs-lookup"><span data-stu-id="53fdf-136">**Last Synchronization**</span></span>  
 <span data-ttu-id="53fdf-137">배포 에이전트가 마지막으로 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-137">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="53fdf-138">동기화가 진행 중인 경우 **진행 중** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53fdf-138">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fdf-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53fdf-139">See Also</span></span>  
 <span data-ttu-id="53fdf-140">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="53fdf-140">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="53fdf-141">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="53fdf-141">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="53fdf-142">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="53fdf-142">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
