---
title: 게시 정보, 모든 구독(트랜잭션 게시) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.tran.f1
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccc34bbe0933f4558478bd1d8276898219016e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647623"
---
# <a name="publication-information-all-subscriptions-transactional-publication"></a><span data-ttu-id="68089-102">게시 정보, 모든 구독(트랜잭션 게시)</span><span class="sxs-lookup"><span data-stu-id="68089-102">Publication Information, All Subscriptions (Transactional Publication)</span></span>
  <span data-ttu-id="68089-103">**모든 구독** 탭은 선택한 트랜잭션 게시의 모든 구독에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-103">The **All Subscriptions** tab displays information on all subscriptions to the selected transactional publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="68089-104">옵션</span><span class="sxs-lookup"><span data-stu-id="68089-104">Options</span></span>  
 <span data-ttu-id="68089-105">자세한 내용 및 구독과 관련된 태스크를 보려면 해당 구독에 대한 행을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="68089-106">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="68089-107">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="68089-108">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="68089-109">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="68089-110">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="68089-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="68089-111">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="68089-112">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="68089-113">**표시**</span><span class="sxs-lookup"><span data-stu-id="68089-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="68089-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="68089-115">선택한 구독 유형에 대해 표시할 구독 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="68089-116">예를 들어 오류가 있는 구독만 표시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68089-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="68089-117">**상태**</span><span class="sxs-lookup"><span data-stu-id="68089-117">**Status**</span></span>  
 <span data-ttu-id="68089-118">배포 에이전트 또는 로그 판독기 에이전트의 상태로 파악할 수 있는 각 구독의 상태입니다. 우선 순위가 높은 상태가 표시되며 지연 업데이트 구독을 사용하는 경우 큐 판독기 에이전트로 상태를 파악할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68089-118">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="68089-119">기본적으로 구독 정보가 들어 있는 표는 **상태** 열을 기준으로 정렬한 다음 상태가 같은 구독을 **성능** 열을 기준으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="68089-120">다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="68089-121">오류</span><span class="sxs-lookup"><span data-stu-id="68089-121">Error</span></span>  
  
-   <span data-ttu-id="68089-122">성능 심각([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)</span><span class="sxs-lookup"><span data-stu-id="68089-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="68089-123">곧 만료됨/만료됨([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전만 해당)</span><span class="sxs-lookup"><span data-stu-id="68089-123">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="68089-124">초기화되지 않은 구독([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당)</span><span class="sxs-lookup"><span data-stu-id="68089-124">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="68089-125">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="68089-125">Retrying failed command</span></span>  
  
-   <span data-ttu-id="68089-126">실행 중이 아님</span><span class="sxs-lookup"><span data-stu-id="68089-126">Not Running</span></span>  
  
-   <span data-ttu-id="68089-127">실행 중</span><span class="sxs-lookup"><span data-stu-id="68089-127">Running</span></span>  
  
 <span data-ttu-id="68089-128">정렬 순서는 지정한 구독의 상태가 두 가지 이상일 경우에 표시할 값도 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-128">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="68089-129">예를 들어 구독에 오류가 있고 곧 만료될 예정이면 **상태** 열에 **오류**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-129">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="68089-130">**성능 심각**, **곧 만료됨/만료됨**및 **초기화되지 않은 구독** 상태 값은 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="68089-130">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="68089-131">경고를 표시할 때 **상태** 열은 에이전트가 실행 중인지 여부도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-131">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="68089-132">예를 들어 상태가 **실행 중, 성능 심각**과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68089-132">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="68089-133">**성능 심각** 및 **곧 만료됨/만료됨** 상태 값은 임계값이 설정된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-133">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="68089-134">성능 측정 및 임계값 설정에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) 및 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68089-134">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="68089-135">**구독**</span><span class="sxs-lookup"><span data-stu-id="68089-135">**Subscription**</span></span>  
 <span data-ttu-id="68089-136">각 구독의 이름으로 *SubscriberName: SubscriptionDatabaseName*형식입니다.</span><span class="sxs-lookup"><span data-stu-id="68089-136">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="68089-137">**성능**</span><span class="sxs-lookup"><span data-stu-id="68089-137">**Performance**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="68089-138">이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-138">and later versions only.</span></span> <span data-ttu-id="68089-139">각 구독의 성능 등급은 복제 모니터에서 측정한 가장 최근의 측정값을 기반으로 하며 이전 성능은 반영하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68089-139">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="68089-140">성능 임계값이 정의된 게시의 구독에 대해 성능을 측정합니다. 게시에 대해 성능 임계값을 정의하지 않으면 이 열에 **사용 안 함**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-140">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="68089-141">성능 등급은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="68089-141">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="68089-142">우수</span><span class="sxs-lookup"><span data-stu-id="68089-142">Excellent</span></span>  
  
-   <span data-ttu-id="68089-143">좋음</span><span class="sxs-lookup"><span data-stu-id="68089-143">Good</span></span>  
  
-   <span data-ttu-id="68089-144">보통</span><span class="sxs-lookup"><span data-stu-id="68089-144">Fair</span></span>  
  
-   <span data-ttu-id="68089-145">나쁨</span><span class="sxs-lookup"><span data-stu-id="68089-145">Poor</span></span>  
  
-   <span data-ttu-id="68089-146">위험</span><span class="sxs-lookup"><span data-stu-id="68089-146">Critical</span></span>  
  
 <span data-ttu-id="68089-147">성능 상태가 심각하면 **상태** 열에 **성능 심각** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-147">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="68089-148">성능 등급 정의 방법 및 성능 임계값 설정 방법에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68089-148">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="68089-149">**대기 시간**</span><span class="sxs-lookup"><span data-stu-id="68089-149">**Latency**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="68089-150">이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="68089-150">and later versions only.</span></span> <span data-ttu-id="68089-151">게시자에서 트랜잭션이 커밋되는 시점과 구독자에서 해당 트랜잭션이 커밋되는 시점 간의 평균 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="68089-151">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="68089-152">표시되는 대기 시간은 복제 모니터에서 측정한 가장 최근의 측정값을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="68089-152">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="68089-153">대기 시간 측정에 대한 자세한 내용은 [트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68089-153">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68089-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68089-154">See Also</span></span>  
 <span data-ttu-id="68089-155">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="68089-155">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="68089-156">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="68089-156">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="68089-157">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="68089-157">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
