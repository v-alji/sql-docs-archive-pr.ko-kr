---
title: Microsoft 연결 알고리즘 기술 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_ITEMSET_SIZE parameter
- MAXIMUM_SUPPORT parameter
- association algorithms [Analysis Services]
- MINIMUM_SUPPORT parameter
- OPTIMIZED_PREDICTION_COUNT parameter
- associations [Analysis Services]
- MAXIMUM_ITEMSET_COUNT parameter
- MAXIMUM_ITEMSET_SIZE parameter
- MINIMUM_PROBABILITY parameter
ms.assetid: 50a22202-e936-4995-ae1d-4ff974002e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: eac813711aafc714edef6acc98cda612dd879549
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648663"
---
# <a name="microsoft-association-algorithm-technical-reference"></a><span data-ttu-id="47d71-102">Microsoft 연결 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="47d71-102">Microsoft Association Algorithm Technical Reference</span></span>
  <span data-ttu-id="47d71-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘은 잘 알려진 Apriori 알고리즘을 간단하게 구현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm is a straightforward implementation of the well-known Apriori algorithm.</span></span>  
  
 <span data-ttu-id="47d71-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘과 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘은 둘 다 연결을 분석하는 데 사용할 수 있지만 각 알고리즘에서 발견되는 규칙은 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-104">Both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm can be used to analyze associations, but the rules that are found by each algorithm can differ.</span></span> <span data-ttu-id="47d71-105">의사 결정 트리 모델에서 특정 규칙을 생성하는 분류는 정보 획득량을 기반으로 하는 반면 연결 모델에서 규칙은 전적으로 신뢰도를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-105">In a decision trees model, the splits that lead to specific rules are based on information gain, whereas in an association model, rules are based completely on confidence.</span></span> <span data-ttu-id="47d71-106">따라서 연결 모델에서 강력한 규칙 또는 신뢰도가 높은 규칙은 새로운 정보를 제공하지 않기 때문에 반드시 유용한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-106">Therefore, in an association model, a strong rule, or one that has high confidence, might not necessarily be interesting because it does not provide new information.</span></span>  
  
## <a name="implementation-of-the-microsoft-association-algorithm"></a><span data-ttu-id="47d71-107">Microsoft 연결 알고리즘 구현</span><span class="sxs-lookup"><span data-stu-id="47d71-107">Implementation of the Microsoft Association Algorithm</span></span>  
 <span data-ttu-id="47d71-108">Apriori 알고리즘은 패턴을 분석하는 대신 *후보 항목 집합*을 생성한 다음 그 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-108">The Apriori algorithm does not analyze patterns, but rather generates and then counts *candidate itemsets*.</span></span> <span data-ttu-id="47d71-109">분석되는 데이터의 형식에 따라 후보 항목은 이벤트, 제품 또는 특성 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-109">An item can represent an event, a product, or the value of an attribute, depending on the type of data that is being analyzed.</span></span>  
  
 <span data-ttu-id="47d71-110">가장 일반적인 연결 모델 유형에서 Yes/No 또는 Missing/Existing 값을 나타내는 부울 변수는 제품 또는 이벤트 이름과 같은 각 특성에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-110">In the most common type of association model Boolean variables, representing a Yes/No or Missing/Existing value, are assigned to each attribute, such as a product or event name.</span></span> <span data-ttu-id="47d71-111">시장 바구니 분석은 부울 변수를 사용하여 고객 시장 바구니에서 특정 제품의 존재 또는 부재를 나타내는 연결 규칙 모델의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-111">A market basket analysis is an example of an association rules model that uses Boolean variables to represent the presence or absence of particular products in a customer's shopping basket.</span></span>  
  
 <span data-ttu-id="47d71-112">각 항목 집합에 대해 알고리즘은 지지도와 신뢰도를 나타내는 점수를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-112">For each itemset, the algorithm then creates scores that represent support and confidence.</span></span> <span data-ttu-id="47d71-113">이러한 점수는 항목 집합에서 유용한 규칙을 이끌어 내고 순위를 지정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-113">These scores can be used to rank and derive interesting rules from the itemsets.</span></span>  
  
 <span data-ttu-id="47d71-114">숫자 특성에 대해서도 연결 모델을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-114">Association models can also be created for numerical attributes.</span></span> <span data-ttu-id="47d71-115">특성이 연속이면 숫자는 버킷에서 *분할* 또는 그룹화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-115">If the attributes are continuous, the numbers can be *discretized, or* grouped in buckets.</span></span> <span data-ttu-id="47d71-116">이렇게 불연속화된 값은 부울 또는 특성-값 쌍으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-116">The discretized values can then be handled either as Booleans or as attribute-value pairs.</span></span>  
  
### <a name="support-probability-and-importance"></a><span data-ttu-id="47d71-117">지지도, 확률 및 중요도</span><span class="sxs-lookup"><span data-stu-id="47d71-117">Support, Probability, and Importance</span></span>  
 <span data-ttu-id="47d71-118">*지지도*는 *빈도*라고도 하며 목표 항목 또는 항목 조합을 포함하는 사례 수를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-118">*Support*, which issometimes referred to as *frequency*, means the number of cases that contain the targeted item or combination of items.</span></span> <span data-ttu-id="47d71-119">지정된 지지도보다 높거나 같은 항목만 모델에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-119">Only items that have at least the specified amount of support can be included in the model.</span></span>  
  
 <span data-ttu-id="47d71-120">*자주 나타나는 항목 집합* 은 항목 조합의 지지도 역시 MINIMUM_SUPPORT 매개 변수에 의해 정의된 임계값보다 큰 항목 모음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-120">A *frequent itemset* refers to a collection of items where the combination of items also has support above the threshold defined by the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="47d71-121">예를 들어 항목 집합이 {A,B,C}이고 MINIMUM_SUPPORT 값이 10일 경우 개별 항목 A, B, C는 각각 최소 10개의 사례에서 발견되어야 모델에 포함될 수 있으며 항목 조합 {A,B,C}도 최소 10개의 사례에서 발견되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-121">For example, if the itemset is {A,B,C} and the MINIMUM_SUPPORT value is 10, each individual item A, B, and C must be found in at least 10 cases to be included in the model, and the combination of items {A,B,C} must also be found in at least 10 cases.</span></span>  
  
 <span data-ttu-id="47d71-122">**참고** 항목 집합의 최대 길이(항목 수)를 지정하여 마이닝 모델의 항목 집합 수를 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-122">**Note** You can also control the number of itemsets in a mining model by specifying the maximum length of an itemset, where length means the number of items.</span></span>  
  
 <span data-ttu-id="47d71-123">기본적으로 특정 항목 또는 항목 집합에 대한 지지도는 해당 항목 또는 항목 집합을 포함하는 사례 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-123">By default, the support for any particular item or itemset represents a count of the cases that contain that item or items.</span></span> <span data-ttu-id="47d71-124">그러나 이 수를 1보다 작은 10진수 값으로 입력하여 MINIMUM_SUPPORT를 데이터 집합에 있는 총 사례 수에 대한 백분율로 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-124">However, you can also express MINIMUM_SUPPORT as a percentage of the total cases in the data set, by typing the number as a decimal value less than 1.</span></span> <span data-ttu-id="47d71-125">예를 들어 MINIMUM_SUPPORT 값을 0.03으로 지정할 경우 데이터 집합에 있는 총 사례 수의 3%에 해당하는 사례에 해당 항목 또는 항목 집합이 있어야 모델에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-125">For example, if you specify a MINIMUM_SUPPORT value of 0.03, it means that at least 3% of the total cases in the data set must contain this item or itemset for inclusion in the model.</span></span> <span data-ttu-id="47d71-126">모델에 따라 개수 또는 백분율 중 적절한 방식을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-126">You should experiment with your model to determine whether using a count or percentage makes more sense.</span></span>  
  
 <span data-ttu-id="47d71-127">반대로 규칙에 대한 임계값은 개수나 백분율이 아닌 확률( *신뢰도*라고도 함)로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-127">In contrast, the threshold for rules is expressed not as a count or percentage, but as a probability, sometimes referred to as *confidence*.</span></span> <span data-ttu-id="47d71-128">예를 들어 항목 집합 {A,B,C}가 50개의 사례에 나타나고 항목 집합 {A,B,D}도 50개의 사례에 나타나지만 항목 집합 {A,B}가 다른 50개의 사례에 나타날 경우 {A,B} 다음에 반드시 {C}가 오는 것이 아니라는 점을 명확하게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-128">For example, if the itemset {A,B,C} occurs in 50 cases, but the itemset {A,B,D} also occurs in 50 cases, and the itemset {A,B} in another 50 cases, it is obvious that {A,B} is not a strong predictor of {C}.</span></span> <span data-ttu-id="47d71-129">따라서 알려진 모든 결과 중 특정 결과에 가중치를 매기기 위해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 항목 집합 {A,B,C}의 지지도를 모든 관련 항목 집합의 지지도로 나눠 개별 규칙(예: If {A,B} Then {C})의 확률을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-129">Therefore, to weight a particular outcomes against all known outcomes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the probability of the individual rule (such as If {A,B} Then {C}) by dividing the support for the itemset {A,B,C} by the support for all related itemsets.</span></span>  
  
 <span data-ttu-id="47d71-130">MINIMUM_PROBABILITY 값을 설정하여 모델이 생성하는 규칙의 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-130">You can restrict the number of rules that a model produces by setting a value for MINIMUM_PROBABILITY.</span></span>  
  
 <span data-ttu-id="47d71-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 생성되는 각 규칙마다 *리프트*라고도 하는 *중요도*를 나타내는 점수를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-131">For each rule that is created, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] outputs a score that indicates its *importance*, which is alsoreferred to as *lift*.</span></span> <span data-ttu-id="47d71-132">리프트 중요도는 항목 집합 및 규칙마다 서로 다르게 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-132">Lift Importance is calculated differently for itemsets and rules.</span></span>  
  
 <span data-ttu-id="47d71-133">항목 집합의 중요도는 항목 집합의 확률을 항목 집합에 있는 개별 항목의 복합 확률로 나눠 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-133">The importance of an itemset is calculated as the probability of the itemset divided by the compound probability of the individual items in the itemset.</span></span> <span data-ttu-id="47d71-134">예를 들어 항목 집합에 {A,B}가 있는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 먼저 이 A와 B 조합을 포함하는 모든 사례 수를 계산하고 이 값을 총 사례 수로 나눈 다음 확률을 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-134">For example, if an itemset contains {A,B}, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] first counts all the cases that contain this combination A and B, and divides that by the total number of cases, and then normalizes the probability.</span></span>  
  
 <span data-ttu-id="47d71-135">규칙의 중요도는 규칙 오른쪽에 대한 규칙 왼쪽의 로그 우도로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-135">The importance of a rule is calculated by the log likelihood of the right-hand side of the rule, given the left-hand side of the rule.</span></span> <span data-ttu-id="47d71-136">예를 들어 `If {A} Then {B}`규칙에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 B가 있고 A는 없는 사례에 대한 A와 B가 있는 사례의 비율을 계산한 다음 로그 눈금 간격을 사용하여 비율을 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-136">For example, in the rule `If {A} Then {B}`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the ratio of cases with A and B over cases with B but without A, and then normalizes that ratio by using a logarithmic scale.</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="47d71-137">기능 선택</span><span class="sxs-lookup"><span data-stu-id="47d71-137">Feature Selection</span></span>  
 <span data-ttu-id="47d71-138">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘은 어떤 종류의 자동 기능 선택도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-138">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm does not perform any kind of automatic feature selection.</span></span> <span data-ttu-id="47d71-139">대신 알고리즘에서 사용하는 데이터를 제어하는 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-139">Instead, the algorithm provides parameters that control the data that is used by the algorithm.</span></span> <span data-ttu-id="47d71-140">이러한 매개 변수에는 각 항목 집합의 크기 제한, 항목 집합을 모델에 추가하는 데 필요한 최대/최소 지지도 설정이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-140">This might include limits on the size of each itemset, or setting the maximum and minimum support required to add an itemset to the model.</span></span>  
  
-   <span data-ttu-id="47d71-141">너무 흔해서 유용하지 않은 항목과 이벤트를 필터를 사용하여 제외시키려면 MAXIMUM_SUPPORT 값을 낮춰 모델에서 자주 나타나는 항목 집합을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-141">To filter out items and events that are too common and therefore uninteresting, decrease the value of MAXIMUM_SUPPORT to remove very frequent itemsets from the model.</span></span>  
  
-   <span data-ttu-id="47d71-142">드물게 나타나는 항목과 항목 집합을 필터를 사용하여 제외시키려면 MINIMUM_SUPPORT 값을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-142">To filter out items and itemsets that are rare, increase the value of MINIMUM_SUPPORT.</span></span>  
  
-   <span data-ttu-id="47d71-143">규칙을 필터를 사용하여 제외시키려면 MINIMUM_PROBABILITY 값을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-143">To filter out rules, increase the value of MINIMUM_PROBABILITY.</span></span>  
  
## <a name="customizing-the-microsoft-association-rules-algorithm"></a><span data-ttu-id="47d71-144">Microsoft 연결 규칙 알고리즘 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="47d71-144">Customizing the Microsoft Association Rules Algorithm</span></span>  
 <span data-ttu-id="47d71-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘은 결과 마이닝 모델의 동작, 성능 및 정확도에 영향을 주는 여러 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-145">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="47d71-146">알고리즘 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="47d71-146">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="47d71-147">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너를 사용하여 언제든지 마이닝 모델의 매개 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-147">You can change the parameters for a mining model at any time by using the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="47d71-148"><xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A>AMO에서 컬렉션을 사용 하거나 XMLA의 [MiningModels 요소 &#40;&#41;요소](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) 를 사용 하 여 매개 변수를 프로그래밍 방식으로 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-148">You can also change parameters programmatically by using the <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> collection in AMO, or by using the [MiningModels Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) in XMLA.</span></span> <span data-ttu-id="47d71-149">다음 표에서는 각 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-149">The following table describes each parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47d71-150">DMX 문을 사용 하 여 기존 모델의 매개 변수를 변경할 수 없습니다. DMX CREATE MODEL 또는 ALTER STRUCTURE ...에서 매개 변수를 지정 해야 합니다. 모델을 만들 때 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-150">You cannot change the parameters in an existing model by using a DMX statement; you must specify the parameters in the DMX CREATE MODEL or ALTER STRUCTURE... ADD MODEL when you create the model.</span></span>  
  
 <span data-ttu-id="47d71-151">*MAXIMUM_ITEMSET_COUNT*</span><span class="sxs-lookup"><span data-stu-id="47d71-151">*MAXIMUM_ITEMSET_COUNT*</span></span>  
 <span data-ttu-id="47d71-152">생성할 최대 항목 집합 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-152">Specifies the maximum number of itemsets to produce.</span></span> <span data-ttu-id="47d71-153">값을 지정하지 않으면 기본값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-153">If no number is specified, the default value is used.</span></span>  
  
 <span data-ttu-id="47d71-154">기본값은 200000입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-154">The default is 200000.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47d71-155">항목 집합은 지지도 순으로 순위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-155">Itemsets are ranked by support.</span></span> <span data-ttu-id="47d71-156">지지도가 동일한 항목 집합 간의 순서는 임의로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-156">Among itemsets that have the same support, ordering is arbitrary.</span></span>  
  
 <span data-ttu-id="47d71-157">*MAXIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="47d71-157">*MAXIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="47d71-158">항목 집합에 사용할 수 있는 최대 항목 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-158">Specifies the maximum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="47d71-159">이 값을 0으로 설정하면 항목 집합 크기가 무제한으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-159">Setting this value to 0 specifies that there is no limit to the size of the itemset.</span></span>  
  
 <span data-ttu-id="47d71-160">기본값은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-160">The default is 3.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47d71-161">제한에 도달하면 모델 처리가 중지되므로 이 값을 줄이면 모델을 만드는 데 필요한 시간이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-161">Decreasing this value can potentially reduce the time that is required for creating the model, because processing of the model stops when the limit is reached.</span></span>  
  
 <span data-ttu-id="47d71-162">*MAXIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="47d71-162">*MAXIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="47d71-163">지지도에 대한 항목 집합의 최대 사례 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-163">Specifies the maximum number of cases that an itemset has for support.</span></span> <span data-ttu-id="47d71-164">이 매개 변수는 자주 나타나 잠재적으로 별 의미가 없는 항목을 제거하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-164">This parameter can be used to eliminate items that appear frequently and therefore potentially have little meaning.</span></span>  
  
 <span data-ttu-id="47d71-165">이 값이 1보다 작으면 총 사례의 백분율을 나타내고</span><span class="sxs-lookup"><span data-stu-id="47d71-165">If this value is less than 1, the value represents a percentage of the total cases.</span></span> <span data-ttu-id="47d71-166">1보다 크면 항목 집합을 포함하는 사례의 절대 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-166">Values greater than 1 represent the absolute number of cases that can contain the itemset.</span></span>  
  
 <span data-ttu-id="47d71-167">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-167">The default is 1.</span></span>  
  
 <span data-ttu-id="47d71-168">*MINIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="47d71-168">*MINIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="47d71-169">항목 집합에 사용할 수 있는 최소 항목 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-169">Specifies the minimum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="47d71-170">이 값을 늘리면 모델에 더 적은 수의 항목 집합이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-170">If you increase this number, the model might contain fewer itemsets.</span></span> <span data-ttu-id="47d71-171">단일 항목으로 구성된 항목 집합을 무시하려는 경우 이 매개 변수가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-171">This can be useful if you want to ignore single-item itemsets, for example.</span></span>  
  
 <span data-ttu-id="47d71-172">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-172">The default is 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47d71-173">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 처리의 일부로 단일 항목의 확률을 계산해야 하기 때문에 최소값을 늘려 모델 처리 시간을 줄일 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-173">You cannot reduce model processing time by increasing the minimum value, because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must calculate probabilities for single items anyway as part of processing.</span></span> <span data-ttu-id="47d71-174">그러나 이 값을 높게 설정하여 작은 항목 집합을 필터를 사용하여 제외시킬 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-174">However, by setting this value higher you can filter out smaller itemsets.</span></span>  
  
 <span data-ttu-id="47d71-175">*MINIMUM_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="47d71-175">*MINIMUM_PROBABILITY*</span></span>  
 <span data-ttu-id="47d71-176">규칙이 참이 되는 최소 확률을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-176">Specifies the minimum probability that a rule is true.</span></span>  
  
 <span data-ttu-id="47d71-177">예를 들어 이 값을 0.5로 설정하면 확률이 50% 미만인 규칙은 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-177">For example, if you set this value to 0.5, it means that no rule with less than fifty percent probability can be generated.</span></span>  
  
 <span data-ttu-id="47d71-178">기본값은 0.4입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-178">The default is 0.4.</span></span>  
  
 <span data-ttu-id="47d71-179">*MINIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="47d71-179">*MINIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="47d71-180">알고리즘이 규칙을 생성하기 전에 항목 집합이 있어야 하는 최소 사례 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-180">Specifies the minimum number of cases that must contain the itemset before the algorithm generates a rule.</span></span>  
  
 <span data-ttu-id="47d71-181">이 값을 1보다 작게 설정하면 최소 사례 수가 총 사례에 대한 백분율로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-181">If you set this value to less than 1, the minimum number of cases is calculated as a percentage of the total cases.</span></span>  
  
 <span data-ttu-id="47d71-182">이 값을 1보다 큰 정수로 설정하면 최소 사례 수가 항목 집합을 포함해야 하는 사례 수로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-182">If you set this value to a whole number greater than 1, specifies the minimum number of cases is calculated as a count of cases that must contain the itemset.</span></span> <span data-ttu-id="47d71-183">메모리가 제한된 경우 알고리즘은 이 매개 변수의 값을 자동으로 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-183">The algorithm might automatically increase the value of this parameter if memory is limited.</span></span>  
  
 <span data-ttu-id="47d71-184">기본값은 0.03입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-184">The default is 0.03.</span></span> <span data-ttu-id="47d71-185">이는 항목 집합이 최소한 총 사례 중 3% 이상에서 발견되어야 모델에 포함될 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-185">This means that to be included in the model, an itemset must be found in at least 3% of cases.</span></span>  
  
 <span data-ttu-id="47d71-186">*OPTIMIZED_PREDICTION_COUNT*</span><span class="sxs-lookup"><span data-stu-id="47d71-186">*OPTIMIZED_PREDICTION_COUNT*</span></span>  
 <span data-ttu-id="47d71-187">예측 최적화를 위해 캐시할 항목 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-187">Defines the number of items to be cached for optimizing prediction.</span></span>  
  
 <span data-ttu-id="47d71-188">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-188">The default value is 0.</span></span> <span data-ttu-id="47d71-189">기본값을 사용할 경우 알고리즘은 쿼리에서 요청한 만큼 많은 예측을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-189">When the default is used, the algorithm will produce as many predictions as requested in the query.</span></span>  
  
 <span data-ttu-id="47d71-190">*OPTIMIZED_PREDICTION_COUNT* 에 대해 0이 아닌 값을 지정하면 추가 예측을 요청한 경우에도 예측 쿼리는 지정된 수 이하의 항목만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-190">If you specify a nonzero value for *OPTIMIZED_PREDICTION_COUNT,* prediction queries can return at most the specified number of items, even if you request additional predictions.</span></span> <span data-ttu-id="47d71-191">그러나 값을 설정하면 예측 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-191">However, setting a value can improve prediction performance.</span></span>  
  
 <span data-ttu-id="47d71-192">예를 들어 이 값을 3으로 설정할 경우 알고리즘은 예측을 위해 3개의 항목만 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-192">For example, if the value is set to 3, the algorithm caches only 3 items for prediction.</span></span> <span data-ttu-id="47d71-193">3개의 항목이 반환된다고 균등하게 예상되는 추가 예측을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-193">You cannot see additional predictions that might be equally probable to the 3 items that are returned.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="47d71-194">모델링 플래그</span><span class="sxs-lookup"><span data-stu-id="47d71-194">Modeling Flags</span></span>  
 <span data-ttu-id="47d71-195">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘과 함께 사용할 수 있는 모델링 플래그는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-195">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="47d71-196">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="47d71-196">NOT NULL</span></span>  
 <span data-ttu-id="47d71-197">열에 null이 포함될 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-197">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="47d71-198">따라서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 가 모델 학습 중 null 값을 발견할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-198">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null during model training.</span></span>  
  
 <span data-ttu-id="47d71-199">마이닝 구조 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-199">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="47d71-200">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="47d71-200">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="47d71-201">열이 `Missing` 및 `Existing` 상태를 갖는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-201">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="47d71-202">Null은 누락 값입니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-202">A null is a missing value.</span></span>  
  
 <span data-ttu-id="47d71-203">마이닝 모델 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-203">Applies to the mining model column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d71-204">요구 사항</span><span class="sxs-lookup"><span data-stu-id="47d71-204">Requirements</span></span>  
 <span data-ttu-id="47d71-205">연결 모델에는 하나의 키 열, 여러 개의 입력 열 및 하나의 예측 가능한 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-205">An association model must contain a key column, input columns, and a single predictable column.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="47d71-206">입력 열과 예측 가능한 열</span><span class="sxs-lookup"><span data-stu-id="47d71-206">Input and Predictable Columns</span></span>  
 <span data-ttu-id="47d71-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘은 다음 표에 나열된 특정 입력 열과 예측 가능한 열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="47d71-208">마이닝 모델의 콘텐츠 형식에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47d71-208">For more information about the meaning of content types in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="47d71-209">열</span><span class="sxs-lookup"><span data-stu-id="47d71-209">Column</span></span>|<span data-ttu-id="47d71-210">내용 유형</span><span class="sxs-lookup"><span data-stu-id="47d71-210">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="47d71-211">입력 특성</span><span class="sxs-lookup"><span data-stu-id="47d71-211">Input attribute</span></span>|<span data-ttu-id="47d71-212">Cyclical, Discrete, Discretized, Key, Table, Ordered</span><span class="sxs-lookup"><span data-stu-id="47d71-212">Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="47d71-213">예측 가능한 특성</span><span class="sxs-lookup"><span data-stu-id="47d71-213">Predictable attribute</span></span>|<span data-ttu-id="47d71-214">Cyclical, Discrete, Discretized, Key, Table, Ordered</span><span class="sxs-lookup"><span data-stu-id="47d71-214">Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="47d71-215">Cyclical  및 Ordered  내용 유형이 지원되기는 하지만 알고리즘은 해당 유형을 불연속 값으로 처리하고 특수한 처리를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47d71-215">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d71-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47d71-216">See Also</span></span>  
 <span data-ttu-id="47d71-217">[Microsoft 연결 알고리즘](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="47d71-217">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="47d71-218">[연결 모델 쿼리 예제](association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="47d71-218">[Association Model Query Examples](association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="47d71-219">연결 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="47d71-219">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
