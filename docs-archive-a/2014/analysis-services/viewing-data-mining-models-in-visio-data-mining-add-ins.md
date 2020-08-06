---
title: Visio에서 데이터 마이닝 모델 보기 (데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3c1e63c058295b93e2562c64a6df90a30273a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649192"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a><span data-ttu-id="cf599-102">Visio에서 데이터 마이닝 모델 보기(데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="cf599-102">Viewing Data Mining Models in Visio (Data Mining Add-ins)</span></span>
  <span data-ttu-id="cf599-103">데이터 마이닝용 Visio 셰이프를 사용하여 서버에 연결하고 기존 데이터 마이닝 모델을 나타내는 다이어그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-103">The Visio shapes for data mining let you connect to a server and create a diagram representing an existing data mining model.</span></span> <span data-ttu-id="cf599-104">그런 다음 Visio 컨트롤을 사용하여 다이어그램을 사용자 지정할 수 있지만, 데이터로 드릴다운하고, 일부 기본 통계를 노출하고, 기본 모델을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-104">The diagrams can then be customized using Visio controls, but you can also drill down into data, expose some of the underlying statistics, and work with the underlying model.</span></span>  
  
## <a name="building-a-model-diagram"></a><span data-ttu-id="cf599-105">모델 다이어그램 작성</span><span class="sxs-lookup"><span data-stu-id="cf599-105">Building a Model Diagram</span></span>  
 <span data-ttu-id="cf599-106">데이터 마이닝용 Visio 셰이프를 포함 하는 파일을 열면 **셰이프** 창에 다음과 같은 모양이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-106">When you open the file containing the Visio shapes for data mining, the **Shapes** pane shows the following shapes.</span></span>  
  
 <span data-ttu-id="cf599-107">Visio를 열 때 데이터 마이닝 셰이프가 표시되지 않으면 설치 폴더에서 템플릿 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-107">If you do not see the data mining shapes when you open Visio, open the template file from the installation folder.</span></span>  
  
 <span data-ttu-id="cf599-108">![DM](media/dm-stencil.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="cf599-108">![DM](media/dm-stencil.gif "DM")</span></span>  
  
 <span data-ttu-id="cf599-109">셰이프를 사용하려면 셰이프를 페이지로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-109">To use a shape, drag it to the page.</span></span> <span data-ttu-id="cf599-110">각 셰이프에 대해 원본 데이터 선택, 특정 다이어그램 유형에 대한 옵션 설정, 음영 및 다른 표시 옵션 지정을 돕는 다른 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-110">Each of the shapes opens a different wizard, which helps you select source data, set options for the specific diagram type, and specify shading and other display options.</span></span>  
  
 <span data-ttu-id="cf599-111">다음 표에는 각 다이어그램 유형에 사용할 수 있는 모델 유형이 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-111">The following table lists the types of models that you can use with each type of diagram.</span></span>  
  
|<span data-ttu-id="cf599-112">Visio 셰이프</span><span class="sxs-lookup"><span data-stu-id="cf599-112">Visio shape</span></span>|<span data-ttu-id="cf599-113">지원되는 모델</span><span class="sxs-lookup"><span data-stu-id="cf599-113">Supported models</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="cf599-114">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="cf599-114">Decision Tree</span></span>|<span data-ttu-id="cf599-115">의사 결정 트리 또는 선형 회귀 알고리즘을 기반으로 하는 모델에 이 셰이프를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-115">Use this shape for models based on the decision tree or linear regression algorithms.</span></span>|  
|<span data-ttu-id="cf599-116">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="cf599-116">Dependency Network</span></span>|<span data-ttu-id="cf599-117">Naive Bayes, 의사 결정 트리 또는 연결 규칙 알고리즘을 기반으로 하는 모델에이 셰이프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-117">Use this shape for models based on any of the following algorithms: Naive Bayes, Decision Trees, or Association Rules.</span></span>|  
|<span data-ttu-id="cf599-118">클러스터</span><span class="sxs-lookup"><span data-stu-id="cf599-118">Cluster</span></span>|<span data-ttu-id="cf599-119">클러스터링 알고리즘을 기반으로 하는 모델에 이 셰이프를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-119">Use this shape for models based on clustering algorithms.</span></span>|  
  
 <span data-ttu-id="cf599-120">마이닝 모델의 데이터 형식에 따라 마법사에서 제공하는 옵션이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-120">Depending on the type of data in your mining model, the wizard may offer different options.</span></span> <span data-ttu-id="cf599-121">예를 들어, 연속 숫자를 포함하는 열은 범주 변수를 포함하는 열과 다르게 시각화됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-121">For example, columns that contain continuous numbers are visualized differently than categorical variables.</span></span>  
  
## <a name="working-with-completed-shapes"></a><span data-ttu-id="cf599-122">완성된 셰이프 사용</span><span class="sxs-lookup"><span data-stu-id="cf599-122">Working with Completed Shapes</span></span>  
 <span data-ttu-id="cf599-123">다이어그램이 완료되면 이 다이어그램을 사용하여 데이터 마이닝 모델을 탐색하거나 프레젠테이션에 맞게 다이어그램을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-123">After the diagram is complete, you can use it to browse the data mining model or enhance the diagram for use in presentations.</span></span>  
  
### <a name="visio-menus"></a><span data-ttu-id="cf599-124">Visio 메뉴</span><span class="sxs-lookup"><span data-stu-id="cf599-124">Visio Menus</span></span>  
 <span data-ttu-id="cf599-125">Visio는 다이어그램 향상을 위한 다양한 렌더링 컨트롤, 테마 및 바로 가기 메뉴를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-125">Visio provides a variety of rendering controls, themes, and shortcut menus to help enhance a diagram.</span></span>  
  
-   <span data-ttu-id="cf599-126">Visio 테마를 사용하여 다이어그램 색을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-126">Use Visio themes to alter diagram colors.</span></span>  
  
-   <span data-ttu-id="cf599-127">커넥터 또는 다이어그램 레이아웃을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-127">Change connectors or diagram layout.</span></span>  
  
### <a name="data-mining-menus"></a><span data-ttu-id="cf599-128">데이터 마이닝 메뉴</span><span class="sxs-lookup"><span data-stu-id="cf599-128">Data Mining Menus</span></span>  
 <span data-ttu-id="cf599-129">이들 도구 모음과 메뉴 항목은 각 셰이프나 모델 형식과 관련된 추가 기능에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-129">These toolbars and menu items are provided by the add-ins that are specific to each shape or model type</span></span>  
  
-   <span data-ttu-id="cf599-130">각 다이어그램 유형에는 특수 옵션에 액세스할 수 있도록 지원하는 셰이프에 대한 바로 가기 메뉴가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-130">Each diagram type has a shortcut menu for the shape that lets you access special options.</span></span> <span data-ttu-id="cf599-131">이 메뉴의 많은 옵션이 모든 Visio 셰이프에 공통적인 것이지만 일부 옵션은 데이터 마이닝 템플릿에 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-131">Although many options in this menu are common to all Visio shapes, some options are unique to the data mining templates</span></span>  
  
     <span data-ttu-id="cf599-132">예를 들어 의사 결정 트리 다이어그램에서 개별 노드를 클릭하고 자식 노드를 축소하여 다이어그램을 더 단순하게 만들거나 자식 노드를 별도 페이지로 옮길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-132">For example, in a decision tree diagram, you can click an individual node and then collapse the child nodes to make the diagram simpler, or move child nodes to a separate page.</span></span>  
  
-   <span data-ttu-id="cf599-133">모델 데이터에 셰이프가 바인딩되기 때문에 다이어그램을 통한 탐색도 어느 정도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-133">Because the shape is bound to the model data, you can also do some amount of exploration using the diagram:</span></span>  
  
     <span data-ttu-id="cf599-134">표시되는 노드를 필터링하거나 트리 수준 또는 그래프 깊이를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cf599-134">Filter the nodes that are displayed, or change the level of the tree or depth of the graph.</span></span>  
  
     <span data-ttu-id="cf599-135">특정 섹션을 확대하고 특정 특성이 포함된 노드를 검색하거나 가장자리별로 종속성 그래프를 필터링합니다(확률).</span><span class="sxs-lookup"><span data-stu-id="cf599-135">Zoom in on specific sections, search for nodes that contain a certain attribute, or filter a dependency graph by its edges (probability).</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="cf599-136">연습</span><span class="sxs-lookup"><span data-stu-id="cf599-136">Walkthroughs</span></span>  
 <span data-ttu-id="cf599-137">완료된 다이어그램에서 작업하거나 해석하는 방법에 대한 예는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf599-137">For examples of how to work with and interpret a completed diagram, see these topics:</span></span>  
  
 [<span data-ttu-id="cf599-138">클러스터 다이어그램 연습</span><span class="sxs-lookup"><span data-stu-id="cf599-138">Cluster Diagram Walkthrough</span></span>](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="cf599-139">종속성 네트워크 다이어그램 연습</span><span class="sxs-lookup"><span data-stu-id="cf599-139">Dependency Net Diagram Walkthrough</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="cf599-140">의사 결정 트리 다이어그램 연습</span><span class="sxs-lookup"><span data-stu-id="cf599-140">Decision Tree Diagram Walkthrough</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf599-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf599-141">See Also</span></span>  
 [<span data-ttu-id="cf599-142">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="cf599-142">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
