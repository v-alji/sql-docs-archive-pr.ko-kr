---
title: '3 단원: 패키지 설치 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8b58cee7bd8e16cd0ca2e726dc8e5eff2cfec5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650175"
---
# <a name="lesson-3-installing-packages"></a><span data-ttu-id="cec5f-102">3단원: 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="cec5f-102">Lesson 3: Installing Packages</span></span>
  <span data-ttu-id="cec5f-103">[2 단원: 배포 번들 만들기](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)에서는 배포 유틸리티를 작성 하 고 다른 컴퓨터에 패키지를 설치 해야 하는 항목이 포함 된 배포 번들을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-103">In [Lesson 2: Creating the Deployment Bundle](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), you built a deployment utility and created the deployment bundle that contains the items that you must install packages on another computer.</span></span> <span data-ttu-id="cec5f-104">또한 배포 번들에서 파일 목록을 확인하고 배포 유틸리티를 작성할 때 만들었던 매니페스트 파일의 내용을 검사했습니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-104">You also verified the file list in the deployment bundle and examined the contents of the manifest file that was created when you built the deployment utility.</span></span>  
  
 <span data-ttu-id="cec5f-105">이 단원에서는 배포 번들을 대상 컴퓨터에 복사한 다음 패키지 설치 마법사를 실행하여 패키지, 패키지 종속 파일 및 보조 파일을 해당 컴퓨터에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-105">In this lesson, you will copy the deployment bundle to the destination computer and then run the Package Installation Wizard to install the packages, package dependencies, and ancillary files on that computer.</span></span> <span data-ttu-id="cec5f-106">패키지는 msdb 데이터베이스에 설치 되 **msdb** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 고 다른 항목은 파일 시스템에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-106">The packages will be installed in the **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database and the other items will be installed in the file system.</span></span> <span data-ttu-id="cec5f-107">패키지 설치를 완료한 후에 패키지 실행 유틸리티를 통해 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 패키지를 실행하여 배포를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-107">After you complete the package installation, you will test the deployment by running the packages from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] using the Execute Package Utility.</span></span>  
  
 <span data-ttu-id="cec5f-108">**이 단원에 소요 되는 예상 시간:** 30 분</span><span class="sxs-lookup"><span data-stu-id="cec5f-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="cec5f-109">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="cec5f-109">Lesson Tasks</span></span>  
 <span data-ttu-id="cec5f-110">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cec5f-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="cec5f-111">1단계: 배포 번들 복사</span><span class="sxs-lookup"><span data-stu-id="cec5f-111">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [<span data-ttu-id="cec5f-112">2단계: 패키지 설치 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="cec5f-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [<span data-ttu-id="cec5f-113">3단계: 배포된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="cec5f-113">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="cec5f-114">단원 시작</span><span class="sxs-lookup"><span data-stu-id="cec5f-114">Start the Lesson</span></span>  
 [<span data-ttu-id="cec5f-115">1단계: 배포 번들 복사</span><span class="sxs-lookup"><span data-stu-id="cec5f-115">Step 1: Copying the Deployment Bundle</span></span>](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
<span data-ttu-id="cec5f-116">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="cec5f-116">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cec5f-117">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cec5f-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cec5f-118">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cec5f-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cec5f-119">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="cec5f-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
