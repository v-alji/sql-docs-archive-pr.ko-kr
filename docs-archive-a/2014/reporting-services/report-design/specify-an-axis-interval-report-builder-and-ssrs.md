---
title: 축 간격 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b64b824933753a8482360f193ca4ccf71e8d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639278"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a><span data-ttu-id="cf620-102">축 간격 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="cf620-102">Specify an Axis Interval (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cf620-103">축 간격은 축에 있는 레이블 및 해당 눈금 표시의 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-103">The axis interval defines the number of labels and accompanying tick marks on an axis.</span></span> <span data-ttu-id="cf620-104">값 축에서 축 간격은 차트의 데이터 요소를 일정하게 측정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-104">On the value axis, axis intervals provide a consistent measure of the data points on the chart.</span></span> <span data-ttu-id="cf620-105">그러나 범주 축에서는 이 기능 때문에 범주가 축 레이블 없이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-105">However, on the category axis, this functionality can cause categories to appear without axis labels.</span></span> <span data-ttu-id="cf620-106">축 Interval 속성에서 원하는 간격 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-106">You can specify the number of intervals you want in the axis Interval property.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cf620-107">는 결과 집합의 데이터를 기반으로 런타임에 간격 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-107">calculates the number of intervals at run time, based on the data in the result set.</span></span> <span data-ttu-id="cf620-108">축 간격을 계산하는 방법에 대한 자세한 내용은 [차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf620-108">For more information about how axis intervals are calculated, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="cf620-109">이 항목은 범주 축의 날짜 또는 시간 값에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-109">This topic is not applicable for date or time values on the category axis.</span></span> <span data-ttu-id="cf620-110">기본적으로 `DateTime` 값은 일로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-110">Be default, `DateTime` values appear as days.</span></span> <span data-ttu-id="cf620-111">월 또는 시간 간격과 같은 다른 날짜 또는 시간 간격을 지정하려면 축 레이블의 서식을 지정하고 `DateTime` 형식 대신 `String` 형식의 인스턴스를 표시하도록 축을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-111">To specify a different date or time interval, such as a month or time interval, you must format the axis labels and set the axis to display instances of `DateTime` types instead of `String` types.</span></span> <span data-ttu-id="cf620-112">또한 Interval 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-112">In addition, you must set the Interval property.</span></span> <span data-ttu-id="cf620-113">자세한 내용은 [축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf620-113">For more information, see [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="cf620-114">이 항목은 축이 없는 원형, 도넛형, 깔때기형 또는 피라미드형 차트에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-114">This topic does not apply to pie, doughnut, funnel or pyramid charts, which do not have axes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf620-115">일반적으로 범주 축은 가로 축 또는 x축이지만</span><span class="sxs-lookup"><span data-stu-id="cf620-115">The category axis is usually the horizontal or x-axis.</span></span> <span data-ttu-id="cf620-116">가로 막대형 차트에서는 범주 축이 세로 축 또는 y축입니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-116">However, for bar charts, the category axis is the vertical or y-axis.</span></span>  
  
 <span data-ttu-id="cf620-117">다른 축 간격을 지정하는 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-117">An example of a chart specifying different axis intervals is available as a sample report.</span></span> <span data-ttu-id="cf620-118">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf620-118">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a><span data-ttu-id="cf620-119">X축에 모든 범주 레이블을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="cf620-119">To show all category labels on the x-axis</span></span>  
  
1.  <span data-ttu-id="cf620-120">범주 축을 마우스 오른쪽 단추로 클릭하고 **축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-120">Right-click the category axis and click **Axis Properties**.</span></span> <span data-ttu-id="cf620-121">**축 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-121">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="cf620-122">**축 옵션**에서을 `Interval` **1**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-122">In **Axis Options**, set `Interval` to **1**.</span></span> <span data-ttu-id="cf620-123">모든 범주 그룹 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-123">Every category group label is displayed.</span></span> <span data-ttu-id="cf620-124">x축에 다른 모든 범주 그룹 레이블을 표시하려면 **2**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-124">If you want to show every other category group label on the x-axis, type **2**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf620-125">축 간격이 설정되면 모든 자동 레이블 지정이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-125">When an axis interval is set, all automatic labeling is disabled.</span></span> <span data-ttu-id="cf620-126">축 간격에 대한 값을 지정할 경우 범주 축의 범주 수에 따라 예측할 수 없는 레이블 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-126">If you specify a value for the axis interval, you may experience unpredictable labeling behavior depending on how many categories are on the category axis.</span></span>  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a><span data-ttu-id="cf620-127">축에서 가변 간격 계산을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="cf620-127">To enable a variable interval calculation on an axis</span></span>  
  
1.  <span data-ttu-id="cf620-128">변경할 차트 축을 마우스 오른쪽 단추로 클릭한 다음 **축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-128">Right-click the chart axis that you want to change, and then click **Axis Properties**.</span></span> <span data-ttu-id="cf620-129">**축 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-129">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="cf620-130">**축 옵션**에서 `Interval` **자동**으로 설정 합니다. 차트에 축을 따라 맞출 수 있는 최적의 범주 레이블 수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf620-130">In **Axis Options**, set `Interval` to **Auto**. The chart will display the optimal number of category labels that can fit along the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf620-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf620-131">See Also</span></span>  
 <span data-ttu-id="cf620-132">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf620-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cf620-133">[차트의 데이터 요소에 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf620-133">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cf620-134">[데이터 영역의 데이터 정렬 &#40;보고서 작성기 및 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf620-134">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cf620-135">[축 속성 대화 상자, 축 옵션 보고서 작성기 및 SSRS &#40;&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf620-135">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cf620-136">[로그 눈금 &#40;보고서 작성기 및 SSRS를 지정&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf620-136">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cf620-137">보조 축에 데이터 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cf620-137">Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;</span></span>](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
