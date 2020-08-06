---
title: Microsoft 시퀀스 클러스터링 알고리즘 기술 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_SEQUENCE_STATES parameter
- MINIMUM_SUPPORT parameter
- MAXIMUM_STATES parameter
- sequence clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: 251c369d-6b02-4687-964e-39bf55c9b009
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3e09018fad9c291ec1f47bbb776797d634950381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639107"
---
# <a name="microsoft-sequence-clustering-algorithm-technical-reference"></a><span data-ttu-id="c37d0-102">Microsoft 시퀀스 클러스터링 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="c37d0-102">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="c37d0-103">Microsoft 시퀀스 클러스터링 알고리즘은 Markov 체인 분석을 사용하여 정렬된 시퀀스를 식별하고, 이 분석 결과를 클러스터링 기술과 결합하여 모델의 시퀀스 및 기타 특성에 따라 클러스터를 생성하는 하이브리드 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-103">The Microsoft Sequence Clustering algorithm is a hybrid algorithm that uses Markov chain analysis to identify ordered sequences, and combines the results of this analysis with clustering techniques to generate clusters based on the sequences and other attributes in the model.</span></span> <span data-ttu-id="c37d0-104">이 항목에서는 알고리즘의 구현, 알고리즘을 사용자 지정하는 방법 및 시퀀스 클러스터링 모델에 대한 특수한 요구 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-104">This topic describes the implementation of the algorithm, how to customize the algorithm, and special requirements for sequence clustering models.</span></span>  
  
 <span data-ttu-id="c37d0-105">시퀀스 클러스터링 모델을 찾아보고 쿼리하는 방법을 비롯하여 알고리즘에 대한 자세한 내용은 [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c37d0-105">For more general information about the algorithm, including how to browse and query sequence clustering models, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
## <a name="implementation-of-the-microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="c37d0-106">Microsoft 시퀀스 클러스터링 알고리즘 구현</span><span class="sxs-lookup"><span data-stu-id="c37d0-106">Implementation of the Microsoft Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="c37d0-107">Microsoft 시퀀스 클러스터링 모델에서는 Markov 모델을 사용하여 시퀀스를 식별하고 시퀀스의 확률을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-107">The Microsoft Sequence Clustering model uses Markov models to identify sequences and determine the probability of sequences.</span></span> <span data-ttu-id="c37d0-108">Markov 모델은 여러 상태 간의 전환을 저장하는 방향 그래프입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-108">A Markov model is a directed graph that stores the transitions between different states.</span></span> <span data-ttu-id="c37d0-109">Microsoft 시퀀스 클러스터링 알고리즘에서는 Hidden Markov 모델이 아니라 n차 Markov 체인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-109">The Microsoft Sequence Clustering algorithm uses n-order Markov chains, not a Hidden Markov model.</span></span>  
  
 <span data-ttu-id="c37d0-110">Markov 체인의 차수는 현재 상태의 확률을 확인하는 데 사용된 상태 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-110">The number of orders in a Markov chain tells you how many states are used to determine the probability of the current states.</span></span> <span data-ttu-id="c37d0-111">예를 들어 1차 Markov 모델에서 현재 상태의 확률은 이전 상태에 따라서만 달라지고,</span><span class="sxs-lookup"><span data-stu-id="c37d0-111">In a first-order Markov model, the probability of the current state depends only on the previous state.</span></span> <span data-ttu-id="c37d0-112">2차 Markov 체인에서 상태의 확률은 이전의 두 상태에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-112">In a second-order Markov chain, the probability of a state depends on the previous two states, and so forth.</span></span> <span data-ttu-id="c37d0-113">각 Markov 체인의 전환 행렬에는 각 상태 조합에 대한 전환이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-113">For each Markov chain, a transition matrix stores the transitions for each combination of states.</span></span> <span data-ttu-id="c37d0-114">Markov 체인의 길이가 늘어나면 행렬의 크기도 기하급수적으로 늘어나며 행렬이 매우 스파스하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-114">As the length of the Markov chain increases, the size of the matrix also increases exponentially, and the matrix becomes extremely sparse.</span></span> <span data-ttu-id="c37d0-115">또한 그에 따라 처리 시간도 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-115">Processing time also increases proportionally.</span></span>  
  
 <span data-ttu-id="c37d0-116">사이트의 웹 페이지 방문을 분석하는 클릭 동향 분석 예를 사용하여 체인을 시각화하면 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-116">It might be helpful to visualize the chain by using the example of clickstream analysis, which analyzes visits to Web pages on a site.</span></span> <span data-ttu-id="c37d0-117">각 사용자는 각 세션에 대해 긴 클릭 시퀀스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-117">Each user creates a long sequence of clicks for each session.</span></span> <span data-ttu-id="c37d0-118">모델을 만들어 웹 사이트에서의 사용자 동작을 분석할 경우 학습에 사용되는 데이터 집합은 URL의 시퀀스로서, 이는 동일한 클릭 경로의 모든 인스턴스 수를 포함하는 그래프로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-118">When you create a model to analyze user behavior on a Web site, the data set used for training is a sequence of URLs, converted to a graph that includes the count of all instances of the same click path.</span></span> <span data-ttu-id="c37d0-119">예를 들어 이 그래프에는 사용자가 1페이지에서 2페이지로 이동하는 확률(10%), 1페이지에서 3페이지로 이동하는 확률(20%) 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-119">For example, the graph contains the probability that the user moves from page 1 to page 2 (10%), the probability that the user moves from page 1 to page 3 (20%), and so forth.</span></span> <span data-ttu-id="c37d0-120">가능한 모든 경로와 부분 경로를 함께 포함하면 관찰된 단일 경로보다 길고 복잡한 그래프가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-120">When you put all the possible paths and pieces of the paths together, you obtain a graph that might be much longer and more complex than any single observed path.</span></span>  
  
 <span data-ttu-id="c37d0-121">기본적으로 Microsoft 시퀀스 클러스터링 알고리즘에서는 EM(Expectation Maximization) 클러스터링 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-121">By default, the Microsoft Sequence Clustering algorithm uses the Expectation Maximization (EM) method of clustering.</span></span> <span data-ttu-id="c37d0-122">자세한 내용은 [Microsoft 클러스터링 알고리즘 기술 참조](microsoft-clustering-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c37d0-122">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="c37d0-123">순차적 특성과 비순차적 특성이 모두 클러스터링 대상이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-123">The targets of clustering are both the sequential and nonsequential attributes.</span></span> <span data-ttu-id="c37d0-124">각 클러스터는 확률 분포를 사용하여 무작위로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-124">Each cluster is randomly selected using a probability distribution.</span></span> <span data-ttu-id="c37d0-125">각 클러스터에는 전체 경로 집합을 나타내는 Markov 체인과 시퀀스 상태 전환 및 확률이 들어 있는 행렬이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-125">Each cluster has a Markov chain that represents the complete set of paths, and a matrix that contains the sequence state transitions and probabilities.</span></span> <span data-ttu-id="c37d0-126">초기 분포에 따라 특정 클러스터에 있는 특성의 확률(시퀀스 포함)을 계산하는 데는 Bayes 규칙이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-126">Based on the initial distribution, Bayes rule is used to calculate the probability of any attribute, including a sequence, in a specific cluster.</span></span>  
  
 <span data-ttu-id="c37d0-127">Microsoft 시퀀스 클러스터링 알고리즘에서는 모델에 비순차적 특성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-127">The Microsoft Sequence Clustering algorithm supports the additional of nonsequential attributes to the model.</span></span> <span data-ttu-id="c37d0-128">일반적인 클러스터링 모델에서와 마찬가지로 이러한 추가 특성은 순차적 특성과 결합되어 비슷한 특성이 있는 사례의 클러스터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-128">This means that these additional attributes are combined with the sequence attributes to create clusters of cases with similar attributes, just like in a typical clustering model.</span></span>  
  
 <span data-ttu-id="c37d0-129">시퀀스 클러스터링 모델은 일반적인 클러스터링 모델보다 더 많은 클러스터를 만드는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-129">A sequence clustering model tends to create many more clusters than a typical clustering model.</span></span> <span data-ttu-id="c37d0-130">따라서 Microsoft 시퀀스 클러스터링 알고리즘은 *클러스터 분해*를 수행하여 시퀀스 및 기타 특성에 따라 클러스터를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-130">Therefore, the Microsoft Sequence Clustering algorithm performs *cluster decomposition*to separate clusters based on sequences and other attributes.</span></span>  
  
### <a name="feature-selection-in-a-sequence-clustering-model"></a><span data-ttu-id="c37d0-131">시퀀스 클러스터링 모델의 기능 선택</span><span class="sxs-lookup"><span data-stu-id="c37d0-131">Feature Selection in a Sequence Clustering Model</span></span>  
 <span data-ttu-id="c37d0-132">시퀀스를 작성할 때는 기능 선택이 호출되지 않지만 클러스터링 단계에서 기능 선택이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-132">Feature selection is not invoked when building sequences; however, feature selection applies at the clustering stage.</span></span>  
  
|<span data-ttu-id="c37d0-133">모델 형식</span><span class="sxs-lookup"><span data-stu-id="c37d0-133">Model type</span></span>|<span data-ttu-id="c37d0-134">기능 선택 방법</span><span class="sxs-lookup"><span data-stu-id="c37d0-134">Feature Selection Method</span></span>|<span data-ttu-id="c37d0-135">주석</span><span class="sxs-lookup"><span data-stu-id="c37d0-135">Comments</span></span>|  
|----------------|------------------------------|--------------|  
|<span data-ttu-id="c37d0-136">시퀀스 클러스터링</span><span class="sxs-lookup"><span data-stu-id="c37d0-136">Sequence Clustering</span></span>|<span data-ttu-id="c37d0-137">사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="c37d0-137">Not used</span></span>|<span data-ttu-id="c37d0-138">기능 선택이 호출되지 않습니다. 그러나 MINIMUM_SUPPORT 및 MINIMUM_PROBABILIITY 매개 변수의 값을 설정하여 알고리즘의 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-138">Feature selection is not invoked; however, you can control the behavior of the algorithm by setting the value of the parameters MINIMUM_SUPPORT and MINIMUM_PROBABILIITY.</span></span>|  
|<span data-ttu-id="c37d0-139">Clustering</span><span class="sxs-lookup"><span data-stu-id="c37d0-139">Clustering</span></span>|<span data-ttu-id="c37d0-140">흥미도 점수</span><span class="sxs-lookup"><span data-stu-id="c37d0-140">Interestingness score</span></span>|<span data-ttu-id="c37d0-141">클러스터링 알고리즘은 불연속 또는 불연속화된 알고리즘을 사용할 수 있지만 각 특성의 점수는 거리로 계산되며 연속적입니다. 따라서 흥미도 점수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-141">Although the clustering algorithm may use discrete or discretized algorithms, the score of each attribute is calculated as a distance and is continuous; therefore the interestingness score is used.</span></span>|  
  
 <span data-ttu-id="c37d0-142">자세한 내용은 [Feature Selection](../../sql-server/install/feature-selection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c37d0-142">For more information, see [Feature Selection](../../sql-server/install/feature-selection.md).</span></span>  
  
### <a name="optimizing-performance"></a><span data-ttu-id="c37d0-143">성능 최적화</span><span class="sxs-lookup"><span data-stu-id="c37d0-143">Optimizing Performance</span></span>  
 <span data-ttu-id="c37d0-144">Microsoft 시퀀스 클러스터링 알고리즘에서는 다양한 방법으로 처리를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-144">The Microsoft Sequence Clustering algorithm supports various ways to optimize processing:</span></span>  
  
-   <span data-ttu-id="c37d0-145">CLUSTER_COUNT 매개 변수의 값을 설정하여 생성되는 클러스터 수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-145">Controlling the number of clusters generated, by setting a value for the CLUSTER_COUNT parameter.</span></span>  
  
-   <span data-ttu-id="c37d0-146">MINIMUM_SUPPORT 매개 변수의 값을 늘려 특성으로 포함되는 시퀀스 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-146">Reducing the number of sequences included as attributes, by increasing the value of the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="c37d0-147">그 결과 빈도가 낮은 시퀀스는 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-147">As a result, rare sequences are eliminated.</span></span>  
  
-   <span data-ttu-id="c37d0-148">모델을 처리하기 전에 관련 특성을 그룹화하여 복잡성을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-148">Reducing complexity before processing the model, by grouping related attributes.</span></span>  
  
 <span data-ttu-id="c37d0-149">일반적으로 다음과 같은 몇 가지 방법으로 n차 Markov 체인 모드의 성능을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-149">In general, you can optimize the performance of an n-order Markov chain mode in several ways:</span></span>  
  
-   <span data-ttu-id="c37d0-150">가능한 시퀀스의 길이를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-150">Controlling the length of the possible sequences.</span></span>  
  
-   <span data-ttu-id="c37d0-151">프로그래밍 방식으로 n 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-151">Programmatically reducing the value of n.</span></span>  
  
-   <span data-ttu-id="c37d0-152">지정된 임계값을 초과하는 확률만 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-152">Storing only probabilities that exceed a specified threshold.</span></span>  
  
 <span data-ttu-id="c37d0-153">이러한 방법에 대한 자세한 설명은 이 항목에서는 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-153">A complete discussion of these methods is beyond the scope of this topic.</span></span>  
  
## <a name="customizing-the-sequence-clustering-algorithm"></a><span data-ttu-id="c37d0-154">시퀀스 클러스터링 알고리즘 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="c37d0-154">Customizing the Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="c37d0-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘은 결과 마이닝 모델의 동작, 성능 및 정확도에 영향을 주는 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="c37d0-156">알고리즘의 학습 데이터 처리 방식을 제어하는 모델링 플래그를 설정하여 완성된 모델의 동작을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-156">You can also modify the behavior of the completed model by setting modeling flags that control the way the algorithm processes training data.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="c37d0-157">알고리즘 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="c37d0-157">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="c37d0-158">다음 표에서는 Microsoft 시퀀스 클러스터링 알고리즘에서 사용할 수 있는 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-158">The following table describes the parameters that can be used with the Microsoft Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="c37d0-159">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="c37d0-159">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="c37d0-160">알고리즘에서 작성할 클러스터의 대략적인 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-160">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="c37d0-161">데이터에서 대략적인 개수의 클러스터를 작성할 수 없는 경우 알고리즘은 가능한 한 많은 클러스터를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-161">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="c37d0-162">CLUSTER_COUNT 매개 변수를 0으로 설정하면 알고리즘은 경험적 접근을 사용하여 작성할 최적의 클러스터 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-162">Setting the CLUSTER_COUNT parameter to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="c37d0-163">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-163">The default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c37d0-164">0이 아닌 숫자를 지정하면 알고리즘에서는 지정된 개수를 찾고자 시도하지만 최종적으로 찾는 개수는 그보다 많을 수도 있고 적을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-164">Specifying a non-zero number acts as a hint to the algorithm, which proceeds with the goal of finding the specified number, but may end up finding more or less.</span></span>  
  
 <span data-ttu-id="c37d0-165">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c37d0-165">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="c37d0-166">특성을 지원하며 클러스터를 만드는 데 필요한 최소 사례 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-166">Specifies the minimum number of cases that is required in support of an attribute to create a cluster.</span></span>  
  
 <span data-ttu-id="c37d0-167">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-167">The default is 10.</span></span>  
  
 <span data-ttu-id="c37d0-168">MAXIMUM_SEQUENCE_STATES</span><span class="sxs-lookup"><span data-stu-id="c37d0-168">MAXIMUM_SEQUENCE_STATES</span></span>  
 <span data-ttu-id="c37d0-169">시퀀스에 포함할 수 있는 최대 상태 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-169">Specifies the maximum number of states that a sequence can have.</span></span>  
  
 <span data-ttu-id="c37d0-170">이 값을 100보다 큰 숫자로 설정하면 알고리즘은 의미 없는 정보를 제공하는 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-170">Setting this value to a number greater than 100 may cause the algorithm to create a model that does not provide meaningful information.</span></span>  
  
 <span data-ttu-id="c37d0-171">기본값은 64입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-171">The default is 64.</span></span>  
  
 <span data-ttu-id="c37d0-172">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="c37d0-172">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="c37d0-173">알고리즘이 지원하는 비시퀀스 특성에 대한 최대 상태 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-173">Specifies the maximum number of states for a non-sequence attribute that the algorithm supports.</span></span> <span data-ttu-id="c37d0-174">시퀀스가 아닌 특성의 상태 수가 최대 상태 수보다 크면 알고리즘은 특성의 가장 인기 있는 상태를 사용 하 고 나머지 상태를로 처리 `Missing` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-174">If the number of states for a non-sequence attribute is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as `Missing`.</span></span>  
  
 <span data-ttu-id="c37d0-175">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-175">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="c37d0-176">모델링 플래그</span><span class="sxs-lookup"><span data-stu-id="c37d0-176">Modeling Flags</span></span>  
 <span data-ttu-id="c37d0-177">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘에서 지원되는 모델링 플래그는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-177">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="c37d0-178">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="c37d0-178">NOT NULL</span></span>  
 <span data-ttu-id="c37d0-179">열에 null이 포함될 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-179">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="c37d0-180">따라서 Analysis Services가 모델 학습 중 Null을 발견할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-180">An error will result if Analysis Services encounters a null during model training.</span></span>  
  
 <span data-ttu-id="c37d0-181">마이닝 구조 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-181">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="c37d0-182">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="c37d0-182">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="c37d0-183">열이 `Missing` 및 `Existing` 상태를 갖는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-183">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="c37d0-184">Null은 `Missing` 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-184">A null is treated as a `Missing` value.</span></span>  
  
 <span data-ttu-id="c37d0-185">마이닝 모델 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-185">Applies to the mining model column.</span></span>  
  
 <span data-ttu-id="c37d0-186">마이닝 모델에서의 누락 값 사용과 누락 값이 확률 점수에 주는 영향에 대한 자세한 내용은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c37d0-186">For more information about the use of Missing values in mining models, and how missing values affect probability scores, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c37d0-187">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c37d0-187">Requirements</span></span>  
 <span data-ttu-id="c37d0-188">사례 테이블에는 사례 ID 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-188">The case table must have a case ID column.</span></span> <span data-ttu-id="c37d0-189">필요에 따라 사례에 대한 특성을 저장하는 다른 열도 사례 테이블에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-189">Optionally the case table can contain other columns that store attributes about the case.</span></span>  
  
 <span data-ttu-id="c37d0-190">Microsoft 시퀀스 클러스터링 알고리즘을 사용하려면 중첩 테이블로 저장된 시퀀스 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-190">The Microsoft Sequence Clustering algorithm requires sequence information, stored as a nested table.</span></span> <span data-ttu-id="c37d0-191">중첩 테이블에는 단일 Key Sequence 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-191">The nested table must have a single Key Sequence column.</span></span> <span data-ttu-id="c37d0-192">`Key Sequence` 열에는 문자열 데이터 형식을 비롯하여 정렬 가능한 모든 형식의 데이터가 포함될 수 있지만 각 사례에 대해 고유한 값이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-192">A `Key Sequence` column can contain any type of data that can be sorted, including string data types, but the column must contain unique values for each case.</span></span> <span data-ttu-id="c37d0-193">또한 모델을 처리하기 전에 사례 테이블과 중첩 테이블이 모두 해당 테이블과 관련된 키를 기준으로 오름차순으로 정렬되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-193">Moreover, before you process the model, you must ensure that both the case table and the nested table are sorted in ascending order on the key that relates the tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c37d0-194">Microsoft 시퀀스 알고리즘을 사용하는 모델을 만들면서 시퀀스 열은 사용하지 않을 경우 결과 모델은 시퀀스를 포함하지 않고 단지 모델에 포함된 다른 특성에 따라 사례를 클러스터링하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-194">If you create a model that uses the Microsoft Sequence algorithm but do not use a sequence column, the resulting model will not contain any sequences, but will simply cluster cases based on other attributes that are included in the model.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="c37d0-195">입력 열과 예측 가능한 열</span><span class="sxs-lookup"><span data-stu-id="c37d0-195">Input and Predictable Columns</span></span>  
 <span data-ttu-id="c37d0-196">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘은 다음 표에 나열된 특정 입력 열과 예측 가능한 열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-196">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="c37d0-197">마이닝 모델에 사용되는 경우 콘텐츠 형식의 의미에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c37d0-197">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="c37d0-198">열</span><span class="sxs-lookup"><span data-stu-id="c37d0-198">Column</span></span>|<span data-ttu-id="c37d0-199">내용 유형</span><span class="sxs-lookup"><span data-stu-id="c37d0-199">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="c37d0-200">입력 특성</span><span class="sxs-lookup"><span data-stu-id="c37d0-200">Input attribute</span></span>|<span data-ttu-id="c37d0-201">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Table 및 Ordered</span><span class="sxs-lookup"><span data-stu-id="c37d0-201">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Table, and Ordered</span></span>|  
|<span data-ttu-id="c37d0-202">예측 가능한 특성</span><span class="sxs-lookup"><span data-stu-id="c37d0-202">Predictable attribute</span></span>|<span data-ttu-id="c37d0-203">Continuous, Cyclical, Discrete, Discretized, Table 및 Ordered</span><span class="sxs-lookup"><span data-stu-id="c37d0-203">Continuous, Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c37d0-204">설명</span><span class="sxs-lookup"><span data-stu-id="c37d0-204">Remarks</span></span>  
  
-   <span data-ttu-id="c37d0-205">시퀀스 예측에 대한 [PredictSequence&#40;DMX&#41;](/sql/dmx/predictsequence-dmx) 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-205">Use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function for Prediction of Sequences.</span></span> <span data-ttu-id="c37d0-206">시퀀스 예측을 지 원하는 버전에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) 을 참조 하세요 https://go.microsoft.com/fwlink/?linkid=232473) .</span><span class="sxs-lookup"><span data-stu-id="c37d0-206">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Sequence Prediction, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="c37d0-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘에서는 PMML(Predictive Model Markup Language)을 사용하여 마이닝 모델을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm does not support using the Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
-   <span data-ttu-id="c37d0-208">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘에서는 드릴스루, OLAP 마이닝 모델 사용 및 데이터 마이닝 차원 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c37d0-208">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports drillthrough, the use of OLAP mining models, and the use of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37d0-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c37d0-209">See Also</span></span>  
 <span data-ttu-id="c37d0-210">[Microsoft 시퀀스 클러스터링 알고리즘](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c37d0-210">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="c37d0-211">[시퀀스 클러스터링 모델 쿼리 예제](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="c37d0-211">[Sequence Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="c37d0-212">시퀀스 클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="c37d0-212">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
