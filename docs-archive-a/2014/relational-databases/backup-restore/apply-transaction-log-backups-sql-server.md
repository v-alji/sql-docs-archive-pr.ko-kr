---
title: 트랜잭션 로그 백업 적용(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c91106f8ca6f15539b4103220860143882c3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650138"
---
# <a name="apply-transaction-log-backups-sql-server"></a><span data-ttu-id="4730b-102">트랜잭션 로그 백업 적용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4730b-102">Apply Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="4730b-103">이 항목에서는 전체 복구 모델 또는 대량 로그 복구 모델과 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-103">The topic is relevant only for the full recovery model or bulk-logged recovery model.</span></span>  
  
 <span data-ttu-id="4730b-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 복원의 일부로 수행되는 트랜잭션 로그 백업 적용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-104">This topic describes applying transaction log backups as part of restoring a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="4730b-105">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="4730b-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="4730b-106">트랜잭션 로그 백업 복원에 대 한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="4730b-106">Requirements for Restoring Transaction Log Backups</span></span>](#Requirements)  
  
-   [<span data-ttu-id="4730b-107">복구 및 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4730b-107">Recovery and Transaction Logs</span></span>](#RecoveryAndTlogs)  
  
-   [<span data-ttu-id="4730b-108">로그 백업을 사용하여 오류 지점까지 복원</span><span class="sxs-lookup"><span data-stu-id="4730b-108">Using Log Backups to Restore to the Point of Failure</span></span>](#PITrestore)  
  
-   [<span data-ttu-id="4730b-109">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4730b-109">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a><span data-ttu-id="4730b-110">트랜잭션 로그 백업 복원에 대 한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="4730b-110">Requirements for Restoring Transaction Log Backups</span></span>  
 <span data-ttu-id="4730b-111">트랜잭션 로그 백업을 적용하려면 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-111">To apply a transaction log backup, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="4730b-112">**복원 시퀀스를 위한 충분한 로그 백업:** 복원 순서를 완료하려면 백업된 로그 레코드가 충분히 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-112">**Enough Log Backups for a Restore Sequence :** You must have enough log records backed up to complete a restore sequence.</span></span> <span data-ttu-id="4730b-113">복원 시퀀스를 시작하려면 필요한 로그 백업(필요한 경우 [비상 로그 백업](tail-log-backups-sql-server.md) 을 포함)을 반드시 확보해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-113">The necessary log backups, including the [tail-log backup](tail-log-backups-sql-server.md) where required, must be available before the start of the restore sequence.</span></span>  
  
-   <span data-ttu-id="4730b-114">**올바른 복원 순서:**  바로 이전의 전체 데이터베이스 백업 또는 차등 데이터베이스 백업을 먼저 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-114">**Correct restore order:**  The immediately previous full database backup or differential database backup must be restored first.</span></span> <span data-ttu-id="4730b-115">그런 후 전체 또는 차등 데이터베이스 백업 후에 생성된 모든 트랜잭션 로그를 시간순으로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-115">Then, all transaction logs that are created after that full or differential database backup must be restored in chronological order.</span></span> <span data-ttu-id="4730b-116">이 로그 체인의 트랜잭션 로그 백업이 손실되거나 손상된 경우 손실된 트랜잭션 로그 이전의 트랜잭션 로그만 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-116">If a transaction log backup in this log chain is lost or damaged, you can restore only transaction logs before the missing transaction log.</span></span>  
  
-   <span data-ttu-id="4730b-117">**아직 복구되지 않은 데이터베이스:**  마지막 트랜잭션 로그가 적용될 때까지 데이터베이스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-117">**Database not yet recovered:**  The database cannot be recovered until after the final transaction log has been applied.</span></span> <span data-ttu-id="4730b-118">로그 체인이 끝나기 이전의 중간 트랜잭션 로그 백업 중 하나를 복원한 후 데이터베이스를 복구할 경우 해당 시점 이후의 데이터베이스를 복원하려면 전체 데이터베이스 백업부터 시작하여 전체 복원 시퀀스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-118">If you recover the database after restoring one of the intermediate transaction log backups, that before the end of the log chain, you cannot restore the database past that point without restarting the complete restore sequence, starting with the full database backup.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="4730b-119">최선의 방법은 모든 로그 백업을 복원하는 것입니다(RESTORE LOG *database_name* WITH NORECOVERY).</span><span class="sxs-lookup"><span data-stu-id="4730b-119">A best practice is to restore all the log backups (RESTORE LOG *database_name* WITH NORECOVERY).</span></span> <span data-ttu-id="4730b-120">그런 후 마지막 로그 백업을 복원한 후 데이터베이스를 별도의 작업으로 복구합니다(RESTORE DATABASE *database_name* WITH RECOVERY).</span><span class="sxs-lookup"><span data-stu-id="4730b-120">Then, after restoring the last log backup, recover the database in a separate operation (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span>  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a><span data-ttu-id="4730b-121">복구 및 트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="4730b-121">Recovery and Transaction Logs</span></span>  
 <span data-ttu-id="4730b-122">복원 작업을 완료하고 데이터베이스를 복구할 때 완료되지 않은 트랜잭션은 모두 롤백되는데</span><span class="sxs-lookup"><span data-stu-id="4730b-122">When you finish the restore operation and recover the database, recovery rolls back all incomplete transactions.</span></span> <span data-ttu-id="4730b-123">이것을 *실행 취소 단계*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-123">This is known as the *undo phase*.</span></span> <span data-ttu-id="4730b-124">롤백은 데이터베이스의 무결성을 복원하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-124">Rolling back is required to restore the integrity of the database.</span></span> <span data-ttu-id="4730b-125">롤백 후 데이터베이스는 온라인 상태가 되고 트랜잭션 로그 백업이 더 이상 데이터베이스에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-125">After rollback, the database goes online, and no more transaction log backups can be applied to the database.</span></span>  
  
 <span data-ttu-id="4730b-126">예를 들어 일련의 트랜잭션 로그 백업은 장기 실행 트랜잭션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-126">For example, a series of transaction log backups contain a long-running transaction.</span></span> <span data-ttu-id="4730b-127">트랜잭션의 시작은 첫 번째 트랜잭션 로그 백업에 기록되지만 트랜잭션의 끝은 두 번째 트랜잭션 로그 백업에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-127">The start of the transaction is recorded in the first transaction log backup, but the end of the transaction is recorded in the second transaction log backup.</span></span> <span data-ttu-id="4730b-128">첫 번째 트랜잭션 로그 백업에는 커밋 또는 롤백 작업의 기록이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-128">There is no record of a commit or rollback operation in the first transaction log backup.</span></span> <span data-ttu-id="4730b-129">첫 번째 트랜잭션 로그 백업이 적용될 때 복구 작업이 실행되면 장기 실행 트랜잭션은 완료되지 않은 것으로 취급되고 해당 트랜잭션에 대한 첫 번째 트랜잭션 로그 백업에 기록된 데이터 수정이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-129">If a recovery operation runs when the first transaction log backup is applied, the long-running transaction is treated as incomplete, and data modifications recorded in the first transaction log backup for the transaction are rolled back.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4730b-130">에서는 이 시점 이후에 두 번째 트랜잭션 로그 백업을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-130">does not allow for the second transaction log backup to be applied after this point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4730b-131">경우에 따라서는 로그 복원 중에 파일을 명시적으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-131">In some circumstances, you can explicitly add a file during log restore.</span></span>  
  
##  <a name="using-log-backups-to-restore-to-the-point-of-failure"></a><a name="PITrestore"></a><span data-ttu-id="4730b-132">로그 백업을 사용 하 여 오류 지점으로 복원</span><span class="sxs-lookup"><span data-stu-id="4730b-132">Using Log Backups to Restore to the Point of Failure</span></span>  
 <span data-ttu-id="4730b-133">예를 들어 다음과 같은 순서의 이벤트가 발생한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-133">Assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="4730b-134">Time</span><span class="sxs-lookup"><span data-stu-id="4730b-134">Time</span></span>|<span data-ttu-id="4730b-135">이벤트</span><span class="sxs-lookup"><span data-stu-id="4730b-135">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="4730b-136">8:00 A.M.</span><span class="sxs-lookup"><span data-stu-id="4730b-136">8:00 A.M.</span></span>|<span data-ttu-id="4730b-137">데이터베이스를 백업하여 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-137">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="4730b-138">정오</span><span class="sxs-lookup"><span data-stu-id="4730b-138">Noon</span></span>|<span data-ttu-id="4730b-139">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-139">Back up transaction log.</span></span>|  
|<span data-ttu-id="4730b-140">오후 4:00</span><span class="sxs-lookup"><span data-stu-id="4730b-140">4:00 P.M.</span></span>|<span data-ttu-id="4730b-141">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-141">Back up transaction log.</span></span>|  
|<span data-ttu-id="4730b-142">오후 6:00</span><span class="sxs-lookup"><span data-stu-id="4730b-142">6:00 P.M.</span></span>|<span data-ttu-id="4730b-143">데이터베이스를 백업하여 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-143">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="4730b-144">8:00 P.M.</span><span class="sxs-lookup"><span data-stu-id="4730b-144">8:00 P.M.</span></span>|<span data-ttu-id="4730b-145">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-145">Back up transaction log.</span></span>|  
|<span data-ttu-id="4730b-146">9:45 P.M.</span><span class="sxs-lookup"><span data-stu-id="4730b-146">9:45 P.M.</span></span>|<span data-ttu-id="4730b-147">오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-147">Failure occurs.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4730b-148">이 백업 시퀀스의 예제에 대한 설명은 [트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4730b-148">For an explanation of this example sequence of backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="4730b-149">데이터베이스를 오류 발생 시점인 오후 9:45의 상태로 복원하려면</span><span class="sxs-lookup"><span data-stu-id="4730b-149">To restore the database to its state at 9:45 P.M.</span></span> <span data-ttu-id="4730b-150">다음 대체 절차 중 하나를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4730b-150">(the point of failure), either of the following alternative procedures can be used:</span></span>  
  
 <span data-ttu-id="4730b-151">**대체 1: 가장 최근의 전체 데이터베이스 백업을 사용하여 데이터베이스 복원**</span><span class="sxs-lookup"><span data-stu-id="4730b-151">**Alternative 1: Restore the database by using the most recent full database backup**</span></span>  
  
1.  <span data-ttu-id="4730b-152">오류 발생 시점에 활성화되어 있던 트랜잭션 로그의 비상 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-152">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="4730b-153">8:00 A.M.의 전체 데이터베이스 백업을</span><span class="sxs-lookup"><span data-stu-id="4730b-153">Do not restore the 8:00 A.M.</span></span> <span data-ttu-id="4730b-154">시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-154">full database backup.</span></span> <span data-ttu-id="4730b-155">대신 가장 최근의 6:00 P.M. 전체 데이터베이스 백업을</span><span class="sxs-lookup"><span data-stu-id="4730b-155">Instead, restore the more recent 6:00 P.M.</span></span> <span data-ttu-id="4730b-156">복원한 다음 8:00 P.M.</span><span class="sxs-lookup"><span data-stu-id="4730b-156">full database backup, and then apply the 8:00 P.M.</span></span> <span data-ttu-id="4730b-157">로그 백업 및 비상 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-157">log backup and the tail-log backup.</span></span>  
  
 <span data-ttu-id="4730b-158">**대체 2: 이전의 전체 데이터베이스 백업을 사용하여 데이터베이스 복원**</span><span class="sxs-lookup"><span data-stu-id="4730b-158">**Alternative 2: Restore the database by using an earlier full database backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4730b-159">이 대체 프로세스는 문제로 인해 6:00 P.M.의 전체 데이터베이스 백업을 사용할 수 없는 경우에</span><span class="sxs-lookup"><span data-stu-id="4730b-159">This alternative process is useful if a problem prevents you from using the 6:00 P.M.</span></span> <span data-ttu-id="4730b-160">시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-160">full database backup.</span></span> <span data-ttu-id="4730b-161">6:00 P.M.의 전체 데이터베이스 백업에서 복원하는 것보다</span><span class="sxs-lookup"><span data-stu-id="4730b-161">This process takes longer than restoring from the 6:00 P.M.</span></span> <span data-ttu-id="4730b-162">시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-162">full database backup.</span></span>  
  
1.  <span data-ttu-id="4730b-163">오류 발생 시점에 활성화되어 있던 트랜잭션 로그의 비상 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-163">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="4730b-164">8:00 A.M.의 전체 데이터베이스 백업을</span><span class="sxs-lookup"><span data-stu-id="4730b-164">Restore the 8:00 A.M.</span></span> <span data-ttu-id="4730b-165">복원한 다음 4개의 트랜잭션 로그 백업을 순서대로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-165">full database backup, and then restore all four transaction log backups in sequence.</span></span> <span data-ttu-id="4730b-166">이렇게 하면 완료된 모든 트랜잭션을 9:45 P.M.까지 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-166">This rolls forward all completed transactions up to 9:45 P.M.</span></span>  
  
     <span data-ttu-id="4730b-167">이 대체 프로세스를 통해 일련의 전체 데이터베이스 백업에서 트랜잭션 로그 백업 체인을 유지함으로써 제공되는 중복 보안을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-167">This alternative points out the redundant security offered by maintaining a chain of transaction log backups across a series of full database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4730b-168">경우에 따라 트랜잭션 로그를 사용하여 데이터베이스를 지정 시간으로 복원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-168">In some cases, you can also use transaction logs to restore a database to a specific point in time.</span></span> <span data-ttu-id="4730b-169">자세한 내용은 [SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4730b-169">For more information, [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4730b-170">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4730b-170">Related Tasks</span></span>  
 <span data-ttu-id="4730b-171">**트랜잭션 로그 백업을 적용하려면**</span><span class="sxs-lookup"><span data-stu-id="4730b-171">**To apply a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="4730b-172">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-172">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="4730b-173">**복구 지점으로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="4730b-173">**To restore to your recovery point**</span></span>  
  
-   [<span data-ttu-id="4730b-174">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-174">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="4730b-175">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-175">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <span data-ttu-id="4730b-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="4730b-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
-   [<span data-ttu-id="4730b-177">표시된 트랜잭션이 포함된 관련 데이터베이스 복구</span><span class="sxs-lookup"><span data-stu-id="4730b-177">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="4730b-178">로그 시퀀스 번호로 복구&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-178">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
 <span data-ttu-id="4730b-179">**WITH NORECOVERY를 사용하여 백업을 복원한 후 데이터베이스를 복구하려면**</span><span class="sxs-lookup"><span data-stu-id="4730b-179">**To recover a database after restoring backups using WITH NORECOVERY**</span></span>  
  
-   [<span data-ttu-id="4730b-180">데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-180">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="4730b-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4730b-181">See Also</span></span>  
 [<span data-ttu-id="4730b-182">트랜잭션 로그&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4730b-182">The Transaction Log &#40;SQL Server&#41;</span></span>](../logs/the-transaction-log-sql-server.md)  
  
  
