---
title: 전체 파일 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backing up [SQL Server], files or filegroups
- backups [SQL Server], files or filegroups
- full recovery model [SQL Server], full file backups
- file backups [SQL Server], full
- files [SQL Server], backing up
- filegroups [SQL Server], backing up
- file backups [SQL Server]
ms.assetid: a716bf8d-0c5a-490d-aadd-597b3b0fac0c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e2e45dc68afa4d464aa3931075a1c1b3be792e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653483"
---
# <a name="full-file-backups-sql-server"></a><span data-ttu-id="a907c-102">전체 파일 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a907c-102">Full File Backups (SQL Server)</span></span>
  <span data-ttu-id="a907c-103">이 항목에서는 여러 개의 파일 및 파일 그룹을 포함하고 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="a907c-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스의 파일을 개별적으로 백업하고 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-104">The files in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database can be backed up and restored individually.</span></span> <span data-ttu-id="a907c-105">또한 각 구성 파일을 개별적으로 지정하는 대신 전체 파일 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-105">Also, you can specify a whole filegroup instead of specifying each constituent file individually.</span></span> <span data-ttu-id="a907c-106">이때 파일 그룹에 오프라인 상태인 파일이 있다면(예: 복원 중인 파일) 전체 파일 그룹이 오프라인 상태가 되고 이를 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-106">Note that if any file in a filegroup is offline (for example, because the file is being restored), the whole filegroup is offline and cannot be backed up.</span></span>  
  
 <span data-ttu-id="a907c-107">읽기 전용 파일 그룹의 파일 백업을 부분 백업과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-107">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="a907c-108">부분 백업은 모든 읽기/쓰기 파일 그룹과 필요에 따라 하나 이상의 읽기 전용 파일 그룹을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-108">Partial backups include all the read/write filegroups and, optionally, one or more read-only filegroups.</span></span> <span data-ttu-id="a907c-109">자세한 내용은 [부분 백업&#40;SQL Server&#41;](partial-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-109">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="a907c-110">파일 백업은 차등 파일 백업의 *차등 기반* 으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-110">A file backup can serve as the *differential base* for differential file backups.</span></span> <span data-ttu-id="a907c-111">자세한 내용은 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-111">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a907c-112">전체 파일 백업은 *차등 파일 백업*과 명시적으로 비교하는 경우를 제외하고 일반적으로 *파일 백업*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-112">Full file backups are typically called *file backups*, except when they are being explicitly compared with *differential file backups*.</span></span>  
  
 <span data-ttu-id="a907c-113">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="a907c-113">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="a907c-114">파일 백업의 이점</span><span class="sxs-lookup"><span data-stu-id="a907c-114">Benefits of File Backups</span></span>](#Benefits)  
  
-   [<span data-ttu-id="a907c-115">파일 백업의 단점</span><span class="sxs-lookup"><span data-stu-id="a907c-115">Disadvantages of File Backups</span></span>](#Disadvantages)  
  
-   [<span data-ttu-id="a907c-116">파일 백업 개요</span><span class="sxs-lookup"><span data-stu-id="a907c-116">Overview of File Backups</span></span>](#Overview)  
  
-   [<span data-ttu-id="a907c-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a907c-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-file-backups"></a><a name="Benefits"></a> <span data-ttu-id="a907c-118">파일 백업의 이점</span><span class="sxs-lookup"><span data-stu-id="a907c-118">Benefits of File Backups</span></span>  
 <span data-ttu-id="a907c-119">파일 백업은 데이터베이스 백업에 비해 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-119">File backups offer the following advantages over database backups:</span></span>  
  
-   <span data-ttu-id="a907c-120">파일 백업을 사용하면 데이터베이스의 나머지 부분을 복원하지 않고 손상된 파일만 복원할 수 있으므로 복구 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-120">Using file backups can increase the speed of recovery by letting you restore only damaged files, without restoring the rest of the database.</span></span>  
  
     <span data-ttu-id="a907c-121">예를 들어 데이터베이스가 서로 다른 디스크에 저장된 여러 개의 파일로 구성되어 있고 한 디스크에 오류가 있으면 오류가 있는 디스크의 파일만 복원하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-121">For example, if a database consists of several files that are located on different disks and one disk fails, only the file on the failed disk has to be restored.</span></span> <span data-ttu-id="a907c-122">손상된 파일을 빠르게 복구할 수 있으므로 전체 데이터베이스에 대해 복구할 때보다 더 빠르게 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-122">The damaged file can be quickly restored, and recovery is faster than it would be for an entire database.</span></span>  
  
-   <span data-ttu-id="a907c-123">파일 백업은 초대형 데이터베이스의 경우 관리가 힘든 전체 데이터베이스 백업에 비해 일정 예약 및 미디어 처리의 유연성이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-123">File backups increase flexibility in scheduling and media handling over full database backups, which for very large databases can become unmanageable.</span></span> <span data-ttu-id="a907c-124">파일 또는 파일 그룹 백업의 뛰어난 유연성은 다양한 업데이트 특성을 가진 데이터가 포함된 대형 데이터베이스에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-124">The increased flexibility of file or filegroup backups is also useful for large databases that contain data that has varying update characteristics.</span></span>  
  
##  <a name="disadvantages-of-file-backups"></a><a name="Disadvantages"></a> <span data-ttu-id="a907c-125">파일 백업의 단점</span><span class="sxs-lookup"><span data-stu-id="a907c-125">Disadvantages of File Backups</span></span>  
  
-   <span data-ttu-id="a907c-126">전체 데이터베이스 백업과 비교하여 파일 백업의 주요 단점은 관리가 더 복잡하다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-126">The primary disadvantage of file backups compared to full database backups is the additional administrative complexity.</span></span> <span data-ttu-id="a907c-127">이렇게 전체 백업을 유지 관리하고 추적하는 태스크는 많은 시간이 소모되므로 전체 데이터베이스 백업의 공간 요구 사항 문제보다 더욱 부담이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-127">Maintaining and keeping track of a complete set of these backups can be a time-consuming task that might outweigh the space requirements of full database backups.</span></span>  
  
-   <span data-ttu-id="a907c-128">미디어 실패가 발생했을 때 손상된 파일이 백업되지 않은 경우 전체 데이터베이스를 복구하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-128">A media failure can make a complete database unrecoverable if a damaged file lacks a backup.</span></span> <span data-ttu-id="a907c-129">따라서 완전한 파일 백업 세트를 유지 관리해야 하며 전체 복구 모델 및 대량 로그 복구 모델의 경우 첫 번째 전체 파일 백업과 마지막 전체 파일 백업 사이의 최소 간격을 포함하는 하나 이상의 로그 백업을 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-129">You must therefore maintain a complete set of file backups, and, for the full/bulk-logged recovery model, one or more log backups covering minimally the interval between the first full file backup and last full file backup.</span></span>  
  
##  <a name="overview-of-file-backups"></a><a name="Overview"></a> <span data-ttu-id="a907c-130">파일 백업 개요</span><span class="sxs-lookup"><span data-stu-id="a907c-130">Overview of File Backups</span></span>  
 <span data-ttu-id="a907c-131">전체 파일 백업은 하나 이상의 파일 또는 파일 그룹에 있는 모든 데이터를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-131">A full file backup backs up all the data in one or more files or filegroups.</span></span> <span data-ttu-id="a907c-132">기본적으로 파일 백업은 충분한 로그 레코드를 포함하여 백업 작업의 끝으로 파일을 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-132">By default, file backups contain enough log records to roll forward the file to the end of the backup operation.</span></span>  
  
 <span data-ttu-id="a907c-133">읽기 전용 파일이나 파일 그룹 백업은 모든 복구 모델에 대해 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-133">Backing up a read-only file or filegroup is the same for every recovery model.</span></span> <span data-ttu-id="a907c-134">전체 복구 모델에서 완전한 전체 파일 백업 세트를 모든 파일 백업을 포함하기에 충분한 로그 백업과 함께 사용하는 것은 전체 데이터베이스 백업을 수행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-134">Under the full recovery model, a complete set of full file backups, together with enough log backups to span all the file backups, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="a907c-135">한 번에 하나의 파일 백업 작업만 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-135">Only one file backup operation can occur at a time.</span></span> <span data-ttu-id="a907c-136">하나의 작업에서 여러 파일을 백업할 수 있지만 단일 파일만 복원해야 할 경우 이 작업으로 인해 복구 시간이 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-136">You can back up multiple files in one operation, but this might extend the recovery time if you only have to restore a single file.</span></span> <span data-ttu-id="a907c-137">이는 해당 파일을 찾기 위해 전체 백업을 읽기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-137">This is because to locate that file, the whole backup is read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a907c-138">개별 파일은 데이터베이스 백업에서 복원할 수도 있지만 데이터베이스 백업에서 파일을 찾아 복원하는 시간은 파일 백업에서보다 더 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-138">Individual files can be restored from a database backup; however, locating and restoring a file takes longer from a database backup than from a file backup.</span></span>  
  
### <a name="file-backups-and-the-simple-recovery-model"></a><span data-ttu-id="a907c-139">파일 백업 및 단순 복구 모델</span><span class="sxs-lookup"><span data-stu-id="a907c-139">File Backups and the Simple Recovery Model</span></span>  
 <span data-ttu-id="a907c-140">단순 복구 모델에서 읽기/쓰기 파일은 모두 함께 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-140">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="a907c-141">이렇게 하면 데이터베이스를 일정한 지정 시간으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-141">This makes sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="a907c-142">각 읽기/쓰기 파일 또는 파일 그룹을 개별적으로 지정하는 대신 READ_WRITE_FILEGROUPS 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-142">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="a907c-143">이 옵션은 데이터베이스의 모든 읽기/쓰기 파일 그룹을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-143">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="a907c-144">READ_WRITE_FILEGROUPS를 지정하여 만든 백업은 부분 백업이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-144">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a partial backup.</span></span> <span data-ttu-id="a907c-145">자세한 내용은 [부분 백업&#40;SQL Server&#41;](partial-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-145">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
### <a name="file-backups-and-the-full-recovery-model"></a><span data-ttu-id="a907c-146">파일 백업 및 전체 복구 모델</span><span class="sxs-lookup"><span data-stu-id="a907c-146">File Backups and the Full Recovery Model</span></span>  
 <span data-ttu-id="a907c-147">전체 복구 모델에서는 나머지 백업 전략에 관계없이 트랜잭션 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-147">Under the full recovery model, you must back up the transaction log, regardless of the rest of your backup strategy.</span></span> <span data-ttu-id="a907c-148">첫 번째 파일 백업에서 시작하여 모든 파일 백업을 수행할 수 있는 충분한 로그 백업과 완전한 전체 파일 백업 세트는 전체 데이터베이스 백업에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-148">A complete set of full file backups, together with enough log backups to span all the file backups from the start of the first file backup, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="a907c-149">파일 및 로그 백업만을 사용하는 데이터베이스 복원은 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-149">Restoring a database using just file and log backups can be complex.</span></span> <span data-ttu-id="a907c-150">따라서 가능한 경우 최상의 방법은 전체 데이터베이스 백업을 수행하고 첫 번째 파일 백업 이전에 로그 백업을 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-150">Therefore, if it is possible, it is a best practice to perform a full database backup and start the log backups before the first file backup.</span></span> <span data-ttu-id="a907c-151">다음 그림에서는 데이터베이스가 생성된 후(시간 t0) 즉시(시간 t1) 전체 데이터베이스 백업이 수행되는 전략을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-151">The following illustration shows a strategy in which a full database backup is taken (at time t1) soon after the database is created (at time t0).</span></span> <span data-ttu-id="a907c-152">이 첫 번째 데이터베이스 백업을 사용하여 트랜잭션 로그 백업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-152">This first database backup enables transaction log backups to start.</span></span> <span data-ttu-id="a907c-153">트랜잭션 로그 백업은 지정된 간격으로 수행되도록 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-153">Transaction log backups are scheduled to occur at set intervals.</span></span> <span data-ttu-id="a907c-154">파일 백업은 데이터베이스의 비즈니스 요구 사항에 가장 적합한 간격으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-154">File backups occur at whatever interval best meets the business requirements for the database.</span></span> <span data-ttu-id="a907c-155">이 그림에서는 한 번에 하나씩 백업되는 4개의 파일 그룹을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-155">This illustration shows each of the four filegroups being backed up one at a time.</span></span> <span data-ttu-id="a907c-156">백업되는 순서(A, C, B, A)는 데이터베이스의 비즈니스 요구 사항을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-156">The order in which they are backed up (A, C, B, A) reflects the business requirements of the database.</span></span>  
  
 <span data-ttu-id="a907c-157">![데이터베이스, 파일 및 로그 백업을 결합하는 전략](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "데이터베이스, 파일 및 로그 백업을 결합하는 전략")</span><span class="sxs-lookup"><span data-stu-id="a907c-157">![Strategy combining database, file, and log backups](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Strategy combining database, file, and log backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a907c-158">전체 복구 모델에서는 파일이 나머지 데이터베이스와 일치하도록 읽기/쓰기 파일 백업을 복원할 때 트랜잭션 로그를 롤포워드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-158">Under the full recovery model, you must roll forward the transaction log when restoring a read/write file backup to make sure that the file is consistent with the rest of the database.</span></span> <span data-ttu-id="a907c-159">여러 트랜잭션 로그 백업을 롤포워드하지 않으려면 차등 파일 백업을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-159">To avoid rolling forward a lot of transaction log backups, consider using differential file backups.</span></span> <span data-ttu-id="a907c-160">자세한 내용은 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a907c-160">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a907c-161">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a907c-161">Related Tasks</span></span>  
 <span data-ttu-id="a907c-162">**파일 또는 파일 그룹 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a907c-162">**To create a file or filegroup backup**</span></span>  
  
-   [<span data-ttu-id="a907c-163">파일 및 파일 그룹 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a907c-163">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="a907c-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="a907c-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a907c-165">유지 관리 계획 마법사는 파일 백업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a907c-165">File backups are not supported by the Maintenance Plan Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a907c-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a907c-166">See Also</span></span>  
 <span data-ttu-id="a907c-167">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a907c-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a907c-168">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-168">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="a907c-169">[백업 및 복원: 상호 운용성 및 공존성&#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-169">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="a907c-170">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-170">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="a907c-171">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-171">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="a907c-172">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-172">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="a907c-173">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a907c-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="a907c-174">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a907c-174">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
