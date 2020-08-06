---
title: 데이터 원본 뷰 디자이너에서 다이어그램 작업 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40a58ed33ff6cfaebf2a6e7c084500dd3ae072da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651343"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a><span data-ttu-id="39b33-102">데이터 원본 뷰 디자이너에서의 다이어그램 작업(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="39b33-102">Work with Diagrams in Data Source View Designer (Analysis Services)</span></span>
  <span data-ttu-id="39b33-103">데이터 원본 뷰(DSV) 다이어그램은 DSV 개체를 시각적으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-103">A data source view (DSV) diagram is a visual representation of the objects in a DSV.</span></span> <span data-ttu-id="39b33-104">다이어그램에서 대화형 작업을 통해 특정 개체를 추가, 숨기기, 삭제 또는 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-104">You can work with the diagram interactively to add, hide, delete or modify specific objects.</span></span> <span data-ttu-id="39b33-105">한 DSV에서 개체의 특정 하위 집합에 초점을 맞춘 다이어그램을 여러 개 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-105">You can also create multiple diagrams on the same DSV to focus attention on a subset of the objects.</span></span>  
  
 <span data-ttu-id="39b33-106">다이어그램 창에 표시할 다이어그램 영역을 변경하려면 창의 오른쪽 아래 모퉁이에서 십자형 화살표를 클릭하여 다이어그램 창에 표시할 영역이 선택될 때까지 선택 상자를 축소판 다이어그램 위로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-106">To change the area of the diagram that appears in the diagram pane, click the four-headed arrow in the lower right corner of the pane, and then drag the selection box over the thumbnail diagram until you select the area that is to appear in the diagram pane.</span></span>  
  
 <span data-ttu-id="39b33-107">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-107">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="39b33-108">다이어그램 추가</span><span class="sxs-lookup"><span data-stu-id="39b33-108">Add a Diagram</span></span>](#bkmk_add)  
  
 [<span data-ttu-id="39b33-109">다이어그램 편집 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="39b33-109">Edit or Delete a Diagram</span></span>](#bkmk_edit)  
  
 [<span data-ttu-id="39b33-110">다이어그램에서 테이블 찾기</span><span class="sxs-lookup"><span data-stu-id="39b33-110">Find Tables in a Diagram</span></span>](#bkmk_findtables)  
  
 [<span data-ttu-id="39b33-111">다이어그램에서 개체 정렬</span><span class="sxs-lookup"><span data-stu-id="39b33-111">Arrange Objects in a Diagram</span></span>](#bkmk_arrangeobjects)  
  
 [<span data-ttu-id="39b33-112">개체 정렬 유지</span><span class="sxs-lookup"><span data-stu-id="39b33-112">Preserve object arrangement</span></span>](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a><span data-ttu-id="39b33-113">다이어그램 추가</span><span class="sxs-lookup"><span data-stu-id="39b33-113">Add a Diagram</span></span>  
 <span data-ttu-id="39b33-114">DSV를 만들면 자동으로 DSV 다이어그램이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-114">DSV diagrams are created automatically when you create the DSV.</span></span> <span data-ttu-id="39b33-115">기존의 DSV에서 다이어그램을 추가하거나 특정 개체를 숨겨 DSV의 표현을 보다 관리하기 쉽게 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-115">After the DSV exists, you can create additional diagrams, remove them, or hide specific objects to create a more manageable representation of the DSV.</span></span>  
  
 <span data-ttu-id="39b33-116">새 다이어그램을 만들려면 **다이어그램 구성 도우미** 창을 마우스 오른쪽 단추로 클릭하고 **새 다이어그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-116">To create a new diagram, right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**.</span></span>  
  
 <span data-ttu-id="39b33-117">Analysis Services 프로젝트에서 처음으로 데이터 원본 뷰 (DSV)를 정의할 때 데이터 원본 뷰에 추가 된 모든 테이블과 뷰가 다이어그램에 추가 됩니다 \<All Tables> .</span><span class="sxs-lookup"><span data-stu-id="39b33-117">When you initially define a data source view (DSV) in an Analysis Services project, all tables and views added to the data source view are added to the \<All Tables> diagram.</span></span> <span data-ttu-id="39b33-118">이 다이어그램은 데이터 원본 뷰 디자이너의 다이어그램 구성 도우미 창에 나타나고 이 다이어그램의 테이블 및 해당 열과 관계는 테이블 창에 나열되며 스키마 창에 그래픽으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-118">This diagram appears in the Diagram Organizer pane in Data Source View Designer, the tables in this diagram (and their columns and relationships) are listed in the Tables pane, and the tables in this diagram (and their columns and relationships) are displayed graphically in the schema pane.</span></span> <span data-ttu-id="39b33-119">그러나 다이어그램에 테이블, 뷰 및 명명 된 쿼리를 추가 하면 \<All Tables> 이 다이어그램의 개체 수가 너무 많아 관계를 시각화 하기가 어렵습니다. 특히 여러 개의 팩트 테이블이 다이어그램에 추가 되 고 차원 테이블이 여러 개의 팩트 테이블과 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-119">However, as you add tables, views and named queries to the \<All Tables> diagram, the sheer number of objects in this diagram makes it difficult to visualize relationships-particularly as multiple fact tables are added to the diagram, and dimension tables relate to multiple fact tables.</span></span>  
  
 <span data-ttu-id="39b33-120">데이터 원본 뷰에서 테이블의 하위 집합만 보려는 경우 시각적으로 복잡하지 않도록 데이터 원본 뷰에서 선택한 하위 집합의 테이블, 뷰 및 명명된 쿼리로 구성된 하위 다이어그램(간단하게 다이어그램이라고 함)을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-120">To reduce the visual clutter when you only want to view a subset of the tables in the data source view, you can define sub-diagrams (simply called diagrams) consisting of selected subsets of the tables, views, and named queries in the data source view.</span></span> <span data-ttu-id="39b33-121">다이어그램을 사용하여 비즈니스 또는 솔루션 요구에 따라 데이터 원본 뷰의 항목을 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-121">You can use diagrams to group items in the data source view according to business or solution needs.</span></span>  
  
 <span data-ttu-id="39b33-122">비즈니스를 목적으로 그리고 많은 테이블, 뷰 및 명명된 쿼리가 포함된 데이터 원본 뷰를 보다 쉽게 이해할 수 있도록 관련 테이블 및 명명된 쿼리를 별도의 다이어그램에 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-122">You can group related tables and named queries in separate diagrams for business purposes, and to make it easier to understand a data source view that contains many tables, views, and named queries.</span></span> <span data-ttu-id="39b33-123">다이어그램을 제외 하 고 동일한 테이블 또는 명명 된 쿼리를 여러 다이어그램에 포함할 수 있습니다 \<All Tables> .</span><span class="sxs-lookup"><span data-stu-id="39b33-123">The same table or named query can be included in multiple diagrams except for the \<All Tables> diagram.</span></span> <span data-ttu-id="39b33-124">다이어그램에서 \<All Tables> 데이터 원본 뷰에 포함 된 모든 개체는 정확히 한 번 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-124">In the \<All Tables> diagram, all objects that are contained in the data source view are shown exactly once.</span></span>  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a><span data-ttu-id="39b33-125">다이어그램 편집 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="39b33-125">Edit or Delete a Diagram</span></span>  
 <span data-ttu-id="39b33-126">다이어그램으로 작업할 경우 개체를 추가 및 삭제하는 데 사용되는 명령에 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-126">When working with a diagram, pay close attention to the commands used for adding and removing objects.</span></span> <span data-ttu-id="39b33-127">예를 들어 다이어그램에서 개체를 삭제하면 DSV에서도 해당 개제가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-127">For example, deleting an object from a diagram will delete it from the DSV.</span></span> <span data-ttu-id="39b33-128">다이어그램에서만 삭제하려면 **테이블 숨기기** 명령을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-128">If you only want to delete it from the diagram, use **Hide Table** instead.</span></span>  
  
 <span data-ttu-id="39b33-129">![다이어그램 작업 영역, 마우스 오른쪽 단추 클릭 메뉴의 스크린 샷](../media/ssas-olapdsv-diagram.gif "다이어그램 작업 영역, 마우스 오른쪽 단추 클릭 메뉴의 스크린 샷")</span><span class="sxs-lookup"><span data-stu-id="39b33-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>  
  
 <span data-ttu-id="39b33-130">개체를 개별적으로 숨길 수 있지만, 숨겨진 개체를 관련 테이블 표시 명령을 사용하여 다시 표시하면 관련된 모든 개체가 다이어그램에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-130">Although you can hide objects individually, bringing them back using the Show Related Tables command returns all related objects to the diagram.</span></span> <span data-ttu-id="39b33-131">작업 영역에 원하는 개체만 반환되게 하려면 테이블 창에서 직접 끌어 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-131">To control which objects are returned to the workspace, drag them from the Tables pane instead.</span></span>  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a><span data-ttu-id="39b33-132">다이어그램에서 테이블 찾기</span><span class="sxs-lookup"><span data-stu-id="39b33-132">Find Tables in a Diagram</span></span>  
 <span data-ttu-id="39b33-133">스키마가 큰 경우 **다이어그램** 창에서 특정 테이블을 찾아 스크롤하기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-133">If your schema is large, scrolling to a particular table in the **Diagram** pane may be difficult.</span></span> <span data-ttu-id="39b33-134">그러나 다음 도구를 사용하면 다이어그램에서 테이블을 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-134">However, the following tools make it easy to find a table in a diagram.</span></span>  
  
-   <span data-ttu-id="39b33-135">**테이블** 창에서 테이블 목록을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-135">Scroll the list of tables in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="39b33-136">현재 표시된 다이어그램에 테이블을 포함하려면 **테이블** 창에서 다이어그램 창으로 테이블을 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-136">To include a table in the currently displayed diagram, drag the table from the **Tables** pane to the diagram pane.</span></span>  
  
     <span data-ttu-id="39b33-137">이미 다이어그램에 포함된 테이블을 가운데에 표시하려면 **테이블** 창에서 해당 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-137">To center the display on a table that is already included in the diagram, select the table in the **Tables** pane.</span></span>  
  
-   <span data-ttu-id="39b33-138">**다이어그램** 창의 테이블 로케이터-테이블 로케이터는 **다이어그램** 창의 오른쪽 아래 모퉁이에서 세로 및 가로 스크롤 막대가 교차 하는 위치에 있는 4 방향 화살표 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-138">Table locator in **Diagram** pane-The table locator is a 4-way arrow icon located at the intersection of the vertical and horizontal scroll bars in the lower right corner of the **Diagram** pane.</span></span> <span data-ttu-id="39b33-139">테이블 로케이터는 다이어그램 창에 축소판 그림으로 표현된 현재 다이어그램을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-139">It opens a thumbnail representation of the current diagram in the Diagram pane.</span></span> <span data-ttu-id="39b33-140">이 축소판 그림을 사용하여 다이어그램 창의 시점을 다이어그램의 임의의 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-140">You can use this thumbnail to change the view in the Diagram pane to any location on the diagram.</span></span>  
  
-   <span data-ttu-id="39b33-141">**테이블 찾기** 대화 상자를 사용 하 여 다이어그램 창의 열린 영역을 마우스 오른쪽 단추로 클릭 하 고 **테이블 찾기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-141">Use the **Find Table** dialog box- Right-click on open area in the Diagram pane and click **Find Table**.</span></span> <span data-ttu-id="39b33-142">또는 도구 모음 또는 **데이터 원본 뷰** 메뉴에서 **테이블 찾기** 명령을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-142">Or, click the **Find Table** command on the toolbar or the **Data Source View** menu.</span></span>  
  
     <span data-ttu-id="39b33-143">필터 입력란에 문자열 및 와일드카드 문자를 입력하여 다이어그램에 있는 테이블의 하위 집합을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-143">You can type strings and wildcard characters in the Filter box to view subsets of the tables in the diagram.</span></span>  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a><span data-ttu-id="39b33-144">다이어그램에서 개체 정렬</span><span class="sxs-lookup"><span data-stu-id="39b33-144">Arrange Objects in a Diagram</span></span>  
 <span data-ttu-id="39b33-145">데이터 원본 뷰 디자이너에서 여러 다이어그램을 정의하여 DSV를 이해하기 쉽게 만들 수 있지만 많은 테이블을 포함하는 다이어그램은 읽기 어려울 수 있으며 수동으로 테이블 레이아웃을 다시 정렬해야 할 경우 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-145">Although Data Source View Designer can define multiple diagrams to make a DSV more understandable, diagrams that contain dozens of tables can be hard to read and manually rearranging table layouts is a tedious process.</span></span> <span data-ttu-id="39b33-146">데이터 원본 뷰 디자이너에서는 현재 다이어그램에 있는 테이블간 관계를 기반으로 사각형 또는 대각선 레이아웃을 사용하여 현재 다이어그램에서 테이블을 자동으로 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-146">The Data Source View Designer can automatically rearrange tables in the current diagram using either a rectangular or diagonal layout based on the relationships between tables in the current diagram.</span></span>  
  
-   <span data-ttu-id="39b33-147">사각형 레이아웃에서 관계선은 열 사이 대신 테이블 사이에 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-147">In a rectangular layout, the relationship lines are drawn between tables instead of between columns.</span></span> <span data-ttu-id="39b33-148">테이블 사이에서는 관계선이 가로와 세로로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-148">Relationship lines are drawn horizontally and vertically between tables.</span></span>  
  
-   <span data-ttu-id="39b33-149">대각선 레이아웃에서 관계선은 테이블의 관련 열 사이에서 가능한 직선으로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-149">In a diagonal layout, relationship lines are drawn as directly as possible between related columns in tables.</span></span> <span data-ttu-id="39b33-150">여러 열에 대한 관계는 테이블의 첫 번째 관련 열에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-150">A relationship to multiple columns attaches to the first related column in the table.</span></span> <span data-ttu-id="39b33-151">테이블의 열이 표시되지 않는 경우 선은 테이블의 맨 위에 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-151">If the columns in a table are not visible, the lines are drawn to the top of the table.</span></span>  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a><span data-ttu-id="39b33-152">개체 정렬 유지</span><span class="sxs-lookup"><span data-stu-id="39b33-152">Preserve object arrangement</span></span>  
 <span data-ttu-id="39b33-153">원하는 방식으로 테이블을 수동 정렬한 후 다이어그램에 테이블을 추가하면 다이어그램 새로 고침이 발생하여 개체 레이아웃에 대한 최근 수정 내용이 모두 제거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-153">After manually arranging tables the way you want, adding more tables to the diagram can result in a diagram refresh that removes any recent modifications you made to the object layout.</span></span>  
  
 <span data-ttu-id="39b33-154">이 동작은 테이블을 추가하여 다이어그램 구성 도우미가 새 테이블을 수용하기 위해 다른 테이블을 이동할 때 발생할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-154">This behavior is more likely to occur when you add a table, causing the Diagram Organizer to move other tables in order to accommodate the new one.</span></span> <span data-ttu-id="39b33-155">그런 후 모든 테이블 및 연결 선이 올바르게 표시되도록 다이어그램을 다시 그립니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-155">It then redraws the diagram to ensure all tables and connection lines represented correctly.</span></span> <span data-ttu-id="39b33-156">이 시점에서 수동으로 조정한 특정 개체의 배치가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-156">At this point, any manual adjustments to the placement of specific objects might be lost.</span></span>  
  
 <span data-ttu-id="39b33-157">이 문제를 방지하려면 마지막으로 조정하기 전에 먼저 모든 테이블을 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="39b33-157">To avoid this problem, add all the tables first, before making any final adjustments.</span></span> <span data-ttu-id="39b33-158">나중에 다이어그램을 다시 열 경우 개체는 다이어그램에서 위치를 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b33-158">Objects should now retain their position in the diagram when you open it again later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b33-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39b33-159">See Also</span></span>  
 <span data-ttu-id="39b33-160">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="39b33-160">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="39b33-161">데이터 원본 뷰 디자이너&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="39b33-161">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
