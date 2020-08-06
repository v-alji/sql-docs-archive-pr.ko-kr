---
title: Integration Services 프로젝트 개발 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 6e90b016-36a5-415e-9440-a20199fffff0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da648b3b09b25fa2a7b1cf886ad1bf770296f5ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660072"
---
# <a name="development-of-an-integration-services-project"></a><span data-ttu-id="74ff4-102">Integration Services 프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="74ff4-102">Development of an Integration Services Project</span></span>
  <span data-ttu-id="74ff4-103">프로젝트에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-103">You add [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to projects.</span></span> <span data-ttu-id="74ff4-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 만들고 사용하려면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 환경을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-104">To create and work with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, you must install the [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] environment.</span></span> <span data-ttu-id="74ff4-105">자세한 내용은 [Integration Services 설치](install-windows/install-integration-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74ff4-105">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
 <span data-ttu-id="74ff4-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 새 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]프로젝트를 만들 때는 **새 프로젝트** 대화 상자에 **Integration Services 프로젝트** 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-106">When you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the **New Project** dialog box includes an **Integration Services Project** template.</span></span> <span data-ttu-id="74ff4-107">이 프로젝트 템플릿은 하나의 패키지가 포함되어 있는 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-107">This project template creates a new project that contains a single package.</span></span>  
  
## <a name="projects-and-solutions"></a><span data-ttu-id="74ff4-108">프로젝트 및 솔루션</span><span class="sxs-lookup"><span data-stu-id="74ff4-108">Projects and Solutions</span></span>  
 <span data-ttu-id="74ff4-109">프로젝트는 솔루션에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-109">Projects are stored in solutions.</span></span> <span data-ttu-id="74ff4-110">솔루션을 먼저 만든 다음 솔루션에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-110">You can create a solution first and then add an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the solution.</span></span> <span data-ttu-id="74ff4-111">솔루션이 없으면 프로젝트를 만들 때 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 솔루션이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-111">If no solution exists, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates one for you when you first create the project.</span></span> <span data-ttu-id="74ff4-112">솔루션에는 여러 형식의 프로젝트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-112">A solution can contain multiple projects of different types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74ff4-113">기본적으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 새 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]프로젝트를 만들 때는 **솔루션 탐색기** 창에 솔루션이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-113">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the solution is not shown in the **Solution Explorer** pane.</span></span> <span data-ttu-id="74ff4-114">이 기본 동작을 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-114">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="74ff4-115">**옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장한 다음 **일반**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-115">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="74ff4-116">**일반** 페이지에서 **솔루션 항상 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74ff4-116">On the **General** page, select **Always show solution**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="74ff4-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="74ff4-117">Related Tasks</span></span>  
  
-   [<span data-ttu-id="74ff4-118">새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="74ff4-118">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="74ff4-119">Integration Services 프로젝트에 항목 추가</span><span class="sxs-lookup"><span data-stu-id="74ff4-119">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
-   [<span data-ttu-id="74ff4-120">솔루션에서 Integration Services 프로젝트 추가 또는 제거</span><span class="sxs-lookup"><span data-stu-id="74ff4-120">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
