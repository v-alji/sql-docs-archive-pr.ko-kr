---
title: 트랜잭션 로그 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b57ca40b08718cda5095249991e0d424e6593a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650140"
---
# <a name="back-up-a-transaction-log-sql-server"></a><span data-ttu-id="b32ec-102">트랜잭션 로그 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b32ec-102">Back Up a Transaction Log (SQL Server)</span></span>
  <span data-ttu-id="b32ec-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 트랜잭션 로그를 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-103">This topic describes how to back up a transaction log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="b32ec-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b32ec-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b32ec-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b32ec-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b32ec-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b32ec-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b32ec-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b32ec-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b32ec-108">보안</span><span class="sxs-lookup"><span data-stu-id="b32ec-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b32ec-109">**트랜잭션 로그를 백업하려면**</span><span class="sxs-lookup"><span data-stu-id="b32ec-109">**To back up a transaction log, using:**</span></span>  
  
     [<span data-ttu-id="b32ec-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b32ec-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b32ec-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b32ec-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b32ec-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b32ec-112">PowerShell</span></span>](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  <span data-ttu-id="b32ec-113"> 또는[유지 관리 계획 마법사](../maintenance-plans/use-the-maintenance-plan-wizard.md)를 사용하여 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-113">Alternatively, you can use the[Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)to create backups.</span></span>  
  
-   [<span data-ttu-id="b32ec-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b32ec-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b32ec-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b32ec-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b32ec-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b32ec-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b32ec-117">명시적 또는 암시적 트랜잭션에서는 BACKUP 문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b32ec-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b32ec-118">Recommendations</span></span>  
  
-   <span data-ttu-id="b32ec-119">데이터베이스에서 전체 또는 대량 로그 복구 모델을 사용하는 경우 데이터를 보호하고 트랜잭션 로그가 채워지지 않도록 트랜잭션 로그를 정기적으로 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-119">If a database uses either the full or bulk-logged recovery model, you must back up the transaction log regularly enough to protect your data and to keep the transaction log from filling.</span></span> <span data-ttu-id="b32ec-120">그러면 로그가 잘리고 특정 시점에 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-120">This truncates the log and supports restoring the database to a specific point in time.</span></span>  
  
-   <span data-ttu-id="b32ec-121">기본적으로 백업 작업을 성공적으로 수행할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 시스템 이벤트 로그에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-121">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="b32ec-122">로그를 자주 백업하는 경우 이러한 성공 메시지는 바로 누적되므로 엄청난 오류 로그가 쌓여 다른 메시지를 찾기 힘들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-122">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="b32ec-123">이 경우 스크립트가 이러한 로그 항목에 종속되지 않을 경우 추적 플래그 3226을 사용하여 이러한 항목을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-123">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="b32ec-124">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-124">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b32ec-125">보안</span><span class="sxs-lookup"><span data-stu-id="b32ec-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b32ec-126">권한</span><span class="sxs-lookup"><span data-stu-id="b32ec-126">Permissions</span></span>  
 <span data-ttu-id="b32ec-127">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-127">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="b32ec-128">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-128">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b32ec-129">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-129">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="b32ec-130">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-130">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="b32ec-131">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-131">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b32ec-132">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b32ec-132">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="b32ec-133">트랜잭션 로그를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="b32ec-133">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="b32ec-134">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-134">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b32ec-135">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-135">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="b32ec-136">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-136">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="b32ec-137">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-137">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="b32ec-138">**데이터베이스** 목록 상자에서 데이터베이스 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-138">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="b32ec-139">필요에 따라 목록에서 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-139">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="b32ec-140">복구 모델이 **FULL** 또는 **BULK_LOGGED**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-140">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="b32ec-141">**백업 유형** 목록 상자에서 **트랜잭션 로그**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-141">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="b32ec-142">필요한 경우 **복사 전용 백업**을 선택하여 복사 전용 백업을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-142">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="b32ec-143">*복사 전용 백업*은 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 시퀀스와 독립적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-143">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="b32ec-144">자세한 내용은 [복사 전용 백업&#40;SQL Server&#41;](copy-only-backups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-144">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b32ec-145">**차등** 옵션을 선택하는 경우 복사 전용 백업을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-145">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="b32ec-146">**이름** 입력란에 제시된 기본 백업 세트 이름을 사용하거나 다른 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-146">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="b32ec-147">필요에 따라 **설명** 입력란에 백업 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-147">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="b32ec-148">백업 세트가 만료될 시기를 다음과 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-148">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="b32ec-149">백업 세트가 특정 일수가 지난 후에 만료되도록 하려면 **다음 이후** (기본 옵션)를 클릭한 다음 백업 세트를 만든 후 백업 세트가 만료되기까지 경과해야 하는 일수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-149">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="b32ec-150">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-150">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="b32ec-151">기본값은 **서버 속성** 대화 상자( **데이터베이스 설정** 페이지)의**백업 미디어 기본 보존 기간(일)** 옵션에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-151">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="b32ec-152">이 대화 상자에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-152">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="b32ec-153">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-153">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="b32ec-154">**디스크**, **URL** 또는 **테이프**를 클릭하여 백업 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-154">Choose the type of backup destination by clicking **Disk**, **URL** or **Tape**.</span></span> <span data-ttu-id="b32ec-155">**추가**를 클릭하면 단일 미디어 세트를 포함하는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-155">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="b32ec-156">선택한 경로는 **백업 대상** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-156">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="b32ec-157">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-157">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="b32ec-158">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-158">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="b32ec-159">고급 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-159">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="b32ec-160">다음 중 하나를 클릭하여 **미디어 덮어쓰기** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-160">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="b32ec-161">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="b32ec-161">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="b32ec-162">이 옵션에는 **기존 백업 세트에 추가** 또는 **기존 백업 세트 모두 덮어쓰기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-162">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="b32ec-163">자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-163">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="b32ec-164">필요에 따라 **미디어 세트 이름 및 백업 세트 만료 확인** 을 선택하여 백업 작업에서 미디어 세트와 백업 세트가 만료되는 날짜와 시간을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-164">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="b32ec-165">필요에 따라 **미디어 세트 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-165">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="b32ec-166">이름을 지정하지 않는 경우 이름이 비어 있는 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-166">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="b32ec-167">미디어 세트 이름을 지정하는 경우 미디어(테이프 또는 디스크)를 선택하여 실제 이름과 여기에서 입력한 이름이 일치하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-167">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="b32ec-168">미디어 이름을 비워 두고 검사하도록 확인란을 선택한 경우 미디어에서 미디어 이름을 비워 두는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-168">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="b32ec-169">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="b32ec-169">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="b32ec-170">이 옵션에는 **새 미디어 세트 이름** 입력란에 이름을 입력하고 필요에 따라 **새 미디어 세트 설명** 입력란에 미디어 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-170">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="b32ec-171">자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-171">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="b32ec-172">**안정성** 섹션에서 필요에 따라 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-172">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="b32ec-173">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="b32ec-173">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="b32ec-174">**미디어에 쓰기 전에 체크섬 수행**및 필요에 따라 **체크섬 오류 발생 시 계속**.</span><span class="sxs-lookup"><span data-stu-id="b32ec-174">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="b32ec-175">체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-175">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="b32ec-176">**트랜잭션 로그** 섹션에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-176">In the **Transaction log** section:</span></span>  
  
    -   <span data-ttu-id="b32ec-177">일상적인 로그 백업의 경우 기본 선택인 **비활성 항목을 제거하여 트랜잭션 로그 잘라내기**를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-177">For routine log backups, keep the default selection, **Truncate the transaction log by removing inactive entries**.</span></span>  
  
    -   <span data-ttu-id="b32ec-178">비상 로그, 즉 활성 로그를 백업하려면 **비상 로그 백업을 수행하고 복원 중인 상태로 데이터베이스 유지**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-178">To back up the tail of the log (that is, the active log), check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
         <span data-ttu-id="b32ec-179">비상 로그 백업은 작업 손실을 방지하기 위해 비상 로그 백업에 실패한 후에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-179">A tail-log backup is taken after a failure to back up the tail of the log in order to prevent work loss.</span></span> <span data-ttu-id="b32ec-180">실패 후, 데이터베이스 복원 시작 전 또는 보조 데이터베이스로 장애 조치(Failover)할 때 활성 로그를 백업합니다(비상 로그 백업).</span><span class="sxs-lookup"><span data-stu-id="b32ec-180">Back up the active log (a tail-log backup) both after a failure, before beginning to restore the database, or when failing over to a secondary database.</span></span> <span data-ttu-id="b32ec-181">이 옵션을 선택하는 것은 Transact-SQL의 BACKUP LOG 문에서 NORECOVERY 옵션을 지정하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-181">Selecting this option is equivalent to specifying the NORECOVERY option in the BACKUP LOG statement of Transact-SQL.</span></span> <span data-ttu-id="b32ec-182">비상 로그 백업에 대한 자세한 내용은 [비상 로그 백업&#40;SQL Server&#41;](tail-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-182">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
16. <span data-ttu-id="b32ec-183">**일반** 페이지의 **대상** 섹션에서 지정한 대로 테이프 드라이브에 백업하는 경우 **백업 후 테이프 언로드** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-183">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="b32ec-184">이 옵션을 클릭하면 **언로드 전에 테이프 되감기** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-184">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="b32ec-185">이상에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-185">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="b32ec-186">기본적으로 백업은 **백업-압축 기본값** 서버 구성 옵션의 값에 따라 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-186">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="b32ec-187">그러나 현재 서버 수준 기본값에 관계없이 **백업 압축**을 선택하여 백업을 압축하고, **백업 압축 안 함**을 선택하여 압축을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-187">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="b32ec-188">**현재 백업 압축 기본값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="b32ec-188">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="b32ec-189">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="b32ec-189">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 <span data-ttu-id="b32ec-190">**암호화**</span><span class="sxs-lookup"><span data-stu-id="b32ec-190">**Encryption**</span></span>  
  
 <span data-ttu-id="b32ec-191">백업 파일을 암호화하려면 **백업 암호화** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-191">To encrypt the backup file check the **Encrypt backup** check box.</span></span> <span data-ttu-id="b32ec-192">백업 파일을 암호화하는 데 사용할 암호화 알고리즘을 선택하고 인증서 또는 비대칭 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-192">Select an encryption algorithm to use for encrypting the backup file and provide a Certificate or Asymmetric key.</span></span> <span data-ttu-id="b32ec-193">사용 가능한 암호화 알고리즘은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-193">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="b32ec-194">AES 128</span><span class="sxs-lookup"><span data-stu-id="b32ec-194">AES 128</span></span>  
  
-   <span data-ttu-id="b32ec-195">AES 192</span><span class="sxs-lookup"><span data-stu-id="b32ec-195">AES 192</span></span>  
  
-   <span data-ttu-id="b32ec-196">AES 256</span><span class="sxs-lookup"><span data-stu-id="b32ec-196">AES 256</span></span>  
  
-   <span data-ttu-id="b32ec-197">Triple DES</span><span class="sxs-lookup"><span data-stu-id="b32ec-197">Triple DES</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b32ec-198">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b32ec-198">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="b32ec-199">트랜잭션 로그를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="b32ec-199">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="b32ec-200">BACKUP LOG 문을 실행하여 트랜잭션 로그를 백업하며 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-200">Execute the BACKUP LOG statement to back up the transaction log, specifying the following:</span></span>  
  
    -   <span data-ttu-id="b32ec-201">백업할 트랜잭션 로그가 속한 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="b32ec-201">The name of the database to which the transaction log that you want to back up belongs.</span></span>  
  
    -   <span data-ttu-id="b32ec-202">트랜잭션 로그 백업이 기록될 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="b32ec-202">The backup device where the transaction log backup is written.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="b32ec-203">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b32ec-203">Example (Transact-SQL)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b32ec-204">이 예에서는 단순 복구 모델을 사용하는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-204">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, which uses the simple recovery model.</span></span> <span data-ttu-id="b32ec-205">로그 백업을 허용하기 위해 전체 데이터베이스를 백업하기 전에 전체 복구 모델을 사용하도록 데이터베이스를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-205">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="b32ec-206">자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-206">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="b32ec-207">이 예에서는 이전에 만든 명명된 백업 디바이스 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 에 `MyAdvWorks_FullRM_log1`데이터베이스의 트랜잭션 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-207">This example creates a transaction log backup for the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to the previously created named backup device, `MyAdvWorks_FullRM_log1`.</span></span>  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b32ec-208">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="b32ec-208">Using PowerShell</span></span>  
  
<span data-ttu-id="b32ec-209">`Backup-SqlDatabase` 매개 변수의 값으로 `Log`를 지정하여 `-BackupAction` cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-209">Use the `Backup-SqlDatabase` cmdlet and specify `Log` for the value of the `-BackupAction` parameter.</span></span>  
  
<span data-ttu-id="b32ec-210">다음 예에서는 서버 인스턴스 `MyDB` 의 기본 백업 위치에 `Computer\Instance`데이터베이스의 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32ec-210">The following example creates a log backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
<span data-ttu-id="b32ec-211">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b32ec-211">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b32ec-212">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b32ec-212">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b32ec-213">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b32ec-213">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="b32ec-214">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="b32ec-214">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="b32ec-215">꽉 찬 트랜잭션 로그 문제 해결&#40;SQL Server 오류 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="b32ec-215">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a><span data-ttu-id="b32ec-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b32ec-216">See Also</span></span>  
 <span data-ttu-id="b32ec-217">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b32ec-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="b32ec-218">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b32ec-218">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b32ec-219">[유지 관리 계획](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="b32ec-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="b32ec-220">전체 파일 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b32ec-220">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
