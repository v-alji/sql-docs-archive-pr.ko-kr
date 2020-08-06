---
title: MSSQLSERVER_30053 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d6262f93ef3dbbc9834053f864046b4dca30f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651033"
---
# <a name="mssqlserver_30053"></a><span data-ttu-id="a39af-102">MSSQLSERVER_30053</span><span class="sxs-lookup"><span data-stu-id="a39af-102">MSSQLSERVER_30053</span></span>
    
## <a name="details"></a><span data-ttu-id="a39af-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a39af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a39af-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a39af-104">Product Name</span></span>|<span data-ttu-id="a39af-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a39af-105">SQL Server</span></span>|  
|<span data-ttu-id="a39af-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a39af-106">Event ID</span></span>|<span data-ttu-id="a39af-107">30053</span><span class="sxs-lookup"><span data-stu-id="a39af-107">30053</span></span>|  
|<span data-ttu-id="a39af-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a39af-108">Event Source</span></span>|<span data-ttu-id="a39af-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a39af-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a39af-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a39af-110">Component</span></span>|<span data-ttu-id="a39af-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a39af-111">SQLEngine</span></span>|  
|<span data-ttu-id="a39af-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a39af-112">Symbolic Name</span></span>|<span data-ttu-id="a39af-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a39af-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span></span>|  
|<span data-ttu-id="a39af-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a39af-114">Message Text</span></span>|<span data-ttu-id="a39af-115">전체 텍스트 쿼리 문자열의 단어 분리 작업이 시간을 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-115">Word breaking timed out for the full-text query string.</span></span> <span data-ttu-id="a39af-116">단어 분리기에서 전체 텍스트 쿼리 문자열을 처리하는 데 오랜 시간이 걸리거나 서버에서 많은 쿼리가 실행되는 경우 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-116">This can happen if the wordbreaker took a long time to process the full-text query string, or if a large number of queries are running on the server.</span></span> <span data-ttu-id="a39af-117">부하를 줄여 쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-117">Try running the query again under a lighter load.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a39af-118">설명</span><span class="sxs-lookup"><span data-stu-id="a39af-118">Explanation</span></span>  
 <span data-ttu-id="a39af-119">다음과 같은 경우 단어 분리 시간 초과 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-119">A word-breaking timeout error can occur in the following situations:</span></span>  
  
-   <span data-ttu-id="a39af-120">쿼리 언어용 단어 분리기가 올바르지 않게 구성된 경우. 해당 레지스트리 설정이 올바르지 않은 경우가 이에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-120">The word breaker for the query language is configured incorrectly; for example, its registry settings are incorrect.</span></span>  
  
-   <span data-ttu-id="a39af-121">특정 쿼리 문자열에 대해 단어 분리기가 제대로 작동하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-121">The word breaker malfunctions for a specific query string.</span></span>  
  
-   <span data-ttu-id="a39af-122">특정 쿼리 문자열에 대해 단어 분리기가 너무 많은 데이터를 반환하는 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-122">The word breaker returns too much data for a specific query string.</span></span> <span data-ttu-id="a39af-123">데이터가 지나치게 많으면 버퍼 오버런 공격으로 간주되어 단어 분리 서비스를 호스팅하는 필터 데몬 프로세스(fdhost.exe)가 종료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-123">Excess data is treated as a potential buffer overrun attack, and shuts down the filter daemon process (fdhost.exe), which hosts the word-breaking services.</span></span>  
  
-   <span data-ttu-id="a39af-124">필터 데몬 프로세스 구성이 올바르지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-124">The filter daemon process configuration is incorrect.</span></span>  
  
     <span data-ttu-id="a39af-125">가장 일반적인 구성 문제는 암호 만료나 필터 데몬 계정이 로그온하지 못하도록 하는 도메인 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-125">The most common configuration problems are password expiration or a domain policy that prevents the filter daemon account from logging on.</span></span>  
  
-   <span data-ttu-id="a39af-126">서버 인스턴스에서 실행되는 쿼리 작업의 양이 너무 많은 경우. 단어 분리기에서 전체 텍스트 쿼리 문자열을 처리하는 데 오랜 시간이 걸리거나 서버에서 많은 쿼리가 실행되는 경우가 이에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-126">A very heavy query workload is running on the server instance; for example, the word-breaker took a long time to process the full-text query string, or a large number of queries are running on the server.</span></span> <span data-ttu-id="a39af-127">이는 가능성이 가장 낮은 원인입니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-127">Note that this is the least likely cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a39af-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a39af-128">User Action</span></span>  
 <span data-ttu-id="a39af-129">다음과 같이 시간 초과 문제의 가능한 원인에 적합한 사용자 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-129">Select the user action that is appropriate to the probable cause of the timeout, as follows:</span></span>  
  
|<span data-ttu-id="a39af-130">가능한 원인:</span><span class="sxs-lookup"><span data-stu-id="a39af-130">Probable cause</span></span>|<span data-ttu-id="a39af-131">사용자 조치</span><span class="sxs-lookup"><span data-stu-id="a39af-131">User action</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a39af-132">쿼리 언어용 단어 분리기가 올바르지 않게 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-132">The word breaker for the query language is configured incorrectly.</span></span>|<span data-ttu-id="a39af-133">타사 단어 분리기를 사용할 경우 운영 체제에 올바르지 않게 등록되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39af-133">If you are using a third-party word breaker it might be incorrectly registered with the operating system.</span></span> <span data-ttu-id="a39af-134">이 경우 단어 분리기를 다시 등록하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-134">In this case, re-register the word breaker.</span></span> <span data-ttu-id="a39af-135">자세한 내용은 [검색에 사용된 단어 분리기를 이전 버전으로 되돌리기](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a39af-135">For more information, see [Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).</span></span>|  
|<span data-ttu-id="a39af-136">특정 쿼리 문자열에 대해 단어 분리기가 제대로 작동하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-136">The word breaker malfunctions for a specific query string.</span></span>|<span data-ttu-id="a39af-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되는 단어 분리기의 경우 Microsoft 고객 서비스 지원 센터에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-137">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="a39af-138">특정 쿼리 문자열에 대해 단어 분리기가 너무 많은 데이터를 반환하는 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-138">The word breaker returns too much data for a specific query string.</span></span>|<span data-ttu-id="a39af-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되는 단어 분리기의 경우 Microsoft 고객 서비스 지원 센터에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-139">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="a39af-140">필터 데몬 프로세스 구성이 올바르지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-140">The filter daemon process configuration is incorrect.</span></span>|<span data-ttu-id="a39af-141">현재 암호를 사용 중이고 도메인 정책에서 필터 데몬 계정 로그온을 차단하고 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-141">Ensure that you are using the current password and that a domain policy is not preventing the filter daemon account from logging on.</span></span>|  
|<span data-ttu-id="a39af-142">서버에서 실행되는 쿼리 작업의 양이 너무 많은 경우</span><span class="sxs-lookup"><span data-stu-id="a39af-142">A very heavy query workload is running on the server instance.</span></span>|<span data-ttu-id="a39af-143">부하를 줄여 쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="a39af-143">Try running the query again under a lighter load.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a39af-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a39af-144">See Also</span></span>  
 <span data-ttu-id="a39af-145">[전체 텍스트 필터 데몬 시작 관리자에 대 한 서비스 계정 설정](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="a39af-145">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="a39af-146">[전체 텍스트 검색](../search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="a39af-146">[Full-Text Search](../search/full-text-search.md) </span></span>  
 <span data-ttu-id="a39af-147">[Transact-sql&#41;sp_help_fulltext_system_components &#40;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a39af-147">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="a39af-148">[검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="a39af-148">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="a39af-149">검색 필터 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="a39af-149">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
