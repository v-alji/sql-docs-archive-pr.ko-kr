---
title: 크로스 컨테이너 트랜잭션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28437f0903459616a574e713c0f138e8bb459870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651247"
---
# <a name="cross-container-transactions"></a><span data-ttu-id="a1bcc-102">크로스 컨테이너 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="a1bcc-102">Cross-Container Transactions</span></span>
  <span data-ttu-id="a1bcc-103">크로스 컨테이너 트랜잭션은 메모리 최적화 테이블에서 고유하게 컴파일된 저장 프로시저 또는 작업에 대한 호출을 포함하는 암시적이거나 명시적인 사용자 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-103">Cross-container transactions are either implicit or explicit user transactions that include calls to natively-compiled stored procedures or operations on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a1bcc-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 저장 프로시저에 대한 호출은 트랜잭션을 시작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-104">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], calls to stored procedures do not initiate a transaction.</span></span> <span data-ttu-id="a1bcc-105">자동 모드에서 고유하게 컴파일된 프로시저의 실행(사용자 트랜잭션의 컨텍스트가 아님)은 크로스 컨테이너 트랜잭션으로 간주되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-105">Executions of natively compiled procedures in autocommit mode (not in the context of a user transaction) are not considered cross-container transactions.</span></span>  
  
 <span data-ttu-id="a1bcc-106">메모리 최적화 테이블을 참조하는 해석된 쿼리는 명시적이거나 암시적인 트랜잭션 또는 자동 커밋 모드에서 실행되는지 여부에 관계없이 크로스 컨테이너 트랜잭션의 일부로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-106">Any interpreted query that references memory-optimized tables is considered a part of a cross-container transaction, whether executed from an explicit or implicit transaction or in auto-commit mode.</span></span>  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a><span data-ttu-id="a1bcc-107">개별 작업의 격리</span><span class="sxs-lookup"><span data-stu-id="a1bcc-107">Isolation of Individual Operations</span></span>  
 <span data-ttu-id="a1bcc-108">각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 트랜잭션마다 격리 수준이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-108">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] transaction has an isolation level.</span></span> <span data-ttu-id="a1bcc-109">기본 격리 수준은 커밋된 읽기입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-109">The default isolation level is Read Committed.</span></span> <span data-ttu-id="a1bcc-110">다른 격리 수준을 사용 하려면 [트랜잭션 격리 수준 설정 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)를 사용 하 여 격리 수준을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-110">To use a different isolation level, you can set the isolation level using [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="a1bcc-111">따라서 디스크 기반 테이블과는 다른 격리 수준의 메모리 최적화 테이블에서 작업을 수행해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-111">It is often necessary to perform operations on memory-optimized tables at a different isolation level than operations on disk-based tables.</span></span> <span data-ttu-id="a1bcc-112">트랜잭션에서는 문의 컬렉션 또는 개별 읽기 작업에 대해 다른 격리 수준을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-112">In a transaction, it is possible to set a different isolation level for a collection of statements or for an individual read operation.</span></span>  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a><span data-ttu-id="a1bcc-113">개별 작업의 격리 수준 지정</span><span class="sxs-lookup"><span data-stu-id="a1bcc-113">Specifying the Isolation Level of Individual Operations</span></span>  
 <span data-ttu-id="a1bcc-114">트랜잭션의 문 집합에 대해 다른 격리 수준을 설정하려면 `SET TRANSACTION ISOLATION LEVEL`을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-114">To set a different isolation level for a set of statements in a transaction, you can use `SET TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="a1bcc-115">트랜잭션의 다음 예제는 기본적으로 직렬화 격리 수준을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-115">The following example of a transaction uses the serializable isolation level as default.</span></span> <span data-ttu-id="a1bcc-116">t3, t2 및 t1의 삽입 및 선택 작업은 반복 가능 읽기 격리에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-116">The insert and select operations on t3, t2, and t1 are executed under repeatable read isolation.</span></span>  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 <span data-ttu-id="a1bcc-117">트랜잭션 기본값과 다른 개별 읽기 작업에 대한 격리 수준을 설정하려면 테이블 힌트(예: 직렬화 가능)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-117">To set an isolation level for individual read operations that is different from the transaction default, you can use a table hint (for example, serializable).</span></span> <span data-ttu-id="a1bcc-118">행을 업데이트하거나 삭제하려면 항상 먼저 행을 읽어야 하므로 모든 선택 작업은 읽기 작업에 해당하고 모든 업데이트 및 삭제 작업은 읽기 작업에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-118">Every select corresponds to a read operation and every update and every delete corresponds to a read, because the row always needs to be read before it can be updated or deleted.</span></span> <span data-ttu-id="a1bcc-119">쓰기는 항상 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 격리되므로 삽입 작업에는 격리 수준이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-119">Insert operations do not have an isolation level, because writes are always isolated in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a1bcc-120">다음 예제에서 트랜잭션의 기본 격리 수준은 커밋된 읽기이지만 테이블 t1은 직렬화 가능에서 액세스되고 t2는 스냅샷 격리에서 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-120">In the following example, the default isolation level for the transaction is read committed, but table t1 is accessed under serializable and t2 under snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a><span data-ttu-id="a1bcc-121">개별 작업에 대한 격리 의미</span><span class="sxs-lookup"><span data-stu-id="a1bcc-121">Isolation Semantics for Individual Operations</span></span>  
 <span data-ttu-id="a1bcc-122">직렬화 트랜잭션 T는 완벽한 격리 상태에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-122">A serializable transaction T is executed in complete isolation.</span></span> <span data-ttu-id="a1bcc-123">이런 상황은 다른 모든 트랜잭션이 T가 시작되기 전에 커밋되거나 T가 커밋된 후에 시작된 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-123">It is as if every other transaction has either committed before T started, or is started after T committed.</span></span> <span data-ttu-id="a1bcc-124">따라서 트랜잭션의 작업마다 격리 수준이 다르면 더 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-124">It becomes more complex when different operations in a transaction have different isolation levels.</span></span>  
  
 <span data-ttu-id="a1bcc-125">의 트랜잭션 격리 수준에 대 한 일반적인 의미 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 와 잠금에 대 한 의미는 [트랜잭션 격리 수준 설정 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-125">The general semantics of the transaction isolation levels in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], along with the implications on locking, is explained in [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="a1bcc-126">작업마다 다른 격리 수준을 가질 수 있는 크로스 컨테이너 트랜잭션의 경우 개별 읽기 작업의 격리에 대한 의미를 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-126">For cross-container transactions where different operations may have different isolation levels, you need to understand the semantics of isolation of individual read operations.</span></span> <span data-ttu-id="a1bcc-127">쓰기 작업은 항상 격리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-127">Write operations are always isolated.</span></span> <span data-ttu-id="a1bcc-128">다른 트랜잭션의 쓰기는 서로 간에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-128">Writes in different transactions cannot impact each other.</span></span>  
  
 <span data-ttu-id="a1bcc-129">데이터 읽기 작업은 필터 조건을 충족하는 행의 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-129">A data read operation returns a number of rows that satisfy a filter condition.</span></span>  
  
 <span data-ttu-id="a1bcc-130">읽기는 트랜잭션 T의 일부로 수행 됩니다. 읽기 작업의 격리 수준은를 기준으로 이해 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-130">Reads are performed as part of a transaction T. Isolation levels for read operations can be understood in terms of,</span></span>  
  
 <span data-ttu-id="a1bcc-131">커밋 상태</span><span class="sxs-lookup"><span data-stu-id="a1bcc-131">Commit Status</span></span>  
 <span data-ttu-id="a1bcc-132">커밋 상태는 데이터 읽기 커밋이 보증되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-132">Commit status refers to whether the data read is guaranteed to be committed.</span></span>  
  
 <span data-ttu-id="a1bcc-133">(트랜잭션) 일관성</span><span class="sxs-lookup"><span data-stu-id="a1bcc-133">(Transactional) Consistency</span></span>  
 <span data-ttu-id="a1bcc-134">읽기 집합에 대한 트랜잭션 일관성은 행 버전 읽기가 트랜잭션의 정확히 동일한 집합의 업데이트를 포함하도록 보장되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-134">Transactional consistency for a set of reads refers to whether the row versions read are all guaranteed to include updates from precisely the same set of transactions.</span></span>  
  
 <span data-ttu-id="a1bcc-135">안정성은 시스템이 데이터 읽기에 대해 트랜잭션 T에 제공하는 것을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-135">Stability guarantees the system gives to transaction T about the data read.</span></span>  
 <span data-ttu-id="a1bcc-136">안정성은 트랜잭션의 읽기가 반복 가능한 지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-136">Stability refers to whether the transaction's reads are repeatable.</span></span> <span data-ttu-id="a1bcc-137">즉, 읽기가 반복될 때 동일한 행 및 행 버전이 반환되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-137">That is, if the reads were repeated would they return the same rows and row versions?</span></span>  
  
 <span data-ttu-id="a1bcc-138">특정 보증은 트랜잭션의 논리적 종료 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-138">Certain guarantees refer to the logical end time of the transaction.</span></span> <span data-ttu-id="a1bcc-139">일반적으로 논리적 종료 시간은 트랜잭션이 데이터베이스에 커밋되는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-139">In general, the logical end time is the time the transaction is committed to the database.</span></span> <span data-ttu-id="a1bcc-140">메모리 최적화 테이블이 트랜잭션에 의해 액세스되는 경우 논리적 종료 시간은 기술적으로 유효성 검사 단계의 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-140">If memory-optimized tables are accessed by the transaction, the logical end time is technically the beginning of the validation phase.</span></span> <span data-ttu-id="a1bcc-141">(자세한 내용은 메모리 액세스에 [최적화 된 테이블의 트랜잭션에](../relational-databases/in-memory-oltp/memory-optimized-tables.md)있는 트랜잭션 수명 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-141">(For more information, see the transaction lifetime discussion in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="a1bcc-142">격리 수준에 관계없이 트랜잭션(T)은 항상 자체 업데이트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-142">Regardless of isolation level, a transaction (T) always sees its own updates:</span></span>  
  
 <span data-ttu-id="a1bcc-143">READ UNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="a1bcc-143">READ UNCOMMITTED</span></span>  
 <span data-ttu-id="a1bcc-144">데이터 읽기는 커밋, 일관성 또는 안정적 어느 것도 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-144">The data read may neither be committed, consistent, or stable.</span></span> <span data-ttu-id="a1bcc-145">그러나 T에서 수행한 이전의 쓰기 작업을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-145">However, it will include earlier write operations done by T.</span></span>  
  
 <span data-ttu-id="a1bcc-146">READ COMMITTED</span><span class="sxs-lookup"><span data-stu-id="a1bcc-146">READ COMMITTED</span></span>  
 <span data-ttu-id="a1bcc-147">데이터 읽기가 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-147">The data read will be committed.</span></span>  
  
 <span data-ttu-id="a1bcc-148">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="a1bcc-148">SNAPSHOT</span></span>  
 <span data-ttu-id="a1bcc-149">스냅샷 격리에서 T가 수행한 모든 읽기 작업은 트랜잭션의 시작과 동일한 논리적 읽기 시간을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-149">All read operations performed by T under snapshot isolation have the same logical read time, which is the beginning of the transaction.</span></span> <span data-ttu-id="a1bcc-150">데이터 읽기는 반드시 커밋되며 논리적 읽기 시간과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-150">The data read is guaranteed to be committed and consistent as of the logical read time.</span></span> <span data-ttu-id="a1bcc-151">원래 읽기 시간에 읽기를 반복하면 같은 반드시 같은 결과를 반환하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-151">Repeating a read as of the original read time is guaranteed to return the same result.</span></span>  
  
 <span data-ttu-id="a1bcc-152">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="a1bcc-152">REPEATABLE READ</span></span>  
 <span data-ttu-id="a1bcc-153">데이터 읽기는 커밋을 보장하며 트랜잭션의 논리적 종료 시간이 될 때까지 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-153">The data read is guaranteed to be committed and stable up to the logical end time of the transaction.</span></span>  
  
 <span data-ttu-id="a1bcc-154">직렬화 가능</span><span class="sxs-lookup"><span data-stu-id="a1bcc-154">SERIALIZABLE</span></span>  
 <span data-ttu-id="a1bcc-155">에서 수행 하는 모든 직렬화 가능 읽기 작업과 관련 하 여 반복 읽기와 가상 방지 및 트랜잭션 일관성을 보장 합니다. 팬텀 방지는 검색 작업에서 T가 작성 한 추가 행만 반환할 수 있지만 다른 트랜잭션에 의해 기록 된 행은 반환할 수 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-155">All guarantees of REPEATABLE READ plus phantom avoidance and transactional consistency with respect to all serializable read operations performed by T. Phantom avoidance means that the scan operation can only return additional rows that were written by T, but no rows that were written by other transactions.</span></span>  
  
 <span data-ttu-id="a1bcc-156">다음과 같은 트랜잭션이 있다고 합시다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-156">Consider the following transaction,</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 <span data-ttu-id="a1bcc-157">이 트랜잭션은 커밋된 읽기 격리에서 t3의 모든 행을 삭제하고 직렬화 격리 상태에서 t1의 모든 행을 t3으로 복사한 다음 t1과 t3을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-157">This transaction deletes all rows from t3 under read committed isolation, copies all rows from t1 to t3 under serializable isolation, and then compares t1 and t3.</span></span> <span data-ttu-id="a1bcc-158">일부 행[t1에는 없음]은 테이블이 비어 있기 때문에 t3에 추가되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-158">Some rows [not in t1] may have been added to t3 since the table was emptied.</span></span> <span data-ttu-id="a1bcc-159">복사본은 직렬화될 수 있기 때문에 t1에는 행이 추가되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-159">No rows were added to t1 as the copy was serializable.</span></span>  
  
 <span data-ttu-id="a1bcc-160">트랜잭션 끝에 있는 t 1의 읽기는 구문상 읽기 커밋 이지만 직렬화 가능 격리 상태에서 트랜잭션 앞부분에서 읽기를 수행 했기 때문에 실제로는 serialize 할 수 있습니다. 순차성는 트랜잭션의 이후 시점에서 읽기가 수행 될 경우 동일한 행이 반환 되도록 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-160">Although the read from t1 at the end of the transaction is syntactically read committed, it is effectively serializable, because the same read was performed earlier in the transaction under serializable isolation: serializability guarantees that if the read is performed at any later point in the transaction, the same rows are returned.</span></span>  
  
## <a name="cross-container-transactions-and-isolation-levels"></a><span data-ttu-id="a1bcc-161">크로스 컨테이너 트랜잭션 및 격리 수준</span><span class="sxs-lookup"><span data-stu-id="a1bcc-161">Cross-Container Transactions and Isolation Levels</span></span>  
 <span data-ttu-id="a1bcc-162">크로스 컨테이너 트랜잭션은 디스크 기반 측면 (디스크 기반 테이블에 대 한 작업의 경우) 및 메모리 최적화 측면 (메모리 최적화 테이블에 대 한 작업의 경우)의 두 면으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-162">A cross-container transaction can be seen as having two sides: a disk-based side (for operations on disk-based tables) and a memory-optimized side (for operations on memory-optimized tables).</span></span> <span data-ttu-id="a1bcc-163">이러한 두 가지 측면은 다른 격리 수준을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-163">These two sides may have different isolation levels.</span></span> <span data-ttu-id="a1bcc-164">사실, 각 측면에서 개별 읽기 작업마다 다른 격리 수준을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-164">In fact, individual read operations on each side may have different isolation levels.</span></span>  
  
 <span data-ttu-id="a1bcc-165">지정된 트랜잭션 T의 디스크 기반 측면은 다음 조건 중 하나가 충족되는 경우 특정 격리 수준에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-165">The disk-based side of a given transaction T reaches a certain isolation level X if one of the following conditions is met:</span></span>  
  
-   <span data-ttu-id="a1bcc-166">X로 시작 합니다. 즉,를 실행 했기 때문에 세션 기본값은 X이 고 `SET TRANSACTION ISOLATION LEVEL` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-166">It starts in X. That is, the session default was X, either because you executed `SET TRANSACTION ISOLATION LEVEL`, or it is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default.</span></span>  
  
-   <span data-ttu-id="a1bcc-167">트랜잭션 동안 `SET TRANSACTION ISOLATION LEVEL`을 사용하여 기본 격리 수준이 X로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-167">During the transaction, the default isolation level is changed to X using `SET TRANSACTION ISOLATION LEVEL`.</span></span>  
  
-   <span data-ttu-id="a1bcc-168">디스크 기반 테이블의 읽기 작업은 구문 `WITH (X)`를 사용하여 격리 수준 X에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-168">A read operation on a disk-based table is executed under isolation level X, using the syntax `WITH (X)`.</span></span>  
  
 <span data-ttu-id="a1bcc-169">T의 메모리 최적화 측면은 T를 실행하는 동안 메모리 최적화 테이블 또는 고유하게 컴파일된 저장 프로시저의 읽기 작업이 격리 수준 Y에서 실행된 경우 격리 수준 Y에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-169">The memory-optimized side of T reaches an isolation level Y if during execution of T, any read operation on a memory-optimized table or any natively compiled stored procedure is executed under isolation level Y.</span></span>  
  
 <span data-ttu-id="a1bcc-170">한 예로 다음 트랜잭션을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-170">Consider the following transaction as an example.</span></span> <span data-ttu-id="a1bcc-171">여기에서 t1과 t2는 디스크 기반 테이블이고 t3과 t4는 메모리 최적화 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-171">Here, t1 and t2 are disk-based tables and t3 and t4 are memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a1bcc-172">트랜잭션의 디스크 기반 측면은 이 수준에서 시작하므로 격리 수준 커밋된 읽기에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-172">The disk-based side of the transaction reaches the isolation level read committed, because it starts in that level.</span></span> <span data-ttu-id="a1bcc-173">또한 디스크 기반 측면은 첫 번째 읽기 작업이 격리 수준 상태에서 실행되므로 반복 읽기에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-173">The disk-based side also reaches repeatable read, because the first read operation is executed under that isolation level.</span></span> <span data-ttu-id="a1bcc-174">트랜잭션이 끝날 때 커밋된 읽기 격리 수준 상태에서 삭제가 실행되므로 새로운 격리 수준이 도입되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-174">The delete at the end of the transaction is executed under read committed isolation level, and so does not introduce a new isolation level.</span></span>  
  
 <span data-ttu-id="a1bcc-175">트랜잭션의 메모리 최적화 측면은 두 수준 중 하나에 도달할 수 있습니다. 즉, condition1이 true 이면 직렬화 가능 하 고, false 이면 메모리 최적화 쪽은 스냅숏 격리에만 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-175">The memory-optimized side of the transaction can reach one of two levels: if condition1 is true, it reaches serializable, while if it is false, the memory-optimized side reaches only snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a><span data-ttu-id="a1bcc-176">크로스 컨테이너 트랜잭션에 지원되는 격리 수준</span><span class="sxs-lookup"><span data-stu-id="a1bcc-176">Supported Isolation Levels for Cross-Container Transactions</span></span>  
 <span data-ttu-id="a1bcc-177">크로스 컨테이너 트랜잭션의 메모리 최적화 테이블에서 작업에 사용되는 격리 수준에는 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-177">There are limitations on the isolation levels used with operations on memory-optimized tables in cross-container transactions.</span></span>  
  
 <span data-ttu-id="a1bcc-178">메모리 액세스에 최적화된 테이블은 격리 수준 SNAPSHOT, REPEATABLE READ 및 SERIALIZABLE을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-178">Memory-optimized tables support the isolation levels SNAPSHOT, REPEATABLE READ, and SERIALIZABLE.</span></span> <span data-ttu-id="a1bcc-179">자동 커밋 트랜잭션의 경우 메모리 최적화 테이블은 격리 수준 READ COMMITTED를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-179">For autocommit transactions, memory-optimized tables support the isolation level READ COMMITTED.</span></span>  
  
 <span data-ttu-id="a1bcc-180">다음과 같은 시나리오가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-180">The following scenarios are supported:</span></span>  
  
-   <span data-ttu-id="a1bcc-181">READ UNCOMMITTED, READ COMMITTED 및 READ_COMMITTED_SNAPSHOT 크로스 컨테이너 트랜잭션은 SNAPSHOT, REPEATABLE READ 및 SERIALIZABLE 격리 상태에서 메모리 최적화 테이블에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-181">READ UNCOMMITTED, READ COMMITTED, and READ_COMMITTED_SNAPSHOT cross-container transactions can access memory-optimized tables under SNAPSHOT, REPEATABLE READ, and SERIALIZABLE isolation.</span></span> <span data-ttu-id="a1bcc-182">READ COMMITTED 보증이 트랜잭션에 적용되며 트랜잭션에서 읽은 모든 행이 데이터베이스에 커밋되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-182">The READ COMMITTED guarantee holds for the transaction; all rows read by the transaction have been committed to the database.</span></span>  
  
-   <span data-ttu-id="a1bcc-183">REPEATABLE READ 및 SERIALIZABLE 트랜잭션은 SNAPSHOT 격리 상태에서 메모리 최적화 테이블에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-183">REPEATABLE READ and SERIALIZABLE transactions can access memory-optimized tables under SNAPSHOT isolation.</span></span>  
  
## <a name="read-only-cross-container-transactions"></a><span data-ttu-id="a1bcc-184">읽기 전용 크로스 컨테이너 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="a1bcc-184">Read-only Cross-Container Transactions</span></span>  
 <span data-ttu-id="a1bcc-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 있는 대부분의 읽기 전용 트랜잭션은 커밋할 때 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-185">Most read-only transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are rolled back at commit time.</span></span> <span data-ttu-id="a1bcc-186">데이터베이스 커밋에는 변경 내용이 없기 때문에 시스템은 트랜잭션에서 사용한 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-186">Because there are no changes to commit to the database, the system simply frees the resources used by the transaction.</span></span> <span data-ttu-id="a1bcc-187">읽기 전용 디스크 기반 트랜잭션의 경우 트랜잭션이 수행한 모든 잠금이 이 때 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-187">For read-only disk-based transactions, all locks taken by the transaction are released at this time.</span></span> <span data-ttu-id="a1bcc-188">단일의 고유하게 컴파일된 프로시저 실행을 포함하는 읽기 전용 메모리 최적화 트랜잭션의 경우 유효성 검사가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-188">For read-only memory-optimized transactions that span a single natively compiled procedure execution, no validation is performed.</span></span>  
  
 <span data-ttu-id="a1bcc-189">자동 커밋 모드의 크로스 컨테이너 읽기 전용 트랜잭션은 트랜잭션이 끝날 때 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-189">Cross-container, read-only transactions in autocommit mode are simply rolled back at the end of the transaction.</span></span> <span data-ttu-id="a1bcc-190">유효성 검사가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-190">No validation is performed.</span></span>  
  
 <span data-ttu-id="a1bcc-191">명시적 또는 암시적 크로스 컨테이너 읽기 전용 트랜잭션은 REPEATABLE READ 또는 SERIALIZABLE 격리 상태에서 트랜잭션이 메모리 최적화 테이블에 액세스하는 경우 커밋할 때 유효성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-191">Explicit or implicit cross-container, read-only transactions perform validation at commit time if the transaction accesses memory-optimized tables under REPEATABLE READ or SERIALIZABLE isolation.</span></span> <span data-ttu-id="a1bcc-192">유효성 검사에 대 한 자세한 내용은 [메모리 최적화 테이블의 트랜잭션에서](../relational-databases/in-memory-oltp/memory-optimized-tables.md)충돌 검색, 유효성 검사 및 커밋 종속성 확인에 대 한 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1bcc-192">For details about validation see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1bcc-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1bcc-193">See Also</span></span>  
 <span data-ttu-id="a1bcc-194">[메모리 액세스에 최적화 된 테이블의 트랜잭션 이해](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a1bcc-194">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="a1bcc-195">[메모리 액세스에 최적화 된 테이블이 있는 트랜잭션 격리 수준에 대 한 지침](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a1bcc-195">[Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="a1bcc-196">메모리 액세스에 최적화된 테이블의 트랜잭션에 대한 재시도 논리 지침</span><span class="sxs-lookup"><span data-stu-id="a1bcc-196">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
