---
title: MSSQL_ENG014005 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d820fd26cceee72b0d08204d6f6ce73a76508e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646361"
---
# <a name="mssql_eng014005"></a><span data-ttu-id="34a24-102">MSSQL_ENG014005</span><span class="sxs-lookup"><span data-stu-id="34a24-102">MSSQL_ENG014005</span></span>
    
## <a name="message-details"></a><span data-ttu-id="34a24-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="34a24-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34a24-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="34a24-104">Product Name</span></span>|<span data-ttu-id="34a24-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="34a24-105">SQL Server</span></span>|  
|<span data-ttu-id="34a24-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="34a24-106">Event ID</span></span>|<span data-ttu-id="34a24-107">14005</span><span class="sxs-lookup"><span data-stu-id="34a24-107">14005</span></span>|  
|<span data-ttu-id="34a24-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="34a24-108">Event Source</span></span>|<span data-ttu-id="34a24-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="34a24-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="34a24-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="34a24-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="34a24-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="34a24-111">Symbolic Name</span></span>||  
|<span data-ttu-id="34a24-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="34a24-112">Message Text</span></span>|<span data-ttu-id="34a24-113">게시를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-113">Could not drop publication.</span></span> <span data-ttu-id="34a24-114">게시에 대한 구독이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-114">A subscription exists to it.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="34a24-115">설명</span><span class="sxs-lookup"><span data-stu-id="34a24-115">Explanation</span></span>  
 <span data-ttu-id="34a24-116">하나 이상의 연결된 구독이 있는 게시를 삭제하려 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-116">You have tried to drop a publication which has one or more associated subscriptions.</span></span> <span data-ttu-id="34a24-117">연결된 구독이 없는 경우에만 게시를 삭제할 수 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-117">A publication can only be dropped if there are no associated subscriptions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34a24-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="34a24-118">User Action</span></span>  
 <span data-ttu-id="34a24-119">게시를 삭제하기 전에 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-119">Drop the subscriptions before dropping the publication.</span></span> <span data-ttu-id="34a24-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 게시를 삭제하는 경우 게시를 삭제하기 전에 연결된 구독을 모두 자동으로 삭제하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-120">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to drop the publication, it will give you the option to automatically drop all associated subscriptions before dropping the publication.</span></span> <span data-ttu-id="34a24-121">저장 프로시저를 사용하는 경우에는 먼저 명시적으로 구독을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-121">If you use stored procedures, you must explicitly drop the subscriptions first.</span></span> <span data-ttu-id="34a24-122">자세한 내용은 [Delete a Push Subscription](delete-a-push-subscription.md) 및 [Delete a Pull Subscription](delete-a-pull-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34a24-122">For more information, see [Delete a Push Subscription](delete-a-push-subscription.md) and [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="34a24-123">게시에 대한 구독이 없거나 게시를 만들 때 이러한 오류가 나타나는 경우에는 이전 구독을 완전히 제거하지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-123">If no subscriptions appear to exist for the publication or if you see this error when you create a publication, you might have a previous subscription that was not completely cleaned up when it was removed.</span></span> <span data-ttu-id="34a24-124">데이터베이스에서 [sp_removedbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 실행하여 복제와 관련된 모든 개체 및 설정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="34a24-124">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) on the database to remove all objects and settings related to replication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a24-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34a24-125">See Also</span></span>  
 [<span data-ttu-id="34a24-126">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="34a24-126">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
