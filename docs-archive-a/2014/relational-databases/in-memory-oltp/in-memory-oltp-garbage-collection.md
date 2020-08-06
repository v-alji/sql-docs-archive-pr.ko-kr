---
title: 메모리 내 OLTP 가비지 수집 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 23997d3664fb48902d2be08bbb22d2189c832298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739981"
---
# <a name="in-memory-oltp-garbage-collection"></a><span data-ttu-id="622fa-102">메모리 내 OLTP 가비지 수집</span><span class="sxs-lookup"><span data-stu-id="622fa-102">In-Memory OLTP Garbage Collection</span></span>
  <span data-ttu-id="622fa-103">데이터 행은 더 이상 활성화되지 않는 트랜잭션에서 삭제된 경우 유효하지 않은 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-103">A data row is considered stale if it was deleted by a transaction that is no longer active.</span></span> <span data-ttu-id="622fa-104">유효하지 않은 행에는 가비지 수집을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-104">A stale row is eligible for garbage collection.</span></span> <span data-ttu-id="622fa-105">[!INCLUDE[hek_2](../../includes/hek-2-md.md)]에서 가비지 수집의 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-105">The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span></span>  
  
-   <span data-ttu-id="622fa-106">비중단.</span><span class="sxs-lookup"><span data-stu-id="622fa-106">Non-blocking.</span></span> <span data-ttu-id="622fa-107">가비지 수집은 시간이 지남에 따라 작업에 미치는 영향을 최소화하면서 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-107">Garbage collection is distributed over time with minimal impact on the workload.</span></span>  
  
-   <span data-ttu-id="622fa-108">공동.</span><span class="sxs-lookup"><span data-stu-id="622fa-108">Cooperative.</span></span> <span data-ttu-id="622fa-109">사용자 트랜잭션이 기본 가비지 수집 스레드와 함께 가비지 수집에 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-109">User transactions participate in garbage collection with main garbage-collection thread.</span></span>  
  
-   <span data-ttu-id="622fa-110">효율.</span><span class="sxs-lookup"><span data-stu-id="622fa-110">Efficient.</span></span> <span data-ttu-id="622fa-111">사용자 트랜잭션은 사용 중인 액세스 경로(인덱스)에서 유효하지 않은 행의 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-111">User transactions delink stale rows in the access path (the index) being used.</span></span> <span data-ttu-id="622fa-112">이로 인해 행이 최종적으로 제거되면 필요한 작업을 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-112">This reduces the work required when the row is finally removed.</span></span>  
  
-   <span data-ttu-id="622fa-113">응답.</span><span class="sxs-lookup"><span data-stu-id="622fa-113">Responsive.</span></span> <span data-ttu-id="622fa-114">메모리 가중에 따라 적극적인 가비지 수집을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-114">Memory pressure leads to aggressive garbage collection.</span></span>  
  
-   <span data-ttu-id="622fa-115">확장 가능.</span><span class="sxs-lookup"><span data-stu-id="622fa-115">Scalable.</span></span> <span data-ttu-id="622fa-116">커밋 후 사용자 트랜잭션에서 가비지 수집 작업 중 일부를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-116">After commit, user transactions do part of the work of garbage collection.</span></span> <span data-ttu-id="622fa-117">트랜잭션 활동이 많을수록 더 많은 트랜잭션에서 유효하지 않은 행의 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-117">The more transaction activity, the more the transactions delink stale rows.</span></span>  
  
 <span data-ttu-id="622fa-118">가비지 수집은 기본 가비지 수집 스레드에서 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-118">Garbage collection is controlled by the main garbage collection thread.</span></span> <span data-ttu-id="622fa-119">기본 가비지 수집 스레드는 매분 또는 커밋된 트랜잭션 수가 내부 임계값을 초과할 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-119">The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold.</span></span> <span data-ttu-id="622fa-120">가비지 수집의 태스크는 다음을 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-120">The task of the garbage collector is to:</span></span>  
  
-   <span data-ttu-id="622fa-121">행 집합을 삭제하거나 업데이트하는 트랜잭션 및 가장 오래된 활성 트랜잭션 전에 커밋된 트랜잭션을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-121">Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.</span></span>  
  
-   <span data-ttu-id="622fa-122">이러한 이전 트랜잭션에서 생성된 행 버전을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-122">Identity row versions created by these old transactions.</span></span>  
  
-   <span data-ttu-id="622fa-123">각각 16행으로 구성된 하나 이상의 단위로 이전 행을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-123">Group old rows into one or more units of 16 rows each.</span></span> <span data-ttu-id="622fa-124">이 작업은 가비지 수집기의 작업을 더 작은 단위로 분배하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-124">This is done to distribute the work of the garbage collector into smaller units.</span></span>  
  
-   <span data-ttu-id="622fa-125">이러한 작업 단위를 각 스케줄러의 가비지 수집 큐로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-125">Move these work units into the garbage collection queue, one for each scheduler.</span></span> <span data-ttu-id="622fa-126">자세한 내용은 다음 가비지 수집기 DMV를 참조하세요. [sys.dm_xtp_gc_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql) 및 [sys.dm_xtp_gc_queue_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="622fa-126">Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql), and [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="622fa-127">사용자 트랜잭션은 커밋 후 실행에 사용된 스케줄러와 연결된 큐에서 모든 큐 항목을 식별한 다음 메모리를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-127">After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory.</span></span> <span data-ttu-id="622fa-128">스케줄러에서 가비지 수집 큐가 비어 있으면 현재 NUMA 노드에서 비어 있지 않은 큐를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-128">If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node.</span></span> <span data-ttu-id="622fa-129">트랜잭션 활동이 적고 메모리 가중이 있는 경우 기본 가비지 수집기 스레드가 개입하여 어떤 큐에서든 행의 가비지 수집에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-129">If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue.</span></span> <span data-ttu-id="622fa-130">예를 들어 많은 수의 행을 삭제한 후 트랜잭션 활동이 없고 메모리 가중이 없는 경우 트랜잭션 활동이 다시 시작되거나 메모리 가중이 있을 때까지 삭제된 행에서 가비지를 수집하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="622fa-130">If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622fa-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="622fa-131">See Also</span></span>  
 [<span data-ttu-id="622fa-132">메모리 내 OLTP의 메모리 관리</span><span class="sxs-lookup"><span data-stu-id="622fa-132">Managing Memory for In-Memory OLTP</span></span>](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  
