---
title: XPath 쿼리에 부울 반환 조건자 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- nested predicates
- successive predicates
- predicates [SQLXML]
- top-level predicates
- Boolean-valued predicates
- multiple predicates
ms.assetid: 5f6e7219-6911-4bca-a54b-56b95e0b43dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 56f2f94ec895c5b76382d5103ca9d518b78cc899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646282"
---
# <a name="specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="4ddb7-102">XPath 쿼리에 부울 반환 조건자 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4ddb7-102">Specifying Boolean-Valued Predicates in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="4ddb7-103">다음 예에서는 XPath 쿼리에 부울 반환 조건자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-103">The following examples show how Boolean-valued predicates are specified in XPath queries.</span></span> <span data-ttu-id="4ddb7-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="4ddb7-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4ddb7-106">예</span><span class="sxs-lookup"><span data-stu-id="4ddb7-106">Examples</span></span>  
  
### <a name="a-specify-multiple-predicates"></a><span data-ttu-id="4ddb7-107">A.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-107">A.</span></span> <span data-ttu-id="4ddb7-108">여러 조건자 지정</span><span class="sxs-lookup"><span data-stu-id="4ddb7-108">Specify multiple predicates</span></span>  
 <span data-ttu-id="4ddb7-109">다음 XPath 쿼리에서는 여러 조건자를 사용하여 지정된 주문 ID 및 고객 ID에 대한 주문 정보를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-109">The following XPath query uses multiple predicates to find order information for a given order ID and a customer ID:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]/child::Order[attribute::OrderID="Ord-43860"]  
```  
  
 <span data-ttu-id="4ddb7-110">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4ddb7-111">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="4ddb7-111">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4ddb7-112">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-112">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4ddb7-113">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-113">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4ddb7-114">다음 템플릿(BooleanValuedPredicatesA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-114">Create the following template (BooleanValuedPredicatesA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4ddb7-115">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-115">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4ddb7-116">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-116">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4ddb7-117">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-117">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4ddb7-118">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-118">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
     <span data-ttu-id="4ddb7-119">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-119">Here is the result:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
        <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-761" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-762" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-765" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-768" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-770" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
      </Order>  
    </ROOT>  
    ```  
  
### <a name="b-specify-successive-and-nested-predicates"></a><span data-ttu-id="4ddb7-120">B.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-120">B.</span></span> <span data-ttu-id="4ddb7-121">연속 및 중첩된 조건자 지정</span><span class="sxs-lookup"><span data-stu-id="4ddb7-121">Specify successive and nested predicates</span></span>  
 <span data-ttu-id="4ddb7-122">다음 쿼리에서는 연속 조건자를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-122">The following query shows using successive predicates.</span></span> <span data-ttu-id="4ddb7-123">이 쿼리는 **\<Customer>** **SalesPersonID** 특성 값이 277이 고 **TerritoryID** 특성이 3 인 컨텍스트 노드의 모든 자식 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-123">The query returns all the **\<Customer>** child elements of the context node that have both a **SalesPersonID** attribute with a value of 277 and a **TerritoryID** attribute with a value of 3:</span></span>  
  
```  
/child::Customer[attribute::SalesPersonID="277"][attribute::TerritoryID="3"]  
```  
  
 <span data-ttu-id="4ddb7-124">이 쿼리는 **\<Customer>** 조건자에 지정 된 조건을 모두 충족 하는 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-124">The query returns the **\<Customer>** elements that satisfy both the conditions specified in the predicates.</span></span>  
  
 <span data-ttu-id="4ddb7-125">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-125">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@SalesPersonID="277"][@TerritoryID="3"]  
```  
  
 <span data-ttu-id="4ddb7-126">다음 XPath 쿼리에서는 중첩된 조건자를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-126">The following XPath query illustrates the use of nested predicates.</span></span> <span data-ttu-id="4ddb7-127">이 쿼리는 **\<Customer>** **\<Order>** **\<Order>** **SalesPersonID** 특성 값이 2 인 요소를 하나 이상 포함 하는 자식 요소를 포함 하는 컨텍스트 노드의 모든 자식 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-127">The query returns all the **\<Customer>** child elements of the context node that include **\<Order>** child elements with at least one **\<Order>** element that has a **SalesPersonID** attribute value of 2.</span></span>  
  
```  
/Customer[Order[@SalesPersonID=2]]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4ddb7-128">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="4ddb7-128">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4ddb7-129">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-129">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4ddb7-130">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-130">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4ddb7-131">다음 템플릿(nestedSuccessive.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-131">Create the following template (nestedSuccessive.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
             /Customer[@SalesPersonID="277"][@TerritoryID="3"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4ddb7-132">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-132">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4ddb7-133">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4ddb7-134">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4ddb7-135">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4ddb7-136">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-136">The following is a partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="22" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="22" CustomerType="S"   
            Orders="Ord-43874 Ord-44519 Ord-46989 Ord-48013 Ord-49130 Ord-50274 Ord-51807 Ord-57113 Ord-63162 Ord-69495">  
    <Order SalesOrderID="Ord-43874" SalesPersonID="277"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
                   OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    ...  
  </Customer>  
  <Customer CustomerID="39" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="39" CustomerType="S"   
            Orders="Ord-47428 Ord-48367 Ord-49529 Ord-50742 Ord-53591 Ord-59051 Ord-65301 Ord-71912">    <Order SalesOrderID="Ord-47428" SalesPersonID="277"   
           OrderDate="2002-09-01T00:00:00"   
           DueDate="2002-09-13T00:00:00"   
           ShipDate="2002-09-08T00:00:00">  
      <OrderDetail ProductID="Prod-759" UnitPrice="563.7528" OrderQty="2" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-769" UnitPrice="563.7528" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
### <a name="c-specify-a-top-level-predicate"></a><span data-ttu-id="4ddb7-137">C.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-137">C.</span></span> <span data-ttu-id="4ddb7-138">최상위 조건자 지정</span><span class="sxs-lookup"><span data-stu-id="4ddb7-138">Specify a top-level predicate</span></span>  
 <span data-ttu-id="4ddb7-139">다음 쿼리는 **\<Customer>** 요소 자식이 있는 컨텍스트 노드의 자식 요소 노드를 반환 합니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="4ddb7-139">The following query returns the **\<Customer>** child element nodes of the context node that have **\<Order>** element children.</span></span> <span data-ttu-id="4ddb7-140">이 쿼리에서는 위치 경로를 최상위 조건자로 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-140">The query tests the location path as the top-level predicate:</span></span>  
  
```  
/child::Customer[child::Order]  
```  
  
 <span data-ttu-id="4ddb7-141">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-141">The `child` axis is the default.</span></span> <span data-ttu-id="4ddb7-142">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-142">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="4ddb7-143">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="4ddb7-143">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="4ddb7-144">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-144">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="4ddb7-145">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-145">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="4ddb7-146">다음 템플릿(TopLevelPredicate.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-146">Create the following template (TopLevelPredicate.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4ddb7-147">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-147">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4ddb7-148">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="4ddb7-149">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4ddb7-150">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4ddb7-151">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="4ddb7-151">Here is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280" TerritoryID="1" AccountNumber="1" CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    <Order SalesOrderID="Ord-44501" SalesPersonID="280" OrderDate="2001-11-01T00:00:00" DueDate="2001-11-13T00:00:00" ShipDate="2001-11-08T00:00:00">  
      <OrderDetail ProductID="Prod-725" UnitPrice="226.8571" OrderQty="3" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-726" UnitPrice="226.8571" OrderQty="2" UnitPriceDiscount="0" />   
      ...  
    </Order>    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
  
