---
title: 사용자 정의 함수 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], components
- user-defined functions [SQL Server], about user-defined functions
ms.assetid: d7ddafab-f5a6-44b0-81d5-ba96425aada4
author: rothja
ms.author: jroth
ms.openlocfilehash: c7e4b1a77f2fe5a13e21d8b3fe59e37931669b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638600"
---
# <a name="user-defined-functions"></a><span data-ttu-id="4bf57-102">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-102">User-Defined Functions</span></span>
  <span data-ttu-id="4bf57-103">프로그래밍 언어의 함수처럼 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 정의 함수는 매개 변수를 받아들이고 복잡한 계산과 같은 동작을 수행하며 해당 작업의 결과를 값으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-103">Like functions in programming languages, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined functions are routines that accept parameters, perform an action, such as a complex calculation, and return the result of that action as a value.</span></span> <span data-ttu-id="4bf57-104">반환 값은 단일 스칼라 값이나 결과 집합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-104">The return value can either be a single scalar value or a result set.</span></span>  
  
 <span data-ttu-id="4bf57-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4bf57-105">**In This Topic**</span></span>  
  
 [<span data-ttu-id="4bf57-106">사용자 정의 함수의 이점</span><span class="sxs-lookup"><span data-stu-id="4bf57-106">User-defined Function Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="4bf57-107">함수 유형</span><span class="sxs-lookup"><span data-stu-id="4bf57-107">Types of Functions</span></span>](#FunctionTypes)  
  
 [<span data-ttu-id="4bf57-108">지침</span><span class="sxs-lookup"><span data-stu-id="4bf57-108">Guidelines</span></span>](#Guidelines)  
  
 [<span data-ttu-id="4bf57-109">함수의 유효한 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-109">Valid Statements in a Function</span></span>](#ValidStatements)  
  
 [<span data-ttu-id="4bf57-110">스키마 바운드 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-110">Schema Bound Functions</span></span>](#SchemaBound)  
  
 [<span data-ttu-id="4bf57-111">매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="4bf57-111">Specifying Parameters</span></span>](#Parameters)  
  
 [<span data-ttu-id="4bf57-112">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4bf57-112">Related Tasks</span></span>](#Tasks)  
  
##  <a name="user-defined-function-benefits"></a><a name="Benefits"></a><span data-ttu-id="4bf57-113">사용자 정의 함수 이점</span><span class="sxs-lookup"><span data-stu-id="4bf57-113">User-defined Function Benefits</span></span>  
 <span data-ttu-id="4bf57-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자 정의 함수를 사용하여 얻을 수 있는 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-114">The benefits of using user-defined functions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="4bf57-115">모듈식 프로그래밍을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-115">They allow modular programming.</span></span>  
  
     <span data-ttu-id="4bf57-116">함수를 한 번 만들어 데이터베이스에 저장한 후에는 프로그램에서 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-116">You can create the function once, store it in the database, and call it any number of times in your program.</span></span> <span data-ttu-id="4bf57-117">사용자 정의 함수는 프로그램 원본 코드에 관계없이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-117">User-defined functions can be modified independently of the program source code.</span></span>  
  
-   <span data-ttu-id="4bf57-118">작업을 더 빨리 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-118">They allow faster execution.</span></span>  
  
     <span data-ttu-id="4bf57-119">저장 프로시저와 마찬가지로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 사용자 정의 함수는 계획을 캐시하고 반복 실행에 다시 사용함으로써 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드의 컴파일 비용을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-119">Similar to stored procedures, [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions reduce the compilation cost of [!INCLUDE[tsql](../../includes/tsql-md.md)] code by caching the plans and reusing them for repeated executions.</span></span> <span data-ttu-id="4bf57-120">즉, 사용자 정의 함수를 매번 다시 구문 분석하고 최적화할 필요가 없기 때문에 더 빨리 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-120">This means the user-defined function does not need to be reparsed and reoptimized with each use resulting in much faster execution times.</span></span>  
  
     <span data-ttu-id="4bf57-121">CLR 함수는 계산 태스크, 문자열 조작 및 비즈니스 논리 면에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수보다 더 뛰어난 성공을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-121">CLR functions offer significant performance advantage over [!INCLUDE[tsql](../../includes/tsql-md.md)] functions for computational tasks, string manipulation, and business logic.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4bf57-122">함수는 데이터를 많이 액세스하는 논리에 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-122">functions are better suited for data-access intensive logic.</span></span>  
  
-   <span data-ttu-id="4bf57-123">네트워크 트래픽을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-123">They can reduce network traffic.</span></span>  
  
     <span data-ttu-id="4bf57-124">단일 스칼라 식으로 표현할 수 없는 일부 복잡한 제약 조건을 기반으로 데이터를 필터링하는 작업을 함수로 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-124">An operation that filters data based on some complex constraint that cannot be expressed in a single scalar expression can be expressed as a function.</span></span> <span data-ttu-id="4bf57-125">그런 다음 WHERE 절에서 이 함수를 호출하여 클라이언트에 전송되는 행 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-125">The function can then invoked in the WHERE clause to reduce the number or rows sent to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bf57-126">쿼리에 포함된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 사용자 정의 함수는 단일 스레드(직렬 실행 계획)에서만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions in queries can only be executed on a single thread (serial execution plan).</span></span>  
  
##  <a name="types-of-functions"></a><a name="FunctionTypes"></a><span data-ttu-id="4bf57-127">함수 유형</span><span class="sxs-lookup"><span data-stu-id="4bf57-127">Types of Functions</span></span>  
 <span data-ttu-id="4bf57-128">스칼라 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-128">Scalar Function</span></span>  
 <span data-ttu-id="4bf57-129">사용자 정의 스칼라 함수는 RETURNS 절에 정의된 유형의 단일 데이터 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-129">User-defined scalar functions return a single data value of the type defined in the RETURNS clause.</span></span> <span data-ttu-id="4bf57-130">인라인 스칼라 함수에는 함수 본문이 없으며 스칼라 값이 단일 문의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-130">For an inline scalar function, there is no function body; the scalar value is the result of a single statement.</span></span> <span data-ttu-id="4bf57-131">다중 문 스칼라 함수의 함수 본문은 BEGIN...END 블록으로 정의되며 여기에는 단일 값을 반환하는 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-131">For a multistatement scalar function, the function body, defined in a BEGIN...END block, contains a series of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that return the single value.</span></span> <span data-ttu-id="4bf57-132">반환 유형은 `text`, `ntext`, `image`, `cursor` 및 `timestamp`를 제외한 모든 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-132">The return type can be any data type except `text`, `ntext`, `image`, `cursor`, and `timestamp`.</span></span>  
  
 <span data-ttu-id="4bf57-133">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-133">Table-Valued Functions</span></span>  
 <span data-ttu-id="4bf57-134">사용자 정의 테이블 반환 함수는 `table` 데이터 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-134">User-defined table-valued functions return a `table` data type.</span></span> <span data-ttu-id="4bf57-135">인라인 테이블 반환 함수에는 함수 본문이 없으며 테이블이 단일 SELECT 문의 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-135">For an inline table-valued function, there is no function body; the table is the result set of a single SELECT statement.</span></span>  
  
 <span data-ttu-id="4bf57-136">시스템 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-136">System Functions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="4bf57-137">에서는 다양한 작업을 수행하는 데 사용되는 다양한 시스템 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-137">provides many system functions that you can use to perform a variety of operations.</span></span> <span data-ttu-id="4bf57-138">기본 제공 함수는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-138">They cannot be modified.</span></span> <span data-ttu-id="4bf57-139">자세한 내용은 [기본 제공 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/functions), [시스템 저장 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql) 및 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bf57-139">For more information, see [Built-in Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions), [System Stored Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql), and [Dynamic Management Views and Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).</span></span>  
  
##  <a name="guidelines"></a><a name="Guidelines"></a> <span data-ttu-id="4bf57-140">지침</span><span class="sxs-lookup"><span data-stu-id="4bf57-140">Guidelines</span></span>  
 <span data-ttu-id="4bf57-141">한 문을 취소하고 모듈(트리거, 저장 프로시저 등)의 다음 문을 실행하도록 하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 오류는 함수 내에서 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-141">[!INCLUDE[tsql](../../includes/tsql-md.md)] errors that cause a statement to be canceled and continue with the next statement in the module (such as triggers or stored procedures) are treated differently inside a function.</span></span> <span data-ttu-id="4bf57-142">함수에서 그러한 오류가 발생하면 함수의 실행이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-142">In functions, such errors cause the execution of the function to stop.</span></span> <span data-ttu-id="4bf57-143">이에 따라 함수를 호출한 문도 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-143">This in turn causes the statement that invoked the function to be canceled.</span></span>  
  
 <span data-ttu-id="4bf57-144">BEGIN...END 블록 내에 있는 문은 어떠한 부작용도 유발하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-144">The statements in a BEGIN...END block cannot have any side effects.</span></span> <span data-ttu-id="4bf57-145">함수의 부작용으로는 데이터베이스 테이블 수정과 같은 함수 외부 범위를 갖는 리소스 상태의 영구적인 변경을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-145">Function side effects are any permanent changes to the state of a resource that has a scope outside the function such as a modification to a database table.</span></span> <span data-ttu-id="4bf57-146">함수의 문에서 변경할 수 있는 것은 로컬 커서나 변수와 같은 함수의 로컬 개체뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-146">The only changes that can be made by the statements in the function are changes to objects local to the function, such as local cursors or variables.</span></span> <span data-ttu-id="4bf57-147">함수에서 수행할 수 없는 동작의 예로는 데이터베이스 테이블의 수정, 함수에서 로컬로 사용되지 않는 커서 작업, 전자 메일 보내기, 카탈로그 수정 시도 및 사용자에게 반환되는 결과 집합 생성 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-147">Modifications to database tables, operations on cursors that are not local to the function, sending e-mail, attempting a catalog modification, and generating a result set that is returned to the user are examples of actions that cannot be performed in a function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bf57-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 CREATE FUNCTION 문이 실행될 때 존재하지 않는 리소스에 대해 부작용이 생기는 경우에는 이 문을 실행하지만</span><span class="sxs-lookup"><span data-stu-id="4bf57-148">If a CREATE FUNCTION statement produces side effects against resources that do not exist when the CREATE FUNCTION statement is issued, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statement.</span></span> <span data-ttu-id="4bf57-149">이 문이 호출되는 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 이 함수가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-149">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not execute the function when it is invoked.</span></span>  
  
 <span data-ttu-id="4bf57-150">쿼리에 지정된 함수가 실제로 실행되는 횟수는 최적화 프로그램에서 작성한 실행 계획마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-150">The number of times that a function specified in a query is actually executed can vary between execution plans built by the optimizer.</span></span> <span data-ttu-id="4bf57-151">예를 들면 WHERE 절의 하위 쿼리에서 호출하는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-151">An example is a function invoked by a subquery in a WHERE clause.</span></span> <span data-ttu-id="4bf57-152">하위 쿼리 및 그 함수가 실행되는 횟수는 최적화 프로그램에서 선택한 액세스 경로에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-152">The number of times the subquery and its function is executed can vary with different access paths chosen by the optimizer.</span></span>  
  
##  <a name="valid-statements-in-a-function"></a><a name="ValidStatements"></a><span data-ttu-id="4bf57-153">함수의 유효한 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-153">Valid Statements in a Function</span></span>  
 <span data-ttu-id="4bf57-154">함수에서 사용할 수 있는 문의 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-154">The types of statements that are valid in a function include:</span></span>  
  
-   <span data-ttu-id="4bf57-155">함수에서 로컬로 사용되는 데이터 변수와 커서를 정의하는 데 사용되는 DECLARE 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-155">DECLARE statements can be used to define data variables and cursors that are local to the function.</span></span>  
  
-   <span data-ttu-id="4bf57-156">SET을 사용하여 스칼라 및 테이블 지역 변수에 값을 할당하는 것과 같이 함수의 로컬 개체에 값 할당</span><span class="sxs-lookup"><span data-stu-id="4bf57-156">Assignments of values to objects local to the function, such as using SET to assign values to scalar and table local variables.</span></span>  
  
-   <span data-ttu-id="4bf57-157">함수에서 커서 선언, 열기, 닫기, 할당 취소 등 로컬 커서를 참조하는 커서 작업.</span><span class="sxs-lookup"><span data-stu-id="4bf57-157">Cursor operations that reference local cursors that are declared, opened, closed, and deallocated in the function.</span></span> <span data-ttu-id="4bf57-158">클라이언트에 데이터를 반환하는 FETCH 문은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-158">FETCH statements that return data to the client are not allowed.</span></span> <span data-ttu-id="4bf57-159">INTO 절을 사용하여 지역 변수에 값을 할당하는 FETCH 문만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-159">Only FETCH statements that assign values to local variables using the INTO clause are allowed.</span></span>  
  
-   <span data-ttu-id="4bf57-160">TRY...CATCH 문을 제외한 흐름 제어 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-160">Control-of-flow statements except TRY...CATCH statements.</span></span>  
  
-   <span data-ttu-id="4bf57-161">함수에서 로컬로 사용되는 변수에 값을 할당하는 식이 있는 선택 목록이 포함된 SELECT 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-161">SELECT statements containing select lists with expressions that assign values to variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="4bf57-162">함수에서 로컬로 사용되는 테이블 변수를 수정하는 UPDATE, INSERT 및 DELETE 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-162">UPDATE, INSERT, and DELETE statements modifying table variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="4bf57-163">확장 저장 프로시저를 호출하는 EXECUTE 문</span><span class="sxs-lookup"><span data-stu-id="4bf57-163">EXECUTE statements calling an extended stored procedure.</span></span>  
  
### <a name="built-in-system-functions"></a><span data-ttu-id="4bf57-164">기본 제공 시스템 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-164">Built-in System Functions</span></span>  
 <span data-ttu-id="4bf57-165">다음과 같은 비결정적 기본 제공 함수는 Transact-SQL 사용자 정의 함수에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-165">The following nondeterministic built-in functions can be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bf57-166">CURRENT_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4bf57-166">CURRENT_TIMESTAMP</span></span>|<span data-ttu-id="4bf57-167">@@MAX_CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="4bf57-167">@@MAX_CONNECTIONS</span></span>|  
|<span data-ttu-id="4bf57-168">GET_TRANSMISSION_STATUS</span><span class="sxs-lookup"><span data-stu-id="4bf57-168">GET_TRANSMISSION_STATUS</span></span>|<span data-ttu-id="4bf57-169">@@PACK_RECEIVED</span><span class="sxs-lookup"><span data-stu-id="4bf57-169">@@PACK_RECEIVED</span></span>|  
|<span data-ttu-id="4bf57-170">GETDATE</span><span class="sxs-lookup"><span data-stu-id="4bf57-170">GETDATE</span></span>|<span data-ttu-id="4bf57-171">@@PACK_SENT</span><span class="sxs-lookup"><span data-stu-id="4bf57-171">@@PACK_SENT</span></span>|  
|<span data-ttu-id="4bf57-172">GETUTCDATE</span><span class="sxs-lookup"><span data-stu-id="4bf57-172">GETUTCDATE</span></span>|<span data-ttu-id="4bf57-173">@@PACKET_ERRORS</span><span class="sxs-lookup"><span data-stu-id="4bf57-173">@@PACKET_ERRORS</span></span>|  
|<span data-ttu-id="4bf57-174">@@CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="4bf57-174">@@CONNECTIONS</span></span>|<span data-ttu-id="4bf57-175">@@TIMETICKS</span><span class="sxs-lookup"><span data-stu-id="4bf57-175">@@TIMETICKS</span></span>|  
|<span data-ttu-id="4bf57-176">@@CPU_BUSY</span><span class="sxs-lookup"><span data-stu-id="4bf57-176">@@CPU_BUSY</span></span>|<span data-ttu-id="4bf57-177">@@TOTAL_ERRORS</span><span class="sxs-lookup"><span data-stu-id="4bf57-177">@@TOTAL_ERRORS</span></span>|  
|<span data-ttu-id="4bf57-178">@@DBTS</span><span class="sxs-lookup"><span data-stu-id="4bf57-178">@@DBTS</span></span>|<span data-ttu-id="4bf57-179">@@TOTAL_READ</span><span class="sxs-lookup"><span data-stu-id="4bf57-179">@@TOTAL_READ</span></span>|  
|<span data-ttu-id="4bf57-180">@@IDLE</span><span class="sxs-lookup"><span data-stu-id="4bf57-180">@@IDLE</span></span>|<span data-ttu-id="4bf57-181">@@TOTAL_WRITE</span><span class="sxs-lookup"><span data-stu-id="4bf57-181">@@TOTAL_WRITE</span></span>|  
|<span data-ttu-id="4bf57-182">@@IO_BUSY</span><span class="sxs-lookup"><span data-stu-id="4bf57-182">@@IO_BUSY</span></span>||  
  
 <span data-ttu-id="4bf57-183">다음과 같은 비결정적 기본 제공 함수는 Transact-SQL 사용자 정의 함수에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-183">The following nondeterministic built-in functions cannot be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bf57-184">NEWID</span><span class="sxs-lookup"><span data-stu-id="4bf57-184">NEWID</span></span>|<span data-ttu-id="4bf57-185">RAND</span><span class="sxs-lookup"><span data-stu-id="4bf57-185">RAND</span></span>|  
|<span data-ttu-id="4bf57-186">NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="4bf57-186">NEWSEQUENTIALID</span></span>|<span data-ttu-id="4bf57-187">TEXTPTR</span><span class="sxs-lookup"><span data-stu-id="4bf57-187">TEXTPTR</span></span>|  
  
 <span data-ttu-id="4bf57-188">결정적 및 비결정적 기본 제공 시스템 함수 목록은 [결정적 함수 및 비결정적 함수](../user-defined-functions/deterministic-and-nondeterministic-functions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bf57-188">For a list of deterministic and nondeterministic built-in system functions, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span>  
  
##  <a name="schema-bound-functions"></a><a name="SchemaBound"></a><span data-ttu-id="4bf57-189">스키마 바운드 함수</span><span class="sxs-lookup"><span data-stu-id="4bf57-189">Schema-Bound Functions</span></span>  
 <span data-ttu-id="4bf57-190">CREATE FUNCTION에서는 테이블, 뷰, 다른 사용자 정의 함수와 같은 참조하는 개체의 스키마에 함수를 바인드하는 SCHEMABINDING 절을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-190">CREATE FUNCTION supports a SCHEMABINDING clause that binds the function to the schema of any objects it references, such as tables, views, and other user-defined functions.</span></span> <span data-ttu-id="4bf57-191">스키마 바운드 함수에서 참조하는 개체는 변경하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-191">An attempt to alter or drop any object referenced by a schema-bound function fails.</span></span>  
  
 <span data-ttu-id="4bf57-192">CREATE FUNCTION에서 SCHEMABINDING 절을 지정하려면 먼저 다음 조건이 만족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-192">These conditions must be met before you can specify SCHEMABINDING in CREATE FUNCTION:</span></span>  
  
-   <span data-ttu-id="4bf57-193">함수에서 참조하는 모든 뷰와 사용자 정의 함수도 스키마 바운드이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-193">All views and user-defined functions referenced by the function must be schema-bound.</span></span>  
  
-   <span data-ttu-id="4bf57-194">함수에서 참조하는 모든 개체가 함수와 같은 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-194">All objects referenced by the function must be in the same database as the function.</span></span> <span data-ttu-id="4bf57-195">개체는 한 부분 또는 두 부분으로 된 이름을 사용하여 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-195">The objects must be referenced using either one-part or two-part names.</span></span>  
  
-   <span data-ttu-id="4bf57-196">함수에서 참조하는 모든 개체(테이블, 뷰, 사용자 정의 함수)에 대해 REFERENCES 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-196">You must have REFERENCES permission on all objects (tables, views, and user-defined functions) referenced in the function.</span></span>  
  
 <span data-ttu-id="4bf57-197">ALTER FUNCTION을 사용하여 스키마 바인딩을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-197">You can use ALTER FUNCTION to remove the schema binding.</span></span> <span data-ttu-id="4bf57-198">ALTER FUNCTION 문에서 WITH SCHEMABINDING 절 없이 함수를 다시 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-198">The ALTER FUNCTION statement should redefine the function without specifying WITH SCHEMABINDING.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="4bf57-199">매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="4bf57-199">Specifying Parameters</span></span>  
 <span data-ttu-id="4bf57-200">사용자 정의 함수에서는 0이나 더 많은 입력 매개 변수를 사용하고 스칼라 값 또는 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-200">A user-defined function takes zero or more input parameters and returns either a scalar value or a table.</span></span> <span data-ttu-id="4bf57-201">하나의 함수에 최대 1024개의 입력 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-201">A function can have a maximum of 1024 input parameters.</span></span> <span data-ttu-id="4bf57-202">함수의 매개 변수에 기본값이 지정되면 기본값을 가져오는 함수를 호출할 때 DEFAULT 키워드를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-202">When a parameter of the function has a default value, the keyword DEFAULT must be specified when calling the function to get the default value.</span></span> <span data-ttu-id="4bf57-203">이 동작은 매개 변수 생략이 기본값을 의미하기도 하는 사용자 정의 저장 프로시저의 기본값이 있는 매개 변수와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-203">This behavior is different from parameters with default values in user-defined stored procedures in which omitting the parameter also implies the default value.</span></span> <span data-ttu-id="4bf57-204">사용자 정의 함수는 출력 매개 변수를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-204">User-defined functions do not support output parameters.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="4bf57-205">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4bf57-205">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bf57-206">**태스크 설명**</span><span class="sxs-lookup"><span data-stu-id="4bf57-206">**Task Description**</span></span>|<span data-ttu-id="4bf57-207">**항목**</span><span class="sxs-lookup"><span data-stu-id="4bf57-207">**Topic**</span></span>|  
|<span data-ttu-id="4bf57-208">Transact-SQL 사용자 정의 함수를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-208">Describes how to create a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="4bf57-209">사용자 정의 함수 만들기&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="4bf57-209">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)|  
|<span data-ttu-id="4bf57-210">CLR 함수를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-210">Describes how create a CLR function.</span></span>|[<span data-ttu-id="4bf57-211">CLR 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="4bf57-211">Create CLR Functions</span></span>](../user-defined-functions/create-clr-functions.md)|  
|<span data-ttu-id="4bf57-212">사용자 정의 집계 함수를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-212">Describes how to create a user-defined aggregate function</span></span>|[<span data-ttu-id="4bf57-213">사용자 정의 집계 만들기</span><span class="sxs-lookup"><span data-stu-id="4bf57-213">Create User-defined Aggregates</span></span>](../user-defined-functions/create-user-defined-aggregates.md)|  
|<span data-ttu-id="4bf57-214">Transact-SQL 사용자 정의 함수를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-214">Describes how to modify a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="4bf57-215">사용자 정의 함수 수정</span><span class="sxs-lookup"><span data-stu-id="4bf57-215">Modify User-defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)|  
|<span data-ttu-id="4bf57-216">사용자 정의 함수를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-216">Describes how to delete a user-defined function.</span></span>|[<span data-ttu-id="4bf57-217">사용자 정의 함수 삭제</span><span class="sxs-lookup"><span data-stu-id="4bf57-217">Delete User-defined Functions</span></span>](../user-defined-functions/delete-user-defined-functions.md)|  
|<span data-ttu-id="4bf57-218">사용자 정의 함수를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-218">Describes how to execute a user-defined function.</span></span>|[<span data-ttu-id="4bf57-219">사용자 정의 함수 실행</span><span class="sxs-lookup"><span data-stu-id="4bf57-219">Execute User-defined Functions</span></span>](../user-defined-functions/execute-user-defined-functions.md)|  
|<span data-ttu-id="4bf57-220">사용자 정의 함수의 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-220">Describes how to rename a user-defined function</span></span>|[<span data-ttu-id="4bf57-221">사용자 정의 함수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="4bf57-221">Rename User-defined Functions</span></span>](../user-defined-functions/rename-user-defined-functions.md)|  
|<span data-ttu-id="4bf57-222">사용자 정의 함수의 정의를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bf57-222">Describes how to view the definition of a user-defined function.</span></span>|[<span data-ttu-id="4bf57-223">사용자 정의 함수 보기</span><span class="sxs-lookup"><span data-stu-id="4bf57-223">View User-defined Functions</span></span>](view-user-defined-functions.md)|  
  
  
