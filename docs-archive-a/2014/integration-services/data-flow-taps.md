---
title: 데이터 흐름 탭 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053b34add45354d0df71fa73a72f8786cc706d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729676"
---
# <a name="data-flow-taps"></a><span data-ttu-id="d8f4a-102">데이터 흐름 탭</span><span class="sxs-lookup"><span data-stu-id="d8f4a-102">Data Flow Taps</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)]<span data-ttu-id="d8f4a-103">에는 런타임에 패키지의 데이터 흐름 경로에서 데이터 탭을 추가하고, 데이터 탭의 출력을 외부 파일에 전달할 수 있는 새로운 기능이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-103">introduces a new feature that allows you to add a data tap on a data flow path of a package at runtime and direct the output from the data tap to an external file.</span></span> <span data-ttu-id="d8f4a-104">이 기능을 사용하려면 프로젝트 배포 모델을 사용하여 SSIS 프로젝트를 SSIS 서버에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-104">To use this feature, you must deploy your SSIS project using the project deployment model to an SSIS Server.</span></span> <span data-ttu-id="d8f4a-105">서버에 패키지를 배포한 후에는 패키지를 실행하기 전에 SSISDB 데이터베이스에 대해 T-SQL 스크립트를 실행하여 데이터 탭을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-105">After you deploy the package to the server, you need to execute T-SQL scripts against the SSISDB database to add data taps before executing the package.</span></span> <span data-ttu-id="d8f4a-106">다음은 예제 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-106">Here is a sample scenario:</span></span>  
  
1.  <span data-ttu-id="d8f4a-107">[catalog.create_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) 저장 프로시저를 사용하여 패키지의 실행 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-107">Create an execution instance of a package by using the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) stored procedure.</span></span>  
  
2.  <span data-ttu-id="d8f4a-108">[catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) 또는 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) 저장 프로시저를 사용하여 데이터 탭을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-108">Add a data tap by using either [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) or [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) stored procedure.</span></span>  
  
3.  <span data-ttu-id="d8f4a-109">[catalog.start_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)을 사용하여 패키지의 실행 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-109">Start the execution instance of the package by using the [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
 <span data-ttu-id="d8f4a-110">다음은 위의 시나리오에 설명된 단계를 수행하는 예제 SQL 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-110">Here is a sample SQL script that performs the steps described in the above scenario:</span></span>  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 <span data-ttu-id="d8f4a-111">create_execution 저장 프로시저의 폴더 이름, 프로젝트 이름 및 패키지 이름 매개 변수는 Integration Services 카탈로그의 폴더, 프로젝트 및 패키지 이름에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-111">The folder name, project name, and package name parameters of the create_execution stored procedure correspond to the folder, project, and package names in the Integration Services catalog.</span></span> <span data-ttu-id="d8f4a-112">다음 그림에 표시된 것처럼 폴더, 프로젝트 및 패키지 이름을 가져와서 SQL Server Management Studio에서 create_execution 호출을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-112">You can get the folder, project, and package names to use in the create_execution call from the SQL Server Management Studio as shown in the following image.</span></span> <span data-ttu-id="d8f4a-113">여기에 SSIS 프로젝트가 나타나지 않으면 프로젝트를 SSIS 서버에 아직 배포하지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-113">If you do not see your SSIS project here, you may not have deployed the project to SSIS server yet.</span></span> <span data-ttu-id="d8f4a-114">Visual Studio에서 SSIS 프로젝트를 마우스 오른쪽 단추로 클릭하고 배포를 클릭하여 예상되는 SSIS 서버에 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-114">Right-click on SSIS project in Visual Studio and click Deploy to deploy the project to the expected SSIS server.</span></span>  
  
 <span data-ttu-id="d8f4a-115">SQL 문을 입력하는 대신 다음 단계를 수행하여 실행 패키지 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-115">Instead of typing the SQL statements, you can generate the execute package script by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="d8f4a-116">**Package.dtsx** 를 마우스 오른쪽 단추로 클릭하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-116">Right-click **Package.dtsx** and click **Execute**.</span></span>  
  
2.  <span data-ttu-id="d8f4a-117">**스크립트** 도구 모음 단추를 클릭하여 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-117">Click **Script** toolbar button to generate the script.</span></span>  
  
3.  <span data-ttu-id="d8f4a-118">이제 start_execution을 호출하기 전에 add_data_tap 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-118">Now, add the add_data_tap statement before the start_execution call.</span></span>  
  
 <span data-ttu-id="d8f4a-119">add_data_tap 저장 프로시저의 task_package_path 매개 변수는 Visual Studio 데이터 흐름 태스크의 PackagePath 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-119">The task_package_path parameter of add_data_tap stored procedure corresponds to the PackagePath property of the data flow task in Visual Studio.</span></span> <span data-ttu-id="d8f4a-120">Visual Studio에서 **데이터 흐름 태스크**를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭하여 속성 창을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-120">In Visual Studio, right-click the **Data Flow Task**, and click **Properties** to launch the Properties window.</span></span>  <span data-ttu-id="d8f4a-121">**PackagePath** 속성 값을 확인하여 add_data_tap 저장 프로시저 호출에 대한 task_package_path 매개 변수 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-121">Note the value of the **PackagePath** property to use it as a value for the task_package_path parameter for add_data_tap stored procedure call.</span></span>  
  
 <span data-ttu-id="d8f4a-122">add_data_tap 저장 프로시저의 dataflow_path_id_string 매개 변수는 데이터 탭을 추가할 데이터 흐름 경로의 IdentificationString 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-122">The dataflow_path_id_string  parameter of add_data_tap stored procedure corresponds to the IdentificationString property of the data flow path to which you want to add a data tap.</span></span> <span data-ttu-id="d8f4a-123">dataflow_path_id_string을 가져오려면 데이터 흐름 경로(데이터 흐름의 태스크 사이에 있는 화살표)를 클릭하고 속성 창에서 **IdentificationString** 속성 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-123">To get the dataflow_path_id_string, click the data flow path (arrow between tasks in the data flow), and note the value of the **IdentificationString** property in the Properties window.</span></span>  
  
 <span data-ttu-id="d8f4a-124">스크립트를 실행하면 출력 파일은 \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-124">When you execute the script, the output file is stored in \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps.</span></span> <span data-ttu-id="d8f4a-125">해당 이름을 가진 파일이 이미 있으면 접미사(예: output[1].txt)로 새 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-125">If a file with the name already exists, a new file with a suffix (for example: output[1].txt)  is created.</span></span>  
  
 <span data-ttu-id="d8f4a-126">앞에서 설명한 대로 add_data_tap 저장 프로시저를 사용하는 대신 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)저장 프로시저를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-126">As mentioned earlier, you can also use [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)stored procedure instead of using add_data_tap stored procedure.</span></span> <span data-ttu-id="d8f4a-127">이 저장 프로시저는 task_package_path 대신 데이터 흐름 태스크의 ID를 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-127">This stored procedure takes the ID of data flow task as a parameter instead of task_package_path.</span></span> <span data-ttu-id="d8f4a-128">Visual Studio의 속성 창에서 데이터 흐름 태스크의 ID를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-128">You can get the ID of data flow task from the properties window in Visual Studio.</span></span>  
  
## <a name="removing-a-data-tap"></a><span data-ttu-id="d8f4a-129">데이터 탭 제거</span><span class="sxs-lookup"><span data-stu-id="d8f4a-129">Removing a data tap</span></span>  
 <span data-ttu-id="d8f4a-130">[catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) 저장 프로시저를 사용하여 실행을 시작하기 전에 데이터 탭을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-130">You can remove a data tap before starting the execution by using the [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) stored procedure.</span></span> <span data-ttu-id="d8f4a-131">이 저장 프로시저는 add_data_tap 저장 프로시저의 출력으로 가져올 수 있는 데이터 탭의 ID를 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-131">This stored procedure takes the ID of data tap as a parameter, which you can get as an output of the add_data_tap stored procedure.</span></span>  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a><span data-ttu-id="d8f4a-132">모든 데이터 탭 나열</span><span class="sxs-lookup"><span data-stu-id="d8f4a-132">Listing all data taps</span></span>  
 <span data-ttu-id="d8f4a-133">catalog.execution_data_taps 뷰를 사용하여 모든 데이터 탭을 나열할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-133">You can also list all the data taps by using the catalog.execution_data_taps view.</span></span> <span data-ttu-id="d8f4a-134">다음 예에서는 사양 실행 인스턴스(ID: 54)의 데이터 탭을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-134">The following example extracts data taps for a specification execution instance (ID: 54).</span></span>  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a><span data-ttu-id="d8f4a-135">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="d8f4a-135">Performance consideration</span></span>  
 <span data-ttu-id="d8f4a-136">자세한 로깅 수준을 사용하도록 설정하고 데이터 탭을 추가하면 데이터 통합 솔루션에서 수행되는 I/O 작업이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-136">Enabling verbose logging level and adding data taps increase the I/O operations performed by your data integration solution.</span></span> <span data-ttu-id="d8f4a-137">따라서 문제 해결을 위해서만 데이터 탭을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-137">Hence, we recommend that you add data taps only for troubleshooting purposes</span></span>  
  
## <a name="video"></a><span data-ttu-id="d8f4a-138">비디오</span><span class="sxs-lookup"><span data-stu-id="d8f4a-138">Video</span></span>  
 <span data-ttu-id="d8f4a-139">이 [TechNet 비디오](https://technet.microsoft.com/sqlserver/dn600163) 에서는 프로그래밍 방식으로 패키지를 디버깅하고 런타임에 일부 결과를 캡처하는 데 도움이 되도록 SQL Server 2012 SSISDB 카탈로그에 데이터 탭을 추가/사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-139">This [video on TechNet](https://technet.microsoft.com/sqlserver/dn600163) demonstrates how to add/use data taps in SQL Server 2012 SSISDB catalog that help with debugging packages programmatically and capturing the partial results at the runtime.</span></span> <span data-ttu-id="d8f4a-140">이러한 데이터 탭을 나열/제거하는 방법과 함께 SSIS 패키지의 데이터 탭을 사용하기 위한 최선의 구현 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f4a-140">It also discusses how to list/ remove these data taps and best practices for using data taps in SSIS packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d8f4a-141">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d8f4a-141">Related Tasks</span></span>  
 [<span data-ttu-id="d8f4a-142">데이터 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="d8f4a-142">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="d8f4a-143">패키지 실행 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="d8f4a-143">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
