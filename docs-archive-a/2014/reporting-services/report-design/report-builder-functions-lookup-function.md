---
title: Lookup 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 053fefff51e4b4e338e262664bd7570280c92540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650706"
---
# <a name="lookup-function-report-builder-and-ssrs"></a><span data-ttu-id="3f090-102">Lookup 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3f090-102">Lookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3f090-103">이름/값 쌍을 포함하는 데이터 세트에서 지정된 이름과 일치하는 첫 번째 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-103">Returns the first matching value for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="3f090-104">구문</span><span class="sxs-lookup"><span data-stu-id="3f090-104">Syntax</span></span>  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f090-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f090-105">Parameters</span></span>  
 <span data-ttu-id="3f090-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="3f090-106">*source_expression*</span></span>  
 <span data-ttu-id="3f090-107">(`Variant`) 현재 범위에서 평가되고, 조회할 키 또는 이름을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="3f090-108">`=Fields!ProdID.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-108">For example, `=Fields!ProdID.Value`.</span></span>  
  
 <span data-ttu-id="3f090-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="3f090-109">*destination_expression*</span></span>  
 <span data-ttu-id="3f090-110">(`Variant`) 데이터 세트의 각 행에 대해 평가되고, 일치시킬 키 또는 이름을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="3f090-111">`=Fields!ProductID.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-111">For example, `=Fields!ProductID.Value`.</span></span>  
  
 <span data-ttu-id="3f090-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="3f090-112">*result_expression*</span></span>  
 <span data-ttu-id="3f090-113">( `Variant` ) *Source_expression*  =  데이터 집합의 행에 대해 평가 되는 식입니다. *destination_expression*이 고, 검색할 값을 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="3f090-114">`=Fields!ProductName.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-114">For example, `=Fields!ProductName.Value`.</span></span>  
  
 <span data-ttu-id="3f090-115">*데이터 세트*</span><span class="sxs-lookup"><span data-stu-id="3f090-115">*dataset*</span></span>  
 <span data-ttu-id="3f090-116">보고서의 데이터 세트 이름을 지정하는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="3f090-117">예를 들면 "Products"입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-117">For example, "Products".</span></span>  
  
## <a name="return"></a><span data-ttu-id="3f090-118">반환 값</span><span class="sxs-lookup"><span data-stu-id="3f090-118">Return</span></span>  
 <span data-ttu-id="3f090-119">`Variant`를 반환하거나, 일치하는 항목이 없으면 `Nothing`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-119">Returns a `Variant`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f090-120">설명</span><span class="sxs-lookup"><span data-stu-id="3f090-120">Remarks</span></span>  
 <span data-ttu-id="3f090-121">`Lookup`을 사용하여 일 대 일 관계의 이름/값 쌍에 대한 지정된 데이터 세트에서 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-121">Use `Lookup` to retrieve the value from the specified dataset for a name/value pair where there is a 1-to-1 relationship.</span></span> <span data-ttu-id="3f090-122">예를 들어 테이블에 있는 ID 필드의 경우 `Lookup`을 사용하여 데이터 영역에 바인딩되지 않은 데이터 세트에서 해당하는 이름 필드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-122">For example, for an ID field in a table, you can use `Lookup` to retrieve the corresponding Name field from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="3f090-123">`Lookup`은 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-123">`Lookup` does the following:</span></span>  
  
-   <span data-ttu-id="3f090-124">현재 범위에서 원본 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="3f090-125">지정된 데이터 세트의 데이터 정렬을 기반으로 필터가 적용된 후 지정된 데이터 세트의 각 행에 대해 대상 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="3f090-126">원본 식과 대상 식의 첫 번째 일치 항목이 발견되면 데이터 세트의 해당 행에 대해 결과 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-126">On the first match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="3f090-127">결과 식 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-127">Returns the result expression value.</span></span>  
  
 <span data-ttu-id="3f090-128">일 대 다 관계가 있는 경우 단일 이름 또는 키 필드에 대해 여러 값을 검색하려면 [LookupSet 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookupset-function.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-128">To retrieve multiple values for a single name or key field where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span> <span data-ttu-id="3f090-129">`Lookup`값 집합에 대해를 호출 하려면 [Multilookup 함수 &#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookup-function.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span>  
  
 <span data-ttu-id="3f090-130">다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="3f090-131">`Lookup`은 모든 필터 식이 적용된 후 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-131">`Lookup` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="3f090-132">조회 수준이 하나만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="3f090-133">원본, 대상 또는 결과 식에는 조회 함수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="3f090-134">원본 식과 대상 식의 데이터 형식이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-134">Source and destination expressions must evaluate to the same data type.</span></span> <span data-ttu-id="3f090-135">반환 형식은 평가된 결과 식의 데이터 형식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-135">The return type is the same as the data type of the evaluated result expression.</span></span>  
  
-   <span data-ttu-id="3f090-136">원본, 대상 및 결과 식에는 보고서 또는 그룹 변수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-136">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="3f090-137">`Lookup`은 다음 보고서 항목에 대한 식으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-137">`Lookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="3f090-138">데이터 원본에 대한 동적 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="3f090-138">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="3f090-139">데이터 세트의 계산된 필드.</span><span class="sxs-lookup"><span data-stu-id="3f090-139">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="3f090-140">데이터 세트의 쿼리 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="3f090-140">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="3f090-141">데이터 세트의 필터.</span><span class="sxs-lookup"><span data-stu-id="3f090-141">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="3f090-142">보고서 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f090-142">Report parameters.</span></span>  
  
    -   <span data-ttu-id="3f090-143">Report.Language 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-143">The Report.Language property.</span></span>  
  
 <span data-ttu-id="3f090-144">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f090-144">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f090-145">예제</span><span class="sxs-lookup"><span data-stu-id="3f090-145">Example</span></span>  
 <span data-ttu-id="3f090-146">다음 예에서는 제품 식별자 ProductID에 대한 필드를 포함하는 데이터 세트에 테이블이 바인딩되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-146">In the following example, assume that a table is bound to a dataset that includes a field for the product identifier ProductID.</span></span> <span data-ttu-id="3f090-147">"Product"라는 별도의 데이터 세트에는 해당하는 제품 식별자 ID와 제품 이름 Name이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-147">A separate dataset called "Product" contains the corresponding product identifier ID and the product name Name.</span></span>  
  
 <span data-ttu-id="3f090-148">다음 식에서 `Lookup`은 ProductID 값을 &quot;Product&quot; 데이터 세트의 각 행에 있는 ID와 비교한 다음, 일치하는 항목이 있으면 해당 행의 Name 필드 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3f090-148">In the following expression, `Lookup` compares the value of ProductID to ID in each row of the dataset called "Product" and, when a match is found, returns the value of the Name field for that row.</span></span>  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f090-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f090-149">See Also</span></span>  
 <span data-ttu-id="3f090-150">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f090-150">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3f090-151">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f090-151">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3f090-152">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3f090-152">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3f090-153">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3f090-153">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
