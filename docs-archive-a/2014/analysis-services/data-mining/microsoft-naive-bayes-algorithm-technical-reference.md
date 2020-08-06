---
title: Microsoft Naive Bayes 알고리즘 기술 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660764"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a><span data-ttu-id="becdd-102">Microsoft Naive Bayes 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="becdd-102">Microsoft Naive Bayes Algorithm Technical Reference</span></span>
  <span data-ttu-id="becdd-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Naive Bayes 알고리즘은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 예측 모델링에 사용 하기 위해에서 제공 하는 분류 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="becdd-104">이 알고리즘은 입력 열과 예측 가능한 열 간의 조건부 확률을 계산하며 열이 서로 독립적이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-104">The algorithm calculates the conditional probability between input and predictable columns, and assumes that the columns are independent.</span></span> <span data-ttu-id="becdd-105">이와 같은 독립성 가정으로 인해 Naive Bayes라는 이름이 붙었습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-105">This assumption of independence leads to the name Naive Bayes.</span></span>  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a><span data-ttu-id="becdd-106">Microsoft Naive Bayes 알고리즘 구현</span><span class="sxs-lookup"><span data-stu-id="becdd-106">Implementation of the Microsoft Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="becdd-107">이 알고리즘은 다른 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘보다 계산 과정이 단순하여 입력 열과 예측 가능한 열 간의 관계를 검색하는 마이닝 모델을 신속하게 생성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-107">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="becdd-108">이 알고리즘은 입력 특성 값과 출력 특성 값의 각 쌍을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-108">The algorithm considers each pair of input attribute values and output attribute values.</span></span>  
  
 <span data-ttu-id="becdd-109">이 설명서에서는 Bayes 정리의 수학적 속성에 대해 설명하지 않습니다. 이에 대한 자세한 내용은 [Bayesian 네트워크 학습: 지식 및 통계 데이터의 조합](https://go.microsoft.com/fwlink/?LinkId=207029)이라는 제목의 Microsoft Research 자료를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becdd-109">A description of the mathematical properties of Bayes Theorem is beyond the scope of this documentation; for more information, see the paper by Microsoft Research titled [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029).</span></span>  
  
 <span data-ttu-id="becdd-110">모든 모델의 확률이 잠재적인 누락 값을 설명하기 위해 조정되는 방식에 대한 설명은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becdd-110">For a description of how probabilities in all models are adjusted to account for potential missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="becdd-111">기능 선택</span><span class="sxs-lookup"><span data-stu-id="becdd-111">Feature Selection</span></span>  
 <span data-ttu-id="becdd-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 자동 기능 선택을 수행하여 모델을 작성할 때 고려되는 값의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm performs automatic feature selection to limit the number of values that are considered when building the model.</span></span> <span data-ttu-id="becdd-113">자세한 내용은 [기능 선택&#40;데이터 마이닝&#41;](feature-selection-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becdd-113">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>  
  
|<span data-ttu-id="becdd-114">알고리즘</span><span class="sxs-lookup"><span data-stu-id="becdd-114">Algorithm</span></span>|<span data-ttu-id="becdd-115">분석 방법</span><span class="sxs-lookup"><span data-stu-id="becdd-115">Method of analysis</span></span>|<span data-ttu-id="becdd-116">주석</span><span class="sxs-lookup"><span data-stu-id="becdd-116">Comments</span></span>|  
|---------------|------------------------|--------------|  
|<span data-ttu-id="becdd-117">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="becdd-117">Naive Bayes</span></span>|<span data-ttu-id="becdd-118">Shannon Entropy</span><span class="sxs-lookup"><span data-stu-id="becdd-118">Shannon's Entropy</span></span><br /><br /> <span data-ttu-id="becdd-119">Bayesian with K2 Prior</span><span class="sxs-lookup"><span data-stu-id="becdd-119">Bayesian with K2 Prior</span></span><br /><br /> <span data-ttu-id="becdd-120">Bayesian Dirichlet with uniform prior(기본값)</span><span class="sxs-lookup"><span data-stu-id="becdd-120">Bayesian Dirichlet with uniform prior (default)</span></span>|<span data-ttu-id="becdd-121">Naive Bayes는 불연속 또는 분할된 특성만 허용하므로 흥미도 점수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-121">Naive Bayes only accepts discrete or discretized attributes; therefore, it cannot use the interestingness score.</span></span>|  
  
 <span data-ttu-id="becdd-122">이 알고리즘은 처리 시간을 최소화하고 가장 중요한 특성을 효율적으로 선택할 수 있도록 디자인되었습니다. 그러나 사용자가 다음과 같은 매개 변수를 설정하여 알고리즘에 사용되는 데이터를 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-122">The algorithm is designed to minimize processing time and efficiently select the attributes that have the greatest importance; however, you can control the data that is used by the algorithm by setting parameters as follows:</span></span>  
  
-   <span data-ttu-id="becdd-123">입력으로 사용되는 값을 제한하려면 MAXIMUM_INPUT_ATTRIBUTES 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-123">To limit the values that are used as inputs, decrease the value of MAXIMUM_INPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="becdd-124">모델이 분석하는 특성의 수를 제한하려면 MAXIMUM_OUTPUT_ATTRIBUTES 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-124">To limit the number of attributes analyzed by the model, decrease the value of MAXIMUM_OUTPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="becdd-125">하나의 특성에 대해 고려할 수 있는 값의 수를 제한하려면 MINIMUM_STATES 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-125">To limit the number of values that can be considered for any one attribute, decrease the value of MINIMUM_STATES.</span></span>  
  
## <a name="customizing-the-naive-bayes-algorithm"></a><span data-ttu-id="becdd-126">Naive Bayes 알고리즘 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="becdd-126">Customizing the Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="becdd-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 결과 마이닝 모델의 동작, 성능 및 정확도에 영향을 주는 여러 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-127">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="becdd-128">모델 열에 모델링 플래그를 설정하여 데이터 처리 방식을 제어하거나, 마이닝 구조에 플래그를 설정하여 누락 값 또는 Null이 처리되는 방식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-128">You can also set modeling flags on the model columns to control how data is processed, or set flags on the mining structure to specify how missing values or nulls should be handled.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="becdd-129">알고리즘 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="becdd-129">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="becdd-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 결과 마이닝 모델의 성능 및 정확도에 영향을 주는 여러 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-130">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the performance and accuracy of the resulting mining model.</span></span> <span data-ttu-id="becdd-131">다음 표에서는 각 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-131">The following table describes each parameter.</span></span>  
  
 <span data-ttu-id="becdd-132">*MAXIMUM_INPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="becdd-132">*MAXIMUM_INPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="becdd-133">기능 선택을 호출하기 전에 알고리즘이 처리할 수 있는 최대 입력 특성 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-133">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="becdd-134">이 값을 0으로 설정하면 입력 특성에 대해 기능 선택을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-134">Setting this value to 0 disables feature selection for input attributes.</span></span>  
  
 <span data-ttu-id="becdd-135">기본값은 255입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-135">The default is 255.</span></span>  
  
 <span data-ttu-id="becdd-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="becdd-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="becdd-137">기능 선택을 호출하기 전에 알고리즘이 처리할 수 있는 최대 출력 특성 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-137">Specifies the maximum number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="becdd-138">이 값을 0으로 설정하면 출력 특성에 대해 기능 선택을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-138">Setting this value to 0 disables feature selection for output attributes.</span></span>  
  
 <span data-ttu-id="becdd-139">기본값은 255입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-139">The default is 255.</span></span>  
  
 <span data-ttu-id="becdd-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="becdd-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span></span>  
 <span data-ttu-id="becdd-141">입력 특성과 출력 특성 간의 최소 종속성 확률을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-141">Specifies the minimum dependency probability between input and output attributes.</span></span> <span data-ttu-id="becdd-142">이 값은 알고리즘에서 생성하는 내용의 크기를 제한하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-142">This value is used to limit the size of the content that is generated by the algorithm.</span></span> <span data-ttu-id="becdd-143">이 속성은 0과 1 사이의 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-143">This property can be set from 0 to 1.</span></span> <span data-ttu-id="becdd-144">이보다 큰 값을 지정하면 모델 내용의 특성 수가 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-144">Larger values reduce the number of attributes in the content of the model.</span></span>  
  
 <span data-ttu-id="becdd-145">기본값은 0.5입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-145">The default is 0.5.</span></span>  
  
 <span data-ttu-id="becdd-146">*MAXIMUM_STATES*</span><span class="sxs-lookup"><span data-stu-id="becdd-146">*MAXIMUM_STATES*</span></span>  
 <span data-ttu-id="becdd-147">알고리즘이 지원하는 최대 특성 상태 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-147">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="becdd-148">특성의 상태 수가 최대 상태 수보다 큰 경우 알고리즘은 특성의 가장 인기 있는 상태를 사용 하 고 나머지 상태를 누락 된 것으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-148">If the number of states that an attribute has is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as missing.</span></span>  
  
 <span data-ttu-id="becdd-149">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-149">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="becdd-150">모델링 플래그</span><span class="sxs-lookup"><span data-stu-id="becdd-150">Modeling Flags</span></span>  
 <span data-ttu-id="becdd-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘은 다음과 같은 모델링 플래그를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-151">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the following modeling flags.</span></span> <span data-ttu-id="becdd-152">마이닝 구조나 마이닝 모델을 만들 경우 분석 중 각 열의 값이 처리되는 방법을 지정하기 위해 모델링 플래그를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-152">When you create the mining structure or mining model, you define modeling flags to specify how values in each column are handled during analysis.</span></span> <span data-ttu-id="becdd-153">자세한 내용은 [모델링 플래그&#40;데이터 마이닝&#41;](modeling-flags-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becdd-153">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
|<span data-ttu-id="becdd-154">모델링 플래그</span><span class="sxs-lookup"><span data-stu-id="becdd-154">Modeling Flag</span></span>|<span data-ttu-id="becdd-155">Description</span><span class="sxs-lookup"><span data-stu-id="becdd-155">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="becdd-156">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="becdd-156">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="becdd-157">열이 누락 및 있음 상태를 갖는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-157">Means that the column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="becdd-158">Null은 누락 값입니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-158">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="becdd-159">마이닝 모델 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-159">Applies to mining model column.</span></span>|  
|<span data-ttu-id="becdd-160">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="becdd-160">NOT NULL</span></span>|<span data-ttu-id="becdd-161">열에 null이 포함될 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-161">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="becdd-162">따라서 Analysis Services가 모델 학습 중 Null을 발견할 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-162">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="becdd-163">마이닝 구조 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-163">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="becdd-164">요구 사항</span><span class="sxs-lookup"><span data-stu-id="becdd-164">Requirements</span></span>  
 <span data-ttu-id="becdd-165">Naive Bayes 트리 모델은 하나의 키 열, 하나 이상의 예측 가능한 특성 및 하나 이상의 입력 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-165">A Naive Bayes tree model must contain a key column, at least one predictable attribute, and at least one input attribute.</span></span> <span data-ttu-id="becdd-166">특성은 연속일 수 없으므로 데이터에 연속 숫자 데이터가 들어 있는 경우 해당 데이터는 무시되거나 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-166">No attribute can be continuous; if your data contains continuous numeric data, it will be ignored or discretized.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="becdd-167">입력 열과 예측 가능한 열</span><span class="sxs-lookup"><span data-stu-id="becdd-167">Input and Predictable Columns</span></span>  
 <span data-ttu-id="becdd-168">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 다음 표에 나열된 특정 입력 열과 예측 가능한 열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-168">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="becdd-169">마이닝 모델에 사용되는 경우 콘텐츠 형식의 의미에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="becdd-169">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="becdd-170">열</span><span class="sxs-lookup"><span data-stu-id="becdd-170">Column</span></span>|<span data-ttu-id="becdd-171">내용 유형</span><span class="sxs-lookup"><span data-stu-id="becdd-171">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="becdd-172">입력 특성</span><span class="sxs-lookup"><span data-stu-id="becdd-172">Input attribute</span></span>|<span data-ttu-id="becdd-173">Cyclical, Discrete, Discretized, Key, Table 및 Ordered</span><span class="sxs-lookup"><span data-stu-id="becdd-173">Cyclical, Discrete, Discretized, Key, Table, and Ordered</span></span>|  
|<span data-ttu-id="becdd-174">예측 가능한 특성</span><span class="sxs-lookup"><span data-stu-id="becdd-174">Predictable attribute</span></span>|<span data-ttu-id="becdd-175">Cyclical, Discrete, Discretized, Table 및 Ordered</span><span class="sxs-lookup"><span data-stu-id="becdd-175">Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="becdd-176">Cyclical  및 Ordered  내용 유형이 지원되기는 하지만 알고리즘은 해당 유형을 불연속 값으로 처리하고 특수한 처리를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="becdd-176">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becdd-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="becdd-177">See Also</span></span>  
 <span data-ttu-id="becdd-178">[Microsoft Naive Bayes 알고리즘](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="becdd-178">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="becdd-179">[Naive Bayes 모델 쿼리 예제](naive-bayes-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="becdd-179">[Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) </span></span>  
 [<span data-ttu-id="becdd-180">Naive Bayes 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="becdd-180">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
