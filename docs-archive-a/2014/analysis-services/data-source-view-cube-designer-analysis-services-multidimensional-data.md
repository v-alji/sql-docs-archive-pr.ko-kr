---
title: 데이터 원본 뷰 (큐브 구조 탭, 큐브 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.datasourcepane.f1
ms.assetid: 1e39c910-5c10-4624-be27-ca02a461b46b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c949eaa17ec9d8bf585a5d595f31779382c41ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733307"
---
# <a name="data-source-view-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="81ea6-102">데이터 원본 뷰(큐브 구조 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="81ea6-102">Data Source View (Cube Structure Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="81ea6-103">**데이터 원본 뷰** 창을 사용하여 선택한 큐브와 연결된 데이터 원본 뷰의 테이블 및 열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-103">Use the **Data Source View** pane to view tables and columns from the data source view associated with the selected cube.</span></span> <span data-ttu-id="81ea6-104">이 창은 **데이터 원본 뷰** 창에서 **측정값** 창으로 열을 끌어 측정값 그룹 및 측정값을 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-104">This pane is used to create measure groups and measures by dragging columns from the **Data Source View** pane to the **Measures** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="81ea6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="81ea6-105">Options</span></span>  
 <span data-ttu-id="81ea6-106">**데이터 원본 뷰**</span><span class="sxs-lookup"><span data-stu-id="81ea6-106">**Data Source View**</span></span>  
 <span data-ttu-id="81ea6-107">선택한 큐브와 연결된 데이터 원본 뷰를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-107">Displays the data source view associated with the selected cube.</span></span>  
  
 <span data-ttu-id="81ea6-108">**(시점 이동)**</span><span class="sxs-lookup"><span data-stu-id="81ea6-108">**(Move viewpoint)**</span></span>  
 <span data-ttu-id="81ea6-109">창 오른쪽 아래 모퉁이에서 스크롤 막대 사이를 클릭하여 확인할 **데이터 원본 뷰** 창의 영역을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-109">Click the lower right corner of the pane, between the scrollbars, to select an area of the **Data Source View** pane to view.</span></span>  
  
## <a name="diagram-context-menu"></a><span data-ttu-id="81ea6-110">다이어그램 상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="81ea6-110">Diagram Context Menu</span></span>  
 <span data-ttu-id="81ea6-111">다음 옵션은 **데이터 원본 뷰** 창의 다이어그램 배경을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-111">The following options are available in the context menu displayed by right-clicking the diagram background of the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="81ea6-112">**테이블 표시**</span><span class="sxs-lookup"><span data-stu-id="81ea6-112">**Show Tables**</span></span>  
 <span data-ttu-id="81ea6-113">**테이블 표시** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-113">Displays the **Show Table** dialog box.</span></span> <span data-ttu-id="81ea6-114">**테이블 표시** 대화 상자에 대한 자세한 내용은 [테이블 표시 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-114">For more information about the **Show Table** dialog box, see [Show Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-115">**모든 테이블 표시**</span><span class="sxs-lookup"><span data-stu-id="81ea6-115">**Show All Tables**</span></span>  
 <span data-ttu-id="81ea6-116">해당 큐브와 연결된 데이터 원본 뷰의 모든 테이블을 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-116">Displays in the pane all tables included in the data source view associated with the cube.</span></span>  
  
 <span data-ttu-id="81ea6-117">**사용된 테이블만 표시**</span><span class="sxs-lookup"><span data-stu-id="81ea6-117">**Show Only Used Tables**</span></span>  
 <span data-ttu-id="81ea6-118">연결된 데이터 원본 뷰의 큐브에서 사용한 테이블만 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-118">Displays in the pane only those tables used by the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="81ea6-119">**이름 표시**</span><span class="sxs-lookup"><span data-stu-id="81ea6-119">**Show Friendly Names**</span></span>  
 <span data-ttu-id="81ea6-120">창에 있는 개체의 이름을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-120">Selects to show friendly names for the objects in the pane.</span></span>  
  
 <span data-ttu-id="81ea6-121">**모두 선택**</span><span class="sxs-lookup"><span data-stu-id="81ea6-121">**Select All**</span></span>  
 <span data-ttu-id="81ea6-122">창에 있는 모든 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-122">Selects all of the objects in the pane.</span></span>  
  
 <span data-ttu-id="81ea6-123">**테이블 찾기**</span><span class="sxs-lookup"><span data-stu-id="81ea6-123">**Find Table**</span></span>  
 <span data-ttu-id="81ea6-124">**테이블 찾기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-124">Displays the **Find Table** dialog box.</span></span> <span data-ttu-id="81ea6-125">**테이블 찾기** 대화 상자에 대한 자세한 내용은 [테이블 찾기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-125">For more information about the **Find Table** dialog box, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-126">**테이블 정렬**</span><span class="sxs-lookup"><span data-stu-id="81ea6-126">**Arrange Tables**</span></span>  
 <span data-ttu-id="81ea6-127">**대각선 레이아웃으로 전환** 또는 **사각형 레이아웃으로 전환**을 선택하여 지정한 레이아웃에 따라 창에 있는 개체를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-127">Arranges the objects in the pane according to the layout specified by selecting either **Switch to Diagonal Layout** or **Switch to Rectangular Layout**.</span></span>  
  
 <span data-ttu-id="81ea6-128">**대각선 레이아웃으로 전환**</span><span class="sxs-lookup"><span data-stu-id="81ea6-128">**Switch to Diagonal Layout**</span></span>  
 <span data-ttu-id="81ea6-129">대각선 패턴으로 개체를 정렬하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-129">Select to arrange objects in a diagonal pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ea6-130">이 옵션은 **사각형 레이아웃으로 전환** 을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-130">This option is displayed only if **Switch to Rectangular Layout** is selected.</span></span>  
  
 <span data-ttu-id="81ea6-131">**사각형 레이아웃으로 전환**</span><span class="sxs-lookup"><span data-stu-id="81ea6-131">**Switch to Rectangular Layout**</span></span>  
 <span data-ttu-id="81ea6-132">사각형 패턴으로 개체를 정렬하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-132">Select to arrange objects in a rectangular pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ea6-133">이 옵션은 **대각선 레이아웃으로 전환** 을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-133">This option is displayed only if **Switch to Diagonal Layout** is selected.</span></span>  
  
 <span data-ttu-id="81ea6-134">**데이터 원본 뷰 편집**</span><span class="sxs-lookup"><span data-stu-id="81ea6-134">**Edit Data Source View**</span></span>  
 <span data-ttu-id="81ea6-135">해당 개체와 연결된 데이터 원본 뷰에 대한 데이터 원본 뷰 디자이너를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-135">Displays Data Source View Designer for the data source view associated with the object.</span></span> <span data-ttu-id="81ea6-136">데이터 원본 뷰 디자이너에 대한 자세한 내용은 [데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-136">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-137">**데이터 원본 뷰 표시 위치**</span><span class="sxs-lookup"><span data-stu-id="81ea6-137">**Show Data Source View In**</span></span>  
 <span data-ttu-id="81ea6-138">다음 옵션 중 하나를 선택하여 **데이터 원본 뷰** 창의 뷰 모드를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-138">Select one of the following options to toggle between viewing the **Data Source View** pane in the following modes:</span></span>  
  
-   <span data-ttu-id="81ea6-139">다이어그램</span><span class="sxs-lookup"><span data-stu-id="81ea6-139">Diagram</span></span>  
  
     <span data-ttu-id="81ea6-140">현재 큐브와 연결된 테이블 및 열의 다이어그램을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-140">Displays a diagram of the tables and columns associated with the current cube.</span></span>  
  
-   <span data-ttu-id="81ea6-141">트리</span><span class="sxs-lookup"><span data-stu-id="81ea6-141">Tree</span></span>  
  
     <span data-ttu-id="81ea6-142">현재 큐브와 연결된 테이블 및 열이 포함된 트리 뷰를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-142">Displays a tree view containing the tables and columns associated with the current cube.</span></span>  
  
 <span data-ttu-id="81ea6-143">**복사할 다이어그램 위치**</span><span class="sxs-lookup"><span data-stu-id="81ea6-143">**Copy Diagram From**</span></span>  
 <span data-ttu-id="81ea6-144">해당 큐브와 연결된 데이터 원본 뷰의 다이어그램 중 하나를 선택하여 **데이터 원본 뷰** 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-144">Select one of the diagrams included in the data source view associated with the cube to display it in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="81ea6-145">**확대/축소**</span><span class="sxs-lookup"><span data-stu-id="81ea6-145">**Zoom**</span></span>  
 <span data-ttu-id="81ea6-146">사용 가능한 확대/축소 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-146">Select an available zoom option.</span></span>  
  
 <span data-ttu-id="81ea6-147">**속성**</span><span class="sxs-lookup"><span data-stu-id="81ea6-147">**Properties**</span></span>  
 <span data-ttu-id="81ea6-148">**에서 큐브와 연결된 데이터 원본 뷰에 대한** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-148">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the data source view associated with the cube.</span></span>  
  
## <a name="table-context-menu"></a><span data-ttu-id="81ea6-149">테이블 상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="81ea6-149">Table Context Menu</span></span>  
 <span data-ttu-id="81ea6-150">다음 옵션은 **데이터 원본 뷰** 창에서 테이블 또는 뷰 이름을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-150">The following options are available in the context menu displayed by right-clicking the name of a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="81ea6-151">**관련 테이블 표시**</span><span class="sxs-lookup"><span data-stu-id="81ea6-151">**Show Related Tables**</span></span>  
 <span data-ttu-id="81ea6-152">데이터 원본 뷰에서 선택한 테이블과 관련된 테이블을 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-152">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="81ea6-153">**테이블 숨기기**</span><span class="sxs-lookup"><span data-stu-id="81ea6-153">**Hide Table**</span></span>  
 <span data-ttu-id="81ea6-154">창에서 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-154">Removes the table from the pane.</span></span>  
  
 <span data-ttu-id="81ea6-155">**데이터 탐색**</span><span class="sxs-lookup"><span data-stu-id="81ea6-155">**Explore Data**</span></span>  
 <span data-ttu-id="81ea6-156">선택한 테이블에 대한 **데이터 탐색** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-156">Display the **Explore Data** dialog box for the selected table.</span></span>  
  
 <span data-ttu-id="81ea6-157">**데이터 원본 뷰 편집**</span><span class="sxs-lookup"><span data-stu-id="81ea6-157">**Edit Data Source View**</span></span>  
 <span data-ttu-id="81ea6-158">선택한 테이블을 포함하는 데이터 원본 뷰에 대한 데이터 원본 뷰 디자이너를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-158">Displays Data Source View Designer for the data source view that contains the selected table.</span></span> <span data-ttu-id="81ea6-159">데이터 원본 뷰 디자이너에 대한 자세한 내용은 [데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-159">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-160">**테이블의 새 측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="81ea6-160">**New Measure Group from Table**</span></span>  
 <span data-ttu-id="81ea6-161">선택한 테이블을 기반으로 **측정값** 창에서 새 측정값 그룹을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-161">Defines a new measure group in the **Measures** pane based on the selected table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ea6-162">이 옵션은 **측정값** 창의 측정값 그룹이 해당 테이블을 참조하지 않는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-162">This option is enabled only if the table is not yet referenced by a measure group in the **Measures** pane.</span></span>  
  
 <span data-ttu-id="81ea6-163">**속성**</span><span class="sxs-lookup"><span data-stu-id="81ea6-163">**Properties**</span></span>  
 <span data-ttu-id="81ea6-164">**에서 선택한 테이블에 대한** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-164">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected table.</span></span>  
  
## <a name="column-context-menu"></a><span data-ttu-id="81ea6-165">열 상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="81ea6-165">Column Context Menu</span></span>  
 <span data-ttu-id="81ea6-166">다음 옵션은 **데이터 원본 뷰** 창에서 테이블 또는 뷰의 열 이름을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-166">The following options are available in the context menu displayed by right-clicking the name of a column in a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="81ea6-167">**열의 새 측정값**</span><span class="sxs-lookup"><span data-stu-id="81ea6-167">**New Measure from Column**</span></span>  
 <span data-ttu-id="81ea6-168">선택한 열을 기반으로 **측정값** 창에서 새 측정값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-168">Defines a new measure in the **Measures** pane based on the selected column.</span></span>  
  
 <span data-ttu-id="81ea6-169">**데이터 탐색**</span><span class="sxs-lookup"><span data-stu-id="81ea6-169">**Explore Data**</span></span>  
 <span data-ttu-id="81ea6-170">선택한 열을 포함하는 테이블에 대한 **데이터 탐색** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-170">Display the **Explore Data** dialog box for the table that contains the selected column.</span></span>  
  
 <span data-ttu-id="81ea6-171">**데이터 원본 뷰 편집**</span><span class="sxs-lookup"><span data-stu-id="81ea6-171">**Edit Data Source View**</span></span>  
 <span data-ttu-id="81ea6-172">선택한 열을 포함하는 데이터 원본 뷰에 대한 데이터 원본 뷰 디자이너를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-172">Displays Data Source View Designer for the data source view that contains the selected column.</span></span> <span data-ttu-id="81ea6-173">데이터 원본 뷰 디자이너에 대한 자세한 내용은 [데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-173">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-174">**속성**</span><span class="sxs-lookup"><span data-stu-id="81ea6-174">**Properties**</span></span>  
 <span data-ttu-id="81ea6-175">**에서 선택한 열에 대한** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-175">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected column.</span></span>  
  
## <a name="relationship-context-menu"></a><span data-ttu-id="81ea6-176">관계 상황에 맞는 메뉴</span><span class="sxs-lookup"><span data-stu-id="81ea6-176">Relationship Context Menu</span></span>  
 <span data-ttu-id="81ea6-177">다음 옵션은 **데이터 원본 뷰** 창에서 관계를 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-177">The following options are available in the context menu displayed by right-clicking a relationship in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="81ea6-178">**데이터 원본 뷰 편집**</span><span class="sxs-lookup"><span data-stu-id="81ea6-178">**Edit Data Source View**</span></span>  
 <span data-ttu-id="81ea6-179">선택한 관계를 포함하는 데이터 원본 뷰에 대한 데이터 원본 뷰 디자이너를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-179">Displays Data Source View Designer for the data source view that contains the selected relationship.</span></span> <span data-ttu-id="81ea6-180">데이터 원본 뷰 디자이너에 대한 자세한 내용은 [데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81ea6-180">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81ea6-181">**속성**</span><span class="sxs-lookup"><span data-stu-id="81ea6-181">**Properties**</span></span>  
 <span data-ttu-id="81ea6-182">**에서 선택한 관계에 대한** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ea6-182">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ea6-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81ea6-183">See Also</span></span>  
 <span data-ttu-id="81ea6-184">[큐브 디자이너 &#40;큐브 구조 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="81ea6-184">[Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="81ea6-185">[측정값 &#40;큐브 구조 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="81ea6-185">[Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="81ea6-186">[차원 &#40;큐브 구조 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="81ea6-186">[Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="81ea6-187">큐브 구조 &#40;큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="81ea6-187">Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
