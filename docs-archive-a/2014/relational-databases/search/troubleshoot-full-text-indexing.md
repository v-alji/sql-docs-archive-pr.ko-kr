---
title: 전체 텍스트 인덱싱 문제 해결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eaca5fcf2dfbac57fc6d3ba6178251927d15aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660981"
---
# <a name="troubleshoot-full-text-indexing"></a><span data-ttu-id="1290f-102">전체 텍스트 인덱싱 문제 해결</span><span class="sxs-lookup"><span data-stu-id="1290f-102">Troubleshoot Full-Text Indexing</span></span>
     
##  <a name="troubleshoot-full-text-indexing-failures"></a><a name="failure"></a> <span data-ttu-id="1290f-103">전체 텍스트 인덱싱 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="1290f-103">Troubleshoot Full-Text Indexing Failures</span></span>  
 <span data-ttu-id="1290f-104">전체 텍스트 인덱스를 채우거나 유지 관리하는 동안 전체 텍스트 인덱서는 아래에서 설명하는 이유로 인해 하나 이상의 행을 인덱싱하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-104">While populating or maintaining a full-text index, the full-text indexer, for reasons described below, might fail to index one or more rows.</span></span> <span data-ttu-id="1290f-105">이러한 행 수준 오류가 발생해도 채우기는 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-105">These row-level errors do not prevent the population from completing.</span></span> <span data-ttu-id="1290f-106">그러나 인덱서가 이러한 행을 건너뛰므로 이러한 행에 포함된 내용은 쿼리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-106">The indexer skips these rows, which means that you are not able to query for content contained in these rows.</span></span>  
  
 <span data-ttu-id="1290f-107">인덱싱 오류는 다음과 같은 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-107">Indexing failures can occur when:</span></span>  
  
-   <span data-ttu-id="1290f-108">인덱서가 필터 또는 단어 분리기 구성 요소를 찾거나 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-108">The indexer cannot find or load a filter or word breaker component.</span></span> <span data-ttu-id="1290f-109">이 오류는 테이블 행에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 등록되지 않은 언어로 된 문서 내용이나 문서 형식이 포함되어 있는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-109">This failure can occur if the table row contains a document format or content in a language that has not been registered with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1290f-110">등록된 단어 분리기 또는 필터 구성 요소에 서명하지 않았거나 로드 시 서명 확인에 실패하는 경우에도 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-110">This failure can also happen if the registered word breaker or filter component was not signed or failed signature verification when it was being loaded.</span></span>  
  
-   <span data-ttu-id="1290f-111">단어 분리기 또는 필터와 같은 구성 요소가 실패하거나 인덱서에 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-111">A component, such as a word breaker or filter, fails and returns an error to the indexer.</span></span> <span data-ttu-id="1290f-112">이 오류는 인덱싱 중인 문서가 손상되어 필터가 문서에서 텍스트를 추출할 수 없는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-112">This can happen if the document being indexed is corrupt and the filter is unable to extract text from the document.</span></span> <span data-ttu-id="1290f-113">전체 텍스트 필터 데몬 호스트(fdhost.exe)의 메모리 제한으로 인해 특정 크기를 초과하는 단일 행의 내용을 처리할 수 없는 경우에도 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-113">This can also occur when a component is unable to handle the content of a single row above a certain size, due to memory limits on the full-text filter daemon host (fdhost.exe).</span></span>  
  
 <span data-ttu-id="1290f-114">각 행 수준 오류의 경우 탐색 로그를 통해 오류 원인에 대한 자세한 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-114">For each row-level failure, the crawl log contains details on the reason for the failure.</span></span> <span data-ttu-id="1290f-115">오류 수는 전체 또는 증분 채우기 완료 시 요약 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-115">The error counts are summarized at the end of a full or incremental population.</span></span>  
  
 <span data-ttu-id="1290f-116">인덱싱 프로세스 자체에 영향을 주어 채우기를 완료할 수 없는 오류도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-116">There are other failures that can impact the indexing process itself and prevent the population from completing:</span></span>  
  
-   <span data-ttu-id="1290f-117">전체 텍스트 인덱스가 전체 텍스트 카탈로그에 포함될 수 있는 행 수에 대한 제한을 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-117">The full-text index exceeds the limit for the number of rows that can be contained in a full-text catalog.</span></span>  
  
-   <span data-ttu-id="1290f-118">인덱싱 중인 테이블에 있는 클러스터형 인덱스 또는 전체 텍스트 키 인덱스가 변경, 삭제 또는 다시 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-118">A clustered index or full-text key index on the table being indexed gets altered, dropped, or rebuilt.</span></span>  
  
-   <span data-ttu-id="1290f-119">하드웨어 오류 또는 디스크 손상으로 인해 전체 텍스트 카탈로그가 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-119">A hardware failure or disk corruption results in the corruption of the full-text catalog.</span></span>  
  
-   <span data-ttu-id="1290f-120">전체 텍스트 인덱싱 중인 테이블을 포함하는 파일 그룹이 오프라인 상태가 되거나 읽기 전용으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-120">A file group that contains the table being full-text indexed goes offline, or is made read-only.</span></span>  
  
 <span data-ttu-id="1290f-121">중요한 전체 텍스트 인덱스 채우기 작업을 완료한 다음이나 채우기가 완료되지 않은 경우 탐색 로그를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-121">You should view the crawl log at the end of any significant full-text index population operation, or when you find that a population did not complete.</span></span>  
  
### <a name="unsigned-components"></a><span data-ttu-id="1290f-122">서명되지 않은 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1290f-122">Unsigned Components</span></span>  
 <span data-ttu-id="1290f-123">기본적으로 전체 텍스트 인덱서를 사용하려면 로드하는 필터 및 단어 분리기에 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-123">By default, the full-text indexer requires the filters and word breakers that it loads to be signed.</span></span> <span data-ttu-id="1290f-124">일부 사용자 지정 구성 요소 설치 시에서와 같이 구성 요소를 서명하지 않는 경우에는 전체 텍스트 인덱서가 서명 확인을 무시하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-124">If they are not signed, which is the case sometimes when custom components are installed, you must configure the full-text indexer to ignore signature verification.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1290f-125">서명 확인을 무시하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 보안 수준이 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-125">Ignoring signature verification makes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] less secure.</span></span> <span data-ttu-id="1290f-126">구현하는 모든 구성 요소에 서명하거나 가져오는 모든 구성 요소에 서명이 되어 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-126">We recommend that you sign any components that you implement or ensure that any components that you acquire are signed.</span></span> <span data-ttu-id="1290f-127">구성 요소에 서명하는 방법은 [sp_fulltext_service&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1290f-127">For information about signing components, see [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  

  
##  <a name="full-text-index-in-inconsistent-state-after-transaction-log-restored"></a><a name="state"></a> <span data-ttu-id="1290f-128">트랜잭션 로그가 복원된 후 일관성 없는 상태의 전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="1290f-128">Full-Text Index in Inconsistent State after Transaction Log Restored</span></span>  
 <span data-ttu-id="1290f-129">데이터베이스의 트랜잭션 로그를 복원할 때 전체 텍스트 인덱스에 일관성이 없다는 경고가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-129">When restoring the transaction log of a database, you might see a warning indicating that the full-text index is not in a consistent state.</span></span> <span data-ttu-id="1290f-130">이는 데이터베이스가 백업된 후 테이블에 대한 전체 텍스트 인덱스가 수정되었기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-130">The reason for this is that the full-text index on a table was modified after the database was backed up.</span></span> <span data-ttu-id="1290f-131">전체 텍스트 인덱스를 일관성 있게 구성하려면 해당 테이블에 대해 전체 채우기(탐색)를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1290f-131">To bring the full-text index to a consistent state, you must run a full population (crawl) on the table.</span></span> <span data-ttu-id="1290f-132">자세한 내용은 [전체 텍스트 인덱스 채우기](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1290f-132">For more information, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="1290f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1290f-133">See Also</span></span>  
 <span data-ttu-id="1290f-134">[ALTER FULLTEXT CATALOG&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1290f-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="1290f-135">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="1290f-135">Populate Full-Text Indexes</span></span>](../indexes/indexes.md)  
  
  
