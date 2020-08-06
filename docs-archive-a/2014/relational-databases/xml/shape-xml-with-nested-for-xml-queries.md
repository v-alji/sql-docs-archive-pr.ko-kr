---
title: 중첩 FOR XML 쿼리로 XML 구체화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: rothja
ms.author: jroth
ms.openlocfilehash: 738b5b3ec67dada90c851d284ccc8b3009a51aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652673"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a><span data-ttu-id="76114-102">중첩 FOR XML 쿼리로 XML 구체화</span><span class="sxs-lookup"><span data-stu-id="76114-102">Shape XML with Nested FOR XML Queries</span></span>
  <span data-ttu-id="76114-103">다음 예에서는 `Production.Product` 테이블을 쿼리하여 특정 제품의 `ListPrice` 및 `StandardCost` 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="76114-103">The following example queries the `Production.Product` table to retrieve the `ListPrice` and `StandardCost` values of a specific product.</span></span> <span data-ttu-id="76114-104">쿼리를 효과적으로 만들기 위해 두 가격이 모두 <`Price`> 요소에 반환되고 각 <`Price`> 요소에는 `PriceType` 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="76114-104">To make the query interesting, both prices are returned in a <`Price`> element, and each <`Price`> element has a `PriceType` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76114-105">예제</span><span class="sxs-lookup"><span data-stu-id="76114-105">Example</span></span>  
 <span data-ttu-id="76114-106">다음은 XML의 예상 셰이프입니다.</span><span class="sxs-lookup"><span data-stu-id="76114-106">This is the expected shape of the XML:</span></span>  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 <span data-ttu-id="76114-107">다음은 중첩된 FOR XML 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="76114-107">This is the nested FOR XML query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 <span data-ttu-id="76114-108">이전 쿼리에서 다음을 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="76114-108">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="76114-109">외부 SELECT 문은 **ProductID** 특성과 두 개의 <`Price`> 자식 요소가 있는 <`Product`> 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="76114-109">The outer SELECT statement constructs the <`Product`> element that has a **ProductID** attribute and two <`Price`> child elements.</span></span>  
  
-   <span data-ttu-id="76114-110">두 개의 내부 SELECT 문은 각각 **PriceType** 특성과 제품 가격을 반환하는 XML이 포함된 두 개의 <`Price`> 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="76114-110">The two inner SELECT statements construct two <`Price`> elements, each with a **PriceType** attribute and XML that returns the product price.</span></span>  
  
-   <span data-ttu-id="76114-111">외부 SELECT 문에 있는 XMLSCHEMA 지시어는 결과 XML의 셰이프를 기술하는 인라인 XSD 스키마를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="76114-111">The XMLSCHEMA directive in the outer SELECT statement generates the inline XSD schema that describes the shape of the resulting XML.</span></span>  
  
 <span data-ttu-id="76114-112">쿼리를 효과적으로 만들기 위해 FOR XML 쿼리를 작성한 다음 결과에 대해 XQuery를 작성하여 다음 쿼리에서와 같이 XML 셰이프를 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76114-112">To make the query interesting, you can write the FOR XML query and then write an XQuery against the result to reshape the XML, as shown in the following query:</span></span>  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="76114-113">이전 예에서는 `query()` 데이터 형식의 `xml` 메서드를 사용하여 내부 FOR XML 쿼리에 의해 반환된 XML을 쿼리하고 예상된 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="76114-113">The previous example uses the `query()` method of the `xml` data type to query the XML returned by the inner FOR XML query and construct the expected result.</span></span>  
  
 <span data-ttu-id="76114-114">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="76114-114">This is the result:</span></span>  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76114-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76114-115">See Also</span></span>  
 [<span data-ttu-id="76114-116">중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="76114-116">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
