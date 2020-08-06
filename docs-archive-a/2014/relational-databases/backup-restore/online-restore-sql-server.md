---
title: 온라인 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- online restores [SQL Server]
- online restores [SQL Server], about online restores
ms.assetid: 7982a687-980a-4eb8-8e9f-6894148e7d8c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4db4d5b5ce08c50646857099d82964bb944bc8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653478"
---
# <a name="online-restore-sql-server"></a><span data-ttu-id="9046b-102">온라인 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9046b-102">Online Restore (SQL Server)</span></span>
  <span data-ttu-id="9046b-103">온라인 복원은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-103">Online restore is supported only on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition.</span></span> <span data-ttu-id="9046b-104">이 버전에서 기본적으로 파일, 페이지 또는 증분 복원은 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-104">In this edition, a file, page, or piecemeal restore is online by default.</span></span> <span data-ttu-id="9046b-105">이 항목에서는 데이터베이스에 여러 개의 파일 또는 파일 그룹이 있는 경우 및 단순 복구 모델에서 데이터베이스에 읽기 전용 파일 그룹만 있는 경우와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-105">This topic is relevant for databases that contain multiple files or filegroups (and, under the simple recovery model, only for read-only filegroups).</span></span>  
  
 <span data-ttu-id="9046b-106">데이터베이스가 온라인 상태인 데이터 복원을 *온라인 복원*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-106">Restoring data while the database is online is called an *online restore*.</span></span> <span data-ttu-id="9046b-107">데이터베이스는 주 파일 그룹이 온라인 상태일 때마다 하나 이상의 보조 파일 그룹이 오프라인 상태일 경우에도 온라인 상태로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-107">A database is considered to be online whenever the primary filegroup is online, even if one or more of its secondary filegroups are offline.</span></span> <span data-ttu-id="9046b-108">복구 모델에서는 데이터베이스가 온라인 상태일 때 오프라인인 파일을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-108">Under any recovery model, you can restore a file that is offline while the database is online.</span></span> <span data-ttu-id="9046b-109">전체 복구 모델에서도 데이터베이스가 온라인 상태일 때 페이지를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-109">Under the full recovery model, you can also restore pages while the database is online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9046b-110">온라인 복원은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise에서 자동으로 수행되며 사용자 동작이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-110">Online restore occurs automatically on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise and requires no user action.</span></span> <span data-ttu-id="9046b-111">온라인 복원을 사용하지 않으려면 복원을 시작하기 전에 데이터베이스를 오프라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-111">If you do not want to use online restore, you can take a database offline before you start a restore.</span></span> <span data-ttu-id="9046b-112">자세한 내용은 이 항목의 뒷부분에 나오는 [데이터베이스 또는 파일을 오프라인 상태로 만들기](#taking_db_or_file_offline)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9046b-112">For more information, see [Taking a Database or File Offline](#taking_db_or_file_offline), later in this topic.</span></span>  
  
 <span data-ttu-id="9046b-113">온라인 파일 복원을 수행하는 동안 복원된 파일과 해당 파일 그룹은 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-113">During an online file restore, any file being restored and its filegroup are offline.</span></span> <span data-ttu-id="9046b-114">온라인 복원을 시작할 때 이러한 모든 파일이 온라인 상태일 경우 첫 번째 복원 문은 해당 파일의 파일 그룹을 오프라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-114">If any of these files is online when an online restore starts, the first restore statement takes the filegroup of the file offline.</span></span> <span data-ttu-id="9046b-115">반대로 온라인 페이지 복원을 수행하는 동안에는 해당 페이지만 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-115">In contrast, during an online page restore, only the page is offline.</span></span>  
  
 <span data-ttu-id="9046b-116">모든 온라인 복원 시나리오에서는 다음과 같은 기본 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-116">Every online restore scenario involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="9046b-117">데이터를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-117">Restore the data.</span></span>  
  
2.  <span data-ttu-id="9046b-118">최종 로그 복원에 WITH RECOVERY를 사용하여 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-118">Restore the log by using WITH RECOVERY for the last log restore.</span></span> <span data-ttu-id="9046b-119">이러면 복원된 데이터가 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-119">This brings the restored data online.</span></span>  
  
 <span data-ttu-id="9046b-120">롤백에 필요한 데이터가 시작 시 오프라인 상태여서 커밋되지 않은 트랜잭션을 롤백할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-120">Occasionally, an uncommitted transaction cannot be rolled back because the data that is required by rollback is offline during startup.</span></span> <span data-ttu-id="9046b-121">이 경우에는 트랜잭션이 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-121">In this case, the transaction is deferred.</span></span> <span data-ttu-id="9046b-122">자세한 내용은 [지연된 트랜잭션&#40;SQL Server&#41;](deferred-transactions-sql-server.md)에서 존재하지 않는 파일 그룹을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9046b-123">데이터베이스가 현재 대량 로그 복구 모델을 사용하고 있을 경우 온라인 복원을 시작하기 전에 전체 복구 모델로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-123">If the database is currently using the bulk-logged recovery model, we recommend that you switch to the full recovery model before you start an online restore.</span></span> <span data-ttu-id="9046b-124">자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9046b-124">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9046b-125">서버에 연결된 여러 디바이스로 백업을 수행한 경우에는 온라인 복원 중에 같은 수의 디바이스를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-125">If the backups were taken with multiple devices that were attached to the server, the same number of devices must be available during an online restore.</span></span>  
  
## <a name="log-backups-for-online-restore"></a><span data-ttu-id="9046b-126">온라인 복원용 로그 백업</span><span class="sxs-lookup"><span data-stu-id="9046b-126">Log Backups for Online Restore</span></span>  
 <span data-ttu-id="9046b-127">온라인 복원에서 복구 지점은 복원되는 데이터가 오프라인 상태로 된 지점이거나 마지막으로 읽기 전용으로 된 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-127">In an online restore, the recovery point is the point when the data being restored was taken offline or made read-only for the last time.</span></span> <span data-ttu-id="9046b-128">이 복구 지점을 포함하여 이 지점까지의 트랜잭션 로그 백업은 모두 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-128">The transaction log backups leading up to and including this recovery point must all be available.</span></span> <span data-ttu-id="9046b-129">일반적으로 로그 백업은 파일을 복구한 후에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-129">Generally, a log backup is required after that point to cover the recovery point for the file.</span></span> <span data-ttu-id="9046b-130">단, 해당 데이터가 읽기 전용이 된 후에 수행된 데이터 백업에서 읽기 전용 데이터의 온라인 복원을 수행하는 중인 경우에는</span><span class="sxs-lookup"><span data-stu-id="9046b-130">The only exception is during an online restore of read-only data from a data backup that was taken after the data became read-only.</span></span> <span data-ttu-id="9046b-131">로그 백업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-131">In this case, you do not have to have a log backup.</span></span>  
  
 <span data-ttu-id="9046b-132">일반적으로 복원 시퀀스를 시작한 이후에도 데이터베이스가 온라인 상태이면 트랜잭션 로그 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-132">Generally, you may take transaction log backups while the database is online, even after the start of the restore sequence.</span></span> <span data-ttu-id="9046b-133">마지막 로그 백업의 시점은 복원된 파일의 속성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-133">The timing of the last log backup depends on the properties of the file being restored:</span></span>  
  
-   <span data-ttu-id="9046b-134">온라인 읽기 전용 파일의 경우 첫 번째 복원 시퀀스 전이나 중간에 복구에 필요한 마지막 로그 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-134">For an online read-only file, you can take the last log backup that is required for recovery before or during the first restore sequence.</span></span> <span data-ttu-id="9046b-135">읽기 전용 파일 그룹에서는 해당 파일 그룹이 읽기 전용이 된 이후에 데이터 또는 차등 백업을 수행한 경우 로그 백업이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-135">A read-only filegroup may not require log backups if a data or differential backup was taken after the filegroup became read-only.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9046b-136">위의 정보는 모든 오프라인 상태인 파일에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-136">The preceding information also applies to every offline file.</span></span>  
  
-   <span data-ttu-id="9046b-137">특별한 경우로 첫 번째 복원 문이 실행된 시점에서 온라인 상태였다가 해당 복원 문에 의해 자동으로 오프라인 상태가 된 읽기/쓰기 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-137">A special case exists for a read/write file that was online when the first restore statement was issued and that was then automatically taken offline by that restore statement.</span></span> <span data-ttu-id="9046b-138">이 경우 반드시 첫 번째 *복원 순서* (데이터를 복원, 롤포워드 및 복구하는 하나 이상의 RESTORE 문의 순서) 중에 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-138">In this case, you must take a log backup during the first *restore sequence* (the sequence of one or more RESTORE statements that restore, roll forward, and recover data).</span></span> <span data-ttu-id="9046b-139">일반적으로 이 로그 백업은 모든 전체 백업을 복원한 이후 그리고 데이터를 복구하기 이전에 발생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-139">Generally, this log backup must occur after you restore all the full backups and before you recover the data.</span></span> <span data-ttu-id="9046b-140">그러나 특정 파일 그룹에 대한 파일 백업이 여러 개인 경우 로그 백업의 최소 시점은 해당 파일 그룹이 오프라인 상태가 된 후입니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-140">However, if there are multiple file backups for a specific filegroup, the minimal point of log backup is the time after the filegroup is offline.</span></span> <span data-ttu-id="9046b-141">이러한 데이터 복원 후 로그 백업은 파일이 오프라인 상태가 된 지점을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-141">This post-data-restore log backup captures the point at which the file was taken offline.</span></span> <span data-ttu-id="9046b-142">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 온라인 복원에 온라인 로그를 사용할 수 없으므로 이러한 데이터 복원 후 로그 백업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-142">The post-data-restore log backup is necessary because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot use online log for an online restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9046b-143">복원 시퀀스 전에 파일을 수동으로 오프라인 상태로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-143">Alternatively, you can manually take the file offline before the restore sequence.</span></span> <span data-ttu-id="9046b-144">자세한 내용은 이 항목의 뒷부분에 나오는 "데이터베이스 또는 파일을 오프라인 상태로 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9046b-144">For more information, see "Taking a Database or File Offline" later in this topic.</span></span>  
  
##  <a name="taking-a-database-or-file-offline"></a><a name="taking_db_or_file_offline"></a> <span data-ttu-id="9046b-145">데이터베이스 또는 파일을 오프라인 상태로 만들기</span><span class="sxs-lookup"><span data-stu-id="9046b-145">Taking a Database or File Offline</span></span>  
 <span data-ttu-id="9046b-146">온라인 복원을 사용하지 않으려면 복원 시퀀스를 시작하기 전에 다음 방법 중 하나를 사용하여 데이터베이스를 오프라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-146">If you do not want to use online restore, you can take the database offline before you start the restore sequence by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="9046b-147">복구 모델에서 다음 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문을 사용하여 데이터베이스를 오프라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-147">Under any recovery model, you can take the database offline by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
     <span data-ttu-id="9046b-148">ALTER DATABASE *database_name* SET OFFLINE</span><span class="sxs-lookup"><span data-stu-id="9046b-148">ALTER DATABASE *database_name* SET OFFLINE</span></span>  
  
-   <span data-ttu-id="9046b-149">또는 전체 복구 모델에서 다음 [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) 문을 사용하여 데이터베이스를 복원 중인 상태로 설정하여 파일이나 페이지 복원을 강제로 오프라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-149">Alternatively, under the full recovery model, you can force a file or page restore to be offline, by using the following [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) statement put the database in to the restoring state:</span></span>  
  
     <span data-ttu-id="9046b-150">BACKUP LOG *database_name* WITH NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="9046b-150">BACKUP LOG *database_name* WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="9046b-151">데이터베이스가 오프라인 상태를 유지하면 모든 복원은 오프라인 복원이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-151">As long as a database remains offline, all restores are offline restores.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9046b-152">예</span><span class="sxs-lookup"><span data-stu-id="9046b-152">Examples</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9046b-153">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9046b-153">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
-   [<span data-ttu-id="9046b-154">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-154">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-155">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-155">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-156">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-156">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-157">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-157">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-158">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-158">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-159">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-159">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="9046b-160">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-160">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9046b-161">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9046b-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9046b-162">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-162">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="9046b-163">페이지 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-163">Restore Pages &#40;SQL Server&#41;</span></span>](restore-pages-sql-server.md)  
  
-   [<span data-ttu-id="9046b-164">suspect_pages 테이블 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-164">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)  
  
-   [<span data-ttu-id="9046b-165">데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-165">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
-   [<span data-ttu-id="9046b-166">존재하지 않는 파일 그룹 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-166">Remove Defunct Filegroups &#40;SQL Server&#41;</span></span>](remove-defunct-filegroups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="9046b-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9046b-167">See Also</span></span>  
 <span data-ttu-id="9046b-168">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9046b-168">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="9046b-169">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9046b-169">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="9046b-170">[페이지 복원&#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9046b-170">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="9046b-171">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9046b-171">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 [<span data-ttu-id="9046b-172">복원 및 복구 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9046b-172">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
