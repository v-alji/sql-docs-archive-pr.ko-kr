---
title: 중첩 FOR XML 쿼리 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 60c4198697f8d19c9b2e5bc1b415e0787861d40a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738056"
---
# <a name="use-nested-for-xml-queries"></a><span data-ttu-id="22e21-102">중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="22e21-102">Use Nested FOR XML Queries</span></span>
  <span data-ttu-id="22e21-103">For `xml` xml 쿼리의 데이터 형식 및 [형식 지시어](type-directive-in-for-xml-queries.md) 를 사용 하면 for xml 쿼리에 의해 반환 된 xml을 서버 및 클라이언트에서 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-103">The `xml` data type and the [TYPE directive in FOR XML queries](type-directive-in-for-xml-queries.md) enable the XML returned by the FOR XML queries to be processed on the server as well as on the client.</span></span>  
  
## <a name="processing-with-xml-type-variables"></a><span data-ttu-id="22e21-104">xml 유형 변수를 사용하여 처리</span><span class="sxs-lookup"><span data-stu-id="22e21-104">Processing with xml Type Variables</span></span>  
 <span data-ttu-id="22e21-105">FOR XML 쿼리 결과를 `xml` 유형의 변수에 할당하거나 XQuery를 사용하여 결과를 쿼리하고 추가 처리를 위해 이 결과를 `xml` 유형의 변수에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-105">You can assign the FOR XML query result to an `xml` type variable, or use XQuery to query the result, and assign that result to an `xml` type variable for more processing.</span></span>  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 <span data-ttu-id="22e21-106">또한 `xml` 데이터 형식 메서드 중 하나를 사용하여 `@x` 변수에 반환된 XML을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-106">You can additionally process the XML returned in the variable, `@x`, by using one of the `xml` data type methods.</span></span> <span data-ttu-id="22e21-107">예를 들어 `ProductModelID` value() 메서드 [를 사용하여](/sql/t-sql/xml/value-method-xml-data-type)특성 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-107">For example, you can retrieve the `ProductModelID` attribute value by using the [value() method](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 <span data-ttu-id="22e21-108">다음 예에서 `FOR XML` 지시어가 `TYPE` 절에 지정되어 있기 때문에 `FOR XML` 쿼리 결과는 `xml` 유형으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-108">In the following example, the `FOR XML` query result is returned as an `xml` type, because the `TYPE` directive is specified in the `FOR XML` clause.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 <span data-ttu-id="22e21-109">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-109">This is the result:</span></span>  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 <span data-ttu-id="22e21-110">결과가 `xml` 유형이기 때문에 다음 쿼리와 같이 이 XML에 대해 `xml` 데이터 형식 메서드 중 하나를 직접 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-110">Because the result is of `xml` type, you can specify one of the `xml` data type methods directly against this XML, as shown in the following query.</span></span> <span data-ttu-id="22e21-111">쿼리에서는 [query() 메서드(xml 데이터 형식)](/sql/t-sql/xml/query-method-xml-data-type)를 사용하여 <`row`> 요소의 첫 번째 <`myRoot`> 요소 자식을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-111">In the query, the [query() method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) is used to retrieve the first <`row`> element child of the <`myRoot`> element.</span></span>  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 <span data-ttu-id="22e21-112">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-112">This is the result:</span></span>  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a><span data-ttu-id="22e21-113">내부 FOR XML 쿼리 결과를 외부 쿼리에 xml 유형 인스턴스로 반환</span><span class="sxs-lookup"><span data-stu-id="22e21-113">Returning Inner FOR XML Query Results to Outer Queries as xml Type Instances</span></span>  
 <span data-ttu-id="22e21-114">내부 쿼리 결과가 `xml` 유형으로 외부 쿼리로 반환되는 중첩 `FOR XML` 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-114">You can write nested `FOR XML` queries where the result of the inner query is returned as an `xml` type to the outer query.</span></span> <span data-ttu-id="22e21-115">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-115">For example:</span></span>  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="22e21-116">이전 쿼리에서 다음을 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="22e21-116">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="22e21-117">내부 `FOR XML` 쿼리에서 생성된 XML이 외부 `FOR XML`에서 생성된 XML에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-117">The XML generated by the inner `FOR XML` query is added to the XML generated by the outer `FOR XML`.</span></span>  
  
-   <span data-ttu-id="22e21-118">내부 쿼리는 `TYPE` 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-118">The inner query specifies the `TYPE` directive.</span></span> <span data-ttu-id="22e21-119">따라서 내부 쿼리에서 반환된 XML 데이터는 `xml` 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-119">Therefore, the XML data returned by the inner query is of `xml` type.</span></span> <span data-ttu-id="22e21-120">TYPE 지시어를 지정하지 않으면 내부 `FOR XML` 쿼리의 결과가 `nvarchar(max)`로 반환되고 XML 데이터가 올바르게 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-120">If the TYPE directive is not specified, the result of the inner `FOR XML` query is returned as `nvarchar(max)` and the XML data is entitized.</span></span>  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a><span data-ttu-id="22e21-121">결과 XML 데이터의 형식 제어</span><span class="sxs-lookup"><span data-stu-id="22e21-121">Controlling the Shape of Resulting XML Data</span></span>  
 <span data-ttu-id="22e21-122">중첩 FOR XML 쿼리를 사용하면 결과 XML 데이터 형식을 보다 자유롭게 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-122">Nested FOR XML queries give you more control in defining the shape of the resulting XML data.</span></span> <span data-ttu-id="22e21-123">중첩 FOR XML 쿼리를 사용하여 일부는 특성 중심이고 일부는 요소 중심인 XML을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-123">You can use nested FOR XML queries to construct XML that is partly attribute-centric and partly element-centric.</span></span>  
  
 <span data-ttu-id="22e21-124">중첩 FOR XML 쿼리로 특성 중심 및 요소 중심 XML을 모두 지정하는 방법은 [FOR XML 쿼리와 중첩 FOR XML 쿼리 비교](../xml/for-xml-query-compared-to-nested-for-xml-query.md) 및 [중첩 FOR XML 쿼리로 XML 구체화](../xml/shape-xml-with-nested-for-xml-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22e21-124">For more information about specifying both attribute-centric and element-centric XML with nested FOR XML queries, see [FOR XML Query Compared to Nested FOR XML Query](../xml/for-xml-query-compared-to-nested-for-xml-query.md) and [Shape XML with Nested FOR XML Queries](../xml/shape-xml-with-nested-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="22e21-125">중첩된 AUTO 모드 FOR XML 쿼리를 지정하여 형제를 포함하는 XML 계층을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-125">You can generate XML hierarchies that include siblings by specifying nested AUTO mode FOR XML queries.</span></span> <span data-ttu-id="22e21-126">자세한 내용은 [중첩 AUTO 모드 쿼리를 사용하여 형제 생성](../xml/generate-siblings-with-a-nested-auto-mode-query.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22e21-126">For more information, see [Generate Siblings with a Nested AUTO Mode Query](../xml/generate-siblings-with-a-nested-auto-mode-query.md).</span></span>  
  
 <span data-ttu-id="22e21-127">사용하는 모드에 관계없이 중첩된 FOR XML 쿼리를 사용하면 결과 XML 형식을 보다 자유롭게 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-127">Regardless of which mode you use, nested FOR XML queries provide more control in describing the shape of the resulting XML.</span></span> <span data-ttu-id="22e21-128">EXPLICIT 모드 쿼리 대신 이러한 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-128">They can be used in the place of EXPLICIT mode queries.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="22e21-129">예제</span><span class="sxs-lookup"><span data-stu-id="22e21-129">Examples</span></span>  
 <span data-ttu-id="22e21-130">다음 항목에서는 중첩 FOR XML 쿼리의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-130">The following topics provide examples of nested FOR XML queries.</span></span>  
  
 [<span data-ttu-id="22e21-131">FOR XML 쿼리와 중첩 FOR XML 쿼리 비교</span><span class="sxs-lookup"><span data-stu-id="22e21-131">FOR XML Query Compared to Nested FOR XML Query</span></span>](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 <span data-ttu-id="22e21-132">단일 수준 FOR XML 쿼리를 중첩 FOR XML 쿼리와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-132">Compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="22e21-133">이 예에서는 특성 중심 및 요소 중심 XML 둘 모두를 쿼리 결과로 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-133">This example includes a demonstration of how to specify both attribute-centric and element-centric XML as the result of the query.</span></span>  
  
 [<span data-ttu-id="22e21-134">중첩 AUTO 모드 쿼리를 사용하여 형제 생성</span><span class="sxs-lookup"><span data-stu-id="22e21-134">Generate Siblings with a Nested AUTO Mode Query</span></span>](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 <span data-ttu-id="22e21-135">중첩 AUTO 모드 쿼리를 사용하여 형제를 생성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-135">Shows how to generate siblings by using a nested AUTO mode query</span></span>  
  
 [<span data-ttu-id="22e21-136">ASP.NET에서 중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="22e21-136">Use Nested FOR XML Queries in ASP.NET</span></span>](use-nested-for-xml-queries-in-asp-net.md)  
 <span data-ttu-id="22e21-137">ASPX 애플리케이션이 FOR XML을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 XML을 반환할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-137">Demonstrates how an ASPX application can use FOR XML to return XML from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="22e21-138">중첩 FOR XML 쿼리로 XML 구체화</span><span class="sxs-lookup"><span data-stu-id="22e21-138">Shape XML with Nested FOR XML Queries</span></span>](../xml/shape-xml-with-nested-for-xml-queries.md)  
 <span data-ttu-id="22e21-139">중첩 FOR XML 쿼리를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만들어진 XML 문서의 구조를 제어하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22e21-139">Shows how to use nested FOR XML queries to control the structure of an XML document created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
