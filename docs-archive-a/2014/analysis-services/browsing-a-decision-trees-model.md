---
title: 의사 결정 트리 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 809d2e494cfa7a6c4078acf95c2c70a0e68c188d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648113"
---
# <a name="browsing-a-decision-trees-model"></a><span data-ttu-id="a1281-102">의사 결정 트리 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="a1281-102">Browsing a Decision Trees Model</span></span>
  <span data-ttu-id="a1281-103">**찾아보기**를 사용 하 여 분류 모델을 열면의 의사 결정 트리 뷰어와 비슷한 대화형 의사 결정 트리 뷰어에 모델이 표시 됩니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a1281-103">When you open a classification model using **Browse**, the model is displayed in an interactive decision tree viewer, similar to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a1281-104">뷰어에는 데이터 그룹을 구별하는 조건을 강조 표시하는 그래프로 분류 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-104">The viewer displays the results of classification as a graph that is designed to highlight the criteria that differentiate one group of data from another.</span></span> <span data-ttu-id="a1281-105">트리의 개별 하위 집합으로 드릴다운하고 기본 데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-105">You can also drill down into individual subsets of the tree and retrieve the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="a1281-106">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="a1281-106">Explore the Model</span></span>  
 <span data-ttu-id="a1281-107">의사 결정 트리 알고리즘을 기반으로 하는 모델에는 검토할 만한 중요한 정보가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-107">Models based on the Decision Trees algorithm have lots of interesting information to explore.</span></span> <span data-ttu-id="a1281-108">**찾아보기** 창에는 그래프를 사용 하 여 패턴을 학습 하 고 결과를 예측 하는 데 도움이 되는 다음과 같은 탭과 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-108">The **Browse** window includes the following tabs and panes to help you learn the patterns and predict outcomes using the graph:</span></span>  
  
-   [<span data-ttu-id="a1281-109">Decision Tree</span><span class="sxs-lookup"><span data-stu-id="a1281-109">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="a1281-110">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="a1281-110">Dependency Network</span></span>](#BKMK_DNetwork)  
  
 <span data-ttu-id="a1281-111">의사 결정 트리 모델을 테스트하려면 샘플 데이터 통합 문서의 학습 데이터나 원본 데이터 탭에 있는 샘플 데이터를 사용하고, Bike Buyer를 예측 가능한 특성으로 사용하여 의사 결정 트리 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-111">To experiment with a decision trees model, you can use the sample data on the Training Data (or Source Data) tab of the sample data workbook, and build a decision tree model using Bike Buyer as the predictable attribute.</span></span>  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="a1281-112">의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="a1281-112">Decision Tree</span></span>  
 <span data-ttu-id="a1281-113">이 보기에서 결과로 이어지는 요인을 이해하고 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-113">This view is intended to help you understand and explore the factors that lead to an outcome.</span></span>  
  
 <span data-ttu-id="a1281-114">의사 결정 트리 그래프는 다음과 같이 왼쪽에서 오른쪽으로 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-114">The decision tree graph can be read from left to right as follows:</span></span>  
  
-   <span data-ttu-id="a1281-115">*노드*라고 하는 사각형에는 데이터의 하위 집합이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-115">The rectangles, which are referred to as *nodes*, contain subsets of the data.</span></span> <span data-ttu-id="a1281-116">노드의 레이블로 해당 하위 집합의 뚜렷한 특징을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-116">The label on the node tells you the defining characteristics of that subset.</span></span>  
  
-   <span data-ttu-id="a1281-117">**모두**레이블이 지정 된 맨 왼쪽 노드는 전체 데이터 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-117">The leftmost node, labeled **All**, represents the complete data set.</span></span> <span data-ttu-id="a1281-118">모든 후속 노드는 데이터의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-118">All subsequent nodes represent subsets of the data.</span></span>  
  
-   <span data-ttu-id="a1281-119">의사 결정 트리에는 많은 *분할*또는 데이터가 특성에 따라 여러 집합으로 달라 지므로는 위치가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-119">A decision tree contains many *splits*, or places where the data diverges into multiple sets based on attributes.</span></span>  
  
     <span data-ttu-id="a1281-120">예를 들어, 샘플 모델의 첫 번째 분할은 데이터 세트을 나이에 따라 세 그룹으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-120">For example, the first split in the sample model divides the dataset into three groups by age.</span></span>  
  
-   <span data-ttu-id="a1281-121">**모든** 노드 바로 뒤의 분할은이 데이터 집합을 나누는 기본 조건을 표시 하므로 가장 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-121">The split immediately after the **All** node is most important because it shows the primary condition that divides this dataset.</span></span>  
  
     <span data-ttu-id="a1281-122">추가 분할은 오른쪽에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-122">Additional splits occur to the right.</span></span> <span data-ttu-id="a1281-123">따라서 트리의 여러 세그먼트를 분석하여 구매 동작에 가장 큰 영향을 끼친 특성을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-123">Thus, by analyzing different segments of the tree, you can learn which attributes had the most influence on purchasing behavior.</span></span>  
  
 <span data-ttu-id="a1281-124">![연결 모델에 대한 종속성 네트워크 그래프](media/dm13-dec-tree-split-definition.gif "연결 모델에 대한 종속성 네트워크 그래프")</span><span class="sxs-lookup"><span data-stu-id="a1281-124">![Dependency network graph for an association model](media/dm13-dec-tree-split-definition.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="a1281-125">이 정보를 사용하여 구매 장려가 필요한 고객에 마케팅 캠페인을 집중할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-125">Using this information, you might focus a marketing campaign on customers that might simply need encouragement to make a purchase.</span></span>  
  
##### <a name="explore-the-decision-tree"></a><span data-ttu-id="a1281-126">의사 결정 트리 탐색</span><span class="sxs-lookup"><span data-stu-id="a1281-126">Explore the decision tree</span></span>  
  
1.  <span data-ttu-id="a1281-127">**모든** 노드를 클릭 하 고 **마이닝 범례**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-127">Click the **All** node, and look at the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="a1281-128">결과 분석과 학습 데이터 집합의 정확한 사례 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-128">It displays the exact count of cases in the training data set, as well as a breakdown of the outcomes.</span></span>  
  
     <span data-ttu-id="a1281-129">노드를 마우스로 가리켜서 동일한 정보를 도구 설명으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-129">You can view the same information in a tooltip if you pause the mouse over a node.</span></span>  
  
2.  <span data-ttu-id="a1281-130">각 노드 옆의 더하기 및 빼기 기호를 클릭하여 트리를 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-130">Click the plus and minus signs next to each node to expand or collapse the tree.</span></span>  
  
     <span data-ttu-id="a1281-131">**수준 표시** 슬라이더를 사용 하 여 트리를 확장 하거나 축소할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-131">You can also use the **Show Level** slider to expand or shrink the tree.</span></span>  
  
3.  <span data-ttu-id="a1281-132">일부 노드는 다른 노드보다 어둡습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-132">Notice that some nodes are darker than others?</span></span>  
  
     <span data-ttu-id="a1281-133">기본적으로 **채우기** 는 음영 변수로 사용 됩니다. 즉, 색의 농도가 가장 많이 지원 되는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-133">By default, **Population** is used as the shading variable, which means that the intensity of the color shows you which nodes have the most support.</span></span>  
  
     <span data-ttu-id="a1281-134">따라서 가장 왼쪽의 노드는 전체 데이터 세트을 포함하기 때문에 가장 어둡습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-134">Therefore the leftmost node is darkest, because it contains the entire dataset.</span></span>  
  
4.  <span data-ttu-id="a1281-135">**모든 경우** 의 **Background** 값을 **예**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-135">Change the value for **Background** from **All Cases** to **Yes**.</span></span>  
  
     <span data-ttu-id="a1281-136">![구매자를 강조 표시하도록 의사 결정 트리 그래프 변경](media/dm13-dectreeshadedbuyer.gif "구매자를 강조 표시하도록 의사 결정 트리 그래프 변경")</span><span class="sxs-lookup"><span data-stu-id="a1281-136">![changing decision tree graph to highlight buyers](media/dm13-dectreeshadedbuyer.gif "changing decision tree graph to highlight buyers")</span></span>  
  
5.  <span data-ttu-id="a1281-137">이제 색의 강도로 각 노드에서 얼마나 많은 고객이 자전거를 구입했는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-137">Now the intensity of the color tells you how many customers in each node purchased a bike, which is the behavior you are interested in.</span></span>  
  
     <span data-ttu-id="a1281-138">각 노드 내에 색이 지정된 막대가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-138">Notice the colored bars within each node.</span></span> <span data-ttu-id="a1281-139">이 막대는 이 데이터 하위 집합 내의 결과 분포를 보여 주는 히스토그램입니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-139">This is a histogram that shows the distribution of outcomes within this subset of data.</span></span> <span data-ttu-id="a1281-140">예를 들어 샘플 자전거 구매자 의사 결정 트리에서 색이 지정 된 막대는 자전거를 구매한 고객의 비율을 보여 줍니다 (값 없음).</span><span class="sxs-lookup"><span data-stu-id="a1281-140">For example, in the sample Bike Buyer decision tree, the colored bar shows the proportion of customers who bought bikes (Yes values) vs. those who did not (No values).</span></span> <span data-ttu-id="a1281-141">정확한 값을 얻으려면 노드를 클릭 하 고 **마이닝 범례**를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-141">To get the exact values, you can click the node and view the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="a1281-142">그래프를 보고 각 데이터 하위 집합이 어떻게 더 작은 그룹으로 나뉘었는지와 결과를 예측하는 데 어느 특성이 가장 유용한지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-142">By following the graph, you can see how each subset of data is further decomposed into smaller groups, and which attributes are most useful in predicting an outcome.</span></span>  
  
     <span data-ttu-id="a1281-143">음영의 강도만으로 관심 있는 몇몇 그룹에 초점을 맞추고 비교를 위한 그룹별 세부 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-143">Just by looking at the intensity of the shading, you can focus on a couple groups of interest, and get more detailed data on them for comparison.</span></span> <span data-ttu-id="a1281-144">예를 들어, 다음 그룹은 자전거를 구입할 확률이 매우 높습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-144">For example, these groups have a fairly high probability of buying bikes:</span></span>  
  
    -   <span data-ttu-id="a1281-145">Age >= 32 및 \< 53 and Yearly Income > = 26000 및 Children = 0</span><span class="sxs-lookup"><span data-stu-id="a1281-145">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children = 0</span></span>  
  
         <span data-ttu-id="a1281-146">총 사례: 1150</span><span class="sxs-lookup"><span data-stu-id="a1281-146">Total cases: 1150</span></span>  
  
         <span data-ttu-id="a1281-147">자전거 구매자 확률: 18%</span><span class="sxs-lookup"><span data-stu-id="a1281-147">Bike buyer probability: 18%</span></span>  
  
    -   <span data-ttu-id="a1281-148">Age >= 32 and \< 53 and Yearly Income > = 26000 And Children not = 0, 결혼 상태 = ' Single '</span><span class="sxs-lookup"><span data-stu-id="a1281-148">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children not = 0 and Marital Status = 'Single'</span></span>  
  
         <span data-ttu-id="a1281-149">총 사례: 402</span><span class="sxs-lookup"><span data-stu-id="a1281-149">Total cases: 402</span></span>  
  
         <span data-ttu-id="a1281-150">자전거 구매자 확률: 16%</span><span class="sxs-lookup"><span data-stu-id="a1281-150">Bike buyer probability: 16%</span></span>  
  
7.  <span data-ttu-id="a1281-151">**배경** 값을 **예** 에서 **아니요** 로 변경 하 고 그래프가 어떻게 변경 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-151">Change the value for **Background** from **Yes** to **No** and see how the graph changes.</span></span>  
  
     <span data-ttu-id="a1281-152">![연결 모델에 대한 종속성 네트워크 그래프](media/dm13-dec-tree-background-no.gif "연결 모델에 대한 종속성 네트워크 그래프")</span><span class="sxs-lookup"><span data-stu-id="a1281-152">![Dependency network graph for an association model](media/dm13-dec-tree-background-no.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="a1281-153">**팁**</span><span class="sxs-lookup"><span data-stu-id="a1281-153">**Tips**</span></span>  
  
-   <span data-ttu-id="a1281-154">데이터를 여러 계열로 나눌 수 있는 경우 모델링할 데이터 집합마다 다른 모델이 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-154">If your data can be divided into multiple series, a different model is built for each set of data that you want to model.</span></span>  
  
-   <span data-ttu-id="a1281-155">샘플 데이터 모델에는 예측 가능한 결과 자전거 구매자가 하나 뿐 이지만 고객이 서비스 계획을 구입 했 고이를 예측 하고자 하는지 여부에 대 한 정보가 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-155">In the sample data model, there is only one predictable outcome - Bike Buyer - but suppose you had information about whether the customer purchased a service plan and wanted to predict that as well.</span></span> <span data-ttu-id="a1281-156">이 경우 별도의 열에 해당 정보를 가지고 있으며 모델에 두 개의 예측 가능한 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-156">In that case you would have that data in a separate column, and include two predictable attributes in the model.</span></span>  
  
     <span data-ttu-id="a1281-157">의사 결정 트리 창의 왼쪽 상단 모서리에 있는 **히스토그램** 옵션을 클릭 하 여 트리의 히스토그램에 나타날 수 있는 최대 상태 수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-157">Click the **Histogram** option, in the upper left corner of the Decision Tree pane, to change the maximum number of states that can appear in the histograms in the tree.</span></span> <span data-ttu-id="a1281-158">이 옵션은 예측 가능한 특성에 많은 상태가 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-158">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="a1281-159">상태는 왼쪽에서 오른쪽으로 히스토그램에 인기도 순서로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-159">The states appear in a histogram in order of popularity from left to right.</span></span>  
  
-   <span data-ttu-id="a1281-160">**의사 결정 트리** 탭의 옵션을 사용 하 여 트리를 표시 하거나 확대/축소 하거나 창에 맞게 그래프 크기를 조정 하는 방법에 영향을 줄 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-160">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed, by zooming in or out, or sizing the graph to fit the window.</span></span>  
  
-   <span data-ttu-id="a1281-161">**기본 확장** 을 사용하여 모델의 모든 트리에 표시되는 기본 수준 개수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-161">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
-   <span data-ttu-id="a1281-162">데이터 원본을 포함 하 여 특성의 전체 이름을 표시 하려면 **긴 이름 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-162">Select **Show long name** to display the full name of the attribute, including the data source.</span></span> <span data-ttu-id="a1281-163">각 사례에 대한 속성과 다른 데이터 원본에서 사례를 얻은 경우가 아니라면 짧은 이름과 긴 이름은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-163">Short names and long names are the same unless your cases are obtained from a different data source than the attributes for each case.</span></span>  
  
 [<span data-ttu-id="a1281-164">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a1281-164">Back To Top</span></span>](#bkmk_Top)  
  
###  <a name="dependency-network"></a><a name="BKMK_DNetwork"></a><span data-ttu-id="a1281-165">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="a1281-165">Dependency Network</span></span>  
 <span data-ttu-id="a1281-166">**종속성 네트워크** 보기에는 모델의 입력 특성과 예측 가능한 특성 간의 연결이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-166">The **Dependency Network** view displays the connections between the input attributes and the predictable attributes in the model.</span></span>  
  
1.  <span data-ttu-id="a1281-167">뷰어 왼쪽에서 슬라이더를 클릭해서 끕니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-167">Click and drag the slider at the left of the viewer</span></span>  
  
     <span data-ttu-id="a1281-168">맨 위에 모든 연결이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-168">At the top position, all connections are shown.</span></span> <span data-ttu-id="a1281-169">슬라이더를 아래로 끌면 가장 강력한 링크만 뷰어에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-169">When you drag the slider down, only the strongest links are shown in the viewer.</span></span>  
  
2.  <span data-ttu-id="a1281-170">이제 Bike Buyer 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-170">Now click the Bike Buyer node.</span></span>  
  
     <span data-ttu-id="a1281-171">![의사 결정 트리에 대한 종속성 네트워크 보기](media/dm13-dectree-depnet.gif "의사 결정 트리에 대한 종속성 네트워크 보기")</span><span class="sxs-lookup"><span data-stu-id="a1281-171">![Dependency network view for decision trees](media/dm13-dectree-depnet.gif "Dependency network view for decision trees")</span></span>  
  
     <span data-ttu-id="a1281-172">노드를 선택하면 뷰어는 해당 노드와 관련된 종속성을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-172">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="a1281-173">이 사례에서 뷰어는 결과 예측에 도움이 되도록 각 노드를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-173">In this case, the viewer highlights each node that helps predict the outcome.</span></span>  
  
3.  <span data-ttu-id="a1281-174">뷰어에 많은 노드가 포함 되어 있으면 **노드 찾기** 단추를 사용 하 여 특정 노드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-174">If the viewer contains many nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="a1281-175">**노드 찾기** 를 클릭하면 **노드 찾기** 대화 상자가 열리며 여기서 필터를 사용하여 특정 노드를 검색하고 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-175">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
4.  <span data-ttu-id="a1281-176">뷰어의 아래쪽에 있는 범례는 색 코드를 그래프에 있는 종속성 유형에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-176">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="a1281-177">예를 들어 예측 가능한 노드를 선택하면 예측 가능한 노드는 옥색으로 표시되며 선택한 노드를 예측하는 노드는 주황색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-177">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="a1281-178">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a1281-178">Back To Top</span></span>](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a><span data-ttu-id="a1281-179">기본 데이터로 드릴스루</span><span class="sxs-lookup"><span data-stu-id="a1281-179">Drill through to Underlying Data</span></span>  
 <span data-ttu-id="a1281-180">모델에서 기본 사례 데이터로 *드릴스루* 하는 기능을 지 원하는 여러 모델 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-180">Several types of models support the ability to *drill through* from the model to the underlying case data.</span></span> <span data-ttu-id="a1281-181">이는 특정 세그먼트의 고객에게 연락하거나 추가 분석을 위해 데이터를 추출하려는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-181">This can be very useful if you want to contact customers in a particular segment or pull out the data to perform further analysis.</span></span>  
  
##### <a name="get-case-data"></a><span data-ttu-id="a1281-182">사례 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1281-182">Get case data</span></span>  
  
1.  <span data-ttu-id="a1281-183">원하는 데이터가 포함된 트리의 노드를 마우스 오른쪽 단추로 클릭하고 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-183">Right-click the node in the tree that contains the desired data and select one of these options:</span></span>  
  
    -   <span data-ttu-id="a1281-184">**모델 드릴스루**.</span><span class="sxs-lookup"><span data-stu-id="a1281-184">**Drill Through Model**.</span></span> <span data-ttu-id="a1281-185">이 옵션은 선택한 노드에 속하는 사례를 가져와서 Excel의 표로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-185">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="a1281-186">모델 작성에 실제로 사용된 데이터 열만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-186">You get back only the columns of data that were actually used in building the model.</span></span>  
  
    -   <span data-ttu-id="a1281-187">**구조 열을 드릴스루**합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-187">**Drill Through Structure Columns**.</span></span> <span data-ttu-id="a1281-188">이 옵션은 선택한 노드에 속하는 사례를 가져와서 Excel의 표로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-188">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="a1281-189">모델에 사용 되지 않은 열을 포함 하 여 기본 데이터를 작성할 때 사용할 수 있었던 모든 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-189">You get all information that was available in the underlying data when you built it, even of a column wasn't used in the model.</span></span> <span data-ttu-id="a1281-190">고객 주소와 우편 번호를 분석에 필요 없어서 제외했지만 구조에 남겨둔 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-190">For example, you might have excluded the customer address and zip code because those fields are not useful with analysis, but left them in the structure.</span></span>  
  
     <span data-ttu-id="a1281-191">Excel로 돌아가서 데이터를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-191">Return to Excel to view your data.</span></span> <span data-ttu-id="a1281-192">찾아보기 뷰어에서 쿼리를 실행하고, 데이터를 새 워크시트에 표로 저장하고, 결과의 레이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1281-192">The Browse viewer runs a query, saves the data to a table in a new worksheet, and labels the results.</span></span>  
  
     <span data-ttu-id="a1281-193">![드릴스루 결과가 Excel에 저장됨](media/dm13-dectree-drillthroughresults.gif "드릴스루 결과가 Excel에 저장됨")</span><span class="sxs-lookup"><span data-stu-id="a1281-193">![results of drillthrough are saved to Excel](media/dm13-dectree-drillthroughresults.gif "results of drillthrough are saved to Excel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1281-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1281-194">See Also</span></span>  
 [<span data-ttu-id="a1281-195">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="a1281-195">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
