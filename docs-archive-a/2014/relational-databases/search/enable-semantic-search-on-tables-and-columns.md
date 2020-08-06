---
title: 테이블 및 열에 대한 의미 체계 검색 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], enabling
ms.assetid: 895d220c-6749-4954-9dd3-2ea4c6a321ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f11ba654f7cc34f521990e8c420d41885d3c55b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733812"
---
# <a name="enable-semantic-search-on-tables-and-columns"></a><span data-ttu-id="b32c2-102">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="b32c2-102">Enable Semantic Search on Tables and Columns</span></span>
  <span data-ttu-id="b32c2-103">문서 또는 텍스트가 들어 있는 선택한 열에서 통계 의미 체계 인덱싱을 사용하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-103">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 <span data-ttu-id="b32c2-104">통계 의미 체계 검색에서는 전체 텍스트 검색을 통해 생성되는 인덱스를 사용하고 추가 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-104">Statistical Semantic Search uses the indexes that are created by Full-Text Search, and creates additional indexes.</span></span> <span data-ttu-id="b32c2-105">전체 텍스트 검색에 대한 이 종속성의 결과로 새 전체 텍스트 인덱스를 정의하거나 기존 전체 텍스트 인덱스를 변경할 때는 새 의미 체계 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-105">As a result of this dependency on full-text search, you create a new semantic index when you define a new full-text index, or when you alter an existing full-text index.</span></span> <span data-ttu-id="b32c2-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하거나 이 항목에서 설명하는 대로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 전체 텍스트 인덱싱 마법사와 다른 대화 상자를 사용하여 새 의미 체계 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-106">You can create a new semantic index by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or by using the Full-Text Indexing Wizard and other dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as described in this topic.</span></span>  
  
##  <a name="creating-a-semantic-index"></a><a name="BasicEnabling"></a><span data-ttu-id="b32c2-107">의미 체계 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="b32c2-107">Creating a Semantic Index</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-semantic-index"></a><a name="reqenable"></a><span data-ttu-id="b32c2-108">의미 체계 인덱스를 만들기 위한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="b32c2-108">Requirements and Restrictions for Creating a Semantic Index</span></span>  
  
-   <span data-ttu-id="b32c2-109">전체 텍스트 인덱싱이 지원되는 데이터베이스 개체(테이블 및 인덱싱된 뷰 포함)에 대한 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-109">You can create an index on any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="b32c2-110">특정 열에 대해 의미 체계 인덱싱을 사용하도록 설정하려면 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-110">Before you can enable semantic indexing for specific columns, the following prerequisites must exist:</span></span>  
  
    -   <span data-ttu-id="b32c2-111">데이터베이스에 대한 전체 텍스트 카탈로그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-111">A full-text catalog must exist for the database.</span></span>  
  
    -   <span data-ttu-id="b32c2-112">테이블에 전체 텍스트 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-112">The table must have a full-text index.</span></span>  
  
    -   <span data-ttu-id="b32c2-113">선택한 열이 전체 텍스트 인덱스에 참여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-113">The selected columns must participate in the full-text index.</span></span>  
  
     <span data-ttu-id="b32c2-114">이러한 모든 요구 사항을 동시에 만들고 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-114">You can create and enable all these requirements at the same time.</span></span>  
  
-   <span data-ttu-id="b32c2-115">전체 텍스트 인덱싱이 지원되는 데이터 형식의 열에 대한 의미 체계 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-115">You can create a semantic index on columns that have any of the data types that are supported for full-text indexing.</span></span> <span data-ttu-id="b32c2-116">자세한 내용은 [전체 텍스트 인덱스 만들기 및 관리](create-and-manage-full-text-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-116">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
-   <span data-ttu-id="b32c2-117">`varbinary(max)` 열에 대해 전체 텍스트 인덱싱이 지원되는 문서 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-117">You can specify any document type that is supported for full-text indexing for `varbinary(max)` columns.</span></span> <span data-ttu-id="b32c2-118">자세한 내용은 이 항목의 [방법: 인덱싱할 수 있는 문서 유형 결정](#doctypes) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-118">For more information, see [How To: Determine Which Document Types Can Be Indexed](#doctypes) in this topic.</span></span>  
  
-   <span data-ttu-id="b32c2-119">의미 체계 인덱싱에서는 선택한 열에 대한 두 가지 유형의 인덱스, 즉 키 구 인덱스와 문서 유사성 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-119">Semantic indexing creates two types of indexes for the columns that you select - an index of key phrases, and an index of document similarity.</span></span> <span data-ttu-id="b32c2-120">의미 체계 인덱싱을 사용하도록 설정할 때 둘 중 한 가지 인덱스 유형만 선택할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-120">You cannot select only one type of index or the other when you enable semantic indexing.</span></span> <span data-ttu-id="b32c2-121">그러나 이러한 두 인덱스는 독립적으로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-121">However you can query these two indexes independently.</span></span> <span data-ttu-id="b32c2-122">자세한 내용은 [의미 체계 검색을 사용하여 문서의 키 구 찾기](find-key-phrases-in-documents-with-semantic-search.md) 및 [의미 체계 검색을 사용하여 유사하거나 관련된 문서 찾기](find-similar-and-related-documents-with-semantic-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-122">For more information, see [Find Key Phrases in Documents with Semantic Search](find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="b32c2-123">의미 체계 인덱스의 LCID를 명시적으로 지정하지 않으면 기본 언어와 관련 언어의 통계만 의미 체계 인덱싱에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-123">If you do not explicitly specify an LCID for a semantic index, then only the primary language and its associated language statistics are used for semantic indexing.</span></span>  
  
-   <span data-ttu-id="b32c2-124">언어 모델을 사용할 수 없는 열에 대해 언어를 지정하면 인덱스 만들기가 실패하고 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-124">If you specify a language for a column for which the language model is not available, the creation of the index fails and returns an error message.</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-no-full-text-index"></a><a name="HowToEnableCreate"></a><span data-ttu-id="b32c2-125">방법: 전체 텍스트 인덱스가 없을 때 의미 체계 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="b32c2-125">How To: Create a Semantic Index When There Is No Full-Text Index</span></span>  
 <span data-ttu-id="b32c2-126">**CREATE FULLTEXT INDEX** 문을 사용하여 새 전체 텍스트 인덱스를 만들 때 열 정의의 일부로 **STATISTICAL_SEMANTICS** 키워드를 지정하여 열 수준에서 의미 체계 인덱싱을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-126">When you create a new full-text index with the **CREATE FULLTEXT INDEX** statement, you can enable semantic indexing at the column level by specifying the keyword **STATISTICAL_SEMANTICS** as part of the column definition.</span></span> <span data-ttu-id="b32c2-127">전체 텍스트 인덱싱 마법사를 사용하여 새 전체 텍스트 인덱스를 만들 때 의미 체계 인덱싱을 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-127">You can also enable semantic indexing when you use the Full-Text Indexing Wizard to create a new full-text index.</span></span>  
  
 <span data-ttu-id="b32c2-128">**Transact-SQL을 사용하여 새 의미 체계 인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="b32c2-128">**Create a new semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="b32c2-129">**CREATE FULLTEXT INDEX** 문을 호출하고 의미 체계 인덱스를 만들 각 열에 대해 **STATISTICAL_SEMANTICS**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-129">Call the **CREATE FULLTEXT INDEX** statement and specify **STATISTICAL_SEMANTICS** for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="b32c2-130">이 문의 모든 옵션에 대한 자세한 내용은 [CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-130">For more information about all the options for this statement, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="b32c2-131">**예제 1: 고유 인덱스, 전체 텍스트 인덱스 및 의미 체계 인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="b32c2-131">**Example 1: Create a unique index, full-text index, and semantic index**</span></span>  
  
 <span data-ttu-id="b32c2-132">다음 예에서는 기본 전체 텍스트 카탈로그 **ft**를 만들고, AdventureWorks2012 예제 데이터베이스의 **HumanResources.JobCandidate** 테이블에 있는 **JobCandidateID** 열에 대해 고유 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-132">The following example creates a default full-text catalog, **ft**. The example then creates a unique index on the **JobCandidateID** column of the **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="b32c2-133">이 고유 인덱스는 전체 텍스트 인덱스에 대한 키 열로 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-133">This unique index is required as the key column for a full-text index.</span></span> <span data-ttu-id="b32c2-134">그런 다음 **Resume** 열에 대한 전체 텍스트 인덱스와 의미 체계 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-134">The example then creates a full-text index and a semantic index on the **Resume** column.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG ft AS DEFAULT  
GO  
  
CREATE UNIQUE INDEX ui_ukJobCand  
    ON HumanResources.JobCandidate(JobCandidateID)  
GO  
  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate  
    (Resume  
        Language 1033  
        Statistical_Semantics  
    )   
    KEY INDEX JobCandidateID   
    WITH STOPLIST = SYSTEM  
GO  
```  
  
 <span data-ttu-id="b32c2-135">**예제 2: 여러 열에 대한 전체 텍스트 및 의미 체계 인덱스 만들고 나중에 인덱스 채우기 수행**</span><span class="sxs-lookup"><span data-stu-id="b32c2-135">**Example 2: Create a full-text and semantic index on several columns with delayed index population**</span></span>  
  
 <span data-ttu-id="b32c2-136">다음 예에서는 AdventureWorks2012 예제 데이터베이스에 전체 텍스트 카탈로그인 **documents_catalog**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-136">The following example creates a full-text catalog, **documents_catalog**, in the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="b32c2-137">그런 다음 이 새 카탈로그를 사용하는 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-137">The example then creates a full-text index that uses this new catalog.</span></span> <span data-ttu-id="b32c2-138">전체 텍스트 인덱스는 **Production.Document**테이블의 **Title**, **DocumentSummary** 및 **Document** 열에 만들어지는 반면 의미 체계 인덱스는 **Document** 열에만 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-138">The full-text index is created on the **Title**, **DocumentSummary**, and **Document** columns of the **Production.Document** table, while the semantic index is only created on the **Document** column.</span></span> <span data-ttu-id="b32c2-139">이 전체 텍스트 인덱스는 새로 만든 전체 텍스트 카탈로그와 기존 고유 키 인덱스 **PK_Document_DocumentID**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-139">This full-text index uses the newly-created full-text catalog and an existing unique key index, **PK_Document_DocumentID**.</span></span> <span data-ttu-id="b32c2-140">권장한 대로 이 인덱스 키는 정수 열 **DocumentID**에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-140">As recommended, this index key is created on an integer column, **DocumentID**.</span></span> <span data-ttu-id="b32c2-141">이 예에서는 열의 데이터 언어인 영어의 LCID 1033을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-141">The example specifies the LCID for English, 1033, which is the language of the data in the columns.</span></span>  
  
 <span data-ttu-id="b32c2-142">또한 이 예에서는 채우기 작업을 수행하지 않고 변경 내용 추적이 해제되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-142">This example also specifies that change tracking is off with no population.</span></span> <span data-ttu-id="b32c2-143">나중에 사용률이 낮은 시간에 **ALTER FULLTEXT INDEX** 문을 사용하여 새 인덱스에 대해 전체 채우기를 시작하고 변경 내용 자동 추적을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-143">Later, during off-peak hours, the example uses an **ALTER FULLTEXT INDEX** statement to start a full population on the new index and enable automatic change tracking.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG documents_catalog  
GO  
  
CREATE FULLTEXT INDEX ON Production.Document  
    (   
    Title  
        Language 1033,   
    DocumentSummary  
        Language 1033,   
    Document   
        TYPE COLUMN FileExtension  
        Language 1033  
        Statistical_Semantics  
    )  
    KEY INDEX PK_Document_DocumentID  
        ON documents_catalog  
        WITH CHANGE_TRACKING OFF, NO POPULATION  
GO  
```  
  
 <span data-ttu-id="b32c2-144">다음과 같이 나중에 사용률이 낮은 시간에 인덱스가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-144">Later, at an off-peak time, the index is populated:</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO  
GO  
```  
  
 <span data-ttu-id="b32c2-145">**SQL Server Management Studio를 사용하여 새 의미 체계 인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="b32c2-145">**Create a new semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="b32c2-146">전체 텍스트 인덱싱 마법사를 실행하고 **테이블 열 선택** 페이지에서 의미 체계 인덱스를 만들 각 열에 대해 **통계 의미 체계** 를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-146">Run the Full-Text Indexing Wizard and enable **Statistical Semantics** on the **Select Table Columns** page for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="b32c2-147">전체 텍스트 인덱싱 마법사를 시작하는 방법을 비롯한 자세한 내용은 [전체 텍스트 인덱싱 마법사 사용](use-the-full-text-indexing-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-147">For more information, including information about how to start the Full-Text Indexing Wizard, see [Use the Full-Text Indexing Wizard](use-the-full-text-indexing-wizard.md).</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-an-existing-full-text-index"></a><a name="HowToEnableAlter"></a><span data-ttu-id="b32c2-148">방법: 기존 전체 텍스트 인덱스가 있을 때 의미 체계 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="b32c2-148">How To: Create a Semantic Index When There Is an Existing Full-Text Index</span></span>  
 <span data-ttu-id="b32c2-149">**ALTER FULLTEXT INDEX** 문을 사용하여 기존 전체 텍스트 인덱스를 변경할 때 의미 체계 인덱싱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-149">You can add semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="b32c2-150">또한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 다양한 대화 상자를 사용하여 의미 체계 인덱싱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-150">You can also add semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b32c2-151">**Transact-SQL을 사용하여 의미 체계 인덱스 추가**</span><span class="sxs-lookup"><span data-stu-id="b32c2-151">**Add a semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="b32c2-152">의미 체계 인덱스를 추가할 각 열에 대해 아래에서 설명하는 옵션을 사용하여 **ALTER FULLTEXT INDEX** 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-152">Call the **ALTER FULLTEXT INDEX** statement with the options described below for each column on which you want to add a semantic index.</span></span> <span data-ttu-id="b32c2-153">이 문의 모든 옵션에 대한 자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-153">For more information about all the options for this statement, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="b32c2-154">별도로 지정하지 않는 한 **ALTER**를 호출하면 전체 텍스트 인덱스와 의미 체계 인덱스가 모두 다시 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-154">Both full-text and semantic indexes are repopulated after a call to **ALTER**, unless you specify otherwise.</span></span>  
  
-   <span data-ttu-id="b32c2-155">열에 전체 텍스트 인덱싱만 추가하려면 **ADD** 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-155">To add full-text indexing only to a column, use the **ADD** syntax.</span></span>  
  
-   <span data-ttu-id="b32c2-156">열에 전체 텍스트 및 의미 체계 인덱싱을 모두 추가하려면 **ADD** 구문과 함께 **STATISTICAL_SEMANTICS** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-156">To add both full-text and semantic indexing to a column, use the **ADD** syntax with the **STATISTICAL_SEMANTICS** option.</span></span>  
  
-   <span data-ttu-id="b32c2-157">이미 전체 텍스트 인덱싱을 사용하도록 설정된 열에 의미 체계 인덱싱을 추가하려면 **ADD STATISTICAL_SEMANTICS** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-157">To add semantic indexing to a column that is already enabled for full-text indexing, use the **ADD STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="b32c2-158">단일 **ALTER** 문에서는 하나의 열에만 의미 체계 인덱싱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-158">You can only add semantic indexing to one column in a single **ALTER** statement.</span></span>  
  
 <span data-ttu-id="b32c2-159">**예제: 전체 텍스트 인덱싱이 이미 있는 열에 의미 체계 인덱싱 추가**</span><span class="sxs-lookup"><span data-stu-id="b32c2-159">**Example: Add semantic indexing to a column that already has full-text indexing**</span></span>  
  
 <span data-ttu-id="b32c2-160">다음 예에서는 AdventureWorks2012 예제 데이터베이스의 **Production.Document** 테이블에 대한 기존 전체 텍스트 인덱스를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-160">The following example alters an existing full-text index on **Production.Document** table in AdventureWorks2012 sample database.</span></span> <span data-ttu-id="b32c2-161">이 예에서는 전체 텍스트 인덱스가 이미 있는 **Production.Document** 테이블의 **Document** 열에 의미 체계 인덱스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-161">The example adds a semantic index on the **Document** column of the **Production.Document** table, which already has a full-text index.</span></span> <span data-ttu-id="b32c2-162">또한 자동으로 다시 채워지지 않는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-162">The example specifies that the index will not be repopulated automatically.</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document  
    ALTER COLUMN Document  
        ADD Statistical_Semantics  
    WITH NO POPULATION  
GO  
```  
  
 <span data-ttu-id="b32c2-163">**SQL Server Management Studio를 사용하여 의미 체계 인덱스 추가**</span><span class="sxs-lookup"><span data-stu-id="b32c2-163">**Add a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="b32c2-164">**전체 텍스트 인덱스 속성** 대화 상자의 **전체 텍스트 인덱스 열** 페이지에서 의미 체계 및 전체 텍스트 인덱싱을 사용하도록 설정된 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-164">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="b32c2-165">자세한 내용은 [전체 텍스트 인덱스 관리](../../database-engine/manage-full-text-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-165">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-an-existing-index"></a><a name="addreq"></a><span data-ttu-id="b32c2-166">기존 인덱스 변경에 대 한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="b32c2-166">Requirements and Restrictions for Altering an Existing Index</span></span>  
  
-   <span data-ttu-id="b32c2-167">인덱스 채우기가 진행 중인 동안에는 기존 인덱스를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-167">You cannot alter an existing index while population of the index is in progress.</span></span> <span data-ttu-id="b32c2-168">인덱스 채우기의 진행률을 모니터링하는 방법은 [의미 체계 검색 관리 및 모니터링](manage-and-monitor-semantic-search.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-168">For more information on monitoring the progress of index population, see [Manage and Monitor Semantic Search](manage-and-monitor-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="b32c2-169">**ALTER FULLTEXT INDEX** 문을 한 번 호출하는 것으로 열에 인덱싱을 추가하고 동일한 열의 인덱싱을 변경하거나 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-169">You cannot add indexing to a column, and alter or drop indexing for the same column, in a single call to the **ALTER FULLTEXT INDEX** statement.</span></span>  
  
##  <a name="dropping-a-semantic-index"></a><a name="dropping"></a><span data-ttu-id="b32c2-170">의미 체계 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="b32c2-170">Dropping a Semantic Index</span></span>  
  
###  <a name="how-to-drop-a-semantic-index"></a><a name="drophow"></a><span data-ttu-id="b32c2-171">방법: 의미 체계 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="b32c2-171">How to: Drop a Semantic Index</span></span>  
 <span data-ttu-id="b32c2-172">**ALTER FULLTEXT INDEX** 문을 사용하여 기존 전체 텍스트 인덱스를 변경할 때 의미 체계 인덱싱을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-172">You can drop semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="b32c2-173">또한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 다양한 대화 상자를 사용하여 의미 체계 인덱싱을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-173">You can also drop semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b32c2-174">**Transact-SQL을 사용하여 의미 체계 인덱스 삭제**</span><span class="sxs-lookup"><span data-stu-id="b32c2-174">**Drop a semantic index by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="b32c2-175">열에서 의미 체계 인덱싱만 삭제하려면 **ALTER COLUMN** column_name **DROP STATISTICAL_SEMANTICS***옵션을 사용하여***ALTER FULLTEXT INDEX** 문을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-175">To drop semantic indexing only from a column or columns, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="b32c2-176">단일 **ALTER** 문으로 여러 열의 인덱싱을 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-176">You can drop the indexing from multiple columns in a single **ALTER** statement.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP STATISTICAL_SEMANTICS  
    GO  
    ```  
  
-   <span data-ttu-id="b32c2-177">열에서 전체 텍스트 및 의미 체계 인덱싱을 모두 삭제 하려면 alter **column***column_name***drop** 옵션을 사용 하 여 **alter 전체 텍스트 인덱스** 문을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-177">To drop both full-text and semantic indexing from a column, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP** option.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP  
    GO  
    ```  
  
 <span data-ttu-id="b32c2-178">**SQL Server Management Studio를 사용하여 의미 체계 인덱스 삭제**</span><span class="sxs-lookup"><span data-stu-id="b32c2-178">**Drop a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="b32c2-179">**전체 텍스트 인덱스 속성** 대화 상자의 **전체 텍스트 인덱스 열** 페이지에서 의미 체계 및 전체 텍스트 인덱싱을 사용하도록 설정된 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-179">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="b32c2-180">자세한 내용은 [전체 텍스트 인덱스 관리](../../database-engine/manage-full-text-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-180">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-dropping-a-semantic-index"></a><a name="dropreq"></a><span data-ttu-id="b32c2-181">의미 체계 인덱스 삭제를 위한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="b32c2-181">Requirements and Restrictions for Dropping a Semantic Index</span></span>  
  
-   <span data-ttu-id="b32c2-182">의미 체계 인덱싱을 유지하는 동안에는 열에서 전체 텍스트 인덱싱을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-182">You cannot drop full-text indexing from a column while retaining semantic indexing.</span></span> <span data-ttu-id="b32c2-183">의미 체계 인덱싱에서는 전체 텍스트 인덱싱에 의존하여 문서 유사성 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-183">Semantic indexing depends on full-text indexing for document similarity results.</span></span>  
  
-   <span data-ttu-id="b32c2-184">테이블에서 의미 체계 인덱싱을 사용하도록 설정된 마지막 열의 의미 체계 인덱싱을 삭제할 경우 **NO POPULATION** 옵션을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-184">You cannot specify the **NO POPULATION** option when you drop semantic indexing from the last column in a table for which semantic indexing was enabled.</span></span> <span data-ttu-id="b32c2-185">이전에 인덱싱된 결과를 제거하려면 채우기 주기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-185">A population cycle is required to remove the results that were indexed previously.</span></span>  
  
## <a name="checking-whether-semantic-search-is-enabled-on-database-objects"></a><span data-ttu-id="b32c2-186">데이터베이스 개체에 의미 체계 검색이 사용하도록 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="b32c2-186">Checking Whether Semantic Search Is Enabled on Database Objects</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-enabled-on-database-objects"></a><a name="HowToCheckEnabled"></a><span data-ttu-id="b32c2-187">방법: 데이터베이스 개체에 의미 체계 검색이 사용 하도록 설정 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="b32c2-187">How To: Check Whether Semantic Search Is Enabled on Database Objects</span></span>  
 <span data-ttu-id="b32c2-188">**데이터베이스에 대해 의미 체계 검색이 사용하도록 설정되어 있는지 확인**</span><span class="sxs-lookup"><span data-stu-id="b32c2-188">**Is semantic search enabled for a database?**</span></span>  
 <span data-ttu-id="b32c2-189">[DATABASEPROPERTYEX&#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 메타데이터 함수의 **IsFullTextEnabled** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-189">Query the **IsFullTextEnabled** property of the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="b32c2-190">반환 값이 1이면 데이터베이스에 대해 전체 텍스트 검색과 의미 체계 검색이 사용하도록 설정되어 있음을 나타내고, 반환 값이 0이면 그렇지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-190">A return value of 1 indicates that full-text search and semantic search are enabled for the database; a return value of 0 indicates that they are not enabled.</span></span>  
  
```sql  
SELECT DATABASEPROPERTYEX('database_name', 'IsFullTextEnabled')  
GO  
```  
  
 <span data-ttu-id="b32c2-191">**테이블에 대해 의미 체계 검색이 사용하도록 설정되어 있는지 확인**</span><span class="sxs-lookup"><span data-stu-id="b32c2-191">**Is semantic search enabled for a table?**</span></span>  
 <span data-ttu-id="b32c2-192">[OBJECTPROPERTYEX&#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) 메타데이터 함수의 **TableFullTextSemanticExtraction** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-192">Query the **TableFullTextSemanticExtraction** property of the [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="b32c2-193">반환 값이 1이면 테이블에 대해 의미 체계 검색이 사용하도록 설정되어 있음을 나타내고, 반환 값이 0이면 그렇지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-193">A return value of 1 indicates that semantic search is enabled for the table; a return value of 0 indicates that it is not enabled.</span></span>  
  
```scr  
SELECT OBJECTPROPERTYEX(OBJECT_ID('table_name'), 'TableFullTextSemanticExtraction')  
GO  
```  
  
 <span data-ttu-id="b32c2-194">**열에 대해 의미 체계 검색이 사용하도록 설정되어 있는지 확인**</span><span class="sxs-lookup"><span data-stu-id="b32c2-194">**Is semantic search enabled for a column?**</span></span>  
 <span data-ttu-id="b32c2-195">특정 열에 대해 의미 체계 검색이 사용하도록 설정되어 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="b32c2-195">To determine whether semantic search is enabled for a specific column:</span></span>  
  
-   <span data-ttu-id="b32c2-196">[COLUMNPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) 메타데이터 함수의 **StatisticalSemantics** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-196">Query the **StatisticalSemantics** property of the [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) metadata function.</span></span>  
  
     <span data-ttu-id="b32c2-197">반환 값이 1이면 열에 대해 의미 체계 검색이 사용하도록 설정되어 있음을 나타내고, 반환 값이 0이면 그렇지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-197">A return value of 1 indicates that semantic search is enabled for the column; a return value of 0 indicates that it is not enabled.</span></span>  
  
    ```sql  
    SELECT COLUMNPROPERTY(OBJECT_ID('table_name'), 'column_name', 'StatisticalSemantics')  
    GO  
    ```  
  
-   <span data-ttu-id="b32c2-198">전체 텍스트 인덱스에 대한 카탈로그 뷰 [sys.fulltext_index_columns&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-198">Query the catalog view [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) for the full-text index.</span></span>  
  
     <span data-ttu-id="b32c2-199">**statistical_semantics** 열의 값이 1이면 지정된 열에 전체 텍스트 인덱싱과 의미 체계 인덱싱이 사용하도록 설정되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-199">A value of 1 in the **statistical_semantics** column indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
    ```sql  
    SELECT * FROM sys.fulltext_index_columns WHERE object_id = OBJECT_ID('table_name')  
    GO  
    ```  
  
-   <span data-ttu-id="b32c2-200">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 개체 탐색기에서 열을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-200">In Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click on a column and select **Properties**.</span></span> <span data-ttu-id="b32c2-201">**열 속성** 대화 상자의 **일반** 페이지에서 **통계 의미 체계** 속성 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-201">On the **General** page of the **Column Properties** dialog box, check the value of the **Statistical Semantics** property.</span></span>  
  
     <span data-ttu-id="b32c2-202">값이 True이면 지정된 열에 전체 텍스트 인덱싱과 의미 체계 인덱싱이 사용하도록 설정되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-202">A value of True indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
## <a name="determining-what-can-be-indexed-for-semantic-search"></a><span data-ttu-id="b32c2-203">의미 체계 검색을 위해 인덱싱할 수 있는 항목 결정</span><span class="sxs-lookup"><span data-stu-id="b32c2-203">Determining What Can Be Indexed for Semantic Search</span></span>  
  
###  <a name="how-to-check-which-languages-are-supported-for-semantic-search"></a><a name="HowToCheckLanguages"></a><span data-ttu-id="b32c2-204">방법: 의미 체계 검색에 지원 되는 언어 확인</span><span class="sxs-lookup"><span data-stu-id="b32c2-204">How To: Check Which Languages Are Supported for Semantic Search</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b32c2-205">의미 체계 인덱싱에 지원되는 언어는 전체 텍스트 인덱싱에 지원되는 언어보다 적습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-205">Fewer languages are supported for semantic indexing than for full-text indexing.</span></span> <span data-ttu-id="b32c2-206">따라서 전체 텍스트 검색을 위해 인덱싱할 수 있지만 의미 체계 검색을 위해서는 인덱싱할 수 없는 열이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-206">As a result, there may be columns that you can index for full-text search, but not for semantic search.</span></span>  
  
 <span data-ttu-id="b32c2-207">카탈로그 뷰 [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-207">Query the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.fulltext_semantic_languages  
GO  
```  
  
 <span data-ttu-id="b32c2-208">의미 체계 인덱싱에 지원되는 언어는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-208">The following languages are supported for semantic indexing.</span></span> <span data-ttu-id="b32c2-209">이 목록은 LCID로 정렬된 카탈로그 뷰 [sys.fulltext_semantic_languages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)의 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-209">This list represents the output of the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql), ordered by LCID.</span></span>  
  
|<span data-ttu-id="b32c2-210">Language</span><span class="sxs-lookup"><span data-stu-id="b32c2-210">Language</span></span>|<span data-ttu-id="b32c2-211">LCID</span><span class="sxs-lookup"><span data-stu-id="b32c2-211">LCID</span></span>|  
|--------------|----------|  
|<span data-ttu-id="b32c2-212">독일어</span><span class="sxs-lookup"><span data-stu-id="b32c2-212">German</span></span>|<span data-ttu-id="b32c2-213">1031</span><span class="sxs-lookup"><span data-stu-id="b32c2-213">1031</span></span>|  
|<span data-ttu-id="b32c2-214">영어(미국)</span><span class="sxs-lookup"><span data-stu-id="b32c2-214">English (US)</span></span>|<span data-ttu-id="b32c2-215">1033</span><span class="sxs-lookup"><span data-stu-id="b32c2-215">1033</span></span>|  
|<span data-ttu-id="b32c2-216">프랑스어</span><span class="sxs-lookup"><span data-stu-id="b32c2-216">French</span></span>|<span data-ttu-id="b32c2-217">1036</span><span class="sxs-lookup"><span data-stu-id="b32c2-217">1036</span></span>|  
|<span data-ttu-id="b32c2-218">이탈리아어</span><span class="sxs-lookup"><span data-stu-id="b32c2-218">Italian</span></span>|<span data-ttu-id="b32c2-219">1040</span><span class="sxs-lookup"><span data-stu-id="b32c2-219">1040</span></span>|  
|<span data-ttu-id="b32c2-220">포르투갈어(브라질)</span><span class="sxs-lookup"><span data-stu-id="b32c2-220">Portuguese (Brazil)</span></span>|<span data-ttu-id="b32c2-221">1046</span><span class="sxs-lookup"><span data-stu-id="b32c2-221">1046</span></span>|  
|<span data-ttu-id="b32c2-222">러시아어</span><span class="sxs-lookup"><span data-stu-id="b32c2-222">Russian</span></span>|<span data-ttu-id="b32c2-223">1049</span><span class="sxs-lookup"><span data-stu-id="b32c2-223">1049</span></span>|  
|<span data-ttu-id="b32c2-224">스웨덴어</span><span class="sxs-lookup"><span data-stu-id="b32c2-224">Swedish</span></span>|<span data-ttu-id="b32c2-225">1053</span><span class="sxs-lookup"><span data-stu-id="b32c2-225">1053</span></span>|  
|<span data-ttu-id="b32c2-226">영어(영국)</span><span class="sxs-lookup"><span data-stu-id="b32c2-226">English (UK)</span></span>|<span data-ttu-id="b32c2-227">2057</span><span class="sxs-lookup"><span data-stu-id="b32c2-227">2057</span></span>|  
|<span data-ttu-id="b32c2-228">포르투갈어(포르투갈)</span><span class="sxs-lookup"><span data-stu-id="b32c2-228">Portuguese (Portugal)</span></span>|<span data-ttu-id="b32c2-229">2070</span><span class="sxs-lookup"><span data-stu-id="b32c2-229">2070</span></span>|  
|<span data-ttu-id="b32c2-230">스페인어</span><span class="sxs-lookup"><span data-stu-id="b32c2-230">Spanish</span></span>|<span data-ttu-id="b32c2-231">3082</span><span class="sxs-lookup"><span data-stu-id="b32c2-231">3082</span></span>|  
  
###  <a name="how-to-determine-which-document-types-can-be-indexed"></a><a name="doctypes"></a><span data-ttu-id="b32c2-232">방법: 인덱싱할 수 있는 문서 유형 결정</span><span class="sxs-lookup"><span data-stu-id="b32c2-232">How To: Determine Which Document Types Can Be Indexed</span></span>  
 <span data-ttu-id="b32c2-233">카탈로그 뷰 [sys.fulltext_document_types&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-233">Query the catalog view [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).</span></span>  
  
 <span data-ttu-id="b32c2-234">인덱싱할 문서 형식이 지원되는 형식 목록에 없는 경우 추가 필터를 찾은 다음 다운로드하여 설치해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-234">If the document type that you want to index is not in the list of supported types, then you may have to locate, download, and install additional filters.</span></span> <span data-ttu-id="b32c2-235">자세한 내용은 [등록된 필터와 단어 분리기 보기 및 변경](view-or-change-registered-filters-and-word-breakers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32c2-235">For more information, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
##  <a name="best-practice-consider-creating-a-separate-filegroup-for-the-full-text-and-semantic-indexes"></a><a name="BestPracticeFilegroup"></a><span data-ttu-id="b32c2-236">모범 사례: 전체 텍스트 및 의미 체계 인덱스에 대 한 별도의 파일 그룹을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-236">Best Practice: Consider Creating a Separate Filegroup for the Full-Text and Semantic Indexes</span></span>  
 <span data-ttu-id="b32c2-237">디스크 공간 할당이 중요한 경우 전체 텍스트 및 의미 체계 인덱스에 대한 별도의 파일 그룹을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-237">Consider creating a separate filegroup for the full-text and semantic indexes if disk space allocation is a concern.</span></span> <span data-ttu-id="b32c2-238">의미 체계 인덱스는 전체 텍스트 인덱스와 동일한 파일 그룹에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-238">The semantic indexes are created in the same filegroup as the full-text index.</span></span> <span data-ttu-id="b32c2-239">완전히 채워진 의미 체계 인덱스에는 많은 양의 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-239">A fully populated semantic index may contain large amount of data.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-searching-on-specific-column-returns-no-results"></a><a name="IssueNoResults"></a><span data-ttu-id="b32c2-240">문제: 특정 열에 대해 검색할 때 결과가 반환 되지 않음</span><span class="sxs-lookup"><span data-stu-id="b32c2-240">Problem: Searching on Specific Column Returns No Results</span></span>  
 <span data-ttu-id="b32c2-241">**유니코드 언어에 대해 비유니코드 LCID가 지정되었습니까?**</span><span class="sxs-lookup"><span data-stu-id="b32c2-241">**Was a non-Unicode LCID specified for a Unicode language?**</span></span>  
 <span data-ttu-id="b32c2-242">비유니코드 열에 대해 의미 체계 인덱싱을 사용하도록 설정할 때 러시아어의 LCID 1049와 같이 유니코드 단어만 있는 언어의 LCID를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-242">It is possible to enable semantic indexing on a non-Unicode column type with an LCID for a language that only has Unicode words, such as LCID 1049 for Russian.</span></span> <span data-ttu-id="b32c2-243">그러나 이 경우에는 이 열에 대한 의미 체계 인덱스에서 결과가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b32c2-243">In this case, no results will ever be returned from the semantic indexes on this column.</span></span>  
  
  
