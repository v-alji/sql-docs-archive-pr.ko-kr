---
title: '5단원: 필드 TDE를 사용 하 여 데이터베이스 암호화 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 613b66c04a69364f3c9be1059f95021dd3eff595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652113"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a><span data-ttu-id="4afc1-103">5단원:</span><span class="sxs-lookup"><span data-stu-id="4afc1-103">Lesson 5.</span></span> <span data-ttu-id="4afc1-104">(선택 사항) TDE를 사용하여 데이터베이스 암호화</span><span class="sxs-lookup"><span data-stu-id="4afc1-104">(Optional) Encrypt your database using TDE</span></span>
  <span data-ttu-id="4afc1-105">선택적 단계로, 새로 만든 데이터베이스를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-105">As an optional step, you can encrypt the newly created database.</span></span> <span data-ttu-id="4afc1-106">TDE(투명한 데이터 암호화)를 통해 데이터 및 로그 파일의 실시간 I/O 암호화 및 암호 해독을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-106">Transparent data encryption (TDE) performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="4afc1-107">이러한 종류의 암호화에서는 DEK(데이터베이스 암호화 키)를 사용하며 이 키는 복구하는 동안 사용할 수 있도록 데이터베이스 부트 레코드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-107">This kind of encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="4afc1-108">자세한 내용은 [투명한 데이터 암호화 &#40;tde&#41;](security/encryption/transparent-data-encryption.md) 및 [Tde로 보호 되는 데이터베이스를 다른 SQL Server로 이동](security/encryption/move-a-tde-protected-database-to-another-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4afc1-108">For more information, see [Transparent Data Encryption &#40;TDE&#41;](security/encryption/transparent-data-encryption.md) and [Move a TDE Protected Database to Another SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).</span></span>  
  
 <span data-ttu-id="4afc1-109">이 단원에서는 다음 단계를 이미 완료했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-109">This lesson assumes you already completed the following steps:</span></span>  
  
-   <span data-ttu-id="4afc1-110">Azure Storage 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-110">You have an Azure Storage account.</span></span>  
  
-   <span data-ttu-id="4afc1-111">Azure Storage 계정으로 컨테이너를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-111">You have created a container under your Azure Storage account.</span></span>  
  
-   <span data-ttu-id="4afc1-112">읽기, 쓰기 및 나열 권한이 있는 컨테이너에 정책을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-112">You have created a policy on a container with read, write, and list rights.</span></span> <span data-ttu-id="4afc1-113">SAS 키도 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-113">You also generated a SAS key.</span></span>  
  
-   <span data-ttu-id="4afc1-114">원본 컴퓨터에서 SQL Server 자격 증명을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-114">You have created a SQL Server credential on the source machine.</span></span>  
  
-   <span data-ttu-id="4afc1-115">4단원에서 설명한 단계를 수행하여 데이터베이스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-115">You have created a database by following the steps that are described in Lesson 4.</span></span>  
  
 <span data-ttu-id="4afc1-116">데이터베이스를 암호화하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-116">If you want to encrypt a database, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4afc1-117">원본 컴퓨터의 쿼리 창에서 다음 문을 수정하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-117">In the source machine, modify and run the following statements in a query window:</span></span>  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  <span data-ttu-id="4afc1-118">다음 단계를 수행하여 원본 컴퓨터에서 새 데이터베이스를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-118">Then, encrypt your new database in the source machine by following these steps:</span></span>  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 <span data-ttu-id="4afc1-119">데이터베이스의 암호화 상태와 연결된 데이터베이스 암호화 키를 알아보려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4afc1-119">If you want to learn the encryption state of a database and its associated database encryption keys, run the following statement:</span></span>  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 <span data-ttu-id="4afc1-120">이 단원에서 사용 된 Transact-sql 문에 대 한 자세한 내용은 [CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql), create [MASTER KEY &#40;](/sql/t-sql/statements/create-master-key-transact-sql)Transact-sql&#41;, [create CERTIFICATE &#40;transact-sql ](/sql/t-sql/statements/create-certificate-transact-sql)&#41;및 dm_database_encryption_keys [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4afc1-120">For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).</span></span>  
  
 <span data-ttu-id="4afc1-121">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="4afc1-121">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="4afc1-122">6단원: 온-프레미스의 원본 머신에서 Azure의 대상 머신으로 데이터베이스 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="4afc1-122">Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure</span></span>](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
