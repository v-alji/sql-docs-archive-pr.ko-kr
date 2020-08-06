---
title: 지도 또는 지도 계층 추가, 변경 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10526"
- sql12.rtp.rptdesigner.maptilelayerproperties.general.f1
- "10529"
- "10525"
- "10535"
- sql12.rtp.rptdesigner.mappolygonlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layervisibility.f1
- sql12.rtp.rptdesigner.mappointlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layerfilters.f1
- "10524"
- sql12.rtp.rptdesigner.maplayerproperties.general.f1
- sql12.rtp.rptdesigner.maplinelayerproperties.general.f1
- "10532"
- "10528"
- "10527"
- sql12.rtp.rptdesigner.maplayerproperties.analyticaldata.f1
ms.assetid: 6e89815e-187e-45bf-bf63-3d5c4a246360
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e9fd178d36ee3322c0bd94dd44d621439139b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650763"
---
# <a name="add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="00f25-102">지도 또는 지도 계층 추가, 변경 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="00f25-102">Add, Change, or Delete a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="00f25-103">지도는 계층의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-103">A map is a collection of layers.</span></span> <span data-ttu-id="00f25-104">보고서에 지도를 추가할 때 첫 번째 계층을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-104">When you add a map to a report, you define the first layer.</span></span> <span data-ttu-id="00f25-105">지도 계층 마법사를 사용하여 추가 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-105">You can create additional layers by using the map layer wizard.</span></span>  
  
 <span data-ttu-id="00f25-106">계층의 옵션을 추가, 제거 또는 변경하는 가장 쉬운 방법은 지도 계층 마법사를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-106">The easiest way to add, remove, or change options for a layer is to use the map layer wizard.</span></span> <span data-ttu-id="00f25-107">지도 창에서 옵션을 수동으로 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-107">You can also change options manually from the Map pane.</span></span> <span data-ttu-id="00f25-108">**지도** 창을 표시하려면 보고서 디자인 화면에서 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-108">To display the **Map** pane, click in the map on the report design surface.</span></span> <span data-ttu-id="00f25-109">다음 그림에서는 창의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-109">The following figure displays the parts of the pane:</span></span>  
  
 <span data-ttu-id="00f25-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span><span class="sxs-lookup"><span data-stu-id="00f25-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span></span>  
  
 <span data-ttu-id="00f25-111">지도 계층은 지도 창에 나타나는 순서대로 아래쪽에서 위쪽으로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-111">Map layers are drawn from bottom to top in the order that they appear in the Map pane.</span></span> <span data-ttu-id="00f25-112">위의 그림에서 타일 계층이 가장 먼저 그려지고 다각형 계층이 마지막으로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-112">In the previous figure, the tile layer is drawn first and the polygon layer is drawn last.</span></span> <span data-ttu-id="00f25-113">이후에 그려지는 계층은 이전에 그려진 계층의 지도 요소를 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-113">Layers that are drawn later might hide map elements on layers that are drawn earlier.</span></span> <span data-ttu-id="00f25-114">지도 창 도구 모음에서 화살표 키를 사용하여 계층의 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-114">You can change the order of layers by using the arrow keys on the Map pane toolbar.</span></span> <span data-ttu-id="00f25-115">계층을 표시하거나 숨기려면 표시 유형 아이콘을 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-115">To show or hide layers, toggle the visibility icon.</span></span> <span data-ttu-id="00f25-116">`Visibility` **계층 데이터** 속성 대화 상자의 페이지에서 계층의 투명도를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-116">You can change the transparency of a layer on the `Visibility` page of the **Layer Data** properties dialog box.</span></span>  
  
 <span data-ttu-id="00f25-117">다음 표에서는 **지도** 창의 도구 모음 아이콘을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-117">The following table displays the toolbar icons for the **Map** pane.</span></span>  
  
|<span data-ttu-id="00f25-118">기호</span><span class="sxs-lookup"><span data-stu-id="00f25-118">Symbol</span></span>|<span data-ttu-id="00f25-119">Description</span><span class="sxs-lookup"><span data-stu-id="00f25-119">Description</span></span>|<span data-ttu-id="00f25-120">사용 시기</span><span class="sxs-lookup"><span data-stu-id="00f25-120">When to use</span></span>|  
|------------|-----------------|-----------------|  
|<span data-ttu-id="00f25-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span><span class="sxs-lookup"><span data-stu-id="00f25-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span></span>|<span data-ttu-id="00f25-122">지도 계층 마법사</span><span class="sxs-lookup"><span data-stu-id="00f25-122">Map Layer Wizard</span></span>|<span data-ttu-id="00f25-123">마법사를 사용하여 계층을 추가하려면 **새 계층 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-123">To add a layer by using a wizard, click **New layer wizard**.</span></span>|  
|<span data-ttu-id="00f25-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span><span class="sxs-lookup"><span data-stu-id="00f25-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span></span>|<span data-ttu-id="00f25-125">계층 추가</span><span class="sxs-lookup"><span data-stu-id="00f25-125">Add Layer</span></span>|<span data-ttu-id="00f25-126">계층을 수동으로 추가하려면 **계층 추가**를 클릭한 다음 추가할 지도 계층의 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-126">To manually add a layer, click **Add Layer**, and then click the type of map layer to add.</span></span>|  
|<span data-ttu-id="00f25-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span><span class="sxs-lookup"><span data-stu-id="00f25-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span></span>|<span data-ttu-id="00f25-128">다각형 계층</span><span class="sxs-lookup"><span data-stu-id="00f25-128">Polygon Layer</span></span>|<span data-ttu-id="00f25-129">다각형 좌표의 집합을 기반으로 영역이나 모양을 표시하는 지도 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-129">Add a map layer that displays areas or shapes that are based sets of polygon coordinates.</span></span>|  
|<span data-ttu-id="00f25-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span><span class="sxs-lookup"><span data-stu-id="00f25-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span></span>|<span data-ttu-id="00f25-131">선 계층</span><span class="sxs-lookup"><span data-stu-id="00f25-131">Line Layer</span></span>|<span data-ttu-id="00f25-132">선 좌표의 집합을 기반으로 경로를 표시하는 지도 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-132">Add a map layer that displays paths or routes that are based on sets of line coordinates.</span></span>|  
|<span data-ttu-id="00f25-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span><span class="sxs-lookup"><span data-stu-id="00f25-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span></span>|<span data-ttu-id="00f25-134">점 계층</span><span class="sxs-lookup"><span data-stu-id="00f25-134">Point Layer</span></span>|<span data-ttu-id="00f25-135">점 좌표의 집합을 기반으로 위치를 표시하는 지도 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-135">Add a map layer that displays locations that are based on sets of point coordinates.</span></span>|  
|<span data-ttu-id="00f25-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span><span class="sxs-lookup"><span data-stu-id="00f25-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span></span>|<span data-ttu-id="00f25-137">타일 계층</span><span class="sxs-lookup"><span data-stu-id="00f25-137">Tile Layer</span></span>|<span data-ttu-id="00f25-138">뷰포트가 정의하는 현재 지도 보기 영역에 해당하는 Bing Maps 타일을 표시하는 지도 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-138">Add a map layer that displays Bing Map tiles that correspond to the current map view area that is defined by the viewport.</span></span>|  
  
 <span data-ttu-id="00f25-139">지도 창의 아래쪽에는 지도 보기 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-139">At the bottom of the Map pane is the Map view area.</span></span> <span data-ttu-id="00f25-140">지도의 중심 및 확대/축소 옵션을 변경하려면 화살표 키를 사용하여 보기 중심을 조정하고 슬라이더를 사용하여 확대/축소 수준을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-140">To change the center or zoom options for the map, use the arrow keys to adjust the view center and the slider to adjust the zoom level.</span></span>  
  
 <span data-ttu-id="00f25-141">계층에 대한 자세한 내용은 [지도&#40;보고서 작성기 및 SSRS&#41;](maps-report-builder-and-ssrs.md)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-141">For more information about layers, see [Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-add-a-layer-from-the-map-layer-wizard"></a><a name="AddLayer"></a> <span data-ttu-id="00f25-142">지도 계층 마법사에서 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-142">To add a layer from the map layer wizard</span></span>  
  
-   <span data-ttu-id="00f25-143">리본의 **삽입** 메뉴에서 **지도**를 클릭한 다음 **지도 Wizard.**</span><span class="sxs-lookup"><span data-stu-id="00f25-143">From the Ribbon, on the **Insert** menu, click **Map**, and then click **Map Wizard.**</span></span> <span data-ttu-id="00f25-144">를 클릭합니다. 이 마법사를 사용하여 기존 지도에 계층을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-144">The wizard enables you to add a layer to the existing map.</span></span> <span data-ttu-id="00f25-145">지도 마법사와 지도 계층 마법사의 마법사 페이지는 대부분 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-145">Most wizard pages are identical between the map wizard and the map layer wizard.</span></span>  
  
     <span data-ttu-id="00f25-146">자세한 내용은 [지도 마법사 및 지도 계층 마법사&#40;보고서 작성기 및 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-146">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-change-options-for-a-layer-by-using-the-map-layer-wizard"></a><a name="ChangeLayer"></a> <span data-ttu-id="00f25-147">지도 계층 마법사를 사용하여 계층의 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-147">To change options for a layer by using the map layer wizard</span></span>  
  
-   <span data-ttu-id="00f25-148">지도 계층 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-148">Run the map layer wizard.</span></span> <span data-ttu-id="00f25-149">이 마법사를 통해 지도 계층 마법사를 사용하여 만든 계층의 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-149">This wizard enables you to change options for a layer that you created by using the map layer wizard.</span></span> <span data-ttu-id="00f25-150">지도 창에서 계층을 마우스 오른쪽 단추로 클릭한 다음에 도구 모음에서 계층 마법사 단추(![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-150">In the Map pane, right-click the layer, and on the toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
     <span data-ttu-id="00f25-151">자세한 내용은 [지도 마법사 및 지도 계층 마법사&#40;보고서 작성기 및 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-151">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-add-a-point-line-or-polygon-layer-from-the-map-pane-toolbar"></a><a name="AddVectorLayer"></a> <span data-ttu-id="00f25-152">지도 창 도구 모음에서 점, 선 또는 다각형 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-152">To add a point, line, or polygon layer from the Map pane toolbar</span></span>  
  
1.  <span data-ttu-id="00f25-153">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-153">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-154">도구 모음에서 **계층 추가** 단추를 클릭하고 드롭다운 목록의 **점**, **선** 또는 **다각형** 중에서 추가할 계층의 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-154">On the toolbar, click the **Add Layer** button, and from the drop-down list, click the type of layer that you want to add: **Point**, **Line**, or **Polygon**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00f25-155">지도 계층을 추가하고 수동으로 구성할 수 있지만 지도 계층 마법사를 사용하여 새 계층을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-155">Although you can add a map layer and configure it manually, we recommend that you use the map layer wizard to add new layers.</span></span> <span data-ttu-id="00f25-156">지도 창 도구 모음에서 마법사를 실행하려면 계층 마법사 단추(![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-156">To launch the wizard from the Map pane toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
3.  <span data-ttu-id="00f25-157">계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-157">Right-click the layer, and then click **Layer Data**.</span></span>  
  
4.  <span data-ttu-id="00f25-158">**다음의 공간 데이터 사용**에서 공간 데이터의 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-158">In **Use spatial data from**, select the source of spatial data.</span></span> <span data-ttu-id="00f25-159">옵션은 선택한 원본에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-159">Options vary based on your selection.</span></span>  
  
     <span data-ttu-id="00f25-160">이 계층의 보고서에서 분석을 시각화하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-160">If you want to visualize analytical from your report on this layer, do the following:</span></span>  
  
    1.  <span data-ttu-id="00f25-161">**분석 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-161">Click **Analytical data**.</span></span>  
  
    2.  <span data-ttu-id="00f25-162">**분석 데이터 세트**에서 분석 데이터와 공간 데이터 간의 관계를 만드는 일치 필드와 분석 데이터가 포함된 데이터 세트의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-162">In **Analytical dataset**, click the name of the dataset that contains analytical data and the match fields to build a relationship between analytical and spatial data.</span></span>  
  
    3.  <span data-ttu-id="00f25-163">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-163">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="00f25-164">공간 데이터 세트에 있는 일치 필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-164">Type the name of the match field from the spatial dataset.</span></span>  
  
    5.  <span data-ttu-id="00f25-165">분석 데이터 세트에 있는 일치 필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-165">Type the name of the match field from the analytical dataset.</span></span>  
  
     <span data-ttu-id="00f25-166">공간 및 분석 데이터를 연결하는 방법에 대한 자세한 내용은 [지도 또는 지도 계층의 데이터 및 표시 사용자 지정&#40;보고서 작성기 및 SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-166">For more information about linking spatial and analytical data, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-filter-analytical-data-for-the-layer"></a><a name="FilterAnalyticalData"></a> <span data-ttu-id="00f25-167">계층에 대한 분석 데이터를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-167">To filter analytical data for the layer</span></span>  
  
1.  <span data-ttu-id="00f25-168">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-168">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-169">지도 창에서 계층을 마우스 오른쪽 단추로 클릭하고  **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-169">Right-click the layer in the Map pane, and then click  **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="00f25-170">**필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-170">Click **Filters**.</span></span>  
  
4.  <span data-ttu-id="00f25-171">지도 표시에 사용되는 분석 데이터를 제한할 필터 수식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-171">Define a filter equation to limit the analytical data that is used in the map display.</span></span> <span data-ttu-id="00f25-172">자세한 내용은 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-172">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-control-point-properties-for-a-point-layer-or-for-polygon-center-points"></a><a name="PointProperties"></a> <span data-ttu-id="00f25-173">점 계층 또는 다각형 중심점에 대한 점 속성을 제어하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-173">To control point properties for a point layer or for polygon center points</span></span>  
  
1.  <span data-ttu-id="00f25-174">**지도 점 속성** 대화 상자에서 **일반** 을 선택하여 다음 지도 요소의 레이블, 도구 설명 및 표식 유형 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-174">Select **General** on the **Map Point Properties** dialog box to change label, tooltip, and marker type options for the following map elements:</span></span>  
  
    -   <span data-ttu-id="00f25-175">점 계층의 모든 동적 또는 포함된 점.</span><span class="sxs-lookup"><span data-stu-id="00f25-175">All dynamic or embedded points on a point layer.</span></span> <span data-ttu-id="00f25-176">점의 색 규칙, 크기 규칙 및 표식 유형 규칙은 이러한 옵션을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-176">Color rules, size rules, and marker type rules for points override these options.</span></span> <span data-ttu-id="00f25-177">특정 포함된 점에 대한 옵션을 무시하려면 [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-177">To override options for a specific embedded point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  
  
    -   <span data-ttu-id="00f25-178">다각형 계층의 모든 동적 또는 포함된 다각형에 대한 중심점.</span><span class="sxs-lookup"><span data-stu-id="00f25-178">The center point for all dynamic or embedded polygons on a polygon layer.</span></span> <span data-ttu-id="00f25-179">중심점의 색 규칙, 크기 규칙 및 표식 유형 규칙은 이러한 옵션을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-179">Color rules, size rules, and marker type rules for center points override these options.</span></span> <span data-ttu-id="00f25-180">특정 중심점에 대한 옵션을 무시하려면 [지도 포함 점 속성 대화 상자, 표식](../map-embedded-point-properties-dialog-box-marker.md) 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-180">To override options for a specific center point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  

##  <a name="to-specify-embedded-data-as-a-source-of-spatial-data"></a><a name="Embedded"></a> <span data-ttu-id="00f25-181">포함된 데이터를 공간 데이터의 원본으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-181">To specify embedded data as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="00f25-182">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-182">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-183">계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-183">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="00f25-184">**다음의 공간 데이터 사용**에서 **보고서에 포함된 데이터**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-184">In **Use spatial data from**, select **Data embedded in report**.</span></span>  
  
4.  <span data-ttu-id="00f25-185">기존 보고서에서 지도 요소를 로드하거나 ESRI 파일에 따라 지도 요소를 만들려면 **찾아보기**를 클릭하고 파일을 가리킨 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-185">To load map elements from an existing report or to create map elements based on an ESRI file, click **Browse**, point to the file, and then click **Open**.</span></span> <span data-ttu-id="00f25-186">지도 요소는 이 보고서 정의에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-186">The map elements are embedded in this report definition.</span></span> <span data-ttu-id="00f25-187">가리키는 공간 데이터는 계층 유형과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-187">The spatial data that you point to must match the layer type.</span></span> <span data-ttu-id="00f25-188">예를 들어 점 계층의 경우 점 좌표의 집합을 지정하는 공간 데이터를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-188">For example, for a point layer, you must point to spatial data that specifies sets of point coordinates.</span></span>  
  
5.  <span data-ttu-id="00f25-189">**공간 필드**에서 공간 데이터가 포함된 필드의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-189">In **Spatial field**, specify the name of the field that contains spatial data.</span></span> <span data-ttu-id="00f25-190">공간 데이터의 원본에서 이 이름을 확인해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-190">You might need to determine this name from the source of spatial data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00f25-191">필드의 이름을 모르고 ESRI 셰이프 파일로 이동한 경우 이 옵션 대신 **ESRI 셰이프 파일에 연결** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-191">If you do not know the name of the field and you browsed to an ESRI Shapefile, use the **Link to ESRI shape file option** instead of this option.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-an-esri-shapefile-as-a-source-of-spatial-data"></a><a name="ESRI"></a> <span data-ttu-id="00f25-192">ESRI 셰이프 파일을 공간 데이터의 원본으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-192">To specify an ESRI Shapefile as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="00f25-193">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-193">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-194">계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-194">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="00f25-195">**다음의 공간 데이터 사용**에서 **ESRI 셰이프 파일에 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-195">In **Use spatial data from**, select **Link to ESRI Shapefile**.</span></span>  
  
4.  <span data-ttu-id="00f25-196">**파일 이름**에 ESRI 셰이프 파일의 위치를 입력하거나 **찾아보기** 를 클릭하여 ESRI 셰이프 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-196">In **File name**, type the location of an ESRI Shapefile, or click **Browse** to select an ESRI Shapefile.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00f25-197">셰이프 파일이 로컬 컴퓨터에 있는 경우 공간 데이터가 보고서 정의에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-197">If the Shapefile is on your local computer, the spatial data is embedded in the report definition.</span></span> <span data-ttu-id="00f25-198">보고서가 처리될 때 데이터를 동적으로 검색하려면 ESRI .shp 파일 및 해당 .dbf 지원 파일을 보고서 서버로 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-198">To retrieve the data dynamically when the report is processed, you must upload the ESRI .shp file and its .dbf support file to the report server.</span></span> <span data-ttu-id="00f25-199">자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에서 "방법: 파일 또는 보고서 업로드(보고서 관리자)"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-199">For more information, see " How to: Upload a File or Report (Report Manager)" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-report-dataset-field-as-a-source-of-spatial-data"></a><a name="DatasetField"></a> <span data-ttu-id="00f25-200">보고서 데이터 세트 필드를 공간 데이터의 원본으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-200">To specify a report dataset field as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="00f25-201">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-201">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-202">계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-202">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="00f25-203">**다음의 공간 데이터 사용**에서 **데이터 세트의 공간 필드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-203">In **Use spatial data from**, select **Spatial field in a dataset**.</span></span>  
  
4.  <span data-ttu-id="00f25-204">**데이터 세트 이름**에서 원하는 공간 데이터가 포함된 보고서의 데이터 세트 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-204">In **Dataset name**, click the name of a dataset in the report that contains that spatial data that you want.</span></span>  
  
5.  <span data-ttu-id="00f25-205">**공간 필드 이름**에서 공간 데이터가 포함된 데이터 세트의 필드 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-205">In **Spatial field name**, click the name of the field in the dataset that contains spatial data.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-add-a-tile-layer"></a><a name="TileLayer"></a> <span data-ttu-id="00f25-206">타일 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-206">To add a tile layer</span></span>  
  
1.  <span data-ttu-id="00f25-207">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-207">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-208">도구 모음에서 **계층 추가** 단추를 클릭하고 드롭다운 목록에서 **타일 계층**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-208">On the toolbar, click the **Add Layer** button, and from the drop-down list, click **Tile Layer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00f25-209"> 보고서에서 Bing 지도 타일을 사용하는 방법은 [추가 사용 조건(Additional Terms of Use)](https://go.microsoft.com/fwlink/?LinkId=151371) 및 [개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=151372)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-209">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
3.  <span data-ttu-id="00f25-210">지도 창에서 타일 계층을 마우스 오른쪽 단추로 클릭한 다음 **타일 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-210">Right-click the tile layer in the Map pane, and then click **Tile Properties**.</span></span>  
  
4.  <span data-ttu-id="00f25-211">**타일 옵션**에서 타일 스타일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-211">In **Tile options**, select a tile style.</span></span> <span data-ttu-id="00f25-212">Bing Maps 타일을 사용할 수 있으면 디자인 화면의 계층이 선택한 스타일로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-212">If the Bing map tiles are available, the layer on the design surface updates with the style that you select.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00f25-213">지도 또는 지도 계층 마법사에서 다각형, 선 또는 점 계층을 추가할 때 타일 계층도 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-213">A tile layer can also be added when you add a polygon, line, or point layer in the Map or Map Layer wizard.</span></span> <span data-ttu-id="00f25-214">**공간 데이터 및 지도 보기 옵션 선택** 페이지에서 **이 지도 보기에 대해 Bing Maps 배경 추가**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-214">On the **Choose spatial data and map view options** page, select the option **Add a Bing Maps background for this map view**.</span></span>  

##  <a name="to-change-the-drawing-order-of-a-layer"></a><a name="DrawingOrder"></a> <span data-ttu-id="00f25-215">계층의 그리기 순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-215">To change the drawing order of a layer</span></span>  
  
1.  <span data-ttu-id="00f25-216">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-216">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-217">지도 창에서 계층을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-217">Click the layer in the Map pane to select it.</span></span>  
  
3.  <span data-ttu-id="00f25-218">지도 창 도구 모음에서 위로 또는 아래로 화살표를 클릭하여 각 계층의 그리기 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-218">On the Map pane toolbar, click the up or down arrow to change the drawing order of each layer.</span></span>  

##  <a name="to-change-the-transparency-of-a-polygon-line-or-point-layer"></a><a name="Transparency"></a> <span data-ttu-id="00f25-219">다각형, 선 또는 점 계층의 투명도를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-219">To change the transparency of a polygon, line, or point layer</span></span>  
  
1.  <span data-ttu-id="00f25-220">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-220">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-221">계층을 마우스 오른쪽 단추로 클릭한 다음 **계층 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-221">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="00f25-222">`Visibility`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-222">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="00f25-223">**투명도 옵션**에서 투명도를 나타내는 값(%)을 입력합니다(예: **40**).</span><span class="sxs-lookup"><span data-stu-id="00f25-223">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span> <span data-ttu-id="00f25-224">0% 투명도는 계층이 불투명함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-224">Zero (0) % transparency means that the layer is opaque.</span></span> <span data-ttu-id="00f25-225">100% 투명도는 보고서에서 계층을 볼 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-225">100% transparency means that you will not see the layer in the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-change-the-transparency-of-a-tile-layer"></a><a name="TileTransparency"></a> <span data-ttu-id="00f25-226">타일 계층의 투명도를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-226">To change the transparency of a tile layer</span></span>  
  
1.  <span data-ttu-id="00f25-227">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-227">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-228">계층을 마우스 오른쪽 단추로 클릭한 다음 **타일 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-228">Right-click the layer, and then click **Tile Properties**.</span></span>  
  
3.  <span data-ttu-id="00f25-229">`Visibility`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-229">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="00f25-230">**투명도 옵션**에서 투명도를 나타내는 값(%)을 입력합니다(예: **40**).</span><span class="sxs-lookup"><span data-stu-id="00f25-230">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-secure-connection-for-a-tile-layer"></a><a name="Secure"></a> <span data-ttu-id="00f25-231">타일 계층에 대한 보안 연결을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-231">To specify a secure connection for a tile layer</span></span>  
  
1.  <span data-ttu-id="00f25-232">지도 창이 나타날 때까지 지도를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-232">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="00f25-233">지도 창에서 타일 계층을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-233">In the Map pane, click the tile layer to select it.</span></span> <span data-ttu-id="00f25-234">속성 창에 타일 계층 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-234">The Properties pane displays the tile layer properties.</span></span>  
  
3.  <span data-ttu-id="00f25-235">속성 창에서 UseSecureConnection을 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-235">In the Properties pane, set UseSecureConnection to **True**.</span></span>  
  
 <span data-ttu-id="00f25-236">Bing Maps 웹 서비스의 연결에서는 HTTP SSL(Secure Sockets Layer) 서비스를 사용하여 해당 계층에 대한 Bing Maps 타일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-236">The connection for the Bing Maps Web service will use the HTTP SSL (Secure Sockets Layer) service to retrieve Bing map tiles for this layer.</span></span>  

##  <a name="to-specify-the-language-for-tile-labels"></a><a name="Language"></a> <span data-ttu-id="00f25-237">타일 레이블의 언어를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="00f25-237">To specify the language for tile labels</span></span>  
  
1.  <span data-ttu-id="00f25-238">기본적으로 레이블을 표시하는 타일 스타일의 경우 언어는 보고서 작성기에 대한 기본 로캘에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-238">By default, for tile styles that display labels, the language is determined from the default locale for Report Builder.</span></span> <span data-ttu-id="00f25-239">다음과 같은 방법으로 타일 레이블에 대한 언어 설정을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-239">You can customize the language setting for tile labels in the following ways.</span></span>  
  
    -   <span data-ttu-id="00f25-240">뷰포트 외부의 지도를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-240">Click the map outside the viewport to select the map.</span></span> <span data-ttu-id="00f25-241">속성 창의 드롭다운 목록에서 TileLanguage 속성에 대한 문화권 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-241">In the Properties pane, for the TileLanguage property, select a culture value from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="00f25-242">보고서 배경을 클릭하여 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-242">Click the report background to select the report.</span></span> <span data-ttu-id="00f25-243">속성 창의 드롭다운 목록에서 Language 속성에 대한 문화권 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-243">In the Properties pane, from for the Language property, select a culture value from the drop-down list.</span></span>  
  
     <span data-ttu-id="00f25-244">타일 레이블 언어 설정의 우선 순위는 보고서 속성 Language, 보고서 작성기에 대한 기본 로캘 및 지도 속성 TileLanguage입니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-244">The order of precedence for setting the tile label language is: report property Language, default locale for Report Builder, and map property TileLanguage.</span></span>  

##  <a name="to-conditionally-hide-a-layer-based-on-viewport-zoom-level"></a><a name="ConditionalHide"></a> <span data-ttu-id="00f25-245">뷰포트 확대/축소 수준을 기반으로 계층을 조건에 따라 숨기려면</span><span class="sxs-lookup"><span data-stu-id="00f25-245">To conditionally hide a layer based on viewport zoom level</span></span>  
  
1.  <span data-ttu-id="00f25-246">`Visibility`지도 계층의 표시를 제어 하는 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-246">Set `Visibility` options to control the display for a map layer.</span></span>  
  
    -   <span data-ttu-id="00f25-247">지도 계층 창에서 계층을 마우스 오른쪽 단추로 클릭하여 선택하고 지도 계층 도구 모음에서 속성을 클릭하여 **지도 계층 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-247">In the Map Layers pane, right-click a layer to select it, and on the Map Layers toolbar, click Properties to open **Map Layer Properties**.</span></span>  
  
    -   <span data-ttu-id="00f25-248">`Visibility`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-248">Click `Visibility`.</span></span>  
  
    -   <span data-ttu-id="00f25-249">계층 표시 유형에서 **확대/축소 값에 따라 표시 또는 숨기기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-249">In Layer visibility, select **Show or hide based on zoom value**.</span></span>  
  
    -   <span data-ttu-id="00f25-250">계층을 표시할 때 사용할 최소 및 최대 확대/축소 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-250">Enter minimum and maximum zoom values for when display the layer.</span></span>  
  
    -   <span data-ttu-id="00f25-251">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="00f25-251">Optional.</span></span> <span data-ttu-id="00f25-252">투명도 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-252">Enter a value for transparency.</span></span>  
  
     <span data-ttu-id="00f25-253">조건에 따라 계층을 숨길 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00f25-253">You can also conditionally hide the layer.</span></span> <span data-ttu-id="00f25-254">자세한 내용은 [항목 숨기기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00f25-254">For more information, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="00f25-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00f25-255">See Also</span></span>  
 <span data-ttu-id="00f25-256">[지도&#40;보고서 작성기 및 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="00f25-256">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="00f25-257">보고서 문제 해결: 맵 보고서&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="00f25-257">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
