---
title: LookupSet 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edc7a17f2aa3813e8aa73e538594b5df3aeabc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650709"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a><span data-ttu-id="9eb77-102">LookupSet 함수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9eb77-102">LookupSet Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9eb77-103">이름/값 쌍을 포함하는 데이터 세트에서 지정된 이름과 일치하는 값 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-103">Returns the set of matching values for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="9eb77-104">구문</span><span class="sxs-lookup"><span data-stu-id="9eb77-104">Syntax</span></span>  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9eb77-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9eb77-105">Parameters</span></span>  
 <span data-ttu-id="9eb77-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="9eb77-106">*source_expression*</span></span>  
 <span data-ttu-id="9eb77-107">(`Variant`) 현재 범위에서 평가되고, 조회할 키 또는 이름을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="9eb77-108">`=Fields!ID.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-108">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="9eb77-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="9eb77-109">*destination_expression*</span></span>  
 <span data-ttu-id="9eb77-110">(`Variant`) 데이터 세트의 각 행에 대해 평가되고, 일치시킬 키 또는 이름을 지정하는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="9eb77-111">`=Fields!CustomerID.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-111">For example, `=Fields!CustomerID.Value`.</span></span>  
  
 <span data-ttu-id="9eb77-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="9eb77-112">*result_expression*</span></span>  
 <span data-ttu-id="9eb77-113">( `Variant` ) *Source_expression*  =  데이터 집합의 행에 대해 평가 되는 식입니다. *destination_expression*이 고, 검색할 값을 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="9eb77-114">`=Fields!PhoneNumber.Value`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-114">For example, `=Fields!PhoneNumber.Value`.</span></span>  
  
 <span data-ttu-id="9eb77-115">*데이터 세트*</span><span class="sxs-lookup"><span data-stu-id="9eb77-115">*dataset*</span></span>  
 <span data-ttu-id="9eb77-116">보고서의 데이터 세트 이름을 지정하는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="9eb77-117">예를 들면 "ContactInformation"입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-117">For example, "ContactInformation".</span></span>  
  
## <a name="return"></a><span data-ttu-id="9eb77-118">반환 값</span><span class="sxs-lookup"><span data-stu-id="9eb77-118">Return</span></span>  
 <span data-ttu-id="9eb77-119">`VariantArray`를 반환하거나, 일치하는 항목이 없으면 `Nothing`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eb77-120">설명</span><span class="sxs-lookup"><span data-stu-id="9eb77-120">Remarks</span></span>  
 <span data-ttu-id="9eb77-121">`LookupSet`을 사용하여 일 대 다 관계의 이름/값 쌍에 대한 지정된 데이터 세트에서 값 집합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-121">Use `LookupSet` to retrieve a set of values from the specified dataset for a name/value pair where there is a 1-to-many relationship.</span></span> <span data-ttu-id="9eb77-122">예를 들어 테이블에 있는 고객 식별자의 경우 `LookupSet`을 사용하여 데이터 영역에 바인딩되지 않은 데이터 세트에서 해당 고객에 대해 연결된 전화 번호를 모두 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-122">For example, for a customer identifier in a table, you can use `LookupSet` to retrieve all the associated phone numbers for that customer from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="9eb77-123">`LookupSet`은 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-123">`LookupSet` does the following:</span></span>  
  
-   <span data-ttu-id="9eb77-124">현재 범위에서 원본 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="9eb77-125">지정된 데이터 세트의 데이터 정렬을 기반으로 필터가 적용된 후 지정된 데이터 세트의 각 행에 대해 대상 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="9eb77-126">원본 식과 대상 식의 일치 항목을 찾을 때마다 데이터 세트의 해당 행에 대해 결과 식을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-126">For each match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="9eb77-127">결과 식 값의 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-127">Returns the set of result expression values.</span></span>  
  
 <span data-ttu-id="9eb77-128">일 대 일 관계의 이름/값 쌍을 포함하는 데이터 세트에서 지정된 이름에 대한 단일 값을 검색하려면 [Lookup 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-lookup-function.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-128">To retrieve a single value from a dataset with name/value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="9eb77-129">`Lookup`값 집합에 대해를 호출 하려면 [Multilookup 함수 &#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-multilookup-function.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-multilookup-function.md).</span></span>  
  
 <span data-ttu-id="9eb77-130">다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="9eb77-131">`LookupSet`은 모든 필터 식이 적용된 후 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-131">`LookupSet` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="9eb77-132">조회 수준이 하나만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="9eb77-133">원본, 대상 또는 결과 식에는 조회 함수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="9eb77-134">원본 식과 대상 식의 데이터 형식이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="9eb77-135">원본, 대상 및 결과 식에는 보고서 또는 그룹 변수에 대한 참조가 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="9eb77-136">`LookupSet`은 다음 보고서 항목에 대한 식으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-136">`LookupSet` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="9eb77-137">데이터 원본에 대한 동적 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="9eb77-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="9eb77-138">데이터 세트의 계산된 필드.</span><span class="sxs-lookup"><span data-stu-id="9eb77-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="9eb77-139">데이터 세트의 쿼리 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="9eb77-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="9eb77-140">데이터 세트의 필터.</span><span class="sxs-lookup"><span data-stu-id="9eb77-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="9eb77-141">보고서 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9eb77-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="9eb77-142">Report.Language 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="9eb77-143">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9eb77-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb77-144">예제</span><span class="sxs-lookup"><span data-stu-id="9eb77-144">Example</span></span>  
 <span data-ttu-id="9eb77-145">다음 예에서는 영업 지역 식별자 TerritoryGroupID를 포함하는 데이터 세트에 테이블이 바인딩되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-145">In the following example, assume the table is bound to a dataset that includes a sales territory identifier TerritoryGroupID.</span></span> <span data-ttu-id="9eb77-146">"Stores"라는 별도의 데이터 세트에는 지역의 모든 매장 목록과 지역 식별자 ID 및 매장 이름 StoreName이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-146">A separate dataset called "Stores" contains the list of all stores in a territory and includes the territory identifier ID and the name of the store StoreName.</span></span>  
  
 <span data-ttu-id="9eb77-147">다음 식에서 `LookupSet`은 TerritoryGroupID 값을 &quot;Stores&quot; 데이터 세트에 있는 각 행의 ID와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-147">In the following expression, `LookupSet` compares the value TerritoryGroupID to ID for each row in the dataset called "Stores".</span></span> <span data-ttu-id="9eb77-148">일치 항목을 찾을 때마다 해당 행에 대한 StoreName 필드의 값이 결과 집합에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-148">For each match, the value of the StoreName field for that row is added to the result set.</span></span>  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a><span data-ttu-id="9eb77-149">예제</span><span class="sxs-lookup"><span data-stu-id="9eb77-149">Example</span></span>  
 <span data-ttu-id="9eb77-150">`LookupSet`은 개체 컬렉션을 반환하므로 결과 식을 입력란에 직접 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-150">Because `LookupSet` returns a collection of objects, you cannot display the result expression directly in a text box.</span></span> <span data-ttu-id="9eb77-151">컬렉션에 있는 각 개체의 값을 문자열로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-151">You can concatenate the value of each object in the collection as a string.</span></span>  
  
 <span data-ttu-id="9eb77-152">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수 `Join`을 사용하여 개체 집합에서 구분된 문자열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-152">Use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function `Join` create a delimited string from a set of objects.</span></span> <span data-ttu-id="9eb77-153">개체를 한 줄로 결합하려면 쉼표를 구분 기호로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-153">Use a comma as a separator to combine the objects in a single line.</span></span> <span data-ttu-id="9eb77-154">일부 렌더러에서는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 줄 바꿈(`vbCrLF`)을 구분 기호로 사용하여 각 값을 새 줄에 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-154">In some renderers, you might use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] line feed (`vbCrLF`) as a separator to list each value on a new line.</span></span>  
  
 <span data-ttu-id="9eb77-155">다음 식을 입력란의 Value 속성으로 사용 하는 경우를 사용 `Join` 하 여 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-155">The following expression, when it is used as the Value property for a text box, uses `Join` to create a list.</span></span>  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a><span data-ttu-id="9eb77-156">예제</span><span class="sxs-lookup"><span data-stu-id="9eb77-156">Example</span></span>  
 <span data-ttu-id="9eb77-157">몇 번만 렌더링되는 입력란의 경우 입력란에 값을 표시하는 HTML을 생성하기 위해 사용자 지정 코드를 추가하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-157">For text boxes that only render a few times, you might choose to add custom code to generate HTML to display values in a text box.</span></span> <span data-ttu-id="9eb77-158">입력란에 HTML을 표시하려면 추가 처리 작업이 필요하므로 수천 번 렌더링되는 입력란의 경우에는 이러한 선택이 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-158">HTML in a text box requires extra processing, so this would not be a good choice for a text box that is rendered thousands of times.</span></span>  
  
 <span data-ttu-id="9eb77-159">다음 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수를 보고서 정의의 Code 블록에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-159">Copy the following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to a Code block in a report definition.</span></span> <span data-ttu-id="9eb77-160">**MakeList** 는 *result_expression* 에서 반환되는 개체 배열을 사용하고 HTML 태그를 사용하여 정렬되지 않은 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-160">**MakeList** takes the object array that is returned in *result_expression* and builds an unordered list by using HTML tags.</span></span> <span data-ttu-id="9eb77-161">**Length** 는 개체 배열의 항목 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-161">**Length** returns the number of items in the object array.</span></span>  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="9eb77-162">예제</span><span class="sxs-lookup"><span data-stu-id="9eb77-162">Example</span></span>  
 <span data-ttu-id="9eb77-163">HTML을 생성하려면 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-163">To generate the HTML, you must call the function.</span></span> <span data-ttu-id="9eb77-164">다음 식을 입력란의 Value 속성에 붙여넣고 텍스트의 태그 형식을 HTML로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9eb77-164">Paste the following expression in the Value property for the text box and set the markup type for text to HTML.</span></span> <span data-ttu-id="9eb77-165">자세한 내용은 [보고서에 HTML 추가&#40;보고서 작성기 및 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9eb77-165">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eb77-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9eb77-166">See Also</span></span>  
 <span data-ttu-id="9eb77-167">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9eb77-167">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9eb77-168">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9eb77-168">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9eb77-169">[식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9eb77-169">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9eb77-170">합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9eb77-170">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
