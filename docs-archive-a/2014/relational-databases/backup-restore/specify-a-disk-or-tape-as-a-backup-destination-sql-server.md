---
title: 디스크 또는 테이프를 백업 대상으로 지정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
- backups [SQL Server], creating
- tape backup devices, backing up
ms.assetid: e391f452-ed8c-4b40-b846-ac3881271b94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a0f8ec5d9741e42f3b7d8eda8ebdba23622982d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731732"
---
# <a name="specify-a-disk-or-tape-as-a-backup-destination-sql-server"></a><span data-ttu-id="d242a-102">디스크 또는 테이프를 백업 대상으로 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d242a-102">Specify a Disk or Tape As a Backup Destination (SQL Server)</span></span>
  <span data-ttu-id="d242a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 백업 대상으로 디스크 또는 테이프를 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-103">This topic describes how to specify a disk or tape as a backup destination in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d242a-104">테이프 백업 디바이스에 대한 지원은 나중 버전의 SQL Server에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="d242a-105">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="d242a-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="d242a-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d242a-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d242a-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d242a-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d242a-108">보안</span><span class="sxs-lookup"><span data-stu-id="d242a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d242a-109">**다음을 사용하여 디스크나 테이프를 백업 대상으로 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="d242a-109">**To specify a disk or tape as a backup destination, using:**</span></span>  
  
     [<span data-ttu-id="d242a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d242a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d242a-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d242a-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d242a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d242a-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d242a-113">보안</span><span class="sxs-lookup"><span data-stu-id="d242a-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d242a-114">권한</span><span class="sxs-lookup"><span data-stu-id="d242a-114">Permissions</span></span>  
 <span data-ttu-id="d242a-115">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-115">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="d242a-116">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-116">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d242a-117">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-117">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="d242a-118">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-118">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="d242a-119">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-119">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d242a-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d242a-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="d242a-121">디스크나 테이프를 백업 대상으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="d242a-121">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="d242a-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-122">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d242a-123">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-123">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="d242a-124">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-124">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="d242a-125">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-125">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d242a-126">**일반** 페이지의 **대상** 섹션에서 **디스크** 또는 **테이프**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-126">In the **Destination** section of the **General** page, click **Disk** or **Tape**.</span></span> <span data-ttu-id="d242a-127">**추가**를 클릭하면 단일 미디어 세트를 포함하는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-127">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span>  
  
     <span data-ttu-id="d242a-128">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-128">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="d242a-129">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-129">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d242a-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d242a-130">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="d242a-131">디스크나 테이프를 백업 대상으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="d242a-131">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="d242a-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d242a-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d242a-134">[BACKUP](/sql/t-sql/statements/backup-transact-sql) 문에서 파일 또는 디바이스와 해당 물리적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the file or device and its physical name.</span></span> <span data-ttu-id="d242a-135">이 예에서는 `AdventureWorks2012` 데이터베이스를 디스크 파일 `Z:\SQLServerBackups\AdventureWorks2012.Bak`에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="d242a-135">This example backs up the `AdventureWorks2012` database to the disk file `Z:\SQLServerBackups\AdventureWorks2012.Bak`.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d242a-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d242a-136">See Also</span></span>  
 <span data-ttu-id="d242a-137">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d242a-137">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="d242a-138">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d242a-138">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="d242a-139">[디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d242a-139">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="d242a-140">[차등 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d242a-140">[Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="d242a-141">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d242a-141">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
