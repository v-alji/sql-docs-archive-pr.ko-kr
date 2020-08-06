---
title: Count 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3617e64d804b6b0f3d9522b5a089f418a942568a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659815"
---
# <a name="count-function-report-builder-and-ssrs"></a><span data-ttu-id="8d968-102">Count 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8d968-102">Count Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8d968-103">식으로 지정되어 정해진 범위의 컨텍스트에서 계산되는 Null이 아닌 값의 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-103">Returns a count of non-null values specified by the expression, evaluated in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="8d968-104">구문</span><span class="sxs-lookup"><span data-stu-id="8d968-104">Syntax</span></span>  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d968-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d968-105">Parameters</span></span>  
 <span data-ttu-id="8d968-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="8d968-106">*expression*</span></span>  
 <span data-ttu-id="8d968-107">(`Variant` 또는 `Binary`) 집계를 수행할 식의 예는 `=Fields!FieldName.Value`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.</span></span>  
  
 <span data-ttu-id="8d968-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="8d968-108">*scope*</span></span>  
 <span data-ttu-id="8d968-109">(`String`) 집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-109">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="8d968-110">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-110">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="8d968-111">*재귀*</span><span class="sxs-lookup"><span data-stu-id="8d968-111">*recursive*</span></span>  
 <span data-ttu-id="8d968-112">(**열거 형식**) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-112">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="8d968-113">`Simple`(기본값) 또는 `RdlRecursive`로,</span><span class="sxs-lookup"><span data-stu-id="8d968-113">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="8d968-114">집계를 재귀적으로 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-114">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="8d968-115">반환 형식</span><span class="sxs-lookup"><span data-stu-id="8d968-115">Return Type</span></span>  
 <span data-ttu-id="8d968-116">`Integer`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-116">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d968-117">설명</span><span class="sxs-lookup"><span data-stu-id="8d968-117">Remarks</span></span>  
 <span data-ttu-id="8d968-118">*scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-118">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="8d968-119">외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-119">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="8d968-120">집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-120">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="8d968-121">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-121">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="8d968-122">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-122">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="8d968-123">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-123">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="8d968-124">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-124">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="8d968-125">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="8d968-125">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="8d968-126">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-126">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="8d968-127">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d968-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="8d968-128">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d968-128">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8d968-129">예제</span><span class="sxs-lookup"><span data-stu-id="8d968-129">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d968-130">Description</span><span class="sxs-lookup"><span data-stu-id="8d968-130">Description</span></span>  
 <span data-ttu-id="8d968-131">다음 코드 예에서는 기본 범위 및 부모 그룹 범위에 대해 Null이 아닌 `Size` 값의 수를 계산하는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-131">The following code example shows an expression that calculates the number of non-null values of `Size` for the default scope and for a parent group scope.</span></span> <span data-ttu-id="8d968-132">`GroupbySubcategory`자식 그룹에 속하는 행의 셀에 식이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-132">The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`.</span></span> <span data-ttu-id="8d968-133">부모 그룹은 `GroupbyCategory`입니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-133">The parent group is `GroupbyCategory`.</span></span> <span data-ttu-id="8d968-134">식은 `GroupbySubcategory` (기본 범위)에 대한 결과를 표시한 후 `GroupbyCategory` (부모 그룹 범위)에 대한 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-134">The expression displays the results for `GroupbySubcategory` (the default scope) and then for `GroupbyCategory` (the parent group scope).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d968-135">식은 실제 캐리지 리턴 및 줄 바꿈을 포함할 수 없습니다. 예의 이러한 항목은 설명서 작성의 편의를 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d968-135">Expressions should not contain actual carriage returns and line breaks; these are included in the example to support documentation renderers.</span></span> <span data-ttu-id="8d968-136">다음 예를 복사할 경우 각 줄에서 캐리지 리턴을 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d968-136">If you copy the following example, remove carriage returns from each line.</span></span>  
  
## <a name="code"></a><span data-ttu-id="8d968-137">코드</span><span class="sxs-lookup"><span data-stu-id="8d968-137">Code</span></span>  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d968-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d968-138">See Also</span></span>  
 <span data-ttu-id="8d968-139">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d968-139">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8d968-140">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d968-140">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8d968-141">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d968-141">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8d968-142">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d968-142">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
