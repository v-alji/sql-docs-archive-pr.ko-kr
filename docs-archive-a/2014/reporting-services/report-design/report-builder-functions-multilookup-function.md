---
title: Multilookup 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fec079e-33b3-4e4d-92b3-6b4d06a49a77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f2aff7a2a39e1a072cf4b05f0a04e12ced529af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650704"
---
# <a name="multilookup-function-report-builder-and-ssrs"></a><span data-ttu-id="6d840-102">Multilookup 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6d840-102">Multilookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6d840-103">이름/값 쌍을 포함하는 데이터 세트에서 지정된 이름 집합과 처음 일치하는 값 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-103">Returns the set of first-match values for the specified set of names from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="6d840-104">구문</span><span class="sxs-lookup"><span data-stu-id="6d840-104">Syntax</span></span>  
  
```  
  
Multilookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d840-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6d840-105">Parameters</span></span>  
 <span data-ttu-id="6d840-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="6d840-106">*source_expression*</span></span>  
 <span data-ttu-id="6d840-107">(`VariantArray`) 현재 범위에서 평가되고, 조회할 키 또는 이름의 집합을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-107">(`VariantArray`) An expression that is evaluated in the current scope and that specifies the set of names or keys to look up.</span></span> <span data-ttu-id="6d840-108">예를 들어 다중값 매개 변수의 경우 `=Parameters!IDs.value`입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-108">For example, for a multivalue parameter, `=Parameters!IDs.value`.</span></span>  
  
 <span data-ttu-id="6d840-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="6d840-109">*destination_expression*</span></span>  
 <span data-ttu-id="6d840-110">(`Variant`) 데이터 세트의 각 행에 대해 평가되고, 일치시킬 키 또는 이름을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="6d840-111">`=Fields!ID.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-111">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="6d840-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="6d840-112">*result_expression*</span></span>  
 <span data-ttu-id="6d840-113">( `Variant` ) *Source_expression*  =  데이터 집합의 행에 대해 평가 되는 식입니다. *destination_expression*이 고, 검색할 값을 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="6d840-114">`=Fields!Name.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-114">For example, `=Fields!Name.Value`.</span></span>  
  
 <span data-ttu-id="6d840-115">*데이터 세트*</span><span class="sxs-lookup"><span data-stu-id="6d840-115">*dataset*</span></span>  
 <span data-ttu-id="6d840-116">보고서의 데이터 세트 이름을 지정하는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="6d840-117">예를 들면 "Colors"입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-117">For example, "Colors".</span></span>  
  
## <a name="return"></a><span data-ttu-id="6d840-118">반환 값</span><span class="sxs-lookup"><span data-stu-id="6d840-118">Return</span></span>  
 <span data-ttu-id="6d840-119">`VariantArray`를 반환하거나, 일치하는 항목이 없으면 `Nothing`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d840-120">설명</span><span class="sxs-lookup"><span data-stu-id="6d840-120">Remarks</span></span>  
 <span data-ttu-id="6d840-121">`Multilookup`을 사용하여 일 대 일 관계가 있는 이름-값 쌍의 데이터 세트에서 값 집합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-121">Use `Multilookup` to retrieve a set of values from a dataset for name-value pairs where each pair has a 1-to-1 relationship.</span></span> <span data-ttu-id="6d840-122">`MultiLookup`은 이름 또는 키 집합에 대해 `Lookup`을 호출하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-122">`MultiLookup` is the equivalent of calling `Lookup` for a set of names or keys.</span></span> <span data-ttu-id="6d840-123">예를 들어 기본 키 식별자를 기반으로 하는 다중값 매개 변수의 경우 테이블의 입력란에 있는 식에 `Multilookup`을 사용하여 매개 변수 또는 테이블에 바인딩되지 않은 데이터 세트에서 연결된 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-123">For example, for a multivalue parameter that is based on primary key identifiers, you can use `Multilookup` in an expression in a text box in a table to retrieve associated values from a dataset that is not bound to the parameter or to the table.</span></span>  
  
 <span data-ttu-id="6d840-124">`Multilookup`은 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-124">`Multilookup` does the following:</span></span>  
  
-   <span data-ttu-id="6d840-125">현재 범위에서 원본 식을 평가하고 변형 개체의 배열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-125">Evaluates the source expression in the current scope and generates an array of variant objects.</span></span>  
  
-   <span data-ttu-id="6d840-126">배열의 각 개체에 대해 [Lookup 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookup-function.md)를 호출하고 결과를 반환 배열에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-126">For each object in the array, calls [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md) and adds the result to the return array.</span></span>  
  
-   <span data-ttu-id="6d840-127">결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-127">Returns the set of results.</span></span>  
  
 <span data-ttu-id="6d840-128">일 대 일 관계의 이름-값 쌍을 포함하는 데이터 세트에서 지정된 이름에 대한 단일 값을 검색하려면 [Lookup 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookup-function.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-128">To retrieve a single value from a dataset with name-value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="6d840-129">일 대 다 관계의 이름-값 쌍을 포함하는 데이터 세트에서 이름에 대한 여러 값을 검색하려면 [LookupSet 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookupset-function.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-129">To retrieve multiple values from a dataset with name-value pairs for a name where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span>  
  
 <span data-ttu-id="6d840-130">다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="6d840-131">`Multilookup`은 모든 필터 식이 적용된 후 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-131">`Multilookup` is evaluated after all filter expressions are applied</span></span>  
  
-   <span data-ttu-id="6d840-132">조회 수준이 하나만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-132">Only one level of look-up is supported.</span></span> <span data-ttu-id="6d840-133">원본, 대상 또는 결과 식에는 조회 함수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="6d840-134">원본 식과 대상 식의 데이터 형식이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="6d840-135">원본, 대상 및 결과 식에는 보고서 또는 그룹 변수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="6d840-136">`Multilookup`은 다음 보고서 항목에 대한 식으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-136">`Multilookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="6d840-137">데이터 원본에 대한 동적 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="6d840-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="6d840-138">데이터 세트의 계산된 필드.</span><span class="sxs-lookup"><span data-stu-id="6d840-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="6d840-139">데이터 세트의 쿼리 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="6d840-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="6d840-140">데이터 세트의 필터.</span><span class="sxs-lookup"><span data-stu-id="6d840-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="6d840-141">보고서 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6d840-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="6d840-142">Report.Language 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="6d840-143">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d840-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d840-144">예제</span><span class="sxs-lookup"><span data-stu-id="6d840-144">Example</span></span>  
 <span data-ttu-id="6d840-145">"Category"라는 데이터 세트에 CategoryList 필드가 포함되어 있다고 가정합니다. 이 필드는 쉼표로 구분된 범주 식별자 목록(예: "2, 4, 2, 1")을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-145">Assume a dataset called "Category" contains the field CategoryList, which is a field that contains a comma-separated list of category identifers, for example, "2, 4, 2, 1".</span></span>  
  
 <span data-ttu-id="6d840-146">CategoryNames 데이터 세트는 다음 표와 같이 범주 식별자와 범주 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-146">The dataset CategoryNames contains the category identifier and category name, as shown in the following table.</span></span>  
  
|<span data-ttu-id="6d840-147">ID</span><span class="sxs-lookup"><span data-stu-id="6d840-147">ID</span></span>|<span data-ttu-id="6d840-148">속성</span><span class="sxs-lookup"><span data-stu-id="6d840-148">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="6d840-149">1</span><span class="sxs-lookup"><span data-stu-id="6d840-149">1</span></span>|<span data-ttu-id="6d840-150">Accessories</span><span class="sxs-lookup"><span data-stu-id="6d840-150">Accessories</span></span>|  
|<span data-ttu-id="6d840-151">2</span><span class="sxs-lookup"><span data-stu-id="6d840-151">2</span></span>|<span data-ttu-id="6d840-152">Bikes</span><span class="sxs-lookup"><span data-stu-id="6d840-152">Bikes</span></span>|  
|<span data-ttu-id="6d840-153">3</span><span class="sxs-lookup"><span data-stu-id="6d840-153">3</span></span>|<span data-ttu-id="6d840-154">Clothing</span><span class="sxs-lookup"><span data-stu-id="6d840-154">Clothing</span></span>|  
|<span data-ttu-id="6d840-155">4</span><span class="sxs-lookup"><span data-stu-id="6d840-155">4</span></span>|<span data-ttu-id="6d840-156">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6d840-156">Components</span></span>|  
  
 <span data-ttu-id="6d840-157">식별자 목록에 해당하는 이름을 조회하려면 `Multilookup`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-157">To look up the names that correspond to the list of  identifiers, use `Multilookup`.</span></span> <span data-ttu-id="6d840-158">먼저 목록을 문자열 배열로 분할한 다음, `Multilookup`을 호출하여 범주 이름을 검색하고 결과를 문자열로 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-158">You must first split the list into a string array, call `Multilookup` to retrieve the category names, and concatenate the results into a string.</span></span>  
  
 <span data-ttu-id="6d840-159">다음 식을 Category 데이터 세트에 바인딩된 데이터 영역의 입력란에 넣으면 "Bikes, Components, Bikes, Accessories"가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-159">The following expression, when placed in a text box in a data region bound to the Category dataset, displays "Bikes, Components, Bikes, Accessories":</span></span>  
  
```  
=Join(MultiLookup(Split(Fields!CategoryList.Value,","),  
   Fields!CategoryID.Value,Fields!CategoryName.Value,"Category")),  
   ", ")  
```  
  
## <a name="example"></a><span data-ttu-id="6d840-160">예제</span><span class="sxs-lookup"><span data-stu-id="6d840-160">Example</span></span>  
 <span data-ttu-id="6d840-161">ProductColors 데이터 세트에 다음 표와 같이 색 식별자 필드 ColorID와 색 값 필드 Color가 포함되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-161">Assume a dataset ProductColors contains a color identifier field ColorID and a color value field Color, as shown in the following table.</span></span>  
  
|<span data-ttu-id="6d840-162">ColorID</span><span class="sxs-lookup"><span data-stu-id="6d840-162">ColorID</span></span>|<span data-ttu-id="6d840-163">색</span><span class="sxs-lookup"><span data-stu-id="6d840-163">Color</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="6d840-164">1</span><span class="sxs-lookup"><span data-stu-id="6d840-164">1</span></span>|<span data-ttu-id="6d840-165">빨강</span><span class="sxs-lookup"><span data-stu-id="6d840-165">Red</span></span>|  
|<span data-ttu-id="6d840-166">2</span><span class="sxs-lookup"><span data-stu-id="6d840-166">2</span></span>|<span data-ttu-id="6d840-167">파랑</span><span class="sxs-lookup"><span data-stu-id="6d840-167">Blue</span></span>|  
|<span data-ttu-id="6d840-168">3</span><span class="sxs-lookup"><span data-stu-id="6d840-168">3</span></span>|<span data-ttu-id="6d840-169">녹색</span><span class="sxs-lookup"><span data-stu-id="6d840-169">Green</span></span>|  
  
 <span data-ttu-id="6d840-170">다중값 매개 변수 *MyColors*가 사용 가능한 값에 대한 데이터 세트에 바인딩되어 있지 않다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-170">Assume the multivalue parameter *MyColors* is not bound to a dataset for its available values.</span></span> <span data-ttu-id="6d840-171">이 매개 변수의 기본값은 2와 3으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-171">The default values for the parameter are set to 2 and 3.</span></span> <span data-ttu-id="6d840-172">다음 식을 테이블의 입력란에 넣으면 매개 변수에 대해 선택된 여러 값을 쉼표로 구분된 목록으로 연결하고 "Blue, Green"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d840-172">The following expression, when placed in a text box in a table, concatenates the multiple selected values for the parameter into a comma-separated list and displays "Blue, Green".</span></span>  
  
```  
=Join(MultiLookup(Parameters!MyColors.Value,Fields!ColorID.Value,Fields!Color.Value,"ProductColors"),", ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d840-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d840-173">See Also</span></span>  
 <span data-ttu-id="6d840-174">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d840-174">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6d840-175">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d840-175">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6d840-176">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d840-176">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6d840-177">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6d840-177">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
