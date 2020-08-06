---
title: 축 속성 대화 상자, 축 옵션 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650813"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a><span data-ttu-id="d227c-102">축 속성 대화 상자, 축 옵션(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d227c-102">Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d227c-103">**가로** 또는 **세로 축 속성** 대화 상자에서 **축 옵션** 을 선택 하 여 차트의 지정 된 축 모양을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-103">Select **Axis Options** on the **Horizontal** or **VerticalAxis Properties** dialog box to define the appearance of the specified axis of the chart.</span></span> <span data-ttu-id="d227c-104">이전 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에서는 기본적으로 차트의 x축에 모든 레이블이 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-104">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the chart displayed all labels on the x-axis by default.</span></span> <span data-ttu-id="d227c-105">그러나 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008에서는 보다 깔끔한 차트 이미지를 제공하고 레이블이 겹치는 것을 방지하기 위해 레이블이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-105">However, in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008, the chart skips labels in order to produce a cleaner image on the chart and avoid labeling collisions.</span></span> <span data-ttu-id="d227c-106">자세한 내용은 [차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d227c-106">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d227c-107">옵션</span><span class="sxs-lookup"><span data-stu-id="d227c-107">Options</span></span>  
 <span data-ttu-id="d227c-108">**배율 구분선 사용**</span><span class="sxs-lookup"><span data-stu-id="d227c-108">**Enable scale breaks**</span></span>  
 <span data-ttu-id="d227c-109">필요하다고 판단되는 경우 차트에 배율 구분선을 그릴 수 있도록 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-109">Select this option to enable the chart to draw a scale breaks when it is deemed necessary.</span></span> <span data-ttu-id="d227c-110">이 옵션을 활성화하면 데이터 세트의 높은 값 요소와 낮은 값 요소 사이의 차이가 충분하여 배율 구분선을 그릴 수 있는지 여부가 차트에서 자동으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-110">When this option is enabled, the chart will automatically calculate whether there is sufficient difference between the high and low points in the dataset to draw a scale break.</span></span>  
  
 <span data-ttu-id="d227c-111">**방향 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="d227c-111">**Reverse direction**</span></span>  
 <span data-ttu-id="d227c-112">차트를 반대 방향으로 바꾸려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-112">Select this option to reverse the direction of the chart.</span></span> <span data-ttu-id="d227c-113">예를 들어 세로 막대형 차트에서는 기본적으로 차트 왼쪽에 y 축이 표시되고 왼쪽에서 오른쪽 순으로 각 범주가 배치되는데</span><span class="sxs-lookup"><span data-stu-id="d227c-113">For example, by default, a column chart displays the y-axis on the left side of the chart and categories from left to right.</span></span> <span data-ttu-id="d227c-114">이 옵션을 선택하면 차트 오른쪽에 y 축이 표시되고 오른쪽에서 왼쪽 순으로 범주가 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-114">When this option is selected, the chart displays the y-axis on the right side of the chart and categories from right to left.</span></span>  
  
 <span data-ttu-id="d227c-115">**인터레이스 색 사용**</span><span class="sxs-lookup"><span data-stu-id="d227c-115">**Use interlacing color**</span></span>  
 <span data-ttu-id="d227c-116">차트에 줄무늬 선을 추가한 다음 색을 선택하거나 식을 입력하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-116">Select this option to add strip lines to the chart, and then select a color or type an expression.</span></span> <span data-ttu-id="d227c-117">줄무늬 선은 눈금선 사이에 밝은 영역과 어두운 영역이 교대로 배치되는 효과를 주는 차트 영역의 음영 밴드입니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-117">Strip lines are shaded bands on the chart area that give the effect of alternating light and dark areas between gridlines.</span></span> <span data-ttu-id="d227c-118">이러한 줄무늬 선은 축에서 반복되는 패턴을 강조 표시하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-118">These strip lines are useful for highlighting repeating patterns on an axis.</span></span>  
  
 <span data-ttu-id="d227c-119">**항상 0 포함**</span><span class="sxs-lookup"><span data-stu-id="d227c-119">**Always include zero**</span></span>  
 <span data-ttu-id="d227c-120">축 눈금에 항상 0을 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-120">Select this option to always include zero on the axis scale.</span></span> <span data-ttu-id="d227c-121">이 옵션을 활성화하지 않으면 차트의 축에 0 값이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-121">If this option is not enabled, the chart will not label the zero value on the axis.</span></span> <span data-ttu-id="d227c-122">데이터 세트에 음수 또는 0인 값이 들어 있으면 0 값을 포함하는 것이 좋을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-122">Including zero values is useful when the dataset includes negative or zero values.</span></span>  
  
 <span data-ttu-id="d227c-123">**스칼라 축**</span><span class="sxs-lookup"><span data-stu-id="d227c-123">**Scalar axis**</span></span>  
 <span data-ttu-id="d227c-124">연속적인 눈금에 축 값의 집합을 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-124">Select this option to display a set of axis values on a continuous scale.</span></span> <span data-ttu-id="d227c-125">예를 들어 데이터 세트에 1월, 3월 및 11월 데이터가 들어 있는 경우 축이 스칼라 형식이 아니면 해당 월만 표시되는 반면 스칼라 축에는 한 해의 모든 월이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-125">For example, if the dataset contains data for January, March, and November, a non-scalar axis displays only those months, whereas a scalar axis displays all of the months in the year.</span></span>  
  
 <span data-ttu-id="d227c-126">**로그 눈금 간격 사용**</span><span class="sxs-lookup"><span data-stu-id="d227c-126">**Use logarithmic scale**</span></span>  
 <span data-ttu-id="d227c-127">y 축 눈금을 로그 눈금으로 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-127">Select this option to indicate that the axis scale is logarithmic.</span></span> <span data-ttu-id="d227c-128">이 옵션은 축에 양수 값이 포함되어 있을 때 y 축에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-128">This option is available only on the y-axis if the axis contains positive numeric values.</span></span>  
  
 <span data-ttu-id="d227c-129">로그 눈금을 사용하도록 축을 설정한 경우 사용할 로그의 밑을 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-129">In the box, type the logarithmic base to use when the axis is set to use a logarithmic scale.</span></span> <span data-ttu-id="d227c-130">기본적으로 차트에는 축의 로그 눈금에 대한 밑으로 10이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-130">By default, the chart uses a base of 10 for the logarithmic scale of an axis.</span></span> <span data-ttu-id="d227c-131">이 옵션은 축이 숫자일 때 y 축에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-131">This option is available only on the y-axis if the axis is numeric.</span></span>  
  
 <span data-ttu-id="d227c-132">**최소**</span><span class="sxs-lookup"><span data-stu-id="d227c-132">**Minimum**</span></span>  
 <span data-ttu-id="d227c-133">x 축의 최소값 또는 이를 반환하는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-133">Type an expression or a value for the minimum value for the x-axis.</span></span> <span data-ttu-id="d227c-134">생략한 경우 데이터 세트에서 반환한 데이터에 의해 최소값이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-134">If omitted, the minimum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="d227c-135">**최댓값**</span><span class="sxs-lookup"><span data-stu-id="d227c-135">**Maximum**</span></span>  
 <span data-ttu-id="d227c-136">X축의 최대값 또는 이를 반환하는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-136">Type an expression or a value for the maximum value for the x-axis.</span></span> <span data-ttu-id="d227c-137">생략한 경우 데이터 세트에서 반환한 데이터에 의해 최대값이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-137">If omitted, the maximum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="d227c-138">**간격**</span><span class="sxs-lookup"><span data-stu-id="d227c-138">**Interval**</span></span>  
 <span data-ttu-id="d227c-139">축 레이블 간의 간격 값 또는 이를 반환하는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-139">Type an expression or value for the interval between axis labels.</span></span> <span data-ttu-id="d227c-140">예를 들어 축에 각 범주 레이블을 표시하려면 1을 입력하고,</span><span class="sxs-lookup"><span data-stu-id="d227c-140">For example, type 1 to display each category label on the axis.</span></span> <span data-ttu-id="d227c-141">범주 레이블을 하나 걸러 하나씩 표시하려면 2를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-141">Type 2 to display every other category label.</span></span> <span data-ttu-id="d227c-142">간격을 지정하지 않으면 레이블은 데이터 세트의 값을 기준으로 자동으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-142">If omitted, the labels are calculated automatically based on the values in the dataset.</span></span>  
  
 <span data-ttu-id="d227c-143">**간격 유형**</span><span class="sxs-lookup"><span data-stu-id="d227c-143">**Interval type**</span></span>  
 <span data-ttu-id="d227c-144">지정된 간격의 간격 유형을 나타내는 식이나 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-144">Type an expression or a value for the interval type of the interval specified.</span></span> <span data-ttu-id="d227c-145">예를 들어 간격을 이틀로 설정하려면 간격으로 **2** 를 지정하고 간격 유형으로 **일** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-145">For example, if you want the interval to be two days, you will specify **2** for interval and **Days** for interval type.</span></span>  
  
 <span data-ttu-id="d227c-146">**양쪽 여백**</span><span class="sxs-lookup"><span data-stu-id="d227c-146">**Side margins**</span></span>  
 <span data-ttu-id="d227c-147">차트 요소와 차트의 양쪽 측면 사이의 여백을 지정하는 값을 선택하거나 이를 반환하는 식을 입력하여 여백을 추가 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-147">Type an expression or select a value to add or remove a margin between the chart elements and the sides of the chart.</span></span> <span data-ttu-id="d227c-148">이 옵션을 **자동**으로 설정하면 양쪽 여백이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d227c-148">If this option is set to **Auto**, a side margins are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d227c-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d227c-149">See Also</span></span>  
 <span data-ttu-id="d227c-150">[차트의 축 레이블 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-150">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-151">[차트 &#40;보고서 작성기 및 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-151">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-152">[차트에서 계열 색 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-152">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-153">[보고서 작성기 및 SSRS &#40;축 간격을 지정&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-153">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-154">[축 레이블의 서식을 날짜 또는 통화로 지정 보고서 작성기 및 SSRS &#40;&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-154">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-155">[보조 축에 데이터 플롯 &#40;보고서 작성기 및 SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-155">[Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d227c-156">[보고서 작성기 및 SSRS &#40;스파크 라인과 데이터 막대&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d227c-156">[Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d227c-157">차트에서 여백 추가 또는 제거&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d227c-157">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
