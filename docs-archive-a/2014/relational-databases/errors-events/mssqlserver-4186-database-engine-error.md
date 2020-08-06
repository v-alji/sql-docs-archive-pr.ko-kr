---
title: MSSQLSERVER_4186 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525c1c3bd6e631044b8bc7f17b2c2a01aeb1ef8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646519"
---
# <a name="mssqlserver_4186"></a><span data-ttu-id="23313-102">MSSQLSERVER_4186</span><span class="sxs-lookup"><span data-stu-id="23313-102">MSSQLSERVER_4186</span></span>
    
## <a name="details"></a><span data-ttu-id="23313-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="23313-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23313-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="23313-104">Product Name</span></span>|<span data-ttu-id="23313-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23313-105">SQL Server</span></span>|  
|<span data-ttu-id="23313-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="23313-106">Event ID</span></span>|<span data-ttu-id="23313-107">4186</span><span class="sxs-lookup"><span data-stu-id="23313-107">4186</span></span>|  
|<span data-ttu-id="23313-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="23313-108">Event Source</span></span>|<span data-ttu-id="23313-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23313-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23313-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="23313-110">Component</span></span>|<span data-ttu-id="23313-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23313-111">SQLEngine</span></span>|  
|<span data-ttu-id="23313-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="23313-112">Symbolic Name</span></span>||  
|<span data-ttu-id="23313-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="23313-113">Message Text</span></span>|<span data-ttu-id="23313-114">열 '%ls.%.\*ls'의 정의가 하위 쿼리를 포함하거나 사용자 또는 시스템 데이터에 액세스하는 함수를 참조하므로 OUTPUT 절에서 해당 열을 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23313-114">Column '%ls.%.\*ls' cannot be referenced in the OUTPUT clause because the column definition contains a subquery or references a function that performs user or system data access.</span></span> <span data-ttu-id="23313-115">함수가 스키마 바인딩되지 않으면 기본적으로 데이터 액세스를 수행하도록 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="23313-115">A function is assumed by default to perform data access if it is not schemabound.</span></span> <span data-ttu-id="23313-116">열 정의에서 하위 쿼리나 함수를 제거하거나 OUTPUT 절에서 열을 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="23313-116">Consider removing the subquery or function from the column definition or removing the column from the OUTPUT clause.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23313-117">설명</span><span class="sxs-lookup"><span data-stu-id="23313-117">Explanation</span></span>  
 <span data-ttu-id="23313-118">비결정적 동작을 방지하기 위해 OUTPUT 절은 뷰 또는 인라인 테이블 반환 함수의 열이 다음 중 한 가지 방법으로 정의된 경우 이러한 열을 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23313-118">To prevent nondeterministic behavior, the OUTPUT clause cannot reference a column from a view or inline table-valued function when that column is defined by one of the following methods:</span></span>  
  
-   <span data-ttu-id="23313-119">하위 쿼리</span><span class="sxs-lookup"><span data-stu-id="23313-119">A subquery.</span></span>  
  
-   <span data-ttu-id="23313-120">사용자 또는 시스템 데이터 액세스를 수행하거나 이러한 액세스를 수행하는 것으로 간주되는 사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="23313-120">A user-defined function that performs user or system data access, or is assumed to perform such access.</span></span>  
  
-   <span data-ttu-id="23313-121">해당 정의에서 사용자 또는 시스템 데이터 액세스를 수행하는 사용자 정의 함수가 포함된 계산 열</span><span class="sxs-lookup"><span data-stu-id="23313-121">A computed column that contains a user-defined function that performs user or system data access in its definition.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23313-122">예제</span><span class="sxs-lookup"><span data-stu-id="23313-122">Examples</span></span>  
 <span data-ttu-id="23313-123">**하위 쿼리에 의해 정의되는 뷰 열**</span><span class="sxs-lookup"><span data-stu-id="23313-123">**View Column Defined by a Subquery**</span></span>  
  
 <span data-ttu-id="23313-124">다음 예에서는 열 `State`를 정의하기 위해 선택 목록에 있는 하위 쿼리를 사용하는 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23313-124">The following example creates a view that uses a subquery in the select list to define the column `State`.</span></span> <span data-ttu-id="23313-125">그러면 UPDATE 문이 OUTPUT 절의 `State` 열을 참조하지만 선택 목록의 하위 쿼리로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-125">An UPDATE statement then references the `State` column in the OUTPUT clause and fails because ob the subquery in the select list.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
 <span data-ttu-id="23313-126">**함수에 의해 정의되는 뷰 열**</span><span class="sxs-lookup"><span data-stu-id="23313-126">**View Column Defined by a Function**</span></span>  
  
 <span data-ttu-id="23313-127">다음 예제에서는 열 `CurrentInventory`를 정의하기 위해 선택 목록에 있는 데이터 액세스 스칼라 함수 `dbo.ufnGetStock`을 사용하는 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23313-127">The following example creates a view that uses the data accessing, scalar function `dbo.ufnGetStock` in the select list to define the column `CurrentInventory`.</span></span> <span data-ttu-id="23313-128">그러면 UPDATE 문이 OUTPUT 절의 `CurrentInventory` 열을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-128">An UPDATE statement then references the `CurrentInventory` column in the OUTPUT clause .</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a><span data-ttu-id="23313-129">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="23313-129">User Action</span></span>  
 <span data-ttu-id="23313-130">다음과 같은 방법으로 오류 4186을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23313-130">Error 4186 can be corrected in one of the following ways:</span></span>  
  
-   <span data-ttu-id="23313-131">하위 쿼리 대신 조인을 사용하여 뷰 또는 함수의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-131">Use joins instead of subqueries to define the column in the view or function.</span></span> <span data-ttu-id="23313-132">예를 들어 다음과 같이 뷰 `dbo.V1`을 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23313-132">For example, you can rewrite the view `dbo.V1` as follows.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   <span data-ttu-id="23313-133">사용자 정의 함수의 정의를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-133">Examine the definition of the user-defined function.</span></span> <span data-ttu-id="23313-134">사용자 정의 함수가 사용자 또는 시스템 액세스를 수행하지 않으면 WITH SCHEMABINDING 절을 포함하도록 함수를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-134">If the function does not perform user or system data access, alter the function to include the WITH SCHEMABINDING clause.</span></span>  
  
-   <span data-ttu-id="23313-135">OUTPUT 절에서 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="23313-135">Remove the column from the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23313-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23313-136">See Also</span></span>  
 [<span data-ttu-id="23313-137">OUTPUT 절&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="23313-137">OUTPUT Clause &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/output-clause-transact-sql)  
  
  
