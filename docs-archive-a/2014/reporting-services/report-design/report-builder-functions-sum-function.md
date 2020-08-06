---
title: Sum 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2b45a024-398d-43b8-9948-b8b23fb674c9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3fce5e86ead5e2d802c7af79650e7419f45f62c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650683"
---
# <a name="sum-function-report-builder-and-ssrs"></a><span data-ttu-id="0ab0e-102">Sum 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0ab0e-102">Sum Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0ab0e-103">식으로 지정되어 정해진 범위에서 계산되는 Null이 아닌 모든 숫자 값의 합계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-103">Returns the sum of all the non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="0ab0e-104">구문</span><span class="sxs-lookup"><span data-stu-id="0ab0e-104">Syntax</span></span>  
  
```  
  
Sum(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ab0e-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0ab0e-105">Parameters</span></span>  
 <span data-ttu-id="0ab0e-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="0ab0e-106">*expression*</span></span>  
 <span data-ttu-id="0ab0e-107">(`Integer` 또는 `Float`) 집계를 수행할 식입니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-107">(`Integer` or `Float`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="0ab0e-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="0ab0e-108">*scope*</span></span>  
 <span data-ttu-id="0ab0e-109">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-109">(`String`) Optional.</span></span> <span data-ttu-id="0ab0e-110">집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="0ab0e-111">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="0ab0e-112">*재귀*</span><span class="sxs-lookup"><span data-stu-id="0ab0e-112">*recursive*</span></span>  
 <span data-ttu-id="0ab0e-113">(**열거 형식**) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="0ab0e-114">`Simple`(기본값) 또는 `RdlRecursive`로,</span><span class="sxs-lookup"><span data-stu-id="0ab0e-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="0ab0e-115">집계를 재귀적으로 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="0ab0e-116">반환 형식</span><span class="sxs-lookup"><span data-stu-id="0ab0e-116">Return Type</span></span>  
 <span data-ttu-id="0ab0e-117">10진수 식에는 `Decimal`을, 그 외 다른 식에는 `Double`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-117">Returns a `Decimal` for decimal expressions and a `Double` for all other expressions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ab0e-118">설명</span><span class="sxs-lookup"><span data-stu-id="0ab0e-118">Remarks</span></span>  
 <span data-ttu-id="0ab0e-119">식에 지정한 데이터 집합은 동일한 데이터 형식으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="0ab0e-120">여러 숫자 데이터 형식이 포함된 데이터를 동일한 데이터 형식으로 변환하려면 `CInt`, `CDbl` 또는 `CDec` 같은 변환 함수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="0ab0e-121">자세한 내용은 [형식 변환 함수](https://go.microsoft.com/fwlink/?LinkId=96142)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="0ab0e-122">*scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-122">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="0ab0e-123">외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="0ab0e-124">집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="0ab0e-125">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="0ab0e-126">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="0ab0e-127">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="0ab0e-128">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="0ab0e-129">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="0ab0e-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="0ab0e-130">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="0ab0e-131">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="0ab0e-132">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ab0e-133">예제</span><span class="sxs-lookup"><span data-stu-id="0ab0e-133">Example</span></span>  
 <span data-ttu-id="0ab0e-134">다음의 두 코드 예에서는 `Order` 그룹 또는 데이터 영역에서 줄 항목 합계의 총계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-134">The following two code examples provides a sum of line item totals in the `Order` group or data region.</span></span>  
  
```  
=Sum(Fields!LineTotal.Value, "Order")  
' or   
=Sum(CDbl(Fields!LineTotal.Value), "Order")  
```  
  
## <a name="example"></a><span data-ttu-id="0ab0e-135">예제</span><span class="sxs-lookup"><span data-stu-id="0ab0e-135">Example</span></span>  
 <span data-ttu-id="0ab0e-136">중첩 행 그룹 Category 및 Subcategory와 중첩 열 그룹 Year 및 Quarter가 있는 행렬 데이터 영역의 가장 안쪽 행 및 열 그룹에 속하는 셀에서 다음 식은 모든 하위 범주에 대한 모든 분기의 최대값으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ab0e-136">In a matrix data region with nested row groups Category and Subcategory, and nested column groups Year and Quarter, in a cell that belongs to the innermost row and column groups, the following expression evaluates to the maximum value from all quarters for all subcategories.</span></span>  
  
```  
=Max(Sum(Fields!Sales.Value))  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ab0e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ab0e-137">See Also</span></span>  
 <span data-ttu-id="0ab0e-138">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ab0e-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ab0e-139">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ab0e-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0ab0e-140">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0ab0e-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0ab0e-141">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0ab0e-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
