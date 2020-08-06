---
title: 차트에서 계열 색 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql12.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql12.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0e4f526e32ba38b94c5707c1ce3acc3cd073626
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727996"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="6f0df-102">차트에서 계열 색 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6f0df-102">Formatting Series Colors on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6f0df-103">Reporting Services는 차트에 여러 개의 기본 제공 색상표를 제공하며, 사용자가 사용자 지정 색상표를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-103">Reporting Services provides several built-in palettes for charts, or you can define a custom palette.</span></span> <span data-ttu-id="6f0df-104">기본적으로 차트는 기본 제공 **BrightPastel** 색상표를 사용 하 여 각 계열을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-104">By default, charts use the built-in **BrightPastel** color palette to fill each series.</span></span> <span data-ttu-id="6f0df-105">이 색은 범례에도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-105">These colors also appear in the legend.</span></span> <span data-ttu-id="6f0df-106">차트에 여러 개의 계열이 추가될 때는 색상표에서 색을 정의한 순서대로 차트가 계열에 색을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-106">When multiple series are added to the chart, the chart assigns the series a color in the order that the colors have been defined in the palette.</span></span>  
  
 <span data-ttu-id="6f0df-107">색상표에 있는 색보다 계열 수가 더 많을 경우 차트는 색을 다시 사용하므로 두 계열의 색이 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-107">If there are a greater number of series than there are colors in the palette, the chart will begin reusing colors, and two series may have the same color.</span></span> <span data-ttu-id="6f0df-108">각 데이터 요소에 색상표의 색이 할당되는 셰이프 차트를 사용하는 경우에 이러한 상황이 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-108">This frequently occurs if you are using a Shape chart, where each data point is assigned a color from the palette.</span></span> <span data-ttu-id="6f0df-109">혼동을 피하려면 적어도 차트에 있는 계열 수만큼의 색이 있는 사용자 지정 색상표를 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f0df-109">To avoid confusion, define a custom palette with at least the same number of colors as you have series on your chart.</span></span>  
  
 <span data-ttu-id="6f0df-110">속성 창에서 새 색상표를 선택하거나 사용자 지정 색상표를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-110">You can select a new palette or define a custom palette from the Properties pane.</span></span> <span data-ttu-id="6f0df-111">자세한 내용은 [색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0df-111">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a><span data-ttu-id="6f0df-112">기본 제공 색상표 사용</span><span class="sxs-lookup"><span data-stu-id="6f0df-112">Using Built-In Palettes</span></span>  
 <span data-ttu-id="6f0df-113">Reporting Services에는 차트의 계열에 대한 색 집합을 정의하는 데 사용할 수 있는 미리 정의된 기본 제공 색상표 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-113">Reporting Services provides a list of predefined, built-in palettes that you can use to define a color set for series on your chart.</span></span> <span data-ttu-id="6f0df-114">모든 기본 제공 색상표에는 10 - 16개의 색 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-114">All built-in palettes contain between 10 and 16 color values.</span></span> <span data-ttu-id="6f0df-115">더 많은 색을 포함하도록 기본 제공 색상표를 확장할 수는 없습니다. 따라서 16개가 넘는 색이 필요한 경우에는 사용자 지정 색상표를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-115">You cannot extend the built-in palette to include more colors, so if you need more than 16 colors, you must define a custom palette.</span></span>  
  
 <span data-ttu-id="6f0df-116">보고서를 인쇄하는 경우 **회색조** 색상표를 사용하는 것을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="6f0df-116">If you are printing a report, consider using the **Greyscale** palette.</span></span> <span data-ttu-id="6f0df-117">이 색상표는 흑백 음영을 사용하여 차트에서 각 계열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-117">This palette uses shades of black and white to represent each series in a chart.</span></span>  
  
 <span data-ttu-id="6f0df-118">이전 버전의 Reporting Services에서는 기본값으로 지정된 색상표가 기본 차트 색상표로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-118">The palette named Default was used as the default chart palette in earlier versions of Reporting Services.</span></span> <span data-ttu-id="6f0df-119">이 색상표는 일관성을 위해 같은 이름으로 계속 사용되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-119">It has been maintained with the same name for consistency.</span></span> <span data-ttu-id="6f0df-120">기본 색상표를 사용해도 차트를 원활하게 업그레이드할 수 있지만, 업그레이드한 후에 변경이 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-120">Charts will upgrade seamlessly using the Default palette, but after upgrading, you might consider changing it.</span></span>  
  
## <a name="using-custom-palettes"></a><span data-ttu-id="6f0df-121">사용자 지정 색상표 사용</span><span class="sxs-lookup"><span data-stu-id="6f0df-121">Using Custom Palettes</span></span>  
 <span data-ttu-id="6f0df-122">차트에 자신만의 색을 적용하려면 사용자 지정 색상표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-122">If you want to apply your own colors to the chart, use a custom palette.</span></span> <span data-ttu-id="6f0df-123">사용자 지정 색상표를 사용하면 자신만의 색을 차트에 표시할 순서대로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-123">A custom palette let you add your own colors in the order you want them to appear on the chart.</span></span> <span data-ttu-id="6f0df-124">사용자 지정 색상표는 디자인할 때 차트에 있는 계열의 수를 알 수 없는 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-124">A custom palette is especially helpful if the number of series in your chart is unknown at design time.</span></span> <span data-ttu-id="6f0df-125">자세한 내용은 [색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f0df-125">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-a-color-fill-on-each-series"></a><span data-ttu-id="6f0df-126">각 계열에 색 채우기 사용</span><span class="sxs-lookup"><span data-stu-id="6f0df-126">Using a Color Fill on Each Series</span></span>  
 <span data-ttu-id="6f0df-127">차트에 있는 각 계열에 대한 색을 지정하여 자신만의 색을 차트에 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-127">You can also define your own colors on the chart by specifying a color for each series on the chart.</span></span> <span data-ttu-id="6f0df-128">이렇게 하려면 **계열 속성** 대화 상자를 열고 **채우기** 의 **색**속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-128">To do this, open the **Series Properties** dialog box and set the **Color** property for **Fill**.</span></span> <span data-ttu-id="6f0df-129">이 방법은 모든 정의된 색상표를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-129">This approach will override all defined palettes.</span></span> <span data-ttu-id="6f0df-130">일반적으로 보고서 처리 전까지는 데이터 세트에 있는 계열 수를 알지 못할 수도 있기 때문에 사용자 지정 색상표를 사용하여 자신만의 색을 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-130">Generally, it is better to use a custom palette to define your own colors because the number of series in your dataset may not be known until report processing.</span></span>  
  
 <span data-ttu-id="6f0df-131">이 방법은 식을 기준으로 계열의 색을 조건부로 설정할 때 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-131">This approach is best suited when you want to conditionally set the color of the series based on an expression.</span></span>  <span data-ttu-id="6f0df-132">자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6f0df-132">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f0df-133">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6f0df-133">In This Section</span></span>  
 [<span data-ttu-id="6f0df-134">여러 셰이프 차트에 일관된 색 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6f0df-134">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="6f0df-135">[색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md))</span><span class="sxs-lookup"><span data-stu-id="6f0df-135">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md))</span></span>  
  
 [<span data-ttu-id="6f0df-136">줄무늬 선을 추가하여 차트 데이터 강조 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6f0df-136">Highlight Chart Data by Adding Strip Lines &#40;Report Builder and SSRS&#41;</span></span>](highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f0df-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f0df-137">See Also</span></span>  
 <span data-ttu-id="6f0df-138">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6f0df-138">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6f0df-139">[차트에 3D 가장자리, 볼록 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="6f0df-139">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="6f0df-140">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6f0df-140">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6f0df-141">차트의 범례 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6f0df-141">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
  
  
