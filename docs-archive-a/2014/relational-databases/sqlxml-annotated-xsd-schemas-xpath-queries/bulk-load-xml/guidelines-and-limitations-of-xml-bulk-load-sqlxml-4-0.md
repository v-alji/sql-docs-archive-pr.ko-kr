---
title: XML 대량 로드에 대 한 지침 및 제한 사항 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: rothja
ms.author: jroth
ms.openlocfilehash: 08c0020ac7b28702f5a573c6158ec9d50c735b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652749"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="c6957-102">XML 대량 로드에 대한 지침 및 제한 사항(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c6957-102">Guidelines and Limitations of XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="c6957-103">XML 대량 로드를 사용하려면 다음의 지침과 제한 사항을 알아 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-103">When you use XML Bulk Load, you should be familiar with the following guidelines and limitations:</span></span>  
  
-   <span data-ttu-id="c6957-104">인라인 스키마는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-104">Inline schemas are not supported.</span></span>  
  
     <span data-ttu-id="c6957-105">원본 XML 문서에 인라인 스키마가 있는 경우 XML 대량 로드에서 해당 스키마를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-105">If you have an inline schema in the source XML document, XML Bulk Load ignores that schema.</span></span> <span data-ttu-id="c6957-106">XML 데이터 외부의 XML 대량 로드에 대한 매핑 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-106">You specify the mapping schema for XML Bulk Load external to the XML data.</span></span> <span data-ttu-id="c6957-107">**Xmlns = "x:schema"** 특성을 사용 하 여 노드에서 매핑 스키마를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-107">You cannot specify the mapping schema at a node by using the **xmlns="x:schema"** attribute.</span></span>  
  
-   <span data-ttu-id="c6957-108">XML 문서는 형식만 검사되고 유효성은 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-108">An XML document is checked for being well-formed, but it is not validated.</span></span>  
  
     <span data-ttu-id="c6957-109">Xml 대량 로드는 xml 문서를 검사 하 여 제대로 구성 되었는지 여부를 확인 합니다. 즉, XML이 World Wide Web 컨소시엄 XML 1.0 권장 사항의 구문 요구 사항을 준수 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-109">XML Bulk Load checks the XML document to determine whether it is well-formed-that is, to ensure that the XML conforms to the syntax requirements of the World Wide Web Consortium's XML 1.0 recommendation.</span></span> <span data-ttu-id="c6957-110">문서 형식이 올바르지 않으면 XML 대량 로드에서 처리가 취소되고 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-110">If the document is not well-formed, XML Bulk Load cancels processing and returns an error.</span></span> <span data-ttu-id="c6957-111">그러나 문서가 조각인 경우(예: 문서에 단일 루트 요소가 없는 경우)에만 예외적으로 형식이 올바르지 않은 문서도 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-111">The only exception to this is when the document is a fragment (for example, the document has no single root element), in which case XML Bulk Load will load the document.</span></span>  
  
     <span data-ttu-id="c6957-112">XML 대량 로드는 XML 데이터 파일 안에 정의되거나 참조되는 XML 데이터 또는 DTD 스키마와 관련하여 문서의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-112">XML Bulk Load does not validate the document with respect to any XML-Data or DTD schema that is defined or referenced within the XML data file.</span></span> <span data-ttu-id="c6957-113">또한 XML 대량 로드에서는 제공된 매핑 스키마를 기준으로 XML 데이터 파일의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-113">In addition, XML Bulk Load does not validate the XML data file against the mapping schema supplied.</span></span>  
  
-   <span data-ttu-id="c6957-114">모든 XML 프롤로그 정보는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-114">Any XML prolog information is ignored.</span></span>  
  
     <span data-ttu-id="c6957-115">XML 대량 로드는 XML 문서에서 요소 앞과 뒤에 있는 모든 정보를 무시 \<root> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-115">XML Bulk Load ignores all the information before and after the \<root> element in the XML document.</span></span> <span data-ttu-id="c6957-116">예를 들어 모든 XML 선언, 내부 DTD 정의, 외부 DTD 참조, 주석 등은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-116">For example, XML Bulk Load ignores any XML declarations, internal DTD definitions, external DTD references, comments, and so on.</span></span>  
  
-   <span data-ttu-id="c6957-117">두 테이블(예: Customer 테이블과 CustOrder 테이블) 간의 기본 키/외래 키 관계를 정의하는 매핑 스키마가 있는 경우, 스키마에서 기본 키가 들어 있는 테이블 설명이 먼저 나오고</span><span class="sxs-lookup"><span data-stu-id="c6957-117">If you have a mapping schema that defines a primary key/foreign key relationship between two tables (such as between Customer and CustOrder), the table with the primary key must be described first in the schema.</span></span> <span data-ttu-id="c6957-118">외래 키 열이 들어 있는 테이블이 그 다음에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-118">The table with the foreign key column must appear later in the schema.</span></span> <span data-ttu-id="c6957-119">그 이유는 스키마에서 테이블이 식별 되는 순서는 데이터베이스에 로드 하는 데 사용 되는 순서 이기 때문입니다. 예를 들어 다음 XDR 스키마는 요소 앞에 요소를 설명 하므로 XML 대량 로드에서 사용 하는 경우 오류를 생성 합니다 **\<Order>** **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="c6957-119">The reason for this is that the order in which the tables are identified in the schema is the order that is used to load them into the database.For example, the following XDR schema will produce an error when it is used in XML Bulk Load because the **\<Order>** element is described before the **\<Customer>** element.</span></span> <span data-ttu-id="c6957-120">여기서 CustOrder의 CustomerID 열은 Cust 테이블의 CustomerID 기본 키 열을 참조하는 외래 키 열입니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-120">The CustomerID column in CustOrder is a foreign key column that refers to the CustomerID primary key column in the Cust table.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   <span data-ttu-id="c6957-121">스키마에서 `sql:overflow-field` 주석을 사용하여 오버플로 열을 지정하지 않으면 XML 대량 로드는 XML 문서에는 있지만 매핑 스키마에는 설명되지 않은 모든 데이터를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-121">If the schema does not specify overflow columns by using the `sql:overflow-field` annotation, XML Bulk Load ignores any data that is present in the XML document but is not described in the mapping schema.</span></span>  
  
     <span data-ttu-id="c6957-122">XML 대량 로드는 알려진 태그가 XML 데이터 스트림에서 발견될 때마다 사용자가 지정한 매핑 스키마를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-122">XML Bulk Load applies the mapping schema that you have specified whenever it encounters known tags in the XML data stream.</span></span> <span data-ttu-id="c6957-123">그러나 XML 문서에는 포함되었지만 스키마에 설명되지 않은 데이터는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-123">It ignores data that is present in the XML document but is not described in the schema.</span></span> <span data-ttu-id="c6957-124">예를 들어 요소를 설명 하는 매핑 스키마가 있다고 가정 **\<Customer>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-124">For example, assume you have a mapping schema that describes a **\<Customer>** element.</span></span> <span data-ttu-id="c6957-125">XML 데이터 파일에는 **\<AllCustomers>** 모든 요소를 포함 하는 루트 태그 (스키마에 설명 되어 있지 않음)가 있습니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="c6957-125">The XML data file has an **\<AllCustomers>** root tag (which is not described in the schema) that encloses all the **\<Customer>** elements:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="c6957-126">이 경우 XML 대량 로드는 요소를 무시 **\<AllCustomers>** 하 고 요소에 대 한 매핑을 시작 **\<Customer>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-126">In this case, XML Bulk Load ignores the **\<AllCustomers>** element and begins mapping at the **\<Customer>** element.</span></span> <span data-ttu-id="c6957-127">XML 대량 로드는 XML 문서에는 있지만 스키마에는 설명되어 있지 않은 모든 요소를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-127">XML Bulk Load ignores the elements that are not described in the schema but are present in the XML document.</span></span>  
  
     <span data-ttu-id="c6957-128">요소가 포함 된 다른 XML 원본 데이터 파일을 고려 **\<Order>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-128">Consider another XML source data file that contains **\<Order>** elements.</span></span> <span data-ttu-id="c6957-129">이러한 요소는 매핑 스키마에 설명되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-129">These elements are not described in the mapping schema:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="c6957-130">XML 대량 로드는 이러한 **\<Order>** 요소를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-130">XML Bulk Load ignores these **\<Order>** elements.</span></span> <span data-ttu-id="c6957-131">그러나 `sql:overflow-field` 스키마에서 주석을 사용 하 여 열을 오버플로 열로 식별 하는 경우 XML 대량 로드는이 열에 사용 되지 않은 모든 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-131">But if you use the `sql:overflow-field`annotation in the schema to identify a column as an overflow column, XML Bulk Load stores all unconsumed data in this column.</span></span>  
  
-   <span data-ttu-id="c6957-132">CDATA 섹션과 엔터티 참조는 데이터베이스에 저장되기 전에 해당하는 문자열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-132">CDATA sections and entity references are translated to their string equivalents before they are stored in the database.</span></span>  
  
     <span data-ttu-id="c6957-133">이 예제에서 CDATA 섹션은 요소에 대 한 값을 래핑합니다 **\<City>** .</span><span class="sxs-lookup"><span data-stu-id="c6957-133">In this example, a CDATA section wraps the value for the **\<City>** element.</span></span> <span data-ttu-id="c6957-134">XML 대량 로드는 요소를 데이터베이스에 삽입 하기 전에 문자열 값 ("요소")을 추출 합니다 **\<City>** .</span><span class="sxs-lookup"><span data-stu-id="c6957-134">XML Bulk Load extracts the string value ("NY") before it inserts the **\<City>** element into the database.</span></span>  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     <span data-ttu-id="c6957-135">XML 대량 로드는 엔터티 참조를 유지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-135">XML Bulk Load does not preserve entity references.</span></span>  
  
-   <span data-ttu-id="c6957-136">매핑 스키마에서 특성의 기본값을 지정하고 XML 원본 데이터에 해당 특성이 없으면, XML 대량 로드는 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-136">If the mapping schema specifies the default value for an attribute and the XML source data does not contain that attribute, XML Bulk Load uses the default value.</span></span>  
  
     <span data-ttu-id="c6957-137">다음 샘플 XDR 스키마는 기본값을 **HireDate** 특성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-137">The following sample XDR schema assigns a default value to the **HireDate** attribute:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     <span data-ttu-id="c6957-138">이 XML 데이터에서 두 번째 요소에는 **HireDate** 특성이 없습니다 **\<Customers>** .</span><span class="sxs-lookup"><span data-stu-id="c6957-138">In this XML data, the **HireDate** attribute is missing from the second **\<Customers>** element.</span></span> <span data-ttu-id="c6957-139">XML 대량 로드는 데이터베이스에 두 번째 **\<Customers>** 요소를 삽입할 때 스키마에 지정 된 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-139">When XML Bulk Load inserts the second **\<Customers>** element into the database, it uses the default value that is specified in the schema.</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   <span data-ttu-id="c6957-140">`sql:url-encode` 주석은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-140">The `sql:url-encode` annotation is not supported:</span></span>  
  
     <span data-ttu-id="c6957-141">XML 데이터 입력에 URL을 지정하면 대량 로드는 해당 위치에서 데이터를 읽지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-141">You cannot specify a URL in the XML data input and expect Bulk Load to read data from that location.</span></span>  
  
     <span data-ttu-id="c6957-142">매핑 스키마에 식별된 테이블이 생성됩니다(데이터베이스가 존재해야 함).</span><span class="sxs-lookup"><span data-stu-id="c6957-142">The tables that are identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="c6957-143">하나 이상의 테이블이 데이터베이스에 이미 있는 경우 SGDropTables 속성은 이러한 기존 테이블을 삭제 하 고 다시 만들지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-143">If one or more of the tables already exists in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
-   <span data-ttu-id="c6957-144">SchemaGen 속성 (예: SchemaGen = true)을 지정 하면 매핑 스키마에서 식별 된 테이블이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-144">If you specify the SchemaGen property (for example, SchemaGen = true), the tables that are identified in the mapping schema are created.</span></span> <span data-ttu-id="c6957-145">그러나 SchemaGen은 다음과 같은 한 가지 예외를 제외 하 고 이러한 테이블에 제약 조건 (예: PRIMARY KEY/FOREIGN KEY 제약 조건)을 만들지 않습니다. 관계의 기본 키를 구성 하는 XML 노드가 ID XML 유형 (XSD의 경우)으로 정의 되 `type="xsd:ID"` 고 SGUseID 속성이 True로 설정 된 경우에는 id 유형의 노드에서 만든 기본 키가 아니라 기본 키/외래 키 관계가 매핑 스키마 관계에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-145">But SchemaGen does not create any constraints (such as the PRIMARY KEY/FOREIGN KEY constraints) on these tables with one exception: If the XML nodes that constitute the primary key in a relationship are defined as having an XML type of ID (that is, `type="xsd:ID"` for XSD) AND the SGUseID property is set to True for SchemaGen, then not only are primary keys created from the ID typed nodes, but primary key/foreign key relationships are created from mapping schema relationships.</span></span>  
  
-   <span data-ttu-id="c6957-146">SchemaGen은 XSD 스키마 패싯 및 확장을 사용 하 여 관계형 스키마를 생성 하지 않습니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6957-146">SchemaGen does not use XSD schema facets and extensions to generate the relational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schema.</span></span>  
  
-   <span data-ttu-id="c6957-147">대량 로드에서 SchemaGen 속성 (예: SchemaGen = true)을 지정 하면 지정 된 테이블 (공유 이름의 뷰 아님)만 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-147">If you specify the SchemaGen property (for example, SchemaGen = true) on Bulk Load, only tables (and not views of shared name) that are specified are updated.</span></span>  
  
-   <span data-ttu-id="c6957-148">SchemaGen은 주석이 추가 된 XSD에서 관계형 스키마를 생성 하는 기본 기능만 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-148">SchemaGen only provides basic functionality for generating the relational schema from annotated XSD.</span></span> <span data-ttu-id="c6957-149">필요한 경우 생성된 테이블을 사용자가 직접 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-149">The user should modify the generated tables manually, if needed.</span></span>  
  
-   <span data-ttu-id="c6957-150">테이블 간에 관계가 있는 경우 SchemaGen은 두 테이블 간에 관련 된 모든 키를 포함 하는 단일 관계를 만들려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-150">Where more than relationship exists between tables,SchemaGen tries to create a single relationship that includes all the keys involved between the two tables.</span></span> <span data-ttu-id="c6957-151">이 제한 사항은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 오류의 원인이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-151">This limitation might be the cause of a [!INCLUDE[tsql](../../../includes/tsql-md.md)] error.</span></span>  
  
-   <span data-ttu-id="c6957-152">XML 데이터를 데이터베이스에 대량 로드할 경우 데이터베이스 열에 매핑되는 특성 또는 자식 요소가 매핑 스키마에 적어도 하나 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-152">When you are bulk loading XML data into a database, there must be at least one attribute or child element in the mapping schema that is mapped to a database column.</span></span>  
  
-   <span data-ttu-id="c6957-153">XML 대량 로드를 사용하여 날짜 값을 삽입할 경우 값을 (-)CCYY-MM-DD((+-)TZ) 형식으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-153">If you are inserting date values by using XML Bulk Load, the values must be specified in the (-)CCYY-MM-DD((+-)TZ) format.</span></span> <span data-ttu-id="c6957-154">이 형식은 날짜에 대한 표준 XSD 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-154">This is the standard XSD format for the date.</span></span>  
  
-   <span data-ttu-id="c6957-155">일부 속성 플래그는 다른 속성 플래그와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-155">Some property flags are not compatible with other property flags.</span></span> <span data-ttu-id="c6957-156">예를 들어 대량 로드는 `Ignoreduplicatekeys=true`와 `Keepidentity=false`를 동시에 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-156">For example, bulk load does not support `Ignoreduplicatekeys=true` together with `Keepidentity=false`.</span></span> <span data-ttu-id="c6957-157">`Keepidentity=false`이면 대량 로드에서는 서버를 통해 키 값이 생성되는 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-157">When `Keepidentity=false`, bulk load expects the server to generate the key values.</span></span> <span data-ttu-id="c6957-158">테이블에는 키에 대한 `IDENTITY` 제약 조건이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-158">Tables should have an `IDENTITY` constraint on the key.</span></span> <span data-ttu-id="c6957-159">서버에서는 중복 키를 생성하지 않으므로 `Ignoreduplicatekeys`를 `true`로 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-159">The server will not generate duplicate keys, which means there is no need for `Ignoreduplicatekeys` to be set to `true`.</span></span> <span data-ttu-id="c6957-160">행이 있는 테이블로 가져온 데이터로부터 기본 키 값을 업로드하고 기본 키가 충돌할 가능성이 있는 경우에만 `Ignoreduplicatekeys`를 `true`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6957-160">`Ignoreduplicatekeys` should be set to `true` only when uploading primary key values from the incoming data into a table that has rows and there is a potential for conflict of primary key values.</span></span>  
  
  
