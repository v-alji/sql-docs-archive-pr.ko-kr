---
title: 차등 데이터베이스 백업 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- restoring databases [SQL Server], full differential backups
- database backups [SQL Server], full differential backups
- database restores [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
ms.assetid: 0dd971a4-ee38-4dd3-9f30-ef77fc58dd11
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8eab18d84efc1a990715e0d5488085252f93a7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653461"
---
# <a name="restore-a-differential-database-backup-sql-server"></a><span data-ttu-id="87a05-102">차등 데이터베이스 백업 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="87a05-102">Restore a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="87a05-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 차등 데이터베이스 백업을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-103">This topic describes how to restore a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="87a05-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="87a05-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87a05-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="87a05-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87a05-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="87a05-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="87a05-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="87a05-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="87a05-108">보안</span><span class="sxs-lookup"><span data-stu-id="87a05-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87a05-109">**차등 데이터베이스 백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="87a05-109">**To restore a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="87a05-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87a05-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87a05-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87a05-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="87a05-112">관련 작업</span><span class="sxs-lookup"><span data-stu-id="87a05-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87a05-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="87a05-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="87a05-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="87a05-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="87a05-115">RESTORE는 명시적 또는 암시적 트랜잭션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-115">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="87a05-116">최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 만든 백업은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-116">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="87a05-117">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 사용하여 만든 데이터베이스 백업에서 사용자 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-117">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can restore a user database from a database backup that was created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="87a05-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="87a05-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="87a05-119">전체 복구 모델 또는 대량 로그 복구 모델의 경우 데이터베이스를 복원하려면 먼저 활성 트랜잭션 로그(비상 로그라고도 함)를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="87a05-120">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87a05-121">보안</span><span class="sxs-lookup"><span data-stu-id="87a05-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87a05-122">권한</span><span class="sxs-lookup"><span data-stu-id="87a05-122">Permissions</span></span>  
 <span data-ttu-id="87a05-123">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="87a05-124">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="87a05-125">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="87a05-126">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87a05-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="87a05-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="87a05-128">차등 데이터베이스 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="87a05-128">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="87a05-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음, 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-129">After you connect to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="87a05-130">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-130">Expand **Databases**.</span></span> <span data-ttu-id="87a05-131">데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스**를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-131">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="87a05-132">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 가리키고 **데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-132">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="87a05-133">**일반** 페이지에서 **원본** 섹션을 사용하여 복원할 백업 집합의 원본과 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-133">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="87a05-134">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-134">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="87a05-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="87a05-135">**Database**</span></span>  
  
         <span data-ttu-id="87a05-136">복원할 데이터베이스를 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-136">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="87a05-137">목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-137">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87a05-138">백업을 다른 서버에서 가져온 경우 대상 서버에 지정한 데이터베이스에 대한 백업 기록 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-138">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="87a05-139">이 경우 **디바이스** 를 선택하여 복원할 파일이나 디바이스를 수동으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-139">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="87a05-140">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="87a05-140">**Device**</span></span>  
  
         <span data-ttu-id="87a05-141">찾아보기( **...** ) 단추를 클릭하여 **백업 디바이스 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-141">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="87a05-142">**백업 미디어 유형** 상자에서 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-142">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="87a05-143">**백업 미디어** 상자에 대해 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-143">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="87a05-144">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-144">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="87a05-145">**원본: 디바이스: 데이터베이스** 목록 상자에서 복원할 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-145">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="87a05-146">**참고** 이 목록은 **디바이스** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-146">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="87a05-147">선택한 디바이스에 백업이 있는 데이터베이스만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-147">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="87a05-148">**대상** 섹션의 **데이터베이스** 상자에는 복원할 데이터베이스의 이름이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-148">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="87a05-149">데이터베이스의 이름을 변경하려면 **데이터베이스** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-149">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87a05-150">특정 시점에 복원을 중지하려면 **시간대** 를 클릭하여 **백업 시간대** 대화 상자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-150">To stop the restore at a specific point in time, click **Timeline** to access the **Backup Timeline** dialog box.</span></span> <span data-ttu-id="87a05-151">특정 시점의 데이터베이스 복원 중지에 대한 도움말은 [SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-151">For help with stopping a database restore at a specific point in time, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
6.  <span data-ttu-id="87a05-152">**복원에 사용할 백업 세트** 표에서 차등 백업을 통해 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-152">In the **Backup sets to restore** grid, select the backups through the differential backup that you wish to restore.</span></span>  
  
     <span data-ttu-id="87a05-153">**복원에 사용할 백업 세트** 표의 열에 대한 자세한 내용은 [데이터베이스 복원&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="87a05-154">상황에 따라 **옵션** 페이지의 **복원 옵션** 패널에서 다음 옵션 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-154">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="87a05-155">**기존 데이터베이스 덮어쓰기(WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="87a05-155">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="87a05-156">**복제 설정 유지(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="87a05-156">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="87a05-157">**각 백업 복원 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="87a05-157">**Prompt before restoring each backup**</span></span>  
  
    -   <span data-ttu-id="87a05-158">**복원된 데이터베이스에 대한 액세스 제한(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="87a05-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="87a05-159">이러한 옵션에 대한 자세한 내용은 [데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
8.  <span data-ttu-id="87a05-160">**복구 상태** 상자에 대한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="87a05-161">이 상자에서 복원 작업 후 데이터베이스의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="87a05-162">**RESTORE WITH RECOVERY** 는 커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용 준비가 된 상태로 유지하는 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="87a05-163">추가 트랜잭션 로그를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="87a05-164">필요한 모든 백업을 지금 복원하는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="87a05-165">**RESTORE WITH NORECOVERY** 는 데이터베이스를 비작동 상태로 유지하고 커밋되지 않은 트랜잭션을 롤백하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="87a05-166">추가 트랜잭션 로그를 복원할 수</span><span class="sxs-lookup"><span data-stu-id="87a05-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="87a05-167">데이터베이스는 복구할 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="87a05-168">**RESTORE WITH STANDBY** 는 읽기 전용 모드로 데이터베이스를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="87a05-169">이 옵션은 커밋되지 않은 트랜잭션의 실행을 취소하지만, 복구 결과를 되돌릴 수 있도록 실행 취소 동작을 대기 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="87a05-170">옵션에 대한 설명은 [데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
9. <span data-ttu-id="87a05-171">데이터베이스에 대한 활성 연결이 있으면 복원 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-171">Restore operations will fail if there are active connections to the database.</span></span> <span data-ttu-id="87a05-172">**기존 연결 닫기** 옵션을 선택하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 와 데이터베이스 간의 모든 활성 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-172">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span>  
  
10. <span data-ttu-id="87a05-173">각 복원 작업 사이에 확인 메시지를 표시하려면 **각 백업 복원 전에 확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-173">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="87a05-174">데이터베이스가 크고 복원 작업의 상태를 모니터링하려는 경우가 아니면 이 옵션은 일반적으로 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-174">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
11. <span data-ttu-id="87a05-175">필요에 따라 **파일** 페이지를 사용하여 데이터베이스를 새 위치로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-175">Optionally, use the **Files** page to restore the database to a new location.</span></span> <span data-ttu-id="87a05-176">데이터베이스 이동과 관련된 도움말을 보려면 [데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-176">For help with moving a database, see [Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87a05-177">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="87a05-177">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="87a05-178">차등 데이터베이스 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="87a05-178">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="87a05-179">NORECOVERY 절을 지정하고 RESTORE DATABASE 문을 실행하여 차등 데이터베이스 백업에 앞서 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-179">Execute the RESTORE DATABASE statement, specifying the NORECOVERY clause, to restore the full database backup that comes before the differential database backup.</span></span> <span data-ttu-id="87a05-180">자세한 내용은 [방법: 전체 백업 복원](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-180">For more information, see [How to: Restore a Full Backup](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="87a05-181">RESTORE DATABASE 문을 실행하여 차등 데이터베이스 백업을 복원합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-181">Execute the RESTORE DATABASE statement to restore the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="87a05-182">차등 데이터베이스 백업이 적용될 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="87a05-182">The name of the database to which the differential database backup is applied.</span></span>  
  
    -   <span data-ttu-id="87a05-183">차등 데이터베이스 백업을 복원하는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="87a05-183">The backup device where the differential database backup is restored from.</span></span>  
  
    -   <span data-ttu-id="87a05-184">차등 데이터베이스 백업이 복원된 후 적용할 트랜잭션 로그 백업이 있을 경우 NORECOVERY 절,</span><span class="sxs-lookup"><span data-stu-id="87a05-184">The NORECOVERY clause if you have transaction log backups to apply after the differential database backup is restored.</span></span> <span data-ttu-id="87a05-185">그렇지 않으면 RECOVERY 절</span><span class="sxs-lookup"><span data-stu-id="87a05-185">Otherwise, specify the RECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="87a05-186">전체 복구 모델이나 대량 로그 복구 모델을 사용할 경우 차등 데이터베이스 백업을 복원하면 차등 데이터베이스 백업이 완료된 시점까지 데이터베이스가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-186">With the full or bulk-logged recovery model, restoring a differential database backup restores the database to the point at which the differential database backup was completed.</span></span> <span data-ttu-id="87a05-187">오류 지점까지 복구하려면 마지막 차등 데이터베이스 백업이 생성된 후에 만든 트랜잭션 로그 백업을 모두 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-187">To recover to the point of failure, you must apply all transaction log backups created after the last differential database backup was created.</span></span> <span data-ttu-id="87a05-188">자세한 내용은 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87a05-188">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="87a05-189">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="87a05-189">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-restoring-a-differential-database-backup"></a><span data-ttu-id="87a05-190">A.</span><span class="sxs-lookup"><span data-stu-id="87a05-190">A.</span></span> <span data-ttu-id="87a05-191">차등 데이터베이스 백업 복원</span><span class="sxs-lookup"><span data-stu-id="87a05-191">Restoring a differential database backup</span></span>  
 <span data-ttu-id="87a05-192">다음은 `MyAdvWorks` 데이터베이스의 데이터베이스 및 차등 데이터베이스 백업을 복원하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-192">This example restores a database and differential database backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost, and restore full database,   
-- specifying the original full database backup and NORECOVERY,   
-- which allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   RECOVERY;  
GO  
```  
  
#### <a name="b-restoring-a-database-differential-database-and-transaction-log-backup"></a><span data-ttu-id="87a05-193">B.</span><span class="sxs-lookup"><span data-stu-id="87a05-193">B.</span></span> <span data-ttu-id="87a05-194">데이터베이스, 차등 데이터베이스, 트랜잭션 로그 백업 복원</span><span class="sxs-lookup"><span data-stu-id="87a05-194">Restoring a database, differential database, and transaction log backup</span></span>  
 <span data-ttu-id="87a05-195">다음은 `MyAdvWorks` 데이터베이스의 데이터베이스, 차등 데이터베이스 및 트랜잭션 로그 백업을 복원하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="87a05-195">This example restores a database, differential database, and transaction log backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost at this point. Now restore the full   
-- database. Specify the original full database backup and NORECOVERY.  
-- NORECOVERY allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   NORECOVERY;  
GO  
-- Now restore each transaction log backup created after  
-- the differential database backup.  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log1  
   WITH NORECOVERY;  
GO  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log2  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="87a05-196">관련 작업</span><span class="sxs-lookup"><span data-stu-id="87a05-196">Related Tasks</span></span>  
  
-   [<span data-ttu-id="87a05-197">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87a05-197">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="87a05-198">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87a05-198">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="87a05-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87a05-199">See Also</span></span>  
 <span data-ttu-id="87a05-200">[차등 백업&#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="87a05-200">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="87a05-201">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87a05-201">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
