---
title: 데이터 영역에서 그룹 추가 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4de53c3c-c6fc-49ce-b692-3609fc0b3ec5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c355ca87db578d47181935e1ca6bc48e75bf8b8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735047"
---
# <a name="add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="2c0b4-102">데이터 영역에서 그룹 추가 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c0b4-102">Add or Delete a Group in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2c0b4-103">표시 및 계산을 위해 데이터를 특정 값 또는 식 집합에 따라 구성하려는 경우 데이터 영역에 그룹을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-103">Add a group to a data region when you want to organize data by a specific value or set of expressions, for display and calculations.</span></span> <span data-ttu-id="2c0b4-104">그룹에는 그룹에 속한 데이터 세트의 데이터를 구분하는 식과 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-104">A group has a name and an expression that identifies which data from a dataset belongs to the group.</span></span> <span data-ttu-id="2c0b4-105">그룹에 대한 자세한 내용은 [그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="2c0b4-106">테이블릭스 데이터 영역에서 테이블, 행렬 또는 목록을 클릭하여 그룹화 창을 표시하고,</span><span class="sxs-lookup"><span data-stu-id="2c0b4-106">In a tablix data region, click in the table, matrix, or list to display the Grouping pane.</span></span> <span data-ttu-id="2c0b4-107">데이터 세트 필드를 행 그룹 및 열 그룹 창으로 끌어 부모 또는 자식 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-107">Drag dataset fields to the Row Group and Column Group pane to create parent or child groups.</span></span> <span data-ttu-id="2c0b4-108">기존 그룹을 마우스 오른쪽 단추로 클릭하여 인접 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-108">Right-click an existing group to add an adjacent group.</span></span> <span data-ttu-id="2c0b4-109">정의에 따르면 세부 정보 그룹은 가장 안쪽 그룹이며 하위 그룹으로만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-109">By definition, the details group is the innermost group and can only be added as a child group.</span></span> <span data-ttu-id="2c0b4-110">기존 그룹을 삭제하려면 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-110">Right-click an existing group to delete it.</span></span> <span data-ttu-id="2c0b4-111">그룹 값을 표시할 행과 열은 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-111">Rows and columns on which to display group values are automatically added for you.</span></span> <span data-ttu-id="2c0b4-112">자세한 내용은 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-112">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="2c0b4-113">차트 데이터 영역에서 차트를 클릭하여 끌어 놓기 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-113">In a Chart data region, click in the chart to display the drop-zones.</span></span> <span data-ttu-id="2c0b4-114">데이터 세트 필드를 범주 및 계열 끌어 놓기 영역으로 끌어서 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-114">Create groups by dragging dataset fields to the category and series drop zones.</span></span> <span data-ttu-id="2c0b4-115">중첩된 그룹을 추가하려면 끌어 놓기 영역에 여러 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-115">To add nested groups, add multiple fields to the drop-zone.</span></span>  
  
 <span data-ttu-id="2c0b4-116">기본적으로 계기에서는 그룹이 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-116">Groups are not defined in a gauge by default.</span></span> <span data-ttu-id="2c0b4-117">계기의 기본 동작은 지정한 필드의 모든 값을 계기에 표시되는 하나의 값으로 집계하는 것이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-117">The default behavior for the gauge is to aggregate all values in the specified field into one value that is displayed on the gauge.</span></span> <span data-ttu-id="2c0b4-118">자세한 내용은 [계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-118">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="2c0b4-119">테이블릭스 데이터 영역에 부모 또는 자식 행이나 열 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-119">To add a parent or child row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-120">필드를 **보고서 데이터** 창에서 **행 그룹** 창 또는 **열 그룹** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-120">Drag a field from the **Report Data** pane to the **Row Groups** pane or the **Column Groups** pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2c0b4-121">그룹화 창이 표시되지 않는 경우 보기 탭에서 **그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-121">If you do not see the Grouping pane, on the View tab, click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="2c0b4-122">안내 막대를 사용하여 필드를 그룹 계층 구조 위 또는 아래로 끌어 놓아서 그룹을 기존 그룹에 부모 그룹이나 자식 그룹으로 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-122">Drop the field above or below the group hierarchy using the guide bar to place the group as a parent group or a child group to an existing group.</span></span>  
  
     <span data-ttu-id="2c0b4-123">기본 이름, 그룹 식 및 필드 이름을 기반으로 하는 정렬 식이 적용된 그룹이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-123">The group is added with a default name, group expression, and sort expression that is based on the field name.</span></span>  
  
### <a name="to-add-an-adjacent-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="2c0b4-124">테이블릭스 데이터 영역에 인접 행 또는 열 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-124">To add an adjacent row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-125">그룹화 창에서 추가할 그룹의 피어 그룹을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-125">In the Grouping pane, right-click a group that is a peer to the group that you want to add.</span></span> <span data-ttu-id="2c0b4-126">**그룹 추가**를 클릭하고 **앞에 인접** 또는 **뒤에 인접** 을 클릭하여 그룹을 추가할 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-126">Click **Add Group**, and then click **Adjacent Before** or **Adjacent After** to specify where to add the group.</span></span> <span data-ttu-id="2c0b4-127">**테이블릭스 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-127">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="2c0b4-128">**이름**에 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-128">In **Name**, type a name for the group.</span></span>  
  
3.  <span data-ttu-id="2c0b4-129">**그룹 식**에서 식을 입력하거나 식 단추(**fx**)를 클릭하여 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-129">In **Group expression**, type an expression or click the expression button (**fx**) to create an expression.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2c0b4-130">새 그룹이 그룹화 창에 추가되고 그룹 값이 표시되는 행 또는 열이 디자인 화면의 테이블릭스 데이터 영역에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-130">A new group is added to the Grouping pane and a row or column on which to display group values is added to the tablix data region on the design surface.</span></span>  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="2c0b4-131">테이블릭스 데이터 영역에 세부 정보 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-131">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-132">그룹화 창에서 가장 안쪽 자식 그룹( **세부 정보** 그룹 아님)을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-132">In the Grouping pane, right-click a group that is the innermost child group, but not the **Details** group.</span></span> <span data-ttu-id="2c0b4-133">**그룹 추가**를 클릭한 다음 **자식 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-133">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="2c0b4-134">**테이블릭스 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-134">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="2c0b4-135">**그룹 식**에서 식을 공백으로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-135">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="2c0b4-136">세부 정보 그룹에는 식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-136">A details group has no expression.</span></span>  
  
3.  <span data-ttu-id="2c0b4-137">**세부 데이터 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-137">Select **Show detail data**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2c0b4-138">새로운 세부 정보 그룹이 그룹화 창에 자식 그룹으로 추가되고 1단계에서 선택한 그룹의 행 핸들에 세부 정보 그룹 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-138">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="2c0b4-139">핸들에 대한 자세한 내용은 [테이블릭스 데이터 영역 셀, 행 및 열&#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-139">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-edit-a-row-or-column-group-in-a-tablix-data-region"></a><span data-ttu-id="2c0b4-140">테이블릭스 데이터 영역에서 행 또는 열 그룹을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-140">To edit a row or column group in a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-141">보고서 디자인 화면에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-141">On the report design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="2c0b4-142">그룹화 창에 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-142">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="2c0b4-143">그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-143">Right-click the group, and then click **Group Properties**.</span></span>  
  
3.  <span data-ttu-id="2c0b4-144">**이름**에 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-144">In **Name**, type the name of the group.</span></span>  
  
4.  <span data-ttu-id="2c0b4-145">**그룹 식**에서 단순 식을 입력 또는 선택하거나 식 단추(**fx**)를 클릭하여 그룹 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-145">In **Group expressions**, type or select a simple expression, or click the Expression (**fx**) button to create a group expression.</span></span>  
  
5.  <span data-ttu-id="2c0b4-146">식을 더 만들려면 **추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-146">Click **Add** to create additional expressions.</span></span> <span data-ttu-id="2c0b4-147">지정하는 모든 식은 논리 AND로 연결되어 이 그룹의 데이터가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-147">All expressions you specify are combined using a logical AND to specify data for this group.</span></span>  
  
6.  <span data-ttu-id="2c0b4-148">(옵션) **페이지 나누기** 를 클릭하여 페이지 나누기 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-148">(Optional) Click **Page Breaks** to set page break options.</span></span>  
  
7.  <span data-ttu-id="2c0b4-149">(옵션) **정렬** 을 클릭하여 그룹의 값에 대한 정렬 순서를 지정하는 식을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-149">(Optional) Click **Sorting** to select or type expressions that specify the sort order for values in the group.</span></span>  
  
8.  <span data-ttu-id="2c0b4-150">(옵션) **표시 유형** 을 클릭하여 항목의 표시 유형 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-150">(Optional) Click **Visibility** to select the visibility options for the item.</span></span>  
  
9. <span data-ttu-id="2c0b4-151">(옵션) **필터** 를 클릭하여 이 그룹에 대한 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-151">(Optional) Click **Filters** to set filters for this group.</span></span>  
  
10. <span data-ttu-id="2c0b4-152">(옵션) **변수** 를 클릭하여 이 그룹을 범위로 하며 모든 자식 그룹에서 액세스할 수 있는 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-152">(Optional) Click **Variables** to define variables scoped to this group and accessible from any child groups.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-tablix-data-region"></a><span data-ttu-id="2c0b4-153">테이블릭스 데이터 영역에서 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-153">To delete a group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-154">그룹화 창에서 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-154">In the Grouping pane, right-click the group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="2c0b4-155">**그룹 삭제** 대화 상자에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-155">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="2c0b4-156">**그룹 및 관련 행과 열 삭제** 그룹 데이터를 표시하는 그룹 정의와 모든 관련 행을 삭제하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-156">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="2c0b4-157">세부 정보 그룹의 경우 같은 행이 세부 데이터와 그룹 데이터 모두에 포함되는 경우에는 세부 데이터 행만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-157">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="2c0b4-158">**그룹만 삭제** 테이블릭스 데이터 영역의 구조는 그대로 유지하고 그룹 정의만 삭제하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-158">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-details-group-from-a-tablix-data-region"></a><span data-ttu-id="2c0b4-159">테이블릭스 데이터 영역에서 세부 정보 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2c0b4-159">To delete a details group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="2c0b4-160">그룹화 창에서 세부 정보 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-160">In the Grouping pane, right-click the details group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="2c0b4-161">**그룹 삭제** 대화 상자에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-161">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="2c0b4-162">**그룹 및 관련 행과 열 삭제** 그룹 데이터를 표시하는 그룹 정의와 모든 관련 행을 삭제하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-162">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="2c0b4-163">세부 정보 그룹의 경우 같은 행이 세부 데이터와 그룹 데이터 모두에 포함되는 경우에는 세부 데이터 행만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-163">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="2c0b4-164">**그룹만 삭제** 테이블릭스 데이터 영역의 구조는 그대로 유지하고 그룹 정의만 삭제하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-164">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2c0b4-165">세부 정보 그룹이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-165">The details group is deleted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2c0b4-166">정보 행을 제거한 후 각 셀의 식에 적절한 집계 식이 지정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-166">Verify that after you remove a details row, the expression in each cell specifies an aggregate expression where appropriate.</span></span> <span data-ttu-id="2c0b4-167">필요한 경우 식을 편집하여 집계 함수를 원하는 대로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b4-167">If necessary, edit the expression to specify aggregate functions as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0b4-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c0b4-168">See Also</span></span>  
 <span data-ttu-id="2c0b4-169">[보고서 및 그룹 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-169">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 <span data-ttu-id="2c0b4-170">[그룹 식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-170">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c0b4-171">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-171">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c0b4-172">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-172">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c0b4-173">[테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-173">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c0b4-174">[행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-174">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c0b4-175">[목록&#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c0b4-175">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2c0b4-176">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2c0b4-176">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
