---
title: 활성 임대가 있는 백업 Blob 파일 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02aea910589633a5c3ec79e283c757727b4d92cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650133"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a><span data-ttu-id="87e27-102">활성 임대가 있는 백업 Blob 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="87e27-102">Deleting Backup Blob Files with Active Leases</span></span>
  <span data-ttu-id="87e27-103">Azure storage에 백업 하거나 복원 하는 경우 SQL Server는 blob에 대 한 단독 액세스를 잠그기 위해 무한 임대를 획득 합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-103">When backing up to or restoring from Azure storage, SQL Server acquires an infinite lease in order to lock exclusive access to the blob.</span></span> <span data-ttu-id="87e27-104">백업 또는 복원 프로세스가 성공적으로 완료되면 임대가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-104">When the backup or restore process is successfully completed, the lease is released.</span></span> <span data-ttu-id="87e27-105">백업 또는 복원에 실패하면 백업 프로세스에서는 잘못된 모든 blob을 정리하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-105">If a backup or restore fails, the backup process attempts to clean up any invalid blob.</span></span> <span data-ttu-id="87e27-106">하지만 오랫동안 지속된 네트워크 연결 오류로 인해 백업이 실패한 경우에는 백업 프로세스에서 blob에 액세스할 수 없으므로 blob이 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-106">However, if the backup fails due to prolonged or sustained network connectivity failure, the backup  process may not be able gain access to the blob and the blob may remain orphaned.</span></span> <span data-ttu-id="87e27-107">즉, 임대가 해제될 때까지 blob을 쓰거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-107">This means that the blob cannot be written to or deleted until the lease is released.</span></span> <span data-ttu-id="87e27-108">이 항목에서는 임대를 해제하고 blob을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-108">This topic describes how to release the lease and deleting the blob..</span></span>  
  
 <span data-ttu-id="87e27-109">임대 유형에 대한 자세한 내용은 이 [문서](https://go.microsoft.com/fwlink/?LinkId=275664)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="87e27-109">For more information on the types of leases, read this [article](https://go.microsoft.com/fwlink/?LinkId=275664).</span></span>  
  
 <span data-ttu-id="87e27-110">백업 작업이 실패하는 경우 잘못된 백업 파일이 만들어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-110">If the backup operation fails, it can result in a backup file that is not valid.</span></span>  <span data-ttu-id="87e27-111">백업 blob 파일에 활성 임대도 있어 해당 blob을 삭제하거나 덮어쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-111">The backup blob file might also have an active lease, preventing it from being deleted or overwritten.</span></span>  <span data-ttu-id="87e27-112">이러한 blob을 삭제하거나 덮어쓰려면 먼저 임대를 해제해야 합니다. 백업 실패 시 임대를 정리하고 blob을 삭제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-112">In order to delete or overwrite such blobs, the lease should first be broken.If there are backup failures, we recommend that you clean up leases and delete blobs.</span></span> <span data-ttu-id="87e27-113">스토리지 관리 작업의 일부로 주기적으로 정리를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-113">You can also choose cleanup periodically as part of storage management tasks.</span></span>  
  
 <span data-ttu-id="87e27-114">복원 실패 시 후속 복원이 차단되지 않으므로 활성 임대는 문제가 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-114">If there is a restore failure, subsequent restores are not blocked, and therefore the active lease may not be an issue.</span></span> <span data-ttu-id="87e27-115">blob을 덮어쓰거나 삭제해야 할 때만 임대 해제가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-115">Breaking the lease is only necessary when you have to overwrite or delete the blob.</span></span>  
  
## <a name="managing-orphaned-blobs"></a><span data-ttu-id="87e27-116">분리된 Blob 관리</span><span class="sxs-lookup"><span data-stu-id="87e27-116">Managing Orphaned Blobs</span></span>  
 <span data-ttu-id="87e27-117">다음 단계에서는 백업 또는 복원 작업 실패 후 정리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-117">The follow steps describe how to clean up after failed backup or restore activity.</span></span> <span data-ttu-id="87e27-118">모든 단계는 PowerShell 스크립트를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-118">All the steps can be done using PowerShell scripts.</span></span> <span data-ttu-id="87e27-119">코드 예제는 다음 섹션에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-119">A code example is provided in the following section:</span></span>  
  
1.  <span data-ttu-id="87e27-120">**임대가 있는 blob 식별:** 백업 프로세스를 실행하는 스크립트가 프로세스가 있는 경우 해당 스크립트나 프로세스 내에서 오류를 캡처하여 blob 정리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-120">**Identifying blobs that have leases:** If you have a script or a process that runs the backup processes, you might be able to capture the failure within the script or process and use that to clean up the blobs.</span></span>   <span data-ttu-id="87e27-121">또한 LeaseStats 및 LeastState 속성을 사용하여 임대가 있는 blob을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-121">You can also use the LeaseStats and LeastState properties to identify the blobs that have leases on them.</span></span> <span data-ttu-id="87e27-122">blob 식별 후에는 blob 삭제 전에 목록을 검토하고 백업 파일이 유효한지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-122">Once you have identified the blobs, we recommend that you review the list, verify the validity of the backup file before deleting the blob.</span></span>  
  
2.  <span data-ttu-id="87e27-123">**임대 해제:** 권한 있는 요청은 임대 ID를 제공하지 않고 임대를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-123">**Breaking the lease:** An authorized request can break the lease without supplying a lease ID.</span></span> <span data-ttu-id="87e27-124">자세한 내용은 [여기](https://go.microsoft.com/fwlink/?LinkID=275664) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="87e27-124">See [here](https://go.microsoft.com/fwlink/?LinkID=275664) for more information.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="87e27-125">SQL Server는 복원 작업 중 임대 ID를 실행하여 단독 액세스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-125">SQL Server issues a lease ID to establish exclusive access during the restore operation.</span></span> <span data-ttu-id="87e27-126">복원 임대 ID는 BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2입니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-126">The restore lease ID is BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.</span></span>  
  
3.  <span data-ttu-id="87e27-127">**Blob 삭제:** 활성 임대가 있는 Blob을 삭제하려면 먼저 임대를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-127">**Deleting the Blob:** To delete a blob that has an active lease, you must first break the lease.</span></span>  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a><span data-ttu-id="87e27-128">PowerShell 스크립트 예제</span><span class="sxs-lookup"><span data-stu-id="87e27-128">PowerShell Script Example</span></span>  
 <span data-ttu-id="87e27-129">중요 PowerShell 2.0을 실행 하는 경우 Microsoft WindowsAzure.Storage.dll 어셈블리를 로드 하는 데 문제가 있을 수 있습니다. \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="87e27-129">**\*\* Important \*\*** If you are running PowerShell 2.0, you may have problems loading the Microsoft WindowsAzure.Storage.dll assembly.</span></span> <span data-ttu-id="87e27-130">문제 해결을 위해 Powershell 3.0으로 업그레이드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-130">We recommend that you upgrade to Powershell 3.0 to solve the issue.</span></span> <span data-ttu-id="87e27-131">PowerShell 2.0에 대한 다음 해결 방법을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-131">You may also use the following workaround for PowerShell 2.0:</span></span>  
  
-   <span data-ttu-id="87e27-132">다음과 같이 powershell.exe.config 파일을 만들거나 수정하여 런타임에 .NET 2.0 및 .NET 4.0 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-132">Create or modify the powershell.exe.config file to load .NET 2.0 and .NET 4.0 assemblies at runtime with the following:</span></span>  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 <span data-ttu-id="87e27-133">다음 예에서는 활성 임대가 있는 blob을 식별한 다음 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-133">The following example illustrates identifying blobs that have active leases and then breaking them.</span></span> <span data-ttu-id="87e27-134">임대 ID를 필터링하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-134">The example also demonstrates how filter for release lease IDs.</span></span>  
  
 <span data-ttu-id="87e27-135">이 스크립트 실행 팁</span><span class="sxs-lookup"><span data-stu-id="87e27-135">Tips on running this script</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="87e27-136">Azure Blob storage 서비스에 대 한 백업이이 스크립트와 동시에 실행 되는 경우이 스크립트는 백업에서 동시에 얻으려고 시도 하는 임대를 중단 하므로 백업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-136">If a backup to Azure Blob storage service is running at the same time as this script, the backup can fail since this script will break the lease that the backup is trying to acquire at the same time.</span></span> <span data-ttu-id="87e27-137">이 스크립트는 유지 관리 기간이나 백업이 실행되지 않을 때 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-137">We recommend running this script during a maintenance windows or when no backups are expected to run.</span></span>  
  
1.  <span data-ttu-id="87e27-138">이 스크립트를 실행 하면 저장소 계정, 저장소 키, 컨테이너 및 Azure storage 어셈블리 경로와 이름 매개 변수 값을 제공 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-138">When you run this script, you will be prompted to provide values for the storage account, storage key, container, and the Azure storage assembly path and name parameters.</span></span> <span data-ttu-id="87e27-139">스토리지 어셈블리의 경로는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 설치 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-139">The path of the storage is assembly is the installation directory of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="87e27-140">스토리지 어셈블리의 파일 이름은 Microsoft.WindowsAzure.Storage.dll입니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-140">The file name for the storage assembly is Microsoft.WindowsAzure.Storage.dll.</span></span> <span data-ttu-id="87e27-141">다음은 프롬프트 및 입력 값의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-141">Following is an example of the prompts and values entered:</span></span>  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  <span data-ttu-id="87e27-142">잠긴 임대를 가진 blob이 없는 경우 다음과 같은 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-142">If there are no blobs that have locked leases you should see the following message:</span></span>  
  
     <span data-ttu-id="87e27-143">**잠긴 임대 상태의 blob 없음**</span><span class="sxs-lookup"><span data-stu-id="87e27-143">**There are no blobs with locked lease status**</span></span>  
  
     <span data-ttu-id="87e27-144">잠긴 임대를 가진 blob이 있는 경우 다음과 같은 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="87e27-144">If there are blobs with locked leases, you should see the following messages:</span></span>  
  
     <span data-ttu-id="87e27-145">**임대 해제 중**</span><span class="sxs-lookup"><span data-stu-id="87e27-145">**Breaking Leases**</span></span>  
  
     <span data-ttu-id="87e27-146">**임대는 \<URL of the Blob> 복원 임대입니다. 아직 활성 상태인 복원 임대가 있는 blob이 있는 경우에만이 메시지가 표시 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="87e27-146">**The lease on \<URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.**</span></span>  
  
     <span data-ttu-id="87e27-147">**의 임대는 \<URL of the Blob> 복원 임대 중단 임대가 아닙니다 \<URL of the Bob> .**</span><span class="sxs-lookup"><span data-stu-id="87e27-147">**The lease on \<URL of the Blob> is not a restore lease Breaking lease on \<URL of the Bob>.**</span></span>  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="87e27-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87e27-148">See Also</span></span>  
 [<span data-ttu-id="87e27-149">URL에 SQL Server 백업 모범 사례 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="87e27-149">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
