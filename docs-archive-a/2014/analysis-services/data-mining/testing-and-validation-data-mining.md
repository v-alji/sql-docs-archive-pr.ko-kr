---
title: 테스트 및 유효성 검사 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c12f0215daed0c3308c63f36df0ba323152ec8d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639089"
---
# <a name="testing-and-validation-data-mining"></a><span data-ttu-id="d4a91-102">테스트 및 유효성 검사(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="d4a91-102">Testing and Validation (Data Mining)</span></span>
  <span data-ttu-id="d4a91-103">유효성 검사는 실제 데이터에 대한 마이닝 모델의 성능을 평가하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-103">Validation is the process of assessing how well your mining models perform against real data.</span></span> <span data-ttu-id="d4a91-104">마이닝 모델을 프로덕션 환경으로 배포하기 전에 품질과 특징을 이해하여 마이닝 모델의 유효성을 검사하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-104">It is important that you validate your mining models by understanding their quality and characteristics before you deploy them into a production environment.</span></span>  
  
 <span data-ttu-id="d4a91-105">이 섹션에서는 모델 품질과 관련 된 몇 가지 기본 개념을 소개 하 고에 제공 된 모델 유효성 검사에 대 한 전략을 설명 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d4a91-105">This section introduces some basic concepts related to model quality, and describes the strategies for model validation that are provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d4a91-106">대규모 데이터 마이닝 프로세스에서 모델 유효성 검사를 수행하는 방법에 대한 개요는 [데이터 마이닝 솔루션](data-mining-solutions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4a91-106">For an overview of how model validation fits into the larger data mining process, see [Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a><span data-ttu-id="d4a91-107">데이터 마이닝 모델의 테스트 및 유효성 검사 방법</span><span class="sxs-lookup"><span data-stu-id="d4a91-107">Methods for Testing and Validation of Data Mining Models</span></span>  
 <span data-ttu-id="d4a91-108">데이터 마이닝 모델의 품질과 특징을 평가하는 데에는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-108">There are many approaches for assessing the quality and characteristics of a data mining model.</span></span>  
  
-   <span data-ttu-id="d4a91-109">통계 유효성의 다양한 측정값을 사용하여 데이터나 모델에 문제가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-109">Use various measures of statistical validity to determine whether there are problems in the data or in the model.</span></span>  
  
-   <span data-ttu-id="d4a91-110">데이터를 학습 집합과 테스트 집합으로 구분하여 예측의 정확도를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-110">Separate the data into training and testing sets to test the accuracy of predictions.</span></span>  
  
-   <span data-ttu-id="d4a91-111">비즈니스 전문가에게 데이터 마이닝 모델의 결과를 검토하도록 요청하여 검색된 패턴이 대상 비즈니스 시나리오에서 의미가 있는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-111">Ask business experts to review the results of the data mining model to determine whether the discovered patterns have meaning in the targeted business scenario</span></span>  
  
 <span data-ttu-id="d4a91-112">이러한 모든 방법은 데이터 마이닝 방법에서 유용하며 특정 문제를 해결하기 위한 모델을 생성, 테스트 및 구체화하면서 반복적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-112">All of these methods are useful in data mining methodology and are used iteratively as you create, test, and refine models to answer a specific problem.</span></span> <span data-ttu-id="d4a91-113">모델이 적당하거나 데이터가 충분하다고 판단하는 기준으로 삼을 수 있는 하나의 포괄적인 규칙은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-113">No single comprehensive rule can tell you when a model is good enough, or when you have enough data.</span></span>  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a><span data-ttu-id="d4a91-114">데이터 마이닝 모델의 유효성 검사를 위한 기준 정의</span><span class="sxs-lookup"><span data-stu-id="d4a91-114">Definition of Criteria for Validating Data Mining Models</span></span>  
 <span data-ttu-id="d4a91-115">데이터 마이닝의 측정값은 일반적으로 정확도, 안정성 및 유용성의 범주로 나누어집니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-115">Measures of data mining generally fall into the categories of accuracy, reliability, and usefulness.</span></span>  
  
 <span data-ttu-id="d4a91-116">*정확도* 는 모델에서 제공된 데이터의 특성과 결과 간 상관 관계를 나타내는 측정값입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-116">*Accuracy* is a measure of how well the model correlates an outcome with the attributes in the data that has been provided.</span></span> <span data-ttu-id="d4a91-117">다양한 정확도 측정값이 있지만 모든 정확도 측정값은 사용되는 데이터에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-117">There are various measures of accuracy, but all measures of accuracy are dependent on the data that is used.</span></span> <span data-ttu-id="d4a91-118">실제로는 값이 없거나 근사값일 수 있으며 여러 프로세스에 의해 데이터가 변경되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-118">In reality, values might be missing or approximate, or the data might have been changed by multiple processes.</span></span> <span data-ttu-id="d4a91-119">특히 탐색 및 개발 단계에서 데이터의 특징이 비교적 균일한 경우 데이터에서 오류가 일정 정도 발생하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-119">Particularly in the phase of exploration and development, you might decide to accept a certain amount of error in the data, especially if the data is fairly uniform in its characteristics.</span></span> <span data-ttu-id="d4a91-120">예를 들어 과거 판매량을 기반으로 특정 매장의 판매량을 예측하는 모델은 해당 매장에서 계속 잘못된 회계 방법을 사용한 경우에도 상관 관계가 높고 매우 정확할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-120">For example, a model that predicts sales for a particular store based on past sales can be strongly correlated and very accurate, even if that store consistently used the wrong accounting method.</span></span> <span data-ttu-id="d4a91-121">따라서 정확도 측정은 안정성 평가에 따라 균형을 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-121">Therefore, measurements of accuracy must be balanced by assessments of reliability.</span></span>  
  
 <span data-ttu-id="d4a91-122">*안정성* 은 다른 데이터 집합에 대한 데이터 마이닝 모델의 성능을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-122">*Reliability* assesses the way that a data mining model performs on different data sets.</span></span> <span data-ttu-id="d4a91-123">제공된 테스트 데이터와 상관없이 동일한 유형의 예측을 생성하거나 동일한 일반적인 종류의 패턴을 찾는 경우 데이터 마이닝 모델은 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-123">A data mining model is reliable if it generates the same type of predictions or finds the same general kinds of patterns regardless of the test data that is supplied.</span></span> <span data-ttu-id="d4a91-124">예를 들어 잘못된 회계 방법을 사용한 매장에 대해 생성하는 모델은 다른 매장에도 적용할 수 있을 정도로 일반화될 수 없으므로 안정적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-124">For example, the model that you generate for the store that used the wrong accounting method would not generalize well to other stores, and therefore would not be reliable.</span></span>  
  
 <span data-ttu-id="d4a91-125">*유용성* 에는 모델이 유용한 정보를 제공하는지 여부를 알려 주는 다양한 메트릭이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-125">*Usefulness* includes various metrics that tell you whether the model provides useful information.</span></span> <span data-ttu-id="d4a91-126">예를 들어 매장 위치와 판매량 간 상관 관계를 찾는 데이터 마이닝 모델은 정확하면서 안정적일 수 있지만 동일한 위치에 있는 다른 매장을 추가하여 결과를 일반화할 수 없으므로 유용하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-126">For example, a data mining model that correlates store location with sales might be both accurate and reliable, but might not be useful, because you cannot generalize that result by adding more stores at the same location.</span></span> <span data-ttu-id="d4a91-127">또한 이 모델로는 특정 위치에서 판매량이 왜 더 많은가라는 기본적인 비즈니스 질문에 대한 답을 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-127">Moreover, it does not answer the fundamental business question of why certain locations have more sales.</span></span> <span data-ttu-id="d4a91-128">성공적으로 보이는 모델이 데이터의 교차 상관 관계를 기반으로 하고 있기 때문에 실제로는 의미가 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-128">You might also find that a model that appears successful in fact is meaningless, because it is based on cross-correlations in the data.</span></span>  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a><span data-ttu-id="d4a91-129">마이닝 모델의 테스트 및 유효성 검사 도구</span><span class="sxs-lookup"><span data-stu-id="d4a91-129">Tools for Testing and Validation of Mining Models</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d4a91-130">에서는 데이터 마이닝 솔루션의 유효성을 여러 방법으로 검사하여 데이터 마이닝 테스트 방법의 모든 단계를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-130">supports multiple approaches to validation of data mining solutions, supporting all phases of the data mining test methodology.</span></span>  
  
-   <span data-ttu-id="d4a91-131">데이터를 학습 및 테스트 집합으로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-131">Partitioning data into testing and training sets.</span></span>  
  
-   <span data-ttu-id="d4a91-132">모델을 필터링하여 동일한 원본 데이터의 서로 다른 조합을 학습하고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-132">Filtering models to train and test different combinations of the same source data.</span></span>  
  
-   <span data-ttu-id="d4a91-133">*리프트* 및 *이득*을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-133">Measuring *lift* and *gain*.</span></span> <span data-ttu-id="d4a91-134">*리프트 차트* 는 데이터 마이닝 모델을 임의 추측과 비교할 때 데이터 마이닝 모델 사용에서 얻는 향상률을 시각화하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-134">A *lift chart* is a method of visualizing the improvement that you get from using a data mining model, when you compare it to random guessing.</span></span>  
  
-   <span data-ttu-id="d4a91-135">데이터 집합의 *교차 유효성 검사* 를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-135">Performing *cross-validation* of data sets</span></span>  
  
-   <span data-ttu-id="d4a91-136">*분류 행렬*을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-136">Generating *classification matrices*.</span></span> <span data-ttu-id="d4a91-137">이러한 차트에서는 모델이 대상 값을 정확하게 예측하는 정도를 쉽게 빠르고 측정할 수 있도록 올바른 추측과 잘못된 추측을 테이블로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-137">These charts sort good and bad guesses into a table so that you can quickly and easily gauge how accurately the model predicts the target value.</span></span>  
  
-   <span data-ttu-id="d4a91-138">회귀 수식에 맞는지 평가할 수 있는 *산점도* 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-138">Creating *scatter plots* to assess the fit of a regression formula.</span></span>  
  
-   <span data-ttu-id="d4a91-139">마이닝 모델 사용과 재무 이익 또는 비용을 연결하는 *수익 차트* 를 만들어 권장 구성의 값을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-139">Creating *profit charts* that associate financial gain or costs with the use of a mining model, so that you can assess the value of the recommendations.</span></span>  
  
 <span data-ttu-id="d4a91-140">이러한 메트릭의 목적은 데이터 마이닝 모델이 비즈니스 질문에 대한 해답을 제공하는지 여부에 대한 질문에 응답하는 것이 아닙니다. 그보다는 예측 분석을 위해 데이터의 안정성을 평가하고 개발 프로세스에서 특정 반복을 사용할지 여부를 결정하도록 돕는 데 사용할 수 있는 객관적인 측정값을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-140">These metrics do not aim to answer the question of whether the data mining model answers your business question; rather, these metrics provide objective measurements that you can use to assess the reliability of your data for predictive analytics, and to guide your decision of whether to use a particular iterate on the development process.</span></span>  
  
 <span data-ttu-id="d4a91-141">이 섹션의 항목에서는 각 방법의 개요를 제공하고 SQL Server 데이터 마이닝을 사용하여 빌드하는 모델의 정확도를 측정하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a91-141">The topics in this section provide an overview of each method and walk you through the process of measuring the accuracy of models that you build using SQL Server Data Mining.</span></span>  
  
### <a name="related-topics"></a><span data-ttu-id="d4a91-142">관련 항목</span><span class="sxs-lookup"><span data-stu-id="d4a91-142">Related Topics</span></span>  
  
|<span data-ttu-id="d4a91-143">토픽</span><span class="sxs-lookup"><span data-stu-id="d4a91-143">Topics</span></span>|<span data-ttu-id="d4a91-144">링크</span><span class="sxs-lookup"><span data-stu-id="d4a91-144">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="d4a91-145">마법사 또는 DMX 명령을 사용하여 테스트 데이터 집합을 설정하는 방법 배우기</span><span class="sxs-lookup"><span data-stu-id="d4a91-145">Learn how to set up a testing data set using a wizard or DMX commands</span></span>|[<span data-ttu-id="d4a91-146">데이터 집합 학습 및 테스트</span><span class="sxs-lookup"><span data-stu-id="d4a91-146">Training and Testing Data Sets</span></span>](training-and-testing-data-sets.md)|  
|<span data-ttu-id="d4a91-147">마이닝 구조에서 데이터의 배포 및 대표성을 테스트하는 방법 배우기</span><span class="sxs-lookup"><span data-stu-id="d4a91-147">Learn how to test the distribution and representativeness of the data in a mining structure</span></span>|[<span data-ttu-id="d4a91-148">교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-148">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="d4a91-149">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]에서 제공하는 정확도 차트 종류에 대해 배우기.</span><span class="sxs-lookup"><span data-stu-id="d4a91-149">Learn about the accuracy chart types provided in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span>|[<span data-ttu-id="d4a91-150">리프트 차트&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-150">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="d4a91-151">수익 차트&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-151">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="d4a91-152">산점도&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-152">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="d4a91-153">여러 참과 거짓의 긍정 및 부정을 평가할 수 있는 분류 행렬(혼동 행렬이라고도 함)을 만드는 방법 배우기.</span><span class="sxs-lookup"><span data-stu-id="d4a91-153">Learn how to create a classification matrix, sometimes called a confusion matrix, for assessing the number of true and false positives and negatives.</span></span>|[<span data-ttu-id="d4a91-154">분류표&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-154">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d4a91-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4a91-155">See Also</span></span>  
 <span data-ttu-id="d4a91-156">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d4a91-156">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="d4a91-157">[데이터 마이닝 솔루션](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="d4a91-157">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="d4a91-158">테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d4a91-158">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
