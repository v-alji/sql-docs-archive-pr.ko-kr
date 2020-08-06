---
title: Aggregate 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fcc65f1e60c29ba9ea6a4206b419eb0b13edb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651491"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a><span data-ttu-id="66c98-102">Aggregate 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="66c98-102">Aggregate Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="66c98-103">데이터 공급자가 정의한 대로 지정한 식의 사용자 지정 집계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-103">Returns a custom aggregate of the specified expression, as defined by the data provider.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="66c98-104">구문</span><span class="sxs-lookup"><span data-stu-id="66c98-104">Syntax</span></span>  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66c98-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="66c98-105">Parameters</span></span>  
 <span data-ttu-id="66c98-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="66c98-106">*expression*</span></span>  
 <span data-ttu-id="66c98-107">집계를 수행할 식입니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-107">The expression on which to perform the aggregation.</span></span> <span data-ttu-id="66c98-108">식은 단순 필드 참조여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-108">The expression must be a simple field reference.</span></span>  
  
 <span data-ttu-id="66c98-109">*범위*</span><span class="sxs-lookup"><span data-stu-id="66c98-109">*scope*</span></span>  
 <span data-ttu-id="66c98-110">(`String`) 집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-110">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="66c98-111">*Scope* 는 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-111">*Scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="66c98-112">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-112">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="66c98-113">반환 형식</span><span class="sxs-lookup"><span data-stu-id="66c98-113">Return Type</span></span>  
 <span data-ttu-id="66c98-114">반환 형식은 데이터 공급자에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-114">Return type is determined by the data provider.</span></span> <span data-ttu-id="66c98-115">데이터 공급자가 이 함수를 지원하지 않거나 데이터를 사용할 수 없는 경우 `Nothing`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-115">Returns `Nothing` if the data provider does not support this function or data is not available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c98-116">설명</span><span class="sxs-lookup"><span data-stu-id="66c98-116">Remarks</span></span>  
 <span data-ttu-id="66c98-117">`Aggregate` 함수를 통해 외부 데이터 원본에서 계산되는 집계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-117">The `Aggregate` function provides a way to use aggregates that are calculated on the external data source.</span></span> <span data-ttu-id="66c98-118">이 기능에 대한 지원은 데이터 확장 프로그램에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-118">Support for this feature is determined by the data extension.</span></span> <span data-ttu-id="66c98-119">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 처리 확장 프로그램은 MDX 쿼리에서 일반 행 세트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-119">For example, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension retrieves flattened rowsets from an MDX query.</span></span> <span data-ttu-id="66c98-120">결과 집합의 일부 행에는 데이터 원본 서버에서 계산된 집계 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-120">Some rows in the result set can contain aggregate values calculated on the data source server.</span></span> <span data-ttu-id="66c98-121">이를 *서버 집계*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-121">These are known as *server aggregates*.</span></span> <span data-ttu-id="66c98-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]용 그래픽 쿼리 디자이너에서 서버 집계를 보려면 도구 모음에서 **집계 표시** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-122">To view server aggregates in the graphical query designer for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the **Show Aggregate** button on the toolbar.</span></span> <span data-ttu-id="66c98-123">자세한 내용은 [Analysis Services MDX 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66c98-123">For more information, see [Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="66c98-124">테이블릭스 데이터 영역의 정보 행에 집계 및 정보 데이터 세트 값의 조합을 표시할 때 서버 집계는 정보 데이터가 아니므로 일반적으로 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-124">When you display the combination of aggregate and detail dataset values on detail rows of a Tablix data region, server aggregates would not typically be included because they are not detail data.</span></span> <span data-ttu-id="66c98-125">하지만 데이터 세트에 대해 검색된 모든 값을 표시하고 집계 데이터가 계산 및 표시되는 방식을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-125">However, you may want to display all values retrieved for the dataset and customize the way aggregate data is calculated and displayed.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="66c98-126">가 표시되는지 확인하기 위해 보고서 식에서 `Aggregate` 함수의 사용 여부를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-126">detects the use of the `Aggregate` function in expressions in your report in order to determine whether to display server aggregates on detail rows.</span></span> <span data-ttu-id="66c98-127">데이터 영역의 식에 `Aggregate`를 포함할 경우 서버 집계는 그룹 합계 또는 총합계 행에만 표시되며 정보 행에는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-127">If you include `Aggregate` in an expression in a data region, server aggregates can only appear on group total or grand total rows, not on detail rows.</span></span> <span data-ttu-id="66c98-128">서버 집계를 정보 행에 표시하려면 `Aggregate` 함수를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="66c98-128">If you want to display server aggregates on detail rows, do not use the `Aggregate` function.</span></span>  
  
 <span data-ttu-id="66c98-129">이러한 기본 동작은 **데이터 세트 속성** 대화 상자에서 **부분합을 정보 행으로 해석** 옵션의 값을 수정하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-129">You can change this default behavior by changing the value of the **Interpret subtotals as details** option on the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="66c98-130">이 옵션이 `True`로 설정된 경우 서버 집계를 포함한 모든 데이터가 정보 데이터로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-130">When this option is set to `True`, all data, including server aggregates, appears as detail data.</span></span> <span data-ttu-id="66c98-131">`False`로 설정된 경우 서버 집계가 합계로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-131">When set to `False`, server aggregates appear as totals.</span></span> <span data-ttu-id="66c98-132">이 속성에 대한 설정은 이 데이터 세트에 연결되어 있는 모든 데이터 영역에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-132">The setting for this property affects all data regions that are linked to this dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66c98-133">`Aggregate`를 참조하는 보고서 항목에 대한 모든 포함 그룹에는 해당 그룹 식에 대한 단순 필드 참조가 있어야 합니다(예: `[FieldName]`).</span><span class="sxs-lookup"><span data-stu-id="66c98-133">All containing groups for the report item that references `Aggregate` must have simple field references for their group expressions, for example, `[FieldName]`.</span></span> <span data-ttu-id="66c98-134">복잡한 그룹 식을 사용하는 데이터 영역에서는 `Aggregate`를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-134">You cannot use `Aggregate` in a data region that uses complex group expressions.</span></span> <span data-ttu-id="66c98-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 처리 확장 프로그램의 경우 `Aggregate` 함수를 사용하여 집계를 지원하려면 쿼리에 `MemberProperty`가 아닌 `LevelProperty` 형식의 MDX 필드가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-135">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension, your query must include MDX fields of type `LevelProperty` (not `MemberProperty`) to support aggregation using the `Aggregate`function.</span></span>  
  
 <span data-ttu-id="66c98-136">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-136">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="66c98-137">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-137">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="66c98-138">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-138">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="66c98-139">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-139">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="66c98-140">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="66c98-140">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="66c98-141">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-141">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="66c98-142">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66c98-142">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="66c98-143">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66c98-143">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a><span data-ttu-id="66c98-144">Aggregate 함수와 Sum 함수 비교</span><span class="sxs-lookup"><span data-stu-id="66c98-144">Comparing the Aggregate and Sum Functions</span></span>  
 <span data-ttu-id="66c98-145">`Aggregate` 함수는 `Sum`과 같은 숫자 집계 함수와 다릅니다. 즉, `Aggregate` 함수는 데이터 공급자 또는 데이터 처리 확장 프로그램에 의해 계산되는 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-145">The `Aggregate` function differs from numeric aggregate functions like `Sum` in that the `Aggregate` function returns a value that is calculated by the data provider or data processing extension.</span></span> <span data-ttu-id="66c98-146">과 같은 숫자 집계 함수는 `Sum` *범위* 매개 변수에 의해 결정 되는 데이터 집합의 데이터 집합에 대 한 보고서 처리기에서 계산 된 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-146">Numeric aggregate functions like `Sum` return a value that is calculated by the report processor on a set of data from the dataset that is determined by the *scope* parameter.</span></span> <span data-ttu-id="66c98-147">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)에 나열된 집계 함수를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66c98-147">For more information, see the aggregate functions listed in [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c98-148">예제</span><span class="sxs-lookup"><span data-stu-id="66c98-148">Example</span></span>  
 <span data-ttu-id="66c98-149">다음 코드 예에서는 `LineTotal`필드에 대한 서버 집계를 검색하는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-149">The following code example shows an expression that retrieves a server aggregate for the field `LineTotal`.</span></span> <span data-ttu-id="66c98-150">`GroupbyOrder`그룹에 속하는 행의 셀에 식이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="66c98-150">The expression is added to a cell in a row that belongs to the group `GroupbyOrder`.</span></span>  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a><span data-ttu-id="66c98-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66c98-151">See Also</span></span>  
 <span data-ttu-id="66c98-152">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66c98-152">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66c98-153">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66c98-153">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66c98-154">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66c98-154">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="66c98-155">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66c98-155">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
