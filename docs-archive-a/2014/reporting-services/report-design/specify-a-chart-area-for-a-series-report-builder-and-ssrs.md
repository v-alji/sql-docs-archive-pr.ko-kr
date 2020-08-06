---
title: 계열에 대한 차트 영역 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483bc6d2fa4aa079c95e9dbd03e18c71d7b13abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639281"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a><span data-ttu-id="ed1a8-102">계열에 대한 차트 영역 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ed1a8-102">Specify a Chart Area for a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ed1a8-103">차트는 외부 테두리, 차트 제목 및 범례를 포함하는 최상위 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-103">The chart is the top-level container that includes the outer border, the chart title, and the legend.</span></span> <span data-ttu-id="ed1a8-104">기본적으로 차트에는 한 개의 기본 차트 영역이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-104">By default, the chart contains one default chart area.</span></span> <span data-ttu-id="ed1a8-105">차트 영역은 차트 화면에는 표시되지 않지만 하나 이상의 계열에 대한 축 레이블, 축 제목 및 그리기 영역만을 포함하는 컨테이너로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-105">The chart area is not visible on the chart surface, but you can think of the chart area as a container that encompasses only the axis labels, the axis title and the plotting area of one or more series.</span></span> <span data-ttu-id="ed1a8-106">다음 그림에서는 단일 차트 내 차트 영역의 개념을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-106">The following illustration shows the concept of chart areas within a single chart.</span></span>  
  
 <span data-ttu-id="ed1a8-107">![차트 영역의 다이어그램 표시](../media/chartareasdiagram.gif "차트 영역의 다이어그램 표시")</span><span class="sxs-lookup"><span data-stu-id="ed1a8-107">![Shows a diagram of a chart area](../media/chartareasdiagram.gif "Shows a diagram of a chart area")</span></span>  
  
 <span data-ttu-id="ed1a8-108">기본적으로 모든 계열이 기본 차트 영역에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-108">By default, all series are added to the default chart area.</span></span> <span data-ttu-id="ed1a8-109">영역형, 세로 막대형, 꺾은선형 또는 분산형 차트를 사용할 때는 이러한 계열을 조합하여 같은 차트 영역에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-109">When using area, column, line, and scatter charts, any combination of these series can be displayed on the same chart area.</span></span> <span data-ttu-id="ed1a8-110">같은 차트 영역에 여러 계열이 있는 경우 차트의 가독성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-110">If you have several series in the same chart area, the readability of the chart is reduced.</span></span> <span data-ttu-id="ed1a8-111">이 경우 차트 종류를 여러 차트 영역으로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-111">You may want to separate the chart types into multiple chart areas.</span></span> <span data-ttu-id="ed1a8-112">여러 차트 영역을 사용하면 가독성이 높아져 손쉽게 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-112">Using multiple chart areas will increase readability for easier comparisons.</span></span> <span data-ttu-id="ed1a8-113">예를 들어 가격/거래량 주식형 차트는 보통 서로 다른 값의 범위를 포함하지만 같은 기간 동안의 가격 및 거래량을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-113">For example, price-volume stock charts often have different ranges of values, but comparisons can be made between the price and volume data over the same period of time.</span></span>  
  
 <span data-ttu-id="ed1a8-114">가로 막대형, 극좌표형 또는 셰이프 계열만 동일한 차트 영역에 있는 같은 차트 종류의 계열과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-114">The bar, polar, or shape series can only be combined with series of the same chart types in the same chart area.</span></span> <span data-ttu-id="ed1a8-115">극좌표형 또는 셰이프 차트를 사용하는 경우 표시할 필드마다 별도의 차트 데이터 영역을 사용하는 방법을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-115">If you are using a Polar or Shape chart, consider using a separate chart data region for each field that you wish to show.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a><span data-ttu-id="ed1a8-116">계열과 새 차트 영역을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ed1a8-116">To associate a series with a new chart area</span></span>  
  
1.  <span data-ttu-id="ed1a8-117">차트의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **새 차트 영역 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-117">Right-click anywhere on the chart and select **Add New Chart Area**.</span></span> <span data-ttu-id="ed1a8-118">새로운 빈 차트가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-118">A new, blank chart area appears on the chart.</span></span>  
  
2.  <span data-ttu-id="ed1a8-119">차트에서 계열을 마우스 오른쪽 단추로 클릭하거나 차트 데이터 창의 해당하는 영역에서 계열 또는 데이터 필드를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-119">Right-click the series on the chart or right-click a series or data field in the appropriate area in the Chart Data pane, and then click **Series Properties**.</span></span>  
  
3.  <span data-ttu-id="ed1a8-120">**축 및 차트 영역**에서 계열을 표시할 차트 영역을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-120">In **Axes and Chart Areas**, select the chart area that you want the series to be shown in.</span></span>  
  
4.  <span data-ttu-id="ed1a8-121">(옵션) 차트 영역을 세로로 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-121">(Optional) Align the chart areas vertically.</span></span> <span data-ttu-id="ed1a8-122">이렇게 하려면 차트를 마우스 오른쪽 단추로 클릭하고 **차트 영역 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-122">To do this, right-click the chart and select **Chart Area Properties**.</span></span> <span data-ttu-id="ed1a8-123">**맞춤**에서, 선택한 차트 영역과 맞출 다른 차트 영역을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed1a8-123">In **Alignment**, select another chart area that you want to align the selected chart area with.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1a8-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed1a8-124">See Also</span></span>  
 <span data-ttu-id="ed1a8-125">[차트의 여러 계열&#40;보고서 작성기 및 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed1a8-125">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ed1a8-126">[차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed1a8-126">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ed1a8-127">[색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed1a8-127">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ed1a8-128">[극좌표형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed1a8-128">[Polar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ed1a8-129">[셰이프 차트&#40;보고서 작성기 및 SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed1a8-129">[Shape Charts &#40;Report Builder and SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ed1a8-130">원형 차트 &#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed1a8-130">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
