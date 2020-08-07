---
title: 자식 패키지 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4fa4fa7c523c55c595341c7aee6a530c5918a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730843"
---
# <a name="implementation-of-child-packages"></a><span data-ttu-id="528b4-102">자식 패키지 구현</span><span class="sxs-lookup"><span data-stu-id="528b4-102">Implementation of Child Packages</span></span>
  <span data-ttu-id="528b4-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]를 사용하여 로그 균형 조정을 구현하면 사용 가능한 CPU 또는 서버 시간을 사용할 다른 서버에 자식 패키지가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-103">When you implement load balancing using [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], child packages are installed on other servers to take advantage of the available CPU or server time.</span></span> <span data-ttu-id="528b4-104">자식 패키지를 만들고 실행하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="528b4-104">To create and run the child packages requires the following steps:</span></span>  
  
-   <span data-ttu-id="528b4-105">자식 패키지 디자인</span><span class="sxs-lookup"><span data-stu-id="528b4-105">Designing the child packages.</span></span>  
  
-   <span data-ttu-id="528b4-106">원격 서버로 패키지 이동</span><span class="sxs-lookup"><span data-stu-id="528b4-106">Moving the packages to the remote server.</span></span>  
  
-   <span data-ttu-id="528b4-107">자식 패키지를 실행하는 단계가 포함된 원격 서버에 SQL Server 에이전트 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="528b4-107">Creating a SQL Server Agent Job on the remote server that contains a step that runs the child package.</span></span>  
  
-   <span data-ttu-id="528b4-108">SQL Server 에이전트 작업 및 자식 패키지 테스트와 디버깅</span><span class="sxs-lookup"><span data-stu-id="528b4-108">Testing and debugging the SQL Server Agent Job and child packages.</span></span>  
  
 <span data-ttu-id="528b4-109">자식 패키지를 디자인하는 경우 패키지를 디자인하는 데 제한이 없으므로 원하는 모든 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-109">When you design the child packages, the packages have no limitations in their design, and you can put in any functionality you desire.</span></span> <span data-ttu-id="528b4-110">그러나 패키지에서 데이터에 액세스하는 경우 해당 데이터에 액세스할 권한이 패키지를 실행하는 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-110">However, if the package accesses data, you must ensure that the server that runs the package has access to the data.</span></span>  
  
 <span data-ttu-id="528b4-111">자식 패키지를 실행하는 부모 패키지를 확인하려면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 의 솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭한 다음 **진입점 패키지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-111">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="528b4-112">자식 패키지가 디자인되면 원격 서버에 해당 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-112">After the child packages have been designed, the next step is to deploy them on the remote servers.</span></span>  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a><span data-ttu-id="528b4-113">원격 인스턴스로 자식 패키지 이동</span><span class="sxs-lookup"><span data-stu-id="528b4-113">Moving the Child Package to the Remote Instance</span></span>  
 <span data-ttu-id="528b4-114">여러 가지 방법으로 패키지를 다른 서버로 이동할 수 있는데</span><span class="sxs-lookup"><span data-stu-id="528b4-114">There are multiple ways to move packages to other servers.</span></span> <span data-ttu-id="528b4-115">그 중 다음 두 가지 방법이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-115">The two suggested methods are:</span></span>  
  
-   <span data-ttu-id="528b4-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 패키지를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-116">Exporting packages by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="528b4-117">배포할 패키지를 포함하는 프로젝트의 배포 유틸리티를 작성한 다음 패키지를 파일 시스템 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 설치하기 위해 패키지 설치 마법사를 실행하여 패키지를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-117">Deploying packages by building a deployment utility for the project that contains the packages you want to deploy, and then running the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="528b4-118">자세한 내용은 [패키지 배포 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="528b4-118">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="528b4-119">사용할 원격 서버마다 배포를 반복하여 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-119">You must repeat the deployment to each remote server you want to use.</span></span>  
  
## <a name="creating-the-sql-server-agent-jobs"></a><span data-ttu-id="528b4-120">SQL Server 에이전트 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="528b4-120">Creating the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="528b4-121">자식 패키지가 여러 서버에 배포되면 자식 패키지가 포함된 서버마다 SQL Server 에이전트 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-121">After the child packages have been deployed to the various servers, create a SQL Server Agent job on each server that contains a child package.</span></span> <span data-ttu-id="528b4-122">SQL Server 에이전트 작업에는 작업 에이전트 호출 시 자식 패키지를 실행하는 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-122">The SQL Server Agent job contains a step that runs the child package when the job agent is called.</span></span> <span data-ttu-id="528b4-123">SQL Server 에이전트 작업은 예약된 작업이 아니며 부모 패키지에서 호출 시에만 자식 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-123">The SQL Server Agent jobs are not scheduled jobs; they run the child packages only when they are called by the parent package.</span></span> <span data-ttu-id="528b4-124">부모 패키지로 다시 전달되는 작업 성공 또는 실패 알림은 자식 패키지의 성공 또는 실패나 실행 여부가 아니라 SQL Server 에이전트 작업의 성공 또는 실패와 호출 성공 여부를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-124">Notification of success or failure of the job back to the parent package reflects the success or failure of the SQL Server Agent job and whether it was called successfully, not the success or failure of the child package or whether it was executed.</span></span>  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a><span data-ttu-id="528b4-125">SQL Server 에이전트 작업 및 자식 패키지 디버깅</span><span class="sxs-lookup"><span data-stu-id="528b4-125">Debugging the SQL Server Agent Jobs and Child Packages</span></span>  
 <span data-ttu-id="528b4-126">다음 방법 중 하나를 사용하여 SQL Server 에이전트 작업 및 해당 자식 패키지를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-126">You can test the SQL Server Agent jobs and their child packages by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="528b4-127">**Debug**  /  **디버깅 하지 않고 시작**디버그를 클릭 하 여 SSIS 디자이너에서 각 자식 패키지를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-127">Running each child package in SSIS Designer, by clicking **Debug** / **Start Without Debugging**.</span></span>  
  
-   <span data-ttu-id="528b4-128">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 원격 컴퓨터에서 개별 SQL Server 에이전트 작업을 실행하여 패키지가 실행되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-128">Running the individual SQL Server Agent job on the remote computer by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to make sure that the package runs.</span></span>  
  
 <span data-ttu-id="528b4-129">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 작업에서 실행한 패키지의 문제를 해결하는 방법은 [지원 기술 자료에서](https://support.microsoft.com/kb/918760) SQL Server 에이전트 작업 단계에서 SSIS 패키지를 호출할 때 SSIS 패키지가 실행하지 않는다 [!INCLUDE[msCoName](../includes/msconame-md.md)] 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="528b4-129">For information about how to troubleshoot packages that you run from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs, see [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760) in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Support Knowledge Base.</span></span>  
  
 <span data-ttu-id="528b4-130">SQL Server 에이전트는 프록시에 대한 하위 시스템 액세스 권한을 확인하고 작업 단계가 실행될 때마다 프록시에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-130">The SQL Server Agent checks subsystem access for a proxy and gives access to the proxy every time the job step runs.</span></span>  
  
 <span data-ttu-id="528b4-131">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 프록시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="528b4-131">You can create a proxy in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="528b4-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="528b4-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="528b4-133">SQL Server Management Studio를 사용하여 SSIS 서버에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="528b4-133">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="528b4-134">관련 내용</span><span class="sxs-lookup"><span data-stu-id="528b4-134">Related Content</span></span>  
  
-   <span data-ttu-id="528b4-135">Andyleonard의 블로그 항목인 [SSIS: 부모 패키지의 변수 액세스](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)</span><span class="sxs-lookup"><span data-stu-id="528b4-135">Blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), on andyleonard.blog.</span></span>  
  
-   <span data-ttu-id="528b4-136">아티클, [패키지 실행 태스크](../integration-services/control-flow/execute-package-task.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="528b4-136">Article, [Execute Package Task](../integration-services/control-flow/execute-package-task.md).</span></span>  
  
  
