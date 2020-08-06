---
title: SQL Server 데이터베이스를 지정 시간으로 복원(전체 복구 모델) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- STOPAT clause [RESTORE LOG statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
ms.assetid: 3a5daefd-08a8-4565-b54f-28ad01a47d32
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c71ff6e75cbbf27042c1eac70b1f97076290865
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653460"
---
# <a name="restore-a-sql-server-database-to-a-point-in-time-full-recovery-model"></a><span data-ttu-id="8e9c2-102">SQL Server 데이터베이스를 지정 시간으로 복원(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="8e9c2-102">Restore a SQL Server Database to a Point in Time (Full Recovery Model)</span></span>
  <span data-ttu-id="8e9c2-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스를 지정 시간으로 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-103">This topic describes how to restore a database to a point in time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8e9c2-104">이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-104">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that use the full or bulk-logged recovery models.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e9c2-105">대량 로그 복구 모델에서 로그 백업에 대량 로그 변경 내용이 있을 경우 해당 백업 내의 지점으로 지정 시간 복구를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-105">Under the bulk-logged recovery model, if a log backup contains bulk-logged changes, point-in-time recovery is not possible to a point within that backup.</span></span> <span data-ttu-id="8e9c2-106">이 경우에는 데이터베이스를 트랜잭션 로그 백업의 끝으로 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-106">The database must be recovered to the end of the transaction log backup.</span></span>  
  
-   <span data-ttu-id="8e9c2-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8e9c2-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8e9c2-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8e9c2-109">보안</span><span class="sxs-lookup"><span data-stu-id="8e9c2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8e9c2-110">**SQL Server 데이터베이스를 지정 시간으로 복원하려면:**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-110">**To restore a SQL Server database to a point in time, using:**</span></span>  
  
     [<span data-ttu-id="8e9c2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e9c2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8e9c2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e9c2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8e9c2-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8e9c2-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8e9c2-114">권장 사항</span><span class="sxs-lookup"><span data-stu-id="8e9c2-114">Recommendations</span></span>  
  
-   <span data-ttu-id="8e9c2-115">STANDBY를 사용하여 알 수 없는 지정 시간을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-115">Use STANDBY to find unknown point in time.</span></span>  
  
-   <span data-ttu-id="8e9c2-116">복원 순서의 이른 시간으로 지정 시간 지정</span><span class="sxs-lookup"><span data-stu-id="8e9c2-116">Specify the point in time early in a restore sequence</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8e9c2-117">보안</span><span class="sxs-lookup"><span data-stu-id="8e9c2-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8e9c2-118">권한</span><span class="sxs-lookup"><span data-stu-id="8e9c2-118">Permissions</span></span>  
 <span data-ttu-id="8e9c2-119">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-119">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="8e9c2-120">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-120">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="8e9c2-121">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-121">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="8e9c2-122">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-122">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8e9c2-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8e9c2-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8e9c2-124">**데이터베이스를 지정 시간으로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-124">**To restore a database to a point in time**</span></span>  
  
1.  <span data-ttu-id="8e9c2-125">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-125">In Object Explorer, connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="8e9c2-126">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-126">Expand **Databases**.</span></span> <span data-ttu-id="8e9c2-127">데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스**를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-127">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="8e9c2-128">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 가리키고 **데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-128">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="8e9c2-129">**일반** 페이지에서 **원본** 섹션을 사용하여 복원할 백업 집합의 원본과 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-129">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="8e9c2-130">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-130">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="8e9c2-131">**Database**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-131">**Database**</span></span>  
  
         <span data-ttu-id="8e9c2-132">복원할 데이터베이스를 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-132">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="8e9c2-133">목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-133">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e9c2-134">백업을 다른 서버에서 가져온 경우 대상 서버에 지정한 데이터베이스에 대한 백업 기록 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-134">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="8e9c2-135">이 경우 **디바이스** 를 선택하여 복원할 파일이나 디바이스를 수동으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-135">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="8e9c2-136">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-136">**Device**</span></span>  
  
         <span data-ttu-id="8e9c2-137">찾아보기( **...** ) 단추를 클릭하여 **백업 디바이스 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-137">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="8e9c2-138">**백업 미디어 유형** 상자에서 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-138">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="8e9c2-139">**백업 미디어** 상자에 대해 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-139">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="8e9c2-140">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-140">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="8e9c2-141">**원본: 디바이스: 데이터베이스** 목록 상자에서 복원할 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-141">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="8e9c2-142">**참고** 이 목록은 **디바이스** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-142">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="8e9c2-143">선택한 디바이스에 백업이 있는 데이터베이스만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-143">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="8e9c2-144">**대상** 섹션의 **데이터베이스** 상자에는 복원할 데이터베이스의 이름이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-144">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="8e9c2-145">데이터베이스의 이름을 변경하려면 **데이터베이스** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-145">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
6.  <span data-ttu-id="8e9c2-146">**일정** 을 클릭하여 **백업 시간대** 대화 상자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-146">Click **Timeline** to access the **Backup Timeline** dialog box.</span></span>  
  
7.  <span data-ttu-id="8e9c2-147">**복원 위치** 섹션에서 **특정 날짜 및 시간**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-147">In the **Restore to** section, click **Specific date and time**.</span></span>  
  
8.  <span data-ttu-id="8e9c2-148">**날짜** 및 **시간** 상자 또는 슬라이더 막대를 사용하여 복원을 중지할 특정 날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-148">Use either the **Date** and **Time** boxes or the slider bar to specify a specific date and time to where the restore should stop.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e9c2-149">**시간대 간격** 상자를 사용하여 일정에 표시되는 시간을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-149">Use the **Timeline Interval** box to change the amount of time displayed on the timeline.</span></span>  
  
9. <span data-ttu-id="8e9c2-150">특정 지정 시간을 지정한 후에는 데이터베이스 복구 관리자에서 해당 지정 시간에 복원해야 하는 백업만 **복원에 사용할 백업 세트 선택** 표의 **복원** 열에서 선택되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-150">After you have specified a specific point in time, the Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected in the **Restore** column of the **Backup sets to restore** grid.</span></span> <span data-ttu-id="8e9c2-151">이러한 선택된 백업은 지정 시간 복원에 필요한 권장 복원 계획을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-151">These selected backups make up the recommended restore plan for your point-in-time restore.</span></span> <span data-ttu-id="8e9c2-152">지정 시간 복원 작업에는 선택된 백업만을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-152">You should use only the selected backups for your point-in-time restore operation.</span></span>  
  
     <span data-ttu-id="8e9c2-153">**복원에 사용할 백업 세트** 표의 열에 대한 자세한 내용은 [데이터베이스 복원&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="8e9c2-154">데이터베이스 복구 관리자에 대한 자세한 내용은 [복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-154">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
10. <span data-ttu-id="8e9c2-155">상황에 따라 **옵션** 페이지의 **복원 옵션** 패널에서 다음 옵션 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-155">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="8e9c2-156">**기존 데이터베이스 덮어쓰기(WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-156">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="8e9c2-157">**복제 설정 유지(WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-157">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="8e9c2-158">**복원된 데이터베이스에 대한 액세스 제한(WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="8e9c2-159">이러한 옵션에 대한 자세한 내용은 [데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
11. <span data-ttu-id="8e9c2-160">**복구 상태** 상자에 대한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="8e9c2-161">이 상자에서 복원 작업 후 데이터베이스의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="8e9c2-162">**RESTORE WITH RECOVERY** 는 커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용 준비가 된 상태로 유지하는 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="8e9c2-163">추가 트랜잭션 로그를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="8e9c2-164">필요한 모든 백업을 지금 복원하는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="8e9c2-165">**RESTORE WITH NORECOVERY** 는 데이터베이스를 비작동 상태로 유지하고 커밋되지 않은 트랜잭션을 롤백하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="8e9c2-166">추가 트랜잭션 로그를 복원할 수</span><span class="sxs-lookup"><span data-stu-id="8e9c2-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="8e9c2-167">데이터베이스는 복구할 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="8e9c2-168">**RESTORE WITH STANDBY** 는 읽기 전용 모드로 데이터베이스를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="8e9c2-169">이 옵션은 커밋되지 않은 트랜잭션의 실행을 취소하지만, 복구 결과를 되돌릴 수 있도록 실행 취소 동작을 대기 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="8e9c2-170">옵션에 대한 설명은 [데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
12. <span data-ttu-id="8e9c2-171">**복원 전 비상 로그 백업 수행** 은 선택한 지정 시간에 필요한 경우에 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-171">**Take tail-log backup before restore** will be selected if it is necessary for the point in time that you have selected.</span></span> <span data-ttu-id="8e9c2-172">이 설정을 수정할 필요는 없지만 필요하지 않은 경우에도 비상 로그를 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-172">You do not need to modify this setting, but you can choose to backup the tail of the log even if it is not required.</span></span>  
  
13. <span data-ttu-id="8e9c2-173">데이터베이스에 대한 활성 연결이 있으면 복원 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-173">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="8e9c2-174">**기존 연결 닫기** 옵션을 선택하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 와 데이터베이스 간의 모든 활성 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-174">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="8e9c2-175">이 확인란을 선택하면 복원 작업을 수행하기 전에 데이터베이스가 단일 사용자 모드로 설정되고 복원 작업이 완료될 때 데이터베이스가 다중 사용자 모드로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-175">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
14. <span data-ttu-id="8e9c2-176">각 복원 작업 사이에 확인 메시지를 표시하려면 **각 백업 복원 전에 확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-176">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="8e9c2-177">데이터베이스가 크고 복원 작업의 상태를 모니터링하려는 경우가 아니면 이 옵션은 일반적으로 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-177">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8e9c2-178">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8e9c2-178">Using Transact-SQL</span></span>  
 <span data-ttu-id="8e9c2-179">**시작하기 전 주의 사항**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-179">**Before you begin**</span></span>  
  
 <span data-ttu-id="8e9c2-180">지정된 시간은 항상 로그 백업에서 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-180">A specified time is always restored from a log backup.</span></span> <span data-ttu-id="8e9c2-181">복원 순서의 모든 RESTORE LOG 문에서 동일한 STOPAT 절에 대상 시간이나 트랜잭션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-181">In every RESTORE LOG statement of the restore sequence, you must specify your target time or transaction in an identical STOPAT clause.</span></span> <span data-ttu-id="8e9c2-182">지정 시간 복원을 수행하려면 먼저 종료 지점이 대상 복원 시간보다 빠른 전체 데이터베이스 백업을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-182">As a prerequisite to a point-in-time restore, you must first restore a full database backup whose end point is earlier than your target restore time.</span></span> <span data-ttu-id="8e9c2-183">대상 지정 시간이 포함된 로그 백업까지의 모든 후속 로그 백업을 복원하는 동안 이 전체 데이터베이스 백업은 가장 최근 전체 데이터베이스 백업보다 더 오래된 버전일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-183">That full database backup can be older than the most recent full database backup as long as you then restore every subsequent log backup, up to and including the log backup that contains your target point in time.</span></span>  
  
 <span data-ttu-id="8e9c2-184">복원할 데이터베이스를 손쉽게 확인하려면 선택적으로 RESTORE DATABASE 문에 WITH STOPAT 절을 지정하여 데이터 백업이 지정된 대상 시간에 비해 너무 최근인 경우 오류가 발생하도록 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-184">To help you identify which database backup to restore, you can optionally specify your WITH STOPAT clause in your RESTORE DATABASE statement to raise an error if a data backup is too recent for the specified target time.</span></span> <span data-ttu-id="8e9c2-185">그러나 데이터 백업에 대상 시간이 포함된 경우에도 항상 전체 데이터 백업이 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-185">The complete data backup is always restored, even if it contains the target time.</span></span>  
  
 <span data-ttu-id="8e9c2-186">**기본 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-186">**Basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax**</span></span>  
  
 <span data-ttu-id="8e9c2-187"><backup_device> STOPAT \*\* = *`time`* ,\*\* RECOVERY로 로그 *database_name* 복원 ...</span><span class="sxs-lookup"><span data-stu-id="8e9c2-187">RESTORE LOG *database_name* FROM <backup_device> WITH STOPAT **=*`time`*,** RECOVERY...</span></span>  
  
 <span data-ttu-id="8e9c2-188">복구 지점은 time에 지정 된 값 또는 그 전에 발생 한 최근 트랜잭션 커밋입니다 `datetime` . *time*</span><span class="sxs-lookup"><span data-stu-id="8e9c2-188">The recovery point is the latest transaction commit that occurred at or before the `datetime` value that is specified by *time*.</span></span>  
  
 <span data-ttu-id="8e9c2-189">특정 시점 이전에 수정한 내용만 복원하려면 복원하는 각 백업에 대해 WITH STOPAT **=** *time*을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-189">To restore only the modifications that were made before a specific point in time, specify WITH STOPAT **=** *time* for each backup you restore.</span></span> <span data-ttu-id="8e9c2-190">이렇게 하면 대상 시간을 지나치지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-190">This makes sure that you do not go past the target time.</span></span>  
  
 <span data-ttu-id="8e9c2-191">**데이터베이스를 지정 시간으로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="8e9c2-191">**To restore a database to a point in time**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e9c2-192">이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-192">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="8e9c2-193">데이터베이스를 복원할 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-193">Connect to server instance on which you want to restore the database.</span></span>  
  
2.  <span data-ttu-id="8e9c2-194">NORECOVERY 옵션을 사용하여 RESTORE DATABASE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-194">Execute the RESTORE DATABASE statement using the NORECOVERY option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e9c2-195">부분 복원 순서에서 [FILESTREAM](../blob/filestream-sql-server.md) 파일 그룹이 제외될 경우 지정 시간 복원은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-195">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="8e9c2-196">복원 순서를 강제로 계속할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="8e9c2-196">You can force the restore sequence to continue.</span></span> <span data-ttu-id="8e9c2-197">RESTORE 문에서 누락된 FILESTREAM 파일 그룹은 복원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-197">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="8e9c2-198">지정 시간 복원을 강제로 수행하려면 후속 RESTORE LOG 문에도 지정해야 하는 STOPAT, STOPATMARK 또는 STOPBEFOREMARK 옵션과 함께 CONTINUE_AFTER_ERROR 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-198">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="8e9c2-199">CONTINUE_AFTER_ERROR를 지정하면 부분 복원 순서가 성공하고 FILESTREAM 파일 그룹이 복구 불가능한 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-199">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
3.  <span data-ttu-id="8e9c2-200">데이터베이스를 복구하지 않고 마지막 전체 데이터베이스 백업과 마지막 차등 데이터베이스 백업(있는 경우)을 복원합니다(RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span><span class="sxs-lookup"><span data-stu-id="8e9c2-200">Restore the last differential database backup, if any,  without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
4.  <span data-ttu-id="8e9c2-201">로그 복원을 중지할 시간을 지정 하 여 각 트랜잭션 로그 백업을 만들어진 순서 대로 적용 합니다 (<backup_device> STOPAT\*\* = *`time`* ,\*\* RECOVERY로 데이터베이스 *database_name* 복원).</span><span class="sxs-lookup"><span data-stu-id="8e9c2-201">Apply each transaction log backup in the same sequence in which they were created, specifying the time at which you intend to stop restoring log (RESTORE DATABASE *database_name* FROM <backup_device> WITH STOPAT**=*`time`*,** RECOVERY).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e9c2-202">RECOVERY 및 STOPAT 옵션.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-202">The RECOVERY and STOPAT options.</span></span> <span data-ttu-id="8e9c2-203">지정된 시간이 트랜잭션 로그에서 수용하는 시간을 초과하는 경우처럼 요청한 시간이 트랜잭션 로그 백업에 포함되지 않을 경우 경고가 생성되고 데이터베이스는 복구되지 않은 상태로 남습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-203">If the transaction log backup does not contain the requested time (for example, if the time specified is beyond the end of the time covered by the transaction log), a warning is generated and the database remains unrecovered.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="8e9c2-204">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8e9c2-204">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="8e9c2-205">다음 예에서는 `12:00 AM` , `April 15, 2020` 상태로 데이터베이스를 복원하고 여러 로그 백업이 연관된 복원 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-205">The following example restores a database to its state as of `12:00 AM` on `April 15, 2020` and shows a restore operation that involves multiple log backups.</span></span> <span data-ttu-id="8e9c2-206">백업 디바이스 `AdventureWorksBackups`에서 복원할 전체 데이터베이스 백업은 해당 디바이스의 세 번째 백업 세트(`FILE = 3`)이고, 첫 번째 로그 백업은 네 번째 백업 세트(`FILE = 4`)이고, 두 번째 로그 백업은 다섯 번째 백업 세트(`FILE = 5`)입니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-206">On the backup device, `AdventureWorksBackups`, the full database backup to be restored is the third backup set on the device (`FILE = 3`), the first log backup is the fourth backup set (`FILE = 4`), and the second log backup is the fifth backup set (`FILE = 5`).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e9c2-207">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스는 단순 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-207">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="8e9c2-208">로그 백업을 허용하기 위해 전체 데이터베이스를 백업하기 전에 `ALTER DATABASE AdventureWorks SET RECOVERY FULL`을 사용하여 전체 복구 모델을 사용하도록 데이터베이스를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="8e9c2-208">To permit log backups, before taking a full database backup, the database was set to use the full recovery model, using `ALTER DATABASE AdventureWorks SET RECOVERY FULL`.</span></span>  
  
```  
RESTORE DATABASE AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks WITH RECOVERY;   
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8e9c2-209">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8e9c2-209">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8e9c2-210">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-210">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="8e9c2-211">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-211">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="8e9c2-212">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-212">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="8e9c2-213">데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-213">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="8e9c2-214">로그 시퀀스 번호로 복구&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-214">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e9c2-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e9c2-215">See Also</span></span>  
 <span data-ttu-id="8e9c2-216">[backupset&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e9c2-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="8e9c2-217">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e9c2-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="8e9c2-218">RESTORE HEADERONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8e9c2-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
  
