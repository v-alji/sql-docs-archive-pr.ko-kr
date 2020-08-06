---
title: Azure에 대 한 관리 되는 백업 SQL Server-보존 및 저장소 설정 | Microsoft Docs
description: 이 항목에서는 데이터베이스에 대해 Microsoft Azure SQL Server 관리 되는 백업을 구성 하 고 인스턴스에 대 한 기본 설정을 구성 하는 방법에 대해 설명 합니다.
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ebdb81f8aa9edb9cd9326bcb1d286d5d3fe632c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736742"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a><span data-ttu-id="d9b0c-103">Azure에 SQL Server 관리 백업 - 보존 및 스토리지 설정</span><span class="sxs-lookup"><span data-stu-id="d9b0c-103">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>
  <span data-ttu-id="d9b0c-104">이 항목에서는 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성하고 인스턴스에 대한 기본 설정을 구성하는 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-104">This topic describes the basic steps to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database and to configure default settings for the instance.</span></span> <span data-ttu-id="d9b0c-105">이 항목에서는 인스턴스에 대한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스를 일시 중지하고 다시 시작하는 데 필요한 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-105">The topic also describes the steps necessary to pause and resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for the instance.</span></span>  
  
 <span data-ttu-id="d9b0c-106">설정에 대 한 전체 연습은 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] [azure에 대 한 관리 되는 백업 SQL Server 설정](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) 및 [가용성 그룹에 대 한 Azure로 관리 되는 백업 SQL Server 설정](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-106">For a complete walkthrough of setting up [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] see [Setting up SQL Server Managed Backup to Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d9b0c-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d9b0c-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d9b0c-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d9b0c-108">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d9b0c-109">현재 유지 관리 계획 또는 로그 전달을 사용하는 데이터베이스에서는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-109">Do not enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on databases that are currently using maintenance plans or log shipping.</span></span> <span data-ttu-id="d9b0c-110">다른 SQL Server 기능과의 상호 운용성 및 공존 성에 대 한 자세한 내용은 [Azure에 대 한 Managed Backup SQL Server: 상호 운용성 및 공존 성](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-110">For more information on interoperability and coexistence with other SQL Server features, see [SQL Server Managed Backup to Azure: Interoperability and Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d9b0c-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d9b0c-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="d9b0c-112">SQL Server 에이전트가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-112">SQL Server Agent should be running.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="d9b0c-113">SQL Server 에이전트가 일정 기간 동안 중지되었다가 다시 시작되면 SQL 에이전트가 중지된 후부터 시작될 때까지 경과된 시간에 따라 백업 작업이 증가할 수 있으며 실행 대기 중인 로그 백업의 백로그가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-113">If SQL Server Agent is stopped for a period of time and then restarted, you may see an increased backup activity depending on the length of time elapsed between the stop and start of SQL Agent, and there might be a backlog of log backups waiting to run.</span></span> <span data-ttu-id="d9b0c-114">시작 시 SQL Server 에이전트가 자동으로 시작되도록 구성해 보세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-114">Consider configuring SQL Server Agent to start automatically on start up.</span></span>  
  
-   <span data-ttu-id="d9b0c-115">를 구성 하기 전에 저장소 계정에 인증 정보를 저장 하는 Azure storage 계정 및 SQL 자격 증명을 모두 만들어야 합니다 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d9b0c-115">A Azure storage account and a SQL Credential that stores the authentication information to the storage account should both be created before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="d9b0c-116">자세한 내용은 [URL에 대한 SQL Server 백업](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) 항목의 **Introduction to Key Components and Concepts** 섹션과 [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-116">For more information see [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) section of the **SQL Server Backup to URL** topic, and [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="d9b0c-117">은 백업을 저장하는 데 필요한 컨테이너를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-117">creates the necessary containers to store the backups.</span></span> <span data-ttu-id="d9b0c-118">컨테이너 이름은 ' machine name-instance name ' 형식을 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-118">The container name is created using 'machine name-instance name' format.</span></span> <span data-ttu-id="d9b0c-119">AlwaysOn 가용성 그룹의 경우 컨테이너의 이름은 가용성 그룹의 GUID를 사용하여 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-119">For AlwaysOn Availability Groups the container is named using the GUID of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d9b0c-120">보안</span><span class="sxs-lookup"><span data-stu-id="d9b0c-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d9b0c-121">권한</span><span class="sxs-lookup"><span data-stu-id="d9b0c-121">Permissions</span></span>  
 <span data-ttu-id="d9b0c-122">에서 사용 하는 저장 프로시저를 실행 하려면 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] `System Administrator` **ALTER ANY CREDENTIAL** 권한이 있는 **db_backupoperator** 데이터베이스 역할의 또는 멤버와 `EXECUTE` **sp_delete_backuphistory**및 저장 프로시저에 대 한 권한이 있어야 합니다 `smart_admin.sp_backup_master_switch` .</span><span class="sxs-lookup"><span data-stu-id="d9b0c-122">To run the stored procedures that enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], you must be a  either a `System Administrator` or  member  in the **db_backupoperator** database role with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on the **sp_delete_backuphistory**, and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  <span data-ttu-id="d9b0c-123">일반적으로 기존 설정을 검토하는 데 사용되는 저장 프로시저 및 함수는 저장 프로시저에 대한 `Execute` 권한과 함수에 대한 `Select` 권한이 각각 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-123">Stored procedures and functions used to review the existing settings typically require `Execute` permissions on the stored procedure and `Select` on the function respectively.</span></span>  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a><span data-ttu-id="d9b0c-124">데이터베이스 및 인스턴스에 대 한 사용 시 고려 사항 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b0c-124">Considerations for enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Databases and Instances</span></span>  
 <span data-ttu-id="d9b0c-125">개별 데이터베이스에 대해 별도로 또는 전체 인스턴스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-125">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] can be enabled for individual databases separately or for the entire instance.</span></span> <span data-ttu-id="d9b0c-126">선택 항목은 인스턴스의 데이터베이스에 대 한 복구 가능성 요구 사항, 여러 데이터베이스 및 인스턴스를 관리 하기 위한 요구 사항, Azure storage를 전략적으로 사용 하기 위한 요구 사항에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-126">The choices depend on the recoverability requirements for the databases on the instance, requirements for managing multiple databases and instances, and using Azure storage strategically.</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a><span data-ttu-id="d9b0c-127">데이터베이스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 설정</span><span class="sxs-lookup"><span data-stu-id="d9b0c-127">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Database Level</span></span>  
 <span data-ttu-id="d9b0c-128">데이터베이스에 인스턴스의 다른 데이터베이스와 다른 백업 및 보존 기간에 대한 특정 요구 사항(복구 기능 SLA)이 있는 경우 이 데이터베이스에 대해 데이터베이스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-128">If a database has specific requirements for backup and retention period (recoverability SLA) that is different from other databases on the instance, configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level for this database.</span></span> <span data-ttu-id="d9b0c-129">데이터베이스 수준 설정은 인스턴스 수준 구성 설정보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-129">Database level settings override instance level configuration settings.</span></span> <span data-ttu-id="d9b0c-130">그러나 이러한 두 옵션을 동일한 인스턴스에서 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-130">However both these options can be used together on the same instance.</span></span> <span data-ttu-id="d9b0c-131">다음은 데이터베이스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 설정할 때의 이점 및 고려 사항 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-131">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
-   <span data-ttu-id="d9b0c-132">세분성: 각 데이터베이스의 구성 설정을 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-132">More granular: Separate configuration settings for each database.</span></span> <span data-ttu-id="d9b0c-133">개별 데이터베이스에 대해 서로 다른 보존 기간을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-133">Can support different retention periods for individual databases.</span></span>  
  
-   <span data-ttu-id="d9b0c-134">데이터베이스에 대해 인스턴스 수준 설정을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-134">Overrides instance level settings for the database.</span></span>  
  
-   <span data-ttu-id="d9b0c-135">백업할 개별 데이터베이스를 선택하여 스토리지 비용을 줄이는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-135">Can be used to reduce storage costs by selecting individual databases to be backed up.</span></span>  
  
-   <span data-ttu-id="d9b0c-136">각 데이터베이스 관리를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-136">Requires managing each database</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a><span data-ttu-id="d9b0c-137">기본 설정을 사용하여 인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 설정</span><span class="sxs-lookup"><span data-stu-id="d9b0c-137">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level with Default Settings</span></span>  
 <span data-ttu-id="d9b0c-138">인스턴스에 있는 대부분의 데이터베이스에 대한 백업 및 보존 정책 요구 사항이 동일한 경우 또는 새 데이터베이스 인스턴스를 생성 시 자동으로 백업할 경우 이 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-138">Use this setting if most of the databases in the instance have the same requirements for backup and retention policies, or if you want new database instances to automatically be backed up on creation.</span></span> <span data-ttu-id="d9b0c-139">정책에 예외인 몇 개의 데이터베이스를 개별적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-139">A few databases that are exception to the policy can still be configured individually.</span></span> <span data-ttu-id="d9b0c-140">다음은 인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 설정할 때의 이점 및 고려 사항 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-140">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level.</span></span>  
  
-   <span data-ttu-id="d9b0c-141">인스턴스 수준의 자동화: 이후에 추가된 새 데이터베이스에 대해 자동으로 적용되는 공통 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-141">Automation at the instance level: Common settings applied to automatically for new databases added thereafter.</span></span>  
  
-   <span data-ttu-id="d9b0c-142">새 데이터베이스는 인스턴스에서 생성되자마자 자동으로 백업됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-142">New databases will be automatically backed up soon after they are created on the instances</span></span>  
  
-   <span data-ttu-id="d9b0c-143">보존 기간 요구 사항이 동일한 데이터베이스에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-143">Can be applied to databases that have the same retention period requirements.</span></span>  
  
-   <span data-ttu-id="d9b0c-144">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 기본 설정을 사용하여 인스턴스 수준에서 설정된 경우에도 다른 보존 기간이 필요한 개별 데이터베이스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-144">You can still configure individual databases that require a different retention period even with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] backup enabled at in instance level with default settings.</span></span> <span data-ttu-id="d9b0c-145">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]백업을 위해 Azure storage를 사용 하지 않으려는 경우에는 데이터베이스에 대해 사용 하지 않도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-145">You can also disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases if you do not intend to use Azure storage for the backups.</span></span>  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a><span data-ttu-id="d9b0c-146">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]데이터베이스에 대해 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="d9b0c-146">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="d9b0c-147">시스템 저장 프로시저 `smart_admin.sp_set_db_backup`은 특정 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-147">The system stored procedure `smart_admin.sp_set_db_backup` is used to enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database.</span></span> <span data-ttu-id="d9b0c-148">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 데이터베이스에서 처음으로 설정될 때 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 설정하는 것 외에도 다음 정보를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-148">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time on the database, the following information must be specified in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:</span></span>  
  
-   <span data-ttu-id="d9b0c-149">데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-149">The name of the database.</span></span>  
  
-   <span data-ttu-id="d9b0c-150">보존 기간</span><span class="sxs-lookup"><span data-stu-id="d9b0c-150">The retention period.</span></span>  
  
-   <span data-ttu-id="d9b0c-151">Azure 저장소 계정에 인증 하는 데 사용 되는 SQL 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-151">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="d9b0c-152">\* \@ Encryption_algorithm\*NO_ENCRYPTION를 사용 하 여 암호화 하지 않도록 지정  =  **NO_ENCRYPTION** 하거나 지원 되는 암호화 알고리즘을 지정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-152">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="d9b0c-153">암호화에 대한 자세한 내용은 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-153">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="d9b0c-154">데이터베이스 수준 구성에 대한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 Transact-SQL을 통해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-154">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for database level configuration is only supported through Transact-SQL.</span></span>  
  
 <span data-ttu-id="d9b0c-155">데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 설정되면 이 정보가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-155">Once [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for a database this information is persisted.</span></span> <span data-ttu-id="d9b0c-156">구성을 변경하는 경우 데이터베이스 이름과 변경하려는 설정만 필요합니다. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 은 지정되지 않은 경우 다른 매개 변수의 기존 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-156">If you are changing the configuration, only the database name and the setting you want to change is required, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values for other parameters when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9b0c-157">데이터베이스에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성하기 전에 기존 구성(있는 경우)을 사용하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-157">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on a database it might be useful to existing configuration if any.</span></span> <span data-ttu-id="d9b0c-158">데이터베이스에 대한 구성 설정을 검토하는 단계는 이 섹션의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-158">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
-   <span data-ttu-id="d9b0c-159">**Transact-sql 사용:**</span><span class="sxs-lookup"><span data-stu-id="d9b0c-159">**Using Transact-SQL:**</span></span>  
  
     <span data-ttu-id="d9b0c-160">을 처음으로 설정 하는 경우 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 필수 매개 변수는 \* \@ database_name*, \* \@ credential_name*, \* \@ encryption_algorithm*, \* \@ enable_backup* \* \@ storage_url\* 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-160">If you are enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time, the required parameters are: *\@database_name*, *\@credential_name*, *\@encryption_algorithm*,  *\@enable_backup* The *\@storage_url* parameter is optional.</span></span> <span data-ttu-id="d9b0c-161">매개 변수에 대 한 값을 제공 하지 않으면 @storage_url SQL 자격 증명의 저장소 계정 정보를 사용 하 여 값이 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-161">If you do not provide a value for  the @storage_url parameter, the value is derived using the storage account information from the SQL Credential.</span></span> <span data-ttu-id="d9b0c-162">스토리지 URL을 제공하는 경우 스토리지 계정의 루트에 대한 URL만 제공해야 하고 지정한 SQL 자격 증명의 정보와 일치시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-162">If you provide the storage URL you should only provide the URL for the root of the storage account, and must match the information in the SQL Credential you specified.</span></span>  
  
    1.  <span data-ttu-id="d9b0c-163">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-163">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
    2.  <span data-ttu-id="d9b0c-164">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-164">From the Standard bar, click **New Query**.</span></span>  
  
    3.  <span data-ttu-id="d9b0c-165">다음 예를 복사 하 여 쿼리 창에 붙여 넣고를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-165">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="d9b0c-166">이 예에서는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ' TestDB ' 데이터베이스에 대해를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-166">This example enables [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database 'TestDB'.</span></span> <span data-ttu-id="d9b0c-167">보존 기간은 30일로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-167">The retention period is set to 30 days.</span></span> <span data-ttu-id="d9b0c-168">이 예제에서는 암호화 알고리즘 및 암호기 정보를 지정하여 암호화 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-168">This sample uses the encryption option by specifying the encryption algorithm and the encryptor information.</span></span>  
  
    ```sql
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d9b0c-169">보존 기간은 1일에서 30일 사이의 값으로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-169">The retention period can be set to any value from 1 to 30 days.</span></span>  
    >   
    >  <span data-ttu-id="d9b0c-170">암호화용 인증서 만들기에 대한 자세한 내용은 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)의 백업 인증서 만들기 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-170">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
     <span data-ttu-id="d9b0c-171">이 저장 프로시저에 대 한 자세한 내용은 [smart_admin set_db_backup &#40;transact-sql을 참조 하세요&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="d9b0c-171">For more information on this stored procedure, see [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span></span>  
  
     <span data-ttu-id="d9b0c-172">데이터베이스에 대한 구성 설정을 검토하려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-172">To review the configuration settings for a database use the following query:</span></span>  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a><span data-ttu-id="d9b0c-173">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]인스턴스에 대 한 기본 설정 사용 및 구성</span><span class="sxs-lookup"><span data-stu-id="d9b0c-173">Enable and Configure Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="d9b0c-174">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]시스템 저장 프로시저 `smart_admin.set_instance_backup` 또는 **SQL Server Management Studio**를 사용 하 여 인스턴스 수준에서 기본 설정을 사용 하도록 설정 하 고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-174">You can enable and configure default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings at the instance level in two ways:  By using the system stored procedure `smart_admin.set_instance_backup` or **SQL Server Management Studio**.</span></span> <span data-ttu-id="d9b0c-175">두 가지 방법이 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-175">The two methods are explained below:</span></span>  
  
 <span data-ttu-id="d9b0c-176">**smart_admin. set_instance_backup:**.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-176">**smart_admin.set_instance_backup:**.</span></span> <span data-ttu-id="d9b0c-177">\* \@ Enable_backup\* 매개 변수에 값 **1** 을 지정 하 여 백업을 사용 하도록 설정 하 고 기본 구성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-177">By specifying the value **1** for *\@enable_backup* parameter, you can enable backup and set the default configurations.</span></span> <span data-ttu-id="d9b0c-178">이러한 기본 설정은 인스턴스 수준에서 적용되면 이 인스턴스에 추가된 모든 새 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-178">Once applied at the instance level, these default settings are applied to any new database that is added to this instance.</span></span>  <span data-ttu-id="d9b0c-179">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 처음으로 설정될 때 인스턴스에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 설정하는 것 외에도 다음 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-179">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time, the following information must be provided in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on the instance:</span></span>  
  
-   <span data-ttu-id="d9b0c-180">보존 기간</span><span class="sxs-lookup"><span data-stu-id="d9b0c-180">The retention period.</span></span>  
  
-   <span data-ttu-id="d9b0c-181">Azure 저장소 계정에 인증 하는 데 사용 되는 SQL 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-181">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="d9b0c-182">암호화 옵션.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-182">The encryption option.</span></span> <span data-ttu-id="d9b0c-183">\* \@ Encryption_algorithm\*NO_ENCRYPTION를 사용 하 여 암호화 하지 않도록 지정  =  **NO_ENCRYPTION** 하거나 지원 되는 암호화 알고리즘을 지정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-183">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="d9b0c-184">암호화에 대한 자세한 내용은 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-184">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="d9b0c-185">이러한 설정은 설정되면 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-185">Once enabled these settings are persisted.</span></span> <span data-ttu-id="d9b0c-186">구성을 변경하는 경우 데이터베이스 이름과 변경하려는 설정만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-186">If you are changing the configuration, only the database name and the setting you want to change is required.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="d9b0c-187">은 지정되지 않은 경우 기존 값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-187">retains the existing values when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9b0c-188">인스턴스에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 구성하기 전에 기존 구성(있는 경우)을 확인하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-188">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on an instance, it might be useful to check for existing configuration, if any.</span></span> <span data-ttu-id="d9b0c-189">데이터베이스에 대한 구성 설정을 검토하는 단계는 이 섹션의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-189">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
 <span data-ttu-id="d9b0c-190">**SQL Server Management Studio:** SQL Server Management Studio에서 이 태스크를 수행하려면 개체 탐색기로 이동하여 **관리** 노드를 확장하고 **관리되는 백업**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-190">**SQL Server Management Studio:** To do this task in SQL Server Management Studio, go the object explorer, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="d9b0c-191">**구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-191">Select **Configure**.</span></span> <span data-ttu-id="d9b0c-192">**관리되는 백업** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-192">This opens the **Managed Backup** dialog.</span></span> <span data-ttu-id="d9b0c-193">이 대화 상자를 사용하여 보존 기간, SQL 자격 증명, 스토리지 URL 및 암호화 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-193">Use this dialog to specify the retention period, SQL Credential, Storage URL, and the encryption settings.</span></span> <span data-ttu-id="d9b0c-194">이 대화 상자에 대 한 특정 도움말은 [관리 되는 백업 &#40;구성 SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-194">For specific help with this dialog, see [Configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).</span></span>  
  
#### <a name="using-transact-sql"></a><span data-ttu-id="d9b0c-195">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d9b0c-195">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="d9b0c-196">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-196">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-197">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-197">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-198">다음 예를 복사 하 여 쿼리 창에 붙여 넣고를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-198">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9b0c-199">보존 기간은 1일에서 30일 사이의 값으로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-199">The retention period can be set to any value from 1 to 30 days.</span></span>  
>   
>  <span data-ttu-id="d9b0c-200">암호화용 인증서 만들기에 대한 자세한 내용은 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)의 백업 인증서 만들기 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-200">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
 <span data-ttu-id="d9b0c-201">인스턴스에 대한 기본 구성 설정을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-201">To view the default configuration settings for the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a><span data-ttu-id="d9b0c-202">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="d9b0c-202">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="d9b0c-203">PowerShell 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-203">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="d9b0c-204">다음 스크립트를 설정에 맞게 수정한 후 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-204">Run the following script after modifying it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9b0c-205">기본 설정을 구성한 후 새 데이터베이스를 만들면 기본 설정으로 데이터베이스가 구성되는 데 최대 15분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-205">When you create a new database after configuring the default settings, it may take up to 15 minutes for the database to be configured with the default settings.</span></span> <span data-ttu-id="d9b0c-206">이는 **Simple** 에서 **Full** 또는 **Bulk-Logged** 복구 모델로 변경되는 데이터베이스에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-206">This also applies to databases that are changed from **Simple** to **Full** or **Bulk-Logged** recovery model.</span></span>  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> <span data-ttu-id="d9b0c-207">데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 해제</span><span class="sxs-lookup"><span data-stu-id="d9b0c-207">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database</span></span>  
 <span data-ttu-id="d9b0c-208">`sp_set_db_backup` 시스템 저장 프로시저를 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 설정을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-208">You can disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings by using the `sp_set_db_backup` system stored procedure.</span></span> <span data-ttu-id="d9b0c-209">\* \@ Enableparameter\* 는 특정 데이터베이스에 대 한 구성을 활성화 하거나 비활성화 하는 데 사용 됩니다 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] . 여기서 1은 구성 설정을 설정 하 고 0은 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-209">The *\@enableparameter* is used to enable and disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for a specific database, where 1 enables and 0 disables the configuration settings.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a><span data-ttu-id="d9b0c-210">특정 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-210">To Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database:</span></span>  
  
1.  <span data-ttu-id="d9b0c-211">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-211">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-212">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-212">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-213">다음 예를 복사 하 여 쿼리 창에 붙여 넣고를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-213">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> <span data-ttu-id="d9b0c-214">인스턴스의 모든 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 해제</span><span class="sxs-lookup"><span data-stu-id="d9b0c-214">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for all the databases on the Instance</span></span>  
 <span data-ttu-id="d9b0c-215">다음 절차는 인스턴스에서 현재 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 설정되어 있는 모든 데이터베이스의 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 구성 설정을 해제하려는 경우에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-215">The following procedure is for when you want to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings from all the databases that currently have [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled on the instance.</span></span>  <span data-ttu-id="d9b0c-216">스토리지 URL, 보존 및 SQL 자격 증명과 같은 구성 설정은 메타데이터에 남아 있으며 나중에 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 설정되는 경우 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-216">The configuration settings like the storage URL, retention, and the SQL Credential will remain in the metadata and can be used  if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the database at a later time.</span></span> <span data-ttu-id="d9b0c-217">일시적으로 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스를 일시 중지하는 경우 이 항목의 뒷부분에 나오는 다음 섹션에서 설명하는 마스터 스위치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-217">If you want to just pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services temporarily, you can use the master switch explained in the following sections later in this topic.</span></span>  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a><span data-ttu-id="d9b0c-218">모든 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-218">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]for all the databases:</span></span>  
  
1.  <span data-ttu-id="d9b0c-219">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-219">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-220">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-220">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-221">다음 예를 복사 하 여 쿼리 창에 붙여 넣고를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-221">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="d9b0c-222">다음 예에서는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 인스턴스 수준에서 구성되어 있는지 여부와 인스턴스에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 설정된 모든 데이터베이스를 식별하고 시스템 저장 프로시저 `sp_set_db_backup`을 실행하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-222">The following example identifies if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured at the instance level and all the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled databases on the instance, and executes the system stored procedure `sp_set_db_backup` to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span>  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END
```  
  
 <span data-ttu-id="d9b0c-223">인스턴스의 모든 데이터베이스에 대한 구성 설정을 보려면 다음 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-223">To review the configuration settings for all the databases on the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> <span data-ttu-id="d9b0c-224">인스턴스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 기본 설정 해제</span><span class="sxs-lookup"><span data-stu-id="d9b0c-224">Disable Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="d9b0c-225">인스턴스 수준의 기본 설정은 해당 인스턴스에 대해 만든 모든 새 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-225">Default settings at the instance level apply to all new databases created on that instance.</span></span>  <span data-ttu-id="d9b0c-226">더 이상 기본 설정이 필요하지 않는 경우 **smart_admin.sp_set_instance_backup** 시스템 저장 프로시저를 사용하여 이 구성을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-226">If you no longer need or require default settings, you can disable this configuration by using the **smart_admin.sp_set_instance_backup** System stored procedure.</span></span> <span data-ttu-id="d9b0c-227">해제하는 경우 스토리지 URL, 보존 설정, SQL 자격 증명 이름 등의 다른 구성 설정이 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-227">Disabling does not remove the other configuration settings like the storage URL, retention setting, or the SQL Credential name.</span></span> <span data-ttu-id="d9b0c-228">이러한 설정은 나중에 인스턴스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 이 설정되면 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-228">These settings will be used if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the instance at a later time.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a><span data-ttu-id="d9b0c-229">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 기본 구성 설정을 해제하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-229">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default configuration settings:</span></span>  
  
1.  <span data-ttu-id="d9b0c-230">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-230">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-231">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-231">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-232">다음 예를 복사 하 여 쿼리 창에 붙여 넣고를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-232">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a><span data-ttu-id="d9b0c-233">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="d9b0c-233">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="d9b0c-234">PowerShell 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-234">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="d9b0c-235">다음 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-235">Run the following script:</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> <span data-ttu-id="d9b0c-236">인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 일시 중지</span><span class="sxs-lookup"><span data-stu-id="d9b0c-236">Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level</span></span>  
 <span data-ttu-id="d9b0c-237">짧은 시간 동안 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스를 일시 중지해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-237">There might be times when you need to temporarily pause the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for a short period time.</span></span>  <span data-ttu-id="d9b0c-238">`smart_admin.sp_backup_master_switch` 시스템 저장 프로시저를 사용하여 인스턴스 수준에서 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-238">The `smart_admin.sp_backup_master_switch` system stored procedure allows you to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] service at the instance level.</span></span>  <span data-ttu-id="d9b0c-239">동일한 저장 프로시저를 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-239">The same stored procedure is used to resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="d9b0c-240">@state 매개 변수는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 설정해야 할지 해제해야 할지를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-240">The @state parameter is used to define whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] should be turned off or on.</span></span>  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a><span data-ttu-id="d9b0c-241">Transact-SQL을 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 서비스를 일시 중지하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-241">To Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Services Using Transact-SQL:</span></span>  
  
1.  <span data-ttu-id="d9b0c-242">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-242">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-243">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-243">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-244">다음 예를 복사 하 여 쿼리 창에 붙여 넣은 후 다음을 클릭 합니다.`Execute`</span><span class="sxs-lookup"><span data-stu-id="d9b0c-244">Copy and paste the following example into the query window and then click `Execute`</span></span>  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a><span data-ttu-id="d9b0c-245">PowerShell을 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 일시 중지하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-245">To pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="d9b0c-246">PowerShell 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-246">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="d9b0c-247">다음 스크립트를 설정에 맞게 수정한 후 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-247">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a><span data-ttu-id="d9b0c-248">Transact-SQL을 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-248">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="d9b0c-249">[!INCLUDE[ssDE](../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-249">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9b0c-250">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-250">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d9b0c-251">다음 예를 복사 하 여 쿼리 창에 붙여 넣은 후를 클릭 `Execute` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-251">Copy and paste the following example into the query window and then click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a><span data-ttu-id="d9b0c-252">PowerShell을 사용하여 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 을 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="d9b0c-252">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="d9b0c-253">PowerShell 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-253">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="d9b0c-254">다음 스크립트를 설정에 맞게 수정한 후 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-254">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
