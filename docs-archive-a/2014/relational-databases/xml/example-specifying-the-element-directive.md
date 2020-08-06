---
title: '예제: ELEMENT 지시어 지정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
ms.assetid: 80dd5d1f-fa90-4f97-a186-8fa3f460a7f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a03d1049fa9df23eff759634bcd74f88f842a8e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728103"
---
# <a name="example-specifying-the-element-directive"></a><span data-ttu-id="91ea6-102">예제: ELEMENT 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="91ea6-102">Example: Specifying the ELEMENT Directive</span></span>
  <span data-ttu-id="91ea6-103">이 예에서는 직원 정보를 검색하고 다음과 같이 요소 중심 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="91ea6-103">This retrieves employee information and generates element-centric XML as shown in the following:</span></span>  
  
```  
<Employee EmpID=...>  
  <Name>  
    <FName>...</FName>  
    <LName>...</LName>  
  </Name>  
</Employee>  
```  
  
 <span data-ttu-id="91ea6-104">열 이름에 `ELEMENT` 지시어가 추가된 것을 제외하면 쿼리는 같은 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="91ea6-104">The query remains the same, except you add the `ELEMENT` directive in the column names.</span></span> <span data-ttu-id="91ea6-105">따라서 특성 대신 <`FName`> 및 <`LName`> 요소 자식이 <`Name`> 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="91ea6-105">Therefore, instead of attributes, the <`FName`> and <`LName`> element children are added to the <`Name`> element.</span></span> <span data-ttu-id="91ea6-106">`Employee!1!EmpID` 열은 `ELEMENT` 지시어를 지정하지 않기 때문에 `EmpID`가 <`Employee`> 요소의 특성으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="91ea6-106">Because the `Employee!1!EmpID` column does not specify the `ELEMENT` directive, `EmpID` is added as the attribute of the <`Employee`> element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName!ELEMENT],  
       NULL       as [Name!2!LName!ELEMENT]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
ORDER BY [Employee!1!EmpID],[Name!2!FName!ELEMENT]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="91ea6-107">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="91ea6-107">This is the partial result.</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name>`  
  
 `<FName>Ken</FName>`  
  
 `<LName>S??nchez</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name>`  
  
 `<FName>Terri</FName>`  
  
 `<LName>Duffy</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `...`  
  
## <a name="see-also"></a><span data-ttu-id="91ea6-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91ea6-108">See Also</span></span>  
 [<span data-ttu-id="91ea6-109">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="91ea6-109">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
