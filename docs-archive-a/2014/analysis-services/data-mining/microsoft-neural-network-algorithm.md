---
title: Microsoft 신경망 알고리즘 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639106"
---
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="3afe4-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="3afe4-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="3afe4-103">에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 입력 특성의 가능한 각 상태를 예측 가능한 특성의 가능한 각 상태와 결합 하 고 학습 데이터를 사용 하 여 확률을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="3afe4-104">나중에 이러한 확률을 분류 또는 회귀에 사용하여 입력 특성을 기반으로 예측 특성의 결과를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="3afe4-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하여 생성된 마이닝 모델은 입력 및 예측에 모두 사용되는 열 개수나 예측에만 사용되는 열 개수에 따라 여러 네트워크를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="3afe4-106">단일 마이닝 모델이 포함할 수 있는 네트워크 수는 마이닝 모델이 사용하는 입력 열 및 예측 가능한 열에 포함된 상태 수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3afe4-107">예제</span><span class="sxs-lookup"><span data-stu-id="3afe4-107">Example</span></span>  
 <span data-ttu-id="3afe4-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 제조 또는 상업 프로세스와 같은 프로세스에서 사용되는 복잡한 입력 데이터를 분석하거나 상당한 양의 학습 데이터가 있지만 다른 알고리즘으로 쉽게 규칙을 이끌어 낼 수 없는 비즈니스 문제를 분석하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="3afe4-109">다음과 같은 시나리오에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="3afe4-110">홍보 메일 행사나 라디오 광고 캠페인의 성공 정도 측정과 같은 마케팅 및 홍보 행사 분석</span><span class="sxs-lookup"><span data-stu-id="3afe4-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="3afe4-111">기록 데이터를 사용하여 주식 이동, 통화 변동 또는 유동성이 큰 기타 재무 정보 예측</span><span class="sxs-lookup"><span data-stu-id="3afe4-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="3afe4-112">제조 및 공업 프로세스 분석</span><span class="sxs-lookup"><span data-stu-id="3afe4-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="3afe4-113">텍스트 마이닝</span><span class="sxs-lookup"><span data-stu-id="3afe4-113">Text mining.</span></span>  
  
-   <span data-ttu-id="3afe4-114">많은 입력과 비교적 적은 출력 간의 복잡한 관계를 분석하는 모든 예측 모델</span><span class="sxs-lookup"><span data-stu-id="3afe4-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="3afe4-115">알고리즘 작동 방법</span><span class="sxs-lookup"><span data-stu-id="3afe4-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="3afe4-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 최대 3개의 뉴런 계층으로 구성된 신경망을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="3afe4-117">이러한 3개의 계층은 입력 계층, 출력 계층 및 숨겨진 계층(옵션)입니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="3afe4-118">**입력 계층:** 입력 뉴런는 데이터 마이닝 모델에 대 한 모든 입력 특성 값과 해당 확률을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="3afe4-119">**숨겨진 계층:** 숨겨진 뉴런는 입력 뉴런에서 입력을 받고 출력에 뉴런 출력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="3afe4-120">숨겨진 뉴런은 입력의 다양한 확률에 가중치가 할당되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="3afe4-121">가중치는 숨겨진 뉴런에 대한 특정 입력의 관련성 또는 중요도를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="3afe4-122">입력에 할당된 가중치가 클수록 해당 입력 값의 중요도도 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="3afe4-123">가중치는 음수가 될 수 있으며 이 경우 입력이 특정 결과를 지지하는 것이 아니라 제한할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="3afe4-124">**출력 계층:** 출력 뉴런는 데이터 마이닝 모델에 대 한 예측 가능한 특성 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="3afe4-125">입력 계층, 숨겨진 계층 및 출력 계층이 생성되고 점수가 매겨지는 방법에 대한 자세한 내용은 [Microsoft 신경망 알고리즘 기술 참조](microsoft-neural-network-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="3afe4-126">신경망 모델에 필요한 데이터</span><span class="sxs-lookup"><span data-stu-id="3afe4-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="3afe4-127">신경망 모델은 하나의 키 열, 하나 이상의 입력 열, 하나 이상의 예측 가능한 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="3afe4-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하는 데이터 마이닝 모델은 알고리즘에 사용 가능한 매개 변수에 대해 사용자가 지정한 값의 영향을 크게 받습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="3afe4-129">이러한 매개 변수는 데이터가 샘플링되는 방식, 데이터가 각 열에 배포되거나 배포될 것으로 예상되는 방식 및 기능 선택이 실행되어 최종 모델에 사용되는 값을 제한하는 시기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="3afe4-130">매개 변수를 설정하여 모델의 동작을 사용자 지정하는 방법에 대한 자세한 내용은 [Microsoft 신경망 알고리즘 기술 참조](microsoft-neural-network-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="3afe4-131">신경망 모델 보기</span><span class="sxs-lookup"><span data-stu-id="3afe4-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="3afe4-132">데이터를 사용하고 모델이 입력과 출력 간의 상관 관계를 찾아내는 방식을 보려면 **Microsoft 신경망 뷰어**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="3afe4-133">이 사용자 지정 뷰어를 사용하면 입력 특성과 해당 값을 필터링하고 이러한 항목이 출력에 주는 영향을 보여 주는 그래프를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="3afe4-134">뷰어의 도구 설명에는 각 입력 및 출력 값 쌍과 연결된 확률 및 리프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="3afe4-135">자세한 내용은 [Microsoft 신경망 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-neural-network-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="3afe4-136">모델의 구조를 탐색하는 가장 쉬운 방법은 **Microsoft 일반 콘텐츠 트리 뷰어**를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="3afe4-137">모델에서 만든 입력, 출력 및 네트워크를 볼 수 있을 뿐 아니라, 노드를 클릭하여 확장한 다음 입력 계층, 출력 계층 또는 숨겨진 계층 노드와 관련된 통계를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="3afe4-138">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="3afe4-139">예측 만들기</span><span class="sxs-lookup"><span data-stu-id="3afe4-139">Creating Predictions</span></span>  
 <span data-ttu-id="3afe4-140">모델이 처리된 후에는 네트워크와 각 노드 내에 저장된 가중치를 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="3afe4-141">신경망 모델에서는 회귀, 연결 및 분류 분석을 지원하므로 각 예측의 의미가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="3afe4-142">모델 자체를 쿼리하여 발견된 상관 관계를 검토하고 관련 통계를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="3afe4-143">신경망 모델에 대한 쿼리를 만드는 방법의 예는 [신경망 모델 쿼리 예제](neural-network-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="3afe4-144">데이터 마이닝 모델에 대한 쿼리를 만드는 방법은 [데이터 마이닝 쿼리](data-mining-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3afe4-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3afe4-145">설명</span><span class="sxs-lookup"><span data-stu-id="3afe4-145">Remarks</span></span>  
  
-   <span data-ttu-id="3afe4-146">드릴스루 또는 데이터 마이닝 차원은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="3afe4-147">이는 마이닝 모델의 노드 구조가 기본 데이터와 반드시 일치하지는 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="3afe4-148">PMML(Predictive Model Markup Language) 형식의 모델 생성은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="3afe4-149">OLAP 마이닝 모델의 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="3afe4-150">데이터 마이닝 차원의 생성은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3afe4-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afe4-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3afe4-151">See Also</span></span>  
 <span data-ttu-id="3afe4-152">[Microsoft 신경망 알고리즘 기술 참조](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3afe4-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="3afe4-153">[신경망 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3afe4-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3afe4-154">[신경망 모델 쿼리 예제](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="3afe4-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="3afe4-155">Microsoft 로지스틱 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="3afe4-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  
