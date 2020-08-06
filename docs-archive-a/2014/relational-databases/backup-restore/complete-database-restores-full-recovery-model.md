---
title: 전체 데이터베이스 복원(전체 복구 모델) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- restoring [SQL Server], database
- full recovery model [SQL Server], performing restores
- log backups [SQL Server[
ms.assetid: 5b4c471c-b972-498e-aba9-92cf7a0ea881
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea6ec9f196acd0a64a0b785024bd6426cd6a5381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661191"
---
# <a name="complete-database-restores-full-recovery-model"></a><span data-ttu-id="b47c0-102">전체 데이터베이스 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="b47c0-102">Complete Database Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="b47c0-103">전체 데이터베이스 복원의 목적은 전체 데이터베이스를 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="b47c0-104">복원하는 동안 전체 데이터베이스는 오프라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="b47c0-105">데이터베이스의 일부를 온라인에 연결하기 전에 데이터베이스의 모든 부분의 지정 시간이 같고 커밋되지 않은 트랜잭션이 없는 일치하는 지점으로 모든 데이터를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="b47c0-106">전체 복구 모델에서는 데이터 백업이나 백업을 복원한 후, 이후의 모든 트랜잭션 로그 백업을 복원한 다음 데이터베이스를 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-106">Under the full recovery model, after you restore your data backup or backups, you must restore all subsequent transaction log backups and then recover the database.</span></span> <span data-ttu-id="b47c0-107">이러한 로그 백업 중 하나의 특정 *복구 지점* 으로 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-107">You can restore a database to a specific *recovery point* within one of these log backups.</span></span> <span data-ttu-id="b47c0-108">복구 지점은 특정 날짜 및 시간, 표시된 트랜잭션 또는 LSN(로그 시퀀스 번호)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-108">The recovery point can be a specific date and time, a marked transaction, or a log sequence number (LSN).</span></span>  
  
 <span data-ttu-id="b47c0-109">데이터베이스를 복원할 경우, 특히 전체 복구 모델 또는 대량 로그 복구 모델에서는 단일 복원 순서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-109">When restoring a database, particularly under the full recovery model or bulk-logged recovery model, you should use a single restore sequence.</span></span> <span data-ttu-id="b47c0-110">*복원 순서* 는 하나 이상의 복원 단계를 통해 데이터를 이동시키는 하나 이상의 복원 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-110">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b47c0-111">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-111">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="b47c0-112">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-112">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="b47c0-113">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-113">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
 <span data-ttu-id="b47c0-114">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="b47c0-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="b47c0-115">데이터베이스를 오류 지점으로 복원</span><span class="sxs-lookup"><span data-stu-id="b47c0-115">Restoring a Database to the Point of Failure</span></span>](#PointOfFailure)  
  
-   [<span data-ttu-id="b47c0-116">데이터베이스를 로그 백업 내 지점으로 복원</span><span class="sxs-lookup"><span data-stu-id="b47c0-116">Restoring a Database to a Point Within a Log Backup</span></span>](#PointWithinBackup)  
  
-   [<span data-ttu-id="b47c0-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b47c0-117">Related Tasks</span></span>](#RelatedTasks)  
  
> [!NOTE]  
>  <span data-ttu-id="b47c0-118">이전 버전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 백업 지원에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)의 "호환성 지원" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-118">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="restoring-a-database-to-the-point-of-failure"></a><a name="PointOfFailure"></a> <span data-ttu-id="b47c0-119">오류 지점으로 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="b47c0-119">Restoring a Database to the Point of Failure</span></span>  
 <span data-ttu-id="b47c0-120">일반적으로 실패 지점으로 데이터베이스를 복구하는 작업에는 다음의 기본 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-120">Typically, recovering a database to the point of failure involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="b47c0-121">활성 트랜잭션 로그(비상 로그)를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-121">Back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="b47c0-122">이렇게 하면 비상 로그 백업이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-122">This creates a tail-log backup.</span></span> <span data-ttu-id="b47c0-123">활성 트랜잭션 로그를 사용할 수 없을 때 해당 로그 부분의 모든 트랜잭션이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-123">If the active transaction log is unavailable, all transactions in that part of the log are lost.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b47c0-124">대량 로그 복구 모델에서 대량 로그 작업이 포함된 로그를 백업하려면 데이터베이스의 모든 데이터 파일에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-124">Under the bulk-logged recovery model, backing up any log that contains bulk-logged operations requires access to all data files in the database.</span></span> <span data-ttu-id="b47c0-125">데이터 파일에 액세스할 수 없는 경우 트랜잭션 로그를 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-125">If the data files cannot be accessed, the transaction log cannot be backed up.</span></span> <span data-ttu-id="b47c0-126">이 경우 가장 최근의 로그 백업 이후 변경된 모든 내용을 수동으로 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-126">In that case, you have to manually redo all changes that were made since the most recent log backup.</span></span>  
  
     <span data-ttu-id="b47c0-127">자세한 내용은 [비상 로그 백업&#40;SQL Server&#41;](tail-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-127">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="b47c0-128">데이터베이스를 복구하지 않고 가장 최근의 전체 데이터베이스 백업을 복원합니다(RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span><span class="sxs-lookup"><span data-stu-id="b47c0-128">Restore the most recent full database backup without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
3.  <span data-ttu-id="b47c0-129">차등 백업이 있는 경우 데이터베이스를 복구하지 않고 가장 최근의 차등 백업을 복원합니다(RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY).</span><span class="sxs-lookup"><span data-stu-id="b47c0-129">If differential backups exist, restore the most recent one without recovering the database (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY).</span></span>  
  
     <span data-ttu-id="b47c0-130">가장 최근의 차등 백업을 복원하면 복원해야 하는 로그 백업 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-130">Restoring the most recent differential backup reduces the number of log backups that must be restored.</span></span>  
  
4.  <span data-ttu-id="b47c0-131">복원한 백업 이후 첫 번째 트랜잭션 로그 백업부터 시작하여 NORECOVERY의 순서로 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-131">Starting with the first transaction log backup that was created after the backup you just restored, restore the logs in sequence with NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="b47c0-132">데이터베이스를 복구합니다(RESTORE DATABASE *database_name* WITH RECOVERY).</span><span class="sxs-lookup"><span data-stu-id="b47c0-132">Recover the database (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span> <span data-ttu-id="b47c0-133">또는 이 단계를 마지막 로그 백업 복원과 결합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-133">Alternatively, this step can be combined with restoring the last log backup.</span></span>  
  
 <span data-ttu-id="b47c0-134">다음 그림은 이 복원 순서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-134">The following illustration shows this restore sequence.</span></span> <span data-ttu-id="b47c0-135">오류가 발생한 후(1) 비상 로그 백업이 생성됩니다(2).</span><span class="sxs-lookup"><span data-stu-id="b47c0-135">After a failure occurs (1), a tail-log backup is created (2).</span></span> <span data-ttu-id="b47c0-136">그런 다음 데이터베이스가 오류 지점으로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-136">Next, the database is restored to the point of the failure.</span></span> <span data-ttu-id="b47c0-137">이 과정에는 데이터베이스 백업 및 후속 차등 백업을 복원하고, 비상 로그 백업을 포함하여 차등 백업 이후에 생성된 모든 로그 백업을 복원하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-137">This involves restoring a database backup, a subsequent differential backup, and every log backup taken after the differential backup, including the tail-log backup.</span></span>  
  
 <span data-ttu-id="b47c0-138">![실패 시간으로 전체 데이터베이스 복원](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "실패 시간으로 전체 데이터베이스 복원")</span><span class="sxs-lookup"><span data-stu-id="b47c0-138">![Complete database restore to the time of a failure](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "Complete database restore to the time of a failure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b47c0-139">데이터베이스 백업을 다른 서버 인스턴스로 복원할 경우 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-139">When you restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="b47c0-140">기본 Transact-SQL RESTORE 구문</span><span class="sxs-lookup"><span data-stu-id="b47c0-140">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="b47c0-141">이전 그림의 복원 순서에 대한 기본 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-141">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for the restore sequence in the preceding illustration is as follows:</span></span>  
  
1.  <span data-ttu-id="b47c0-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="b47c0-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span></span>  
  
2.  <span data-ttu-id="b47c0-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="b47c0-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span></span>  
  
3.  <span data-ttu-id="b47c0-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="b47c0-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span></span>  
  
     <span data-ttu-id="b47c0-145">각 추가 로그 백업에 대해 이 복원 로그 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-145">Repeat this restore-log step for each additional log backup.</span></span>  
  
4.  <span data-ttu-id="b47c0-146">RESTORE DATABASE *database* WITH RECOVERY;</span><span class="sxs-lookup"><span data-stu-id="b47c0-146">RESTORE DATABASE *database* WITH RECOVERY;</span></span>  
  
###  <a name="example-recovering-to-the-point-of-failure-transact-sql"></a><a name="ExampleToPoFTsql"></a> <span data-ttu-id="b47c0-147">예제: 오류 지점으로 복구(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b47c0-147">Example: Recovering to the Point of Failure (Transact-SQL)</span></span>  
 <span data-ttu-id="b47c0-148">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 예에서는 복원 순서에서 오류 지점으로 데이터베이스를 복원하는 필수 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-148">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] example shows the essential options in a restore sequence that restores the database to the point of failure.</span></span> <span data-ttu-id="b47c0-149">이 예에서는 데이터베이스의 비상 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-149">The example creates a tail-log backup of the database.</span></span> <span data-ttu-id="b47c0-150">다음으로 전체 데이터베이스 백업 및 로그 백업을 복원한 다음 비상 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-150">Next, the example restores a full database backup and log backup and then restores the tail-log backup.</span></span> <span data-ttu-id="b47c0-151">이 예의 경우 별도의 마지막 단계에서 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-151">The example recovers the database in a separate, final step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b47c0-152">이 예에서는 [전체 데이터베이스 백업&#40;SQL Server&#41;](full-database-backups-sql-server.md)의 "호환성 지원" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-152">This example uses a database backup and log backup that is created in the "Using Database Backups Under the Full Recovery Model" section in [Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md).</span></span> <span data-ttu-id="b47c0-153">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스는 데이터베이스 백업 전에 전체 복구 모델을 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-153">Before the database backup, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database was set to use the full recovery model.</span></span>  
  
```  
USE master;  
--Create tail-log backup.  
BACKUP LOG AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'    
   WITH NORECOVERY;   
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=1,   
    NORECOVERY;  
  
--Restore the regular log backup (from backup set 2).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=2,   
    NORECOVERY;  
  
--Restore the tail-log backup (from backup set 3).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'  
  WITH FILE=3,   
    NORECOVERY;  
GO  
--recover the database:  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
GO  
```  
  
##  <a name="restoring-a-database-to-a-point-within-a-log-backup"></a><a name="PointWithinBackup"></a> <span data-ttu-id="b47c0-154">데이터베이스를 로그 백업 내 지점으로 복원</span><span class="sxs-lookup"><span data-stu-id="b47c0-154">Restoring a Database to a Point Within a Log Backup</span></span>  
 <span data-ttu-id="b47c0-155">전체 복구 모델에서, 전체 데이터베이스 복원은 일반적으로 지정 시간, 표시된 트랜잭션 또는 로그 백업 내 LSN으로 복구될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-155">Under the full recovery model, a complete database restore can usually be recovered to a point of time, a marked transaction, or an LSN within a log backup.</span></span> <span data-ttu-id="b47c0-156">그러나 대량 로그 복구 모델에서 로그 백업에 대량 로그 변경 내용이 있을 경우 지정 시간 복구를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-156">However, under the bulk-logged recovery model, if the log backup contains bulk-logged changes, point-in-time recovery is not possible.</span></span>  
  
### <a name="sample-point-in-time-restore-scenarios"></a><span data-ttu-id="b47c0-157">예제 지정 시간 복원 시나리오</span><span class="sxs-lookup"><span data-stu-id="b47c0-157">Sample Point-in-Time Restore Scenarios</span></span>  
 <span data-ttu-id="b47c0-158">다음 예에서는 매일 자정에 전체 데이터베이스 백업을 만들고 월요일부터 토요일까지 정시에 차등 데이터베이스 백업을 만들며 하루 종일 10분마다 트랜잭션 로그 백업을 만드는 업무용 데이터베이스 시스템이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-158">The following example assumes a mission-critical database system for which a full database backup is created daily at midnight, a differential database backup is created on the hour, Monday through Saturday, and transaction log backups are created every 10 minutes throughout the day.</span></span> <span data-ttu-id="b47c0-159">데이터베이스를 수요일 5:19 A.M. 상태로 복원하려면</span><span class="sxs-lookup"><span data-stu-id="b47c0-159">To restore the database to the state is was in at 5:19 A.M.</span></span> <span data-ttu-id="b47c0-160">다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-160">Wednesday, do the following:</span></span>  
  
1.  <span data-ttu-id="b47c0-161">화요일 자정에 만든 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-161">Restore the full database backup that was created Tuesday at midnight.</span></span>  
  
2.  <span data-ttu-id="b47c0-162">수요일 5:00 A.M.에 만든 차등 데이터베이스 백업을</span><span class="sxs-lookup"><span data-stu-id="b47c0-162">Restore the differential database backup that was created at 5:00 A.M.</span></span> <span data-ttu-id="b47c0-163">적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-163">on Wednesday.</span></span>  
  
3.  <span data-ttu-id="b47c0-164">수요일 5:10 A.M.에 만든 트랜잭션 로그 백업을</span><span class="sxs-lookup"><span data-stu-id="b47c0-164">Apply the transaction log backup that was created at 5:10 A.M.</span></span> <span data-ttu-id="b47c0-165">적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-165">on Wednesday.</span></span>  
  
4.  <span data-ttu-id="b47c0-166">복구 프로세스에서 5:19 A.M. 전에 발생한 트랜잭션만 적용하도록 지정하여 수요일 5:20 A.M.에</span><span class="sxs-lookup"><span data-stu-id="b47c0-166">Apply the transaction log backup that was created 5:20 A.M.</span></span> <span data-ttu-id="b47c0-167">만든 트랜잭션 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-167">on Wednesday, specifying that the recovery process applies only to transactions that occurred before 5:19 A.M.</span></span>  
  
 <span data-ttu-id="b47c0-168">또는 데이터베이스를 목요일 3:04 A.M.의 상태로 복원해야 하는데</span><span class="sxs-lookup"><span data-stu-id="b47c0-168">Alternatively, if the database needs to be restored to its state at 3:04 A.M.</span></span> <span data-ttu-id="b47c0-169">목요일 3:00 A.M.에 만든 차등 데이터베이스 백업을 사용할 수 없으면</span><span class="sxs-lookup"><span data-stu-id="b47c0-169">Thursday, but the differential database backup that was created at 3:00 A.M.</span></span> <span data-ttu-id="b47c0-170">다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-170">Thursday is unavailable, do the following:</span></span>  
  
1.  <span data-ttu-id="b47c0-171">수요일 자정에 만든 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-171">Restore the database backup that was created Wednesday at midnight.</span></span>  
  
2.  <span data-ttu-id="b47c0-172">목요일 2:00 A.M.에 만든 차등 데이터베이스 백업을</span><span class="sxs-lookup"><span data-stu-id="b47c0-172">Restore the differential database backup that was created at 2:00 A.M.</span></span> <span data-ttu-id="b47c0-173">적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-173">on Thursday.</span></span>  
  
3.  <span data-ttu-id="b47c0-174">목요일 2:10 A.M.부터 3:00 A.M.까지 만든 트랜잭션 로그 백업을</span><span class="sxs-lookup"><span data-stu-id="b47c0-174">Apply all the transaction log backups created from 2:10 A.M.</span></span> <span data-ttu-id="b47c0-175">모두</span><span class="sxs-lookup"><span data-stu-id="b47c0-175">to 3:00 A.M.</span></span> <span data-ttu-id="b47c0-176">적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-176">on Thursday.</span></span>  
  
4.  <span data-ttu-id="b47c0-177">목요일 3:04 A.M.에 복구 프로세스를 중지하여 3:10 A.M.에 만든</span><span class="sxs-lookup"><span data-stu-id="b47c0-177">Apply the transaction log backup that was created at 3:10 A.M.</span></span> <span data-ttu-id="b47c0-178">트랜잭션 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b47c0-178">on Thursday, stopping the recovery process at 3:04 A.M.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b47c0-179">지정 시간으로 복원하는 예제를 보려면 [SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)의 "호환성 지원" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b47c0-179">For an example of a point-in-time restore, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b47c0-180">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b47c0-180">Related Tasks</span></span>  
 <span data-ttu-id="b47c0-181">**전체 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="b47c0-181">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="b47c0-182">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-182">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="b47c0-183">데이터베이스를 새 위치로 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-183">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="b47c0-184">**차등 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="b47c0-184">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="b47c0-185">차등 데이터베이스 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-185">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="b47c0-186">**트랜잭션 로그 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="b47c0-186">**To restore a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="b47c0-187">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-187">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="b47c0-188">**SMO(SQL Server 관리 개체)를 사용하여 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="b47c0-188">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
 <span data-ttu-id="b47c0-189">**데이터베이스를 로그 백업 내 지점으로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="b47c0-189">**To restore a database to a point within a log backup**</span></span>  
  
-   [<span data-ttu-id="b47c0-190">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-190">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="b47c0-191">표시된 트랜잭션이 포함된 관련 데이터베이스 복구</span><span class="sxs-lookup"><span data-stu-id="b47c0-191">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="b47c0-192">로그 시퀀스 번호로 복구&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-192">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b47c0-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b47c0-193">See Also</span></span>  
 <span data-ttu-id="b47c0-194">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b47c0-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="b47c0-195">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b47c0-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="b47c0-196">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b47c0-196">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b47c0-197">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b47c0-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="b47c0-198">[전체 데이터베이스 백업&#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b47c0-198">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b47c0-199">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b47c0-199">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b47c0-200">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b47c0-200">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="b47c0-201">복원 및 복구 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b47c0-201">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
