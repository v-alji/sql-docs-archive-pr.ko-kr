---
title: '예제: XMLDATA 및 XMLSCHEMA 옵션을 사용하여 결과로 스키마 요청 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, requesting schema example
- RAW mode, with XMLDATA and XMLSCHEMA
ms.assetid: 3504ca38-be66-42b2-8dab-f499c9584840
author: rothja
ms.author: jroth
ms.openlocfilehash: af244e3436df4d8665079ce20fb749a44021fe04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739627"
---
# <a name="example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options"></a><span data-ttu-id="56f06-102">예제: XMLDATA 및 XMLSCHEMA 옵션을 사용하여 결과로 스키마 요청</span><span class="sxs-lookup"><span data-stu-id="56f06-102">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>
  <span data-ttu-id="56f06-103">다음 쿼리는 문서 구조를 설명하는 XMLDATA 스키마를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-103">The following query returns the XML-DATA schema that describes the document structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56f06-104">예제</span><span class="sxs-lookup"><span data-stu-id="56f06-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLDATA  
GO  
```  
  
 <span data-ttu-id="56f06-105">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-105">This is the result:</span></span>  
  
```  
<Schema name="Schema1" xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="row" content="empty" model="closed">  
    <AttributeType name="ProductModelID" dt:type="i4" />  
    <AttributeType name="Name" dt:type="string" />  
    <attribute type="ProductModelID" />  
    <attribute type="Name" />  
  </ElementType>  
</Schema>  
<row xmlns="x-schema:#Schema1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="x-schema:#Schema1" ProductModelID="119" Name="Bike Wash" />  
```  
  
> [!NOTE]
>  <span data-ttu-id="56f06-106"><`Schema`>는 네임스페이스로 선언되었습니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-106">The <`Schema`> is declared as a namespace.</span></span> <span data-ttu-id="56f06-107">서로 다른 FOR XML 쿼리에서 여러 XML-Data 스키마를 요청할 때는 네임스페이스 충돌을 피하기 위해 쿼리가 실행될 때마다 네임스페이스 식별자(이 예제에서는 `Schema1` )가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-107">To avoid namespace collisions when multiple XML-Data schemas are requested in different FOR XML queries, the namespace identifier, `Schema1` in this example, changes with every query execution.</span></span> <span data-ttu-id="56f06-108">네임 스페이스 식별자는 **Schema_n_** 으로 구성 됩니다. 여기서 **_n_** 은 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-108">The namespace identifier is made up of **Schema_n_** where **_n_** is an integer.</span></span>  
  
 <span data-ttu-id="56f06-109">`XMLSCHEMA` 옵션을 지정하면 결과에 대해 XSD 스키마를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-109">By specifying the `XMLSCHEMA` option, you can request the XSD schema for the result.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA  
GO  
```  
  
 <span data-ttu-id="56f06-110">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-110">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="119" Name="Bike Wash" />  
  
```  
  
 <span data-ttu-id="56f06-111">대상 네임스페이스 URI를 FOR XML의 XMLSCHEMA에 대한 선택적 인수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-111">You can specify the target namespace URI as an optional argument to XMLSCHEMA in FOR XML.</span></span> <span data-ttu-id="56f06-112">이렇게 하면 스키마에 있는 지정된 대상 네임스페이스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-112">This returns the specified target namespace in the schema.</span></span> <span data-ttu-id="56f06-113">이 대상 네임스페이스는 쿼리를 실행할 때마다 같은 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-113">This target namespace remains the same every time you execute the query.</span></span> <span data-ttu-id="56f06-114">예를 들어 이전 쿼리에서 수정된 다음 쿼리에는 네임스페이스 URI인 `'urn:example.com'`이 인수로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-114">For example, the following modified version of the previous query includes the namespace URI, `'urn:example.com'`, as an argument.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA ('urn:example.com')  
GO  
```  
  
 <span data-ttu-id="56f06-115">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="56f06-115">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:example.com" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:example.com" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:example.com" ProductModelID="119" Name="Bike Wash" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="56f06-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56f06-116">See Also</span></span>  
 [<span data-ttu-id="56f06-117">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="56f06-117">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
