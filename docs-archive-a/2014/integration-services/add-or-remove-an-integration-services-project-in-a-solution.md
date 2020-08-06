---
title: 솔루션에서 Integration Services 프로젝트 추가 또는 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638967"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a><span data-ttu-id="69c3d-102">솔루션에서 Integration Services 프로젝트 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="69c3d-102">Add or Remove an Integration Services Project in a Solution</span></span>
  <span data-ttu-id="69c3d-103">다음 절차에서는 솔루션에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 추가 또는 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-103">The following procedures descibe how to add or remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution.</span></span>  
  
 <span data-ttu-id="69c3d-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 솔루션을 볼 수 있는 경우에만 해당 솔루션에 프로젝트를 추가하거나 솔루션에서 프로젝트를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-104">You can only add a project to an existing solution, or remove a project from a solution, when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="69c3d-105">에서 **솔루션 항상 표시** 옵션을 선택한 경우 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 솔루션이 하나의 프로젝트만 포함 하는 경우에도에서 솔루션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-105">If you have selected the **Always show solution** option in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution even when that solution contains only one project.</span></span> <span data-ttu-id="69c3d-106">그렇지 않은 경우 솔루션은 두 개 이상의 프로젝트를 포함하는 경우에만 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-106">Otherwise, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution only when that solution contains more than one project.</span></span> <span data-ttu-id="69c3d-107">추가 프로젝트는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 프로젝트이거나 다른 형식의 프로젝트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-107">The additional projects can be either [!INCLUDE[ssIS](../includes/ssis-md.md)] projects or projects of other types.</span></span>  
  
## <a name="adding-an-integration-services-project"></a><span data-ttu-id="69c3d-108">Integration Services 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="69c3d-108">Adding an Integration Services Project</span></span>  
 <span data-ttu-id="69c3d-109">프로젝트를 추가할 때 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 새로운 빈 프로젝트를 만들도록 하거나 다른 솔루션용으로 이미 만든 프로젝트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-109">When you add a project, you can have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] create a new, blank project, or you can add a project that you have already created for a different solution.</span></span> <span data-ttu-id="69c3d-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 솔루션을 볼 수 있는 경우에만 해당 솔루션에 프로젝트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-110">You can only add a project to an existing solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a><span data-ttu-id="69c3d-111">솔루션에 새 Integration Services 프로젝트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="69c3d-111">To add a new Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="69c3d-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 새 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 추가하려는 솔루션을 열고 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="69c3d-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="69c3d-113">솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 클릭한 후 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-113">Right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
    -   <span data-ttu-id="69c3d-114">**파일** 메뉴에서 **추가**를 가리키고 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-114">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="69c3d-115">**새 프로젝트 추가** 대화 상자의 **템플릿** 창에서 **Integration Services 프로젝트** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-115">In the **Add New Project** dialog box, click **Integration Services Project** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="69c3d-116">선택적으로 프로젝트 이름과 위치를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-116">Optionally, edit the project name and location.</span></span>  
  
4.  <span data-ttu-id="69c3d-117">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-117">Click **OK**.</span></span>  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a><span data-ttu-id="69c3d-118">솔루션에 기존 Integration Services 프로젝트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="69c3d-118">To add an existing Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="69c3d-119">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 기존 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 추가하려는 솔루션을 열고 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-119">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="69c3d-120">솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 후 **기존 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-120">Right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  
  
    -   <span data-ttu-id="69c3d-121">**파일** 메뉴에서 **추가**를 클릭한 후 **기존 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-121">On the **File** menu, click **Add**, and then click **Existing Project**.</span></span>  
  
2.  <span data-ttu-id="69c3d-122">**기존 프로젝트 추가** 대화 상자에서 추가할 프로젝트를 찾은 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-122">In the **Add Existing Project** dialog box, browse to locate the project you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="69c3d-123">**솔루션 탐색기**의 솔루션 폴더에 프로젝트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-123">The project is added to the solution folder in **Solution Explorer**.</span></span>  
  
## <a name="removing-an-integration-services-project"></a><span data-ttu-id="69c3d-124">Integration Services 프로젝트 제거</span><span class="sxs-lookup"><span data-stu-id="69c3d-124">Removing an Integration Services Project</span></span>  
 <span data-ttu-id="69c3d-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 솔루션을 볼 수 있는 경우에만 해당 솔루션에서 프로젝트를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-125">You can only remove a project from a solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="69c3d-126">솔루션이 표시되면 한 프로젝트를 제외한 나머지 프로젝트를 모두 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-126">After the solution is visible, you can remove all except one project.</span></span> <span data-ttu-id="69c3d-127">프로젝트가 한 개만 남으면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에 더 이상 해당 솔루션 폴더가 표시되지 않으므로 마지막 프로젝트를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-127">As soon as only one project remains, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] no longer displays the solution folder and you cannot remove the last project.</span></span>  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a><span data-ttu-id="69c3d-128">솔루션에서 Integration Services 프로젝트를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="69c3d-128">To remove an Integration Services project from a solution</span></span>  
  
1.  <span data-ttu-id="69c3d-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 제거하려는 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution from which you want to remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="69c3d-130">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **프로젝트 언로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-130">In Solution Explorer, right-click the project, and then click **Unload Project**.</span></span>  
  
3.  <span data-ttu-id="69c3d-131">**확인**을 클릭하여 제거를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="69c3d-131">Click **OK** to confirm the removal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c3d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69c3d-132">See Also</span></span>  
 <span data-ttu-id="69c3d-133">[SSIS&#41; 프로젝트 &#40;Integration Services](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="69c3d-133">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="69c3d-134">새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="69c3d-134">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
