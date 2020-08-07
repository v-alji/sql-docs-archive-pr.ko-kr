---
title: Updategrams 소개 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
author: rothja
ms.author: jroth
ms.openlocfilehash: eb2f29d7f5d86d28254dacb9c55cceb9b4c72d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732447"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a><span data-ttu-id="7a9b4-102">Updategram 소개(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7a9b4-102">Introduction to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="7a9b4-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UPDATEGRAM 또는 OPENXML 함수를 사용 하 여 기존 XML 문서에서 데이터베이스를 수정 (삽입, 업데이트 또는 삭제) 할 수 있습니다 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="7a9b4-104">OPENXML 함수는 기존 XML 문서를 조각화하여 INSERT, UPDATE 또는 DELETE 문에 전달할 수 있는 행 집합을 제공함으로써 데이터베이스를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-104">The OPENXML function modifies a database by shredding the existing XML document and providing a rowset that can be passed to an INSERT, UPDATE, or DELETE statement.</span></span> <span data-ttu-id="7a9b4-105">OPENXML을 사용하면 작업이 데이터베이스 테이블에 대해 직접 수행되기 때문에</span><span class="sxs-lookup"><span data-stu-id="7a9b4-105">With OPENXML, operations are performed directly against the database tables.</span></span> <span data-ttu-id="7a9b4-106">OPENXML은 테이블과 같은 행 집합 공급자를 원본으로 표시할 수 있는 경우에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-106">Therefore, OPENXML is most appropriate wherever rowset providers, such as a table, can appear as a source.</span></span>  
  
 <span data-ttu-id="7a9b4-107">OPENXML과 마찬가지로 updategram을 사용하면 데이터베이스에서 데이터를 삽입, 업데이트 또는 삭제할 수 있습니다. 그러나 updategram은 주석 XSD(또는 XDR) 스키마에서 제공하는 XML 뷰에 대해 작업을 수행합니다. 예를 들면 매핑 스키마에서 제공하는 XML 뷰에 업데이트가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-107">Like OPENXML, an updategram allows you to insert, update, or delete data in the database; however, an updategram works against the XML views provided by the annotated XSD (or an XDR) schema; for example, the updates are applied to the XML view provided by the mapping schema.</span></span> <span data-ttu-id="7a9b4-108">매핑 스키마에는 XML 요소와 특성을 해당 데이터베이스 테이블과 열에 매핑하는 데 필요한 정보가 있으며</span><span class="sxs-lookup"><span data-stu-id="7a9b4-108">The mapping schema, in turn, has the necessary information to map XML elements and attributes to the corresponding database tables and columns.</span></span> <span data-ttu-id="7a9b4-109">updategram은 이 매핑 정보를 사용하여 데이터베이스 테이블과 열을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-109">The updategram uses this mapping information to update the database tables and columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a9b4-110">이 설명서에서는 사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 템플릿 및 매핑 스키마 지원에 대해 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-110">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7a9b4-111">자세한 내용은 주석이 추가 된 [XSD 스키마 소개 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-111">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="7a9b4-112">XDR을 사용 하는 레거시 응용 프로그램의 경우 [SQLXML 4.0&#41;에서 사용 되지 &#40;주석이 추가 된 Xdr 스키마 ](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-112">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="required-namespaces-in-the-updategram"></a><span data-ttu-id="7a9b4-113">Updategram의 필수 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="7a9b4-113">Required Namespaces in the Updategram</span></span>  
 <span data-ttu-id="7a9b4-114">Updategram의 키워드 (예: **\<sync>** , 및)는 **\<before>** **\<after>** `urn:schemas-microsoft-com:xml-updategram` 네임 스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-114">The keywords in an updategram, such as **\<sync>**, **\<before>**, and **\<after>**, exist in the `urn:schemas-microsoft-com:xml-updategram` namespace.</span></span> <span data-ttu-id="7a9b4-115">임의의 네임스페이스 접두사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-115">The namespace prefix that you use is arbitrary.</span></span> <span data-ttu-id="7a9b4-116">이 설명서에서 `updg` 접두사는 `updategram` 네임스페이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-116">In this documentation, the `updg` prefix denotes the `updategram` namespace.</span></span>  
  
## <a name="reviewing-syntax"></a><span data-ttu-id="7a9b4-117">구문 검토</span><span class="sxs-lookup"><span data-stu-id="7a9b4-117">Reviewing Syntax</span></span>  
 <span data-ttu-id="7a9b4-118">Updategram는 **\<sync>** **\<before>** **\<after>** updategram의 구문을 구성 하는, 및 블록이 포함 된 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-118">An updategram is a template with **\<sync>**, **\<before>**, and **\<after>** blocks that form the syntax of the updategram.</span></span> <span data-ttu-id="7a9b4-119">다음 코드에서는 가장 간단한 형태의 updategram 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-119">The following code shows this syntax in its simplest form:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="7a9b4-120">다음 정의는 각 블록의 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-120">The following definitions describe the role of each of these blocks:</span></span>  
  
 **\<before>**  
 <span data-ttu-id="7a9b4-121">레코드 인스턴스의 기존 상태("이전 상태"라고도 함)를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-121">Identifies the existing state (also called "the before state") of the record instance.</span></span>  
  
 **\<after>**  
 <span data-ttu-id="7a9b4-122">데이터가 변경될 새 상태를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-122">Identifies the new state to which data is to be changed.</span></span>  
  
 **\<sync>**  
 <span data-ttu-id="7a9b4-123">**\<before>** 및 블록을 포함 **\<after>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-123">Contains the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="7a9b4-124">블록은 둘 **\<sync>** 이상의 및 블록 집합을 포함할 수 있습니다 **\<before>** **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-124">A **\<sync>** block can contain more than one set of **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="7a9b4-125">및 블록 집합이 여러 개 있는 경우 **\<before>** **\<after>** 이러한 블록 (비어 있는 경우에도)은 쌍으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-125">If there is more than one set of **\<before>** and **\<after>** blocks, these blocks (even if they are empty) must be specified as pairs.</span></span> <span data-ttu-id="7a9b4-126">또한 updategram에는 두 개 이상의 블록이 있을 수 있습니다 **\<sync>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-126">Furthermore, an updategram can have more than one **\<sync>** block.</span></span> <span data-ttu-id="7a9b4-127">각 **\<sync>** 블록은 하나의 트랜잭션 단위입니다. 즉, 블록의 모든 항목을 **\<sync>** 수행 하거나 아무 것도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-127">Each **\<sync>** block is one unit of transaction (which means that either everything in the **\<sync>** block is done or nothing is done).</span></span> <span data-ttu-id="7a9b4-128">Updategram에서 여러 블록을 지정 하는 경우 **\<sync>** 한 블록의 오류는 다른 블록에 **\<sync>** 영향을 주지 않습니다 **\<sync>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-128">If you specify multiple **\<sync>** blocks in an updategram, the failure of one **\<sync>** block does not affect the other **\<sync>** blocks.</span></span>  
  
 <span data-ttu-id="7a9b4-129">Updategram가 레코드 인스턴스를 삭제, 삽입 또는 업데이트 하는지 여부는 및 블록의 내용에 따라 달라 집니다 **\<before>** **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-129">Whether an updategram deletes, inserts, or updates a record instance depends on the contents of the **\<before>** and **\<after>** blocks:</span></span>  
  
-   <span data-ttu-id="7a9b4-130">블록에 해당 하는 인스턴스가 없는 블록에만 레코드 인스턴스가 표시 되 면 **\<before>** **\<after>** updategram는 삭제 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-130">If a record instance appears only in the **\<before>** block with no corresponding instance in the **\<after>** block, the updategram performs a delete operation.</span></span>  
  
-   <span data-ttu-id="7a9b4-131">블록에 해당 하는 인스턴스가 없는 블록에만 레코드 인스턴스가 표시 되 면 **\<after>** **\<before>** 삽입 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-131">If a record instance appears only in the **\<after>** block with no corresponding instance in the **\<before>** block, it is an insert operation.</span></span>  
  
-   <span data-ttu-id="7a9b4-132">레코드 인스턴스가 블록에 표시 되 **\<before>** 고 블록에 해당 인스턴스가 있으면 **\<after>** 업데이트 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-132">If a record instance appears in the **\<before>** block and has a corresponding instance in the **\<after>** block, it is an update operation.</span></span> <span data-ttu-id="7a9b4-133">이 경우 updategram는 레코드 인스턴스를 블록에 지정 된 값으로 업데이트 합니다 **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-133">In this case, the updategram updates the record instance to the values that are specified in the **\<after>** block.</span></span>  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a><span data-ttu-id="7a9b4-134">Updategram에 매핑 스키마 지정</span><span class="sxs-lookup"><span data-stu-id="7a9b4-134">Specifying a Mapping Schema in the Updategram</span></span>  
 <span data-ttu-id="7a9b4-135">Updategram에는 매핑 스키마(XSD 및 XDR 스키마 모두 지원됨)에서 제공하는 XML 추상화를 암시적 또는 명시적으로 지정할 수 있습니다. 즉, updategram은 매핑 스키마가 지정되었는지 여부에 관계없이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-135">In an updategram, the XML abstraction that is provided by a mapping schema (both XSD and XDR schemas are supported) can be implicit or explicit (that is, an updategram can work with or without a specified mapping schema).</span></span> <span data-ttu-id="7a9b4-136">매핑 스키마를 지정 하지 않으면 updategram는 암시적 매핑 (기본 매핑)을 가정 합니다. 여기서 블록 또는 블록의 각 요소는 **\<before>** **\<after>** 테이블에 매핑되고 각 요소의 자식 요소 또는 특성은 데이터베이스의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-136">If you do not specify a mapping schema, the updategram assumes an implicit mapping (the default mapping), where each element in the **\<before>** block or **\<after>** block maps to a table and each element's child element or attribute maps to a column in the database.</span></span> <span data-ttu-id="7a9b4-137">매핑 스키마를 명시적으로 지정할 경우에는 updategram의 요소 및 특성이 매핑 스키마의 요소 및 특성과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-137">If you explicitly specify a mapping schema, the elements and attributes in the updategram must match the elements and attributes in the mapping schema.</span></span>  
  
### <a name="implicit-default-mapping"></a><span data-ttu-id="7a9b4-138">암시적(기본) 매핑</span><span class="sxs-lookup"><span data-stu-id="7a9b4-138">Implicit (default) Mapping</span></span>  
 <span data-ttu-id="7a9b4-139">일반적으로 간단한 업데이트를 수행하는 updategram에는 매핑 스키마가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-139">In most cases, an updategram that performs simple updates might not require a mapping schema.</span></span> <span data-ttu-id="7a9b4-140">이 경우에는 기본 매핑 스키마가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-140">In this case, the updategram relies on the default mapping schema.</span></span>  
  
 <span data-ttu-id="7a9b4-141">다음 updategram은 암시적 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-141">The following updategram demonstrates implicit mapping.</span></span> <span data-ttu-id="7a9b4-142">이 예에서 updategram은 Sales.Customer 테이블에 새 고객을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-142">In this example, the updategram inserts a new customer in the Sales.Customer table.</span></span> <span data-ttu-id="7a9b4-143">이 updategram는 암시적 매핑을 사용 하기 때문에 \<Sales.Customer> 요소는 sales. customer 테이블에 매핑되고 CustomerID 및 SalesPersonID 특성은 sales. customer 테이블의 해당 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-143">Because this updategram uses implicit mapping, the \<Sales.Customer> element maps to the Sales.Customer table, and the CustomerID and SalesPersonID attributes map to the corresponding columns in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a><span data-ttu-id="7a9b4-144">명시적 매핑</span><span class="sxs-lookup"><span data-stu-id="7a9b4-144">Explicit Mapping</span></span>  
 <span data-ttu-id="7a9b4-145">매핑 스키마(XSD 또는 XDR)를 지정하면 updategram은 이 스키마를 사용하여 업데이트할 대상 데이터베이스 테이블과 열을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-145">If you specify a mapping schema (either XSD or XDR), the updategram uses the schema to determine the database tables and columns that are to be updated.</span></span>  
  
 <span data-ttu-id="7a9b4-146">Updategram으로 복잡한 업데이트를 수행하는 경우, 예를 들면 매핑 스키마에 지정된 부모-자식 관계를 기준으로 여러 테이블에 레코드를 삽입하는 경우에는 updategram이 실행되는 대상 `mapping-schema` 특성을 사용하여 매핑 스키마를 명시적으로 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-146">If the updategram performs a complex update (for example, inserting records in multiple tables on the basis of the parent-child relationship that is specified in the mapping schema), you must explicitly provide the mapping schema by using the `mapping-schema` attribute against which the updategram executes.</span></span>  
  
 <span data-ttu-id="7a9b4-147">Updategram은 템플릿이기 때문에 updategram의 매핑 스키마에 대해 지정된 경로는 템플릿 파일의 위치(updategram이 저장된 위치)를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-147">Because an updategram is a template, the path specified for the mapping schema in the updategram is relative to the location of the template file (relative to where the updategram is stored).</span></span> <span data-ttu-id="7a9b4-148">자세한 내용은 [Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정 ](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-148">For more information, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a><span data-ttu-id="7a9b4-149">Updategram의 요소 중심 및 특성 중심 매핑</span><span class="sxs-lookup"><span data-stu-id="7a9b4-149">Element-centric and Attribute-centric Mapping in Updategrams</span></span>  
 <span data-ttu-id="7a9b4-150">Updategram에 매핑 스키마가 지정되지 않은 기본 매핑의 경우 updategram 요소는 테이블에 매핑되고 자식 요소(요소 중심 매핑)와 특성(특성 중심 매핑)은 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-150">With default mapping (when the mapping schema is not specified in the updategram), the updategram elements map to tables and the  child elements (in the case of element-centric mapping) and the attributes (in the case of attribute-centric mapping) map to columns.</span></span>  
  
### <a name="element-centric-mapping"></a><span data-ttu-id="7a9b4-151">요소 중심 매핑</span><span class="sxs-lookup"><span data-stu-id="7a9b4-151">Element-centric Mapping</span></span>  
 <span data-ttu-id="7a9b4-152">요소 중심 updategram의 경우 요소에는 요소의 속성을 나타내는 자식 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-152">In an element-centric updategram, an element contains child elements that denote the properties of the element.</span></span> <span data-ttu-id="7a9b4-153">한 가지 예로 다음 updategram을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-153">As an example, refer to the following updategram.</span></span> <span data-ttu-id="7a9b4-154">**\<Person.Contact>** 요소는 **\<FirstName>** 및 자식 요소를 포함 합니다 **\<LastName>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-154">The **\<Person.Contact>** element contains the **\<FirstName>** and **\<LastName>** child elements.</span></span> <span data-ttu-id="7a9b4-155">이러한 자식 요소는 요소의 속성입니다 **\<Person.Contact>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-155">These child elements are properties of the **\<Person.Contact>** element.</span></span>  
  
 <span data-ttu-id="7a9b4-156">이 updategram는 매핑 스키마를 지정 하지 않으므로 updategram는 암시적 매핑을 사용 합니다 **\<Person.Contact>** . 여기서 요소는 Person. Contact 테이블에 매핑되고 자식 요소는 FirstName 및 LastName 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-156">Because this updategram does not specify a mapping schema, the updategram uses implicit mapping, where the **\<Person.Contact>** element maps to the Person.Contact table and its child elements map to the FirstName and LastName columns.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a><span data-ttu-id="7a9b4-157">특성 중심 매핑</span><span class="sxs-lookup"><span data-stu-id="7a9b4-157">Attribute-centric Mapping</span></span>  
 <span data-ttu-id="7a9b4-158">특성 중심 매핑에서는 요소가 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-158">In an attribute-centric mapping, the elements have attributes.</span></span> <span data-ttu-id="7a9b4-159">다음 updategram은 특성 중심 매핑을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-159">The following updategram uses attribute-centric mapping.</span></span> <span data-ttu-id="7a9b4-160">이 예제에서 요소는 **\<Person.Contact>** **FirstName** 및 **LastName** 특성으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-160">In this example, the **\<Person.Contact>** element consists of the **FirstName** and **LastName** attributes.</span></span> <span data-ttu-id="7a9b4-161">이러한 특성은 요소의 속성입니다 **\<Person.Contact>** .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-161">These attributes are the properties of the **\<Person.Contact>** element.</span></span> <span data-ttu-id="7a9b4-162">앞의 예제와 같이이 updategram는 매핑 스키마를 지정 하지 않으므로 암시적 매핑을 사용 하 여 **\<Person.Contact>** 요소를 Person. Contact 테이블 및 요소의 특성을 테이블의 해당 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-162">As in the previous example, this updategram specifies no mapping schema, so it relies on implicit mapping to map the **\<Person.Contact>** element to the Person.Contact table and the element's attributes to the respective columns in the table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a><span data-ttu-id="7a9b4-163">요소 중심 및 특성 중심 매핑 모두 사용</span><span class="sxs-lookup"><span data-stu-id="7a9b4-163">Using Both Element-centric and Attribute-centric Mapping</span></span>  
 <span data-ttu-id="7a9b4-164">다음 updategram과 같이 요소 중심 및 특성 중심 매핑을 혼합하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-164">You can specify a mix of element-centric and attribute-centric mapping, as shown in the following updategram.</span></span> <span data-ttu-id="7a9b4-165">요소에는 **\<Person.Contact>** 특성과 자식 요소가 모두 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-165">Notice that the **\<Person.Contact>** element contains both an attribute and a child element.</span></span> <span data-ttu-id="7a9b4-166">또한 이 updategram에는 암시적 매핑이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-166">Also, this updategram relies on implicit mapping.</span></span> <span data-ttu-id="7a9b4-167">따라서 **FirstName** 특성과 **\<LastName>** 자식 요소는 Person. Contact 테이블의 해당 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-167">Thus, the **FirstName** attribute and the **\<LastName>** child element map to corresponding columns in the Person.Contact table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a><span data-ttu-id="7a9b4-168">SQL Server에서는 유효하지만 XML에서는 유효하지 않은 문자 사용</span><span class="sxs-lookup"><span data-stu-id="7a9b4-168">Working with Characters Valid in SQL Server but Not Valid in XML</span></span>  
 <span data-ttu-id="7a9b4-169">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 테이블 이름에 공백이 포함될 수 있지만</span><span class="sxs-lookup"><span data-stu-id="7a9b4-169">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space.</span></span> <span data-ttu-id="7a9b4-170">이러한 형식의 테이블 이름은 XML에서는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-170">However, this type of table name is not valid in XML.</span></span>  
  
 <span data-ttu-id="7a9b4-171">유효한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 식별자 이지만 유효한 XML 식별자가 아닌 문자를 인코딩하려면 ' __xHHHH \_ \_ '를 인코딩 값으로 사용 합니다. 여기서 HHHH는 가장 중요 한 비트 우선 순서로 문자에 대 한 4 자리 16 진수 UCS-2 코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-171">To encode characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but are not valid XML identifiers, use '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="7a9b4-172">이 인코딩 체계를 사용 하면 공백 문자가 x0020 (공백 문자에 대 한 4 자리 16 진수 코드)로 바뀝니다. 따라서의 테이블 이름 [Order Details]는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] \_ XML로 _x005B_Order_x0020_Details_x005D 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-172">Using this encoding scheme, a space character gets replaced with x0020 (the four-digit hexadecimal code for a space character); thus, the table name [Order Details] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] becomes _x005B_Order_x0020_Details_x005D\_ in XML.</span></span>  
  
 <span data-ttu-id="7a9b4-173">마찬가지로 세 부분으로 구성 된 요소 이름 (예:)을 지정 해야 할 수도 있습니다 \<[database].[owner].[table]> .</span><span class="sxs-lookup"><span data-stu-id="7a9b4-173">Similarly, you might need to specify three-part element names, such as \<[database].[owner].[table]>.</span></span> <span data-ttu-id="7a9b4-174">XML에서는 대괄호 문자 ([및])가 유효 하지 않기 때문에이를로 지정 해야 합니다 \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_> . 여기서 _x005B \_ 는 왼쪽 대괄호 ([)의 인코딩입니다 \_ . _x005D 오른쪽 대괄호 (])에 대 한 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-174">Because the bracket characters ([ and ]) are not valid in XML, you must specify this as \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, where _x005B\_ is the encoding for the left bracket ([) and _x005D\_ is the encoding for the right bracket (]).</span></span>  
  
## <a name="executing-updategrams"></a><span data-ttu-id="7a9b4-175">Updategram 실행</span><span class="sxs-lookup"><span data-stu-id="7a9b4-175">Executing Updategrams</span></span>  
 <span data-ttu-id="7a9b4-176">Updategram은 템플릿이기 때문에 템플릿의 모든 처리 메커니즘이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-176">Because an updategram is a template, all the processing mechanisms of a template apply to the updategram.</span></span> <span data-ttu-id="7a9b4-177">SQLXML 4.0에서는 다음 방법 중 하나로 updategram을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b4-177">For SQLXML 4.0, you can execute an updategram in either of the following ways:</span></span>  
  
-   <span data-ttu-id="7a9b4-178">ADO 명령으로 전송</span><span class="sxs-lookup"><span data-stu-id="7a9b4-178">By submitting it in an ADO command.</span></span>  
  
-   <span data-ttu-id="7a9b4-179">OLE DB 명령으로 전송</span><span class="sxs-lookup"><span data-stu-id="7a9b4-179">By submitting it as an OLE DB command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9b4-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a9b4-180">See Also</span></span>  
 [<span data-ttu-id="7a9b4-181">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="7a9b4-181">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
