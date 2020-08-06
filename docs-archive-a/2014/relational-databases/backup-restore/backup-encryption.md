---
title: 백업 암호화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a78ae4969982fbfe5295ee4219855f48ac60793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743339"
---
# <a name="backup-encryption"></a><span data-ttu-id="82494-102">백업 암호화</span><span class="sxs-lookup"><span data-stu-id="82494-102">Backup Encryption</span></span>
  <span data-ttu-id="82494-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업의 암호화 옵션에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-103">This topic provides an overview of the encryption options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="82494-104">여기에서는 백업 중의 암호화에 대한 사용법, 이점 및 권장 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="82494-104">It includes details of the usage, benefits, and recommended practices for encrypting during backup.</span></span>  
  
  
##  <a name="overview"></a><a name="Overview"></a> <span data-ttu-id="82494-105">개요</span><span class="sxs-lookup"><span data-stu-id="82494-105">Overview</span></span>  
 <span data-ttu-id="82494-106">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]부터 SQL Server에는 백업을 만드는 동안 데이터를 암호화하는 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-106">Starting in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SQL Server has the ability to encrypt the data while creating a backup.</span></span> <span data-ttu-id="82494-107">백업을 만들 때 암호화 알고리즘과 암호기(인증서 또는 비대칭 키)를 지정하여 암호화된 백업 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-107">By specifying the encryption algorithm and the encryptor (a Certificate or Asymmetric Key) when creating a backup, you can create an encrypted backup file.</span></span> <span data-ttu-id="82494-108">모든 스토리지 대상, 즉 온-프레미스 및 Window Azure Storage가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-108">All storage destinations: on-premises and Window Azure storage are supported.</span></span> <span data-ttu-id="82494-109">또한 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 에서 도입된 새로운 기능인 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]작업에 대해 암호화 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-109">In addition, encryption options can be configured for [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] operations, a new feature introduced in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="82494-110">백업 중에 암호화하려면 암호화 키를 보호할 암호기와 암호화 알고리즘을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-110">To encrypt during backup, you must specify an encryption algorithm, and an encryptor to secure the encryption key.</span></span> <span data-ttu-id="82494-111">지원되는 암호화 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-111">The following are the supported encryption options:</span></span>  
  
-   <span data-ttu-id="82494-112">**암호화 알고리즘:** 지원되는 암호화 알고리즘은 AES 128, AES 192, AES 256 및 Triple DES입니다.</span><span class="sxs-lookup"><span data-stu-id="82494-112">**Encryption Algorithm:** The supported encryption algorithms are: AES 128, AES 192, AES 256, and Triple DES</span></span>  
  
-   <span data-ttu-id="82494-113">**암호기:** 인증서 또는 비대칭 키</span><span class="sxs-lookup"><span data-stu-id="82494-113">**Encryptor:** A certificate or asymmetric Key</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="82494-114">인증서나 비대칭 키를 백업하는 것이 매우 중요하며, 이때 가급적이면 인증서나 비대칭 키를 사용하여 암호화한 백업 파일과 다른 위치에 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-114">It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt.</span></span> <span data-ttu-id="82494-115">인증서나 비대칭 키가 없으면 백업을 복원할 수 없으므로 백업 파일을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-115">Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable.</span></span>  
  
 <span data-ttu-id="82494-116">**암호화된 백업 복원:** SQL Server 복원에서는 복원 중에 암호화 매개 변수를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-116">**Restoring the encrypted backup:** SQL Server restore does not require any encryption parameters to be specified during restores.</span></span> <span data-ttu-id="82494-117">또한 복원할 대상 인스턴스에서 백업 파일을 암호화하는 데 사용된 인증서나 비대칭 키를 사용할 수 없어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-117">It does require that the certificate or the asymmetric key used to encrypt the backup file be available on the instance that you are restoring to.</span></span> <span data-ttu-id="82494-118">복원을 수행하는 사용자 계정에는 인증서나 키에 대한 `VIEW DEFINITION` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-118">The user account performing the restore must have `VIEW DEFINITION` permissions on the certificate or key.</span></span> <span data-ttu-id="82494-119">암호화된 백업을 다른 인스턴스로 복원하는 경우 해당 인스턴스에서 인증서를 사용할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-119">If you are restoring the encrypted backup to a different instance, you must make sure that the certificate is available on that instance.</span></span>  
  
 <span data-ttu-id="82494-120">TDE로 암호화된 데이터베이스에서 백업을 복원하는 경우에는 복원할 대상 인스턴스에서 TDE 인증서를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-120">If you are restoring a backup from a TDE encrypted database, the TDE certificate should be available on the instance you are restoring to.</span></span>  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="82494-121">이점</span><span class="sxs-lookup"><span data-stu-id="82494-121">Benefits</span></span>  
  
1.  <span data-ttu-id="82494-122">데이터베이스 백업을 암호화하면 데이터를 보호하는 데 도움이 됩니다. SQL Server는 백업을 만드는 동안 백업 데이터를 암호화하는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-122">Encrypting the database backups helps secure the data: SQL Server provides the option to encrypt the backup data while creating a backup.</span></span>  
  
2.  <span data-ttu-id="82494-123">TDE를 사용하여 암호화된 데이터베이스에도 암호화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-123">Encryption can also be used for databases that are encrypted using TDE.</span></span>  
  
3.  <span data-ttu-id="82494-124">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]으로 수행된 백업에 대한 암호화가 지원되며, 이를 통해 오프사이트 백업의 보안이 강화됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-124">Encryption is supported for backups done by [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], which provides additional security for off-site backups.</span></span>  
  
4.  <span data-ttu-id="82494-125">이 기능은 AES 256비트까지 여러 암호화 알고리즘을 지원하므로</span><span class="sxs-lookup"><span data-stu-id="82494-125">This feature supports multiple encryption algorithms up to AES 256 bit.</span></span> <span data-ttu-id="82494-126">사용자의 요구 사항에 적합한 알고리즘을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-126">This gives you the option to select an algorithm that aligns with your requirements.</span></span>  
  
5.  <span data-ttu-id="82494-127">EKM(확장 키 관리) 공급자와 암호화 키를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-127">You can integrate encryption keys with Extended Key Management (EKM) providers.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="82494-128">필수 조건</span><span class="sxs-lookup"><span data-stu-id="82494-128">Prerequisites</span></span>  
 <span data-ttu-id="82494-129">백업을 암호화하기 위한 사전 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-129">The following are prerequisites for encrypting a backup:</span></span>  
  
1.  <span data-ttu-id="82494-130">**master 데이터베이스의 데이터베이스 마스터 키를 만듭니다.** 데이터베이스 마스터 키는 데이터베이스에 있는 비대칭 키와 인증서의 프라이빗 키를 보호하는 데 사용되는 대칭 키입니다.</span><span class="sxs-lookup"><span data-stu-id="82494-130">**Create a Database Master Key for the master database:** The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="82494-131">자세한 내용은 [SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82494-131">For more information, see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
2.  <span data-ttu-id="82494-132">백업 암호화에 사용할 인증서나 비대칭 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82494-132">Create a certificate or asymmetric Key to use for backup encryption.</span></span> <span data-ttu-id="82494-133">인증서를 만드는 방법은 [CREATE CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82494-133">For more information on creating a certificate, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span> <span data-ttu-id="82494-134">비대칭 키를 만드는 방법은 [CREATE ASYMMETRIC KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82494-134">For more information on creating an asymmetric key, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="82494-135">EKM(확장 키 관리)에 있는 비대칭 키만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-135">Only asymmetric keys residing in an Extended Key Management (EKM) are supported.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="82494-136">제한 사항</span><span class="sxs-lookup"><span data-stu-id="82494-136">Restrictions</span></span>  
 <span data-ttu-id="82494-137">암호화 옵션에 적용되는 제한 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-137">The following are restrictions that apply to the encryption options:</span></span>  
  
-   <span data-ttu-id="82494-138">비대칭 키를 사용하여 백업 데이터를 암호화하는 경우 EKM 공급자에 있는 비대칭 키만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-138">If you are using asymmetric key to encrypt the backup data, only asymmetric keys residing in the EKM provider are supported.</span></span>  
  
-   <span data-ttu-id="82494-139">SQL Server Express와 SQL Server Web은 백업 중에 암호화를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-139">SQL Server Express and SQL Server Web do not support encryption during backup.</span></span> <span data-ttu-id="82494-140">그러나 암호화된 백업을 SQL Server Express 또는 SQL Server Web의 인스턴스로 복원할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-140">However restoring from an encrypted backup to an instance of SQL Server Express or SQL Server Web is supported.</span></span>  
  
-   <span data-ttu-id="82494-141">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 암호화된 백업을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-141">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read encrypted backups.</span></span>  
  
-   <span data-ttu-id="82494-142">암호화된 백업의 경우 기존 백업 세트 옵션에 추가는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-142">Appending to an existing backup set option is not supported for encrypted backups.</span></span>  
  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="82494-143">권한</span><span class="sxs-lookup"><span data-stu-id="82494-143">Permissions</span></span>  
 <span data-ttu-id="82494-144">**백업을 암호화하거나 암호화된 백업에서 복원하려면:**</span><span class="sxs-lookup"><span data-stu-id="82494-144">**To encrypt a backup or to restore from an encrypted backup:**</span></span>  
  
 <span data-ttu-id="82494-145">데이터베이스 백업을 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 `VIEW DEFINITION` 권한</span><span class="sxs-lookup"><span data-stu-id="82494-145">`VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database backup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82494-146">TDE 인증서에 대한 액세스 권한은 TDE로 보호되는 데이터베이스를 백업하거나 복원하는 데 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-146">Access to the TDE certificate is not required to back up or restore a TDE protected database.</span></span>  
  
##  <a name="backup-encryption-methods"></a><a name="Methods"></a> <span data-ttu-id="82494-147">백업 암호화 방법</span><span class="sxs-lookup"><span data-stu-id="82494-147">Backup Encryption Methods</span></span>  
 <span data-ttu-id="82494-148">아래의 섹션들에서는 백업 중에 데이터를 암호화하는 단계를 간략하게 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-148">The sections below provide a brief introduction to the steps to encrypting the data during backup.</span></span> <span data-ttu-id="82494-149">Transact-SQL을 사용하여 백업을 암호화하는 다른 단계에 대한 전체 연습은 [암호화된 백업 만들기](create-an-encrypted-backup.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82494-149">For a complete walkthrough of the different steps of encrypting your backup using Transact-SQL, see [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
### <a name="using-sql-server-management-studio"></a><span data-ttu-id="82494-150">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="82494-150">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="82494-151">다음 대화 상자에서 데이터베이스의 백업을 만들 때 백업을 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-151">You can encrypt a backup when creating the backup of a database in any of the following dialog boxes:</span></span>  
  
1.  <span data-ttu-id="82494-152">[데이터베이스 백업&#40;백업 옵션 페이지&#41;](back-up-database-backup-options-page.md)**백업 옵션** 페이지에서 **암호화**를 선택하고 암호화 알고리즘과 암호화에 사용할 인증서 또는 비대칭 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-152">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) On the **Backup Options** page, you can select **Encryption**, and specify the encryption algorithm and the certificate or asymmetric key to use for the encryption.</span></span>  
  
2.  <span data-ttu-id="82494-153">[유지 관리 계획 마법사 사용](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) 백업 태스크를 선택할 때 **백업 태스크 정의** 페이지의 **옵션** 탭에서 **백업 암호화**를 선택하고 암호화 알고리즘과 암호화에 사용할 인증서 또는 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-153">[Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) When you select a backup task, on the **Options** tab of the **Define Backup ()Task** page, you can select **Backup Encryption**, and specify the encryption algorithm and the certificate or key to use for the encryption.</span></span>  
  
### <a name="using-transact-sql"></a><span data-ttu-id="82494-154">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="82494-154">Using Transact SQL</span></span>  
 <span data-ttu-id="82494-155">다음은 백업 파일을 암호화하는 예제 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="82494-155">Following is a sample Transact-SQL statement to encrypt the backup file:</span></span>  
  
```sql
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO
```  
  
 <span data-ttu-id="82494-156">전체 Transact-SQL 문 구문은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82494-156">For the full Transact-SQL statement syntax, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="using-powershell"></a><span data-ttu-id="82494-157">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="82494-157">Using PowerShell</span></span>  
 <span data-ttu-id="82494-158">이 예제에서는 암호화 옵션을 만든 다음 **Backup-SqlDatabase** cmdlet에서 매개 변수 값으로 사용하여 암호화된 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82494-158">This example creates the encryption options and uses it as a parameter value in **Backup-SqlDatabase** cmdlet to create an encrypted backup.</span></span>  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="recommended-practices"></a><a name="RecommendedPractices"></a> <span data-ttu-id="82494-159">권장 방법</span><span class="sxs-lookup"><span data-stu-id="82494-159">Recommended Practices</span></span>  
 <span data-ttu-id="82494-160">암호화 인증서 및 키의 백업을 인스턴스가 설치된 로컬 컴퓨터 이외의 위치에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82494-160">Create a backup of the encryption certificate and keys to a location other than your local machine where the instance is installed.</span></span> <span data-ttu-id="82494-161">재해 복구 시나리오를 고려하여 인증서 또는 키의 백업을 오프사이트 위치에 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-161">To account for disaster recovery scenarios, consider storing a backup of the certificate or key to an off-site location.</span></span> <span data-ttu-id="82494-162">암호화된 백업은 해당 백업을 암호화하는 데 사용된 인증서 없이 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82494-162">You cannot restore an encrypted backup without the certificate used to encrypt the backup.</span></span>  
  
 <span data-ttu-id="82494-163">암호화된 백업을 복원하려면 일치하는 지문을 사용하여 백업을 만들 때 사용된 원래 인증서가 복원할 대상 인스턴스에서 사용 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-163">To restore an encrypted backup, the original certificate used when the backup was taken with the matching thumbprint should be available on the instance you are restoring to.</span></span> <span data-ttu-id="82494-164">따라서 인증서가 만료 시 갱신되거나 어떤 식으로든 변경되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-164">Therefore, the certificate should not be renewed on expiry or changed in any way.</span></span> <span data-ttu-id="82494-165">갱신하면 인증서가 업데이트되어 지문 변경이 트리거될 수 있으므로 백업 파일에 인증서를 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-165">Renewal can result in updating the certificate triggering the change of the thumbprint, therefore making the certificate invalid for the backup file.</span></span> <span data-ttu-id="82494-166">복원을 수행하는 계정에는 백업 중에 암호화하는 데 사용된 인증서나 비대칭 키에 대한 VIEW DEFINITION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-166">The account performing the restore should have VIEW DEFINITION permissions on the certificate or the asymmetric key used to encrypt during backup.</span></span>  
  
 <span data-ttu-id="82494-167">가용성 그룹 데이터베이스 백업은 기본 백업 복제본에서 일반적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="82494-167">Availability Group database backups are typically performed on the preferred backup replica.</span></span>  <span data-ttu-id="82494-168">백업이 수행된 복제본이 아닌 복제본에서 백업을 복원하는 경우 백업에 사용된 원래 인증서가 복원할 복제본에서 사용 가능한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-168">If restoring a backup on a replica other than where the backup was taken from, ensure that the original certificate used for backup is available on the replica you are restoring to.</span></span>  
  
 <span data-ttu-id="82494-169">데이터베이스에서 TDE를 사용하도록 설정된 경우 데이터베이스와 백업을 암호화하기 위해 다른 인증서 또는 비대칭 키를 선택하여 보안을 강화합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-169">If the database is TDE enabled, choose different certificates or asymmetric keys for encrypting the database and the backup to increase security.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="82494-170">관련 작업</span><span class="sxs-lookup"><span data-stu-id="82494-170">Related Tasks</span></span>  
  
|<span data-ttu-id="82494-171">항목/태스크</span><span class="sxs-lookup"><span data-stu-id="82494-171">Topic/Task</span></span>|<span data-ttu-id="82494-172">Description</span><span class="sxs-lookup"><span data-stu-id="82494-172">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="82494-173">암호화된 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="82494-173">Create an Encrypted Backup</span></span>](create-an-encrypted-backup.md)|<span data-ttu-id="82494-174">암호화된 백업을 만드는 데 필요한 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-174">Describes the basic steps required to create an encrypted backup</span></span>|  
|[<span data-ttu-id="82494-175">Azure에 SQL Server 관리 백업 - 보존 및 스토리지 설정</span><span class="sxs-lookup"><span data-stu-id="82494-175">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|<span data-ttu-id="82494-176">암호화 옵션이 지정된 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 을 구성하는 데 필요한 기본 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-176">Describes the basic steps required to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with the encryption options specified.</span></span>|  
|[<span data-ttu-id="82494-177">Azure Key Vault를 사용한 확장 가능 키 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82494-177">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|<span data-ttu-id="82494-178">Azure 키 자격 증명 모음에서 키로 보호하는 암호화된 백업을 만드는 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82494-178">Provides an example of creating an encrypted backup protected by keys in the Azure Key Vault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82494-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82494-179">See Also</span></span>  
 [<span data-ttu-id="82494-180">백업 개요&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82494-180">Backup Overview &#40;SQL Server&#41;</span></span>](backup-overview-sql-server.md)  
  
  
