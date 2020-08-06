---
title: 백업 기록 및 헤더 정보(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup headers [SQL Server]
- history tables [SQL Server]
- file restores [SQL Server], status information
- backup sets [SQL Server], status information
- listing backed up databases
- status information [SQL Server], backups
- backing up [SQL Server], viewing backup sets
- restoring [SQL Server], history tables
- restoring databases [SQL Server], status information
- backups [SQL Server], status information
- headers [SQL Server]
- media headers [SQL Server]
- backup history tables [SQL Server]
- viewing backup information
- restoring files [SQL Server], viewing backup information
- restoring databases [SQL Server], history tables
- displaying backup information
- restoring files [SQL Server], status information
- historical information [SQL Server], backups
- database restores [SQL Server], history tables
- restore history tables [SQL Server]
- listing backed up files
ms.assetid: 799b9934-0ec2-4f43-960b-5c9653f18374
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ff1e75cc88e51de75af32bcd9d48860be52d5861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743323"
---
# <a name="backup-history-and-header-information-sql-server"></a><span data-ttu-id="ca3f1-102">백업 기록 및 헤더 정보(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-102">Backup History and Header Information (SQL Server)</span></span>
  <span data-ttu-id="ca3f1-103">서버 인스턴스에서 이루어지는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원 작업에 대한 전체 기록은 **msdb** 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-103">A complete history of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore operations on a server instance is stored in the **msdb** database.</span></span> <span data-ttu-id="ca3f1-104">이 항목에서는 백업 및 복원 기록 테이블에 대해 설명하고 백업 기록에 액세스하는 데 사용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-104">This topic introduces the backup and restore history tables and also the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are used to access backup history.</span></span> <span data-ttu-id="ca3f1-105">또한 이 항목에서는 데이터베이스와 트랜잭션 로그 파일을 나열하는 것이 유용한 경우에 대해 설명하고, 백업 헤더 정보와 미디어 헤더 정보를 사용하는 경우를 비교하여 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-105">The topic also discusses when listing database and transaction log files is useful and when to use media-header information compared to when to use backup-header information.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ca3f1-106">백업 및 복원 기록의 최근 변경 내용에 대한 손실 위험을 줄이려면 **msdb** 를 자주 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-106">To manage the risk of losing recent changes to your backup and restore history, back up **msdb** frequently.</span></span> <span data-ttu-id="ca3f1-107">백업해야 하는 시스템 데이터베이스에 대한 자세한 내용은 [시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-107">For information about which of the system databases you must back up, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
 <span data-ttu-id="ca3f1-108">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="ca3f1-109">백업 및 복원 기록 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3f1-109">Backup and Restore History Tables</span></span>](#BnRHistoryTables)  
  
-   [<span data-ttu-id="ca3f1-110">백업 기록에 액세스하는 Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="ca3f1-110">Transact-SQL Statements for Accessing Backup History</span></span>](#TsqlStatementsForBackupHistory)  
  
-   [<span data-ttu-id="ca3f1-111">데이터베이스 및 트랜잭션 로그 파일</span><span class="sxs-lookup"><span data-stu-id="ca3f1-111">Database and Transaction Log Files</span></span>](#ListDbTlogFiles)  
  
-   [<span data-ttu-id="ca3f1-112">미디어 헤더 정보</span><span class="sxs-lookup"><span data-stu-id="ca3f1-112">Media-Header Information</span></span>](#MediaHeader)  
  
-   [<span data-ttu-id="ca3f1-113">백업 헤더 정보</span><span class="sxs-lookup"><span data-stu-id="ca3f1-113">Backup-Header Information</span></span>](#BackupHeader)  
  
-   [<span data-ttu-id="ca3f1-114">미디어 헤더 정보 및 백업 헤더 정보 비교</span><span class="sxs-lookup"><span data-stu-id="ca3f1-114">Comparison of Media-Header and Backup-Header Information</span></span>](#CompareMediaHeaderBackupHeader)  
  
-   [<span data-ttu-id="ca3f1-115">백업 확인</span><span class="sxs-lookup"><span data-stu-id="ca3f1-115">Backup Verification</span></span>](#Verification)  
  
-   [<span data-ttu-id="ca3f1-116">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ca3f1-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="backup-and-restore-history-tables"></a><a name="BnRHistoryTables"></a> <span data-ttu-id="ca3f1-117">백업 및 복원 기록 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3f1-117">Backup and Restore History Tables</span></span>  
 <span data-ttu-id="ca3f1-118">이 섹션에서는 **msdb** 시스템 데이터베이스에 백업 및 복원 메타데이터를 저장하는 기록 테이블에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-118">This section introduces the history tables that store backup and restore metadata in the **msdb** system database.</span></span>  
  
|<span data-ttu-id="ca3f1-119">기록 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3f1-119">History table</span></span>|<span data-ttu-id="ca3f1-120">Description</span><span class="sxs-lookup"><span data-stu-id="ca3f1-120">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="ca3f1-121">backupfile</span><span class="sxs-lookup"><span data-stu-id="ca3f1-121">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="ca3f1-122">백업되는 각 데이터 또는 로그 파일에 대해 한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-122">Contains one row for each data or log file that is backed up.</span></span>|  
|[<span data-ttu-id="ca3f1-123">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="ca3f1-123">backupfilegroup</span></span>](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)|<span data-ttu-id="ca3f1-124">백업 세트의 각 파일 그룹에 대해 한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-124">Contains a row for each filegroup in a backup set.</span></span>|  
|[<span data-ttu-id="ca3f1-125">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="ca3f1-125">backupmediafamily</span></span>](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)|<span data-ttu-id="ca3f1-126">각 미디어 패밀리에 대해 한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-126">Contains one row for each media family.</span></span> <span data-ttu-id="ca3f1-127">미디어 패밀리가 미러된 미디어 세트에 있을 경우 이 미디어 패밀리에는 미디어 세트의 각 미러에 대한 별도의 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-127">If a media family resides in a mirrored media set, the family has a separate row for each mirror in the media set.</span></span>|  
|[<span data-ttu-id="ca3f1-128">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="ca3f1-128">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="ca3f1-129">각 백업 미디어 세트에 대해 한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-129">Contains one row for each backup media set.</span></span>|  
|[<span data-ttu-id="ca3f1-130">backupset</span><span class="sxs-lookup"><span data-stu-id="ca3f1-130">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="ca3f1-131">각 백업 세트마다 하나의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-131">Contains a row for each backup set.</span></span>|  
|[<span data-ttu-id="ca3f1-132">restorefile</span><span class="sxs-lookup"><span data-stu-id="ca3f1-132">restorefile</span></span>](/sql/relational-databases/system-tables/restorefile-transact-sql)|<span data-ttu-id="ca3f1-133">복원된 각 파일 그룹에 대해 하나의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-133">Contains one row for each restored file.</span></span> <span data-ttu-id="ca3f1-134">여기에는 파일 그룹 이름에 의해 간접적으로 복원된 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-134">This includes files restored indirectly by filegroup name.</span></span>|  
|[<span data-ttu-id="ca3f1-135">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="ca3f1-135">restorefilegroup</span></span>](/sql/relational-databases/system-tables/restorefilegroup-transact-sql)|<span data-ttu-id="ca3f1-136">복원된 각 파일 그룹에 대해 하나의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-136">Contains one row for each restored filegroup.</span></span>|  
|[<span data-ttu-id="ca3f1-137">restorehistory</span><span class="sxs-lookup"><span data-stu-id="ca3f1-137">restorehistory</span></span>](/sql/relational-databases/system-tables/restorehistory-transact-sql)|<span data-ttu-id="ca3f1-138">각 복원 작업에 대해 하나의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-138">Contains one row for each restore operation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ca3f1-139">복원을 수행하면 백업 기록 테이블 및 복원 기록 테이블이 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-139">When a restore is performed, backup history tables and restore history tables are modified.</span></span>  
  
##  <a name="transact-sql-statements-for-accessing-backup-history"></a><a name="TsqlStatementsForBackupHistory"></a> <span data-ttu-id="ca3f1-140">백업 기록에 액세스하는 Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="ca3f1-140">Transact-SQL Statements for Accessing Backup History</span></span>  
 <span data-ttu-id="ca3f1-141">복원 정보 문은 백업 기록 테이블에 저장된 정보와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-141">The restore information statements correspond with information stored in certain backup history tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ca3f1-142">RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY 및 RESTORE VERIFYONLY Transact-SQL 문에는 CREATE DATABASE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-142">The RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, and RESTORE VERIFYONLY Transact-SQL statements require CREATE DATABASE permission.</span></span> <span data-ttu-id="ca3f1-143">이 요구 사항을 통해 이전 버전보다 더욱 백업 파일의 보안을 유지하고 백업 정보를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-143">This requirement secures your backup files and protects your backup information more fully than in previous versions.</span></span> <span data-ttu-id="ca3f1-144">이 사용 권한에 대한 자세한 내용은 [GRANT 데이터베이스 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-144">For information about this permission, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
|<span data-ttu-id="ca3f1-145">정보 문</span><span class="sxs-lookup"><span data-stu-id="ca3f1-145">Information statement</span></span>|<span data-ttu-id="ca3f1-146">백업 기록 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3f1-146">Backup history table</span></span>|<span data-ttu-id="ca3f1-147">Description</span><span class="sxs-lookup"><span data-stu-id="ca3f1-147">Description</span></span>|  
|---------------------------|--------------------------|-----------------|  
|[<span data-ttu-id="ca3f1-148">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="ca3f1-148">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)|[<span data-ttu-id="ca3f1-149">backupfile</span><span class="sxs-lookup"><span data-stu-id="ca3f1-149">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="ca3f1-150">지정한 백업 세트에 포함된 데이터베이스와 로그 파일의 목록이 있는 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-150">Returns a result set that has a list of the database and log files that are contained in the specified backup set.</span></span><br /><br /> <span data-ttu-id="ca3f1-151">자세한 내용은 이 항목의 뒷부분에 나오는 "데이터베이스와 트랜잭션 로그 파일 목록 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-151">For more information, see "Listing Database and Transaction Log Files," later in this topic.</span></span>|  
|[<span data-ttu-id="ca3f1-152">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="ca3f1-152">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)|[<span data-ttu-id="ca3f1-153">backupset</span><span class="sxs-lookup"><span data-stu-id="ca3f1-153">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="ca3f1-154">특정 백업 디바이스의 모든 백업 세트에 대한 백업 헤더 정보를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-154">Retrieves all the backup header information for all backup sets on a particular backup device.</span></span> <span data-ttu-id="ca3f1-155">RESTORE HEADERONLY 실행 결과는 결과 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-155">The result from executing RESTORE HEADERONLY is a result set.</span></span><br /><br /> <span data-ttu-id="ca3f1-156">자세한 내용은 이 항목의 뒷부분에 나오는 "백업 헤더 정보 보기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-156">For more information, see "Viewing the Backup-Header Information," later in this topic.</span></span>|  
|[<span data-ttu-id="ca3f1-157">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="ca3f1-157">RESTORE LABELONLY</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)|[<span data-ttu-id="ca3f1-158">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="ca3f1-158">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="ca3f1-159">지정한 백업 디바이스의 백업 미디어에 대한 정보가 포함된 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-159">Returns a result set that contains information about the backup media on a specified backup device.</span></span><br /><br /> <span data-ttu-id="ca3f1-160">자세한 내용은 이 항목의 뒷부분에 나오는 "미디어 헤더 정보 보기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-160">For more information, see "Viewing the Media-Header Information," later in this topic.</span></span>|  
  
##  <a name="database-and-transaction-log-files"></a><a name="ListDbTlogFiles"></a> <span data-ttu-id="ca3f1-161">데이터베이스 및 트랜잭션 로그 파일</span><span class="sxs-lookup"><span data-stu-id="ca3f1-161">Database and Transaction Log Files</span></span>  
 <span data-ttu-id="ca3f1-162">백업에서 트랜잭션 로그 파일과 데이터베이스의 목록을 만들 때 표시되는 정보에는 논리적 이름, 물리적 이름, 파일 형식(데이터베이스나 로그), 파일 그룹 멤버, 파일 크기(바이트 단위), 최대 허용 파일 크기, 미리 정의된 파일 증가 크기(바이트 단위) 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-162">Information that is displayed when the database and transaction log files are listed in a backup includes the logical name, physical name, file type (database or log), filegroup membership, file size (in bytes), the maximum allowed file size, and the predefined file growth size (in bytes).</span></span> <span data-ttu-id="ca3f1-163">이 정보는 다음의 경우, 데이터베이스 백업을 복원하기 전에 데이터베이스 백업에서 파일 이름을 결정하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-163">This information is useful, in the following situations, to determine the names of the files in a database backup before you restore the database backup:</span></span>  
  
-   <span data-ttu-id="ca3f1-164">데이터베이스에 대한 파일이 하나 이상 있는 디스크 드라이브를 손실했을 경우</span><span class="sxs-lookup"><span data-stu-id="ca3f1-164">You have lost a disk drive that contains one or more of the files for a database.</span></span>  
  
     <span data-ttu-id="ca3f1-165">데이터베이스를 백업한 후에 만든 트랜잭션 로그 백업을 적용하고 해당 파일만 복원하거나 전체 데이터베이스를 복원할 때 어느 파일이 영향을 받았는지 알아내기 위해 데이터베이스 백업에서 파일 목록을 만든 다음 그 파일을 다른 드라이브로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-165">You can list the files in the database backup to determine which files were affected, and then restore those files onto a different drive when you restore the whole database; or restore just those files and apply any transaction log backups created since the database was backed up.</span></span>  
  
-   <span data-ttu-id="ca3f1-166">한 서버에서 다른 서버로 데이터베이스를 복원하는데 디렉터리 구조와 드라이브 매핑이 서버에 존재하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="ca3f1-166">You are restoring a database from one server onto another server, but the directory structure and drive mapping does not exist on the server.</span></span>  
  
     <span data-ttu-id="ca3f1-167">백업에 파일 목록을 만들면 어느 파일이 영향을 받았는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-167">Listing the files in the backup let you determine which files are affected.</span></span> <span data-ttu-id="ca3f1-168">예를 들어 백업에 포함된 파일을 드라이브 E에 복원해야 하는데 대상 서버에는 드라이브 E가 없는 경우 파일을 복원할 때 드라이브 Z 등의 다른 위치로 파일 위치를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-168">For example, the backup contains a file that it has to restore to drive E, but the destination server does not have a drive E. The file must be relocated to another location, such as drive Z, when the file is restored.</span></span>  
  
##  <a name="media-header-information"></a><a name="MediaHeader"></a> <span data-ttu-id="ca3f1-169">미디어 헤더 정보</span><span class="sxs-lookup"><span data-stu-id="ca3f1-169">Media-Header Information</span></span>  
 <span data-ttu-id="ca3f1-170">미디어 헤더를 보면 미디어의 백업이 아닌 미디어 자체에 대한 정보가 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-170">Viewing the media header displays information about the media itself, instead of about the backups on the media.</span></span> <span data-ttu-id="ca3f1-171">표시된 미디어 헤더 정보에는 미디어 이름, 설명, 미디어 헤더를 만든 소프트웨어 이름, 미디어 헤더가 쓰여진 날짜 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-171">Media header information that is displayed includes the media name, description, name of the software that created the media header, and the date the media header was written.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca3f1-172">미디어 헤더를 신속하게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-172">Viewing the media header is quick.</span></span>  
  
 <span data-ttu-id="ca3f1-173">자세한 내용은 이 항목의 뒷부분에 나오는 [미디어 헤더 정보 및 백업 헤더 정보 비교](#CompareMediaHeaderBackupHeader)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-173">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
##  <a name="backup-header-information"></a><a name="BackupHeader"></a> <span data-ttu-id="ca3f1-174">백업 헤더 정보</span><span class="sxs-lookup"><span data-stu-id="ca3f1-174">Backup-Header Information</span></span>  
 <span data-ttu-id="ca3f1-175">백업 헤더를 보면 미디어에 있는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 비[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 세트에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-175">Viewing the backup header displays information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup sets on the media.</span></span> <span data-ttu-id="ca3f1-176">표시된 정보에는 사용한 백업 디바이스의 유형, 백업 유형(예: 데이터베이스, 트랜잭션, 파일 또는 차등 데이터베이스), 백업 시작과 중지 시간/날짜 정보 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-176">Information that is displayed includes the types of backup devices that are used, the types of backup (for example, database, transaction, file, or differential database), and backup start and stop date/time information.</span></span> <span data-ttu-id="ca3f1-177">이 정보는 테이프에서 복원할 백업 세트나 미디어에 포함된 백업을 결정할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-177">This information is useful when you have to determine which backup set on the tape to restore, or the backups that are contained on the media.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca3f1-178">미디어에서 각 백업에 관한 정보를 표시하기 위해 전체 미디어를 검사해야 하기 때문에 고용량 테이프의 경우 백업 헤더 정보를 보는 데 시간이 많이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-178">Viewing backup header information can take a long time for high-capacity tapes, because the whole media must be scanned to display information about each backup on the media.</span></span>  
  
 <span data-ttu-id="ca3f1-179">자세한 내용은 이 항목의 뒷부분에 나오는 [미디어 헤더 정보 및 백업 헤더 정보 비교](#CompareMediaHeaderBackupHeader)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-179">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
### <a name="which-backup-set-to-restore"></a><span data-ttu-id="ca3f1-180">복원할 백업 세트</span><span class="sxs-lookup"><span data-stu-id="ca3f1-180">Which Backup Set to Restore</span></span>  
 <span data-ttu-id="ca3f1-181">복원할 백업 세트를 식별하는 데 백업 헤더 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-181">You can use information in the backup header to identify which backup set to restore.</span></span> <span data-ttu-id="ca3f1-182">데이터베이스 엔진은 백업 미디어에 있는 각 백업 세트에 번호를 매깁니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-182">The Database Engine numbers each backup set on the backup media.</span></span> <span data-ttu-id="ca3f1-183">이렇게 하면 미디어에서 백업 세트의 위치를 사용하여 복원할 백업 세트를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-183">This lets you identify the backup set you want to restore by using its position on the media.</span></span> <span data-ttu-id="ca3f1-184">예를 들어 다음 미디어에는 3개의 백업 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-184">For example, the following media contains three backup sets.</span></span>  
  
 <span data-ttu-id="ca3f1-185">![SQL Server 백업 세트를 포함하는 백업 미디어](../../database-engine/media/bnr-media-backup-sets.gif "SQL Server 백업 세트를 포함하는 백업 미디어")</span><span class="sxs-lookup"><span data-stu-id="ca3f1-185">![Backup media containing SQL Server backup sets](../../database-engine/media/bnr-media-backup-sets.gif "Backup media containing SQL Server backup sets")</span></span>  
  
 <span data-ttu-id="ca3f1-186">특정 백업 세트를 복원하려면 복원할 백업 세트의 위치 번호를 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-186">To restore a specific backup set, specify the position number of the backup set you want to restore.</span></span> <span data-ttu-id="ca3f1-187">예를 들어 두 번째 백업 세트를 복원하려면 2를 복원할 백업 세트로 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-187">For example, to restore the second backup set, specify 2 as the backup set to restore.</span></span>  
  
##  <a name="comparison-of-media-header-and-backup-header-information"></a><a name="CompareMediaHeaderBackupHeader"></a> <span data-ttu-id="ca3f1-188">미디어 헤더 정보 및 백업 헤더 정보 비교</span><span class="sxs-lookup"><span data-stu-id="ca3f1-188">Comparison of Media-Header and Backup-Header Information</span></span>  
 <span data-ttu-id="ca3f1-189">다음 그림에서는 백업 헤더를 볼 때와 미디어 헤더 정보를 볼 때의 차이점을 예를 들어 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-189">The following illustration provides an example of the differences between viewing backup-header and media-header information.</span></span> <span data-ttu-id="ca3f1-190">미디어 헤더를 얻으려면 테이프의 시작에서만 정보를 검색해야 하고</span><span class="sxs-lookup"><span data-stu-id="ca3f1-190">Obtaining the media header requires retrieving information from only the start of the tape.</span></span> <span data-ttu-id="ca3f1-191">백업 헤더를 얻으려면 모든 백업 세트의 헤더를 볼 수 있도록 전체 테이프를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-191">Obtaining the backup header requires scanning the whole tape to look at the header of every backup set.</span></span>  
  
 <span data-ttu-id="ca3f1-192">![3개의 SQL Server 백업 세트를 포함하는 미디어 세트](../../database-engine/media/bnr-media-label.gif "3개의 SQL Server 백업 세트를 포함하는 미디어 세트")</span><span class="sxs-lookup"><span data-stu-id="ca3f1-192">![Media set containing three SQL Server backup sets](../../database-engine/media/bnr-media-label.gif "Media set containing three SQL Server backup sets")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca3f1-193">여러 미디어 패밀리가 있는 미디어 세트를 사용하면 모든 미디어 패밀리에 미디어 헤더와 백업 세트가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-193">When you use media sets that have multiple media families, the media header and backup set are written to all media families.</span></span> <span data-ttu-id="ca3f1-194">따라서 이러한 보고 작업에 하나의 미디어 패밀리만 제공하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-194">Therefore, you only have to provide a single media family for these reporting operations.</span></span>  
  
 <span data-ttu-id="ca3f1-195">미디어 헤더를 보는 방법은 이 항목의 앞부분에 나오는 "미디어 헤더 정보 보기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-195">For information about how to view the media-header, see "Viewing the Media-Header Information," earlier in this topic.</span></span>  
  
 <span data-ttu-id="ca3f1-196">백업 디바이스에서 모든 백업 세트의 백업 헤더 정보를 보는 방법은 이 항목의 앞부분에 나오는 "백업 헤더 정보 보기"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-196">For information about how to view the backup header information for all backup sets on a backup device, see "Viewing the Backup-Header Information," earlier in this topic.</span></span>  
  
##  <a name="backup-verification"></a><a name="Verification"></a> <span data-ttu-id="ca3f1-197">백업 확인</span><span class="sxs-lookup"><span data-stu-id="ca3f1-197">Backup Verification</span></span>  
 <span data-ttu-id="ca3f1-198">백업 확인은 필수는 아니지만 유용한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-198">Although not required, verifying a backup is a useful practice.</span></span> <span data-ttu-id="ca3f1-199">백업 확인은 백업의 모든 파일을 읽을 수 있고 저장할 수 있으며 백업을 사용해야 할 때 복원할 수 있도록 백업이 물리적으로 손상되지 않고 그대로인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-199">Verifying a backup checks that the backup is intact physically, to ensure that all the files in the backup are readable and can be restored, and that you can restore your backup in the event you need to use it.</span></span> <span data-ttu-id="ca3f1-200">백업 확인은 백업의 데이터 구조를 확인하지 않는다는 점을 이해하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-200">It is important to understand that verifying a backup does not verify the structure of the data on the backup.</span></span> <span data-ttu-id="ca3f1-201">그러나 WITH CHECKSUMS를 사용하여 백업을 만든 경우 WITH CHECKSUMS를 사용하여 백업을 확인하면 백업 데이터의 안정성을 정확히 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca3f1-201">However, if the backup was created using WITH CHECKSUMS, verifying the backup using WITH CHECKSUMS can provide a good indication of the reliability of the data on the backup.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ca3f1-202">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ca3f1-202">Related Tasks</span></span>  
 <span data-ttu-id="ca3f1-203">**백업 및 복원 기록 테이블에서 오래된 행을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-203">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="ca3f1-204">sp_delete_backuphistory&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="ca3f1-205">**백업 및 복원 기록 테이블에서 특정 데이터베이스에 대한 모든 행을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-205">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="ca3f1-206">sp_delete_database_backuphistory&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="ca3f1-207">**백업 세트의 데이터와 로그 파일을 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-207">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="ca3f1-208">RESTORE FILELISTONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
-   <span data-ttu-id="ca3f1-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ca3f1-210">**미디어 헤더 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-210">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="ca3f1-211">RESTORE LABELONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="ca3f1-212">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-212">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="ca3f1-213">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-213">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="ca3f1-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ca3f1-215">**백업 헤더 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-215">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="ca3f1-216">RESTORE HEADERONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="ca3f1-217">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-217">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="ca3f1-218">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-218">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="ca3f1-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ca3f1-220">**백업 및 복원 기록 테이블에서 오래된 행을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-220">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="ca3f1-221">sp_delete_backuphistory&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="ca3f1-222">**백업 및 복원 기록 테이블에서 특정 데이터베이스에 대한 모든 행을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-222">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="ca3f1-223">sp_delete_database_backuphistory&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="ca3f1-224">**미디어 헤더 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-224">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="ca3f1-225">RESTORE LABELONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="ca3f1-226">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-226">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="ca3f1-227">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-227">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="ca3f1-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ca3f1-229">**백업 헤더 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-229">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="ca3f1-230">RESTORE HEADERONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="ca3f1-231">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-231">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="ca3f1-232">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-232">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="ca3f1-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="ca3f1-234">**백업 세트의 파일을 보려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-234">**To view the files in a backup set**</span></span>  
  
-   [<span data-ttu-id="ca3f1-235">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="ca3f1-236">RESTORE HEADERONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
 <span data-ttu-id="ca3f1-237">**백업을 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="ca3f1-237">**To verify a backup**</span></span>  
  
-   [<span data-ttu-id="ca3f1-238">RESTORE VERIFYONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
-   <span data-ttu-id="ca3f1-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ca3f1-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3f1-240">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca3f1-240">See Also</span></span>  
 <span data-ttu-id="ca3f1-241">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca3f1-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ca3f1-242">[미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca3f1-242">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="ca3f1-243">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca3f1-243">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="ca3f1-244">[미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca3f1-244">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 [<span data-ttu-id="ca3f1-245">백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3f1-245">Possible Media Errors During Backup and Restore &#40;SQL Server&#41;</span></span>](possible-media-errors-during-backup-and-restore-sql-server.md)  
  
  
