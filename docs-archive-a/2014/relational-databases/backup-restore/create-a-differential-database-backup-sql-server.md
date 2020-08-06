---
title: 차등 데이터베이스 백업 만들기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- database backups [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
- backups [SQL Server], creating
ms.assetid: 70f49794-b217-4519-9f2a-76ed61fa9f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c3fb53d90ce633498bc518282d1ff03ce0b926e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661177"
---
# <a name="create-a-differential-database-backup-sql-server"></a><span data-ttu-id="27988-102">차등 데이터베이스 백업 만들기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="27988-102">Create a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="27988-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 차등 데이터베이스 백업을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-103">This topic describes how to create a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="27988-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="27988-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="27988-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="27988-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="27988-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="27988-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="27988-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="27988-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="27988-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="27988-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="27988-109">보안</span><span class="sxs-lookup"><span data-stu-id="27988-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="27988-110">**다음을 사용하여 차등 데이터베이스 백업을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="27988-110">**To create a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="27988-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="27988-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="27988-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="27988-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="27988-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="27988-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="27988-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="27988-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="27988-115">명시적 또는 암시적 트랜잭션에서는 BACKUP 문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-115">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="27988-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="27988-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="27988-117">차등 데이터베이스 백업을 만들려면 이전 전체 데이터베이스 백업이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-117">Creating a differential database backup requires that a previous full database backup exist.</span></span> <span data-ttu-id="27988-118">선택한 데이터베이스를 백업한 적이 없으면 차등 백업을 만들기 전에 전체 데이터베이스 백업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-118">If the selected database has never been backed up, run a full database backup before creating any differential backups.</span></span> <span data-ttu-id="27988-119">자세한 내용은 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)에서 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27988-119">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="27988-120">권장 사항</span><span class="sxs-lookup"><span data-stu-id="27988-120">Recommendations</span></span>  
  
-   <span data-ttu-id="27988-121">차등 백업의 크기가 커질수록 차등 백업을 복원할 때 데이터베이스 복원 시간이 훨씬 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-121">As the differential backups increase in size, restoring a differential backup can significantly increase the time that is required to restore a database.</span></span> <span data-ttu-id="27988-122">따라서 새 전체 백업을 지정된 간격으로 수행하여 데이터의 새 차등 기반을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-122">Therefore, we recommend that you take a new full backup at set intervals to establish a new differential base for the data.</span></span> <span data-ttu-id="27988-123">예를 들어 전체 데이터베이스의 전체 백업(즉, 전체 데이터베이스 백업)을 매주 수행하고 주중에 일련의 정기적인 차등 데이터베이스 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-123">For example, you might take a weekly full backup of the whole database (that is, a full database backup) followed by a regular series of differential database backups during the week.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="27988-124">보안</span><span class="sxs-lookup"><span data-stu-id="27988-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="27988-125">권한</span><span class="sxs-lookup"><span data-stu-id="27988-125">Permissions</span></span>  
 <span data-ttu-id="27988-126">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-126">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="27988-127">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-127">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="27988-128">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-128">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="27988-129">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-129">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="27988-130">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-130">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="27988-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="27988-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="27988-132">차등 데이터베이스 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="27988-132">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="27988-133">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-133">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="27988-134">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-134">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="27988-135">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-135">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="27988-136">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="27988-136">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="27988-137">**데이터베이스** 목록 상자에서 데이터베이스 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-137">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="27988-138">필요에 따라 목록에서 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-138">You can optionally select a different database from the list.</span></span>  
  
     <span data-ttu-id="27988-139">모든 복구 모델(전체, 대량 로그, 단순)에 대해 차등 백업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-139">You can perform a differential backup for any recovery model (full, bulk-logged, or simple).</span></span>  
  
5.  <span data-ttu-id="27988-140">**백업 유형** 목록 상자에서 **차등**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-140">In the **Backup type** list box, select **Differential**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="27988-141">**차등**을 선택하는 경우 **복사 전용 백업** 확인란을 선택하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-141">When **Differential** is selected, verify that the **Copy Only Backup** check box is cleared.</span></span>  
  
6.  <span data-ttu-id="27988-142">**백업 구성 요소**의 경우 **데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-142">For **Backup component**, click **Database**.</span></span>  
  
7.  <span data-ttu-id="27988-143">**이름** 입력란에 제시된 기본 백업 세트 이름을 사용하거나 다른 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-143">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
8.  <span data-ttu-id="27988-144">필요에 따라 **설명** 입력란에 백업 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-144">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
9. <span data-ttu-id="27988-145">백업 세트가 만료될 시기를 다음과 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-145">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="27988-146">백업 세트가 특정 일수가 지난 후에 만료되도록 하려면 **다음 이후** (기본 옵션)를 클릭한 다음 백업 세트를 만든 후 백업 세트가 만료되기까지 경과해야 하는 일수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-146">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="27988-147">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-147">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="27988-148">기본값은 **서버 속성** 대화 상자( **데이터베이스 설정** 페이지)의**백업 미디어 기본 보존 기간(일)** 옵션에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-148">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="27988-149">이 페이지에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-149">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="27988-150">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-150">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
10. <span data-ttu-id="27988-151">**디스크** 나 **테이프**를 클릭하여 백업 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-151">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="27988-152">**추가**를 클릭하면 단일 미디어 세트를 포함하는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-152">To select the path of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="27988-153">선택한 경로는 **백업 대상** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-153">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="27988-154">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-154">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="27988-155">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-155">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
11. <span data-ttu-id="27988-156">고급 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-156">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
12. <span data-ttu-id="27988-157">다음 중 하나를 클릭하여 **미디어 덮어쓰기** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-157">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="27988-158">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="27988-158">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="27988-159">이 옵션에는 **기존 백업 세트에 추가** 또는 **기존 백업 세트 모두 덮어쓰기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-159">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="27988-160">필요에 따라 **미디어 세트 이름 및 백업 세트 만료 확인** 확인란을 선택하거나 **미디어 세트 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-160">Optionally, check the **Check media set name and backup set expiration** check box and, optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="27988-161">이름을 지정하지 않는 경우 이름이 비어 있는 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-161">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="27988-162">미디어 세트 이름을 지정하는 경우 실제 이름과 입력한 이름이 일치하는지 확인하도록 미디어(테이프 또는 디스크)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-162">If you specify a media set name, the media (tape or disk) is checked to see if the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="27988-163">미디어 이름을 비워 두고 검사하도록 확인란을 선택한 경우 미디어에서 미디어 이름을 비워 두는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="27988-163">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="27988-164">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="27988-164">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="27988-165">이 옵션에는 **새 미디어 세트 이름** 입력란에 이름을 입력하고 필요에 따라 **새 미디어 세트 설명** 입력란에 미디어 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-165">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
13. <span data-ttu-id="27988-166">**안정성** 섹션에서 필요에 따라 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-166">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="27988-167">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="27988-167">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="27988-168">**미디어에 쓰기 전에 체크섬 수행**및 필요에 따라 **체크섬 오류 발생 시 계속**.</span><span class="sxs-lookup"><span data-stu-id="27988-168">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="27988-169">체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27988-169">For information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="27988-170">**일반** 페이지의 **대상** 섹션에서 지정한 대로 테이프 드라이브에 백업하는 경우 **백업 후 테이프 언로드** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="27988-171">이 옵션을 클릭하면 **언로드 전에 테이프 되감기** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27988-172">**일반** 페이지의 **백업 유형** 섹션에서 지정한 대로 트랜잭션 로그를 백업하지 않으면 **트랜잭션 로그** 섹션의 옵션이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-172">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
15. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="27988-173">이상에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-173">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="27988-174">기본적으로 백업은 **백업-압축 기본값** 서버 구성 옵션의 값에 따라 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="27988-174">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="27988-175">그러나 현재 서버 수준 기본값에 관계없이 **백업 압축**을 선택하여 백업을 압축하고, **백업 압축 안 함**을 선택하여 압축을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-175">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="27988-176">**현재 백업 압축 기본값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="27988-176">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="27988-177">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="27988-177">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
    > [!NOTE]  
    >  <span data-ttu-id="27988-178">또는 유지 관리 계획 마법사를 사용하여 차등 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-178">Alternatively, you can use the Maintenance Plan Wizard to create differential database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="27988-179">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="27988-179">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="27988-180">차등 데이터베이스 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="27988-180">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="27988-181">BACKUP DATABASE 문을 실행하여 차등 데이터베이스 백업을 만듭니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27988-181">Execute the BACKUP DATABASE statement to create the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="27988-182">백업할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="27988-182">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="27988-183">전체 데이터베이스 백업이 기록되는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="27988-183">The backup device where the full database backup is written.</span></span>  
  
    -   <span data-ttu-id="27988-184">마지막 전체 데이터베이스 백업이 생성된 후 변경된 데이터베이스 부분만 백업하도록 지정하는 DIFFERENTIAL 절</span><span class="sxs-lookup"><span data-stu-id="27988-184">The DIFFERENTIAL clause, to specify that only the parts of the database that have changed after the last full database backup was created are backed up.</span></span>  
  
     <span data-ttu-id="27988-185">필요한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27988-185">The required syntax is:</span></span>  
  
     <span data-ttu-id="27988-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="27988-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="27988-187">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27988-187">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="27988-188">이 예에서는 `MyAdvWorks` 데이터베이스에 대한 전체 및 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="27988-188">This example creates a full and a differential database backup for the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Create a full database backup first.  
BACKUP DATABASE MyAdvWorks   
   TO MyAdvWorks_1   
   WITH INIT;  
GO  
-- Time elapses.  
-- Create a differential database backup, appending the backup  
-- to the backup device containing the full database backup.  
BACKUP DATABASE MyAdvWorks  
   TO MyAdvWorks_1  
   WITH DIFFERENTIAL;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="27988-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27988-189">See Also</span></span>  
 <span data-ttu-id="27988-190">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27988-190">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="27988-191">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27988-191">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="27988-192">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27988-192">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="27988-193">[차등 데이터베이스 백업 복원&#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27988-193">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="27988-194">[트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27988-194">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="27988-195">[유지 관리 계획](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="27988-195">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="27988-196">전체 파일 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="27988-196">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
  
  
