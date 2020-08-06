---
title: Microsoft 트리 뷰어를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Tree Viewer [Analysis Services]
- predictions [Analysis Services], discrete attributes
- mining model content, viewing
- predictions [Analysis Services], continuous attributes
- mining legend [Analysis Services]
- discrete attributes [Analysis Services]
- Microsoft Decision Trees algorithm [Analysis Services]
- decision tree algorithms [Analysis Services]
- Microsoft Tree Viewer
- decision trees [Analysis Services]
- dependencies [Analysis Services]
- continuous attributes
ms.assetid: 0c96d518-ed20-40b7-8d62-b26ad6244287
author: minewiskan
ms.author: owend
ms.openlocfilehash: cebe1e05435fad453757b4f747ae809f379c410f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661446"
---
# <a name="browse-a-model-using-the-microsoft-tree-viewer"></a><span data-ttu-id="0690a-102">Microsoft 트리 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="0690a-102">Browse a Model Using the Microsoft Tree Viewer</span></span>
  <span data-ttu-id="0690a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 트리 뷰어는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 사용 하 여 작성 된 의사 결정 트리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays decision trees that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="0690a-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 알고리즘은 분류와 회귀를 둘 다 지원하는 하이브리드 의사 결정 트리 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is a hybrid decision tree algorithm that supports both classification and regression.</span></span> <span data-ttu-id="0690a-105">따라서 이 뷰어를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 선형 회귀 알고리즘을 기반으로 모델을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-105">Therefore, you can also use this viewer to view models based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="0690a-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘은 불연속 및 연속 특성 모두의 예측 모델링에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-106">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is used for predictive modeling of both discrete and continuous attributes.</span></span> <span data-ttu-id="0690a-107">이 알고리즘에 대한 자세한 내용은 [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0690a-107">For more information about this algorithm, see [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0690a-108">발견된 패턴 및 모델에 사용된 수식에 대한 자세한 정보를 보려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0690a-108">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="0690a-109">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) 또는 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0690a-109">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_TabsPanes"></a><span data-ttu-id="0690a-110">뷰어 탭</span><span class="sxs-lookup"><span data-stu-id="0690a-110">Viewer Tabs</span></span>  
 <span data-ttu-id="0690a-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 찾으면 해당 모델의 적절한 뷰어에서 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 해당 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="0690a-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 트리 뷰어에는 다음과 같은 탭과 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer includes the following tabs and panes:</span></span>  
  
-   [<span data-ttu-id="0690a-113">Decision Tree</span><span class="sxs-lookup"><span data-stu-id="0690a-113">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="0690a-114">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0690a-114">Dependency Network</span></span>](#BKMK_DependencyNetwork)  
  
-   [<span data-ttu-id="0690a-115">마이닝 범례</span><span class="sxs-lookup"><span data-stu-id="0690a-115">Mining Legend</span></span>](#BKMK_MiningLegend)  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="0690a-116">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="0690a-116">Decision Tree</span></span>  
 <span data-ttu-id="0690a-117">의사 결정 트리 모델을 생성할 때 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 예측 가능한 각 특성에 대해 별도의 트리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-117">When you build a decision tree model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds a separate tree for each predictable attribute.</span></span> <span data-ttu-id="0690a-118">뷰어의 **의사 결정 트리** 탭에 있는 **트리** 목록에서 개별 트리를 선택하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-118">You can view an individual tree by selecting it from the **Tree** list on the **Decision Tree** tab of the viewer.</span></span>  
  
 <span data-ttu-id="0690a-119">의사 결정 트리는 일련의 분할로 구성되며 알고리즘의 결정에 따라 가장 중요한 분할이 **모두** 노드의 뷰어 왼쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-119">A decision tree is composed of a series of splits, with the most important split, as determined by the algorithm, at the left of the viewer in the **All** node.</span></span> <span data-ttu-id="0690a-120">추가 분할은 오른쪽에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-120">Additional splits occur to the right.</span></span> <span data-ttu-id="0690a-121">**모두** 노드의 분할은 데이터 세트에서 분할을 유발하는 가장 큰 조건을 포함하므로 가장 중요하며, 이로 인해 첫 번째 분할이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-121">The split in the **All** node is most important because it contains the strongest split-causing conditional in the dataset, and therefore it caused the first split.</span></span>  
  
 <span data-ttu-id="0690a-122">트리의 개별 노드를 확장하거나 축소하여 각 노드 다음에 발생하는 분할을 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-122">You can expand or collapse individual nodes in the tree to show or hide the splits that occur after each node.</span></span> <span data-ttu-id="0690a-123">**의사 결정 트리** 탭의 옵션을 사용하여 트리 표시 방법을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-123">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed.</span></span> <span data-ttu-id="0690a-124">**수준 표시** 슬라이더를 사용하여 트리에 표시되는 수준의 개수를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-124">Use the **Show Level** slider to adjust the number of levels that are shown in the tree.</span></span> <span data-ttu-id="0690a-125">**기본 확장** 을 사용하여 모델의 모든 트리에 표시되는 기본 수준 개수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-125">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
#### <a name="predicting-discrete-attributes"></a><span data-ttu-id="0690a-126">불연속 특성 예측</span><span class="sxs-lookup"><span data-stu-id="0690a-126">Predicting Discrete Attributes</span></span>  
 <span data-ttu-id="0690a-127">예측 가능한 불연속 특성을 사용하여 트리를 작성할 때 뷰어는 트리의 각 노드에 대해 다음을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-127">When a tree is built with a discrete predictable attribute, the viewer displays the following on each node in the tree:</span></span>  
  
-   <span data-ttu-id="0690a-128">분할 발생 조건</span><span class="sxs-lookup"><span data-stu-id="0690a-128">The condition that caused the split.</span></span>  
  
-   <span data-ttu-id="0690a-129">인기도 순서로 예측 가능한 특성의 상태 분포를 나타내는 히스토그램</span><span class="sxs-lookup"><span data-stu-id="0690a-129">A histogram that represents the distribution of the states of the predictable attribute, ordered by popularity.</span></span>  
  
 <span data-ttu-id="0690a-130">**히스토그램** 옵션을 사용하여 트리의 히스토그램에 나타나는 상태 수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-130">You can use the **Histogram** option to change the number of states that appear in the histograms in the tree.</span></span> <span data-ttu-id="0690a-131">이 옵션은 예측 가능한 특성에 많은 상태가 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-131">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="0690a-132">상태는 왼쪽에서 오른쪽으로 히스토그램에 인기도 순서로 나타납니다. 표시할 상태 수가 특성의 전체 상태 수보다 적으면 가장 인기 없는 상태는 전체가 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-132">The states appear in a histogram in order of popularity from left to right; if the number of states that you choose to display is fewer than the total number of states in the attribute, the least popular states are displayed collectively in gray.</span></span> <span data-ttu-id="0690a-133">노드에 대한 각 상태의 정확한 수를 확인하려면 노드 위에 포인터를 올려 놓고 잠시 기다리면 나타나는 정보 팁을 보거나 노드를 선택하여 **마이닝 범례**에서 세부 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-133">To see the exact count for each state for a node, pause the pointer over the node to view an InfoTip, or select the node to view its details in the **Mining Legend**.</span></span>  
  
 <span data-ttu-id="0690a-134">각 노드의 배경색은 **배경** 옵션을 사용하여 선택한 특성 상태의 사례 집중을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-134">The background color of each node represents the concentration of cases of the particular attribute state that you select by using the **Background** option.</span></span> <span data-ttu-id="0690a-135">이 옵션을 사용하여 관심 있는 특정 대상이 포함된 노드를 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-135">You can use this option to highlight nodes that contain a particular target in which you are interested.</span></span>  
  
#### <a name="predicting-continuous-attributes"></a><span data-ttu-id="0690a-136">연속 특성 예측</span><span class="sxs-lookup"><span data-stu-id="0690a-136">Predicting Continuous Attributes</span></span>  
 <span data-ttu-id="0690a-137">예측 가능한 연속 특성을 사용하여 트리를 작성할 때 뷰어는 트리의 각 노드에 대해 히스토그램 대신 다이아몬드 차트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-137">When a tree is built with a continuous predictable attribute, the viewer displays a diamond chart, instead of a histogram, for each node in the tree.</span></span> <span data-ttu-id="0690a-138">다이아몬드 차트에는 특성의 범위를 나타내는 선이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-138">The diamond chart has a line that represents the range of the attribute.</span></span> <span data-ttu-id="0690a-139">다이아몬드는 노드의 평균에 있고 다이아몬드 너비는 해당 노드에서 특성의 분산을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-139">The diamond is located at the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="0690a-140">다이아몬드가 가늘수록 노드에서 보다 더 정확한 예측을 도출할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-140">A thinner diamond indicates that the node can create a more accurate prediction.</span></span> <span data-ttu-id="0690a-141">뷰어는 노드의 분할을 결정하는 데 사용되는 회귀 수식도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-141">The viewer also displays the regression equation, which is used to determine the split in the node.</span></span>  
  
#### <a name="additional-decision-tree-display-options"></a><span data-ttu-id="0690a-142">추가 의사 결정 트리 표시 옵션</span><span class="sxs-lookup"><span data-stu-id="0690a-142">Additional Decision Tree Display Options</span></span>  
 <span data-ttu-id="0690a-143">의사 결정 트리 모델에 대해 드릴스루를 사용하면 트리에서 노드를 마우스 오른쪽 단추로 클릭하고 **드릴스루**를 선택하여 해당 노드를 지원하는 학습 사례에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-143">When drill through is enabled for a decision tree model, you can access the training cases that support a node by right-clicking the node in the tree and selecting **Drill Through**.</span></span> <span data-ttu-id="0690a-144">**마이닝 모델** 탭에서 마이닝 모델에 대한 드릴스루 속성을 조정하거나 데이터 마이닝 마법사 내에서 드릴스루를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-144">You can enable drill through within the Data Mining Wizard, or by adjusting the drill through property on the mining model in the **Mining Models** tab.</span></span>  
  
 <span data-ttu-id="0690a-145">**의사 결정 트리** 탭의 확대/축소 옵션을 사용하여 트리를 확대 또는 축소하거나 **크기 조정** 을 사용하여 전체 모델을 뷰어 화면에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-145">You can use the zoom options on the **Decision Tree** tab to zoom in or out of a tree, or use **Size to Fit** to fit the whole model in the viewer screen.</span></span> <span data-ttu-id="0690a-146">트리가 너무 커서 화면에 맞게 크기를 조정할 수 없으면 **탐색**옵션을 사용하여 트리를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-146">If a tree is too large to be sized to fit the screen, you can use the **Navigation**option to navigate through the tree.</span></span> <span data-ttu-id="0690a-147">**탐색** 을 클릭하면 표시할 모델 섹션을 선택하는 데 사용할 수 있는 별도의 탐색 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-147">Clicking **Navigation** opens a separate navigation window that you can use to select sections of the model to display.</span></span>  
  
 <span data-ttu-id="0690a-148">트리 뷰 이미지를 클립보드로 복사하여 문서 또는 이미지 조작 소프트웨어에 붙여 넣을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-148">You can also copy the tree view image to the Clipboard, so that you can paste it into documents or into image manipulation software.</span></span> <span data-ttu-id="0690a-149">**그래프 뷰 복사** 를 사용하여 뷰어에 표시된 트리 섹션만 복사하거나 **전체 그래프 복사** 를 사용하여 트리에서 확장된 모든 노드를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-149">Use **Copy Graph View** to copy only the section of the tree that is visible in the viewer, or use **Copy Entire Graph** to copy all the expanded nodes in the tree.</span></span>  
  
 [<span data-ttu-id="0690a-150">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0690a-150">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="dependency-network"></a><a name="BKMK_DependencyNetwork"></a><span data-ttu-id="0690a-151">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0690a-151">Dependency Network</span></span>  
 <span data-ttu-id="0690a-152">**종속성 네트워크** 는 모델의 입력 특성과 예측 가능한 특성 간의 종속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-152">The **Dependency Network** displays the dependencies between the input attributes and the predictable attributes in the model.</span></span> <span data-ttu-id="0690a-153">뷰어의 왼쪽에 있는 슬라이더는 종속성 수준에 연결된 필터 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-153">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="0690a-154">슬라이더를 아래로 이동하면 가장 강력한 링크만 뷰어에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-154">If you lower the slider, only the strongest links are shown in the viewer.</span></span>  
  
 <span data-ttu-id="0690a-155">노드를 선택하면 뷰어는 해당 노드와 관련된 종속성을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-155">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="0690a-156">예를 들어 예측 가능한 노드를 선택하면 뷰어는 예측 가능한 노드를 예측하는 데 도움을 주는 각 노드도 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-156">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="0690a-157">뷰어에 많은 노드가 포함되어 있으면 **노드 찾기** 단추를 사용하여 특정 노드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-157">If the viewer contains numerous nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="0690a-158">**노드 찾기** 를 클릭하면 **노드 찾기** 대화 상자가 열리며 여기서 필터를 사용하여 특정 노드를 검색하고 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-158">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
 <span data-ttu-id="0690a-159">뷰어의 아래쪽에 있는 범례는 색 코드를 그래프에 있는 종속성 유형에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-159">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="0690a-160">예를 들어 예측 가능한 노드를 선택하면 예측 가능한 노드는 옥색으로 표시되며 선택한 노드를 예측하는 노드는 주황색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-160">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="0690a-161">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0690a-161">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="mining-legend"></a><a name="BKMK_MiningLegend"></a><span data-ttu-id="0690a-162">마이닝 범례</span><span class="sxs-lookup"><span data-stu-id="0690a-162">Mining Legend</span></span>  
 <span data-ttu-id="0690a-163">의사 결정 트리 모델에서 노드를 선택하면 **마이닝 범례** 에 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-163">The **Mining Legend** displays the following information when you select a node in the decision tree model:</span></span>  
  
-   <span data-ttu-id="0690a-164">예측 가능한 특성 상태로 분류된 노드의 사례 수</span><span class="sxs-lookup"><span data-stu-id="0690a-164">The number of cases in the node, broken down by the states of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="0690a-165">노드의 예측 가능한 특성에 대한 각 사례의 확률</span><span class="sxs-lookup"><span data-stu-id="0690a-165">The probability of each case of the predictable attribute for the node.</span></span>  
  
-   <span data-ttu-id="0690a-166">예측 가능한 특성의 각 상태 수가 포함된 히스토그램</span><span class="sxs-lookup"><span data-stu-id="0690a-166">A histogram that includes a count for each state of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="0690a-167">특정 노드에 도달하는 데 필요한 조건( *노드 경로*라고도 함)</span><span class="sxs-lookup"><span data-stu-id="0690a-167">The conditions that are required to reach a specific node, also known as the *node path*.</span></span>  
  
-   <span data-ttu-id="0690a-168">선형 회귀 모델의 경우 회귀 수식</span><span class="sxs-lookup"><span data-stu-id="0690a-168">For linear regression models, the regression formula.</span></span>  
  
 <span data-ttu-id="0690a-169">솔루션 탐색기와 유사한 방식으로 **마이닝 범례** 를 도킹하고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0690a-169">You can dock and work with the **Mining Legend** in a similar manner as with Solution Explorer.</span></span>  
  
 [<span data-ttu-id="0690a-170">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0690a-170">Back to Top</span></span>](#BKMK_TabsPanes)  
  
## <a name="see-also"></a><span data-ttu-id="0690a-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0690a-171">See Also</span></span>  
 <span data-ttu-id="0690a-172">[Microsoft 의사 결정 트리 알고리즘](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0690a-172">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="0690a-173">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](../mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="0690a-173">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](../mining-model-viewers-data-mining-model-designer.md) </span></span>  
 <span data-ttu-id="0690a-174">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="0690a-174">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="0690a-175">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0690a-175">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="0690a-176">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="0690a-176">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
