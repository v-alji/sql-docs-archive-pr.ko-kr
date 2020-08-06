---
title: '2단계: 배포 번들 확인 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f452a87154175ac05a050761d8f12b6bfe61cd8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647112"
---
# <a name="step-2-verifying-the-deployment-bundle"></a><span data-ttu-id="3822c-102">2단계: 배포 번들 확인</span><span class="sxs-lookup"><span data-stu-id="3822c-102">Step 2: Verifying the Deployment Bundle</span></span>
  <span data-ttu-id="3822c-103">1단원에서는 Deployment Tutorial 프로젝트를 만들고 패키지와 보조 파일을 프로젝트에 추가했습니다. 이전 태스크에서는 프로젝트를 위한 배포 유틸리티를 작성했습니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-103">In lesson 1, you created the Deployment Tutorial project and added packages and ancillary files to the project; in the previous task you built a deployment utility for the project.</span></span>  
  
 <span data-ttu-id="3822c-104">이 태스크에서는 배포 번들의 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-104">In this task, you will verify the contents of the deployment bundle.</span></span> <span data-ttu-id="3822c-105">배포 번들은 대상 컴퓨터에 복사하고 패키지를 설치하는 데 사용하는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-105">The deployment bundle is the folder that you will copy to the destination computer and use to install packages.</span></span> <span data-ttu-id="3822c-106">배포 유틸리티의 위치로 기본값인 bin\Deployment를 사용한 경우 배포 번들은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트의 Deployment Tutorial 폴더 내에 있는 Bin\Deployment 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-106">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a><span data-ttu-id="3822c-107">배포 번들의 내용을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="3822c-107">To verify the content of deployment bundle</span></span>  
  
1.  <span data-ttu-id="3822c-108">컴퓨터에서 bin\Deployment 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-108">Locate the bin\Deployment folder on your computer.</span></span>  
  
2.  <span data-ttu-id="3822c-109">다음 파일이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-109">Verify that the following files are present:</span></span>  
  
    -   <span data-ttu-id="3822c-110">DataTransfer.dtsx</span><span class="sxs-lookup"><span data-stu-id="3822c-110">DataTransfer.dtsx</span></span>  
  
    -   <span data-ttu-id="3822c-111">datatransferconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="3822c-111">datatransferconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="3822c-112">Deployment Tutorial.SSISDeploymentManifest</span><span class="sxs-lookup"><span data-stu-id="3822c-112">Deployment Tutorial.SSISDeploymentManifest</span></span>  
  
    -   <span data-ttu-id="3822c-113">LoadXMLData.dtsx</span><span class="sxs-lookup"><span data-stu-id="3822c-113">LoadXMLData.dtsx</span></span>  
  
    -   <span data-ttu-id="3822c-114">loadxmldataconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="3822c-114">loadxmldataconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="3822c-115">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="3822c-115">NewCustomers.txt</span></span>  
  
    -   <span data-ttu-id="3822c-116">orders.xml</span><span class="sxs-lookup"><span data-stu-id="3822c-116">orders.xml</span></span>  
  
    -   <span data-ttu-id="3822c-117">orders.xsd</span><span class="sxs-lookup"><span data-stu-id="3822c-117">orders.xsd</span></span>  
  
    -   <span data-ttu-id="3822c-118">Readme.txt</span><span class="sxs-lookup"><span data-stu-id="3822c-118">Readme.txt</span></span>  
  
3.  <span data-ttu-id="3822c-119">Deployment Tutorial.SSISDeploymentManifest를 마우스 오른쪽 단추로 클릭하고 **연결 프로그램**을 가리킨 다음 **Internet Explorer**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-119">Right-click Deployment Tutorial.SSISDeploymentManifest, point **to Open With**, and then click **Internet Explorer**.</span></span> <span data-ttu-id="3822c-120">또한 메모장과 같은 텍스트 편집기에서 파일을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-120">You can also open the file in a text editor such as Notepad.</span></span> <span data-ttu-id="3822c-121">파일의 XML 코드는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-121">The XML code of the file should be the following:</span></span>  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  <span data-ttu-id="3822c-122">`AllowConfigurationChanges`특성 값이 **true** 이 고 xml에 두 패키지 각각에 대 한 요소 `Package` , 두 개의 `MiscellaneousFile` 비 패키지 파일에 대 한 요소, `ConfigurationFile` 두 xml 구성 파일 각각에 대 한 요소가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-122">Verify that the value of the `AllowConfigurationChanges` attribute is **true** and the XML includes a `Package` element for each of the two packages, a `MiscellaneousFile` element for each of the four non-package files, and a `ConfigurationFile` element for each of the two XML configuration files.</span></span>  
  
5.  <span data-ttu-id="3822c-123">Internet Explorer 또는 텍스트 편집기를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="3822c-123">Exit Internet Explorer or the text editor.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3822c-124">다음 단원</span><span class="sxs-lookup"><span data-stu-id="3822c-124">Next Lesson</span></span>  
 [<span data-ttu-id="3822c-125">3단원: 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="3822c-125">Lesson 3: Installing Packages</span></span>](../integration-services/lesson-3-install-ssis-package.md)  
  
<span data-ttu-id="3822c-126">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="3822c-126">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3822c-127">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="3822c-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3822c-128">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="3822c-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3822c-129">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="3822c-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
