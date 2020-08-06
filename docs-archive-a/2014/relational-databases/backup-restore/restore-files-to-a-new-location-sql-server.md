---
title: 새 위치로 파일 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring databases [SQL Server], moving
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
ms.assetid: b4f4791d-646e-4632-9980-baae9cb1aade
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a8336e5d186fb72df4e0a17fdd9affccab4ee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731739"
---
# <a name="restore-files-to-a-new-location-sql-server"></a><span data-ttu-id="40f6d-102">새 위치로 파일 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40f6d-102">Restore Files to a New Location (SQL Server)</span></span>
  <span data-ttu-id="40f6d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 파일을 새 위치에 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-103">This topic describes how to restore files to a new location in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="40f6d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="40f6d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="40f6d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="40f6d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="40f6d-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="40f6d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="40f6d-107">보안</span><span class="sxs-lookup"><span data-stu-id="40f6d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="40f6d-108">**다음을 사용하여 새 위치로 파일을 복원합니다.**</span><span class="sxs-lookup"><span data-stu-id="40f6d-108">**To restore files to a new location, using:**</span></span>  
  
     [<span data-ttu-id="40f6d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="40f6d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="40f6d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="40f6d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40f6d-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="40f6d-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="40f6d-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="40f6d-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="40f6d-113">파일을 복원하는 시스템 관리자는 복원될 데이터베이스를 현재 사용하고 있는 유일한 사람이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-113">The system administrator restoring the files must be the only person currently using the database to be restored.</span></span>  
  
-   <span data-ttu-id="40f6d-114">RESTORE는 명시적 또는 암시적 트랜잭션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-114">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="40f6d-115">전체 복구 모델 또는 대량 로그 복구 모델의 경우 파일을 복원하려면 먼저 활성 트랜잭션 로그(비상 로그라고도 함)를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-115">Under the full or bulk-logged recovery model, before you can restore files, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="40f6d-116">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-116">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="40f6d-117">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-117">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="40f6d-118">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-118">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="40f6d-119">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-119">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="40f6d-120">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40f6d-120">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="40f6d-121">보안</span><span class="sxs-lookup"><span data-stu-id="40f6d-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="40f6d-122">권한</span><span class="sxs-lookup"><span data-stu-id="40f6d-122">Permissions</span></span>  
 <span data-ttu-id="40f6d-123">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="40f6d-124">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다. FROM DATABASE_SNAPSHOT 옵션의 경우 데이터베이스가 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="40f6d-125">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="40f6d-126">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="40f6d-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="40f6d-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="40f6d-128">새 위치로 파일을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="40f6d-128">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="40f6d-129">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하고 해당 인스턴스를 확장한 다음 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-129">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="40f6d-130">원하는 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**, **복원**을 차례로 가리킨 다음 **파일 및 파일 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-130">Right-click the database that you want, point to **Tasks**, point to **Restore**, and then click **Files and Filegroups**.</span></span>  
  
3.  <span data-ttu-id="40f6d-131">**일반** 페이지의 **데이터베이스** 목록 상자에 복원할 데이터베이스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-131">On the **General** page, in the **To database** list box, enter the database to restore.</span></span> <span data-ttu-id="40f6d-132">새 데이터베이스를 입력하거나 드롭다운 목록에서 기존 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-132">You can enter a new database or choose an existing database from the drop-down list.</span></span> <span data-ttu-id="40f6d-133">이 목록에는 시스템 데이터베이스인 **master** 및 **tempdb**를 제외한 서버의 모든 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-133">The list includes all databases on the server, excluding the system databases **master** and **tempdb**.</span></span>  
  
4.  <span data-ttu-id="40f6d-134">복원할 백업 세트의 원본 및 위치를 지정하려면 다음 옵션 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-134">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="40f6d-135">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="40f6d-135">**From database**</span></span>  
  
         <span data-ttu-id="40f6d-136">목록 상자에 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-136">Enter a database name in the list box.</span></span> <span data-ttu-id="40f6d-137">이 목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-137">This list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="40f6d-138">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="40f6d-138">**From device**</span></span>  
  
         <span data-ttu-id="40f6d-139">찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-139">Click the browse button.</span></span> <span data-ttu-id="40f6d-140">**백업 디바이스 지정** 대화 상자에서 **백업 미디어 유형** 목록 상자에 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-140">In the **Specify backup devices** dialog box, select one of the listed device types in the **Backup media type** list box.</span></span> <span data-ttu-id="40f6d-141">**백업 미디어** 목록 상자에서 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-141">To select one or more devices for the **Backup media** list box, click **Add**.</span></span>  
  
         <span data-ttu-id="40f6d-142">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-142">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
5.  <span data-ttu-id="40f6d-143">**복원에 사용할 백업 세트 선택** 표에서 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-143">In the **Select the backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="40f6d-144">이 표는 지정한 위치에서 사용 가능한 백업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-144">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="40f6d-145">기본적으로 복구 계획이 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-145">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="40f6d-146">제안된 복구 계획을 재정의하려면 표에서 선택 항목을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-146">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="40f6d-147">선택 취소된 백업에 의존하는 모든 백업은 자동으로 선택 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-147">Any backups that depend on a deselected backup are deselected automatically.</span></span>  
  
    |<span data-ttu-id="40f6d-148">열 머리글</span><span class="sxs-lookup"><span data-stu-id="40f6d-148">Column head</span></span>|<span data-ttu-id="40f6d-149">값</span><span class="sxs-lookup"><span data-stu-id="40f6d-149">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="40f6d-150">**복원**</span><span class="sxs-lookup"><span data-stu-id="40f6d-150">**Restore**</span></span>|<span data-ttu-id="40f6d-151">확인란이 선택되어 있으면 백업 세트가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-151">The selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="40f6d-152">**이름**</span><span class="sxs-lookup"><span data-stu-id="40f6d-152">**Name**</span></span>|<span data-ttu-id="40f6d-153">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-153">The name of the backup set.</span></span>|  
    |<span data-ttu-id="40f6d-154">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="40f6d-154">**File Type**</span></span>|<span data-ttu-id="40f6d-155">백업의 데이터 형식인 **데이터**, **로그** 또는 **Filestream 데이터**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-155">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="40f6d-156">테이블에 포함된 데이터는 **데이터** 파일에 있고,</span><span class="sxs-lookup"><span data-stu-id="40f6d-156">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="40f6d-157">트랜잭션 로그 데이터는 **로그** 파일에 있으며,</span><span class="sxs-lookup"><span data-stu-id="40f6d-157">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="40f6d-158">파일 시스템에 저장되는 BLOB(Binary Large Object) 데이터는 **Filestream 데이터** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-158">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="40f6d-159">**형식**</span><span class="sxs-lookup"><span data-stu-id="40f6d-159">**Type**</span></span>|<span data-ttu-id="40f6d-160">수행된 백업 유형: **전체**, **차등** 또는 **트랜잭션 로그**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-160">The type of backup performed: **Full**, **Differential**, or **Transaction Log**.</span></span>|  
    |<span data-ttu-id="40f6d-161">**Server**</span><span class="sxs-lookup"><span data-stu-id="40f6d-161">**Server**</span></span>|<span data-ttu-id="40f6d-162">백업 작업을 수행한 데이터베이스 엔진 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-162">The name of the Database-Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="40f6d-163">**논리적 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="40f6d-163">**File Logical Name**</span></span>|<span data-ttu-id="40f6d-164">파일의 논리적 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-164">The logical name of the file.</span></span>|  
    |<span data-ttu-id="40f6d-165">**Database**</span><span class="sxs-lookup"><span data-stu-id="40f6d-165">**Database**</span></span>|<span data-ttu-id="40f6d-166">백업 작업과 관련된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-166">The name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="40f6d-167">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="40f6d-167">**Start Date**</span></span>|<span data-ttu-id="40f6d-168">클라이언트의 국가별 설정으로 표시되는 백업 작업 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-168">The date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="40f6d-169">**완료 날짜**</span><span class="sxs-lookup"><span data-stu-id="40f6d-169">**Finish Date**</span></span>|<span data-ttu-id="40f6d-170">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-170">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="40f6d-171">**크기**</span><span class="sxs-lookup"><span data-stu-id="40f6d-171">**Size**</span></span>|<span data-ttu-id="40f6d-172">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-172">The size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="40f6d-173">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="40f6d-173">**User Name**</span></span>|<span data-ttu-id="40f6d-174">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-174">The name of the user who performed the backup operation.</span></span>|  
  
6.  <span data-ttu-id="40f6d-175">**페이지 선택** 창에서 **옵션** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-175">In the **Select a page** pane, click the **Options** page.</span></span>  
  
7.  <span data-ttu-id="40f6d-176">**데이터베이스 파일을 다음으로 복원** 표에서 이동하려는 파일의 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-176">In the **Restore database files as** grid, specify a new location for the file or files that you want to move.</span></span>  
  
    |<span data-ttu-id="40f6d-177">열 머리글</span><span class="sxs-lookup"><span data-stu-id="40f6d-177">Column head</span></span>|<span data-ttu-id="40f6d-178">값</span><span class="sxs-lookup"><span data-stu-id="40f6d-178">Values</span></span>|  
    |-----------------|------------|  
    |<span data-ttu-id="40f6d-179">**원래 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="40f6d-179">**Original File Name**</span></span>|<span data-ttu-id="40f6d-180">원본 백업 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-180">The full path of a source backup file.</span></span>|  
    |<span data-ttu-id="40f6d-181">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="40f6d-181">**File Type**</span></span>|<span data-ttu-id="40f6d-182">백업의 데이터 형식인 **데이터**, **로그** 또는 **Filestream 데이터**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-182">Specifies the type of data in the backup: **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="40f6d-183">테이블에 포함된 데이터는 **데이터** 파일에 있고,</span><span class="sxs-lookup"><span data-stu-id="40f6d-183">Data that is contained in tables is in **Data** files.</span></span> <span data-ttu-id="40f6d-184">트랜잭션 로그 데이터는 **로그** 파일에 있으며,</span><span class="sxs-lookup"><span data-stu-id="40f6d-184">Transaction log data is in **Log** files.</span></span> <span data-ttu-id="40f6d-185">파일 시스템에 저장되는 BLOB(Binary Large Object) 데이터는 **Filestream 데이터** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-185">Binary large object (BLOB) data that is stored on the file system is in **Filestream Data** files.</span></span>|  
    |<span data-ttu-id="40f6d-186">**다음으로 복원**</span><span class="sxs-lookup"><span data-stu-id="40f6d-186">**Restore As**</span></span>|<span data-ttu-id="40f6d-187">복원할 데이터베이스 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-187">The full path of the database file to be restored.</span></span> <span data-ttu-id="40f6d-188">새 복원 파일을 지정하려면 입력란을 클릭하고 제안된 경로와 파일 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-188">To specify a new restore file, click the text box and edit the suggested path and file name.</span></span> <span data-ttu-id="40f6d-189">**다음으로 복원** 열에서 경로 또는 파일 이름을 변경하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 문에서 MOVE 옵션을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-189">Changing the path or file name in the **Restore As** column is equivalent to using the MOVE option in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.</span></span>|  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="40f6d-190">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="40f6d-190">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-files-to-a-new-location"></a><span data-ttu-id="40f6d-191">새 위치로 파일을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="40f6d-191">To restore files to a new location</span></span>  
  
1.  <span data-ttu-id="40f6d-192">필요에 따라 RESTORE FILELISTONLY 문을 실행하여 전체 데이터베이스 백업에 포함된 파일의 개수와 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-192">Optionally, execute the RESTORE FILELISTONLY statement to determine the number and names of the files in the full database backup.</span></span>  
  
2.  <span data-ttu-id="40f6d-193">RESTORE DATABASE 문을 실행하여 전체 데이터베이스 백업을 복원합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-193">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="40f6d-194">복원할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="40f6d-194">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="40f6d-195">복원할 전체 데이터베이스 백업이 있는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="40f6d-195">The backup device from where the full database backup will be restored.</span></span>  
  
    -   <span data-ttu-id="40f6d-196">새 위치로 각 파일을 복원하기 위한 MOVE 절</span><span class="sxs-lookup"><span data-stu-id="40f6d-196">The MOVE clause for each file to restore to a new location.</span></span>  
  
    -   <span data-ttu-id="40f6d-197">NORECOVERY 절</span><span class="sxs-lookup"><span data-stu-id="40f6d-197">The NORECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="40f6d-198">파일 백업을 만든 후에 파일이 수정된 경우에는 RESTORE LOG 문을 실행하여 트랜잭션 로그 백업을 적용합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-198">If the files have been modified after the file backup was created, execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="40f6d-199">트랜잭션 로그가 적용될 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="40f6d-199">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="40f6d-200">트랜잭션 로그 백업이 복원될 원본 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="40f6d-200">The backup device from where the transaction log backup will be restored.</span></span>  
  
    -   <span data-ttu-id="40f6d-201">현재 트랜잭션 로그 백업 다음에 적용할 다른 트랜잭션 로그 백업이 있으면 NORECOVERY 절을 지정하고 없으면 RECOVERY 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-201">The NORECOVERY clause if you have another transaction log backup to apply after the current one; otherwise, specify the RECOVERY clause.</span></span>  
  
         <span data-ttu-id="40f6d-202">트랜잭션 로그 백업이 적용되는 경우 파일과 파일 그룹을 백업한 시점이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-202">The transaction log backups, if applied, must cover the time when the files and filegroups were backed up.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="40f6d-203">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="40f6d-203">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="40f6d-204">다음 예에서는 원래 드라이브 C에 있었던 `MyNwind` 데이터베이스의 두 파일을 드라이브 D의 새 위치로 복원합니다. 두 트랜잭션 로그도 적용되어 데이터베이스를 현재 시간으로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-204">This example restores two of the files for the `MyNwind` database that were originally located on Drive C to new locations on Drive D. Two transaction logs will also be applied to restore the database to the current time.</span></span> <span data-ttu-id="40f6d-205">`RESTORE FILELISTONLY` 문은 복원할 데이터베이스에 있는 파일의 수와 논리적/물리적 이름을 확인하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="40f6d-205">The `RESTORE FILELISTONLY` statement is used to determine the number and logical and physical names of the files in the database being restored.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
RESTORE FILELISTONLY  
   FROM MyNwind_1;  
-- Restore the files for MyNwind.  
RESTORE DATABASE MyNwind  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   MOVE 'MyNwind_data_1' TO 'D:\MyData\MyNwind_data_1.mdf',   
   MOVE 'MyNwind_data_2' TO 'D:\MyData\MyNwind_data_2.ndf';  
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
  
## <a name="see-also"></a><span data-ttu-id="40f6d-206">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40f6d-206">See Also</span></span>  
 <span data-ttu-id="40f6d-207">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="40f6d-207">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="40f6d-208">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40f6d-208">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="40f6d-209">[백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="40f6d-209">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="40f6d-210">파일 및 파일 그룹 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40f6d-210">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
  
