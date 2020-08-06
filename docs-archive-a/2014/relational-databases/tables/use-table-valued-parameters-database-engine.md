---
title: 테이블 반환 매개 변수 사용(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- DECLARE
- CREATE TYPE
helpviewer_keywords:
- table-valued parameters
- table-valued parameters, about table-valued parameters
- parameters [SQL Server], table-valued
- TVP See table-valued parameters
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa7013fddc6b2ce12ad9ad0f9fcb511d93915e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650858"
---
# <a name="use-table-valued-parameters-database-engine"></a><span data-ttu-id="a6892-102">테이블 반환 매개 변수 사용(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="a6892-102">Use Table-Valued Parameters (Database Engine)</span></span>
  <span data-ttu-id="a6892-103">테이블 반환 매개 변수는 사용자 정의 테이블 형식을 사용하여 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-103">Table-valued parameters are declared by using user-defined table types.</span></span> <span data-ttu-id="a6892-104">테이블 반환 매개 변수를 사용하면 임시 테이블이나 많은 매개 변수를 만들지 않고도 저장 프로시저 또는 함수와 같은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이나 루틴에 여러 행의 데이터를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-104">You can use table-valued parameters to send multiple rows of data to a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a routine, such as a stored procedure or function, without creating a temporary table or many parameters.</span></span>  
  
 <span data-ttu-id="a6892-105">테이블 반환 매개 변수는 OLE DB 및 ODBC의 매개 변수 배열과 유사하지만 보다 유연하고 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 보다 긴밀하게 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-105">Table-valued parameters are like parameter arrays in OLE DB and ODBC, but offer more flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a6892-106">또한 테이블 반환 매개 변수는 집합 기반 작업에 사용할 수 있다는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-106">Table-valued parameters also have the benefit of being able to participate in set-based operations.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a6892-107">은 입력 데이터의 복사본을 만들지 않기 위해 참조로 루틴에 테이블 반환 매개 변수를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-107">passes table-valued parameters to routines by reference to avoid making a copy of the input data.</span></span> <span data-ttu-id="a6892-108">테이블 반환 매개 변수를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 루틴을 만들고 실행한 다음 모든 관리 언어의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드, 관리되는 클라이언트 및 기본 클라이언트에서 해당 루틴을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-108">You can create and execute [!INCLUDE[tsql](../../includes/tsql-md.md)] routines with table-valued parameters, and call them from [!INCLUDE[tsql](../../includes/tsql-md.md)] code, managed and native clients in any managed language.</span></span>  
  
 <span data-ttu-id="a6892-109">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="a6892-109">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="a6892-110">이점</span><span class="sxs-lookup"><span data-stu-id="a6892-110">Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="a6892-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a6892-111">Restrictions</span></span>](#Restrictions)  
  
 [<span data-ttu-id="a6892-112">테이블 반환 매개 변수와 BULK INSERT 작업 비교</span><span class="sxs-lookup"><span data-stu-id="a6892-112">Table-Valued Parameters vs. BULK INSERT Operations</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="a6892-113">예제</span><span class="sxs-lookup"><span data-stu-id="a6892-113">Example</span></span>](#Example)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="a6892-114">이점</span><span class="sxs-lookup"><span data-stu-id="a6892-114">Benefits</span></span>  
 <span data-ttu-id="a6892-115">테이블 반환 매개 변수의 범위는 다른 매개 변수와 똑같이 저장 프로시저, 함수 또는 동적 [!INCLUDE[tsql](../../includes/tsql-md.md)] 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-115">A table-valued parameter is scoped to the stored procedure, function, or dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] text, exactly like other parameters.</span></span> <span data-ttu-id="a6892-116">마찬가지로 테이블 형식 변수의 범위는 DECLARE 문을 사용하여 만든 다른 모든 지역 변수의 범위와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-116">Similarly, a variable of table type has scope like any other local variable that is created by using a DECLARE statement.</span></span> <span data-ttu-id="a6892-117">동적 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 내에서 테이블 반환 변수를 선언하고 이 변수를 저장 프로시저 및 함수에 테이블 반환 매개 변수로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-117">You can declare table-valued variables within dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and pass these variables as table-valued parameters to stored procedures and functions.</span></span>  
  
 <span data-ttu-id="a6892-118">테이블 반환 매개 변수는 매개 변수 목록을 전달하는 임시 테이블 또는 다른 방법보다 유연하며 경우에 따라 보다 뛰어난 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-118">Table-valued parameters offer more flexibility and in some cases better performance than temporary tables or other ways to pass a list of parameters.</span></span> <span data-ttu-id="a6892-119">테이블 반환 매개 변수에서 제공하는 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-119">Table-valued parameters offer the following benefits:</span></span>  
  
-   <span data-ttu-id="a6892-120">클라이언트의 데이터를 처음 채울 때 잠글 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-120">Do not acquire locks for the initial population of data from a client.</span></span>  
  
-   <span data-ttu-id="a6892-121">간단한 프로그래밍 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-121">Provide a simple programming model.</span></span>  
  
-   <span data-ttu-id="a6892-122">단일 루틴에 복잡한 비즈니스 논리를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-122">Enable you to include complex business logic in a single routine.</span></span>  
  
-   <span data-ttu-id="a6892-123">서버 왕복을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-123">Reduce round trips to the server.</span></span>  
  
-   <span data-ttu-id="a6892-124">카디널리티가 다른 테이블 구조를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-124">Can have a table structure of different cardinality.</span></span>  
  
-   <span data-ttu-id="a6892-125">강력한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-125">Are strongly typed.</span></span>  
  
-   <span data-ttu-id="a6892-126">클라이언트가 정렬 순서 및 고유 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-126">Enable the client to specify sort order and unique keys.</span></span>  
  
-   <span data-ttu-id="a6892-127">저장 프로시저에서 사용 될 때 임시 테이블과 같이 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-127">Are cached like a temp table when used in a stored procedure.</span></span> <span data-ttu-id="a6892-128">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 테이블-반환 매개 변수는 또한 매개 변수가 있는 쿼리에 대해 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-128">Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], table-valued parameters are also cached for parameterized queries.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a6892-129">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a6892-129">Restrictions</span></span>  
 <span data-ttu-id="a6892-130">테이블 반환 매개 변수에는 다음과 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-130">Table-valued parameters have the following restrictions:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a6892-131">는 테이블 반환 매개 변수의 열에 대한 통계를 유지 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-131">does not maintain statistics on columns of table-valued parameters.</span></span>  
  
-   <span data-ttu-id="a6892-132">테이블 반환 매개 변수는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 루틴에 입력 READONLY 매개 변수로 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-132">Table-valued parameters must be passed as input READONLY parameters to [!INCLUDE[tsql](../../includes/tsql-md.md)] routines.</span></span> <span data-ttu-id="a6892-133">루틴 본문의 테이블 반환 매개 변수에 대해서는 UPDATE, DELETE 또는 INSERT와 같은 DML 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-133">You cannot perform DML operations such as UPDATE, DELETE, or INSERT on a table-valued parameter in the body of a routine.</span></span>  
  
-   <span data-ttu-id="a6892-134">테이블 반환 매개 변수를 SELECT INTO 또는 INSERT EXEC 문의 대상으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-134">You cannot use a table-valued parameter as target of a SELECT INTO or INSERT EXEC statement.</span></span> <span data-ttu-id="a6892-135">테이블 반환 매개 변수는 SELECT INTO의 FROM 절 또는 INSERT EXEC 문자열이나 저장 프로시저에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-135">A table-valued parameter can be in the FROM clause of SELECT INTO or in the INSERT EXEC string or stored procedure.</span></span>  
  
##  <a name="table-valued-parameters-vs-bulk-insert-operations"></a><a name="BulkInsert"></a><span data-ttu-id="a6892-136">테이블 반환 매개 변수와 BULK INSERT 작업 비교</span><span class="sxs-lookup"><span data-stu-id="a6892-136">Table-Valued Parameters vs. BULK INSERT Operations</span></span>  
 <span data-ttu-id="a6892-137">테이블 반환 매개 변수를 사용하는 방법은 집합 기반 변수를 사용하는 다른 방법과 유사하지만 큰 데이터 집합의 경우 테이블 반환 매개 변수를 사용하는 것이 훨씬 빠른 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-137">Using table-valued parameters is comparable to other ways of using set-based variables; however, using table-valued parameters frequently can be faster for large data sets.</span></span> <span data-ttu-id="a6892-138">테이블 반환 매개 변수보다 더 많은 시작 비용이 드는 대량 작업과 비교해볼 때 테이블 반환 매개 변수는 1,000개 미만의 행을 삽입할 때 더 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-138">Compared to bulk operations that have a greater startup cost than table-valued parameters, table-valued parameters perform well for inserting less than 1000 rows.</span></span>  
  
 <span data-ttu-id="a6892-139">다시 사용되는 테이블 반환 매개 변수는 임시 테이블 캐싱을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-139">Table-valued parameters that are reused benefit from temporary table caching.</span></span> <span data-ttu-id="a6892-140">이 테이블 캐싱은 이와 동일한 BULK INSERT 작업보다 뛰어난 확장성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-140">This table caching enables better scalability than equivalent BULK INSERT operations.</span></span> <span data-ttu-id="a6892-141">작은 행 삽입 작업을 사용하는 경우에는 BULK INSERT 작업 또는 테이블 반환 매개 변수 대신 매개 변수 목록 또는 일괄 처리된 문을 사용하여 작은 성능 이점을 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-141">By using small row-insert operations a small performance benefit might be gained by using parameter lists or batched statements instead of BULK INSERT operations or table-valued parameters.</span></span> <span data-ttu-id="a6892-142">그러나 이러한 메서드는 프로그래밍하기가 다소 불편하고 행이 늘어남에 따라 성능이 빠르게 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-142">However, these methods are less convenient to program, and performance decreases quickly as rows increase.</span></span>  
  
 <span data-ttu-id="a6892-143">테이블 반환 매개 변수는 동일한 매개 변수 배열 구현 이상의 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-143">Table-valued parameters perform equally well or better than an equivalent parameter array implementation.</span></span>  
  
##  <a name="example"></a><a name="Example"></a> <span data-ttu-id="a6892-144">예제</span><span class="sxs-lookup"><span data-stu-id="a6892-144">Example</span></span>  
 <span data-ttu-id="a6892-145">다음 예에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하며 테이블 반환 매개 변수 형식을 만들고, 해당 형식을 참조하는 변수를 선언하고, 매개 변수 목록을 채운 다음 저장 프로시저에 값을 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6892-145">The following example uses [!INCLUDE[tsql](../../includes/tsql-md.md)] and shows you how to create a table-valued parameter type, declare a variable to reference it, fill the parameter list, and then pass the values to a stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6892-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6892-146">See Also</span></span>  
 <span data-ttu-id="a6892-147">[CREATE TYPE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span></span>  
 <span data-ttu-id="a6892-148">[DECLARE @local_variable&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="a6892-149">[Transact-sql &#40;&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-149">[sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span></span>  
 <span data-ttu-id="a6892-150">[sys. Transact-sql&#41;&#40;매개 변수](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-150">[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span></span>  
 <span data-ttu-id="a6892-151">[parameter_type_usages &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-151">[sys.parameter_type_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span></span>  
 <span data-ttu-id="a6892-152">[CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6892-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="a6892-153">CREATE FUNCTION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a6892-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
