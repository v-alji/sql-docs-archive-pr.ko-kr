---
title: 이름이 XPath 노드 테스트인 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6555815d97308bed6e70d9fedb9858fc3abe7685
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730260"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a><span data-ttu-id="56bf5-102">이름이 XPath 노드 테스트인 열</span><span class="sxs-lookup"><span data-stu-id="56bf5-102">Columns with the Name of an XPath Node Test</span></span>
  <span data-ttu-id="56bf5-103">열 이름이 XPath 노드 테스트 중 하나일 경우 다음 표에서와 같이 내용이 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-103">If the column name is one of the XPath node tests, the content is mapped as shown in the following table.</span></span> <span data-ttu-id="56bf5-104">열 이름이 XPath 노드 테스트이면 내용이 해당 노드로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-104">When the column name is an XPath node test, the content is mapped to the corresponding node.</span></span> <span data-ttu-id="56bf5-105">열의 SQL 유형이 `xml`이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-105">If the SQL type of the column is `xml`, an error is returned.</span></span>  
  
|<span data-ttu-id="56bf5-106">열 이름</span><span class="sxs-lookup"><span data-stu-id="56bf5-106">Column Name</span></span>|<span data-ttu-id="56bf5-107">동작</span><span class="sxs-lookup"><span data-stu-id="56bf5-107">Behavior</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="56bf5-108">text()</span><span class="sxs-lookup"><span data-stu-id="56bf5-108">text()</span></span>|<span data-ttu-id="56bf5-109">이름이 text()인 열의 경우 열의 문자열 값이 텍스트 노드로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-109">For a column with the name of text(), the string value in that column is added as a text node.</span></span>|  
|<span data-ttu-id="56bf5-110">comment()</span><span class="sxs-lookup"><span data-stu-id="56bf5-110">comment()</span></span>|<span data-ttu-id="56bf5-111">이름이 comment()인 열의 경우 열의 문자열 값이 XML 주석으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-111">For a column with the name of comment(), the string value in that column is added as an XML comment.</span></span>|  
|<span data-ttu-id="56bf5-112">node()</span><span class="sxs-lookup"><span data-stu-id="56bf5-112">node()</span></span>|<span data-ttu-id="56bf5-113">이름이 node()인 열의 경우 열 이름이 와일드카드 문자(\*)일 때와 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-113">For a column with the name of node(), the result is the same as it is when the column name is a wildcard character (\*).</span></span>|  
|<span data-ttu-id="56bf5-114">processing-instruction(name)</span><span class="sxs-lookup"><span data-stu-id="56bf5-114">processing-instruction(name)</span></span>|<span data-ttu-id="56bf5-115">이름이 처리 명령인 열의 경우 열의 문자열 값이 처리 명령 대상 이름의 PI 값으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-115">For a column with the name of a processing instruction, the string value in that column is added as the PI value for the processing instruction target name.</span></span>|  
  
 <span data-ttu-id="56bf5-116">다음 쿼리에서는 노드 테스트를 열 이름으로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-116">The following query shows the use of the node tests as column names.</span></span> <span data-ttu-id="56bf5-117">쿼리는 결과 XML에 텍스트 노드와 주석을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-117">It adds text nodes and comments in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="56bf5-118">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="56bf5-118">This is the result:</span></span>  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>S??nchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="56bf5-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56bf5-119">See Also</span></span>  
 [<span data-ttu-id="56bf5-120">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="56bf5-120">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
