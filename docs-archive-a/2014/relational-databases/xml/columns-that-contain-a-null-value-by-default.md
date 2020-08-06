---
title: 기본적으로 Null 값을 포함하는 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ea51101f73695be2075a1b41deb62ca021f496
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646231"
---
# <a name="columns-that-contain-a-null-value-by-default"></a><span data-ttu-id="9d19c-102">기본적으로 Null 값을 포함하는 열</span><span class="sxs-lookup"><span data-stu-id="9d19c-102">Columns that Contain a Null Value By Default</span></span>
  <span data-ttu-id="9d19c-103">기본적으로 열에 Null 값이 있으면 특성, 노드 또는 요소가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d19c-103">By default, a null value in a column maps to the absence of the attribute, node, or element.</span></span> <span data-ttu-id="9d19c-104">다음 쿼리에서와 같이 ELEMENTS 지시어를 사용하여 요소 중심 XML을 요청하고 NULL 값에 대해 요소 추가를 요청하도록 XSINIL을 지정하면 이 기본 동작을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d19c-104">This default behavior can be overwritten by requesting element-centric XML using the ELEMENTS directive and specifying XSINIL to request adding elements for NULL values, as shown in the following query:</span></span>  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="9d19c-105">다음은 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9d19c-105">The following shows the result.</span></span> <span data-ttu-id="9d19c-106">XSINIL을 지정하지 않으면 <`Middle`> 요소가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d19c-106">Note that if XSINIL is not specified, the <`Middle`> element will be absent.</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d19c-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d19c-107">See Also</span></span>  
 [<span data-ttu-id="9d19c-108">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="9d19c-108">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
