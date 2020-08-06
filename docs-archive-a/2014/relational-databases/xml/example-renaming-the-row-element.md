---
title: '예제: &lt;행&gt; 요소 이름 바꾸기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: rothja
ms.author: jroth
ms.openlocfilehash: 39375fa125f451f21d936b3a6897b93928fa2f02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646224"
---
# <a name="example-renaming-the-ltrowgt-element"></a><span data-ttu-id="bb3d8-102">예제: &lt;행&gt; 요소 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="bb3d8-102">Example: Renaming the &lt;row&gt; Element</span></span>
  <span data-ttu-id="bb3d8-103">결과 집합의 각 행에 대해 RAW 모드는 `<row>`요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb3d8-103">For each row in the result set, the RAW mode generates an element `<row>`.</span></span> <span data-ttu-id="bb3d8-104">이 쿼리에 표시된 것과 같이 RAW 모드에 선택적 인수를 지정하여 선택적으로 이 요소에 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb3d8-104">You can optionally specify another name for this element by specifying an optional argument to the RAW mode, as shown in this query.</span></span> <span data-ttu-id="bb3d8-105">이 쿼리는 행 집합의 각 행에 대해 <`ProductModel`> 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb3d8-105">The query returns a <`ProductModel`> element for each row in the rowset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb3d8-106">예제</span><span class="sxs-lookup"><span data-stu-id="bb3d8-106">Example</span></span>  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 <span data-ttu-id="bb3d8-107">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="bb3d8-107">This is the result.</span></span> <span data-ttu-id="bb3d8-108">쿼리에 `ELEMENTS` 지시어가 추가되었기 때문에 결과는 요소 중심입니다.</span><span class="sxs-lookup"><span data-stu-id="bb3d8-108">Because the `ELEMENTS` directive is added in the query, the result is element-centric.</span></span>  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a><span data-ttu-id="bb3d8-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb3d8-109">See Also</span></span>  
 [<span data-ttu-id="bb3d8-110">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="bb3d8-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
