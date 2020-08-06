---
title: dtexec 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7b6867fa-1039-49b3-90fb-85b84678a612
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45820aa673f31ae9cea7d1f2f4e8b61d63b8670c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734332"
---
# <a name="dtexec-utility"></a><span data-ttu-id="3ffce-102">dtexec 유틸리티</span><span class="sxs-lookup"><span data-stu-id="3ffce-102">dtexec Utility</span></span>
  <span data-ttu-id="3ffce-103">`dtexec`명령 프롬프트 유틸리티는 패키지를 구성 하 고 실행 하는 데 사용 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3ffce-103">The `dtexec` command prompt utility is used to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="3ffce-104">`dtexec`유틸리티에서는 매개 변수, 연결, 속성, 변수, 로깅, 진행률 표시기 등의 모든 패키지 구성 및 실행 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-104">The `dtexec` utility provides access to all the package configuration and execution features, such as parameters, connections, properties, variables, logging, and progress indicators.</span></span> <span data-ttu-id="3ffce-105">`dtexec`유틸리티를 사용 하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버, .ispac 프로젝트 파일, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스, [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소 및 파일 시스템 원본에서 패키지를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-105">The `dtexec` utility lets you load packages from these sources: the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, an .ispac project file, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ffce-106">[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]과 함께 제공되는 `dtexec` 유틸리티 버전을 사용하여 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 또는 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 패키지를 실행할 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 일시적으로 패키지를 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-106">When you use the version of the `dtexec` utility that comes with [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] to run a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or a [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] temporarily upgrades the package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].</span></span> <span data-ttu-id="3ffce-107">그러나 `dtexec` 유틸리티를 사용하여 이러한 업그레이드된 변경 내용을 저장할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-107">However, you cannot use the `dtexec` utility to save these upgraded changes.</span></span> <span data-ttu-id="3ffce-108">패키지를 영구적으로로 업그레이드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] [Integration Services 패키지 업그레이드](../install-windows/upgrade-integration-services-packages.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-108">For more information about how to permanently upgrade a package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)], see [Upgrade Integration Services Packages](../install-windows/upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="3ffce-109">이 항목에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-109">This topic includes the following sections:</span></span>  
  
-   [<span data-ttu-id="3ffce-110">Integration Services 서버 및 프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="3ffce-110">Integration Services Server and Project File</span></span>](#server)  
  
-   [<span data-ttu-id="3ffce-111">64비트 컴퓨터에서의 설치 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3ffce-111">Installation Considerations on 64-bit Computers</span></span>](#bit)  
  
-   [<span data-ttu-id="3ffce-112">병렬 설치 컴퓨터에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3ffce-112">Considerations on Computers with Side-by-Side Installations</span></span>](#side)  
  
-   [<span data-ttu-id="3ffce-113">실행 단계</span><span class="sxs-lookup"><span data-stu-id="3ffce-113">Phases of Execution</span></span>](#phases)  
  
-   [<span data-ttu-id="3ffce-114">반환된 종료 코드</span><span class="sxs-lookup"><span data-stu-id="3ffce-114">Exit Codes Returned</span></span>](#exit)  
  
-   [<span data-ttu-id="3ffce-115">구문 규칙</span><span class="sxs-lookup"><span data-stu-id="3ffce-115">Syntax Rules</span></span>](#syntaxRules)  
  
-   [<span data-ttu-id="3ffce-116">xp_cmdshell에서 dtexec 사용</span><span class="sxs-lookup"><span data-stu-id="3ffce-116">Using dtexec from the xp_cmdshell</span></span>](#cmdshell)  
  
-   [<span data-ttu-id="3ffce-117">구문</span><span class="sxs-lookup"><span data-stu-id="3ffce-117">Syntax</span></span>](#syntax)  
  
-   [<span data-ttu-id="3ffce-118">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3ffce-118">Parameters</span></span>](#parameter)  
  
-   [<span data-ttu-id="3ffce-119">주의</span><span class="sxs-lookup"><span data-stu-id="3ffce-119">Remarks</span></span>](#remark)  
  
-   [<span data-ttu-id="3ffce-120">예</span><span class="sxs-lookup"><span data-stu-id="3ffce-120">Examples</span></span>](#example)  
  
##  <a name="integration-services-server-and-project-file"></a><a name="server"></a> <span data-ttu-id="3ffce-121">Integration Services 서버 및 프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="3ffce-121">Integration Services Server and Project File</span></span>  
 <span data-ttu-id="3ffce-122">를 사용 `dtexec` 하 여 서버에서 패키지를 실행 하는 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 카탈로그를 호출 합니다 `dtexec` [. create_execution &#40;ssisdb 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [카탈로그. set_execution_parameter_value &#40;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) ssisdb 데이터베이스&#41;및 [카탈로그. start_execution](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) ssisdb 데이터베이스 &#40;저장 프로시저를 사용 하 여 실행을 만들고, 매개 변수 값을 설정 하 고, 실행을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-122">When you use `dtexec` to run packages on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, `dtexec` calls the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) stored procedures to create an execution, set parameter values and start the execution.</span></span> <span data-ttu-id="3ffce-123">실행 로그는 관련 뷰의 서버에서 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 사용 가능한 표준 보고서를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-123">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3ffce-124">보고서에 대한 자세한 내용은 [Integration Services 서버를 위한 보고서](../reports-for-the-integration-services-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-124">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="3ffce-125">다음은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에서의 패키지 실행 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-125">The following is an example of executing a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
DTExec /ISSERVER "\SSISDB\folderB\Integration Services Project17\Package.dtsx" /SERVER "." /Envreference 2 /Par "$Project::ProjectParameter(Int32)";1 /Par "Parameter(Int32)";21 /Par "CM.sqlcldb2.SSIS_repro.InitialCatalog";ssisdb /Par "$ServerOption::SYNCHRONIZED(Boolean)";True  
```  
  
 <span data-ttu-id="3ffce-126">`dtexec`를 사용하여 .ispac 프로젝트 파일에서 패키지를 실행할 경우 이와 관련하여 프로젝트 경로와 프로젝트 스트림 이름을 지정하는 데 사용하는 /Proj[ect] 및 /Pack[age] 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-126">When you use `dtexec` to run a package from the .ispac project file, the related options are: /Proj[ect] and /Pack[age] that are used to specify the project path and package stream name.</span></span> <span data-ttu-id="3ffce-127">**에서** Integration Services 프로젝트 변환 마법사 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 실행하여 프로젝트를 프로젝트 배포 모델로 변환할 경우 마법사가 .ispac 프로젝트 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-127">When you convert a project to the project deployment model by running the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the wizard generates an .ispac projec file.</span></span> <span data-ttu-id="3ffce-128">자세한 내용은 [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-128">For more information, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="3ffce-129">`dtexec`타사 일정 도구와 함께를 사용 하 여 서버에 배포 된 패키지를 예약할 수 있습니다 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3ffce-129">You can use `dtexec` with third-party scheduling tools to schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
##  <a name="installation-considerations-on-64-bit-computers"></a><a name="bit"></a> <span data-ttu-id="3ffce-130">64비트 컴퓨터에서의 설치 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3ffce-130">Installation Considerations on 64-bit Computers</span></span>  
 <span data-ttu-id="3ffce-131">64비트 컴퓨터의 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 64비트 버전의 `dtexec` 유틸리티(dtexec.exe)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-131">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs a 64-bit version of the `dtexec` utility (dtexec.exe).</span></span> <span data-ttu-id="3ffce-132">특정 패키지를 32비트 모드로 실행해야 하는 경우 `dtexec` 유틸리티의 32비트 버전을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-132">If you have to run certain packages in 32-bit mode, you will have to install the 32-bit version of the `dtexec` utility.</span></span> <span data-ttu-id="3ffce-133">32비트 버전의 `dtexec` 유틸리티를 설치하려면 설치 도중 클라이언트 도구 또는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-133">To install the 32-bit version of the `dtexec` utility, you must select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="3ffce-134">기본적으로 64비트 및 32비트 버전의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 명령 프롬프트 유틸리티가 모두 설치되어 있는 64비트 컴퓨터는 명령 프롬프트에서 32비트 버전을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-134">By default, a 64-bit computer that has both the 64-bit and 32-bit versions of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] command prompt utility installed will run the 32-bit version at the command prompt.</span></span> <span data-ttu-id="3ffce-135">64비트 버전에 대한 디렉터리 경로 앞에 32비트 버전에 대한 디렉터리 경로가 PATH 환경 변수에 나타나기 때문에 32비트 버전이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-135">The 32-bit version runs because the directory path for the 32-bit version appears in the PATH environment variable before the directory path for the 64-bit version.</span></span> <span data-ttu-id="3ffce-136">일반적으로 32비트 디렉터리 경로는 *\<drive>* :\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn이고, 64비트 디렉터리 경로는 *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-136">(Typically, the 32-bit directory path is *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn, while the 64-bit directory path is *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ffce-137">SQL Server 에이전트를 사용하여 유틸리티를 실행하는 경우 SQL Server 에이전트는 64비트 버전의 유틸리티를 자동으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-137">If you use SQL Server Agent to run the utility, SQL Server Agent automatically uses the 64-bit version of the utility.</span></span> <span data-ttu-id="3ffce-138">SQL Server 에이전트는 PATH 환경 변수가 아닌 레지스트리를 사용하여 유틸리티에 대한 올바른 실행 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-138">SQL Server Agent uses the registry, not the PATH environment variable, to locate the correct executable for the utility.</span></span>  
  
 <span data-ttu-id="3ffce-139">명령 프롬프트에서 64비트 버전의 유틸리티를 실행하기 위해 다음 동작 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-139">To ensure that you run the 64-bit version of the utility at the command prompt, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="3ffce-140">명령 프롬프트 창을 열고 64비트 버전의 유틸리티가 포함되어 있는 디렉터리( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn)로 변경한 다음, 해당 위치에서 유틸리티를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-140">Open a Command Prompt window, change to the directory that contains the 64-bit version of the utility (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn), and then run the utility from that location.</span></span>  
  
-   <span data-ttu-id="3ffce-141">명령 프롬프트에서 64비트 버전의 유틸리티에 대한 전체 경로( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn)를 입력하여 유틸리티를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-141">At the command prompt, run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) to the 64-bit version of the utility.</span></span>  
  
-   <span data-ttu-id="3ffce-142">PATH 환경 변수에서 32비트 경로( *\<drive>* :\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) 앞에 64비트 경로( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn)를 배치하여 변수에서의 경로 순서를 영구적으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-142">Permanently change the order of the paths in the PATH environment variable by placing the 64-bit path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) before the 32-bit path (*\<drive>*:\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) in the variable.</span></span>  
  
##  <a name="considerations-on-computers-with-side-by-side-installations"></a><a name="side"></a> <span data-ttu-id="3ffce-143">병렬 설치 컴퓨터에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3ffce-143">Considerations on Computers with Side-by-Side Installations</span></span>  
 <span data-ttu-id="3ffce-144">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 또는 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]가 설치된 컴퓨터에 When [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]를 설치하면 여러 버전의 `dtexec` 유틸리티가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-144">When [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] is installed on a machine that has [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] installed, multiple versions of the `dtexec` utility are installed.</span></span>  
  
 <span data-ttu-id="3ffce-145">올바른 버전의 유틸리티가 실행되도록 하려면 명령 프롬프트에서 전체 경로( *\<drive>* :\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn)를 입력하는 방식으로 유틸리티를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-145">To ensure that you run the correct version of the utility, at the command prompt run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn).</span></span>  
  
##  <a name="phases-of-execution"></a><a name="phases"></a> <span data-ttu-id="3ffce-146">실행 단계</span><span class="sxs-lookup"><span data-stu-id="3ffce-146">Phases of Execution</span></span>  
 <span data-ttu-id="3ffce-147">이 유틸리티를 실행하면 다음 4단계가</span><span class="sxs-lookup"><span data-stu-id="3ffce-147">The utility has four phases that it proceeds through as it executes.</span></span> <span data-ttu-id="3ffce-148">수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-148">The phases are as follows:</span></span>  
  
1.  <span data-ttu-id="3ffce-149">명령을 읽어들이는 단계: 명령 프롬프트는 지정된 옵션 및 인수 목록을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-149">Command sourcing phase: The command prompt reads the list of options and arguments that have been specified.</span></span> <span data-ttu-id="3ffce-150">**/?**</span><span class="sxs-lookup"><span data-stu-id="3ffce-150">All subsequent phases are skipped if a **/?**</span></span> <span data-ttu-id="3ffce-151">또는 **/HELP** 옵션이 있으면 이후의 모든 단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-151">or **/HELP** option is encountered.</span></span>  
  
2.  <span data-ttu-id="3ffce-152">패키지 로드 단계: `/SQL` , **/file**또는 옵션으로 지정 된 패키지가 `/DTS` 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-152">Package load phase: The package specified by the `/SQL`, **/FILE**, or `/DTS` option is loaded.</span></span>  
  
3.  <span data-ttu-id="3ffce-153">구성 단계: 옵션은 다음 순서로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-153">Configuration phase: Options are processed in this order:</span></span>  
  
    -   <span data-ttu-id="3ffce-154">패키지 플래그, 변수 및 속성을 설정하는 옵션</span><span class="sxs-lookup"><span data-stu-id="3ffce-154">Options that set package flags, variables, and properties.</span></span>  
  
    -   <span data-ttu-id="3ffce-155">패키지 버전 및 빌드를 확인하는 옵션</span><span class="sxs-lookup"><span data-stu-id="3ffce-155">Options that verify the package version and build.</span></span>  
  
    -   <span data-ttu-id="3ffce-156">보고와 같은 유틸리티의 런타임 동작을 구성하는 옵션</span><span class="sxs-lookup"><span data-stu-id="3ffce-156">Options that configure the run-time behavior of the utility, such as reporting.</span></span>  
  
4.  <span data-ttu-id="3ffce-157">유효성 검사 및 실행 단계: 패키지가 실행되거나 **/VALIDATE** 옵션을 지정한 경우에는 실행되지 않고 유효성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-157">Validation and execution phase: The package is run, or validated without running if the **/VALIDATE** option was specified.</span></span>  
  
##  <a name="exit-codes-returned"></a><a name="exit"></a> <span data-ttu-id="3ffce-158">반환된 종료 코드</span><span class="sxs-lookup"><span data-stu-id="3ffce-158">Exit Codes Returned</span></span>  
 <span data-ttu-id="3ffce-159">**dtexec 유틸리티에서 반환된 종료 코드**</span><span class="sxs-lookup"><span data-stu-id="3ffce-159">**Exit codes returned from dtexec utility**</span></span>  
  
 <span data-ttu-id="3ffce-160">패키지를 실행하면 `dtexec`에서 종료 코드를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-160">When a package runs, `dtexec` can return an exit code.</span></span> <span data-ttu-id="3ffce-161">종료 코드는 ERRORLEVEL 변수를 채우는 데 사용되며 이 변수의 값은 배치 파일 내의 분기 논리 또는 조건문에서 테스트될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-161">The exit code is used to populate the ERRORLEVEL variable, the value of which can then be tested in conditional statements or branching logic within a batch file.</span></span> <span data-ttu-id="3ffce-162">다음 표에서는 `dtexec` 종료 시 유틸리티에서 설정할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-162">The following table lists the values that the `dtexec` utility can set when exiting.</span></span>  
  
|<span data-ttu-id="3ffce-163">값</span><span class="sxs-lookup"><span data-stu-id="3ffce-163">Value</span></span>|<span data-ttu-id="3ffce-164">Description</span><span class="sxs-lookup"><span data-stu-id="3ffce-164">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ffce-165">0</span><span class="sxs-lookup"><span data-stu-id="3ffce-165">0</span></span>|<span data-ttu-id="3ffce-166">패키지가 성공적으로 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-166">The package executed successfully.</span></span>|  
|<span data-ttu-id="3ffce-167">1</span><span class="sxs-lookup"><span data-stu-id="3ffce-167">1</span></span>|<span data-ttu-id="3ffce-168">패키지가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-168">The package failed.</span></span>|  
|<span data-ttu-id="3ffce-169">3</span><span class="sxs-lookup"><span data-stu-id="3ffce-169">3</span></span>|<span data-ttu-id="3ffce-170">사용자가 패키지를 취소했습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-170">The package was canceled by the user.</span></span>|  
|<span data-ttu-id="3ffce-171">4</span><span class="sxs-lookup"><span data-stu-id="3ffce-171">4</span></span>|<span data-ttu-id="3ffce-172">유틸리티에서 요청된 패키지를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-172">The utility was unable to locate the requested package.</span></span> <span data-ttu-id="3ffce-173">패키지를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-173">The package could not be found.</span></span>|  
|<span data-ttu-id="3ffce-174">5</span><span class="sxs-lookup"><span data-stu-id="3ffce-174">5</span></span>|<span data-ttu-id="3ffce-175">유틸리티에서 요청된 패키지를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-175">The utility was unable to load the requested package.</span></span> <span data-ttu-id="3ffce-176">패키지를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-176">The package could not be loaded.</span></span>|  
|<span data-ttu-id="3ffce-177">6</span><span class="sxs-lookup"><span data-stu-id="3ffce-177">6</span></span>|<span data-ttu-id="3ffce-178">유틸리티의 명령줄에서 내부 구문 오류 또는 의미 체계 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-178">The utility encountered an internal error of syntactic or semantic errors in the command line.</span></span>|  
  
##  <a name="syntax-rules"></a><a name="syntaxRules"></a> <span data-ttu-id="3ffce-179">구문 규칙</span><span class="sxs-lookup"><span data-stu-id="3ffce-179">Syntax Rules</span></span>  
 <span data-ttu-id="3ffce-180">**유틸리티 구문 규칙**</span><span class="sxs-lookup"><span data-stu-id="3ffce-180">**Utility syntax rules**</span></span>  
  
 <span data-ttu-id="3ffce-181">모든 옵션은 슬래시(/) 또는 빼기 기호(-)로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-181">All options must start with a slash (/) or a minus sign (-).</span></span> <span data-ttu-id="3ffce-182">여기에 표시된 옵션은 슬래시(/)로 시작하지만 빼기 기호(-)를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-182">The options that are shown here start with a slash (/), but the minus sign (-) can be substituted.</span></span>  
  
 <span data-ttu-id="3ffce-183">인수에 공백이 있는 경우 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-183">An argument must be enclosed in quotation marks if it contains a space.</span></span> <span data-ttu-id="3ffce-184">인수를 따옴표로 묶지 않으면 인수에 공백을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-184">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="3ffce-185">따옴표로 묶인 문자열 안의 큰따옴표는 이스케이프된 작은따옴표를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-185">Doubled quotation marks within quoted strings represent escaped single quotation marks.</span></span>  
  
 <span data-ttu-id="3ffce-186">암호를 제외한 옵션 및 인수는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-186">Options and arguments are not case-sensitive, except for passwords.</span></span>  
  
##  <a name="using-dtexec-from-the-xp_cmdshell"></a><a name="cmdshell"></a> <span data-ttu-id="3ffce-187">xp_cmdshell에서 dtexec 사용</span><span class="sxs-lookup"><span data-stu-id="3ffce-187">Using dtexec from the xp_cmdshell</span></span>  
 <span data-ttu-id="3ffce-188">**xp_cmdshell에서 dtexec 사용**</span><span class="sxs-lookup"><span data-stu-id="3ffce-188">**Using dtexec from the xp_cmdshell**</span></span>  
  
 <span data-ttu-id="3ffce-189">**xp_cmdshell** 프롬프트에서 dtexec를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-189">You can run dtexec from the **xp_cmdshell** prompt.</span></span> <span data-ttu-id="3ffce-190">다음 예에서는 UpsertData.dtsx라는 패키지를 실행하고 반환 코드를 무시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-190">The following example shows how to run a package called UpsertData.dtsx and ignore the return code:</span></span>  
  
```  
EXEC xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
 <span data-ttu-id="3ffce-191">다음 예에서는 동일한 패키지를 실행하고 반환 코드를 캡처하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-191">The following example shows how to run the same package and capture the return code:</span></span>  
  
```  
DECLARE @returncode int  
EXEC @returncode = xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ffce-192">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 기본적으로 새 설치에 대해 **xp_cmdshell** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-192">In [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **xp_cmdshell** option is disabled by default on new installations.</span></span> <span data-ttu-id="3ffce-193">이 옵션은 **sp_configure** 시스템 저장 프로시저를 실행하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-193">The option can be enabled by running the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="3ffce-194">자세한 내용은 [xp_cmdshell 서버 구성 옵션](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-194">For more information, see [xp_cmdshell Server Configuration Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).</span></span>  
  
##  <a name="syntax"></a><a name="syntax"></a> <span data-ttu-id="3ffce-195">구문</span><span class="sxs-lookup"><span data-stu-id="3ffce-195">Syntax</span></span>  
  
```  
dtexec /option [value] [/option [value]]...  
```  
  
##  <a name="parameters"></a><a name="parameter"></a> <span data-ttu-id="3ffce-196">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3ffce-196">Parameters</span></span>  
  
-   <span data-ttu-id="3ffce-197">**/?**</span><span class="sxs-lookup"><span data-stu-id="3ffce-197">**/?**</span></span> [*option_name*]: 선택 사항입니다. <span data-ttu-id="3ffce-199">지정된 *option_name* 에 대한 명령 프롬프트 옵션 또는 도움말을 표시하고 유틸리티를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-199">Displays the command prompt options, or displays help for the specified *option_name* and then closes the utility.</span></span>  
  
     <span data-ttu-id="3ffce-200">*Option_name* 인수를 지정 하면에서 `dtexec` 온라인 설명서를 시작 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하 고 dtexec 유틸리티 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-200">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="3ffce-201">**/Ca [llerInfo]**:</span><span class="sxs-lookup"><span data-stu-id="3ffce-201">**/Ca[llerInfo]**:</span></span>   
                  <span data-ttu-id="3ffce-202">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-202">Optional.</span></span> <span data-ttu-id="3ffce-203">패키지 실행에 대한 추가 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-203">Specifies additional information for a package execution.</span></span> <span data-ttu-id="3ffce-204">SQL Server 에이전트를 사용하여 패키지를 실행할 때 에이전트는 패키지 실행이 SQL Server 에이전트로 호출되었음을 나타내도록 이 인수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-204">When you run a package using SQL Server Agent, agent sets this argument to indicate that the package execution is invoked by SQL Server Agent.</span></span> <span data-ttu-id="3ffce-205">`dtexec` 유틸리티가 명령줄로부터 실행될 경우 이 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-205">This parameter is ignored when the `dtexec` utility is run from the command line.</span></span>  
  
-   <span data-ttu-id="3ffce-206">**/CheckF[ile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-206">**/CheckF[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="3ffce-207">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-207">Optional.</span></span> <span data-ttu-id="3ffce-208">패키지의 `CheckpointFileName` 속성을 *filespec*의 경로 및 파일 spemandcified 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-208">Sets the `CheckpointFileName` property on the package to the path and file spemandcified in *filespec*.</span></span> <span data-ttu-id="3ffce-209">이 파일은 패키지를 다시 시작할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-209">This file is used when the package restarts.</span></span> <span data-ttu-id="3ffce-210">이 옵션을 지정하고 파일 이름 값을 제공하지 않으면 패키지의 `CheckpointFileName`이 빈 문자열로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-210">If this option is specified and no value is supplied for the file name, the `CheckpointFileName` for the package is set to an empty string.</span></span> <span data-ttu-id="3ffce-211">이 옵션을 지정하지 않으면 패키지의 값이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-211">If this option is not specified, the values in the package are retained.</span></span>  
  
-   <span data-ttu-id="3ffce-212">**/CheckP [ointing]** _{on\off}_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-212">**/CheckP[ointing]** _{on\off}_:</span></span>   
                  <span data-ttu-id="3ffce-213">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-213">Optional.</span></span> <span data-ttu-id="3ffce-214">패키지 실행 중 패키지에서 검사점을 사용하는지 여부를 결정하는 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-214">Sets a value that determines whether the package will use checkpoints during package execution.</span></span> <span data-ttu-id="3ffce-215">**on** 값에서는 실패한 패키지를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-215">The value **on** specifies that a failed package is to be rerun.</span></span> <span data-ttu-id="3ffce-216">실패한 패키지가 다시 실행되면 런타임 엔진에서 검사점 파일을 사용하여 실패한 지점에서 패키지를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-216">When the failed package is rerun, the run-time engine uses the checkpoint file to restart the package from the point of failure.</span></span>  
  
     <span data-ttu-id="3ffce-217">값을 지정하지 않고 이 옵션을 선언할 경우 기본값은 on입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-217">The default value is on if the option is declared without a value.</span></span> <span data-ttu-id="3ffce-218">값을 on으로 설정한 경우 검사점 파일을 찾을 수 없으면 패키지를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-218">Package execution will fail if the value is set to on and the checkpoint file cannot be found.</span></span> <span data-ttu-id="3ffce-219">이 옵션을 지정하지 않으면 패키지에 설정된 값이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-219">If this option is not specified, the value set in the package is retained.</span></span> <span data-ttu-id="3ffce-220">자세한 내용은 [검사점을 사용하여 패키지 다시 시작](restart-packages-by-using-checkpoints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-220">For more information, see [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md).</span></span>  
  
     <span data-ttu-id="3ffce-221">Dtexec의 **/con** 옵션은 `SaveCheckpoints` 패키지의 속성을 True로 설정 하 고 속성을 항상로 설정 하는 것과 같습니다 `CheckpointUsage` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-221">The **/CheckPointing on** option of dtexec is equivalent to setting the `SaveCheckpoints` property of the package to True, and the `CheckpointUsage` property to Always.</span></span>  
  
-   <span data-ttu-id="3ffce-222">**/Com[mandFile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-222">**/Com[mandFile]** _filespec_:</span></span>   
                  <span data-ttu-id="3ffce-223">(선택 사항).</span><span class="sxs-lookup"><span data-stu-id="3ffce-223">(Optional).</span></span> <span data-ttu-id="3ffce-224">`dtexec`와 함께 실행되는 명령 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-224">Specifies the command options that run with `dtexec`.</span></span> <span data-ttu-id="3ffce-225">*filespec* 에 지정된 파일을 열고 이 파일에서 EOF가 검색될 때까지 옵션을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-225">The file specified in *filespec* is opened and options from the file are read until EOF is found in the file.</span></span> <span data-ttu-id="3ffce-226">*filespec* 는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-226">*filespec* is a text file.</span></span> <span data-ttu-id="3ffce-227">*filespec* 인수는 패키지 실행과 연관시킬 명령 파일의 이름과 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-227">The *filespec* argument specifies the file name and path of the command file to associate with the execution of the package.</span></span>  
  
-   <span data-ttu-id="3ffce-228">**/Arys [igFile]** _filespec_: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-228">**/Conf[igFile]** _filespec_: Optional.</span></span> <span data-ttu-id="3ffce-229">값을 추출할 구성 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-229">Specifies a configuration file to extract values from.</span></span> <span data-ttu-id="3ffce-230">이 옵션을 사용하면 패키지의 디자인 타임에 지정한 구성과 다르게 런타임 구성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-230">Using this option, you can set a run-time configuration that differs from the configuration that was specified at design time for the package.</span></span> <span data-ttu-id="3ffce-231">다른 구성 설정을 XML 구성 파일에 저장한 다음 패키지를 실행하기 전에 **ConfigFile** 옵션을 사용하여 이 설정을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-231">You can store different configuration settings in an XML configuration file and then load the settings before package execution by using the **/ConfigFile** option.</span></span>  
  
     <span data-ttu-id="3ffce-232">**/ConfigFile** 옵션을 사용하면 디자인 타임에 지정하지 않은 추가 구성을 런타임에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-232">You can use the **/ConfigFile** option to load additional configurations at run time that you did not specify at design time.</span></span> <span data-ttu-id="3ffce-233">그러나 디자인 타임에도 지정한 구성 값을 **/ConfigFile** 옵션을 사용하여 바꿀 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-233">However, you cannot use the **/ConfigFile** option to replace configured values that you also specified at design time.</span></span> <span data-ttu-id="3ffce-234">패키지 구성이 적용되는 방법을 이해하려면 [Package Configurations](../package-configurations.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-234">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md).</span></span>  
  
-   <span data-ttu-id="3ffce-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span></span>   
                  <span data-ttu-id="3ffce-236">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-236">Optional.</span></span> <span data-ttu-id="3ffce-237">이름 또는 GUID가 지정된 연결 관리자가 패키지에 있음을 지정하고 연결 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-237">Specifies that the connection manager with the specified name or GUID is located in the package, and specifies a connection string.</span></span>  
  
     <span data-ttu-id="3ffce-238">이 옵션을 사용하려면 두 매개 변수 모두를 지정해야 합니다. 즉, *id_or_name* 인수에 연결 관리자 이름 또는 GUID를 제공하고 *connection_string* 인수에 올바른 연결 문자열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-238">This option requires that both parameters be specified: the connection manager name or GUID must be provided in the *id_or_name* argument, and a valid connection string must be specified in the *connection_string* argument.</span></span> <span data-ttu-id="3ffce-239">자세한 내용은 [Integration Services&#40;SSIS&#41; 연결](../connection-manager/integration-services-ssis-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-239">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
     <span data-ttu-id="3ffce-240">런타임에 **/Connection** 옵션을 사용하면 디자인 타임에 지정한 위치와 다른 위치에서 패키지 구성을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-240">At run time, you can use the **/Connection** option to load package configurations from a location other than the location that you specified at design time.</span></span> <span data-ttu-id="3ffce-241">그러면 원래 지정된 값이 이러한 구성 값으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-241">The values of these configurations then replace the values that were originally specified.</span></span> <span data-ttu-id="3ffce-242">그러나 연결 관리자를 사용하는 **구성과 같은 구성에만** /Connection [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-242">However you can use the **/Connection** option only for configurations, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations, that use a connection manager.</span></span> <span data-ttu-id="3ffce-243">패키지 구성이 적용 되는 방법을 이해 하려면 [SQL Server 2014의 Integration Services 기능에 대](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)한 [패키지 구성](../package-configurations.md) 및 동작 변경을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-243">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="3ffce-244">**//Hs [oleLog]** [[*displayoptions*]; [ *list_options*; *src_name_or_guid*] ...]: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-244">**/Cons[oleLog]** [[*displayoptions*];[*list_options*;*src_name_or_guid*]...]: Optional.</span></span> <span data-ttu-id="3ffce-245">패키지 실행 중 지정된 로그 항목을 콘솔에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-245">Displays specified log entries to the console during package execution.</span></span> <span data-ttu-id="3ffce-246">이 옵션을 생략하면 콘솔에 로그 항목이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-246">If this option is omitted, no log entries are shown in the console.</span></span> <span data-ttu-id="3ffce-247">표시를 제한하는 매개 변수 없이 이 옵션을 지정하면 모든 로그 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-247">If the option is specified without parameters that limit the display, every log entry will display.</span></span> <span data-ttu-id="3ffce-248">콘솔에 표시되는 항목을 제한하려면 *displayoptions* 매개 변수를 사용하여 표시할 열을 지정하고 *list_options* 매개 변수를 사용하여 로그 항목 유형을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-248">To limit the entries that are displayed to the console, you can specify the columns to show by using the *displayoptions* parameter, and limit the log entry types by using the *list_options* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ffce-249">매개 변수를 사용 하 여 서버에서 패키지를 실행 하는 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `/ISSERVER` 콘솔 출력이 제한 되며 대부분의 **/Cs [oleLog]** 옵션은 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-249">When you run a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server by using the `/ISSERVER` parameter, console output is limited and most of the **/Cons[oleLog]** options are not applicable.</span></span> <span data-ttu-id="3ffce-250">실행 로그는 관련 뷰의 서버에서 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 사용 가능한 표준 보고서를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-250">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3ffce-251">보고서에 대한 자세한 내용은 [Integration Services 서버를 위한 보고서](../reports-for-the-integration-services-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-251">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
     <span data-ttu-id="3ffce-252">*displayoptions* 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-252">The *displayoptions* values are as follows:</span></span>  
  
    -   <span data-ttu-id="3ffce-253">N(이름)</span><span class="sxs-lookup"><span data-stu-id="3ffce-253">N (Name)</span></span>  
  
    -   <span data-ttu-id="3ffce-254">C(컴퓨터)</span><span class="sxs-lookup"><span data-stu-id="3ffce-254">C (Computer)</span></span>  
  
    -   <span data-ttu-id="3ffce-255">O(운영자)</span><span class="sxs-lookup"><span data-stu-id="3ffce-255">O (Operator)</span></span>  
  
    -   <span data-ttu-id="3ffce-256">S(원본 이름)</span><span class="sxs-lookup"><span data-stu-id="3ffce-256">S (Source Name)</span></span>  
  
    -   <span data-ttu-id="3ffce-257">G(원본 GUID)</span><span class="sxs-lookup"><span data-stu-id="3ffce-257">G (Source GUID)</span></span>  
  
    -   <span data-ttu-id="3ffce-258">X(실행 GUID)</span><span class="sxs-lookup"><span data-stu-id="3ffce-258">X (Execution GUID)</span></span>  
  
    -   <span data-ttu-id="3ffce-259">M(메시지)</span><span class="sxs-lookup"><span data-stu-id="3ffce-259">M (Message)</span></span>  
  
    -   <span data-ttu-id="3ffce-260">T(시간 시작 및 종료 시간)</span><span class="sxs-lookup"><span data-stu-id="3ffce-260">T (Time Start and End)</span></span>  
  
     <span data-ttu-id="3ffce-261">*list_options* 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-261">The *list_options* values are as follows:</span></span>  
  
    -   <span data-ttu-id="3ffce-262">*I* - 포함 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-262">*I* - Specifies the inclusion list.</span></span> <span data-ttu-id="3ffce-263">지정된 원본 이름 또는 GUID만 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-263">Only the source names or GUIDs that are specified are logged.</span></span>  
  
    -   <span data-ttu-id="3ffce-264">*E* - 제외 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-264">*E* - Specifies the exclusion list.</span></span> <span data-ttu-id="3ffce-265">지정된 원본 이름 또는 GUID가 로깅되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-265">The source names or GUIDs that are specified are not logged.</span></span>  
  
    -   <span data-ttu-id="3ffce-266">포함 또는 제외하도록 지정된 *src_name_or_guid* 매개 변수는 이벤트 이름, 원본 이름 또는 원본 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-266">The *src_name_or_guid* parameter specified for inclusion or exclusion is an event name, source name, or source GUID.</span></span>  
  
     <span data-ttu-id="3ffce-267">같은 명령 프롬프트에 여러 **/ConsoleLog** 옵션을 사용하면 다음과 같이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-267">If you use multiple **/ConsoleLog** options on the same command prompt, they interact as follows:</span></span>  
  
    -   <span data-ttu-id="3ffce-268">시각적인 순서에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-268">Their order of appearance has no effect.</span></span>  
  
    -   <span data-ttu-id="3ffce-269">명령줄에 포함 목록이 없으면 모든 유형의 로그 항목에 제외 목록이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-269">If no inclusion lists are present on the command line, exclusion lists are applied against all kinds of log entries.</span></span>  
  
    -   <span data-ttu-id="3ffce-270">명령줄에 포함 목록이 있으면 모든 포함 목록의 집합에 제외 목록이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-270">If any inclusion lists are present on the command line, exclusion lists are applied against the union of all inclusion lists.</span></span>  
  
     <span data-ttu-id="3ffce-271">**/ConsoleLog** 옵션에 대 한 예는 **주의** 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-271">For examples of the **/ConsoleLog** option, see the **Remarks** section.</span></span>  
  
-   <span data-ttu-id="3ffce-272">**/D[ts]** _package_path_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-272">**/D[ts]** _package_path_:</span></span>   
                  <span data-ttu-id="3ffce-273">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-273">Optional.</span></span> <span data-ttu-id="3ffce-274">SSIS 패키지 저장소에서 패키지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-274">Loads a package from the SSIS Package Store.</span></span> <span data-ttu-id="3ffce-275">SSIS 패키지 저장소에 저장된 패키지는 레거시 패키지 배포 모델을 사용하여 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-275">Packages that are stored in the SSIS Package Store, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="3ffce-276">프로젝트 배포 모델을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지를 실행하려면 `/ISServer` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-276">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="3ffce-277">패키지 및 프로젝트 배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-277">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="3ffce-278">*package_path* 인수는 SSIS 패키지 저장소의 루트에서 시작하여 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 상대 경로를 지정하고 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-278">The *package_path* argument specifies the relative path of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package, starting at the root of the SSIS Package Store, and includes the name of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="3ffce-279">*package_path* 인수에 지정된 경로나 파일 이름에 공백이 있는 경우 *package_path* 인수를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-279">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="3ffce-280">`/DTS` 옵션은 `/File` 또는 `/SQL` 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-280">The `/DTS` option cannot be used together with the `/File` or `/SQL` option.</span></span> <span data-ttu-id="3ffce-281">여러 개의 옵션을 지정하는 경우 `dtexec`는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-281">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="3ffce-282">**/De [암호]**  _암호_: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-282">**/De[crypt]**  _password_: Optional.</span></span> <span data-ttu-id="3ffce-283">암호가 암호화된 패키지를 로드할 때 사용할 해독 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-283">Sets the decryption password that is used when you load a package with password encryption.</span></span>  
  
-   <span data-ttu-id="3ffce-284">**/Dump** _error code_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-284">**/Dump** _error code_:</span></span>  
                  <span data-ttu-id="3ffce-285">옵션은 패키지를 실행 하는 동안 하나 이상의 지정 된 이벤트가 발생할 때 디버그 덤프 파일 (.mdmp 및 .tmp)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-285">Optional Creates the debug dump files, .mdmp and .tmp, when one or more specified events occur while the package is running.</span></span> <span data-ttu-id="3ffce-286">*error code* 인수는 시스템에서 디버그 덤프 파일을 만들도록 트리거할 이벤트 코드 유형(오류, 경고 또는 정보)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-286">The *error code* argument specifies the type of event code-error, warning, or information-that will trigger the system to create the debug dump files.</span></span> <span data-ttu-id="3ffce-287">여러 이벤트 코드를 지정하려면 각 *error code* 인수를 세미콜론(;)으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-287">To specify multiple event codes, separate each *error code* argument by a semi-colon (;).</span></span> <span data-ttu-id="3ffce-288">이때 *error code* 인수를 따옴표로 묶으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-288">Do not include quotes with the *error code* argument.</span></span>  
  
     <span data-ttu-id="3ffce-289">다음 예에서는 DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER 오류가 발생할 때 디버그 덤프 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-289">The following example generates the debug dump files when the DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER error occurs.</span></span>  
  
    ```  
    /Dump 0xC020801C  
    ```  
  
     <span data-ttu-id="3ffce-290">기본적으로에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 디버그 덤프 파일을 *\<drive>* : FILEFILES\MICROSOFT SQL server\110\shared\errordumps 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-290">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ffce-291">디버그 덤프 파일에는 중요한 정보가 들어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-291">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="3ffce-292">ACL(액세스 제어 목록)을 사용하여 파일에 대한 액세스를 제한하거나 파일을 액세스가 제한된 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-292">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="3ffce-293">예를 들어 디버그 파일을 Microsoft 지원 서비스에 보내기 전에 중요한 정보나 기밀 정보를 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-293">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="3ffce-294">유틸리티에서 실행 하는 모든 패키지에이 옵션을 적용 하려면 `dtexec` HKEY_LOCAL_MACHINE **DumpOnCodes** \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 레지스트리 키에 값 REG_SZ 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-294">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnCodes** REG_SZ value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="3ffce-295">**DumpOnCodes** 의 데이터 값은 시스템에서 디버그 덤프 파일을 만들도록 트리거할 오류 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-295">The data value in **DumpOnCodes** specifies the error code or codes that will trigger the system to create debug dump files.</span></span> <span data-ttu-id="3ffce-296">여러 오류 코드를 지정하려면 세미콜론(;)으로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-296">Multiple error codes must be separated by a semi-colon (;).</span></span>  
  
     <span data-ttu-id="3ffce-297">레지스트리 키에 **DumpOnCodes** 값을 추가하고 **/Dump** 옵션을 사용하는 경우 시스템에서 두 설정을 기반으로 디버그 덤프 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-297">If you add a **DumpOnCodes** value to the registry key, and use the **/Dump** option, the system will create debug dump files that are based on both settings.</span></span>  
  
     <span data-ttu-id="3ffce-298">디버그 덤프 파일에 대한 자세한 내용은 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-298">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
-   <span data-ttu-id="3ffce-299">**/Caryonerror**:</span><span class="sxs-lookup"><span data-stu-id="3ffce-299">**/DumpOnError**:</span></span>   
                  <span data-ttu-id="3ffce-300">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-300">Optional.</span></span> <span data-ttu-id="3ffce-301">패키지를 실행 하는 동안 오류가 발생 하는 경우 디버그 덤프 파일 (.mdmp 및 .tmp)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-301">Creates the debug dump files, .mdmp and .tmp, when any error occurs while the package is running.</span></span>  
  
     <span data-ttu-id="3ffce-302">기본적으로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 디버그 덤프 파일을 *\<drive>* :\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-302">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ffce-303">디버그 덤프 파일에는 중요한 정보가 들어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-303">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="3ffce-304">ACL(액세스 제어 목록)을 사용하여 파일에 대한 액세스를 제한하거나 파일을 액세스가 제한된 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-304">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="3ffce-305">예를 들어 디버그 파일을 Microsoft 지원 서비스에 보내기 전에 중요한 정보나 기밀 정보를 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-305">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="3ffce-306">유틸리티에서 실행 하는 모든 패키지에이 옵션을 적용 하려면 `dtexec` HKEY_LOCAL_MACHINE **DumpOnError** \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 레지스트리 키에 REG_DWORD 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-306">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnError** REG_DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="3ffce-307">다음 값을 사용 하 여 다음을 수행 해야 합니다. **/cREG_DWORD** **onerror** onerror 옵션을 유틸리티와 함께 사용 해야 하는지 여부를 결정 합니다 `dtexec` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-307">The value of the **DumpOnError** REG_DWORD value determines whether the **/DumpOnError** option needs to be used with the `dtexec` utility:</span></span>  
  
    -   <span data-ttu-id="3ffce-308">0이 아닌 데이터 값은 유틸리티에 **/Cfileonerror** 옵션을 사용 하는지 여부에 관계 없이 오류가 발생할 때 시스템에서 디버그 덤프 파일을 만들도록 지정 합니다 `dtexec` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-308">A non-zero data value indicates that the system will create debug dump files when any error occurs, regardless of whether you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
    -   <span data-ttu-id="3ffce-309">0이 아닌 데이터 값은 유틸리티에 **/Dumponerror** 옵션을 사용 하지 않는 한 시스템에서 디버그 덤프 파일을 만들지 않음을 나타냅니다 `dtexec` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-309">A zero data value indicates that the system will not create the debug dump files unless you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
     <span data-ttu-id="3ffce-310">디버그 덤프 파일에 대한 자세한 내용은 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-310">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)</span></span>  
  
-   <span data-ttu-id="3ffce-311">`/Env[Reference]`*환경 참조 ID*:</span><span class="sxs-lookup"><span data-stu-id="3ffce-311">`/Env[Reference]` *environment reference ID*:</span></span>   
                  <span data-ttu-id="3ffce-312">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-312">Optional.</span></span> <span data-ttu-id="3ffce-313">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지에 대해 패키지 실행에서 사용되는 환경 참조(ID)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-313">Specifies the environment reference (ID) that is used by the package execution, for a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="3ffce-314">변수에 바인딩하도록 구성된 매개 변수는 환경에 포함된 변수 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-314">The parameters configured to bind to variables will use the values of the variables that are contained in the environment.</span></span>  
  
     <span data-ttu-id="3ffce-315">`/Env[Reference]` 옵션은 `/ISServer` 및 `/Server` 옵션과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-315">You use `/Env[Reference]` option together with the `/ISServer` and the `/Server` options.</span></span>  
  
     <span data-ttu-id="3ffce-316">이 매개 변수는 SQL Server 에이전트에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-316">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="3ffce-317">**/F[ile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-317">**/F[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="3ffce-318">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-318">Optional.</span></span> <span data-ttu-id="3ffce-319">파일 시스템에 저장된 패키지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-319">Loads a package that is saved in the file system.</span></span> <span data-ttu-id="3ffce-320">파일 시스템에 저장된 패키지는 레거시 패키지 배포 모델을 사용하여 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-320">Packages that are saved in the file system, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="3ffce-321">프로젝트 배포 모델을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지를 실행하려면 `/ISServer` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-321">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="3ffce-322">패키지 및 프로젝트 배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-322">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)</span></span>  
  
     <span data-ttu-id="3ffce-323">*filespec* 인수는 패키지의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-323">The *filespec* argument specifies the path and file name of the package.</span></span> <span data-ttu-id="3ffce-324">경로는 UNC(Universal Naming Convention) 경로나 로컬 경로로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-324">You can specify the path as either a Universal Naming Convention (UNC) path or a local path.</span></span> <span data-ttu-id="3ffce-325">*filespec* 인수에 지정된 경로나 파일 이름에 공백이 있는 경우 *filespec* 인수를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-325">If the path or file name specified in the *filespec* argument contains a space, you must put quotation marks around the *filespec* argument.</span></span>  
  
     <span data-ttu-id="3ffce-326">`/File` 옵션은 `/DTS` 또는 `/SQL` 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-326">The `/File` option cannot be used together with the `/DTS` or `/SQL` option.</span></span> <span data-ttu-id="3ffce-327">여러 개의 옵션을 지정하는 경우 `dtexec`는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-327">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="3ffce-328">**/H [elp]** [*Option_name*]: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-328">**/H[elp]** [*option_name*]: Optional.</span></span> <span data-ttu-id="3ffce-329">옵션에 대한 도움말 또는 지정된 *option_name* 에 대한 도움말을 표시하고 유틸리티를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-329">Displays help for the options, or displays help for the specified *option_name* and closes the utility.</span></span>  
  
     <span data-ttu-id="3ffce-330">*Option_name* 인수를 지정 하면에서 `dtexec` 온라인 설명서를 시작 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하 고 dtexec 유틸리티 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-330">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="3ffce-331">`/ISServer`*packagepath*:</span><span class="sxs-lookup"><span data-stu-id="3ffce-331">`/ISServer` *packagepath*:</span></span>  
                  <span data-ttu-id="3ffce-332">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-332">Optional.</span></span> <span data-ttu-id="3ffce-333">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-333">Runs a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="3ffce-334">*PackagePath* 인수는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지의 전체 경로 및 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-334">The *PackagePath* argument specifies the full path and file name of the package deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="3ffce-335">*PackagePath* 인수에 지정된 경로나 파일 이름에 공백이 있는 경우 *PackagePath* 인수를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-335">If the path or file name specified in the *PackagePath* argument contains a space, you must put quotation marks around the *PackagePath* argument.</span></span>  
  
     <span data-ttu-id="3ffce-336">패키지 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-336">The package format is as follows:</span></span>  
  
    ```  
    \<catalog name>\<folder name>\<project name>\package file name  
    ```  
  
     <span data-ttu-id="3ffce-337">`/Server` 옵션은 `/ISSERVER` 옵션과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-337">You use `/Server` option together with the `/ISSERVER` option.</span></span> <span data-ttu-id="3ffce-338">Windows 인증만 SSIS 서버에서 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-338">Only Windows Authentication can execute a package on the SSIS Server.</span></span> <span data-ttu-id="3ffce-339">현재 Windows 사용자는 패키지에 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-339">The current Windows user is used to access the package.</span></span> <span data-ttu-id="3ffce-340">/Server 옵션을 생략할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 로컬 인스턴스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-340">If the /Server option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="3ffce-341">`/ISSERVER` 옵션은 `/DTS`, `/SQL` 또는 `/File` 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-341">The `/ISSERVER` option cannot be used together with the `/DTS`, `/SQL` or `/File` option.</span></span> <span data-ttu-id="3ffce-342">여러 개의 옵션을 지정하는 경우 dtexec는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-342">If multiple options are specified, dtexec fails.</span></span>  
  
     <span data-ttu-id="3ffce-343">이 매개 변수는 SQL Server 에이전트에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-343">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="3ffce-344">**/L[ogger]** _classid_orprogid;configstring_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-344">**/L[ogger]** _classid_orprogid;configstring_:</span></span>  
                  <span data-ttu-id="3ffce-345">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-345">Optional.</span></span> <span data-ttu-id="3ffce-346">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 실행에 하나 이상의 로그 공급자를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-346">Associates one or more log providers with the execution of an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="3ffce-347">*classid_orprogid* 매개 변수는 로그 공급자를 지정하며 클래스 GUID로 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-347">The *classid_orprogid* parameter specifies the log provider, and can be specified as a class GUID.</span></span> <span data-ttu-id="3ffce-348">*configstring* 은 로그 공급자를 구성하는 데 사용되는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-348">The *configstring* is the string that is used to configure the log provider.</span></span>  
  
     <span data-ttu-id="3ffce-349">다음 목록에서는 사용 가능한 로그 공급자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-349">The following list shows the available log providers:</span></span>  
  
    -   <span data-ttu-id="3ffce-350">텍스트 파일:</span><span class="sxs-lookup"><span data-stu-id="3ffce-350">Text file:</span></span>  
  
        -   <span data-ttu-id="3ffce-351">ProgID: DTS.LogProviderTextFile.1</span><span class="sxs-lookup"><span data-stu-id="3ffce-351">ProgID: DTS.LogProviderTextFile.1</span></span>  
  
        -   <span data-ttu-id="3ffce-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span><span class="sxs-lookup"><span data-stu-id="3ffce-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span></span>  
  
    -   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<span data-ttu-id="3ffce-353">:</span><span class="sxs-lookup"><span data-stu-id="3ffce-353">:</span></span>  
  
        -   <span data-ttu-id="3ffce-354">ProgID: DTS.LogProviderSQLProfiler.1</span><span class="sxs-lookup"><span data-stu-id="3ffce-354">ProgID: DTS.LogProviderSQLProfiler.1</span></span>  
  
        -   <span data-ttu-id="3ffce-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span><span class="sxs-lookup"><span data-stu-id="3ffce-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3ffce-356">:</span><span class="sxs-lookup"><span data-stu-id="3ffce-356">:</span></span>  
  
        -   <span data-ttu-id="3ffce-357">ProgID: DTS.LogProviderSQLServer.1</span><span class="sxs-lookup"><span data-stu-id="3ffce-357">ProgID: DTS.LogProviderSQLServer.1</span></span>  
  
        -   <span data-ttu-id="3ffce-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span><span class="sxs-lookup"><span data-stu-id="3ffce-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span></span>  
  
    -   <span data-ttu-id="3ffce-359">Windows 이벤트 로그:</span><span class="sxs-lookup"><span data-stu-id="3ffce-359">Windows Event Log:</span></span>  
  
        -   <span data-ttu-id="3ffce-360">ProgID: DTS.LogProviderEventLog.1</span><span class="sxs-lookup"><span data-stu-id="3ffce-360">ProgID: DTS.LogProviderEventLog.1</span></span>  
  
        -   <span data-ttu-id="3ffce-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span><span class="sxs-lookup"><span data-stu-id="3ffce-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span></span>  
  
    -   <span data-ttu-id="3ffce-362">XML 파일:</span><span class="sxs-lookup"><span data-stu-id="3ffce-362">XML File:</span></span>  
  
        -   <span data-ttu-id="3ffce-363">ProgID: DTS.LogProviderXMLFile.1</span><span class="sxs-lookup"><span data-stu-id="3ffce-363">ProgID: DTS.LogProviderXMLFile.1</span></span>  
  
        -   <span data-ttu-id="3ffce-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span><span class="sxs-lookup"><span data-stu-id="3ffce-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span></span>  
  
-   <span data-ttu-id="3ffce-365">**/M[axConcurrent]** _concurrent_executables_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-365">**/M[axConcurrent]** _concurrent_executables_:</span></span>  
                  <span data-ttu-id="3ffce-366">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-366">Optional.</span></span> <span data-ttu-id="3ffce-367">패키지에서 동시에 실행할 수 있는 실행 파일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-367">Specifies the number of executable files that the package can run concurrently.</span></span> <span data-ttu-id="3ffce-368">값은 음수가 아닌 정수 또는 -1로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-368">The value specified must be either a non-negative integer, or -1.</span></span> <span data-ttu-id="3ffce-369">-1 값은 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 에서 패키지를 실행하는 컴퓨터의 총 프로세서 수에 2를 더한 값과 같은 동시에 실행 가능한 최대 실행 파일 수를 허용함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-369">A value of -1 means that [!INCLUDE[ssIS](../../includes/ssis-md.md)] will allow a maximum number of concurrently running executables that is equal to the total number of processors on the computer executing the package, plus two.</span></span>  
  
-   <span data-ttu-id="3ffce-370">**/Pack[age]** _PackageName_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-370">**/Pack[age]** _PackageName_:</span></span>  
                  <span data-ttu-id="3ffce-371">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-371">Optional.</span></span> <span data-ttu-id="3ffce-372">실행되는 패키지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-372">Specifies the package that is executed.</span></span> <span data-ttu-id="3ffce-373">이 매개 변수는 주로 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 패키지를 실행할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-373">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="3ffce-374">**/P [assword]** _암호_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-374">**/P[assword]** _password_:</span></span>  
                  <span data-ttu-id="3ffce-375">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-375">Optional.</span></span> <span data-ttu-id="3ffce-376">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증으로 보호되는 패키지를 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-376">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="3ffce-377">이 옵션은 **/User** 옵션과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-377">This option is used together with the **/User** option.</span></span> <span data-ttu-id="3ffce-378">**/Password** 옵션을 생략하고 **/User** 옵션을 사용하면 빈 암호가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-378">If the **/Password** option is omitted and the **/User** option is used, a blank password is used.</span></span> <span data-ttu-id="3ffce-379">*password* 값은 따옴표로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-379">The *password* value may be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="3ffce-380">**/Ps [ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)]; *literal_value*: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-380">**/Par[ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)]; *literal_value*: Optional.</span></span> <span data-ttu-id="3ffce-381">매개 변수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-381">Specifies parameter values.</span></span> <span data-ttu-id="3ffce-382">여러 **/Parameter** 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-382">Multiple **/Parameter** options can be specified.</span></span> <span data-ttu-id="3ffce-383">데이터 형식은 문자열인 CLR TypeCodes입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-383">The data types are CLR TypeCodes as strings.</span></span> <span data-ttu-id="3ffce-384">문자열이 아닌 매개 변수의 경우 데이터 형식은 매개 변수 이름 다음에 괄호로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-384">For a non-string parameter, the data type is specified in parenthesis, following the parameter name.</span></span>  
  
     <span data-ttu-id="3ffce-385">**/Parameter** 옵션은 옵션과 함께 사용할 수 있습니다 `/ISServer` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-385">The **/Parameter** option can be used only with the `/ISServer` option.</span></span>  
  
     <span data-ttu-id="3ffce-386">$Package, $Project 및 $ServerOption 접두사는 각각 패키지 매개 변수, 프로젝트 매개 변수 및 서버 옵션 매개 변수를 나타내기 위해 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-386">You use the $Package, $Project, and $ServerOption prefixes to indicate a package parameter, project parameter, and a server option parameter, respectively.</span></span> <span data-ttu-id="3ffce-387">기본 매개 변수 유형은 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-387">The default parameter type is package.</span></span>  
  
     <span data-ttu-id="3ffce-388">다음은 패키지를 실행하고 프로젝트 매개 변수(myparam)에 대해 myvalue를 제공하고 패키지 매개 변수(anotherparam)에 대해 정수 값 12를 제공하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-388">The following is an example of executing a package and providing myvalue for the project parameter (myparam) and the integer value 12 for the package parameter (anotherparam).</span></span>  
  
     `Dtexec /isserver "SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "." /parameter $Project::myparam;myvalue /parameter anotherparam(int32);12`  
  
     <span data-ttu-id="3ffce-389">매개 변수를 사용하여 연결 관리자 속성을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-389">You can also set connection manager properties by using parameters.</span></span> <span data-ttu-id="3ffce-390">CM 접두사를 사용하여 연결 관리자 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-390">You use the CM prefix to denote a connection manager parameter.</span></span>  
  
     <span data-ttu-id="3ffce-391">다음 예에서 SourceServer 연결 관리자의 InitialCatalog 속성은 `ssisdb`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-391">In the following example, InitialCatalog property of the SourceServer connection manager is set to `ssisdb`.</span></span>  
  
    ```  
    /parameter CM.SourceServer.InitialCatalog;ssisdb  
    ```  
  
     <span data-ttu-id="3ffce-392">다음 예에서는 SourceServer 연결 관리자의 ServerName 속성을 마침표(.)로 설정하여 로컬 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-392">In the following example, ServerName property of the SourceServer connection manager is set to a period (.) to indicate the local server.</span></span>  
  
    ```  
    /parameter CM.SourceServer.ServerName;.  
    ```  
  
-   <span data-ttu-id="3ffce-393">**/Proj[ect]** _ProjectFile_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-393">**/Proj[ect]** _ProjectFile_:</span></span>  
                  <span data-ttu-id="3ffce-394">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-394">Optional.</span></span> <span data-ttu-id="3ffce-395">실행되는 패키지를 검색할 프로젝트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-395">Specifies the project from which to retrieve the package that is executed.</span></span> <span data-ttu-id="3ffce-396">*ProjectFile* 인수는 .ispac 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-396">The *ProjectFile* argument specifies the .ispac file name.</span></span> <span data-ttu-id="3ffce-397">이 매개 변수는 주로 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 패키지를 실행할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-397">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="3ffce-398">**/Rem** _comment_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-398">**/Rem** _comment_:</span></span>  
                  <span data-ttu-id="3ffce-399">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-399">Optional.</span></span> <span data-ttu-id="3ffce-400">명령 프롬프트 또는 명령 파일에 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-400">Includes comments on the command prompt or in command files.</span></span> <span data-ttu-id="3ffce-401">이 인수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-401">The argument is optional.</span></span> <span data-ttu-id="3ffce-402">*comment* 값은 따옴표로 묶여 있거나 공백이 없는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-402">The value of *comment* is a string that must be enclosed in quotation marks, or contain no white space.</span></span> <span data-ttu-id="3ffce-403">인수를 지정하지 않으면 빈 줄이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-403">If no argument is specified, a blank line is inserted.</span></span> <span data-ttu-id="3ffce-404">*comment* 값은 명령을 읽어 들이는 단계를 수행하는 동안 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-404">*comment* values are discarded during the command sourcing phase.</span></span>  
  
-   <span data-ttu-id="3ffce-405">**/Ss [orting]** _level_ [*; event_guid_or_name*[*; event_guid_or_name*[...]]: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-405">**/Rep[orting]** _level_ [*;event_guid_or_name*[*;event_guid_or_name*[...]]: Optional.</span></span> <span data-ttu-id="3ffce-406">보고할 메시지의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-406">Specifies what types of messages to report.</span></span> <span data-ttu-id="3ffce-407">*level* 에 대해 사용할 수 있는 보고 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-407">The available reporting options for *level* are as follows:</span></span>  
  
     <span data-ttu-id="3ffce-408">**N** - 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-408">**N** No reporting.</span></span>  
  
     <span data-ttu-id="3ffce-409">`E`오류가 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-409">`E` Errors are reported.</span></span>  
  
     <span data-ttu-id="3ffce-410">**W** - 경고를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-410">**W** Warnings are reported.</span></span>  
  
     <span data-ttu-id="3ffce-411">`I`정보 메시지가 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-411">`I` Informational messages are reported.</span></span>  
  
     <span data-ttu-id="3ffce-412">**C** - 사용자 지정 이벤트를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-412">**C** Custom events are reported.</span></span>  
  
     <span data-ttu-id="3ffce-413">**D** - 데이터 흐름 태스크 이벤트를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-413">**D** Data Flow task events are reported.</span></span>  
  
     <span data-ttu-id="3ffce-414">**P** - 진행률을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-414">**P** Progress is reported.</span></span>  
  
     <span data-ttu-id="3ffce-415">**V** - 자세한 사항을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-415">**V** Verbose reporting.</span></span>  
  
     <span data-ttu-id="3ffce-416">V 및 N 인수는 다른 인수와 함께 사용할 수 없으므로 단독으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-416">The arguments of V and N are mutually exclusive to all other arguments; they must be specified alone.</span></span> <span data-ttu-id="3ffce-417">**/Cers** 옵션을 지정 하지 않으면 기본 수준은 `E` (오류), **W** (경고) 및 **P** (진행 상황)입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-417">If the **/Reporting** option is not specified then the default level is `E` (errors), **W** (warnings), and **P** (progress).</span></span>  
  
     <span data-ttu-id="3ffce-418">모든 이벤트 앞에는 "YY/MM/DD HH:MM:SS" 형식의 타임스탬프가 있으며 GUID 또는 이름이 옵니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="3ffce-418">All events are preceded with a timestamp in the format "YY/MM/DD HH:MM:SS", and a GUID or friendly name if available.</span></span>  
  
     <span data-ttu-id="3ffce-419">선택적 매개 변수 *event_guid_or_name* 은 로그 공급자에 대한 예외 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-419">The optional parameter *event_guid_or_name* is a list of exceptions to the log providers.</span></span> <span data-ttu-id="3ffce-420">예외는 정상적인 상황에서는 기록되어야 하지만 기록되지 않는 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-420">The exception specifies the events that are not logged that otherwise might have been logged.</span></span>  
  
     <span data-ttu-id="3ffce-421">기본적으로 기록되지 않는 경우에는 이벤트를 제외시킬 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-421">You do not have to exclude an event if the event is not ordinarily logged by default</span></span>  
  
-   <span data-ttu-id="3ffce-422">**/Res [t)]** {*deny | Force | ifpossible*}: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-422">**/Res[tart]** {*deny | force | ifPossible*}: Optional.</span></span> <span data-ttu-id="3ffce-423">패키지에서 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 속성의 새 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-423">Specifies a new value for the <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property on the package.</span></span> <span data-ttu-id="3ffce-424">매개 변수의 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-424">The meaning of the parameters are as follows:</span></span>  
  
     <span data-ttu-id="3ffce-425">*Deny*<xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 속성을 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-425">*Deny* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>.</span></span>  
  
     <span data-ttu-id="3ffce-426">*Force*<xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 속성을 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-426">*Force* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>.</span></span>  
  
     <span data-ttu-id="3ffce-427">*ifPossible*<xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 속성을 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-427">*ifPossible* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>.</span></span>  
  
     <span data-ttu-id="3ffce-428">값을 지정하지 않으면 기본값인 **force** 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-428">The default value of **force** is used if no value is specified.</span></span>  
  
-   <span data-ttu-id="3ffce-429">**/Set** [$Sensitive::]*propertyPath; 값*: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-429">**/Set** [$Sensitive::]*propertyPath;value*: Optional.</span></span> <span data-ttu-id="3ffce-430">패키지에서 매개 변수, 변수, 속성, 컨테이너, 로그 공급자, Foreach 열거자 또는 연결의 구성을 재지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-430">Overrides the configuration of a parameter, variable, property, container, log provider, Foreach enumerator, or connection within a package.</span></span> <span data-ttu-id="3ffce-431">이 옵션을 사용하면 **/Set** 는 *propertyPath* 인수를 지정된 값으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-431">When this option is used, **/Set** changes the *propertyPath* argument to the value specified.</span></span> <span data-ttu-id="3ffce-432">여러 **/Set** 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-432">Multiple **/Set** options can be specified.</span></span>  
  
     <span data-ttu-id="3ffce-433">**/Set** 옵션을 **/f [사용자 이름]** 옵션과 함께 사용 하는 것 외에도 **/set** 옵션을 `/ISServer` 옵션 또는 옵션과 함께 사용할 수 있습니다 `/Project` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-433">In addition to using the **/Set** option with the **/F[ile]** option, you can also use the **/Set** option with the `/ISServer` option or the `/Project` option.</span></span> <span data-ttu-id="3ffce-434">**/Set** 를와 함께 사용 하 `/Project` 는 경우 **/set** 는 매개 변수 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-434">When you use **/Set** with `/Project`, **/Set** sets parameter values.</span></span> <span data-ttu-id="3ffce-435">**/Set** 를와 함께 사용 하 `/ISServer` 는 경우 **/set** 는 속성 재정의를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-435">When you use **/Set** with `/ISServer`, **/Set** sets property overrides.</span></span> <span data-ttu-id="3ffce-436">또한 **/set** 를와 함께 사용 하는 경우 `/ISServer` 선택적 $Sensitive 접두사를 사용 하 여 서버에서 속성을 중요 한 것으로 처리 하도록 지정할 수 있습니다 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3ffce-436">In addition, when you use **/Set** with `/ISServer`, you can use the optional $Sensitive prefix to indicate that the property should be treated as sensitive on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="3ffce-437">패키지 구성 마법사를 실행하여 *propertyPath* 의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-437">You can determine the value of *propertyPath* by running the Package Configuration Wizard.</span></span> <span data-ttu-id="3ffce-438">선택한 항목의 경로는 마지막 **마법사 완료** 페이지에 표시되며 복사하여 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-438">The paths for items that you select are displayed on the final **Completing the Wizard** page, and can be copied and pasted.</span></span> <span data-ttu-id="3ffce-439">이러한 용도로만 마법사를 사용하는 경우에는 경로를 복사한 다음 마법사를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-439">If you have used the wizard only for this purpose, you can cancel the wizard after you copy the paths.</span></span>  
  
     <span data-ttu-id="3ffce-440">다음은 파일 시스템에 저장된 패키지를 실행하고 변수에 새 값을 제공하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-440">The following is an example of executing a package that is saved in the file system and providing a new value for a variable:</span></span>  
  
     `dtexec /f mypackage.dtsx /set \package.variables[myvariable].Value;myvalue`  
  
     <span data-ttu-id="3ffce-441">다음은 .ispac 프로젝트 파일에서 패키지를 실행하고 패키지 및 프로젝트 매개 변수를 설정하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-441">The following example of running a package from the .ispac project file and setting package and project parameters.</span></span>  
  
     `/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1`  
  
     <span data-ttu-id="3ffce-442">**/Set** 옵션을 사용하면 패키지 구성이 로드되는 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-442">You can use the **/Set** option to change the location from which package configurations are loaded.</span></span> <span data-ttu-id="3ffce-443">그러나 디자인 타임에 구성으로 지정한 값은 **/Set** 옵션을 사용하여 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-443">However, you cannot use the **/Set** option to override a value that was specified by a configuration at design time.</span></span> <span data-ttu-id="3ffce-444">패키지 구성이 적용 되는 방법을 이해 하려면 [SQL Server 2014의 Integration Services 기능에 대](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)한 [패키지 구성](../package-configurations.md) 및 동작 변경을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-444">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="3ffce-445">`/Ser[ver]`*서버*:</span><span class="sxs-lookup"><span data-stu-id="3ffce-445">`/Ser[ver]` *server*:</span></span>  
                  <span data-ttu-id="3ffce-446">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-446">Optional.</span></span> <span data-ttu-id="3ffce-447">`/SQL` 또는 `/DTS` 옵션을 지정한 경우 이 옵션은 패키지를 검색할 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-447">When the `/SQL` or `/DTS` option is specified, this option specifies the name of the server from which to retrieve the package.</span></span> <span data-ttu-id="3ffce-448">`/Server` 옵션을 생략하고 `/SQL` 또는 `/DTS` 옵션을 지정하면 로컬 서버에 대해 패키지가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-448">If you omit the `/Server` option and the `/SQL` or `/DTS` option is specified, package execution is tried against the local server.</span></span> <span data-ttu-id="3ffce-449">*server_instance* 값은 따옴표로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-449">The *server_instance* value may be quoted.</span></span>  
  
     <span data-ttu-id="3ffce-450">`/Ser[ver]` 옵션이 지정된 경우 `/ISServer` 옵션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-450">The `/Ser[ver]` option is required when the `/ISServer` option is specified.</span></span>  
  
-   <span data-ttu-id="3ffce-451">**/SQ[L]** _package_path_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-451">**/SQ[L]** _package_path_:</span></span>  
                  <span data-ttu-id="3ffce-452">`msdb` 데이터베이스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 패키지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-452">Loads a package that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in `msdb` database.</span></span> <span data-ttu-id="3ffce-453">`msdb` 데이터베이스에 저장된 패키지는 패키지 배포 모델을 사용하여 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-453">Packages that are stored in the `msdb` database, are deployed using the package deployment model.</span></span> <span data-ttu-id="3ffce-454">프로젝트 배포 모델을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 패키지를 실행하려면 `/ISServer` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-454">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="3ffce-455">패키지 및 프로젝트 배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ffce-455">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="3ffce-456">*package_path* 인수는 검색할 패키지의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-456">The *package_path* argument specifies the name of the package to retrieve.</span></span> <span data-ttu-id="3ffce-457">경로에 폴더가 포함된 경우 백슬래시("\\")로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-457">If folders are included in the path, they are terminated with backslashes ("\\").</span></span> <span data-ttu-id="3ffce-458">*package_path* 값은 따옴표로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-458">The *package_path* value can be quoted.</span></span> <span data-ttu-id="3ffce-459">*package_path* 인수에 지정된 경로나 파일 이름에 공백이 있는 경우 *package_path* 인수를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-459">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="3ffce-460">옵션은 **/user**, **/password**및 옵션과 함께 사용할 수 있습니다 `/Server` `/SQL` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-460">You can use the **/User**, **/Password**, and `/Server` options together with the `/SQL` option.</span></span>  
  
     <span data-ttu-id="3ffce-461">**/User** 옵션을 생략하면 패키지에 액세스하는 데 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-461">If you omit the **/User** option, Windows Authentication is used to access the package.</span></span> <span data-ttu-id="3ffce-462">**/User** 옵션을 사용하면 지정된 **/User** 로그인 이름이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-462">If you use the **/User** option, the **/User** login name specified is associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="3ffce-463">**/Password** 옵션은 **/User** 옵션과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-463">The **/Password** option is used only together with the **/User** option.</span></span> <span data-ttu-id="3ffce-464">**/Password** 옵션을 사용할 경우 패키지는 제공된 사용자 이름 및 암호 정보로 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-464">If you use the **/Password** option, the package is accessed with the user name and password information provided.</span></span> <span data-ttu-id="3ffce-465">**/Password** 옵션을 생략하면 빈 암호가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-465">If you omit the **/Password** option, a blank password is used.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
     <span data-ttu-id="3ffce-466">`/Server` 옵션을 생략하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 로컬 인스턴스로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-466">If the `/Server` option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="3ffce-467">`/SQL` 옵션은 `/DTS` 또는 `/File` 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-467">The `/SQL` option cannot be used together with the `/DTS` or `/File` option.</span></span> <span data-ttu-id="3ffce-468">여러 개의 옵션을 지정하는 경우 `dtexec`는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-468">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="3ffce-469">**/Su [m]**: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-469">**/Su[m]**: Optional.</span></span> <span data-ttu-id="3ffce-470">다음 구성 요소에서 받을 행 수를 포함하는 증분 카운터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-470">Shows an incremental counter that contains the number of rows that will be received by the next component.</span></span>  
  
-   <span data-ttu-id="3ffce-471">**/U [ser]** _user_name_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-471">**/U[ser]** _user_name_:</span></span>  
                  <span data-ttu-id="3ffce-472">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-472">Optional.</span></span> <span data-ttu-id="3ffce-473">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증으로 보호되는 패키지를 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-473">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="3ffce-474">이 옵션은 `/SQL` 옵션을 지정한 경우에만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-474">This option is used only when the `/SQL` option is specified.</span></span> <span data-ttu-id="3ffce-475">*user_name* 값은 따옴표로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-475">The *user_name* value can be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="3ffce-476">**/Va [lidate]**:</span><span class="sxs-lookup"><span data-stu-id="3ffce-476">**/Va[lidate]**:</span></span>  
                  <span data-ttu-id="3ffce-477">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-477">Optional.</span></span> <span data-ttu-id="3ffce-478">유효성 검사 단계 후에 실제로 패키지를 실행하지 않고 패키지 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-478">Stops the execution of the package after the validatation phase, without actually running the package.</span></span> <span data-ttu-id="3ffce-479">유효성 검사 중에 **/WarnAsError** 옵션을 사용 하면에서 `dtexec` 경고를 오류로 간주 하므로 유효성 검사 중 경고가 발생 하면 패키지가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-479">During validation, use of the **/WarnAsError** option causes `dtexec` to treat a warning as an error; therefore the package fails if a warning occurs during validation.</span></span>  
  
-   <span data-ttu-id="3ffce-480">**/Verifyb [uild]** _major_[*; minor*[*; build*]]: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-480">**/VerifyB[uild]** _major_[*;minor*[*;build*]]: Optional.</span></span> <span data-ttu-id="3ffce-481">확인 단계 동안 *major*, *minor*및 *build* 인수에 지정된 빌드 번호에 대해 패키지의 빌드 번호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-481">Verifies the build number of a package against the build numbers that were specified during the verification phase in the *major*, *minor*, and *build* arguments.</span></span> <span data-ttu-id="3ffce-482">일치하지 않을 경우 패키지가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-482">If a mismatch occurs, the package will not execute.</span></span>  
  
     <span data-ttu-id="3ffce-483">값은 정수(Long)입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-483">The values are long integers.</span></span> <span data-ttu-id="3ffce-484">인수의 형식으로 3가지 중 하나를 사용할 수 있으며 *major* 값은 항상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-484">The argument can have one of three forms, with a value for *major* always required:</span></span>  
  
    -   <span data-ttu-id="3ffce-485">*major*</span><span class="sxs-lookup"><span data-stu-id="3ffce-485">*major*</span></span>  
  
    -   <span data-ttu-id="3ffce-486">*major*;*minor*</span><span class="sxs-lookup"><span data-stu-id="3ffce-486">*major*;*minor*</span></span>  
  
    -   <span data-ttu-id="3ffce-487">*major*; *minor*; *build*</span><span class="sxs-lookup"><span data-stu-id="3ffce-487">*major*; *minor*; *build*</span></span>  
  
-   <span data-ttu-id="3ffce-488">**/VerifyP[ackageID]** _packageID_:</span><span class="sxs-lookup"><span data-stu-id="3ffce-488">**/VerifyP[ackageID]** _packageID_:</span></span>  
                  <span data-ttu-id="3ffce-489">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-489">Optional.</span></span> <span data-ttu-id="3ffce-490">실행할 패키지의 GUID를 *package_id* 인수에 지정된 값과 비교하여 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-490">Verifies the GUID of the package to be executed by comparing it to the value specified in the *package_id* argument.</span></span>  
  
-   <span data-ttu-id="3ffce-491">**/VerifyS[igned]**:</span><span class="sxs-lookup"><span data-stu-id="3ffce-491">**/VerifyS[igned]**:</span></span>  
                  <span data-ttu-id="3ffce-492">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-492">Optional.</span></span> <span data-ttu-id="3ffce-493">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 가 패키지의 디지털 서명을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-493">Causes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of the package.</span></span> <span data-ttu-id="3ffce-494">패키지가 서명되지 않았거나 서명이 잘못된 경우 패키지가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-494">If the package is not signed or the signature is not valid, the package fails.</span></span> <span data-ttu-id="3ffce-495">자세한 내용은 [디지털 서명을 사용하여 패키지 원본 확인](../security/identify-the-source-of-packages-with-digital-signatures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ffce-495">For more information, see [Identify the Source of Packages with Digital Signatures](../security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3ffce-496">패키지의 서명을 확인하도록 구성된 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 는 디지털 서명이 있는지, 유효한지, 그리고 신뢰할 수 있는 원본에서 제공된 것인지만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-496">When configured to check the signature of the package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] only checks whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="3ffce-497">는 패키지가 변경되었는지 여부는 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-497">does not check whether the package has been changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ffce-498">선택적 **BlockedSignatureStates** 레지스트리 값은 또는 명령줄에서 설정 된 디지털 서명 옵션 보다 더 제한적인 설정을 지정할 수 있습니다 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] `dtexec` .</span><span class="sxs-lookup"><span data-stu-id="3ffce-498">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] or at the `dtexec` command line.</span></span> <span data-ttu-id="3ffce-499">이 경우 더 제한적인 설정이 다른 설정보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-499">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
-   <span data-ttu-id="3ffce-500">**/Verifyv [ersionID]** _인수: 선택 사항입니다._</span><span class="sxs-lookup"><span data-stu-id="3ffce-500">**/VerifyV[ersionID]** _versionID_: Optional.</span></span> <span data-ttu-id="3ffce-501">패키지 유효성 검사 단계 동안 실행할 패키지의 버전 GUID를 *version_id* 인수에 지정된 값과 비교하여 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-501">Verifies the version GUID of a package to be executed by comparing it to the value specified in the *version_id* argument during package Validation Phase.</span></span>  
  
-   <span data-ttu-id="3ffce-502">**/VLog** _[Filespec]_: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-502">**/VLog** _[Filespec]_: Optional.</span></span> <span data-ttu-id="3ffce-503">패키지를 디자인할 때 사용하도록 설정한 로그 공급자에 모든 Integration Services 패키지 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-503">Writes all Integration Services package events to the log providers that were enabled when the package was designed.</span></span> <span data-ttu-id="3ffce-504">Integration Services가 텍스트 파일용 로그 공급자를 사용하고 지정된 텍스트 파일에 로그 이벤트를 기록하도록 만들려면 경로 및 파일 이름을 *Filespec* 매개 변수로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-504">To have Integration Services enable a log provider for text files and write log events to a specified text file, include a path and file name as the *Filespec* parameter.</span></span>  
  
     <span data-ttu-id="3ffce-505">*Filespec* 매개 변수를 포함하지 않으면 Integration Services가 텍스트 파일용 로그 공급자를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-505">If you do not include the *Filespec* parameter, Integration Services will not enable a log provider for text files.</span></span> <span data-ttu-id="3ffce-506">Integration Services는 패키지를 디자인할 때 사용하도록 설정한 로그 공급자에만 로그 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-506">Integration Services will only write log events to the log providers that were enabled when the package was designed.</span></span>  
  
-   <span data-ttu-id="3ffce-507">**/W [arnAsError]**:</span><span class="sxs-lookup"><span data-stu-id="3ffce-507">**/W[arnAsError]**:</span></span>  
                  <span data-ttu-id="3ffce-508">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-508">Optional.</span></span> <span data-ttu-id="3ffce-509">패키지에서 경고를 오류로 간주하도록 하므로 유효성 검사 동안 경고가 발생하면 패키지가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-509">Causes the package to consider a warning as an error; therefore, the package will fail if a warning occurs during validation.</span></span> <span data-ttu-id="3ffce-510">유효성 검사 동안 경고가 발생하지 않았고 **/Validate** 옵션을 지정하지 않은 경우 패키지가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-510">If no warnings occur during validation and the **/Validate** option is not specified, the package is executed.</span></span>  
  
-   <span data-ttu-id="3ffce-511">**/X86**: 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-511">**/X86**: Optional.</span></span> <span data-ttu-id="3ffce-512">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 64비트 컴퓨터에서 32비트 모드로 패키지를 실행하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-512">Causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run the package in 32-bit mode on a 64-bit computer.</span></span> <span data-ttu-id="3ffce-513">이 옵션은 다음 조건이 충족되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-513">This option is set by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent when the following conditions are true:</span></span>  
  
    -   <span data-ttu-id="3ffce-514">작업 단계 유형이 **SQL Server Integration Services 패키지**입니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-514">The job step type is **SQL Server Integration Services package**.</span></span>  
  
    -   <span data-ttu-id="3ffce-515">**새 작업 단계** 대화 상자의 **실행 옵션** 탭에서 **32비트 런타임 사용** 옵션이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-515">The **Use 32 bit runtime** option on the **Execution options** tab of the **New Job Step** dialog box is selected.</span></span>  
  
     <span data-ttu-id="3ffce-516">또한 저장 프로시저나 SMO(SQL Server 관리 개체)를 사용하여 프로그래밍 방식으로 작업을 만들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에 대해 이 옵션을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-516">You can also set this option for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step by using stored procedures or SQL Server Management Objects (SMO) to programmatically create the job.</span></span>  
  
     <span data-ttu-id="3ffce-517">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-517">This option is only used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3ffce-518">명령 프롬프트에서 `dtexec` 유틸리티를 실행하는 경우에는 이 옵션이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-518">This option is ignored if you run the `dtexec` utility at the command prompt.</span></span>  
  
##  <a name="remarks"></a><a name="remark"></a> <span data-ttu-id="3ffce-519">주의</span><span class="sxs-lookup"><span data-stu-id="3ffce-519">Remarks</span></span>  
 <span data-ttu-id="3ffce-520">명령 옵션을 지정하는 순서에 따라 패키지 실행 방법이 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-520">The order in which you specify command options can influence the way in which the package executes:</span></span>  
  
-   <span data-ttu-id="3ffce-521">명령줄에 나타나는 순서대로 옵션이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-521">Options are processed in the order they are encountered on the command line.</span></span> <span data-ttu-id="3ffce-522">명령줄에 명령 파일이 있으면 명령 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-522">Command files are read in as they are encountered on the command line.</span></span> <span data-ttu-id="3ffce-523">명령 파일의 명령도 나타나는 순서대로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-523">The commands in the command file are also processed in the order they are encountered.</span></span>  
  
-   <span data-ttu-id="3ffce-524">같은 명령줄 문에 같은 옵션, 매개 변수 또는 변수가 두 번 이상 나타나는 경우 마지막 옵션이 우선 순위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-524">If the same option, parameter, or variable appears in the same command line statement more than one time, the last instance of the option takes precedence.</span></span>  
  
-   <span data-ttu-id="3ffce-525">**/Set** 및 **/ConfigFile** 옵션은 나타나는 순서대로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-525">**/Set** and **/ConfigFile** options are processed in the order they are encountered.</span></span>  
  
##  <a name="examples"></a><a name="example"></a> <span data-ttu-id="3ffce-526">예</span><span class="sxs-lookup"><span data-stu-id="3ffce-526">Examples</span></span>  
 <span data-ttu-id="3ffce-527">다음 예에서는 명령 프롬프트 유틸리티를 사용 하 여 패키지를 구성 하 고 실행 하는 방법을 보여 줍니다 `dtexec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3ffce-527">The following examples demonstrate how to use the `dtexec` command prompt utility to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="3ffce-528">**실행 중인 패키지**</span><span class="sxs-lookup"><span data-stu-id="3ffce-528">**Running Packages**</span></span>  
  
 <span data-ttu-id="3ffce-529">Windows 인증을 사용하여 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 에 저장된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 패키지를 실행하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-529">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer  
```  
  
 <span data-ttu-id="3ffce-530">SSIS 패키지 저장소의 파일 시스템 폴더에 저장된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 실행하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-530">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to the File System folder in the SSIS Package Store, use the following code:</span></span>  
  
```  
dtexec /dts "\File System\MyPackage"  
```  
  
 <span data-ttu-id="3ffce-531">Windows 인증을 사용하며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 저장된 패키지를 실행하지 않고 유효성을 검사하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-531">To validate a package that uses Windows Authentication and is saved in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without executing the package, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer /va  
```  
  
 <span data-ttu-id="3ffce-532">파일 시스템에 저장된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 실행하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-532">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx"   
```  
  
 <span data-ttu-id="3ffce-533">파일 시스템에 저장된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 실행하고 로깅 옵션을 지정하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-533">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, and specify logging options, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /l "DTS.LogProviderTextFile;c:\log.txt"  
```  
  
 <span data-ttu-id="3ffce-534">Windows 인증을 사용하며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 로컬 인스턴스에 저장된 패키지를 실행하려면 실행하기 전에 버전을 확인하고 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-534">To execute a package that uses Windows Authentication and is saved to the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and verify the version before it is executed, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /verifyv {c200e360-38c5-11c5-11ce-ae62-08002b2b79ef}  
```  
  
 <span data-ttu-id="3ffce-535">파일 시스템에 저장되고 외부적으로 구성된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 실행하려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-535">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system and configured externally, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /conf "c:\pkgOneConfig.cfg"  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3ffce-536">경로나 파일 이름에 공백이 있는 경우 /SQL, /DTS 또는 /FILE 옵션의 *package_path* 또는 *filespec* 인수를 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-536">The *package_path* or *filespec* arguments of the /SQL, /DTS, or /FILE options must be enclosed in quotation marks if the path or file name contains a space.</span></span> <span data-ttu-id="3ffce-537">인수를 따옴표로 묶지 않으면 인수에 공백을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-537">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="3ffce-538">**로깅 옵션**</span><span class="sxs-lookup"><span data-stu-id="3ffce-538">**Logging Option**</span></span>  
  
 <span data-ttu-id="3ffce-539">A, B, C라는 3개의 로그 항목 유형이 있는 경우 매개 변수가 없는 다음 **ConsoleLog** 옵션은 모든 필드와 함께 3개의 로그 유형을 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-539">If there are three log entry types of A, B, and C, the following **ConsoleLog** option without a parameter displays all three log types with all fields:</span></span>  
  
```  
/CONSOLELOG  
```  
  
 <span data-ttu-id="3ffce-540">다음 옵션은 모든 로그 유형을 표시하지만 이름 및 메시지 열만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-540">The following option displays all log types, but with the Name and Message columns only:</span></span>  
  
```  
/CONSOLELOG NM  
```  
  
 <span data-ttu-id="3ffce-541">다음 옵션은 모든 열을 표시하지만 로그 항목 유형 A에 대해서만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-541">The following option displays all columns, but only for log entry type A:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="3ffce-542">다음 옵션은 이름 및 메시지 열과 함께 로그 항목 유형 A만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-542">The following option displays only log entry type A, with Name and Message columns:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA  
```  
  
 <span data-ttu-id="3ffce-543">다음 옵션은 로그 항목 유형 A와 B에 대한 로그 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-543">The following option displays log entries for log entry types A and B:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA;LogEntryTypeB  
```  
  
 <span data-ttu-id="3ffce-544">여러 **ConsoleLog** 옵션을 사용하여 같은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-544">You can achieve the same results by using multiple **ConsoleLog** options:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA /CONSOLELOG I;LogEntryTypeB  
```  
  
 <span data-ttu-id="3ffce-545">**ConsoleLog** 옵션을 매개 변수 없이 사용하면 모든 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-545">If the **ConsoleLog** option is used without parameters, all fields are displayed.</span></span> <span data-ttu-id="3ffce-546">*list_options* 매개 변수를 포함하면 다음은 모든 필드와 함께 로그 항목 유형 A만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-546">The inclusion of a *list_options* parameter causes the following to displays only log entry type A, with all fields:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA /CONSOLELOG  
```  
  
 <span data-ttu-id="3ffce-547">다음 옵션은 로그 항목 유형 A를 제외한 모든 로그 항목(로그 항목 유형 B 및 C)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-547">The following displays all log entries except log entry type A: that is, it displays log entry types B and C:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA  
```  
  
 <span data-ttu-id="3ffce-548">다음 예에서는 여러 **ConsoleLog** 옵션을 사용하고 하나를 제외하여 같은 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-548">The following example achieves the same results by using multiple **ConsoleLog** options and a single exclusion:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG E;LogEntryTypeA  
/CONSOLELOG E;LogEntryTypeA;LogEntryTypeA  
```  
  
 <span data-ttu-id="3ffce-549">로그 파일 종류가 포함 목록과 제외 목록 모두에 있는 경우 제외되므로 다음 예에서는 로그 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-549">The following example displays no log messages, because when a log file type is found in both the included and excluded lists, it will be excluded.</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="3ffce-550">**SET 옵션**</span><span class="sxs-lookup"><span data-stu-id="3ffce-550">**SET Option**</span></span>  
  
 <span data-ttu-id="3ffce-551">다음 예제에서는 명령줄에서 패키지를 시작하는 경우 모든 패키지의 속성 또는 변수 값을 변경할 수 있는 **/SET** 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-551">The following example shows how to use the **/SET** option, which lets you change the value of any package property or variable when you start the package from the command line.</span></span>  
  
```  
/SET \package\DataFlowTask.Variables[User::MyVariable].Value;newValue  
```  
  
 <span data-ttu-id="3ffce-552">**프로젝트 옵션**</span><span class="sxs-lookup"><span data-stu-id="3ffce-552">**Project Option**</span></span>  
  
 <span data-ttu-id="3ffce-553">다음 예에서는 `/Project`와 `/Package` 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-553">The following example shows how to use the `/Project` and the `/Package` option.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx  
```  
  
 <span data-ttu-id="3ffce-554">다음 예에서는 `/Project` 및 `/Package` 옵션을 사용하고 패키지 및 프로젝트 매개 변수를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-554">The following example shows how to use the `/Project` and `/Package` options, and set package and project parameters.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1  
  
```  
  
 <span data-ttu-id="3ffce-555">**ISServer 옵션**</span><span class="sxs-lookup"><span data-stu-id="3ffce-555">**ISServer Option**</span></span>  
  
 <span data-ttu-id="3ffce-556">다음 예에서는 `/ISServer` 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-556">The following example shows how to use the `/ISServer` option.</span></span>  
  
```  
dtexec /isserver "\SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "."  
```  
  
 <span data-ttu-id="3ffce-557">다음 예에서는 `/ISServer` 옵션을 사용하여 프로젝트 및 연결 관리자 매개 변수를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ffce-557">The following example shows how to use the `/ISServer` option and set project and connection manager parameters.</span></span>  
  
```  
/Server localhost /ISServer "\SSISDB\MyFolder\Integration Services Project1\Package.dtsx" /Par "$Project::ProjectParameter(Int32)";1 /Par "CM.SourceServer.InitialCatalog";SourceDB  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="3ffce-558">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3ffce-558">Related Tasks</span></span>  
 [<span data-ttu-id="3ffce-559">SQL Server Data Tools에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="3ffce-559">Run a Package in SQL Server Data Tools</span></span>](../run-a-package-in-sql-server-data-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="3ffce-560">관련 내용</span><span class="sxs-lookup"><span data-stu-id="3ffce-560">Related Content</span></span>  
 <span data-ttu-id="3ffce-561">[www.mattmasson.com](www.mattmasson.com) 의 [종료 코드, DTEXEC 및 SSIS 카탈로그](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/)블로그 항목</span><span class="sxs-lookup"><span data-stu-id="3ffce-561">Blog entry, [Exit Codes, DTEXEC, and SSIS Catalog](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/), on www.mattmasson.com.</span></span>  
  
  
