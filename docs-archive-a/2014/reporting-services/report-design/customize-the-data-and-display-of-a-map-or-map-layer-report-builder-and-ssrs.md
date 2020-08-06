---
title: 지도 또는 지도 계층의 데이터 및 표시 사용자 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10521"
- sql12.rtp.rptdesigner.shared.shadowdv.f1
- "10515"
- "10512"
- "10520"
- "10523"
- sql12.rtp.rptdesigner.mapgroupproperties.variables.f1
- sql12.rtp.rptdesigner.mapgroupproperties.filter.f1
- sql12.rtp.rptdesigner.shared.number.f1
- sql12.rtp.rptdesigner.shared.font.f1
- sql12.rtp.rptdesigner.mapgroupproperties.general.f1
- "10507"
ms.assetid: fdd9b994-d138-4990-a291-279b0249eb72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05987cea7ebde9d3587ade3f567eeb8ccef5e8fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736112"
---
# <a name="customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="6247e-102">지도 또는 지도 계층의 데이터 및 표시 사용자 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6247e-102">Customize the Data and Display of a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6247e-103">마법사를 사용하여 보고서에 지도나 지도 계층을 추가한 후 보고서에 지도가 표시되는 모양을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-103">After you add a map or map layer to a report by using a wizard, you might want to change the way the map looks in the report.</span></span> <span data-ttu-id="6247e-104">다음을 고려하여 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-104">You can make improvements by considering the following ideas:</span></span>  
  
-   <span data-ttu-id="6247e-105">사용자가 지도의 데이터 표시를 해석하는 방법을 이해하는 데 도움이 되도록 범례 및 색 눈금을 추가하고 레이블 및 도구 설명을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-105">To help your users understand how to interpret the data display on a map, you can add legends and a color scale, and add labels and tooltips.</span></span>  
  
-   <span data-ttu-id="6247e-106">지도를 읽기 쉽게 만들려면 중심 및 확대/축소 수준을 변경하고, 거리 눈금을 추가하고, 배경 눈금을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-106">To make the map easier to read, change the center and zoom level, add a distance scale, and display a background grid.</span></span>  
  
-   <span data-ttu-id="6247e-107">보고서를 실행할 때 지도 그리기 시간을 제어하려면 해상도를 조정하여 지도 요소를 단순화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-107">To help control map drawing time when you run the report, you can adjust the resolution to simplify the map elements.</span></span>  
  
-   <span data-ttu-id="6247e-108">지도 요소를 보고서 정의에 포함한 다음 개별 요소가 나타나는 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-108">You can embed map elements in the report definition, and then change how individual elements appear.</span></span> <span data-ttu-id="6247e-109">예를 들어 압정으로 주 사무실 위치를 표시하고 원으로 다른 사무실 위치를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-109">For example, you can display the primary office location with a pushpin and other office locations with circles.</span></span>  
  
-   <span data-ttu-id="6247e-110">사용자 고유의 데이터 그룹 식을 지정하여 사용자 지정 영역을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-110">You can add customized regions by specifying your own data group expressions.</span></span>  
  
-   <span data-ttu-id="6247e-111">포함된 점이 있는 지도 계층에 지정하는 점에 사용자 지정 위치를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-111">You can add a custom location at a  point that you specify on a map layer that has embedded points.</span></span> <span data-ttu-id="6247e-112">점 계층의 다른 점과 독립적으로 사용자 지정 점의 값과 표시 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-112">You can set the value and display properties for custom points independently from other points on a point layer.</span></span>  
  
-   <span data-ttu-id="6247e-113">자세한 정보를 제공하려면 각 계층에서 사용자가 관련 보고서를 열기 위해 클릭할 수 있는 지도 요소에 대한 링크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-113">To provide more detail, you can add links to map elements on each layer that a user can click to open related reports.</span></span>  
  
 <span data-ttu-id="6247e-114">보고서를 개선하는 방법은 [보고서 계획&#40;보고서 작성기&#41;](planning-a-report-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6247e-114">For more ideas about improving a report, see [Planning a Report &#40;Report Builder&#41;](planning-a-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="6247e-115">표시 옵션은 보고서를 볼 때 지도 또는 지도의 일부분이 표시되는 방식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-115">Display options affect the way a map or the parts of a map appear when you view the report.</span></span> <span data-ttu-id="6247e-116">일부 옵션은 지도에 표시되는 영역 또는 테두리 및 글꼴과 같은 지도의 모양을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-116">Some options control the appearance of the map, such as the borders and fonts or the area represented on the map.</span></span> <span data-ttu-id="6247e-117">다른 옵션은 거품 크기, 표식 유형, 레이블, 도구 설명 등 각 계층의 내용을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-117">Other options control the content of each layer, such as bubble sizes, marker types, labels, or tooltips.</span></span>  
  
 <span data-ttu-id="6247e-118">지도 보고서 항목에는 지도 자체, 지도 뷰포트, 제목 집합, 범례 집합(범례, 색 눈금 및 거리 눈금), 계층 집합, 각 계층의 지도 요소 집합(다각형, 선, 점)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-118">A map report item includes the following parts: the map itself, a map viewport, a set of titles, a set of legends (legend, color scale, and distance scale), a set of layers, a set of map elements on each layer (polygons or lines or points).</span></span> <span data-ttu-id="6247e-119">다음 섹션에서는 지도의 다양한 부분에 대한 표시 옵션을 제어하는 각 속성 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-119">Use the information in the following sections to understand which property dialog box controls the display options for different parts of a map.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="change-options-for-the-map"></a><a name="Map"></a> <span data-ttu-id="6247e-120">지도의 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-120">Change Options for the Map</span></span>  
 <span data-ttu-id="6247e-121">지도 보고서 항목에서 다음을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-121">On a map report item, you can control the following:</span></span>  
  
-   <span data-ttu-id="6247e-122">여러 제목 추가</span><span class="sxs-lookup"><span data-stu-id="6247e-122">Add multiple titles.</span></span>  
  
-   <span data-ttu-id="6247e-123">여러 범례 추가.</span><span class="sxs-lookup"><span data-stu-id="6247e-123">Add multiple legends.</span></span> <span data-ttu-id="6247e-124">범례의 내용을 변경하려면 추가 범례를 만든 다음 규칙을 변경하여 각 규칙에서 생성된 범례 항목을 입력하는 데 사용할 범례를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-124">To change the contents of a legend, you need to create additional legends and then change the rules to specify in which legend to enter the legend items created by each rule.</span></span>  
  
-   <span data-ttu-id="6247e-125">계층 더 추가</span><span class="sxs-lookup"><span data-stu-id="6247e-125">Add more layers.</span></span>  
  
-   <span data-ttu-id="6247e-126">거리 눈금 또는 색 눈금 숨기기 또는 표시</span><span class="sxs-lookup"><span data-stu-id="6247e-126">Hide or show the distance scale or color scale.</span></span>  
  
-   <span data-ttu-id="6247e-127">그림자를 지정하여 깊이감 제공</span><span class="sxs-lookup"><span data-stu-id="6247e-127">Provide the illusion of depth by specifying a shadow.</span></span>  
  
 <span data-ttu-id="6247e-128">이러한 옵션을 변경하려면 지도를 마우스 오른쪽 단추로 클릭하고 **지도**를 클릭한 다음 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-128">To change these options, right-click the map, click **Map**, and change the options.</span></span>  
  
 
  
##  <a name="change-options-for-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="6247e-129">뷰포트의 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-129">Change Options for the Viewport</span></span>  
 <span data-ttu-id="6247e-130">보고서에 나타나는 지도의 보기를 변경하려면 뷰포트 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-130">Use the viewport options to change the view of the map that appears in your report.</span></span>  
  
 <span data-ttu-id="6247e-131">공간 데이터 원본에서 보고서에 표시해야 하는 것보다 많은 영역을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-131">The source of spatial data might provide more area than you need to display in the report.</span></span> <span data-ttu-id="6247e-132">뷰포트를 사용하여 중심 및 확대/축소 수준을 설정하고 지도의 영역을 자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-132">You can use the viewport to set the center, the zoom level, and to crop the area for the map.</span></span>  
  
 <span data-ttu-id="6247e-133">뷰포트에 대해 다음 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-133">The following options can be set for the viewport:</span></span>  
  
-   <span data-ttu-id="6247e-134">좌표계를 선택하고 지리 좌표계의 경우 도법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-134">Choose the coordinate system and, for a geographic coordinate system, choose the projection.</span></span>  
  
-   <span data-ttu-id="6247e-135">지도의 중심을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-135">Choose the center for the map.</span></span>  
  
-   <span data-ttu-id="6247e-136">지도의 보기를 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-136">Crop the view for the map.</span></span>  
  
-   <span data-ttu-id="6247e-137">확대/축소 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-137">Set the zoom level.</span></span>  
  
-   <span data-ttu-id="6247e-138">해상도 및 단순화.</span><span class="sxs-lookup"><span data-stu-id="6247e-138">Resolution and simplification.</span></span> <span data-ttu-id="6247e-139">선 및 다각형의 세부 윤곽선과 그리기 시간 간의 균형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-139">Choose a balance between drawing time and detailed outlines for lines and polygons.</span></span>  
  
 <span data-ttu-id="6247e-140">이러한 옵션을 변경하려면 지도 뷰포트를 마우스 오른쪽 단추로 클릭하고 [지도 뷰포트 속성 대화 상자, 일반](../map-viewport-properties-dialog-box-general.md) 페이지 및 관련 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-140">To change these options, right-click the map viewport, use the [Map Viewport Properties Dialog Box, General](../map-viewport-properties-dialog-box-general.md) page and related pages.</span></span>  
  

  
##  <a name="change-options-for-the-legends"></a><a name="Legends"></a> <span data-ttu-id="6247e-141">범례의 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-141">Change Options for the Legends</span></span>  
 <span data-ttu-id="6247e-142">범례는 사용자가 지도의 데이터를 해석하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-142">Legends help users interpret the data on a map.</span></span>  
  
 <span data-ttu-id="6247e-143">기본적으로 계층에 지정하는 모든 규칙은 첫 번째 범례에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-143">By default, all rules that you specify for a layer add items to the first legend.</span></span> <span data-ttu-id="6247e-144">또한 모든 색 규칙은 색 눈금에 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-144">In addition, all color rules display values in the color scale.</span></span>  
  
-   <span data-ttu-id="6247e-145">뷰포트와 상대적인 범례의 위치를 비롯한 범례의 모양에 대한 표시 옵션을 변경하려면 범례 자체에서 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-145">To change the display options for the appearance of the legend, including its position relative to the viewport, set options on the legend itself.</span></span>  
  
-   <span data-ttu-id="6247e-146">범례의 내용이나 내용 형식을 변경하려면 계층에 대한 해당 규칙의 범례 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-146">To change the contents or the format of contents for a legend, change the legend options for the corresponding rules for a layer.</span></span>  
  
 <span data-ttu-id="6247e-147">자세한 내용은 [지도 범례, 색 눈금 및 관련 규칙 변경&#40;보고서 작성기 및 SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6247e-147">For more information, see [Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="change-options-for-the-layer"></a><a name="Layer"></a> <span data-ttu-id="6247e-148">계층의 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-148">Change Options for the Layer</span></span>  
 <span data-ttu-id="6247e-149">지도의 계층을 표시하려면 지도를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-149">To display the layers for a map, click the map to select it.</span></span> <span data-ttu-id="6247e-150">그러면 지도 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-150">The Map pane appears.</span></span> <span data-ttu-id="6247e-151">계층의 옵션을 변경하려면 계층을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-151">To change options for a layer, right-click the layer and use the shortcut menu.</span></span>  
  
 <span data-ttu-id="6247e-152">계층은 공간 데이터 원본에서 반환되는 공간 데이터에 따라 다각형 계층, 선 계층 또는 점 계층 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-152">A layer can be one of three types based on the spatial data that is returned by the spatial data source: a polygon layer, a line layer, or a point layer.</span></span>  
  
 <span data-ttu-id="6247e-153">계층에 대해 다음 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-153">The following options can be set for the layer:</span></span>  
  
-   <span data-ttu-id="6247e-154">연결된 분석 데이터 및 일치 필드.</span><span class="sxs-lookup"><span data-stu-id="6247e-154">The associated analytical data and match fields.</span></span> <span data-ttu-id="6247e-155">공간 데이터 원본은 지도 창에서 계층 이름 아래에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-155">The source of the spatial data is listed on the Map pane under the name of the layer.</span></span> <span data-ttu-id="6247e-156">공간 데이터 원본이 포함된 경우 계층의 지도 요소는 보고서 정의의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-156">When the source is embedded, the map elements for the layer are part of the report definition.</span></span> <span data-ttu-id="6247e-157">공간 데이터 원본이 포함되지 않은 경우에는 공간 데이터가 런타임에 검색되고 보고서가 처리될 때 보고서 처리기가 계층의 지도 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-157">If the source is not embedded, then the spatial data is retrieved at run time and the report processor creates the map elements for the layer when the report is processed.</span></span> <span data-ttu-id="6247e-158">계층의 데이터 옵션을 변경하려면 지도 계층 대화 상자에서 분석 데이터 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-158">To change data options on the layer, use the Analytical Data page in the Map Layer dialog box.</span></span>  
  
-   <span data-ttu-id="6247e-159">계층 그리기 순서.</span><span class="sxs-lookup"><span data-stu-id="6247e-159">Layer drawing order.</span></span> <span data-ttu-id="6247e-160">지도 창에 나열되는 계층이 표시되는 순서는 계층 그리기 순서의 역순입니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-160">The order that you see the layers listed in the Map pane is the reverse drawing order for the layers.</span></span> <span data-ttu-id="6247e-161">즉, 목록의 마지막 계층이 맨 처음 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-161">The last layer in the list is drawn first.</span></span> <span data-ttu-id="6247e-162">예를 들어 점 계층의 점이 다각형 계층의 다각형 맨 위에 표시되도록 하려면 점 계층이 첫 번째여야 하고 다각형 계층이 두 번째여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-162">For example, if you want the points on a point layer to appear on top of the polygons in the polygon layer, the point layer should be first and the polygon layer second.</span></span>  
  
-   <span data-ttu-id="6247e-163">투명도를 비롯한 계층 표시 유형.</span><span class="sxs-lookup"><span data-stu-id="6247e-163">Layer visibility, including transparency.</span></span> <span data-ttu-id="6247e-164">한 계층이 다른 계층을 통해 표시되도록 하려면 투명도를 0보다 큰 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-164">To have one layer show through another layer, set the transparency to a value higher than 0.</span></span> <span data-ttu-id="6247e-165">100% 값은 계층이 표시되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-165">A value of 100% means the layer is not visible.</span></span> <span data-ttu-id="6247e-166">개별 계층을 사용하여 작업하려면 지도 창에서 **표시 유형** 아이콘을 사용하여 각 계층을 독립적으로 쉽게 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-166">To work with an individual layer, you can easily show or hide each layer independently by using the **Visibility** icon in the Map pane.</span></span> <span data-ttu-id="6247e-167">확대/축소 수준 옵션을 설정하여 확대/축소 수준에 따라 계층의 지도 요소를 표시하거나 숨기는 경우를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-167">You can also set zoom level options to specify when to show or hide map elements on the layer based on the zoom level.</span></span>  
  
-   <span data-ttu-id="6247e-168">현재 뷰포트 중심 및 확대/축소 수준에 대한 Bing Maps 타일 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-168">Add a Bing map tile layer for the current viewport center and zoom level.</span></span> <span data-ttu-id="6247e-169">타일 계층의 지리 좌표를 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-169">You do not need to specify the geographic coordinates for a tile layer.</span></span> <span data-ttu-id="6247e-170">타일은 좌표계가 지리이고, 도법이 메르카토르이고, Bing Maps 서버를 사용할 수 있고 보고서 서버가 이 기능을 지원하도록 구성된 경우 뷰포트 영역과 일치되도록 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-170">Tiles are automatically loaded to match the viewport area when the coordinate system is Geographic, the projection is Mercator, the Bing Maps servers are available, and when the report server has been configured to support this feature.</span></span> <span data-ttu-id="6247e-171">각 보고서에 대해 보안 연결을 사용하여 타일을 검색할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-171">For each report, you can specify whether to use a secure connection to retrieve tiles.</span></span>  
  
 <span data-ttu-id="6247e-172">계층에 대한 자세한 내용은 [지도 또는 지도 계층 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6247e-172">For more information about layers, see [Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="change-data-grouping-for-the-layer"></a><a name="DataGrouping"></a> <span data-ttu-id="6247e-173">계층의 데이터 그룹화 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-173">Change Data Grouping for the Layer</span></span>  
 <span data-ttu-id="6247e-174">사용자 고유의 셰이프에 맞게 공간 데이터의 집계 방식을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-174">You can customize the way to aggregate spatial data for your own shapes.</span></span> <span data-ttu-id="6247e-175">계층의 그룹 속성을 설정하려면 지도 창에서 계층을 선택하고 계층의 속성 창에서 **그룹**을 클릭한 다음, 줄임표(…)를 클릭하여 그룹 속성을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-175">To set the group properties for a layer, select the layer in the Map pane, and in the Properties pane for the layer, click **Group**, and then click the ellipsis (...) to open the Group properties.</span></span> <span data-ttu-id="6247e-176">이 대화 상자에서 그룹 식을 지정하고, 그룹 변수를 만들고, 그룹화에 사용되는 데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-176">In this dialog box, you can specify group expressions, create group variables, and filter data that is used for grouping.</span></span>  
  
 <span data-ttu-id="6247e-177">그룹 식은 공간 데이터와 관계가 있는 분석 데이터가 계층의 각 지도 요소에 대해 집계되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-177">The group expression specifies how analytical data that has a relationship to spatial data is aggregated for each map element on the layer.</span></span> <span data-ttu-id="6247e-178">기본적으로 그룹 식은 공간 데이터와 분석 데이터 간의 관계에 대해 지정된 일치 필드의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-178">By default, the group expression is the set of match fields that was specified for the relationship between the spatial data and the analytical data.</span></span> <span data-ttu-id="6247e-179">예를 들어 국가 또는 지역의 도시 위치와 인구 크기를 표시하는 거품형 지도의 경우 이름이 같은 도시가 여러 개일 수 있기 때문에 일치 필드에는 도시 이름 [City]와 지역 이름 [Region]이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-179">For example, for a bubble map that displays city locations and population size for a country or region, the match fields include city name [City] and region name [Region] because there can be multiple cities with the same name.</span></span> <span data-ttu-id="6247e-180">해당 그룹 식에는 두 필드 [City] 및 [Region]이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-180">The corresponding group expression includes two fields: [City] and [Region].</span></span>  
  
 <span data-ttu-id="6247e-181">자세한 내용은 [지도 팁: 셰이프 파일을 SQL Server로 가져오고 공간 데이터를 집계하는 방법](https://go.microsoft.com/fwlink/?LinkID=214991)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6247e-181">For more information, see [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data](https://go.microsoft.com/fwlink/?LinkID=214991).</span></span>  
  
 
  
##  <a name="change-options-for-the-map-elements-on-the-layer"></a><a name="MapElements"></a> <span data-ttu-id="6247e-182">계층의 지도 요소에 대한 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="6247e-182">Change Options for the Map Elements on the Layer</span></span>  
 <span data-ttu-id="6247e-183">지도 요소는 계층에서 공간 데이터를 기반으로 하는 점, 선 또는 다각형입니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-183">Map elements are the points, lines, or polygons on a layer that are based on the spatial data.</span></span> <span data-ttu-id="6247e-184">지도 요소에 대해 다음 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-184">For map elements, the following options can be set.</span></span> <span data-ttu-id="6247e-185">이러한 옵션은 포함되었는지 여부와 관계없이 계층의 모든 지도 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-185">These options apply to all map elements on the layer, whether or not they are embedded:</span></span>  
  
-   <span data-ttu-id="6247e-186">레이블, 레이블 표시 유형, 레이블 오프셋 및 서식</span><span class="sxs-lookup"><span data-stu-id="6247e-186">Labels, label visibility, label offset, and formatting.</span></span>  
  
-   <span data-ttu-id="6247e-187">테두리 및 채우기</span><span class="sxs-lookup"><span data-stu-id="6247e-187">Borders and fill.</span></span>  
  
-   <span data-ttu-id="6247e-188">드릴스루 동작</span><span class="sxs-lookup"><span data-stu-id="6247e-188">Drillthrough actions.</span></span>  
  
-   <span data-ttu-id="6247e-189">옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-189">Display options.</span></span>  
  
 <span data-ttu-id="6247e-190">지도 요소의 표시 옵션은 계층, 지도 요소, 지도 요소에 대한 규칙 및 포함된 지도 요소의 무시 옵션에 따른 우선 순위를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-190">Display options for map elements follow a precedence order based on the layer, the map element, rules for the map element, and override options for embedded map elements.</span></span>  
  
 <span data-ttu-id="6247e-191">이러한 옵션을 변경하려면 지도 요소를 마우스 오른쪽 단추로 클릭하고 포함된 속성 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-191">To change these options, right-click the map element, use the embedded properties dialog box.</span></span> <span data-ttu-id="6247e-192">예를 들어, 포함된 다각형이라면 지도 포함 다각형 속성 대화 상자의 일반 페이지 및 관련 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-192">For example, for an embedded polygon, use the Map Embedded Polygon Properties Dialog Box, General page and related pages.</span></span>  
  

  
##  <a name="understanding-display-option-precedence"></a><a name="Precedence"></a> <span data-ttu-id="6247e-193">표시 옵션 우선 순위 이해</span><span class="sxs-lookup"><span data-stu-id="6247e-193">Understanding Display Option Precedence</span></span>  
 <span data-ttu-id="6247e-194">지도 계층에서 점, 선 또는 다각형의 표시 모양을 제어하려면 표시 옵션을 설정할 수 있는 곳과 우선 순위가 더 높은 옵션을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-194">When you want to control the display appearance of a point, line, or polygon on a map layer, you must understand where display options can be set and which options have a higher precedence.</span></span> <span data-ttu-id="6247e-195">다음 표시 옵션은 우선 순위가 낮은 것에서 높은 것 순으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-195">The following display options are listed from lowest to highest.</span></span> <span data-ttu-id="6247e-196">상위 표시 옵션이 이 목록에 있는 하위 표시 옵션을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-196">Higher display options override lower display options in this list:</span></span>  
  
-   <span data-ttu-id="6247e-197">계층 옵션</span><span class="sxs-lookup"><span data-stu-id="6247e-197">Layer options.</span></span>  
  
-   <span data-ttu-id="6247e-198">각 계층의 점, 선 또는 다각형 옵션.</span><span class="sxs-lookup"><span data-stu-id="6247e-198">Points, Lines, or Polygons options on each layer.</span></span> <span data-ttu-id="6247e-199">이러한 옵션은 보고서가 처리될 때 지도 요소가 동적으로 검색되는지 여부나 지도 요소가 보고서 정의에 포함되는지 여부와 관계없이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-199">This applies whether the map elements are dynamically retrieved when the report is processed or whether they the map elements are embedded in the report definition.</span></span> <span data-ttu-id="6247e-200">예를 들어 계층의 모든 요소에 대해 채우기 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-200">For example, you specify a fill color for all elements on a layer.</span></span>  
  
-   <span data-ttu-id="6247e-201">규칙.</span><span class="sxs-lookup"><span data-stu-id="6247e-201">Rules.</span></span> <span data-ttu-id="6247e-202">계층의 모든 지도 요소에 대한 색, 크기, 두께 또는 표식 유형을 제어하는 규칙을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-202">You can set rules to control color, size, width, or marker type for all map elements on a layer.</span></span> <span data-ttu-id="6247e-203">설정할 수 있는 규칙은 지도 요소의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-203">The rules that you can set depend on the type of map element.</span></span>  
  
    -   <span data-ttu-id="6247e-204">색 규칙.</span><span class="sxs-lookup"><span data-stu-id="6247e-204">Color Rules.</span></span> <span data-ttu-id="6247e-205">점, 선, 다각형의 표식과 다각형 중심점의 표식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-205">Apply to markers for points, lines, polygons, and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="6247e-206">크기 규칙.</span><span class="sxs-lookup"><span data-stu-id="6247e-206">Size Rules.</span></span> <span data-ttu-id="6247e-207">점의 표식과 다각형 중심점의 표식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-207">Apply to markers for points and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="6247e-208">두께 규칙.</span><span class="sxs-lookup"><span data-stu-id="6247e-208">Width Rules.</span></span> <span data-ttu-id="6247e-209">선 두께에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-209">Applies to line widths.</span></span>  
  
    -   <span data-ttu-id="6247e-210">표식 유형 규칙.</span><span class="sxs-lookup"><span data-stu-id="6247e-210">Marker Type Rules.</span></span> <span data-ttu-id="6247e-211">점의 표식과 다각형 중심점의 표식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-211">Applies to markers for points and markers for polygon center points.</span></span>  
  
-   <span data-ttu-id="6247e-212">계층의 개별 포함된 점, 선 또는 다각형에 대한 옵션을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-212">Override options for individual embedded points, lines, or polygons on a layer.</span></span> <span data-ttu-id="6247e-213">변경하는 내용은 영구적입니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-213">Changes that you make are permanent.</span></span> <span data-ttu-id="6247e-214">이러한 변경 내용을 되돌리려면 계층의 데이터를 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6247e-214">To revert these changes, you must reload the data for the layer.</span></span>  
  
 <span data-ttu-id="6247e-215">자세한 내용은 [규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6247e-215">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="6247e-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6247e-216">See Also</span></span>  
 <span data-ttu-id="6247e-217">[지도 마법사 및 지도 계층 마법사&#40;보고서 작성기 및 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6247e-217">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6247e-218">지도&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6247e-218">Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
  
  
