---
title: SQL Server Data Tools에서 패키지 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31ca2390ef6bb04b63e4de9978193aed8884da36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729560"
---
# <a name="run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="f7155-102">SQL Server Data Tools에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="f7155-102">Run a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="f7155-103">패키지는 개발, 디버깅 및 테스팅이 이루어지는 동안 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 일반적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-103">You typically run packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] during the development, debugging, and testing of packages.</span></span> <span data-ttu-id="f7155-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 패키지를 실행하는 경우 패키지는 항상 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-104">When you run a package from [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the package always runs immediately.</span></span>  
  
 <span data-ttu-id="f7155-105">패키지를 실행하는 동안 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너는 **진행률** 탭에 패키지 실행 진행률을 표시합니다. 패키지 및 패키지의 태스크 및 컨테이너의 시작 시각 및 종료 시각을 볼 수 있으며 또한 패키지 내의 실패한 모든 태스크 및 컨테이너에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-105">While a package is running, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer displays the progress of package execution on the **Progress** tab. You can view the start and finish time of the package and its tasks and containers, in addition to information about any tasks or containers in the package that failed.</span></span> <span data-ttu-id="f7155-106">패키지 실행이 종료되면 **실행 결과** 탭에서 런타임 정보를 확인할 수 있습니다. 자세한 내용은 [Debugging Control Flow](control-flow/control-flow.md)항목의 "진행률 보고" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7155-106">After the package finishes running, the run-time information remains available on the **Execution Results** tab. For more information, see the section, "Progress Reporting," in the topic, [Debugging Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="f7155-107">**디자인 타임 배포**.</span><span class="sxs-lookup"><span data-stu-id="f7155-107">**Design-time deployment**.</span></span> <span data-ttu-id="f7155-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 실행하면 패키지가 빌드된 다음 폴더에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-108">When you run a package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the package is built and then deployed to a folder.</span></span> <span data-ttu-id="f7155-109">패키지를 실행하기 전에 패키지가 배포되는 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-109">Before you run the package, you can specify the folder to which the package is deployed.</span></span> <span data-ttu-id="f7155-110">폴더를 지정하지 않으면 **bin** 폴더가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-110">If you do not specify a folder, the **bin** folder is used by default.</span></span> <span data-ttu-id="f7155-111">이러한 종류의 배포를 디자인 타임 배포라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-111">This type of deployment is called design-time deployment.</span></span>  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a><span data-ttu-id="f7155-112">SQL Server Data Tools에서 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="f7155-112">To run a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="f7155-113">솔루션 탐색기에서 솔루션에 여러 프로젝트가 포함되어 있는 경우 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 폴더를 마우스 오른쪽 단추로 클릭한 다음 **시작 개체로 설정** 을 클릭하여 시작 프로젝트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-113">In Solution Explorer, if your solution contains multiple projects, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package, and then click **Set as StartUp Object** to set the startup project.</span></span>  
  
2.  <span data-ttu-id="f7155-114">솔루션 탐색기에서 프로젝트에 여러 패키지가 포함되어 있는 경우 패키지를 마우스 오른쪽 단추로 클릭한 다음 **시작 개체로 설정** 을 클릭하여 시작 패키지를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-114">In Solution Explorer, if your project contains multiple packages, right-click a package, and then click **Set as StartUp Object** to set the startup package.</span></span>  
  
3.  <span data-ttu-id="f7155-115">패키지를 실행하려면 다음 절차 중 하나를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-115">To run a package, use one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="f7155-116">실행하려는 패키지를 연 다음 메뉴 모음에서 **디버깅 시작** 을 클릭하거나 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-116">Open the package that you want to run and then click **Start Debugging** on the menu bar, or press F5.</span></span> <span data-ttu-id="f7155-117">패키지 실행이 완료된 다음 Shift+F5를 눌러서 디자인 모드로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-117">After the package finishes running, press Shift+F5 to return to design mode.</span></span>  
  
    -   <span data-ttu-id="f7155-118">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭한 다음 **패키지 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-118">In Solution Explorer, right-click the package, and then click **Execute Package**.</span></span>  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a><span data-ttu-id="f7155-119">디자인 타임 배포를 위한 다른 폴더를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f7155-119">To specify a different folder for design-time deployment</span></span>  
  
1.  <span data-ttu-id="f7155-120">솔루션 탐색기에서 실행할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 폴더를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-120">In Solution Explorer, right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project folder that contains the package you want to run, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f7155-121">**\<project name> 속성 페이지** 대화 상자에서 **빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-121">In the **\<project name> Property Pages** dialog box, click **Build**.</span></span>  
  
3.  <span data-ttu-id="f7155-122">OutputPath 속성의 값을 업데이트하여 디자인 타임 배포에 사용할 폴더를 지정하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7155-122">Update the value in the OutputPath property to specify the folder you want to use for design-time deployment, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7155-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7155-123">See Also</span></span>  
 <span data-ttu-id="f7155-124">[프로젝트 및 패키지 실행](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="f7155-124">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="f7155-125">Integration Services&#40;SSIS&#41; 패키지</span><span class="sxs-lookup"><span data-stu-id="f7155-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
