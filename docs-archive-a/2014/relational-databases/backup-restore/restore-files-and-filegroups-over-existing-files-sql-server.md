---
title: 기존 파일에서 파일 및 파일 그룹 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
- overwriting filegroups
- overwriting files
ms.assetid: 517e07eb-9685-4b06-90af-b1cc496700b7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc72ae3ae2472fe579755fa624e9af6953c7aed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650120"
---
# <a name="restore-files-and-filegroups-over-existing-files-sql-server"></a><span data-ttu-id="f4846-102">기존 파일에서 파일 및 파일 그룹 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4846-102">Restore Files and Filegroups over Existing Files (SQL Server)</span></span>
  <span data-ttu-id="f4846-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 기존 파일에 대해 파일 및 파일 그룹을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-103">This topic describes how to restore files and filegroups over existing files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f4846-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f4846-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f4846-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f4846-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f4846-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f4846-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f4846-107">보안</span><span class="sxs-lookup"><span data-stu-id="f4846-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f4846-108">**다음을 사용하여 기존 파일에서 파일과 파일 그룹을 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="f4846-108">**To restore files and filegroups over existing files, using:**</span></span>  
  
     [<span data-ttu-id="f4846-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f4846-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f4846-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f4846-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f4846-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f4846-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f4846-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f4846-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f4846-113">파일과 파일 그룹을 복원하는 시스템 관리자가 현재 복원될 데이터베이스를 사용하고 있는 유일한 사용자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-113">The system administrator who is restoring the files and filegroups must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="f4846-114">RESTORE는 명시적 또는 암시적 트랜잭션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="f4846-115">전체 복구 모델 또는 대량 로그 복구 모델의 경우 파일을 복원하려면 먼저 활성 트랜잭션 로그(비상 로그라고도 함)를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="f4846-116">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f4846-117">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="f4846-118">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="f4846-119">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="f4846-120">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4846-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f4846-121">보안</span><span class="sxs-lookup"><span data-stu-id="f4846-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f4846-122">권한</span><span class="sxs-lookup"><span data-stu-id="f4846-122">Permissions</span></span>  
 <span data-ttu-id="f4846-123">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="f4846-124">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="f4846-125">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="f4846-126">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f4846-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f4846-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-and-filegroups-over-existing-files"></a><span data-ttu-id="f4846-128">기존 파일에서 파일과 파일 그룹을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="f4846-128">To restore files and filegroups over existing files</span></span>  
  
1.  <span data-ttu-id="f4846-129">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하고 해당 인스턴스를 확장한 다음 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="f4846-130">원하는 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**, **복원**을 차례로 가리킨 다음 **파일 및 파일 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="f4846-131">**일반** 페이지의 **데이터베이스** 목록 상자에 복원할 데이터베이스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="f4846-132">새 데이터베이스를 입력하거나 드롭다운 목록에서 기존 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="f4846-133">이 목록에는 시스템 데이터베이스인 **master** 및 **tempdb**를 제외한 서버의 모든 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="f4846-134">복원할 백업 세트의 원본 및 위치를 지정하려면 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="f4846-135">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f4846-135">**From database**</span></span>  
  
         <span data-ttu-id="f4846-136">목록 상자에 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-136">Enter a database name in the list box.</span></span> <span data-ttu-id="f4846-137">이 목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="f4846-138">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="f4846-138">**From device**</span></span>  
  
         <span data-ttu-id="f4846-139">찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-139">Click the browse button.</span></span> <span data-ttu-id="f4846-140">**백업 디바이스 지정** 대화 상자에서 **백업 미디어 유형** 목록 상자에 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="f4846-141">**백업 미디어** 목록 상자에서 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="f4846-142">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="f4846-143">**복원에 사용할 백업 세트 선택** 표에서 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="f4846-144">이 표는 지정한 위치에서 사용 가능한 백업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="f4846-145">기본적으로 복구 계획이 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="f4846-146">제안된 복구 계획을 재정의하려면 표에서 선택 항목을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="f4846-147">선택 취소된 백업에 의존하는 모든 백업은 자동으로 선택 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="f4846-148">열 머리글</span><span class="sxs-lookup"><span data-stu-id="f4846-148">Column head</span></span>|<span data-ttu-id="f4846-149">값</span><span class="sxs-lookup"><span data-stu-id="f4846-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="f4846-150">**복원**</span><span class="sxs-lookup"><span data-stu-id="f4846-150">**Restore**</span></span>|<span data-ttu-id="f4846-151">확인란이 선택되어 있으면 백업 세트가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="f4846-152">**이름**</span><span class="sxs-lookup"><span data-stu-id="f4846-152">**Name**</span></span>|<span data-ttu-id="f4846-153">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="f4846-154">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="f4846-154">**File Type**</span></span>|<span data-ttu-id="f4846-155">백업의 데이터 형식인 **데이터**, **로그** 또는 **Filestream 데이터**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="f4846-156">테이블에 포함된 데이터는 **데이터** 파일에 있고,</span><span class="sxs-lookup"><span data-stu-id="f4846-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="f4846-157">트랜잭션 로그 데이터는 **로그** 파일에 있으며,</span><span class="sxs-lookup"><span data-stu-id="f4846-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="f4846-158">파일 시스템에 저장되는 BLOB(Binary Large Object) 데이터는 **Filestream 데이터** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="f4846-159">**형식**</span><span class="sxs-lookup"><span data-stu-id="f4846-159">**Type**</span></span>|<span data-ttu-id="f4846-160">수행된 백업 유형: **전체**, **차등** 또는 **트랜잭션 로그**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="f4846-161">**Server**</span><span class="sxs-lookup"><span data-stu-id="f4846-161">**Server**</span></span>|<span data-ttu-id="f4846-162">백업 작업을 수행한 데이터베이스 엔진 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="f4846-163">**논리적 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="f4846-163">**File Logical Name**</span></span>|<span data-ttu-id="f4846-164">파일의 논리적 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="f4846-165">**Database**</span><span class="sxs-lookup"><span data-stu-id="f4846-165">**Database**</span></span>|<span data-ttu-id="f4846-166">백업 작업과 관련된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="f4846-167">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="f4846-167">**Start Date**</span></span>|<span data-ttu-id="f4846-168">클라이언트의 국가별 설정으로 표시되는 백업 작업 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f4846-169">**완료 날짜**</span><span class="sxs-lookup"><span data-stu-id="f4846-169">**Finish Date**</span></span>|<span data-ttu-id="f4846-170">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="f4846-171">**크기**</span><span class="sxs-lookup"><span data-stu-id="f4846-171">**Size**</span></span>|<span data-ttu-id="f4846-172">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="f4846-173">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="f4846-173">**User Name**</span></span>|<span data-ttu-id="f4846-174">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="f4846-175">**페이지 선택** 창에서 **옵션** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="f4846-176">**복원 옵션** 패널에서 **기존 데이터베이스 덮어쓰기(WITH REPLACE)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-176">In the **Restore options** panel, select **Overwrite the existing database (WITH REPLACE)**.</span></span> <span data-ttu-id="f4846-177">복원 작업은 이름이 동일한 데이터베이스 또는 파일이 이미 있더라도 기존 데이터베이스 및 관련 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-177">The restore operation overwrites any existing databases and their related files, even if another database or file already exists with the same name.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f4846-178">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f4846-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-and-filegroups-over-existing-files"></a><span data-ttu-id="f4846-179">기존 파일에서 파일과 파일 그룹을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="f4846-179">To restore files and filegroups over existing files</span></span>  
  
1.  <span data-ttu-id="f4846-180">RESTORE DATABASE 문을 실행하여 파일과 파일 그룹 백업을 복원합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-180">Execute the RESTORE DATABASE statement to restore the file and filegroup backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f4846-181">복원할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="f4846-181">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="f4846-182">복원할 전체 데이터베이스 백업이 있는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="f4846-182">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f4846-183">복원할 각 파일에 대한 FILE 절</span><span class="sxs-lookup"><span data-stu-id="f4846-183">The FILE clause for each file to restore.</span></span>  
  
    -   <span data-ttu-id="f4846-184">복원할 각 파일 그룹에 대한 FILEGROUP 절</span><span class="sxs-lookup"><span data-stu-id="f4846-184">The FILEGROUP clause for each filegroup to restore.</span></span>  
  
    -   <span data-ttu-id="f4846-185">각 파일이 같은 이름과 위치에 있는 기존 파일로 복원될 수 있도록 지정하기 위한 REPLACE 옵션</span><span class="sxs-lookup"><span data-stu-id="f4846-185">The REPLACE option to specify that each file can be restored over existing files of the same name and location.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="f4846-186">REPLACE 옵션을 사용할 때는 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="f4846-186">Use the REPLACE option cautiously.</span></span> <span data-ttu-id="f4846-187">자세한 내용은 을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4846-187">For more information, see .</span></span>  
  
    -   <span data-ttu-id="f4846-188">NORECOVERY 옵션.</span><span class="sxs-lookup"><span data-stu-id="f4846-188">The NORECOVERY option.</span></span> <span data-ttu-id="f4846-189">백업을 만든 후 해당 파일들을 수정하지 않았으면 RECOVERY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-189">If the files have not been modified after the backup was created, specify the RECOVERY clause.</span></span>  
  
2.  <span data-ttu-id="f4846-190">파일 백업을 만든 후에 파일이 수정된 경우에는 RESTORE LOG 문을 실행하여 트랜잭션 로그 백업을 적용합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-190">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="f4846-191">트랜잭션 로그가 적용될 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="f4846-191">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="f4846-192">트랜잭션 로그 백업이 복원될 원본 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="f4846-192">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="f4846-193">현재 트랜잭션 로그 백업 다음에 적용할 다른 트랜잭션 로그 백업이 있으면 NORECOVERY 절을 지정하고 없으면 RECOVERY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-193">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="f4846-194">트랜잭션 로그 백업이 적용되는 경우 파일과 파일 그룹을 백업한 시점이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-194">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f4846-195">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f4846-195">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f4846-196">다음 예에서는 `MyNwind` 데이터베이스의 파일과 파일 그룹을 복원하고 같은 이름의 기존 파일을 모두 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-196">The following example restores the files and filegroups for the `MyNwind` database, and replaces any existing files of the same name.</span></span> <span data-ttu-id="f4846-197">또한 현재 시간으로 데이터베이스를 복원하기 위한 두 개의 트랜잭션 로그가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4846-197">Two transaction logs will also be applied to restore the database to the current time.</span></span>  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyNwind.  
RESTORE DATABASE MyNwind  
   FILE = 'MyNwind_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyNwind_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   REPLACE;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4846-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4846-198">See Also</span></span>  
 <span data-ttu-id="f4846-199">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="f4846-199">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="f4846-200">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f4846-200">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f4846-201">[파일 및 파일 그룹 복원&#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4846-201">[Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="f4846-202">백업 및 복원으로 데이터베이스 복사</span><span class="sxs-lookup"><span data-stu-id="f4846-202">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
