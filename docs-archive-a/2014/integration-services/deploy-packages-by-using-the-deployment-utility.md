---
title: 배포 유틸리티를 사용 하 여 패키지 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], installing
- installing packages
- dependencies [Integration Services]
- deploying packages [Integration Services], installing
ms.assetid: eaf4b56e-2023-4d17-971c-703031da758c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a09ad307dc0215fca679cfb1ef5a37031f951caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734391"
---
# <a name="deploy-packages-by-using-the-deployment-utility"></a><span data-ttu-id="80a00-102">배포 유틸리티를 사용한 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="80a00-102">Deploy Packages by Using the Deployment Utility</span></span>
  <span data-ttu-id="80a00-103">다른 컴퓨터에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 패키지를 설치하기 위해 배포 유틸리티를 빌드한 다음에는 먼저 대상 컴퓨터에 배포 폴더를 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-103">When you have built a deployment utility to install packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different computer than the one on which the deployment utility was built, you must first copy the deployment folder to the destination computer.</span></span>  
  
 <span data-ttu-id="80a00-104">배포 폴더의 경로는 배포 유틸리티를 만든 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 DeploymentOutputPath 속성에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-104">The path of the deployment folder is specified in the DeploymentOutputPath property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you created the deployment utility.</span></span> <span data-ttu-id="80a00-105">기본 경로는 bin\Deployment이며 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-105">The default path is bin\Deployment, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="80a00-106">자세한 내용은 [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80a00-106">For more information, see [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="80a00-107">패키지 설치 마법사를 사용하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-107">You use the Package Installation Wizard to install the packages.</span></span> <span data-ttu-id="80a00-108">마법사를 시작하려면 배포 폴더를 서버로 복사한 다음 배포 유틸리티 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-108">To launch the wizard, double-click the deployment utility file after you have copied the deployment folder to the server.</span></span> <span data-ttu-id="80a00-109">이 파일의 이름은 \<project name>.SSISDeploymentManifest이며 대상 컴퓨터의 배포 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-109">This file is named \<project name>.SSISDeploymentManifest, and can be found in the deployment folder on the destination computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80a00-110">배포하는 패키지의 버전에 따라 여러 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 함께 설치할 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-110">Depending on the version of the package that you are deploying, you might encounter an error if you have different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installed side-by-side.</span></span> <span data-ttu-id="80a00-111">이 오류는 .SSISDeploymentManifest 파일 이름 확장명이 모든 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전에서 동일하기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-111">This error can occur because the .SSISDeploymentManifest file name extension is the same for all versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="80a00-112">파일을 두 번 클릭하면 가장 최근에 설치된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전의 설치 관리자가 호출되며 이 버전이 배포 유틸리티 파일과 동일한 버전이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-112">Double-clicking the file calls the installer (dtsinstall.exe) for the most recently installed version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], which might not be the same version as the deployment utility file.</span></span> <span data-ttu-id="80a00-113">이 문제를 해결하려면 명령줄에서 정확한 버전의 dtsinstall.exe를 실행한 후 배포 유틸리티 파일의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-113">To work around this problem, run the correct version of dtsinstall.exe from the command line, and provide the path of the deployment utility file.</span></span>  
  
 <span data-ttu-id="80a00-114">패키지 설치 마법사는 파일 시스템 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 패키지를 설치하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-114">The Package Installation Wizard guides you through the steps to install packages to the file system or to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="80a00-115">다음과 같은 방법으로 설치를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-115">You can configure the installation in the following ways:</span></span>  
  
-   <span data-ttu-id="80a00-116">패키지를 설치할 위치 유형 및 위치 선택</span><span class="sxs-lookup"><span data-stu-id="80a00-116">Choosing the location type and location to install the packages.</span></span>  
  
-   <span data-ttu-id="80a00-117">패키지 종속 파일을 설치할 위치 선택</span><span class="sxs-lookup"><span data-stu-id="80a00-117">Choosing location to install package dependencies.</span></span>  
  
-   <span data-ttu-id="80a00-118">대상 서버에 패키지 설치 후 패키지의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="80a00-118">Validating the packages after they are installed on the target server.</span></span>  
  
 <span data-ttu-id="80a00-119">패키지의 파일 기반 종속성은 항상 파일 시스템에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-119">The file-based dependencies for packages are always installed to the file system.</span></span> <span data-ttu-id="80a00-120">파일 시스템에 패키지를 설치한 경우 패키지에 지정한 것과 동일한 폴더에 종속성이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-120">If you install a package to the file system, the dependencies are installed in the same folder as the one that you specify for the package.</span></span> <span data-ttu-id="80a00-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 패키지를 설치하는 경우 파일 기반 종속성을 저장할 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-121">If you install a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify the folder in which to store the file-based dependencies.</span></span>  
  
 <span data-ttu-id="80a00-122">패키지에 대상 컴퓨터에서 사용하기 위해 수정할 구성이 포함된 경우 마법사를 사용하여 속성 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-122">If the package includes configurations that you want to modify for use on the destination computer, you can update the values of the properties by using the wizard.</span></span>  
  
 <span data-ttu-id="80a00-123">패키지 설치 마법사를 사용하여 패키지를 설치하는 방법 이외에도 **dtutil** 명령 프롬프트 유틸리티를 사용하여 패키지를 복사 및 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-123">In addition to installing packages by using the Package Installation Wizard, you can copy and move packages by using the **dtutil** command prompt utility.</span></span> <span data-ttu-id="80a00-124">자세한 내용은 [dtutil Utility](dtutil-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80a00-124">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-deploy-packages-to-an-instance-of-sql-server"></a><span data-ttu-id="80a00-125">SQL Server 인스턴스에 패키지를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="80a00-125">To deploy packages to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="80a00-126">대상 컴퓨터에서 배포 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-126">Open the deployment folder on the target computer.</span></span>  
  
2.  <span data-ttu-id="80a00-127">매니페스트 파일 \<project name>.SSISDeploymentManifest를 두 번 클릭하여 패키지 설치 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-127">Double-click the manifest file, \<project name>.SSISDeploymentManifest, to start the Package Installation Wizard.</span></span>  
  
3.  <span data-ttu-id="80a00-128">**SSIS 패키지 배포** 페이지에서 **SQL Server 배포** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-128">On the **Deploy SSIS Packages** page, select the **SQL Server deployment** option.</span></span>  
  
4.  <span data-ttu-id="80a00-129">필요에 따라 **설치 후 패키지 유효성 검사** 를 선택하여 대상 서버에 패키지를 설치한 후 패키지의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-129">Optionally, select **Validate packages after installation** to validate packages after they are installed on the target server.</span></span>  
  
5.  <span data-ttu-id="80a00-130">**대상 SQL Server 지정** 페이지에서 패키지를 설치할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 지정하고 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-130">On the **Specify Target SQL Server** page, specify the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to install the packages to and select an authentication mode.</span></span> <span data-ttu-id="80a00-131">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 선택하는 경우 사용자 이름 및 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-131">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and a password.</span></span>  
  
6.  <span data-ttu-id="80a00-132">**설치 폴더 선택** 페이지에서 패키지 종속성에 의해 설치될 파일 시스템 내의 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-132">On the **Select Installation Folder** page, specify the folder in the file system for the package dependencies that will be installed.</span></span>  
  
7.  <span data-ttu-id="80a00-133">패키지가 구성을 포함하는 경우 구성 패키지 페이지에서 **값** 목록의 값을 업데이트하여 구성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-133">If the package includes configurations, you can edit configurations by updating values in the **Value** list on the Configure Packages page.</span></span>  
  
8.  <span data-ttu-id="80a00-134">설치 후에 패키지의 유효성 검사를 수행하도록 선택한 경우 배포된 패키지의 유효성 검사 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="80a00-134">If you elected to validate packages after installation, view the validation results of the deployed packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a00-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80a00-135">See Also</span></span>  
 [<span data-ttu-id="80a00-136">SSIS&#41;패키지 배포 &#40;</span><span class="sxs-lookup"><span data-stu-id="80a00-136">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
