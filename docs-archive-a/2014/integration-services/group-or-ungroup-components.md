---
title: 구성 요소 그룹화 또는 그룹 해제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6811dffca41a12fe0afeeeb334e0107ac127c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647123"
---
# <a name="group-or-ungroup-components"></a><span data-ttu-id="e1cb0-102">구성 요소 그룹화 또는 그룹 해제</span><span class="sxs-lookup"><span data-stu-id="e1cb0-102">Group or Ungroup Components</span></span>
  <span data-ttu-id="e1cb0-103">**디자이너의**제어 흐름 **,** 데이터 흐름 **및** 이벤트 처리기 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭에서는 축소 가능한 그룹화를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-103">The **Control Flow**, **Data Flow**, and **Event Handlers** tabs in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer supports collapsible grouping.</span></span> <span data-ttu-id="e1cb0-104">패키지에 여러 구성 요소가 있는 경우 탭이 복잡해져서 모든 구성 요소를 한 번에 확인하기 어렵고 사용하려는 항목을 쉽게 찾기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-104">If a package has many components, the tabs can become crowded, making it difficult to view all the components at one time and to locate the item with which you want to work.</span></span> <span data-ttu-id="e1cb0-105">축소 가능한 그룹화 기능을 사용하면 작업 공간을 절약하고 큰 패키지를 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-105">The collapsible grouping feature can conserve space on the work surface and make it easier to work with large packages.</span></span>  
  
 <span data-ttu-id="e1cb0-106">그룹화하려는 구성 요소를 선택하여 그룹화한 다음 작업에 맞게 그룹을 확장하거나 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-106">You select the components that you want to group, group them, and then expand or collapse the groups to suit your work.</span></span> <span data-ttu-id="e1cb0-107">그룹을 확장하면 해당 그룹에 들어 있는 구성 요소의 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-107">Expanding a group provides access to the properties of the components in the group.</span></span> <span data-ttu-id="e1cb0-108">태스크와 컨테이너를 연결하는 선행 제약 조건은 그룹에 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-108">The precedence constraints that connect tasks and containers are automatically included in the group.</span></span>  
  
 <span data-ttu-id="e1cb0-109">다음은 구성 요소를 그룹화할 때 고려할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-109">The following are considerations for grouping components.</span></span>  
  
-   <span data-ttu-id="e1cb0-110">구성 요소를 그룹화하려면 제어 흐름, 데이터 흐름 또는 이벤트 처리기에 두 개 이상의 구성 요소가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-110">To group components, the control flow, data flow, or event handler must contain more than one component.</span></span>  
  
-   <span data-ttu-id="e1cb0-111">또한 그룹을 중첩하여 그룹 내에 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-111">Groups can also be nested, making it possible to create groups within groups.</span></span> <span data-ttu-id="e1cb0-112">디자인 화면에서는 중첩되지 않은 여러 그룹을 구현할 수 있지만 그룹이 중첩되지 않은 경우 구성 요소는 하나의 그룹에만 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-112">The design surface can implement multiple un-nested groups, but a component can belong to only one group, unless the groups are nested.</span></span>  
  
-   <span data-ttu-id="e1cb0-113">패키지가 저장되면 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 그룹화 구성이 저장되지만 그룹화 구성은 패키지 실행에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-113">When a package is saved, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the grouping, but the grouping has no effect on package execution.</span></span> <span data-ttu-id="e1cb0-114">구성 요소를 그룹화하는 기능은 디자인 타임 기능이며 패키지의 런타임 동작에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-114">The ability to group components is a design-time feature; it does not affect the run-time behavior of the package.</span></span>  
  
### <a name="to-group-components"></a><span data-ttu-id="e1cb0-115">구성 요소를 그룹화하려면</span><span class="sxs-lookup"><span data-stu-id="e1cb0-115">To group components</span></span>  
  
1.  <span data-ttu-id="e1cb0-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e1cb0-117">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e1cb0-118">**제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-118">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="e1cb0-119">탭의 디자인 화면에서 그룹화하려는 구성 요소를 선택하고 선택한 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-119">On the design surface of the tab, select the components you want to group, right-click a selected component, and then click **Group**.</span></span>  
  
5.  <span data-ttu-id="e1cb0-120">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-ungroup-components"></a><span data-ttu-id="e1cb0-121">구성 요소를 그룹 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e1cb0-121">To ungroup components</span></span>  
  
1.  <span data-ttu-id="e1cb0-122">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e1cb0-123">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e1cb0-124">**제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-124">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="e1cb0-125">탭의 디자인 화면에서 그룹 해제하려는 구성 요소가 들어 있는 그룹을 선택하고 마우스 오른쪽 단추를 클릭한 다음 **그룹 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-125">On the design surface of the tab, select the group that contains the component you want to ungroup, right-click, and then click **Ungroup**.</span></span>  
  
5.  <span data-ttu-id="e1cb0-126">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cb0-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1cb0-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1cb0-127">See Also</span></span>  
 [<span data-ttu-id="e1cb0-128">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="e1cb0-128">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
     
 [<span data-ttu-id="e1cb0-129">기본 선행 제약 조건을 사용하여 태스크 및 컨테이너 연결</span><span class="sxs-lookup"><span data-stu-id="e1cb0-129">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
  
