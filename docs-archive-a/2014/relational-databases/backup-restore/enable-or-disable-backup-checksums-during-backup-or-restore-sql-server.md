---
title: 백업 또는 복원 중 백업 체크섬 설정 또는 해제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a239dcdfca689be8555117104264d66a2ac037f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742332"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a><span data-ttu-id="9ada9-102">백업 또는 복원 중 백업 체크섬 설정 또는 해제(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9ada9-102">Enable or Disable Backup Checksums During Backup or Restore (SQL Server)</span></span>
  <span data-ttu-id="9ada9-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스를 백업하거나 복원할 때 백업 체크섬을 설정 또는 해제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-103">This topic describes how to enable or disable backup checksums when you are backing up or restoring a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9ada9-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9ada9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9ada9-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9ada9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9ada9-106">보안</span><span class="sxs-lookup"><span data-stu-id="9ada9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9ada9-107">**다음을 사용하여 백업 체크섬을 설정 또는 해제합니다.**</span><span class="sxs-lookup"><span data-stu-id="9ada9-107">**To enable or disable backup checksums, using:**</span></span>  
  
     [<span data-ttu-id="9ada9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ada9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9ada9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9ada9-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ada9-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9ada9-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ada9-111">보안</span><span class="sxs-lookup"><span data-stu-id="9ada9-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9ada9-112">권한</span><span class="sxs-lookup"><span data-stu-id="9ada9-112">Permissions</span></span>  
 <span data-ttu-id="9ada9-113">BACKUP</span><span class="sxs-lookup"><span data-stu-id="9ada9-113">BACKUP</span></span>  
 <span data-ttu-id="9ada9-114">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="9ada9-115">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ada9-116">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="9ada9-117">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="9ada9-118">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="9ada9-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="9ada9-119">RESTORE</span></span>  
 <span data-ttu-id="9ada9-120">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="9ada9-121">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="9ada9-122">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="9ada9-123">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9ada9-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9ada9-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a><span data-ttu-id="9ada9-125">백업 작업 중 체크섬을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="9ada9-125">To enable or disable checksums during a backup operation</span></span>  
  
1.  <span data-ttu-id="9ada9-126">[데이터베이스 백업 만들기](create-a-full-database-backup-sql-server.md)단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="9ada9-127">**옵션** 페이지의 **안정성** 섹션에서 **미디어에 쓰기 전에 체크섬 수행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9ada9-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9ada9-128">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a><span data-ttu-id="9ada9-129">백업 작업에 대한 백업 체크섬을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="9ada9-129">To enable or disable backup checksum for a backup operation</span></span>  
  
1.  <span data-ttu-id="9ada9-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ada9-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9ada9-132">[BACKUP](/sql/t-sql/statements/backup-transact-sql) 문에서 백업 체크섬을 설정하려면 WITH CHECKSUM 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-132">To enable backup checksums in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="9ada9-133">백업 체크섬을 해제하려면 WITH NO_CHECKSUM 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-133">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="9ada9-134">이 동작은 압축된 백업을 제외한 경우의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-134">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="9ada9-135">다음 예제는 체크섬이 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-135">The following example specifies that checksums be performed.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a><span data-ttu-id="9ada9-136">복원 작업에 대한 백업 체크섬을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="9ada9-136">To enable or disable backup checksum for a restore operation</span></span>  
  
1.  <span data-ttu-id="9ada9-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ada9-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9ada9-139">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문에서 백업 체크섬을 설정하려면 WITH CHECKSUM 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-139">To enable backup checksums in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="9ada9-140">이 동작은 압축된 백업의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-140">This is the default behavior for a compressed backup.</span></span> <span data-ttu-id="9ada9-141">백업 체크섬을 해제하려면 WITH NO_CHECKSUM 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-141">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="9ada9-142">이 동작은 압축된 백업을 제외한 경우의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-142">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="9ada9-143">다음 예제는 백업 체크섬이 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-143">The following example specifies that backup checksums be performed.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  <span data-ttu-id="9ada9-144">복원 작업에 대해 CHECKSUM을 명시적으로 요청하는 경우와 백업에 백업 체크섬이 들어 있는 경우에는 기본적인 경우처럼 백업 체크섬과 페이지 체크섬이 모두 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-144">If you explicitly request CHECKSUM for a restore operation and if the backup contains backup checksums, backup checksums and page checksums are both verified, as in the default case.</span></span> <span data-ttu-id="9ada9-145">그러나 백업 세트에 백업 체크섬이 없으면 복원 작업은 체크섬이 없다는 메시지를 표시하고 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ada9-145">However, if the backup set lacks backup checksums, the restore operation fails with a message indicating that checksums are not present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ada9-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ada9-146">See Also</span></span>  
 <span data-ttu-id="9ada9-147">[RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-148">[RESTORE HEADERONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-149">[RESTORE LABELONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-150">[RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-151">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-152">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-153">[RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ada9-153">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="9ada9-154">[백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ada9-154">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="9ada9-155">오류 발생 후 백업 또는 복원 작업 계속 또는 중지 여부 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ada9-155">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
