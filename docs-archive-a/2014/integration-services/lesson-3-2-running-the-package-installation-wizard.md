---
title: '2단계: 패키지 설치 마법사 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9492f9ecc843ef475a3c5d32cde2952e0ff498fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728491"
---
# <a name="step-2-running-the-package-installation-wizard"></a><span data-ttu-id="2dd3c-102">2단계: 패키지 설치 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="2dd3c-102">Step 2: Running the Package Installation Wizard</span></span>
  <span data-ttu-id="2dd3c-103">이 태스크에서는 패키지 설치 마법사를 실행하여 Deployment Tutorial 프로젝트의 패키지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-103">In this task, you will run the Package Installation Wizard to deploy the packages from the Deployment Tutorial project to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2dd3c-104">패키지만 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 sysssispackages 테이블에 설치할 수 있고 배포 번들에 포함된 지원 파일은 파일 시스템에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-104">Only packages can be installed in the sysssispackages table in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, the supporting files that the deployment bundle includes will be deployed to the file system.</span></span>  
  
 <span data-ttu-id="2dd3c-105">패키지 설치 마법사는 패키지를 설치하고 구성하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-105">The Package Installation Wizard will guide you through the steps to install and configure the packages.</span></span> <span data-ttu-id="2dd3c-106">배포 번들을 복사한 컴퓨터인 대상 컴퓨터의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-106">You will install the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the destination computer (the computer to which you copied the deployment bundle.</span></span> <span data-ttu-id="2dd3c-107">또한 패키지가 아닌 파일을 마법사에서 설치하는 C:\DeploymentTutorialInstall 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-107">You will also create a folder, C:\DeploymentTutorialInstall, in which the wizard will install the non-package files.</span></span>  
  
 <span data-ttu-id="2dd3c-108">이전 단원에서는 구성을 사용하도록 자습서의 패키지를 수정했습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-108">In an earlier lesson, you modified the packages in the tutorial to use configurations.</span></span> <span data-ttu-id="2dd3c-109">설치되는 환경에서 패키지가 성공적으로 실행될 수 있도록 패키지 설치 마법사를 사용하여 이러한 구성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-109">Using the Package Installation Wizard, you will edit these configurations to enable packages to run successfully in the installed-to environment.</span></span>  
  
### <a name="to-install-the-packages"></a><span data-ttu-id="2dd3c-110">패키지를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="2dd3c-110">To install the packages</span></span>  
  
1.  <span data-ttu-id="2dd3c-111">대상 컴퓨터에서 배포 번들을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-111">On the destination computer, locate the deployment bundle.</span></span>  
  
     <span data-ttu-id="2dd3c-112">배포 유틸리티의 위치로 기본값인 bin\Deployment를 사용한 경우 배포 번들은 Deployment Tutorial 프로젝트의 Deployment 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-112">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Deployment folder in the Deployment Tutorial project.</span></span>  
  
2.  <span data-ttu-id="2dd3c-113">Deployment 폴더에서 매니페스트 파일인 Deployment Tutorial.SSISDeploymentManifest를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-113">In the Deployment folder, double-click the manifest file, Deployment Tutorial.SSISDeploymentManifest.</span></span>  
  
3.  <span data-ttu-id="2dd3c-114">패키지 설치 마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-114">On the Welcome page of the Package Installation Wizard, click **Next**.</span></span>  
  
4.  <span data-ttu-id="2dd3c-115">SSIS 패키지 배포 페이지에서 **SQL Server 배포** 옵션을 선택하고 **설치 후 패키지 유효성 검사** 확인란을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-115">On the Deploy SSIS Packages page, select the **SQL Server deployment** option, select the **Validate packages after installation** check box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2dd3c-116">대상 SQL Server 지정 페이지에서 **서버 이름**상자에 **(local)** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-116">On the Specify Target SQL Server page, specify **(local**), in the **Server name** box.</span></span>  
  
6.  <span data-ttu-id="2dd3c-117">SQL Server 인스턴스에서 Windows 인증이 지원될 경우에는 **Windows 인증 사용**을 선택하고 지원되지 않을 경우에는 **SQL Server 인증 사용** 을 선택하고 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-117">If the instance of SQL Server supports Windows Authentication, select **Use Windows Authentication**; otherwise, select **Use SQL Server Authentication** and provide a user name and a password.</span></span>  
  
7.  <span data-ttu-id="2dd3c-118">**암호화에 서버 스토리지 사용** 확인란의 선택이 취소되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-118">Verify that the **Rely on server storage for encryption** check box is cleared.</span></span>  
  
8.  <span data-ttu-id="2dd3c-119">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-119">Click **Next.**</span></span>  
  
9. <span data-ttu-id="2dd3c-120">설치 폴더 선택 페이지에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-120">On the Select Installation Folder page, click **Browse.**</span></span>  
  
10. <span data-ttu-id="2dd3c-121">**폴더 찾아보기** 대화 상자에서 **내 컴퓨터** 를 확장한 다음 **로컬 디스크(C:)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-121">In the **Browse For Folder** dialog box, expand **My Computer** and then click **Local Disk (C:)**.</span></span>  
  
11. <span data-ttu-id="2dd3c-122">**새 폴더 만들기** 를 클릭하고 새 폴더의 기본 이름인 **새 폴더**를 **DeploymentTutorialInstall**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-122">Click **Make New Folder** and replace the default name of the new folder, **New Folder**, with **DeploymentTutorialInstall**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2dd3c-123">이 이름은 구성이 사용하는 환경 변수 값에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-123">This name is referenced in the value of the environment variables that configurations use.</span></span> <span data-ttu-id="2dd3c-124">폴더 이름과 참조가 일치해야 하며 그렇지 않으면 패키지를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-124">The name of the folder and the reference must match or the package cannot run.</span></span>  
  
12. <span data-ttu-id="2dd3c-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-125">Click **OK**.</span></span>  
  
13. <span data-ttu-id="2dd3c-126">설치 폴더 선택 페이지에서 폴더 상자에 **C:\DeploymentTutorialInstall** 이 있는지 확인한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-126">On the Select Installation Folder page, verify that the Folder box contains **C:\DeploymentTutorialInstall** and then click **Next**.</span></span>  
  
14. <span data-ttu-id="2dd3c-127">설치 확인 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-127">On the Confirm Installation page, click **Next**.</span></span>  
  
     <span data-ttu-id="2dd3c-128">마법사는 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-128">The wizard installs the packages.</span></span> <span data-ttu-id="2dd3c-129">설치가 완료된 후 패키지 구성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-129">After installation is completed, the Configure Packages page opens.</span></span>  
  
15. <span data-ttu-id="2dd3c-130">패키지 구성 페이지에서 **구성 파일** 상자에 datatransferconfig.dtsconfig 및 loadxmldataconfig.dtsconfig가 나열되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-130">On the Configure Packages page, verify that the **Configuration file** box lists datatransferconfig.dtsconfig and loadxmldataconfig.dtsconfig.</span></span>  
  
16. <span data-ttu-id="2dd3c-131">**구성 파일** 목록에서 **datatransferconfig.dtsconfig**를 클릭하고 **구성** 상자의 **경로** 열에서 속성을 확장한 후 **값** 열을 다음 값으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-131">In the **Configuration file** list, click **datatransferconfig.dtsconfig**, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="2dd3c-132">속성</span><span class="sxs-lookup"><span data-stu-id="2dd3c-132">Property</span></span>|<span data-ttu-id="2dd3c-133">값</span><span class="sxs-lookup"><span data-stu-id="2dd3c-133">Value</span></span>|<span data-ttu-id="2dd3c-134">업데이트된 값</span><span class="sxs-lookup"><span data-stu-id="2dd3c-134">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="2dd3c-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="2dd3c-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span></span>|<span data-ttu-id="2dd3c-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="2dd3c-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span></span>|<span data-ttu-id="2dd3c-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="2dd3c-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span></span>|  
    |<span data-ttu-id="2dd3c-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="2dd3c-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span></span>|<span data-ttu-id="2dd3c-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="2dd3c-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span></span>|<span data-ttu-id="2dd3c-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="2dd3c-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span></span>|  
  
17. <span data-ttu-id="2dd3c-141">**구성 파일** 목록에서 loadxmldataconfig.dtsconfig를 클릭하고 **구성** 상자의 **경로** 열에서 속성을 확장한 후 **값** 열을 다음 값으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-141">In the **Configuration file** list, click loadxmldataconfig.dtsconfig, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="2dd3c-142">속성</span><span class="sxs-lookup"><span data-stu-id="2dd3c-142">Property</span></span>|<span data-ttu-id="2dd3c-143">값</span><span class="sxs-lookup"><span data-stu-id="2dd3c-143">Value</span></span>|<span data-ttu-id="2dd3c-144">업데이트된 값</span><span class="sxs-lookup"><span data-stu-id="2dd3c-144">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="2dd3c-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span><span class="sxs-lookup"><span data-stu-id="2dd3c-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span></span>|<span data-ttu-id="2dd3c-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span><span class="sxs-lookup"><span data-stu-id="2dd3c-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span></span>|<span data-ttu-id="2dd3c-147">C:\DeploymentTutorialInstall\orders.xml</span><span class="sxs-lookup"><span data-stu-id="2dd3c-147">C:\DeploymentTutorialInstall\orders.xml</span></span>|  
    |<span data-ttu-id="2dd3c-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span><span class="sxs-lookup"><span data-stu-id="2dd3c-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span></span>|<span data-ttu-id="2dd3c-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="2dd3c-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span></span>|<span data-ttu-id="2dd3c-150">C:\DeploymentTutorialInstall\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="2dd3c-150">C:\DeploymentTutorialInstall\orders.xsd</span></span>|  
  
18. <span data-ttu-id="2dd3c-151">패키지 유효성 검사 페이지에서 설치된 각 패키지의 유효성 검사 결과를 확인한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-151">On the Package Validation page, view the validation results of each package installed and then click **Next**.</span></span>  
  
     <span data-ttu-id="2dd3c-152">대상 컴퓨터의 환경 변수 값이 개발 컴퓨터의 환경 변수 값과 다르므로 패키지 유효성 검사 페이지에 여러 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-152">Because the values of the environment variables on the destination computer differ from the values of the environment variables on the development computer, several warnings appear on the Package Validation page.</span></span> <span data-ttu-id="2dd3c-153">다음 4개의 경고를 예상해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-153">You should expect four warnings:</span></span>  
  
    -   <span data-ttu-id="2dd3c-154">구성 파일 "C:\DeploymentTutorial\DataTransferConfig.dtsConfig"가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-154">The configuration file: "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" is not valid.</span></span> <span data-ttu-id="2dd3c-155">구성 파일 이름을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-155">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="2dd3c-156">패키지에 대한 구성 항목을 적어도 하나 이상 로드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-156">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="2dd3c-157">구성 항목과 이전 경고를 검사하여 실패한 구성에 대한 설명을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-157">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
    -   <span data-ttu-id="2dd3c-158">구성 파일 "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig"가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-158">The configuration file: "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig is not valid.</span></span> <span data-ttu-id="2dd3c-159">구성 파일 이름을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-159">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="2dd3c-160">패키지에 대한 구성 항목을 적어도 하나 이상 로드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-160">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="2dd3c-161">구성 항목과 이전 경고를 검사하여 실패한 구성에 대한 설명을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-161">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
     <span data-ttu-id="2dd3c-162">이러한 경고는 패키지 설치에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-162">These warnings do not affect package installation.</span></span>  
  
     <span data-ttu-id="2dd3c-163">SSIS 패키지 배포 페이지에서 **설치 후 패키지 유효성 검사** 옵션을 선택하지 않은 경우 패키지 유효성 검사 페이지가 열리지 않고 유효성 검사에 대한 사후 설치 정보가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-163">If you did not select the **Validate packages after installation** option on the Deploy SSIS Packages page, the Package Validation pages does not open and the wizard does not display post-installation information about validation.</span></span>  
  
19. <span data-ttu-id="2dd3c-164">패키지 설치 마법사 마침 페이지에서 설치 요약을 읽은 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-164">On the Finish the Package Installation Wizard page, read the installation summary and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2dd3c-165">패키지 유효성 검사에 사용되는 임시 로그 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-165">A temporary log file is created to use in the package validation.</span></span> <span data-ttu-id="2dd3c-166">이 파일은 패키지가 실행될 때 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-166">This file is not used when the package runs.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2dd3c-167">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2dd3c-167">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2dd3c-168">3단계: 배포된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="2dd3c-168">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
<span data-ttu-id="2dd3c-169">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="2dd3c-169">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2dd3c-170">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-170">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2dd3c-171">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-171">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2dd3c-172">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="2dd3c-172">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd3c-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dd3c-173">See Also</span></span>  
 <span data-ttu-id="2dd3c-174">[SSIS 서비스 &#40;Integration Services 서비스&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="2dd3c-174">[Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="2dd3c-175">Integration Services 서비스 관리</span><span class="sxs-lookup"><span data-stu-id="2dd3c-175">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
