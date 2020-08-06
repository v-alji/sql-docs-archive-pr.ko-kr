---
title: 계산 열 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e1011278-556d-4984-b01d-a37f8a33b304
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d77b36ee3327d1b9e0d31ac97e5dbe135093a63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727352"
---
# <a name="calculated-columns-ssas-tabular"></a><span data-ttu-id="86762-102">계산 열(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="86762-102">Calculated Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="86762-103">테이블 형식 모델에서 계산 열을 사용하여 새 데이터를 모델에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-103">Calculated columns, in tabular models, allow you to add new data to your model.</span></span> <span data-ttu-id="86762-104">열에 값을 붙여 넣거나 가져오는 대신 열의 행 수준 값을 정의 하는 DAX 수식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86762-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="86762-105">그러면 보고서, 피벗 테이블 또는 피벗 차트에서 다른 열과 마찬가지로 계산 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-105">The calculated column can then be used in a report, PivotTable, or PivotChart as would any other column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86762-106">DirectQuery 모드의 테이블 형식 모델에 대해서는 계산 열이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-106">Calculated columns are not supported for tabular models in DirectQuery mode.</span></span> <span data-ttu-id="86762-107">자세한 내용은 [DirectQuery 모드&#40;SSAS 테이블 형식&#41;](directquery-mode-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86762-107">For more information, see [DirectQuery Mode &#40;SSAS Tabular&#41;](directquery-mode-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="86762-108">이 항목의 섹션:</span><span class="sxs-lookup"><span data-stu-id="86762-108">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="86762-109">이점</span><span class="sxs-lookup"><span data-stu-id="86762-109">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="86762-110">계산 열 이름 지정</span><span class="sxs-lookup"><span data-stu-id="86762-110">Naming a Calculated Column</span></span>](#bkmk_naming)  
  
-   [<span data-ttu-id="86762-111">계산 열의 성능</span><span class="sxs-lookup"><span data-stu-id="86762-111">Performance of Calculated Columns</span></span>](#bkmk_perf)  
  
-   [<span data-ttu-id="86762-112">관련 작업</span><span class="sxs-lookup"><span data-stu-id="86762-112">Related Tasks</span></span>](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="86762-113">이점</span><span class="sxs-lookup"><span data-stu-id="86762-113">Benefits</span></span>  
 <span data-ttu-id="86762-114">계산 열의 수식은 Excel의 수식과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-114">Formulas in calculated columns are much like formulas in Excel.</span></span> <span data-ttu-id="86762-115">하지만 Excel과는 달리, 테이블의 행마다 서로 다른 수식을 만들 수 없습니다. 대신 DAX 수식이 전체 열에 자동으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-115">Unlike Excel, however, you cannot create different formulas for different rows in a table; instead, the DAX formula is automatically applied to the entire column.</span></span>  
  
 <span data-ttu-id="86762-116">열에 수식이 있으면 각 행에 대해 값이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-116">When a column contains a formula, the value is computed for each row.</span></span> <span data-ttu-id="86762-117">유효한 수식을 입력하면 열에 대해 결과가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-117">The results are calculated for the column when you enter a valid formula.</span></span> <span data-ttu-id="86762-118">그런 다음 내부 데이터가 새로 고쳐지는 경우와 같이 필요에 따라 열 값이 다시 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-118">Column values are then recalculated as necessary, such as when the underlying data is refreshed.</span></span>  
  
 <span data-ttu-id="86762-119">측정값과 다른 계산된 열을 기반으로 하는 계산된 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-119">You can create calculated columns that are based on measures and other calculated columns.</span></span> <span data-ttu-id="86762-120">예를 들어, 계산 열 하나를 만들어 텍스트 문자열에서 숫자를 추출한 다음 해당 숫자를 다른 계산 열에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-120">For example, you might create one calculated column to extract a number from a string of text, and then use that number in another calculated column.</span></span>  
  
 <span data-ttu-id="86762-121">계산 열은 기존 테이블에 이미 있는 데이터를 기반으로 하거나 DAX 수식을 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="86762-121">A calculated column is based on data that you already have in an existing table, or created by using a DAX formula.</span></span> <span data-ttu-id="86762-122">예를 들어 값을 연결하거나, 더하기를 수행하거나, 부분 문자열을 추출하거나, 다른 필드의 값과 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-122">For example, you might choose to concatenate values, perform addition, extract substrings, or compare the values in other fields.</span></span> <span data-ttu-id="86762-123">계산 열을 추가하려면 모델에 테이블이 최소한 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-123">To add a calculated column, you must have at least one table in your model.</span></span>  
  
 <span data-ttu-id="86762-124">다음 예제에서는 계산 열의 간단한 수식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-124">This example demonstrates a simple formula in a calculated column:</span></span>  
  
```  
=EOMONTH([StartDate],0])  
  
```  
  
 <span data-ttu-id="86762-125">이 수식은 StartDate 열에서 월을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-125">This formula extracts the month from the StartDate column.</span></span> <span data-ttu-id="86762-126">그런 다음 테이블의 각 행에 대해 월의 마지막 날을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-126">It then calculates the end of the month value for each row in the table.</span></span> <span data-ttu-id="86762-127">두 번째 매개 변수는 StartDate에서 해당 월의 이전 또는 이후의 월 수를 지정합니다. 이 경우 0이며 같은 달임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="86762-127">The second parameter specifies the number of months before or after the month in StartDate; in this case, 0 means the same month.</span></span> <span data-ttu-id="86762-128">예를 들어 StartDate 열의 값이 6/1/2001일 경우 계산 열의 값은 6/30/2001이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-128">For example, if the value in the StartDate column is 6/1/2001, the value in the calculated column will be 6/30/2001.</span></span>  
  
##  <a name="naming-a-calculated-column"></a><a name="bkmk_naming"></a><span data-ttu-id="86762-129">계산 열 이름 지정</span><span class="sxs-lookup"><span data-stu-id="86762-129">Naming a Calculated Column</span></span>  
 <span data-ttu-id="86762-130">기본적으로 새 계산 열은 테이블의 다른 열 오른쪽에 추가되며, **CalculatedColumn1**, **CalculatedColumn2**등의 기본 이름이 열에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-130">By default, new calculated columns are added to the right of other columns in a table, and the column is automatically assigned the default name of **CalculatedColumn1**, **CalculatedColumn2**, and so forth.</span></span> <span data-ttu-id="86762-131">열을 마우스 오른쪽 단추로 클릭한 다음 열 삽입을 클릭하여 두 개의 기존 열 사이에 새 열을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-131">You can also right click a column, and then click Insert Column to create a new column between two existing columns.</span></span> <span data-ttu-id="86762-132">동일한 테이블 내에서 열을 클릭하고 끌어서 다시 정렬할 수 있으며 열을 만든 후에 열의 이름을 바꿀 수 있습니다. 하지만 계산 열의 변경에 대해 다음과 같은 제한 사항을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-132">You can rearrange columns within the same table by clicking and dragging, and you can rename columns after they are created; however, you should be aware of the following restrictions on changes to calculated columns:</span></span>  
  
-   <span data-ttu-id="86762-133">각 열 이름은 테이블에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-133">Each column name must be unique within a table.</span></span>  
  
-   <span data-ttu-id="86762-134">동일한 모델 내에서 측정값에 이미 사용된 이름은 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="86762-134">Avoid names that have already been used for measures within the same model.</span></span> <span data-ttu-id="86762-135">측정값과 계산 열에 동일한 이름을 사용할 수 있지만 이름이 고유하지 않으면 계산 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-135">Although it is possible for a measure and a calculated column to have the same name, if names are not unique you can get calculation errors.</span></span> <span data-ttu-id="86762-136">열을 참조할 때는 실수로 측정값을 호출하지 않으려면 항상 정규화된 열 참조를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-136">To avoid accidentally invoking a measure, when referring to a column always use a fully qualified column reference.</span></span>  
  
-   <span data-ttu-id="86762-137">계산 열의 이름을 바꿀 때는 해당 열에 의존하는 공식을 수동으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-137">When you rename a calculated column, any formulas that rely on the column must be updated manually.</span></span> <span data-ttu-id="86762-138">수동 업데이트 모드가 아닌 한 수식 결과 업데이트는 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-138">Unless you are in manual update mode, updating the results of formulas takes place automatically.</span></span> <span data-ttu-id="86762-139">하지만 이 작업은 어느 정도 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-139">However, this operation might take some time.</span></span>  
  
-   <span data-ttu-id="86762-140">열 이름 내에 사용할 수 없는 몇 가지 문자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-140">There are some characters that cannot be used within the names of columns.</span></span> <span data-ttu-id="86762-141">자세한 내용은 [DAX Syntax Specification for PowerPivot](/dax/dax-syntax-reference)의 "명명 요구 사항"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="86762-141">For more information, see "Naming Requirements" in [DAX Syntax Specification for PowerPivot](/dax/dax-syntax-reference).</span></span>  
  
##  <a name="performance-of-calculated-columns"></a><a name="bkmk_perf"></a><span data-ttu-id="86762-142">계산 열의 성능</span><span class="sxs-lookup"><span data-stu-id="86762-142">Performance of Calculated Columns</span></span>  
 <span data-ttu-id="86762-143">계산 열의 수식은 측정값에 사용된 수식보다 더 많은 리소스가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-143">The formula for a calculated column can be more resource-intensive than the formula used for a measure.</span></span> <span data-ttu-id="86762-144">한 가지 이유는 계산 열의 결과는 테이블의 각 행에 대해 항상 계산되지만 측정값은 보고서, 피벗 테이블 또는 피벗 차트에 사용된 필터에 의해 정의된 셀에 대해서만 계산된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86762-144">One reason is that the result for a calculated column is always calculated for each row in a table, whereas a measure is only calculated for the cells defined by the filter used in a report, PivotTable, or PivotChart.</span></span> <span data-ttu-id="86762-145">예를 들어 백만 개의 행이 있는 테이블에는 항상 백만 개의 결과가 있는 계산 열이 있으며 성능에 대한 영향이 각각 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="86762-145">For example, a table with a million rows will always have a calculated column with a million results, and a corresponding effect on performance.</span></span> <span data-ttu-id="86762-146">하지만 피벗 테이블은 일반적으로 행 및 열 머리글을 적용하여 데이터를 필터링하므로 피벗 테이블의 각 셀에 있는 데이터의 하위 집합에 대해서만 측정값이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-146">However, a PivotTable generally filters data by applying row and column headings; therefore, a measure is calculated only for the subset of data in each cell of the PivotTable.</span></span>  
  
 <span data-ttu-id="86762-147">수식에는 값을 평가하는 식이나 다른 열과 같은 수식에서 참조되는 개체에 대한 종속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-147">A formula has dependencies on the objects that are referenced in the formula, such as other columns or expressions that evaluate values.</span></span> <span data-ttu-id="86762-148">예를 들어 다른 열을 기반으로 하는 계산된 열을 계산하거나 열 참조가 있는 식을 포함하는 계산을 수행하려면 먼저 다른 열을 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-148">For example, a calculated column that is based on another column, or a calculation that contains an expression with a column reference, cannot be evaluated until the other column is evaluated.</span></span> <span data-ttu-id="86762-149">통합 문서에는 기본적으로 자동 새로 고침이 사용되도록 설정되어 있으므로 값이 업데이트되고 수식이 새로 고쳐지는 동안에는 해당 종속성이 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-149">By default, automatic refresh is enabled in workbooks; therefore, all such dependencies can affect performance while values are updated and formulas refreshed.</span></span>  
  
 <span data-ttu-id="86762-150">계산된 열을 만들 때 성능 문제를 방지하려면 다음 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="86762-150">To avoid performance issues when you create calculated columns, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="86762-151">여러 복잡한 종속성이 포함된 단일 수식을 작성하기 보다는 결과를 확인하고 성능을 평가할 수 있도록 결과를 열에 저장하면서 단계별로 수식을 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="86762-151">Rather than create a single formula that contains many complex dependencies, create the formulas in steps, with results saved to columns, so that you can validate the results and assess performance.</span></span>  
  
-   <span data-ttu-id="86762-152">데이터를 수정하면 계산된 열을 다시 계산해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="86762-152">Modification of data will often require that calculated columns be recalculated.</span></span> <span data-ttu-id="86762-153">다시 계산 모드를 수동으로 설정하여 이런 경우를 방지할 수 있지만 계산된 열의 값이 잘못된 경우 데이터를 새로 고치거나 다시 계산할 때까지 해당 열은 회색으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="86762-153">You can prevent this by setting the recalculation mode to manual; however, if any values in the calculated column are incorrect the column will be grayed out until you refresh and recalculate the data.</span></span>  
  
-   <span data-ttu-id="86762-154">테이블 간의 관계를 변경하거나 삭제하는 경우 이러한 테이블의 열을 사용하는 수식이 유효하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86762-154">If you change or delete relationships between tables, formulas that use columns in those tables will become invalid.</span></span>  
  
-   <span data-ttu-id="86762-155">순환 참조 또는 자체 참조 종속성이 있는 수식을 만드는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-155">If you create a formula that contains a circular or self-referencing dependency, an error will occur.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> <span data-ttu-id="86762-156">관련 작업</span><span class="sxs-lookup"><span data-stu-id="86762-156">Related Tasks</span></span>  
  
|<span data-ttu-id="86762-157">항목</span><span class="sxs-lookup"><span data-stu-id="86762-157">Topic</span></span>|<span data-ttu-id="86762-158">Description</span><span class="sxs-lookup"><span data-stu-id="86762-158">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="86762-159">계산 열 만들기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="86762-159">Create a Calculated Column &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns-create-a-calculated-column.md)|<span data-ttu-id="86762-160">이 항목의 태스크에서는 새 계산 열을 테이블에 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86762-160">Tasks in this topic describe how to add a new calculated column to a table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86762-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86762-161">See Also</span></span>  
 <span data-ttu-id="86762-162">[SSAS 테이블 형식&#41;&#40;테이블 및 열](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="86762-162">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="86762-163">[SSAS 테이블 형식&#41;&#40;측정값](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="86762-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="86762-164">계산&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="86762-164">Calculations &#40;SSAS Tabular&#41;</span></span>](calculations-ssas-tabular.md)  
  
  
