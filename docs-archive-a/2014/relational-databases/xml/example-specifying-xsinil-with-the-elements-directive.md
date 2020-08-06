---
title: '예제: ELEMENTS 지시어를 사용하여 XSINIL 지정 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
author: rothja
ms.author: jroth
ms.openlocfilehash: 7817d2c72909ca66fb9fac10f8fcb32a759faf56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728100"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a><span data-ttu-id="df1d6-102">예제: ELEMENTS 지시어를 사용하여 XSINIL 지정</span><span class="sxs-lookup"><span data-stu-id="df1d6-102">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>
  <span data-ttu-id="df1d6-103">다음 쿼리는 `ELEMENTS` 지시어를 지정하여 쿼리 결과로부터 요소 중심 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="df1d6-103">The following query specifies the `ELEMENTS` directive to generate element-centric XML from the query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df1d6-104">예제</span><span class="sxs-lookup"><span data-stu-id="df1d6-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="df1d6-105">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="df1d6-105">This is the partial result.</span></span>  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 <span data-ttu-id="df1d6-106">`Color` 열에 일부 제품에 대해 Null 값이 있기 때문에 결과 XML은 해당 <`Color`> 요소를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df1d6-106">Because the `Color` column has null values for some products, the resulting XML will not generate the corresponding <`Color`> element.</span></span> <span data-ttu-id="df1d6-107">`XSINIL` 지시어를 `ELEMENTS`와 함께 추가하면 NULL 색상 값에 대해서도 <`Color`> 요소를 결과 집합에 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1d6-107">By adding the `XSINIL` directive with `ELEMENTS`, you can generate the <`Color`> element even for NULL color values in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 <span data-ttu-id="df1d6-108">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="df1d6-108">This is the partial result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df1d6-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df1d6-109">See Also</span></span>  
 [<span data-ttu-id="df1d6-110">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="df1d6-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
