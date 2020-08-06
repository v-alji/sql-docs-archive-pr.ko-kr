---
title: '예제: PATH 모드 사용 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, examples
ms.assetid: 3564e13b-9b97-49ef-8cf9-6a78677b09a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0876d93ffe246b6129a3838f8dbae47f3be7ffaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743103"
---
# <a name="examples-using-path-mode"></a><span data-ttu-id="c0380-102">예제: PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="c0380-102">Examples: Using PATH Mode</span></span>
  <span data-ttu-id="c0380-103">다음 예에서는 SELECT 쿼리에서 XML을 생성할 때 PATH 모드를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-103">The following examples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="c0380-104">이러한 쿼리는 대부분 ProductModel 테이블의 Instructions 열에 저장된 자전거 제조 지침 XML 문서에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-104">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="specifying-a-simple-path-mode-query"></a><span data-ttu-id="c0380-105">간단한 PATH 모드 쿼리 지정</span><span class="sxs-lookup"><span data-stu-id="c0380-105">Specifying a simple PATH mode query</span></span>  
 <span data-ttu-id="c0380-106">이 쿼리는 FOR XML PATH 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-106">This query specifies a FOR XML PATH mode.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   
       ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH;  
GO  
```  
  
 <span data-ttu-id="c0380-107">다음 결과는 결과 행 집합의 각 열 값이 요소에 래핑되는 요소 중심 XML입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-107">The following result is element-centric XML where each column value in the resulting rowset is wrapped in an element.</span></span> <span data-ttu-id="c0380-108">`SELECT` 절은 열 이름에 별칭을 지정하지 않으므로 생성된 자식 요소 이름은 `SELECT` 절에 있는 해당 열 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-108">Because the `SELECT` clause does not specify any aliases for the column names, the child element names generated are the same as the corresponding column names in the `SELECT` clause.</span></span> <span data-ttu-id="c0380-109">행 집합의 각 행마다 <`row`> 태그가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-109">For each row in the rowset a <`row`> tag is added.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</row>`  
  
 `<row>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</row>`  
  
 <span data-ttu-id="c0380-110">다음 결과는 `RAW` 옵션이 지정된 `ELEMENTS` 모드 쿼리와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-110">The following result is the same as the `RAW` mode query with the `ELEMENTS` option specified.</span></span> <span data-ttu-id="c0380-111">여기서는 결과 집합의 각 행에 대해 기본 <`row`> 요소가 있는 요소 중심 XML을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-111">It returns element-centric XML with a default <`row`> element for each row in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML RAW, ELEMENTS;  
```  
  
 <span data-ttu-id="c0380-112">필요에 따라 행 요소 이름을 지정하여 기본 <`row`>를 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-112">You can optionally specify the row element name to overwrite the default <`row`>.</span></span> <span data-ttu-id="c0380-113">예를 들어 다음 쿼리는 행 집합의 각 행에 대해 <`ProductModel`> 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-113">For example, the following query returns the <`ProductModel`> element for each row in the rowset.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModel');  
GO  
```  
  
 <span data-ttu-id="c0380-114">결과 XML은 지정된 행 요소 이름을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-114">The resulting XML will have a specified row element name.</span></span>  
  
 `<ProductModel>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ProductModel>`  
  
 `<ProductModel>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ProductModel>`  
  
 <span data-ttu-id="c0380-115">길이가 0인 문자열을 지정하면 래핑 요소가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-115">If you specify a zero-length string, the wrapping element is not produced.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('');  
GO  
```  
  
 <span data-ttu-id="c0380-116">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-116">This is the result:</span></span>  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
## <a name="specifying-xpath-like-column-names"></a><span data-ttu-id="c0380-117">XPath 형식의 열 이름 지정</span><span class="sxs-lookup"><span data-stu-id="c0380-117">Specifying XPath-like column names</span></span>  
 <span data-ttu-id="c0380-118">다음 쿼리에서 지정된 열 이름 `ProductModelID`는 ‘\@’으로 시작하며 슬래시 기호('/')를 포함하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="c0380-118">In the following query the `ProductModelID` column name specified starts with '\@' and does not contain a slash mark ('/').</span></span> <span data-ttu-id="c0380-119">해당 열 값을 포함하는 <`row`> 요소의 특성이 결과 XML에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-119">Therefore, an attribute of the <`row`> element that has the corresponding column value is created in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('ProductModelData');  
GO  
```  
  
 <span data-ttu-id="c0380-120">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-120">This is the result:</span></span>  
  
 `< ProductModelData id="122">`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ ProductModelData >`  
  
 `< ProductModelData id="119">`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ ProductModelData >`  
  
 <span data-ttu-id="c0380-121">`root` 에 `FOR XML`옵션을 지정하여 최상위 요소 하나를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-121">You can add a single top-level element by specifying the `root` option in `FOR XML`.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="c0380-122">계층을 생성하려면 PATH 형식 구문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-122">To generate a hierarchy, you can include PATH-like syntax.</span></span> <span data-ttu-id="c0380-123">예를 들어 `Name` 열의 열 이름을 "SomeChild/ModelName"으로 변경하면 다음 결과와 같이 계층이 있는 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-123">For example, change the column name for the `Name` column to "SomeChild/ModelName" and you will obtain XML with hierarchy, as shown in this result:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="122">`  
  
 `<SomeChild>`  
  
 `<ModelName>All-Purpose Bike Stand</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData id="119">`  
  
 `<SomeChild>`  
  
 `<ModelName>Bike Wash</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="c0380-124">다음 쿼리에서는 제품 모델 ID와 이름 외에 제품 모델의 제조 지침 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-124">Besides the product model ID and name, the following query retrieves the manufacturing instruction locations for the product model.</span></span> <span data-ttu-id="c0380-125">Instructions 열은 `xml` 유형이므로 `query()` 데이터 형식의 `xml` 메서드를 지정하여 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-125">Because the Instructions column is of `xml` type, the `query()` method of `xml` data type is specified to retrieve the location.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') AS ManuInstr  
FROM Production.ProductModel  
WHERE ProductModelID = 7  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="c0380-126">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-126">This is the partial result.</span></span> <span data-ttu-id="c0380-127">쿼리에서 ManuInstr를 열 이름으로 지정 하므로 메서드에 의해 반환 된 XML은 `query()` 다음과 같이 <`ManuInstr`> 태그로 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-127">Because the query specifies ManuInstr as the column name, the XML returned by the `query()` method is wrapped in a <`ManuInstr`> tag as shown in the following:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="7">`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<ManuInstr>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `<MI:step>...</MI:step>...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ManuInstr>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="c0380-128">위의 FOR XML 쿼리에 <`Root`> 및 <`ProductModelData`> 요소에 대한 네임스페이스를 포함하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-128">In the previous FOR XML query, you may want to include namespaces for the <`Root`> and <`ProductModelData`> elements.</span></span> <span data-ttu-id="c0380-129">먼저 WITH XMLNAMESPACES를 사용하여 네임스페이스 바인딩에 접두사를 정의하고 FOR XML 쿼리에 접두사를 사용하여 네임스페이스에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-129">You can do this by first defining the prefix to namespace binding by using WITH XMLNAMESPACES and using prefixes in the FOR XML query.</span></span> <span data-ttu-id="c0380-130">자세한 내용은 [WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가](add-namespaces-to-queries-with-with-xmlnamespaces.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0380-130">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES (  
   'uri1' AS ns1,    
   'uri2' AS ns2,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' as MI)  
SELECT ProductModelID AS "ns1:ProductModelID",  
       Name           AS "ns1:Name",  
       Instructions.query('  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ('ns2:ProductInfo'), root('ns1:root');  
GO  
```  
  
 <span data-ttu-id="c0380-131">`MI` 에는 `WITH XMLNAMESPACES`접두사도 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-131">Note that the `MI` prefix is also defined in the `WITH XMLNAMESPACES`.</span></span> <span data-ttu-id="c0380-132">그 결과로 지정된 `query()` 유형의 `xml` 메서드는 쿼리 프롤로그에 접두사를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-132">As a result, the `query()` method of the `xml` type specified does not define the prefix in the query prolog.</span></span> <span data-ttu-id="c0380-133">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-133">This is the result:</span></span>  
  
 `<ns1:root xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">`  
  
 `<ns2:ProductInfo>`  
  
 `<ns1:ProductModelID>7</ns1:ProductModelID>`  
  
 `<ns1:Name>HL Touring Frame</ns1:Name>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `LaborHours="2.5" LotSize="100" MachineHours="3" SetupHours="0.5" LocationID="10" xmlns="">`  
  
 `<MI:step>`  
  
 `Insert <MI:material>aluminum sheet MS-2341</MI:material> into the <MI:tool>T-85A framing tool</MI:tool>.`  
  
 `</MI:step>`  
  
 `...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ns2:ProductInfo>`  
  
 `</ns1:root>`  
  
## <a name="generating-a-value-list-using-path-mode"></a><span data-ttu-id="c0380-134">PATH 모드를 사용하여 값 목록 생성</span><span class="sxs-lookup"><span data-stu-id="c0380-134">Generating a value list using PATH mode</span></span>  
 <span data-ttu-id="c0380-135">이 쿼리에서는 각 제품 모델에 대해 제품 ID의 값 목록을 생성하고</span><span class="sxs-lookup"><span data-stu-id="c0380-135">For each product model, this query constructs a value list of product IDs.</span></span> <span data-ttu-id="c0380-136">이 XML 조각에서와 같이 각 제품 ID에 대해 <`ProductName`> 중첩 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-136">For each product ID, the query also constructs <`ProductName`> nested elements, as shown in this XML fragment:</span></span>  
  
 `<ProductModelData ProductModelID="7" ProductModelName="..."`  
  
 `ProductIDs="product id list in the product model" >`  
  
 `<ProductName>...</ProductName>`  
  
 `<ProductName>...</ProductName>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="c0380-137">다음은 필요한 XML을 생성하는 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-137">This is the query that produces the XML you want:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID     AS "@ProductModelID",  
       Name               S "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')) S "@ProductIDs",  
       (SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
        FOR XML PATH ('')) as "ProductNames"  
FROM   Production.ProductModel  
WHERE  ProductModelID= 7 or ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="c0380-138">이전 쿼리에서 다음을 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="c0380-138">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="c0380-139">첫 번째 중첩 `SELECT` 는 `data()` 를 열 이름으로 사용하여 ProductID 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-139">The first nested `SELECT` returns a list of ProductIDs by using `data()` as the column name.</span></span> <span data-ttu-id="c0380-140">쿼리에서 빈 문자열을 `FOR XML PATH`의 행 요소 이름으로 지정하므로 요소가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-140">Because the query specifies an empty string as the row element name in `FOR XML PATH`, no element is generated.</span></span> <span data-ttu-id="c0380-141">대신 값 목록이 `ProductID` 특성에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-141">Instead, the value list is assigned to the `ProductID` attribute.</span></span>  
  
-   <span data-ttu-id="c0380-142">두 번째 중첩 `SELECT` 는 제품 모델에 속한 제품에 대해 제품 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-142">The second nested `SELECT` retrieves product names for products in the product model.</span></span> <span data-ttu-id="c0380-143">쿼리에서 `ProductNames`를 열 이름으로 지정하므로 <`ProductNames`> 요소에 래핑되어 반환되는 <`ProductName`> 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-143">It generates <`ProductName`> elements that are returned wrapped in the <`ProductNames`> element, because the query specifies `ProductNames` as the column name.</span></span>  
  
 <span data-ttu-id="c0380-144">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-144">This is the partial result:</span></span>  
  
 `<ProductModelData PId="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>HL Touring Frame - Yellow, 60</ProductName>`  
  
 `<ProductName>HL Touring Frame - Yellow, 46</ProductName></ProductNames>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 `<ProductModelData PId="9"`  
  
 `ProductModelName="LL Road Frame"`  
  
 `ProductIDs="722 723 724 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>LL Road Frame - Black, 58</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 60</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 62</ProductName>`  
  
 `...`  
  
 `</ProductNames>`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="c0380-145">제품 이름을 생성하는 하위 쿼리가 올바르게 수정되어 XML에 추가된 문자열로 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-145">The subquery constructing the product names returns the result as a string that is entitized and then added to the XML.</span></span> <span data-ttu-id="c0380-146">type 지시어 `FOR XML PATH (''), type`을 추가하면 하위 쿼리가 `xml` 유형으로 결과를 반환하며 수정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-146">If you add the type directive, `FOR XML PATH (''), type`, the subquery returns the result as `xml` type and no entitization occurs.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@ProductModelID",  
      Name AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ProductIDs",  
       (  
       SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH (''), type  
       ) AS "ProductNames"  
  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
## <a name="adding-namespaces-in-the-resulting-xml"></a><span data-ttu-id="c0380-147">결과 XML에 네임스페이스 추가</span><span class="sxs-lookup"><span data-stu-id="c0380-147">Adding namespaces in the resulting XML</span></span>  
 <span data-ttu-id="c0380-148">[WITH XMLNAMESPACES를 사용하여 네임스페이스 추가](add-namespaces-to-queries-with-with-xmlnamespaces.md)항목에 설명된 대로 WITH XMLNAMESPACES를 사용하여 PATH 모드 쿼리에 네임스페이스를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-148">As described in [Adding Namespaces Using WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md), you can use WITH XMLNAMESPACES to include namespaces in the PATH mode queries.</span></span> <span data-ttu-id="c0380-149">예를 들어 SELECT 절에 지정된 이름에는 네임스페이스 접두사가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-149">For example, names specified in the SELECT clause include namespace prefixes.</span></span> <span data-ttu-id="c0380-150">다음 `PATH` 모드 쿼리는 네임스페이스가 있는 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-150">The following `PATH` mode query constructs XML with namespaces.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
GO  
```  
  
 <span data-ttu-id="c0380-151"><`English`> 요소에 추가된 `@xml:lang` 특성이 미리 정의된 xml 네임스페이스에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-151">The `@xml:lang` attribute added to the <`English`> element is defined in the predefined xml namespace.</span></span>  
  
 <span data-ttu-id="c0380-152">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-152">This is the result:</span></span>  
  
 `<Translation>`  
  
 `<English xml:lang="en">food</English>`  
  
 `<German xml:lang="ger">Essen</German>`  
  
 `</Translation>`  
  
 <span data-ttu-id="c0380-153">다음 쿼리는 `WITH XMLNAMESPACES` 를 사용하여 XML 결과에 네임스페이스를 포함한다는 점을 제외하고 예 3과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-153">The following query is similar to example C, except that it uses `WITH XMLNAMESPACES` to include namespaces in the XML result.</span></span> <span data-ttu-id="c0380-154">자세한 내용은 [WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가](add-namespaces-to-queries-with-with-xmlnamespaces.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0380-154">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES ('uri1' AS ns1,  DEFAULT 'uri2')  
SELECT ProductModelID AS "@ns1:ProductModelID",  
      Name AS "@ns1:ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ns1:ProductIDs",  
       (  
       SELECT ProductID AS "@ns1:ProductID",   
              Name AS "@ns1:ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH , type   
       ) AS "ns1:ProductNames"  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData'), root('root');  
```  
  
 <span data-ttu-id="c0380-155">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c0380-155">This is the result:</span></span>  
  
 `<root xmlns="uri2" xmlns:ns1="uri1">`  
  
 `<ProductModelData ns1:ProductModelID="7" ns1:ProductModelName="HL Touring Frame" ns1:ProductIDs="885 887 888 889 890 891 892 893">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="885" ns1:ProductName="HL Touring Frame - Yellow, 60" />`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="887" ns1:ProductName="HL Touring Frame - Yellow, 46" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData ns1:ProductModelID="9" ns1:ProductModelName="LL Road Frame" ns1:ProductIDs="722 723 724 725 726 727 728 729 730 736 737 738">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="722" ns1:ProductName="LL Road Frame - Black, 58" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `</root>`  
  
## <a name="see-also"></a><span data-ttu-id="c0380-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0380-156">See Also</span></span>  
 [<span data-ttu-id="c0380-157">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="c0380-157">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
