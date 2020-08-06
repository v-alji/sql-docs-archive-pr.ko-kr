---
title: XPath 쿼리에 부울 함수 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
author: rothja
ms.author: jroth
ms.openlocfilehash: d230c7cd8792066732085b9ce501c0794687d17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646284"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="32e4c-102">XPath 쿼리에 부울 함수 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="32e4c-102">Specifying Boolean Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="32e4c-103">다음 예에서는 XPath 쿼리에 부울 함수를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-103">The following examples show how Boolean functions are specified in XPath queries.</span></span> <span data-ttu-id="32e4c-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="32e4c-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="32e4c-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="32e4c-106">예</span><span class="sxs-lookup"><span data-stu-id="32e4c-106">Examples</span></span>  
  
## <a name="a-specify-the-not-boolean-function"></a><span data-ttu-id="32e4c-107">A.</span><span class="sxs-lookup"><span data-stu-id="32e4c-107">A.</span></span> <span data-ttu-id="32e4c-108">not() 부울 함수 지정</span><span class="sxs-lookup"><span data-stu-id="32e4c-108">Specify the not() Boolean function</span></span>  
 <span data-ttu-id="32e4c-109">이 쿼리는 **\<Customer>** 자식 요소가 없는 컨텍스트 노드의 모든 자식 요소를 반환 합니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="32e4c-109">This query returns all the **\<Customer>** child elements of the context node that do not have **\<Order>** child elements:</span></span>  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 <span data-ttu-id="32e4c-110">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-110">The `child` axis is the default.</span></span> <span data-ttu-id="32e4c-111">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-111">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="32e4c-112">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="32e4c-112">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="32e4c-113">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-113">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="32e4c-114">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-114">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="32e4c-115">다음 템플릿(BooleanFunctionsA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-115">Create the following template (BooleanFunctionsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="32e4c-116">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-116">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="32e4c-117">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-117">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="32e4c-118">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-118">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="32e4c-119">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="32e4c-119">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="32e4c-120">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-120">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a><span data-ttu-id="32e4c-121">B.</span><span class="sxs-lookup"><span data-stu-id="32e4c-121">B.</span></span> <span data-ttu-id="32e4c-122">true() 및 false() 부울 함수 지정</span><span class="sxs-lookup"><span data-stu-id="32e4c-122">Specify the true() and false() Boolean functions</span></span>  
 <span data-ttu-id="32e4c-123">이 쿼리는 **\<Customer>** 자식 요소가 없는 컨텍스트 노드의 모든 요소 자식을 반환 **\<Order>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-123">This query returns all **\<Customer>** element children of the context node that do not have **\<Order>** child elements.</span></span> <span data-ttu-id="32e4c-124">관계적인 측면으로 설명하면 이 쿼리는 주문을 하지 않은 모든 고객을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-124">In relational terms, this query returns all customers who have not placed any orders.</span></span>  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 <span data-ttu-id="32e4c-125">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-125">The `child` axis is the default.</span></span> <span data-ttu-id="32e4c-126">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-126">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order=false()]  
```  
  
 <span data-ttu-id="32e4c-127">이 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-127">This query is equivalent to the following:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
 <span data-ttu-id="32e4c-128">다음 쿼리는 주문을 한 번 이상 한 모든 고객을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-128">The following query returns all the customers who have placed at least one order:</span></span>  
  
```  
/Customer[Order=true()]  
```  
  
 <span data-ttu-id="32e4c-129">이 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-129">This query is equivalent to this one:</span></span>  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="32e4c-130">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="32e4c-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="32e4c-131">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="32e4c-132">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="32e4c-133">다음 템플릿(BooleanFunctionsB.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-133">Create the following template (BooleanFunctionsB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="32e4c-134">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="32e4c-135">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="32e4c-136">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="32e4c-137">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="32e4c-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="32e4c-138">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="32e4c-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
