---
title: MSSQL_ENG014157 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0682d740d82c995d64427f56aabce24b8a48ca65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649493"
---
# <a name="mssql_eng014157"></a><span data-ttu-id="cf7fb-102">MSSQL_ENG014157</span><span class="sxs-lookup"><span data-stu-id="cf7fb-102">MSSQL_ENG014157</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cf7fb-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="cf7fb-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf7fb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="cf7fb-104">Product Name</span></span>|<span data-ttu-id="cf7fb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf7fb-105">SQL Server</span></span>|  
|<span data-ttu-id="cf7fb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="cf7fb-106">Event ID</span></span>|<span data-ttu-id="cf7fb-107">14157</span><span class="sxs-lookup"><span data-stu-id="cf7fb-107">14157</span></span>|  
|<span data-ttu-id="cf7fb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="cf7fb-108">Event Source</span></span>|<span data-ttu-id="cf7fb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf7fb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf7fb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cf7fb-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cf7fb-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="cf7fb-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cf7fb-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="cf7fb-112">Message Text</span></span>|<span data-ttu-id="cf7fb-113">구독자 '%s'이(가) 게시 '%s'에 대해 만든 구독이 만료되어 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-113">The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf7fb-114">설명</span><span class="sxs-lookup"><span data-stu-id="cf7fb-114">Explanation</span></span>  
 <span data-ttu-id="cf7fb-115">구독자는 게시 보존 기간에 지정된 시간 내에 게시자와 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-115">A Subscriber must synchronize with the Publisher within the time specified in the publication retention period.</span></span> <span data-ttu-id="cf7fb-116">구독자가 이 기간 내에 동기화하지 않으면 구독이 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-116">If a Subscriber does not synchronize within this period, the subscription expires.</span></span> <span data-ttu-id="cf7fb-117">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-117">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf7fb-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="cf7fb-118">User Action</span></span>  
 <span data-ttu-id="cf7fb-119">구독자가 데이터 변경 내용을 다시 받을 수 있으려면 먼저 구독을 다시 만들고 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-119">The subscription must be re-created and initialized before the Subscriber can begin receiving data changes again:</span></span>  
  
-   <span data-ttu-id="cf7fb-120">구독 만들기에 대한 자세한 내용은 [게시 구독](subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-120">For information about creating subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="cf7fb-121">구독 초기화에 대한 자세한 내용은 [구독 초기화](initialize-a-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-121">For information about initializing subscriptions, see [Initialize a Subscription](initialize-a-subscription.md).</span></span>  
  
 <span data-ttu-id="cf7fb-122">구독 데이터베이스에 게시자와 동기화되지 않은 변경 내용이 있을 경우 [tablediff Utility](../../tools/tablediff-utility.md) 를 사용하여 게시 및 구독 데이터베이스에서 일치하지 않는 행을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-122">If the subscription database contains changes that have not been synchronized with the Publisher, you can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span>  
  
 <span data-ttu-id="cf7fb-123">게시 보존 기간을 늘려 구독이 만료되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-123">You can increase the publication retention period to avoid having subscriptions expire.</span></span> <span data-ttu-id="cf7fb-124">높은 값을 설정할 경우 더 많은 데이터와 메타데이터가 저장되어 성능에 영향을 줄 수 있으므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-124">Use caution in setting a high value, because this can result in more data and metadata being stored, which affects performance.</span></span> <span data-ttu-id="cf7fb-125">자세한 내용은 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf7fb-125">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7fb-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf7fb-126">See Also</span></span>  
 [<span data-ttu-id="cf7fb-127">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="cf7fb-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
