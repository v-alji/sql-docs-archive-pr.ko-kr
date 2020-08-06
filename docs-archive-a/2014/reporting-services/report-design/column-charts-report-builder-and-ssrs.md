---
title: 세로 막대형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6ebada49e65d44a2294228a3840bf4951140812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742835"
---
# <a name="column-charts-report-builder-and-ssrs"></a><span data-ttu-id="3fb00-102">세로 막대형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3fb00-102">Column Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3fb00-103">세로 막대형 차트에서 계열은 범주별로 그룹화된 일련의 세로 막대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="3fb00-104">세로 막대형 차트는 기간에 따라 변경되는 데이터를 표시하거나 항목 간 차이를 설명하는 데 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-104">Column charts are useful for showing data changes over a period of time or for illustrating comparisons among items.</span></span> <span data-ttu-id="3fb00-105">일반 세로 막대형 차트는 가로 막대 집합으로 계열을 표시하는 가로 막대형 차트 및 시작점과 끝점이 다양한 세로 막대 집합으로 계열을 표시하는 범위형 세로 막대 차트와 밀접하게 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-105">The plain column chart is closely related to the bar chart, which displays series as sets of horizontal bars, and the range column chart, which displays series as sets of vertical bars with varying beginning and end points.</span></span> <span data-ttu-id="3fb00-106">자세한 내용은 [가로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) 및 [범위형 차트&#40;보고서 작성기 및 SSRS&#41;](range-charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fb00-106">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and [Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3fb00-107">세 계열이 모두 공통 기간을 공유하여 각 계열을 서로 비교하는 것이 가능하므로 이 데이터에는 세로 막대형 차트가 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-107">The column chart is well suited for this data because all three series share a common time period, allowing for valid comparisons to be made.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a><span data-ttu-id="3fb00-108">세로 막대형 차트의 변형</span><span class="sxs-lookup"><span data-stu-id="3fb00-108">Variations of a Column Chart</span></span>  
  
-   <span data-ttu-id="3fb00-109">**누적 가로 막대형**.</span><span class="sxs-lookup"><span data-stu-id="3fb00-109">**Stacked**.</span></span> <span data-ttu-id="3fb00-110">여러 계열을 세로로 누적하여 표시하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-110">A column chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="3fb00-111">차트에 계열이 하나만 있으면 누적 세로 막대형 차트는 세로 막대형 차트와 동일한 모양으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-111">If there is only one series in your chart, the stacked column chart will display the same as a column chart.</span></span>  
  
-   <span data-ttu-id="3fb00-112">**100% 기준 누적 가로 막대형**.</span><span class="sxs-lookup"><span data-stu-id="3fb00-112">**Percent stacked**.</span></span> <span data-ttu-id="3fb00-113">차트 영역 전체에 꼭 맞도록 여러 계열을 세로로 누적하여 표시하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-113">A column chart where multiple series are stacked vertically to fit 100% of the chart area.</span></span> <span data-ttu-id="3fb00-114">차트에 계열이 하나만 있으면 모든 세로 막대가 차트 영역 전체에 맞게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-114">If there is only one series in your chart, all the column bars will fit to 100% of the chart area.</span></span>  
  
-   <span data-ttu-id="3fb00-115">**3D 묶은 가로 막대형**.</span><span class="sxs-lookup"><span data-stu-id="3fb00-115">**3D clustered**.</span></span> <span data-ttu-id="3fb00-116">3D 차트에서 각 계열을 별도의 행에 표시하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-116">A column chart that shows individual series in separate rows on a 3D chart.</span></span>  
  
-   <span data-ttu-id="3fb00-117">**3D 원통형**.</span><span class="sxs-lookup"><span data-stu-id="3fb00-117">**3D cylinder**.</span></span> <span data-ttu-id="3fb00-118">3D 차트에서 막대를 실린더 모양으로 표시하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-118">A column chart whose bars are shaped like cylinders on a 3D chart.</span></span>  
  
-   <span data-ttu-id="3fb00-119">`Histogram`.</span><span class="sxs-lookup"><span data-stu-id="3fb00-119">`Histogram`.</span></span> <span data-ttu-id="3fb00-120">막대가 정규 분포로 정렬되도록 차트를 계산하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-120">A column chart which the chart calculates so that its bars are arranged in a normal distribution.</span></span>  
  
-   <span data-ttu-id="3fb00-121">`Pareto`.</span><span class="sxs-lookup"><span data-stu-id="3fb00-121">`Pareto`.</span></span> <span data-ttu-id="3fb00-122">가장 긴 막대에서 가장 짧은 막대 순서로 막대를 정렬하는 세로 막대형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-122">A column chart whose bars are arranged from highest to lowest.</span></span>  
  
## <a name="data-considerations-for-a-column-chart"></a><span data-ttu-id="3fb00-123">세로 막대형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3fb00-123">Data Considerations for a Column Chart</span></span>  
  
-   <span data-ttu-id="3fb00-124">가로 막대형 및 세로 막대형 차트는 그룹 간의 비교에 매우 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-124">Bar and column charts are most commonly used to show comparisons between groups.</span></span> <span data-ttu-id="3fb00-125">네 개 이상의 계열을 차트에 표시해야 하는 경우에는 누적 가로 막대형 또는 세로 막대형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-125">If more than three series are present on the chart, consider using a stacked bar or column chart.</span></span> <span data-ttu-id="3fb00-126">차트에 표시할 계열이 여러 개인 경우 누적 가로 막대형 또는 세로 막대형 차트를 여러 개의 그룹으로 묶을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-126">You can also collect stacked bar or column charts into multiple groups if you have several series on your chart.</span></span> <span data-ttu-id="3fb00-127">자세한 내용은 [가로 막대형 차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) 및 *세로 막대형 차트*를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3fb00-127">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and *Column Charts*.</span></span>  
  
-   <span data-ttu-id="3fb00-128">세로 막대형 차트에서는 범주 축 레이블을 가로로 표시할 수 있는 공간이 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-128">In a column chart, you have less space for category axis labels to display horizontally.</span></span> <span data-ttu-id="3fb00-129">범주 레이블이 긴 경우 가로 막대형 차트를 사용하거나 레이블의 회전 각도를 변경하는 것이 좋을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-129">If you have longer category labels, consider using a bar chart or changing the rotation angle of the label.</span></span>  
  
-   <span data-ttu-id="3fb00-130">세로 막대형 차트의 개별 막대에 특별한 그리기 스타일을 추가하여 시각적 효과를 더욱 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-130">You can add special drawing styles to the individual bars on a column chart to increase its visual impact.</span></span> <span data-ttu-id="3fb00-131">그리기 스타일에는 쐐기형, 볼록, 원통형 및 그라데이션 효과 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-131">Drawing styles include wedge, emboss, cylinder and light-to-dark.</span></span> <span data-ttu-id="3fb00-132">이러한 효과는 2D 차트의 모양을 향상시킬 목적으로 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-132">These effects are designed to improve the appearance of your 2D chart.</span></span> <span data-ttu-id="3fb00-133">3D 차트를 사용할 때도 그리기 스타일을 적용할 수는 있지만 그 효과는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-133">If you are using a 3D chart, the drawing styles will still be applied, but may not have the same effect.</span></span> <span data-ttu-id="3fb00-134">막대형 차트에 그리기 스타일을 추가하는 방법에 대한 자세한 내용은 [차트에 빗면 효과, 볼록 효과 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fb00-134">For more information about how to add a drawing style to a bar chart, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
-   <span data-ttu-id="3fb00-135">세로 막대형 차트에서만 차트를 히스토그램 또는 파레토 차트로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb00-135">Unique to column charts is the ability to show your chart as a histogram or Pareto chart.</span></span> <span data-ttu-id="3fb00-136">이렇게 하려면 속성 창에서 ShowColumnAs 속성을 또는로 설정 합니다 `Histogram` `Pareto` `true` .</span><span class="sxs-lookup"><span data-stu-id="3fb00-136">To do so, set the ShowColumnAs property to `Histogram` or `Pareto` in the Properties window to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb00-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3fb00-137">See Also</span></span>  
 <span data-ttu-id="3fb00-138">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fb00-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fb00-139">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fb00-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fb00-140">[가로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fb00-140">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fb00-141">[범위형 차트&#40;보고서 작성기 및 SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3fb00-141">[Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3fb00-142">[자습서: 보고서에 막대형 차트 추가&#40;보고서 작성기&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3fb00-142">[Tutorial: Add a Bar Chart to Your Report &#40;Report Builder&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="3fb00-143">차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3fb00-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
