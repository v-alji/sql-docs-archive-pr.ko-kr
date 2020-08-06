---
title: '예제: ELEMENT 지시어 및 엔터티 인코딩 지정 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ba4e419d31aa7c02cc2dc8f19a3350c233f042b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728112"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a><span data-ttu-id="ba54a-102">예제: ELEMENT 지시어 및 엔터티 인코딩 지정</span><span class="sxs-lookup"><span data-stu-id="ba54a-102">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>
  <span data-ttu-id="ba54a-103">이 예에서는 **ELEMENT** 및 **XML** 지시어 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-103">This example illustrates the difference between the **ELEMENT** and **XML** directives.</span></span> <span data-ttu-id="ba54a-104">**ELEMENT** 지시어는 데이터를 엔터티화하지만 **XML** 지시어는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-104">The **ELEMENT** directive entitizes the data, but the **XML** directive does not.</span></span> <span data-ttu-id="ba54a-105">\<Summary> 요소는 쿼리에서 할당된 XML인 `<Summary>This is summary description</Summary>`입니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-105">The \<Summary> element is assigned XML, `<Summary>This is summary description</Summary>`, in the query.</span></span>  
  
 <span data-ttu-id="ba54a-106">다음 쿼리를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="ba54a-106">Consider this query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="ba54a-107">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-107">This is the result.</span></span> <span data-ttu-id="ba54a-108">요약 설명이 결과에 엔터티화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-108">The summary description is entitized in the result.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="ba54a-109">이제 **XML** 지시어 대신 열 이름에 `Summary!2!SummaryDescription!XML`ELEMENT **지시어인** 을 지정하면 엔터티화 없이 요약 설명을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-109">Now, if you specify the **XML** directive in the column name, `Summary!2!SummaryDescription!XML`, instead of the **ELEMENT** directive, you will receive the summary description without entitization.</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 <span data-ttu-id="ba54a-110">다음 쿼리에서는 정적 XML 값을 할당하는 대신 **xml** 유형의 **query()** 메서드를 사용하여 **xml** 유형의 CatalogDescription 열에서 제품 모델의 요약 설명을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-110">Instead of assigning a static XML value, the following query uses the **query()** method of the **xml** type to retrieve the product model summary description from the CatalogDescription column of **xml** type.</span></span> <span data-ttu-id="ba54a-111">결과는 **xml** 유형으로 알려져 있기 때문에 엔터티화가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba54a-111">Because the result is known to be of **xml** type, no entitization is applied.</span></span>  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba54a-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba54a-112">See Also</span></span>  
 [<span data-ttu-id="ba54a-113">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="ba54a-113">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
