---
title: 게시 및 배포 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8843dac310d1e023fe7ce63eded02c9e1bed3731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646923"
---
# <a name="disable-publishing-and-distribution"></a><span data-ttu-id="af2ef-102">게시 및 배포 해제</span><span class="sxs-lookup"><span data-stu-id="af2ef-102">Disable Publishing and Distribution</span></span>
  <span data-ttu-id="af2ef-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 게시 및 배포를 해제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-103">This topic describes how to disable publishing and distribution in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="af2ef-104">사용할 수 있는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-104">You can do the following:</span></span>  
  
-   <span data-ttu-id="af2ef-105">배포자에서 모든 배포 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-105">Delete all distribution databases on the Distributor.</span></span>  
  
-   <span data-ttu-id="af2ef-106">배포자를 사용하는 모든 게시자를 해제하고 이 게시자의 게시를 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-106">Disable all Publishers that use the Distributor and delete all publications on those Publishers.</span></span>  
  
-   <span data-ttu-id="af2ef-107">게시에 대한 구독을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-107">Delete all subscriptions to the publications.</span></span> <span data-ttu-id="af2ef-108">게시 및 구독 데이터베이스의 데이터는 삭제되지 않지만 게시 데이터베이스에 대한 동기화 관계는 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-108">Data in the publication and subscription databases will not be deleted; however, it loses its synchronization relationship to any publication databases.</span></span> <span data-ttu-id="af2ef-109">구독자의 데이터는 수동으로만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-109">If you want the data at the Subscriber to be deleted, you must delete it manually.</span></span>  
  
 <span data-ttu-id="af2ef-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="af2ef-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="af2ef-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="af2ef-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="af2ef-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="af2ef-112">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="af2ef-113">**다음을 사용하여 게시 및 배포를 해제하려면**</span><span class="sxs-lookup"><span data-stu-id="af2ef-113">**To disable publishing and distribution, using:**</span></span>  
  
     [<span data-ttu-id="af2ef-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af2ef-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="af2ef-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af2ef-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="af2ef-116">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="af2ef-116">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af2ef-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="af2ef-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="af2ef-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="af2ef-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="af2ef-119">게시 및 배포를 해제하려면 모든 배포 및 게시 데이터베이스가 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-119">To disable publishing and distribution, all distribution and publication databases must be online.</span></span> <span data-ttu-id="af2ef-120">배포 또는 게시 데이터베이스에 대한 *데이터베이스 스냅샷* 이 있는 경우 이 스냅샷을 먼저 삭제한 다음 게시 및 배포를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-120">If any *database snapshots* exist for distribution or publication databases, they must be dropped before disabling publishing and distribution.</span></span> <span data-ttu-id="af2ef-121">데이터베이스 스냅샷은 데이터베이스의 읽기 전용 오프라인 사본이며 복제 스냅샷과 연관되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-121">A database snapshot is a read-only offline copy of a database and is not related to a replication snapshot.</span></span> <span data-ttu-id="af2ef-122">자세한 내용은 [데이터베이스 스냅샷&#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2ef-122">For more information, see [Database Snapshots &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af2ef-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="af2ef-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="af2ef-124">게시 및 배포 해제 마법사를 사용하여 게시 및 배포를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-124">Disable publishing and distribution by using the Disable Publishing and Distribution Wizard.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="af2ef-125">게시 및 배포를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="af2ef-125">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="af2ef-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 해제할 게시자나 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-126">Connect to the Publisher or Distributor you want to disable in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="af2ef-127">**복제** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **게시 및 배포 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-127">Right-click the **Replication** folder, and then click **Disable Publishing and Distribution**.</span></span>  
  
3.  <span data-ttu-id="af2ef-128">게시 및 배포 해제 마법사의 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-128">Complete the steps in the Disable Publishing and Distribution Wizard.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af2ef-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="af2ef-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="af2ef-130">복제 저장 프로시저를 사용하여 게시 및 배포를 프로그래밍 방식으로 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-130">Publishing and distributing can be disabled programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="af2ef-131">게시 및 배포를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="af2ef-131">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="af2ef-132">모든 복제 관련 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-132">Stop all replication-related jobs.</span></span> <span data-ttu-id="af2ef-133">작업 이름 목록은 [복제 에이전트 보안 모델](security/replication-agent-security-model.md)의 "SQL Server 에이전트의 에이전트 보안" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2ef-133">For a list of job names, see the "Agent Security Under SQL Server Agent" section of [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
2.  <span data-ttu-id="af2ef-134">구독 데이터베이스의 각 구독자에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 을 실행하여 데이터베이스에서 복제 개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-134">At each Subscriber on the subscription database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span> <span data-ttu-id="af2ef-135">이 저장 프로시저는 배포자의 복제 작업은 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-135">This stored procedure will not remove replication jobs at the Distributor.</span></span>  
  
3.  <span data-ttu-id="af2ef-136">게시 데이터베이스의 게시자에서 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 을 실행하여 데이터베이스에서 복제 개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-136">At the Publisher on the publication database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span>  
  
4.  <span data-ttu-id="af2ef-137">게시자가 원격 배포자를 사용하는 경우 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-137">If the Publisher uses a remote Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql).</span></span>  
  
5.  <span data-ttu-id="af2ef-138">배포자에서 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-138">At the Distributor, execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span> <span data-ttu-id="af2ef-139">이 저장 프로시저는 배포자에 등록된 각 게시자에 대해 한 번만 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-139">This stored procedure should be run once for each Publisher registered at the Distributor.</span></span>  
  
6.  <span data-ttu-id="af2ef-140">배포자에서 [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) 를 실행하여 배포 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-140">At the Distributor, execute [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) to delete the distribution database.</span></span> <span data-ttu-id="af2ef-141">이 저장 프로시저는 배포자의 각 배포 데이터베이스에 대해 한 번만 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-141">This stored procedure should be run once for each distribution database at the Distributor.</span></span> <span data-ttu-id="af2ef-142">그러면 배포 데이터베이스와 연결된 모든 큐 판독기 에이전트 작업도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-142">This also removes any Queue Reader Agent jobs associated with the distribution database.</span></span>  
  
7.  <span data-ttu-id="af2ef-143">배포자에서 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) 를 실행하여 서버에서 배포자 지정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-143">At the Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) to remove the Distributor designation from the server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="af2ef-144">모든 복제 게시 및 배포 개체가 삭제되지 않은 상태로 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) 및 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)를 실행하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-144">If all replication publishing and distribution objects are not dropped before you execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) and [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql), these procedures will return an error.</span></span> <span data-ttu-id="af2ef-145">게시자 또는 배포자를 삭제할 때 모든 복제 관련 개체를 삭제 하려면 \*\* \@ no_checks\*\* 매개 변수를 **1**로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-145">To drop all replication-related objects when a Publisher or Distributor is dropped, the **\@no_checks** parameter must be set to **1**.</span></span> <span data-ttu-id="af2ef-146">게시자 또는 배포자가 오프 라인 이거나 연결할 수 없는 경우에는 \*\* \@ ignore_distributor\*\* 매개 변수를 **1** 로 설정 하 여 삭제할 수 있습니다. 그러나 남아 있는 모든 게시 및 배포 개체는 수동으로 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-146">If a Publisher or Distributor is offline or unreachable, the **\@ignore_distributor** parameter can be set to **1** so that they can be dropped; however, any publishing and distributing objects left behind must be removed manually.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="af2ef-147">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="af2ef-147">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="af2ef-148">다음 스크립트 예에서는 구독 데이터베이스에서 복제 개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-148">This example script removes replication objects from the subscription database.</span></span>  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 <span data-ttu-id="af2ef-149">다음 스크립트 예에서는 게시자 및 배포자 역할의 서버에서 게시 및 배포를 해제하고 배포 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-149">This example script disables publishing and distribution on a server that is a Publisher and Distributor and drops the distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="af2ef-150">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="af2ef-150">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="af2ef-151">게시 및 배포를 해제하려면</span><span class="sxs-lookup"><span data-stu-id="af2ef-151">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="af2ef-152">배포자를 사용하는 게시에 대한 모든 구독을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-152">Remove all subscriptions to publications that use the Distributor.</span></span> <span data-ttu-id="af2ef-153">자세한 내용은 [Delete a Pull Subscription](delete-a-pull-subscription.md) 및 [Delete a Push Subscription](delete-a-push-subscription.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2ef-153">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md) and [Delete a Push Subscription](delete-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="af2ef-154">배포자를 사용하는 모든 게시를 제거하고 게시자와 배포자가 동일한 서버에 있는 경우에는 모든 데이터베이스에 대한 게시를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-154">Remove all publications that use the Distributor, and disable publishing for all databases if the Publisher and Distributor are on the same server.</span></span> <span data-ttu-id="af2ef-155">자세한 내용은 [Delete a Publication](publish/delete-a-publication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2ef-155">For more information, see [Delete a Publication](publish/delete-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="af2ef-156"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
4.  <span data-ttu-id="af2ef-157"><xref:Microsoft.SqlServer.Replication.DistributionPublisher> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="af2ef-158"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 속성을 지정하고 3단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-158">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property, and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
5.  <span data-ttu-id="af2ef-159">필요에 따라 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 개체의 속성을 얻고 게시자가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-159">(Optional) Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object and verify that the Publisher exists.</span></span> <span data-ttu-id="af2ef-160">이 메서드가 `false`를 반환하면 4단계에서 지정한 게시자 이름이 올바르지 않거나 이 배포자에서 게시자를 사용하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-160">If this method returns `false`, the Publisher name set in step 4 was incorrect or the Publisher is not used by this Distributor.</span></span>  
  
6.  <span data-ttu-id="af2ef-161"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-161">Call the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> method.</span></span> <span data-ttu-id="af2ef-162">`true`게시자와 배포자가 다른 서버에 있고 게시자에 게시가 더 이상 존재 하지 않는지 먼저 확인 하지 않고 배포자에서 게시자를 제거 해야 하 *는 경우* 에는 값을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-162">Pass a value of `true` for *force* if the Publisher and Distributor are on different servers, and when the Publisher should be uninstalled at the Distributor without first verifying that publications no longer exist at the Publisher.</span></span>  
  
7.  <span data-ttu-id="af2ef-163"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-163">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="af2ef-164">3단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-164">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
8.  <span data-ttu-id="af2ef-165"><xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-165">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> method.</span></span> <span data-ttu-id="af2ef-166">`true`모든 로컬 게시 데이터베이스가 사용 하지 않도록 설정 되어 있고 배포 데이터베이스가 제거 되었는지 먼저 확인 하지 않고 배포자에서 모든 복제 개체를 제거 하려면 *값을 전달* 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-166">Pass a value of `true` for *force* to remove all replication objects at the Distributor without first verifying that all local publication databases have been disabled, and distribution databases have been uninstalled.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="af2ef-167">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="af2ef-167">Examples (RMO)</span></span>  
 <span data-ttu-id="af2ef-168">다음 예에서는 배포자에서 게시 등록을 제거하고 배포 데이터베이스 삭제하며 배포자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-168">This example removes the Publisher registration at the Distributor, drops the distribution database, and uninstalls the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 <span data-ttu-id="af2ef-169">다음 예에서는 먼저 로컬 게시 데이터베이스를 해제하거나 배포 데이터베이스를 삭제하지 않고 배포자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="af2ef-169">This example uninstalls the Distributor without first disabling local publication databases or dropping the distribution database.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a><span data-ttu-id="af2ef-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af2ef-170">See Also</span></span>  
 <span data-ttu-id="af2ef-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="af2ef-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="af2ef-172">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="af2ef-172">Replication System Stored Procedures Concepts</span></span>](concepts/replication-system-stored-procedures-concepts.md)  
  
  
