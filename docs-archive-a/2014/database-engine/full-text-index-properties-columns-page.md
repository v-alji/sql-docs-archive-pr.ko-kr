---
title: 전체 텍스트 인덱스 속성 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: rothja
ms.author: jroth
ms.openlocfilehash: f947af04463948ef551c6df866d5a306c248c6b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661310"
---
# <a name="full-text-index-properties-columns-page"></a><span data-ttu-id="23335-102">전체 텍스트 인덱스 속성(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="23335-102">Full-Text Index Properties (Columns Page)</span></span>
  <span data-ttu-id="23335-103">**전체 텍스트 인덱스의 속성을 보거나 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="23335-103">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="23335-104">전체 텍스트 인덱스 관리</span><span class="sxs-lookup"><span data-stu-id="23335-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="23335-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="23335-105">UI element list</span></span>  
 <span data-ttu-id="23335-106">**고유 인덱스**</span><span class="sxs-lookup"><span data-stu-id="23335-106">**Unique index**</span></span>  
 <span data-ttu-id="23335-107">드롭다운 목록에서 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23335-107">Select an index from the drop down list.</span></span> <span data-ttu-id="23335-108">인덱스는 Null 값을 허용하지 않는 고유한 단일 키 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23335-108">The index must be a single-key-column, unique, non-nullable index.</span></span>  
  
 <span data-ttu-id="23335-109">**전체 텍스트 인덱싱할 적절한 열을 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="23335-109">**Select the eligible columns that will be full-text indexed**</span></span>  
 <span data-ttu-id="23335-110">표에는 이 전체 텍스트 인덱스에 사용할 수 있는 테이블 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23335-110">The grid displays the table columns that are available for this full-text index.</span></span> <span data-ttu-id="23335-111">현재 전체 텍스트 인덱싱된 열은 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23335-111">Columns that are currently full-text indexed are checked.</span></span> <span data-ttu-id="23335-112">경우에 따라 전체 텍스트 인덱싱할 추가 열을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23335-112">Optionally, you can check additional columns that you want to be full-text indexed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23335-113">확인을 클릭하기 전에 최소한 하나의 열이 선택되어 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="23335-113">Ensure that at least one column is checked before you click OK.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23335-114">**사용 가능한 열**</span><span class="sxs-lookup"><span data-stu-id="23335-114">**Available Columns**</span></span>|<span data-ttu-id="23335-115">열 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="23335-115">The column name.</span></span>|  
|<span data-ttu-id="23335-116">**단어 분리기 용 언어**</span><span class="sxs-lookup"><span data-stu-id="23335-116">**Language for Word Breaker**</span></span>|<span data-ttu-id="23335-117">단어 분리기와 형태소 분석기에서 모든 전체 텍스트 인덱싱된 데이터에 대해 언어 분석을 수행하는 데 사용되는 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="23335-117">The language whose word breakers and stemmers perform linguistic analysis on all full-text indexed data.</span></span><br /><br /> <span data-ttu-id="23335-118">자세한 내용은 [검색을 위해 단어 분리기 및 형태소 분석기 구성 및 관리](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) 를 참조 하 고 [전체 텍스트 인덱스를 만들 때 언어를 선택](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="23335-118">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) and [Choose a Language When Creating a Full-Text Index](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).</span></span>|  
|<span data-ttu-id="23335-119">**형식**</span><span class="sxs-lookup"><span data-stu-id="23335-119">**Type**</span></span>|<span data-ttu-id="23335-120">선택한 열의 문서 유형을 보관하는 테이블 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="23335-120">The name of the table column that holds the document type of the selected column.</span></span> <span data-ttu-id="23335-121">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="23335-121">This is a read-only property.</span></span>|  
|<span data-ttu-id="23335-122">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="23335-122">**Statistical Semantics**</span></span>|<span data-ttu-id="23335-123">선택한 열에 대해 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23335-123">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="23335-124">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23335-124">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="23335-125">**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23335-125">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="23335-126">**언어** 를 선택하기 전에 **통계 의미 체계**를 선택한 경우 드롭다운 콤보 상자에서 사용할 수 있는 언어가 의미 체계 언어 모델에서 지원하는 언어로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="23335-126">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23335-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23335-127">See Also</span></span>  
 [<span data-ttu-id="23335-128">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="23335-128">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
