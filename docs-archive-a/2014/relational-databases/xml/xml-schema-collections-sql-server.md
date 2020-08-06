---
title: XML 스키마 컬렉션(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652671"
---
# <a name="xml-schema-collections-sql-server"></a><span data-ttu-id="49468-102">XML 스키마 컬렉션 [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="49468-102">XML Schema Collections (SQL Server)</span></span>
  <span data-ttu-id="49468-103">[Xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)항목에서 설명 하는 것 처럼 SQL Server는 데이터 형식을 통해 xml 데이터의 기본 저장소를 제공 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="49468-103">As described in the topic, [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql), SQL Server provides native storage of XML data through the `xml` data type.</span></span> <span data-ttu-id="49468-104">필요에 따라 XML 스키마 컬렉션을 통해 XSD 스키마를 변수나 형식의 열에 연결할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="49468-104">You can optionally associate XSD schemas with a variable or a column of `xml` type through an XML schema collection.</span></span> <span data-ttu-id="49468-105">XML 스키마 컬렉션은 가져온 XML 스키마를 저장하고 다음을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-105">The XML schema collection stores the imported XML schemas and is then used to do the following:</span></span>  
  
-   <span data-ttu-id="49468-106">XML 인스턴스 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="49468-106">Validate XML instances</span></span>  
  
-   <span data-ttu-id="49468-107">데이터베이스에 저장될 때 XML 데이터 형식화</span><span class="sxs-lookup"><span data-stu-id="49468-107">Type the XML data as it is stored in the database</span></span>  
  
 <span data-ttu-id="49468-108">XML 스키마 컬렉션은 데이터베이스에 있는 테이블과 같은 메타데이터 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-108">Note that the XML schema collection is a metadata entity like a table in the database.</span></span> <span data-ttu-id="49468-109">스키마 컬렉션은 생성, 수정 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-109">You can create, modify, and drop them.</span></span> <span data-ttu-id="49468-110">[CREATE XML SCHEMA COLLECTION(Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) 문에 지정된 스키마는 새로 만든 XML 스키마 컬렉션 개체에 자동으로 가져와집니다.</span><span class="sxs-lookup"><span data-stu-id="49468-110">Schemas specified in a [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) statement are automatically imported into the newly created XML schema collection object.</span></span> <span data-ttu-id="49468-111">[ALTER XML SCHEMA COLLECTION(Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) 문을 사용하여 추가 스키마 또는 스키마 구성 요소를 데이터베이스에 있는 기존 컬렉션 개체로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-111">You can import additional schemas or schema components into an existing collection object in the database by using the [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="49468-112">[형식화된 XML과 형식화되지 않은 XML](../xml/compare-typed-xml-to-untyped-xml.md) 항목에 설명된 것과 같이 스키마가 연결된 열 또는 변수에 저장된 XML은 스키마가 인스턴스 데이터에 대해 필요한 데이터 형식 정보를 제공하기 때문에 **형식화된** XML이라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="49468-112">As described in the topic, [Typed vs. Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md), the XML stored in a column or variable that a schema is associated with is referred to as **typed** XML, because the schema provides the necessary data type information for the instance data.</span></span> <span data-ttu-id="49468-113">SQL Server는 이 유형 정보를 사용하여 데이터 스토리지를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-113">SQL Server uses this type information to optimize data storage.</span></span>  
  
 <span data-ttu-id="49468-114">쿼리 프로세싱 엔진은 또한 유형 검사 및 쿼리와 데이터 수정 최적화를 위해 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-114">The query-processing engine also uses the schema for type checking and to optimize queries and data modification.</span></span>  
  
 <span data-ttu-id="49468-115">또한 SQL Server는 형식화 된의 경우 연결 된 XML 스키마 컬렉션을 사용 하 여 `xml` xml 인스턴스의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-115">Also, SQL Server uses the associated XML schema collection, in the case of typed `xml`, to validate the XML instance.</span></span> <span data-ttu-id="49468-116">XML 인스턴스가 스키마로 컴파일되는 경우 데이터베이스에서 인스턴스를 해당 유형 정보와 함께 시스템에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-116">If the XML instance complies with the schema, the database allows the instance to be stored in the system with their type information.</span></span> <span data-ttu-id="49468-117">그렇지 않으면 인스턴스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-117">Otherwise, it rejects the instance.</span></span>  
  
 <span data-ttu-id="49468-118">내장 함수 XML_SCHEMA_NAMESPACE를 사용하여 데이터베이스에 저장된 스키마 컬렉션을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-118">You can use the intrinsic function XML_SCHEMA_NAMESPACE to retrieve the schema collection that is stored in the database.</span></span> <span data-ttu-id="49468-119">자세한 내용은 [저장된 XML 스키마 컬렉션 보기](../xml/view-a-stored-xml-schema-collection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49468-119">For more information, see [View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md).</span></span>  
  
 <span data-ttu-id="49468-120">또한 XML 스키마 컬렉션을 사용하여 XML 변수, 매개 변수 및 열을 형식화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-120">You can also use the XML schema collection to type XML variables, parameters, and columns.</span></span>  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> <span data-ttu-id="49468-121">스키마 컬렉션 관리 DDL</span><span class="sxs-lookup"><span data-stu-id="49468-121">DDL for Managing Schema Collections</span></span>  
 <span data-ttu-id="49468-122">데이터베이스에서 XML 스키마 컬렉션을 만들고 이를 `xml` 유형의 변수 및 열과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-122">You can create XML schema collections in the database and associate them with variables and columns of `xml` type.</span></span> <span data-ttu-id="49468-123">데이터베이스에 있는 스키마 컬렉션을 관리하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 다음 DDL 문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-123">To manage schema collections in the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following DDL statements:</span></span>  
  
-   <span data-ttu-id="49468-124">[CREATE XML SCHEMA COLLECTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)은 데이터베이스에 스키마 구성 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="49468-124">[CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) Imports schema components into a database.</span></span>  
  
-   <span data-ttu-id="49468-125">[ALTER XML SCHEMA COLLECTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql)은 기존 XML 스키마 컬렉션의 스키마 구성 요소를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-125">[ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) Modifies the schema components in an existing XML schema collection.</span></span>  
  
-   <span data-ttu-id="49468-126">[DROP XML SCHEMA COLLECTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)은 전체 XML 스키마 컬렉션 및 모든 해당 구성 요소를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-126">[DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) Deletes a complete XML schema collection and all its components.</span></span>  
  
 <span data-ttu-id="49468-127">XML 스키마 컬렉션과 여기에 포함되는 스키마를 사용하려면 먼저 CREATE XML SCHEMA COLLECTION 문을 사용하여 컬렉션과 스키마를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-127">To use an XML schema collection and the schemas it contains, you must first create the collection and the schemas by using the CREATE XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="49468-128">스키마 컬렉션을 만든 다음에는 `xml` 유형의 변수와 열을 만들고 스키마 컬렉션과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-128">After the schema collection is created, you can then create variables and columns of `xml` type and associate the schema collection with them.</span></span> <span data-ttu-id="49468-129">스키마 컬렉션을 만든 다음에는 여러 스키마 구성 요소가 메타데이터에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-129">Note that after a schema collection is created, various schema components are stored in the metadata.</span></span> <span data-ttu-id="49468-130">또한 ALTER XML SCHEMA COLLECTION을 사용하여 기존 스키마에 더 많은 구성 요소를 추가하거나 기존 컬렉션에 새로운 스키마를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-130">You can also use the ALTER XML SCHEMA COLLECTION to add more components to the existing schemas or add new schemas to an existing collection.</span></span>  
  
 <span data-ttu-id="49468-131">스키마 컬렉션을 삭제하려면 DROP XML SCHEMA COLLECTION 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-131">To drop the schema collection, use the DROP XML SCHEMA COLLECTION statement.</span></span> <span data-ttu-id="49468-132">이렇게 하면 컬렉션에 포함된 모든 스키마가 삭제되고 컬렉션 개체가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-132">This drops all schemas that are contained in the collection and removes the collection object.</span></span> <span data-ttu-id="49468-133">스키마 컬렉션을 삭제하려면 [DROP XML SCHEMA COLLECTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)에 기술된 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-133">Note that before you can drop a schema collection, the conditions described in [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql)must be met.</span></span>  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> <span data-ttu-id="49468-134">스키마 구성 요소 이해</span><span class="sxs-lookup"><span data-stu-id="49468-134">Understanding Schema Components</span></span>  
 <span data-ttu-id="49468-135">CREATE XML SCHEMA COLLECTION 문을 사용하면 여러 스키마 구성 요소를 데이터베이스로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="49468-135">When you use the CREATE XML SCHEMA COLLECTION statement, various schema components are imported into the database.</span></span> <span data-ttu-id="49468-136">스키마 구성 요소에는 스키마 요소, 특성 및 유형 정의가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-136">Schema components include schema elements, attributes, and type definitions.</span></span> <span data-ttu-id="49468-137">DROP XML SCHEMA COLLECTION 문을 사용하면 전체 컬렉션을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-137">When you use the DROP XML SCHEMA COLLECTION statement, you remove the complete collection.</span></span>  
  
 <span data-ttu-id="49468-138">CREATE XML SCHEMA COLLECTION은 여러 시스템 테이블에 스키마 구성 요소를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-138">CREATE XML SCHEMA COLLECTION saves the schema components into various system tables.</span></span>  
  
 <span data-ttu-id="49468-139">예를 들어 다음 스키마를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="49468-139">For example, consider the following schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 <span data-ttu-id="49468-140">이전 스키마는 데이터베이스에 저장할 수 있는 여러 유형의 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49468-140">The previous schema shows the different types of components that can be stored in the database.</span></span> <span data-ttu-id="49468-141">여기에는 `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`및 `ShippedDate`이(가) 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-141">These include `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`, and `ShippedDate`.</span></span>  
  
### <a name="component-categories"></a><span data-ttu-id="49468-142">구성 요소 범주</span><span class="sxs-lookup"><span data-stu-id="49468-142">Component Categories</span></span>  
 <span data-ttu-id="49468-143">데이터베이스에 저장되는 스키마 구성 요소는 다음 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-143">The Schema components stored in the database fall into the following categories:</span></span>  
  
-   <span data-ttu-id="49468-144">ELEMENT</span><span class="sxs-lookup"><span data-stu-id="49468-144">ELEMENT</span></span>  
  
-   <span data-ttu-id="49468-145">ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="49468-145">ATTRIBUTE</span></span>  
  
-   <span data-ttu-id="49468-146">TYPE(간단하거나 복잡한 유형)</span><span class="sxs-lookup"><span data-stu-id="49468-146">TYPE (for simple or complex types)</span></span>  
  
-   <span data-ttu-id="49468-147">ATTRIBUTEGROUP</span><span class="sxs-lookup"><span data-stu-id="49468-147">ATTRIBUTEGROUP</span></span>  
  
-   <span data-ttu-id="49468-148">MODELGROUP</span><span class="sxs-lookup"><span data-stu-id="49468-148">MODELGROUP</span></span>  
  
 <span data-ttu-id="49468-149">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-149">For example:</span></span>  
  
-   <span data-ttu-id="49468-150">**SomeAttribute** 는 ATTRIBUTE 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-150">**SomeAttribute** is an ATTRIBUTE component.</span></span>  
  
-   <span data-ttu-id="49468-151">**SomeType**, **OrderType**및 **CustomerType** 은 TYPE 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-151">**SomeType**, **OrderType**, and **CustomerType** are TYPE components.</span></span>  
  
-   <span data-ttu-id="49468-152">**Customer** 는 ELEMENT 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-152">**Customer** is an ELEMENT component.</span></span>  
  
 <span data-ttu-id="49468-153">데이터베이스로 스키마를 가져올 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 스키마 자체는 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-153">When you import a schema into the database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not store the schema itself.</span></span> <span data-ttu-id="49468-154">대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 여러 개별 구성 요소를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-154">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stores the various individual components.</span></span> <span data-ttu-id="49468-155">즉, \<Schema> 태그는 저장되지 않으며 이 태그 내에 정의된 구성 요소만 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-155">That is, the \<Schema> tag is not stored, only the components that are defined within it are preserved.</span></span> <span data-ttu-id="49468-156">모든 스키마 요소는 보관되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-156">All schema elements are not preserved.</span></span> <span data-ttu-id="49468-157">\<Schema> 태그에 해당 구성 요소의 기본 동작을 지정하는 특성이 포함된 경우 이러한 특성은 다음 표에 설명된 것과 같이 가져오기 프로세스 중에 태그 내에 있는 스키마 구성 요소로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-157">If the \<Schema> tag contains attributes that specify default behavior of its components, these attributes are moved to the schema components within it during the import process, as shown in the following table.</span></span>  
  
|<span data-ttu-id="49468-158">특성 이름</span><span class="sxs-lookup"><span data-stu-id="49468-158">Attribute name</span></span>|<span data-ttu-id="49468-159">동작</span><span class="sxs-lookup"><span data-stu-id="49468-159">Behavior</span></span>|  
|--------------------|--------------|  
|<span data-ttu-id="49468-160">**attributeFormDefault**</span><span class="sxs-lookup"><span data-stu-id="49468-160">**attributeFormDefault**</span></span>|<span data-ttu-id="49468-161">아직 제공되지 않았고 값이 **attributeFormDefault** 특성의 값으로 설정된 스키마의 모든 특성 선언에 적용된 **form** 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-161">The **form** attribute applied to all attribute declarations in the schema where it is not already present and the value is set to the value of the **attributeFormDefault** attribute.</span></span>|  
|<span data-ttu-id="49468-162">**elementFormDefault**</span><span class="sxs-lookup"><span data-stu-id="49468-162">**elementFormDefault**</span></span>|<span data-ttu-id="49468-163">아직 제공되지 않았고 값이 **elementFormDefault** 특성의 값으로 설정된 스키마의 모든 요소 선언에 적용된 **form** 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-163">The **form** attribute applied to all element declarations in the schema where it is not already present and the value is set to the value of the **elementFormDefault** attribute.</span></span>|  
|<span data-ttu-id="49468-164">**blockDefault**</span><span class="sxs-lookup"><span data-stu-id="49468-164">**blockDefault**</span></span>|<span data-ttu-id="49468-165">아직 제공되지 않았고 값이 **blockDefault** 특성의 값으로 설정된 모든 요소 선언 및 유형 정의에 적용된 **block** 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-165">The **block** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **blockDefault** attribute.</span></span>|  
|<span data-ttu-id="49468-166">**finalDefault**</span><span class="sxs-lookup"><span data-stu-id="49468-166">**finalDefault**</span></span>|<span data-ttu-id="49468-167">아직 제공되지 않았고 값이 **finalDefault** 특성의 값으로 설정된 모든 요소 선언 및 유형 정의에 적용된 **final** 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-167">The **final** attribute applied to all element declarations and type definitions where it is not already present and the value is set to the value of the **finalDefault** attribute.</span></span>|  
|<span data-ttu-id="49468-168">**targetNamespace**</span><span class="sxs-lookup"><span data-stu-id="49468-168">**targetNamespace**</span></span>|<span data-ttu-id="49468-169">대상 네임스페이스에 속하는 구성 요소에 대한 정보는 메타데이터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-169">Information about the components that belong to the target namespace is stored in the metadata.</span></span>|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> <span data-ttu-id="49468-170">XML 스키마 컬렉션에 대한 사용 권한</span><span class="sxs-lookup"><span data-stu-id="49468-170">Permissions on an XML Schema Collection</span></span>  
 <span data-ttu-id="49468-171">다음을 수행하는 데 필요한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-171">You must have the necessary permissions to do the following:</span></span>  
  
-   <span data-ttu-id="49468-172">XML 스키마 컬렉션 생성/로드</span><span class="sxs-lookup"><span data-stu-id="49468-172">Create/load the XML schema collection</span></span>  
  
-   <span data-ttu-id="49468-173">XML 스키마 컬렉션 수정</span><span class="sxs-lookup"><span data-stu-id="49468-173">Modify the XML schema collection</span></span>  
  
-   <span data-ttu-id="49468-174">XML 스키마 컬렉션 삭제</span><span class="sxs-lookup"><span data-stu-id="49468-174">Drop the XML schema collection</span></span>  
  
-   <span data-ttu-id="49468-175">XML 스키마 컬렉션을 사용 하 여 `xml` 형식 열, 변수 및 매개 변수를 입력 하거나 테이블 또는 열 제약 조건에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-175">Use the XML schema collection to type `xml` type columns, variables, and parameters, or use it in table or column constraints</span></span>  
  
 <span data-ttu-id="49468-176">SQL Server 보안 모델에서는 모든 개체에 대한 CONTROL 권한이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-176">The SQL Server security model allows CONTROL permission on every object.</span></span> <span data-ttu-id="49468-177">이 사용 권한의 피부여자는 개체에 대한 모든 기타 사용 권한을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-177">The grantee of this permission obtains all other permissions on the object.</span></span> <span data-ttu-id="49468-178">개체의 소유자는 또한 개체에 대한 모든 사용 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="49468-178">The owner of the object also has all the permissions on the object.</span></span>  
  
 <span data-ttu-id="49468-179">개체에 대한 CONTROL 권한의 소유자 및 피부여자는 해당 개체에 대한 모든 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-179">The owner and the grantee of the CONTROL permission on an object can grant any permission on the object.</span></span> <span data-ttu-id="49468-180">소유자가 아니고 CONTROL 권한이 없는 사용자도 WITH GRANT OPTION이 지정된 경우에는 개체에 대한 사용 권한을 계속 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-180">A user who is not the owner and does not have CONTROL permission can still grant permission on an object when WITH GRANT OPTION is specified.</span></span> <span data-ttu-id="49468-181">예를 들어 WITH GRANT OPTION을 통해 사용자 A에게 XML 스키마 컬렉션 S에 대한 REFERENCES 권한이 있지만 S에 대한 다른 사용 권한이 없다고 가정해 보십시오. 이 경우 사용자 A는 사용자 B에게 스키마 컬렉션 S에 대한 REFERENCES 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-181">For example, assume User A has REFERENCES permission on XML schema collection S, through WITH GRANT OPTION, but no other permissions on S. User A could grant User B REFERENCES permission on schema collection S.</span></span>  
  
 <span data-ttu-id="49468-182">보안 모델에서는 또한 사용 권한을 통해 XML 스키마 컬렉션을 만들고 사용하거나 한 사용자에서 다른 사용자로 소유권을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-182">The security model also allows permissions to create and use XML schema collections or transfer ownership from one user to another.</span></span> <span data-ttu-id="49468-183">다음 항목에서는 XML 스키마 컬렉션 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-183">The following topics describe the XML schema collection permissions.</span></span>  
  
-   [<span data-ttu-id="49468-184">XML 스키마 컬렉션에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="49468-184">Grant Permissions on an XML Schema Collection</span></span>](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="49468-185">이 항목에서는 XML 스키마 컬렉션을 만들기 위한 사용 권한을 부여하고 XML 스키마 컬렉션 개체에 대한 사용 권한을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-185">This topic discussess how to grant permissions to create an XML schema collection and how to grant permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="49468-186">XML 스키마 컬렉션에 대한 사용 권한 취소</span><span class="sxs-lookup"><span data-stu-id="49468-186">Revoke Permissions on an XML Schema Collection</span></span>](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="49468-187">이 항목에서는 사용 권한 취소를 사용하여 XML 스키마 컬렉션이 생성되지 않도록 방지하고 XML 스키마 컬렉션 개체에서 사용 권한을 취소하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-187">This topic discusses how revoking permissions can be used to prevent the creation of an XML schema collection and how to revoke permissions on an XML schema collection object.</span></span>  
  
-   [<span data-ttu-id="49468-188">XML 스키마 컬렉션에 대한 사용 권한 거부</span><span class="sxs-lookup"><span data-stu-id="49468-188">Deny Permissions on an XML Schema Collection</span></span>](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     <span data-ttu-id="49468-189">이 항목에서는 XML 스키마 컬렉션을 만들기 위한 사용 권한을 거부하고 XML 스키마 컬렉션 개체에 대한 사용 권한을 거부하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-189">This topic discusses how to deny permissions to create an XML schema collection and deny permission on an XML schema collection object.</span></span>  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> <span data-ttu-id="49468-190">XML 스키마 및 스키마 컬렉션에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="49468-190">Getting Information about XML Schemas and Schema Collections</span></span>  
 <span data-ttu-id="49468-191">XML 스키마 컬렉션은 sys.xml_schema_collections 카탈로그 뷰에 열거됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-191">XML schema collections are enumerated in the catalog view, sys.xml_schema_collections.</span></span> <span data-ttu-id="49468-192">XML 스키마 컬렉션 "sys"는 시스템에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-192">The XML schema collection "sys" is defined by the system.</span></span> <span data-ttu-id="49468-193">여기에는 명시적으로 로드할 필요 없이 모든 사용자 정의 XML 스키마 컬렉션에서 사용할 수 있는 미리 정의된 네임스페이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-193">It contains the predefined namespaces that can be used in all user-defined XML schema collections without having to load them explicitly.</span></span> <span data-ttu-id="49468-194">이 목록에는 xml, xs, xsi, fn 및 xdt에 대한 네임스페이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="49468-194">This list contains the namespaces for xml, xs, xsi, fn, and xdt.</span></span> <span data-ttu-id="49468-195">두 개의 다른 카탈로그 뷰는 각 XML 스키마 컬렉션 내에서 모든 네임스페이스를 열거하는 sys.xml_schema_namespaces와 각 XML 스키마 내에서 모든 XML 스키마 구성 요소를 열거하는 sys.xml_components입니다.</span><span class="sxs-lookup"><span data-stu-id="49468-195">Two other catalog views are sys.xml_schema_namespaces, which enumerates all namespaces within each XML schema collection, and sys.xml_components, which enumerates all XML schema components within each XML schema.</span></span>  
  
 <span data-ttu-id="49468-196">기본 제공 **XML_SCHEMA_NAMESPACE**함수인 *XmlSchemacollectionName, schemaName,, NAMESPACE uri*는 `xml` 데이터 형식 인스턴스를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-196">The built-in function **XML_SCHEMA_NAMESPACE**, *schemaName, XmlSchemacollectionName, namespace-uri*, yields an `xml` data type instance..</span></span> <span data-ttu-id="49468-197">이 인스턴스에는 미리 정의된 XML 스키마를 제외하고 XML 스키마 컬렉션에 포함된 스키마에 대한 XML 스키마 조각이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-197">This instance contains XML schema fragments for schemas that are contained in an XML schema collection, except the predefined XML schemas.</span></span>  
  
 <span data-ttu-id="49468-198">XML 스키마 컬렉션의 내용은 다음과 같은 방식으로 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-198">You can enumerate the contents of an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="49468-199">XML 스키마 컬렉션에 적합한 카탈로그 뷰에 Transact-SQL 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-199">Write Transact-SQL queries on the appropriate catalog views for XML schema collections.</span></span>  
  
-   <span data-ttu-id="49468-200">기본 제공 함수 **XML_SCHEMA_NAMESPACE()** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-200">Use the built-in function **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="49468-201">`xml`이 함수의 출력에 데이터 형식 메서드를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-201">You can apply `xml` data type methods on the output of this function.</span></span> <span data-ttu-id="49468-202">하지만 기본 XML 스키마는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-202">However, you cannot modify the underlying XML schemas.</span></span>  
  
 <span data-ttu-id="49468-203">이러한 내용은 다음 예에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-203">These are illustrated in the following examples.</span></span>  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a><span data-ttu-id="49468-204">예제: XML 스키마 컬렉션에 XML 네임스페이스 열거</span><span class="sxs-lookup"><span data-stu-id="49468-204">Example: Enumerate the XML Namespaces in an XML Schema Collection</span></span>  
 <span data-ttu-id="49468-205">XML 스키마 컬렉션 "myCollection"에 대해 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-205">Use the following query for the XML schema collection "myCollection":</span></span>  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a><span data-ttu-id="49468-206">예제: XML 스키마 컬렉션의 내용 열거</span><span class="sxs-lookup"><span data-stu-id="49468-206">Example: Enumerate the Contents of an XML Schema Collection</span></span>  
 <span data-ttu-id="49468-207">다음 문은 관계형 스키마 dbo 내에 있는 XML 스키마 컬렉션 "myCollection"의 내용을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-207">The following statement enumerates the contents of the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 <span data-ttu-id="49468-208">컬렉션 내의 개별 XML 스키마 `xml` 는 **XML_SCHEMA_NAMESPACE ()** 에 대 한 세 번째 인수로 대상 네임 스페이스를 지정 하 여 데이터 형식 인스턴스로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-208">Individual XML schemas within the collection can be obtained as `xml` data type instances by specifying the target namespace as the third argument to **XML_SCHEMA_NAMESPACE()**.</span></span> <span data-ttu-id="49468-209">이는 다음 예에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-209">This is shown in the following example.</span></span>  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a><span data-ttu-id="49468-210">예제: XML 스키마 컬렉션으로부터 지정된 스키마 출력</span><span class="sxs-lookup"><span data-stu-id="49468-210">Example: Output a Specified Schema from an XML Schema Collection</span></span>  
 <span data-ttu-id="49468-211">다음 명령문은 관계형 스키마 dbo 내에 있는 XML 스키마 컬렉션 "myCollection"으로부터 대상 네임스페이스가 <https://www.microsoft.com/books>인 XML 스키마를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-211">The following statement outputs the XML schema with the target namespace "<https://www.microsoft.com/books>" from the XML schema collection "myCollection" within the relational schema, dbo.</span></span>  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a><span data-ttu-id="49468-212">XML 스키마 쿼리</span><span class="sxs-lookup"><span data-stu-id="49468-212">Querying XML Schemas</span></span>  
 <span data-ttu-id="49468-213">XML 스키마 컬렉션에 로드한 XML 스키마를 다음과 같은 방식으로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-213">You can query XML schemas that you have loaded into XML schema collections in the following ways:</span></span>  
  
-   <span data-ttu-id="49468-214">XML 스키마 네임스페이스에 대한 카탈로그 뷰에서 Transact-SQL 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-214">Write Transact-SQL queries on catalog views for XML schema namespaces.</span></span>  
  
-   <span data-ttu-id="49468-215">`xml` 데이터 형식의 열이 포함된 테이블을 만들어서 XML 스키마를 저장하고 이를 XML 유형의 시스템으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-215">Create a table that contains an `xml` data type column to store your XML schemas and also load them into the XML type system.</span></span> <span data-ttu-id="49468-216">`xml` 데이터 형식의 메서드를 사용하여 XML 열을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-216">You can query the XML column by using the `xml` data type methods.</span></span> <span data-ttu-id="49468-217">또한 이 열에서 XML 인덱스를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49468-217">Also, you can build an XML index on this column.</span></span> <span data-ttu-id="49468-218">하지만 이 접근 방식에서는 애플리케이션이 XML 열에 저장된 XML 스키마와 XML 유형 시스템 간의 일관성을 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-218">However, with this approach, the application must maintain consistency between the XML schemas stored in the XML column and the XML type system.</span></span> <span data-ttu-id="49468-219">예를 들어 XML 유형 시스템으로부터 XML 스키마 네임스페이스를 삭제하면 일관성 유지를 위해 테이블에서도 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49468-219">For example, if you drop the XML schema namespace from the XML type system, you also have to drop it from the table in order to preserve consistency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49468-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49468-220">See Also</span></span>  
 <span data-ttu-id="49468-221">[저장된 XML 스키마 컬렉션 보기](../xml/view-a-stored-xml-schema-collection.md) </span><span class="sxs-lookup"><span data-stu-id="49468-221">[View a Stored XML Schema Collection](../xml/view-a-stored-xml-schema-collection.md) </span></span>  
 <span data-ttu-id="49468-222">[포함된 스키마를 병합하기 위해 스키마 전처리](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="49468-222">[Preprocess a Schema to Merge Included Schemas](../xml/preprocess-a-schema-to-merge-included-schemas.md) </span></span>  
 [<span data-ttu-id="49468-223">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="49468-223">Requirements and Limitations for XML Schema Collections on the Server</span></span>](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
