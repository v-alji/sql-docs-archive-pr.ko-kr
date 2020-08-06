---
title: 해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: rothja
ms.author: jroth
ms.openlocfilehash: af4b3ca7731e7ca13e697f43e76ac3cc3cacb4f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653860"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a><span data-ttu-id="61027-102">해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스</span><span class="sxs-lookup"><span data-stu-id="61027-102">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>
  <span data-ttu-id="61027-103">단지 몇 가지 예외를 제외하고 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 또는 DML 작업(SELECT, INSERT, UPDATE 또는 DELETE), 임시 일괄 처리, 테이블 반환 함수, 트리거, 뷰 및 저장 프로시저와 같은 SQL 모듈을 사용하여 메모리 최적화 테이블에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-103">With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../includes/tsql-md.md)] query or DML operation (SELECT, INSERT, UPDATE, or DELETE), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.</span></span>  
  
 <span data-ttu-id="61027-104">해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리 또는 고유하게 컴파일된 저장 프로시저가 아닌 저장 프로시저를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="61027-104">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] refers to [!INCLUDE[tsql](../../includes/tsql-md.md)] batches or stored procedures other than a natively compiled stored procedure.</span></span> <span data-ttu-id="61027-105">메모리 최적화 테이블에 대한 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스를 interop 액세스라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="61027-105">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access to memory-optimized tables is referred to as interop access.</span></span>  
  
 <span data-ttu-id="61027-106">메모리 액세스에 최적화된 테이블은 고유하게 컴파일된 저장 프로시저를 사용하여 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-106">Memory-optimized tables can also be accessed using a natively compiled stored procedure.</span></span> <span data-ttu-id="61027-107">고유하게 컴파일된 저장 프로시저는 성능이 중요한 OLTP 작업에 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="61027-107">Natively compiled stored procedures are recommended for performance-critical OLTP operations.</span></span>  
  
 <span data-ttu-id="61027-108">해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스는 다음과 같은 시나리오에 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="61027-108">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access is recommended for these scenarios:</span></span>  
  
-   <span data-ttu-id="61027-109">임시 쿼리 및 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="61027-109">Ad hoc queries and administrative tasks.</span></span>  
  
-   <span data-ttu-id="61027-110">고유하게 컴파일된 저장 프로시저(예: 창 함수)에서 사용할 수 없는 구문을 일반적으로 사용하는 보고 쿼리</span><span class="sxs-lookup"><span data-stu-id="61027-110">Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as window functions).</span></span>  
  
-   <span data-ttu-id="61027-111">애플리케이션 코드를 최소한으로 변경하거나 변경하지 않고 애플리케이션에서 성능이 중요한 부분을 메모리 최적화 테이블로 마이그레이션하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="61027-111">To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes.</span></span> <span data-ttu-id="61027-112">테이블을 마이그레이션하면 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-112">You can potentially see performance improvements from migrating tables.</span></span> <span data-ttu-id="61027-113">그런 다음 저장 프로시저를 고유하게 컴파일된 저장 프로시저로 마이그레이션하면 성능이 추가로 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-113">If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.</span></span>  
  
-   <span data-ttu-id="61027-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 고유하게 컴파일된 저장 프로시저에 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="61027-114">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is not available for natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="61027-115">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 메모리 최적화 테이블의 데이터에 액세스하는 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-115">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures that access data in a memory-optimized table.</span></span>  
  
|<span data-ttu-id="61027-116">영역</span><span class="sxs-lookup"><span data-stu-id="61027-116">Area</span></span>|<span data-ttu-id="61027-117">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="61027-117">Unsupported</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="61027-118">테이블에 대한 액세스</span><span class="sxs-lookup"><span data-stu-id="61027-118">Access to tables</span></span>|<span data-ttu-id="61027-119">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="61027-119">TRUNCATE TABLE</span></span><br /><br /> <span data-ttu-id="61027-120">MERGE(메모리 최적화 테이블을 대상으로 사용)</span><span class="sxs-lookup"><span data-stu-id="61027-120">MERGE (memory-optimized table as target)</span></span><br /><br /> <span data-ttu-id="61027-121">동적 및 키 집합 커서(자동으로 정적 커서로 강등됨)</span><span class="sxs-lookup"><span data-stu-id="61027-121">Dynamic and keyset cursors (these automatically degrade to static).</span></span><br /><br /> <span data-ttu-id="61027-122">컨텍스트 연결을 사용하여 CLR 모듈에서 액세스</span><span class="sxs-lookup"><span data-stu-id="61027-122">Access from CLR modules, using the context connection.</span></span><br /><br /> <span data-ttu-id="61027-123">인덱싱된 뷰에서 메모리 최적화 테이블 참조</span><span class="sxs-lookup"><span data-stu-id="61027-123">Referencing a memory-optimized table from an indexed view.</span></span>|  
|<span data-ttu-id="61027-124">데이터베이스 간</span><span class="sxs-lookup"><span data-stu-id="61027-124">Cross-database</span></span>|<span data-ttu-id="61027-125">데이터베이스 간 쿼리</span><span class="sxs-lookup"><span data-stu-id="61027-125">Cross-database queries</span></span><br /><br /> <span data-ttu-id="61027-126">데이터베이스 간 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="61027-126">Cross-database transactions</span></span><br /><br /> <span data-ttu-id="61027-127">연결된 서버</span><span class="sxs-lookup"><span data-stu-id="61027-127">Linked servers</span></span>|  
  
## <a name="table-hints"></a><span data-ttu-id="61027-128">테이블 힌트</span><span class="sxs-lookup"><span data-stu-id="61027-128">Table Hints</span></span>  
 <span data-ttu-id="61027-129">테이블 힌트에 대한 자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="61027-129">For more information about table hints, see.</span></span> <span data-ttu-id="61027-130">[테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="61027-130">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span> <span data-ttu-id="61027-131">[!INCLUDE[hek_2](../../includes/hek-2-md.md)]를 지원하기 위해 SNAPSHOT 격리가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-131">SNAPSHOT isolation was added to support [!INCLUDE[hek_2](../../includes/hek-2-md.md)].</span></span>  
  
 <span data-ttu-id="61027-132">다음 테이블 힌트는 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 메모리 최적화 테이블에 액세스하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-132">The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="61027-133">HOLDLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-133">HOLDLOCK</span></span>|<span data-ttu-id="61027-134">IGNORE_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="61027-134">IGNORE_CONSTRAINTS</span></span>|<span data-ttu-id="61027-135">IGNORE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="61027-135">IGNORE_TRIGGERS</span></span>|<span data-ttu-id="61027-136">NOWAIT</span><span class="sxs-lookup"><span data-stu-id="61027-136">NOWAIT</span></span>|  
|<span data-ttu-id="61027-137">PAGLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-137">PAGLOCK</span></span>|<span data-ttu-id="61027-138">READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="61027-138">READCOMMITTED</span></span>|<span data-ttu-id="61027-139">READCOMMITTEDLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-139">READCOMMITTEDLOCK</span></span>|<span data-ttu-id="61027-140">READPAST</span><span class="sxs-lookup"><span data-stu-id="61027-140">READPAST</span></span>|  
|<span data-ttu-id="61027-141">READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="61027-141">READUNCOMMITTED</span></span>|<span data-ttu-id="61027-142">ROWLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-142">ROWLOCK</span></span>|<span data-ttu-id="61027-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span><span class="sxs-lookup"><span data-stu-id="61027-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span></span>|<span data-ttu-id="61027-144">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-144">TABLOCK</span></span>|  
|<span data-ttu-id="61027-145">TABLOCKXX</span><span class="sxs-lookup"><span data-stu-id="61027-145">TABLOCKXX</span></span>|<span data-ttu-id="61027-146">UPDLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-146">UPDLOCK</span></span>|<span data-ttu-id="61027-147">XLOCK</span><span class="sxs-lookup"><span data-stu-id="61027-147">XLOCK</span></span>||  
  
 <span data-ttu-id="61027-148">해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 명시적 또는 암시적 트랜잭션으로부터 메모리 최적화 테이블에 액세스할 때 SNAPSHOT, REPEATABLEREAD, SERIALIZABLE 등의 격리 수준 테이블 힌트 중 하나를 포함해야 합니다. 또는 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT을 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="61027-148">When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] you must include either an isolation level table hint such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE, or you can use MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span></span> <span data-ttu-id="61027-149">자세한 내용은 [메모리 최적화 테이블을 사용 하는 트랜잭션 격리 수준에 대 한 지침](memory-optimized-tables.md) 및 [Transact-sql&#41;&#40;ALTER database SET 옵션 ](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="61027-149">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](memory-optimized-tables.md) and [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61027-150">자동 커밋 모드에서 실행되는 쿼리에서 액세스하는 메모리 최적화 테이블에는 격리 수준 테이블 힌트가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="61027-150">An isolation level table hint is not required for memory-optimized tables accessed by queries running in auto-commit mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61027-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61027-151">See Also</span></span>  
 <span data-ttu-id="61027-152">[메모리 내 OLTP에 대한 Transact-SQL 지원](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="61027-152">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="61027-153">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="61027-153">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
