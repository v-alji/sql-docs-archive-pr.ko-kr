---
title: 메모리 액세스에 최적화된 개체의 스토리지 만들기 및 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 118e5e582a284023dd8e5cc71629d635e79fb989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649562"
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a><span data-ttu-id="461eb-102">메모리 액세스에 최적화된 개체의 스토리지 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="461eb-102">Creating and Managing Storage for Memory-Optimized Objects</span></span>
  <span data-ttu-id="461eb-103">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 엔진은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 통합되어 있으므로 메모리 최적화 테이블과 기존의 디스크 기반 테이블을 모두 같은 데이터베이스에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-103">The [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine is integrated into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which lets you have both memory-optimized tables and (traditional) disk-based tables in the same database.</span></span> <span data-ttu-id="461eb-104">그러나 메모리 최적화 테이블의 스토리지 구조는 디스크 기반 테이블과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-104">However, the storage structure for memory-optimized tables is different from disk-based tables.</span></span>  
  
 <span data-ttu-id="461eb-105">디스크 기반 테이블용 스토리지의 주요 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-105">Storage for disk-based table has following key attributes:</span></span>  
  
-   <span data-ttu-id="461eb-106">파일이 하나 이상 포함된 파일 그룹에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-106">Mapped to a filegroup and the filegroup contains one or more files.</span></span>  
  
-   <span data-ttu-id="461eb-107">각 파일은 8페이지 익스텐트로 구분되며 각 페이지의 크기는 8,000바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-107">Each file is divided into extents of 8 pages and each page is of size 8K bytes.</span></span>  
  
-   <span data-ttu-id="461eb-108">여러 테이블에서 익스텐트를 공유할 수는 있지만 할당된 페이지와 테이블 또는 인덱스 간에는 일대일 매핑이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-108">An extent can be shared across multiple tables, but a there is 1-to-1 mapping between an allocated page and the table or index.</span></span> <span data-ttu-id="461eb-109">즉, 둘 이상의 테이블이나 인덱스에서 가져온 행을 한 페이지에 포함할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-109">In other words, a page can't have rows from two or more tables or index.</span></span>  
  
-   <span data-ttu-id="461eb-110">데이터는 필요에 따라 메모리(버퍼 풀)로 이동되며 수정되거나 새로 생성된 페이지는 디스크에 비동기로 기록되므로 대개 임의의 IO가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-110">The data is moved into memory (the buffer pool) as needed and the modified or newly created pages are asynchronously written to the disk generating mostly random IO.</span></span>  
  
 <span data-ttu-id="461eb-111">메모리 최적화 테이블용 스토리지의 주요 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-111">Storage for memory-optimized tables has following key attributes:</span></span>  
  
-   <span data-ttu-id="461eb-112">메모리 최적화 모든 테이블은 메모리 최적화 파일 그룹에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-112">All memory-optimized tables are mapped to a memory-optimized filegroup.</span></span> <span data-ttu-id="461eb-113">이 파일 그룹은 파일 스트림 파일 그룹을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-113">This filegroup is built using the filestream filegroup.</span></span>  
  
-   <span data-ttu-id="461eb-114">페이지는 없으며 데이터는 행으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-114">There are no pages and the data is persisted as a row.</span></span>  
  
-   <span data-ttu-id="461eb-115">메모리 최적화 테이블의 모든 변경 내용은 활성 파일에 추가되는 방식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-115">All changes to memory-optimized tables are stored by appending to active files.</span></span> <span data-ttu-id="461eb-116">파일 읽기와 파일에 쓰기는 모두 순차적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-116">Both reading and writing to files is sequential.</span></span>  
  
-   <span data-ttu-id="461eb-117">업데이트는 삭제 후 삽입으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-117">An update is implemented as a delete followed by an insert.</span></span> <span data-ttu-id="461eb-118">삭제된 행은 스토리지에서 즉시 제거되지 않으며,</span><span class="sxs-lookup"><span data-stu-id="461eb-118">The deleted rows are not immediately removed from the storage.</span></span> <span data-ttu-id="461eb-119">삭제된 행은 [메모리 액세스에 최적화된 테이블에 대한 내구성](memory-optimized-tables.md)에서 설명한 대로 정책을 기반으로 하여 MERGE라는 백그라운드 프로세스를 통해 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-119">The deleted rows are removed by a background process, called MERGE, based on a policy as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
-   <span data-ttu-id="461eb-120">디스크 기반 테이블과 달리 메모리 최적화 테이블용 스토리지는 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-120">Unlike disk-based tables, storage for memory-optimized tables is not compressed.</span></span> <span data-ttu-id="461eb-121">압축된(ROW 또는 PAGE) 디스크 기반 테이블을 메모리 최적화 테이블로 마이그레이션할 때는 크기 변경을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-121">When migrating a compressed (ROW or PAGE) disk-based table to memory-optimized table, you will need to account for the change in size.</span></span>  
  
-   <span data-ttu-id="461eb-122">메모리 최적화 테이블은 지속형일 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-122">A memory-optimized table can be durable or can be non-durable.</span></span> <span data-ttu-id="461eb-123">메모리 액세스에 최적화된 내구성이 있는 테이블의 스토리지만 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-123">You only need to configure storage for durable memory-optimize tables.</span></span>  
  
 <span data-ttu-id="461eb-124">이 섹션에서는 검사점 파일 쌍 외에도 메모리 최적화 테이블의 데이터가 저장되는 방법의 다른 측면에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="461eb-124">This section describes checkpoint file pairs and other aspects of how data in memory-optimized tables is stored.</span></span>  
  
 <span data-ttu-id="461eb-125">이 섹션의 항목:</span><span class="sxs-lookup"><span data-stu-id="461eb-125">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="461eb-126">메모리 액세스에 최적화된 테이블 스토리지 구성</span><span class="sxs-lookup"><span data-stu-id="461eb-126">Configuring Storage for Memory-Optimized Tables</span></span>](configuring-storage-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="461eb-127">메모리 액세스에 최적화된 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="461eb-127">The Memory Optimized Filegroup</span></span>](the-memory-optimized-filegroup.md)  
  
-   [<span data-ttu-id="461eb-128">메모리 액세스에 최적화된 테이블에 대한 내구성</span><span class="sxs-lookup"><span data-stu-id="461eb-128">Durability for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
-   [<span data-ttu-id="461eb-129">메모리 액세스에 최적화된 테이블에 대한 검사점 작업</span><span class="sxs-lookup"><span data-stu-id="461eb-129">Checkpoint Operation for Memory-Optimized Tables</span></span>](checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="461eb-130">메모리 액세스에 최적화된 개체에 대한 내구성 정의</span><span class="sxs-lookup"><span data-stu-id="461eb-130">Defining Durability for Memory-Optimized Objects</span></span>](defining-durability-for-memory-optimized-objects.md)  
  
-   [<span data-ttu-id="461eb-131">디스크 기반 테이블 스토리지와 메모리 액세스에 최적화된 테이블 스토리지 비교</span><span class="sxs-lookup"><span data-stu-id="461eb-131">Comparing Disk-Based Table Storage to Memory-Optimized Table Storage</span></span>](comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
-   [<span data-ttu-id="461eb-132">데이터 및 델타 파일 쌍에 대한 병합 모니터링 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="461eb-132">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>](../../database-engine/monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs.md)  
  
## <a name="see-also"></a><span data-ttu-id="461eb-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="461eb-133">See Also</span></span>  
 [<span data-ttu-id="461eb-134">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="461eb-134">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
