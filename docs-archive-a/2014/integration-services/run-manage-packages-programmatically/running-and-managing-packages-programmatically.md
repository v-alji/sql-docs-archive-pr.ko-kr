---
title: 프로그래밍 방식으로 패키지 실행 및 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b07b0b98674fa17891dbbcb01ec42934c2a72e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730839"
---
# <a name="running-and-managing-packages-programmatically"></a><span data-ttu-id="132fe-102">프로그래밍 방식으로 패키지 실행 및 관리</span><span class="sxs-lookup"><span data-stu-id="132fe-102">Running and Managing Packages Programmatically</span></span>
  <span data-ttu-id="132fe-103">개발 환경 외부에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 관리 및 실행해야 하는 경우 패키지를 프로그래밍 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-103">If you need manage and run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="132fe-104">이 경우 다음 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-104">In this approach, you have a range of options:</span></span>  
  
-   <span data-ttu-id="132fe-105">기존 패키지를 로드하고 수정하지 않은 채로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-105">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="132fe-106">기존 패키지를 로드하고 다시 구성(예: 다른 데이터 원본에 대해)한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-106">Load an existing package, reconfigure it (for example, for a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="132fe-107">새 패키지를 만들고 구성 요소를 개체별 및 속성별로 구성한 다음 새 패키지를 저장 후 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-107">Create a new package, add and configure components object by object and property by property, save it, and run it.</span></span>  
  
 <span data-ttu-id="132fe-108">단 몇 줄의 코드를 작성하여 클라이언트 애플리케이션에서 기존 패키지를 로드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-108">You can load and run an existing package from a client application by writing only a few lines of code.</span></span>  
  
 <span data-ttu-id="132fe-109">이 섹션에서는 기존 패키지를 프로그래밍 방식으로 실행하는 방법과 다른 애플리케이션에서 데이터 흐름의 출력에 액세스하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-109">This section describes and demonstrates how to run an existing package programmatically and how to access the output of the data flow from other applications.</span></span> <span data-ttu-id="132fe-110">고급 프로그래밍 옵션인 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]프로그래밍 방식으로 패키지 작성[ 항목의 설명에 따라 ](../building-packages-programmatically/building-packages-programmatically.md) 패키지를 프로그래밍 방식으로 한 줄씩 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-110">As an advanced programming option, you can programmatically create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package line by line as described in the topic, [Building Packages Programmatically](../building-packages-programmatically/building-packages-programmatically.md).</span></span>  
  
 <span data-ttu-id="132fe-111">이 섹션에서는 저장된 패키지, 실행 중인 패키지 및 패키지 역할을 관리하기 위해 프로그래밍 방식으로 수행할 수 있는 기타 관리 태스크도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-111">This section also discusses other administrative tasks that you can perform programmatically to manage stored packages, running packages, and package roles.</span></span>  
  
## <a name="running-packages-on-the-integration-services-server"></a><span data-ttu-id="132fe-112">Integration Services 서버의 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="132fe-112">Running Packages on the Integration Services Server</span></span>  
 <span data-ttu-id="132fe-113">패키지를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포한 경우 <xref:Microsoft.SqlServer.Management.IntegrationServices> 네임스페이스를 사용하여 프로그래밍 방식으로 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-113">When you deploy packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can run the packages programmatically by using the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace.</span></span> <span data-ttu-id="132fe-114">Microsoft.SqlServer.Management.IntegrationServices 어셈블리는 .NET Framework 3.5로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-114">The Microsoft.SqlServer.Management.IntegrationServices assembly is compiled with .NET Framework 3.5.</span></span> <span data-ttu-id="132fe-115">.NET Framework 4.0 애플리케이션을 빌드하는 경우 프로젝트 파일에 어셈블리 참조를 직접 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-115">If you are building a .NET Framework 4.0 application, you might need to add the assembly reference directly to your project file.</span></span>  
  
 <span data-ttu-id="132fe-116">또한 네임스페이스를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 배포 및 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-116">You can also use the namespace to deploy and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="132fe-117">네임스페이스 및 코드 조각에 대한 개요는 blogs.msdn.com에서 [SSIS 카탈로그 관리 개체 모델에 대한 이해](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)블로그 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="132fe-117">For an overview of the namespace and code snippets, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="132fe-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="132fe-118">In This Section</span></span>  
 [<span data-ttu-id="132fe-119">로컬 실행과 원격 실행의 차이점 이해</span><span class="sxs-lookup"><span data-stu-id="132fe-119">Understanding the Differences between Local and Remote Execution</span></span>](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 <span data-ttu-id="132fe-120">패키지를 로컬로 실행할 때와 서버에서 실행할 때의 중요한 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-120">Discusses critical differences between executing a package locally or on the server.</span></span>  
  
 [<span data-ttu-id="132fe-121">프로그래밍 방식으로 로컬 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="132fe-121">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 <span data-ttu-id="132fe-122">로컬 컴퓨터의 클라이언트 애플리케이션에서 기존 패키지를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-122">Describes how to execute an existing package from a client application on the local computer.</span></span>  
  
 [<span data-ttu-id="132fe-123">프로그래밍 방식으로 원격 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="132fe-123">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 <span data-ttu-id="132fe-124">클라이언트 애플리케이션에서 기존 패키지를 실행하고 해당 패키지가 서버에서 실행되도록 하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-124">Describes how to execute an existing package from a client application and to ensure that the package runs on the server.</span></span>  
  
 [<span data-ttu-id="132fe-125">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="132fe-125">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 <span data-ttu-id="132fe-126">로컬 컴퓨터에서 패키지를 실행하는 방법과 DataReader 대상 및 DtsClient 네임스페이스를 사용하여 데이터 흐름의 출력을 클라이언트 애플리케이션으로 로드하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-126">Describes how to execute a package on the local computer and how to load the data flow output into a client application by using the DataReader destination and the DtsClient namespace.</span></span>  
  
 [<span data-ttu-id="132fe-127">프로그래밍 방식으로 사용 가능 패키지 열거</span><span class="sxs-lookup"><span data-stu-id="132fe-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 <span data-ttu-id="132fe-128">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스에 의해 관리되는 사용 가능한 패키지를 검색하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-128">Describes how to discover available packages that are managed by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
 [<span data-ttu-id="132fe-129">프로그래밍 방식으로 패키지 및 폴더 관리</span><span class="sxs-lookup"><span data-stu-id="132fe-129">Managing Packages and Folders Programmatically</span></span>](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 <span data-ttu-id="132fe-130">패키지 및 폴더를 만들고, 이름을 바꾸고, 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-130">Describes how to create, rename, and delete both packages and folders.</span></span>  
  
 [<span data-ttu-id="132fe-131">프로그래밍 방식으로 실행 중인 패키지 관리</span><span class="sxs-lookup"><span data-stu-id="132fe-131">Managing Running Packages Programmatically</span></span>](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 <span data-ttu-id="132fe-132">현재 실행 중인 패키지를 나열하고 해당 속성을 조사하고 실행 중인 패키지를 중지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-132">Describes how to list packages that are currently running, examine their properties, and stop a running package.</span></span>  
  
 [<span data-ttu-id="132fe-133">프로그래밍 방식으로 패키지 역할 관리&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="132fe-133">Managing Package Roles Programmatically &#40;SSIS Service&#41;</span></span>](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 <span data-ttu-id="132fe-134">패키지 또는 폴더에 할당된 역할에 대한 정보를 가져오거나 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-134">Describes how to get or set information about the roles assigned to a package or a folder.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="132fe-135">참조</span><span class="sxs-lookup"><span data-stu-id="132fe-135">Reference</span></span>  
 [<span data-ttu-id="132fe-136">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="132fe-136">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="132fe-137">미리 정의된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 코드와 해당 심볼 이름 및 설명을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-137">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="132fe-138">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="132fe-138">Related Sections</span></span>  
 [<span data-ttu-id="132fe-139">스크립팅을 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="132fe-139">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="132fe-140">스크립트 태스크를 사용하여 제어 흐름을 확장하는 방법과 스크립트 구성 요소를 사용하여 데이터 흐름을 확장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-140">Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="132fe-141">사용자 지정 개체를 사용한 패키지 확장</span><span class="sxs-lookup"><span data-stu-id="132fe-141">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="132fe-142">여러 패키지에서 사용할 프로그램 사용자 지정 태스크, 데이터 흐름 구성 요소 및 기타 패키지 개체를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-142">Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="132fe-143">프로그래밍 방식으로 패키지 빌드</span><span class="sxs-lookup"><span data-stu-id="132fe-143">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="132fe-144">프로그래밍 방식으로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만들고 구성 및 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="132fe-144">Discusses how to create, configure, and save [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="132fe-145">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="132fe-145">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="132fe-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 최신 다운로드, 아티클, 예제 및 비디오와 커뮤니티의 정선된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="132fe-146">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="132fe-147">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="132fe-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="132fe-148">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="132fe-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132fe-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="132fe-149">See Also</span></span>  
 [<span data-ttu-id="132fe-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="132fe-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
