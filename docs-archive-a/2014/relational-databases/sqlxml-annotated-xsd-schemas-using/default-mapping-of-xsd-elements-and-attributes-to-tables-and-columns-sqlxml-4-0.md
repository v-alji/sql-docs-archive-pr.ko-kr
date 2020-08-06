---
title: 테이블 및 열에 대 한 XSD 요소 및 특성의 기본 매핑 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bccec2413e8a0a6e13283a0f3e5f63ab61e934b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650897"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="0767c-102">테이블 및 열에 대한 XSD 요소 및 특성의 기본 매핑(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0767c-102">Default Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="0767c-103">기본적으로 주석이 추가된 XSD 스키마에서 복합 유형의 요소는 지정된 데이터베이스에 있는 같은 이름의 테이블(뷰)에 매핑되고 단순 유형의 요소 또는 특성은 테이블에 있는 같은 이름의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-103">By default, an element of complex type in an XSD annotated schema maps to the table (view) with the same name in the specified database, and an element or attribute of simple type maps to the column with the same name in the table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0767c-104">예</span><span class="sxs-lookup"><span data-stu-id="0767c-104">Examples</span></span>  
 <span data-ttu-id="0767c-105">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-105">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="0767c-106">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0767c-106">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-default-mapping"></a><span data-ttu-id="0767c-107">A.</span><span class="sxs-lookup"><span data-stu-id="0767c-107">A.</span></span> <span data-ttu-id="0767c-108">기본 매핑 지정</span><span class="sxs-lookup"><span data-stu-id="0767c-108">Specifying default mapping</span></span>  
 <span data-ttu-id="0767c-109">이 예에서는 XSD 스키마에 주석이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-109">In this example, no annotations are specified in the XSD schema.</span></span> <span data-ttu-id="0767c-110">**\<Person.Contact>** 요소는 복합 유형 이므로 기본적으로 AdventureWorks 데이터베이스의 Person. Contact 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-110">The **\<Person.Contact>** element is of complex type and, therefore, maps by default to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="0767c-111">요소의 모든 특성 (ContactID, FirstName, LastName) **\<Person.Contact>** 은 단순 형식 이며 기본적으로 Person. Contact 테이블에서 이름이 같은 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-111">All the attributes (ContactID, FirstName, LastName) of the **\<Person.Contact>** element are of simple type and map by default to columns with the same names in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="0767c-112">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="0767c-112">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="0767c-113">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-113">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0767c-114">파일을 MySchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-114">Save the file as MySchema.xml.</span></span>  
  
2.  <span data-ttu-id="0767c-115">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-115">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="0767c-116">파일을 MySchema.xml을 저장한 디렉터리와 같은 디렉터리에 MySchemaT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-116">Save the file as MySchemaT.xml in the same directory where you saved MySchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0767c-117">매핑 스키마(MySchema.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-117">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0767c-118">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  <span data-ttu-id="0767c-119">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0767c-120">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0767c-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0767c-121">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-121">Here is the partial result set:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a><span data-ttu-id="0767c-122">B.</span><span class="sxs-lookup"><span data-stu-id="0767c-122">B.</span></span> <span data-ttu-id="0767c-123">XML 요소를 데이터베이스 열에 매핑</span><span class="sxs-lookup"><span data-stu-id="0767c-123">Mapping an XML element to a database column</span></span>  
 <span data-ttu-id="0767c-124">이 예에서는 주석이 사용되지 않기 때문에 기본 매핑이 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-124">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="0767c-125">**\<Person.Contact>** 요소는 복합 유형이 며 데이터베이스에 있는 같은 이름의 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-125">The **\<Person.Contact>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="0767c-126">요소 **\<FirstName>** 와 **\<LastName>** 및 **EmployeeID** 특성은 단순 유형 이므로 같은 이름의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-126">The elements **\<FirstName>** and **\<LastName>** and the **EmployeeID** attribute are of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="0767c-127">이 예와 이전 예의 유일한 차이점은 요소가 FirstName 및 LastName 필드 매핑에 사용된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-127">The only difference between this and the previous example are that elements are used for mapping the FirstName and LastName fields.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="0767c-128">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="0767c-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="0767c-129">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0767c-130">파일을 MySchemaElements.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-130">Save the file as MySchemaElements.xml.</span></span>  
  
2.  <span data-ttu-id="0767c-131">다음 템플릿(MySchemaElementsT.xml)을 만들어 이전 단계에서 사용한 디렉터리와 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-131">Create the following template (MySchemaElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0767c-132">매핑 스키마에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-132">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0767c-133">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  <span data-ttu-id="0767c-134">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0767c-135">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0767c-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0767c-136">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-136">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a><span data-ttu-id="0767c-137">C.</span><span class="sxs-lookup"><span data-stu-id="0767c-137">C.</span></span> <span data-ttu-id="0767c-138">XML 요소를 XML 데이터 형식 열에 매핑</span><span class="sxs-lookup"><span data-stu-id="0767c-138">Mapping an XML element to an XML data type column</span></span>  
 <span data-ttu-id="0767c-139">이 예에서는 주석이 사용되지 않기 때문에 기본 매핑이 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-139">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="0767c-140">**\<Production.ProductModel>** 요소는 복합 유형이 며 데이터베이스에 있는 같은 이름의 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-140">The **\<Production.ProductModel>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="0767c-141">**제품 Modelid** 특성은 단순 유형 이므로 같은 이름의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-141">The **ProductModelID** attribute is of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="0767c-142">이 예와 이전 예의 유일한 차이점은 **\<Instructions>** 요소는 `xml` 형식을 사용 하 여 데이터 형식을 사용 하는 열에 매핑되는 것입니다 `xsd:anyType` .</span><span class="sxs-lookup"><span data-stu-id="0767c-142">The only difference between this and the previous examples is that the **\<Instructions>** element is mapping to a column that uses the `xml` data type by using the `xsd:anyType` type.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="0767c-143">`xml` 데이터 형식은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-143">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="0767c-144">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="0767c-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="0767c-145">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-145">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0767c-146">파일을 MySchemaXmlAnyElements.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-146">Save the file as MySchemaXmlAnyElements.xml.</span></span>  
  
2.  <span data-ttu-id="0767c-147">다음 템플릿(MySchemaXmlAnyElementsT.xml)을 만들어 이전 단계에서 사용한 디렉터리와 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-147">Create the following template (MySchemaXmlAnyElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0767c-148">매핑 스키마에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-148">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0767c-149">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-149">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  <span data-ttu-id="0767c-150">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-150">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0767c-151">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0767c-151">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0767c-152">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="0767c-152">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0767c-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0767c-153">See Also</span></span>  
 <span data-ttu-id="0767c-154">[SQLXML 4.0 &#40;주석이 추가 된 스키마 보안 고려 사항&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="0767c-154">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="0767c-155">[XML 데이터&#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0767c-155">[XML Data &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span></span>  
 [<span data-ttu-id="0767c-156">SQLXML 4.0의 xml 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="0767c-156">xml Data Type Support in SQLXML 4.0</span></span>](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
