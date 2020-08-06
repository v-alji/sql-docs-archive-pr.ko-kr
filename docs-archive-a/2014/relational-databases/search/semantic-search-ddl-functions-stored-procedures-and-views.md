---
title: 의미 체계 검색 DDL, 함수, 저장 프로시저 및 뷰 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce6c23f9a8ff1d0dac8986bf6b44c7725d4badc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735183"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="af9c7-102">의미 체계 검색 DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="af9c7-102">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="af9c7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 통계 의미 체계 검색을 지원하는 Transact-SQL 문 및 데이터베이스 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="af9c7-103">Lists the Transact-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="af9c7-104">전체 텍스트 검색을 지원하는 문과 데이터베이스 개체의 목록은 [전체 텍스트 검색 DDL, 함수, 저장 프로시저 및 뷰](../views/views.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af9c7-104">For the list of statements and database objects that support full-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="af9c7-105">Transact-SQL DDL(데이터 정의 언어) 문</span><span class="sxs-lookup"><span data-stu-id="af9c7-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
|<span data-ttu-id="af9c7-106">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-106">Object</span></span>|<span data-ttu-id="af9c7-107">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-107">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-108">ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[<span data-ttu-id="af9c7-109">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="af9c7-109">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="af9c7-110">CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[<span data-ttu-id="af9c7-111">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="af9c7-111">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="af9c7-112">시스템 함수</span><span class="sxs-lookup"><span data-stu-id="af9c7-112">System Functions</span></span>  
  
|<span data-ttu-id="af9c7-113">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-113">Object</span></span>|<span data-ttu-id="af9c7-114">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-114">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-115">semantickeyphrasetable&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[<span data-ttu-id="af9c7-116">의미 체계 검색을 사용하여 문서에서 키 구 찾기</span><span class="sxs-lookup"><span data-stu-id="af9c7-116">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)|  
|[<span data-ttu-id="af9c7-117">semanticsimilaritydetailstable&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[<span data-ttu-id="af9c7-118">의미 체계 검색을 사용하여 유사하거나 관련된 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="af9c7-118">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
|[<span data-ttu-id="af9c7-119">semanticsimilaritytable&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[<span data-ttu-id="af9c7-120">의미 체계 검색을 사용하여 유사하거나 관련된 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="af9c7-120">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="af9c7-121">시스템 메타데이터 함수</span><span class="sxs-lookup"><span data-stu-id="af9c7-121">System Metadata Functions</span></span>  
  
|<span data-ttu-id="af9c7-122">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-122">Object</span></span>|<span data-ttu-id="af9c7-123">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-123">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-124">COLUMNPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|[<span data-ttu-id="af9c7-125">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="af9c7-125">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="af9c7-126">DATABASEPROPERTYEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/databasepropertyex-transact-sql)|[<span data-ttu-id="af9c7-127">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="af9c7-127">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="af9c7-128">FULLTEXTCATALOGPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[<span data-ttu-id="af9c7-129">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-129">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="af9c7-130">INDEXPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|[<span data-ttu-id="af9c7-131">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-131">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="af9c7-132">OBJECTPROPERTYEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|[<span data-ttu-id="af9c7-133">테이블 및 열에 대한 의미 체계 검색 사용</span><span class="sxs-lookup"><span data-stu-id="af9c7-133">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="af9c7-134">SERVERPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|[<span data-ttu-id="af9c7-135">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="af9c7-135">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-stored-procedures"></a><a name="sproc"></a> <span data-ttu-id="af9c7-136">시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="af9c7-136">System Stored Procedures</span></span>  
  
|<span data-ttu-id="af9c7-137">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-137">Object</span></span>|<span data-ttu-id="af9c7-138">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-138">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-139">sp_fulltext_semantic_register_language_statistics_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[<span data-ttu-id="af9c7-140">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="af9c7-140">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="af9c7-141">sp_fulltext_semantic_unregister_language_statistics_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[<span data-ttu-id="af9c7-142">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="af9c7-142">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---catalog-views"></a><a name="cv"></a> <span data-ttu-id="af9c7-143">시스템 뷰 - 카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="af9c7-143">System Views - Catalog Views</span></span>  
  
|<span data-ttu-id="af9c7-144">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-144">Object</span></span>|<span data-ttu-id="af9c7-145">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-145">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-146">sys.fulltext_index_columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[<span data-ttu-id="af9c7-147">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-147">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="af9c7-148">sys.fulltext_semantic_language_statistics_database&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[<span data-ttu-id="af9c7-149">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="af9c7-149">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="af9c7-150">sys.fulltext_semantic_languages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[<span data-ttu-id="af9c7-151">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="af9c7-151">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="af9c7-152">시스템 뷰 - 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="af9c7-152">System Views - Dynamic Management Views</span></span>  
  
|<span data-ttu-id="af9c7-153">Object</span><span class="sxs-lookup"><span data-stu-id="af9c7-153">Object</span></span>|<span data-ttu-id="af9c7-154">추가 정보</span><span class="sxs-lookup"><span data-stu-id="af9c7-154">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="af9c7-155">sys.dm_db_fts_index_physical_stats&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[<span data-ttu-id="af9c7-156">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-156">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="af9c7-157">sys.dm_fts_index_population&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[<span data-ttu-id="af9c7-158">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-158">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="af9c7-159">sys.dm_fts_semantic_similarity_population&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af9c7-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[<span data-ttu-id="af9c7-160">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-160">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a><span data-ttu-id="af9c7-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af9c7-161">See Also</span></span>  
 [<span data-ttu-id="af9c7-162">의미 체계 검색 관리 및 모니터링</span><span class="sxs-lookup"><span data-stu-id="af9c7-162">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
  
  
