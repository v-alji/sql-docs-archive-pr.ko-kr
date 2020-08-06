---
title: 'sql: relationship 및 키 순서 지정 규칙 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: rothja
ms.author: jroth
ms.openlocfilehash: 716e911676dc81539fc641bee139d92e29dc49db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652752"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a><span data-ttu-id="c23ed-102">sql:relationship 및 키 순서 지정 규칙(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c23ed-102">sql:relationship and the Key Ordering Rule (SQLXML 4.0)</span></span>
  <span data-ttu-id="c23ed-103">XML 대량 로드는 해당 노드의 범위가 시작될 때 레코드를 생성하고 해당 노드의 범위가 끝날 때 이러한 노드를 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 보내기 때문에 레코드의 데이터는 노드 범위 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-103">Because XML Bulk Load generates records as their nodes enter into scope and sends those records to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as their nodes exit scope, the data for the record must be present within the scope of the node.</span></span>  
  
 <span data-ttu-id="c23ed-104">**\<Customer>** **\<Order>** 요소를 사용 하 여 및 요소 (한 명의 고객에 게 여러 개의 주문을 놓을 수 있음) 간의 일 대 다 관계를 지정 하는 다음 XSD 스키마를 고려해 보십시오 `<sql:relationship>` .</span><span class="sxs-lookup"><span data-stu-id="c23ed-104">Consider the following XSD schema, in which the one-to-many relationship between **\<Customer>** and **\<Order>** elements (one customer can place many orders) is specified by using the `<sql:relationship>` element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="c23ed-105">**\<Customer>** 요소 노드가 범위에 들어가면 XML 대량 로드에서 고객 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-105">As the **\<Customer>** element node enters into scope, XML Bulk Load generates a customer record.</span></span> <span data-ttu-id="c23ed-106">이 레코드는 XML 대량 로드 읽기가 끝날 때까지 유지 **\</Customer>** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-106">This record stays until XML Bulk Load reads **\</Customer>**.</span></span> <span data-ttu-id="c23ed-107">요소 노드를 처리할 때 **\<Order>** XML 대량 로드는를 사용 하 여 `<sql:relationship>` 부모 요소에서 CustOrder 테이블의 customerid 외래 키 열 값을 가져옵니다 **\<Customer>** **\<Order>** .이 요소는 **customerid** 특성을 지정 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-107">In processing the **\<Order>** element node, XML Bulk Load uses `<sql:relationship>` to obtain the value of the CustomerID foreign key column of the CustOrder table from the **\<Customer>** parent element, because the **\<Order>** element does not specify the **CustomerID** attribute.</span></span> <span data-ttu-id="c23ed-108">즉 **\<Customer>** , 요소를 정의할 때를 지정 하기 전에 스키마에 **CustomerID** 특성을 지정 해야 합니다 `<sql:relationship>` .</span><span class="sxs-lookup"><span data-stu-id="c23ed-108">This means that in defining the **\<Customer>** element, you must specify the **CustomerID** attribute in the schema before you specify `<sql:relationship>`.</span></span> <span data-ttu-id="c23ed-109">그렇지 않고 **\<Order>** 요소가 범위에 들어가면 Xml 대량 로드는 CustOrder 테이블에 대 한 레코드를 생성 하 고, Xml 대량 로드가 끝 태그에 도달 하면 **\</Order>** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CustomerID 외래 키 열 값을 사용 하지 않고에 레코드를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-109">Otherwise, when an **\<Order>** element enters into scope, XML Bulk Load generates a record for the CustOrder table, and when the XML Bulk Load reaches the **\</Order>** end tag, it sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] without the CustomerID foreign key column value.</span></span>  
  
 <span data-ttu-id="c23ed-110">이 예에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-110">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="c23ed-111">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="c23ed-111">To test a working sample</span></span>  
  
1.  <span data-ttu-id="c23ed-112">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-112">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="c23ed-113">다음 예제 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-113">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  <span data-ttu-id="c23ed-114">XML 대량 로드를 실행하려면 다음 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VBScript(Visual Basic Scripting Edition) 예제를 MySample.vbs로 저장한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-114">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as MySample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     <span data-ttu-id="c23ed-115">그러면 XML 대량 로드가 CustOrder 테이블의 CustomerID 외래 키 열에 NULL 값을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-115">The result is that XML Bulk Load inserts a NULL value in the CustomerID foreign key column of the CustOrder table.</span></span> <span data-ttu-id="c23ed-116">자식 요소가 자식 요소 앞에 나타나도록 XML 샘플 데이터를 수정 하는 경우 **\<CustomerID>** **\<Order>** 예상 결과를 얻을 수 있습니다. Xml 대량 로드는 지정 된 외래 키 값을 열에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-116">If you revise the XML sample data so that the **\<CustomerID>** child element appears before the **\<Order>** child element, you get the expected result: XML Bulk Load inserts the specified foreign key value into the column.</span></span>  
  
 <span data-ttu-id="c23ed-117">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="c23ed-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  
