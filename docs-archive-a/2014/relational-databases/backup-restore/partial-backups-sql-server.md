---
title: 부분 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c03cf2fb4d3af6fe87459e881e26c48cfacc232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653475"
---
# <a name="partial-backups-sql-server"></a><span data-ttu-id="a4308-102">부분 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a4308-102">Partial Backups (SQL Server)</span></span>
  <span data-ttu-id="a4308-103">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복구 모델은 부분 백업을 지원하므로 이 항목에서는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="a4308-104">그러나 부분 백업은 하나 이상의 읽기 전용 파일 그룹을 포함하는 초대형 데이터베이스를 백업할 경우의 유연성 향상을 위해 단순 복구 모델에서 사용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-104">However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read-only filegroups.</span></span>  
  
 <span data-ttu-id="a4308-105">부분 백업은 읽기 전용 파일 그룹을 제외할 때마다 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-105">Partial backups are useful whenever you want to exclude read-only filegroups.</span></span> <span data-ttu-id="a4308-106">*부분 백업* 은 전체 데이터베이스 백업과 유사하지만 부분 백업에 모든 파일 그룹이 포함되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-106">A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups.</span></span> <span data-ttu-id="a4308-107">대신 읽기/쓰기 데이터베이스의 경우 부분 백업은 주 파일 그룹, 모든 읽기/쓰기 파일 그룹, 하나 이상의 읽기 전용 파일(선택 사항)의 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-107">Instead, for a read-write database, a partial backup contains the data in the primary filegroup, every read-write filegroup, and, optionally, one or more read-only files.</span></span> <span data-ttu-id="a4308-108">읽기 전용 데이터베이스의 부분 백업에는 주 파일 그룹만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-108">A partial backup of a read-only database contains only the primary filegroup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4308-109">부분 백업 후 읽기 전용 데이터베이스를 읽기/쓰기로 변경하는 경우 부분 백업에는 없는 읽기/쓰기 보조 파일 그룹이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-109">If a read-only database is changed to read/write after a partial backup, there might be read/write secondary filegroups that are not in the partial backup.</span></span> <span data-ttu-id="a4308-110">이 경우 차등 부분 백업을 시도하면 백업이 실패하며</span><span class="sxs-lookup"><span data-stu-id="a4308-110">In this case, if you try to take a differential partial backup, the backup fails.</span></span> <span data-ttu-id="a4308-111">다른 부분 백업을 수행해야만 데이터베이스의 차등 부분 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-111">Before you can take a differential partial backup of the database, you must take another partial backup.</span></span> <span data-ttu-id="a4308-112">새 부분 백업은 모든 읽기/쓰기 보조 파일 그룹을 포함하며 차등 부분 백업의 기반으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-112">The new partial backup contains every read/write secondary filegroup and can serve as the base for differential partial backups.</span></span>  
  
 <span data-ttu-id="a4308-113">읽기 전용 파일 그룹의 파일 백업을 부분 백업과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-113">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="a4308-114">파일 백업에 대한 자세한 내용은 [전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4308-114">For information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="a4308-115">부분 백업은 차등 부분 백업에 대해 *차등 기반* 으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-115">A partial backup can serve as the *differential base* for differential partial backups.</span></span> <span data-ttu-id="a4308-116">자세한 내용은 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4308-116">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a4308-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a4308-117">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4308-118">부분 백업은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 유지 관리 계획 마법사에서 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4308-118">Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the Maintenance Plan Wizard.</span></span>  
  
 <span data-ttu-id="a4308-119">**부분 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a4308-119">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="a4308-120">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)(READ_WRITE_FILEGROUPS, FILEGROUP 그룹 옵션, 필요한 경우)</span><span class="sxs-lookup"><span data-stu-id="a4308-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP option, if needed)</span></span>  
  
 <span data-ttu-id="a4308-121">**복원 시퀀스에서 부분 백업을 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="a4308-121">**To use a partial backup in a restore sequence**</span></span>  
  
-   [<span data-ttu-id="a4308-122">예: 데이터베이스의 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="a4308-122">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="a4308-123">예: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="a4308-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4308-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4308-124">See Also</span></span>  
 <span data-ttu-id="a4308-125">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a4308-125">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="a4308-126">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a4308-126">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="a4308-127">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4308-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
