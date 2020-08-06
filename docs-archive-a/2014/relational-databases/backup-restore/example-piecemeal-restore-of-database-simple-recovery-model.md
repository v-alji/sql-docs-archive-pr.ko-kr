---
title: '예제: 데이터베이스의 증분 복원(단순 복구 모델) | Microsoft 문서'
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
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69de84fa2ff3a853eb9926549ad4859d2f1ae38e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735372"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a><span data-ttu-id="7827e-102">예제: 데이터베이스의 증분 복원(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="7827e-102">Example: Piecemeal Restore of Database (Simple Recovery Model)</span></span>
  <span data-ttu-id="7827e-103">증분 복원 시퀀스는 주 파일 그룹에서 시작하여 모든 읽기/쓰기 파일 그룹, 보조 파일 그룹의 순서로 파일 그룹 수준에서 데이터베이스를 복원하고 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="7827e-104">이 예에서 `adb` 데이터베이스는 재해 발생 후 새 컴퓨터에 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="7827e-105">데이터베이스는 단순 복구 모델을 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-105">The database is using the simple recovery model.</span></span> <span data-ttu-id="7827e-106">재해가 발생하기 전에 모든 파일 그룹은 온라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="7827e-107">파일 그룹 `A` 및 `C` 는 읽기/쓰기가 가능하며 파일 그룹 `B` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-107">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="7827e-108">가장 최근의 부분 백업 이전에 파일 그룹 `B` 는 읽기 전용 파일이 되었으며 주 파일 그룹과 읽기/쓰기가 가능한 보조 파일 그룹인 `A` 와 `C`를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-108">Filegroup `B` became read-only before the most recent partial backup, which contains the primary filegroup and the read/write secondary filegroups, `A` and `C`.</span></span> <span data-ttu-id="7827e-109">파일 그룹 `B` 가 읽기 전용 파일이 된 후에 파일 그룹 `B` 의 별도 파일 백업이 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-109">After filegroup `B` became read-only, a separate file backup of filegroup `B` was taken.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="7827e-110">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="7827e-110">Restore Sequences</span></span>  
  
1.  <span data-ttu-id="7827e-111">주 파일 그룹과 파일 그룹 `A` 및 `C`를 부분 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-111">Partial restore of the primary and filegroups `A` and `C`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     <span data-ttu-id="7827e-112">이 시점에서 주 파일 그룹과 파일 그룹 `A` 와 `C` 가 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-112">At this point, the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="7827e-113">파일 그룹 `B` 의 모든 파일은 복구 보류 상태이고 이 파일 그룹은 오프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-113">All files in filegroup `B` are recovery pending, and the filegroup is offline.</span></span>  
  
2.  <span data-ttu-id="7827e-114">파일 그룹 `B`를 온라인 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-114">Online restore of filegroup `B`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     <span data-ttu-id="7827e-115">이제 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="7827e-115">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="7827e-116">추가 예</span><span class="sxs-lookup"><span data-stu-id="7827e-116">Additional Examples</span></span>  
  
-   [<span data-ttu-id="7827e-117">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="7827e-118">예: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-118">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="7827e-119">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-119">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="7827e-120">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="7827e-121">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-121">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="7827e-122">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-122">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="7827e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7827e-123">See Also</span></span>  
 <span data-ttu-id="7827e-124">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7827e-124">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="7827e-125">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7827e-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="7827e-126">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7827e-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="7827e-127">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7827e-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
