---
title: 클러스터형 Columnstore 인덱스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: afc7da4e28ef7f32ca4a2b4ea762e5a5af442471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646587"
---
# <a name="using-clustered-columnstore-indexes"></a><span data-ttu-id="de9cf-102">클러스터형 columnstore 인덱스 사용</span><span class="sxs-lookup"><span data-stu-id="de9cf-102">Using Clustered Columnstore Indexes</span></span>
  <span data-ttu-id="de9cf-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 클러스터형 columnstore 인덱스를 사용하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-103">Tasks for using clustered columnstore indexes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="de9cf-104">columnstore 인덱스에 대한 개요는 [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="de9cf-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="de9cf-105">클러스터형 columnstore 인덱스에 대한 자세한 내용은 [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="de9cf-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="de9cf-106">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="de9cf-106">Contents</span></span>

-   [<span data-ttu-id="de9cf-107">클러스터형 Columnstore 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="de9cf-107">Create a Clustered Columnstore Index</span></span>](#create)

-   [<span data-ttu-id="de9cf-108">클러스터형 columnstore 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="de9cf-108">Drop a Clustered Columnstore Index</span></span>](#drop)

-   [<span data-ttu-id="de9cf-109">클러스터형 columnstore 인덱스로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="de9cf-109">Load Data into a Clustered Columnstore Index</span></span>](#load)

-   [<span data-ttu-id="de9cf-110">클러스터형 columnstore 인덱스의 데이터 변경</span><span class="sxs-lookup"><span data-stu-id="de9cf-110">Change Data in a Clustered Columnstore Index</span></span>](#change)

-   [<span data-ttu-id="de9cf-111">클러스터형 Columnstore 인덱스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="de9cf-111">Rebuild a Clustered Columnstore Index</span></span>](#rebuild)

-   [<span data-ttu-id="de9cf-112">클러스터형 Columnstore 인덱스 다시 구성</span><span class="sxs-lookup"><span data-stu-id="de9cf-112">Reorganize a Clustered Columnstore Index</span></span>](#reorganize)

##  <a name="create-a-clustered-columnstore-index"></a><a name="create"></a><span data-ttu-id="de9cf-113">클러스터형 Columnstore 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="de9cf-113">Create a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-114">클러스터형 columnstore 인덱스를 만들려면 먼저 rowstore 테이블을 힙 또는 클러스터형 인덱스로 만든 다음 [CREATE CLUSTERED COLUMNSTORE index &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) 문을 사용 하 여 테이블을 클러스터형 columnstore 인덱스로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-114">To create a clustered columnstore index, first create a rowstore table as a heap or clustered index, and then use the [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) statement to convert the table to a clustered columnstore index.</span></span> <span data-ttu-id="de9cf-115">클러스터형 columnstore 인덱스의 이름을 클러스터형 인덱스와 동일하게 지정하려면 DROP_EXISTING 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-115">If you want the clustered columnstore index to have the same name as the clustered index, use the DROP_EXISTING option.</span></span>

 <span data-ttu-id="de9cf-116">이 예에서는 테이블을 힙으로 만들고 이를 cci_Simple라는 클러스터형 columnstore 인덱스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-116">This example creates a table as a heap and then converts it to a clustered columnstore index named cci_Simple.</span></span> <span data-ttu-id="de9cf-117">이렇게 하면 전체 테이블의 스토리지가 rowstore에서 columnstore로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-117">This changes the storage for the entire table from rowstore to columnstore.</span></span>

```
CREATE TABLE T1(
    ProductKey [int] NOT NULL, 
    OrderDateKey [int] NOT NULL, 
    DueDateKey [int] NOT NULL, 
    ShipDateKey [int] NOT NULL);
GO
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;
GO
```

 <span data-ttu-id="de9cf-118">더 많은 예제를 보려면 [CREATE CLUSTERED COLUMNSTORE INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)의 예제 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="de9cf-118">For more examples, see the Examples section in [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

##  <a name="drop-a-clustered-columnstore-index"></a><a name="drop"></a><span data-ttu-id="de9cf-119">클러스터형 Columnstore 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="de9cf-119">Drop a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-120">[DROP INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/drop-index-transact-sql) 문을 사용 하 여 클러스터형 columnstore 인덱스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-120">Use the [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql) statement to drop a clustered columnstore index.</span></span> <span data-ttu-id="de9cf-121">이 연산은 인덱스를 삭제하고 columnstore 테이블을 rowstore 힙으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-121">This operation will drop the index and convert the columnstore table to a rowstore heap.</span></span>

##  <a name="load-data-into-a-clustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="de9cf-122">클러스터형 Columnstore 인덱스로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="de9cf-122">Load Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-123">표준 로딩 방법 중 하나를 사용하여 기존 클러스터형 columnstore 인덱스에 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-123">You can add data to an existing clustered columnstore index by using any of the standard loading methods.</span></span>  <span data-ttu-id="de9cf-124">예를 들어 bcp 대량 로드 도구, Integration Services 및 INSERT ... SELECT는 모두 클러스터형 columnstore 인덱스에 데이터를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-124">For example, the bcp bulk loading tool, Integration Services, and INSERT ... SELECT can all load data into a clustered columnstore index.</span></span>

 <span data-ttu-id="de9cf-125">클러스터형 columnstore 인덱스는 columnstore의 열 세그먼트 조각화를 방지하기 위해 deltastore를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-125">Clustered columnstore indexes leverage the deltastore in order to prevent fragmentation of column segments in the columnstore.</span></span>

### <a name="loading-into-a-partitioned-table"></a><span data-ttu-id="de9cf-126">분할된 테이블로 로드</span><span class="sxs-lookup"><span data-stu-id="de9cf-126">Loading into a partitioned table</span></span>
 <span data-ttu-id="de9cf-127">분할된 데이터에 대해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 먼저 각 행을 파티션에 할당한 다음 파티션 내에서 데이터에 columnstore 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-127">For partitioned data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] first assigns each row to a partition, and then performs columnstore operations on the data within the partition.</span></span> <span data-ttu-id="de9cf-128">각 파티션에는 고유한 행 그룹 수와 적어도 하나의 deltastore가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-128">Each partition has its own rowgroups and at least one deltastore.</span></span>

### <a name="deltastore-loading-scenarios"></a><span data-ttu-id="de9cf-129">Deltastore 로드 시나리오</span><span class="sxs-lookup"><span data-stu-id="de9cf-129">Deltastore loading scenarios</span></span>
 <span data-ttu-id="de9cf-130">행 수가 행 그룹에 허용된 최대 행 수에 도달할 때까지 행은 deltastore에 누적됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-130">Rows accumulate in the deltastore until the number of rows is the maximum number of rows allowed for a rowgroup.</span></span> <span data-ttu-id="de9cf-131">Deltastore는 행 그룹 당 최대 행 수를 포함 하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 행 그룹를 "닫힘"으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-131">When the deltastore contains the maximum number of rows per rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the rowgroup as "CLOSED".</span></span> <span data-ttu-id="de9cf-132">"튜플-이동" 이라고 하는 백그라운드 프로세스는 닫힌 행 그룹를 찾고 columnstore로 이동 합니다. 여기서 행 그룹는 열 세그먼트로 압축 되며 열 세그먼트는 columnstore에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-132">A background process, called the "tuple-mover", finds the CLOSED rowgroup and moves into the columnstore, where the rowgroup is compressed into column segments and the column segments are stored in the columnstore.</span></span>

 <span data-ttu-id="de9cf-133">클러스터형 columnstore 인덱스마다 여러 deltastore가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-133">For each clustered columnstore index there can be multiple deltastores.</span></span>

-   <span data-ttu-id="de9cf-134">deltastore가 잠겨 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 다른 deltastore를 잠그려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-134">If a deltastore is locked, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will try to obtain a lock on a different deltastore.</span></span> <span data-ttu-id="de9cf-135">사용 가능한 deltastore가 없으면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 새 deltastore를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-135">If there are no deltastores available, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will create a new deltastore.</span></span>

-   <span data-ttu-id="de9cf-136">분할된 테이블의 경우 각 파티션에 대해 하나 이상의 deltastore가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-136">For a partitioned table, there can be one or more deltastores for each partition.</span></span>

 <span data-ttu-id="de9cf-137">다음 시나리오에서는 클러스터형 columnstore 인덱스에 대해서만 로드된 행이 언제 columnstore로 곧바로 이동하거나 deltastore로 이동하는지를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-137">For clustered columnstore indexes only, the following scenarios describe when loaded rows go directly to the columnstore or when they go to the deltastore.</span></span>

 <span data-ttu-id="de9cf-138">예를 들어, 각 행 그룹에는 행 그룹당 102,400-1,048,576행이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-138">In the example, each rowgroup can have 102,400-1,048,576 rows per rowgroup.</span></span>

|<span data-ttu-id="de9cf-139">대량 로드할 행</span><span class="sxs-lookup"><span data-stu-id="de9cf-139">Rows to Bulk Load</span></span>|<span data-ttu-id="de9cf-140">Columnstore에 추가된 행</span><span class="sxs-lookup"><span data-stu-id="de9cf-140">Rows Added to the Columnstore</span></span>|<span data-ttu-id="de9cf-141">Deltastore에 추가된 행</span><span class="sxs-lookup"><span data-stu-id="de9cf-141">Rows Added to the Deltastore</span></span>|
|-----------------------|-----------------------------------|----------------------------------|
|<span data-ttu-id="de9cf-142">102,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-142">102,000</span></span>|<span data-ttu-id="de9cf-143">0</span><span class="sxs-lookup"><span data-stu-id="de9cf-143">0</span></span>|<span data-ttu-id="de9cf-144">102,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-144">102,000</span></span>|
|<span data-ttu-id="de9cf-145">145,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-145">145,000</span></span>|<span data-ttu-id="de9cf-146">145,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-146">145,000</span></span><br /><br /> <span data-ttu-id="de9cf-147">행 그룹 크기: 145,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-147">Rowgroup size: 145,000</span></span>|<span data-ttu-id="de9cf-148">0</span><span class="sxs-lookup"><span data-stu-id="de9cf-148">0</span></span>|
|<span data-ttu-id="de9cf-149">1,048,577</span><span class="sxs-lookup"><span data-stu-id="de9cf-149">1,048,577</span></span>|<span data-ttu-id="de9cf-150">1,048,576</span><span class="sxs-lookup"><span data-stu-id="de9cf-150">1,048,576</span></span><br /><br /> <span data-ttu-id="de9cf-151">행 그룹 크기: 1,048,576</span><span class="sxs-lookup"><span data-stu-id="de9cf-151">Rowgroup size: 1,048,576.</span></span>|<span data-ttu-id="de9cf-152">1</span><span class="sxs-lookup"><span data-stu-id="de9cf-152">1</span></span>|
|<span data-ttu-id="de9cf-153">2,252,152</span><span class="sxs-lookup"><span data-stu-id="de9cf-153">2,252,152</span></span>|<span data-ttu-id="de9cf-154">2,252,152</span><span class="sxs-lookup"><span data-stu-id="de9cf-154">2,252,152</span></span><br /><br /> <span data-ttu-id="de9cf-155">행 그룹 크기: 1,048,576, 1,048,576, 155,000</span><span class="sxs-lookup"><span data-stu-id="de9cf-155">Rowgroup sizes: 1,048,576, 1,048,576, 155,000.</span></span>|<span data-ttu-id="de9cf-156">0</span><span class="sxs-lookup"><span data-stu-id="de9cf-156">0</span></span>|

 <span data-ttu-id="de9cf-157">다음 예제에서는 1,048,577행을 파티션으로 로드하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-157">The following example shows the results of loading 1,048,577 rows into a partition.</span></span> <span data-ttu-id="de9cf-158">결과에는 columnstore에 COMPRESSED 행 그룹이 하나 있고(열 세그먼트로 압축됨) deltastore에 행이 1개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-158">The results show that one COMPRESSED rowgroup in the columnstore (as compressed column segments), and 1 row in the deltastore.</span></span>

```sql
SELECT * FROM sys.column_store_row_groups;
```

 <span data-ttu-id="de9cf-159">![일괄 처리 로드를 위한 행 그룹 및 deltastore](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "일괄 처리 로드를 위한 행 그룹 및 deltastore")</span><span class="sxs-lookup"><span data-stu-id="de9cf-159">![Rowgroup and deltastore for a batch load](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")</span></span>



##  <a name="change-data-in-a-clustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="de9cf-160">클러스터형 Columnstore 인덱스의 데이터 변경</span><span class="sxs-lookup"><span data-stu-id="de9cf-160">Change Data in a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-161">클러스터형 columnstore 인덱스는 DML 삽입, 업데이트 및 삭제 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-161">Clustered columnstore indexes support insert, update, and delete DML operations.</span></span>

 <span data-ttu-id="de9cf-162">[Insert &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql) 를 사용 하 여 행을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-162">Use [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) to insert a row.</span></span> <span data-ttu-id="de9cf-163">그러면 행이 deltastore에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-163">The row will be added to the deltastore.</span></span>

 <span data-ttu-id="de9cf-164">행을 삭제하려면 [DELETE&#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-164">Use [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) to delete a row.</span></span>

-   <span data-ttu-id="de9cf-165">행이 columnstore에 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 행을 논리적으로 삭제된 것으로 표시하지만, 인덱스가 다시 작성될 때까지는 행에 대한 물리적 스토리지를 회수하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-165">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted but does not reclaim the physical storage for the row until the index is rebuilt.</span></span>

-   <span data-ttu-id="de9cf-166">행이 deltastore에 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 행을 논리적 및 물리적으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-166">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logically and physically deletes the row.</span></span>

 <span data-ttu-id="de9cf-167">행을 삭제하려면 [UPDATE&#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-167">Use [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) to update a row.</span></span>

-   <span data-ttu-id="de9cf-168">행이 columnstore에 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 행을 논리적으로 삭제됨으로 표시한 다음 업데이트된 행을 deltastore에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-168">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted, and then inserts the updated row into the deltastore.</span></span>

-   <span data-ttu-id="de9cf-169">행이 deltastore에 있는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 deltastore에 있는 행을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-169">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] updates the row in the deltastore.</span></span>

##  <a name="rebuild-a-clustered-columnstore-index"></a><a name="rebuild"></a><span data-ttu-id="de9cf-170">클러스터형 Columnstore 인덱스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="de9cf-170">Rebuild a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-171">[CREATE CLUSTERED COLUMNSTORE index &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) 또는 [ALTER index &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql) 를 사용 하 여 기존 클러스터형 columnstore 인덱스의 전체 다시 빌드를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-171">Use [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) to perform a full rebuild of an existing clustered columnstore index.</span></span> <span data-ttu-id="de9cf-172">또한 ALTER INDEX ...를 사용할 수 있습니다. 다시 빌드하여 특정 파티션을 다시 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-172">Additionally, you can use ALTER INDEX ... REBUILD to rebuild a specific partition.</span></span>

### <a name="rebuild-process"></a><span data-ttu-id="de9cf-173">프로세스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="de9cf-173">Rebuild Process</span></span>
 <span data-ttu-id="de9cf-174">클러스터형 columnstore 인덱스를 다시 작성하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="de9cf-174">To rebuild a clustered columnstore index, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>

-   <span data-ttu-id="de9cf-175">다시 작성 작업이 발생한 동안 테이블 또는 파티션에서 배타적 잠금을 획득합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-175">Acquires an exclusive lock on the table or partition while the rebuild occurs.</span></span>  <span data-ttu-id="de9cf-176">다시 작성 중에 데이터는 “오프라인”이며 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-176">The data is "offline" and unavailable during the rebuild.</span></span>

-   <span data-ttu-id="de9cf-177">테이블에서 논리적으로 삭제된 행을 물리적으로 삭제하여 columnstore를 조각 모음합니다. 삭제된 바이트는 물리적 미디어에서 회수됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-177">Defragments the columnstore by physically deleting rows that have been logically deleted from the table; the deleted bytes are reclaimed on the physical media.</span></span>

-   <span data-ttu-id="de9cf-178">인덱스를 다시 작성하기 전에 deltastore의 rowstore 데이터를 columnstore의 데이터와 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-178">Merges the rowstore data in the deltastore with the data in the columnstore before it rebuilds the index.</span></span> <span data-ttu-id="de9cf-179">다시 작성 작업을 마치면 모든 데이터가 columnstore 형식으로 저장되며 deltastore는 비워집니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-179">When the rebuild is finished, all data is stored in columnstore format, and the deltastore is empty.</span></span>

-   <span data-ttu-id="de9cf-180">모든 데이터를 columnstore로 다시 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-180">Re-compresses all data into the columnstore.</span></span> <span data-ttu-id="de9cf-181">다시 작성 작업이 발생한 동안에는 columnstore 인덱스의 두 복사본이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-181">Two copies of the columnstore index exist while the rebuild is taking place.</span></span> <span data-ttu-id="de9cf-182">다시 작성 작업이 끝나면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 원래 columnstore 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-182">When the rebuild is finished, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deletes the original columnstore index.</span></span>

### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a><span data-ttu-id="de9cf-183">클러스터형 Columnstore 인덱스 다시 작성 관련 권장 사항</span><span class="sxs-lookup"><span data-stu-id="de9cf-183">Recommendations for Rebuilding a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-184">클러스터형 columnstore 인덱스 다시 작성은 조각화 제거 및 모든 행을 columnstore로 이동하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-184">Rebuilding a clustered columnstore index is useful for removing fragmentation, and for moving all rows into the columnstore.</span></span> <span data-ttu-id="de9cf-185">다음 권장 사항을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-185">We have the following recommendations:</span></span>

-   <span data-ttu-id="de9cf-186">전체 테이블 대신 파티션을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-186">Rebuild a partition instead of the entire table.</span></span>

    1.  <span data-ttu-id="de9cf-187">인덱스가 큰 경우 전체 테이블을 다시 작성하려면 많은 시간이 소요되고 다시 작성 중에 인덱스의 추가 복사본을 저장할 수 있는 충분한 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-187">Rebuilding the entire table takes a long time if the index is large, and it requires enough disk space to store an additional copy of the index during the rebuild.</span></span> <span data-ttu-id="de9cf-188">일반적으로 가장 최근에 사용한 파티션만 다시 작성하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-188">Usually it is only necessary to rebuild the most recently used partition.</span></span>

    2.  <span data-ttu-id="de9cf-189">분할된 테이블의 경우 최근 수정된 파티션에서만 주로 조각화가 발생하므로 전체 columnstore 인덱스를 다시 작성할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-189">For partitioned tables, you do not need to rebuild the entire columnstore index because fragmentation is likely to occur in only the partitions that have been modified recently.</span></span> <span data-ttu-id="de9cf-190">팩트 테이블 및 대규모 차원 테이블은 일반적으로 테이블 청크에서 백업 및 관리 작업을 수행하기 위해 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-190">Fact tables and large dimension tables are usually partitioned in order to perform backup and management operations on chunks of the table.</span></span>

-   <span data-ttu-id="de9cf-191">리소스 사용량이 많은 DML 작업 후 파티션을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-191">Rebuild a partition after heavy DML operations.</span></span>

     <span data-ttu-id="de9cf-192">파티션을 다시 작성하면 파티션을 조각 모음하여 디스크 스토리지를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-192">Rebuilding a partition will defragment the partition and reduce disk storage.</span></span> <span data-ttu-id="de9cf-193">다시 작성 시 columnstore에서 삭제 표시된 모든 행이 삭제되고 deltastore의 모든 행이 columnstore로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-193">Rebuilding will delete all rows from the columnstore that are marked for deletion, and it will move all rows from the deltastore into the columnstore.</span></span>

-   <span data-ttu-id="de9cf-194">데이터를 로드한 후 파티션을 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-194">Rebuild a partition after loading data.</span></span>

     <span data-ttu-id="de9cf-195">이렇게 하면 모든 데이터가 columnstore에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-195">This ensures all data is stored in the columnstore.</span></span> <span data-ttu-id="de9cf-196">여러 로드를 동시에 수행하면 각 파티션에 여러 deltastore가 생길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-196">If multiple loads occur at the same time, each partition could end up having multiple deltastores.</span></span> <span data-ttu-id="de9cf-197">다시 작성 시 deltastore의 모든 행이 columnstore로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-197">Rebuilding will move all deltastore rows into the columnstore.</span></span>

##  <a name="reorganize-a-clustered-columnstore-index"></a><a name="reorganize"></a><span data-ttu-id="de9cf-198">클러스터형 Columnstore 인덱스 다시 구성</span><span class="sxs-lookup"><span data-stu-id="de9cf-198">Reorganize a Clustered Columnstore Index</span></span>
 <span data-ttu-id="de9cf-199">클러스터형 columnstore 인덱스를 다시 구성하면 모든 CLOSED 행 그룹이 columnstore로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-199">Reorganizing a clustered columnstore index moves all CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="de9cf-200">다시 구성 하려면 [ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)에서 다시 구성 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-200">To perform a reorganize, use [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)with the REORGANIZE option.</span></span>

 <span data-ttu-id="de9cf-201">CLOSED 행 그룹을 columnstore로 이동할 경우에는 다시 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-201">Reorganizing is not required in order to move CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="de9cf-202">tuple-mover 프로세스에서 모든 CLOSED 행 그룹을 찾아서 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-202">The tuple-mover process will eventually find all CLOSED rowgroups and move them.</span></span> <span data-ttu-id="de9cf-203">하지만 tuple-mover는 단일 스레드이므로 작업에 맞게 충분히 빠르게 행 그룹을 이동하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-203">However, the tuple-mover is single-threaded and might not move rowgroups fast enough for your workload.</span></span>

### <a name="recommendations-for-reorganizing"></a><span data-ttu-id="de9cf-204">재구성 관련 권장 사항</span><span class="sxs-lookup"><span data-stu-id="de9cf-204">Recommendations for Reorganizing</span></span>
 <span data-ttu-id="de9cf-205">클러스터형 columnstore 인덱스를 다시 구성해야 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="de9cf-205">When to reorganize a clustered columnstore index:</span></span>

-   <span data-ttu-id="de9cf-206">하나 이상의 데이터 로드 후에는 최대한 빠르게 쿼리 성능 장점을 얻기 위해 클러스터형 columnstore 인덱스를 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-206">Reorganize a clustered columnstore index after one or more data loads to achieve query performance benefits as quickly as possible.</span></span> <span data-ttu-id="de9cf-207">다시 구성하려면 처음에 데이터를 압축하기 위한 추가 CPU 리소스가 필요하므로 전체 시스템 성능이 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-207">Reorganizing will initially require additional CPU resources to compress the data, which could slow overall system performance.</span></span> <span data-ttu-id="de9cf-208">하지만 데이터가 압축되는 즉시 쿼리 성능을 향상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9cf-208">However, as soon as the data is compressed, query performance can improve.</span></span>


