---
title: "' 게시자 정보 ' 대화 상자 SQL Server 복제 | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3797ae4f9fe8f42b4abec715c63bc627c2a62cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730467"
---
# <a name="sql-server-replication-publisher-information-dialog-box"></a><span data-ttu-id="a75be-102">' 게시자 정보 ' 대화 상자 SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="a75be-102">SQL Server Replication 'Publisher Information' dialog box</span></span>
  <span data-ttu-id="a75be-103">**게시** 탭은 왼쪽 창에서 선택한 게시자에서의 모든 게시에 대한 요약 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-103">The **Publications** tab provides summary information for all publications at the Publisher selected in the left pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a75be-104">옵션</span><span class="sxs-lookup"><span data-stu-id="a75be-104">Options</span></span>  
 <span data-ttu-id="a75be-105">표에서 데이터를 표시하는 방식을 변경하려면 표를 마우스 오른쪽 단추로 클릭한 후 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-105">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="a75be-106">**정렬**: **열 정렬** 대화 상자에서 한 개 이상의 열에 대해 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-106">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="a75be-107">**표시할 열 선택**: **열 선택** 대화 상자에서 표시할 열 및 해당 열이 표시되는 순서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-107">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="a75be-108">**필터**: **필터 설정** 대화 상자의 열 값에 따라 표의 행을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-108">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="a75be-109">**필터 지우기**: 표에 대한 모든 필터 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-109">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="a75be-110">필터 설정은 각 표에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-110">Filter settings are specific to each grid.</span></span> <span data-ttu-id="a75be-111">열 선택 및 정렬은 각 게시자에 대한 게시 표와 같이 동일한 유형의 모든 표에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-111">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="a75be-112">**상태**</span><span class="sxs-lookup"><span data-stu-id="a75be-112">**Status**</span></span>  
 <span data-ttu-id="a75be-113">해당 구독의 가장 높은 우선 순위 상태에 의해 결정되는 각 게시 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-113">The status of each publication, which is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="a75be-114">기본적으로 게시 정보가 포함된 표는 **상태** 열을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-114">By default, the grid containing publication information is sorted by the **Status** column.</span></span> <span data-ttu-id="a75be-115">다음 목록에서는 가능한 상태 값 및 값 정렬 순서를 보여 줍니다. 예를 들어 오류는 항상 표의 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-115">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid):</span></span>  
  
-   <span data-ttu-id="a75be-116">Error</span><span class="sxs-lookup"><span data-stu-id="a75be-116">Error</span></span>  
  
-   <span data-ttu-id="a75be-117">성능 심각</span><span class="sxs-lookup"><span data-stu-id="a75be-117">Performance critical</span></span>  
  
-   <span data-ttu-id="a75be-118">실패한 명령 다시 시도 중</span><span class="sxs-lookup"><span data-stu-id="a75be-118">Retrying failed command</span></span>  
  
-   <span data-ttu-id="a75be-119">확인</span><span class="sxs-lookup"><span data-stu-id="a75be-119">OK</span></span>  
  
 <span data-ttu-id="a75be-120">상태 값 **성능 심각** 은 트랜잭션 구독과 병합 구독에 적용되며 트랜잭션 구독의 경우 임계값이 설정된 경우에만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-120">The status value **Performance critical** is relevant for transactional subscriptions and merge subscriptions; for transactional subscriptions, it can be displayed only if a threshold is set.</span></span> <span data-ttu-id="a75be-121">성능 측정 및 임계값 설정에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) 및 [복제 모니터에 임계값 및 경고 설정](monitor/set-thresholds-and-warnings-in-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a75be-121">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="a75be-122">**게시**</span><span class="sxs-lookup"><span data-stu-id="a75be-122">**Publication**</span></span>  
 <span data-ttu-id="a75be-123">*PublicationDatabaseName: PublicationName*형식의 각 게시의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-123">The name of each publication, in the form *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="a75be-124">**구독**</span><span class="sxs-lookup"><span data-stu-id="a75be-124">**Subscriptions**</span></span>  
 <span data-ttu-id="a75be-125">각 게시에 대한 구독 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-125">The number of subscriptions for each publication.</span></span>  
  
 <span data-ttu-id="a75be-126">**동기화 중**</span><span class="sxs-lookup"><span data-stu-id="a75be-126">**Synchronizing**</span></span>  
 <span data-ttu-id="a75be-127">각 게시에 대해 현재 동기화 중인 구독 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-127">The number of subscriptions for each publication that are currently synchronizing:</span></span>  
  
-   <span data-ttu-id="a75be-128">트랜잭션 복제에서 "동기화 중"은 배포 에이전트가 실행 중이지만 데이터를 반드시 복제할 필요가 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-128">For transactional replication, "synchronizing" means that the Distribution Agent is running, but data is not necessarily being replicated.</span></span>  
  
-   <span data-ttu-id="a75be-129">병합 복제에서 "동기화 중"은 병합 에이전트가 실행 중이며 데이터가 현재 복제되고 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-129">For merge replication, "synchronizing" means that the Merge Agent is running and that data is currently being replicated.</span></span>  
  
-   <span data-ttu-id="a75be-130">스냅샷 복제에서 "동기화 중"은 배포 에이전트가 실행 중이며 데이터가 현재 복제되고 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-130">For snapshot replication, "synchronizing" means that the Distribution Agent is running and that data is currently being replicated.</span></span>  
  
 <span data-ttu-id="a75be-131">**현재 평균 성능** 및 **현재 가장 낮은 성능**</span><span class="sxs-lookup"><span data-stu-id="a75be-131">**Current Average Performance** and **Current Worst Performance**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a75be-132">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-132">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="a75be-133">게시에 대한 모든 구독의 평균 성능 등급과 가장 낮은 성능 등급입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-133">The average performance rating and the worst performance rating, respectively, for all subscriptions to a publication.</span></span> <span data-ttu-id="a75be-134">등급은 복제 모니터에서 측정한 가장 최근 측정값을 기반으로 하며 이전 구독 성능을 반영하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-134">Ratings are based on the most recent measurements taken by Replication Monitor and do not reflect the performance of a subscription over time.</span></span>  
  
 <span data-ttu-id="a75be-135">트랜잭션 복제의 경우 복제 모니터는 성능 임계값이 정의된 게시에 대해서만 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-135">For transactional replication, Replication Monitor displays a value only for publications that have performance thresholds defined.</span></span> <span data-ttu-id="a75be-136">게시에 대해 성능 임계값을 정의하지 않으면 이 열에 **사용 안 함**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-136">If performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="a75be-137">병합 복제의 경우 복제 모니터는 같은 유형의 연결(전화 접속 또는 LAN)별로 50개 이상의 변경 사항을 5번 동기화한 후에 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-137">For merge replication, Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection (dial-up or LAN).</span></span> <span data-ttu-id="a75be-138">50개 이상의 변경 사항에 대해 동기화가 5번 미만으로 수행되었거나 가장 최근에 동기화가 수행된 변경 사항이 50개 미만인 경우에는 이 열이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-138">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
 <span data-ttu-id="a75be-139">성능 등급은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a75be-139">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="a75be-140">최고</span><span class="sxs-lookup"><span data-stu-id="a75be-140">Excellent</span></span>  
  
-   <span data-ttu-id="a75be-141">좋음</span><span class="sxs-lookup"><span data-stu-id="a75be-141">Good</span></span>  
  
-   <span data-ttu-id="a75be-142">보통</span><span class="sxs-lookup"><span data-stu-id="a75be-142">Fair</span></span>  
  
-   <span data-ttu-id="a75be-143">나쁨</span><span class="sxs-lookup"><span data-stu-id="a75be-143">Poor</span></span>  
  
-   <span data-ttu-id="a75be-144">위험</span><span class="sxs-lookup"><span data-stu-id="a75be-144">Critical</span></span>  
  
 <span data-ttu-id="a75be-145">성능 등급 정의 방법 및 성능 임계값 설정 방법은 [복제 모니터로 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a75be-145">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75be-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a75be-146">See Also</span></span>  
 <span data-ttu-id="a75be-147">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a75be-147">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="a75be-148">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a75be-148">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="a75be-149">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="a75be-149">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
