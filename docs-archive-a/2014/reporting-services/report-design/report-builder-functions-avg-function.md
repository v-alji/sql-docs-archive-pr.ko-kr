---
title: Avg 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f1276c4c-bb44-44c0-a1bf-386a0c340003
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfa9d3517e3b3b0c2e4e01853ffa30295ec343df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736059"
---
# <a name="avg-function-report-builder-and-ssrs"></a><span data-ttu-id="b98fc-102">Avg 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b98fc-102">Avg Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b98fc-103">식으로 지정되어 정해진 범위에서 계산되는 Null이 아닌 모든 숫자 값의 평균을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-103">Returns the average of all non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="b98fc-104">구문</span><span class="sxs-lookup"><span data-stu-id="b98fc-104">Syntax</span></span>  
  
```  
  
Avg(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b98fc-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b98fc-105">Parameters</span></span>  
 <span data-ttu-id="b98fc-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="b98fc-106">*expression*</span></span>  
 <span data-ttu-id="b98fc-107">`Float`) 집계를 수행할 식입니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-107">(`Float`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="b98fc-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="b98fc-108">*scope*</span></span>  
 <span data-ttu-id="b98fc-109">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-109">(`String`) Optional.</span></span> <span data-ttu-id="b98fc-110">집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="b98fc-111">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="b98fc-112">*재귀*</span><span class="sxs-lookup"><span data-stu-id="b98fc-112">*recursive*</span></span>  
 <span data-ttu-id="b98fc-113">(**열거 형식**) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="b98fc-114">`Simple`(기본값) 또는 `RdlRecursive`로,</span><span class="sxs-lookup"><span data-stu-id="b98fc-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="b98fc-115">집계를 재귀적으로 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="b98fc-116">반환 형식</span><span class="sxs-lookup"><span data-stu-id="b98fc-116">Return Type</span></span>  
 <span data-ttu-id="b98fc-117">10진수 식에는 `Decimal`을, 그 외 다른 식에는 `Double`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-117">Returns a `Decimal` for decimal expressions and a `Double` for all other expressions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b98fc-118">설명</span><span class="sxs-lookup"><span data-stu-id="b98fc-118">Remarks</span></span>  
 <span data-ttu-id="b98fc-119">식에 지정한 데이터 집합은 동일한 데이터 형식으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="b98fc-120">여러 숫자 데이터 형식이 포함된 데이터를 동일한 데이터 형식으로 변환하려면 `CInt`, `CDbl` 또는 `CDec` 같은 변환 함수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="b98fc-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="b98fc-121">자세한 내용은 [형식 변환 함수](https://go.microsoft.com/fwlink/?LinkId=96142)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b98fc-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="b98fc-122">*scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-122">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="b98fc-123">외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="b98fc-124">집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="b98fc-125">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="b98fc-126">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="b98fc-127">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="b98fc-128">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="b98fc-129">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="b98fc-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="b98fc-130">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="b98fc-131">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b98fc-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="b98fc-132">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b98fc-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b98fc-133">예제</span><span class="sxs-lookup"><span data-stu-id="b98fc-133">Example</span></span>  
 <span data-ttu-id="b98fc-134">다음 두 코드 예에서는 `Cost`라는 데이터 세트에 포함된 `Inventory`필드의 모든 값에 대한 평균을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b98fc-134">The following two code examples provide an average of all values in the `Cost` field contained in a dataset named `Inventory`.</span></span>  
  
```  
=Avg(Fields!Cost.Value, "Inventory")   
  OR    
=Avg (CDbl(Fields!Cost.Value), "Inventory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b98fc-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b98fc-135">See Also</span></span>  
 <span data-ttu-id="b98fc-136">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b98fc-136">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b98fc-137">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b98fc-137">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b98fc-138">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b98fc-138">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b98fc-139">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b98fc-139">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
