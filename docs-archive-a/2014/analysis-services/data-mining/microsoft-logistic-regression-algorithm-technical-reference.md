---
title: Microsoft 로지스틱 회귀 알고리즘 기술 참조 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- HOLDOUT_PERCENTAGE parameter
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- regression algorithms [Analysis Services]
- HOLDOUT_SEED parameter
ms.assetid: cf32f1f3-153e-476f-91a4-bb834ec7c88d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72597453c9a52b890c822dd7c46aff46bc3ba44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660766"
---
# <a name="microsoft-logistic-regression-algorithm-technical-reference"></a><span data-ttu-id="1984a-102">Microsoft 로지스틱 회귀 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="1984a-102">Microsoft Logistic Regression Algorithm Technical Reference</span></span>
  <span data-ttu-id="1984a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 분석 알고리즘은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘의 변형으로, *HIDDEN_NODE_RATIO* 매개 변수가 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, where the *HIDDEN_NODE_RATIO* parameter is set to 0.</span></span> <span data-ttu-id="1984a-104">이렇게 설정하면 숨겨진 계층을 포함하지 않으므로 로지스틱 회귀와 동등한 신경망 모델이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-104">This setting will create a neural network model that does not contain a hidden layer, and that therefore is equivalent to logistic regression.</span></span>

## <a name="implementation-of-the-microsoft-logistic-regression-algorithm"></a><span data-ttu-id="1984a-105">Microsoft 로지스틱 회귀 알고리즘 구현</span><span class="sxs-lookup"><span data-stu-id="1984a-105">Implementation of the Microsoft Logistic Regression Algorithm</span></span>
 <span data-ttu-id="1984a-106">예측 가능한 열에 포함된 상태가 두 개뿐이지만 예측 가능한 열에 특정 상태가 포함될 확률과 입력 열을 연결하여 회귀 분석을 수행한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-106">Suppose the predictable column contains only two states, yet you still want to perform a regression analysis, relating input columns to the probability that the predictable column will contain a specific state.</span></span> <span data-ttu-id="1984a-107">다음 다이어그램에서는 예측 가능한 열의 상태에 1과 0을 할당하고 열에 특정 상태가 포함될 확률을 계산한 다음 입력 변수에 대해 선형 회귀를 수행할 경우 나타나는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-107">The following diagram illustrates the results you will obtain if you assign 1 and 0 to the states of the predictable column, calculate the probability that the column will contain a specific state, and perform a linear regression against an input variable.</span></span>

 <span data-ttu-id="1984a-108">![선형 회귀를 사용하여 잘못된 방식으로 모델링한 데이터](../media/logistic-linear-regression.gif "선형 회귀를 사용하여 잘못된 방식으로 모델링한 데이터")</span><span class="sxs-lookup"><span data-stu-id="1984a-108">![Poorly modeled data using linear regression](../media/logistic-linear-regression.gif "Poorly modeled data using linear regression")</span></span>

 <span data-ttu-id="1984a-109">x축은 입력 열의 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-109">The x-axis contains values of an input column.</span></span> <span data-ttu-id="1984a-110">y축은 예측 가능한 열이 특정 상태일 확률을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-110">The y-axis contains the probabilities that the predictable column will be one state or the other.</span></span> <span data-ttu-id="1984a-111">이 경우 선형 회귀가 열의 최대값과 최소값인 0과 1 사이에 있도록 열을 제한하지 않는다는 문제점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-111">The problem with this is that the linear regression does not constrain the column to be between 0 and 1, even though those are the maximum and minimum values of the column.</span></span> <span data-ttu-id="1984a-112">이 문제를 해결하는 방법은 로지스틱 회귀를 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-112">A way to solve this problem is to perform logistic regression.</span></span> <span data-ttu-id="1984a-113">선형 회귀 분석은 직선을 만드는 대신 최대 및 최소 제약 조건이 포함된 "S"자 곡선을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-113">Instead of creating a straight line, logistic regression analysis creates an "S" shaped curve that contains maximum and minimum constraints.</span></span> <span data-ttu-id="1984a-114">예를 들어 다음 다이어그램에서는 이전 예에 사용된 것과 동일한 데이터에 대해 로지스틱 회귀를 수행할 경우 나타나는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-114">For example, the following diagram illustrates the results you will achieve if you perform a logistic regression against the same data as used for the previous example.</span></span>

 <span data-ttu-id="1984a-115">![로지스틱 회귀를 사용하여 모델링한 데이터](../media/logistic-regression.gif "로지스틱 회귀를 사용하여 모델링한 데이터")</span><span class="sxs-lookup"><span data-stu-id="1984a-115">![Data modeled by using logistic regression](../media/logistic-regression.gif "Data modeled by using logistic regression")</span></span>

 <span data-ttu-id="1984a-116">곡선이 0과 1 사이에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-116">Notice how the curve never goes above 1 or below 0.</span></span> <span data-ttu-id="1984a-117">로지스틱 회귀를 사용하면 예측 가능한 열의 상태를 결정할 때 어떤 입력 열이 중요한지 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-117">You can use logistic regression to describe which input columns are important in determining the state of the predictable column.</span></span>

### <a name="feature-selection"></a><span data-ttu-id="1984a-118">기능 선택</span><span class="sxs-lookup"><span data-stu-id="1984a-118">Feature Selection</span></span>
 <span data-ttu-id="1984a-119">모든 Analysis Services 데이터 마이닝 알고리즘에서는 자동으로 기능 선택을 사용하여 분석을 향상시키고 처리 로드를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-119">Feature selection is used automatically by all Analysis Services data mining algorithms to improve analysis and reduce processing load.</span></span> <span data-ttu-id="1984a-120">로지스틱 회귀 모델의 기능 선택에 사용되는 방법은 특성의 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-120">The method used for feature selection in a logistic regression model depends on the data type of the attribute.</span></span> <span data-ttu-id="1984a-121">로지스틱 회귀는 Microsoft 신경망 알고리즘을 기반으로 하므로 신경망에 적용되는 기능 선택 방법 중 일부를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-121">Because logistic regression is based on the Microsoft Neural Network algorithm, it uses a subset of the feature selection methods that apply to neural networks.</span></span> <span data-ttu-id="1984a-122">자세한 내용은 [기능 선택&#40;데이터 마이닝&#41;](feature-selection-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1984a-122">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>

### <a name="scoring-inputs"></a><span data-ttu-id="1984a-123">입력 점수 매기기</span><span class="sxs-lookup"><span data-stu-id="1984a-123">Scoring Inputs</span></span>
 <span data-ttu-id="1984a-124">신경망 모델 또는 로지스틱 회귀 모델의 컨텍스트에서*점수 매기기* 는 데이터에 있는 값을 동일한 배율을 사용하는 값 집합으로 변환하여 각 값을 비교할 수 있게 해 주는 프로세스를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-124">*Scoring* in the context of a neural network model or logistic regression model means the process of converting the values that are present in the data into a set of values that use the same scale and therefore can be compared to each other.</span></span> <span data-ttu-id="1984a-125">예를 들어 Income의 입력 범위는 0에서 100,000 사이이고 [Number of Children]의 입력 범위는 0에서 5 사이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-125">For example, suppose the inputs for Income range from 0 to 100,000 whereas the inputs for [Number of Children] range from 0 to 5.</span></span> <span data-ttu-id="1984a-126">이 변환 프로세스를 사용하면 값의 차이에 관계없이 각 입력의 중요도에 *점수를 매기거나*각 입력의 중요도를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-126">This conversion process allows you to *score*, or compare, the importance of each input regardless of the difference in values.</span></span>

 <span data-ttu-id="1984a-127">모델은 학습 집합에 나타나는 각 상태에 대해 입력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-127">For each state that appears in the training set, the model generates an input.</span></span> <span data-ttu-id="1984a-128">불연속 또는 불연속화된 입력의 경우 학습 집합에서 누락 상태가 한 번 이상 나타나면 Missing 상태를 나타내기 위해 추가 입력이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-128">For discrete or discretized inputs, an additional input is created to represent the Missing state, if the missing state appears at least once in the training set.</span></span> <span data-ttu-id="1984a-129">연속 입력의 경우 최대 두 개의 입력 노드가 만들어집니다. 하나는 Missing 값(학습 데이터에 있는 경우)에 대한 입력을 포함하고, 다른 하나는 존재하는, 즉 Null이 아닌 모든 값에 대한 입력을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-129">For continuous inputs, at most two input nodes are created: one for Missing values, if present in the training data, and one input for all existing, or non-null, values.</span></span> <span data-ttu-id="1984a-130">각 입력은 z 점수 정규화 방법 (x-μ)/a s n을 사용 하 여 숫자 형식으로 크기가 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-130">Each input is scaled to a numeric format using the z-score normalization method, (x - μ)/StdDev.</span></span>

 <span data-ttu-id="1984a-131">z 점수 정규화 도중에는 전체 학습 집합을 대상으로 평균(μ) 및 표준 편차를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-131">During z-score normalization, the mean (μ) and standard deviation are obtained over the complete training set.</span></span>

 <span data-ttu-id="1984a-132">**연속 값**</span><span class="sxs-lookup"><span data-stu-id="1984a-132">**Continuous values**</span></span>

 <span data-ttu-id="1984a-133">값이 있음: (X-μ)/σ//X는 인코딩된 실제 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-133">Value is present:   (X - μ)/σ // X is the actual value being encoded)</span></span>

 <span data-ttu-id="1984a-134">값이 없음:-μ/σ//음수 mu는 시그마로 나눈 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-134">Value is absent:    -   μ/σ  // negative mu divided by sigma)</span></span>

 <span data-ttu-id="1984a-135">**불연속 값**</span><span class="sxs-lookup"><span data-stu-id="1984a-135">**Discrete values**</span></span>

 <span data-ttu-id="1984a-136">μ = p-(상태의 사전 확률)</span><span class="sxs-lookup"><span data-stu-id="1984a-136">μ = p - (the prior probability of a state)</span></span>

 <span data-ttu-id="1984a-137">StdDev  = sqrt(p(1-p))</span><span class="sxs-lookup"><span data-stu-id="1984a-137">StdDev  = sqrt(p(1-p))</span></span>

 <span data-ttu-id="1984a-138">값이 있음: (1-μ)/σ//(1-mu)는 시그마로 나눈 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-138">Value is present:     (1 - μ)/σ// (One minus mu) divided by sigma)</span></span>

 <span data-ttu-id="1984a-139">값이 없음: (-μ)/σ//음수 mu는 시그마로 나눈 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-139">Value is absent:     (- μ)/σ// negative mu divided by sigma)</span></span>

### <a name="understanding-logistic-regression-coefficients"></a><span data-ttu-id="1984a-140">로지스틱 회귀 계수 이해</span><span class="sxs-lookup"><span data-stu-id="1984a-140">Understanding Logistic Regression Coefficients</span></span>
 <span data-ttu-id="1984a-141">통계 자료에서는 다양한 방법으로 로지스틱 회귀를 수행할 수 있지만 모든 방법에서 중요한 부분은 모델의 적합도를 평가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-141">There are various methods in the statistical literature for performing logistic regression, but an important part of all methods is assessing the fit of the model.</span></span> <span data-ttu-id="1984a-142">교차비와 공변량 패턴 간에는 다양한 적합도 통계가 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-142">A variety of goodness-to-fit statistics have been proposed, among them odds ratios and covariate patterns.</span></span> <span data-ttu-id="1984a-143">모델의 적합도를 측정하는 방법에 대한 설명은 이 항목에서 다루지 않습니다. 그러나 모델에서 계수 값을 검색하고 이 값을 사용하여 고유한 적합도 측정 방법을 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-143">A discussion of how to measure the fit of a model is beyond the scope of this topic; however, you can retrieve the value of the coefficients in the model and use them to design your own measures of fit.</span></span>

> [!NOTE]
>  <span data-ttu-id="1984a-144">로지스틱 회귀 모델의 일부로 만들어진 계수는 교차비를 나타내지 않으므로 교차비로 해석되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-144">The coefficients that are created as part of a logistic regression model do not represent odds ratios and should not be interpreted as such.</span></span>

 <span data-ttu-id="1984a-145">모델 그래프의 각 노드에 대한 계수는 해당 노드에 대한 입력의 가중치 합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-145">The coefficients for each node in the model graph represent a weighted sum of the inputs to that node.</span></span> <span data-ttu-id="1984a-146">로지스틱 회귀 모델에서 숨겨진 계층은 비어 있으므로 출력 노드에 저장되는 계수 집합은 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-146">In a logistic regression model, the hidden layer is empty; therefore, there is only one set of coefficients, which is stored in the output nodes.</span></span> <span data-ttu-id="1984a-147">계수 값은 다음 쿼리를 사용하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-147">You can retrieve the values of the coefficients by using the following query:</span></span>

```
SELECT FLATTENED [NODE_UNIQUE NAME],
(SELECT ATTRIBUTE_NAME< ATTRIBUTE_VALUE
FROM NODE_DISTRIBUTION) AS t
FROM <model name>.CONTENT
WHERE NODE_TYPE = 23
```

 <span data-ttu-id="1984a-148">이 쿼리는 각 출력 값에 대해 다시 관련 입력 노드를 가리키는 계수 및 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-148">For each output value, this query returns the coefficients and an ID that points back to the related input node.</span></span> <span data-ttu-id="1984a-149">또한 출력 값과 절편이 들어 있는 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-149">It also returns a row that contains the value of the output and the intercept.</span></span> <span data-ttu-id="1984a-150">각 입력 X에는 고유한 계수 (Ci)가 있지만 중첩 테이블에는 다음 수식에 따라 계산 된 "자유" 계수 (Co)도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-150">Each input X has its own coefficient (Ci), but the nested table also contains a "free" coefficient (Co), calculated according to the following formula:</span></span>

 <span data-ttu-id="1984a-151">F (X) = X1 \* C1 + X2 \* C2 + ... + Xn \* Cn + X0</span><span class="sxs-lookup"><span data-stu-id="1984a-151">F(X) = X1\*C1 + X2\*C2 + ... +Xn\*Cn + X0</span></span>

 <span data-ttu-id="1984a-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span><span class="sxs-lookup"><span data-stu-id="1984a-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span></span>

 <span data-ttu-id="1984a-153">자세한 내용은 [로지스틱 회귀 분석 모델 쿼리 예제](logistic-regression-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1984a-153">For more information, see [Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md).</span></span>

## <a name="customizing-the-logistic-regression-algorithm"></a><span data-ttu-id="1984a-154">로지스틱 회귀 알고리즘 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="1984a-154">Customizing the Logistic Regression Algorithm</span></span>
 <span data-ttu-id="1984a-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 알고리즘은 결과 마이닝 모델의 동작, 성능 및 정확도에 영향을 주는 여러 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] logistic regression algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="1984a-156">입력으로 사용된 열에 모델링 플래그를 설정하여 모델의 동작을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-156">You can also modify the behavior of the model by setting modeling flags on the columns used as input.</span></span>

### <a name="setting-algorithm-parameters"></a><span data-ttu-id="1984a-157">알고리즘 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="1984a-157">Setting Algorithm Parameters</span></span>
 <span data-ttu-id="1984a-158">다음 표에서는 Microsoft 로지스틱 회귀 알고리즘에서 사용할 수 있는 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-158">The following table describes the parameters that can be used with the Microsoft Logistic Regression algorithm.</span></span>

 <span data-ttu-id="1984a-159">HOLDOUT_PERCENTAGE 홀드 아웃 오류를 계산 하는 데 사용 되는 학습 데이터 내의 사례 비율을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-159">HOLDOUT_PERCENTAGE Specifies the percentage of cases within the training data used to calculate the holdout error.</span></span> <span data-ttu-id="1984a-160">HOLDOUT_PERCENTAGE는 마이닝 모델의 학습 중 중지 조건의 일부로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-160">HOLDOUT_PERCENTAGE is used as part of the stopping criteria while training the mining model.</span></span>

 <span data-ttu-id="1984a-161">기본값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-161">The default is 30.</span></span>

 <span data-ttu-id="1984a-162">HOLDOUT_SEED 홀드 아웃 데이터를 임의로 결정할 때 난수 생성기의 초기값으로 사용할 숫자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-162">HOLDOUT_SEED Specifies a number to use to seed the pseudo-random generator when randomly determining the holdout data.</span></span> <span data-ttu-id="1984a-163">HOLDOUT_SEED를 0으로 설정하면 알고리즘은 마이닝 모델의 이름을 기반으로 초기값을 생성하여 다시 처리하는 동안 모델 내용이 동일하게 유지되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-163">If HOLDOUT_SEED is set to 0, the algorithm generates the seed based on the name of the mining model, to guarantee that the model content remains the same during reprocessing.</span></span>

 <span data-ttu-id="1984a-164">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-164">The default is 0.</span></span>

 <span data-ttu-id="1984a-165">MAXIMUM_INPUT_ATTRIBUTES는 기능 선택을 호출 하기 전에 알고리즘이 처리할 수 있는 입력 특성 수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-165">MAXIMUM_INPUT_ATTRIBUTES Defines the number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="1984a-166">이 값을 0으로 설정하면 기능 선택이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-166">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="1984a-167">기본값은 255입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-167">The default is 255.</span></span>

 <span data-ttu-id="1984a-168">MAXIMUM_OUTPUT_ATTRIBUTES 기능 선택을 호출 하기 전에 알고리즘이 처리할 수 있는 출력 특성 수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-168">MAXIMUM_OUTPUT_ATTRIBUTES Defines the number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="1984a-169">이 값을 0으로 설정하면 기능 선택이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-169">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="1984a-170">기본값은 255입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-170">The default is 255.</span></span>

 <span data-ttu-id="1984a-171">MAXIMUM_STATES 알고리즘에서 지 원하는 최대 특성 상태 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-171">MAXIMUM_STATES Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="1984a-172">특성의 상태 수가 최대 상태 수보다 많으면 알고리즘은 가장 많이 사용되는 특성 상태를 사용하고 나머지 상태를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-172">If the number of states that an attribute has is larger than the maximum number of states, the algorithm uses the most popular states of the attribute and ignores the remaining states.</span></span>

 <span data-ttu-id="1984a-173">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-173">The default is 100.</span></span>

 <span data-ttu-id="1984a-174">모델을 학습 하는 데 사용할 사례 수를 지정 SAMPLE_SIZE입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-174">SAMPLE_SIZE Specifies the number of cases to be used to train the model.</span></span> <span data-ttu-id="1984a-175">알고리즘 공급자는 지정한 수와 HOLDOUT_PERCENTAGE 매개 변수로 지정된 홀드아웃 비율에 포함되지 않은 총 사례 수의 비율 중 더 작은 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-175">The algorithm provider uses either this number or the percentage of total of cases that are not included in the holdout percentage as specified by the HOLDOUT_PERCENTAGE parameter, whichever value is smaller.</span></span>

 <span data-ttu-id="1984a-176">즉, HOLDOUT_PERCENTAGE를 30으로 설정하면 알고리즘은 이 매개 변수 값이나 총 사례 수의 70%에 해당하는 값 중 더 작은 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-176">In other words, if HOLDOUT_PERCENTAGE is set to 30, the algorithm will use either the value of this parameter, or a value that is equal to 70 percent of the total number of cases, whichever is smaller.</span></span>

 <span data-ttu-id="1984a-177">기본값은 10000입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-177">The default is 10000.</span></span>

### <a name="modeling-flags"></a><span data-ttu-id="1984a-178">모델링 플래그</span><span class="sxs-lookup"><span data-stu-id="1984a-178">Modeling Flags</span></span>
 <span data-ttu-id="1984a-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 알고리즘에서 지원되는 모델링 플래그는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-179">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>

 <span data-ttu-id="1984a-180">NOT NULL은 열에 null이 포함 될 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-180">NOT NULL Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="1984a-181">따라서 Analysis Services가 모델 학습 중 Null을 발견할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-181">An error will result if Analysis Services encounters a null during model training.</span></span>

 <span data-ttu-id="1984a-182">마이닝 구조 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-182">Applies to mining structure columns.</span></span>

 <span data-ttu-id="1984a-183">MODEL_EXISTENCE_ONLY은 열이 및 이라는 두 가지 가능한 상태를 갖는 것으로 처리 됨을 의미 합니다. `Missing` `Existing`</span><span class="sxs-lookup"><span data-stu-id="1984a-183">MODEL_EXISTENCE_ONLY Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="1984a-184">Null은 누락 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-184">A null is a missing value.</span></span>

 <span data-ttu-id="1984a-185">마이닝 모델 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-185">Applies to mining model column.</span></span>

## <a name="requirements"></a><span data-ttu-id="1984a-186">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1984a-186">Requirements</span></span>
 <span data-ttu-id="1984a-187">로지스틱 회귀 모델은 하나의 키 열, 입력 열 및 하나 이상의 예측 가능한 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-187">A logistic regression model must contain a key column, input columns, and at least one predictable column.</span></span>

### <a name="input-and-predictable-columns"></a><span data-ttu-id="1984a-188">입력 열과 예측 가능한 열</span><span class="sxs-lookup"><span data-stu-id="1984a-188">Input and Predictable Columns</span></span>
 <span data-ttu-id="1984a-189">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 알고리즘은 다음 표에 나열된 특정 입력 열 내용 유형, 예측 가능한 열 내용 유형 및 모델링 플래그를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1984a-189">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the specific input column content types, predictable column content types, and modeling flags that are listed in the following table.</span></span> <span data-ttu-id="1984a-190">마이닝 모델에 사용되는 경우 콘텐츠 형식의 의미에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1984a-190">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>

|<span data-ttu-id="1984a-191">열</span><span class="sxs-lookup"><span data-stu-id="1984a-191">Column</span></span>|<span data-ttu-id="1984a-192">내용 유형</span><span class="sxs-lookup"><span data-stu-id="1984a-192">Content types</span></span>|
|------------|-------------------|
|<span data-ttu-id="1984a-193">입력 특성</span><span class="sxs-lookup"><span data-stu-id="1984a-193">Input attribute</span></span>|<span data-ttu-id="1984a-194">Continuous, Discrete, Discretized, Key, Table</span><span class="sxs-lookup"><span data-stu-id="1984a-194">Continuous, Discrete, Discretized, Key, Table</span></span>|
|<span data-ttu-id="1984a-195">예측 가능한 특성</span><span class="sxs-lookup"><span data-stu-id="1984a-195">Predictable attribute</span></span>|<span data-ttu-id="1984a-196">Continuous, Discrete, Discretized</span><span class="sxs-lookup"><span data-stu-id="1984a-196">Continuous, Discrete, Discretized</span></span>|

## <a name="see-also"></a><span data-ttu-id="1984a-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1984a-197">See Also</span></span>
 <span data-ttu-id="1984a-198">[Microsoft 로지스틱 회귀 알고리즘](microsoft-logistic-regression-algorithm.md) [선형 회귀 모델 쿼리 예제](linear-regression-model-query-examples.md) [로지스틱 회귀 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft 신경망 알고리즘](microsoft-neural-network-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="1984a-198">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)</span></span>


