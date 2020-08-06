---
title: '3 단원: SQL Server 자격 증명 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 808438e544e3beb18b2e2afa9c399b5666277483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739921"
---
# <a name="lesson-3-create-a-sql-server-credential"></a><span data-ttu-id="1e545-102">3단원: SQL Server 자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="1e545-102">Lesson 3: Create a SQL Server Credential</span></span>
  <span data-ttu-id="1e545-103">이 단원에서는 Azure 저장소 계정에 액세스 하는 데 사용 되는 보안 정보를 저장 하는 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-103">In this lesson, you will create a credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="1e545-104">SQL Server 자격 증명은 SQL Server 외부의 리소스에 연결하는 데 필요한 인증 정보를 저장하는 데 사용되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-104">A SQL Server credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span> <span data-ttu-id="1e545-105">자격 증명에는 스토리지 컨테이너의 URI 경로와 공유 액세스 서명 키 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-105">The credential stores the URI path of the storage container and the shared access signature key values.</span></span> <span data-ttu-id="1e545-106">데이터 또는 로그 파일에서 사용하는 각 스토리지 컨테이너에 대해 컨테이너 경로와 일치하는 이름의 SQL Server 자격 증명을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-106">For each storage container used by a data or log file, you must create a SQL Server Credential whose name matches the container path.</span></span>  
  
 <span data-ttu-id="1e545-107">자격 증명에 대 한 일반 정보는 [자격 증명 &#40;데이터베이스 엔진&#41;](security/authentication-access/credentials-database-engine.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e545-107">For general information about credentials, see [Credentials &#40;Database Engine&#41;](security/authentication-access/credentials-database-engine.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e545-108">아래에 설명 된 SQL Server 자격 증명을 만들기 위한 요구 사항은 [Azure의 SQL Server 데이터 파일](databases/sql-server-data-files-in-microsoft-azure.md) 기능에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-108">The requirements for creating a SQL Server credential described below are specific to the [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md) feature.</span></span> <span data-ttu-id="1e545-109">Azure 스토리지에서 백업 프로세스를 위한 자격 증명을 만드는 방법에 대한 자세한 내용은 [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e545-109">For information on creating credentials for backup processes in Azure storage, see [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
 <span data-ttu-id="1e545-110">SQL Server 자격 증명을 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-110">To create a SQL Server Credential, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1e545-111">SQL Server Management Studio에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-111">Connect to SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="1e545-112">개체 탐색기에서 설치된 데이터베이스 엔진의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-112">In Object Explorer, connect to the instance of Database Engine installed.</span></span>  
  
3.  <span data-ttu-id="1e545-113">표준 도구 모음에서 새 쿼리를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-113">On the Standard tool bar, click New Query.</span></span>  
  
4.  <span data-ttu-id="1e545-114">다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-114">Copy and paste the following example into the query window, modify as needed.</span></span> <span data-ttu-id="1e545-115">다음 명령문은 저장소 컨테이너의 공유 액세스 인증서를 저장 하는 SQL Server 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-115">The following statement will create a SQL Server Credential to store your storage container's Shared Access Certificate.</span></span>  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     <span data-ttu-id="1e545-116">자세한 내용은 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql) SQL Server 온라인 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e545-116">For detailed information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server Books Online.</span></span>  
  
5.  <span data-ttu-id="1e545-117">사용할 수 있는 모든 자격 증명을 보려면 쿼리 창에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e545-117">To see all available credentials, you can run the following statement in the query window:</span></span>  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     <span data-ttu-id="1e545-118">Sys. 자격 증명에 대 한 자세한 내용은 [sys. 자격 증명 &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) SQL Server 온라인 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e545-118">For more information on sys.credentials, see [sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="1e545-119">**다음 단원:**</span><span class="sxs-lookup"><span data-stu-id="1e545-119">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="1e545-120">4단원: Azure Storage에서 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="1e545-120">Lesson 4: Create a database in Azure Storage</span></span>](lesson-3-database-backup-to-url.md)  
  
  
