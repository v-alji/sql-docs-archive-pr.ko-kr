---
title: 이름이 없는 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: rothja
ms.author: jroth
ms.openlocfilehash: 43d1cbce816e4666e6dab52fdffe5850e65740e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730259"
---
# <a name="columns-without-a-name"></a><span data-ttu-id="8aa0f-102">이름이 없는 열</span><span class="sxs-lookup"><span data-stu-id="8aa0f-102">Columns without a Name</span></span>
  <span data-ttu-id="8aa0f-103">이름이 없는 열은 인라인됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-103">Any column without a name will be inlined.</span></span> <span data-ttu-id="8aa0f-104">예를 들어 계산 열이나 열 별칭을 지정하지 않는 중첩된 스칼라 쿼리는 이름이 없는 열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-104">For example, computed columns or nested scalar queries that do not specify column alias will generate columns without any name.</span></span> <span data-ttu-id="8aa0f-105">`xml` 유형의 열일 경우 해당 데이터 형식 인스턴스의 내용이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-105">If the column is of `xml` type, the content of that data type instance is inserted.</span></span> <span data-ttu-id="8aa0f-106">그렇지 않을 경우에는 열 내용이 텍스트 노드로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-106">Otherwise, the column content is inserted as a text node.</span></span>  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 <span data-ttu-id="8aa0f-107">이 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-107">Produce this XML.</span></span> <span data-ttu-id="8aa0f-108">기본적으로 행 집합의 각 행에 대해 결과 XML에 <`row`> 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-108">By default, for each row in the rowset, a <`row`> element is generated in the resulting XML.</span></span> <span data-ttu-id="8aa0f-109">이 동작은 RAW 모드와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-109">This is the same as RAW mode.</span></span>  
  
 `<row>4</row>`  
  
 <span data-ttu-id="8aa0f-110">다음 쿼리는 3개의 열로 구성된 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-110">The following query returns a three-column rowset.</span></span> <span data-ttu-id="8aa0f-111">이름이 없는 세 번째 열에는 XML 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-111">The third column without a name has XML data.</span></span> <span data-ttu-id="8aa0f-112">PATH 모드는 xml 유형의 인스턴스를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-112">The PATH mode inserts an instance of the xml type.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 <span data-ttu-id="8aa0f-113">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa0f-113">This is the partial result:</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="8aa0f-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8aa0f-114">See Also</span></span>  
 [<span data-ttu-id="8aa0f-115">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="8aa0f-115">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
