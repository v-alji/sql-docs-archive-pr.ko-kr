---
title: 서버 인스턴스 업그레이드 시 미러된 데이터베이스의 가동 중지 시간 최소화 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a343e6b9e93aa1910c82f436f3a50daf00d57bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649683"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a><span data-ttu-id="6b3ad-102">서버 인스턴스 업그레이드 시 미러된 데이터베이스의 작동 중단 최소화</span><span class="sxs-lookup"><span data-stu-id="6b3ad-102">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>
  <span data-ttu-id="6b3ad-103">서버 인스턴스를로 업그레이드할 때 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] *롤링 업그레이드*라고 하는 순차적 업그레이드를 수행 하 여 각 미러된 데이터베이스의 가동 중지 시간을 단일 수동 장애 조치 (failover)로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-103">When upgrading server instances to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can reduce downtime for each mirrored database to only a single manual failover by performing a sequential upgrade, known as a *rolling upgrade*.</span></span> <span data-ttu-id="6b3ad-104">롤링 업그레이드란 간단히 말해서 현재 미러링 세션에서 미러 서버 역할을 하고 있는 서버 인스턴스를 업그레이드한 다음 미러된 데이터베이스를 수동으로 장애 조치(Failover)하고, 이전 주 서버를 업그레이드하고, 미러링을 다시 시작하는 여러 단계로 이루어진 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-104">A rolling upgrade is a multi-stage process that in its simplest form involves upgrading the server instance that is currently acting as the mirror server in a mirroring session, then manually failing over the mirrored database, upgrading the former principal server, and resuming mirroring.</span></span> <span data-ttu-id="6b3ad-105">실제로 정확한 프로세스는 업그레이드 중인 서버 인스턴스에서 실행되는 미러링 세션의 개수 및 레이아웃과 운영 모드에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-105">In practice, the exact process will depend on the operating mode and the number and layout of mirroring session running on the server instances that you are upgrading.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b3ad-106">롤링 업그레이드를 수행 하 여 Service Pack 또는 핫픽스를 설치 하는 방법에 대 한 자세한 내용은 [미러된 데이터베이스의 가동 중지 시간을 최소화 하면서 시스템에 서비스 팩 설치](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-106">For information about performing a rolling upgrade to install a service pack or hotfix, see [Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md).</span></span>  
  
 <span data-ttu-id="6b3ad-107">**권장되는 준비 사항(최선의 구현 방법)**</span><span class="sxs-lookup"><span data-stu-id="6b3ad-107">**Recommended Preparation (Best Practices)**</span></span>  
  
 <span data-ttu-id="6b3ad-108">롤링 업그레이드를 시작하기 전에 다음과 같이 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-108">Before starting a rolling upgrade, we recommend that you:</span></span>  
  
1.  <span data-ttu-id="6b3ad-109">미러링 세션 중 하나 이상에서 수동 장애 조치(Failover)를 연습해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-109">Perform a practice manual failover on at least one of your mirroring sessions:</span></span>  
  
    -   [<span data-ttu-id="6b3ad-110">데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3ad-110">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="6b3ad-111">[데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6b3ad-111">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b3ad-112">수동 장애 조치(failover)의 작동 방식에 대한 자세한 내용은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-112">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="6b3ad-113">데이터를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-113">Protect your data:</span></span>  
  
    1.  <span data-ttu-id="6b3ad-114">모든 주 데이터베이스에 대해 전체 데이터베이스 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-114">Perform a full database backup on every principal database:</span></span>  
  
         <span data-ttu-id="6b3ad-115">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="6b3ad-115">[Create a Full Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="6b3ad-116">모든 주 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-116">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
 <span data-ttu-id="6b3ad-117">**롤링 업그레이드 단계**</span><span class="sxs-lookup"><span data-stu-id="6b3ad-117">**Stages of a Rolling Upgrade**</span></span>  
  
 <span data-ttu-id="6b3ad-118">세부적인 롤링 업그레이드 단계는 미러링 구성의 운영 모드에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-118">The specific steps of a rolling upgrade depend on the operating mode of the mirroring configuration.</span></span> <span data-ttu-id="6b3ad-119">그러나 기본 단계는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-119">However, the basic stages are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b3ad-120">운영 모드에 대한 자세한 내용은 [데이터베이스 미러링 운영 모드](database-mirroring-operating-modes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-120">For information about the operating modes, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="6b3ad-121">다음 그림은 각 운영 모드별로 롤링 업그레이드의 기본 단계를 보여 주는 순서도입니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-121">The following illustration is a flowchart that shows the basic stages of a rolling upgrade for each operating mode.</span></span> <span data-ttu-id="6b3ad-122">단계별 절차는 이 그림 다음에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-122">The corresponding procedures are described after the illustration.</span></span>  
  
 <span data-ttu-id="6b3ad-123">![롤링 업그레이드 단계를 보여 주는 순서도](../media/dbm-rolling-upgrade.gif "롤링 업그레이드 단계를 보여 주는 순서도")</span><span class="sxs-lookup"><span data-stu-id="6b3ad-123">![Flowchart showing steps of a rolling upgrade](../media/dbm-rolling-upgrade.gif "Flowchart showing steps of a rolling upgrade")</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6b3ad-124">동시 미러링 세션에서는 서버 인스턴스가 다른 역할(주 서버, 미러 서버 또는 미러링 모니터)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-124">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="6b3ad-125">이 경우 기본 롤링 업그레이드 프로세스를 적절히 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-125">In this case, you will have to adapt the basic rolling upgrade process accordingly.</span></span> <span data-ttu-id="6b3ad-126">자세한 내용은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-126">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="6b3ad-127">세션을 성능 우선 모드에서 보호 우선 모드로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6b3ad-127">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="6b3ad-128">미러링 세션이 보호 우선 모드에서 실행되고 있을 경우 롤링 업그레이드를 수행하기 전에 자동 장애 조치가 없는 보호 우선 모드로 운영 모드를 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-128">If a mirroring session is running in high-performance mode, before you perform a rolling upgrade, change the operating mode to high safety without automatic failover.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6b3ad-129">미러 서버가 주 서버와 지리적으로 먼 거리에 있는 경우에는 롤링 업그레이드가 적합하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-129">If the mirror server is geographically distant from the principal server, a rolling upgrade might be inappropriate.</span></span>  
  
    -   <span data-ttu-id="6b3ad-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 경우: **데이터베이스 속성** 대화 상자의 [미러링 페이지](../../relational-databases/databases/database-properties-mirroring-page.md)를 사용하여 **운영 모드** 옵션을 **자동 장애 조치(Failover) 없는 보호 우선(동기)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="6b3ad-131">이 페이지에 액세스하는 방법은 [데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-131">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="6b3ad-132">[!INCLUDE[tsql](../../includes/tsql-md.md)]의 경우: 트랜잭션 보안을 FULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-132">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="6b3ad-133">자세한 내용은 [데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-133">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="6b3ad-134">세션에서 미러링 모니터를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="6b3ad-134">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="6b3ad-135">미러링 세션에 미러링 모니터가 있을 경우 롤링 업그레이드를 수행하기 전에 미러링 모니터를 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-135">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling upgrade.</span></span> <span data-ttu-id="6b3ad-136">미러링 모니터를 제거하지 않으면 미러 서버 인스턴스를 업그레이드할 때 주 서버 인스턴스에 연결된 채로 남아있는 미러링 모니터에 의해 데이터베이스의 가용성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-136">Otherwise, when the mirror server instance is being upgraded, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="6b3ad-137">미러링 모니터를 제거하고 나면 데이터베이스 가동 중단의 위험 없이 롤링 업그레이드 프로세스 도중 언제라도 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-137">After you remove a witness, you can upgrade it at any time during the rolling upgrade process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b3ad-138">자세한 내용은 [쿼럼: 미러링 모니터 서버가 데이터베이스 가용성에 미치는 영향&#40;데이터베이스 미러링&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-138">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
    -   [<span data-ttu-id="6b3ad-139">데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3ad-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a><span data-ttu-id="6b3ad-140">롤링 업그레이드를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="6b3ad-140">To perform the rolling upgrade</span></span>  
  
1.  <span data-ttu-id="6b3ad-141">가동 중단을 최소화하려면 다음 방법을 사용하는 것이 좋습니다. 롤링 업그레이드를 시작할 때 자체 미러링 세션 내의 미러 서버인 모든 미러링 파트너를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-141">To minimize downtime, we recommend the following: Start the rolling upgrade by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="6b3ad-142">이때 여러 서버 인스턴스를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-142">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b3ad-143">미러링 모니터는 롤링 업그레이드 프로세스 도중 언제라도 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-143">A witness can be upgraded at any point in the rolling upgrade process.</span></span> <span data-ttu-id="6b3ad-144">예를 들어 서버 인스턴스가 Session 1의 미러 서버이고 미러링 모니터가 Session 2에 있을 경우 지금 서버 인스턴스를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-144">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can upgrade the server instance now.</span></span>  
  
     <span data-ttu-id="6b3ad-145">처음 업그레이드할 서버 인스턴스는 다음과 같이 미러링 세션의 현재 구성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-145">The server instance to upgrade first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="6b3ad-146">서버 인스턴스가 자체 미러링 세션의 미러 서버인 경우 서버 인스턴스를 새 버전으로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-146">If any server instance is already the mirror server in all its mirroring sessions, upgrade the server instance to the new version.</span></span>  
  
    -   <span data-ttu-id="6b3ad-147">현재 모든 서버 인스턴스가 미러링 세션의 주 서버일 경우 처음 업그레이드할 서버 인스턴스 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-147">If all your server instances are currently the principal server in any mirroring sessions, select one server instance to upgrade first.</span></span> <span data-ttu-id="6b3ad-148">그런 다음 각각의 주 데이터베이스를 수동으로 장애 조치(Failover)하고 서버 인스턴스를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-148">Then, manually fail over each of its principal databases and upgrade that server instance.</span></span>  
  
     <span data-ttu-id="6b3ad-149">업그레이드가 끝나면 서버 인스턴스는 자동으로 자체 미러링 세션에 다시 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-149">After being upgraded, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
2.  <span data-ttu-id="6b3ad-150">미러 서버 인스턴스가 업그레이드된 각 미러링 세션이 동기화될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-150">For each mirroring session whose mirror server instance has just been upgraded, wait for the session to synchronize.</span></span> <span data-ttu-id="6b3ad-151">그런 다음 주 서버 인스턴스에 연결하여 세션을 수동으로 장애 조치(Failover)합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-151">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="6b3ad-152">장애 조치(Failover)를 수행하면 업그레이드된 서버 인스턴스는 해당 세션의 주 서버가 되고 이전 주 서버는 미러 서버가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-152">On failover, the upgraded server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="6b3ad-153">이 단계의 목적은 업그레이드된 서버 인스턴스가 파트너로 참여하는 모든 미러링 세션에서 다른 서버 인스턴스를 미러 서버로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-153">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
     <span data-ttu-id="6b3ad-154">**업그레이드된 서버 인스턴스를 장애 조치(Failover)한 후의 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="6b3ad-154">**Restrictions after you failover to an upgraded server instance.**</span></span>  
  
     <span data-ttu-id="6b3ad-155">이전 서버 인스턴스에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 서버 인스턴스로 장애 조치(Failover)한 후에는 데이터베이스 세션이 일시 중지되며</span><span class="sxs-lookup"><span data-stu-id="6b3ad-155">After failing over from an earlier server instance to a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] server instance, the database session is suspended.</span></span> <span data-ttu-id="6b3ad-156">다른 파트너가 업그레이드되기 전에는 재개할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-156">It cannot be resumed until the other partner has been upgraded.</span></span> <span data-ttu-id="6b3ad-157">그러나 주 서버에는 계속 연결할 수 있으며 주 서버에 있는 데이터에 액세스하고 수정하는 것도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-157">However, the principal server is still accepting connections and allowing data access and modifications on the principal database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b3ad-158">새 미러링 세션을 시작하려면 모든 서버 인스턴스가 같은 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-158">Establishing a new mirroring session requires that the server instances all be running the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="6b3ad-159">장애 조치 (failover)를 수행한 후에는 주 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 명령을 실행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-159">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on theprincipal database.</span></span>  
  
4.  <span data-ttu-id="6b3ad-160">파트너로 참여하는 모든 미러링 세션에서 이제 미러 서버가 된 각 서버 인스턴스를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-160">Upgrade each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="6b3ad-161">이때 여러 서버를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-161">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6b3ad-162">미러링 구성이 복잡할 경우 일부 서버 인스턴스가 하나 이상의 미러링 세션에서 원래의 주 서버로 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-162">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="6b3ad-163">이러한 서버 인스턴스에 대해 2-4단계를 반복하여 관련된 모든 인스턴스를 업그레이드하십시오.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-163">Repeat steps 2-4 for those server instances until all instances involved are upgraded.</span></span>  
  
5.  <span data-ttu-id="6b3ad-164">미러링 세션을 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-164">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b3ad-165">자동 장애 조치(Failover)는 미러링 모니터가 업그레이드되고 미러링 세션에 다시 추가되기 전까지 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-165">Automatic failover will not work until the witness has been upgraded and added back into the mirroring session.</span></span>  
  
6.  <span data-ttu-id="6b3ad-166">모든 미러링 세션에서 미러링 모니터로 남아 있는 나머지 서버 인스턴스를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-166">Upgrade any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="6b3ad-167">업그레이드된 미러링 모니터가 미러링 세션에 다시 참여한 후에는 자동 장애 조치(Failover)가 다시 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-167">After an upgraded witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="6b3ad-168">이때 여러 서버를 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-168">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="6b3ad-169">세션을 성능 우선 모드로 되돌리려면</span><span class="sxs-lookup"><span data-stu-id="6b3ad-169">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="6b3ad-170">선택적으로, 다음 중 한 가지 방법을 사용하여 성능 우선 모드로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-170">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6b3ad-171">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 경우: **데이터베이스 속성** 대화 상자의 **미러링 페이지**를 사용하여 [운영 모드](../../relational-databases/databases/database-properties-mirroring-page.md) 옵션을 **성능 우선(동기)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-171">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="6b3ad-172">[!INCLUDE[tsql](../../includes/tsql-md.md)]의 경우: [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)를 사용하여 트랜잭션 보안을 OFF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-172">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)to set transaction safety to OFF.</span></span>  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a><span data-ttu-id="6b3ad-173">미러링 모니터를 미러링 세션에 다시 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6b3ad-173">To add a witness back into a mirroring session</span></span>  
  
1.  <span data-ttu-id="6b3ad-174">보호 우선 모드의 경우 선택적으로 미러링 모니터를 각 미러링 세션에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b3ad-174">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="6b3ad-175">**미러링 모니터를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="6b3ad-175">**To return a witness**</span></span>  
  
    -   [<span data-ttu-id="6b3ad-176">데이터베이스 미러링 모니터 서버 추가 또는 바꾸기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3ad-176">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="6b3ad-177">Windows 인증을 사용하여 데이터베이스 미러링 모니터 추가&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b3ad-177">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b3ad-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b3ad-178">See Also</span></span>  
 <span data-ttu-id="6b3ad-179">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-179">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="6b3ad-180">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-180">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6b3ad-181">[미러된 데이터베이스 상태 보기&#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-181">[View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="6b3ad-182">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-182">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="6b3ad-183">[미러된 데이터베이스의 가동 중지 시간을 최소화 하면서 시스템에 서비스 팩 설치](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-183">[Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span></span>  
 <span data-ttu-id="6b3ad-184">[데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-184">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="6b3ad-185">[데이터베이스 미러링 세션에 서비스 강제 수행&#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-185">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="6b3ad-186">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6b3ad-186">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="6b3ad-187">데이터베이스 미러링 운영 모드</span><span class="sxs-lookup"><span data-stu-id="6b3ad-187">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
