---
title: 새 전체 텍스트 중지 목록 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: rothja
ms.author: jroth
ms.openlocfilehash: a6272fb570b85989f38c8187e29712966862710d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660134"
---
# <a name="new-full-text-stoplist-general-page"></a><span data-ttu-id="893d5-102">새 전체 텍스트 중지 목록(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="893d5-102">New Full-Text Stoplist (General Page)</span></span>
  <span data-ttu-id="893d5-103">이 대화 상자를 사용하여 전체 텍스트 중지 목록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-103">Use this dialog box to create a full-text stoplist.</span></span> <span data-ttu-id="893d5-104">*중지 목록은\*\*중지 단어*라고 하는 일반적으로 사용되는 단어 집합으로, 중지 목록을 사용하는 테이블에 대한 전체 텍스트 인덱싱에서 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-104">A *stoplist* is a set of commonly used words, called *stopwords*, that are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="893d5-105">자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](../relational-databases/search/full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="893d5-105">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="893d5-106">**SQL Server Management Studio를 사용하여 중지 목록을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="893d5-106">**To use SQL Server Management Studio to create a stoplist**</span></span>  
  
-   [<span data-ttu-id="893d5-107">전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="893d5-107">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="893d5-108">옵션</span><span class="sxs-lookup"><span data-stu-id="893d5-108">Options</span></span>  
 <span data-ttu-id="893d5-109">**전체 텍스트 중지 목록 이름**</span><span class="sxs-lookup"><span data-stu-id="893d5-109">**Full-text stoplist name**</span></span>  
 <span data-ttu-id="893d5-110">전체 텍스트 중지 목록의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-110">Enter the name of the full-text stoplist.</span></span>  
  
 <span data-ttu-id="893d5-111">**소유자**</span><span class="sxs-lookup"><span data-stu-id="893d5-111">**Owner**</span></span>  
 <span data-ttu-id="893d5-112">전체 텍스트 중지 목록의 소유자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-112">Specify the owner of the full-text stoplist.</span></span> <span data-ttu-id="893d5-113">자기 자신, 즉 현재 사용자에게 소유권을 할당하려면 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-113">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span>  
  
 <span data-ttu-id="893d5-114">다른 사용자를 지정하려면 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-114">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-stoplist-options"></a><span data-ttu-id="893d5-115">중지 목록 생성 옵션</span><span class="sxs-lookup"><span data-stu-id="893d5-115">Create stoplist options</span></span>  
 <span data-ttu-id="893d5-116">다음 생성 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-116">Click one of the following create options:</span></span>  
  
 <span data-ttu-id="893d5-117">**빈 중지 목록 만들기**</span><span class="sxs-lookup"><span data-stu-id="893d5-117">**Create an empty stoplist**</span></span>  
 <span data-ttu-id="893d5-118">새 중지 목록에 중지 단어가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-118">The new stoplist will not contain any stopwords.</span></span>  
  
 <span data-ttu-id="893d5-119">**시스템 중지 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="893d5-119">**Create from the system stoplist**</span></span>  
 <span data-ttu-id="893d5-120">[리소스 데이터베이스](../relational-databases/databases/resource-database.md)에 기본적으로 존재하는 중지 목록으로 새 중지 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-120">The new stoplist is created from the stoplist that exists by default in the [Resource database](../relational-databases/databases/resource-database.md).</span></span>  
  
 <span data-ttu-id="893d5-121">**기존 전체 텍스트 중지 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="893d5-121">**Create from an existing full-text stoplist**</span></span>  
 <span data-ttu-id="893d5-122">기존 중지 목록을 복사하여 새 중지 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-122">The new stoplist is created by copying an existing stoplist.</span></span>  
  
 <span data-ttu-id="893d5-123">**원본 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="893d5-123">**Source database**</span></span>  
 <span data-ttu-id="893d5-124">기존 중지 목록이 속하는 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-124">Specifies the name of the database to which the existing stoplist belongs.</span></span> <span data-ttu-id="893d5-125">기본적으로 현재 데이터베이스가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-125">The current database is selected by default.</span></span> <span data-ttu-id="893d5-126">필요에 따라 목록 상자에서 다른 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-126">Optionally, select a different database from the list box.</span></span>  
  
 <span data-ttu-id="893d5-127">**원본 중지 목록**</span><span class="sxs-lookup"><span data-stu-id="893d5-127">**Source stoplist**</span></span>  
 <span data-ttu-id="893d5-128">기존 중지 목록의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-128">Specifies the name of an existing stoplist.</span></span> <span data-ttu-id="893d5-129">사용 가능한 중지 목록이 나열된 목록에서 원본으로 사용할 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-129">From the list of available stoplists, select the one to use as the source.</span></span> <span data-ttu-id="893d5-130">사용 가능한 중지 목록은 개체 탐색기에 표시되는 순서대로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-130">The available stoplists are listed in the order in which they appear in Object Explorer.</span></span>  
  
 <span data-ttu-id="893d5-131">원본 중지 목록에 중지 단어로 지정된 언어가 현재 데이터베이스에 등록되지 않은 경우 CREATE FULLTEXT STOPLIST는 성공하지만 경고가 반환되고 해당 중지 단어가 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="893d5-131">If any languages specified in the stop words of the source stoplist are not registered in the current database, CREATE FULLTEXT STOPLIST succeeds, but warning(s) are returned and the corresponding stop words are not added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893d5-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893d5-132">See Also</span></span>  
 <span data-ttu-id="893d5-133">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 변경](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="893d5-133">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="893d5-134">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 만들기](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="893d5-134">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="893d5-135">[Transact-sql&#41;&#40;전체 텍스트 중지 목록 삭제](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="893d5-135">[DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="893d5-136">[전체 텍스트 검색에 대 한 중지 단어 및 중지 목록 구성 및 관리](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="893d5-136">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 [<span data-ttu-id="893d5-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="893d5-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
