---
title: Microsoft 로지스틱 회귀 알고리즘 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logical regression algorithms [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 3dd54d07-1c3b-4b87-b7f0-b962ed8cf844
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56a1b0b82f82b62e55d0c7fdd528195b5713fcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660762"
---
# <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="c6fc5-102">Microsoft 로지스틱 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c6fc5-102">Microsoft Logistic Regression Algorithm</span></span>
  <span data-ttu-id="c6fc5-103">로지스틱 회귀는 이진 결과 모델링에 사용되는 유명한 통계 기법입니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-103">Logistic regression is a well-known statistical technique that is used for modeling binary outcomes.</span></span>  
  
 <span data-ttu-id="c6fc5-104">통계 연구에는 여러 가지 학습 기법을 사용하는 로지스틱 회귀의 다양한 구현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-104">There are various implementations of logistic regression in statistics research, using different learning techniques.</span></span> <span data-ttu-id="c6fc5-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 알고리즘은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘의 변형을 사용하여 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm has been implemented by using a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="c6fc5-106">이 알고리즘은 신경망의 많은 특성을 공유하지만 학습하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-106">This algorithm shares many of the qualities of neural networks but is easier to train.</span></span>  
  
 <span data-ttu-id="c6fc5-107">로지스틱 회귀는 매우 유연하여 모든 종류의 입력을 사용하며 다음과 같은 여러 가지 분석 태스크를 지원한다는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-107">One advantage of logistic regression is that the algorithm is highly flexible, taking any kind of input, and supports several different analytical tasks:</span></span>  
  
-   <span data-ttu-id="c6fc5-108">특정 질병의 위험성과 같은 결과를 예측하려면 인구 통계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-108">Use demographics to make predictions about outcomes, such as risk for a certain disease.</span></span>  
  
-   <span data-ttu-id="c6fc5-109">결과에 영향을 주는 요소를 조사하여 가중치를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-109">Explore and weight the factors that contribute to a result.</span></span> <span data-ttu-id="c6fc5-110">예를 들어 고객이 상점을 다시 방문하도록 하는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-110">For example, find the factors that influence customers to make a repeat visit to a store.</span></span>  
  
-   <span data-ttu-id="c6fc5-111">문서, 전자 메일 또는 여러 특성이 있는 기타 개체를 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-111">Classify documents, e-mail, or other objects that have many attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6fc5-112">예제</span><span class="sxs-lookup"><span data-stu-id="c6fc5-112">Example</span></span>  
 <span data-ttu-id="c6fc5-113">인구 통계 정보가 유사하며 Adventure Works사에서 제품을 구입하는 고객 그룹을 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-113">Consider a group of people who share similar demographic information and who buy products from the Adventure Works company.</span></span> <span data-ttu-id="c6fc5-114">대상 제품 구매 등의 특정 결과와 관계되도록 데이터를 모델링하여 인구 통계 정보에 따라 대상 제품에 대한 고객의 구매 가능성이 어떻게 달라지는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-114">By modeling the data to relate to a specific outcome, such as purchase of a target product, you can see how the demographic information contributes to someone's likelihood of buying the target product.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="c6fc5-115">알고리즘 작동 방법</span><span class="sxs-lookup"><span data-stu-id="c6fc5-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="c6fc5-116">로지스틱 회귀는 한 쌍의 결과에 대한 여러 요소의 기여도를 측정하는 유명한 통계 기법입니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-116">Logistic regression is a well-known statistical method for determining the contribution of multiple factors to a pair of outcomes.</span></span> <span data-ttu-id="c6fc5-117">Microsoft에서 구현한 방법은 수정된 신경망을 사용하여 입력과 출력 간의 관계를 모델링하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-117">The Microsoft implementation uses a modified neural network to model the relationships between inputs and outputs.</span></span> <span data-ttu-id="c6fc5-118">즉, 각 입력이 출력에 주는 영향을 측정하고 완성된 모델에서 다양한 입력에 가중치를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-118">The effect of each input on the output is measured, and the various inputs are weighted in the finished model.</span></span> <span data-ttu-id="c6fc5-119">로지스틱 회귀라는 이름은 데이터 곡선이 로지스틱 변환을 통해 요약되어 극단적인 값으로 인한 영향을 최소화한다는 사실에서 비롯된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-119">The name logistic regression comes from the fact that the data curve is compressed by using a logistic transformation, to minimize the effect of extreme values.</span></span> <span data-ttu-id="c6fc5-120">구현에 대한 자세한 내용과 알고리즘을 사용자 지정하는 방법에 대한 자세한 내용은 [Microsoft 로지스틱 회귀 알고리즘 기술 참조](microsoft-logistic-regression-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-120">For more information about the implementation, and how to customize the algorithm, see [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-logistic-regression-models"></a><span data-ttu-id="c6fc5-121">로지스틱 회귀 모델에 필요한 데이터</span><span class="sxs-lookup"><span data-stu-id="c6fc5-121">Data Required for Logistic Regression Models</span></span>  
 <span data-ttu-id="c6fc5-122">로지스틱 회귀 모델을 학습하는 데 사용할 데이터를 준비할 때는 필요한 데이터의 양과 사용법을 비롯하여 특정 알고리즘의 요구 사항을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-122">When you prepare data for use in training a logistic regression model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>  
  
 <span data-ttu-id="c6fc5-123">로지스틱 회귀 모델의 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-123">The requirements for a logistic regression model are as follows:</span></span>  
  
 <span data-ttu-id="c6fc5-124">**단일 키 열** 각 모델은 각 레코드를 고유하게 식별하는 숫자 또는 텍스트 열을 하나 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-124">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="c6fc5-125">복합 키는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-125">Compound keys are not allowed.</span></span>  
  
 <span data-ttu-id="c6fc5-126">**입력 열** 각 모델은 분석에서 요소로 사용되는 값을 포함하는 입력 열을 하나 이상 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-126">**Input columns** Each model must contain at least one input column that contains the values that are used as factors in analysis.</span></span> <span data-ttu-id="c6fc5-127">입력 열은 원하는 만큼 사용할 수 있지만 각 열의 값 수에 따라 추가되는 열로 인해 모델 학습에 걸리는 시간이 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-127">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>  
  
 <span data-ttu-id="c6fc5-128">**하나 이상의 예측 가능한 열** 모델은 연속 숫자 데이터를 포함하여 모든 데이터 형식의 예측 가능한 열을 하나 이상 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-128">**At least one predictable column** The model must contain at least one predictable column of any data type, including continuous numeric data.</span></span> <span data-ttu-id="c6fc5-129">또한 예측 가능한 열의 값은 모델에 대한 입력으로 처리될 수도 있고, 이를 예측용으로만 사용하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-129">The values of the predictable column can also be treated as inputs to the model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="c6fc5-130">중첩 테이블은 예측 가능한 열에 사용할 수 없지만 입력으로는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-130">Nested tables are not allowed for predictable columns, but can be used as inputs.</span></span>  
  
 <span data-ttu-id="c6fc5-131">로지스틱 회귀 모델에 대해 지원되는 콘텐츠 형식 및 데이터 형식에 대한 자세한 내용은 [Microsoft 로지스틱 회귀 알고리즘 기술 참조](microsoft-logistic-regression-algorithm-technical-reference.md)의 요구 사항 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-131">For more detailed information about the content types and data types supported for logistic regression models, see the Requirements section of [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-logistic-regression-model"></a><span data-ttu-id="c6fc5-132">로지스틱 회귀 모델 보기</span><span class="sxs-lookup"><span data-stu-id="c6fc5-132">Viewing a Logistic Regression Model</span></span>  
 <span data-ttu-id="c6fc5-133">모델을 탐색하려면 Microsoft 신경망 뷰어 또는 Microsoft 일반 콘텐츠 트리 뷰어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-133">To explore the model, you can use the Microsoft Neural Network Viewer, or the Microsoft Generic Content Tree Viewer.</span></span>  
  
 <span data-ttu-id="c6fc5-134">Microsoft 신경망 뷰어를 사용하여 모델을 보는 경우 Analysis Services에서는 특정 결과에 영향을 주는 요소를 중요도에 따라 순위를 지정하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-134">When you view the model by using the Microsoft Neural Network Viewer, Analysis Services shows you the factors that contribute to a particular outcome, ranked by their importance.</span></span> <span data-ttu-id="c6fc5-135">비교할 특성 및 값은 사용자가 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-135">You can choose an attribute and values to compare.</span></span> <span data-ttu-id="c6fc5-136">자세한 내용은 [Microsoft 신경망 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-neural-network-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-136">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="c6fc5-137">보다 자세한 내용을 보려면 Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 세부 정보를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-137">If you want to know more, you can browse the model details by using the Microsoft Generic Content Tree Viewer.</span></span> <span data-ttu-id="c6fc5-138">로지스틱 회귀 모델의 모델 콘텐츠에는 모델에 사용된 모든 입력과 예측 가능한 특성의 하위 네트워크를 보여 주는 한계 노드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-138">The model content for a logistic regression model includes a marginal node that shows you the all the inputs used for the model, and subnetworks for the predictable attributes.</span></span> <span data-ttu-id="c6fc5-139">자세한 내용은 [로지스틱 회귀 분석 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-139">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="c6fc5-140">예측 만들기</span><span class="sxs-lookup"><span data-stu-id="c6fc5-140">Creating Predictions</span></span>  
 <span data-ttu-id="c6fc5-141">모델을 학습한 후에는 모델 콘텐츠에 대한 쿼리를 만들어 회귀 계수 및 기타 세부 정보를 가져오거나, 모델을 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-141">After the model has been trained, you can create queries against the model content to get the regression coefficients and other details, or you can use the model to make predictions.</span></span>  
  
-   <span data-ttu-id="c6fc5-142">데이터 마이닝 모델에 대한 쿼리를 만드는 방법에 대한 일반적인 내용은 [데이터 마이닝 쿼리](data-mining-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-142">For general information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
-   <span data-ttu-id="c6fc5-143">로지스틱 회귀 모델에 대한 쿼리 예는 [클러스터링 모델 쿼리 예제](clustering-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-143">For examples of queries on a logistic regression model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6fc5-144">설명</span><span class="sxs-lookup"><span data-stu-id="c6fc5-144">Remarks</span></span>  
  
-   <span data-ttu-id="c6fc5-145">드릴스루는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-145">Does not support drillthrough.</span></span> <span data-ttu-id="c6fc5-146">이는 마이닝 모델의 노드 구조가 기본 데이터와 반드시 일치하지는 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-146">This is because the structure of nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="c6fc5-147">데이터 마이닝 차원의 생성은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-147">Does not support the creation of data mining dimensions.</span></span>  
  
-   <span data-ttu-id="c6fc5-148">OLAP 마이닝 모델의 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-148">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="c6fc5-149">PMML(Predictive Model Markup Language)을 사용한 마이닝 모델 생성은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6fc5-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6fc5-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6fc5-150">See Also</span></span>  
 <span data-ttu-id="c6fc5-151">[로지스틱 회귀 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="c6fc5-151">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 <span data-ttu-id="c6fc5-152">[Microsoft 로지스틱 회귀 알고리즘 기술 참조](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c6fc5-152">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="c6fc5-153">로지스틱 회귀 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="c6fc5-153">Logistic Regression Model Query Examples</span></span>](logistic-regression-model-query-examples.md)  
  
  
