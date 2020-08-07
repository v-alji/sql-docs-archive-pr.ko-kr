---
title: 데이터베이스 미러링을 위한 필수 조건, 제한 사항 및 권장 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dc29dbdc8432a4abd197a2a1a3f15b6ff5f6d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733099"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a><span data-ttu-id="89fe1-102">데이터베이스 미러링을 위한 필수 구성 요소, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="89fe1-102">Prerequisites, Restrictions, and Recommendations for Database Mirroring</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="89fe1-103">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="89fe1-104">이 항목에서는 데이터베이스 미러링을 설정하기 위한 사전 요구 사항 및 권장 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-104">This topic describes the prerequisites and recommendations for setting up database mirroring.</span></span> <span data-ttu-id="89fe1-105">데이터베이스 미러링에 대한 소개는 [데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-105">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89fe1-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 디스크상 스토리지 형식은 64비트 및 32비트 환경에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="89fe1-107">따라서 데이터베이스 미러링 세션은 32비트 환경에서 실행하는 서버 인스턴스와 64비트 환경에서 실행하는 서버 인스턴스를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-107">Therefore, a database mirroring session can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  

  
##  <a name="support-for-database-mirroring"></a><a name="DbmSupport"></a><span data-ttu-id="89fe1-108">데이터베이스 미러링 지원</span><span class="sxs-lookup"><span data-stu-id="89fe1-108">Support For Database Mirroring</span></span>  
 <span data-ttu-id="89fe1-109">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 데이터베이스 미러링 지원에 대한 자세한 내용은 [SQL Server 2014 버전에서 지원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-109">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="89fe1-110">데이터베이스 미러링은 지원되는 모든 데이터베이스 호환성 수준에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-110">Note that database mirroring works with any supported database compatibility level.</span></span> <span data-ttu-id="89fe1-111">지원되는 호환성 수준에 대한 자세한 내용은 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-111">For information about the supported compatibility levels, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="89fe1-112">필수 조건</span><span class="sxs-lookup"><span data-stu-id="89fe1-112">Prerequisites</span></span>  
  
-   <span data-ttu-id="89fe1-113">미러링 세션을 설정하려면 파트너 및 미러링 모니터 서버(있는 경우)가 같은 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-113">For a mirroring session to be established, the partners and the witness, if any, must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="89fe1-114">각각 주 서버와 미러 서버인 두 파트너가 같은 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-114">The two partners, that is the principal server and mirror server, must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89fe1-115">미러링 모니터 서버(있는 경우)는 데이터베이스 미러링을 지원하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 모든 버전에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-115">The witness, if any, can run on any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89fe1-116">미러링 세션의 파트너인 서버 인스턴스를 최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-116">You can upgrade server instances that are partners in a mirroring session to a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89fe1-117">자세한 내용은 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-117">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="89fe1-118">이 데이터베이스는 전체 복구 모델을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-118">The database must use the full recovery model.</span></span> <span data-ttu-id="89fe1-119">단순 복구 모델 및 대량 로그 복구 모델에서는 데이터베이스 미러링이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-119">The simple and bulk-logged recovery models do not support database mirroring.</span></span> <span data-ttu-id="89fe1-120">따라서 대량 작업이 미러링된 데이터베이스에 대해 항상 전체 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-120">Therefore, bulk operations are always fully logged for a mirrored database.</span></span> <span data-ttu-id="89fe1-121">복구 모델에 대한 자세한 내용은 [복구 모델&#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-121">For information about recovery models, see [Recovery Models &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).</span></span>  
  
-   <span data-ttu-id="89fe1-122">미러 서버에 미러 데이터베이스를 위한 디스크 공간이 충분히 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-122">Verify that the mirror server has sufficient disk space for the mirror database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89fe1-123">복제된 데이터베이스에서 데이터베이스 미러링을 사용하는 방법은 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-123">For information about how to use database mirroring on a replicated database, see [Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="89fe1-124">미러 서버에 미러 데이터베이스를 만들 때는 WITH NORECOVERY로 동일한 데이터베이스 이름을 지정하여 주 데이터베이스의 백업을 복원하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-124">When you are creating the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="89fe1-125">백업 후에 생성된 모든 로그 백업 또한 WITH NORECOVERY를 사용하여 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-125">Also, all log backups that were created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="89fe1-126">데이터베이스 미러링이 중지된 경우 주 데이터베이스에서 수행된 모든 후속 로그 백업을 미러 데이터베이스에 적용해야만 미러링을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-126">If database mirroring has been stopped, before you can restart it, any subsequent log backups taken on the principal database must be applied to the mirror database.</span></span>  
  

  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="89fe1-127">제한 사항</span><span class="sxs-lookup"><span data-stu-id="89fe1-127">Restrictions</span></span>  
  
-   <span data-ttu-id="89fe1-128">사용자 데이터베이스만 미러링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-128">Only user databases can be mirrored.</span></span> <span data-ttu-id="89fe1-129">**master**, **msdb**, **tempdb**또는 **model** 데이터베이스는 미러링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-129">You cannot mirror the **master**, **msdb**, **tempdb**, or **model** databases.</span></span>  
  
-   <span data-ttu-id="89fe1-130">데이터베이스 미러링 세션 동안에는 미러된 데이터베이스의 이름을 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-130">A mirrored database cannot be renamed during a database mirroring session.</span></span>  
  
-   <span data-ttu-id="89fe1-131">데이터베이스 미러링은 FILESTREAM을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-131">Database mirroring does not support FILESTREAM.</span></span> <span data-ttu-id="89fe1-132">주 서버에서 FILESTREAM 파일 그룹을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-132">A FILESTREAM filegroup cannot be created on the principal server.</span></span> <span data-ttu-id="89fe1-133">FILESTREAM 파일 그룹이 포함된 데이터베이스에 대해 데이터베이스 미러링을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-133">Database mirroring cannot be configured for a database that contains FILESTREAM filegroups.</span></span>  
  
-   <span data-ttu-id="89fe1-134">32비트 시스템에서 데이터베이스 미러링은 각 데이터베이스 미러링 세션에서 사용하는 작업자 스레드의 수로 인해 서버 인스턴스당 최대 약 10개의 데이터베이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-134">On a 32-bit system, database mirroring can support a maximum of about 10 databases per server instance because of the numbers of worker threads that are consumed by each database mirroring session.</span></span>  
  
-   <span data-ttu-id="89fe1-135">데이터베이스 미러링은 데이터베이스 간 트랜잭션 또는 분산 트랜잭션에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-135">Database mirroring is not supported with either cross-database transactions or distributed transactions.</span></span> <span data-ttu-id="89fe1-136">자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-136">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  

  
##  <a name="recommendations-for-configuring-partner-servers"></a><a name="RecommendationsForPartners"></a><span data-ttu-id="89fe1-137">파트너 서버 구성에 대 한 권장 사항</span><span class="sxs-lookup"><span data-stu-id="89fe1-137">Recommendations for Configuring Partner Servers</span></span>  
  
-   <span data-ttu-id="89fe1-138">동일한 작업을 처리할 수 있는 동등한 시스템에서 파트너를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-138">The partners should run on comparable systems that can handle identical workloads.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89fe1-139">자동 장애 조치(Failover)가 있는 보호 우선 모드를 사용하려면 각 장애 조치(Failover) 파트너의 일반적인 로드에서 사용하는 CPU 양이 50% 미만이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-139">If you plan to use high-safety mode with automatic failover, the normal load on each failover partner should be less than 50 percent of the CPU.</span></span> <span data-ttu-id="89fe1-140">작업이 CPU를 오버로드하면 장애 조치(Failover) 파트너에서 미러링 세션의 다른 서버 인스턴스에 ping을 실행할 수 없어</span><span class="sxs-lookup"><span data-stu-id="89fe1-140">If your work load overloads the CPU, a failover partner might be unable to ping the other server instances in the mirroring session.</span></span> <span data-ttu-id="89fe1-141">불필요한 장애 조치가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-141">This causes a unnecessary failover.</span></span> <span data-ttu-id="89fe1-142">CPU 사용을 50% 미만으로 유지할 수 없는 경우 자동 장애 조치 없는 보호 우선 모드나 성능 우선 모드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-142">If you cannot keep the CPU usage under 50 percent, we recommend that you use either high-safety mode without automatic failover or high-performance mode.</span></span>  
  
-   <span data-ttu-id="89fe1-143">가능한 경우 드라이브 문자를 포함한 미러 데이터베이스의 경로가 주 데이터베이스의 경로와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-143">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span> <span data-ttu-id="89fe1-144">파일 레이아웃이 다른 경우 RESTORE 문에 MOVE 옵션을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-144">You must include the MOVE option in the RESTORE statement if the file layouts must differ.</span></span> <span data-ttu-id="89fe1-145">예를 들어 주 데이터베이스가 'F:' 드라이브에 있는데 미러링 시스템에는 F: 드라이브가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-145">For example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="89fe1-146">미러 데이터베이스를 만들 때 데이터베이스 파일을 이동한 경우 나중에 데이터베이스에 파일을 추가하려면 미러링을 일시 중지해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-146">If you move the database files when you create the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
-   <span data-ttu-id="89fe1-147">미러링 세션의 모든 서버 인스턴스에서 같은 마스터 코드 페이지와 데이터 정렬을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-147">All of the server instances in a mirroring session should use the same master code page and collation.</span></span> <span data-ttu-id="89fe1-148">차이가 있으면 미러링 설정 중에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-148">Differences can cause a problem during mirroring setup.</span></span>  
  
-   <span data-ttu-id="89fe1-149">필요에 따라 데이터베이스 장애 조치에 걸리는 시간을 예상하여 현재 시스템 구성이 필요한 성능을 제공하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-149">Optionally, estimate the time to fail over a database, to make sure that the system configuration will provide the performance you require.</span></span> <span data-ttu-id="89fe1-150">자세한 내용은 [역할 전환 중 서비스 중단 예측&#40;데이터베이스 미러링&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)프로세스를 통해 주 역할과 미러 역할을 서로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-150">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="89fe1-151">최상의 성능을 위해 미러링 전용 네트워크 어댑터(네트워크 인터페이스 카드)를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="89fe1-151">For best performance, use a dedicated network adapter (network interface card) for mirroring.</span></span>  
  
-   <span data-ttu-id="89fe1-152">보호 우선 모드 사용 시 WAN(광역 통신망)은 데이터베이스 미러링에 대해 안정적이지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-152">We make no recommendations about whether a wide-area network (WAN) is reliable enough for database mirroring in high-safety mode.</span></span> <span data-ttu-id="89fe1-153">WAN에서 보호 우선 모드를 사용할 경우 필요 없는 자동 장애 조치가 발생할 수 있으므로 세션에 미러링 모니터 서버를 추가하는 방식에 대해 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-153">If you decide to use high-safety mode over a WAN, be cautious about how you add a witness to the session, because unwanted automatic failovers can occur.</span></span> <span data-ttu-id="89fe1-154">자세한 내용은 이 항목의 뒷부분에 나오는 [데이터베이스 미러링 배포 시의 권장 구성](#RecommendationsForDeploying)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="89fe1-154">For more information, see [Recommendations for Deploying Database Mirroring](#RecommendationsForDeploying), later in this topic.</span></span>  
  

  
##  <a name="recommendations-for-deploying-database-mirroring"></a><a name="RecommendationsForDeploying"></a><span data-ttu-id="89fe1-155">데이터베이스 미러링 배포에 대 한 권장 사항</span><span class="sxs-lookup"><span data-stu-id="89fe1-155">Recommendations for Deploying Database Mirroring</span></span>  
 <span data-ttu-id="89fe1-156">비동기 작업을 사용하면 데이터베이스 미러링 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-156">Optimal database mirroring performance is obtained by using asynchronous operation.</span></span> <span data-ttu-id="89fe1-157">동기 작업을 사용하는 미러링 세션의 경우 작업에서 대량의 트랜잭션 로그 데이터가 생성될 때 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-157">A mirroring session that uses synchronous operation might experience slowed performance when its workload generates large amounts of transaction log data.</span></span>  
  
 <span data-ttu-id="89fe1-158">테스트 환경에서 모든 운영 모드를 시험하여 데이터베이스 미러링 성능을 평가하는 것도 좋지만</span><span class="sxs-lookup"><span data-stu-id="89fe1-158">In test environments, it is appropriate to explore all the operating modes to evaluate how database mirroring performs.</span></span> <span data-ttu-id="89fe1-159">프로덕션 환경에 미러링을 배포하기 전에 실제 네트워크 작동 방식을 이해하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-159">However, before you deploy mirroring into a production environment, make sure that you understand how the network functions in the real world.</span></span>  
  
 <span data-ttu-id="89fe1-160">자동 장애 조치 있는 보호 우선 모드는 가능한 네트워크 오류 출처를 최소화하는 비교적 단순한 네트워크 구성이나 전용 연결이 있는 고품질 서비스 네트워크를 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-160">High-safety mode with automatic failover is designed for a high-service network that has either a dedicated connection or a fairly simple network configuration that minimizes the sources of possible network failures.</span></span> <span data-ttu-id="89fe1-161">이러한 고품질 네트워크 환경은 자동 장애 조치 있는 보호 우선 모드에 반드시 필요하며 모든 데이터베이스 미러링 세션에 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-161">Such a high-quality network environment is necessary for high-safety mode with automatic failover and is recommended for all database mirroring sessions.</span></span> <span data-ttu-id="89fe1-162">그러나 성능 우선 모드와 자동 장애 조치 없는 보호 우선 모드는 네트워크 안정성의 영향을 훨씬 적게 받습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-162">However, high-performance mode and high-safety mode without automatic failover are much less affected by network reliability.</span></span>  
  
 <span data-ttu-id="89fe1-163">따라서 프로덕션 환경에 대해 다음 배포 지침을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-163">Therefore, for production environments we recommend that you adhere to the following deployment guidelines:</span></span>  
  
1.  <span data-ttu-id="89fe1-164">비동기 성능 우선 모드로 실행하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-164">Start running in asynchronous, high-performance mode.</span></span> <span data-ttu-id="89fe1-165">이 모드는 네트워크 환경의 영향을 가장 적게 받으며 미러링 작동 방식을 살펴 보기에 가장 좋은 구성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-165">This mode is the least sensitive to the network environment and provides the best configuration for exploring how mirroring works.</span></span> <span data-ttu-id="89fe1-166">대역폭이 미러링을 지원한다는 것이 확인되고 환경에서의 비동기 모드 성능과 미러링 설정을 충분히 이해할 때까지 시스템을 비동기적으로 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-166">We recommend that you run your system asynchronously until you are confident that your bandwidth supports mirroring and you have developed an understanding of mirroring setup and of the performance of asynchronous mode in your environment.</span></span> <span data-ttu-id="89fe1-167">자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-167">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="89fe1-168">테스트 작업 중 세션에서 데이터베이스 미러링 실패를 발생시키는 네트워크 오류를 모니터링하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-168">Throughout testing, we recommend that you monitor your sessions for network errors that cause database mirroring to fail.</span></span> <span data-ttu-id="89fe1-169">잠재적 오류 출처에 대한 자세한 내용은 [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="89fe1-169">For more information about potential sources of failure, see [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md).</span></span> <span data-ttu-id="89fe1-170">데이터베이스 미러링을 모니터링하는 방법은 [데이터베이스 미러링 모니터링&#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-170">For information about how to monitor database mirroring, see [Monitoring Database Mirroring &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="89fe1-171">비동기 작업이 비즈니스 요구를 만족시킨다고 확신하는 경우 데이터 보호를 향상시키기 위해 동기 작업을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-171">When you are confident that asynchronous operation is meeting the business needs, you might want to try synchronous operation to improve your data protection.</span></span> <span data-ttu-id="89fe1-172">환경에서 동기 미러링이 어떻게 작동하는지 테스트할 때는 먼저 자동 장애 조치 없는 보호 우선 모드를 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-172">When you test how synchronous mirroring works in your environment, we recommend that first you test high-safety mode without automatic failover.</span></span> <span data-ttu-id="89fe1-173">이 테스트의 주요 목적은 동기 작업이 데이터베이스 성능에 미치는 영향을 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-173">The primary purpose of this testing is to see how synchronous operation affects the database performance.</span></span> <span data-ttu-id="89fe1-174">자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89fe1-174">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
3.  <span data-ttu-id="89fe1-175">자동 장애 조치 없는 보호 우선 모드에서 비즈니스 요구를 만족시키며 네트워크 오류로 인해 실패하지 않는다고 확신하기 전에는 자동 장애 조치를 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="89fe1-175">Wait to enable automatic failover until you are confident that high-safety mode without automatic failover is meeting the business needs and that network errors are not causing failures.</span></span> <span data-ttu-id="89fe1-176">자세한 내용은 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89fe1-176">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="89fe1-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89fe1-177">See Also</span></span>  
 <span data-ttu-id="89fe1-178">[데이터베이스 미러링 설정&#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="89fe1-178">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="89fe1-179">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="89fe1-179">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="89fe1-180">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="89fe1-180">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="89fe1-181">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89fe1-181">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
