---
title: Azure에 대 한 SQL Server Managed Backup 설정 | Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9e3b86fde91028106263310aad8a1952fc041a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659989"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a><span data-ttu-id="d2bd1-102">Azure에 SQL Server 관리 백업 설정</span><span class="sxs-lookup"><span data-stu-id="d2bd1-102">Setting up SQL Server Managed Backup to Azure</span></span>
  <span data-ttu-id="d2bd1-103">이 항목에는 다음 두 자습서가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-103">This topic includes two tutorials:</span></span>  
  
 <span data-ttu-id="d2bd1-104">데이터베이스 수준에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 설정, 전자 메일 알림 설정 및 백업 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="d2bd1-104">Set up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="d2bd1-105">인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 설정, 전자 메일 알림 설정 및 백업 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="d2bd1-105">Setting up  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the instance level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="d2bd1-106">가용성 그룹을 설정 하는 방법에 대 한 자습서는 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] [가용성 그룹에 대 한 Microsoft Azure SQL Server Managed Backup 설정](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-106">For a tutorial on setting up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for Availability Groups, see [Setting up SQL Server Managed Backup to Microsoft Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
## <a name="setting-up-ss_smartbackup"></a><span data-ttu-id="d2bd1-107">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 설정</span><span class="sxs-lookup"><span data-stu-id="d2bd1-107">Setting Up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span></span>  
  
### <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><span data-ttu-id="d2bd1-108">데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="d2bd1-108">Enable and Configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="d2bd1-109">이 자습서는 데이터베이스(TestDB)에 대해 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 설정 및 구성하고 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 상태 모니터링을 설정하는 데 필요한 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-109">This tutorial describes the steps necessary to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a database (TestDB), followed by steps to enable monitoring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="d2bd1-110">**사용 권한:**</span><span class="sxs-lookup"><span data-stu-id="d2bd1-110">**Permissions:**</span></span>  
  
-   <span data-ttu-id="d2bd1-111">**ALTER ANY CREDENTIAL** 권한 및 **db_backupoperator** `EXECUTE` **sp_delete_backuphistory**저장 프로시저에 대 한 권한이 있는 db_backupoperator 데이터베이스 역할의 멤버 자격이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-111">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="d2bd1-112">Smart_admin에 대 한 **SELECT** 권한이 필요 합니다. **fn_get_current_xevent_settings**함수.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-112">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="d2bd1-113">`EXECUTE` **Smart_admin sp_get_backup_diagnostics** 저장 프로시저에 대 한 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-113">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="d2bd1-114">또한 `VIEW SERVER STATE` 권한도 필요한데, 이 권한이 필요한 다른 시스템 개체를 내부적으로 호출하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-114">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="d2bd1-115">`EXECUTE`및 저장 프로시저에 대 한 권한이 필요 `smart_admin.sp_set_instance_backup` `smart_admin.sp_backup_master_switch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-115">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  


1.  <span data-ttu-id="d2bd1-116">**Microsoft Azure 저장소 계정 만들기:** 백업은 Microsoft Azure storage 서비스에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-116">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="d2bd1-117">계정이 아직 없는 경우 먼저 Microsoft Azure storage 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-117">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="d2bd1-118">SQL Server 2014는 블록 및 추가 blob과 다른 페이지 blob을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-118">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="d2bd1-119">따라서 blob 계정이 아닌 범용 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-119">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="d2bd1-120">자세한 내용은 [Azure Storage 계정 정보](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-120">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="d2bd1-121">스토리지 계정 이름 및 액세스 키를 적어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-121">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="d2bd1-122">스토리지 계정 이름 및 액세스 키 정보는 SQL 자격 증명을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-122">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="d2bd1-123">SQL 자격 증명은 스토리지 계정 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-123">The SQL Credential is used to authenticate to the storage account.</span></span>  
 
2.  <span data-ttu-id="d2bd1-124">**SQL 자격 증명 만들기:** 저장소 계정의 이름을 Id로 사용 하 고 저장소 액세스 키를 암호로 사용 하 여 SQL 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-124">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="d2bd1-125">**SQL Server 에이전트 서비스가 시작 되 고 실행 중인지 확인 합니다.**  현재 실행 되 고 있지 않은 경우 SQL Server 에이전트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-125">**Ensure SQL Server Agent service is Started and Running:**  Start SQL Server Agent if it is not currently running.</span></span>  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="d2bd1-126">을 실행하여 백업 작업을 수행하려면 SQL Server 에이전트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-126">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="d2bd1-127">SQL Server 에이전트가 자동으로 실행되어 백업 작업이 정기적으로 발생하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-127">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="d2bd1-128">**보존 기간 결정:** 백업 파일의 보존 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-128">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="d2bd1-129">보존 기간은 일 단위로 지정되며 1-30일의 범위로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-129">The retention period is specified in days and can range from 1 to 30.</span></span>  
  
5.  <span data-ttu-id="d2bd1-130">**설정 및 구성 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** SQL Server Management Studio를 시작 하 고 데이터베이스가 설치 된 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-130">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance where the database is installed.</span></span> <span data-ttu-id="d2bd1-131">요구 사항에 따라 데이터베이스 이름, SQL 자격 증명, 보존 기간 및 암호화 옵션의 값을 수정한 후 쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-131">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="d2bd1-132">암호화에 대 한 인증서를 만드는 방법에 대 한 자세한 내용은 [암호화 된 백업 만들기](create-an-encrypted-backup.md)의 **백업 인증서 만들기** 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-132">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="d2bd1-133">이 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-133">is now enabled on the database you specified.</span></span> <span data-ttu-id="d2bd1-134">데이터베이스에서 백업 작업이 실행을 시작하려면 최대 15분이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-134">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span>  
  
6.  <span data-ttu-id="d2bd1-135">**확장 이벤트 기본 구성 검토:** 다음 Transact-SQL 문을 실행하여 확장 이벤트 설정을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-135">**Review Extended Event Default Configuration:** Review the Extended Event settings by running the following transact-SQL statement.</span></span>  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="d2bd1-136">Admin, Operational 및 Analytical 채널 이벤트가 기본적으로 설정되어 있고 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-136">You should see that Admin, Operational, and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="d2bd1-137">수동 작업이 필요한 이벤트를 모니터링하기에 충분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-137">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="d2bd1-138">디버그 이벤트를 설정할 수 있지만 디버그 채널에는 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 에서 문제를 발견 및 해결하는 데 사용하는 정보와 디버그 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-138">You can enable debug events, but the debug channels include informational and debug events that [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="d2bd1-139">자세한 내용은 [Microsoft Azure에 대 한 관리 되는 백업 SQL Server 모니터링](sql-server-managed-backup-to-microsoft-azure.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-139">For more information, see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
7.  <span data-ttu-id="d2bd1-140">**Health 상태 알림 사용 및 구성:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]에는 주의가 필요할 수 있는 오류나 경고의 메일 알림을 보내는 에이전트 작업을 만드는 저장 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-140">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span> <span data-ttu-id="d2bd1-141">전자 메일 알림을 사용 및 구성하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-141">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="d2bd1-142">인스턴스에 데이터베이스 메일이 설정되지 않은 경우 데이터베이스 메일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-142">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="d2bd1-143">자세한 내용은 [Configure Database Mail](../database-mail/configure-database-mail.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-143">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="d2bd1-144">데이터베이스 메일을 사용하도록 SQL Server 에이전트 알림을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-144">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="d2bd1-145">자세한 내용은 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-145">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="d2bd1-146">**백업 오류 및 경고를 수신하도록 이메일 알림 설정:** 쿼리 창에서 다음 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-146">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         <span data-ttu-id="d2bd1-147">자세한 내용 및 전체 샘플 스크립트는 [Microsoft Azure에 대 한 관리 되는 백업 SQL Server 모니터링](sql-server-managed-backup-to-microsoft-azure.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-147">For more information, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
8.  <span data-ttu-id="d2bd1-148">**Microsoft Azure Storage 계정에서 백업 파일 보기:** SQL Server Management Studio 또는 Azure 관리 Portal에서 스토리지 계정에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-148">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="d2bd1-149">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 사용하도록 구성한 데이터베이스를 호스팅하는 SQL Server 인스턴스에 대한 컨테이너가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-149">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="d2bd1-150">데이터베이스에 대한 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 설정한 후 15분 이내에 데이터베이스 및 로그 백업도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-150">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
9. <span data-ttu-id="d2bd1-151">**상태 모니터링:**  이전에 구성한 메일 알림을 통해 모니터링하거나 기록된 이벤트를 적극적으로 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-151">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="d2bd1-152">다음은 이벤트를 표시하는 데 사용하는 예제 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-152">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="d2bd1-153">이 섹션에서는 데이터베이스에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 을 처음 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-153">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="d2bd1-154">동일한 시스템 저장 프로시저 smart_admin를 사용 하 여 기존 구성을 수정할 수 있습니다 **. sp_set_db_backup** 하 고 새 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-154">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="d2bd1-155">자세한 내용은 [Microsoft Azure SQL Server 관리 되는 백업-보존 및 저장소 설정](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-155">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="enable-ss_smartbackup-for-the-instance-with-default-settings"></a><span data-ttu-id="d2bd1-156">기본 설정을 사용하여 인스턴스에 대한 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 설정</span><span class="sxs-lookup"><span data-stu-id="d2bd1-156">Enable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the Instance with Default Settings</span></span>  
 <span data-ttu-id="d2bd1-157">이 자습서에서는 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ' MyInstance ' 인스턴스를 사용 하도록 설정 하 고 구성 하는 단계를 설명 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="d2bd1-157">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the instance, 'MyInstance',\\.</span></span> <span data-ttu-id="d2bd1-158">여기에는 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 상태 모니터링을 설정하는 단계가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-158">It includes steps to enable monitoring the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="d2bd1-159">**사용 권한:**</span><span class="sxs-lookup"><span data-stu-id="d2bd1-159">**Permissions:**</span></span>  
  
-   <span data-ttu-id="d2bd1-160">**ALTER ANY CREDENTIAL** 권한 및 **db_backupoperator** `EXECUTE` **sp_delete_backuphistory**저장 프로시저에 대 한 권한이 있는 db_backupoperator 데이터베이스 역할의 멤버 자격이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-160">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="d2bd1-161">Smart_admin에 대 한 **SELECT** 권한이 필요 합니다. **fn_get_current_xevent_settings**함수.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-161">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="d2bd1-162">`EXECUTE` **Smart_admin sp_get_backup_diagnostics** 저장 프로시저에 대 한 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-162">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="d2bd1-163">또한 `VIEW SERVER STATE` 권한도 필요한데, 이 권한이 필요한 다른 시스템 개체를 내부적으로 호출하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-163">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  


1.  <span data-ttu-id="d2bd1-164">**Microsoft Azure 저장소 계정 만들기:** 백업은 Microsoft Azure storage 서비스에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-164">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="d2bd1-165">계정이 아직 없는 경우 먼저 Microsoft Azure storage 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-165">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="d2bd1-166">SQL Server 2014는 블록 및 추가 blob과 다른 페이지 blob을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-166">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="d2bd1-167">따라서 blob 계정이 아닌 범용 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-167">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="d2bd1-168">자세한 내용은 [Azure Storage 계정 정보](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-168">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="d2bd1-169">스토리지 계정 이름 및 액세스 키를 적어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-169">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="d2bd1-170">스토리지 계정 이름 및 액세스 키 정보는 SQL 자격 증명을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-170">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="d2bd1-171">SQL 자격 증명은 스토리지 계정 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-171">The SQL Credential is used to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="d2bd1-172">**SQL 자격 증명 만들기:** 저장소 계정의 이름을 Id로 사용 하 고 저장소 액세스 키를 암호로 사용 하 여 SQL 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-172">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="d2bd1-173">**SQL Server 에이전트 서비스가 시작되고 실행 중인지 확인:** 현재 SQL Server 에이전트가 실행되지 않고 있으면 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-173">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="d2bd1-174">을 실행하여 백업 작업을 수행하려면 SQL Server 에이전트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-174">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="d2bd1-175">SQL Server 에이전트가 자동으로 실행되어 백업 작업이 정기적으로 발생하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-175">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="d2bd1-176">**보존 기간 결정:** 백업 파일의 보존 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-176">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="d2bd1-177">보존 기간은 일 단위로 지정되며 1-30일의 범위로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-177">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="d2bd1-178">기본값을 사용하여 인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]이 설정되면 이후 만들어진 모든 새 데이터베이스는 해당 설정을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-178">Once [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is enabled at the instance level with the defaults all new databases created thereafter will inherit the settings.</span></span> <span data-ttu-id="d2bd1-179">전체 또는 대량 로그 복구 모델로 설정된 데이터베이스만 지원되고 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-179">Only databases that are set to full or bulk-logged recovery models are supported and will be configured automatically.</span></span> <span data-ttu-id="d2bd1-180">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 구성을 원하지 않는 경우 언제든지 특정 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-180">You may disable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a specific database at any time if you  do not want [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configured.</span></span> <span data-ttu-id="d2bd1-181">또한 데이터베이스 수준에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 구성하여 특정 데이터베이스에 대한 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-181">You can also change the configuration for a specific database by configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
5.  <span data-ttu-id="d2bd1-182">**설정 및 구성 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** SQL Server Management Studio를 시작 하 고 SQL Server 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-182">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance of SQL Server.</span></span> <span data-ttu-id="d2bd1-183">요구 사항에 따라 데이터베이스 이름, SQL 자격 증명, 보존 기간 및 암호화 옵션의 값을 수정한 후 쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-183">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and the encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="d2bd1-184">암호화에 대 한 인증서를 만드는 방법에 대 한 자세한 내용은 [암호화 된 백업 만들기](create-an-encrypted-backup.md)의 **백업 인증서 만들기** 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-184">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     <span data-ttu-id="d2bd1-185">이제 인스턴스에서 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-185">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is now enabled on the instance.</span></span>  
  
6.  <span data-ttu-id="d2bd1-186">다음 Transact-SQL 문을 실행하여 구성 설정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-186">Verify the configuration settings by running the following Transact-SQL statement:</span></span>  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  <span data-ttu-id="d2bd1-187">인스턴스에 대한 새 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-187">Create a new database on the instance.</span></span> <span data-ttu-id="d2bd1-188">다음 Transact-SQL 문을 실행하여 데이터베이스에 대한 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 구성 설정을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-188">Run the following Transact-SQL statement to view the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration settings for the database:</span></span>  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     <span data-ttu-id="d2bd1-189">설정이 표시되고 데이터베이스에 대한 백업 작업이 실행을 시작하려면 최대 15분이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-189">It may take up to 15 minutes for the settings to show and backup operations on the database to start to run.</span></span>  
  
8.  <span data-ttu-id="d2bd1-190">**Health 상태 알림 사용 및 구성:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]에는 주의가 필요할 수 있는 오류나 경고의 메일 알림을 보내는 에이전트 작업을 만드는 저장 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-190">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="d2bd1-191">이러한 알림을 수신하려면 SQL Server 에이전트 작업을 만드는 저장 프로시저를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-191">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="d2bd1-192">전자 메일 알림을 사용 및 구성하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-192">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="d2bd1-193">인스턴스에 데이터베이스 메일이 설정되지 않은 경우 데이터베이스 메일을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-193">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="d2bd1-194">자세한 내용은 [Configure Database Mail](../database-mail/configure-database-mail.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-194">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="d2bd1-195">데이터베이스 메일을 사용하도록 SQL Server 에이전트 알림을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-195">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="d2bd1-196">자세한 내용은 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-196">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="d2bd1-197">**백업 오류 및 경고를 수신하도록 이메일 알림 설정:** 쿼리 창에서 다음 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-197">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         <span data-ttu-id="d2bd1-198">을 모니터링 하는 방법에 대 한 자세한 내용 및 전체 샘플 스크립트는 [Microsoft Azure에 대 한 관리 되는 백업 SQL Server 모니터링](sql-server-managed-backup-to-microsoft-azure.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-198">For more information about how to monitor, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="d2bd1-199">**Microsoft Azure Storage 계정에서 백업 파일 보기:** SQL Server Management Studio 또는 Azure 관리 Portal에서 스토리지 계정에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-199">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="d2bd1-200">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]을 사용하도록 구성한 데이터베이스를 호스팅하는 SQL Server 인스턴스에 대한 컨테이너가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-200">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="d2bd1-201">새 데이터베이스를 만든 후 15분 이내에 데이터베이스 및 로그 백업도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-201">You may also see a database and a log backup within 15 minutes of creating a new database.</span></span>  
  
10. <span data-ttu-id="d2bd1-202">**상태 모니터링:**  이전에 구성한 메일 알림을 통해 모니터링하거나 기록된 이벤트를 적극적으로 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-202">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="d2bd1-203">다음은 이벤트를 표시하는 데 사용하는 예제 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-203">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="d2bd1-204">데이터베이스 수준에서 설정을 구성하여 특정 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 기본 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-204">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] default settings can be overridden for a specific database by configuring the settings specifically at the database level.</span></span> <span data-ttu-id="d2bd1-205">또한 일시적으로 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 서비스를 일시 중지하고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-205">You can also pause and resume [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] service temporarily.</span></span> <span data-ttu-id="d2bd1-206">자세한 내용은 [Microsoft Azure SQL Server 관리 되는 백업-보존 및 저장소 설정](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2bd1-206">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span></span>  
  
  
