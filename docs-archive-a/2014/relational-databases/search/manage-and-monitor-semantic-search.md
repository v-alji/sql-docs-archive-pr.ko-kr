---
title: 의미 체계 검색 관리 및 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733763"
---
# <a name="manage-and-monitor-semantic-search"></a><span data-ttu-id="29414-102">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="29414-102">Manage and Monitor Semantic Search</span></span>
  <span data-ttu-id="29414-103">의미 체계 인덱싱의 과정과 인덱스를 모니터링하고 관리하는 데 관련된 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-103">Describes the process of semantic indexing and the tasks related to managing and monitoring the indexes.</span></span>  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a><span data-ttu-id="29414-104">방법: 의미 체계 인덱싱의 상태 확인</span><span class="sxs-lookup"><span data-stu-id="29414-104">How To: Check the Status of Semantic Indexing</span></span>  
 <span data-ttu-id="29414-105">**의미 체계 인덱싱의 첫 번째 단계가 완료되었는지 확인**</span><span class="sxs-lookup"><span data-stu-id="29414-105">**Is the first phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="29414-106">동적 관리 뷰 [sys.dm_fts_index_population&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)을 쿼리하고 **status** 및 **status_description** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-106">Query the dynamic management view, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), and check the **status** and **status_description** columns.</span></span>  
  
 <span data-ttu-id="29414-107">인덱싱의 첫 번째 단계에는 문서 유사성 데이터의 추출뿐만 아니라 전체 텍스트 키워드 인덱스와 의미 체계 키 구 인덱스의 채우기도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="29414-107">The first phase of indexing includes the population of the full-text keyword index and the semantic key phrase index, as well as the extraction of document similarity data.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="29414-108">**의미 체계 인덱싱의 두 번째 단계가 완료되었는지 확인**</span><span class="sxs-lookup"><span data-stu-id="29414-108">**Is the second phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="29414-109">동적 관리 뷰 [sys.dm_fts_semantic_similarity_population&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)을 쿼리하고 **status** 및 **status_description** 열을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-109">Query the dynamic management view, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), and check the **status** and **status_description** columns..</span></span>  
  
 <span data-ttu-id="29414-110">인덱싱의 두 번째 단계에는 의미 체계적 문서 유사성 인덱스의 채우기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="29414-110">The second phase of indexing includes the population of the semantic document similarity index.</span></span>  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a><span data-ttu-id="29414-111">방법: 의미 체계 인덱스의 크기 확인</span><span class="sxs-lookup"><span data-stu-id="29414-111">How To: Check the Size of the Semantic Indexes</span></span>  
 <span data-ttu-id="29414-112">**의미 체계 키 구 인덱스 또는 의미 체계 문서 유사성 인덱스의 논리적 크기 확인**</span><span class="sxs-lookup"><span data-stu-id="29414-112">**What is the logical size of a semantic key phrase index or a semantic document similarity index?**</span></span>  
 <span data-ttu-id="29414-113">동적 관리 뷰 [sys.dm_db_fts_index_physical_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-113">Query the dynamic management view, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="29414-114">논리적 크기는 인덱스 페이지의 수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="29414-114">The logical size is displayed in number of index pages.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="29414-115">**전체 텍스트 카탈로그에 대한 전체 텍스트 및 의미 체계 인덱스의 총 크기 확인**</span><span class="sxs-lookup"><span data-stu-id="29414-115">**What is the total size of the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="29414-116">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 메타데이터 함수의 **IndexSize** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-116">Query the **IndexSize** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 <span data-ttu-id="29414-117">**전체 텍스트 카탈로그에 대한 전체 텍스트 및 의미 체계 인덱스에서 인덱싱된 항목 수 확인**</span><span class="sxs-lookup"><span data-stu-id="29414-117">**How many items are indexed in the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="29414-118">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 메타데이터 함수의 **ItemCount** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-118">Query the **ItemCount** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a><span data-ttu-id="29414-119">방법: 의미 체계 인덱스의 채우기 적용</span><span class="sxs-lookup"><span data-stu-id="29414-119">How To: Force the Population of the Semantic Indexes</span></span>  
 <span data-ttu-id="29414-120">전체 텍스트 인덱스에 대해 설명한 것과 구문 및 동작이 동일한 START/STOP/PAUSE 또는 RESUME POPULATION 절을 사용하여 전체 텍스트 및 의미 체계 인덱스의 채우기를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29414-120">You can force the population of full-text and semantic indexes by using the START/STOP/PAUSE or RESUME POPULATION clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="29414-121">자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 및 [전체 텍스트 인덱스 채우기](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29414-121">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) and [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="29414-122">의미 체계 인덱싱은 전체 텍스트 인덱싱에 따라 달라지므로 의미 체계 인덱스는 연결된 전체 텍스트 인덱스가 채워진 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="29414-122">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="29414-123">**예: 전체 텍스트 및 의미 체계 인덱스의 전체 채우기 시작**</span><span class="sxs-lookup"><span data-stu-id="29414-123">**Example: Start a full population of full-text and semantic indexes**</span></span>  
  
 <span data-ttu-id="29414-124">다음 예에서는 AdventureWorks2012 예제 데이터베이스의 **Production.Document** 테이블에 대한 기존의 전체 텍스트 인덱스를 변경하여 전체 텍스트 및 의미 체계 인덱스 모두에 대한 전체 채우기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-124">The following example starts full population of both full-text and semantic indexes by altering an existing full-text index on the **Production.Document** table in the AdventureWorks2012 sample database.</span></span>  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a><span data-ttu-id="29414-125">방법: 의미 체계 인덱싱 해제 또는 다시 설정</span><span class="sxs-lookup"><span data-stu-id="29414-125">How To: Disable or Re-enable Semantic Indexing</span></span>  
 <span data-ttu-id="29414-126">전체 텍스트 인덱스에 대해 설명한 것과 구문 및 동작이 동일한 ENABLE/DISABLE 절을 사용하여 전체 텍스트 또는 의미 체계 인덱싱을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29414-126">You can enable or disable full-text or semantic indexing by using the ENABLE/DISABLE clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="29414-127">자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29414-127">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="29414-128">의미 체계 인덱싱이 사용하지 않도록 설정되거나 일시 중지된 경우에도 의미 체계 데이터에 대한 쿼리는 계속 작동하여 이전에 인덱싱된 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-128">When semantic indexing is disabled and suspended, queries over semantic data continue to work successfully and to return previously indexed data.</span></span> <span data-ttu-id="29414-129">이 동작은 전체 텍스트 검색의 동작과 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29414-129">This behavior is not consistent with the behavior of Full-Text Search.</span></span>  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a><span data-ttu-id="29414-130">의미 체계 인덱싱의 단계</span><span class="sxs-lookup"><span data-stu-id="29414-130">Phases of Semantic Indexing</span></span>  
 <span data-ttu-id="29414-131">의미 체계 검색에서는 의미 체계 검색을 사용하도록 설정된 각 열에 대해 다음 두 종류의 데이터를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="29414-131">Semantic Search indexes two kinds of data for each column on which it is enabled:</span></span>  
  
1.  <span data-ttu-id="29414-132">**핵심 구**</span><span class="sxs-lookup"><span data-stu-id="29414-132">**Key phrases**</span></span>  
  
2.  <span data-ttu-id="29414-133">**문서 유사성**</span><span class="sxs-lookup"><span data-stu-id="29414-133">**Document similarity**</span></span>  
  
 <span data-ttu-id="29414-134">의미 체계 인덱싱은 전체 텍스트 인덱싱과 함께 다음 두 단계로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="29414-134">Semantic indexing occurs in two phases, in conjunction with full-text indexing:</span></span>  
  
1.  <span data-ttu-id="29414-135">**단계 1**</span><span class="sxs-lookup"><span data-stu-id="29414-135">**Phase 1**.</span></span> <span data-ttu-id="29414-136">전체 텍스트 키워드 인덱스와 의미 체계 키 구 인덱스가 동시에 병렬로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="29414-136">The full-text keyword index and the semantic key phrase index are populated in parallel at the same time.</span></span> <span data-ttu-id="29414-137">이때 문서 유사성을 인덱싱하는 데 필요한 데이터도 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="29414-137">The data required to index document similarity is also extracted at this time.</span></span>  
  
2.  <span data-ttu-id="29414-138">**단계 2**:</span><span class="sxs-lookup"><span data-stu-id="29414-138">**Phase 2**.</span></span> <span data-ttu-id="29414-139">그런 다음 의미 체계 문서 유사성 인덱스가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="29414-139">The semantic document similarity index is then populated.</span></span> <span data-ttu-id="29414-140">이 인덱스는 이전 단계에서 채워진 두 인덱스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="29414-140">This index depends on both indexes that were populated in the preceding phase.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a><span data-ttu-id="29414-141">문제: 의미 체계 인덱스가 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29414-141">Problem: Semantic Indexes Are Not Populated</span></span>  
 <span data-ttu-id="29414-142">**연결된 전체 텍스트 인덱스가 채워졌습니까?**</span><span class="sxs-lookup"><span data-stu-id="29414-142">**Are the associated full-text indexes populated?**</span></span>  
 <span data-ttu-id="29414-143">의미 체계 인덱싱은 전체 텍스트 인덱싱에 따라 달라지므로 의미 체계 인덱스는 연결된 전체 텍스트 인덱스가 채워진 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="29414-143">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="29414-144">**전체 텍스트 검색 및 의미 체계 검색이 올바르게 설치 및 구성되어 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="29414-144">**Are full-text search and semantic search properly installed and configured?**</span></span>  
 <span data-ttu-id="29414-145">자세한 내용은 [의미 체계 검색 설치 및 구성](install-and-configure-semantic-search.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29414-145">For more information, see [Install and Configure Semantic Search](install-and-configure-semantic-search.md).</span></span>  
  
 <span data-ttu-id="29414-146">**FDHOST 서비스를 사용할 수 없거나 전체 텍스트 인덱싱이 실패할 만한 다른 조건이 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="29414-146">**Is the FDHOST service not available, or is there another condition that would cause full-text indexing to fail?**</span></span>  
 <span data-ttu-id="29414-147">자세한 내용은 [전체 텍스트 인덱싱 문제 해결](troubleshoot-full-text-indexing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29414-147">For more information, see [Troubleshoot Full-Text Indexing](troubleshoot-full-text-indexing.md).</span></span>  
  
  
