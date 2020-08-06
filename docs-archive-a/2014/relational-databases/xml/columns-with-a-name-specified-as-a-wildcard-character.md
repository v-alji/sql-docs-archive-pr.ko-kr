---
title: 이름이 와일드카드 문자로 지정된 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650833"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a><span data-ttu-id="fe723-102">이름이 와일드카드 문자로 지정된 열</span><span class="sxs-lookup"><span data-stu-id="fe723-102">Columns with a Name Specified as a Wildcard Character</span></span>
  <span data-ttu-id="fe723-103">지정된 열 이름이 와일드카드 문자(\*)이면 열 이름이 지정되지 않은 경우처럼 열 내용이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-103">If the column name specified is a wildcard character (\*), the content of that column is inserted as if there is no column name specified.</span></span> <span data-ttu-id="fe723-104">이 열이 비-`xml` 유형 열이면 다음 예에서와 같이 열 내용이 텍스트 노드로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-104">If this column is a non-`xml` type column, the column content is inserted as a text node, as shown in the following example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="fe723-105">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-105">This is the result:</span></span>  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 <span data-ttu-id="fe723-106">열이 `xml` 유형일 경우 해당 XML 트리가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-106">If the column is of `xml` type, the corresponding XML tree is inserted.</span></span> <span data-ttu-id="fe723-107">예를 들어 다음 쿼리는 Instructions 열에 대해 XQuery에서 반환한 XML이 포함된 열 이름에 "\*"를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-107">For example, the following query specifies "\*" for the column name that contains the XML returned by the XQuery against the Instructions column.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 <span data-ttu-id="fe723-108">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-108">This is the result.</span></span> <span data-ttu-id="fe723-109">XQuery에서 반환한 XML이 래핑 요소 없이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe723-109">The XML returned by XQuery is inserted without a wrapping element.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="fe723-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe723-110">See Also</span></span>  
 [<span data-ttu-id="fe723-111">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="fe723-111">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
