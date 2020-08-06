---
title: 차트의 3D, 빗면 및 기타 효과(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10156"
ms.assetid: 18ef2119-2931-43ae-9078-f39b460462dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f505a0226d1c95a1c0c7c3caffde2be60f407b43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659841"
---
# <a name="3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="7b10c-102">차트의 3D, 빗면 및 기타 효과(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7b10c-102">3D, Bevel, and Other Effects in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7b10c-103">3D(3차원) 효과를 사용하여 차트에 깊이를 더하고 시각적 효과를 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="7b10c-104">예를 들어 쪼개진 원형 차트에서 특정 조각을 강조하려는 경우 차트를 돌려 원근감을 변경함으로써 해당 조각이 가장 먼저 보이도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="7b10c-105">차트에 3D 효과를 적용할 경우 모든 그라데이션 색과 해칭 스타일이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
 <span data-ttu-id="7b10c-106">3차원 효과는 개별 차트에 적용할 수 있으며, 동일 보고서에서 2차원 및 3차원 차트를 모두 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-106">Three-dimensional effects can be applied to individual charts, and it is possible to display both two-dimensional and three-dimensional charts on the same report.</span></span>  
  
 <span data-ttu-id="7b10c-107">**3D 사용** 을 선택하면 모든 차트 종류에 대해 **차트 영역 속성**대화 상자의 차트 영역에 3차원 효과를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-107">For all chart types, you can add three-dimensional effects to a chart area in the **Chart Area Properties** dialog box by selecting **Enable 3D**.</span></span> <span data-ttu-id="7b10c-108">자세한 내용은 [차트에 3D 효과 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)대화 상자의 차트 영역에 3차원 효과를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-108">For more information, see [Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-3d-effects-report-builder.md).</span></span>  
  
 <span data-ttu-id="7b10c-109">가로 막대형 차트, 세로 막대형 차트, 원형 차트 및 도넛형 차트에 빗면 효과, 볼록 효과 및 질감 스타일을 추가하여 차트에 시각적 효과를 줄 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-109">Another way to add visual impact to charts is by adding bevel, emboss and texture styles in bar, column, pie and doughnut charts.</span></span> <span data-ttu-id="7b10c-110">자세한 내용은 [차트에 빗면 효과, 볼록 효과 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b10c-110">For more information, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="coordinate-based-three-dimensional-charts"></a><span data-ttu-id="7b10c-111">좌표 기반 3차원 차트</span><span class="sxs-lookup"><span data-stu-id="7b10c-111">Coordinate-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="7b10c-112">좌표 기반 차트 종류(세로 막대형, 가로 막대형, 영역형, 점, 꺾은선형 및 범위형)를 사용할 경우 3차원 효과를 적용하면 "z축"이라는 세 번째 축이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-112">When working with coordinate-based chart types (Column, Bar, Area, Point, Line and Range), three-dimensional effects display the chart with a third axis, known as the "z-axis".</span></span> <span data-ttu-id="7b10c-113">이 세 번째 축을 사용하면 차트에 다양한 시각적 효과를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-113">The introduction of this third axis allows you to apply a variety of visual enhancements to your chart.</span></span>  
  
### <a name="changing-the-white-space-in-a-3d-chart"></a><span data-ttu-id="7b10c-114">3D 차트에서 공백 변경</span><span class="sxs-lookup"><span data-stu-id="7b10c-114">Changing the White Space in a 3D Chart</span></span>  
 <span data-ttu-id="7b10c-115">3차원 모드로 차트 영역을 표시할 때 각 계열은 차트의 z축을 따라 개별 행으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-115">When you display a chart area in three-dimensional mode, each series is shown in a separate row along the z-axis of the chart.</span></span> <span data-ttu-id="7b10c-116">각 계열 간의 간격을 변경하려면 3D 효과 대화 상자의 **요소 간격 깊이** 속성을 변경하여 차트의 요소 간격 깊이를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-116">To change the amount of space between each series, modify the chart's point gap depth by changing the **Point Gap Depth** property in the 3D Effects dialog box.</span></span>  
  
### <a name="changing-the-projection-of-a-3d-chart"></a><span data-ttu-id="7b10c-117">3D 차트의 투영 변경</span><span class="sxs-lookup"><span data-stu-id="7b10c-117">Changing the Projection of a 3D Chart</span></span>  
 <span data-ttu-id="7b10c-118">3D 투영에는 오블리크 투영과 큐브 뷰 투영이라는 두 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-118">There are two types of 3D projections: oblique and perspective.</span></span> <span data-ttu-id="7b10c-119">차트에 오블리크 투영을 사용하면 2차원 차트에 깊이 차원이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-119">An oblique projection to the chart adds a depth dimension to a two-dimensional chart.</span></span> <span data-ttu-id="7b10c-120">z축은 가로 축과 세로 축에서 동일한 각도로 그려지며 2차원 차트에서와 같이 상호 수직 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-120">The z-axis is drawn at equal angles from the horizontal and vertical axes, which remain perpendicular to each other just as in a two-dimensional chart.</span></span>  
  
 <span data-ttu-id="7b10c-121">큐브 뷰 투영은 해당 시점에서 바라보는 것처럼 뷰 평면을 예측하고 다시 그려 차트를 변형시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-121">Perspective projection transforms the chart by estimating a view plane and re-drawing the chart as if it were being viewed from that point.</span></span> <span data-ttu-id="7b10c-122">**회전** 값은 뷰를 수평(0도)에서 수직(90도)까지 세로로 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-122">The **Rotation** value shifts the view vertically from "ground level" at 0 to overhead at 90.</span></span> <span data-ttu-id="7b10c-123">**기울기** 값은 시점 각도를 왼쪽 또는 오른쪽으로 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-123">The **Inclination** value shifts the viewing angle to the left or right.</span></span> <span data-ttu-id="7b10c-124">0 값은 차트를 2차원으로 볼 때와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-124">A value of 0 is equivalent to a two-dimensional view of the chart.</span></span> <span data-ttu-id="7b10c-125">**큐브 뷰** 값은 투영을 표시할 때 사용되는 왜곡의 비율을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-125">The **Perspective** value defines the percentage of distortion that will be used when displaying the projection.</span></span> <span data-ttu-id="7b10c-126">이 유형의 투영에서는 차트의 비례는 유지되지만 차트의 모양이 왜곡되므로 낮은 큐브 뷰를 사용하는 것이 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-126">This type of projection maintains the proportions of your chart, but the chart's appearance becomes distorted, so it is most effective to use a lower degree of perspective.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b10c-127">오블리크 및 큐브 뷰 투영은 서로 별개의 투영 유형이므로 동일 차트에서 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-127">The oblique and perspective projections are separate types of projections, so they cannot be used together on the same chart.</span></span>  
  
### <a name="clustering-data"></a><span data-ttu-id="7b10c-128">데이터 클러스터링</span><span class="sxs-lookup"><span data-stu-id="7b10c-128">Clustering Data</span></span>  
 <span data-ttu-id="7b10c-129">2D 차트에서는 여러 데이터 계열이 나란히 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-129">In 2D charts, multiple series of data appear side-by-side.</span></span> <span data-ttu-id="7b10c-130">클러스터링은 3D 차트에서 각 계열을 별도의 행으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-130">Clustering shows individual series in separate rows on a 3D chart.</span></span> <span data-ttu-id="7b10c-131">예를 들어 3개의 데이터 요소 계열을 포함하는 차트에서 클러스터링을 사용하면 이 3개의 각 계열이 z축을 따라 별도의 행에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-131">For example, if you have a chart that contains three series of data points, clustering will display each of the three series on a separate row along the z-axis.</span></span> <span data-ttu-id="7b10c-132">기본적으로 3D로 표시되는 모든 차트 종류에는 클러스터링이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-132">By default, all chart types shown in 3D are clustered.</span></span>  
  
 <span data-ttu-id="7b10c-133">가로 막대형 및 세로 막대형 차트에서는 클러스터링을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-133">Clustering can be disabled for bar and column charts.</span></span> <span data-ttu-id="7b10c-134">클러스터링을 해제하면 여러 가로 막대 및 세로 막대 계열이 하나의 행으로 나란히 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-134">When clustering is disabled, multiple bar and column series are displayed side-by-side in one row.</span></span>  
  
## <a name="shape-based-three-dimensional-charts"></a><span data-ttu-id="7b10c-135">셰이프 기반 3차원 차트</span><span class="sxs-lookup"><span data-stu-id="7b10c-135">Shape-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="7b10c-136">셰이프 기반 차트 종류(원형, 도넛형, 깔때기형, 피라미드형)의 경우 사용할 수 있는 3차원 효과의 수가 더 적습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-136">Shape-based chart types (Pie, Doughnut, Funnel, Pyramid) have fewer three-dimensional effects available.</span></span> <span data-ttu-id="7b10c-137">셰이프 기반 차트 종류를 사용할 때는 회전 및 기울기 값만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-137">When working with shape-based chart types, you can change the rotation and inclination values only.</span></span>  
  
## <a name="rotations"></a><span data-ttu-id="7b10c-138">회전</span><span class="sxs-lookup"><span data-stu-id="7b10c-138">Rotations</span></span>  
 <span data-ttu-id="7b10c-139">차트는 가로 또는 세로로 -90도에서 90도까지 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-139">Charts can be rotated horizontally and vertically from -90 to 90 degrees.</span></span> <span data-ttu-id="7b10c-140">양수 수평 각도는 x축을 따라 시계 반대 방향으로 차트를 회전시키고, 양수 수직 각도는 y축을 따라 시계 방향으로 차트를 회전시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-140">A positive horizontal angle will rotate the chart counter-clockwise around the x-axis, while a positive vertical angle will rotate the chart clockwise around the y-axis.</span></span>  
  
## <a name="highlighting-3d-effects"></a><span data-ttu-id="7b10c-141">3D 효과 강조</span><span class="sxs-lookup"><span data-stu-id="7b10c-141">Highlighting 3D Effects</span></span>  
 <span data-ttu-id="7b10c-142">**음영** 속성을 통해 3D 차트에 강조 스타일을 추가할 수 있습니다. 이 속성은 차트 영역을 선택할 때 속성 창에 있는 Area3DStyle 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-142">You can add highlighting styles to a 3D chart via the **Shading** property, which appears under Area3DStyle in the Properties pane when the chart area is selected.</span></span> <span data-ttu-id="7b10c-143">단순 조명 스타일은 차트 영역 요소에 동일한 색상을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-143">A simple lighting style applies the same hue to the chart area elements.</span></span> <span data-ttu-id="7b10c-144">현실적인 스타일은 지정된 조명 각도에 따라 차트 영역 요소의 색상을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7b10c-144">A realistic style changes the hues of the chart area elements depending on a specified lighting angle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b10c-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b10c-145">See Also</span></span>  
 <span data-ttu-id="7b10c-146">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7b10c-146">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7b10c-147">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7b10c-147">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7b10c-148">차트에 3D 효과 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7b10c-148">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
