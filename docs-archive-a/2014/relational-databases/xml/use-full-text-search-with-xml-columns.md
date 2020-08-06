---
title: XML 열에 전체 텍스트 검색 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml columns [full-text search]
- indexes [full-text search]
ms.assetid: 8096cfc6-1836-4ed5-a769-a5d63b137171
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b6b23933fde6a09d043c7055b0daa7c07035cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730227"
---
# <a name="use-full-text-search-with-xml-columns"></a><span data-ttu-id="b53f9-102">XML 열에 전체 텍스트 검색 사용</span><span class="sxs-lookup"><span data-stu-id="b53f9-102">Use Full-Text Search with XML Columns</span></span>
  <span data-ttu-id="b53f9-103">XML 값의 내용을 인덱싱하지만 XML 태그는 무시하는 전체 텍스트 인덱스를 XML 열에 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-103">You can create a full-text index on XML columns that indexes the content of the XML values, but ignores the XML markup.</span></span> <span data-ttu-id="b53f9-104">요소 태그는 토큰 경계로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-104">Element tags are used as token boundaries.</span></span> <span data-ttu-id="b53f9-105">다음 항목이 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-105">The following items are indexed:</span></span>  
  
-   <span data-ttu-id="b53f9-106">XML 요소의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-106">The content of XML elements.</span></span>  
  
-   <span data-ttu-id="b53f9-107">그 값이 숫자 값이 아니면 최상위 요소의 XML 특성의 내용만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-107">The content of XML attributes of the top-level element only, unless those values are numeric values.</span></span>  
  
 <span data-ttu-id="b53f9-108">가능한 경우 다음과 같은 방식으로 전체 텍스트 검색을 XML 인덱스와 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-108">When possible, you can combine full-text search with XML index in the following way:</span></span>  
  
1.  <span data-ttu-id="b53f9-109">먼저 SQL 전체 텍스트 검색을 사용하여 원하는 XML 값을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-109">First, filter the XML values of interest by using SQL full-text search.</span></span>  
  
2.  <span data-ttu-id="b53f9-110">그런 다음 XML 열에서 XML 인덱스를 사용하는 해당 XML 값을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-110">Next, query those XML values that use XML index on the XML column.</span></span>  
  
## <a name="example-combining-full-text-search-with-xml-querying"></a><span data-ttu-id="b53f9-111">예제: 전체 텍스트 검색과 XML 쿼리 조합</span><span class="sxs-lookup"><span data-stu-id="b53f9-111">Example: Combining Full-text Search with XML Querying</span></span>  
 <span data-ttu-id="b53f9-112">XML 열에 전체 텍스트 인덱스를 만든 후 다음 쿼리는 XML 값에 책 제목 중 "custom"이라는 단어가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-112">After the full-text index has been created on the XML column, the following query checks that an XML value contains the word "custom" in the title of a book:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'custom')   
AND    xCol.exist('/book/title/text()[contains(.,"custom")]') =1  
```  
  
 <span data-ttu-id="b53f9-113">**contains()** 메서드는 전체 텍스트 인덱스를 사용하여 문서의 아무 곳에나 "custom"이 포함된 XML 값을 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-113">The **contains()** method uses the full-text index to subset the XML values that contain the word "custom" anywhere in the document.</span></span> <span data-ttu-id="b53f9-114">**exist()** 절은 "custom"이 책의 제목 부분에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-114">The **exist()** clause ensures that the word "custom" occurs in the title of a book.</span></span>  
  
 <span data-ttu-id="b53f9-115">**contains()** 및 XQuery **contains()** 를 사용하는 전체 텍스트 검색은 서로 다른 의미를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-115">A full-text search that uses **contains()** and XQuery **contains()** has different semantics.</span></span> <span data-ttu-id="b53f9-116">후자는 하위 문자열 일치 검색이며 전자는 형태소 분석을 사용하는 토큰 일치 검색입니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-116">The latter is a substring match and the former is a token match that uses stemming.</span></span> <span data-ttu-id="b53f9-117">따라서 검색이 제목에 "run"이 포함된 문자열을 찾는 경우, 전체 텍스트 **contains()** 및 Xquery **contains()** 가 모두 만족하기 때문에 일치 항목에는 "run", "runs" 및 "running"이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-117">Therefore, if the search is for the string that has "run" in the title, the matches will include "run", "runs", and "running", because both the full-text **contains()** and the Xquery **contains()** are satisfied.</span></span> <span data-ttu-id="b53f9-118">하지만 쿼리가 전체 텍스트 **contains()** 가 실패한 제목에서 "customizable"이라는 단어와 일치하지 않지만 Xquery **contains()** 는 만족합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-118">However, the query does not match the word "customizable" in the title in that the full-text **contains()** fails, but the Xquery **contains()** is satisfied.</span></span> <span data-ttu-id="b53f9-119">일반적으로 순수한 부분 문자열 비교를 위해 전체 텍스트 **contains()** 절을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-119">Generally, for pure substring match, the full-text **contains()** clause should be removed.</span></span>  
  
 <span data-ttu-id="b53f9-120">또한 전체 텍스트 검색은 단어 형태소 분석을 사용하지만 XQuery **contains()** 는 리터럴 일치 검색입니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-120">Additionally, full-text search uses word stemming, but XQuery **contains()** is a literal match.</span></span> <span data-ttu-id="b53f9-121">이러한 차이점은 다음 예에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-121">This difference is illustrated in the next example.</span></span>  
  
## <a name="example-full-text-search-on-xml-values-using-stemming"></a><span data-ttu-id="b53f9-122">예제: 형태소 분석을 사용하여 XML 값에서 전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="b53f9-122">Example: Full-text Search on XML Values Using Stemming</span></span>  
 <span data-ttu-id="b53f9-123">이전 예에서 수행된 XQuery **contains()** 검사는 일반적으로 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-123">The XQuery **contains()** check that was performed in the previous example generally cannot be eliminated.</span></span> <span data-ttu-id="b53f9-124">다음 쿼리를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="b53f9-124">Consider this query:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'run')   
```  
  
 <span data-ttu-id="b53f9-125">문서에 있는 "ran"이라는 단어는 형태소 분석으로 인해 검색 조건과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-125">The word "ran" in the document matches the search condition because of stemming.</span></span> <span data-ttu-id="b53f9-126">또한 검색 컨텍스트는 XQuery를 사용하여 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-126">Additionally, the search context is not checked by using XQuery.</span></span>  
  
 <span data-ttu-id="b53f9-127">전체 텍스트 인덱싱되는 AXSD를 사용하여 XML을 관계형 열로 분해하는 경우 XML 뷰에 대해 발생하는 XPath 쿼리는 기본 테이블에서 전체 텍스트 검색을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b53f9-127">When XML is decomposed into relational columns by using AXSD that are full-text indexed, XPath queries that occur over the XML view do not perform full-text search on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53f9-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b53f9-128">See Also</span></span>  
 [<span data-ttu-id="b53f9-129">XML 인덱스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b53f9-129">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
