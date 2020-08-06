---
title: '2 단원: 배포 번들 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 927bcd393e4b54e92971c197d93dcc1e2804dcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652901"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a><span data-ttu-id="777f2-102">2단원: 배포 번들 만들기</span><span class="sxs-lookup"><span data-stu-id="777f2-102">Lesson 2: Creating the Deployment Bundle</span></span>
  <span data-ttu-id="777f2-103">[1단원: 배포 번들 작성 준비](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)에서는 Deployment Tutorial이라는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들고 패키지 및 지원 파일을 이 프로젝트에 추가했으며 패키지에서 구성을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-103">In [Lesson 1: Preparing to Create the Deployment Bundle](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md), you created the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project named Deployment Tutorial, added the packages and supporting files to the project, and implemented configurations in packages.</span></span>  
  
 <span data-ttu-id="777f2-104">이 단원에서는 패키지를 다른 컴퓨터에 설치하는 데 필요한 항목을 포함하는 폴더인 배포 번들을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-104">In this lesson, you will create the deployment bundle, which is a folder that contains the items that you need to install packages on another computer.</span></span> <span data-ttu-id="777f2-105">배포 번들은 Deployment Tutorial 프로젝트의 배포 매니페스트, 패키지 복사본 및 지원 파일 복사본을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-105">The deployment bundle will include a deployment manifest, copies of the packages, and copies of the supporting files from the Deployment Tutorial project.</span></span> <span data-ttu-id="777f2-106">배포 매니페스트는 배포 번들의 패키지, 기타 파일 및 구성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-106">The deployment manifest lists the packages, miscellaneous files, and configurations in the deployment bundle.</span></span>  
  
 <span data-ttu-id="777f2-107">또한 배포 번들의 파일 목록을 확인하고 매니페스트의 내용을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-107">You will also verify the file list in the deployment bundle and examine the contents of the manifest.</span></span>  
  
 <span data-ttu-id="777f2-108">**이 단원에 소요되는 예상 시간:** 30분</span><span class="sxs-lookup"><span data-stu-id="777f2-108">**Estimated time to complete this lesson:** 30 minutes</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="777f2-109">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="777f2-109">Lesson Tasks</span></span>  
 <span data-ttu-id="777f2-110">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="777f2-110">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="777f2-111">1단계: 배포 유틸리티 작성</span><span class="sxs-lookup"><span data-stu-id="777f2-111">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [<span data-ttu-id="777f2-112">2단계: 배포 번들 확인</span><span class="sxs-lookup"><span data-stu-id="777f2-112">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="777f2-113">단원 시작</span><span class="sxs-lookup"><span data-stu-id="777f2-113">Start the Lesson</span></span>  
 [<span data-ttu-id="777f2-114">1단계: 배포 유틸리티 작성</span><span class="sxs-lookup"><span data-stu-id="777f2-114">Step 1: Building the Deployment Utility</span></span>](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
<span data-ttu-id="777f2-115">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="777f2-115">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="777f2-116">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="777f2-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="777f2-117">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="777f2-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="777f2-118">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="777f2-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
