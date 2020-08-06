---
title: 저장 프로시저 다시 컴파일 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sp_recompile
- WITH RECOMPILE clause
- recompiling stored procedures
- stored procedures [SQL Server], recompiling
ms.assetid: b90deb27-0099-4fe7-ba60-726af78f7c18
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a9bc0e1d4baecb7f4c66b83b57081ed3131123d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661623"
---
# <a name="recompile-a-stored-procedure"></a><span data-ttu-id="32c54-102">저장 프로시저 다시 컴파일</span><span class="sxs-lookup"><span data-stu-id="32c54-102">Recompile a Stored Procedure</span></span>
  <span data-ttu-id="32c54-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저를 다시 컴파일하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-103">This topic describes how to recompile a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="32c54-104">이 작업을 수행 하는 방법에는 다음 세 가지가 있습니다. `WITH RECOMPILE` 옵션은 프로시저 정의 또는 프로시저가 호출 될 때, `RECOMPILE` 개별 문에 대해 쿼리 힌트를 사용 하거나 `sp_recompile` 시스템 저장 프로시저를 사용 하 여 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-104">There are three ways to do this: `WITH RECOMPILE` option in the procedure definition or when the procedure is called, the `RECOMPILE` query hint on individual statements, or by using the `sp_recompile` system stored procedure.</span></span> <span data-ttu-id="32c54-105">이 항목에서는 프로시저 정의를 만들고 기존 프로시저를 실행할 때 RECOMPILE 옵션을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-105">This topic describes using the WITH RECOMPILE option when creating a procedure definition and executing an existing procedure.</span></span> <span data-ttu-id="32c54-106">또한 sp_recompile 시스템 저장 프로시저를 사용하여 기존 프로시저를 다시 컴파일하는 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-106">It also describes using the sp_recompile system stored procedure to recompile an existing procedure.</span></span>  
  
 <span data-ttu-id="32c54-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="32c54-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="32c54-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="32c54-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="32c54-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="32c54-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="32c54-110">보안</span><span class="sxs-lookup"><span data-stu-id="32c54-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="32c54-111">**저장 프로시저를 다시 컴파일하려면:**</span><span class="sxs-lookup"><span data-stu-id="32c54-111">**To recompile a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="32c54-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32c54-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="32c54-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="32c54-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="32c54-114">권장 사항</span><span class="sxs-lookup"><span data-stu-id="32c54-114">Recommendations</span></span>  
  
-   <span data-ttu-id="32c54-115">프로시저가 처음 컴파일되거나 다시 컴파일될 때 프로시저의 쿼리 계획은 데이터베이스와 해당 개체의 현재 상태에 맞게 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-115">When a procedure is compiled for the first time or recompiled, the procedure's query plan is optimized for the current state of the database and its objects.</span></span> <span data-ttu-id="32c54-116">데이터베이스의 데이터나 구조가 크게 변경되는 경우 프로시저를 다시 컴파일하면 해당 변경 내용에 대한 프로시저의 쿼리 계획이 업데이트되고 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-116">If a database undergoes significant changes to its data or structure, recompiling a procedure updates and optimizes the procedure's query plan for those changes.</span></span> <span data-ttu-id="32c54-117">이에 따라 프로시저의 처리 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-117">This can improve the procedure's processing performance.</span></span>  
  
-   <span data-ttu-id="32c54-118">프로시저 재컴파일이 강제로 수행되어야 하는 경우도 있고 자동으로 발생하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-118">There are times when procedure recompilation must be forced and other times when it occurs automatically.</span></span> <span data-ttu-id="32c54-119">자동 재컴파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 다시 시작될 때마다 발생하고</span><span class="sxs-lookup"><span data-stu-id="32c54-119">Automatic recompiling occurs whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span> <span data-ttu-id="32c54-120">프로시저에서 참조하는 기본 테이블의 물리적 디자인이 변경되는 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-120">It also occurs if an underlying table referenced by the procedure has undergone physical design changes.</span></span>  
  
-   <span data-ttu-id="32c54-121">프로시저를 강제로 다시 컴파일하는 또 다른 이유는 프로시저 컴파일의 "매개 변수 스니핑" 동작을 막기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-121">Another reason to force a procedure to recompile is to counteract the "parameter sniffing" behavior of procedure compilation.</span></span> <span data-ttu-id="32c54-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 프로시저를 실행하면 프로시저 컴파일에 사용되는 모든 매개 변수 값이 쿼리 계획 생성 시 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-122">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes procedures, any parameter values that are used by the procedure when it compiles are included as part of generating the query plan.</span></span> <span data-ttu-id="32c54-123">이러한 매개 변수 값이 나중에 프로시저를 호출할 때 사용되는 일반적인 값을 나타낼 경우 프로시저가 컴파일되고 실행될 때마다 이 쿼리 계획을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-123">If these values represent the typical ones with which the procedure is subsequently called, then the procedure benefits from the query plan every time that it compiles and executes.</span></span> <span data-ttu-id="32c54-124">프로시저의 매개 변수 값이 흔히 부정형인 경우 여러 가지 매개 변수 값에 따라 새 계획과 프로시저 재컴파일을 강제로 적용하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-124">If parameter values on the procedure are frequently atypical, forcing a recompile of the procedure and a new plan based on different parameter values can improve performance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="32c54-125">에서는 프로시저를 문 수준으로 다시 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-125">features statement-level recompilation of procedures.</span></span> <span data-ttu-id="32c54-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 저장 프로시저를 다시 컴파일할 때 전체 프로시저가 아닌 재컴파일이 필요한 문만 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recompiles stored procedures, only the statement that caused the recompilation is compiled, instead of the complete procedure.</span></span>  
  
-   <span data-ttu-id="32c54-127">프로시저의 특정 쿼리에서 비정형 값이나 임시 값을 정기적으로 사용하는 경우 해당 쿼리 내에서 RECOMPILE 쿼리 힌트를 사용하여 프로시저 성능을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-127">If certain queries in a procedure regularly use atypical or temporary values, procedure performance can be improved by using the RECOMPILE query hint inside those queries.</span></span> <span data-ttu-id="32c54-128">전체 프로시저 대신 쿼리 힌트를 사용하는 쿼리만 다시 컴파일되므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 문 수준 재컴파일 동작이 모방됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-128">Since only the queries using the query hint will be recompiled instead of the complete procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]'s statement-level recompilation behavior is mimicked.</span></span> <span data-ttu-id="32c54-129">그러나 RECOMPILE 쿼리 힌트는 프로시저의 현재 매개 변수 값을 사용할 뿐만 아니라 문을 컴파일할 때 저장 프로시저에 있는 지역 변수의 값도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-129">But in addition to using the procedure's current parameter values, the RECOMPILE query hint also uses the values of any local variables inside the stored procedure when you compile the statement.</span></span> <span data-ttu-id="32c54-130">자세한 내용은 [쿼리 힌트(Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32c54-130">For more information, see [Query Hint (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="32c54-131">보안</span><span class="sxs-lookup"><span data-stu-id="32c54-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="32c54-132">권한</span><span class="sxs-lookup"><span data-stu-id="32c54-132">Permissions</span></span>  
 <span data-ttu-id="32c54-133">`WITH RECOMPILE`Option</span><span class="sxs-lookup"><span data-stu-id="32c54-133">`WITH RECOMPILE` Option</span></span>  
 <span data-ttu-id="32c54-134">프로시저 정의를 만들 때 이 옵션을 사용하는 경우 데이터베이스에서 CREATE PROCEDURE 권한과 프로시저를 만들고 있는 스키마에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-134">If this option is used when the procedure definition is created, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="32c54-135">EXECUTE 문에서 이 옵션을 사용하는 경우 프로시저에 대한 EXECUTE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-135">If this option is used in an EXECUTE statement, it requires EXECUTE permissions on the procedure.</span></span> <span data-ttu-id="32c54-136">EXECUTE 문 자체에 대한 권한은 필요하지 않지만 EXECUTE 문에서 참조되는 프로시저에 대한 실행 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-136">Permissions are not required on the EXECUTE statement itself but execute permissions are required on the procedure referenced in the EXECUTE statement.</span></span> <span data-ttu-id="32c54-137">자세한 내용은 [EXECUTE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="32c54-137">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
 <span data-ttu-id="32c54-138">`RECOMPILE`쿼리 힌트</span><span class="sxs-lookup"><span data-stu-id="32c54-138">`RECOMPILE` Query Hint</span></span>  
 <span data-ttu-id="32c54-139">이 기능은 프로시저를 만들고 프로시저의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 힌트를 포함할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-139">This feature is used when the procedure is created and the hint is included in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure.</span></span> <span data-ttu-id="32c54-140">따라서 데이터베이스에서 CREATE PROCEDURE 권한과 프로시저를 만들 스키마에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-140">Therefore, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="32c54-141">`sp_recompile`시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="32c54-141">`sp_recompile` System Stored Procedure</span></span>  
 <span data-ttu-id="32c54-142">지정된 프로시저에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-142">Requires ALTER permission on the specified procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="32c54-143">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="32c54-143">Using Transact-SQL</span></span>  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="32c54-144">WITH RECOMPILE 옵션을 사용하여 저장 프로시저를 다시 컴파일하려면</span><span class="sxs-lookup"><span data-stu-id="32c54-144">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="32c54-145">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-145">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="32c54-146">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-146">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="32c54-147">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="32c54-148">이 예에서는 프로시저 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-148">This example creates the procedure definition.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
    DROP PROCEDURE dbo.uspProductByVendor;  
GO  
CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
WITH RECOMPILE  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
    FROM Purchasing.Vendor AS v   
    JOIN Purchasing.ProductVendor AS pv   
      ON v.BusinessEntityID = pv.BusinessEntityID   
    JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID  
    WHERE v.Name LIKE @Name;  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="32c54-149">WITH RECOMPILE 옵션을 사용하여 저장 프로시저를 다시 컴파일하려면</span><span class="sxs-lookup"><span data-stu-id="32c54-149">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="32c54-150">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-150">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="32c54-151">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="32c54-152">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="32c54-153">이 예에서는 뷰에서 모든 직원(성과 이름 제공됨), 직함 및 부서 이름을 반환하는 간단한 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-153">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="32c54-154">그런 다음 두 번째 코드 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-154">And then copy and paste the second code example into the query window and click **Execute**.</span></span> <span data-ttu-id="32c54-155">프로시저가 실행되고 프로시저의 쿼리 계획이 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-155">This executes the procedure and recompiles the procedure's query plan.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE HumanResources.uspGetAllEmployees WITH RECOMPILE;  
GO  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-sp_recompile"></a><span data-ttu-id="32c54-156">sp_recompile을 사용하여 저장 프로시저를 다시 컴파일하려면</span><span class="sxs-lookup"><span data-stu-id="32c54-156">To recompile a stored procedure by using sp_recompile</span></span>  
  
1.  <span data-ttu-id="32c54-157">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-157">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="32c54-158">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="32c54-159">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-159">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="32c54-160">이 예에서는 뷰에서 모든 직원(성과 이름 제공됨), 직함 및 부서 이름을 반환하는 간단한 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-160">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="32c54-161">그런 다음 다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-161">Then, copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="32c54-162">프로시저가 실행되지는 않지만 다음에 프로시저가 실행될 때 쿼리 계획이 업데이트될 수 있게 프로시저가 다시 컴파일되도록 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="32c54-162">This does not execute the procedure but it does mark the procedure to be recompiled so that its query plan is updated the next time that the procedure is executed.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'HumanResources.uspGetAllEmployees';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="32c54-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32c54-163">See Also</span></span>  
 <span data-ttu-id="32c54-164">[저장 프로시저 만들기](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="32c54-164">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="32c54-165">[저장 프로시저 수정](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="32c54-165">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="32c54-166">[저장 프로시저 이름 바꾸기](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="32c54-166">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="32c54-167">[저장 프로시저의 정의 보기](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="32c54-167">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="32c54-168">[저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="32c54-168">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="32c54-169">DROP PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32c54-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
