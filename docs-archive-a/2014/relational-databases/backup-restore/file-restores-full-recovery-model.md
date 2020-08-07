---
title: 파일 복원(전체 복구 모델) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- full recovery model [SQL Server], performing restores
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- file restores [SQL Server], full recovery model
- restoring files [SQL Server], full recovery model
- Transact-SQL restore sequence
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: d2236a2a-4cf1-4c3f-b542-f73f6096e15c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 488515ec900867f13d33580402e36a3f98747bb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731763"
---
# <a name="file-restores-full-recovery-model"></a><span data-ttu-id="559c7-102">파일 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="559c7-102">File Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="559c7-103">이 항목에서는 전체 또는 대량 로드 복구 모델에서 데이터베이스에 여러 개의 파일 또는 파일 그룹이 있는 경우와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-103">This topic is relevant only for databases that contain multiple files or filegroups under the full or bulk-load recovery model.</span></span>  
  
 <span data-ttu-id="559c7-104">파일 복원의 목표는 전체 데이터베이스를 복원하지 않고 하나 이상의 손상된 파일을 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="559c7-105">파일 복원 시나리오는 해당 데이터를 복사하고 롤포워드하고 복구하는 단일 복원 시퀀스로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-105">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data</span></span>  
  
 <span data-ttu-id="559c7-106">복원 중인 파일 그룹이 읽기/쓰기가 가능한 경우 손상되지 않은 로그 백업 체인은 마지막 데이터 또는 차등 백업이 복원된 후에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-106">If the filegroup that is being restored is read/write, an unbroken chain of log backups must be applied after the last data or differential backup is restored.</span></span> <span data-ttu-id="559c7-107">이를 통해 파일 그룹을 로그 파일에 있는 현재 활성 로그 레코드의 로그 레코드로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-107">This brings the filegroup forward to the log records in the current active log records in the log file.</span></span> <span data-ttu-id="559c7-108">일반적으로 복구 지점은 로그의 후반부이지만 반드시 그런 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-108">The recovery point is typically near the end of log, but not necessarily.</span></span>  
  
 <span data-ttu-id="559c7-109">복원 중인 파일 그룹이 읽기 전용인 경우 일반적으로 로그 백업을 적용할 필요가 없으므로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-109">If the filegroup that is being restored is read-only, usually applying log backups is unnecessary and is skipped.</span></span> <span data-ttu-id="559c7-110">파일이 읽기 전용 상태가 된 이후에 백업이 수행되면 마지막 백업이 복원되고</span><span class="sxs-lookup"><span data-stu-id="559c7-110">If the backup was taken after the file became read-only, that is the last backup to restore.</span></span> <span data-ttu-id="559c7-111">롤포워드가 대상 지점에서 정지됩니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-111">Roll forward stops at the target point.</span></span>  
  
 <span data-ttu-id="559c7-112">파일 복원 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-112">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="559c7-113">오프라인 파일 복원</span><span class="sxs-lookup"><span data-stu-id="559c7-113">Offline file restore</span></span>  
  
     <span data-ttu-id="559c7-114">*오프라인 파일 복원*에서 손상된 파일 또는 파일 그룹이 복원되는 동안 데이터베이스는 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-114">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="559c7-115">복원 시퀀스의 마지막에 데이터베이스는 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-115">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="559c7-116">모든 버전의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 오프라인 파일 복원을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-116">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="559c7-117">온라인 파일 복원</span><span class="sxs-lookup"><span data-stu-id="559c7-117">Online file restore</span></span>  
  
     <span data-ttu-id="559c7-118">*온라인 파일 복원*의 경우 데이터베이스가 복원 시점에 온라인 상태이면 파일 복원 중에 온라인 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-118">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="559c7-119">그러나 파일을 복원할 각 파일 그룹은 복원 작업 중에 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-119">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="559c7-120">오프라인 파일 그룹의 모든 파일이 복구되면 파일 그룹이 자동으로 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-120">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="559c7-121">온라인 페이지 및 파일 복원 지원에 대한 자세한 내용은 [SQL Server 2014 버전에서 지원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="559c7-121">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="559c7-122">온라인 복원에 대한 자세한 내용은 [온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="559c7-122">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="559c7-123">파일 복원을 위해 데이터베이스를 오프라인 상태로 전환하려면 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 문: ALTER DATABASE *database_name* SET OFFLINE을 실행하여 복원 시퀀스를 시작하기 전에 데이터베이스 오프라인으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-123">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  
  
  
##  <a name="restoring-damaged-files-from-file-backups"></a><a name="Overview"></a> <span data-ttu-id="559c7-124">파일 백업에서 손상된 파일 복원</span><span class="sxs-lookup"><span data-stu-id="559c7-124">Restoring Damaged Files from File Backups</span></span>  
  
1.  <span data-ttu-id="559c7-125">하나 이상의 손상된 파일을 복원하려면 먼저 [비상 로그 백업](tail-log-backups-sql-server.md)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-125">Before restoring one or more damaged files, attempt to create a [tail-log backup](tail-log-backups-sql-server.md).</span></span>  
  
     <span data-ttu-id="559c7-126">로그가 손상된 경우에는 비상 로그 백상을 만들 수 없으며 데이터베이스 전체를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-126">If the log has been damaged, a tail-log backup cannot be created, and you must restore the whole database.</span></span>  
  
     <span data-ttu-id="559c7-127">트랜잭션 로그를 백업하는 방법은 [트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="559c7-127">For information about how to back up a transaction log, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="559c7-128">오프라인 파일을 복원하려면 이 파일을 복원하기 전에 비상 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-128">For an offline file restore, you must always take a tail-log backup before the file restore.</span></span> <span data-ttu-id="559c7-129">온라인 파일을 복원하려면 이 파일을 복원한 후에 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-129">For an online file restore, you must always take the log backup after the file restore.</span></span> <span data-ttu-id="559c7-130">이러한 로그 백업은 파일을 데이터베이스의 나머지 부분과 일치하는 상태로 복구해야 하기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-130">This log backup is necessary to allow for the file to be recovered to a state consistent with the rest of the database.</span></span>  
  
2.  <span data-ttu-id="559c7-131">각 손상된 파일을 해당 파일의 최신 백업에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-131">Restore each damaged file from the most recent file backup of that file.</span></span>  
  
3.  <span data-ttu-id="559c7-132">복원된 각 파일에 대한 가장 최근의 차등 파일 백업(있을 경우)을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-132">Restore the most recent differential file backup, if any, for each restored file.</span></span>  
  
4.  <span data-ttu-id="559c7-133">복원 파일 중 가장 오래된 것을 포함하는 백업부터 시작하여 1단계에서 만든 비상 로그 백업까지 트랜잭션 로그 백업을 순서대로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-133">Restore transaction log backups in sequence, starting with the backup that covers the oldest of the restored files and ending with the tail-log backup created in step 1.</span></span>  
  
     <span data-ttu-id="559c7-134">파일 백업 후에는 생성된 트랜잭션 로그 백업을 복원하여 데이터베이스와 일치하는 상태로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-134">You must restore the transaction log backups that were created after the file backups to bring the database to a consistent state.</span></span> <span data-ttu-id="559c7-135">트랜잭션 로그 백업은 복원 파일에 적용된 변경 내용만 적용하므로 빨리 롤포워드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-135">The transaction log backups can be rolled forward quickly, because only the changes that apply to the restored files are applied.</span></span> <span data-ttu-id="559c7-136">손상되지 않은 파일은 복사되지 않고 롤포워드되므로 개별 파일 복원이 전체 데이터베이스 복원보다 나을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-136">Restoring individual files can be better than restoring the whole database, because undamaged files are not copied and then rolled forward.</span></span> <span data-ttu-id="559c7-137">하지만 전체 로그 백업 체인은 읽기가 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-137">However, the whole chain of log backups still has to be read.</span></span>  
  
5.  <span data-ttu-id="559c7-138">데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-138">Recover the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="559c7-139">파일 백업은 지정 시간 이전의 시점으로 데이터베이스를 복원하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-139">File backups can be used to restore the database to an earlier point in time.</span></span> <span data-ttu-id="559c7-140">이렇게 하려면 파일 백업의 전체 세트를 복원한 후 최근 복원된 파일 백업 다음에 있는 대상 지점에 이를 때까지 순서대로 트랜잭션 로그 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-140">To do this, you must restore a complete set of file backups, and then restore transaction log backups in sequence to reach a target point that is after the end of the most recent restored file backup.</span></span> <span data-ttu-id="559c7-141">지정 시간 복구에 대한 자세한 내용은 [SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="559c7-141">For more information about point-in-time recovery, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
## <a name="transact-sql-restore-sequence-for-an-offline-file-restore-full-recovery-model"></a><span data-ttu-id="559c7-142">오프라인 파일 복원을 위한 Transact-SQL 복원 시퀀스(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="559c7-142">Transact-SQL Restore Sequence for an Offline File Restore (Full Recovery Model)</span></span>  
 <span data-ttu-id="559c7-143">파일 복원 시나리오는 해당 데이터를 복사하고 롤포워드하고 복구하는 단일 복원 시퀀스로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-143">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data.</span></span>  
  
 <span data-ttu-id="559c7-144">이 섹션에서는 파일 복원 시퀀스에 대한 필수 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-144">This section shows the essential [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a file-restore sequence.</span></span> <span data-ttu-id="559c7-145">이 용도와 관련 없는 구문 및 세부 사항은 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-145">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="559c7-146">다음 예에서는 WITH NORECOVERY를 사용하여 두 개의 보조 파일 `A` 와 `B`를 오프라인 복원하는 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-146">The following sample restore sequence shows an offline restore of two secondary files, `A` and `B`, using WITH NORECOVERY.</span></span> <span data-ttu-id="559c7-147">그런 다음 두 개의 로그 백업에 NORECOVERY를 적용한 다음 WITH RECOVERY를 사용하여 복원되는 비상 로그 백업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-147">Next, two log backups are applied with NORECOVERY, followed with the tail-log backup, and this is restored using WITH RECOVERY.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="559c7-148">다음 예에서는 파일을 오프라인으로 전환하여 복원 시퀀스를 시작하고 비상 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="559c7-148">The following sample restore sequence starts by taking the file offline and then creates a tail-log backup.</span></span>  
  
```  
--Take the file offline.  
ALTER DATABASE database_name MODIFY FILE SET OFFLINE;  
-- Back up the currently active transaction log.  
BACKUP LOG database_name  
   TO <tail_log_backup>  
   WITH NORECOVERY;  
GO   
-- Restore the files.  
RESTORE DATABASE database_name FILE=name   
   FROM <file_backup_of_file_A>   
   WITH NORECOVERY;  
RESTORE DATABASE database_name FILE=<name> ......  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
-- Restore the log backups.  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <tail_log_backup>   
   WITH RECOVERY;  
```  
  
## <a name="examples"></a><span data-ttu-id="559c7-149">예</span><span class="sxs-lookup"><span data-stu-id="559c7-149">Examples</span></span>  
  
-   [<span data-ttu-id="559c7-150">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-150">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="559c7-151">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-151">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="559c7-152">예: 주 파일 그룹 및 다른 파일 그룹의 오프라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-152">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="559c7-153">관련 작업</span><span class="sxs-lookup"><span data-stu-id="559c7-153">Related Tasks</span></span>  
 <span data-ttu-id="559c7-154">**파일과 파일 그룹을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="559c7-154">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="559c7-155">새 위치로 파일 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-155">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="559c7-156">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-156">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="559c7-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="559c7-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="559c7-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="559c7-158">See Also</span></span>  
 <span data-ttu-id="559c7-159">[백업 및 복원: 상호 운용성 및 공존성&#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-159">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="559c7-160">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-160">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="559c7-161">[전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-161">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="559c7-162">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-162">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="559c7-163">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-163">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="559c7-164">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="559c7-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="559c7-165">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="559c7-165">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="559c7-166">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="559c7-166">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
