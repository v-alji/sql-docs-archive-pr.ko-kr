---
title: '1단계: 배포 유틸리티 작성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d32dcbf4bfcf9758dfe58803b75094d1807aa90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651109"
---
# <a name="step-1-building-the-deployment-utility"></a><span data-ttu-id="81a75-102">1단계: 배포 유틸리티 빌드</span><span class="sxs-lookup"><span data-stu-id="81a75-102">Step 1: Building the Deployment Utility</span></span>
  <span data-ttu-id="81a75-103">이 태스크에서는 Deployment Tutorial 프로젝트를 위한 배포 유틸리티를 구성 및 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-103">In this task, you will configure and build a deployment utility for the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="81a75-104">배포 유틸리티를 작성할 수 있으려면 Deployment Tutorial 프로젝트의 속성을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-104">Before you can build the deployment utility, you must modify the properties of the Deployment Tutorial project.</span></span> <span data-ttu-id="81a75-105">**Deployment Tutorial 속성 페이지** 대화 상자를 사용하여 이러한 속성을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-105">You will use the **Deployment Tutorial Property Pages** dialog box to configure these properties.</span></span> <span data-ttu-id="81a75-106">이 대화 상자에서 배포 중에 구성을 업데이트하는 기능을 설정하고 빌드 프로세스에서 배포 유틸리티를 생성하도록 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-106">In this dialog box, you must enable the ability to update configurations during deployment and specify that the build process generates a deployment utility.</span></span> <span data-ttu-id="81a75-107">속성을 설정한 후에 프로젝트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-107">After you set the properties, you will build the project.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="81a75-108">에서는 패키지를 디버그하는 데 사용할 수 있는 일련의 창이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-108">provides a set of windows that you can use to debug packages.</span></span> <span data-ttu-id="81a75-109">오류, 경고 및 정보 메시지를 확인하고 런타임에 패키지 상태를 추적하며 빌드 프로세스의 진행률과 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-109">You can view error, warning, and information messages, track about the status of packages at run time, or view the progress and results of build processes.</span></span> <span data-ttu-id="81a75-110">이 단원에서는 출력 창을 사용하여 배포 유틸리티 작성의 진행률과 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-110">For this lesson, you will use the Output window to view the progress and results of building the deployment utility.</span></span>  
  
### <a name="to-set-the-deployment-utility-properties"></a><span data-ttu-id="81a75-111">배포 유틸리티 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="81a75-111">To set the deployment utility properties</span></span>  
  
1.  <span data-ttu-id="81a75-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 아직 열지 않은 경우 **시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **Business Intelligence Development Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-112">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="81a75-113">**파일** 메뉴에서 **열기**, **프로젝트/솔루션**, **Deployment Tutorial** 폴더, **열기**를 차례로 클릭한 다음 **Deployment Tutorial.sln**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-113">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="81a75-114">솔루션 탐색기에서 Deployment Tutorial을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-114">In Solution Explorer, right-click Deployment Tutorial and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="81a75-115">**Deployment Tutorial 속성 페이지** 대화 상자에서 구성 속성을 확장하고 배포 유틸리티를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-115">In the **Deployment Tutorial Property Pages** dialog box, expand Configuration Properties, and click Deployment Utility.</span></span>  
  
5.  <span data-ttu-id="81a75-116">**Deployment Tutorial 속성 페이지** 대화 상자의 오른쪽 창에서 `AllowConfigurationChanges` 가로 설정 되어 있는지 확인 하 고를 `true` 로 설정한 `CreateDeploymentUtility` `true` 다음 필요에 따라의 기본값을 업데이트 `DeploymentOutputPath` 합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-116">In the right pane of the **Deployment Tutorial Property Pages** dialog box, verify that `AllowConfigurationChanges` is set to `true`, set `CreateDeploymentUtility` to `true`, and optionally update the default value of `DeploymentOutputPath`.</span></span>  
  
6.  <span data-ttu-id="81a75-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-117">Click **OK**.</span></span>  
  
### <a name="to-build-the-deployment-utility"></a><span data-ttu-id="81a75-118">배포 유틸리티를 작성하려면</span><span class="sxs-lookup"><span data-stu-id="81a75-118">To build the deployment utility</span></span>  
  
1.  <span data-ttu-id="81a75-119">솔루션 탐색기에서 **Deployment Tutorial**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-119">In Solution Explorer, click **Deployment Tutorial**.</span></span>  
  
2.  <span data-ttu-id="81a75-120">**보기** 메뉴에서 **출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-120">On the **View** menu, click **Output**.</span></span> <span data-ttu-id="81a75-121">기본적으로 출력 창은 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 왼쪽 하단 모퉁이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-121">By default, the Output window is located in the bottom left corner of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="81a75-122">**빌드** 메뉴에서 **Deployment Tutorial 빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-122">On the **Build** menu, click **Build Deployment Tutorial**.</span></span>  
  
4.  <span data-ttu-id="81a75-123">출력 창에서 다음 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-123">In the Output window, verify the following information:</span></span>  
  
     <span data-ttu-id="81a75-124">빌드 시작: SQL Integration Services 프로젝트: 증분...</span><span class="sxs-lookup"><span data-stu-id="81a75-124">Build started: SQL Integration Services project: Incremental ...</span></span>  
  
     <span data-ttu-id="81a75-125">배포 유틸리티를 만드는 중...</span><span class="sxs-lookup"><span data-stu-id="81a75-125">Creating deployment utility...</span></span>  
  
     <span data-ttu-id="81a75-126">배포 유틸리티가 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-126">Deployment Utility created.</span></span>  
  
     <span data-ttu-id="81a75-127">빌드 완료 -- 0개 오류, 0개 경고</span><span class="sxs-lookup"><span data-stu-id="81a75-127">Build complete -- 0 errors, 0 warnings</span></span>  
  
     <span data-ttu-id="81a75-128">========== 빌드: 성공 0, 실패 0, 최신 1, 생략 0 ==========</span><span class="sxs-lookup"><span data-stu-id="81a75-128">========== Build: 0 succeeded, 0 failed, 1 up-to-date, 0 skipped ==========</span></span>  
  
5.  <span data-ttu-id="81a75-129">**파일** 메뉴에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-129">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="81a75-130">Deployment Tutorial 항목의 변경 내용을 저장할 것인지 묻는 메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="81a75-130">If prompted to save changes to Deployment Tutorial items, click **Yes**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="81a75-131">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="81a75-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="81a75-132">2단계: 배포 번들 확인</span><span class="sxs-lookup"><span data-stu-id="81a75-132">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
<span data-ttu-id="81a75-133">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="81a75-133">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="81a75-134">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81a75-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="81a75-135">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81a75-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="81a75-136">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="81a75-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a75-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81a75-137">See Also</span></span>  
 [<span data-ttu-id="81a75-138">배포 유틸리티 만들기</span><span class="sxs-lookup"><span data-stu-id="81a75-138">Create a Deployment Utility</span></span>](../../2014/integration-services/create-a-deployment-utility.md)  
  
  
