---
title: 메모리 액세스에 최적화된 테이블에 필요한 메모리 예측 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c5218a96d3650cbae22501ab2794b1b553996b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738392"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a><span data-ttu-id="3e4ef-102">메모리 액세스에 최적화된 테이블에 필요한 메모리 예측</span><span class="sxs-lookup"><span data-stu-id="3e4ef-102">Estimate Memory Requirements for Memory-Optimized Tables</span></span>
  <span data-ttu-id="3e4ef-103">메모리 최적화 테이블을 새로 만들거나 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 기존 디스크 기반 테이블을 메모리 최적화 테이블로 마이그레이션하는 경우에는 충분 한 메모리를 사용 하 여 서버를 프로 비전 할 수 있도록 각 테이블의 메모리 요구 사항을 적절 하 게 예측 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-103">Whether you are creating a new [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized table or migrating an existing disk-based table to a memory-optimized table, it is important to have a reasonable estimate of each table's memory needs so you can provision the server with sufficient memory.</span></span> <span data-ttu-id="3e4ef-104">이 섹션에서는 메모리 최적화 테이블의 데이터를 저장하는 데 필요한 메모리 양을 예측하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-104">This section describes how to estimate the amount of memory that you need to hold data for a memory-optimized table.</span></span>  
  
 <span data-ttu-id="3e4ef-105">디스크 기반 테이블에서 메모리 최적화 테이블로 마이그레이션을 고려하는 경우 이 항목을 진행하기 전에 마이그레이션에 가장 적합한 테이블에 대한 지침에 대해 [메모리 내 OLTP에 테이블 또는 저장 프로시저를 이식해야 하는지 확인](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-105">If you are contemplating migrating from disk-based tables to memory-optimized tables, before you proceed in this topic, see the topic [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) for guidance on which tables are best to migrate.</span></span> <span data-ttu-id="3e4ef-106">[메모리 내 OLTP로 마이그레이션](migrating-to-in-memory-oltp.md) 아래의 모든 항목은 디스크 기반 테이블에서 메모리 최적화 테이블로 마이그레이션하는 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-106">All the topics under [Migrating to In-Memory OLTP](migrating-to-in-memory-oltp.md) provide guidance on migrating from disk-based to memory-optimized tables.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="3e4ef-107">이 항목의 단원</span><span class="sxs-lookup"><span data-stu-id="3e4ef-107">Sections in this topic</span></span>  
  
-   [<span data-ttu-id="3e4ef-108">메모리 최적화 테이블의 예</span><span class="sxs-lookup"><span data-stu-id="3e4ef-108">Example memory-optimized table</span></span>](#bkmk_ExampleTable)  
  
-   [<span data-ttu-id="3e4ef-109">테이블에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-109">Memory for the table</span></span>](#bkmk_MemoryForTable)  
  
-   [<span data-ttu-id="3e4ef-110">인덱스에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-110">Memory for indexes</span></span>](#bkmk_IndexMeemory)  
  
-   [<span data-ttu-id="3e4ef-111">행 버전 관리에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-111">Memory for row versioning</span></span>](#bkmk_MemoryForRowVersions)  
  
-   [<span data-ttu-id="3e4ef-112">테이블 변수에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-112">Memory for table variables</span></span>](#bkmk_TableVariables)  
  
-   [<span data-ttu-id="3e4ef-113">증가에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-113">Memory for growth</span></span>](#bkmk_MemoryForGrowth)  
  
##  <a name="example-memory-optimized-table"></a><a name="bkmk_ExampleTable"></a> <span data-ttu-id="3e4ef-114">메모리 최적화 테이블의 예</span><span class="sxs-lookup"><span data-stu-id="3e4ef-114">Example memory-optimized table</span></span>  
 <span data-ttu-id="3e4ef-115">다음 메모리 최적화 테이블 스키마를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-115">Consider the following memory-optimized table schema:</span></span>  
  
```sql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 <span data-ttu-id="3e4ef-116">위의 스키마를 사용하여 이 메모리 최적화 테이블에 필요한 최소 메모리를 결정할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-116">Using this schema we will determine the minimum memory needed for this memory-optimized table.</span></span>  
  
##  <a name="memory-for-the-table"></a><a name="bkmk_MemoryForTable"></a> <span data-ttu-id="3e4ef-117">테이블에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-117">Memory for the table</span></span>  
 <span data-ttu-id="3e4ef-118">메모리 최적화 테이블 행은 다음 세 부분으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-118">A memory-optimized table row is comprised of three parts:</span></span>  
  
-   <span data-ttu-id="3e4ef-119">**타임스탬프** </span><span class="sxs-lookup"><span data-stu-id="3e4ef-119">**Timestamps** </span></span>  
    <span data-ttu-id="3e4ef-120">행 머리글/타임스탬프 = 24바이트</span><span class="sxs-lookup"><span data-stu-id="3e4ef-120">Row header/timestamps = 24 bytes.</span></span>  
  
-   <span data-ttu-id="3e4ef-121">**인덱스 포인터** </span><span class="sxs-lookup"><span data-stu-id="3e4ef-121">**Index pointers** </span></span>  
    <span data-ttu-id="3e4ef-122">테이블의 각 해시 인덱스의 경우, 각 행의 인덱스에는 다음 행에 대한 8바이트 주소 포인터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-122">For each hash index in the table, each row has an 8-byte address pointer to the next row in the index.</span></span>  <span data-ttu-id="3e4ef-123">인덱스가 4개 있으므로 각 행에 인덱스 포인터에 대한 32바이트가 할당됩니다(인덱스당 8바이트 포인터).</span><span class="sxs-lookup"><span data-stu-id="3e4ef-123">Since there are 4 indexes, each row will allocate 32 bytes for index pointers (an 8 byte pointer for each index).</span></span>  
  
-   <span data-ttu-id="3e4ef-124">**데이터** </span><span class="sxs-lookup"><span data-stu-id="3e4ef-124">**Data** </span></span>  
    <span data-ttu-id="3e4ef-125">행의 데이터 부분 크기는 각 데이터 열의 형식 크기를 합하여 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-125">The size of the data portion of the row is determined by summing the type size for each data column.</span></span>  <span data-ttu-id="3e4ef-126">예제 테이블에는 4바이트 정수 5개, 50바이트 문자 열 3개, 30바이트 문자 열 1개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-126">In our table we have five 4-byte integers, three 50-byte character columns, and one 30-byte character column.</span></span>  <span data-ttu-id="3e4ef-127">따라서 각 행의 데이터 부분은 4 + 4 + 4 + 4 + 4 + 50 + 50 + 50 + 30 또는 200바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-127">Therefore the data portion of each row is 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 or 200 bytes.</span></span>  
  
 <span data-ttu-id="3e4ef-128">다음은 메모리 최적화 테이블에 있는 5,000,000(5백만)개 행에 대한 크기 계산입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-128">The following is a size computation for 5,000,000 (5 million) rows in a memory-optimized table.</span></span> <span data-ttu-id="3e4ef-129">데이터 행에서 사용하는 총 메모리는 다음과 같이 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-129">The total memory used by data rows is estimated as follows:</span></span>  
  
 <span data-ttu-id="3e4ef-130">**테이블의 행에 대한 메모리**</span><span class="sxs-lookup"><span data-stu-id="3e4ef-130">**Memory for the table's rows**</span></span>  
  
 <span data-ttu-id="3e4ef-131">위의 계산에서 메모리 최적화 테이블의 각 행 크기는 24 + 32 + 200 또는 256바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-131">From the above calculations, the size of each row in the memory-optimized table is 24 + 32 + 200, or 256 bytes.</span></span>  <span data-ttu-id="3e4ef-132">행이 500만 개이므로 테이블은 5,000,000 \* 256바이트 또는 1,280,000,000바이트, 즉 1.28GB 정도를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-132">Since we have 5 million rows, the table will consume 5,000,000 \* 256 bytes, or 1,280,000,000 bytes - approximately 1.28 GB.</span></span>  
  
##  <a name="memory-for-indexes"></a><a name="bkmk_IndexMeemory"></a> <span data-ttu-id="3e4ef-133">인덱스에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-133">Memory for indexes</span></span>  
 <span data-ttu-id="3e4ef-134">**각 해시 인덱스에 대한 메모리**</span><span class="sxs-lookup"><span data-stu-id="3e4ef-134">**Memory for each hash index**</span></span>  
  
 <span data-ttu-id="3e4ef-135">각 해시 인덱스는 8바이트 주소 포인터의 해시 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-135">Each hash index is a hash array of 8-byte address pointers.</span></span>  <span data-ttu-id="3e4ef-136">배열의 크기는 해당 인덱스에 대한 고유한 인덱스 값의 수에 따라 최적으로 결정됩니다. 예를 들어 고유한 Col2 값의 수는 t1c2_index의 배열 크기를 계산하기 위한 좋은 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-136">The size of the array is best determined by the number of unique index values for that index - e.g., the number of unique Col2 values is a good starting point for the array size for the t1c2_index.</span></span> <span data-ttu-id="3e4ef-137">해시 배열이 너무 크면 메모리가 낭비되고,</span><span class="sxs-lookup"><span data-stu-id="3e4ef-137">A hash array that is too big wastes memory.</span></span>  <span data-ttu-id="3e4ef-138">해시 배열이 너무 작으면 동일한 인덱스로 해시되는 인덱스 값에 의한 충돌이 너무 많이 발생하므로 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-138">A hash array that is too small slows performance since there will be too many collisions by index values that hash to the same index.</span></span>  
  
 <span data-ttu-id="3e4ef-139">해시 인덱스는 같은지 여부를 확인하는 다음과 같은 조회를 매우 빠르게 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-139">Hash indexes achieve very fast equality lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 <span data-ttu-id="3e4ef-140">비클러스터형 인덱스는 다음과 같은 범위 조회의 경우 더욱 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-140">Nonclustered indexes are faster for range lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 <span data-ttu-id="3e4ef-141">디스크 기반 테이블을 마이그레이션하는 경우 다음을 사용하여 t1c2_index 인덱스에 대한 고유 값의 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-141">If you are migrating a disk-based table you can use the following to determine the number of unique values for the index t1c2_index.</span></span>  
  
```sql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 <span data-ttu-id="3e4ef-142">새 테이블을 만드는 경우 배열 크기를 예측하거나 배포 전에 테스트에서 데이터를 수집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-142">If you are creating a new table, you'll need to estimate the array size or gather data from your testing prior to deployment.</span></span>  
  
 <span data-ttu-id="3e4ef-143">해시 인덱스가 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 메모리 최적화 테이블에서 작동하는 방식에 대한 자세한 내용은 [해시 인덱스](../../database-engine/hash-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-143">For information on how hash indexes work in [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized tables, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="3e4ef-144">**참고:** 해시 인덱스 배열 크기를 즉시 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-144">**Note:** You cannot change the hash index array size on the fly.</span></span> <span data-ttu-id="3e4ef-145">해시 인덱스 배열 크기를 변경하려면 테이블을 삭제하고 bucket_count 값을 변경한 다음 테이블을 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-145">To change the hash index array size you must drop the table, change the bucket_count value and recreate the table.</span></span>  
  
 <span data-ttu-id="3e4ef-146">**해시 인덱스 배열 크기 설정**</span><span class="sxs-lookup"><span data-stu-id="3e4ef-146">**Setting the hash index array size**</span></span>  
  
 <span data-ttu-id="3e4ef-147">해시 배열 크기는 `(bucket_count= <value>)` 에 의해 설정됩니다. 여기서 \<value> 는 0보다 큰 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-147">The hash array size is set by `(bucket_count= <value>)` where \<value> is an integer value greater than zero.</span></span> <span data-ttu-id="3e4ef-148">\<value> 가 2의 제곱이 아니면 실제 bucket_count는 가장 가까운 다음 2의 제곱으로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-148">If \<value> is not a power of 2, the actual bucket_count is rounded up to the next closest power of 2.</span></span>  <span data-ttu-id="3e4ef-149">예제 테이블 (bucket_count = 500만)에서 500만은 2의 거듭제곱이 아니기 때문에 실제 버킷 수는 8388608 (2<sup>23</sup>)로 반올림 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-149">In our example table, (bucket_count = 5000000), since 5,000,000 is not a power of 2, the actual bucket count rounds up to 8,388,608 (2<sup>23</sup>).</span></span>  <span data-ttu-id="3e4ef-150">해시 배열에 필요한 메모리를 계산할 때는 5,000,000이 아니라 이 수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-150">You must use this number, not 5,000,000 when calculating memory needed by the hash array.</span></span>  
  
 <span data-ttu-id="3e4ef-151">따라서 이 예제에서 각 해시 배열에 필요한 메모리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-151">Thus, in our example, the memory needed for each hash array is:</span></span>  
  
 <span data-ttu-id="3e4ef-152">8388608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67108864 또는 약 64 MB.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-152">8,388,608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67,108,864 or approximately 64 MB.</span></span>  
  
 <span data-ttu-id="3e4ef-153">해시 인덱스가 3개 있으므로 해시 인덱스에 필요한 메모리는 3 \* 64MB = 192MB입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-153">Since we have three hash indexes, the memory needed for the hash indexes is 3 \* 64MB = 192MB.</span></span>  
  
 <span data-ttu-id="3e4ef-154">**비클러스터형 인덱스에 대한 메모리**</span><span class="sxs-lookup"><span data-stu-id="3e4ef-154">**Memory for nonclustered indexes**</span></span>  
  
 <span data-ttu-id="3e4ef-155">비클러스터형 인덱스는 인덱스 값과 이후 노드에 대한 포인터가 포함된 내부 노드가 있는 BTrees로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-155">Nonclustered indexes are implemented as BTrees with the inner nodes containing the index value and pointers to subsequent nodes.</span></span>  <span data-ttu-id="3e4ef-156">리프 노드에는 인덱스 값과 메모리의 테이블 행에 대한 포인터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-156">Leaf nodes contain the index value and a pointer to the table row in memory.</span></span>  
  
 <span data-ttu-id="3e4ef-157">해시 인덱스와 달리 비클러스터형 인덱스에는 고정된 버킷 크기가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-157">Unlike hash indexes, nonclustered indexes do not have a fixed bucket size.</span></span> <span data-ttu-id="3e4ef-158">인덱스는 데이터와 함께 동적으로 증가하고 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-158">The index grows and shrinks dynamically with the data.</span></span>  
  
 <span data-ttu-id="3e4ef-159">비클러스터형 인덱스에 필요한 메모리는 다음과 같이 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-159">Memory needed by nonclustered indexes can be computed as follows:</span></span>  
  
-   <span data-ttu-id="3e4ef-160">**리프가 아닌 노드에 할당된 메모리** </span><span class="sxs-lookup"><span data-stu-id="3e4ef-160">**Memory allocated to non-leaf nodes** </span></span>  
    <span data-ttu-id="3e4ef-161">일반적인 구성에서 리프가 아닌 노드에 할당된 메모리는 인덱스에 사용되는 전체 메모리의 작은 비율을 차지합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-161">For a typical configuration, the memory allocated to non-leaf nodes is a small percentage of the overall memory taken by the index.</span></span> <span data-ttu-id="3e4ef-162">이 비율은 매우 작으므로 무시해도 괜찮습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-162">This is so small it can safely be ignored.</span></span>  
  
-   <span data-ttu-id="3e4ef-163">**리프 노드에 대한 메모리** </span><span class="sxs-lookup"><span data-stu-id="3e4ef-163">**Memory for leaf nodes** </span></span>  
    <span data-ttu-id="3e4ef-164">리프 노드에는 테이블의 고유 키마다 행이 하나씩 있으며 이 행은 해당 고유 키가 있는 데이터 행을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-164">The leaf nodes have one row for each unique key in the table that points to the data rows with that unique key.</span></span>  <span data-ttu-id="3e4ef-165">동일한 키가 있는 행이 여러 개인 경우(즉, 고유하지 않은 비클러스터형 인덱스가 있는 경우), 인덱스 리프 노드에는 행이 하나만 있으며 이 행은 다른 행과 서로 연결된 행 중 하나를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-165">If you have multiple rows with the same key (i.e., you have a non-unique nonclustered index), there is only one row in the index leaf node that points to one of the rows with the other rows linked to each other.</span></span>  <span data-ttu-id="3e4ef-166">따라서 필요한 총 메모리는 대략적으로 다음과 같이 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-166">Thus, the total memory required can be approximated by:</span></span>   
    <span data-ttu-id="3e4ef-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span><span class="sxs-lookup"><span data-stu-id="3e4ef-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span></span>  
  
 <span data-ttu-id="3e4ef-168">비클러스터형 인덱스는 다음 쿼리로 예시된 범위 조회에 사용될 때 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-168">Nonclustered indexes are best when used for range lookups, as exemplified by the following query:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="memory-for-row-versioning"></a><a name="bkmk_MemoryForRowVersions"></a> <span data-ttu-id="3e4ef-169">행 버전 관리에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-169">Memory for row versioning</span></span>  
 <span data-ttu-id="3e4ef-170">잠금을 방지하기 위해 메모리 내 OLTP는 행을 업데이트하거나 삭제할 때 낙관적 동시성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-170">To avoid locks, In-Memory OLTP uses optimistic concurrency when updating or deleting rows.</span></span> <span data-ttu-id="3e4ef-171">즉, 행이 업데이트될 때 행의 추가 버전이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-171">This means that when a row is updated, an additional version of the row is created.</span></span> <span data-ttu-id="3e4ef-172">시스템은 이전 버전을 사용할 수도 있는 모든 트랜잭션의 실행이 완료될 때까지 해당 버전을 사용 가능한 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-172">The system keeps the previous versions available until all transactions that could possibly use the version have finished execution.</span></span> <span data-ttu-id="3e4ef-173">행이 삭제될 때 시스템은 업데이트와 유사한 방식으로 작동하며 버전이 더 이상 필요하지 않을 때까지 버전을 사용 가능한 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-173">When a row is deleted, the system acts in a similar way to an update, keeping the version available until it is no longer necessary.</span></span> <span data-ttu-id="3e4ef-174">읽을 때와 삽입할 때는 행의 추가 버전이 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-174">Reads and inserts do not create additional row versions.</span></span>  
  
 <span data-ttu-id="3e4ef-175">언제든지 가비지 수집 주기에 따라 메모리가 해제되기를 기다리는 많은 추가 행이 메모리에 있을 수 있기 때문에 이러한 추가 행을 수용하는 데 충분한 메모리가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-175">Because there may be a number of additional rows in memory at any time waiting for the garbage collection cycle to release their memory, you must have sufficient memory to accommodate these additional rows.</span></span>  
  
 <span data-ttu-id="3e4ef-176">추가 행 수는 행 업데이트 및 삭제의 초당 최대 수를 계산한 다음 가장 긴 트랜잭션에 소요되는 초 단위 시간(최소값 1)과 곱하여 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-176">The number of additional rows can be estimated by computing the peak number of row updates and deletions per second, then multiplying that by the number of seconds the longest transaction takes (minimum of 1).</span></span>  
  
 <span data-ttu-id="3e4ef-177">그런 다음 이 값을 행 크기와 곱하면 행 버전 관리에 필요한 바이트 수를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-177">That value is then multiplied by the row size to get the number of bytes you need for row versioning.</span></span>  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 <span data-ttu-id="3e4ef-178">부실 행의 메모리 요구는 메모리 최적화 테이블 행의 크기를 기준으로 오래 된 행 수를 곱하여 추정 됩니다 (위 [표의 메모리](#bkmk_MemoryForTable) 참조).</span><span class="sxs-lookup"><span data-stu-id="3e4ef-178">Memory needs for stale rows is then estimated by multiplying the number of stale rows by the size of a memory-optimized table row (see [Memory for the table](#bkmk_MemoryForTable) above).</span></span>  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="memory-for-table-variables"></a><a name="bkmk_TableVariables"></a> <span data-ttu-id="3e4ef-179">테이블 변수에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-179">Memory for table variables</span></span>  
 <span data-ttu-id="3e4ef-180">테이블 변수에 사용되는 메모리는 테이블 변수가 범위를 벗어날 때만 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-180">Memory used for a table variable is released only when the table variable goes out of scope.</span></span> <span data-ttu-id="3e4ef-181">업데이트의 일부로 삭제된 행을 포함하여 테이블 변수에서 삭제된 행은 가비지 수집의 대상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-181">Deleted rows, including rows deleted as part of an update, from a table variable are not subject to garbage collection.</span></span> <span data-ttu-id="3e4ef-182">테이블 변수가 범위를 벗어날 때까지는 메모리가 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-182">No memory is released until the table variable exits scope.</span></span>  
  
 <span data-ttu-id="3e4ef-183">프로시저 범위와 반대로 많은 트랜잭션에서 사용되는 큰 SQL 일괄 처리에서 정의된 테이블 변수는 다량의 메모리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-183">Table variables defined in a large SQL batch, as opposed to a procedure scope, which are used in many transactions, can consume a lot of memory.</span></span> <span data-ttu-id="3e4ef-184">테이블 변수는 가비지 수집되지 않기 때문에 테이블 변수의 삭제된 행은 다량의 메모리를 사용할 수 있으며 읽기 작업이 삭제된 행을 통과하여 검색해야 하므로 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-184">Because they are not garbage collected, deleted rows in a table variable can consume a lot memory and degrade performance since read operations need to scan past the deleted rows.</span></span>  
  
##  <a name="memory-for-growth"></a><a name="bkmk_MemoryForGrowth"></a> <span data-ttu-id="3e4ef-185">증가에 대한 메모리</span><span class="sxs-lookup"><span data-stu-id="3e4ef-185">Memory for growth</span></span>  
 <span data-ttu-id="3e4ef-186">위의 계산에서는 현재 상태의 테이블에 필요한 메모리를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-186">The above calculations estimate your memory needs for the table as it currently exists.</span></span> <span data-ttu-id="3e4ef-187">이 메모리 외에도 테이블의 증가를 예측하고 이러한 증가를 수용하는 데 충분한 메모리를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-187">In addition to this memory, you need to estimate the growth of the table and provide sufficient memory to accommodate that growth.</span></span>  <span data-ttu-id="3e4ef-188">예를 들어 10% 증가를 예상하는 경우 위의 결과에 1.1을 곱하여 테이블에 필요한 총 메모리를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e4ef-188">For example, if you anticipate 10% growth then you need to multiple the results from above by 1.1 to get the total memory needed for your table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e4ef-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e4ef-189">See Also</span></span>  
 [<span data-ttu-id="3e4ef-190">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="3e4ef-190">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
