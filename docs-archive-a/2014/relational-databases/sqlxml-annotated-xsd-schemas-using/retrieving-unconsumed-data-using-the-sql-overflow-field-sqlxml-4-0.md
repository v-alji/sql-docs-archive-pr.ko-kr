---
title: 'Sql: 오버플로 필드를 사용 하 여 사용 되지 않은 데이터 검색 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: rothja
ms.author: jroth
ms.openlocfilehash: 796fda9428954c5f18c5d37b353de9fd4122551e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659892"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a><span data-ttu-id="336ab-102">sql:overflow-field를 사용하여 사용되지 않은 데이터 검색(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="336ab-102">Retrieving Unconsumed Data Using the sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="336ab-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML 함수를 사용하여 XML 문서에서 데이터베이스로 레코드를 삽입하는 경우 원본 XML 문서에서 사용되지 않은 모든 데이터를 한 열에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-103">When records are inserted in a database from an XML document by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML function, all the unconsumed data from the source XML document can be stored in a column.</span></span> <span data-ttu-id="336ab-104">주석 스키마를 사용하여 데이터베이스에서 데이터를 검색할 때는 `sql:overflow-field` 특성을 지정하여 오버플로 데이터가 저장되어 있는 테이블 열을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-104">When you retrieve data from a database by using annotated schemas, you can specify the `sql:overflow-field` attribute to identify the column in the table in which the overflow data is stored.</span></span> <span data-ttu-id="336ab-105">`sql:overflow-field`에서 특성을 지정할 수 있습니다 **\<element>** .</span><span class="sxs-lookup"><span data-stu-id="336ab-105">The `sql:overflow-field` attribute can be specified on **\<element>**.</span></span>  
  
 <span data-ttu-id="336ab-106">이 데이터는 다음과 같은 방법으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-106">This data is then retrieved in these ways:</span></span>  
  
-   <span data-ttu-id="336ab-107">오버플로 열에 저장된 특성은 `sql:overflow-field` 주석이 포함된 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-107">Attributes stored in the overflow column are added to the element that contains the `sql:overflow-field` annotation.</span></span>  
  
-   <span data-ttu-id="336ab-108">데이터베이스의 오버플로 열에 저장된 자식 요소와 해당 하위 항목은 스키마에 명시적으로 지정된 내용에 따라 자식 요소로 추가되며,</span><span class="sxs-lookup"><span data-stu-id="336ab-108">The child elements and their descendents, stored in the overflow column in the database, are added as child elements following the content that is explicitly specified in the schema.</span></span> <span data-ttu-id="336ab-109">이때 순서는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-109">(No order is preserved.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="336ab-110">예</span><span class="sxs-lookup"><span data-stu-id="336ab-110">Examples</span></span>  
 <span data-ttu-id="336ab-111">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-111">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="336ab-112">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="336ab-112">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a><span data-ttu-id="336ab-113">A.</span><span class="sxs-lookup"><span data-stu-id="336ab-113">A.</span></span> <span data-ttu-id="336ab-114">요소에 Specifying sql:overflow-field 지정</span><span class="sxs-lookup"><span data-stu-id="336ab-114">Specifying sql:overflow-field for an element</span></span>  
 <span data-ttu-id="336ab-115">이 예에서는 다음 스크립트를 실행한 결과 tempdb 데이터베이스에 Customers2라는 테이블이 생성되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-115">This example assumes that the following script has been run so that a table named Customers2 exists in the tempdb database:</span></span>  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 <span data-ttu-id="336ab-116">또한 tempdb 데이터베이스에 대 한 가상 디렉터리를 만들어야 하며 `template` "template" 이라는 형식의 템플릿 가상 이름도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-116">In addition, you must create a virtual directory for the tempdb database-and a template virtual name of `template` type named "template".</span></span>  
  
 <span data-ttu-id="336ab-117">다음 예에서 매핑 스키마는 Customers2 테이블의 AddressOverflow 열에 저장되어 있는 사용되지 않은 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-117">In the following example, the mapping schema retrieves the unconsumed data that is stored in the AddressOverflow column of the Customers2 table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="336ab-118">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="336ab-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="336ab-119">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="336ab-120">파일을 Overflow.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-120">Save the file as Overflow.xml.</span></span>  
  
2.  <span data-ttu-id="336ab-121">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="336ab-122">파일을 Overflow.xml을 저장한 디렉터리와 같은 디렉터리에 OverflowT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-122">Save the file as OverflowT.xml in the same directory where you saved Overflow.xml.</span></span> <span data-ttu-id="336ab-123">템플릿의 쿼리는 Customers2 테이블의 레코드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-123">The query in the template selects the records in the Customers2 table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="336ab-124">매핑 스키마(Overflow.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-124">The directory path specified for the mapping schema (Overflow.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="336ab-125">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  <span data-ttu-id="336ab-126">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="336ab-127">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="336ab-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="336ab-128">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="336ab-128">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
