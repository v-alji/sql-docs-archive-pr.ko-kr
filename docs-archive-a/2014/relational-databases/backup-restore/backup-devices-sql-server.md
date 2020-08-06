---
title: 백업 디바이스(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8abbba087679d263c00484764ecf445d6e5a006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743327"
---
# <a name="backup-devices-sql-server"></a><span data-ttu-id="4fcb8-102">백업 디바이스(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-102">Backup Devices (SQL Server)</span></span>
  <span data-ttu-id="4fcb8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 백업 작업 중에 백업되는 데이터인 *백업*은 물리적 백업 디바이스에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-103">During a backup operation on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the backed up data (the *backup*) is written to a physical backup device.</span></span> <span data-ttu-id="4fcb8-104">이 물리적 백업 디바이스는 미디어 세트의 첫 번째 백업을 디바이스에 기록할 때 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-104">This physical backup device is initialized when the first backup in a media set is written to it.</span></span> <span data-ttu-id="4fcb8-105">하나 이상의 백업 디바이스 세트에서의 백업이 미디어 세트 하나를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-105">The backups on a set of one or more backup devices compose a single media set.</span></span>  
  
 <span data-ttu-id="4fcb8-106">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="4fcb8-107">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="4fcb8-107">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="4fcb8-108">디스크 백업 디바이스 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-108">Using Disk Backup Devices</span></span>](#DiskBackups)  
  
-   [<span data-ttu-id="4fcb8-109">테이프 장치 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-109">Using Tape Devices</span></span>](#TapeDevices)  
  
-   [<span data-ttu-id="4fcb8-110">논리적 백업 디바이스 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-110">Using a Logical Backup Device</span></span>](#LogicalBackupDevice)  
  
-   [<span data-ttu-id="4fcb8-111">미러된 백업 미디어 세트</span><span class="sxs-lookup"><span data-stu-id="4fcb8-111">Mirrored Backup Media Sets</span></span>](#MirroredMediaSets)  
  
-   [<span data-ttu-id="4fcb8-112">SQL Server 백업 보관</span><span class="sxs-lookup"><span data-stu-id="4fcb8-112">Archiving SQL Server Backups</span></span>](#Archiving)  
  
-   [<span data-ttu-id="4fcb8-113">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4fcb8-113">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="4fcb8-114">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="4fcb8-114">Terms and Definitions</span></span>  
 <span data-ttu-id="4fcb8-115">백업 디스크</span><span class="sxs-lookup"><span data-stu-id="4fcb8-115">backup disk</span></span>  
 <span data-ttu-id="4fcb8-116">백업 파일이 하나 이상 포함된 하드 디스크나 다른 디스크 스토리지 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-116">A hard disk or other disk storage media that contains one or more backup files.</span></span> <span data-ttu-id="4fcb8-117">백업 파일은 일반적인 운영 체제 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-117">A backup file is a regular operating system file.</span></span>  
  
 <span data-ttu-id="4fcb8-118">미디어 세트(media set)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-118">media set</span></span>  
 <span data-ttu-id="4fcb8-119">고정된 유형과 개수의 백업 디바이스를 사용하는 백업 미디어, 테이프 또는 디스크 파일을 정렬하여 모아 놓은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-119">An ordered collection of backup media, tapes or disk files, that uses a fixed type and number of backup devices.</span></span> <span data-ttu-id="4fcb8-120">미디어 세트에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-120">For more information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="4fcb8-121">물리적 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="4fcb8-121">physical backup device</span></span>  
 <span data-ttu-id="4fcb8-122">운영 체제에서 제공하는 테이프 드라이브나 디스크 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-122">Either a tape drive or a disk file that is provided by the operating system.</span></span> <span data-ttu-id="4fcb8-123">백업은 1개에서 64개까지의 백업 디바이스에 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-123">A backup can be written to from 1 to 64 backup devices.</span></span> <span data-ttu-id="4fcb8-124">백업에 여러 개의 백업 디바이스가 필요한 경우 모든 디바이스 유형은 디스크 또는 테이프 중 하나로 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-124">If a backup requires multiple backup devices, the devices all must correspond to a single type of device (disk or tape).</span></span>  
  
 <span data-ttu-id="4fcb8-125">디스크나 테이프뿐 아니라 Azure Blob Storage 서비스에도 SQL Server 백업을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-125">SQL Server Backups can also be written to Azure Blob storage service in addition to disk or tape.</span></span>  
  
##  <a name="using-disk-backup-devices"></a><a name="DiskBackups"></a><span data-ttu-id="4fcb8-126">디스크 백업 장치 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-126">Using Disk Backup Devices</span></span>  
 <span data-ttu-id="4fcb8-127">**섹션 내용**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-127">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="4fcb8-128">실제 이름을 사용하여 백업 파일 지정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-128">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>](#BackupFileUsingPhysicalName)  
  
-   [<span data-ttu-id="4fcb8-129">디스크 백업 파일의 경로 지정</span><span class="sxs-lookup"><span data-stu-id="4fcb8-129">Specifying the Path of a Disk Backup File</span></span>](#BackupFileDiskPath)  
  
-   [<span data-ttu-id="4fcb8-130">네트워크 공유의 파일로 백업</span><span class="sxs-lookup"><span data-stu-id="4fcb8-130">Backing Up to a File on a Network Share</span></span>](#NetworkShare)  
  
 <span data-ttu-id="4fcb8-131">백업 작업에서 미디어 세트에 백업을 추가하는 동안 디스크 파일이 꽉 차면 백업 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-131">If a disk file fills while a backup operation is appending a backup to the media set, the backup operation fails.</span></span> <span data-ttu-id="4fcb8-132">백업 파일의 최대 크기는 디스크 디바이스에서 사용 가능한 디스크 공간에 의해 결정되므로 백업 디스크 디바이스에 적합한 크기는 백업 크기에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-132">The maximum size of a backup file is determined by the free disk space available on the disk device; therefore, the appropriate size for a backup disk device depends on the size of your backups.</span></span>  
  
 <span data-ttu-id="4fcb8-133">디스크 백업 디바이스는 ATA 드라이브와 같은 간단한 디스크 디바이스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-133">A disk backup device could be a simple disk device, such as an ATA drive.</span></span> <span data-ttu-id="4fcb8-134">또는 드라이브의 전체 디스크를 빈 디스크로 투명하게 교체할 수 있는 핫 스왑 가능 디스크 드라이브를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-134">Alternatively, you could use a hot-swappable disk drive that would let you transparently replace a full disk on the drive with an empty disk.</span></span> <span data-ttu-id="4fcb8-135">백업 디스크는 서버의 로컬 디스크나 공유 네트워크 리소스인 원격 디스크일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-135">A backup disk can be a local disk on the server or a remote disk that is a shared network resource.</span></span> <span data-ttu-id="4fcb8-136">원격 디스크를 사용하는 방법은 이 항목의 뒷부분에 나오는 [네트워크 공유의 파일로 백업](#NetworkShare)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-136">For information about how to use a remote disk, see [Backing Up to a File on a Network Share](#NetworkShare), later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4fcb8-137">관리 도구는 디스크 파일에 타임스탬프 이름을 자동으로 생성하기 때문에 디스크 백업 디바이스를 유연하게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-137">management tools are very flexible at handling disk backup devices because they automatically generate a time-stamped name on the disk file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4fcb8-138">데이터베이스 데이터 및 로그 디스크가 아닌 다른 디스크를 백업 디스크로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-138">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="4fcb8-139">이렇게 하면 데이터 또는 로그 디스크가 실패할 경우 백업에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-139">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="specifying-a-backup-file-by-using-its-physical-name-transact-sql"></a><a name="BackupFileUsingPhysicalName"></a><span data-ttu-id="4fcb8-140">실제 이름을 사용 하 여 백업 파일 지정 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-140">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="4fcb8-141">물리적 디바이스 이름을 사용하여 백업 파일을 지정하기 위한 기본 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-141">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup file by using its physical device name is:</span></span>  
  
 <span data-ttu-id="4fcb8-142">BACKUP DATABASE *database_name*</span><span class="sxs-lookup"><span data-stu-id="4fcb8-142">BACKUP DATABASE *database_name*</span></span>  
  
 <span data-ttu-id="4fcb8-143">TO DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-143">TO DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="4fcb8-144">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="4fcb8-144">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 <span data-ttu-id="4fcb8-145">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문에서 물리적 디스크 디바이스를 지정하기 위한 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-145">To specify a physical disk device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="4fcb8-146">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="4fcb8-146">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="4fcb8-147">FROM DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-147">FROM DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="4fcb8-148">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-148">For example,</span></span>  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="specifying-the-path-of-a-disk-backup-file"></a><a name="BackupFileDiskPath"></a><span data-ttu-id="4fcb8-149">디스크 백업 파일의 경로 지정</span><span class="sxs-lookup"><span data-stu-id="4fcb8-149">Specifying the Path of a Disk Backup File</span></span>  
 <span data-ttu-id="4fcb8-150">백업 파일을 지정할 경우 전체 경로 및 파일 이름을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-150">When you are specifying a backup file, you should enter its full path and file name.</span></span> <span data-ttu-id="4fcb8-151">파일에 백업할 때 파일 이름이나 상대 경로만 지정하면 백업 파일이 기본 백업 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-151">If you specify only the file name or a relative path when you are backing up to a file, the backup file is put in the default backup directory.</span></span> <span data-ttu-id="4fcb8-152">기본 백업 디렉터리는 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup입니다. 여기서 *n* 은 서버 인스턴스의 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-152">The default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup, where *n* is the number of the server instance.</span></span> <span data-ttu-id="4fcb8-153">따라서 기본 서버 인스턴스의 기본 백업 디렉터리는 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-153">Therefore, for the default server instance, the default backup directory is: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="4fcb8-154">특히 스크립트에서 모호성을 피하기 위해 모든 DISK 절에 백업 디렉터리의 경로를 명시적으로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-154">To avoid ambiguity, especially in scripts, we recommend that you explicitly specify the path of the backup directory in every DISK clause.</span></span> <span data-ttu-id="4fcb8-155">그러나 쿼리 편집기를 사용할 경우 이는 그다지 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-155">However, this is less important when you are using Query Editor.</span></span> <span data-ttu-id="4fcb8-156">쿼리 편집기를 사용할 경우 백업 파일이 확실히 기본 백업 디렉터리에 있으면 DISK 절에서 경로를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-156">In that case, if you are sure that the backup file resides in the default backup directory, you can omit the path from a DISK clause.</span></span> <span data-ttu-id="4fcb8-157">예를 들어 다음 `BACKUP` 문은 기본 백업 디렉터리에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-157">For example, the following `BACKUP` statement backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to the default backup directory.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4fcb8-158">기본 위치는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer** 아래의 **BackupDirectory**레지스트리 키에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-158">The default location is stored in the **BackupDirectory** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**.</span></span>  
  
###  <a name="backing-up-to-a-file-on-a-network-share"></a><a name="NetworkShare"></a><span data-ttu-id="4fcb8-159">네트워크 공유의 파일로 백업</span><span class="sxs-lookup"><span data-stu-id="4fcb8-159">Backing Up to a File on a Network Share</span></span>  
 <span data-ttu-id="4fcb8-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 원격 디스크 파일에 액세스하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에 네트워크 공유에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access a remote disk file, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account must have access to the network share.</span></span> <span data-ttu-id="4fcb8-161">여기에는 백업 작업에서 네트워크 공유에 쓰는 데 필요한 사용 권한과 복원 작업에서 네트워크 공유를 읽는 데 필요한 사용 권한이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-161">This includes having the permissions needed for backup operations to write to the network share and for restore operations to read from it.</span></span> <span data-ttu-id="4fcb8-162">네트워크 드라이브 및 사용 권한의 가용성은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되고 있는 컨텍스트에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-162">The availability of network drives and permissions depends on the context is which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running:</span></span>  
  
-   <span data-ttu-id="4fcb8-163">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 도메인 사용자 계정으로 실행 중일 때 네트워크 드라이브에 백업하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되고 있는 세션에서 공유 드라이브를 네트워크 드라이브로 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-163">To back up to a network drive when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in a domain user account, the shared drive must be mapped as a network drive in the session where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="4fcb8-164">명령줄에서 Sqlservr.exe를 시작하면 로그인 세션에서 매핑한 모든 네트워크 드라이브가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-164">If you start Sqlservr.exe from command line, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sees any network drives you have mapped in your login session.</span></span>  
  
-   <span data-ttu-id="4fcb8-165">Sqlservr.exe를 서비스로 실행하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 로그인 세션과 관계없는 별도의 세션으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-165">When you run Sqlservr.exe as a service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs in a separate session that has no relation to your login session.</span></span> <span data-ttu-id="4fcb8-166">일반적인 경우는 아니지만 서비스가 실행되는 세션에 고유하게 매핑된 드라이브가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-166">The session in which a service runs can have its own mapped drives, although it usually does not.</span></span>  
  
-   <span data-ttu-id="4fcb8-167">도메인 사용자 대신 컴퓨터 계정을 사용하여 네트워크 서비스 계정과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-167">You can connect with the network service account by using the computer account instead of a domain user.</span></span> <span data-ttu-id="4fcb8-168">특정 컴퓨터에서 공유 드라이브로 백업할 수 있도록 하려면 해당 컴퓨터 계정에 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-168">To enable backups from specific computers to a shared drive, grant access to the computer accounts.</span></span> <span data-ttu-id="4fcb8-169">백업을 작성하는 Sqlservr.exe 프로세스에 액세스 권한이 있으면 BACKUP 명령을 보내는 사용자에게 액세스 권한이 있는지 여부는 상관이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-169">As long as the Sqlservr.exe process that is writing the backup has access, it is irrelevant whether the user sending the BACKUP command has access.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4fcb8-170">네트워크를 통해 데이터를 백업하면 네트워크 오류가 발생하기 쉬우므로 원격 디스크를 사용하는 경우 완료 후에 백업 작업을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-170">Backing up data over a network can be subject to network errors; therefore, we recommend that when you are using a remote disk you verify the backup operation after it finishes.</span></span> <span data-ttu-id="4fcb8-171">자세한 내용은 [RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-171">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a><span data-ttu-id="4fcb8-172">UNC(Universal Naming Convention) 이름 지정</span><span class="sxs-lookup"><span data-stu-id="4fcb8-172">Specifying a Universal Naming Convention (UNC) Name</span></span>  
 <span data-ttu-id="4fcb8-173">백업이나 복원 명령에서 네트워크 공유를 지정하려면 백업 디바이스에 정규화된 UNC 파일 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-173">To specify a network share in a backup or restore command, you should use the fully qualified universal naming convention (UNC) name of the file for the backup device.</span></span> <span data-ttu-id="4fcb8-174">UNC 이름은 **\\\\** _Systemname_ **\\** _ShareName_ **\\** _Path_ **\\** _FileName_.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-174">A UNC name has the form **\\\\**_Systemname_**\\**_ShareName_**\\**_Path_**\\**_FileName_.</span></span>  
  
 <span data-ttu-id="4fcb8-175">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="4fcb8-175">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="using-tape-devices"></a><a name="TapeDevices"></a><span data-ttu-id="4fcb8-176">테이프 장치 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-176">Using Tape Devices</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fcb8-177">테이프 백업 디바이스에 대한 지원은 이후 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-177">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4fcb8-178">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-178">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="4fcb8-179">**섹션 내용**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-179">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="4fcb8-180">실제 이름을 사용하여 백업 테이프 지정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-180">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>](#BackupTapeUsingPhysicalName)  
  
-   [<span data-ttu-id="4fcb8-181">테이프 특정 BACKUP 및 RESTORE 옵션 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-181">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>](#TapeOptions)  
  
-   [<span data-ttu-id="4fcb8-182">열려 있는 테이프 관리</span><span class="sxs-lookup"><span data-stu-id="4fcb8-182">Managing Open Tapes</span></span>](#OpenTapes)  
  
 <span data-ttu-id="4fcb8-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터를 테이프에 백업하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 운영 체제에서 지원하는 테이프 드라이브 또는 드라이브를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-183">Backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data to tape requires that the tape drive or drives be supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system.</span></span> <span data-ttu-id="4fcb8-184">또한 지정된 테이프 드라이브에는 드라이브 제조업체가 권장하는 테이프만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-184">Additionally, for the given tape drive, we recommend that you use only tapes recommended by the drive manufacturer.</span></span> <span data-ttu-id="4fcb8-185">테이프 드라이브 설치 방법은 Windows 운영 체제 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-185">For more information about how to install a tape drive, see the documentation for the Windows operating system.</span></span>  
  
 <span data-ttu-id="4fcb8-186">테이프 드라이브를 사용하여 백업할 경우 한 개의 테이프가 가득 차면 계속해서 다른 테이프에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-186">When a tape drive is used, a backup operation may fill one tape and continue onto another tape.</span></span> <span data-ttu-id="4fcb8-187">각 테이프에는 미디어 헤더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-187">Each tape contains a media header.</span></span> <span data-ttu-id="4fcb8-188">첫 번째로 사용된 미디어를 *초기 테이프*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-188">The first media used is called the *initial tape*.</span></span> <span data-ttu-id="4fcb8-189">각각의 연속되는 테이프는 *연속 테이프* 라고 하며 이전 테이프의 일련 번호보다 높은 미디어 일련 번호가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-189">Each successive tape is known as a *continuation tape* and has a media sequence number that is one higher than the previous tape.</span></span> <span data-ttu-id="4fcb8-190">예를 들어 4개의 테이프 디바이스가 연결된 미디어 세트에는 적어도 4개의 초기 테이프가 있으며 데이터베이스가 맞지 않은 경우 4개의 연속적인 테이프가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-190">For example, a media set associated with four tape devices contains at least four initial tapes (and, if the database does not fit, four series of continuation tapes).</span></span> <span data-ttu-id="4fcb8-191">백업 세트를 추가할 때 마지막 테이프를 연속하여 탑재해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-191">When appending a backup set, you must mount the last tape in the series.</span></span> <span data-ttu-id="4fcb8-192">마지막 테이프를 탑재하지 않으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 탑재된 테이프의 끝으로 빨리 감아 검색한 다음 테이프를 교체하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-192">If the last tape is not mounted, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] scans forward to the end of the mounted tape and then requires that you change the tape.</span></span> <span data-ttu-id="4fcb8-193">이때 마지막 테이프를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-193">At that point, mount the last tape.</span></span>  
  
 <span data-ttu-id="4fcb8-194">테이프 백업 디바이스는 다음 사항을 제외하고 디스크 디바이스와 같이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-194">Tape backup devices are used like disk devices, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="4fcb8-195">테이프 디바이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스를 실행하는 컴퓨터에 물리적으로 연결되어 있어야 하며</span><span class="sxs-lookup"><span data-stu-id="4fcb8-195">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4fcb8-196">원격 테이프 디바이스로 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-196">Backing up to remote tape devices is not supported.</span></span>  
  
-   <span data-ttu-id="4fcb8-197">백업 작업 중에 테이프 백업 디바이스가 찼는데 작성할 데이터가 더 남아 있으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 새 테이프를 넣으라는 메시지를 표시하고 새 테이프가 로드된 후에 백업 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-197">If a tape backup device is filled during the backup operation, but more data still must be written, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prompts for a new tape and continues the backup operation after a new tape is loaded.</span></span>  
  
###  <a name="specifying-a-backup-tape-by-using-its-physical-name-transact-sql"></a><a name="BackupTapeUsingPhysicalName"></a><span data-ttu-id="4fcb8-198">실제 이름을 사용 하 여 백업 테이프 지정 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-198">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="4fcb8-199">테이프 드라이브의 물리적 디바이스 이름을 사용하여 백업 테이프를 지정하기 위한 기본 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-199">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup tape using the physical device name of the tape drive is:</span></span>  
  
 <span data-ttu-id="4fcb8-200">BACKUP { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="4fcb8-200">BACKUP { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="4fcb8-201">TO TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-201">TO TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="4fcb8-202">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="4fcb8-202">For example:</span></span>  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 <span data-ttu-id="4fcb8-203">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문에서 물리적 테이프 디바이스를 지정하기 위한 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-203">To specify a physical tape device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="4fcb8-204">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="4fcb8-204">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="4fcb8-205">FROM TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-205">FROM TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
###  <a name="tape-specific-backup-and-restore-options-transact-sql"></a><a name="TapeOptions"></a><span data-ttu-id="4fcb8-206">테이프 특정 BACKUP 및 RESTORE 옵션 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-206">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>  
 <span data-ttu-id="4fcb8-207">테이프를 편리하게 관리할 수 있도록 BACKUP 문은 다음과 같은 테이프 관련 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-207">To facilitate tape management, the BACKUP statement provides the following tape-specific options:</span></span>  
  
-   <span data-ttu-id="4fcb8-208">{ NOUNLOAD | **UNLOAD** }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-208">{ NOUNLOAD | **UNLOAD** }</span></span>  
  
     <span data-ttu-id="4fcb8-209">백업 또는 복원 작업 후에 테이프 드라이브에서 자동으로 백업 테이프를 언로드할지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-209">You can control whether a backup tape is unloaded automatically from the tape drive after a backup or restore operation.</span></span> <span data-ttu-id="4fcb8-210">UNLOAD/NOUNLOAD는 세션 기간 동안이나 다른 옵션을 지정하여 다시 설정할 때까지 유지되는 세션 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-210">UNLOAD/NOUNLOAD is a session setting that persists for the life of the session or until it is reset by specifying the alternative.</span></span>  
  
-   <span data-ttu-id="4fcb8-211">{ **REWIND** | NOREWIND }</span><span class="sxs-lookup"><span data-stu-id="4fcb8-211">{ **REWIND** | NOREWIND }</span></span>  
  
     <span data-ttu-id="4fcb8-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 백업이나 복원 작업 후에 테이프를 열어 놓을지 또는 테이프가 꽉 찬 후에 테이프를 해제하고 되감을지를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-212">You can control whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keeps the tape remains open after the backup or restore operation or releases and rewinds the tape after it fills.</span></span> <span data-ttu-id="4fcb8-213">기본 동작은 테이프를 되감는 것입니다(REWIND).</span><span class="sxs-lookup"><span data-stu-id="4fcb8-213">The default behavior is to rewind the tape (REWIND).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fcb8-214">BACKUP 구문 및 인수에 대한 자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-214">For more information about the BACKUP syntax and arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="4fcb8-215">RESTORE 구문 및 인수에 대한 자세한 내용은 각각 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 및 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-215">For more information about the RESTORE syntax and arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql), respectively.</span></span>  
  
###  <a name="managing-open-tapes"></a><a name="OpenTapes"></a><span data-ttu-id="4fcb8-216">열려 있는 테이프 관리</span><span class="sxs-lookup"><span data-stu-id="4fcb8-216">Managing Open Tapes</span></span>  
 <span data-ttu-id="4fcb8-217">열려 있는 테이프 디바이스 목록 및 탑재 요청 상태를 보려면 [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) 동적 관리 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-217">To view a list of open tape devices and the status of mount requests, query the [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) dynamic management view.</span></span> <span data-ttu-id="4fcb8-218">이 뷰는 다음 BACKUP 또는 RESTORE 작업을</span><span class="sxs-lookup"><span data-stu-id="4fcb8-218">This view shows all the open tapes.</span></span> <span data-ttu-id="4fcb8-219">기다리는 동안 일시적으로 유휴 상태에 있는 사용 중인 테이프를 비롯하여 열려 있는 모든 테이프를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-219">These include in-use tapes that are temporarily idle while they wait for the next BACKUP or RESTORE operation.</span></span>  
  
 <span data-ttu-id="4fcb8-220">테이프를 실수로 열어 놓은 경우 테이프를 해제하는 가장 빠른 방법은 RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_ 명령을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-220">If a tape has been accidentally left open, the fastest way to release the tape is by using the following command: RESTORE REWINDONLY FROM TAPE **=**_backup_device_name_.</span></span> <span data-ttu-id="4fcb8-221">자세한 내용은 [RESTORE REWINDONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-221">For more information, see [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).</span></span>  
  
## <a name="using-the-azure-blob-storage-service"></a><span data-ttu-id="4fcb8-222">Azure Blob Storage 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-222">Using the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="4fcb8-223">Azure Blob Storage 서비스에 SQL Server 백업을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-223">SQL Server Backups can be written to the Azure Blob Storage Service.</span></span>  <span data-ttu-id="4fcb8-224">백업에 Azure Blob storage 서비스를 사용 하는 방법에 대 한 자세한 내용은 [Azure Blob Storage 서비스를 사용 하 여 백업 및 복원 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-224">For more information on how to use the Azure Blob storage service for your backups, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
##  <a name="using-a-logical-backup-device"></a><a name="LogicalBackupDevice"></a><span data-ttu-id="4fcb8-225">논리적 백업 장치 사용</span><span class="sxs-lookup"><span data-stu-id="4fcb8-225">Using a Logical Backup Device</span></span>  
 <span data-ttu-id="4fcb8-226">*논리적 백업 디바이스*는 특정 물리적 백업 디바이스(디스크 파일 또는 테이프 드라이브)를 가리키는 선택적인 사용자 정의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-226">A *logical backup device* is an optional, user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span> <span data-ttu-id="4fcb8-227">논리적 백업 디바이스를 사용하면 해당 물리적 백업 디바이스를 참조할 때 간접 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-227">A logical backup device lets you use indirection when referencing the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="4fcb8-228">논리적 백업 디바이스를 정의하려면 물리적 디바이스에 논리적 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-228">Defining a logical backup device involves assigning a logical name to a physical device.</span></span> <span data-ttu-id="4fcb8-229">예를 들어 논리적 디바이스인 AdventureWorksBackups가 Z:\SQLServerBackups\AdventureWorks2012.bak 파일이나 \\\\.\tape0 테이프 드라이브를 가리키도록 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-229">For example, a logical device, AdventureWorksBackups, could be defined to point to the Z:\SQLServerBackups\AdventureWorks2012.bak file or the \\\\.\tape0 tape drive.</span></span> <span data-ttu-id="4fcb8-230">그런 다음 백업 및 복원 명령에서 DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' 또는 TAPE = '\\\\.\tape0' 대신 AdventureWorksBackups를 백업 디바이스로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-230">Backup and restore commands can then specify AdventureWorksBackups as the backup device, instead of DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' or TAPE = '\\\\.\tape0'.</span></span>  
  
 <span data-ttu-id="4fcb8-231">논리적 디바이스 이름은 서버 인스턴스의 모든 논리적 백업 디바이스에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-231">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="4fcb8-232">기존의 논리적 디바이스 이름을 보려면 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-232">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span> <span data-ttu-id="4fcb8-233">이 뷰는 각 논리적 백업 디바이스의 이름을 표시하고 해당하는 물리적 백업 디바이스의 유형과 물리적 파일 이름 또는 경로를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-233">This view displays the name of each logical backup device and describes the type and physical file name or path of the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="4fcb8-234">논리적 백업 디바이스를 정의한 후에는 BACKUP 또는 RESTORE 명령에서 디바이스의 실제 이름 대신 논리적 백업 디바이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-234">After a logical backup device is defined, in a BACKUP or RESTORE command, you can specify the logical backup device instead of the physical name of the device.</span></span> <span data-ttu-id="4fcb8-235">예를 들어 다음 문은 `AdventureWorks2012` 논리적 백업 디바이스에 `AdventureWorksBackups` 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-235">For example, the following statement backs up the `AdventureWorks2012` database to the `AdventureWorksBackups` logical backup device.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4fcb8-236">지정된 BACKUP 또는 RESTORE 문에서 논리적 백업 디바이스 이름과 해당 물리적 백업 디바이스 이름을 바꾸어 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-236">In a given BACKUP or RESTORE statement, the logical backup device name and the corresponding physical backup device name are interchangeable.</span></span>  
  
 <span data-ttu-id="4fcb8-237">논리적 백업 디바이스는 긴 경로보다 사용이 편리하다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-237">One advantage of using a logical backup device is that it is simpler to use than a long path.</span></span> <span data-ttu-id="4fcb8-238">동일한 경로 또는 테이프 디바이스에 일련의 백업을 작성하려는 경우 논리적 백업 디바이스를 사용하면 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-238">Using a logical backup device can help if you plan to write a series of backups to the same path or to a tape device.</span></span> <span data-ttu-id="4fcb8-239">논리적 백업 디바이스는 특히 테이프 백업 디바이스를 식별하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-239">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
 <span data-ttu-id="4fcb8-240">특정 논리적 백업 디바이스를 사용하도록 백업 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-240">A backup script can be written to use a particular logical backup device.</span></span> <span data-ttu-id="4fcb8-241">이렇게 하면 스크립트를 업데이트하지 않고도 새로운 물리적 백업 디바이스로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-241">This lets you switch to a new physical backup devices without updating the script.</span></span> <span data-ttu-id="4fcb8-242">전환 과정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-242">Switching involves the following process:</span></span>  
  
1.  <span data-ttu-id="4fcb8-243">원래의 논리적 백업 디바이스 삭제</span><span class="sxs-lookup"><span data-stu-id="4fcb8-243">Dropping the original logical backup device.</span></span>  
  
2.  <span data-ttu-id="4fcb8-244">원래의 논리적 디바이스 이름을 사용하지만 다른 물리적 백업 디바이스에 매핑되는 새 논리적 백업 디바이스 정의.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-244">Defining a new logical backup device that uses the original logical device name but maps to a different physical backup device.</span></span> <span data-ttu-id="4fcb8-245">논리적 백업 디바이스는 특히 테이프 백업 디바이스를 식별하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-245">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
##  <a name="mirrored-backup-media-sets"></a><a name="MirroredMediaSets"></a><span data-ttu-id="4fcb8-246">미러된 백업 미디어 세트</span><span class="sxs-lookup"><span data-stu-id="4fcb8-246">Mirrored Backup Media Sets</span></span>  
 <span data-ttu-id="4fcb8-247">백업 미디어 세트를 미러링하면 백업 디바이스의 오작동에 따른 영향이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-247">Mirroring of backup media sets reduces the effect of backup-device malfunctions.</span></span> <span data-ttu-id="4fcb8-248">데이터 손실을 방지할 수 있는 최후의 수단이 백업이므로 이러한 오작동은 특히 심각합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-248">These malfunctions are especially serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="4fcb8-249">데이터베이스의 크기가 커지면 백업 디바이스 또는 미디어의 실패로 인해 복원 불가능한 백업을 만들게 될 가능성이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-249">As the sizes of databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="4fcb8-250">백업 미디어를 미러링하면 물리적 백업 디바이스에 중복을 제공하여 백업의 안정성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-250">Mirroring backup media increases the reliability of backups by providing redundancy for the physical backup device.</span></span> <span data-ttu-id="4fcb8-251">자세한 내용은 이 항목의 뒷부분에 나오는 [미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-251">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fcb8-252">미러된 백업 미디어 세트는 [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] 이상 버전에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-252">Mirrored backup media sets are supported only in [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] and later versions.</span></span>  
  
##  <a name="archiving-sql-server-backups"></a><a name="Archiving"></a><span data-ttu-id="4fcb8-253">SQL Server 백업 보관</span><span class="sxs-lookup"><span data-stu-id="4fcb8-253">Archiving SQL Server Backups</span></span>  
 <span data-ttu-id="4fcb8-254">파일 시스템 백업 유틸리티를 사용하여 디스크 백업을 보관하고 오프사이트에 보관 파일을 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-254">We recommend that you use a file system backup utility to archive the disk backups and that you store the archives off-site.</span></span> <span data-ttu-id="4fcb8-255">디스크를 사용할 경우 보관된 백업을 네트워크를 통해 오프사이트 디스크에 쓸 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-255">Using disk has the advantage that you use the network to write the archived backups onto an off-site disk.</span></span> <span data-ttu-id="4fcb8-256">Azure Blob Storage 서비스를 오프 사이트 보관 옵션으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-256">The Azure Blob storage service can be used as off-site archival option.</span></span>  <span data-ttu-id="4fcb8-257">Azure Blob Storage 서비스에 디스크 백업을 업로드하거나 백업을 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-257">You can either upload your disk backups, or directly write the backups to the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="4fcb8-258">다른 일반적인 보관 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업을 로컬 백업 디스크에 쓰고 테이프에 보관한 다음 오프사이트에 테이프를 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4fcb8-258">Another common archiving approach is to write [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups onto a local backup disk, archive them to tape, and then store the tapes off-site.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4fcb8-259">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4fcb8-259">Related Tasks</span></span>  
 <span data-ttu-id="4fcb8-260">**디스크 디바이스를 지정하려면(SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-260">**To specify a disk device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="4fcb8-261">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-261">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="4fcb8-262">**테이프 디바이스를 지정하려면(SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-262">**To specify a tape device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="4fcb8-263">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-263">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="4fcb8-264">**논리적 백업 디바이스를 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-264">**To define a logical backup device**</span></span>  
  
-   [<span data-ttu-id="4fcb8-265">sp_addumpdevice&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-265">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [<span data-ttu-id="4fcb8-266">디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-266">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="4fcb8-267">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-267">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <span data-ttu-id="4fcb8-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span><span class="sxs-lookup"><span data-stu-id="4fcb8-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span></span>  
  
 <span data-ttu-id="4fcb8-269">**논리적 백업 디바이스를 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-269">**To use a logical backup device**</span></span>  
  
-   [<span data-ttu-id="4fcb8-270">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-270">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="4fcb8-271">디바이스에서 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-271">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="4fcb8-272">BACKUP&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-272">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
-   [<span data-ttu-id="4fcb8-273">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-273">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 <span data-ttu-id="4fcb8-274">**백업 디바이스에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-274">**To View Information About Backup Devices**</span></span>  
  
-   [<span data-ttu-id="4fcb8-275">백업 기록 및 헤더 정보&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-275">Backup History and Header Information &#40;SQL Server&#41;</span></span>](backup-history-and-header-information-sql-server.md)  
  
-   [<span data-ttu-id="4fcb8-276">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-276">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="4fcb8-277">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-277">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 <span data-ttu-id="4fcb8-278">**논리적 백업 디바이스를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="4fcb8-278">**To delete a logical backup device**</span></span>  
  
-   [<span data-ttu-id="4fcb8-279">sp_dropdevice&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-279">sp_dropdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [<span data-ttu-id="4fcb8-280">백업 디바이스 삭제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-280">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4fcb8-281">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fcb8-281">See Also</span></span>  
 <span data-ttu-id="4fcb8-282">[SQL Server, Backup Device 개체](../performance-monitor/sql-server-backup-device-object.md) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-282">[SQL Server, Backup Device Object](../performance-monitor/sql-server-backup-device-object.md) </span></span>  
 <span data-ttu-id="4fcb8-283">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="4fcb8-284">[유지 관리 계획](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-284">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="4fcb8-285">[미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-285">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="4fcb8-286">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="4fcb8-287">[RESTORE LABELONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="4fcb8-288">[sys.backup_devices&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="4fcb8-289">[sys.dm_io_backup_tapes&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4fcb8-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span></span>  
 [<span data-ttu-id="4fcb8-290">미러된 백업 미디어 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4fcb8-290">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
