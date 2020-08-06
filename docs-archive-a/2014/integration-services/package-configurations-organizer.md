---
title: 패키지 구성 도우미 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fdc9ca0faeff57c18fdb6e4d10acca3e9963f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736525"
---
# <a name="package-configurations-organizer"></a><span data-ttu-id="fa4ff-102">패키지 구성 도우미</span><span class="sxs-lookup"><span data-stu-id="fa4ff-102">Package Configurations Organizer</span></span>
  <span data-ttu-id="fa4ff-103">**패키지 구성 도우미** 대화 상자를 사용하여 패키지 구성을 설정하고, 현재 패키지에 대한 구성 목록을 보고, 구성을 로드해야 하는 기본 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-103">Use the **Package Configurations Organizer** dialog box to enable package configurations, view a list of configurations for the current package, and specify the preferred order in which the configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa4ff-104">구성은 패키지 배포 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="fa4ff-105">매개 변수는 프로젝트 배포 모델에 대한 구성 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="fa4ff-106">프로젝트 배포 모델을 사용하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="fa4ff-107">배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="fa4ff-108">여러 구성에서 동일한 속성을 업데이트하는 경우 구성 목록에서 더 아래에 있는 구성의 값이 목록에서 위에 있는 구성의 값을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-108">If multiple configurations update the same property, values from configurations listed lower in the configuration list will replace values from configurations higher in the list.</span></span> <span data-ttu-id="fa4ff-109">패키지를 실행하면 마지막으로 속성에 로드된 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-109">The last value loaded into the property is the value that is used when the package runs.</span></span> <span data-ttu-id="fa4ff-110">또한 패키지가 XML 구성 파일 등의 직접 구성과 환경 변수 등의 간접 구성을 조합해서 사용하는 경우 직접 구성의 위치를 가리키는 간접 구성이 목록에서 더 위에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-110">Also, if the package uses a combination of direct configuration such as an XML configuration file and an indirect configuration such as an environment variable, the indirect configuration that points to the location of the direct configuration must be higher in the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa4ff-111">패키지 구성이 기본 순서로 로드되는 경우 **패키지 구성 도우미** 대화 상자에 표시된 목록의 맨 위에서 맨 아래까지의 구성이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-111">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="fa4ff-112">그러나 런타임 시 패키지 구성이 기본 순서로 로드되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-112">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="fa4ff-113">특히 부모 패키지 구성은 다른 유형의 구성보다 뒤에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-113">In particular, Parent Package Configurations load after configurations of other types.</span></span>  
  
 <span data-ttu-id="fa4ff-114">패키지 구성은 런타임 시 패키지 개체의 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-114">Package configurations update the values of properties of package objects at run time.</span></span> <span data-ttu-id="fa4ff-115">패키지가 로드되면 구성의 값이 패키지 개발 시 설정한 값을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-115">When a package is loaded, the values from the configurations replace the values that were set when the package was developed.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fa4ff-116">에서는 여러 가지 구성 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-116">supports different configuration types.</span></span> <span data-ttu-id="fa4ff-117">예를 들어 여러 구성이 포함될 수 있는 XML 파일이나 단일 구성이 포함되는 환경 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-117">For example, you can use an XML file that can contain multiple configurations, or an environment variable that contains a single configuration.</span></span> <span data-ttu-id="fa4ff-118">자세한 내용은 [Package Configurations](../../2014/integration-services/package-configurations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-118">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa4ff-119">옵션</span><span class="sxs-lookup"><span data-stu-id="fa4ff-119">Options</span></span>  
 <span data-ttu-id="fa4ff-120">**패키지 구성 설정**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-120">**Enable package configurations**</span></span>  
 <span data-ttu-id="fa4ff-121">패키지에 구성을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-121">Select to use configurations with the package.</span></span>  
  
 <span data-ttu-id="fa4ff-122">**구성 이름**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-122">**Configuration Name**</span></span>  
 <span data-ttu-id="fa4ff-123">구성의 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-123">View the name of the configuration.</span></span>  
  
 <span data-ttu-id="fa4ff-124">**구성 유형**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-124">**Configuration Type**</span></span>  
 <span data-ttu-id="fa4ff-125">구성이 저장된 위치의 유형을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-125">View the type of the location where configurations are stored.</span></span>  
  
 <span data-ttu-id="fa4ff-126">**구성 문자열**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-126">**Configuration String**</span></span>  
 <span data-ttu-id="fa4ff-127">구성 값이 저장된 위치를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-127">View the location where the configuration values are stored.</span></span> <span data-ttu-id="fa4ff-128">위치는 파일 경로, 환경 변수 이름, 부모 패키지 변수 이름, 레지스트리 키 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-128">The location can be the path of a file, the name of an environment variable, the name of a parent package variable, a Registry key, or the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="fa4ff-129">**대상 개체**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-129">**Target Object**</span></span>  
 <span data-ttu-id="fa4ff-130">구성에서 업데이트하는 개체의 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-130">View the name of the object that the configuration updates.</span></span> <span data-ttu-id="fa4ff-131">구성이 XML 구성 파일이나 SQL Server 테이블인 경우 여러 개체를 포함할 수 있으므로 열이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-131">If the configuration is an XML configuration file or a SQL Server table, the column is blank because the configuration can include multiple objects.</span></span>  
  
 <span data-ttu-id="fa4ff-132">**대상 속성**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-132">**Target Property**</span></span>  
 <span data-ttu-id="fa4ff-133">구성에서 수정하는 속성의 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-133">View the name of the property modified by the configuration.</span></span> <span data-ttu-id="fa4ff-134">구성 유형에서 여러 구성을 지원하는 경우 이 열은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-134">This column is blank if the configuration type supports multiple configurations.</span></span>  
  
 <span data-ttu-id="fa4ff-135">**추가**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-135">**Add**</span></span>  
 <span data-ttu-id="fa4ff-136">패키지 구성 마법사를 사용하여 구성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-136">Add a configuration by using the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="fa4ff-137">**편집**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-137">**Edit**</span></span>  
 <span data-ttu-id="fa4ff-138">패키지 구성 마법사를 다시 실행하여 기존 구성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-138">Edit an existing configuration by rerunning the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="fa4ff-139">**제거**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-139">**Remove**</span></span>  
 <span data-ttu-id="fa4ff-140">구성을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-140">Select a configuration, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="fa4ff-141">**화살표**</span><span class="sxs-lookup"><span data-stu-id="fa4ff-141">**Arrows**</span></span>  
 <span data-ttu-id="fa4ff-142">구성을 선택하고 위로 화살표 및 아래로 화살표를 사용하여 해당 구성을 목록에서 위 또는 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-142">Select a configuration and use the up and down arrows to move it up or down in the list.</span></span> <span data-ttu-id="fa4ff-143">구성은 목록에 나타나는 순서대로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ff-143">Configurations are loaded in the sequence in which they appear in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ff-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa4ff-144">See Also</span></span>  
 [<span data-ttu-id="fa4ff-145">패키지 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="fa4ff-145">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
