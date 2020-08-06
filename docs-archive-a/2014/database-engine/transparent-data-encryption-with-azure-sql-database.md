---
title: Azure SQL Database를 사용한 투명한 데이터 암호화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6af7c52741b85a2733b93c2b1ed8c03a14dd6343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651237"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a><span data-ttu-id="0097a-102">Azure SQL 데이터베이스를 사용한 투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="0097a-102">Transparent Data Encryption with Azure SQL Database</span></span>
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="0097a-103">투명한 데이터 암호화(미리 보기)는 애플리케이션을 변경할 필요 없이 사용하지 않는 데이터베이스, 연결된 백업 및 트랜잭션 로그 파일에 대한 실시간 암호화 및 암호 해독을 수행하여 악의적인 활동의 위협으로부터 보호하도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-103">transparent data encryption (preview) helps protect against the threat of malicious activity by performing real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application.</span></span>

 <span data-ttu-id="0097a-104">TDE는 데이터베이스 암호화 키라는 대칭 키를 사용하여 전체 데이터베이스의 스토리지를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="0097a-105">[!INCLUDE[ssSDS](../includes/sssds-md.md)] 에서 데이터베이스 암호화 키는 기본 제공 서버 인증서로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-105">In [!INCLUDE[ssSDS](../includes/sssds-md.md)] the database encryption key is protected by a built-in server certificate.</span></span> <span data-ttu-id="0097a-106">기본 제공 서버 인증서는 각 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 서버에 대해 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-106">The built-in server certificate is unique for each [!INCLUDE[ssSDS](../includes/sssds-md.md)] server.</span></span> <span data-ttu-id="0097a-107">GeoDR 관계에 있는 데이터베이스는 각 서버에서 다른 키로 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-107">If a database is in a GeoDR relationship, it is protected by a different key on each server.</span></span> <span data-ttu-id="0097a-108">두 개의 데이터베이스가 동일한 서버에 연결된 경우에는 동일한 기본 제공 인증서를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-108">If 2 databases are connected to the same server, they share the same built-in certificate.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="0097a-109">는 적어도 90일마다 이러한 인증서를 자동으로 회전시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-109">automatically rotates these certificates at least every 90 days.</span></span> <span data-ttu-id="0097a-110">TDE에 대한 일반적인 설명은 [투명한 데이터 암호화&#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0097a-110">For a general description of TDE, see [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).</span></span>

 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] <span data-ttu-id="0097a-111">는 TDE와의 Azure 주요 자격 증명 모음 통합을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-111">does not support Azure Key Vault integration with TDE.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="0097a-112">에서는 주요 자격 증명 모음의 비대칭 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-112">running on an Azure virtual machine can use an asymmetric key from the Key Vault.</span></span> <span data-ttu-id="0097a-113">자세한 내용은 [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0097a-113">For more information, see [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).</span></span>

||
|-|
|<span data-ttu-id="0097a-114">**적용 대상**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([일부 지역에서는 미리 보기](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span><span class="sxs-lookup"><span data-stu-id="0097a-114">**Applies to**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="0097a-115">현재 미리 보기 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-115">This is currently a preview feature.</span></span> <span data-ttu-id="0097a-116">내 데이터베이스에서의 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 투명한 데이터 암호화 구현에는 사용권 계약의 미리 보기 약관(예: 기업계약, Microsoft Azure 계약 또는 Microsoft 온라인 정기가입 계약)과 해당 [Microsoft Azure Preview 추가 사용 약관](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)이 적용됨을 확인하고 이에 동의합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-116">I acknowledge and agree that implementation of [!INCLUDE[ssSDS](../includes/sssds-md.md)] transparent data encryption in my database(s) is subject to the preview terms in my license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

 <span data-ttu-id="0097a-117">TDE 상태 미리보기는 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 의 버전 제품군 V12가 현재 일반 가용성 상태에 있다고 알려진 지역의 하위 집합에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-117">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="0097a-118">[!INCLUDE[ssSDS](../includes/sssds-md.md)] 에 대한 TDE는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 이(가) TDE가 미리보기에서 GA로 승격되었음을 알릴 때까지 제품 데이터베이스에서 사용하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-118">TDE for [!INCLUDE[ssSDS](../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="0097a-119">[!INCLUDE[ssSDS](../includes/sssds-md.md)] V12에 대한 자세한 내용은 [Azure SQL Database의 새로운 소식](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-119">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0097a-120">권한</span><span class="sxs-lookup"><span data-stu-id="0097a-120">Permissions</span></span>
 <span data-ttu-id="0097a-121">미리 보기에 등록하고 REST API나 PowerShell을 사용하여 Azure 포털을 통해 TDE를 구성하려면 Azure 소유자, 참가자 또는 SQL 보안 관리자로 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-121">To sign up for the preview and to configure TDE through the Azure portal, by using the REST API, or by using PowerShell, you must be connected as the Azure Owner, Contributor, or SQL Security Manager.</span></span>

 <span data-ttu-id="0097a-122">[!INCLUDE[tsql](../includes/tsql-md.md)] 을 사용하여 TDE를 구성하려면 다음 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-122">To configure TDE by using [!INCLUDE[tsql](../includes/tsql-md.md)] requires the following:</span></span>

-   <span data-ttu-id="0097a-123">이미 TDE 미리 보기에 등록되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-123">You must be already signed up for the TDE preview.</span></span>

-   <span data-ttu-id="0097a-124">데이터베이스 암호화 키를 만들려면 [!INCLUDE[ssSDS](../includes/sssds-md.md)] 관리자여야 하거나 master 데이터베이스의 **dbmanager** 역할 구성원이고 데이터베이스에 대한 **CONTROL** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-124">To create the database encryption key you must be a [!INCLUDE[ssSDS](../includes/sssds-md.md)] administrator or you must be a member of the **dbmanager** role in the master database and have the **CONTROL** permission on the database.</span></span>

-   <span data-ttu-id="0097a-125">SET 옵션을 사용하여 ALTER DATABASE 문을 실행하려면 **dbmanager** 역할에서 구성원 자격만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-125">To execute the ALTER DATABASE statement with the SET option only requires membership in the **dbmanager** role.</span></span>

##  <a name="sign-up-for-the-preview-of-tde-and-enable-tde-on-a-database"></a><a name="Preview"></a><span data-ttu-id="0097a-126">TDE 미리 보기에 등록 하 고 데이터베이스에서 TDE를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-126">Sign Up for the Preview of TDE and Enable TDE on a Database</span></span>

1.  <span data-ttu-id="0097a-127">에서 Azure Portal을 방문 [https://portal.azure.com](https://portal.azure.com) 하 고 Azure 관리자 또는 참가자 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-127">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="0097a-128">왼쪽 배너에서 **찾아보기**를 클릭한 다음 **SQL 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-128">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="0097a-129">왼쪽 창에서 **SQL 데이터베이스**를 선택한 상태로 사용자 데이터베이스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-129">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="0097a-130">데이터베이스 블레이드에서 **모든 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-130">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="0097a-131">**설정** 블레이드에서 **투명한 데이터 암호화(미리 보기)** 부분을 클릭하여 **투명한 데이터 암호화 미리 보기** 블레이드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-131">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span> <span data-ttu-id="0097a-132">TDE 미리 보기에 아직 등록하지 않은 경우 등록을 완료할 때까지 데이터 암호화가 사용되지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-132">If you have not already signed up for the TDE preview, the data encryption settings will be disabled until you complete signup.</span></span>

6.  <span data-ttu-id="0097a-133">**미리 보기 조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-133">Click **PREVIEW TERMS**.</span></span>

7.  <span data-ttu-id="0097a-134">미리 보기의 조건을 읽고 조건에 동의 하는 경우 **투명 한 데이터 및 미리 보기 약관** 확인란을 선택 하 고 페이지 아래쪽에서 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-134">Read the terms of the preview, and if you agree to the terms, select the **Transparent Data encryptionPreview terms** check box, and then click **OK** near the bottom of the page.</span></span> <span data-ttu-id="0097a-135">이제 데이터 **암호화** 단추를 사용 하도록 설정 해야 하는 **데이터 \ 미리 보기** 블레이드로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-135">Returning to the **Data encryptionPREVIEW** blade, where the **Data encryption** button should now be enabled.</span></span>

8.  <span data-ttu-id="0097a-136">**데이터 암호화 미리 보기** 블레이드에서 **데이터 암호화** 단추를 **켬**으로 이동한 다음 페이지 위쪽의 **저장** 을 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-136">In the **Data encryption PREVIEW** blade, move the **Data encryption** button to **On**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="0097a-137">**암호화 상태** 는 투명한 데이터 암호화의 진행률과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-137">The **Encryption status** will approximate the progress of the transparent data encryption.</span></span>

     <span data-ttu-id="0097a-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span><span class="sxs-lookup"><span data-stu-id="0097a-138">![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")</span></span>

     <span data-ttu-id="0097a-139">[!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 권한이 있는 데이터베이스 사용자로 **와 같은 쿼리 도구를 사용하여** 에 연결하는 방법으로도 암호화 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-139">You can also monitor the progress of encryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="0097a-140">`encryption_state` [Dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) 뷰의 열을 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-140">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="enabling-tde-on-sssds-by-using-transact-sql"></a><a name="Encrypt"></a><span data-ttu-id="0097a-141">[!INCLUDE[ssSDS](../includes/sssds-md.md)]Transact-sql을 사용 하 여에서 TDE 사용 설정</span><span class="sxs-lookup"><span data-stu-id="0097a-141">Enabling TDE on [!INCLUDE[ssSDS](../includes/sssds-md.md)] by Using Transact-SQL</span></span>
 <span data-ttu-id="0097a-142">다음 단계에서는 미리 보기에 이미 등록된 상태인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-142">The following steps, assume you have already signed up for the preview.</span></span>

###  <a name="TsqlProcedure"></a>

1.  <span data-ttu-id="0097a-143">관리자 또는 master 데이터베이스의 **dbmanager** 역할 구성원인 로그인을 사용하여 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-143">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="0097a-144">다음 문을 실행하여 데이터베이스 암호화 키를 만들고 데이터베이스를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-144">Execute the following statements to create a database encryption key and encrypt the database.</span></span>

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  <span data-ttu-id="0097a-145">에서 암호화 진행률을 모니터링 하기 위해 [!INCLUDE[ssSDS](../includes/sssds-md.md)] **VIEW database STATE** 권한이 있는 데이터베이스 사용자는 `encryption_state` [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) 뷰의 열을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-145">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a><span data-ttu-id="0097a-146">PowerShell을 사용하여 SQL Database에서 TDE 사용 설정</span><span class="sxs-lookup"><span data-stu-id="0097a-146">Enabling TDE on SQL Database by Using PowerShell</span></span>
 <span data-ttu-id="0097a-147">Azure PowerShell을 사용하면 다음 명령을 실행하여 TDE를 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-147">Using the Azure PowerShell you can run the following command to turn TDE on/off.</span></span> <span data-ttu-id="0097a-148">명령을 실행하기 전에 계정을 PS 창에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-148">You do have to connect your account to the PS window before running the command.</span></span> <span data-ttu-id="0097a-149">다음 단계에서는 미리 보기에 이미 등록된 상태인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-149">The following steps, assume you have already signed up for the preview.</span></span> <span data-ttu-id="0097a-150">PowerShell에 대한 자세한 내용은 [Azure PowerShell을 설치 및 구성하는 방법](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0097a-150">For additional information about PowerShell, see [How to install and configure Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).</span></span>

1.  <span data-ttu-id="0097a-151">TDE를 사용하도록 설정하려면 TDE 상태를 반환하고 암호화 작업을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-151">To enable TDE, return the TDE status, and view the encryption activity.</span></span>

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  <span data-ttu-id="0097a-152">TDE를 사용하지 않도록 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-152">To disable TDE:</span></span>

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="decrypting-a-tde-protected-database-on-sssds"></a><a name="Decrypt"></a><span data-ttu-id="0097a-153">에서 TDE로 보호 되는 데이터베이스 암호 해독[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0097a-153">Decrypting a TDE Protected Database on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>

#### <a name="to-disable-tde-by-using-the-azure-portal"></a><span data-ttu-id="0097a-154">Azure 포털을 사용하여 TDE를 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0097a-154">To Disable TDE by Using the Azure Portal</span></span>

1.  <span data-ttu-id="0097a-155">에서 Azure Portal을 방문 [https://portal.azure.com](https://portal.azure.com) 하 고 Azure 관리자 또는 참가자 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-155">Visit the Azure Portal at [https://portal.azure.com](https://portal.azure.com) and sign-in with your Azure Administrator or Contributor account.</span></span>

2.  <span data-ttu-id="0097a-156">왼쪽 배너에서 **찾아보기**를 클릭한 다음 **SQL 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-156">On the left banner, click to **BROWSE**, and then click **SQL databases**.</span></span>

3.  <span data-ttu-id="0097a-157">왼쪽 창에서 **SQL 데이터베이스**를 선택한 상태로 사용자 데이터베이스를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-157">With **SQL databases** selected in the left pane, click your user database.</span></span>

4.  <span data-ttu-id="0097a-158">데이터베이스 블레이드에서 **모든 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-158">In the database blade, click **All settings**.</span></span>

5.  <span data-ttu-id="0097a-159">**설정** 블레이드에서 **투명한 데이터 암호화(미리 보기)** 부분을 클릭하여 **투명한 데이터 암호화 미리 보기** 블레이드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-159">In the **Settings** blade, click **Transparent data encryption (preview)** part to open the **Transparent data encryption PREVIEW** blade.</span></span>

6.  <span data-ttu-id="0097a-160">**투명한 데이터 암호화 미리 보기** 블레이드에서 **데이터 암호화** 단추를 **끔**으로 이동한 다음 페이지 상단의 **저장** 을 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-160">In the **Transparent data encryption PREVIEW** blade, move the **Data encryption** button to **Off**, and then click **Save** (at the top of the page) to apply the setting.</span></span> <span data-ttu-id="0097a-161">**암호화 상태** 는 투명한 데이터 암호 해독의 진행률과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-161">The **Encryption status** will approximate the progress of the transparent data decryption.</span></span>

     <span data-ttu-id="0097a-162">[!INCLUDE[ssSDS](../includes/sssds-md.md)] VIEW DATABASE STATE [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 권한이 있는 데이터베이스 사용자로 **와 같은 쿼리 도구를 사용하여** 에 연결하는 방법으로도 암호 해독의 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-162">You can also monitor the progress of decryption by connecting to [!INCLUDE[ssSDS](../includes/sssds-md.md)] using a query tool such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] as a database user with the **VIEW DATABASE STATE** permission.</span></span> <span data-ttu-id="0097a-163">`encryption_state` [Dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)뷰의 열을 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-163">Query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)view.</span></span>

#### <a name="to-disable-tde-by-using-transact-sql"></a><span data-ttu-id="0097a-164">Transact-SQL을 사용하여 TDE를 사용하지 않도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0097a-164">To Disable TDE by Using Transact-SQL</span></span>

1.  <span data-ttu-id="0097a-165">관리자 또는 master 데이터베이스의 **dbmanager** 역할 구성원인 로그인을 사용하여 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-165">Connect to the database using a login that is an administrator or a member of the **dbmanager** role in the master database.</span></span>

2.  <span data-ttu-id="0097a-166">다음 문을 실행하여 데이터베이스의 암호를 해독합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-166">Execute the following statements to decrypt the database.</span></span>

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  <span data-ttu-id="0097a-167">에서 암호화 진행률을 모니터링 하기 위해 [!INCLUDE[ssSDS](../includes/sssds-md.md)] **VIEW database STATE** 권한이 있는 데이터베이스 사용자는 `encryption_state` [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) 뷰의 열을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-167">To monitor the progress of encryption on [!INCLUDE[ssSDS](../includes/sssds-md.md)], database users with the **VIEW DATABASE STATE** permission can query the `encryption_state` column of the [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) view.</span></span>

##  <a name="working-with-tde-protected-databases-on-sssds"></a><a name="Working"></a><span data-ttu-id="0097a-168">에서 TDE로 보호 되는 데이터베이스 작업[!INCLUDE[ssSDS](../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0097a-168">Working with TDE Protected Databases on [!INCLUDE[ssSDS](../includes/sssds-md.md)]</span></span>
 <span data-ttu-id="0097a-169">Azure 내에서의 작업을 위해 데이터베이스 암호를 해독할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-169">You do not need to decrypt databases for operations within Azure.</span></span> <span data-ttu-id="0097a-170">원본 데이터베이스 또는 주 데이터베이스의 TDE 설정은 대상에서 투명하게 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-170">The TDE settings on the source database or primary database are transparently inherited on the target.</span></span> <span data-ttu-id="0097a-171">여기에는 다음과 관련된 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-171">This includes operations involving:</span></span>

-   <span data-ttu-id="0097a-172">지리적 복원</span><span class="sxs-lookup"><span data-stu-id="0097a-172">Geo-Restore</span></span>

-   <span data-ttu-id="0097a-173">셀프 서비스 특정 시점 복원</span><span class="sxs-lookup"><span data-stu-id="0097a-173">Self-Service Point in Time Restore</span></span>

-   <span data-ttu-id="0097a-174">삭제된 데이터베이스 복원</span><span class="sxs-lookup"><span data-stu-id="0097a-174">Restore a Deleted Database</span></span>

-   <span data-ttu-id="0097a-175">활성 지역 복제</span><span class="sxs-lookup"><span data-stu-id="0097a-175">Active Geo_Replication</span></span>

-   <span data-ttu-id="0097a-176">데이터베이스 복사본 만들기</span><span class="sxs-lookup"><span data-stu-id="0097a-176">Creating a Database Copy</span></span>

##  <a name="moving-a-tde-protected-database-on-using-bacpac-files"></a><a name="Moving"></a><span data-ttu-id="0097a-177">을 사용 하 여 TDE로 보호 되는 데이터베이스 이동 Bacpac 파일</span><span class="sxs-lookup"><span data-stu-id="0097a-177">Moving a TDE Protected Database on using .Bacpac Files</span></span>
 <span data-ttu-id="0097a-178">[!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] 포털 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서 데이터베이스 내보내기 함수를 사용하여 TDE로 보호되는 데이터베이스를 내보내는 경우 데이터베이스의 내용이 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-178">When exporting a TDE protected database using the Export Database function in the [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Portal or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard, the content of the database is not encrypted.</span></span> <span data-ttu-id="0097a-179">암호화되지 않은.bacpac 파일에 내용이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-179">The content is stored in .bacpac files which are not encrypted.</span></span>  <span data-ttu-id="0097a-180">새 데이터베이스 가져오기가 완료되면 .bacpac 파일을 적절하게 보호하고 TDE를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0097a-180">Be sure to protect the .bacpac files appropriately and enable TDE once import of the new database is completed.</span></span>

## <a name="related-sql-server-topic"></a><span data-ttu-id="0097a-181">관련 SQL Server 항목</span><span class="sxs-lookup"><span data-stu-id="0097a-181">Related SQL Server Topic</span></span>
 [<span data-ttu-id="0097a-182">EKM을 사용 하 여 TDE 사용</span><span class="sxs-lookup"><span data-stu-id="0097a-182">Enable TDE Using EKM</span></span>](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a><span data-ttu-id="0097a-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0097a-183">See Also</span></span>
 <span data-ttu-id="0097a-184">[&#40;TDE&#41;투명한 데이터 암호화](../relational-databases/security/encryption/transparent-data-encryption.md) [자격 증명 만들기 &#40;](/sql/t-sql/statements/create-credential-transact-sql) [TRANSACT-SQL&#41;create a](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [database Encryption key](/sql/t-sql/statements/create-database-encryption-key-transact-sql) &#40;transact-sql&#41;[alter](/sql/t-sql/statements/alter-database-transact-sql) database &#40;transact-sql&#41;alter database [SET 옵션](/sql/t-sql/statements/alter-database-transact-sql-set-options) &#40;transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0097a-184">[Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)</span></span>
