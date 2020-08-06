---
title: 인덱스 DDL 작업의 디스크 공간 요구 사항 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- temporary disk space [SQL Server]
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac25fc1555d6b6cfd8ee97b50d261cf5788f587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660574"
---
# <a name="disk-space-requirements-for-index-ddl-operations"></a><span data-ttu-id="3bc61-102">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="3bc61-102">Disk Space Requirements for Index DDL Operations</span></span>
  <span data-ttu-id="3bc61-103">디스크 공간은 인덱스를 생성, 다시 작성 또는 삭제할 때 고려해야 할 주요 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-103">Disk space is an important consideration when you create, rebuild, or drop indexes.</span></span> <span data-ttu-id="3bc61-104">디스크 공간이 부족하면 성능이 저하되거나 인덱스 작업이 실패할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-104">Inadequate disk space can degrade performance or even cause the index operation to fail.</span></span> <span data-ttu-id="3bc61-105">이 항목에서는 인덱스 DDL(데이터 정의 언어) 작업에 필요한 디스크 공간을 결정하는 데 도움이 되는 일반 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-105">This topic provides general information that can help you determine the amount of disk space required for index data definition language (DDL) operations.</span></span>  
  
## <a name="index-operations-that-require-no-additional-disk-space"></a><span data-ttu-id="3bc61-106">추가 디스크 공간이 필요 없는 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="3bc61-106">Index Operations That Require No Additional Disk Space</span></span>  
 <span data-ttu-id="3bc61-107">다음 인덱스 작업에는 추가 디스크 공간이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-107">The following index operations require no additional disk space:</span></span>  
  
-   <span data-ttu-id="3bc61-108">ALTER INDEX REORGANIZE. 로그 공간은 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-108">ALTER INDEX REORGANIZE; however, log space is required.</span></span>  
  
-   <span data-ttu-id="3bc61-109">DROP INDEX. 비클러스터형 인덱스를 삭제할 때 추가 디스크 공간이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-109">DROP INDEX when you are dropping a nonclustered index.</span></span>  
  
-   <span data-ttu-id="3bc61-110">DROP INDEX. 비클러스터형 인덱스가 없는 경우 MOVE TO 절을 지정하지 않고 오프라인으로 클러스터형 인덱스를 삭제할 때 추가 디스크 공간이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-110">DROP INDEX when you are dropping a clustered index offline without specifying the MOVE TO clause and nonclustered indexes do not exist.</span></span>  
  
-   <span data-ttu-id="3bc61-111">CREATE TABLE(PRIMARY KEY 또는 UNIQUE 제약 조건)</span><span class="sxs-lookup"><span data-stu-id="3bc61-111">CREATE TABLE (PRIMARY KEY or UNIQUE constraints)</span></span>  
  
## <a name="index-operations-that-require-additional-disk-space"></a><span data-ttu-id="3bc61-112">추가 디스크 공간이 필요한 인덱스 작업</span><span class="sxs-lookup"><span data-stu-id="3bc61-112">Index Operations That Require Additional Disk Space</span></span>  
 <span data-ttu-id="3bc61-113">이외의 DDL 작업에는 모두 작업 중 사용할 추가 임시 디스크 공간과 새 인덱스 구조를 저장할 영구 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-113">All other index DDL operations require additional temporary disk space to use during the operation, and permanent disk space to store the new index structure or structures.</span></span>  
  
 <span data-ttu-id="3bc61-114">새 인덱스 구조가 생성되면 해당 파일과 파일 그룹에 기존(원본) 구조와 새(대상) 구조를 위한 디스크 공간이 모두 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-114">When a new index structure is created, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="3bc61-115">기존 구조는 인덱스 생성 트랜잭션이 커밋된 후 할당 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-115">The old structure is not deallocated until the index creation transaction commits.</span></span>  
  
 <span data-ttu-id="3bc61-116">다음 인덱스 DDL 작업에서는 새 인덱스 구조가 생성되고 추가 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-116">The following index DDL operations create new index structures and require additional disk space:</span></span>  
  
-   <span data-ttu-id="3bc61-117">CREATE  INDEX</span><span class="sxs-lookup"><span data-stu-id="3bc61-117">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="3bc61-118">CREATE  INDEX  WITH  DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="3bc61-118">CREATE INDEX WITH DROP_EXISTING</span></span>  
  
-   <span data-ttu-id="3bc61-119">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="3bc61-119">ALTER INDEX REBUILD</span></span>  
  
-   <span data-ttu-id="3bc61-120">ALTER  TABLE  ADD  CONSTRAINT(PRIMARY  KEY  또는 UNIQUE)</span><span class="sxs-lookup"><span data-stu-id="3bc61-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY or UNIQUE)</span></span>  
  
-   <span data-ttu-id="3bc61-121">ALTER TABLE DROP CONSTRAINT(PRIMARY KEY 또는 UNIQUE)(제약 조건이 클러스터형 인덱스를 기반으로 하는 경우)</span><span class="sxs-lookup"><span data-stu-id="3bc61-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY or UNIQUE) when the constraint is based on a clustered index</span></span>  
  
-   <span data-ttu-id="3bc61-122">DROP INDEX MOVE TO(클러스터형 인덱스에만 적용됨)</span><span class="sxs-lookup"><span data-stu-id="3bc61-122">DROP INDEX MOVE TO (Applies only to clustered indexes.)</span></span>  
  
## <a name="temporary-disk-space-for-sorting"></a><span data-ttu-id="3bc61-123">정렬을 위한 임시 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="3bc61-123">Temporary Disk Space for Sorting</span></span>  
 <span data-ttu-id="3bc61-124">원본 및 대상 구조에 필요한 디스크 공간 이외에도 쿼리 최적화 프로그램에서 정렬이 필요 없는 실행 계획을 찾지 못할 경우 정렬을 위한 임시 디스크 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-124">Besides the disk space required for the source and target structures, temporary disk space is required for sorting, unless the query optimizer finds an execution plan that does not require sorting.</span></span>  
  
 <span data-ttu-id="3bc61-125">정렬이 필요할 경우 한 번에 한 인덱스만 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-125">If sorting is required, sorting occurs one new index at a time.</span></span> <span data-ttu-id="3bc61-126">예를 들어 단일 문 내에서 클러스터형 인덱스와 관련 비클러스터형 인덱스를 다시 작성할 때 인덱스는 차례로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-126">For example, when you rebuild a clustered index and associated nonclustered indexes within a single statement, the indexes are sorted one after the other.</span></span> <span data-ttu-id="3bc61-127">따라서 정렬에 필요한 추가 임시 디스크 공간은 작업에서 가장 큰 인덱스만큼만 크면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-127">Therefore, the additional temporary disk space that is required for sorting only has to be as large as the largest index in the operation.</span></span> <span data-ttu-id="3bc61-128">대개 클러스터형 인덱스가 가장 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-128">This is almost always the clustered index.</span></span>  
  
 <span data-ttu-id="3bc61-129">SORT_IN_TEMPDB 옵션이 ON으로 설정된 경우 가장 큰 인덱스가 **tempdb**에 맞아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-129">If the SORT_IN_TEMPDB option is set to ON, the largest index must fit into **tempdb**.</span></span> <span data-ttu-id="3bc61-130">이 옵션을 사용하면 인덱스를 만드는 데 사용되는 임시 디스크 공간이 늘어나지만 **tempdb** 가 사용자 데이터베이스와 다른 디스크 집합에 있을 때 인덱스를 만드는 데 필요한 시간은 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-130">Although this option increases the amount of temporary disk space that is used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a set of disks different from the user database.</span></span>  
  
 <span data-ttu-id="3bc61-131">SORT_IN_TEMPDB이 기본값인 OFF로 설정된 경우 분할된 인덱스를 비롯한 각 인덱스가 해당 대상 디스크 공간에서 정렬됩니다. 이때 새 인덱스 구조를 위한 디스크 공간만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-131">If SORT_IN_TEMPDB is set to OFF (the default) each index, including partitioned indexes, is sorted in its destination disk space; and only the disk space for the new index structures is required.</span></span>  
  
 <span data-ttu-id="3bc61-132">디스크 공간을 계산하는 예는 [Index Disk Space Example](index-disk-space-example.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3bc61-132">For an example of calculating disk space, see [Index Disk Space Example](index-disk-space-example.md).</span></span>  
  
## <a name="temporary-disk-space-for-online-index-operations"></a><span data-ttu-id="3bc61-133">온라인 인덱스 작업을 위한 임시 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="3bc61-133">Temporary Disk Space for Online Index Operations</span></span>  
 <span data-ttu-id="3bc61-134">온라인으로 인덱스 작업을 수행하면 임시 디스크 공간이 추가로 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-134">When you perform index operations online, additional temporary disk space is required.</span></span>  
  
 <span data-ttu-id="3bc61-135">온라인으로 클러스터형 인덱스를 생성, 다시 작성 또는 삭제할 경우 기존 책갈피를 새 책갈피에 매핑하기 위해 임시 비클러스터형 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-135">If a clustered index is created, rebuilt, or dropped online, a temporary nonclustered index is created to map old bookmarks to new bookmarks.</span></span> <span data-ttu-id="3bc61-136">SORT_IN_TEMPDB 옵션이 ON으로 설정된 경우 **tempdb**에 이 임시 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-136">If the SORT_IN_TEMPDB option is set to ON, this temporary index is created in **tempdb**.</span></span> <span data-ttu-id="3bc61-137">SORT_IN_TEMPDB가 OFF로 설정된 경우 대상 인덱스와 같은 파일 그룹이나 파티션 구성표가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-137">If SORT_IN_TEMPDB is set to OFF, the same filegroup or partition scheme as the target index is used.</span></span> <span data-ttu-id="3bc61-138">임시 매핑 인덱스에는 테이블의 각 행에 대한 레코드가 하나씩 들어 있고 해당 내용은 기존 책갈피 열과 새 책갈피 행을 합친 것입니다. 여기에는 두 책갈피에 모두 사용되는 열이 한 번만 포함되며 고유 식별자와 레코드 식별자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-138">The temporary mapping index contains one record for each row in the table, and its contents is the union of the old and new bookmark columns, including uniqueifiers and record identifiers and including only a single copy of any column used in both bookmarks.</span></span> <span data-ttu-id="3bc61-139">온라인 인덱스 작업에 대한 자세한 내용은 [온라인으로 인덱스 작업 수행](perform-index-operations-online.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bc61-139">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bc61-140">DROP INDEX 문에는 SORT_IN_TEMPDB 옵션을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-140">The SORT_IN_TEMPDB option cannot be set for DROP INDEX statements.</span></span> <span data-ttu-id="3bc61-141">임시 매핑 인덱스는 항상 대상 인덱스와 같은 파일 그룹이나 파티션 구성표에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-141">The temporary mapping index is always created in the same filegroup or partition scheme as the target index.</span></span>  
  
 <span data-ttu-id="3bc61-142">온라인 인덱스 작업은 행 버전 관리를 사용하여 다른 트랜잭션에서 수정하는 내용의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-142">Online index operations use row versioning to isolate the index operation from the effects of modifications made by other transactions.</span></span> <span data-ttu-id="3bc61-143">따라서 이미 읽은 행에 대한 공유 잠금을 요청할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-143">This avoids the need for requesting share locks on rows that have been read.</span></span> <span data-ttu-id="3bc61-144">온라인 인덱스 작업 중 여러 사용자가 동시에 업데이트 및 삭제 작업을 수행하려면 **tempdb**의 버전 레코드를 위한 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3bc61-144">Concurrent user update and delete operations during online index operations require space for version records in **tempdb**.</span></span> <span data-ttu-id="3bc61-145">자세한 내용은 [온라인으로 인덱스 작업 수행](perform-index-operations-online.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bc61-145">For more information, see [Perform Index Operations Online](perform-index-operations-online.md) .</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3bc61-146">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3bc61-146">Related Tasks</span></span>  
 [<span data-ttu-id="3bc61-147">인덱스 디스크 공간 예</span><span class="sxs-lookup"><span data-stu-id="3bc61-147">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
 [<span data-ttu-id="3bc61-148">인덱스 작업에 필요한 트랜잭션 로그 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="3bc61-148">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
 [<span data-ttu-id="3bc61-149">테이블 크기 예측</span><span class="sxs-lookup"><span data-stu-id="3bc61-149">Estimate the Size of a Table</span></span>](../databases/estimate-the-size-of-a-table.md)  
  
 [<span data-ttu-id="3bc61-150">클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="3bc61-150">Estimate the Size of a Clustered Index</span></span>](../databases/estimate-the-size-of-a-clustered-index.md)  
  
 [<span data-ttu-id="3bc61-151">비클러스터형 인덱스의 크기 예측</span><span class="sxs-lookup"><span data-stu-id="3bc61-151">Estimate the Size of a Nonclustered Index</span></span>](../databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [<span data-ttu-id="3bc61-152">힙 크기 예측</span><span class="sxs-lookup"><span data-stu-id="3bc61-152">Estimate the Size of a Heap</span></span>](../databases/estimate-the-size-of-a-heap.md)  
  
## <a name="related-content"></a><span data-ttu-id="3bc61-153">관련 내용</span><span class="sxs-lookup"><span data-stu-id="3bc61-153">Related Content</span></span>  
 [<span data-ttu-id="3bc61-154">CREATE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bc61-154">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="3bc61-155">ALTER INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bc61-155">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [<span data-ttu-id="3bc61-156">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3bc61-156">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="3bc61-157">인덱스의 채우기 비율 지정</span><span class="sxs-lookup"><span data-stu-id="3bc61-157">Specify Fill Factor for an Index</span></span>](specify-fill-factor-for-an-index.md)  
  
 [<span data-ttu-id="3bc61-158">인덱스 다시 구성 및 다시 작성</span><span class="sxs-lookup"><span data-stu-id="3bc61-158">Reorganize and Rebuild Indexes</span></span>](indexes.md)  
  
  
