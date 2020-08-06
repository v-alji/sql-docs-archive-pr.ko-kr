---
title: 데이터베이스가 손상된 경우 트랜잭션 로그 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], damaged
- backing up [SQL Server]. damaged database
- transaction log backups [SQL Server], damaged databases
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea712e6bc4e73119a4f07a7775f9f25e212f8534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638862"
---
# <a name="back-up-the-transaction-log-when-the-database-is-damaged-sql-server"></a><span data-ttu-id="9d490-102">데이터베이스가 손상된 경우 트랜잭션 로그 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9d490-102">Back Up the Transaction Log When the Database Is Damaged (SQL Server)</span></span>
  <span data-ttu-id="9d490-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스가 손상되었을 때 트랜잭션 로그를 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-103">This topic describes how to back up a transaction log when the database is damaged in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9d490-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9d490-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9d490-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9d490-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9d490-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9d490-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9d490-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9d490-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9d490-108">보안</span><span class="sxs-lookup"><span data-stu-id="9d490-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9d490-109">**다음을 사용하여 데이터베이스가 손상되었을 때 트랜잭션 로그를 백업합니다.**</span><span class="sxs-lookup"><span data-stu-id="9d490-109">**To back up the transaction log when the database is damaged, using:**</span></span>  
  
     [<span data-ttu-id="9d490-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9d490-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9d490-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9d490-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9d490-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9d490-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9d490-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9d490-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9d490-114">명시적 또는 암시적 트랜잭션에서는 BACKUP 문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-114">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9d490-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9d490-115">Recommendations</span></span>  
  
-   <span data-ttu-id="9d490-116">전체 또는 대량 로그 복구 모델을 사용하는 데이터베이스의 경우 대개 데이터베이스를 복원하기 전에 비상 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-116">For a database that uses either the full or bulk-logged recovery model, you generally need to back up the tail of the log before beginning to restore the database.</span></span> <span data-ttu-id="9d490-117">또한 로그 전달 구성의 장애 조치를 수행하기 전에 주 데이터베이스의 비상 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-117">You also should back up the tail of the log of the primary database before failing over a log shipping configuration.</span></span> <span data-ttu-id="9d490-118">데이터베이스를 복구하기 전에 비상 로그 백업을 최종 로그 백업으로 복원하면 오류 후 작업 손실이 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-118">Restoring the tail-log backup as the final log backup before recovering the database avoids work loss after a failure.</span></span> <span data-ttu-id="9d490-119">비상 로그 백업에 대한 자세한 내용은 [비상 로그 백업&#40;SQL Server&#41;](tail-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d490-119">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9d490-120">보안</span><span class="sxs-lookup"><span data-stu-id="9d490-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9d490-121">권한</span><span class="sxs-lookup"><span data-stu-id="9d490-121">Permissions</span></span>  
 <span data-ttu-id="9d490-122">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-122">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="9d490-123">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-123">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9d490-124">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-124">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="9d490-125">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-125">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="9d490-126">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-126">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9d490-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9d490-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-the-tail-of-the-transaction-log"></a><span data-ttu-id="9d490-128">트랜잭션 비상 로그를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="9d490-128">To back up the tail of the transaction log</span></span>  
  
1.  <span data-ttu-id="9d490-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-129">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9d490-130">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-130">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="9d490-131">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-131">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="9d490-132">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-132">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="9d490-133">**데이터베이스** 목록 상자에서 데이터베이스 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-133">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="9d490-134">필요에 따라 목록에서 다른 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-134">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="9d490-135">복구 모델이 **FULL** 또는 **BULK_LOGGED**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-135">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="9d490-136">**백업 유형** 목록 상자에서 **트랜잭션 로그**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-136">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="9d490-137">**복사 전용 백업** 을 선택하지 않은 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-137">Leave **Copy Only Backup** deselected.</span></span>  
  
8.  <span data-ttu-id="9d490-138">**백업 세트** 영역에서 **이름** 입력란에 제시된 기본 백업 세트 이름을 사용하거나 다른 백업 세트 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-138">In the **Backup set** area, either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="9d490-139">**설명** 입력란에 비상 로그 백업에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-139">In the **Description** text box, enter a description for the tail-log backup.</span></span>  
  
10. <span data-ttu-id="9d490-140">백업 세트가 만료될 시기를 다음과 같이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-140">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="9d490-141">백업 세트가 특정 일수가 지난 후에 만료되도록 하려면 **다음 이후** (기본 옵션)를 클릭한 다음 백업 세트를 만든 후 백업 세트가 만료되기까지 경과해야 하는 일수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-141">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="9d490-142">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-142">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="9d490-143">기본값은 **서버 속성** 대화 상자( **데이터베이스 설정** 페이지)의**백업 미디어 기본 보존 기간(일)** 옵션에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-143">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="9d490-144">이 대화 상자에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-144">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="9d490-145">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-145">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="9d490-146">**디스크** 나 **테이프**를 클릭하여 백업 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-146">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="9d490-147">**추가**를 클릭하면 단일 미디어 세트를 포함하는 디스크나 테이프 드라이브에 대한 경로를 64개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-147">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="9d490-148">선택한 경로는 **백업 대상** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-148">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="9d490-149">백업 대상을 제거하려면 해당 대상을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-149">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="9d490-150">백업 대상의 내용을 보려면 선택한 다음 **내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-150">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="9d490-151">**옵션** 페이지에서 다음 중 하나를 클릭하여 **미디어 덮어쓰기** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-151">On the **Options** page, select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="9d490-152">**기존 미디어 세트에 백업**</span><span class="sxs-lookup"><span data-stu-id="9d490-152">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="9d490-153">이 옵션에는 **기존 백업 세트에 추가** 또는 **기존 백업 세트 모두 덮어쓰기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-153">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span>  
  
         <span data-ttu-id="9d490-154">필요에 따라 **미디어 세트 이름 및 백업 세트 만료 확인** 을 선택하여 백업 작업에서 미디어 세트와 백업 세트가 만료되는 날짜와 시간을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-154">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="9d490-155">필요에 따라 **미디어 세트 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-155">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="9d490-156">이름을 지정하지 않는 경우 이름이 비어 있는 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-156">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="9d490-157">미디어 세트 이름을 지정하는 경우 미디어(테이프 또는 디스크)를 선택하여 실제 이름과 여기에서 입력한 이름이 일치하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-157">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="9d490-158">미디어 이름을 비워 두고 검사하도록 확인란을 선택한 경우 미디어에서 미디어 이름을 비워 두는 것과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-158">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="9d490-159">**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="9d490-159">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="9d490-160">이 옵션에는 **새 미디어 세트 이름** 입력란에 이름을 입력하고 필요에 따라 **새 미디어 세트 설명** 입력란에 미디어 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-160">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
     <span data-ttu-id="9d490-161">미디어 세트 옵션에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d490-161">For more information about media set options, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
13. <span data-ttu-id="9d490-162">**안정성** 섹션에서 필요에 따라 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-162">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="9d490-163">**완료 시 백업 확인**</span><span class="sxs-lookup"><span data-stu-id="9d490-163">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="9d490-164">**미디어에 쓰기 전에 체크섬 수행**</span><span class="sxs-lookup"><span data-stu-id="9d490-164">**Perform checksum before writing to media**.</span></span>  
  
    -   <span data-ttu-id="9d490-165">**체크섬 오류 발생 시 계속**</span><span class="sxs-lookup"><span data-stu-id="9d490-165">**Continue on checksum error**</span></span>  
  
     <span data-ttu-id="9d490-166">체크섬에 대한 자세한 내용은 [백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d490-166">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="9d490-167">**트랜잭션 로그** 섹션에서 **비상 로그 백업을 수행하고 복원 중인 상태로 데이터베이스 유지**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-167">In the **Transaction log** section, check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
     <span data-ttu-id="9d490-168">이는 다음 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-168">This is equivalent to specifying the following [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9d490-169">복원 시 데이터베이스 복원 대화 상자에 비상 로그 백업의 유형이 **트랜잭션 로그(복사 전용)** 로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-169">At restore time, the Restore Database dialog box displays the type of a tail-log backup as **Transaction Log (Copy Only)**.</span></span>  
  
15. <span data-ttu-id="9d490-170">**일반** 페이지의 **대상** 섹션에서 지정한 대로 테이프 드라이브에 백업하는 경우 **백업 후 테이프 언로드** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="9d490-171">이 옵션을 클릭하면 **언로드 전에 테이프 되감기** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="9d490-172">이상에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-172">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="9d490-173">기본적으로 백업은 **백업-압축 기본값** 서버 구성 옵션의 값에 따라 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-173">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="9d490-174">그러나 현재 서버 수준 기본값에 관계없이 **백업 압축**을 선택하여 백업을 압축하고, **백업 압축 안 함**을 선택하여 압축을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-174">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="9d490-175">**현재 백업 압축 기본값을 보려면**</span><span class="sxs-lookup"><span data-stu-id="9d490-175">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="9d490-176">backup compression default 서버 구성 옵션 보기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="9d490-176">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9d490-177">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9d490-177">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-backup-of-the-currently-active-transaction-log"></a><span data-ttu-id="9d490-178">현재 활성화된 트랜잭션 로그의 백업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="9d490-178">To create a backup of the currently active transaction log</span></span>  
  
1.  <span data-ttu-id="9d490-179">BACKUP LOG 문을 실행하여 현재 활성화되어 있는 트랜잭션 로그를 백업합니다. 이 때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-179">Execute the BACKUP LOG statement to back up the currently active transaction log, specifying:</span></span>  
  
    -   <span data-ttu-id="9d490-180">백업할 트랜잭션 로그가 속한 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="9d490-180">The name of the database to which the transaction log to back up belongs.</span></span>  
  
    -   <span data-ttu-id="9d490-181">트랜잭션 로그 백업이 기록될 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="9d490-181">The backup device where the transaction log backup will be written.</span></span>  
  
    -   <span data-ttu-id="9d490-182">NO_TRUNCATE 절</span><span class="sxs-lookup"><span data-stu-id="9d490-182">The NO_TRUNCATE clause.</span></span>  
  
         <span data-ttu-id="9d490-183">트랜잭션 로그 파일이 액세스 가능하며 손상되지 않은 경우 이 절을 사용하면 데이터베이스에 액세스할 수 없는 경우에도 트랜잭션 로그의 활성 부분을 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-183">This clause allows the active part of the transaction log to be backed up even if the database is inaccessible, provided that the transaction log file is accessible and undamaged.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="9d490-184">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9d490-184">Example (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d490-185">이 예에서는 단순 복구 모델을 사용하는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-185">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], which uses the simple recovery model.</span></span> <span data-ttu-id="9d490-186">로그 백업을 허용하기 위해 전체 데이터베이스를 백업하기 전에 전체 복구 모델을 사용하도록 데이터베이스를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-186">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="9d490-187">자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d490-187">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="9d490-188">이 예에서는 데이터베이스가 손상되어 액세스할 수 없고 트랜잭션 로그가 손상되지 않았고 액세스할 수 있는 경우 현재 활성 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="9d490-188">This example backs up the currently active transaction log when a database is damaged and inaccessible, if the transaction log is undamaged and accessible.</span></span>  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d490-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d490-189">See Also</span></span>  
 <span data-ttu-id="9d490-190">[트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-190">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="9d490-191">[SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-191">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="9d490-192">[데이터베이스 백업&#40;백업 옵션 페이지&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-192">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="9d490-193">[데이터베이스 백업&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-193">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="9d490-194">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-194">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="9d490-195">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9d490-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="9d490-196">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9d490-196">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="9d490-197">파일 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="9d490-197">File Restores &#40;Full Recovery Model&#41;</span></span>](file-restores-full-recovery-model.md)  
  
  
