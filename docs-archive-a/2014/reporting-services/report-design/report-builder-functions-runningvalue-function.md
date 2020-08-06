---
title: RunningValue 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 168073a0409455041f4ebe3aa4c5dcfc8fa129a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650692"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a><span data-ttu-id="d3e43-102">RunningValue 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d3e43-102">RunningValue Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d3e43-103">식으로 지정되어 정해진 범위에서 계산되는 Null이 아닌 모든 숫자 값의 실행 집계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-103">Returns a running aggregate of all non-null numeric values specified by the expression, evaluated for the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="d3e43-104">구문</span><span class="sxs-lookup"><span data-stu-id="d3e43-104">Syntax</span></span>  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e43-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d3e43-105">Parameters</span></span>  
 <span data-ttu-id="d3e43-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="d3e43-106">*expression*</span></span>  
 <span data-ttu-id="d3e43-107">집계를 수행할 식입니다(예: `[Quantity]`).</span><span class="sxs-lookup"><span data-stu-id="d3e43-107">The expression on which to perform the aggregation, for example, `[Quantity]`.</span></span>  
  
 <span data-ttu-id="d3e43-108">*function*</span><span class="sxs-lookup"><span data-stu-id="d3e43-108">*function*</span></span>  
 <span data-ttu-id="d3e43-109">(`Enum`) 식에 적용할 집계 함수의 이름입니다(예: `Sum`).</span><span class="sxs-lookup"><span data-stu-id="d3e43-109">(`Enum`) The name of the aggregate function to apply to the expression, for example, `Sum`.</span></span> <span data-ttu-id="d3e43-110">이 함수는 `RunningValue`, `RowNumber` 또는 `Aggregate`일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-110">This function cannot be `RunningValue`, `RowNumber`, or `Aggregate`.</span></span>  
  
 <span data-ttu-id="d3e43-111">*범위*</span><span class="sxs-lookup"><span data-stu-id="d3e43-111">*scope*</span></span>  
 <span data-ttu-id="d3e43-112">(`String`) 집계를 계산할 컨텍스트를 지정하는 데이터 세트, 데이터 영역, 그룹의 이름인 문자열 상수 또는 Null([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 `Nothing`)입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-112">(`String`) A string constant that is the name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the aggregation.</span></span> <span data-ttu-id="d3e43-113">`Nothing`은 가장 바깥쪽 컨텍스트를 지정하며 이는 일반적으로 보고서 데이터 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-113">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="d3e43-114">반환 형식</span><span class="sxs-lookup"><span data-stu-id="d3e43-114">Return Type</span></span>  
 <span data-ttu-id="d3e43-115">반환 형식은 *function* 매개 변수에 지정된 집계 함수에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-115">Determined by the aggregate function that is specified in the *function* parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3e43-116">설명</span><span class="sxs-lookup"><span data-stu-id="d3e43-116">Remarks</span></span>  
 <span data-ttu-id="d3e43-117">`RunningValue` 값은 범위의 각 새로운 인스턴스에 대해 0으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-117">The value for `RunningValue` resets to 0 for each new instance of the scope.</span></span> <span data-ttu-id="d3e43-118">그룹이 지정되어 있는 경우 그룹 식이 변경되면 실행 값이 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-118">If a group is specified, the running value is reset when the group expression changes.</span></span> <span data-ttu-id="d3e43-119">데이터 영역이 지정되어 있는 경우 데이터 영역의 새 인스턴스 각각에 대해 실행 값이 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-119">If a data region is specified, the running value is reset for each new instance of the data region.</span></span> <span data-ttu-id="d3e43-120">데이터 세트가 지정되어 있으면 전체 데이터 세트에서 실행 값이 다시 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-120">If a dataset is specified, the running value is not reset throughout the entire dataset.</span></span>  
  
 <span data-ttu-id="d3e43-121">`RunningValue`는 필터 또는 정렬 식에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-121">`RunningValue` cannot be used in a filter or sort expression.</span></span>  
  
 <span data-ttu-id="d3e43-122">실행 값이 계산되는 데이터 집합의 데이터 형식은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-122">The set of data for which the running value is calculated must have the same data type.</span></span> <span data-ttu-id="d3e43-123">여러 숫자 데이터 형식이 포함된 데이터를 동일한 데이터 형식으로 변환하려면 `CInt`, `CDbl` 또는 `CDec` 같은 변환 함수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-123">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="d3e43-124">자세한 내용은 [형식 변환 함수](https://go.microsoft.com/fwlink/?LinkId=96142)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-124">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="d3e43-125">*Scope* 는 식이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-125">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="d3e43-126">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-126">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="d3e43-127">중첩 집계의 범위는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-127">Scope for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="d3e43-128">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-128">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="d3e43-129">중첩 집계의 범위는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-129">Scope for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="d3e43-130">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="d3e43-130">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="d3e43-131">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-131">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="d3e43-132">행 개수의 실행 값을 계산하려면 `RowNumber`를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-132">To calculate the running value of the number of rows, use `RowNumber`.</span></span> <span data-ttu-id="d3e43-133">자세한 내용은 [RowNumber 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-rownumber-function.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-133">For more information, see [RowNumber Function &#40;Report Builder and SSRS&#41;](report-builder-functions-rownumber-function.md).</span></span>  
  
 <span data-ttu-id="d3e43-134">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-134">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="d3e43-135">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3e43-135">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d3e43-136">예</span><span class="sxs-lookup"><span data-stu-id="d3e43-136">Examples</span></span>  
 <span data-ttu-id="d3e43-137">다음 코드 예에서는 가장 바깥쪽 범위인 데이터 세트에서 `Cost`라는 필드의 실행 합계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-137">The following code example provides a running sum of the field named `Cost` in the outermost scope, which is the dataset.</span></span>  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 <span data-ttu-id="d3e43-138">다음 코드 예에서는 `Score` 데이터 세트에서 `DataSet1`라는 필드의 실행 합계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-138">The following code example provides a running sum of the field named `Score` in the dataset named `DataSet1`.</span></span>  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 <span data-ttu-id="d3e43-139">다음 코드 예에서는 가장 바깥쪽 범위에서 `Traffic Charges` 라는 필드의 실행 합계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3e43-139">The following code example provides a running sum of the field named `Traffic Charges` in the outermost scope.</span></span>  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3e43-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3e43-140">See Also</span></span>  
 <span data-ttu-id="d3e43-141">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d3e43-141">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d3e43-142">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d3e43-142">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d3e43-143">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d3e43-143">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d3e43-144">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e43-144">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
