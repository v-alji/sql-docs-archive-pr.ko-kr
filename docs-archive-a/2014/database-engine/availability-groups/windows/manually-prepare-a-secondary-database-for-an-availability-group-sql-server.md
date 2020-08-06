---
title: 가용성 그룹에 대한 보조 데이터베이스 수동 준비(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.configsecondarydbs.f1
- sql12.swb.availabilitygroup.preparedbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 9f2feb3c-ea9b-4992-8202-2aeed4f9a6dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3da3f7332bdabce65785b2844157dd4639389254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649185"
---
# <a name="manually-prepare-a-secondary-database-for-an-availability-group-sql-server"></a><span data-ttu-id="a412b-102">가용성 그룹에 대한 보조 데이터베이스 수동 준비(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a412b-102">Manually Prepare a Secondary Database for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="a412b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 AlwaysOn 가용성 그룹에 대한 보조 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-103">This topic describes how to prepare a secondary database for an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="a412b-104">보조 데이터베이스를 준비하려면 (1) RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 데이터베이스 백업과 후속 로그 백업을 보조 복제본을 호스트하는 각 서버 인스턴스로 복원하고 (2) 복원된 데이터베이스를 가용성 그룹에 조인하는 두 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-104">Preparing a secondary database requires two steps: (1) restoring a recent database backup of the primary database and subsequent log backups onto each server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY, and (2) joining the restored database to the availability group.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a412b-105">기존 로그 전달 구성이 있는 경우 하나 이상의 보조 데이터베이스와 함께 로그 전달 주 데이터베이스를 AlwaysOn 주 데이터베이스 및 하나 이상의 AlwaysOn 보조 데이터베이스로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-105">If you have an existing log shipping configuration, you might be able to convert the log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and one or more AlwaysOn secondary databases.</span></span> <span data-ttu-id="a412b-106">자세한 내용은 [로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;로 마이그레이션하기 위한 필수 조건 ](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-106">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="a412b-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a412b-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a412b-108">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="a412b-108">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="a412b-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a412b-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a412b-110">보안</span><span class="sxs-lookup"><span data-stu-id="a412b-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a412b-111">**보조 데이터베이스를 준비하려면:**</span><span class="sxs-lookup"><span data-stu-id="a412b-111">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="a412b-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a412b-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a412b-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a412b-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="a412b-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="a412b-114">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="a412b-115">관련된 백업 및 복원 태스크</span><span class="sxs-lookup"><span data-stu-id="a412b-115">Related Backup and Restore Tasks</span></span>](#RelatedTasks)  
  
-   <span data-ttu-id="a412b-116">**후속 작업:** [보조 데이터베이스를 준비한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a412b-116">**Follow Up:** [After Preparing a Secondary Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a412b-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a412b-117">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="a412b-118">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="a412b-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="a412b-119">데이터베이스를 배치할 시스템에 보조 데이터베이스를 위한 충분한 공간을 가진 디스크 드라이브가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-119">Make sure that the system where you plan to place database possesses a disk drive with sufficient space for the secondary databases.</span></span>  
  
-   <span data-ttu-id="a412b-120">보조 데이터베이스의 이름이 주 데이터베이스의 이름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-120">The name of the secondary database must be the same as the name of the primary database.</span></span>  
  
-   <span data-ttu-id="a412b-121">모든 복원 작업에 대해 RESTORE WITH NORECOVERY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-121">Use RESTORE WITH NORECOVERY for every restore operation.</span></span>  
  
-   <span data-ttu-id="a412b-122">보조 데이터베이스가 주 데이터베이스와 다른 파일 경로(드라이브 문자 포함)에 있어야 하는 경우 복원 명령에서 각 데이터베이스 파일에 대해 WITH MOVE 옵션을 사용하여 보조 데이터베이스의 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-122">If the secondary database needs to reside on a different file path (including the drive letter) than the primary database, the restore command must also use the WITH MOVE option for each of the database files to specify them to the path of the secondary database.</span></span>  
  
-   <span data-ttu-id="a412b-123">파일 그룹별로 데이터베이스 파일 그룹을 복원하는 경우에는 전체 데이터베이스를 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-123">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
-   <span data-ttu-id="a412b-124">데이터베이스를 복원한 후 마지막으로 복원한 데이터 백업 이후에 만든 모든 로그 백업을 복원(WITH NORECOVERY)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-124">After restoring the database, you must restore (WITH NORECOVERY) every log backup created since the last restored data backup.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a412b-125">권장 사항</span><span class="sxs-lookup"><span data-stu-id="a412b-125">Recommendations</span></span>  
  
-   <span data-ttu-id="a412b-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 독립 실행형 인스턴스의 경우 지정된 보조 데이터베이스의 드라이브 문자를 포함한 파일 경로는 가급적 해당 주 데이터베이스의 경로와 동일한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-126">On stand-alone instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], we recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span> <span data-ttu-id="a412b-127">보조 데이터베이스를 만들 때 데이터베이스 파일을 이동하면 이후의 파일 추가 작업이 보조 데이터베이스에서 실패하고 보조 데이터베이스가 일시 중지될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-127">This is because if you move the database files when creating a secondary database, a later add-file operation might fail on the secondary database and cause the secondary database to be suspended.</span></span>  
  
-   <span data-ttu-id="a412b-128">보조 데이터베이스를 준비하기 전에 보조 복제본의 초기화가 완료될 때까지 가용성 그룹에서 데이터베이스에 대한 예약된 로그 백업을 일시 중지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-128">Before preparing your secondary databases, we strongly recommend that you suspend scheduled log backups on the databases in the availability group until the initialization of secondary replicas has completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a412b-129">보안</span><span class="sxs-lookup"><span data-stu-id="a412b-129">Security</span></span>  
 <span data-ttu-id="a412b-130">데이터베이스가 백업 되 면 신뢰할 수 있는 [데이터베이스 속성이](../../../relational-databases/security/trustworthy-database-property.md) OFF로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-130">When a database is backed up, the [TRUSTWORTHY database property](../../../relational-databases/security/trustworthy-database-property.md) is set to OFF.</span></span> <span data-ttu-id="a412b-131">따라서 새로 복원된 데이터베이스의 TRUSTWORTHY는 항상 OFF입니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-131">Therefore, TRUSTWORTHY is always OFF on a newly restored database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a412b-132">권한</span><span class="sxs-lookup"><span data-stu-id="a412b-132">Permissions</span></span>  
 <span data-ttu-id="a412b-133">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span> <span data-ttu-id="a412b-134">자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-134">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="a412b-135">복원할 데이터베이스가 서버 인스턴스에 없으면 RESTORE 문에 CREATE DATABASE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-135">When the database being restored does not exist on the server instance, the RESTORE statement requires CREATE DATABASE permissions.</span></span> <span data-ttu-id="a412b-136">자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 통해 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-136">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a412b-137">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a412b-137">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a412b-138"> 주 복제본을 호스팅하는 서버 인스턴스와 보조 복제본을 호스팅하는 모든 인스턴스 간에 백업 및 복원 파일 경로가 동일한 경우 [새 가용성 그룹 마법사](use-the-availability-group-wizard-sql-server-management-studio.md), [복제본을 가용성 그룹에 추가 마법사](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)또는 [가용성 그룹에 데이터베이스 추가 마법사](availability-group-add-database-to-group-wizard.md)를 사용하여 보조 데이터베이스를 만들 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-138">If the backup and restore file paths are identical between the server instance that hosts the primary replica and every instance that hosts a secondary replica, you should be able create secondary databases by using [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md).</span></span>  
  
 <span data-ttu-id="a412b-139">**보조 데이터베이스를 준비하려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-139">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="a412b-140">주 데이터베이스의 최근 데이터베이스 백업이 아직 없는 경우 전체 데이터베이스 백업 또는 차등 데이터베이스 백업을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-140">Unless you already have a recent database backup of the primary database, create a new full or differential database backup.</span></span> <span data-ttu-id="a412b-141">이 백업과 모든 후속 로그 백업을 권장 네트워크 공유에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-141">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="a412b-142">주 데이터베이스의 로그 백업을 하나 이상 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-142">Create at least one new log backup of the primary database.</span></span>  
  
3.  <span data-ttu-id="a412b-143">보조 복제본을 호스팅하는 서버 인스턴스에서 주 데이터베이스의 전체 데이터베이스 백업과 원하는 차등 백업을 복원한 다음 모든 후속 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-143">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by any subsequent log backups.</span></span>  
  
     <span data-ttu-id="a412b-144">**RESTORE WITH NORECOVERY 옵션** 페이지에서 다음을 선택합니다. **데이터베이스를 비작동 상태로 유지하고 커밋되지 않은 트랜잭션을 롤백하지 않습니다. 추가 트랜잭션 로그를 복원할 수 있습니다(RESTORE WITH NORECOVERY).** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-144">On the **RESTORE DATABASEOptions** page, select **Leave the database non-operational, and do not roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**.</span></span>  
  
     <span data-ttu-id="a412b-145">주 데이터베이스와 보조 데이터베이스의 파일 경로가 다른 경우(예: 주 데이터베이스는 'F:' 드라이브에 있지만 보조 복제본을 호스트하는 서버 인스턴스에 F: 드라이브가 없는 경우) WITH 절에 MOVE 옵션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-145">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
4.  <span data-ttu-id="a412b-146">보조 데이터베이스 구성을 완료하려면 보조 데이터베이스를 가용성 그룹에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-146">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="a412b-147">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-147">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a412b-148">이러한 백업 및 복원 작업 수행 방법에 대한 자세한 내용은 이 섹션의 뒷부분에 나오는 [관련 백업 및 복원 태스크](#RelatedTasks)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-148">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this section.</span></span>  
  
###  <a name="related-backup-and-restore-tasks"></a><a name="RelatedTasks"></a><span data-ttu-id="a412b-149">관련 된 백업 및 복원 태스크</span><span class="sxs-lookup"><span data-stu-id="a412b-149">Related Backup and Restore Tasks</span></span>  
 <span data-ttu-id="a412b-150">**데이터베이스 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-150">**To create a database backup**</span></span>  
  
-   [<span data-ttu-id="a412b-151">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-151">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="a412b-152">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-152">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="a412b-153">**로그 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-153">**To create a log backup**</span></span>  
  
-   [<span data-ttu-id="a412b-154">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-154">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 <span data-ttu-id="a412b-155">**백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-155">**To restore backups**</span></span>  
  
-   [<span data-ttu-id="a412b-156">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-156">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="a412b-157">차등 데이터베이스 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-157">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="a412b-158">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-158">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="a412b-159">데이터베이스를 새 위치로 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-159">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a412b-160">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a412b-160">Using Transact-SQL</span></span>  
 <span data-ttu-id="a412b-161">**보조 데이터베이스를 준비하려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-161">**To prepare a secondary database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a412b-162">이 절차에 대한 예는 이 항목의 앞부분에 나오는 [예(Transact-SQL)](#ExampleTsql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-162">For an example of this procedure, see [Example (Transact-SQL)](#ExampleTsql), earlier in this topic.</span></span>  
  
1.  <span data-ttu-id="a412b-163">주 데이터베이스의 최근 전체 백업이 없는 경우 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-163">Unless you have a recent full backup of the primary database, connect to the server instance that hosts the primary replica and create a full database backup.</span></span> <span data-ttu-id="a412b-164">이 백업과 모든 후속 로그 백업을 권장 네트워크 공유에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-164">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="a412b-165">보조 복제본을 호스팅하는 서버 인스턴스에서 주 데이터베이스의 전체 데이터베이스 백업과 원하는 차등 백업을 복원한 다음 모든 후속 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-165">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by all subsequent log backups.</span></span> <span data-ttu-id="a412b-166">모든 복원 작업에 대해 WITH NORECOVERY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-166">Use WITH NORECOVERY for every restore operation.</span></span>  
  
     <span data-ttu-id="a412b-167">주 데이터베이스와 보조 데이터베이스의 파일 경로가 다른 경우(예: 주 데이터베이스는 'F:' 드라이브에 있지만 보조 복제본을 호스트하는 서버 인스턴스에 F: 드라이브가 없는 경우) WITH 절에 MOVE 옵션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-167">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
3.  <span data-ttu-id="a412b-168">필수 로그 백업 이후 주 데이터베이스에서 로그 백업이 수행된 경우 이러한 로그 백업도 보조 복제본을 호스팅하는 서버 인스턴스에 복사하여 가장 빠른 로그 백업부터 각각 보조 데이터베이스에 적용해야 합니다. 항상 RESTORE WITH NORECOVERY를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-168">If any log backups have been taken on the primary database since the required log backup, you must also copy these to the server instance that hosts the secondary replica and apply each of those log backups to the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a412b-169">주 데이터베이스를 방금 만들었으며 아직 로그 백업이 수행되지 않은 경우 또는 복구 모델이 방금 SIMPLE에서 FULL로 변경된 경우에는 로그 백업이 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-169">A log backup would not exist if the primary database has just been created and no log backup has been taken yet or if the recovery model has just been changed from simple to full.</span></span>  
  
4.  <span data-ttu-id="a412b-170">보조 데이터베이스 구성을 완료하려면 보조 데이터베이스를 가용성 그룹에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-170">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="a412b-171">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-171">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a412b-172">이러한 백업 및 복원 작업 수행 방법에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 [관련 백업 및 복원 태스크](#RelatedTasks)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-172">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this topic.</span></span>  
  
###  <a name="transact-sql-example"></a><a name="ExampleTsql"></a><span data-ttu-id="a412b-173">Transact-sql 예제</span><span class="sxs-lookup"><span data-stu-id="a412b-173">Transact-SQL Example</span></span>  
 <span data-ttu-id="a412b-174">다음 예에서는 보조 데이터베이스를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-174">The following example prepares a secondary database.</span></span> <span data-ttu-id="a412b-175">이 예에서는 기본적으로 단순 복구 모델을 사용하는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-175">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="a412b-176">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스를 사용하려면 전체 복구 모델을 사용하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-176">To use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```sql
    USE master;  
    GO  
    ALTER DATABASE MyDB1   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="a412b-177">데이터베이스 복구 모델을 SIMPLE에서 FULL로 변경한 후 보조 데이터베이스를 만드는 데 사용할 수 있는 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-177">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the secondary database.</span></span> <span data-ttu-id="a412b-178">복구 모델이 방금 변경되었으므로 WITH FORMAT 옵션을 지정하여 새 미디어 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-178">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="a412b-179">이 옵션은 단순 복구 모델에서 만든 이전 백업과 전체 복구 모델에서 만든 백업을 구분하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-179">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="a412b-180">이 예에서는 백업 파일(C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak)이 데이터베이스와 같은 드라이브에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-180">For the purpose of this example, the backup file (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a412b-181">프로덕션 데이터베이스의 경우에는 항상 별도의 디바이스에 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-181">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="a412b-182">주 복제본(`INSTANCE01`)을 호스팅하는 서버 인스턴스에서 다음과 같이 주 데이터베이스의 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-182">On the server instance that hosts the primary replica (`INSTANCE01`), create a full backup of the primary database as follows:</span></span>  
  
    ```sql
    BACKUP DATABASE MyDB1   
        TO DISK = 'C:\MyDB1.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="a412b-183">보조 복제본을 호스팅하는 서버 인스턴스에 전체 백업을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-183">Copy the full backup to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="a412b-184">RESTORE WITH NORECOVERY를 사용하여 보조 복제본을 호스팅하는 서버 인스턴스에 전체 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-184">Restore the full backup, using RESTORE WITH NORECOVERY, onto the server instance that hosts the secondary replica.</span></span> <span data-ttu-id="a412b-185">복원 명령은 주 데이터베이스와 보조 데이터베이스의 경로가 동일한지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-185">The restore command depends on whether the paths of primary and secondary databases are identical.</span></span>  
  
    -   <span data-ttu-id="a412b-186">**경로가 동일한 경우**</span><span class="sxs-lookup"><span data-stu-id="a412b-186">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="a412b-187">보조 복제본을 호스팅하는 컴퓨터에서 다음과 같이 전체 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-187">On the computer that hosts the secondary replica, restore the full backup as follows:</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1   
            FROM DISK = 'C:\MyDB1.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="a412b-188">**경로가 다른 경우**</span><span class="sxs-lookup"><span data-stu-id="a412b-188">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="a412b-189">보조 데이터베이스의 경로와 주 데이터베이스의 경로가 다른 경우(예: 드라이브 문자가 다른 경우) 보조 데이터베이스를 만들 때 복원 작업에 MOVE 절을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-189">If the path of the secondary database differs from the path of the primary database (for instance, their drive letters differ), creating the secondary database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="a412b-190">주 데이터베이스와 보조 데이터베이스의 경로 이름이 다른 경우 파일을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-190">If the path names of the primary and secondary databases differ, you cannot add a file.</span></span> <span data-ttu-id="a412b-191">이는 파일 추가 작업에 대한 로그를 받을 때 보조 복제본의 서버 인스턴스가 주 데이터베이스에서 사용되는 것과 동일한 경로에 새 파일을 배치하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-191">This is because on receiving the log for the add file operation, the server instance of the secondary replica attempts to place the new file in the same path as used by the primary database.</span></span>  
  
         <span data-ttu-id="a412b-192">예를 들어 다음 명령은 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 기본 인스턴스에 대한 데이터 디렉터리(C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA)에 있는 주 데이터베이스의 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-192">For example, the following command restores a backup of a primary database that resides in the data directory of the default instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA.</span></span> <span data-ttu-id="a412b-193">데이터베이스 복원 작업에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 다른 클러스터 노드에 있는 보조 복제본을 호스팅하는 (*AlwaysOn1*) 라는 원격 인스턴스의 데이터 디렉터리로 데이터베이스를 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-193">The restore database operation must move the database to the data directory of a remote instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] named  (*AlwaysOn1*), which hosts the secondary replica on another cluster node.</span></span> <span data-ttu-id="a412b-194">이 경우 데이터 및 로그 파일이 *C:\Program FILES\MICROSOFT SQL Server\MSSQL12.에 복원 됩니다. ALWAYSON1\MSSQL\DATA* 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-194">There, the data and log files are restored to the *C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA* directory .</span></span> <span data-ttu-id="a412b-195">복원 작업에서는 WITH NORECOVERY를 사용하여 보조 데이터베이스를 복원 중인 데이터베이스에 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-195">The restore operation uses WITH NORECOVERY, to leave the secondary database in the restoring database.</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1  
          FROM DISK='C:\MyDB1.bak'  
         WITH NORECOVERY,   
            MOVE 'MyDB1_Data' TO   
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.mdf',   
            MOVE 'MyDB1_Log' TO  
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="a412b-196">전체 백업을 복원한 후 주 데이터베이스에서 로그 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-196">After you restore the full backup, you must create a log backup on the primary database.</span></span> <span data-ttu-id="a412b-197">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 로그를 *E:\MyDB1_log.bak*라는 백업 파일에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-197">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement backs up the log to the a backup file named *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    BACKUP LOG MyDB1   
      TO DISK = 'E:\MyDB1_log.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="a412b-198">데이터베이스를 보조 복제본에 조인하려면 필수 로그 백업과 모든 후속 로그 백업을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-198">Before you can join the database to the secondary replica, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="a412b-199">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 *C:\MyDB1.bak*에서 첫 번째 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-199">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores the first log from *C:\MyDB1.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="a412b-200">데이터베이스에서 보조 복제본을 조인하기 전에 추가 로그 백업이 수행되면 해당 로그 백업도 RESTORE WITH NORECOVERY를 사용하여 보조 복제본을 호스팅하는 서버 인스턴스에 순서대로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-200">If any additional log backups occur before the database joins the secondary replica, you must also restore all of those log backups, in sequence, to the server instance that hosts the secondary replica using RESTORE WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="a412b-201">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 *E:\MyDB1_log.bak*에서 두 개의 로그를 추가로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-201">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores two additional logs from *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="a412b-202">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="a412b-202">Using PowerShell</span></span>  
 <span data-ttu-id="a412b-203">**보조 데이터베이스를 준비하려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-203">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="a412b-204">주 데이터베이스의 최근 백업을 만들어야 하는 경우 주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-204">If you need to create a recent backup of the primary database, change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="a412b-205">`Backup-SqlDatabase` cmdlet을 사용하여 각 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-205">Use the `Backup-SqlDatabase` cmdlet to create each of the backups.</span></span>  
  
3.  <span data-ttu-id="a412b-206">보조 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-206">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="a412b-207">각 주 서버의 데이터베이스와 로그 백업을 복원하려면 `restore-SqlDatabase` 복원 매개 변수를 지정하여 `NoRecovery` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-207">To restore the database and log backups of each primary database, use the `restore-SqlDatabase` cmdlet, specifying the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="a412b-208">또한 주 복제본을 호스팅하는 컴퓨터와 대상 보조 복제본을 호스팅하는 컴퓨터의 파일 경로가 다른 경우 `RelocateFile` 복원 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-208">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a412b-209">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-209">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="a412b-210">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-210">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
5.  <span data-ttu-id="a412b-211">보조 데이터베이스 구성을 완료하려면 보조 데이터베이스를 가용성 그룹에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-211">To complete configuration of the secondary database, you need to join it to the availability group.</span></span> <span data-ttu-id="a412b-212">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a412b-212">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="a412b-213">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="a412b-213">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="a412b-214">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="a412b-214">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="sample-backup-and-restore-script-and-command"></a><a name="ExamplePSscript"></a><span data-ttu-id="a412b-215">예제 백업 및 복원 스크립트 및 명령</span><span class="sxs-lookup"><span data-stu-id="a412b-215">Sample Backup and Restore Script and Command</span></span>  
 <span data-ttu-id="a412b-216">다음 PowerShell 명령은 전체 데이터베이스 백업과 트랜잭션 로그를 네트워크 공유에 백업하고 해당 공유에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-216">The following PowerShell commands back up a full database backup and transaction log to a network share and restore those backups from that share.</span></span> <span data-ttu-id="a412b-217">이 예에서는 데이터베이스를 복원할 파일 경로가 데이터베이스를 백업한 파일 경로와 동일한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-217">This example assumes that the file path to which the database is restored is the same as the file path on which the database was backed up.</span></span>  
  
```powershell
# Create database backup  
Backup-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -ServerInstance "SourceMachine\Instance"  
# Create log backup  
Backup-SqlDatabase -Database "MyDB1" -BackupAction "Log" -BackupFile "\\share\backups\MyDB1.trn" -ServerInstance "SourceMachine\Instance"  
# Restore database backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
# Restore log backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.trn" -RestoreAction "Log" -NoRecovery -ServerInstance "DestinationMachine\Instance"
```  
  
##  <a name="follow-up-after-preparing-a-secondary-database"></a><a name="FollowUp"></a><span data-ttu-id="a412b-218">후속 작업: 보조 데이터베이스를 준비한 후</span><span class="sxs-lookup"><span data-stu-id="a412b-218">Follow Up: After Preparing a Secondary Database</span></span>  
 <span data-ttu-id="a412b-219">보조 데이터베이스 구성을 완료하려면 새로 복원한 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-219">To complete configuration of the secondary database, join the newly restored database to the availability group.</span></span> <span data-ttu-id="a412b-220">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a412b-220">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a412b-221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a412b-221">See Also</span></span>  
 <span data-ttu-id="a412b-222">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a412b-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a412b-223">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a412b-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a412b-224">[RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a412b-224">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="a412b-225">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a412b-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="a412b-226">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="a412b-226">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
