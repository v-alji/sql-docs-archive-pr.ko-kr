---
title: 전체 데이터베이스 복원(단순 복구 모델) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67eee8d7d6f44c9ff83795bf2a8bd612309bf0a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661188"
---
# <a name="complete-database-restores-simple-recovery-model"></a><span data-ttu-id="efe63-102">전체 데이터베이스 복원(단순 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="efe63-102">Complete Database Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="efe63-103">전체 데이터베이스 복원의 목적은 전체 데이터베이스를 복원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="efe63-104">복원하는 동안 전체 데이터베이스는 오프라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="efe63-105">데이터베이스의 일부를 온라인에 연결하기 전에 데이터베이스의 모든 부분의 지정 시간이 같고 커밋되지 않은 트랜잭션이 없는 일치하는 지점으로 모든 데이터를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="efe63-106">단순 복구 모델에서는 특정 백업 내의 특정 시점으로 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-106">Under the simple recovery model, the database cannot be restored to a specific point in time within a specific backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="efe63-107">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-107">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="efe63-108">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-108">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="efe63-109">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="efe63-109">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="efe63-110">이전 버전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 백업 지원에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)의 "호환성 지원" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efe63-110">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="overview-of-database-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="efe63-111">단순 복구 모델에서의 데이터베이스 복원 개요</span><span class="sxs-lookup"><span data-stu-id="efe63-111">Overview of Database Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="efe63-112">단순 복구 모델에서는 차등 데이터베이스 백업을 복원할지 여부에 따라 전체 데이터베이스 복원이 하나 또는 두 개의 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-112">A full database restore under the simple recovery model involves one or two [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statements, depending on whether you want to restore a differential database backup.</span></span> <span data-ttu-id="efe63-113">전체 데이터베이스 백업만 사용하는 경우 다음 그림과 같이 최신 백업을 복원하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-113">If you are using only a full database backup, just restore the most recent backup, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="efe63-114">![전체 데이터베이스 백업만 복원](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "전체 데이터베이스 백업만 복원")</span><span class="sxs-lookup"><span data-stu-id="efe63-114">![Restoring only a full database backup](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Restoring only a full database backup")</span></span>  
  
 <span data-ttu-id="efe63-115">또한 차등 데이터베이스 백업을 사용하는 경우 데이터베이스를 복구하지 않고 가장 최근의 전체 데이터베이스 백업을 복원한 다음 가장 최근의 차등 데이터베이스 백업을 복원하고 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-115">If you are also using a differential database backup, restore the most recent full database backup without recovering the database, and then restore the most recent differential database backup and recover the database.</span></span> <span data-ttu-id="efe63-116">다음 그림에서는 이 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-116">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="efe63-117">![전체 및 차등 데이터베이스 백업 복원](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "전체 및 차등 데이터베이스 백업 복원")</span><span class="sxs-lookup"><span data-stu-id="efe63-117">![Restoring full and differential database backups](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Restoring full and differential database backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efe63-118">데이터베이스 백업을 다른 서버 인스턴스로 복원하려면 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efe63-118">If you plan to restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="efe63-119">기본 Transact-SQL RESTORE 구문</span><span class="sxs-lookup"><span data-stu-id="efe63-119">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="efe63-120">전체 데이터베이스 백업을 복원하는 기본 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-120">The basic [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a full database backup is:</span></span>  
  
 <span data-ttu-id="efe63-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span><span class="sxs-lookup"><span data-stu-id="efe63-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efe63-122">차등 데이터베이스 백업도 복원하려면 WITH NORECOVERY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-122">Use WITH NORECOVERY if you plan to also restore a differential database backup.</span></span>  
  
 <span data-ttu-id="efe63-123">데이터베이스 백업을 복원하는 기본 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-123">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a database backup is:</span></span>  
  
 <span data-ttu-id="efe63-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="efe63-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span></span>  
  
###  <a name="example-transact-sql"></a><a name="Example"></a> <span data-ttu-id="efe63-125">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="efe63-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="efe63-126">다음 예에서는 먼저 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 사용하여 전체 데이터베이스 백업과 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 차등 데이터베이스 백업을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-126">The following example first shows how to use the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to create a full database backup and a differential database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="efe63-127">그런 다음 이러한 백업을 차례로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-127">The example then restores these backups in sequence.</span></span> <span data-ttu-id="efe63-128">데이터베이스는 차등 데이터베이스 백업이 완료된 시점의 상태로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-128">The database is restored to its state as of the time that the differential database backup finished.</span></span>  
  
 <span data-ttu-id="efe63-129">이 예에서는 전체 데이터베이스 복원 시나리오에 따른 복원 시퀀스의 중요 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-129">The example shows the critical options in a restore sequence for the complete database restore scenario.</span></span> <span data-ttu-id="efe63-130">*복원 순서* 는 하나 이상의 복원 단계를 통해 데이터를 이동시키는 하나 이상의 복원 작업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-130">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span> <span data-ttu-id="efe63-131">이 용도와 관련 없는 구문 및 세부 사항은 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-131">Syntax and details that are not relevant to this purpose are omitted.</span></span> <span data-ttu-id="efe63-132">데이터베이스를 복구할 때 명확성을 위해 RECOVERY 옵션(기본값)을 명시적으로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-132">When you recover a database, we recommend explicitly specifying the RECOVERY option for clarity, even though it is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efe63-133">이 예제는 복구 모델을 [로 설정하는](/sql/t-sql/statements/alter-database-transact-sql) ALTER DATABASE `SIMPLE`문으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="efe63-133">The example starts with an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement that sets the recovery model to `SIMPLE`.</span></span>  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="efe63-134">관련 작업</span><span class="sxs-lookup"><span data-stu-id="efe63-134">Related Tasks</span></span>  
 <span data-ttu-id="efe63-135">**전체 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="efe63-135">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="efe63-136">단순 복구 모델에서 데이터베이스 백업 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efe63-136">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="efe63-137">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="efe63-137">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="efe63-138">데이터베이스를 새 위치로 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="efe63-138">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="efe63-139">**차등 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="efe63-139">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="efe63-140">차등 데이터베이스 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="efe63-140">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="efe63-141">**SMO(SQL Server 관리 개체)를 사용하여 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="efe63-141">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a><span data-ttu-id="efe63-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efe63-142">See Also</span></span>  
 <span data-ttu-id="efe63-143">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="efe63-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="efe63-144">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="efe63-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="efe63-145">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="efe63-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="efe63-146">[전체 데이터베이스 백업&#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="efe63-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="efe63-147">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="efe63-147">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="efe63-148">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="efe63-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="efe63-149">복원 및 복구 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="efe63-149">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
