---
title: '예제: 일부 파일 그룹만 증분 복원(단순 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8254ac96a269b6fb433759e5a649bf9df1b7feac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742316"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model"></a><span data-ttu-id="be3b8-102">예제: 일부 파일 그룹만 증분 복원(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="be3b8-102">Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)</span></span>
  <span data-ttu-id="be3b8-103">이 항목에서는 읽기 전용 파일 그룹이 있는 단순 복구 모델에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span>  
  
 <span data-ttu-id="be3b8-104">증분 복원 시퀀스는 주 파일 그룹에서 시작하여 모든 읽기/쓰기 파일 그룹, 보조 파일 그룹의 순서로 파일 그룹 수준에서 데이터베이스를 복원하고 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="be3b8-105">이 예에서는 단순 복구 모델을 사용하는 `adb`라는 데이터베이스에 3개의 파일 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-105">In this example, a database named `adb`, which uses the simple recovery model, contains three filegroups.</span></span> <span data-ttu-id="be3b8-106">파일 그룹 `A` 는 읽기/쓰기가 가능하고 파일 그룹 `B` 와 파일 그룹 `C` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="be3b8-107">처음에는 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="be3b8-108">`B` 데이터베이스의 주 파일 그룹 및 파일 그룹 `adb` 가 손상된 것으로 나타나자 데이터베이스 관리자는 증분 복원 시퀀스를 사용하여 이를 복원하기로 합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-108">The primary and filegroup `B` of database `adb` appear to be damaged; therefore, the database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="be3b8-109">단순 복구 모델에서는 읽기/쓰기가 가능한 모든 파일 그룹을 같은 부분 백업에서 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-109">Under the simple recovery model, all read/write filegroups must be restored from the same partial backup.</span></span> <span data-ttu-id="be3b8-110">파일 그룹 `A` 는 손상되지 않았지만 데이터베이스가 마지막 부분 백업 끝에서 정의된 지정 시간으로 복원되어 일관성을 유지할 수 있도록 주 파일 그룹으로 복원되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-110">Although filegroup `A` is intact, it must be restored with the primary filegroup to make sure that they are consistent (the database will be restored to the point in time defined by the end of the last partial backup).</span></span> <span data-ttu-id="be3b8-111">파일 그룹 `C` 는 손상되지 않았지만 온라인 상태로 만들려면 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-111">Filegroup `C` is intact, but it must be recovered to bring it online.</span></span> <span data-ttu-id="be3b8-112">파일 그룹 `B`는 손상되었지만 포함된 데이터는 파일 그룹 `C`의 데이터보다 중요성이 낮습니다. 따라서 파일 그룹 `B` 를 마지막에 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-112">Filegroup `B`, although damaged, contains less critical data than Filegroup `C`; therefore, `B` will be restored last.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="be3b8-113">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="be3b8-113">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be3b8-114">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-114">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="be3b8-115">주 파일 그룹 및 파일 그룹 `A` 를 부분 백업에서 부분 복원</span><span class="sxs-lookup"><span data-stu-id="be3b8-115">Partial restore of the primary and filegroup `A` from a partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     <span data-ttu-id="be3b8-116">이 시점에서 주 파일 그룹과 파일 그룹 `A` 가 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-116">At this point the primary filegroup and filegroup `A` are online.</span></span> <span data-ttu-id="be3b8-117">파일 그룹 `B` 와 `C` 의 파일 복구는 보류 중이며 파일 그룹은 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-117">Files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
2.  <span data-ttu-id="be3b8-118">파일 그룹 `C`의 온라인 복구</span><span class="sxs-lookup"><span data-stu-id="be3b8-118">Online recovery of filegroup `C`.</span></span>  
  
     <span data-ttu-id="be3b8-119">파일 그룹 `C` 는 앞서 복원된 부분 백업이 파일 그룹 `C` 가 읽기 전용이 된 이후에 만든 것이기 때문에 복원 시 데이터베이스를 이전 상태로 만드는 경우에도 일관성이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-119">Filegroup `C` is consistent because the partial backup that was restored above was taken after filegroup `C` became read-only, although the database was taken back in time by the restore.</span></span> <span data-ttu-id="be3b8-120">데이터베이스 관리자는 파일 그룹 `C`를 복원하지 않고 복구하여 온라인 상태로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-120">The database administrator recovers the filegroup `C`, without restoring it, to bring it online.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="be3b8-121">이 시점에서 주 파일 그룹 및 파일 그룹 `A` 와 `C` 가 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-121">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="be3b8-122">filegroupB의 파일은 해당 파일 그룹이 오프라인 상태이므로 복구 보류 중 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-122">Files in filegroupB remain recovery pending, with the filegroup offline.</span></span>  
  
3.  <span data-ttu-id="be3b8-123">파일 그룹 `B.`</span><span class="sxs-lookup"><span data-stu-id="be3b8-123">Online restore of filegroup `B.`</span></span>  
  
     <span data-ttu-id="be3b8-124">파일 그룹 `B` 의 파일은 반드시 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-124">Files in filegroup `B` must be restored.</span></span> <span data-ttu-id="be3b8-125">데이터베이스 관리자는 파일 그룹 `B` 가 읽기 전용이 된 후와 부분 백업 전에 만든 백업으로 파일 그룹 `B` 를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-125">The database administrator restores the backup of filegroup `B` taken after filegroup `B` became read-only and before the partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     <span data-ttu-id="be3b8-126">이제 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="be3b8-126">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="be3b8-127">추가 예</span><span class="sxs-lookup"><span data-stu-id="be3b8-127">Additional Examples</span></span>  
  
-   [<span data-ttu-id="be3b8-128">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-128">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="be3b8-129">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-129">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="be3b8-130">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-130">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="be3b8-131">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-131">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="be3b8-132">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-132">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="be3b8-133">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-133">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="be3b8-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be3b8-134">See Also</span></span>  
 <span data-ttu-id="be3b8-135">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be3b8-135">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="be3b8-136">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="be3b8-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="be3b8-137">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="be3b8-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="be3b8-138">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="be3b8-138">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
