---
title: 차트의 레이블 위치 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e90cbf04e0282454658e6324f0ba6600a99cb718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727928"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="44b1f-102">차트의 레이블 위치 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="44b1f-102">Position Labels in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="44b1f-103">차트 종류마다 셰이프가 다르므로 데이터 요소 레이블은 차트에서 방해가 되지 않을 최적의 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-103">Because each chart type has a different shape, data point labels are placed in an optimal location so as not to interfere on the chart.</span></span> <span data-ttu-id="44b1f-104">레이블의 기본 위치는 차트 종류에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-104">The default position of the labels depends varies with the chart type:</span></span>  
  
-   <span data-ttu-id="44b1f-105">누적 차트에서 레이블은 계열의 안쪽에만 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-105">On stacked charts, labels can only be positioned inside the series.</span></span>  
  
-   <span data-ttu-id="44b1f-106">깔때기형 또는 피라미드형 차트에서 레이블은 열의 바깥쪽에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-106">On funnel or pyramid charts, labels are placed on the outside in a column.</span></span>  
  
-   <span data-ttu-id="44b1f-107">원형 차트에서 레이블은 원형 차트의 개별 조각 안쪽에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-107">On pie charts, labels are placed inside the individual slices on a pie chart.</span></span>  
  
-   <span data-ttu-id="44b1f-108">가로 막대형 차트에서 레이블은 데이터 요소를 나타내는 막대의 바깥쪽에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-108">On bar charts, labels are placed outside of the bars that represent data points.</span></span>  
  
-   <span data-ttu-id="44b1f-109">극좌표형 차트에서 레이블은 데이터 요소를 나타내는 원형 영역의 바깥쪽에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-109">On polar charts, labels are placed outside of the circular area that represents data points.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a><span data-ttu-id="44b1f-110">원형 차트에서 요소 레이블의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="44b1f-110">To change the position of point labels in a Pie chart</span></span>  
  
1.  <span data-ttu-id="44b1f-111">원형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-111">Create a pie chart.</span></span>  
  
2.  <span data-ttu-id="44b1f-112">디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-112">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="44b1f-113">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-113">Open the Properties pane.</span></span> <span data-ttu-id="44b1f-114">**보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-114">On the **View** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="44b1f-115">디자인 화면에서 차트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-115">On the design surface, click the chart.</span></span> <span data-ttu-id="44b1f-116">차트의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-116">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="44b1f-117">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-117">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="44b1f-118">원형 차트에 대한 특성 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-118">A list of attributes for the pie chart is displayed.</span></span>  
  
6.  <span data-ttu-id="44b1f-119">PieLabelStyle 속성의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-119">Select a value for the PieLabelStyle property.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a><span data-ttu-id="44b1f-120">깔때기형 또는 피라미드형 차트에서 요소 레이블의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="44b1f-120">To change the position of point labels in a Funnel or Pyramid chart</span></span>  
  
1.  <span data-ttu-id="44b1f-121">깔때기형 또는 피라미드형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-121">Create a funnel or pyramid chart.</span></span>  
  
2.  <span data-ttu-id="44b1f-122">디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-122">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="44b1f-123">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-123">Open the Properties pane.</span></span> <span data-ttu-id="44b1f-124">**보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-124">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="44b1f-125">디자인 화면에서 차트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-125">On the design surface, click the chart.</span></span> <span data-ttu-id="44b1f-126">차트의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-126">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="44b1f-127">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-127">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="44b1f-128">깔때기형 차트에 대한 특성 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-128">A list of attributes for the funnel chart is displayed.</span></span>  
  
6.  <span data-ttu-id="44b1f-129">깔때기형 차트의 경우 FunnelLabelStyle 속성의 값을 선택하고,</span><span class="sxs-lookup"><span data-stu-id="44b1f-129">For a funnel chart, select a value for the FunnelLabelStyle property.</span></span> <span data-ttu-id="44b1f-130">피라미드형 차트의 경우 PyramidLabelStyle 속성의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-130">For a pyramid chart, select a value for the PyramidLabelStyle property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44b1f-131">이 속성을 `OutsideInColumn` 값으로 설정하면 레이블이 세로 열에 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-131">When this property is set to a value `OutsideInColumn`, the labels are drawn in a vertical column.</span></span> <span data-ttu-id="44b1f-132">열의 위치는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-132">There is no way to change the position of the column.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a><span data-ttu-id="44b1f-133">가로 막대형 차트에서 요소 레이블의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="44b1f-133">To change the position of point labels in a Bar chart</span></span>  
  
1.  <span data-ttu-id="44b1f-134">가로 막대형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-134">Create a bar chart.</span></span>  
  
2.  <span data-ttu-id="44b1f-135">디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-135">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="44b1f-136">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-136">Open the Properties pane.</span></span> <span data-ttu-id="44b1f-137">**보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-137">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="44b1f-138">디자인 화면에서 차트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-138">On the design surface, click the chart.</span></span> <span data-ttu-id="44b1f-139">차트의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-139">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="44b1f-140">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-140">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="44b1f-141">막대형 차트에 대한 특성 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-141">A list of attributes for the bar chart is displayed.</span></span>  
  
6.  <span data-ttu-id="44b1f-142">BarLabelStyle 속성의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-142">Select a value for the BarLabelStyle property.</span></span>  
  
 <span data-ttu-id="44b1f-143">막대 레이블 스타일을 `Outside`로 설정하면 레이블이 차트 영역 내에서 막대의 바깥쪽에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-143">When the bar label style is set to `Outside`, the labels will be placed outside of the bar, as long as it fits in the chart area.</span></span> <span data-ttu-id="44b1f-144">레이블을 막대의 바깥쪽에 배치할 수 없지만 차트 영역의 안쪽에는 배치할 수 있는 경우 레이블은 막대 안쪽에서 막대 끝에 가장 가까운 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-144">If the label cannot be placed outside of the bar but inside of the chart area, the label is placed inside the bar at the position closest to the end of the bar.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a><span data-ttu-id="44b1f-145">영역형, 세로 막대형, 꺾은선형 또는 분산형 차트에서 요소 레이블의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="44b1f-145">To change the position of point labels in an Area, Column, Line or Scatter chart</span></span>  
  
1.  <span data-ttu-id="44b1f-146">영역형, 세로 막대형, 꺾은선형 또는 분산형 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-146">Create an Area, Column, Line or Scatter chart.</span></span>  
  
2.  <span data-ttu-id="44b1f-147">디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-147">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="44b1f-148">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-148">Open the Properties pane.</span></span> <span data-ttu-id="44b1f-149">**보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-149">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="44b1f-150">디자인 화면에서 계열을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-150">On the design surface, click the series.</span></span> <span data-ttu-id="44b1f-151">계열의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-151">The properties for the series are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="44b1f-152">**데이터** 섹션에서 **DataPoint** 노드를 확장한 다음 **Label**노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-152">In the **Data** section, expand the **DataPoint** node, then expand the **Label**node.</span></span>  
  
6.  <span data-ttu-id="44b1f-153">Position 속성의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b1f-153">Select a value for the Position property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b1f-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44b1f-154">See Also</span></span>  
 <span data-ttu-id="44b1f-155">[원형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44b1f-155">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44b1f-156">[가로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44b1f-156">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44b1f-157">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44b1f-157">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44b1f-158">[축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44b1f-158">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="44b1f-159">[원형 차트 외부에 데이터 요소 레이블 표시&#40;보고서 작성기 및 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="44b1f-159">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="44b1f-160">차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="44b1f-160">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  
