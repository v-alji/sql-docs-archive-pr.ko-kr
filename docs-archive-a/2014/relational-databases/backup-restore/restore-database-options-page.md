---
title: 데이터베이스 복원(옵션 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.options.f1
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d60474b5d72ab9745500325dfd523f83f155343c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650128"
---
# <a name="restore-database-options-page"></a><span data-ttu-id="49155-102">데이터베이스 복원(옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="49155-102">Restore Database (Options Page)</span></span>
  <span data-ttu-id="49155-103">**데이터베이스 복원** 대화 상자의 **옵션** 페이지를 사용하여 복원 작업의 동작 및 결과를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-103">Use the **Options** page of the **Restore Database** dialog box to modify the behavior and outcome of the restore operation.</span></span>  
  
 <span data-ttu-id="49155-104">**SQL Server Management Studio를 사용하여 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="49155-104">**To use SQL Server Management Studio to restore a database backup**</span></span>  
  
-   [<span data-ttu-id="49155-105">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49155-105">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [<span data-ttu-id="49155-106">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="49155-106">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="49155-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 복원 태스크를 지정할 때 이 복원 작업에 대해 RESTORE 문을 포함하는 해당 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-107">When you specify a restore task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate a corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] script containing the RESTORE statements for this restore operation.</span></span> <span data-ttu-id="49155-108">스크립트를 생성하려면 **스크립트** 를 클릭한 다음 스크립트 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-108">To generate the script, click **Script** and then select a destination for the script.</span></span> <span data-ttu-id="49155-109">RESTORE 구문에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49155-109">For information about the RESTORE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="49155-110">옵션</span><span class="sxs-lookup"><span data-stu-id="49155-110">Options</span></span>  
  
### <a name="restore-options"></a><span data-ttu-id="49155-111">복원 옵션</span><span class="sxs-lookup"><span data-stu-id="49155-111">Restore options</span></span>  
 <span data-ttu-id="49155-112">복원 작업의 동작 측면을 수정하려면 **복원 옵션** 패널의 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-112">To modify aspects of the behavior of the restore operation, use the options of the **Restore options** panel.</span></span>  
  
 <span data-ttu-id="49155-113">**기존 데이터베이스 덮어쓰기[WITH REPLACE]**</span><span class="sxs-lookup"><span data-stu-id="49155-113">**Overwrite the existing database [WITH REPLACE]**</span></span>  
 <span data-ttu-id="49155-114">**데이터베이스 복원**대화 상자에 있는 [일반](../../integration-services/general-page-of-integration-services-designers-options.md) 페이지의 **복원 위치** 필드에서 지정하는 데이터베이스 이름을 현재 사용 중인 모든 데이터베이스의 파일을 복원 작업에서 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="49155-114">The restore operation will overwrite the files of any database that is currently using the database name that you are specifying in the **Restore to**field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Restore Database** dialog box.</span></span> <span data-ttu-id="49155-115">다른 데이터베이스에서 기존 데이터베이스 이름으로 백업을 복원하는 중이더라도 기존 데이터베이스의 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="49155-115">The files of the existing database will be overwritten even if you are restoring backups from a different database to the existing database name.</span></span> <span data-ttu-id="49155-116">이 옵션을 선택하는 것은 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 문에서 REPLACE 옵션을 사용하는 것과 같습니다.([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="49155-116">Selecting this option is equivalent to using the REPLACE option in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="49155-117">이 옵션은 신중하게 고려한 후에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-117">Use this option only after careful consideration.</span></span> <span data-ttu-id="49155-118">자세한 내용은 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49155-118">For more information, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
 <span data-ttu-id="49155-119">**복제 설정 유지[WITH KEEP_REPLICATION]**</span><span class="sxs-lookup"><span data-stu-id="49155-119">**Preserve the replication settings [WITH KEEP_REPLICATION]**</span></span>  
 <span data-ttu-id="49155-120">게시된 데이터베이스를 해당 데이터베이스가 생성된 서버 이외의 다른 서버로 복원할 경우 복제 설정을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-120">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span> <span data-ttu-id="49155-121">이 옵션은 백업을 만들 때 데이터베이스가 복제된 경우에만 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-121">This option is relevant only if the database was replicated when the backup was created.</span></span>  
  
 <span data-ttu-id="49155-122">이 옵션은 RECOVERY 옵션을 사용하여 백업을 복원하는 것과 같은 **커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용할 수 있는 상태로 유지합니다.** 옵션(이 표의 뒷부분에서 설명)과 함께만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-122">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions** option (described later in this table), which is equivalent to restoring a backup with the RECOVERY option.</span></span>  
  
 <span data-ttu-id="49155-123">이 옵션을 선택하는 것은 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문에서 KEEP_REPLICATION 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-123">Selecting this option is equivalent to using the KEEP_REPLICATION option in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="49155-124">자세한 내용은 [복제된 데이터베이스 백업 및 복원](../replication/administration/back-up-and-restore-replicated-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49155-124">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
 <span data-ttu-id="49155-125">**복원된 데이터베이스에 대한 액세스 제한[WITH RESTRICTED_USER]**</span><span class="sxs-lookup"><span data-stu-id="49155-125">**Restrict access to the restored database [WITH RESTRICTED_USER]**</span></span>  
 <span data-ttu-id="49155-126">**db_owner**, **dbcreator**또는 **sysadmin**의 멤버만 복원된 데이터베이스를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-126">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
 <span data-ttu-id="49155-127">이 옵션을 선택하는 것은 RESTORE 문에서 RESTRICTED_USER 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-127">Selecting this option is synonymous to using the RESTRICTED_USER option in a RESTORE statement.</span></span>  
  
### <a name="recovery-state"></a><span data-ttu-id="49155-128">복구 상태</span><span class="sxs-lookup"><span data-stu-id="49155-128">Recovery state</span></span>  
 <span data-ttu-id="49155-129">저장 작업 후에 데이터베이스의 상태를 확인하려면 **복구 상태** 패널의 옵션 중 하나를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-129">To determine the state of the database after the store operation, you must select one of the options of the **Recovery state** panel.</span></span>  
  
 <span data-ttu-id="49155-130">**RESTORE WITH RECOVERY**</span><span class="sxs-lookup"><span data-stu-id="49155-130">**RESTORE WITH RECOVERY**</span></span>  
 <span data-ttu-id="49155-131">**일반 페이지**의 [복원에 사용할 백업 세트](../../integration-services/general-page-of-integration-services-designers-options.md)표에서 선택된 최종 백업을 복원한 후에 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-131">Recovers the database after restoring the final backup checked in the **Backup sets to restore**grid on the [General page](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="49155-132">이는 기본 옵션이고 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 문([!INCLUDE[tsql](../../includes/tsql-md.md)])에서 WITH RECOVERY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-132">This is the default option and is equivalent to specifying WITH RECOVERY in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49155-133">전체 복구 모델 또는 대량 로그 복구 모델에서 모든 로그 파일을 지금 복원하는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-133">Under the full recovery model or bulk-logged recovery model, choose this option only if you are restoring all the log files now.</span></span>  
  
 <span data-ttu-id="49155-134">**RESTORE WITH NORECOVERY**</span><span class="sxs-lookup"><span data-stu-id="49155-134">**RESTORE WITH NORECOVERY**</span></span>  
 <span data-ttu-id="49155-135">데이터베이스를 복원 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-135">Leaves the database in the restoring state.</span></span> <span data-ttu-id="49155-136">현재 복구 경로에서 추가 백업을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-136">This allows you to restore additional backups in the current recovery path.</span></span> <span data-ttu-id="49155-137">데이터베이스를 복구하려면 RESTORE WITH RECOVERY 옵션을 사용하여 복원 작업을 수행해야 합니다(이전 옵션 참조).</span><span class="sxs-lookup"><span data-stu-id="49155-137">To recover the database, you will have to perform a restore operation by using the RESTORE WITH RECOVERY option (see the preceding option).</span></span>  
  
 <span data-ttu-id="49155-138">이 옵션은 RESTORE 문에서 WITH NORECOVERY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-138">This option is equivalent to specifying WITH NORECOVERY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="49155-139">이 옵션을 선택하면 **복제 설정 유지** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-139">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
 <span data-ttu-id="49155-140">**RESTORE WITH STANDBY**</span><span class="sxs-lookup"><span data-stu-id="49155-140">**RESTORE WITH STANDBY**</span></span>  
 <span data-ttu-id="49155-141">제한된 읽기 전용 액세스로 데이터베이스를 사용할 수 있도록 데이터베이스를 대기 모드로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-141">Leaves the database in a standby state, in which the database is available for limited read-only access.</span></span> <span data-ttu-id="49155-142">이 옵션은 RESTORE 문에서 WITH STANDBY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-142">This option is equivalent to specifying WITH STANDBY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="49155-143">이 옵션을 선택하면 **대기 파일** 입력란에서 대기 파일을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-143">Choosing this option requires that you specify a standby file in the **Standby file** text box.</span></span> <span data-ttu-id="49155-144">대기 파일은 복구 결과를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-144">The standby file allows the recovery effects to be undone.</span></span>  
  
 <span data-ttu-id="49155-145">**대기 파일**</span><span class="sxs-lookup"><span data-stu-id="49155-145">**Standby file**</span></span>  
 <span data-ttu-id="49155-146">대기 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-146">Specifies a standby file.</span></span> <span data-ttu-id="49155-147">대기 파일을 찾아보거나 입력란에 해당 경로 이름을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-147">You can browse for the standby file or enter its pathname directly in the text box.</span></span>  
  
### <a name="tail-log-backup"></a><span data-ttu-id="49155-148">비상 로그 백업</span><span class="sxs-lookup"><span data-stu-id="49155-148">Tail-Log backup</span></span>  
 <span data-ttu-id="49155-149">데이터베이스 복원과 함께 수행할 비상 로그 백업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-149">Allows you to designate that a tail-log backup be performed along with the database restore.</span></span>  
  
 <span data-ttu-id="49155-150">**복원 전에 비상 로그 백업 가져오기**</span><span class="sxs-lookup"><span data-stu-id="49155-150">**Take tail-Log backup before restoring**</span></span>  
 <span data-ttu-id="49155-151">비상 로그 백업을 수행하도록 지정하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-151">Check this box to designate that a tail-log backup should be performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49155-152">[백업 시간대](backup-timeline.md) 대화 상자에서 선택한 시점에 비상 로그 백업이 필요한 경우에는 이 확인란이 자동으로 선택되며 선택 사항을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-152">If the point-in-time you have selected in the [Backup Timeline](backup-timeline.md) dialog box requires a tail-log backup, this box will be selected and you will not be able to edit it.</span></span>  
  
 <span data-ttu-id="49155-153">**백업 파일**</span><span class="sxs-lookup"><span data-stu-id="49155-153">**Backup file**</span></span>  
 <span data-ttu-id="49155-154">비상 로그에 대한 백업 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-154">Specifies a backup file for the tail of the log.</span></span> <span data-ttu-id="49155-155">백업 파일을 찾아보거나 입력란에 해당 이름을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-155">You can browse for the backup file or enter its name directly in the text box.</span></span>  
  
### <a name="server-connections"></a><span data-ttu-id="49155-156">서버 연결</span><span class="sxs-lookup"><span data-stu-id="49155-156">Server connections</span></span>  
 <span data-ttu-id="49155-157">기존 데이터베이스 연결을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-157">Allows you to close existing database connections.</span></span>  
  
 <span data-ttu-id="49155-158">**기존 연결 닫기**</span><span class="sxs-lookup"><span data-stu-id="49155-158">**Close existing connections**</span></span>  
 <span data-ttu-id="49155-159">데이터베이스에 대한 활성 연결이 있으면 복원 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-159">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="49155-160">**기존 연결 닫기** 옵션을 선택하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 와 데이터베이스 간의 모든 활성 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-160">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="49155-161">이 확인란을 선택하면 복원 작업을 수행하기 전에 데이터베이스가 단일 사용자 모드로 설정되고 복원 작업이 완료될 때 데이터베이스가 다중 사용자 모드로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="49155-161">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
### <a name="prompt"></a><span data-ttu-id="49155-162">prompt</span><span class="sxs-lookup"><span data-stu-id="49155-162">Prompt</span></span>  
 <span data-ttu-id="49155-163">**각 백업 복원 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="49155-163">**Prompt before restoring each backup**</span></span>  
 <span data-ttu-id="49155-164">각 백업을 복원한 후 복원 순서를 계속할지 여부를 묻는 **복원 계속** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-164">Specifies that after each backup is restored, the **Continue with Restore** dialog box will be displayed to inquire whether you want to continue the restore sequence.</span></span> <span data-ttu-id="49155-165">이 대화 상자는 다음 미디어 세트(알려진 경우)의 이름과 다음 백업 세트의 이름 및 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-165">This dialog box displays the name of the next media set (if known) and the name and description of the next backup set.</span></span>  
  
 <span data-ttu-id="49155-166">이 옵션을 지정하면 모든 백업을 복원한 후에 복원 순서를 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-166">This option allows you to pause a restore sequence after restoring any of the backups.</span></span> <span data-ttu-id="49155-167">예를 들어 이 옵션은 서버에 테이프 디바이스가 하나만 있어 다양한 미디어 세트의 테이프를 교체해야 할 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-167">This option is particularly useful when you must swap tapes for different media sets; for example, when your server has only one tape device.</span></span> <span data-ttu-id="49155-168">계속할 준비가 되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-168">When you are ready to proceed, click **OK**.</span></span>  
  
 <span data-ttu-id="49155-169">**아니요**를 클릭하여 복원 순서를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-169">You can interrupt a restore sequence by clicking **No**.</span></span> <span data-ttu-id="49155-170">이렇게 하면 데이터베이스를 복원 중인 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="49155-170">This leaves the database is in the restoring state.</span></span> <span data-ttu-id="49155-171">사용자 편의를 위해 **복원 계속** 대화 상자에 설명된 다음 백업으로 재개하여 복원 순서를 나중에 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49155-171">At your convenience, you can later continue the restore sequence by resuming with the next backup described in the **Continue with Restore** dialog box.</span></span> <span data-ttu-id="49155-172">다음 백업 복원 절차는 다음과 같이 데이터나 트랜잭션 로그를 포함하는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="49155-172">The procedure restoring the next backup depends on whether it contains data or transaction log, as follows:</span></span>  
  
-   <span data-ttu-id="49155-173">다음 백업이 전체 백업 또는 차등 백업인 경우 **데이터베이스 복원** 태스크를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-173">If the next backup is a full or differential backup, use the **Restore Database** task again.</span></span>  
  
-   <span data-ttu-id="49155-174">다음 백업이 파일 백업인 경우 **파일 및 파일 그룹 복원**태스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-174">If the next backup is a file backup, use the **Restore Files and Filegroup**s task.</span></span> <span data-ttu-id="49155-175">자세한 내용은 [파일 및 파일 그룹 복원&#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49155-175">For more information, see [Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="49155-176">다음 백업이 로그 백업인 경우 **트랜잭션 로그 복원** 태스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49155-176">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span> <span data-ttu-id="49155-177">트랜잭션 로그를 복원하여 복원 순서를 재개하는 방법은 [트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49155-177">For information about resuming a restore sequence by restoring a transaction log, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49155-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49155-178">See Also</span></span>  
 <span data-ttu-id="49155-179">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="49155-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="49155-180">[디바이스에서 백업 복원&#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49155-180">[Restore a Backup from a Device &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span></span>  
 <span data-ttu-id="49155-181">[트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49155-181">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="49155-182">[미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49155-182">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="49155-183">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49155-183">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="49155-184">데이터베이스 복원&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="49155-184">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
