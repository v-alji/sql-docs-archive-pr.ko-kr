---
title: 미러된 데이터베이스의 가동 중지 시간을 최소화 하면서 시스템에 서비스 팩을 설치 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e878d31ec926f8b2cc460854f422b4d01d32d414
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734439"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a><span data-ttu-id="ee507-102">미러된 데이터베이스 작동 중단을 최소화하면서 시스템에 서비스 팩 설치</span><span class="sxs-lookup"><span data-stu-id="ee507-102">Install a Service Pack on a System with Minimal Downtime for Mirrored Databases</span></span>
  <span data-ttu-id="ee507-103">이 항목에서는 서비스 팩과 핫픽스를 설치할 때 미러된 데이터베이스의 작동 중단을 최소화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-103">This topic describes how to minimize downtime for mirrored databases when you install service packs and hotfixes.</span></span> <span data-ttu-id="ee507-104">이 프로세스에는 데이터베이스 미러링에 참여하는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 인스턴스를 순차적으로 업그레이드하는 과정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-104">This process involves sequentially upgrading the instances of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] that are participating in database mirroring.</span></span> <span data-ttu-id="ee507-105">*롤링 업데이트*라고 하는 이러한 형태의 업데이트는 단일 장애 조치 (failover)에 대해서만 가동 중지 시간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-105">This form of update, which is known as a *rolling update*, reduces downtime to only a single failover.</span></span> <span data-ttu-id="ee507-106">미러 서버가 주 서버와 지리적으로 먼 거리에 있는 성능 우선 모드 세션의 경우는 롤링 업데이트가 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-106">Note that for high-performance mode sessions in which the mirror server is geographically distant from the principal server, a rolling update might be inappropriate.</span></span>  
  
 <span data-ttu-id="ee507-107">롤링 업데이트는 다음과 같은 여러 단계로 구성되는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-107">A rolling update is a multi-stage process that consists of the following stages:</span></span>  
  
-   <span data-ttu-id="ee507-108">데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-108">Protect your data.</span></span>  
  
-   <span data-ttu-id="ee507-109">세션에 미러링 모니터가 포함되어 있는 경우 미러링 모니터를 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-109">If the session includes a witness, we recommend that you remove the witness.</span></span> <span data-ttu-id="ee507-110">미러링 모니터를 제거하지 않으면 미러 서버 인스턴스를 업데이트할 때 주 서버 인스턴스에 연결된 채로 남아있는 미러링 모니터에 의해 데이터베이스의 가용성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-110">Otherwise, when the mirror server instance is being updated, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="ee507-111">미러링 모니터를 제거하고 나면 데이터베이스 가동 중단의 위험 없이 롤링 업데이트 프로세스 도중 언제라도 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-111">After you remove a witness, you can update it at any time during the rolling update process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee507-112">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee507-112">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="ee507-113">세션이 성능 우선 모드에서 실행되는 경우 운영 모드를 보호 우선 모드로 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee507-113">If a session is running in high-performance mode, change the operating mode to high-safety mode.</span></span>  
  
-   <span data-ttu-id="ee507-114">데이터베이스 미러링에 관련된 각 서버 인스턴스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-114">Update each server instance that is involved in database mirroring.</span></span> <span data-ttu-id="ee507-115">롤링 업데이트는 현재 미러 서버인 서버 인스턴스를 업그레이드하고, 이 서버 인스턴스의 미러된 각 데이터베이스를 수동으로 장애 조치(failover)하고, 처음에 주 서버였으며 현재는 새 미러 서버인 서버 인스턴스를 업그레이드하는 과정으로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-115">A rolling update involves upgrading the server instance that is currently the mirror server, manually failing over each of its mirrored databases, and upgrading the server instance that was first the principal server (and is now the new mirror server).</span></span> <span data-ttu-id="ee507-116">이때 미러링을 재개해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-116">At this point, you will have to resume mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee507-117">롤링 업데이트를 시작하기 전에 미러링 세션 중 적어도 하나에 대해 수동 장애 조치(failover)를 수행하는 과정을 연습해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-117">Before starting a rolling update, we recommend that you perform a practice manual failover on at least one of your mirroring sessions.</span></span>  
  
-   <span data-ttu-id="ee507-118">필요할 경우 성능 우선 모드로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-118">Revert to high-performance mode, if it is required.</span></span>  
  
-   <span data-ttu-id="ee507-119">필요할 경우 미러링 모니터를 미러링 세션에 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-119">Return the witness to the mirroring session, if it is required.</span></span>  
  
 <span data-ttu-id="ee507-120">이러한 각 단계를 수행하는 절차는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-120">The procedures for these stages are described here.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ee507-121">동시 미러링 세션에서는 서버 인스턴스가 다른 역할(주 서버, 미러 서버 또는 미러링 모니터)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-121">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="ee507-122">이 경우 기본 롤링 업데이트 프로세스를 적절히 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-122">In this case, you will have to adapt the basic rolling update process accordingly.</span></span>  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a><span data-ttu-id="ee507-123">업데이트 전에 데이터를 보호하려면(최상의 방법)</span><span class="sxs-lookup"><span data-stu-id="ee507-123">To protect your data before an update (a best practice)</span></span>  
  
1.  <span data-ttu-id="ee507-124">모든 주 데이터베이스에 대해 전체 데이터베이스 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-124">Perform a full database backup on every principal database.</span></span>  
  
     <span data-ttu-id="ee507-125">**데이터베이스를 백업하려면**</span><span class="sxs-lookup"><span data-stu-id="ee507-125">**To back up a database**</span></span>  
  
    -   <span data-ttu-id="ee507-126">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="ee507-126">[Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="ee507-127">모든 주 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-127">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="ee507-128">세션에서 미러링 모니터를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="ee507-128">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="ee507-129">미러링 세션에 미러링 모니터 서버가 있을 경우 롤링 업데이트를 수행하기 전에 미러링 모니터 서버를 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-129">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling update.</span></span>  
  
     <span data-ttu-id="ee507-130">**미러링 모니터를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="ee507-130">**To remove the witness**</span></span>  
  
    -   [<span data-ttu-id="ee507-131">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ee507-131">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="ee507-132">세션을 성능 우선 모드에서 보호 우선 모드로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ee507-132">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="ee507-133">미러링 세션이 성능 우선 모드에서 실행되고 있을 경우 롤링 업데이트를 수행하기 전에 자동 장애 조치(Failover)가 없는 보호 우선 모드로 운영 모드를 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee507-133">If a mirroring session is running in high-performance mode, before you perform a rolling update, change the operating mode to high safety without automatic failover.</span></span> <span data-ttu-id="ee507-134">다음 방법 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-134">Use one of the following methods:</span></span>  
  
    -   <span data-ttu-id="ee507-135">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 경우: **데이터베이스 속성** 대화 상자의 [미러링 페이지](../relational-databases/databases/database-properties-mirroring-page.md)를 사용하여 **운영 모드** 옵션을 **자동 장애 조치(Failover) 없는 보호 우선(동기)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-135">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="ee507-136">이 페이지에 액세스하는 방법은 [데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee507-136">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="ee507-137">[!INCLUDE[tsql](../includes/tsql-md.md)]의 경우: 트랜잭션 보안을 FULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-137">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="ee507-138">자세한 내용은 [데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee507-138">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
### <a name="to-perform-the-rolling-update"></a><span data-ttu-id="ee507-139">롤링 업데이트를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="ee507-139">To perform the rolling update</span></span>  
  
1.  <span data-ttu-id="ee507-140">가동 중지 시간을 최소화 하려면 다음을 수행 하는 것이 좋습니다. 롤링 업데이트는 현재 미러 서버에 있는 모든 미러링 세션에서 미러링 파트너를 업데이트 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-140">To minimize downtime, we recommend the following: Start the rolling update by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="ee507-141">이때 여러 서버 인스턴스를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-141">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee507-142">미러링 모니터는 롤링 업데이트 프로세스 도중 언제라도 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-142">A witness can be updated at any point in the rolling update process.</span></span> <span data-ttu-id="ee507-143">예를 들어 서버 인스턴스가 Session 1의 미러 서버이고 미러링 모니터가 Session 2에 있을 경우 지금 서버 인스턴스를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-143">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can update the server instance now.</span></span>  
  
     <span data-ttu-id="ee507-144">처음 업데이트할 서버 인스턴스는 다음과 같이 미러링 세션의 현재 구성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-144">The server instance to update first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="ee507-145">서버 인스턴스가 자체 모든 미러링 세션의 미러 서버인 경우 서버 인스턴스에 서비스 팩이나 핫픽스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-145">If any server instance is already the mirror server in all of its mirroring sessions, install the service pack or the hotfix on that server instance.</span></span>  
  
    -   <span data-ttu-id="ee507-146">현재 모든 서버 인스턴스가 미러링 세션의 주 서버일 경우 처음 업데이트할 서버 인스턴스 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-146">If all of your server instances are currently the principal server in any mirroring sessions, select one server instance to update first.</span></span> <span data-ttu-id="ee507-147">그런 다음 서비스 팩이나 핫픽스를 설치하여 각각의 주 데이터베이스를 수동으로 장애 조치(failover)하고 서버 인스턴스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-147">Then, manually fail over each of its principal databases and update that server instance by installing the service pack or the hotfix.</span></span>  
  
     <span data-ttu-id="ee507-148">업데이트가 끝나면 서버 인스턴스는 자동으로 자체 미러링 세션에 다시 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-148">After being updated, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
     <span data-ttu-id="ee507-149">**수동 장애 조치 (failover)를 수행 하려면**</span><span class="sxs-lookup"><span data-stu-id="ee507-149">**To perform a manual failover**</span></span>  
  
    -   [<span data-ttu-id="ee507-150">데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ee507-150">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="ee507-151">[데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ee507-151">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
     <span data-ttu-id="ee507-152">수동 장애 조치(failover)의 작동 방식에 대한 자세한 내용은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee507-152">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="ee507-153">미러 서버 인스턴스가 업데이트된 각 미러링 세션이 동기화될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-153">For each mirroring session whose mirror server instance has just been updated, wait for the session to synchronize.</span></span> <span data-ttu-id="ee507-154">그런 다음 주 서버 인스턴스에 연결하여 세션을 수동으로 장애 조치(Failover)합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-154">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="ee507-155">장애 조치(Failover)를 수행하면 업데이트된 서버 인스턴스는 해당 세션의 주 서버가 되고 이전 주 서버는 미러 서버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-155">On failover, the updated server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="ee507-156">이 단계의 목적은 업그레이드된 서버 인스턴스가 파트너로 참여하는 모든 미러링 세션에서 다른 서버 인스턴스를 미러 서버로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-156">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
3.  <span data-ttu-id="ee507-157">장애 조치(failover)를 수행한 후에는 주 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 명령을 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-157">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on the principal database.</span></span>  
  
4.  <span data-ttu-id="ee507-158">파트너로 참여하는 모든 미러링 세션에서 이제 미러 서버가 된 각 서버 인스턴스에 서비스 팩이나 핫픽스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-158">Install the service pack or the hotfix on each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="ee507-159">이때 여러 서버를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-159">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ee507-160">미러링 구성이 복잡할 경우 일부 서버 인스턴스가 하나 이상의 미러링 세션에서 원래의 주 서버로 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-160">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="ee507-161">관련 된 모든 인스턴스를 업데이트할 때까지 해당 서버 인스턴스에 대해 2-4 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-161">Repeat steps 2-4 for those server instances until all instances involved are updated.</span></span>  
  
5.  <span data-ttu-id="ee507-162">미러링 세션을 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-162">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee507-163">미러링 모니터가 업데이트되기 전까지 자동 장애 조치(failover)는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-163">Automatic failover will not work until the witness has been updated.</span></span>  
  
6.  <span data-ttu-id="ee507-164">모든 미러링 세션에서 미러링 모니터가 된 나머지 서버 인스턴스에 서비스 팩이나 핫픽스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-164">Install the service packs or hotfixes on any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="ee507-165">업데이트된 미러링 모니터가 미러링 세션에 다시 참여한 후에는 자동 장애 조치(Failover)가 다시 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-165">After an updated witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="ee507-166">이때 여러 서버를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-166">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="ee507-167">세션을 성능 우선 모드로 되돌리려면</span><span class="sxs-lookup"><span data-stu-id="ee507-167">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="ee507-168">선택적으로, 다음 중 한 가지 방법을 사용하여 성능 우선 모드로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-168">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="ee507-169">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 경우: **데이터베이스 속성** 대화 상자의 **미러링 페이지**를 사용하여 [운영 모드](../relational-databases/databases/database-properties-mirroring-page.md) 옵션을 **성능 우선(동기)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-169">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="ee507-170">의 [!INCLUDE[tsql](../includes/tsql-md.md)] 경우: [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) 를 사용 하 여 트랜잭션 보안을 OFF로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-170">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) to set transaction safety to OFF.</span></span>  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a><span data-ttu-id="ee507-171">미러링 모니터를 미러링 세션에 다시 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ee507-171">To return a witness to a mirroring session</span></span>  
  
1.  <span data-ttu-id="ee507-172">보호 우선 모드의 경우 선택적으로 미러링 모니터를 각 미러링 세션에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ee507-172">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="ee507-173">**미러링 모니터 서버를 다시 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="ee507-173">**To reestablish the witness**</span></span>  
  
    -   [<span data-ttu-id="ee507-174">데이터베이스 미러링 모니터 서버 추가 또는 바꾸기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ee507-174">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="ee507-175">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ee507-175">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="ee507-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee507-176">See Also</span></span>  
 <span data-ttu-id="ee507-177">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="ee507-177">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="ee507-178">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ee507-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ee507-179">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee507-179">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="ee507-180">[데이터베이스 미러링 운영 모드](database-mirroring/database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="ee507-180">[Database Mirroring Operating Modes](database-mirroring/database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="ee507-181">[데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee507-181">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="ee507-182">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee507-182">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="ee507-183">미러된 데이터베이스의 상태 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ee507-183">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
