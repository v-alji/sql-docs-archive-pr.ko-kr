---
title: 의사 결정 트리 다이어그램 연습 (데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: bbe54db1ab3d00d074917db770a9a731f884f49a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649814"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a><span data-ttu-id="a34cb-102">의사 결정 트리 다이어그램 연습 (데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="a34cb-102">Decision Tree Diagram Walkthrough  (Data Mining Add-ins)</span></span>
  <span data-ttu-id="a34cb-103">의사 결정 트리 모델을 만든 경우 의사 결정 트리 셰이프 또는 종속성 네트워크 셰이프를 사용하여 Visio에서 사용자 지정된 다이어그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-103">If you have created a decision tree model, you can create a customized diagram in Visio by using either the Decision Tree shape or the Dependency Network shape.</span></span> <span data-ttu-id="a34cb-104">이 항목에서는 **의사 결정 트리** 셰이프 및 다음 컨트롤을 사용 하 여 수행할 수 있는 사용자 지정에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-104">This topic describes the customizations you can perform using the **Decision Tree** shape and these controls:</span></span>  
  
-   <span data-ttu-id="a34cb-105">의사 결정 트리 다이어그램의 렌더링 컨트롤</span><span class="sxs-lookup"><span data-stu-id="a34cb-105">Rendering controls for the decision tree diagram</span></span>  
  
     <span data-ttu-id="a34cb-106">이러한 옵션은 Visio 작업 영역에 셰이프를 놓을 때 시작 되는 **의사 결정 트리 마법사** 의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-106">These options are part of the **Decision Tree Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="a34cb-107">**데이터 마이닝 레이아웃** 도구 모음</span><span class="sxs-lookup"><span data-stu-id="a34cb-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="a34cb-108">이러한 옵션은 셰이프와 상호 작용하는 데 도움이 되도록 Visio 작업 영역에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-108">These options are added to the Visio workspace to help you interact with the shape.</span></span>  
  
## <a name="build-a-decision-tree-diagram"></a><span data-ttu-id="a34cb-109">의사 결정 트리 다이어그램 작성</span><span class="sxs-lookup"><span data-stu-id="a34cb-109">Build a Decision Tree Diagram</span></span>  
 <span data-ttu-id="a34cb-110">의사 결정 트리 셰이프를 Visio 페이지에 끌어 놓고 **의사 결정 트리 Visio 셰이프 마법사** 를 시작 하 고 다이어그램 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-110">You drop the Decision Tree shape onto the Visio page to launch the **Decision Tree Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-decision-tree-wizard"></a><span data-ttu-id="a34cb-111">의사 결정 트리 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="a34cb-111">Use the Decision Tree Wizard</span></span>  
  
1.  <span data-ttu-id="a34cb-112">**셰이프** 목록에 **Microsoft 데이터 마이닝 셰이프가** 표시 되지 않는 경우 **추가 셰이프**를 클릭 하 고, **스텐실 열기**를 선택 하 고, 기본 설치 위치에서 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-112">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="a34cb-113">\<drive>: Filefiles (x85) \Microsoft SQL Server 2012 DM 추가 기능</span><span class="sxs-lookup"><span data-stu-id="a34cb-113">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="a34cb-114">**의사 결정 트리** 셰이프를 페이지로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-114">Drag the **Decision Tree** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="a34cb-115">**의사 결정 트리 Visio 셰이프 마법사**의 시작 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-115">On the welcome page of the **Decision Tree Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="a34cb-116">**클러스터 마법사**의 **데이터 원본 선택** 페이지에서 시각화할 모델이 있는 서버에 대 한 연결을 선택 합니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a34cb-116">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="a34cb-117">적절 한 마이닝 모델을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-117">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="a34cb-118">이 다이어그램 유형은 의사 결정 트리 또는 선형 회귀 알고리즘을 사용하여 만들어진 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-118">This diagram type supports models created using the Decision Trees or Linear Regression algorithm.</span></span>  
  
6.  <span data-ttu-id="a34cb-119">**의사 결정 트리 선택** 페이지에서 표시할 개별 트리를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-119">On the **Select Decision Tree** page, choose an individual tree to display.</span></span>  
  
     <span data-ttu-id="a34cb-120">트리는 모델링 한 특정 결과로 이어질 수 있는 상호 작용을 모델링 합니다. 따라서 모델에 여러 결과가 포함 된 경우에도 한 번에 하나의 트리만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-120">A tree models the interactions that lead to a particular outcome you've modeled; therefore, even if your model contains multiple outcomes, you can display only one tree at a time.</span></span>  
  
7.  <span data-ttu-id="a34cb-121">**의사 결정 트리 선택** 대화 상자에서 다음과 같은 렌더링 옵션을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-121">In the **Select Decision Tree** dialog box, you can also set these rendering options:</span></span>  
  
     <span data-ttu-id="a34cb-122">**최대 렌더링 깊이**</span><span class="sxs-lookup"><span data-stu-id="a34cb-122">**Maximum Rendering Depth**</span></span>  
     <span data-ttu-id="a34cb-123">표시되는 노드 수를 제어하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-123">Use this option to control how many nodes are displayed.</span></span>  
  
     <span data-ttu-id="a34cb-124">의사 결정 트리가 매우 깊어서 페이지에 맞지 않는 다이어그램이 만들어질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-124">A decision tree might go very deep, creating a diagram that does not fit on the page.</span></span> <span data-ttu-id="a34cb-125">보다 중요한 가장 왼쪽의 노드에 초점을 맞추려면 이 컨트롤을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-125">Use this control to focus on the leftmost nodes, which are more important.</span></span>  
  
     <span data-ttu-id="a34cb-126">기본값은 세 수준의 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-126">The default is three levels of nodes.</span></span>  
  
     <span data-ttu-id="a34cb-127">**값의 색 및 표시 텍스트 선택**</span><span class="sxs-lookup"><span data-stu-id="a34cb-127">**Select color and display text for values**</span></span>  
     <span data-ttu-id="a34cb-128">결과를 각각 나타낼 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-128">Choose the color that will represent each one of the outcomes.</span></span> <span data-ttu-id="a34cb-129">색을 지정하지 않으면 현재 비디오 테마 색을 사용하여 색이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-129">If you do not specify colors, they are automatically generated using the current video theme colors.</span></span>  
  
8.  <span data-ttu-id="a34cb-130">**고급** 을 클릭 하 여 의사 결정 트리 다이어그램의 각 노드에 대해 다음 옵션을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-130">Click **Advanced** to customize the following options for each of the nodes in the decision tree diagram.</span></span>  
  
     <span data-ttu-id="a34cb-131">**음영 변수** 및 **상태**</span><span class="sxs-lookup"><span data-stu-id="a34cb-131">**Shading Variable** and **State**</span></span>  
     <span data-ttu-id="a34cb-132">트리 다이어그램에 표시하려는 대상 결과를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-132">Choose the target outcome that you want to show in the tree diagram.</span></span>  
  
     <span data-ttu-id="a34cb-133">**히스토그램 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-133">**Show Histogram**</span></span>  
     <span data-ttu-id="a34cb-134">해당 노드를 정의하는 규칙을 표시하는 차트를 각 노드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-134">Adds a chart to each node that shows the rules that define that node.</span></span>  
  
     <span data-ttu-id="a34cb-135">**레이블 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-135">**Show Label**</span></span>  
     <span data-ttu-id="a34cb-136">히스토그램에 열 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-136">Adds column names to the histogram.</span></span>  
  
     <span data-ttu-id="a34cb-137">**확률 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-137">**Show Probability**</span></span>  
     <span data-ttu-id="a34cb-138">각 값의 확률을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-138">Displays the probability of each value.</span></span>  
  
     <span data-ttu-id="a34cb-139">**지지도 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-139">**Show Support**</span></span>  
     <span data-ttu-id="a34cb-140">각 값에 대한 지지도를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-140">Displays the support for each value.</span></span>  
  
     <span data-ttu-id="a34cb-141">**바닥글 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-141">**Show Footer**</span></span>  
     <span data-ttu-id="a34cb-142">모든 표시된 값을 요약하는 바닥글을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-142">Adds a footer that sums all displayed values.</span></span>  
  
     <span data-ttu-id="a34cb-143">**머리글 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-143">**Show Header**</span></span>  
     <span data-ttu-id="a34cb-144">열 머리글을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-144">Adds column headings.</span></span>  
  
     <span data-ttu-id="a34cb-145">**지지도가 없는 상태 표시**</span><span class="sxs-lookup"><span data-stu-id="a34cb-145">**Show states with zero support**</span></span>  
     <span data-ttu-id="a34cb-146">누락 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-146">Lets you display missing values.</span></span>  
  
9. <span data-ttu-id="a34cb-147">**마침** 을 클릭 하 여 그래프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-147">Click **Finish** to create the graph.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="a34cb-148">일부 환경에서는 차트의 연결선이 Office 2013에서 렌더링되지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-148">In some environments, connectors in the chart might fail to render in Office 2013.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="a34cb-149">완성된 다이어그램 탐색 및 수정</span><span class="sxs-lookup"><span data-stu-id="a34cb-149">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="a34cb-150">**의사 결정 트리 Visio 셰이프 마법사**를 완료 하면 visio는 예측 된 결과로 이어질 수 있는 규칙을 그래픽으로 표시 하는 트리 다이어그램을 페이지에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-150">After you have completed the **Decision Tree Visio Shape Wizard**, Visio creates a tree diagram on the page that graphically displays the rules that lead to the predicted outcome.</span></span>  
  
 <span data-ttu-id="a34cb-151">의사 결정 트리 다이어그램의 다음 컨트롤을 사용하여 셰이프를 계속 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-151">You can continue to modify the shape by using the following controls for decision tree diagrams:</span></span>  
  
#### <a name="using-the-decision-tree-option-menus"></a><span data-ttu-id="a34cb-152">의사 결정 트리 옵션 메뉴 사용</span><span class="sxs-lookup"><span data-stu-id="a34cb-152">Using the decision tree option menus</span></span>  
  
1.  <span data-ttu-id="a34cb-153">**추가 기능** 리본을 클릭 한 다음 데이터 마이닝 다이어그램 작업에 사용 되는 사용자 지정 도구 모음 중 하나를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-153">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="a34cb-154">**레이아웃**</span><span class="sxs-lookup"><span data-stu-id="a34cb-154">**Layout**</span></span>  
     <span data-ttu-id="a34cb-155">현재 페이지에 맞도록 트리의 정렬을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-155">Optimizes the arrangement of the tree to fit the current page.</span></span>  
  
     <span data-ttu-id="a34cb-156">**페이지 크기 조정**</span><span class="sxs-lookup"><span data-stu-id="a34cb-156">**Resize Page**</span></span>  
     <span data-ttu-id="a34cb-157">이 컨트롤은 이전 HTML 버전용입니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-157">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="a34cb-158">Visio 페이지 크기 조정 컨트롤을 대신 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="a34cb-158">Use the Visio page resizing controls instead,</span></span>  
  
     <span data-ttu-id="a34cb-159">**설명**</span><span class="sxs-lookup"><span data-stu-id="a34cb-159">**Description**</span></span>  
     <span data-ttu-id="a34cb-160">트리의 노드가 선택된 경우 노드의 사례에 대한 세부 정보를 표시하려면 이 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-160">When a node of the tree is selected, click this option to display details about the cases in the node.</span></span>  
  
2.  <span data-ttu-id="a34cb-161">Visio **디자인** 리본의 **레이아웃 다시 레이아웃** 옵션을 사용 하 여 다른 트리 레이아웃을 시험해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-161">Use the **Re-Layout Page** option in the Visio **Design** ribbon to experiment with different tree layouts.</span></span>  
  
3.  <span data-ttu-id="a34cb-162">**디자인** 탭에서 **연결선** 옵션을 사용 하 여 트리의 노드 간에 사용 되는 커넥터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-162">Use the **Connectors** option on the **Design** tab to change the connectors used between nodes in the tree.</span></span>  
  
4.  <span data-ttu-id="a34cb-163">Visio **뷰** 리본의 **작업 창** 영역에서 **팬 및 확대/축소** 컨트롤을 사용 하 여 다이어그램의 특정 영역에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-163">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a particular area of the diagram.</span></span>  
  
5.  <span data-ttu-id="a34cb-164">트리에서 아무 노드나 마우스 오른쪽 단추로 클릭하고 의사 결정 트리 다이어그램과 관련된 다음 바로 가기 메뉴 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-164">Right-click any node in the tree, and choose from these shortcut menu options specific to decision tree diagrams:</span></span>  
  
     <span data-ttu-id="a34cb-165">**페이지 레이아웃 개선**</span><span class="sxs-lookup"><span data-stu-id="a34cb-165">**Improve Page Layout**</span></span>  
     <span data-ttu-id="a34cb-166">페이지에 노드를 고르게 배치하고 모든 노드가 표시되도록 페이지 보기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-166">Distributes the nodes evenly on the page and adjusts the page view to see all nodes.</span></span>  
  
     <span data-ttu-id="a34cb-167">**새 페이지로 자식 노드 이동**</span><span class="sxs-lookup"><span data-stu-id="a34cb-167">**Move Children to New Page**</span></span>  
     <span data-ttu-id="a34cb-168">현재 선택한 노드의 자식 노드를 새 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-168">Moves the children of the currently selected node to a new page.</span></span>  
  
     <span data-ttu-id="a34cb-169">**자식 노드 축소**</span><span class="sxs-lookup"><span data-stu-id="a34cb-169">**Collapse Child Nodes**</span></span>  
     <span data-ttu-id="a34cb-170">현재 선택한 노드의 자식 노드를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-170">Hides the children of the currently selected node.</span></span>  
  
     <span data-ttu-id="a34cb-171">**자식 노드 확장**</span><span class="sxs-lookup"><span data-stu-id="a34cb-171">**Expand Child Nodes**</span></span>  
     <span data-ttu-id="a34cb-172">현재 선택한 노드의 자식 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a34cb-172">Displays the children of the currently selected node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34cb-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a34cb-173">See Also</span></span>  
 [<span data-ttu-id="a34cb-174">Visio 데이터 마이닝 다이어그램 문제 해결 SQL Server 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="a34cb-174">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
