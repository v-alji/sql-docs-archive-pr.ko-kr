---
title: 파일 복원(단순 복구 모델) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ed48f48f531e727de5d6e1403ef47f5399f874d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731760"
---
# <a name="file-restores-simple-recovery-model"></a><span data-ttu-id="86058-102">파일 복원(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="86058-102">File Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="86058-103">이 항목에서는 하나 이상의 읽기 전용 보조 파일 그룹이 있는 단순 모델 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="86058-103">This topic is relevant only for simple-model databases that contain at least one read-only secondary filegroup.</span></span>  
  
 <span data-ttu-id="86058-104">파일 복원의 목표는 전체 데이터베이스를 복원하지 않고 하나 이상의 손상된 파일을 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86058-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="86058-105">단순 복구 모델에서 파일 백업은 읽기 전용 파일에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-105">Under the simple recovery model, file backups are supported only for read-only files.</span></span> <span data-ttu-id="86058-106">데이터베이스 또는 부분 백업 복원 시 항상 주 파일 그룹 및 읽기/쓰기 보조 파일 그룹이 함께 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-106">The primary filegroup and read/write secondary filegroups are always restored together, by restoring a database or partial backup.</span></span>  
  
 <span data-ttu-id="86058-107">파일 복원 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86058-107">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="86058-108">오프라인 파일 복원</span><span class="sxs-lookup"><span data-stu-id="86058-108">Offline file restore</span></span>  
  
     <span data-ttu-id="86058-109">*오프라인 파일 복원*에서 손상된 파일 또는 파일 그룹이 복원되는 동안 데이터베이스는 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="86058-109">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="86058-110">복원 시퀀스의 마지막에 데이터베이스는 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-110">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="86058-111">모든 버전의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 는 오프라인 파일 복원을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-111">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="86058-112">온라인 파일 복원</span><span class="sxs-lookup"><span data-stu-id="86058-112">Online file restore</span></span>  
  
     <span data-ttu-id="86058-113">*온라인 파일 복원*의 경우 데이터베이스가 복원 시점에 온라인 상태이면 파일 복원 중에 온라인 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-113">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="86058-114">그러나 파일을 복원할 각 파일 그룹은 복원 작업 중에 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="86058-114">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="86058-115">오프라인 파일 그룹의 모든 파일이 복구되면 파일 그룹이 자동으로 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-115">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="86058-116">온라인 페이지 및 파일 복원 지원에 대한 자세한 내용은 [SQL Server 2014 버전에서 지원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86058-116">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="86058-117">온라인 복원에 대한 자세한 내용은 [온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86058-117">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="86058-118">파일 복원을 위해 데이터베이스를 오프라인 상태로 전환하려면 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 문: ALTER DATABASE *database_name* SET OFFLINE을 실행하여 복원 시퀀스를 시작하기 전에 데이터베이스 오프라인으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-118">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  

  
##  <a name="overview-of-file-and-filegroup-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="86058-119">단순 복구 모델의 파일 및 파일 그룹 복원 개요</span><span class="sxs-lookup"><span data-stu-id="86058-119">Overview of File and Filegroup Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="86058-120">파일 복원 시나리오는 다음과 같이 올바른 데이터를 복사, 롤포워드 및 복구하는 단일 복원 시퀀스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-120">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:</span></span>  
  
1.  <span data-ttu-id="86058-121">가장 최근의 파일 백업에서 각각의 손상된 파일을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-121">Restore each damaged file from its most recent file backup.</span></span>  
  
2.  <span data-ttu-id="86058-122">복원된 각 파일에 대한 가장 최근의 차등 파일 백업을 복원하고 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-122">Restore the most recent differential file backup for each restored file and recover the database.</span></span>  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a><span data-ttu-id="86058-123">파일 복원 시퀀스의 Transact-SQL 단계(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="86058-123">Transact-SQL Steps for File Restore Sequence (Simple Recovery Model)</span></span>  
 <span data-ttu-id="86058-124">이 섹션에서는 단순 파일 복원 시퀀스에 대한 필수 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86058-124">This section shows the essential [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a simple file-restore sequence.</span></span> <span data-ttu-id="86058-125">이 용도와 관련 없는 구문 및 세부 사항은 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-125">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="86058-126">복원 시퀀스는 두 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="86058-126">The restore sequence contains only two [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="86058-127">첫 번째 문은 WITH NORECOVERY를 사용하여 보조 파일인 `A`파일을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-127">The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY.</span></span> <span data-ttu-id="86058-128">두 번째 작업에서는 다른 백업 디바이스에서 WITH RECOVERY를 사용하여 `B` 및 `C` 파일을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="86058-128">The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:</span></span>  
  
1.  <span data-ttu-id="86058-129">RESTORE DATABASE *database* FILE **=** _name_of_file_A_</span><span class="sxs-lookup"><span data-stu-id="86058-129">RESTORE DATABASE *database* FILE **=**_name_of_file_A_</span></span>  
  
     <span data-ttu-id="86058-130">FROM *file_backup_of_file_A*</span><span class="sxs-lookup"><span data-stu-id="86058-130">FROM *file_backup_of_file_A*</span></span>  
  
     <span data-ttu-id="86058-131">WITH NORECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="86058-131">WITH NORECOVERY **;**</span></span>  
  
2.  <span data-ttu-id="86058-132">RESTORE DATABASE *database* FILE **=** _name_of_file_B_ **,** _name_of_file_C_</span><span class="sxs-lookup"><span data-stu-id="86058-132">RESTORE DATABASE *database* FILE **=**_name_of_file_B_**,**_name_of_file_C_</span></span>  
  
     <span data-ttu-id="86058-133">FROM *file_backup_of_files_B_and_C*</span><span class="sxs-lookup"><span data-stu-id="86058-133">FROM *file_backup_of_files_B_and_C*</span></span>  
  
     <span data-ttu-id="86058-134">WITH RECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="86058-134">WITH RECOVERY **;**</span></span>  
  
### <a name="examples"></a><span data-ttu-id="86058-135">예</span><span class="sxs-lookup"><span data-stu-id="86058-135">Examples</span></span>  
  
-   [<span data-ttu-id="86058-136">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-136">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="86058-137">예: 주 파일 그룹 및 다른 파일 그룹의 오프라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-137">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="86058-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="86058-138">Related Tasks</span></span>  
 <span data-ttu-id="86058-139">**파일과 파일 그룹을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="86058-139">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="86058-140">기존 파일에서 파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-140">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="86058-141">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-141">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="86058-142">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-142">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="86058-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="86058-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="86058-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86058-144">See Also</span></span>  
 <span data-ttu-id="86058-145">[백업 및 복원: 상호 운용성 및 공존성&#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86058-145">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="86058-146">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86058-146">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="86058-147">[전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86058-147">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="86058-148">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86058-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="86058-149">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="86058-149">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="86058-150">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="86058-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="86058-151">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="86058-151">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="86058-152">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="86058-152">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
