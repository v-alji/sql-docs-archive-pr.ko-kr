---
title: '예제: 일부 파일 그룹만 증분 복원(전체 복구 모델) | Microsoft 문서'
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
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b3cb1a5ea33a5016c99fdf1f5a7f4e892c045b59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742319"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a><span data-ttu-id="5be70-102">예제: 일부 파일 그룹만 증분 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="5be70-102">Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)</span></span>
  <span data-ttu-id="5be70-103">이 항목에서는 여러 개의 파일 또는 파일 그룹이 있는 전체 복구 모델에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="5be70-104">증분 복원 시퀀스는 주 파일 그룹에서 시작하여 모든 읽기/쓰기 파일 그룹, 보조 파일 그룹의 순서로 파일 그룹 수준에서 데이터베이스를 복원하고 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="5be70-105">이 예에서는 전체 복구 모델을 사용하는 `adb`라는 데이터베이스에 3개의 파일 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-105">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="5be70-106">파일 그룹 `A` 는 읽기/쓰기가 가능하고 파일 그룹 `B` 와 파일 그룹 `C` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="5be70-107">처음에는 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="5be70-108">데이터베이스 `B` 의 주 파일 그룹 및 파일 그룹 `adb` 가 손상된 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-108">The primary and filegroup `B` of database `adb` appear to be damaged.</span></span> <span data-ttu-id="5be70-109">주 파일 그룹은 크기가 작으므로 빠르게 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-109">The primary filegroup is fairly small and can be restored quickly.</span></span> <span data-ttu-id="5be70-110">데이터베이스 관리자는 증분 복원 시퀀스를 사용하여 이들을 복원하기로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-110">The database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="5be70-111">우선 주 파일 그룹과 다음 트랜잭션 로그를 복원하고 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-111">First, the primary filegroup and the subsequent transaction logs are restored the database is recovered.</span></span>  
  
 <span data-ttu-id="5be70-112">손상되지 않은 파일 그룹 `A` 와 `C` 에는 중요한 데이터가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-112">The intact filegroups `A` and `C` contain critical data.</span></span> <span data-ttu-id="5be70-113">그러므로 가능한 빨리 온라인 상태로 만들기 위해 다음으로 이들을 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-113">Therefore, they will be recovered next to bring them online as quickly as possible.</span></span> <span data-ttu-id="5be70-114">마지막으로 손상된 보조 파일 그룹 `B`를 복원하고 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-114">Finally, the damaged secondary filegroup, `B`, is restored and recovered.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="5be70-115">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="5be70-115">Restore Sequences:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5be70-116">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-116">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="5be70-117">데이터베이스 `adb`의 비상 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-117">Create a tail log backup of database `adb`.</span></span> <span data-ttu-id="5be70-118">이 단계는 데이터베이스 복구 지점을 사용하여 손상되지 않은 파일 그룹 `A` 와 `C` 를 최신 상태로 유지하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-118">This step is essential to make the intact filegroups `A` and `C` current with the recovery point of the database.</span></span>  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  <span data-ttu-id="5be70-119">주 파일 그룹을 부분 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-119">Partial restore of the primary filegroup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5be70-120">이 시점에서 주 파일 그룹은 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-120">At this point the primary is online.</span></span> <span data-ttu-id="5be70-121">파일 그룹 `A`, `B`및 `C` 의 파일은 복구 보류 상태이고 파일 그룹은 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-121">Files in filegroups `A`, `B`, and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
3.  <span data-ttu-id="5be70-122">파일 그룹 `A` 및 `C`를 온라인 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-122">Online restore of filegroups `A` and `C`.</span></span>  
  
     <span data-ttu-id="5be70-123">데이터가 손상되지 않았으므로 이 파일 그룹을 백업에서 복원할 필요는 없지만 복구하여 온라인 상태로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-123">Because their data is undamaged, these filegroups do not have to be restored from a backup, but they do have to be recovered to bring them online.</span></span>  
  
     <span data-ttu-id="5be70-124">데이터베이스 관리자가 `A` 와 `C` 를 즉시 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-124">The database administrator recovers `A` and `C` immediately.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5be70-125">이 시점에서 주 파일 그룹 및 파일 그룹 `A` 와 `C` 가 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-125">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="5be70-126">파일 그룹 `B` 의 파일은 복구가 보류된 상태이며 파일 그룹은 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-126">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span>  
  
4.  <span data-ttu-id="5be70-127">파일 그룹 `B`를 온라인 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-127">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="5be70-128">파일 그룹 `B` 의 파일은 이후 언제든지 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-128">Files in filegroup `B` are restored any time thereafter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5be70-129">파일 그룹 `B` 는 파일 그룹이 읽기 전용이 된 후 백업했으므로 이러한 파일을 롤포워드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-129">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, these files do not have to be rolled forward.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5be70-130">이제 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="5be70-130">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="5be70-131">추가 예</span><span class="sxs-lookup"><span data-stu-id="5be70-131">Additional Examples</span></span>  
  
-   [<span data-ttu-id="5be70-132">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5be70-133">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5be70-134">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-134">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5be70-135">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="5be70-136">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-136">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="5be70-137">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-137">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="5be70-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5be70-138">See Also</span></span>  
 <span data-ttu-id="5be70-139">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5be70-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="5be70-140">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5be70-140">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="5be70-141">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5be70-141">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="5be70-142">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5be70-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="5be70-143">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5be70-143">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
