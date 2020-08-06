---
title: 데이터 다시 게시 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- republishing data
- publishing [SQL Server replication], Subscribers
- Subscribers [SQL Server replication], republishing data
ms.assetid: a1485cf4-b1c4-49e9-ab06-8ccfaad998f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1e4213266121b3bf55bf2857e15f71f1e94e301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646313"
---
# <a name="republish-data"></a><span data-ttu-id="2238d-102">데이터 다시 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-102">Republish Data</span></span>
  <span data-ttu-id="2238d-103">재게시 모델에서 게시자는 구독자로 데이터를 보내고 구독자는 다른 모든 구독자에 데이터를 다시 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-103">In a republishing model, the Publisher sends data to a Subscriber, which then republishes the data to any number of other Subscribers.</span></span> <span data-ttu-id="2238d-104">이 방법은 게시자가 속도가 느리거나 비용이 많이 드는 통신 연결로 데이터를 구독자에 보내야 할 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-104">This is useful when a Publisher must send data to Subscribers over a slow or expensive communications link.</span></span> <span data-ttu-id="2238d-105">연결 끝 쪽에 다수의 구독자가 있을 경우 재게시자를 사용하면 대량의 배포 로드가 해당 연결 쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-105">If there are a number of Subscribers on the far side of that link, using a republisher shifts the bulk of the distribution load to that side of the link.</span></span>  
  
 <span data-ttu-id="2238d-106">데이터 재게시 과정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-106">Republishing data involves the following steps:</span></span>  
  
1.  <span data-ttu-id="2238d-107">게시자에서 게시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-107">Create a publication at the Publisher.</span></span>  
  
2.  <span data-ttu-id="2238d-108">재게시 구독자에 대해 게시에 대한 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-108">Create a subscription to the publication for the republishing Subscriber.</span></span>  
  
3.  <span data-ttu-id="2238d-109">구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-109">Initialize the subscription.</span></span> <span data-ttu-id="2238d-110">재게시 구독자에서 게시를 만들기 전에 구독을 초기화하지 않으면 복제가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-110">The subscription must be initialized before the publication is created at the republishing Subscriber, or replication will fail.</span></span>  
  
4.  <span data-ttu-id="2238d-111">재게시 구독자의 구독 데이터베이스에 게시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-111">Create a publication in the subscription database at the republishing Subscriber.</span></span>  
  
5.  <span data-ttu-id="2238d-112">다른 구독자에 대해 재게시 구독자에서 게시에 대한 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-112">Create subscriptions to the publication at the republishing Subscriber for the other Subscribers.</span></span>  
  
6.  <span data-ttu-id="2238d-113">구독을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-113">Initialize the subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2238d-114">재게시 토폴로지에서 병합 복제를 사용하는 경우 모든 재게시 구독자에서 서버 구독을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-114">If you use merge replication in a republishing topology, all republishing Subscribers must use server subscriptions.</span></span> <span data-ttu-id="2238d-115">구독 유형에 대한 자세한 내용은 [게시 구독](subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2238d-115">For more information about subscription types, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="2238d-116">다음 그림에서 게시자와 재게시자는 모두 자체 로컬 배포자로 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-116">In the following illustration, both the Publisher and the republisher are acting as their own local Distributors.</span></span> <span data-ttu-id="2238d-117">여기에 원격 배포자를 설정하면 각 배포자는 속도가 느리거나 비용이 많이 드는 통신 연결의 같은 쪽에 게시자로 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-117">If each were set up to use a remote Distributor, each Distributor would need to be on the same side of the slow or expensive communications link as its Publisher.</span></span> <span data-ttu-id="2238d-118">게시자는 안정적인 고속 통신 연결로 배포자에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-118">Publishers must be connected to remote Distributors by reliable, high-speed communications links.</span></span>  
  
 <span data-ttu-id="2238d-119">![데이터 재게시](media/repl-06a.gif "데이터 재게시")</span><span class="sxs-lookup"><span data-stu-id="2238d-119">![Republishing data](media/repl-06a.gif "Republishing data")</span></span>  
  
 <span data-ttu-id="2238d-120">모든 서버는 게시자인 동시에 구독자로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-120">Any server can act as both a Publisher and Subscriber.</span></span> <span data-ttu-id="2238d-121">예를 들어 다음 다이어그램에서 런던에 존재하며 미국의 다른 4개 도시인 시카고, 뉴욕, 샌디에고 및 시애틀과 같은 4개 도시에 배포해야 하는 테이블 게시를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-121">For example, consider the following diagram in which a publication of a table exists in London and must be distributed to four different cities in the United States: Chicago, New York, San Diego, and Seattle.</span></span> <span data-ttu-id="2238d-122">이 경우 다음과 같이 뉴욕 사이트가 조건에 맞기 때문에 뉴욕에 있는 서버를 런던에서 시작된 게시된 테이블로 구독하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-122">The server in New York is chosen to subscribe to the published table originating in London, because the New York site meets these conditions:</span></span>  
  
-   <span data-ttu-id="2238d-123">런던으로 돌아가는 네트워크 연결이 상대적으로 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-123">The network link back to London is relatively reliable.</span></span>  
  
-   <span data-ttu-id="2238d-124">런던 및 뉴욕 간 통신 비용이 적당합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-124">The London-to-New York communication costs are acceptable.</span></span>  
  
-   <span data-ttu-id="2238d-125">뉴욕에서 미국의 다른 모든 구독자 사이트 간 네트워크 통신 회선이 양호합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-125">There are good network communications lines from New York to all other Subscriber sites in the United States.</span></span>  
  
     <span data-ttu-id="2238d-126">![여러 위치로 데이터 재게시](media/repl-06.gif "여러 위치로 데이터 재게시")</span><span class="sxs-lookup"><span data-stu-id="2238d-126">![Republishing data to dispersed locations](media/repl-06.gif "Republishing data to dispersed locations")</span></span>  
  
 <span data-ttu-id="2238d-127">복제는 다음 표에 나와 있는 재게시 시나리오를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-127">Replication supports the republishing scenarios shown in the following table.</span></span>  
  
|<span data-ttu-id="2238d-128">게시자</span><span class="sxs-lookup"><span data-stu-id="2238d-128">Publisher</span></span>|<span data-ttu-id="2238d-129">게시 구독자</span><span class="sxs-lookup"><span data-stu-id="2238d-129">Publishing Subscriber</span></span>|<span data-ttu-id="2238d-130">가입자</span><span class="sxs-lookup"><span data-stu-id="2238d-130">Subscriber</span></span>|  
|---------------|---------------------------|----------------|  
|<span data-ttu-id="2238d-131">트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-131">Transactional publication</span></span>|<span data-ttu-id="2238d-132">트랜잭션 구독/트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-132">Transactional subscription/transactional publication</span></span>|<span data-ttu-id="2238d-133">트랜잭션 구독</span><span class="sxs-lookup"><span data-stu-id="2238d-133">Transactional subscription</span></span>|  
|<span data-ttu-id="2238d-134">트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-134">Transactional publication</span></span>|<span data-ttu-id="2238d-135">트랜잭션 구독/병합 게시<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2238d-135">Transactional subscription/merge publication<sup>1</sup></span></span>|<span data-ttu-id="2238d-136">병합 구독</span><span class="sxs-lookup"><span data-stu-id="2238d-136">Merge subscription</span></span>|  
|<span data-ttu-id="2238d-137">병합 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-137">Merge publication</span></span>|<span data-ttu-id="2238d-138">병합 구독/병합 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-138">Merge subscription/merge publication</span></span>|<span data-ttu-id="2238d-139">병합 구독</span><span class="sxs-lookup"><span data-stu-id="2238d-139">Merge subscription</span></span>|  
|<span data-ttu-id="2238d-140">병합 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-140">Merge publication</span></span>|<span data-ttu-id="2238d-141">병합 구독/트랜잭션 게시</span><span class="sxs-lookup"><span data-stu-id="2238d-141">Merge subscription/transactional publication</span></span>|<span data-ttu-id="2238d-142">트랜잭션 구독</span><span class="sxs-lookup"><span data-stu-id="2238d-142">Transactional subscription</span></span>|  
  
 <span data-ttu-id="2238d-143"><sup>1</sup> `@published_in_tran_pub`병합 게시에 속성을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-143"><sup>1</sup>You should set the `@published_in_tran_pub` property on the merge publication.</span></span> <span data-ttu-id="2238d-144">기본적으로 트랜잭션 복제에서 구독자의 테이블은 읽기 전용으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-144">By default, transactional replication expects tables at the Subscriber to be treated as read-only.</span></span> <span data-ttu-id="2238d-145">병합 복제에서 트랜잭션 구독의 테이블 데이터를 변경하는 경우 데이터가 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-145">If merge replication makes data changes to a table in a transactional subscription, non-convergence of data can occur.</span></span> <span data-ttu-id="2238d-146">이렇게 되지 않도록 하려면 병합 게시에서 이러한 테이블을 다운로드 전용으로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-146">To avoid this risk, we recommend that any such table be specified as download-only in the merge publication.</span></span> <span data-ttu-id="2238d-147">그러면 병합 구독자가 테이블에 데이터 변경을 업로드하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2238d-147">This prevents a merge Subscriber from uploading data changes to the table.</span></span> <span data-ttu-id="2238d-148">자세한 내용은 [다운로드 전용 아티클로 병합 복제 성능 최적화](merge/optimize-merge-replication-performance-with-download-only-articles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2238d-148">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2238d-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2238d-149">See Also</span></span>  
 <span data-ttu-id="2238d-150">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="2238d-150">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="2238d-151">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2238d-151">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="2238d-152">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="2238d-152">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="2238d-153">[구독 초기화](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="2238d-153">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="2238d-154">데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="2238d-154">Synchronize Data</span></span>](synchronize-data.md)  
  
  
