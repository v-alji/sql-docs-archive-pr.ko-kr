---
title: SSIS 카탈로그 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2572cc131f34a21171054a159e3b7968c453a780
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647780"
---
# <a name="create-the-ssis-catalog"></a><span data-ttu-id="56d9e-102">SSIS 카탈로그 만들기</span><span class="sxs-lookup"><span data-stu-id="56d9e-102">Create the SSIS Catalog</span></span>
  <span data-ttu-id="56d9e-103">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 디자인하고 테스트한 후에는 이 패키지가 포함된 프로젝트를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="56d9e-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 프로젝트를 배포하려면 서버에 `SSISDB` 카탈로그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-104">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the server must contain the `SSISDB` catalog.</span></span> <span data-ttu-id="56d9e-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 설치 프로그램에서 카탈로그를 자동으로 만들지 않으므로 다음 지침에 따라 카탈로그를 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-105">The installation program for [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] does not automatically create the catalog; you need to manually create the catalog by using the following instructions.</span></span>  
  
 <span data-ttu-id="56d9e-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 SSISDB 카탈로그를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-106">You can create the SSISDB catalog in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="56d9e-107">Windows PowerShell을 사용하여 프로그래밍 방식으로 카탈로그를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-107">You also create the catalog programmatically by using Windows PowerShell.</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a><span data-ttu-id="56d9e-108">SQL Server Management Studio에서 SSISDB 카탈로그를 만들려면</span><span class="sxs-lookup"><span data-stu-id="56d9e-108">To create the SSISDB catalog in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="56d9e-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="56d9e-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 엔진에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-110">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Database Engine.</span></span>  
  
3.  <span data-ttu-id="56d9e-111">개체 탐색기에서 서버 노드를 확장하고 **Integration Services 카탈로그** 노드를 마우스 오른쪽 단추로 클릭한 다음 **카탈로그 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-111">In Object Explorer, expand the server node, right-click the **Integration Services Catalogs** node, and then click **Create Catalog**.</span></span>  
  
4.  <span data-ttu-id="56d9e-112">**CLR 통합 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-112">Click **Enable CLR Integration**.</span></span>  
  
     <span data-ttu-id="56d9e-113">카탈로그에 CLR 저장 프로시저가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-113">The catalog uses CLR stored procedures.</span></span>  
  
5.  <span data-ttu-id="56d9e-114">**SQL Server 시작 시 Integration Services 저장 프로시저 자동 실행** 을 클릭하여 [서버 인스턴스를 다시 시작할 때마다](/sql/integration-services/system-stored-procedures/catalog-startup) catalog.startup [!INCLUDE[ssIS](../includes/ssis-md.md)] 저장 프로시저를 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-114">Click **Enable automatic execution of Integration Services stored procedure at SQL Server startup** to enable the [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) stored procedure to run each time the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance is restarted.</span></span>  
  
     <span data-ttu-id="56d9e-115">저장 프로시저에서는 SSISDB 카탈로그에 대한 작업의 상태를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-115">The stored procedure performs maintenance of the state of operations for the SSISDB catalog.</span></span> <span data-ttu-id="56d9e-116">[!INCLUDE[ssIS](../includes/ssis-md.md)] 서버 인스턴스가 다운될 때 실행 중이었던 패키지의 상태를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-116">It fixes the status of any packages there were running if and when the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance goes down.</span></span>  
  
6.  <span data-ttu-id="56d9e-117">암호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-117">Enter a password, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="56d9e-118">암호는 카탈로그 데이터를 암호화하는 데 사용되는 데이터베이스 마스터 키를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-118">The password protects the database master key that is used for encrypting the catalog data.</span></span> <span data-ttu-id="56d9e-119">암호를 안전한 위치에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="56d9e-119">Save the password in a secure location.</span></span> <span data-ttu-id="56d9e-120">데이터베이스 마스터 키도 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-120">It is recommended that you also back up the database master key.</span></span> <span data-ttu-id="56d9e-121">자세한 내용은 [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56d9e-121">For more information, see [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md).</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a><span data-ttu-id="56d9e-122">SSISDB 카탈로그를 프로그래밍 방식으로 만들려면</span><span class="sxs-lookup"><span data-stu-id="56d9e-122">To create the SSISDB catalog programmatically</span></span>  
  
1.  <span data-ttu-id="56d9e-123">다음 PowerShell 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56d9e-123">Execute the following PowerShell script:</span></span>  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     <span data-ttu-id="56d9e-124">Windows PowerShell 및 <xref:Microsoft.SqlServer.Management.IntegrationServices> 네임스페이스를 사용하는 방법의 예를 더 보려면 blogs.msdn.com에서 [SQL Server 2012의 SSIS 및 PowerShell](https://go.microsoft.com/fwlink/?LinkId=242539) 블로그 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56d9e-124">For more examples of how to use Windows PowerShell and the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace, see the blog entry, [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), on blogs.msdn.com.</span></span> <span data-ttu-id="56d9e-125">네임스페이스 및 코드 예제에 대한 개요는 blogs.msdn.com에서 [SSIS 카탈로그 관리 개체 모델에 대한 이해](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)블로그 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="56d9e-125">For an overview of the namespace and code examples, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d9e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56d9e-126">See Also</span></span>  
 <span data-ttu-id="56d9e-127">[SSIS 카탈로그](catalog/ssis-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="56d9e-127">[SSIS Catalog](catalog/ssis-catalog.md) </span></span>  
 [<span data-ttu-id="56d9e-128">SSIS 카탈로그 백업, 복원 및 이동</span><span class="sxs-lookup"><span data-stu-id="56d9e-128">Backup, Restore, and Move the SSIS Catalog</span></span>](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
