---
title: 차트에 배율 구분선 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c081debd1e0a84158615edebdb6b84705c10e5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735024"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="02e18-102">차트에 배율 구분선 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="02e18-102">Add Scale Breaks to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="02e18-103">배율 구분선은 값 축(일반적으로 세로 또는 Y축)에서 높은 값과 낮은 값 사이의 연속성을 구분하기 위해 차트의 그리기 영역에 표시되는 줄무늬입니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-103">A scale break is a stripe drawn across the plotting area of a chart to denote a break in continuity between the high and low values on a value axis (usually the vertical, or y-axis).</span></span> <span data-ttu-id="02e18-104">배율 구분선을 사용하여 동일한 차트 영역에 두 개의 서로 다른 범위를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-104">Use a scale break to display two distinct ranges in the same chart area.</span></span>  
  
 <span data-ttu-id="02e18-105">![눈금 구분선을 포함하는 차트](../media/rs-multipledatarangeschart-scalebreak.gif "눈금 구분선을 포함하는 차트")</span><span class="sxs-lookup"><span data-stu-id="02e18-105">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02e18-106">차트에서 배율 구분선의 배치 위치는 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-106">You cannot specify where to place a scale break on your chart.</span></span> <span data-ttu-id="02e18-107">차트는 데이터 세트의 값을 기반으로 자체 계산을 사용하여 런타임에 값 축(y축)에 배율 구분선을 그릴 수 있을 만큼 데이터 범위가 충분히 분리되어 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-107">The chart uses its own calculations based on the values in your dataset to determine whether there is sufficient separation between data ranges to draw a scale break on the value axis (y-axis) at run time.</span></span>  
  
 <span data-ttu-id="02e18-108">배율 구분선이 있는 차트의 예는 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-108">An example of a chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="02e18-109">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="02e18-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a><span data-ttu-id="02e18-110">차트에서 배율 구분선을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="02e18-110">To enable scale breaks on the chart</span></span>  
  
1.  <span data-ttu-id="02e18-111">세로 축을 마우스 오른쪽 단추로 클릭한 다음 **축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-111">Right-click the vertical axis and then click **Axis Properties**.</span></span> <span data-ttu-id="02e18-112">**세로 축 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-112">The **VerticalAxis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="02e18-113">**배율 구분선 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-113">Select the **Enable scale breaks** check box.</span></span>  
  
### <a name="to-change-the-style-of-the-scale-break"></a><span data-ttu-id="02e18-114">배율 구분선 스타일을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="02e18-114">To change the style of the scale break</span></span>  
  
1.  <span data-ttu-id="02e18-115">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-115">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="02e18-116">디자인 화면에서 차트의 y축을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-116">On the design surface, right-click on the y-axis of the chart.</span></span> <span data-ttu-id="02e18-117">y축 개체(기본 이름은 Chart Axis)에 대한 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-117">The properties for the y-axis object (named Chart Axis by default) are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="02e18-118">**배율** 섹션에서 ScaleBreakStyle 속성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-118">In the **Scale** section, expand the ScaleBreakStyle property.</span></span>  
  
4.  <span data-ttu-id="02e18-119">BreakLineType 및 간격과 같은 ScaleBreakStyle 속성에 대한 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="02e18-119">Change the values for ScaleBreakStyle properties, such as BreakLineType and Spacing.</span></span> <span data-ttu-id="02e18-120">배율 구분선 속성에 대한 자세한 내용은 [차트에 데이터 범위가 여러 개 있는 계열 표시&#40;보고서 작성기 및 SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="02e18-120">For more information about scale break properties, see [Displaying a Series with Multiple Data Ranges on a Chart &#40;Report Builder and SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e18-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02e18-121">See Also</span></span>  
 <span data-ttu-id="02e18-122">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02e18-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02e18-123">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02e18-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="02e18-124">축 속성 대화 상자, 축 옵션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="02e18-124">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
