---
title: 해시 인덱스에 대 한 올바른 버킷 수 결정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0579a98e3302b6944f68ca449d3e7cda0ecc01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648550"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a><span data-ttu-id="73499-102">해시 인덱스에 대한 올바른 버킷 수 결정</span><span class="sxs-lookup"><span data-stu-id="73499-102">Determining the Correct Bucket Count for Hash Indexes</span></span>
  <span data-ttu-id="73499-103">메모리 최적화 테이블을 만들 때 `BUCKET_COUNT` 매개 변수 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-103">You must specify a value for the `BUCKET_COUNT` parameter when you create the memory-optimized table.</span></span> <span data-ttu-id="73499-104">이 항목에서는 적절한 `BUCKET_COUNT` 매개 변수 값을 결정하기 위한 권장 사항을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-104">This topic makes recommendations for determining the appropriate value for the `BUCKET_COUNT` parameter.</span></span> <span data-ttu-id="73499-105">정확한 버킷 수를 확인할 수 없으면 대신 비클러스터형 인덱스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-105">If you cannot determine the correct bucket count, use a nonclustered index instead.</span></span>  <span data-ttu-id="73499-106">잘못된 `BUCKET_COUNT` 값, 특히 너무 낮은 값을 사용하면 데이터베이스 복구 시간과 작업 성능에 큰 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-106">An incorrect `BUCKET_COUNT` value, especially one that is too low, can significantly impact workload performance, as well as recovery time of the database.</span></span> <span data-ttu-id="73499-107">버킷 수를 더 많이 추정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-107">It is better to overestimate the bucket count.</span></span>  
  
 <span data-ttu-id="73499-108">중복 인덱스 키는 해시 인덱스를 사용하는 경우 동일한 버킷에 해시되어 해당 버킷의 체인이 증가하도록 하기 때문에 성능을 저하시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-108">Duplicate index keys can decrease performance with a hash index because the keys are hashed to the same bucket, causing that bucket's chain to increase.</span></span>  
  
 <span data-ttu-id="73499-109">비클러스터형 해시 인덱스에 대한 자세한 내용은 [Hash Indexes](hash-indexes.md) 및 [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-109">For more information about nonclustered hash indexes, see [Hash Indexes](hash-indexes.md) and [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="73499-110">메모리 최적화 테이블에서 각 해시 인덱스에 대해 한 해시 테이블이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-110">One hash table is allocated for each hash index on a memory-optimized table.</span></span> <span data-ttu-id="73499-111">인덱스에 할당 된 해시 테이블의 크기는 `BUCKET_COUNT` [CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql) 또는 [CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)매개 변수에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-111">The size of the hash table allocated for an index is specified by the `BUCKET_COUNT` parameter in [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) or [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span> <span data-ttu-id="73499-112">버킷 수는 내부적으로 다음 2의 제곱 수로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-112">The bucket count will internally be rounded up to the next power of two.</span></span> <span data-ttu-id="73499-113">예를 들어, 버킷 수를 300,000개로 지정하면 실제 버킷 수가 524,288개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-113">For example, specifying a bucket count of 300,000 will result in an actual bucket count of 524,288.</span></span>  
  
 <span data-ttu-id="73499-114">버킷 수와 관련한 문서 및 비디오에 대한 링크를 보려면 [해시 인덱스(메모리 내 OLTP)에 대한 올바른 버킷 수를 결정하는 방법](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/)(영문)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-114">For links to an article and video on bucket count, see [How to determine the right bucket count for hash indexes (In-Memory OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/).</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="73499-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="73499-115">Recommendations</span></span>  
 <span data-ttu-id="73499-116">대부분의 경우 버킷 수는 인덱스 키에 있는 고유한 값 수의 1~2배 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-116">In most cases the bucket count should be between 1 and 2 times the number of distinct values in the index key.</span></span> <span data-ttu-id="73499-117">인덱스 키에 중복 값이 많이 포함되어 있는 경우 평균적으로 각 인덱스 키 값에 대해 10개 이상의 행이 있으므로 대신 비클러스터형 인덱스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-117">If the index key contains a lot of duplicate values, on average there are more than 10 rows for each index key value, use a nonclustered index instead</span></span>  
  
 <span data-ttu-id="73499-118">특정 인덱스 키에 얼마나 많은 값이 지정될지 항상 예측할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="73499-118">You may not always be able to predict how many values a particular index key may have or will have.</span></span> <span data-ttu-id="73499-119">`BUCKET_COUNT` 값이 실제 키 값 수의 5배 이내에 해당하는 경우 성능이 적절해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-119">Performance should be acceptable if the `BUCKET_COUNT` value is within 5 times of the actual number of key values.</span></span>  
  
 <span data-ttu-id="73499-120">기존 데이터에 있는 고유한 인덱스 키 수를 확인하려면 다음 예제와 비슷한 쿼리를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-120">To determine the number of unique index keys in existing data, use queries similar to the following examples:</span></span>  
  
### <a name="primary-key-and-unique-indexes"></a><span data-ttu-id="73499-121">기본 키 및 고유 인덱스</span><span class="sxs-lookup"><span data-stu-id="73499-121">Primary Key and Unique Indexes</span></span>  
 <span data-ttu-id="73499-122">기본 키 인덱스는 고유하므로 키의 고유 값 수가 테이블에 있는 행 수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-122">Because the primary key index is unique, the number of distinct values in the key corresponds to the number of rows in the table.</span></span> <span data-ttu-id="73499-123">예를 들어, AdventureWorks 데이터베이스의 Sales.SalesOrderDetail 테이블에 있는 (SalesOrderID, SalesOrderDetailID)에 대한 기본 키의 경우 다음 쿼리를 실행하여 테이블의 행 수에 해당하는 고유한 기본 키 값 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-123">For an example primary key on (SalesOrderID, SalesOrderDetailID) in the table Sales.SalesOrderDetail in the AdventureWorks database, issue the following query to calculate the number of distinct primary key values, which corresponds to the number of rows in the table:</span></span>  
  
```sql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 <span data-ttu-id="73499-124">이 쿼리는 121,317개의 행 수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73499-124">This query shows a row count of 121,317.</span></span> <span data-ttu-id="73499-125">행 수가 크게 변경되지 않을 경우 버킷 수로 240,000개를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-125">Use a bucket count of 240,000 if the row count will not change significantly.</span></span> <span data-ttu-id="73499-126">테이블의 판매 주문 수가 4배가 될 것으로 예상되는 경우 버킷 수로 480,000개를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-126">Use a bucket count of 480,000 if the number of sales orders in the table is expected to quadruple.</span></span>  
  
### <a name="non-unique-indexes"></a><span data-ttu-id="73499-127">고유하지 않은 인덱스</span><span class="sxs-lookup"><span data-stu-id="73499-127">Non-Unique Indexes</span></span>  
 <span data-ttu-id="73499-128">다른 인덱스, 예를 들어 (SpecialOfferID, ProductID)에 대한 다중 열 인덱스의 경우 다음 쿼리를 발행하여 고유한 인덱스 키 값 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-128">For other indexes, for example a multi-column index on (SpecialOfferID, ProductID), issue the following query to determine the number of unique index key values:</span></span>  
  
```sql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 <span data-ttu-id="73499-129">이 쿼리는 (SpecialOfferID, ProductID)에 대한 인덱스 키 수로 484를 반환하여 비클러스터형 해시 인덱스 대신 비클러스터형 인덱스를 사용해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73499-129">This query returns an index key count for (SpecialOfferID, ProductID) of 484, indicating a that a nonclustered index should be used instead of a nonclustered hash index.</span></span>  
  
### <a name="determining-the-number-of-duplicates"></a><span data-ttu-id="73499-130">중복 항목 수 확인</span><span class="sxs-lookup"><span data-stu-id="73499-130">Determining the Number of Duplicates</span></span>  
 <span data-ttu-id="73499-131">인덱스 키 값의 평균 중복 값 수를 확인하려면 총 행 수를 고유한 인덱스 키 값 수로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="73499-131">To determine the average number of duplicate values for an index key value, divide the total number of rows by the number of unique index keys.</span></span>  
  
 <span data-ttu-id="73499-132">예를 들어, (SpecialOfferID, ProductID)의 경우 이 값은 121317/484 = 251개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-132">For the example index on (SpecialOfferID, ProductID), this leads to 121317 / 484 = 251.</span></span> <span data-ttu-id="73499-133">즉, 인덱스 키 값이 평균 251개가 되며 비클러스터형 인덱스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-133">This means index key values have an average of 251, and thus this should be a nonclustered index.</span></span>  
  
## <a name="troubleshooting-the-bucket-count"></a><span data-ttu-id="73499-134">버킷 수 문제 해결</span><span class="sxs-lookup"><span data-stu-id="73499-134">Troubleshooting the Bucket Count</span></span>  
 <span data-ttu-id="73499-135">메모리 최적화 테이블의 버킷 수 문제를 해결 하려면 [dm_db_xtp_hash_index_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) 를 사용 하 여 빈 버킷 및 행 체인의 길이에 대 한 통계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="73499-135">To troubleshoot bucket count issues in memory-optimized tables, use [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) to obtain statistics about the empty buckets and the length of row chains.</span></span> <span data-ttu-id="73499-136">다음 쿼리는 현재 데이터베이스의 모든 해시 인덱스에 대한 통계를 가져오는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-136">The following query can be used to obtain statistics about all the hash indexes in the current database.</span></span> <span data-ttu-id="73499-137">데이터베이스에 큰 테이블이 있는 경우 이 쿼리를 실행하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-137">The query can take several minutes to run if there are large tables in the database.</span></span>  
  
```sql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 <span data-ttu-id="73499-138">해시 인덱스 상태의 두 가지 키 지표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-138">The two key indicators of hash index health are:</span></span>  
  
 <span data-ttu-id="73499-139">*empty_bucket_percent*</span><span class="sxs-lookup"><span data-stu-id="73499-139">*empty_bucket_percent*</span></span>  
 <span data-ttu-id="73499-140">*empty_bucket_percent* 는 해시 인덱스에 있는 빈 버킷 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73499-140">*empty_bucket_percent* indicates the number of empty buckets in the hash index.</span></span>  
  
 <span data-ttu-id="73499-141">*empty_bucket_percent* 가 10% 미만인 경우 버킷 수도 적을 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="73499-141">If *empty_bucket_percent* is less than 10 percent, the bucket count is likely to be too low.</span></span> <span data-ttu-id="73499-142">*empty_bucket_percent* 가 33% 이상이 되는 것이 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-142">Ideally, the *empty_bucket_percent* should be 33 percent or greater.</span></span> <span data-ttu-id="73499-143">버킷 수가 인덱스 키 값 수와 일치하는 경우 해시 분포로 인해 버킷의 1/3이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-143">If the bucket count matches the number of index key values, about 1/3 of the buckets is empty, due to hash distribution.</span></span>  
  
 <span data-ttu-id="73499-144">*avg_chain_length*</span><span class="sxs-lookup"><span data-stu-id="73499-144">*avg_chain_length*</span></span>  
 <span data-ttu-id="73499-145">*avg_chain_length* 는 해시 버킷의 평균 행 체인 길이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73499-145">*avg_chain_length* indicates the average length of the row chains in the hash buckets.</span></span>  
  
 <span data-ttu-id="73499-146">*avg_chain_length* 가 10보다 크고 *empty_bucket_percent* 가 10% 이상이면 중복 인덱스 키 값이 많을 수 있으므로 비클러스터형 인덱스가 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-146">If *avg_chain_length* is greater than 10 and *empty_bucket_percent* is greater than 10 percent, there likely are many duplicate index key values and a nonclustered index would be more appropriate.</span></span> <span data-ttu-id="73499-147">평균 체인 길이 1이 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-147">An average chain length of 1 is ideal.</span></span>  
  
 <span data-ttu-id="73499-148">다음 두 가지 요소가 체인 길이에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73499-148">There are two factors that impact the chain length:</span></span>  
  
1.  <span data-ttu-id="73499-149">중복 행. 모든 중복 행은 해시 인덱스에 있는 동일한 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-149">Duplicates; all duplicate rows are part of the same chain in the hash index.</span></span>  
  
2.  <span data-ttu-id="73499-150">여러 키 값이 동일한 버킷에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-150">Multiple key values map to the same bucket.</span></span> <span data-ttu-id="73499-151">버킷 수가 적을수록 여러 값이 매핑되는 버킷이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-151">The lower the bucket count, the more buckets that will have multiple values mapped to them.</span></span>  
  
 <span data-ttu-id="73499-152">예를 들어, 다음 테이블 및 스크립트를 고려하여 테이블에 샘플 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-152">As an example, consider the following table and script to insert sample rows in the table:</span></span>  
  
```sql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 <span data-ttu-id="73499-153">이 스크립트는 테이블에 262,144개의 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-153">The script inserts 262,144 rows in the table.</span></span> <span data-ttu-id="73499-154">기본 키 인덱스 및 IX_OrderSequence에 고유한 값을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-154">It inserts unique values in the primary key index and in IX_OrderSequence.</span></span> <span data-ttu-id="73499-155">IX_Status 인덱스에 다수의 중복 값을 삽입합니다. 이 스크립트는 8개의 고유 값만 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-155">It inserts a lot of duplicate values in the index IX_Status: the script only generates 8 distinct values.</span></span>  
  
 <span data-ttu-id="73499-156">BUCKET_COUNT 문제 해결 쿼리의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-156">The output of the BUCKET_COUNT troubleshooting query is as follows:</span></span>  
  
|<span data-ttu-id="73499-157">인덱스 이름</span><span class="sxs-lookup"><span data-stu-id="73499-157">index name</span></span>|<span data-ttu-id="73499-158">total_bucket_count</span><span class="sxs-lookup"><span data-stu-id="73499-158">total_bucket_count</span></span>|<span data-ttu-id="73499-159">empty_bucket_count</span><span class="sxs-lookup"><span data-stu-id="73499-159">empty_bucket_count</span></span>|<span data-ttu-id="73499-160">empty_bucket_percent</span><span class="sxs-lookup"><span data-stu-id="73499-160">empty_bucket_percent</span></span>|<span data-ttu-id="73499-161">avg_chain_length</span><span class="sxs-lookup"><span data-stu-id="73499-161">avg_chain_length</span></span>|<span data-ttu-id="73499-162">max_chain_length</span><span class="sxs-lookup"><span data-stu-id="73499-162">max_chain_length</span></span>|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|<span data-ttu-id="73499-163">IX_Status</span><span class="sxs-lookup"><span data-stu-id="73499-163">IX_Status</span></span>|<span data-ttu-id="73499-164">8</span><span class="sxs-lookup"><span data-stu-id="73499-164">8</span></span>|<span data-ttu-id="73499-165">4</span><span class="sxs-lookup"><span data-stu-id="73499-165">4</span></span>|<span data-ttu-id="73499-166">50</span><span class="sxs-lookup"><span data-stu-id="73499-166">50</span></span>|<span data-ttu-id="73499-167">65536</span><span class="sxs-lookup"><span data-stu-id="73499-167">65536</span></span>|<span data-ttu-id="73499-168">65536</span><span class="sxs-lookup"><span data-stu-id="73499-168">65536</span></span>|  
|<span data-ttu-id="73499-169">IX_OrderSequence</span><span class="sxs-lookup"><span data-stu-id="73499-169">IX_OrderSequence</span></span>|<span data-ttu-id="73499-170">32768</span><span class="sxs-lookup"><span data-stu-id="73499-170">32768</span></span>|<span data-ttu-id="73499-171">13</span><span class="sxs-lookup"><span data-stu-id="73499-171">13</span></span>|<span data-ttu-id="73499-172">0</span><span class="sxs-lookup"><span data-stu-id="73499-172">0</span></span>|<span data-ttu-id="73499-173">8</span><span class="sxs-lookup"><span data-stu-id="73499-173">8</span></span>|<span data-ttu-id="73499-174">26</span><span class="sxs-lookup"><span data-stu-id="73499-174">26</span></span>|  
|<span data-ttu-id="73499-175">PK_SalesOrd_B14003C3F8FB3364</span><span class="sxs-lookup"><span data-stu-id="73499-175">PK_SalesOrd_B14003C3F8FB3364</span></span>|<span data-ttu-id="73499-176">262144</span><span class="sxs-lookup"><span data-stu-id="73499-176">262144</span></span>|<span data-ttu-id="73499-177">96319</span><span class="sxs-lookup"><span data-stu-id="73499-177">96319</span></span>|<span data-ttu-id="73499-178">36</span><span class="sxs-lookup"><span data-stu-id="73499-178">36</span></span>|<span data-ttu-id="73499-179">1</span><span class="sxs-lookup"><span data-stu-id="73499-179">1</span></span>|<span data-ttu-id="73499-180">8</span><span class="sxs-lookup"><span data-stu-id="73499-180">8</span></span>|  
  
 <span data-ttu-id="73499-181">이 테이블의 경우 3개의 해시 인덱스를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-181">Consider the three hash indexes on this table:</span></span>  
  
-   <span data-ttu-id="73499-182">IX_Status: 버킷의 50%가 비어 있으며 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-182">IX_Status: 50 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="73499-183">하지만 평균 체인 길이는 매우 깁니다(65,536).</span><span class="sxs-lookup"><span data-stu-id="73499-183">However, the average chain length is very high (65,536).</span></span> <span data-ttu-id="73499-184">이것은 중복 값이 많다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73499-184">This indicates a large number of duplicate values.</span></span> <span data-ttu-id="73499-185">따라서 이 경우 비클러스터형 해시 인덱스를 사용하는 것은 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-185">Therefore, using a nonclustered hash index is not appropriate in this case.</span></span> <span data-ttu-id="73499-186">대신 비클러스터형 인덱스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-186">A nonclustered index should be used instead.</span></span>  
  
-   <span data-ttu-id="73499-187">IX_OrderSequence: 버킷의 0%는 비어 있으며 너무 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-187">IX_OrderSequence: 0 percent of the buckets are empty, which is too low.</span></span> <span data-ttu-id="73499-188">또한 평균 체인 길이는 8입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-188">In addition, the average chain length is 8.</span></span> <span data-ttu-id="73499-189">이 인덱스에서 값이 고유하므로 이것은 평균 8개의 값이 각 버킷에 매핑됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-189">As the values in this index are unique, this means on average 8 values are mapped to each bucket.</span></span> <span data-ttu-id="73499-190">버킷 수를 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-190">The bucket count should be increased.</span></span> <span data-ttu-id="73499-191">인덱스 키에 262,144개의 고유한 값이 있으므로 버킷 수가 적어도 262,144개가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-191">As the index key has 262,144 unique values, the bucket count should be at least 262,144.</span></span> <span data-ttu-id="73499-192">향후에 더 성장할 것으로 예상된다면 수를 더 높여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-192">If future growth is expected, the number should be higher.</span></span>  
  
-   <span data-ttu-id="73499-193">기본 키 인덱스 (PK__SalesOrder ...): 버킷의 36%가 비어 있으며이는 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-193">Primary key index (PK__SalesOrder...): 36 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="73499-194">또한 평균 체인 길이가 1이면 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-194">In addition the average chain length is 1, which is also good.</span></span> <span data-ttu-id="73499-195">변경할 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-195">No change needed.</span></span>  
  
 <span data-ttu-id="73499-196">메모리 최적화 해시 인덱스 문제 해결에 대한 자세한 내용은 [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73499-196">For more information on troubleshooting issues with your memory-optimized hash indexes, see [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).</span></span>  
  
## <a name="detailed-considerations-for-further-optimization"></a><span data-ttu-id="73499-197">추가 최적화에 대한 세부 고려 사항</span><span class="sxs-lookup"><span data-stu-id="73499-197">Detailed Considerations for Further Optimization</span></span>  
 <span data-ttu-id="73499-198">이 섹션에서는 버킷 수를 최적화하기 위한 추가 고려 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-198">This section outlines further considerations for optimizing the bucket count.</span></span>  
  
 <span data-ttu-id="73499-199">해시 인덱스에서 최상의 성능을 얻으려면 해시 테이블에 할당된 메모리 크기와 인덱스 키에 있는 고유 값의 수가 균형을 이루어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-199">To achieve the best performance for hash indexes, balance the amount of memory allocated to the hash table and the number of distinct values in the index key.</span></span> <span data-ttu-id="73499-200">다음과 같이 포인트 조회 및 테이블 검색의 성능도 서로 균형을 이루어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-200">There is also a balance between the performance of point lookups and table scans:</span></span>  
  
-   <span data-ttu-id="73499-201">버킷 수 값이 높을수록 인덱스에 있을 빈 버킷 수가 더 많아집니다.</span><span class="sxs-lookup"><span data-stu-id="73499-201">The higher the bucket count value, the more empty buckets there will be in the index.</span></span> <span data-ttu-id="73499-202">각 버킷은 테이블 검색의 일부로 검색되므로 이것은 메모리 사용(버킷당 8바이트)과 테이블 검색 성능에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-202">This has an impact on memory usage (8 bytes per bucket) and the performance of table scans, as each bucket is scanned as part of a table scan.</span></span>  
  
-   <span data-ttu-id="73499-203">버킷 수가 낮을 수록 단일 버킷에 더 많은 값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-203">The lower the bucket count, the more values are assigned to a single bucket.</span></span> <span data-ttu-id="73499-204">이렇게 하면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이 검색 조건자에 지정된 값을 찾기 위해 단일 버킷에 여러 값을 순환해야 할 수 있으므로 포인트 조회와 삽입 성능이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="73499-204">This decreases performance for point lookups and inserts, because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] may need to traverse several values in a single bucket to find the value specified by the search predicate.</span></span>  
  
 <span data-ttu-id="73499-205">버킷 수가 고유한 인덱스 키 수에 비해 지나치게 적으면 각 버킷에 많은 값이 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-205">If the bucket count is significantly lower than the number of unique index keys, many values will map to each bucket.</span></span> <span data-ttu-id="73499-206">이로 인해 특히 포인트 조회(개별 인덱스 키의 조회) 및 삽입과 같은 대부분의 DML 작업 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-206">This degrades performance of most DML operations, particularly point lookups (lookups of individual index keys) and insert operations.</span></span> <span data-ttu-id="73499-207">예를 들어, WHERE 절에 인덱스 키 열과 일치하는 같음 조건자를 사용하면 UPDATE 및 DELETE 작업과 SELECT 쿼리의 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-207">For example, you may see poor performance of SELECT queries and, UPDATE and DELETE operations with equality predicates matching the index key columns in the WHERE clause.</span></span> <span data-ttu-id="73499-208">데이터베이스 시작 시 인덱스가 재생성되므로 버킷 수가 적어도 데이터베이스의 복구 시간에 영향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-208">A low bucket count will also affect the recovery time of the database, as the indexes are recreated on database startup.</span></span>  
  
### <a name="duplicate-index-key-values"></a><span data-ttu-id="73499-209">중복된 인덱스 키 값</span><span class="sxs-lookup"><span data-stu-id="73499-209">Duplicate Index Key Values</span></span>  
 <span data-ttu-id="73499-210">중복 값이 해시 충돌 성능에 미치는 영향이 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-210">Duplicate values can increase the performance impact of hash collisions.</span></span> <span data-ttu-id="73499-211">일반적으로 각 인덱스 키에 포함된 중복 항목 수가 적으므로 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-211">This is usually not a problem if each index key has a low number of duplicates.</span></span> <span data-ttu-id="73499-212">하지만 고유한 인덱스 키 수와 테이블 행 수의 차이가 너무 크면 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-212">But this can be a problem if the discrepancy between the number of unique index keys and the number of rows in the tables becomes very large.</span></span>  
  
 <span data-ttu-id="73499-213">동일한 인덱스 키가 있는 모든 행은 동일한 중복 체인으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-213">All rows with the same index key will go into the same duplicate chain.</span></span> <span data-ttu-id="73499-214">해시 충돌로 인해 동일한 버킷에 여러 인덱스 키가 있으면 인덱스 스캐너에서 첫 번째 값의 전체 중복 체인을 검색한 다음에야 두 번째 값에 해당하는 첫 번째 행을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-214">If multiple index keys are in the same bucket due to a hash collision, index scanners always need to scan the full duplicate chain for the first value before they can locate the first row corresponding to the second value.</span></span> <span data-ttu-id="73499-215">또한 중복 키를 사용하면 가비지 컬렉션에서 행을 찾기 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="73499-215">Duplicate keys also make it more difficult for garbage collection to locate the row.</span></span> <span data-ttu-id="73499-216">예를 들어 특정 키에 대해 중복이 1000개 있고 행 중 하나가 삭제된 경우 가비지 수집기에서 1000개의 중복 체인을 검색하여 인덱스에서 행의 연결을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-216">For example, if there are 1,000 duplicates for any key and one of the rows is deleted, the garbage collector needs to scan the chain of 1,000 duplicates to unlink the row from the index.</span></span> <span data-ttu-id="73499-217">이는 가비지 수집기가 모든 인덱스에서 연결을 해제해야 하므로 삭제된 행을 찾은 쿼리가 더 효율적인 인덱스(기본 키 인덱스)를 사용하여 행을 찾은 경우에도 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-217">This is true even if the query that found the delete used a more efficient index (a primary key index) to locate the row, because the garbage collector needs to unlink from every index</span></span>  
  
 <span data-ttu-id="73499-218">해시 인덱스의 경우 중복 인덱스 키 값에 의해 발생하는 작업을 줄이는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-218">For hash indexes, there are two ways to reduce the work caused by duplicate index key values:</span></span>  
  
-   <span data-ttu-id="73499-219">대신 비클러스터형 인덱스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-219">Use a nonclustered index instead.</span></span> <span data-ttu-id="73499-220">애플리케이션을 변경하지 않고도 인덱스 키에 열을 추가하여 중복을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-220">You can decrease the duplicates by adding columns to the index key without requiring any changes to the application.</span></span>  
  
-   <span data-ttu-id="73499-221">인덱스에 대해 매우 높은 버킷 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-221">Specify a very high bucket count for the index.</span></span> <span data-ttu-id="73499-222">예를 들어, 고유 인덱스 키 수의 20-100배로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-222">For example, 20-to-100 times the number of unique index keys.</span></span> <span data-ttu-id="73499-223">이렇게 하면 해시 충돌이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="73499-223">This will reduce hash collisions.</span></span>  
  
### <a name="small-tables"></a><span data-ttu-id="73499-224">작은 테이블</span><span class="sxs-lookup"><span data-stu-id="73499-224">Small Tables</span></span>  
 <span data-ttu-id="73499-225">작은 테이블의 경우 인덱스의 크기가 전체 데이터베이스 크기에 비해 작으므로 일반적으로 메모리 사용률은 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-225">For smaller tables, memory utilization is usually not a concern, as the size of the index will be small compared to the overall size of the database.</span></span>  
  
 <span data-ttu-id="73499-226">이제 원하는 성능에 따라 항목을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-226">You must now make a choice based on the kind of performance you want:</span></span>  
  
-   <span data-ttu-id="73499-227">인덱스에서 성능이 중요한 작업이 주로 포인트 조회 및/또는 삽입 작업인 경우 높은 버킷 수가 해시 충돌 가능성을 줄이므로 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-227">If the performance-critical operations on the index are predominantly point lookups and/or insert operations, a higher bucket count would be appropriate to reduce the likelihood of hash collisions.</span></span> <span data-ttu-id="73499-228">행 수의 3배 이상이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-228">Three times the number of rows or even more would be the best option.</span></span>  
  
-   <span data-ttu-id="73499-229">성능이 중요한 작업이 전체 인덱스 검색인 경우 실제 인덱스 키 값 수에 가까운 버킷 수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-229">If full index scans are the predominant performance-critical operations, use a bucket count that is close to the actual number of index key values.</span></span>  
  
### <a name="big-tables"></a><span data-ttu-id="73499-230">큰 테이블</span><span class="sxs-lookup"><span data-stu-id="73499-230">Big Tables</span></span>  
 <span data-ttu-id="73499-231">큰 테이블의 경우 메모리 사용률이 관심사가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-231">For large tables, memory utilization could become a concern.</span></span> <span data-ttu-id="73499-232">예를 들어 4 개의 해시 인덱스가 있는 2억5000만 행 테이블을 사용 하는 경우 각각의 버킷 수가 10억 인 경우 해시 테이블에 대 한 오버 헤드는 4 개의 인덱스 \* 10억 버킷 \* 8 바이트 = 32 gb의 메모리 사용률입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-232">For example, with a 250 million row table that has 4 hash indexes, each with a bucket count of one billion, the overhead for the hash tables is 4 indexes \* 1 billion buckets \* 8 bytes = 32 gigabytes of memory utilization.</span></span> <span data-ttu-id="73499-233">각 인덱스에 대해 2억 5천만 개의 버킷 수를 선택할 때 해시 테이블의 총 오버헤드는 8기가바이트가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73499-233">When choosing a bucket count of 250 million for each of the indexes, the total overhead for the hash tables will be 8 gigabytes.</span></span> <span data-ttu-id="73499-234">이는 8 바이트의 메모리 사용량 외에도 각 인덱스는이 시나리오에서 8gb 인 각 개별 행에 추가 됩니다. 4 개의 인덱스 \* 8 바이트 \* 2억5000만 행입니다.</span><span class="sxs-lookup"><span data-stu-id="73499-234">Note that this is in addition to the 8 bytes of memory usage each index adds to each individual row, which is 8 gigabytes in this scenario (4 indexes \* 8 bytes \* 250 million rows).</span></span>  
  
 <span data-ttu-id="73499-235">일반적으로 전체 테이블 검색은 OLTP 작업에서 성능이 중요한 경로에 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-235">Full table scans are not usually in the performance-critical path for OLTP workloads.</span></span> <span data-ttu-id="73499-236">따라서 포인트 조회 및 삽입 작업 성능과 메모리 사용률 간에 다음과 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-236">Therefore, the choice is between memory utilization versus performance of point lookup and insert operations:</span></span>  
  
-   <span data-ttu-id="73499-237">메모리 사용률이 중요한 경우 버킷 수를 인덱스 키 값 수에 가깝게 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-237">If memory utilization is a concern, choose a bucket count close to the number of index key values.</span></span> <span data-ttu-id="73499-238">버킷 수가 인덱스 키 값 수보다 너무 적으면 안 됩니다. 이 경우 대부분의 DML 작업과 서버 재시작 후 데이터베이스를 복구하는 시간에 영향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-238">The bucket count should not be significantly lower than the number of index key values, as this impacts most DML operations as well the time it takes to recover the database after server restart.</span></span>  
  
-   <span data-ttu-id="73499-239">포인트 조회를 위해 성능을 최적화하는 경우 버킷 수를 고유한 인덱스 값 수보다 2-3배 많이 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73499-239">When optimizing the performance for point lookups, a higher bucket count of two or even three times the number of unique index values would be appropriate.</span></span> <span data-ttu-id="73499-240">버킷 수가 많다는 것은 메모리 사용률이 증가하고 전체 인덱스 검색에 필요한 시간이 증가한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="73499-240">A higher bucket count would mean an increased memory utilization and an increase in the time required for a full index scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73499-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73499-241">See Also</span></span>  
 [<span data-ttu-id="73499-242">메모리 액세스에 최적화된 테이블의 인덱스</span><span class="sxs-lookup"><span data-stu-id="73499-242">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
