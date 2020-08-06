---
title: XML 데이터 형식 변수 및 열 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
author: rothja
ms.author: jroth
ms.openlocfilehash: 08b79888eb47634deaccc910b2ea3c93800b7c78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738073"
---
# <a name="create-xml-data-type-variables-and-columns"></a><span data-ttu-id="6baaa-102">XML 데이터 형식 변수 및 열 만들기</span><span class="sxs-lookup"><span data-stu-id="6baaa-102">Create XML Data Type Variables and Columns</span></span>
  <span data-ttu-id="6baaa-103">`xml` 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 제공 데이터 형식이며 `int` 및 `varchar`와 같은 다른 기본 제공 유형과 비슷한 점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-103">The `xml` data type is a built-in data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is somewhat similar to other built-in types such as `int` and `varchar`.</span></span> <span data-ttu-id="6baaa-104">다른 기본 제공 유형과 마찬가지로 `xml` 변수 유형, 매개 변수 유형, 함수 반환 유형 또는 [CAST 및 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)로 테이블을 만들 때 데이터 형식을 열 유형으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-104">As with other built-in types, you can use the `xml` data type as a column type when you create a table as a variable type, a parameter type, a function-return type, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
## <a name="creating-columns-and-variables"></a><span data-ttu-id="6baaa-105">열 및 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="6baaa-105">Creating Columns and Variables</span></span>  
 <span data-ttu-id="6baaa-106">다음 예에서와 같이 테이블의 일부분으로 `xml` 유형 열을 만들려면 `CREATE TABLE` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-106">To create an `xml` type column as part of a table, use a `CREATE TABLE` statement, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 <span data-ttu-id="6baaa-107">다음 예에서와 같이 `DECLARE statement` 문을 사용하여 `xml` 유형의 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-107">You can use a `DECLARE statement` to create a variable of `xml` type, as the following example shows.</span></span>  
  
```  
DECLARE @x xml   
```  
  
 <span data-ttu-id="6baaa-108">다음 예에서와 같이 XML 스키마 컬렉션을 지정하여 형식화된 `xml` 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-108">Create a typed `xml` variable by specifying an XML schema collection, as shown in the following example.</span></span>  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 <span data-ttu-id="6baaa-109">다음 예에서와 같이 저장된 프로시저로 `xml` 유형 매개 변수를 전달하려면 `CREATE PROCEDURE` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-109">To pass an `xml` type parameter to a stored procedure, use a `CREATE PROCEDURE` statement, as shown in the following example.</span></span>  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 <span data-ttu-id="6baaa-110">XQuery를 사용하여 열, 매개 변수 또는 변수에 저장된 XML 인스턴스를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-110">You can use XQuery to query XML instances stored in columns, parameters, or variables.</span></span> <span data-ttu-id="6baaa-111">또한 XML DML(XML 데이터 조작 언어)을 사용하여 XML 인스턴스에 업데이트를 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-111">You can also use the XML Data Manipulation Language (XML DML) to apply updates to the XML instances.</span></span> <span data-ttu-id="6baaa-112">XQuery 표준에서는 개발 당시 XQuery DML을 정의하지 않았으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 [XML 데이터 수정 언어](/sql/t-sql/xml/xml-data-modification-language-xml-dml) 확장을 XQuery에 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-112">Because the XQuery standard did not define XQuery DML at the time of development, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduces [XML Data Modification Language](/sql/t-sql/xml/xml-data-modification-language-xml-dml) extensions to XQuery.</span></span> <span data-ttu-id="6baaa-113">이러한 확장을 사용하여 작업을 삽입, 업데이트 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-113">These extensions allow you to perform insert, update, and delete operations.</span></span>  
  
## <a name="assigning-defaults"></a><span data-ttu-id="6baaa-114">기본값 할당</span><span class="sxs-lookup"><span data-stu-id="6baaa-114">Assigning Defaults</span></span>  
 <span data-ttu-id="6baaa-115">테이블에서 `xml` 유형의 열에 기본 XML 인스턴스를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-115">In a table, you can assign a default XML instance to a column of `xml` type.</span></span> <span data-ttu-id="6baaa-116">기본 XML을 제공할 수 있는 방법으로는 XML 상수를 사용하거나 `xml` 유형으로 명시적 캐스트를 사용하는 두 가지 방법 중 하나가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-116">You can provide the default XML in one of two ways: by using an XML constant, or by using an explicit cast to the `xml` type.</span></span>  
  
 <span data-ttu-id="6baaa-117">XML 상수로 기본 XML을 제공하려면 다음 예에서와 같이 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-117">To provide the default XML as an XML constant, use syntax as shown in the following example.</span></span> <span data-ttu-id="6baaa-118">문자열은 `xml` 유형으로 암시적으로 CAST가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-118">Note that the string is implicitly CAST to `xml` type.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 <span data-ttu-id="6baaa-119">명시적 `CAST` 로써 기본 XML을 `xml`에 제공하려면 다음 예에서와 같이 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-119">To provide the default XML as an explicit `CAST` to `xml`, use syntax as shown in the following example.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6baaa-120">에서는 `xml` 유형의 열에서 NULL과 NOT NULL 제약 조건도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-120">also supports NULL and NOT NULL constraints on columns of `xml` type.</span></span> <span data-ttu-id="6baaa-121">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-121">For example:</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a><span data-ttu-id="6baaa-122">제약 조건 지정</span><span class="sxs-lookup"><span data-stu-id="6baaa-122">Specifying Constraints</span></span>  
 <span data-ttu-id="6baaa-123">`xml` 유형의 열을 만들 때 열 수준이나 테이블 수준 제약 조건을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-123">When you create columns of `xml` type, you can define column-level or table-level constraints.</span></span> <span data-ttu-id="6baaa-124">다음 경우에 제약 조건을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-124">Use constraints in the following situations:</span></span>  
  
-   <span data-ttu-id="6baaa-125">비즈니스 규칙을 XML 스키마에 표현할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-125">Your business rules cannot be expressed in XML schemas.</span></span> <span data-ttu-id="6baaa-126">예를 들어 꽃 판매점의 배달 주소는 해당 영업소 위치에서 81km 이내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-126">For example, the delivery address of a flower shop must be within 50 miles of its business location.</span></span> <span data-ttu-id="6baaa-127">이러한 사항은 XML 열에 대한 제약 조건으로 작성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-127">This can be written as a constraint on the XML column.</span></span> <span data-ttu-id="6baaa-128">제약 조건에는 `xml` 데이터 형식의 메서드가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-128">The constraint may involve `xml` data type methods.</span></span>  
  
-   <span data-ttu-id="6baaa-129">제약 조건에 테이블의 XML 또는 비-XML 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-129">Your constraint involves other XML or non-XML columns in the table.</span></span> <span data-ttu-id="6baaa-130">한 예는 관계형 CustomerID 열에 있는 값과 일치하는 XML 인스턴스에 있는 고객의 ID(`/Customer/@CustId`)에 대한 강제 적용입니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-130">An example is the enforcement of the ID of a Customer (`/Customer/@CustId`) found in an XML instance to match the value in a relational CustomerID column.</span></span>  
  
 <span data-ttu-id="6baaa-131">형식화되거나 형식화되지 않은 `xml` 데이터 형식 열에 대해 제약 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-131">You can specify constraints for typed or untyped `xml` data type columns.</span></span> <span data-ttu-id="6baaa-132">그러나 제약 조건을 지정할 때 [XML 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods) 를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-132">However, you cannot use the [XML data type methods](/sql/t-sql/xml/xml-data-type-methods) when you specify constraints.</span></span> <span data-ttu-id="6baaa-133">또한 `xml` 데이터 형식은 다음 열 및 테이블 제약 조건을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-133">Also, note that the `xml` data type does not support the following column and table constraints:</span></span>  
  
-   <span data-ttu-id="6baaa-134">PRIMARY KEY/ FOREIGN KEY</span><span class="sxs-lookup"><span data-stu-id="6baaa-134">PRIMARY KEY/ FOREIGN KEY</span></span>  
  
-   <span data-ttu-id="6baaa-135">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6baaa-135">UNIQUE</span></span>  
  
-   <span data-ttu-id="6baaa-136">COLLATE</span><span class="sxs-lookup"><span data-stu-id="6baaa-136">COLLATE</span></span>  
  
     <span data-ttu-id="6baaa-137">XML은 자체 인코딩을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-137">XML provides its own encoding.</span></span> <span data-ttu-id="6baaa-138">데이터 정렬은 문자열 유형에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-138">Collations apply to string types only.</span></span> <span data-ttu-id="6baaa-139">`xml` 데이터 형식은 문자열 유형이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-139">The `xml` data type is not a string type.</span></span> <span data-ttu-id="6baaa-140">하지만 문자열 표현이 있으며 문자열 데이터 형식으로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-140">However, it does have string representation and allows casting to and from string data types.</span></span>  
  
-   <span data-ttu-id="6baaa-141">RULE</span><span class="sxs-lookup"><span data-stu-id="6baaa-141">RULE</span></span>  
  
 <span data-ttu-id="6baaa-142">대신 다음 예처럼 사용자 정의 함수인 래퍼를 만들어 `xml` 데이터 형식 메서드를 래핑하고 CHECK 제약 조건에 사용자 정의 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-142">An alternative to using constraints is to create a wrapper, user-defined function to wrap the `xml` data type method and specify user-defined function in the check constraint as shown in the following example.</span></span>  
  
 <span data-ttu-id="6baaa-143">다음 예에서 `Col2` 의 제약 조건은 이 열에 저장된 각 XML 인스턴스가 `<ProductDescription>` 특성을 포함하는 `ProductID` 요소를 갖도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-143">In the following example, the constraint on `Col2` specifies that each XML instance stored in this column must have a `<ProductDescription>` element that contains a `ProductID` attribute.</span></span> <span data-ttu-id="6baaa-144">이 제약 조건은 사용자 정의 함수에 의해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-144">This constraint is enforced by this user-defined function:</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 <span data-ttu-id="6baaa-145">인스턴스의 `exist()` 요소에 `xml` 특성이 있으면 `1` 데이터 형식의 `<ProductDescription>` 메서드가 `ProductID` 을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-145">Note that the `exist()` method of the `xml` data type returns `1` if the `<ProductDescription>` element in the instance contains the `ProductID` attribute.</span></span> <span data-ttu-id="6baaa-146">그렇지 않으면 `0`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-146">Otherwise, it returns `0`.</span></span>  
  
 <span data-ttu-id="6baaa-147">이제 다음과 같이 열 수준 제약 조건을 가진 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-147">Now, you can create a table with a column-level constraint as follows:</span></span>  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 <span data-ttu-id="6baaa-148">다음이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-148">The following insert succeeds:</span></span>  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 <span data-ttu-id="6baaa-149">제약 조건 때문에 다음은 삽입되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-149">Because of the constraint, the following insert fails:</span></span>  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a><span data-ttu-id="6baaa-150">같은 테이블 또는 다른 테이블</span><span class="sxs-lookup"><span data-stu-id="6baaa-150">Same or Different Table</span></span>  
 <span data-ttu-id="6baaa-151">`xml`다른 관계형 열이 포함 된 테이블 또는 주 테이블에 대 한 외래 키 관계가 있는 별도의 테이블에 데이터 형식 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-151">An `xml` data type column can be created in a table that contains other relational columns, or in a separate table with a foreign key relationship to a main table.</span></span>  
  
 <span data-ttu-id="6baaa-152">`xml`다음 조건 중 하나에 해당 하는 경우 동일한 테이블에 데이터 형식 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-152">Create an `xml` data type column in the same table when one of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="6baaa-153">애플리케이션이 XML 열에서 데이터 검색을 수행하고 XML 열에 XML 인덱스가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-153">Your application performs data retrieval on the XML column and does not require an XML index on the XML column.</span></span>  
  
-   <span data-ttu-id="6baaa-154">`xml` 데이터 형식의 열에 XML 인덱스를 작성하려고 하며 기본 테이블의 기본 키는 해당 클러스터링 키와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-154">You want to build an XML index on the `xml` data type column and the primary key of the main table is the same as its clustering key.</span></span> <span data-ttu-id="6baaa-155">자세한 내용은 [XML 인덱스&#40;SQL Server&#41;](xml-indexes-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6baaa-155">For more information, see [XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md).</span></span>  
  
 <span data-ttu-id="6baaa-156">다음 조건에 맞는 경우 별개의 테이블에 `xml` 데이터 형식의 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-156">Create the `xml` data type column in a separate table if the following conditions are true:</span></span>  
  
-   <span data-ttu-id="6baaa-157">`xml` 데이터 형식의 열에 XML 인덱스를 작성하려고 하지만 기본 테이블의 기본 키가 해당 클러스터링 키와 다르거나, 기본 테이블에 기본 키가 없거나, 기본 테이블이 힙(비 클러스터링 키)입니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-157">You want to build an XML index on the `xml` data type column, but the primary key of the main table is different from its clustering key, or the main table does not have a primary key, or the main table is a heap (no clustering key).</span></span> <span data-ttu-id="6baaa-158">기본 테이블이 이미 있는 경우에는 이 조건에 부합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-158">This may be true if the main table already exists.</span></span>  
  
-   <span data-ttu-id="6baaa-159">테이블에 있는 XML 열로 인해 테이블 검색 속도가 느려지는 것을 원치 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-159">You do not want table scans to slow down because of the presence of the XML column in the table.</span></span> <span data-ttu-id="6baaa-160">XML 열은 행 안에 있든 행 밖에 있든 간에 공간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6baaa-160">This uses space whether it is stored in-row or out-of-row.</span></span>  
  
  
