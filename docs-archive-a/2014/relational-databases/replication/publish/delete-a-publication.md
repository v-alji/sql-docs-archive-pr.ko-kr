---
title: 게시 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d2b39a326d59333868b4f8015eb9a2e59d59e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741780"
---
# <a name="delete-a-publication"></a><span data-ttu-id="580ab-102">게시 삭제</span><span class="sxs-lookup"><span data-stu-id="580ab-102">Delete a Publication</span></span>
  <span data-ttu-id="580ab-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 게시를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-103">This topic describes how to delete a publication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="580ab-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="580ab-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="580ab-105">**게시를 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="580ab-105">**To delete a publication, using:**</span></span>  
  
     [<span data-ttu-id="580ab-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="580ab-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="580ab-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="580ab-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="580ab-108">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="580ab-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="580ab-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="580ab-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="580ab-110">**의** 로컬 게시 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]폴더에서 게시를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-110">Delete publications from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-a-publication"></a><span data-ttu-id="580ab-111">게시를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="580ab-111">To delete a publication</span></span>  
  
1.  <span data-ttu-id="580ab-112">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="580ab-113">**복제** 폴더를 확장한 다음 **로컬 게시** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="580ab-114">삭제할 게시를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-114">Right-click the publication you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="580ab-115">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="580ab-115">Using Transact-SQL</span></span>  
 <span data-ttu-id="580ab-116">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 게시를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-116">Publications can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="580ab-117">사용하는 저장 프로시저는 삭제하려는 게시의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-117">The stored procedures that you use depend on the type of publication being deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="580ab-118">게시를 삭제해도 게시 데이터베이스의 게시된 개체 또는 구독 데이터베이스의 해당 개체는 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-118">Deleting a publication does not remove published objects from the publication database or the corresponding objects from the subscription database.</span></span> <span data-ttu-id="580ab-119">필요한 경우 `DROP <object>` 명령을 사용하여 이러한 개체를 수동으로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-119">Use the `DROP <object>` command to manually remove these objects if necessary.</span></span>  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a><span data-ttu-id="580ab-120">스냅샷 또는 트랜잭션 게시를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="580ab-120">To delete a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="580ab-121">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="580ab-122">단일 게시를 삭제하려면 게시 데이터베이스의 게시자에서 [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-122">To delete a single publication, execute [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="580ab-123">모든 게시를 삭제하고 게시된 데이터베이스에서 모든 복제 개체를 제거하려면 게시자에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-123">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="580ab-124">`tran` \*\* \@ 형식\*\*에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-124">Specify a value of `tran` for **\@type**.</span></span> <span data-ttu-id="580ab-125">(옵션) 배포자에 액세스할 수 없거나 데이터베이스의 상태가 주의 대상 또는 오프라인인 경우 **\@force**에 값 **1**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-125">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="580ab-126">(옵션) 게시 데이터베이스에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)이 실행되지 않은 경우 **\@dbname**에 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-126">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="580ab-127">**\@force**에 값 **1**을 지정하면 데이터베이스에 복제 관련 게시 개체가 남을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-127">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="580ab-128">(선택 사항) 이 데이터베이스에 다른 게시가 없으면 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행하여 스냅샷 또는 트랜잭션 복제를 통해 현재 데이터베이스를 게시할 수 없도록 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-128">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using snapshot or transactional replication.</span></span>  
  
3.  <span data-ttu-id="580ab-129">(옵션) 구독 데이터베이스의 구독자에서 [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) 을 실행하여 구독 데이터베이스에 남은 모든 복제 메타데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-129">(Optional) At the Subscriber on the subscription database, execute [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-merge-publication"></a><span data-ttu-id="580ab-130">병합 게시를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="580ab-130">To delete a merge publication</span></span>  
  
1.  <span data-ttu-id="580ab-131">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-131">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="580ab-132">단일 게시를 삭제하려면 게시 데이터베이스의 게시자에서 [sp_dropmergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-132">To delete a single publication, execute [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="580ab-133">모든 게시를 삭제하고 게시된 데이터베이스에서 모든 복제 개체를 제거하려면 게시자에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-133">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="580ab-134">`merge` \*\* \@ 형식\*\*에 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-134">Specify a value of `merge` for **\@type**.</span></span> <span data-ttu-id="580ab-135">(옵션) 배포자에 액세스할 수 없거나 데이터베이스의 상태가 주의 대상 또는 오프라인인 경우 **\@force**에 값 **1**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-135">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="580ab-136">(옵션) 게시 데이터베이스에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)이 실행되지 않은 경우 **\@dbname**에 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-136">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="580ab-137">**\@force**에 값 **1**을 지정하면 데이터베이스에 복제 관련 게시 개체가 남을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-137">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="580ab-138">(선택 사항) 이 데이터베이스에 다른 게시가 없으면 [sp_replicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)을 실행하여 병합 복제를 통해 현재 데이터베이스를 게시할 수 없도록 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-138">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using merge replication.</span></span>  
  
3.  <span data-ttu-id="580ab-139">(선택 사항) 구독 데이터베이스의 구독자에서 [sp_mergesubscription_cleanup&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql)을 실행하여 구독 데이터베이스에 남은 모든 복제 메타데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-139">(Optional) At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="580ab-140">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="580ab-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="580ab-141">다음 예에서는 트랜잭션 게시를 제거하고 데이터베이스에 대한 트랜잭션 게시를 해제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-141">This example shows how to remove a transactional publication and disable transactional publishing for a database.</span></span> <span data-ttu-id="580ab-142">이 예에서는 모든 구독이 이전에 제거되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-142">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="580ab-143">자세한 내용은 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 또는 [Delete a Push Subscription](../delete-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="580ab-143">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_droppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droppublication)]  
  
 <span data-ttu-id="580ab-144">다음 예에서는 병합 게시를 제거하고 데이터베이스에 대한 병합 게시를 해제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-144">This example shows how to remove a merge publication and disable merge publishing for a database.</span></span> <span data-ttu-id="580ab-145">이 예에서는 모든 구독이 이전에 제거되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-145">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="580ab-146">자세한 내용은 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 또는 [Delete a Push Subscription](../delete-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="580ab-146">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="580ab-147">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="580ab-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="580ab-148">RMO(복제 관리 개체)를 사용하여 프로그래밍 방식으로 게시를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-148">You can delete publications programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="580ab-149">게시를 제거하는 데 사용하는 RMO 클래스는 제거하는 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-149">The RMO classes that you use to remove a publication depend on the type of publication you remove.</span></span>  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a><span data-ttu-id="580ab-150">스냅샷 또는 트랜잭션 게시를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="580ab-150">To remove a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="580ab-151"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="580ab-152"><xref:Microsoft.SqlServer.Replication.TransPublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="580ab-153">게시에 대해 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-153">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="580ab-154"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 통해 게시가 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="580ab-155">이 속성의 값이 `false`이면 3단계의 게시 속성이 올바르게 정의되지 않았거나 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-155">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="580ab-156"><xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-156">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="580ab-157">(옵션) 이 데이터베이스에 대한 다른 트랜잭션 게시가 없는 경우 다음과 같이 트랜잭션 게시에 대해 데이터베이스를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-157">(Optional) If no other transactional publications exist for this database, the database can be disabled for transactional publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="580ab-158"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-158">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="580ab-159"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-159">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
    2.  <span data-ttu-id="580ab-160"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="580ab-161">이 메서드가 `false`를 반환할 경우 데이터베이스가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-161">If this method returns `false`, confirm that the database exists.</span></span>  
  
    3.  <span data-ttu-id="580ab-162"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> 속성을 `false`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-162">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="580ab-163"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-163">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="580ab-164">연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-164">Close the connections.</span></span>  
  
#### <a name="to-remove-a-merge-publication"></a><span data-ttu-id="580ab-165">병합 게시를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="580ab-165">To remove a merge publication</span></span>  
  
1.  <span data-ttu-id="580ab-166"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-166">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="580ab-167"><xref:Microsoft.SqlServer.Replication.MergePublication> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-167">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span>  
  
3.  <span data-ttu-id="580ab-168">게시에 대해 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 및 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 속성을 설정하고 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-168">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="580ab-169"><xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 속성을 통해 게시가 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-169">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="580ab-170">이 속성의 값이 `false`이면 3단계의 게시 속성이 올바르게 정의되지 않았거나 게시가 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-170">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="580ab-171"><xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-171">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="580ab-172">(옵션) 이 데이터베이스에 대한 다른 병합 게시가 없는 경우 다음과 같이 병합 게시에 대해 데이터베이스를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-172">(Optional) If no other merge publications exist for this database, the database can be disabled for merge publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="580ab-173"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="580ab-174"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-174">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from Step 1.</span></span>  
  
    2.  <span data-ttu-id="580ab-175"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-175">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="580ab-176">이 메서드가 `false`를 반환하면 데이터베이스가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-176">If this method returns `false`, verify that the database exists.</span></span>  
  
    3.  <span data-ttu-id="580ab-177"><xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> 속성을 `false`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-177">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="580ab-178"><xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="580ab-179">연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-179">Close the connections.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="580ab-180">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="580ab-180">Examples (RMO)</span></span>  
 <span data-ttu-id="580ab-181">다음 예에서는 트랜잭션 게시를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-181">The following example deletes a transactional publication.</span></span> <span data-ttu-id="580ab-182">이 데이터베이스에 대한 다른 트랜잭션 게시가 없으면 트랜잭션 게시도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-182">If no other transactional publications exist for this database, transactional publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 <span data-ttu-id="580ab-183">다음 예에서는 병합 게시를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-183">The following example deletes a merge publication.</span></span> <span data-ttu-id="580ab-184">이 데이터베이스에 대한 다른 병합 게시가 없으면 병합 게시도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="580ab-184">If no other merge publications exist for this database, merge publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a><span data-ttu-id="580ab-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="580ab-185">See Also</span></span>  
 <span data-ttu-id="580ab-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="580ab-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="580ab-187">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="580ab-187">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
