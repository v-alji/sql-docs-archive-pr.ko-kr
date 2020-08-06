---
title: 전체 텍스트 검색 DDL, 함수, 저장 프로시저 및 뷰 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 98c36715-4195-482e-a4a3-d93ff65b75f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29b026ac60fd3f7d00ca519c4ced84533ce9740f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659913"
---
# <a name="full-text-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="f1228-102">전체 텍스트 검색 DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="f1228-102">Full-Text Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="f1228-103">속성 검색 기능을 포함하여 전체 텍스트 검색을 지원하는 Transact-SQL 문 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f1228-103">Lists the Transact-SQL statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that support full-text search, including the property search feature.</span></span>  
  
 <span data-ttu-id="f1228-104">사용되지 않는 개체는 이 목록에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1228-104">This list does not include deprecated objects.</span></span>  
  
 <span data-ttu-id="f1228-105">의미 체계 검색을 지원하는 데이터베이스 개체 목록은 [Semantic Search DDL, Functions, Stored Procedures, and Views](../views/views.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1228-105">For the list of database objects that support semantic search, see [Semantic Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="f1228-106">Transact-SQL DDL(데이터 정의 언어) 문</span><span class="sxs-lookup"><span data-stu-id="f1228-106">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
-   [<span data-ttu-id="f1228-107">CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-107">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="f1228-108">CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-108">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="f1228-109">CREATE FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-109">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="f1228-110">CREATE SEARCH PROPERTY LIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-110">CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-search-property-list-transact-sql)  
  
-   [<span data-ttu-id="f1228-111">ALTER FULLTEXT CATALOG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-111">ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="f1228-112">ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-112">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="f1228-113">ALTER FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-113">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="f1228-114">ALTER SEARCH PROPERTY LIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-114">ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-search-property-list-transact-sql)  
  
-   [<span data-ttu-id="f1228-115">"DROP FULLTEXT CATALOG&#40;Transact-SQL&#41;"</span><span class="sxs-lookup"><span data-stu-id="f1228-115">DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="f1228-116">DROP FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-116">DROP FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="f1228-117">DROP FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-117">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
-   [<span data-ttu-id="f1228-118">DROP SEARCH PROPERTY LIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-118">DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-search-property-list-transact-sql)  
  
##  <a name="system-predicates-and-functions"></a><a name="func"></a> <span data-ttu-id="f1228-119">시스템 조건자 및 함수</span><span class="sxs-lookup"><span data-stu-id="f1228-119">System Predicates and Functions</span></span>  
  
-   [<span data-ttu-id="f1228-120">CONTAINS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-120">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
-   [<span data-ttu-id="f1228-121">CONTAINSTABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-121">CONTAINSTABLE &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)  
  
-   [<span data-ttu-id="f1228-122">FREETEXT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-122">FREETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/freetext-transact-sql)  
  
-   [<span data-ttu-id="f1228-123">FREETEXTTABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-123">FREETEXTTABLE &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/freetexttable-transact-sql)  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="f1228-124">시스템 메타데이터 함수</span><span class="sxs-lookup"><span data-stu-id="f1228-124">System Metadata Functions</span></span>  
  
-   [<span data-ttu-id="f1228-125">COLUMNPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-125">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)  
  
-   [<span data-ttu-id="f1228-126">FULLTEXTCATALOGPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-126">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)  
  
-   [<span data-ttu-id="f1228-127">FULLTEXTSERVICEPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-127">FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)  
  
-   [<span data-ttu-id="f1228-128">INDEXPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-128">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)  
  
-   [<span data-ttu-id="f1228-129">OBJECTPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-129">OBJECTPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectpropertyex-transact-sql)  
  
-   [<span data-ttu-id="f1228-130">OBJECTPROPERTYEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-130">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
-   [<span data-ttu-id="f1228-131">SERVERPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> <span data-ttu-id="f1228-132">시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="f1228-132">System Stored Procedures</span></span>  
  
-   [<span data-ttu-id="f1228-133">sp_fulltext_keymappings&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-133">sp_fulltext_keymappings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql)  
  
-   [<span data-ttu-id="f1228-134">sp_fulltext_load_thesaurus_file&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-134">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
-   [<span data-ttu-id="f1228-135">sp_fulltext_pendingchanges&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-135">sp_fulltext_pendingchanges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql)  
  
-   [<span data-ttu-id="f1228-136">sp_fulltext_service&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-136">sp_fulltext_service &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)  
  
-   [<span data-ttu-id="f1228-137">sp_help_fulltext_system_components&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-137">sp_help_fulltext_system_components &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> <span data-ttu-id="f1228-138">시스템 뷰 - 카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="f1228-138">System Views - Catalog Views</span></span>  
  
-   [<span data-ttu-id="f1228-139">sys.fulltext_catalogs&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-139">sys.fulltext_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)  
  
-   [<span data-ttu-id="f1228-140">sys.fulltext_document_types&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-140">sys.fulltext_document_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)  
  
-   [<span data-ttu-id="f1228-141">sys.fulltext_index_catalog_usages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-141">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)  
  
-   [<span data-ttu-id="f1228-142">sys.fulltext_index_columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-142">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
-   [<span data-ttu-id="f1228-143">sys.fulltext_index_fragments&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-143">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)  
  
-   [<span data-ttu-id="f1228-144">sys.fulltext_indexes&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-144">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)  
  
-   [<span data-ttu-id="f1228-145">sys.fulltext_languages&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-145">sys.fulltext_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)  
  
-   [<span data-ttu-id="f1228-146">sys.fulltext_stoplists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-146">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="f1228-147">sys.fulltext_stopwords&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-147">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
-   [<span data-ttu-id="f1228-148">sys.fulltext_system_stopwords&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-148">sys.fulltext_system_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql)  
  
-   [<span data-ttu-id="f1228-149">sys.registered_search_properties&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-149">sys.registered_search_properties &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql)  
  
-   [<span data-ttu-id="f1228-150">sys.registered_search_property_lists&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-150">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="f1228-151">시스템 뷰 - 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="f1228-151">System Views - Dynamic Management Views</span></span>  
  
-   [<span data-ttu-id="f1228-152">sys.dm_fts_active_catalogs&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-152">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
-   [<span data-ttu-id="f1228-153">sys.dm_fts_fdhosts&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-153">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
-   [<span data-ttu-id="f1228-154">sys.dm_fts_index_keywords&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-154">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)  
  
-   [<span data-ttu-id="f1228-155">sys.dm_fts_index_keywords_by_document&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-155">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)  
  
-   [<span data-ttu-id="f1228-156">sys.dm_fts_index_keywords_by_property&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-156">sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql)  
  
-   [<span data-ttu-id="f1228-157">sys.dm_fts_index_population&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
-   [<span data-ttu-id="f1228-158">sys.dm_fts_memory_buffers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-158">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
-   [<span data-ttu-id="f1228-159">sys.dm_fts_memory_pools&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-159">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
-   [<span data-ttu-id="f1228-160">sys.dm_fts_outstanding_batches&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-160">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
-   [<span data-ttu-id="f1228-161">sys.dm_fts_parser&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-161">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
-   [<span data-ttu-id="f1228-162">sys.dm_fts_population_ranges&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1228-162">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
