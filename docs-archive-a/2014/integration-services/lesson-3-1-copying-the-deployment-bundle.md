---
title: '1단계: 배포 번들 복사 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 326a85a4d04fc22382457b4e2e919f81096ce989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660683"
---
# <a name="step-1-copying-the-deployment-bundle"></a><span data-ttu-id="744d9-102">1단계: 배포 번들 복사</span><span class="sxs-lookup"><span data-stu-id="744d9-102">Step 1: Copying the Deployment Bundle</span></span>
  <span data-ttu-id="744d9-103">이 태스크에서는 배포 번들을 대상 컴퓨터에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-103">In this task, you will copy the deployment bundle to the destination computer.</span></span>  
  
 <span data-ttu-id="744d9-104">배포 번들을 대상 컴퓨터에 복사하는 가장 쉬운 방법은 먼저 대상 컴퓨터에서 공유 위치를 만든 다음 드라이브를 공유 위치에 매핑하고 배포 번들을 공유 위치에 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-104">The easiest way to copy the deployment bundle to the destination computer is to first create a public share on the destination computer, map a drive to the public share, and then copy the deployment bundle to the share.</span></span> <span data-ttu-id="744d9-105">공유 폴더를 생성 및 구성하거나 드라이브를 매핑하는 방법을 모를 경우 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="744d9-105">If you do not know how to create and configure public folders or map drives, see the Windows documentation.</span></span>  
  
### <a name="to-copy-the-deployment-bundle"></a><span data-ttu-id="744d9-106">배포 번들을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="744d9-106">To copy the deployment bundle</span></span>  
  
1.  <span data-ttu-id="744d9-107">컴퓨터에서 배포 번들을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-107">Locate the deployment bundle on your computer.</span></span>  
  
     <span data-ttu-id="744d9-108">기본 위치를 사용한 경우 배포 번들은 Deployment Tutorial 폴더 내의 Bin\Deployment 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-108">If you used the default location, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder.</span></span>  
  
2.  <span data-ttu-id="744d9-109">Deployment 폴더를 마우스 오른쪽 단추로 클릭하고 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-109">Right-click the Deployment folder and click **Copy**.</span></span>  
  
3.  <span data-ttu-id="744d9-110">대상 컴퓨터에서 폴더를 복사할 공유 위치를 찾은 다음 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="744d9-110">Locate the public share to which you want to copy the folder on the target computer and click **Paste**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="744d9-111">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="744d9-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="744d9-112">2단계: 패키지 설치 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="744d9-112">Step 2: Running the Package Installation Wizard</span></span>](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
<span data-ttu-id="744d9-113">![Integration Services 아이콘 (작은 아이콘)](media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="744d9-113">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="744d9-114">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="744d9-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="744d9-115">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="744d9-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="744d9-116">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="744d9-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
