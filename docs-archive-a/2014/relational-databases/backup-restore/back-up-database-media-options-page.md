---
title: 데이터베이스 백업(미디어 옵션 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- swb.backupdatabase.mediaoptions.f1
- sql12.swb.backupdatabase.mediaoptions.f1
ms.assetid: eff36228-710c-4ed5-9af5-95859575dc0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd09eb091a7f488f891bc2e69d19ad039b65e065
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735380"
---
# <a name="back-up-database-media-options-page"></a><span data-ttu-id="50d77-102">데이터베이스 백업(미디어 옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="50d77-102">Back Up Database (Media Options Page)</span></span>
  <span data-ttu-id="50d77-103">**데이터베이스 백업** 대화 상자의 **미디어 옵션** 페이지를 사용하여 데이터베이스 미디어 옵션을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-103">Use the  **Media Options** page of the **Back Up Database** dialog box to view or modify database media options.</span></span>  
  
 <span data-ttu-id="50d77-104">**SQL Server Management Studio를 사용하여 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="50d77-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="50d77-105">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="50d77-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="50d77-106">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="50d77-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50d77-107">데이터베이스 유지 관리 계획을 정의하여 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="50d77-108">자세한 내용은 [유지 관리 계획](../maintenance-plans/maintenance-plans.md) 및 [유지 관리 계획 마법사 사용](../maintenance-plans/use-the-maintenance-plan-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50d77-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 백업 태스크를 지정할 때 [!INCLUDE[tsql](../../includes/tsql-md.md)][스크립트](/sql/t-sql/statements/backup-transact-sql) 단추를 클릭한 다음 스크립트에 대한 대상을 선택하여 해당되는 **BACKUP** 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="50d77-110">옵션</span><span class="sxs-lookup"><span data-stu-id="50d77-110">Options</span></span>  
  
### <a name="overwrite-media"></a><span data-ttu-id="50d77-111">미디어 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="50d77-111">Overwrite media</span></span>  
 <span data-ttu-id="50d77-112">**미디어 덮어쓰기** 패널의 옵션은 백업이 미디어에 쓰여지는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-112">The options of the **Overwrite media** panel control how the backup is written to the media.</span></span> <span data-ttu-id="50d77-113">URL(Azure Storage)을 데이터베이스 백업 대화 상자의 일반 페이지에 있는 백업 대상으로 선택한 경우 미디어 덮어쓰기 섹션의 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-113">IF you selected URL (Azure Storage) as the backup destination on the General page of the Back Up Database dialog box, the options under the Overwrite media section are disabled.</span></span> <span data-ttu-id="50d77-114">`BACKUP TO URL.. WITH FORMAT` Transact-SQL 문을 사용하여 백업을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-114">You can overwrite a backup using the `BACKUP TO URL.. WITH FORMAT` Transact-SQL statement.</span></span> <span data-ttu-id="50d77-115">자세한 내용은 [URL에 대한 SQL Server Backup](sql-server-backup-to-url.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-115">For more information, see [SQL Server Backup to URL](sql-server-backup-to-url.md).</span></span>  
  
 <span data-ttu-id="50d77-116">**새 미디어에 백업하고 기존 백업 세트 모두 지우기** 옵션만 암호화 옵션과 함께 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-116">Only the option, **Backup to a new media, and erase all existing backup sets** is supported with encryption options.</span></span> <span data-ttu-id="50d77-117">**기존 미디어에 백업** 섹션의 옵션을 선택하는 경우 **백업 옵션** 페이지의 암호화 옵션을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-117">If you select the options under the **Back up to existing media** section, the encryptions options on the **Backup Options** page will be disabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50d77-118">미디어 세트에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)인스턴스를 실행하는 컴퓨터에 테이프 드라이브가 연결되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-118">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="50d77-119">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="50d77-119">**Back up to the existing media set**</span></span>  
 <span data-ttu-id="50d77-120">데이터베이스를 기존 미디어 세트에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-120">Back up a database to an existing media set.</span></span> <span data-ttu-id="50d77-121">이 옵션 단추를 선택하면 세 개의 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-121">Selecting this option button activates three options.</span></span>  
  
 <span data-ttu-id="50d77-122">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-122">Choose one of the following options:</span></span>  
  
 <span data-ttu-id="50d77-123">**기존 백업 세트에 추가**</span><span class="sxs-lookup"><span data-stu-id="50d77-123">**Append to the existing backup set**</span></span>  
 <span data-ttu-id="50d77-124">모든 이전 백업을 유지하면서 백업 세트를 기존 미디어 세트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-124">Append the backup set to the existing media set, preserving any prior backups.</span></span>  
  
 <span data-ttu-id="50d77-125">**기존 백업 세트 모두 덮어쓰기**</span><span class="sxs-lookup"><span data-stu-id="50d77-125">**Overwrite all existing backup sets**</span></span>  
 <span data-ttu-id="50d77-126">기존 미디어 세트의 모든 이전 백업을 현재 백업으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-126">Replace any prior backups on the existing media set with the current backup.</span></span>  
  
 <span data-ttu-id="50d77-127">**미디어 세트 이름 및 백업 세트 만료 확인**</span><span class="sxs-lookup"><span data-stu-id="50d77-127">**Check media set name and backup set expiration**</span></span>  
 <span data-ttu-id="50d77-128">상황에 따라 기존 미디어 세트로 백업할 경우 백업 세트의 만료 날짜 및 이름을 식별하기 위해 백업 작업이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-128">Optionally, if backing up to an existing media set, require the backup operation to verify the name and the expiration date of the backup sets.</span></span>  
  
 <span data-ttu-id="50d77-129">**미디어 세트 이름**</span><span class="sxs-lookup"><span data-stu-id="50d77-129">**Media set name**</span></span>  
 <span data-ttu-id="50d77-130">**미디어 세트 이름 및 백업 세트 만료 확인** 을 선택한 경우 필요에 따라 이 백업 작업에 사용되는 미디어 세트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-130">If **Check media set name and backup set expiration** is selected, optionally, specify the name of the media set to be used for this backup operation.</span></span>  
  
 <span data-ttu-id="50d77-131">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="50d77-131">**Back up to a new media set, and erase all existing backup sets**</span></span>  
 <span data-ttu-id="50d77-132">이전 백업 세트를 지우고 새 미디어 세트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-132">Use a new media set, erasing the previous backup sets.</span></span>  
  
 <span data-ttu-id="50d77-133">이 옵션을 클릭하면 다음 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-133">Clicking this option activates the following options:</span></span>  
  
 <span data-ttu-id="50d77-134">**새 미디어 세트 이름**</span><span class="sxs-lookup"><span data-stu-id="50d77-134">**New media set name**</span></span>  
 <span data-ttu-id="50d77-135">필요에 따라 미디어 세트의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-135">Optionally, enter a new name for the media set.</span></span>  
  
 <span data-ttu-id="50d77-136">**새 미디어 세트 설명**</span><span class="sxs-lookup"><span data-stu-id="50d77-136">**New media set description**</span></span>  
 <span data-ttu-id="50d77-137">필요에 따라 새 미디어 세트에 대한 이해하기 쉬운 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-137">Optionally, enter a meaningful description of the new media set.</span></span> <span data-ttu-id="50d77-138">이 설명은 내용을 정확하게 전달할 수 있을 만큼 구체적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-138">This description should be specific enough to communicate the contents accurately.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="50d77-139">안정성</span><span class="sxs-lookup"><span data-stu-id="50d77-139">Reliability</span></span>  
 <span data-ttu-id="50d77-140">**트랜잭션 로그** 패널의 옵션은 백업 작업으로 오류 관리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-140">The options of the **Transaction log** panel control error management by the backup operation.</span></span>  
  
 <span data-ttu-id="50d77-141">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="50d77-141">**Verify backup when finished**</span></span>  
 <span data-ttu-id="50d77-142">백업 세트가 올바른지 확인하고 모든 볼륨을 읽을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-142">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="50d77-143">**미디어에 쓰기 전에 체크섬 수행**</span><span class="sxs-lookup"><span data-stu-id="50d77-143">**Perform checksum before writing to media**</span></span>  
 <span data-ttu-id="50d77-144">백업 미디어에 쓰기 전에 체크섬을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-144">Verify the checksums before writing to the backup media.</span></span> <span data-ttu-id="50d77-145">이 옵션을 선택하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 BACKUP 문에서 CHECKSUM 옵션을 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-145">Selecting this option is equivalent to specifying the CHECKSUM option in the BACKUP statement of [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="50d77-146">이 옵션을 선택하면 작업이 증가하여 백업 작업의 백업 처리량이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-146">Selecting this option may increase the workload, and decrease the backup throughput of the backup operation.</span></span> <span data-ttu-id="50d77-147">백업 체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-147">For information about backup checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
 <span data-ttu-id="50d77-148">**오류 발생 시 계속**</span><span class="sxs-lookup"><span data-stu-id="50d77-148">**Continue on error**</span></span>  
 <span data-ttu-id="50d77-149">하나 이상의 오류가 발생한 다음에도 백업 작업이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-149">The backup operation is to continue even after encountering one or more errors.</span></span>  
  
### <a name="transaction-log"></a><span data-ttu-id="50d77-150">트랜잭션 로그</span><span class="sxs-lookup"><span data-stu-id="50d77-150">Transaction log</span></span>  
 <span data-ttu-id="50d77-151">**트랜잭션 로그** 패널의 옵션은 트랜잭션 로그 백업의 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-151">The options of the **Transaction log** panel control the behavior of a transaction log backup.</span></span> <span data-ttu-id="50d77-152">이러한 옵션은 전체 복구 모델 또는 대량 로그 복구 모델에서만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-152">These options are relevant only under the full recovery model or bulk-logged recovery model.</span></span> <span data-ttu-id="50d77-153">**트랜잭션 로그** 가 **데이터베이스 백업** 대화 상자의 [일반](../../integration-services/general-page-of-integration-services-designers-options.md) 페이지에 있는 **백업 유형** 필드에서 선택된 경우에만 이 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-153">They are activated only if **Transaction log** has been selected in the **Backup type** field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50d77-154">트랜잭션 로그 백업에 대한 자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-154">For information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="50d77-155">**트랜잭션 로그 잘라내기**</span><span class="sxs-lookup"><span data-stu-id="50d77-155">**Truncate the transaction log**</span></span>  
 <span data-ttu-id="50d77-156">트랜잭션 로그를 백업한 다음 잘라 로그 공간을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-156">Back up the transaction log and truncate it to free log space.</span></span> <span data-ttu-id="50d77-157">데이터베이스는 온라인 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-157">The database remains online.</span></span> <span data-ttu-id="50d77-158">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-158">This is the default option.</span></span>  
  
 <span data-ttu-id="50d77-159">**비상 로그 백업을 수행하고 복원 중인 상태로 데이터베이스 유지**</span><span class="sxs-lookup"><span data-stu-id="50d77-159">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="50d77-160">비상 로그 백업을 수행하고 데이터베이스를 복원 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-160">Back up the tail of the log and leave the database in a restoring state.</span></span> <span data-ttu-id="50d77-161">이 옵션을 사용하여 일반적으로 데이터베이스 복원 준비 과정에서 백업되지 않은 로그(활성 로그)를 백업하는 *비상 로그 백업*을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-161">This option creates a *tail-log backup*, which backs up logs that have not yet been backed up (the active log), typically, in preparation for restoring a database.</span></span> <span data-ttu-id="50d77-162">데이터베이스가 완전히 복원되기 전까지는 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-162">The database will be unavailable to users until it is completely restored.</span></span>  
  
 <span data-ttu-id="50d77-163">이 옵션을 선택하는 것은 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문([!INCLUDE[tsql](../../includes/tsql-md.md)])에서 WITH NO_TRUNCATE, NORECOVERY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-163">Selecting this option is equivalent to specifying WITH NO_TRUNCATE, NORECOVERY in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span> <span data-ttu-id="50d77-164">자세한 내용은 [비상 로그 백업&#40;SQL Server&#41;](tail-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
### <a name="tape-drive"></a><span data-ttu-id="50d77-165">테이프 드라이브</span><span class="sxs-lookup"><span data-stu-id="50d77-165">Tape drive</span></span>  
 <span data-ttu-id="50d77-166">**테이프 드라이브** 패널의 옵션은 백업 작업 동안 테이프 관리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-166">The options of the **Tape drive** panel control tape management during the backup operation.</span></span> <span data-ttu-id="50d77-167">**테이프** 가 **데이터베이스 백업** 대화 상자의 [일반](../../integration-services/general-page-of-integration-services-designers-options.md) 페이지에 있는 **대상** 필드에서 선택된 경우에만 이 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-167">These options are activated only if **Tape** has been selected in the **Destination** panel on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50d77-168">테이프 디바이스를 사용하는 방법은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50d77-168">For information about how to use tape devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="50d77-169">**백업 후 테이프 언로드**</span><span class="sxs-lookup"><span data-stu-id="50d77-169">**Unload the tape after backup**</span></span>  
 <span data-ttu-id="50d77-170">백업이 완료된 후 테이프를 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-170">After the backup is complete, unload the tape.</span></span>  
  
 <span data-ttu-id="50d77-171">**언로드 전에 테이프 되감기**</span><span class="sxs-lookup"><span data-stu-id="50d77-171">**Rewind the tape before unloading**</span></span>  
 <span data-ttu-id="50d77-172">테이프를 언로드하기 전에 되감습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-172">Before unloading the tape, release and rewind it.</span></span> <span data-ttu-id="50d77-173">**백업 후 테이프 언로드** 를 선택한 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50d77-173">This is enabled only if **Unload the tape after backup** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d77-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50d77-174">See Also</span></span>  
 <span data-ttu-id="50d77-175">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="50d77-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="50d77-176">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="50d77-176">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="50d77-177">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="50d77-177">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="50d77-178">데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="50d77-178">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
