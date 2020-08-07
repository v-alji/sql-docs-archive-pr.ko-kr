---
title: 백업 및 복원으로 데이터베이스 복사 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], back up and restore
- restoring databases [SQL Server], previous SQL Server versions
- database restores [SQL Server], copying databases
- restoring databases [SQL Server], onto another server instance
- restoring [SQL Server], onto another server instance
- backing up databases [SQL Server], copying databases
- database backups [SQL Server], copying databases
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8ffed36767f961f7482aa0dccf755118c80c019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731716"
---
# <a name="copy-databases-with-backup-and-restore"></a><span data-ttu-id="80062-102">백업 및 복원으로 데이터베이스 복사</span><span class="sxs-lookup"><span data-stu-id="80062-102">Copy Databases with Backup and Restore</span></span>
  <span data-ttu-id="80062-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 사용하여 만든 사용자 데이터베이스 백업을 복원하여 새 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create a new database by restoring a backup of a user database created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span> <span data-ttu-id="80062-104">그러나 이전 **버전을 사용하여 만든**master **,** model **및** msdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 통해 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-104">However, backups of **master**, **model** and **msdb** that were created by using an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="80062-105">또한 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 백업을 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복원할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-105">Also, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] backups cannot be restored by any earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="80062-106">는 이전 버전과는 다른 기본 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-106">uses a different default path than earlier versions.</span></span> <span data-ttu-id="80062-107">따라서 이전 버전의 기본 위치에 만든 데이터베이스 백업을 복원하려면 MOVE 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-107">Therefore, to restore backups of a database created in the default location of earlier versions you must use the MOVE option.</span></span> <span data-ttu-id="80062-108">새 기본 경로에 대한 자세한 내용은 [SQL Server 기본 인스턴스 및 명명된 인스턴스의 파일 위치](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="80062-108">For information about the new default path see [File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span> <span data-ttu-id="80062-109">데이터베이스 파일을 이동하는 방법은 이 항목의 뒷부분에 나오는 "데이터베이스 파일 이동"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="80062-109">For more information about moving database files, see "Moving the Database Files," later in this topic.</span></span>  
  
## <a name="general-steps-for-using-backup-and-restore-to-copy-a-database"></a><span data-ttu-id="80062-110">백업과 복원을 사용하여 데이터베이스를 복사하는 일반적인 단계</span><span class="sxs-lookup"><span data-stu-id="80062-110">General Steps for Using Backup and Restore to Copy a Database</span></span>  
 <span data-ttu-id="80062-111">백업과 복원을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 인스턴스로 데이터베이스를 복사할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되는 모든 플랫폼이 원본 컴퓨터 및 대상 컴퓨터가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-111">When you use backup and restore to copy a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the source and destination computers can be any platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs.</span></span>  
  
 <span data-ttu-id="80062-112">일반적인 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-112">The general steps are:</span></span>  
  
1.  <span data-ttu-id="80062-113">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상의 인스턴스에 있을 수 있는 원본 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-113">Back up the source database, which can reside on an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="80062-114">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 실행 중인 컴퓨터가 *원본 컴퓨터*입니다.</span><span class="sxs-lookup"><span data-stu-id="80062-114">The computer on which this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running is the *source computer*.</span></span>  
  
2.  <span data-ttu-id="80062-115">데이터베이스를 복사 하려는 컴퓨터 ( *대상 컴퓨터*)에서 데이터베이스를 복원 하려는의 인스턴스에 연결 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="80062-115">On the computer to which you want to copy the database (the *destination computer*), connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you plan to restore the database.</span></span> <span data-ttu-id="80062-116">필요한 경우 대상 서버 인스턴스에 원본 데이터베이스의 백업에 사용된 것과 같은 백업 디바이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80062-116">If needed, on the destination server instance, create the same backup devices as used to the backup of the source databases.</span></span>  
  
3.  <span data-ttu-id="80062-117">대상 컴퓨터에서 원본 데이터베이스의 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-117">Restore the backup of the source database on the destination computer.</span></span> <span data-ttu-id="80062-118">데이터베이스를 복원하면 자동으로 모든 데이터베이스 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="80062-118">Restoring the database automatically creates all of the database files.</span></span>  
  
 <span data-ttu-id="80062-119">다음 항목에서는 이 프로세스에 영향을 줄 수 있는 추가 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-119">The following topics address additional considerations that may affect this process.</span></span>  
  
## <a name="before-you-restore-database-files"></a><span data-ttu-id="80062-120">데이터베이스 파일을 복원하기 전 고려 사항</span><span class="sxs-lookup"><span data-stu-id="80062-120">Before You Restore Database Files</span></span>  
 <span data-ttu-id="80062-121">데이터베이스를 복원하면 복원 중인 데이터베이스에 필요한 데이터베이스 파일이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="80062-121">Restoring a database automatically creates the database files that are needed by the restoring database.</span></span> <span data-ttu-id="80062-122">기본적으로 복원 프로세스 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 만든 파일은 원본 컴퓨터에 있는 원본 데이터베이스의 백업 파일과 같은 이름과 경로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-122">By default, the files that are created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] during the restoration process use the same names and paths as the backup files from the original database on the source computer.</span></span>  
  
 <span data-ttu-id="80062-123">원하는 경우 데이터베이스를 복원할 때 디바이스 매핑, 파일 이름 또는 데이터베이스 복원 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-123">Optionally, when restoring the database, you can specify the device mapping, file names, or path for the restoring database.</span></span> <span data-ttu-id="80062-124">이 방법은 다음과 같은 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-124">This might be necessary in the following situations:</span></span>  
  
-   <span data-ttu-id="80062-125">원래 컴퓨터에서 데이터베이스에 사용된 디렉터리 구조나 드라이브 매핑이 다른 컴퓨터에는 존재하지 않는 경우.</span><span class="sxs-lookup"><span data-stu-id="80062-125">The directory structure or drive mapping used by the database on the original computer not exist on the other computer.</span></span> <span data-ttu-id="80062-126">예를 들어 백업에 포함된 파일이 기본적으로 E 드라이브에 복원되는데 대상 컴퓨터에는 E 드라이브가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-126">For example, perhaps the backup contains a file that would be restored to drive E by default, but the destination computer lacks a drive E.</span></span>  
  
-   <span data-ttu-id="80062-127">대상 위치의 공간이 부족한 경우.</span><span class="sxs-lookup"><span data-stu-id="80062-127">The target location might have insufficient space.</span></span>  
  
-   <span data-ttu-id="80062-128">복원 대상에 있는 데이터베이스 이름을 다시 사용하며, 데이터베이스의 모든 파일 이름이 백업 집합의 데이터베이스 파일 이름과 동일하게 지정되는 경우에는 다음 중 한 가지 현상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-128">You are reusing a database name that exists on the restore destination and any of its files is named the same as a database file in the backup set, one of the following occurs:</span></span>  
  
    -   <span data-ttu-id="80062-129">기존 데이터베이스 파일을 덮어쓸 수 있는 경우 덮어씁니다. 이 경우 다른 데이터베이스 이름이 속하는 파일에는 아무런 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-129">If the existing database file can be overwritten, it will be overwritten (this would not affect a file that belongs to a different database name).</span></span>  
  
    -   <span data-ttu-id="80062-130">기존 파일을 덮어쓸 수 없는 경우 복원 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-130">If the existing file cannot be overwritten, a restore error would occur.</span></span>  
  
 <span data-ttu-id="80062-131">오류 및 의도하지 않은 결과를 방지하려면 복원 작업 전에 [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) 기록 테이블을 통해 복원하려는 백업에서 데이터베이스 및 로그 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-131">To avoid errors and unintended consequences, before the restore operation, you can use the [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) history table to find out the database and log files in the backup you plan to restore.</span></span>  
  
## <a name="moving-the-database-files"></a><span data-ttu-id="80062-132">데이터베이스 파일 이동</span><span class="sxs-lookup"><span data-stu-id="80062-132">Moving the Database Files</span></span>  
 <span data-ttu-id="80062-133">위에서 설명한 이유 때문에 데이터베이스 백업 내의 파일을 대상 컴퓨터에 복원할 수 없으면 복원 도중에 이 파일을 새 위치로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-133">If the files within the database backup cannot be restored onto the destination computer because of the reasons mentioned earlier, it is necessary to move the files to a new location while they are being restored.</span></span> <span data-ttu-id="80062-134">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="80062-134">For example:</span></span>  
  
-   <span data-ttu-id="80062-135">이전 버전의 기본 위치에 만든 백업에서 데이터베이스를 복원하려는 경우</span><span class="sxs-lookup"><span data-stu-id="80062-135">You want to restore a database from backups created in the default location of the earlier version.</span></span>  
  
-   <span data-ttu-id="80062-136">용량을 고려해야 하기 때문에 백업의 데이터베이스 파일 일부를 다른 드라이브로 복원해야 할 경우.</span><span class="sxs-lookup"><span data-stu-id="80062-136">It may be necessary to restore some of the database files in the backup to a different drive because of capacity considerations.</span></span> <span data-ttu-id="80062-137">이는 조직 내에 있는 대부분의 컴퓨터가 디스크 드라이브의 크기 및 번호가 다르고 소프트웨어 구성이 같지 않기 때문에 흔히 있는 일입니다.</span><span class="sxs-lookup"><span data-stu-id="80062-137">This is likely to be a common occurrence because most computers within an organization do not have the same number and size of disk drives or identical software configurations.</span></span>  
  
-   <span data-ttu-id="80062-138">테스트용으로 같은 컴퓨터에 기존 데이터베이스의 복사본을 만들 경우.</span><span class="sxs-lookup"><span data-stu-id="80062-138">It may be necessary to create a copy of an existing database on the same computer for testing purposes.</span></span> <span data-ttu-id="80062-139">이 경우 원래 데이터베이스에 대한 데이터베이스 파일이 이미 존재하므로 복사 작업 중에 데이터베이스 복사본을 만들 때 파일 이름을 다르게 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-139">In this case, the database files for the original database already exist, so different file names need to be specified when the database copy is created during the restore operation.</span></span>  
  
 <span data-ttu-id="80062-140">자세한 내용은 이 항목의 뒷부분에 나오는 "파일과 파일 그룹을 새 위치로 복원"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="80062-140">For more information, see "To restore files and filegroups to a new location," later in this topic.</span></span>  
  
## <a name="changing-the-database-name"></a><span data-ttu-id="80062-141">데이터베이스 이름 변경</span><span class="sxs-lookup"><span data-stu-id="80062-141">Changing the Database Name</span></span>  
 <span data-ttu-id="80062-142">데이터베이스를 대상 컴퓨터에 복원할 때 데이터베이스를 먼저 복원한 다음 이름을 수동으로 변경하지 않고도 데이터베이스 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-142">The name of the database can be changed as it is restored to the destination computer, without having to restore the database first and then change the name manually.</span></span> <span data-ttu-id="80062-143">예를 들어 데이터베이스 이름을 **Sales** 에서 **SalesCopy** 로 변경하면 이것이 데이터베이스의 복사본임을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-143">For example, it may be necessary to change the database name from **Sales** to **SalesCopy** to indicate that this is a copy of a database.</span></span>  
  
 <span data-ttu-id="80062-144">데이터베이스를 복원할 때 명시적으로 제공한 데이터베이스 이름은 자동으로 새 데이터베이스의 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80062-144">The database name that is explicitly supplied when you restore a database is used automatically as the new database name.</span></span> <span data-ttu-id="80062-145">데이터베이스 이름이 기존에 존재하지 않기 때문에 백업에 있는 파일을 사용하여 새 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80062-145">Because the database name does not already exist, a new one is created by using the files in the backup.</span></span>  
  
## <a name="when-upgrading-a-database-by-using-restore"></a><span data-ttu-id="80062-146">복원을 사용하여 데이터베이스를 업그레이드하는 경우</span><span class="sxs-lookup"><span data-stu-id="80062-146">When Upgrading a Database by Using Restore</span></span>  
 <span data-ttu-id="80062-147">이전 버전에서 백업을 복원할 때는 백업에 있는 각각의 전체 텍스트 카탈로그의 경로(드라이브 및 디렉터리)가 대상 컴퓨터에 존재하는지 미리 알아 두면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80062-147">When restoring backups from an earlier version, it is helpful to know in advance whether the path (drive and directory) of each of the full-text catalogs in a backup exists on the destination computer.</span></span> <span data-ttu-id="80062-148">카탈로그 파일을 비롯하여 백업에 있는 모든 파일의 논리적 이름, 물리적 이름, 경로 및 파일 이름을 나열하려면 RESTORE FILELISTONLY FROM *<backup_device>* 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-148">To list the logical names and physical names, path and file name) of every file in a backup, including the catalog files, use a RESTORE FILELISTONLY FROM *<backup_device>* statement.</span></span> <span data-ttu-id="80062-149">자세한 내용은 [RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80062-149">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
 <span data-ttu-id="80062-150">대상 컴퓨터에 같은 경로가 존재하지 않을 경우 다음 두 가지 대체 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-150">If the same path does not exist on the destination computer, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="80062-151">대상 컴퓨터에 원본과 동일한 드라이브/디렉터리 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80062-151">Create the equivalent drive/directory mapping on the destination computer.</span></span>  
  
-   <span data-ttu-id="80062-152">RESTORE DATABASE 문 안에 WITH MOVE 절을 사용하여 복원 작업을 하는 중에 카탈로그 파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="80062-152">Move the catalog files to a new location during the restore operation, by using the WITH MOVE clause in your RESTORE DATABASE statement.</span></span> <span data-ttu-id="80062-153">자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 통해 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-153">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
 <span data-ttu-id="80062-154">다른 전체 텍스트 인덱스 업그레이드 옵션에 대한 자세한 내용은 [전체 텍스트 검색 업그레이드](../search/upgrade-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80062-154">For information about alternative options for upgrading full-text indexes, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
## <a name="database-ownership"></a><span data-ttu-id="80062-155">데이터베이스 소유권</span><span class="sxs-lookup"><span data-stu-id="80062-155">Database Ownership</span></span>  
 <span data-ttu-id="80062-156">데이터베이스를 다른 컴퓨터에서 복원할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 또는 복원 작업을 시작하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자가 자동으로 새 데이터베이스 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80062-156">When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user who initiates the restore operation becomes the owner of the new database automatically.</span></span> <span data-ttu-id="80062-157">데이터베이스를 복원할 때 시스템 관리자나 새 데이터베이스 소유자는 데이터베이스 소유권을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-157">When the database is restored, the system administrator or the new database owner can change database ownership.</span></span> <span data-ttu-id="80062-158">데이터베이스가 무단으로 복원되는 것을 방지하려면 미디어 또는 백업 세트에 암호를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="80062-158">To prevent unauthorized restoration of a database, use media or backup set passwords.</span></span>  
  
## <a name="managing-metadata-when-restoring-to-another-server-instance"></a><span data-ttu-id="80062-159">다른 서버 인스턴스로 복원 시 메타데이터 관리</span><span class="sxs-lookup"><span data-stu-id="80062-159">Managing Metadata When Restoring to Another Server Instance</span></span>  
 <span data-ttu-id="80062-160">데이터베이스를 다른 서버 인스턴스로 복원하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 로그인, 작업 등 데이터베이스의 일부 또는 모든 메타데이터를 다른 서버 인스턴스에서 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80062-160">When you restore a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="80062-161">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80062-161">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="80062-162">**백업 세트의 데이터와 로그 파일을 보려면**</span><span class="sxs-lookup"><span data-stu-id="80062-162">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="80062-163">RESTORE FILELISTONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
 <span data-ttu-id="80062-164">**파일과 파일 그룹을 새 위치로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-164">**To restore files and filegroups to a new location**</span></span>  
  
-   [<span data-ttu-id="80062-165">새 위치로 파일 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-165">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="80062-166">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-166">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="80062-167">**기존 파일에서 파일과 파일 그룹을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-167">**To restore files and filegroups over existing files**</span></span>  
  
-   [<span data-ttu-id="80062-168">기존 파일에서 파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-168">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 <span data-ttu-id="80062-169">**새 이름으로 데이터베이스를 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-169">**To restore a database with a new name**</span></span>  
  
-   [<span data-ttu-id="80062-170">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-170">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="80062-171">**중단된 복원 작업을 다시 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-171">**To restart an interrupted restore operation**</span></span>  
  
-   [<span data-ttu-id="80062-172">중단된 복원 작업 다시 시작&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-172">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](../backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 <span data-ttu-id="80062-173">**데이터베이스의 소유자를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-173">**To change the owner of a database**</span></span>  
  
-   [<span data-ttu-id="80062-174">sp_changedbowner&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-174">sp_changedbowner &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-changedbowner-transact-sql)  
  
 <span data-ttu-id="80062-175">**SMO(SQL Server 관리 개체)를 사용하여 데이터베이스를 복사하려면**</span><span class="sxs-lookup"><span data-stu-id="80062-175">**To copy a database by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## <a name="see-also"></a><span data-ttu-id="80062-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80062-176">See Also</span></span>  
 <span data-ttu-id="80062-177">[데이터베이스를 다른 서버로 복사](copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="80062-177">[Copy Databases to Other Servers](copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="80062-178">[SQL Server 기본 인스턴스 및 명명된 인스턴스의 파일 위치](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="80062-178">[File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="80062-179">[RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="80062-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 [<span data-ttu-id="80062-180">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="80062-180">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
