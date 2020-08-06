---
title: XPath 쿼리에 관계형 연산자 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], relational operators
- relational operators [SQLXML]
- XPath operators [SQLXML]
- operators [SQLXML]
ms.assetid: 177a0eb2-11ef-4459-a317-485a433ee769
author: rothja
ms.author: jroth
ms.openlocfilehash: 50d59ebd3a776386c61f4c3a8a1e892d30981d1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646275"
---
# <a name="specifying-relational-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="1232e-102">XPath 쿼리에 관계형 연산자 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1232e-102">Specifying Relational Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="1232e-103">다음 예에서는 XPath 쿼리에 관계형 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-103">The following examples show how relational operators are specified in XPath queries.</span></span> <span data-ttu-id="1232e-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="1232e-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1232e-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1232e-106">예</span><span class="sxs-lookup"><span data-stu-id="1232e-106">Examples</span></span>  
  
### <a name="a-specify-relational-operator"></a><span data-ttu-id="1232e-107">A.</span><span class="sxs-lookup"><span data-stu-id="1232e-107">A.</span></span> <span data-ttu-id="1232e-108">관계형 연산자 지정</span><span class="sxs-lookup"><span data-stu-id="1232e-108">Specify relational operator</span></span>  
 <span data-ttu-id="1232e-109">이 XPath 쿼리는 **\<Customer>** **CustomerID** 특성 값이 "1"이 고 모든 자식 **\<Order>** 요소에 값이 **\<OrderDetail>** 3 보다 큰 **OrderQty** 특성을 가진 자식이 포함 된 요소의 자식 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-109">This XPath query returns the child elements of the **\<Customer>** element where the **CustomerID** attribute value is "1" and where any child **\<Order>** elements contain an **\<OrderDetail>** child with a **OrderQty** attribute with a value greater than 3:</span></span>  
  
```  
/child::Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
 <span data-ttu-id="1232e-110">대괄호에 지정 된 조건자는 요소를 필터링 합니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="1232e-110">The predicate specified in the brackets filters the **\<Customer>** elements.</span></span> <span data-ttu-id="1232e-111">**\<Customer>** **\<OrderDetail>** OrderQty 특성 값이 3 보다 큰 손자가 하나 이상 있는 요소만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-111">Only the **\<Customer>** elements that have at least one **\<OrderDetail>** grandchild with a OrderQty attribute value greater than 3 are returned.</span></span>  
  
 <span data-ttu-id="1232e-112">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-112">The `child` axis is the default.</span></span> <span data-ttu-id="1232e-113">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-113">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="1232e-114">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="1232e-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="1232e-115">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="1232e-116">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="1232e-117">다음 템플릿(SpecifyRelationalA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-117">Create the following template (SpecifyRelationalA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="1232e-118">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="1232e-119">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="1232e-120">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="1232e-121">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1232e-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="1232e-122">다음은 템플릿 실행의 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-122">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-760" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-766" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-757" UnitPrice="1049.7528" OrderQty="4" UnitPriceDiscount="0" />   
</ROOT>  
```  
  
### <a name="b-specify-relational-operator-in-the-xpath-query-and-use-boolean-function-to-compare-the-result"></a><span data-ttu-id="1232e-123">B.</span><span class="sxs-lookup"><span data-stu-id="1232e-123">B.</span></span> <span data-ttu-id="1232e-124">XPath 쿼리에 관계형 연산자 지정 및 부울 함수를 사용하여 결과 비교</span><span class="sxs-lookup"><span data-stu-id="1232e-124">Specify relational operator in the XPath query and use Boolean function to compare the result</span></span>  
 <span data-ttu-id="1232e-125">이 쿼리는 **\<Order>** **SalesPersonID** 특성 값이 270 보다 작은 컨텍스트 노드의 모든 요소 자식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-125">This query returns all the **\<Order>** element children of the context node that have an **SalesPersonID** attribute value that is less than 270:</span></span>  
  
```  
/child::Customer/child::Order[(attribute::SalesPersonID < 270)=true()]  
```  
  
 <span data-ttu-id="1232e-126">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-126">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer/Order[(@SalesPersonID < 270)=true()]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1232e-127">이 쿼리를 템플릿에서 지정 하는 경우 < 문자는 XML 문서에서 특별 한 의미가 있기 때문에 < 문자는 엔터티 인코딩 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-127">When this query is specified in a template, the < character must be entity encoded because the < character has special meaning in an XML document.</span></span> <span data-ttu-id="1232e-128">템플릿에서 `<` < 문자를 지정 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-128">In a template, use `<` to specify the < character.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="1232e-129">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="1232e-129">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="1232e-130">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-130">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="1232e-131">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-131">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="1232e-132">다음 템플릿(SpecifyRelationalB.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-132">Create the following template (SpecifyRelationalB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="SampleSchema1.xml">  
            /Customer/Order[(@SalesPersonID<270)=true()]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="1232e-133">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-133">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="1232e-134">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-134">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="1232e-135">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-135">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="1232e-136">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1232e-136">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="1232e-137">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="1232e-137">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-46613" SalesPersonID="268"   
         OrderDate="2002-07-01T00:00:00"   
         DueDate="2002-07-13T00:00:00"   
         ShipDate="2002-07-08T00:00:00">  
    <OrderDetail ProductID="Prod-739" UnitPrice="917.9363"   
                 OrderQty="2" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-779" UnitPrice="1491.4221"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-825" UnitPrice="242.1391"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  <Order SalesOrderID="Ord-71919" SalesPersonID="268"  
         OrderDate="2004-06-01T00:00:00"   
         DueDate="2004-06-13T00:00:00"   
         ShipDate="2004-06-08T00:00:00">  
    <OrderDetail ProductID="Prod-961" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-965" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-966" UnitPrice="1716.5304"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  ...  
</ROOT>  
```  
  
  
