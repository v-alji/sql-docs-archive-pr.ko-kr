---
title: 데이터를 복원하지 않고 데이터베이스 복구(Transact-SQL ) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 04e4f78e51adb803bb65530c0b3b903aa7f76419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653473"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a><span data-ttu-id="dd157-102">데이터를 복원하지 않고 데이터베이스 복구(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dd157-102">Recover a Database Without Restoring Data (Transact-SQL)</span></span>
  <span data-ttu-id="dd157-103">일반적으로 데이터베이스가 복구되기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 있는 모든 데이터가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-103">Usually, all of the data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is restored before the database is recovered.</span></span> <span data-ttu-id="dd157-104">하지만 예를 들어 데이터베이스와 일치하는 읽기 전용 파일을 복원할 경우 복원 작업에서 백업을 실제로 복원하지 않고 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-104">However, a restore operation can recover a database without actually restoring a backup; for example, when recovering a read-only file that is consistent with the database.</span></span> <span data-ttu-id="dd157-105">이 작업을 *복구 전용 복원*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-105">This is referred to as a *recovery-only restore*.</span></span> <span data-ttu-id="dd157-106">오프라인 데이터가 데이터베이스와 이미 일치하고 사용 가능한 상태로만 만들면 되는 경우 복구 전용 복원 작업은 데이터베이스 복구를 완료하고 데이터를 온라인으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-106">When offline data is already consistent with the database and needs only to be made available, a recovery-only restore operation completes the recovery of the database and bring the data online.</span></span>  
  
 <span data-ttu-id="dd157-107">복구 전용 복원은 전체 데이터베이스 또는 하나 이상의 파일 또는 파일 그룹에 대해 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-107">A recovery-only restore can occur for a whole database or for one or more a files or filegroups.</span></span>  
  
## <a name="recovery-only-database-restore"></a><span data-ttu-id="dd157-108">복구 전용 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="dd157-108">Recovery-Only Database Restore</span></span>  
 <span data-ttu-id="dd157-109">복구 전용 데이터베이스 복원은 다음 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-109">A recovery-only database restore can be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="dd157-110">복원 시퀀스에서 마지막 백업을 복원할 때 데이터베이스를 복구하지 않았으며 데이터베이스를 지금 복구하여 온라인 상태로 전환하려는 경우</span><span class="sxs-lookup"><span data-stu-id="dd157-110">You did not recover the database when restoring the last backup in a restore sequence, and you now want to recover the database to bring it online.</span></span>  
  
-   <span data-ttu-id="dd157-111">데이터베이스가 대기 모드에 있고 다른 로그 백업을 적용하지 않고 데이터베이스를 업데이트할 수 있게 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="dd157-111">The database is in standby mode, and you want to make the database updatable without applying another log backup.</span></span>  
  
 <span data-ttu-id="dd157-112">복구 전용 데이터베이스 복원의 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-112">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only database restore is as follows:</span></span>  
  
 <span data-ttu-id="dd157-113">RESTORE DATABASE *database_name* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="dd157-113">RESTORE DATABASE *database_name* WITH RECOVERY</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd157-114">FROM **=** \<*backup_device>\* 절은 백업이 필요 없으므로 복구 전용 복원에 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-114">The FROM **=** \<*backup_device>\* clause is not used for recovery-only restores because no backup is necessary.</span></span>  
  
 <span data-ttu-id="dd157-115">**예제**</span><span class="sxs-lookup"><span data-stu-id="dd157-115">**Example**</span></span>  
  
 <span data-ttu-id="dd157-116">다음 예에서는 데이터를 복원하지 않고 복원 작업에서 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-116">The following example recovers the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in a restore operation without restoring data.</span></span>  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a><span data-ttu-id="dd157-117">복구 전용 파일 복원</span><span class="sxs-lookup"><span data-stu-id="dd157-117">Recovery-Only File Restore</span></span>  
 <span data-ttu-id="dd157-118">복구 전용 파일 복원은 다음 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-118">A recovery-only file restore can be useful in the following situation:</span></span>  
  
 <span data-ttu-id="dd157-119">데이터베이스가 증분 복원된 경우.</span><span class="sxs-lookup"><span data-stu-id="dd157-119">A database is restored piecemeal.</span></span> <span data-ttu-id="dd157-120">주 파일 그룹의 복원이 완료된 후 하나 이상의 복원되지 않은 파일이 새 데이터베이스 상태와 일치하는 경우입니다. 이는 이 파일이 읽기 전용이었기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-120">After restore of the primary filegroup is complete, one or more of the unrestored files are consistent with the new database state, perhaps because it has been read-only for some time.</span></span> <span data-ttu-id="dd157-121">이러한 파일은 복구만 하면 되며 따로 데이터를 복사할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-121">These files only have to be recovered; data copying is unnecessary.</span></span>  
  
 <span data-ttu-id="dd157-122">복구 전용 복원 작업에 따라 오프라인 상태인 파일 그룹의 데이터는 온라인 상태로 전환되지만 데이터 복사, 다시 실행 또는 실행 취소 단계는 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-122">A recovery-only restore operation brings the data in the offline filegroup online; no data-copy, redo, or undo phase occurs.</span></span> <span data-ttu-id="dd157-123">복원 단계에 대한 자세한 내용은 [복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd157-123">For information about the phases of restore, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="dd157-124">복구 전용 파일 복원의 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-124">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only file restore is:</span></span>  
  
 <span data-ttu-id="dd157-125">데이터베이스 *database_name* {FILE **=** _logical_file_name_ | 복원 FILEGROUP **=** _logical_filegroup_name_ } [ **,**... *n* ] WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="dd157-125">RESTORE DATABASE *database_name* { FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ }[ **,**...*n* ] WITH RECOVERY</span></span>  
  
 <span data-ttu-id="dd157-126">**예제**</span><span class="sxs-lookup"><span data-stu-id="dd157-126">**Example**</span></span>  
  
 <span data-ttu-id="dd157-127">다음 예에서는 `SalesGroup2`데이터베이스의 보조 파일 그룹 `Sales` 에 있는 파일의 복구 전용 파일 복원에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-127">The following example illustrates a recovery-only file restore of the files in a secondary filegroup, `SalesGroup2`, in the `Sales` database.</span></span> <span data-ttu-id="dd157-128">주 파일 그룹은 이미 증분 복원의 초기 단계로 복원되었으며 `SalesGroup2` 는 복원된 주 파일 그룹과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-128">The primary filegroup has already been restored as the initial step of a piecemeal restore, and `SalesGroup2` is consistent with the restored primary filegroup.</span></span> <span data-ttu-id="dd157-129">이 파일 그룹을 복구하고 파일 그룹을 온라인 상태로 만들려면 다음과 같은 단일 문만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dd157-129">Recovering this filegroup and bringing it online requires only a single statement.</span></span>  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a><span data-ttu-id="dd157-130">복구 전용 복원을 통한 증분 복원 시나리오 완료의 예</span><span class="sxs-lookup"><span data-stu-id="dd157-130">Examples of Completing a Piecemeal Restore Scenario with a Recovery-Only Restore</span></span>  
 <span data-ttu-id="dd157-131">**단순 복구 모델**</span><span class="sxs-lookup"><span data-stu-id="dd157-131">**Simple recovery model**</span></span>  
  
-   [<span data-ttu-id="dd157-132">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="dd157-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="dd157-133">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="dd157-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 <span data-ttu-id="dd157-134">**전체 복구 모델**</span><span class="sxs-lookup"><span data-stu-id="dd157-134">**Full recovery model**</span></span>  
  
-   [<span data-ttu-id="dd157-135">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="dd157-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="dd157-136">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="dd157-136">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a><span data-ttu-id="dd157-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd157-137">See Also</span></span>  
 <span data-ttu-id="dd157-138">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd157-138">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="dd157-139">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd157-139">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="dd157-140">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="dd157-140">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="dd157-141">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="dd157-141">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="dd157-142">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dd157-142">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
