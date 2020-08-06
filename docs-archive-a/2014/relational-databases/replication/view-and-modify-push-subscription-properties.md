---
title: 밀어넣기 구독 속성 보기 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1506d4f83fcfb94d62efd01c4d6447048fecfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738176"
---
# <a name="view-and-modify-push-subscription-properties"></a><span data-ttu-id="3341e-102">밀어넣기 구독 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="3341e-102">View and Modify Push Subscription Properties</span></span>
  <span data-ttu-id="3341e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 밀어넣기 구독 속성을 보고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-103">This topic describes how to view and modify push subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="3341e-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3341e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3341e-105">**다음을 사용하여 밀어넣기 구독 속성을 보고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="3341e-105">**To view and modify push subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="3341e-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3341e-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3341e-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3341e-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="3341e-108">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="3341e-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3341e-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3341e-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3341e-110">다음 위치에서 게시자의 밀어넣기 구독 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-110">View and modify push subscription properties from the Publisher in:</span></span>  
  
-   <span data-ttu-id="3341e-111">**구독 속성 - \<Publisher>: \<PublicationDatabase>** 대화 상자 - [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-111">The **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="3341e-112">**모든 구독** 탭 - 복제 모니터에서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-112">The **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="3341e-113">복제 모니터를 시작하는 방법은 [복제 모니터 시작](monitor/start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3341e-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a><span data-ttu-id="3341e-114">Management Studio에서 밀어넣기 구독 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-114">To view and modify push subscription properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="3341e-115">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="3341e-116">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="3341e-117">해당 게시를 확장하고 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3341e-118">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-118">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a><span data-ttu-id="3341e-119">복제 모니터에서 밀어넣기 구독 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-119">To view and modify push subscription properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="3341e-120">복제 모니터에서 왼쪽 창의 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-120">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="3341e-121">**모든 구독** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-121">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="3341e-122">해당 구독을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3341e-123">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3341e-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3341e-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="3341e-125">밀어넣기 구독은 수정할 수 있으며 해당 속성은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-125">Push subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="3341e-126">사용되는 저장 프로시저는 구독이 속한 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-126">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3341e-127">스냅샷 또는 트랜잭션 게시에 대한 밀어넣기 구독의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="3341e-127">To view the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3341e-128">게시 데이터베이스의 게시자에서 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-128">At the Publisher on the publication database, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="3341e-129">**@publication**, **@subscriber** 및에 **all** 값을 지정 **@article** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-129">Specify **@publication**, **@subscriber**, and a value of **all** for **@article**.</span></span>  
  
2.  <span data-ttu-id="3341e-130">게시 데이터베이스의 게시자에서 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)를 실행하고 **@subscriber**에서 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-130">At the Publisher on the publication database, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3341e-131">스냅샷 또는 트랜잭션 게시에 대한 밀어넣기 구독의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-131">To change the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3341e-132">게시 데이터베이스의 게시자에서 [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)를 실행하고 **@subscriber** 를 지정하며 변경할 구독자 속성의 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-132">At the Publisher on the publication database, execute [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql), specifying **@subscriber** and any parameters for the Subscriber properties being changed.</span></span>  
  
2.  <span data-ttu-id="3341e-133">게시 데이터베이스의 게시자에서 [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-133">At the Publisher on the publication database, execute [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql).</span></span> <span data-ttu-id="3341e-134">,,, 값을 모두로 지정 하 고, **@publication** **@subscriber** **@destination_db** **all** **@article** 구독 속성을로 변경 하 **@property** 고, 새 값을로 **@value** 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-134">Specify **@publication**, **@subscriber**, **@destination_db**, a value of **all** for **@article**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span> <span data-ttu-id="3341e-135">이렇게 하면 밀어넣기 구독의 보안 설정이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-135">This changes security settings for the push subscription.</span></span>  
  
3.  <span data-ttu-id="3341e-136">(옵션) 구독의 DTS(데이터 변환 서비스) 패키지 속성을 변경하려면 구독 데이터베이스의 구독자에서 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-136">(Optional) To change the Data Transformation Services (DTS) package properties of a subscription, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="3341e-137">에 배포 에이전트 작업의 ID를 지정 **@jobid** 하 고 다음과 같은 DTS 패키지 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-137">Specify the ID of the Distribution Agent job for **@jobid** and the following DTS package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="3341e-138">이렇게 하면 구독의 DTS 패키지 속성이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-138">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3341e-139">작업 ID는 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-139">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="3341e-140">병합 게시에 대한 밀어넣기 구독의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="3341e-140">To view the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="3341e-141">게시 데이터베이스의 게시자에서 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-141">At the Publisher on the publication database, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql).</span></span> <span data-ttu-id="3341e-142">**@publication**및를 지정 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-142">Specify **@publication** and **@subscriber**.</span></span>  
  
2.  <span data-ttu-id="3341e-143">게시자에서를 지정 하 여 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)를 실행 **@subscriber** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-143">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="3341e-144">병합 게시에 대한 밀어넣기 구독의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-144">To change the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="3341e-145">게시 데이터베이스의 게시자에서 [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-145">At the Publisher on the publication database, execute [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql).</span></span> <span data-ttu-id="3341e-146">**@publication**, **@subscriber** , **@subscriber_db** , 변경 되는 구독 속성 **@property** , 새 값 **@value** 을로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-146">Specify **@publication**, **@subscriber**, **@subscriber_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3341e-147">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3341e-147">Example (Transact-SQL)</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="3341e-148">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="3341e-148">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="3341e-149">밀어넣기 구독 속성을 보거나 수정하는 데 사용되는 RMO 클래스는 밀어넣기 구독이 구독하는 게시의 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-149">The RMO classes you use to view or modify push subscription properties depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3341e-150">스냅샷 또는 트랜잭션 게시에 대한 밀어넣기 구독의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-150">To view or modify properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3341e-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="3341e-152"><xref:Microsoft.SqlServer.Replication.TransSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="3341e-153"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>및 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-153">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="3341e-154"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성 설정에 1단계의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-154">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="3341e-155"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-155">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="3341e-156">이 메서드가 `false`를 반환하는 경우 3단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-156">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="3341e-157">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.TransSubscription> 속성 중 하나에 대해 새 값을 설정한 다음 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-157">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="3341e-158">(옵션) 새 설정을 보려면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 메서드를 호출하여 구독에 대한 속성을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-158">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="3341e-159">병합 게시에 대한 밀어넣기 구독의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="3341e-159">To view or modify properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="3341e-160"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 구독자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-160">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="3341e-161"><xref:Microsoft.SqlServer.Replication.MergeSubscription> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-161">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="3341e-162"><xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>및 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-162">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="3341e-163"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성 설정에 1단계의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-163">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="3341e-164"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-164">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="3341e-165">이 메서드가 `false`를 반환하는 경우 3단계에서 구독 속성이 올바르게 정의되지 않았거나 구독이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-165">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="3341e-166">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 속성 중 하나에 대해 새 값을 설정한 다음 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-166">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="3341e-167">(옵션) 새 설정을 보려면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 메서드를 호출하여 구독에 대한 속성을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3341e-167">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3341e-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3341e-168">See Also</span></span>  
 <span data-ttu-id="3341e-169">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3341e-169">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="3341e-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="3341e-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="3341e-171">게시 구독</span><span class="sxs-lookup"><span data-stu-id="3341e-171">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
