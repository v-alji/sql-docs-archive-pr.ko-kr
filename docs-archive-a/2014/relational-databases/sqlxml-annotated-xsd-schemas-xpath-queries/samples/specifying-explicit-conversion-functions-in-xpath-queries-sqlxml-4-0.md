---
title: XPath 쿼리에 명시적 변환 함수 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b4b9bd5f5665c8cb86cb74c1397e2bd06e113fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646279"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="8f324-102">XPath 쿼리에 명시적 변환 함수 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8f324-102">Specifying Explicit Conversion Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="8f324-103">다음 예에서는 XPath 쿼리에 명시적 변환 함수를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-103">The following examples show how explicit conversion functions are specified in XPath queries.</span></span> <span data-ttu-id="8f324-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="8f324-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f324-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8f324-106">예</span><span class="sxs-lookup"><span data-stu-id="8f324-106">Examples</span></span>  
  
### <a name="a-use-the-number-explicit-conversion-function"></a><span data-ttu-id="8f324-107">A.</span><span class="sxs-lookup"><span data-stu-id="8f324-107">A.</span></span> <span data-ttu-id="8f324-108">number() 명시적 변환 함수 사용</span><span class="sxs-lookup"><span data-stu-id="8f324-108">Use the number() explicit conversion function</span></span>  
 <span data-ttu-id="8f324-109">`number()` 함수는 인수를 숫자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-109">The `number()` function converts an argument to a number.</span></span>  
  
 <span data-ttu-id="8f324-110">**ContactID** 의 값이 숫자가 아닌 경우 다음 쿼리는 **ContactID** 를 숫자로 변환 하 고 값 4와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-110">Assuming the value of **ContactID** is nonnumeric, the following query converts **ContactID** to a number and compares it with the value 4.</span></span> <span data-ttu-id="8f324-111">그런 다음 쿼리는 **\<Employee>** 숫자 값이 4 인 **ContactID** 특성을 사용 하 여 컨텍스트 노드의 모든 요소 자식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-111">The query then returns all **\<Employee>** element children of the context node with the **ContactID** attribute that has a numeric value of 4:</span></span>  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 <span data-ttu-id="8f324-112">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-112">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 <span data-ttu-id="8f324-113">관계형 용어에서 쿼리는 **ContactID** 가 4 인 직원을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-113">In relational terms, the query returns an employee with a **ContactID** of 4.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="8f324-114">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="8f324-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="8f324-115">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="8f324-116">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="8f324-117">다음 템플릿(ExplicitConversionA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-117">Create the following template (ExplicitConversionA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="8f324-118">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="8f324-119">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="8f324-120">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="8f324-121">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f324-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="8f324-122">다음은 이 템플릿 실행의 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-122">The result set for this template execution is:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a><span data-ttu-id="8f324-123">B.</span><span class="sxs-lookup"><span data-stu-id="8f324-123">B.</span></span> <span data-ttu-id="8f324-124">string() 명시적 변환 함수 사용</span><span class="sxs-lookup"><span data-stu-id="8f324-124">Use the string() explicit conversion function</span></span>  
 <span data-ttu-id="8f324-125">`string()` 함수는 인수를 문자열로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-125">The `string()` function converts an argument to a string.</span></span>  
  
 <span data-ttu-id="8f324-126">다음 쿼리는 **ContactID** 을 문자열로 변환 하 고 문자열 값 "4"와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-126">The following query converts **ContactID** to a string and compares it with the string value "4".</span></span> <span data-ttu-id="8f324-127">이 쿼리는 **\<Employee>** 문자열 값이 "4" 인 **ContactID** 를 사용 하 여 컨텍스트 노드의 모든 요소 자식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-127">The query returns all **\<Employee>** element children of the context node with a **ContactID** with a string value of "4":</span></span>  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 <span data-ttu-id="8f324-128">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-128">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 <span data-ttu-id="8f324-129">이 쿼리는 숫자 값(즉, 숫자 4)이 아닌 문자열 값에 대해 계산을 수행하지만 기능적으로 앞의 예제 쿼리와 동일한 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-129">Functionally, this query returns the same results as the previous example query, though the evaluation is done against a string value and not the numeric value (that is, the number 4).</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="8f324-130">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="8f324-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="8f324-131">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="8f324-132">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="8f324-133">다음 템플릿(ExplicitConversionB.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-133">Create the following template (ExplicitConversionB.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="8f324-134">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="8f324-135">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="8f324-136">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="8f324-137">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f324-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="8f324-138">다음은 템플릿 실행의 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8f324-138">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
