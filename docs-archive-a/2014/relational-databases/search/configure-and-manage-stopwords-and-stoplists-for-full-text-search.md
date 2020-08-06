---
title: 전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 103b5024368c5ca239856580e9b45473aabf6a92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741748"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a><span data-ttu-id="92090-102">전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="92090-102">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>
  <span data-ttu-id="92090-103">전체 텍스트 인덱스가 너무 확장되지 않도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에는 검색에 도움이 되지 않지만 자주 사용되는 문자열을 무시하는 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-103">To prevent a full-text index from becoming bloated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a mechanism that discards commonly occurring strings that do not help the search.</span></span> <span data-ttu-id="92090-104">이렇게 무시된 문자열을 *중지 단어*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-104">These discarded strings are called *stopwords*.</span></span> <span data-ttu-id="92090-105">인덱스를 만드는 동안 전체 텍스트 엔진은 전체 텍스트 인덱스에서 중지 단어를 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-105">During index creation, the Full-Text Engine omits stopwords from the full-text index.</span></span> <span data-ttu-id="92090-106">즉, 전체 텍스트 쿼리는 중지 단어에서 검색하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-106">This means that full-text queries will not search on stopwords.</span></span>  
  
##  <a name="understanding-stopwords-and-stoplists"></a><a name="understand"></a><span data-ttu-id="92090-107">중지 단어 및 중지 목록 이해</span><span class="sxs-lookup"><span data-stu-id="92090-107">Understanding Stopwords and Stoplists</span></span>  
 <span data-ttu-id="92090-108">중지 단어는 특정 언어에서 의미 있는 단어이거나 언어적 의미가 없는 *토큰* 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-108">A stopword can be a word with meaning in a specific language, or it can be a *token* that does not have linguistic meaning.</span></span> <span data-ttu-id="92090-109">예를 들어 영어의 경우 "a", "and", "is" 및 "the"와 같은 단어는 검색에 도움이 되지 않으므로 전체 텍스트 인덱스에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="92090-109">For example, in the English language, words such as "a," "and," "is," and "the" are left out of the full-text index since they are known to be useless to a search.</span></span>  
  
 <span data-ttu-id="92090-110">전체 텍스트 인덱스는 중지 단어의 포함을 무시하지만 위치를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-110">Although it ignores the inclusion of stopwords, the full-text index does take into account their position.</span></span> <span data-ttu-id="92090-111">예를 들어 "Instructions are applicable to these Adventure Works Cycles models"라는 구를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-111">For example, consider the phrase, "Instructions are applicable to these Adventure Works Cycles models".</span></span> <span data-ttu-id="92090-112">다음 표에서는 이 구에서의 단어 위치를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-112">The following table depicts the position of the words in the phrase:</span></span>  
  
|<span data-ttu-id="92090-113">단어</span><span class="sxs-lookup"><span data-stu-id="92090-113">Word</span></span>|<span data-ttu-id="92090-114">위치</span><span class="sxs-lookup"><span data-stu-id="92090-114">Position</span></span>|  
|----------|--------------|  
|<span data-ttu-id="92090-115">Instructions</span><span class="sxs-lookup"><span data-stu-id="92090-115">Instructions</span></span>|<span data-ttu-id="92090-116">1</span><span class="sxs-lookup"><span data-stu-id="92090-116">1</span></span>|  
|<span data-ttu-id="92090-117">are</span><span class="sxs-lookup"><span data-stu-id="92090-117">are</span></span>|<span data-ttu-id="92090-118">2</span><span class="sxs-lookup"><span data-stu-id="92090-118">2</span></span>|  
|<span data-ttu-id="92090-119">applicable</span><span class="sxs-lookup"><span data-stu-id="92090-119">applicable</span></span>|<span data-ttu-id="92090-120">3</span><span class="sxs-lookup"><span data-stu-id="92090-120">3</span></span>|  
|<span data-ttu-id="92090-121">다음으로 변경:</span><span class="sxs-lookup"><span data-stu-id="92090-121">to</span></span>|<span data-ttu-id="92090-122">4</span><span class="sxs-lookup"><span data-stu-id="92090-122">4</span></span>|  
|<span data-ttu-id="92090-123">these</span><span class="sxs-lookup"><span data-stu-id="92090-123">these</span></span>|<span data-ttu-id="92090-124">5</span><span class="sxs-lookup"><span data-stu-id="92090-124">5</span></span>|  
|<span data-ttu-id="92090-125">Adventure</span><span class="sxs-lookup"><span data-stu-id="92090-125">Adventure</span></span>|<span data-ttu-id="92090-126">6</span><span class="sxs-lookup"><span data-stu-id="92090-126">6</span></span>|  
|<span data-ttu-id="92090-127">Works</span><span class="sxs-lookup"><span data-stu-id="92090-127">Works</span></span>|<span data-ttu-id="92090-128">7</span><span class="sxs-lookup"><span data-stu-id="92090-128">7</span></span>|  
|<span data-ttu-id="92090-129">Cycles</span><span class="sxs-lookup"><span data-stu-id="92090-129">Cycles</span></span>|<span data-ttu-id="92090-130">8</span><span class="sxs-lookup"><span data-stu-id="92090-130">8</span></span>|  
|<span data-ttu-id="92090-131">모델</span><span class="sxs-lookup"><span data-stu-id="92090-131">models</span></span>|<span data-ttu-id="92090-132">9</span><span class="sxs-lookup"><span data-stu-id="92090-132">9</span></span>|  
  
 <span data-ttu-id="92090-133">위치 2, 4, 5에 있는 중지 단어 "are", "to", "these"는 전체 텍스트 인덱스에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="92090-133">The stopwords "are", "to", and "these" that are in positions 2, 4, and 5 are left out of the full-text index.</span></span> <span data-ttu-id="92090-134">그러나 해당 위치 정보는 유지되므로 구의 다른 단어 위치에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-134">However, their positional information is maintained, thereby leaving the position of the other words in the phrase unaffected.</span></span>  
  
 <span data-ttu-id="92090-135">중지 단어는 데이터베이스에서 중지 목록이라는 개체를 사용하여 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="92090-135">Stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="92090-136">*중지 목록* 은 전체 텍스트 인덱스와 연결된 경우 해당 인덱스의 전체 텍스트 쿼리에 적용되는 중지 단어 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="92090-136">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span>  
  
  
##  <a name="creating-a-stoplist"></a><a name="creating"></a><span data-ttu-id="92090-137">중지 목록 만들기</span><span class="sxs-lookup"><span data-stu-id="92090-137">Creating a Stoplist</span></span>  
 <span data-ttu-id="92090-138">다음과 같은 방법으로 중지 목록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-138">You can create a stoplist in any of the following ways:</span></span>  
  
-   <span data-ttu-id="92090-139">데이터베이스에서 시스템 제공 중지 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-139">Using the system-supplied stoplist in the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="92090-140">에서는 지원되는 각 언어, 즉 기본적으로 지정된 단어 분리기와 연결된 모든 언어에서 가장 일반적으로 사용되는 중지 단어가 포함된 시스템 중지 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-140">ships with a system stoplist that contains the most commonly used stopwords for each supported language, that is for every language that is associated with given word breakers by default.</span></span> <span data-ttu-id="92090-141">시스템 중지 목록에는 지원되는 모든 언어의 일반적인 중지 단어가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="92090-141">The system stoplist contains common stopwords for all supported languages.</span></span>  <span data-ttu-id="92090-142">시스템 중지 목록 사본을 만들고 여기에서 중지 단어를 추가 및 제거하여 사본을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-142">You can copy the system stoplist, and customize your copy by adding and removing stopwords.</span></span>  
  
     <span data-ttu-id="92090-143">시스템 중지 목록은 [리소스](../databases/resource-database.md) 데이터베이스에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="92090-143">The system stoplist is installed in the [Resource](../databases/resource-database.md) database.</span></span>  
  
-   <span data-ttu-id="92090-144">고유한 중지 목록을 만든 다음 여기에 지정한 모든 언어의 중지 단어를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-144">Creating your own stoplist, and then adding stopwords to it for any language that you specify.</span></span> <span data-ttu-id="92090-145">필요하면 중지 목록에서 중지 단어를 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-145">You can also drop stopwords from your stoplist when necessary.</span></span>  
  
-   <span data-ttu-id="92090-146">현재 서버 인스턴스에서 다른 데이터베이스의 기존 사용자 지정 중지 목록을 사용한 후 필요에 따라 중지 단어를 추가 및 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-146">Using an existing custom stoplist from any other database in the current server instance and then adding and dropping stopwords as necessary.</span></span>  
  
 <span data-ttu-id="92090-147">**중지 목록을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="92090-147">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="92090-148">CREATE FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a><span data-ttu-id="92090-149">Management Studio에서 전체 텍스트 중지 목록을 만들려면</span><span class="sxs-lookup"><span data-stu-id="92090-149">To create a full-text stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="92090-150">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-150">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="92090-151">**데이터베이스**를 확장한 다음 전체 텍스트 중지 목록을 만들려는 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-151">Expand **Databases**, and then expand the database in which you want to create the full-text stoplist.</span></span>  
  
3.  <span data-ttu-id="92090-152">**스토리지**를 확장한 다음 **전체 텍스트 중지 목록**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-152">Expand **Storage**, and then right-click **Full-Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="92090-153">**새 전체 텍스트 중지 목록**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-153">Select **New Full-Text Stoplist**.</span></span>  
  
5.  <span data-ttu-id="92090-154">중지 목록 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-154">Specify the stoplist name.</span></span>  
  
6.  <span data-ttu-id="92090-155">필요에 따라 중지 목록 소유자로 다른 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-155">Optionally, specify someone else as the stoplist owner.</span></span>  
  
7.  <span data-ttu-id="92090-156">다음 중지 목록 생성 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-156">Select one of the following create stoplist options:</span></span>  
  
    -   <span data-ttu-id="92090-157">**빈 중지 목록 만들기**</span><span class="sxs-lookup"><span data-stu-id="92090-157">**Create an empty stoplist**</span></span>  
  
    -   <span data-ttu-id="92090-158">**시스템 중지 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="92090-158">**Create from the system stoplist**</span></span>  
  
    -   <span data-ttu-id="92090-159">**기존 전체 텍스트 중지 목록에서 만들기**</span><span class="sxs-lookup"><span data-stu-id="92090-159">**Create from an existing full-text stoplist**</span></span>  
  
     <span data-ttu-id="92090-160">자세한 내용은 [새 전체 텍스트 중지 목록&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92090-160">For more information, see [New Full-Text Stoplist &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="92090-161">**중지 목록을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="92090-161">**To drop a stoplist**</span></span>  
  
-   [<span data-ttu-id="92090-162">DROP FULLTEXT STOPLIST&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="using-a-stoplist-in-full-text-queries"></a><a name="queries"></a><span data-ttu-id="92090-163">전체 텍스트 쿼리에서 중지 목록 사용</span><span class="sxs-lookup"><span data-stu-id="92090-163">Using a Stoplist in Full-Text Queries</span></span>  
 <span data-ttu-id="92090-164">쿼리에서 중지 목록을 사용하려면 해당 중지 목록을 전체 텍스트 인덱스와 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-164">To make use of a stoplist in queries, you must associate it with a full-text index.</span></span> <span data-ttu-id="92090-165">인덱스를 만들 때 중지 목록을 전체 텍스트 인덱스에 연결하거나 나중에 인덱스를 변경하여 중지 목록을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-165">You can attach a stoplist to a full-text index when you create the index, or you can alter the index later to add a stoplist.</span></span>  
  
 <span data-ttu-id="92090-166">**전체 텍스트 인덱스를 만들고 중지 목록과 연결하려면**</span><span class="sxs-lookup"><span data-stu-id="92090-166">**To create a full-text index and associate a stoplist with it**</span></span>  
  
-   [<span data-ttu-id="92090-167">CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 <span data-ttu-id="92090-168">**중지 목록을 기존 전체 텍스트 인덱스와 연결하거나 연결을 끊으려면**</span><span class="sxs-lookup"><span data-stu-id="92090-168">**To associate or disassociate a stoplist with an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="92090-169">ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 <span data-ttu-id="92090-170">**중지 단어로 인해 전체 텍스트 쿼리에 대한 부울 연산이 실패할 경우 오류 메시지를 표시하지 않으려면**</span><span class="sxs-lookup"><span data-stu-id="92090-170">**To suppress an error message if stopwords cause a Boolean operation on a full-text query to fail**</span></span>  
  
-   [<span data-ttu-id="92090-171">transform noise words 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="92090-171">transform noise words Server Configuration Option</span></span>](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing-stoplists-and-stoplist-metadata"></a><a name="viewing"></a><span data-ttu-id="92090-172">중지 목록 및 중지 목록 메타 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="92090-172">Viewing Stoplists and Stoplist Metadata</span></span>  
 <span data-ttu-id="92090-173">**중지 목록의 모든 중지 단어를 보려면**</span><span class="sxs-lookup"><span data-stu-id="92090-173">**To view all the stopwords of a stoplist**</span></span>  
  
-   [<span data-ttu-id="92090-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="92090-175">**현재 데이터베이스에 있는 모든 중지 목록에 대한 정보를 얻으려면**</span><span class="sxs-lookup"><span data-stu-id="92090-175">**To get information about all the stoplists in the current database**</span></span>  
  
-   [<span data-ttu-id="92090-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="92090-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="92090-178">**단어 분리기, 동의어 사전 및 중지 목록 조합의 토큰화 결과를 보려면**</span><span class="sxs-lookup"><span data-stu-id="92090-178">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="92090-179">dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-179">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="changing-the-stopwords-in-a-stoplist"></a><a name="change"></a><span data-ttu-id="92090-180">중지 목록에서 중지 단어 변경</span><span class="sxs-lookup"><span data-stu-id="92090-180">Changing the Stopwords in a Stoplist</span></span>  
 <span data-ttu-id="92090-181">**중지 목록에서 중지 단어를 추가 또는 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="92090-181">**To add or drop stopwords from a stoplist**</span></span>  
  
-   [<span data-ttu-id="92090-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92090-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a><span data-ttu-id="92090-183">Management Studio에서 중지 목록의 중지 단어를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="92090-183">To change the stopwords in a stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="92090-184">개체 탐색기에서 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-184">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="92090-185">**데이터베이스**를 확장한 다음 해당 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-185">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="92090-186">**스토리지**를 확장한 다음 **전체 텍스트 중지 목록**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-186">Expand **Storage**, and then select **Full Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="92090-187">변경할 속성이 있는 중지 목록을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-187">Right-click the stoplist whose properties you want to change, and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="92090-188">[전체 텍스트 중지 목록 속성](../../database-engine/full-text-stoplist-properties.md) 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-188">In the [Full-Text Stoplist Properties](../../database-engine/full-text-stoplist-properties.md) dialog box:</span></span>  
  
    1.  <span data-ttu-id="92090-189">**동작** 목록 상자에서 **중지 단어 추가**, **중지 단어 삭제**, **모든 중지 단어 삭제**또는 **중지 목록 지우기**동작 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-189">In the **Action** list box, select one of the following actions: **Add stopword**, **Delete stopword**, **Delete all stopwords**, or **Clear stoplist**.</span></span>  
  
    2.  <span data-ttu-id="92090-190">선택한 동작에 대해 **중지 단어** 입력란이 활성화되면 단일 중지 단어를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-190">If the **Stopword** text box is enabled for the selected action, enter a single stopword.</span></span> <span data-ttu-id="92090-191">이 중지 단어는 고유해야 합니다. 즉, 선택한 언어의 이 중지 목록에 이미 있는 중지 단어는 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-191">This stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
    3.  <span data-ttu-id="92090-192">선택한 동작에 대해 **전체 텍스트 언어** 목록 상자가 활성화되면 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92090-192">If the **Full-text language** list box is enabled for the selected action, select a language.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrading-noise-words-from-sql-server-2005"></a><a name="upgrade"></a><span data-ttu-id="92090-193">SQL Server 2005에서 의미 없는 단어 업그레이드</span><span class="sxs-lookup"><span data-stu-id="92090-193">Upgrading Noise Words from SQL Server 2005</span></span>  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="92090-194">의 의미 없는 단어가 중지 단어로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-194">noise words have been replaced by stopwords.</span></span> <span data-ttu-id="92090-195">데이터베이스를 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에서 업그레이드하면 의미 없는 단어 파일이 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-195">When a database is upgraded from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the noise-word files are no longer used.</span></span> <span data-ttu-id="92090-196">그러나 의미 없는 단어 파일이 FTDATA\ FTNoiseThesaurusBak 폴더에 저장되므로 나중에 해당 중지 목록을 업데이트하거나 새로 작성할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92090-196">However, the noise-word files are stored in the FTDATA\ FTNoiseThesaurusBak folder, and you can use them later when updating or building the corresponding stoplists.</span></span> <span data-ttu-id="92090-197">의미 없는 단어 파일을 중지 목록으로 업그레이드하는 방법은 [전체 텍스트 검색 업그레이드](upgrade-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92090-197">For information about upgrading noise-word files to stoplists, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
  
  
