---
title: 메모리 액세스에 최적화 된 테이블의 트랜잭션 이해 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0671bba8b7a0bda27ea27cf059cb9e3b1bb87b2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732891"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a><span data-ttu-id="426d2-102">메모리 액세스에 최적화된 테이블의 트랜잭션 이해</span><span class="sxs-lookup"><span data-stu-id="426d2-102">Understanding Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="426d2-103">트랜잭션은 낙관적 동시 버전 동시성 제어의 형태를 사용하여 메모리 최적화 테이블에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-103">Transactions access memory-optimized tables using a form of optimistic, multi-version concurrency control.</span></span> <span data-ttu-id="426d2-104">즉, 데이터의 서로 다른 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-104">This means that there are different versions of the data.</span></span> <span data-ttu-id="426d2-105">각 트랜잭션은 동시에 실행 중인 다른 트랜잭션에 독립적이면서 트랜잭션 측면에서 데이터베이스 자체의 일관된 버전에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-105">Each transaction operates on its own transactionally consistent version of the database, independent from other concurrently running transactions.</span></span> <span data-ttu-id="426d2-106">뿐만 아니라 트랜잭션은 다른 동시 트랜잭션과 충돌이 없을 것이라는 낙관적 가정 하에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-106">In addition, transactions operate under the optimistic assumption that there will be no conflicts with other, concurrent, transactions.</span></span> <span data-ttu-id="426d2-107">이렇게 하면 잠금을 사용할 필요가 없지만 시스템이 충돌을 감지하고 충돌하는 트랜잭션 중 하나를 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-107">This avoids the need to use locks, but does require the system to detect conflicts and terminate one of the conflicting transactions.</span></span> <span data-ttu-id="426d2-108">충돌은 쓰기-쓰기 트랜잭션 및 읽기-쓰기 트랜잭션에 대해서만 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-108">Conflicts can occur only for write-write transactions and for read-write transactions.</span></span> <span data-ttu-id="426d2-109">쓰기-쓰기 충돌이 발생할 경우 쓰기 트랜잭션 하나가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-109">If there is a write-write conflict, one write transaction is terminated.</span></span>  
  
 <span data-ttu-id="426d2-110">메모리 최적화 테이블의 동시성 제어와 디스크 기반 테이블의 READ_COMMITTED_SNAPSHOT 및 SNAPSHOT 트랜잭션 격리 수준에 대한 동시성 제어 사이에는 유사성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-110">There are similarities between the concurrency control for memory-optimized tables and the concurrency control for disk-based tables for the READ_COMMITTED_SNAPSHOT and SNAPSHOT transaction isolation levels.</span></span> <span data-ttu-id="426d2-111">디스크 기반 테이블에 대 한 자세한 내용은 [데이터베이스 엔진의 행 버전 관리 기반 격리 수준](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="426d2-111">(For more information about disk-based tables, see [Row Versioning-based Isolation Levels in the Database Engine](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)</span></span>  
  
## <a name="topics-in-this-section"></a><span data-ttu-id="426d2-112">이 섹션의 항목</span><span class="sxs-lookup"><span data-stu-id="426d2-112">Topics in This Section</span></span>  
 <span data-ttu-id="426d2-113">메모리 최적화 테이블의 트랜잭션에 대한 이 섹션에는 다음 항목들이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="426d2-113">This section on transactions in memory-optimized tables includes the following topics:</span></span>  
  
-   [<span data-ttu-id="426d2-114">메모리 액세스에 최적화된 테이블의 트랜잭션 격리 수준에 대한 지침</span><span class="sxs-lookup"><span data-stu-id="426d2-114">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [<span data-ttu-id="426d2-115">메모리 액세스에 최적화된 테이블의 트랜잭션에 대한 재시도 논리 지침</span><span class="sxs-lookup"><span data-stu-id="426d2-115">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="426d2-116">메모리 액세스에 최적화된 테이블의 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="426d2-116">Transactions in Memory-Optimized Tables</span></span>](transactions-in-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="426d2-117">트랜잭션 격리 수준</span><span class="sxs-lookup"><span data-stu-id="426d2-117">Transaction Isolation Levels</span></span>](transaction-isolation-levels.md)  
  
-   [<span data-ttu-id="426d2-118">크로스 컨테이너 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="426d2-118">Cross-Container Transactions</span></span>](cross-container-transactions.md)  
  
 <span data-ttu-id="426d2-119">자세한 내용은 [트랜잭션 내구성 제어](../relational-databases/logs/control-transaction-durability.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="426d2-119">For more information, see [Control Transaction Durability](../relational-databases/logs/control-transaction-durability.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426d2-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="426d2-120">See Also</span></span>  
 [<span data-ttu-id="426d2-121">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="426d2-121">Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
