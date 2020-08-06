---
title: SSIS 카탈로그 백업, 복원 및 이동 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9de552ddd54168f516f42d9988302561616fd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649658"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a><span data-ttu-id="e0054-102">SSIS 카탈로그 백업, 복원 및 이동</span><span class="sxs-lookup"><span data-stu-id="e0054-102">Backup, Restore, and Move the SSIS Catalog</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="e0054-103">에는 SSISDB 데이터베이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-103">includes the SSISDB database.</span></span> <span data-ttu-id="e0054-104">SSISDB 데이터베이스에서 뷰를 쿼리하여 **SSISDB** 카탈로그에 저장된 개체, 설정 및 작업 데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-104">You query views in the SSISDB database to inspect objects, settings, and operational data that are stored in the **SSISDB** catalog.</span></span> <span data-ttu-id="e0054-105">이 항목에서는 데이터베이스 백업 및 복원에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-105">This topic provides instructions for backing up and restoring the database.</span></span>  
  
 <span data-ttu-id="e0054-106">**SSISDB** 카탈로그는 사용자가 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포한 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-106">The **SSISDB** catalog stores the packages that you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e0054-107">카탈로그에 대한 자세한 내용은 [SSIS 카탈로그](catalog/ssis-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-107">For more information about the catalog, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a> <span data-ttu-id="e0054-108">SSIS 데이터베이스를 백업하려면</span><span class="sxs-lookup"><span data-stu-id="e0054-108">To Back up the SSIS Database</span></span>  
  
1.  <span data-ttu-id="e0054-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0054-110">BACKUP MASTER KEY Transact-SQL 문을 사용하여 SSISDB 데이터베이스에 대한 마스터 키를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-110">Back up the master key for the SSISDB database, by using the BACKUP MASTER KEY Transact-SQL statement.</span></span> <span data-ttu-id="e0054-111">이 키는 사용자가 지정한 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-111">The key is stored in a file that you specify.</span></span> <span data-ttu-id="e0054-112">암호를 사용하여 파일의 마스터 키를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-112">Use a password to encrypt the master key in the file.</span></span>  
  
     <span data-ttu-id="e0054-113">문에 대한 자세한 내용은 [BACKUP MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-113">For more information about the statement, see [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
     <span data-ttu-id="e0054-114">다음 예에서는 마스터 키를 `c:\temp directory\RCTestInstKey` 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-114">In the following example, the master key is exported to the `c:\temp directory\RCTestInstKey` file.</span></span> <span data-ttu-id="e0054-115">마스터 키를 암호화하는 데에는 `LS2Setup!` 암호가 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-115">The `LS2Setup!` password is used to encrypt the master key.</span></span>  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  <span data-ttu-id="e0054-116">**에서** 데이터베이스 백업 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자를 사용하여 SSISDB 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-116">Back up the SSISDB database by using the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e0054-117">자세한 내용은 [방법: 데이터베이스 백업(SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-117">For more information, see [How to: Back Up a Database (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).</span></span>  
  
4.  <span data-ttu-id="e0054-118">다음을 수행하여 ##MS_SSISServerCleanupJobLogin##에 대한 CREATE LOGIN 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-118">Generate the CREATE LOGIN script for ##MS_SSISServerCleanupJobLogin##, by doing the following.</span></span> <span data-ttu-id="e0054-119">자세한 내용은 [CREATE LOGIN&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-119">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="e0054-120">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 **보안** 노드를 확장한 후 **로그인** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-120">In Object Explorer in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Security** node and then expand the **Logins** node.</span></span>  
  
    2.  <span data-ttu-id="e0054-121">**##MS_SSISServerCleanupJobLogin##** 을 마우스 오른쪽 단추로 클릭한 후 **로그인 스크립팅** > **CREATE** > **새 쿼리 편집기 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-121">Right-click **##MS_SSISServerCleanupJobLogin##**, and then click **Script Login as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
5.  <span data-ttu-id="e0054-122">SSISDB 카탈로그가 만들어지지 않은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스로 SSISDB 데이터베이스를 복원할 경우 다음을 수행하여 sp_ssis_startup에 대한 CREATE PROCEDURE 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-122">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate the CREATE PROCEDURE script for sp_ssis_startup, by doing the following.</span></span> <span data-ttu-id="e0054-123">자세한 내용은 [CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-123">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
    1.  <span data-ttu-id="e0054-124">개체 탐색기에서 **데이터베이스** 노드를 확장 한 다음 **시스템 데이터베이스**  >  **마스터**  >  **프로그래밍 기능**  >  **저장 프로시저** 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-124">In Object Explorer, expand the **Databases** node and then expand the **System Databases** > **master** > **Programmability** > **Stored Procedures** node.</span></span>  
  
    2.  <span data-ttu-id="e0054-125">**dbo.sp_ssis_startup**을 마우스 오른쪽 단추로 클릭한 후 **저장 프로시저 스크립팅** > **CREATE** > **새 쿼리 편집기 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-125">Right click **dbo.sp_ssis_startup**, and then click **Script Stored Procedure as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
6.  <span data-ttu-id="e0054-126">SQL Server 에이전트가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-126">Confirm that SQL Server Agent has been started</span></span>  
  
7.  <span data-ttu-id="e0054-127">SSISDB 카탈로그가 만들어지지 않은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스로 SSISDB 데이터베이스를 복원할 경우 다음을 수행하여 SSIS 서버 유지 관리 작업에 대한 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-127">If you will be restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, generate a script for the SSIS Server Maintenance Job by doing the following.</span></span> <span data-ttu-id="e0054-128">이 스크립트는 SSISDB 카탈로그가 생성될 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트에 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-128">The script is created in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent automatically when the SSISDB catalog is created.</span></span> <span data-ttu-id="e0054-129">이 작업은 보존 기간이 지난 작업 로그를 정리하고 오래된 프로젝트 버전을 제거하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-129">The job helps clean up cleanup operation logs outside the retention window and remove older versions of projects.</span></span>  
  
    1.  <span data-ttu-id="e0054-130">개체 탐색기에서 **SQL Server 에이전트** 노드를 확장한 후 **작업** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-130">In Object Explorer, expand the **SQL Server Agent** node and then expand the **Jobs** node.</span></span>  
  
    2.  <span data-ttu-id="e0054-131">SSIS 서버 유지 관리 작업을 마우스 오른쪽 단추로 클릭 한 후 **작업 스크립팅**  >  **CREATE**  >  **새 쿼리 편집기 창**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-131">Right click SSIS Server Maintenance Job, and then click **Script Job as** > **CREATE To** > **New Query Editor Window**.</span></span>  
  
### <a name="to-restore-the-ssis-database"></a><span data-ttu-id="e0054-132">SSIS 데이터베이스를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="e0054-132">To Restore the SSIS Database</span></span>  
  
1.  <span data-ttu-id="e0054-133">SSISDB 카탈로그가 만들어지지 않은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 SSISDB 데이터베이스를 복원할 경우 sp_configure 저장 프로시저를 실행하여 CLR(공용 언어 런타임)을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-133">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, enable common language runtime (clr) by running the sp_configure stored procedure.</span></span> <span data-ttu-id="e0054-134">자세한 내용은 [sp_configure&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 및 [clr enabled 옵션](https://go.microsoft.com/fwlink/?LinkId=231855)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-134">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [clr enabled Option](https://go.microsoft.com/fwlink/?LinkId=231855).</span></span>  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  <span data-ttu-id="e0054-135">SSISDB 카탈로그가 만들어지지 않은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스로 SSISDB 데이터베이스를 복원할 경우 비대칭 키를 만들고 비대칭 키로부터 로그인한 후 해당 로그인에 UNSAFE 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-135">If you are restoring the SSISDB database to an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog was never created, create the asymmetric key and the login from the asymmetric key, and grant UNSAFE permission to the login.</span></span>  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e0054-136">CLR 저장 프로시저를 사용하려면 해당 로그인에 UNSAFE 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-136">CLR stored procedures require UNSAFE permissions to be granted to the login because the login requires additional access to restricted resources, such as the Microsoft Win32 API.</span></span> <span data-ttu-id="e0054-137">UNSAFE 코드 권한에 대한 자세한 내용은 [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0054-137">For more information about the UNSAFE code permission, see [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).</span></span>  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  <span data-ttu-id="e0054-138">**에서** 데이터베이스 복원 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자를 사용하여 백업에서 SSISDB 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-138">Restore the SSISDB database from the backup by using the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e0054-139">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0054-139">For more information, see the following topics.</span></span>  
  
    -   [<span data-ttu-id="e0054-140">데이터베이스 복원&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="e0054-140">Restore Database &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="e0054-141">데이터베이스 복원&#40;파일 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="e0054-141">Restore Database &#40;Files Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [<span data-ttu-id="e0054-142">데이터베이스 복원&#40;옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="e0054-142">Restore Database &#40;Options Page&#41;</span></span>](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  <span data-ttu-id="e0054-143">[SSIS 데이터베이스를 백업하려면](#backup) 에서 ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup 및 SSIS 서버 유지 관리 작업에 대해 만든 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-143">Execute the scripts that you created in the [To Back up the SSIS Database](#backup) for ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup, and SSIS Server Maintenance Job.</span></span> <span data-ttu-id="e0054-144">SQL Server 에이전트가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-144">Confirm that SQL Server Agent has been started.</span></span>  
  
5.  <span data-ttu-id="e0054-145">다음 문을 실행하여 sp_ssis_startup 프로시저가 자동 실행되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-145">Run the following statement to set the sp_ssis_startup prodecure for autoexecution.</span></span> <span data-ttu-id="e0054-146">자세한 내용은 [sp_procoption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-146">For more information, see [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).</span></span>  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  <span data-ttu-id="e0054-147">**에서** 로그인 속성 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]대화 상자를 사용하여 SSISDB 사용자 ##MS_SSISServerCleanupJobUser##(SSISDB 데이터베이스)를 ##MS_SSISServerCleanupJobLogin##에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-147">Map the SSISDB user ##MS_SSISServerCleanupJobUser## (SSISDB database) to ##MS_SSISServerCleanupJobLogin##, by using the **Login Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
7.  <span data-ttu-id="e0054-148">다음 방법 중 하나를 사용하여 마스터 키를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-148">Restore the master key by using one of the following methods.</span></span> <span data-ttu-id="e0054-149">암호화에 대한 자세한 내용은 [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0054-149">For more information about encryption, see [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).</span></span>  
  
    -   <span data-ttu-id="e0054-150">**메서드 1**</span><span class="sxs-lookup"><span data-stu-id="e0054-150">**Method 1**</span></span>  
  
         <span data-ttu-id="e0054-151">이미 데이터베이스 마스터 키에 대한 백업을 수행했고 마스터 키를 암호화하기 위해 사용된 암호가 있는 경우 이 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-151">Use this method if you've already performed a backup of the database master key, and you have the password used to encrypt the master key.</span></span>  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="e0054-152">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 서비스 계정에 백업 키 파일에 대한 읽기 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-152">Confirm that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service account has permissions to read the backup key file.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e0054-153">데이터베이스 마스터 키가 아직 서비스 마스터 키로 암호화되지 않은 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에 다음과 같은 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-153">You will see the following warning message displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] if the database master key has not yet been encrypted by the service master key.</span></span> <span data-ttu-id="e0054-154">경고 메시지를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-154">Ignore the warning message.</span></span>  
        >   
        >  <span data-ttu-id="e0054-155">**현재 마스터 키를 해독할 수 없습니다. FORCE 옵션이 지정되어 있어 오류가 무시되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="e0054-155">**The current master key cannot be decrypted. The error was ignored because the FORCE option was specified.**</span></span>  
        >   
        >  <span data-ttu-id="e0054-156">FORCE 인수는 현재 데이터베이스 마스터 키가 열려 있지 않더라도 복원 프로세스가 계속되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-156">The FORCE argument specifies that the restore process should continue even if the current database master key is not open.</span></span> <span data-ttu-id="e0054-157">SSISDB 카탈로그의 경우 사용자가 데이터베이스를 복원 중인 인스턴스에서 데이터베이스 마스터 키가 아직 열려 있지 않으므로 이 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-157">For the SSISDB catalog, because the database master key has not been opened on the instance where you are restoring the database, you will see this message.</span></span>  
  
    -   <span data-ttu-id="e0054-158">**방법 2**</span><span class="sxs-lookup"><span data-stu-id="e0054-158">**Method 2**</span></span>  
  
         <span data-ttu-id="e0054-159">SSISDB를 만들기 위해 사용된 원래 암호를 갖고 있는 경우 이 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-159">Use this method if you have the original password that was used to create SSISDB.</span></span>  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  <span data-ttu-id="e0054-160">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.check_schema_version [을 실행하여 SSISDB 카탈로그 스키마와](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)바이너리 파일(ISServerExec 및 SQLCLR 어셈블리)이 호환되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-160">Determine whether the SSISDB catalog schema and the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] binaries (ISServerExec and SQLCLR assembly) are compatible, by running [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).</span></span>  
  
9. <span data-ttu-id="e0054-161">SSISDB 데이터베이스가 성공적으로 복원되었는지 확인하려면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포된 패키지를 실행하는 등 SSISDB 카탈로그에 대해 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-161">To confirm that the SSISDB database has been restored successfully, perform operations against the SSISDB catalog such as running packages that have been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e0054-162">자세한 내용은 [SQL Server Management Studio를 사용하여 SSIS 서버에서 패키지 실행](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-162">For more information, see [Run a Package on the SSIS Server Using SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).</span></span>  
  
### <a name="to-move-the-ssis-database"></a><span data-ttu-id="e0054-163">SSIS 데이터베이스를 이동하려면</span><span class="sxs-lookup"><span data-stu-id="e0054-163">To Move the SSIS Database</span></span>  
  
-   <span data-ttu-id="e0054-164">사용자 데이터베이스 이동 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-164">Follow the instructions for moving user databases.</span></span> <span data-ttu-id="e0054-165">자세한 내용은 [Move User Databases](../relational-databases/databases/move-user-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-165">For more information, see [Move User Databases](../relational-databases/databases/move-user-databases.md).</span></span>  
  
     <span data-ttu-id="e0054-166">SSISDB 데이터베이스의 마스터 키를 백업하고 백업 파일을 보호하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0054-166">Ensure that you back up the master key for the SSISDB database and protect the backup file.</span></span> <span data-ttu-id="e0054-167">자세한 내용은 [SSIS 데이터베이스를 백업하려면](#backup)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0054-167">For more information, see [To Back up the SSIS Database](#backup).</span></span>  
  
     <span data-ttu-id="e0054-168">Integration Services(SSIS) 관련 개체가 SSISDB 카탈로그가 아직 만들어지지 않은 새 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0054-168">Ensure that the Integration Services (SSIS) relevant objects are created in the new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance where the SSISDB catalog has not yet been created.</span></span>  
  
  
