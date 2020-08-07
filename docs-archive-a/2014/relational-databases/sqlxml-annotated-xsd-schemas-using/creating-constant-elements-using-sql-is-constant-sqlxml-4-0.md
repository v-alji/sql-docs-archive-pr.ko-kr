---
title: 'Sql: is 상수를 사용 하 여 상수 요소 만들기 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 8deedd8547d6bc3f0154eedb889ad908750f071a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733727"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a><span data-ttu-id="d060c-102">sql:is-constant를 사용하여 상수 요소 만들기(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d060c-102">Creating Constant Elements Using sql:is-constant (SQLXML 4.0)</span></span>
  <span data-ttu-id="d060c-103">상수 요소, 즉 데이터베이스 테이블 또는 열에 매핑되지 않는 XSD 스키마의 요소를 지정 하려면 주석을 사용할 수 있습니다 `sql:is-constant` .</span><span class="sxs-lookup"><span data-stu-id="d060c-103">To specify a constant element-that is, an element in the XSD schema that does not map to any database table or column-you can use the `sql:is-constant` annotation.</span></span> <span data-ttu-id="d060c-104">이 주석은 부울 값(0=false, 1=true)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-104">This annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="d060c-105">허용되는 값은 0, 1, true 및 false입니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-105">The acceptable values are 0, 1, true, and false.</span></span> <span data-ttu-id="d060c-106">`sql:is-constant` 주석은 특성이 없는 요소에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-106">The `sql:is-constant` annotation can be specified on an element that does not have any attributes.</span></span> <span data-ttu-id="d060c-107">값이 true(또는 1)인 요소에 이 주석을 지정하면 해당 요소는 데이터베이스에 매핑되지 않지만 XML 문서에 계속 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-107">If it is specified on an element with the value true (or 1), that element is not mapped to the database but still appears in the XML document.</span></span>  
  
 <span data-ttu-id="d060c-108">`sql:is-constant` 주석은 다음과 같은 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-108">The `sql:is-constant` annotation can be used for:</span></span>  
  
-   <span data-ttu-id="d060c-109">XML 문서에 최상위 요소 추가.</span><span class="sxs-lookup"><span data-stu-id="d060c-109">Adding a top-level element to the XML document.</span></span> <span data-ttu-id="d060c-110">XML 문서에는 단일 최상위 요소(root 요소)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-110">XML requires a single top-level element (root element) for the document.</span></span>  
  
-   <span data-ttu-id="d060c-111">**\<Orders>** 모든 주문을 래핑하는 요소와 같은 컨테이너 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="d060c-111">Creating container elements, such as an **\<Orders>** element that wraps all orders.</span></span>  
  
 <span data-ttu-id="d060c-112">`sql:is-constant`주석은 요소에 추가할 수 있습니다 **\<complexType>** .</span><span class="sxs-lookup"><span data-stu-id="d060c-112">The `sql:is-constant` annotation can be added to a **\<complexType>** element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d060c-113">예제</span><span class="sxs-lookup"><span data-stu-id="d060c-113">Examples</span></span>  
 <span data-ttu-id="d060c-114">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-114">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="d060c-115">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d060c-115">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a><span data-ttu-id="d060c-116">A.</span><span class="sxs-lookup"><span data-stu-id="d060c-116">A.</span></span> <span data-ttu-id="d060c-117">컨테이너 요소를 추가하는 sql:is-constant 지정</span><span class="sxs-lookup"><span data-stu-id="d060c-117">Specifying sql:is-constant to add a container element</span></span>  
 <span data-ttu-id="d060c-118">주석이 추가 된이 XSD 스키마에서 **\<CustomerOrders>** 은 `sql:is-constant` 값이 1 인 특성을 지정 하 여 상수 요소로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-118">In this annotated XSD schema, **\<CustomerOrders>** is defined as a constant element by specifying the `sql:is-constant` attribute with a value of 1.</span></span> <span data-ttu-id="d060c-119">따라서 **\<CustomerOrders>** 는 데이터베이스 테이블 또는 열에 매핑되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-119">Therefore, **\<CustomerOrders>** is not mapped to any database table or column.</span></span> <span data-ttu-id="d060c-120">이 상수 요소는 **\<Order>** 자식 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-120">This constant element consists of the **\<Order>** child elements.</span></span>  
  
 <span data-ttu-id="d060c-121">**\<CustomerOrders>** 는 어떠한 데이터베이스 테이블이 나 열에도 매핑되지 않지만 결과 XML에는 자식 요소를 포함 하는 컨테이너 요소로 표시 됩니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="d060c-121">Although **\<CustomerOrders>** does not map to any database table or column, it still appears in the resulting XML as a container element containing the **\<Order>** child elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d060c-122">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d060c-122">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d060c-123">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-123">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d060c-124">파일을 isConstant.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-124">Save the file as isConstant.xml.</span></span>  
  
2.  <span data-ttu-id="d060c-125">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-125">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="d060c-126">파일을 isConstant.xml을 저장한 디렉터리와 같은 디렉터리에 isConstantT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-126">Save the file as isConstantT.xml in the same directory where you saved isConstant.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d060c-127">매핑 스키마(isConstant.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-127">The directory path specified for the mapping schema (isConstant.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d060c-128">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-128">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  <span data-ttu-id="d060c-129">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-129">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d060c-130">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d060c-130">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d060c-131">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="d060c-131">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
