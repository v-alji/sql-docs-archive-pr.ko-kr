---
title: 패키지 설치 마법사 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c15b423c66891e799f7f8dcd27682036dce6d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729600"
---
# <a name="package-installation-wizard-ui-reference"></a><span data-ttu-id="b567d-102">패키지 설치 마법사 UI 참조</span><span class="sxs-lookup"><span data-stu-id="b567d-102">Package Installation Wizard UI Reference</span></span>
  <span data-ttu-id="b567d-103">**패키지 설치 마법사** 를 사용하여 프로젝트에 포함된 패키지 및 기타 파일과 모든 패키지 종속 파일을 포함한 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-103">Use the **Package Installation Wizard** to deploy a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, including the packages and miscellaneous files it contains and any package dependencies.</span></span>  
  
 <span data-ttu-id="b567d-104">패키지를 배포하기 전에 구성을 만들어 패키지와 함께 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-104">Before you deploy packages, you can create configurations and then deploy them with the packages.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="b567d-105">는 구성을 사용하여 런타임 시 패키지와 패키지 개체의 속성을 동적으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-105">uses configurations to dynamically update properties of packages and package objects at run time.</span></span> <span data-ttu-id="b567d-106">예를 들어 연결 문자열이 포함된 속성에 값을 매핑하는 구성을 제공하여 OLE DB 연결의 연결 문자열을 런타임 시 동적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-106">For example, the connection string of an OLE DB connection can be set dynamically at run time by providing a configuration that maps a value to the property that contains the connection string.</span></span>  
  
 <span data-ttu-id="b567d-107">패키지 설치 마법사는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 작성하고 배포 유틸리티를 만든 후에만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-107">You cannot run the Package Installation Wizard until you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and create a deployment utility.</span></span> <span data-ttu-id="b567d-108">자세한 내용은 [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b567d-108">For more information, see [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="b567d-109">다음 섹션에서는 마법사의 페이지에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-109">The following sections describe pages of the wizard.</span></span>  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a><span data-ttu-id="b567d-110">패키지 설치 마법사 시작 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-110">Welcome to the Package Installation Wizard Page</span></span>  
 <span data-ttu-id="b567d-111">**패키지 설치 마법사** 를 사용하여 패키지 배포 유틸리티를 만든 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-111">Use the **Package Installation Wizard** to deploy an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you built a package deployment utility.</span></span>  
  
 <span data-ttu-id="b567d-112">**이 시작 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="b567d-112">**Do not show this starting page again**</span></span>  
 <span data-ttu-id="b567d-113">마법사를 다시 실행할 때 시작 페이지를 건너뛰려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-113">Select to skip the starting page when you run the wizard again.</span></span>  
  
 <span data-ttu-id="b567d-114">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-114">**Next**</span></span>  
 <span data-ttu-id="b567d-115">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-115">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="b567d-116">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-116">**Finish**</span></span>  
 <span data-ttu-id="b567d-117">패키지 설치 마법사 마침 페이지로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-117">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-118">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-118">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="configure-packages-page"></a><span data-ttu-id="b567d-119">패키지 구성 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-119">Configure Packages Page</span></span>  
 <span data-ttu-id="b567d-120">**패키지 구성** 페이지를 사용하여 패키지 구성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-120">Use the **Configure Packages** page to edit package configurations.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b567d-121">옵션</span><span class="sxs-lookup"><span data-stu-id="b567d-121">Options</span></span>  
 <span data-ttu-id="b567d-122">**구성 파일**</span><span class="sxs-lookup"><span data-stu-id="b567d-122">**Configuration file**</span></span>  
 <span data-ttu-id="b567d-123">목록에서 파일을 선택하여 구성 파일의 내용을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-123">Edit the contents of a configuration file by selecting the file from the list.</span></span>  
  
 <span data-ttu-id="b567d-124">**관련 항목:** [패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md)</span><span class="sxs-lookup"><span data-stu-id="b567d-124">**Related Topics:** [Create Package Configurations](../../2014/integration-services/create-package-configurations.md)</span></span>  
  
 <span data-ttu-id="b567d-125">**Path**</span><span class="sxs-lookup"><span data-stu-id="b567d-125">**Path**</span></span>  
 <span data-ttu-id="b567d-126">구성할 속성의 경로를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-126">View the path of the property to be configured.</span></span>  
  
 <span data-ttu-id="b567d-127">**형식**</span><span class="sxs-lookup"><span data-stu-id="b567d-127">**Type**</span></span>  
 <span data-ttu-id="b567d-128">속성의 데이터 형식을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-128">View the data type of the property.</span></span>  
  
 <span data-ttu-id="b567d-129">**값**</span><span class="sxs-lookup"><span data-stu-id="b567d-129">**Value**</span></span>  
 <span data-ttu-id="b567d-130">구성의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-130">Specify the value of the configuration.</span></span>  
  
 <span data-ttu-id="b567d-131">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-131">**Next**</span></span>  
 <span data-ttu-id="b567d-132">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-132">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="b567d-133">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-133">**Finish**</span></span>  
 <span data-ttu-id="b567d-134">패키지 설치 마법사 마침 페이지로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-134">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-135">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-135">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="confirm-installation-page"></a><span data-ttu-id="b567d-136">설치 페이지 확인</span><span class="sxs-lookup"><span data-stu-id="b567d-136">Confirm Installation Page</span></span>  
 <span data-ttu-id="b567d-137">**설치 확인** 페이지를 사용하여 패키지 설치를 시작하고, 상태를 보고, 지정한 프로젝트의 파일을 설치할 때 마법사에서 사용할 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-137">Use the **Confirm Installation** page to start the installation of packages, to view the status, and to view the information that the wizard will use to install files from the specified project.</span></span>  
  
 <span data-ttu-id="b567d-138">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-138">**Next**</span></span>  
 <span data-ttu-id="b567d-139">패키지와 종속 파일을 설치하고 설치가 완료되면 마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-139">Install the packages and their dependencies and go to the next wizard page when installation is completed.</span></span>  
  
 <span data-ttu-id="b567d-140">**상태**</span><span class="sxs-lookup"><span data-stu-id="b567d-140">**Status**</span></span>  
 <span data-ttu-id="b567d-141">패키지 설치 진행률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-141">Shows the progress of the package installation.</span></span>  
  
 <span data-ttu-id="b567d-142">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-142">**Finish**</span></span>  
 <span data-ttu-id="b567d-143">패키지 설치 마법사 마침 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-143">Go to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-144">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-144">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all the required options.</span></span>  
  
## <a name="deploy-ssis-packages-page"></a><span data-ttu-id="b567d-145">SSIS 패키지 배포 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-145">Deploy SSIS Packages Page</span></span>  
 <span data-ttu-id="b567d-146">**SSIS 패키지 배포** 페이지를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지 및 해당 종속성을 설치할 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-146">Use the **Deploy SSIS Packages** page to specify where to install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b567d-147">옵션</span><span class="sxs-lookup"><span data-stu-id="b567d-147">Options</span></span>  
 <span data-ttu-id="b567d-148">**파일 시스템 배포**</span><span class="sxs-lookup"><span data-stu-id="b567d-148">**File system deployment**</span></span>  
 <span data-ttu-id="b567d-149">파일 시스템에서 지정한 폴더에 패키지 및 종속성을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-149">Deploy packages and dependencies in a specified folder in the file system.</span></span>  
  
 <span data-ttu-id="b567d-150">**SQL Server 배포**</span><span class="sxs-lookup"><span data-stu-id="b567d-150">**SQL Server deployment**</span></span>  
 <span data-ttu-id="b567d-151">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 패키지 및 종속성을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-151">Deploy packages and dependencies in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b567d-152">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 서버 간에 패키지를 공유하는 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-152">Use this option if [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shares packages between servers.</span></span> <span data-ttu-id="b567d-153">모든 패키지 종속성은 파일 시스템에서 지정한 폴더에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-153">Any package dependencies are installed in the specified folder in the file system.</span></span>  
  
 <span data-ttu-id="b567d-154">**설치 후 패키지 유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="b567d-154">**Validate packages after installation**</span></span>  
 <span data-ttu-id="b567d-155">설치 후 패키지 유효성 검사 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-155">Indicate whether to validate packages after installation.</span></span>  
  
 <span data-ttu-id="b567d-156">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-156">**Next**</span></span>  
 <span data-ttu-id="b567d-157">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-157">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="b567d-158">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-158">**Finish**</span></span>  
 <span data-ttu-id="b567d-159">패키지 설치 마법사 마침 페이지로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-159">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-160">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-160">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="packages-validation-page"></a><span data-ttu-id="b567d-161">패키지 유효성 검사 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-161">Packages Validation Page</span></span>  
 <span data-ttu-id="b567d-162">**패키지 유효성 검사** 페이지를 사용하여 패키지 유효성 검사의 진행률 및 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-162">Use the **Packages Validation** page to view the progress and results of the package validation.</span></span>  
  
 <span data-ttu-id="b567d-163">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-163">**Next**</span></span>  
 <span data-ttu-id="b567d-164">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-164">Go to the next page in the wizard.</span></span>  
  
## <a name="select-installation-folder-page"></a><span data-ttu-id="b567d-165">설치 폴더 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-165">Select Installation Folder Page</span></span>  
 <span data-ttu-id="b567d-166">**설치 폴더 선택** 페이지를 사용하여 패키지 및 패키지의 종속성을 설치할 파일 시스템 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-166">Use the **Select Installation Folder** page to specify the file system folder in which to install the packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="b567d-167">옵션</span><span class="sxs-lookup"><span data-stu-id="b567d-167">Options</span></span>  
 <span data-ttu-id="b567d-168">**폴더**</span><span class="sxs-lookup"><span data-stu-id="b567d-168">**Folder**</span></span>  
 <span data-ttu-id="b567d-169">패키지 및 해당 패키지의 종속성을 복사할 경로 및 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-169">Specify the path and folder in which to copy the package and its dependencies.</span></span>  
  
 <span data-ttu-id="b567d-170">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="b567d-170">**Browse**</span></span>  
 <span data-ttu-id="b567d-171">**폴더 찾아보기** 대화 상자를 사용하여 대상 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-171">Browse to the target folder by using the **Browse For Folder** dialog box.</span></span>  
  
 <span data-ttu-id="b567d-172">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-172">**Next**</span></span>  
 <span data-ttu-id="b567d-173">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-173">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="b567d-174">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-174">**Finish**</span></span>  
 <span data-ttu-id="b567d-175">패키지 설치 마법사 마침 페이지로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-175">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-176">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-176">Use this option if you have backtracked through the wizard pages to revise your choices and if have specified all of the required options.</span></span>  
  
## <a name="specify-target-sql-server-page"></a><span data-ttu-id="b567d-177">대상 SQL Server 지정 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-177">Specify Target SQL Server Page</span></span>  
 <span data-ttu-id="b567d-178">**대상 SQL Server 지정** 페이지를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 패키지를 배포할 수 있는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-178">Use the **Specify Target SQL Server** page to specify options for deploying the package to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="options"></a><span data-ttu-id="b567d-179">옵션</span><span class="sxs-lookup"><span data-stu-id="b567d-179">Options</span></span>  
 <span data-ttu-id="b567d-180">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="b567d-180">**Server name**</span></span>  
 <span data-ttu-id="b567d-181">패키지를 배포할 서버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-181">Specify the name of the server to deploy the packages to.</span></span>  
  
 <span data-ttu-id="b567d-182">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="b567d-182">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="b567d-183">Windows 인증을 사용하여 서버에 로그온하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-183">Specify whether to use Windows Authentication to log on to the server.</span></span> <span data-ttu-id="b567d-184">보안을 강화하려면 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-184">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="b567d-185">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="b567d-185">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="b567d-186">패키지에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 서버에 로그온하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-186">Specify whether the package should use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to log on to the server.</span></span> <span data-ttu-id="b567d-187">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하는 경우 사용자 이름과 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-187">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="b567d-188">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="b567d-188">**User name**</span></span>  
 <span data-ttu-id="b567d-189">사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-189">Specify a user name.</span></span>  
  
 <span data-ttu-id="b567d-190">**암호**</span><span class="sxs-lookup"><span data-stu-id="b567d-190">**Password**</span></span>  
 <span data-ttu-id="b567d-191">암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-191">Specify a password.</span></span>  
  
 <span data-ttu-id="b567d-192">**패키지 경로**</span><span class="sxs-lookup"><span data-stu-id="b567d-192">**Package path**</span></span>  
 <span data-ttu-id="b567d-193">논리적 폴더의 이름을 지정하거나 "/"를 입력하여 기본 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-193">Specify the name of the logical folder, or enter "/" for the default folder.</span></span>  
  
 <span data-ttu-id="b567d-194">**SSIS 패키지** 대화 상자에서 폴더를 선택하려면 찾아보기(...)를 클릭합니다. 그러나 이 대화 상자에서는 기본 폴더를 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-194">To select the folder in the **SSIS Package** dialog box, click browse (...). However, the dialog box does not provide a means to select the default folder.</span></span> <span data-ttu-id="b567d-195">기본 폴더를 사용하려면 입력란에 "/"를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-195">If you want to use the default folder, you have to enter "/" in the text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b567d-196">유효한 패키지 경로를 입력하지 않으면 "인수 중 하나가 올바르지 않습니다"라는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-196">If you do not enter a valid package path, the following error message appears: "One or more arguments are invalid."</span></span>  
  
 <span data-ttu-id="b567d-197">**암호화에 서버 스토리지 사용**</span><span class="sxs-lookup"><span data-stu-id="b567d-197">**Rely on server storage for encryption**</span></span>  
 <span data-ttu-id="b567d-198">패키지를 보호하기 위해 [!INCLUDE[ssDE](../includes/ssde-md.md)] 의 보안 기능을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-198">Select to use security features of the [!INCLUDE[ssDE](../includes/ssde-md.md)] to help secure the packages.</span></span>  
  
 <span data-ttu-id="b567d-199">**다음**</span><span class="sxs-lookup"><span data-stu-id="b567d-199">**Next**</span></span>  
 <span data-ttu-id="b567d-200">마법사의 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-200">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="b567d-201">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-201">**Finish**</span></span>  
 <span data-ttu-id="b567d-202">패키지 설치 마법사 마침 페이지로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-202">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="b567d-203">마법사 페이지를 역추적하여 선택 내용을 수정하고 필요한 옵션을 모두 지정한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-203">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="finish-the-package-installation-page"></a><span data-ttu-id="b567d-204">패키지 설치 마침 페이지</span><span class="sxs-lookup"><span data-stu-id="b567d-204">Finish the Package Installation Page</span></span>  
 <span data-ttu-id="b567d-205">**패키지 설치 마법사 마침** 페이지를 사용하여 패키지 설치 결과에 대한 요약을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-205">Use the **Finish the Package Installation Wizard** page to view a summary of the package installation results.</span></span> <span data-ttu-id="b567d-206">이 페이지에서는 배포된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 이름, 설치한 패키지, 구성 파일 및 설치 위치와 같은 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-206">This page provides details such as the name of the deployed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, the packages that were installed, the configuration files, and the installation location.</span></span>  
  
 <span data-ttu-id="b567d-207">**마침**</span><span class="sxs-lookup"><span data-stu-id="b567d-207">**Finish**</span></span>  
 <span data-ttu-id="b567d-208">**마침**을 클릭하여 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="b567d-208">Exit the wizard by clicking **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b567d-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b567d-209">See Also</span></span>  
 [<span data-ttu-id="b567d-210">SSIS&#41;패키지 배포 &#40;</span><span class="sxs-lookup"><span data-stu-id="b567d-210">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
