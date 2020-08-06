---
title: XPath 쿼리에 부울 연산자 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dd6e1f120b53382ce984684ea352b36d34b768
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646283"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="c0b27-102">XPath 쿼리에 부울 연산자 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c0b27-102">Specifying Boolean Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="c0b27-103">다음 예에서는 XPath 쿼리에 부울 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-103">The following example shows how Boolean operators are specified in XPath queries.</span></span> <span data-ttu-id="c0b27-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="c0b27-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b27-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c0b27-106">예</span><span class="sxs-lookup"><span data-stu-id="c0b27-106">Examples</span></span>  
  
### <a name="a-specify-the-or-boolean-operator"></a><span data-ttu-id="c0b27-107">A.</span><span class="sxs-lookup"><span data-stu-id="c0b27-107">A.</span></span> <span data-ttu-id="c0b27-108">OR 부울 연산자 지정</span><span class="sxs-lookup"><span data-stu-id="c0b27-108">Specify the OR Boolean operator</span></span>  
 <span data-ttu-id="c0b27-109">이 XPath 쿼리는 **\<Customer>** **CustomerID** 특성 값이 13 또는 31 인 컨텍스트 노드의 요소 자식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-109">This XPath query returns the **\<Customer>** element children of the context node with the **CustomerID** attribute value of 13 or 31:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 <span data-ttu-id="c0b27-110">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본값이므로 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted:</span></span>  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 <span data-ttu-id="c0b27-111">조건자에서 `attribute` 는 축이 고 `CustomerID` 는 노드 테스트 ( **CustomerID** **\<attribute>** 해당 **\<attribute>** 노드가 축에 대 한 주 노드인지 때문에 CustomerID가 노드인 경우 TRUE `attribute` )입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-111">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an **\<attribute>** node, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span> <span data-ttu-id="c0b27-112">조건자는 요소를 필터링 **\<Customer>** 하 고 조건자에 지정 된 조건을 만족 하는 요소만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-112">The predicate filters the **\<Customer>** elements and returns only those that satisfy the condition specified in the predicate.</span></span>  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a><span data-ttu-id="c0b27-113">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="c0b27-113">To test the XPath queries against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c0b27-114">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c0b27-115">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c0b27-116">다음 템플릿(BooleanOperatorsA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-116">Create the following template (BooleanOperatorsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c0b27-117">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c0b27-118">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c0b27-119">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c0b27-120">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b27-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c0b27-121">다음은 템플릿 실행의 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b27-121">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
