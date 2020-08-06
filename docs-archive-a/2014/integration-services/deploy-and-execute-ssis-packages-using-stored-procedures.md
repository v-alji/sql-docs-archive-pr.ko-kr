---
title: 저장 프로시저를 사용 하 여 SSIS 패키지 배포 및 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1570207dca6e944b54c553a1d83256d8f4fa3244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740167"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a><span data-ttu-id="10a4a-102">저장 프로시저를 사용하여 SSIS 패키지 배포 및 실행</span><span class="sxs-lookup"><span data-stu-id="10a4a-102">Deploy and Execute SSIS Packages using Stored Procedures</span></span>
  <span data-ttu-id="10a4a-103">프로젝트 배포 모델을 사용하도록 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 구성하면 [!INCLUDE[ssIS](../includes/ssis-md.md)] 카탈로그의 저장 프로시저를 사용하여 프로젝트를 배포하고 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-103">When you configure an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to use the project deployment model, you can use stored procedures in the [!INCLUDE[ssIS](../includes/ssis-md.md)] catalog to deploy the project and execute the packages.</span></span> <span data-ttu-id="10a4a-104">프로젝트 배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="10a4a-104">For information about the project deployment model, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="10a4a-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 사용하여 프로젝트를 배포하고 패키지를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-105">You can also use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to deploy the project and execute the packages.</span></span> <span data-ttu-id="10a4a-106">자세한 내용은 **참고 항목** 섹션의 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="10a4a-106">For more information, see the topics in the **See Also** section.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="10a4a-107">다음을 수행하여 아래 절차에 나열된 저장 프로시저에 대한 Transact-SQL 문을 쉽게 생성할 수 있습니다. 단, catalog.deploy_project는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-107">You can easily generate the Transact-SQL statements for the stored procedures listed in the procedure below, with the exception of catalog.deploy_project, by doing the following:</span></span>  
> 
>  1.  <span data-ttu-id="10a4a-108">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 **Integration Services 카탈로그** 노드를 확장하고 실행할 패키지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-108">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** node in Object Explorer and navigate to the package you want to execute.</span></span>  
> 2.  <span data-ttu-id="10a4a-109">패키지를 마우스 오른쪽 단추로 클릭하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-109">Right-click the package, and then click **Execute**.</span></span>  
> 3.  <span data-ttu-id="10a4a-110">필요에 따라 **고급** 탭에서 로깅 수준 등의 옵션을 설정하거나 매개 변수 값과 연결 관리자 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-110">As needed, set parameters values, connection manager properties, and options in the **Advanced** tab such as the logging level.</span></span>  
> 
>      <span data-ttu-id="10a4a-111">로깅 수준에 대한 자세한 내용은 [SSIS 서버에서 패키지 실행에 대한 로깅 설정](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="10a4a-111">For more information about logging levels, see [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).</span></span>  
> 4.  <span data-ttu-id="10a4a-112">**확인** 을 클릭하여 패키지를 실행하기 전에 **스크립트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-112">Before clicking **OK** to execute the package, click **Script**.</span></span> <span data-ttu-id="10a4a-113">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 편집기 창에 Transact-SQL이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-113">The Transact-SQL appears in a Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a><span data-ttu-id="10a4a-114">저장 프로시저를 사용하여 패키지를 배포하고 실행하려면</span><span class="sxs-lookup"><span data-stu-id="10a4a-114">To deploy and execute a package using stored procedures</span></span>  
  
1.  <span data-ttu-id="10a4a-115">[catalog.deploy_project&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database)를 호출하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 대한 패키지를 포함하는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-115">Call [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) to deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="10a4a-116">프로젝트 배포 파일의 이진 콘텐츠를 검색 하려면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] \* \@ project_stream\* 매개 변수에 대해 SELECT 문을 OPENROWSET 함수 및 BULK 행 집합 공급자와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-116">To retrieve the binary contents of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project deployment file, for the *\@project_stream* parameter, use a SELECT statement with the OPENROWSET function and the BULK rowset provider.</span></span> <span data-ttu-id="10a4a-117">BULK 행 집합 공급자를 사용하여 파일에서 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-117">The BULK rowset provider enables you to read data from a file.</span></span> <span data-ttu-id="10a4a-118">BULK 행 집합 공급자에 대한 SINGLE_BLOB 인수는 데이터 파일의 내용을 varbinary(max) 형식의 단일 행, 단일 열 행 집합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-118">The SINGLE_BLOB argument for the BULK rowset provider returns the contents of the data file as a single-row, single-column rowset of type varbinary(max).</span></span> <span data-ttu-id="10a4a-119">자세한 내용은 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10a4a-119">For more information, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
     <span data-ttu-id="10a4a-120">다음 예에서는 SSISPackages_ProjectDeployment 프로젝트를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버의 SSIS Packages 폴더에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-120">In the following example, the SSISPackages_ProjectDeployment project is deployed to the SSIS Packages folder on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="10a4a-121">이진 데이터는 프로젝트 파일 SSISPackage_ProjectDeployment (.ispac)에서 읽고 varbinary (max) 형식의 \* \@ projectbinary\* 매개 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-121">The binary data is read from the project file (SSISPackage_ProjectDeployment.ispac) and is stored in the *\@ProjectBinary* parameter of type varbinary(max).</span></span> <span data-ttu-id="10a4a-122">\* \@ Projectbinary\* 매개 변수 값이 \* \@ project_stream\* 매개 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-122">The *\@ProjectBinary* parameter value is assigned to the *\@project_stream* parameter.</span></span>  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  <span data-ttu-id="10a4a-123">[catalog.create_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)을 호출하여 프로젝트 실행 인스턴스를 만들고 필요에 따라 [catalog.set_execution_parameter_value&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)를 호출하여 런타임 매개 변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-123">Call [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) to create an instance of the package execution, and optionally call [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) to set runtime parameter values.</span></span>  
  
     <span data-ttu-id="10a4a-124">다음 예에서는 catalog.create_execution이 SSISPackage_ProjectDeployment 프로젝트에 포함된 package.dtsx에 대한 실행 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-124">In the following example, catalog.create_execution creates an instance of execution for package.dtsx that is contained in the SSISPackage_ProjectDeployment project.</span></span> <span data-ttu-id="10a4a-125">프로젝트는 SSIS Packages 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-125">The project is located in the SSIS Packages folder.</span></span> <span data-ttu-id="10a4a-126">저장 프로시저에서 반환된 execution_id가 catalog.set_execution_parameter_value 호출에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-126">The execution_id returned by the stored procedure is used in the call to catalog.set_execution_parameter_value.</span></span> <span data-ttu-id="10a4a-127">이 두 번째 저장 프로시저는 LOGGING_LEVEL 매개 변수를 3(자세한 로깅)으로 설정하고 Parameter1이라는 패키지 매개 변수의 값을 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-127">This second stored procedure sets the LOGGING_LEVEL parameter to 3 (verbose logging) and sets a package parameter named Parameter1 to a value of 1.</span></span>  
  
     <span data-ttu-id="10a4a-128">LOGGING_LEVEL과 같은 매개 변수의 object_type 값은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-128">For parameters such as LOGGING_LEVEL the object_type value is 50.</span></span> <span data-ttu-id="10a4a-129">패키지 매개 변수의 object_type 값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-129">For package parameters the object_type value is 30.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  <span data-ttu-id="10a4a-130">[catalog.start_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)을 호출하여 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-130">Call [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) to execute the package.</span></span>  
  
     <span data-ttu-id="10a4a-131">다음 예에서는 패키지 실행 시작을 위해 catalog.start_execution 호출이 Transact-SQL에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-131">In the following example, a call to catalog.start_execution is added to the Transact-SQL to start the package execution.</span></span> <span data-ttu-id="10a4a-132">catalog.create_execution 저장 프로시저에서 반환된 execution_id가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-132">The execution_id returned by the catalog.create_execution stored procedure is used.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a><span data-ttu-id="10a4a-133">저장 프로시저를 사용하여 서버 간에 프로젝트를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="10a4a-133">To deploy a project from server to server using stored procedures</span></span>  
 <span data-ttu-id="10a4a-134">[catalog.get_project&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) 및 [catalog.deploy_project&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) 저장 프로시저를 사용하여 서버 간에 프로젝트를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-134">You can deploy a project from server to server by using the [catalog.get_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) and [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) stored procedures.</span></span>  
  
 <span data-ttu-id="10a4a-135">저장 프로시저를 실행하기 전에 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-135">You need to do the following before running the stored procedures.</span></span>  
  
-   <span data-ttu-id="10a4a-136">연결된 서버 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-136">Create a linked server object.</span></span> <span data-ttu-id="10a4a-137">자세한 내용은 [연결된 서버 만들기&#40;SQL Server 데이터베이스 엔진&#41;](../database-engine/sql-server-database-engine-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10a4a-137">For more information, see [Create Linked Servers &#40;SQL Server Database Engine&#41;](../database-engine/sql-server-database-engine-overview.md).</span></span>  
  
     <span data-ttu-id="10a4a-138">**연결된 서버 속성** 대화 상자의 **서버 옵션** 페이지에서 **RPC** 와 **RPC 내보내기** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-138">On the **Server Options** page of the **Linked Server Properties** dialog box, set **RPC** and **RPC Out** to **True**.</span></span> <span data-ttu-id="10a4a-139">**RPC에 대한 분산 트랜잭션 승격 설정** 도 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-139">Also, set **Enable Promotion of Distributed Transactions for RPC** to **False**.</span></span>  
  
-   <span data-ttu-id="10a4a-140">개체 탐색기의 **연결된 서버** 에서 **공급자** 노드를 확장하고 공급자를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하여 연결된 서버에 대해 선택된 공급자에 동적 매개 변수를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-140">Enable dynamic parameters for the provider you selected for the linked server, by expanding the **Providers** node under **Linked Servers** in Object Explorer, right-clicking the provider, and then clicking **Properties**.</span></span> <span data-ttu-id="10a4a-141">**동적 매개 변수** 옆에서 **사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-141">Select **Enable** next to **Dynamic parameter.**</span></span>  
  
-   <span data-ttu-id="10a4a-142">DTC(Distributed Transaction Coordinator)가 두 서버에서 모두 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-142">Confirm that the Distributed Transaction Coordinator (DTC) is started on both servers.</span></span>  
  
 <span data-ttu-id="10a4a-143">catalog.get_project를 호출하여 프로젝트에 대한 이진값을 반환하고 catalog.deploy_project를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-143">Call catalog.get_project to return the binary for the project, and then call catalog.deploy_project.</span></span> <span data-ttu-id="10a4a-144">catalog.get_project에서 반환된 값이 varbinary(max) 형식의 테이블 변수에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-144">The value returned by catalog.get_project is inserted into a table variable of type varbinary(max).</span></span> <span data-ttu-id="10a4a-145">연결된 서버에서는 varbinary(max) 형식의 결과를 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-145">The linked server can't return results that are varbinary(max).</span></span>  
  
 <span data-ttu-id="10a4a-146">다음 예에서는 catalog.get_project가 연결된 서버의 SSISPackages 프로젝트에 대한 이진값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-146">In the following example, catalog.get_project returns a binary for the SSISPackages project on the linked server.</span></span> <span data-ttu-id="10a4a-147">catalog.deploy_project가 로컬 서버의 DestFolder 폴더에 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="10a4a-147">The catalog.deploy_project deploys the project to the local server, to the folder named DestFolder.</span></span>  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="10a4a-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10a4a-148">See Also</span></span>  
 <span data-ttu-id="10a4a-149">[Integration Services 서버에 프로젝트 배포](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="10a4a-149">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 <span data-ttu-id="10a4a-150">[SQL Server Data Tools에서 패키지를 실행 합니다.](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="10a4a-150">[Run a Package in SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="10a4a-151">SQL Server Management Studio를 사용하여 SSIS 서버에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="10a4a-151">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
