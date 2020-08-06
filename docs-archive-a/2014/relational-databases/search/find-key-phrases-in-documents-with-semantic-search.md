---
title: 의미 체계 검색을 사용하여 문서에서 키 구 찾기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8388fb704bf13f44d025e6e32a1450d537f61832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730451"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a><span data-ttu-id="048ff-102">의미 체계 검색을 사용하여 문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="048ff-102">Find Key Phrases in Documents with Semantic Search</span></span>
  <span data-ttu-id="048ff-103">통계 의미 체계 인덱싱을 위해 구성된 문서 또는 텍스트 열의 키 구를 찾는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-103">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-key-phrases-in-documents"></a><a name="BasicsQueryKey"></a><span data-ttu-id="048ff-104">문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="048ff-104">Finding Key Phrases in Documents</span></span>  
  
###  <a name="how-to-find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a><span data-ttu-id="048ff-105">방법: SEMANTICKEYPHRASETABLE를 사용 하 여 문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="048ff-105">How to: Find the Key Phrases in Documents with SEMANTICKEYPHRASETABLE</span></span>  
 <span data-ttu-id="048ff-106">특정 문서에서 키 구를 식별하거나 특정 키 구가 포함된 문서를 식별하려면 [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 함수를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-106">To identify the key phrases in specific documents, or to identify documents that contain specific key phrases, query the function [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
 <span data-ttu-id="048ff-107">SEMANTICKEYPHRASETABLE은 지정된 테이블의 열과 관련된 키 구가 있는 0개 이상의 행으로 구성된 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-107">SEMANTICKEYPHRASETABLE returns a table with zero, one, or more rows for those key phrases associated with columns in the specified table.</span></span> <span data-ttu-id="048ff-108">SELECT 문의 FROM 절에서 이 행 집합 함수를 일반 테이블 이름과 마찬가지로 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-108">This rowset function can be referenced in the FROM clause of a SELECT statement as if it were a regular table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="048ff-109">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 단일 단어만 의미 체계 검색을 위해 인덱싱되며 여러 단어로 된 구(ngrams)는 인덱싱되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-109">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], only single words are indexed for semantic search; multi-word phrases (ngrams) are not indexed.</span></span> <span data-ttu-id="048ff-110">또한 동일한 단어의 다양한 형태가 개별적으로 인덱싱됩니다. 예를 들어 "computer"와 "computers"는 개별적으로 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-110">Also, various forms of the same word are indexed separately; for example, "computer" and "computers" are indexed separately.</span></span>  
  
 <span data-ttu-id="048ff-111">SEMANTICKEYPHRASETABLE 함수에 필요한 매개 변수와 이 함수에서 반환되는 결과 테이블에 대한 자세한 내용은 [semantickeyphrasetable&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="048ff-111">For detailed information about the parameters required by the SEMANTICKEYPHRASETABLE function, and about the table of results that it returns, see [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="048ff-112">대상 열에는 전체 텍스트 및 의미 체계 인덱싱이 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a><span data-ttu-id="048ff-113">예 1: 특정 문서에서 상위 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="048ff-113">Example 1: Find the Top Key Phrases in a Specific Document</span></span>  
 <span data-ttu-id="048ff-114">다음 예제에서는 AdventureWorks 예제 데이터베이스에 있는 Production.Document 테이블의 Document 열에서 @DocumentId 변수를 통해 지정된 문서에서 상위 10개의 키 구를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-114">The following example retrieves the top 10 key phrases from the document specified by the @DocumentId variable in the Document column of the Production.Document table of the AdventureWorks sample database.</span></span> <span data-ttu-id="048ff-115">@DocumentId 변수는 전체 텍스트 인덱스의 키 열에 있는 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-115">The @DocumentId variable represents a value from the key column of the full-text index.</span></span>  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 <span data-ttu-id="048ff-116">**SEMANTICKEYPHRASETABLE** 함수는 테이블 검색 대신 인덱스 검색을 사용하여 이러한 결과를 효율적으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-116">The **SEMANTICKEYPHRASETABLE** function retrieves these results efficiently by using an index seek instead of a table scan.</span></span>  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a><span data-ttu-id="048ff-117">예 2: 특정 키 구가 포함 된 상위 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="048ff-117">Example 2: Find the Top Documents that Contain a Specific Key Phrase</span></span>  
 <span data-ttu-id="048ff-118">다음 예제에서는 AdventureWorks 예제 데이터베이스에 있는 Production.Document 테이블의 Document 열에서 "Bracket" 키 구가 포함된 상위 25개의 문서를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="048ff-118">The following example retrieves the top 25 documents that contain the key phrase "Bracket" from the Document column of the Production.Document table of the AdventureWorks sample database.</span></span>  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
