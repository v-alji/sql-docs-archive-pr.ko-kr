---
title: 비상 로그 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd7c505701a4edb1f66ca516d06179b2eb1a222d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647066"
---
# <a name="tail-log-backups-sql-server"></a><span data-ttu-id="6210e-102">비상 로그 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6210e-102">Tail-Log Backups (SQL Server)</span></span>
  <span data-ttu-id="6210e-103">이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 백업 및 복원과 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-103">This topic is relevant only for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="6210e-104">*비상 로그 백업* 에서는 아직 백업되지 않은 로그 레코드를 캡처하여( *비상 로그*) 캡처하여 작업 손실을 방지하고 로그 체인을 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-104">A *tail-log backup* captures any log records that have not yet been backed up (the *tail of the log*) to prevent work loss and to keep the log chain intact.</span></span> <span data-ttu-id="6210e-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 마지막 시점으로 복구하려면 트랜잭션 비상 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-105">Before you can recover a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to its latest point in time, you must back up the tail of its transaction log.</span></span> <span data-ttu-id="6210e-106">비상 로그 백업은 데이터베이스에 대한 복구 계획의 마지막 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-106">The tail-log backup will be the last backup of interest in the recovery plan for the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6210e-107">모든 복원 시나리오에서 비상 로그 백업이 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-107">Not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="6210e-108">복구 시점이 이전 로그 백업에 포함될 경우에는 비상 로그 백업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-108">You do not need a tail-log backup if the recovery point is contained in an earlier log backup.</span></span> <span data-ttu-id="6210e-109">데이터베이스를 이동 또는 대체(덮어쓰기)하며 가장 최근 백업 이후의 시점으로 이를 복원할 필요가 없을 경우에도 비상 로그 백업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-109">Also, a tail-log backup is unnecessary if you are moving or replacing (overwriting) a database and do not need to restore it to a point of time after its most recent backup.</span></span>  
  
 
  
##  <a name="scenarios-that-require-a-tail-log-backup"></a><a name="TailLogScenarios"></a> <span data-ttu-id="6210e-110">비상 로그 백업이 필요한 시나리오</span><span class="sxs-lookup"><span data-stu-id="6210e-110">Scenarios That Require a Tail-Log Backup</span></span>  
 <span data-ttu-id="6210e-111">다음과 같은 경우에는 비상 로그 백업을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-111">We recommend that you take a tail-log backup in the following scenarios:</span></span>  
  
-   <span data-ttu-id="6210e-112">데이터베이스가 온라인이며 데이터베이스에서 복원 작업을 수행하려는 경우 먼저 비상 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-112">If the database is online and you plan to perform a restore operation on the database, begin by backing up the tail of the log.</span></span> <span data-ttu-id="6210e-113">온라인 데이터베이스에 대 한 오류를 방지 하려면 다음을 사용 해야 합니다. [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문의 WITH NORECOVERY 옵션을 사용 [!INCLUDE[tsql](../../includes/tsql-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-113">To avoid an error for an online database, you must use the ... WITH NORECOVERY option of the [BACKUP](/sql/t-sql/statements/backup-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="6210e-114">데이터베이스가 오프라인이고 시작되지 않아서 데이터베이스를 복원해야 할 경우 먼저 비상 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-114">If a database is offline and fails to start and you need to restore the database, first back up the tail of the log.</span></span> <span data-ttu-id="6210e-115">이 시점에서는 트랜잭션이 발생할 수 없으므로 WITH NORECOVERY 옵션의 사용은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-115">Because no transactions can occur at this time, using the WITH NORECOVERY is optional.</span></span>  
  
-   <span data-ttu-id="6210e-116">데이터베이스가 손상된 경우 BACKUP 문의 WITH CONTINUE_AFTER_ERROR 옵션을 사용하여 비상 로그 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-116">If a database is damaged, try to take a tail-log backup by using the WITH CONTINUE_AFTER_ERROR option of the BACKUP statement.</span></span>  
  
     <span data-ttu-id="6210e-117">손상된 데이터베이스에 대한 비상 로그 백업은 로그 파일이 손상되지 않고, 데이터베이스가 비상 로그 백업을 지원하는 상태에 있고, 데이터베이스에 대량 로깅된 변경 내용이 없는 경우에만 성공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-117">On a damaged database backing up the tail of the log can succeed only if the log files are undamaged, the database is in a state that supports tail-log backups, and the database does not contain any bulk-logged changes.</span></span> <span data-ttu-id="6210e-118">배상 로그 백업을 만들 수 없는 경우 마지막 로그 백업 이후에 커밋된 모든 트랜잭션은 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-118">If a tail-log backup cannot be created, any transactions committed after the latest log backup are lost.</span></span>  
  
 <span data-ttu-id="6210e-119">다음 표에는 BACKUP NORECOVERY 및 CONTINUE_AFTER_ERROR 옵션이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-119">The following table summarizes the BACKUP NORECOVERY and CONTINUE_AFTER_ERROR options.</span></span>  
  
|<span data-ttu-id="6210e-120">BACKUP LOG 옵션</span><span class="sxs-lookup"><span data-stu-id="6210e-120">BACKUP LOG option</span></span>|<span data-ttu-id="6210e-121">주석</span><span class="sxs-lookup"><span data-stu-id="6210e-121">Comments</span></span>|  
|-----------------------|--------------|  
|<span data-ttu-id="6210e-122">NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="6210e-122">NORECOVERY</span></span>|<span data-ttu-id="6210e-123">데이터베이스에서 복원 작업을 계속하려는 경우 NORECOVERY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-123">Use NORECOVERY whenever you intend to continue with a restore operation on the database.</span></span> <span data-ttu-id="6210e-124">NORECOVERY는 데이터베이스를 복원 중인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-124">NORECOVERY takes the database into the restoring state.</span></span> <span data-ttu-id="6210e-125">이렇게 하면 비상 로그 백업 후 데이터베이스가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-125">This guarantees that the database does not change after the tail-log backup.</span></span>  <span data-ttu-id="6210e-126">NO_TRUNCATE 옵션 또는 COPY_ONLY 옵션을 함께 지정하지 않으면 로그가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-126">The log is truncated unless the NO_TRUNCATE option or COPY_ONLY option is also specified.</span></span><br /><br /> <span data-ttu-id="6210e-127">중요 데이터베이스가 손상 된 경우를 제외 하 고 NO_TRUNCATE를 사용 하지 않는 것이 좋습니다. \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="6210e-127">**\*\* Important \*\*** We recommend that you avoid using NO_TRUNCATE, except when the database is damaged.</span></span>|  
|<span data-ttu-id="6210e-128">CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="6210e-128">CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="6210e-129">손상된 데이터베이스의 비상 로그를 백업하는 경우에만 CONTINUE_AFTER_ERROR를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-129">Use CONTINUE_AFTER_ERROR only if you are backing up the tail of a damaged database.</span></span><br /><br /> <span data-ttu-id="6210e-130">참고: 손상 된 데이터베이스에서 비상 로그 백업을 사용 하는 경우 일반적으로 로그 백업에서 캡처되는 메타 데이터 중 일부를 사용할 수 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-130">Note: When you use back up the tail of the log on a damaged database, some of the metadata ordinarily captured in log backups might be unavailable.</span></span> <span data-ttu-id="6210e-131">자세한 내용은 이 항목의 뒷부분에 나오는 [완전하지 않은 백업 메타데이터가 포함된 비상 로그 백업](#IncompleteMetadata)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6210e-131">For more information, see [Tail-Log Backups That Have Incomplete Backup Metadata](#IncompleteMetadata), later in this topic.</span></span>|  
  
##  <a name="tail-log-backups-that-have-incomplete-backup-metadata"></a><a name="IncompleteMetadata"></a><span data-ttu-id="6210e-132">완전 하지 않은 백업 메타 데이터가 포함 된 비상 로그 백업</span><span class="sxs-lookup"><span data-stu-id="6210e-132">Tail-Log Backups That Have Incomplete Backup Metadata</span></span>  
 <span data-ttu-id="6210e-133">비상 로그 백업은 데이터베이스가 오프라인이거나 손상되었거나 데이터 파일이 없는 경우에도 비상 로그를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-133">Tail log backups capture the tail of the log even if the database is offline, damaged, or missing data files.</span></span> <span data-ttu-id="6210e-134">이로 인해 복원 정보 명령과 **msdb**의 메타데이터가 완전하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-134">This might cause incomplete metadata from the restore information commands and **msdb**.</span></span> <span data-ttu-id="6210e-135">그러나 메타데이터가 완전하지 않은 경우에도 캡처된 로그는 완전한 상태이며 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-135">However, only the metadata is incomplete; the captured log is complete and usable.</span></span>  
  
 <span data-ttu-id="6210e-136">비상 로그 백업에 완전하지 않은 메타데이터가 있으면 [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) 테이블의 **has_incomplete_metadata** 가 **1**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-136">If a tail-log backup has incomplete metadata, in the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table, **has_incomplete_metadata** is set to **1**.</span></span> <span data-ttu-id="6210e-137">또한 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)출력에서 **HasIncompleteMetadata** 는 **1**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-137">Also, in the output of [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql), **HasIncompleteMetadata** is set to **1**.</span></span>  
  
 <span data-ttu-id="6210e-138">비상 로그 백업의 메타데이터가 완전하지 않으면 [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) 테이블은 비상 로그 백업 당시 파일 그룹에 대한 대부분의 정보를 잃게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-138">If the metadata in a tail-log backup is incomplete, the [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) table will be missing most of the information about filegroups at the time of the tail-log backup.</span></span> <span data-ttu-id="6210e-139">대부분의 **backupfilegroup** 테이블 열은 NULL이 되며 다음 열만 의미를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="6210e-139">Most of the **backupfilegroup** table columns are NULL; the only meaningful columns are as follows:</span></span>  
  
-   <span data-ttu-id="6210e-140">**backup_set_id**</span><span class="sxs-lookup"><span data-stu-id="6210e-140">**backup_set_id**</span></span>  
  
-   <span data-ttu-id="6210e-141">**filegroup_id**</span><span class="sxs-lookup"><span data-stu-id="6210e-141">**filegroup_id**</span></span>  
  
-   <span data-ttu-id="6210e-142">**type**</span><span class="sxs-lookup"><span data-stu-id="6210e-142">**type**</span></span>  
  
-   <span data-ttu-id="6210e-143">**type_desc**</span><span class="sxs-lookup"><span data-stu-id="6210e-143">**type_desc**</span></span>  
  
-   <span data-ttu-id="6210e-144">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="6210e-144">**is_readonly**</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6210e-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6210e-145">Related Tasks</span></span>  
 <span data-ttu-id="6210e-146">비상 로그 백업을 만들려면 [데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6210e-146">To create a tail-log backup, see [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
 <span data-ttu-id="6210e-147">트랜잭션 로그 백업을 복원하려면 [트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6210e-147">To restore a transaction log backup, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6210e-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6210e-148">See Also</span></span>  
 <span data-ttu-id="6210e-149">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6210e-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6210e-150">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6210e-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="6210e-151">[SQL Server 데이터베이스 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="6210e-151">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="6210e-152">[복사 전용 백업&#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6210e-152">[Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6210e-153">[트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6210e-153">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="6210e-154">트랜잭션 로그 백업 적용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6210e-154">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
