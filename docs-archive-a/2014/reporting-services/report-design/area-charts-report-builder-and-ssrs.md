---
title: 영역형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f401efa0abd5eac8ab39e511bc6b16a4f381ebdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733643"
---
# <a name="area-charts-report-builder-and-ssrs"></a><span data-ttu-id="ad7cc-102">영역형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ad7cc-102">Area Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ad7cc-103">영역형 차트에서 계열은 선으로 연결된 일련의 점(선 아래 영역이 모두 채워짐)으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-103">An area chart displays a series as a set of points connected by a line, with all the area filled in below the line.</span></span> <span data-ttu-id="ad7cc-104">영역형 차트에 데이터를 추가하는 방법에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-104">For more information on how to add data to an area chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ad7cc-105">다음 그림에서는 누적 영역형 차트의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-105">The following illustration shows an example of a stacked area chart.</span></span> <span data-ttu-id="ad7cc-106">누적 영역형 차트에서는 모든 계열의 합계를 비롯하여 각 계열이 합계에서 차지하는 비율을 표시할 수 있으므로 이 차트에는 이 예에서와 같은 데이터를 표시하는 것이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-106">The data is well suited for display on a stacked area chart because the chart can display totals for all series as well as the proportion that each series contributes to the total.</span></span>  
  
 <span data-ttu-id="ad7cc-107">![영역형 차트](../media/areachart.gif "영역형 차트")</span><span class="sxs-lookup"><span data-stu-id="ad7cc-107">![Area chart](../media/areachart.gif "Area chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="ad7cc-108">변형</span><span class="sxs-lookup"><span data-stu-id="ad7cc-108">Variations</span></span>  
  
-   <span data-ttu-id="ad7cc-109">**누적 영역형**.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-109">**Stacked area**.</span></span> <span data-ttu-id="ad7cc-110">여러 계열이 세로로 누적되는 영역형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-110">An area chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="ad7cc-111">차트의 계열이 한 개뿐이면 누적 영역형 차트가 영역형 차트와 같은 모양으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-111">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="ad7cc-112">**100% 기준 누적 영역형**.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-112">**Percent stacked area**.</span></span> <span data-ttu-id="ad7cc-113">전체 차트 영역에 꼭 맞도록 여러 계열을 세로로 누적하여 표시하는 영역형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-113">An area chart where multiple series are stacked vertically to fit the entire chart area.</span></span> <span data-ttu-id="ad7cc-114">차트의 계열이 한 개뿐이면 누적 영역형 차트가 영역형 차트와 같은 모양으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-114">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="ad7cc-115">**곡선 영역형**.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-115">**Smooth area**.</span></span> <span data-ttu-id="ad7cc-116">일반적인 직선 대신 매끄러운 곡선을 사용하여 데이터 요소를 연결하는 영역형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-116">An area chart where the data points are connected by a smooth line instead of a regular line.</span></span> <span data-ttu-id="ad7cc-117">개별 데이터 요소의 값을 표시하는 것보다 추세를 표시하는 것이 더 중요한 경우 영역형 차트 대신 곡선 영역형 차트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-117">Use a smooth area chart instead of an area chart when you are more concerned with displaying trends than with displaying the values of individual data points.</span></span>  
  
## <a name="data-considerations-for-area-charts"></a><span data-ttu-id="ad7cc-118">영역형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ad7cc-118">Data Considerations for Area Charts</span></span>  
  
-   <span data-ttu-id="ad7cc-119">꺾은선형 차트 이외에 데이터를 연속적으로 표시할 수 있는 유일한 차트 종류는 영역형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-119">Along with the line chart, the area chart is the only chart type that displays data contiguously.</span></span> <span data-ttu-id="ad7cc-120">따라서 영역형 차트는 연속적인 기간 동안 발생하는 데이터를 나타내는 데 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-120">For this reason, an area chart is commonly used to represent data that occurs over a continuous period of time.</span></span>  
  
-   <span data-ttu-id="ad7cc-121">100% 기준 누적 영역형 차트는 일정 기간 동안 발생하는 데이터의 비율을 표시하는 데 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-121">A percent stacked area chart is useful for showing proportional data that occurs over time.</span></span>  
  
-   <span data-ttu-id="ad7cc-122">계열이 한 개뿐이면 누적 영역형 차트가 영역형 차트와 같은 모양으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-122">If there is only one series, a stacked area chart will be drawn as an area chart.</span></span>  
  
-   <span data-ttu-id="ad7cc-123">일반 영역형 차트에서는 여러 계열의 값이 유사한 경우 영역이 겹쳐 표시되어 중요한 데이터 요소 값을 식별하기가 쉽지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-123">In a plain area chart, if the values in multiple series are similar, the areas may overlap, obscuring important data point values.</span></span> <span data-ttu-id="ad7cc-124">영역형 차트에 여러 계열을 표시하도록 디자인된 누적 영역형 차트로 차트 종류를 변경하면 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-124">You can resolve this issue by changing the chart type to a stacked area chart, which is designed to show multiple series on an area chart.</span></span>  
  
-   <span data-ttu-id="ad7cc-125">누적 영역형 차트에 간격이 포함되어 있으면 데이터 세트에 빈 값이 포함되었음을 의미하는 것일 수 있습니다. 빈 값은 누적 영역형 차트에서 빈 섹션으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-125">If your stacked area chart contains gaps, it is possible that your dataset includes empty values, which will be shown as a vacant section on a stacked area chart.</span></span> <span data-ttu-id="ad7cc-126">데이터 세트에 빈 값이 포함되어 있으면 차트에 빈 요소를 삽입하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-126">If your dataset includes empty values, consider inserting empty points on the chart.</span></span> <span data-ttu-id="ad7cc-127">빈 요소를 추가하면 차트의 빈 영역을 다른 색으로 채워 Null 값이나 0인 값을 쉽게 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-127">Adding empty points will fill in the empty areas on the chart with a different color to indicate null or zero values.</span></span> <span data-ttu-id="ad7cc-128">자세한 내용은 [차트에 빈 요소 추가 &#40;보고서 작성기 및 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-128">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="ad7cc-129">영역형 차트 종류의 동작 방식은 세로 막대형 및 꺾은선형 차트와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-129">Area chart types are very similar to column and line charts in behavior.</span></span> <span data-ttu-id="ad7cc-130">여러 계열을 서로 비교하려는 경우에는 세로 막대형 차트를 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-130">If you are making a comparison between multiple series, consider using a column chart instead.</span></span> <span data-ttu-id="ad7cc-131">일정 기간 동안의 추세를 분석하려는 경우에는 꺾은선형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-131">If you are analyzing trends over a period of time, consider using a line chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7cc-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad7cc-132">See Also</span></span>  
 <span data-ttu-id="ad7cc-133">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ad7cc-133">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ad7cc-134">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ad7cc-134">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ad7cc-135">[꺾은선형 차트&#40;보고서 작성기 및 SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ad7cc-135">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ad7cc-136">[차트 종류 변경&#40;보고서 작성기 및 SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ad7cc-136">[Change a Chart Type &#40;Report Builder and SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ad7cc-137">차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ad7cc-137">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
