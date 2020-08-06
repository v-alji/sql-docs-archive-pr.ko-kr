---
title: 주석이 추가 된 XSD 스키마 소개 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: rothja
ms.author: jroth
ms.openlocfilehash: b91be71569daa9e5bf4143be9f652617ba7c5b01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652717"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a><span data-ttu-id="6556e-102">주석이 추가된 XSD 스키마 소개(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6556e-102">Introduction to Annotated XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="6556e-103">XSD(XML 스키마 정의) 언어를 사용하여 관계형 데이터의 XML 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-103">You can create XML views of relational data by using the XML Schema Definition (XSD) language.</span></span> <span data-ttu-id="6556e-104">그런 다음 XPath(XML Path Language) 쿼리를 사용하여 뷰를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-104">These views can then be queried by using XML Path language (XPath) queries.</span></span> <span data-ttu-id="6556e-105">이는 CREATE VIEW 문을 사용하여 뷰를 만들고 뷰에 대해 SQL 쿼리를 지정하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-105">This is similar to creating views by using CREATE VIEW statements and then specifying SQL queries against the view.</span></span>  
  
 <span data-ttu-id="6556e-106">XML 스키마는 XML 문서의 구조뿐만 아니라 문서 내의 데이터에 대한 다양한 제약 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-106">An XML schema describes the structure of an XML document and also describes the various constraints on the data in the document.</span></span> <span data-ttu-id="6556e-107">스키마에 대해 XPath 쿼리를 지정하면 XPath 쿼리가 실행되는 스키마에 따라 반환되는 XML 문서의 구조가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-107">When you specify XPath queries against the schema, the structure of the XML document returned is determined by the schema against which the XPath query is executed.</span></span>  
  
 <span data-ttu-id="6556e-108">XSD 스키마에서 **\<xsd:schema>** 요소는 전체 스키마를 포함 합니다. 모든 요소 선언은 요소 내에 포함 되어야 합니다 **\<xsd:schema>** .</span><span class="sxs-lookup"><span data-stu-id="6556e-108">In an XSD schema, the **\<xsd:schema>** element encloses the entire schema; all element declarations must be contained within the **\<xsd:schema>** element.</span></span> <span data-ttu-id="6556e-109">스키마가 있는 네임 스페이스 및 스키마에 사용 되는 네임 스페이스를 정의 하는 특성을 요소의 속성으로 설명할 수 있습니다 **\<xsd:schema>** .</span><span class="sxs-lookup"><span data-stu-id="6556e-109">You can describe attributes that define the namespace in which the schema resides and the namespaces that are used in the schema as properties of the **\<xsd:schema>** element.</span></span>  
  
 <span data-ttu-id="6556e-110">유효한 XSD 스키마는 다음과 같이 정의 된 요소를 포함 해야 합니다 **\<xsd:schema>** .</span><span class="sxs-lookup"><span data-stu-id="6556e-110">A valid XSD schema must contain the **\<xsd:schema>** element defined as follows:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 <span data-ttu-id="6556e-111">요소는의 **\<xsd:schema>** XML 스키마 네임 스페이스 사양에서 파생 됩니다 http://www.w3.org/2001/XMLSchema .</span><span class="sxs-lookup"><span data-stu-id="6556e-111">The **\<xsd:schema>** element is derived from the XML Schema namespace specification at http://www.w3.org/2001/XMLSchema.</span></span>  
  
## <a name="annotations-to-the-xsd-schema"></a><span data-ttu-id="6556e-112">XSD 스키마에 주석 추가</span><span class="sxs-lookup"><span data-stu-id="6556e-112">Annotations to the XSD Schema</span></span>  
 <span data-ttu-id="6556e-113">데이터베이스에 대한 매핑을 설명하는 주석을 XSD 스키마에 추가하여 데이터베이스를 쿼리하고 결과를 XML 문서 형식으로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-113">You can use an XSD schema with annotations that describe the mapping to a database, query the database, and return the results in the form of an XML document.</span></span> <span data-ttu-id="6556e-114">주석을 사용하여 XSD 스키마를 데이터베이스 테이블 및 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-114">Annotations are provided to map an XSD schema to database tables and columns.</span></span> <span data-ttu-id="6556e-115">XSD 스키마로 생성된 XML 뷰에 대해 XPath 쿼리를 지정하여 데이터베이스를 쿼리하고 결과를 XML 형식으로 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-115">XPath queries can be specified against the XML view created by the XSD schema to query the database and obtain results as an XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6556e-116">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0의 XSD 스키마 언어는 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]에서 주석이 추가된 XDR(XML-Data Reduced) 스키마 언어에 도입된 주석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-116">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports the annotations introduced with annotated XML-Data Reduced (XDR) schema language in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="6556e-117">주석이 추가된 XDR은 SQLXML 4.0에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-117">Annotated XDR is deprecated in SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="6556e-118">관계형 데이터베이스 컨텍스트에서는 임의의 XSD 스키마를 관계형 저장소에 매핑하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-118">In the context of the relational database, it is useful to map the arbitrary XSD schema to a relational store.</span></span> <span data-ttu-id="6556e-119">이를 수행하는 한 가지 방법은 XSD 스키마에 주석을 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-119">One way to achieve this is to annotate the XSD schema.</span></span> <span data-ttu-id="6556e-120">주석을 포함 하는 XSD 스키마를 *매핑 스키마*라고 하며,이 스키마는 XML 데이터가 관계형 저장소에 매핑되는 방법과 관련 된 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-120">An XSD schema with the annotations is referred to as a *mapping schema*, which provides information pertaining to how XML data is to be mapped to the relational store.</span></span> <span data-ttu-id="6556e-121">매핑 스키마는 궁극적으로 관계형 데이터에 대한 XML 뷰로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-121">A mapping schema is, in effect, an XML view of the relational data.</span></span> <span data-ttu-id="6556e-122">이러한 매핑을 사용하여 관계형 데이터를 XML 문서로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-122">These mappings can be used to retrieve relational data as an XML document.</span></span>  
  
## <a name="namespace-for-annotations"></a><span data-ttu-id="6556e-123">주석에 대한 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="6556e-123">Namespace for Annotations</span></span>  
 <span data-ttu-id="6556e-124">XSD 스키마에서 주석은 **urn: schema-microsoft-com: mapping 스키마**네임 스페이스를 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-124">In an XSD schema, annotations are specified by using the namespace **urn:schemas-microsoft-com:mapping-schema**.</span></span> <span data-ttu-id="6556e-125">다음 예제와 같이 네임 스페이스를 지정 하는 가장 쉬운 방법은 태그에서 지정 하는 것입니다 **\<xsd:schema>** .</span><span class="sxs-lookup"><span data-stu-id="6556e-125">As shown in the following example, the easiest way to specify the namespace is to specify it in the **\<xsd:schema>** tag.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 <span data-ttu-id="6556e-126">사용된 네임스페이스 접두사는 임의로 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-126">The namespace prefix that is used is arbitrary.</span></span> <span data-ttu-id="6556e-127">이 설명서에서 **sql** 접두사는 주석 네임 스페이스를 나타내고이 네임 스페이스의 주석을 다른 네임 스페이스의 주석과 구별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-127">In this documentation, the **sql** prefix is used to denote the annotation namespace and to distinguish annotations in this namespace from those in other namespaces.</span></span>  
  
## <a name="example-of-an-annotated-xsd-schema"></a><span data-ttu-id="6556e-128">주석이 추가된 XSD 스키마 예</span><span class="sxs-lookup"><span data-stu-id="6556e-128">Example of an Annotated XSD Schema</span></span>  
 <span data-ttu-id="6556e-129">다음 예에서 XSD 스키마는 요소로 구성 됩니다 **\<Person.Contact>** .</span><span class="sxs-lookup"><span data-stu-id="6556e-129">In the following example, the XSD schema consists of an **\<Person.Contact>** element.</span></span> <span data-ttu-id="6556e-130">요소에는 **\<Employee>** **ContactID** 특성 및 **\<FirstName>** 및 **\<LastName>** 자식 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-130">The **\<Employee>** element has a **ContactID** attribute and **\<FirstName>** and **\<LastName>** child elements:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="6556e-131">해당 요소와 특성을 데이터베이스 테이블 및 열에 매핑하기 위해 이 XSD 스키마에 주석을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-131">Annotations are added to this XSD schema to map its elements and attributes to the database tables and columns:</span></span>  
  
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
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="6556e-132">매핑 스키마에서 **\<Contact>** 요소는 주석을 사용 하 여 샘플 AdventureWorks 데이터베이스의 Person. Contact 테이블에 매핑됩니다. `sql:relation`</span><span class="sxs-lookup"><span data-stu-id="6556e-132">In the mapping schema, the **\<Contact>** element is mapped to the Person.Contact table in the sample AdventureWorks database by using the `sql:relation` annotation.</span></span> <span data-ttu-id="6556e-133">ConID, FName 및 LName 특성은 `sql:field` 주석을 사용하여 Person.Contact 테이블의 ContactID, FirstName 및 LastName 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-133">The attributes ConID, FName, and LName are mapped to the ContactID, FirstName, and LastName columns in the Person.Contact table by using the `sql:field` annotations.</span></span>  
  
 <span data-ttu-id="6556e-134">주석이 추가된 이 XSD 스키마는 관계형 데이터에 대한 XML 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-134">This annotated XSD schema provides the XML view of the relational data.</span></span> <span data-ttu-id="6556e-135">이 XML 뷰는 XPath 언어를 사용하여 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-135">This XML view can be queried using the XPath language.</span></span> <span data-ttu-id="6556e-136">SQL 쿼리에서 행 집합을 반환하는 것과는 달리 XPath 쿼리에서는 XML 문서를 결과로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-136">An XPath query returns an XML document as a result, instead of the rowset that is returned by SQL queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6556e-137">매핑 스키마에서 지정된 관계형 값(예: 테이블 이름 및 열 이름)의 대/소문자 구분은 SQL Server에서 대/소문자 구분 데이터 정렬 설정을 사용하고 있는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6556e-137">In the mapping schema, case-sensitivity for the specified relational values (such as table name and column name) depends upon if SQL Server is using case-sensitive collation settings.</span></span> <span data-ttu-id="6556e-138">자세한 내용은 [Collation and Unicode Support](../../collations/collation-and-unicode-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6556e-138">For more information, see [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="6556e-139">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="6556e-139">Other Resources</span></span>  
 <span data-ttu-id="6556e-140">XSD(XML 스키마 정의 언어), XPath(XML Path Language) 및 XSLT(Extensible Stylesheet Language Transformations)에 대한 자세한 내용은 다음 웹 사이트를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6556e-140">You can find more information about XML Schema Definition language (XSD), XML Path language (XPath), and Extensible Stylesheet Language Transformations (XSLT) at the following Web sites:</span></span>  
  
-   <span data-ttu-id="6556e-141">XML 스키마 파트 0: 입문, W3C 권장 사항 (http://www.w3.org/TR/xmlschema-0/)</span><span class="sxs-lookup"><span data-stu-id="6556e-141">XML Schema Part 0: Primer, W3C Recommendation (http://www.w3.org/TR/xmlschema-0/)</span></span>  
  
-   <span data-ttu-id="6556e-142">XML 스키마 파트 1: 구조, W3C 권장 사항 (http://www.w3.org/TR/xmlschema-1/)</span><span class="sxs-lookup"><span data-stu-id="6556e-142">XML Schema Part 1: Structures, W3C Recommendation (http://www.w3.org/TR/xmlschema-1/)</span></span>  
  
-   <span data-ttu-id="6556e-143">XML 스키마 파트 2: 데이터 형식, W3C 권장 사항 (http://www.w3.org/TR/xmlschema-2/)</span><span class="sxs-lookup"><span data-stu-id="6556e-143">XML Schema Part 2:Datatypes, W3C Recommendation (http://www.w3.org/TR/xmlschema-2/)</span></span>  
  
-   <span data-ttu-id="6556e-144">XPath (XML Path Language) (http://www.w3.org/TR/xpath)</span><span class="sxs-lookup"><span data-stu-id="6556e-144">XML Path Language (XPath) (http://www.w3.org/TR/xpath)</span></span>  
  
-   <span data-ttu-id="6556e-145">XSLT (XSL 변환) (http://www.w3.org/TR/xslt)</span><span class="sxs-lookup"><span data-stu-id="6556e-145">XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6556e-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6556e-146">See Also</span></span>  
 <span data-ttu-id="6556e-147">[SQLXML 4.0 &#40;주석이 추가 된 스키마 보안 고려 사항&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6556e-147">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="6556e-148">주석이 추가 된 XDR 스키마 &#40;SQLXML 4.0에서 더 이상 사용 되지 않습니다&#41;</span><span class="sxs-lookup"><span data-stu-id="6556e-148">Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;</span></span>](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
