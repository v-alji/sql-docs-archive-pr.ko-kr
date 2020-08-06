---
title: 제어 흐름 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], elements
- SSIS control flow elements
- SQL Server Integration Services control flow elements
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81ace5d285a67c6fee8a3a568ed89bc564193c42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650219"
---
# <a name="control-flow"></a><span data-ttu-id="fcf5f-102">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="fcf5f-102">Control Flow</span></span>
  <span data-ttu-id="fcf5f-103">패키지는 제어 흐름과 하나 이상의 데이터 흐름(선택적)으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-103">A package consists of a control flow and, optionally, one or more data flows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fcf5f-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서는 패키지의 구조를 제공하는 컨테이너, 기능을 제공하는 태스크 및 실행 파일, 컨테이너, 태스크를 정렬된 제어 흐름으로 연결하는 선행 제약 조건 등 3가지 유형의 제어 흐름 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides three different types of control flow elements: containers that provide structures in packages, tasks that provide functionality, and precedence constraints that connect the executables, containers, and tasks into an ordered control flow.</span></span>

 <span data-ttu-id="fcf5f-105">자세한 내용은 [Precedence Constraints](precedence-constraints.md), [Integration Services Containers](integration-services-containers.md)및 [Integration Services Tasks](integration-services-tasks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-105">For more information, see [Precedence Constraints](precedence-constraints.md), [Integration Services Containers](integration-services-containers.md), and [Integration Services Tasks](integration-services-tasks.md).</span></span>

 <span data-ttu-id="fcf5f-106">다음 다이어그램에서는 하나의 컨테이너와 6개의 태스크가 포함된 하나의 제어 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-106">The following diagram shows a control flow that has one container and six tasks.</span></span> <span data-ttu-id="fcf5f-107">태스크 중 5개는 패키지 수준에서 정의되며 남은 하나의 태스크는 컨테이너 수준에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-107">Five of the tasks are defined at the package level, and one task is defined at the container level.</span></span> <span data-ttu-id="fcf5f-108">이 태스크는 컨테이너 내부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-108">The task is inside a container.</span></span>

 <span data-ttu-id="fcf5f-109">![6개의 태스크와 1개의 컨테이너가 있는 제어 흐름](../media/ssis-controlflowelmt.gif "6개의 태스크와 1개의 컨테이너가 있는 제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="fcf5f-109">![Control flow with six tasks and a container](../media/ssis-controlflowelmt.gif "Control flow with six tasks and a container")</span></span>

 <span data-ttu-id="fcf5f-110">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 아키텍처는 컨테이너 중첩을 지원하며 제어 흐름에는 중첩된 컨테이너의 여러 수준이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-110">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] architecture supports the nesting of containers, and a control flow can include multiple levels of nested containers.</span></span> <span data-ttu-id="fcf5f-111">예를 들어 패키지에는 또 다른 Foreach 루프 컨테이너 등을 포함할 수 있는 Foreach 루프 컨테이너와 같은 컨테이너가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-111">For example, a package could contain a container such as a Foreach Loop container, which in turn could contain another Foreach Loop container and so on.</span></span>

 <span data-ttu-id="fcf5f-112">또한 이벤트 처리기에는 같은 종류의 제어 흐름 요소를 사용하여 작성되는 제어 흐름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-112">Event handlers also have control flows, which are built using the same kinds of control flow elements.</span></span>

## <a name="control-flow-implementation"></a><span data-ttu-id="fcf5f-113">제어 흐름 구현</span><span class="sxs-lookup"><span data-stu-id="fcf5f-113">Control Flow Implementation</span></span>
 <span data-ttu-id="fcf5f-114">**디자이너의** 제어 흐름 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 탭을 사용하여 패키지의 제어 흐름을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-114">You create the control flow in a package by using the **Control Flow** tab in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="fcf5f-115">**제어 흐름** 탭이 활성화된 경우 제어 흐름에 추가할 수 있는 태스크 및 컨테이너가 도구 상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-115">When the **Control Flow** tab is active, the Toolbox lists the tasks and containers that you can add to the control flow.</span></span>

 <span data-ttu-id="fcf5f-116">다음 다이어그램에서는 제어 흐름 디자이너에서의 간단한 패키지에 대한 제어 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-116">The following diagram shows the control flow of a simple package in the control flow designer.</span></span> <span data-ttu-id="fcf5f-117">다이어그램에 표시된 제어 흐름은 3개의 패키지 수준 태스크와 3개의 태스크가 포함된 한 개의 패키지 수준 컨테이너로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-117">The control flow shown in the diagram is made up of three package-level tasks and one package-level container that contains three tasks.</span></span> <span data-ttu-id="fcf5f-118">태스크와 컨테이너는 선행 제약 조건을 사용하여 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-118">The tasks and container are connected by using precedence constraints.</span></span>

 <span data-ttu-id="fcf5f-119">![패키지가 포함된 제어 흐름 디자이너의 스크린샷](../media/samplecontrolflow.gif "패키지가 포함된 제어 흐름 디자이너의 스크린샷")</span><span class="sxs-lookup"><span data-stu-id="fcf5f-119">![Screenshot of control flow designer with package](../media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

 <span data-ttu-id="fcf5f-120">제어 흐름을 만드는 데에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-120">Creating a control flow includes the following tasks:</span></span>

-   <span data-ttu-id="fcf5f-121">패키지에서 반복되는 워크플로를 구현하거나 제어 흐름을 하위 집합으로 구분하는 컨테이너를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-121">Adding containers that implement repeating workflows in a package or divide a control flow into subsets.</span></span>

-   <span data-ttu-id="fcf5f-122">데이터 흐름을 지원하고, 데이터를 준비하고, 워크플로 및 비즈니스 인텔리전스 기능을 수행하고, 스크립트를 구현하는 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-122">Adding tasks that support data flow, prepare data, perform workflow and business intelligence functions, and implement script.</span></span>

     [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]<span data-ttu-id="fcf5f-123">에는 패키지의 비즈니스 요구 사항을 만족시켜주는 제어 흐름을 만들기 위해 사용할 수 있는 여러 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-123">includes a variety of tasks that you can use to create control flow that meets the business requirements of the package.</span></span> <span data-ttu-id="fcf5f-124">패키지에서 데이터를 사용해야 하는 경우 제어 흐름에는 적어도 하나 이상의 데이터 흐름 태스크가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-124">If the package has to work with data, the control flow must include at least one Data Flow task.</span></span> <span data-ttu-id="fcf5f-125">예를 들어 패키지에서 데이터를 추출하고, 데이터 값을 집계한 다음 결과를 데이터 원본에 기록해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-125">For example, a package might have to extract data, aggregate data values, and then write the results to a data source.</span></span>  <span data-ttu-id="fcf5f-126">자세한 내용은 [Integration Services 태스크](integration-services-tasks.md) 및 [제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](add-or-delete-a-task-or-a-container-in-a-control-flow.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-126">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>

-   <span data-ttu-id="fcf5f-127">선행 제약 조건을 사용하여 컨테이너와 태스크를 정렬된 제어 흐름으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-127">Connecting containers and tasks into an ordered control flow by using precedence constraints.</span></span>

     <span data-ttu-id="fcf5f-128">**제어 흐름** 탭의 디자인 화면에 태스크나 컨테이너를 추가하면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너가 해당 항목에 연결선을 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-128">After you add a task or container to the design surface of the **Control Flow** tab, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically adds a connector to the item.</span></span> <span data-ttu-id="fcf5f-129">패키지에 두 개 이상의 항목, 태스크 또는 컨테이너가 포함된 경우 해당 연결선을 서로 연결하여 이를 하나의 제어 흐름으로 결합시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-129">If a package includes two or more items, tasks or containers, you can join them into a control flow by dragging their connectors from one item to another.</span></span>

     <span data-ttu-id="fcf5f-130">두 항목 간의 연결선을 선행 제약 조건이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-130">The connector between two items represents a precedence constraint.</span></span> <span data-ttu-id="fcf5f-131">선행 제약 조건은 연결된 두 항목 간의 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-131">A precedence constraint defines the relationship between the two connected items.</span></span> <span data-ttu-id="fcf5f-132">선행 제약 조건은 런타임에 태스크 및 컨테이너가 실행되는 순서와 태스크 및 컨테이너가 실행되는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-132">It specifies the order in which tasks and containers are executed at run time and the conditions under which tasks and containers run.</span></span> <span data-ttu-id="fcf5f-133">예를 들어 선행 제약 조건을 사용하면 특정 태스크가 성공해야 제어 흐름의 다음 태스크가 실행되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-133">For example, a precedence constraint can specify that a task must succeed for the next task in the control flow to run.</span></span> <span data-ttu-id="fcf5f-134">자세한 내용은 [Precedence Constraints](precedence-constraints.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-134">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>

-   <span data-ttu-id="fcf5f-135">연결 관리자 추가</span><span class="sxs-lookup"><span data-stu-id="fcf5f-135">Adding connection managers.</span></span>

     <span data-ttu-id="fcf5f-136">대부분의 태스크에는 데이터 원본에 대한 연결이 필요하며, 이를 위해서는 해당 태스크에 필요한 연결 관리자를 패키지에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-136">Many tasks require a connection to a data source, and you have to add the connection managers that the task requires to the package.</span></span> <span data-ttu-id="fcf5f-137">사용되는 열거자 유형에 따라 Foreach 루프 컨테이너에도 연결 관리자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-137">Depending on the enumerator type it uses, the Foreach Loop container may also require a connection manager.</span></span> <span data-ttu-id="fcf5f-138">연결 관리자는 제어 흐름을 항목별로 구성할 때나 제어 흐름 구성을 시작하기 전에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-138">You can add the connection managers as you construct the control flow item by item or before you start to construct the control flow.</span></span> <span data-ttu-id="fcf5f-139">자세한 내용은 [Integration Services&#40;SSIS&#41; 연결](../connection-manager/integration-services-ssis-connections.md) 및 [연결 관리자 만들기](../create-connection-managers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-139">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../create-connection-managers.md).</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="fcf5f-140">디자이너에는 디자인 화면을 관리하고 제어 흐름을 이해하기 쉽게 만드는 데 사용할 수 있는 여러 디자인 타임 기능도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcf5f-140">Designer also includes many design-time features that you can use to manage the design surface and make the control flow self-documenting.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="fcf5f-141">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fcf5f-141">Related Tasks</span></span>

-   [<span data-ttu-id="fcf5f-142">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="fcf5f-142">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)

-   [<span data-ttu-id="fcf5f-143">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="fcf5f-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)

-   [<span data-ttu-id="fcf5f-144">구성 요소 그룹화 또는 그룹 해제</span><span class="sxs-lookup"><span data-stu-id="fcf5f-144">Group or Ungroup Components</span></span>](../group-or-ungroup-components.md)


