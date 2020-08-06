---
title: '예제: 데이터베이스의 증분 복원(전체 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfccccdbdc0c4fb3b189ee0a9fa3aeaf426578b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735375"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a><span data-ttu-id="3c400-102">예제: 데이터베이스의 증분 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="3c400-102">Example: Piecemeal Restore of Database (Full Recovery Model)</span></span>
  <span data-ttu-id="3c400-103">증분 복원 시퀀스는 주 파일 그룹에서 시작하여 모든 읽기/쓰기가 가능한 모든 보조 파일 그룹의 순서로 파일 그룹 수준에서 데이터베이스를 복원하고 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read-write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="3c400-104">이 예에서 `adb` 데이터베이스는 재해 발생 후 새 컴퓨터에 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="3c400-105">데이터베이스에서 전체 복구 모델을 사용하고 있으므로 복원이 시작되기 전에 데이터베이스의 비상 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-105">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="3c400-106">재해가 발생하기 전에 모든 파일 그룹은 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="3c400-107">파일 그룹 `B` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-107">Filegroup `B` is read-only.</span></span> <span data-ttu-id="3c400-108">모든 보조 파일 그룹이 복원되어야 합니다. 단, 복원은 `A` (가장 중요), `C`, `B`와 같은 중요도 순으로 이루어져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-108">All of the secondary filegroups must be restored, but they are restored in order of importance: `A` (highest), `C`, and lastly `B`.</span></span> <span data-ttu-id="3c400-109">이 예에서는 비상 로그 백업을 포함하여 4개의 로그 백업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-109">In this example, there are four log backups, including the tail-log backup.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="3c400-110">비상 로그 백업</span><span class="sxs-lookup"><span data-stu-id="3c400-110">Tail-Log Backup</span></span>  
 <span data-ttu-id="3c400-111">데이터베이스를 복원하기 전에 데이터베이스 관리자는 비상 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-111">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="3c400-112">데이터베이스가 손상되었으므로 비상 로그 백업을 만들려면 NO_TRUNCATE 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-112">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="3c400-113">비상 로그 백업은 다음 복원 시퀀스에서 마지막으로 적용되는 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-113">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="3c400-114">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="3c400-114">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c400-115">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-115">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="3c400-116">주 파일 그룹과 보조 파일 그룹 `A`를 부분 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-116">Partial restore of the primary and secondary filegroup `A`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  <span data-ttu-id="3c400-117">파일 그룹 `C`를 온라인 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-117">Online restore of filegroup `C`.</span></span>  
  
     <span data-ttu-id="3c400-118">이때 주 파일 그룹과 보조 파일 그룹 `A` 는 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-118">At this point, the primary filegroup and secondary filegroup `A` are online.</span></span> <span data-ttu-id="3c400-119">파일 그룹 `B` 와 `C` 의 모든 파일은 복구가 보류된 상태이며 파일 그룹은 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-119">All the files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
     <span data-ttu-id="3c400-120">1단계에서 마지막 `RESTORE LOG` 문의 메시지는 파일 그룹 `C` 를 사용할 수 없어 이 파일 그룹에 관련된 트랜잭션 롤백이 지연되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-120">Messages from the last `RESTORE LOG` statement in step 1 indicate that rollback of transactions that involve filegroup `C` was deferred, because this filegroup is not available.</span></span> <span data-ttu-id="3c400-121">일반적인 작업은 계속할 수 있지만 이러한 트랜잭션에 의해 잠금이 유지되며 롤백이 완료되기 전에는 로그 잘림이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-121">Regular operations can continue, but locks are held by these transactions and log truncation will not occur until the rollback can complete.</span></span>  
  
     <span data-ttu-id="3c400-122">두 번째 복원 시퀀스에서 데이터베이스 관리자는 파일 그룹 `C`를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-122">In the second restore sequence, the database administrator restores filegroup `C`:</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="3c400-123">이 시점에서 주 파일 그룹 및 파일 그룹 `A` 와 `C` 가 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-123">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="3c400-124">파일 그룹 `B` 의 파일은 복구가 보류된 상태이며 파일 그룹은 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-124">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span> <span data-ttu-id="3c400-125">지연된 트랜잭션이 해결되고 로그 잘림이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-125">Deferred transactions have been resolved, and log truncation occurs.</span></span>  
  
3.  <span data-ttu-id="3c400-126">파일 그룹 `B`를 온라인 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-126">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="3c400-127">3번째 복원 시퀀스에서 데이터베이스 관리자는 파일 그룹 `B`를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-127">In the third restore sequence, the database administrator restores filegroup `B`.</span></span> <span data-ttu-id="3c400-128">파일 그룹 `B` 는 파일 그룹이 읽기 전용이 된 후 백업했으므로 복구 중에 롤포워드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-128">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, it does not have to be rolled forward during recovery.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     <span data-ttu-id="3c400-129">이제 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="3c400-129">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="3c400-130">추가 예</span><span class="sxs-lookup"><span data-stu-id="3c400-130">Additional Examples</span></span>  
  
-   [<span data-ttu-id="3c400-131">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-131">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="3c400-132">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-132">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="3c400-133">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-133">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="3c400-134">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-134">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="3c400-135">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-135">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="3c400-136">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-136">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c400-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c400-137">See Also</span></span>  
 <span data-ttu-id="3c400-138">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3c400-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3c400-139">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c400-139">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="3c400-140">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c400-140">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="3c400-141">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3c400-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="3c400-142">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3c400-142">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
