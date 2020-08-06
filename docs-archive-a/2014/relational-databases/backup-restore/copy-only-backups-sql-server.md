---
title: 복사 전용 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc74d7b1bba2a0163ac9edefb5d465c54ef6296c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661178"
---
# <a name="copy-only-backups-sql-server"></a><span data-ttu-id="40047-102">복사 전용 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40047-102">Copy-Only Backups (SQL Server)</span></span>
  <span data-ttu-id="40047-103">*복사 전용 백업*은 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 시퀀스와 독립적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="40047-103">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="40047-104">일반적으로 백업을 수행하면 데이터베이스가 변경되므로 이후 백업이 복원되는 방식에 영향을 주게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40047-104">Usually, taking a backup changes the database and affects how later backups are restored.</span></span> <span data-ttu-id="40047-105">그러나 백업 전체에 영향을 주지 않고 특별한 용도로 백업을 수행한 다음 데이터베이스에 대한 프로시저를 복원하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-105">However, occasionally, it is useful to take a backup for a special purpose without affecting the overall backup and restore procedures for the database.</span></span> <span data-ttu-id="40047-106">이러한 용도로 복사 전용 백업이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="40047-106">Copy-only backups serve this purpose.</span></span>  
  
 <span data-ttu-id="40047-107">복사 전용 백업의 종류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-107">The types of copy-only backups are as follows:</span></span>  
  
-   <span data-ttu-id="40047-108">복사 전용 전체 백업(모든 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="40047-108">Copy-only full backups (all recovery models)</span></span>  
  
     <span data-ttu-id="40047-109">복사 전용 백업은 차등 기반 또는 차등 백업으로 사용될 수 없으며 차등 기반에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-109">A copy-only backup cannot serve as a differential base or differential backup and does not affect the differential base.</span></span>  
  
     <span data-ttu-id="40047-110">복사 전용 전체 백업을 복원하는 과정은 다른 전체 백업을 복원하는 과정과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="40047-110">Restoring a copy-only full backup is the same as restoring any other full backup.</span></span>  
  
-   <span data-ttu-id="40047-111">복사 전용 로그 백업(전체 복구 모델 및 대량 로그 복구 모델 전용)</span><span class="sxs-lookup"><span data-stu-id="40047-111">Copy-only log backups (full recovery model and bulk-logged recovery model only)</span></span>  
  
     <span data-ttu-id="40047-112">복사 전용 로그 백업은 기존 로그 보관 지점을 유지하므로 정기적인 로그 백업 시퀀스에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-112">A copy-only log backup preserves the existing log archive point and, therefore, does not affect the sequencing of regular log backups.</span></span> <span data-ttu-id="40047-113">복사 전용 로그 백업은 일반적으로 불필요한 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="40047-113">Copy-only log backups are typically unnecessary.</span></span> <span data-ttu-id="40047-114">대신 WITH NORECOVERY를 사용하여 새 정기 로그 백업을 만든 다음 해당 백업을 복원 시퀀스에 필요한 모든 이전 로그 백업과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-114">Instead, you can create a new routine log backup (using WITH NORECOVERY) and use that backup together with any previous log backups that are required for the restore sequence.</span></span> <span data-ttu-id="40047-115">하지만 복사 전용 로그 백업은 온라인 복원에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-115">However, a copy-only log backup can sometimes be useful for performing an online restore.</span></span> <span data-ttu-id="40047-116">이에 대한 예제는 [예제: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40047-116">For an example of this, see [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).</span></span>  
  
     <span data-ttu-id="40047-117">복사 전용 백업 이후에는 트랜잭션 로그를 자를 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-117">The transaction log is never truncated after a copy-only backup.</span></span>  
  
 <span data-ttu-id="40047-118">복사 전용 백업은 **backupset** 테이블의 [is_copy_only](/sql/relational-databases/system-tables/backupset-transact-sql) 열에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="40047-118">Copy-only backups are recorded in the **is_copy_only** column of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table.</span></span>  
  
## <a name="to-create-a-copy-only-backup"></a><span data-ttu-id="40047-119">복사 전용 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="40047-119">To Create a Copy-Only Backup</span></span>  
 <span data-ttu-id="40047-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 복사 전용 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-120">You can create a copy-only backup by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="40047-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="40047-121">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="40047-122">**데이터베이스 백업** 대화 상자의 **일반** 페이지에서 **복사 전용 백업** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40047-122">On the **General** page of the **Back Up Database** dialog box, select the **Copy Only Backup** option.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="40047-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="40047-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="40047-124">필수 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-124">The essential [!INCLUDE[tsql](../../../includes/tsql-md.md)] syntax is as follows:</span></span>  
  
-   <span data-ttu-id="40047-125">복사 전용 전체 백업의 경우:</span><span class="sxs-lookup"><span data-stu-id="40047-125">For a copy-only full backup:</span></span>  
  
     <span data-ttu-id="40047-126">데이터베이스 *database_name* \<backup_device*> 에 백업 ... COPY_ONLY 사용 ...</span><span class="sxs-lookup"><span data-stu-id="40047-126">BACKUP DATABASE *database_name* TO \<backup_device*>\* ... WITH COPY_ONLY ...</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40047-127">DIFFERENTIAL 옵션과 함께 지정하면 COPY_ONLY가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40047-127">COPY_ONLY has no effect when specified with the DIFFERENTIAL option.</span></span>  
  
-   <span data-ttu-id="40047-128">복사 전용 로그 백업의 경우:</span><span class="sxs-lookup"><span data-stu-id="40047-128">For a copy-only log backup:</span></span>  
  
     <span data-ttu-id="40047-129">백업 로그 *database_name* ... *\<*backup_device*>* COPY_ONLY 사용 ...</span><span class="sxs-lookup"><span data-stu-id="40047-129">BACKUP LOG *database_name* TO *\<*backup_device*>* ... WITH COPY_ONLY ...</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="40047-130">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="40047-130">Using PowerShell</span></span>  
  
<span data-ttu-id="40047-131">`Backup-SqlDatabase` cmdlet을 `-CopyOnly` 매개 변수와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="40047-131">Use the `Backup-SqlDatabase` cmdlet with the `-CopyOnly` parameter.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="40047-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="40047-132">Related Tasks</span></span>  

### <a name="to-create-a-full-or-log-backup"></a><span data-ttu-id="40047-133">전체 또는 로그 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="40047-133">To create a full or log backup</span></span>
  
-   [<span data-ttu-id="40047-134">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40047-134">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="40047-135">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40047-135">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a><span data-ttu-id="40047-136">복사 전용 백업을 보려면</span><span class="sxs-lookup"><span data-stu-id="40047-136">To view copy-only backups</span></span>
  
-   [<span data-ttu-id="40047-137">backupset&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40047-137">backupset &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><span data-ttu-id="40047-138">SQL Server PowerShell 공급자를 설정하고 사용하려면</span><span class="sxs-lookup"><span data-stu-id="40047-138">To set up and use the SQL Server PowerShell provider</span></span>
  
-   [<span data-ttu-id="40047-139">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="40047-139">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a><span data-ttu-id="40047-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40047-140">See Also</span></span>  
 <span data-ttu-id="40047-141">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40047-141">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="40047-142">[복구 모델&#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="40047-142">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="40047-143">[백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="40047-143">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="40047-144">복원 및 복구 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40047-144">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
