---
title: 메모리 액세스에 최적화 된 테이블에서 인덱스 사용에 대 한 지침 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f00d643088634c918eb626917eae64a001ce3678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732916"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a><span data-ttu-id="b98c4-102">메모리 액세스에 최적화된 테이블의 인덱스 사용 지침</span><span class="sxs-lookup"><span data-stu-id="b98c4-102">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>
  <span data-ttu-id="b98c4-103">인덱스는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블에서 데이터에 효율적으로 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-103">Indexes are used for efficiently accessing data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="b98c4-104">올바른 인덱스를 지정하면 쿼리 성능을 크게 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-104">Specifying the right indexes can dramatically improve query performance.</span></span> <span data-ttu-id="b98c4-105">예를 들어, 다음 쿼리를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="b98c4-105">Consider, for example, the query:</span></span>  
  
```sql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 <span data-ttu-id="b98c4-106">열 c1에 인덱스가 없는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]은 전체 테이블 t를 검색한 다음 조건 c1=1을 만족하는 행을 필터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-106">If there is no index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will need to scan the entire table t, and then filter on the rows that satisfy the condition c1=1.</span></span> <span data-ttu-id="b98c4-107">그러나 열 c1에 인덱스가 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]은 값 1을 직접 검색하고 행을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-107">However, if t has an index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can seek directly on the value 1 and retrieve the rows.</span></span>  
  
 <span data-ttu-id="b98c4-108">테이블에 있는 하나 이상의 열에 대해 특정한 값 또는 값의 범위를 갖는 레코드를 검색할 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]은 이러한 열에 있는 인덱스를 사용하여 해당 레코드를 신속하게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-108">When searching for records that have a specific value, or range of values, for one or more columns in the table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can use an index on those columns to quickly locate the corresponding records.</span></span> <span data-ttu-id="b98c4-109">디스크 기반 및 메모리 최적화 테이블 모두 인덱스를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-109">Both disk-based and memory-optimized tables benefit from indexes.</span></span> <span data-ttu-id="b98c4-110">그러나 메모리 최적화 테이블을 사용하는 경우에는 인덱스 구조 사이의 특정한 차이를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-110">There are, however, certain differences between index structures that need to be considered when using memory-optimized tables.</span></span> <span data-ttu-id="b98c4-111">메모리 최적화 테이블의 인덱스를 메모리 최적화 인덱스 라고 합니다. 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-111">(Indexes on memory-optimized tables are referred to as memory-optimized indexes.) Some of the key differences are:</span></span>  
  
-   <span data-ttu-id="b98c4-112">[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)를 사용 하 여 메모리 최적화 인덱스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-112">Memory-optimized indexes must be created with [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span> <span data-ttu-id="b98c4-113">디스크 기반 인덱스는 `CREATE TABLE` 및 `CREATE INDEX`를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-113">Disk-based indexes can be created with `CREATE TABLE` and `CREATE INDEX`.</span></span>  
  
-   <span data-ttu-id="b98c4-114">메모리 액세스에 최적화된 인덱스는 메모리에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-114">Memory-optimized indexes exist only in memory.</span></span> <span data-ttu-id="b98c4-115">인덱스 구조는 디스크에 유지되지 않으며 인덱스 작업은 트랜잭션 로그에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-115">Index structures are not persisted to disk and index operations are not logged in the transaction log.</span></span> <span data-ttu-id="b98c4-116">CREATE TABLE 실행 중과 데이터베이스 시작 중에 메모리 최적화 테이블이 메모리에 만들어질 때 인덱스 구조가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-116">The index structure is created when the memory-optimized table is created in memory, both during CREATE TABLE and during database startup.</span></span>  
  
-   <span data-ttu-id="b98c4-117">메모리 액세스에 최적화된 인덱스는 본질적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-117">Memory-optimized indexes are inherently covering.</span></span> <span data-ttu-id="b98c4-118">포함이란 모든 열이 인덱스에 거의 포함되며 메모리 최적화 테이블의 경우 책갈피 조회가 필요하지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-118">Covering means that all columns are virtually included in the index and bookmark lookups are not needed for memory-optimized tables.</span></span> <span data-ttu-id="b98c4-119">기본 키를 참조하는 대신 메모리 최적화 인덱스는 테이블 데이터 구조에서 실제 행에 대한 메모리 포인터만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-119">Rather than a reference to the primary key, memory-optimized indexes simply contain a memory pointer to the actual row in the table data structure.</span></span>  
  
-   <span data-ttu-id="b98c4-120">조각화 및 fillfactor는 메모리 최적화 인덱스에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-120">Fragmentation and fillfactor do not apply to memory-optimized indexes.</span></span> <span data-ttu-id="b98c4-121">디스크 기반 인덱스에서 조각화는 디스크에 순서 없이 쓰여지는 B-트리의 페이지를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-121">In disk-based indexes, fragmentation refers to pages in the B-tree being written to disk out-of-order.</span></span> <span data-ttu-id="b98c4-122">메모리 액세스에 최적화된 인덱스는 디스크에 쓰거나 디스크에서 읽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-122">Memory-optimized indexes are not written to or read from disk.</span></span> <span data-ttu-id="b98c4-123">디스크 기반 B-트리 인덱스의 Fillfactor는 물리적 페이지 구조가 실제 데이터로 채워지는 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-123">Fillfactor in disk-based B-tree indexes refers to the degree to which the physical page structures are filled with actual data.</span></span> <span data-ttu-id="b98c4-124">메모리 최적화 인덱스 구조에는 크기가 고정된 페이지가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-124">The memory-optimized index structures do not have fixed-size pages.</span></span>  
  
 <span data-ttu-id="b98c4-125">메모리 최적화 인덱스의 종류는 다음 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-125">There are two types of memory-optimized indexes:</span></span>  
  
-   <span data-ttu-id="b98c4-126">포인트 조회를 위해 만들어진 비클러스터형 해시 인덱스.</span><span class="sxs-lookup"><span data-stu-id="b98c4-126">Nonclustered hash indexes, which are made for point lookups.</span></span> <span data-ttu-id="b98c4-127">해시 인덱스에 대 한 자세한 내용은 [해시 인덱스](hash-indexes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b98c4-127">For more information about hash indexes, see [Hash Indexes](hash-indexes.md).</span></span>  
  
-   <span data-ttu-id="b98c4-128">범위 검색 및 정렬된 검색을 위해 만들어진 비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="b98c4-128">Nonclustered indexes, which are made for range scans and ordered scans.</span></span>  
  
 <span data-ttu-id="b98c4-129">해시 인덱스를 사용하면 메모리의 해시 테이블을 통해 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-129">With a hash index, data is accessed through an in-memory hash table.</span></span> <span data-ttu-id="b98c4-130">해시 인덱스에는 페이지가 없으며 크기가 항상 고정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-130">Hash indexes do not have pages and are always of a fixed size.</span></span> <span data-ttu-id="b98c4-131">그러나 해시 인덱스는 빈 해시 버킷을 가질 수 있어 낭비되는 공간이 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-131">However, a hash index can have empty hash buckets, which result in limited wasted space.</span></span> <span data-ttu-id="b98c4-132">해시 인덱스를 사용하여 쿼리에서 반환되는 값은 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-132">The values returned from a query using a hash index are not sorted.</span></span> <span data-ttu-id="b98c4-133">해시 인덱스는 같음 조건자에 대한 인덱스 검색에 최적화되며 전체 인덱스 검색도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-133">Hash indexes are optimized for index seeks on equality predicates and also support full index scans.</span></span>  
  
 <span data-ttu-id="b98c4-134">비클러스터형 인덱스(해시 인덱스가 아님)는 해시 인덱스가 지원하는 모든 것을 지원하며 보다 큼 또는 보다 작음과 같은 같지 않음 조건자에 대한 Seek 연산 및 정렬 순서를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-134">Nonclustered indexes (not hash indexes) support everything that hash indexes supports plus seek operations on inequality predicates such as greater than or less than, as well as sort order.</span></span> <span data-ttu-id="b98c4-135">인덱스 생성 시 지정한 순서에 따라 행을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-135">Rows can be retrieved according to the order specified with index creation.</span></span> <span data-ttu-id="b98c4-136">인덱스 정렬 순서가 특정 쿼리에 필요한 정렬 순서와 일치하면, 예를 들어, 인덱스 키가 ORDER BY 절과 일치하면 쿼리 실행의 일부로 행을 정렬할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-136">If the sort order of the index matches the sort order required for a particular query, for example if the index key matches the ORDER BY clause, there is no need to sort the rows as part of query execution.</span></span> <span data-ttu-id="b98c4-137">메모리 액세스에 최적화된 비클러스터형 인덱스는 단방향이며 따라서 인덱스 정렬 순서의 역방향으로 행을 검색하는 것은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-137">Memory-optimized nonclustered indexes are unidirectional; they do not support retrieving rows in a sort order that is the reverse of the sort order of the index.</span></span> <span data-ttu-id="b98c4-138">예를 들어, (c1 ASC)로 지정된 경우 역방향(c1 DESC) 인덱스 검색은 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-138">For example, for an index specified as (c1 ASC), it is not possible to scan the index in reverse order, as (c1 DESC).</span></span>  
  
 <span data-ttu-id="b98c4-139">각 인덱스는 메모리를 소모합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-139">Each index consumes memory.</span></span> <span data-ttu-id="b98c4-140">해시 인덱스는 고정된 크기의 메모리를 소모하며, 버킷 수의 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-140">Hash indexes consume a fixed amount of memory, which is a function of the bucket count.</span></span> <span data-ttu-id="b98c4-141">비클러스터형 인덱스의 경우 메모리 사용은 행 개수, 인덱스 키 열의 크기, 작업에 따라 발생하는 일정량의 추가 오버헤드를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-141">For nonclustered indexes, memory consumption is a function of the row count and the size of the index key columns, with some additional overhead depending on the workload.</span></span> <span data-ttu-id="b98c4-142">메모리 최적화 인덱스용 메모리는 메모리 최적화 테이블에 행을 저장하는 데 사용되는 메모리와 별개로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-142">Memory for memory-optimized indexes is in addition to and separate from the memory used to store rows in memory-optimized tables.</span></span>  
  
 <span data-ttu-id="b98c4-143">중복 키 값은 항상 동일한 해시 버킷을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-143">Duplicate key values always share the same hash bucket.</span></span> <span data-ttu-id="b98c4-144">해시 인덱스에 여러 중복 키 값이 포함되어 있어 긴 해시 체인이 만들어지면 성능에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-144">If a hash index contains many duplicate key values, the resulting long hash chains will harm performance.</span></span> <span data-ttu-id="b98c4-145">해시 충돌이 해시 인덱스에서 발생하면 이 시나리오의 성능이 한층 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-145">Hash collisions, which occur in any hash index, will further reduce performance in this scenario.</span></span> <span data-ttu-id="b98c4-146">따라서 고유한 인덱스 키의 수가 행 수보다 100 배 더 작은 경우 버킷 수를 훨씬 더 크게 설정 하 여 해시 충돌의 위험을 줄일 수 있습니다. 자세한 내용은 [해시 인덱스에 대 한 올바른 버킷 수 결정](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) 을 참조 하십시오. 또는 비클러스터형 인덱스를 사용 하 여 해시 충돌을 완전히 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-146">For that reason, if the number of unique index keys is at least 100 times smaller than the row count, you can reduce the risk of hash collisions by making the bucket count much larger (at least eight times the number of unique index keys; see [Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) for more information) or you can eliminate hash collisions entirely by using a nonclustered index.</span></span>  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a><span data-ttu-id="b98c4-147">메모리 액세스에 최적화된 테이블에 사용할 인덱스 결정</span><span class="sxs-lookup"><span data-stu-id="b98c4-147">Determining Which Indexes to Use for a Memory-Optimized Table</span></span>  
 <span data-ttu-id="b98c4-148">메모리 최적화 각 테이블에는 하나 이상의 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-148">Each memory-optimized table must have at least one index.</span></span> <span data-ttu-id="b98c4-149">각 PRIMARY KEY 제약 조건은 인덱스를 암시적으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-149">Note that each PRIMARY KEY constraint implicitly creates an index.</span></span> <span data-ttu-id="b98c4-150">따라서 테이블에 기본 키가 있는 경우 인덱스가 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-150">Therefore, if a table has a primary key, it has an index.</span></span> <span data-ttu-id="b98c4-151">기본 키는 내구성 있는 메모리 최적화 테이블에 대한 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-151">A primary key is a requirement for a durable memory-optimized table.</span></span>  
  
 <span data-ttu-id="b98c4-152">메모리 최적화 테이블을 쿼리하는 경우 조건자 절에 같음 조건자만 포함되어 있으면 해시 인덱스의 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-152">When querying a memory-optimized table, hash indexes perform better when the predicate clause contains only equality predicates.</span></span> <span data-ttu-id="b98c4-153">조건자에는 해시 인덱스 키의 모든 열이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-153">The predicate must include all columns in the hash index key.</span></span> <span data-ttu-id="b98c4-154">해시 인덱스는 같지 않음 조건자가 주어진 경우 검색으로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-154">A hash index will revert to a scan given an inequality predicate.</span></span>  
  
 <span data-ttu-id="b98c4-155">메모리 최적화 테이블의 열은 해시 인덱스와 비클러스터형 인덱스 둘 다에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-155">A column in a memory-optimized table can be part of both a hash index and a nonclustered index.</span></span>  
  
 <span data-ttu-id="b98c4-156">같지 않음 조건자를 사용하여 메모리 최적화 테이블을 쿼리하는 경우 비클러스터형 인덱스는 비클러스터형 해시 인덱스보다 성능이 우수합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-156">When querying a memory-optimized table with inequality predicates, nonclustered indexes will perform better than nonclustered hash indexes.</span></span>  
  
 <span data-ttu-id="b98c4-157">해시 인덱스는 인덱스를 검색하기 위해 해시할 키를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-157">The hash index requires a key (to hash) to seek into the index.</span></span> <span data-ttu-id="b98c4-158">인덱스 키가 두 열로 구성된 경우 첫 번째 열만 제공하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 해시할 완전한 키를 갖추지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-158">If an index key consists of two columns and you only provide the first column, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a complete key to hash.</span></span> <span data-ttu-id="b98c4-159">이 때문에 인덱스 검색 쿼리 계획이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-159">This will result in an index scan query plan.</span></span> <span data-ttu-id="b98c4-160">인덱싱되어야 하는 열은 사용 사례에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-160">Usage determines which columns should be indexed.</span></span>  
  
 <span data-ttu-id="b98c4-161">비클러스터형 인덱스의 열 값이 많은 행에서 같은 경우(인덱스 키 열에 중복 값이 많은 경우) 업데이트, 삽입 및 삭제 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-161">When a column in a nonclustered index has the same value in many rows (index key columns have a lot of duplicate values), performance can degrade for updates, inserts, and deletions.</span></span>  <span data-ttu-id="b98c4-162">이 상황에서 성능을 향상시키는 한 가지 방법은 비클러스터형 인덱스에 다른 열을 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-162">One way to improve performance in this situation is to add another column to the nonclustered index.</span></span>  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a><span data-ttu-id="b98c4-163">메모리 최적화 인덱스 및 디스크 기반 인덱스의 작업.</span><span class="sxs-lookup"><span data-stu-id="b98c4-163">Operations on memory-optimized and disk-based indexes.</span></span>  
  
|<span data-ttu-id="b98c4-164">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="b98c4-164">Operation</span></span>|<span data-ttu-id="b98c4-165">메모리 액세스에 최적화된 비클러스터형 해시, 인덱스</span><span class="sxs-lookup"><span data-stu-id="b98c4-165">Memory-optimized, nonclustered hash, index</span></span>|<span data-ttu-id="b98c4-166">메모리 액세스에 최적화된 비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="b98c4-166">Memory-optimized nonclustered index</span></span>|<span data-ttu-id="b98c4-167">디스크 기반 인덱스</span><span class="sxs-lookup"><span data-stu-id="b98c4-167">Disk-based index</span></span>|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|<span data-ttu-id="b98c4-168">색인 검색은 모든 테이블 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-168">Index Scan, retrieve all table rows.</span></span>|<span data-ttu-id="b98c4-169">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-169">Yes</span></span>|<span data-ttu-id="b98c4-170">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-170">Yes</span></span>|<span data-ttu-id="b98c4-171">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-171">Yes</span></span>|  
|<span data-ttu-id="b98c4-172">같음 조건자(=)의 인덱스 검색.</span><span class="sxs-lookup"><span data-stu-id="b98c4-172">Index seek on equality predicate(s) (=).</span></span>|<span data-ttu-id="b98c4-173">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-173">Yes</span></span><br /><br /> <span data-ttu-id="b98c4-174">(전체 키 필요)</span><span class="sxs-lookup"><span data-stu-id="b98c4-174">(Full key required.)</span></span>|<span data-ttu-id="b98c4-175">예 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b98c4-175">Yes <sup>1</sup></span></span>|<span data-ttu-id="b98c4-176">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-176">Yes</span></span>|  
|<span data-ttu-id="b98c4-177">같지 않음 조건자에 대 한 Index seek (>, <, \<=, > =, BETWEEN).</span><span class="sxs-lookup"><span data-stu-id="b98c4-177">Index seek on inequality predicates (>, <, \<=, >=, BETWEEN).</span></span>|<span data-ttu-id="b98c4-178">아니요(인덱스 검색의 결과)</span><span class="sxs-lookup"><span data-stu-id="b98c4-178">No (results in an index scan)</span></span>|<span data-ttu-id="b98c4-179">예 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b98c4-179">Yes <sup>1</sup></span></span>|<span data-ttu-id="b98c4-180">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-180">Yes</span></span>|  
|<span data-ttu-id="b98c4-181">인덱스 정의와 일치하는 정렬 순서로 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-181">Retrieve rows in a sort-order matching the index definition.</span></span>|<span data-ttu-id="b98c4-182">아니요</span><span class="sxs-lookup"><span data-stu-id="b98c4-182">No</span></span>|<span data-ttu-id="b98c4-183">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-183">Yes</span></span>|<span data-ttu-id="b98c4-184">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-184">Yes</span></span>|  
|<span data-ttu-id="b98c4-185">인덱스 정의의 역순과 일치하는 정렬 순서로 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-185">Retrieve rows in a sort-order matching the reverse of the index definition.</span></span>|<span data-ttu-id="b98c4-186">아니요</span><span class="sxs-lookup"><span data-stu-id="b98c4-186">No</span></span>|<span data-ttu-id="b98c4-187">아니요</span><span class="sxs-lookup"><span data-stu-id="b98c4-187">No</span></span>|<span data-ttu-id="b98c4-188">예</span><span class="sxs-lookup"><span data-stu-id="b98c4-188">Yes</span></span>|  
  
 <span data-ttu-id="b98c4-189">이 표에서 테이블에서 "예"는 인덱스가 요청을 적절히 처리할 수 있음을 의미하며 "아니요"는 인덱스를 사용하여 요청을 충족할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-189">In the table, Yes means that the index can adequately service the request and No means that the index cannot be used successfully to satisfy the request.</span></span>  
  
 <span data-ttu-id="b98c4-190"><sup>1</sup> 비클러스터형 메모리 최적화 인덱스의 경우 인덱스 검색을 수행 하는 데 전체 키가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-190"><sup>1</sup> For a nonclustered memory-optimized index, the full key is not required to perform an index seek.</span></span> <span data-ttu-id="b98c4-191">하지만 인덱스 키의 열 순서가 지정된 경우 누락된 열 뒤에 열의 값이 나오면 검색이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-191">Although, given the column order of the index key, a scan will occur if a value for a column comes after a missing column.</span></span>  
  
## <a name="index-count"></a><span data-ttu-id="b98c4-192">인덱스 개수</span><span class="sxs-lookup"><span data-stu-id="b98c4-192">Index Count</span></span>  
 <span data-ttu-id="b98c4-193">메모리 최적화 테이블은 기본 키로 만들어진 인덱스를 포함하여 최대 8개의 인덱스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-193">A memory-optimized table can have up to 8 indexes, including the index created with the primary key.</span></span>  
  
 <span data-ttu-id="b98c4-194">메모리 최적화 테이블에 만들어진 인덱스 개수는 다음 사항을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="b98c4-194">Regarding the number of indexes created on a memory-optimized table, consider the following:</span></span>  
  
-   <span data-ttu-id="b98c4-195">테이블을 만들 때 필요한 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-195">Specify the indexes you need when you create the table.</span></span> <span data-ttu-id="b98c4-196">테이블을 만든 후 메모리 최적화 테이블을 위한 인덱스는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-196">You cannot create an index for a memory-optimized table after the table is created.</span></span> <span data-ttu-id="b98c4-197">메모리 최적화 테이블에 인덱스를 추가하려면 해당 테이블을 삭제한 후 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-197">If you want to add an index to a memory-optimized table, drop and recreate that table.</span></span>  
  
-   <span data-ttu-id="b98c4-198">거의 사용하지 않는 인덱스는 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b98c4-198">Do not create an index that you rarely use:</span></span>  
  
     <span data-ttu-id="b98c4-199">가비지 컬렉션은 테이블의 모든 인덱스를 사용하는 경우 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-199">Garbage collection works best if all indexes on the table are frequently used.</span></span> <span data-ttu-id="b98c4-200">드물게 사용되는 인덱스는 오래된 행 버전의 경우 가비지 컬렉션 시스템이 최적의 성능을 발휘하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b98c4-200">Rarely-used indexes may cause the garbage collection system to not perform optimally for old row versions.</span></span>  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a><span data-ttu-id="b98c4-201">메모리 액세스에 최적화 된 인덱스 만들기: 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="b98c4-201">Creating a Memory-Optimized Index: Code Samples</span></span>  
 <span data-ttu-id="b98c4-202">열 수준 해시 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-202">Column level hash index:</span></span>  
  
```sql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="b98c4-203">테이블 수준 해시 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-203">Table level hash index:</span></span>  
  
```sql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="b98c4-204">열 수준 기본 키 해시 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-204">Column level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="b98c4-205">테이블 수준 기본 키 해시 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-205">Table level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="b98c4-206">열 수준 비클러스터형 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-206">Column level nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="b98c4-207">테이블 수준 비클러스터형 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-207">Table level nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="b98c4-208">열 수준 기본 키 비클러스터형 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-208">Column level primary key nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="b98c4-209">테이블 수준 기본 키 비클러스터형 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-209">Table level primary key nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="b98c4-210">열이 정의된 후 정의된 다중 열 인덱스:</span><span class="sxs-lookup"><span data-stu-id="b98c4-210">Multicolumn index defined after columns are defined:</span></span>  
  
```sql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="b98c4-211">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b98c4-211">See Also</span></span>  
 <span data-ttu-id="b98c4-212">[메모리 액세스에 최적화 된 테이블의 인덱스](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="b98c4-212">[Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="b98c4-213">[해시 인덱스에 대 한 올바른 버킷 수 결정](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b98c4-213">[Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span></span>  
 [<span data-ttu-id="b98c4-214">해시 인덱스</span><span class="sxs-lookup"><span data-stu-id="b98c4-214">Hash Indexes</span></span>](hash-indexes.md)  
  
  
