---
title: 전체 텍스트 중지 목록 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661299"
---
# <a name="full-text-stoplist-properties"></a><span data-ttu-id="41dfb-102">전체 텍스트 중지 목록 속성</span><span class="sxs-lookup"><span data-stu-id="41dfb-102">Full-Text Stoplist Properties</span></span>
  <span data-ttu-id="41dfb-103">이 대화 상자를 사용하여 중지 단어를 개별적으로 추가 또는 삭제하거나 특정 언어에 대한 중지 단어를 모두 삭제하거나 현재 중지 목록을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-103">Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist.</span></span> <span data-ttu-id="41dfb-104">중지 단어란 자주 사용되는 단어 중 중지 목록에 포함된 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-104">A stopword is a commonly used word that is included in a stoplist.</span></span> <span data-ttu-id="41dfb-105">중지 목록에 있는 중지 단어는 해당 중지 목록을 사용하는 테이블에 대한 전체 텍스트 인덱싱에서 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-105">The stopwords in a stoplist are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="41dfb-106">자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](../relational-databases/search/full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41dfb-106">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="41dfb-107">**SQL Server Management Studio를 사용하여 중지 목록 속성을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="41dfb-107">**To use SQL Server Management Studio to change stoplist properties**</span></span>  
  
-   [<span data-ttu-id="41dfb-108">전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="41dfb-108">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="41dfb-109">옵션</span><span class="sxs-lookup"><span data-stu-id="41dfb-109">Options</span></span>  
 <span data-ttu-id="41dfb-110">**동작**</span><span class="sxs-lookup"><span data-stu-id="41dfb-110">**Action**</span></span>  
 <span data-ttu-id="41dfb-111">수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-111">Specifies the action that you want to perform.</span></span>  
  
 <span data-ttu-id="41dfb-112">**중지 단어 추가**</span><span class="sxs-lookup"><span data-stu-id="41dfb-112">**Add stopword**</span></span>  
 <span data-ttu-id="41dfb-113">자주 사용되는 단어를 중지 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-113">Add a commonly used word to the stoplist.</span></span>  
  
 <span data-ttu-id="41dfb-114">**중지 단어 삭제**</span><span class="sxs-lookup"><span data-stu-id="41dfb-114">**Delete stopword**</span></span>  
 <span data-ttu-id="41dfb-115">중지 단어를 중지 목록에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-115">Delete a stopword from the stoplist.</span></span>  
  
 <span data-ttu-id="41dfb-116">**모든 중지 단어 삭제**</span><span class="sxs-lookup"><span data-stu-id="41dfb-116">**Delete all stopwords**</span></span>  
 <span data-ttu-id="41dfb-117">특정 언어에 대한 중지 단어를 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-117">Delete all the stopwords for a specific language.</span></span>  
  
 <span data-ttu-id="41dfb-118">**중지 목록 지우기**</span><span class="sxs-lookup"><span data-stu-id="41dfb-118">**Clear stoplist**</span></span>  
 <span data-ttu-id="41dfb-119">모든 언어에 대한 중지 단어를 모두 삭제하여 중지 목록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-119">Clear the stoplist by deleting all the stopwords for all languages.</span></span>  
  
 <span data-ttu-id="41dfb-120">**중지 단어**</span><span class="sxs-lookup"><span data-stu-id="41dfb-120">**Stopword**</span></span>  
 <span data-ttu-id="41dfb-121">**중지 단어 추가** 또는 **중지 단어 삭제**를 선택한 경우 **중지 단어** 필드에 해당 중지 단어를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-121">If you selected **Add stopword** or **Delete stopword**, enter the stopword in the **Stopword** field.</span></span> <span data-ttu-id="41dfb-122">새 중지 단어는 고유해야 합니다. 즉, 선택한 언어의 이 중지 목록에 이미 있는 중지 단어는 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-122">A new stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
 <span data-ttu-id="41dfb-123">**전체 텍스트 언어**</span><span class="sxs-lookup"><span data-stu-id="41dfb-123">**Full-text language**</span></span>  
 <span data-ttu-id="41dfb-124">**중지 단어 추가**, **중지 단어 삭제**또는 **모든 중지 단어 삭제**를 선택한 경우 목록 상자에서 중지 단어나 중지 단어의 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-124">If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box.</span></span> <span data-ttu-id="41dfb-125">이 목록 상자에는 서버 인스턴스에서 지원하는 모든 전체 텍스트 언어가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="41dfb-125">This lists all the full-text languages that are supported by the server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dfb-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41dfb-126">See Also</span></span>  
 <span data-ttu-id="41dfb-127">[fulltext_stopwords &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41dfb-127">[sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span></span>  
 <span data-ttu-id="41dfb-128">[fulltext_stoplists &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41dfb-128">[sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span></span>  
 <span data-ttu-id="41dfb-129">[전체 텍스트 검색에 대 한 중지 단어 및 중지 목록 구성 및 관리](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="41dfb-129">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="41dfb-130">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 변경](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41dfb-130">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="41dfb-131">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 만들기](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41dfb-131">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 [<span data-ttu-id="41dfb-132">DROP FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="41dfb-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
