---
title: 차트에 데이터 범위가 여러 개 있는 계열 표시 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da3d39-278e-4760-a4b3-9932c9547cf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfe378f3fb5aa50ddf02f95b2b4be04dd1ae6ac5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647438"
---
# <a name="displaying-a-series-with-multiple-data-ranges-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="83370-102">차트에 데이터 범위가 여러 개 있는 계열 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="83370-102">Displaying a Series with Multiple Data Ranges on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="83370-103">차트는 최소 계열 값과 최대 계열 값을 사용하여 축 배율을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-103">Chart will use the minimum and maximum values of a series to calculate the axis scale.</span></span> <span data-ttu-id="83370-104">차트 계열에 두 개 이상의 데이터 범위가 포함되어 있으면 데이터 요소가 가려지고 몇 개의 데이터 요소만 차트에서 쉽게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-104">When a series on your chart contains more than one range of data, the data points can become obscured, and only a few data points to be seen easily on the chart.</span></span> <span data-ttu-id="83370-105">예를 들어 보고서에서 한 달 간의 하루 총 판매량을 표시한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-105">For example, suppose a report displays daily sales totals over a period of 30 days.</span></span>  
  
 <span data-ttu-id="83370-106">![데이터 범위가 여러 개 있는 차트](../media/rs-multipledatarangeschart.gif "데이터 범위가 여러 개 있는 차트")</span><span class="sxs-lookup"><span data-stu-id="83370-106">![Chart with multiple data ranges](../media/rs-multipledatarangeschart.gif "Chart with multiple data ranges")</span></span>  
  
 <span data-ttu-id="83370-107">한 달 동안 하루 총 판매량은 대부분 10에서 40 사이에 분포했지만</span><span class="sxs-lookup"><span data-stu-id="83370-107">For most of the month, the sales are between 10 and 40.</span></span> <span data-ttu-id="83370-108">4월 초의 판매량은 한 주 동안의 진행된 판촉 행사로 급등했습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-108">However, a one-week sales marketing campaign has caused a sudden sales increase at the beginning of April.</span></span> <span data-ttu-id="83370-109">이러한 판매 데이터 변경으로 인해 데이터 요소가 균일하지 않게 배포되어 차트에 대한 전체 가독성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="83370-109">This change in sales data produces an uneven distribution of data points that reduces the overall readability of the chart.</span></span>  
  
 <span data-ttu-id="83370-110">가독성을 개선하기 위해 다음과 같이 여러 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-110">There are different ways to improve readability:</span></span>  
  
-   <span data-ttu-id="83370-111">**배율 구분선 사용**.</span><span class="sxs-lookup"><span data-stu-id="83370-111">**Enable scale breaks**.</span></span> <span data-ttu-id="83370-112">데이터가 두 개 이상의 데이터 범위 집합을 형성하는 경우 배율 구분선을 사용하여 범위 간격을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-112">If your data forms two or more sets of data ranges, use a scale break to remove the gap between the ranges.</span></span> <span data-ttu-id="83370-113">배율 구분선은 계열에서 높은 값과 낮은 값 사이가 구분되도록 그리기 영역에 표시하는 줄무늬입니다.</span><span class="sxs-lookup"><span data-stu-id="83370-113">A scale break is a stripe drawn across the plotting area to denote a break between the high and low values of a series.</span></span>  
  
-   <span data-ttu-id="83370-114">**불필요한 값 필터링**.</span><span class="sxs-lookup"><span data-stu-id="83370-114">**Filter out unnecessary values**.</span></span> <span data-ttu-id="83370-115">차트에 표시할 중요한 데이터 범위를 가리는 데이터 요소가 있는 경우 보고서 필터를 사용하여 원하지 않는 데이터 요소를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-115">If you have data points that are obscuring the important data range to be displayed on the chart, remove the unwanted points using a report filter.</span></span> <span data-ttu-id="83370-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 차트에 필터를 추가하는 방법에 대한 자세한 내용은 [데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83370-116">For information on how to add a filter to the chart in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
-   <span data-ttu-id="83370-117">**여러 계열 비교를 위해 각 데이터 범위를 개별 계열로 그리기**.</span><span class="sxs-lookup"><span data-stu-id="83370-117">**Plot each data range as a separate series for multiple series comparison**.</span></span> <span data-ttu-id="83370-118">데이터 범위가 두 개 이상인 경우 데이터 범위를 개별 계열로 구분하십시오.</span><span class="sxs-lookup"><span data-stu-id="83370-118">If you have more than two data ranges, consider separating the data ranges into separate series.</span></span> <span data-ttu-id="83370-119">자세한 내용은 [차트의 여러 계열&#40;보고서 작성기 및 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83370-119">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-multiple-data-ranges-using-scale-breaks"></a><span data-ttu-id="83370-120">배율 구분선을 사용하여 여러 데이터 범위 표시</span><span class="sxs-lookup"><span data-stu-id="83370-120">Displaying Multiple Data Ranges Using Scale Breaks</span></span>  
 <span data-ttu-id="83370-121">배율 구분선을 사용하면 차트 위에서 선을 그릴 위치가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="83370-121">When you enable a scale break, the chart calculates where to draw a line across the chart.</span></span> <span data-ttu-id="83370-122">배율 구분선을 그리기 위해 범위 사이를 충분히 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-122">You must have sufficient separation between ranges to draw a scale break.</span></span> <span data-ttu-id="83370-123">기본적으로 차트의 25% 이상의 데이터 범위 사이가 구분되는 경우에만 배율 구분선을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-123">By default, a scale break can be added only if there is a separation between the data ranges of at least 25% of the chart.</span></span>  
  
 <span data-ttu-id="83370-124">![눈금 구분선을 포함하는 차트](../media/rs-multipledatarangeschart-scalebreak.gif "눈금 구분선을 포함하는 차트")</span><span class="sxs-lookup"><span data-stu-id="83370-124">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83370-125">차트에서 배율 구분선의 배치 위치는 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-125">You cannot specify where to place a scale break on a chart.</span></span> <span data-ttu-id="83370-126">그러나 이 항목의 뒷부분에 설명되어 있는 대로 배율 구분선을 계산하는 방식은 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-126">You can, however, modify how the scale break is calculated, described later in this topic.</span></span>  
  
 <span data-ttu-id="83370-127">데이터 범위 사이에 충분한 간격이 있어도 사용되는 배율 구분선이 표시되지 않는 경우 CollapsibleSpaceThreshold 속성을 25 미만의 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-127">If you enable a scale break but it does not appear, even though there is sufficient distance between the data ranges, you can set the CollapsibleSpaceThreshold property to a value less than 25.</span></span> <span data-ttu-id="83370-128">CollapsibleSpaceThreshold는 데이터 범위 사이에 필요한 축소 가능한 공간의 백분율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83370-128">The CollapsibleSpaceThreshold specifies the percent of collapsible space required between the data ranges.</span></span> <span data-ttu-id="83370-129">자세한 내용은 [차트에 배율 구분선 추가&#40;보고서 작성기 및 SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83370-129">For more information, see [Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="83370-130">차트에서는 차트당 최대 5개의 배율 구분선을 지원하지만 두 개 이상의 배율 구분선을 표시하면 차트를 읽을 수 없게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-130">Charts support up to five scale breaks per chart; however, displaying more than one scale break can cause the chart to become unreadable.</span></span> <span data-ttu-id="83370-131">데이터 범위가 두 개 이상인 경우 이 데이터를 표시하는 다른 방법을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="83370-131">If you have more than two data ranges, consider using a different method for displaying this data.</span></span> <span data-ttu-id="83370-132">자세한 내용은 [차트의 여러 계열&#40;보고서 작성기 및 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83370-132">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="unsupported-scale-break-scenarios"></a><span data-ttu-id="83370-133">지원되지 않는 배율 구분선 시나리오</span><span class="sxs-lookup"><span data-stu-id="83370-133">Unsupported Scale Break Scenarios</span></span>  
 <span data-ttu-id="83370-134">다음과 같은 차트 시나리오에서는 배율 구분선이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-134">Scale breaks are not supported in the following chart scenarios:</span></span>  
  
-   <span data-ttu-id="83370-135">3차원 차트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="83370-135">The chart is 3-D enabled.</span></span>  
  
-   <span data-ttu-id="83370-136">로그 값 축이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-136">A logarithmic value axis has been specified.</span></span>  
  
-   <span data-ttu-id="83370-137">값 축 최소 또는 최대가 명시적으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83370-137">The value axis minimum or maximum has been explicitly set.</span></span>  
  
-   <span data-ttu-id="83370-138">이 차트 종류가 극좌표형, 방사형, 원형, 도넛형, 깔때기형, 피라미드형 또는 모든 누적 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="83370-138">The chart type is polar, radar, pie, doughnut, funnel, pyramid, or any stacked chart.</span></span>  
  
 <span data-ttu-id="83370-139">배율 구분선이 있는 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="83370-139">An example of chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="83370-140">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83370-140">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83370-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83370-141">See Also</span></span>  
 <span data-ttu-id="83370-142">[차트의 여러 계열 &#40;보고서 작성기 및 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83370-142">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="83370-143">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83370-143">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="83370-144">[차트 &#40;보고서 작성기 및 SSRS의 3D, 빗면 및 기타 효과&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="83370-144">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="83370-145">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83370-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="83370-146">[축 속성 대화 상자, 축 옵션 보고서 작성기 및 SSRS &#40;&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="83370-146">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="83370-147">원형 차트에서 작은 조각 수집&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="83370-147">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
