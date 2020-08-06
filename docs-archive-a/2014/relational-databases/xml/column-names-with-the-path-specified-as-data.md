---
title: 경로가 data()로 지정된 열 이름 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: rothja
ms.author: jroth
ms.openlocfilehash: 61aa7f85c7ee2358ddcf99f81c87c1295fac8fb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646233"
---
# <a name="column-names-with-the-path-specified-as-data"></a><span data-ttu-id="d3bdd-102">경로가 data()로 지정된 열 이름</span><span class="sxs-lookup"><span data-stu-id="d3bdd-102">Column Names with the Path Specified as data()</span></span>
  <span data-ttu-id="d3bdd-103">열 이름으로 지정된 경로가 "data()"일 경우 생성된 XML에서 해당 값이 원자 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-103">If the path specified as column name is "data()", the value is treated as an atomic value in the generated XML.</span></span> <span data-ttu-id="d3bdd-104">직렬화의 다음 항목도 원자성 값이면 공백 문자가 XML에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-104">A space character is added to the XML if the next item in the serialization is also an atomic value.</span></span> <span data-ttu-id="d3bdd-105">이 특징은 목록 유형의 요소와 특성 값을 만들 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-105">This is useful when you are creating list typed element and attribute values.</span></span> <span data-ttu-id="d3bdd-106">다음 쿼리는 제품 모델 ID, 이름 및 해당 제품 모델에 속한 제품 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-106">The following query retrieves the product model ID, name, and list of products in that product model.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="d3bdd-107">중첩 SELECT가 제품 ID 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-107">The nested SELECT retrieves a list of product IDs.</span></span> <span data-ttu-id="d3bdd-108">"data()"를 제품 ID에 대한 열 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-108">It specifies "data()" as the column name for product IDs.</span></span> <span data-ttu-id="d3bdd-109">PATH 모드에서는 행 요소 이름에 빈 문자열을 지정하므로 행 요소가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-109">Because PATH mode specifies an empty string for the row element name, there is no row element generated.</span></span> <span data-ttu-id="d3bdd-110">대신 부모 SELECT의 <`ProductModelData`> 행 요소에 대한 ProductID 특성에 할당된 대로 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-110">Instead, the values are returned as assigned to a ProductIDs attribute of the <`ProductModelData`> row element of the parent SELECT.</span></span> <span data-ttu-id="d3bdd-111">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="d3bdd-111">This is the result:</span></span>  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a><span data-ttu-id="d3bdd-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3bdd-112">See Also</span></span>  
 [<span data-ttu-id="d3bdd-113">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="d3bdd-113">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
