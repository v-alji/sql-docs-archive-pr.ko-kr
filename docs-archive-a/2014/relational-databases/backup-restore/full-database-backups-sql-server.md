---
title: 전체 데이터베이스 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backups [SQL Server], database
- backing up databases [SQL Server], full backups
- estimating database backup size
- backing up [SQL Server], size of backup
- database backups [SQL Server], full backups
- size [SQL Server], backups
- database backups [SQL Server], about backing up databases
ms.assetid: 4d933d19-8d21-4aa1-8153-d230cb3a3f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ee871b6cabbe6c2b2cb4f444fd1e2d42d711dfbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731759"
---
# <a name="full-database-backups-sql-server"></a><span data-ttu-id="8bc59-102">전체 데이터베이스 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8bc59-102">Full Database Backups (SQL Server)</span></span>
  <span data-ttu-id="8bc59-103">전체 데이터베이스 백업은 전체 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-103">A full database backup backs up the whole database.</span></span> <span data-ttu-id="8bc59-104">이 백업은 전체 데이터베이스 백업이 복원된 후 전체 데이터베이스가 복구될 수 있도록 트랜잭션 로그의 일부를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-104">This includes part of the transaction log so that the full database can be recovered after a full database backup is restored.</span></span> <span data-ttu-id="8bc59-105">전체 데이터베이스 백업은 백업 완료 시점의 데이터베이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-105">Full database backups represent the database at the time the backup finished.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8bc59-106">데이터베이스가 커짐에 따라 전체 데이터베이스 백업은 완료하는 데 시간이 오래 걸리고 스토리지 공간도 더 많이 필요하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-106">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="8bc59-107">따라서 큰 데이터베이스의 경우 *차등 데이터베이스 백업*으로 전체 데이터베이스 백업을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-107">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="8bc59-108">자세한 내용은 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc59-108">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8bc59-109">데이터베이스 백업에서 TRUSTWORTHY는 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-109">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="8bc59-110">TRUSTWORTHY를 ON으로 설정하는 방법은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc59-110">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="8bc59-111">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="8bc59-111">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="8bc59-112">단순 복구 모델에서 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="8bc59-112">Database Backups Under the Simple Recovery Model</span></span>](#DbBuRMs)  
  
-   [<span data-ttu-id="8bc59-113">전체 복구 모델에서 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="8bc59-113">Database Backups Under the Full Recovery Model</span></span>](#DbBuRMf)  
  
-   [<span data-ttu-id="8bc59-114">전체 데이터베이스 백업을 사용하여 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="8bc59-114">Use a Full Database Backup to Restore the Database</span></span>](#RestoreDbBu)  
  
-   [<span data-ttu-id="8bc59-115">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8bc59-115">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="database-backups-under-the-simple-recovery-model"></a><a name="DbBuRMs"></a> <span data-ttu-id="8bc59-116">단순 복구 모델에서 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="8bc59-116">Database Backups Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="8bc59-117">단순 복구 모델에서는 각 백업 후 재해가 발생할 경우 데이터베이스가 잠재적 작업 손실 위험에 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-117">Under the simple recovery model, after each backup, the database is exposed to potential work loss if a disaster were to occur.</span></span> <span data-ttu-id="8bc59-118">다음 백업이 시작되어 작업 손실 가능성이 다시 0이 되고 새 작업 손실 가능성 주기가 시작될 때까지 작업 손실 가능성은 업데이트를 수행할 때마다 커집니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-118">The work-loss exposure increases with each update until the next backup, when the work-loss exposure returns to zero and a new cycle of work-loss exposure starts.</span></span> <span data-ttu-id="8bc59-119">시간의 경과에 따라 백업 사이의 작업 손실 가능성이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-119">Work-loss exposure increases over time between backups.</span></span> <span data-ttu-id="8bc59-120">다음 그림에서는 전체 데이터베이스 백업만 사용하는 백업 전략의 작업 손실 가능성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-120">The following illustration shows the work-loss exposure for a backup strategy that uses only full database backups.</span></span>  
  
 <span data-ttu-id="8bc59-121">![데이터베이스 백업 간의 작업 손실 가능성 표시](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "데이터베이스 백업 간의 작업 손실 가능성 표시")</span><span class="sxs-lookup"><span data-stu-id="8bc59-121">![Shows work-loss exposure between database backups](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "Shows work-loss exposure between database backups")</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="8bc59-122">예제([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8bc59-122">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="8bc59-123">다음 예에서는 기존 백업을 덮어쓰고 새 미디어 세트를 만들기 위해 WITH FORMAT을 사용하여 전체 데이터베이스 백업을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-123">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span>  
  
```  
-- Back up the AdventureWorks2012 database to new media set.  
BACKUP DATABASE AdventureWorks2012  
    TO DISK = 'Z:\SQLServerBackups\AdventureWorksSimpleRM.bak'   
    WITH FORMAT;  
GO  
```  
  
##  <a name="database-backups-under-the-full-recovery-model"></a><a name="DbBuRMf"></a> <span data-ttu-id="8bc59-124">전체 복구 모델에서 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="8bc59-124">Database Backups Under the Full Recovery Model</span></span>  
 <span data-ttu-id="8bc59-125">전체 및 대량 로그 복구를 사용하는 데이터베이스의 경우 데이터베이스 백업이 필요하지만 이것만으로 충분하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-125">For databases that use full and bulk-logged recovery, database backups are necessary but not sufficient.</span></span> <span data-ttu-id="8bc59-126">또한 트랜잭션 로그 백업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-126">Transaction log backups are also required.</span></span> <span data-ttu-id="8bc59-127">다음 그림에서는 전체 복구 모델에서 사용 가능한 가장 단순한 백업 전략을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-127">The following illustration shows the least complex backup strategy that is possible under the full recovery model.</span></span>  
  
 <span data-ttu-id="8bc59-128">![일련의 전체 데이터베이스 백업 및 로그 백업](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "일련의 전체 데이터베이스 백업 및 로그 백업")</span><span class="sxs-lookup"><span data-stu-id="8bc59-128">![Series of full database backups and log backups](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "Series of full database backups and log backups")</span></span>  
  
 <span data-ttu-id="8bc59-129">로그 백업을 만드는 방법은 [트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc59-129">For information about how to create log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="8bc59-130">예제([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8bc59-130">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="8bc59-131">다음 예에서는 기존 백업을 덮어쓰고 새 미디어 세트를 만들기 위해 WITH FORMAT을 사용하여 전체 데이터베이스 백업을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-131">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span> <span data-ttu-id="8bc59-132">그런 다음 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-132">Then, the example backs up the transaction log.</span></span> <span data-ttu-id="8bc59-133">실제 상황에서는 일련의 정기적인 로그 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-133">In a real-life situation, you would have to perform a series of regular log backups.</span></span> <span data-ttu-id="8bc59-134">이 예의 경우 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스는 전체 복구 모델을 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-134">For this example, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database is set to use the full recovery model.</span></span>  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
-- Back up the AdventureWorks2012 database to new media set (backup set 1).  
BACKUP DATABASE AdventureWorks2012  
  TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak'   
  WITH FORMAT;  
GO  
--Create a routine log backup (backup set 2).  
BACKUP LOG AdventureWorks2012 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak';  
GO  
```  
  
##  <a name="use-a-full-database-backup-to-restore-the-database"></a><a name="RestoreDbBu"></a> <span data-ttu-id="8bc59-135">전체 데이터베이스 백업을 사용하여 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="8bc59-135">Use a Full Database Backup to Restore the Database</span></span>  
 <span data-ttu-id="8bc59-136">전체 데이터베이스 백업에서 임의 위치로 데이터베이스를 복원하여 전체 데이터베이스를 한 번에 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-136">You can re-create a whole database in one step by restoring the database from a full database backup to any location.</span></span> <span data-ttu-id="8bc59-137">충분한 트랜잭션 로그가 백업에 포함되어 있으므로 백업 완료 시점에 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-137">Enough of the transaction log is included in the backup to let you recover the database to the time when the backup finished.</span></span> <span data-ttu-id="8bc59-138">복원된 데이터베이스는 커밋되지 않은 트랜잭션을 제외하면 데이터베이스 백업이 완료된 당시의 원래 데이터베이스 상태와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-138">The restored database matches the state of the original database when the database backup finished, minus any uncommitted transactions.</span></span> <span data-ttu-id="8bc59-139">전체 복구 모델에서는 모든 후속 트랜잭션 로그 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-139">Under the full recovery model, you should then restore all subsequent transaction log backups.</span></span> <span data-ttu-id="8bc59-140">데이터베이스가 복구되면 커밋되지 않은 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bc59-140">When the database is recovered, uncommitted transactions are rolled back.</span></span>  
  
 <span data-ttu-id="8bc59-141">자세한 내용은 [전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) 또는 [전체 데이터베이스 복원&#40;전체 복구 모델&#41;](complete-database-restores-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bc59-141">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8bc59-142">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8bc59-142">Related Tasks</span></span>  
 <span data-ttu-id="8bc59-143">**전체 데이터베이스 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="8bc59-143">**To create a full database backup**</span></span>  
  
-   [<span data-ttu-id="8bc59-144">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8bc59-144">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   <span data-ttu-id="8bc59-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="8bc59-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="8bc59-146">**백업 작업을 예약하려면**</span><span class="sxs-lookup"><span data-stu-id="8bc59-146">**To schedule backup jobs**</span></span>  
  
 [<span data-ttu-id="8bc59-147">유지 관리 계획 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="8bc59-147">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="8bc59-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bc59-148">See Also</span></span>  
 <span data-ttu-id="8bc59-149">[SQL Server 데이터베이스 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8bc59-149">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="8bc59-150">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8bc59-150">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="8bc59-151">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="8bc59-151">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
  
