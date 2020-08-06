---
title: 전체 텍스트 검색을 사용한 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d78707925303d5e19d93b170f257d76fb7d1747d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732523"
---
# <a name="query-with-full-text-search"></a><span data-ttu-id="9e8a5-102">Query with Full-Text Search</span><span class="sxs-lookup"><span data-stu-id="9e8a5-102">Query with Full-Text Search</span></span>
  <span data-ttu-id="9e8a5-103">전체 텍스트 검색을 정의하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 쿼리는 전체 텍스트 조건자(CONTAINS 및 FREETEXT) 및 함수(CONTAINSTABLE 및 FREETEXTTABLE)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-103">To define full-text searches, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text queries use the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE.</span></span> <span data-ttu-id="9e8a5-104">이러한 조건자와 함수는 다양한 형태의 쿼리 용어를 지원하는 많은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-104">These support rich [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that supports a variety of forms of query terms.</span></span> <span data-ttu-id="9e8a5-105">전체 텍스트 쿼리를 작성하려면 이러한 조건자와 함수를 사용하는 시기와 방법을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-105">To write full-text queries, you must learn when and how to use these predicates and functions.</span></span>  
  
##  <a name="overview-of-the-full-text-predicates-contains-and-freetext"></a><a name="OV_ft_predicates"></a><span data-ttu-id="9e8a5-106">전체 텍스트 조건자 (CONTAINS 및 FREETEXT) 개요</span><span class="sxs-lookup"><span data-stu-id="9e8a5-106">Overview of the Full-Text Predicates (CONTAINS and FREETEXT)</span></span>  
 <span data-ttu-id="9e8a5-107">CONTAINS 및 FREETEXT 조건자는 TRUE 또는 FALSE 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-107">The CONTAINS and FREETEXT predicates return a TRUE or FALSE value.</span></span> <span data-ttu-id="9e8a5-108">이러한 조건자는 지정된 행이 전체 텍스트 쿼리와 일치하는지 여부를 확인하는 선택 조건을 지정하는 데에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-108">They can be used only to specify selection criteria for determining whether a given row matches the full-text query.</span></span> <span data-ttu-id="9e8a5-109">일치하는 행은 결과 집합에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-109">Matching rows are returned in the result set.</span></span> <span data-ttu-id="9e8a5-110">CONTAINS 및 FREETEXT는 SELECT 문의 WHERE 또는 HAVING 절에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-110">CONTAINS and FREETEXT are specified in the WHERE or HAVING clause of a SELECT statement.</span></span> <span data-ttu-id="9e8a5-111">CONTAINS 및 FREETEXT는 LIKE와 BETWEEN 등의 다른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 조건자와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-111">They can be combined with any of the other [!INCLUDE[tsql](../../includes/tsql-md.md)] predicates, such as LIKE and BETWEEN.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-112">이러한 조건자의 구문 및 인수에 대 한 자세한 내용은 [CONTAINS &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql) 및 [FREETEXT &#40;transact-sql&#41;](/sql/t-sql/queries/freetext-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-112">For information about the syntax and arguments of these predicates, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) and [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).</span></span>  
  
 <span data-ttu-id="9e8a5-113">CONTAINS 또는 FREETEXT를 사용하면 검색할 테이블의 단일 열, 열 목록 또는 모든 열을 지정할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="9e8a5-113">When using CONTAINS or FREETEXT, you can specify either a single column, a list of columns, or all columns in the table to be searched.</span></span> <span data-ttu-id="9e8a5-114">경우에 따라 단어 분리, 형태소 분석, 동의어 사전 조회 및 의미 없는 단어 제거를 위해 지정된 전체 텍스트 쿼리에서 사용할 리소스의 언어를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-114">Optionally, you can specify the language whose resources will be used by given full-text query for word breaking and stemming, thesaurus lookups, and noise-word removal.</span></span>  
  
 <span data-ttu-id="9e8a5-115">CONTAINS 및 FREETEXT는 다음과 같은 다양한 유형의 일치에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-115">CONTAINS and FREETEXT are useful for different kind of matches, as follows:</span></span>  
  
-   <span data-ttu-id="9e8a5-116">CONTAINS(또는 CONTAINSTABLE)를 사용하여 특정 단어나 구와 정확히 일치하거나 비슷하게 일치하는 단어를 검색하거나, 서로 근접한 단어를 검색하거나, 가중치 검색을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-116">Use CONTAINS (or CONTAINSTABLE) for precise or fuzzy (less precise) matches to single words and phrases, the proximity of words within a certain distance of one another, or weighted matches.</span></span> <span data-ttu-id="9e8a5-117">CONTAINS를 사용할 경우 검색할 텍스트를 지정하는 하나 이상의 검색 조건과 일치 여부를 결정하는 조건을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-117">When using CONTAINS, you must specify at least one search condition that specifies the text that you are searching for and the conditions that determine matches.</span></span>  
  
     <span data-ttu-id="9e8a5-118">검색 조건 사이에 논리적 연산을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-118">You can use logical operation between search conditions.</span></span> <span data-ttu-id="9e8a5-119">자세한 내용은이 항목의 뒷부분에 나오는 [부울 연산자 사용-AND, OR, AND NOT (CONTAINS 및 CONTAINSTABLE)](#Using_Boolean_Operators)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-119">For more information, see [Using Boolean operators-AND, OR, AND NOT (in CONTAINS and CONTAINSTABLE)](#Using_Boolean_Operators), later in this topic.</span></span>  
  
-   <span data-ttu-id="9e8a5-120">FREETEXT(또는 FREETEXTTABLE)를 사용하여 지정된 단어, 구 또는 문장( *freetext 문자열*)의 정확한 단어가 아닌 의미를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-120">Use FREETEXT (or FREETEXTTABLE) for matching the meaning, but not the exact wording, of specified words, phrases or sentences (the *freetext string*).</span></span> <span data-ttu-id="9e8a5-121">지정된 열의 모든 용어나 용어 형태가 전체 텍스트 인덱스에 있으면 일치하는 항목이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-121">Matches are generated if any term or form of any term is found in the full-text index of a specified column.</span></span>  
  
 <span data-ttu-id="9e8a5-122">CONTAINS 또는 FREETEXT 조건자에 네 부분으로 된 이름을 사용하여 연결된 서버의 대상 테이블에 대한 전체 텍스트 인덱싱된 열을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-122">You can use a four-part name in the CONTAINS or FREETEXT predicate to query full-text indexed columns of the target tables on a linked server.</span></span> <span data-ttu-id="9e8a5-123">원격 서버에서 전체 텍스트 쿼리를 받도록 준비하려면 원격 서버의 대상 테이블 및 열에 대한 전체 텍스트 인덱스를 만든 다음 원격 서버를 연결된 서버로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-123">To prepare a remote server to receive full-text queries, create a full-text index on the target tables and columns on the remote server and then add the remote server as a linked server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-124">데이터베이스 호환성 수준이 100로 설정 된 경우에는 [OUTPUT 절](/sql/t-sql/queries/output-clause-transact-sql) 에 전체 텍스트 조건자가 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-124">Full-text predicates are not allowed in the [OUTPUT Clause](/sql/t-sql/queries/output-clause-transact-sql) when the database compatibility level is set to 100.</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="9e8a5-125">예</span><span class="sxs-lookup"><span data-stu-id="9e8a5-125">Examples</span></span>  
  
#### <a name="a-using-contains-with-simple_term"></a><span data-ttu-id="9e8a5-126">A.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-126">A.</span></span> <span data-ttu-id="9e8a5-127"><simple_term>에 CONTAINS 사용</span><span class="sxs-lookup"><span data-stu-id="9e8a5-127">Using CONTAINS with <simple_term></span></span>  
 <span data-ttu-id="9e8a5-128">다음 예에서는 가격이 `$80.99` 이고 `"Mountain"`이라는 단어가 포함된 모든 제품을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-128">The following example finds all products with a price of `$80.99` that contain the word `"Mountain"`.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a><span data-ttu-id="9e8a5-129">B.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-129">B.</span></span> <span data-ttu-id="9e8a5-130">FREETEXT를 사용하여 지정된 문자 값을 포함하는 단어 검색</span><span class="sxs-lookup"><span data-stu-id="9e8a5-130">Using FREETEXT to search for words containing specified character values</span></span>  
 <span data-ttu-id="9e8a5-131">다음 예에서는 vital, safety, components와 관련된 단어를 포함하는 문서를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-131">The following example searches for all documents containing the words related to vital, safety, components.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="overview-of-the-full-text-functions-containstable-and-freetexttable"></a><a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a><span data-ttu-id="9e8a5-132">전체 텍스트 함수 개요 (CONTAINSTABLE 및 FREETEXTTABLE)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-132">Overview of the Full-Text Functions (CONTAINSTABLE and FREETEXTTABLE)</span></span>  
 <span data-ttu-id="9e8a5-133">CONTAINSTABLE 및 FREETEXTTABLE 함수는 일반 테이블 이름처럼 SELECT 문의 FROM 절에서 참조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-133">The CONTAINSTABLE and FREETEXTTABLE functions are referenced like a regular table name in the FROM clause of a SELECT statement.</span></span> <span data-ttu-id="9e8a5-134">이러한 함수는 전체 텍스트 쿼리와 일치하는 행이 0개, 1개 또는 그 이상 있는 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-134">They return a table of zero, one, or more rows that match the full-text query.</span></span> <span data-ttu-id="9e8a5-135">반환된 테이블에는 함수의 전체 텍스트 검색 조건에 지정된 선택 조건과 일치하는 기본 테이블의 행만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-135">The returned table contains only rows of the base table that match the selection criteria specified in the full-text search condition of the function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-136">이러한 함수의 구문 및 인수에 대 한 자세한 내용은 [CONTAINSTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-136">For information about the syntax and arguments of these functions, see [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).</span></span>  
  
 <span data-ttu-id="9e8a5-137">이러한 함수 중 하나를 사용하는 쿼리는 다음과 같이 각 행에 대해 적절한 순위 값(RANK) 및 전체 텍스트 키(KEY)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-137">Queries using one of these functions return a relevance ranking value (RANK) and full-text key (KEY) for each row, as follows:</span></span>  
  
-   <span data-ttu-id="9e8a5-138">KEY 열</span><span class="sxs-lookup"><span data-stu-id="9e8a5-138">KEY column</span></span>  
  
     <span data-ttu-id="9e8a5-139">KEY 열은 반환된 행의 고유 값을 반환하며,</span><span class="sxs-lookup"><span data-stu-id="9e8a5-139">The KEY column returns unique values of the returned rows.</span></span> <span data-ttu-id="9e8a5-140">선택 조건을 지정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-140">The KEY column can be used to specify selection criteria.</span></span>  
  
-   <span data-ttu-id="9e8a5-141">RANK 열</span><span class="sxs-lookup"><span data-stu-id="9e8a5-141">RANK column</span></span>  
  
     <span data-ttu-id="9e8a5-142">RANK 열은 각 행이 선택 조건과 일치하는 정도를 나타내는 *순위 값* 을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-142">The RANK column returns a *rank value* for each row that indicates how well the row matched the selection criteria.</span></span> <span data-ttu-id="9e8a5-143">행의 텍스트 또는 문서 순위 값이 높을수록 지정된 전체 텍스트 쿼리에 대한 행의 관련성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-143">The higher the rank value of the text or document in a row, the more relevant the row is for the given full-text query.</span></span> <span data-ttu-id="9e8a5-144">또한 여러 행에 동일한 순위가 지정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-144">Note that different rows can be ranked identically.</span></span> <span data-ttu-id="9e8a5-145">선택적 *top_n_by_rank* 매개 변수를 지정하면 반환될 일치 항목 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-145">You can limit the number of matches to be returned by specifying the optional *top_n_by_rank* parameter.</span></span> <span data-ttu-id="9e8a5-146">자세한 내용은 [RANK를 사용하여 검색 결과 제한](limit-search-results-with-rank.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-146">For more information, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
 <span data-ttu-id="9e8a5-147">이러한 함수 중 하나를 사용할 경우 전체 텍스트를 검색할 기본 테이블을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-147">When using either of these functions, you must specify the base table that is to be full-text searched.</span></span> <span data-ttu-id="9e8a5-148">조건자와 마찬가지로 검색할 테이블의 단일 열, 열 목록 또는 모든 열을 지정할 수 있으며, 경우에 따라 전체 텍스트 쿼리에서 사용할 리소스의 언어를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-148">As with the predicates, you can specify a single column, a list of columns, or all columns in the table to be searched, and optionally, the language whose resources will be used by given full-text query.</span></span>  
  
 <span data-ttu-id="9e8a5-149">CONTAINSTABLE은 CONTAINS와 같은 유형의 일치에 유용하고 FREETEXTTABLE은 FREETEXT와 같은 유형의 일치에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-149">CONTAINSTABLE is useful for the same kinds of matches as CONTAINS, and FREETEXTTABLE is useful for the same kinds of matches as FREETEXT.</span></span> <span data-ttu-id="9e8a5-150">자세한 내용은 이 항목의 앞부분에 나오는 [전체 텍스트 조건자(CONTAINS 및 FREETEXT) 개요](#OV_ft_predicates)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-150">For more information, see [Overview of the Full-Text Predicates (CONTAINS and FREETEXT)](#OV_ft_predicates), earlier in this topic.</span></span> <span data-ttu-id="9e8a5-151">CONTAINSTABLE 및 FREETEXTTABLE 함수를 사용하는 쿼리를 실행할 경우 반환된 행을 원래 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 테이블의 행과 명시적으로 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-151">When running queries that use the CONTAINSTABLE and FREETEXTTABLE functions you must explicitly join rows that are returned with the rows in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base table.</span></span>  
  
 <span data-ttu-id="9e8a5-152">일반적으로 CONTAINSTABLE 또는 FREETEXTTABLE 결과는 기본 테이블과 조인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-152">Typically, the result of CONTAINSTABLE or FREETEXTTABLE needs to be joined with the base table.</span></span> <span data-ttu-id="9e8a5-153">이러한 경우 고유 키 열 이름을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-153">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="9e8a5-154">모든 전체 텍스트 사용 테이블에서 발생 하는이 열은 테이블에 고유 행을 적용 하는 데 사용 됩니다 ( *고유 \* \* 키 열*).</span><span class="sxs-lookup"><span data-stu-id="9e8a5-154">This column, which occurs in every full-text enabled table, is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="9e8a5-155">자세한 내용은 [전체 텍스트 인덱스 관리](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-155">For more information, see [Manage Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="9e8a5-156">예</span><span class="sxs-lookup"><span data-stu-id="9e8a5-156">Examples</span></span>  
  
#### <a name="a-using-containstable"></a><span data-ttu-id="9e8a5-157">A.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-157">A.</span></span> <span data-ttu-id="9e8a5-158">CONTAINSTABLE 사용</span><span class="sxs-lookup"><span data-stu-id="9e8a5-158">Using CONTAINSTABLE</span></span>  
 <span data-ttu-id="9e8a5-159">다음 예에서는 **Description** 열에서 "light" 또는 "lightweight"라는 단어 근처에 "aluminum"이라는 단어가 포함된 모든 제품의 설명 ID와 설명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-159">The following example returns the description ID and description of all products for which the **Description** column contain the word "aluminum" near either the word "light" or the word "lightweight."</span></span> <span data-ttu-id="9e8a5-160">등급 값이 2 이상인 행만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-160">Only rows with a rank value of 2 or higher are returned.</span></span>  
  
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
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a><span data-ttu-id="9e8a5-161">B.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-161">B.</span></span> <span data-ttu-id="9e8a5-162">FREETEXTTABLE 사용</span><span class="sxs-lookup"><span data-stu-id="9e8a5-162">Using FREETEXTTABLE</span></span>  
 <span data-ttu-id="9e8a5-163">다음 예에서는 순위가 높은 행을 먼저 반환하고 SELECT 목록에 각 행의 순위를 추가하도록 FREETEXTTABLE 쿼리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-163">The following example extends a FREETEXTTABLE query to return the highest ranked rows first and to add the ranking of each row to the select list.</span></span> <span data-ttu-id="9e8a5-164">쿼리를 지정 하려면 **productdescriptionid 임을** 가 테이블의 고유 키 열 이라는 것을 알아야 합니다 `ProductDescription` .</span><span class="sxs-lookup"><span data-stu-id="9e8a5-164">To specify the query, you must know that **ProductDescriptionID** is the unique key column for the `ProductDescription` table.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="9e8a5-165">다음은 순위 값이 10 이상인 행만 반환하도록 동일한 쿼리를 확장한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-165">Here is an extension of the same query that only returns rows with a rank value of 10 or greater:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="using-boolean-operators---and-or-and-not---in-contains-and-containstable"></a><a name="Using_Boolean_Operators"></a><span data-ttu-id="9e8a5-166">부울 연산자 (AND, OR 및 NOT in CONTAINS 및 CONTAINSTABLE) 사용</span><span class="sxs-lookup"><span data-stu-id="9e8a5-166">Using Boolean operators - AND, OR, and NOT - in CONTAINS and CONTAINSTABLE</span></span>  
 <span data-ttu-id="9e8a5-167">CONTAINS 조건자와 CONTAINSTABLE 함수는 동일한 검색 조건을 사용하며,</span><span class="sxs-lookup"><span data-stu-id="9e8a5-167">The CONTAINS predicate and CONTAINSTABLE function use the same search conditions.</span></span> <span data-ttu-id="9e8a5-168">둘 다 부울 연산자 (AND, OR 및 NOT)를 사용 하 여 여러 검색 단어를 결합 하 여 논리적 연산을 수행할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-168">Both support combining several search terms by using Boolean operators-AND, OR, AND NOT-to perform logical operations.</span></span> <span data-ttu-id="9e8a5-169">예를 들어 AND를 사용하여 "latte"와 "New York-style bagel"이 둘 다 포함된 행을 찾거나</span><span class="sxs-lookup"><span data-stu-id="9e8a5-169">You could use AND, for example, to find rows that contain both "latte" and "New York-style bagel".</span></span> <span data-ttu-id="9e8a5-170">AND NOT을 사용하여 "bagel"은 포함되지만 "cream cheese"는 포함되지 않은 행을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-170">You can use AND NOT, for example, to find the rows that contain "bagel" but do not contain "cream cheese".</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-171">반면에 FREETEXT 및 FREETEXTTABLE은 부울 단어를 검색할 단어로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-171">In contrast, FREETEXT and FREETEXTTABLE treat the Boolean terms as words to be searched.</span></span>  
  
 <span data-ttu-id="9e8a5-172">CONTAINS를 논리 연산자 AND, OR 및 NOT을 사용하는 다른 조건자와 결합하는 방법은 [검색 조건&#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-172">For information about combining CONTAINS with other predicates that use the logical operators AND, OR, and NOT, see [Search Condition &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e8a5-173">예제</span><span class="sxs-lookup"><span data-stu-id="9e8a5-173">Example</span></span>  
 <span data-ttu-id="9e8a5-174">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스의 ProductDescription 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-174">The following example uses the ProductDescription table of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="9e8a5-175">이 쿼리는 CONTAINS 조건자를 사용하여 설명 ID가 5와 같지 않고 "Aluminum"이라는 단어와 "spindle"이라는 단어가 모두 포함된 설명을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-175">The query uses the CONTAINS predicate to search for descriptions in which the description ID is not equal to 5 and the description contains both the word "Aluminum" and the word "spindle."</span></span> <span data-ttu-id="9e8a5-176">검색 조건에는 AND 부울 연산자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-176">The search condition uses the AND Boolean operator.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="additional-considerations-for-full-text-queries"></a><a name="Additional_Considerations"></a><span data-ttu-id="9e8a5-177">전체 텍스트 쿼리에 대 한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="9e8a5-177">Additional Considerations for Full-Text Queries</span></span>  
 <span data-ttu-id="9e8a5-178">전체 텍스트 쿼리를 작성할 때 다음 사항도 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-178">When writing full-text queries also consider the following:</span></span>  
  
-   <span data-ttu-id="9e8a5-179">LANGUAGE 옵션</span><span class="sxs-lookup"><span data-stu-id="9e8a5-179">The LANGUAGE option</span></span>  
  
     <span data-ttu-id="9e8a5-180">많은 쿼리 용어는 단어 분리기 동작에 크게 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-180">Many query terms depend heavily on word-breaker behavior.</span></span> <span data-ttu-id="9e8a5-181">올바른 단어 분리기(및 형태소 분석기)를 사용하고 있는지 확인하려면 LANGUAGE 옵션을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-181">To ensure that you are using the correct word breaker (and stemmer) and thesaurus file, we recommend that you specify the LANGUAGE option.</span></span> <span data-ttu-id="9e8a5-182">자세한 내용은 [전체 텍스트 인덱스 생성 시 언어 선택](choose-a-language-when-creating-a-full-text-index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-182">For more information, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
-   <span data-ttu-id="9e8a5-183">중지 단어</span><span class="sxs-lookup"><span data-stu-id="9e8a5-183">Stopwords</span></span>  
  
     <span data-ttu-id="9e8a5-184">전체 텍스트 쿼리를 정의할 때 전체 텍스트 엔진은 검색 조건에서 중지 단어(의미 없는 단어라고도 함)를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-184">When defining a full-text query, the Full-Text Engine discards stopwords (also called noise words) from the search criteria.</span></span> <span data-ttu-id="9e8a5-185">중지 단어란 "a", "and", "is", "the" 등과 같이 자주 사용되지만 일반적으로 특정 텍스트 검색에는 도움이 되지 않는 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-185">Stopwords are words such as "a," "and," "is," or "the," that can occur frequently but that typically do not help when searching for particular text.</span></span> <span data-ttu-id="9e8a5-186">중지 단어는 중지 목록에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-186">Stopwords are listed in a stoplist.</span></span> <span data-ttu-id="9e8a5-187">인덱싱할 때 쿼리 또는 인덱스에서 생략된 중지 단어를 확인할 수 있도록 각 전체 텍스트 인덱스는 특정 중지 목록과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-187">Each full-text index is associated with a specific stoplist, which determines what stopwords are omitted from the query or the index at indexing time.</span></span> <span data-ttu-id="9e8a5-188">자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-188">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](full-text-search.md).</span></span>  
  
-   <span data-ttu-id="9e8a5-189">동의어 사전</span><span class="sxs-lookup"><span data-stu-id="9e8a5-189">The thesaurus</span></span>  
  
     <span data-ttu-id="9e8a5-190">FREETEXT 및 FREETEXTTABLE 쿼리에는 기본적으로 동의어 사전이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-190">FREETEXT and FREETEXTTABLE queries use the thesaurus by default.</span></span> <span data-ttu-id="9e8a5-191">CONTAINS 및 CONTAINSTABLE은 선택적 THESAURUS 인수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-191">CONTAINS and CONTAINSTABLE support an optional THESAURUS argument.</span></span>  
  
-   <span data-ttu-id="9e8a5-192">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="9e8a5-192">Case sensitivity</span></span>  
  
     <span data-ttu-id="9e8a5-193">전체 텍스트 검색 쿼리는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-193">Full-text search queries are case-insensitive.</span></span> <span data-ttu-id="9e8a5-194">그러나 일본어에는 철자 표준화 개념이 대/소문자를 구분하지 않는 것과 비슷한 여러 가지 음성 철자법이 있습니다(예: 가나를 구분하지 않음).</span><span class="sxs-lookup"><span data-stu-id="9e8a5-194">However, in Japanese, there are multiple phonetic orthographies in which the concept of orthographic normalization is akin to case insensitivity (for example, kana = insensitivity).</span></span> <span data-ttu-id="9e8a5-195">이러한 철자 표준화는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-195">This type of orthographic normalization is not supported.</span></span>  
  

  
##  <a name="querying-varbinarymax-and-xml-columns"></a><a name="varbinary"></a><span data-ttu-id="9e8a5-196">Varbinary (max) 및 xml 열 쿼리</span><span class="sxs-lookup"><span data-stu-id="9e8a5-196">Querying varbinary(max) and xml Columns</span></span>  
 <span data-ttu-id="9e8a5-197">`varbinary(max)`, `varbinary` 또는 `xml` 열이 전체 텍스트 인덱싱된 경우 다른 전체 텍스트 인덱싱된 열과 마찬가지로 전체 텍스트 조건자(CONTAINS 및 FREETEXT) 및 함수(CONTAINSTABLE 및 FREETEXTTABLE)를 사용하여 이러한 열을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-197">If a `varbinary(max)`, `varbinary`, or `xml` column is full-text indexed, it can be queried using the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE), like any other full-text indexed column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9e8a5-198">전체 텍스트 검색은 이미지 열에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-198">Full-text search also works with image columns.</span></span> <span data-ttu-id="9e8a5-199">그러나 `image` 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이후 버전에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-199">However, the `image` data type will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e8a5-200">새 개발 작업에서는 이 데이터 형식을 사용하지 않도록 하고 현재 이 데이터 형식을 사용하는 애플리케이션은 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-200">Avoid using this data type in new development work, and plan to modify applications that currently use it.</span></span> <span data-ttu-id="9e8a5-201">대신 `varbinary(max)` 데이터 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-201">Use the `varbinary(max)` data type instead.</span></span>  
  
### <a name="varbinarymax-or-varbinary-data"></a><span data-ttu-id="9e8a5-202">varbinary(max) 또는 varbinary 데이터</span><span class="sxs-lookup"><span data-stu-id="9e8a5-202">varbinary(max) or varbinary data</span></span>  
 <span data-ttu-id="9e8a5-203">단일 `varbinary(max)` 또는 `varbinary` 열에 많은 문서 유형을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-203">A single `varbinary(max)` or `varbinary` column can store many types of documents.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9e8a5-204">에서는 필터가 설치되어 있고 운영 체제에서 사용할 수 있는 문서 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-204">supports any document type for which a filter is installed and available in the operative system.</span></span> <span data-ttu-id="9e8a5-205">각 문서의 문서 유형은 문서의 파일 확장명으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-205">The document type of each document is identified by the file extension of the document.</span></span> <span data-ttu-id="9e8a5-206">예를 들어 .doc 파일 확장명의 경우 전체 텍스트 검색은 Microsoft Word 문서를 지원하는 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-206">For example, for a .doc file extension, full-text search uses the filter that supports Microsoft Word documents.</span></span> <span data-ttu-id="9e8a5-207">사용 가능한 문서 유형의 목록을 보려면 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 카탈로그 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-207">For a list of available document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="9e8a5-208">전체 텍스트 엔진은 운영 체제에 설치된 기존 필터를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-208">Note that the Full-Text Engine can leverage existing filters that are installed in the operating system.</span></span> <span data-ttu-id="9e8a5-209">운영 체제 필터, 단어 분리기, 형태소 분석기를 사용하려면 먼저 다음과 같이 서버 인스턴스에 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-209">Before you can use operating-system filters, word breakers, and stemmers, you must load them in the server instance, as follows:</span></span>  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 <span data-ttu-id="9e8a5-210">`varbinary(max)` 열에 대한 전체 텍스트 인덱스를 만들려면 전체 텍스트 엔진이 `varbinary(max)` 열에 있는 문서의 파일 확장명에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-210">To create a full-text index on a `varbinary(max)` column, the Full-Text Engine needs access to the file extensions of the documents in the `varbinary(max)` column.</span></span> <span data-ttu-id="9e8a5-211">이 정보는 전체 텍스트 인덱스의 `varbinary(max)` 열에 연결해야 하는 테이블 열, 즉 유형 열에 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-211">This information must be stored in a table column, called a type column, that must be associated with the `varbinary(max)` column in the full-text index.</span></span> <span data-ttu-id="9e8a5-212">문서를 인덱싱할 때 전체 텍스트 엔진은 유형 열의 파일 확장명을 사용하여 사용할 필터를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-212">When indexing a document, the Full-Text Engine uses the file extension in the type column to identify which filter to use.</span></span>  
  
 
  
### <a name="xml-data"></a><span data-ttu-id="9e8a5-213">xml 데이터</span><span class="sxs-lookup"><span data-stu-id="9e8a5-213">xml data</span></span>  
 <span data-ttu-id="9e8a5-214">`xml` 데이터 형식 열에는 XML 문서만 저장되고 이러한 문서에는 XML 필터만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-214">An `xml` data type column stores only XML documents and fragments, and only the XML filter is used for the documents.</span></span> <span data-ttu-id="9e8a5-215">따라서 유형 열은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-215">Therefore, a type column is unnecessary.</span></span> <span data-ttu-id="9e8a5-216">`xml` 열에서 전체 텍스트 인덱스는 XML 요소의 내용은 인덱싱하지만 XML 태그는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-216">On `xml` columns, the full-text index indexes the content of the XML elements, but ignores the XML markup.</span></span> <span data-ttu-id="9e8a5-217">특성 값은 숫자 값이 아니면 전체 텍스트 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-217">Attribute values are full-text indexed unless they are numeric values.</span></span> <span data-ttu-id="9e8a5-218">요소 태그는 토큰 경계로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-218">Element tags are used as token boundaries.</span></span> <span data-ttu-id="9e8a5-219">여러 언어를 포함하는 올바른 형식의 XML 또는 HTML 문서와 조각이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-219">Well-formed XML or HTML documents and fragments containing multiple languages are supported.</span></span>  
  
 <span data-ttu-id="9e8a5-220">열을 쿼리 하는 방법에 대 한 자세한 내용은 `xml` [XML 열에 전체 텍스트 검색 사용](../xml/use-full-text-search-with-xml-columns.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-220">For more information about querying on an `xml` column, see [Use Full-Text Search with XML Columns](../xml/use-full-text-search-with-xml-columns.md).</span></span>  
  
 
  
##  <a name="supported-forms-of-query-terms"></a><a name="supported"></a><span data-ttu-id="9e8a5-221">지원 되는 쿼리 용어 형태</span><span class="sxs-lookup"><span data-stu-id="9e8a5-221">Supported Forms of Query Terms</span></span>  
 <span data-ttu-id="9e8a5-222">이 섹션에서는 전체 텍스트 조건자 및 행 집합 반환 함수에서 각 쿼리 형태에 제공하는 지원에 대해 간략히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-222">This section summarizes the support provided for each form of query by the full-text predicates and rowset-valued functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-223"> 쿼리 용어의 구문을 보려면 다음 표의 **지원 요소** 열에서 해당 링크를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-223">For the syntax a given query term, click the corresponding links in **Supported by** column of the following table.</span></span>  
  
|<span data-ttu-id="9e8a5-224">쿼리 용어 형태</span><span class="sxs-lookup"><span data-stu-id="9e8a5-224">Query-term form</span></span>|<span data-ttu-id="9e8a5-225">Description</span><span class="sxs-lookup"><span data-stu-id="9e8a5-225">Description</span></span>|<span data-ttu-id="9e8a5-226">지원 요소</span><span class="sxs-lookup"><span data-stu-id="9e8a5-226">Supported by</span></span>|  
|----------------------|-----------------|------------------|  
|<span data-ttu-id="9e8a5-227">하나 이상의 특정 단어 또는 구(*단순 단어*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-227">One or more specific words or phrases (*simple term*)</span></span>|<span data-ttu-id="9e8a5-228">전체 텍스트 검색에서 단어(또는 *토큰*)는 지정된 언어의 언어 규칙에 따라 적절한 단어 분리기에 의해 경계가 식별되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-228">In full-text search, a word (or *token*) is a string whose boundaries are identified by appropriate word breakers, following the linguistic rules of the specified language.</span></span> <span data-ttu-id="9e8a5-229">올바른 구는 여러 단어로 구성됩니다. 문장 부호는 있을 수도 있고 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-229">A valid phrase consists of multiple words, with or without any punctuation marks between them.</span></span><br /><br /> <span data-ttu-id="9e8a5-230">예를 들어 "크 라 상"는 단어이 고 "caf?"는</span><span class="sxs-lookup"><span data-stu-id="9e8a5-230">For example, "croissant" is a word, and "caf??</span></span> <span data-ttu-id="9e8a5-231">au lait "는 구입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-231">au lait" is a phrase.</span></span> <span data-ttu-id="9e8a5-232">이와 같은 단어 및 구를 단순 단어라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-232">Words and phrases such as these are called simple terms.</span></span><br /><br /> <span data-ttu-id="9e8a5-233">자세한 내용은 이 항목 뒷부분의 [특정 단어 또는 구(단순 단어) 검색](#Simple_Term)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-233">For more information, see [Searching for Specific word or Phrase (Simple Term)](#Simple_Term), later in this topic.</span></span>|<span data-ttu-id="9e8a5-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 은 정확히 일치하는 구를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) look for an exact match for the phrase.</span></span><br /><br /> <span data-ttu-id="9e8a5-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 은 구를 여러 개의 단어로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) break up the phrase into separate words.</span></span>|  
|<span data-ttu-id="9e8a5-236">특정 텍스트로 시작하는 단어 또는 그러한 단어를 포함하는 구(*접두사 단어*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-236">A word or a phrase where the words begin with specified text (*prefix term*)</span></span>|<span data-ttu-id="9e8a5-237">접두사 단어는 파생어를 만들거나 굴절형을 만들기 위해 단어 앞에 추가되는 문자열을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-237">A prefix term refers to a string that is affixed to the front of a word to produce a derivative word or an inflected form.</span></span><br /><br /> <span data-ttu-id="9e8a5-238">단일 접두사 단어의 경우 지정된 단어로 시작하는 모든 단어가 결과 집합의 일부로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-238">For a single prefix term, any word starting with the specified term will be part of the result set.</span></span> <span data-ttu-id="9e8a5-239">예를 들어 "auto\*" 단어를 사용하면 "automatic", "automobile" 등이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-239">For example, the term "auto\*" matches "automatic", "automobile", and so forth.</span></span><br /><br /> <span data-ttu-id="9e8a5-240">구의 경우 구에 포함된 각 단어가 접두사 단어로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-240">For a phrase, each word within the phrase is considered to be a prefix term.</span></span> <span data-ttu-id="9e8a5-241">예를 들어 "auto tran\*"은 "automatic transmission" 및 "automobile transducer"와 일치하지만 "automatic motor transmission"과는 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-241">For example, the term "auto tran\*" matches "automatic transmission" and "automobile transducer", but it does not match "automatic motor transmission".</span></span><br /><br /> <span data-ttu-id="9e8a5-242">자세한 내용은 이 항목 뒷부분의 [접두사(접두사 단어) 검색](#Prefix_Term)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-242">For more information, see [Performing Prefix Searches (Prefix Term)](#Prefix_Term), later in this topic.</span></span>|<span data-ttu-id="9e8a5-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="9e8a5-244">특정 단어의 굴절 형 (*생성 단어-굴절 형*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-244">Inflectional forms of a specific word (*generation term-inflectional*)</span></span>|<span data-ttu-id="9e8a5-245">굴절형은 동사의 여러 시제 및 변화와 명사의 단수형 및 복수형을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-245">The inflectional forms are the different tenses and conjugations of a verb or the singular and plural forms of a noun.</span></span> <span data-ttu-id="9e8a5-246">예를 들어 "drive"라는 단어의 굴절형을 검색한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-246">For example, search for the inflectional form of the word "drive".</span></span> <span data-ttu-id="9e8a5-247">테이블의 여러 행에 "drive", "drives", "drove", "driving", "driven" 등의 단어가 포함되어 있는 경우 이러한 각 단어는 drive라는 단어를 활용하여 생성된 것이므로 모두 결과 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-247">If various rows in the table include the words "drive", "drives", "drove", "driving", and "driven", all would be in the result set because each of these can be inflectionally generated from the word drive.</span></span><br /><br /> <span data-ttu-id="9e8a5-248">자세한 내용은 이 항목 뒷부분의 [특정 단어의 굴절형(생성 단어) 검색](#Inflectional_Generation_Term)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-248">For more information, see [Searching for the Inflectional Form of a Specific Word (Generation Term)](#Inflectional_Generation_Term), later in this topic.</span></span>|<span data-ttu-id="9e8a5-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 은 기본적으로 지정된 모든 단어의 굴절형을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) look for inflectional terms of all specified words by default.</span></span><br /><br /> <span data-ttu-id="9e8a5-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 은 선택적 INFLECTIONAL 인수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional INFLECTIONAL argument.</span></span>|  
|<span data-ttu-id="9e8a5-251">특정 단어의 동의어 형태 (*생성 단어-동의어 사전*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-251">Synonymous forms of a specific word (*generation term-thesaurus*)</span></span>|<span data-ttu-id="9e8a5-252">동의어 사전은 단어에 대한 사용자 지정 동의어를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-252">A thesaurus defines user-specified synonyms for terms.</span></span> <span data-ttu-id="9e8a5-253">예를 들어 동의어 사전에 "{car, automobile, truck, van}" 항목을 추가하면 "car"라는 단어의 동의어 형태를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-253">For example, if an entry, "{car, automobile, truck, van}", is added to a thesaurus, you can search for the thesaurus form of the word "car".</span></span> <span data-ttu-id="9e8a5-254">"automobile", "truck", "van" 또는 "car"라는 단어는 각각 "car"라는 단어를 포함하는 동의어 확장 집합에 속하므로 이러한 단어를 포함하는 쿼리된 테이블의 모든 행이 결과 집합에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-254">All rows in the table queried that include the words "automobile", "truck", "van", or "car", appear in the result set because each of these words belong to the synonym expansion set containing the word "car".</span></span><br /><br /> <span data-ttu-id="9e8a5-255">동의어 사전 파일의 구조에 대한 자세한 내용은 [전체 텍스트 검색에 사용할 동의어 사전 파일 구성 및 관리](configure-and-manage-thesaurus-files-for-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-255">For information about the structure of thesaurus files, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>|<span data-ttu-id="9e8a5-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 는 기본적으로 동의어 사전을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) use the thesaurus by default.</span></span><br /><br /> <span data-ttu-id="9e8a5-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 는 선택적 동의어 사전 인수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional THESAURUS argument.</span></span>|  
|<span data-ttu-id="9e8a5-258">다른 단어나 구와 근접한 단어나 구(*근접 단어*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-258">A word or phrase close to another word or phrase (*proximity term*)</span></span>|<span data-ttu-id="9e8a5-259">근접 단어는 서로 근접하는 단어나 구를 나타냅니다. 첫 번째 검색 단어와 마지막 검색 단어를 구분하는 검색 대상이 아닌 단어의 최대 개수를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-259">A proximity term indicates words or phrases that are near to each other., You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="9e8a5-260">또한 임의의 순서나 지정한 순서로 단어 또는 구를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-260">In addition, you can search for words or phrases in any order, or in the order in which you specify them.</span></span><br /><br /> <span data-ttu-id="9e8a5-261">예를 들어 "ice"라는 단어가 "hockey"라는 단어와 근접해 있거나 "ice skating"이라는 구가 "ice hockey"라는 구와 근접해 있는 행을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-261">For example, you want to find the rows in which the word "ice" is near the word "hockey" or in which the phrase "ice skating" is near the phrase "ice hockey".</span></span><br /><br /> <span data-ttu-id="9e8a5-262">자세한 내용은 [NEAR를 사용하여 근접 단어 검색](search-for-words-close-to-another-word-with-near.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-262">For more information, see [Search for Words Close to Another Word with NEAR](search-for-words-close-to-another-word-with-near.md).</span></span>|<span data-ttu-id="9e8a5-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="9e8a5-264">가중치를 사용하는 단어나 구(*가중치 단어*)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-264">Words or phrases using weighted values (*weighted term*)</span></span>|<span data-ttu-id="9e8a5-265">단어와 구 집합에서 각 단어와 구의 중요도를 나타내는 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-265">A weighting value that indicates the degree of importance for each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="9e8a5-266">가중치는 0.0이 가장 낮고 1.0이 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-266">A weight value of 0.0 is the lowest, and a weight value of 1.0 is the highest.</span></span><br /><br /> <span data-ttu-id="9e8a5-267">예를 들어 여러 단어를 검색하는 쿼리에서 각 검색 단어에 검색 조건에 있는 다른 단어에 대한 상대적 중요도를 나타내는 가중치를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-267">For example, in a query searching for multiple terms, you can assign each search word a weight value indicating its importance relative to the other words in the search condition.</span></span> <span data-ttu-id="9e8a5-268">이러한 쿼리 유형의 결과에서는 검색 단어에 지정한 상대적 가중치에 따라 관련성이 가장 높은 행이 먼저 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-268">The results for this type of query return the most relevant rows first, according to the relative weight you have assigned to search words.</span></span> <span data-ttu-id="9e8a5-269">결과 집합에는 지정된 단어(또는 단어 사이의 내용) 중 적어도 하나를 포함하는 문서 또는 행이 반환되지만 일부 결과는 검색된 여러 개의 단어와 관련된 가중치의 차이 때문에 다른 결과보다 관련이 높은 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-269">The result sets contain documents or rows containing any of the specified terms (or content between them); however, some results will be considered more relevant than others because of the variation in the weighted values associated with different searched terms.</span></span><br /><br /> <span data-ttu-id="9e8a5-270">자세한 내용은 이 항목 뒷부분의 [가중치를 사용하는 단어 또는 구(가중치 단어) 검색](#Weighted_Term)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-270">For more information, see [Searching for Words or Phrases Using Weighted Values (Weighted Term)](#Weighted_Term), later in this topic.</span></span>|[<span data-ttu-id="9e8a5-271">CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="9e8a5-271">CONTAINSTABLE</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="searching-for-specific-word-or-phrase-simple-term"></a><a name="Simple_Term"></a><span data-ttu-id="9e8a5-272">특정 단어 또는 구 (단순 단어) 검색</span><span class="sxs-lookup"><span data-stu-id="9e8a5-272">Searching for Specific Word or Phrase (Simple Term)</span></span>  
 <span data-ttu-id="9e8a5-273">[CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)또는 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 을 사용하여 테이블에서 특정 구를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-273">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search a table for a specific phrase.</span></span> <span data-ttu-id="9e8a5-274">예를 들어 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스의 `ProductReview` 테이블을 검색하여 "learning curve"라는 구가 포함된 제품 설명을 모두 찾으려면 CONTAINS 조건자를 다음과 같이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-274">For example, if you want to search the `ProductReview` table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to find all comments about a product with the phrase "learning curve", you could use the CONTAINS predicate as follows:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 <span data-ttu-id="9e8a5-275">검색 조건(이 경우 "learning curve")은 매우 복잡할 수 있으며 하나 이상의 단어로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-275">The search condition, in this case "learning curve", can be quite complex and can be composed of one or more terms</span></span>  
  
 
  
###  <a name="performing-prefix-searches-prefix-term"></a><a name="Prefix_Term"></a><span data-ttu-id="9e8a5-276">접두사 검색 수행 (접두사 단어)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-276">Performing Prefix Searches (Prefix Term)</span></span>  
 <span data-ttu-id="9e8a5-277">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 또는 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 을 사용하여 지정된 접두사가 포함된 단어나 구를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-277">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql) or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases with a specified prefix.</span></span> <span data-ttu-id="9e8a5-278">열에서 지정된 접두사로 시작하는 텍스트가 포함된 모든 항목이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-278">All entries in the column that contain text beginning with the specified prefix are returned.</span></span> <span data-ttu-id="9e8a5-279">예를 들어 `top`, `top``ple`및 `top``ping`에서와 같이 `top`- 접두사가 포함된 모든 행을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="9e8a5-279">For example, to search for all rows that contain the prefix `top`-, as in `top``ple`, `top``ping`, and `top`.</span></span> <span data-ttu-id="9e8a5-280">쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-280">The query looks like this:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 <span data-ttu-id="9e8a5-281">별표(\*) 앞에 지정된 텍스트와 일치하는 모든 텍스트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-281">All text that matches the text specified before the asterisk (\*) is returned.</span></span> <span data-ttu-id="9e8a5-282">`CONTAINS (DESCRIPTION, 'top*')`에서와 같이 텍스트와 별표가 큰따옴표로 구분되지 않은 경우 전체 텍스트 검색은 별표를 와일드카드로 간주하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-282">If the text and asterisk are not delimited by double quotation marks, as in `CONTAINS (DESCRIPTION, 'top*')`, full-text search does not consider the asterisk to be a wildcard..</span></span>  
  
 <span data-ttu-id="9e8a5-283">접두사 단어가 구일 경우 구에 포함된 각 토큰이 별도의 접두사 단어로 간주되므로</span><span class="sxs-lookup"><span data-stu-id="9e8a5-283">When the prefix term is a phrase, each token making up the phrase is considered a separate prefix term.</span></span> <span data-ttu-id="9e8a5-284">접두사 단어로 시작하는 단어가 포함된 모든 행이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-284">All rows that have words beginning with the prefix terms will be returned.</span></span> <span data-ttu-id="9e8a5-285">예를 들어 접두사 단어가 "light bread\*"이면 "light breaded", "lightly breaded", "light bread" 등의 텍스트가 포함된 행이 검색되지만 "lightly toasted bread"는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-285">For example, the prefix term "light bread\*" will find rows with text of "light breaded," "lightly breaded," or "light bread," but it will not return "lightly toasted bread".</span></span>  
  
 
  
###  <a name="searching-for-inflectional-forms-of-a-specific-word-generation-term"></a><a name="Inflectional_Generation_Term"></a><span data-ttu-id="9e8a5-286">특정 단어의 굴절 형 (생성 단어) 검색</span><span class="sxs-lookup"><span data-stu-id="9e8a5-286">Searching for Inflectional Forms of a Specific Word (Generation Term)</span></span>  
 <span data-ttu-id="9e8a5-287">[CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)또는 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 을 사용하여 동사의 여러 시제나 변화 또는 명사의 단수형과 복수형을 모두 검색(굴절형 검색)하거나, 특정 단어의 동의어 형태를 모두 검색(동의어 검색)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-287">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search for all the different tenses and conjugations of a verb or both the singular and plural forms of a noun (an inflectional search) or for synonymous forms of a specific word (a thesaurus search).</span></span>  
  
 <span data-ttu-id="9e8a5-288">다음 예에서는 `Comments` 데이터베이스의 `ProductReview` 테이블에 있는 `AdventureWorks` 열에서 "foot"의 모든 형태("foot", "feet" 등)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-288">The following example searches for any form of "foot" ("foot", "feet", and so on) in the `Comments` column of the `ProductReview` table in the `AdventureWorks` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9e8a5-289">전체 텍스트 검색에서는 동사의 다양한 시제와 변화 또는 명사의 단수형과 복수형을 모두 검색할 수 있는 형태소 분석기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-289">Full-text search uses stemmers, which allow you to search for the different tenses and conjugations of a verb, or both the singular and plural forms of a noun.</span></span> <span data-ttu-id="9e8a5-290">형태소 분석기에 대한 자세한 내용은 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](configure-and-manage-word-breakers-and-stemmers-for-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-290">For more information about stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  

  
###  <a name="searching-for-words-or-phrases-using-weighted-values-weighted-term"></a><a name="Weighted_Term"></a><span data-ttu-id="9e8a5-291">가중치가 적용 되는 값을 사용 하 여 단어 또는 구 검색 (가중치 단어)</span><span class="sxs-lookup"><span data-stu-id="9e8a5-291">Searching for Words or Phrases Using Weighted Values (Weighted Term)</span></span>  
 <span data-ttu-id="9e8a5-292">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 을 사용하여 단어나 구를 검색하고 가중치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-292">You can use [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases and specify a weighting value.</span></span> <span data-ttu-id="9e8a5-293">가중치는 0.0에서 1.0 사이의 숫자로 측정되며 단어와 구 집합에서 각 단어와 구의 중요도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-293">Weight, measured as a number from 0.0 through 1.0, indicates the importance of each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="9e8a5-294">가중치 0.0이 가장 낮고 1.0이 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-294">A weight of 0.0 is the lowest, and a weight of 1.0 is the highest.</span></span>  
  
 <span data-ttu-id="9e8a5-295">다음 예에서는 가중치를 사용하여 문자열 "Bay"로 시작하는 텍스트에 "Street" 또는 "View"가 있는 모든 고객 주소를 검색하는 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-295">The following example shows a query that searches for all customer addresses, using weights, in which any text beginning with the string "Bay" has either "Street" or "View".</span></span> <span data-ttu-id="9e8a5-296">지정한 단어가 많이 포함된 행일수록 높은 가중치가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-296">The results give a higher rank to those rows that contain more of the words specified.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="9e8a5-297">가중치 단어는 단순 단어, 접두사 단어, 생성 단어 또는 근접 단어와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-297">A weighted term can be used in conjunction with any simple term, prefix term, generation term, or proximity term.</span></span>  
  

  
##  <a name="viewing-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a><a name="tokens"></a><span data-ttu-id="9e8a5-298">단어 분리기, 동의어 사전 및 중지 목록 조합의 토큰화 결과 보기</span><span class="sxs-lookup"><span data-stu-id="9e8a5-298">Viewing the Tokenization Result of a Word Breaker, Thesaurus, and Stoplist Combination</span></span>  
 <span data-ttu-id="9e8a5-299">쿼리 문자열 입력에 특정 단어 분리기, 동의어 사전 및 중지 목록 조합을 적용하면 **sys.dm_fts_parser** 동적 관리 뷰를 사용하여 토큰화 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-299">After applying a given word breaker, thesaurus, and stoplist combination to a query string input, you can view the tokenization result by using the **sys.dm_fts_parser** dynamic management view.</span></span> <span data-ttu-id="9e8a5-300">자세한 내용은 [sys.dm_fts_parser&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e8a5-300">For more information, see [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="9e8a5-301">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e8a5-301">See Also</span></span>  
 <span data-ttu-id="9e8a5-302">[CONTAINS&#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e8a5-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="9e8a5-303">[CONTAINSTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e8a5-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="9e8a5-304">[FREETEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e8a5-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="9e8a5-305">[FREETEXTTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e8a5-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 <span data-ttu-id="9e8a5-306">[전체 텍스트 검색 쿼리 만들기&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9e8a5-306">[Create Full-Text Search Queries &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9e8a5-307">전체 텍스트 쿼리 성능 향상</span><span class="sxs-lookup"><span data-stu-id="9e8a5-307">Improve the Performance of Full-Text Queries</span></span>](improve-the-performance-of-full-text-queries.md)  
  
  
