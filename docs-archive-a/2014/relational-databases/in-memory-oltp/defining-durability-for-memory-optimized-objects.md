---
title: 메모리 액세스에 최적화된 개체에 대한 내구성 정의 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 325f50a74ea75270dd62fc3564200c59255dc6cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648374"
---
# <a name="defining-durability-for-memory-optimized-objects"></a><span data-ttu-id="b6398-102">메모리 액세스에 최적화된 개체에 대한 내구성 정의</span><span class="sxs-lookup"><span data-stu-id="b6398-102">Defining Durability for Memory-Optimized Objects</span></span>
  <span data-ttu-id="b6398-103">메모리 내 OLTP는 완전한 ACID(원자성, 일관성, 격리 및 내구성) 속성을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-103">In-Memory OLTP guarantees full atomicity, consistency, isolation, and full durability (ACID) properties.</span></span> <span data-ttu-id="b6398-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 메모리 최적화 테이블의 컨텍스트에서 내구성은 다음과 같은 보증을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-104">Durability in the context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and memory-optimized tables provides following guarantees:</span></span>  
  
 <span data-ttu-id="b6398-105">트랜잭션 내구성</span><span class="sxs-lookup"><span data-stu-id="b6398-105">Transactional Durability</span></span>  
 <span data-ttu-id="b6398-106">메모리 최적화 테이블에 DDL 또는 DML 변경을 적용한 완전한 내구성이 있는 트랜잭션을 커밋하면 메모리 최적화 내구성이 있는 테이블에 적용한 이 변경은 영구적이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-106">When you commit a fully durable transaction that made (DDL or DML) changes to a memory-optimized table, the changes made to a durable memory-optimized table are permanent.</span></span>  
  
 <span data-ttu-id="b6398-107">지연된 내구성이 있는 트랜잭션을 메모리 최적화 테이블로 커밋하면 메모리 내 트랜잭션 로그가 디스크에 저장된 이후에만 트랜잭션이 내구성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-107">When you commit a delayed durable transaction to a memory-optimized table, the transaction becomes durable only after the in-memory transaction log is saved to disk.</span></span>  
  
 <span data-ttu-id="b6398-108">다시 시작 내구성</span><span class="sxs-lookup"><span data-stu-id="b6398-108">Restart Durability</span></span>  
 <span data-ttu-id="b6398-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 충돌이나 계획된 종료 후에 다시 시작되면 메모리 최적화 내구성이 있는 테이블이 다시 인스턴스화되어 종료나 충돌 전의 상태로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-109">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts after a crash or planned shutdown, the memory-optimized durable tables are reinstantiated to restore them to the state before the shutdown or crash.</span></span>  
  
 <span data-ttu-id="b6398-110">미디어 오류 내구성</span><span class="sxs-lookup"><span data-stu-id="b6398-110">Media Failure Durability</span></span>  
 <span data-ttu-id="b6398-111">실패했거나 손상된 디스크에 메모리 최적화 내구성이 있는 개체의 영구 복사본이 하나 이상 포함되어 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원 기능은 메모리 최적화 테이블을 새 미디어에 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-111">If a failed or corrupt disk contains one or more persisted copies of durable memory-optimized objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore feature restores memory-optimized tables on the new media.</span></span>  
  
 <span data-ttu-id="b6398-112">메모리 최적화 테이블에는 두 가지 내구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-112">There are two durability options for memory-optimized tables:</span></span>  
  
 <span data-ttu-id="b6398-113">SCHEMA_ONLY(내구성이 없는 테이블)</span><span class="sxs-lookup"><span data-stu-id="b6398-113">SCHEMA_ONLY (non-durable table)</span></span>  
 <span data-ttu-id="b6398-114">이 옵션은 인덱스를 포함한 테이블 스키마의 내구성을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-114">This option ensures durability of the table schema, including indexes.</span></span> <span data-ttu-id="b6398-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]을 다시 시작하면 내구성이 없는 테이블이 다시 만들어지지만 데이터가 없이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted, the non-durable table is recreated, but starts with no data.</span></span> <span data-ttu-id="b6398-116">(이것은 다시 시작하면 테이블과 데이터가 손실되는 tempdb의 테이블과는 다릅니다.) 내구성이 없는 테이블을 만드는 일반적인 시나리오는 ETL 프로세스를 위한 준비 테이블 같은 임시 테이블을 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-116">(This is unlike a table in tempdb, where both the table and its data are lost upon restart.) A typical scenario for creating a non-durable table is to store transient data, such as a staging table for an ETL process.</span></span> <span data-ttu-id="b6398-117">SCHEMA_ONLY 내구성은 트랜잭션 로깅과 검사점을 방지하여 I/O 작업을 크게 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-117">A SCHEMA_ONLY durability avoids both transaction logging and checkpoint, which can significantly reduce I/O operations.</span></span>  
  
 <span data-ttu-id="b6398-118">SCHEMA_AND_DATA(내구성이 있는 테이블)</span><span class="sxs-lookup"><span data-stu-id="b6398-118">SCHEMA_AND_DATA (durable table)</span></span>  
 <span data-ttu-id="b6398-119">이 옵션은 스키마와 데이터 모두에 대한 내구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-119">This option provides durability of both schema and data.</span></span> <span data-ttu-id="b6398-120">데이터 내구성 수준은 트랜잭션을 완전 내구성으로 커밋할지 아니면 지연된 내구성으로 커밋할지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-120">The level of data durability depends on whether you commit a transaction as fully durable or with delayed durability.</span></span> <span data-ttu-id="b6398-121">완전한 내구성이 있는 트랜잭션은 디스크 기반 테이블과 유사하게 스키마 및 데이터에 대한 동일한 내구성 보증을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-121">Fully durable transactions provide the same durability guarantee for data and schema, similar to a disk-based table.</span></span> <span data-ttu-id="b6398-122">지연된 내구성은 성능을 향상시키지만 서버 충돌이나 장애 조치(Failover)의 경우 데이터 손실을 발생시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-122">Delayed durability will improve performance but can potentially result in data loss in case of a server crash or fail over.</span></span> <span data-ttu-id="b6398-123">지연된 내구성에 자세한 내용은 [트랜잭션 내구성 제어](../logs/control-transaction-durability.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6398-123">(For more information about delayed durability, see [Control Transaction Durability](../logs/control-transaction-durability.md).)</span></span>  
  
 <span data-ttu-id="b6398-124">메모리 최적화 테이블의 스키마는 데이터베이스의 기본 파일 그룹에서 디스크 기반 테이블과 비슷하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-124">The schema of the memory-optimized table is persisted, similar to disk-based tables, in the primary file group of a database.</span></span>  
  
 <span data-ttu-id="b6398-125">메모리 최적화 내구성이 있는 테이블의 데이터는 데이터 및 델타 파일 쌍에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-125">Data in durable memory-optimized tables is saved in data and delta file pairs.</span></span>  
  
 <span data-ttu-id="b6398-126">메모리 최적화 테이블에 정의된 인덱스는 메타데이터에서만 유지되고 스토리지에서는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-126">The indexes defined in memory-optimized tables persist only in metadata, not in storage.</span></span> <span data-ttu-id="b6398-127">인덱스 구조는 메모리 최적화 테이블을 로드하는 과정에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-127">Index structures are generated as part of loading memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b6398-128">행은 DELETE 문에 의해 명시적으로 또는 UPDATE 문에 의해 간접적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-128">Rows are deleted either explicitly by a DELETE statement or indirectly by an UPDATE statement.</span></span> <span data-ttu-id="b6398-129">UPDATE 작업은 삭제 후 삽입으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-129">An UPDATE operation is executed as a delete followed by an insert.</span></span> <span data-ttu-id="b6398-130">행이 삭제되면 데이터 파일에는 아무런 변경이 없지만 삭제된 행을 식별하는 새로운 행이 해당 델타 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-130">When a row is deleted, no change is made to a data file but a new row, identifying the deleted row, is appended to the corresponding delta file.</span></span>  
  
 <span data-ttu-id="b6398-131">복구 또는 복원 작업 중에 메모리 내 OLTP 엔진은 물리적 메모리에 로드하기 위해 데이터 및 델타 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-131">During recovery or restore operations, the In-Memory OLTP engine reads data and delta files for loading into physical memory.</span></span> <span data-ttu-id="b6398-132">로드 시간을 결정하는 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-132">The load time is determined by:</span></span>  
  
-   <span data-ttu-id="b6398-133">로드할 데이터의 양</span><span class="sxs-lookup"><span data-stu-id="b6398-133">The amount of data to load.</span></span>  
  
-   <span data-ttu-id="b6398-134">순차 I/O 대역폭</span><span class="sxs-lookup"><span data-stu-id="b6398-134">Sequential I/O bandwidth.</span></span>  
  
-   <span data-ttu-id="b6398-135">파일 컨테이너 및 프로세서 코어의 수로 결정되는 병렬 처리 수준</span><span class="sxs-lookup"><span data-stu-id="b6398-135">Degree of parallelism, determined by number of file containers and processor cores.</span></span>  
  
-   <span data-ttu-id="b6398-136">다시 실행해야 할 로그의 활성 부분에 있는 로그 레코드의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="b6398-136">The amount of log records in the active portion of the log that need to be redone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6398-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6398-137">See Also</span></span>  
 [<span data-ttu-id="b6398-138">메모리 최적화 개체에 대한 스토리지 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="b6398-138">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
