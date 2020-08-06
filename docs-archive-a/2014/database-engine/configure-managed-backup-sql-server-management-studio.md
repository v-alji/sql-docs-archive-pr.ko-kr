---
title: 관리 되는 백업 구성 (SQL Server Management Studio) | Microsoft Docs
description: 관리 되는 백업 대화 상자를 사용 하 여 Azure 기본 설정으로 SQL Server 관리 되는 백업을 구성할 수 있습니다. 고려해 야 할 옵션에 대해 알아봅니다.
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e952ef1102ac67bd0ed9f72d0c201d54b320b5ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639000"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a><span data-ttu-id="38f2e-104">관리되는 백업 구성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="38f2e-104">Configure Managed Backup (SQL Server Management Studio)</span></span>
  <span data-ttu-id="38f2e-105">**관리되는 백업** 대화에서는 인스턴스의 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 기본값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-105">The **Managed Backup** dialog allows you to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] defaults for the instance.</span></span> <span data-ttu-id="38f2e-106">이 항목에서는 이 대화를 사용하여인스턴스에 대한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 기본값을 구성하는 방법과, 이 때 고려해야 할 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-106">This topic describes how to use this dialog to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default settings for the instance and options you must consider when doing so.</span></span> <span data-ttu-id="38f2e-107">인스턴스에 대한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성할 때 이 설정은 이후 생성되는 모든 새 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-107">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for the instance, the settings are applied to any new database created thereafter.</span></span>  
  
 <span data-ttu-id="38f2e-108">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]특정 데이터베이스에 대해을 구성 하려면 [데이터베이스에 대해 Azure에 대 한 관리 되는 백업 SQL Server 사용 및 구성](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-108">If you want to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="38f2e-109">프록시 서버에서 SQL Server Managed Backup이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-109">SQL Server Managed Backup is not supported with proxy servers.</span></span> 
  
## <a name="task-list"></a><span data-ttu-id="38f2e-110">작업 목록</span><span class="sxs-lookup"><span data-stu-id="38f2e-110">Task List</span></span>  
  
## <a name="ss_smartbackup-functions-using-managed-backup-interface-in-sql-server-management-studio"></a><span data-ttu-id="38f2e-111">SQL Server Management Studio에서 관리되는 백업 인터페이스를 사용하는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 함수</span><span class="sxs-lookup"><span data-stu-id="38f2e-111">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Functions Using Managed Backup Interface in SQL Server Management Studio</span></span>  
 <span data-ttu-id="38f2e-112">이 릴리스에서는 **관리 백업** 인터페이스를 사용하여 인스턴스 수준 기본 설정을 구성할 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-112">In this release, you can only configure instance level default settings using the **Management Backup** interface.</span></span> <span data-ttu-id="38f2e-113">데이터베이스용 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성하거나, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 작업을 일시 중지 또는 재개하거나, 이메일 알림을 설정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-113">You cannot configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database, pause or resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations, or setup email notifications.</span></span> <span data-ttu-id="38f2e-114">현재 **Managed backup** 인터페이스를 통해 지원 되지 않는 작업을 수행 하는 방법에 대 한 자세한 내용은 [Azure에 대 한 관리 되는 백업-보존 및 저장소 설정 SQL Server](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-114">For information on how to perform operations not currently supported through the **Managed Backup** interface, see [SQL Server Managed Backup to Azure - Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="38f2e-115">사용 권한</span><span class="sxs-lookup"><span data-stu-id="38f2e-115">Permissions</span></span>  
 <span data-ttu-id="38f2e-116">**SQL Server Management Studio에서 관리되는 백업 노드 보기:\*\*\*\*개체 탐색기** 에서 **관리되는 백업**노드를 보려면 시스템 관리자이거나, 사용자 계정에 다음 특정 권한이 부여되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-116">**View Managed Backup Node is SQL Server Management Studio:** To view  **Managed Backup** node in **Object Explorer**, you must either be a System Admin or have the following permissions specifically granted to your user account:</span></span>  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   <span data-ttu-id="38f2e-117">`EXECUTE`의 `smart_admin.fn_is_master_switch_on`.</span><span class="sxs-lookup"><span data-stu-id="38f2e-117">`EXECUTE` on `smart_admin.fn_is_master_switch_on`.</span></span>  
  
-   <span data-ttu-id="38f2e-118">`SELECT`의 `smart_admin.fn_backup_instance_config`.</span><span class="sxs-lookup"><span data-stu-id="38f2e-118">`SELECT` on `smart_admin.fn_backup_instance_config`.</span></span>  
  
 <span data-ttu-id="38f2e-119">**관리되는 백업을 구성하려면:** SQL Server Management Studio에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 구성하기 위해서는 시스템 관리자이거나 다음 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-119">**To Configure Managed Backup:** to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] in SQL Server Management Studio, you must be a System Administrator or have the following permissions:</span></span>  
  
 <span data-ttu-id="38f2e-120">`db_backupoperator` 데이터베이스 역할의 멤버 자격, `ALTER ANY CREDENTIAL` 사용 권한 및 `sp_delete_backuphistory` 저장 프로시저의 `EXECUTE` 사용 권한.</span><span class="sxs-lookup"><span data-stu-id="38f2e-120">Membership in `db_backupoperator` database role, with `ALTER ANY CREDENTIAL` permissions, and `EXECUTE` permissions on `sp_delete_backuphistory` stored procedure.</span></span>  
  
 <span data-ttu-id="38f2e-121">`smart_admin.fn_get_current_xevent_settings` 함수에 대한 `SELECT` 사용 권한.</span><span class="sxs-lookup"><span data-stu-id="38f2e-121">`SELECT` permissions on the `smart_admin.fn_get_current_xevent_settings` function.</span></span>  
  
 <span data-ttu-id="38f2e-122">`EXECUTE`저장 프로시저에 대 한 사용 권한 `smart_admin.sp_get_backup_diagnostics` .</span><span class="sxs-lookup"><span data-stu-id="38f2e-122">`EXECUTE` permissions on the `smart_admin.sp_get_backup_diagnostics` stored procedure.</span></span> <span data-ttu-id="38f2e-123">또한 `VIEW SERVER STATE` 권한도 필요한데, 이 권한이 필요한 다른 시스템 개체를 내부적으로 호출하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-123">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
 <span data-ttu-id="38f2e-124">`smart_admin.sp_set_instance_backup` 및 `smart_admin.sp_backup_master_switch`에서 `EXECUTE` 권한</span><span class="sxs-lookup"><span data-stu-id="38f2e-124">`EXECUTE` permissions on `smart_admin.sp_set_instance_backup`, and `smart_admin.sp_backup_master_switch`.</span></span>  
  
## <a name="configure-ss_smartbackup-using-sql-server-management-studio"></a><span data-ttu-id="38f2e-125">SQL Server Management Studio를 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 구성</span><span class="sxs-lookup"><span data-stu-id="38f2e-125">Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] using SQL Server Management Studio</span></span>  
 <span data-ttu-id="38f2e-126">**개체 탐색기**에서 **관리** 노드를 확장하고 **관리되는 백업**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-126">From the **object explorer**, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="38f2e-127">**구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-127">Select **Configure**.</span></span> <span data-ttu-id="38f2e-128">**관리되는 백업** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-128">This opens the **Managed Backup** dialog.</span></span>  
  
 <span data-ttu-id="38f2e-129">**관리되는 백업 사용** 옵션을 선택하고 구성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-129">Check **Enable Managed Backup** option and specify the configuration values:</span></span>  
  
 <span data-ttu-id="38f2e-130">**파일 보존** 기간은 일 단위로 지정하며 범위는 1~30입니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-130">The **File retention** period is specified in days and should be between 1 and 30.</span></span>  
  
 <span data-ttu-id="38f2e-131">선택한 **SQL 자격 증명** 은 스토리지 계정과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-131">The **SQL Credential** you select should match the storage account.</span></span> <span data-ttu-id="38f2e-132">현재 인증 정보를 저장하는 SQL 자격 증명이 없는 경우 **만들기**를 클릭하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-132">If you currently do not have a SQL Credential that stores the authentication information, you can create one by clicking **Create**.</span></span> <span data-ttu-id="38f2e-133">또한 CREATE CREDENTIAL Transact-SQL 문을 사용해서 자격 증명을 만들고 SECRET 매개 변수의 ID와 액세스 키에 대해 스토리지 계정 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-133">You can also create credential by using the CREATE CREDENTIAL Transact-SQL statement, and provide the storage account name for Identity and the access key for the SECRET parameters.</span></span> <span data-ttu-id="38f2e-134">자세한 내용은 [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-134">For more information, see [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).</span></span>  
  
 <span data-ttu-id="38f2e-135">Azure storage 계정에 대 한 **저장소 URL** , 저장소 계정에 대 한 인증 정보를 저장 하는 SQL 자격 증명과 백업 파일의 보존 기간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-135">Specify the **Storage URL** for the Azure storage account, the SQL Credential that stores the authentication information for the storage account, and the retention period for the backup files.</span></span>  
  
 <span data-ttu-id="38f2e-136">저장소 URL 형식은 다음과 같습니다. https:// \<StorageAccount> . blob.core.windows.net/</span><span class="sxs-lookup"><span data-stu-id="38f2e-136">The storage URL format is: https://\<StorageAccount>.blob.core.windows.net/</span></span>  
  
 <span data-ttu-id="38f2e-137">인스턴스 수준에서 암호화 설정을 지정하려면 **암호화 백업** 옵션을 선택하고 암호화에 사용할 알고리즘 및 인증서 또는 비대칭 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-137">To set the encryption settings at the instance level, check **Encrypt Backup** option, and specify the algorithm and a Certificate or Asymmetric Key to use for the encryption.</span></span>  <span data-ttu-id="38f2e-138">이 항목은 인스턴스 수준에서 설정되어 이 구성 적용 후 생성되는 모든 새 데이터베이스에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-138">This is set at the instance level is used for all the new databases created once this configuration has been applied.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="38f2e-139">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]구성 없이 이 대화 상자를 사용하여 암호화 옵션을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-139">This dialog cannot be used to specify the encryption options without configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="38f2e-140">이러한 암호화 옵션은 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 작업에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-140">These encryption options only apply to [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations.</span></span> <span data-ttu-id="38f2e-141">다른 백업 절차에 암호화를 사용하려면 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-141">To use encryption for other backup procedures, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
### <a name="considerations"></a><span data-ttu-id="38f2e-142">고려 사항</span><span class="sxs-lookup"><span data-stu-id="38f2e-142">Considerations</span></span>  
 <span data-ttu-id="38f2e-143">인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성할 경우 이후 생성되는 모든 새 데이터베이스에 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-143">If you configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level, the settings are applied to any new database created thereafter.</span></span>  <span data-ttu-id="38f2e-144">그러나 기존 데이터베이스가 자동으로 이 설정을 상속하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-144">However, existing database will not automatically inherit these settings.</span></span> <span data-ttu-id="38f2e-145">기존 데이터베이스에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성하려면 각 데이터베이스를 특정하게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-145">To configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on previously existing databases, you must configure each database specifically.</span></span> <span data-ttu-id="38f2e-146">자세한 내용은 [Azure에 대 한 데이터베이스에 대해 관리 되는 백업 SQL Server 사용 및 구성](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-146">For more information, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
  
 <span data-ttu-id="38f2e-147">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 사용 하 여가 일시 중지 된 경우 `smart_admin.sp_backup_master_switch` "관리 되는 백업이 비활성화 되었으며 현재 구성이 적용 되지 않습니다 ..." 라는 경고 메시지가 표시 됩니다. 구성을 완료 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-147">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has been paused using the `smart_admin.sp_backup_master_switch`, you will see a warning message " Managed Backup is disabled and the current configurations will not take effect..." when you try to complete the configuration.</span></span> <span data-ttu-id="38f2e-148">저장 된를 사용 `smart_admin.sp_backup_master_switch` 하 고 @new_state = 1을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-148">Use the `smart_admin.sp_backup_master_switch` stored and set the @new_state=1.</span></span> <span data-ttu-id="38f2e-149">그러면 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스가 재개되고 구성 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-149">This will resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services and the configuration settings will take into effect.</span></span> <span data-ttu-id="38f2e-150">저장 프로시저에 대 한 자세한 내용은 [smart_admin sp_ backup_master_switch &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-150">For more information on the stored procedure, see [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f2e-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38f2e-151">See Also</span></span>  
 [<span data-ttu-id="38f2e-152">Azure에 SQL Server 관리 백업: 상호 운용성 및 공존성</span><span class="sxs-lookup"><span data-stu-id="38f2e-152">SQL Server Managed Backup to Azure: Interoperability and Coexistence</span></span>](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
