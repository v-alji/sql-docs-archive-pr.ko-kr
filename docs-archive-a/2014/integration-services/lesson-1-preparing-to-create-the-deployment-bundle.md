---
title: '1단원: 배포 번들 작성 준비 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0deda2a81ddd86d4e40c1c546232b8056264508a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651115"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a><span data-ttu-id="3664d-102">1단원: 배포 번들 작성 준비</span><span class="sxs-lookup"><span data-stu-id="3664d-102">Lesson 1: Preparing to Create the Deployment Bundle</span></span>
  <span data-ttu-id="3664d-103">이 단원에서는 자습서를 지원하는 작업 폴더 및 환경 변수를 만들고 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만든 다음 여러 패키지와 지원 파일을 프로젝트에 추가하고 패키지에서 구성을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-103">In this lesson, you will create the working folders and environment variables that support the tutorial, create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add several packages and their supporting files to the project, and implement configurations in packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="3664d-104">는 패키지를 프로젝트 단위로 배포합니다. 따라서 배포 번들을 만드는 첫 번째 단계에서는 모든 패키지와 패키지 종속 파일을 하나의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 수집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-104">deploys packages on a project basis; therefore, as the first step in creating the deployment bundle, you must collect all the packages and package dependencies into one [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="3664d-105">배포된 패키지에 다른 정보를 포함하면 도움이 되는 경우가 많습니다. 예를 들어 이 패키지 그룹에 대한 기본 설명서를 제공하는 추가 정보 파일을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-105">Frequently it is useful to include other information with the deployed packages: for example you will also add to the project a Readme file that provides basic documentation for this group of packages.</span></span>  
  
 <span data-ttu-id="3664d-106">패키지와 파일을 추가한 후에 아직 구성이 사용되지 않는 패키지에 구성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-106">After you have added the packages and files, you will add configurations to packages that do not already use configurations.</span></span> <span data-ttu-id="3664d-107">이러한 구성은 패키지 및 패키지 개체의 속성을 런타임에 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-107">The configurations update properties of packages and package objects at run time.</span></span> <span data-ttu-id="3664d-108">이후의 단원에서는 배포된 환경에서 패키지를 지원하기 위해 패키지 배포 도중에 이러한 구성의 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-108">In a later lesson, you will modify the values of these configurations during package deployment to support the packages in the deployed-to environment.</span></span>  
  
 <span data-ttu-id="3664d-109">구성을 추가한 후에 ETL 패키지 작성을 위한 [!INCLUDE[ssIS](../includes/ssis-md.md)] 그래픽 도구인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 디자이너에서 패키지를 열고 배포에서 해결해야 하는 문제를 더 잘 이해할 수 있도록 패키지 및 패키지 요소의 속성과 패키지 구성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-109">After you have added the configurations, you should open the packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] graphical tool for building ETL packages, and examine the properties of packages and package elements as well as the package configurations to better understand the issues that the deployment needs to address.</span></span> <span data-ttu-id="3664d-110">예를 들어 패키지 중 하나가 텍스트 파일에서 데이터를 추출하므로 배포된 패키지를 성공적으로 실행하려면 데이터 파일의 위치를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-110">For example, one of the packages extracts data from text files, so the location of the data files must be updated before the deployed packages will run successfully.</span></span>  
  
 <span data-ttu-id="3664d-111">**이 단원에 소요되는 예상 시간:** 1시간</span><span class="sxs-lookup"><span data-stu-id="3664d-111">**Estimated time to complete this lesson:** 1 hour</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="3664d-112">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="3664d-112">Lesson Tasks</span></span>  
 <span data-ttu-id="3664d-113">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="3664d-113">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="3664d-114">1단계: 작업 폴더 및 환경 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="3664d-114">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [<span data-ttu-id="3664d-115">2단계: 배포 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="3664d-115">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [<span data-ttu-id="3664d-116">3단계: 패키지 및 기타 파일 추가</span><span class="sxs-lookup"><span data-stu-id="3664d-116">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [<span data-ttu-id="3664d-117">4단계: 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="3664d-117">Step 4: Adding Package Configurations</span></span>](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [<span data-ttu-id="3664d-118">5단계: 업데이트된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="3664d-118">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="3664d-119">단원 시작</span><span class="sxs-lookup"><span data-stu-id="3664d-119">Start the Lesson</span></span>  
 [<span data-ttu-id="3664d-120">1단계: 작업 폴더 및 환경 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="3664d-120">Step 1: Creating Working Folders and Environment Variables</span></span>](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
<span data-ttu-id="3664d-121">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="3664d-121">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3664d-122">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="3664d-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3664d-123">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="3664d-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3664d-124">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="3664d-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
