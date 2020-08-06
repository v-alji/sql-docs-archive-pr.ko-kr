---
title: '예제: 직원 정보 검색 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT mode
ms.assetid: 63cd6569-2600-485b-92b4-1f6ba09db219
author: rothja
ms.author: jroth
ms.openlocfilehash: ae4578aedb7dbcc63388d5ef797e3a0bf5d8c306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651563"
---
# <a name="example-retrieving-employee-information"></a><span data-ttu-id="f2ac1-102">예제: 직원 정보 검색</span><span class="sxs-lookup"><span data-stu-id="f2ac1-102">Example: Retrieving Employee Information</span></span>
  <span data-ttu-id="f2ac1-103">이 예에서는 각 직원에 대한 직원 ID와 직원 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-103">This example retrieves an employee ID and employee name for each employee.</span></span> <span data-ttu-id="f2ac1-104">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 employeeID는 Employee 테이블의 BusinessEntityID 열로부터 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-104">In the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, the employeeID can be obtained from the BusinessEntityID column in the Employee table.</span></span> <span data-ttu-id="f2ac1-105">직원 이름은 Person 테이블로부터 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-105">Employee names can be obtained from the Person table.</span></span> <span data-ttu-id="f2ac1-106">BusinessEntityID 열을 사용하면 테이블을 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-106">The BusinessEntityID column can be used to join the tables.</span></span>  
  
 <span data-ttu-id="f2ac1-107">FOR XML EXPLICIT 변환으로 다음과 같이 XML을 생성한다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-107">Assume that you want FOR XML EXPLICIT transformation to generate XML as shown in the following:</span></span>  
  
```  
<Employee EmpID="1" >  
  <Name FName="Ken" LName="S??nchez" />  
</Employee>  
...  
```  
  
 <span data-ttu-id="f2ac1-108">계층에 두 수준이 있기 때문에 두 개의 `SELECT` 쿼리를 작성하고 UNION ALL을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-108">Because there are two levels in the hierarchy, you would write two `SELECT` queries and apply UNION ALL.</span></span> <span data-ttu-id="f2ac1-109">이 쿼리는 <`Employee`> 요소에 대한 값과 해당 특성을 검색하는 첫 번째 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-109">This is the first query that retrieves values for the <`Employee`> element and its attributes.</span></span> <span data-ttu-id="f2ac1-110">이 쿼리는 <`Employee`> 요소에 대한 `1` 값으로 `Tag`을 할당하고 최상위 요소이기 때문에 `Parent`에는 NULL을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-110">The query assigns `1` as `Tag` value for the <`Employee`> element and NULL as `Parent`, because it is the top-level element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID AS [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="f2ac1-111">다음은 두 번째 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-111">This is the second query.</span></span> <span data-ttu-id="f2ac1-112">이 쿼리는 <`Name`> 요소에 대한 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-112">It retrieves values for the <`Name`> element.</span></span> <span data-ttu-id="f2ac1-113">이 쿼리는 <`Name`> 요소에 대한 `2` 값으로 `Tag`를 할당하고 <`Employee`>를 부모로 지정하는 `1` 태그 값으로 `Parent`을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-113">It assigns `2` as `Tag` value for the <`Name`> element and `1` as `Parent` tag value identifying <`Employee`> as the parent.</span></span>  
  
```  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="f2ac1-114">이러한 쿼리를 `UNION AL`과 조합하고 `FOR XML EXPLICIT`를 적용하고 필요한 `ORDER BY` 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-114">You combine these queries with `UNION AL`L, apply `FOR XML EXPLICIT`, and specify the required `ORDER BY` clause.</span></span> <span data-ttu-id="f2ac1-115">먼저 `BusinessEntityID` 로 행 집합을 정렬하고 이름에 있는 NULL 값이 먼저 표시되도록 이름으로도 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-115">You must sort the rowset first by `BusinessEntityID` and then by name so that the NULL values in the name appear first.</span></span> <span data-ttu-id="f2ac1-116">FOR XML 절 없이 다음 쿼리를 실행하면 범용 테이블이 생성되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-116">By executing the following query without the FOR XML clause, you can see the universal table generated.</span></span>  
  
 <span data-ttu-id="f2ac1-117">마지막 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-117">This is the final query:</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
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
ORDER BY [Employee!1!EmpID],[Name!2!FName]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="f2ac1-118">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-118">This is the partial result:</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name FName="Ken" LName="S??nchez" />`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name FName="Terri" LName="Duffy" />`  
  
 `</Employee>`  
  
 `...`  
  
 <span data-ttu-id="f2ac1-119">첫 번째 `SELECT` 는 결과 행 집합에 대해 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-119">The first `SELECT` specifies names for columns in the resulting rowset.</span></span> <span data-ttu-id="f2ac1-120">이러한 이름은 두 개의 열 그룹을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-120">These names form two column groups.</span></span> <span data-ttu-id="f2ac1-121">열 이름에서 `Tag` 값이 `1` 인 그룹은 `Employee` 를 요소로, `EmpID` 는 특성으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-121">The group that has `Tag` value `1` in the column name identifies `Employee` as an element and `EmpID` as the attribute.</span></span> <span data-ttu-id="f2ac1-122">다른 열 그룹에는 열에 `Tag` 값 `2`가 있으며 <`Name`>을 요소로, `FName` 및 `LName`은 특성으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-122">The other column group has `Tag` value `2` in the column and identifies <`Name`> as the element and `FName` and `LName` as the attributes.</span></span>  
  
 <span data-ttu-id="f2ac1-123">다음 테이블은 쿼리에 의해 생성된 부분 행 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-123">The following table shows the partial rowset generated by the query:</span></span>  
  
 `Tag Parent  Employee!1!EmpID Name!2!FName Name!2!LName`  
  
 `--- ------  ---------------- ------------ ------------`  
  
 `1   NULL    1                NULL         NULL`  
  
 `2   1       1                Ken          S??nchez`  
  
 `1   NULL    2                NULL         NULL`  
  
 `2   1       2                Terri        Duffy`  
  
 `1   NULL    3                NULL         NULL`  
  
 `2   1       3                Roberto      Tamburello`  
  
 `...`  
  
 <span data-ttu-id="f2ac1-124">이 테이블은 범용 테이블의 행을 처리하여 결과 XML 트리를 생성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-124">This is how the rows in the universal table are processed to produce the resulting XML tree:</span></span>  
  
 <span data-ttu-id="f2ac1-125">첫 번째 행은 `Tag` 값 `1`을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-125">The first row identifies `Tag` value `1`.</span></span> <span data-ttu-id="f2ac1-126">따라서 `Tag` 값 `1` 이 있는 열 그룹은 `Employee!1!EmpID`로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-126">Therefore, the column group that has the `Tag` value `1` is identified, `Employee!1!EmpID`.</span></span> <span data-ttu-id="f2ac1-127">이 열은 `Employee` 를 요소 이름으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-127">This column identifies `Employee` as the element name.</span></span> <span data-ttu-id="f2ac1-128">그런 다음 `EmpID` 특성이 포함된 <`Employee`> 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-128">An <`Employee`> element is then created that has `EmpID` attributes.</span></span> <span data-ttu-id="f2ac1-129">이러한 특성에는 해당 열 값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-129">Corresponding column values are assigned to these attributes.</span></span>  
  
 <span data-ttu-id="f2ac1-130">두 번째 행에는 `Tag` 값 `2`가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-130">The second row has the `Tag` value `2`.</span></span> <span data-ttu-id="f2ac1-131">따라서 열 이름에 `Tag` 값 `2` 가 포함된 열 그룹 `Name!2!FName`및 `Name!2!LName`이 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-131">Therefore, the column group that has the `Tag` value `2` in the column name, `Name!2!FName`, `Name!2!LName`, is identified.</span></span> <span data-ttu-id="f2ac1-132">이러한 열 이름은 `Name` 을 요소 이름으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-132">These column names identify `Name` as element name.</span></span> <span data-ttu-id="f2ac1-133">`FName` 및 `LName` 특성이 포함된 <`Name`> 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-133">A <`Name`> element is created that has `FName` and `LName` attributes.</span></span> <span data-ttu-id="f2ac1-134">이러한 특성에는 해당 열 값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-134">Corresponding column values are then assigned to these attributes.</span></span> <span data-ttu-id="f2ac1-135">이 행은 `1` 을 `Parent`로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-135">This row identifies `1` as `Parent`.</span></span> <span data-ttu-id="f2ac1-136">이 요소 자식은 이전 <`Employee`> 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-136">This element child is added to the previous <`Employee`> element.</span></span>  
  
 <span data-ttu-id="f2ac1-137">이러한 프로세스는 행 집합의 남은 열에 대해 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-137">This process is repeated for rest of the rows in the rowset.</span></span> <span data-ttu-id="f2ac1-138">FOR XML EXPLICIT에서 행 집합을 순서대로 처리하고 원하는 XML을 생성하기 위해서는 범용 테이블의 행을 정렬하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ac1-138">Note the importance of ordering the rows in the universal table so that FOR XML EXPLICIT can process the rowset in order and generate the XML you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ac1-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2ac1-139">See Also</span></span>  
 [<span data-ttu-id="f2ac1-140">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="f2ac1-140">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
