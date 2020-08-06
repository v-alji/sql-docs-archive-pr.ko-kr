---
title: 게시 정보, 모든 구독(병합 게시) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251e4c6e2e2adc60c838c7875d5d7d99aee64b54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740823"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a><span data-ttu-id="70762-102">게시 정보, 모든 구독(병합 게시)</span><span class="sxs-lookup"><span data-stu-id="70762-102">Publication Information, All Subscriptions (Merge Publication)</span></span>
  <span data-ttu-id="70762-103">**모든 구독** 탭은 선택한 병합 게시에 대한 모든 구독 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-103">The **All Subscriptions** tab displays information on all subscriptions to the selected merge publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70762-104">옵션</span><span class="sxs-lookup"><span data-stu-id="70762-104">Options</span></span>  
 <span data-ttu-id="70762-105">자세한 내용 및 구독과 관련된 태스크를 보려면 해당 구독에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="70762-106">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="70762-107">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="70762-108">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="70762-109">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="70762-110">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="70762-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="70762-111">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="70762-112">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="70762-113">**표시**</span><span class="sxs-lookup"><span data-stu-id="70762-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="70762-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="70762-115">선택한 구독 유형에 대해 표시할 구독 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="70762-116">예를 들어 오류가 있는 구독만 표시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="70762-117">**상태**</span><span class="sxs-lookup"><span data-stu-id="70762-117">**Status**</span></span>  
 <span data-ttu-id="70762-118">병합 에이전트의 상태에 의해 결정되는 각 구독의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-118">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="70762-119">기본적으로 구독 정보가 들어 있는 표는 **상태** 열을 기준으로 정렬한 다음 상태가 같은 구독을 **성능** 열을 기준으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="70762-120">다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="70762-121">오류</span><span class="sxs-lookup"><span data-stu-id="70762-121">Error</span></span>  
  
-   <span data-ttu-id="70762-122">성능 심각([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)</span><span class="sxs-lookup"><span data-stu-id="70762-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="70762-123">장기 실행 트랜잭션 병합([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)</span><span class="sxs-lookup"><span data-stu-id="70762-123">Long-running merge ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="70762-124">곧 만료됨/만료됨([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)</span><span class="sxs-lookup"><span data-stu-id="70762-124">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="70762-125">초기화되지 않은 구독([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)</span><span class="sxs-lookup"><span data-stu-id="70762-125">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="70762-126">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="70762-126">Retrying failed command</span></span>  
  
-   <span data-ttu-id="70762-127">동기화 중</span><span class="sxs-lookup"><span data-stu-id="70762-127">Synchronizing</span></span>  
  
-   <span data-ttu-id="70762-128">비동기화 중</span><span class="sxs-lookup"><span data-stu-id="70762-128">Not synchronizing</span></span>  
  
 <span data-ttu-id="70762-129">정렬 순서는 지정한 구독의 상태가 두 가지 이상일 경우에 표시할 값도 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-129">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="70762-130">예를 들어 구독에 오류가 있고 곧 만료될 예정이면 **상태** 열에 **오류**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-130">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="70762-131">**성능 심각**, **장기 실행 트랜잭션 병합**, **곧 만료됨/만료됨**및 **초기화되지 않은 구독** 상태 값은 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-131">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="70762-132">경고를 표시할 때 **상태** 열은 에이전트가 동기화 중인지 여부도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-132">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="70762-133">예를 들어 상태가 **동기화 중, 성능 심각**과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-133">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="70762-134">**곧 만료됨/만료됨** 및 **장기 실행 트랜잭션 병합** 상태 값은 임계값이 설정된 경우에만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-134">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="70762-135">상태 값 **성능 심각** 은 동일한 연결 유형(전화 접속 또는 LAN)으로 구독을 5회 동기화한 후에만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-135">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="70762-136">성능 측정 및 임계값 설정에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) 및 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70762-136">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="70762-137">**구독**</span><span class="sxs-lookup"><span data-stu-id="70762-137">**Subscription**</span></span>  
 <span data-ttu-id="70762-138">각 구독의 이름으로, 형식은*SubscriberName: SubscriptionDatabaseName*입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-138">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="70762-139">**식별 이름**</span><span class="sxs-lookup"><span data-stu-id="70762-139">**Friendly Name**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="70762-140">이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-140">and later versions only.</span></span> <span data-ttu-id="70762-141">각 구독에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-141">The description of each subscription.</span></span> <span data-ttu-id="70762-142">설명은 **구독 속성** 대화 상자에서 입력하거나 **@description** 또는 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) 의 [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-142">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="70762-143">설명을 구독의 "이름" 또는 애칭으로 사용하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-143">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="70762-144">**성능**</span><span class="sxs-lookup"><span data-stu-id="70762-144">**Performance**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="70762-145">이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-145">and later versions only.</span></span> <span data-ttu-id="70762-146">복제 모니터에서 측정한 가장 최근의 배달 속도 측정값을 기반으로 하는 각 구독의 성능 등급입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-146">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="70762-147">등급은 개별 구독 성능과 게시에 대한 구독(연결 유형이 전화 접속 또는 LAN 등으로 동일한 구독)의 평균 기록 성능을 비교하여 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-147">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="70762-148">복제 모니터는 같은 유형의 연결별로 50개 이상의 변경 사항을 5번 동기화한 후에 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-148">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="70762-149">50개 이상의 변경 사항에 대해 동기화가 5번 미만으로 수행되었거나 가장 최근에 동기화가 수행된 변경 사항이 50개 미만인 경우에는 이 열이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-149">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70762-150">성능은 **연결** 열에 표시된 연결 유형을 기준으로 하기 때문에 느린 연결을 통해 첫 번째 구독을 동기화할 경우 배달 속도가 느린 구독이 다른 구독보다 성능 등급이 높게 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-150">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="70762-151">성능 등급은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-151">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="70762-152">우수</span><span class="sxs-lookup"><span data-stu-id="70762-152">Excellent</span></span>  
  
-   <span data-ttu-id="70762-153">좋음</span><span class="sxs-lookup"><span data-stu-id="70762-153">Good</span></span>  
  
-   <span data-ttu-id="70762-154">보통</span><span class="sxs-lookup"><span data-stu-id="70762-154">Fair</span></span>  
  
-   <span data-ttu-id="70762-155">나쁨</span><span class="sxs-lookup"><span data-stu-id="70762-155">Poor</span></span>  
  
 <span data-ttu-id="70762-156">성능 등급 정의 방법 및 성능 임계값 설정 방법에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70762-156">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="70762-157">**배달 속도**</span><span class="sxs-lookup"><span data-stu-id="70762-157">**Delivery Rate**</span></span>  
 <span data-ttu-id="70762-158">병합 에이전트에서 처리하는 초당 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-158">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="70762-159">**마지막 동기화**</span><span class="sxs-lookup"><span data-stu-id="70762-159">**Last Synchronization**</span></span>  
 <span data-ttu-id="70762-160">병합 에이전트가 마지막으로 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-160">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="70762-161">마지막 동기화 중에 변경 내용이 처리될 수도 있고 처리되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70762-161">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="70762-162">동기화가 진행 중이면 백분율로 진행 상황을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70762-162">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="70762-163">**기간**</span><span class="sxs-lookup"><span data-stu-id="70762-163">**Duration**</span></span>  
 <span data-ttu-id="70762-164">마지막 동기화 중에 병합 에이전트가 실행된 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-164">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="70762-165">병합 에이전트가 현재 동기화 중이면 이 시간은 경과된 시간을 나타내고 병합 에이전트가 이전에 동기화된 경우에는 총 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70762-165">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="70762-166">**연결**</span><span class="sxs-lookup"><span data-stu-id="70762-166">**Connection**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="70762-167">이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-167">and later versions only.</span></span> <span data-ttu-id="70762-168">구독자와 게시자 간의 연결 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-168">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="70762-169">가능한 값은 **LAN**, **전화 접속**및 **인터넷**입니다.</span><span class="sxs-lookup"><span data-stu-id="70762-169">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="70762-170">**인터넷** 값은 구독에서 웹 동기화를 사용하는 경우에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70762-170">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70762-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70762-171">See Also</span></span>  
 <span data-ttu-id="70762-172">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="70762-172">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="70762-173">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="70762-173">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="70762-174">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="70762-174">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="70762-175">병합 복제에 대한 웹 동기화</span><span class="sxs-lookup"><span data-stu-id="70762-175">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
