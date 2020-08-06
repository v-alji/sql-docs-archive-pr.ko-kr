---
title: Integration Services (SSIS) 프로젝트 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f71555a5339412bd0b79492607769d744c0d1a89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651159"
---
# <a name="integration-services-ssis-projects"></a><span data-ttu-id="508c8-102">Integration Services(SSIS) 프로젝트</span><span class="sxs-lookup"><span data-stu-id="508c8-102">Integration Services (SSIS) Projects</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="508c8-103">에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 패키지 개발을 위해 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-103">provides [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the development of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="508c8-104">데이터베이스 또는 패키지 저장소에 패키지를 배포 하는 경우 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssIS](../includes/ssis-md.md)] 서비스를 사용 하 여 패키지를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-104">When you deploy packages to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, you use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to manage the packages.</span></span> <span data-ttu-id="508c8-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-105">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="508c8-106">서비스에 대한 자세한 내용은 [Integration Services 서비스&#40;SSIS 서비스&#41;](service/integration-services-service-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508c8-106">For more information about the service, see [Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span> <span data-ttu-id="508c8-107">패키지 배포에 대 한 자세한 내용은 [패키지 배포 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="508c8-107">For more information about package deployment, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>

 <span data-ttu-id="508c8-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 배포하는 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 Transact-SQL 뷰 및 저장 프로시저를 사용하여 프로젝트를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-108">When you deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you use Transact-SQL views and stored procedures in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the projects.</span></span> <span data-ttu-id="508c8-109">프로젝트 배포에 대한 자세한 내용은 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="508c8-109">For more information about project deployment, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="508c8-110">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]서버에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 서버](catalog/integration-services-ssis-server-and-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508c8-110">For more information about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>

 <span data-ttu-id="508c8-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 및 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에 대한 개요는 [Integration Services&#40;SSIS&#41; 및 Studio 환경](integration-services-ssis-development-and-management-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508c8-111">For an overview of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="understanding-integration-services-projects"></a><span data-ttu-id="508c8-112">Integration Services 프로젝트 이해</span><span class="sxs-lookup"><span data-stu-id="508c8-112">Understanding Integration Services Projects</span></span>
 <span data-ttu-id="508c8-113">프로젝트는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 개발하는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-113">A project is a container in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="508c8-114">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트는 패키지와 관련된 파일을 저장하고 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-114">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project stores and groups the files that are related to the package.</span></span> <span data-ttu-id="508c8-115">예를 들어 특정 ETL(추출, 변환 및 로드) 솔루션을 만드는 데 필요한 파일이 프로젝트에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-115">For example, a project includes the files that are required to create a specific extract, transfer, and load (ETL) solution.</span></span>

 <span data-ttu-id="508c8-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들려면 먼저 이러한 종류의 프로젝트에 포함되는 기본 내용에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-116">Before you create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, you should become familiar with the basic contents of this kind of project.</span></span> <span data-ttu-id="508c8-117">프로젝트에 포함되는 내용을 이해한 후에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-117">After you understand what a project contains, you can begin creating and working with an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

### <a name="folders-in-integration-services-projects"></a><span data-ttu-id="508c8-118">Integration Services 프로젝트의 폴더</span><span class="sxs-lookup"><span data-stu-id="508c8-118">Folders in Integration Services Projects</span></span>
 <span data-ttu-id="508c8-119">다음 다이어그램은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]프로젝트에 있는 폴더를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-119">The following diagram shows the folders in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="508c8-120">![Integration Services 프로젝트의 폴더](media/solutionexplorer.gif "Integration Services 프로젝트의 폴더")</span><span class="sxs-lookup"><span data-stu-id="508c8-120">![Folders in an Integration Services project](media/solutionexplorer.gif "Folders in an Integration Services project")</span></span>

 <span data-ttu-id="508c8-121">다음 표에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 표시되는 폴더에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-121">The following table describes the folders that appear in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

|<span data-ttu-id="508c8-122">폴더</span><span class="sxs-lookup"><span data-stu-id="508c8-122">Folder</span></span>|<span data-ttu-id="508c8-123">Description</span><span class="sxs-lookup"><span data-stu-id="508c8-123">Description</span></span>|
|------------|-----------------|
|[!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="508c8-124">패키지</span><span class="sxs-lookup"><span data-stu-id="508c8-124">Packages</span></span>|<span data-ttu-id="508c8-125">패키지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-125">Contains packages.</span></span> <span data-ttu-id="508c8-126">자세한 내용은 [Integration Services&#40;SSIS&#41; 패키지](../../2014/integration-services/integration-services-ssis-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="508c8-126">For more information, see [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md).</span></span>|
|<span data-ttu-id="508c8-127">기타</span><span class="sxs-lookup"><span data-stu-id="508c8-127">Miscellaneous</span></span>|<span data-ttu-id="508c8-128">패키지 파일 이외의 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-128">Contains files other than package files.</span></span>|

### <a name="files-in-integration-services-projects"></a><span data-ttu-id="508c8-129">Integration Services 프로젝트의 파일</span><span class="sxs-lookup"><span data-stu-id="508c8-129">Files in Integration Services Projects</span></span>
 <span data-ttu-id="508c8-130">신규 또는 기존 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 솔루션에 추가하면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 확장명이 .dtproj, .dtproj.user 및 .database인 프로젝트 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-130">When you add a new or an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to a solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates project files that have the extensions .dtproj and .dtproj.user and .database.</span></span>

-   <span data-ttu-id="508c8-131">\*.dtproj 파일에는 패키지와 같은 프로젝트 구성 및 항목에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-131">The \*.dtproj file contains information about project configurations and items such as packages.</span></span>

-   <span data-ttu-id="508c8-132">\*.dtproj.user 파일에는 프로젝트를 사용하기 위한 기본 설정에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-132">The \*.dtproj.user file contains information about your preferences for working with the project.</span></span>

-   <span data-ttu-id="508c8-133">\*.database 파일에는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 여는 데 필요한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-133">The \*.database file contains information that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] requires to open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

## <a name="understanding-solutions"></a><span data-ttu-id="508c8-134">솔루션 이해</span><span class="sxs-lookup"><span data-stu-id="508c8-134">Understanding Solutions</span></span>
 <span data-ttu-id="508c8-135">솔루션은 엔드투엔드 비즈니스 솔루션을 개발할 때 사용되는 프로젝트를 그룹화 및 관리하는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-135">A solution is a container that groups and manages the projects that you use when you develop end-to-end business solutions.</span></span> <span data-ttu-id="508c8-136">솔루션을 사용하면 여러 프로젝트를 하나의 단위로 취급하고 비즈니스 솔루션에 관련된 하나 이상의 관련 프로젝트를 하나로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-136">A solution lets you handle multiple projects as one unit and to bring together one or more related projects that contribute to a business solution.</span></span>

 <span data-ttu-id="508c8-137">솔루션에는 여러 형식의 프로젝트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-137">Solutions can include different types of projects.</span></span> <span data-ttu-id="508c8-138">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 만들려면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 제공하는 솔루션의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]프로젝트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-138">If you want to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you work in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution provided by [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="508c8-139">새 솔루션을 만들 때 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 는 솔루션 탐색기에 솔루션 폴더를 추가하고 확장명이 .sln 및 .suo인 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-139">When you create a new solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] adds a Solution folder to Solution Explorer, and creates files that have the extensions, .sln and .suo:</span></span>

-   <span data-ttu-id="508c8-140">\*.sln 파일에는 솔루션 구성에 대한 정보가 포함되고 솔루션의 프로젝트가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-140">The \*.sln file contains information about the solution configuration and lists the projects in the solution.</span></span>

-   <span data-ttu-id="508c8-141">\*.suo 파일에는 솔루션을 사용하기 위한 기본 설정에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-141">The \*.suo file contains information about your preferences for working with the solution.</span></span>

 <span data-ttu-id="508c8-142">새 프로젝트를 만들면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 솔루션이 자동으로 생성되지만 빈 솔루션을 만든 다음 프로젝트를 나중에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-142">While [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates a solution when you create a new project, you can also create a blank solution, and then add projects later.</span></span>

> [!NOTE]
>  <span data-ttu-id="508c8-143">기본적으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 새 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]프로젝트를 만들 때는 **솔루션 탐색기** 에 솔루션이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-143">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the solution is not shown in the **Project Explorer** pane.</span></span> <span data-ttu-id="508c8-144">이 기본 동작을 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-144">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="508c8-145">**옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장한 다음 **일반**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-145">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="508c8-146">**일반** 페이지에서 **솔루션 항상 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="508c8-146">On the **General** page, select **Always show solution**.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="508c8-147">관련 작업</span><span class="sxs-lookup"><span data-stu-id="508c8-147">Related Tasks</span></span>
 [<span data-ttu-id="508c8-148">솔루션에서 Integration Services 프로젝트 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="508c8-148">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)

 [<span data-ttu-id="508c8-149">새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="508c8-149">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)

 [<span data-ttu-id="508c8-150">Integration Services 프로젝트에 항목 추가</span><span class="sxs-lookup"><span data-stu-id="508c8-150">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)

 [<span data-ttu-id="508c8-151">프로젝트 항목 복사</span><span class="sxs-lookup"><span data-stu-id="508c8-151">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)

## <a name="related-content"></a><span data-ttu-id="508c8-152">관련 내용</span><span class="sxs-lookup"><span data-stu-id="508c8-152">Related Content</span></span>
 [<span data-ttu-id="508c8-153">Integration Services 프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="508c8-153">Development of an Integration Services Project</span></span>](../../2014/integration-services/development-of-an-integration-services-project.md)


