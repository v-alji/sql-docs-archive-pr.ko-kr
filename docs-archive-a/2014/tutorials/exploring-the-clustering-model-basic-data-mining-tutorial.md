---
title: 클러스터링 모델 탐색 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cca9d395fece59f607c8faf209128b9d32663a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742720"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a><span data-ttu-id="8c4c8-102">클러스터링 모델 탐색(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="8c4c8-102">Exploring the Clustering Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="8c4c8-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]클러스터링 알고리즘은 사례를 유사한 특성을 포함 하는 클러스터로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm groups cases into clusters that contain similar characteristics.</span></span> <span data-ttu-id="8c4c8-104">이러한 그룹화는 데이터 탐색, 데이터 내 잘못된 부분 식별, 예측 만들기 등에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-104">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>  
  
 <span data-ttu-id="8c4c8-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] 클러스터 뷰어는 클러스터링 마이닝 모델 탐색 시 사용할 수 있는 다음과 같은 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a><span data-ttu-id="8c4c8-106">클러스터 다이어그램 탭</span><span class="sxs-lookup"><span data-stu-id="8c4c8-106">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="8c4c8-107">클러스터 다이어그램 탭에서는 마이닝 모델에 있는 클러스터를 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-107">The Cluster Diagram tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="8c4c8-108">클러스터 사이의 선은 "일치 정도"를 나타내며 클러스터가 얼마나 비슷한지에 따라 음영 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-108">The lines between the clusters represent "closeness" and are shaded based on how similar the clusters are.</span></span> <span data-ttu-id="8c4c8-109">각 클러스터의 실제 색은 클러스터에 있는 변수와 상태의 빈도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-109">The actual color of each cluster represents the frequency of the variable and the state in the cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a><span data-ttu-id="8c4c8-110">클러스터 다이어그램 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="8c4c8-110">To explore the model in the Cluster Diagram tab</span></span>  
  
1.  <span data-ttu-id="8c4c8-111">**마이닝 모델 뷰어** 탭의 위쪽에 있는 **마이닝 모델** 목록을 사용 하 여 모델로 전환할 수 `TM_Clustering` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-111">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_Clustering` model.</span></span>  
  
2.  <span data-ttu-id="8c4c8-112">**뷰어** 목록에서 **Microsoft 클러스터 뷰어**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-112">In the **Viewer** list, select **Microsoft Cluster Viewer**.</span></span>  
  
3.  <span data-ttu-id="8c4c8-113">**음영 변수** 상자에서 **자전거 구매자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-113">In the **Shading Variable** box, select **Bike Buyer**.</span></span>  
  
     <span data-ttu-id="8c4c8-114">기본 변수는 **채우기**이지만이를 모델의 임의의 특성으로 변경 하 여 원하는 특성을 가진 멤버를 포함 하는 클러스터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-114">The default variable is **Population**, but you can change this to any attribute in the model, to discover which clusters contain members that have the attributes you want.</span></span>  
  
4.  <span data-ttu-id="8c4c8-115">**상태** 상자에서 **1** 을 선택 하 여 자전거를 구매한 경우를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-115">Select **1** in the **State** box to explore those cases where a bike was purchased.</span></span>  
  
     <span data-ttu-id="8c4c8-116">**밀도** 범례는 음영 변수 및 상태에서 선택한 특성 상태 쌍의 밀도를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-116">The **Density** legend describes the density of the attribute state pair selected in the Shading Variable and the State.</span></span> <span data-ttu-id="8c4c8-117">이 예제에서는 가장 어두운 음영이 있는 clusterwith 최고 비율의 자전거 구매자가 있음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-117">In this example it tells us that the clusterwith the darkest shading has the highest percentage of bike buyers.</span></span>  
  
5.  <span data-ttu-id="8c4c8-118">음영이 가장 짙은 클러스터 위에 마우스를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-118">Pause your mouse over the cluster with the darkest shading.</span></span>  
  
     <span data-ttu-id="8c4c8-119">도구 설명에서 특성이 `Bike Buyer = 1`인 사례의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-119">A tooltip displays the percentage of cases that have the attribute, `Bike Buyer = 1`.</span></span>  
  
6.  <span data-ttu-id="8c4c8-120">밀도가 가장 높은 클러스터를 선택 하 고, 클러스터를 마우스 오른쪽 단추로 클릭 하 고, **클러스터 이름 바꾸기** 를 선택 하 고, 나중에 확인을 위해 **자전거 구매자 높음** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-120">Select the cluster that has the highest density, right-click the cluster, select **Rename Cluster** and type **Bike Buyers High** for later identification.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="8c4c8-121">음영이 가장 밝고 밀도가 가장 낮은 클러스터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-121">Find the cluster that has the lightest shading (and the lowest density).</span></span> <span data-ttu-id="8c4c8-122">클러스터를 마우스 오른쪽 단추로 클릭 하 고 **클러스터 이름 바꾸기** 를 선택 하 고 **자전거 구매자 낮음**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-122">Right-click the cluster, select **Rename Cluster** and type **Bike Buyers Low**.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="8c4c8-123">**자전거 구매자 상위** 클러스터를 클릭 하 고 다른 클러스터에 대 한 연결을 명확 하 게 보여 주는 창 영역으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-123">Click the **Bike Buyers High** cluster and drag it to an area of the pane that will give you a clear view of its connections to the other clusters.</span></span>  
  
     <span data-ttu-id="8c4c8-124">클러스터를 선택하면 이 클러스터를 다른 클러스터에 연결하는 선이 강조 표시되므로 이 클러스터에 대한 모든 관계를 쉽게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-124">When you select a cluster, the lines that connect this cluster to other clusters are highlighted, so that you can easily see all the relationships for this cluster.</span></span> <span data-ttu-id="8c4c8-125">클러스터를 선택하지 않은 경우 다이어그램에 있는 모든 클러스터 간 관계의 밀접도는 선이 짙은 정도로 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-125">When the cluster is not selected, you can tell by the darkness of the lines how strong the relationships are amongst all the clusters in the diagram.</span></span> <span data-ttu-id="8c4c8-126">음영이 옅거나 없으면 두 클러스터가 그다지 유사하지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-126">If the shading is light or nonexistent, the clusters are not very similar.</span></span>  
  
9. <span data-ttu-id="8c4c8-127">네트워크 왼쪽의 슬라이더를 사용하여 약한 링크를 필터로 제외시키고 가장 밀접한 관계가 있는 클러스터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-127">Use the slider to the left of the network, to filter out the weaker links and find the clusters with the closest relationships.</span></span> <span data-ttu-id="8c4c8-128">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 마케팅 부서에서 대상 메일을 배달하기 위한 최상의 방법을 결정할 때 유사한 클러스터를 함께 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-128">The [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department might want to combine similar clusters together when determining the best method for delivering the targeted mailing.</span></span>  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a><span data-ttu-id="8c4c8-129">클러스터 프로필 탭</span><span class="sxs-lookup"><span data-stu-id="8c4c8-129">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="8c4c8-130">**클러스터 프로필** 탭에서는 모델의 전체 보기를 제공 합니다 `TM_Clustering` .</span><span class="sxs-lookup"><span data-stu-id="8c4c8-130">The **Cluster Profiles** tab provides an overall view of the `TM_Clustering` model.</span></span> <span data-ttu-id="8c4c8-131">**클러스터 프로필** 탭에는 모델의 각 클러스터에 대 한 열이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-131">The **Cluster Profiles** tab contains a column for each cluster in the model.</span></span> <span data-ttu-id="8c4c8-132">첫 번째 열에는 적어도 하나의 클러스터와 연결된 특성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-132">The first column lists the attributes that are associated with at least one cluster.</span></span> <span data-ttu-id="8c4c8-133">뷰어의 나머지 부분에는 각 클러스터에 대한 특성의 상태 분포가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-133">The rest of the viewer contains the distribution of the states of an attribute for each cluster.</span></span> <span data-ttu-id="8c4c8-134">불연속 변수의 분포는 **히스토그램 막대** 목록에 표시 되는 최대 막대 수가 있는 색이 지정 된 막대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-134">The distribution of a discrete variable is shown as a colored bar with the maximum number of bars displayed in the **Histogram bars** list.</span></span> <span data-ttu-id="8c4c8-135">연속 특성은 각 클러스터의 평균과 표준 편차를 나타내는 다이아몬드 차트를 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-135">Continuous attributes are displayed with a diamond chart, which represents the mean and standard deviation in each cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a><span data-ttu-id="8c4c8-136">클러스터 프로필 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="8c4c8-136">To explore the model in the Cluster Profiles tab</span></span>  
  
1.  <span data-ttu-id="8c4c8-137">**히스토그램** 막대를 **5**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-137">Set **Histogram** bars to **5**.</span></span>  
  
     <span data-ttu-id="8c4c8-138">이 모델에서 5는 어느 한 변수의 상태에 지정할 수 있는 최대값입니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-138">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
2.  <span data-ttu-id="8c4c8-139">**마이닝 범례** 가 **특성 프로필**의 표시를 차단 하는 경우이를 밖으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-139">If the **Mining Legend** blocks the display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="8c4c8-140">**자전거 구매자 High** 열을 선택 하 여 **모집단** 열의 오른쪽으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-140">Select the **Bike Buyers High** column and drag it to the right of the **Population** column.</span></span>  
  
4.  <span data-ttu-id="8c4c8-141">**자전거 구매자 Low** 열을 선택 하 고 **자전거 구매자 상위** 열의 오른쪽으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-141">Select the **Bike Buyers Low** column and drag it to the right of the **Bike Buyers High** column.</span></span>  
  
5.  <span data-ttu-id="8c4c8-142">**자전거 구매자 상위** 열을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-142">Click the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="8c4c8-143">**Variables** 열은 해당 클러스터의 중요도 순으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-143">The **Variables** column is sorted in order of importance for that cluster.</span></span> <span data-ttu-id="8c4c8-144">열을 스크롤하고 Bike Buyer High 클러스터의 특징을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-144">Scroll through the column and review characteristics of the Bike Buyer High cluster.</span></span> <span data-ttu-id="8c4c8-145">예를 들어 이 클러스터에 속한 사람들은 통근 거리가 짧을 가능성이 더 많습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-145">For example, they are more likely to have a short commute.</span></span>  
  
6.  <span data-ttu-id="8c4c8-146">**자전거 구매자 High** 열에서 **Age** 셀을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-146">Double-click the **Age** cell in the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="8c4c8-147">**마이닝 범례** 에는 보다 자세한 보기가 표시 되며 이러한 고객의 연령 범위와 평균 나이가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-147">The **Mining Legend** displays a more detailed view and you can see the age range of these customers as well as the mean age.</span></span>  
  
7.  <span data-ttu-id="8c4c8-148">**자전거 구매자 Low** 열을 마우스 오른쪽 단추로 클릭 하 고 **열 숨기기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-148">Right-click the **Bike Buyers Low** column and select **Hide Column**.</span></span>  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a><span data-ttu-id="8c4c8-149">클러스터 특징 탭</span><span class="sxs-lookup"><span data-stu-id="8c4c8-149">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="8c4c8-150">**클러스터 특징** 탭을 사용 하 여 클러스터를 구성 하는 특성을 자세히 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-150">With the **Cluster Characteristics** tab, you can examine in more detail the characteristics that make up a cluster.</span></span> <span data-ttu-id="8c4c8-151">클러스터 프로필 탭에서 모든 클러스터의 특징을 비교하는 대신 한 번에 하나의 클러스터를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-151">Instead of comparing the characteristics of all of the clusters (as in the Cluster Profiles tab), you can explore one cluster at a time.</span></span> <span data-ttu-id="8c4c8-152">예를 들어 **클러스터** 목록에서 **자전거 구매자** 를 선택 하는 경우이 클러스터의 고객 특징을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-152">For example, if you select **Bike Buyers High** from the **Cluster** list, you can see the characteristics of the customers in this cluster.</span></span> <span data-ttu-id="8c4c8-153">클러스터 프로필 뷰어와 다르게 표시되지만 결과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-153">Though the display is different from the Cluster Profiles viewer, the findings are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c4c8-154">**Holdoutseed**에 대 한 초기 값을 설정 하지 않으면 모델을 처리할 때마다 결과가 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-154">Unless you set an initial value for **holdoutseed**, results will vary each time you process the model.</span></span> <span data-ttu-id="8c4c8-155">자세한 내용은 [HoldoutSeed 요소](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-155">For more information, see [HoldoutSeed Element](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span></span>  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a><span data-ttu-id="8c4c8-156">클러스터 판별 탭</span><span class="sxs-lookup"><span data-stu-id="8c4c8-156">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="8c4c8-157">**클러스터 판별** 탭을 사용 하 여 한 클러스터를 다른 클러스터와 구별 하는 특성을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-157">With the **Cluster Discrimination** tab, you can explore the characteristics that distinguish one cluster from another.</span></span> <span data-ttu-id="8c4c8-158">**클러스터 1** 목록에서 두 개의 클러스터를 선택 하 고 클러스터 **2** 목록에서 클러스터를 선택 하면 뷰어는 클러스터 간의 차이점을 계산 하 고 클러스터를 가장 많이 구분 하는 특성 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-158">After you select two clusters, one from the **Cluster 1** list, and one from the **Cluster 2** list, the viewer calculates the differences between the clusters and displays a list of the attributes that distinguish the clusters most.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a><span data-ttu-id="8c4c8-159">클러스터 판별 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="8c4c8-159">To explore the model in the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="8c4c8-160">**클러스터 1** 상자에서 **자전거 구매자 높음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-160">In the **Cluster 1** box, select **Bike Buyers High**.</span></span>  
  
2.  <span data-ttu-id="8c4c8-161">**클러스터 2** 상자에서 **자전거 구매자 낮음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-161">In the **Cluster 2** box, select **Bike Buyers Low**.</span></span>  
  
3.  <span data-ttu-id="8c4c8-162">사전순으로 정렬 하려면 **변수** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-162">Click **Variables** to sort alphabetically.</span></span>  
  
     <span data-ttu-id="8c4c8-163">**자전거 구매자** 의 고객과 **자전거 구매자** 의 많은 차이점 중 일부는 나이, 자동차 소유권, 자녀 수 및 지역이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-163">Some of the more substantial differences among the customers in the **Bike Buyers Low** and **Bike Buyers High** clusters include age, car ownership, number of children, and region.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8c4c8-164">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8c4c8-164">Related Tasks</span></span>  
 <span data-ttu-id="8c4c8-165">다른 마이닝 모델을 탐색 하려면 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c4c8-165">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="8c4c8-166">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4c8-166">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="8c4c8-167">Naive Bayes 모델 &#40;기본 데이터 마이닝 자습서 살펴보기&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4c8-167">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8c4c8-168">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="8c4c8-168">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8c4c8-169">Naive Bayes 모델 &#40;기본 데이터 마이닝 자습서 살펴보기&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4c8-169">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="8c4c8-170">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="8c4c8-170">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="8c4c8-171">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4c8-171">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c4c8-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c4c8-172">See Also</span></span>  
 <span data-ttu-id="8c4c8-173">[Microsoft 클러스터 뷰어를 사용 하 여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="8c4c8-173">[Browse a Model Using the Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span></span>  
 <span data-ttu-id="8c4c8-174">[클러스터 판별 탭 &#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="8c4c8-174">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="8c4c8-175">[마이닝 모델 뷰어를 &#40;클러스터 프로필 탭&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="8c4c8-175">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="8c4c8-176">[마이닝 모델 뷰어를 &#40;클러스터 특징 탭&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="8c4c8-176">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="8c4c8-177">마이닝 모델 뷰어를 &#40;클러스터 다이어그램 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="8c4c8-177">Cluster Diagram Tab &#40;Mining Model Viewer&#41;</span></span>](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
