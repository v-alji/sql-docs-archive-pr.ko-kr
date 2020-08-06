---
title: 클러스터 판별 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35435736bcdf1b1962de6babace2def953bbfff0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648686"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="269c9-102">클러스터 판별 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="269c9-102">Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="269c9-103">**클러스터 판별** 탭을 사용하여 클러스터링 모델에 있는 두 클러스터를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-103">Use the **Cluster Discrimination** tab to compare two clusters that exist in a clustering model.</span></span> <span data-ttu-id="269c9-104">특성 및 값의 여러 가지 조합이 클러스터 내에서 표시되는 방식을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-104">You can see how different combinations of attributes and values are represented within the clusters.</span></span>  
  
 <span data-ttu-id="269c9-105">**자세한 내용:** [Microsoft 클러스터링 알고리즘](data-mining/microsoft-clustering-algorithm.md), [Microsoft 클러스터 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="269c9-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="269c9-106">옵션</span><span class="sxs-lookup"><span data-stu-id="269c9-106">Options</span></span>  
 <span data-ttu-id="269c9-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="269c9-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="269c9-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="269c9-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="269c9-109">**Mining Model**</span></span>  
 <span data-ttu-id="269c9-110">현재 마이닝 구조에서 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="269c9-111">관련 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="269c9-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="269c9-112">**Viewer**</span></span>  
 <span data-ttu-id="269c9-113">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="269c9-114">클러스터링 모델의 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-114">You can use the custom viewer for clustering models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="269c9-115">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="269c9-116">**클러스터 1**</span><span class="sxs-lookup"><span data-stu-id="269c9-116">**Cluster 1**</span></span>  
 <span data-ttu-id="269c9-117">다른 클러스터와 비교할 수 있도록 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-117">Select a cluster, so that you can compare it to another cluster.</span></span>  
  
 <span data-ttu-id="269c9-118">**클러스터 2**</span><span class="sxs-lookup"><span data-stu-id="269c9-118">**Cluster 2**</span></span>  
 <span data-ttu-id="269c9-119">마이닝 모델의 클러스터 목록에서 **클러스터 1**과 비교할 두 번째 클러스터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-119">Select a second cluster from the list of clusters in the mining model, to compare to **Cluster 1**.</span></span> <span data-ttu-id="269c9-120">클러스터를 해당 보수와 비교할 수도 있습니다. 즉, 선택한 클러스터에 없는 모델의 모든 사례와 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-120">You can also compare a cluster to its complement, meaning all cases in the model except those in the selected cluster.</span></span>  
  
 <span data-ttu-id="269c9-121">**및에 대 한 판별 점수 \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="269c9-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="269c9-122">그래프의 열에서는 각 특성-값 쌍과 선택한 두 클러스터의 관련성에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-122">The columns in the graph provide information about how each attribute-value pair is related to the two selected clusters.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="269c9-123">**변수**</span><span class="sxs-lookup"><span data-stu-id="269c9-123">**Variables**</span></span>|<span data-ttu-id="269c9-124">마이닝 모델의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-124">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="269c9-125">**값**</span><span class="sxs-lookup"><span data-stu-id="269c9-125">**Values**</span></span>|<span data-ttu-id="269c9-126">**변수**에서 선택한 특성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-126">A value of the attribute selected in **Variables**.</span></span>|  
|<span data-ttu-id="269c9-127">**우위\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="269c9-127">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="269c9-128">왼쪽의 막대 그래프는 선택한 특성-값 쌍이 **클러스터 1**에서 선택한 클러스터의 특징을 나타낼 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-128">The bar graph on the left represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 1**.</span></span> <span data-ttu-id="269c9-129">막대 위에 마우스를 놓으면 백분율로 표시된 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-129">You can pause the mouse over the bar to see the value, represented as a percentage.</span></span> <span data-ttu-id="269c9-130">값이 0 인 경우에도 클러스터에서 특성-값이 누락 된 것을 의미 하지는 않습니다. 배포는 다른 클러스터에 대 한 클러스터를 강력 하 게 우위를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-130">Note that even if the value is zero, it doesn't mean the attribute-value is necessarily missing from the cluster, just that the distribution strongly favors one cluster over the other.</span></span>|  
|<span data-ttu-id="269c9-131">**우위\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="269c9-131">**Favors \<cluster 2>**</span></span>|<span data-ttu-id="269c9-132">오른쪽의 막대 그래프는 선택한 특성-값 쌍이 **클러스터 2**에서 선택한 클러스터의 특징을 나타낼 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="269c9-132">The bar graph on the right represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="269c9-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="269c9-133">See Also</span></span>  
 <span data-ttu-id="269c9-134">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="269c9-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="269c9-135">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="269c9-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="269c9-136">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="269c9-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
