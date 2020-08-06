---
title: 미러 데이터베이스의 미러링 준비(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf46b4f6fd8e7af55e1930ef6063c4754673fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733104"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a><span data-ttu-id="e968d-102">미러 데이터베이스의 미러링 준비(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e968d-102">Prepare a Mirror Database for Mirroring (SQL Server)</span></span>
  <span data-ttu-id="e968d-103">데이터베이스 미러링 세션을 시작하기 전에 데이터베이스 소유자나 시스템 관리자는 미러 데이터베이스가 생성되었으며 미러링 준비가 완료되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-103">Before a database mirroring session can start, the database owner or system administrator must make sure that the mirror database has been created and is ready for mirroring.</span></span> <span data-ttu-id="e968d-104">새 미러 데이터베이스를 만들려면 최소한 주 데이터베이스의 전체 백업과 후속 로그 백업이 필요하며 WITH NORECOVERY를 사용하여 두 백업을 모두 미러 서버 인스턴스로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-104">Creating a new mirror database minimally requires taking a full backup of the principal database and a subsequent log backup and restoring them both onto the mirror server instance, using WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="e968d-105">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-105">This topic describes how to prepare a mirror database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e968d-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e968d-106">Before You Begin</span></span>  
  
###  <a name="requirements"></a><a name="Requirements"></a> <span data-ttu-id="e968d-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e968d-107">Requirements</span></span>  
  
-   <span data-ttu-id="e968d-108">주 서버와 미러 서버 인스턴스가 같은 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-108">The principal and mirror server instances must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e968d-109">미러 서버에 상위 버전의 SQL Server가 있을 수 있지만 이 구성은 세심하게 계획된 업그레이드 프로세스 중에만 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-109">While it is possible for the mirror server to have a higher version of SQL Server, this configuration is only recommended during a carefully planned upgrade process.</span></span> <span data-ttu-id="e968d-110">이 구성에서 자동 장애 조치(failover)가 발생할 수 있습니다. 이 경우 데이터를 하위 버전의 SQL Server로 옮길 수 없으므로 데이터 이동이 자동으로 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-110">In such a configuration, you run the risk of an automatic failover, in which data movement is automatically suspended because data cannot move to a lower version of SQL Server.</span></span> <span data-ttu-id="e968d-111">자세한 내용은 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-111">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="e968d-112">주 서버와 미러 서버 인스턴스가 같은 에디션의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-112">The principal and mirror server instances must be running on the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e968d-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 데이터베이스 미러링 지원에 대한 자세한 내용은 [SQL Server 2014 버전에서 지원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-113">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="e968d-114">이 데이터베이스는 전체 복구 모델을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-114">The database must use the full recovery model.</span></span>  
  
     <span data-ttu-id="e968d-115">자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) 또는 [sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 및 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-115">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) or [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) and [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="e968d-116">미러 데이터베이스의 이름은 주 데이터베이스의 이름과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-116">The name of the mirror database must be the same as the name of the principal database.</span></span>  
  
-   <span data-ttu-id="e968d-117">미러링이 작동하려면 미러 데이터베이스가 RESTORING 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-117">The mirror database must be in the RESTORING state for mirroring to work.</span></span> <span data-ttu-id="e968d-118">미러 데이터베이스를 준비할 때는 모든 복원 작업에 대해 RESTORE WITH NORECOVERY를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-118">When preparing a mirror database, you must use RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="e968d-119">최소한 NORECOVERY를 사용하여 주 데이터베이스의 전체 백업을 복원하고 이후의 모든 로그 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-119">Minimally, you will need to restore WITH NORECOVERY a full backup of the principal database, followed by all subsequent log backups.</span></span>  
  
-   <span data-ttu-id="e968d-120">미러 데이터베이스를 만들려는 시스템에 미러 데이터베이스를 저장할 공간이 충분한 디스크 드라이브가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-120">The system where you plan to create the mirror database must possesses a disk drive with sufficient space to hold the mirror database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e968d-121">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e968d-121">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e968d-122">**master**, **msdb**, **temp**또는 **model** 시스템 데이터베이스는 미러링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-122">You cannot mirror the **master**, **msdb**, **temp**, or **model** system databases.</span></span>  
  
-   <span data-ttu-id="e968d-123">[AlwaysOn 가용성 그룹 (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md)에 속한 데이터베이스는 미러링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-123">You cannot mirror a database that belongs to an [AlwaysOn Availability Groups (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e968d-124">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e968d-124">Recommendations</span></span>  
  
-   <span data-ttu-id="e968d-125">주 데이터베이스의 아주 최근 전체 데이터베이스 백업 또는 최근 차등 데이터베이스 백업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-125">Use a very recent full database backup or a recent differential database backup of the principal database.</span></span>  
  
-   <span data-ttu-id="e968d-126">로그 백업 작업이 주 데이터베이스에서 자주 실행되도록 예약한 경우 미러링이 시작할 때까지 백업 작업을 사용하지 않도록 설정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-126">If a log backup job is scheduled to run very frequently on the principal database, you might have to disable the backup job until mirroring has started.</span></span>  
  
-   <span data-ttu-id="e968d-127">가능한 경우 드라이브 문자를 포함한 미러 데이터베이스의 경로가 주 데이터베이스의 경로와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-127">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span>  
  
     <span data-ttu-id="e968d-128">주 데이터베이스는 'F:' 드라이브에 있는데 미러 시스템에는 F: 드라이브가 없는 경우 등 파일 경로가 달라야 하는 경우에는 RESTORE STATEMENT에 MOVE 옵션을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-128">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE STATEMENT.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e968d-129">미러링 세션에 영향을 주지 않고 해당 세션 중 파일을 추가하려면 파일의 경로가 두 서버 모두에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-129">Adding a file during a mirroring session without impacting the session requires that the path of the file exists on both servers.</span></span> <span data-ttu-id="e968d-130">따라서 미러 데이터베이스를 만들 때 데이터베이스 파일을 이동하면 나중에 미러 데이터베이스에 파일을 추가할 수 없고 미러링이 일시 중지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-130">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span> <span data-ttu-id="e968d-131">실패한 파일 생성 작업을 처리하는 방법은 [데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-131">For information about dealing with a failed create-file operation, see [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e968d-132">주 데이터베이스에 전체 텍스트 카탈로그가 있는 경우 [데이터베이스 미러링 및 전체 텍스트 카탈로그&#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md)를 참조하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-132">If the principal database has any full-text catalogs, we recommend that you see [Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e968d-133">프로덕션 데이터베이스의 경우에는 항상 별도의 디바이스에 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-133">For a production database, always back up to a separate device.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e968d-134">보안</span><span class="sxs-lookup"><span data-stu-id="e968d-134">Security</span></span>  
 <span data-ttu-id="e968d-135">데이터베이스를 백업하면 TRUSTWORTHY가 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-135">TRUSTWORTHY is set to OFF when a database is backed up.</span></span> <span data-ttu-id="e968d-136">따라서 새 미러 데이터베이스의 TRUSTWORTHY는 항상 OFF입니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-136">Therefore, TRUSTWORTHY is always OFF on a new mirror database.</span></span> <span data-ttu-id="e968d-137">장애 조치(Failover) 후 데이터베이스를 신뢰할 수 있어야 하는 경우에는 추가 설정 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-137">If the database needs to be trustworthy after a failover, additional setup steps are necessary.</span></span> <span data-ttu-id="e968d-138">자세한 내용은 [Trustworthy 속성을 사용하도록 미러 데이터베이스 설정&#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-138">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
 <span data-ttu-id="e968d-139">미러 데이터베이스의 데이터베이스 마스터 키 자동 암호 해독을 설정하는 방법은 [암호화된 미러 데이터베이스 설정](set-up-an-encrypted-mirror-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-139">For information about enabling automatic decryption of the database master key of a mirror database, see [Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e968d-140">권한</span><span class="sxs-lookup"><span data-stu-id="e968d-140">Permissions</span></span>  
 <span data-ttu-id="e968d-141">데이터베이스 소유자 또는 시스템 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-141">Database owner or system administrator.</span></span>  
  
##  <a name="to-prepare-an-existing-mirror-database-to-restart-mirroring"></a><a name="PrepareToRestartMirroring"></a> <span data-ttu-id="e968d-142">미러링을 다시 시작하기 위해 기존 미러 데이터베이스를 준비하려면</span><span class="sxs-lookup"><span data-stu-id="e968d-142">To Prepare an Existing Mirror Database to Restart Mirroring</span></span>  
 <span data-ttu-id="e968d-143">미러링이 제거되었고 미러 데이터베이스가 아직 RECOVERING 상태인 경우 미러링을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-143">If mirroring has been removed and the mirror database is still in the RECOVERING state, you can restart mirroring.</span></span>  
  
1.  <span data-ttu-id="e968d-144">주 데이터베이스에서 하나 이상의 로그 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-144">Take at least one log backup on the principal database.</span></span> <span data-ttu-id="e968d-145">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-145">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="e968d-146">미러 데이터베이스에서 RESTORE WITH NORECOVERY를 사용하여, 미러링이 제거된 후에 주 데이터베이스에서 수행한 모든 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-146">On the mirror database, use RESTORE WITH NORECOVERY to restore all log backups taken on the principal database since mirroring was removed.</span></span> <span data-ttu-id="e968d-147">자세한 내용은 [트랜잭션 로그 백업 복원&#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-147">For more information, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
##  <a name="to-prepare-a-new-mirror-database"></a><a name="CombinedProcedure"></a> <span data-ttu-id="e968d-148">새 미러 데이터베이스를 준비하려면</span><span class="sxs-lookup"><span data-stu-id="e968d-148">To Prepare a New Mirror Database</span></span>  
 <span data-ttu-id="e968d-149">**미러 데이터베이스를 준비하려면**</span><span class="sxs-lookup"><span data-stu-id="e968d-149">**To prepare a mirror database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e968d-150">이 절차에 대한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 예는 이 섹션의 뒷부분에 나오는 [예(Transact-SQL)](#TsqlExample)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e968d-150">For a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="e968d-151">주 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-151">Connect to principal server instance.</span></span>  
  
2.  <span data-ttu-id="e968d-152">주 데이터베이스의 전체 데이터베이스 백업 또는 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-152">Create either a full database backup or a differential database backup of the principal database.</span></span>  
  
    -   [<span data-ttu-id="e968d-153">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-153">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   <span data-ttu-id="e968d-154">[차등 데이터베이스 백업 만들기&#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="e968d-154">[Create a Differential Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="e968d-155">일반적으로 주 데이터베이스에서 하나 이상의 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-155">Typically, you need to take at least one log backup on the principal database.</span></span> <span data-ttu-id="e968d-156">그러나 데이터베이스를 방금 만들었으며 아직 로그 백업이 수행되지 않은 경우 또는 복구 모델이 방금 SIMPLE에서 FULL로 변경된 경우에는 로그 백업이 필요하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-156">However, a log backup might be unnecessary, if the database has just been created and no log backup has been taken yet, or if the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
    -   [<span data-ttu-id="e968d-157">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-157">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  <span data-ttu-id="e968d-158">두 시스템에서 액세스할 수 있는 네트워크 드라이브에 백업이 있지 않으면 데이터베이스 백업과 로그 백업을 미러 서버 인스턴스를 호스팅할 시스템에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-158">Unless the backups are on a network drive that is accessible from both systems, copy the database and log backups to the system that will host the mirror server instance.</span></span>  
  
5.  <span data-ttu-id="e968d-159">미러 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-159">Connect to mirror server instance.</span></span>  
  
6.  <span data-ttu-id="e968d-160">RESTORE WITH NORECOVERY를 통해 전체 데이터베이스 백업 및 필요에 따라 가장 최근의 차등 데이터베이스 백업을 미러 서버 인스턴스에 복원하여 미러 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-160">Using RESTORE WITH NORECOVERY, create the mirror database by restoring the full database backup and, optionally, the most recent differential database backup, onto the mirror server instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e968d-161">파일 그룹별로 데이터베이스 파일 그룹을 복원하는 경우에는 전체 데이터베이스를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-161">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
    -   [<span data-ttu-id="e968d-162">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-162">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   <span data-ttu-id="e968d-163">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 및 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
7.  <span data-ttu-id="e968d-164">RESTORE WITH NORECOVERY를 사용하여 처리 중인 로그 백업을 미러 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-164">Using RESTORE WITH NORECOVERY, apply any outstanding log backup or backups to the mirror database.</span></span>  
  
    -   [<span data-ttu-id="e968d-165">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-165">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e968d-166">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e968d-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="e968d-167">데이터베이스 미러링 세션이 시작되기 전에 미러 데이터베이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-167">Before you can start a database mirroring session, you must create the mirror database.</span></span> <span data-ttu-id="e968d-168">이 작업은 미러링 세션을 시작하기 직전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-168">You should do this just before starting the mirroring session.</span></span>  
  
 <span data-ttu-id="e968d-169">이 예에서는 기본적으로 단순 복구 모델을 사용하는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-169">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="e968d-170">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 데이터베이스 미러링을 사용하려면 전체 복구 모델을 사용하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-170">To use database mirroring with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="e968d-171">데이터베이스 복구 모델을 SIMPLE에서 FULL로 변경한 후 미러 데이터베이스를 만드는 데 사용할 수 있는 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-171">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the mirror database.</span></span> <span data-ttu-id="e968d-172">복구 모델이 방금 변경되었으므로 WITH FORMAT 옵션을 지정하여 새 미디어 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-172">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="e968d-173">이 옵션은 단순 복구 모델에서 만든 이전 백업과 전체 복구 모델에서 만든 백업을 구분하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-173">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="e968d-174">이 예에서는 백업 파일(`C:\AdventureWorks.bak`)이 데이터베이스와 같은 드라이브에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-174">For the purpose of this example, the backup file (`C:\AdventureWorks.bak`) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e968d-175">프로덕션 데이터베이스의 경우에는 항상 별도의 디바이스에 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-175">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="e968d-176">`PARTNERHOST1`의 주 서버 인스턴스에서 주 데이터베이스의 전체 백업을 다음과 같이 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-176">On the principal server instance (on `PARTNERHOST1`), create a full backup of the principal database as follows:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="e968d-177">전체 백업을 미러 서버에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-177">Copy the full backup to the mirror server.</span></span>  
  
4.  <span data-ttu-id="e968d-178">RESTORE WITH NORECOVERY를 사용하여 전체 백업을 미러 서버 인스턴스에 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-178">Using RESTORE WITH NORECOVERY, restore the full backup onto the mirror server instance.</span></span> <span data-ttu-id="e968d-179">복원 명령은 주 데이터베이스와 미러 데이터베이스의 경로가 동일한지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-179">The restore command depends on whether the paths of principal and mirror databases are identical.</span></span>  
  
    -   <span data-ttu-id="e968d-180">**경로가 동일한 경우**</span><span class="sxs-lookup"><span data-stu-id="e968d-180">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="e968d-181">`PARTNERHOST5`의 미러 서버 인스턴스에서 전체 백업을 다음과 같이 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-181">On the mirror server instance (on `PARTNERHOST5`), restore the full backup as follows:</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="e968d-182">**경로가 다른 경우**</span><span class="sxs-lookup"><span data-stu-id="e968d-182">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="e968d-183">미러 데이터베이스의 경로와 주 데이터베이스의 경로가 다른 경우(예: 드라이브 문자가 다른 경우) 미러 데이터베이스를 만들 때 복원 작업에 MOVE 절을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-183">If the path of the mirror database differs from the path of the principal database (for instance, their drive letters differ), creating the mirror database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e968d-184">주 데이터베이스 및 미러 데이터베이스의 경로 이름이 다른 경우 파일을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-184">If the path names of the principal and mirror databases differ, you cannot add a file.</span></span> <span data-ttu-id="e968d-185">이는 파일 추가 작업에 대한 로그를 받을 때 미러 서버 인스턴스가 주 데이터베이스에서 사용하는 위치에 새 파일을 배치하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-185">This is because on receiving the log for the add file operation, the mirror server instance attempts to place the new file in the location used by the principal database.</span></span>  
  
         <span data-ttu-id="e968d-186">예를 들어 다음 명령은 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\에 있는 주 데이터베이스의 백업을 미러 데이터베이스가 배치될 다른 위치인 D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-186">For example, the following command restores a backup of a principal database residing in C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ to a different location, D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`, where the mirror database is to reside.</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="e968d-187">전체 백업을 만든 후 주 데이터베이스에서 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-187">After you create the full backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="e968d-188">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 앞의 전체 백업에 사용된 파일에 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-188">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding full backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="e968d-189">미러링을 시작하기 전에 필수 로그 백업 및 모든 후속 로그 백업을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-189">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="e968d-190">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 `C:\AdventureWorks.bak`에서 첫 번째 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-190">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="e968d-191">미러링을 시작하기 전에 추가 로그 백업이 수행되면 이러한 로그 백업도 WITH NORECOVERY를 사용하여 순서대로 미러 서버로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-191">If any additional log backups occur before you start mirroring, you must also restore all of those log backups, in sequence, to the mirror server using WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="e968d-192">예를 들어 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 `C:\AdventureWorks.bak`에서 두 개의 로그를 추가로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-192">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores two additional logs from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 <span data-ttu-id="e968d-193">보안 설정 표시, 미러 데이터베이스 준비, 파트너 설정 및 미러링 모니터 서버 추가 등의 작업을 수행하는 전체 예제는 [데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-193">For a complete example of setting up database mirroring, showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-preparing-a-mirror-database"></a><a name="FollowUp"></a> <span data-ttu-id="e968d-194">후속 작업: 미러 데이터베이스를 준비한 후</span><span class="sxs-lookup"><span data-stu-id="e968d-194">Follow Up: After Preparing a Mirror Database</span></span>  
  
1.  <span data-ttu-id="e968d-195">대부분의 최근 RESTORE LOG 작업을 수행한 이후 추가 로그 백업이 수행된 경우 RESTORE WITH NORECOVERY를 사용하여 모든 추가 로그 백업을 수동으로 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-195">If any additional log backups have been taken since your most recent RESTORE LOG operation, you must manually apply every additional log backup, using RESTORE WITH NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="e968d-196">미러링 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-196">Start the mirroring session.</span></span> <span data-ttu-id="e968d-197">자세한 내용은 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) 을 사용하여 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-197">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) or [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="e968d-198">주 데이터베이스에서 백업 작업을 해제한 경우 작업을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-198">If you disabled the backup job on the principal database, reenable the job.</span></span>  
  
4.  <span data-ttu-id="e968d-199">장애 조치(Failover) 후 데이터베이스를 신뢰할 수 있어야 하는 경우에는 미러링이 시작된 다음 추가 설정 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-199">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span> <span data-ttu-id="e968d-200">자세한 내용은 [Trustworthy 속성을 사용하도록 미러 데이터베이스 설정&#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)에 미러 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e968d-200">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e968d-201">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e968d-201">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e968d-202">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-202">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="e968d-203">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-203">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="e968d-204">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-204">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="e968d-205">Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-205">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="e968d-206">암호화된 미러 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="e968d-206">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
-   [<span data-ttu-id="e968d-207">Trustworthy 속성을 사용하도록 미러 데이터베이스 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-207">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="e968d-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e968d-208">See Also</span></span>  
 <span data-ttu-id="e968d-209">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-209">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e968d-210">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-210">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="e968d-211">[데이터베이스 미러링 설정&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-211">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e968d-212">[전체 텍스트 카탈로그와 인덱스 백업 및 복원](../../relational-databases/indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-212">[Back Up and Restore Full-Text Catalogs and Indexes](../../relational-databases/indexes/indexes.md) </span></span>  
 <span data-ttu-id="e968d-213">[데이터베이스 미러링 및 전체 텍스트 카탈로그&#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-213">[Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span></span>  
 <span data-ttu-id="e968d-214">[데이터베이스 미러링 및 복제&#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e968d-214">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="e968d-215">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e968d-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e968d-216">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e968d-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="e968d-217">RESTORE 인수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e968d-217">RESTORE Arguments &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
