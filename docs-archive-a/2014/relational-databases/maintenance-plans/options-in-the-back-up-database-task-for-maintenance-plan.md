---
title: 데이터베이스 백업 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.backup.f1
- sql12.swb.maint.maintplanproperties.logbackup.f1
helpviewer_keywords:
- Back Up Database Task dialog box
ms.assetid: ed1ef012-fa14-4ba5-bafe-d1527ba065b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 952730f09deeede360dff5e2bd83f8cdc8a20a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649519"
---
# <a name="back-up-database-task-maintenance-plan"></a><span data-ttu-id="c7b0b-102">데이터베이스 백업 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="c7b0b-102">Back Up Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="c7b0b-103">**데이터베이스 백업 태스크** 대화 상자를 사용하여 유지 관리 계획에 백업 작업을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-103">Use the **Back Up Database Task** dialog to add a backup task to the maintenance plan.</span></span> <span data-ttu-id="c7b0b-104">데이터베이스 백업은 시스템이나 하드웨어 상의 장애 또는 사용자의 오류로 인해 데이터베이스가 손상되어 백업 복사본을 복원해야 하는 경우를 대비하기 위한 중요한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-104">Backing up the database is important in case of system or hardware failure (or user errors) that cause the database to be damaged in some way, thus requiring a backed-up copy to be restored.</span></span> <span data-ttu-id="c7b0b-105">이 태스크를 통해 전체 백업, 차등 백업, 파일 및 파일 그룹 백업, 트랜잭션 로그 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-105">This task allows you to perform full, differential, files and filegroups, and transaction log backups.</span></span>  
  
 <span data-ttu-id="c7b0b-106">**데이터베이스 백업 태스크를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-106">**To create a backup database task**</span></span>  
  
-   [<span data-ttu-id="c7b0b-107">유지 관리 계획 만들기</span><span class="sxs-lookup"><span data-stu-id="c7b0b-107">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
## <a name="options"></a><span data-ttu-id="c7b0b-108">옵션</span><span class="sxs-lookup"><span data-stu-id="c7b0b-108">Options</span></span>  
 <span data-ttu-id="c7b0b-109">**연결**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-109">**Connection**</span></span>  
 <span data-ttu-id="c7b0b-110">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="c7b0b-111">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-111">**New**</span></span>  
 <span data-ttu-id="c7b0b-112">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="c7b0b-113">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="c7b0b-114">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-114">**Databases**</span></span>  
 <span data-ttu-id="c7b0b-115">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-115">Specify the databases affected by this task.</span></span> <span data-ttu-id="c7b0b-116">이 옵션을 선택하면 **모든 데이터베이스**, **모든 시스템 데이터베이스**, **모든 사용자 데이터베이스**, **다음 데이터베이스** 옵션을 제공하는 드롭다운 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-116">When selected, the drop down list provides the following options: **All databases**, **All system databases**, **All user databases**, **These specific databases**.</span></span>  
  
 <span data-ttu-id="c7b0b-117">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-117">**All databases**</span></span>  
 <span data-ttu-id="c7b0b-118">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-118">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="c7b0b-119">**모든 시스템 데이터베이스(master, msdb, model)**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-119">**All system databases (master, msdb, model)**</span></span>  
 <span data-ttu-id="c7b0b-120">각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-120">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span> <span data-ttu-id="c7b0b-121">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-121">No maintenance tasks are run against user-created databases.</span></span>  
  
 <span data-ttu-id="c7b0b-122">**모든 사용자 데이터베이스(master, model, msdb, tempdb 제외)**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-122">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
 <span data-ttu-id="c7b0b-123">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-123">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="c7b0b-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-124">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
 <span data-ttu-id="c7b0b-125">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-125">**These databases**</span></span>  
 <span data-ttu-id="c7b0b-126">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-126">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="c7b0b-127">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-127">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="c7b0b-128">**백업 유형**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-128">**Backup type**</span></span>  
 <span data-ttu-id="c7b0b-129">수행할 백업 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-129">Shows the type of backup to be performed.</span></span>  
  
 <span data-ttu-id="c7b0b-130">**백업 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-130">**Backup component**</span></span>  
 <span data-ttu-id="c7b0b-131">전체 데이터베이스를 백업하려면 **데이터베이스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-131">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="c7b0b-132">데이터베이스 일부만 백업하려면 **파일 및 파일 그룹** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-132">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="c7b0b-133">이 옵션을 선택한 경우 파일 또는 파일 그룹 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-133">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="c7b0b-134">**데이터베이스** 상자에서 여러 데이터베이스를 선택한 경우에는 **백업 구성 요소** 에 대해 **데이터베이스**만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-134">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="c7b0b-135">파일 또는 파일 그룹 백업을 수행하려면 각 데이터베이스에 대해 태스크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-135">To perform file or filegroup backups, create a task for each database.</span></span>  
  
 <span data-ttu-id="c7b0b-136">**백업 세트 만료 기한**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-136">**Backup set will expire**</span></span>  
 <span data-ttu-id="c7b0b-137">백업 세트를 다른 백업 세트로 덮어쓸 수 있는 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-137">Specify when the backup set can be overwritten by another backup set.</span></span>  
  
 <span data-ttu-id="c7b0b-138">**백업할 위치**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-138">**Back up to**</span></span>  
 <span data-ttu-id="c7b0b-139">파일 또는 테이프에 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-139">Back up the database to a file or to tape.</span></span> <span data-ttu-id="c7b0b-140">데이터베이스를 포함하는 컴퓨터에 연결된 테이프 디바이스만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-140">Only tape devices attached to the computer containing the database are available.</span></span>  
  
 <span data-ttu-id="c7b0b-141">**하나 이상의 파일에 데이터베이스 백업**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-141">**Back up databases across one or more files**</span></span>  
 <span data-ttu-id="c7b0b-142">**추가** 를 클릭하여 **백업 대상 선택** 대화 상자를 연 다음 하나 이상의 디스크 위치나 테이프 디바이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-142">Click **Add** to open the **Select Backup Destination** dialog box, and provide one or more a disk location, or tape device.</span></span>  
  
 <span data-ttu-id="c7b0b-143">**백업 파일이 있는 경우**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-143">**If backup files exist**</span></span>  
 <span data-ttu-id="c7b0b-144">파일의 끝에 이 백업을 추가하려면 **추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-144">Select **Append** to add this backup to the end of the file.</span></span> <span data-ttu-id="c7b0b-145">파일의 이전 백업을 모두 제거하고 새 백업으로 바꾸려면 **덮어쓰기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-145">Select **Overwrite**, to remove any old backup in the file and replace them with this new backup.</span></span>  
  
 <span data-ttu-id="c7b0b-146">**모든 데이터베이스에 대한 백업 파일 만들기**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-146">**Create a backup file for every database**</span></span>  
 <span data-ttu-id="c7b0b-147">폴더 상자에서 지정한 위치에 백업 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-147">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="c7b0b-148">선택한 데이터베이스당 하나의 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-148">One file will be created for each database selected.</span></span>  
  
 <span data-ttu-id="c7b0b-149">**각 데이터베이스에 대한 하위 디렉터리 만들기**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-149">**Create a sub-directory for each database**</span></span>  
 <span data-ttu-id="c7b0b-150">각 데이터베이스를 하위 폴더에 저장하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-150">Select to place each database in a subfolder.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7b0b-151">유지 관리 계획으로 하위 디렉터리를 만들 수는 있지만 의 유지 관리 태스크로 하위 디렉터리를 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-151">Although maintenance plans can create subdirectories, maintenance tasks cannot delete subdirectories.</span></span> <span data-ttu-id="c7b0b-152">이 기능은 유지 관리 정리 태스크를 사용하여 파일을 삭제하는 악의적 공격의 가능성을 줄여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-152">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7b0b-153">하위 디렉터리는 부모 디렉터리에서 사용 권한을 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-153">The subdirectory inherits permissions from the parent directory.</span></span> <span data-ttu-id="c7b0b-154">무단으로 액세스하지 못하도록 하려면 사용 권한을 제한하세요.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-154">Restrict permissions to avoid unauthorized access.</span></span>  
  
 <span data-ttu-id="c7b0b-155">**폴더**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-155">**Folder**</span></span>  
 <span data-ttu-id="c7b0b-156">자동으로 생성된 데이터베이스 파일을 포함할 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-156">Specify the folder to contain the automatically created database files.</span></span>  
  
 <span data-ttu-id="c7b0b-157">**백업 파일 확장명**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-157">**Backup file extension**</span></span>  
 <span data-ttu-id="c7b0b-158">백업 파일에 사용할 확장명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-158">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="c7b0b-159">기본값은 **.bak**입니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-159">The default is **.bak**.</span></span>  
  
 <span data-ttu-id="c7b0b-160">**백업 무결성 확인**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-160">**Verify backup integrity**</span></span>  
 <span data-ttu-id="c7b0b-161">백업 세트가 올바른지 확인하고 모든 볼륨을 읽을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-161">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="c7b0b-162">**비상 로그 백업을 수행하고 복원 중인 상태로 데이터베이스 유지**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-162">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="c7b0b-163">데이터베이스를 복원하기 전의 마지막 단계로 로그 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-163">Perform a log backup as the last step before restoring a database.</span></span> <span data-ttu-id="c7b0b-164">자세한 내용은 [비상 로그 백업&#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="c7b0b-165">**백업 압축 설정**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-165">**Set backup compression**</span></span>  
 <span data-ttu-id="c7b0b-166">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (이상 버전)에서 다음 [백업 압축](../backup-restore/backup-compression-sql-server.md) 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-166">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7b0b-167">**기본 서버 설정 사용**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-167">**Use the default server setting**</span></span>|<span data-ttu-id="c7b0b-168">서버 수준 기본값을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-168">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="c7b0b-169">이 기본값은 **백업 압축 기본값** 서버 구성 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-169">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="c7b0b-170">이 옵션의 현재 설정을 확인하는 방법은 [backup compression default 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-170">For information about how to view the current setting of this option,  see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="c7b0b-171">**백업 압축**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-171">**Compress backup**</span></span>|<span data-ttu-id="c7b0b-172">서버 수준 기본값에 관계없이 백업을 압축하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-172">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="c7b0b-173">**\*\* 중요 \*\*** 압축 시에는 기본적으로 CPU 사용량이 크게 증가하며, 압축 프로세스에서 CPU를 추가로 사용하므로 동시 작업 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-173">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="c7b0b-174">따라서 CPU 사용량이 [리소스 관리자](../resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-174">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="c7b0b-175">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-175">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="c7b0b-176">**백업 압축 안 함**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-176">**Do not compress backup**</span></span>|<span data-ttu-id="c7b0b-177">서버 수준 기본값에 관계없이 압축되지 않은 백업을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-177">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
 <span data-ttu-id="c7b0b-178">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-178">**View T-SQL**</span></span>  
 <span data-ttu-id="c7b0b-179">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-179">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7b0b-180">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-180">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="c7b0b-181">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="c7b0b-181">New Connection Dialog Box</span></span>  
 <span data-ttu-id="c7b0b-182">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-182">**Connection name**</span></span>  
 <span data-ttu-id="c7b0b-183">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-183">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="c7b0b-184">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-184">**Select or enter a server name**</span></span>  
 <span data-ttu-id="c7b0b-185">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-185">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="c7b0b-186">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-186">**Refresh**</span></span>  
 <span data-ttu-id="c7b0b-187">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-187">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="c7b0b-188">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-188">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="c7b0b-189">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-189">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="c7b0b-190">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-190">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="c7b0b-191">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-191">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="c7b0b-192">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-192">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="c7b0b-193">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-193">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c7b0b-194">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-194">This option is not available.</span></span>  
  
 <span data-ttu-id="c7b0b-195">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-195">**User name**</span></span>  
 <span data-ttu-id="c7b0b-196">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-196">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="c7b0b-197">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-197">This option is not available.</span></span>  
  
 <span data-ttu-id="c7b0b-198">**암호**</span><span class="sxs-lookup"><span data-stu-id="c7b0b-198">**Password**</span></span>  
 <span data-ttu-id="c7b0b-199">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-199">Provide a password to use when authenticating.</span></span> <span data-ttu-id="c7b0b-200">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b0b-200">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b0b-201">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7b0b-201">See Also</span></span>  
 [<span data-ttu-id="c7b0b-202">BACKUP&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7b0b-202">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
  
