---
title: 테이블에 열 추가 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5974a3cc-caf8-4558-8836-6e3c24b1ee23
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f329150e3b679e67ee65570efbca904a0570786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649222"
---
# <a name="add-columns-to-a-table-ssas-tabular"></a><span data-ttu-id="e4a51-102">테이블에 열 추가(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="e4a51-102">Add Columns to a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="e4a51-103">이 항목에서는 기존 테이블에 열을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-103">This topic describes how to add columns to an existing table.</span></span>  
  
## <a name="add-columns-from-the-data-source"></a><span data-ttu-id="e4a51-104">데이터 원본의 열 추가</span><span class="sxs-lookup"><span data-stu-id="e4a51-104">Add Columns from the Data Source</span></span>  
 <span data-ttu-id="e4a51-105">데이터 원본 테이블에서 데이터를 가져오기 위해 테이블 가져오기 마법사를 사용할 경우 원본 테이블의 모든 열을 포함하거나 미리 보기 및 필터 기능을 사용하여 특정 열을 필터링하여 제외하도록 선택한 경우 해당 열 및 선택한 필터링된 데이터를 포함하는 새 테이블이 모델에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-105">When using the Table Import Wizard to import data from a data source table, a new table is created in the model which includes all of the columns in the source table, or if you choose to filter out certain columns by using the Preview and Filter feature, only those columns and filtered data you select.</span></span> <span data-ttu-id="e4a51-106">가져올 특정 열만 지정하는 SQL 쿼리를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-106">You can also write a SQL Query that specifies only certain columns to import.</span></span> <span data-ttu-id="e4a51-107">그러나 나중에 추가로 원본 테이블의 다른 열을 모델 테이블에 가져오거나 DAX 수식에서 값을 유추하는 계산 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-107">You may, however, later determine a source table has additional columns that you want to add to the model table, or you need to add a calculated column with values derived from a DAX formula.</span></span>  
  
 <span data-ttu-id="e4a51-108">예를 들어 먼저 테이블 가져오기 마법사에서 미리 보기 및 필터 기능을 사용하여 데이터 원본의 일부 열만 선택하여 데이터를 가져온 다음, 나중에 원본 테이블에는 존재하지만 모델 테이블에 없는 다른 열을 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-108">If, for example, when you initially imported from a data source, you used the Preview and Filter feature in the Table Import Wizard to select a limited number of columns from the source table, you later determine that you need to add another column that exists at the source table, but does not yet exist in the model table.</span></span> <span data-ttu-id="e4a51-109">또는 데이터 원본의 FactSales 테이블에 새 AdjustedProfit 열을 추가한 다음 동일한 AdjustedProfit 열과 데이터를 모델의 Sales 테이블에 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-109">Or, for example, a new AdjustedProfit column was added to the FactSales table at the data source, and you now want to add the same AdjustedProfit column and data to the Sales table in the model.</span></span>  
  
 <span data-ttu-id="e4a51-110">이러한 경우 테이블 속성 편집 대화 상자를 사용하여 원본 테이블의 열을 선택한 후 모델 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-110">In these cases, you can use the Edit Table Properties dialog box to select columns from the source table and add them to the model table.</span></span> <span data-ttu-id="e4a51-111">테이블 속성 편집 대화 상자에는 테이블 미리 보기 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-111">The Edit Table Properties dialog box includes the table preview window.</span></span> <span data-ttu-id="e4a51-112">이 테이블 미리 보기 창에 원본의 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-112">The table preview window displays the table at the source.</span></span> <span data-ttu-id="e4a51-113">모델 테이블 정의에 이미 포함된 열은 확인란이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-113">Columns that are already included in the model table definition are already checked.</span></span> <span data-ttu-id="e4a51-114">모델 테이블 정의에 아직 포함되지 않은 열은 선택이 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-114">Those columns that are not already included in the model table definition are not checked.</span></span> <span data-ttu-id="e4a51-115">열을 선택한 후 확인을 클릭하여 원본의 열을 모델 테이블 정의에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-115">You can add columns from the source to the model table definition by selecting the column and clicking OK.</span></span> <span data-ttu-id="e4a51-116">테이블 속성 편집 대화 상자의 테이블 미리 보기 창은 테이블 가져오기 마법사의 미리 보기 및 필터 페이지에 있는 테이블 미리 보기 창과 동일한 보기와 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-116">The table preview window in the Edit Table Properties dialog box provides the same view and features as the table preview window in the Preview and Filter page of the Table Import Wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4a51-117">두 개 이상의 파티션이 포함된 테이블에 열을 추가하려면 먼저 파티션 관리자를 사용하여 정의된 모든 파티션에 열을 추가한 후, 테이블 속성 편집 대화 상자를 사용하여 테이블 정의에 열을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-117">When adding a column to a table that contains two or more partitions, before adding the column to the table definition by using the Edit Table Properties dialog box, you must first use Partition Manager to add the column to all defined partitions.</span></span> <span data-ttu-id="e4a51-118">정의된 파티션에 열을 추가한 후 테이블 속성 편집 대화 상자를 사용하여 테이블 정의에 동일한 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-118">After you have added the column to the defined partitions, you can then add the same column to the table definition by using the Edit Table Properties dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4a51-119">처음에 테이블 가져오기 마법사를 사용하여 데이터를 가져올 때 SQL 쿼리를 사용하여 테이블 및 열을 선택한 경우에는 나중에 테이블 속성 편집 대화 상자에서 모델 테이블에 열을 추가할 때에도 SQL 쿼리를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-119">If you used a SQL Query to select tables and columns when you initially used the Table Import Wizard to import data, you must again use a SQL Query in the Edit Table Properties dialog box to add columns to the model table.</span></span>  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a><span data-ttu-id="e4a51-120">테이블 속성 편집 대화 상자를 사용하여 데이터 원본의 열을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e4a51-120">To add a column from the data source by using the Edit Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="e4a51-121">모델 디자이너에서 열을 추가할 테이블을 클릭한 다음 **테이블** 메뉴를 클릭하고  **테이블 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-121">In the model designer, click on the table you want to add a column to, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="e4a51-122">**테이블 속성 편집** 대화 상자의 테이블 미리 보기 창에서 추가할 원본 열을 선택한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-122">In the **Edit Table Properties** dialog box, in the table preview window, select the source column you want to add, and then click OK.</span></span> <span data-ttu-id="e4a51-123">이때 모델 테이블 정의에 이미 포함된 열은 확인란이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-123">Columns already included in the table definition will already be checked.</span></span>  
  
## <a name="add-a-calculated-column"></a><span data-ttu-id="e4a51-124">계산 열 추가</span><span class="sxs-lookup"><span data-stu-id="e4a51-124">Add a Calculated Column</span></span>  
 <span data-ttu-id="e4a51-125">계산 열에서는 DAX 수식에 따라 각 행의 값이 정해집니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-125">In a calculated column, a DAX formula is used to define a value for each row.</span></span> <span data-ttu-id="e4a51-126">예를 들어 각 행에 값으로 1을 추가하는 간단한 수식(=1)으로 계산된 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-126">For example, you can create a calculated column with a simple formula (=1) that adds a value of 1 to each row.</span></span> <span data-ttu-id="e4a51-127">또는 모델의 다른 데이터를 바탕으로 값을 계산하는 좀 더 복잡한 수식의 계산된 열을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-127">Calculated columns can also have more complex formulas that calculate values based on other data in the model.</span></span> <span data-ttu-id="e4a51-128">계산 열은 다른 항목에서 더 자세히 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-128">Calculated columns are covered in more detail in other topics.</span></span> <span data-ttu-id="e4a51-129">자세한 내용은 [계산 열&#40;SSAS 테이블 형식&#41;](ssas-calculated-columns.md)에서 작성된 테이블 형식 모델 프로젝트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-129">For more information, see [Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md).</span></span>  
  
#### <a name="to-create-a-calculated-column"></a><span data-ttu-id="e4a51-130">계산 열을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e4a51-130">To create a calculated column</span></span>  
  
1.  <span data-ttu-id="e4a51-131">모델 디자이너의 데이터 뷰에서 새로운 빈 계산 열을 추가하려는 테이블을 선택한 다음 맨 오른쪽 열로 스크롤하거나 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-131">In the model designer, in Data View, select the table to which you want to add a new, blank calculated column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="e4a51-132">기존의 두 열 사이에 새 열을 만들려면 기존 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-132">To create a new column between two existing columns, right-click on an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="e4a51-133">수식 입력줄에 DAX 수식을 입력하여 각 행에 대한 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-133">In the formula bar, type a DAX formula to add attributes for each row.</span></span>  
  
## <a name="add-a-blank-column"></a><span data-ttu-id="e4a51-134">빈 열 추가</span><span class="sxs-lookup"><span data-stu-id="e4a51-134">Add a Blank Column</span></span>  
 <span data-ttu-id="e4a51-135">모델 테이블에서 명명된 빈 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-135">You can create a named, blank column in a model table.</span></span> <span data-ttu-id="e4a51-136">빈 열은 다른 원본에서 데이터를 가져와서 붙여넣을 경우에 유용하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-136">Blank columns can be useful if you want to paste data from another source.</span></span> <span data-ttu-id="e4a51-137">붙여넣은 데이터는 가져올 때와 다르게 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-137">Keep in-mind that pasted data is stored differently than imported data.</span></span> <span data-ttu-id="e4a51-138">자세한 내용은 [데이터 복사 및 붙여넣기&#40;SSAS 테이블 형식&#41;](../copy-and-paste-data-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4a51-138">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
#### <a name="to-create-a-named-blank-column"></a><span data-ttu-id="e4a51-139">명명된 빈 열을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e4a51-139">To create a named, blank column</span></span>  
  
1.  <span data-ttu-id="e4a51-140">모델 디자이너의 데이터 뷰에서 빈 열을 추가하려는 테이블을 선택한 다음 맨 오른쪽 열로 스크롤하거나 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-140">In the model designer, in Data View, select the table to which you want to add a blank column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="e4a51-141">기존의 두 열 사이에 새 열을 만들려면 기존 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-141">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="e4a51-142">맨 위 셀을 클릭하고 이름을 입력한 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e4a51-142">Click on the top cell, then type a name, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a51-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4a51-143">See Also</span></span>  
 <span data-ttu-id="e4a51-144">[테이블 속성 편집 대화 상자 &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="e4a51-144">[Edit Table Properties Dialog Box &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span></span>  
 [<span data-ttu-id="e4a51-145">테이블, 열 또는 행 필터 매핑 변경&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="e4a51-145">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
