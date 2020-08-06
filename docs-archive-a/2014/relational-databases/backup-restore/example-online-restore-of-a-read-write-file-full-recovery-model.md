---
title: '예제: 읽기-쓰기 파일의 온라인 복원(전체 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5b99a3d97644c2a5f104173457f30fc5b3fd7188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647068"
---
# <a name="example-online-restore-of-a-read-write-file-full-recovery-model"></a><span data-ttu-id="ad2bc-102">예제: 읽기/쓰기 파일의 온라인 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="ad2bc-102">Example: Online Restore of a Read-Write File (Full Recovery Model)</span></span>
  <span data-ttu-id="ad2bc-103">이 항목에서는 여러 개의 파일 또는 파일 그룹이 있는 전체 복구 모델에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="ad2bc-104">이 예에서는 전체 복구 모델을 사용하는 `adb`라는 데이터베이스에 3개의 파일 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="ad2bc-105">파일 그룹 `A` 는 읽기/쓰기가 가능하고 파일 그룹 `B` 와 파일 그룹 `C` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="ad2bc-106">처음에는 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="ad2bc-107">파일 그룹 `a1` 에 손상된 파일 `A` 이 있으므로 데이터베이스 관리자는 데이터베이스를 온라인 상태로 유지하면서 이 파일을 복원하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-107">File `a1` in filegroup `A` appears to be damaged, and the database administrator decides to restore it while the database remains online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad2bc-108">단순 복구 모델에서는 온라인 상태에서 읽기/쓰기 데이터를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-108">Under the simple recovery model, online restore of read/write data is not allowed.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="ad2bc-109">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="ad2bc-109">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad2bc-110">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-110">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="ad2bc-111">파일 `a1`의 온라인 복원</span><span class="sxs-lookup"><span data-stu-id="ad2bc-111">Online restore of file `a1`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     <span data-ttu-id="ad2bc-112">이때 파일 a1은 RESTORING 상태이고 파일 그룹 A는 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-112">At this point, file a1 is in the RESTORING state, and filegroup A is offline.</span></span>  
  
2.  <span data-ttu-id="ad2bc-113">파일을 복원한 후 데이터베이스 관리자는 파일이 오프라인 상태로 전환된 시점이 캡처되도록 새 로그 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-113">After restoring the file, the database administrator takes a new log backup to make sure that the point at which the file went offline is captured.</span></span>  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  <span data-ttu-id="ad2bc-114">로그 백업의 온라인 복원</span><span class="sxs-lookup"><span data-stu-id="ad2bc-114">Online restore of log backups.</span></span>  
  
     <span data-ttu-id="ad2bc-115">관리자는 복원된 파일 백업 이후에 수행된 로그 백업부터 시작하여 가장 최근의 로그 백업(2단계에서 수행한*log_backup3*)까지 모든 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-115">The administrator restores all the log backups taken since the restored file backup, ending with the latest log backup (*log_backup3*, taken in step 2).</span></span> <span data-ttu-id="ad2bc-116">마지막 로그 백업이 복원되면 데이터베이스가 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-116">After the last backup is restored, the database is recovered.</span></span>  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     <span data-ttu-id="ad2bc-117">이제 파일 `a1` 은 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bc-117">File `a1` is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="ad2bc-118">추가 예</span><span class="sxs-lookup"><span data-stu-id="ad2bc-118">Additional Examples</span></span>  
  
-   [<span data-ttu-id="ad2bc-119">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-119">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ad2bc-120">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ad2bc-121">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-121">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="ad2bc-122">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-122">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="ad2bc-123">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="ad2bc-124">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-124">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad2bc-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad2bc-125">See Also</span></span>  
 <span data-ttu-id="ad2bc-126">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad2bc-126">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="ad2bc-127">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad2bc-127">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="ad2bc-128">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ad2bc-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ad2bc-129">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad2bc-129">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="ad2bc-130">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad2bc-130">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="ad2bc-131">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad2bc-131">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
