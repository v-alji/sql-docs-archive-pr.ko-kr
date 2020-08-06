---
title: 마이닝 모델 뷰어 (데이터 마이닝 모델 디자이너) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4cc1c9d72a08ef49ed2f4f466953d2ba61394178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740564"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a><span data-ttu-id="c201a-102">마이닝 모델 뷰어(데이터 마이닝 모델 디자이너)</span><span class="sxs-lookup"><span data-stu-id="c201a-102">Mining Model Viewers (Data Mining Model Designer)</span></span>
  <span data-ttu-id="c201a-103">**마이닝 모델 뷰어** 탭을 사용하여 마이닝 구조에 포함된 마이닝 모델을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-103">Use the **Mining Model Viewer** tab to explore the mining models that a mining structure contains.</span></span>

 <span data-ttu-id="c201a-104">먼저 마이닝 모델을 선택한 다음 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-104">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="c201a-105">항상 각 모델에는 여러 탭을 포함할 수 있는 사용자 지정 뷰어와 일반 뷰어라는 두 개의 뷰어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-105">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>

 <span data-ttu-id="c201a-106">각 뷰어를 사용하는 방법을 보여 주는 연습은 [데이터 마이닝 모델 뷰어](data-mining/data-mining-model-viewers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c201a-106">For a walkthrough of how to use each viewer, see [Data Mining Model Viewers](data-mining/data-mining-model-viewers.md).</span></span>

## <a name="common-options"></a><span data-ttu-id="c201a-107">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="c201a-107">Common Options</span></span>
 <span data-ttu-id="c201a-108">**뷰어 내용 새로 고침** 뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-108">**Refresh viewer content** Reload the mining model in the viewer.</span></span>

 <span data-ttu-id="c201a-109">**마이닝 모델** 현재 마이닝 구조에서 볼 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-109">**Mining Model** Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="c201a-110">마이닝 모델은 연결된 사용자 지정 뷰어에서 먼저 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-110">The mining model will first open in its associated custom viewer.</span></span>

 <span data-ttu-id="c201a-111">**뷰어** 선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-111">**Viewer** Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="c201a-112">이 목록 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에는 각 마이닝 모델에 대해 제공 하는 뷰어, [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어 및 모든 플러그 인 뷰어가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-112">This list includes the viewers that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides for each mining model, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer, and any plug-in viewers.</span></span>

 <span data-ttu-id="c201a-113">다음 다이어그램에서는 같은 모델에 대해 사용자 지정 뷰어와 일반 뷰어를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-113">The following diagram shows a custom viewer and the generic viewer for the same model.</span></span>

-   <span data-ttu-id="c201a-114">위쪽 다이어그램은 Microsoft Time Series 알고리즘을 기반으로 하는 마이닝 모델에 대한 뷰어를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-114">The upper diagram shows the viewer for a mining model based on the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="c201a-115">이 사용자 지정 뷰어에서는 시계열 그래프를 자동으로 만들고 5개의 예측을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-115">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>

-   <span data-ttu-id="c201a-116">아래쪽 다이어그램은 **Microsoft 일반 콘텐츠 트리 뷰어**를 사용하여 표시되는 동일한 모델을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-116">The lower diagram shows the same model displayed using the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="c201a-117">이 뷰어에는 표준화된 스키마에 따라 마이닝 모델의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-117">This viewer presents the contents of the mining model according to a standardized schema.</span></span> <span data-ttu-id="c201a-118">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c201a-118">For more information, see [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](microsoft-generic-content-tree-viewer-data-mining.md).</span></span>

 <span data-ttu-id="c201a-119">![마이닝 모델 디자이너 개요](media/generic-mining-model-tab1.gif "마이닝 모델 디자이너 개요")</span><span class="sxs-lookup"><span data-stu-id="c201a-119">![Overview of mining model designer](media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>

## <a name="viewers-and-their-components"></a><span data-ttu-id="c201a-120">뷰어 및 해당 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c201a-120">Viewers and Their Components</span></span>
 <span data-ttu-id="c201a-121">선택한 모델에 따라, 선택된 데이터 마이닝 모델을 만들 때 사용한 알고리즘에 맞게 조정된 각기 다른 사용자 지정 뷰어가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-121">Depending on the model that you select, you will see a different custom viewer, tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="c201a-122">각 사용자 지정 뷰어에는 모델의 패턴 및 통계를 탐색하는 데 도움이 되는 다양한 도구 및 대화 상자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-122">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model.</span></span>

 <span data-ttu-id="c201a-123">다음 목록에서는 각 사용자 지정 뷰어에 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c201a-123">The following list describes the options in each of the custom viewers.</span></span>

### <a name="microsoft-association-rules-algorithm"></a><span data-ttu-id="c201a-124">Microsoft 연결 규칙 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-124">Microsoft Association Rules Algorithm</span></span>

-   [<span data-ttu-id="c201a-125">Microsoft 연결 규칙 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-125">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   [<span data-ttu-id="c201a-126">항목 집합 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-126">Itemsets Tab &#40;Mining Model Viewer&#41;</span></span>](itemsets-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-127">마이닝 모델 뷰어 &#40;규칙 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-127">Rules Tab &#40;Mining Model Viewer&#41;</span></span>](rules-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-128">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-128">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

### <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="c201a-129">Microsoft Clustering Algorithm</span><span class="sxs-lookup"><span data-stu-id="c201a-129">Microsoft Clustering Algorithm</span></span>

-   [<span data-ttu-id="c201a-130">Microsoft 클러스터 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-130">Browse a Model Using the Microsoft Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   [<span data-ttu-id="c201a-131">마이닝 모델 뷰어를 &#40;클러스터 다이어그램 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-131">Cluster Diagram Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-diagram-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-132">마이닝 모델 뷰어를 &#40;클러스터 프로필 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-132">Cluster Profiles Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-133">마이닝 모델 뷰어를 &#40;클러스터 특징 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-133">Cluster Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-134">클러스터 판별 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-134">Cluster Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-discrimination-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-135">마이닝 범례 대화 상자 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-135">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-decision-tree-algorithm"></a><span data-ttu-id="c201a-136">Microsoft 의사 결정 트리 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-136">Microsoft Decision Tree Algorithm</span></span>

-   [<span data-ttu-id="c201a-137">Microsoft 트리 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-137">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   [<span data-ttu-id="c201a-138">마이닝 모델 뷰어를 &#40;의사 결정 트리 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-138">Decision Tree Tab &#40;Mining Model Viewer&#41;</span></span>](decision-tree-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-139">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-139">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-140">마이닝 범례 대화 상자 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-140">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="c201a-141">Microsoft 선형 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-141">Microsoft Linear Regression Algorithm</span></span>

-   [<span data-ttu-id="c201a-142">Microsoft 신경망 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-142">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [<span data-ttu-id="c201a-143">마이닝 모델 뷰어를 &#40;의사 결정 트리 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-143">Decision Tree Tab &#40;Mining Model Viewer&#41;</span></span>](decision-tree-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-144">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-144">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-145">마이닝 범례 대화 상자 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-145">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="c201a-146">Microsoft 로지스틱 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-146">Microsoft Logistic Regression Algorithm</span></span>

-   [<span data-ttu-id="c201a-147">Microsoft 신경망 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-147">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a><span data-ttu-id="c201a-148">Microsoft Naive Bayes 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-148">Microsoft Naïve Bayes Algorithm</span></span>

-   [<span data-ttu-id="c201a-149">Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-149">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   [<span data-ttu-id="c201a-150">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-150">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-151">마이닝 모델 뷰어 &#40;특성 프로필 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-151">Attribute Profiles Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-152">마이닝 모델 뷰어 &#40;특성 특징 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-152">Attribute Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-153">마이닝 모델 뷰어를 &#40;특성 판별 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-153">Attribute Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-discrimination-tab-mining-model-viewer.md)

### <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="c201a-154">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="c201a-154">Microsoft Neural Network Algorithm</span></span>

-   [<span data-ttu-id="c201a-155">Microsoft 신경망 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-155">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [<span data-ttu-id="c201a-156">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-156">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-157">신경망 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-157">Neural Network &#40;Mining Model Viewer&#41;</span></span>](neural-network-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-158">마이닝 모델 뷰어를 &#40;노드 찾기 대화 상자&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-158">Find Node Dialog Box &#40;Mining Model Viewer&#41;</span></span>](find-node-dialog-box-mining-model-viewer.md)

### <a name="microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="c201a-159">Microsoft 시퀀스 클러스터링 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-159">Microsoft Sequence Clustering Algorithm</span></span>

-   [<span data-ttu-id="c201a-160">Microsoft 시퀀스 클러스터 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-160">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   [<span data-ttu-id="c201a-161">시퀀스 클러스터링 클러스터 다이어그램 탭 &#40;마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="c201a-161">Sequence Clustering Cluster Diagram Tab &#40;Mining Model Viewer</span></span>](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-162">마이닝 모델 뷰어 &#40;시퀀스 클러스터링 클러스터 프로필 탭</span><span class="sxs-lookup"><span data-stu-id="c201a-162">Sequence Clustering Cluster Profiles Tab &#40;Mining Model Viewer</span></span>](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-163">시퀀스 클러스터링 클러스터 특징 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-163">Sequence Clustering Cluster Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-164">시퀀스 클러스터링 클러스터 판별 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-164">Sequence Clustering Cluster Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="c201a-165">시퀀스 클러스터링 클러스터 전환 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-165">Sequence Clustering Cluster Transition Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)

### <a name="microsoft-time-series-algorithm"></a><span data-ttu-id="c201a-166">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c201a-166">Microsoft Time Series Algorithm</span></span>

-   [<span data-ttu-id="c201a-167">Microsoft 시계열 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c201a-167">Browse a Model Using the Microsoft Time Series Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   [<span data-ttu-id="c201a-168">모델 탭 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-168">Model Tab &#40;Mining Model Viewers&#41;</span></span>](model-tab-mining-model-viewers.md)

    -   [<span data-ttu-id="c201a-169">마이닝 모델 뷰어를 &#40;차트 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-169">Chart Tab &#40;Mining Model Viewers&#41;</span></span>](chart-tab-mining-model-viewers.md)

    -   [<span data-ttu-id="c201a-170">마이닝 범례 대화 상자 &#40;마이닝 모델 뷰어&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-170">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

## <a name="see-also"></a><span data-ttu-id="c201a-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c201a-171">See Also</span></span>
 <span data-ttu-id="c201a-172">마이닝 [모델 뷰 &#40;데이터](mining-models-view-data-mining-model-designer.md) 마이닝 모델 디자이너&#41;마이닝 [구조 뷰 &#40;데이터 마이닝 모델 디자이너&#41;](mining-structure-view-data-mining-model-designer.md) [마이닝 정확도 차트 디자이너 &#40;](mining-accuracy-chart-designer-data-mining.md) 데이터 마이닝&#41;[예측 쿼리 작성기 &#40;데이터 마이닝](prediction-query-builder-data-mining.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="c201a-172">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) [Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) [Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) [Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)</span></span>


