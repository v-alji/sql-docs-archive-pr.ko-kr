---
title: 쿼리에 주석이 추가 된 XSD 스키마 사용 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: rothja
ms.author: jroth
ms.openlocfilehash: c3038ea234f707da7a87a030cb4110510f5a77c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652720"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a><span data-ttu-id="cf3ea-102">쿼리에 주석이 추가된 XSD 스키마 사용(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="cf3ea-102">Using Annotated XSD Schemas in Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="cf3ea-103">템플릿에 XDR 스키마에 대한 XPath 쿼리를 지정하는 방식으로 주석이 추가된 스키마에 대해 쿼리를 지정하여 데이터베이스에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-103">You can specify queries against an annotated schema to retrieve data from the database by specifying XPath queries in a template against the XSD schema.</span></span>  
  
 <span data-ttu-id="cf3ea-104">**\<sql:xpath-query>** 요소를 사용 하면 주석이 추가 된 스키마에 정의 된 XML 뷰에 대해 XPath 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-104">The **\<sql:xpath-query>** element allows you to specify an XPath query against the XML view that is defined by the annotated schema.</span></span> <span data-ttu-id="cf3ea-105">XPath 쿼리가 실행 될 주석이 추가 된 스키마는 요소의 특성을 사용 하 여 식별 됩니다 `mapping-schema` **\<sql:xpath-query>** .</span><span class="sxs-lookup"><span data-stu-id="cf3ea-105">The annotated schema against which the XPath query is to be executed is identified by using the `mapping-schema` attribute of the **\<sql:xpath-query>** element.</span></span>  
  
 <span data-ttu-id="cf3ea-106">템플릿은 하나 이상의 쿼리를 포함하는 유효한 XML 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-106">Templates are valid XML documents that contain one or more queries.</span></span> <span data-ttu-id="cf3ea-107">FOR XML 및 XPath 쿼리는 문서 조각을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-107">The FOR XML and XPath queries return a document fragment.</span></span> <span data-ttu-id="cf3ea-108">템플릿은 문서 조각의 컨테이너 역할을 하며 단일 최상위 요소를 지정하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-108">Templates act as containers for the document fragments; templates thus provide a way to specify a single, top-level element.</span></span>  
  
 <span data-ttu-id="cf3ea-109">이 항목의 예에서는 템플릿을 통해 주석이 추가된 스키마에 대해 XPath 쿼리를 지정하여 데이터베이스에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-109">The examples in this topic use templates to specify an XPath query against an annotated schema to retrieve data from the database.</span></span>  
  
 <span data-ttu-id="cf3ea-110">예를 들어 주석이 추가된 다음 스키마를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-110">For example, consider this annotated schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="cf3ea-111">이해하기 쉽도록 이 XSD 스키마는 Schema2.xml이라는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-111">For the purpose of illustration, this XSD schema is stored in file named Schema2.xml.</span></span> <span data-ttu-id="cf3ea-112">따라서 다음 템플릿 파일(Schema2T.xml)에 주석이 추가된 스키마에 대한 XPath 쿼리를 지정할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-112">You could then have an XPath query against the annotated schema specified in the following template file (Schema2T.xml):</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="cf3ea-113">그러면 SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만들어서 사용하여 템플릿 파일의 일부로 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-113">You can then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the query as part of a template file.</span></span> <span data-ttu-id="cf3ea-114">자세한 내용은 [SQLXML 4.0&#41;에서 사용 되지 &#40;주석이 추가 된 XDR 스키마 ](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-114">For more information, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="using-inline-mapping-schemas"></a><span data-ttu-id="cf3ea-115">인라인 매핑 스키마 사용</span><span class="sxs-lookup"><span data-stu-id="cf3ea-115">Using Inline Mapping Schemas</span></span>  
 <span data-ttu-id="cf3ea-116">주석이 추가된 스키마를 템플릿에 직접 포함한 다음 이 템플릿에 인라인 스키마에 대한 XPath 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-116">An annotated schema can be included directly in a template, and then an XPath query can be specified in the template against the inline schema.</span></span> <span data-ttu-id="cf3ea-117">이 템플릿은 Updategram일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-117">The template can also be an updategram.</span></span>  
  
 <span data-ttu-id="cf3ea-118">템플릿에는 여러 개의 인라인 스키마가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-118">A template can include multiple inline schemas.</span></span> <span data-ttu-id="cf3ea-119">템플릿에 포함 된 인라인 스키마를 사용 하려면 요소에 고유한 값을 사용 하 여 **id** 특성을 지정한 **\<xsd:schema>** 다음 **#idvalue** 를 사용 하 여 인라인 스키마를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-119">To use an inline schema that is included in a template, specify the **id** attribute with a unique value on the **\<xsd:schema>** element, and then use **#idvalue** to reference the inline schema.</span></span> <span data-ttu-id="cf3ea-120">**Id** 특성은 XDR 스키마에 사용 되는 **sql: id** ({urn: 스키마-microsoft-com: xml) id)의 동작과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-120">The **id** attribute is identical in behavior to the **sql:id** ({urn:schemas-microsoft-com:xml-sql}id) used in XDR schemas.</span></span>  
  
 <span data-ttu-id="cf3ea-121">예를 들어 다음 템플릿에서는 주석이 추가된 두 개의 인라인 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-121">For example, the following template specifies two inline-annotated schemas:</span></span>  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 <span data-ttu-id="cf3ea-122">이 템플릿에서는 두 개의 XPath 쿼리도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-122">The template also specifies two XPath queries.</span></span> <span data-ttu-id="cf3ea-123">각 요소는 **\<xpath-query>** 특성을 지정 하 여 매핑 스키마를 고유 하 게 식별 합니다 `mapping-schema` .</span><span class="sxs-lookup"><span data-stu-id="cf3ea-123">Each of the **\<xpath-query>** elements uniquely identifies the mapping schema by specifying the `mapping-schema` attribute.</span></span>  
  
 <span data-ttu-id="cf3ea-124">템플릿에서 인라인 스키마를 지정 하는 경우 `sql:is-mapping-schema` 에도 요소에 주석을 지정 해야 합니다 **\<xsd:schema>** .</span><span class="sxs-lookup"><span data-stu-id="cf3ea-124">When you specify an inline schema in the template, the `sql:is-mapping-schema` annotation must also be specified on the **\<xsd:schema>** element.</span></span> <span data-ttu-id="cf3ea-125">`sql:is-mapping-schema`는 부울 값(0=false, 1=true)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-125">The `sql:is-mapping-schema` takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="cf3ea-126">**Sql: is 매핑-schema = "1"** 인 인라인 스키마는 인라인 주석이 추가 된 스키마로 처리 되 고 XML 문서에서 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-126">An inline schema with **sql:is-mapping-schema="1"** is treated as inline annotated schema and is not returned in the XML document.</span></span>  
  
 <span data-ttu-id="cf3ea-127">`sql:is-mapping-schema` 주석은 템플릿 네임스페이스 `urn:schemas-microsoft-com:xml-sql`에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-127">The `sql:is-mapping-schema` annotation belongs to the template namespace `urn:schemas-microsoft-com:xml-sql`.</span></span>  
  
 <span data-ttu-id="cf3ea-128">이 예를 테스트하려면 로컬 디렉터리에 템플릿(InlineSchemaTemplate.xml)을 지정한 다음 SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만들어서 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-128">To test this example, save the template (InlineSchemaTemplate.xml) in a local directory and then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="cf3ea-129">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-129">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="cf3ea-130">템플릿의 요소에 특성을 지정 하는 것 외에도 `mapping-schema` **\<sql:xpath-query>** (XPath 쿼리가 있을 때) 또는 **\<updg:sync>** updategram의 요소에는 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-130">In addition to specifying the `mapping-schema` attribute on the **\<sql:xpath-query>** element in a template (when there is an XPath query), or on **\<updg:sync>** element in an updategram, you can do the following:</span></span>  
  
-   <span data-ttu-id="cf3ea-131">`mapping-schema` **\<ROOT>** 템플릿의 요소 (전역 선언)에 특성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-131">Specify the `mapping-schema` attribute on the **\<ROOT>** element (global declaration) in the template.</span></span> <span data-ttu-id="cf3ea-132">그러면 이 매핑 스키마가 명시적 `mapping-schema` 주석이 없는 모든 XPath 및 Updategram 노드에서 사용할 기본 스키마가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-132">This mapping schema then becomes the default schema that will be used by all XPath and updategram nodes that have no explicit `mapping-schema` annotation.</span></span>  
  
-   <span data-ttu-id="cf3ea-133">ADO `mapping schema` 개체를 사용하여 `Command` 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-133">Specify the `mapping schema` attribute by using the ADO `Command` object.</span></span>  
  
 <span data-ttu-id="cf3ea-134">`mapping-schema`또는 요소에 지정 된 특성의 **\<xpath-query>** **\<updg:sync>** 우선 순위가 가장 높습니다. ADO `Command` 개체의 우선 순위가 가장 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-134">The `mapping-schema` attribute that is specified on the **\<xpath-query>** or **\<updg:sync>** element has the highest precedence; the ADO `Command` object has the lowest precedence.</span></span>  
  
 <span data-ttu-id="cf3ea-135">템플릿에서 XPath 쿼리를 지정 하 고 XPath 쿼리가 실행 되는 매핑 스키마를 지정 하지 않으면 XPath 쿼리가 **dbobject** type 쿼리로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-135">Note that if you specify an XPath query in a template and do not specify a mapping schema against which the XPath query is executed, the XPath query is treated as a **dbobject** type query.</span></span> <span data-ttu-id="cf3ea-136">예를 들어 다음 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-136">For example, consider this template:</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="cf3ea-137">이 템플릿에서는 XPath 쿼리만 지정하고 매핑 스키마는 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-137">The template specifies an XPath query but it does not specify a mapping schema.</span></span> <span data-ttu-id="cf3ea-138">따라서이 쿼리는 **dbobject** 형식 쿼리로 처리 됩니다. 여기서는 Production photo가 테이블 이름이 고 @ProductPhotoID = ' 100 '은 ID 값이 100 인 제품 사진을 찾는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-138">Therefore, this query is treated as a **dbobject** type query in which Production.ProductPhoto is the table name and @ProductPhotoID='100' is a predicate that finds a product photo with the ID value of 100.</span></span> <span data-ttu-id="cf3ea-139">@LargePhoto값을 검색할 열입니다.</span><span class="sxs-lookup"><span data-stu-id="cf3ea-139">@LargePhoto is the column from which to retrieve the value.</span></span>  
  
  
