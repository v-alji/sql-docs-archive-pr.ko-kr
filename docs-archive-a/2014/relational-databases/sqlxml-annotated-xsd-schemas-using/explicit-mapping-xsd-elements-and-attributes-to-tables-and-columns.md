---
title: 테이블 및 열에 대 한 XSD 요소 및 특성의 명시적 매핑 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: rothja
ms.author: jroth
ms.openlocfilehash: f3400682b5f28835ca039912aab058691929a6c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647549"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="f5b38-102">테이블 및 열에 대한 XSD 요소 및 특성의 명시적 매핑(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f5b38-102">Explicit Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="f5b38-103">XSD 스키마를 사용하여 관계형 데이터베이스의 XML 뷰를 제공할 때는 스키마의 요소 및 특성을 데이터베이스의 테이블 및 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-103">When using an XSD schema to provide an XML view of the relational database , the elements and attributes of the schema must be mapped to tables and columns of the database.</span></span> <span data-ttu-id="f5b38-104">데이터베이스 테이블/뷰의 행은 XML 문서의 요소에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-104">The rows in the database table/view will map to elements in the XML document.</span></span> <span data-ttu-id="f5b38-105">데이터베이스의 열 값은 특성 또는 요소에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-105">The column values in the database map to attributes or elements.</span></span>  
  
 <span data-ttu-id="f5b38-106">XPath 쿼리는 주석이 추가된 XSD 스키마에 대해 지정되며 스키마의 요소 및 특성에 대한 데이터는 매핑되는 테이블 및 열에서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-106">When XPath queries are specified against the annotated XSD schema, the data for the elements and attributes in the schema is retrieved from the tables and columns to which they map.</span></span> <span data-ttu-id="f5b38-107">데이터베이스에서 단일 값을 얻으려면 XSD 스키마에 지정된 매핑에 관계 및 필드 사양이 모두 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-107">To obtain a single value from the database, the mapping specified in the XSD schema must have both relation and field specification.</span></span> <span data-ttu-id="f5b38-108">요소/특성의 이름이 매핑되는 테이블/뷰 또는 열 이름과 다른 경우 `sql:relation` 및 `sql:field` 주석을 사용하여 XML 문서의 요소 또는 특성과 데이터베이스의 테이블(뷰) 또는 열 간의 매핑을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-108">If the name of an element/attribute is not the same name as the table/view or column name to which it maps, the `sql:relation` and `sql:field` annotations are used to specify the mapping between an element or attribute in an XML document and the table (view) or column in a database.</span></span>  
  
## <a name="sql-relation"></a><span data-ttu-id="f5b38-109">sql-relation</span><span class="sxs-lookup"><span data-stu-id="f5b38-109">sql-relation</span></span>  
 <span data-ttu-id="f5b38-110">`sql:relation` 주석은 XSD 스키마의 XML 노드를 데이터베이스 테이블에 매핑하기 위해 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-110">The `sql:relation` annotation is added to map an XML node in the XSD schema to a database table.</span></span> <span data-ttu-id="f5b38-111">테이블(뷰)의 이름은 `sql:relation` 주석의 값으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-111">The name of a table (view) is specified as the value of the `sql:relation` annotation.</span></span>  
  
 <span data-ttu-id="f5b38-112">요소에 `sql:relation`을 지정하면 이 주석의 범위가 해당 요소의 복합 유형 정의에 기술된 모든 특성 및 자식 요소에 적용되므로 주석을 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-112">When `sql:relation` is specified on an element, the scope of this annotation applies to all attributes and child elements that are described in the complex type definition of that element, therefore providing a shortcut in writing annotations.</span></span>  
  
 <span data-ttu-id="f5b38-113">`sql:relation`주석은에서 유효한 식별자가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML에서 유효 하지 않은 경우에도 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-113">The `sql:relation` annotation is also useful when identifiers that are valid in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not valid in XML.</span></span> <span data-ttu-id="f5b38-114">예를 들어 "Order Details"는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 유효한 테이블 이름이지만 XML에서는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-114">For example, "Order Details" is a valid table name in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but not in XML.</span></span> <span data-ttu-id="f5b38-115">이 경우 `sql:relation` 주석을 사용하여 매핑을 지정할 수 있습니다. 예를 들어 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-115">In such cases, the `sql:relation` annotation can be used to specify the mapping, for example:</span></span>  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a><span data-ttu-id="f5b38-116">sql-field</span><span class="sxs-lookup"><span data-stu-id="f5b38-116">sql-field</span></span>  
 <span data-ttu-id="f5b38-117">`sql-field` 주석은 요소 또는 특성을 데이터베이스 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-117">The `sql-field` annotation maps an element or attribute to a database column.</span></span> <span data-ttu-id="f5b38-118">`sql:field` 주석은 스키마의 XML 노드를 데이터베이스 열에 매핑하기 위해 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-118">The `sql:field` annotation is added to map an XML node in the schema to a database column.</span></span> <span data-ttu-id="f5b38-119">비어 있는 콘텐츠 요소에는 `sql:field`를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-119">You cannot specify `sql:field` on an empty content element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f5b38-120">예</span><span class="sxs-lookup"><span data-stu-id="f5b38-120">Examples</span></span>  
 <span data-ttu-id="f5b38-121">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-121">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="f5b38-122">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5b38-122">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a><span data-ttu-id="f5b38-123">A.</span><span class="sxs-lookup"><span data-stu-id="f5b38-123">A.</span></span> <span data-ttu-id="f5b38-124">sql:relation 및 sql:field 주석 지정</span><span class="sxs-lookup"><span data-stu-id="f5b38-124">Specifying the sql:relation and sql:field annotations</span></span>  
 <span data-ttu-id="f5b38-125">이 예에서 XSD 스키마는 **\<Contact>** **\<FName>** 및 **\<LName>** 자식 요소와 **ContactID** 특성을 포함 하는 복합 형식의 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-125">In this example, the XSD schema consists of an **\<Contact>** element of complex type with **\<FName>** and **\<LName>** child elements and the **ContactID** attribute.</span></span>  
  
 <span data-ttu-id="f5b38-126">`sql:relation`주석은 **\<Contact>** AdventureWorks 데이터베이스의 Person. Contact 테이블에 요소를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-126">The `sql:relation` annotation maps the **\<Contact>** element to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="f5b38-127">`sql:field`주석은 **\<FName>** 요소를 FirstName 열에 매핑하고 요소를 **\<LName>** LastName 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-127">The `sql:field` annotation maps the **\<FName>** element to the FirstName column and the **\<LName>** element to the LastName column.</span></span>  
  
 <span data-ttu-id="f5b38-128">**ContactID** 특성에는 주석이 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-128">No annotation is specified for the **ContactID** attribute.</span></span> <span data-ttu-id="f5b38-129">따라서 이름이 같은 열에 특성을 매핑하는 기본 매핑이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-129">This results in a default mapping of the attribute to the column with the same name.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="f5b38-130">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f5b38-130">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="f5b38-131">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="f5b38-132">파일을 MySchema-annotated.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-132">Save the file as MySchema-annotated.xml.</span></span>  
  
2.  <span data-ttu-id="f5b38-133">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-133">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="f5b38-134">MySchema-annotated.xml을 저장한 디렉터리와 같은 디렉터리에 MySchema-annotatedT.xml 이름으로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-134">Save the file as MySchema-annotatedT.xml in the same directory where you saved MySchema-annotated.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f5b38-135">매핑 스키마(MySchema-annotated.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-135">The directory path specified for the mapping schema (MySchema-annotated.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f5b38-136">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  <span data-ttu-id="f5b38-137">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="f5b38-138">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5b38-138">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f5b38-139">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f5b38-139">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
