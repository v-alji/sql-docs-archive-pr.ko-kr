---
title: 시퀀스 클러스터링 모델 탐색 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bac603d2480ec1f344d14351757027de749f8c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735636"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="a3809-102">시퀀스 클러스터링 모델 탐색(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="a3809-102">Exploring the Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="a3809-103">이제 지역 모델을 사용 하 여 **시퀀스 클러스터링** 을 빌드 했으므로 [!INCLUDE[msCoName](../includes/msconame-md.md)] 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 있는 시퀀스 클러스터링 뷰어를 사용 하 여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-103">Now that you have built the **Sequence Clustering with Region** model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="a3809-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]시퀀스 클러스터 뷰어에는 **클러스터 다이어그램**, **클러스터 프로필**, **클러스터 특징**, **clusterdiscrimination**, **상태 전환**의 5 개 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Cluster Viewer contains five tabs: **Cluster Diagram**, **Cluster Profiles**, **Cluster Characteristics**, **ClusterDiscrimination**, and **State Transitions**.</span></span> <span data-ttu-id="a3809-105">이 뷰어를 사용 하는 방법에 대 한 자세한 내용은 [Microsoft 시퀀스 클러스터 뷰어를 사용 하 여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-105">For more information about how to use this viewer, see [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).</span></span>  
  
-   [<span data-ttu-id="a3809-106">클러스터 다이어그램 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-106">Cluster Diagram tab</span></span>](#bkmk_CDiagram)  
  
-   [<span data-ttu-id="a3809-107">클러스터 프로필 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-107">Cluster Profiles tab</span></span>](#bkmk_CProfiles)  
  
-   [<span data-ttu-id="a3809-108">클러스터 특징 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-108">Cluster Characteristics tab</span></span>](#bkmk_CChars)  
  
-   [<span data-ttu-id="a3809-109">클러스터 판별 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-109">Cluster Discrimination tab</span></span>](#bkmk_CDiscrim2)  
  
-   [<span data-ttu-id="a3809-110">상태 전환 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-110">State Transitions tab</span></span>](#bkmk_StateTran)  
  
-   [<span data-ttu-id="a3809-111">일반 콘텐츠 뷰</span><span class="sxs-lookup"><span data-stu-id="a3809-111">Generic Content View</span></span>](#bkmk_Generic)  
  
##  <a name="cluster-diagram-tab"></a><a name="bkmk_CDiagram"></a><span data-ttu-id="a3809-112">클러스터 다이어그램 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-112">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="a3809-113">**클러스터 다이어그램** 탭은 알고리즘이 데이터베이스에서 발견 한 클러스터를 그래픽으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-113">The **Cluster Diagram** tab graphically displays the clusters that the algorithm discovered in the database.</span></span> <span data-ttu-id="a3809-114">다이어그램의 레이아웃은 비슷한 클러스터가 서로 가깝게 그룹화되는 클러스터 관계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-114">The layout in the diagram represents the relationships of the clusters, with similar clusters grouped close together.</span></span> <span data-ttu-id="a3809-115">기본적으로 각 노드의 음영은 클러스터에 있는 모든 사례의 밀도를 나타냅니다. 노드의 음영이 짙을수록 노드에 있는 사례 개수가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-115">By default, the shade of each node represents the density of all cases in the cluster: the darker the shade of the node, the more cases it contains.</span></span> <span data-ttu-id="a3809-116">노드 음영이 각 클러스터 내에서 특성과 상태에 대한 지원을 나타내도록 음영의 의미를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-116">You can change the meaning of the shading of the nodes so that it represents support, within each cluster, for an attribute and a state.</span></span>  
  
 <span data-ttu-id="a3809-117">식별 및 대상 클러스터와의 작업이 쉽도록 클러스터의 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-117">You can also rename the clusters, to make it easier to identify and work with target clusters.</span></span> <span data-ttu-id="a3809-118">이 자습서에서는 Pacific 지역에서 고객 비율이 가장 높은 클러스터와 전체적으로 가장 많은 사례를 포함하는 클러스터의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-118">For this tutorial, you will rename the cluster that has the highest percentage of customers from the Pacific region, and the cluster that has the most cases overall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3809-119">데이터 및 모델 매개 변수에 따라 모델을 다시 처리할 때 특정 클러스터에 할당된 사례가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-119">The cases that are assigned to specific clusters might change when you reprocess the model, depending on the data and the model parameters.</span></span> <span data-ttu-id="a3809-120">또한 클러스터의 이름을 바꿀 경우 마이닝 모델을 다시 처리하면 이름이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-120">Also, if you rename clusters, the names will be lost when you reprocess the mining model.</span></span>  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a><span data-ttu-id="a3809-121">클러스터를 강조 표시하는 데 사용되는 특성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a3809-121">To change the attribute used for highlighting clusters</span></span>  
  
1.  <span data-ttu-id="a3809-122">**음영 변수** 목록에서 **모델**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-122">In the **Shading Variable** list, select **Model**.</span></span>  
  
2.  <span data-ttu-id="a3809-123">**상태** 목록에서 **순환 캡** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-123">Select **Cycling Cap** in the **State** list.</span></span>  
  
     <span data-ttu-id="a3809-124">다이어그램이 업데이트되어 각 클러스터에서 선택된 제품의 집중 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-124">The diagram updates to show the concentration of the selected product in each of the clusters.</span></span> <span data-ttu-id="a3809-125">음영이 가장 짙은 클러스터에는 가장 높은 밀도의 자전거 모자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-125">The cluster that has the darkest shading contains the highest density of cycling caps.</span></span> <span data-ttu-id="a3809-126">모든 입력 열의 상태를 사용 하도록 음영 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-126">You can change the shading variable to use any state of any input column.</span></span>  
  
3.  <span data-ttu-id="a3809-127">**음영 변수** 목록에서 **채우기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-127">In the **Shading Variable** list, select **Population**.</span></span>  
  
     <span data-ttu-id="a3809-128">음영 변수를 모집단으로 변경하면 다이어그램이 업데이트되어 클러스터가 크기별로 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-128">When you change the shading variable to population, the diagram updates to compare the clusters by size.</span></span> <span data-ttu-id="a3809-129">음영이 가장 짙은 클러스터에는 다른 클러스터보다 많은 사례가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-129">The cluster that has the darkest shading contains more cases than the other clusters.</span></span>  
  
#### <a name="to-rename-nodes-in-the-model"></a><span data-ttu-id="a3809-130">모델 노드의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="a3809-130">To rename nodes in the model</span></span>  
  
1.  <span data-ttu-id="a3809-131">**음영 변수** 를로 변경 하 `Region` 고 **상태** 를 **태평양**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-131">Change **Shading Variable** to `Region`, and set **State** to **Pacific**.</span></span>  
  
2.  <span data-ttu-id="a3809-132">그래프에서 가장 짙은 노드를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-132">Highlight the darkest node in the graph.</span></span>  
  
3.  <span data-ttu-id="a3809-133">이 클러스터를 마우스 오른쪽 단추로 클릭 하 고 **클러스터 이름 바꾸기를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="a3809-133">Right-click this cluster and select **Rename Cluster.**</span></span>  
  
4.  <span data-ttu-id="a3809-134">**태평양 클러스터** 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-134">Type the name**Pacific Cluster.**</span></span>  
  
5.  <span data-ttu-id="a3809-135">**음영 변수** 값을 **모집단**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-135">Change the value of **Shading Variable** to **Population**.</span></span>  
  
6.  <span data-ttu-id="a3809-136">업데이트된 그래프에서 가장 짙은 클러스터, 즉 가장 큰 클러스터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-136">In the updated graph, locate the darkest cluster, which should be the largest cluster.</span></span> <span data-ttu-id="a3809-137">음영으로 가장 큰 클러스터를 찾을 수 없는 경우 각 클러스터 위에 마우스를 놓으면 나타나는 도구 설명을 확인하여 사례가 가장 많이 포함된 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-137">If you cannot tell by the shading which cluster is largest, pause the mouse over each cluster and view the ToolTip, and then choose the cluster that contains the most cases.</span></span>  
  
7.  <span data-ttu-id="a3809-138">이 클러스터를 마우스 오른쪽 단추로 클릭 하 고 **클러스터 이름 바꾸기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-138">Right-click this cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="a3809-139">새 이름을 입력 `Largest Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-139">Type the new name, `Largest Cluster`.</span></span>  
  
 <span data-ttu-id="a3809-140">클러스터를 나타내는 노드에서 드릴스루하면 각 클러스터에 있는 사례에 대한 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-140">You can drill through from the node that represents the cluster to view details of the cases that are in each cluster.</span></span> <span data-ttu-id="a3809-141">분석 결과에 따라 고객에게 전자 메일을 보내는 등의 조치를 취하려는 경우 이렇게 하면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-141">This can be useful if you want to take action on the results of your analysis, such as sending e-mail to a customer.</span></span> <span data-ttu-id="a3809-142">구조에 포함했지만 모델에 사용하지는 않은 사례의 기타 특성(예: Region 및 Income Group)을 찾아볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-142">You can also browse the other attributes of the cases that you included in the structure but did not use in the model, such as Region and IncomeGroup.</span></span> <span data-ttu-id="a3809-143">마이닝 모델에서 기본 사례로 드릴링 하는 방법에 대 한 자세한 내용은 [드릴스루 쿼리 &#40;데이터 마이닝&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-143">For more information about drilling through from mining models to the underlying cases, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a><span data-ttu-id="a3809-144">클러스터 다이어그램에서 세부 정보로 드릴스루하려면</span><span class="sxs-lookup"><span data-stu-id="a3809-144">To drill through to details from the Cluster diagram</span></span>  
  
1.  <span data-ttu-id="a3809-145">마우스 오른쪽 단추 `Pacific Cluster` 를 클릭 하 고 **드릴스루**를 선택한 다음 **모델 및 구조 열**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-145">Right-click `Pacific Cluster`, select **Drill Through**, and then select **Model and Structure columns**.</span></span>  
  
     <span data-ttu-id="a3809-146">**드릴스루** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-146">The **Drill Through** dialog box opens.</span></span> <span data-ttu-id="a3809-147">모델에는 사용 되지 않지만 쿼리에 사용할 수 있는 열에는 **구조가**접두사로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-147">Columns that are not used in the model but that are available for querying are prefixed with **Structure**.</span></span>  
  
     <span data-ttu-id="a3809-148">이 클러스터에 포함된 고객이 대부분 Pacific 지역 고객이고 일부만 다른 지역 고객임을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-148">You can see that this cluster contains mostly customers from the Pacific region, with only a few customers from other regions.</span></span>  
  
2.  <span data-ttu-id="a3809-149">중첩 열 v Assoc Seq Line Items의 더하기 기호를 클릭하여 특정 고객 주문에 포함된 항목의 시퀀스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-149">Click the plus sign in the nested column v Assoc Seq Line Items to view the sequence of items in a particular customer order.</span></span>  
  
3.  <span data-ttu-id="a3809-150">**드릴스루** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-150">Close the **Drill Through** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3809-151">**재생** 단추를 사용 하 여 데이터를 다시 쿼리할 수 있습니다. 그러나 모델이 다른 프로세스에 의해 백그라운드에서 동적으로 업데이트 되지 않는 한 다시 쿼리하면 표시 되는 데이터가 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-151">The **Play** button enables you to requery the data; however, requerying does not change the data that is displayed, unless the model has been dynamically updated in the background by some other process.</span></span>  
  
 [<span data-ttu-id="a3809-152">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-152">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-profiles-tab"></a><a name="bkmk_CProfiles"></a><span data-ttu-id="a3809-153">클러스터 프로필 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-153">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="a3809-154">**클러스터 프로필** 탭에는 각 클러스터에 있는 시퀀스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-154">The **Cluster Profiles** tab displays the sequences that are in each cluster.</span></span> <span data-ttu-id="a3809-155">클러스터는 **상태** 열의 오른쪽에 있는 개별 열에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-155">The clusters are listed in individual columns to the right of the **States** column.</span></span>  
  
 <span data-ttu-id="a3809-156">뷰어에서 **모델** 행은 클러스터에 있는 항목의 전체 분포를 설명 하 고, **samples** 행은 항목의 시퀀스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-156">In the viewer, the **Model** row describes the overall distribution of items in a cluster, and the **Model.samples** row contains sequences of the items.</span></span> <span data-ttu-id="a3809-157">**모델 samples** 행의 각 셀에 있는 색 시퀀스의 각 줄은 클러스터에서 임의로 선택 된 사용자의 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-157">Each line of the color sequences in each cell of the **Model.samples** row represents the behavior of a randomly selected user in the cluster.</span></span>  
  
 <span data-ttu-id="a3809-158">개별 시퀀스 히스토그램의 각 색은 제품 모델을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-158">Each color in an individual sequence histogram represents a product model.</span></span> <span data-ttu-id="a3809-159">마이닝 범례는 색 구분 및 제품 모델 이름을 모두 사용하여 제품의 시퀀스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-159">The Mining Legend shows you the sequences of products by using both color-coding and the product model names.</span></span> <span data-ttu-id="a3809-160">모델에 다른 클러스터링용 열(예: Region 또는 Income Group)을 추가한 경우 뷰어에는 각 클러스터 내에서 이러한 값의 분포를 보여 주는 추가 행이 각 열에 대해 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-160">If you have added other columns to the model for clustering, such as Region or Income Group, the viewer will contain an additional row for each column that shows the distribution of these values within each cluster.</span></span>  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a><span data-ttu-id="a3809-161">클러스터에서 가장 일반적인 시퀀스를 보려면</span><span class="sxs-lookup"><span data-stu-id="a3809-161">To view the sequences that are most common in a cluster</span></span>  
  
1.  <span data-ttu-id="a3809-162">클러스터의 열에서 **모델** 행을 마우스 오른쪽 단추로 클릭 `Largest Cluster` 하 고 **범례 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-162">Right-click the **Model** row in the column for the cluster `Largest Cluster`, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="a3809-163">**색** 열에는 시퀀스에 있는 항목의 빈도를 나타내는 음영 처리 된 막대가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-163">The **Color** column contains a shaded bar that indicates the frequency of items found in sequences.</span></span> <span data-ttu-id="a3809-164">각 항목은 서로 다른 색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-164">Each item is represented by a different color.</span></span> <span data-ttu-id="a3809-165">**의미** 열에는 각 색에 대 한 제품 모델 이름이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-165">The **Meaning** column lists the product model names for each color.</span></span> <span data-ttu-id="a3809-166">**분포** 열은이 항목이 시퀀스에 포함 된 사례의 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-166">The **Distribution** column tells you the percentage of cases that contained this item in a sequence.</span></span>  
  
2.  <span data-ttu-id="a3809-167">**마이닝 범례**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-167">Close the **Mining Legend**.</span></span>  
  
3.  <span data-ttu-id="a3809-168">제목이, **채우기** 인 열에서 **samples** 행을 마우스 오른쪽 단추로 클릭 하 고 **범례 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-168">Right-click the **Model.samples** row in the column with the heading, **Population,** and select **Show Legend**.</span></span>  
  
4.  <span data-ttu-id="a3809-169">전체 모델의 시퀀스 목록 검색`.`</span><span class="sxs-lookup"><span data-stu-id="a3809-169">Scan the list of sequences in the overall model`.`</span></span>  
  
     <span data-ttu-id="a3809-170">마이닝 범례에는 가장 일반적인 시퀀스가 먼저 나열되므로 Mountain Tire Tube가 많은 시퀀스에서 첫 번째 항목임을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-170">The Mining Legend lists the most common sequences first, so you can see that Mountain Tire Tube is the first item in many sequences.</span></span> <span data-ttu-id="a3809-171">이는 고객이 시장 바구니에 Mountain Tire Tube를 먼저 담을 가능성이 매우 높음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-171">This means that a customer is very likely to put the Mountain Tire Tube in the shopping basket first.</span></span>  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a><span data-ttu-id="a3809-172">클러스터 뷰어에서 사례로 드릴스루하려면</span><span class="sxs-lookup"><span data-stu-id="a3809-172">To drill through to cases from the cluster viewer</span></span>  
  
1.  <span data-ttu-id="a3809-173">특성 창에서 특성에 대 한 행을 찾을 때까지 아래로 스크롤합니다 `Region` .</span><span class="sxs-lookup"><span data-stu-id="a3809-173">Scroll down in the Attribute pane until you find the row for the `Region` attribute.</span></span>  
  
     <span data-ttu-id="a3809-174">행에는 모델의 각 클러스터에 대 한 히스토그램과 **모집단**에 대 한 추가 히스토그램 하나 (모델에 사용 되는 전체 사례 집합)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-174">The row contains a histogram for each cluster in the model, plus one additional histogram for **Population**, meaning the entire set of cases used in the model.</span></span> <span data-ttu-id="a3809-175">히스토그램은 다양한 색이 포함된 막대입니다. 여기서 각 색은 특성을 나타내며 이러한 특성에 대해 색이 지정된 부분의 크기는 해당 특성이 지정된 사례의 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-175">A histogram is a bar with different colors in it, where each color represents an attribute, and the size of the colored section for that attribute represents the percentage of cases with that attribute.</span></span>  
  
2.  <span data-ttu-id="a3809-176">이름을 바꾼 클러스터에 대 한 히스토그램을 비교 `Pacific Cluster` `Largest Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-176">Compare the histograms for the clusters that you renamed `Pacific Cluster` and `Largest Cluster`.</span></span> <span data-ttu-id="a3809-177">각 클러스터는 서로 다른 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-177">Each cluster appears in a different column.</span></span>  
  
     <span data-ttu-id="a3809-178">둘 모두 단색처럼 보이지만 사실은 다른 색입니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-178">Both look like solid colors, but the colors are different.</span></span>  
  
3.  <span data-ttu-id="a3809-179">행에서 `Region` 에 대 한 색이 지정 된 히스토그램 위에 마우스를 놓습니다 `Largest Cluster` .</span><span class="sxs-lookup"><span data-stu-id="a3809-179">In the `Region` row, pause the mouse over the colored histogram for `Largest Cluster`.</span></span>  
  
     <span data-ttu-id="a3809-180">도구 설명에 각 지역의 실제 사례 비율을 보여 주는 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-180">The ToolTip displays values that show the actual percentages of cases from each region.</span></span>  
  
4.  <span data-ttu-id="a3809-181">에 대 한 행에서 색이 지정 된 히스토그램을 마우스 오른쪽 단추로 클릭 `Region` `Pacific Cluster` 하 고 **드릴스루**를 선택한 다음 **모델 열만**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-181">Right-click the colored histogram in the `Region` row for `Pacific Cluster`, select **Drill Through**, and then select **Model Columns Only**.</span></span>  
  
5.  <span data-ttu-id="a3809-182">스크롤 막대를 이동하여 이 클러스터의 모든 고객을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-182">Move the scroll bar to review all of the customers in this cluster.</span></span>  
  
     <span data-ttu-id="a3809-183">다시 세부 정보로 드릴스루하면 클러스터에 포함된 주문이 대부분 Pacific 지역 주문이지만 North America 및 Europe 지역 주문도 일부 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-183">Again, from drilling through to the details you can see that the cluster contains mostly orders from the Pacific region but also a few from the North America and Europe regions.</span></span>  
  
6.  <span data-ttu-id="a3809-184">**드릴스루** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-184">Close the **Drill Through** dialog box.</span></span>  
  
 [<span data-ttu-id="a3809-185">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-185">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-characteristics-tab"></a><a name="bkmk_CChars"></a><span data-ttu-id="a3809-186">클러스터 특징 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-186">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="a3809-187">**클러스터 특징** 탭은 선택한 클러스터에 대 한 특성 값의 중요도를 시각적으로 표시 하는 막대를 표시 하 여 클러스터 상태 간의 전환을 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-187">The **Cluster Characteristics** tab summarizes the transitions between states in a cluster by displaying bars that visually represent the importance of the attribute value for the selected cluster.</span></span> <span data-ttu-id="a3809-188">**Variables** 열은 선택 된 클러스터 또는 모집단에 대해 중요 한 것으로 확인 된 모델의 결과를 표시 합니다. 특정 값 또는 값 사이의 관계 ( *전환*이라고 함)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-188">The **Variables** column tells you what the model found to be important for the selected cluster or population: either a particular value or the relationship between values, known as *transition*.</span></span> <span data-ttu-id="a3809-189">값 **열은** 값 또는 전환에 대 한 자세한 정보를 제공 하며 **확률** 열은이 특성 또는 전환의 가중치를 시각적으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-189">The **Values** column provides more detail about the value or transition, and the **Probability** column visually represents the weight of this attribute or transition.</span></span>  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a><span data-ttu-id="a3809-190">클러스터에 대해 중요한 특성을 보려면</span><span class="sxs-lookup"><span data-stu-id="a3809-190">To view the important attributes for a cluster</span></span>  
  
1.  <span data-ttu-id="a3809-191">**클러스터** 드롭다운 목록에서을 선택 `Pacific Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-191">In the **Cluster** dropdown list, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="a3809-192">목록은 이름을 바꾼 클러스터의 특성을 표시 하도록 업데이트 `Pacific Cluster` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-192">The list updates to show the characteristics of the cluster that you renamed `Pacific Cluster`.</span></span> <span data-ttu-id="a3809-193">이 클러스터에서 가장 중요 한 특징은 `Region` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-193">In this cluster, the most important characteristic is `Region`.</span></span>  
  
2.  <span data-ttu-id="a3809-194">에 대 한 행의 음영 처리 된 막대 위에 마우스를 놓습니다 `Region` .</span><span class="sxs-lookup"><span data-stu-id="a3809-194">Pause the mouse over the shaded bar in the row for `Region`.</span></span>  
  
     <span data-ttu-id="a3809-195">값이 Pacific일 확률이 매우 높습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-195">The probability of the value being Pacific is very high.</span></span> <span data-ttu-id="a3809-196">이러한 값을 해석 하는 방법에 대 한 자세한 내용은 [Microsoft 시퀀스 클러스터링 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-196">For more information about how to interpret these values, see [Microsoft Sequence Clustering Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).</span></span>  
  
3.  <span data-ttu-id="a3809-197">클러스터의 특징 목록을 살펴보아 첫 번째 전환 행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-197">Look through the list of characteristics for the cluster until you find the first transition row.</span></span>  
  
4.  <span data-ttu-id="a3809-198">전환 행은 **Variables** 열의 텍스트 전환을 포함 하 고 **값** 열에는 일련의 순차 특성 값을 조합 하 여 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-198">A transition row contains the text Transition in the **Variables** column, and some combination of sequential attribute values in the **Value** column.</span></span> <span data-ttu-id="a3809-199">시퀀스는 시작 지점 및 누락 값도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-199">The sequence can also contain starting points and missing values.</span></span>  
  
     <span data-ttu-id="a3809-200">예를 들어 전환에 [Start]-> 도로의 타이어 튜브 값이 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-200">For example, suppose the transition has the value, [Start] -> Road Tire Tube.</span></span> <span data-ttu-id="a3809-201">이 클러스터의 고객이 시장 바구니에 Road Tire Tube를 먼저 담는 경우가 많음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-201">This means that customers in this cluster frequently put the Road Tire Tube in their shopping basket first.</span></span> <span data-ttu-id="a3809-202">이는 해당 제품이 고객이 먼저 찾는 인기 항목임을 나타내거나 단지 구매처에서 찾기 쉬운 항목임을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-202">This might signify that the product is a popular item that customers seek out first, or it might only indicate that the product is easy to find on the purchasing site.</span></span>  
  
5.  <span data-ttu-id="a3809-203">**[시작]** 또는 **누락** 되지 않은 첫 번째 전환을 찾을 때까지 목록을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-203">Scroll through the list until you find the first transition that does not have **[Start]** or **missing** in it.</span></span>  
  
     <span data-ttu-id="a3809-204">예를 들어, **여행용 타이어, 여행용 타이어 튜브**를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-204">For example, suppose you find the transition, **Touring Tire, Touring Tire Tube**.</span></span> <span data-ttu-id="a3809-205">이 클러스터의 고객이 해당 항목을 이 순서대로 함께 구매하는 경우가 많음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-205">This means that customers in this cluster frequently purchased these items together, in exactly this order.</span></span>  
  
6.  <span data-ttu-id="a3809-206">이 전환에 대해 음영 처리된 막대 위에 마우스를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-206">Pause the mouse over the shaded bar for this transition.</span></span>  
  
     <span data-ttu-id="a3809-207">이 전환의 확률이 백분율로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-207">The probability of this transition is displayed as a percentage.</span></span>  
  
7.  <span data-ttu-id="a3809-208">**클러스터** 드롭다운 목록에서 **채우기 (모두)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-208">In the **Cluster** dropdown list, select **Population (All)**.</span></span>  
  
     <span data-ttu-id="a3809-209">특성 목록이 업데이트되어 모델을 만드는 데 사용된 모든 주문의 특징이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-209">The list of attributes updates to show the characteristics of all orders used to create the model.</span></span> <span data-ttu-id="a3809-210">이 마이닝 모델에서 클러스터를 구별 하는 가장 중요 한 특성은 `Region` **북아메리카**값입니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-210">In this mining model, the most important characteristic for distinguishing between clusters is `Region`, with a value of **North America**.</span></span>  
  
 <span data-ttu-id="a3809-211">이러한 태스크를 검토하면 두 가지 사실을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-211">After reviewing these tasks, you realize two things.</span></span> <span data-ttu-id="a3809-212">첫 번째는 의미 있는 조합 수를 얻으려면 많은 데이터가 필요하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-212">The first is that you need a lot of data to obtain a meaningful number of combinations.</span></span> <span data-ttu-id="a3809-213">예를 들어 확률이 가장 높은 시퀀스는 **[시작]** 또는 **누락** 된 상태를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-213">For example, the sequences with the highest probabilities are likely to include a **[Start]** or **Missing** state.</span></span>  
  
 <span data-ttu-id="a3809-214">두 번째는의 특성에 대 한 강력한 클러스터링 효과를 가지 며,이를 `Region` 통해 시퀀스 그룹을 보는 것이 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-214">The second is that there is a strong clustering effect on attributes for `Region`, which makes it more difficult to see the groups of sequences.</span></span> <span data-ttu-id="a3809-215">이에 따라 시퀀스만 사용하며 지역 또는 수입에 대한 열을 포함하지 않는 다른 모델을 만들기로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-215">Therefore, you decide to create another model that uses sequences only, and does not include the columns for region or income.</span></span>  
  
 [<span data-ttu-id="a3809-216">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-216">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-discrimination-tab"></a><a name="bkmk_CDiscrim2"></a><span data-ttu-id="a3809-217">클러스터 판별 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-217">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="a3809-218">**클러스터 판별** 탭에서는 두 클러스터를 비교 하 여 특정 클러스터를 다른 클러스터와 구별 하는 특성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-218">The **Cluster Discrimination** tab helps you compare two clusters, to determine which attributes distinguish a particular cluster from another cluster.</span></span> <span data-ttu-id="a3809-219">이 탭에는 **변수**, **값**, **클러스터 1**및 **클러스터 2**의 4 개 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-219">The tab contains four columns: **Variables**, **Values**, **Cluster 1**, and **Cluster 2**.</span></span>  <span data-ttu-id="a3809-220">클러스터 **1** 및 **클러스터 2**로 사용할 클러스터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-220">You can choose any cluster to use as **Cluster 1** and **Cluster 2**.</span></span>  
  
 <span data-ttu-id="a3809-221">**Variables** 열에는 특성 이름이 나 열 이름과 단어 **전환**의 조합을 지정할 수 있는 특성 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-221">The **Variables** column tells you the name of the attribute, which can either be a column name or combination of column name and the word **transition**.</span></span> <span data-ttu-id="a3809-222">**값** 열에는 특성 또는 전환의 정확한 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-222">The **Values** column shows the exact value of the attribute or the transition.</span></span> <span data-ttu-id="a3809-223">**클러스터 1** 및 **클러스터 2** 의 열에 있는 음영 처리 된 막대는 비교할 클러스터에서 특성의 강도를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-223">The shaded bars in the columns for **Cluster 1** and **Cluster 2** indicate the strength of the attribute in the clusters that you are comparing.</span></span> <span data-ttu-id="a3809-224">막대가 길수록 클러스터가 해당 특성이 지정된 사례를 포함할 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-224">The longer the bar, the more the cluster is likely to include cases with that attribute.</span></span>  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a><span data-ttu-id="a3809-225">클러스터 판별 탭을 사용하여 두 클러스터를 비교하려면</span><span class="sxs-lookup"><span data-stu-id="a3809-225">To compare two clusters by using the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="a3809-226">클러스터 **판별** 탭에서 **클러스터 1**에 대해를 선택 `Pacific Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-226">In the **Cluster Discrimination** tab, for **Cluster 1**, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="a3809-227">기본적으로 **클러스터 2** 에 대 한 선택은 **태평양 클러스터의 보수**로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-227">By default, the selection for **Cluster 2** changes to **Complement of Pacific Cluster**.</span></span>  
  
     <span data-ttu-id="a3809-228">다른 모든 사례를 구별 하는 최상위 특성은 `Pacific Cluster` 지역입니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-228">The top attribute that distinguishes `Pacific Cluster` from all other cases is the region.</span></span> <span data-ttu-id="a3809-229">Region은 클러스터링에 대해 영향이 큰 특성이어서 다른 특성을 모호하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-229">Region is such a strong attribute for clustering that it obscures other attributes.</span></span> <span data-ttu-id="a3809-230">이러한 영향을 방지하려면 보다 작은 여러 클러스터를 서로 비교해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a3809-230">To avoid this effect, try comparing several of the smaller clusters to each other.</span></span> <span data-ttu-id="a3809-231">이렇게 하면 특성 목록이 변경되어 모델 간에 더 많은 전환이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-231">When you do so, the list of attributes changes and might include more transitions between models.</span></span>  
  
2.  <span data-ttu-id="a3809-232">전환 열을 찾아 음영 처리된 막대 위에 마우스를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-232">Locate a transition row, and pause the mouse over the shaded bar.</span></span>  
  
     <span data-ttu-id="a3809-233">**Values** 열의 항목에는 상태와 전환이 모두 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-233">The items in the **Values** column can include both states and transitions.</span></span> <span data-ttu-id="a3809-234">각 항목의 음영은 판별 점수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-234">The shading for each item indicates the discrimination score.</span></span> <span data-ttu-id="a3809-235">여러 점수의 의미에 대 한 자세한 내용은 [데이터 마이닝&#41;Analysis Services &#40;시퀀스 클러스터링 모델에 대 한 마이닝 모델 콘텐츠 ](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-235">To learn more about the meaning of different scores, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="a3809-236">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-236">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="state-transitions-tab"></a><a name="bkmk_StateTran"></a><span data-ttu-id="a3809-237">상태 전환 탭</span><span class="sxs-lookup"><span data-stu-id="a3809-237">State Transitions Tab</span></span>  
 <span data-ttu-id="a3809-238">**상태 전환** 탭에서 클러스터를 선택 하 고 상태 전환을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-238">On the **State Transitions** tab, you can select a cluster and browse through its state transitions.</span></span> <span data-ttu-id="a3809-239">클러스터 드롭다운 목록에서 **채우기 (모두)** 를 선택 하는 경우 다이어그램은 전체 마이닝 모델의 상태 분포를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-239">If you select **Population (All)** from the cluster drop-down list, the diagram shows the distribution of states for the whole mining model.</span></span>  
  
 <span data-ttu-id="a3809-240">그래프의 각 노드는 분석하려는 시퀀스의 상태 또는 가능한 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-240">Each node in the graph represents a state, or possible value, of the sequences that you are trying to analyze.</span></span> <span data-ttu-id="a3809-241">노드의 배경색은 해당 상태의 빈도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-241">The background color of the nodes represents the frequency of that state.</span></span> <span data-ttu-id="a3809-242">일부 상태를 연결하는 선은 상태 간 전환을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-242">Lines connect some states, indicating a transition between states.</span></span> <span data-ttu-id="a3809-243">슬라이더를 위나 아래로 이동하여 전환에 대한 확률 임계값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-243">You can move the slider up or down to change the probability threshold for the transitions.</span></span> <span data-ttu-id="a3809-244">일부 노드와 연결된 숫자는 해당 상태의 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-244">Numbers are associated with some nodes, indicating the probability of that state.</span></span>  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a><span data-ttu-id="a3809-245">상태 전환 탭에서 관계를 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="a3809-245">To explore the relationships in the State Transition tab</span></span>  
  
1.  <span data-ttu-id="a3809-246">마이닝 모델 뷰어의 **상태 전환** 탭에서 `Pacific Cluster` 클러스터 목록에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-246">In the **State Transitions** tab of the Mining Model viewer, select `Pacific Cluster` from the list of clusters.</span></span> <span data-ttu-id="a3809-247">**가장자리 레이블 표시** 옵션이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-247">Ensure that the **Show Edge Labels** option is selected.</span></span>  
  
     <span data-ttu-id="a3809-248">그래프가 업데이트되어 이 클러스터에서 가장 일반적인 전환이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-248">The graph updates to show the transitions that are most common in this cluster.</span></span>  
  
2.  <span data-ttu-id="a3809-249">선으로 다른 노드에 연결된 임의의 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-249">Click any node that is connected by a line to another node.</span></span>  
  
     <span data-ttu-id="a3809-250">그래프가 업데이트되고 관련 노드가 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-250">The graph is updated and highlights the related nodes.</span></span> <span data-ttu-id="a3809-251">선 옆의 숫자 값은 해당 전환의 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-251">The numeric value next to the line indicates the probability of the transition.</span></span>  
  
3.  <span data-ttu-id="a3809-252">**모든 링크**까지 슬라이더를 올리고 그래프에 포함 된 전환 수를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-252">Raise the slider up to **All Links**, to increase the number of transitions included in the graph.</span></span>  
  
4.  <span data-ttu-id="a3809-253">**클러스터**에서 **채우기 (모두)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-253">Select **Population (All)** from **Cluster**.</span></span>  
  
     <span data-ttu-id="a3809-254">다른 클러스터를 로드하면 그래프가 기본 표시 설정으로 다시 설정되어 슬라이더 컨트롤이 가운데 위치로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-254">Note that when you load a different cluster, the graph resets to the default display settings, so the slider control is reset to the middle position.</span></span>  
  
5.  <span data-ttu-id="a3809-255">그래프에서 가장 짙은 노드 ( **스포츠-100)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-255">Click the darkest node in the graph, which should be **Sport-100**.</span></span>  
  
     <span data-ttu-id="a3809-256">이 제품을 다른 제품에 연결하는 선이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-256">Note that there are no lines connecting this product to other products.</span></span>  
  
6.  <span data-ttu-id="a3809-257">슬라이더를 한 단계 올려 그래프에 포함되는 전환 수를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-257">Raise the slider up one step, to increase the number of transitions included in the graph.</span></span> <span data-ttu-id="a3809-258">**모든 링크** 를 아직 이동 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-258">Do not go all the way to **All Links** yet.</span></span>  
  
     <span data-ttu-id="a3809-259">그래프가 업데이트되어 여러 전환이 더 추가되지만 Sport-100 모델을 포함하는 전환은 아직 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-259">The graph is updated by adding several more transitions to the graph, but none that include the Sport-100 model.</span></span>  
  
7.  <span data-ttu-id="a3809-260">슬라이더 컨트롤을 **모든 링크로**이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-260">Move the slider control all the way to **All Links**.</span></span> <span data-ttu-id="a3809-261">Sport-100 노드가 선택되어 있지 않으면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-261">Click the Sport-100 node if it is not already selected.</span></span>  
  
     <span data-ttu-id="a3809-262">그래프가 업데이트되어 Sport-100 제품을 포함한 많은 전환이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-262">The graph updates to show many transitions that include the Sport-100 product.</span></span> <span data-ttu-id="a3809-263">연결선에 있는 화살표의 방향을 통해 Sport-100 항목이 해당 쌍에서 첫 번째 항목으로 선택되었는지, 아니면 두 번째 항목으로 선택되었는지를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-263">The direction of the arrow on the connecting line tells you whether the Sport-100 item was selected as the first item or the second item in the pair.</span></span>  
  
8.  <span data-ttu-id="a3809-264">Touring Tire에 대한 노드를 클릭하면 슬라이더 컨트롤이 다시 가운데 위치로 내려갑니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-264">Clicking the node for Touring Tire and move the slider control back down to the middle position.</span></span>  
  
     <span data-ttu-id="a3809-265">처음에는 여행용 타이어를 다른 제품에 연결 하는 많은 전환 선이 있지만 확률 임계값을 올리면 전환, 여행용 타이어 > 여행용 타이어 튜브를 그대로 두고 그래프에서 낮은 전환이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-265">At first, there are many transition lines connecting Touring Tire to other products, but when you raise the probability threshold, the less likely transitions are eliminated from the graph, leaving just the transition, Touring Tire > Touring Tire Tube.</span></span> <span data-ttu-id="a3809-266">이 전환은 한 고객이 Touring Tire를 시장 바구니에 담을 경우 해당 고객이 다음에 Touring Tire Tube를 시장 바구니에 담을 확률이 매우 높음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-266">This transition means that if a customer puts a Touring Tire into the shopping basket, there is a strong probability that the customer will next put a Touring Tire Tube into the basket.</span></span>  
  
 [<span data-ttu-id="a3809-267">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-267">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_Generic"></a><span data-ttu-id="a3809-268">일반 콘텐츠 트리 뷰어</span><span class="sxs-lookup"><span data-stu-id="a3809-268">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="a3809-269">이 뷰어는 알고리즘이나 모델 유형에 관계없이 모든 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-269">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="a3809-270">**MicrosoftGeneric 콘텐츠 트리 뷰어** 는 **뷰어** 드롭다운 목록에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-270">The **MicrosoftGeneric Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="a3809-271">콘텐츠 트리는 마이닝 모델을 일련의 노드로 표현한 것입니다. 여기서 각 노드는 학습 데이터에 대해 얻은 지식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-271">A content tree is a representation of any mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="a3809-272">노드에는 패턴, 일련의 규칙, 클러스터 또는 일부 특성을 공유하는 날짜 범위의 정의가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-272">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some attributes.</span></span> <span data-ttu-id="a3809-273">노드의 콘텐츠는 알고리즘 및 예측 가능한 특성에 따라 달라지지만 콘텐츠의 일반적인 표현은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-273">The exact content of the node differs depending on the algorithm and the predictable attribute, but the general representation of the content is the same.</span></span>  
  
 <span data-ttu-id="a3809-274">각 노드를 확장하여 세부 수준을 높이고 노드의 콘텐츠를 클립보드로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-274">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span> <span data-ttu-id="a3809-275">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-275">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a><span data-ttu-id="a3809-276">일반 콘텐츠 트리 뷰어를 사용하여 시퀀스 클러스터링 모델에 대한 세부 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="a3809-276">To view details for a sequence clustering model by using the Generic Content Tree Viewer</span></span>  
  
1.  <span data-ttu-id="a3809-277">**마이닝 모델 뷰어** 탭에서 **뷰어** 목록을 클릭 하 고 **Microsoft 일반 콘텐츠 트리 뷰어**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-277">In the **Mining Model Viewer** tab, click the **Viewer** list, and select **Microsoft Generic Content Tree viewer**.</span></span>  
  
2.  <span data-ttu-id="a3809-278">**노드 캡션** 창에서를 클릭 `Pacific Cluster (1)` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-278">In the **Node Caption** pane, click `Pacific Cluster (1)`.</span></span>  
  
     <span data-ttu-id="a3809-279">이 노드의 이름에는 사용자가 클러스터에 할당한 이름과 기본 노드 ID가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-279">The name for this node contains both the friendly name that you assigned to the cluster and the underlying node ID.</span></span> <span data-ttu-id="a3809-280">노드 ID를 사용하여 모델의 추가 세부 정보로 드릴다운할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-280">You can use the node IDs to drill down into additional detail in the model.</span></span>  
  
3.  <span data-ttu-id="a3809-281">**클러스터 1에 대해**명명 된 첫 번째 자식 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-281">Expand the first child node, named **Sequence level for cluster 1**.</span></span>  
  
     <span data-ttu-id="a3809-282">클러스터에 대한 시퀀스 수준 노드에는 해당 클러스터에 포함된 상태 및 전환에 대한 세부 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-282">The sequence level node for a cluster contains details about the states and transitions that are included in that cluster.</span></span> <span data-ttu-id="a3809-283">NODE_DISTRIBUTION 열에서 사용 가능한 이러한 세부 정보를 통해 각 클러스터 또는 전체 모델에 대한 시퀀스 및 상태를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-283">You can use these details, available in the NODE_DISTRIBUTION column, to explore the sequences and the states for each cluster or for the model as a while.</span></span>  
  
4.  <span data-ttu-id="a3809-284">HTML 뷰어 창에서 계속 노드를 확장하여 세부 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a3809-284">Continue to expand nodes and view the details in the HTML viewer pane.</span></span>  
  
 <span data-ttu-id="a3809-285">마이닝 모델 콘텐츠에 대 한 자세한 내용과 뷰어에서 세부 정보를 사용 하는 방법에 대 한 자세한 내용은 [Analysis Services 데이터 마이닝&#41;&#40;시퀀스 클러스터링 모델에 대 한 마이닝 모델 콘텐츠 ](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a3809-285">For more information about the mining model content, and how to use the details in the viewer, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="a3809-286">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="a3809-286">Back to Top</span></span>](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a3809-287">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a3809-287">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a3809-288">관련 된 시퀀스 클러스터링 모델 만들기 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="a3809-288">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3809-289">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3809-289">See Also</span></span>  
 <span data-ttu-id="a3809-290">[Microsoft 시퀀스 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a3809-290">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="a3809-291">시퀀스 클러스터링 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="a3809-291">Sequence Clustering Model Query Examples</span></span>](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
