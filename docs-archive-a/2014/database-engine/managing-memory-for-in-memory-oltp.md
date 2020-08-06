---
title: 메모리 내 OLTP에 대 한 메모리 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90f9b638697d59a0a573a9a31c0a5faade23e870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738686"
---
# <a name="managing-memory-for-in-memory-oltp"></a><span data-ttu-id="911ce-102">메모리 내 OLTP의 메모리 관리</span><span class="sxs-lookup"><span data-stu-id="911ce-102">Managing Memory for In-Memory OLTP</span></span>
  <span data-ttu-id="911ce-103">메모리 액세스에 최적화된 테이블을 사용하려면 모든 행과 인덱스를 메모리 내에 유지하는 데 충분한 메모리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-103">Memory-optimized tables require that sufficient memory exist to keep all of the rows and indexes in memory.</span></span> <span data-ttu-id="911ce-104">메모리는 한정된 리소스이므로 시스템에서 메모리 사용량을 파악하고 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-104">Because memory is a finite resource, it is important that you understand and manage memory usage on your system.</span></span> <span data-ttu-id="911ce-105">이 섹션의 항목에서는 일반적인 메모리 사용 및 관리 시나리오를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-105">The topics in this section cover common memory use and management scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="911ce-106">단원 내용</span><span class="sxs-lookup"><span data-stu-id="911ce-106">In this section</span></span>  
  
|<span data-ttu-id="911ce-107">섹션</span><span class="sxs-lookup"><span data-stu-id="911ce-107">Section</span></span>|<span data-ttu-id="911ce-108">Description</span><span class="sxs-lookup"><span data-stu-id="911ce-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="911ce-109">메모리 액세스에 최적화된 테이블에 필요한 메모리 예측</span><span class="sxs-lookup"><span data-stu-id="911ce-109">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|<span data-ttu-id="911ce-110">테이블의 메모리 요구 사항을 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-110">Estimate a table's memory needs.</span></span>|  
|[<span data-ttu-id="911ce-111">메모리 액세스에 최적화된 테이블이 있는 데이터베이스를 리소스 풀에 바인딩</span><span class="sxs-lookup"><span data-stu-id="911ce-111">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|<span data-ttu-id="911ce-112">데이터베이스를 리소스 풀과 바인딩하기 위한 단계별 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-112">Step by step walkthrough to bind a database with a resource pool.</span></span>|  
|[<span data-ttu-id="911ce-113">메모리 사용량 모니터링 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="911ce-113">Monitor and Troubleshoot Memory Usage</span></span>](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|<span data-ttu-id="911ce-114">메모리 사용량을 모니터링하는 데 사용할 수 있는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-114">Tools you can use to monitor your memory usage.</span></span> <span data-ttu-id="911ce-115">메모리 사용량이 너무 증가하는 경우 문제 해결도 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-115">Also covers troubleshooting if memory usage gets too high.</span></span>|  
|[<span data-ttu-id="911ce-116">메모리 부족 문제 해결</span><span class="sxs-lookup"><span data-stu-id="911ce-116">Resolve Out Of Memory Issues</span></span>](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|<span data-ttu-id="911ce-117">OOM(메모리 부족) 상황에서 복구하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-117">Steps to recover from an OOM (Out of Memory) situation.</span></span>|  
|[<span data-ttu-id="911ce-118">데이터베이스를 복원하여 리소스 풀에 바인딩</span><span class="sxs-lookup"><span data-stu-id="911ce-118">Restore a Database and Bind it to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|<span data-ttu-id="911ce-119">[!INCLUDE[hek_2](../includes/hek-2-md.md)] 데이터베이스를 복원하고 명명된 리소스 풀에 바인딩하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-119">Steps to restore an [!INCLUDE[hek_2](../includes/hek-2-md.md)] database and bind it to a named resource pool.</span></span>|  
|[<span data-ttu-id="911ce-120">메모리 내 OLTP 가비지 수집</span><span class="sxs-lookup"><span data-stu-id="911ce-120">In-Memory OLTP Garbage Collection</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|<span data-ttu-id="911ce-121">삭제된 행에서 가비지 수집이 작동하는 방법을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="911ce-121">Understand how garbage collection operates on deleted rows.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="911ce-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="911ce-122">See Also</span></span>  
 [<span data-ttu-id="911ce-123">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="911ce-123">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
