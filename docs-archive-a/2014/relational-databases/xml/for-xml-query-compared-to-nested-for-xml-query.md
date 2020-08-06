---
title: FOR XML 쿼리와 중첩 FOR XML 쿼리 비교 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], comparing query types
ms.assetid: 19225b4a-ee3f-47cf-8bcc-52699eeda32c
author: rothja
ms.author: jroth
ms.openlocfilehash: ca10060702d0c7e50f2be79310c55e177dca358d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743100"
---
# <a name="for-xml-query-compared-to-nested-for-xml-query"></a><span data-ttu-id="a2a83-102">FOR XML 쿼리와 중첩 FOR XML 쿼리 비교</span><span class="sxs-lookup"><span data-stu-id="a2a83-102">FOR XML Query Compared to Nested FOR XML Query</span></span>
  <span data-ttu-id="a2a83-103">이 항목에서는 단일 수준 FOR XML 쿼리를 중첩 FOR XML 쿼리와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-103">This topic compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="a2a83-104">중첩 FOR XML 쿼리를 사용할 때의 이점 중 하나는 쿼리 결과에 특성 중심 및 요소 중심의 XML을 조합하여 지정할 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-104">One of the benefits of using nested FOR XML queries is that you can specify a combination of attribute-centric and element-centric XML for query results.</span></span> <span data-ttu-id="a2a83-105">다음 예에서는 이러한 이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-105">The example demonstrates this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a83-106">예제</span><span class="sxs-lookup"><span data-stu-id="a2a83-106">Example</span></span>  
 <span data-ttu-id="a2a83-107">다음 `SELECT` 쿼리는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 제품 범주와 하위 범주 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-107">The following `SELECT` query retrieves product category and subcategory information in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="a2a83-108">쿼리에는 중첩 FOR XML이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-108">There is no nested FOR XML in the query.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductCategory.ProductCategoryID,   
         ProductCategory.Name as CategoryName,  
         ProductSubCategory.ProductSubCategoryID,   
         ProductSubCategory.Name  
FROM     Production.ProductCategory, Production.ProductSubCategory  
WHERE    ProductCategory.ProductCategoryID = ProductSubCategory.ProductCategoryID  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="a2a83-109">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-109">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory ProductSubCategoryID="1" Name="Mountain Bike"/>  
  <ProductSubCategory ProductSubCategoryID="2" Name="Road Bike"/>  
  <ProductSubCategory ProductSubCategoryID="3" Name="Touring Bike"/>  
</ProductCategory>  
...  
```  
  
 <span data-ttu-id="a2a83-110">쿼리에서 `ELEMENTS` 지시어를 지정하면 다음 결과 조각에서와 같이 요소 중심 결과를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-110">If you specify the `ELEMENTS` directive in the query, you receive an element-centric result, as shown in the following result fragment:</span></span>  
  
```  
<ProductCategory>  
  <ProductCategoryID>1</ProductCategoryID>  
  <CategoryName>Bike</CategoryName>  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <Name>Mountain Bike</Name>  
  </ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  </ProductSubCategory>  
</ProductCategory>  
```  
  
 <span data-ttu-id="a2a83-111">그런 후 다음 조각에서와 같이 특성 중심 및 요소 중심 XML이 조합된 XML 계층을 생성한다고 가정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2a83-111">Next, assume that you want to generate an XML hierarchy that is a combination of attribute-centric and element-centric XML, as shown in the following fragment:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="a2a83-112">이전 조각에서 범주 ID 및 범주 이름과 같은 제품 범주 정보는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-112">In the previous fragment, product category information such as category ID and category name are attributes.</span></span> <span data-ttu-id="a2a83-113">하지만 하위 범주 정보는 요소 중심입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-113">However, the subcategory information is element-centric.</span></span> <span data-ttu-id="a2a83-114"><`ProductCategory`> 요소를 생성하기 위해 다음과 같이 `FOR XML` 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-114">To construct the <`ProductCategory`> element, you can write a `FOR XML` query as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName  
FROM Production.ProductCategory ProdCat  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="a2a83-115">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-115">This is the result:</span></span>  
  
```  
< ProdCat ProductCategoryID="1" CategoryName="Bikes" />  
< ProdCat ProductCategoryID="2" CategoryName="Components" />  
< ProdCat ProductCategoryID="3" CategoryName="Clothing" />  
< ProdCat ProductCategoryID="4" CategoryName="Accessories" />  
```  
  
 <span data-ttu-id="a2a83-116">그런 다음 XML에서 원하는 중첩된 <`ProductSubCategory`> 요소를 생성하려면 다음과 같이 중첩된 `FOR XML` 쿼리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-116">To construct the nested <`ProductSubCategory`> elements in the XML you want, you then add a nested `FOR XML` query, as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName  
        FROM   Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="a2a83-117">이전 쿼리에서 다음을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2a83-117">Note the following in the previous query:</span></span>  
  
-   <span data-ttu-id="a2a83-118">내부 `FOR XML` 쿼리는 제품 하위 범주 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-118">The inner `FOR XML` query retrieves product subcategory information.</span></span> <span data-ttu-id="a2a83-119">`ELEMENTS` 지시어는 외부 쿼리에 의해 생성되는 XML에 추가된 요소 중심 XML을 생성하기 위해 내부 `FOR XML` 에 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-119">The `ELEMENTS` directive is added in the inner `FOR XML` to generate element-centric XML that is added to the XML generated by the outer query.</span></span> <span data-ttu-id="a2a83-120">기본적으로 외부 쿼리는 특성 중심 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-120">By default, the outer query generates attribute-centric XML.</span></span>  
  
-   <span data-ttu-id="a2a83-121">내부 쿼리에서 결과가 `TYPE` xml **유형이 되도록** 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-121">In the inner query, the `TYPE` directive is specified so the result is of **xml** type.</span></span> <span data-ttu-id="a2a83-122">`TYPE`을 지정하지 않으면 결과가 `nvarchar(max)` 유형으로 반환되고 XML 데이터는 엔터티로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-122">If `TYPE` is not specified, the result is returned as `nvarchar(max)` type and the XML data is returned as entities.</span></span>  
  
-   <span data-ttu-id="a2a83-123">외부 쿼리도 `TYPE` 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-123">The outer query also specifies the `TYPE` directive.</span></span> <span data-ttu-id="a2a83-124">따라서 이 쿼리의 결과는 클라이언트에 **xml** 유형으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-124">Therefore, the result of this query is returned to the client as **xml** type.</span></span>  
  
 <span data-ttu-id="a2a83-125">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-125">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="a2a83-126">다음 쿼리는 이전 쿼리를 확장한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-126">The following query is just an extension of the previous query.</span></span> <span data-ttu-id="a2a83-127">여기에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 전체 제품 계층을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-127">It shows the full product hierarchy in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="a2a83-128">여기에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-128">This includes the following:</span></span>  
  
-   <span data-ttu-id="a2a83-129">제품 범주</span><span class="sxs-lookup"><span data-stu-id="a2a83-129">Product categories</span></span>  
  
-   <span data-ttu-id="a2a83-130">각 범주의 제품 하위 범주</span><span class="sxs-lookup"><span data-stu-id="a2a83-130">Product subcategories in each category</span></span>  
  
-   <span data-ttu-id="a2a83-131">각 하위 범주의 제품 모델</span><span class="sxs-lookup"><span data-stu-id="a2a83-131">Product models in each subcategory</span></span>  
  
-   <span data-ttu-id="a2a83-132">각 모델의 제품</span><span class="sxs-lookup"><span data-stu-id="a2a83-132">Products in each model</span></span>  
  
 <span data-ttu-id="a2a83-133">다음 쿼리는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-133">You might find the following query useful in understanding the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName,  
               (SELECT ProductModel.ProductModelID,   
                       ProductModel.Name as ModelName,  
                       (SELECT ProductID, Name as ProductName, Color  
                        FROM   Production.Product  
                        WHERE  Product.ProductModelID =   
                               ProductModel.ProductModelID  
                        FOR XML AUTO, TYPE)  
                FROM   (SELECT distinct ProductModel.ProductModelID,   
                               ProductModel.Name  
                        FROM   Production.ProductModel,   
                               Production.Product  
                        WHERE  ProductModel.ProductModelID =   
                               Product.ProductModelID  
                        AND    Product.ProductSubCategoryID =   
                               ProductSubCategory.ProductSubCategoryID)   
                                  ProductModel  
                FOR XML AUTO, type  
               )  
        FROM Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="a2a83-134">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-134">This is the partial result:</span></span>  
  
```  
<Production.ProductCategory ProductCategoryID="1" CategoryName="Bikes">  
  <Production.ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bikes</SubCategoryName>  
    <ProductModel ProductModelID="19" ModelName="Mountain-100">  
      <Production.Product ProductID="771"   
                ProductName="Mountain-100 Silver, 38" Color="Silver" />  
      <Production.Product ProductID="772"   
                ProductName="Mountain-100 Silver, 42" Color="Silver" />  
      <Production.Product ProductID="773"   
                ProductName="Mountain-100 Silver, 44" Color="Silver" />  
        ...  
    </ProductModel>  
     ...  
```  
  
 <span data-ttu-id="a2a83-135">제품 하위 범주를 생성하는 중첩된 `ELEMENTS` 쿼리에서 `FOR XML` 지시어를 제거하면 전체 결과가 특성 중심이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-135">If you remove the `ELEMENTS` directive from the nested `FOR XML` query that generates product subcategories, the whole result is attribute-centric.</span></span> <span data-ttu-id="a2a83-136">그런 다음 중첩 없이 이 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-136">You can then write this query without nesting.</span></span> <span data-ttu-id="a2a83-137">`ELEMENTS` 를 추가하면 부분적으로 특성 중심이고 요소 중심이기도 한 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-137">The addition of `ELEMENTS` results in an XML that is partly attribute-centric and partly element-centric.</span></span> <span data-ttu-id="a2a83-138">이 결과는 단일 수준의 FOR XML 쿼리에 의해 생성될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a83-138">This result cannot be generated by a single-level, FOR XML query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a83-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2a83-139">See Also</span></span>  
 [<span data-ttu-id="a2a83-140">중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="a2a83-140">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
