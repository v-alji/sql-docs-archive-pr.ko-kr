---
title: FOR XML 쿼리의 TYPE 지시어 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
author: rothja
ms.author: jroth
ms.openlocfilehash: cddce90718ef5edfcf161ddc6cc52b617825a2e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660917"
---
# <a name="type-directive-in-for-xml-queries"></a><span data-ttu-id="205fb-102">FOR XML 쿼리의 TYPE 지시어</span><span class="sxs-lookup"><span data-stu-id="205fb-102">TYPE Directive in FOR XML Queries</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="205fb-103">[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql) 를 지원 하므로 필요에 따라 type 지시어를 지정 하 여 for xml 쿼리 결과가 데이터 형식으로 반환 되도록 요청할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="205fb-103">support for the [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql) enables you to optionally request that the result of a FOR XML query be returned as `xml` data type by specifying the TYPE directive.</span></span> <span data-ttu-id="205fb-104">그러면 서버에서 FOR XML 쿼리 결과를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-104">This allows you to process the result of a FOR XML query on the server.</span></span> <span data-ttu-id="205fb-105">예를 들어이에 대해 XQuery를 지정 하거나, 결과를 `xml` 유형 변수에 할당 하거나, [중첩 FOR XML 쿼리](use-nested-for-xml-queries.md)를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-105">For example, you can specify an XQuery against it, assign the result to an `xml` type variable, or write [Nested FOR XML queries](use-nested-for-xml-queries.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="205fb-106">에서는 TYPE 지시어를 사용하거나 `xml` 데이터 형식을 사용하여 SQL 테이블 열과 출력 매개 변수에서 XML 인스턴스 데이터 값을 반환하는 FOR XML 쿼리와 같은 여러 서버 구문의 결과로 XML 데이터 형식 인스턴스 데이터를 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-106">returns XML data type instance data to the client as a result of different server-constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML instance data values from SQL table columns and output parameters.</span></span> <span data-ttu-id="205fb-107">클라이언트 애플리케이션 코드에서 ADO.NET 공급자가 이 XML 데이터 형식 정보를 서버에서 이진 인코딩으로 보내도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-107">In client application code, the ADO.NET provider requests this XML data type information to be sent in a binary encoding from the server.</span></span> <span data-ttu-id="205fb-108">그러나 TYPE 지시어 없이 FOR XML을 사용하면 XML 데이터가 문자열 유형으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-108">However, if you are using FOR XML without the TYPE directive, the XML data comes back as a string type.</span></span> <span data-ttu-id="205fb-109">클라이언트 공급자는 항상 두 XML 유형 중 하나를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-109">In any case, the client provider will always be able to handle either form of XML.</span></span> <span data-ttu-id="205fb-110">TYPE 지시어가 없는 최상위 FOR XML은 커서와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-110">Note that top-level FOR XML without the TYPE directive cannot be used with cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="205fb-111">예제</span><span class="sxs-lookup"><span data-stu-id="205fb-111">Examples</span></span>  
 <span data-ttu-id="205fb-112">다음 예에서는 TYPE 지시어를 FOR XML 쿼리와 함께 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-112">The following examples illustrate the use of the TYPE directive with FOR XML queries.</span></span>  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a><span data-ttu-id="205fb-113">FOR XML 쿼리 결과를 xml 유형으로 검색</span><span class="sxs-lookup"><span data-stu-id="205fb-113">Retrieving FOR XML query results as xml type</span></span>  
 <span data-ttu-id="205fb-114">다음 쿼리에서는 `Contacts` 테이블에서 고객 연락처 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-114">The following query retrieves customer contact information from the `Contacts` table.</span></span> <span data-ttu-id="205fb-115">`TYPE`에 `FOR XML` 지시어가 지정되어 있으므로 결과는 `xml` 유형으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-115">Because the `TYPE` directive is specified in `FOR XML`, the result is returned as `xml` type.</span></span>  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="205fb-116">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-116">This is the partial result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a><span data-ttu-id="205fb-117">xml 유형 변수에 FOR XML 쿼리 결과 할당</span><span class="sxs-lookup"><span data-stu-id="205fb-117">Assigning FOR XML query results to an xml type variable</span></span>  
 <span data-ttu-id="205fb-118">다음 예에서는 FOR XML 결과가 `xml` 유형 변수 `@x`에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-118">In the following example, a FOR XML result is assigned to an `xml` type variable, `@x`.</span></span> <span data-ttu-id="205fb-119">쿼리는 `BusinessEntityID` `FirstName` `LastName` 의 열에서,, 및 추가 전화 번호와 같은 연락처 정보를 검색 합니다 `AdditionalContactInfo` `xml``TYPE` .</span><span class="sxs-lookup"><span data-stu-id="205fb-119">The query retrieves contact information, such as the `BusinessEntityID`, `FirstName`, `LastName`, and additional telephone numbers, from the `AdditionalContactInfo` column of `xml``TYPE`.</span></span> <span data-ttu-id="205fb-120">`FOR XML` 절은 `TYPE` 지시어를 지정하므로 XML은 `xml` 유형으로 반환되며 변수에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-120">Because the `FOR XML` clause specifies `TYPE` directive, the XML is returned as `xml` type and is assigned to a variable.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a><span data-ttu-id="205fb-121">FOR XML 쿼리 결과 쿼리</span><span class="sxs-lookup"><span data-stu-id="205fb-121">Querying results of a FOR XML query</span></span>  
 <span data-ttu-id="205fb-122">FOR XML 쿼리가 XML을 반환하므로</span><span class="sxs-lookup"><span data-stu-id="205fb-122">The FOR XML queries return XML.</span></span> <span data-ttu-id="205fb-123">FOR XML 쿼리에서 반환한 XML 결과에 `xml`, `query()` 등의 `value()` 유형 메서드를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-123">Therefore, you can apply `xml` type methods, such as `query()` and `value()`, to the XML result returned by FOR XML queries.</span></span>  
  
 <span data-ttu-id="205fb-124">다음 쿼리에서는 `xml` 데이터 형식의 `query()` 메서드를 사용하여 `FOR XML` 쿼리 결과를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-124">In the following query, the `query()` method of the `xml` data type is used to query the result of the `FOR XML` query.</span></span> <span data-ttu-id="205fb-125">자세한 내용은 [query&#40;&#41; 메서드&#40;xml 데이터 형식&#41;](/sql/t-sql/xml/query-method-xml-data-type)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="205fb-125">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 <span data-ttu-id="205fb-126">내부 `SELECT ... FOR XML` 쿼리는 외부 `SELECT`가 `query()` 메서드를 `xml` 유형에 적용하는 `xml` 유형 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-126">The inner `SELECT ... FOR XML` query returns an `xml` type result to which the outer `SELECT` applies the `query()` method to the `xml` type.</span></span> <span data-ttu-id="205fb-127">지정된 `TYPE` 지시어에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="205fb-127">Note the `TYPE` directive specified.</span></span>  
  
 <span data-ttu-id="205fb-128">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-128">This is the result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 <span data-ttu-id="205fb-129">다음 쿼리에서는 `xml` 데이터 형식의 `value()` 메서드를 사용하여 `SELECT...FOR XML` 쿼리가 반환한 XML 결과에서 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-129">In the following query, the `value()` method of the `xml` data type is used to retrieve a value from the XML result returned by the `SELECT...FOR XML` query.</span></span> <span data-ttu-id="205fb-130">자세한 내용은 [value&#40;&#41; 메서드&#40;xml 데이터 형식&#41;](/sql/t-sql/xml/value-method-xml-data-type)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="205fb-130">For more information, see [value&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 <span data-ttu-id="205fb-131">`value()` 메서드의 XQuery 경로 식이 `BusinessEntityID` 가 `1`인 고객 연락처의 첫 번째 전화 번호를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-131">The XQuery path expression in the `value()` method retrieves the first telephone number of a customer contact whose `BusinessEntityID` is `1`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="205fb-132">TYPE 지시어를 지정하지 않으면 FOR XML 쿼리 결과가 `nvarchar(max)` 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-132">If the TYPE directive is not specified, the FOR XML query result is returned as type `nvarchar(max)`.</span></span>  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a><span data-ttu-id="205fb-133">INSERT, UPDATE 및 DELETE(Transact-SQL DML)에 FOR XML 쿼리 결과 사용</span><span class="sxs-lookup"><span data-stu-id="205fb-133">Using FOR XML query results in INSERT, UPDATE, and DELETE (Transact-SQL DML)</span></span>  
 <span data-ttu-id="205fb-134">다음 예에서는 DML(데이터 조작 언어) 문에 FOR XML 쿼리를 사용할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-134">The following example demonstrates how FOR XML queries can be used in Data Manipulation Language (DML) statements.</span></span> <span data-ttu-id="205fb-135">예에서 `FOR XML`은 `xml` 유형의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-135">In the example, the `FOR XML` returns an instance of `xml` type.</span></span> <span data-ttu-id="205fb-136">`INSERT` 문은 이 XML을 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="205fb-136">The `INSERT` statement inserts this XML into a table.</span></span>  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="205fb-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="205fb-137">See Also</span></span>  
 [<span data-ttu-id="205fb-138">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="205fb-138">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
