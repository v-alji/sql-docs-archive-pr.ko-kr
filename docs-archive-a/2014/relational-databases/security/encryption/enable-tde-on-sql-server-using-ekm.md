---
title: EKM을 사용 하 여 TDE 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: e659c5ff0245fdb17192b845eafc60badf5e295e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741711"
---
# <a name="enable-tde-using-ekm"></a><span data-ttu-id="da86f-102">EKM을 사용하여 TDE 설정</span><span class="sxs-lookup"><span data-stu-id="da86f-102">Enable TDE Using EKM</span></span>
  <span data-ttu-id="da86f-103">이 항목에서는 EKM(확장 가능 키 관리) 모듈에 저장된 비대칭 키를 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에 사용하여 데이터베이스 암호화 키를 보호하기 위해 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 TDE(투명한 데이터 암호화)를 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-103">This topic describes how to enable transparent data encryption (TDE) in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to protect a database encryption key by using an asymmetric key stored in an extensible key management (EKM) module with [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="da86f-104">TDE는 데이터베이스 암호화 키라는 대칭 키를 사용하여 전체 데이터베이스의 스토리지를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-104">TDE encrypts the storage of an entire database by using a symmetric key called the database encryption key.</span></span> <span data-ttu-id="da86f-105">또한 master 데이터베이스의 데이터베이스 마스터 키로 보호되는 인증서를 사용하여 데이터베이스 암호화 키를 보호할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-105">The database encryption key can also be protected using a certificate which is protected by the database master key of the master database.</span></span> <span data-ttu-id="da86f-106">데이터베이스 마스터 키를 사용하여 데이터베이스 암호화 키를 보호하는 방법은 [TDE&#40;투명한 데이터 암호화&#41;](transparent-data-encryption.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da86f-106">For more information about protecting the database encryption key by using the database master key, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span> <span data-ttu-id="da86f-107">Azure VM에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]이 실행 중인 경우 TDE 구성 방법은 [Azure 주요 자격 증명 모음을 사용한 확장 가능 키 관리&#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da86f-107">For information about configuring TDE when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running on an Azure VM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
 <span data-ttu-id="da86f-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="da86f-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="da86f-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="da86f-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="da86f-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="da86f-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="da86f-111">보안</span><span class="sxs-lookup"><span data-stu-id="da86f-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="da86f-112">Transact-SQL에서 EKM을 사용하여 TDE를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="da86f-112">To enable TDE using EKM, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="da86f-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="da86f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="da86f-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="da86f-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="da86f-115">데이터베이스 암호화 키를 만들고 데이터베이스를 암호화하려면 시스템 관리자와 같은 높은 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-115">You must be a high privileged user (such as a system administrator) to create a database encryption key and encrypt a database.</span></span> <span data-ttu-id="da86f-116">해당 사용자는 EKM 모듈로 인증될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-116">That user must be able to be authenticated by the EKM module.</span></span>  
  
-   <span data-ttu-id="da86f-117">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 시작 시 데이터베이스를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-117">Upon start up the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must open the database.</span></span> <span data-ttu-id="da86f-118">이를 위해서는 EKM에서 인증할 인증서를 만들고 비대칭 키를 기반으로 하는 로그인에 인증서를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-118">To do this, you should create a credential that will be authenticated by the EKM, and add it to a login that is based on an asymmetric key.</span></span> <span data-ttu-id="da86f-119">사용자는 이 로그인을 사용하여 로그인할 수 없지만 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 은 이를 사용하여 EKM 디바이스에서 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-119">Users cannot login using that login, but the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] will be able to authenticate itself with the EKM device.</span></span>  
  
-   <span data-ttu-id="da86f-120">EKM 모듈에 저장된 비대칭 키를 분실한 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 해당 데이터베이스를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-120">If the asymmetric key stored in the EKM module is lost, the database will not be able to be opened by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="da86f-121">EKM 공급자가 비대칭 키를 백업할 수 있도록 허용하는 경우 백업을 만들고 안전한 위치에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-121">If the EKM provider lets you back up the asymmetric key, you should create a back up and store it in a secure location.</span></span>  
  
-   <span data-ttu-id="da86f-122">EKM 공급자에 필요한 옵션 및 매개 변수는 아래 코드 예에 제공된 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-122">The options and parameters required by your EKM provider can differ from what is provided in the code example below.</span></span> <span data-ttu-id="da86f-123">자세한 내용은 해당 EKM 공급자를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da86f-123">For more information, see your EKM provider.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="da86f-124">보안</span><span class="sxs-lookup"><span data-stu-id="da86f-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="da86f-125">권한</span><span class="sxs-lookup"><span data-stu-id="da86f-125">Permissions</span></span>  
 <span data-ttu-id="da86f-126">이 항목에서는 다음 권한이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-126">This topic uses the following permissions:</span></span>  
  
-   <span data-ttu-id="da86f-127">구성 옵션을 변경하고 RECONFIGURE 문을 실행하려면 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-127">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="da86f-128">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
-   <span data-ttu-id="da86f-129">ALTER ANY CREDENTIAL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-129">Requires ALTER ANY CREDENTIAL permission.</span></span>  
  
-   <span data-ttu-id="da86f-130">ALTER ANY LOGIN 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-130">Requires ALTER ANY LOGIN permission.</span></span>  
  
-   <span data-ttu-id="da86f-131">CREATE ASYMMETRIC KEY 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-131">Requires CREATE ASYMMETRIC KEY permission.</span></span>  
  
-   <span data-ttu-id="da86f-132">데이터베이스를 암호화하려면 데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-132">Requires CONTROL permission on the database to encrypt the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="da86f-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="da86f-133">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-tde-using-ekm"></a><span data-ttu-id="da86f-134">EKM을 사용하여 TDE를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="da86f-134">To enable TDE using EKM</span></span>  
  
1.  <span data-ttu-id="da86f-135">EKM 공급자가 제공하는 파일을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 컴퓨터의 적절한 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-135">Copy the files supplied by the EKM provider to an appropriate location on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="da86f-136">이 예에서는 **C:\EKM** 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-136">In this example, we use the **C:\EKM** folder.</span></span>  
  
2.  <span data-ttu-id="da86f-137">EKM 공급자의 요구 사항에 따라 컴퓨터에 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-137">Install certificates to the computer as required by your EKM provider.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="da86f-138">는 EKM 공급자를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-138">does not supply an EKM provider.</span></span> <span data-ttu-id="da86f-139">각 EKM 공급자에 따라 사용자 설치, 구성 및 권한 부여에 대한 절차가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-139">Each EKM provider can have different procedures for installing, configuring and authorizing users.</span></span>  <span data-ttu-id="da86f-140">이 단계를 수행하려면 해당 EKM 공급자 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da86f-140">Consult your EKM provider documentation to complete this step.</span></span>  
  
3.  <span data-ttu-id="da86f-141">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
4.  <span data-ttu-id="da86f-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-142">On the Standard bar, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="da86f-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da86f-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 <span data-ttu-id="da86f-144">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="da86f-144">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="da86f-145">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-145">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="da86f-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-146">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [<span data-ttu-id="da86f-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-147">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="da86f-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [<span data-ttu-id="da86f-149">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-149">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [<span data-ttu-id="da86f-150">CREATE DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-150">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="da86f-151">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-151">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [<span data-ttu-id="da86f-152">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-152">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="da86f-153">Azure Key Vault를 사용한 확장 가능 키 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="da86f-153">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [<span data-ttu-id="da86f-154">Azure SQL Database를 사용한 투명한 데이터 암호화</span><span class="sxs-lookup"><span data-stu-id="da86f-154">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
