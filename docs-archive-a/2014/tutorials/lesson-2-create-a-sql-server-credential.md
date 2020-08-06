---
title: '2 단원: SQL Server 자격 증명 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8b13c8d4d9e5937064cef5503ec64bfd6e4a2d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742704"
---
# <a name="lesson-2-create-a-sql-server-credential"></a><span data-ttu-id="842ff-102">2단원: SQL Server 자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="842ff-102">Lesson 2: Create a SQL Server Credential</span></span>
  <span data-ttu-id="842ff-103">**자격 증명:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 자격 증명은 SQL Server 외부의 리소스에 연결하는 데 필요한 인증 정보를 저장하는 데 사용되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-103">**Credential:** A [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="842ff-104">여기에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원 프로세스는 자격 증명을 사용 하 여 Azure Blob 저장소 서비스에 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-104">Here, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="842ff-105">자격 증명에는 스토리지 계정 이름과 스토리지 계정 **액세스 키** 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-105">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="842ff-106">만든 자격 증명은 BACKUP/RESTORE 문을 실행할 때 WITH CREDENTIAL 옵션에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-106">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="842ff-107">저장소 계정 **액세스 키**를 보고, 복사 하거나, 다시 생성 하는 방법에 대 한 자세한 내용은 [저장소 계정 액세스 키](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-107">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="842ff-108">자격 증명에 대 한 일반 정보는 [자격 증명](../relational-databases/security/authentication-access/credentials-database-engine.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-108">For general information about credentials, see [Credentials](../relational-databases/security/authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="842ff-109">자격 증명을 사용 하는 다른 예제에 대 한 자세한 내용은 [SQL Server 에이전트 프록시 만들기](../ssms/agent/create-a-sql-server-agent-proxy.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-109">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="842ff-110">아래에 설명 된 SQL Server 자격 증명을 만들기 위한 요구 사항은 SQL Server 백업 프로세스 ([URL에 백업 SQL Server](../relational-databases/backup-restore/sql-server-backup-to-url.md)하 고 [Azure에 대 한 관리 되는 백업 SQL Server](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md))에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-110">The requirements for creating a SQL Server credential described below are specific to SQL Server backup processes ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), and [SQL Server Managed  Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)).</span></span> <span data-ttu-id="842ff-111">Azure 스토리지에 액세스하여 백업을 쓰거나 읽을 때 SQL Server는 스토리지 계정 이름 및 액세스 키 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-111">SQL Server, when accessing Azure storage to write or read backups uses the storage account name and access key information.</span></span>  <span data-ttu-id="842ff-112">Azure 스토리지에 데이터베이스 파일을 저장하는 데 사용할 자격 증명 만들기에 대한 자세한 내용은 [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-112">For more information on creating credentials for storing database files in Azure storage, see [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)</span></span>  
  
## <a name="create-a-sql-server-credential"></a><span data-ttu-id="842ff-113">SQL Server 자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="842ff-113">Create a SQL Server Credential</span></span>  
 <span data-ttu-id="842ff-114">SQL Server 자격 증명을 만들려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-114">To create a SQL Server Credential, use the following steps:</span></span>  
  
1.  <span data-ttu-id="842ff-115">SQL Server Management Studio에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-115">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="842ff-116">개체 탐색기에서 AdventureWorks2012 데이터베이스가 설치된 데이터베이스 엔진의 인스턴스에 연결하거나 이 자습서에서 사용할 자신의 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-116">In Object Explorer, connect to the instance of Database Engine that has AdventureWorks2012 database installed, or use your own database you plan to use for this tutorial.</span></span>  
  
3.  <span data-ttu-id="842ff-117">**표준** 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-117">On the **Standard** tool bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="842ff-118">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-118">Copy and paste the following example into the query window, modify as needed.</span></span>  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     <span data-ttu-id="842ff-119">![SQL 자격 증명에 저장소 계정 매핑](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "SQL 자격 증명에 저장소 계정 매핑")</span><span class="sxs-lookup"><span data-stu-id="842ff-119">![mapping storage account to sql credentials](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
5.  <span data-ttu-id="842ff-120">T-SQL 문을 확인하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="842ff-120">Verify the T-SQL statement and click **Execute**.</span></span>  
  
 <span data-ttu-id="842ff-121">백업 개념 및 요구 사항에 대 한 Azure Blob storage 서비스에 대 한 자세한 내용은 [SQL Server 백업 및 복원 Azure Blob Storage 서비스](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="842ff-121">For more information about the Azure Blob storage service for backup concepts and requirements, see [SQL Server Backup and Restore with Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="842ff-122">다음 단원</span><span class="sxs-lookup"><span data-stu-id="842ff-122">Next Lesson</span></span>  
 <span data-ttu-id="842ff-123">[3 단원: Azure Blob Storage 서비스에 전체 데이터베이스 백업 작성](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)</span><span class="sxs-lookup"><span data-stu-id="842ff-123">[Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).</span></span>  
  
  
