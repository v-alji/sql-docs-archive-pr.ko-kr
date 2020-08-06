---
title: 메모리 액세스에 최적화 된 해시 인덱스의 일반적인 성능 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cef98571edd7736bc45ba8caf17451007a74cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728671"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a><span data-ttu-id="ea41e-102">메모리 액세스에 최적화된 해시 인덱스의 일반적인 성능 문제 해결</span><span class="sxs-lookup"><span data-stu-id="ea41e-102">Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes</span></span>
  <span data-ttu-id="ea41e-103">이 항목에서는 해시 인덱스의 일반적인 문제 해결을 집중적으로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-103">This topic will focus on troubleshooting and working around common issues with hash indexes.</span></span>  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a><span data-ttu-id="ea41e-104">검색에 해시 인덱스 키 열의 하위 집합 필요</span><span class="sxs-lookup"><span data-stu-id="ea41e-104">Search Requires a Subset of Hash Index Key Columns</span></span>  
 <span data-ttu-id="ea41e-105">**문제:** 해시 인덱스는 해시 값을 계산 하 고 해시 테이블에서 해당 행을 찾기 위해 모든 인덱스 키 열에 대 한 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-105">**Issue:** Hash indexes require values for all index key columns in order to compute the hash value, and locate the corresponding rows in the hash table.</span></span> <span data-ttu-id="ea41e-106">따라서 쿼리의 WHERE 절에 인덱스 키의 하위 집합에만 적용되는 같음 조건자가 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 Index Seek를 사용하여 WHERE 절의 조건자에 해당하는 행을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-106">Therefore, if a query includes equality predicates for only a subset of the index keys in the WHERE clause, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot use an index seek to locate the rows corresponding to the predicates in the WHERE clause.</span></span>  
  
 <span data-ttu-id="ea41e-107">반대로 디스크 기반 비클러스터형 인덱스 및 메모리 최적화 비클러스터형 인덱스와 같은 정렬된 인덱스는 인덱스 키 열의 하위 집합에서 Index Seek를 지원합니다(해당 열이 인덱스의 선행 열인 한에서).</span><span class="sxs-lookup"><span data-stu-id="ea41e-107">In contrast, ordered indexes like the disk-based nonclustered indexes and the memory-optimized nonclustered indexes support index seek on a subset of the index key columns, as long as they are the leading columns in the index.</span></span>  
  
 <span data-ttu-id="ea41e-108">**증상:** 이로 인해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인덱스 검색 대신 전체 테이블 검색을 실행 해야 하기 때문에 성능이 저하 될 수 있습니다. 일반적으로이 작업은 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-108">**Symptom:** This results in a performance degradation, as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] needs to execute full table scans rather than an index seek, which is typically a faster operation.</span></span>  
  
 <span data-ttu-id="ea41e-109">**문제를 해결 하는 방법:** 성능 저하 외에도 쿼리 계획 검사는 인덱스 검색 대신 검색을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-109">**How to troubleshoot:** Besides the performance degradation, inspection of the query plans will show a scan instead of an index seek.</span></span> <span data-ttu-id="ea41e-110">쿼리가 매우 간단한 경우 쿼리 텍스트와 인덱스 정의를 검사해도 검색에 인덱스 키 열의 하위 집합이 필요한지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-110">If the query is fairly simple, inspection of the query text and index definition will also show whether the search requires a subset of the index key columns.</span></span>  
  
 <span data-ttu-id="ea41e-111">다음 테이블과 쿼리를 살펴 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ea41e-111">Consider the following table and query:</span></span>  
  
```sql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 <span data-ttu-id="ea41e-112">테이블에는 두 열(o_id, od_id)에 해시 인덱스가 있지만 쿼리에는 (o_id)에 같음 조건자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-112">The table has a hash index on the two columns (o_id, od_id), while the query has an equality predicate on (o_id).</span></span> <span data-ttu-id="ea41e-113">쿼리에는 인덱스 키 열의 하위 집합에만 같음 연산자가 있으므로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 PK_od를 사용하여 Index Seek 연산을 수행할 수 없습니다. 그 대신, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 전체 인덱스 검색으로 돌아가야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-113">As the query has equality predicates on only a subset of the index key columns, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot perform an index seek operation using PK_od; instead, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has to revert to a full index scan.</span></span>  
  
 <span data-ttu-id="ea41e-114">**해결 방법:** 몇 가지 가능한 해결 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-114">**Workarounds:** There are a number of possible workarounds.</span></span> <span data-ttu-id="ea41e-115">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-115">For example:</span></span>  
  
-   <span data-ttu-id="ea41e-116">비클러스터형 해시 대신 비클러스터형 유형으로 인덱스를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-116">Recreate the index as type nonclustered instead of nonclustered hash.</span></span> <span data-ttu-id="ea41e-117">메모리 최적화 비클러스터형 인덱스가 정렬되므로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 선행 인덱스 키 열에서 Index Seek를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-117">The memory-optimized nonclustered index is ordered, and thus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can perform an index seek on the leading index key columns.</span></span> <span data-ttu-id="ea41e-118">결과적으로 이 예의 기본 키 정의는 `constraint PK_od primary key nonclustered`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-118">The resulting primary key definition for the example would be `constraint PK_od primary key nonclustered`.</span></span>  
  
-   <span data-ttu-id="ea41e-119">현재 인덱스 키를 WHERE 절의 열과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-119">Change the current index key to match the columns in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="ea41e-120">쿼리의 WHERE 절에 있는 열과 일치하는 새 해시 인덱스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-120">Add a new hash index that matches with the columns in the WHERE clause of the query.</span></span> <span data-ttu-id="ea41e-121">이 예에서는 결과 테이블 정의가 다음과 같은 모양이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-121">In the example, the resulting table definition would look at follows:</span></span>  
  
    ```sql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 <span data-ttu-id="ea41e-122">지정 된 인덱스 키 값에 대 한 중복 행이 많은 경우 메모리 최적화 해시 인덱스가 최적으로 수행 되지 않습니다. 예를 들어 o_id 열에 대 한 고유 값 수가 테이블의 행 수보다 훨씬 작은 경우에는 인덱스를 추가 하는 것이 최적이 아닙니다 (o_id). 대신 인덱스 PK_od의 형식을 해시에서 비클러스터형으로 변경 하는 것이 더 나은 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="ea41e-122">Note that a memory-optimized hash index does not perform optimally if there are a lot of duplicate rows for a given index key value: in the example, if the number of unique values for the column o_id is much smaller than the number of rows in the table, it would not be optimal to add an index on (o_id); instead, changing the type of the index PK_od from hash to nonclustered would be the better solution.</span></span> <span data-ttu-id="ea41e-123">자세한 내용은 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea41e-123">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea41e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea41e-124">See Also</span></span>  
 [<span data-ttu-id="ea41e-125">메모리 액세스에 최적화된 테이블의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ea41e-125">Indexes on Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
