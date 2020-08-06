---
title: 암호화된 백업 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d46cc686684d87fe393a5db7cfe01194ae917836
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740089"
---
# <a name="create-an-encrypted-backup"></a><span data-ttu-id="b3462-102">암호화된 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="b3462-102">Create an Encrypted Backup</span></span>
  <span data-ttu-id="b3462-103">이 항목에서는 Transact-SQL을 사용하여 암호화된 백업을 만드는 데 필요한 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-103">This topic describes the steps necessary to create an encrypted backup using Transact-SQL.</span></span>  
  
## <a name="backup-to-disk-with-encryption"></a><span data-ttu-id="b3462-104">암호화하여 디스크에 백업</span><span class="sxs-lookup"><span data-stu-id="b3462-104">Backup to Disk with Encryption</span></span>  
 <span data-ttu-id="b3462-105">**사전 요구 사항:**</span><span class="sxs-lookup"><span data-stu-id="b3462-105">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="b3462-106">데이터베이스의 백업을 만드는 데 적합한 공간이 있는 로컬 디스크나 스토리지에 대한 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="b3462-106">Access to a local disk or to storage with adequate space to create a backup of the database.</span></span>  
  
-   <span data-ttu-id="b3462-107">master 데이터베이스의 데이터베이스 마스터 키 및 SQL Server 인스턴스에서 사용할 수 있는 인증서 또는 비대칭 키.</span><span class="sxs-lookup"><span data-stu-id="b3462-107">A Database Master Key for the master database, and a certificate or asymmetric key available on the instance of SQL Server.</span></span> <span data-ttu-id="b3462-108">암호화 요구 사항과 사용 권한에 대한 자세한 내용은 [Backup Encryption](backup-encryption.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3462-108">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
 <span data-ttu-id="b3462-109">다음 단계를 사용하여 로컬 디스크에 데이터베이스의 암호화된 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-109">Use the following steps to create an encrypted backup of a database to a local disk.</span></span> <span data-ttu-id="b3462-110">이 예에서는 MyTestDB라는 사용자 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-110">This example uses a user database called MyTestDB.</span></span>  
  
1.  <span data-ttu-id="b3462-111">**master 데이터베이스의 데이터베이스 마스터 키 만들기:** 데이터베이스에 저장되는 마스터 키의 복사본을 암호화하기 위한 암호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-111">**Create a Database Master Key of the master database:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="b3462-112">데이터베이스 엔진에 연결하고 새 쿼리 창을 시작한 다음 아래의 예를 복사하여 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-112">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  <span data-ttu-id="b3462-113">**백업 인증서 만들기:** master 데이터베이스에 백업 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-113">**Create a Backup Certificate:** Create a backup certificate in the master database.</span></span> <span data-ttu-id="b3462-114">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-114">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="b3462-115">**데이터베이스 백업:** 사용할 암호화 알고리즘과 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-115">**Backup the database:** Specify the encryption algorithm and certificate to use.</span></span> <span data-ttu-id="b3462-116">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-116">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 <span data-ttu-id="b3462-117">EKM에 의해 보호되는 백업을 암호화하는 예제를 보려면 [Azure 키 자격 증명 모음을 사용한 확장 가능 키 관리&#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3462-117">For an example of encrypting a backup protected by an EKM, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
### <a name="backup-to-azure-storage-with-encryption"></a><span data-ttu-id="b3462-118">암호화하여 Azure Storage에 백업</span><span class="sxs-lookup"><span data-stu-id="b3462-118">Backup to Azure Storage with Encryption</span></span>  
 <span data-ttu-id="b3462-119">**URL에 대한 SQL Server 백업** 옵션을 사용하여 Azure Storage에 백업을 만드는 경우 암호화 단계는 동일하지만 URL을 대상으로 사용하고 SQL 자격 증명을 사용하여 Azure Storage에 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-119">If you are creating a backup to Azure storage using the **SQL Server Backup to URL** option, the encryption steps are the same, but you must use URL as the destination and a SQL Credential to authenticate to the Azure storage.</span></span> <span data-ttu-id="b3462-120">암호화 옵션을 사용 하 여를 구성 하려면 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] [azure에 대 한 관리 되는 백업 SQL Server 설정](enable-sql-server-managed-backup-to-microsoft-azure.md) [SQL Server 및 가용성 그룹에 대 한 Azure로의 관리 되는 백업](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b3462-120">If you want to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with encryption options, see [Setting up SQL Server Managed Backup to Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 <span data-ttu-id="b3462-121">**사전 요구 사항:**</span><span class="sxs-lookup"><span data-stu-id="b3462-121">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="b3462-122">Windows 스토리지 계정 및 컨테이너.</span><span class="sxs-lookup"><span data-stu-id="b3462-122">A windows storage account and a container.</span></span> <span data-ttu-id="b3462-123">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3462-123">For more information, see.</span></span> <span data-ttu-id="b3462-124">[1단원: Azure Storage 개체 만들기](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b3462-124">[Lesson 1: Create Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).</span></span>  
  
-   <span data-ttu-id="b3462-125">master 데이터베이스의 데이터베이스 마스터 키 및 SQL Server 인스턴스에 대한 인증서 또는 비대칭 키.</span><span class="sxs-lookup"><span data-stu-id="b3462-125">A Database Master Key for the master database, and a certificate or asymmetric key  on the instance of SQL Server.</span></span> <span data-ttu-id="b3462-126">암호화 요구 사항과 사용 권한에 대한 자세한 내용은 [Backup Encryption](backup-encryption.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b3462-126">For encryption requirements and permissions, see [Backup Encryption](backup-encryption.md).</span></span>  
  
1.  <span data-ttu-id="b3462-127">**SQL Server 자격 증명 만들기:** SQL Server 자격 증명을 만들려면 데이터베이스 엔진에 연결하고 새 쿼리 창을 연 다음 아래의 예를 복사하여 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-127">**Create SQL Server Credential:** To create a SQL Server credential, connect to the Database Engine, open a new query window, and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  <span data-ttu-id="b3462-128">**데이터베이스 마스터 키 만들기:** 데이터베이스에 저장되는 마스터 키의 복사본을 암호화하기 위한 암호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-128">**Create a Database Master Key:** Choose a password for encrypting the copy of the master key that will be stored in the database.</span></span> <span data-ttu-id="b3462-129">데이터베이스 엔진에 연결하고 새 쿼리 창을 시작한 다음 아래의 예를 복사하여 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-129">Connect to the database engine, start a new query windows and copy and paste the following example and click **Execute**.</span></span>  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  <span data-ttu-id="b3462-130">**백업 인증서 만들기:** master 데이터베이스에 백업 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-130">**Create a Backup Certificate:** Create a Backup Certificate in the master database.</span></span> <span data-ttu-id="b3462-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-131">Copy and paste the following example in the query window and click **Execute**</span></span>  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  <span data-ttu-id="b3462-132">**데이터베이스 백업:** 사용할 암호화 알고리즘과 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-132">**Backup the database:** Specify the encryption algorithm and the certificate to use.</span></span> <span data-ttu-id="b3462-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3462-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
