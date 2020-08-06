---
title: 기존 게시에 대한 아티클 추가 및 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f72f15886e7105dde8d0e15dd0598a7474ed7e39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661029"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a><span data-ttu-id="5e080-102">기존 게시에 대한 아티클 추가 및 삭제</span><span class="sxs-lookup"><span data-stu-id="5e080-102">Add Articles to and Drop Articles from Existing Publications</span></span>
  <span data-ttu-id="5e080-103">게시가 생성된 후에는 아티클을 추가 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-103">After a publication is created, it is possible to add and drop articles.</span></span> <span data-ttu-id="5e080-104">아티클 추가 작업은 언제든지 수행할 수 있지만 아티클 삭제에 필요한 동작은 복제 유형과 아티클 삭제 시기에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-104">Articles can be added at any time, but the actions required for dropping articles depend on the type of replication and when the article is dropped.</span></span>  
  
## <a name="adding-articles"></a><span data-ttu-id="5e080-105">아티클 추가</span><span class="sxs-lookup"><span data-stu-id="5e080-105">Adding Articles</span></span>  
 <span data-ttu-id="5e080-106">아티클을 추가하려면 아티클을 게시에 추가하고, 게시에 대한 새 스냅샷을 만들고, 구독을 동기화하여 새 아티클에 대한 스키마 및 데이터를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-106">Adding an article involves: adding the article to the publication; creating a new snapshot for the publication; synchronizing the subscription to apply the schema and data for the new article.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e080-107">병합 게시에 아티클을 추가하고 기존 아티클이 새 아티클에 종속된 경우 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 및 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)의 **\@processing_order** 매개 변수를 사용하여 두 아티클의 처리 순서를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-107">If you add an article to a merge publication and an existing article depends on the new article, you must specify a processing order for both articles using the **\@processing_order** parameter of [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) and [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="5e080-108">다음과 같은 시나리오를 고려해 보십시오. 테이블을 게시하지만 테이블이 참조하는 함수는 게시하지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-108">Consider the following scenario: you publish a table but you do not publish a function that the table references.</span></span> <span data-ttu-id="5e080-109">함수를 게시하지 않을 경우 구독자에서 테이블을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-109">If you do not publish the function, the table cannot be created at the Subscriber.</span></span> <span data-ttu-id="5e080-110">게시에 함수를 추가할 경우에는 **sp_addmergearticle**의 **\@processing_order** 매개 변수에 값 **1**을 지정하고 **sp_changemergearticle**의 **\@processing_order** 매개 변수에 값 **2**를 지정하며 **\@article** 매개 변수에는 테이블 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-110">When you add the function to the publication: specify a value of **1** for the **\@processing_order** parameter of **sp_addmergearticle**; and specify a value of **2** for the **\@processing_order** parameter of **sp_changemergearticle**, specifying the table name for the parameter **\@article**.</span></span> <span data-ttu-id="5e080-111">이 처리 순서를 사용하면 함수에 종속된 테이블이 생성되기 전에 해당 함수가 구독자에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-111">This processing order ensures that you create the function at the Subscriber before the table that depends on it.</span></span> <span data-ttu-id="5e080-112">함수 번호가 테이블 번호보다 낮은 경우 각 아티클에 다른 번호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-112">You can use different numbers for each article, as long as the number for the function is lower than the number for the table.</span></span>  
  
1.  <span data-ttu-id="5e080-113">다음 방법 중 하나를 사용하여 하나 이상의 아티클을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-113">Add one or more articles through one of the following methods:</span></span>  
  
    -   [<span data-ttu-id="5e080-114">게시에 대한 아티클 추가 및 삭제&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5e080-114">Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;</span></span>](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [<span data-ttu-id="5e080-115">아티클 정의</span><span class="sxs-lookup"><span data-stu-id="5e080-115">Define an Article</span></span>](define-an-article.md)  
  
2.  <span data-ttu-id="5e080-116">아티클을 게시에 추가한 후에는 게시에 대한 새 스냅샷을 만들어야 합니다. 매개 변수가 있는 필터가 포함된 병합 게시인 경우에는 파티션도 모두 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-116">After adding an article to a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span> <span data-ttu-id="5e080-117">그러면 배포 에이전트 또는 병합 에이전트가 새 아티클에 대한 스키마 및 데이터를 구독자로 복사합니다. 이때 전체 게시를 다시 초기화하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-117">The Distribution Agent or Merge Agent then copies the schema and data for the new article to the Subscriber (it does not reinitialize the entire publication).</span></span>  
  
    -   <span data-ttu-id="5e080-118">새 스냅샷을 만들려면 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e080-118">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="5e080-119">매개 변수가 있는 필터로 병합 게시에 대한 새 스냅샷을 만들려면 [매개 변수가 있는 필터로 병합 게시에 대한 스냅샷 만들기](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-119">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
3.  <span data-ttu-id="5e080-120">스냅샷이 생성된 후에 구독을 동기화하여 새 아티클에 대한 스키마 및 데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-120">After the snapshot is created, synchronize the subscription to copy the schema and data for the new article.</span></span>  
  
    -   <span data-ttu-id="5e080-121">밀어넣기 구독을 동기화하려면 [Synchronize a Push Subscription](../synchronize-a-push-subscription.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e080-121">To synchronize a push subscription, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).</span></span>  
  
    -   <span data-ttu-id="5e080-122">끌어오기 구독을 동기화하려면 [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e080-122">To synchronize a pull subscription, see [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span>  
  
## <a name="dropping-articles"></a><span data-ttu-id="5e080-123">아티클 삭제</span><span class="sxs-lookup"><span data-stu-id="5e080-123">Dropping Articles</span></span>  
 <span data-ttu-id="5e080-124">언제든지 아티클을 게시에서 삭제할 수 있지만 다음 동작을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-124">Articles can be dropped from a publication at any time, but you must take into account the following behaviors:</span></span>  
  
-   <span data-ttu-id="5e080-125">게시에서 아티클을 삭제해도 해당 개체가 게시 데이터베이스에서 삭제되거나 구독 데이터베이스의 해당 개체가 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-125">Dropping an article from a publication does not remove the object from the publication database or the corresponding object from the subscription database.</span></span> <span data-ttu-id="5e080-126">필요한 경우 DROP \<Object>를 사용하여 이러한 개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-126">Use DROP \<Object> to remove these objects if necessary.</span></span> <span data-ttu-id="5e080-127">외래 키 제약 조건을 통해 다른 게시된 아티클과 관련된 아티클을 삭제하는 경우에는 테이블을 구독자에서 수동으로 삭제하거나, 적절한 DROP \<Object> 문이 포함된 스크립트를 지정하고 요청 시 실행하여 테이블을 삭제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-127">When you drop an article that is related to other published articles through foreign key constraints, we recommend that you drop the table at the Subscriber manually or by using on-demand script execution: specify a script that includes the appropriate DROP \<Object> statements.</span></span> <span data-ttu-id="5e080-128">자세한 내용은 [동기화 중 스크립트 실행&#40;복제 Transact-SQL 프로그래밍&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-128">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="5e080-129">호환성 수준이 90RTM 이상인 병합 게시의 경우에는 언제든지 아티클을 삭제할 수 있지만 새 스냅샷이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-129">For merge publications with a compatibility level of 90RTM or higher, articles can be dropped at any time, but a new snapshot is required.</span></span> <span data-ttu-id="5e080-130">또한 다음 작업도 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-130">Additionally:</span></span>  
  
    -   <span data-ttu-id="5e080-131">아티클이 조인 필터 또는 논리적 레코드 관계에서 부모 아티클인 경우에는 해당 관계를 먼저 삭제해야 하므로 재초기화가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-131">If an article is a parent article in a join filter or logical record relationship, the relationships must be dropped first, which requires reinitialization.</span></span>  
  
    -   <span data-ttu-id="5e080-132">게시에서 아티클에 매개 변수가 있는 마지막 필터가 있는 경우에는 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-132">If an article has the last parameterized filter in a publication, subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="5e080-133">호환성 수준이 90RTM 이하인 병합 게시의 경우에는 구독의 초기 동기화 이전에 특별한 고려 사항 없이 아티클을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-133">For merge publications with a compatibility level lower than 90RTM, articles can be dropped with no special considerations prior to the initial synchronization of subscriptions.</span></span> <span data-ttu-id="5e080-134">하나 이상의 구독이 동기화된 후에 아티클을 삭제하면 해당 구독을 삭제한 뒤 다시 만들고 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-134">If an article is dropped after one or more subscriptions is synchronized, the subscriptions must be dropped, re-created, and synchronized.</span></span>  
  
-   <span data-ttu-id="5e080-135">스냅샷 또는 트랜잭션 게시의 경우에는 구독을 만들기 전에 특별한 고려 사항 없이 아티클을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-135">For snapshot or transactional publications, articles can be dropped with no special considerations prior to subscriptions being created.</span></span> <span data-ttu-id="5e080-136">하나 이상의 구독이 생성된 후에 아티클을 삭제하면 해당 구독을 삭제한 뒤 다시 만들고 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-136">If an article is dropped after one or more subscriptions is created, the subscriptions must be dropped, recreated, and synchronized.</span></span> <span data-ttu-id="5e080-137">구독 삭제에 대한 자세한 내용은 [게시 구독](../subscribe-to-publications.md) 및 [sp_dropsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-137">For more information about dropping subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md) and [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="5e080-138">**sp_dropsubscription** 을 사용하면 전체 구독 대신 구독에서 단일 아티클을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-138">**sp_dropsubscription** allows you to drop a single article from the subscription rather than the entire subscription.</span></span>  
  
1.  <span data-ttu-id="5e080-139">게시에서 아티클을 삭제하려면 아티클을 삭제하고 게시에 대한 새 스냅샷을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-139">Dropping an article from a publication involves dropping the article and creating a new snapshot for the publication.</span></span> <span data-ttu-id="5e080-140">아티클을 삭제하면 현재 스냅샷이 무효화되므로 새 스냅샷을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-140">Dropping an article invalidates the current snapshot; therefore a new snapshot must be created.</span></span>  
  
    -   <span data-ttu-id="5e080-141">게시에서 아티클을 삭제하려면 [게시에 대한 아티클 추가 및 삭제&#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) 또는 [아티클 삭제](delete-an-article.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-141">To drop an article from a publication, see [Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) or [Delete an Article](delete-an-article.md).</span></span>  
  
2.  <span data-ttu-id="5e080-142">게시에서 아티클을 삭제한 후에는 게시에 대한 새 스냅샷을 만들어야 합니다. 매개 변수가 있는 필터가 포함된 병합 게시인 경우에는 파티션도 모두 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-142">After dropping an article from a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span>  
  
    -   <span data-ttu-id="5e080-143">새 스냅샷을 만들려면 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e080-143">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="5e080-144">매개 변수가 있는 필터로 병합 게시에 대한 새 스냅샷을 만들려면 [매개 변수가 있는 필터로 병합 게시에 대한 스냅샷 만들기](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-144">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="5e080-145">위에서 언급한 대로 경우에 따라서는 아티클을 삭제하면 구독을 삭제한 뒤 다시 만들고 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e080-145">As noted above, in some cases dropping an article requires subscriptions to be dropped, recreated, and then synchronized.</span></span> <span data-ttu-id="5e080-146">자세한 내용은 [게시 구독](../subscribe-to-publications.md) 및 [데이터 동기화](../synchronize-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e080-146">For more information, see [Subscribe to Publications](../subscribe-to-publications.md) and [Synchronize Data](../synchronize-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e080-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e080-147">See Also</span></span>  
 <span data-ttu-id="5e080-148">[데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5e080-148">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="5e080-149">[구독 다시 초기화](../reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="5e080-149">[Reinitialize Subscriptions](../reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="5e080-150">게시 데이터베이스의 스키마 변경</span><span class="sxs-lookup"><span data-stu-id="5e080-150">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
