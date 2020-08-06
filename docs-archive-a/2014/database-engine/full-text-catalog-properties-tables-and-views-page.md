---
title: 전체 텍스트 카탈로그 속성 (테이블 및 뷰 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
ms.openlocfilehash: eb4d968af6c550d19fbb8934b5d76a1bd63cb8da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740293"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a><span data-ttu-id="74465-102">전체 텍스트 카탈로그 속성(테이블 및 뷰 페이지)</span><span class="sxs-lookup"><span data-stu-id="74465-102">Full-Text Catalog Properties (Tables and Views Page)</span></span>
  <span data-ttu-id="74465-103">이 대화 상자를 사용하여 전체 텍스트 카탈로그에 할당된 테이블과 뷰를 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74465-103">Use this dialog page to view or modify the tables and views that are assigned to the full-text catalog.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="74465-104">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="74465-104">UI element list</span></span>  
 <span data-ttu-id="74465-105">**이 데이터베이스에서 적합한 모든 테이블/뷰 개체**</span><span class="sxs-lookup"><span data-stu-id="74465-105">**All eligible table/view objects in this database**</span></span>  
 <span data-ttu-id="74465-106">고유 인덱스가 정의되어 있지만 아직 전체 텍스트 카탈로그에 포함되지 않은 테이블 및 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-106">Lists the tables and views that have a unique index defined on them, but are not already a part of the full-text catalog.</span></span> <span data-ttu-id="74465-107">테이블이 나 뷰를 선택 하 여 카탈로그에 할당 하려면 목록 상자에서 항목을 선택 하 고 "->" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="74465-107">To select a table or view and assign it to the catalog, select the items in the list box and press the "->" button.</span></span>  
  
 <span data-ttu-id="74465-108">**카탈로그에 할당된 테이블/뷰 개체**</span><span class="sxs-lookup"><span data-stu-id="74465-108">**Table/view objects assigned to the catalog**</span></span>  
 <span data-ttu-id="74465-109">현재 전체 텍스트 카탈로그에 할당된 테이블과 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-109">Lists the tables and views that are currently assigned to the full-text catalog</span></span>  
  
## <a name="selected-object-properties"></a><span data-ttu-id="74465-110">선택한 개체 속성</span><span class="sxs-lookup"><span data-stu-id="74465-110">Selected Object Properties</span></span>  
 <span data-ttu-id="74465-111">**선택한 개체 속성**</span><span class="sxs-lookup"><span data-stu-id="74465-111">**Selected object properties**</span></span>  
 <span data-ttu-id="74465-112">카탈로그에 할당된 개체 목록 상자에서 선택한 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-112">Displays the properties of the selected object in the list box of objects assigned to the catalog.</span></span>  
  
 <span data-ttu-id="74465-113">**고유 인덱스**</span><span class="sxs-lookup"><span data-stu-id="74465-113">**Unique Index**</span></span>  
 <span data-ttu-id="74465-114">테이블이나 뷰에 사용할 수 있는 고유 인덱스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-114">Lists the available unique indexes of the table or view.</span></span>  
  
 <span data-ttu-id="74465-115">**테이블에서 전체 텍스트 사용**</span><span class="sxs-lookup"><span data-stu-id="74465-115">**Table is full-text enabled**</span></span>  
 <span data-ttu-id="74465-116">테이블에서 전체 텍스트 인덱스를 사용하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-116">Select this check box to enable the full-text index on the table.</span></span> <span data-ttu-id="74465-117">전체 텍스트 인덱스를 사용하지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-117">Clear the check box to disable the full-text index.</span></span>  
  
## <a name="eligible-columns-grid"></a><span data-ttu-id="74465-118">적합한 열 표</span><span class="sxs-lookup"><span data-stu-id="74465-118">Eligible Columns Grid</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74465-119">**사용 가능한 열**</span><span class="sxs-lookup"><span data-stu-id="74465-119">**Available Columns**</span></span>|<span data-ttu-id="74465-120">전체 텍스트 인덱싱된 모든 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-120">Displays all the columns that are full-text indexed.</span></span> <span data-ttu-id="74465-121">전체 텍스트 인덱스에 열을 추가하려면 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-121">Select a check box to add a column to the full-text index.</span></span>|  
|<span data-ttu-id="74465-122">**단어 분리기 용 언어**</span><span class="sxs-lookup"><span data-stu-id="74465-122">**Language for Word Breaker**</span></span>|<span data-ttu-id="74465-123">단어 분리기의 언어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-123">Displays the language of the word breaker.</span></span>|  
|<span data-ttu-id="74465-124">**데이터 형식 열**</span><span class="sxs-lookup"><span data-stu-id="74465-124">**Data Type Column**</span></span>|<span data-ttu-id="74465-125">열이 또는 열인 경우 **사용 가능한 열** 에 나열 된 열의 문서 유형을 포함 하는 테이블의 열 이름을 나열 합니다 `varbinary(max)` `image` .</span><span class="sxs-lookup"><span data-stu-id="74465-125">Lists the name of the column in the table that holds the document type of the column listed in **Available Columns** if the column is a `varbinary(max)` or `image` column.</span></span>|  
|<span data-ttu-id="74465-126">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="74465-126">**Statistical Semantics**</span></span>|<span data-ttu-id="74465-127">선택한 열에 대해 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-127">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="74465-128">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74465-128">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="74465-129">**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74465-129">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="74465-130">**언어** 를 선택하기 전에 **통계 의미 체계**를 선택한 경우 드롭다운 콤보 상자에서 사용할 수 있는 언어가 의미 체계 언어 모델에서 지원하는 언어로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="74465-130">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="track-changes"></a><span data-ttu-id="74465-131">변경 내용 추적</span><span class="sxs-lookup"><span data-stu-id="74465-131">Track Changes</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74465-132">**자동**</span><span class="sxs-lookup"><span data-stu-id="74465-132">**Automatic**</span></span>|<span data-ttu-id="74465-133">기본 테이블의 데이터가 수정, 추가 또는 삭제되면 전체 텍스트 인덱스가 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="74465-133">The full-text index is automatically updated when the data in the underlying table is modified, added, or deleted.</span></span>|  
|<span data-ttu-id="74465-134">**수동**</span><span class="sxs-lookup"><span data-stu-id="74465-134">**Manual**</span></span>|<span data-ttu-id="74465-135">인덱싱된 데이터가 수정, 추가 또는 삭제되면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 변경 내용을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-135">When data is modified, added, or deleted in the indexed data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracks the changes.</span></span> <span data-ttu-id="74465-136">**수동** 변경 내용 추적을 사용하는 경우 해당 변경 내용으로 인덱스가 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74465-136">When **Manual** change tracking is in effect, the index is not automatically updated with these changes.</span></span> <span data-ttu-id="74465-137">대신 관리자가 [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 문을 사용하여 수동으로 변경 내용을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74465-137">Instead, an administrator can apply the changes manually by using an [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement.</span></span>|  
|<span data-ttu-id="74465-138">**변경 내용 추적 안 함**</span><span class="sxs-lookup"><span data-stu-id="74465-138">**Do not track change**</span></span>|<span data-ttu-id="74465-139">이 옵션을 사용하는 경우 카탈로그의 인덱싱된 데이터에 대한 변경 내용이 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74465-139">With this option in effect, changes to the indexed data in the catalog are not recorded.</span></span> <span data-ttu-id="74465-140">관리자는 ALTER FULLTEXT INDEX와 함께 FULL POPULATION 또는 INCREMENTAL POPULATION을 사용하여 인덱스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74465-140">An administrator must build the index by using ALTER FULLTEXT INDEX with either FULL POPULATION or INCREMENTAL POPULATION.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74465-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74465-141">See Also</span></span>  
 <span data-ttu-id="74465-142">[CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="74465-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="74465-143">[Transact-sql&#41;&#40;전체 텍스트 카탈로그 변경](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="74465-143">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="74465-144">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="74465-144">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
