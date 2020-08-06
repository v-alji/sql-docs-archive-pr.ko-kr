---
title: 지도 범례, 색 눈금 및 관련 규칙 변경 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.maprulesdistribution.f1
- "10512"
- "10539"
- "10533"
- sql12.rtp.rptdesigner.mappointlayerproperties.typerules.f1
- "10534"
- sql12.rtp.rptdesigner.maplegendproperties.general.f1
- sql12.rtp.rptdesigner.mapdistancescaleproperties.general.f1
- "10516"
- sql12.rtp.rptdesigner.mapcolorscaleproperties.labels.f1
- sql12.rtp.rptdesigner.maplegendtitleproperties.general.f1
- "10514"
- sql12.rtp.rptdesigner.shared.mapruleslegend.f1
- sql12.rtp.rptdesigner.mapcolorscaleproperties.general.f1
- sql12.rtp.rptdesigner.shared.embeddedlabels.f1
- "10513"
- sql12.rtp.rptdesigner.mappointlayerproperties.sizerules.f1
- sql12.rtp.rptdesigner.mapcolorscaletitleproperties.general.f1
- "10510"
- "10509"
- "10540"
- "10517"
ms.assetid: a1d691b2-c5ae-420f-af60-b7c54a7385a4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17220c12e672ce49d3c5b1023f2a00db04e7613e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648800"
---
# <a name="change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs"></a><span data-ttu-id="2f589-102">지도 범례, 색 눈금 및 관련 규칙 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2f589-102">Change Map Legends, Color Scale, and Associated Rules (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2f589-103">지도에는 지도 범례, 색 눈금 및 거리 눈금이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-103">A map can contain map legends, a color scale, and a distance scale.</span></span> <span data-ttu-id="2f589-104">이러한 지도 부분은 지도에서 데이터 시각화를 해석하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-104">These parts of a map help users interpret the data visualization on the map.</span></span>  
  
 <span data-ttu-id="2f589-105">범례에는 다음과 같은 지도 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-105">Legends include the following parts of a map:</span></span>  
  
-   <span data-ttu-id="2f589-106">**지도 범례** 지도 계층에 있는 지도 요소의 표시를 변경하는 분석 데이터를 해석하는 데 도움이 되는 지침을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-106">**Map legend** Displays a guide to help interpret the analytical data that varies the display of a map elements on a map layer.</span></span> <span data-ttu-id="2f589-107">하나의 지도에 여러 개의 범례가 있을 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="2f589-107">A map can have multiple legends.</span></span> <span data-ttu-id="2f589-108">각 지도 계층에서 사용할 범례를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-108">For each map layer, you A specify which legend to use.</span></span> <span data-ttu-id="2f589-109">범례에는 둘 이상의 지도 계층에 대한 지침이 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-109">A legend can provide a guide to more than one map layer.</span></span>  
  
-   <span data-ttu-id="2f589-110">**색 눈금** 지도에 표시된 색을 해석하는 데 도움이 되는 지침을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-110">**Color scale** Displays a guide to help interpret colors on the map.</span></span> <span data-ttu-id="2f589-111">각 지도에는 하나의 색 눈금이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-111">A map has one color scale.</span></span> <span data-ttu-id="2f589-112">색 눈금에 대한 데이터는 여러 계층에 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-112">Multiple layers can provide the data for the color scale.</span></span>  
  
-   <span data-ttu-id="2f589-113">**거리 눈금** 지도의 눈금을 해석하는 데 도움이 되는 지침을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-113">**Distance scale** Displays a guide to help interpret the scale of the map.</span></span> <span data-ttu-id="2f589-114">각 지도에는 하나의 거리 눈금이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-114">A map has one distance scale.</span></span> <span data-ttu-id="2f589-115">거리 눈금은 현재 지도 뷰포트 확대/축소 값에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-115">The current map viewport zoom value determines the distance scale.</span></span>  
  
 <span data-ttu-id="2f589-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span><span class="sxs-lookup"><span data-stu-id="2f589-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="2f589-117">뷰포트에 상대적인 범례의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-117">To change the position of a legend relative to the viewport</span></span>  
  
#### <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><span data-ttu-id="2f589-118">뷰포트에 상대적인 범례의 위치를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-118">To change the position of a legend relative to the viewport</span></span>  
  
1.  <span data-ttu-id="2f589-119">디자인 뷰에서 범례를 마우스 오른쪽 단추로 클릭 하 고 _\<report item->_ **속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-119">In Design view, right-click the legend and open the _\<report item->_**Properties** page.</span></span>  
  
2.  <span data-ttu-id="2f589-120">**위치**에서 뷰포트에 상대적인 범례를 표시할 곳을 지정하는 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-120">In **Position**, click the location that specifies where to display the legend relative to the viewport.</span></span>  
  
3.  <span data-ttu-id="2f589-121">뷰포트 외부에 범례를 표시 하려면 \*\* \<report item> 뷰포트 외부에 표시\*\*를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-121">To display the legend outside the viewport, select **Show \<report item> outside viewport**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f589-122">미리 보기에서 지도 범례와 색 눈금은 해당 범례와 관련된 규칙의 결과가 있는 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-122">In preview, map legends and the color scale appear only when there are results from the rules related to that legend.</span></span> <span data-ttu-id="2f589-123">표시할 항목이 없으면 범례가 렌더링된 보고서에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-123">If there are no items to display, the legend does not appear in the rendered report.</span></span>  
  
  
  
##  <a name="to-change-the-layout-of-a-map-legend"></a><a name="MapLegend"></a> <span data-ttu-id="2f589-124">지도 범례의 레이아웃을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-124">To change the layout of a map legend</span></span>  
  
#### <a name="to-change-the-layout-of-a-map-legend"></a><span data-ttu-id="2f589-125">지도 범례의 레이아웃을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-125">To change the layout of a map legend</span></span>  
  
1.  <span data-ttu-id="2f589-126">디자인 뷰에서 범례를 마우스 오른쪽 단추로 클릭하고 **범례 속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-126">In Design view, right-click the legend and open the **Legend Properties** page.</span></span>  
  
2.  <span data-ttu-id="2f589-127">**범례 레이아웃**에서 범례에 사용할 테이블 레이아웃을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-127">In **Legend layout**, click the table layout that you want to use for the legend.</span></span> <span data-ttu-id="2f589-128">다른 옵션을 클릭하면 디자인 화면의 레이아웃이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-128">As you click different options, the layout on the design surface changes.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-show-or-hide-a-map-legend-title"></a><a name="MapLegendTitle"></a> <span data-ttu-id="2f589-129">지도 범례 제목을 표시하거나 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2f589-129">To show or hide a map legend title</span></span>  
  
#### <a name="to-show-or-hide-a-map-legend-title"></a><span data-ttu-id="2f589-130">지도 범례 제목을 표시하거나 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2f589-130">To show or hide a map legend title</span></span>  
  
-   <span data-ttu-id="2f589-131">디자인 화면에서 지도 범례를 마우스 오른쪽 단추로 클릭한 다음 **범례 제목 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-131">Right-click the map legend on the design surface, and then click **Show Legend Title**.</span></span>  
  
  
  
##  <a name="to-show-or-hide-a-color-scale-title"></a><a name="ColorScaleTitle"></a> <span data-ttu-id="2f589-132">색 눈금 제목을 표시하거나 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2f589-132">To show or hide a color scale title</span></span>  
  
#### <a name="to-show-or-hide-a-color-scale-title"></a><span data-ttu-id="2f589-133">색 눈금 제목을 표시하거나 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2f589-133">To show or hide a color scale title</span></span>  
  
-   <span data-ttu-id="2f589-134">디자인 화면에서 색 눈금을 마우스 오른쪽 단추로 클릭한 다음 **색 눈금 제목 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-134">Right-click the color scale on the design surface, and then click **Show Color Scale Title**.</span></span>  
  
  
  
##  <a name="to-move-items-out-of-the-first-legend"></a><a name="MoveItems"></a> <span data-ttu-id="2f589-135">첫 번째 범례에서 항목을 제외하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-135">To move items out of the first legend</span></span>  
 <span data-ttu-id="2f589-136">필요한 만큼 범례를 추가로 만들고 규칙 결과를 표시할 범례를 지정하는 각 지도 계층에 대한 규칙을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-136">Create as many additional legends as you need and then update the rules for each map layer specify which legend to display the rule results in.</span></span>  
  
#### <a name="to-create-a-new-legend"></a><span data-ttu-id="2f589-137">새 범례를 만들려면</span><span class="sxs-lookup"><span data-stu-id="2f589-137">To create a new legend</span></span>  
  
-   <span data-ttu-id="2f589-138">디자인 뷰에서 지도 뷰포트 외부의 지도를 마우스 오른쪽 단추로 클릭한 다음 **범례 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-138">In Design view, right-click the map outside the map viewport, and then click **Add Legend**.</span></span>  
  
     <span data-ttu-id="2f589-139">지도에 새 범례가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-139">A new legend appears on the map.</span></span>  
  
#### <a name="to-display-rule-results-in-a-legend"></a><span data-ttu-id="2f589-140">범례에 규칙 집합을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-140">To display rule results in a legend</span></span>  
  
1.  <span data-ttu-id="2f589-141">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-141">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-142">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-142">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-143">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-143">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="2f589-144">**이 범례에 표시** 드롭다운 목록에서 규칙 결과를 표시할 범례의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-144">In the **Show in this legend** drop-down list, click the name of the legend to display the rule results in.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-a-template-style"></a><a name="TemplateStyle"></a> <span data-ttu-id="2f589-145">템플릿 스타일에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-145">To vary map element colors based on a template style</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-a-template-style"></a><span data-ttu-id="2f589-146">템플릿 스타일에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-146">To vary map element colors based on a template style</span></span>  
  
1.  <span data-ttu-id="2f589-147">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-147">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-148">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-148">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-149">**템플릿 스타일 적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-149">Click **Apply template style**.</span></span>  
  
     <span data-ttu-id="2f589-150">템플릿 스타일은 글꼴, 테두리 스타일 및 색상표를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-150">A template style specifies font, border style, and color palette.</span></span> <span data-ttu-id="2f589-151">각 지도 요소에는 지도 마법사나 지도 계층 마법사에서 지정된 테마에 대한 색상표의 색이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-151">Each map element is assigned a different color from the color palette for the theme that was specified in the Map Wizard or Map Layer Wizard.</span></span> <span data-ttu-id="2f589-152">이것이 분석 데이터가 연결되지 않은 계층에 적용되는 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-152">This is the only option that applies to layers that do not have associated analytical data.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-palette"></a><a name="ColorPalette"></a> <span data-ttu-id="2f589-153">색상표에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-153">To vary map element colors based on color palette</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-palette"></a><span data-ttu-id="2f589-154">색상표에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-154">To vary map element colors based on color palette</span></span>  
  
1.  <span data-ttu-id="2f589-155">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-155">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-156">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-156">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-157">**색상표를 사용하여 데이터 시각화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-157">Click **Visualize data by using color palette**.</span></span>  
  
     <span data-ttu-id="2f589-158">이 옵션은 기본 제공 색상표나 지정한 사용자 지정 색상표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-158">This option uses a built-in or custom palette that you specify.</span></span> <span data-ttu-id="2f589-159">관련된 분석 데이터에 따라 각 지도 요소에는 색상표의 색 음영이나 다른 색이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-159">Based on related analytical data, each map element is assigned a different color or shade of color from the palette.</span></span>  
  
4.  <span data-ttu-id="2f589-160">**데이터 필드**에 색으로 시각화할 분석 데이터가 포함된 필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-160">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="2f589-161">**색상표**의 드롭다운 목록에서 사용할 색상표의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-161">In **Palette**, from the drop-down list, select the name of the palette to use.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-ranges"></a><a name="ColorRanges"></a> <span data-ttu-id="2f589-162">색 범위에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-162">To vary map element colors based on color ranges</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-ranges"></a><span data-ttu-id="2f589-163">색 범위에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-163">To vary map element colors based on color ranges</span></span>  
  
1.  <span data-ttu-id="2f589-164">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-164">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-165">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-165">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-166">**색 범위를 사용하여 데이터 시각화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-166">Click **Visualize data by using color ranges**.</span></span>  
  
     <span data-ttu-id="2f589-167">이 옵션은 이 페이지에서 지정하는 시작, 중간 및 마지막 색과 **분포** 페이지에서 지정하는 옵션과 결합되어 관련 분석 데이터를 범위로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-167">This option, combined with the start, middle, and end colors that you specify on this page and the options that you specify on the **Distribution** page, divide the related analytical data into ranges.</span></span> <span data-ttu-id="2f589-168">보고서 처리기는 연결된 데이터와 속한 범위에 따라 각 지도 요소에 적절한 색을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-168">The report processor assigns the appropriate color to each map element based on the its associated data and the range that it falls into.</span></span>  
  
4.  <span data-ttu-id="2f589-169">**데이터 필드**에 색으로 시각화할 분석 데이터가 포함된 필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-169">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="2f589-170">**시작 색**에서 가장 작은 범위에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-170">In **Start color**, specify the color to use for the lowest range.</span></span>  
  
6.  <span data-ttu-id="2f589-171">**중간 색**에서 중간 범위에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-171">In **Middle color**, specify the color to use for the middle range.</span></span>  
  
7.  <span data-ttu-id="2f589-172">**마지막 색**에서 가장 큰 범위에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-172">In **End color**, specify the color to use for the highest range.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-custom-colors"></a><a name="CustomColors"></a> <span data-ttu-id="2f589-173">사용자 지정 색에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-173">To vary map element colors based on custom colors</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-custom-colors"></a><span data-ttu-id="2f589-174">사용자 지정 색에 따라 지도 요소 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-174">To vary map element colors based on custom colors</span></span>  
  
1.  <span data-ttu-id="2f589-175">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-175">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-176">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-176">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-177">**사용자 지정 색을 사용하여 데이터 시각화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-177">Click **Visualize data by using custom colors**.</span></span>  
  
     <span data-ttu-id="2f589-178">이 옵션은 지정한 색 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-178">This option uses the list of colors that you specify.</span></span> <span data-ttu-id="2f589-179">관련된 분석 데이터에 따라 각 지도 요소에는 목록의 색이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-179">Based on related analytical data, each map element is assigned a color from the list.</span></span> <span data-ttu-id="2f589-180">색보다 많은 지도 요소가 있으면 색이 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-180">If there are more map elements than colors, no color is assigned.</span></span>  
  
4.  <span data-ttu-id="2f589-181">**데이터 필드**에 색으로 시각화할 분석 데이터가 포함된 필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-181">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="2f589-182">**사용자 지정 색**에서 **추가** 를 클릭하여 각 사용자 지정 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-182">In **Custom colors**, click **Add** to specify each custom color.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-set-distribution-options-for-a-legend"></a><a name="DistributionOptions"></a> <span data-ttu-id="2f589-183">범례의 분포 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-183">To set distribution options for a legend</span></span>  
  
#### <a name="to-set-distribution-options-for-a-legend"></a><span data-ttu-id="2f589-184">범례의 분포 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-184">To set distribution options for a legend</span></span>  
  
1.  <span data-ttu-id="2f589-185">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-185">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-186">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-186">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-187">을 **사용 하 여 데이터 시각화** \<rule type\> 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-187">Select the **Visualize data by using** \<rule type\> option.</span></span> <span data-ttu-id="2f589-188">배포 옵션을 사용하려면 계층과 연결된 분석 데이터에 따라 **분포** 페이지에서 범위를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-188">To use distribution options, you must create ranges on the **Distribution** page based on analytical data that is associated with the layer.</span></span>  
  
4.  <span data-ttu-id="2f589-189">**분포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-189">Click **Distribution**.</span></span>  
  
5.  <span data-ttu-id="2f589-190">다음 분포 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-190">Select one of the following distribution types:</span></span>  
  
    -   <span data-ttu-id="2f589-191">**동일 간격**.</span><span class="sxs-lookup"><span data-stu-id="2f589-191">**EqualInterval**.</span></span> <span data-ttu-id="2f589-192">데이터를 동일한 범위 간격으로 나누는 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-192">Specifies ranges that divide the data into equal range intervals.</span></span>  
  
    -   <span data-ttu-id="2f589-193">**동일 분포**.</span><span class="sxs-lookup"><span data-stu-id="2f589-193">**EqualDistribution**.</span></span> <span data-ttu-id="2f589-194">각 범위에 동일한 수의 항목이 있도록 해당 데이터를 나누는 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-194">Specifies ranges that divide that data so that each range has an equal number of items.</span></span>  
  
    -   <span data-ttu-id="2f589-195">**최적**.</span><span class="sxs-lookup"><span data-stu-id="2f589-195">**Optimal**.</span></span> <span data-ttu-id="2f589-196">균형 있는 하위 범위를 만들기 위해 분포를 자동으로 조정하는 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-196">Specifies ranges that automatically adjust distribution to create balanced subranges.</span></span>  
  
    -   <span data-ttu-id="2f589-197">**사용자 지정**.</span><span class="sxs-lookup"><span data-stu-id="2f589-197">**Custom**.</span></span> <span data-ttu-id="2f589-198">값의 분포를 제어하기 위해 범위 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-198">Specify your own number of ranges to control the distribution of values.</span></span>  
  
     <span data-ttu-id="2f589-199">배포 옵션에 대한 자세한 내용은 [규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f589-199">For more information about distribution options, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
6.  <span data-ttu-id="2f589-200">**하위 범위 수**에 사용할 하위 범위 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-200">In **Number of subranges**, type the number of subranges to use.</span></span> <span data-ttu-id="2f589-201">분포 유형이 **최적**이면 하위 범위의 수가 자동으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-201">When the distribution type is **Optimal**, the number of subranges is automatically calculated.</span></span>  
  
7.  <span data-ttu-id="2f589-202">**범위 시작**에 최소 범위 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-202">In **Range start**, type a minimum range value.</span></span> <span data-ttu-id="2f589-203">이 값보다 작은 모든 값은 범위 최소값으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-203">All values less than this number are the same as the range minimum.</span></span>  
  
8.  <span data-ttu-id="2f589-204">**범위 끝**에 최대 범위 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-204">In **Range end**, type a maximum range value.</span></span> <span data-ttu-id="2f589-205">이 값보다 큰 모든 값은 범위 최대값으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-205">All values larger than this number are the same as the range maximum.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-a-rule-legend"></a><a name="RuleLegend"></a> <span data-ttu-id="2f589-206">규칙 범례의 내용을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-206">To change the contents of a rule legend</span></span>  
  
#### <a name="to-change-the-contents-of-a-color-size-width-or-marker-type-legend"></a><span data-ttu-id="2f589-207">색, 크기, 두께 또는 표식 유형 범례의 내용을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-207">To change the contents of a color, size, width, or marker type legend</span></span>  
  
1.  <span data-ttu-id="2f589-208">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-208">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-209">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-209">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-210">를 **사용 하 여 데이터 시각화** \<*rule type*> 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-210">Verify that **Visualize data by using** \<*rule type*> is selected.</span></span>  
  
4.  <span data-ttu-id="2f589-211">**데이터 필드**에서 계층에서 시각화할 분석 데이터가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-211">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f589-212">드롭다운 목록에 필드가 나타나지 않으면 계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터** 를 클릭하여 지도 계층 데이터 속성 대화 상자, 분석 데이터 페이지를 열고 이 계층의 분석 데이터를 지정했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-212">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="2f589-213">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-213">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="2f589-214">**이 범례에 표시**에서 규칙 결과를 표시하는 데 사용할 지도 범례를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-214">In **Show in this legend**, select the map legend to use to display the rule results.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-the-color-scale"></a><a name="ColorScale"></a> <span data-ttu-id="2f589-215">색 눈금의 내용을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-215">To change the contents of the color scale</span></span>  
  
#### <a name="to-change-the-contents-of-the-color-scale-or-a-color-legend"></a><span data-ttu-id="2f589-216">색 눈금 또는 색 범례의 내용을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-216">To change the contents of the color scale or a color legend</span></span>  
  
1.  <span data-ttu-id="2f589-217">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-217">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-218">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-218">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-219">사용할 색 규칙 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-219">Select the color rule option to use.</span></span> <span data-ttu-id="2f589-220">지도 범례나 색 눈금에 항목을 표시 하려면 옵션을 **사용 하 여 데이터 시각화** 중 하나를 선택 해야 합니다 \<rule type> .</span><span class="sxs-lookup"><span data-stu-id="2f589-220">To display items in a map legend or color scale, you must select one of the **Visualize data by using** \<rule type> options.</span></span>  
  
4.  <span data-ttu-id="2f589-221">**데이터 필드**에서 계층에서 시각화할 분석 데이터가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-221">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f589-222">드롭다운 목록에 필드가 나타나지 않으면 계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터** 를 클릭하여 지도 계층 데이터 속성 대화 상자, 분석 데이터 페이지를 열고 이 계층의 분석 데이터를 지정했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-222">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="2f589-223">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-223">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="2f589-224">**색 눈금 옵션**에서 **색 눈금에 표시** 를 선택하여 색 눈금에 규칙 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-224">In **Color scale options**, select **Show in color scale** to display the rule results in the color scale.</span></span> <span data-ttu-id="2f589-225">둘 이상의 색 규칙에 대해 이 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-225">You can specify this option for more than one color rule.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-remove-all-items-from-a-legend"></a><a name="HideItems"></a> <span data-ttu-id="2f589-226">범례에서 모든 항목을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-226">To remove all items from a legend</span></span>  
  
#### <a name="to-hide-items-based-on-a-rule"></a><span data-ttu-id="2f589-227">규칙에 따라 항목을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="2f589-227">To hide items based on a rule</span></span>  
  
1.  <span data-ttu-id="2f589-228">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-228">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-229">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-229">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-230">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-230">Click **Legend**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-format-of-content-in-a-legend"></a><a name="ChangeFormatItems"></a> <span data-ttu-id="2f589-231">범례의 내용 형식을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-231">To change the format of content in a legend</span></span>  
 <span data-ttu-id="2f589-232">지도 범례와 연결된 규칙의 범례 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-232">Set legend options for the rule that is associated with the map legend.</span></span>  
  
#### <a name="to-change-the-format-of-content-in-a-legend"></a><span data-ttu-id="2f589-233">범례의 내용 형식을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2f589-233">To change the format of content in a legend</span></span>  
  
1.  <span data-ttu-id="2f589-234">디자인 뷰에서 지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-234">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="2f589-235">원하는 데이터가 있는 계층을 마우스 오른쪽 단추로 클릭 한 다음 _\<map element type\>_ **규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-235">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="2f589-236">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-236">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="2f589-237">**범례 텍스트** 에 범례에 표시할 데이터를 지정하는 키워드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-237">**Legend text** displays keywords that specify which data appears in the legend.</span></span> <span data-ttu-id="2f589-238">범례 키워드와 사용자 지정 형식을 사용하여 범례 텍스트의 형식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-238">Use map keywords and custom formats to help control the format of legend text.</span></span> <span data-ttu-id="2f589-239">예를 들어 #FROMVALUE {C2}는 소수 자릿수가 두 자리인 통화를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f589-239">For example, #FROMVALUE {C2} specifies a currency format with two decimal places.</span></span> <span data-ttu-id="2f589-240">자세한 내용은 [규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f589-240">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="2f589-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f589-241">See Also</span></span>  
 <span data-ttu-id="2f589-242">[지도&#40;보고서 작성기 및 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f589-242">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2f589-243">[지도 또는 지도 계층 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f589-243">[Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2f589-244">[지도 또는 지도 계층의 데이터 및 표시 사용자 지정&#40;보고서 작성기 및 SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f589-244">[Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2f589-245">[보고서 문제해결: 지도 보고서&#40;보고서 작성기 및 SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2f589-245">[Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2f589-246">지도 마법사 및 지도 계층 마법사&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2f589-246">Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;</span></span>](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)  
  
  
