---
title: 밀어넣기 구독 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- push subscriptions [SQL Server replication], deleting
- deleting subscriptions
- subscriptions [SQL Server replication], push
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 912958e00d117f51c5dc95c0dc1247d278acb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646927"
---
# <a name="delete-a-push-subscription"></a><span data-ttu-id="243d6-102">밀어넣기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="243d6-102">Delete a Push Subscription</span></span>
  <span data-ttu-id="243d6-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 밀어넣기 구독을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-103">This topic describes how to delete a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="243d6-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="243d6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="243d6-105">**밀어넣기 구독을 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="243d6-105">**To delete a push subscription, using:**</span></span>  
  
     [<span data-ttu-id="243d6-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="243d6-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="243d6-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="243d6-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="243d6-108">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="243d6-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="243d6-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="243d6-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="243d6-110">게시자( **의** 로컬 게시 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]폴더 사용) 또는 구독자( **로컬 구독** 폴더 사용)에서 밀어넣기 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-110">Delete a push subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="243d6-111">구독을 삭제해도 구독에서 개체나 데이터가 제거되지는 않으며 개체나 데이터는 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-publisher"></a><span data-ttu-id="243d6-112">게시자에서 밀어넣기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-112">To delete a push subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="243d6-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="243d6-114">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="243d6-115">삭제할 구독과 연결된 게시를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="243d6-116">구독을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="243d6-117">확인 대화 상자에서 구독 정보를 삭제할 구독자에 연결할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="243d6-118">**구독자에 연결** 확인란의 선택을 취소한 경우 나중에 구독자에 연결하여 해당 정보를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-118">If you clear the **Connect to Subscriber** checkbox, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-subscriber"></a><span data-ttu-id="243d6-119">구독자에서 밀어넣기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-119">To delete a push subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="243d6-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="243d6-121">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="243d6-122">삭제할 구독을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="243d6-123">확인 대화 상자에서 구독 정보를 삭제할 게시자에 연결할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="243d6-124">**게시자에 연결** 확인란의 선택을 취소한 경우 나중에 게시자에 연결하여 해당 정보를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="243d6-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="243d6-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="243d6-126">밀어넣기 구독은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-126">Push subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="243d6-127">사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-127">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="243d6-128">스냅샷 또는 트랜잭션 게시에 대한 밀어넣기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-128">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="243d6-129">게시 데이터베이스의 게시자에서 [sp_dropsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-129">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="243d6-130">**@publication**및를 지정 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-130">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="243d6-131">**@article**에 **all** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-131">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="243d6-132">(옵션) 배포자에 액세스할 수 없으면 **@ignore_distributor** 에 **@ignore_distributor** 을 지정하여 배포자에서 관련 개체를 제거하지 않고 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-132">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="243d6-133">구독 데이터베이스의 구독자에서 [sp_subscription_cleanup&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql)을 실행하여 구독 데이터베이스에 있는 복제 메타데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-133">At the Subscriber on the subscription database, execute [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="243d6-134">병합 게시에 대한 밀어내기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-134">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="243d6-135">게시자에서 [sp_dropmergesubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)를 실행 하 **@publication** 고를 지정 **@subscriber** **@subscriber_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-135">At the Publisher, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql), specifying **@publication**, **@subscriber** and **@subscriber_db**.</span></span> <span data-ttu-id="243d6-136">(옵션) 배포자에 액세스할 수 없으면 **@ignore_distributor** 에 **@ignore_distributor** 을 지정하여 배포자에서 관련 개체를 제거하지 않고 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-136">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="243d6-137">구독 데이터베이스의 구독자에서 [sp_mergesubscription_cleanup&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-137">At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql).</span></span> <span data-ttu-id="243d6-138">**@publisher**, **@publisher_db** 및를 지정 **@publication** 합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-138">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="243d6-139">이렇게 하면 구독 데이터베이스에서 병합 메타데이터가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-139">This removes merge metadata from the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="243d6-140">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="243d6-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="243d6-141">이 예에서는 트랜잭션 게시에 대한 밀어넣기 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-141">This example deletes a push subscription to a transactional publication.</span></span>  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="243d6-142">이 예에서는 병합 게시에 대한 밀어넣기 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-142">This example deletes a push subscription to a merge publication.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="243d6-143">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="243d6-143">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="243d6-144">밀어넣기 구독을 삭제하는 데 사용되는 RMO 클래스는 밀어넣기 구독이 구독하는 게시의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-144">The RMO classes that you use to delete a push subscription depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="243d6-145">스냅샷 또는 트랜잭션 게시에 대한 밀어넣기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-145">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="243d6-146"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-146">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="243d6-147"><xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-147">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="243d6-148"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>및 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-148">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="243d6-149"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성을 1단계의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-149">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="243d6-150"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 구독이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-150">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="243d6-151">이 속성의 값이 `false`이면 2단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-151">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="243d6-152"><xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-152">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="243d6-153">병합 게시에 대한 밀어내기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="243d6-153">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="243d6-154"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-154">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="243d6-155"><xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-155">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="243d6-156"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>및 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-156">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="243d6-157"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성을 1단계의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-157">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="243d6-158"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 구독이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-158">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="243d6-159">이 속성의 값이 `false`이면 2단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-159">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="243d6-160"><xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-160">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="243d6-161">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="243d6-161">Examples (RMO)</span></span>  
 <span data-ttu-id="243d6-162">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 밀어넣기 구독을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-162">You can delete push subscriptions programmatically by using Replication Management Objects (RMO).</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="243d6-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="243d6-163">See Also</span></span>  
 <span data-ttu-id="243d6-164">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="243d6-164">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="243d6-165">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="243d6-165">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
