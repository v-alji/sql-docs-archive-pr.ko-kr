---
title: 'Sql: hide |를 사용 하 여 요소 및 특성 숨기기 Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a3beb48be1d9809b170faeafa964ba45156ac28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741671"
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a><span data-ttu-id="62058-102">sql:hide를 사용하여 요소 및 특성 숨기기</span><span class="sxs-lookup"><span data-stu-id="62058-102">Hiding Elements and Attributes by Using sql:hide</span></span>
  <span data-ttu-id="62058-103">XSD 스키마에 대해 XPath 쿼리를 실행하면 결과 XML 문서에는 스키마에 지정된 요소와 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="62058-103">When an XPath query is executed against an XSD schema, the resulting XML document has elements and attributes that are specified in the schema.</span></span> <span data-ttu-id="62058-104">`sql:hide` 주석을 사용하여 일부 요소와 특성이 스키마에서 숨겨지도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-104">You can specify that some elements and attributes be hidden in the schema by using the `sql:hide` annotation.</span></span> <span data-ttu-id="62058-105">이는 쿼리의 선택 조건에 스키마의 특정 요소나 특성이 필요하지만 생성되는 XML 문서에는 해당 요소나 특성이 포함되지 않게 하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-105">This is useful when the selection criteria of the query require particular elements or attributes in the schema, but you do not want them returned in the XML document that is generated.</span></span>  
  
 <span data-ttu-id="62058-106">`sql:hide` 주석은 부울 값(0=false, 1=true)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-106">The `sql:hide` annotation takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="62058-107">허용되는 값은 0, 1, true 및 false입니다.</span><span class="sxs-lookup"><span data-stu-id="62058-107">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="62058-108">예</span><span class="sxs-lookup"><span data-stu-id="62058-108">Examples</span></span>  
 <span data-ttu-id="62058-109">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="62058-110">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62058-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a><span data-ttu-id="62058-111">A.</span><span class="sxs-lookup"><span data-stu-id="62058-111">A.</span></span> <span data-ttu-id="62058-112">특성에 sql:hide 지정</span><span class="sxs-lookup"><span data-stu-id="62058-112">Specifying sql:hide on an attribute</span></span>  
 <span data-ttu-id="62058-113">이 예의 XSD 스키마는 **\<Person.Contact>** **ContactID**, **FirstName**및 **LastName** 특성이 있는 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62058-113">The XSD schema in this example consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span>  
  
 <span data-ttu-id="62058-114">**\<Person.Contact>** 요소는 복합 유형 이므로 동일한 이름 (기본 매핑)의 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="62058-114">The **\<Person.Contact>** element is of complex type and, therefore, maps to the table of the same name (default mapping).</span></span> <span data-ttu-id="62058-115">요소의 모든 특성은 **\<Person.Contact>** 단순 형식이 며 AdventureWorks 데이터베이스의 Person 테이블에서 이름이 같은 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="62058-115">All the attributes of **\<Person.Contact>** element are of simple type and map to columns with the same names in the Person.Contacttable in the AdventureWorks database.</span></span> <span data-ttu-id="62058-116">스키마에서 `sql:hide` 주석은 **ContactID** 특성에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62058-116">In the schema, the `sql:hide` annotation is specified on the **ContactID** attribute.</span></span> <span data-ttu-id="62058-117">이 스키마에 대해 XPath 쿼리를 지정 하면 **ContactID** 는 XML 문서에 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-117">When an XPath query is specified against this schema, the **ContactID** is not returned in the XML document.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="62058-118">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="62058-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="62058-119">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="62058-120">파일을 Hide.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-120">Save the file as Hide.xml.</span></span>  
  
2.  <span data-ttu-id="62058-121">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="62058-122">파일을 Hide.xml을 저장한 디렉터리와 같은 디렉터리에 HideT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-122">Save the file as HideT.xml in the same directory where you saved Hide.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="62058-123">매핑 스키마(Hide.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="62058-123">The directory path specified for the mapping schema (Hide.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="62058-124">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-124">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  <span data-ttu-id="62058-125">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="62058-125">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="62058-126">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62058-126">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="62058-127">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-127">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 <span data-ttu-id="62058-128">요소에 대해 `sql:hide`를 지정하면 생성되는 XML 문서에 요소와 해당 특성 또는 자식 요소가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-128">When `sql:hide` is specified on an element, the element and its attributes or child elements do not appear in the XML document that is generated.</span></span> <span data-ttu-id="62058-129">다음은 `sql:hide` 요소에를 지정 하는 다른 XSD 스키마입니다 **\<OD>** .</span><span class="sxs-lookup"><span data-stu-id="62058-129">Here is another XSD schema in which `sql:hide` is specified on the **\<OD>** element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="62058-130">이 스키마에 대해 XPath 쿼리 (예:)를 지정 하는 경우 `/Customers[@CID="1"]` 생성 된 XML 문서에는 **\<OD>** 다음 부분 결과와 같이 요소와 해당 자식이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62058-130">When an XPath query (for example `/Customers[@CID="1"]`) is specified against this schema, the XML document that is generated does not include the **\<OD>** element and its children, as shown in this partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  
