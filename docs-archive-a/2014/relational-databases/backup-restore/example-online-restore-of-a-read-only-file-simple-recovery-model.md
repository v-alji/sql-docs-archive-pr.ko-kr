---
title: '예제: 읽기 전용 파일의 온라인 복원(단순 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d84c920a2cb40866ba106b4d30d8e24c4caea611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742324"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a><span data-ttu-id="53447-102">예제: 읽기 전용 파일의 온라인 복원(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="53447-102">Example: Online Restore of a Read-Only File (Simple Recovery Model)</span></span>
  <span data-ttu-id="53447-103">이 항목에서는 읽기 전용 파일 그룹이 있는 단순 복구 모델에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="53447-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span> <span data-ttu-id="53447-104">단순 복구 모델의 경우 파일이 마지막으로 읽기 전용이 된 후에 수행된 파일 백업이 존재하는 경우 읽기 전용 파일을 온라인으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53447-104">Under the simple recovery model, a read-only file can be restored online if a file backup exists that was taken since the file became read-only for the last time.</span></span>  
  
 <span data-ttu-id="53447-105">이 예에서 `adb` 라는 데이터베이스에 3개의 파일 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53447-105">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="53447-106">파일 그룹 `A` 는 읽기/쓰기가 가능하며 파일 그룹 `B` 와 `C` 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="53447-106">Filegroup `A` is read/write, and filegroups `B` and `C` are read-only.</span></span> <span data-ttu-id="53447-107">처음에는 모든 파일 그룹이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="53447-107">Initially, all of the filegroups are online.</span></span> <span data-ttu-id="53447-108">파일 그룹 `B`의 읽기 전용 파일인 `b1`을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53447-108">A read-only file in filegroup `B`, `b1`, has to be restored.</span></span> <span data-ttu-id="53447-109">데이터베이스 관리자는 파일이 읽기 전용이 된 후에 수행된 백업을 사용하여 파일을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53447-109">The database administrator can restore it by using a backup that was taken after the file became read-only.</span></span> <span data-ttu-id="53447-110">복원하는 동안 파일 그룹 `B` 는 오프라인 상태이지만 데이터베이스의 나머지 파일 그룹은 온라인 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53447-110">For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="53447-111">복원 시퀀스</span><span class="sxs-lookup"><span data-stu-id="53447-111">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53447-112">온라인 복원 시퀀스의 구문은 오프라인 복원 시퀀스의 구문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="53447-112">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="53447-113">데이터베이스 관리자는 다음 복원 시퀀스에 따라 파일을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53447-113">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 <span data-ttu-id="53447-114">이제 파일이 온라인입니다.</span><span class="sxs-lookup"><span data-stu-id="53447-114">The file is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="53447-115">추가 예</span><span class="sxs-lookup"><span data-stu-id="53447-115">Additional Examples</span></span>  
  
-   [<span data-ttu-id="53447-116">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-116">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="53447-117">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="53447-118">예: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="53447-119">예: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="53447-120">예: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="53447-121">예: 읽기 전용 파일의 온라인 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-121">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="53447-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53447-122">See Also</span></span>  
 <span data-ttu-id="53447-123">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="53447-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="53447-124">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="53447-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="53447-125">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="53447-125">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="53447-126">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="53447-126">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="53447-127">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="53447-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
