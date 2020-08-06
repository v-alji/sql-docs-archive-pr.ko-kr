---
title: 검색 속성 목록을 사용하여 문서 속성 검색 | Microsoft 문서
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- full-text search [SQL Server], properties
- search property lists [SQL Server]
- property searching [SQL Server], about
- full-text indexes [SQL Server], search property lists
- search property lists [SQL Server], about
- property searching [SQL Server]
ms.assetid: ffae5914-b1b2-4267-b927-37e8382e0a9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16ab59a9fcdab29c927cb624dabcdfa71eaae1e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735195"
---
# <a name="search-document-properties-with-search-property-lists"></a><span data-ttu-id="6cbd2-102">검색 속성 목록을 사용하여 문서 속성 검색</span><span class="sxs-lookup"><span data-stu-id="6cbd2-102">Search Document Properties with Search Property Lists</span></span>
  <span data-ttu-id="6cbd2-103">이전에는 문서 속성의 내용을 문서 본문의 내용과 구분할 수 없었으므로</span><span class="sxs-lookup"><span data-stu-id="6cbd2-103">The content of document properties was previously indistinguishable from the content of the document body.</span></span> <span data-ttu-id="6cbd2-104">전체 문서에서 일반 검색에 대해 전체 텍스트 쿼리를 수행할 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-104">This limitation restricted full-text queries to generic searches on whole documents.</span></span> <span data-ttu-id="6cbd2-105">그러나 이제 `varbinary`, `varbinary(max)`(`FILESTREAM` 포함) 또는 `image` 이진 데이터 열의 지원되는 문서 유형의 경우 Author 및 Title과 같은 특정 속성에 대한 속성 범위 검색을 지원하도록 전체 텍스트 인덱스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-105">Now, however, you can configure a full-text index to support property-scoped searching on particular properties, such as Author and Title, for supported document types in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` binary data column.</span></span> <span data-ttu-id="6cbd2-106">이러한 형태의 검색을 *속성 검색*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-106">This form of searching is known as *property searching*.</span></span>  
  
 <span data-ttu-id="6cbd2-107">연결된 [필터](configure-and-manage-filters-for-search.md) (IFilter)에 따라 특정 문서 유형에서 속성 검색이 가능한지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-107">The associated [filter](configure-and-manage-filters-for-search.md) (IFilter) determines whether property searching is possible on a specific type of document.</span></span> <span data-ttu-id="6cbd2-108">일부 문서 유형의 경우 연결된 IFilter가 문서 본문의 내용뿐만 아니라 해당 문서 유형에 대해 정의된 속성의 일부 또는 전부를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-108">For some document types, the associated IFilter extracts some or all of the properties defined for that type of document, as well as the content of the document body.</span></span> <span data-ttu-id="6cbd2-109">전체 텍스트 인덱싱 중 IFilter가 추출한 속성에 대해서만 속성 검색을 지원하도록 전체 텍스트 인덱스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-109">You can configure a full-text index to support property searching only on properties that are extracted by an IFilter during full-text indexing.</span></span> <span data-ttu-id="6cbd2-110">여러 문서 속성을 추출하는 IFilter 중에는 .docx, .xlsx 및 .pptx와 같은 Microsoft Office 문서 유형에 대한 IFilter가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-110">Among IFilters that extract a number of document properties are the IFilters for Microsoft Office document types (such as .docx, .xlsx, and .pptx).</span></span> <span data-ttu-id="6cbd2-111">반면에 XML 필터는 속성을 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-111">On the other hand, the XML IFilter does not emit properties.</span></span>  
  
##  <a name="how-full-text-search-works-with-search-properties"></a><a name="How_FTS_Works_with_search_properties"></a> <span data-ttu-id="6cbd2-112">전체 텍스트 검색이 검색 속성을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="6cbd2-112">How Full-Text Search Works with Search Properties</span></span>  
  
### <a name="internal-property-ids"></a><span data-ttu-id="6cbd2-113">내부 속성 ID</span><span class="sxs-lookup"><span data-stu-id="6cbd2-113">Internal Property IDs</span></span>  
 <span data-ttu-id="6cbd2-114">전체 텍스트 엔진은 특정 검색 목록에서 속성을 고유하게 식별하고 이 검색 속성 목록에 고유한 내부 속성 ID를 등록된 각 속성에 임의로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-114">The Full-Text Engine arbitrarily assigns each registered property an internal property ID, which uniquely identifies the property in that particular search list and which is specific to that search property list.</span></span> <span data-ttu-id="6cbd2-115">따라서 속성이 여러 검색 속성 목록에 추가되면 목록마다 내부 속성 ID가 다를 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-115">Therefore, if a property is added to multiple search property lists, its internal property ID is likely to differ between different lists.</span></span>  
  
 <span data-ttu-id="6cbd2-116">속성을 검색 목록에 등록하면 전체 텍스트 엔진이 속성에 *내부 속성 ID* 를 임의로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-116">When a property is registered for a search list, the Full-Text Engine arbitrarily assigns an *internal property ID* to the property.</span></span> <span data-ttu-id="6cbd2-117">내부 속성 ID는 검색 속성 목록에서 속성을 고유하게 식별하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-117">The internal property ID is an integer that uniquely identifies the property in that search property list.</span></span>  
  
 <span data-ttu-id="6cbd2-118">다음 설명에서는 Title 및 Keywords라는 두 개의 속성을 지정하는 검색 속성 목록의 논리적 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-118">The following illustration shows a logical view of a search property list that specifies two properties, Title and Keywords.</span></span> <span data-ttu-id="6cbd2-119">Keywords의 속성 목록 이름은 "Tags"입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-119">The property-list name for Keywords is "Tags".</span></span> <span data-ttu-id="6cbd2-120">이 속성은 GUID가 F29F85E0-4FF9-1068-AB91-08002B27B3D9인 동일한 속성 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-120">These properties belong to the same property set, whose GUID is F29F85E0-4FF9-1068-AB91-08002B27B3D9.</span></span> <span data-ttu-id="6cbd2-121">속성 정수 식별자는 Title의 경우 2이고, Tags(Keywords)의 경우 5입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-121">The property integer identifiers are 2 for Title and 5 for Tags (Keywords).</span></span> <span data-ttu-id="6cbd2-122">전체 텍스트 엔진은 각 속성을 검색 속성 목록에 고유한 내부 속성 ID로 임의 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-122">The Full-Text Engine arbitrarily maps each property to an internal property ID that is unique to the search property list.</span></span> <span data-ttu-id="6cbd2-123">Title 속성의 내부 속성 ID는 1이고 Tags 속성의 내부 속성 ID는 2입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-123">The internal property ID for the Title property is 1, and the internal property ID for the Tags property is 2.</span></span>  
  
 <span data-ttu-id="6cbd2-124">![내부 테이블에 대한 검색 속성 목록의 매핑](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "내부 테이블에 대한 검색 속성 목록의 매핑")</span><span class="sxs-lookup"><span data-stu-id="6cbd2-124">![Mapping of search property list to internal table](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "Mapping of search property list to internal table")</span></span>  
  
 <span data-ttu-id="6cbd2-125">내부 속성 ID는 속성의 속성 정수 식별자와 다를 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-125">The internal property ID is likely to be different from the property integer identifier of the property.</span></span> <span data-ttu-id="6cbd2-126">지정된 속성이 여러 검색 속성 목록에 대해 등록된 경우 검색 속성 목록마다 서로 다른 내부 속성 ID가 할당될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-126">If a given property is registered for multiple search property lists, a different internal property ID might be assigned for each search property list.</span></span> <span data-ttu-id="6cbd2-127">예를 들어 내부 속성 ID가 한 검색 속성 목록에서는 4이고, 다른 목록에서는 1이고, 또 다른 목록에서는 3일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-127">For example, the internal property ID might be 4 in one search property list, 1 in another, 3 in another, and so on.</span></span> <span data-ttu-id="6cbd2-128">반대로 속성 정수 식별자는 속성에 내재된 것이므로 속성이 사용되는 위치에 관계없이 항상 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-128">In contrast, the property integer identifier is intrinsic to the property, and it remains the same wherever the property is used.</span></span>  
  
  
  
### <a name="indexing-of-registered-properties"></a><span data-ttu-id="6cbd2-129">등록된 속성 인덱싱</span><span class="sxs-lookup"><span data-stu-id="6cbd2-129">Indexing of Registered Properties</span></span>  
 <span data-ttu-id="6cbd2-130">전체 텍스트 인덱스를 검색 속성 목록과 연결한 후 인덱스를 다시 채워야 속성별 검색 단어를 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-130">After a full-text index is associated with a search property list, the index must be repopulated to index property-specific search terms.</span></span> <span data-ttu-id="6cbd2-131">전체 텍스트 인덱싱 중 모든 속성의 내용은 다른 내용과 함께 전체 텍스트 인덱스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-131">During full-text indexing, the contents of all properties are stored in the full-text index along with other content.</span></span> <span data-ttu-id="6cbd2-132">하지만 등록된 속성에 있는 검색 단어를 인덱싱하는 경우 전체 텍스트 인덱서는 단어와 함께 해당 내부 속성 ID도 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-132">However, when indexing a search term found in a registered property, the full-text indexer also stores the corresponding internal property ID with the term.</span></span> <span data-ttu-id="6cbd2-133">반대로 속성이 등록되어 있지 않으면 해당 속성은 문서 본문의 일부이고 내부 속성 ID 값이 0인 것처럼 전체 텍스트 인덱스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-133">In contrast, if a property is not registered, it is stored in the full-text index as if it were part of the document body, and it has a value of zero for the internal property ID.</span></span>  
  
 <span data-ttu-id="6cbd2-134">다음 설명에서는 앞의 설명에 표시된 검색 속성 목록과 연결된 전체 텍스트 목록에 검색 단어가 어떻게 나타나는지에 대한 논리적 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-134">The following illustration shows a logical view of how search terms appear in a full-text index that is associated with the search property list shown in the preceding illustration.</span></span> <span data-ttu-id="6cbd2-135">샘플 문서인 Document 1은 문서 본문과 Title, Author 및 Keywords라는 세 개의 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-135">A sample document, Document 1 contains three properties-Title, Author, and Keywords-as well as the document body.</span></span> <span data-ttu-id="6cbd2-136">검색 속성 목록에 지정된 Title 및 Keywords 속성의 경우 검색 단어는 전체 텍스트 인덱스에서 해당 내부 속성 ID와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-136">For the properties Title and Keywords, which are specified in the search property list, search terms are associated with their corresponding internal property IDs in the full-text index.</span></span> <span data-ttu-id="6cbd2-137">반면 Author 속성의 내용은 문서 본문의 일부인 것처럼 인덱싱됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-137">In contrast, the content of the Author property is indexed as if it were part of the document body.</span></span> <span data-ttu-id="6cbd2-138">즉, 속성을 등록하면 속성에 저장되는 내용의 양에 따라 전체 텍스트 인덱스 크기가 어느 정도 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-138">This means registering a property increases the size of the full-text index somewhat, depending on the amount of content stored in the property.</span></span>  
  
 <span data-ttu-id="6cbd2-139">![검색 속성 목록을 사용하는 전체 텍스트 인덱스](../../database-engine/media/ifts-spl-and-fti.gif "검색 속성 목록을 사용하는 전체 텍스트 인덱스")</span><span class="sxs-lookup"><span data-stu-id="6cbd2-139">![Full-text index that uses a search property list](../../database-engine/media/ifts-spl-and-fti.gif "Full-text index that uses a search property list")</span></span>  
  
 <span data-ttu-id="6cbd2-140">Title 속성의 검색 단어("Favorite", "Biking" 및 "Trails")는 이 인덱스에 대해 Title에 할당된 내부 속성 ID 1과 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-140">Search terms in the Title property-"Favorite," "Biking," and "Trails"-are associated with the internal property ID assigned to Title for this index, 1.</span></span> <span data-ttu-id="6cbd2-141">Keywords 속성의 검색 단어("biking" 및 "mountain")는 이 인덱스에 대해 Tags에 할당된 내부 속성 ID 2와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-141">Search terms in the Keywords property-"biking" and "mountain"-are associated with the internal property ID assigned to Tags for this index, 2.</span></span> <span data-ttu-id="6cbd2-142">Author 속성의 검색 단어("Jane" 및 "Doe")와 문서 본문의 검색 단어의 경우 내부 속성 ID는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-142">For search terms n the Author property-"Jane" and "Doe"-and search terms in the document body, the internal property ID is 0.</span></span> <span data-ttu-id="6cbd2-143">"biking"이라는 단어는 Title 속성, Keywords(Tags) 속성 및 문서 본문에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-143">Note that the term "biking" occurs in the Title property, in the Keywords (Tags) property, and in the document body.</span></span> <span data-ttu-id="6cbd2-144">Title 또는 Keywords(Tags) 속성에서 "biking"에 대한 속성 검색을 수행하면 결과에 이 문서가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-144">A property search for "biking" in the Title or Keywords (Tags) property would return this document in the results.</span></span> <span data-ttu-id="6cbd2-145">"biking"에 대한 일반 전체 텍스트 쿼리에서도 속성 검색에 대해 인덱스가 구성되지 않은 것처럼 이 문서가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-145">A generic full-text query for "biking" would also return this document, just as if the index were not configured for property searching.</span></span> <span data-ttu-id="6cbd2-146">Author 속성에서 "biking"에 대한 속성 검색을 수행하면 이 문서가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-146">A property search for "biking" in the Author property would not return this document.</span></span>  
  
 <span data-ttu-id="6cbd2-147">속성 범위 전체 텍스트 쿼리는 전체 텍스트 인덱스의 현재 검색 속성 목록에 등록된 내부 속성 ID를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-147">A property-scoped full-text query uses the internal property IDs registered for the current search property list of the full-text index.</span></span>  
  
  
  
##  <a name="impact-of-enabling-property-searching"></a><a name="impact"></a> <span data-ttu-id="6cbd2-148">속성 검색 사용의 영향</span><span class="sxs-lookup"><span data-stu-id="6cbd2-148">Impact of Enabling Property Searching</span></span>  
 <span data-ttu-id="6cbd2-149">하나 이상의 속성에 대한 검색을 지원하도록 전체 텍스트 인덱스를 구성하면 검색 속성 목록에 지정한 속성 수와 각 속성의 내용에 따라 인덱스 크기가 어느 정도 커집니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-149">Configuring a full-text index to support searching on one or more properties increases the size of the index somewhat, depending on the number of properties you specify in your search property list and on the content of each property.</span></span>  
  
 <span data-ttu-id="6cbd2-150">Microsoft Word의 일반적인 인덱싱하도록?, Excel<sup>??</sup>?<sup>및 PowerPoint를 테스트 하</sup> <sup>는 경우</sup></span><span class="sxs-lookup"><span data-stu-id="6cbd2-150">In testing typical corpuses of Microsoft Word<sup>??</sup>, Excel<sup>??</sup>, and PowerPoint<sup>??</sup></span></span> <span data-ttu-id="6cbd2-151">문서에서는 일반 검색 속성을 인덱싱하는 전체 텍스트 인덱스를 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-151">documents, we configured a full-text index to index typical search properties.</span></span> <span data-ttu-id="6cbd2-152">이러한 속성을 인덱싱하면 전체 텍스트 인덱스 크기가 약 5% 커집니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-152">Indexing these properties increased the size of the full-text index size by approximately 5 percent.</span></span> <span data-ttu-id="6cbd2-153">대부분의 문서 모음에서는 대략 이 정도로 인덱스 크기가 증가할 것으로 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-153">We anticipate that this approximate size increase will to be typical for most document corpuses.</span></span> <span data-ttu-id="6cbd2-154">하지만 궁극적으로 인덱스 크기는 전체 데이터 크기에 상대적인 지정된 문서 모음에 있는 속성 데이터 크기에 따라 증가할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-154">However, ultimately, the size increase will depend on the amount of property data in a given document corpus relative to the amount of overall data.</span></span>  
  
  
  
##  <a name="creating-a-search-property-list-and-enabling-property-search"></a><a name="creating"></a><span data-ttu-id="6cbd2-155">검색 속성 목록 만들기 및 속성 검색 활성화</span><span class="sxs-lookup"><span data-stu-id="6cbd2-155">Creating a Search Property List and Enabling Property Search</span></span>  
  
###  <a name="creating-a-search-property-list"></a><a name="creating_sub"></a> <span data-ttu-id="6cbd2-156">검색 속성 목록 만들기</span><span class="sxs-lookup"><span data-stu-id="6cbd2-156">Creating a Search Property List</span></span>  
 <span data-ttu-id="6cbd2-157">**Transact-SQL을 사용하여 검색 속성 목록을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-157">**To create a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="6cbd2-158">[CREATE SEARCH PROPERTY LIST&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) 문을 사용하고 목록에 이름을 하나 이상 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-158">Use the [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) statement and provide at least a name the list.</span></span>  
  
##### <a name="to-create-a-search-property-list-in-management-studio"></a><span data-ttu-id="6cbd2-159">Management Studio에서 검색 속성 목록을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6cbd2-159">To create a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="6cbd2-160">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-160">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="6cbd2-161">**데이터베이스**를 확장한 다음 검색 속성 목록을 만들려는 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-161">Expand **Databases**, and then expand the database in which you want to create the search property list.</span></span>  
  
3.  <span data-ttu-id="6cbd2-162">**스토리지**를 확장하고 **검색 속성 목록**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-162">Expand **Storage**, and then right-click **Search Property Lists**.</span></span>  
  
4.  <span data-ttu-id="6cbd2-163">**새 검색 속성 목록**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-163">Select **New Search Property List**.</span></span>  
  
5.  <span data-ttu-id="6cbd2-164">속성 목록 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-164">Specify the property list name.</span></span>  
  
6.  <span data-ttu-id="6cbd2-165">필요에 따라 다른 사용자를 속성 목록 소유자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-165">Optionally, specify someone else as the property list owner.</span></span>  
  
7.  <span data-ttu-id="6cbd2-166">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-166">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="6cbd2-167">**빈 검색 속성 목록 만들기**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-167">**Create an empty search property list**</span></span>  
  
    -   <span data-ttu-id="6cbd2-168">**기존 검색 속성 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-168">**Create from an existing search property list**</span></span>  
  
     <span data-ttu-id="6cbd2-169">자세한 내용은 [New Search Property List](../../database-engine/new-search-property-list.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-169">For more information, see [New Search Property List](../../database-engine/new-search-property-list.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 
  
###  <a name="adding-properties-to-a-search-property-list"></a><a name="adding"></a><span data-ttu-id="6cbd2-170">검색 속성 목록에 속성 추가</span><span class="sxs-lookup"><span data-stu-id="6cbd2-170">Adding Properties to a Search Property List</span></span>  
 <span data-ttu-id="6cbd2-171">속성 검색을 수행하려면 *검색 속성 목록* 을 만들고 검색 가능한 속성으로 만들 하나 이상의 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-171">Property searching requires creating a *search property list* and specifying one or more properties that you want to make searchable.</span></span> <span data-ttu-id="6cbd2-172">속성을 검색 속성 목록에 추가하면 속성이 해당 목록에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-172">When you add a property to a search property list, the property is registered for that particular list.</span></span> <span data-ttu-id="6cbd2-173">속성을 검색 속성 목록에 추가하려면 다음과 같은 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-173">To add a property to a search property list you need the following values:</span></span>  
  
-   <span data-ttu-id="6cbd2-174">속성 집합 GUID</span><span class="sxs-lookup"><span data-stu-id="6cbd2-174">Property set GUID</span></span>  
  
     <span data-ttu-id="6cbd2-175">각 검색 속성은 관련 속성 그룹을 포함하는 단일 속성 집합에 속해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-175">Each search property belongs to single property set that contains a group of related properties.</span></span> <span data-ttu-id="6cbd2-176">각 속성 집합은 GUID(Globally Unique Identifier)로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-176">Each property set is identified by a globally unique identifier (GUID).</span></span>  
  
-   <span data-ttu-id="6cbd2-177">속성 정수 식별자</span><span class="sxs-lookup"><span data-stu-id="6cbd2-177">Property integer identifier</span></span>  
  
     <span data-ttu-id="6cbd2-178">각 검색 속성은 속성 집합 안에서 고유한 식별자를 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-178">Each search property possesses an identifier that is unique within the property set.</span></span> <span data-ttu-id="6cbd2-179">지정된 속성에 대해 식별자는 정수 또는 문자열일 수 있지만 전체 텍스트 검색은 정수 식별자만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-179">Note that for a given property, the identifier could be either an integer or a string, however full-text search supports only integer identifiers.</span></span>  
  
-   <span data-ttu-id="6cbd2-180">속성 이름</span><span class="sxs-lookup"><span data-stu-id="6cbd2-180">Property name</span></span>  
  
     <span data-ttu-id="6cbd2-181">사용자가 속성을 검색하기 위해 전체 텍스트 쿼리에서 지정할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-181">This is the name that users will specify in full-text queries to search on the property.</span></span> <span data-ttu-id="6cbd2-182">속성 이름은 내부에 공백을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-182">A property name can contain internal spaces.</span></span> <span data-ttu-id="6cbd2-183">최대 길이는 256자입니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-183">The maximum length is 256 characters.</span></span>  
  
     <span data-ttu-id="6cbd2-184">속성 이름은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-184">The property name can be any of the following:</span></span>  
  
    -   <span data-ttu-id="6cbd2-185">속성의 Windows 정식 이름(예: `System.Author` 또는 `System.Contact.HomeAddress`)</span><span class="sxs-lookup"><span data-stu-id="6cbd2-185">The Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span>  
  
    -   <span data-ttu-id="6cbd2-186">사용자가 기억하기 쉬운 이름.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-186">A user-friendly name that is easy for your users to remember.</span></span> <span data-ttu-id="6cbd2-187">일부 속성은 잘 알려진 이름(예: "Author" 또는 "Home Address")과 연결되어 있지만 사용자에게 가장 적합한 임의의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-187">Some properties are associated with a well-known user-friendly name, such as "Author" or "Home Address," but you can specify whatever name is most appropriate to your users.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6cbd2-188">지정된 속성 집합 GUID와 속성 식별자의 조합은 지정된 검색 속성 목록에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-188">A given combination of property set GUID and property identifier must be unique in a given search property list.</span></span> <span data-ttu-id="6cbd2-189">즉, 동일한 속성을 다른 이름이나 설명으로 두 번 이상 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-189">This means that you cannot add the same property more than once with different names or descriptions.</span></span>  
  
-   <span data-ttu-id="6cbd2-190">속성 설명(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="6cbd2-190">Property description (optional)</span></span>  
  
     <span data-ttu-id="6cbd2-191">검색 속성을 검색 속성 목록에 추가할 때 선택적으로 설명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-191">When adding a search property to a search property list, you can supply an optional description.</span></span> <span data-ttu-id="6cbd2-192">예를 들어 이름만으로는 명확하지 않은 속성에 대한 정보를 제공하거나 속성의 속성 집합에 대해 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-192">For example, you might want to provide information about a property that is not evident from its name, or you might want to describe the property set of the property.</span></span>  
  
 <span data-ttu-id="6cbd2-193">**검색 속성 목록 값을 얻으려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-193">**To obtain values for a search property list**</span></span>  
  
 <span data-ttu-id="6cbd2-194">[검색 속성의 속성 집합 GUID 및 속성 정수 ID찾기](find-property-set-guids-and-property-integer-ids-for-search-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-194">See [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="6cbd2-195">**Transact-SQL을 사용하여 속성을 검색 속성 목록에 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-195">**To add a property to a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="6cbd2-196">[검색 속성의 속성 집합 GUID 및 속성 정수 ID찾기](find-property-set-guids-and-property-integer-ids-for-search-properties.md) 항목에서 설명한 방법 중 하나를 사용하여 가져온 값과 함께 [ALTER SEARCH PROPERTY LIST&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-196">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement with the values that you obtained by using one of the methods described in the topic, [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="6cbd2-197">다음 예에서는 속성을 검색 속성 목록에 추가할 때 이러한 값을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-197">The following example demonstrates the use of these values when adding a property to a search property list:</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST DocumentTablePropertyList  
   ADD 'Title'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
```  
  
 <span data-ttu-id="6cbd2-198">**Management Studio에서 속성을 검색 속성 목록에 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-198">**To add a property to a search property list in Management Studio**</span></span>  
  
 <span data-ttu-id="6cbd2-199">**검색 속성 목록 속성** 대화 상자를 사용하여 검색 속성을 추가하고 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-199">Use the **Search Property List Properties** dialog box to add and remove search properties.</span></span> <span data-ttu-id="6cbd2-200">개체 탐색기에서 연결된 데이터베이스의 **스토리지** 노드 아래에서 **검색 속성 목록**을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-200">You can find **Search Property Lists** in Object Explorer under the **Storage** node of the associated database.</span></span>  
  
  
  
###  <a name="associating-a-search-property-list-with-a-full-text-index"></a><a name="associating"></a> <span data-ttu-id="6cbd2-201">전체 텍스트 인덱스에 검색 속성 목록 연결</span><span class="sxs-lookup"><span data-stu-id="6cbd2-201">Associating a Search Property List with a Full-Text Index</span></span>  
 <span data-ttu-id="6cbd2-202">전체 텍스트 인덱스가 검색 속성 목록에 등록된 속성에 대한 속성 검색을 지원하려면 검색 속성 목록을 인덱스와 연결하고 해당 인덱스를 다시 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-202">For a full-text index to support property searching on the properties that are registered for a search property list, you need to associate the search property list with the index and repopulate the index.</span></span> <span data-ttu-id="6cbd2-203">전체 텍스트 인덱스를 다시 채우면 등록된 각 속성의 검색 단어에 대해 속성 관련 인덱스 항목이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-203">Repopulating the full-text index creates property-specific index entries for search terms in each of the registered properties.</span></span>  
  
 <span data-ttu-id="6cbd2-204">전체 텍스트 인덱스가 이 검색 속성 목록에 연결되어 있는 한 전체 텍스트 쿼리는 CONTAINS 조건자의 PROPERTY 옵션을 사용하여 해당 검색 속성 목록에 등록된 속성을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-204">As long as the full-text index remains associated with this search property list, full-text query can use the PROPERTY option of the CONTAINS predicate to search on properties that are registered for that search property list.</span></span>  
  
 <span data-ttu-id="6cbd2-205">전체 텍스트 인덱스에 연결된 검색 속성 목록을 변경하는 경우 인덱스를 다시 작성하여 일관된 상태로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-205">If you change the search property list associated with a full-text index, then the index must be rebuilt to bring it into a consistent state.</span></span> <span data-ttu-id="6cbd2-206">인덱스는 즉시 잘려 전체 채우기를 실행할 때까지 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-206">The index is truncated immediately and is empty until the full population runs.</span></span> <span data-ttu-id="6cbd2-207">검색 속성 목록을 변경하면 인덱스를 다시 작성해야 하는 경우는 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)에서 "주의"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-207">For more information about when changing the search property list causes rebuilding the index, see "Remarks," in [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="6cbd2-208">**Transact-SQL을 사용하여 전체 텍스트 인덱스에 검색 속성 목록을 연결하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-208">**To associate a search property list with a full-text index with Transact-SQL**</span></span>  
  
 <span data-ttu-id="6cbd2-209">`SET SEARCH PROPERTY LIST = <property_list_name>` 절과 함께 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-209">Use the [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement with the `SET SEARCH PROPERTY LIST = <property_list_name>` clause.</span></span>  
  
 <span data-ttu-id="6cbd2-210">**Management Studio를 사용하여 전체 텍스트 인덱스에 검색 속성 목록을 연결하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-210">**To associate a search property list with a full-text index with Management Studio**</span></span>  
  
 <span data-ttu-id="6cbd2-211">**전체 텍스트 인덱스 속성** 대화 상자의 **일반** 페이지에서 **검색 속성 목록**의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-211">Specify a value for **Search Property List** on the **General** page of the **Full-Text Index Properties** dialog box.</span></span>  
  
  
  
##  <a name="querying-search-properties-with-contains"></a><a name="Ov_CONTAINS_using_PROPERTY"></a><span data-ttu-id="6cbd2-212">CONTAINS를 사용 하 여 검색 속성 쿼리</span><span class="sxs-lookup"><span data-stu-id="6cbd2-212">Querying Search Properties with CONTAINS</span></span>  
 <span data-ttu-id="6cbd2-213">속성 범위 전체 텍스트 쿼리를 위한 기본 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-213">The basic [CONTAINS](/sql/t-sql/queries/contains-transact-sql) syntax for a property-scoped full-text query is as follows:</span></span>  
  
```sql  
SELECT column_name FROM table_name  
  WHERE CONTAINS ( PROPERTY ( column_name, 'property_name' ), '<contains_search_condition>' )  
```  
  
 <span data-ttu-id="6cbd2-214">예를 들어 다음 쿼리는 `Title`데이터베이스에 있는 `Document` 테이블의 `Production.Document` 열에서 인덱싱된 속성인 `AdventureWorks` 을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-214">For example, the following query searches on an indexed property, `Title`, in the `Document` column of the `Production.Document` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="6cbd2-215">쿼리는 `Title` 속성에 `Maintenance` 또는 `Repair`</span><span class="sxs-lookup"><span data-stu-id="6cbd2-215">The query returns only documents whose `Title` property contains the string `Maintenance` or `Repair`</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT Document FROM Production.Document  
  WHERE CONTAINS ( PROPERTY ( Document, 'Title' ), 'Maintenance OR Repair')  
GO  
```  
  
 <span data-ttu-id="6cbd2-216">이 예에서는 문서의 IFilter가 Title 속성을 추출하고 Title 속성이 검색 속성 목록에 추가되어 있으며 검색 속성 목록이 전체 텍스트 인덱스에 연결되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-216">This example assumes that the IFilter for the document extracts its Title property, that the Title property is added to the search property list, and that the search property list is associated with the full-text index.</span></span>  
  
  
  
##  <a name="managing-search-property-lists"></a><a name="managing"></a><span data-ttu-id="6cbd2-217">검색 속성 목록 관리</span><span class="sxs-lookup"><span data-stu-id="6cbd2-217">Managing Search Property Lists</span></span>  
  
###  <a name="viewing-and-changing-a-search-property-list"></a><a name="viewing"></a><span data-ttu-id="6cbd2-218">검색 속성 목록 보기 및 변경</span><span class="sxs-lookup"><span data-stu-id="6cbd2-218">Viewing and Changing a Search Property List</span></span>  
 <span data-ttu-id="6cbd2-219">**Transact-SQL을 사용하여 검색 속성 목록을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-219">**To change a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="6cbd2-220">[ALTER SEARCH PROPERTY LIST&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) 문을 사용하여 검색 속성을 추가 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-220">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add or remove search properties.</span></span>  
  
##### <a name="to-view-and-change-a-search-property-list-in-management-studio"></a><span data-ttu-id="6cbd2-221">Management Studio에서 검색 속성 목록을 보고 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6cbd2-221">To view and change a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="6cbd2-222">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-222">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="6cbd2-223">**데이터베이스**를 확장한 다음 해당 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-223">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="6cbd2-224">**스토리지**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-224">Expand **Storage**.</span></span>  
  
4.  <span data-ttu-id="6cbd2-225">**검색 속성 목록**을 확장하여 검색 속성 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-225">Expand **Search Property Lists** to display the search property lists.</span></span>  
  
5.  <span data-ttu-id="6cbd2-226">속성 목록을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-226">Right-click the property list, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="6cbd2-227">\*\* 속성 목록 편집기\*\* 대화 상자에서 속성 표를 사용하여 검색 속성을 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-227">In the **Search Property List Editor** dialog box, use the Properties grid to add or remove search properties:</span></span>  
  
    1.  <span data-ttu-id="6cbd2-228">문서 속성을 제거하려면 속성 왼쪽에 있는 행 머리글을 클릭하고 Del 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-228">To remove a document property, click the row header to the left of the property, and press DEL .</span></span>  
  
    2.  <span data-ttu-id="6cbd2-229">문서 속성을 추가 하려면의 오른쪽에 있는 목록 아래쪽에서 빈 행을 클릭 하 **\*** 고 새 속성의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-229">To add a document property, click in the empty row at the bottom of the list, to the right of the **\***, and enter the values for the new property.</span></span>  
  
         <span data-ttu-id="6cbd2-230">이러한 값에 대한 자세한 내용은 [검색 속성 목록 편집기](../../database-engine/search-property-list-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-230">For information about these values, see [Search Property List Editor](../../database-engine/search-property-list-editor.md).</span></span> <span data-ttu-id="6cbd2-231">Microsoft에서 정의한 속성의 이러한 값을 가져오는 방법은 [검색 속성의 속성 집합 GUID 및 속성 정수 ID 찾기](find-property-set-guids-and-property-integer-ids-for-search-properties.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-231">For information about how to obtain these values for properties defined by Microsoft, see [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span> <span data-ttu-id="6cbd2-232">ISV(Independent Software Vendor)에서 정의한 속성에 대한 자세한 내용은 해당 공급업체의 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-232">For information about properties defined by an independent software vendor (ISV), see the documentation of that vendor.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
###  <a name="deleting-a-search-property-list"></a><a name="deleting"></a><span data-ttu-id="6cbd2-233">검색 속성 목록 삭제</span><span class="sxs-lookup"><span data-stu-id="6cbd2-233">Deleting a Search Property List</span></span>  
 <span data-ttu-id="6cbd2-234">데이터베이스의 속성 목록이 전체 텍스트 인덱스에 연결되어 있는 경우에는 해당 속성 목록을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-234">You cannot drop a property list from a database while the list is associated with any full-text index.</span></span>  
  
 <span data-ttu-id="6cbd2-235">**Transact-SQL을 사용하여 검색 속성 목록을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="6cbd2-235">**To delete a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="6cbd2-236">[DROP SEARCH PROPERTY LIST&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-236">Use the [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) statement.</span></span>  
  
##### <a name="to-delete-a-search-property-list-in-management-studio"></a><span data-ttu-id="6cbd2-237">Management Studio에서 검색 속성 목록을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6cbd2-237">To delete a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="6cbd2-238">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-238">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="6cbd2-239">**데이터베이스**를 확장한 다음 해당 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-239">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="6cbd2-240">**스토리지**를 확장하고 **검색 속성 목록** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-240">Expand **Storage**, and then expand the **Search Property Lists** node.</span></span>  
  
4.  <span data-ttu-id="6cbd2-241">삭제할 속성 목록을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbd2-241">Right-click the property list that you want to delete, and click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

  
## <a name="see-also"></a><span data-ttu-id="6cbd2-242">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6cbd2-242">See Also</span></span>  
 <span data-ttu-id="6cbd2-243">[검색 속성에 대 한 속성 집합 Guid 및 속성 정수 Id 찾기](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6cbd2-243">[Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span></span>  
 [<span data-ttu-id="6cbd2-244">검색 필터 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="6cbd2-244">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
