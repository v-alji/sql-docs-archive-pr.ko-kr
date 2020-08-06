---
title: '5단계: 업데이트된 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a075af2e030c8257d01abf5eba7d330b1cc8efe7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651124"
---
# <a name="step-5-testing-the-updated-packages"></a><span data-ttu-id="1b6dd-102">5단계: 업데이트된 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="1b6dd-102">Step 5: Testing the Updated Packages</span></span>
  <span data-ttu-id="1b6dd-103">대상 컴퓨터에 자습서 패키지를 설치하는 데 사용할 배포 번들을 만드는 다음 단원을 진행하기 전에 패키지를 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-103">Before you go on to the next lesson, in which you will create the deployment bundle to use to install the tutorial packages on the destination computer, you should test the packages.</span></span> <span data-ttu-id="1b6dd-104">이 태스크에서는 Deployment Tutorial 프로젝트에 추가한 후 구성을 사용하여 확장했던 DataTransfer.dtsx 및 LoadXMLData 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-104">In this task, you will run the packages, DataTransfer.dtsx and LoadXMLData, that you added to the Deployment Tutorial project and then extended with configurations.</span></span>  
  
 <span data-ttu-id="1b6dd-105">패키지가 실행되면 패키지의 각 실행 파일은 성공적으로 완료되었을 때 녹색이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-105">When the packages run, each executable in the package becomes a green color as it completes successfully.</span></span> <span data-ttu-id="1b6dd-106">모든 실행 파일이 녹색이면 패키지가 성공적으로 완료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-106">When all executables are green, the package has completed successfully.</span></span> <span data-ttu-id="1b6dd-107">또한 **진행률** 탭에서 패키지 실행 진행률을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-107">You can also view the package execution progress on the **Progress** tab.</span></span>  
  
 <span data-ttu-id="1b6dd-108">패키지가 성공적으로 실행되지 않은 경우 다음 단원을 진행하기 전에 패키지를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-108">If the packages do not run successfully, you must fix them before you go on to the next lesson.</span></span>  
  
### <a name="to-run-the-datatransfer-package"></a><span data-ttu-id="1b6dd-109">DataTransfer 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="1b6dd-109">To run the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="1b6dd-110">솔루션 탐색기에서 DataTransfer.dtsx를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-110">In Solution Explorer, click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="1b6dd-111">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-111">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="1b6dd-112">패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-112">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-run-the-loadxmldata-package"></a><span data-ttu-id="1b6dd-113">LoadXMLData 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="1b6dd-113">To run the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="1b6dd-114">솔루션 탐색기에서 LoadXMLData.dtsx를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-114">In Solution Explorer, click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="1b6dd-115">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-115">On **Debug** menu, click **Start Debugging**.</span></span>  
  
3.  <span data-ttu-id="1b6dd-116">패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-116">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="1b6dd-117">다음 단원</span><span class="sxs-lookup"><span data-stu-id="1b6dd-117">Next Lesson</span></span>  
 [<span data-ttu-id="1b6dd-118">2단원: 배포 번들 만들기</span><span class="sxs-lookup"><span data-stu-id="1b6dd-118">Lesson 2: Creating the Deployment Bundle</span></span>](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
<span data-ttu-id="1b6dd-119">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1b6dd-119">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1b6dd-120">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-120">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1b6dd-121">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-121">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1b6dd-122">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="1b6dd-122">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
