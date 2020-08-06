---
title: '자습서: 맵 보고서(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b737bb3fe74eb3524f2944a7458cb4837b1aeedf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737786"
---
# <a name="tutorial-map-report-report-builder"></a><span data-ttu-id="d71d0-102">자습서: 지도 보고서(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="d71d0-102">Tutorial: Map Report (Report Builder)</span></span>
  <span data-ttu-id="d71d0-103">이 자습서는 지리적 배경에 대한 보고서 데이터를 표시하는 데 사용할 수 있는 지도 기능을 이해하는 데 도움을 주기 위해 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-103">This tutorial is designed to help you learn about the map features you can use to display report data against a geographic background.</span></span>  
  
 <span data-ttu-id="d71d0-104">지도는 일반적으로 점, 선 및 다각형으로 구성된 공간 데이터를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-104">Maps are based on spatial data that typically consists of points, lines, and polygons.</span></span> <span data-ttu-id="d71d0-105">예를 들어 다각형으로는 군의 경계를 나타내고, 선으로는 도로를 나타내며, 점으로는 도시의 위치를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-105">For example, a polygon can represent the outline of a county, a line can represent a road, and a point can represent the location of a city.</span></span> <span data-ttu-id="d71d0-106">각 공간 데이터 형식은 별도의 지도 계층에 지도 요소 집합으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-106">Each type of spatial data is displayed on a separate map layer as a set of map elements.</span></span>  
  
 <span data-ttu-id="d71d0-107">지도 요소의 모양을 변경하려면 지도 요소를 데이터 세트의 분석 데이터와 일치시키는 값이 있는 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-107">To vary the appearance of map elements, you specify a field that has values that match the map elements with analytical data from a dataset.</span></span> <span data-ttu-id="d71d0-108">또한 데이터의 범위에 따라 색, 크기 또는 기타 속성을 변경하는 규칙을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-108">You can also define rules that vary color, size, or other properties based on ranges of data.</span></span>  
  
 <span data-ttu-id="d71d0-109">이 자습서에서는 뉴욕 주의 군에 있는 상점 위치를 표시하는 지도 보고서를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-109">In this tutorial, you will build a map report that displays store locations in New York state counties.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="d71d0-110">학습 내용</span><span class="sxs-lookup"><span data-stu-id="d71d0-110">What You Will Learn</span></span>  
 <span data-ttu-id="d71d0-111">이 자습서에서는 다음 작업 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="d71d0-112">지도 마법사에서 다각형 계층을 사용하여 지도 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-112">Create a Map with a Polygon Layer from the Map Wizard</span></span>](#Map)  
  
2.  [<span data-ttu-id="d71d0-113">지도 점 계층을 추가하여 상점 위치 표시</span><span class="sxs-lookup"><span data-stu-id="d71d0-113">Add a Map Point Layer to Display Store Locations</span></span>](#PointLayer)  
  
3.  [<span data-ttu-id="d71d0-114">지도 선 계층을 추가하여 경로 표시</span><span class="sxs-lookup"><span data-stu-id="d71d0-114">Add a Map Line Layer to Display a Route</span></span>](#LineLayer)  
  
4.  [<span data-ttu-id="d71d0-115">Bing Maps 타일 배경 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-115">Add a Bing Maps Tile Background</span></span>](#TileLayer)  
  
5.  [<span data-ttu-id="d71d0-116">계층을 투명하게 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-116">Make a Layer Transparent</span></span>](#Transparent)  
  
6.  [<span data-ttu-id="d71d0-117">판매량을 기준으로 군 색 변경</span><span class="sxs-lookup"><span data-stu-id="d71d0-117">Vary County Color Based on Sales</span></span>](#Vary)  
  
    1.  [<span data-ttu-id="d71d0-118">공간 데이터와 분석 데이터 간의 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-118">Build a Relationship between Spatial and Analytical Data</span></span>](#Relationship)  
  
    2.  [<span data-ttu-id="d71d0-119">다각형에 대한 색 규칙 지정</span><span class="sxs-lookup"><span data-stu-id="d71d0-119">Specify Color Rules for Polygons</span></span>](#ColorRules)  
  
    3.  [<span data-ttu-id="d71d0-120">색 눈금의 데이터 형식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="d71d0-120">Format the Data in the Color Scale as Currency</span></span>](#ColorScale)  
  
    4.  [<span data-ttu-id="d71d0-121">새 범례 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-121">Create a New Legend</span></span>](#NewLegend)  
  
    5.  [<span data-ttu-id="d71d0-122">범례와 색 규칙 연결</span><span class="sxs-lookup"><span data-stu-id="d71d0-122">Associate Legend and Color Rules</span></span>](#Associate)  
  
    6.  [<span data-ttu-id="d71d0-123">데이터가 없는 군에서 색 지우기</span><span class="sxs-lookup"><span data-stu-id="d71d0-123">Clear Color from Counties with No Data</span></span>](#NoData)  
  
7.  [<span data-ttu-id="d71d0-124">사용자 지정 점 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-124">Add a Custom Point</span></span>](#CustomPoint)  
  
8.  [<span data-ttu-id="d71d0-125">지도 보기 가운데 맞추기</span><span class="sxs-lookup"><span data-stu-id="d71d0-125">Center the Map View</span></span>](#CenterView)  
  
9. [<span data-ttu-id="d71d0-126">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-126">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="d71d0-127">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="d71d0-127">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="d71d0-128">이 자습서에서 마법사의 단계는 두 개의 절차로 통합됩니다. 하나는 데이터 세트를 만드는 절차이고 다른 하나는 테이블을 만드는 절차입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-128">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="d71d0-129">보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 세트를 만들고, 마법사를 실행하는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d71d0-129">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="d71d0-130">이 자습서에 소요되는 예상 시간: 30분</span><span class="sxs-lookup"><span data-stu-id="d71d0-130">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71d0-131">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d71d0-131">Requirements</span></span>  
 <span data-ttu-id="d71d0-132">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d71d0-132">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a><span data-ttu-id="d71d0-133">1. 지도 마법사에서 다각형 계층을 사용 하 여 지도 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-133">1. Create a Map with a Polygon Layer from the Map Wizard</span></span>  
 <span data-ttu-id="d71d0-134">지도 갤러리에서 보고서에</span><span class="sxs-lookup"><span data-stu-id="d71d0-134">Add a map to your report from the map gallery.</span></span> <span data-ttu-id="d71d0-135">뉴욕 주의 군을 표시하는 계층이 하나 있는 지도를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-135">The map has one layer that displays the counties in New York state.</span></span> <span data-ttu-id="d71d0-136">각 군의 모양은 지도 갤러리의 지도에 포함된 공간 데이터를 기반으로 하는 다각형으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-136">The shape of each county is a polygon based on spatial data that is embedded in the map from the map gallery.</span></span>  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a><span data-ttu-id="d71d0-137">새 보고서에서 지도 마법사를 사용하여 지도를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-137">To add a map with the map wizard in a new report</span></span>  
  
1.  <span data-ttu-id="d71d0-138">**시작**을 클릭 하 고 **프로그램**, 보고서 작성기을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-138">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="d71d0-139">시작 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-139">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d71d0-140">시작 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-140">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="d71d0-141">왼쪽 창에서 **보고서** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-141">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="d71d0-142">오른쪽 창에서 **지도 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-142">In the right pane, click **Map Wizard**.</span></span>  
  
4.  <span data-ttu-id="d71d0-143">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-143">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="d71d0-144">**공간 데이터의 원본 선택** 페이지에서 **지도 갤러리** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-144">**Choose a source of spatial data** page, verify that **Map gallery** is selected.</span></span>  
  
6.  <span data-ttu-id="d71d0-145">지도 갤러리 창에서 미국, **대한민국**에서 시/ **군** /시를 확장 하 고 **뉴욕**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-145">In the Map Gallery pane, expand **States by County** under **USA**, and click **New York**.</span></span>  
  
     <span data-ttu-id="d71d0-146">지도 미리 보기 창에 뉴욕 주 지도가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-146">The Map Preview pane displays the New York county map.</span></span>  
  
7.  <span data-ttu-id="d71d0-147">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-147">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d71d0-148">**공간 데이터 및 지도 보기 옵션 선택** 페이지에서 기본값을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-148">On the **Choose spatial data and map view options** page, accept the defaults.</span></span> <span data-ttu-id="d71d0-149">기본적으로 지도 갤러리의 지도 요소는 보고서 정의에 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-149">By default, map elements from a map gallery will automatically be embedded in the report definition.</span></span>  
  
9. <span data-ttu-id="d71d0-150">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-150">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d71d0-151">**지도 시각화 선택** 페이지에서 **기본 지도** 가 선택되어 있는지 확인하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-151">On the **Choose map visualization** page, verify **Basic Map** is selected, and click **Next**.</span></span>  
  
11. <span data-ttu-id="d71d0-152">**색 테마 및 데이터 시각화 선택** 페이지에서 **레이블 표시** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-152">On the **Choose color theme and data visualization** page, select the **Display labels** option.</span></span>  
  
12. <span data-ttu-id="d71d0-153">**단색 지도** 옵션이 선택되어 있으면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-153">If it is selected, clear the **Single color map** option.</span></span>  
  
13. <span data-ttu-id="d71d0-154">**데이터 필드** 드롭다운 목록에서 #COUNTYNAME을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-154">From the **Data field** drop-down list, click #COUNTYNAME.</span></span> <span data-ttu-id="d71d0-155">마법사의 지도 미리 보기 창에 다음 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-155">The Map Preview pane in the wizard displays the following items:</span></span>  
  
    -   <span data-ttu-id="d71d0-156">**지도 제목**텍스트가 포함된 제목</span><span class="sxs-lookup"><span data-stu-id="d71d0-156">A title with the text **Map Title**.</span></span>  
  
    -   <span data-ttu-id="d71d0-157">뉴욕의 군을 표시하는 지도. 각 군이 다른 색이고 군 이름이 군 지역 위의 적절한 곳에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-157">A map that displays counties in New York where each county is a different color and the county name appears wherever it fits over the county area.</span></span>  
  
    -   <span data-ttu-id="d71d0-158">제목과 항목 1 ~ 5의 목록이 포함된 범례</span><span class="sxs-lookup"><span data-stu-id="d71d0-158">A legend that contains a title and a list of items 1 through 5.</span></span>  
  
    -   <span data-ttu-id="d71d0-159">값 1 ~ 160이 포함되고 색이 없는 색 눈금</span><span class="sxs-lookup"><span data-stu-id="d71d0-159">A color scale that contains values 0 to 160 and no color.</span></span>  
  
    -   <span data-ttu-id="d71d0-160">킬로미터(km) 및 마일(mi)이 표시되는 거리 눈금</span><span class="sxs-lookup"><span data-stu-id="d71d0-160">A distance scale that displays kilometers (km) and miles (mi).</span></span>  
  
14. <span data-ttu-id="d71d0-161">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-161">Click **Finish**.</span></span>  
  
     <span data-ttu-id="d71d0-162">디자인 화면에 지도가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-162">The map is added to the design surface.</span></span>  
  
15. <span data-ttu-id="d71d0-163">지도를 클릭 하 여 선택 하 고 **지도 계층 창을**표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-163">Click the map to select it and display the **Map Layers Pane**.</span></span> <span data-ttu-id="d71d0-164">**지도 계층 창** 에는 **포함**계층 유형의 다각형 계층이 하나 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-164">The **Map Layers Pane** shows one polygon layer of layer type **Embedded**.</span></span> <span data-ttu-id="d71d0-165">각 군은 이 계층의 포함된 지도 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-165">Each county is an embedded map element on this layer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d71d0-166">**지도 계층** 창이 표시 되지 않으면 현재 보기 외부에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-166">If you do not see the **Map Layers** pane, it might be displayed outside your current view.</span></span> <span data-ttu-id="d71d0-167">디자인 뷰 창의 아래쪽에 있는 스크롤 막대를 사용하여 뷰를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-167">Use the scroll bar at the bottom of the Design view window to change your view.</span></span> <span data-ttu-id="d71d0-168">또는 **보기** 탭에서 **속성** 또는 **보고서 데이터** 옵션의 선택을 취소 하 여 더 많은 디자인 화면 영역을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-168">Alternatively, in the **View** tab, clear the **Properties** or the **Report Data** option to provide more design surface area.</span></span>  
  
16. <span data-ttu-id="d71d0-169">지도 제목을 마우스 오른쪽 단추로 클릭 한 다음 **제목 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-169">Right-click the map title, and then click **Title Properties**.</span></span>  
  
17. <span data-ttu-id="d71d0-170">제목 텍스트를 **Sales By Store**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-170">Replace the title text with **Sales by Store**.</span></span>  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. <span data-ttu-id="d71d0-171">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-171">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-172">렌더링된 보고서에 지도 제목, 지도 및 거리 눈금이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-172">The rendered report displays the map title, the map, and the distance scale.</span></span> <span data-ttu-id="d71d0-173">군은 지도 다각형 계층에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-173">The counties are on a map polygon layer.</span></span> <span data-ttu-id="d71d0-174">각 군은 색상표의 색으로 구분되지만 해당 색은 데이터와 연결되어 있지 않은 다각형으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-174">Each county is a polygon that varies by color from a color palette, but the colors are not associated with any data.</span></span> <span data-ttu-id="d71d0-175">거리 눈금에는 킬로미터와 마일 단위로 거리가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-175">The distance scale displays distances in both kilometers and miles.</span></span>  
  
 <span data-ttu-id="d71d0-176">각 군과 연결된 분석 데이터가 없기 때문에 지도 범례와 색 눈금은 아직 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-176">The map legend and color scale do not yet appear because there is no analytical data associated with each county.</span></span> <span data-ttu-id="d71d0-177">이 자습서의 뒷부분에서 분석 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-177">You will add analytical data later in this tutorial.</span></span>  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a><span data-ttu-id="d71d0-178">2. 지도 점 계층을 추가 하 여 상점 위치 표시</span><span class="sxs-lookup"><span data-stu-id="d71d0-178">2. Add a Map Point Layer to Display Store Locations</span></span>  
 <span data-ttu-id="d71d0-179">지도 계층 마법사를 사용하여 상점의 위치를 표시하는 점 계층을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-179">Use the map layer wizard to add a point layer that displays the locations of stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d71d0-180">이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-180">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="d71d0-181">따라서 쿼리가 상당히 길어집니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-181">This makes the query quite long.</span></span> <span data-ttu-id="d71d0-182">비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-182">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="d71d0-183">이 자습서의 쿼리는 학습용으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-183">This is for learning purposes only.</span></span>  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a><span data-ttu-id="d71d0-184">SQL Server 공간 쿼리에 따라 점 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-184">To add a point layer based on a SQL Server spatial query</span></span>  
  
1.  <span data-ttu-id="d71d0-185">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-185">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-186">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-186">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="d71d0-187">도구 모음에서 **새 계층 마법사** 단추 ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-187">On the toolbar, click the **New layer wizard** button ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").</span></span>  
  
3.  <span data-ttu-id="d71d0-188">**공간 데이터의 원본 선택** 페이지에서 **SQL Server 공간 쿼리**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-188">On the **Choose a source of spatial data** page, select **SQL Server spatial query**, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="d71d0-189">**SQL Server 공간 데이터를 사용 하 여 데이터 집합 선택** 페이지에서 **SQL Server 공간 데이터가 있는 새 데이터 집합 추가**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-189">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d71d0-190">**SQL Server 공간 데이터 원본에 대한 연결을 선택하십시오.** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버로 이동한 후 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-190">On the **Choose a connection to a SQL Server spatial data source** page, select an existing data source or browse to the report server and select a data source.</span></span>  
  
6.  <span data-ttu-id="d71d0-191">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-191">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d71d0-192">쿼리 디자인 페이지에서 **텍스트로 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-192">On the Design a Query page, click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="d71d0-193">쿼리 창에서 다음 텍스트를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-193">Paste the following text in the query pane:</span></span>  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. <span data-ttu-id="d71d0-194">쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-194">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="d71d0-195">결과 집합에는 StoreName Key,, SellingArea, City, 관할지, Sales 및 Spatiallocation이의 7 개 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-195">The result set displays seven columns: StoreKey, StoreName, SellingArea, City, County, Sales, and SpatialLocation.</span></span> <span data-ttu-id="d71d0-196">이 데이터는 소비재를 판매하는 뉴욕 주의 상점 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-196">This data represents a set of stores in New York State that sell consumer goods.</span></span> <span data-ttu-id="d71d0-197">결과 집합의 각 행에는 상점 식별자, 상점 이름, 제품 전시 구역, 상점이 있는 도시와 군, 판매량 합계, 경도와 위도로 나타낸 공간 위치 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-197">Each row in the result set contains a store identifier, store name, the area available for product display, the city and county where the store is located, the sales total, and the spatial location in longitude and latitude.</span></span> <span data-ttu-id="d71d0-198">전시 구역의 범위는 455제곱피트(42제곱미터)부터 1125제곱피트(105제곱미터)까지입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-198">The display area ranges from 455 square feet to 1125 square feet.</span></span>  
  
10. <span data-ttu-id="d71d0-199">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-199">Click **Next**.</span></span>  
  
     <span data-ttu-id="d71d0-200">DataSet1이라는 보고서 데이터 세트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-200">The report dataset named DataSet1 is created for you.</span></span> <span data-ttu-id="d71d0-201">마법사를 완료한 후 보고서 데이터를 사용하여 해당 필드 컬렉션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-201">After you complete the wizard, you can use the Report Data to its field collection.</span></span>  
  
11. <span data-ttu-id="d71d0-202">**공간 데이터 및 지도 보기 옵션 선택** 페이지에서 **공간 필드가** 이 `SpatialLocation` 고 **계층 유형이** **점**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-202">On the **Choose a spatial data and map view options** page, verify that the **Spatial field** is `SpatialLocation` and that the **Layer type** is **Point**.</span></span> <span data-ttu-id="d71d0-203">이 페이지의 다른 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-203">Accept the other defaults on this page.</span></span>  
  
     <span data-ttu-id="d71d0-204">지도 보기에 각 상점의 위치를 표시하는 원이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-204">The map view displays circles that mark the location of each store.</span></span>  
  
12. <span data-ttu-id="d71d0-205">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-205">Click **Next**.</span></span>  
  
13. <span data-ttu-id="d71d0-206">분석 데이터에 따라 달라지는 표식을 표시하는 지도 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-206">Specify a map type that displays markers that vary by analytic data.</span></span> <span data-ttu-id="d71d0-207">지도 시각화 선택 페이지에서 **분석 표식 지도**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-207">On the Choose map visualization page, click **Analytical Marker Map**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="d71d0-208">**분석 데이터 집합 선택** 페이지에서 DataSet1를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-208">On the **Choose the analytical dataset** page, click DataSet1.</span></span> <span data-ttu-id="d71d0-209">이 데이터 세트에는 새 점 계층에 표시될 분석 데이터와 공간 데이터가 모두 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-209">This dataset contains both analytical data and spatial data that will be displayed on the new point layer.</span></span>  
  
15. <span data-ttu-id="d71d0-210">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-210">Click **Next**.</span></span>  
  
16. <span data-ttu-id="d71d0-211">**색 테마 및 데이터 시각화 선택** 페이지에서 **표식 색을 사용 하 여 데이터 시각화** 옵션의 선택을 취소 하 고 **표식 유형을 사용 하 여 데이터 시각화**옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-211">On the **Choose color theme and data visualization** page, clear the **Use marker colors to visualize data** option, and then select the option **Use marker types to visualize data**.</span></span>  
  
17. <span data-ttu-id="d71d0-212">**데이터 필드**에서 매장이 `[Sum(SellingArea)]` 제품을 표시 하기 위해 따로 설정 하는 영역의 크기에 따라 표식 유형을 변경 하려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-212">In **Data field**, select `[Sum(SellingArea)]` to vary marker types by the size of the area a store sets aside to display the products.</span></span>  
  
18. <span data-ttu-id="d71d0-213">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-213">Click **Finish**.</span></span>  
  
     <span data-ttu-id="d71d0-214">보고서에 지도 계층이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-214">The map layer is added to the report.</span></span> <span data-ttu-id="d71d0-215">범례에 SellingArea 값에 따른 표식 유형이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-215">The legend displays marker types based on SellingArea values.</span></span>  
  
     <span data-ttu-id="d71d0-216">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-216">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="d71d0-217">**지도 계층** 창에 공간 데이터 원본 유형이 **DataRegion**인 새 계층 PointLayer1이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-217">The **Map Layer** pane displays a new layer, PointLayer1, with spatial data source type **DataRegion**.</span></span>  
  
19. <span data-ttu-id="d71d0-218">범례 제목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-218">Add a legend title.</span></span> <span data-ttu-id="d71d0-219">범례 제목을 마우스 오른쪽 단추로 클릭 한 다음 **범례 제목 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-219">Right-click the legend title, and then click **Legend Title Properties**.</span></span>  
  
20. <span data-ttu-id="d71d0-220">제목을 삭제 하 고 **표시 영역 (평방 피트)** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-220">Delete the title, and type **Display Area (Square Feet)**.</span></span>  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. <span data-ttu-id="d71d0-221">마법사를 통해 설정된 기본값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-221">View the default values that were set by the wizard.</span></span> <span data-ttu-id="d71d0-222">**지도 계층 창**에서 점 계층을 마우스 오른쪽 단추로 클릭 한 다음 **표식 유형 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-222">In the **Map Layers Pane**, right-click the point layer, and then click **Marker Type Rule**.</span></span>  
  
     <span data-ttu-id="d71d0-223">**일반** 탭에서 표식은 범례에 표시 되는 순서 대로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-223">On the **General** tab, the markers are listed in the order in which they appear in the legend.</span></span> <span data-ttu-id="d71d0-224">**배포** 탭에서 하위 범위의 수는 5입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-224">On the **Distribution** tab, the number of subranges is 5.</span></span> <span data-ttu-id="d71d0-225">**범례** 탭에서 범례 텍스트는 각 범위의 시작 값과 끝 값을 표시 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-225">On the **Legend** tab, the legend text is set to display the start and end value in each range.</span></span>  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. <span data-ttu-id="d71d0-226">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-226">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-227">지도에 뉴욕 주에 있는 상점의 위치가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-227">The map displays the locations of stores in New York state.</span></span> <span data-ttu-id="d71d0-228">각 상점의 표식 유형은 전시 구역에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-228">The marker type for each store is based on the display area.</span></span> <span data-ttu-id="d71d0-229">이 자습서에는 다섯 개의 전시 구역 범위가 자동으로 계산되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-229">Five ranges of display area were automatically calculated for you.</span></span>  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a><span data-ttu-id="d71d0-230">3. 지도 선 계층을 추가 하 여 경로 표시</span><span class="sxs-lookup"><span data-stu-id="d71d0-230">3. Add a Map Line Layer to Display a Route</span></span>  
 <span data-ttu-id="d71d0-231">지도 계층 마법사를 사용하여 두 상점 간의 경로를 표시하는 지도 계층을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-231">Use the map layer wizard to add a map layer that displays a route between two stores.</span></span> <span data-ttu-id="d71d0-232">이 자습서에서는 세 개의 상점 위치를 연결하는 경로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-232">In this tutorial, the path is created from three store locations.</span></span> <span data-ttu-id="d71d0-233">비즈니스 애플리케이션에서 이 경로는 상점 간 최적 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-233">In a business application, the path might be the best route between stores.</span></span>  
  
#### <a name="to-add-a-line-layer-to-map"></a><span data-ttu-id="d71d0-234">선 계층을 지도에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-234">To add a line layer to map</span></span>  
  
1.  <span data-ttu-id="d71d0-235">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-235">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-236">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-236">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="d71d0-237">도구 모음에서 **새 계층 마법사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-237">On the toolbar, click **New layer wizard**.</span></span>  
  
3.  <span data-ttu-id="d71d0-238">**공간 데이터의 원본 선택** 페이지에서 **SQL Server 공간 쿼리** 를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-238">On the **Choose a source of spatial data** page, select **SQL Server spatial query** and click **Next**.</span></span>  
  
4.  <span data-ttu-id="d71d0-239">**SQL Server 공간 데이터가 있는 데이터 세트 선택** 페이지에서 **SQL Server 공간 데이터가 있는 새 데이터 세트 추가**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-239">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data** and click **Next**.</span></span>  
  
5.  <span data-ttu-id="d71d0-240">**SQL Server 공간 데이터 원본에 대 한 연결을 선택**하십시오 .에서 첫 번째 절차에서 만든 데이터 원본인 DataSource1를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-240">On the **Choose a connection to a SQL Server spatial data source**, select DataSource1, the data source that you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="d71d0-241">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-241">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d71d0-242">**쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-242">On the **Design a Query** page, click **Edit as Text**.</span></span> <span data-ttu-id="d71d0-243">쿼리 디자이너가 텍스트 기반 모드로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-243">The query designer switches to text-based mode.</span></span>  
  
8.  <span data-ttu-id="d71d0-244">쿼리 창에서 다음 텍스트를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-244">Paste the following text in the query pane:</span></span>  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. <span data-ttu-id="d71d0-245">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-245">Click **Next**.</span></span>  
  
     <span data-ttu-id="d71d0-246">지도에 세 개의 상점을 연결하는 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-246">A path appears on the map that connects three stores.</span></span>  
  
10. <span data-ttu-id="d71d0-247">**공간 데이터 및 지도 보기 옵션 선택** 페이지에서 **공간 필드** 가 **Route** 이고 **계층 유형** 이 **선**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-247">On the **Choose spatial data and map view options** page, verify that the **Spatial field** is **Route** and that the **Layer type** is **Line**.</span></span> <span data-ttu-id="d71d0-248">다른 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-248">Accept the other defaults.</span></span>  
  
     <span data-ttu-id="d71d0-249">지도 보기에 뉴욕 주 북부에 있는 한 상점에서 뉴욕 주 남부에 있는 한 상점까지의 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-249">The map view displays a path from a store in the northern part of New York state to a store in the southern part of New York state.</span></span>  
  
11. <span data-ttu-id="d71d0-250">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-250">Click **Next**.</span></span>  
  
12. <span data-ttu-id="d71d0-251">**지도 시각화 선택** 페이지에서 **기본 선 지도**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-251">On the **Choose map visualization** page, click **Basic Line Map**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="d71d0-252">**색 테마 및 데이터 시각화 선택**에서 **단색 지도**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-252">On the **Choose color theme and data visualization**, select the option **Single color map**.</span></span> <span data-ttu-id="d71d0-253">경로가 선택한 테마에 따라 단색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-253">The path appears as a single color based on the selected theme.</span></span>  
  
14. <span data-ttu-id="d71d0-254">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-254">Click **Finish**.</span></span>  
  
 <span data-ttu-id="d71d0-255">지도에 공간 데이터 원본 유형 **데이터 집합이**있는 새 선 계층이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-255">The map displays a new line layer with spatial data source type **DataSet**.</span></span> <span data-ttu-id="d71d0-256">이 예제에서 공간 데이터는 데이터 세트에서 제공되지만 분석 데이터가 선과 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-256">In this example, the spatial data comes from a dataset but no analytical data is associated with the line.</span></span>  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a><span data-ttu-id="d71d0-257">4. Bing Maps 타일 배경 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-257">4. Add a Bing Maps Tile Background</span></span>  
 <span data-ttu-id="d71d0-258">Bing Maps 타일 배경을 표시하는 지도 계층을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-258">Add a map layer that displays a Bing Maps tile background.</span></span>  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a><span data-ttu-id="d71d0-259">Virtual Earth 타일 배경을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-259">To add a Virtual Earth tile background</span></span>  
  
1.  <span data-ttu-id="d71d0-260">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-260">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-261">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-261">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="d71d0-262">도구 모음에서 **계층 추가**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-262">On the toolbar, click **Add Layer**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").</span></span>  
  
3.  <span data-ttu-id="d71d0-263">드롭다운 목록에서 **타일 계층**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-263">From the drop-down list, click **Tile Layer**.</span></span>  
  
     <span data-ttu-id="d71d0-264">**지도 계층** 창의 마지막 계층은 TileLayer1입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-264">The last layer in the **Map Layer** pane is TileLayer1.</span></span> <span data-ttu-id="d71d0-265">기본적으로 타일 계층에는 도로 지도 스타일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-265">By default, the tile layer displays the road map style.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d71d0-266">마법사의 **공간 데이터 및 지도 보기 옵션 선택** 페이지에서 타일 계층을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-266">In the wizard, you can also add a tile layer on the **Choose spatial data and map view options** page.</span></span> <span data-ttu-id="d71d0-267">이렇게 하려면 **이 지도 보기에 대해 Bing 지도 배경 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-267">To do this, select **Add a Bing Maps background for this map view**.</span></span> <span data-ttu-id="d71d0-268">렌더링된 보고서의 타일 배경에 현재 지도 뷰포트 중심과 확대/축소 수준에 해당하는 Bing Maps 타일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-268">In a rendered report, the tile background displays Bing Maps tiles for the current map viewport center and zoom level.</span></span>  
  
4.  <span data-ttu-id="d71d0-269">TileLayer1에서 아래쪽 화살표를 클릭 한 다음 **타일 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-269">Click the down arrow on TileLayer1, and then click **Tile Properties**.</span></span>  
  
5.  <span data-ttu-id="d71d0-270">**유형**에서 **항공**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-270">In **Type**, select **Aerial**.</span></span> <span data-ttu-id="d71d0-271">항공 보기에는 텍스트가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-271">The aerial view does not contain text.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a><span data-ttu-id="d71d0-272">5. 계층을 투명 하 게 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-272">5. Make a Layer Transparent</span></span>  
 <span data-ttu-id="d71d0-273">한 계층의 항목이 다른 계층을 통과하여 표시되도록 하려면 원하는 효과를 얻을 때까지 계층의 순서와 각 계층의 투명도를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-273">To let the items on one layer show through another layer, you can adjust the order of layers and the transparency of each layer to get the effect that you want.</span></span>  
  
#### <a name="to-set-the-transparency-of-a-layer"></a><span data-ttu-id="d71d0-274">계층의 투명도를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-274">To set the transparency of a layer</span></span>  
  
1.  <span data-ttu-id="d71d0-275">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-275">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-276">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-276">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="d71d0-277">PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 **계층 데이터**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-277">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="d71d0-278">**지도 다각형 계층 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-278">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="d71d0-279">**표시 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-279">Click **Visibility**.</span></span>  
  
5.  <span data-ttu-id="d71d0-280">**투명도 (%)** 에 **30**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-280">In **Transparency (%)**, type **30**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="d71d0-281">디자인 화면에 군이 반투명으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-281">The design surface displays the counties as semi-transparent.</span></span>  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a><span data-ttu-id="d71d0-282">6. 판매량을 기준으로 군 색 변경</span><span class="sxs-lookup"><span data-stu-id="d71d0-282">6. Vary County Color Based on Sales</span></span>  
 <span data-ttu-id="d71d0-283">보고서 처리기가 지도 마법사의 마지막 페이지에서 선택한 테마에 따라 색상표에서 색 값을 자동으로 할당하기 때문에 다각형 계층에 있는 각 군의 색은 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-283">Each county on the polygon layer has a different color because the report processor automatically assigns a color value from the color palette based on the theme that you chose on the last page of the map wizard.</span></span>  
  
 <span data-ttu-id="d71d0-284">다음 단계에서는 특정 색을 각 군의 상점별 판매량 범위와 연결하는 색 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-284">In the following steps, specify a color rule to associate specific colors with a range of store sales for each county.</span></span> <span data-ttu-id="d71d0-285">빨강-노랑-녹색은 상대적인 높은-중간-낮은 판매량을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-285">The colors red-yellow-green indicate relative high-middle-low sales.</span></span> <span data-ttu-id="d71d0-286">통화를 표시하도록 색 눈금의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-286">Format the color scale to show currency.</span></span> <span data-ttu-id="d71d0-287">새 범례에서 연간 판매량 범위를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-287">Display the annual sales ranges in a new legend.</span></span> <span data-ttu-id="d71d0-288">상점이 없는 군의 경우 연결된 데이터가 없음을 표시하기 위해 색을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-288">For counties that do not contain stores, use no color to show that there is no associated data.</span></span>  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a><span data-ttu-id="d71d0-289">6a.</span><span class="sxs-lookup"><span data-stu-id="d71d0-289">6a.</span></span> <span data-ttu-id="d71d0-290">공간 데이터와 분석 데이터 간의 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-290">Build a Relationship between Spatial and Analytical Data</span></span>  
 <span data-ttu-id="d71d0-291">분석 데이터에 따른 색으로 군 모양을 변경하려면 먼저 분석 데이터를 공간 데이터와 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-291">To vary the county shapes by color based on analytical data, you first must associate the analytical data with the spatial data.</span></span> <span data-ttu-id="d71d0-292">이 자습서에서는 일치시킬 군 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-292">In this tutorial, you will use the county name to match on.</span></span>  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a><span data-ttu-id="d71d0-293">공간 데이터와 분석 데이터 간의 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-293">To build a relationship between spatial data and analytical data</span></span>  
  
1.  <span data-ttu-id="d71d0-294">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-294">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-295">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-295">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="d71d0-296">PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 **계층 데이터**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-296">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="d71d0-297">**지도 다각형 계층 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-297">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="d71d0-298">**분석 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-298">Click **Analytical data**.</span></span>  
  
5.  <span data-ttu-id="d71d0-299">드롭다운 목록에서 DataSet1을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-299">From the drop-down list, select DataSet1.</span></span> <span data-ttu-id="d71d0-300">이 데이터 세트은 군에 대한 공간 데이터 쿼리를 지정했을 때 마법사에서 만들어진 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-300">This dataset was created by the wizard when you specified the spatial data query for the counties.</span></span>  
  
6.  <span data-ttu-id="d71d0-301">**일치 시킬 필드**에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-301">In **Fields to match on**, click **Add**.</span></span> <span data-ttu-id="d71d0-302">새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-302">A new row is added.</span></span>  
  
7.  <span data-ttu-id="d71d0-303">**공간 데이터 집합**의 드롭다운 목록에서 COUNTYNAME를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-303">In **From spatial dataset**, from the drop-down list, click COUNTYNAME.</span></span>  
  
8.  <span data-ttu-id="d71d0-304">**분석 데이터 집합**의 드롭다운 목록에서 [국가]를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-304">In **From analytical dataset**, from the drop-down list, click [County].</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="d71d0-305">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-305">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-306">공간 데이터 원본과 분석 데이터 세트에서 일치 필드를 지정하면 보고서 처리기가 지도 요소에 따라 분석 데이터를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-306">By specifying a match field from the spatial data source and from the analytical dataset, you enable the report processor to group analytical data based on the map elements.</span></span> <span data-ttu-id="d71d0-307">데이터 바인딩된 지도 요소에는 지정한 값에 대한 성공적인 일치 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-307">A data-bound map element has a successful match for the values that you specified.</span></span>  
  
 <span data-ttu-id="d71d0-308">상점이 있는 각 군은 마법사에서 선택한 스타일의 색상표를 기반으로 하는 색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-308">Each county that contains a store has a color that is based on the color palette for the style that you chose in the wizard.</span></span>  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a><span data-ttu-id="d71d0-309">6b.</span><span class="sxs-lookup"><span data-stu-id="d71d0-309">6b.</span></span> <span data-ttu-id="d71d0-310">다각형에 대한 색 규칙 지정</span><span class="sxs-lookup"><span data-stu-id="d71d0-310">Specify Color Rules for Polygons</span></span>  
 <span data-ttu-id="d71d0-311">상점 판매량을 기반으로 각 군의 색을 변경하는 규칙을 만들려면 범위 값, 표시할 범위 내의 하위 범위 수 및 사용할 색을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-311">To create a rule that varies the color of each county based store sales, you must specify the range values, the number of divisions within that range that you want to display, and the colors to use.</span></span>  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a><span data-ttu-id="d71d0-312">연결된 데이터가 있는 모든 다각형에 대한 색 규칙을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-312">To specify color rules for all polygons that have associated data</span></span>  
  
1.  <span data-ttu-id="d71d0-313">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-313">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-314">PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 **다각형 색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-314">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="d71d0-315">**지도 색 규칙 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-315">The **Map Color Rules Properties** dialog box opens.</span></span> <span data-ttu-id="d71d0-316">색 규칙 옵션 **색상표를 사용하여 데이터 시각화** 가 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-316">Notice that the color rule option **Visualize data by using color palette** is selected.</span></span> <span data-ttu-id="d71d0-317">이 옵션은 마법사에서 설정된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-317">This option was set by the wizard.</span></span>  
  
3.  <span data-ttu-id="d71d0-318">**색 범위를 사용하여 데이터 시각화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-318">Select **Visualize data by using color ranges**.</span></span> <span data-ttu-id="d71d0-319">색상표 옵션이 시작 색, 중간 색 및 마지막 색 옵션으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-319">The palette option is replaced by start color, middle color, and end color options.</span></span>  
  
4.  <span data-ttu-id="d71d0-320">군별 판매량에 대한 범위 값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-320">Define range values for sales per county.</span></span> <span data-ttu-id="d71d0-321">**데이터 필드**의 드롭다운 목록에서 `[Sum(Sales)]`을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-321">In **Data field**, from the drop-down list, select `[Sum(Sales)]`.</span></span>  
  
5.  <span data-ttu-id="d71d0-322">통화가 천 단위로 표시되도록 형식을 변경하려면 식을 다음과 같이 변경합니다. `=Sum(Fields!Sales.Value)/1000`</span><span class="sxs-lookup"><span data-stu-id="d71d0-322">To change the format to display currency in thousands, change the expression to the following: `=Sum(Fields!Sales.Value)/1000`</span></span>  
  
6.  <span data-ttu-id="d71d0-323">**시작 색** 을 **빨강**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-323">Change **Start color** to **Red**.</span></span>  
  
7.  <span data-ttu-id="d71d0-324">**마지막 색** 을 **녹색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-324">Change **End color** to **Green**.</span></span>  
  
     <span data-ttu-id="d71d0-325">**빨강** 은 낮은 판매량 값을 나타내고, **노랑** 은 중간 판매량 값을 나타내며, **녹색** 은 높은 판매량 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-325">**Red** represents low sales values, **Yellow** represents middle sales values, and **Green** represents high sales values.</span></span> <span data-ttu-id="d71d0-326">보고서 처리기는 이러한 값과 **분포** 페이지에서 선택한 옵션에 따라 색의 범위를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-326">The report processor calculates a range of colors based on these values and the options that you choose on the **Distribution** page.</span></span>  
  
8.  <span data-ttu-id="d71d0-327">**분포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-327">Click **Distribution**.</span></span>  
  
9. <span data-ttu-id="d71d0-328">분포 유형이 **최적**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-328">Verify that the distribution type is **Optimal**.</span></span> <span data-ttu-id="d71d0-329">5단계에 있는 식의 경우 최적 분포는 각 범위에 있는 항목 수와 각 범위 간격의 균형을 맞추는 하위 범위로 값을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-329">For the expression from step 5, optimal distribution divides the values into subranges that balance the number of items in each range and the span for each range.</span></span>  
  
10. <span data-ttu-id="d71d0-330">이 페이지에 있는 다른 옵션에 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-330">Accept the default values for other options on this page.</span></span> <span data-ttu-id="d71d0-331">최적 배포 유형을 선택하는 경우 보고서가 실행될 때 하위 범위의 수가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-331">When you select the optimal distribution type, the number of subranges are calculated when the report runs.</span></span>  
  
11. <span data-ttu-id="d71d0-332">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-332">Click **Legend**.</span></span>  
  
12. <span data-ttu-id="d71d0-333">**색 눈금 옵션**에서 **색 눈금에 표시** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-333">In **Color scale options**, verify that **Show in color scale** is selected.</span></span>  
  
13. <span data-ttu-id="d71d0-334">**이 범례에 표시**의 드롭다운 목록에서 빈 줄을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-334">In **Show in this legend**, from the drop-down list, select the blank line.</span></span> <span data-ttu-id="d71d0-335">이제부터 색 눈금에서만 색 범위가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-335">For now, you will show the color ranges only in the color scale.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="d71d0-336">색 눈금에 빨강, 주황, 노랑, 황록색 및 녹색이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-336">The color scale displays five colors: red, orange, yellow, yellow green, and green.</span></span> <span data-ttu-id="d71d0-337">각 색은 군별 판매량에 따라 자동으로 계산되는 판매량 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-337">Each color represents a sales range that is automatically calculated based on the sales by county.</span></span>  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a><span data-ttu-id="d71d0-338">6c.</span><span class="sxs-lookup"><span data-stu-id="d71d0-338">6c.</span></span> <span data-ttu-id="d71d0-339">색 눈금의 데이터 형식을 통화로 지정</span><span class="sxs-lookup"><span data-stu-id="d71d0-339">Format the Data in the Color Scale as Currency</span></span>  
 <span data-ttu-id="d71d0-340">기본적으로 데이터는 일반 형식을 사용하지만</span><span class="sxs-lookup"><span data-stu-id="d71d0-340">By default, data has a general format.</span></span> <span data-ttu-id="d71d0-341">사용자 지정 형식을 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-341">You can apply custom formats.</span></span>  
  
##### <a name="to-set-the-format-for-the-color-scale"></a><span data-ttu-id="d71d0-342">색 눈금의 형식을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-342">To set the format for the color scale</span></span>  
  
1.  <span data-ttu-id="d71d0-343">색 눈금을 마우스 오른쪽 단추로 클릭 한 다음 **색 눈금 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-343">Right-click the color scale, and then click **Color Scale Properties**.</span></span>  
  
2.  <span data-ttu-id="d71d0-344">**숫자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-344">Click **Number**.</span></span>  
  
3.  <span data-ttu-id="d71d0-345">**범주**에서 **통화**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-345">In **Category**, click **Currency**.</span></span>  
  
4.  <span data-ttu-id="d71d0-346">**소수 자릿수**에 **0**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-346">In **Decimal places**, type **0**.</span></span> <span data-ttu-id="d71d0-347">이 형식은 통화에 소수 자릿수가 없음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-347">This format specifies no decimal places for currency.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="d71d0-348">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-348">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-349">색 눈금에 각 범위에 대한 통화 형식으로 연간 판매량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-349">The color scale displays annual sales in currency format for each range.</span></span>  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a><span data-ttu-id="d71d0-350">6d.</span><span class="sxs-lookup"><span data-stu-id="d71d0-350">6d.</span></span> <span data-ttu-id="d71d0-351">새 범례 만들기</span><span class="sxs-lookup"><span data-stu-id="d71d0-351">Create a New Legend</span></span>  
 <span data-ttu-id="d71d0-352">기본적으로 모든 규칙은 첫 번째 범례에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-352">By default, all rules display in the first legend.</span></span> <span data-ttu-id="d71d0-353">지도의 표시를 향상시키기 위해 범례를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-353">To improve the display for a map, you can add legends.</span></span>  
  
 <span data-ttu-id="d71d0-354">기본 표시를 변경하려면 새 범례를 만들고 지도 계층에 대한 규칙 결과를 새 범례와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-354">To change the default display, there are two steps: create a new legend and then associate the rule results for a map layer with the new legend.</span></span>  
  
##### <a name="to-create-a-new-legend"></a><span data-ttu-id="d71d0-355">새 범례를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-355">To create a new legend</span></span>  
  
1.  <span data-ttu-id="d71d0-356">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-356">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-357">뷰포트 외부의 지도를 마우스 오른쪽 단추로 클릭 한 다음 **범례 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-357">Right-click the map outside the viewport, and then click **Add Legend**.</span></span> <span data-ttu-id="d71d0-358">새 범례가 지도의 기본 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-358">A new legend is added to the map at a default location.</span></span>  
  
3.  <span data-ttu-id="d71d0-359">범례를 마우스 오른쪽 단추로 클릭 한 다음 **범례 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-359">Right-click the legend, and then click **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="d71d0-360">**위치 옵션**에서 뷰포트를 기준으로 범례를 표시할 위치를 지정 하는 위치를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-360">In **Position options**, click the location that specifies where you want the legend to appear relative to the viewport.</span></span> <span data-ttu-id="d71d0-361">디자인 화면의 지도가 변경되어 선택 항목의 효과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-361">The map on the design surface changes to show the effect of your selections.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="d71d0-362">범례에서 **제목** 을 클릭 하 여 범례 제목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-362">Click **Title** on the legend to select the legend title.</span></span>  
  
7.  <span data-ttu-id="d71d0-363">**제목** 을 다시 클릭 하 여 텍스트에 대 한 삽입 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-363">Click **Title** again to enter insert mode for the text.</span></span> <span data-ttu-id="d71d0-364">**제목을** **Sales (천 단위)** 로 바꾸고 텍스트 바깥쪽을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-364">Replace **Title** by **Sales (Thousands)**, and then click outside the text.</span></span>  
  
 <span data-ttu-id="d71d0-365">범례가 확장되어 제목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-365">The legend expands to display the title.</span></span>  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a><span data-ttu-id="d71d0-366">6e.</span><span class="sxs-lookup"><span data-stu-id="d71d0-366">6e.</span></span> <span data-ttu-id="d71d0-367">범례와 색 규칙 연결</span><span class="sxs-lookup"><span data-stu-id="d71d0-367">Associate Legend and Color Rules</span></span>  
 <span data-ttu-id="d71d0-368">각 범례에는 하나 이상의 규칙 결과 집합이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-368">Each legend can display one or more sets of rule results.</span></span>  
  
##### <a name="to-associate-a-legend-with-color-rules"></a><span data-ttu-id="d71d0-369">범례를 색 규칙과 연결하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-369">To associate a legend with color rules</span></span>  
  
1.  <span data-ttu-id="d71d0-370">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-370">Double-click the map to display the **Map Layer** pane.</span></span>  
  
2.  <span data-ttu-id="d71d0-371">PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 **다각형 색 규칙**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-371">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="d71d0-372">**지도 색 규칙 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-372">The **Map Color Rules Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d71d0-373">**범례**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-373">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="d71d0-374">**색 눈금 옵션**에서 **색 눈금에 표시**를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-374">In **Color scale options**, clear **Show in color scale**.</span></span>  
  
5.  <span data-ttu-id="d71d0-375">**범례 옵션**의 드롭다운 목록에서 Legend2를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-375">In **Legend options**, from the drop-down list, select Legend2.</span></span> <span data-ttu-id="d71d0-376">범례 텍스트 옵션이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-376">The legend text option appears.</span></span> <span data-ttu-id="d71d0-377">기본적으로 범례 텍스트는 일반 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식 문자열을 사용하여 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-377">By default, legend text is formatted with a general [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] format string.</span></span> <span data-ttu-id="d71d0-378">N0의 0은 소수 자릿수가 표시되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-378">The 0 in N0 specifies no decimal digits.</span></span>  
  
6.  <span data-ttu-id="d71d0-379">**범례 텍스트**에서 다음 형식을 사용 하 여 숫자 없이 통화를 지정 합니다.`#FROMVALUE {C0} - #TOVALUE {C0}`</span><span class="sxs-lookup"><span data-stu-id="d71d0-379">In **Legend text**, use the following format to specify currency with no decimal digits: `#FROMVALUE {C0} - #TOVALUE {C0}`</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="d71d0-380">디자인 화면의 범례에 통화로 형식이 지정된 예제 데이터를 사용하여 색 범위가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-380">On the design surface, the legend displays the color ranges with sample data formatted as currency.</span></span>  
  
8.  <span data-ttu-id="d71d0-381">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-381">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-382">연결된 상점과 판매량이 있는 군은 색 규칙에 따라 표시되고</span><span class="sxs-lookup"><span data-stu-id="d71d0-382">The counties that have associated stores and sales display according to the color rules.</span></span> <span data-ttu-id="d71d0-383">판매량이 없는 군은 무색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-383">Counties that have no sales have no color.</span></span>  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a><span data-ttu-id="d71d0-384">6f.</span><span class="sxs-lookup"><span data-stu-id="d71d0-384">6f.</span></span> <span data-ttu-id="d71d0-385">데이터가 없는 군의 색 변경</span><span class="sxs-lookup"><span data-stu-id="d71d0-385">Change Color for Counties with No Data</span></span>  
 <span data-ttu-id="d71d0-386">계층에 있는 모든 지도 요소의 기본 표시 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-386">You can set the default display options for all map elements on a layer.</span></span> <span data-ttu-id="d71d0-387">색 규칙은 이러한 표시 옵션보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-387">Color rules take precedence over these display options.</span></span>  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a><span data-ttu-id="d71d0-388">계층의 모든 요소에 대한 표시 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-388">To set the display properties for all elements on a layer</span></span>  
  
1.  <span data-ttu-id="d71d0-389">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-389">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-390">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-390">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="d71d0-391">PolygonLayer1에서 아래쪽 화살표를 클릭한 다음 **다각형 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-391">Click the down arrow on PolygonLayer1, and then click **Polygon Properties**.</span></span> <span data-ttu-id="d71d0-392">**지도 다각형 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-392">The **Map Polygon Properties** dialog box opens.</span></span> <span data-ttu-id="d71d0-393">규칙 기반 표시 옵션이 적용되기 전에 이 대화 상자의 표시 옵션 집합이 계층에 있는 모든 다각형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-393">Display options set in this dialog box apply to all polygons on the layer before rule-based display options are applied.</span></span>  
  
4.  <span data-ttu-id="d71d0-394">**채우기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-394">Click **Fill**.</span></span>  
  
5.  <span data-ttu-id="d71d0-395">채우기 스타일이 단색 인지 확인 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="d71d0-395">Verify that the fill style is **Solid.**</span></span> <span data-ttu-id="d71d0-396">인지 확인합니다. 그라데이션과 패턴이 모든 색에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-396">Gradients and patterns apply to all colors.</span></span>  
  
6.  <span data-ttu-id="d71d0-397">**색**에서 아래쪽 화살표를 클릭 한 다음 **연한 강철 파랑**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-397">In **Color**, click the down arrow, and then click **Light Steel Blue**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="d71d0-398">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-398">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-399">연결된 데이터가 없는 군은 파란색으로 표시되고</span><span class="sxs-lookup"><span data-stu-id="d71d0-399">Counties that have no associated data display as blue.</span></span> <span data-ttu-id="d71d0-400">분석 데이터가 연결 된 군만 지정한 색 규칙에서 **빨강** ~ **녹색** 색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-400">Only counties that have associated analytical data appear in the **Red** through **Green** colors from the color rules that you specified.</span></span>  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a><span data-ttu-id="d71d0-401">7. 사용자 지정 점 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-401">7. Add a Custom Point</span></span>  
 <span data-ttu-id="d71d0-402">아직 빌드되지 않은 새 저장소를 나타내려면 점을 지정 하 고 **압정** 표식 유형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-402">To represent a new store that has not yet been built, specify a point and use the **PushPin** marker type.</span></span>  
  
#### <a name="to-add-a-custom-point"></a><span data-ttu-id="d71d0-403">사용자 지정 점을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-403">To add a custom point</span></span>  
  
1.  <span data-ttu-id="d71d0-404">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-404">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-405">지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-405">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="d71d0-406">도구 모음에서 **계층 추가**를 클릭 한 다음 **점 계층**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-406">On the toolbar, click **Add Layer**, and then click **Point Layer**.</span></span>  
  
     <span data-ttu-id="d71d0-407">새 점 계층이 지도에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-407">A new point layer is added to the map.</span></span> <span data-ttu-id="d71d0-408">기본적으로 점 계층의 공간 데이터 형식은 **포함**입니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-408">By default, the point layer has spatial data type **Embedded**.</span></span>  
  
3.  <span data-ttu-id="d71d0-409">PointLayer2에서 아래쪽 화살표를 클릭 한 다음 **점 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-409">Click the down arrow on PointLayer2, and then click **Add Point**.</span></span>  
  
4.  <span data-ttu-id="d71d0-410">지도 뷰포트로 포인터를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-410">Move the pointer over the map viewport.</span></span> <span data-ttu-id="d71d0-411">커서는 십자 기호로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-411">The cursor changes to crosshairs.</span></span>  
  
5.  <span data-ttu-id="d71d0-412">점을 추가할 지도의 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-412">Click the location on the map where you want to add a point.</span></span> <span data-ttu-id="d71d0-413">이 자습서에서는 경로의 시작 부분 옆에 있는 군의 한 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-413">In this tutorial, click a location in a county next to the start of the route.</span></span> <span data-ttu-id="d71d0-414">원으로 표시된 점이 계층의 클릭한 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-414">A point marked by a circle is added to the layer at the location where you clicked.</span></span> <span data-ttu-id="d71d0-415">기본적으로 점이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-415">By default, the point is selected.</span></span>  
  
6.  <span data-ttu-id="d71d0-416">추가한 점을 마우스 오른쪽 단추로 클릭하고 **포함 점 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-416">Right-click the point you added, and then click **Embedded Point Properties**.</span></span>  
  
7.  <span data-ttu-id="d71d0-417">**이 계층의 점 옵션 무시**옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-417">Select the option **Override point options for this layer**.</span></span> <span data-ttu-id="d71d0-418">추가 페이지가 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-418">Additional pages appear in the dialog box.</span></span> <span data-ttu-id="d71d0-419">여기서 설정한 값은 계층 또는 색 규칙에 대한 표시 옵션보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-419">Values that you set here take precedence over display options for the layer or for color rules.</span></span>  
  
8.  <span data-ttu-id="d71d0-420">**표식**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-420">Click **Marker**.</span></span>  
  
9. <span data-ttu-id="d71d0-421">**표식 유형**에서 **Star**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-421">For **Marker type**, select **Star**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="d71d0-422">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-422">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-423">추가한 새 점이 **별 모양**으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-423">The new point you added appears as a **Star**.</span></span>  
  
#### <a name="to-add-a-label-for-the-custom-point"></a><span data-ttu-id="d71d0-424">사용자 지정 점에 대한 레이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-424">To add a label for the custom point</span></span>  
  
1.  <span data-ttu-id="d71d0-425">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-425">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-426">방금 추가한 점을 마우스 오른쪽 단추로 클릭 하 고 **포함 점 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-426">Right-click the point you just added, and then click **Embedded Point Properties**.</span></span>  
  
3.  <span data-ttu-id="d71d0-427">**레이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-427">Click **Labels**.</span></span>  
  
4.  <span data-ttu-id="d71d0-428">**레이블 텍스트**에 **New Store**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-428">In **Label text**, type **New Store**.</span></span>  
  
5.  <span data-ttu-id="d71d0-429">**배치**에서 **위쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-429">In **Placement**, click **Top**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="d71d0-430">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-430">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-431">레이블이 상점 위치 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-431">The label appears above the store location.</span></span>  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a><span data-ttu-id="d71d0-432">지도 보기 가운데 맞춤</span><span class="sxs-lookup"><span data-stu-id="d71d0-432">Center the Map View</span></span>  
 <span data-ttu-id="d71d0-433">지도 뷰포트 중심 및 확대/축소 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-433">Change the map viewport center and zoom level.</span></span>  
  
#### <a name="to-change-the-viewport"></a><span data-ttu-id="d71d0-434">뷰포트를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-434">To change the viewport</span></span>  
  
1.  <span data-ttu-id="d71d0-435">지도 뷰포트를 마우스 오른쪽 단추로 클릭 한 다음 **뷰포트 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-435">Right-click the map viewport, and then click **Viewport Properties**.</span></span>  
  
2.  <span data-ttu-id="d71d0-436">**가운데 및 확대/축소를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-436">Click **Center and Zoom**.</span></span>  
  
3.  <span data-ttu-id="d71d0-437">**보기 중심 및 확대/축소 수준 설정** 옵션이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-437">Verify that the option **Set a view center and zoom level** is selected.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="d71d0-438">지도 뷰포트를 마우스 왼쪽 단추로 클릭하고 뷰포트의 중심을 원하는 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-438">Left-click the map viewport, and drag the center of the viewport to the location that you want.</span></span>  
  
6.  <span data-ttu-id="d71d0-439">마우스 휠을 사용하여 뷰포트의 확대/축소 수준을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-439">Use the mouse wheel to change the zoom level of the viewport.</span></span>  
  
7.  <span data-ttu-id="d71d0-440">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-440">Preview the report.</span></span>  
  
 <span data-ttu-id="d71d0-441">디자인 뷰의 화면과 보기에 지도가 예제 데이터를 기반으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-441">In Design view, the map on the display surface and the view is based on sample data.</span></span> <span data-ttu-id="d71d0-442">렌더링된 보고서에서는 지도 보기가 지정한 보기의 가운데에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-442">In the rendered report, the map view is centered on the view that you specified.</span></span>  
  
##  <a name="add-a-report-title"></a><a name="Title"></a><span data-ttu-id="d71d0-443">보고서 제목 추가</span><span class="sxs-lookup"><span data-stu-id="d71d0-443">Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="d71d0-444">보고서 제목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-444">To add a report title</span></span>  
  
1.  <span data-ttu-id="d71d0-445">디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-445">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="d71d0-446">**Sales in New York Stores** 를 입력한 다음 입력란 바깥쪽을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-446">Type **Sales in New York Stores** and then click outside the text box.</span></span>  
  
 <span data-ttu-id="d71d0-447">이 제목은 보고서 맨 위에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-447">This title will appear at the top of the report.</span></span> <span data-ttu-id="d71d0-448">페이지 머리글이 정의되지 않았을 때 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-448">Items at the top of the report body when there is no page header defined are the equivalent of a report header.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="d71d0-449">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="d71d0-449">Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="d71d0-450">보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="d71d0-450">To save the report</span></span>  
  
1.  <span data-ttu-id="d71d0-451">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-451">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d71d0-452">보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-452">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="d71d0-453">**이름**에 **Store Sales in New York**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-453">In **Name**, type **Store Sales in New York**.</span></span>  
  
 <span data-ttu-id="d71d0-454">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-454">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d71d0-455">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d71d0-455">Next Steps</span></span>  
 <span data-ttu-id="d71d0-456">보고서에 지도를 추가하는 방법에 대한 연습을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="d71d0-456">This concludes the walkthrough for how to add a map to your report.</span></span>  
  
 <span data-ttu-id="d71d0-457">자세한 내용은 [지도 &#40;보고서 작성기 및 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) 및 블로그 항목 지도 제작상 blogs.msdn.com의 [SQL Server Reporting Services에 대 한 공간 데이터 조정](https://go.microsoft.com/fwlink/?LinkId=152771) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d71d0-457">For more information, see [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) and the blog entry [Cartographic Adjustment of Spatial Data for SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) on blogs.msdn.com.</span></span>  
  
 <span data-ttu-id="d71d0-458">추가 자습서는 [자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d71d0-458">For more tutorials, see [Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71d0-459">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d71d0-459">See Also</span></span>  
 <span data-ttu-id="d71d0-460">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="d71d0-460">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="d71d0-461">[2014 SQL Server의 보고서 작성기](report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="d71d0-461">[Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="d71d0-462">[지도 마법사 및 지도 계층 마법사 &#40;보고서 작성기 및 SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d71d0-462">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d71d0-463">규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d71d0-463">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
