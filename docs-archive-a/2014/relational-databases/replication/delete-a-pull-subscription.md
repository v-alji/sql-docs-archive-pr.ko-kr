---
title: 끌어오기 구독 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f869e26075bb837b2110e9db3ac5ac7220659525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646931"
---
# <a name="delete-a-pull-subscription"></a><span data-ttu-id="6899c-102">끌어오기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="6899c-102">Delete a Pull Subscription</span></span>
  <span data-ttu-id="6899c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 끌어오기 구독을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-103">This topic describes how to delete a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="6899c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6899c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6899c-105">**다음을 사용하여 끌어오기 구독을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="6899c-105">**To delete a pull subscription, using:**</span></span>  
  
     [<span data-ttu-id="6899c-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6899c-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6899c-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6899c-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6899c-108">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="6899c-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6899c-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6899c-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6899c-110">게시자( **의** 로컬 게시 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]폴더 사용) 또는 구독자( **로컬 구독** 폴더 사용)에서 끌어오기 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-110">Delete a pull subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="6899c-111">구독을 삭제해도 구독에서 개체나 데이터가 제거되지는 않으며 개체나 데이터는 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a><span data-ttu-id="6899c-112">게시자에서 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-112">To delete a pull subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="6899c-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6899c-114">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="6899c-115">삭제할 구독과 연결된 게시를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="6899c-116">구독을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="6899c-117">확인 대화 상자에서 구독 정보를 삭제할 구독자에 연결할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="6899c-118">**구독자에 연결** 확인란의 선택을 취소한 경우 나중에 구독자에 연결하여 해당 정보를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-118">If you clear the **Connect to Subscriber** check box, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a><span data-ttu-id="6899c-119">구독자에서 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-119">To delete a pull subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="6899c-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 구독자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="6899c-121">**복제** 폴더를 확장한 다음 **로컬 구독** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="6899c-122">삭제할 구독을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="6899c-123">확인 대화 상자에서 구독 정보를 삭제할 게시자에 연결할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="6899c-124">**게시자에 연결** 확인란의 선택을 취소한 경우 나중에 게시자에 연결하여 해당 정보를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6899c-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6899c-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="6899c-126">끌어오기 구독은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-126">Pull subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="6899c-127">사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-127">The stored procedures used will depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="6899c-128">스냅샷 또는 트랜잭션 게시에 대한 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-128">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="6899c-129">구독 데이터베이스의 구독자에서 [sp_droppullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-129">At the Subscriber on the subscription database, execute [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql).</span></span> <span data-ttu-id="6899c-130">**@publication**, **@publisher** 및를 지정 **@publisher_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-130">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="6899c-131">게시 데이터베이스의 게시자에서 [sp_dropsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-131">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="6899c-132">**@publication**및를 지정 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-132">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="6899c-133">**@article**에 **all** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-133">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="6899c-134">(옵션) 배포자에 액세스할 수 없으면 **@ignore_distributor** 에 **@ignore_distributor** 을 지정하여 배포자에서 관련 개체를 제거하지 않고 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-134">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="6899c-135">병합 게시에 대한 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-135">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="6899c-136">구독 데이터베이스의 구독자에서 [sp_dropmergepullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-136">At the Subscriber on the subscription database, execute [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="6899c-137">**@publication**, **@publisher** 및를 지정 **@publisher_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-137">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="6899c-138">게시 데이터베이스의 게시자에서 [sp_dropmergesubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-138">At the Publisher on the publication database, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql).</span></span> <span data-ttu-id="6899c-139">**@publication**, **@subscriber** 및를 지정 **@subscriber_db** 합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-139">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="6899c-140">**@subscription_type**에 **pull** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-140">Specify a value of **pull** for **@subscription_type**.</span></span> <span data-ttu-id="6899c-141">(옵션) 배포자에 액세스할 수 없으면 **@ignore_distributor** 에 **@ignore_distributor** 을 지정하여 배포자에서 관련 개체를 제거하지 않고 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-141">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="6899c-142">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6899c-142">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="6899c-143">다음은 트랜잭션 게시에 대한 끌어오기 구독을 삭제하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-143">The following example deletes a pull subscription to a transactional publication.</span></span> <span data-ttu-id="6899c-144">첫 번째 일괄 처리는 구독자에서 실행되고 두 번째 일괄 처리는 게시자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-144">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="6899c-145">다음은 병합 게시에 대한 끌어오기 구독을 삭제하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-145">The following example deletes a pull subscription to a merge publication.</span></span> <span data-ttu-id="6899c-146">첫 번째 일괄 처리는 구독자에서 실행되고 두 번째 일괄 처리는 게시자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-146">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="6899c-147">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="6899c-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="6899c-148">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 끌어오기 구독을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-148">You can delete pull subscriptions programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="6899c-149">끌어오기 구독을 삭제하는 데 사용되는 RMO 클래스는 끌어오기 구독이 구독하는 게시의 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-149">The RMO classes that you use to delete a pull subscription depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="6899c-150">스냅샷 또는 트랜잭션 게시에 대한 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-150">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="6899c-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 및 게시자 모두에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-151">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="6899c-152"><xref:Microsoft.SqlServer.Replication.TransPullSubscription> 클래스의 인스턴스를 만들고 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="6899c-153">1단계의 구독자 연결을 사용하여 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-153">Use the Subscriber connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="6899c-154"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 구독이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="6899c-155">이 속성의 값이 `false`이면 2단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-155">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="6899c-156"><xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-156">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="6899c-157">1단계에서 만든 게시자 연결을 사용하여 <xref:Microsoft.SqlServer.Replication.TransPublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="6899c-158"><xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-158">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="6899c-159"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-159">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="6899c-160">이 메서드가 `false`를 반환하는 경우 5단계에서 지정한 속성이 올바르지 않거나 서버에 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-160">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="6899c-161"><xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-161">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="6899c-162">*subscriber* 및 *subscriberDB* 매개 변수에 구독자의 이름과 구독 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-162">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="6899c-163">병합 게시에 대한 끌어오기 구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6899c-163">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="6899c-164"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 및 게시자 모두에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-164">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="6899c-165"><xref:Microsoft.SqlServer.Replication.MergePullSubscription> 클래스의 인스턴스를 만들고 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>및 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="6899c-166">1단계의 연결을 사용하여 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-166">Use the connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="6899c-167"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 확인하여 구독이 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-167">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="6899c-168">이 속성의 값이 `false`이면 2단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-168">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="6899c-169"><xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-169">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="6899c-170">1단계에서 만든 게시자 연결을 사용하여 <xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-170">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="6899c-171"><xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 및 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-171">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="6899c-172"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-172">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="6899c-173">이 메서드가 `false`를 반환하는 경우 5단계에서 지정한 속성이 올바르지 않거나 서버에 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-173">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="6899c-174"><xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-174">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="6899c-175">*subscriber* 및 *subscriberDB* 매개 변수에 구독자의 이름과 구독 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-175">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="6899c-176">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="6899c-176">Examples (RMO)</span></span>  
 <span data-ttu-id="6899c-177">이 예에서는 트랜잭션 게시에 대한 끌어오기 구독을 삭제하고 게시자에서 구독 등록을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-177">This example deletes a pull subscription to a transactional publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 <span data-ttu-id="6899c-178">이 예에서는 병합 게시에 대한 끌어오기 구독을 삭제하고 게시자에서 구독 등록을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6899c-178">This example deletes a pull subscription to a merge publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a><span data-ttu-id="6899c-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6899c-179">See Also</span></span>  
 <span data-ttu-id="6899c-180">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="6899c-180">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="6899c-181">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="6899c-181">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
