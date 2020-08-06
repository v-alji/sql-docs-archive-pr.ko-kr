---
title: 사용자 데이터베이스 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- editions [SQL Server], moving databases between
- moving full-text catalogs
- scheduled disk maintenace [SQL Server]
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- moving user databases
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: ad9a4e92-13fb-457d-996a-66ffc2d55b79
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c2b82c3bec13c82aa30aebd175ef78f8136ee04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650096"
---
# <a name="move-user-databases"></a><span data-ttu-id="dbaf6-102">사용자 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="dbaf6-102">Move User Databases</span></span>
  <span data-ttu-id="dbaf6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문의 FILENAME 절에 새 파일 위치를 지정하여 사용자 데이터베이스의 데이터, 로그 및 전체 텍스트 카탈로그 파일을 새 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move the data, log, and full-text catalog files of a user database to a new location by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="dbaf6-104">이 방법은 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 내에서 데이터베이스 파일을 이동하는 경우에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-104">This method applies to moving database files within the same instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbaf6-105">데이터베이스를 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스나 다른 서버로 이동하려면 [백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 작업이나 [분리/연결](move-a-database-using-detach-and-attach-transact-sql.md)작업을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-105">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach operations](move-a-database-using-detach-and-attach-transact-sql.md).</span></span>  
  
## <a name="considerations"></a><span data-ttu-id="dbaf6-106">고려 사항</span><span class="sxs-lookup"><span data-stu-id="dbaf6-106">Considerations</span></span>  
 <span data-ttu-id="dbaf6-107">데이터베이스를 다른 서버 인스턴스로 이동하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 데이터베이스의 일부 또는 모든 메타데이터를 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-107">When you move a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all the metadata for the database.</span></span> <span data-ttu-id="dbaf6-108">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-108">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="dbaf6-109">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 일부 기능 중 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 데이터베이스 파일의 정보를 저장하는 방법이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-109">Some features of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] change the way that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores information in the database files.</span></span> <span data-ttu-id="dbaf6-110">이러한 기능은 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-110">These features are restricted to specific editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbaf6-111">이러한 기능을 포함하는 데이터베이스는 이러한 기능이 지원되지 않는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전으로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-111">A database that contains these features cannot be moved to an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support them.</span></span> <span data-ttu-id="dbaf6-112">현재 데이터베이스에 설정된 모든 버전별 기능 목록을 보려면 sys.dm_db_persisted_sku_features 동적 관리 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-112">Use the sys.dm_db_persisted_sku_features dynamic management view to list all edition-specific features that are enabled in the current database.</span></span>  
  
 <span data-ttu-id="dbaf6-113">이 항목의 절차를 사용하려면 데이터베이스 파일의 논리적 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-113">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="dbaf6-114">논리적 파일 이름을 구하려면 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 카탈로그 뷰의 name 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-114">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="dbaf6-115">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서 시작하여 전체 텍스트 카탈로그는 파일 시스템에 저장되는 대신 데이터베이스에 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-115">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], full-text catalogs are integrated into the database rather than being stored in the file system.</span></span> <span data-ttu-id="dbaf6-116">데이터베이스를 이동할 때 전체 텍스트 카탈로그는 이제 자동으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-116">The full-text catalogs now move automatically when you move a database.</span></span>  
  
## <a name="planned-relocation-procedure"></a><span data-ttu-id="dbaf6-117">계획된 재배치 절차</span><span class="sxs-lookup"><span data-stu-id="dbaf6-117">Planned Relocation Procedure</span></span>  
 <span data-ttu-id="dbaf6-118">계획된 재배치의 일부로 데이터 또는 로그 파일을 이동하려면 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-118">To move a data or log file as part of a planned relocation, follow these steps:</span></span>  
  
1.  <span data-ttu-id="dbaf6-119">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-119">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET OFFLINE;  
    ```  
  
2.  <span data-ttu-id="dbaf6-120">파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-120">Move the file or files to the new location.</span></span>  
  
3.  <span data-ttu-id="dbaf6-121">이동한 각 파일에 대해 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-121">For each file moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name, FILENAME = 'new_path\os_file_name' );  
    ```  
  
4.  <span data-ttu-id="dbaf6-122">다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-122">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET ONLINE;  
    ```  
  
5.  <span data-ttu-id="dbaf6-123">다음 쿼리를 실행하여 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-123">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="relocation-for-scheduled-disk-maintenance"></a><span data-ttu-id="dbaf6-124">예약된 디스크 유지 관리를 위한 재배치</span><span class="sxs-lookup"><span data-stu-id="dbaf6-124">Relocation for Scheduled Disk Maintenance</span></span>  
 <span data-ttu-id="dbaf6-125">예약된 디스크 유지 관리 프로세스의 일부로 파일을 재배치하려면 다음 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-125">To relocate a file as part of a scheduled disk maintenance process, follow these steps:</span></span>  
  
1.  <span data-ttu-id="dbaf6-126">이동할 각 파일에 대해 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-126">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
2.  <span data-ttu-id="dbaf6-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 중지하거나 시스템을 종료하여 유지 관리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-127">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="dbaf6-128">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-128">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="dbaf6-129">파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-129">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="dbaf6-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스나 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-130">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="dbaf6-131">자세한 내용은 [데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)를 참조하세요</span><span class="sxs-lookup"><span data-stu-id="dbaf6-131">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)</span></span>  
  
5.  <span data-ttu-id="dbaf6-132">다음 쿼리를 실행하여 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-132">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="failure-recovery-procedure"></a><span data-ttu-id="dbaf6-133">오류 복구 절차</span><span class="sxs-lookup"><span data-stu-id="dbaf6-133">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="dbaf6-134">하드웨어 오류로 인해 파일을 이동해야 하는 경우 다음 단계에 따라 파일을 새 위치에 재배치합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-134">If a file must be moved because of a hardware failure, use the following steps to relocate the file to a new location.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbaf6-135">데이터베이스가 주의 대상 모드에 있거나 복구할 수 없는 상태여서 시작할 수 없는 경우에는 sysadmin 고정 역할의 멤버만 파일을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-135">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="dbaf6-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 시작된 경우 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-136">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="dbaf6-137">명령 프롬프트에서 다음 명령 중 하나를 입력하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 마스터 전용 복구 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-137">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span>  
  
    -   <span data-ttu-id="dbaf6-138">기본(MSSQLSERVER) 인스턴스의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-138">For the default (MSSQLSERVER) instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="dbaf6-139">명명된 인스턴스의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-139">For a named instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="dbaf6-140">자세한 내용은 [SQL Server 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-140">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="dbaf6-141">이동할 각 파일에 대해 **sqlcmd** 명령 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 를 사용하여 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-141">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
     <span data-ttu-id="dbaf6-142">**sqlcmd** 유틸리티 사용 방법은 [sqlcmd 유틸리티 사용](../scripting/sqlcmd-use-the-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-142">For more information about how to use the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="dbaf6-143">**sqlcmd** 유틸리티 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-143">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="dbaf6-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-144">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="dbaf6-145">파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-145">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="dbaf6-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-146">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbaf6-147">예를 들어 `NET START MSSQLSERVER`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-147">For example, run: `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="dbaf6-148">다음 쿼리를 실행하여 파일 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-148">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="examples"></a><span data-ttu-id="dbaf6-149">예</span><span class="sxs-lookup"><span data-stu-id="dbaf6-149">Examples</span></span>  
 <span data-ttu-id="dbaf6-150">다음 예에서는 계획된 재배치의 일부로 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 로그 파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="dbaf6-150">The following example moves the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] log file to a new location as part of a planned relocation.</span></span>  
  
```  
USE master;  
GO  
-- Return the logical file name.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
GO  
ALTER DATABASE AdventureWorks2012 SET OFFLINE;  
GO  
-- Physically move the file to a new location.  
-- In the following statement, modify the path specified in FILENAME to  
-- the new location of the file on your server.  
ALTER DATABASE AdventureWorks2012   
    MODIFY FILE ( NAME = AdventureWorks2012_Log,   
                  FILENAME = 'C:\NewLoc\AdventureWorks2012_Log.ldf');  
GO  
ALTER DATABASE AdventureWorks2012 SET ONLINE;  
GO  
--Verify the new location.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbaf6-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbaf6-151">See Also</span></span>  
 <span data-ttu-id="dbaf6-152">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="dbaf6-153">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="dbaf6-154">[데이터베이스 분리 및 연결&#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-154">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="dbaf6-155">[시스템 데이터베이스 이동](system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-155">[Move System Databases](system-databases.md) </span></span>  
 <span data-ttu-id="dbaf6-156">[데이터베이스 파일 이동](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-156">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="dbaf6-157">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="dbaf6-158">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbaf6-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="dbaf6-159">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="dbaf6-159">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
