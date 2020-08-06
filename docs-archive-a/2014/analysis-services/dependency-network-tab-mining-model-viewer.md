---
title: 종속성 네트워크 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
ms.openlocfilehash: 94ce82524445ffb8999c671c736087362ef0adfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728935"
---
# <a name="dependency-network-tab-mining-model-viewer"></a><span data-ttu-id="597b7-102">종속성 네트워크 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="597b7-102">Dependency Network Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="597b7-103">**종속성 네트워크** 탭에서는 마이닝 모델에 포함된 모든 특성에 대한 그래픽 뷰를 제공하고 특성의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-103">The **Dependency Net** tab provides a graphical view of all attributes that the mining model contains, and shows how the attributes are related.</span></span>  
  
 <span data-ttu-id="597b7-104">**종속성 네트워크**  탭은 Naïve Bayes 모델, 의사 결정 트리 모델 및 연결 모델을 비롯한 몇 가지 유형의 마이닝 모델에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-104">The **Dependency Net**  tab is used for several types of mining models, including Naïve Bayes models, decision tree models, and association models.</span></span> <span data-ttu-id="597b7-105">이러한 모델의 컨텍스트에서 **종속성 네트워크**  탭의 내용을 해석하는 방법은 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="597b7-105">For more information about how to interpret the contents of the **Dependency Net**  tab in the context of these models, see the following links:</span></span>  
  
 [<span data-ttu-id="597b7-106">Microsoft 트리 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="597b7-106">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [<span data-ttu-id="597b7-107">Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="597b7-107">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [<span data-ttu-id="597b7-108">Microsoft 연결 규칙 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="597b7-108">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a><span data-ttu-id="597b7-109">옵션</span><span class="sxs-lookup"><span data-stu-id="597b7-109">Options</span></span>  
 <span data-ttu-id="597b7-110">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="597b7-110">**Refresh viewer content**</span></span>  
 <span data-ttu-id="597b7-111">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-111">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="597b7-112">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="597b7-112">**Mining Model**</span></span>  
 <span data-ttu-id="597b7-113">현재 마이닝 구조에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-113">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="597b7-114">사용자 지정 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-114">The mining model will open in a custom viewer.</span></span> <span data-ttu-id="597b7-115">각 모델에 사용되는 사용자 지정 뷰어의 유형은 모델을 만드는 데 사용한 알고리즘에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-115">The type of custom viewer that is used for each model is determined by the algorithm that you used to create the model.</span></span>  
  
 <span data-ttu-id="597b7-116">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="597b7-116">**Viewer**</span></span>  
 <span data-ttu-id="597b7-117">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-117">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="597b7-118">각 마이닝 모델에 대해 제공되는 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-118">For each model, you can use either the custom viewer is provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="597b7-119">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-119">You can also use plug-in viewers if available.</span></span> <span data-ttu-id="597b7-120">Microsoft 콘텐츠 트리 뷰어는 모든 모델에서 사용할 수 있으며 HTML 테이블로 모델 콘텐츠를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-120">The Microsoft Content Tree Viewer can be used with all models, and represents the model content in an HTML table.</span></span>  
  
 <span data-ttu-id="597b7-121">**확대**</span><span class="sxs-lookup"><span data-stu-id="597b7-121">**Zoom In**</span></span>  
 <span data-ttu-id="597b7-122">특성을 자세히 볼 수 있도록 다이어그램을 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-122">Zoom in to the diagram, so that you can see the attributes in more detail.</span></span>  
  
 <span data-ttu-id="597b7-123">**축소**</span><span class="sxs-lookup"><span data-stu-id="597b7-123">**Zoom Out**</span></span>  
 <span data-ttu-id="597b7-124">특성을 더 보고 특성 간의 링크를 볼 수 있도록 다이어그램을 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-124">Zoom out from the diagram, so that you can see more attributes and the links between them.</span></span>  
  
 <span data-ttu-id="597b7-125">**그래프 뷰 복사**</span><span class="sxs-lookup"><span data-stu-id="597b7-125">**Copy Graph View**</span></span>  
 <span data-ttu-id="597b7-126">다이어그램에서 표시되는 섹션을 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-126">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="597b7-127">**전체 그래프 복사**</span><span class="sxs-lookup"><span data-stu-id="597b7-127">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="597b7-128">전체 다이어그램을 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-128">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="597b7-129">**링크**</span><span class="sxs-lookup"><span data-stu-id="597b7-129">**Links**</span></span>  
 <span data-ttu-id="597b7-130">특성의 오른쪽에 있는 슬라이더를 조정하여 뷰어에 표시되는 링크(가장자리) 및 노드의 수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-130">Adjust how many links (edges) and nodes the viewer shows by adjusting the slider to the right of the attributes.</span></span> <span data-ttu-id="597b7-131">슬라이더 막대를 아래로 끌면 임계값이 증가하므로 가장 강력한 링크만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-131">Dragging the slider bar down increases the threshold value, so that only the strongest links are shown.</span></span> <span data-ttu-id="597b7-132">각 모델 유형에 대해 약간 다른 값이 그래프의 링크를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-132">For each model type, a slightly different value is used to represent the links in the graph:</span></span>  
  
-   <span data-ttu-id="597b7-133">**의사 결정 트리** 모델에서 가장자리는 분할 점수에 의해 부분적으로 결정되는 연결의 예측 강도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-133">In a **decision tree** model, the edges represent the predictive strength of the connection, determined partly by the split score.</span></span>  
  
-   <span data-ttu-id="597b7-134">**Naïve Bayes** 모델에서 두 노드 간의 링크는 양방향으로 이동할 수 있습니다. 즉, 노드 A는 노드 B를 예측할 수 있고 노드 B는 노드 A를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-134">In a **Naïve Bayes** model, the links between two nodes can go either way: that is, node A can predict the node B, and vice versa.</span></span> <span data-ttu-id="597b7-135">가장자리와 연결된 점수는 연결의 예측 강도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-135">The score associated with the edge represents the predictive strength of the connection.</span></span>  
  
-   <span data-ttu-id="597b7-136">**연결 모델**에서 노드 간의 가장자리는 두 항목 집합을 연결하는 규칙의 중요도 점수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-136">In an **association model**, the edges between nodes represent the importance score of the rule that connects two itemsets.</span></span>  
  
 <span data-ttu-id="597b7-137">모든 모델 유형에 대한 일반 규칙은 링크가 강력할수록 두 특성 간의 예측 관계도 강력하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="597b7-137">A general rule for all model types is that the stronger the link, the stronger the predictive relationship between the two attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597b7-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="597b7-138">See Also</span></span>  
 <span data-ttu-id="597b7-139">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="597b7-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="597b7-140">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="597b7-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="597b7-141">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="597b7-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
