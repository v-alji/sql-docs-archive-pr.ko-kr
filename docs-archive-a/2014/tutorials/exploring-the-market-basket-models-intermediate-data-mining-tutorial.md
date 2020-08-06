---
title: 시장 바구니 모델 탐색 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6246aa9330042f0e8033b6f2633a3ed24331ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735639"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="ad6fc-102">시장 바구니 모델 탐색(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="ad6fc-102">Exploring the Market Basket Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="ad6fc-103">모델을 작성 했으므로 이제 `Association` [!INCLUDE[msCoName](../includes/msconame-md.md)] 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 있는 연결 뷰어를 사용 하 여 모델을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-103">Now that you have built the `Association` model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="ad6fc-104">이 자습서는 뷰어를 사용하여 항목 간 관계를 탐색하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-104">This tutorial walks you through using the viewer to explore relationships between items.</span></span> <span data-ttu-id="ad6fc-105">뷰어에서는 함께 나타나는 경향이 있는 제품을 한 눈에 확인하고, 나타나는 패턴을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-105">The viewer helps you see at a glance which products tend to appear together, and get a general idea of the emerging patterns.</span></span>  
  
 <span data-ttu-id="ad6fc-106">[!INCLUDE[msCoName](../includes/msconame-md.md)]연결 뷰어에는 **규칙**, **항목 집합**및 **종속성 네트워크**의 세 가지 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-106">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer contains three tabs: **Rules**, **Itemsets**, and **Dependency Network**.</span></span> <span data-ttu-id="ad6fc-107">각 탭에서 데이터를 약간씩 다르게 표시하기 때문에 모델을 탐색할 때는 일반적으로 내용을 제대로 파악하기 위해 서로 다른 창을 여러 번 앞뒤로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-107">Because each tab reveals a slightly different view of the data, when you are exploring a model, you will typically switch back and forth between the different panes several times as you pursue insights.</span></span>  
  
-   [<span data-ttu-id="ad6fc-108">종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-108">Dependency Network tab</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="ad6fc-109">항목 집합 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-109">Itemsets tab</span></span>](#bkmk_Itemsets)  
  
-   [<span data-ttu-id="ad6fc-110">규칙 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-110">Rules tab</span></span>](#bkmk_Rules)  
  
-   [<span data-ttu-id="ad6fc-111">일반 콘텐츠 뷰</span><span class="sxs-lookup"><span data-stu-id="ad6fc-111">Generic Content View</span></span>](#bkmk_ContentViewer)  
  
 <span data-ttu-id="ad6fc-112">이 자습서에서는 **종속성 네트워크** 탭에서 시작 하 고 **규칙** 탭 및 **항목 집합** 탭을 사용 하 여 뷰어에 표시 되는 관계에 대 한 이해를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-112">For this tutorial, you will start on the **Dependency Network** tab, and then use the **Rules** tab and **Itemsets** tab to deepen your understanding of the relationships revealed in the viewer.</span></span> <span data-ttu-id="ad6fc-113">또한 **Microsoft 일반 콘텐츠 트리 뷰어** 를 사용 하 여 개별 규칙 또는 항목 집합에 대 한 자세한 통계를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-113">You will also use the **Microsoft Generic Content Tree Viewer** to retrieve detailed statistics for individual rules or itemsets.</span></span>  
  
##  <a name="dependency-network-tab"></a><a name="bkmk_DepNet"></a><span data-ttu-id="ad6fc-114">종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-114">Dependency Network Tab</span></span>  
 <span data-ttu-id="ad6fc-115">**종속성 네트워크** 탭을 사용 하 여 모델의 여러 항목에 대 한 상호 작용을 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-115">With the **Dependency Network** tab, you can investigate the interaction of the different items in the model.</span></span> <span data-ttu-id="ad6fc-116">뷰어의 각 노드는 항목을 나타내고 항목 사이의 선은 규칙을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-116">Each node in the viewer represents an item, while the lines between them represent rules.</span></span> <span data-ttu-id="ad6fc-117">노드를 선택하면 선택된 항목을 예측하는 다른 노드나 현재 항목이 예측하는 항목을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-117">By selecting a node, you can see which other nodes predict the selected item, or which items the current item predicts.</span></span> <span data-ttu-id="ad6fc-118">항목 간에 양방향 연결이 있는 경우(같은 트랜잭션에 자주 나타남)도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-118">In some cases, there is a two-way association between items, meaning that they often appear in the same transaction.</span></span> <span data-ttu-id="ad6fc-119">탭 아래쪽에 있는 색 범례를 참조하여 연결의 방향을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-119">You can refer to the color legend at the bottom of the tab to determine the direction of the association.</span></span>  
  
 <span data-ttu-id="ad6fc-120">두 항목을 연결하는 선은 이러한 항목이 트랜잭션에 함께 나타날 가능성이 높음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-120">A line connecting two items means that these items are likely to appear in a transaction together.</span></span> <span data-ttu-id="ad6fc-121">즉, 고객이 이러한 항목을 함께 구매할 가능성이 높음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-121">In other words, customers are likely to buy these items together.</span></span> <span data-ttu-id="ad6fc-122">슬라이더는 규칙의 확률과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-122">The slider is associated with the probability of the rule.</span></span> <span data-ttu-id="ad6fc-123">슬라이더를 위나 아래로 이동하여 필터로 약한 연결(확률이 낮은 규칙)을 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-123">Move the slider up or down to filter out weak associations, meaning rules with low probability.</span></span>  
  
 <span data-ttu-id="ad6fc-124">종속성 네트워크 그래프에는 논리적으로 >B로 나타낼 수 있는 쌍으로 된 규칙이 표시 됩니다. 즉, 제품 A를 구매한 경우 제품 B가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-124">The dependency network graph shows pairwise rules, which can be represented logically as A->B, meaning if Product A is purchased, then Product B is likely.</span></span> <span data-ttu-id="ad6fc-125">그래프에서는 AB->C 형식의 규칙을 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-125">The graph cannot show rules of the type AB->C.</span></span> <span data-ttu-id="ad6fc-126">모든 규칙을 표시하기 위해 슬라이더를 이동하지만 그래프에 어떤 선도 표시되지 않는 경우 알고리즘 매개 변수의 조건에 맞는 규칙 쌍이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-126">If you move the slider to show all rules but still do not see any lines in the graph, it means that there were no pairwise rules that met the criteria of the algorithm parameters.</span></span>  
  
 <span data-ttu-id="ad6fc-127">또한 특성 이름의 첫 문자를 입력하여 이름별로 노드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-127">You can also find nodes by name, by typing the first letters of the attribute name.</span></span> <span data-ttu-id="ad6fc-128">자세한 내용은 [노드 찾기 대화 상자&#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-128">For more information, see [Find Node Dialog Box &#40;Mining Model Viewer&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).</span></span>  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a><span data-ttu-id="ad6fc-129">Microsoft 연결 규칙 뷰어에서 연결 모드를 열려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-129">To open the Association mode in the Microsoft Assocaition Rules Viewer</span></span>  
  
1.  <span data-ttu-id="ad6fc-130">**솔루션 탐색기**에서 연결 구조를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-130">In **Solution Explorer**, double-click the Association structure.</span></span>  
  
2.  <span data-ttu-id="ad6fc-131">데이터 마이닝 디자이너에서 **마이닝 모델 뷰어** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-131">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="ad6fc-132">**마이닝 모델** 드롭다운 목록의 마이닝 모델 목록에서 연결을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-132">Select Association from the list of mining models in the **Mining Model** dropdown list.</span></span>  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a><span data-ttu-id="ad6fc-133">종속성 그래프를 탐색하고 특정 노드를 찾으려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-133">To navigate the dependency graph and locate specific nodes</span></span>  
  
1.  <span data-ttu-id="ad6fc-134">**마이닝 모델 뷰어** 탭에서 **종속성 네트워크** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-134">In the **Mining Model Viewer** tab, click the **Dependency Network** tab.</span></span>  
  
2.  <span data-ttu-id="ad6fc-135">각 노드의 레이블을 쉽게 볼 수 있을 때까지 여러 번 **확대/축소** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-135">Click **Zoom In** several times, until you can easily view the labels for each node.</span></span>  
  
     <span data-ttu-id="ad6fc-136">기본적으로 모든 노드가 표시되어 있는 그래프가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-136">By default, the graph displays with all nodes visible.</span></span> <span data-ttu-id="ad6fc-137">복잡한 모델에서는 노드 수가 많아 각 노드의 크기가 매우 작을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-137">In a complex model, there may be many nodes, making each node quite small.</span></span>  
  
3.  <span data-ttu-id="ad6fc-138">**+** 뷰어의 오른쪽 아래 모서리에 있는 기호를 클릭 하 고 마우스 단추를 누른 채로 그래프를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-138">Click the **+** sign in the lower right-hand corner of the viewer and hold down the mouse button to pan around the graph.</span></span>  
  
4.  <span data-ttu-id="ad6fc-139">뷰어의 왼쪽에서 슬라이더를 아래로 끌어서 **모든 링크** (기본값)에서 슬라이더 컨트롤의 아래쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-139">On the left side of the viewer, drag the slider down, moving it from **All Links** (the default) to the bottom of the slider control.</span></span>  
  
5.  <span data-ttu-id="ad6fc-140">뷰어는 그래프를 업데이트하여 가장 강력한 연결인 Touring Tire 항목과 Touring Tire Tube 항목 간의 연결만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-140">The viewer updates the graph to now show only the strongest association, between the Touring Tire and Touring Tire Tube items.</span></span>  
  
6.  <span data-ttu-id="ad6fc-141">**여행용 타이어 튜브 = 기존**이라는 레이블이 지정 된 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-141">Click the node labeled **Touring Tire Tube = Existing**.</span></span>  
  
     <span data-ttu-id="ad6fc-142">그래프가 업데이트되어 이 항목과 강력하게 연결되는 항목만 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-142">The graph is updated to highlight only items that are strongly related to this item.</span></span> <span data-ttu-id="ad6fc-143">두 항목 사이의 화살표 방향을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-143">Note the direction of the arrow between the two items.</span></span>  
  
7.  <span data-ttu-id="ad6fc-144">뷰어의 왼쪽에서 슬라이더를 다시 위로 끌어 아래에서 중간 근처로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-144">On the left side of the viewer, drag the slider up again, moving it from the bottom to around the middle.</span></span>  
  
     <span data-ttu-id="ad6fc-145">두 항목을 연결하는 화살표의 변경 내용을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-145">Note the changes in the arrow that connects the two items.</span></span>  
  
8.  <span data-ttu-id="ad6fc-146">종속성 네트워크 창의 맨 위에 있는 드롭다운 목록에서 **특성 이름만 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-146">Select **Show attribute name only** from the dropdown list at the top of the Dependency Network pane.</span></span>  
  
     <span data-ttu-id="ad6fc-147">그래프의 텍스트 레이블이 업데이트되어 모델 이름만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-147">The text labels in the graph are updated to show only the model name.</span></span>  
  
 [<span data-ttu-id="ad6fc-148">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ad6fc-148">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="itemsets-tab"></a><a name="bkmk_Itemsets"></a><span data-ttu-id="ad6fc-149">항목 집합 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-149">Itemsets Tab</span></span>  
 <span data-ttu-id="ad6fc-150">다음으로 Touring Tire 및 Touring Tire Tube 제품에 대한 모델로 생성된 규칙 및 항목 집합에 대해 좀 더 자세히 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-150">Next, you will learn more about the rules and itemsets generated by the model for the Touring Tire and Touring Tire Tube products.</span></span> <span data-ttu-id="ad6fc-151">**항목 집합** 탭은 연결 알고리즘이 검색 하는 항목 집합와 관련 된 세 가지 중요 한 정보를 표시 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad6fc-151">The **Itemsets** tab displays three important pieces of information that relate to the itemsets that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm discovers:</span></span>  
  
-   <span data-ttu-id="ad6fc-152">**지원:** 항목 집합이 발생 하는 트랜잭션 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-152">**Support:** The number of transactions in which the itemset occurs.</span></span>  
  
-   <span data-ttu-id="ad6fc-153">**크기:** 항목 집합에 있는 항목의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-153">**Size:** The number of items in the itemset.</span></span>  
  
-   <span data-ttu-id="ad6fc-154">**항목:** 각 항목 집합에 포함 된 항목의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-154">**Items:** A list of the items included in each itemset.</span></span>  
  
 <span data-ttu-id="ad6fc-155">알고리즘 매개 변수가 설정된 방식에 따라 알고리즘에서 많은 항목 집합을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-155">Depending on how the algorithm parameters are set, the algorithm might generate many itemsets.</span></span> <span data-ttu-id="ad6fc-156">뷰어에 반환되는 각 항목 집합은 항목이 판매된 트랜잭션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-156">Each itemset that is returned in the viewer represents transactions in which the item was sold.</span></span> <span data-ttu-id="ad6fc-157">**항목 집합** 탭의 맨 위에 있는 컨트롤을 사용 하 여 지정 된 최소 지원 및 항목 집합 크기를 포함 하는 항목 집합 표시 하도록 뷰어를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-157">By using the controls at the top of the **Itemsets** tab, you can filter the viewer to show only the itemsets that contain a specified minimum support and itemset size.</span></span>  
  
 <span data-ttu-id="ad6fc-158">다른 마이닝 모델을 사용하고 있는데 항목 집합이 나열되지 않는 경우 알고리즘 매개 변수의 조건에 맞는 항목 집합이 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-158">If you are working with a different mining model and no itemsets are listed, it is because no itemsets met the criteria of the algorithm parameters.</span></span> <span data-ttu-id="ad6fc-159">이러한 시나리오에서는 지원이 낮은 항목 집합을 허용하도록 알고리즘 매개 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-159">In such a scenario, you can change the algorithm parameters to allow itemsets that have lower support.</span></span>  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a><span data-ttu-id="ad6fc-160">뷰어에 표시되는 항목 집합을 이름별로 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-160">To filter the itemsets that are shown in the viewer by name</span></span>  
  
1.  <span data-ttu-id="ad6fc-161">뷰어의 **항목 집합** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-161">Click the **Itemsets** tab of the viewer.</span></span>  
  
2.  <span data-ttu-id="ad6fc-162">항목 **집합 필터** 상자에를 입력 한 `Touring Tire` 다음 상자 바깥쪽을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-162">In the **Filter Itemset** box, type `Touring Tire`, and then click outside the box.</span></span>  
  
     <span data-ttu-id="ad6fc-163">필터가 이 문자열이 포함된 항목을 모두 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-163">The filter returns all items that contain this string.</span></span>  
  
3.  <span data-ttu-id="ad6fc-164">**표시** 목록에서 **특성 이름만 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-164">In the **Show** list, select **Show attribute name only**.</span></span>  
  
4.  <span data-ttu-id="ad6fc-165">**긴 이름 표시** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-165">Select the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="ad6fc-166">항목 집합 목록이 업데이트되어 Touring Tire라는 문자열이 있는 항목 집합만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-166">The list of itemsets is updated to show only the itemsets that contain the string Touring Tire.</span></span> <span data-ttu-id="ad6fc-167">항목 집합의 긴 이름에는 각 항목에 대한 특성 및 값이 들어 있는 테이블의 이름이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-167">The long name of the itemset includes the name of the table that contains the attribute and value for each item.</span></span>  
  
5.  <span data-ttu-id="ad6fc-168">**긴 이름 표시** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-168">Clear the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="ad6fc-169">항목 집합 목록이 업데이트되어 짧은 이름만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-169">The list of itemsets is updated to show only the short name.</span></span>  
  
 <span data-ttu-id="ad6fc-170">**Support** 열의 값은 각 항목 집합에 대 한 트랜잭션 수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-170">The values in the **Support** column indicate the number of transactions for each itemset.</span></span> <span data-ttu-id="ad6fc-171">항목 집합에 대한 트랜잭션은 항목 집합의 모든 항목이 포함된 구매를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-171">A transaction for an itemset means a purchase that included all the items in the itemset.</span></span>  
  
 <span data-ttu-id="ad6fc-172">기본적으로 뷰어는 항목 집합을 지원별로 내림차순으로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-172">By default, the viewer lists the itemsets in descending order by support.</span></span> <span data-ttu-id="ad6fc-173">열 머리글을 클릭하여 항목 집합 크기 또는 이름과 같은 다른 열별로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-173">You can click on the column headers to sort by a different column, such as the itemset size or name.</span></span> <span data-ttu-id="ad6fc-174">항목 집합에 포함된 개별 트랜잭션에 대해 좀 더 자세히 알아보려는 경우 항목 집합에서 개별 사례로 드릴스루할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-174">If you are interested in learning more about the individual transactions that are included in an itemset, you can drill through from the itemsets to the individual cases.</span></span> <span data-ttu-id="ad6fc-175">드릴스루 결과의 구조 열은 모델에 사용되지 않은 고객의 소득 수준 및 고객 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-175">The structure columns in the drillthrough results are the customer's income level and customer ID, which were not used in the model.</span></span>  
  
#### <a name="to-view-details-for-an-itemset"></a><span data-ttu-id="ad6fc-176">항목 집합의 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-176">To view details for an itemset</span></span>  
  
1.  <span data-ttu-id="ad6fc-177">항목 집합 목록에서 항목 **집합** 열 머리글을 클릭 하 여 이름별로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-177">In the list of itemsets, click the **Itemset** column heading to sort by name.</span></span>  
  
2.  <span data-ttu-id="ad6fc-178">항목 `Touring Tire` (두 번째 항목 없음)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-178">Locate the item, `Touring Tire` (with no second item).</span></span>  
  
3.  <span data-ttu-id="ad6fc-179">항목을 마우스 오른쪽 단추로 클릭 하 고 `Touring Tire` **드릴스루**를 선택한 다음 **모델 및 구조 열**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-179">Right-click the item, `Touring Tire`, select **Drill Through**, and then select **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="ad6fc-180">**드릴스루** 대화 상자에는이 항목 집합에 대 한 지원으로 사용 되는 개별 트랜잭션이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-180">The **Drill Through** dialog box displays the individual transactions used as support for this itemset.</span></span>  
  
4.  <span data-ttu-id="ad6fc-181">중첩 테이블 vAssocSeqLineItems를 확장하여 트랜잭션에 있는 구매의 실제 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-181">Expand the nested table, vAssocSeqLineItems, to view the actual list of purchases in the transaction.</span></span>  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a><span data-ttu-id="ad6fc-182">항목 집합을 지원 또는 크기별로 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-182">To filter itemsets by support or size</span></span>  
  
1.  <span data-ttu-id="ad6fc-183">항목 **집합 필터** 상자에 있을 수 있는 모든 텍스트를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-183">Clear any text that might be in the **Filter Itemset** box.</span></span> <span data-ttu-id="ad6fc-184">텍스트 필터와 숫자 필터를 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-184">You cannot use a text filter together with a numeric filter.</span></span>  
  
2.  <span data-ttu-id="ad6fc-185">**최소 지원** 상자에 100을 입력 한 다음 뷰어의 배경을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-185">In the **Minimum support** box, type 100, and then click the background of the viewer.</span></span>  
  
     <span data-ttu-id="ad6fc-186">항목 집합 목록이 업데이트되어 적어도 100개 이상 지원되는 항목 집합만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-186">The list of itemsets is updated to show only itemsets with support of at least 100.</span></span>  
  
 [<span data-ttu-id="ad6fc-187">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ad6fc-187">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="rules-tab"></a><a name="bkmk_Rules"></a><span data-ttu-id="ad6fc-188">규칙 탭</span><span class="sxs-lookup"><span data-stu-id="ad6fc-188">Rules Tab</span></span>  
 <span data-ttu-id="ad6fc-189">**규칙** 탭에는 알고리즘이 검색 하는 규칙과 관련 된 다음 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-189">The **Rules** tab displays the following information that is related to the rules that the algorithm finds.</span></span>  
  
-   <span data-ttu-id="ad6fc-190">**확률:** 왼쪽 항목이 지정 된 경우 오른쪽 항목의 확률로 정의 되는 규칙의 *가능성* 입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-190">**Probability:** The *likelihood* of a rule, defined as the probability of the right-hand item given the left-hand side item.</span></span>  
  
-   <span data-ttu-id="ad6fc-191">**중요도:** 규칙의 유용성을 측정 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-191">**Importance:** A measure of the usefulness of a rule.</span></span> <span data-ttu-id="ad6fc-192">값이 클수록 더 나은 규칙을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-192">A greater value means a better rule.</span></span>  
  
     <span data-ttu-id="ad6fc-193">중요도는 확률만 보면 오해가 발생할 수 있으므로 규칙의 유용성을 측정할 수 있도록 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-193">Importance is provided to help you gauge the usefulness of a rule, because probability alone can be misleading.</span></span> <span data-ttu-id="ad6fc-194">예를 들어 모든 트랜잭션에 물병이 포함되어 있는 경우(물병이 홍보의 일환으로 각 고객의 시장 바구니에 자동으로 추가된 경우) 모델은 물병의 확률이 1이라고 예측하는 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-194">For example, if every transaction contains a water bottle--perhaps the water bottle is added to each customer's cart automatically as part of a promotion--the model would create a rule predicting that water bottle has a probability of 1.</span></span> <span data-ttu-id="ad6fc-195">확률만 봐서는 이 규칙이 매우 정확하지만 유용한 정보를 제공하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-195">Based on probability alone, this rule is very accurate, but it does not provide useful information.</span></span>  
  
-   <span data-ttu-id="ad6fc-196">**규칙:** 규칙의 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-196">**Rule:** The definition of the rule.</span></span> <span data-ttu-id="ad6fc-197">시장 바구니 모델의 경우 규칙은 항목의 특정 조합을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-197">For a market basket model, a rule describes a specific combination of items.</span></span>  
  
 <span data-ttu-id="ad6fc-198">각 규칙을 사용하여 다른 항목의 존재를 기반으로 트랜잭션에 있는 특정 항목의 존재 여부를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-198">Each rule can be used to predict the presence of an item in a transaction based on the presence of other items.</span></span> <span data-ttu-id="ad6fc-199">**항목 집합** 탭에서와 마찬가지로 가장 관심 있는 규칙만 표시 되도록 규칙을 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-199">Just like in the **Itemsets** tab, you can filter the rules so that only the most interesting rules are shown.</span></span> <span data-ttu-id="ad6fc-200">규칙이 없는 마이닝 모델을 사용하고 있는 경우 알고리즘 매개 변수를 변경하여 규칙에 대한 확률 임계값을 낮게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-200">If you are working with a mining model that does not have any rules, you might want to change the algorithm parameters to lower the probability threshold for rules.</span></span>  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a><span data-ttu-id="ad6fc-201">Mountain-200 자전거를 포함하는 규칙만 표시하려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-201">To see only rules that include the Mountain-200 bicycle</span></span>  
  
1.  <span data-ttu-id="ad6fc-202">**마이닝 모델 뷰어** 탭에서 **규칙** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-202">In the **Mining Model Viewer** tab, click the **Rules** tab.</span></span>  
  
2.  <span data-ttu-id="ad6fc-203">**필터 규칙** 상자에를 입력 `Mountain-200` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-203">In the **Filter Rule** box, enter `Mountain-200`.</span></span>  
  
     <span data-ttu-id="ad6fc-204">**긴 이름 표시** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-204">Clear the **Show long name** check box.</span></span>  
  
3.  <span data-ttu-id="ad6fc-205">**표시** 목록에서 **특성 이름만 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-205">From the **Show** list, select **Show attribute name only**.</span></span>  
  
     <span data-ttu-id="ad6fc-206">그러면 뷰어에 "" 이라는 단어가 포함 된 규칙만 표시 됩니다 `Mountain-200` .</span><span class="sxs-lookup"><span data-stu-id="ad6fc-206">The viewer will then display only the rules that contain the words "`Mountain-200`".</span></span> <span data-ttu-id="ad6fc-207">이 규칙의 확률은 다른 사람이 자전거를 구매할 때 해당 사용자가 나열 된 `Mountain-200` 다른 제품도 구매할 가능성이 있음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-207">The probability of the rule tells you how likely it is that when someone buys a `Mountain-200` bicycle, that person will also buy the other listed product.</span></span>  
  
 <span data-ttu-id="ad6fc-208">규칙은 확률별로 내림차순으로 정렬되지만 열 머리글을 클릭하여 정렬 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-208">The rules are ordered by probability in descending order, but you can click the column headings to change the sort order.</span></span> <span data-ttu-id="ad6fc-209">특정 규칙에 대한 자세한 내용을 확인하려면 드릴스루를 사용하여 지원하는 사례를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-209">If you are interested in finding out more details about a particular rule, you can use drillthrough to view the supporting cases.</span></span>  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a><span data-ttu-id="ad6fc-210">특정 규칙을 지원하는 사례를 보려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-210">To view cases that support a particular rule</span></span>  
  
1.  <span data-ttu-id="ad6fc-211">**규칙** 탭에서 보려는 규칙을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-211">In the **Rules** tab, right-click the rule that you want to view.</span></span>  
  
2.  <span data-ttu-id="ad6fc-212">**드릴스루**를 선택한 다음 **모델 열만**또는 **모델 및 구조 열**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-212">Select **Drill Through**, and then select **Model Columns Only**, or **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="ad6fc-213">**드릴스루** 대화 상자는 창의 맨 위에 있는 규칙에 대 한 요약 및 규칙에 대 한 지원 데이터로 사용 된 모든 사례 목록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-213">The **Drill Through** dialog box provides a summary of the rule at the top of the pane, and a list of all cases that were used as supporting data for the rule.</span></span>  
  
 [<span data-ttu-id="ad6fc-214">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ad6fc-214">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_ContentViewer"></a><span data-ttu-id="ad6fc-215">일반 콘텐츠 트리 뷰어</span><span class="sxs-lookup"><span data-stu-id="ad6fc-215">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="ad6fc-216">이 뷰어는 알고리즘이나 모델 유형에 관계없이 모든 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-216">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="ad6fc-217">**Microsoft 일반 콘텐츠 트리 뷰어** 는 **뷰어** 드롭다운 목록에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-217">The **Microsoft Generic Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="ad6fc-218">콘텐츠 트리는 마이닝 모델을 일련의 노드로 표시합니다. 여기서 각 노드는 데이터의 일부 하위 집합에 대해 배운 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-218">A content tree is a representation of a mining model as a series of nodes, where each node represents learned knowledge about some subset of the data.</span></span> <span data-ttu-id="ad6fc-219">노드에는 패턴, 일련의 규칙, 클러스터 또는 일부 특징을 공유하는 날짜 범위의 정의가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-219">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some characteristics.</span></span> <span data-ttu-id="ad6fc-220">노드의 정확한 콘텐츠는 예측 가능한 특성의 유형 및 알고리즘에 따라 다르지만 콘텐츠의 일반적인 표시는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-220">The exact content of the node differs depending on the algorithm and the type of the predictable attribute, but the general representation of the content is the same.</span></span> <span data-ttu-id="ad6fc-221">각 노드를 확장하여 세부 수준을 높이고 노드의 콘텐츠를 클립보드로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-221">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span>  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a><span data-ttu-id="ad6fc-222">콘텐츠 뷰어를 사용하여 규칙에 대한 자세한 내용을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="ad6fc-222">To view details about the rule by using the content viewer</span></span>  
  
1.  <span data-ttu-id="ad6fc-223">**마이닝 모델 뷰어** 탭의 **뷰어** 목록에서 **Microsoft 일반 콘텐츠 트리 뷰어** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-223">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** list.</span></span>  
  
2.  <span data-ttu-id="ad6fc-224">노드 캡션 창에서 목록의 맨 아래로 스크롤하고 마지막 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-224">In the Node Caption pane, scroll to the bottom of the list, and click the last node.</span></span>  
  
     <span data-ttu-id="ad6fc-225">뷰어는 먼저 항목 집합을 표시하고 그 다음으로 규칙을 표시하지만 이들을 그룹화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-225">The viewer shows itemsets first and rules next, but does not group them.</span></span> <span data-ttu-id="ad6fc-226">특정 노드를 가장 쉽게 찾는 방법은 내용 쿼리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-226">The easiest way to find a specific node is to create a content query.</span></span> <span data-ttu-id="ad6fc-227">자세한 내용은 [연결 모델 쿼리 예제](../../2014/analysis-services/data-mining/association-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-227">For more information, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
3.  <span data-ttu-id="ad6fc-228">노드 정보 창에서 NODE_TYPE 및 NODE_DESCRIPTION에 대한 값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-228">In the Node Details pane, review the value for NODE_TYPE and NODE_DESCRIPTION.</span></span>  
  
     <span data-ttu-id="ad6fc-229">노드 유형 8은 규칙이고 노드 유형 7은 항목 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-229">A node type of 8 is a rule, and a node type of 7 is an itemset.</span></span> <span data-ttu-id="ad6fc-230">규칙에서 NODE_DESCRIPTION 값은 규칙을 구성하는 조건을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-230">For a rule, the value of NODE_DESCRIPTION tells you the conditions that make up the rule.</span></span> <span data-ttu-id="ad6fc-231">항목 집합에서 NODE_DESCRIPTION 값은 항목 집합에 포함된 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-231">For an itemset, the value of NODE_DESCRIPTION tells you the items included in the itemset.</span></span>  
  
 <span data-ttu-id="ad6fc-232">또한 내용 쿼리를 만들어 규칙에 대한 자세한 통계를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-232">You can also create a content query to obtain detailed statistics about the rules.</span></span> <span data-ttu-id="ad6fc-233">마이닝 모델 콘텐츠에 대 한 자세한 내용과이를 해석 하는 방법에 대 한 자세한 내용은 [연결 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services-데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad6fc-233">For more information about mining model content and how to interpret it, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="ad6fc-234">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ad6fc-234">Back to Top</span></span>](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ad6fc-235">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ad6fc-235">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ad6fc-236">마이닝 모델의 중첩 테이블 필터링 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="ad6fc-236">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad6fc-237">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad6fc-237">See Also</span></span>  
 <span data-ttu-id="ad6fc-238">[3 단원: 중급 데이터 마이닝 자습서 &#40;시장 바구니 시나리오 구축&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="ad6fc-238">[Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="ad6fc-239">[4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ad6fc-239">[Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span></span>  
 <span data-ttu-id="ad6fc-240">[Microsoft 연결 알고리즘](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ad6fc-240">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="ad6fc-241">Microsoft 연결 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="ad6fc-241">Microsoft Association Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  
