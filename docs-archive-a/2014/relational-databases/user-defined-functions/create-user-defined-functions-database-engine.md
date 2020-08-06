---
title: 사용자 정의 함수 만들기(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
ms.openlocfilehash: 790fa1b969f933890e050311173fcde3f12c37ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660376"
---
# <a name="create-user-defined-functions-database-engine"></a><span data-ttu-id="2dd2f-102">사용자 정의 함수 만들기(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="2dd2f-102">Create User-defined Functions (Database Engine)</span></span>
  <span data-ttu-id="2dd2f-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 함수를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-103">This topic describes how to create a user-defined function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2dd2f-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2dd2f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2dd2f-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2dd2f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2dd2f-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2dd2f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2dd2f-107">보안</span><span class="sxs-lookup"><span data-stu-id="2dd2f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2dd2f-108">**사용자 정의 함수를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="2dd2f-108">**To create a user-defined function:**</span></span>  
  
     [<span data-ttu-id="2dd2f-109">스칼라 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="2dd2f-109">Create a Scalar Function</span></span>](#Scalar)  
  
     [<span data-ttu-id="2dd2f-110">테이블 반환 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="2dd2f-110">Create a Table-valued Function</span></span>](#TVF)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2dd2f-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2dd2f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2dd2f-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2dd2f-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2dd2f-113">사용자 정의 함수는 데이터베이스 상태 수정 동작을 수행하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-113">User-defined functions cannot be used to perform actions that modify the database state.</span></span>  
  
-   <span data-ttu-id="2dd2f-114">사용자 정의 함수에는 테이블이 대상인 OUTPUT INTO 절을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-114">User-defined functions cannot contain an OUTPUT INTO clause that has a table as its target.</span></span>  
  
-   <span data-ttu-id="2dd2f-115">사용자 정의 함수는 여러 결과 집합을 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-115">User-defined functions can not return multiple result sets.</span></span> <span data-ttu-id="2dd2f-116">여러 결과 집합을 반환해야 하는 경우 저장 프로시저를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-116">Use a stored procedure if you need to return multiple result sets.</span></span>  
  
-   <span data-ttu-id="2dd2f-117">오류 처리는 사용자 정의 함수에서 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-117">Error handling is restricted in a user-defined function.</span></span> <span data-ttu-id="2dd2f-118">UDF는 TRY...CATCH를 지원 하지 않습니다. CATCH @ERROR 또는 RAISERROR.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-118">A UDF does not support TRY...CATCH, @ERROR or RAISERROR.</span></span>  
  
-   <span data-ttu-id="2dd2f-119">사용자 정의 함수는 저장 프로시저를 호출할 수 없지만 확장 저장 프로시저는 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-119">User-defined functions cannot call a stored procedure, but can call an extended stored procedure.</span></span>  
  
-   <span data-ttu-id="2dd2f-120">사용자 정의 함수는 동적 SQL 또는 임시 테이블을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-120">User-defined functions cannot make use of dynamic SQL or temp tables.</span></span> <span data-ttu-id="2dd2f-121">테이블 변수는 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-121">Table variables are allowed.</span></span>  
  
-   <span data-ttu-id="2dd2f-122">SET 문은 사용자 정의 함수에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-122">SET statements are not allowed in a user-defined function.</span></span>  
  
-   <span data-ttu-id="2dd2f-123">FOR XML 절은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-123">The FOR XML clause is not allowed</span></span>  
  
-   <span data-ttu-id="2dd2f-124">사용자 정의 함수는 중첩될 수 있습니다. 즉, 하나의 사용자 정의 함수가 다른 사용자 정의 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-124">User-defined functions can be nested; that is, one user-defined function can call another.</span></span> <span data-ttu-id="2dd2f-125">중첩 수준은 호출된 함수의 실행이 시작되면 늘어나고 호출된 함수의 실행이 끝나면 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-125">The nesting level is incremented when the called function starts execution, and decremented when the called function finishes execution.</span></span> <span data-ttu-id="2dd2f-126">사용자 정의 함수는 최대 32 수준까지 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-126">User-defined functions can be nested up to 32 levels.</span></span> <span data-ttu-id="2dd2f-127">최대 중첩 수준을 초과하면 전체 함수 호출 체인이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-127">Exceeding the maximum levels of nesting causes the whole calling function chain to fail.</span></span> <span data-ttu-id="2dd2f-128">Transact-SQL 사용자 정의 함수의 관리 코드 참조는 32 수준의 중첩 제한에 대해 한 수준으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-128">Any reference to managed code from a Transact-SQL user-defined function counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="2dd2f-129">관리 코드 내에서 호출된 메서드는 이 제한에 따라 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-129">Methods invoked from within managed code do not count against this limit.</span></span>  
  
-   <span data-ttu-id="2dd2f-130">다음 Service Broker 문은 Transact-SQL 사용자 정의 함수에 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-130">The following Service Broker statements cannot be included in the definition of a Transact-SQL user-defined function:</span></span>  
  
    -   <span data-ttu-id="2dd2f-131">BEGIN DIALOG CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="2dd2f-131">BEGIN DIALOG CONVERSATION</span></span>  
  
    -   <span data-ttu-id="2dd2f-132">END CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="2dd2f-132">END CONVERSATION</span></span>  
  
    -   <span data-ttu-id="2dd2f-133">GET CONVERSATION GROUP</span><span class="sxs-lookup"><span data-stu-id="2dd2f-133">GET CONVERSATION GROUP</span></span>  
  
    -   <span data-ttu-id="2dd2f-134">MOVE CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="2dd2f-134">MOVE CONVERSATION</span></span>  
  
    -   <span data-ttu-id="2dd2f-135">RECEIVE</span><span class="sxs-lookup"><span data-stu-id="2dd2f-135">RECEIVE</span></span>  
  
    -   <span data-ttu-id="2dd2f-136">SEND</span><span class="sxs-lookup"><span data-stu-id="2dd2f-136">SEND</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2dd2f-137">보안</span><span class="sxs-lookup"><span data-stu-id="2dd2f-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2dd2f-138">권한</span><span class="sxs-lookup"><span data-stu-id="2dd2f-138">Permissions</span></span>  
 <span data-ttu-id="2dd2f-139">데이터베이스에 대한 CREATE FUNCTION 권한과 함수가 생성되는 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-139">Requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span> <span data-ttu-id="2dd2f-140">함수에 사용자 정의 형식이 지정되면 해당 유형에 대한 EXECUTE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-140">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="scalar-functions"></a><a name="Scalar"></a><span data-ttu-id="2dd2f-141">스칼라 함수</span><span class="sxs-lookup"><span data-stu-id="2dd2f-141">Scalar Functions</span></span>  
 <span data-ttu-id="2dd2f-142">다음 예에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스의 다중 문 스칼라 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-142">The following example creates a multistatement scalar function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="2dd2f-143">함수에 `ProductID`가 단일 입력 값으로 입력되고 지정한 제품의 총 재고 수량이 단일 데이터 값으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-143">The function takes one input value, a `ProductID`, and returns a single data value, the aggregated quantity of the specified product in inventory.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 <span data-ttu-id="2dd2f-144">다음 예에서는 `ufnGetInventoryStock` 함수를 사용하여 `ProductModelID` 가 75와 80 사이인 제품의 현재 재고 수량을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-144">The following example uses the `ufnGetInventoryStock` function to return the current inventory quantity for products that have a `ProductModelID` between 75 and 80.</span></span>  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="table-valued-functions"></a><a name="TVF"></a><span data-ttu-id="2dd2f-145">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="2dd2f-145">Table-Valued Functions</span></span>  
 <span data-ttu-id="2dd2f-146">다음 예에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스에서 인라인 테이블 값 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-146">The following example creates an inline table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="2dd2f-147">함수에 고객(상점) ID가 단일 입력 매개 변수로 입력되고 `ProductID`, `Name`및 `YTD Total` (해당 상점에 판매된 각 제품의 연간 총 매출액) 열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-147">The function takes one input parameter, a customer (store) ID, and returns the columns `ProductID`, `Name`, and the aggregate of year-to-date sales as `YTD Total` for each product sold to the store.</span></span>  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 <span data-ttu-id="2dd2f-148">다음 예에서는 함수를 호출하고 고객 ID 602를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-148">The following example invokes the function and specifies customer ID 602.</span></span>  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 <span data-ttu-id="2dd2f-149">다음 예에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스에서 테이블 값 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-149">The following example creates a table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="2dd2f-150">함수에 `EmployeeID` 가 단일 입력 매개 변수로 입력되고 지정한 직원에게 직접 또는 간접적으로 보고하는 모든 직원의 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-150">The function takes a single input parameter, an `EmployeeID` and returns a list of all the employees who report to the specified employee directly or indirectly.</span></span> <span data-ttu-id="2dd2f-151">그런 다음 직원 ID 109를 지정하여 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-151">The function is then invoked specifying employee ID 109.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dd2f-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dd2f-152">See Also</span></span>  
 <span data-ttu-id="2dd2f-153">[사용자 정의 함수](user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="2dd2f-153">[User-Defined Functions](user-defined-functions.md) </span></span>  
 [<span data-ttu-id="2dd2f-154">CREATE FUNCTION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2dd2f-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
