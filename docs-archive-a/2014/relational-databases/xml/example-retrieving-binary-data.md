---
title: '예제: 이진 데이터 검색 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: rothja
ms.author: jroth
ms.openlocfilehash: 516c7d91d0a6ebac7366b4bb3cbafe5d05aaa232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660921"
---
# <a name="example-retrieving-binary-data"></a><span data-ttu-id="02011-102">예제: 이진 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="02011-102">Example: Retrieving Binary Data</span></span>
  <span data-ttu-id="02011-103">다음 쿼리는 `varbinary(max)` 유형 열에 저장된 제품 사진을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="02011-103">The following query returns the product photo stored in a `varbinary(max)` type column.</span></span> <span data-ttu-id="02011-104">이진 데이터를 base64 인코딩 형식으로 반환하기 위해 쿼리에서 `BINARY BASE64` 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="02011-104">The `BINARY BASE64` option is specified in the query to return the binary data in base64-encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02011-105">예제</span><span class="sxs-lookup"><span data-stu-id="02011-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 <span data-ttu-id="02011-106">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="02011-106">This is the result:</span></span>  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02011-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02011-107">See Also</span></span>  
 [<span data-ttu-id="02011-108">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="02011-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
