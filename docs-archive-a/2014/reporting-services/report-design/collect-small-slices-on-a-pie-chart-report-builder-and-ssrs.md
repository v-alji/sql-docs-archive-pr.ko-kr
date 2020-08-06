---
title: 원형 차트에서 작은 조각 수집(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2302217843864115847aeb544d1c64727b8ad3a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651497"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="997b0-102">원형 차트에서 작은 조각 수집(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="997b0-102">Collect Small Slices on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="997b0-103">원형 차트에서 너무 많은 데이터 요소를 표시하면 복잡하게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-103">When pie charts display too many points of data, they begin to look cluttered.</span></span> <span data-ttu-id="997b0-104">이 문제를 해결하기 위해 특정 값 미만의 모든 데이터를 원형 차트의 한 조각으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-104">To resolve this issue, you can show all data that falls beneath a certain value as one slice on the pie chart.</span></span>  
  
 <span data-ttu-id="997b0-105">여러 개의 작은 조각을 한 조각으로 수집하려면 먼저 작은 조각을 수집하기 위한 임계값을 원형 차트의 백분율과 고정 값 중 어떤 것으로 측정할지 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-105">To collect small slices into one slice, first decide whether your threshold for collecting small slices is measured as a percentage of the pie chart or as a fixed value.</span></span> <span data-ttu-id="997b0-106">그런 다음 CollectedThreshold 및 CollectedThresholdUsePercent 속성을 설정합니다. 데이터를 수집할 차트의 백분율(이 백분율 미만의 데이터가 수집됨) 또는 실제 임계 데이터 값으로 CollectedThreshold 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-106">Then set the CollectedThreshold and CollectedThresholdUsePercent properties.Set the CollectedThreshold property to either the percentage of the chart that a value must fall below to be collected, or the actual threshold data value for collection.</span></span> <span data-ttu-id="997b0-107">CollectedThresholdUsePercent 속성을로 설정 하 여 `True` 백분율을 사용 하거나 `False` 실제 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-107">Set the CollectedThresholdUsePercent property to `True` to use a percentage or `False` to use an actual value.</span></span>  
  
 <span data-ttu-id="997b0-108">첫 번째 원형 차트에서 수집된 조각으로 만든 두 번째 원형 차트에 작은 조각을 수집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-108">You can also collect small slices into a second pie chart that is called out from a collected slice of the first pie chart.</span></span> <span data-ttu-id="997b0-109">두 번째 원형 차트는 첫 번째 원형 차트의 오른쪽에 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-109">The second pie chart is drawn to the right of the original pie chart.</span></span>  
  
 <span data-ttu-id="997b0-110">깔때기형 차트나 피라미드형 차트의 조각은 한 조각으로 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-110">You cannot combine slices of funnel or pyramid charts into one slice.</span></span>  
  
 <span data-ttu-id="997b0-111">이 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-111">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="997b0-112">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="997b0-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a><span data-ttu-id="997b0-113">작은 조각을 원형 차트의 한 조각으로 수집하려면</span><span class="sxs-lookup"><span data-stu-id="997b0-113">To collect small slices into a single slice on a pie chart</span></span>  
  
1.  <span data-ttu-id="997b0-114">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-114">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="997b0-115">디자인 화면에서 원형 차트의 조각을 아무 것이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-115">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="997b0-116">계열의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-116">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="997b0-117">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-117">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="997b0-118">CollectedStyle 속성을 **SingleSlice**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-118">Set the CollectedStyle property to **SingleSlice**.</span></span>  
  
5.  <span data-ttu-id="997b0-119">수집된 임계값 및 임계값의 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-119">Set the collected threshold value and type of threshold.</span></span> <span data-ttu-id="997b0-120">다음 예는 수집된 임계값을 설정하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-120">The following examples are common ways of setting collected thresholds.</span></span>  
  
    -   <span data-ttu-id="997b0-121">**백분율로 설정.**</span><span class="sxs-lookup"><span data-stu-id="997b0-121">**By percentage.**</span></span> <span data-ttu-id="997b0-122">예를 들어 원형 차트에서 10% 미만의 모든 조각을 한 개의 조각으로 수집하려면</span><span class="sxs-lookup"><span data-stu-id="997b0-122">For example, to collect any slice on your pie chart that is less than 10% into a single slice:</span></span>  
  
         <span data-ttu-id="997b0-123">CollectedThresholdUsePercent 속성을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-123">Set the CollectedThresholdUsePercent property to `True`.</span></span>  
  
         <span data-ttu-id="997b0-124">CollectedThreshold 속성을 **10**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-124">Set the CollectedThreshold property to **10**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="997b0-125">CollectedStyle를 **singleslice로 설정**로 설정 하 고 CollectedThreshold를 **100**보다 큰 값으로 설정 하 고 CollectedThresholdUsePercent가 인 경우 `True` 백분율을 계산할 수 없기 때문에 차트에서 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-125">If you set CollectedStyle to **SingleSlice**, CollectedThreshold to a value greater than **100**, and CollectedThresholdUsePercent is `True`, the chart will throw an exception because it cannot calculate a percentage.</span></span> <span data-ttu-id="997b0-126">이 문제를 해결하려면 CollectedThreshold를 **100**보다 작은 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-126">To resolve this issue, set the CollectedThreshold to a value less than **100**.</span></span>  
  
    -   <span data-ttu-id="997b0-127">**데이터 값으로.**</span><span class="sxs-lookup"><span data-stu-id="997b0-127">**By data value.**</span></span> <span data-ttu-id="997b0-128">예를 들어 원형 차트에서 5000개 미만의 모든 조각을 한 개의 조각으로 수집하려면</span><span class="sxs-lookup"><span data-stu-id="997b0-128">For example, to collect any slice on your pie chart that is less than 5000 into a single slice:</span></span>  
  
         <span data-ttu-id="997b0-129">CollectedThresholdUsePercent 속성을로 설정 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-129">Set the CollectedThresholdUsePercent property to `False`.</span></span>  
  
         <span data-ttu-id="997b0-130">CollectedThreshold 속성을 **5000**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-130">Set the CollectedThreshold property to **5000**.</span></span>  
  
6.  <span data-ttu-id="997b0-131">CollectedLabel 속성을 수집된 조각에 표시할 텍스트 레이블을 나타내는 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-131">Set the CollectedLabel property to a string that represents the text label that will be shown on the collected slice.</span></span>  
  
7.  <span data-ttu-id="997b0-132">(선택 사항) CollectedSliceExploded, CollectedColor, CollectedLegendText 및 CollectedToolTip 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-132">(Optional) Set the CollectedSliceExploded, CollectedColor, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="997b0-133">이러한 속성은 단일 조각의 모양, 색, 레이블 텍스트, 범례 텍스트 및 도구 설명 측면을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-133">These properties change the appearance, color, label text, legend text and tooltip aspects of the single slice.</span></span>  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a><span data-ttu-id="997b0-134">작은 조각을 보조 설명선 원형 차트로 수집하려면</span><span class="sxs-lookup"><span data-stu-id="997b0-134">To collect small slices into a secondary, callout pie chart</span></span>  
  
1.  <span data-ttu-id="997b0-135">위의 1-3단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-135">Follow Steps 1-3 from above.</span></span>  
  
2.  <span data-ttu-id="997b0-136">CollectedStyle 속성을 **CollectedPie**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-136">Set the CollectedStyle property to **CollectedPie**.</span></span>  
  
3.  <span data-ttu-id="997b0-137">CollectedThreshold 속성을 작은 조각을 한 조각으로 수집할 임계값을 나타내는 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-137">Set the CollectedThresholdproperty to a value that represents the threshold at which small slices will be collected into one slice.</span></span> <span data-ttu-id="997b0-138">CollectedStyle 속성을 **CollectedPie**로 설정 하면 CollectedThresholdUsePercentproperty은 항상로 설정 되며 수집 된 `True` 임계값은 항상 백분율로 측정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-138">When the CollectedStyle property is set to **CollectedPie**, the CollectedThresholdUsePercentproperty is always set to `True`, and the collected threshold is always measured in percent.</span></span>  
  
4.  <span data-ttu-id="997b0-139">(선택 사항) CollectedColor, CollectedLabel, CollectedLegendText 및 CollectedToolTip 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-139">(Optional) Set the CollectedColor, CollectedLabel, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="997b0-140">"Collected"로 명명된 다른 모든 속성은 수집된 원형에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-140">All other properties named "Collected" do not apply to the collected pie.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="997b0-141">보조 원형 차트는 데이터의 작은 조각을 기반으로 계산되므로 미리 보기에만 나타나며</span><span class="sxs-lookup"><span data-stu-id="997b0-141">The secondary pie chart is calculated based on the small slices in your data so it will only appear in Preview.</span></span> <span data-ttu-id="997b0-142">디자인 화면에는 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-142">It does not appear on the design surface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="997b0-143">보조 원형 차트의 서식은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-143">You cannot format the secondary pie chart.</span></span> <span data-ttu-id="997b0-144">이러한 이유로 원형 조각을 수집할 때는 첫 번째 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="997b0-144">For this reason, it is strongly recommended to use the first approach when collecting pie slices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997b0-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="997b0-145">See Also</span></span>  
 <span data-ttu-id="997b0-146">[원형 차트는 보고서 작성기 및 SSRS를 &#40;&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="997b0-146">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="997b0-147">[차트의 데이터 요소에 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="997b0-147">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="997b0-148">[원형 차트 외부에 데이터 요소 레이블을 표시 하 고 보고서 작성기 및 SSRS를 &#40;&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="997b0-148">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="997b0-149">[원형 차트 &#40;보고서 작성기 및 SSRS에 백분율 값을 표시&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="997b0-149">[Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="997b0-150">차트에 3D 효과 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="997b0-150">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
