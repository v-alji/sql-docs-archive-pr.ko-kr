---
title: 전체 텍스트 인덱스 속성 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
ms.openlocfilehash: 61b9f2948df138c39230cf6f5787c395a364c695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661307"
---
# <a name="full-text-index-properties-general-page"></a><span data-ttu-id="5cd5a-102">전체 텍스트 인덱스 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="5cd5a-102">Full-Text Index Properties (General Page)</span></span>
  <span data-ttu-id="5cd5a-103">**전체 텍스트 인덱스의 수정 가능한 속성을 보거나 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-103">**To view or change the modifiable properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="5cd5a-104">전체 텍스트 인덱스 관리</span><span class="sxs-lookup"><span data-stu-id="5cd5a-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="5cd5a-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="5cd5a-105">UI element list</span></span>  
 <span data-ttu-id="5cd5a-106">**전체 텍스트 카탈로그**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-106">**Full-Text Catalog**</span></span>  
 <span data-ttu-id="5cd5a-107">전체 텍스트 인덱스와 연결된 전체 텍스트 카탈로그의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-107">Displays the name of the full-text catalog with which the full-text index is associated.</span></span>  
  
 <span data-ttu-id="5cd5a-108">**Database**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-108">**Database**</span></span>  
 <span data-ttu-id="5cd5a-109">전체 텍스트 인덱스가 있는 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-109">Displays the name of the database in which the full-text index resides.</span></span>  
  
 <span data-ttu-id="5cd5a-110">**테이블**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-110">**Table**</span></span>  
 <span data-ttu-id="5cd5a-111">전체 텍스트 인덱스가 정의된 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-111">Displays the name of the table on which the full-text index is defined.</span></span>  
  
 <span data-ttu-id="5cd5a-112">**전체 텍스트 인덱스 키**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-112">**Full-Text Index Key**</span></span>  
 <span data-ttu-id="5cd5a-113">테이블의 단일 열에 대한 고유 인덱스인 전체 텍스트 인덱스 키의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-113">Displays the name of the full-text index key, which is a unique index on a single column of the table.</span></span>  
  
 <span data-ttu-id="5cd5a-114">**테이블 전체 텍스트 채우기 상태**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-114">**Table Full-Text Populate Status**</span></span>  
 <span data-ttu-id="5cd5a-115">전체 텍스트 인덱싱된 테이블의 채우기 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-115">Displays the population status of the full-text indexed table.</span></span>  
  
 <span data-ttu-id="5cd5a-116">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-116">The possible values are as follows:</span></span>  
  
 <span data-ttu-id="5cd5a-117">0 = 유휴 상태</span><span class="sxs-lookup"><span data-stu-id="5cd5a-117">0 = Idle.</span></span>  
  
 <span data-ttu-id="5cd5a-118">1 = 전체 채우기가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-118">1 = Full population is in progress.</span></span>  
  
 <span data-ttu-id="5cd5a-119">2 = 증분 채우기가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-119">2 = Incremental population is in progress.</span></span>  
  
 <span data-ttu-id="5cd5a-120">3 = 추적된 변경 내용의 전파가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-120">3 = Propagation of tracked changes is in progress.</span></span>  
  
 <span data-ttu-id="5cd5a-121">4 = 변경 내용 자동 추적과 같은 백그라운드 업데이트 인덱스가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-121">4 = Background update index is in progress, such as automatic change tracking.</span></span>  
  
 <span data-ttu-id="5cd5a-122">5 = 전체 텍스트 인덱싱이 정체 또는 일시 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-122">5 = Full-text indexing is throttled or paused.</span></span>  
  
 <span data-ttu-id="5cd5a-123">**활성 전체 텍스트 인덱스**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-123">**Active Full-Text Index**</span></span>  
 <span data-ttu-id="5cd5a-124">테이블에 활성 전체 텍스트 인덱스가 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-124">Indicates whether the table has an active full-text index.</span></span>  
  
 <span data-ttu-id="5cd5a-125">1 = True</span><span class="sxs-lookup"><span data-stu-id="5cd5a-125">1 = True</span></span>  
  
 <span data-ttu-id="5cd5a-126">0 = False</span><span class="sxs-lookup"><span data-stu-id="5cd5a-126">0 = False</span></span>  
  
 <span data-ttu-id="5cd5a-127">**전체 텍스트 인덱스 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-127">**Full-Text Index Filegroup**</span></span>  
 <span data-ttu-id="5cd5a-128">전체 텍스트 인덱스가 속하는 파일 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-128">The filegroup to which the full-text index belongs.</span></span>  
  
 <span data-ttu-id="5cd5a-129">**전체 텍스트 인덱스 중지 목록**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-129">**Full-Text Index Stoplist**</span></span>  
 <span data-ttu-id="5cd5a-130">전체 텍스트 인덱스에 현재 연결되어 있는 중지 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-130">The stoplist that is currently associated with the full-text index.</span></span> <span data-ttu-id="5cd5a-131">중지 목록은 [중지 단어](../relational-databases/search/full-text-search.md)의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-131">A stoplist is a list of [stopwords](../relational-databases/search/full-text-search.md).</span></span> <span data-ttu-id="5cd5a-132">전체 텍스트 인덱스에 연결된 중지 목록이 있으면 해당 인덱스에 대한 전체 텍스트 쿼리에 중지 목록이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-132">The stoplist associated with a full-text index, if any, is applied to full-text queries on that index.</span></span> <span data-ttu-id="5cd5a-133">목록에서 선택 하 여 인덱스에서 중지 목록을 제거 **\<OFF>** 하거나 다른 중지 목록을 선택할 수 있습니다. **\<SYSTEM>** 는 시스템 중지 목록을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-133">You can remove the stoplist from the index by selecting **\<OFF>** from the list, or you can select a different stoplist; **\<SYSTEM>** indicates the system stoplist.</span></span>  
  
 <span data-ttu-id="5cd5a-134">**중지 목록을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-134">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="5cd5a-135">전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="5cd5a-135">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
 <span data-ttu-id="5cd5a-136">**검색 속성 목록**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-136">**Search Property List**</span></span>  
 <span data-ttu-id="5cd5a-137">현재 전체 텍스트 인덱스와 연결된 검색 속성 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-137">The search property list that is currently associated with the full-text index, if any.</span></span> <span data-ttu-id="5cd5a-138">검색 속성 목록은 연결된 전체 텍스트 인덱스가 채워질 때 해당 인덱스에 포함되는 문서 속성 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-138">A search property list specifies a set of document properties that are included in the associated full-text index when it is populated.</span></span> <span data-ttu-id="5cd5a-139">자세한 내용은 [검색 속성 목록을 사용하여 문서 속성 검색](../relational-databases/search/search-document-properties-with-search-property-lists.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-139">For more information, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="5cd5a-140">**\<Off>** 현재 인덱스와 연결 된 검색 속성 목록이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-140">**\<Off>** indicates that there is currently no search property list associated with the index.</span></span> <span data-ttu-id="5cd5a-141">목록에서 선택 하 여 인덱스에서 현재 검색 속성 목록을 제거 **\<Off>** 하거나 목록에서 다른 검색 속성 목록을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-141">You can remove the current search property list from the index by selecting **\<Off>** from the list, or you can select a different search property list from the list.</span></span> <span data-ttu-id="5cd5a-142">현재 데이터베이스의 검색 속성 목록만 여기에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-142">Only search property lists in the current database are listed here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5cd5a-143">지정한 검색 속성 목록을 같은 데이터베이스에 있는 둘 이상의 전체 텍스트 인덱스와 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-143">You can associate a given search property list with more than one full-text index in the same database.</span></span>  
  
 <span data-ttu-id="5cd5a-144">**검색 속성 목록을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-144">**To create a search property list**</span></span>  
  
-   [<span data-ttu-id="5cd5a-145">검색 속성 목록을 사용하여 문서 속성 검색</span><span class="sxs-lookup"><span data-stu-id="5cd5a-145">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 <span data-ttu-id="5cd5a-146">**테이블 전체 텍스트 항목 수**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-146">**Table Full-Text Item Count**</span></span>  
 <span data-ttu-id="5cd5a-147">전체 텍스트 인덱싱 작업이 성공적으로 완료된 행의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-147">Indicates the number of rows that were full-text indexed successfully.</span></span>  
  
 <span data-ttu-id="5cd5a-148">이 속성은 OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] 함수에서 반환하는 `TableFulltextItemCount` 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-148">This property corresponds to the `TableFulltextItemCount` property returned by the OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="5cd5a-149">**테이블 전체 텍스트 처리된 문서**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-149">**Table Full-Text Docs Processed**</span></span>  
 <span data-ttu-id="5cd5a-150">전체 텍스트 인덱싱이 시작된 이후에 처리된 행의 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-150">Displays the number of rows that have been processed since the start of full-text indexing.</span></span> <span data-ttu-id="5cd5a-151">전체 텍스트 검색을 위해 인덱싱 중인 테이블에서 한 행의 모든 열은 인덱싱할 한 문서의 일부로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-151">In a table that is being indexed for full-text search, all the columns of one row are considered as part of one document to be indexed.</span></span> <span data-ttu-id="5cd5a-152">삭제된 행은 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-152">Deleted rows are not counted.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cd5a-153">0</span><span class="sxs-lookup"><span data-stu-id="5cd5a-153">0</span></span>|<span data-ttu-id="5cd5a-154">전체 텍스트 인덱싱이 완료되었고 활성 채우기가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-154">Indicates that full-text indexing is completed and there is no active population.</span></span>|  
|<span data-ttu-id="5cd5a-155">> 0</span><span class="sxs-lookup"><span data-stu-id="5cd5a-155">> 0</span></span>|<span data-ttu-id="5cd5a-156">활성 채우기에서 채우기, 백그라운드 업데이트 인덱스 채우기가 지정된 변경 내용 추적(예: 변경 내용 자동 추적) 설정, 전체 텍스트 인덱스 스키마 변경, 전체 텍스트 카탈로그 다시 작성, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스 다시 시작 등의 작업이 수행된 이후에 삽입 또는 업데이트 작업에 의해 처리된 문서 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-156">For an active population, indicates the number of documents processed by insert or update operations since any of the following: a population, enabling of change tracking with background update index population (such as auto change tracking), changing the full-text index schema, rebuilding the full-text catalog, restarting the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and so forth.</span></span>|  
  
 <span data-ttu-id="5cd5a-157">**테이블 전체 텍스트 보류 중인 변경 내용**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-157">**Table Full-Text Pending Changes**</span></span>  
 <span data-ttu-id="5cd5a-158">처리할 보류 중인 변경 내용 추적 항목의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-158">Number of pending change tracking entries to process.</span></span>  
  
 <span data-ttu-id="5cd5a-159">0 = 변경 내용 추적이 활성화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-159">0 = change tracking is not enabled.</span></span>  
  
 <span data-ttu-id="5cd5a-160">NULL = 테이블에 전체 텍스트 인덱스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-160">NULL = Table does not have a full-text index.</span></span>  
  
 <span data-ttu-id="5cd5a-161">**테이블 전체 텍스트 실패 횟수**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-161">**Table Full-Text Fail Count**</span></span>  
 <span data-ttu-id="5cd5a-162">전체 텍스트 검색이 인덱싱되지 않은 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-162">The number of rows that full-text search did not index.</span></span>  
  
 <span data-ttu-id="5cd5a-163">0 = 채우기가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-163">0 = The population has completed.</span></span>  
  
 <span data-ttu-id="5cd5a-164">\>0 = 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-164">\>0 = One of the following:</span></span>  
  
-   <span data-ttu-id="5cd5a-165">전체, 증분 및 수동 변경 내용 추적 채우기가 시작된 이후에 인덱싱되지 않은 문서의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-165">The number of documents that were not indexed since the start of full, incremental, or manual change tracking population.</span></span>  
  
-   <span data-ttu-id="5cd5a-166">백그라운드 업데이트 인덱스가 지정된 변경 내용 추적에서 채우기가 시작 또는 다시 시작된 이후에 인덱싱되지 않은 행의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-166">For change tracking with background update index, the number of rows that were not indexed since the start of the population, or the restart of the population.</span></span> <span data-ttu-id="5cd5a-167">이러한 결과는 스키마 변경, 카탈로그 다시 작성, 서버 다시 시작 등으로 인해 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-167">This could be caused by a schema change, rebuild of the catalog, server restart, and so on</span></span>  
  
 <span data-ttu-id="5cd5a-168">**전체 텍스트 인덱싱 설정**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-168">**Full-Text Indexing Enabled**</span></span>  
 <span data-ttu-id="5cd5a-169">전체 텍스트 인덱싱을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-169">Specifies whether full-text indexing is enabled.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cd5a-170">**True**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-170">**True**</span></span>|<span data-ttu-id="5cd5a-171">사용</span><span class="sxs-lookup"><span data-stu-id="5cd5a-171">Enabled</span></span>|  
|<span data-ttu-id="5cd5a-172">**False**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-172">**False**</span></span>|<span data-ttu-id="5cd5a-173">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="5cd5a-173">Disabled</span></span>|  
  
 <span data-ttu-id="5cd5a-174">**변경 내용 추적**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-174">**Change Tracking**</span></span>  
 <span data-ttu-id="5cd5a-175">테이블에서 전체 텍스트 변경 내용 추적을 사용할지 여부를 지정하고, 사용할 경우 종류를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-175">Specifies whether the table has full-text change-tracking enabled, and if so, what kind.</span></span> <span data-ttu-id="5cd5a-176">전체 텍스트 변경 내용 추적은 전체 텍스트 인덱싱이 설정된 테이블과 인덱싱된 뷰에서 수정된 행의 레코드를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-176">Full-text change tracking maintains a record of the rows that have been modified in a table or indexed view that has been set up for full-text indexing.</span></span> <span data-ttu-id="5cd5a-177">이러한 변경 내용은 전체 텍스트 인덱스로 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-177">These changes can be propagated to the full-text index.</span></span>  
  
 <span data-ttu-id="5cd5a-178">**변경 내용 추적** 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-178">The **Change Tracking** values are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cd5a-179">해제</span><span class="sxs-lookup"><span data-stu-id="5cd5a-179">**Off**</span></span>|<span data-ttu-id="5cd5a-180">기본 데이터의 변경 내용으로 전체 텍스트 인덱스가 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-180">The full-text index is not updated with changes to the underlying data.</span></span>|  
|<span data-ttu-id="5cd5a-181">**수동**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-181">**Manual**</span></span>|<span data-ttu-id="5cd5a-182">기본 데이터가 변경될 때 전체 텍스트 인덱스가 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-182">The full-text index is not updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="5cd5a-183">그러나 기본 데이터의 변경 내용은 그대로 유지되므로</span><span class="sxs-lookup"><span data-stu-id="5cd5a-183">However, changes to the underlying data are maintained, and you can propagate them to the .</span></span> <span data-ttu-id="5cd5a-184">SQL Server 에이전트를 사용하여 일정에 따라 또는 수동으로 그러한 변경 내용을 전체 텍스트 인덱스로 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-184">full-text index either on a schedule using SQL Server Agent or manually.</span></span>|  
|<span data-ttu-id="5cd5a-185">**자동**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-185">**Automatic**</span></span>|<span data-ttu-id="5cd5a-186">기본 테이블의 데이터가 변경되면 전체 텍스트 인덱스가 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-186">The full-text index is updated automatically as changes occur to the underlying data in the base table.</span></span>|  
  
 <span data-ttu-id="5cd5a-187">**인덱스 다시 채우기**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-187">**Repopulate index**</span></span>  
 <span data-ttu-id="5cd5a-188">대화 상자를 닫을 때 전체 텍스트 인덱스 채우기를 시작하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-188">Click to start a population on the full-text index on exiting the dialog box.</span></span> <span data-ttu-id="5cd5a-189">다음 채우기 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-189">Select one of the following types of population:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cd5a-190">**전체**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-190">**Full**</span></span>|<span data-ttu-id="5cd5a-191">테이블에 대해 전체 채우기를 수행하는 동안 모든 행에 대해 인덱스 항목이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-191">During a full population of a table, index entries are built for all the rows.</span></span>|  
|<span data-ttu-id="5cd5a-192">**대비**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-192">**Incremental**</span></span>|<span data-ttu-id="5cd5a-193">증분 채우기는 마지막 채우기 후 또는 마지막 채우기를 진행 중인 동안 추가, 삭제 또는 수정된 행에 대해 전체 텍스트 인덱스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-193">Incremental population updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="5cd5a-194">증분 채우기를 수행하려면 기본 테이블에 `timestamp` 데이터 형식의 열이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-194">Performing an incremental population requires that the base table contain a column of the `timestamp` data type.</span></span>|  
|<span data-ttu-id="5cd5a-195">**Update**</span><span class="sxs-lookup"><span data-stu-id="5cd5a-195">**Update**</span></span>|<span data-ttu-id="5cd5a-196">기본 테이블의 데이터가 수정될 때마다 전체 텍스트 인덱스가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cd5a-196">The full-text index is updated whenever the data in the base table is modified.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cd5a-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cd5a-197">See Also</span></span>  
 [<span data-ttu-id="5cd5a-198">전체 텍스트 검색 시작</span><span class="sxs-lookup"><span data-stu-id="5cd5a-198">Get Started with Full-Text Search</span></span>](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
