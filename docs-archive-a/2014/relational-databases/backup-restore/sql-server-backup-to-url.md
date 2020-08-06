---
title: URL에 대한 SQL Server 백업 | Microsoft 문서
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6918a099e00b1de9e773320b5c6c0e4089859e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734195"
---
# <a name="sql-server-backup-to-url"></a><span data-ttu-id="776a5-102">URL에 대한 SQL Server 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-102">SQL Server Backup to URL</span></span>
  <span data-ttu-id="776a5-103">이 항목에서는 Azure Blob 저장소 서비스를 백업 대상으로 사용 하는 데 필요한 개념, 요구 사항 및 구성 요소를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-103">This topic introduces the concepts, requirements and components necessary to use the Azure Blob storage service as a backup destination.</span></span> <span data-ttu-id="776a5-104">백업 및 복원 기능은 디스크나 테이프를 사용하는 경우와 동일하거나 비슷하지만 몇 가지 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-104">The backup and restore functionality are same or similar to when using DISK or TAPE, with a few differences.</span></span> <span data-ttu-id="776a5-105">이러한 차이점과 주목할 만한 예외 및 몇 가지 코드 예가 이 항목에서 소개됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-105">The differences are and any notable exceptions, and a few code examples are included in this topic.</span></span>  
  
## <a name="requirements-components-and-concepts"></a><span data-ttu-id="776a5-106">요구 사항, 구성 요소 및 개념</span><span class="sxs-lookup"><span data-stu-id="776a5-106">Requirements, Components, and Concepts</span></span>  
 <span data-ttu-id="776a5-107">**섹션 내용**</span><span class="sxs-lookup"><span data-stu-id="776a5-107">**In this section:**</span></span>  
  
-   [<span data-ttu-id="776a5-108">보안</span><span class="sxs-lookup"><span data-stu-id="776a5-108">Security</span></span>](#security)  
  
-   [<span data-ttu-id="776a5-109">주요 구성 요소 및 개념 소개</span><span class="sxs-lookup"><span data-stu-id="776a5-109">Introduction to Key Components and Concepts</span></span>](#intorkeyconcepts)  
  
-   [<span data-ttu-id="776a5-110">Azure Blob Storage 서비스</span><span class="sxs-lookup"><span data-stu-id="776a5-110">Azure Blob Storage Service</span></span>](#Blob)  
  
-   [<span data-ttu-id="776a5-111">SQL Server 구성 요소</span><span class="sxs-lookup"><span data-stu-id="776a5-111">SQL Server Components</span></span>](#sqlserver)  
  
-   [<span data-ttu-id="776a5-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="776a5-112">Limitations</span></span>](#limitations)  
  
-   [<span data-ttu-id="776a5-113">Backup/Restore 문 지원</span><span class="sxs-lookup"><span data-stu-id="776a5-113">Support for Backup/Restore Statements</span></span>](#Support)  
  
-   [<span data-ttu-id="776a5-114">SQL Server Management Studio에서 백업 태스크 사용</span><span class="sxs-lookup"><span data-stu-id="776a5-114">Using Backup Task in SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [<span data-ttu-id="776a5-115">유지 관리 계획 마법사를 사용하여 URL로 SQL Server 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-115">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [<span data-ttu-id="776a5-116">SQL Server Management Studio를 사용하여 Azure Storage에서 복원</span><span class="sxs-lookup"><span data-stu-id="776a5-116">Restoring from Azure storage Using SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a><a name="security"></a> <span data-ttu-id="776a5-117">보안</span><span class="sxs-lookup"><span data-stu-id="776a5-117">Security</span></span>  
 <span data-ttu-id="776a5-118">다음은 Azure Blob 저장소 서비스로 백업 하거나 복원 하는 경우의 보안 고려 사항 및 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-118">The following are security considerations and requirements when backing up to or restoring from the Azure Blob storage services.</span></span>  
  
-   <span data-ttu-id="776a5-119">Azure Blob 저장소 서비스에 대 한 컨테이너를 만들 때 액세스 권한을 **개인**으로 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-119">When creating a container for the Azure Blob storage service, we recommend that you set the access to **private**.</span></span> <span data-ttu-id="776a5-120">액세스 권한을 프라이빗으로 설정하면 Azure 계정에 인증하는 데 필요한 정보를 제공할 수 있는 사용자 또는 계정으로 액세스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-120">Setting the access to private restricts the access to users or accounts able to provide the necessary information to authenticate to the Azure account.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="776a5-121">자격 증명에 저장 하려면 Azure 계정 이름 및 액세스 키 인증이 필요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-121">requires Azure account name and access key authentication to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential.</span></span> <span data-ttu-id="776a5-122">이 정보는 백업 또는 복원 작업을 수행할 때 Azure 계정에 인증 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-122">This information is used to authenticate to the Azure account when it performs backup or restore operations.</span></span>  
  
-   <span data-ttu-id="776a5-123">BACKUP 또는 RESTORE 명령을 실행하는 데 사용되는 사용자 계정은 **모든 자격 증명 변경** 권한이 있는 **db_backup operator** 데이터베이스 역할에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-123">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
###  <a name="introduction-to-key-components-and-concepts"></a><a name="intorkeyconcepts"></a><span data-ttu-id="776a5-124">주요 구성 요소 및 개념 소개</span><span class="sxs-lookup"><span data-stu-id="776a5-124">Introduction to Key Components and Concepts</span></span>  
 <span data-ttu-id="776a5-125">다음 두 섹션에서는 azure blob storage 서비스와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure blob 저장소 서비스로 백업 하거나 복원할 때 사용 되는 구성 요소를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-125">The following two sections introduce the Azure Blob storage service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components used when backing up to or restoring from the Azure Blob storage service.</span></span> <span data-ttu-id="776a5-126">Azure Blob 저장소 서비스에 대 한 백업 또는 복원 작업을 수행 하기 위해 구성 요소와 구성 요소 간의 상호 작용을 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-126">It is important to understand the components and the interaction between them to do a backup to or restore from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="776a5-127">이 프로세스의 첫 번째 단계는 Azure 계정을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-127">Creating an Azure account is the first step to this process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="776a5-128">는 **Azure storage 계정 이름** 및 해당 **액세스 키** 값을 사용 하 여 저장소 서비스에 대 한 blob을 인증 하 고 쓰고 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-128">uses the **Azure storage account name** and its **access key** values to authenticate and write and read blobs to the storage service.</span></span> <span data-ttu-id="776a5-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자격 증명은 이 인증 정보를 저장하며 백업 또는 복원 작업 중에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-129">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential stores this authentication information and is used during the backup or restore operations.</span></span> <span data-ttu-id="776a5-130">저장소 계정을 만들고 간단한 복원을 수행 하는 전체 연습은 [자습서를 사용 하 여 SQL Server 백업 및 복원에 대 한 Azure Storage 서비스 사용 자습서](https://go.microsoft.com/fwlink/?LinkId=271615)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-130">For a complete walkthrough of creating a storage account and performing a simple restore, see [Tutorial Using Azure Storage Service for SQL Server Backup and Restore](https://go.microsoft.com/fwlink/?LinkId=271615).</span></span>  
  
 <span data-ttu-id="776a5-131">![SQL 자격 증명에 저장소 계정 매핑](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "SQL 자격 증명에 저장소 계정 매핑")</span><span class="sxs-lookup"><span data-stu-id="776a5-131">![mapping storage account to sql credentials](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
###  <a name="azure-blob-storage-service"></a><a name="Blob"></a><span data-ttu-id="776a5-132">Azure Blob Storage 서비스</span><span class="sxs-lookup"><span data-stu-id="776a5-132">Azure Blob Storage Service</span></span>  
 <span data-ttu-id="776a5-133">**스토리지 계정:** 스토리지 계정은 모든 스토리지 서비스를 사용하기 위한 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-133">**Storage Account:** The storage account is the starting point for all storage services.</span></span> <span data-ttu-id="776a5-134">Azure Blob Storage 서비스에 액세스 하려면 먼저 Azure Storage 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-134">To access the Azure Blob Storage service, first create an Azure storage account.</span></span> <span data-ttu-id="776a5-135">Azure Blob Storage 서비스와 해당 구성 요소를 인증 하려면 **저장소 계정 이름** 및 해당 **액세스 키** 속성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-135">The **storage account name** and its **access key** properties are required to authenticate to the Azure Blob Storage service and its components.</span></span>  
  
 <span data-ttu-id="776a5-136">**컨테이너:** 컨테이너는 Blob 집합의 그룹화를 제공 하며 Blob을 무제한으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-136">**Container:** A container provides a grouping of a set of Blobs, and can store an unlimited number of Blobs.</span></span> <span data-ttu-id="776a5-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Azure Blob service에 백업을 쓰려면 적어도 루트 컨테이너가 만들어져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-137">To write a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to the Azure Blob service, you must have at least the root container created.</span></span>  
  
 <span data-ttu-id="776a5-138">**Blob:** 모든 형식과 크기의 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-138">**Blob:** A file of any type and size.</span></span> <span data-ttu-id="776a5-139">Azure Blob 저장소 서비스에는 블록 및 페이지 blob 이라는 두 가지 유형의 blob을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-139">There are two types of blobs that can be stored in the Azure Blob storage service: block and page blobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="776a5-140">백업에서는 페이지 Blob을 Blob 유형으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-140">backup uses page Blobs as the Blob type.</span></span> <span data-ttu-id="776a5-141">Blob은 다음 URL 형식을 사용 하 여 주소를 지정할 수 있습니다. https:// \<storage account> . blob.core.windows.net/\<container>/\<blob></span><span class="sxs-lookup"><span data-stu-id="776a5-141">Blobs are addressable using the following URL format: https://\<storage account>.blob.core.windows.net/\<container>/\<blob></span></span>  
  
 <span data-ttu-id="776a5-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span><span class="sxs-lookup"><span data-stu-id="776a5-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span></span>  
  
 <span data-ttu-id="776a5-143">Azure Blob 저장소 서비스에 대 한 자세한 내용은 [Azure Blob Storage 서비스를 사용 하는 방법](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-143">For more information about the Azure Blob storage service, see [How to use the Azure Blob Storage Service](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span></span>  
  
 <span data-ttu-id="776a5-144">페이지 Blob에 대한 자세한 내용은 [블록 및 페이지 Blob 이해](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-144">For more information about page Blobs, see [Understanding Block and Page Blobs](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span></span>  
  
###  <a name="ssnoversion-components"></a><a name="sqlserver"></a> <span data-ttu-id="776a5-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소</span><span class="sxs-lookup"><span data-stu-id="776a5-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components</span></span>  
 <span data-ttu-id="776a5-146">**URL:** URL은 고유한 백업 파일에 대한 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-146">**URL:** A URL specifies a Uniform Resource Identifier (URI) to a unique backup file.</span></span> <span data-ttu-id="776a5-147">URL은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 파일의 위치와 이름을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-147">The URL is used to provide the location and name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup file.</span></span> <span data-ttu-id="776a5-148">이 구현에서 올바른 URL은 Azure storage 계정의 페이지 Blob을 가리키는 유일한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-148">In this implementation, the only valid URL is one that points to a page Blob in an Azure storage account.</span></span> <span data-ttu-id="776a5-149">URL은 컨테이너가 아닌 실제 Blob을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-149">The URL must point to an actual Blob, not just a container.</span></span> <span data-ttu-id="776a5-150">Blob이 없으면 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-150">If the Blob does not exist, it is created.</span></span> <span data-ttu-id="776a5-151">기존 Blob이 지정 된 경우 "WITH FORMAT" 옵션을 지정 하지 않으면 백업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-151">If an existing Blob is specified, BACKUP fails, unless the "WITH FORMAT" option is specified.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="776a5-152">백업 파일을 복사 하 여 Azure Blob storage 서비스에 업로드 하도록 선택한 경우 페이지 Blob을 저장소 옵션으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-152">If you choose to copy and upload a backup file to the Azure Blob storage service, use page blob as your storage option.</span></span> <span data-ttu-id="776a5-153">블록 Blob에서 복원은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-153">Restores from Block Blobs are not supported.</span></span> <span data-ttu-id="776a5-154">블록 Blob 유형에서 RESTORE는 오류와 함께 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-154">RESTORE from a block blob type fails with an error.</span></span>  
  
 <span data-ttu-id="776a5-155">예제 URL 값은 http [s]://ACCOUNTNAME.Blob.core.windows.net/ \<CONTAINER> / \<FILENAME.bak> 입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-155">Here is a sample URL value: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<CONTAINER>/\<FILENAME.bak>.</span></span> <span data-ttu-id="776a5-156">HTTPS는 필수 사항은 아니지만 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-156">HTTPS is not required, but is recommended.</span></span>  
  
 <span data-ttu-id="776a5-157">**자격 증명:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자격 증명은 SQL Server 외부의 리소스에 연결하는 데 필요한 인증 정보를 저장하는 데 사용되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-157">**Credential:** A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="776a5-158">여기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 및 복원 프로세스는 자격 증명을 사용 하 여 Azure Blob 저장소 서비스에 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-158">Here, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="776a5-159">자격 증명에는 스토리지 계정 이름과 스토리지 계정 **액세스 키** 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-159">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="776a5-160">만든 자격 증명은 BACKUP/RESTORE 문을 실행할 때 WITH CREDENTIAL 옵션에 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-160">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="776a5-161">저장소 계정 **액세스 키**를 보고, 복사 하거나, 다시 생성 하는 방법에 대 한 자세한 내용은 [저장소 계정 액세스 키](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-161">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="776a5-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자격 증명을 만드는 방법에 대한 단계별 지침은 이 항목 뒷부분의 [Create a Credential](#credential) 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="776a5-162">For step by step instructions about how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential, see [Create a Credential](#credential) example later in this topic.</span></span>  
  
 <span data-ttu-id="776a5-163">자격 증명에 대한 자세한 내용은 [자격 증명](../security/authentication-access/credentials-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-163">For general information about credentials, see [Credentials](../security/authentication-access/credentials-database-engine.md)</span></span>  
  
 <span data-ttu-id="776a5-164">자격 증명을 사용 하는 다른 예제에 대 한 자세한 내용은 [SQL Server 에이전트 프록시 만들기](../../ssms/agent/create-a-sql-server-agent-proxy.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-164">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
###  <a name="limitations"></a><a name="limitations"></a> <span data-ttu-id="776a5-165">제한 사항</span><span class="sxs-lookup"><span data-stu-id="776a5-165">Limitations</span></span>  
  
-   <span data-ttu-id="776a5-166">Premium 스토리지로 백업은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-166">Backup to premium storage is not supported.</span></span>  
  
-   <span data-ttu-id="776a5-167">지원되는 최대 백업 크기는 1TB입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-167">The maximum backup size supported is 1 TB.</span></span>  
  
-   <span data-ttu-id="776a5-168">TSQL, SMO 또는 PowerShell cmdlet을 사용하여 백업 또는 복원 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-168">You can issue backup or restore statements by using TSQL, SMO, or PowerShell cmdlets.</span></span> <span data-ttu-id="776a5-169">SQL Server Management Studio 백업 또는 복원 마법사를 사용 하 여 Azure Blob 저장소 서비스에 백업 하거나 복원 하는 기능은 현재 사용 하도록 설정 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-169">A backup to or restoring from the Azure Blob storage service by using SQL Server Management Studio Backup or Restore wizard is not currently enabled.</span></span>  
  
-   <span data-ttu-id="776a5-170">논리적 디바이스 이름을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-170">Creating a logical device name is not supported.</span></span> <span data-ttu-id="776a5-171">따라서 SQL Server Management Studio나 sp_dumpdevice를 사용하여 URL을 백업 디바이스로 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-171">So adding URL as a backup device using sp_dumpdevice or through SQL Server Management Studio is not supported.</span></span>  
  
-   <span data-ttu-id="776a5-172">기존 백업 Blob에 추가는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-172">Appending to existing backup blobs is not supported.</span></span> <span data-ttu-id="776a5-173">기존 Blob으로 백업은 WITH FORMAT 옵션을 사용하여 덮어쓸 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-173">Backups to an existing Blob can only be overwritten by using the WITH FORMAT option.</span></span>  
  
-   <span data-ttu-id="776a5-174">단일 백업 작업에서 여러 blob으로 백업은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-174">Backup to multiple blobs in a single backup operation is not supported.</span></span> <span data-ttu-id="776a5-175">예를 들어 다음은 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-175">For example, the following returns an error:</span></span>  
  
    ```sql
    BACKUP DATABASE AdventureWorks2012
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'
          WITH CREDENTIAL = 'mycredential'
         ,STATS = 5;  
    GO
    ```  
  
-   <span data-ttu-id="776a5-176">`BACKUP`에 블록 크기 지정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-176">Specifying a block size with `BACKUP` is not supported.</span></span>  
  
-   <span data-ttu-id="776a5-177">`MAXTRANSFERSIZE` 지정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-177">Specifying `MAXTRANSFERSIZE` is not supported.</span></span>  
  
-   <span data-ttu-id="776a5-178">`RETAINDAYS`와 `EXPIREDATE` 백업 세트 옵션 지정은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-178">Specifying backupset options - `RETAINDAYS` and `EXPIREDATE` are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="776a5-179">에서는 백업 디바이스 이름이 최대 259자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-179">has a maximum limit of 259 characters for a backup device name.</span></span> <span data-ttu-id="776a5-180">BACKUP TO URL에서 URL - ‘ https://.blob.core.windows.net//.bak ’를 지정하는 데 사용되는 필수 요소에 36자가 사용되며, 계정, 컨테이너 및 blob 이름에 사용할 수 있는 문자는 223자입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-180">The BACKUP TO URL consumes 36 characters for the required elements used to specify the URL - 'https://.blob.core.windows.net//.bak', leaving 223 characters for account, container, and blob names put together.</span></span>  
  
###  <a name="support-for-backuprestore-statements"></a><a name="Support"></a> <span data-ttu-id="776a5-181">Backup/Restore 문 지원</span><span class="sxs-lookup"><span data-stu-id="776a5-181">Support for Backup/Restore Statements</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="776a5-182">Backup/Restore 문</span><span class="sxs-lookup"><span data-stu-id="776a5-182">Backup/Restore Statement</span></span>|<span data-ttu-id="776a5-183">지원됨</span><span class="sxs-lookup"><span data-stu-id="776a5-183">Supported</span></span>|<span data-ttu-id="776a5-184">예외</span><span class="sxs-lookup"><span data-stu-id="776a5-184">Exceptions</span></span>|<span data-ttu-id="776a5-185">주석</span><span class="sxs-lookup"><span data-stu-id="776a5-185">Comments</span></span>|  
|<span data-ttu-id="776a5-186">BACKUP</span><span class="sxs-lookup"><span data-stu-id="776a5-186">BACKUP</span></span>|<span data-ttu-id="776a5-187">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-187">&#x2713;</span></span>|<span data-ttu-id="776a5-188">BLOCKSIZE 및 MAXTRANSFERSIZE는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-188">BLOCKSIZE, and MAXTRANSFERSIZE are not supported.</span></span>|<span data-ttu-id="776a5-189">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-189">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-190">RESTORE</span><span class="sxs-lookup"><span data-stu-id="776a5-190">RESTORE</span></span>|<span data-ttu-id="776a5-191">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-191">&#x2713;</span></span>||<span data-ttu-id="776a5-192">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-192">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-193">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-193">RESTORE FILELISTONLY</span></span>|<span data-ttu-id="776a5-194">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-194">&#x2713;</span></span>||<span data-ttu-id="776a5-195">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-195">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-196">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-196">RESTORE HEADERONLY</span></span>|<span data-ttu-id="776a5-197">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-197">&#x2713;</span></span>||<span data-ttu-id="776a5-198">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-198">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-199">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-199">RESTORE LABELONLY</span></span>|<span data-ttu-id="776a5-200">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-200">&#x2713;</span></span>||<span data-ttu-id="776a5-201">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-201">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-202">RESTORE VERIFYONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-202">RESTORE VERIFYONLY</span></span>|<span data-ttu-id="776a5-203">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-203">&#x2713;</span></span>||<span data-ttu-id="776a5-204">WITH CREDENTIAL 지정 필요</span><span class="sxs-lookup"><span data-stu-id="776a5-204">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="776a5-205">RESTORE REWINDONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-205">RESTORE REWINDONLY</span></span>|<span data-ttu-id="776a5-206">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-206">&#x2713;</span></span>|||  
  
 <span data-ttu-id="776a5-207">구문과 Backup 문에 대한 자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-207">For syntax and general information about backup statements, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="776a5-208">구문과 Restore 문에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-208">For syntax and general information about restore statements, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
### <a name="support-for-backup-arguments"></a><span data-ttu-id="776a5-209">Backup 인수 지원</span><span class="sxs-lookup"><span data-stu-id="776a5-209">Support for Backup Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="776a5-210">인수</span><span class="sxs-lookup"><span data-stu-id="776a5-210">Argument</span></span>|<span data-ttu-id="776a5-211">지원됨</span><span class="sxs-lookup"><span data-stu-id="776a5-211">Supported</span></span>|<span data-ttu-id="776a5-212">예외</span><span class="sxs-lookup"><span data-stu-id="776a5-212">Exception</span></span>|<span data-ttu-id="776a5-213">주석</span><span class="sxs-lookup"><span data-stu-id="776a5-213">Comments</span></span>|  
|<span data-ttu-id="776a5-214">DATABASE</span><span class="sxs-lookup"><span data-stu-id="776a5-214">DATABASE</span></span>|<span data-ttu-id="776a5-215">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-215">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-216">LOG</span><span class="sxs-lookup"><span data-stu-id="776a5-216">LOG</span></span>|<span data-ttu-id="776a5-217">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-217">&#x2713;</span></span>|||  
||  
|<span data-ttu-id="776a5-218">TO (URL)</span><span class="sxs-lookup"><span data-stu-id="776a5-218">TO (URL)</span></span>|<span data-ttu-id="776a5-219">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-219">&#x2713;</span></span>|<span data-ttu-id="776a5-220">DISK 및 TAPE와 달리 URL은 논리적 이름 지정 및 작성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-220">Unlike DISK and TAPE, URL does not support specifying or creating a logical name.</span></span>|<span data-ttu-id="776a5-221">이 인수는 백업 파일에 대한 URL 경로를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-221">This argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="776a5-222">MIRROR TO</span><span class="sxs-lookup"><span data-stu-id="776a5-222">MIRROR TO</span></span>|<span data-ttu-id="776a5-223">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-223">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-224">**WITH 옵션:**</span><span class="sxs-lookup"><span data-stu-id="776a5-224">**WITH OPTIONS:**</span></span>||||  
|<span data-ttu-id="776a5-225">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="776a5-225">CREDENTIAL</span></span>|<span data-ttu-id="776a5-226">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-226">&#x2713;</span></span>||<span data-ttu-id="776a5-227">WITH CREDENTIAL은 BACKUP TO URL 옵션을 사용 하 여 Azure Blob 저장소 서비스로 백업할 때만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-227">WITH CREDENTIAL is only supported when using BACKUP TO URL option to back up to the Azure Blob storage service.</span></span>|  
|<span data-ttu-id="776a5-228">DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="776a5-228">DIFFERENTIAL</span></span>|<span data-ttu-id="776a5-229">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-229">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-230">COPY_ONLY</span><span class="sxs-lookup"><span data-stu-id="776a5-230">COPY_ONLY</span></span>|<span data-ttu-id="776a5-231">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-231">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-232">COMPRESSION&#124;NO_COMPRESSION</span><span class="sxs-lookup"><span data-stu-id="776a5-232">COMPRESSION&#124;NO_COMPRESSION</span></span>|<span data-ttu-id="776a5-233">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-233">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-234">설명</span><span class="sxs-lookup"><span data-stu-id="776a5-234">DESCRIPTION</span></span>|<span data-ttu-id="776a5-235">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-235">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-236">NAME</span><span class="sxs-lookup"><span data-stu-id="776a5-236">NAME</span></span>|<span data-ttu-id="776a5-237">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-237">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-238">EXPIREDATE &#124; RETAINDAYS</span><span class="sxs-lookup"><span data-stu-id="776a5-238">EXPIREDATE &#124; RETAINDAYS</span></span>|<span data-ttu-id="776a5-239">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-239">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-240">NOINIT &#124; INIT</span><span class="sxs-lookup"><span data-stu-id="776a5-240">NOINIT &#124; INIT</span></span>|<span data-ttu-id="776a5-241">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-241">&#x2713;</span></span>||<span data-ttu-id="776a5-242">이 옵션은 사용 시 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-242">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="776a5-243">Blob에 추가는 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-243">Appending to blobs is not possible.</span></span> <span data-ttu-id="776a5-244">백업을 덮어쓰려면 FORMAT 인수를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="776a5-244">To overwrite a backup use the FORMAT argument.</span></span>|  
|<span data-ttu-id="776a5-245">NOSKIP &#124; SKIP</span><span class="sxs-lookup"><span data-stu-id="776a5-245">NOSKIP &#124; SKIP</span></span>|<span data-ttu-id="776a5-246">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-246">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-247">NOFORMAT &#124; FORMAT</span><span class="sxs-lookup"><span data-stu-id="776a5-247">NOFORMAT &#124; FORMAT</span></span>|<span data-ttu-id="776a5-248">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-248">&#x2713;</span></span>||<span data-ttu-id="776a5-249">이 옵션은 사용 시 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-249">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="776a5-250">WITH FORMAT을 지정하지 않으면 기존 blob으로 백업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-250">A backup taken to an existing blob fails unless WITH FORMAT is specified.</span></span> <span data-ttu-id="776a5-251">WITH FORMAT을 지정하면 기존 blob을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-251">The existing blob is overwritten when WITH FORMAT is specified.</span></span>|  
|<span data-ttu-id="776a5-252">MEDIADESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="776a5-252">MEDIADESCRIPTION</span></span>|<span data-ttu-id="776a5-253">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-253">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-254">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="776a5-254">MEDIANAME</span></span>|<span data-ttu-id="776a5-255">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-255">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-256">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="776a5-256">BLOCKSIZE</span></span>|<span data-ttu-id="776a5-257">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-257">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-258">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="776a5-258">BUFFERCOUNT</span></span>|<span data-ttu-id="776a5-259">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-259">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-260">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="776a5-260">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="776a5-261">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-261">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-262">NO_CHECKSUM &#124; CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="776a5-262">NO_CHECKSUM &#124; CHECKSUM</span></span>|<span data-ttu-id="776a5-263">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-263">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="776a5-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="776a5-265">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-265">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-266">통계</span><span class="sxs-lookup"><span data-stu-id="776a5-266">STATS</span></span>|<span data-ttu-id="776a5-267">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-267">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-268">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="776a5-268">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="776a5-269">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-269">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-270">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="776a5-270">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="776a5-271">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-271">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-272">NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="776a5-272">NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="776a5-273">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-273">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-274">NO_TRUNCATE</span><span class="sxs-lookup"><span data-stu-id="776a5-274">NO_TRUNCATE</span></span>|<span data-ttu-id="776a5-275">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-275">&#x2713;</span></span>|||  
  
 <span data-ttu-id="776a5-276">Backup 인수에 대한 자세한 내용은 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-276">For more information about backup arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="support-for-restore-arguments"></a><span data-ttu-id="776a5-277">Restore 인수 지원</span><span class="sxs-lookup"><span data-stu-id="776a5-277">Support for Restore Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="776a5-278">인수</span><span class="sxs-lookup"><span data-stu-id="776a5-278">Argument</span></span>|<span data-ttu-id="776a5-279">지원됨</span><span class="sxs-lookup"><span data-stu-id="776a5-279">Supported</span></span>|<span data-ttu-id="776a5-280">예외</span><span class="sxs-lookup"><span data-stu-id="776a5-280">Exceptions</span></span>|<span data-ttu-id="776a5-281">주석</span><span class="sxs-lookup"><span data-stu-id="776a5-281">Comments</span></span>|  
|<span data-ttu-id="776a5-282">DATABASE</span><span class="sxs-lookup"><span data-stu-id="776a5-282">DATABASE</span></span>|<span data-ttu-id="776a5-283">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-283">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-284">LOG</span><span class="sxs-lookup"><span data-stu-id="776a5-284">LOG</span></span>|<span data-ttu-id="776a5-285">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-285">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-286">FROM (URL)</span><span class="sxs-lookup"><span data-stu-id="776a5-286">FROM (URL)</span></span>|<span data-ttu-id="776a5-287">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-287">&#x2713;</span></span>||<span data-ttu-id="776a5-288">FROM URL 인수는 백업 파일에 대한 URL 경로를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-288">The FROM URL argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="776a5-289">**WITH Options:**</span><span class="sxs-lookup"><span data-stu-id="776a5-289">**WITH Options:**</span></span>||||  
|<span data-ttu-id="776a5-290">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="776a5-290">CREDENTIAL</span></span>|<span data-ttu-id="776a5-291">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-291">&#x2713;</span></span>||<span data-ttu-id="776a5-292">WITH CREDENTIAL은 RESTORE FROM URL 옵션을 사용 하 여 Azure Blob Storage 서비스에서 복원할 때만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-292">WITH CREDENTIAL is only supported when using RESTORE FROM URL option to restore from Azure Blob Storage service.</span></span>|  
|<span data-ttu-id="776a5-293">PARTIAL</span><span class="sxs-lookup"><span data-stu-id="776a5-293">PARTIAL</span></span>|<span data-ttu-id="776a5-294">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-294">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="776a5-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="776a5-296">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-296">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-297">LOADHISTORY</span><span class="sxs-lookup"><span data-stu-id="776a5-297">LOADHISTORY</span></span>|<span data-ttu-id="776a5-298">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-298">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-299">MOVE</span><span class="sxs-lookup"><span data-stu-id="776a5-299">MOVE</span></span>|<span data-ttu-id="776a5-300">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-300">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-301">REPLACE</span><span class="sxs-lookup"><span data-stu-id="776a5-301">REPLACE</span></span>|<span data-ttu-id="776a5-302">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-302">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-303">RESTART</span><span class="sxs-lookup"><span data-stu-id="776a5-303">RESTART</span></span>|<span data-ttu-id="776a5-304">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-304">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-305">RESTRICTED_USER</span><span class="sxs-lookup"><span data-stu-id="776a5-305">RESTRICTED_USER</span></span>|<span data-ttu-id="776a5-306">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-306">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-307">FILE</span><span class="sxs-lookup"><span data-stu-id="776a5-307">FILE</span></span>|<span data-ttu-id="776a5-308">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-308">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-309">PASSWORD</span><span class="sxs-lookup"><span data-stu-id="776a5-309">PASSWORD</span></span>|<span data-ttu-id="776a5-310">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-310">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-311">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="776a5-311">MEDIANAME</span></span>|<span data-ttu-id="776a5-312">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-312">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-313">MEDIAPASSWORD</span><span class="sxs-lookup"><span data-stu-id="776a5-313">MEDIAPASSWORD</span></span>|<span data-ttu-id="776a5-314">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-314">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-315">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="776a5-315">BLOCKSIZE</span></span>|<span data-ttu-id="776a5-316">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-316">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-317">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="776a5-317">BUFFERCOUNT</span></span>|<span data-ttu-id="776a5-318">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-318">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-319">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="776a5-319">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="776a5-320">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-320">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-321">CHECKSUM &#124; NO_CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="776a5-321">CHECKSUM &#124; NO_CHECKSUM</span></span>|<span data-ttu-id="776a5-322">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-322">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="776a5-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="776a5-324">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-324">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-325">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="776a5-325">FILESTREAM</span></span>|<span data-ttu-id="776a5-326">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-326">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-327">통계</span><span class="sxs-lookup"><span data-stu-id="776a5-327">STATS</span></span>|<span data-ttu-id="776a5-328">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-328">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-329">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="776a5-329">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="776a5-330">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-330">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-331">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="776a5-331">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="776a5-332">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-332">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-333">KEEP_REPLICATION</span><span class="sxs-lookup"><span data-stu-id="776a5-333">KEEP_REPLICATION</span></span>|<span data-ttu-id="776a5-334">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-334">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-335">KEEP_CDC</span><span class="sxs-lookup"><span data-stu-id="776a5-335">KEEP_CDC</span></span>|<span data-ttu-id="776a5-336">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-336">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span><span class="sxs-lookup"><span data-stu-id="776a5-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span></span>|<span data-ttu-id="776a5-338">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-338">&#x2713;</span></span>|||  
|<span data-ttu-id="776a5-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span><span class="sxs-lookup"><span data-stu-id="776a5-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span></span>|<span data-ttu-id="776a5-340">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="776a5-340">&#x2713;</span></span>|||  
  
 <span data-ttu-id="776a5-341">Restore 인수에 대한 자세한 내용은 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-341">For more information about Restore arguments, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
##  <a name="using-backup-task-in-sql-server-management-studio"></a><a name="BackupTaskSSMS"></a><span data-ttu-id="776a5-342">SQL Server Management Studio에서 백업 작업 사용</span><span class="sxs-lookup"><span data-stu-id="776a5-342">Using Backup Task in SQL Server Management Studio</span></span>  
 <span data-ttu-id="776a5-343">SQL Server Management Studio의 백업 태스크는 대상 옵션 중 하나로 URL을 포함 하 고 SQL 자격 증명과 같은 Azure storage에 백업 하는 데 필요한 다른 지원 개체를 포함 하도록 향상 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-343">The Backup task in SQL Server Management Studio has been enhanced to include URL as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span>  
  
 <span data-ttu-id="776a5-344">다음 단계에서는 Azure 저장소로 백업할 수 있도록 데이터베이스 백업 태스크에 대 한 변경 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-344">The following steps describe the changes made to the Back Up Database task to allow for backing up to Azure storage.:</span></span>  
  
1.  <span data-ttu-id="776a5-345">SQL Server Management Studio를 시작하고 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-345">Start SQL Server Management Studio and connect to the SQL Server instance.</span></span>  <span data-ttu-id="776a5-346">백업할 데이터베이스를 선택 하 고 **작업**을 마우스 오른쪽 단추로 클릭 한 다음 **백업**...을 선택 합니다. 그러면 데이터베이스 백업 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-346">Select a database you want to backup, and right click on **Tasks**, and select **Back Up..**. This opens the Back Up Database dialog box.</span></span>  
  
2.  <span data-ttu-id="776a5-347">일반 페이지에서 **URL** 옵션은 Azure storage에 백업을 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-347">On the general page the **URL** option is used to create a backup to Azure storage.</span></span> <span data-ttu-id="776a5-348">이 옵션을 선택하면 이 페이지에서 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-348">When you select this option, you see other options enabled on this page:</span></span>  
  
    1.  <span data-ttu-id="776a5-349">**파일 이름:** 백업 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-349">**File Name:** Name of the backup file.</span></span>  
  
    2.  <span data-ttu-id="776a5-350">**SQL 자격 증명:** 기존 SQL Server 자격 증명을 지정하거나, SQL 자격 증명 상자 옆의 **만들기** 를 클릭하여 새로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-350">**SQL Credential:** You can either specify an existing SQL Server Credential, or can create a new one by clicking on the **Create** next to the SQL Credential box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="776a5-351">**만들기** 를 클릭하면 열리는 대화 상자에서는 관리 인증서나 구독용 게시 프로필이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-351">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="776a5-352">SQL Server는 현재 프로필 버전 2.0 게시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-352">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="776a5-353">게시 프로필의 지원되는 버전을 다운로드하려면 [게시 프로필 2.0 다운로드](https://go.microsoft.com/fwlink/?LinkId=396421)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-353">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
        >   
        >  <span data-ttu-id="776a5-354">관리 인증서나 게시 프로필에 액세스할 수 없는 경우 Transact-SQL이나 SQL Server Management Studio를 사용하여 스토리지 계정 이름을 지정하고 키 정보에 액세스하여 SQL 자격 증명을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-354">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="776a5-355">[자격 증명 만들기](#credential) 섹션의 예제 코드를 보고 Transact-SQL을 사용하여 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-355">See the sample code in the [Create a Credential](#credential) section to create a credential using Transact-SQL.</span></span> <span data-ttu-id="776a5-356">또는 SQL Server Management Studio를 사용하여 데이터베이스 엔진 인스턴스에서 **보안**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **자격 증명**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-356">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="776a5-357">**ID** 에 대한 스토리지 계정 이름을 지정하고 **암호** 필드에 액세스 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-357">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
    3.  <span data-ttu-id="776a5-358">**Azure 저장소 컨테이너:** 백업 파일을 저장할 Azure 저장소 컨테이너의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-358">**Azure storage container:** The name of the Azure storage container to store the backup files.</span></span>  
  
    4.  <span data-ttu-id="776a5-359">**URL 접두사:** 이전 단계에서 설명하는 필드에서 지정된 정보를 사용하여 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-359">**URL prefix:** This is built automatically using the information specified in the fields described in the previous steps.</span></span> <span data-ttu-id="776a5-360">이 값을 수동으로 편집하는 경우 이전에 제공한 다른 정보와 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-360">If you do edit this value manually, make sure it matches with the other information you provided previously.</span></span> <span data-ttu-id="776a5-361">예를 들어 스토리지 URL을 수정하는 경우 SQL 자격 증명이 동일한 스토리지 계정에 인증하도록 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-361">For example if you modify the storage URL, make sure the SQL Credential is set to authenticate to the same storage account.</span></span>  
  
 <span data-ttu-id="776a5-362">URL 을 대상으로 선택하는 경우 **미디어 옵션** 페이지의 특정 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-362">When you select URL as the destination, certain options in the **Media Options** page are disabled.</span></span>  <span data-ttu-id="776a5-363">다음 항목에서는 데이터베이스 백업 대화 상자에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-363">The following topics have more information on the Back Up Database dialog:</span></span>  
  
 [<span data-ttu-id="776a5-364">데이터베이스 백업&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-364">Back Up Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="776a5-365">데이터베이스 백업&#40;미디어 옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-365">Back Up Database &#40;Media Options Page&#41;</span></span>](back-up-database-media-options-page.md)  
  
 [<span data-ttu-id="776a5-366">데이터베이스 백업&#40;백업 옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-366">Back Up Database &#40;Backup Options Page&#41;</span></span>](back-up-database-backup-options-page.md)  
  
 [<span data-ttu-id="776a5-367">자격 증명 만들기 - Azure Storage 인증</span><span class="sxs-lookup"><span data-stu-id="776a5-367">Create Credential - Authenticate to Azure Storage</span></span>](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="sql-server-backup-to-url-using-maintenance-plan-wizard"></a><a name="MaintenanceWiz"></a><span data-ttu-id="776a5-368">유지 관리 계획 마법사를 사용 하 여 URL에 백업 SQL Server</span><span class="sxs-lookup"><span data-stu-id="776a5-368">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>  
 <span data-ttu-id="776a5-369">이전에 설명한 백업 작업과 마찬가지로, 대상 옵션 중 하나로 **URL** 을 포함 하 고 SQL 자격 증명과 같은 Azure storage로 백업 하는 데 필요한 다른 지원 개체를 포함 하도록 SQL Server Management Studio의 유지 관리 계획 마법사가 향상 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-369">Similar to the backup task described previously, the Maintenance Plan Wizard in SQL Server Management Studio has been enhanced to include **URL** as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span> <span data-ttu-id="776a5-370">자세한 내용은 **Using Maintenance Plan Wizard** 의 [백업 태스크 정의](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776a5-370">For more information, see  the **Define Backup Tasks** section in [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).</span></span>  
  
##  <a name="restoring-from-azure-storage-using-sql-server-management-studio"></a><a name="RestoreSSMS"></a><span data-ttu-id="776a5-371">SQL Server Management Studio를 사용 하 여 Azure storage에서 복원</span><span class="sxs-lookup"><span data-stu-id="776a5-371">Restoring from Azure storage Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="776a5-372">데이터베이스를 복원하는 경우 **URL** 이 복원할 원본 디바이스로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-372">If you are restoring a database, **URL** is included as the device to restore from.</span></span> <span data-ttu-id="776a5-373">다음 단계에서는 Azure storage에서 복원할 수 있도록 복원 작업의 변경 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-373">Following steps describe the changes in the Restore task to allow restoring from Azure storage:</span></span>  
  
1.  <span data-ttu-id="776a5-374">SQL Server Management Studio에 있는 복원 태스크의 **일반** 페이지에서 **디바이스** 를 선택하면 **URL** 이 백업 미디어 유형으로 포함된 **백업 디바이스 선택** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-374">When you select **Devices** in the **General** page of the Restore task in SQL Server Management Studio, this takes you to the **Select backup devices** dialog box which includes **URL** as a backup media type.</span></span>  
  
2.  <span data-ttu-id="776a5-375">**URL** 을 선택하고 **추가**를 클릭하면 **Azure 스토리지에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-375">When you select **URL** and click **Add**, this opens the **Connect to Azure storage** dialog.</span></span> <span data-ttu-id="776a5-376">Azure storage에 인증 하기 위한 SQL 자격 증명 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-376">Specify the SQL Credential information to authenticate to Azure storage.</span></span>  
  
3.  <span data-ttu-id="776a5-377">그런 다음 사용자가 제공한 SQL 자격 증명 정보를 사용 하 여 Azure storage에 연결 하 고 **azure에서 백업 파일 찾기** 대화 상자를 엽니다. SQL Server</span><span class="sxs-lookup"><span data-stu-id="776a5-377">SQL Server then connects to Azure storage using the SQL Credential information you provided and opens the **Locate Backup File in Azure** dialog.</span></span> <span data-ttu-id="776a5-378">스토리지에 있는 백업 파일이 이 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-378">The backup files residing in the storage are displayed on this page.</span></span> <span data-ttu-id="776a5-379">복원하는 데 사용할 파일을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-379">Select the file you want to use to restore and click **OK**.</span></span> <span data-ttu-id="776a5-380">**백업 디바이스 선택** 대화 상자가 표시됩니다. 이 대화 상자에서 **확인**을 클릭하면 복원을 완료할 수 있는 기본 **복원** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-380">This takes you back to the **Select Backup Devices** dialog, and Clicking **OK** on this dialog takes you back to the main **Restore** dialog where you will be able complete the restore.</span></span>  <span data-ttu-id="776a5-381">자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="776a5-381">For more information see, the following topics:</span></span>  
  
     [<span data-ttu-id="776a5-382">데이터베이스 복원&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-382">Restore Database &#40;General Page&#41;</span></span>](restore-database-general-page.md)  
  
     [<span data-ttu-id="776a5-383">데이터베이스 복원&#40;파일 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-383">Restore Database &#40;Files Page&#41;</span></span>](restore-database-files-page.md)  
  
     [<span data-ttu-id="776a5-384">데이터베이스 복원&#40;옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-384">Restore Database &#40;Options Page&#41;</span></span>](restore-database-options-page.md)  
  
##  <a name="code-examples"></a><a name="Examples"></a> <span data-ttu-id="776a5-385">코드 예제</span><span class="sxs-lookup"><span data-stu-id="776a5-385">Code Examples</span></span>  
 <span data-ttu-id="776a5-386">이 섹션에서는 다음과 같은 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-386">This section contains the following examples.</span></span>  
  
-   [<span data-ttu-id="776a5-387">자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-387">Create a Credential</span></span>](#credential)  
  
-   [<span data-ttu-id="776a5-388">전체 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-388">Backing up a complete database</span></span>](#complete)  
  
-   [<span data-ttu-id="776a5-389">데이터베이스 및 로그 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-389">Backing up the database and log</span></span>](#databaselog)  
  
-   [<span data-ttu-id="776a5-390">PRIMARY 파일 그룹의 전체 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-390">Creating a full file backup of the primary filegroup</span></span>](#filebackup)  
  
-   [<span data-ttu-id="776a5-391">PRIMARY 파일 그룹의 차등 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-391">Creating a differential file backup of the primary filegroups</span></span>](#differential)  
  
-   [<span data-ttu-id="776a5-392">데이터베이스 복원 및 파일 이동</span><span class="sxs-lookup"><span data-stu-id="776a5-392">Restoring a database and move files</span></span>](#restoredbwithmove)  
  
-   [<span data-ttu-id="776a5-393">STOPAT를 사용하여 지정 시간으로 복원</span><span class="sxs-lookup"><span data-stu-id="776a5-393">Restoring to a point-in-time using STOPAT</span></span>](#PITR)  
  
###  <a name="create-a-credential"></a><a name="credential"></a> <span data-ttu-id="776a5-394">자격 증명 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-394">Create a Credential</span></span>  
 <span data-ttu-id="776a5-395">다음 예제에서는 Azure Storage 인증 정보를 저장 하는 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-395">The following example creates a credential that stores the Azure Storage authentication information.</span></span>  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="backing-up-a-complete-database"></a><a name="complete"></a><span data-ttu-id="776a5-396">전체 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-396">Backing up a complete database</span></span>  
 <span data-ttu-id="776a5-397">다음 예에서는 Azure Blob 저장소 서비스에 AdventureWorks2012 데이터베이스를 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-397">The following example backs up the AdventureWorks2012 database to the Azure Blob storage service.</span></span>
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);  
   ```
  
   ```powershell
   # create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
   # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance  
   CD $srvPath   
   $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On
   ```  
  
###  <a name="backing-up-the-database-and-log"></a><a name="databaselog"></a><span data-ttu-id="776a5-398">데이터베이스 및 로그 백업</span><span class="sxs-lookup"><span data-stu-id="776a5-398">Backing up the database and log</span></span>  
 <span data-ttu-id="776a5-399">다음 예에서는 기본적으로 단순 복구 모델을 사용하는 AdventureWorks2012 예제 데이터베이스를 백업하고</span><span class="sxs-lookup"><span data-stu-id="776a5-399">The following example backups up the AdventureWorks2012 sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="776a5-400">로그 백업을 지원하기 위해 전체 복구 모델을 사용하도록 AdventureWorks2012 데이터베이스를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-400">To support log backups, the AdventureWorks2012 database is modified to use the full recovery model.</span></span> <span data-ttu-id="776a5-401">그런 다음 Azure Blob에 대 한 전체 데이터베이스 백업을 만들고 업데이트 작업 기간이 지난 후 로그를 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-401">The example then creates a full database backup to Azure Blob, and after a period of update activity, backs up the log.</span></span> <span data-ttu-id="776a5-402">이 예에서는 날짜/시간 스탬프를 포함한 백업 파일 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-402">This example creates a backup file name with a datetime stamp.</span></span>  
  
   ```sql
   -- To permit log backups, before the full database backup, modify the database   
   -- to use the full recovery model.  
   USE master;  
   GO  
   ALTER DATABASE AdventureWorks2012  
      SET RECOVERY FULL;  
   GO  
  
   -- Back up the full AdventureWorks2012 database.  
          -- First create a file name for the backup file with DateTime stamp  
  
   DECLARE @Full_Filename AS VARCHAR (300);  
   SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
   --Back up Adventureworks2012 database  
  
   BACKUP DATABASE AdventureWorks2012  
   TO URL =  @Full_Filename  
   WITH CREDENTIAL = 'mycredential';  
   ,COMPRESSION  
   GO  
   -- Back up the AdventureWorks2012 log.  
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url for data backup  
   string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database to Url  
   Backup backupData = new Backup();  
   backupData.CredentialName = credentialName;  
   backupData.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
   backupData.SqlBackup(server);  
  
   // Generate Unique Url for data backup  
   string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database Log to Url  
   Backup backupLog = new Backup();  
   backupLog.CredentialName = credentialName;  
   backupLog.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
   backupLog.Action = BackupActionType.Log;  
   backupLog.SqlBackup(server);  
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to theSQL Server Instance
   CD $srvPath   
   #Create a unique file name for the full database backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Backup Database to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
   #Create a unique file name for log backup  
  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup Log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log
   ```  
  
###  <a name="creating-a-full-file-backup-of-the-primary-filegroup"></a><a name="filebackup"></a><span data-ttu-id="776a5-403">주 파일 그룹의 전체 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-403">Creating a full file backup of the primary filegroup</span></span>  
 <span data-ttu-id="776a5-404">다음 예에서는 PRIMARY 파일 그룹의 전체 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-404">The following example creates a full file backup of the primary filegroup.</span></span>
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to the SQL Server Instance  
  
   CD $srvPath   
   #Create a unique file name for the file backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
   #Backup Primary File Group to URL  
  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary
   ```  
  
###  <a name="creating-a-differential-file-backup-of-the-primary-filegroup"></a><a name="differential"></a><span data-ttu-id="776a5-405">주 파일 그룹의 차등 파일 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="776a5-405">Creating a differential file backup of the primary filegroup</span></span>  
 <span data-ttu-id="776a5-406">다음 예에서는 PRIMARY 파일 그룹의 차등 파일 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-406">The following example creates a differential file backup of the primary filegroup.</span></span>  
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
   GO
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.Incremental = true;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server); 
   ```

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Create a differential backup of the primary filegroup
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental
   ```  
  
###  <a name="restore-a-database-and-move-files"></a><a name="restoredbwithmove"></a><span data-ttu-id="776a5-407">데이터베이스 복원 및 파일 이동</span><span class="sxs-lookup"><span data-stu-id="776a5-407">Restore a database and move files</span></span>  
 <span data-ttu-id="776a5-408">전체 데이터베이스 백업을 복원하고 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data 디렉터리로 복원한 데이터베이스를 이동하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-408">To restore a full database backup and move the restored database to C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data directory, use the following steps.</span></span>
  
   ```sql
   -- Backup the tail of the log first
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
   GO  
  
   RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
   WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for tail log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
   restore.SqlRestore(server);
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)
   ```  
  
###  <a name="restoring-to-a-point-in-time-using-stopat"></a><a name="PITR"></a> <span data-ttu-id="776a5-409">STOPAT를 사용하여 지정 시간으로 복원</span><span class="sxs-lookup"><span data-stu-id="776a5-409">Restoring to a point-in-time using STOPAT</span></span>  
 <span data-ttu-id="776a5-410">다음 예에서는 지정 시간의 상태로 데이터베이스를 복원하고 복원 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="776a5-410">The following example restores a database to its state to a point in time, and shows a restore operation.</span></span>  
  
   ```sql
   RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
   WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
   GO   
  
   RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
   WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
   GO  
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for Tail Log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.NoRecovery = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
   restore.SqlRestore(server);  
      
   // Restore transaction Log with stop at   
   Restore restoreLog = new Restore();  
   restoreLog.CredentialName = credentialName;  
   restoreLog.Database = dbName;  
   restoreLog.Action = RestoreActionType.Log;  
   restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restoreLog.ToPointInTime = DateTime.Now.ToString();   
   restoreLog.SqlRestore(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Navigate to SQL Server Instance Directory
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
   # Restore Transaction log with Stop At:  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()
   ```  
  
## <a name="see-also"></a><span data-ttu-id="776a5-411">참고 항목</span><span class="sxs-lookup"><span data-stu-id="776a5-411">See Also</span></span>  
 <span data-ttu-id="776a5-412">[URL에 대한 SQL Server 백업 - 최상의 방법 및 문제 해결](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="776a5-412">[SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span></span>  
 [<span data-ttu-id="776a5-413">시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="776a5-413">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](back-up-and-restore-of-system-databases-sql-server.md)   
