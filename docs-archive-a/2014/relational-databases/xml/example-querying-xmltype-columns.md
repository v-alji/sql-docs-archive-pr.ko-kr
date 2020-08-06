---
title: '예제: XMLType 열 쿼리 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: rothja
ms.author: jroth
ms.openlocfilehash: 0eedfa5a5a265f3715a76a6ca80d489bbec199bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646225"
---
# <a name="example-querying-xmltype-columns"></a><span data-ttu-id="a72b8-102">예제: XMLType 열 쿼리</span><span class="sxs-lookup"><span data-stu-id="a72b8-102">Example: Querying XMLType Columns</span></span>
  <span data-ttu-id="a72b8-103">다음 쿼리에는 `xml` 유형의 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-103">The following query includes columns of `xml` type.</span></span> <span data-ttu-id="a72b8-104">이 쿼리는 `xml` 유형의 `Instructions` 열로부터 첫 번째 위치에서 제품 모델 ID, 이름 및 제조 단계를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-104">The query retrieves product model ID, name, and manufacturing steps at the first location from the `Instructions` column of the `xml` type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a72b8-105">예제</span><span class="sxs-lookup"><span data-stu-id="a72b8-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 <span data-ttu-id="a72b8-106">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-106">The following is the result.</span></span> <span data-ttu-id="a72b8-107">테이블에는 일부 제품 모델에 대해서만 제조 지침이 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-107">Note that the table stores manufacturing instructions for only some product models.</span></span> <span data-ttu-id="a72b8-108">제조 단계는 <`ProductModelData`> 요소의 하위 요소로 결과에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-108">The manufacturing steps are returned as subelements of the <`ProductModelData`> element in the result.</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 <span data-ttu-id="a72b8-109">다음 `SELECT` 문에 지정된 것과 같이 쿼리가 XQuery에 의해 반환된 XML에 대한 열 이름을 지정하는 경우 제조 단계는 지정된 이름이 포함된 요소에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-109">If the query specifies a column name for the XML returned by the XQuery, as specified in the following `SELECT` statement, the manufacturing steps are wrapped in the element that has the specified name.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 <span data-ttu-id="a72b8-110">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-110">This is the result:</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 <span data-ttu-id="a72b8-111">다음 쿼리는 `ELEMENTS` 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-111">The following query specifies the `ELEMENTS` directive.</span></span> <span data-ttu-id="a72b8-112">따라서 반환된 결과는 요소 중심입니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-112">Therefore, the result returned is element-centric.</span></span> <span data-ttu-id="a72b8-113">`XSINIL` 지시어와 함께 지정된 `ELEMENTS` 옵션은 행 집합의 해당 열이 NULL인 경우에도 <`ManuSteps`> 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-113">The `XSINIL` option specified with the `ELEMENTS` directive returns the <`ManuSteps`> elements, even if the corresponding column in the rowset is NULL.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 <span data-ttu-id="a72b8-114">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a72b8-114">This is the result:</span></span>  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a72b8-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a72b8-115">See Also</span></span>  
 [<span data-ttu-id="a72b8-116">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="a72b8-116">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
