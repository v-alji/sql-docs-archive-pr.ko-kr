---
title: 메모리 액세스에 최적화 된 테이블이 있는 트랜잭션 격리 수준에 대 한 지침 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 834c5950a8f8b0ddf8854d06c6fb1073a264fc22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732919"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a><span data-ttu-id="e07d0-102">메모리 액세스에 최적화된 테이블의 트랜잭션 격리 수준에 대한 지침</span><span class="sxs-lookup"><span data-stu-id="e07d0-102">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>
  <span data-ttu-id="e07d0-103">대부분의 경우 트랜잭션 격리 수준을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-103">In many scenarios, you must specify the transaction isolation level.</span></span> <span data-ttu-id="e07d0-104">메모리 최적화 테이블에 대한 트랜잭션 격리는 디스크 기반 테이블과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-104">Transaction isolation for memory-optimized tables differs from disk-based tables.</span></span>  
  
 <span data-ttu-id="e07d0-105">트랜잭션 격리 수준을 지정하기 위한 요구 사항:</span><span class="sxs-lookup"><span data-stu-id="e07d0-105">Requirements for specifying transaction isolation level:</span></span>  
  
-   <span data-ttu-id="e07d0-106">트랜잭션 격리 수준은 고유하게 컴파일된 저장 프로시저의 콘텐츠를 구성하는 ATOMIC 블록에 대한 필수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-106">TRANSACTION ISOLATION LEVEL is a required option for the ATOMIC block comprising the content of a natively compiled stored procedure.</span></span>  
  
-   <span data-ttu-id="e07d0-107">크로스 컨테이너 트랜잭션에서 격리 수준을 사용할 때 적용되는 제한 사항 때문에 해석된 [!INCLUDE[tsql](../includes/tsql-md.md)]에서 메모리 최적화 테이블을 사용할 때는 종종 테이블에 액세스하는 데 사용되는 격리 수준을 지정하는 테이블 힌트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-107">Because of restrictions on isolation level use in cross-container transactions, uses of memory-optimized tables in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] must often be accompanied by a table hint specifying the isolation level used to access the table.</span></span> <span data-ttu-id="e07d0-108">격리 수준 힌트 및 크로스 컨테이너 트랜잭션에 대한 자세한 내용은 [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07d0-108">For more information about isolation level hints and cross-container transactions, see [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="e07d0-109">원하는 트랜잭션 격리 수준을 명시적으로 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-109">The desired transaction isolation level must be explicitly declared.</span></span> <span data-ttu-id="e07d0-110">트랜잭션에서 특정 행 또는 테이블의 격리를 보증하기 위해 잠금 힌트(예: XLOCK)를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-110">It is not possible to use locking hints (such as XLOCK) to guarantee the isolation of certain rows or tables in the transaction.</span></span>  
  
-   <span data-ttu-id="e07d0-111">데이터베이스에 액세스하는 애플리케이션은 트랜잭션 실패 충돌, 위반 오류 및 커밋 종속성 오류로 인해 발생하는 오류를 처리하는 다시 시도 논리를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-111">The application accessing the database should implement retry logic to deal with errors resulting from transaction-dooming conflicts, validation failures, and commit-dependency failures.</span></span> <span data-ttu-id="e07d0-112">커밋 종속성 오류는 읽기 전용 트랜잭션에서도 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-112">Note that commit dependency failures can occur even with read-only transactions.</span></span>  
  
-   <span data-ttu-id="e07d0-113">장기적으로 실행되는 트랜잭션은 메모리 최적화 테이블 사용을 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-113">Long-running transactions should be avoided with memory-optimized tables.</span></span> <span data-ttu-id="e07d0-114">이러한 트랜잭션은 충돌 및 후속 트랜잭션 종료 가능성을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-114">Such transactions increase the likelihood of conflicts and subsequent transaction terminations.</span></span> <span data-ttu-id="e07d0-115">장기 실행 트랜잭션으로 인해 가비지 수집도 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-115">A long-running transaction also defers garbage collection.</span></span> <span data-ttu-id="e07d0-116">트랜잭션 실행 시간이 늘어날수록, 메모리 내 OLTP에서 최근에 삭제된 행 버전을 더 오래 유지하며, 이는 새 트랜잭션에 대한 조회 성능을 저하시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-116">The longer a transaction runs, the longer In-Memory OLTP keeps recently deleted row versions, which can decrease lookup performance for new transactions.</span></span>  
  
 <span data-ttu-id="e07d0-117">일반적으로 디스크 기반 테이블은 잠금과 차단을 사용하여 트랜잭션 격리를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-117">Disk-based tables typically rely on locking and blocking for transaction isolation.</span></span> <span data-ttu-id="e07d0-118">메모리 액세스에 최적화된 테이블은 다중 버전 관리 및 충돌 검색을 사용하여 격리를 보증합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-118">Memory-optimized tables rely on multi-versioning and conflict detection to guarantee isolation.</span></span> <span data-ttu-id="e07d0-119">자세한 내용은 [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)의 충돌 검색, 유효성 검사 및 커밋 종속성 확인에 대한 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07d0-119">For details, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="e07d0-120">디스크 기반 테이블은 SNAPSHOT 및 READ_COMMITTED_SNAPSHOT 격리 수준을 사용한 다중 버전 관리를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-120">Disk-based tables do allow multi-versioning with the isolation levels SNAPSHOT and READ_COMMITTED_SNAPSHOT.</span></span> <span data-ttu-id="e07d0-121">메모리 최적화 테이블의 경우 모든 격리 수준이 REPEATABLE READ 및 SERIALIZABLE을 비롯한 여러 버전을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-121">For memory-optimized tables all isolation levels are multi-version based, including REPEATABLE READ and SERIALIZABLE.</span></span>  
  
## <a name="types-of-transactions"></a><span data-ttu-id="e07d0-122">트랜잭션 유형</span><span class="sxs-lookup"><span data-stu-id="e07d0-122">Types of Transactions</span></span>  
 <span data-ttu-id="e07d0-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 모든 쿼리는 트랜잭션의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-123">Every query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] runs in the context of a transaction.</span></span>  
  
 <span data-ttu-id="e07d0-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에는 다음과 같은 세 가지 유형의 트랜잭션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-124">There are three types of transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e07d0-125">자동 커밋 트랜잭션.</span><span class="sxs-lookup"><span data-stu-id="e07d0-125">Autocommit transactions.</span></span> <span data-ttu-id="e07d0-126">세션에 활성 트랜잭션 컨텍스트가 없고 암시적 트랜잭션이 ON으로 설정되지 않은 경우 쿼리마다 고유한 트랜잭션 컨텍스트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-126">If there is no active transaction context and implicit transactions are not set to ON in the session, each query has its own transaction context.</span></span> <span data-ttu-id="e07d0-127">트랜잭션은 문 실행이 시작되면 시작되고 문 실행이 끝나면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-127">The transaction starts when the statement starts execution, and completes when the statement finishes.</span></span>  
  
-   <span data-ttu-id="e07d0-128">명시적 트랜잭션.</span><span class="sxs-lookup"><span data-stu-id="e07d0-128">Explicit transactions.</span></span> <span data-ttu-id="e07d0-129">사용자는 명시적 BEGIN TRAN 또는 BEGIN ATOMIC을 통해 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-129">The user starts the transaction through an explicit BEGIN TRAN or BEGIN ATOMIC.</span></span> <span data-ttu-id="e07d0-130">트랜잭션은 해당 COMMIT 및 ROLLBACK 또는 END(ATOMIC 블록의 경우) 다음에 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-130">The transaction is completed following the corresponding COMMIT and ROLLBACK or END (in the case of an atomic block).</span></span>  
  
-   <span data-ttu-id="e07d0-131">암시적 트랜잭션.</span><span class="sxs-lookup"><span data-stu-id="e07d0-131">Implicit transactions.</span></span> <span data-ttu-id="e07d0-132">IMPLICIT_TRANSACTIONS 옵션이 ON으로 설정된 경우 활성 트랜잭션 컨텍스트가 없는 상태에서 사용자가 문을 실행할 때마다 트랜잭션이 암시적으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-132">When the option IMPLICIT_TRANSACTIONS is set to ON, a transaction is started implicitly whenever the user executes a statement and there is no active transaction context.</span></span> <span data-ttu-id="e07d0-133">트랜잭션은 명시적 COMMIT 및 ROLLBACK을 통해 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-133">The transaction is completed through an explicit COMMIT and ROLLBACK.</span></span>  
  
## <a name="baseline-read-committed-isolation"></a><span data-ttu-id="e07d0-134">기준 READ COMMITTED 격리</span><span class="sxs-lookup"><span data-stu-id="e07d0-134">Baseline READ COMMITTED Isolation</span></span>  
 <span data-ttu-id="e07d0-135">READ COMMITTED는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 기본 격리 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-135">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e07d0-136">격리 수준 READ COMMITTED를 사용하면 트랜잭션은 현재 트랜잭션 외부의 변경 내용에서 커밋되지 않은 데이터를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-136">The isolation level READ COMMITTED guarantees that transactions do not see any uncommitted data from changes outside the current transaction.</span></span> <span data-ttu-id="e07d0-137">즉, 트랜잭션은 데이터베이스에 커밋되었거나 현재 트랜잭션에 의해 변경된 데이터만 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-137">In other words, the transaction only reads data which has either been committed to the database, or has been changed by the current transaction.</span></span>  
  
 <span data-ttu-id="e07d0-138">메모리 최적화 테이블에 대해 지원되는 모든 격리 수준은 커밋된 읽기 보증을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-138">All isolation levels supported for memory-optimized tables provide the read committed guarantee.</span></span> <span data-ttu-id="e07d0-139">따라서 트랜잭션에 더 강력한 보증이 필요 없는 경우에는 메모리 최적화 테이블에 대해 지원되는 아무 격리 수준이나 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-139">Therefore, if the transaction does not require stronger guarantees, you can use any of the isolation levels supported for memory-optimized tables.</span></span> <span data-ttu-id="e07d0-140">SNAPSHOT은 다른 어떤 격리 수준보다 가장 적은 시스템 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-140">SNAPSHOT uses the fewest system resources, compared to other isolation levels.</span></span>  
  
 <span data-ttu-id="e07d0-141">SNAPSHOT 격리 수준(메모리 최적화 테이블에 대해 지원되는 가장 낮은 격리 수준)이 제공하는 보증에는 READ COMMITTED의 보증이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-141">The guarantee provided by the SNAPSHOT isolation level (the lowest level of isolation supported for memory-optimized tables) includes the guarantees of READ COMMITTED.</span></span> <span data-ttu-id="e07d0-142">트랜잭션의 각 문은 동일한 버전의 데이터베이스를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-142">Every statement in the transaction reads the same, consistent version of the database.</span></span> <span data-ttu-id="e07d0-143">트랜잭션에서 읽은 모든 행이 데이터베이스에 커밋될 뿐 아니라 모든 읽기 작업이 동일한 트랜잭션 집합에 의해 변경된 내용 집합을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-143">Not only are all the rows read by the transaction committed to the database, also all the read operations see the set of changes made by the same set of transactions.</span></span>  
  
 <span data-ttu-id="e07d0-144">**지침**: READ COMMITTED 격리 보증만 필요한 경우 고유하게 컴파일된 저장 프로시저에 대해 SNAPSHOT 격리를 사용하여 해석된 [!INCLUDE[tsql](../includes/tsql-md.md)]을 통해 메모리 최적화 테이블에 액세스하세요.</span><span class="sxs-lookup"><span data-stu-id="e07d0-144">**Guideline**: If only the READ COMMITTED isolation guarantee is required, use SNAPSHOT isolation with natively compiled stored procedures and for accessing memory-optimized tables through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e07d0-145">자동 커밋 트랜잭션의 경우 READ COMMITTED 격리 수준이 메모리 최적화 테이블에 대한 SNAPSHOT에 암시적으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-145">For autocommit transactions, the isolation level READ COMMITTED is implicitly mapped to SNAPSHOT for memory-optimized tables.</span></span> <span data-ttu-id="e07d0-146">따라서 TRANSACTION ISOLATION LEVEL 세션 설정이 READ COMMITTED로 설정된 경우 메모리 최적화 테이블에 액세스할 때 테이블 힌트를 통해 격리 수준을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-146">Therefore, if the TRANSACTION ISOLATION LEVEL session setting is set to READ COMMITTED, it is not necessary to specify the isolation level through a table hint when accessing memory-optimized tables.</span></span>  
  
 <span data-ttu-id="e07d0-147">다음 자동 커밋 트랜잭션 예에서는 임시 일괄 처리의 일부로 메모리 최적화 테이블 Customers와 일반 테이블 [Order History] 간의 조인을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-147">The following autocommit transaction example shows a join between a memory-optimized table Customers and a regular table [Order History], as part of an ad hoc batch:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 <span data-ttu-id="e07d0-148">다음 명시적 또는 암시적 트랜잭션 예에서는 이번에는 명시적 사용자 트랜잭션에서 수행된다는 점만 다르고 위와 동일한 조인을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-148">The following explicit or implicit transactions example shows the same join, but this time in an explicit user transaction.</span></span> <span data-ttu-id="e07d0-149">테이블 힌트 WITH (SNAPSHOT)에 표시된 대로 메모리 최적화 테이블 Customers는 스냅샷 격리에서 액세스되고 일반 테이블 [Order History]는 커밋된 읽기 격리에서 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-149">The memory-optimized table Customers is accessed under snapshot isolation, as indicated through the table hint WITH (SNAPSHOT), and the regular table [Order History] is accessed under read committed isolation:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a><span data-ttu-id="e07d0-150">작동 차이</span><span class="sxs-lookup"><span data-stu-id="e07d0-150">Operational Differences</span></span>  
 <span data-ttu-id="e07d0-151">커밋된 읽기 보증 외에도 디스크 기반 테이블을 사용하는 애플리케이션에서 사용할 수 있는 두 가지 중요한 구현 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-151">Besides the read committed guarantee, there are also two key implementation details that applications using disk-based tables may rely on.</span></span> <span data-ttu-id="e07d0-152">READ COMMITTED를 사용하여 액세스하는 디스크 기반 테이블을 SNAPSHOT 격리를 사용하여 액세스하는 메모리 최적화 테이블로 변환할 때는 다음 사항에 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="e07d0-152">Be aware of the following when converting a disk-based table that is accessed using READ COMMITTED isolation to a memory-optimized table that is accessed using SNAPSHOT isolation:</span></span>  
  
-   <span data-ttu-id="e07d0-153">디스크 기반 테이블에 대해 READ COMMITTED 격리 수준(READ_COMMITTED_SNAPSHOT이 OFF라고 가정)을 구현할 때는 판독기와 기록기가 충돌하는 것을 방지하기 위해 잠금이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-153">The implementation of the READ COMMITTED isolation level for disk-based tables (assuming READ_COMMITTED_SNAPSHOT is OFF) uses locks to prevent conflicts between readers and writers.</span></span> <span data-ttu-id="e07d0-154">기록기가 행을 업데이트하기 시작하면 잠금이 설정되고 트랜잭션이 커밋될 때까지 잠금이 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-154">When a writer starts updating a row, it takes a lock and does not release the lock until the transaction is committed.</span></span> <span data-ttu-id="e07d0-155">모든 읽기 작업은 차단되고 쓰기 트랜잭션이 커밋될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-155">Any read operations are blocked and will wait for the write transaction to commit.</span></span>  
  
     <span data-ttu-id="e07d0-156">일부 애플리케이션의 경우 판독기는 항상 기록기가 커밋할 때까지 기다린다고 가정할 수도 있습니다. 특히 애플리케이션 계층에서 두 트랜잭션 간의 동기화가 있을 경우 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-156">Some applications may assume readers always wait for writers to commit, particularly if there is any synchronization between the two transactions in the application tier.</span></span>  
  
     <span data-ttu-id="e07d0-157">**지침:** 애플리케이션은 차단 동작을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-157">**Guideline:** Applications cannot rely on blocking behavior.</span></span> <span data-ttu-id="e07d0-158">응용 프로그램에서 동시 트랜잭션을 동기화 해야 하는 경우에는 [sp_getapplock &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql)를 통해 응용 프로그램 계층 이나 데이터베이스 계층에서 이러한 논리를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-158">If an application needs synchronization between concurrent transactions, such logic can be implemented in the application tier or in the database tier, through [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span></span>  
  
-   <span data-ttu-id="e07d0-159">READ COMMITTED 격리를 사용하는 트랜잭션에서는 각 문이 데이터베이스에 있는 행의 최신 버전을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-159">In transactions that use READ COMMITTED isolation, each statement sees the most recent version of the rows in the database.</span></span> <span data-ttu-id="e07d0-160">따라서 이후 문은 데이터베이스 상태에 대한 변경 내용을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-160">Therefore, subsequent statements see changes in the state of the database.</span></span>  
  
     <span data-ttu-id="e07d0-161">이 가정을 사용하는 애플리케이션 패턴의 예로 새 행을 찾을 때까지 WHILE 루프를 사용하여 테이블을 폴링하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-161">Polling a table using a WHILE loop until a new row has been found is an example of an application pattern that uses this assumption.</span></span> <span data-ttu-id="e07d0-162">루프가 반복될 때마다 쿼리는 데이터베이스에 있는 최신 업데이트를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-162">With each iteration of the loop, the query will see the latest updates in the database.</span></span>  
  
     <span data-ttu-id="e07d0-163">**지침:** 애플리케이션에서 테이블에 쓰여진 최신 행을 가져오기 위해 메모리 최적화 테이블을 폴링해야 하는 경우 폴링 루프를 트랜잭션 범위 밖으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-163">**Guideline:** If an application needs to poll a memory-optimized table to obtain the most recent rows written to the table, move the polling loop outside the scope of the transaction.</span></span>  
  
     <span data-ttu-id="e07d0-164">다음은 이 가정을 사용하는 애플리케이션 패턴의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-164">The following is an example application pattern that uses this assumption.</span></span> <span data-ttu-id="e07d0-165">새 행을 찾을 때까지 WHILE 루트를 사용하여 테이블을 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-165">Polling a table using a WHILE loop until a new row is found.</span></span> <span data-ttu-id="e07d0-166">루프가 반복될 때마다 쿼리는 데이터베이스에 있는 최신 업데이트에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-166">In each loop iteration, the query will access the latest updates in the database.</span></span>  
  
 <span data-ttu-id="e07d0-167">다음 스크립트 예에서는 행을 찾을 때까지 t1 테이블을 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-167">The following example script polls a table t1 until it has a row.</span></span> <span data-ttu-id="e07d0-168">그런 다음 추가 처리를 위해 테이블에서 행 하나를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-168">It then removes a single row from the table for further processing.</span></span>  
  
 <span data-ttu-id="e07d0-169">폴링 논리는 스냅샷 격리를 사용하여 t1 테이블에 액세스하므로 트랜잭션 범위 밖에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-169">Notice that the polling logic needs to be outside the scope of the transaction, as it is using snapshot isolation to access table t1.</span></span> <span data-ttu-id="e07d0-170">트랜잭션 범위 내에서 폴링 논리를 사용하면 장기 실행 트랜잭션이 만들어지는데, 이는 좋은 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-170">Using polling logic inside the scope of a transaction would create a long-running transaction, which is a bad practice.</span></span>  
  
```sql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a><span data-ttu-id="e07d0-171">테이블 잠금 힌트</span><span class="sxs-lookup"><span data-stu-id="e07d0-171">Locking Table Hints</span></span>  
 <span data-ttu-id="e07d0-172">HOLDLOCK 및 XLOCK 등의 잠금[&#41;&#40;](/sql/t-sql/queries/hints-transact-sql-table)힌트는 디스크 기반 테이블에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 지정 된 격리 수준에 필요한 것 보다 더 많은 잠금을 수행 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-172">Locking hints ([Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) such as HOLDLOCK and XLOCK can be used with disk-based tables to have [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] take more locks than are required for the specified isolation level.</span></span>  
  
 <span data-ttu-id="e07d0-173">메모리 액세스에 최적화된 테이블은 잠금을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-173">Memory-optimized tables do not use locks.</span></span> <span data-ttu-id="e07d0-174">REPEATABLE READ와 SERIALIZABLE 같은 더 높은 격리 수준을 사용하여 원하는 보증을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-174">Higher isolation levels such as REPEATABLE READ and SERIALIZABLE can be used to declare the desired guarantees.</span></span>  
  
 <span data-ttu-id="e07d0-175">잠금 힌트는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-175">Locking hints are not supported.</span></span> <span data-ttu-id="e07d0-176">대신 트랜잭션 격리 수준을 통해 필요한 보증을 선언하십시오.</span><span class="sxs-lookup"><span data-stu-id="e07d0-176">Instead, declare the required guarantees through the transaction isolation levels.</span></span> <span data-ttu-id="e07d0-177">([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 메모리 최적화 테이블을 잠그지 않기 때문에 NOLOCK이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e07d0-177">(NOLOCK is supported because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not take locks on memory-optimized tables.</span></span> <span data-ttu-id="e07d0-178">디스크 기반 테이블과 달리 NOLOCK은 메모리 최적화 테이블에 대한 READ UNCOMMITTED 동작을 의미하지는 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="e07d0-178">Note that, in contrast to disk-based tables, NOLOCK does not imply READ UNCOMMITTED behavior for memory-optimized tables.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07d0-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e07d0-179">See Also</span></span>  
 <span data-ttu-id="e07d0-180">[메모리 액세스에 최적화 된 테이블의 트랜잭션 이해](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="e07d0-180">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="e07d0-181">[메모리 액세스에 최적화 된 테이블의 트랜잭션에 대 한 재시도 논리 지침](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="e07d0-181">[Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="e07d0-182">트랜잭션 격리 수준</span><span class="sxs-lookup"><span data-stu-id="e07d0-182">Transaction Isolation Levels</span></span>](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
