---
title: SQL Server, Locks 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f13d4ea1172d6b32b90c045a45445c5c87f48a94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647627"
---
# <a name="sql-server-locks-object"></a><span data-ttu-id="630bf-102">SQL Server, Locks 개체</span><span class="sxs-lookup"><span data-stu-id="630bf-102">SQL Server, Locks Object</span></span>
  <span data-ttu-id="630bf-103">Microsoft **의** SQLServer:Locks [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 개별 리소스 유형에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 잠금 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-103">The **SQLServer:Locks** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locks on individual resource types.</span></span> <span data-ttu-id="630bf-104">트랜잭션 동안 읽거나 수정한 행과 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에는 잠금이 설정되어 다른 트랜잭션에서 동시에 리소스를 사용하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-104">Locks are held on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources, such as rows read or modified during a transaction, to prevent concurrent use of resources by different transactions.</span></span> <span data-ttu-id="630bf-105">예를 들어 트랜잭션에 의해 테이블에 있는 행에 배타적(X) 잠금이 설정되어 있다면 잠금을 풀기 전까지는 다른 트랜잭션으로 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-105">For example, if an exclusive (X) lock is held on a row within a table by a transaction, no other transaction can modify that row until the lock is released.</span></span> <span data-ttu-id="630bf-106">잠금을 최소화하면 동시성을 늘려 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-106">Minimizing locks increases concurrency, which can improve performance.</span></span> <span data-ttu-id="630bf-107">**Locks** 개체의 여러 인스턴스는 리소스 유형의 잠금을 나타내는 각 인스턴스와 함께 동시 모니터링이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-107">Multiple instances of the **Locks** object can be monitored at the same time, with each instance representing a lock on a resource type.</span></span>  
  
 <span data-ttu-id="630bf-108">이 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** counters.</span></span>  
  
|<span data-ttu-id="630bf-109">SQL Server Locks 카운터</span><span class="sxs-lookup"><span data-stu-id="630bf-109">SQL Server Locks counters</span></span>|<span data-ttu-id="630bf-110">Description</span><span class="sxs-lookup"><span data-stu-id="630bf-110">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="630bf-111">**Average Wait Time(ms)**</span><span class="sxs-lookup"><span data-stu-id="630bf-111">**Average Wait Time (ms)**</span></span>|<span data-ttu-id="630bf-112">대기한 각 잠금 요청에 대한 평균 대기 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-112">Average amount of wait time (in milliseconds) for each lock request that resulted in a wait.</span></span>|  
|<span data-ttu-id="630bf-113">**Lock Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="630bf-113">**Lock Requests/sec**</span></span>|<span data-ttu-id="630bf-114">잠금 관리자에서 요청한 초당 새 잠금 및 잠금 변환 수입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-114">Number of new locks and lock conversions per second requested from the lock manager.</span></span>|  
|<span data-ttu-id="630bf-115">**Lock Timeouts (timeout > 0)/sec**</span><span class="sxs-lookup"><span data-stu-id="630bf-115">**Lock Timeouts (timeout > 0)/sec**</span></span>|<span data-ttu-id="630bf-116">시간 초과된 초당 잠금 요청 수입니다. 단, 여기에는 NOWAIT 잠금에 대한 요청이 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-116">Number of lock requests per second that timed out, but excluding requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="630bf-117">**Lock Timeouts/sec**</span><span class="sxs-lookup"><span data-stu-id="630bf-117">**Lock Timeouts/sec**</span></span>|<span data-ttu-id="630bf-118">시간 초과된 초당 잠금 요청 수입니다. 여기에는 NOWAIT 잠금에 대한 요청이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-118">Number of lock requests per second that timed out, including requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="630bf-119">**Lock Wait Time(ms)**</span><span class="sxs-lookup"><span data-stu-id="630bf-119">**Lock Wait Time (ms)**</span></span>|<span data-ttu-id="630bf-120">마지막 1초 동안의 잠금에 대한 총 대기 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-120">Total wait time (in milliseconds) for locks in the last second.</span></span>|  
|<span data-ttu-id="630bf-121">**Lock Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="630bf-121">**Lock Waits/sec**</span></span>|<span data-ttu-id="630bf-122">호출자가 기다려야 하는 초당 잠금 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-122">Number of lock requests per second that required the caller to wait.</span></span>|  
|<span data-ttu-id="630bf-123">**Number of Deadlocks/sec**</span><span class="sxs-lookup"><span data-stu-id="630bf-123">**Number of Deadlocks/sec**</span></span>|<span data-ttu-id="630bf-124">교착 상태를 일으킨 초당 잠금 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-124">Number of lock requests per second that resulted in a deadlock.</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="630bf-125">에서 잠글 수 있는 리소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-125">can lock these resources.</span></span>  
  
|<span data-ttu-id="630bf-126">항목</span><span class="sxs-lookup"><span data-stu-id="630bf-126">Item</span></span>|<span data-ttu-id="630bf-127">Description</span><span class="sxs-lookup"><span data-stu-id="630bf-127">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="630bf-128">**_Total**</span><span class="sxs-lookup"><span data-stu-id="630bf-128">**_Total**</span></span>|<span data-ttu-id="630bf-129">모든 잠금 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-129">Information for all locks.</span></span>|  
|<span data-ttu-id="630bf-130">**AllocUnit**</span><span class="sxs-lookup"><span data-stu-id="630bf-130">**AllocUnit**</span></span>|<span data-ttu-id="630bf-131">할당 단위에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-131">A lock on an allocation unit.</span></span>|  
|<span data-ttu-id="630bf-132">**애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="630bf-132">**Application**</span></span>|<span data-ttu-id="630bf-133">애플리케이션이 지정한 리소스에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-133">A lock on an application-specified resource.</span></span>|  
|<span data-ttu-id="630bf-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="630bf-134">**Database**</span></span>|<span data-ttu-id="630bf-135">데이터베이스의 모든 개체를 포함한 데이터베이스에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-135">A lock on a database, including all objects in the database.</span></span>|  
|<span data-ttu-id="630bf-136">**Extent**</span><span class="sxs-lookup"><span data-stu-id="630bf-136">**Extent**</span></span>|<span data-ttu-id="630bf-137">연결된 8페이지 그룹에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-137">A lock on a contiguous group of 8 pages.</span></span>|  
|<span data-ttu-id="630bf-138">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="630bf-138">**File**</span></span>|<span data-ttu-id="630bf-139">데이터베이스 파일에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-139">A lock on a database file.</span></span>|  
|<span data-ttu-id="630bf-140">**Heap/BTree**</span><span class="sxs-lookup"><span data-stu-id="630bf-140">**Heap/BTree**</span></span>|<span data-ttu-id="630bf-141">힙 또는 BTree(HOBT)입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-141">Heap or BTree (HOBT).</span></span> <span data-ttu-id="630bf-142">데이터 페이지의 힙 또는 인덱스의 BTree 구조에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-142">A lock on a heap of data pages, or on the BTree structure of an index.</span></span>|  
|<span data-ttu-id="630bf-143">**Key**</span><span class="sxs-lookup"><span data-stu-id="630bf-143">**Key**</span></span>|<span data-ttu-id="630bf-144">인덱스의 행에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-144">A lock on a row in an index.</span></span>|  
|<span data-ttu-id="630bf-145">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="630bf-145">**Metadata**</span></span>|<span data-ttu-id="630bf-146">메타데이터라고도 하는 카탈로그 정보에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-146">A lock on a piece of catalog information, also called metadata.</span></span>|  
|<span data-ttu-id="630bf-147">**Object**</span><span class="sxs-lookup"><span data-stu-id="630bf-147">**Object**</span></span>|<span data-ttu-id="630bf-148">모든 데이터 및 인덱스를 포함한 테이블, 저장 프로시저, 뷰 등에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-148">A lock on table, stored procedure, view, etc, including all data and indexes.</span></span> <span data-ttu-id="630bf-149">**sys.all_objects**에 항목이 있는 모든 개체가 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-149">The object can be anything that has an entry in **sys.all_objects**.</span></span>|  
|<span data-ttu-id="630bf-150">**호출**</span><span class="sxs-lookup"><span data-stu-id="630bf-150">**Page**</span></span>|<span data-ttu-id="630bf-151">데이터베이스의 8KB 페이지에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-151">A lock on an 8-kilobyte (KB) page in a database.</span></span>|  
|<span data-ttu-id="630bf-152">**RID**</span><span class="sxs-lookup"><span data-stu-id="630bf-152">**RID**</span></span>|<span data-ttu-id="630bf-153">행 ID를 의미하며</span><span class="sxs-lookup"><span data-stu-id="630bf-153">Row ID.</span></span> <span data-ttu-id="630bf-154">힙의 단일 행에 대한 잠금입니다.</span><span class="sxs-lookup"><span data-stu-id="630bf-154">A lock on a single row in a heap.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="630bf-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="630bf-155">See Also</span></span>  
 [<span data-ttu-id="630bf-156">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="630bf-156">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
