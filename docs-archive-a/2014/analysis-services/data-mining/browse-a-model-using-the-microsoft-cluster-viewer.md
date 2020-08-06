---
title: Microsoft 클러스터 뷰어를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clusters [Analysis Services]
- discrimination [Analysis Services]
- names [Analysis Services], clusters
- Microsoft Cluster Viewer
- mining model content, viewing
- comparing clusters
- viewing clusters
- displaying clusters
- data mining [Analysis Services], clusters
- Cluster Viewer [Analysis Services]
- mining models [Analysis Services], clusters
ms.assetid: 591fe30b-d88f-4a71-94d4-4a3907fc275d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3597c97ad285d8ddc40b398723f6d3ec652ceb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660792"
---
# <a name="browse-a-model-using-the-microsoft-cluster-viewer"></a><span data-ttu-id="44c9e-102">Microsoft 클러스터 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="44c9e-102">Browse a Model Using the Microsoft Cluster Viewer</span></span>
  <span data-ttu-id="44c9e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 클러스터 뷰어는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 클러스터링 알고리즘을 사용 하 여 작성 된 마이닝 모델을 표시 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="44c9e-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="44c9e-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터링 알고리즘은 데이터를 탐색하여 데이터의 잘못된 부분을 식별하고 예측을 만드는 데 사용할 수 있는 세그먼트화 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm is a segmentation algorithm for use in exploring data to identify anomalies in the data and to create predictions.</span></span> <span data-ttu-id="44c9e-105">이 알고리즘에 대한 자세한 내용은 [Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44c9e-105">For more information about this algorithm, see [Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44c9e-106">발견된 패턴 및 모델에 사용된 수식에 대한 자세한 정보를 보려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="44c9e-106">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="44c9e-107">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) 또는 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44c9e-107">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="44c9e-108">뷰어 탭</span><span class="sxs-lookup"><span data-stu-id="44c9e-108">Viewer Tabs</span></span>  
 <span data-ttu-id="44c9e-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 찾으면 해당 모델의 적절한 뷰어에서 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 해당 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-109">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="44c9e-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터 뷰어는 클러스터링 마이닝 모델 탐색 시 사용할 수 있는 다음과 같은 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-110">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  
-   [<span data-ttu-id="44c9e-111">클러스터 다이어그램</span><span class="sxs-lookup"><span data-stu-id="44c9e-111">Cluster Diagram</span></span>](#BKMK_Diagram)  
  
-   [<span data-ttu-id="44c9e-112">클러스터 프로필</span><span class="sxs-lookup"><span data-stu-id="44c9e-112">Cluster Profiles</span></span>](#BKMK_Profile)  
  
-   [<span data-ttu-id="44c9e-113">클러스터 특징</span><span class="sxs-lookup"><span data-stu-id="44c9e-113">Cluster Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="44c9e-114">클러스터 판별</span><span class="sxs-lookup"><span data-stu-id="44c9e-114">Cluster Discrimination</span></span>](#BKMK_Discrimination)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a><span data-ttu-id="44c9e-115">클러스터 다이어그램</span><span class="sxs-lookup"><span data-stu-id="44c9e-115">Cluster Diagram</span></span>  
 <span data-ttu-id="44c9e-116">**클러스터 뷰어의** 클러스터 다이어그램 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 탭에서는 마이닝 모델에 있는 모든 클러스터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-116">The **Cluster Diagram** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="44c9e-117">두 클러스터를 연결하는 선의 음영은 클러스터의 유사성 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-117">The shading of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="44c9e-118">음영이 옅거나 없으면 두 클러스터가 그다지 유사하지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-118">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="44c9e-119">선이 어두울수록 링크의 유사성은 더 강해집니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-119">As the line becomes darker, the similarity of the links becomes stronger.</span></span> <span data-ttu-id="44c9e-120">클러스터의 오른쪽에 있는 슬라이더를 조정하여 뷰어에 표시되는 선의 개수를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-120">You can adjust how many lines the viewer shows by adjusting the slider to the right of the clusters.</span></span> <span data-ttu-id="44c9e-121">슬라이더를 내리면 강력한 링크만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-121">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="44c9e-122">기본적으로 음영은 클러스터의 채우기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-122">By default, the shade represents the population of the cluster.</span></span> <span data-ttu-id="44c9e-123">**ShadingVariable** 및 **state** 옵션을 사용 하 여 음영이 나타내는 특성 및 상태 쌍을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-123">By using the **ShadingVariable** and **State** options, you can select which attribute and state pair the shading represents.</span></span> <span data-ttu-id="44c9e-124">음영이 어두울수록 특정 상태에 대한 특성 분포는 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-124">The darker the shading, the greater the attribute distribution is for a specific state.</span></span> <span data-ttu-id="44c9e-125">음영이 밝을수록 분포는 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-125">The distribution decreases as the shading gets lighter.</span></span>  
  
 <span data-ttu-id="44c9e-126">클러스터의 이름을 바꾸려면 해당 노드를 마우스 오른쪽 단추로 클릭한 다음 **클러스터 이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-126">To rename a cluster, right-click its node and select **Rename Cluster**.</span></span> <span data-ttu-id="44c9e-127">새 이름은 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-127">The new name is persisted to the server.</span></span>  
  
 <span data-ttu-id="44c9e-128">다이어그램에서 표시되는 섹션을 클립보드로 복사하려면 **그래프 뷰 복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-128">To copy the visible section of the diagram to the Clipboard, click **Copy Graph View**.</span></span> <span data-ttu-id="44c9e-129">전체 다이어그램을 복사하려면 **전체 그래프 복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-129">To copy the complete diagram, click **Copy Entire Graph**.</span></span> <span data-ttu-id="44c9e-130">또한 **확대** 와 **축소**를 사용하여 확대 및 축소할 수 있으며 **창에 맞게 다이어그램 크기 조정**을 사용하여 다이어그램을 화면에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-130">You can also zoom in and out by using **Zoom In** and **Zoom Out**, or you can fit the diagram to the screen by using **Scale Diagram to Fit in Window**.</span></span>  
  
 [<span data-ttu-id="44c9e-131">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="44c9e-131">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a><span data-ttu-id="44c9e-132">클러스터 프로필</span><span class="sxs-lookup"><span data-stu-id="44c9e-132">Cluster Profiles</span></span>  
 <span data-ttu-id="44c9e-133">**클러스터 프로필** 탭을 사용하여 모델의 알고리즘이 만드는 클러스터를 전체적으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-133">The **Cluster Profiles** tab provides an overall view of the clusters that the algorithm in your model creates.</span></span> <span data-ttu-id="44c9e-134">이 보기에서는 각 클러스터에서의 특성 분포와 함께 각 특성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-134">This view displays each attribute, together with the distribution of the attribute in each cluster.</span></span> <span data-ttu-id="44c9e-135">각 셀의 정보 팁에서는 분포 통계를 표시하고 각 열 제목의 정보 팁에서는 클러스터 채우기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-135">An InfoTip for each cell displays the distribution statistics, and an InfoTip for each column heading displays the cluster population.</span></span> <span data-ttu-id="44c9e-136">불연속 특성은 색이 지정된 막대로 표시되고 연속 특성은 각 클러스터의 평균 편차 및 표준 편차를 나타내는 다이아몬드 차트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-136">Discrete attributes are shown as colored bars, and continuous attributes are shown as a diamond chart that represents the mean and standard deviation in each cluster.</span></span> <span data-ttu-id="44c9e-137">**히스토그램 막대** 옵션은 히스토그램에 표시되는 막대의 수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-137">The **Histogram bars** option controls the number of bars that are visible in the histogram.</span></span> <span data-ttu-id="44c9e-138">선택한 것보다 더 많은 막대가 있는 경우 중요성이 가장 높은 막대가 유지되고 나머지 막대는 모두 회색 버킷으로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-138">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into a gray bucket.</span></span>  
  
 <span data-ttu-id="44c9e-139">클러스터의 기본 이름을 좀 더 구체적인 이름으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-139">You can change the default names of the clusters, to make the names more descriptive.</span></span> <span data-ttu-id="44c9e-140">클러스터의 열 제목을 마우스 오른쪽 단추로 클릭하고 **클러스터 이름 바꾸기**를 선택하여 클러스터의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-140">Rename a cluster by right-clicking its column heading and selecting **Rename cluster**.</span></span> <span data-ttu-id="44c9e-141">**열 숨기기**를 선택하여 클러스터를 숨길 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-141">You can also hide clusters by selecting **Hide column**.</span></span>  
  
 <span data-ttu-id="44c9e-142">클러스터를 더 크고 자세하게 보여 주는 창을 열려면 **상태** 열의 셀이나 뷰어의 히스토그램을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-142">To open a window that provides a larger, more detailed view of the clusters, double-click either a cell in the **States** column or a histogram in the viewer.</span></span>  
  
 <span data-ttu-id="44c9e-143">해당 클러스터에 대한 중요도 순으로 특성을 정렬하려면 열 제목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-143">Click a column heading to sort the attributes in order of importance for that cluster.</span></span> <span data-ttu-id="44c9e-144">열을 끌어 뷰어에서 열을 다시 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-144">You can also drag columns to reorder them in the viewer.</span></span>  
  
 [<span data-ttu-id="44c9e-145">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="44c9e-145">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="44c9e-146">클러스터 특징</span><span class="sxs-lookup"><span data-stu-id="44c9e-146">Cluster Characteristics</span></span>  
 <span data-ttu-id="44c9e-147">**클러스터 특징** 탭을 사용하려면 **클러스터** 목록에서 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-147">To use the **Cluster Characteristics** tab, select a cluster from the **Cluster** list.</span></span> <span data-ttu-id="44c9e-148">클러스터를 선택한 다음 해당 클러스터를 구성하는 특징을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-148">After you select a cluster, you can examine the characteristics that make up that specific cluster.</span></span> <span data-ttu-id="44c9e-149">클러스터에 포함된 특성은 **변수** 열에 나열되어 있으며 나열된 특성의 상태는 **값** 열에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-149">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span> <span data-ttu-id="44c9e-150">특성 상태는 클러스터에서 나타날 확률이 높은 순서에 따라 중요도 순으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-150">Attribute states are listed in order of importance, described by the probability that they will appear in the cluster.</span></span> <span data-ttu-id="44c9e-151">이러한 확률은 **확률** 열에 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-151">The probability is shown in the **Probability** column.</span></span>  
  
 [<span data-ttu-id="44c9e-152">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="44c9e-152">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="44c9e-153">클러스터 판별</span><span class="sxs-lookup"><span data-stu-id="44c9e-153">Cluster Discrimination</span></span>  
 <span data-ttu-id="44c9e-154">**클러스터 판별** 탭을 사용하여 두 클러스터 간 특성을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-154">You can use the **Cluster Discrimination** tab to compare attributes between two clusters.</span></span> <span data-ttu-id="44c9e-155">**클러스터 1** 및 **클러스터 2** 목록을 사용하여 비교할 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-155">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span> <span data-ttu-id="44c9e-156">뷰어는 클러스터 간의 가장 중요한 차이점을 확인하여 해당 차이점과 연결된 특성 상태를 중요도 순으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-156">The viewer determines the most important differences between the clusters, and displays the attribute states that are associated with the differences, in order of importance.</span></span> <span data-ttu-id="44c9e-157">특성의 오른쪽에 있는 막대는 상태가 유사한 클러스터를 보여 주며 막대의 크기는 상태가 클러스터와 유사한 정도를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44c9e-157">A bar to the right of the attribute shows which cluster the state favors, and the size of the bar shows how strongly the state favors the cluster.</span></span>  
  
 [<span data-ttu-id="44c9e-158">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="44c9e-158">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="44c9e-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44c9e-159">See Also</span></span>  
 <span data-ttu-id="44c9e-160">[Microsoft 클러스터링 알고리즘](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="44c9e-160">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="44c9e-161">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="44c9e-161">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="44c9e-162">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="44c9e-162">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="44c9e-163">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="44c9e-163">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="44c9e-164">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="44c9e-164">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
