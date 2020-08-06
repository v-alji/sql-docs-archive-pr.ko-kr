---
title: 설명 된 Columnstore 인덱스 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 80a29b8e8cc5b53c09369156a5cf5f717e9447a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740960"
---
# <a name="columnstore-indexes-described"></a><span data-ttu-id="05ad9-102">Columnstore Indexes Described</span><span class="sxs-lookup"><span data-stu-id="05ad9-102">Columnstore Indexes Described</span></span>
  <span data-ttu-id="05ad9-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *메모리 내 columnstore 인덱스* 는 열 기반 데이터 저장소 및 열 기반 쿼리 처리를 사용 하 여 데이터를 저장 하 고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *in-memory columnstore index* stores and manages data by using column-based data storage and column-based query processing.</span></span> <span data-ttu-id="05ad9-104">columnstore 인덱스는 주로 대량 로드 및 읽기 전용 쿼리를 수행하는 데이터 웨어하우징 작업에 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-104">Columnstore indexes work well for data warehousing workloads that primarily perform bulk loads and read-only queries.</span></span> <span data-ttu-id="05ad9-105">columnstore 인덱스를 사용하면 기존의 행 기반 스토리지보다 최대 **10배의 쿼리 성능** 이익과 압축되지 않은 데이터 크기보다 최대 **7배의 데이터 압축** 을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-105">Use the columnstore index to achieve up to **10x query performance** gains over traditional row-oriented storage, and up to **7x data compression** over the uncompressed data size.</span></span>

> [!NOTE]
>  <span data-ttu-id="05ad9-106">클러스터형 columnstore 인덱스를 대형 데이터 웨어하우징 팩트 테이블을 저장하기 위한 표준으로 보고 대부분의 데이터 웨어하우징 시나리오에 사용될 것으로 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-106">We view the clustered columnstore index as the standard for storing large data warehousing fact tables, and expect it will be used in most data warehousing scenarios.</span></span> <span data-ttu-id="05ad9-107">클러스터형 columnstore 인덱스는 업데이트 가능하므로 해당 작업에서 많은 삽입, 업데이트 및 삭제 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-107">Since the clustered columnstore index is updateable, your workload can perform a large number of insert, update, and delete operations.</span></span>

## <a name="contents"></a><span data-ttu-id="05ad9-108">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="05ad9-108">Contents</span></span>

-   [<span data-ttu-id="05ad9-109">기본 사항</span><span class="sxs-lookup"><span data-stu-id="05ad9-109">Basics</span></span>](#basics)

-   [<span data-ttu-id="05ad9-110">데이터 로드 중</span><span class="sxs-lookup"><span data-stu-id="05ad9-110">Loading Data</span></span>](#dataload)

-   [<span data-ttu-id="05ad9-111">성능 팁</span><span class="sxs-lookup"><span data-stu-id="05ad9-111">Performance Tips</span></span>](#performance)

-   [<span data-ttu-id="05ad9-112">관련 태스크 및 항목</span><span class="sxs-lookup"><span data-stu-id="05ad9-112">Related Tasks and Topics</span></span>](#related)

##  <a name="basics"></a><a name="basics"></a><span data-ttu-id="05ad9-113">기본 사항</span><span class="sxs-lookup"><span data-stu-id="05ad9-113">Basics</span></span>
 <span data-ttu-id="05ad9-114">*columnstore index* 는 columnstore라는 칼럼 데이터 형식을 사용하여 데이터를 저장, 검색 및 관리하는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-114">A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="05ad9-115">는 클러스터형 columnstore 인덱스와 비클러스터형 columnstore 인덱스를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-115">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="05ad9-116">둘 다 동일한 메모리 내 columnstore 기술을 사용하지만 용도와 지원 기능에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-116">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

###  <a name="benefits"></a><a name="benefits"></a> <span data-ttu-id="05ad9-117">이점</span><span class="sxs-lookup"><span data-stu-id="05ad9-117">Benefits</span></span>
 <span data-ttu-id="05ad9-118">columnstore 인덱스는 대개 큰 데이터 집합을 분석하는 읽기 전용 쿼리에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-118">Columnstore indexes work well for mostly read-only queries that perform analysis on large data sets.</span></span> <span data-ttu-id="05ad9-119">주로 데이터 웨어하우징 작업에 대한 쿼리가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-119">Often, these are queries for data warehousing workloads.</span></span> <span data-ttu-id="05ad9-120">columnstore 인덱스는 전체 테이블 검색을 사용하는 쿼리에는 뛰어난 성능을 제공하지만 특정 값을 찾아 데이터를 검색하는 쿼리에는 부적합합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-120">Columnstore indexes give high performance gains for queries that use full table scans, and are not well-suited for queries that seek into the data, searching for a particular value.</span></span>

 <span data-ttu-id="05ad9-121">columnstore 인덱스의 이점:</span><span class="sxs-lookup"><span data-stu-id="05ad9-121">Columnstore Index benefits:</span></span>

-   <span data-ttu-id="05ad9-122">열에는 비슷한 데이터가 있기 때문에 높은 압축 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-122">Columns often have similar data, which results in high compression rates.</span></span>

-   <span data-ttu-id="05ad9-123">압축 비율이 높으면 메모리 내 사용 공간이 감소되어 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-123">High compression rates improve query performance by using a smaller in-memory footprint.</span></span> <span data-ttu-id="05ad9-124">또한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 가 더 많은 쿼리 및 데이터 작업을 메모리 내에서 수행할 수 있으므로 쿼리 성능도 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-124">In turn, query performance can improve because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can perform more query and data operations in-memory.</span></span>

-   <span data-ttu-id="05ad9-125">배치 모드 실행이라는 새로운 쿼리 실행 메커니즘이 SQL Server에 추가되어 CPU 사용량을 크게 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-125">A new query execution mechanism called batch-mode execution has been added to SQL Server that reduces CPU usage by a large amount.</span></span> <span data-ttu-id="05ad9-126">배치 모드 실행은 columnstore 스토리지 형식과 긴밀히 통합되고 그에 맞게 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-126">Batch-mode execution is closely integrated with, and optimized around, the columnstore storage format.</span></span> <span data-ttu-id="05ad9-127">배치 모드 실행을 벡터 기반 또는 벡터화된 실행이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-127">Batch-mode execution is sometimes known as vector-based or vectorized execution.</span></span>

-   <span data-ttu-id="05ad9-128">쿼리는 대개 테이블에서 적은 수의 열만 선택하므로 실제 미디어의 총 I/O가 감소됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-128">Queries often select only a few columns from a table, which reduces total I/O from the physical media.</span></span>

### <a name="columnstore-versions"></a><span data-ttu-id="05ad9-129">columnstore 버전</span><span class="sxs-lookup"><span data-stu-id="05ad9-129">Columnstore Versions</span></span>
 <span data-ttu-id="05ad9-130">SQL Server 2012, SQL Server 2012 Parallel Data Warehouse 및 SQL Server 2014 모두 columnstore 인덱스를 사용하여 일반적인 데이터 웨어하우스 쿼리 속도를 높입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-130">SQL Server 2012, SQL Server 2012 Parallel Data Warehouse, and SQL Server 2014 all use columnstore indexes to accelerate common data warehouse queries.</span></span> <span data-ttu-id="05ad9-131">SQL Server 2012에는 비클러스터형 columnstore 인덱스와 "배치" 단위로 데이터를 처리하는 벡터 기반 쿼리 실행이라는 두 가지 기능이 새로 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-131">SQL Server 2012 introduced two new features: a nonclustered columnstore index and a vector-based query execution capability that processes data in units called "batches."</span></span> <span data-ttu-id="05ad9-132">SQL Server 2014는 SQL Server 2012의 기능과 함께 업데이트 가능한 클러스터형 columnstore 인덱스 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-132">SQL Server 2014 has the features of SQL Server 2012 plus updateable clustered columnstore indexes.</span></span>

### <a name="key-characteristics"></a><span data-ttu-id="05ad9-133">주요 특징</span><span class="sxs-lookup"><span data-stu-id="05ad9-133">Key Characteristics</span></span>

||
|-|
|<span data-ttu-id="05ad9-134">**적용 대상**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 부터 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]까지</span><span class="sxs-lookup"><span data-stu-id="05ad9-134">**Applies to**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="05ad9-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 클러스터형 columnstore 인덱스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-135">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a clustered columnstore index:</span></span>

-   <span data-ttu-id="05ad9-136">Enterprise, Developer 및 Evaluation 버전으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-136">Is available in Enterprise, Developer, and Evaluation editions.</span></span>

-   <span data-ttu-id="05ad9-137">업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-137">Is updateable.</span></span>

-   <span data-ttu-id="05ad9-138">전체 테이블의 주 스토리지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-138">Is the primary storage method for the entire table.</span></span>

-   <span data-ttu-id="05ad9-139">키 열이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-139">Has no key columns.</span></span> <span data-ttu-id="05ad9-140">모든 열이 포괄 열입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-140">All columns are included columns.</span></span>

-   <span data-ttu-id="05ad9-141">테이블에 있는 유일한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-141">Is the only index on the table.</span></span> <span data-ttu-id="05ad9-142">다른 인덱스와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-142">It cannot be combined with any other indexes.</span></span>

-   <span data-ttu-id="05ad9-143">columnstore 또는 columnstore 보관 압축을 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-143">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="05ad9-144">열을 정렬 순서에 따라 물리적으로 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-144">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="05ad9-145">그 대신 압축과 성능을 개선할 수 있는 방법으로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-145">Instead, it stores data to improve compression and performance.</span></span>

||
|-|
|<span data-ttu-id="05ad9-146">**적용 대상**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 부터 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]까지</span><span class="sxs-lookup"><span data-stu-id="05ad9-146">**Applies to**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="05ad9-147">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 비클러스터형 columnstore 인덱스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-147">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a nonclustered columnstore index:</span></span>

-   <span data-ttu-id="05ad9-148">열의 하위 집합을 클러스터형 인덱스 또는 힙으로 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-148">Can index a subset of columns in the clustered index or heap.</span></span> <span data-ttu-id="05ad9-149">예를 들어, 자주 사용하는 열을 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-149">For example, it can index the frequently used columns.</span></span>

-   <span data-ttu-id="05ad9-150">인덱스의 열 복사본을 저장할 추가 스토리지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-150">Requires extra storage to store a copy of the columns in the index.</span></span>

-   <span data-ttu-id="05ad9-151">인덱스를 다시 작성 하거나 파티션을 전환 하거나 체크 아웃 하 여 업데이트 됩니다. Insert, update, delete 등의 DML 작업을 사용 하 여 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-151">Is updated by rebuilding the index or switching partitions in and out. It is not updateable by using the DML operations such as insert, update, and delete.</span></span>

-   <span data-ttu-id="05ad9-152">테이블의 다른 인덱스와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-152">Can be combined with other indexes on the table.</span></span>

-   <span data-ttu-id="05ad9-153">columnstore 또는 columnstore 보관 압축을 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-153">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="05ad9-154">열을 정렬 순서에 따라 물리적으로 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-154">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="05ad9-155">그 대신 압축과 성능을 개선할 수 있는 방법으로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-155">Instead, it stores data to improve compression and performance.</span></span> <span data-ttu-id="05ad9-156">columnstore 인덱스 작성 전 데이터 사전 정렬은 필수는 아니지만 columnstore 압축을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-156">Pre-sorting the data before creating the columnstore index is not required, but can improve columnstore compression.</span></span>

###  <a name="key-concepts-and-terms"></a><a name="Concepts"></a><span data-ttu-id="05ad9-157">주요 개념 및 용어</span><span class="sxs-lookup"><span data-stu-id="05ad9-157">Key Concepts and Terms</span></span>
 <span data-ttu-id="05ad9-158">다음은 columnstore 인덱스와 관련된 주요 용어와 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-158">The following key terms and concepts are associated with columnstore indexes.</span></span>

 <span data-ttu-id="05ad9-159">columnstore 인덱스 columnstore *인덱스* 는 columnstore 라는 칼럼 형식의 데이터 형식을 사용 하 여 데이터를 저장, 검색 및 관리 하는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-159">columnstore index A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="05ad9-160">는 클러스터형 columnstore 인덱스와 비클러스터형 columnstore 인덱스를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-160">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="05ad9-161">둘 다 동일한 메모리 내 columnstore 기술을 사용하지만 용도와 지원 기능에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-161">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

 <span data-ttu-id="05ad9-162">columnstore *columnstore* 는 행과 열이 포함 된 테이블로 논리적으로 구성 되 고 열 단위 데이터 형식으로 물리적으로 저장 되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-162">columnstore A *columnstore* is data that is logically organized as a table with rows and columns, and physically stored in a column-wise data format.</span></span>

 <span data-ttu-id="05ad9-163">rowstore는 행과 열이 있는 테이블로 논리적으로 구성 된 다음 행 단위 데이터 형식으로 물리적으로 저장 되는 *데이터입니다.*</span><span class="sxs-lookup"><span data-stu-id="05ad9-163">rowstore A *rowstore* is data that is logically organized as a table with rows and columns, and then physically stored in a row-wise data format.</span></span> <span data-ttu-id="05ad9-164">이 방식은 관계형 테이블 데이터를 저장하는 전통적인 방법이었습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-164">This has been the traditional way to store relational table data.</span></span>

 <span data-ttu-id="05ad9-165">행 그룹 및 열 세그먼트-고성능 및 높은 압축률을 위해 columnstore 인덱스는 테이블을 행 그룹 이라는 행 그룹으로 분할 한 다음 열 단위 방식으로 각 행 그룹을 압축 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-165">rowgroups and column segments For high performance and high compression rates, the columnstore index slices the table into groups of rows, called row groups, and then compresses each row group in a column-wise manner.</span></span> <span data-ttu-id="05ad9-166">행 그룹의 행 수는 압축률을 높일 만큼 크고, 메모리 내 작업을 활용할 만큼 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-166">The number of rows in the row group must be large enough to improve compression rates, and small enough to benefit from in-memory operations.</span></span>

 <span data-ttu-id="05ad9-167">행 그룹 A *행 그룹* 은 columnstore 형식으로 동시에 압축 되는 행의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-167">row group A *rowgroup* is a group of rows that are compressed into columnstore format at the same time.</span></span>

 <span data-ttu-id="05ad9-168">열 세그먼트 *열 세그먼트* 는 행 그룹 내의 데이터 열입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-168">column segment A *column segment* is a column of data from within the rowgroup.</span></span>

-   <span data-ttu-id="05ad9-169">열 그룹에는 대개 1,048,576개(행 그룹당 최대 행 수)의 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-169">A rowgroup usually contains the maximum number of rows per rowgroup which is 1,048,576 rows.</span></span>

-   <span data-ttu-id="05ad9-170">각 행 그룹에는 테이블의 모든 열에 대해 각각 하나의 열 세그먼트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-170">Each rowgroup contains one column segment for every column in the table.</span></span>

-   <span data-ttu-id="05ad9-171">각 열 세그먼트는 함께 압축되며 실제 미디어에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-171">Each column segment is compressed together and stored on physical media.</span></span>

 <span data-ttu-id="05ad9-172">![열 세그먼트](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "열 세그먼트")</span><span class="sxs-lookup"><span data-stu-id="05ad9-172">![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")</span></span>

 <span data-ttu-id="05ad9-173">비클러스터형 columnstore 인덱스 *비클러스터형 columnstore 인덱스* 는 기존 클러스터형 인덱스 또는 힙 테이블에 생성 된 읽기 전용 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-173">nonclustered columnstore index A *nonclustered columnstore index* is a read-only index created on an existing clustered index or heap table.</span></span> <span data-ttu-id="05ad9-174">여기에는 테이블의 모든 열을 포함한 열 하위 집합의 복사본이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-174">It contains a copy of a subset of columns, up to and including all of the columns in the table..</span></span> <span data-ttu-id="05ad9-175">테이블은 비클러스터형 columnstore 인덱스를 포함 하는 동안 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-175">The table is read-only while it contains a nonclustered columnstore index.</span></span>

 <span data-ttu-id="05ad9-176">비클러스터형 columnstore 인덱스는 원래 테이블에 대해 읽기 전용 작업을 수행하면서 동시에 분석 쿼리를 실행하기 위해 columnstore 인덱스를 포함하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-176">A nonclustered columnstore index provides a way to have a columnstore index for running analysis queries while at the same time performing read-only operations on the original table.</span></span>

 <span data-ttu-id="05ad9-177">![비클러스터형 columnstore 인덱스](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "비클러스터형 columnstore 인덱스")</span><span class="sxs-lookup"><span data-stu-id="05ad9-177">![Nonclustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "Nonclustered columnstore index")</span></span>

 <span data-ttu-id="05ad9-178">클러스터형 columnstore 인덱스 *클러스터형 columnstore 인덱스* 는 전체 테이블에 대 한 물리적 저장소 이며 테이블의 유일한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-178">clustered columnstore index A *clustered columnstore index* is the physical storage for the entire table and is the only index for the table.</span></span> <span data-ttu-id="05ad9-179">클러스터형 인덱스는 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-179">The clustered index is updateable.</span></span> <span data-ttu-id="05ad9-180">인덱스에 대해 삽입, 삭제 및 업데이트 작업을 수행할 수 있으며, 인덱스로 데이터를 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-180">You can perform insert, delete, and update operations on the index and you can bulk load data into the index.</span></span>

 <span data-ttu-id="05ad9-181">![클러스터형 Columnstore 인덱스](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "클러스터형 Clustered 인덱스")</span><span class="sxs-lookup"><span data-stu-id="05ad9-181">![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")</span></span>

 <span data-ttu-id="05ad9-182">열 세그먼트의 조각화를 줄이고 성능을 향상시키기 위해 columnstore 인덱스는 삭제된 행에 대한 ID의 B-트리와 함께 deltastore라는 rowstore 테이블에 일부 데이터를 임시로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-182">To reduce fragmentation of the column segments and improve performance, the columnstore index might store some data temporarily into a rowstore table, called a deltastore, plus a B-Tree of IDs for deleted rows.</span></span> <span data-ttu-id="05ad9-183">deltastore 작업은 백그라운드에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-183">The deltastore operations are handled behind the scenes.</span></span> <span data-ttu-id="05ad9-184">정확한 쿼리 결과를 반환하기 위해 클러스터형 columnstore 인덱스는 columnstore와 deltastore의 쿼리 결과를 모두 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-184">To return the correct query results, the clustered columnstore index combines query results from both the columnstore and the deltastore.</span></span>

 <span data-ttu-id="05ad9-185">deltastore는 클러스터형 columnstore 인덱스에만 사용 되며, *deltastore* 는 행 수가 columnstore로 이동 하기에 충분히 클 때까지 행을 저장 하는 rowstore 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-185">deltastore Used with clustered columnstore indexes only, a *deltastore* is a rowstore table that stores rows until the number of rows is large enough to be moved into the columnstore.</span></span> <span data-ttu-id="05ad9-186">deltastore는 다른 DML 작업과 로드 성능을 향상을 위해 클러스터형 columnstore 인덱스와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-186">A deltastore is used with clustered columnstore indexes to improve performance for loading and other DML operations.</span></span>

 <span data-ttu-id="05ad9-187">대규모 대량 로드 중에 대부분의 행은 deltastore를 통과하지 않고 columnstore로 곧바로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-187">During a large bulk load, most of the rows go directly to the columnstore without passing through the deltastore.</span></span> <span data-ttu-id="05ad9-188">대량 로드 끝부분의 일부 행은 수가 너무 적어서 행 그룹의 최소 크기(102,400개 행)에 맞지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-188">Some rows at the end of the bulk load might be too few in number to meet the minimum size of a rowgroup which is 102,400 rows.</span></span> <span data-ttu-id="05ad9-189">이 경우 최종 행은 columnstore 대신 deltastore로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-189">When this happens, the final rows go to the deltastore instead of the columnstore.</span></span> <span data-ttu-id="05ad9-190">행 수가 102,400개 미만인 소규모 대량 로드의 경우 모든 행이 deltastore로 곧바로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-190">For small bulk loads with less than 102,400 rows, all of the rows go directly to the deltastore.</span></span>

 <span data-ttu-id="05ad9-191">deltastore가 최대 행 수에 도달하면 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-191">When the deltastore reaches the maximum number of rows, it becomes closed.</span></span> <span data-ttu-id="05ad9-192">tuple-move 프로세스는 닫힌 행 그룹이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-192">A tuple-move process checks for closed row groups.</span></span> <span data-ttu-id="05ad9-193">닫힌 행 그룹을 찾으면 압축하여 columnstore에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-193">When it finds the closed rowgroup, it compresses it and stores it into the columnstore.</span></span>

##  <a name="loading-data"></a><a name="dataload"></a><span data-ttu-id="05ad9-194">데이터 로드 중</span><span class="sxs-lookup"><span data-stu-id="05ad9-194">Loading Data</span></span>

###  <a name="loading-data-into-a-nonclustered-columnstore-index"></a><a name="dataload_nci"></a><span data-ttu-id="05ad9-195">비클러스터형 Columnstore 인덱스로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="05ad9-195">Loading Data into a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="05ad9-196">비클러스터형 columnstore 인덱스로 데이터를 로드 하려면 먼저 힙 또는 클러스터형 인덱스로 저장 된 기존의 rowstore 테이블로 데이터를 로드 한 다음 [CREATE COLUMNSTORE index &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)를 사용 하 여 비클러스터형 columnstore 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-196">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then create the nonclustered columnstore index with [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

 <span data-ttu-id="05ad9-197">![데이터를 columnstore 인덱스로 로드](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "데이터를 columnstore 인덱스로 로드")</span><span class="sxs-lookup"><span data-stu-id="05ad9-197">![Loading data into a columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

 <span data-ttu-id="05ad9-198">비클러스터형 columnstore 인덱스가 있는 테이블은 인덱스가 삭제되거나 비활성화될 때까지 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-198">A table with a nonclustered columnstore index is read-only until the index is dropped or disabled.</span></span> <span data-ttu-id="05ad9-199">테이블과 비클러스터형 columnstore 인덱스를 업데이트 하려면 파티션을 내부 및 외부로 전환할 수 있습니다. 인덱스를 사용 하지 않도록 설정 하 고 테이블을 업데이트 한 다음 인덱스를 다시 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-199">To update the table and the nonclustered columnstore index you can switch partitions in and out. You can also disable the index, update the table, and then rebuild the index.</span></span>

 <span data-ttu-id="05ad9-200">자세한 내용은 [Using Nonclustered Columnstore Indexes](indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05ad9-200">For more information see [Using Nonclustered Columnstore Indexes](indexes.md)</span></span>

###  <a name="loading-data-into-a-clustered-columnstore-index"></a><a name="dataload_cci"></a><span data-ttu-id="05ad9-201">클러스터형 Columnstore 인덱스로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="05ad9-201">Loading Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="05ad9-202">![클러스터형 columnstore 인덱스로 로드](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "클러스터형 columnstore 인덱스로 로드")</span><span class="sxs-lookup"><span data-stu-id="05ad9-202">![Loading into a clustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Loading into a clustered columnstore index")</span></span>

 <span data-ttu-id="05ad9-203">다이어그램과 같이, 클러스터형 columnstore 인덱스에 데이터를 로드하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-203">As the diagram suggests, to load data into a clustered columnstore index, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

1.  <span data-ttu-id="05ad9-204">최대 크기의 행 그룹을 columnstore에 직접 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-204">Inserts maximum-size rowgroups directly into the columnstore.</span></span> <span data-ttu-id="05ad9-205">데이터가 로드되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]은 열려 있는 행 그룹에 데이터 행을 선착순으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-205">As the data is loaded, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns the data rows in a first-come first-serve order into an open rowgroup.</span></span>

2.  <span data-ttu-id="05ad9-206">각 행 그룹에 대해 행 그룹이 최대 크기에 도달한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-206">For each rowgroup, after it reaches the maximum size, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

    1.  <span data-ttu-id="05ad9-207">행 그룹을 CLOSED로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-207">Marks the rowgroup as CLOSED.</span></span>

    2.  <span data-ttu-id="05ad9-208">deltastore를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-208">Bypasses the deltastore.</span></span>

    3.  <span data-ttu-id="05ad9-209">columnstore 압축을 사용하여 행 그룹이 있는 각 열 세그먼트를 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-209">Compresses each column segment with the rowgroup with columnstore compression.</span></span>

    4.  <span data-ttu-id="05ad9-210">각 압축 열 세그먼트를 columnstore에 물리적으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-210">Physically stores each compressed column segment into the columnstore.</span></span>

3.  <span data-ttu-id="05ad9-211">다음과 같이 나머지 행을 columnstore 또는 deltastore에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-211">Inserts the remaining rows into the columnstore or the deltastore as follows:</span></span>

    1.  <span data-ttu-id="05ad9-212">행 수가 행 그룹당 최대 행 요구 사항을 충족하면 행이 columnstore에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-212">If the number of rows meets the minimum rows per rowgroup requirement, the rows are added to the columnstore.</span></span>

    2.  <span data-ttu-id="05ad9-213">행 수가 행 그룹당 최대 행보다 적으면 행이 deltastore에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-213">If the number of rows is less than the minimum rows per rowgroup, the rows are added to the deltastore.</span></span>

 <span data-ttu-id="05ad9-214">deltastore 태스크와 프로세스에 대한 자세한 내용은 [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05ad9-214">For more information about deltastore tasks and processes, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)</span></span>

##  <a name="performance-tips"></a><a name="performance"></a><span data-ttu-id="05ad9-215">성능 팁</span><span class="sxs-lookup"><span data-stu-id="05ad9-215">Performance Tips</span></span>

### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a><span data-ttu-id="05ad9-216">병렬로 columnstore 인덱스를 만들기에 충분한 메모리 계획</span><span class="sxs-lookup"><span data-stu-id="05ad9-216">Plan for enough memory to create columnstore indexes in parallel</span></span>
 <span data-ttu-id="05ad9-217">인덱스 만들기는 메모리가 제한되지 않는 한 기본적으로 병렬 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-217">Creating a columnstore index is by default a parallel operation unless memory is constrained.</span></span> <span data-ttu-id="05ad9-218">병렬로 인덱스를 만들려면 직렬로 인덱스를 만들 때보다 많은 메모리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-218">Creating the index in parallel requires more memory than creating the index serially.</span></span> <span data-ttu-id="05ad9-219">메모리가 충분하면 동일한 열에 B-트리를 작성할 때보다 1.5배 많은 메모리가 columnstore 인덱스를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-219">When there is ample memory, creating a columnstore index takes on the order of 1.5 times as long as building a B-tree on the same columns.</span></span>

 <span data-ttu-id="05ad9-220">columnstore 인덱스를 만드는 데 필요한 메모리는 열 수, 문자열 열 수, DOP(병렬 처리 수준) 및 데이터의 특징에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-220">The memory required for creating a columnstore index depends on the number of columns, the number of string columns, the degree of parallelism (DOP), and the characteristics of the data.</span></span> <span data-ttu-id="05ad9-221">예를 들어, 테이블의 행 수가 100만 개 미만일 경우 SQL Server는 한 스레드만 사용하여 columnstore 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-221">For example, if your table has fewer than one million rows, SQL Server will use only one thread to create the columnstore index.</span></span>

 <span data-ttu-id="05ad9-222">테이블 행 수가 100만 개 이상이지만 SQL Server에서 MAXDOP를 사용하여 인덱스를 만들기에 충분한 메모리 부여를 얻을 수 없는 경우 SQL Server에서 사용 가능한 메모리 부여에 맞게 필요한 만큼 자동으로 MAXDOP를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-222">If your table has more than one million rows, but SQL Server cannot get a large enough memory grant to create the index using MAXDOP, SQL Server will automatically decrease MAXDOP as needed to fit into the available memory grant.</span></span>  <span data-ttu-id="05ad9-223">일부 경우 제한된 메모리로 인덱스를 작성하도록 DOP를 줄여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-223">In some cases, DOP must be decreased to one in order to build the index under constrained memory.</span></span>

##  <a name="related-tasks-and-topics"></a><a name="related"></a><span data-ttu-id="05ad9-224">관련 태스크 및 항목</span><span class="sxs-lookup"><span data-stu-id="05ad9-224">Related Tasks and Topics</span></span>

### <a name="nonclustered-columnstore-indexes"></a><span data-ttu-id="05ad9-225">비클러스터형 columnstore 인덱스</span><span class="sxs-lookup"><span data-stu-id="05ad9-225">Nonclustered Columnstore Indexes</span></span>
 <span data-ttu-id="05ad9-226">일반 태스크는 [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05ad9-226">For common tasks, see [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="05ad9-227">CREATE COLUMNSTORE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-227">CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="05ad9-228">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql) (다시 작성).</span><span class="sxs-lookup"><span data-stu-id="05ad9-228">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD.</span></span>

-   [<span data-ttu-id="05ad9-229">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-229">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

### <a name="clustered-columnstore-indexes"></a><span data-ttu-id="05ad9-230">클러스터형 columnstore 인덱스</span><span class="sxs-lookup"><span data-stu-id="05ad9-230">Clustered Columnstore Indexes</span></span>
 <span data-ttu-id="05ad9-231">일반 태스크는 [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05ad9-231">For common tasks, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="05ad9-232">Transact-sql&#41;&#40;클러스터형 COLUMNSTORE 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="05ad9-232">CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="05ad9-233">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql) 다시 작성 하거나 다시 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-233">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD or REORGANIZE.</span></span>

-   [<span data-ttu-id="05ad9-234">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-234">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

-   [<span data-ttu-id="05ad9-235">INSERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-235">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)

-   [<span data-ttu-id="05ad9-236">UPDATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-236">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)

-   [<span data-ttu-id="05ad9-237">DELETE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-237">DELETE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/delete-transact-sql)

### <a name="metadata"></a><span data-ttu-id="05ad9-238">메타데이터</span><span class="sxs-lookup"><span data-stu-id="05ad9-238">Metadata</span></span>
 <span data-ttu-id="05ad9-239">columnstore 인덱스에 있는 모든 열이 메타데이터에 포괄 열로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-239">All of the columns in a columnstore index are stored in the metadata as included columns.</span></span> <span data-ttu-id="05ad9-240">columnstore 인덱스에는 키 열이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05ad9-240">The columnstore index does not have key columns.</span></span>

-   [<span data-ttu-id="05ad9-241">sys.indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-241">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)

-   [<span data-ttu-id="05ad9-242">sys.index_columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-242">sys.index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)

-   [<span data-ttu-id="05ad9-243">sys.partitions&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-243">sys.partitions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)

-   [<span data-ttu-id="05ad9-244">sys.column_store_segments&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-244">sys.column_store_segments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)

-   [<span data-ttu-id="05ad9-245">sys.column_store_dictionaries&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-245">sys.column_store_dictionaries &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)

-   [<span data-ttu-id="05ad9-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05ad9-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)


