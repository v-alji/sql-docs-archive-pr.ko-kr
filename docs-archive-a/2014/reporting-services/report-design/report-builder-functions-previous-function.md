---
title: Previous 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3891deec3f152cdf46da77a7f2d11d38387c5c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650700"
---
# <a name="previous-function-report-builder-and-ssrs"></a><span data-ttu-id="31899-102">Previous 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="31899-102">Previous Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="31899-103">지정된 범위 내에서 항목의 이전 인스턴스에 대한 지정된 집계 값 또는 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-103">Returns the value or the specified aggregate value for the previous instance of an item within the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="31899-104">구문</span><span class="sxs-lookup"><span data-stu-id="31899-104">Syntax</span></span>  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31899-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="31899-105">Parameters</span></span>  
 <span data-ttu-id="31899-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="31899-106">*expression*</span></span>  
 <span data-ttu-id="31899-107">(`Variant` 또는 `Binary`) 데이터를 식별하거나 이전 값을 검색하기 위한 식입니다(예: `Fields!Fieldname.Value` 또는 `Sum(Fields!Fieldname.Value)`).</span><span class="sxs-lookup"><span data-stu-id="31899-107">(`Variant` or `Binary`) The expression to use to identify the data and for which to retrieve the previous value, for example, `Fields!Fieldname.Value` or `Sum(Fields!Fieldname.Value)`.</span></span>  
  
 <span data-ttu-id="31899-108">*범위*</span><span class="sxs-lookup"><span data-stu-id="31899-108">*scope*</span></span>  
 <span data-ttu-id="31899-109">(`String`) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="31899-109">(`String`) Optional.</span></span> <span data-ttu-id="31899-110">`Nothing` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] *식*으로 지정 된 이전 값을 검색할 범위를 지정 하는 그룹 또는 데이터 영역의 이름 이거나 null (의 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="31899-110">The name of a group or data region, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the scope from which to retrieve the previous value specified by *expression*.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="31899-111">반환 형식</span><span class="sxs-lookup"><span data-stu-id="31899-111">Return Type</span></span>  
 <span data-ttu-id="31899-112">`Variant` 또는 `Binary`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-112">Returns a `Variant` or `Binary`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31899-113">설명</span><span class="sxs-lookup"><span data-stu-id="31899-113">Remarks</span></span>  
 <span data-ttu-id="31899-114">`Previous` 함수는 모든 정렬 및 필터링이 적용된 다음 지정된 범위에서 계산된 식의 이전 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-114">The `Previous` function returns the previous value for the expression evaluated in the specified scope after all sorting and filtering have been applied.</span></span>  
  
 <span data-ttu-id="31899-115">*식* 에 집계가 포함 되지 않은 경우이 `Previous` 함수는 기본적으로 보고서 항목의 현재 범위를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-115">If *expression* does not contain an aggregate, the `Previous` function defaults to the current scope for the report item.</span></span>  
  
 <span data-ttu-id="31899-116">세부 정보 그룹에서 `Previous`를 사용하여 세부 행의 이전 인스턴스에 필드 참조 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-116">In a details group, use `Previous` to specify the value of a field reference in the previous instance of the detail row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31899-117">`Previous`함수는 세부 정보 그룹의 필드 참조만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-117">The `Previous` function only supports field references in the details group.</span></span> <span data-ttu-id="31899-118">예를 들어 세부 정보 그룹의 입력란에서 `=Previous(Fields!Quantity.Value)` 는 이전 행의 `Quantity` 필드에 대한 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-118">For example, in a text box in the details group, `=Previous(Fields!Quantity.Value)` returns the data for the field `Quantity` from the previous row.</span></span> <span data-ttu-id="31899-119">첫 번째 행에서 이 식은 Null([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 경우 `Nothing`)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-119">In the first row, this expression returns a null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  
  
 <span data-ttu-id="31899-120">*식* 에 기본 범위를 사용 하는 집계 함수가 포함 된 경우는 `Previous` 집계 함수 호출에 지정 된 범위의 이전 인스턴스 내에서 데이터를 집계 합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-120">If *expression* contains an aggregate function that uses a default scope, `Previous` aggregates the data within the previous instance of the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="31899-121">*식* 에 기본값 이외의 범위를 지정 하는 집계 함수가 포함 된 경우 함수의 *범위* 매개 변수는 `Previous` 집계 함수 호출에 지정 된 범위에 대해 포함 하는 범위 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-121">If *expression* contains an aggregate function that specifies a scope other than the default, the *scope* parameter for the `Previous` function must be a containing scope for the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="31899-122">`Level`, 및 함수 `InScope` 는 `Aggregate` `Previous` *expression*매개 변수에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31899-122">The functions `Level`, `InScope`, `Aggregate` and `Previous` cannot be used in the *expression*parameter.</span></span> <span data-ttu-id="31899-123">집계 함수에 대해 *recursive* 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31899-123">Specifying the *recursive* parameter for any aggregate function is not supported.</span></span>  
  
 <span data-ttu-id="31899-124">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31899-124">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="31899-125">예</span><span class="sxs-lookup"><span data-stu-id="31899-125">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="31899-126">Description</span><span class="sxs-lookup"><span data-stu-id="31899-126">Description</span></span>  
 <span data-ttu-id="31899-127">다음 코드 예는 데이터 영역의 기본 데이터 행에 배치될 경우 이전 행의 `LineTotal` 필드에 대한 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-127">The following code example, when placed in the default data row of a data region, provides the value for the field `LineTotal` in the previous row.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31899-128">코드</span><span class="sxs-lookup"><span data-stu-id="31899-128">Code</span></span>  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a><span data-ttu-id="31899-129">Description</span><span class="sxs-lookup"><span data-stu-id="31899-129">Description</span></span>  
 <span data-ttu-id="31899-130">다음 예에서는 월 중 특정 일에 대한 판매 합계를 계산하고 이전 연도의 해당 월 및 일에 대한 이전 값을 계산하는 식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31899-130">The following example shows an expression that calculates the sum of sales on a specific day of the month and the previous value for that day of the month in a previous year.</span></span> <span data-ttu-id="31899-131">`GroupbyDay`자식 그룹에 속하는 행의 셀에 식이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="31899-131">The expression is added to a cell in a row that belongs to the child group `GroupbyDay`.</span></span> <span data-ttu-id="31899-132">부모 그룹은 `GroupbyMonth`이며 이 그룹의 부모 그룹은 `GroupbyYear`입니다.</span><span class="sxs-lookup"><span data-stu-id="31899-132">Its parent group is `GroupbyMonth`, which has a parent group `GroupbyYear`.</span></span> <span data-ttu-id="31899-133">식은 GroupbyDay(기본 범위)에 대한 결과와 `GroupbyYear` ( `GroupbyMonth`부모 그룹의 부모)에 대한 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="31899-133">The expression displays the results for GroupbyDay (the default scope) and then for `GroupbyYear` (the parent of the parent group `GroupbyMonth`).</span></span>  
  
 <span data-ttu-id="31899-134">예를 들어 `Year`라는 부모 그룹을 가진 데이터 영역의 경우 자식 그룹의 이름은 `Month`이고 이 그룹의 자식 그룹 이름은 `Day` 가 됩니다(3수준 중첩).</span><span class="sxs-lookup"><span data-stu-id="31899-134">For example, for a data region with a parent group named `Year`, its child group named `Month`, and its child group named `Day` (3 nested levels).</span></span> <span data-ttu-id="31899-135">`=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` 그룹과 관련된 행에서 `Day` 식을 사용하면 이전 연도의 동일 월 및 일에 대한 판매 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="31899-135">The expression `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in a row associated with the group `Day` returns the sales value for the same day and month for the previous year.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31899-136">코드</span><span class="sxs-lookup"><span data-stu-id="31899-136">Code</span></span>  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a><span data-ttu-id="31899-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31899-137">See Also</span></span>  
 <span data-ttu-id="31899-138">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31899-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31899-139">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31899-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31899-140">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31899-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="31899-141">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="31899-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
