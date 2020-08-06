---
title: Atomic 블록 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ca8f5b4d767ef0fe836cd260f8d12dd5b40c75d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647002"
---
# <a name="atomic-blocks"></a><span data-ttu-id="7a69b-102">ATOMIC 블록</span><span class="sxs-lookup"><span data-stu-id="7a69b-102">Atomic Blocks</span></span>
  <span data-ttu-id="7a69b-103">`BEGIN ATOMIC`은 ANSI SQL 표준의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-103">`BEGIN ATOMIC` is part of the ANSI SQL standard.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="7a69b-104">는 고유하게 컴파일된 저장 프로시저의 최상위 수준에서만 ATOMIC 블록을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-104">supports atomic blocks only at the top-level of natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="7a69b-105">고유하게 컴파일된 모든 저장 프로시저에는 항상 하나의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 블록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-105">Every natively compiled stored procedure contains exactly one block of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7a69b-106">이것이 ATOMIC 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-106">This is an ATOMIC block.</span></span>  
  
-   <span data-ttu-id="7a69b-107">고유하지 않은 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저 및 임시 일괄 처리는 ATOMIC 블록을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-107">Non-native, interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and ad hoc batches do not support atomic blocks.</span></span>  
  
 <span data-ttu-id="7a69b-108">ATOMIC 블록은 트랜잭션 내에서 하나의 큰 단위로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-108">Atomic blocks are executed (atomically) within the transaction.</span></span> <span data-ttu-id="7a69b-109">블록의 모든 문이 성공하거나 전체 블록이 블록 시작 시 만들어진 저장점으로 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-109">Either all statements in the block succeed or the entire block will be rolled back to the savepoint that was created at the start of the block.</span></span> <span data-ttu-id="7a69b-110">또한 세션 설정이 ATOMIC 블록에 대해 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-110">In addition, the session settings are fixed for the atomic block.</span></span> <span data-ttu-id="7a69b-111">세션에서 동일한 ATOMIC 블록을 여러 가지 다른 설정으로 실행하면 현재 세션 설정과 관계없이 같은 동작이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-111">Executing the same atomic block in sessions with different settings will result in the same behavior, independent of the settings of the current session.</span></span>  
  
## <a name="transactions-and-error-handling"></a><span data-ttu-id="7a69b-112">트랜잭션 및 오류 처리</span><span class="sxs-lookup"><span data-stu-id="7a69b-112">Transactions and Error Handling</span></span>  
 <span data-ttu-id="7a69b-113">세션에 트랜잭션이 이미 있는 경우(`BEGIN TRANSACTION` 문과 트랜잭션을 실행한 일괄 처리가 활성 상태로 유지되므로) ATOMIC 블록을 시작하면 트랜잭션에서 저장점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-113">If a transaction already exists on a session (because a batch executed a `BEGIN TRANSACTION` statement and the transaction remains active), then starting an atomic block will create a savepoint in the transaction.</span></span> <span data-ttu-id="7a69b-114">예외가 발생하지 않고 블록이 종료되면 블록 커밋에 대한 새 저장점이 만들어지지만 세션 수준에서 트랜잭션이 커밋되어야 트랜잭션이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-114">If the block exits without an exception, the savepoint that was created for the block commits, but the transaction will not commit until the transaction at the session level commits.</span></span> <span data-ttu-id="7a69b-115">블록에서 예외가 발생하면 블록의 효과는 롤백되지만 예외로 인해 트랜잭션이 실패하지 않으면 세션 수준의 트랜잭션이 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-115">If the block throws an exception, the effects of the block are rolled back but the transaction at the session level will proceed, unless the exception is transaction-dooming.</span></span> <span data-ttu-id="7a69b-116">예를 들어, 쓰기 충돌로 인해 트랜잭션이 실패하지만 쓰기 충돌이 형식 캐스팅 오류는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-116">For example a write conflict is transaction-dooming, but not a type casting error.</span></span>  
  
 <span data-ttu-id="7a69b-117">세션에 활성 트랜잭션이 없는 경우 `BEGIN ATOMIC`은 새 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-117">If there is no active transaction on a session, `BEGIN ATOMIC` will start a new transaction.</span></span> <span data-ttu-id="7a69b-118">블록 범위 밖에서 예외가 발생하지 않는다면 트랜잭션은 블록 끝에서 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-118">If no exception is thrown outside the scope of the block, the transaction will be committed at the end of the block.</span></span> <span data-ttu-id="7a69b-119">블록에서 예외가 발생하면(예외가 catch되지 않고 블록 내에서 처리됨) 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-119">If the block throws an exception (that is, the exception is not caught and handled within the block), the transaction will be rolled back.</span></span> <span data-ttu-id="7a69b-120">단일 ATOMIC 블록에 걸쳐 있는 트랜잭션(고유하게 컴파일된 단일 저장 프로시저)의 경우 `BEGIN TRANSACTION` 및 `COMMIT` 또는 `ROLLBACK` 문을 명시적으로 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-120">For transactions that span a single atomic block (a single natively compiled stored procedure), you do not need to write explicit `BEGIN TRANSACTION` and `COMMIT` or `ROLLBACK` statements.</span></span>  
  
 <span data-ttu-id="7a69b-121">고유하게 컴파일된 저장 프로시저는 오류 처리를 위해 `TRY`, `CATCH` 및 `THROW` 구문을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-121">Natively compiled stored procedures support the `TRY`, `CATCH`, and `THROW` constructs for error handling.</span></span> <span data-ttu-id="7a69b-122">`RAISERROR`은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-122">`RAISERROR` is not supported.</span></span>  
  
 <span data-ttu-id="7a69b-123">다음 예에서는 ATOMIC 블록 및 고유하게 컴파일된 저장 프로시저에 대한 오류 처리 동작을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-123">The following example illustrates the error handling behavior with atomic blocks and natively compiled stored procedures:</span></span>  
  
```sql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 <span data-ttu-id="7a69b-124">메모리 최적화 테이블에 대한 다음 오류 메시지가 발생하면 트랜잭션이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-124">The following error messages specific to memory-optimized tables are transaction dooming.</span></span> <span data-ttu-id="7a69b-125">Atomic 블록 범위 내에서 10772, 41301, 41302, 41305, 41325, 41332 및 41333 오류가 발생하면 트랜잭션을 중단시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-125">If they occur in the scope of an atomic block, they will cause the transaction to abort: 10772, 41301, 41302, 41305, 41325, 41332, and 41333.</span></span>  
  
## <a name="session-settings"></a><span data-ttu-id="7a69b-126">세션 설정</span><span class="sxs-lookup"><span data-stu-id="7a69b-126">Session Settings</span></span>  
 <span data-ttu-id="7a69b-127">저장 프로시저가 컴파일되면 ATOMIC 블록의 세션 설정은 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-127">The session settings in atomic blocks are fixed when the stored procedure is compiled.</span></span> <span data-ttu-id="7a69b-128">설정은 `BEGIN ATOMIC`으로 지정할 수도 있고 같은 값으로 항상 고정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-128">Some settings can be specified with `BEGIN ATOMIC` while other settings are always fixed to the same value.</span></span>  
  
 <span data-ttu-id="7a69b-129">`BEGIN ATOMIC`에는 다음 옵션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-129">The following options are required with `BEGIN ATOMIC`:</span></span>  
  
|<span data-ttu-id="7a69b-130">필요한 설정</span><span class="sxs-lookup"><span data-stu-id="7a69b-130">Required Setting</span></span>|<span data-ttu-id="7a69b-131">Description</span><span class="sxs-lookup"><span data-stu-id="7a69b-131">Description</span></span>|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|<span data-ttu-id="7a69b-132">지원되는 값은 `SNAPSHOT`, `REPEATABLEREAD` 및 `SERIALIZABLE`입니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-132">Supported values are `SNAPSHOT`, `REPEATABLEREAD`, and `SERIALIZABLE`.</span></span>|  
|`LANGUAGE`|<span data-ttu-id="7a69b-133">날짜 및 시간 형식과 시스템 메시지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-133">Determines date and time formats and system messages.</span></span> <span data-ttu-id="7a69b-134">[sys.syslanguages&#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)의 모든 언어와 별칭이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-134">All languages and aliases in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) are supported.</span></span>|  
  
 <span data-ttu-id="7a69b-135">다음 설정은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-135">The following settings are optional:</span></span>  
  
|<span data-ttu-id="7a69b-136">선택적 설정</span><span class="sxs-lookup"><span data-stu-id="7a69b-136">Optional Setting</span></span>|<span data-ttu-id="7a69b-137">Description</span><span class="sxs-lookup"><span data-stu-id="7a69b-137">Description</span></span>|  
|----------------------|-----------------|  
|`DATEFORMAT`|<span data-ttu-id="7a69b-138">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-138">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date formats are supported.</span></span> <span data-ttu-id="7a69b-139">지정되면 `DATEFORMAT`에서 `LANGUAGE`와 관련된 기본 날짜 형식을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-139">When specified, `DATEFORMAT` overrides the default date format associated with `LANGUAGE`.</span></span>|  
|`DATEFIRST`|<span data-ttu-id="7a69b-140">지정되면 `DATEFIRST`에서 `LANGUAGE`와 관련된 기본값을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-140">When specified, `DATEFIRST` overrides the default associated with `LANGUAGE`.</span></span>|  
|`DELAYED_DURABILITY`|<span data-ttu-id="7a69b-141">지원되는 값은 `OFF` 및 `ON`입니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-141">Supported values are `OFF` and `ON`.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7a69b-142">트랜잭션은 완전 내구성이 있는(기본값) 커밋 또는 지연된 내구성이 있는 커밋을 수행할 수 있습니다. 자세한 내용은 [트랜잭션 내구성 제어](../logs/control-transaction-durability.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a69b-142">transaction commits can be either fully durable, the default, or delayed durable.For more information, see [Control Transaction Durability](../logs/control-transaction-durability.md).</span></span>|  
  
 <span data-ttu-id="7a69b-143">다음 SET 옵션은 고유하게 컴파일된 모든 저장 프로시저의 모든 ATOMIC 블록에 대해 동일한 시스템 기본값을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-143">The following SET options have the same system default value for all atomic blocks in all natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="7a69b-144">SET 옵션</span><span class="sxs-lookup"><span data-stu-id="7a69b-144">Set Option</span></span>|<span data-ttu-id="7a69b-145">ATOMIC 블록의 시스템 기본값</span><span class="sxs-lookup"><span data-stu-id="7a69b-145">System Default for Atomic Blocks</span></span>|  
|----------------|--------------------------------------|  
|<span data-ttu-id="7a69b-146">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="7a69b-146">ANSI_NULLS</span></span>|<span data-ttu-id="7a69b-147">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-147">ON</span></span>|  
|<span data-ttu-id="7a69b-148">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="7a69b-148">ANSI_PADDING</span></span>|<span data-ttu-id="7a69b-149">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-149">ON</span></span>|  
|<span data-ttu-id="7a69b-150">ANSI_WARNING</span><span class="sxs-lookup"><span data-stu-id="7a69b-150">ANSI_WARNING</span></span>|<span data-ttu-id="7a69b-151">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-151">ON</span></span>|  
|<span data-ttu-id="7a69b-152">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="7a69b-152">ARITHABORT</span></span>|<span data-ttu-id="7a69b-153">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-153">ON</span></span>|  
|<span data-ttu-id="7a69b-154">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="7a69b-154">ARITHIGNORE</span></span>|<span data-ttu-id="7a69b-155">OFF</span><span class="sxs-lookup"><span data-stu-id="7a69b-155">OFF</span></span>|  
|<span data-ttu-id="7a69b-156">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="7a69b-156">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="7a69b-157">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-157">ON</span></span>|  
|<span data-ttu-id="7a69b-158">IDENTITY_INSERT</span><span class="sxs-lookup"><span data-stu-id="7a69b-158">IDENTITY_INSERT</span></span>|<span data-ttu-id="7a69b-159">OFF</span><span class="sxs-lookup"><span data-stu-id="7a69b-159">OFF</span></span>|  
|<span data-ttu-id="7a69b-160">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="7a69b-160">NOCOUNT</span></span>|<span data-ttu-id="7a69b-161">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-161">ON</span></span>|  
|<span data-ttu-id="7a69b-162">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="7a69b-162">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="7a69b-163">OFF</span><span class="sxs-lookup"><span data-stu-id="7a69b-163">OFF</span></span>|  
|<span data-ttu-id="7a69b-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="7a69b-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="7a69b-165">켜기</span><span class="sxs-lookup"><span data-stu-id="7a69b-165">ON</span></span>|  
|<span data-ttu-id="7a69b-166">ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="7a69b-166">ROWCOUNT</span></span>|<span data-ttu-id="7a69b-167">0</span><span class="sxs-lookup"><span data-stu-id="7a69b-167">0</span></span>|  
|<span data-ttu-id="7a69b-168">TEXTSIZE</span><span class="sxs-lookup"><span data-stu-id="7a69b-168">TEXTSIZE</span></span>|<span data-ttu-id="7a69b-169">0</span><span class="sxs-lookup"><span data-stu-id="7a69b-169">0</span></span>|  
|<span data-ttu-id="7a69b-170">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="7a69b-170">XACT_ABORT</span></span>|<span data-ttu-id="7a69b-171">OFF</span><span class="sxs-lookup"><span data-stu-id="7a69b-171">OFF</span></span><br /><br /> <span data-ttu-id="7a69b-172">catch되지 않는 예외는 ATOMIC 블록을 롤백시키지만 오류로 인해 트랜잭션이 실패하지 않는다면 트랜잭션이 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a69b-172">Uncaught exceptions cause the atomic block to roll back, but not cause the transaction to abort unless the error is transaction dooming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a69b-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a69b-173">See Also</span></span>  
 [<span data-ttu-id="7a69b-174">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="7a69b-174">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
