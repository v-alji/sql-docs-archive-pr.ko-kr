---
title: 형식화된 XML과 형식화되지 않은 XML 비교 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- parameters [XML in SQL Server]
- facets [XML in SQL Server]
- xml data type [SQL Server], columns
- untyped XML
- xml data type [SQL Server], typed xml
- XML [SQL Server], typed
- variables [XML in SQL Server], creating
- xml data type [SQL Server], untyped xml
- columns [XML in SQL Server], creating
- typed XML
- document mode processing [SQL Server]
- XML [SQL Server], untyped
- xml data type [SQL Server], parameters
ms.assetid: 4bc50af9-2f7d-49df-bb01-854d080c72c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fae9ca930bd8741a1332b61c8272f2133590483e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730256"
---
# <a name="compare-typed-xml-to-untyped-xml"></a><span data-ttu-id="d8e75-102">형식화된 XML과 형식화되지 않은 XML 비교</span><span class="sxs-lookup"><span data-stu-id="d8e75-102">Compare Typed XML to Untyped XML</span></span>
  <span data-ttu-id="d8e75-103">`xml` 유형의 변수, 매개 변수 및 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-103">You can create variables, parameters, and columns of the `xml` type.</span></span> <span data-ttu-id="d8e75-104">선택적으로 XML 스키마 컬렉션을 `xml` 유형의 변수, 매개 변수 또는 열과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-104">You can optionally associate a collection of XML schemas with a variable, parameter, or column of `xml` type.</span></span> <span data-ttu-id="d8e75-105">이 경우 `xml` 데이터 형식 인스턴스를 *형식화*됨 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-105">In this case, the `xml` data type instance is called *typed*.</span></span> <span data-ttu-id="d8e75-106">그 외의 경우에는 XML 인스턴스를 *형식화되지 않았다*고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-106">Otherwise, the XML instance is called *untyped*.</span></span>  
  
## <a name="well-formed-xml-and-the-xml-data-type"></a><span data-ttu-id="d8e75-107">올바른 형식의 XML 및 xml 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d8e75-107">Well-formed XML and the xml Data Type</span></span>  
 <span data-ttu-id="d8e75-108">`xml` 데이터 형식은 ISO 표준 `xml` 데이터 형식을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-108">The `xml` data type implements the ISO standard `xml` data type.</span></span> <span data-ttu-id="d8e75-109">따라서 올바른 형식의 XML 버전 1.0 문서를 저장할 수 있으며 텍스트 노드 및 형식화되지 않은 XML 열의 최상위 요소가 임의의 개수로 포함된 XML 내용 조각을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-109">Therefore, it can store well-formed XML version 1.0 documents and also so-called XML content fragments with text nodes and an arbitrary number of top-level elements in an untyped XML column.</span></span> <span data-ttu-id="d8e75-110">시스템은 데이터가 올바른 형식인지 확인하고, 열이 XML 스키마로 바인딩되도록 요구하지 않으며, 넓은 의미에서 올바른 형식이 아닌 데이터를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-110">The system checks that the data is well-formed, does not require the column to be bound to XML schemas, and rejects data that is not well-formed in the extended sense.</span></span> <span data-ttu-id="d8e75-111">형식화되지 않은 XML 변수 및 매개 변수도 여기에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-111">This is true also of untyped XML variables and parameters.</span></span>  
  
## <a name="xml-schemas"></a><span data-ttu-id="d8e75-112">XML 스키마</span><span class="sxs-lookup"><span data-stu-id="d8e75-112">XML Schemas</span></span>  
 <span data-ttu-id="d8e75-113">XML 스키마는 다음을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-113">An XML schema provides the following:</span></span>  
  
-   <span data-ttu-id="d8e75-114">**유효성 검사 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="d8e75-114">**Validation constraints.**</span></span> <span data-ttu-id="d8e75-115">형식화된 xml 인스턴스가 할당 또는 수정될 때마다 SQL Sever가 인스턴스의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-115">Whenever a typed xml instance is assigned to or modified, SQL Server validates the instance.</span></span>  
  
-   <span data-ttu-id="d8e75-116">**데이터 형식 정보**</span><span class="sxs-lookup"><span data-stu-id="d8e75-116">**Data type information.**</span></span> <span data-ttu-id="d8e75-117">스키마는 `xml` 데이터 형식 인스턴스에 있는 특성 및 요소의 유형에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-117">Schemas provide information about the types of attributes and elements in the `xml` data type instance.</span></span> <span data-ttu-id="d8e75-118">유형 정보는 인스턴스에 포함되어 있는 값에 대해 형식화되지 않은 `xml`에 있을 수 있는 것보다 정확한 작업 의미를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-118">The type information provides more precise operational semantics to the values contained in the instance than is possible with untyped `xml`.</span></span> <span data-ttu-id="d8e75-119">예를 들어 숫자 산술 연산은 문자열 값이 10진수 값에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-119">For example, decimal arithmetic operations can be performed on a decimal value, but not on a string value.</span></span> <span data-ttu-id="d8e75-120">따라서 형식화된 XML 스토리지는 형식화되지 않은 XML보다 더욱 간결하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-120">Because of this, typed XML storage can be made significantly more compact than untyped XML.</span></span>  
  
## <a name="choosing-typed-or-untyped-xml"></a><span data-ttu-id="d8e75-121">형식화된 XML 또는 형식화되지 않은 XML 선택</span><span class="sxs-lookup"><span data-stu-id="d8e75-121">Choosing Typed or Untyped XML</span></span>  
 <span data-ttu-id="d8e75-122">다음 경우에 형식화되지 않은 `xml` 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-122">Use untyped `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="d8e75-123">XML 데이터에 대한 스키마가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-123">You do not have a schema for your XML data.</span></span>  
  
-   <span data-ttu-id="d8e75-124">스키마가 있지만 서버에서 데이터 유효성 검사를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-124">You have schemas, but you do not want the server to validate the data.</span></span> <span data-ttu-id="d8e75-125">이러한 경우는 데이터를 서버에 저장하기 전에 애플리케이션이 클라이언트 쪽 유효성 검사를 수행하거나, 스키마에 대해 유효하지 않은 XML 데이터를 임시적으로 저장하거나, 서버에서 지원되지 않는 스키마 구성 요소를 사용하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-125">This is sometimes the case when an application performs client-side validation before storing the data at the server, or temporarily stores XML data that is invalid according to the schema, or uses schema components that are not supported at the server.</span></span>  
  
 <span data-ttu-id="d8e75-126">`xml`다음과 같은 상황에서 형식화 된 데이터 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-126">Use typed `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="d8e75-127">XML 데이터에 대한 스키마가 있으며 이 XML 스키마에 따라 서버에서 XML 데이터의 유효성을 검사하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-127">You have schemas for your XML data and you want the server to validate your XML data according to the XML schemas.</span></span>  
  
-   <span data-ttu-id="d8e75-128">형식 정보에 따라 스토리지 및 쿼리 최적화를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-128">You want to take advantage of storage and query optimizations based on type information.</span></span>  
  
-   <span data-ttu-id="d8e75-129">쿼리 컴파일 시 형식 정보를 더욱 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-129">You want to take better advantage of type information during compilation of your queries.</span></span>  
  
 <span data-ttu-id="d8e75-130">형식화된 XML 열, 매개 변수 및 변수는 XML 문서 또는 내용을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-130">Typed XML columns, parameters, and variables can store XML documents or content.</span></span> <span data-ttu-id="d8e75-131">그러나 선언 시 문서를 저장하는지 아니면 내용을 저장하는지에 따라 플래그를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-131">However, you have to specify with a flag whether you are storing a document or content at the time of declaration.</span></span> <span data-ttu-id="d8e75-132">또한 XML 스키마의 컬렉션을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-132">Additionally, you have to provide the collection of XML schemas.</span></span> <span data-ttu-id="d8e75-133">각 XML 인스턴스에 정확히 하나의 최상위 요소가 있는 경우 DOCUMENT를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-133">Specify DOCUMENT if each XML instance has exactly one top-level element.</span></span> <span data-ttu-id="d8e75-134">그렇지 않으면 CONTENT를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-134">Otherwise, use CONTENT.</span></span> <span data-ttu-id="d8e75-135">쿼리 컴파일러는 쿼리 컴파일 중에 형식 검사에서 DOCUMENT 플래그를 사용하여 단일 항목인 최상위 요소를 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-135">The query compiler uses the DOCUMENT flag in type checks during query compilation to infer singleton top-level elements.</span></span>  
  
## <a name="creating-typed-xml"></a><span data-ttu-id="d8e75-136">형식화된 XML 만들기</span><span class="sxs-lookup"><span data-stu-id="d8e75-136">Creating Typed XML</span></span>  
 <span data-ttu-id="d8e75-137">형식화 `xml` 된 변수, 매개 변수 또는 열을 만들려면 먼저 [transact-sql&#41;&#40;CREATE XML schema collection ](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)을 사용 하 여 xml 스키마 컬렉션을 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-137">Before you can create typed `xml` variables, parameters, or columns, you must first register the XML schema collection by using [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span> <span data-ttu-id="d8e75-138">그런 다음 XML 스키마 컬렉션을 `xml` 데이터 형식의 변수, 매개 변수 또는 열과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-138">You can then associate the XML schema collection with variables, parameters, or columns of the `xml` data type.</span></span>  
  
 <span data-ttu-id="d8e75-139">다음 예에서는 XML 스키마 컬렉션 이름을 지정하기 위해 두 부분으로 된 명명 규칙이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-139">In the following examples, a two-part naming convention is used for specifying the XML schema collection name.</span></span> <span data-ttu-id="d8e75-140">첫 번째 부분은 스키마 이름이고 두 번째 부분은 XML 스키마 컬렉션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-140">The first part is the schema name, and the second part is the XML schema collection name.</span></span>  
  
### <a name="example-associating-a-schema-collection-with-an-xml-type-variable"></a><span data-ttu-id="d8e75-141">예제: xml 유형 변수와 스키마 컬렉션 연결</span><span class="sxs-lookup"><span data-stu-id="d8e75-141">Example: Associating a Schema Collection with an xml Type Variable</span></span>  
 <span data-ttu-id="d8e75-142">다음 예에서는 `xml` 형식 변수를 만들고이를 스키마 컬렉션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-142">The following example creates an`xml` type variable and associates a schema collection with it.</span></span> <span data-ttu-id="d8e75-143">이 예에서 지정된 스키마 컬렉션은 이미 **AdventureWorks** 데이터베이스로 가져온 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-143">The schema collection specified in the example is already imported in the **AdventureWorks** database.</span></span>  
  
```  
DECLARE @x xml (Production.ProductDescriptionSchemaCollection);   
```  
  
### <a name="example-specifying-a-schema-for-an-xml-type-column"></a><span data-ttu-id="d8e75-144">예제: xml 유형 열에 스키마 지정</span><span class="sxs-lookup"><span data-stu-id="d8e75-144">Example: Specifying a Schema for an xml Type Column</span></span>  
 <span data-ttu-id="d8e75-145">다음 예에서는 `xml` 유형 열이 포함된 테이블을 만들고 이 열에 대한 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-145">The following example creates a table with an `xml` type column and specifies a schema for the column:</span></span>  
  
```  
CREATE TABLE T1(  
 Col1 int,   
 Col2 xml (Production.ProductDescriptionSchemaCollection)) ;  
```  
  
### <a name="example-passing-an-xml-type-parameter-to-a-stored-procedure"></a><span data-ttu-id="d8e75-146">예제: xml 유형 매개 변수를 저장 프로시저에 전달</span><span class="sxs-lookup"><span data-stu-id="d8e75-146">Example: Passing an xml Type Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="d8e75-147">다음 예에서는 `xml` 유형 매개 변수를 저장 프로시저에 전달하고 해당 변수에 대한 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-147">The following example passes an `xml` type parameter to a stored procedure and specifies a schema for the variable:</span></span>  
  
```  
CREATE PROCEDURE SampleProc   
  @ProdDescription xml (Production.ProductDescriptionSchemaCollection)   
AS   
...  
```  
  
 <span data-ttu-id="d8e75-148">XML 스키마 컬렉션에 대한 다음 내용에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8e75-148">Note the following about the XML schema collection:</span></span>  
  
-   <span data-ttu-id="d8e75-149">XML 스키마 컬렉션은 [XML 스키마 컬렉션 만들기](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)를 사용하여 등록한 데이터베이스에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-149">An XML schema collection is available only in the database in which it was registered by using [Creating an XML Schema Collection](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span>  
  
-   <span data-ttu-id="d8e75-150">또한 문자열을 형식화된 `xml` 데이터 형식으로 캐스팅하는 경우 구문 분석 시 지정된 컬렉션에 있는 XML 스키마 네임스페이스에 따라 유효성 검사와 형식 지정도 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-150">If you cast from a string to a typed `xml` data type, the parsing also performs validation and typing, based on the XML schema namespaces in the collection specified.</span></span>  
  
-   <span data-ttu-id="d8e75-151">형식화된 `xml` 데이터 형식을 형식화되지 않은 `xml` 데이터 형식으로 캐스팅하거나 그 반대로도 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-151">You can cast from a typed `xml` data type to an untyped `xml` data type, and vice versa.</span></span>  
  
 <span data-ttu-id="d8e75-152">SQL Server에서 XML을 생성하는 다른 방법은 [XML 데이터 인스턴스 만들기](create-instances-of-xml-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d8e75-152">For more information about other ways to generate XML in SQL Server, see [Create Instances of XML Data](create-instances-of-xml-data.md).</span></span> <span data-ttu-id="d8e75-153">XML을 생성한 후 `xml` 데이터 형식 변수에 할당하거나 `xml` 유형 열에 저장하여 추가 처리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-153">After XML is generated, it can be assigned either to an `xml` data type variable or stored in `xml` type columns for additional processing.</span></span>  
  
 <span data-ttu-id="d8e75-154">데이터 형식 계층에서 `xml` 데이터 형식은 `sql_variant` 및 사용자 정의 형식 아래, 기본 제공 유형 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-154">In the data type hierarchy, the `xml` data type appears below `sql_variant` and user-defined types, but above any of the built-in types.</span></span>  
  
### <a name="example-specifying-facets-to-constrain-a-typed-xml-column"></a><span data-ttu-id="d8e75-155">예제: 형식화된 xml 열을 제한하기 위한 패싯 지정</span><span class="sxs-lookup"><span data-stu-id="d8e75-155">Example: Specifying Facets to Constrain a Typed xml Column</span></span>  
 <span data-ttu-id="d8e75-156">형식화된 `xml` 열의 경우 열에 저장된 각 인스턴스에 대해 최상위의 단일 요소만 허용하도록 열을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-156">For typed `xml` columns, you can constrain the column to allow only single, top-level elements for each instance stored in it.</span></span> <span data-ttu-id="d8e75-157">이렇게 하려면 다음 예에서와 같이 테이블을 만들 때 선택 항목인 `DOCUMENT` 패싯을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-157">You do this by specifying the optional `DOCUMENT` facet when a table is created, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml   
   (DOCUMENT Production.ProductDescriptionSchemaCollection));  
GO  
DROP TABLE T;  
GO  
```  
  
 <span data-ttu-id="d8e75-158">기본적으로 형식화된 `xml` 열에 저장된 인스턴스는 XML 문서가 아닌 XML 콘텐츠로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-158">By default, instances stored in the typed `xml` column are stored as XML content and not as XML documents.</span></span> <span data-ttu-id="d8e75-159">이러한 설정은 다음의 경우에 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-159">This allows for the following:</span></span>  
  
-   <span data-ttu-id="d8e75-160">0개 이상의 최상위 요소</span><span class="sxs-lookup"><span data-stu-id="d8e75-160">Zero or many top-level elements</span></span>  
  
-   <span data-ttu-id="d8e75-161">최상위 요소에 있는 텍스트 노드</span><span class="sxs-lookup"><span data-stu-id="d8e75-161">Text nodes in top-level elements</span></span>  
  
 <span data-ttu-id="d8e75-162">또한 다음 예에서와 같이 `CONTENT` 패싯을 추가하여 이 동작을 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-162">You can also explicitly specify this behavior by adding `CONTENT` facet, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml(CONTENT Production.ProductDescriptionSchemaCollection));  
GO -- Default  
```  
  
 <span data-ttu-id="d8e75-163">`xml` 유형(형식화된 xml)을 정의할 때 항상 선택 항목인 DOCUMENT/CONTENT 패싯을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-163">Note that you can specify the optional DOCUMENT/CONTENT facets anywhere you define `xml` type (typed xml).</span></span> <span data-ttu-id="d8e75-164">예를 들어 형식화된 `xml` 변수를 만들 때 다음과 같이 DOCUMENT/CONTENT 패싯을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-164">For example, when you create a typed `xml` variable, you can add the DOCUMENT/CONTENT facet, as shown in the following:</span></span>  
  
```  
declare @x xml (DOCUMENT Production.ProductDescriptionSchemaCollection);  
```  
  
## <a name="document-type-definition-dtd"></a><span data-ttu-id="d8e75-165">DTD(문서 유형 정의)</span><span class="sxs-lookup"><span data-stu-id="d8e75-165">Document Type Definition (DTD)</span></span>  
 <span data-ttu-id="d8e75-166">`xml` 데이터 형식의 열, 변수 및 매개 변수는 DTD가 아닌 XML 스키마를 사용하여 형식화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-166">The `xml` data type columns, variables, and parameters can be typed by using XML schema, but not by using DTD.</span></span> <span data-ttu-id="d8e75-167">하지만 인라인 DTD는 형식화되지 않은 XML 및 형식화된 XML에 모두 사용하여 기본값을 제공하고 엔터티 참조를 해당 확장 형식으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-167">However, inline DTD can be used for both untyped and typed XML to supply default values and to replace entity references with their expanded form.</span></span>  
  
 <span data-ttu-id="d8e75-168">타사 도구를 사용하여 DTD를 XML 스키마 문서로 변환하고 XML 스키마를 데이터베이스에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-168">You can convert DTDs to XML schema documents by using third-party tools, and load the XML schemas into the database.</span></span>  
  
## <a name="upgrading-typed-xml-from-sql-server-2005"></a><span data-ttu-id="d8e75-169">SQL Server 2005에서 형식화된 XML 업그레이드</span><span class="sxs-lookup"><span data-stu-id="d8e75-169">Upgrading Typed XML from SQL Server 2005</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="d8e75-170">에서는 XML 스키마 지원이 여러 가지로 확대되었습니다. 여기에는 lax 유효성 검사에 대한 지원, 향상된 **xs:date**, **xs:time** 및 **xs:dateTime** 인스턴스 데이터 처리, 목록 유형 및 공용 구조체 유형에 대한 추가 지원이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-170">made several extensions to the XML Schema support, including support for lax validation, improved handling of **xs:date**, **xs:time** and **xs:dateTime** instance data, and added support for list and union types.</span></span> <span data-ttu-id="d8e75-171">대부분의 경우 변경 사항이 업그레이드에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-171">In most cases the changes do not affect the upgrade experience.</span></span> <span data-ttu-id="d8e75-172">그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] xs:date **,** xs:time **또는**xs:dateTime **형식이나 하위 형식의 값을 사용할 수 있는** 의 XML 스키마 컬렉션을 사용한 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스를 그 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에 연결하면 다음 업그레이드 단계가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-172">However if you used an XML Schema collection in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] that allowed values of type **xs:date**, **xs:time**, or **xs:dateTime** (or any subtype) then the following upgrade steps occur when you attach your [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database to a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="d8e75-173">모든 XML 열의 경우, 이 열이 **xs:anyType**, **xs:anySimpleType**, **xs:date** 또는 해당 하위 유형, **xs:time** 또는 해당 하위 유형, **xs:dateTime** 또는 해당 하위 유형으로 형식화되거나 이러한 유형이 포함된 공용 구조체나 목록 유형으로 형식화된 요소나 특성이 들어 있는 XML 스키마 컬렉션으로 형식화되면 다음과 같은 상황이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-173">For every XML column, that is typed with an XML Schema Collection that contains elements or attributes that are typed as either **xs:anyType**, **xs:anySimpleType**, **xs:date** or any of its subtypes, **xs:time** or any subtype thereof, or **xs:dateTime** or any of its subtypes, or are union or list types containing any of these types the following occurs:</span></span>  
  
    1.  <span data-ttu-id="d8e75-174">열의 모든 XML 인덱스가 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-174">All XML indices on the column will be disabled.</span></span>  
  
    2.  <span data-ttu-id="d8e75-175">모든 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 값이 Z 표준 시간대로 표준화되었으므로 이 값이 Z 표준 시간대로 계속 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-175">All [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] values will continue to be represented in the Z timezone, because they have been normalized to the Z timezone.</span></span>  
  
    3.  <span data-ttu-id="d8e75-176">일 년 중 1월 1일보다 작은 **xs:date** 또는 **xs:dateTime** 값은 인덱스가 다시 작성되거나 XQuery 또는 XML-DML 문이 해당 값을 포함하는 XML 데이터 형식에 대해 실행되면 런타임 오류를 일으킵니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-176">Any **xs:date** or **xs:dateTime** values that are smaller than January 1st of year 1 will lead to a runtime error when the index gets rebuild or an XQuery or XML-DML statements gets executed against the XML data type containing that value.</span></span>  
  
2.  <span data-ttu-id="d8e75-177">**xs:date** 또는 **xs:dateTime** 패싯의 음수 연도나 XML 스키마 컬렉션의 기본값은 기본 **xs:date** 또는 **xs:dateTime** 형식(예: **xs:dateTime**의 경우 0001-01-01T00:00:00.0000000Z)에 의해 허용되는 최소값으로 자동 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-177">Any negative years in **xs:date** or **xs:dateTime** facets or default values in an XML Schema collection will automatically be updated to the smallest value allowed by the base **xs:date** or **xs:dateTime** type (e.g., 0001-01-01T00:00:00.0000000Z for **xs:dateTime**).</span></span>  
  
 <span data-ttu-id="d8e75-178">간단한 SQL SELECT 문을 계속 사용하면 음수 연도가 포함될 경우에도 전체 XML 데이터 형식을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-178">Note that you can still use a simple SQL select statement to retrieve the whole XML data type, even if it contains negative years.</span></span> <span data-ttu-id="d8e75-179">음수 연도를 새로 지원되는 범위에 있는 연도로 대체하거나 해당 요소나 특성의 유형을 **xs:string**으로 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d8e75-179">It is recommended that you replace negative years with a year within the newly supported range or change the type of the element or attribute to **xs:string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e75-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8e75-180">See Also</span></span>  
 <span data-ttu-id="d8e75-181">[XML 데이터 인스턴스 만들기](create-instances-of-xml-data.md) </span><span class="sxs-lookup"><span data-stu-id="d8e75-181">[Create Instances of XML Data](create-instances-of-xml-data.md) </span></span>  
 <span data-ttu-id="d8e75-182">[xml 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="d8e75-182">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="d8e75-183">[XML DML&#40;XML 데이터 수정 언어&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="d8e75-183">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="d8e75-184">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d8e75-184">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
