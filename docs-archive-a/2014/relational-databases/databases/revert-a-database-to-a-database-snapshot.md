---
title: 데이터베이스를 데이터베이스 스냅샷으로 되돌리기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], reverting to
- reverting databases
ms.assetid: 8f74dd31-c9ca-4537-8760-0c7648f0787d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c78da3d7c559309c0563760e7062f01cf784648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650089"
---
# <a name="revert-a-database-to-a-database-snapshot"></a><span data-ttu-id="ebc89-102">데이터베이스를 데이터베이스 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="ebc89-102">Revert a Database to a Database Snapshot</span></span>
  <span data-ttu-id="ebc89-103">온라인 데이터베이스의 데이터가 손상되면 일부 경우 데이터베이스를 손상 발생 이전의 데이터베이스 스냅샷으로 되돌리는 작업이 백업에서 온라인 데이터베이스를 복원하는 방법에 대한 대체 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-103">If data in an online database becomes damaged, in some cases, reverting the database to a database snapshot that predates the damage might be an appropriate alternative to restoring the database from a backup.</span></span> <span data-ttu-id="ebc89-104">예를 들어 데이터베이스 되돌리기 작업은 테이블 삭제와 같은 최근의 심각한 사용자 오류 발생 전의 상황으로 돌아가는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-104">For example, reverting a database might be useful for reverse a recent serious user error, such as a dropped table.</span></span> <span data-ttu-id="ebc89-105">그러나 스냅샷을 만든 후의 모든 변경 내용은 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-105">However, all changes made after the snapshot was created are lost.</span></span>  
  
-   <span data-ttu-id="ebc89-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ebc89-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ebc89-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ebc89-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ebc89-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ebc89-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ebc89-109">보안</span><span class="sxs-lookup"><span data-stu-id="ebc89-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ebc89-110">**데이터베이스를 데이터베이스 스냅샷으로 되돌리려면 다음을 사용합니다.**  [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="ebc89-110">**To Revert a Database to a Database Snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ebc89-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ebc89-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ebc89-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ebc89-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ebc89-113">다음과 같은 경우에는 되돌리기가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-113">Reverting is unsupported under the following conditions:</span></span>  
  
-   <span data-ttu-id="ebc89-114">데이터베이스는 현재 되돌릴 계획인 데이터베이스 스냅샷을 하나만 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-114">The database must currently have only one database snapshot, to which you plan to revert.</span></span>  
  
-   <span data-ttu-id="ebc89-115">데이터베이스에 읽기 전용 또는 압축 파일 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-115">Any read-only or compressed filegroups exist in the database.</span></span>  
  
-   <span data-ttu-id="ebc89-116">스냅샷이 만들어질 때 온라인 상태였던 파일이 이제 오프라인 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-116">Any files are now offline but were online when the snapshot was created.</span></span>  
  
 <span data-ttu-id="ebc89-117">데이터베이스를 되돌리기 전에 다음 제한 사항을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-117">Before reverting a database, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="ebc89-118">되돌리기는 미디어 복구용으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-118">Reverting is not intended for media recovery.</span></span> <span data-ttu-id="ebc89-119">.</span><span class="sxs-lookup"><span data-stu-id="ebc89-119">.</span></span> <span data-ttu-id="ebc89-120">데이터베이스 스냅샷은 데이터베이스 파일의 불완전한 복사본이므로 데이터베이스나 데이터베이스 스냅샷이 손상된 경우 스냅샷에서 되돌릴 수 없는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-120">A database snapshot is an incomplete copy of the database files, so if either the database or the database snapshot is corrupted, reverting from a snapshot is likely to be impossible.</span></span> <span data-ttu-id="ebc89-121">가능하다고 해도 손상된 경우에는 되돌리기를 수행해도 문제가 해결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-121">Furthermore, even when it is possible, reverting in the event of corruption is unlikely to correct the problem.</span></span> <span data-ttu-id="ebc89-122">따라서 데이터베이스를 보호하려면 정기적으로 백업하고 복원 계획을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-122">Therefore, taking regular backups and testing your restore plan are essential to protect a database.</span></span> <span data-ttu-id="ebc89-123">자세한 내용은 [SQL Server Database 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-123">For more information, see [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ebc89-124">데이터베이스 스냅샷을 만든 시점까지 원본 데이터베이스를 복원해야 하는 경우 전체 복구 모델을 사용하고 이 작업을 수행할 수 있는 백업 정책을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-124">If you need to be able to restore the source database to the point in time at which you created a database snapshot, use the full recovery model and implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="ebc89-125">원래의 원본 데이터베이스를 되돌린 데이터베이스로 덮어쓰기 때문에 스냅샷을 만든 후 데이터베이스에 대해 수행된 모든 업데이트는 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-125">The original source database is overwritten by the reverted database, so any updates to the database since the snapshot's creation are lost.</span></span>  
  
-   <span data-ttu-id="ebc89-126">또한 되돌리기 작업으로 오래된 로그 파일이 덮어 쓰이고 로그가 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-126">The revert operation also overwrites the old log file and rebuilds the log.</span></span> <span data-ttu-id="ebc89-127">따라서 되돌린 데이터베이스를 사용자 오류 발생 지점으로 롤포워드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-127">Consequently, you cannot roll the reverted database forward to the point of user error.</span></span> <span data-ttu-id="ebc89-128">그러므로 데이터베이스를 되돌리기 전에 로그를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-128">Therefore, we recommend that you back up the log before reverting a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ebc89-129">원본 로그를 복원하여 데이터베이스를 롤포워드할 수 없어도 원본 로그 파일의 내용은 손실된 데이터를 다시 구성할 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-129">Although you cannot restore the original log to roll forward the database, the information in the original log file can be useful for reconstructing lost data.</span></span>  
  
-   <span data-ttu-id="ebc89-130">되돌리기로 인해 로그 백업 체인이 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-130">Reverting breaks the log backup chain.</span></span> <span data-ttu-id="ebc89-131">따라서 되돌려진 데이터베이스의 로그를 백업하기 전에 먼저 전체 데이터베이스 또는 파일을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-131">Therefore, before you can take log backups of the reverted database, you must first take a full database backup or file backup.</span></span> <span data-ttu-id="ebc89-132">전체 데이터베이스를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-132">We recommend a full database backup.</span></span>  
  
-   <span data-ttu-id="ebc89-133">되돌리기 작업 동안 스냅샷과 원본 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-133">During a revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="ebc89-134">원본 데이터베이스와 스냅샷은 모두 "복원 중"으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-134">The source database and snapshot are both marked "In restore."</span></span> <span data-ttu-id="ebc89-135">되돌리기 작업 중 오류가 발생하면 데이터베이스가 다시 시작될 때 되돌리기를 완료하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-135">If an error occurs during the revert operation, when the database starts up again, the revert operation will try to finish reverting.</span></span>  
  
-   <span data-ttu-id="ebc89-136">되돌려진 데이터베이스의 메타데이터는 스냅샷 시점의 메타데이터와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-136">The metadata of a reverted database is the same as the metadata at the time of the snapshot.</span></span>  
  
-   <span data-ttu-id="ebc89-137">되돌리면 전체 텍스트 카탈로그가 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-137">Reverting drops all the full-text catalogs.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ebc89-138">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ebc89-138">Prerequisites</span></span>  
 <span data-ttu-id="ebc89-139">원본 데이터베이스 및 데이터베이스 스냅샷은 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-139">Ensure that the source database and database snapshot meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="ebc89-140">데이터베이스가 손상되지 않았어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-140">Verify that the database has not become corrupted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ebc89-141">데이터베이스가 손상된 경우 백업에서 해당 데이터베이스를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-141">If the database has been corrupted, you will need to restore it from backups.</span></span> <span data-ttu-id="ebc89-142">자세한 내용은 [전체 데이터베이스 복원&#40;단순 복구 모델&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) 또는 [전체 데이터베이스 복원&#40;전체 복구 모델&#41;](../backup-restore/complete-database-restores-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-142">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](../backup-restore/complete-database-restores-full-recovery-model.md).</span></span>  
  
-   <span data-ttu-id="ebc89-143">오류가 발생하기 전에 만든 최근 스냅샷을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-143">Identify a recent snapshot that was created before the error.</span></span> <span data-ttu-id="ebc89-144">자세한 내용은 [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="ebc89-144">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ebc89-145">데이터베이스에 현재 있는 다른 모든 스냅샷을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-145">Drop any other snapshots that currently exist on the database.</span></span> <span data-ttu-id="ebc89-146">자세한 내용은 [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ebc89-146">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ebc89-147">보안</span><span class="sxs-lookup"><span data-stu-id="ebc89-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ebc89-148">권한</span><span class="sxs-lookup"><span data-stu-id="ebc89-148">Permissions</span></span>  
 <span data-ttu-id="ebc89-149">원본 데이터베이스에 대한 RESTORE DATABASE 권한을 가진 사용자는 해당 데이터베이스를 데이터베이스 스냅샷을 만들었을 때의 상태로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-149">Any user who has RESTORE DATABASE permissions on the source database can revert it to its state when a database snapshot was created.</span></span>  
  
##  <a name="how-to-revert-a-database-to-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ebc89-150">데이터베이스를 데이터베이스 스냅샷으로 되돌리는 방법(Transact-SQL 사용)</span><span class="sxs-lookup"><span data-stu-id="ebc89-150">How to Revert a Database to a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="ebc89-151">**데이터베이스를 데이터베이스 스냅샷으로 되돌리려면**</span><span class="sxs-lookup"><span data-stu-id="ebc89-151">**To revert a database to a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebc89-152">이 프로시저의 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-152">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="ebc89-153">데이터베이스를 되돌릴 데이터베이스 스냅샷을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-153">Identify the database snapshot to which you want to revert the database.</span></span> <span data-ttu-id="ebc89-154">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 데이터베이스의 스냅샷을 확인할 수 있습니다([데이터베이스 스냅샷 보기&#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="ebc89-154">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)).</span></span> <span data-ttu-id="ebc89-155">또한 **sys.databases&amp;#40;Transact-SQL&amp;#41;** 카탈로그 뷰의 [sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 열에서 뷰의 원본 데이터베이스를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-155">Also, you can identify the source database of a view from the **source_database_id** column of the [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
2.  <span data-ttu-id="ebc89-156">다른 모든 데이터베이스 스냅샷을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-156">Drop any other database snapshots.</span></span>  
  
     <span data-ttu-id="ebc89-157">스냅샷 삭제 방법은 [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ebc89-157">For information on dropping snapshots, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span> <span data-ttu-id="ebc89-158">되돌리기 전에 데이터베이스에서 전체 복구 모델을 사용하는 경우 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-158">If the database uses the full recovery model, before reverting, you should back up the log.</span></span> <span data-ttu-id="ebc89-159">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) 또는 [데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-159">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) or [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="ebc89-160">되돌리기 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-160">Perform the revert operation.</span></span>  
  
     <span data-ttu-id="ebc89-161">되돌리기 작업을 수행하려면 원본 데이터베이스에 대해 RESTORE DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-161">A revert operation requires RESTORE DATABASE permissions on the source database.</span></span> <span data-ttu-id="ebc89-162">데이터베이스를 되돌리려면 다음과 같은 Transact-SQL 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-162">To revert the database, use the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="ebc89-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=** _database_snapshot_name_</span><span class="sxs-lookup"><span data-stu-id="ebc89-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=**_database_snapshot_name_</span></span>  
  
     <span data-ttu-id="ebc89-164">여기서 *database_name* 은 원본 데이터베이스이고 *database_snapshot_name* 은 데이터베이스를 되돌리려는 스냅샷의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-164">Where *database_name* is the source database and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="ebc89-165">이 문에서 백업 디바이스가 아닌 스냅샷 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-165">Notice that in this statement, you must specify a snapshot name rather than a backup device.</span></span>  
  
     <span data-ttu-id="ebc89-166">자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 통해 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-166">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ebc89-167">되돌리기 작업 동안 스냅샷과 원본 데이터베이스를 모두 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-167">During the revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="ebc89-168">원본 데이터베이스와 스냅샷이 모두 "복원 중"으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-168">The source database and snapshot are both marked as "In restore."</span></span> <span data-ttu-id="ebc89-169">되돌리기 작업 중에 오류가 발생하면 데이터베이스가 다시 시작될 때 되돌리기를 완료하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-169">If an error occurs during the revert operation, it will try to finish reverting when the database starts up again.</span></span>  
  
4.  <span data-ttu-id="ebc89-170">데이터베이스 스냅샷을 만든 후 데이터베이스 소유자가 변경된 경우 되돌린 데이터베이스의 데이터베이스 소유자를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-170">If the database owner changed since creation of the database snapshot, you may want to update the database owner of the reverted database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ebc89-171">되돌린 데이터베이스는 데이터베이스 스냅샷의 사용 권한과 구성(데이터베이스 소유자, 복구 모델 등)을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-171">The reverted database retains the permissions and configuration (such as database owner and recovery model) of the database snapshot.</span></span>  
  
5.  <span data-ttu-id="ebc89-172">데이터베이스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-172">Start the database.</span></span>  
  
6.  <span data-ttu-id="ebc89-173">필요에 따라, 특히 전체 또는 대량 로그 복구 모델을 사용하는 경우 되돌린 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-173">Optionally, back up the reverted database, especially if it uses the full (or bulk-logged) recovery model.</span></span> <span data-ttu-id="ebc89-174">데이터베이스를 백업하려면 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-174">To back up a database, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ebc89-175">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ebc89-175">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="ebc89-176">이 섹션에는 데이터베이스를 데이터베이스 스냅샷으로 되돌리는 다음 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-176">This section contains the following examples of reverting a database to a database snapshot:</span></span>  
  
-   <span data-ttu-id="ebc89-177">A.</span><span class="sxs-lookup"><span data-stu-id="ebc89-177">A.</span></span> [<span data-ttu-id="ebc89-178">AdventureWorks 데이터베이스에 대한 스냅샷 되돌리기</span><span class="sxs-lookup"><span data-stu-id="ebc89-178">Reverting a snapshot on the AdventureWorks database</span></span>](#Reverting_AW)  
  
-   <span data-ttu-id="ebc89-179">B.</span><span class="sxs-lookup"><span data-stu-id="ebc89-179">B.</span></span> [<span data-ttu-id="ebc89-180">Sales 데이터베이스에 대한 스냅샷 되돌리기</span><span class="sxs-lookup"><span data-stu-id="ebc89-180">Reverting a snapshot on the Sales database</span></span>](#Reverting_Sales)  
  
####  <a name="a-reverting-a-snapshot-on-the-adventureworks-database"></a><a name="Reverting_AW"></a> <span data-ttu-id="ebc89-181">1.</span><span class="sxs-lookup"><span data-stu-id="ebc89-181">A.</span></span> <span data-ttu-id="ebc89-182">AdventureWorks 데이터베이스에 대한 스냅샷 되돌리기</span><span class="sxs-lookup"><span data-stu-id="ebc89-182">Reverting a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="ebc89-183">이 예에서는 현재 하나의 스냅샷만 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-183">This example assumes that only one snapshot currently exists on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="ebc89-184">여기서 데이터베이스가 되돌려지는 스냅샷을 만드는 예는 [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ebc89-184">For the example that creates the snapshot to which the database is reverted here, see [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
USE master;  
-- Reverting AdventureWorks to AdventureWorks_dbss1800  
RESTORE DATABASE AdventureWorks from   
DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
  
####  <a name="b-reverting-a-snapshot-on-the-sales-database"></a><a name="Reverting_Sales"></a> <span data-ttu-id="ebc89-185">2.</span><span class="sxs-lookup"><span data-stu-id="ebc89-185">B.</span></span> <span data-ttu-id="ebc89-186">Sales 데이터베이스에 대한 스냅샷 되돌리기</span><span class="sxs-lookup"><span data-stu-id="ebc89-186">Reverting a snapshot on the Sales database</span></span>  
 <span data-ttu-id="ebc89-187">이 예에서는 **Sales** 데이터베이스에 현재 두 개의 스냅샷인 **sales_snapshot0600** 및 **sales_snapshot1200**이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-187">This example assumes that two snapshots currently exist on the **Sales** database: **sales_snapshot0600** and **sales_snapshot1200**.</span></span> <span data-ttu-id="ebc89-188">스냅샷 중 오래된 항목을 삭제하고 데이터베이스를 가장 최근의 스냅샷으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="ebc89-188">The example deletes the older of the snapshots and reverts the database to the more recent snapshot.</span></span>  
  
 <span data-ttu-id="ebc89-189">이 예에 사용되는 예제 데이터베이스와 스냅샷을 만드는 코드는 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-189">For the code for creating the sample database and snapshots on which this example depends, see:</span></span>  
  
-   <span data-ttu-id="ebc89-190">**Sales** 데이터베이스와 **sales_snapshot0600** 스냅샷의 경우 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)의 "파일 그룹이 포함된 데이터베이스 만들기" 및 "데이터베이스 스냅샷 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebc89-190">For the **Sales** database and the **sales_snapshot0600** snapshot, see "Creating a database with filegroups" and "Creating a database snapshot" in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
-   <span data-ttu-id="ebc89-191">**sales_snapshot1200** 스냅샷의 경우 [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ebc89-191">For the **sales_snapshot1200** snapshot, see "Creating a snapshot on the Sales database" in [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
--Test to see if sales_snapshot0600 exists and if it   
-- does, delete it.  
IF EXISTS (SELECT dbid FROM sys.databases  
    WHERE NAME='sales_snapshot0600')  
    DROP DATABASE SalesSnapshot0600;  
GO  
-- Reverting Sales to sales_snapshot1200  
USE master;  
RESTORE DATABASE Sales FROM DATABASE_SNAPSHOT = 'sales_snapshot1200';  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ebc89-192">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ebc89-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ebc89-193">데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ebc89-193">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="ebc89-194">데이터베이스 스냅샷 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ebc89-194">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="ebc89-195">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ebc89-195">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="ebc89-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ebc89-196">See Also</span></span>  
 <span data-ttu-id="ebc89-197">[데이터베이스 스냅샷&#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ebc89-197">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="ebc89-198">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ebc89-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="ebc89-199">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ebc89-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="ebc89-200">데이터베이스 미러링 및 데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ebc89-200">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
  
