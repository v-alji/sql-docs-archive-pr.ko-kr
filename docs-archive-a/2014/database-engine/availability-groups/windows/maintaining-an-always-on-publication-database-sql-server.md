---
title: AlwaysOn 게시 데이터베이스 유지 관리 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8f36d29049140b6e5bbdfc1a4e716d41a766a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650261"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a><span data-ttu-id="42419-102">AlwaysOn 게시 데이터베이스 유지 관리(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="42419-102">Maintaining an AlwaysOn Publication Database (SQL Server)</span></span>
  <span data-ttu-id="42419-103">이 항목에서는 AlwaysOn 가용성 그룹을 사용할 경우 게시 데이터베이스 유지 관리와 관련하여 특별히 고려해야 할 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-103">This topic discusses special considerations for maintaining a publication database when you use AlwaysOn availability groups.</span></span>  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a><span data-ttu-id="42419-104">가용성 그룹에서 게시 된 데이터베이스 유지 관리</span><span class="sxs-lookup"><span data-stu-id="42419-104">Maintaining a Published Database in an Availability Group</span></span>  
 <span data-ttu-id="42419-105">AlwaysOn 게시 데이터베이스를 유지 관리하는 작업은 표준 게시 데이터베이스를 유지 관리하는 작업과 기본적으로 동일하지만 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-105">Maintaining an AlwaysOn publication database is basically the same as maintaining a standard publication database, with the following considerations:</span></span>  
  
-   <span data-ttu-id="42419-106">관리는 주 복제본 호스트에서 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-106">Administration must occur at the primary replica host.</span></span> <span data-ttu-id="42419-107">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 게시는 **로컬 게시** 폴더 아래에 주 복제본 호스트 및 읽을 수 있는 보조 복제본을 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42419-107">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], publications appear under the **Local Publications** folder for the primary replica host and also for readable secondary replicas.</span></span> <span data-ttu-id="42419-108">읽을 수 없는 보조 복제본이 주 복제본으로 승격된 경우 장애 조치(failover) 후 수동으로 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 를 새로 고쳐 변경 내용을 반영해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-108">After failover, you might have to manually refresh [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] for the change to be reflected if the secondary that was promoted to primary was not readable.</span></span>  
  
-   <span data-ttu-id="42419-109">복제 모니터는 항상 원래 게시자에서 게시 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-109">Replication Monitor always displays publication information under the original publisher.</span></span> <span data-ttu-id="42419-110">그러나 원래 게시자를 서버로 추가하면 어떤 복제본에서든지 복제 모니터에서 이 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42419-110">However, this information can be viewed in Replication Monitor from any replica by adding the original publisher as a server.</span></span>  
  
-   <span data-ttu-id="42419-111">게시자 이름 지정 등을 위해 저장 프로시저나 RMO(복제 관리 개체)를 사용하여 현재 주 복제본에서 복제를 관리할 때는 복제용으로 설정된 데이터베이스(원래 게시자)에서 인스턴스 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-111">When using stored procedures or Replication Management Objects (RMO) to administer replication at the current primary, for cases in which you specify the Publisher name, you must specify the name of the instance on which the database was enabled for replication (the original publisher).</span></span> <span data-ttu-id="42419-112">올바른 이름을 확인하려면 `PUBLISHINGSERVERNAME` 함수를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="42419-112">To determine the appropriate name, use the `PUBLISHINGSERVERNAME` function.</span></span> <span data-ttu-id="42419-113">게시 데이터베이스를 가용성 그룹에 조인하면 보조 데이터베이스 복제본에 저장된 복제 메타데이터가 주 데이터베이스 복제본의 복제 메타데이터와 동일해집니다.</span><span class="sxs-lookup"><span data-stu-id="42419-113">When a publishing database joins an availability group, the replication metadata stored in the secondary database replicas is identical to that at the primary.</span></span> <span data-ttu-id="42419-114">따라서 주 서버에서 복제용으로 설정된 게시 데이터베이스의 경우 보조 서버에서 시스템 테이블에 저장된 게시자 인스턴스 이름은 보조 서버가 아닌 주 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="42419-114">Consequently, for publication databases enabled for replication at the primary, the publisher instance name stored in system tables at the secondary is the name of the primary, not the secondary.</span></span> <span data-ttu-id="42419-115">이러한 방식은 게시 데이터베이스가 보조로 장애 조치되는 경우 복제 구성 및 유지 관리에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42419-115">This affects replication configuration and maintenance if the publication database fails over to a secondary.</span></span> <span data-ttu-id="42419-116">예를 들어 장애 조치 (failover) 후 보조 데이터베이스에 저장 프로시저를 사용 하 여 복제를 구성 하 고 다른 복제본에서 사용 하도록 설정 된 게시 데이터베이스에 대 한 끌어오기 구독을 사용 하려는 경우에는 현재 게시자 대신 *@publisher* 또는의 매개 변수로 원래 게시자 이름을 지정 해야 합니다 `sp_addpullsubscription` `sp_addmergepulllsubscription` .</span><span class="sxs-lookup"><span data-stu-id="42419-116">For example, if you are configuring replication with stored procedures at a secondary after failover, and you want a pull subscription to a publication database that was enabled at a different replica, you must specify the name of the original publisher instead of the current publisher as the *@publisher* parameter of `sp_addpullsubscription` or `sp_addmergepulllsubscription`.</span></span> <span data-ttu-id="42419-117">그러나 장애 조치 후 게시 데이터베이스를 활성화하면 시스템 테이블에 저장된 게시자 인스턴스 이름이 현재 주 호스트의 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42419-117">However, if you enable a publication database after failover, the publisher instance name stored in the system tables is the name of the current primary host.</span></span> <span data-ttu-id="42419-118">이 경우 매개 변수에 대해 현재 주 복제본의 호스트 이름을 사용 *@publisher* 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-118">In this case, you would use the host name of the current primary replica for the *@publisher* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42419-119">와 같은 일부 프로시저의 경우 `sp_addpublication` *@publisher* 매개 변수는 인스턴스가 아닌 게시자에 대해서만 지원 되며, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이 경우 AlwaysOn과는 관련이 없습니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="42419-119">For some procedures, such as `sp_addpublication`, the *@publisher* parameter is supported only for publishers that are not instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; in these cases, it is not relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.</span></span>  
  
-   <span data-ttu-id="42419-120">장애 조치 후 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 에서 구독을 동기화하려면 구독자에서 끌어오기 구독을 동기화하고 활성 게시자에서 밀어넣기 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-120">To synchronize a subscription in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] after a failover, synchronize pull subscriptions from the subscriber and synchronize push subscriptions from the active publisher.</span></span>  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a><span data-ttu-id="42419-121">가용성 그룹에서 게시 된 데이터베이스 제거</span><span class="sxs-lookup"><span data-stu-id="42419-121">Removing a Published Database from an Availability Group</span></span>  
 <span data-ttu-id="42419-122">게시된 데이터베이스를 가용성 그룹에서 제거하거나 게시된 멤버 데이터베이스가 있는 가용성 그룹을 삭제할 경우 다음 문제를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="42419-122">Consider the following issues if a published database is removed from an availability group, or if an availability group that has a published member database is dropped.</span></span>  
  
-   <span data-ttu-id="42419-123">원본 게시자의 게시 데이터베이스가 가용성 그룹 주 복제본에서 제거 된 경우에는 `sp_redirect_publisher` *@redirected_publisher* 게시자/데이터베이스 쌍에 대 한 리디렉션을 제거 하기 위해 매개 변수의 값을 지정 하지 않고를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-123">If the publication database at the original publisher is removed from an availability group primary replica, you must run `sp_redirect_publisher` without specifying a value for the *@redirected_publisher* parameter in order to remove the redirection for the publisher/database pair.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     <span data-ttu-id="42419-124">주 복제본에서 데이터베이스가 복구 중 상태로 남게 되므로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-124">The database will be left in the recovering state at the primary and must be restored.</span></span> <span data-ttu-id="42419-125">이렇게 하면 원래 게시자에 대해 복제가 변함 없이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-125">Once you do this, replication should work unchanged against the original Publisher.</span></span>  
  
-   <span data-ttu-id="42419-126">게시 데이터베이스를 원래 게시자에서 복제본으로 장애 조치하며 데이터베이스를 가용성 그룹 주 복제본에서 제거할 경우 `sp_redirect_publisher` 저장 프로시저를 실행하여 원래 게시자를 명시적으로 새 게시자로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-126">If the publication database fails over from the original publisher to a replica and the database is removed from the availability group primary replica, use the stored procedure `sp_redirect_publisher` to explicitly redirect the original publisher to the new publisher.</span></span> <span data-ttu-id="42419-127">데이터베이스가 복구 중 상태로 남게 되므로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-127">The database will be left in the recovering state and must be restored.</span></span> <span data-ttu-id="42419-128">이렇게 하면 가용성 그룹에 있을 때와 마찬가지로 복제가 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-128">Once you do this, replication should continue to work as it did under the availability group.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     <span data-ttu-id="42419-129">서버에 더 이상 액세스할 수 없더라도 원래 게시자의 원격 서버를 배포자에서 제거하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="42419-129">Do not remove the remote server for the original publisher from the distributor, even if the server can no longer be accessed.</span></span> <span data-ttu-id="42419-130">게시 메타데이터 쿼리를 충족하려면 배포자에 원래 게시자의 서버 메타데이터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-130">The server metadata for the original publisher is needed at the distributor to satisfy publication metadata queries.</span></span>  
  
-   <span data-ttu-id="42419-131">가용성 그룹 전체를 제거할 경우 복제된 멤버 데이터베이스와 관련된 동작은 게시된 데이터베이스를 가용성 그룹에서 제거할 때와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-131">If a complete availability group is removed, the behavior with regard to a member replicated database is the same as when a published database is removed from an availability group.</span></span> <span data-ttu-id="42419-132">데이터베이스를 복원하고 리디렉션을 수정한 후 곧바로 마지막 주 복제본부터 복제를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42419-132">Replication can be resumed from the last primary as soon as the database has been restored and the redirection has been modified.</span></span> <span data-ttu-id="42419-133">데이터베이스를 원래 게시자에서 복원하는 경우 리디렉션을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-133">If the database is restored at its original publisher, redirection should be removed.</span></span> <span data-ttu-id="42419-134">데이터베이스를 다른 호스트에서 복원하는 경우 새 호스트로 명시적으로 리디렉션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-134">If the database is restored at a different host, redirection should be explicitly directed to the new host.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42419-135">게시된 멤버 데이터베이스가 있는 가용성 그룹을 제거하거나 게시된 데이터베이스를 가용성 그룹에서 제거하면 게시된 데이터베이스의 모든 복사본이 복구 중 상태로 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42419-135">When an availability group is removed that has published member databases, or a published database is removed from an availability group, all copies of the published databases will be left in the recovering state.</span></span> <span data-ttu-id="42419-136">데이터베이스를 복원하면 각각이 게시된 데이터베이스로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42419-136">If restored, each will appear as a published database.</span></span> <span data-ttu-id="42419-137">한 복사본에만 게시 메타데이터를 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-137">Only one copy should be retained with publication metadata.</span></span> <span data-ttu-id="42419-138">게시된 데이터베이스 복사본에 대해 복제를 비활성화하려면 먼저 모든 구독 및 게시를 데이터베이스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-138">To disable replication for a published database copy, first remove all subscriptions and publications from the database.</span></span>  
  
     <span data-ttu-id="42419-139">`sp_dropsubscription`을 실행하여 게시의 구독을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-139">Run `sp_dropsubscription` to remove publication subscriptions.</span></span> <span data-ttu-id="42419-140">*@ignore_distributributor*배포자에서 활성 게시 데이터베이스에 대 한 메타 데이터를 유지 하려면 매개 변수를 1로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-140">Make sure to set the parameter *@ignore_distributributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="42419-141">`sp_droppublication`을 실행하여 모든 게시를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-141">Run `sp_droppublication` to remove all publications.</span></span> <span data-ttu-id="42419-142">다시 매개 변수를 *@ignore_distributor* 1로 설정 하 여 배포자의 활성 게시 데이터베이스에 대 한 메타 데이터를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-142">Again, set the parameter *@ignore_distributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="42419-143">`sp_replicationdboption`을 실행하여 데이터베이스에 대해 복제를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="42419-143">Run `sp_replicationdboption` to disable replication for the database.</span></span>  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     <span data-ttu-id="42419-144">이때 게시된 데이터베이스의 복사본을 유지하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42419-144">At this point, the copy of the published database can be retained or dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="42419-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="42419-145">Related Tasks</span></span>  
  
-   [<span data-ttu-id="42419-146">AlwaysOn 가용성 그룹에 대한 복제 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="42419-146">Configure Replication for AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="42419-147">복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="42419-147">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="42419-148">복제 관리 FAQ</span><span class="sxs-lookup"><span data-stu-id="42419-148">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [<span data-ttu-id="42419-149">복제 구독자 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="42419-149">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="42419-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42419-150">See Also</span></span>  
 <span data-ttu-id="42419-151">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="42419-151">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="42419-152">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="42419-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="42419-153">[AlwaysOn 가용성 그룹: 상호 운용성 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="42419-153">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="42419-154">SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="42419-154">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
  
  
