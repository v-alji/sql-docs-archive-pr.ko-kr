---
title: '1단계: 작업 폴더 및 환경 변수 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63308d406e230538e5ca8b90dbb55bb802759bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651144"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a><span data-ttu-id="69067-102">1단계: 작업 폴더 및 환경 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="69067-102">Step 1: Creating Working Folders and Environment Variables</span></span>
  <span data-ttu-id="69067-103">이 태스크에서는 이후의 자습서 태스크에서 사용할 작업 폴더(C:\DeploymentTutorial)와 새 시스템 환경 변수(`DataTransfer` 및 `LoadXMLData`)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69067-103">In this task, you will create the working folder (C:\DeploymentTutorial) and the new system environment variables (`DataTransfer` and `LoadXMLData`) that you will use in later tutorial tasks.</span></span>  
  
 <span data-ttu-id="69067-104">작업 폴더는 C 드라이브의 루트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69067-104">The working folder is at the root of the C drive.</span></span> <span data-ttu-id="69067-105">필요한 경우 다른 드라이브나 위치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69067-105">If you must use a different drive or location, you can do that.</span></span> <span data-ttu-id="69067-106">단, 해당 위치를 메모해 두었다가 자습서에서 DeploymentTutorial 작업 폴더의 위치를 참조할 때마다 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-106">However, you need to note this location and then use it wherever the tutorial refers to the location of the DeploymentTutorial working folder.</span></span>  
  
 <span data-ttu-id="69067-107">이후 단원에서는 파일 시스템에 저장된 패키지를 msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 sysssispackages 테이블에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-107">In a later lesson, you will deploy packages that are saved to the file system to the sysssispackages table in the msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="69067-108">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 다른 컴퓨터에 배포하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="69067-108">Ideally you will deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to a different computer.</span></span> <span data-ttu-id="69067-109">그렇게 할 수 없는 경우에는 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 패키지를 배포하여 이 자습서에서 수행하는 많은 것들을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69067-109">If that is not possible, you can still learn a lot from doing this tutorial by deploying the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is on the local computer.</span></span> <span data-ttu-id="69067-110">로컬 및 대상 컴퓨터에서 사용되는 환경 변수는 동일한 변수 이름을 가져야 하지만 변수에 다른 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="69067-110">The environment variables that are used on the local and destination computers have the same variable names, but different values are stored in the variables.</span></span> <span data-ttu-id="69067-111">예를 들어 로컬 컴퓨터에서 `DataTransfer` 환경 변수의 값은 C:\DeploymentTutorial 폴더를 참조하고 대상 컴퓨터에서 `DataTransfer` 환경 변수는 C:\DeploymentTutorialInstall 폴더를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-111">For example, on the local computer, the value of the environment variable `DataTransfer` references the C:\DeploymentTutorial folder, whereas on the target computer the environment variable `DataTransfer` references the C:\DeploymentTutorialInstall folder.</span></span>  
  
 <span data-ttu-id="69067-112">로컬 컴퓨터에 배포하려는 경우 하나의 환경 변수 집합만 만들어야 합니다. 단, 로컬 배포를 수행하기 전에 환경 변수의 값을 적절한 값으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-112">If you plan to deploy to the local computer, you need to create only one set of environment variables; however, you will need to update the value of the environment variables to an appropriate value before you do the local deployment.</span></span>  
  
 <span data-ttu-id="69067-113">패키지를 다른 컴퓨터에 배포하려는 경우 두 개의 환경 변수 집합을 만들어야 합니다. 이러한 집합 중 하나는 로컬 컴퓨터용이고 다른 하나는 대상 컴퓨터용입니다.</span><span class="sxs-lookup"><span data-stu-id="69067-113">If you plan to deploy the packages to a different computer, you must create two sets of environment variables: one set for the local computer, and one set for the destination computer.</span></span> <span data-ttu-id="69067-114">지금은 원본 컴퓨터에 대한 변수만 만들 수 있고 나중에 대상 컴퓨터에 대한 변수를 만들 수 있지만 패키지를 대상 컴퓨터에 설치할 수 있으려면 폴더 및 환경 변수를 대상 컴퓨터에서 모두 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-114">You can create only the variables for the source computer now, and create the variables for the destination computer later, but you must have both the folder and environment variables available on the destination computer before you can install the packages on that computer.</span></span>  
  
### <a name="to-create-the-local-working-folder"></a><span data-ttu-id="69067-115">로컬 작업 폴더를 만들려면</span><span class="sxs-lookup"><span data-stu-id="69067-115">To create the local working folder</span></span>  
  
1.  <span data-ttu-id="69067-116">시작 메뉴를 마우스 오른쪽 단추로 클릭하고 탐색을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-116">Right-click the Start menu, and click Explore.</span></span>  
  
2.  <span data-ttu-id="69067-117">**로컬 디스크(C:)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-117">Click **Local Disk (C:)**.</span></span>  
  
3.  <span data-ttu-id="69067-118">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **폴더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-118">On the **File** menu, point to **New**, and then click **Folder**.</span></span>  
  
4.  <span data-ttu-id="69067-119">새 폴더의 이름을로 바꿉니다 `DeploymentTutorial` .</span><span class="sxs-lookup"><span data-stu-id="69067-119">Rename New Folder to `DeploymentTutorial`.</span></span>  
  
### <a name="to-create-local-environment-variables"></a><span data-ttu-id="69067-120">로컬 환경 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="69067-120">To create local environment variables</span></span>  
  
1.  <span data-ttu-id="69067-121">**시작** 메뉴에서 **제어판**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-121">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="69067-122">제어판에서 **시스템**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-122">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="69067-123">**시스템 속성** 대화 상자에서 **고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-123">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="69067-124">**환경 변수** 대화 상자의 **시스템 변수** 프레임에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-124">In the **Environment Variables** dialog box, in the **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="69067-125">**새 시스템 변수** 대화 상자에서 `DataTransfer` **변수 이름** 상자에를 입력 하 고 `C:\DeploymentTutorial\datatransferconfig.dtsconfig` **변수 값** 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-125">In the **New System Variable** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorial\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="69067-126">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-126">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="69067-127">**새로 만들기** 를 다시 클릭 하 고 `LoadXMLData` **변수 이름** 상자에를 입력 하 고 `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` **변수 값** 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-127">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="69067-128">**확인** 을 클릭하여 **환경 변수** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-128">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="69067-129">**확인** 을 클릭하여 **시스템 속성** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-129">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="69067-130">필요에 따라 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-130">Optionally, restart your computer.</span></span> <span data-ttu-id="69067-131">컴퓨터를 다시 시작하지 않을 경우 새 변수의 이름이 패키지 구성 마법사에 표시되지 않지만 새 변수를 사용할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69067-131">If you do not restart the computer, the name of the new variable will not be displayed in the Package Configuration Wizard, but you can still use it.</span></span>  
  
### <a name="to-create-destination-environment-variables"></a><span data-ttu-id="69067-132">대상 환경 변수를 만들려면</span><span class="sxs-lookup"><span data-stu-id="69067-132">To create destination environment variables</span></span>  
  
1.  <span data-ttu-id="69067-133">**시작** 메뉴에서 **제어판**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-133">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="69067-134">제어판에서 **시스템**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-134">In Control Panel, double-click **System**.</span></span>  
  
3.  <span data-ttu-id="69067-135">**시스템 속성** 대화 상자에서 **고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-135">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="69067-136">**환경 변수** 대화 상자의 **시스템 변수** 프레임에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-136">In the **Environment Variables** dialog box, in **System variables** frame, click **New**.</span></span>  
  
5.  <span data-ttu-id="69067-137">**새 시스템 변수** 대화 상자의 변수 `DataTransfer` **이름** 상자에를 입력 하 고 `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` **변수 값** 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-137">In the **New System Variables** dialog box, type `DataTransfer` in the **Variable name** box, and `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
6.  <span data-ttu-id="69067-138">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-138">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="69067-139">**새로 만들기** 를 다시 클릭 하 고 `LoadXMLData` **변수 이름** 상자에를 입력 하 고 `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` **변수 값** 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-139">Click **New** again, and type `LoadXMLData` in the **Variable name** box, and `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` in the **Variable value** box.</span></span>  
  
8.  <span data-ttu-id="69067-140">**확인** 을 클릭하여 **환경 변수** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-140">Click **OK** to exit the **Environment Variables** dialog box.</span></span>  
  
9. <span data-ttu-id="69067-141">**확인** 을 클릭하여 **시스템 속성** 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-141">Click **OK** to exit the **System Properties** dialog box.\</span></span>  
  
10. <span data-ttu-id="69067-142">필요에 따라 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69067-142">Optionally, restart your computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="69067-143">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="69067-143">Next Task in Lesson</span></span>  
 [<span data-ttu-id="69067-144">2단계: 배포 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="69067-144">Step 2: Creating the Deployment Project</span></span>](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
<span data-ttu-id="69067-145">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="69067-145">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="69067-146">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="69067-146">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="69067-147">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="69067-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="69067-148">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="69067-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
