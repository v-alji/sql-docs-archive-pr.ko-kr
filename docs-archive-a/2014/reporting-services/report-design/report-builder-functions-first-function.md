---
title: First 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0914520-30c5-4d63-9b59-8d9342ed63b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cd8578a1d9a17030d603457d4eaadf107316bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650714"
---
# <a name="first-function-report-builder-and-ssrs"></a><span data-ttu-id="126e2-102">First 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="126e2-102">First Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="126e2-103">지정된 식의 지정된 범위에서 첫 번째 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-103">Returns the first value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="126e2-104">구문</span><span class="sxs-lookup"><span data-stu-id="126e2-104">Syntax</span></span>  
  
```  
  
First(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="126e2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="126e2-105">Parameters</span></span>  
 <span data-ttu-id="126e2-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="126e2-106">*expression*</span></span>  
 <span data-ttu-id="126e2-107">(`Variant` 또는 `Binary`) 집계를 수행할 식의 예는 `=Fields!FieldName.Value`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.</span></span>  
  
 <span data-ttu-id="126e2-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="126e2-108">*scope*</span></span>  
 <span data-ttu-id="126e2-109">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-109">(`String`) Optional.</span></span> <span data-ttu-id="126e2-110">집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="126e2-111">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-111">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="126e2-112">반환 형식</span><span class="sxs-lookup"><span data-stu-id="126e2-112">Return Type</span></span>  
 <span data-ttu-id="126e2-113">식 유형에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-113">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126e2-114">설명</span><span class="sxs-lookup"><span data-stu-id="126e2-114">Remarks</span></span>  
 <span data-ttu-id="126e2-115">`First` 함수는 지정된 범위에 모든 정렬 및 필터링을 적용한 후 데이터 집합에서 첫 번째 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-115">The `First` function returns the first value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="126e2-116">`First` 함수는 그룹 필터 식에서 현재(기본) 범위 외에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-116">The `First` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="126e2-117">페이지의 첫 번째와 마지막 항목을 표시하는 사전 스타일의 머리글을 만들기 위해 페이지 머리글에 `First`를 사용하여 페이지에 대한 `ReportItems` 컬렉션의 첫 번째 값을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-117">You can also use `First` in a page header to return the first value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="126e2-118">*scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-118">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="126e2-119">외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-119">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="126e2-120">집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-120">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="126e2-121">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-121">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="126e2-122">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-122">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="126e2-123">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-123">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="126e2-124">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-124">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="126e2-125">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="126e2-125">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="126e2-126">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-126">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="126e2-127">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="126e2-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="126e2-128">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="126e2-128">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="126e2-129">예제</span><span class="sxs-lookup"><span data-stu-id="126e2-129">Example</span></span>  
 <span data-ttu-id="126e2-130">다음 코드 예에서는 데이터 영역의 `Category` 그룹에서 첫 번째 제품 번호를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="126e2-130">The following code example returns the first product number in the `Category` group of a data region:</span></span>  
  
```  
=First(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="126e2-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="126e2-131">See Also</span></span>  
 <span data-ttu-id="126e2-132">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="126e2-132">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="126e2-133">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="126e2-133">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="126e2-134">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="126e2-134">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="126e2-135">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="126e2-135">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
