---
title: 테이블 또는 행렬에 대화형 정렬 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10121"
- sql12.rtp.rptdesigner.textboxproperties.intrctvsort.f1
ms.assetid: 05819637-729b-4cf6-82de-91a99f184ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c0c453a8ea338ab9a09d7552c064f2eb85add985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739357"
---
# <a name="add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="76950-102">테이블 또는 행렬에 대화형 정렬 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="76950-102">Add Interactive Sort to a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="76950-103">대화형 정렬 단추를 추가하면 사용자가 테이블 및 행렬에서 행 및 열의 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-103">Add interactive sort buttons to enable users to change the sort order of rows and columns in tables and matrices.</span></span> <span data-ttu-id="76950-104">이 기능은 HTML처럼 사용자 상호 작용을 지원하는 랜더링 형식에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-104">This feature is supported only in rendering formats that support user interaction, such as HTML.</span></span>  
  
 <span data-ttu-id="76950-105">대화형 정렬 단추를 만들 때는 정렬 대상, 정렬 기준 및 정렬을 적용할 범위를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-105">When you create an interactive sort button, you must specify what to sort, what to sort by, and the scope to which to apply the sort.</span></span> <span data-ttu-id="76950-106">예를 들어 고객의 성을 기준으로 정보 행을 정렬하거나, 판매량을 기준으로 범주 그룹 내 하위 범주 그룹 값을 정렬하거나, 합계로 결합된 범주 및 하위 범주 그룹 값을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-106">For example, you can sort detail rows by customer last name, subcategory group values within a category group by sales, or category and subcategory group values combined by totals.</span></span>  
  
 <span data-ttu-id="76950-107">보고서를 볼 때 대화형 정렬을 지원하는 열에는 정렬 순서가 표시되도록 변경할 수 있는 화살표 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-107">When you view the report, columns that support interactive sorting have arrow icons that change to indicate the sort order.</span></span> <span data-ttu-id="76950-108">대화형 정렬 단추를 처음 클릭하면 항목이 오름차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-108">The first time you click an interactive sort button, items are sorted in ascending order.</span></span> <span data-ttu-id="76950-109">계속 클릭하면 오름차순 정렬 순서와 내림차순 정렬 순서 사이를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-109">Subsequent clicks toggle the sort order between ascending and descending order.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="in-this-article"></a><a name="BackToTop"></a> <span data-ttu-id="76950-110">문서 내용</span><span class="sxs-lookup"><span data-stu-id="76950-110">In this Article</span></span>  
 [<span data-ttu-id="76950-111">그룹이 없는 테이블의 정보 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-111">Sorting Detail Rows for a Table with No Groups</span></span>](#SortingDetailRows)  
  
 [<span data-ttu-id="76950-112">테이블 또는 행렬의 최상위 부모 행 그룹 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-112">Sorting a Top Level Parent Row Group for a Table or Matrix</span></span>](#SortingTopLevelParent)  
  
 [<span data-ttu-id="76950-113">그룹의 자식 그룹 또는 정보 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-113">Sorting Child Groups or Detail Rows for a Group</span></span>](#SortingChildGroups)  
  
 [<span data-ttu-id="76950-114">복잡한 그룹 식을 기준으로 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-114">Sorting Rows Based on a Complex Group Expression</span></span>](#SortingMultipleRowGroups)  
  
 [<span data-ttu-id="76950-115">여러 데이터 영역에 대한 정렬 순서 동기화</span><span class="sxs-lookup"><span data-stu-id="76950-115">Synchronizing Sort Order for Multiple Data Regions</span></span>](#SynchronizingSortOrder)  
  
##  <a name="sorting-detail-rows-for-a-table-with-no-groups"></a><a name="SortingDetailRows"></a> <span data-ttu-id="76950-116">그룹이 없는 테이블의 정보 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-116">Sorting Detail Rows for a Table with No Groups</span></span>  
 <span data-ttu-id="76950-117">대화형 정렬 단추를 열 머리글에 추가하면 사용자가 열 머리글을 클릭하고 테이블의 해당 열에 표시된 값을 기준으로 정보 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-117">Add an interactive sort button to a column header to enable a user to click the column header and sort the details rows in a table by the value displayed in that column.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-the-table-by-value"></a><span data-ttu-id="76950-118">대화형 정렬 단추를 열 머리글에 추가하여 값을 기준으로 테이블을 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="76950-118">To add an interactive sort button to a column header to sort the table by value</span></span>  
  
1.  <span data-ttu-id="76950-119">보고서 디자인 뷰의 그룹이 없는 테이블에서 대화형 정렬 단추를 추가할 열 머리글의 입력란을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-119">In report design view, in a table with no groups, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="76950-120">**대화형 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-120">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="76950-121">**이 입력란에서 대화형 정렬 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-121">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="76950-122">**정렬할 항목 선택**에서 **정보 행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-122">In **Choose what to sort**, click **Detail rows**.</span></span>  
  
5.  <span data-ttu-id="76950-123">**정렬 기준**에서 정렬 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-123">In **Sort by**, specify a sort expression.</span></span> <span data-ttu-id="76950-124">드롭다운 목록에서 정렬 동작을 정의할 열에 해당하는 필드를 선택합니다. 예를 들어 "Title"이라는 열 제목의 경우 `[Title]`을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-124">From the drop-down list, select the field that corresponds to the column for which you are defining a sort action (for example, for a column heading named "Title", choose `[Title]`).</span></span> <span data-ttu-id="76950-125">정렬 식은 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-125">Specifying a sort expression is required.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="76950-126">대화형 정렬 단추를 추가할 각 열에 대해 1-6단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-126">Repeat steps 1-6 for every column to which you want to add an interactive sort button.</span></span>  
  
 <span data-ttu-id="76950-127">정렬 동작을 확인하려면 **실행** 을 클릭하여 보고서를 미리 본 후 대화형 정렬 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-127">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="76950-128">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [맨 위로 이동](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="76950-128">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-a-top-level-parent-row-group-for-a-table-or-matrix"></a><a name="SortingTopLevelParent"></a> <span data-ttu-id="76950-129">테이블 또는 행렬의 최상위 부모 행 그룹 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-129">Sorting a Top-Level Parent Row Group for a Table or Matrix</span></span>  
 <span data-ttu-id="76950-130">대화형 정렬 단추를 열 머리글에 추가하면 사용자가 열 머리글을 클릭하고 테이블 또는 행렬의 해당 열에 표시된 값을 기준으로 부모 그룹 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-130">Add an interactive sort button to a column header to enable a user to click the column header and sort the parent group rows in a table or matrix by the value displayed in that column.</span></span> <span data-ttu-id="76950-131">자식 그룹의 순서는 변경되지 않고 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-131">The order of child groups remains unchanged.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-groups"></a><span data-ttu-id="76950-132">대화형 정렬 단추를 열 머리글에 추가하여 그룹을 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="76950-132">To add an interactive sort button to a column header to sort groups</span></span>  
  
1.  <span data-ttu-id="76950-133">보고서 디자인 뷰의 테이블 또는 행렬에서 대화형 정렬 단추를 추가할 그룹의 열 머리글에 있는 입력란을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-133">In a table or matrix in report design view, right-click the text box in the column header for the group to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="76950-134">**대화형 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-134">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="76950-135">**이 입력란에서 대화형 정렬 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-135">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="76950-136">**정렬할 항목 선택**에서 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-136">In **Choose what to sort**, click **Groups**.</span></span>  
  
5.  <span data-ttu-id="76950-137">드롭다운 목록에서 정렬할 그룹의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-137">From the drop-down list, select the name of the group that you are sorting.</span></span> <span data-ttu-id="76950-138">단순 그룹 식을 기준으로 하는 그룹의 경우 **정렬 기준** 값이 그룹 식으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="76950-138">For groups based on simple group expressions, the **Sort by** value is populated with group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76950-139">복잡한 그룹 식의 경우 **정렬 기준** 식을 그룹 식과 같은 값으로 직접 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-139">For complex group expressions, manually set the **Sort by** expression to the same value as the group expression.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="76950-140">정렬 동작을 확인하려면 **실행** 을 클릭하여 보고서를 미리 본 후 대화형 정렬 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-140">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="76950-141">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [맨 위로 이동](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="76950-141">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-child-groups-or-detail-rows-for-a-group"></a><a name="SortingChildGroups"></a> <span data-ttu-id="76950-142">그룹의 자식 그룹 또는 정보 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-142">Sorting Child Groups or Detail Rows for a Group</span></span>  
 <span data-ttu-id="76950-143">대화형 정렬 단추를 그룹 머리글 행에 추가하면 사용자가 부모 그룹의 자식 그룹 값을 정렬하거나 가장 안쪽에 있는 자식 그룹의 정보 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-143">Add an interactive sort button to a group header row to enable the user to sort the values of a child group from a parent group or to sort the detail rows for the innermost child group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-text-box-in-a-group-row-header-to-sort-child-groups-or-detail-rows"></a><span data-ttu-id="76950-144">대화형 정렬 단추를 그룹 행 머리글의 입력란에 추가하여 자식 그룹 또는 정보 행을 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="76950-144">To add an interactive sort button to a text box in a group row header to sort child groups or detail rows</span></span>  
  
1.  <span data-ttu-id="76950-145">보고서 디자인 뷰에서 대화형 정렬 단추를 추가할 그룹 헤더 행의 입력란을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-145">In report design view, right-click the text box in the group header row to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="76950-146">**대화형 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-146">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="76950-147">**이 입력란에서 대화형 정렬 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-147">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="76950-148">**정렬할 항목 선택**에서 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-148">In **Choose what to sort**, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="76950-149">**세부 정보** 정보 행을 정렬하려면 **세부 정보** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-149">**Details** Click **Details** to sort the detail rows.</span></span> <span data-ttu-id="76950-150">드롭다운 목록에서 정렬 기준 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-150">From the drop-down list, select the field to sort by.</span></span> <span data-ttu-id="76950-151">이 옵션에서는 정렬 기준 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-151">For this option, you must specify the value to sort by.</span></span>  
  
    -   <span data-ttu-id="76950-152">**그룹** 자식 그룹 값을 정렬하려면 **그룹** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-152">**Groups** Click **Groups** to sort the child group values.</span></span> <span data-ttu-id="76950-153">이 옵션에서는 **정렬 기준** 식이 그룹 식으로 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="76950-153">For this option, the **Sort by** expression is automatically filled in from the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="76950-154">정렬 동작을 확인하려면 **실행** 을 클릭하여 보고서를 미리 본 후 대화형 정렬 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-154">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="76950-155">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [맨 위로 이동](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="76950-155">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-rows-based-on-a-complex-group-expression"></a><a name="SortingMultipleRowGroups"></a> <span data-ttu-id="76950-156">복잡한 그룹 식을 기준으로 행 정렬</span><span class="sxs-lookup"><span data-stu-id="76950-156">Sorting Rows Based on a Complex Group Expression</span></span>  
 <span data-ttu-id="76950-157">대화형 정렬 단추를 열 머리글에 추가하면 사용자가 열 머리글을 클릭하고 결합된 부모 및 자식 그룹을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-157">Add an interactive sort button to a column header to enable a user to click the column header and sort the combined parent and child groups.</span></span> <span data-ttu-id="76950-158">이러한 결과를 얻으려면 그룹 식을 두 그룹의 복합 형태로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-158">To achieve this affect, you must change the group expression to be a composite of both groups.</span></span> <span data-ttu-id="76950-159">예를 들어 상점에 대한 행렬에 색 및 크기로 그룹화된 품목의 총 재고량이 표시된다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-159">For example, suppose a matrix displays inventory totals for a store for items grouped by both color and size.</span></span> <span data-ttu-id="76950-160">색 및 크기 각각에 대해 별도의 그룹을 만들지 않고 색 및 크기의 조합을 기준으로 행을 정렬하려면 색 및 크기의 조합을 기준으로 그룹을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-160">To sort the rows based on the combination of color and size, instead of having a separate group for color and a separate group for size, you can define a group based on the combination of color and size.</span></span> <span data-ttu-id="76950-161">그룹 식을 정의하는 방법에 대한 자세한 내용은 [그룹 식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76950-161">For more information about defining group expressions, see [Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="76950-162">다음 절차에서는 테이블릭스 데이터 영역을 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-162">In the following procedure, terms specify tablix data region areas.</span></span> <span data-ttu-id="76950-163">자세한 내용은 [테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76950-163">For more information, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="76950-164">일반적으로 여러 그룹을 기반으로 하는 행을 정렬할 때는 열 그룹에 관계없이 정렬된 행에 대한 합계를 보고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-164">Typically, when you sort rows based on multiple groups, you want to see totals for the sorted rows, regardless of column groups.</span></span> <span data-ttu-id="76950-165">이 절차에서는 열 그룹이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-165">In this procedure, no column groups are used.</span></span> <span data-ttu-id="76950-166">먼저 행렬을 추가하고 기본 열 그룹을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-166">You start by adding a matrix and removing the default column group.</span></span> <span data-ttu-id="76950-167">또는 테이블을 추가하고 세부 정보 그룹을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-167">Alternatively, you could start by adding a table and removing the details group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-multiple-groups"></a><span data-ttu-id="76950-168">대화형 정렬 단추를 열 머리글에 추가하여 여러 그룹을 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="76950-168">To add an interactive sort button to a column header to sort multiple groups</span></span>  
  
1.  <span data-ttu-id="76950-169">보고서 디자인 뷰에서 행렬을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-169">In report design view, add a matrix.</span></span>  
  
2.  <span data-ttu-id="76950-170">숫자 필드를 데이터 셀로 끌어 데이터 세트를 행렬에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-170">Drag a numeric field to the data cell to link the dataset to the matrix.</span></span>  
  
     <span data-ttu-id="76950-171">그런 다음 여러 필드를 지정하는 그룹 식을 이용해 그룹을 만들고 그룹 값을 표시할 그룹 머리글을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76950-171">Next, you will create a group with a group expression that specifies multiple fields, and a group header to use to display the group values.</span></span>  
  
3.  <span data-ttu-id="76950-172">보고서 디자인 화면에서 행렬이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-172">Verify that the matrix is selected on the design surface.</span></span> <span data-ttu-id="76950-173">그룹화 창에 기본 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-173">The Grouping pane displays a default row and column group.</span></span>  
  
4.  <span data-ttu-id="76950-174">행 그룹 창에서 기본 행 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-174">In the Row Groups pane, right-click the default row group, and then click **Edit Group**.</span></span> <span data-ttu-id="76950-175">**그룹 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="76950-175">The **Group Properties** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="76950-176">**이름**에서 그룹화할 여러 그룹을 지정하는 이름으로 기본 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="76950-176">In **Name**, replace the default name with a name that specifies the multiple groups that you want to group by.</span></span>  
  
6.  <span data-ttu-id="76950-177">**그룹 식**의 **그룹화 대상**에서 식 단추(**fx**)를 클릭하여 **식** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76950-177">In **Group expressions**, in **Group on**, click the Expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
7.  <span data-ttu-id="76950-178">그룹화할 모든 필드를 지정하는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-178">Type the expression that specifies all fields that you want to group by.</span></span> <span data-ttu-id="76950-179">예를 들어 다음 그룹 식 `=Fields!Color.Value & Fields!Size.Value`은(는) Color와 Size라는 이름을 가진 필드를 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-179">For example, the following group expression combines a field named Color and a field named Size: `=Fields!Color.Value & Fields!Size.Value`.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="76950-180">이제 그룹이 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-180">You have now defined the group.</span></span> <span data-ttu-id="76950-181">다음에는 표시할 필드를 행렬의 테이블릭스 본문 영역으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-181">Next, drag the fields to display to the tablix body area of the matrix.</span></span> <span data-ttu-id="76950-182">7단계에서 그룹화할 대상으로 선택한 필드를 각각 고유한 열을 가진 테이블릭스 본문 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-182">Add the fields that you chose to group by in step 7 to the tablix body area, each in its own column.</span></span>  
  
     <span data-ttu-id="76950-183">이 시나리오에서 테이블릭스 행 그룹 영역의 첫 번째 열은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-183">For this scenario, the first column in the tablix row groups area is not needed.</span></span> <span data-ttu-id="76950-184">해당 열을 삭제하려면 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-184">To delete the column, right-click the column header, and then click **Delete Columns**.</span></span> <span data-ttu-id="76950-185">관련 그룹을 삭제할지 여부를 묻는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-185">A dialog box asks whether to delete the associated groups.</span></span> <span data-ttu-id="76950-186">**아니요**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-186">Click **No**.</span></span> <span data-ttu-id="76950-187">행 그룹 영역이 삭제되고 테이블릭스 본문 영역만 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-187">The row group area is deleted and only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="76950-188">다음으로 기본 열 그룹을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-188">Next, you will remove the default column group.</span></span>  
  
9. <span data-ttu-id="76950-189">열 그룹 창에서 기본 열 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-189">In the Column Groups pane, right-click the default column group, and then click **Delete Group**.</span></span> <span data-ttu-id="76950-190">해당 그룹과 관련 행 및 열 또는 그룹만 삭제할지 여부를 묻는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-190">A dialog box asks whether to delete the group and related rows and columns or the group only.</span></span> <span data-ttu-id="76950-191">**그룹만 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-191">Click **Delete group only**.</span></span> <span data-ttu-id="76950-192">열 그룹이 삭제된 다음 열 그룹 영역이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-192">The column group is deleted, and the column group area is deleted.</span></span> <span data-ttu-id="76950-193">테이블릭스 본문 영역만 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-193">Only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="76950-194">그런 다음, 행렬에 걸쳐 있는 입력란에 대화형 정렬 단추를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-194">Next, you will add an interactive sort button to the text box that spans the matrix.</span></span>  
  
10. <span data-ttu-id="76950-195">첫 번째 행의 입력란을 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-195">Click in the text box in the first row and then click **Text Box Properties**.</span></span>  
  
11. <span data-ttu-id="76950-196">**대화형 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-196">Click **Interactive Sorting**.</span></span>  
  
12. <span data-ttu-id="76950-197">**이 입력란에서 대화형 정렬 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-197">Select **Enable interactive sorting on this text box**.</span></span>  
  
13. <span data-ttu-id="76950-198">**정렬할 항목 선택**에서 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-198">In **Choose what to sort**, click **Groups**.</span></span>  
  
14. <span data-ttu-id="76950-199">드롭다운 목록에서 5단계에서 만든 그룹의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-199">From the drop-down list, select the name of the group you created in step 5.</span></span> <span data-ttu-id="76950-200">그룹 식이 **정렬 기준** 입력란에 자동으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-200">The group expression is automatically copied to the **Sort by** text box.</span></span>  
  
15. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="76950-201">입력란에 정렬 단추를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-201">You have added the sort button to the text box.</span></span>  
  
16. <span data-ttu-id="76950-202">(옵션) 그룹 값이 표시되는 열에서 중복 값을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-202">(Optional) You can suppress duplicate values in the columns that display group values.</span></span> <span data-ttu-id="76950-203">보고서 디자인 화면에서 숨기려는 반복 값이 표시되는 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-203">On the report design surface, click the text box that displays the value for which you want to hide repeating values.</span></span> <span data-ttu-id="76950-204">속성 창에서 **HideDuplicates**로 스크롤하고 드롭다운 목록에서 이 행렬에 연결된 데이터 세트의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-204">In the Properties pane, scroll to **HideDuplicates**, and from the drop-down list, select the name of the dataset that is linked to this matrix.</span></span>  
  
 <span data-ttu-id="76950-205">정렬 동작을 확인하려면 **실행** 을 클릭하여 보고서를 미리 본 후 대화형 정렬 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-205">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="76950-206">각 값이 고유의 열로 표시되기는 하지만 그룹 식의 결합된 값을 기준으로 행렬이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-206">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="76950-207">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [맨 위로 이동](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="76950-207">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="synchronizing-sort-order-for-multiple-data-regions"></a><a name="SynchronizingSortOrder"></a> <span data-ttu-id="76950-208">여러 데이터 영역에 대한 정렬 순서 동기화</span><span class="sxs-lookup"><span data-stu-id="76950-208">Synchronizing Sort Order for Multiple Data Regions</span></span>  
 <span data-ttu-id="76950-209">대화형 정렬 단추를 추가하면 사용자가 한 개의 정렬 단추를 클릭하여 여러 데이터 영역을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-209">Add an interactive sort button that enables a user to click one sort button and sort multiple data regions.</span></span> <span data-ttu-id="76950-210">대화형 정렬 단추를 만들 때 동일한 보고서 데이터 세트를 기반으로 여러 데이터 영역에 대한 정렬을 동기화할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-210">When you create an interactive sort button, you can specify whether to synchronize the sort for multiple data regions based on the same report dataset.</span></span> <span data-ttu-id="76950-211">예를 들어 보고서에는 행렬과 그래픽으로 데이터를 표시하는 차트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-211">For example, a report might include a matrix and a chart that graphically displays the data.</span></span> <span data-ttu-id="76950-212">사용자가 행렬에서 행의 정렬 순서를 변경하면 차트도 자동으로 동일한 정렬 순서로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-212">When a user changes the sort order of the rows in the matrix, the chart automatically displays the same sort order.</span></span>  
  
 <span data-ttu-id="76950-213">정렬 순서를 동기화하려면 정렬할 데이터 영역 또는 그룹에 대해 같은 정렬 식을 사용해야 하며 두 데이터 영역에 대해 상위 항목이 되는 정렬 범위를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-213">To synchronize the sort order, you must use identical sort expressions for the data regions or groups to sort, and define the scope for the sort to be a mutual ancestor of both data regions.</span></span> <span data-ttu-id="76950-214">상위 항목은 두 데이터 영역이 연결된 데이터 세트 또는 두 데이터 영역이 들어 있는 포함 데이터 영역일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-214">The mutual ancestor can be either the dataset to which both data regions are linked or a containing data region within which both data regions appear.</span></span> <span data-ttu-id="76950-215">예를 들어 보고서에 같은 데이터 세트의 데이터를 표시하는 동시에 목록에 포함되어 있는 행렬과 차트가 모두 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-215">For example, assume a report has both a matrix and a chart that display data from the same dataset and that are contained in a list.</span></span> <span data-ttu-id="76950-216">정렬 동작을 동기화하려면 행렬의 열에 대화형 정렬을 지정하고 목록에 대한 범위를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-216">To synchronize the sort action, you must specify the interactive sort on a column in the matrix and set the scope to the list.</span></span> <span data-ttu-id="76950-217">사용자가 행렬을 정렬하면 차트도 함께 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-217">When the user sorts the matrix, the chart is also sorted.</span></span>  
  
#### <a name="to-synchronize-sort-order-with-a-chart-for-an-interactive-sort-button-on-a-matrix-data-region"></a><span data-ttu-id="76950-218">행렬 데이터 영역의 대화형 정렬 단추에 대한 차트와 정렬 순서를 동기화하려면</span><span class="sxs-lookup"><span data-stu-id="76950-218">To synchronize sort order with a chart for an interactive sort button on a matrix data region</span></span>  
  
1.  <span data-ttu-id="76950-219">보고서 디자인 뷰에서 보고서에 행렬을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-219">In report design view, add a matrix to the report.</span></span>  
  
2.  <span data-ttu-id="76950-220">행렬 데이터 셀에 수량이나 판매량 등을 나타내는 숫자 데이터 세트 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-220">Add a numeric dataset field to the matrix data cell, for example, a field representing quantity or sales.</span></span>  
  
3.  <span data-ttu-id="76950-221">행 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-221">Define a row group.</span></span> <span data-ttu-id="76950-222">기본적으로 그룹의 정렬 순서는 그룹 식과 같은 식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-222">By default, the sort order for the group is set to the same expression as the group expression.</span></span>  
  
4.  <span data-ttu-id="76950-223">보고서에 원형 차트와 같은 차트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-223">Add a chart to the report, for example, a pie chart.</span></span>  
  
5.  <span data-ttu-id="76950-224">2단계에서 선택한 필드를 끌어 **차트 데이터** 창의 **값** 영역에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-224">Drag the field you chose in step 2 to the **Value** area of the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="76950-225">그룹화하기 위해 선택한 필드를 끌어 **범주 그룹** 영역에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="76950-225">Drag the field you chose to group by to the **Category Groups** area.</span></span>  
  
     <span data-ttu-id="76950-226">행렬의 그룹 식 행 그룹과 차트 범주 그룹은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-226">The group expression for the matrix row group and the chart category group must be identical.</span></span>  
  
7.  <span data-ttu-id="76950-227">범주 그룹을 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-227">Right-click the category group, and then click **Category Group Properties**.</span></span>  
  
8.  <span data-ttu-id="76950-228">**정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-228">Click **Sorting**.</span></span>  
  
9. <span data-ttu-id="76950-229">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-229">Click **Add**.</span></span> <span data-ttu-id="76950-230">표의 정렬 옵션에 새 정렬 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-230">A new sort row is added to the sorting options grid.</span></span>  
  
10. <span data-ttu-id="76950-231">정렬 기준의 드롭다운 목록에서 6단계에서 그룹화할 대상으로 선택했던 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-231">In Sort by, from the drop-down list, choose the same field that you chose in step 6 to group by.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
12. <span data-ttu-id="76950-232">행렬에서 대화형 정렬 단추를 추가할 열 머리글의 입력란을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-232">In the matrix, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
13. <span data-ttu-id="76950-233">**대화형 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-233">Click **Interactive Sorting**.</span></span>  
  
14. <span data-ttu-id="76950-234">**이 입력란에서 대화형 정렬 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-234">Select **Enable interactive sorting on this text box**.</span></span>  
  
15. <span data-ttu-id="76950-235">**정렬할 항목 선택**에서 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-235">In **Choose what to sort**, click **Groups**.</span></span>  
  
16. <span data-ttu-id="76950-236">**그룹**의 드롭다운 목록에서 정렬할 그룹의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-236">From the drop-down list under **Groups**, select the name of the group that you are sorting.</span></span> <span data-ttu-id="76950-237">이 그룹에 대한 그룹 식이 **정렬 기준** 값에 따라 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-237">The group expression for this group is automatically set for the **Sort by** value.</span></span>  
  
17. <span data-ttu-id="76950-238">**다음 범위 내에서 이 정렬을 다른 그룹 및 데이터 영역에도 적용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-238">Select **Also apply this sort to other groups and data regions within**.</span></span> <span data-ttu-id="76950-239">입력란에서 "SalesData"와 같은 데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-239">In the text box, type the name of the dataset, for example, "SalesData".</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="76950-240">정렬 동작을 확인하려면 **실행** 을 클릭하여 보고서를 미리 본 후 대화형 정렬 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76950-240">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="76950-241">각 값이 고유의 열로 표시되기는 하지만 그룹 식의 결합된 값을 기준으로 행렬이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="76950-241">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="76950-242">![맨 위로 이동 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [맨 위로 이동](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="76950-242">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76950-243">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76950-243">See Also</span></span>  
 <span data-ttu-id="76950-244">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76950-244">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="76950-245">[대화형 정렬&#40;보고서 작성기 및 SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76950-245">[Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="76950-246">[데이터 영역의 데이터 정렬&#40;보고서 작성기 및 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76950-246">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="76950-247">테이블릭스 데이터 영역의 유연성 살펴보기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="76950-247">Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)  
  
  
