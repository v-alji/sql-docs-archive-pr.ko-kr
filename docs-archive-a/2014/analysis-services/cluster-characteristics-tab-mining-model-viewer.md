---
title: 클러스터 특징 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648062"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="d3b82-102">클러스터 특징 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="d3b82-102">Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="d3b82-103">**클러스터 특징** 탭에서는 클러스터링 모델에 있는 클러스터의 특징이나 모델에 있는 모든 사례 집합의 특징을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-103">The **Cluster Characteristics** tab lets you explore the characteristics of a cluster in a clustering model, or the set of all cases in the model.</span></span> <span data-ttu-id="d3b82-104">이 그래프에는 다른 클러스터와 비교한 각 특성-값 쌍의 중요도가 클러스터를 정의하는 특징으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-104">The graph shows the importance of each attribute-value pair as a characteristic that defines the cluster, in comparison with other clusters.</span></span>  
  
 <span data-ttu-id="d3b82-105">**자세한 내용:** [Microsoft 클러스터링 알고리즘](data-mining/microsoft-clustering-algorithm.md), [Microsoft 클러스터 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="d3b82-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="d3b82-106">옵션</span><span class="sxs-lookup"><span data-stu-id="d3b82-106">Options</span></span>  
 <span data-ttu-id="d3b82-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="d3b82-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="d3b82-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="d3b82-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="d3b82-109">**Mining Model**</span></span>  
 <span data-ttu-id="d3b82-110">현재 마이닝 구조에서 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="d3b82-111">사용자 지정 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-111">The mining model will open in the custom viewer.</span></span>  
  
 <span data-ttu-id="d3b82-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="d3b82-112">**Viewer**</span></span>  
 <span data-ttu-id="d3b82-113">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="d3b82-114">이 모델 유형과 연결된 사용자 지정 뷰어 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-114">You can use the custom viewer associated with this model type, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="d3b82-115">또한 사용 가능한 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-115">You can also use any plug-in viewers that are available.</span></span>  
  
 <span data-ttu-id="d3b82-116">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="d3b82-116">**Cluster**</span></span>  
 <span data-ttu-id="d3b82-117">보려는 클러스터를 선택하거나 모델의 특성 분포를 전체적으로 보려면 **채우기(모두)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-117">Choose the cluster you want to view, or choose **Population (All)** to see the distribution of attributes for the model as a whole.</span></span>  
  
 <span data-ttu-id="d3b82-118">**특성\<cluster>**</span><span class="sxs-lookup"><span data-stu-id="d3b82-118">**Characteristics for \<cluster>**</span></span>  
 <span data-ttu-id="d3b82-119">이 그래프에는 선택한 클러스터의 특징을 설명하는 다음 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-119">The graph contains the following columns, which describe the characteristics of the selected cluster.</span></span>  
  
|<span data-ttu-id="d3b82-120">값</span><span class="sxs-lookup"><span data-stu-id="d3b82-120">Value</span></span>|<span data-ttu-id="d3b82-121">Description</span><span class="sxs-lookup"><span data-stu-id="d3b82-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3b82-122">**변수**</span><span class="sxs-lookup"><span data-stu-id="d3b82-122">**Variable**</span></span>|<span data-ttu-id="d3b82-123">선택한 클러스터에 있는 마이닝 모델의 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-123">Lists the attributes from the mining model that are found in the selected cluster.</span></span>|  
|<span data-ttu-id="d3b82-124">**값**</span><span class="sxs-lookup"><span data-stu-id="d3b82-124">**Values**</span></span>|<span data-ttu-id="d3b82-125">현재 선택한 클러스터에 있는 현재 특성 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-125">Lists the values of the current attributes that are found in the currently selected cluster.</span></span>|  
|<span data-ttu-id="d3b82-126">**Probability**</span><span class="sxs-lookup"><span data-stu-id="d3b82-126">**Probability**</span></span>|<span data-ttu-id="d3b82-127">이 막대는 이 클러스터의 특징적인 기능으로 특성-값 쌍의 강도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-127">The bar indicates the strength of the attribute-value pair as a distinguishing feature of this cluster.</span></span> <span data-ttu-id="d3b82-128">막대를 마우스로 가리키면 백분율로 표시된 확률 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-128">If you hover the mouse over the bar, you can see the probability value, represented as a percentage.</span></span> <span data-ttu-id="d3b82-129">이는 특정 사례에서 이 특성 및 값 조합이 제공된 경우 해당 사례가 이 클러스터에 속할 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3b82-129">What this indicates is, given this attribute and value combination in any particular case, what is the probability that the case would belong in this cluster.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3b82-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3b82-130">See Also</span></span>  
 <span data-ttu-id="d3b82-131">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d3b82-131">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d3b82-132">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="d3b82-132">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="d3b82-133">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="d3b82-133">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
