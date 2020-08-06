---
title: 차트에 3D 효과 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4fcd90452e32b760bc446ac5d085ed00520a2f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659840"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="36e21-102">차트에 3D 효과 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="36e21-102">Add 3D Effects to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="36e21-103">3D(3차원) 효과를 사용하여 차트에 깊이를 더하고 시각적 효과를 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="36e21-104">예를 들어 쪼개진 원형 차트에서 특정 조각을 강조하려는 경우 차트를 돌려 원근감을 변경함으로써 해당 조각이 가장 먼저 보이도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="36e21-105">차트에 3D 효과를 적용할 경우 모든 그라데이션 색과 해칭 스타일이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a><span data-ttu-id="36e21-106">범위형, 영역형, 꺾은선형, 분산형 또는 극좌표형 차트에 3D 효과를 적용하려면</span><span class="sxs-lookup"><span data-stu-id="36e21-106">To apply 3D effects to a Range, Area, Line, Scatter or Polar chart</span></span>  
  
1.  <span data-ttu-id="36e21-107">차트 영역의 아무 위치나 마우스 오른쪽 단추로 클릭하고 **3D 효과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-107">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="36e21-108">**차트 영역 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-108">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="36e21-109">**3D 옵션**에서 **3D 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-109">In **3D Options**, select the **Enable 3D** option.</span></span>  
  
3.  <span data-ttu-id="36e21-110">(옵션) **3D 옵션**에서 3D 각도 및 장면 옵션과 관련된 다양한 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-110">(Optional) In **3D Options**, you can set a variety of properties relating to 3D angles and scene options.</span></span> <span data-ttu-id="36e21-111">이러한 속성에 대한 자세한 내용은 [차트의 3D, 빗면 및 기타 효과&#40;보고서 작성기 및 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-111">For more information about these properties, see [3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).</span></span>  
  
4.  <span data-ttu-id="36e21-112">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-112">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a><span data-ttu-id="36e21-113">깔때기형 차트에 3D 효과를 적용하려면</span><span class="sxs-lookup"><span data-stu-id="36e21-113">To apply 3D effects to a Funnel chart</span></span>  
  
1.  <span data-ttu-id="36e21-114">차트 영역의 아무 위치나 마우스 오른쪽 단추로 클릭하고 **3D 효과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-114">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="36e21-115">**차트 영역 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-115">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="36e21-116">**3D 옵션**에서 **3D 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-116">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="36e21-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-117">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="36e21-118">(옵션) 깔때기형 차트의 시각적 모양을 사용자 지정하려면 속성 창으로 이동하여 깔때기형 차트에 관련된 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-118">(Optional) To customize the funnel chart visual appearance, you can go to the Properties pane and change properties specific to the funnel chart.</span></span>  
  
    1.  <span data-ttu-id="36e21-119">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-119">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="36e21-120">디자인 화면에서 깔때기형 차트의 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-120">On the design surface, click anywhere on the funnel.</span></span> <span data-ttu-id="36e21-121">깔때기형 차트의 계열에 대한 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-121">The properties for the series of the funnel chart are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="36e21-122">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-122">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="36e21-123">**Funnel3DDrawingStyle** 속성에서 깔때기형 차트를 원형으로 표시할지 사각형으로 표시할지 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-123">For the **Funnel3DDrawingStyle** property, select whether the funnel will be shown with as circular or square.</span></span>  
  
    5.  <span data-ttu-id="36e21-124">**Funnel3DRotationAngle** 속성에 대해 -10에서 10 사이의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-124">For the **Funnel3DRotationAngle** property, set a value between -10 and 10.</span></span> <span data-ttu-id="36e21-125">이 값은 3D 깔때기형 차트에 표시될 기울기 정도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-125">This will determine the degree of tilt that will be displayed on the 3D funnel chart.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a><span data-ttu-id="36e21-126">원형 차트에 3D 효과를 적용하려면</span><span class="sxs-lookup"><span data-stu-id="36e21-126">To apply 3D effects to a Pie chart</span></span>  
  
1.  <span data-ttu-id="36e21-127">차트 영역의 아무 위치나 마우스 오른쪽 단추로 클릭하고 3D 효과를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-127">Right-click anywhere inside the chart area and select 3D Effects.</span></span> <span data-ttu-id="36e21-128">**차트 영역 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-128">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="36e21-129">**3D 옵션**에서 **3D 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-129">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="36e21-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-130">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="36e21-131">(옵션) **회전**에 원형 차트의 수평 회전을 나타내는 정수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-131">(Optional) In **Rotation**, type an integer value that represents the horizontal rotation of the pie chart.</span></span>  
  
4.  <span data-ttu-id="36e21-132">(옵션) **기울기**에 원형 차트의 수직 기울기 회전을 나타내는 정수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-132">(Optional) In **Inclination**, type an integer value that represents the vertical tilt rotation of the pie chart.</span></span>  
  
5.  <span data-ttu-id="36e21-133">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-133">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a><span data-ttu-id="36e21-134">가로 막대형 또는 세로 막대형 차트에 3D 효과를 적용하려면</span><span class="sxs-lookup"><span data-stu-id="36e21-134">To apply 3D effects to a Bar or Column chart</span></span>  
  
1.  <span data-ttu-id="36e21-135">차트 영역의 아무 위치나 마우스 오른쪽 단추로 클릭하고 **3D 효과**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-135">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="36e21-136">**차트 영역 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-136">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="36e21-137">**3D 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-137">Select the **Enable 3D** option.</span></span> <span data-ttu-id="36e21-138">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-138">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="36e21-139">(옵션) **계열 클러스터링 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-139">(Optional) Select the **Enable series clustering** option.</span></span> <span data-ttu-id="36e21-140">차트에 여러 개의 가로 막대형 또는 세로 막대형 차트 계열이 포함되어 있는 경우 이 옵션을 선택하면 계열이 클러스터형으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-140">If your chart contains multiple bar or column chart series, this option will display the series as clustered.</span></span> <span data-ttu-id="36e21-141">기본적으로 여러 개의 가로 막대형 또는 세로 막대형 계열이 나란히 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-141">By default, multiple bar or column series are shown side-by-side.</span></span>  
  
4.  <span data-ttu-id="36e21-142">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-142">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="36e21-143">(옵션) 가로 막대형 또는 세로 막대형 차트에 원통형 효과를 추가하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-143">(Optional) To add cylinder effects to a bar or column chart, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="36e21-144">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-144">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="36e21-145">디자인 화면에서 계열의 가로 막대 중 아무 것이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-145">On the design surface, click any of the bars in the series.</span></span> <span data-ttu-id="36e21-146">계열의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-146">The properties for the series are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="36e21-147">**일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-147">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="36e21-148">**DrawingStyle** 속성에서 **Cylinder** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36e21-148">For the **DrawingStyle** property, specify the **Cylinder** value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e21-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36e21-149">See Also</span></span>  
 <span data-ttu-id="36e21-150">[차트의 3D, 빗면 및 기타 효과&#40;보고서 작성기 및 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="36e21-150">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="36e21-151">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36e21-151">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="36e21-152">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="36e21-152">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
