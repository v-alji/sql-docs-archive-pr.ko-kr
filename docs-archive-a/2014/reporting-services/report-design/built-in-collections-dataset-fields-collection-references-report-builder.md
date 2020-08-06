---
title: 데이터 세트 필드 컬렉션 참조(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 006c6bd3-d776-4c20-9092-32e40688ac49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e4140c35f8035e3ac8fae37aefb9d7f2afcaecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659845"
---
# <a name="dataset-fields-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="8edc1-102">데이터 세트 필드 컬렉션 참조(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8edc1-102">Dataset Fields Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8edc1-103">보고서의 각 데이터 세트에는 Fields 컬렉션이 하나씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-103">Each dataset in a report contains one Fields collection.</span></span> <span data-ttu-id="8edc1-104">Fields 컬렉션은 데이터 세트 쿼리에서 지정하는 필드와 사용자가 만드는 모든 추가 계산 필드의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-104">The Fields collection is the set of fields specified by the dataset query plus any additional calculated fields that you create.</span></span> <span data-ttu-id="8edc1-105">데이터 세트를 만든 후 필드 컬렉션이 **보고서 데이터** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-105">After you create a dataset, the field collection appears in the **Report Data** pane.</span></span>  
  
 <span data-ttu-id="8edc1-106">식의 단순 필드 참조가 디자인 화면에 단순 식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-106">A simple field reference in an expression displays on the design surface as a simple expression.</span></span> <span data-ttu-id="8edc1-107">예를 들어 보고서 데이터 창의 `Sales` 필드를 디자인 화면의 테이블 셀로 끌어 오면 `[Sales]` 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-107">For example, when you drag the field `Sales` from the Report Data pane to a table cell on the design surface, `[Sales]` is displayed.</span></span> <span data-ttu-id="8edc1-108">이는 Value 입력란 속성에 설정된 `=Fields!Sales.Value` 기본 식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-108">This represents the underlying expression `=Fields!Sales.Value` that is set on the text box Value property.</span></span> <span data-ttu-id="8edc1-109">보고서를 실행하면 보고서 처리기에서 이 식을 계산하고 테이블 셀의 입력란에 있는 데이터 원본의 실제 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-109">When the report runs, the report processor evaluates this expression and displays the actual data from the data source in the text box in the table cell.</span></span> <span data-ttu-id="8edc1-110">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) 및 [데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8edc1-110">For more, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) and [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-the-field-collection-for-a-dataset"></a><span data-ttu-id="8edc1-111">데이터 세트에 대한 필드 컬렉션 표시</span><span class="sxs-lookup"><span data-stu-id="8edc1-111">Displaying the Field Collection for a Dataset</span></span>  
 <span data-ttu-id="8edc1-112">필드 컬렉션에 대한 개별 값을 표시하려면 각 필드를 테이블 정보 행으로 끌고 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-112">To display the individual values for a field collection, drag each field to a table detail row and run the report.</span></span> <span data-ttu-id="8edc1-113">테이블 또는 목록 데이터 영역에 대한 정보 행의 참조가 데이터 세트의 각 행에 대한 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-113">References from the detail row of a table or list data region display a value for each row in the dataset.</span></span>  
  
 <span data-ttu-id="8edc1-114">필드의 요약된 값을 표시하려면 각 숫자 필드를 행렬의 데이터 영역으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-114">To display summarized values for a field, drag each numeric field to the data area of a matrix.</span></span> <span data-ttu-id="8edc1-115">합계 행에 대한 기본 집계 함수는 Sum입니다. 예를 들어 `=Sum(Fields!Sales.Value)`입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-115">The default aggregate function for the total row is Sum, for example, `=Sum(Fields!Sales.Value)`.</span></span> <span data-ttu-id="8edc1-116">다른 합계를 계산하기 위해 기본 함수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-116">You can change the default function in order to calculate different totals.</span></span> <span data-ttu-id="8edc1-117">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8edc1-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="8edc1-118">입력란의 필드 컬렉션에 대한 요약된 값을 데이터 영역의 일부가 아닌 디자인 화면에 직접 표시하려면 데이터 세트 이름을 집계 함수에 대한 범위로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-118">To display summarized values for a field collection in a text box directly on the design surface (not part of a data region), you must specify the dataset name as a scope for the aggregate function.</span></span> <span data-ttu-id="8edc1-119">예를 들어 `SalesData`라는 데이터 세트에 대해 `=Sum(Fields!Sales,"SalesData")` 식은 `Sales` 필드에 대한 모든 값의 합계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-119">For example, for a dataset named `SalesData`, the following expression specifies the total of all values for the field `Sales`: `=Sum(Fields!Sales,"SalesData")`.</span></span>  
  
 <span data-ttu-id="8edc1-120">**식** 대화 상자를 사용하여 단순 필드 참조를 정의하는 경우 범주 창에서 Fields 컬렉션을 선택하고 **필드** 창에서 사용 가능한 필드 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-120">When you use the **Expression** dialog box to define a simple field reference, you can select the Fields collection in the Category pane and see the list of available fields in the **Field** pane.</span></span> <span data-ttu-id="8edc1-121">각 필드에는 Value 및 IsMissing을 비롯한 여러 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-121">Each field has several properties, including Value and IsMissing.</span></span> <span data-ttu-id="8edc1-122">나머지 속성은 데이터 원본 유형에 따라 데이터 세트에 사용할 수 있는 미리 정의된 확장 필드 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-122">The remaining properties are predefined extended field properties that may be available to the dataset depending on the data source type.</span></span>  
  
### <a name="detecting-nulls-for-a-dataset-field"></a><span data-ttu-id="8edc1-123">데이터 세트 필드에 대한 Null 검색</span><span class="sxs-lookup"><span data-stu-id="8edc1-123">Detecting Nulls for a Dataset Field</span></span>  
 <span data-ttu-id="8edc1-124">Null([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서 `Nothing`)인 필드 값을 검색하려면 `IsNothing` 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-124">To detect a field value that is null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), you can use the function `IsNothing`.</span></span> <span data-ttu-id="8edc1-125">테이블 정보 행의 입력란에 다음 식이 배치되면 `MiddleName` 필드를 테스트하여 값이 Null인 경우 "No Middle Name" 텍스트를 대체하고, 값이 Null이 아닌 경우 필드 값 자체를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-125">When placed in a text box in a table details row, the following expression tests the field `MiddleName` and substitutes the text "No Middle Name" when the value is null, and the field value itself when the value is not null:</span></span>  
  
 `=IIF(IsNothing(Fields!MiddleName.Value),"No Middle Name",Fields!MiddleName.Value)`  
  
### <a name="detecting-missing-fields-for-dynamic-queries-at-run-time"></a><span data-ttu-id="8edc1-126">런타임에 동적 쿼리에 대해 누락된 필드 검색</span><span class="sxs-lookup"><span data-stu-id="8edc1-126">Detecting Missing Fields for Dynamic Queries at Run Time</span></span>  
 <span data-ttu-id="8edc1-127">Fields 컬렉션의 항목에는 기본적으로 Value 및 IsMissing 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-127">By default, items in the Fields collection have two properties: Value and IsMissing.</span></span> <span data-ttu-id="8edc1-128">IsMissing 속성은 디자인 타임에 데이터 세트에 대해 정의된 필드가 런타임에 검색되는 필드에 포함되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-128">The IsMissing property indicates whether a field that is defined for a dataset at design time is contained in the fields retrieved at run time.</span></span> <span data-ttu-id="8edc1-129">예를 들어 쿼리는 입력 매개 변수에 따라 결과 집합이 달라 지는 저장 프로시저를 호출 하거나 쿼리가 `SELECT * FROM` *\<table>* 테이블 정의가 변경 된 위치에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-129">For example, your query might call a stored procedure in which the result set varies with an input parameter, or your query might be `SELECT * FROM` *\<table>* where the table definition changed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8edc1-130">IsMissing은 모든 유형의 데이터 원본에 대해 디자인 타임과 런타임 간의 데이터 세트 스키마 변경을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-130">IsMissing detects changes in the dataset schema between design time and run time for any type of data source.</span></span> <span data-ttu-id="8edc1-131">IsMissing은 다차원 큐브의 빈 멤버를 검색 하는 데 사용할 수 없으며 및의 MDX 쿼리 언어 개념과 관련이 없습니다 `EMPTY` `NON EMPTY` .</span><span class="sxs-lookup"><span data-stu-id="8edc1-131">IsMissing cannot be used to detect empty members in a multidimensional cube and is not related to the MDX query language concepts of `EMPTY` and `NON EMPTY`.</span></span>  
  
 <span data-ttu-id="8edc1-132">사용자 지정 코드에서 IsMissing 속성을 테스트하여 결과 집합에 필드가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-132">You can test the IsMissing property in custom code to determine if a field is present in the result set.</span></span> <span data-ttu-id="8edc1-133">`IIF` 또는 `SWITCH`와 같은 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수 호출을 포함하는 식을 사용하여 필드의 존재 여부를 테스트할 수 없습니다. [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서는 함수 호출에서 모든 매개 변수를 평가하므로 누락된 필드에 대한 참조가 평가될 때 오류가 발생하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-133">You cannot test for its presence using an expression with a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function call such as `IIF` or `SWITCH`, because [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] evaluates all parameters in the call to the function, which results in an error when the reference to the missing is evaluated.</span></span>  
  
#### <a name="example-for-controlling-the-visibility-of-a-dynamic-column-for-a-missing-field"></a><span data-ttu-id="8edc1-134">누락된 필드에 대한 동적 열의 표시 유형을 제어하는 작업의 예</span><span class="sxs-lookup"><span data-stu-id="8edc1-134">Example for Controlling the Visibility of a Dynamic Column for a Missing Field</span></span>  
 <span data-ttu-id="8edc1-135">데이터 세트에 필드를 표시하는 열의 표시 유형을 제어하는 식을 설정하려면 먼저 필드의 누락 여부에 따라 부울 값을 반환하는 사용자 지정 코드 함수를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-135">To set an expression that controls the visibility of a column that displays a field in a dataset, you must first define a custom code function that returns a Boolean value based on whether the field is missing.</span></span> <span data-ttu-id="8edc1-136">예를 들어 다음 사용자 지정 코드 함수에서는 필드가 누락되면 True를 반환하고 필드가 존재하면 False를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-136">For example, the following custom code function returns true if the field is missing and false if the field exists.</span></span>  
  
```  
Public Function IsFieldMissing(field as Field) as Boolean  
 If (field.IsMissing) Then  
 Return True  
  Else   
  Return False  
 End If  
End Function  
```  
  
 <span data-ttu-id="8edc1-137">이 함수를 사용하여 열의 표시 유형을 제어하려면 열의 Hidden 속성을 다음 식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-137">To use this function to control visibility of a column, set the Hidden property of the column to the following expression:</span></span>  
  
 `=Code.IsFieldMissing(Fields!FieldName)`  
  
 <span data-ttu-id="8edc1-138">필드가 없는 경우 열이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-138">The column is hidden when the field does not exist.</span></span>  
  
#### <a name="example-for-controlling-the-text-box-value-for-a-missing-field"></a><span data-ttu-id="8edc1-139">누락된 필드에 대한 입력란 값을 제어하는 작업의 예</span><span class="sxs-lookup"><span data-stu-id="8edc1-139">Example for Controlling the Text Box Value for a Missing Field</span></span>  
 <span data-ttu-id="8edc1-140">누락된 필드 값 대신 작성할 텍스트를 대체하려면 필드가 누락된 경우 필드 값 대신 사용할 수 있는 텍스트를 반환하는 사용자 지정 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-140">To substitute text that you write in place of the value of a missing field, you must write custom code that returns text you can use in place of a field value when the field is missing.</span></span> <span data-ttu-id="8edc1-141">예를 들어 다음 사용자 지정 코드 함수에서는 필드가 있으면 필드 값을 반환하고 필드가 없으면 두 번째 매개 변수로 지정하는 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-141">For example, the following custom code function returns the value of the field if the field exists, and the message that you specify as the second parameter if the field does not exist:</span></span>  
  
```  
Public Function IsFieldMissingThenString(field as Field, strMessage as String) as String  
 If (field.IsMissing) Then  
  Return strMessage  
 Else   
  Return field.Value  
  End If  
End Function  
```  
  
 <span data-ttu-id="8edc1-142">입력란에 이 함수를 사용하려면 Value 속성에 다음 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-142">To use this function in a text box, add the following expression to the Value property:</span></span>  
  
 `=Code.IsFieldMissingThenString(Fields!FieldName,"Missing")`  
  
 <span data-ttu-id="8edc1-143">입력란에 지정한 필드 값 또는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-143">The text box displays either the field value or the text that you specified.</span></span>  
  
### <a name="using-extended-field-properties"></a><span data-ttu-id="8edc1-144">확장 필드 속성 사용</span><span class="sxs-lookup"><span data-stu-id="8edc1-144">Using Extended Field Properties</span></span>  
 <span data-ttu-id="8edc1-145">확장 필드 속성은 데이터 세트에 대한 데이터 원본 유형에 의해 결정되는 데이터 처리 확장 프로그램에서 필드에 대해 정의하는 추가 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-145">Extended field properties are additional properties defined on a field by the data processing extension, which is determined by the data source type for the dataset.</span></span> <span data-ttu-id="8edc1-146">확장 필드 속성은 미리 정의되거나 데이터 원본 유형 관련 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-146">Extended field properties are predefined or specific to a data source type.</span></span> <span data-ttu-id="8edc1-147">자세한 내용은 [Analysis Services 데이터베이스에 대한 확장 필드 속성 &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8edc1-147">For more information, see [Extended Field Properties for an Analysis Services Database &#40;SSRS&#41;](../report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).</span></span>  
  
 <span data-ttu-id="8edc1-148">해당 필드에 지원되지 않는 속성을 지정하는 경우 식이 `null`([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서 `Nothing`)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-148">If you specify a property that is not supported for that field, the expression evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="8edc1-149">데이터 공급자가 확장 필드 속성을 지원하지 않거나 쿼리가 실행될 때 해당 필드가 없으면 속성 값은 `null` 및 `Nothing` 형식 속성의 경우 `String`([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서 `Object`)이 되고 `Integer` 형식 속성의 경우 0이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-149">If a data provider does not support extended field properties, or if the field is not found when the query is executed, the value for the property is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) for properties of type `String` and `Object`, and zero (0) for properties of type `Integer`.</span></span> <span data-ttu-id="8edc1-150">데이터 처리 확장 프로그램에서는 이 구문이 포함된 쿼리를 최적화하여 미리 정의된 속성을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-150">A data processing extension may take advantage of predefined properties by optimizing queries that include this syntax.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8edc1-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8edc1-151">See Also</span></span>  
 <span data-ttu-id="8edc1-152">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8edc1-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8edc1-153">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edc1-153">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-datasets-ssrs.md)  
  
  
