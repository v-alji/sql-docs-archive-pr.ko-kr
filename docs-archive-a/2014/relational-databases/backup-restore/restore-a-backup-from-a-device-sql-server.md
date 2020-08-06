---
title: 디바이스에서 백업 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50d7f7b8e255aea470a1065df669c0cc3169a8dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730759"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a><span data-ttu-id="6bad7-102">디바이스에서 백업 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6bad7-102">Restore a Backup from a Device (SQL Server)</span></span>
  <span data-ttu-id="6bad7-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 디바이스에서 백업을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-103">This topic describes how to restore a backup from a device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bad7-104">Azure Blob storage 서비스에 대 한 SQL Server 백업에 대 한 자세한 내용은 [Azure Blob Storage 서비스로 백업 및 복원 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bad7-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="6bad7-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6bad7-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6bad7-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6bad7-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6bad7-107">보안</span><span class="sxs-lookup"><span data-stu-id="6bad7-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6bad7-108">**다음을 사용하여 디바이스에서 백업을 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="6bad7-108">**To restore a backup from a device, using:**</span></span>  
  
     [<span data-ttu-id="6bad7-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bad7-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6bad7-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6bad7-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bad7-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6bad7-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6bad7-112">보안</span><span class="sxs-lookup"><span data-stu-id="6bad7-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6bad7-113">권한</span><span class="sxs-lookup"><span data-stu-id="6bad7-113">Permissions</span></span>  
 <span data-ttu-id="6bad7-114">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-114">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="6bad7-115">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-115">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="6bad7-116">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-116">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="6bad7-117">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-117">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6bad7-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6bad7-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="6bad7-119">디바이스에서 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="6bad7-119">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="6bad7-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6bad7-121">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="6bad7-122">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-122">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="6bad7-123">원하는 복원 작업의 유형(**데이터베이스**, **파일 및 파일 그룹**또는 **트랜잭션 로그**)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-123">Click the type of restore operation you want (**Database**, **Files and Filegroups**, or **Transaction Log**).</span></span> <span data-ttu-id="6bad7-124">이렇게 하면 해당되는 복원 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-124">This opens the corresponding restore dialog box.</span></span>  
  
5.  <span data-ttu-id="6bad7-125">**일반** 페이지의 **복원 원본** 섹션에서 **디바이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-125">On the **General** page, in the **Restore source** section, click **From device**.</span></span>  
  
6.  <span data-ttu-id="6bad7-126">**디바이스** 입력란에 대한 찾아보기 단추를 클릭합니다. **백업 지정** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-126">Click the browse button for the **From device** text box, which opens the **Specify Backup** dialog box.</span></span>  
  
7.  <span data-ttu-id="6bad7-127">**백업 미디어** 입력란에서 **백업 디바이스**를 선택하고 **추가** 단추를 클릭하여 **백업 디바이스 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-127">In the **Backup media** text box, select **Backup Device**, and click the **Add** button to open the **Select Backup Device** dialog box.</span></span>  
  
8.  <span data-ttu-id="6bad7-128">**백업 디바이스** 입력란에서 복원 작업에 사용하려는 디바이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-128">In the **Backup device** text box, select the device you want to use for the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6bad7-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6bad7-129">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="6bad7-130">디바이스에서 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="6bad7-130">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="6bad7-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6bad7-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6bad7-133">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문에서 백업 작업에 사용할 논리적 백업 디바이스나 물리적 백업 디바이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-133">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify a logical or physical backup device to use for the backup operation.</span></span> <span data-ttu-id="6bad7-134">이 예에서는 실제 이름이 `Z:\SQLServerBackups\AdventureWorks2012.bak`인 디스크 파일로부터 복원을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad7-134">This example restores from a disk file that has the physical name `Z:\SQLServerBackups\AdventureWorks2012.bak`.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bad7-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bad7-135">See Also</span></span>  
 <span data-ttu-id="6bad7-136">[RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bad7-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="6bad7-137">[RESTORE HEADERONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bad7-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="6bad7-138">[RESTORE LABELONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bad7-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="6bad7-139">[RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bad7-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="6bad7-140">[단순 복구 모델에서 데이터베이스 백업 복원&#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-140">[Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span></span>  
 <span data-ttu-id="6bad7-141">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-141">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="6bad7-142">[차등 데이터베이스 백업 복원&#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-142">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="6bad7-143">[데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-143">[Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="6bad7-144">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-144">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="6bad7-145">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bad7-145">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="6bad7-146">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6bad7-146">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
