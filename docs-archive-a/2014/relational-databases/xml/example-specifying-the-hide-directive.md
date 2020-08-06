---
title: '예제: HIDE 지시어 지정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
author: rothja
ms.author: jroth
ms.openlocfilehash: 423ee36f679467c07a604b9754172f6e261971b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659861"
---
# <a name="example-specifying-the-hide-directive"></a><span data-ttu-id="53720-102">예제: HIDE 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="53720-102">Example: Specifying the HIDE Directive</span></span>
  <span data-ttu-id="53720-103">이 예에서는 **HIDE** 지시어 사용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="53720-103">This example illustrates the use of the **HIDE** directive.</span></span> <span data-ttu-id="53720-104">이 지시어는 쿼리에 의해 반환된 범용 테이블의 행을 정렬하기 위한 특성은 쿼리가 반환하게 하고 최종 결과 XML 문서에는 그 특성이 포함되지 않게 하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-104">This directive is useful when you want the query to return an attribute for ordering the rows in the universal table that is returned by the query, but you do not want that attribute in the final resulting XML document.</span></span>  
  
 <span data-ttu-id="53720-105">다음 쿼리는 이러한 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-105">This query constructs this XML:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="53720-106">이 쿼리는 원하는 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-106">This query generates the XML you want.</span></span> <span data-ttu-id="53720-107">이 쿼리는 열 이름의 Tag 값으로 1과 2가 포함된 두 열 그룹을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-107">The query identifies two column groups having 1 and 2 as Tag values in the column names.</span></span>  
  
 <span data-ttu-id="53720-108">이 쿼리는 [xml](/sql/t-sql/xml/query-method-xml-data-type) 데이터 형식의 **query() 메서드(xml 데이터 형식)** 를 사용하여 요약 설명을 검색하기 위해 **xml** 유형의 CatalogDescription 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-108">This query uses the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) of the **xml** data type to query the CatalogDescription column of **xml** type in order to retrieve the summary description.</span></span> <span data-ttu-id="53720-109">이 쿼리는 또한 [xml](/sql/t-sql/xml/value-method-xml-data-type) 데이터 형식의 **value() 메서드(xml 데이터 형식)** 를 사용하여 CatalogDescription 열로부터 ProductModelID 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-109">The query also uses the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) of the **xml** data type to retrieve the ProductModelID value from the CatalogDescription column.</span></span> <span data-ttu-id="53720-110">이 값은 결과 XML에 필요하지 않지만 결과 행 집합을 정렬하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="53720-110">This value is not required in the resulting XML, but is required to sort the resulting rowset.</span></span> <span data-ttu-id="53720-111">따라서 열 이름 `[Summary!2!ProductModelID!HIDE]`에는 **HIDE** 지시어가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="53720-111">Therefore, the column name, `[Summary!2!ProductModelID!HIDE]`, includes the **HIDE** directive.</span></span> <span data-ttu-id="53720-112">이 열이 SELECT 문에 포함되지 않은 경우 `[ProductModel!1!ProdModelID]` xml `[Summary!2!SummaryDescription]` 유형인 **및** 으로 행 집합을 정렬해야 하며 ORDER BY에서는 **xml** 유형의 열을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53720-112">If this column is not included in the SELECT statement, you will have to sort the rowset by `[ProductModel!1!ProdModelID]` and `[Summary!2!SummaryDescription]` that is **xml** type and you cannot use the **xml** type column in ORDER BY.</span></span> <span data-ttu-id="53720-113">따라서 추가 `[Summary!2!ProductModelID!HIDE]` 열이 추가된 다음 ORDER BY 절에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="53720-113">Therefore, the additional `[Summary!2!ProductModelID!HIDE]` column is added and is then specified in the ORDER BY clause.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 <span data-ttu-id="53720-114">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="53720-114">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53720-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53720-115">See Also</span></span>  
 [<span data-ttu-id="53720-116">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="53720-116">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
