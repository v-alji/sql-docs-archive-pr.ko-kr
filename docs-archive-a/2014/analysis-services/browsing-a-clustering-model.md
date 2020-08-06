---
title: 클러스터링 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d508603acd29fde981bddc5642b54ca9413f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648128"
---
# <a name="browsing-a-clustering-model"></a><span data-ttu-id="5023b-102">클러스터링 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="5023b-102">Browsing a Clustering Model</span></span>
  <span data-ttu-id="5023b-103">**찾아보기**를 사용 하 여 클러스터링 모델을 열면의 클러스터링 뷰어와 비슷한 대화형 뷰어에 모델이 표시 됩니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5023b-103">When you open a clustering model using **Browse**, the model is displayed in an interactive viewer, similar to the clustering viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5023b-104">이 뷰어는 만들어진 클러스터를 탐색하고 클러스터의 특징을 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-104">The viewer helps you explore the clusters that were created, and understand cluster characteristics.</span></span> <span data-ttu-id="5023b-105">또한 개별 세그먼트를 다른 세그먼트 또는 모집단과 비교하고 대조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-105">You can also compare and contrast individual segments with other segments or with the population.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="5023b-106">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="5023b-106">Explore the Model</span></span>  
 <span data-ttu-id="5023b-107">**찾아보기** 창에는 클러스터링 모델을 이해 하 고 기본 데이터 그룹의 특성을 탐색 하는 데 도움이 되는 다음과 같은 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-107">The **Browse** window includes the following tools to help you understand your clustering model and explore the attributes of the underlying data groups:</span></span>  
  
-   [<span data-ttu-id="5023b-108">클러스터 다이어그램</span><span class="sxs-lookup"><span data-stu-id="5023b-108">Cluster Diagram</span></span>](#BKMK_ClusterDiagram)  
  
-   [<span data-ttu-id="5023b-109">클러스터 프로필</span><span class="sxs-lookup"><span data-stu-id="5023b-109">Cluster Profiles</span></span>](#BKMK_ClusterProfiles)  
  
-   [<span data-ttu-id="5023b-110">클러스터 특징</span><span class="sxs-lookup"><span data-stu-id="5023b-110">Cluster Characteristics</span></span>](#BKMK_ClusterCharacteristics)  
  
-   [<span data-ttu-id="5023b-111">클러스터 판별</span><span class="sxs-lookup"><span data-stu-id="5023b-111">Cluster Discrimination</span></span>](#BKMK_ClusterDiscrimination)  
  
 <span data-ttu-id="5023b-112">클러스터링 모델을 사용 하 여 시험해 보려면 샘플 데이터 통합 문서의 학습 탭에 있는 샘플 데이터를 사용 하 고, [&#41;Excel 용 데이터 마이닝 추가 기능](cluster-wizard-data-mining-add-ins-for-excel.md) 및 모든 기본값을 &#40;클러스터 마법사를 사용 하 여 클러스터링 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-112">To experiment with a clustering model, you can use the sample data on the Training tab of the sample data workbook, and build a clustering model using [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and all the defaults.</span></span>  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a><span data-ttu-id="5023b-113">클러스터 다이어그램</span><span class="sxs-lookup"><span data-stu-id="5023b-113">Cluster Diagram</span></span>  
 <span data-ttu-id="5023b-114">**클러스터 다이어그램** 탭은 마이닝 모델에 있는 모든 클러스터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-114">The **Cluster Diagram** tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="5023b-115">데이터 집합에서 검색된 그룹 수와 이러한 그룹이 서로 얼마나 가깝거나 멀게 떨어져 있는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-115">Here you can see how many different groupings were found in your data set, and how near or far they are from each other.</span></span>  
  
##### <a name="explore-the-cluster-diagram"></a><span data-ttu-id="5023b-116">클러스터 다이어그램 탐색</span><span class="sxs-lookup"><span data-stu-id="5023b-116">Explore the cluster diagram</span></span>  
  
1.  <span data-ttu-id="5023b-117">다이어그램에서 클러스터 1을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-117">Click Cluster 1 in the diagram.</span></span>  
  
     <span data-ttu-id="5023b-118">모든 클러스터를 연결하는 회색 선 중에서 선택한 클러스터로 이어지는 선이 변경되어 밝은 파란색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-118">Note how the gray lines connecting all clusters change so that lines leading to the selected cluster are highlighted in bright blue.</span></span>  
  
     <span data-ttu-id="5023b-119">![클러스터 다이어그램 소개](media/dm13-cluster-diagram-intro.gif "클러스터 다이어그램 소개")</span><span class="sxs-lookup"><span data-stu-id="5023b-119">![cluster diagram intro](media/dm13-cluster-diagram-intro.gif "cluster diagram intro")</span></span>  
  
     <span data-ttu-id="5023b-120">두 클러스터를 연결하는 선의 음영은 클러스터의 유사성 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-120">The intensity of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="5023b-121">음영이 옅거나 없으면 두 클러스터가 그다지 유사하지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="5023b-122">선이 짙을수록 두 클러스터 간의 유사성이 더욱 강하다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-122">As the line becomes darker, it indicates that the similarity between the two clusters is stronger.</span></span>  
  
2.  <span data-ttu-id="5023b-123">슬라이더를 클릭하여 클러스터 다이어그램의 왼쪽으로 끌어 뷰어에 표시되는 선의 개수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-123">Click and drag the slider to the left of the cluster diagram, to adjust how many lines the viewer shows.</span></span>  
  
     <span data-ttu-id="5023b-124">슬라이더를 아래로 끌면 클러스터 간의 가장 강력한 링크만 표시되므로</span><span class="sxs-lookup"><span data-stu-id="5023b-124">When you drag the slider down, only the strongest links between clusters are shown.</span></span> <span data-ttu-id="5023b-125">관련된 그룹에 집중하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-125">This helps you focus on related groups.</span></span>  
  
3.  <span data-ttu-id="5023b-126">**클러스터 다이어그램** 창의 오른쪽 위 모퉁이에 있는 **음영 변수** 컨트롤을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-126">Notice the **Shading Variable** control in the upper right corner of the **Cluster Diagram** window.</span></span>  
  
     <span data-ttu-id="5023b-127">기본적으로 **채우기**로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-127">By default, it is set to **Population**.</span></span> <span data-ttu-id="5023b-128">이는 클러스터가 짙을수록 지지도가 커짐을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-128">What this means is that the darker clusters have greater support.</span></span>  
  
4.  <span data-ttu-id="5023b-129">클러스터 위에 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-129">Pause over any cluster with the cursor.</span></span>  
  
     <span data-ttu-id="5023b-130">해당 클러스터의 모집단이 포함된 도구 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-130">A ToolTip is displayed that contains the population of that cluster.</span></span>  
  
5.  <span data-ttu-id="5023b-131">이제 **음영 변수** 드롭다운 목록을 클릭 하 고 **Age** 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-131">Now, click the **Shading Variable** dropdown list and choose the **Age** variable.</span></span> <span data-ttu-id="5023b-132">이렇게 하면 값 목록이 **상태** 텍스트 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-132">As you do so, a list of values appears in the **State** text box.</span></span>  
  
     <span data-ttu-id="5023b-133">이 모델의 입력으로 사용되는 Age 열에는 연속 숫자 값이 포함되어 있지만 클러스터링 목적을 위해 알고리즘에서 항상 숫자를 불연속화합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-133">The Age column used as input to this model contains continuous numeric values, but for the purpose of clustering, the algorithm always discretizes numbers.</span></span> <span data-ttu-id="5023b-134">여기서는 "매우 낮음 ( \<=27)" and "Very High (> = 63)"과 같이 알고리즘이 만든 bin 또는 그룹을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-134">Here you can see the bins, or groups that the algorithm created, such as "Very Low (\<=27)" and "Very High (>=63)".</span></span>  
  
6.  <span data-ttu-id="5023b-135">**상태** 드롭다운 목록에서 **매우 높음** 을 선택 하 고 다이어그램이 어떻게 변경 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-135">From the **State** dropdown lists, select **Very High** and see how the diagram changes.</span></span>  
  
     <span data-ttu-id="5023b-136">음영 변수를 변경하여 이 대상 연령 그룹이 많이 포함된 클러스터와 이 연령 그룹의 고객이 매우 적게 포함된 클러스터를 한눈에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-136">By changing the shading variable, you can see at a glance which clusters contain more of this targeted age group, and which clusters contain very few customers in this age group.</span></span>  
  
     <span data-ttu-id="5023b-137">![클러스터 다이어그램을 수정하여 기간 표시](media/dm13-cluster-diagramshadebyage.gif "클러스터 다이어그램을 수정하여 기간 표시")</span><span class="sxs-lookup"><span data-stu-id="5023b-137">![Modify the cluster diagram to show age](media/dm13-cluster-diagramshadebyage.gif "Modify the cluster diagram to show age")</span></span>  
  
     <span data-ttu-id="5023b-138">음영이 짙을수록 해당 클러스터의 대상 특성 및 값 분포의 모집단이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-138">The darker the shading, the larger the proportion of the target attribute and value distribution that cluster.</span></span>  
  
7.  <span data-ttu-id="5023b-139">**음영 변수가** Age >65로 설정 된 경우 가장 어두운 회색으로 표시 된 클러스터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-139">Locate the cluster that is shaded darkest when the **Shading Variable** is set to Age >65.</span></span>  
  
     <span data-ttu-id="5023b-140">클러스터 위로 마우스를 가져갑니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-140">Hover the mouse over the cluster.</span></span>  
  
     <span data-ttu-id="5023b-141">도구 설명에 표시된 값이 이제 이 클러스터에서 65세가 넘는 고객의 모집단을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-141">The value displayed in the ToolTip now shows you the population of customers in this cluster who are over 65.</span></span>  
  
8.  <span data-ttu-id="5023b-142">클러스터를 마우스 오른쪽 단추로 클릭 하 고 **클러스터 이름 바꾸기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-142">Right-click the cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="5023b-143">설명 (예: **65 이상**)의 새 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-143">Type a new name that is descriptive, such as **Over 65**.</span></span> <span data-ttu-id="5023b-144">새 이름이 모델과 함께 서버에 저장되고 다른 클러스터링 뷰에서 클러스터를 식별하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-144">The new name is saved with the model to the server and can be used for identifying the cluster in the other clustering views.</span></span>  
  
 [<span data-ttu-id="5023b-145">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="5023b-145">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a><span data-ttu-id="5023b-146">클러스터 프로필</span><span class="sxs-lookup"><span data-stu-id="5023b-146">Cluster Profiles</span></span>  
 <span data-ttu-id="5023b-147">**클러스터 프로필** 탭을 사용 하 여 모든 클러스터의 구성을를 한눈에 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-147">The **Cluster Profiles** tab lets you compare the makeup of all clusters at a glance.</span></span> <span data-ttu-id="5023b-148">모델에 익숙해지면 이곳에서 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-148">This is a good place to start when you are getting familiar with the model.</span></span> <span data-ttu-id="5023b-149">이 뷰는 특정 클러스터를 탐색하다가 관련 클러스터를 찾아야 한다고 이후에 결정하는 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-149">This view is also useful later on, if you have been exploring a particular cluster and decide you need to find related ones.</span></span>  
  
 <span data-ttu-id="5023b-150">**클러스터 프로필** 은 클러스터가 서로 어떻게 다른 지에 대 한 유용한 개요도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-150">**Cluster Profiles** also gives you a good overview of how the clusters are different from each other.</span></span> <span data-ttu-id="5023b-151">따라서 이 뷰를 사용하여 각 클러스터에 설명이 포함된 이름을 간편하게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-151">Therefore, you might find it convenient to use this view to give each cluster a descriptive name.</span></span>  
  
##### <a name="explore-the-cluster-profiles"></a><span data-ttu-id="5023b-152">클러스터 프로필 탐색</span><span class="sxs-lookup"><span data-stu-id="5023b-152">Explore the cluster profiles</span></span>  
  
1.  <span data-ttu-id="5023b-153">**상태** 열에서 직업의 셀을 클릭 하 여 직업에 대 한 모든 값의 목록을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-153">Click the cell for Occupations, in the **States** column, to see the list of all values for Occupation.</span></span>  
  
2.  <span data-ttu-id="5023b-154">이제 클러스터 프로필에서 Occupation 위로 커서를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-154">Now move the cursor over Occupation in the cluster profiles.</span></span>  
  
     <span data-ttu-id="5023b-155">도구 설명에 해당 클러스터의 직업 분포가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-155">The ToolTip shows the distribution of occupations in that cluster.</span></span>  
  
     <span data-ttu-id="5023b-156">![도구 설명 또는 범례에서 자세한 값 보기](media/dm13-cluster-profile-age-tooltip.gif "도구 설명 또는 범례에서 자세한 값 보기")</span><span class="sxs-lookup"><span data-stu-id="5023b-156">![View detailed values in Tooltips or in Legend](media/dm13-cluster-profile-age-tooltip.gif "View detailed values in Tooltips or in Legend")</span></span>  
  
     <span data-ttu-id="5023b-157">일부 클러스터 (예: 그래픽의)에서 직업의 목록이 완전 하지 않으며 일부 직업는 **다른**레이블로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-157">Notice that, in some clusters (such as the one in the graphic), the list of occupations is not complete, and some occupations are replaced with the label, **Other**.</span></span>  
  
     <span data-ttu-id="5023b-158">히스토그램의 많은 작은 막대를 구별하기가 어려울 수 있기 때문에 이것은 의도적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-158">This is by design, because it can be hard to tell the difference between many small bars in a histogram.</span></span> <span data-ttu-id="5023b-159">기본적으로 가장 높은 중요도의 막대만 유지 되 고 나머지 막대는 회색 **다른** 버킷으로 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-159">By default only the bars of highest importance are retained, and the remaining bars are grouped together into a gray **Other** bucket.</span></span>  
  
     <span data-ttu-id="5023b-160">히스토그램에 표시 되는 막대의 수를 변경 하려면 **히스토그램 막대**옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-160">To change the number of bars that are visible in any histogram, use the option **Histogram bars**.</span></span>  
  
3.  <span data-ttu-id="5023b-161">**Age** 열은 다른 열과 다르게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-161">Note that the **Age** column looks different from the others.</span></span> <span data-ttu-id="5023b-162">Age를 나타내는 데 사용되는 차트에서 다이아몬드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-162">Click the diamond in the chart used to represent Age.</span></span>  
  
     <span data-ttu-id="5023b-163">Age 열에는 원래 연속 숫자만 포함되어 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-163">The column Age originally contained only continuous numbers.</span></span> <span data-ttu-id="5023b-164">클러스터링 알고리즘은 불연속 값을 필요로 하므로 Age 열의 숫자 값을 값의 분포에 따라 제한된 수의 연령 그룹으로 나누었습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-164">The clustering algorithm requires discrete values, so it grouped the numeric values in the Age column into a limited number of age groups, based on the distribution of values.</span></span>  
  
4.  <span data-ttu-id="5023b-165">클러스터 프로필에서 다이아몬드 차트 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-165">Click one of the diamond charts in a cluster profile.</span></span>  
  
     <span data-ttu-id="5023b-166">이러한 다이아몬드 차트는 원본 데이터가 연속 숫자 값을 사용하는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-166">These diamond charts are displayed only when the source data uses continuous numeric values.</span></span> <span data-ttu-id="5023b-167">다이아몬드 차트는 각 클러스터에서 해당 값의 평균 및 표준 편차를 비롯한 몇 가지 유용한 기술 통계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-167">The diamond charts provide some useful descriptive statistics, including the mean and standard deviation for that value in each cluster:</span></span>  
  
    -   <span data-ttu-id="5023b-168">다이아몬드 차트의 선은 특성 값의 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-168">The line in the diamond chart represents the range of values for the attribute.</span></span> <span data-ttu-id="5023b-169">값은 **프로필** 차트의 왼쪽에 있는 **상태** 열에도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-169">The values are also shown in the **States** column at the left of the **Profiles** chart.</span></span>  
  
    -   <span data-ttu-id="5023b-170">다이아몬드의 중심은 노드의 평균에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-170">The center of the diamond is positioned at the mean for the node.</span></span>  
  
    -   <span data-ttu-id="5023b-171">다이아몬드의 너비는 해당 노드에서 특성의 분산을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-171">The width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="5023b-172">따라서 다이아몬드가 얇을수록 노드에서 더욱 정확한 예측을 도출할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-172">Therefore, a thinner diamond indicates that the node can create a more accurate prediction.</span></span>  
  
5.  <span data-ttu-id="5023b-173">그래프에서 더 많은 공간을 만들려면 즉시 볼 필요가 없는 클러스터를 마우스 오른쪽 단추로 클릭 하 고 **열 숨기기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-173">To make more room in the graph, right-click a cluster you don't need to view right away, and select **Hide Column**.</span></span> <span data-ttu-id="5023b-174">이렇게 하면 모델에서 삭제 되지 않으므로 열이 일시적으로 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-174">This doesn't delete it from the model, just collapses the column temporarily.</span></span>  
  
     <span data-ttu-id="5023b-175">숨겨진 클러스터를 보려면 열 가장자리를 클릭 하 여 끌거나 목록 **, 클러스터 목록**에서 클러스터 이름을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-175">To view clusters that you've hidden, you can click and drag the column edge, or select the cluster name from the list, **More clusters**.</span></span>  
  
6.  <span data-ttu-id="5023b-176">Bike Buyer를 찾을 때까지 특성 목록을 아래로 스크롤한 다음 Yes 값의 비율이 가장 높은 클러스터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-176">Scroll down the attribute list till you find Bike Buyer, and then find the cluster that has the highest percentage of Yes values.</span></span>  
  
     <span data-ttu-id="5023b-177">이름을 바꿀 클러스터의 열 머리글을 마우스 오른쪽 단추로 클릭 하 고 **클러스터 이름 바꾸기**를 선택 하 고 **자전거 구매자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-177">Right-click the column heading for the cluster that you want to rename, select **Rename cluster**, and type **Bike Buyers**.</span></span>  
  
     <span data-ttu-id="5023b-178">새 클러스터 이름이 모든 뷰에서 유지되고 서버에서는 모델을 다시 처리할 때까지 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-178">The new cluster name is persisted in all views, and on the server, until you reprocess the model.</span></span>  
  
     <span data-ttu-id="5023b-179">![차트를 쉽게 사용할 수 있도록 클러스터 이름 바꾸기](media/dm13-cluster-rename.gif "차트를 쉽게 사용할 수 있도록 클러스터 이름 바꾸기")</span><span class="sxs-lookup"><span data-stu-id="5023b-179">![Rename clusters to make chart easier to use](media/dm13-cluster-rename.gif "Rename clusters to make chart easier to use")</span></span>  
  
 <span data-ttu-id="5023b-180">**팁**</span><span class="sxs-lookup"><span data-stu-id="5023b-180">**Tips**</span></span>  
  
-   <span data-ttu-id="5023b-181">해당 클러스터에 대한 중요도 순으로 특성을 정렬하려면 열 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-181">Click a column heading to sort the attributes in order of importance for that cluster.</span></span>  
  
-   <span data-ttu-id="5023b-182">뷰어에서 열을 다시 정렬하려면 열을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-182">Drag columns to reorder them in the viewer.</span></span>  
  
-   <span data-ttu-id="5023b-183">**마이닝 범례**에서 자세한 통계를 보려면 프로필 차트에서 아무 셀 이나 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-183">Click any cell in the profiles chart to view detailed statistics in the **Mining Legend**.</span></span>  
  
-   <span data-ttu-id="5023b-184">셀을 마우스 오른쪽 단추로 클릭 하 고 **드릴스루 모델 열** 을 선택 하 여 기본 데이터를 Excel의 새 워크시트에 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-184">Right-click any cell and select **Drillthrough model columns** to output the underlying data to a new worksheet in Excel.</span></span>  
  
-   <span data-ttu-id="5023b-185">클러스터의 열 제목을 마우스 오른쪽 단추로 클릭 하 고 **구조 데이터로 드릴스루** 를 선택 하 여 모델에 포함 되지 않은 클러스터 구성원에 대 한 자세한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-185">Right-click the cluster's column heading and select **Drillthrough to structure data** to get detailed information about the cluster members that wasn't included in the model.</span></span>  
  
     <span data-ttu-id="5023b-186">예를 들어 고객을 프로 파일링 하는 경우에는 분석에 유용 하지 않기 때문에 기본 데이터 (마이닝 구조)에 연락처 정보를 그대로 둘 수 있지만 모델에는 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-186">For example, if you are profiling customers, you might leave the contact information in the underlying data (the mining structure) but not include it in the model, because it's not useful for analysis.</span></span> <span data-ttu-id="5023b-187">그러나 고객이 클러스터에 할당된 후 드릴스루를 사용하여 세부 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-187">However, after customers have been assigned to clusters, you can view the detailed data by using drillthrough.</span></span>  
  
 [<span data-ttu-id="5023b-188">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="5023b-188">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a> <span data-ttu-id="5023b-189">클러스터 특징</span><span class="sxs-lookup"><span data-stu-id="5023b-189">Cluster Characteristics</span></span>  
 <span data-ttu-id="5023b-190">클러스터 특징 뷰를 사용하면 단일 클러스터를 실제로 탐색하여 이 데이터 그룹의 가장 큰 특징을 결정하는 특성을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-190">The Cluster Characteristics view lets you really explore a single cluster, to find which attributes most strongly characterize this group of data.</span></span>  
  
##### <a name="explore-the-cluster-characteristics"></a><span data-ttu-id="5023b-191">클러스터 특징 탐색</span><span class="sxs-lookup"><span data-stu-id="5023b-191">Explore the cluster characteristics</span></span>  
  
1.  <span data-ttu-id="5023b-192">**클러스터** 목록에서 **Over 65** 클러스터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-192">Select the **Over 65** cluster from the **Cluster** list.</span></span>  
  
     <span data-ttu-id="5023b-193">클러스터를 선택한 후 해당 클러스터를 구성하는 특징을 자세히 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-193">After you select a cluster, you can see in detail the characteristics that make up that specific cluster.</span></span>  
  
     <span data-ttu-id="5023b-194">클러스터에 포함된 특성은 **변수** 열에 나열되어 있으며 나열된 특성의 상태는 **값** 열에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-194">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span>  
  
     <span data-ttu-id="5023b-195">특성 상태는 중요도 순으로 나열 되 고 **확률 열에** 색이 지정 된 막대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-195">Attribute states are listed in order of importance, accompanied by their probability in this cluster, represented as a colored bar in the **Probability** column.</span></span>  
  
     <span data-ttu-id="5023b-196">![클러스터링 모델의 특징](media/dm13-cluster-characteristics.gif "클러스터링 모델의 특징")</span><span class="sxs-lookup"><span data-stu-id="5023b-196">![Characteristics of a clustering model](media/dm13-cluster-characteristics.gif "Characteristics of a clustering model")</span></span>  
  
2.  <span data-ttu-id="5023b-197">**Variables** 열을 클릭 하 여 특성을 기준으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-197">Click the **Variables** column to sort by attribute.</span></span>  
  
     <span data-ttu-id="5023b-198">정렬 변수를 변경하여 소득이나 자동차 소유와 같은 변수의 값이 그룹에서 어떻게 분포되어 있는지를 보다 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-198">By changing the sort variable, you can more easily see how values for variables such as income or car ownership are distributed in the group.</span></span>  
  
3.  <span data-ttu-id="5023b-199">**Excel로 복사를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-199">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="5023b-200">선택한 클러스터의 특징이 포함된 새 워크시트가 통합 문서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-200">A new worksheet is added to your workbook that contains the characteristics of the selected cluster.</span></span>  
  
4.  <span data-ttu-id="5023b-201">이제 **자전거 구매자**목록에서 다른 클러스터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-201">Now choose a different cluster from the list, **Bike Buyers**.</span></span>  
  
5.  <span data-ttu-id="5023b-202">**Excel로 복사를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-202">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="5023b-203">새 클러스터 특징 차트가 자체 워크시트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-203">Note that the new cluster characteristics chart is added on its own worksheet.</span></span> <span data-ttu-id="5023b-204">다른 프로필과 동일한 워크시트로 이동 하 여 보다 쉽게 비교할 수 있습니다 .이 작업은 다음 단계에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-204">You can move it onto the same worksheet as the other profile to make it easier to compare them, which you'll do in the next step.</span></span>  
  
 <span data-ttu-id="5023b-205">**팁**</span><span class="sxs-lookup"><span data-stu-id="5023b-205">**Tips**</span></span>  
  
-   <span data-ttu-id="5023b-206">65 클러스터에서 고객의 주요 특징은 제품을 구입 하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-206">Note that the primary characteristic of the customer in the Over 65 cluster is that they don't buy your product!</span></span> <span data-ttu-id="5023b-207">그 이유를 알고 싶은 경우 클러스터를 탐색하고 그룹을 비교하거나, 의사 결정 트리 모델 또는 Naïve Bayes 모델과 같이 원인과 결과를 탐색하는 데 유용한 알고리즘을 사용하여 관련 모델을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-207">If you want to know why this is so, you can browse clusters and compare groups, or you might create a related model using an algorithm that is good at exploring causes and outcomes, such as a decision tree model or a Naïve Bayes model.</span></span>  
  
-   <span data-ttu-id="5023b-208">이 클러스터(또는 모든 클러스터)에 대한 특성 및 확률의 전체 목록을 얻으려면 쿼리를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-208">If you want to get a complete list of attributes and probabilities for this cluster (or all clusters) you can create a query.</span></span> <span data-ttu-id="5023b-209">클러스터링 모델에 대 한 쿼리의 예는 [클러스터링 모델 쿼리 예제](data-mining/clustering-model-query-examples.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5023b-209">For examples of queries on clustering models, see [Clustering Model Query Examples](data-mining/clustering-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="5023b-210">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="5023b-210">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a><span data-ttu-id="5023b-211">클러스터 판별</span><span class="sxs-lookup"><span data-stu-id="5023b-211">Cluster Discrimination</span></span>  
 <span data-ttu-id="5023b-212">**클러스터 판별** 탭을 사용 하 여 두 클러스터의 특성을 비교 하거나 클러스터와 데이터 집합의 다른 모든 사례 간에 특성을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-212">You use the **Cluster Discrimination** tab to compare attributes between two clusters, or between a cluster and all the other cases in the data set.</span></span>  
  
 <span data-ttu-id="5023b-213">이 뷰어의 기능을 강조 하기 위해 **클러스터 특징** 보기를 기반으로 만든 Excel의 side-by-side 테이블과 비교해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-213">To highlight the features of this viewer, we'll compare it to the side-by-side tables in Excel that you created based on the **Cluster Characteristics** view.</span></span>  
  
##### <a name="explore-cluster-discrimination"></a><span data-ttu-id="5023b-214">클러스터 판별 탐색</span><span class="sxs-lookup"><span data-stu-id="5023b-214">Explore cluster discrimination</span></span>  
  
1.  <span data-ttu-id="5023b-215">**클러스터 1** 및 **클러스터 2** 목록을 사용하여 비교할 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-215">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span>  
  
    -   <span data-ttu-id="5023b-216">클러스터 1에서 Over 65를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-216">For Cluster 1, select Over 65.</span></span>  
  
    -   <span data-ttu-id="5023b-217">클러스터 2에서 Bike Buyers를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-217">For Cluster 2, select Bike Buyers.</span></span>  
  
     <span data-ttu-id="5023b-218">두 클러스터에 대한 비교가 다음 그래픽과 유사하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-218">The comparison should look similar to the following graphic.</span></span>  
  
     <span data-ttu-id="5023b-219">![모델에서 클러스터 비교](media/dm13-cluster-compareclusters.gif "모델에서 클러스터 비교")</span><span class="sxs-lookup"><span data-stu-id="5023b-219">![comparing clusters in a model](media/dm13-cluster-compareclusters.gif "comparing clusters in a model")</span></span>  
  
     <span data-ttu-id="5023b-220">내부적으로 **클러스터 판별** 뷰어는 데이터 마이닝 서버에 복잡 한 쿼리를 전송 하 여 두 그룹을 구분 하는 데 가장 중요 한 특성을 추출 하므로 두 고객 집합을 보다 쉽게 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-220">Note that, under the covers, the **Cluster Discrimination** viewer sends complex queries to the data mining server, to extract the attributes that are most important in distinguishing between the two groups, making it easier to compare two sets of customers.</span></span>  
  
2.  <span data-ttu-id="5023b-221">**우위 ...** 열 중 하나를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-221">Click either of the **Favors...** columns.</span></span>  
  
     <span data-ttu-id="5023b-222">특성 및 값 목록의 오른쪽에 있는 막대가 선택한 클러스터의 특징으로 가장 중요한 기능이나 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-222">The bar to the right of the attribute and value list shows which features or values are most important as a characteristic of the selected cluster.</span></span>  
  
3.  <span data-ttu-id="5023b-223">이제 Excel에서 목록을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-223">Now compare the lists in Excel.</span></span>  
  
     <span data-ttu-id="5023b-224">![연결 모델에 대한 종속성 네트워크 그래프](media/dm13-comparing-profiles-in-excel.gif "연결 모델에 대한 종속성 네트워크 그래프")</span><span class="sxs-lookup"><span data-stu-id="5023b-224">![Dependency network graph for an association model](media/dm13-comparing-profiles-in-excel.gif "Dependency network graph for an association model")</span></span>  
  
     <span data-ttu-id="5023b-225">뷰어에서 이미지를 작성하는 데 사용된 기본 통계가 Excel에 테이블로 저장되기 때문에 실제 확률 값을 필터링 및 정렬하고 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-225">Because the underlying statistics that were used to build the image in the viewer are saved to Excel as tables, you can filter and sort, and view the actual probability values.</span></span>  
  
     <span data-ttu-id="5023b-226">Excel을 사용하는 것 외에도 데이터 요소를 볼 수 있을 뿐 아니라 그래프를 광범위하게 수정하고 개선할 수도 있는 Visio용 클러스터 뷰어를 사용해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-226">In addition to using Excel, we recommend that you try the cluster viewer for Visio, which also allows you to not just view data points but also extensively modify and enhance the graph.</span></span> <span data-ttu-id="5023b-227">자세한 내용은 [클러스터 다이어그램 연습 &#40;데이터 마이닝 추가 기능&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5023b-227">For more information, see [Cluster Diagram Walkthrough &#40;Data Mining Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).</span></span>  
  
 <span data-ttu-id="5023b-228">**팁**</span><span class="sxs-lookup"><span data-stu-id="5023b-228">**Tips**</span></span>  
  
 <span data-ttu-id="5023b-229">고객 그룹에 대 한 정보를 파악 한 후에는 [가상 시나리오 &#40;excel 용 테이블 분석 도구&#41;](what-if-scenario-table-analysis-tools-for-excel.md) 또는 [목표 검색&#41;&#40;시나리오](goal-seek-scenario-table-analysis-tools-for-excel.md) 를 사용 하 여 결과에 영향을 주기 위해 변경 될 수 있는 모델 요소를 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5023b-229">After getting some insights into groups of customers, try using the [What-If Scenario &#40;Table Analysis Tools for Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) or [Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) tools, to explore factors in the model that might be changed to affect the outcome.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5023b-230">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5023b-230">See Also</span></span>  
 <span data-ttu-id="5023b-231">[Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="5023b-231">[Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="5023b-232">클러스터 마법사는 Excel 용 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="5023b-232">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
