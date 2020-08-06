---
title: MSSQL_ENG020598 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730511"
---
# <a name="mssql_eng020598"></a><span data-ttu-id="87a77-102">MSSQL_ENG020598</span><span class="sxs-lookup"><span data-stu-id="87a77-102">MSSQL_ENG020598</span></span>
    
## <a name="message-details"></a><span data-ttu-id="87a77-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="87a77-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87a77-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="87a77-104">Product Name</span></span>|<span data-ttu-id="87a77-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="87a77-105">SQL Server</span></span>|  
|<span data-ttu-id="87a77-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="87a77-106">Event ID</span></span>|<span data-ttu-id="87a77-107">20598</span><span class="sxs-lookup"><span data-stu-id="87a77-107">20598</span></span>|  
|<span data-ttu-id="87a77-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="87a77-108">Event Source</span></span>|<span data-ttu-id="87a77-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="87a77-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="87a77-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="87a77-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="87a77-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="87a77-111">Symbolic Name</span></span>||  
|<span data-ttu-id="87a77-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="87a77-112">Message Text</span></span>|<span data-ttu-id="87a77-113">복제된 명령을 적용하는 동안 구독자에서 행을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-113">The row was not found at the Subscriber when applying the replicated command.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87a77-114">설명</span><span class="sxs-lookup"><span data-stu-id="87a77-114">Explanation</span></span>  
 <span data-ttu-id="87a77-115">배포 에이전트가 구독자에서 행을 업데이트하려고 하지만 해당 행이 삭제되었거나 해당 행의 기본 키가 변경된 경우 트랜잭션 복제에서 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-115">This error is raised in transactional replication if the Distribution Agent attempts to update a row at the Subscriber, but the row has been deleted or the primary key of the row has been changed.</span></span> <span data-ttu-id="87a77-116">기본적으로 변경 내용은 게시자로 다시 전파되지 않기 때문에 트랜잭션 게시에 대한 구독자는 읽기 전용으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-116">By default, Subscribers to transactional publications should be treated as read-only, because changes are not propagated back to the Publisher.</span></span> <span data-ttu-id="87a77-117">트랜잭션 복제의 경우 업데이트할 수 있는 구독이나 피어 투 피어 복제를 사용하는 경우에만 사용자가 구독자에서 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-117">For transactional replication, user changes should be made at the Subscriber only if updatable subscriptions or peer-to-peer replication is used.</span></span> <span data-ttu-id="87a77-118">이러한 옵션에 대한 자세한 내용은 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) 및 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="87a77-118">For information about these options, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) and [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87a77-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="87a77-119">User Action</span></span>  
 <span data-ttu-id="87a77-120">**이 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="87a77-120">**To resolve this problem:**</span></span>  
  
1.  <span data-ttu-id="87a77-121">오류 원인을 식별하는 동안 복제가 계속되어야 하는 경우 배포 에이전트에 매개 변수 **-SkipErrors 20598** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-121">If replication must continue while you identify the source of the error, specify the parameter **-SkipErrors 20598** for the Distribution Agent.</span></span> <span data-ttu-id="87a77-122">이렇게 하면 에이전트는 오류 20598이 발생한 변경 내용을 건너뛰고 다른 변경 내용을 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-122">This allows the agent to skip changes that result in error 20598, while allowing other changes to be replicated.</span></span>  
  
2.  <span data-ttu-id="87a77-123">구독자에서 삭제되었거나 기본 키가 게시자의 해당 행과 일치하지 않는 행을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-123">Identify which rows at the Subscriber have been deleted or have a different primary key than the corresponding rows at the Publisher.</span></span> <span data-ttu-id="87a77-124">[tablediff Utility](../../tools/tablediff-utility.md) 를 사용하여 게시 및 구독 데이터베이스에서 일치하지 않는 행을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-124">You can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span> <span data-ttu-id="87a77-125">복제된 데이터베이스에서 이 유틸리티를 사용하는 방법은 [복제된 테이블의 차이점 비교&#40;복제 프로그래밍&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a77-125">For information about using this utility with replicated databases, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).</span></span>  
  
3.  <span data-ttu-id="87a77-126">**tablediff** 유틸리티나 다른 방법을 사용하여 구독자에서 행을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-126">Correct the rows at the Subscriber using the **tablediff** utility or another method.</span></span>  
  
4.  <span data-ttu-id="87a77-127">(선택 사항) **-SkipErrors** 매개 변수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="87a77-127">(Optional) Remove the **-SkipErrors** parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a77-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87a77-128">See Also</span></span>  
 [<span data-ttu-id="87a77-129">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="87a77-129">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
