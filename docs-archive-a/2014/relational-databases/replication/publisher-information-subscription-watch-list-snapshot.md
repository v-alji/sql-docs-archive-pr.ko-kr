---
title: 게시자 정보, 구독 조사 목록 (스냅숏 게시, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732575"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="40885-102">게시자 정보, 구독 조사 목록(스냅샷 게시, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="40885-102">Publisher Information, Subscription Watch List (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="40885-103">**구독 조사 목록** 탭은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 실행하는 배포자에 대해 사용할 수 있으며 선택한 게시자에서 사용 가능한 모든 게시의 구독 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="40885-104">구독 목록을 필터링하여 오류, 경고 및 성능이 저조한 구독을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40885-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="40885-105">이 탭에서는 관리자가 게시자에서의 모든 복제 작업을 모니터링할 수 있는 단일 위치를 제공합니다. 복제 모니터는 선택한 복제 유형과 **표시** 드롭다운 목록 상자에서 선택한 옵션에 기반하여 주의가 필요한 모든 구독을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="40885-106">이 탭에 표시되는 항목은 현재 상태와 성능에 기반하기 때문에 현재 **표시** 목록 상자의 옵션과 일치하는 구독만 이 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40885-107">옵션</span><span class="sxs-lookup"><span data-stu-id="40885-107">Options</span></span>  
 <span data-ttu-id="40885-108">자세한 내용 및 구독과 관련된 태스크를 보려면 해당 구독에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="40885-109">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="40885-110">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="40885-111">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="40885-112">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="40885-113">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="40885-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="40885-114">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="40885-115">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="40885-116">**스냅샷 구독 표시**</span><span class="sxs-lookup"><span data-stu-id="40885-116">**Show Snapshot Subscriptions**</span></span>  
 <span data-ttu-id="40885-117">선택한 게시자에 대해 표시할 구독 유형(트랜잭션, 스냅샷 또는 병합)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="40885-118">**표시**</span><span class="sxs-lookup"><span data-stu-id="40885-118">**Show**</span></span>  
 <span data-ttu-id="40885-119">선택한 구독 유형에 대해 표시할 구독 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="40885-120">예를 들어 오류가 있는 구독만 표시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40885-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="40885-121">**상태**</span><span class="sxs-lookup"><span data-stu-id="40885-121">**Status**</span></span>  
 <span data-ttu-id="40885-122">스냅샷 에이전트 또는 배포 에이전트의 상태에 따라 결정되는 각 구독의 상태입니다. 우선 순위가 높은 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-122">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="40885-123">기본적으로 구독 정보가 포함된 표는 **상태** 열을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-123">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="40885-124">다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="40885-125">오류</span><span class="sxs-lookup"><span data-stu-id="40885-125">Error</span></span>  
  
-   <span data-ttu-id="40885-126">곧 만료됨/만료됨</span><span class="sxs-lookup"><span data-stu-id="40885-126">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="40885-127">초기화되지 않은 구독</span><span class="sxs-lookup"><span data-stu-id="40885-127">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="40885-128">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="40885-128">Retrying failed command</span></span>  
  
-   <span data-ttu-id="40885-129">동기화 중</span><span class="sxs-lookup"><span data-stu-id="40885-129">Synchronizing</span></span>  
  
-   <span data-ttu-id="40885-130">비동기화 중</span><span class="sxs-lookup"><span data-stu-id="40885-130">Not synchronizing</span></span>  
  
 <span data-ttu-id="40885-131">정렬 순서는 지정한 구독의 상태가 두 가지 이상일 경우에 표시할 값도 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-131">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="40885-132">예를 들어 구독에 오류가 있고 곧 만료될 예정이면 **상태** 열에 **오류**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-132">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="40885-133">**곧 만료됨/만료됨** 및 **초기화되지 않은 구독** 상태 값은 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="40885-133">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="40885-134">경고를 표시할 때 **상태** 열은 에이전트가 실행 중인지 여부도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="40885-134">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="40885-135">예를 들어 상태가 **실행 중, 곧 만료됨/만료됨**과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40885-135">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="40885-136">**곧 만료됨/만료됨** 상태 값은 임계값을 설정한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-136">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="40885-137">임계값 설정에 대한 자세한 내용은 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40885-137">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="40885-138">**구독**</span><span class="sxs-lookup"><span data-stu-id="40885-138">**Subscription**</span></span>  
 <span data-ttu-id="40885-139">각 구독의 이름으로 *SubscriberName: SubscriptionDatabaseName*형식입니다.</span><span class="sxs-lookup"><span data-stu-id="40885-139">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="40885-140">**게시**</span><span class="sxs-lookup"><span data-stu-id="40885-140">**Publication**</span></span>  
 <span data-ttu-id="40885-141">구독을 동기화할 게시의 이름이며 *PublicationDatabaseName: PublicationName*형식입니다.</span><span class="sxs-lookup"><span data-stu-id="40885-141">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="40885-142">**마지막 동기화**</span><span class="sxs-lookup"><span data-stu-id="40885-142">**Last Synchronization**</span></span>  
 <span data-ttu-id="40885-143">배포 에이전트가 마지막으로 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="40885-143">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="40885-144">동기화가 진행 중인 경우 **진행 중** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="40885-144">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40885-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40885-145">See Also</span></span>  
 <span data-ttu-id="40885-146">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="40885-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="40885-147">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="40885-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="40885-148">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="40885-148">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
