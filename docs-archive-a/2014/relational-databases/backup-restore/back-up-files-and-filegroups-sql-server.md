---
title: 파일 및 파일 그룹 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up filegroups [SQL Server]
- file backups [SQL Server], how-to topics
- backing up files [SQL Server]
- backups [SQL Server], creating
- filegroups [SQL Server], backing up
ms.assetid: a0d3a567-7d8b-4cfe-a505-d197b9a51f70
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7affc90b064febaa70e0a67108074f412b4bbf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646546"
---
# <a name="back-up-files-and-filegroups-sql-server"></a><span data-ttu-id="1a1ed-102">파일 및 파일 그룹 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1a1ed-102">Back Up Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="1a1ed-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 파일 및 파일 그룹을 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-103">This topic describes how to back up files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="1a1ed-104">데이터베이스 크기와 성능 요구 사항으로 인해 전체 데이터베이스 백업이 불가능할 경우 이를 대신하여 파일 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-104">When the database size and performance requirements make a full database backup impractical, you can create a file backup instead.</span></span> <span data-ttu-id="1a1ed-105">*파일 백업* 에는 하나 이상의 파일(또는 파일 그룹)에 있는 모든 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-105">A *file backup* contains all the data in one or more files (or filegroups).</span></span> <span data-ttu-id="1a1ed-106">파일 백업에 대한 자세한 내용은 [전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md) 및 [차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-106">For more information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) and [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="1a1ed-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1a1ed-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1a1ed-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1a1ed-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1a1ed-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1a1ed-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1a1ed-111">보안</span><span class="sxs-lookup"><span data-stu-id="1a1ed-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1a1ed-112">**다음을 사용하여 파일 및 파일 그룹을 백업합니다.**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-112">**To back up files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="1a1ed-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1a1ed-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1a1ed-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a1ed-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1a1ed-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a1ed-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a1ed-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1a1ed-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1a1ed-117">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1a1ed-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1a1ed-118">명시적 또는 암시적 트랜잭션에서는 BACKUP 문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-118">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="1a1ed-119">단순 복구 모델에서 읽기/쓰기 파일은 모두 함께 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-119">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="1a1ed-120">이렇게 하면 데이터베이스를 일정한 지정 시간으로 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-120">This helps make sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="1a1ed-121">각 읽기/쓰기 파일 또는 파일 그룹을 개별적으로 지정하는 대신 READ_WRITE_FILEGROUPS 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-121">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="1a1ed-122">이 옵션은 데이터베이스의 모든 읽기/쓰기 파일 그룹을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-122">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="1a1ed-123">READ_WRITE_FILEGROUPS를 지정 하 여 만드는 백업을 *부분 백업*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-123">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a *partial backup*.</span></span> <span data-ttu-id="1a1ed-124">자세한 내용은 [부분 백업&#40;SQL Server&#41;](partial-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-124">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1a1ed-125">제한 사항에 대한 자세한 내용은 [백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-125">For more information about limitations and restrictions, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1a1ed-126">권장 사항</span><span class="sxs-lookup"><span data-stu-id="1a1ed-126">Recommendations</span></span>  
  
-   <span data-ttu-id="1a1ed-127">기본적으로 백업 작업을 성공적으로 수행할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 시스템 이벤트 로그에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-127">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="1a1ed-128">로그를 자주 백업하는 경우 이러한 성공 메시지는 바로 누적되므로 엄청난 오류 로그가 쌓여 다른 메시지를 찾기 힘들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-128">If you back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="1a1ed-129">이 경우 스크립트가 이러한 로그 항목에 종속되지 않을 경우 추적 플래그 3226을 사용하여 이러한 항목을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-129">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="1a1ed-130">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-130">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a1ed-131">보안</span><span class="sxs-lookup"><span data-stu-id="1a1ed-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a1ed-132">권한</span><span class="sxs-lookup"><span data-stu-id="1a1ed-132">Permissions</span></span>  
 <span data-ttu-id="1a1ed-133">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="1a1ed-134">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-134">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1a1ed-135">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-135">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="1a1ed-136">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-136">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="1a1ed-137">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-137">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1a1ed-138">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1a1ed-138">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-database-files-and-filegroups"></a><span data-ttu-id="1a1ed-139">데이터베이스 파일 및 파일 그룹을 백업하려면</span><span class="sxs-lookup"><span data-stu-id="1a1ed-139">To back up database files and filegroups</span></span>  
  
1.  <span data-ttu-id="1a1ed-140">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-140">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="1a1ed-141">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-141">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="1a1ed-142">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-142">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="1a1ed-143">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-143">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="1a1ed-144">**데이터베이스** 목록에서 데이터베이스 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-144">In the **Database** list, verify the database name.</span></span> <span data-ttu-id="1a1ed-145">필요에 따라 목록에서 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-145">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="1a1ed-146">**백업 유형** 목록에서 **전체** 또는 **차등**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-146">In the **Backup type** list, select **Full** or **Differential**.</span></span>  
  
6.  <span data-ttu-id="1a1ed-147">**백업 구성 요소** 옵션에서 **파일 및 파일 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-147">For the **Backup component** option, click **File and Filegroups**.</span></span>  
  
7.  <span data-ttu-id="1a1ed-148">**파일 및 파일 그룹 선택** 대화 상자에서 백업할 파일 및 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-148">In the **Select Files and Filegroups** dialog box, select the files and filegroups you want to back up.</span></span> <span data-ttu-id="1a1ed-149">개별 파일을 하나 이상 선택하거나 파일 그룹의 확인란을 선택하여 해당 파일 그룹의 모든 파일을 자동으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-149">You can select one or more individual files or check the box for a filegroup to automatically select all the files in that filegroup.</span></span>  
  
8.  <span data-ttu-id="1a1ed-150">**이름** 입력란에 제시된 기본 백업 세트 이름을 사용하거나 다른 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-150">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="1a1ed-151">필요에 따라 **설명** 입력란에 백업 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-151">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="1a1ed-152">백업 세트가 만료될 시기를 다음과 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-152">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="1a1ed-153">백업 세트가 특정 일 수 후에 만료되게 하려면 **다음 이후** (기본 옵션)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-153">To have the backup set expire after a specific number of days, click **After** (the default option).</span></span> <span data-ttu-id="1a1ed-154">그런 다음 세트를 만든 후 세트가 만료되는 일 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-154">Then, enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="1a1ed-155">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-155">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="1a1ed-156">기본값은 **서버 속성** 대화 상자( **데이터베이스 설정** 페이지)의**백업 미디어 기본 보존 기간(일)** 옵션에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-156">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="1a1ed-157">이 옵션에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-157">To access this option, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="1a1ed-158">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-158">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="1a1ed-159">**디스크** 나 **테이프**를 클릭하여 백업 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-159">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="1a1ed-160">**추가**를 클릭하면 단일 미디어 세트가 들어 있는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-160">To select the paths of up to 64 disk or tape drives that contain a single media set, click **Add**.</span></span> <span data-ttu-id="1a1ed-161">선택한 경로는 **백업할 위치** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-161">The selected paths are displayed in the **Backup to** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a1ed-162">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="1a1ed-163">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="1a1ed-164">고급 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-164">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="1a1ed-165">다음 중 하나를 클릭하여 **미디어 덮어쓰기** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="1a1ed-166">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="1a1ed-167">이 옵션에는 **기존 백업 세트에 추가** 또는 **기존 백업 세트 모두 덮어쓰기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="1a1ed-168">기존 미디어 세트에 백업에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-168">For information about backing up to an existing media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="1a1ed-169">필요에 따라 **미디어 세트 이름 및 백업 세트 만료 확인** 을 선택하여 백업 작업에서 미디어 세트와 백업 세트가 만료되는 날짜와 시간을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="1a1ed-170">필요에 따라 **미디어 세트 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="1a1ed-171">이름을 지정하지 않는 경우 이름이 비어 있는 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="1a1ed-172">미디어 세트 이름을 지정하는 경우 실제 이름과 입력한 이름이 일치하는지 확인하기 위해 미디어(테이프 또는 디스크)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name that you enter here.</span></span>  
  
         <span data-ttu-id="1a1ed-173">미디어 이름을 비워 두고 검사하도록 확인란을 선택한 경우 미디어에서 미디어 이름을 비워 두는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-173">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="1a1ed-174">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-174">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="1a1ed-175">이 옵션에는 **새 미디어 세트 이름** 입력란에 이름을 입력하고 필요에 따라 **새 미디어 세트 설명** 입력란에 미디어 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-175">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="1a1ed-176">새 미디어 세트 만들기에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-176">For more information about creating a new media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="1a1ed-177">**안정성** 섹션에서 필요에 따라 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-177">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="1a1ed-178">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-178">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="1a1ed-179">**미디어에 쓰기 전에 체크섬 수행**및 필요에 따라 **체크섬 오류 발생 시 계속**.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-179">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="1a1ed-180">체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-180">For more information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="1a1ed-181">**일반** 페이지의 **대상** 섹션에서 지정한 대로 테이프 드라이브에 백업하는 경우 **백업 후 테이프 언로드** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-181">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="1a1ed-182">이 옵션을 클릭하면 **언로드 전에 테이프 되감기** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-182">Clicking this option enables the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a1ed-183">**일반** 페이지의 **백업 유형** 섹션에서 지정한 대로 트랜잭션 로그를 백업하지 않으면 **트랜잭션 로그** 섹션의 옵션이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-183">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="1a1ed-184">이상 버전에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-184">and later versions support [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="1a1ed-185">기본적으로 백업은 **백업-압축 기본값** 서버 구성 옵션의 값에 따라 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-185">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="1a1ed-186">그러나 현재 서버 수준 기본값에 관계없이 **백업 압축**을 선택하여 백업을 압축하고, **백업 압축 안 함**을 선택하여 압축을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-186">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="1a1ed-187">**현재 백업 압축 기본값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="1a1ed-187">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="1a1ed-188">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="1a1ed-188">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1a1ed-189">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1a1ed-189">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-files-and-filegroups"></a><span data-ttu-id="1a1ed-190">파일과 파일 그룹을 백업하려면</span><span class="sxs-lookup"><span data-stu-id="1a1ed-190">To back up files and filegroups</span></span>  
  
1.  <span data-ttu-id="1a1ed-191">파일 또는 파일 그룹 백업을 만들려면 [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-191">To create a file or filegroup backup, use a [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) statement.</span></span> <span data-ttu-id="1a1ed-192">최소한 이 문은 다음 항목을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-192">Minimally, this statement must specify the following:</span></span>  
  
    -   <span data-ttu-id="1a1ed-193">데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-193">The database name.</span></span>  
  
    -   <span data-ttu-id="1a1ed-194">각 파일 또는 파일 그룹에 대한 각각의 FILE 또는 FILEGROUP 절</span><span class="sxs-lookup"><span data-stu-id="1a1ed-194">A FILE or FILEGROUP clause for each file or filegroup, respectively.</span></span>  
  
    -   <span data-ttu-id="1a1ed-195">전체 백업이 기록될 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="1a1ed-195">The backup device on which the full backup will be written.</span></span>  
  
     <span data-ttu-id="1a1ed-196">파일 백업의 기본 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-196">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a file backup is:</span></span>  
  
     <span data-ttu-id="1a1ed-197">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="1a1ed-197">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="1a1ed-198">{ FILE **=** _logical_file_name_ | FILEGROUP **=** _logical_filegroup_name_ } [ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="1a1ed-198">{ FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ } [ **,**...*f* ]</span></span>  
  
     <span data-ttu-id="1a1ed-199">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1a1ed-199">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="1a1ed-200">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="1a1ed-200">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="1a1ed-201">옵션</span><span class="sxs-lookup"><span data-stu-id="1a1ed-201">Option</span></span>|<span data-ttu-id="1a1ed-202">Description</span><span class="sxs-lookup"><span data-stu-id="1a1ed-202">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="1a1ed-203">*database*</span><span class="sxs-lookup"><span data-stu-id="1a1ed-203">*database*</span></span>|<span data-ttu-id="1a1ed-204">트랜잭션 로그, 일부 데이터베이스, 전체 데이터베이스가 백업되는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-204">Is the database from which the transaction log, partial database, or complete database is backed up.</span></span>|  
    |<span data-ttu-id="1a1ed-205">FILE **=** _logical_file_name_</span><span class="sxs-lookup"><span data-stu-id="1a1ed-205">FILE **=**_logical_file_name_</span></span>|<span data-ttu-id="1a1ed-206">파일 백업에 포함할 파일의 논리적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-206">Specifies the logical name of a file to include in the file backup.</span></span>|  
    |<span data-ttu-id="1a1ed-207">FILEGROUP **=** _logical_filegroup_name_</span><span class="sxs-lookup"><span data-stu-id="1a1ed-207">FILEGROUP **=**_logical_filegroup_name_</span></span>|<span data-ttu-id="1a1ed-208">파일 백업에 포함할 파일 그룹의 논리적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-208">Specifies the logical name of a filegroup to include in the file backup.</span></span> <span data-ttu-id="1a1ed-209">단순 복구 모델에서 파일 그룹 백업은 읽기 전용 파일 그룹에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-209">Under the simple recovery model, a filegroup backup is allowed only for a read-only filegroup.</span></span>|  
    |<span data-ttu-id="1a1ed-210">[ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="1a1ed-210">[ **,**...*f* ]</span></span>|<span data-ttu-id="1a1ed-211">여러 개의 파일 및 파일 그룹을 지정할 수 있음을 나타내는 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-211">Is a placeholder that indicates that multiple files and filegroups may be specified.</span></span> <span data-ttu-id="1a1ed-212">이때 파일 또는 파일 그룹의 수는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-212">The number of files or filegroups is unlimited.</span></span>|  
    |<span data-ttu-id="1a1ed-213">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1a1ed-213">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="1a1ed-214">백업 작업에 사용할 1-64개의 백업 디바이스 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-214">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="1a1ed-215">물리적 백업 디바이스를 지정하거나, 이미 정의된 경우 해당 논리적 백업 디바이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-215">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="1a1ed-216">물리적 백업 디바이스를 지정하려면 다음 DISK 또는 TAPE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-216">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="1a1ed-217">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="1a1ed-217">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="1a1ed-218">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-218">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="1a1ed-219">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="1a1ed-219">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="1a1ed-220">필요에 따라 DIFFERENTIAL과 같은 하나 이상의 추가 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-220">Optionally, specifies one or more additional options, such as DIFFERENTIAL.</span></span><br /><br /> <span data-ttu-id="1a1ed-221">참고: 차등 파일 백업에는 기반으로 전체 파일 백업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-221">Note: A differential file backup requires a full file backup as a base.</span></span> <span data-ttu-id="1a1ed-222">자세한 내용은 [차등 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-222">For more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>|  
  
2.  <span data-ttu-id="1a1ed-223">전체 복구 모델에서는 트랜잭션 로그도 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-223">Under the full recovery model, you must also back up the transaction log.</span></span> <span data-ttu-id="1a1ed-224">전체 파일 백업의 전체 세트를 사용하여 데이터베이스를 복원하려면 첫 번째 파일 백업을 시작할 때부터 모든 파일 백업을 포함할 정도의 충분한 로그 백업이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-224">To use a complete set of full file backups to restore a database, you must also have enough log backups to span all the file backups, from the start of the first file backup.</span></span> <span data-ttu-id="1a1ed-225">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-225">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1a1ed-226">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a1ed-226">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="1a1ed-227">다음 예에서는 `Sales` 데이터베이스의 보조 파일 그룹에 있는 하나 이상의 파일을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-227">The following examples back up one or more files of the secondary filegroups of the `Sales` database.</span></span> <span data-ttu-id="1a1ed-228">이 데이터베이스는 전체 복구 모델을 사용하고 다음과 같은 보조 파일 그룹을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-228">This database uses the full recovery model and contains the following secondary filegroups:</span></span>  
  
-   <span data-ttu-id="1a1ed-229">`SalesGroup1` 및 `SGrp1Fi1` 파일을 포함하는 `SGrp1Fi2`파일 그룹</span><span class="sxs-lookup"><span data-stu-id="1a1ed-229">A filegroup named `SalesGroup1` that has the files `SGrp1Fi1` and `SGrp1Fi2`.</span></span>  
  
-   <span data-ttu-id="1a1ed-230">`SalesGroup2` 및 `SGrp2Fi1` 파일을 포함하는 `SGrp2Fi2`파일 그룹</span><span class="sxs-lookup"><span data-stu-id="1a1ed-230">A filegroup named `SalesGroup2` that has the files `SGrp2Fi1` and `SGrp2Fi2`.</span></span>  
  
#### <a name="a-creating-a-file-backup-of-two-files"></a><span data-ttu-id="1a1ed-231">A.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-231">A.</span></span> <span data-ttu-id="1a1ed-232">두 파일의 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="1a1ed-232">Creating a file backup of two files</span></span>  
 <span data-ttu-id="1a1ed-233">다음 예에서는 `SGrp1Fi2` 의 `SalesGroup1` 파일과 `SGrp2Fi2` 파일 그룹의 `SalesGroup2` 파일에 대해서만 차등 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-233">The following example creates a differential file backup of only the `SGrp1Fi2` file of the `SalesGroup1` and the `SGrp2Fi2` file of the `SalesGroup2` filegroup.</span></span>  
  
```sql  
--Backup the files in the SalesGroup1 secondary filegroup.  
BACKUP DATABASE Sales  
   FILE = 'SGrp1Fi2',   
   FILE = 'SGrp2Fi2'   
   TO DISK = 'G:\SQL Server Backups\Sales\SalesGroup1.bck';  
GO  
```  
  
#### <a name="b-creating-a-full-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="1a1ed-234">B.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-234">B.</span></span> <span data-ttu-id="1a1ed-235">보조 파일 그룹의 전체 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="1a1ed-235">Creating a full file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="1a1ed-236">다음 예에서는 두 보조 파일 그룹에 있는 모든 파일의 전체 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-236">The following example creates a full file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck';  
GO  
```  
  
#### <a name="c-creating-a-differential-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="1a1ed-237">C.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-237">C.</span></span> <span data-ttu-id="1a1ed-238">보조 파일 그룹의 차등 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="1a1ed-238">Creating a differential file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="1a1ed-239">다음 예에서는 두 보조 파일 그룹에 있는 모든 파일의 차등 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-239">The following example creates a differential file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1a1ed-240">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="1a1ed-240">Using PowerShell</span></span>  
  
<span data-ttu-id="1a1ed-241">`Backup-SqlDatabase` 매개 변수의 값으로 `Files`를 지정하여 `-BackupAction` cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-241">Use the `Backup-SqlDatabase` cmdlet and specify `Files` for the value of the `-BackupAction` parameter.</span></span> <span data-ttu-id="1a1ed-242">또한 다음 매개 변수 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-242">Also, specify one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="1a1ed-243">특정 파일을 백업 하려면 `-DatabaseFile` *문자열* 매개 변수를 지정 합니다. 여기서 *string* 은 백업할 하나 이상의 데이터베이스 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-243">To back up a specific file, specify the `-DatabaseFile`*String* parameter, where *String* is one or more database files to be backed up.</span></span>  
  
    -   <span data-ttu-id="1a1ed-244">지정 된 파일 그룹의 모든 파일을 백업 하려면 `-DatabaseFileGroup` *문자열* 매개 변수를 지정 합니다. 여기서 *string* 은 백업할 하나 이상의 데이터베이스 파일 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-244">To back up all the files in a given filegroup, specify the `-DatabaseFileGroup`*String* parameter, where *String* is one or more database filegroups to be backed up.</span></span>  
  
     <span data-ttu-id="1a1ed-245">다음 예에서는 `MyDB` 데이터베이스의 보조 파일 그룹 'FileGroup1' 및 'FileGroup2'에 있는 모든 파일의 전체 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-245">The following example creates a full file backup of every file in the secondary filegroups 'FileGroup1' and 'FileGroup2' in the `MyDB` database.</span></span> <span data-ttu-id="1a1ed-246">백업은 서버 인스턴스 `Computer\Instance`의 기본 백업 위치에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-246">The backups are created on the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Files -DatabaseFileGroup "FileGroup1","FileGroup2"  
    ```  
  
<span data-ttu-id="1a1ed-247">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a1ed-247">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1a1ed-248">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a1ed-248">See Also</span></span>  
 <span data-ttu-id="1a1ed-249">[백업 개요&#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-249">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="1a1ed-250">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="1a1ed-251">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="1a1ed-252">[백업 기록 및 헤더 정보&#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-252">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 <span data-ttu-id="1a1ed-253">[데이터베이스 백업&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-253">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1a1ed-254">[데이터베이스 백업&#40;백업 옵션 페이지&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-254">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="1a1ed-255">[전체 파일 백업&#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-255">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1a1ed-256">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-256">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1a1ed-257">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="1a1ed-257">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="1a1ed-258">파일 복원&#40;단순 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="1a1ed-258">File Restores &#40;Simple Recovery Model&#41;</span></span>](file-restores-simple-recovery-model.md)  
  
  
