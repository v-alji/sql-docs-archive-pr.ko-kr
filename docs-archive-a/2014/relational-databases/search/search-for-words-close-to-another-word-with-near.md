---
title: NEAR를 사용하여 근접 단어 검색 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- word searches [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- proximity searches [full-text search]
- full-text search [SQL Server], proximity searches
- full-text queries [SQL Server], proximity
- queries [full-text search], proximity
ms.assetid: 87520646-4865-49ae-8790-f766b80a41f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c2d187ea3ed951ac6f17eb4babc5f4f77451d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735188"
---
# <a name="search-for-words-close-to-another-word-with-near"></a><span data-ttu-id="ac173-102">NEAR를 사용하여 근접 단어 검색</span><span class="sxs-lookup"><span data-stu-id="ac173-102">Search for Words Close to Another Word with NEAR</span></span>
  <span data-ttu-id="ac173-103">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 조건자 또는 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 함수에서 근접 단어(NEAR)를 사용하여 단어나 구를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-103">You can use a proximity term (NEAR) in a [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) function to search for words or phrases near one another.</span></span> <span data-ttu-id="ac173-104">첫 번째 검색 단어와 마지막 검색 단어를 분리하는 검색 대상이 아닌 단어의 최대 수를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-104">You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="ac173-105">또한 단어나 구를 순서에 관계 없이 검색하거나 지정한 순서로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-105">In addition, you can search for words or phrases in any order, or you can search for words and phrases in the order in which you specify them.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ac173-106">는 이전에 사용 되지 않는 [일반 근접 단어](#Generic_NEAR)와의 새로운 인 [사용자 지정 근접 단어](#Custom_NEAR)를 모두 지원 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-106">supports both the earlier [generic proximity term](#Generic_NEAR), which is now deprecated, and the [custom proximity term](#Custom_NEAR), which is new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
##  <a name="the-custom-proximity-term"></a><a name="Custom_NEAR"></a><span data-ttu-id="ac173-107">사용자 지정 근접 단어</span><span class="sxs-lookup"><span data-stu-id="ac173-107">The Custom Proximity Term</span></span>  
 <span data-ttu-id="ac173-108">사용자 지정 근접 단어는 다음과 같은 새로운 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-108">The custom proximity term introduces the following new capabilities:</span></span>  
  
-   <span data-ttu-id="ac173-109">일치 항목이 되기 위한 첫 번째 검색 단어와 마지막 검색 단어를 분리하는 검색 대상이 아닌 단어의 최대 수( *최대 거리*)를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-109">You can specify the maximum number of non-search terms, or *maximum distance*, that separates the first and last search terms in order to constitute a match.</span></span>  
  
-   <span data-ttu-id="ac173-110">최대 단어 수를 지정하는 경우 일치 항목이 지정된 순서로 검색 단어를 포함하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-110">If you specify the maximum number of terms, you can also specify that matches must contain the search terms in the specified order.</span></span>  
  
 <span data-ttu-id="ac173-111">일치 항목이 되려면 텍스트 문자열은 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-111">To qualify as a match, a string of text must:</span></span>  
  
-   <span data-ttu-id="ac173-112">지정된 검색 단어 중 하나로 시작하고 지정된 다른 검색 단어 중 하나로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-112">Start with one of the specified search terms and end with the one of the other specified search terms.</span></span>  
  
-   <span data-ttu-id="ac173-113">지정된 검색 단어를 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-113">Contain all of the specified search terms.</span></span>  
  
-   <span data-ttu-id="ac173-114">중지 단어를 포함하여 첫 번째 검색 단어와 마지막 검색 단어 사이에 있는 검색 대상이 아닌 단어의 수는 최대 거리(지정된 경우)보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-114">The number of non-search terms, including stopwords, that occur between the first and last search terms must be less than or equal to the maximum distance, if specified.</span></span>  
  
 <span data-ttu-id="ac173-115">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-115">The basic syntax is:</span></span>  
  
 <span data-ttu-id="ac173-116">NEAR (</span><span class="sxs-lookup"><span data-stu-id="ac173-116">NEAR (</span></span>  
  
 <span data-ttu-id="ac173-117">{</span><span class="sxs-lookup"><span data-stu-id="ac173-117">{</span></span>  
  
 <span data-ttu-id="ac173-118">*search_term* [,... *n* ]</span><span class="sxs-lookup"><span data-stu-id="ac173-118">*search_term* [ ,...*n* ]</span></span>  
  
 |  
  
 <span data-ttu-id="ac173-119">(*search_term* [,... *n* ]) [, <maximum_distance> [, <match_order>]]</span><span class="sxs-lookup"><span data-stu-id="ac173-119">(*search_term* [ ,...*n* ] ) [, <maximum_distance> [, <match_order> ] ]</span></span>  
  
 <span data-ttu-id="ac173-120">}</span><span class="sxs-lookup"><span data-stu-id="ac173-120">}</span></span>  
  
 <span data-ttu-id="ac173-121">)</span><span class="sxs-lookup"><span data-stu-id="ac173-121">)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac173-122"><custom_proximity_term> 구문에 대한 자세한 내용은 [CONTAINS&#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac173-122">For more information about the <custom_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="ac173-123">예를 들어 다음과 같이 'Smith'와의 사이에 최대 두 단어가 있는 'John'을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-123">For example, you could search for 'John' within two terms of 'Smith', as follows:</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((John, Smith), 2)')  
```  
  
 <span data-ttu-id="ac173-124">일치하는 문자열의 예로는 "`John Jacob Smith`" 및 "`Smith, John`" 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-124">Some examples of strings that match are "`John Jacob Smith`" and "`Smith, John`".</span></span> <span data-ttu-id="ac173-125">문자열 "`John Jones knows Fred Smith`"는 두 단어 사이에 검색 대상이 아닌 단어가 3개 있으므로 일치 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-125">The string "`John Jones knows Fred Smith`" contains three intervening non-search terms, so it is not a match.</span></span>  
  
 <span data-ttu-id="ac173-126">특정 순서로 단어를 찾으려면 예에 있는 근접 단어를 `NEAR((John, Smith),2, TRUE).` 로 변경합니다. 이제 "`John`"와 두 단어 거리 이내에서 "`Smith`"을 검색하지만 "`John`"이 "`Smith`"의 앞에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-126">To require that the terms be found in the specified order, you would change the example proximity term to `NEAR((John, Smith),2, TRUE).` This searches for "`John`" within two terms of "`Smith`" but only when "`John`" precedes "`Smith`".</span></span> <span data-ttu-id="ac173-127">영어와 같이 왼쪽에서 오른쪽으로 읽는 언어에서 일치하는 문자열의 예로는 "`John Jacob Smith`"가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-127">In a language that reads from left to right, such as English, an example of a string that matches is "`John Jacob Smith`".</span></span>  
  
 <span data-ttu-id="ac173-128">아랍어나 히브리어와 같이 오른쪽에서 왼쪽으로 읽는 언어에서는 전체 텍스트 엔진이 지정된 단어를 반대 방향으로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-128">Note that for a language that reads from right to left, such as Arabic or Hebrew, the Full-Text Engine applies the specified terms in reverse order.</span></span> <span data-ttu-id="ac173-129">또한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 개체 탐색기는 오른쪽에서 왼쪽으로 읽는 언어로 지정된 단어의 표시 순서를 자동으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-129">Also, Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] automatically reverses the display order of words specified in right-to-left languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac173-130">자세한 내용은 이 항목의 뒷부분에 나오는 "[근접 검색에 대한 추가 고려 사항](#Additional_Considerations)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac173-130">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="how-maximum-distance-is-measured"></a><span data-ttu-id="ac173-131">최대 거리를 측정하는 방법</span><span class="sxs-lookup"><span data-stu-id="ac173-131">How Maximum Distance Is Measured</span></span>  
 <span data-ttu-id="ac173-132">10 또는 25와 같은 특정 최대 거리는 지정된 문자열에서 중지 단어를 포함하여 첫 번째 검색 단어와 마지막 검색 단어 사이에 있는 검색 대상이 아닌 단어의 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-132">A specific maximum distance, such as 10 or 25, determines how many non-search terms, including stopwords, can occur between the first and last search terms in a given string.</span></span> <span data-ttu-id="ac173-133">예를 들어 `NEAR((dogs, cats, "hunting mice"), 3)` 는 검색 대상이 아닌 단어 수가 총 3개("`enjoy`", "`but`" 및 "`avoid`")인 다음 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-133">For example, `NEAR((dogs, cats, "hunting mice"), 3)` would return the following row, in which the total number of non-search terms is three ("`enjoy`", "`but`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="ac173-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="ac173-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span></span>  
  
 <span data-ttu-id="ac173-135">이 근접 단어는 검색 대상이 아닌 단어가 4개("`enjoy`", "`but`", "`usually`" 및 "`avoid`")여서 최대 거리가 초과된 다음 행을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-135">The same proximity term would not return the following row, because the maximum distance is exceeded by the four non-search terms ("`enjoy`", "`but`", "`usually`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="ac173-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="ac173-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span></span>  
  
### <a name="combining-a-custom-proximity-term-with-other-terms"></a><span data-ttu-id="ac173-137">사용자 지정 근접 단어와 기타 단어 결합</span><span class="sxs-lookup"><span data-stu-id="ac173-137">Combining a Custom Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="ac173-138">사용자 지정 근접 단어를 일부 다른 단어와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-138">You can combine a custom proximity term with some other terms.</span></span> <span data-ttu-id="ac173-139">AND(&), OR(|) 또는 AND NOT(&!)을 사용하여 사용자 지정 근접 단어를 다른 사용자 지정 근접 단어, 단순 단어 또는 접두사 단어와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-139">You can use AND (&), OR (|), or AND NOT (&!) to combine a custom proximity term with another custom proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="ac173-140">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ac173-140">For example:</span></span>  
  
-   <span data-ttu-id="ac173-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span><span class="sxs-lookup"><span data-stu-id="ac173-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span></span>  
  
-   <span data-ttu-id="ac173-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span><span class="sxs-lookup"><span data-stu-id="ac173-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span></span>  
  
-   <span data-ttu-id="ac173-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span><span class="sxs-lookup"><span data-stu-id="ac173-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span></span>  
  
-   <span data-ttu-id="ac173-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span><span class="sxs-lookup"><span data-stu-id="ac173-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span></span>  
  
-   <span data-ttu-id="ac173-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span><span class="sxs-lookup"><span data-stu-id="ac173-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span></span>  
  
 <span data-ttu-id="ac173-146">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-146">For example,</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((term1, term2), 5, TRUE) AND term3')  
```  
  
 <span data-ttu-id="ac173-147">사용자 지정 근접 단어를 일반 근접 단어 (*term1* NEAR *term2*), 생성 단어 (isabout ...) 또는 가중치가 적용 된 용어 (양식 ...)와 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-147">You cannot combine a custom proximity term with a generic proximity term (*term1* NEAR *term2*), a generation term (ISABOUT ...), or a weighted term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-custom-proximity-term"></a><span data-ttu-id="ac173-148">예제: 사용자 지정 근접 단어 사용</span><span class="sxs-lookup"><span data-stu-id="ac173-148">Example: Using the Custom Proximity Term</span></span>  
 <span data-ttu-id="ac173-149">다음 예에서는 `Production.Document` 샘플 데이터베이스의 `AdventureWorks2012` 테이블에서 "bracket"이라는 단어와 동일한 문서에 "reflector"라는 단어가 들어 있는 모든 문서 요약을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-149">The following example searches the `Production.Document` table of the `AdventureWorks2012` sample database for all document summaries that contain the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  

  
##  <a name="additional-considerations-for-proximity-searches"></a><a name="Additional_Considerations"></a><span data-ttu-id="ac173-150">근접 검색에 대 한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ac173-150">Additional Considerations for Proximity Searches</span></span>  
 <span data-ttu-id="ac173-151">이 섹션에서는 일반 및 사용자 지정 근접 검색에 영향을 미치는 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-151">This section discusses consideration that affect both generic and custom proximity searches:</span></span>  
  
-   <span data-ttu-id="ac173-152">검색 단어가 겹쳐서 나타남</span><span class="sxs-lookup"><span data-stu-id="ac173-152">Overlapping occurrences of search terms</span></span>  
  
     <span data-ttu-id="ac173-153">모든 근접 검색은 검색 단어가 겹치지 않는 경우만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-153">All proximity searches always look for only non-overlapping occurrences.</span></span> <span data-ttu-id="ac173-154">검색 단어가 겹쳐서 나타나는 경우 일치 항목이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-154">Overlapping occurrences of search terms never qualify as matches.</span></span> <span data-ttu-id="ac173-155">예를 들어 다음 근접 단어는 최대 거리를 두 단어로 지정하여 "`A`" 및 "`AA`"를 이 순서대로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-155">For example, consider the following proximity term, which searches "`A`" and "`AA`" in this order with a maximum distance of two terms:</span></span>  
  
    ```  
    CONTAINS(column_name, 'NEAR((A,AA),2, TRUE')  
    ```  
  
     <span data-ttu-id="ac173-156">가능한 일치 항목은 "`AAA`", "`A.AA`" 및 "`A..AA`" 등입니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-156">The possible matches are as "`AAA`", "`A.AA`", and "`A..AA`".</span></span> <span data-ttu-id="ac173-157">"`AA`"만 포함하는 행은 일치 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-157">Rows containing just "`AA`" would not match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac173-158">예를 들어 `NEAR("mountain bike", "bike trails")` 또는 `(NEAR(comfort*, comfortable), 5)`와 같이 겹치는 단어를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-158">You can specify terms that overlap, for example, `NEAR("mountain bike", "bike trails")` or `(NEAR(comfort*, comfortable), 5)`.</span></span> <span data-ttu-id="ac173-159">겹치는 단어를 지정하면 일치하는 항목의 가능한 조합이 늘어나므로 쿼리의 복잡도가 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-159">Specifying a overlapping terms increases the complexity of the query by increasing the possible match permutations.</span></span> <span data-ttu-id="ac173-160">이렇게 겹치는 단어를 많이 지정하면 쿼리가 리소스 부족으로 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-160">If you specify a large number of such overlapping terms, the query can run out of resources and fail.</span></span> <span data-ttu-id="ac173-161">이런 경우 쿼리를 단순화한 다음 다시 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac173-161">If this occurs, simplify the query and try again.</span></span>  
  
-   <span data-ttu-id="ac173-162">일반 NEAR 및 사용자 지정 NEAR는 최대 거리 지정 여부에 관계없이 모두 단어간 절대 거리가 아닌 논리적 거리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-162">Both generic NEAR and custom NEAR (regardless of whether a maximum distance is specified) indicate the logical distance between terms, rather than the absolute distance between them.</span></span> <span data-ttu-id="ac173-163">예를 들어 단락 내에서 다른 구 또는 문장에 있는 단어는 관련이 더 적다고 가정하므로 실제 근접성에 관계없이 같은 구 또는 문장에 있는 단어보다 더 멀리 떨어져 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-163">For example, terms within different phrases or sentences within a paragraph are treated as farther apart than terms in the same phrase or sentence, regardless of their actual proximity, on the assumption that they are less related.</span></span> <span data-ttu-id="ac173-164">마찬가지로 다른 단락에 있는 단어는 이보다도 더 많이 떨어져 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-164">Likewise, terms in different paragraphs are treated as being even farther apart.</span></span> <span data-ttu-id="ac173-165">일치 항목이 문장, 단락 또는 장의 끝을 넘어가면 문서의 순위를 지정하는 데 사용되는 간격이 각각 8, 128 또는 1024만큼 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-165">If a match spans the end of a sentence, paragraph, or chapter, the gap used for ranking a document is increased by 8, 128, or 1024, respectively.</span></span>  
  
-   <span data-ttu-id="ac173-166">CONTAINSTABLE 함수의 순위 지정에 근접 단어가 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="ac173-166">Impact of proximity terms on ranking by the CONTAINSTABLE function</span></span>  
  
     <span data-ttu-id="ac173-167">CONTAINSTABLE 함수에서 NEAR를 사용하는 경우 문서 길이에 상대적인 문서 내 적중 수와 각 적중의 첫 번째 검색 단어와 마지막 검색 단어 간 거리가 각 문서의 순위에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-167">When NEAR is used in the CONTAINSTABLE function, the number of hits in a document relative to its length as well as the distance between the first and last search terms in each of the hits affects the ranking of each document.</span></span> <span data-ttu-id="ac173-168">일반 근접 단어의 경우 일치하는 검색 단어가 논리적 단어 50개보다 더 떨어져 있으면 문서에 대해 반환되는 순위는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-168">For a generic proximity term, if the matched search terms are >50 logical terms apart, the rank returned on a document is 0.</span></span> <span data-ttu-id="ac173-169">최대 거리로 정수를 지정하지 않은 사용자 지정 근접 단어의 경우 간격이 논리적 단어 100개보다 더 떨어져 있는 적중만 포함된 문서의 순위는 0이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-169">For a custom proximity term that does not specify an integer as the maximum distance, a document that contains only hits whose gap is >100 logical terms will receive a ranking of 0.</span></span> <span data-ttu-id="ac173-170">사용자 지정 근접 검색의 순위 지정에 대한 자세한 내용은 [Limit Search Results with RANK](limit-search-results-with-rank.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac173-170">For more information about ranking of custom proximity searches, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
-   <span data-ttu-id="ac173-171">**의미 없는 단어 변환** 서버 옵션</span><span class="sxs-lookup"><span data-stu-id="ac173-171">The **transform noise words** server option</span></span>  
  
     <span data-ttu-id="ac173-172">근접 검색에 중지 단어가 지정된 경우 **의미 없는 단어 변환** 의 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 중지 단어를 처리하는 방법에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-172">The value of **transform noise words** impacts how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] treats stopwords if they are specified in proximity searches.</span></span> <span data-ttu-id="ac173-173">자세한 내용은 [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac173-173">For more information, see [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).</span></span>  
  

  
##  <a name="the-deprecated-generic-proximity-term"></a><a name="Generic_NEAR"></a><span data-ttu-id="ac173-174">사용 되지 않는 일반 근접 단어</span><span class="sxs-lookup"><span data-stu-id="ac173-174">The Deprecated Generic Proximity Term</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="ac173-175">[사용자 지정 근접 단어](#Custom_NEAR)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-175">We recommend that you use the [custom proximity term](#Custom_NEAR).</span></span>  
  
 <span data-ttu-id="ac173-176">일반 근접 단어를 사용하는 경우 일치 항목이 반환되려면 지정된 검색 단어가 모두 문서에 포함되어 있어야 합니다. 이때 검색 단어 사이의 검색 대상이 아닌 단어 수( *거리*)는 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-176">A generic proximity term indicates that the specified search terms must all occur in a document for a match to be returned, regardless of the number of non-search terms (the *distance*) between the search terms.</span></span> <span data-ttu-id="ac173-177">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-177">The basic syntax is:</span></span>  
  
 <span data-ttu-id="ac173-178">{ *search_term* {NEAR | ~} *search_term* } [ ,... *n* ]</span><span class="sxs-lookup"><span data-stu-id="ac173-178">{ *search_term* { NEAR | ~ } *search_term* } [ ,...*n* ]</span></span>  
  
 <span data-ttu-id="ac173-179">예를 들어 다음 예에서 일치 항목이 반환되려면 순서에 관계없이 단어 'fox'와 'chicken'이 모두 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-179">For example, in the following examples, the words 'fox' and 'chicken' must both appear, in either order, to produce a match:</span></span>  
  
-   `CONTAINS(column_name, 'fox NEAR chicken')`  
  
-   `CONTAINSTABLE(table_name, column_name, 'fox ~ chicken')`  
  
> [!NOTE]  
>  <span data-ttu-id="ac173-180"><generic_proximity_term> 구문에 대한 자세한 내용은 [CONTAINS&#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac173-180">For information about the <generic_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="ac173-181">자세한 내용은 이 항목의 뒷부분에 나오는 "[근접 검색에 대한 추가 고려 사항](#Additional_Considerations)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac173-181">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="combining-a-generic-proximity-term-with-other-terms"></a><span data-ttu-id="ac173-182">일반 근접 단어와 기타 단어 결합</span><span class="sxs-lookup"><span data-stu-id="ac173-182">Combining a Generic Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="ac173-183">AND(&), OR(|) 또는 AND NOT(&!)을 사용하여 일반 근접 단어를 다른 일반 근접 단어, 단순 단어 또는 접두사 단어와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-183">You can use AND (&), OR (|), or AND NOT (&!) to combine a generic proximity term with another generic proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="ac173-184">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ac173-184">For example:</span></span>  
  
```  
CONTAINSTABLE (Production.ProductDescription,  
   Description,   
   '(light NEAR aluminum) OR  
   (lightweight NEAR aluminum)'  
)  
```  
  
 <span data-ttu-id="ac173-185">일반 근접 단어를 `NEAR((term1,term2),5)` 가중치 단어 (ISABOUT ...) 또는 세대 term (양식 ...)과 같은 사용자 지정 근접 단어와 결합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-185">You cannot combine a generic proximity term with a custom proximity term, such as `NEAR((term1,term2),5)`, a weighted term (ISABOUT ...), or a generational term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-generic-proximity-term"></a><span data-ttu-id="ac173-186">예제: 일반 근접 단어 사용</span><span class="sxs-lookup"><span data-stu-id="ac173-186">Example: Using the Generic Proximity Term</span></span>  
 <span data-ttu-id="ac173-187">다음 예에서는 일반 근접 단어를 사용하여 "bracket"이라는 단어와 동일한 문서에서 "reflector"라는 단어를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-187">The following example uses the generic proximity term to search for the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable INNER JOIN  
  CONTAINSTABLE(Production.Document, Document,  
  '(reflector NEAR bracket)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
 <span data-ttu-id="ac173-188">CONTAINSTABLE에서 단어 순서를 바꿔도 결과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-188">Notice that you can also reverse the terms in CONTAINSTABLE to get the same result:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(bracket NEAR reflector)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="ac173-189">위의 쿼리에서 NEAR 키워드 대신 물결표(~)를 사용해도 결과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-189">You can use the tilde character (~) in place of the NEAR keyword in the earlier query, and get the same results:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="ac173-190">검색 조건에 단어나 구를 세 개 이상 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-190">More than two words or phrases can be specified in the search conditions.</span></span> <span data-ttu-id="ac173-191">예를 들면 다음과 같이 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-191">For example, it is possible to write:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket ~ installation)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="ac173-192">이 구문은 "reflector"가 "bracket"과 같은 문서에 있어야 하고 "bracket"이 "installation"과 같은 문서에 있어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac173-192">This means that "reflector" must be in the same document as "bracket", and "bracket" must be in the same document as "installation".</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="ac173-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac173-193">See Also</span></span>  
 <span data-ttu-id="ac173-194">[CONTAINSTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ac173-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="ac173-195">[전체 텍스트 검색을 사용한 쿼리](query-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="ac173-195">[Query with Full-Text Search](query-with-full-text-search.md) </span></span>  
 [<span data-ttu-id="ac173-196">CONTAINS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ac173-196">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
