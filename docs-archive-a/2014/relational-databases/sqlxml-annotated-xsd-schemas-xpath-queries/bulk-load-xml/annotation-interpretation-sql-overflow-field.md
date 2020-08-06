---
title: 'sql: 오버플로 필드 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: f005182b-6151-432d-ab22-3bc025742cd3
author: rothja
ms.author: jroth
ms.openlocfilehash: ea52eb642964844a03304d082632c2b7157f723b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652754"
---
# <a name="sqloverflow-field-sqlxml-40"></a><span data-ttu-id="0c7cc-102">sql:overflow-field(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0c7cc-102">sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="0c7cc-103">스키마에서 열을 오버플로 열로 식별하여 XML 문서에서 사용되지 않은 데이터를 모두 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-103">In a schema, you can identify a column as an overflow column to receive all unconsumed data from the XML document.</span></span> <span data-ttu-id="0c7cc-104">이 열은 `sql:overflow-field` 주석을 사용하여 스키마에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-104">This column is specified in the schema by using the `sql:overflow-field` annotation.</span></span> <span data-ttu-id="0c7cc-105">오버플로 열을 여러 개 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-105">It is possible to have multiple overflow columns.</span></span>  
  
 <span data-ttu-id="0c7cc-106">`sql:overflow-field` 주석이 정의되어 있는 XML 노드(요소 또는 특성)가 범위에 들어오면 오버플로 열이 활성화되어 사용되지 않은 데이터를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-106">Whenever an XML node (element or attribute) for which there is a `sql:overflow-field` annotation defined enters into scope, the overflow column is activated and receives unconsumed data.</span></span> <span data-ttu-id="0c7cc-107">노드가 범위를 벗어나면 오버플로 열이 더 이상 활성화되지 않고 XML 대량 로드를 통해 이전 오버플로 필드(있는 경우)가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-107">When the node goes out of scope, the overflow column is no longer active and XML Bulk Load makes the previous overflow field (if any) active.</span></span>  
  
 <span data-ttu-id="0c7cc-108">XML 대량 로드에서는 오버플로 열에 데이터를 저장할 때 `sql:overflow-field`가 정의된 부모 요소의 여는 태그와 닫는 태그도 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-108">As it stores data in the overflow column, XML Bulk Load also stores the opening and closing tags of the parent element for which `sql:overflow-field` is defined.</span></span>  
  
 <span data-ttu-id="0c7cc-109">예를 들어, 다음 스키마는 및 요소에 대해 설명 합니다 **\<Customers>** **\<CustOrder>** .</span><span class="sxs-lookup"><span data-stu-id="0c7cc-109">For example, the following schema describes the **\<Customers>** and **\<CustOrder>** elements.</span></span> <span data-ttu-id="0c7cc-110">이러한 각 요소는 오버플로 열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-110">Each of these elements identifies an overflow column:</span></span>  
  
```  
<?xml version="1.0" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
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
 <xsd:element name="ROOT" sql:is-constant="1">  
  <xsd:complexType>  
    <xsd:sequence>   
      <xsd:element name="Customers"   
                   sql:relation="Cust"  
                   sql:overflow-field="OverflowColumn">  
        <xsd:complexType>  
             <xsd:sequence>   
             <xsd:element name="CustomerID" type="xsd:integer"/>  
             <xsd:element name="CompanyName"  type="xsd:string"/>  
             <xsd:element name="City" type="xsd:string"/>  
             <xsd:element name="Order"  
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder"  
                          sql:overflow-field="OverflowColumn">  
               <xsd:complexType>  
                 <xsd:attribute name="OrderID"/>  
                 <xsd:attribute name="CustomerID"/>  
               </xsd:complexType>  
             </xsd:element>  
          </xsd:sequence>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="0c7cc-111">스키마에서 **\<Customer>** 요소는 Cust 테이블에 매핑되고 **\<Order>** 요소는 CustOrder 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-111">In the schema, the **\<Customer>** element maps to the Cust table and the **\<Order>** element maps to the CustOrder table.</span></span>  
  
 <span data-ttu-id="0c7cc-112">**\<Customer>** 및 요소는 모두 **\<Order>** 오버플로 열을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-112">Both the **\<Customer>** and **\<Order>** elements identify an overflow column.</span></span> <span data-ttu-id="0c7cc-113">따라서 XML 대량 로드는 요소에 있는 모든 자식 요소와 특성을 **\<Customer>** Cust 테이블의 오버플로 열에 저장 하 고 **\<Order>** CustOrder 테이블의 오버플로 열에서 요소의 소비 되지 않은 모든 자식 요소와 특성을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-113">Thus, XML Bulk Load saves all the unconsumed child elements and attributes of the **\<Customer>** element in the overflow column of the Cust table, and all the unconsumed child elements and attributes of the **\<Order>** element in the overflow column of the CustOrder table.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="0c7cc-114">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="0c7cc-114">To test a working sample</span></span>  
  
1.  <span data-ttu-id="0c7cc-115">이 예에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-115">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="0c7cc-116">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-116">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
              CustomerID     int         PRIMARY KEY,  
              CompanyName    varchar(20) NOT NULL,  
              City           varchar(20) DEFAULT 'Seattle',  
              OverflowColumn nvarchar(200))  
    GO  
    CREATE TABLE CustOrder (  
              OrderID        int         PRIMARY KEY,  
              CustomerID     int         FOREIGN KEY REFERENCES  
                                              Cust(CustomerID),  
              OverflowColumn nvarchar(200))  
    GO  
    ```  
  
3.  <span data-ttu-id="0c7cc-117">다음 예제 XML 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-117">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
          <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
     </Customers>  
     <Customers>  
       <CustomerID>1112</CustomerID>  
       <CompanyName>Toms Spezialitten</CompanyName>  
       <City><![CDATA[LA]]> </City>  
       <xyz><address>111 Maple, Seattle</address></xyz>     
       <Order OrderID="3" />  
     </Customers>  
       <Customers>  
       <CustomerID>1113</CustomerID>  
       <CompanyName>Victuailles en stock</CompanyName>  
       <Order OrderID="4" />  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="0c7cc-118">XML 대량 로드를 실행하려면 이 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VBScript(Visual Basic Scripting Edition) 예를 Sample.vbs로 저장한 다음 이 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7cc-118">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
