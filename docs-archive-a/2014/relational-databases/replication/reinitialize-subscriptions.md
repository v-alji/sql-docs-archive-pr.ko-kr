---
title: 구독 다시 초기화 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bf9c68f66a32d1a5ddcf08b845396f815385e83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741763"
---
# <a name="reinitialize-subscriptions"></a><span data-ttu-id="7af6d-102">구독 다시 초기화</span><span class="sxs-lookup"><span data-stu-id="7af6d-102">Reinitialize Subscriptions</span></span>
  <span data-ttu-id="7af6d-103">구독을 다시 초기화하면 아티클의 새 스냅샷이 구독자에 적용됩니다. 트랜잭션 및 스냅샷 복제를 사용하면 개별 아티클을 다시 초기화할 수 있으며 병합 복제를 사용하면 모든 아티클을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-103">Reinitializing a subscription involves applying a new snapshot of one or more articles to one or more Subscribers: transactional and snapshot replication allow individual articles to be reinitialized; merge replication requires all articles to be reinitialized.</span></span> <span data-ttu-id="7af6d-104">피어 투 피어 트랜잭션 복제 토폴로지의 노드는 다시 초기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-104">Nodes in a peer-to-peer transactional replication topology cannot be reinitialized.</span></span> <span data-ttu-id="7af6d-105">노드에 새로운 데이터 복사본을 유지하려면 해당 노드에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-105">If you need to ensure a node has a new copy of the data, restore a backup at the node.</span></span> <span data-ttu-id="7af6d-106">다시 초기화는 다음 두 가지 이유로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-106">Reinitialization occurs for one of two reasons:</span></span>  
  
-   <span data-ttu-id="7af6d-107">구독을 다시 초기화되도록 명시적으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-107">You explicitly mark a subscription for reinitialization.</span></span>  
  
-   <span data-ttu-id="7af6d-108">속성 변경과 같이 다시 초기화가 필요한 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-108">You perform an action, such as a property change, that requires a reinitialization.</span></span> <span data-ttu-id="7af6d-109">다시 초기화가 필요한 작업에 대한 자세한 내용은 [게시 및 아티클 속성 변경](publish/change-publication-and-article-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7af6d-109">For more information about actions that require reinitialization, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="7af6d-110">두 경우 모두 다음에 배포 에이전트 또는 병합 에이전트가 실행될 때 최신 스냅샷이 구독자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-110">In both cases, the most recent snapshot is applied to the Subscriber the next time the Distribution Agent or the Merge Agent runs.</span></span> <span data-ttu-id="7af6d-111">스냅샷 및 트랜잭션 복제의 경우 다시 초기화가 발생할 때 구독자에서는 수행되었지만 아직 게시자와 동기화되지 않은 변경 내용은 새 스냅샷의 애플리케이션에서 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-111">For snapshot and transactional replication, when reinitialization occurs, any changes made at the Subscriber, but not yet synchronized with the Publisher, are overwritten by the application of the new snapshot.</span></span>  
  
 <span data-ttu-id="7af6d-112">병합 복제의 경우 스냅샷이 적용되기 전에 모든 데이터 변경 내용을 구독자에서 업로드하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-112">For merge replication, you can choose to have all the data changes uploaded from the Subscriber before the snapshot is applied.</span></span> <span data-ttu-id="7af6d-113">게시자에서 보류 중인 스키마 변경이 구독자에 적용된 다음 스냅샷이 다시 적용되기 전에 마지막 동기화 이후 구독자에서 수행된 모든 업데이트가 게시자로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-113">Any pending schema changes from the Publisher are applied at the Subscriber, and then any updates that have been made at the Subscriber since the last synchronization are propagated to the Publisher before the snapshot is reapplied.</span></span> <span data-ttu-id="7af6d-114">이러한 동작은 **upload_first** 및 **automatic_reinitialization_policy** 속성을 통해 제어할 수 있습니다. 자세한 내용은 [Reinitialize a Subscription](reinitialize-a-subscription.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7af6d-114">This behavior is controlled by the **upload_first** and **automatic_reinitialization_policy** properties; for more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span> <span data-ttu-id="7af6d-115">SQL Server Management Studio 또는 복제 모니터를 사용하여 구독을 다시 초기화로 표시하면 변경을 먼저 업로드하는 옵션이 **구독 다시 초기화** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-115">If you mark a subscription for reinitialization using SQL Server Management Studio or Replication Monitor, you are given an option in the **Reinitialize Subscription(s)** dialog box to upload changes first.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7af6d-116">병합 게시에 매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 보류 중인 구독자의 변경 내용을 다시 초기화 중에 게시자로 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-116">If you add, drop, or change a parameterized filter in a merge publication, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="7af6d-117">보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.</span><span class="sxs-lookup"><span data-stu-id="7af6d-117">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
 <span data-ttu-id="7af6d-118">구독을 만들 때 구독자에 적용할 초기 스냅샷이 없는 것으로 지정한 후에 해당 구독을 다시 초기화로 표시할 경우 스냅샷이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-118">If, you specified that no initial snapshot was to be applied to the Subscriber when you created the subscription, and you then mark the subscription for reinitialization, a snapshot is not applied.</span></span> <span data-ttu-id="7af6d-119">자세한 내용은 [스냅샷 없이 트랜잭션 구독 초기화](initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-119">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="7af6d-120">**구독을 다시 초기화하려면**</span><span class="sxs-lookup"><span data-stu-id="7af6d-120">**To reinitialize a subscription**</span></span>  
  
 <span data-ttu-id="7af6d-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 저장 프로시저 또는 RMO(복제 관리 개체)를 사용하여 구독의 모든 아티클을 다시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-121">To reinitialize all articles in a subscription, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], stored procedures or Replication Management Objects (RMO).</span></span> <span data-ttu-id="7af6d-122">스냅샷 및 트랜잭션 게시의 개별 아티클을 다시 초기화하려면 저장 프로시저를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7af6d-122">To reinitialize individual articles in snapshot and transactional publications, you must use stored procedures.</span></span> <span data-ttu-id="7af6d-123">자세한 내용은 [Reinitialize a Subscription](reinitialize-a-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7af6d-123">For more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af6d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7af6d-124">See Also</span></span>  
 <span data-ttu-id="7af6d-125">[구독 초기화](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="7af6d-125">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="7af6d-126">구독 만료 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="7af6d-126">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
