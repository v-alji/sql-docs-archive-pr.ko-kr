---
title: 전체 데이터베이스 백업 만들기(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f406464680a1669133dc87bdfb231c644d33fbdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741096"
---
# <a name="create-a-full-database-backup-sql-server"></a><span data-ttu-id="fca15-102">전체 데이터베이스 백업 만들기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fca15-102">Create a Full Database Backup (SQL Server)</span></span>
  <span data-ttu-id="fca15-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 전체 데이터베이스 백업을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-103">This topic describes how to create a full database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca15-104">Azure Blob storage 서비스에 대 한 SQL Server 백업에 대 한 자세한 내용은 [Azure Blob Storage 서비스로 백업 및 복원 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="fca15-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fca15-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fca15-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fca15-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fca15-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fca15-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fca15-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fca15-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="fca15-109">보안</span><span class="sxs-lookup"><span data-stu-id="fca15-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fca15-110">**다음을 사용하여 전체 데이터베이스 백업을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="fca15-110">**To create a full database backup, using:**</span></span>  
  
     [<span data-ttu-id="fca15-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fca15-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fca15-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fca15-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="fca15-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fca15-113">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="fca15-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fca15-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fca15-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fca15-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fca15-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fca15-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fca15-117">명시적 또는 암시적 트랜잭션에서는 BACKUP 문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="fca15-118">최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 만든 백업은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-118">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fca15-119">자세한 내용은 [백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-119">For more information, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fca15-120">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fca15-120">Recommendations</span></span>  
  
-   <span data-ttu-id="fca15-121">데이터베이스가 커짐에 따라 전체 데이터베이스 백업은 완료하는 데 시간이 오래 걸리고 스토리지 공간도 더 많이 필요하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-121">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="fca15-122">따라서 큰 데이터베이스의 경우 *차등 데이터베이스 백업*으로 전체 데이터베이스 백업을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-122">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="fca15-123">자세한 내용은 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-123">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="fca15-124">[sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 시스템 저장 프로시저를 사용하여 전체 데이터베이스 백업의 크기를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-124">You can estimate the size of a full database backup by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure.</span></span>  
  
-   <span data-ttu-id="fca15-125">기본적으로 백업 작업을 성공적으로 수행할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 시스템 이벤트 로그에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-125">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="fca15-126">로그를 자주 백업하는 경우 이러한 성공 메시지는 바로 누적되므로 엄청난 오류 로그가 쌓여 다른 메시지를 찾기 힘들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-126">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="fca15-127">이 경우 스크립트가 이러한 로그 항목에 종속되지 않을 경우 추적 플래그 3226을 사용하여 이러한 항목을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-127">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="fca15-128">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-128">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fca15-129">보안</span><span class="sxs-lookup"><span data-stu-id="fca15-129">Security</span></span>  
 <span data-ttu-id="fca15-130">데이터베이스 백업에서 TRUSTWORTHY는 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-130">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="fca15-131">TRUSTWORTHY를 ON으로 설정하는 방법은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-131">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="fca15-132">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 `PASSWORD` 및 `MEDIAPASSWORD` 옵션은 백업을 만드는 데 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-132">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] the `PASSWORD` and `MEDIAPASSWORD` options are discontinued for creating backups.</span></span> <span data-ttu-id="fca15-133">암호를 사용하여 만든 백업은 계속 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-133">You can still restore backups created with passwords.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fca15-134">권한</span><span class="sxs-lookup"><span data-stu-id="fca15-134">Permissions</span></span>  
 <span data-ttu-id="fca15-135">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-135">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="fca15-136">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-136">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fca15-137">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-137">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="fca15-138">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-138">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="fca15-139">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-139">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fca15-140">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fca15-140">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca15-141">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 백업 태스크를 지정할 때 **스크립트** 단추를 클릭하고 스크립트 대상을 선택하여 해당되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-141">When you specify a back up task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and selecting a script destination.</span></span>  
  
#### <a name="to-back-up-a-database"></a><span data-ttu-id="fca15-142">데이터베이스를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="fca15-142">To back up a database</span></span>  
  
1.  <span data-ttu-id="fca15-143">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-143">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="fca15-144">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-144">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="fca15-145">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-145">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="fca15-146">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-146">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="fca15-147">`Database`목록 상자에서 데이터베이스 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-147">In the `Database` list box, verify the database name.</span></span> <span data-ttu-id="fca15-148">필요에 따라 목록에서 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-148">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="fca15-149">모든 복구 모델(**전체**, **대량 로그**또는 **단순**)에서 데이터베이스 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-149">You can perform a database backup for any recovery model (**FULL**, **BULK_LOGGED**, or **SIMPLE**).</span></span>  
  
6.  <span data-ttu-id="fca15-150">**백업 유형** 목록 상자에서 **전체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-150">In the **Backup type** list box, select **Full**.</span></span>  
  
     <span data-ttu-id="fca15-151">전체 데이터베이스 백업을 만든 후 차등 데이터베이스 백업을 만들 수 있습니다. 자세한 내용은 [차등 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-151">Note that after creating a full database backup, you can create a differential database backup; for more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="fca15-152">필요한 경우 **복사 전용 백업**을 선택하여 복사 전용 백업을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-152">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="fca15-153">*복사 전용 백업*은 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 시퀀스와 독립적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-153">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="fca15-154">자세한 내용은 [복사 전용 백업&#40;SQL Server&#41;](copy-only-backups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-154">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fca15-155">**차등** 옵션을 선택하는 경우 복사 전용 백업을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-155">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="fca15-156">**백업 구성 요소**에 대해를 클릭 `Database` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-156">For **Backup component**, click `Database`.</span></span>  
  
9. <span data-ttu-id="fca15-157">**이름** 입력란에 제시된 기본 백업 세트 이름을 사용하거나 다른 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-157">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
10. <span data-ttu-id="fca15-158">필요에 따라 **설명** 입력란에 백업 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-158">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
11. <span data-ttu-id="fca15-159">**디스크**, **테이프** 또는 **URL**을 클릭하여 백업 대상의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-159">Choose the type of backup destination by clicking **Disk**, **Tape** or **URL**.</span></span> <span data-ttu-id="fca15-160">**추가**를 클릭하면 단일 미디어 세트를 포함하는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-160">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="fca15-161">선택한 경로는 **백업 대상** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-161">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="fca15-162">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="fca15-163">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="fca15-164">미디어 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **미디어 옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-164">To view or select the media options, click **Media Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="fca15-165">다음 중 하나를 클릭하여 **미디어 덮어쓰기** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="fca15-166">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="fca15-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="fca15-167">이 옵션에는 **기존 백업 세트에 추가** 또는 **기존 백업 세트 모두 덮어쓰기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="fca15-168">자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-168">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="fca15-169">필요에 따라 **미디어 세트 이름 및 백업 세트 만료 확인** 을 선택하여 백업 작업에서 미디어 세트와 백업 세트가 만료되는 날짜와 시간을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="fca15-170">필요에 따라 **미디어 세트 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="fca15-171">이름을 지정하지 않는 경우 이름이 비어 있는 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="fca15-172">미디어 세트 이름을 지정하는 경우 미디어(테이프 또는 디스크)를 선택하여 실제 이름과 여기에서 입력한 이름이 일치하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fca15-173">**일반** 페이지에서 **URL** 을 백업 대상으로 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-173">This option is disabled if you selected **URL** as the backup destination in the **General** page.</span></span> <span data-ttu-id="fca15-174">자세한 내용은 [데이터베이스 백업&#40;미디어 옵션 페이지&#41;](back-up-database-media-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-174">For more information, see [Back Up Database &#40;Media Options Page&#41;](back-up-database-media-options-page.md)</span></span>  
        >   
        >  <span data-ttu-id="fca15-175">암호화를 사용할 계획인 경우 이 옵션을 선택하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-175">If you plan to use encryption, do not select this option.</span></span> <span data-ttu-id="fca15-176">이 옵션을 선택하면 **백업 옵션** 페이지의 암호화 옵션을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-176">If you select this option, the encryption options in the **Backup Options** page will be disabled.</span></span> <span data-ttu-id="fca15-177">기존 백업 세트에 추가할 때는 암호화가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-177">Encryption is not supported when appending to the existing backup set.</span></span>  
  
    -   <span data-ttu-id="fca15-178">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="fca15-178">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="fca15-179">이 옵션에는 **새 미디어 세트 이름** 입력란에 이름을 입력하고 필요에 따라 **새 미디어 세트 설명** 입력란에 미디어 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-179">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fca15-180">**일반** 페이지에서 **URL** 을 선택한 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-180">This option is disabled if you selected **URL** in the **General** page.</span></span> <span data-ttu-id="fca15-181">이러한 작업은 Azure storage로 백업할 때 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-181">These actions are not supported when backing up to Azure storage.</span></span>  
  
14. <span data-ttu-id="fca15-182">**안정성** 섹션에서 필요에 따라 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-182">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="fca15-183">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="fca15-183">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="fca15-184">**미디어에 쓰기 전에 체크섬 수행**및 필요에 따라 **체크섬 오류 발생 시 계속**.</span><span class="sxs-lookup"><span data-stu-id="fca15-184">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="fca15-185">체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-185">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="fca15-186">**일반** 페이지의 **대상** 섹션에서 지정한 대로 테이프 드라이브에 백업하는 경우 **백업 후 테이프 언로드** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-186">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="fca15-187">이 옵션을 클릭하면 **언로드 전에 테이프 되감기** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-187">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fca15-188">**일반** 페이지의 **백업 유형** 섹션에서 지정한 대로 트랜잭션 로그를 백업하지 않으면 **트랜잭션 로그** 섹션의 옵션이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-188">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. <span data-ttu-id="fca15-189">백업 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **백업 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-189">To view or select the backup options, click **Backup Options** in the **Select a page** pane.</span></span>  
  
17. <span data-ttu-id="fca15-190">백업 세트가 만료되고 명시적으로 만료 날짜 확인을 생략할 필요 없이 덮어쓸 수 있는 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-190">Specify when the backup set will expire and can be overwritten without explicitly skipping verification of the expiration data:</span></span>  
  
    -   <span data-ttu-id="fca15-191">백업 세트가 특정 일수가 지난 후에 만료되도록 하려면 **다음 이후** (기본 옵션)를 클릭한 다음 백업 세트를 만든 후 백업 세트가 만료되기까지 경과해야 하는 일수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-191">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="fca15-192">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-192">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="fca15-193">기본값은 **서버 속성** 대화 상자 (데이터베이스 설정 페이지)의 **백업 미디어 기본 보존 기간 (일)** 옵션에 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-193">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (Database Settings Page).</span></span> <span data-ttu-id="fca15-194">이 페이지에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-194">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="fca15-195">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-195">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
         <span data-ttu-id="fca15-196">백업 만료 날짜에 대한 자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-196">For more information about backup expiration dates, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="fca15-197">이상에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-197">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="fca15-198">기본적으로 백업은 **백업-압축 기본값** 서버 구성 옵션의 값에 따라 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-198">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="fca15-199">그러나 현재 서버 수준 기본값에 관계없이 **백업 압축**을 선택하여 백업을 압축하고, **백업 압축 안 함**을 선택하여 압축을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-199">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="fca15-200">**현재 백업 압축 기본값을 보거나 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="fca15-200">**To view or change the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="fca15-201">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="fca15-201">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. <span data-ttu-id="fca15-202">백업에 암호화를 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-202">Specify whether to use encryption for the backup.</span></span> <span data-ttu-id="fca15-203">암호화 단계에 사용할 암호화 알고리즘을 선택하고 기존 인증서 또는 비대칭 키 목록의 인증서 또는 비대칭 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-203">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="fca15-204">암호화는 SQL Server 2014 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-204">Encryption is supported in SQL Server 2014 or later.</span></span> <span data-ttu-id="fca15-205">암호화 옵션에 대한 자세한 내용은 [데이터베이스 백업&#40;백업 옵션 페이지&#41;](back-up-database-backup-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-205">For more details on the Encryption options, see [Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca15-206">또는 유지 관리 계획 마법사를 사용하여 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-206">Alternatively, you can use the Maintenance Plan Wizard to create database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fca15-207">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fca15-207">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-full-database-backup"></a><span data-ttu-id="fca15-208">전체 데이터베이스 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="fca15-208">To create a full database backup</span></span>  
  
1.  <span data-ttu-id="fca15-209">BACKUP DATABASE 문을 실행하여 전체 데이터베이스 백업을 만듭니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-209">Execute the BACKUP DATABASE statement to create the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="fca15-210">백업할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="fca15-210">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="fca15-211">전체 데이터베이스 백업이 기록되는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="fca15-211">The backup device where the full database backup is written.</span></span>  
  
     <span data-ttu-id="fca15-212">전체 데이터베이스 백업의 기본 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-212">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a full database backup is:</span></span>  
  
     <span data-ttu-id="fca15-213">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="fca15-213">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="fca15-214">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="fca15-214">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="fca15-215">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="fca15-215">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="fca15-216">옵션</span><span class="sxs-lookup"><span data-stu-id="fca15-216">Option</span></span>|<span data-ttu-id="fca15-217">Description</span><span class="sxs-lookup"><span data-stu-id="fca15-217">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="fca15-218">*database*</span><span class="sxs-lookup"><span data-stu-id="fca15-218">*database*</span></span>|<span data-ttu-id="fca15-219">백업할 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-219">Is the database that is to be backed up.</span></span>|  
    |<span data-ttu-id="fca15-220">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="fca15-220">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="fca15-221">백업 작업에 사용할 1-64개의 백업 디바이스 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-221">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="fca15-222">물리적 백업 디바이스를 지정하거나, 이미 정의된 경우 해당 논리적 백업 디바이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-222">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="fca15-223">물리적 백업 디바이스를 지정하려면 다음 DISK 또는 TAPE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-223">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="fca15-224">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="fca15-224">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="fca15-225">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-225">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="fca15-226">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="fca15-226">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="fca15-227">필요에 따라 *o*등과 같은 하나 이상의 추가 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-227">Optionally, specifies one or more additional options, *o*.</span></span> <span data-ttu-id="fca15-228">몇 가지 WITH의 기본 옵션에 대한 자세한 내용은 2단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-228">For information about some of the basic with options, see step 2.</span></span>|  
  
2.  <span data-ttu-id="fca15-229">필요에 따라 한 개 이상의 WITH 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-229">Optionally, specify one or more WITH options.</span></span> <span data-ttu-id="fca15-230">몇 가지 WITH의 기본 옵션은 이 페이지에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-230">A few basic WITH options are described here.</span></span> <span data-ttu-id="fca15-231">모든 WITH 옵션에 대한 자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-231">For information about all the WITH options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
    -   <span data-ttu-id="fca15-232">기본 백업 세트 WITH 옵션</span><span class="sxs-lookup"><span data-stu-id="fca15-232">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="fca15-233">{ COMPRESSION | NO_COMPRESSION }</span><span class="sxs-lookup"><span data-stu-id="fca15-233">{ COMPRESSION | NO_COMPRESSION }</span></span>  
         <span data-ttu-id="fca15-234">[!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] 이상에서만 사용 가능. 이 백업에서 [백업 압축](backup-compression-sql-server.md) 을 수행하고 서버 수준 기본값을 재정의할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-234">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] and later only, specifies whether [backup compression](backup-compression-sql-server.md) is performed on this backup, overriding the server-level default.</span></span>  
  
         <span data-ttu-id="fca15-235">ENCRYPTION (ALGORITHM, SERVER CERTIFICATE |ASYMMETRIC KEY)</span><span class="sxs-lookup"><span data-stu-id="fca15-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span></span>  
         <span data-ttu-id="fca15-236">SQL Server 2014 이상에서만 사용할 암호화 알고리즘과 암호화 보안에 사용할 인증서 또는 비대칭 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-236">In SQL Server 2014 or later only, specify the encryption algorithm to use, and the Certificate or Asymmetric key to use to secure the encryption.</span></span>  
  
         <span data-ttu-id="fca15-237">설명 **=** { **' *`text`* '**  |  **@** _text_variable_ }</span><span class="sxs-lookup"><span data-stu-id="fca15-237">DESCRIPTION **=** { **'*`text`*'** | **@**_text_variable_ }</span></span>  
         <span data-ttu-id="fca15-238">백업 세트를 설명하는 자유 형식의 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-238">Specifies the free-form text that describes the backup set.</span></span> <span data-ttu-id="fca15-239">문자열을 최대 255자까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-239">The string can have a maximum of 255 characters.</span></span>  
  
         <span data-ttu-id="fca15-240">이름 **=** { *backup_set_name*  |  **@** _backup_set_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="fca15-240">NAME **=** { *backup_set_name* | **@**_backup_set_name_var_ }</span></span>  
         <span data-ttu-id="fca15-241">백업 세트의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-241">Specifies the name of the backup set.</span></span> <span data-ttu-id="fca15-242">이름은 최대 128자까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-242">Names can have a maximum of 128 characters.</span></span> <span data-ttu-id="fca15-243">NAME을 지정하지 않으면 공백이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-243">If NAME is not specified, it is blank.</span></span>  
  
    -   <span data-ttu-id="fca15-244">기본 백업 세트 WITH 옵션</span><span class="sxs-lookup"><span data-stu-id="fca15-244">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="fca15-245">기본적으로 BACKUP은 기존 백업 세트를 유지하면서 기존 미디어 세트에 백업을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-245">By default, BACKUP appends the backup to an existing media set, preserving existing backup sets.</span></span> <span data-ttu-id="fca15-246">이것을 명시적으로 지정하려면 NOINIT 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-246">To explicitly specify this, use the NOINIT option.</span></span> <span data-ttu-id="fca15-247">기존 백업 세트에 추가하는 방법은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fca15-247">For information about appending to existing backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="fca15-248">또는 백업 미디어의 형식을 지정하기 위해 FORMAT 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-248">Alternatively, to format the backup media, use the FORMAT option:</span></span>  
  
         <span data-ttu-id="fca15-249">FORMAT [ **,** MEDIANAME **=** { *media_name*  |  **@** _media_name_variable_ }] [ **,** mediadescription **=** { *text*  |  **@** _text_variable_ }]</span><span class="sxs-lookup"><span data-stu-id="fca15-249">FORMAT [ **,** MEDIANAME**=** { *media_name* | **@**_media_name_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@**_text_variable_ } ]</span></span>  
         <span data-ttu-id="fca15-250">미디어를 처음 사용하거나 기존의 모든 데이터를 덮어쓰려고 하는 경우 FORMAT 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-250">Use the FORMAT clause when you are using media for the first time or you want to overwrite all existing data.</span></span> <span data-ttu-id="fca15-251">필요에 따라 새 미디어에 미디어 이름과 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-251">Optionally, assign the new media a media name and description.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fca15-252">BACKUP 문의 FORMAT 절을 사용하는 경우 백업 미디어에 이전에 저장된 백업이 모두 삭제되므로 각별히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-252">Use extreme caution when you are using the FORMAT clause of the BACKUP statement because this destroys any backups that were previously stored on the backup media.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="fca15-253">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fca15-253">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-backing-up-to-a-disk-device"></a><span data-ttu-id="fca15-254">A.</span><span class="sxs-lookup"><span data-stu-id="fca15-254">A.</span></span> <span data-ttu-id="fca15-255">디스크 디바이스에 백업</span><span class="sxs-lookup"><span data-stu-id="fca15-255">Backing up to a disk device</span></span>  
 <span data-ttu-id="fca15-256">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 을 사용하여 새 미디어 세트를 만들어 `FORMAT` 데이터베이스 전체를 디스크에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-256">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to disk, by using `FORMAT` to create a new media set.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a><span data-ttu-id="fca15-257">B.</span><span class="sxs-lookup"><span data-stu-id="fca15-257">B.</span></span> <span data-ttu-id="fca15-258">테이프 디바이스에 백업</span><span class="sxs-lookup"><span data-stu-id="fca15-258">Backing up to a tape device</span></span>  
 <span data-ttu-id="fca15-259">다음 예에서는 이전 백업에 백업을 추가하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]데이터베이스 전체를 테이프에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-259">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]database to tape, appending the backup to the previous backups.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a><span data-ttu-id="fca15-260">C.</span><span class="sxs-lookup"><span data-stu-id="fca15-260">C.</span></span> <span data-ttu-id="fca15-261">논리적 테이프 디바이스에 백업</span><span class="sxs-lookup"><span data-stu-id="fca15-261">Backing up to a logical tape device</span></span>  
 <span data-ttu-id="fca15-262">다음 예에서는 테이프 드라이브에 대한 논리적 백업 디바이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-262">The following example creates a logical backup device for a tape drive.</span></span> <span data-ttu-id="fca15-263">그런 다음 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스 전체를 이 디바이스에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-263">The example then backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to that device.</span></span>  
  
```sql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="fca15-264">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="fca15-264">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="fca15-265">`Backup-SqlDatabase` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-265">Use the `Backup-SqlDatabase` cmdlet.</span></span> <span data-ttu-id="fca15-266">전체 데이터베이스 백업 임을 명시적으로 나타내기 위해 **-backupaction** 매개 변수를 기본값인로 지정 `Database` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-266">To explicitly indicate that this is a full database backup, specify the **-BackupAction**  parameter with its default value, `Database`.</span></span> <span data-ttu-id="fca15-267">전체 데이터베이스 백업의 경우 이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-267">This parameter is optional for full database backups.</span></span>  
  
     <span data-ttu-id="fca15-268">다음 예에서는 서버 인스턴스 `MyDB` 의 기본 백업 위치에 `Computer\Instance`데이터베이스의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-268">The following example creates a full database backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span> <span data-ttu-id="fca15-269">선택 사항으로, 이 예에서는 `-BackupAction Database`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fca15-269">Optionally, this example specifies `-BackupAction Database`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 <span data-ttu-id="fca15-270">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="fca15-270">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="fca15-271">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="fca15-271">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fca15-272">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fca15-272">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fca15-273">데이터베이스 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fca15-273">Back Up a Database (SQL Server)</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fca15-274">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-274">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fca15-275">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-275">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="fca15-276">단순 복구 모델에서 데이터베이스 백업 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-276">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="fca15-277">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-277">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="fca15-278">데이터베이스를 새 위치로 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-278">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="fca15-279">유지 관리 계획 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="fca15-279">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="fca15-280">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fca15-280">See Also</span></span>  
 <span data-ttu-id="fca15-281">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-281">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="fca15-282">[트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-282">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="fca15-283">[미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-283">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="fca15-284">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fca15-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="fca15-285">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fca15-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="fca15-286">[데이터베이스 백업&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-286">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fca15-287">[데이터베이스 백업&#40;백업 옵션 페이지&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-287">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="fca15-288">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fca15-288">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="fca15-289">전체 데이터베이스 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fca15-289">Full Database Backups &#40;SQL Server&#41;</span></span>](full-database-backups-sql-server.md)  
