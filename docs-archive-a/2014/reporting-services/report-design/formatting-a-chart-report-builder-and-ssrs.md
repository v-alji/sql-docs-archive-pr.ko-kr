---
title: 차트 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af164d4db9b6439f0634d113652b95939827b0f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649381"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="84519-102">차트 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="84519-102">Formatting a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="84519-103">차트용 데이터를 정의한 후 차트가 원하는 대로 표시되면 서식을 추가하여 전반적인 차트 모양을 향상시키고 중요한 데이터 요소를 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-103">After you have defined the data for your chart and it is appearing the way you want, you can add formatting to improve the overall appearance and highlight key data points.</span></span> <span data-ttu-id="84519-104">가장 일반적인 서식 지정 옵션은 차트 요소를 마우스 오른쪽 단추로 클릭하여 표시되는 바로 가기 메뉴에서 제공되는 속성 대화 상자에서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-104">The most common formatting options can be modified from the Properties dialog box that are found when you right-click a chart element to display its shortcut menu.</span></span> <span data-ttu-id="84519-105">각 차트 요소에는 자체 대화 상자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-105">Each chart element has its own dialog box.</span></span> <span data-ttu-id="84519-106">차트 요소에 대한 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84519-106">For more information about chart elements, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="84519-107">차트와 관련된 모든 속성은 속성 창에 있지만 이들 중 많은 속성은 대화 상자에서도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-107">All properties that relate to the chart are located in the Properties pane, but many of these properties can also be set from a dialog box.</span></span> <span data-ttu-id="84519-108">계열에 서식을 지정하는 경우 속성 창의 **CustomAttributes** 속성 범주에만 있는 사용자 지정 특성을 사용하여 계열 관련 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-108">If you are formatting the series, you can specify series-specific properties using custom attributes, which can only be found in the **CustomAttributes** category of properties, located in the Properties pane.</span></span>  
  
 <span data-ttu-id="84519-109">최소한의 단계를 사용하여 효과적으로 차트에 서식을 지정하려면 기본 테두리 스타일, 색상표 및 그리기 스타일을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="84519-109">To effectively format the chart using a minimal number of steps, change the default border style, palette and drawing style.</span></span> <span data-ttu-id="84519-110">이 세 가지 기능은 차트에서 시각적으로 가장 큰 변화를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-110">These three features produce the largest visible change on the chart.</span></span> <span data-ttu-id="84519-111">그리기 스타일은 원형, 도넛형, 가로 막대형 및 세로 막대형 차트에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84519-111">Drawing styles are only applicable to pie, doughnut, bar and column charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="84519-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="84519-112">In This Section</span></span>  
 [<span data-ttu-id="84519-113">차트에서 계열 색 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-113">Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="84519-114">색상표를 사용하여 색을 정의하고 고유한 색상표를 정의하고 식을 기반으로 색을 정의하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-114">Discusses how colors are defined using a palette, how you can define your own color palette, and how to define colors based on an expression.</span></span>  
  
 [<span data-ttu-id="84519-115">차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-115">Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="84519-116">눈금선, 눈금 표시, 제목을 표시하는 방법과 축 눈금의 숫자와 날짜에 서식을 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-116">Discusses how to display gridlines, tick marks, and titles, and how to format numbers and dates on the axis scale.</span></span>  
  
 [<span data-ttu-id="84519-117">차트의 범례 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-117">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
 <span data-ttu-id="84519-118">차트 범례에서 항목 순서를 바꾸고 서식을 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-118">Discusses how to re-order and format items in the chart legend.</span></span>  
  
 [<span data-ttu-id="84519-119">차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-119">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="84519-120">데이터 요소 레이블의 위치를 지정하고 차트의 모든 계열에 대한 데이터 요소 표식에 서식을 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-120">Discusses how to position data point labels and format data point markers for every series on the chart.</span></span>  
  
 [<span data-ttu-id="84519-121">차트의 3D, 빗면 및 기타 효과&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-121">3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-3d-bevel-and-other-report-builder.md)  
 <span data-ttu-id="84519-122">차트에 적용할 수 있는 다양한 3D 효과를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-122">Discusses various 3D effects that you can apply to a chart.</span></span>  
  
 [<span data-ttu-id="84519-123">차트에 테두리 프레임 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-123">Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="84519-124">차트에 테두리 프레임을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84519-124">Explains how to add a border frame to a chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84519-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84519-125">See Also</span></span>  
 <span data-ttu-id="84519-126">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84519-126">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="84519-127">[차트에 테두리 프레임 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84519-127">[Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="84519-128">[색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84519-128">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="84519-129">차트에 3D 가장자리, 볼록 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84519-129">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
