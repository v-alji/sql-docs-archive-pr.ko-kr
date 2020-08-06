---
title: MSSQLSERVER_30089 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0b9c71ea620174f993ae87befed8a21bb3d0bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651028"
---
# <a name="mssqlserver_30089"></a><span data-ttu-id="b33d1-102">MSSQLSERVER_30089</span><span class="sxs-lookup"><span data-stu-id="b33d1-102">MSSQLSERVER_30089</span></span>
    
## <a name="details"></a><span data-ttu-id="b33d1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b33d1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b33d1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b33d1-104">Product Name</span></span>|<span data-ttu-id="b33d1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b33d1-105">SQL Server</span></span>|  
|<span data-ttu-id="b33d1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b33d1-106">Event ID</span></span>|<span data-ttu-id="b33d1-107">30089</span><span class="sxs-lookup"><span data-stu-id="b33d1-107">30089</span></span>|  
|<span data-ttu-id="b33d1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b33d1-108">Event Source</span></span>|<span data-ttu-id="b33d1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b33d1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b33d1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b33d1-110">Component</span></span>|<span data-ttu-id="b33d1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b33d1-111">SQLEngine</span></span>|  
|<span data-ttu-id="b33d1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b33d1-112">Symbolic Name</span></span>|<span data-ttu-id="b33d1-113">IFTS_FDHOST_TERMINATEDABNORMAL</span><span class="sxs-lookup"><span data-stu-id="b33d1-113">IFTS_FDHOST_TERMINATEDABNORMAL</span></span>|  
|<span data-ttu-id="b33d1-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b33d1-114">Message Text</span></span>|<span data-ttu-id="b33d1-115">전체 텍스트 필터 데몬 호스트(FDHost) 프로세스가 비정상적으로 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-115">The fulltext filter daemon host (FDHost) process has stopped abnormally.</span></span> <span data-ttu-id="b33d1-116">전체 텍스트 인덱싱 또는 쿼리 처리 작업을 수행하는 동안 단어 분리기, 형태소 분석기 또는 필터와 같은 언어 구성 요소가 잘못 구성되었거나 제대로 작동하지 않아 오류가 발생한 경우일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-116">This can occur if an incorrectly configured or malfunctioning linguistic component, such as a wordbreaker, stemmer or filter has caused an irrecoverable error during full-text indexing or query processing.</span></span> <span data-ttu-id="b33d1-117">프로세스는 자동으로 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-117">The process will be restarted automatically.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b33d1-118">설명</span><span class="sxs-lookup"><span data-stu-id="b33d1-118">Explanation</span></span>  
 <span data-ttu-id="b33d1-119">전체 텍스트 필터 데몬 호스트에서 오류가 발생하여 비정상적으로 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-119">The full-text filter daemon host has encountered some problem that has forced it to stop abnormally.</span></span> <span data-ttu-id="b33d1-120">문제의 원인은 잘못된 형식의 문서, 필터나 단어 분리기의 버그, 필터 데몬의 문제일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-120">The cause of the problem could be a badly formatted document, a bug in the filter or word-breaker, or a problem in filter daemon.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b33d1-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b33d1-121">User Action</span></span>  
 <span data-ttu-id="b33d1-122">일반적으로 데몬이 오류를 복구하지만</span><span class="sxs-lookup"><span data-stu-id="b33d1-122">Typically, the daemon will recover from the error.</span></span> <span data-ttu-id="b33d1-123">문제가 지속되면 이를 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-123">If it is consistently failing, troubleshooting is necessary.</span></span> <span data-ttu-id="b33d1-124">다음 방법을 사용하여 문제를 해결해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="b33d1-124">Try the following to isolate the issue:</span></span>  
  
1.  <span data-ttu-id="b33d1-125">최근에 새로운 언어 구성 요소를 설치한 경우 시스템에서 이를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-125">If a new linguistic component has been installed recently, remove it from the system.</span></span>  
  
2.  <span data-ttu-id="b33d1-126">탐색 로그를 보고 전체 텍스트 인덱스에 실패한 새 문서가 있는지 확인한 후 이를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b33d1-126">Look at the crawl log to identify any new document that failed to be full-text indexed, and remove it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b33d1-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b33d1-127">See Also</span></span>  
 <span data-ttu-id="b33d1-128">[Transact-sql&#41;sp_help_fulltext_system_components &#40;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b33d1-128">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="b33d1-129">[검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="b33d1-129">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="b33d1-130">검색 필터 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="b33d1-130">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
