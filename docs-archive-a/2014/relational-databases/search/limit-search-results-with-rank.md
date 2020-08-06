---
title: RANK를 사용하여 검색 결과 제한 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- row ranking [full-text search]
- relevance ranking values [full-text search]
- full-text search [SQL Server], rankings
- index rankings [full-text search]
- ranked results [full-text search]
- rankings [full-text search]
- per-row rank values [full-text search]
ms.assetid: 06a776e6-296c-4ec7-9fa5-0794709ccb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1b930b3238cb541965e1984d1561f1a1c22d87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733776"
---
# <a name="limit-search-results-with-rank"></a><span data-ttu-id="2d255-102">RANK를 사용하여 검색 결과 제한</span><span class="sxs-lookup"><span data-stu-id="2d255-102">Limit Search Results with RANK</span></span>
  <span data-ttu-id="2d255-103">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 함수는 0부터 1000까지의 서수 값(순위 값)이 포함된 RANK라는 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-103">The [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) functions return a column named RANK that contains ordinal values from 0 through 1000 (rank values).</span></span> <span data-ttu-id="2d255-104">이러한 값은 반환된 행이 선택 조건에 얼마나 일치하는지에 따라 순위를 매기는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-104">These values are used to rank the rows returned according to how well they match the selection criteria.</span></span> <span data-ttu-id="2d255-105">순위 값은 결과 집합에 포함된 행의 관련성을 나타내는 상대적 순서일 뿐이며 값이 작을수록 관련이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-105">The rank values indicate only a relative order of relevance of the rows in the result set, with a lower value indicating lower relevance.</span></span> <span data-ttu-id="2d255-106">실제 값은 중요하지 않으며 일반적으로 쿼리가 실행될 때마다 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-106">The actual values are unimportant and typically differ each time the query is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d255-107">CONTAINS 및 FREETEXT 조건자는 순위 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-107">The CONTAINS and FREETEXT predicates do not return any rank values.</span></span>  
  
 <span data-ttu-id="2d255-108">검색 조건과 일치하는 항목 수는 종종 매우 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-108">The number of items matching a search condition is often very large.</span></span> <span data-ttu-id="2d255-109">CONTAINSTABLE 또는 FREETEXTTABLE 쿼리가 반환하는 일치하는 항목 수를 줄이려면 행의 하위 집합만 반환하는 선택적 *top_n_by_rank* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-109">To prevent CONTAINSTABLE or FREETEXTTABLE queries from returning too many matches, use the optional *top_n_by_rank* parameter, which returns only a subset of rows.</span></span> <span data-ttu-id="2d255-110">*top_n_by_rank* 는 내림차순으로 최고 등급 *n*개의 일치하는 항목만 반환되도록 지정하는 정수 값 *n* 입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-110">*top_n_by_rank* is an integer value, *n*, that specifies that only the *n* highest ranked matches are to be returned, in descending order.</span></span> <span data-ttu-id="2d255-111">*top_n_by_rank* 를 다른 매개 변수와 함께 사용하면 실제로 모든 조건자와 일치하는 행 수보다 적은 수의 행이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-111">If *top_n_by_rank* is combined with other parameters, the query could return fewer rows than the number of rows that actually match all the predicates.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="2d255-112">는 일치하는 항목을 순위별로 정렬하고 지정한 개수만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-112">orders the matches by rank and returns only up to the specified number of rows.</span></span> <span data-ttu-id="2d255-113">이 방법을 사용하면 성능이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-113">This choice can result in a dramatic increase in performance.</span></span> <span data-ttu-id="2d255-114">예를 들어 백만 개의 행이 있는 테이블에서 100,000개의 행을 반환하는 쿼리에 대해 상위 100개의 행만 요청하면 쿼리가 훨씬 빨리 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-114">For example, a query that would normally return 100,000 rows from a table of one million rows are processed more quickly if only the top 100 rows are requested.</span></span>  
  
##  <a name="examples-of-using-rank-to-limit-search-results"></a><a name="examples"></a> <span data-ttu-id="2d255-115">순위를 사용하여 검색 결과를 제한하는 예</span><span class="sxs-lookup"><span data-stu-id="2d255-115">Examples of Using RANK to Limit Search Results</span></span>  
  
### <a name="example-a-searching-for-only-the-top-three-matches"></a><span data-ttu-id="2d255-116">예 A: 상위 3개의 일치하는 항목만 검색</span><span class="sxs-lookup"><span data-stu-id="2d255-116">Example A: Searching for only the top three matches</span></span>  
 <span data-ttu-id="2d255-117">다음 예제에서는 CONTAINSTABLE을 사용하여 상위 3개의 일치하는 항목만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-117">The following example uses CONTAINSTABLE to return only the top three matches.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT K.RANK, AddressLine1, City  
FROM Person.Address AS A  
  INNER JOIN  
  CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("des*",  
    Rue WEIGHT(0.5),  
    Bouchers WEIGHT(0.9))',  
    3) AS K  
  ON A.AddressID = K.[KEY]  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
RANK        Address                          City  
----------- -------------------------------- ------------------------------  
172         9005, rue des Bouchers           Paris  
172         5, rue des Bouchers              Orleans  
172         5, rue des Bouchers              Metz  
  
(3 row(s) affected)  
```  
  
  
### <a name="example-b-searching-for-the-top-ten-matches"></a><span data-ttu-id="2d255-118">예 B: 상위 10개의 일치하는 항목 검색</span><span class="sxs-lookup"><span data-stu-id="2d255-118">Example B: Searching for the top ten matches</span></span>  
 <span data-ttu-id="2d255-119">다음 예에서는 CONTAINSTABLE을 사용하여 `Description` 열에 "light"나 "lightweight"라는 단어와 근접한 "aluminum"이라는 단어가 포함된 상위 5개 제품에 대한 설명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-119">The following example uses CONTAINSTABLE to return the description of the top 5 products where the `Description` column contains the word "aluminum" near either the word "light" or the word "lightweight".</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
GO  
```  
  
  
##  <a name="how-search-query-results-are-ranked"></a><a name="how"></a> <span data-ttu-id="2d255-120">검색 쿼리 결과의 순위를 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="2d255-120">How Search Query Results Are Ranked</span></span>  
 <span data-ttu-id="2d255-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 전체 텍스트 검색은 전체 텍스트 쿼리가 반환하는 데이터의 관련성을 나타내는 선택적 점수(또는 순위 값)를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-121">Full-text search in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can generate an optional score (or rank value) that indicates the relevance of the data returned by a full-text query.</span></span> <span data-ttu-id="2d255-122">이 순위 값은 모든 행에 대해 계산되고 지정된 쿼리의 결과 집합을 관련 순으로 정렬하는 정렬 조건으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-122">This rank value is calculated on every row and can be used as an ordering criteria to sort the result set of a given query by relevance.</span></span> <span data-ttu-id="2d255-123">순위 값은 결과 집합에 포함된 행의 관련성을 나타내는 상대적 순서일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-123">The rank values indicate only a relative order of relevance of the rows in the result set.</span></span> <span data-ttu-id="2d255-124">실제 값은 중요하지 않으며 일반적으로 쿼리가 실행될 때마다 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-124">The actual values are unimportant and typically differ each time the query is run.</span></span> <span data-ttu-id="2d255-125">순위 값은 전체 쿼리에서 아무 의미도 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-125">The rank value does not hold any significance across queries.</span></span>  
  
### <a name="statistics-for-ranking"></a><span data-ttu-id="2d255-126">순위용 통계</span><span class="sxs-lookup"><span data-stu-id="2d255-126">Statistics for Ranking</span></span>  
 <span data-ttu-id="2d255-127">인덱스를 작성할 때 순위에 사용할 통계가 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-127">When an index is built, statistics are collected for use in ranking.</span></span> <span data-ttu-id="2d255-128">전체 텍스트 카탈로그의 작성 과정에서 직접 단일 인덱스 구조가 생성되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-128">The process of building a full-text catalog does not directly result in a single index structure.</span></span> <span data-ttu-id="2d255-129">대신 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 용 전체 텍스트 검색 엔진은 데이터가 인덱싱될 때 중간 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-129">Instead, the Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] creates intermediate indexes as data is indexed.</span></span> <span data-ttu-id="2d255-130">그런 다음 전체 텍스트 검색 엔진은 필요에 따라 이러한 인덱스를 큰 인덱스로 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-130">The Full-Text Engine then merges these indexes into a larger index as needed.</span></span> <span data-ttu-id="2d255-131">이 프로세스는 여러 번 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-131">This process can be repeated many times.</span></span> <span data-ttu-id="2d255-132">최종적으로 전체 텍스트 검색 엔진은 모든 중간 인덱스를 큰 마스터 인덱스로 결합하는 "마스터 병합"을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-132">The Full-Text Engine then conducts a "master merge" that combines all of the intermediate indexes into one large master index.</span></span>  
  
 <span data-ttu-id="2d255-133">통계는 각 중간 인덱스 수준에서 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-133">Statistics are collected at each intermediate index level.</span></span> <span data-ttu-id="2d255-134">인덱스를 병합할 때 통계도 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-134">The statistics are merged when the indexes are merged.</span></span> <span data-ttu-id="2d255-135">일부 통계 값은 마스터 병합 프로세스 중에만 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-135">Some statistical values can only be generated during the master merging process.</span></span>  
  
 <span data-ttu-id="2d255-136">쿼리 결과 집합의 순위를 지정할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 가장 큰 중간 인덱스의 통계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-136">While ranking a query result set, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses statistics from the largest intermediate index.</span></span> <span data-ttu-id="2d255-137">이는 중간 인덱스의 병합 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-137">This depends on whether intermediate indexes have been merged or not.</span></span> <span data-ttu-id="2d255-138">따라서 중간 인덱스가 병합되지 않은 경우 순위 통계의 정확도가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-138">As a result, ranking statistics can vary in accuracy if the intermediate indexes have not been merged.</span></span> <span data-ttu-id="2d255-139">이런 이유로 시간이 경과하면서 전체 텍스트 인덱싱된 데이터가 추가, 수정 및 삭제되고 작은 인덱스가 병합됨에 따라 동일한 쿼리에서 여러 순위 결과가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-139">This explains why the same query can return different rank results over time as full-text indexed data is added, modified, and deleted, and as the smaller indexes are merged.</span></span>  
  
 <span data-ttu-id="2d255-140">인덱스 크기와 복잡한 계산을 최소화하기 위해 통계를 반올림하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-140">To minimize the size of the index and computational complexity, statistics are often rounded.</span></span>  
  
 <span data-ttu-id="2d255-141">아래 목록에는 자주 사용하는 용어와 순위 계산 시 중요한 통계 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-141">The list below includes some commonly used terms and statistical values that are important in calculating rank.</span></span>  
  
 <span data-ttu-id="2d255-142">속성</span><span class="sxs-lookup"><span data-stu-id="2d255-142">Property</span></span>  
 <span data-ttu-id="2d255-143">행의 전체 텍스트 인덱싱된 열입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-143">A full-text indexed column of the row.</span></span>  
  
 <span data-ttu-id="2d255-144">문서</span><span class="sxs-lookup"><span data-stu-id="2d255-144">Document</span></span>  
 <span data-ttu-id="2d255-145">쿼리에서 반환된 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-145">The entity that is returned in queries.</span></span> <span data-ttu-id="2d255-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 문서는 행에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-146">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] this corresponds to a row.</span></span> <span data-ttu-id="2d255-147">행이 여러 개의 전체 텍스트 인덱싱된 열을 가질 수 있는 것처럼 문서는 여러 속성을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-147">A document can have multiple properties, just as a row can have multiple full-text indexed columns.</span></span>  
  
 <span data-ttu-id="2d255-148">인덱스</span><span class="sxs-lookup"><span data-stu-id="2d255-148">Index</span></span>  
 <span data-ttu-id="2d255-149">하나 이상의 문서에 대해 반전된 단일 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-149">A single inverted index of one or more documents.</span></span> <span data-ttu-id="2d255-150">인덱스 전체가 메모리나 디스크에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-150">This may be entirely in memory or on disk.</span></span> <span data-ttu-id="2d255-151">많은 쿼리 통계는 항목이 일치한 개별 인덱스를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-151">Many query statistics are relative to the individual index where the match occurred.</span></span>  
  
 <span data-ttu-id="2d255-152">전체 텍스트 카탈로그</span><span class="sxs-lookup"><span data-stu-id="2d255-152">Full-Text Catalog</span></span>  
 <span data-ttu-id="2d255-153">쿼리에 대해 하나의 엔터티로 처리되는 중간 인덱스 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-153">A collection of intermediate indexes treated as one entity for queries.</span></span> <span data-ttu-id="2d255-154">카탈로그는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 관리자에게 표시되는 조직 구성 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-154">Catalogs are the unit of organization visible to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="2d255-155">단어, 토큰 또는 항목</span><span class="sxs-lookup"><span data-stu-id="2d255-155">Word, token or item</span></span>  
 <span data-ttu-id="2d255-156">전체 텍스트 검색 엔진에서 일치하는 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-156">The unit of matching in the full-text engine.</span></span> <span data-ttu-id="2d255-157">문서의 텍스트 스트림은 언어별 단어 분리기에 의해 단어 또는 토큰으로 토큰화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-157">Streams of text from documents are tokenized into words, or tokens by language-specific word breakers.</span></span>  
  
 <span data-ttu-id="2d255-158">발생 빈도</span><span class="sxs-lookup"><span data-stu-id="2d255-158">Occurrence</span></span>  
 <span data-ttu-id="2d255-159">단어 분리기에서 결정된 문서 속성의 단어 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-159">The word offset in a document property as determined by the word breaker.</span></span> <span data-ttu-id="2d255-160">첫 번째 단어는 발생 빈도 1, 다음 단어는 발생 빈도 2 등으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-160">The first word is at occurrence 1, the next at 2, and so on.</span></span> <span data-ttu-id="2d255-161">구 및 근접 쿼리에서 잘못된 단어가 검색되는 것을 방지하기 위해 문장 끝(End-of-Sentence)과 단락 끝(End-of-Paragraph)으로 발생 간격을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-161">In order to avoid false positives in phrase and proximity queries, end-of-sentence and end-of-paragraph introduce larger occurrence gaps.</span></span>  
  
 <span data-ttu-id="2d255-162">TermFrequency</span><span class="sxs-lookup"><span data-stu-id="2d255-162">TermFrequency</span></span>  
 <span data-ttu-id="2d255-163">해당 키 값이 행에서 나오는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-163">The number times the key value occurs in a row.</span></span>  
  
 <span data-ttu-id="2d255-164">IndexedRowCount</span><span class="sxs-lookup"><span data-stu-id="2d255-164">IndexedRowCount</span></span>  
 <span data-ttu-id="2d255-165">인덱싱된 전체 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-165">Total number of rows indexed.</span></span> <span data-ttu-id="2d255-166">이 개수는 중간 인덱스에서 유지 관리되는 행 수를 기준으로 계산되므로</span><span class="sxs-lookup"><span data-stu-id="2d255-166">This is computed, based on counts maintained in the intermediate indexes.</span></span> <span data-ttu-id="2d255-167">정확도가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-167">This number can vary in accuracy.</span></span>  
  
 <span data-ttu-id="2d255-168">KeyRowCount</span><span class="sxs-lookup"><span data-stu-id="2d255-168">KeyRowCount</span></span>  
 <span data-ttu-id="2d255-169">전체 텍스트 카탈로그에서 지정된 키가 포함된 전체 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-169">Total number of rows in the full-text catalog that contain a given key.</span></span>  
  
 <span data-ttu-id="2d255-170">MaxOccurrence</span><span class="sxs-lookup"><span data-stu-id="2d255-170">MaxOccurrence</span></span>  
 <span data-ttu-id="2d255-171">지정된 행 속성에 대해 전체 텍스트 카탈로그에 저장된 최대 발생 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-171">The largest occurrence stored in a full-text catalog for a given property in a row.</span></span>  
  
 <span data-ttu-id="2d255-172">MaxQueryRank</span><span class="sxs-lookup"><span data-stu-id="2d255-172">MaxQueryRank</span></span>  
 <span data-ttu-id="2d255-173">전체 텍스트 검색 엔진에서 반환된 최대 순위로 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-173">The maximum rank, 1000, returned by the Full-Text Engine.</span></span>  
  
  
### <a name="rank-computation-issues"></a><span data-ttu-id="2d255-174">순위 계산 문제</span><span class="sxs-lookup"><span data-stu-id="2d255-174">Rank Computation Issues</span></span>  
 <span data-ttu-id="2d255-175">많은 요소가 순위 계산 과정에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-175">The process of computing rank, depends on a number of factors.</span></span>  <span data-ttu-id="2d255-176">각 언어별 단어 분리기는 텍스트를 다르게 토큰화합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-176">Different language word breakers tokenize text differently.</span></span> <span data-ttu-id="2d255-177">예를 들어 "dog-house"란 문자열을 특정 단어 분리기는 "dog" "house"로 분리하고 다른 단어 분리기는 "dog-house"로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-177">For example, the string "dog-house" could be broken into "dog" "house" by one word breaker and into "dog-house" by another.</span></span> <span data-ttu-id="2d255-178">즉, 단어뿐만 아니라 문서 길이도 다르기 때문에 지정된 언어에 따라 일치 항목과 순위가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-178">This means that matching and ranking will vary based on the language specified, because not only are the words different, but so is the document length.</span></span> <span data-ttu-id="2d255-179">문서 길이의 차이는 모든 쿼리의 순위에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-179">The document length difference can affect ranking for all queries.</span></span>  
  
 <span data-ttu-id="2d255-180">`IndexRowCount`와 같은 통계는 크게 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-180">Statistics such as `IndexRowCount` can vary widely.</span></span> <span data-ttu-id="2d255-181">예를 들어 카탈로그의 마스터 인덱스에 20억 개 행이 있고 메모리 내 중간 인덱스에 하나의 새 문서가 인덱싱되면 메모리 내 인덱스의 문서 수를 기준으로 한 해당 문서의 순위와 마스터 인덱스 문서에 대한 순위에 차이가 생길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-181">For example, if a catalog has 2 billion rows in the master index, then one new document is indexed into an in-memory intermediate index, and ranks for that document based on the number of documents in the in-memory index could be skewed compared with ranks for documents from the master index.</span></span> <span data-ttu-id="2d255-182">이런 이유로 다수의 행이 인덱싱 또는 다시 인덱싱 채우기 후에는 ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 인덱스를 마스터 인덱스에 병합하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-182">For this reason, it is recommended that after any population that results in large number of rows being indexed or re-indexed the indexes be merged into a master index using the ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="2d255-183">또한 전체 텍스트 검색 엔진은 중간 인덱스의 개수와 크기 같은 매개 변수를 기준으로 인덱스를 자동으로 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-183">The Full-Text Engine will also automatically merge the indexes based on parameters such as the number and size of intermediate indexes.</span></span>  
  
 <span data-ttu-id="2d255-184">`MaxOccurrence` 값은 32개 범위 중 하나로 정규화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-184">`MaxOccurrence` values are normalized into 1 of 32 ranges.</span></span> <span data-ttu-id="2d255-185">예를 들어 이것은 50단어 길이의 문서가 100단어 길이의 문서와 동일하게 처리된다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-185">This means, for example, that a document 50 words long is treated the same as a document 100 words long.</span></span> <span data-ttu-id="2d255-186">정규화에 사용되는 표는 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-186">Below is the table used for normalization.</span></span> <span data-ttu-id="2d255-187">문서 길이는 인접 한 테이블 값 32과 128 사이의 범위에 있기 때문에 실제로는 동일한 길이인 128 (32 < `docLength` <= 128)로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-187">Because the document lengths are in the range between adjacent table values 32 and 128, they are effectively treated as having the same length, 128 (32 < `docLength` <= 128).</span></span>  
  
```  
{ 16, 32, 128, 256, 512, 725, 1024, 1450, 2048, 2896, 4096, 5792, 8192, 11585,   
16384, 23170, 28000, 32768, 39554, 46340, 55938, 65536, 92681, 131072, 185363,   
262144, 370727, 524288, 741455, 1048576, 2097152, 4194304 };  
  
```  
  
  
### <a name="ranking-of-containstable"></a><span data-ttu-id="2d255-188">CONTAINSTABLE 순위</span><span class="sxs-lookup"><span data-stu-id="2d255-188">Ranking of CONTAINSTABLE</span></span>  
 <span data-ttu-id="2d255-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 순위는 다음 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) ranking uses the following algorithm:</span></span>  
  
```  
StatisticalWeight = Log2( ( 2 + IndexedRowCount ) / KeyRowCount )  
Rank = min( MaxQueryRank, HitCount * 16 * StatisticalWeight / MaxOccurrence )  
```  
  
 <span data-ttu-id="2d255-190">구 일치는 `KeyRowCount`(구가 포함된 행 수)가 예상 개수이므로 부정확하고 실제 개수보다 많을 수 있는 점을 제외하고 개별 키와 마찬가지로 순위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-190">Phrase matches are ranked just like individual keys except that `KeyRowCount` (the number of rows containing the phrase) is estimated and can be inaccurate and higher than the actual number.</span></span>  
  
 <span data-ttu-id="2d255-191">**NEAR 순위**</span><span class="sxs-lookup"><span data-stu-id="2d255-191">**Ranking of NEAR**</span></span>  
  
 <span data-ttu-id="2d255-192">CONTAINSTABLE은 NEAR 옵션을 사용하여 서로 근접한 검색 단어를 두 개 이상 쿼리하는 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-192">CONTAINSTABLE supports querying for two or more search terms in proximity to each other by using the NEAR option.</span></span> <span data-ttu-id="2d255-193">반환된 각 행의 순위 값은 여러 매개 변수를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-193">The rank value of each returned row is based on several parameters.</span></span> <span data-ttu-id="2d255-194">하나의 주 순위 요인은 문서 길이에 대한 총 일치 항목( *적중*) 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-194">One major ranking factor is the total number of matches (or *hits*) relative to the length of the document.</span></span> <span data-ttu-id="2d255-195">따라서 100단어 문서와 900단어 문서에 동일한 일치 항목이 있는 경우 100단어 문서의 순위가 보다 높게 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-195">Thus, for example, if a 100-word document and a 900-word document contain identical matches, the 100-word document is ranked higher.</span></span>  
  
 <span data-ttu-id="2d255-196">행에서의 각 적중에 대한 총 길이도 해당 적중의 첫 번째 검색 용어와 마지막 검색 요소 간의 거리를 기준으로 하는 해당 행의 순위에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-196">The total length of each hit in a row will also contribute to the ranking of that row based on the distance between the first and last search terms of that hit.</span></span> <span data-ttu-id="2d255-197">이 거리가 더 가까울수록 적중이 행 순위 값에 끼치는 영향이 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-197">The smaller the distance, the more the hit contributes to the rank value of the row.</span></span> <span data-ttu-id="2d255-198">전체 텍스트 쿼리가 정수를 최대 거리로 지정하지 않는 경우 거리가 100개 논리적 용어 이상 떨어져 있는 적중만 포함하는 문서의 순위는 0이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-198">If a full-text query does not specify an integer as the maximum distance, a document that contains only hits whose distances are greater than 100 logical terms apart, will have a ranking of 0.</span></span>  
  
 <span data-ttu-id="2d255-199">**ISABOUT 순위**</span><span class="sxs-lookup"><span data-stu-id="2d255-199">**Ranking of ISABOUT**</span></span>  
  
 <span data-ttu-id="2d255-200">CONTAINSTABLE은 ISABOUT 옵션을 사용하여 가중치 용어를 쿼리하는 것을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-200">CONTAINSTABLE supports querying for weighted terms by using the ISABOUT option.</span></span> <span data-ttu-id="2d255-201">ISABOUT은 일반적인 정보 검색 용어로 벡터 공간 쿼리를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-201">ISABOUT is a vector-space query in traditional information retrieval terminology.</span></span> <span data-ttu-id="2d255-202">사용되는 기본 순위 알고리즘은 널리 알려진 수식인 Jaccard입니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-202">The default ranking algorithm used is Jaccard, a widely known formula.</span></span> <span data-ttu-id="2d255-203">순위는 쿼리의 각 단어에 대해 계산된 다음 아래에 설명된 것처럼 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-203">The ranking is computed for each term in the query and then combined as described below.</span></span>  
  
```  
ContainsRank = same formula used for CONTAINSTABLE ranking of a single term (above).  
Weight = the weight specified in the query for each term. Default weight is 1.  
WeightedSum = ??[key=1 to n] ContainsRankKey * WeightKey  
Rank =  ( MaxQueryRank * WeightedSum ) / ( ( ??[key=1 to n] ContainsRankKey^2 )   
      + ( ??[key=1 to n] WeightKey^2 ) - ( WeightedSum ) )  
  
```  
  
  
### <a name="ranking-of-freetexttable"></a><span data-ttu-id="2d255-204">FREETEXTTABLE 순위</span><span class="sxs-lookup"><span data-stu-id="2d255-204">Ranking of FREETEXTTABLE</span></span>  
 <span data-ttu-id="2d255-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 순위는 OKAPI BM25 순위 수식을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) ranking is based on the OKAPI BM25 ranking formula.</span></span> <span data-ttu-id="2d255-206">FREETEXTTABLE 쿼리는 활용 생성(원래 쿼리 단어의 활용 형태)을 통해 쿼리에 단어를 추가합니다. 이러한 단어는 원래 단어와 특별한 관계없이 별도의 단어로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-206">FREETEXTTABLE queries will add words to the query via inflectional generation (inflected forms of the original query words); these words are treated as separate words with no special relationship to the words from which they were generated.</span></span> <span data-ttu-id="2d255-207">사전 기능에서 생성된 동의어도 가중치가 같은 별도의 단어로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-207">Synonyms generated from the Thesaurus feature are treated as separate, equally weighted terms.</span></span> <span data-ttu-id="2d255-208">쿼리의 각 단어가 순위에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d255-208">Each word in the query contributes to the rank.</span></span>  
  
```  
Rank = ??[Terms in Query] w ( ( ( k1 + 1 ) tf ) / ( K + tf ) ) * ( ( k3 + 1 ) qtf / ( k3 + qtf ) ) )  
Where:   
w is the Robertson-Sparck Jones weight.   
In simplified form, w is defined as:   
w = log10 ( ( ( r + 0.5 ) * ( N - R + r + 0.5 ) ) / ( ( R - r + 0.5 ) * ( n - r + 0.5 ) )  
N is the number of indexed rows for the property being queried.   
n is the number of rows containing the word.   
K is ( k1 * ( ( 1 - b ) + ( b * dl / avdl ) ) ).   
dl is the property length, in word occurrences.   
avdl is the average length of the property being queried, in word occurrences.   
k1, b, and k3 are the constants 1.2, 0.75, and 8.0, respectively.   
tf is the frequency of the word in the queried property in a specific row.   
qtf is the frequency of the term in the query.   
```  
  
  
## <a name="see-also"></a><span data-ttu-id="2d255-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d255-209">See Also</span></span>  
 [<span data-ttu-id="2d255-210">전체 텍스트 검색을 사용한 쿼리</span><span class="sxs-lookup"><span data-stu-id="2d255-210">Query with Full-Text Search</span></span>](query-with-full-text-search.md)  
  
  
