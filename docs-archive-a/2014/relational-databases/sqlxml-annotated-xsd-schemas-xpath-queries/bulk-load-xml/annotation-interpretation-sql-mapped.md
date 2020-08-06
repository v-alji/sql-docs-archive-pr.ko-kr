---
title: 'sql: 매핑됨 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2cbccf271e069cd87860af672fed6c4bab462b41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650880"
---
# <a name="sqlmapped-sqlxml-40"></a><span data-ttu-id="6b494-102">sql:mapped(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6b494-102">sql:mapped (SQLXML 4.0)</span></span>
  <span data-ttu-id="6b494-103">XML 대량 로드는 `sql:mapped` XSD 스키마의 주석을 예상 대로 처리 합니다. 즉, 매핑 스키마가 `sql:mapped="false"` 요소 또는 특성에 대해를 지정 하는 경우 Xml 대량 로드는 관련 데이터를 해당 열에 저장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-103">XML Bulk Load processes the `sql:mapped` annotation in the XSD schema as expected-that is, if the mapping schema specifies `sql:mapped="false"` for any element or attribute, XML Bulk Load does not attempt to store the associated data in the corresponding column.</span></span>  
  
 <span data-ttu-id="6b494-104">XML 대량 로드는 스키마에 기술되지 않았거나 XSD 스키마에서 `sql:mapped="false"`로 주석이 지정되어 있어 매핑되지 않은 요소 및 특성을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-104">XML Bulk Load ignores elements and attributes that are not mapped (either because they are not described in the schema, or because they are annotated in the XSD schema with `sql:mapped="false"`).</span></span> <span data-ttu-id="6b494-105">매핑되지 않은 모든 데이터는 `sql:overflow-field`를 사용하여 지정된 오버플로 열에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-105">All unmapped data goes into the overflow column, if such a column is specified by using `sql:overflow-field`.</span></span>  
  
 <span data-ttu-id="6b494-106">예를 들어 다음 XSD 스키마를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b494-106">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="6b494-107">**HomePhone** 특성은를 지정 하므로 `sql:mapped="false"` XML 대량 로드는이 특성을 해당 열에 매핑하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-107">Because the **HomePhone** attribute specifies `sql:mapped="false"`, XML Bulk Load does not map this attribute to the corresponding column.</span></span> <span data-ttu-id="6b494-108">XSD 스키마는 XML 대량 로드에서이 소비 되지 않은 데이터를 저장 하는 오버플로 열 (**OverflowColumn**)을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-108">The XSD schema identifies an overflow column (**OverflowColumn**) in which XML Bulk Load stores this unconsumed data.</span></span>  
  
### <a name="to-test-a-working-sample"></a><span data-ttu-id="6b494-109">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6b494-109">To test a working sample</span></span>  
  
1.  <span data-ttu-id="6b494-110">**Tempdb** 데이터베이스에 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-110">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  <span data-ttu-id="6b494-111">이 예에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-111">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="6b494-112">다음 예제 XML 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-112">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="6b494-113">XML 대량 로드를 실행하려면 이 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VBScript(Visual Basic Scripting Edition) 예를 Sample.vbs로 저장한 다음 이 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-113">To execute XML Bulk Load, save and execute this [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example as Sample.vbs:</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 <span data-ttu-id="6b494-114">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="6b494-114">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
