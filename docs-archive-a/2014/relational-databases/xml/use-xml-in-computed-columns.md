---
title: 계산 열에 XML 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: rothja
ms.author: jroth
ms.openlocfilehash: 33a7549823dc3e4a23cecfa97d7345a6421cb1b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728087"
---
# <a name="use-xml-in-computed-columns"></a><span data-ttu-id="45cfa-102">계산 열에 XML 사용</span><span class="sxs-lookup"><span data-stu-id="45cfa-102">Use XML in Computed Columns</span></span>
  <span data-ttu-id="45cfa-103">XML 인스턴스는 계산 열의 원본이나 계산 열의 유형으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-103">XML instances can appear as a source for a computed column, or as a type of computed column.</span></span> <span data-ttu-id="45cfa-104">이 항목의 예에서는 계산 열이 있는 XML을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-104">The examples in this topic show how to use XML with computed columns.</span></span>  
  
## <a name="creating-computed-columns-from-xml-columns"></a><span data-ttu-id="45cfa-105">XML 열에서 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="45cfa-105">Creating Computed Columns from XML Columns</span></span>  
 <span data-ttu-id="45cfa-106">다음 `CREATE TABLE` 문에서 `xml` 유형 열(`col2`)은 `col1`에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-106">In the following `CREATE TABLE` statement, an `xml` type column (`col2`) is computed from `col1`:</span></span>  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 <span data-ttu-id="45cfa-107">다음 `xml` 문에서와 같이 계산 열을 만들 때도 `CREATE TABLE` 데이터 형식이 원본으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-107">The `xml` data type can also appear as a source in creating a computed column, as shown in the following `CREATE TABLE` statement:</span></span>  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 <span data-ttu-id="45cfa-108">다음 예에서와 같이 `xml` 유형 열에서 값을 추출하여 계산 열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-108">You can create a computed column by extracting a value from an `xml` type column as shown in the following example.</span></span> <span data-ttu-id="45cfa-109">계산 열을 만들 때는 `xml` 데이터 형식 메서드를 직접 사용할 수 없으므로 이 예에서는 XML 인스턴스에서 값을 반환하는 함수(`my_udf`)를 먼저 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-109">Because the `xml` data type methods cannot be used directly in creating computed columns, the example first defines a function (`my_udf`) that returns a value from an XML instance.</span></span> <span data-ttu-id="45cfa-110">이 함수는 `value()` 유형의 `xml` 메서드를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-110">The function wraps the `value()` method of the `xml` type.</span></span> <span data-ttu-id="45cfa-111">그러면 함수 이름이 계산 열의 `CREATE TABLE` 문에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-111">The function name is then specified in the `CREATE TABLE` statement for the computed column.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 <span data-ttu-id="45cfa-112">이전 예에서와 같이 다음 예에서는 계산 열에 대해 `xml` 유형 인스턴스를 반환하도록 함수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-112">As in the previous example, the following example defines a function to return an `xml` type instance for a computed column.</span></span> <span data-ttu-id="45cfa-113">함수 내에서 `query()` 데이터 형식의 `xml` 메서드는 `xml` 유형 매개 변수에서 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-113">Inside the function, the `query()` method of the `xml` data type retrieves a value from an `xml` type parameter.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 <span data-ttu-id="45cfa-114">다음 `CREATE TABLE` 문에서 `Col2` 는 함수에서 반환된 XML 데이터(`<Features>` 요소)를 사용하는 계산 열입니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-114">In the following `CREATE TABLE` statement, `Col2` is a computed column that uses the XML data (`<Features>` element) that is returned by the function:</span></span>  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a><span data-ttu-id="45cfa-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="45cfa-115">In This Section</span></span>  
  
|<span data-ttu-id="45cfa-116">항목</span><span class="sxs-lookup"><span data-stu-id="45cfa-116">Topic</span></span>|<span data-ttu-id="45cfa-117">Description</span><span class="sxs-lookup"><span data-stu-id="45cfa-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="45cfa-118">계산 열을 사용하여 자주 사용되는 XML 값 승격</span><span class="sxs-lookup"><span data-stu-id="45cfa-118">Promote Frequently Used XML Values with Computed Columns</span></span>](promote-frequently-used-xml-values-with-computed-columns.md)|<span data-ttu-id="45cfa-119">속성 테이블 및 계산 열이 있는 속성 승격을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="45cfa-119">Describes how to use property promotion with computed columns and property tables.</span></span>|  
  
  
