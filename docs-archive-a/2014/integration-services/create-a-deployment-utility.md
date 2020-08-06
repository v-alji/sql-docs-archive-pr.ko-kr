---
title: 배포 유틸리티 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bdf1328d440920fed98e5fa1d16024c5fec32cbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651831"
---
# <a name="create-a-deployment-utility"></a><span data-ttu-id="177ba-102">Create a Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="177ba-102">Create a Deployment Utility</span></span>
  <span data-ttu-id="177ba-103">패키지를 배포하는 첫 번째 단계는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 배포 유틸리티를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-103">The first step in deploying packages is to create a deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="177ba-104">배포 유틸리티는 다른 서버로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 패키지를 배포하는 데 필요한 파일이 포함된 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-104">The deployment utility is a folder that contains the files you need to deploy the packages in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different server.</span></span> <span data-ttu-id="177ba-105">배포 유틸리티는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트가 저장된 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-105">The deployment utility is created on the computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project is stored.</span></span>  
  
 <span data-ttu-id="177ba-106">먼저 배포 유틸리티를 만들도록 빌드 프로세스를 구성한 다음 프로젝트를 빌드하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 패키지 배포 유틸리티를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-106">You create a package deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project by first configuring the build process to create a deployment utility, and then building the project.</span></span> <span data-ttu-id="177ba-107">프로젝트를 빌드할 때 프로젝트의 모든 패키지와 패키지 구성은 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-107">When you build the project, all packages and package configurations in the project are automatically included.</span></span> <span data-ttu-id="177ba-108">추가 정보 파일 등의 추가 파일을 프로젝트와 함께 배포하려면 해당 파일을 **프로젝트의** 기타 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 폴더에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="177ba-108">To deploy additional files such as a Readme file with the project, place the files in the **Miscellaneous** folder of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="177ba-109">프로젝트가 빌드될 때 이러한 파일도 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-109">When the project is built, these files are also automatically included.</span></span>  
  
 <span data-ttu-id="177ba-110">각 프로젝트 배포를 다르게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-110">You can configure each project deployment differently.</span></span> <span data-ttu-id="177ba-111">프로젝트를 빌드하고 패키지 배포 유틸리티를 작성하기 전에 배포 유틸리티의 속성을 설정하여 프로젝트의 패키지를 배포하는 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-111">Before you build the project and create the package deployment utility, you can set the properties on the deployment utility to customize the way the packages in the project will be deployed.</span></span> <span data-ttu-id="177ba-112">예를 들어 프로젝트를 배포할 때 패키지 구성을 업데이트할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-112">For example, you can specify whether package configurations can be updated when the project is deployed.</span></span> <span data-ttu-id="177ba-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 속성에 액세스하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-113">To access the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, right-click the project and click **Properties**.</span></span>  
  
 <span data-ttu-id="177ba-114">다음 표에서는 배포 유틸리티 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-114">The following table lists the deployment utility properties.</span></span>  
  
|<span data-ttu-id="177ba-115">속성</span><span class="sxs-lookup"><span data-stu-id="177ba-115">Property</span></span>|<span data-ttu-id="177ba-116">Description</span><span class="sxs-lookup"><span data-stu-id="177ba-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="177ba-117">AllowConfigurationChange</span><span class="sxs-lookup"><span data-stu-id="177ba-117">AllowConfigurationChange</span></span>|<span data-ttu-id="177ba-118">배포 도중 구성의 업데이트를 허용할지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-118">A value that specifies whether configurations can be updated during deployment.</span></span>|  
|<span data-ttu-id="177ba-119">CreateDeploymentUtility</span><span class="sxs-lookup"><span data-stu-id="177ba-119">CreateDeploymentUtility</span></span>|<span data-ttu-id="177ba-120">프로젝트를 빌드할 때 패키지 배포 유틸리티를 만들지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-120">A value that specifies whether a package deployment utility is created when the project is built.</span></span> <span data-ttu-id="177ba-121">배포 유틸리티를 만들려면 이 속성을 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-121">This property must be `True` to create a deployment utility.</span></span>|  
|<span data-ttu-id="177ba-122">DeploymentOutputPath</span><span class="sxs-lookup"><span data-stu-id="177ba-122">DeploymentOutputPath</span></span>|<span data-ttu-id="177ba-123">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트와 관련된 배포 유틸리티의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-123">The location, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, of the deployment utility.</span></span>|  
  
 <span data-ttu-id="177ba-124">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 빌드하면 매니페스트 파일인 \<project name>.SSISDeploymentManifest.xml이 패키지 종속 관계 및 패키지의 복사본과 함께 프로젝트의 bin\Deployment 폴더 또는 DeploymentOutputPath 속성에서 지정한 위치에 만들어지고 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-124">When you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, a manifest file, \<project name>.SSISDeploymentManifest.xml, is created and added, together with copies of the project packages and package dependencies, to the bin\Deployment folder in the project, or to the location specified in the DeploymentOutputPath property.</span></span> <span data-ttu-id="177ba-125">매니페스트 파일은 프로젝트의 패키지, 패키지 구성 및 모든 기타 파일을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-125">The manifest file lists the packages, the package configurations, and any miscellaneous files in the project.</span></span>  
  
 <span data-ttu-id="177ba-126">배포 폴더의 내용은 프로젝트를 작성할 때마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-126">The content of the deployment folder is refreshed every time that you build the project.</span></span> <span data-ttu-id="177ba-127">즉, 배포 폴더에 저장되었지만 빌드 프로세스로 폴더에 다시 복사되지 않은 파일은 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-127">This means that any file saved to this folder that is not copied to the folder again by the build process will be deleted.</span></span> <span data-ttu-id="177ba-128">예를 들어 배포 폴더에 저장된 패키지 구성 파일은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-128">For example, package configuration files saved to the deployment folders will be deleted.</span></span>  
  
### <a name="to-create-a-package-deployment-utility"></a><span data-ttu-id="177ba-129">패키지 배포 유틸리티를 만들려면</span><span class="sxs-lookup"><span data-stu-id="177ba-129">To create a package deployment utility</span></span>  
  
1.  <span data-ttu-id="177ba-130">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지 배포 유틸리티를 만들 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트가 들어 있는 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-130">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you want to create a package deployment utility.</span></span>  
  
2.  <span data-ttu-id="177ba-131">프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-131">Right-click the project and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="177ba-132">**\<project name> 속성 페이지** 대화 상자에서 **배포 유틸리티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-132">In the **\<project name> Property Pages** dialog box, click **Deployment Utility**.</span></span>  
  
4.  <span data-ttu-id="177ba-133">패키지를 배포할 때 패키지 구성을 업데이트 하려면 **Allowconfigurationchanges** 를로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-133">To update package configurations when packages are deployed, set **AllowConfigurationChanges** to `True`.</span></span>  
  
5.  <span data-ttu-id="177ba-134">`CreateDeploymentUtility`를 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-134">Set `CreateDeploymentUtility` to `True`.</span></span>  
  
6.  <span data-ttu-id="177ba-135">필요에 따라 `DeploymentOutputPath` 속성을 수정하여 배포 유틸리티의 위치를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-135">Optionally, update the location of the deployment utility by modifying the `DeploymentOutputPath` property.</span></span>  
  
7.  <span data-ttu-id="177ba-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-136">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="177ba-137">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-137">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="177ba-138">**출력** 창에서 빌드 과정 및 빌드 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="177ba-138">View the build progress and build errors in the **Output** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177ba-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="177ba-139">See Also</span></span>  
 <span data-ttu-id="177ba-140">[패키지 구성](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="177ba-140">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="177ba-141">[패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="177ba-141">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="177ba-142">[배포 유틸리티를 사용 하 여 패키지 배포](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span><span class="sxs-lookup"><span data-stu-id="177ba-142">[Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span></span>  
 [<span data-ttu-id="177ba-143">SSIS&#41;패키지 배포 &#40;</span><span class="sxs-lookup"><span data-stu-id="177ba-143">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
