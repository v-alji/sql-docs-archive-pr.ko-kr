---
title: XSD 스키마에 주석 사용 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: e2be94aa5815593d7a5a2e0c00bcd8849e81484e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650893"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a><span data-ttu-id="d54a6-102">XSD 스키마에 주석 사용(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d54a6-102">Using Annotations in XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="d54a6-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0의 XSD 스키마 언어는 XDR(XML-Data Reduced) 스키마 언어에 도입된 주석과 비슷한 방식으로 주석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports annotations in a manner similar to the annotations introduced in the XML-Data Reduced (XDR) schema language.</span></span> <span data-ttu-id="d54a6-104">XSD에는 XDR에서는 지원되지 않은 추가 주석도 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-104">There are additional annotations introduced in XSD that are not supported in XDR.</span></span>  
  
 <span data-ttu-id="d54a6-105">이러한 주석은 XSD 스키마 내에서 XML-관계형 매핑을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-105">These annotations can be used within the XSD schema to specify XML-to-relational mapping.</span></span> <span data-ttu-id="d54a6-106">여기에는 XSD 스키마의 요소 및 특성을 데이터베이스의 테이블(뷰) 및 열에 매핑하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-106">This includes mapping between elements and attributes in the XSD schema to tables (views) and columns in the databases.</span></span>  
  
 <span data-ttu-id="d54a6-107">주석을 지정하지 않으면 기본 매핑이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-107">If you do not specify the annotations, default mapping takes place.</span></span> <span data-ttu-id="d54a6-108">기본적으로 복합 유형의 XSD 요소는 지정된 데이터베이스의 테이블(뷰) 이름에 매핑되며 단순 유형의 요소 또는 특성은 같은 이름의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-108">By default, an XSD element with a complex type maps to a table (view) name in the specified database, and an element or attribute with a simple type maps to the column with the same name as the element or attribute.</span></span>  
  
 <span data-ttu-id="d54a6-109">이러한 주석은 XML에서 계층 관계를 지정 하는 데에도 사용할 수 있습니다. 따라서 XSD 스키마는 단순히 관계형 데이터의 XML 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-109">These annotations can also be used to specify the hierarchical relationships in XML-thus representing the relationships in the database, because an XSD schema is simply an XML view of relational data.</span></span>  
  
 <span data-ttu-id="d54a6-110">이 섹션에서는 XSD 스키마에서 사용할 수 있는 주석에 대해 설명하고 사용 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-110">This section provides descriptions of the annotations you can use with XSD schemas and examples of their usage.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d54a6-111">이 섹션에 있는 모든 예는 각 예에서 설명된 주석이 추가된 XSD 스키마에 대해 간단한 XPath 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-111">All the examples in this section specify simple XPath queries against the annotated XSD schema described in each example.</span></span> <span data-ttu-id="d54a6-112">이 섹션에서는 사용자가 XPath 언어에 대해 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-112">Familiarity with the XPath language is assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d54a6-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d54a6-113">In This Section</span></span>  
 [<span data-ttu-id="d54a6-114">&#40;SQLXML 4.0&#41;XSD 주석</span><span class="sxs-lookup"><span data-stu-id="d54a6-114">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](xsd-annotations-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-115">XSD 스키마에서 사용할 수 있는 주석, 이러한 주석에 대한 설명, 그리고 이러한 주석에 해당하는 XDR 주석을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-115">Lists the annotations you can use with XSD schemas, their descriptions, and the equivalent annotations for XDR.</span></span>  
  
 [<span data-ttu-id="d54a6-116">SQLXML 4.0 &#40;테이블 및 열에 대 한 XSD 요소 및 특성의 기본 매핑&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-116">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-117">기본 매핑 및 이와 관련된 태스크의 예를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-117">Explains default mapping and provides examples of tasks related to default mapping.</span></span>  
  
 [<span data-ttu-id="d54a6-118">SQLXML 4.0 &#40;테이블 및 열에 대 한 XSD 요소 및 특성의 명시적 매핑&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-118">Explicit Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 <span data-ttu-id="d54a6-119">`sql:relation` 및 `sql:field` 주석을 사용한 명시적 매핑에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-119">Explains explicit mapping with the `sql:relation` and `sql:field` annotations, and provides examples.</span></span>  
  
 [<span data-ttu-id="d54a6-120">Sql: relationship &#40;SQLXML 4.0&#41;를 사용 하 여 관계 지정</span><span class="sxs-lookup"><span data-stu-id="d54a6-120">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-121">`sql:relationship` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-121">Describes and provides examples of the `sql:relationship` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-122">Sql: relationship에 sql: 역 특성 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-122">Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-123">`sql:inverse` 주석에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-123">Describes the `sql:inverse` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-124">Sql: is 상수 &#40;SQLXML 4.0&#41;를 사용 하 여 상수 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-124">Creating Constant Elements Using sql:is-constant &#40;SQLXML 4.0&#41;</span></span>](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-125">`sql:is-constant` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-125">Describes and provides examples of the `sql:is-constant` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-126">Sql: mapped &#40;SQLXML 4.0&#41;를 사용 하 여 결과 XML 문서에서 스키마 요소 제외</span><span class="sxs-lookup"><span data-stu-id="d54a6-126">Excluding Schema Elements from the Resulting XML Document Using sql:mapped &#40;SQLXML 4.0&#41;</span></span>](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 <span data-ttu-id="d54a6-127">`sql:mapped` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-127">Describes and provides examples of the `sql:mapped` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-128">Sql: limit 필드 및 sql: limit 값을 사용 하 여 값 필터링 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-128">Filtering Values Using sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="d54a6-129">`sql:limit-field` 및 `sql:limit-value` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-129">Describes and provides examples of the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 [<span data-ttu-id="d54a6-130">Sql: 키-필드 &#40;SQLXML 4.0&#41;를 사용 하 여 키 열 식별</span><span class="sxs-lookup"><span data-stu-id="d54a6-130">Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;</span></span>](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-131">`sql:key-fields` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-131">Describes and provides examples of the `sql:key-fields` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-132">TargetNamespace 특성 &#40;사용 하 여 대상 네임 스페이스 지정&#41;SQLXML 4.0</span><span class="sxs-lookup"><span data-stu-id="d54a6-132">Specifying a Target Namespace Using the targetNamespace Attribute &#40;SQLXML 4.0&#41;</span></span>](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-133">**TargetNamespace** 특성에 대해 설명 하 고 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-133">Describes and provides examples of the **targetNamespace** attribute.</span></span>  
  
 [<span data-ttu-id="d54a6-134">Sql: prefix &#40;SQLXML 4.0&#41;를 사용 하 여 유효한 ID, IDREF 및 IDREFS 유형 특성 만들기</span><span class="sxs-lookup"><span data-stu-id="d54a6-134">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix &#40;SQLXML 4.0&#41;</span></span>](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-135">`sql:prefix` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-135">Describes and provides examples of the `sql:prefix` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-136">데이터 형식 강제 변환 및 sql: datatype 주석 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-136">Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;</span></span>](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-137">`sql:datatype` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-137">Describes and provides examples of the `sql:datatype` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-138">&#40;SQLXML 4.0&#41;XSD 데이터 형식을 XPath 데이터 형식에 매핑</span><span class="sxs-lookup"><span data-stu-id="d54a6-138">Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-139">XSD, XDR 및 XPath 데이터 형식을 비교하고 연관된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변환을 나열하는 표를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-139">Provides a table that compares XSD, XDR, and XPath datatypes and lists the relevant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversions.</span></span>  
  
 [<span data-ttu-id="d54a6-140">Sql: use-cdata &#40;SQLXML 4.0&#41;를 사용 하 여 CDATA 섹션 만들기</span><span class="sxs-lookup"><span data-stu-id="d54a6-140">Creating CDATA Sections Using sql:use-cdata &#40;SQLXML 4.0&#41;</span></span>](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-141">`sql:use-data` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-141">Describes and provides examples of the `sql:use-data` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-142">Sql: encoding &#40;SQLXML 4.0&#41;를 사용 하 여 BLOB 데이터에 대 한 URL 참조 요청</span><span class="sxs-lookup"><span data-stu-id="d54a6-142">Requesting URL References to BLOB Data Using sql:encode &#40;SQLXML 4.0&#41;</span></span>](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 <span data-ttu-id="d54a6-143">`sql:encode` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-143">Describes and provides examples of the `sql:encode` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-144">Sql: 오버플로 필드 &#40;SQLXML 4.0&#41;를 사용 하 여 사용 되지 않은 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-144">Retrieving Unconsumed Data Using the sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="d54a6-145">`sql:overflow-field` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-145">Describes and provides examples of the `sql:overflow-field` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-146">sql:hide를 사용하여 요소 및 특성 숨기기</span><span class="sxs-lookup"><span data-stu-id="d54a6-146">Hiding Elements and Attributes by Using sql:hide</span></span>](hiding-elements-and-attributes-by-using-sql-hide.md)  
 <span data-ttu-id="d54a6-147">`sql:hide` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-147">Describes and provides examples of the `sql:hide` annotation.</span></span>  
  
 [<span data-ttu-id="d54a6-148">sql:identity 및 sql:guid 주석 사용</span><span class="sxs-lookup"><span data-stu-id="d54a6-148">Using the sql:identity and sql:guid Annotations</span></span>](using-the-sql-identity-and-sql-guid-annotations.md)  
 <span data-ttu-id="d54a6-149">`sql:identity` 및 `sql:guid` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-149">Describes and provides examples of the `sql:identity` and `sql:guid` annotations.</span></span>  
  
 [<span data-ttu-id="d54a6-150">sql:max-depth를 사용하여 재귀 관계의 깊이 지정</span><span class="sxs-lookup"><span data-stu-id="d54a6-150">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 <span data-ttu-id="d54a6-151">`sql:max-depth` 주석에 대해 설명하고 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d54a6-151">Describes and provides examples of the `sql:max-depth` annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54a6-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d54a6-152">See Also</span></span>  
 [<span data-ttu-id="d54a6-153">SQLXML 4.0 &#40;주석이 추가 된 스키마 보안 고려 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="d54a6-153">Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
