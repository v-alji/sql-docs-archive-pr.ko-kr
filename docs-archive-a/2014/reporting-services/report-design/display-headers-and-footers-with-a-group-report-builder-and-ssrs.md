---
title: 그룹과 함께 머리글 및 바닥글 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adbb3674a16fc77d04ac3ac490a284894588c657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650734"
---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a><span data-ttu-id="014d0-102">그룹과 함께 머리글 및 바닥글 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="014d0-102">Display Headers and Footers with a Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="014d0-103">그룹 머리글 또는 바닥글 같은 정적 행을 테이블릭스 데이터 영역의 그룹과 연결된 동적 행과 함께 렌더링할지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-103">You can help control whether a static row, such as a group header or footer, renders with dynamic rows that are associated with a group in a tablix data region.</span></span>  
  
 <span data-ttu-id="014d0-104">모든 열 머리글 또는 행 머리글을 여러 페이지에서 반복하려면 테이블릭스 데이터 영역에 대해 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-104">To repeat all the column headings or row headings on multiple pages, you can set properties for the tablix data region.</span></span> <span data-ttu-id="014d0-105">자세한 내용은 [여러 페이지에 행 및 열 머리글 표시&#40;보고서 작성기 및 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="014d0-105">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="014d0-106">중첩된 그룹에 연결된 동적 행 및 열 또는 레이블이나 부분합과 연결된 정적 행 및 열의 렌더링 동작을 제어하려면 테이블릭스 멤버에 대해 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-106">To control the rendering behavior for dynamic rows and columns that are associated with nested groups, or for static rows and columns that are associated with labels or subtotals, you must set properties for the tablix member.</span></span> <span data-ttu-id="014d0-107">테이블릭스 멤버는 정적이거나 동적인 행 또는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-107">A tablix member represents a static or dynamic row or column.</span></span> <span data-ttu-id="014d0-108">정적 멤버는 한 번씩 반복되는 멤버로,</span><span class="sxs-lookup"><span data-stu-id="014d0-108">A static member repeats once.</span></span> <span data-ttu-id="014d0-109">총합계 행을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-109">For example, a grand total row is a static row.</span></span> <span data-ttu-id="014d0-110">동적 멤버는 그룹 인스턴스당 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-110">A dynamic member repeats once for each group instance.</span></span> <span data-ttu-id="014d0-111">예를 들어 그룹 식 [Territory]가 있는 그룹과 연결된 행은 해당 지역의 각 고유 값에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-111">For example, a row that is associated with a group that has the group expression [Territory] repeats once for each unique value for territory.</span></span> <span data-ttu-id="014d0-112">테이블릭스 멤버에 대한 자세한 내용은 [테이블릭스 데이터 영역 셀, 행 및 열&#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="014d0-112">For more information about tablix members, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="014d0-113">그룹화 창에서 테이블릭스 멤버를 선택하고 속성 창에서 **KeepWithGroup**, **KeepTogether**및 **RepeatOnNewPage** 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-113">You can select a tablix member in the Grouping pane and set the properties **KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** in the Properties pane.</span></span> <span data-ttu-id="014d0-114">그룹 머리글 및 바닥글이 그룹과 같은 페이지에 표시되도록 하려면 **KeepWithGroup** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-114">Use **KeepWithGroup** to help display group headers and footers on the same page as the group.</span></span> <span data-ttu-id="014d0-115">정적 멤버가 그룹의 행이나 열과 함께 표시되도록 하려면 **KeepTogether** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-115">Use **KeepTogether** to help display static members with the rows or columns of a group.</span></span> <span data-ttu-id="014d0-116">**KeepWithGroup** 값으로 지정된 행 그룹 멤버의 전체 인스턴스를 적어도 하나 이상 표시하는 모든 페이지에서 그룹 머리글 또는 바닥글을 반복하려면 **RepeatOnNewPage** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-116">Use **RepeatOnNewPage** to repeat the group header or footer on every page that displays at least one complete instance of the row group member designated by the **KeepWithGroup** value.</span></span> <span data-ttu-id="014d0-117">열 그룹 멤버에 대해서는**RepeatOnNewPage** 가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-117">**RepeatOnNewPage** is not supported for column group members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="014d0-118">**KeepWithGroup**, **KeepTogether** 및 **RepeatOnNewPage**는 그룹화 창의 **고급 모드**를 사용하여 설정할 수 있는 그룹 멤버 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-118">**KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** are group member properties that you can set by using the **Advanced Mode** of the Grouping pane.</span></span> <span data-ttu-id="014d0-119">자세한 내용은 [그룹화 창&#40;보고서 작성기#41;](grouping-pane-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="014d0-119">For more information, see [Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a><span data-ttu-id="014d0-120">정적 행을 행 그룹과 연결된 동적 행 집합과 함께 표시하려면</span><span class="sxs-lookup"><span data-stu-id="014d0-120">To keep a static row with a set of dynamic rows associated with a row group</span></span>  
  
1.  <span data-ttu-id="014d0-121">디자인 화면에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-121">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="014d0-122">그룹화 창에 데이터 영역에 대한 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-122">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="014d0-123">그룹화 창의 오른쪽에서 아래쪽 화살표를 클릭한 다음 **고급 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-123">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="014d0-124">행 그룹 창에 행 그룹 계층 구조의 계층적 정적 및 동적 멤버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-124">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="014d0-125">그룹 행과 함께 유지할 행 머리글 또는 바닥글에 해당하는 정적 멤버를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-125">Click the static member that corresponds to the row header or footer that you want to keep with the group rows.</span></span> <span data-ttu-id="014d0-126">속성 창에 **테이블릭스 멤버** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-126">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="014d0-127">속성 창에서 **KeepWithGroup**을 클릭하고 드롭다운 목록에서 다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-127">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="014d0-128">**없음** 이 멤버를 선택된 행 그룹의 멤버와 함께 유지하도록 설정하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-128">**None** Select this option to indicate no preference for keeping this member with the members of the selected row group.</span></span>  
  
    -   <span data-ttu-id="014d0-129">**이전** 이 멤버를 이전 그룹의 멤버와 함께 유지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-129">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="014d0-130">이 옵션은 그룹 바닥글 행에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-130">You might use this for group footer rows.</span></span>  
  
    -   <span data-ttu-id="014d0-131">**이후** 이 멤버를 다음 그룹의 멤버와 함께 유지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-131">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="014d0-132">이 옵션은 그룹 머리글 행에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-132">You might use this for group header rows.</span></span>  
  
5.  <span data-ttu-id="014d0-133">(옵션) 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-133">(Optional) Preview the report.</span></span> <span data-ttu-id="014d0-134">가능한 경우, 보고서는 이 멤버를 지정된 행 그룹 멤버와 함께 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-134">Where possible, the report renderer keeps this member with the specified row group members.</span></span>  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a><span data-ttu-id="014d0-135">정적 열을 열 그룹과 연결된 동적 열 집합과 함께 표시하려면</span><span class="sxs-lookup"><span data-stu-id="014d0-135">To keep a static column with a set of dynamic columns associated with a column group</span></span>  
  
1.  <span data-ttu-id="014d0-136">디자인 화면에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-136">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="014d0-137">그룹화 창에 데이터 영역에 대한 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-137">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="014d0-138">그룹화 창의 오른쪽에서 아래쪽 화살표를 클릭한 다음 **고급 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-138">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="014d0-139">열 그룹 창에 열 그룹 계층 구조의 계층적 정적 및 동적 멤버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-139">The Column Groups pane displays the hierarchical static and dynamic members for the column group hierarchy.</span></span>  
  
3.  <span data-ttu-id="014d0-140">그룹 열과 함께 유지할 정적 열에 해당하는 정적 멤버를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-140">Click the static member that corresponds to the static column that you want to keep with the group columns.</span></span> <span data-ttu-id="014d0-141">속성 창에 **테이블릭스 멤버** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-141">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="014d0-142">속성 창에서 **KeepWithGroup**을 클릭하고 드롭다운 목록에서 다음 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-142">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="014d0-143">**없음** 이 멤버를 선택된 열 그룹의 멤버와 함께 유지하도록 기본 설정하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-143">**None** Select this option to indicate no preference for keeping this member with the members of the selected column group.</span></span>  
  
    -   <span data-ttu-id="014d0-144">**이전** 이 멤버를 이전 그룹의 멤버와 함께 유지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-144">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="014d0-145">이 옵션은 지정한 열 그룹 멤버 이전에 표시되는 열 레이블에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-145">You might use this for column labels that display before the specified column group members.</span></span>  
  
    -   <span data-ttu-id="014d0-146">**이후** 이 멤버를 다음 그룹의 멤버와 함께 유지하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-146">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="014d0-147">이 옵션은 지정한 열 그룹 멤버 이후에 표시되는 열 합계에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-147">You might use this for column totals that display after the specified column group members.</span></span>  
  
5.  <span data-ttu-id="014d0-148">(옵션) 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-148">(Optional) Preview the report.</span></span> <span data-ttu-id="014d0-149">가능한 경우, 보고서는 이 멤버를 지정된 열 그룹 멤버와 함께 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="014d0-149">Where possible, the report renderer keeps this member with the specified column group members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014d0-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="014d0-150">See Also</span></span>  
 <span data-ttu-id="014d0-151">[테이블 릭 스 데이터 영역 셀, 행 및 열 &#40;보고서 작성기&#41; 및 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-151">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="014d0-152">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-152">[Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="014d0-153">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-153">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="014d0-154">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-154">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="014d0-155">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-155">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="014d0-156">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="014d0-156">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="014d0-157">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="014d0-157">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
