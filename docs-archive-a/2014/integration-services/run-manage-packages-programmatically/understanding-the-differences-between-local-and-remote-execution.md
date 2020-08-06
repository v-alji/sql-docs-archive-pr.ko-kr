---
title: 로컬 실행과 원격 실행의 차이점 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 399584c790f4c5a5dd136121c58a5ff7743f4969
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730836"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a><span data-ttu-id="cfd2f-102">로컬 실행과 원격 실행의 차이점 이해</span><span class="sxs-lookup"><span data-stu-id="cfd2f-102">Understanding the Differences between Local and Remote Execution</span></span>
  <span data-ttu-id="cfd2f-103">패키지 개발자와 관리자는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 실행되는 위치와 관련된 제한 사항을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-103">Package developers and administrators should be aware that there are restrictions related to where an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package runs.</span></span>  
  
-   <span data-ttu-id="cfd2f-104">**패키지는 해당 패키지를 실행하는 프로그램과 동일한 컴퓨터에서 실행됩니다**.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-104">**A package runs on the same computer as the program that launches it**.</span></span> <span data-ttu-id="cfd2f-105">프로그램에서 다른 서버에 원격으로 저장된 패키지를 로드하더라도 해당 패키지는 로컬 컴퓨터에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-105">Even when a program loads a package that is stored remotely on another server, the package runs on the local computer.</span></span>  
  
-   <span data-ttu-id="cfd2f-106">**Integration Services가 설치된 컴퓨터의 개발 환경 외부에서만 패키지를 실행할 수 있습니다**.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-106">**You can only run a package outside the development environment on a computer that has Integration Services installed**.</span></span> <span data-ttu-id="cfd2f-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]가 설치되지 않은 클라이언트 컴퓨터의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 외부에서는 패키지를 실행할 수 없으며, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용권 계약에 따라 추가 컴퓨터에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]를 설치하는 것이 허용되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-107">You cannot run packages outside of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing may not permit you to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cfd2f-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]는 서버 구성 요소이며 클라이언트 컴퓨터에 재배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is a server component and is not redistributable to client computers.</span></span> <span data-ttu-id="cfd2f-109">클라이언트 컴퓨터에서 패키지를 실행하려면 패키지가 서버에서 실행되도록 하는 방식으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-109">To run packages from a client computer, you need to launch them in a manner that ensures that the packages run on the server.</span></span>  
  
 <span data-ttu-id="cfd2f-110">저장된 패키지를 로드 및 실행하는 방법은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-110">For more information about loading and running a saved package, see:</span></span>  
  
-   [<span data-ttu-id="cfd2f-111">프로그래밍 방식으로 로컬 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="cfd2f-111">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [<span data-ttu-id="cfd2f-112">프로그래밍 방식으로 원격 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="cfd2f-112">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 <span data-ttu-id="cfd2f-113">패키지를 실행하고 해당 출력을 사용자 지정 프로그램으로 로드하는 방법은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-113">For more information about running a package and loading its output into a custom program, see:</span></span>  
  
-   [<span data-ttu-id="cfd2f-114">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="cfd2f-114">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
<span data-ttu-id="cfd2f-115">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="cfd2f-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cfd2f-116">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cfd2f-117">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cfd2f-118">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="cfd2f-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd2f-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfd2f-119">See Also</span></span>  
 <span data-ttu-id="cfd2f-120">[프로그래밍 방식으로 로컬 패키지 로드 및 실행](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="cfd2f-120">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 <span data-ttu-id="cfd2f-121">[프로그래밍 방식으로 원격 패키지 로드 및 실행](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="cfd2f-121">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="cfd2f-122">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="cfd2f-122">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
