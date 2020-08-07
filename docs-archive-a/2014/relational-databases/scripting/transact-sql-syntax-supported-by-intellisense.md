---
title: IntelliSense에서 지원되는 Transact-SQL 구문
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL IntelliSense
- IntelliSense [SQL Server], Transact-SQL syntax
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d34fc79dd7817e64b34b61083415477860ce97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733835"
---
# <a name="transact-sql-syntax-supported-by-intellisense"></a><span data-ttu-id="6e957-102">IntelliSense에서 지원되는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-102">Transact-SQL Syntax Supported by IntelliSense</span></span>
  <span data-ttu-id="6e957-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 의 IntelliSense에서 지원하는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]문 및 구문 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-103">This topic describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and syntax elements that are supported by IntelliSense in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="statements-supported-by-intellisense"></a><span data-ttu-id="6e957-104">IntelliSense에서 지원하는 문</span><span class="sxs-lookup"><span data-stu-id="6e957-104">Statements Supported by IntelliSense</span></span>  
 <span data-ttu-id="6e957-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 IntelliSense는 가장 일반적으로 사용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-105">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], IntelliSense supports only the most commonly used [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="6e957-106">일부 일반적인 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기 조건으로 인해 IntelliSense가 제대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-106">Some general [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor conditions might prevent IntelliSense from functioning.</span></span> <span data-ttu-id="6e957-107">자세한 내용은 [IntelliSense 문제 해결&#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e957-107">For more information, see [Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e957-108">암호화된 저장 프로시저 또는 사용자 정의 함수와 같이 암호화된 데이터베이스 개체에 대해 IntelliSense를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-108">IntelliSense is not available for encrypted database objects, such as encrypted stored procedures or user-defined functions.</span></span> <span data-ttu-id="6e957-109">확장 저장 프로시저 및 CLR 통합 사용자 정의 유형의 매개 변수에 대해 매개 변수 도움말 및 요약 정보를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-109">Parameter help and Quick Info are not available for the parameters of extended stored procedures and CLR Integration user-defined types.</span></span>  
  
### <a name="select-statement"></a><span data-ttu-id="6e957-110">SELECT 문</span><span class="sxs-lookup"><span data-stu-id="6e957-110">SELECT Statement</span></span>  
 <span data-ttu-id="6e957-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서는 SELECT 문의 다음 구문 요소에 대한 IntelliSense 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor provides IntelliSense support for the following syntax elements in the SELECT statement:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e957-112">SELECT</span><span class="sxs-lookup"><span data-stu-id="6e957-112">SELECT</span></span>|<span data-ttu-id="6e957-113">WHERE</span><span class="sxs-lookup"><span data-stu-id="6e957-113">WHERE</span></span>|  
|<span data-ttu-id="6e957-114">FROM</span><span class="sxs-lookup"><span data-stu-id="6e957-114">FROM</span></span>|<span data-ttu-id="6e957-115">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="6e957-115">ORDER BY</span></span>|  
|<span data-ttu-id="6e957-116">HAVING</span><span class="sxs-lookup"><span data-stu-id="6e957-116">HAVING</span></span>|<span data-ttu-id="6e957-117">UNION</span><span class="sxs-lookup"><span data-stu-id="6e957-117">UNION</span></span>|  
|<span data-ttu-id="6e957-118">FOR</span><span class="sxs-lookup"><span data-stu-id="6e957-118">FOR</span></span>|<span data-ttu-id="6e957-119">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="6e957-119">GROUP BY</span></span>|  
|<span data-ttu-id="6e957-120">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="6e957-120">TOP</span></span>|<span data-ttu-id="6e957-121">OPTION (hint)</span><span class="sxs-lookup"><span data-stu-id="6e957-121">OPTION (hint)</span></span>|  
  
### <a name="additional-transact-sql-statements-that-are-supported"></a><span data-ttu-id="6e957-122">지원되는 추가 Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="6e957-122">Additional Transact-SQL Statements That Are Supported</span></span>  
 <span data-ttu-id="6e957-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서는 다음 표에 표시된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 대한 IntelliSense 지원도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-123">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor also provides IntelliSense support for [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are shown in the following table.</span></span>  
  
|<span data-ttu-id="6e957-124">Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="6e957-124">Transact-SQL statement</span></span>|<span data-ttu-id="6e957-125">지원되는 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-125">Syntax supported</span></span>|  
|-----------------------------|----------------------|  
|[<span data-ttu-id="6e957-126">INSERT</span><span class="sxs-lookup"><span data-stu-id="6e957-126">INSERT</span></span>](/sql/t-sql/statements/insert-transact-sql)|<span data-ttu-id="6e957-127">*execute_statement* 절을 제외한 모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-127">All syntax, except the *execute_statement* clause.</span></span>|  
|[<span data-ttu-id="6e957-128">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6e957-128">UPDATE</span></span>](/sql/t-sql/queries/update-transact-sql)|<span data-ttu-id="6e957-129">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-129">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-130">DELETE</span><span class="sxs-lookup"><span data-stu-id="6e957-130">DELETE</span></span>](/sql/t-sql/statements/delete-transact-sql)|<span data-ttu-id="6e957-131">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-131">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-132">있다고@local_variable</span><span class="sxs-lookup"><span data-stu-id="6e957-132">DECLARE @local_variable</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)|<span data-ttu-id="6e957-133">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-133">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-134">설정@local_variable</span><span class="sxs-lookup"><span data-stu-id="6e957-134">SET @local_variable</span></span>](/sql/t-sql/language-elements/set-local-variable-transact-sql)|<span data-ttu-id="6e957-135">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-135">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-136">실행할</span><span class="sxs-lookup"><span data-stu-id="6e957-136">EXECUTE</span></span>](/sql/t-sql/language-elements/execute-transact-sql)|<span data-ttu-id="6e957-137">사용자 정의 저장 프로시저, 시스템 저장 프로시저, 사용자 정의 함수 및 시스템 함수 실행</span><span class="sxs-lookup"><span data-stu-id="6e957-137">Execution of user-defined stored procedures, system stored procedures, user-defined functions, and system functions.</span></span>|  
|[<span data-ttu-id="6e957-138">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="6e957-138">CREATE TABLE</span></span>](/sql/t-sql/statements/create-table-transact-sql)|<span data-ttu-id="6e957-139">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-139">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-140">CREATE VIEW</span><span class="sxs-lookup"><span data-stu-id="6e957-140">CREATE VIEW</span></span>](/sql/t-sql/statements/create-view-transact-sql)|<span data-ttu-id="6e957-141">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-141">All syntax.</span></span>|  
|[<span data-ttu-id="6e957-142">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="6e957-142">CREATE PROCEDURE</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)|<span data-ttu-id="6e957-143">모든 구문. 단, 다음 항목은 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-143">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="6e957-144">EXTERNAL NAME 절에 대한 IntelliSense 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-144">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="6e957-145">AS 절에서 IntelliSense는 이 항목에 나열된 문과 구문만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-145">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="6e957-146">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="6e957-146">ALTER PROCEDURE</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)|<span data-ttu-id="6e957-147">모든 구문. 단, 다음 항목은 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-147">All syntax, with the following exceptions:</span></span><br /><br /> <span data-ttu-id="6e957-148">EXTERNAL NAME 절에 대한 IntelliSense 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-148">There is no IntelliSense support for the EXTERNAL NAME clause.</span></span><br /><br /> <span data-ttu-id="6e957-149">AS 절에서 IntelliSense는 이 항목에 나열된 문과 구문만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-149">In the AS clause, IntelliSense supports only the statements and syntax that are listed in this topic.</span></span>|  
|[<span data-ttu-id="6e957-150">사용</span><span class="sxs-lookup"><span data-stu-id="6e957-150">USE</span></span>](/sql/t-sql/language-elements/use-transact-sql)|<span data-ttu-id="6e957-151">모든 구문</span><span class="sxs-lookup"><span data-stu-id="6e957-151">All syntax.</span></span>|  
  
## <a name="intellisense-in-supported-statements"></a><span data-ttu-id="6e957-152">지원되는 문의 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="6e957-152">IntelliSense in Supported Statements</span></span>  
 <span data-ttu-id="6e957-153">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 IntelliSense는 지원되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 중 하나에서 사용되는 경우 다음 구문 요소를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-153">IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following syntax elements when they are used in one of the supported [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
-   <span data-ttu-id="6e957-154">APPLY를 비롯한 모든 조인 유형</span><span class="sxs-lookup"><span data-stu-id="6e957-154">All join types, including APPLY</span></span>  
  
-   <span data-ttu-id="6e957-155">PIVOT 및 UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="6e957-155">PIVOT and UNPIVOT</span></span>  
  
-   <span data-ttu-id="6e957-156">다음 데이터베이스 개체에 대한 참조</span><span class="sxs-lookup"><span data-stu-id="6e957-156">References to the following database objects:</span></span>  
  
    -   <span data-ttu-id="6e957-157">데이터베이스 및 스키마</span><span class="sxs-lookup"><span data-stu-id="6e957-157">Databases and schemas</span></span>  
  
    -   <span data-ttu-id="6e957-158">테이블, 뷰, 테이블 반환 함수 및 테이블 식</span><span class="sxs-lookup"><span data-stu-id="6e957-158">Tables, views, table-valued functions, and table expressions</span></span>  
  
    -   <span data-ttu-id="6e957-159">열</span><span class="sxs-lookup"><span data-stu-id="6e957-159">Columns</span></span>  
  
    -   <span data-ttu-id="6e957-160">프로시저 및 프로시저 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6e957-160">Procedures and procedure parameters</span></span>  
  
    -   <span data-ttu-id="6e957-161">스칼라 함수 및 스칼라 식</span><span class="sxs-lookup"><span data-stu-id="6e957-161">Scalar functions and scalar expressions</span></span>  
  
    -   <span data-ttu-id="6e957-162">로컬 변수</span><span class="sxs-lookup"><span data-stu-id="6e957-162">Local variables</span></span>  
  
    -   <span data-ttu-id="6e957-163">CTE(공통 테이블 식)</span><span class="sxs-lookup"><span data-stu-id="6e957-163">Common table expressions (CTE)</span></span>  
  
-   <span data-ttu-id="6e957-164">스크립트나 일괄 처리에 있는 CREATE 또는 ALTER 문에서만 참조되지만 스크립트나 일괄 처리를 아직 실행하지 않았기 때문에 데이터베이스에 없는 데이터베이스 개체.</span><span class="sxs-lookup"><span data-stu-id="6e957-164">Database objects that are referenced only in CREATE or ALTER statements in the script or batch, but which do not exist in the database because the script or batch has not yet been run.</span></span> <span data-ttu-id="6e957-165">이러한 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-165">These objects are as follows:</span></span>  
  
    -   <span data-ttu-id="6e957-166">스크립트나 일괄 처리에 있는 CREATE TABLE 또는 CREATE PROCEDURE 문에서 지정한 테이블 및 프로시저</span><span class="sxs-lookup"><span data-stu-id="6e957-166">Tables and procedures that have been specified in a CREATE TABLE or CREATE PROCEDURE statement in the script or batch.</span></span>  
  
    -   <span data-ttu-id="6e957-167">스크립트나 일괄 처리에 있는 ALTER TABLE 또는 ALTER PROCEDURE 문에서 지정한 테이블 및 프로시저에 대한 변경 내용</span><span class="sxs-lookup"><span data-stu-id="6e957-167">Changes to tables and procedures that have been specified in an ALTER TABLE or ALTER PROCEDURE statement in the script or batch.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e957-168">CREATE VIEW 문을 실행할 때까지 CREATE VIEW 문의 열에 대해 IntelliSense를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-168">IntelliSense is not available for the columns of a CREATE VIEW statement until the CREATE VIEW statement has been executed.</span></span>  
  
 <span data-ttu-id="6e957-169">앞에서 나열된 요소가 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 사용되는 경우에는 IntelliSense가 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-169">IntelliSense is not provided for the previously listed elements when they are used in other [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="6e957-170">예를 들어 SELECT 문에서 사용되는 열 이름에 대해서는 IntelliSense가 지원되지만 CREATE FUNCTION 문에서 사용되는 열에 대해서는 IntelliSense가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-170">For example, there is IntelliSense support for column names that are used in a SELECT statement, but not for columns that are used in the CREATE FUNCTION statement.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6e957-171">예제</span><span class="sxs-lookup"><span data-stu-id="6e957-171">Examples</span></span>  
 <span data-ttu-id="6e957-172">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트나 일괄 처리 내에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기의 IntelliSense는 이 항목에 나열된 문과 구문만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-172">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports only the statements and syntax that are listed in this topic.</span></span> <span data-ttu-id="6e957-173">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 예제에서는 IntelliSense에서 지원하는 문 및 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code examples show what statements and syntax elements IntelliSense supports.</span></span> <span data-ttu-id="6e957-174">예를 들어 다음 일괄 처리에서 IntelliSense는 `SELECT` 가 `SELECT` 문에 포함되어 있지 않고 자체적으로 코딩된 경우 `CREATE FUNCTION` 문에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-174">For example, in the following batch, IntelliSense is available for the `SELECT` statement when it is coded by itself, but not when the `SELECT` is contained in a `CREATE FUNCTION` statement.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 <span data-ttu-id="6e957-175">이 기능은 CREATE PROCEDURE 또는 ALTER PROCEDURE 문의 AS 절에 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 집합에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-175">This functionality also applies to the sets of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the AS clause of a CREATE PROCEDURE or ALTER PROCEDURE statement.</span></span>  
  
 <span data-ttu-id="6e957-176">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트나 일괄 처리 내에서 IntelliSense는 CREATE 또는 ALTER 문에서 지정했지만 문을 실행하지 않았기 때문에 데이터베이스에 없는 개체를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-176">Within a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or batch, IntelliSense supports objects that have been specified in a CREATE or ALTER statement; however, these objects do not exist in the database because the statements have not been executed.</span></span> <span data-ttu-id="6e957-177">예를 들어 쿼리 편집기에 다음과 같은 코드를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-177">For example, you might enter the following code in the Query Editor:</span></span>  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 <span data-ttu-id="6e957-178">`SELECT`를 입력하면 스크립트를 실행하지 않아 **이**에 아직 없더라도 IntelliSense는 SELECT 목록에 **PrimaryKeyCol**, **FirstNameCol** 및 `MyTable` LastNameCol `MyTestDB`을 사용 가능한 요소로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6e957-178">After you type `SELECT`, IntelliSense lists **PrimaryKeyCol**, **FirstNameCol**, and **LastNameCol** as possible elements in the select list, even if the script has not been executed and `MyTable` does not yet exist in `MyTestDB`.</span></span>  
  
  
