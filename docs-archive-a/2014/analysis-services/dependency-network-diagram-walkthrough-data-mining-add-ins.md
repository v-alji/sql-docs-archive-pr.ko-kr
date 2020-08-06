---
title: 종속성 네트워크 다이어그램 연습 (데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07f97dac7ffb0211f0ff1e1b58c2e0792d026174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660195"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="245dc-102">종속성 네트워크 다이어그램 연습(데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="245dc-102">Dependency Network Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="245dc-103">몇 가지 유형의 데이터 마이닝 모델은 데이터에서 관계를 탐색하는 수단으로 네트워크 그래프를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-103">Several different types of data mining models use a network graph as a way of exploring relationships in the data.</span></span> <span data-ttu-id="245dc-104">**종속성 네트워크** 셰이프를 사용 하 여 이러한 모델을 Visio로 가져온 다음 계속 해 서 레이아웃을 사용자 지정 하 고 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-104">You can import these models into Visio using the **Dependency Network** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="245dc-105">**Visio 용 데이터 마이닝 셰이프에** 는 종속성 네트워크 다이어그램을 사용 하기 위한 다음과 같은 사용자 지정 컨트롤이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-105">The **Data Mining Shapes for Visio** include the following custom controls for working with dependency network diagrams:</span></span>  
  
-   <span data-ttu-id="245dc-106">네트워크 그래프의 렌더링 컨트롤</span><span class="sxs-lookup"><span data-stu-id="245dc-106">Rendering controls for the network graph</span></span>  
  
     <span data-ttu-id="245dc-107">이러한 옵션은 Visio 작업 영역에 셰이프를 끌어서 놓을 때 시작되는 마법사의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-107">These options are part of the wizard that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="245dc-108">**데이터 마이닝 레이아웃** 도구 모음</span><span class="sxs-lookup"><span data-stu-id="245dc-108">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="245dc-109">이러한 옵션은 종속성 네트워크 그래프와 상호 작용하는 데 도움이 되도록 Visio 작업 영역에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-109">These options are added to the Visio workspace to help you interact with the dependency network graph.</span></span>  
  
## <a name="build-a-dependency-network-graph"></a><span data-ttu-id="245dc-110">종속성 네트워크 그래프 작성</span><span class="sxs-lookup"><span data-stu-id="245dc-110">Build a Dependency Network Graph</span></span>  
 <span data-ttu-id="245dc-111">셰이프를 Visio 페이지에 끌어 놓아 **종속성 네트워크 Visio 셰이프 마법사** 를 시작 하 고 다이어그램 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-111">You drop a shape onto the Visio page to launch the **Dependency Net Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a><span data-ttu-id="245dc-112">종속성 네트워크 Visio 셰이프 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="245dc-112">Use the Dependency Net Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="245dc-113">**셰이프** 목록에 **Microsoft 데이터 마이닝 셰이프가** 표시 되지 않는 경우 **추가 셰이프**를 클릭 하 고, **스텐실 열기**를 선택 하 고, 기본 설치 위치에서 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-113">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="245dc-114">\<drive>: Filefiles (x85) \Microsoft SQL Server 2012 DM 추가 기능</span><span class="sxs-lookup"><span data-stu-id="245dc-114">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="245dc-115">**종속성 네트워크** 셰이프를 페이지로 끌어 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-115">Drag the **Dependency Network** shape onto the page to start the wizard.</span></span> <span data-ttu-id="245dc-116">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-116">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="245dc-117">**종속성 네트워크 Visio 셰이프 마법사**의 시작 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-117">On the welcome page of the **Dependency Network Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="245dc-118">**종속성 네트워크 Visio 셰이프 마법사**의 **데이터 원본 선택** 페이지에서 시각화할 모델이 있는 서버에 대 한 연결을 선택 합니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="245dc-118">On the **Select a Data Source** page of the **Dependency Network Visio Shape Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="245dc-119">적절 한 마이닝 모델을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-119">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="245dc-120">적절 한 모델을 선택 하기 위해 **속성** 창에서 데이터의 이름, 설명, 열 및 유형을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-120">To select an appropriate model, you can review the name, description, columns, and type of data in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="245dc-121">이 셰이프는 다음 알고리즘을 사용하여 만들어진 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-121">This shape supports models created by using these algorithms:</span></span>  
  
    -   <span data-ttu-id="245dc-122">Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="245dc-122">Naïve Bayes</span></span>  
  
    -   <span data-ttu-id="245dc-123">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="245dc-123">Decision Trees</span></span>  
  
    -   <span data-ttu-id="245dc-124">연결 규칙</span><span class="sxs-lookup"><span data-stu-id="245dc-124">Association Rules</span></span>  
  
6.  <span data-ttu-id="245dc-125">페이지에서 **렌더링할 노드를 선택**하 고, 그래프 크기를 사용자 지정 하 고, 필요에 따라 특정 노드만 포함 하도록 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-125">On the page, **Select Nodes to Render**, customize the size of the graph, and optionally filter to only include certain nodes.</span></span>  
  
     <span data-ttu-id="245dc-126">큰 데이터 집합을 사용 하면 종속성 그래프가 크게 커지고 *노드로*표현 되는 여러 관련 개체를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-126">With a large dataset, a dependency graph can become huge, and contain many related objects, represented as *nodes*.</span></span> <span data-ttu-id="245dc-127">이 대화 상자를 사용하여 관심 있는 노드만 포함된 사용자 지정 네트워크 그래프를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-127">By using this dialog box, you can create a custom network graph that includes only the nodes of interest.</span></span>  
  
     <span data-ttu-id="245dc-128">[아트 자리 표시자]</span><span class="sxs-lookup"><span data-stu-id="245dc-128">[art placeholder]</span></span>  
  
     <span data-ttu-id="245dc-129">**인출할 노드 수**</span><span class="sxs-lookup"><span data-stu-id="245dc-129">**Number of nodes to fetch**</span></span>  
     <span data-ttu-id="245dc-130">모델에 포함된 노드보다 큰 수를 지정하면 이 설정은 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-130">If the model contains fewer than the specified number of nodes, this setting has no effect.</span></span> <span data-ttu-id="245dc-131">모델에 포함된 노드보다 작은 수를 지정하는 경우에는 가장 강력한 노드만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-131">If the model contains more nodes than the specified number, only the strongest nodes are displayed.</span></span>  
  
     <span data-ttu-id="245dc-132">**포함 문자**</span><span class="sxs-lookup"><span data-stu-id="245dc-132">**Name contains**</span></span>  
     <span data-ttu-id="245dc-133">모델에 있는 모든 노드를 검색하려면 이 입력란을 비워 두고 녹색 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-133">Leave this box blank and click the green arrow to retrieve all nodes in the model.</span></span>  
  
     <span data-ttu-id="245dc-134">또는 지정한 문자열을 포함하는 노드만 반환되게 하려면 문자열을 입력하고 녹색 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-134">Or, type a string and click the green arrow to return only those nodes that contain the specified string.</span></span>  
  
     <span data-ttu-id="245dc-135">예제 데이터로 만들 수 있는 대부분의 모델은 크지 않으므로 이 예의 경우 노드 수를 10개로 늘린 다음 녹색 화살표를 클릭하여 쿼리를 실행하고 모든 노드의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-135">Most of the models that you can create with the sample data are not big, so for this example, increase the number of nodes to 10, and then click the green arrow to run a query and get the list of all nodes.</span></span>  
  
7.  <span data-ttu-id="245dc-136">**고급** 을 클릭 하 여 그래프의 음영 및 셰이프 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-136">Click **Advanced** to set shading and shape options for the graph.</span></span>  
  
8.  <span data-ttu-id="245dc-137">**닫기** 를 클릭 하 여 **고급** 옵션 대화 상자를 종료 한 다음 **마침** 을 클릭 하 여 그래프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-137">Click **Close** to exit the **Advanced** options dialog box, and then click **Finish** to create the graph.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="245dc-138">완성된 다이어그램 탐색 및 수정</span><span class="sxs-lookup"><span data-stu-id="245dc-138">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="245dc-139">Visio에서 네트워크 종속성 그래프를 만든 후 Visio의 기능을 사용하여 계속해서 그래프를 수정하고 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-139">After Visio has created the network dependency graph, you can continue to modify and enhance the graph by using the features in Visio.</span></span>  
  
 <span data-ttu-id="245dc-140">종속성 네트워크 그래프의 기본 레이아웃은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-140">The following graphic shows the default layout of a dependency network graph.</span></span>  
  
 <span data-ttu-id="245dc-141">[아트 자리 표시자]</span><span class="sxs-lookup"><span data-stu-id="245dc-141">[art placeholder]</span></span>  
  
1.  <span data-ttu-id="245dc-142">Visio **뷰** 리본의 **작업 창** 영역에서 **팬 및 확대/축소** 컨트롤을 사용 하 여 그래프의 특정 부분에 초점을 맞춘 후 다이어그램 주위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-142">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a section of the graph and move around the diagram.</span></span>  
  
2.  <span data-ttu-id="245dc-143">Visio **레이아웃 다시 사용 페이지** 옵션에서 제공 하는 다양 한 그래프 레이아웃을 시험해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-143">Experiment with different graph layouts provided by the Visio **Re-Layout Page** option.</span></span>  
  
3.  <span data-ttu-id="245dc-144">**추가 기능** 리본을 클릭 한 다음 데이터 마이닝 다이어그램 작업에 사용 되는 사용자 지정 도구 모음 중 하나를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-144">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="245dc-145">**레이아웃**</span><span class="sxs-lookup"><span data-stu-id="245dc-145">**Layout**</span></span>  
     <span data-ttu-id="245dc-146">페이지의 노드 레이아웃을 최적화하고 모든 노드가 표시되도록 보기를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-146">Optimizes the layout of nodes on the page, and changes the view so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="245dc-147">**페이지 크기 조정**</span><span class="sxs-lookup"><span data-stu-id="245dc-147">**Resize Page**</span></span>  
     <span data-ttu-id="245dc-148">모든 노드가 표시되도록 페이지의 크기를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-148">Changes the size of the page so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="245dc-149">**가장자리 수준**</span><span class="sxs-lookup"><span data-stu-id="245dc-149">**Edge Strength**</span></span>  
     <span data-ttu-id="245dc-150">전체 그래프에 대한 가장자리 수준 표시를 설정/해제합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-150">Toggles display of edge strength for the entire graph.</span></span> <span data-ttu-id="245dc-151">가장자리는 노드 간 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-151">An edge is a connection between nodes.</span></span> <span data-ttu-id="245dc-152">슬라이더 컨트롤을 사용하여 강력하지 않은 연결을 필터링으로 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-152">You can use the slider control to filter out connections that are not strong.</span></span>  
  
     <span data-ttu-id="245dc-153">**슬라이더**</span><span class="sxs-lookup"><span data-stu-id="245dc-153">**Slider**</span></span>  
     <span data-ttu-id="245dc-154">**슬라이더** 를 사용 하 여 종속성 네트워크 다이어그램에 표시 되는 관계의 강도를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-154">The **Slider** helps you control the strength of the relationships that are displayed in the dependency network diagram.</span></span>  
  
     <span data-ttu-id="245dc-155">그래프의 각 노드는 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-155">Each node in the graph represents a state.</span></span> <span data-ttu-id="245dc-156">화살표는 두 상태 간의 전환 및 이 전환과 관련된 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-156">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="245dc-157">그래프의 노드 수를 줄이려면 슬라이더 막대를 위로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-157">To reduce the number of nodes in the graph, move the slider bar up.</span></span>  
  
     <span data-ttu-id="245dc-158">그래프의 노드 수를 늘리려면 슬라이더 막대를 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-158">To increase the number of nodes in the graph, move the slider bar down.</span></span>  
  
     <span data-ttu-id="245dc-159">**항목 추가**</span><span class="sxs-lookup"><span data-stu-id="245dc-159">**Add Items**</span></span>  
     <span data-ttu-id="245dc-160">그래프에 추가할 새 노드를 선택할 수 있도록 **렌더링할 노드 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-160">Opens the **Select Nodes to Render** dialog box so that you can select new nodes to add to the graph.</span></span>  
  
4.  <span data-ttu-id="245dc-161">모델에 연결되어 있는 동안 그래프를 원하는 대로 간단하거나 복잡하게 만들고 주석을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-161">You can make the graphs as simple or elaborate as you like, and add annotations, while staying connected to the model.</span></span>  
  
     <span data-ttu-id="245dc-162">[아트 자리 표시자]</span><span class="sxs-lookup"><span data-stu-id="245dc-162">[ art placeholder]</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="245dc-163">이전 버전의 추가 기능에서 사용할 수 있었던 종속 노드의 강조 표시 및 기타 바로 가기 메뉴 옵션은 Office 2013에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="245dc-163">Highlighting of dependent nodes and other shortcut menu options that were available in previous versions of the Add-Ins do not work in Office 2013.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245dc-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="245dc-164">See Also</span></span>  
 [<span data-ttu-id="245dc-165">Visio 데이터 마이닝 다이어그램 문제 해결 SQL Server 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="245dc-165">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
