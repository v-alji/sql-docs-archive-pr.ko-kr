---
title: 고유 하 게 컴파일된 저장 프로시저에서 지원 되는 구문 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: rothja
ms.author: jroth
ms.openlocfilehash: 65e6e794c5858a68c4b2a9b298513911b487cf52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660575"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a><span data-ttu-id="a38f4-102">고유하게 컴파일된 저장 프로시저에서 지원되는 구문</span><span class="sxs-lookup"><span data-stu-id="a38f4-102">Supported Constructs in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="a38f4-103">이 항목에는 고유 하 게 컴파일된 저장 프로시저에 대해 지원 되는 기능 목록이 포함 되어 있습니다 ([CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql)).</span><span class="sxs-lookup"><span data-stu-id="a38f4-103">This topic contains a list of supported features for natively compiled stored procedures ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):</span></span>  
  
-   [<span data-ttu-id="a38f4-104">고유하게 컴파일된 저장 프로시저의 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="a38f4-104">Programmability in Natively Compiled Stored Procedures</span></span>](#pncsp)  
  
-   [<span data-ttu-id="a38f4-105">지원 되는 연산자</span><span class="sxs-lookup"><span data-stu-id="a38f4-105">Supported Operators</span></span>](#so)  
  
-   [<span data-ttu-id="a38f4-106">고유하게 컴파일된 저장 프로시저의 기본 제공 함수</span><span class="sxs-lookup"><span data-stu-id="a38f4-106">Built-in Functions in Natively Compiled Stored Procedures</span></span>](#bfncsp)  
  
-   [<span data-ttu-id="a38f4-107">고유하게 컴파일된 저장 프로시저의 쿼리 노출 영역</span><span class="sxs-lookup"><span data-stu-id="a38f4-107">Query Surface Area in Natively Compiled Stored Procedures</span></span>](#qsancsp)  
  
-   [<span data-ttu-id="a38f4-108">감사</span><span class="sxs-lookup"><span data-stu-id="a38f4-108">Auditing</span></span>](#auditing)  
  
-   [<span data-ttu-id="a38f4-109">테이블, 쿼리 및 조인 힌트</span><span class="sxs-lookup"><span data-stu-id="a38f4-109">Table, Query, and Join Hints</span></span>](#tqh)  
  
-   [<span data-ttu-id="a38f4-110">정렬에 대 한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="a38f4-110">Limitations on Sorting</span></span>](#los)  
  
 <span data-ttu-id="a38f4-111">기본적으로 컴파일된 저장 프로시저에서 지원되는 데이터 형식에 대한 자세한 내용은 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-111">For information on data types supported in natively compiled stored procedures, see [Supported Data Types](supported-data-types-for-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="a38f4-112">고유하게 컴파일된 저장 프로시저에서 지원되지 않는 구문에 대한 자세한 내용과 지원되지 않는 일부 기능을 해결하는 방법은 [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-112">For complete information about unsupported constructs, and for information about how to work around some of the unsupported features in natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span> <span data-ttu-id="a38f4-113">지원되지 않는 기능에 대한 자세한 내용은 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-113">For more information about unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
##  <a name="programmability-in-natively-compiled-stored-procedures"></a><a name="pncsp"></a><span data-ttu-id="a38f4-114">고유 하 게 컴파일된 저장 프로시저의 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="a38f4-114">Programmability in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="a38f4-115">다음 항목이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-115">The following are supported:</span></span>  
  
-   <span data-ttu-id="a38f4-116">BEGIN ATOMIC(저장 프로시저의 외부 수준), LANGUAGE, ISOLATION LEVEL, DATEFORMAT 및 DATEFIRST</span><span class="sxs-lookup"><span data-stu-id="a38f4-116">BEGIN ATOMIC (at the outer level of the stored procedure), LANGUAGE, ISOLATION LEVEL, DATEFORMAT, and DATEFIRST.</span></span>  
  
-   <span data-ttu-id="a38f4-117">NULL 또는 NOT NULL로 변수 선언</span><span class="sxs-lookup"><span data-stu-id="a38f4-117">Declaring variables as NULL or NOT NULL.</span></span> <span data-ttu-id="a38f4-118">변수가 NOT NULL로 선언된 경우 선언에 이니셜라이저가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-118">If a variable is declared as NOT NULL, the declaration must have an initializer.</span></span> <span data-ttu-id="a38f4-119">변수가 NOT NULL로 선언되지 않은 경우 이니셜라이저는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-119">If a variable is not declared as NOT NULL, an initializer is optional.</span></span>  
  
-   <span data-ttu-id="a38f4-120">IF 및 WHILE</span><span class="sxs-lookup"><span data-stu-id="a38f4-120">IF and WHILE</span></span>  
  
-   <span data-ttu-id="a38f4-121">INSERT/UPDATE/DELETE</span><span class="sxs-lookup"><span data-stu-id="a38f4-121">INSERT/UPDATE/DELETE</span></span>  
  
     <span data-ttu-id="a38f4-122">하위 쿼리는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-122">Subqueries are not supported.</span></span> <span data-ttu-id="a38f4-123">WHERE 또는 HAVING 절에서 AND 및 BETWEEN은 지원되고, OR, NOT 및 IN은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-123">In the WHERE or HAVING clause, AND and BETWEEN are supported; OR, NOT, and IN are not supported.</span></span>  
  
-   <span data-ttu-id="a38f4-124">메모리 액세스에 최적화된 테이블 형식 및 테이블 변수</span><span class="sxs-lookup"><span data-stu-id="a38f4-124">Memory-optimized table types and table variables.</span></span>  
  
-   <span data-ttu-id="a38f4-125">RETURN</span><span class="sxs-lookup"><span data-stu-id="a38f4-125">RETURN</span></span>  
  
-   <span data-ttu-id="a38f4-126">선택</span><span class="sxs-lookup"><span data-stu-id="a38f4-126">SELECT</span></span>  
  
-   <span data-ttu-id="a38f4-127">SET</span><span class="sxs-lookup"><span data-stu-id="a38f4-127">SET</span></span>  
  
-   <span data-ttu-id="a38f4-128">TRY/CATCH/THROW</span><span class="sxs-lookup"><span data-stu-id="a38f4-128">TRY/CATCH/THROW</span></span>  
  
     <span data-ttu-id="a38f4-129">성능을 최적화하기 위해서는 전체 고유하게 컴파일된 저장 프로시저에 대해 단일 TRY/CATCH 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-129">To optimize performance, use a single TRY/CATCH block for an entire natively compiled stored procedure.</span></span>  
  
##  <a name="supported-operators"></a><a name="so"></a> <span data-ttu-id="a38f4-130">지원되는 연산자</span><span class="sxs-lookup"><span data-stu-id="a38f4-130">Supported Operators</span></span>  
 <span data-ttu-id="a38f4-131">지원되는 연산자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-131">The following operators are supported.</span></span>  
  
-   <span data-ttu-id="a38f4-132">[Transact-sql&#41;&#40;비교 연산자](/sql/t-sql/language-elements/comparison-operators-transact-sql) (예: >, \<, > = 및 <=)는 조건 (IF, WHILE)에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-132">[Comparison Operators &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comparison-operators-transact-sql) (for example, >, \<, >=, and <=) are supported in conditionals (IF, WHILE).</span></span>  
  
-   <span data-ttu-id="a38f4-133">단항 연산자(+, -).</span><span class="sxs-lookup"><span data-stu-id="a38f4-133">Unary operators (+, -).</span></span>  
  
-   <span data-ttu-id="a38f4-134">이항 연산자(\*, /, +, -, %(모듈로))</span><span class="sxs-lookup"><span data-stu-id="a38f4-134">Binary operators (\*, /, +, -, % (modulo)).</span></span>  
  
     <span data-ttu-id="a38f4-135">더하기 연산자(+)는 숫자 및 문자열에서 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-135">The plus operator (+) is supported on both numbers and strings.</span></span>  
  
-   <span data-ttu-id="a38f4-136">논리 연산자(AND, OR, NOT).</span><span class="sxs-lookup"><span data-stu-id="a38f4-136">Logical operators (AND, OR, NOT).</span></span> <span data-ttu-id="a38f4-137">OR 및 NOT은 IF 및 WHILE 문에서 지원되지만 WHERE 또는 HAVING 절에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-137">OR and NOT are supported in IF and WHILE statements but not in WHERE or HAVING clauses.</span></span>  
  
-   <span data-ttu-id="a38f4-138">비트 연산자 ~, &, | 및 ^</span><span class="sxs-lookup"><span data-stu-id="a38f4-138">Bitwise operators ~, &, |, and ^</span></span>  
  
##  <a name="built-in-functions-in-natively-compiled-stored-procedures"></a><a name="bfncsp"></a><span data-ttu-id="a38f4-139">고유 하 게 컴파일된 저장 프로시저의 기본 제공 함수</span><span class="sxs-lookup"><span data-stu-id="a38f4-139">Built-in Functions in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="a38f4-140">다음 함수는 메모리 최적화 테이블에 대한 기본 제약 조건과 고유하게 컴파일된 저장 프로시저에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-140">The following functions are supported in default constraints on memory-optimized tables and in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="a38f4-141">수식 함수: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE 및 TAN</span><span class="sxs-lookup"><span data-stu-id="a38f4-141">Math Functions: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE, and TAN</span></span>  
  
-   <span data-ttu-id="a38f4-142">날짜 함수: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME 및 YEAR.</span><span class="sxs-lookup"><span data-stu-id="a38f4-142">Date Functions: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME, and YEAR.</span></span>  
  
-   <span data-ttu-id="a38f4-143">문자열 함수: LEN, LTRIM, RTRIM 및 SUBSTRING</span><span class="sxs-lookup"><span data-stu-id="a38f4-143">String Functions: LEN, LTRIM, RTRIM, and SUBSTRING</span></span>  
  
-   <span data-ttu-id="a38f4-144">ID 함수: SCOPE_IDENTITY</span><span class="sxs-lookup"><span data-stu-id="a38f4-144">Identity Function: SCOPE_IDENTITY</span></span>  
  
-   <span data-ttu-id="a38f4-145">NULL 함수: ISNULL</span><span class="sxs-lookup"><span data-stu-id="a38f4-145">NULL functions: ISNULL</span></span>  
  
-   <span data-ttu-id="a38f4-146">Uniqueidentifier 함수: NEWID 및 NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="a38f4-146">Uniqueidentifier functions: NEWID and NEWSEQUENTIALID</span></span>  
  
-   <span data-ttu-id="a38f4-147">오류 함수: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY 및 ERROR_STATE</span><span class="sxs-lookup"><span data-stu-id="a38f4-147">Error Functions: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE</span></span>  
  
-   <span data-ttu-id="a38f4-148">변환: CAST 및 CONVERT.</span><span class="sxs-lookup"><span data-stu-id="a38f4-148">Conversions: CAST and CONVERT.</span></span> <span data-ttu-id="a38f4-149">유니코드 문자열과 유니코드가 아닌 문자열(n(var)char 및 (var)char) 간의 변환은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-149">Conversions between Unicode and non-Unicode character strings (n(var)char and (var)char) are not supported.</span></span>  
  
-   <span data-ttu-id="a38f4-150">시스템 함수: @@rowcount</span><span class="sxs-lookup"><span data-stu-id="a38f4-150">System Functions: @@rowcount.</span></span> <span data-ttu-id="a38f4-151">고유하게 컴파일된 저장 프로시저 내의 문은 @@rowcount를 업데이트합니다. 고유하게 컴파일된 저장 프로시저에서 @@rowcount를 사용하여 고유하게 컴파일된 저장 프로시저 내에서 실행된 마지막 문의 영향을 받는 행의 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-151">Statements inside natively compiled stored procedures update @@rowcount and you can use @@rowcount in a natively compiled stored procedure to determine the number of rows affected by the last statement executed within that natively compiled stored procedure.</span></span> <span data-ttu-id="a38f4-152">그러나 @@rowcount는 고유하게 컴파일된 저장 프로시저의 실행이 시작될 때와 끝날 때 0으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-152">However, @@rowcount is reset to 0 at the start and at the end of the execution of a natively compiled stored procedure.</span></span>  
  
##  <a name="query-surface-area-in-natively-compiled-stored-procedures"></a><a name="qsancsp"></a><span data-ttu-id="a38f4-153">고유 하 게 컴파일된 저장 프로시저의 쿼리 노출 영역</span><span class="sxs-lookup"><span data-stu-id="a38f4-153">Query Surface Area in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="a38f4-154">다음 항목이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-154">The following are supported:</span></span>  
  
-   <span data-ttu-id="a38f4-155">BETWEEN</span><span class="sxs-lookup"><span data-stu-id="a38f4-155">BETWEEN</span></span>  
  
-   <span data-ttu-id="a38f4-156">열 이름 별칭(AS 또는 = 구문 사용).</span><span class="sxs-lookup"><span data-stu-id="a38f4-156">Column name aliases (using either AS or = syntax).</span></span>  
  
-   <span data-ttu-id="a38f4-157">SELECT 쿼리에서만 지원되는 CROSS JOIN 및 INNER JOIN</span><span class="sxs-lookup"><span data-stu-id="a38f4-157">CROSS JOIN and INNER JOIN, supported only with SELECT queries.</span></span>  
  
-   <span data-ttu-id="a38f4-158">식이 지원 되는 연산자를 사용 하는 경우 SELECT 목록 및 [where &#40;transact-sql&#41;](/sql/t-sql/queries/where-transact-sql) 절에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-158">Expressions are supported in SELECT list and [WHERE &#40;Transact-SQL&#41;](/sql/t-sql/queries/where-transact-sql) clause if they use a supported operator.</span></span> <span data-ttu-id="a38f4-159">현재 지원되는 연산자의 목록은 [Supported Operators](#so) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-159">See [Supported Operators](#so) for the list of currently-supported operators.</span></span>  
  
-   <span data-ttu-id="a38f4-160">필터 조건자 IS [NOT] NULL</span><span class="sxs-lookup"><span data-stu-id="a38f4-160">Filter predicate IS [NOT] NULL</span></span>  
  
-   <span data-ttu-id="a38f4-161">FROM \<memory optimized table></span><span class="sxs-lookup"><span data-stu-id="a38f4-161">FROM \<memory optimized table></span></span>  
  
-   <span data-ttu-id="a38f4-162">AVG, COUNT, COUNT_BIG, MIN, MAX 및 SUM 집계 함수를 사용 하 [여 GROUP BY &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql) 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-162">[GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) is supported, along with the aggregate functions AVG, COUNT, COUNT_BIG, MIN, MAX, and SUM.</span></span> <span data-ttu-id="a38f4-163">MIN 및 MAX는 nvarchar, char, varchar, varchar, varbinary 및 binary 형식에 대해 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-163">MIN and MAX are not supported for types nvarchar, char, varchar, varchar, varbinary, and binary.</span></span> <span data-ttu-id="a38f4-164">Order by 목록의 식이 GROUP BY 목록에 표시 되는 경우에는 Order by 절을 사용 하 여 [order By 절](/sql/t-sql/queries/select-order-by-clause-transact-sql) 에서 [group By &#40;&#41;transact-sql](/sql/t-sql/queries/select-group-by-transact-sql)&#41;를 사용할 수 &#40;.</span><span class="sxs-lookup"><span data-stu-id="a38f4-164">[ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) is supported with [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) if an expression in the ORDER BY list appears verbatim in the GROUP BY list.</span></span> <span data-ttu-id="a38f4-165">예를 들어, GROUP BY a + b ORDER BY a + b는 지원되지만 GROUP BY a, b ORDER BY a + b는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-165">For example, GROUP BY a + b ORDER BY a + b is supported, but GROUP BY a, b ORDER BY a + b is not.</span></span>  
  
-   <span data-ttu-id="a38f4-166">HAVING(WHERE 절과 동일한 식 제한 사항이 적용됨)</span><span class="sxs-lookup"><span data-stu-id="a38f4-166">HAVING, subject to the same expression limitations as the WHERE clause.</span></span>  
  
-   <span data-ttu-id="a38f4-167">INSERT VALUES(문당 하나의 행) 및 INSERT SELECT</span><span class="sxs-lookup"><span data-stu-id="a38f4-167">INSERT VALUES (one row per statement) and INSERT SELECT</span></span>  
  
-   <span data-ttu-id="a38f4-168">정렬 기준 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a38f4-168">ORDER BY <sup>1</sup></span></span>  
  
-   <span data-ttu-id="a38f4-169">열을 참조하지 않는 조건자</span><span class="sxs-lookup"><span data-stu-id="a38f4-169">Predicates not referencing a column.</span></span>  
  
-   <span data-ttu-id="a38f4-170">SELECT, UPDATE 및 DELETE</span><span class="sxs-lookup"><span data-stu-id="a38f4-170">SELECT, UPDATE, and DELETE</span></span>  
  
-   <span data-ttu-id="a38f4-171">상위 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a38f4-171">TOP <sup>1</sup></span></span>  
  
-   <span data-ttu-id="a38f4-172">SELECT 목록의 변수 할당.</span><span class="sxs-lookup"><span data-stu-id="a38f4-172">Variable assignment in the SELECT list.</span></span>  
  
-   <span data-ttu-id="a38f4-173">위치 ... 하거나</span><span class="sxs-lookup"><span data-stu-id="a38f4-173">WHERE ... AND</span></span>  
  
 <span data-ttu-id="a38f4-174"><sup>1</sup> ORDER BY 및 TOP은 몇 가지 제한 사항이 있지만 고유 하 게 컴파일된 저장 프로시저에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-174"><sup>1</sup> ORDER BY and TOP are supported in natively compiled stored procedures, with some restrictions:</span></span>  
  
-   <span data-ttu-id="a38f4-175">`DISTINCT` 또는 `SELECT` 절에서는 `ORDER BY`가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-175">There is no support for `DISTINCT` in the `SELECT` or `ORDER BY` clause.</span></span>  
  
-   <span data-ttu-id="a38f4-176">`WITH TIES` 절에서는 `PERCENT` 또는 `TOP`가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-176">There is no support for `WITH TIES` or `PERCENT` in the `TOP` clause.</span></span>  
  
-   <span data-ttu-id="a38f4-177">`TOP` 절에서 상수를 사용할 때 `ORDER BY`과 `TOP`를 함께 사용할 경우 8,192개 이상은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-177">`TOP` combined with `ORDER BY` does not support more than 8,192 when using a constant in the `TOP` clause.</span></span> <span data-ttu-id="a38f4-178">쿼리에 조인 또는 집계 함수가 포함되어 있으면 이 제한이 더 낮아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-178">This limit may be lowered in case the query contains joins or aggregate functions.</span></span> <span data-ttu-id="a38f4-179">예를 들어, 조인이 하나 있고 테이블이 두 개 있으면 4,096개의 행으로 제한되고,</span><span class="sxs-lookup"><span data-stu-id="a38f4-179">(For example, with one join (two tables), the limit is 4,096 rows.</span></span> <span data-ttu-id="a38f4-180">조인이 두 개 있고 테이블이 세 개 있으면 2,730개의 행으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-180">With two joins (three tables), the limit is 2,730 rows.)</span></span>  
  
     <span data-ttu-id="a38f4-181">변수에 행 수를 저장하여 8,192개 이상의 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-181">You can obtain results greater than 8,192 by storing the number of rows in a variable:</span></span>  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 <span data-ttu-id="a38f4-182">하지만 `TOP` 절에 상수를 사용하면 변수를 사용할 때보다 나은 성능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-182">However, a constant in the `TOP` clause results in better performance compared to using a variable.</span></span>  
  
 <span data-ttu-id="a38f4-183">이러한 제한 사항은 메모리 최적화 테이블에 대한 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-183">These restrictions do not apply to interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access on memory-optimized tables.</span></span>  
  
##  <a name="auditing"></a><a name="auditing"></a> <span data-ttu-id="a38f4-184">감사</span><span class="sxs-lookup"><span data-stu-id="a38f4-184">Auditing</span></span>  
 <span data-ttu-id="a38f4-185">프로시저 수준 감사는 고유하게 컴파일된 저장 프로시저에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-185">Procedure level auditing is supported in natively compiled stored procedures.</span></span> <span data-ttu-id="a38f4-186">문 수준 감사는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-186">Statement level auditing is not supported.</span></span>  
  
 <span data-ttu-id="a38f4-187">감사에 대한 자세한 내용은 [서버 감사 및 데이터베이스 감사 사양 만들기](../security/auditing/create-a-server-audit-and-database-audit-specification.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-187">For more information about auditing, see [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md).</span></span>  
  
##  <a name="table-query-and-join-hints"></a><a name="tqh"></a><span data-ttu-id="a38f4-188">테이블, 쿼리 및 조인 힌트</span><span class="sxs-lookup"><span data-stu-id="a38f4-188">Table, Query, and Join Hints</span></span>  
 <span data-ttu-id="a38f4-189">다음 항목이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-189">The following are supported:</span></span>  
  
-   <span data-ttu-id="a38f4-190">테이블 힌트 구문 또는 쿼리의 [OPTION 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql)에 있는 INDEX, FORCESCAN 및 FORCESEEK 힌트.</span><span class="sxs-lookup"><span data-stu-id="a38f4-190">INDEX, FORCESCAN, and FORCESEEK hints, either in table hints syntax or in [OPTION Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) of the query.</span></span>  
  
-   <span data-ttu-id="a38f4-191">FORCE ORDER</span><span class="sxs-lookup"><span data-stu-id="a38f4-191">FORCE ORDER</span></span>  
  
-   <span data-ttu-id="a38f4-192">INNER LOOP JOIN</span><span class="sxs-lookup"><span data-stu-id="a38f4-192">INNER LOOP JOIN</span></span>  
  
-   <span data-ttu-id="a38f4-193">OPTIMIZE FOR</span><span class="sxs-lookup"><span data-stu-id="a38f4-193">OPTIMIZE FOR</span></span>  
  
 <span data-ttu-id="a38f4-194">자세한 내용은 [&#40;t-sql&#41;힌트 ](/sql/t-sql/queries/hints-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a38f4-194">For more information, see [Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).</span></span>  
  
##  <a name="limitations-on-sorting"></a><a name="los"></a> <span data-ttu-id="a38f4-195">정렬의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="a38f4-195">Limitations on Sorting</span></span>  
 <span data-ttu-id="a38f4-196">[TOP&#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 및 [ORDER BY 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)을 사용하는 쿼리에서는 8,000개 이상의 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-196">You can sort greater than 8,000 rows in a query that uses [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span> <span data-ttu-id="a38f4-197">하지만 [ORDER BY 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)이 없을 경우, [TOP&#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql)은 최대 8,000개까지만 행을 정렬할 수 있습니다. 조인이 있으면 이러한 행 수가 더 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-197">However, without [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) can sort up to 8,000 rows (fewer rows if there are joins).</span></span>  
  
 <span data-ttu-id="a38f4-198">쿼리에서 [TOP&#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 연산자와 [ORDER BY 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)을 모두 사용하는 경우 TOP 연산자에 대해 최대 8192행을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-198">If your query uses both the [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) operator and an [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), you can specify up to 8192 rows for the TOP operator.</span></span> <span data-ttu-id="a38f4-199">8192행보다 더 많이 지정하면 다음 오류 메시지가 나타납니다. **메시지 41398, 수준 16, 상태 1, 프로시저 *\<procedureName>* , 줄 *\<lineNumber>* TOP 연산자는 최대 8,192행을 반환할 수 있으며 *\<number>* 행이 요청되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="a38f4-199">If you specify more than 8192 rows you get the error message: **Msg 41398, Level 16, State 1, Procedure *\<procedureName>*, Line *\<lineNumber>* The TOP operator can return a maximum of 8192 rows; *\<number>* was requested.**</span></span>  
  
 <span data-ttu-id="a38f4-200">TOP 절을 사용하지 않는 경우 ORDER BY를 사용하여 몇 행이든 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-200">If you do not have a TOP clause, you can sort any number of rows with ORDER BY.</span></span>  
  
 <span data-ttu-id="a38f4-201">ORDER BY 절을 사용하지 않는 경우 TOP 연산자와 함께 어떤 정수 값이든 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-201">If you do not use an ORDER BY clause, you can use any integer value with the TOP operator.</span></span>  
  
 <span data-ttu-id="a38f4-202">TOP N = 8192의 예: 컴파일</span><span class="sxs-lookup"><span data-stu-id="a38f4-202">Example with TOP N = 8192: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="a38f4-203">TOP N > 8192의 예: 컴파일이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-203">Example with TOP N > 8192: Fails to compile.</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="a38f4-204">8192 행 제한은 `TOP N` 에만 적용됩니다. 여기서 `N` 은 앞의 예와 같이 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-204">The 8192 row limitation only applies to `TOP N` where `N` is a constant, as in the preceding examples.</span></span>  <span data-ttu-id="a38f4-205">8192보다 큰 `N` 이 필요한 경우 값을 변수에 할당하고 이 변수를 `TOP`과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-205">If you need `N` greater than 8192 you can assign the value to a variable and use that variable with `TOP`.</span></span>  
  
 <span data-ttu-id="a38f4-206">변수 사용 예: 컴파일</span><span class="sxs-lookup"><span data-stu-id="a38f4-206">Example using a variable: Compiles</span></span>  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 <span data-ttu-id="a38f4-207">**반환되는 행에 대한 제한:** 다음 두 경우에는 TOP 연산자가 반환할 수 있는 행 수를 잠재적으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-207">**Limitations on rows returned:** There are two cases where that can potentially reduce the number of rows that can be returned by the TOP operator:</span></span>  
  
-   <span data-ttu-id="a38f4-208">쿼리에서 JOIN 사용.</span><span class="sxs-lookup"><span data-stu-id="a38f4-208">Using JOINs in the query.</span></span>  <span data-ttu-id="a38f4-209">JOIN이 제한에 미치는 영향은 쿼리 계획에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-209">The influence of JOINs on the limitation depends on the query plan.</span></span>  
  
-   <span data-ttu-id="a38f4-210">집계 함수 또는 참조를 사용하여 ORDER BY 절에서 함수 집계.</span><span class="sxs-lookup"><span data-stu-id="a38f4-210">Using aggregate functions or references to aggregate functions in the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="a38f4-211">TOP N에서 지원되는 최대 N의 경우를 계산하는 공식은 `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`입니다.</span><span class="sxs-lookup"><span data-stu-id="a38f4-211">The formula to calculate a worst case maximum supported N in TOP N is: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38f4-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a38f4-212">See Also</span></span>  
 <span data-ttu-id="a38f4-213">[고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a38f4-213">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="a38f4-214">고유하게 컴파일된 저장 프로시저의 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="a38f4-214">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
