---
title: 'sql: limit 필드 및 sql: limit 값 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: 402c21cf-9566-463f-a928-f94270c11db3
author: rothja
ms.author: jroth
ms.openlocfilehash: a6d0383aece7a2bafa5d21b76d0c4da9cb057984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650881"
---
# <a name="sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="d793a-102">sql:limit-field 및 sql:limit-value (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d793a-102">sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="d793a-103">XML 대량 로드는 해당 정의별로 `sql:limit-field` 및 `sql:limit-value` 주석을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-103">XML Bulk Load processes the `sql:limit-field` and `sql:limit-value` annotations per their definition.</span></span> <span data-ttu-id="d793a-104">자세한 내용은 [sql을 사용 하 여 값 필터링: limit 필드 및 sql: limit 값 &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d793a-104">For more information, see [Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md).</span></span>  
  
 <span data-ttu-id="d793a-105">예를 들어 데이터베이스에 다음과 같은 테이블이 포함된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-105">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="d793a-106">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="d793a-106">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="d793a-107">Addresses (CustomerID, StreetAddress, AddressType)</span><span class="sxs-lookup"><span data-stu-id="d793a-107">Addresses (CustomerID, StreetAddress, AddressType)</span></span>  
  
 <span data-ttu-id="d793a-108">고객은 많은 주소를 가질 수 있으며, 각 주소에 주소 유형(예: 배달 주소 또는 요금 청구서 주소)이 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-108">A customer can have many addresses, and each address has an address type associated with it (for example, a shipping address or a billing address).</span></span>  
  
 <span data-ttu-id="d793a-109">이제 다음과 같은 주석이 추가된 XSD 스키마에 지정된 이러한 테이블의 XML 뷰를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="d793a-109">Now consider this XML view of these tables as specified in the following annotated XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Address"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
        <xsd:attribute name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
        <xsd:attribute name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="d793a-110">이 스키마와 XML 데이터를 받으면 XML 대량 로드는 BillTo 특성에 지정된 값을 CustAddress 테이블의 StreetAddress 열에 삽입하고 "billing" 값을 AddressType 열에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-110">Upon receiving this schema and XML data, XML Bulk Load inserts the value that is specified for the BillTo attribute into the StreetAddress column of the CustAddress table along with the "billing" value for the AddressType column.</span></span>  
  
 <span data-ttu-id="d793a-111">마찬가지로, XML 대량 로드는 ShipTo 특성에 지정된 값을 StreetAddress 열에 삽입하고 "shipping" 값을 AddressType 열에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-111">Similarly, XML Bulk Load inserts the value that is specified for the ShipTo attribute into the StreetAddress column along with the "shipping" value in the AddressType column.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="d793a-112">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d793a-112">To test a working sample</span></span>  
  
1.  <span data-ttu-id="d793a-113">이 예에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-113">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="d793a-114">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-114">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Customer(  
                     CustomerID     int         PRIMARY KEY,  
                     CompanyName    varchar(20) NOT NULL)  
    GO  
    CREATE TABLE Address(  
                      CustomerID     int        FOREIGN KEY REFERENCES   
                                                 Customer(CustomerID),   
                      StreetAddress  varchar(50),  
                      AddressType    varchar(10))  
    GO  
    ```  
  
3.  <span data-ttu-id="d793a-115">다음 예제 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-115">Save the following sample data as SampleXMLData.xml:</span></span>  
  
    ```  
    <Customer CustomerID="1111" CompanyName="Sean Chai" City="NY"   
                 BillTo="111 Maple (Billing) "   
                 ShipTo="111 Maple (Shipping)" />  
    <Customer CustomerID="1112" CompanyName="Dont Know" City="LA"   
                 BillTo="222 Spruce (Billing)"   
                 ShipTo="222 Spruce (Shipping)" />  
    ```  
  
4.  <span data-ttu-id="d793a-116">XML 대량 로드를 실행하려면 이 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VBScript(Visual Basic Scripting Edition) 예를 Sample.vbs로 저장한 다음 이 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-116">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.XMLFragment = True  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 <span data-ttu-id="d793a-117">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="d793a-117">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="CompanyName" />  
    <AttributeType name="BillTo" />  
    <AttributeType name="ShipTo" />  
  
    <attribute type="CustomerID" />  
    <attribute type="CompanyName" />  
    <attribute type="BillTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="billing"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                        key="CustomerID"  
                        key-relation="Customer"  
                        foreign-relation="Address"  
                        foreign-key="CustomerID" />  
    </attribute>  
    <attribute type="ShipTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="shipping"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                     key="CustomerID"  
                     key-relation="Customer"  
                     foreign-relation="Address"  
                     foreign-key="CustomerID" />  
    </attribute>  
</ElementType>  
</Schema>  
```  
  
  
