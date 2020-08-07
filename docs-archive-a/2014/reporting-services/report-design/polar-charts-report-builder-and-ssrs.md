---
title: 극좌표형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b8c4dd9394fab3e076c4a714375954a616e081f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727935"
---
# <a name="polar-charts-report-builder-and-ssrs"></a><span data-ttu-id="c5669-102">극좌표형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c5669-102">Polar Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c5669-103">극좌표형 차트에서는 360도 원에서 범주별로 그룹화된 점의 집합으로 계열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-103">A polar chart displays a series as a set of points that are grouped by category on a 360-degree circle.</span></span> <span data-ttu-id="c5669-104">값은 원의 중심에서 측정한 점까지의 거리로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-104">Values are represented by the length of the point as measured from the center of the circle.</span></span> <span data-ttu-id="c5669-105">점이 중심에서 멀수록 더 큰 값을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-105">The farther the point is from the center, the greater its value.</span></span> <span data-ttu-id="c5669-106">범주 레이블은 차트의 주위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-106">Category labels are displayed on the perimeter of the chart.</span></span> <span data-ttu-id="c5669-107">극좌표형 차트에 데이터를 추가하는 방법은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5669-107">For more information on how to add data to a polar chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="c5669-108">변형</span><span class="sxs-lookup"><span data-stu-id="c5669-108">Variations</span></span>  
  
-   <span data-ttu-id="c5669-109">**방사형 차트**.</span><span class="sxs-lookup"><span data-stu-id="c5669-109">**Radar chart**.</span></span> <span data-ttu-id="c5669-110">방사형 차트에서는 계열이 원을 이루는 선이나 영역으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-110">A radar chart displays a series as a circular line or area.</span></span> <span data-ttu-id="c5669-111">극좌표형 차트와 달리 방사형 차트에서는 데이터를 표시하는 데 극좌표를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-111">Unlike the polar chart, the radar chart does not display data in terms of polar coordinates.</span></span>  
  
## <a name="data-considerations-for-polar-charts"></a><span data-ttu-id="c5669-112">극좌표형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c5669-112">Data Considerations for Polar Charts</span></span>  
  
-   <span data-ttu-id="c5669-113">방사형 차트는 여러 계열에 속하는 범주 데이터를 서로 비교하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-113">The radar chart is useful for comparisons between multiple series of category data.</span></span>  
  
-   <span data-ttu-id="c5669-114">극좌표형 차트는 각 데이터 요소가 각도와 거리에 따라 결정되는 극좌표형 데이터를 그래프로 표현하는 데 가장 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-114">Polar charts are most commonly used to graph polar data, where each data point is determined by an angle and a distance.</span></span>  
  
-   <span data-ttu-id="c5669-115">극좌표형 차트는 동일한 차트 영역의 다른 어떠한 차트 종류와도 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-115">Polar charts cannot be combined with any other chart type in the same chart area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5669-116">예제</span><span class="sxs-lookup"><span data-stu-id="c5669-116">Example</span></span>  
 <span data-ttu-id="c5669-117">다음 예에서는 방사형 차트를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-117">The following example shows how a radar chart can be used.</span></span> <span data-ttu-id="c5669-118">아래 표에는 이 차트에 사용한 데이터가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-118">The table below provides sample data for the chart.</span></span>  
  
|<span data-ttu-id="c5669-119">속성</span><span class="sxs-lookup"><span data-stu-id="c5669-119">Name</span></span>|<span data-ttu-id="c5669-120">Sales</span><span class="sxs-lookup"><span data-stu-id="c5669-120">Sales</span></span>|  
|----------|-----------|  
|<span data-ttu-id="c5669-121">Shrubs</span><span class="sxs-lookup"><span data-stu-id="c5669-121">Shrubs</span></span>|<span data-ttu-id="c5669-122">61</span><span class="sxs-lookup"><span data-stu-id="c5669-122">61</span></span>|  
|<span data-ttu-id="c5669-123">Seeds</span><span class="sxs-lookup"><span data-stu-id="c5669-123">Seeds</span></span>|<span data-ttu-id="c5669-124">78</span><span class="sxs-lookup"><span data-stu-id="c5669-124">78</span></span>|  
|<span data-ttu-id="c5669-125">Bulbs</span><span class="sxs-lookup"><span data-stu-id="c5669-125">Bulbs</span></span>|<span data-ttu-id="c5669-126">60</span><span class="sxs-lookup"><span data-stu-id="c5669-126">60</span></span>|  
|<span data-ttu-id="c5669-127">Trees</span><span class="sxs-lookup"><span data-stu-id="c5669-127">Trees</span></span>|<span data-ttu-id="c5669-128">38</span><span class="sxs-lookup"><span data-stu-id="c5669-128">38</span></span>|  
|<span data-ttu-id="c5669-129">Flowers</span><span class="sxs-lookup"><span data-stu-id="c5669-129">Flowers</span></span>|<span data-ttu-id="c5669-130">81</span><span class="sxs-lookup"><span data-stu-id="c5669-130">81</span></span>|  
  
 <span data-ttu-id="c5669-131">이 예에서 이름 필드는 범주 그룹 영역에 배치되고,</span><span class="sxs-lookup"><span data-stu-id="c5669-131">In this example, the Name field is placed in the Category Groups area.</span></span> <span data-ttu-id="c5669-132">판매량 필드는 값 영역에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-132">The Sales field is placed in the Values area.</span></span> <span data-ttu-id="c5669-133">판매량 필드를 끌어다 놓으면 차트에서 해당 필드가 자동으로 집계 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-133">The Sales field is automatically aggregated for the chart when you drop it.</span></span> <span data-ttu-id="c5669-134">방사형 차트에서는 판매량 필드에 몇 개의 값이 있는지 확인한 후 이를 기준으로 레이블의 위치를 결정합니다. 이 예의 경우 판매량 필드에 다섯 개의 값이 포함되므로 레이블을 원에서 균등한 거리에 있는 다섯 지점에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-134">The radar chart calculates where to place the labels based on the number of values in the Sales field, which contains five values and places labels at five equidistant points on a circle.</span></span> <span data-ttu-id="c5669-135">판매량 필드에 포함된 값이 세 개이면 레이블이 원에서 균등한 거리에 있는 세 지점에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-135">If the Sales field contained three values, the labels would be placed at three equidistant points on a circle.</span></span>  
  
 <span data-ttu-id="c5669-136">다음 그림에서는 위의 데이터를 기준으로 생성된 방사형 차트의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c5669-136">The following illustration shows an example of a radar chart based on the data presented.</span></span>  
  
 <span data-ttu-id="c5669-137">![방사형 차트](../media/rs-radarchart.gif "방사형 차트")</span><span class="sxs-lookup"><span data-stu-id="c5669-137">![Radar chart](../media/rs-radarchart.gif "Radar chart")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5669-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5669-138">See Also</span></span>  
 <span data-ttu-id="c5669-139">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5669-139">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5669-140">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5669-140">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5669-141">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5669-141">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5669-142">[꺾은선형 차트&#40;보고서 작성기 및 SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5669-142">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c5669-143">차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c5669-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
