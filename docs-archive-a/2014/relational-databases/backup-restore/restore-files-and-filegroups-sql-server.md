---
title: 파일 및 파일 그룹 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restorefilesandfilegrps.general.f1
- sql12.swb.restorefilesandfilegrps.options.f1
- sql12.swb.bselectfilegrpsfiles.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], restoring files and filegroups
- restoring [SQL Server], files
ms.assetid: 72603b21-3065-4b56-8b01-11b707911b05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2576f1326cb50fa197b1623aaa1326d70137823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731743"
---
# <a name="restore-files-and-filegroups-sql-server"></a><span data-ttu-id="f8bef-102">파일 및 파일 그룹 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f8bef-102">Restore Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="f8bef-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 파일 및 파일 그룹을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-103">This topic describes how to restore files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f8bef-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f8bef-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f8bef-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f8bef-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f8bef-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f8bef-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="f8bef-107">보안</span><span class="sxs-lookup"><span data-stu-id="f8bef-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f8bef-108">**다음을 사용하여 파일과 파일 그룹을 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="f8bef-108">**To restore files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="f8bef-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f8bef-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f8bef-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8bef-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f8bef-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f8bef-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f8bef-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f8bef-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f8bef-113">복원될 데이터베이스를 현재 사용하고 있는 사람만  파일과 파일 그룹을 복원하는 시스템 관리자가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-113">The system administrator restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="f8bef-114">RESTORE는 명시적 또는 암시적 트랜잭션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="f8bef-115">단순 복구 모델에서 파일은 읽기 전용 파일 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-115">Under the simple recovery model, the file must belong to a read-only filegroup.</span></span>  
  
-   <span data-ttu-id="f8bef-116">전체 복구 모델 또는 대량 로그 복구 모델의 경우 파일을 복원하려면 먼저 활성 트랜잭션 로그(비상 로그라고도 함)를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-116">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="f8bef-117">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-117">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f8bef-118">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-118">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="f8bef-119">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-119">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="f8bef-120">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-120">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="f8bef-121">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bef-121">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f8bef-122">보안</span><span class="sxs-lookup"><span data-stu-id="f8bef-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f8bef-123">권한</span><span class="sxs-lookup"><span data-stu-id="f8bef-123">Permissions</span></span>  
 <span data-ttu-id="f8bef-124">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-124">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="f8bef-125">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-125">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="f8bef-126">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-126">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="f8bef-127">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-127">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f8bef-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f8bef-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="f8bef-129">파일과 파일 그룹을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="f8bef-129">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="f8bef-130">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-130">After you connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f8bef-131">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-131">Expand **Databases**.</span></span> <span data-ttu-id="f8bef-132">데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스**를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-132">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="f8bef-133">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-133">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="f8bef-134">**파일 및 파일 그룹**을 클릭하여 **파일 및 파일 그룹 복원** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-134">Click **Files and Filegroups**, which opens the **Restore Files and Filegroups** dialog box.</span></span>  
  
5.  <span data-ttu-id="f8bef-135">**일반** 페이지의 **데이터베이스** 목록 상자에 복원할 데이터베이스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-135">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="f8bef-136">새 데이터베이스를 입력하거나 드롭다운 목록에서 기존 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-136">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="f8bef-137">이 목록에는 시스템 데이터베이스인 **master** 및 **tempdb**를 제외한 서버의 모든 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-137">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
6.  <span data-ttu-id="f8bef-138">복원할 백업 세트의 원본 및 위치를 지정하려면 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-138">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="f8bef-139">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f8bef-139">**From database**</span></span>  
  
         <span data-ttu-id="f8bef-140">목록 상자에 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-140">Enter a database name in the list box.</span></span> <span data-ttu-id="f8bef-141">이 목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-141">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="f8bef-142">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="f8bef-142">**From device**</span></span>  
  
         <span data-ttu-id="f8bef-143">찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-143">Click the browse button.</span></span> <span data-ttu-id="f8bef-144">**백업 디바이스 지정** 대화 상자에서 **백업 미디어 유형** 목록 상자에 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-144">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="f8bef-145">**백업 미디어** 목록 상자에서 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-145">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="f8bef-146">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-146">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
7.  <span data-ttu-id="f8bef-147">**복원에 사용할 백업 세트 선택** 표에서 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-147">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="f8bef-148">이 표는 지정한 위치에서 사용 가능한 백업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-148">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="f8bef-149">기본적으로 복구 계획이 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-149">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="f8bef-150">제안된 복구 계획을 재정의하려면 표에서 선택 항목을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-150">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="f8bef-151">선택 취소된 백업에 의존하는 모든 백업은 자동으로 선택 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-151">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="f8bef-152">열 머리글</span><span class="sxs-lookup"><span data-stu-id="f8bef-152">Column head</span></span>|<span data-ttu-id="f8bef-153">값</span><span class="sxs-lookup"><span data-stu-id="f8bef-153">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="f8bef-154">**복원**</span><span class="sxs-lookup"><span data-stu-id="f8bef-154">**Restore**</span></span>|<span data-ttu-id="f8bef-155">확인란이 선택되어 있으면 백업 세트가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-155">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="f8bef-156">**이름**</span><span class="sxs-lookup"><span data-stu-id="f8bef-156">**Name**</span></span>|<span data-ttu-id="f8bef-157">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-157">The name of the backup set.</span></span>|  
    |<span data-ttu-id="f8bef-158">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="f8bef-158">**File Type**</span></span>|<span data-ttu-id="f8bef-159">백업의 데이터 형식인 **데이터**, **로그** 또는 **Filestream 데이터**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-159">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="f8bef-160">테이블에 포함된 데이터는 **데이터** 파일에 있고,</span><span class="sxs-lookup"><span data-stu-id="f8bef-160">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="f8bef-161">트랜잭션 로그 데이터는 **로그** 파일에 있으며,</span><span class="sxs-lookup"><span data-stu-id="f8bef-161">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="f8bef-162">파일 시스템에 저장되는 BLOB(Binary Large Object) 데이터는 **Filestream 데이터** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-162">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="f8bef-163">**형식**</span><span class="sxs-lookup"><span data-stu-id="f8bef-163">**Type**</span></span>|<span data-ttu-id="f8bef-164">수행된 백업 유형: **전체**, **차등** 또는 **트랜잭션 로그**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-164">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="f8bef-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="f8bef-165">**Server**</span></span>|<span data-ttu-id="f8bef-166">백업 작업을 수행한 데이터베이스 엔진 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-166">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="f8bef-167">**논리적 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="f8bef-167">**File Logical Name**</span></span>|<span data-ttu-id="f8bef-168">파일의 논리적 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-168">The logical name of the file.</span></span>|  
    |<span data-ttu-id="f8bef-169">**Database**</span><span class="sxs-lookup"><span data-stu-id="f8bef-169">**Database**</span></span>|<span data-ttu-id="f8bef-170">백업 작업과 관련된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-170">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="f8bef-171">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="f8bef-171">**Start Date**</span></span>|<span data-ttu-id="f8bef-172">클라이언트의 국가별 설정으로 표시되는 백업 작업 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-172">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f8bef-173">**완료 날짜**</span><span class="sxs-lookup"><span data-stu-id="f8bef-173">**Finish Date**</span></span>|<span data-ttu-id="f8bef-174">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-174">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f8bef-175">**크기**</span><span class="sxs-lookup"><span data-stu-id="f8bef-175">**Size**</span></span>|<span data-ttu-id="f8bef-176">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-176">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="f8bef-177">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="f8bef-177">**User Name**</span></span>|<span data-ttu-id="f8bef-178">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-178">The name of the user who performed the backup operation.</span></span>|  
  
8.  <span data-ttu-id="f8bef-179">고급 옵션을 보거나 선택하려면 **페이지 선택** 창에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-179">To view or select the advanced options, click **Options** in the **Select a page pane**.</span></span>  
  
9. <span data-ttu-id="f8bef-180">**복원 옵션** 패널에서 상황에 맞는 경우 다음 옵션에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-180">In the **Restore options** panel, you can choose any of the following options, if appropriate for your situation.</span></span>  
  
     <span data-ttu-id="f8bef-181">**파일 그룹으로 복원**</span><span class="sxs-lookup"><span data-stu-id="f8bef-181">**Restore as filegroup**</span></span>  
     <span data-ttu-id="f8bef-182">전체 파일 그룹을 복원함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-182">Indicates that an entire filegroup is being restored.</span></span>  
  
     <span data-ttu-id="f8bef-183">**기존 데이터베이스 덮어쓰기**</span><span class="sxs-lookup"><span data-stu-id="f8bef-183">**Overwrite the existing database**</span></span>  
     <span data-ttu-id="f8bef-184">이름이 동일한 데이터베이스 또는 파일이 이미 있더라도 복원 작업에서 기존 데이터베이스 및 관련 파일을 덮어쓰도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-184">Specifies that the restore operation should overwrite any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
     <span data-ttu-id="f8bef-185">이 옵션을 선택하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 REPLACE 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-185">Selecting this option is equivalent to using the REPLACE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="f8bef-186">**각 백업 복원 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="f8bef-186">**Prompt before restoring each backup**</span></span>  
     <span data-ttu-id="f8bef-187">각 백업 세트를 복원하기 전에 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-187">Asks you for confirmation before restoring each backup set.</span></span>  
  
     <span data-ttu-id="f8bef-188">이 옵션은 서버에 하나의 테이프 디바이스가 있을 때와 같이 여러 미디어 세트의 테이프를 바꿔야 할 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-188">This option is particularly useful where you must swap tapes for different media sets, such as when the server has one tape device.</span></span>  
  
     <span data-ttu-id="f8bef-189">**복원된 데이터베이스에 대한 액세스 제한**</span><span class="sxs-lookup"><span data-stu-id="f8bef-189">**Restrict access to the restored database**</span></span>  
     <span data-ttu-id="f8bef-190">**db_owner**, **dbcreator**또는 **sysadmin**의 멤버만 복원된 데이터베이스를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-190">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
     <span data-ttu-id="f8bef-191">이 옵션을 선택하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 RESTRICTED_USER 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-191">Selecting this option is synonymous to using the RESTRICTED_USER option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
10. <span data-ttu-id="f8bef-192">상황에 따라 **데이터베이스 파일을 다음으로 복원** 표에서 각 파일에 대한 새 복원 대상을 지정하여 데이터베이스를 새 위치에 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-192">Optionally, you can restore the database to a new location by specifying a new restore destination for each file in the **Restore database files as** grid.</span></span>  
  
    |<span data-ttu-id="f8bef-193">열 머리글</span><span class="sxs-lookup"><span data-stu-id="f8bef-193">Column head</span></span>|<span data-ttu-id="f8bef-194">값</span><span class="sxs-lookup"><span data-stu-id="f8bef-194">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="f8bef-195">**원래 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="f8bef-195">**Original File Name**</span></span>|<span data-ttu-id="f8bef-196">원본 백업 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-196">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="f8bef-197">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="f8bef-197">**File Type**</span></span>|<span data-ttu-id="f8bef-198">백업의 데이터 형식인 **데이터**, **로그** 또는 **Filestream 데이터**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-198">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="f8bef-199">테이블에 포함된 데이터는 **데이터** 파일에 있고,</span><span class="sxs-lookup"><span data-stu-id="f8bef-199">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="f8bef-200">트랜잭션 로그 데이터는 **로그** 파일에 있으며,</span><span class="sxs-lookup"><span data-stu-id="f8bef-200">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="f8bef-201">파일 시스템에 저장되는 BLOB(Binary Large Object) 데이터는 **Filestream 데이터** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-201">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="f8bef-202">**다음으로 복원**</span><span class="sxs-lookup"><span data-stu-id="f8bef-202">**Restore As**</span></span>|<span data-ttu-id="f8bef-203">복원할 데이터베이스 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-203">The full path of the database file to be restored.</span></span> <span data-ttu-id="f8bef-204">새 복원 파일을 지정하려면 입력란을 클릭하고 제안된 경로와 파일 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-204">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="f8bef-205">**다음으로 복원** 열에서 경로 또는 파일 이름을 변경하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 MOVE 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-205">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
11. <span data-ttu-id="f8bef-206">**복구 상태** 패널에서 복원 작업 이후의 데이터베이스 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-206">The **Recovery state** panel determines the state of the database after the restore operation.</span></span>  
  
     <span data-ttu-id="f8bef-207">**커밋되지 않은 트랜잭션을 롤백하여 데이터베이스를 사용할 수 있는 상태로 유지합니다. 추가 트랜잭션 로그를 복원할 수 없습니다. (RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="f8bef-207">**Leave the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
     <span data-ttu-id="f8bef-208">데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-208">Recovers the database.</span></span> <span data-ttu-id="f8bef-209">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-209">This is the default behavior.</span></span> <span data-ttu-id="f8bef-210">필요한 모든 백업을 지금 복원하는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-210">Choose this option only if you are restoring all of the necessary backups now.</span></span> <span data-ttu-id="f8bef-211">이 옵션은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 WITH RECOVERY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-211">This option is equivalent to specifying WITH RECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="f8bef-212">**데이터베이스를 비작동 상태로 유지하고 커밋되지 않은 트랜잭션을 롤백하지 않습니다. 추가 트랜잭션 로그를 복원할 수 (RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="f8bef-212">**Leave the database non-operational, and don't roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
     <span data-ttu-id="f8bef-213">데이터베이스를 복원 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-213">Leaves the database in the restoring state.</span></span> <span data-ttu-id="f8bef-214">데이터베이스를 복구하려면 앞의 RESTORE WITH RECOVERY 옵션을 사용하여 다른 복원을 수행해야 합니다(위의 내용 참조).</span><span class="sxs-lookup"><span data-stu-id="f8bef-214">To recover the database, you will need to perform another restore using the preceding RESTORE WITH RECOVERY option (see above).</span></span> <span data-ttu-id="f8bef-215">이 옵션은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 WITH NORECOVERY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-215">This option is equivalent to specifying WITH NORECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="f8bef-216">이 옵션을 선택하면 **복제 설정 유지** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-216">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
     <span data-ttu-id="f8bef-217">**데이터베이스를 읽기 전용 모드로 유지합니다. 커밋되지 않은 트랜잭션을 롤백하지만 복구 결과를 실행 취소할 수 있도록 롤백 작업을 파일에 (RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="f8bef-217">**Leave the database in read-only mode. Roll back the uncommitted transactions, but save the rollback operation in a file so the recovery effects can be undone. (RESTORE WITH STANDBY)**</span></span>  
     <span data-ttu-id="f8bef-218">데이터베이스를 대기 모드로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-218">Leaves the database in a standby state.</span></span> <span data-ttu-id="f8bef-219">이 옵션은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 WITH STANDBY를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-219">This option is equivalent to specifying WITH STANDBY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>  
  
     <span data-ttu-id="f8bef-220">이 옵션을 선택하려면 대기 파일을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-220">Choosing this option requires that you specify a standby file.</span></span>  
  
     <span data-ttu-id="f8bef-221">**롤백 실행 취소 파일**</span><span class="sxs-lookup"><span data-stu-id="f8bef-221">**Rollback undo file**</span></span>  
     <span data-ttu-id="f8bef-222">**롤백 실행 취소 파일** 입력란에 대기 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-222">Specify a standby file name in the **Rollback undo file** text box.</span></span> <span data-ttu-id="f8bef-223">데이터베이스를 읽기 전용 모드로 유지하는 경우 이 옵션이 필요합니다(RESTORE WITH STANDBY).</span><span class="sxs-lookup"><span data-stu-id="f8bef-223">This option is required if you leave the database in read-only mode (RESTORE WITH STANDBY).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f8bef-224">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f8bef-224">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups"></a><span data-ttu-id="f8bef-225">파일과 파일 그룹을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="f8bef-225">To restore files and filegroups</span></span>  
  
1.  <span data-ttu-id="f8bef-226">RESTORE DATABASE 문을 실행하여 파일과 파일 그룹 백업을 복원합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-226">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f8bef-227">복원할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="f8bef-227">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="f8bef-228">복원할 전체 데이터베이스 백업이 있는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="f8bef-228">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f8bef-229">복원할 각 파일에 대한 FILE 절</span><span class="sxs-lookup"><span data-stu-id="f8bef-229">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="f8bef-230">복원할 각 파일 그룹에 대한 FILEGROUP 절</span><span class="sxs-lookup"><span data-stu-id="f8bef-230">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="f8bef-231">NORECOVERY 절</span><span class="sxs-lookup"><span data-stu-id="f8bef-231">The NORECOVERY clause.</span></span> <span data-ttu-id="f8bef-232">백업을 만든 후 해당 파일들을 수정하지 않았으면 RECOVERY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-232">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="f8bef-233">파일 백업을 만든 후에 파일이 수정된 경우에는 RESTORE LOG 문을 실행하여 트랜잭션 로그 백업을 적용합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-233">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f8bef-234">트랜잭션 로그가 적용될 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="f8bef-234">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="f8bef-235">트랜잭션 로그 백업이 복원될 원본 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="f8bef-235">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f8bef-236">현재 트랜잭션 로그 백업 다음에 적용할 다른 트랜잭션 로그 백업이 있으면 NORECOVERY 절을 지정하고 없으면 RECOVERY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-236">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="f8bef-237">트랜잭션 로그 백업이 적용되는 경우, 트랜잭션 로그 백업은 로그의 끝까지(모든 데이터베이스 파일을 복원하지 않는 경우) 파일 및 파일 그룹을 백업하는 시점을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-237">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up until the end of log (unless ALL database files are restored).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f8bef-238">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f8bef-238">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f8bef-239">다음은 `MyDatabase` 데이터베이스의 파일과 파일 그룹을 복원하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-239">This example restores the files and filegroups for the `MyDatabase` database.</span></span> <span data-ttu-id="f8bef-240">현재 시간으로 데이터베이스를 복원하기 위해 두 개의 트랜잭션 로그가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bef-240">To restore the database to the current time, two transaction logs are applied.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyDatabase.  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyDatabase_1  
   WITH NORECOVERY;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8bef-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8bef-241">See Also</span></span>  
 <span data-ttu-id="f8bef-242">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="f8bef-242">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="f8bef-243">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f8bef-243">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="f8bef-244">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f8bef-244">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="f8bef-245">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f8bef-245">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="f8bef-246">[트랜잭션 로그 백업 복원&#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f8bef-246">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="f8bef-247">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f8bef-247">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
