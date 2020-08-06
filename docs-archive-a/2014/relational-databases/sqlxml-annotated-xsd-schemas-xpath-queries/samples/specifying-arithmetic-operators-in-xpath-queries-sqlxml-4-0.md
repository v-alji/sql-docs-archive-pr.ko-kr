---
title: XPath 쿼리에 산술 연산자 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 904f3b920029d45d1b72641a19e2ac07befd4def
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646287"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="dcac7-102">XPath 쿼리에 산술 연산자 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="dcac7-102">Specifying Arithmetic Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="dcac7-103">다음 예에서는 XPath 쿼리에 산술 연산자를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-103">The following example shows how arithmetic operators are specified in XPath queries.</span></span> <span data-ttu-id="dcac7-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="dcac7-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcac7-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dcac7-106">예</span><span class="sxs-lookup"><span data-stu-id="dcac7-106">Examples</span></span>  
  
### <a name="a-specify-the--arithmetic-operator"></a><span data-ttu-id="dcac7-107">A.</span><span class="sxs-lookup"><span data-stu-id="dcac7-107">A.</span></span> <span data-ttu-id="dcac7-108">\* 산술 연산자 지정</span><span class="sxs-lookup"><span data-stu-id="dcac7-108">Specify the \* arithmetic operator</span></span>  
 <span data-ttu-id="dcac7-109">이 XPath 쿼리 **\<OrderDetail>** 는 지정 된 조건자를 충족 하는 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-109">This XPath query returns **\<OrderDetail>** elements that satisfy the predicate specified:</span></span>  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 <span data-ttu-id="dcac7-110">쿼리에서는 `child` 축 이며 `OrderDetail` 노드 테스트 ( **orderdetail** 이 **\<element node>** **\<element>** 축에 대 한 주 노드인지 때문에 orderdetail이 인 경우 TRUE `child` )입니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-110">In the query, `child` is the axis and `OrderDetail` is the node test (TRUE if **OrderDetail** is an **\<element node>**, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="dcac7-111">모든 **\<OrderDetail>** 요소 노드에 대해 조건자의 테스트가 적용 되며 조건을 충족 하는 노드만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-111">For all the **\<OrderDetail>** element nodes, the test in the predicate is applied, and only those nodes that satisfy the condition are returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcac7-112">XPath의 숫자는 배정밀도 부동 소수점 숫자이며 이 예와 같이 부동 소수점 숫자를 비교하면 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-112">The numbers in XPath are double-precision floating-point numbers, and comparing floating-point numbers as in the example causes rounding.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="dcac7-113">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="dcac7-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="dcac7-114">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="dcac7-115">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="dcac7-116">다음 템플릿(ArithmeticOperatorA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-116">Create the following template (ArithmeticOperatorA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="dcac7-117">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="dcac7-118">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="dcac7-119">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dcac7-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="dcac7-120">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcac7-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  
