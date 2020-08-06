---
title: 의미 체계 검색(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91062864b77ba3c62a87d66b8ff93068f9c10c8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735180"
---
# <a name="semantic-search-sql-server"></a><span data-ttu-id="a618b-102">의미 체계 검색(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a618b-102">Semantic Search (SQL Server)</span></span>
  <span data-ttu-id="a618b-103">통계 의미 체계 검색은 통계적으로 관련성이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 키 구 *를 추출한 다음 인덱싱하여*데이터베이스에 저장된 구조화되지 않은 문서를 깊이 있게 검색하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-103">Statistical Semantic Search provides deep insight into unstructured documents stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases by extracting and indexing statistically relevant *key phrases*.</span></span> <span data-ttu-id="a618b-104">그런 다음 이 키 구를 사용하여 *유사하거나 관련된 문서*를 식별한 후 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-104">Then it also uses these key phrases to identify and index *documents that are similar or related*.</span></span>  
  
 <span data-ttu-id="a618b-105">세 개의 Transact-SQL 행 집합 함수를 통해 의미 체계 인덱스를 쿼리하여 구조화된 데이터 결과를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-105">You query these semantic indexes by using three Transact-SQL rowset functions to retrieve the results as structured data.</span></span>  
  
##  <a name="what-can-i-do-with-semantic-search"></a><a name="whatcanido"></a><span data-ttu-id="a618b-106">의미 체계 검색을 사용 하 여 무엇을 할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="a618b-106">What Can I Do with Semantic Search?</span></span>  
 <span data-ttu-id="a618b-107">의미 체계 검색은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기존 전체 텍스트 검색 기능을 기반으로 구축되었지만 이를 통해 키워드 검색보다 뛰어난 새로운 시나리오가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-107">Semantic search builds upon the existing full-text search feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but enables new scenarios that extend beyond keyword searches.</span></span> <span data-ttu-id="a618b-108">전체 텍스트 검색을 사용하면 문서의 *단어* 를 쿼리할 수 있지만, 의미 체계 검색을 사용하면 문서의 *의미* 를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-108">While full-text search lets you query the *words* in a document, semantic search lets you query the *meaning* of the document.</span></span> <span data-ttu-id="a618b-109">가능한 솔루션에는 자동 태그 추출, 관련 내용 검색 및 유사 내용 간의 계층 탐색이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-109">Solutions that are now possible include automatic tag extraction, related content discovery, and hierarchical navigation across similar content.</span></span> <span data-ttu-id="a618b-110">예를 들어 키 구의 인덱스를 쿼리하여 조직 또는 문서 모음에 대한 분류를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-110">For example, you can query the index of key phrases to build the taxonomy for an organization, or for a corpus of documents.</span></span> <span data-ttu-id="a618b-111">또는 문서 유사성 인덱스를 쿼리하여 업무 설명과 일치하는 이력서를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-111">Or, you can query the document similarity index to identify resumes that match a job description.</span></span>  
  
 <span data-ttu-id="a618b-112">다음 예에서는 의미 체계 검색 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-112">The following examples demonstrate the capabilities of Semantic Search.</span></span>  
  
###  <a name="find-the-key-phrases-in-a-document"></a><a name="find1"></a><span data-ttu-id="a618b-113">문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="a618b-113">Find the Key Phrases in a Document</span></span>  
 <span data-ttu-id="a618b-114">다음 쿼리는 예제 문서에서 식별된 키 구를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-114">The following query gets the key phrases that were identified in the sample document.</span></span> <span data-ttu-id="a618b-115">쿼리 결과는 각 키 구의 통계적 유의성 점수를 기준으로 내림차순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-115">It presents the results in descending order by the score that ranks the statistical significance of each key phrase.</span></span> <span data-ttu-id="a618b-116">이 쿼리는 [semantickeyphrasetable&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-116">This query calls the [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) function.</span></span>  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-similar-or-related-documents"></a><a name="find2"></a><span data-ttu-id="a618b-117">유사 하거나 관련 된 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="a618b-117">Find Similar or Related Documents</span></span>  
 <span data-ttu-id="a618b-118">다음 쿼리에서는 예제 문서와 유사하거나 관련된 것으로 확인된 문서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-118">The following query gets the documents that were identified as similar or related to the sample document.</span></span> <span data-ttu-id="a618b-119">쿼리 결과는 두 문서의 유의성 점수를 기준으로 내림차순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-119">It presents the results in descending order by the score that ranks the similarity of the 2 documents.</span></span> <span data-ttu-id="a618b-120">이 쿼리는 [semanticsimilaritytable&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-120">This query calls the [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) function.</span></span>  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-the-key-phrases-that-make-documents-similar-or-related"></a><a name="find3"></a><span data-ttu-id="a618b-121">문서를 비슷하거나 관련 된 것으로 만드는 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="a618b-121">Find the Key Phrases That Make Documents Similar or Related</span></span>  
 <span data-ttu-id="a618b-122">다음 쿼리에서는 두 예제 문서를 서로 유사하거나 관련된 것으로 만드는 키 구를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-122">The following query gets the key phrases that make the 2 sample documents similar or related to one another.</span></span> <span data-ttu-id="a618b-123">쿼리 결과는 각 키 구의 가중치 점수를 기준으로 내림차순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-123">It presents the results in descending order by the score that ranks the weight of each key phrase.</span></span> <span data-ttu-id="a618b-124">이 쿼리는 [semanticsimilaritydetailstable&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-124">This query calls the [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) function.</span></span>  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="storing-documents-in-sql-server"></a><a name="store"></a><span data-ttu-id="a618b-125">SQL Server에 문서 저장</span><span class="sxs-lookup"><span data-stu-id="a618b-125">Storing Documents in SQL Server</span></span>  
 <span data-ttu-id="a618b-126">의미 체계 검색을 사용하여 문서를 인덱싱하려면 문서를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-126">Before you can index documents with Semantic Search, you have to store the documents in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="a618b-127">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 FileTable 기능을 사용하여 구조화되지 않은 파일과 문서를 관계형 데이터베이스의 주요 데이터로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-127">The FileTable feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] makes unstructured files and documents first-class citizens of the relational database.</span></span> <span data-ttu-id="a618b-128">따라서 데이터베이스 개발자는 Transact-SQL 집합 기반 작업에서 구조화된 데이터와 함께 문서를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-128">As a result, database developers can manipulate documents together with structured data in Transact-SQL set-based operations.</span></span>  
  
 <span data-ttu-id="a618b-129">FileTable 기능에 대한 자세한 내용은 [FileTable&#40;SQL Server&#41;](../blob/filetables-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a618b-129">For more information about the FileTable feature, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span> <span data-ttu-id="a618b-130">데이터베이스에 문서를 저장하는 다른 옵션인 FILESTREAM 기능에 대한 자세한 내용은 [FILESTREAM&#40;SQL Server&#41;](../blob/filestream-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a618b-130">For information about the FILESTREAM feature, which is another option for storing documents in the database, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="a618b-131">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a618b-131">Related Tasks</span></span>  
 [<span data-ttu-id="a618b-132">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="a618b-132">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)  
 <span data-ttu-id="a618b-133">통계 의미 체계 검색을 위한 필수 구성 요소와 이러한 필수 구성 요소의 설치 또는 확인 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-133">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
 [<span data-ttu-id="a618b-134">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="a618b-134">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)  
 <span data-ttu-id="a618b-135">문서 또는 텍스트가 들어 있는 선택한 열에서 통계 의미 체계 인덱싱을 사용하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-135">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 [<span data-ttu-id="a618b-136">의미 체계 검색을 사용하여 문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="a618b-136">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)  
 <span data-ttu-id="a618b-137">통계 의미 체계 인덱싱을 위해 구성된 문서 또는 텍스트 열의 키 구를 찾는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-137">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="a618b-138">의미 체계 검색을 사용하여 유사하거나 관련된 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="a618b-138">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)  
 <span data-ttu-id="a618b-139">통계적 의미 체계 인덱싱을 위해 구성된 열에서 유사하거나 관련된 문서 또는 텍스트 값을 찾고 유사하거나 연관된 정도에 관한 정보를 찾는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-139">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="a618b-140">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="a618b-140">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
 <span data-ttu-id="a618b-141">의미 체계 인덱싱의 과정과 인덱스를 모니터링하고 관리하는 데 관련된 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-141">Describes the process of semantic indexing and the tasks related to monitoring and managing the indexes.</span></span>  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="a618b-142">관련 내용</span><span class="sxs-lookup"><span data-stu-id="a618b-142">Related Content</span></span>  
 [<span data-ttu-id="a618b-143">의미 체계 검색 DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="a618b-143">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="a618b-144">통계 의미 체계 검색을 지원하기 위해 추가되거나 변경된 Transact-SQL 문 및 SQL Server 데이터베이스 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a618b-144">Lists the Transact-SQL statements and the SQL Server database objects added or changed to support statistical semantic search.</span></span>  
  
  
