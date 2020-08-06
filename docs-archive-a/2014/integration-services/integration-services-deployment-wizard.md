---
title: Integration Services 배포 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9afdc529baa4546f126eb67456927e770cb345dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736568"
---
# <a name="integration-services-deployment-wizard"></a><span data-ttu-id="7a617-102">Integration Services 배포 마법사</span><span class="sxs-lookup"><span data-stu-id="7a617-102">Integration Services Deployment Wizard</span></span>
  <span data-ttu-id="7a617-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 배포 마법사는 프로젝트 배포 모델을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 SSISDB 카탈로그에 프로젝트를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-103">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard deploys projects to the SSISDB catalog on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance using the project deployment model.</span></span>  
  
 <span data-ttu-id="7a617-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 열려 있는 프로젝트에서 배포 마법사를 시작 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **프로젝트** 메뉴에서 **배포** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-104">To start the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard from an open project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], select **Deploy** from the **Project** menu.</span></span> <span data-ttu-id="7a617-105">에서 마법사를 시작 하려면 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 **Integration Services 카탈로그**  >  **SSISDB** 노드를 확장 하 고 **프로젝트** 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **프로젝트 배포**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-105">To start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** > **SSISDB** node in Object Explorer, right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
 <span data-ttu-id="7a617-106">마법사에서 다음 네 단계가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-106">The wizard proceeds through the following four steps.</span></span> <span data-ttu-id="7a617-107">다음 **을 클릭 하** 여 다음 단계로 이동 하거나 이전 단계로 돌아가려면 **이전** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-107">Click **Next** to move to the next step, or **Previous** to return to the previous step.</span></span>  
  
1.  <span data-ttu-id="7a617-108">**원본 선택** -배포 하려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-108">**Select Source** - Select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that you want to deploy.</span></span>  
  
2.  <span data-ttu-id="7a617-109">**대상 선택** -프로젝트 대상을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-109">**Select Destination** - Select the project destination.</span></span>  
  
3.  <span data-ttu-id="7a617-110">**검토** -선택 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-110">**Review** - Displays your selections.</span></span>  
  
4.  <span data-ttu-id="7a617-111">**배포/결과** -프로젝트를 배포 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-111">**Deploy/Results** - Deploys the project and displays the results.</span></span>  
  
## <a name="select-source"></a><span data-ttu-id="7a617-112">원본 선택</span><span class="sxs-lookup"><span data-stu-id="7a617-112">Select Source</span></span>  
 <span data-ttu-id="7a617-113">만든 프로젝트 배포 파일을 배포 하려면 **프로젝트 배포 파일** 을 선택 하 고 .ispac 파일의 경로를 입력 하거나 **찾아보기** 를 클릭 하 여 프로젝트 폴더에서 찾습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a617-113">To deploy a project deployment file that you created, select **Project deployment file** and enter the path to the .ispac file or click **Browse** to find it in the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project folder.</span></span> <span data-ttu-id="7a617-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 카탈로그에 있는 프로젝트를 배포하려면 **Integration Services 카탈로그**를 선택한 후 서버 이름과 카탈로그에 있는 프로젝트 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-114">To deploy a project that resides in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, select **Integration Services catalog**, and then enter the server name and the path to the project in the catalog.</span></span>  
  
 <span data-ttu-id="7a617-115">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 마법사를 시작하면 기본적으로 마법사에서 열린 프로젝트가 원본으로 선택되고 이 단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-115">If you start the wizard in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], then by default the wizard selects the open project as the source and skips this step.</span></span> <span data-ttu-id="7a617-116">이 단계로 돌아가서 다른 원본을 선택 하려면 **이전** 을 클릭 하거나 왼쪽 창에서 **원본 선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-116">To return to this step and select a different source, click **Previous** or click **Select Source** in the left pane.</span></span>  
  
## <a name="select-destination"></a><span data-ttu-id="7a617-117">대상 선택</span><span class="sxs-lookup"><span data-stu-id="7a617-117">Select Destination</span></span>  
 <span data-ttu-id="7a617-118">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 카탈로그에서 프로젝트에 대한 대상 폴더를 선택하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 입력하거나 서버 목록에서 **찾아보기** 를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-118">To select the destination folder for the project in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or click **Browse** to select from a list of servers.</span></span> <span data-ttu-id="7a617-119">SSISDB에 프로젝트 경로를 입력하거나 **찾아보기** 를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-119">Enter the project path in SSISDB or click **Browse** to select it.</span></span>  
  
 <span data-ttu-id="7a617-120">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 마법사를 시작하면 기본적으로 마법사에서 연결된 서버 인스턴스를 선택하고 선택한 프로젝트에 대한 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-120">If you start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], then by default the wizard selects the connected server instance and enters the path to the selected project.</span></span> <span data-ttu-id="7a617-121">다른 위치에 프로젝트를 배포할 경우 이러한 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-121">You can change these values to deploy the project to a different location.</span></span>  
  
## <a name="review"></a><span data-ttu-id="7a617-122">검토</span><span class="sxs-lookup"><span data-stu-id="7a617-122">Review</span></span>  
 <span data-ttu-id="7a617-123">이 마법사에서는 프로젝트를 배포하기 전에 사용자가 선택한 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-123">The wizard allows you to review the settings you have selected before deploying the project.</span></span> <span data-ttu-id="7a617-124">**이전**을 클릭하거나 왼쪽 창의 단계 중 하나를 클릭하여 선택 항목을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-124">You can change your selections by clicking **Previous**, or by clicking any of the steps in the left pane.</span></span>  
  
## <a name="deployresults"></a><span data-ttu-id="7a617-125">배포/결과</span><span class="sxs-lookup"><span data-stu-id="7a617-125">Deploy/Results</span></span>  
 <span data-ttu-id="7a617-126">**검토** 페이지에서 **배포** 를 클릭 하면 프로젝트가 배포 되 고 **결과** 페이지에 각 동작의 성공 또는 실패 여부가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-126">When you click **Deploy** from the **Review** page, the project is deployed and the **Results** page displays the success or failure of each action.</span></span> <span data-ttu-id="7a617-127">작업이 실패하면 **결과** 열에서 **실패** 를 클릭하여 해당 오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-127">If the action fails, click the **Failed** in the **Result** column to display an explanation of the error.</span></span> <span data-ttu-id="7a617-128">**보고서 저장** ...을 클릭 하 여 결과를 XML 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-128">Click **Save Report...** to save the results to an XML file.</span></span>  
  
 <span data-ttu-id="7a617-129">**닫기**를 클릭하여 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7a617-129">Click **Close** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a617-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a617-130">See Also</span></span>  
 <span data-ttu-id="7a617-131">[Integration Services 서버에 프로젝트 배포](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="7a617-131">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 [<span data-ttu-id="7a617-132">프로젝트 및 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="7a617-132">Deployment of Projects and Packages</span></span>](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
