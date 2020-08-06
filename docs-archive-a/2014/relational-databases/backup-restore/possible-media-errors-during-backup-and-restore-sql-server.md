---
title: 백업 및 복원 중 발생 가능한 미디어 오류(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15691c513aad6027be1063ef566ebdf245ebcc8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736442"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a><span data-ttu-id="56bae-102">백업 및 복원 중 발생 가능한 미디어 오류(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="56bae-102">Possible Media Errors During Backup and Restore (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="56bae-103">에서는 오류가 검색되면 데이터베이스를 복구할 수 있는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-103">gives you the option of recovering a database despite detected errors.</span></span> <span data-ttu-id="56bae-104">중요한 새 오류 검색 메커니즘을 사용하면 백업 작업으로 만들고 복원 작업으로 유효성을 검사할 수 있는 백업 체크섬을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-104">An important new error-detection mechanism is the optional creation of a backup checksum that can be created by a backup operation and validated by a restore operation.</span></span> <span data-ttu-id="56bae-105">작업에서 오류를 검사할지 여부 및 오류 발생 시 작업을 중지할지 아니면 계속할지를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-105">You can control whether an operation checks for errors and whether the operation stops or continues on encountering an error.</span></span> <span data-ttu-id="56bae-106">백업에 백업 체크섬이 들어 있으면 RESTORE 문과 RESTORE VERIFYONLY 문으로 오류를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-106">If a backup contains a backup checksum, RESTORE and RESTORE VERIFYONLY statements can check for errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56bae-107">미러된 백업은 미디어 세트 복사본(미러)을 4개까지 제공하고 손상된 미디어로 인한 오류를 복구하기 위한 대체 복사본을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-107">Mirrored backups provide up to four copies (mirrors) of a media set, providing alternative copies for recovering from errors caused by damaged media.</span></span> <span data-ttu-id="56bae-108">자세한 내용은 이 항목의 뒷부분에 나오는 [미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-108">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
  
  
##  <a name="backup-checksums"></a><a name="BckChecksums"></a> <span data-ttu-id="56bae-109">백업 체크섬</span><span class="sxs-lookup"><span data-stu-id="56bae-109">Backup Checksums</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="56bae-110">에서는 페이지 체크섬, 로그 블록 체크섬 및 백업 체크섬의 3가지 유형의 체크섬을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-110">supports three types of checksums: a checksum on pages, a checksum in log blocks, and a backup checksum.</span></span> <span data-ttu-id="56bae-111">백업 체크섬을 생성할 때 BACKUP은 데이터베이스에서 읽은 데이터가 데이터베이스에 들어 있는 체크섬이나 조각난 페이지 표시와 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-111">When generating a backup checksum, BACKUP verifies that the data read from the database is consistent with any checksum or torn-page indication that is present in the database.</span></span>  
  
 <span data-ttu-id="56bae-112">BACKUP 문은 필요에 따라 백업 스트림에 대한 백업 체크섬을 계산합니다. 페이지 체크섬 또는 조각난 페이지 정보가 지정한 페이지에 있을 경우 BACKUP은 해당 페이지를 백업하면서 해당 페이지의 체크섬과 조각난 페이지 상태 및 페이지 ID도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-112">The BACKUP statement optionally computes a backup checksum on the backup stream; if page-checksum or torn-page information is present on a given page, when backing up the page, BACKUP also verifies the checksum and torn-page status and the page ID, of the page.</span></span> <span data-ttu-id="56bae-113">백업 체크섬을 만들 때 백업 작업은 체크섬을 페이지에 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-113">When creating a backup checksum, a backup operation does not add any checksums to pages.</span></span> <span data-ttu-id="56bae-114">페이지는 데이터베이스에 있는 대로 백업되고 페이지가 백업에 의해 수정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-114">Pages are backed up as they exist in the database, and the pages are unmodified by backup.</span></span>  
  
 <span data-ttu-id="56bae-115">백업 체크섬을 사용하면 백업 체크섬을 확인하고 생성하는 오버헤드로 인해 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-115">Due to the overhead verifying and generating backup checksums, using backup checksums poses a potential performance impact.</span></span> <span data-ttu-id="56bae-116">작업과 백업 처리량이 모두 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-116">Both the workload and the backup throughput may be affected.</span></span> <span data-ttu-id="56bae-117">그러므로 백업 체크섬은 필요한 경우에만 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-117">Therefore, using backup checksums is optional.</span></span> <span data-ttu-id="56bae-118">백업하는 동안 체크섬을 생성하기로 결정했으면 시스템에서 실행 중인 동시 작업에 대한 영향과 CPU 오버헤드 발생을 주의 깊게 모니터링하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-118">When deciding to generate checksums during a backup, carefully monitor the CPU overhead incurred as well as the impact on any concurrent workload on the system.</span></span>  
  
 <span data-ttu-id="56bae-119">BACKUP은 디스크에 있는 원본 페이지와 페이지의 내용을 절대로 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-119">BACKUP never modifies the source page on disk nor the contents of a page.</span></span>  
  
 <span data-ttu-id="56bae-120">백업 체크섬을 사용하도록 설정하면 백업 작업에서 다음 단계가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-120">When backup checksums are enabled, a backup operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="56bae-121">백업 미디어에 페이지를 쓰기 전에 백업 작업은 페이지 체크섬 또는 조각난 페이지 검색 등 페이지 수준 정보(있는 경우)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-121">Before writing a page to the backup media, the backup operation verifies the page-level information (page checksum or torn page detection), if either exists.</span></span> <span data-ttu-id="56bae-122">아무 것도 없으면 백업이 페이지를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-122">If neither exists, backup cannot verify the page.</span></span> <span data-ttu-id="56bae-123">확인할 수 없으면 페이지가 있는 그대로 포함되고 해당 콘텐츠가 전체 백업 체크섬에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-123">Unverified the pages are included as is, and their contents are added to the overall backup checksum.</span></span>  
  
     <span data-ttu-id="56bae-124">확인 중 백업 작업에 페이지 오류가 발생할 경우 백업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-124">If the backup operation encounters a page error during verification, the backup fails.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="56bae-125">페이지 체크섬과 조각난 페이지 검색에 대한 자세한 내용은 ALTER DATABASE 문의 PAGE_VERIFY 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-125">For more information about page checksums and torn page detection, see the PAGE_VERIFY option of the ALTER DATABASE statement.</span></span> <span data-ttu-id="56bae-126">자세한 내용은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-126">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
2.  <span data-ttu-id="56bae-127">페이지 체크섬이 있는지 여부에 관계없이 BACKUP은 백업 스트림에 대해 별도의 백업 체크섬을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-127">Regardless of whether page checksums are present, BACKUP generates a separate backup checksum for the backup streams.</span></span> <span data-ttu-id="56bae-128">복원 작업은 경우에 따라 백업 체크섬을 사용하여 백업이 손상되지 않았는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-128">Restore operations can optionally use the backup checksum to validate that the backup is not corrupted.</span></span> <span data-ttu-id="56bae-129">백업 체크섬은 데이터베이스 페이지가 아니라 백업 미디어에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-129">The backup checksum is stored on the backup media, not on the database pages.</span></span> <span data-ttu-id="56bae-130">백업 체크섬은 복원할 때 사용되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-130">The backup checksum can optionally be used at restore time.</span></span>  
  
3.  <span data-ttu-id="56bae-131">백업 세트의 플래그는 **msdb..backupset** 의 **has_backup_checksums**열에서 포함 백업 체크섬으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-131">The backup set is flagged as containing backup checksums (in the **has_backup_checksums** column of **msdb..backupset)**.</span></span> <span data-ttu-id="56bae-132">자세한 내용은 [backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-132">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
 <span data-ttu-id="56bae-133">복원 작업 중 백업 미디어에 백업 체크섬이 있을 경우 기본적으로 RESTORE 문과 RESTORE VERIFYONLY 문은 백업 체크섬과 페이지 체크섬을 모두 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-133">During a restore operation, if backup checksums are present on the backup media, by default, both the RESTORE and RESTORE VERIFYONLY statements verify the backup checksums and page checksums.</span></span> <span data-ttu-id="56bae-134">백업 체크섬이 없을 경우 복원 작업은 확인 없이 진행됩니다. 백업 체크섬이 없으면 복원이 페이지 체크섬을 안정적으로 확인할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-134">If there is no backup checksum, either restore operation proceeds without any verification; this is because without a backup checksum, restore cannot reliably verify page checksums.</span></span>  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a><span data-ttu-id="56bae-135">백업 또는 복원 작업 중에 페이지 체크섬 오류에 응답</span><span class="sxs-lookup"><span data-stu-id="56bae-135">Response to Page Checksum Errors During a Backup or Restore Operation</span></span>  
 <span data-ttu-id="56bae-136">기본적으로 페이지 체크섬 오류가 발생한 후 BACKUP 또는 RESTORE 작업이 실패하고 RESTORE VERIFYONLY 작업이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-136">By default, after encountering a page checksum error, a BACKUP or RESTORE operation fails and a RESTORE VERIFYONLY operation continues.</span></span> <span data-ttu-id="56bae-137">하지만 오류가 발생할 때 지정된 작업이 실패하도록 하거나 가능한 한 작업을 계속하도록 할지를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-137">However, you can control whether a given operation fails on encountering an error or continues as best it can.</span></span>  
  
 <span data-ttu-id="56bae-138">오류가 발생한 후 BACKUP 작업이 계속될 경우 작업에서 다음 단계가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-138">If a BACKUP operation continues after encountering errors, the operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="56bae-139">백업 미디어의 백업 세트에 오류가 포함되었다는 플래그를 지정하고 **msdb** 데이터베이스의 **suspect_pages** 테이블에 들어 있는 페이지를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-139">Flags the backup set on the backup media as containing errors and tracks the page in the **suspect_pages** table in the **msdb** database.</span></span> <span data-ttu-id="56bae-140">자세한 내용은 [suspect_pages&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-140">For more information, see [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span></span>  
  
2.  <span data-ttu-id="56bae-141">SQL Server 오류 로그에 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-141">Logs the error in the SQL Server error log.</span></span>  
  
3.  <span data-ttu-id="56bae-142">**msdb.backupset** 의 **is_damaged**열에 이런 종류의 오류가 들어 있는 것으로 백업 세트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-142">Marks the backup set as containing this type of error (in the **is_damaged** column of **msdb.backupset)**.</span></span> <span data-ttu-id="56bae-143">자세한 내용은 [backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56bae-143">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
4.  <span data-ttu-id="56bae-144">백업이 생성되었지만 페이지 오류가 있다는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56bae-144">Issues a message that the backup was successfully generated, but contains page errors.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="56bae-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="56bae-145">Related Tasks</span></span>  
 <span data-ttu-id="56bae-146">**백업 체크섬을 설정 또는 해제하려면**</span><span class="sxs-lookup"><span data-stu-id="56bae-146">**To enable or disable backup checksums**</span></span>  
  
-   [<span data-ttu-id="56bae-147">백업 또는 복원 중 백업 체크섬 설정 또는 해제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="56bae-147">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 <span data-ttu-id="56bae-148">**백업 작업 중 오류에 대한 응답을 제어하려면**</span><span class="sxs-lookup"><span data-stu-id="56bae-148">**To control the response to a error during a backup operation**</span></span>  
  
-   [<span data-ttu-id="56bae-149">오류 발생 후 백업 또는 복원 작업 계속 또는 중지 여부 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="56bae-149">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a><span data-ttu-id="56bae-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56bae-150">See Also</span></span>  
 <span data-ttu-id="56bae-151">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56bae-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="56bae-152">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56bae-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="56bae-153">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56bae-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="56bae-154">[미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56bae-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 <span data-ttu-id="56bae-155">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="56bae-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="56bae-156">RESTORE VERIFYONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="56bae-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
