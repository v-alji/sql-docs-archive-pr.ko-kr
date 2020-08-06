---
title: Union 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c80926be53254ec512b2189c4b67e8cd5885733f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650687"
---
# <a name="union-function-report-builder-and-ssrs"></a><span data-ttu-id="c87e1-102">Union 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c87e1-102">Union Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c87e1-103">식으로 지정되어 정해진 범위에서 계산되는 Null이 아닌 모든 숫자 값의 합집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-103">Returns the union of all the non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="c87e1-104">구문</span><span class="sxs-lookup"><span data-stu-id="c87e1-104">Syntax</span></span>  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c87e1-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c87e1-105">Parameters</span></span>  
 <span data-ttu-id="c87e1-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="c87e1-106">*expression*</span></span>  
 <span data-ttu-id="c87e1-107">(`SqlGeometry` 또는 `SqlGeography`) 집계를 수행할 식입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-107">(`SqlGeometry` or `SqlGeography`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="c87e1-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="c87e1-108">*scope*</span></span>  
 <span data-ttu-id="c87e1-109">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-109">(`String`) Optional.</span></span> <span data-ttu-id="c87e1-110">집계 함수를 적용할 보고서 항목을 포함하는 데이터 세트, 그룹 또는 데이터 영역의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="c87e1-111">*scope* 를 지정하지 않은 경우 현재 범위가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="c87e1-112">*재귀*</span><span class="sxs-lookup"><span data-stu-id="c87e1-112">*recursive*</span></span>  
 <span data-ttu-id="c87e1-113">(**열거 형식**) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="c87e1-114">`Simple`(기본값) 또는 `RdlRecursive`로,</span><span class="sxs-lookup"><span data-stu-id="c87e1-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="c87e1-115">집계를 재귀적으로 수행할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return"></a><span data-ttu-id="c87e1-116">반환 값</span><span class="sxs-lookup"><span data-stu-id="c87e1-116">Return</span></span>  
 <span data-ttu-id="c87e1-117">식 유형에 따라 `SqlGeometry` 또는 `SqlGeography` 공간 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-117">Returns a spatial object, either `SqlGeometry` or `SqlGeography`, based on the expression type.</span></span> <span data-ttu-id="c87e1-118">및 공간 데이터 형식에 대 한 자세한 내용은 `SqlGeometry` `SqlGeography` [공간 데이터 형식 개요](../../relational-databases/spatial/spatial-data-types-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e1-118">For more information about `SqlGeometry` and `SqlGeography` spatial data types, see [Spatial Data Types Overview](../../relational-databases/spatial/spatial-data-types-overview.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c87e1-119">설명</span><span class="sxs-lookup"><span data-stu-id="c87e1-119">Remarks</span></span>  
 <span data-ttu-id="c87e1-120">식에 지정한 데이터 집합은 동일한 데이터 형식으로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-120">The set of data specified in the expression must have the same data type.</span></span>  
  
 <span data-ttu-id="c87e1-121">*scope* 의 값은 문자열 상수여야 하고 식일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-121">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="c87e1-122">외부 집계나 다른 집계를 지정하지 않는 집계의 경우 *scope* 는 현재 범위나 포함하는 범위를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-122">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="c87e1-123">데이터 세트 범위는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-123">Dataset scopes are not supported.</span></span> <span data-ttu-id="c87e1-124">집계의 집계의 경우 중첩 집계는 자식 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="c87e1-125">*Expression* 에는 다음 예외와 조건이 있는 중첩 집계 함수에 대한 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="c87e1-126">중첩 집계의*Scope* 는 외부 집계의 범위와 동일하거나 외부 집계의 범위에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="c87e1-127">식에 있는 모든 고유 범위의 경우 한 범위는 다른 모든 범위에 대한 자식 관계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="c87e1-128">중첩 집계의 *Scope*는 데이터 세트의 이름일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="c87e1-129">*식은* `First` , `Last` , `Previous` 또는 함수를 포함 하지 않아야 합니다 `RunningValue` .</span><span class="sxs-lookup"><span data-stu-id="c87e1-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="c87e1-130">*Expression* 에는 *recursive*를 지정하는 중첩 집계가 포함되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="c87e1-131">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e1-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="c87e1-132">재귀 집계에 대한 자세한 내용은 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e1-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c87e1-133">예제</span><span class="sxs-lookup"><span data-stu-id="c87e1-133">Example</span></span>  
 <span data-ttu-id="c87e1-134">다음 표에서는 `SqlGeometry` 식 예와 `Union` 결과 식을 보여 줍니다. 여기서 공간 데이터는 WKT(Well Known Text) 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e1-134">The following table shows examples of `SqlGeometry` expressions and `Union` result expression, shown in WKT (Well Known Text) format for spatial data.</span></span>  
  
|<span data-ttu-id="c87e1-135">공간 데이터가 포함된 필드</span><span class="sxs-lookup"><span data-stu-id="c87e1-135">Field with spatial data</span></span>|<span data-ttu-id="c87e1-136">예제</span><span class="sxs-lookup"><span data-stu-id="c87e1-136">Example</span></span>|<span data-ttu-id="c87e1-137">Union 결과</span><span class="sxs-lookup"><span data-stu-id="c87e1-137">Union result</span></span>|  
|-----------------------------|-------------|------------------|  
|<span data-ttu-id="c87e1-138">[PointLocation]</span><span class="sxs-lookup"><span data-stu-id="c87e1-138">[PointLocation]</span></span>|<span data-ttu-id="c87e1-139">POINT(1 2)</span><span class="sxs-lookup"><span data-stu-id="c87e1-139">POINT(1 2)</span></span><br /><br /> <span data-ttu-id="c87e1-140">POINT(3 4)</span><span class="sxs-lookup"><span data-stu-id="c87e1-140">POINT(3 4)</span></span>|<span data-ttu-id="c87e1-141">MULTIPOINT((1 2), (3 4))</span><span class="sxs-lookup"><span data-stu-id="c87e1-141">MULTIPOINT((1 2), (3 4))</span></span>|  
|<span data-ttu-id="c87e1-142">[PathDefinition]</span><span class="sxs-lookup"><span data-stu-id="c87e1-142">[PathDefinition]</span></span>|<span data-ttu-id="c87e1-143">LINESTRING(1 2, 3 4)</span><span class="sxs-lookup"><span data-stu-id="c87e1-143">LINESTRING(1 2, 3 4)</span></span><br /><br /> <span data-ttu-id="c87e1-144">LINESTRING(5 6, 7 8)</span><span class="sxs-lookup"><span data-stu-id="c87e1-144">LINESTRING(5 6, 7 8)</span></span>|<span data-ttu-id="c87e1-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span><span class="sxs-lookup"><span data-stu-id="c87e1-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span></span>|  
|<span data-ttu-id="c87e1-146">[PolygonDefinition]</span><span class="sxs-lookup"><span data-stu-id="c87e1-146">[PolygonDefinition]</span></span>|<span data-ttu-id="c87e1-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span><span class="sxs-lookup"><span data-stu-id="c87e1-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span></span><br /><br /> <span data-ttu-id="c87e1-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span><span class="sxs-lookup"><span data-stu-id="c87e1-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span></span>|<span data-ttu-id="c87e1-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span><span class="sxs-lookup"><span data-stu-id="c87e1-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span></span>|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a><span data-ttu-id="c87e1-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c87e1-150">See Also</span></span>  
 <span data-ttu-id="c87e1-151">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c87e1-151">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c87e1-152">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c87e1-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c87e1-153">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c87e1-153">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c87e1-154">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c87e1-154">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
