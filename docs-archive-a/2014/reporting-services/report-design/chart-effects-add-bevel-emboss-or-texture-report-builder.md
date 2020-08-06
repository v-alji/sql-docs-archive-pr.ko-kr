---
title: 차트에 빗면 효과, 볼록 효과 및 질감 스타일 추가(보고서 작성기 및 SSRS)| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92c5d4af47b7889b9ba5ec421706848f8822075b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659837"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="6e3af-102">차트에 빗면 효과, 볼록 효과 및 질감 스타일 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6e3af-102">Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6e3af-103">특정 차트 종류를 사용할 때 그리기 효과를 지정하여 차트의 시각적 효과를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-103">When using certain chart types, you can specify a drawing effect to increase the visual impact of your chart.</span></span> <span data-ttu-id="6e3af-104">이러한 그리기 효과는 차트의 계열에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-104">These drawing effects are only applied to the series of your chart.</span></span> <span data-ttu-id="6e3af-105">다른 차트 요소에는 그리기 효과가 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-105">They have no effect on any other chart element.</span></span>  
  
 <span data-ttu-id="6e3af-106">원형 또는 도넛형 차트의 변형을 사용하는 경우 이미지에 적용할 수 있는 빗면 효과나 볼록 효과와 비슷한 부드러운 가장자리 또는 오목 그리기 스타일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-106">When you are using any variant of a pie or doughnut chart, you can specify a soft edge or concave drawing style, similar to bevel or emboss effects that can be applied to an image.</span></span>  
  
 <span data-ttu-id="6e3af-107">가로 막대형 또는 세로 막대형 차트의 변형을 사용하는 경우 각각의 가로 또는 세로 막대에 원통형, 쐐기형 및 그라데이션 같은 질감 스타일을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-107">When you are using any variant of a bar or column chart, you can apply texture styles, such as cylinder, wedge, and light-to-dark, to the individual bars or columns.</span></span>  
  
 <span data-ttu-id="6e3af-108">이러한 그리기 스타일 이외에도 여러 가지 차트 요소에 테두리와 그림자를 추가하여 깊이감을 더할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-108">In addition to these drawing styles, you can add borders and shadows to many chart elements to give the illusion of depth.</span></span> <span data-ttu-id="6e3af-109">차트의 서식을 지정하는 다른 방법에 대한 자세한 내용은 [차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e3af-109">For more information on other ways to format the chart, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a><span data-ttu-id="6e3af-110">원형 또는 도넛형 차트에 빗면 또는 볼록 스타일을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6e3af-110">To add bevel or emboss styles to a pie or doughnut chart</span></span>  
  
1.  <span data-ttu-id="6e3af-111">**보기** 탭에서 **속성** 을 선택하여 속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-111">On the **View** tab, select **Properties** to open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="6e3af-112">그리기 효과를 적용할 원형 또는 도넛형 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-112">Select the pie or doughnut chart that you want to enhance.</span></span> <span data-ttu-id="6e3af-113">전체 차트가 아니라 차트의 데이터 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-113">Select a data field in the chart, not the entire chart.</span></span>  
  
3.  <span data-ttu-id="6e3af-114">속성 창에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-114">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="6e3af-115">드롭다운 목록에서 PieDrawingStyle에 대한 스타일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-115">For PieDrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e3af-116">3D와 빗면 또는 볼록 스타일을 동일한 차트에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-116">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="6e3af-117">차트에 3D를 사용하도록 설정한 경우 PieDrawingStyle 속성이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-117">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="6e3af-118">![오목 그리기 스타일을 포함하는 원형 차트](../media/rs-piedrawingeffects-concave.gif "오목 그리기 스타일을 포함하는 원형 차트")</span><span class="sxs-lookup"><span data-stu-id="6e3af-118">![Pie chart with concave drawing style](../media/rs-piedrawingeffects-concave.gif "Pie chart with concave drawing style")</span></span>  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a><span data-ttu-id="6e3af-119">가로 막대형 또는 세로 막대형 차트에 질감 스타일을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6e3af-119">To add texture styles to a bar or column chart</span></span>  
  
1.  <span data-ttu-id="6e3af-120">질감 스타일을 적용할 가로 막대형 또는 세로 막대형 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-120">Select the bar or column chart that you want to enhance.</span></span> <span data-ttu-id="6e3af-121">전체 차트가 아니라 차트의 데이터 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-121">Select a data field in the chart, not the entire chart.</span></span>  
  
2.  <span data-ttu-id="6e3af-122">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-122">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="6e3af-123">**CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-123">Expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="6e3af-124">드롭다운 목록에서 DrawingStyle에 대한 스타일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-124">For DrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e3af-125">3D와 빗면 또는 볼록 스타일을 동일한 차트에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-125">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="6e3af-126">차트에 3D를 사용하도록 설정한 경우 PieDrawingStyle 속성이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e3af-126">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="6e3af-127">![LightToDark 그리기 효과를 포함하는 가로 막대형 차트](../media/rs-bardrawingeffects-lighttodark.gif "LightToDark 그리기 효과를 포함하는 가로 막대형 차트")</span><span class="sxs-lookup"><span data-stu-id="6e3af-127">![Bar chart with LightToDark drawing effect](../media/rs-bardrawingeffects-lighttodark.gif "Bar chart with LightToDark drawing effect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3af-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e3af-128">See Also</span></span>  
 <span data-ttu-id="6e3af-129">[가로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e3af-129">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e3af-130">[세로 막대형 차트&#40;보고서 작성기 및 SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e3af-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e3af-131">[원형 차트&#40;보고서 작성기 및 SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e3af-131">[Pie Charts &#40;Report Builder and SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6e3af-132">차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6e3af-132">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
