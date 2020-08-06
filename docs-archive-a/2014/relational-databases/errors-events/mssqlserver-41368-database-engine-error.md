---
title: MSSQLSERVER_41368 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 10e187223a3f35b4b21ede6965e3c9efea2e30c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731628"
---
# <a name="mssqlserver_41368"></a><span data-ttu-id="bbd03-102">MSSQLSERVER_41368</span><span class="sxs-lookup"><span data-stu-id="bbd03-102">MSSQLSERVER_41368</span></span>
    
## <a name="details"></a><span data-ttu-id="bbd03-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="bbd03-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbd03-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="bbd03-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="bbd03-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="bbd03-105">Event ID</span></span>|<span data-ttu-id="bbd03-106">41368</span><span class="sxs-lookup"><span data-stu-id="bbd03-106">41368</span></span>|  
|<span data-ttu-id="bbd03-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="bbd03-107">Event Source</span></span>|<span data-ttu-id="bbd03-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bbd03-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bbd03-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="bbd03-109">Component</span></span>|<span data-ttu-id="bbd03-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bbd03-110">SQLEngine</span></span>|  
|<span data-ttu-id="bbd03-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="bbd03-111">Symbolic Name</span></span>|<span data-ttu-id="bbd03-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="bbd03-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="bbd03-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="bbd03-113">Message Text</span></span>|<span data-ttu-id="bbd03-114">READ COMMITTED 격리 수준을 사용한 메모리 액세스에 최적화된 테이블 액세스는 자동 커밋 트랜잭션에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-114">Accessing memory optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="bbd03-115">명시적 또는 암시적 트랜잭션에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-115">It is not supported for explicit or implicit transactions.</span></span> <span data-ttu-id="bbd03-116">WITH (SNAPSHOT) 같은 테이블 힌트를 사용하여 메모리 액세스에 최적화된 테이블에 대해 지원되는 격리 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-116">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bbd03-117">설명</span><span class="sxs-lookup"><span data-stu-id="bbd03-117">Explanation</span></span>  
 <span data-ttu-id="bbd03-118">READ COMMITTED 격리 수준을 사용한 메모리 최적화 테이블 액세스는 자동 커밋 트랜잭션에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-118">Accessing memory-optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="bbd03-119">자세한 내용은 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bbd03-119">For more information, see [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).</span></span>  
  
 <span data-ttu-id="bbd03-120">BEGIN TRANSACTION으로 시작된 명시적 트랜잭션에서 메모리 최적화 테이블에 액세스할 때 IMPLICIT_TRANSACTIONS가 ON으로 설정되어 있으면 READ COMMITTED 격리 수준이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-120">When accessing a memory-optimized table from an explicit transaction that was started with BEGIN TRANSACTION, or from an implicit transaction, if IMPLICIT_TRANSACTIONS is set to ON, the READ COMMITTED isolation level is not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bbd03-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="bbd03-121">User Action</span></span>  
 <span data-ttu-id="bbd03-122">명시적 또는 암시적 READ COMMITTED 트랜잭션에서 메모리 최적화 테이블에 액세스할 때는 SNAPSHOT을 사용하여 테이블에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd03-122">When accessing a memory-optimized table from an explicit or implicit READ COMMITTED transaction, use SNAPSHOT to access the table.</span></span> <span data-ttu-id="bbd03-123">이는 테이블 힌트 WITH (SNAPSHOT)을 사용 하 여 수행할 수 있습니다. 자세한 내용은 [메모리 최적화 테이블을 사용 하는 트랜잭션 격리 수준에 대 한 지침](../in-memory-oltp/memory-optimized-tables.md)을 참조 하거나 데이터베이스 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT 옵션을 ON으로 설정 하 여 수행할 수 있습니다. 자세한 내용은 [ALTER database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bbd03-123">This can be achieved by using the table hint WITH (SNAPSHOT) (for more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md)) or by setting the database option MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT to ON (for more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd03-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbd03-124">See Also</span></span>  
 [<span data-ttu-id="bbd03-125">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="bbd03-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
