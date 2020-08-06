---
title: 업데이트 가능한 트랜잭션 구독에 대한 업데이트 모드 전환 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661643"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a><span data-ttu-id="38405-102">업데이트 가능한 트랜잭션 구독에 대한 업데이트 모드 전환</span><span class="sxs-lookup"><span data-stu-id="38405-102">Switch Between Update Modes for an Updatable Transactional Subscription</span></span>
  <span data-ttu-id="38405-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 업데이트된 트랜잭션 구독에 대한 업데이트 모드를 전환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-103">This topic describes how to switch between update modes for an updatable transaction subscription in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="38405-104">새 구독 마법사를 사용하여 업데이트할 수 있는 구독에 대한 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-104">Specify the mode for updatable subscriptions using the New Subscription Wizard.</span></span> <span data-ttu-id="38405-105">이 마법사를 사용할 때 모드를 설정하는 방법은 [끌어오기 구독 속성 보기 및 수정](../view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38405-105">For information about setting the mode when using this wizard, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38405-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="38405-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38405-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="38405-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="38405-108">언제든지 즉시 업데이트에서 지연 업데이트로 장애 조치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38405-108">You can fail over from immediate to queued updating at any time.</span></span> <span data-ttu-id="38405-109">그러나 장애 조치한 후에는 구독자와 게시자가 연결되고 큐 판독기 에이전트에서 큐의 보류 중인 모든 메시지를 게시자에 적용할 때까지는 즉시 업데이트로 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38405-109">After you do, however, you cannot return to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="38405-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="38405-110">Recommendations</span></span>  
  
-   <span data-ttu-id="38405-111">트랜잭션 게시에 대한 업데이트 구독이 한 업데이트 모드에서 다른 업데이트 모드로의 장애 조치를 지원하면 업데이트 모드를 프로그래밍 방식으로 전환하여 짧은 시간 동안 연결이 변경되는 경우를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38405-111">When an updating subscription to a transactional publication supports failover from one updating mode to another, you can programmatically switch update modes to handle situations when connectivity changes for a short period of time.</span></span> <span data-ttu-id="38405-112">업데이트 모드는 요청 시 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38405-112">The update mode can be set programmatically and on demand using replication stored procedures.</span></span> <span data-ttu-id="38405-113">자세한 내용은 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38405-113">For more information, see [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38405-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="38405-114">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38405-115">구독이 생성된 후에 업데이트 모드를 변경하려면 구독이 생성될 때 **update_mode** 속성을 즉시 업데이트에서 지연 업데이트로 전환할 수 있는 **failover** 또는 지연 업데이트에서 즉시 업데이트로 전환할 수 있는 **queued failover** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-115">To change the update mode after the subscription is created, the **update_mode** property must be set to **failover** (which allows a switch from immediate updating to queued updating) or **queued failover** (which allows a switch from queued updating to immediate updating) when the subscription is created.</span></span> <span data-ttu-id="38405-116">이러한 속성은 새 구독 마법사에서 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38405-116">These properties are set automatically in the New Subscription Wizard.</span></span>  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a><span data-ttu-id="38405-117">밀어넣기 구독에 대한 업데이트 모드를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="38405-117">To set the updating mode for a push subscription</span></span>  
  
1.  <span data-ttu-id="38405-118">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-118">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="38405-119">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-119">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="38405-120">업데이트 모드를 설정하려는 구독을 마우스 오른쪽 단추로 클릭한 다음 **업데이트 방법 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-120">Right-click the subscription for which you want to set the update mode, and then click **Set Update Method**.</span></span>  
  
4.  <span data-ttu-id="38405-121">**업데이트 방법 설정 - \<Subscriber>: \<SubscriptionDatabase>** 대화 상자에서 **즉시 업데이트** 또는 **지연 업데이트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-121">In the **Set Update Method - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select **Immediate updating** or **Queued updating**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a><span data-ttu-id="38405-122">끌어오기 구독에 대한 업데이트 모드를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="38405-122">To set the updating mode for a pull subscription</span></span>  
  
1.  <span data-ttu-id="38405-123">**구독 속성 - \<Publisher>: \<PublicationDatabase>** 대화 상자에서 **구독자 업데이트 방법** 옵션에 대해 **즉시 변경 내용 복제** 또는 **변경 내용 대기** 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-123">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, select a value of **Immediately replicate changes** or **Queue changes** for the **Subscriber update method** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="38405-124">**구독 속성 - \<Publisher>: \<PublicationDatabase>** 대화 상자에 액세스하는 방법은 [끌어오기 구독 속성 보기 및 수정](../view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38405-124">For more information about accessing the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38405-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="38405-125">Using Transact-SQL</span></span>  
  
#### <a name="to-switch-between-update-modes"></a><span data-ttu-id="38405-126">업데이트 모드를 전환하려면</span><span class="sxs-lookup"><span data-stu-id="38405-126">To switch between update modes</span></span>  
  
1.  <span data-ttu-id="38405-127">끌어오기 구독의 경우 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) , 밀어넣기 구독의 경우 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) 을 실행하여 구독에서 장애 조치가 지원되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-127">Verify that the subscription supports failover by executing [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) for a pull subscription or [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) for a push subscription.</span></span> <span data-ttu-id="38405-128">결과 집합의 **업데이트 모드** 값이 **3** 또는 **4**이면 장애 조치가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38405-128">If the value of **update mode** in the result set is **3** or **4**, failover is supported.</span></span>  
  
2.  <span data-ttu-id="38405-129">구독 데이터베이스의 구독자에서 [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-129">At the Subscriber on the subscription database, execute [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql).</span></span> <span data-ttu-id="38405-130">**@publisher**,, **@publisher_db** 를 지정 **@publication** 하 고에 다음 값 중 하나를 지정 합니다 **@failover_mode** .</span><span class="sxs-lookup"><span data-stu-id="38405-130">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@failover_mode**:</span></span>  
  
    -   <span data-ttu-id="38405-131">**queued** - 연결이 일시적으로 끊어진 경우 지연 업데이트로 장애 조치합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-131">**queued** - fail over to queued updating when connectivity has been temporarily lost.</span></span>  
  
    -   <span data-ttu-id="38405-132">**immediate** - 연결이 복원되었을 때 즉시 업데이트로 장애 초지합니다.</span><span class="sxs-lookup"><span data-stu-id="38405-132">**immediate** - fail over to immediate updating when connectivity has been restored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38405-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38405-133">See Also</span></span>  
 [<span data-ttu-id="38405-134">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="38405-134">Updatable Subscriptions for Transactional Replication</span></span>](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
