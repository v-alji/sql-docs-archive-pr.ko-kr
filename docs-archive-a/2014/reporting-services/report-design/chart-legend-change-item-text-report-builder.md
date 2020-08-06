---
title: 범례 항목의 텍스트 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d0bb721aa0ff03a5211065111c98605cd86e971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659832"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a><span data-ttu-id="683c7-102">범례 항목의 텍스트 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="683c7-102">Change the Text of a Legend Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="683c7-103">차트의 값 영역에 필드를 배치하면 해당 필드의 이름이 들어 있는 범례 항목이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-103">When a field is placed in the Values area of the chart, a legend item is automatically generated that contains the name of this field.</span></span> <span data-ttu-id="683c7-104">모든 범례 항목은 차트의 개별 계열에 연결됩니다. 단, 셰이프 차트의 경우에는 범례가 개별 계열 대신 개별 데이터 요소에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-104">Every legend item is connected to an individual series on the chart, with the exception of shape charts, where the legend is connected to individual data points instead of individual series.</span></span>  
  
 <span data-ttu-id="683c7-105">셰이프 차트에서는 범례 항목의 텍스트를 변경하여 개별 데이터 요소에 대해 추가적인 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-105">On shape charts, you can change the text of a legend item to show more information about the individual data points.</span></span> <span data-ttu-id="683c7-106">예를 들어 데이터 요소의 값을 범례에서 백분율로 표시하려면 `#PERCENT`과 같은 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-106">For example, if you want to show the values of the data points as percentages in the legend, you can use a keyword such as `#PERCENT`.</span></span> <span data-ttu-id="683c7-107">.NET Framework 형식 코드와 키워드를 함께 추가하여 숫자 및 날짜 형식을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-107">You can append .NET Framework format codes in conjunction with keywords to apply numeric and date formats.</span></span> <span data-ttu-id="683c7-108">키워드에 대한 자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="683c7-108">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="683c7-109">![뾰족한 차트](../media/sharpchart.png "뾰족한 차트")</span><span class="sxs-lookup"><span data-stu-id="683c7-109">![Sharp Chart](../media/sharpchart.png "Sharp Chart")</span></span>  
  
 <span data-ttu-id="683c7-110">셰이프 차트가 아닌 차트에서도 범례 항목의 텍스트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-110">On non-shape charts, you can change the text of a legend item.</span></span> <span data-ttu-id="683c7-111">예를 들어 계열 이름이 "Series1"인 경우 "Sales for 2008"과 같이 이해하기 쉬운 텍스트로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-111">For example, if your series name is "Series1", you may want to change the text to something more descriptive like "Sales for 2008".</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a><span data-ttu-id="683c7-112">셰이프 차트의 범례에 나타나는 텍스트를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="683c7-112">To modify the text that appears in the legend on a Shape chart</span></span>  
  
1.  <span data-ttu-id="683c7-113">**값** 영역에 포함된 필드 또는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-113">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="683c7-114">**범례** 를 클릭하고 **사용자 지정 범례 텍스트** 상자에서 키워드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-114">Click **Legend** and in the **Custom legend text** box, type a keyword.</span></span>  
  
 <span data-ttu-id="683c7-115">다음 표에서는 **사용자 지정 범례 텍스트** 속성에 사용하는 차트별 키워드의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-115">The following table provides examples of chart-specific keywords to use for the **Custom Legend Text** property.</span></span> <span data-ttu-id="683c7-116">키워드에 대한 자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="683c7-116">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
|<span data-ttu-id="683c7-117">키워드</span><span class="sxs-lookup"><span data-stu-id="683c7-117">Keyword</span></span>|<span data-ttu-id="683c7-118">Description</span><span class="sxs-lookup"><span data-stu-id="683c7-118">Description</span></span>|<span data-ttu-id="683c7-119">범례에 텍스트로 나타나는 항목의 예</span><span class="sxs-lookup"><span data-stu-id="683c7-119">Example of what appears as text in the legend</span></span>|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|<span data-ttu-id="683c7-120">합계 값의 백분율을 소수점 한 자리 수로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-120">Displays the percentage of the total value to one decimal place.</span></span>|<span data-ttu-id="683c7-121">85.0%</span><span class="sxs-lookup"><span data-stu-id="683c7-121">85.0%</span></span>|  
|`#VALY`|<span data-ttu-id="683c7-122">데이터 필드의 실제 숫자 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-122">Displays the actual numeric value of the data field.</span></span>|<span data-ttu-id="683c7-123">17000</span><span class="sxs-lookup"><span data-stu-id="683c7-123">17000</span></span>|  
|`#VALY{C2}`|<span data-ttu-id="683c7-124">데이터 필드의 실제 숫자 값을 소수점 두 자리의 통화로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-124">Displays the actual numeric value of the data field as a currency to two decimal places.</span></span>|<span data-ttu-id="683c7-125">$17000.00</span><span class="sxs-lookup"><span data-stu-id="683c7-125">$17000.00</span></span>|  
|`#AXISLABEL (#PERCENT{P0})`|<span data-ttu-id="683c7-126">범주 필드의 텍스트 표현과 각 범주가 차트에 표시되는 백분율을 차례로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-126">Displays the text representation of the category field, followed by the percentage that each category displays on the chart.</span></span>|<span data-ttu-id="683c7-127">Michael Blythe (85%)</span><span class="sxs-lookup"><span data-stu-id="683c7-127">Michael Blythe (85%)</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="683c7-128">#AXISLABEL 키워드는 **계열 그룹** 영역에 지정된 필드가 없을 때 런타임에만 평가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-128">The #AXISLABEL keyword can only be evaluated at run time when there is not a field specified in the **Series Groups** area.</span></span>  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a><span data-ttu-id="683c7-129">셰이프 차트가 아닌 차트의 범례에 나타나는 텍스트를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="683c7-129">To modify the text that appears in the legend on a non-Shape chart</span></span>  
  
1.  <span data-ttu-id="683c7-130">**값** 영역에 포함된 필드 또는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-130">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="683c7-131">**범례** 를 클릭하고 **사용자 지정 범례 텍스트** 상자에서 범례 레이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-131">Click **Legend** and in the **Custom legend text** box, type a legend label.</span></span> <span data-ttu-id="683c7-132">입력한 텍스트로 계열이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="683c7-132">The series is updated with your text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683c7-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="683c7-133">See Also</span></span>  
 <span data-ttu-id="683c7-134">[차트의 범례 서식 지정&#40;보고서 작성기 및 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="683c7-134">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="683c7-135">[차트에서 계열 색 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="683c7-135">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="683c7-136">차트에서 범례 항목 숨기기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="683c7-136">Hide Legend Items on the Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-hide-items-report-builder.md)  
  
  
