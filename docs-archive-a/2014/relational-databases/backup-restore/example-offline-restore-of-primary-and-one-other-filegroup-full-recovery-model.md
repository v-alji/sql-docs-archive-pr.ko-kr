---
title: '예: 주 파일 그룹 및 다른 파일 그룹의 오프 라인 복원 (전체 복구 모델) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f845927fdd74fba476139fccbf9a5fa112d434e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659987"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a><span data-ttu-id="c59e2-102">예제: 주 파일 그룹 및 다른 파일 그룹의 오프라인 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="c59e2-102">Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)</span></span>
  <span data-ttu-id="c59e2-103">이 항목에서는 전체 복구 모델에서 데이터베이스에 여러 개의 파일 그룹이 있는 경우와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-103">This topic is relevant only for databases under the full recovery model that contain multiple filegroups.</span></span>  
  
 <span data-ttu-id="c59e2-104">이 예에서 `adb` 라는 데이터베이스에 3개의 파일 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-104">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="c59e2-105">파일 그룹 `A` 및 `C` 는 읽기/쓰기가 가능하며 파일 그룹 `B` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-105">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="c59e2-106">주 파일 그룹과 파일 그룹 `B` 는 손상되지만 파일 그룹 `A` 와 `C` 는 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-106">The primary filegroup and filegroup `B` are damaged, but filegroups `A` and `C` are intact.</span></span> <span data-ttu-id="c59e2-107">재해가 발생하기 전에 모든 파일 그룹은 온라인 상태였습니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-107">Before the disaster, all the filegroups were online.</span></span>  
  
 <span data-ttu-id="c59e2-108">데이터베이스 관리자가 주 파일 그룹과 파일 그룹 `B`를 복원 및 복구하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-108">The database administrator decides to restore and recover the primary filegroup and filegroup `B`.</span></span> <span data-ttu-id="c59e2-109">데이터베이스에서 전체 복구 모델을 사용하고 있으므로 복원이 시작되기 전에 데이터베이스의 비상 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-109">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="c59e2-110">데이터베이스가 온라인 상태가 되면 파일 그룹 `A` 와 `C` 도 자동으로 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-110">When the database comes on line, Filegroups `A` and `C` are automatically brought online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c59e2-111">오프라인 복원 시퀀스는 읽기 전용 파일의 온라인 복원 시퀀스보다 단계 수가 적습니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-111">The offline restore sequence has fewer steps than an online restore of a read-only file.</span></span> <span data-ttu-id="c59e2-112">예를 보려면 [예제: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c59e2-112">For an example, see [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md).</span></span> <span data-ttu-id="c59e2-113">그러나 전체 데이터베이스는 시퀀스가 진행되는 동안 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-113">However, the whole database is offline for the duration of the sequence.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="c59e2-114">비상 로그 백업</span><span class="sxs-lookup"><span data-stu-id="c59e2-114">Tail-Log Backup</span></span>  
 <span data-ttu-id="c59e2-115">데이터베이스를 복원하기 전에 데이터베이스 관리자는 비상 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-115">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="c59e2-116">데이터베이스가 손상되었으므로 비상 로그 백업을 만들려면 NO_TRUNCATE 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-116">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="c59e2-117">비상 로그 백업은 다음 복원 시퀀스에서 마지막으로 적용되는 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-117">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="c59e2-118">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="c59e2-118">Restore Sequence</span></span>  
 <span data-ttu-id="c59e2-119">주 파일 그룹과 파일 그룹 `B`를 복원하기 위해 데이터베이스 관리자는 다음과 같이 PARTIAL 옵션이 없는 복원 시퀀스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-119">To restore the primary filegroup and filegroup `B`, the database administrator uses a restore sequence without the PARTIAL option, as follows:</span></span>  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 <span data-ttu-id="c59e2-120">복원되지 않은 파일은 자동으로 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-120">The files that are not restored are automatically brought online.</span></span> <span data-ttu-id="c59e2-121">이제 모든 파일 그룹이 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c59e2-121">All the filegroups are now online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c59e2-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c59e2-122">See Also</span></span>  
 <span data-ttu-id="c59e2-123">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c59e2-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="c59e2-124">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c59e2-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="c59e2-125">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="c59e2-125">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="c59e2-126">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c59e2-126">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="c59e2-127">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c59e2-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
