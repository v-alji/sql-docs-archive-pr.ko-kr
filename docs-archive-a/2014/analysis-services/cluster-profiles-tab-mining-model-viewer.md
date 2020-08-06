---
title: 클러스터 프로필 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7ec1ce5b5204ae81a9313ca7b7e5df58c98c5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648682"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a><span data-ttu-id="69195-102">클러스터 프로필 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="69195-102">Cluster Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="69195-103">**클러스터 프로필** 탭을 사용하여 알고리즘이 클러스터링 모델 내에서 발견한 클러스터를 전체적으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69195-103">Use the **Cluster Profiles** tab for an overall view of the clusters that the algorithm discovered within a clustering model.</span></span> <span data-ttu-id="69195-104">이 탭에는 각 클러스터에서의 특성 분포와 함께 각 특성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="69195-104">The tab displays each attribute, together with the distribution of the attribute in each cluster.</span></span>  
  
 <span data-ttu-id="69195-105">**자세한 내용:** [Microsoft 클러스터링 알고리즘](data-mining/microsoft-clustering-algorithm.md), [Microsoft 클러스터 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="69195-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="69195-106">옵션</span><span class="sxs-lookup"><span data-stu-id="69195-106">Options</span></span>  
 <span data-ttu-id="69195-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="69195-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="69195-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="69195-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="69195-109">**Mining Model**</span></span>  
 <span data-ttu-id="69195-110">현재 마이닝 구조에서 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="69195-111">관련 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="69195-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="69195-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="69195-112">**Viewer**</span></span>  
 <span data-ttu-id="69195-113">선택한 마이닝 모델을 보는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="69195-114">마이닝 모델에 대해 제공되는 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69195-114">You can use the custom viewer for the mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="69195-115">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69195-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="69195-116">**범례 표시**</span><span class="sxs-lookup"><span data-stu-id="69195-116">**Show Legend**</span></span>  
 <span data-ttu-id="69195-117">**상태** 열의 값에 대한 뷰어 색의 매핑을 보여 주는 키를 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-117">Select this option to display a key that shows the mapping of colors in the viewer to values in the **States** column.</span></span>  
  
 <span data-ttu-id="69195-118">**히스토그램 막대**</span><span class="sxs-lookup"><span data-stu-id="69195-118">**Histogram Bars**</span></span>  
 <span data-ttu-id="69195-119">각 히스토그램에 포함되는 상태 수를 제어하려면 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-119">Change this value to control how many states are included in each histogram.</span></span> <span data-ttu-id="69195-120">표시하도록 선택한 것보다 많은 상태가 있는 경우 확률이 가장 높은 상태가 히스토그램에 표시되고 나머지 상태는 모두 **기타**로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="69195-120">If there are more states than you choose to display, the states with the highest probability are shown in the histogram, and the remaining states are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="69195-121">**특성**</span><span class="sxs-lookup"><span data-stu-id="69195-121">**Attributes**</span></span>  
 <span data-ttu-id="69195-122">클러스터링 모델에 있는 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-122">Lists the columns that are in the clustering model.</span></span> <span data-ttu-id="69195-123">각 특성의 히스토그램에는 알고리즘으로 식별된 클러스터 간에 특성이 어떻게 분포되어 있는지 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="69195-123">The histograms for each attribute show how the attribute is distributed among the clusters identified by the algorithm.</span></span>  
  
 <span data-ttu-id="69195-124">**상태**</span><span class="sxs-lookup"><span data-stu-id="69195-124">**States**</span></span>  
 <span data-ttu-id="69195-125">클러스터의 해당 행에서 각 상태를 나타내는 색을 지정하는 키를 제공하거나 연속 숫자 값의 분포를 나타내는 다이아몬드가 있는 슬라이더를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69195-125">Provides a key that either denotes what color represents each state in the corresponding row of clusters, or a slider with diamond that indicates the distribution of continuous numeric values.</span></span> <span data-ttu-id="69195-126">**범례 표시** 확인란을 사용하여 이 열을 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69195-126">You can show or hide this column by using the **Show Legend** check box.</span></span>  
  
 <span data-ttu-id="69195-127">**클러스터 프로필**</span><span class="sxs-lookup"><span data-stu-id="69195-127">**Cluster Profiles**</span></span>  
 <span data-ttu-id="69195-128">이 섹션에는 모델의 각 클러스터에 대한 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="69195-128">This section contains a column for each cluster in the model.</span></span> <span data-ttu-id="69195-129">각 특성에 대해 히스토그램에 해당 클러스터에 대한 특성의 값 분포가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="69195-129">For each attribute, the histogram shows the distribution of the values in the attribute for just that cluster.</span></span> <span data-ttu-id="69195-130">히스토그램을 사용하여 모델의 모든 사례가 아니라 각 특성에 대한 값의 분포를 표시하는 **모집단**에 대한 열도 차트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69195-130">The chart also has a column for **Population**, which also uses histograms to display the distribution of values for each attribute, but for all cases in the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69195-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69195-131">See Also</span></span>  
 <span data-ttu-id="69195-132">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="69195-132">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="69195-133">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="69195-133">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="69195-134">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="69195-134">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
