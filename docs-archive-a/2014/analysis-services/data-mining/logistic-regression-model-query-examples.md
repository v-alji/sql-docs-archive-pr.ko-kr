---
title: 로지스틱 회귀 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- content queries [DMX]
ms.assetid: 7c8e13a3-5c67-46c2-abfa-4881e6ef9c62
author: minewiskan
ms.author: owend
ms.openlocfilehash: d432d38794e65e8b8bea69608479e330649ee395
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639113"
---
# <a name="logistic-regression-model-query-examples"></a><span data-ttu-id="30ac7-102">로지스틱 회귀 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="30ac7-102">Logistic Regression Model Query Examples</span></span>
  <span data-ttu-id="30ac7-103">데이터 마이닝 모델에 대한 쿼리를 작성할 때 분석 중에 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 작성하거나, 모델의 패턴을 사용하여 새 데이터를 사용한 예측을 만드는 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions using new data.</span></span>  
  
 <span data-ttu-id="30ac7-104">이 섹션에서는 Microsoft 로지스틱 회귀 알고리즘을 기반으로 하는 모델에 대해 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-104">This section explains how to create queries for models that are based on the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="30ac7-105">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="30ac7-105">**Content Queries**</span></span>  
  
 [<span data-ttu-id="30ac7-106">데이터 마이닝 스키마 행 집합을 사용하여 모델 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="30ac7-106">Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="30ac7-107">DMX를 사용하여 모델에 대한 추가 세부 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="30ac7-107">Finding Additional Detail about the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 <span data-ttu-id="30ac7-108">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="30ac7-108">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="30ac7-109">연속 값에 대한 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="30ac7-109">Making Predictions for a Continuous Value</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="30ac7-110">불연속 값에 대한 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="30ac7-110">Making Predictions for a Discrete Value</span></span>](#bkmk_Query4)  
  
##  <a name="getting-information-about-the-logistic-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="30ac7-111">로지스틱 회귀 모델에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="30ac7-111">Getting Information about the Logistic Regression Model</span></span>  
 <span data-ttu-id="30ac7-112">로지스틱 회귀 모델은 Microsoft 신경망 알고리즘과 특수한 매개 변수 집합을 사용하여 만듭니다. 따라서 로지스틱 회귀 모델은 신경망 모델과 동일한 정보를 일부 포함하지만 신경망 모델보다는 덜 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-112">Logistic regression models are created by using the Microsoft Neural Network algorithm with a special set of parameters; therefore, a logistic regression model has some of the same information as a neural networks model, but is less complex.</span></span> <span data-ttu-id="30ac7-113">모델 콘텐츠의 구조와 노드 유형에 따라 저장되는 정보의 종류를 이해하려면 [로지스틱 회귀 분석 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-113">To understand the structure of the model content, and which node types store what kind of information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 <span data-ttu-id="30ac7-114">중급 데이터 마이닝 자습서의 [5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-114">To follow along in the query scenarios, you can create a logistic regression model as described in the following section of the Intermediate Data Mining Tutorial: [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="30ac7-115">[기본 데이터 마이닝 자습서](../../tutorials/basic-data-mining-tutorial.md)의 마이닝 구조인 타겟 메일링을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-115">You can also use the mining structure, Targeted Mailing, from the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
ALTER MINING STRUCTURE [Targeted Mailing]  
ADD MINING MODEL [TM_Logistic Regression]  
([Customer Key],  
[Age],  
[Bike Buyer] PREDICT,  
[Yearly Income] PREDICT,  
[Commute Distance],  
[English Education],  
Gender,  
[House Owner Flag],  
[Marital Status],  
[Number Cars Owned],  
[Number Children At Home],  
[Region],  
[Total Children]  
)  
USING Microsoft_Logistic_Regression  
```  
  
###  <a name="sample-query-1-retrieving-model-parameters-by-using-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="30ac7-116">예제 쿼리 1: 데이터 마이닝 스키마 행 집합을 사용 하 여 모델 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="30ac7-116">Sample Query 1: Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="30ac7-117">데이터 마이닝 스키마 행 집합을 쿼리하면 모델이 만들어진 날짜, 모델이 마지막으로 처리된 날짜, 모델의 기반이 되는 마이닝 구조의 이름, 예측 가능한 특성으로 사용된 열 이름 등 모델에 대한 메타데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-117">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="30ac7-118">다음 예에서는 모델을 처음 만들 때 사용한 매개 변수와 함께 모델의 이름, 유형 및 작성 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-118">The following example returns the parameters that were used when the model was first created, together with the name and type of the model, and the date that it was created.</span></span>  
  
```  
SELECT MODEL_NAME, SERVICE_NAME, DATE_CREATED, MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center_LR'  
```  
  
 <span data-ttu-id="30ac7-119">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="30ac7-119">Sample results:</span></span>  
  
|<span data-ttu-id="30ac7-120">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="30ac7-120">MODEL_NAME</span></span>|<span data-ttu-id="30ac7-121">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="30ac7-121">SERVICE_NAME</span></span>|<span data-ttu-id="30ac7-122">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="30ac7-122">DATE_CREATED</span></span>|<span data-ttu-id="30ac7-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30ac7-123">MINING_PARAMETERS</span></span>|  
|-----------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="30ac7-124">Call Center_LR</span><span class="sxs-lookup"><span data-stu-id="30ac7-124">Call Center_LR</span></span>|<span data-ttu-id="30ac7-125">Microsoft_Logistic_Regression</span><span class="sxs-lookup"><span data-stu-id="30ac7-125">Microsoft_Logistic_Regression</span></span>|<span data-ttu-id="30ac7-126">04/07/2009 20:38:33</span><span class="sxs-lookup"><span data-stu-id="30ac7-126">04/07/2009 20:38:33</span></span>|<span data-ttu-id="30ac7-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span><span class="sxs-lookup"><span data-stu-id="30ac7-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span></span>|  
  
###  <a name="sample-query-2-finding-additional-detail-about-the-model-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="30ac7-128">예제 쿼리 2: DMX를 사용 하 여 모델에 대 한 추가 세부 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="30ac7-128">Sample Query 2: Finding Additional Detail about the Model by Using DMX</span></span>  
 <span data-ttu-id="30ac7-129">다음 쿼리에서는 로지스틱 회귀 모델에 대한 몇 가지 기본 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-129">The following query returns some basic information about the logistic regression model.</span></span> <span data-ttu-id="30ac7-130">로지스틱 회귀 모델은 입력으로 사용된 값을 설명하는 한계 통계 노드(NODE_TYPE = 24)가 있다는 점을 비롯하여 여러 면에서 신경망 모델과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-130">A logistic regression model is similar to a neural network model in many ways, including the presence of a marginal statistic node (NODE_TYPE = 24) that describes the values used as inputs.</span></span> <span data-ttu-id="30ac7-131">이 예제 쿼리에서는 Targeted Mailing 모델을 사용하며 NODE_DISTRIBUTION이라는 중첩 테이블에서 값을 검색해 모든 입력의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-131">This example query uses the Targeted Mailing model, and gets the values of all the inputs by retrieving them from the nested table, NODE_DISTRIBUTION.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM [TM_Logistic Regression].CONTENT   
```  
  
 <span data-ttu-id="30ac7-132">일부 결과:</span><span class="sxs-lookup"><span data-stu-id="30ac7-132">Partial results:</span></span>  
  
|<span data-ttu-id="30ac7-133">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="30ac7-133">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="30ac7-134">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="30ac7-134">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="30ac7-135">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="30ac7-135">t.SUPPORT</span></span>|<span data-ttu-id="30ac7-136">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="30ac7-136">t.PROBABILITY</span></span>|<span data-ttu-id="30ac7-137">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="30ac7-137">t.VARIANCE</span></span>|<span data-ttu-id="30ac7-138">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="30ac7-138">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="30ac7-139">연령</span><span class="sxs-lookup"><span data-stu-id="30ac7-139">Age</span></span>|<span data-ttu-id="30ac7-140">Missing</span><span class="sxs-lookup"><span data-stu-id="30ac7-140">Missing</span></span>|<span data-ttu-id="30ac7-141">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-141">0</span></span>|<span data-ttu-id="30ac7-142">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-142">0</span></span>|<span data-ttu-id="30ac7-143">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-143">0</span></span>|<span data-ttu-id="30ac7-144">1</span><span class="sxs-lookup"><span data-stu-id="30ac7-144">1</span></span>|  
|<span data-ttu-id="30ac7-145">연령</span><span class="sxs-lookup"><span data-stu-id="30ac7-145">Age</span></span>|<span data-ttu-id="30ac7-146">45.43491192</span><span class="sxs-lookup"><span data-stu-id="30ac7-146">45.43491192</span></span>|<span data-ttu-id="30ac7-147">17484</span><span class="sxs-lookup"><span data-stu-id="30ac7-147">17484</span></span>|<span data-ttu-id="30ac7-148">1</span><span class="sxs-lookup"><span data-stu-id="30ac7-148">1</span></span>|<span data-ttu-id="30ac7-149">126.9544114</span><span class="sxs-lookup"><span data-stu-id="30ac7-149">126.9544114</span></span>|<span data-ttu-id="30ac7-150">3</span><span class="sxs-lookup"><span data-stu-id="30ac7-150">3</span></span>|  
|<span data-ttu-id="30ac7-151">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="30ac7-151">Bike Buyer</span></span>|<span data-ttu-id="30ac7-152">Missing</span><span class="sxs-lookup"><span data-stu-id="30ac7-152">Missing</span></span>|<span data-ttu-id="30ac7-153">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-153">0</span></span>|<span data-ttu-id="30ac7-154">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-154">0</span></span>|<span data-ttu-id="30ac7-155">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-155">0</span></span>|<span data-ttu-id="30ac7-156">1</span><span class="sxs-lookup"><span data-stu-id="30ac7-156">1</span></span>|  
|<span data-ttu-id="30ac7-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="30ac7-157">Bike Buyer</span></span>|<span data-ttu-id="30ac7-158">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-158">0</span></span>|<span data-ttu-id="30ac7-159">8869</span><span class="sxs-lookup"><span data-stu-id="30ac7-159">8869</span></span>|<span data-ttu-id="30ac7-160">0.507263784</span><span class="sxs-lookup"><span data-stu-id="30ac7-160">0.507263784</span></span>|<span data-ttu-id="30ac7-161">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-161">0</span></span>|<span data-ttu-id="30ac7-162">4</span><span class="sxs-lookup"><span data-stu-id="30ac7-162">4</span></span>|  
|<span data-ttu-id="30ac7-163">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="30ac7-163">Bike Buyer</span></span>|<span data-ttu-id="30ac7-164">1</span><span class="sxs-lookup"><span data-stu-id="30ac7-164">1</span></span>|<span data-ttu-id="30ac7-165">8615</span><span class="sxs-lookup"><span data-stu-id="30ac7-165">8615</span></span>|<span data-ttu-id="30ac7-166">0.492736216</span><span class="sxs-lookup"><span data-stu-id="30ac7-166">0.492736216</span></span>|<span data-ttu-id="30ac7-167">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-167">0</span></span>|<span data-ttu-id="30ac7-168">4</span><span class="sxs-lookup"><span data-stu-id="30ac7-168">4</span></span>|  
|<span data-ttu-id="30ac7-169">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="30ac7-169">Commute Distance</span></span>|<span data-ttu-id="30ac7-170">Missing</span><span class="sxs-lookup"><span data-stu-id="30ac7-170">Missing</span></span>|<span data-ttu-id="30ac7-171">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-171">0</span></span>|<span data-ttu-id="30ac7-172">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-172">0</span></span>|<span data-ttu-id="30ac7-173">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-173">0</span></span>|<span data-ttu-id="30ac7-174">1</span><span class="sxs-lookup"><span data-stu-id="30ac7-174">1</span></span>|  
|<span data-ttu-id="30ac7-175">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="30ac7-175">Commute Distance</span></span>|<span data-ttu-id="30ac7-176">5-10 Miles</span><span class="sxs-lookup"><span data-stu-id="30ac7-176">5-10 Miles</span></span>|<span data-ttu-id="30ac7-177">3033</span><span class="sxs-lookup"><span data-stu-id="30ac7-177">3033</span></span>|<span data-ttu-id="30ac7-178">0.173472889</span><span class="sxs-lookup"><span data-stu-id="30ac7-178">0.173472889</span></span>|<span data-ttu-id="30ac7-179">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-179">0</span></span>|<span data-ttu-id="30ac7-180">4</span><span class="sxs-lookup"><span data-stu-id="30ac7-180">4</span></span>|  
  
 <span data-ttu-id="30ac7-181">실제 쿼리는 보다 많은 행을 반환하지만 이 예제에서는 입력에 대해 제공된 정보 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-181">The actual query returns many more rows; however, this sample illustrates the type of information that is provided about the inputs.</span></span> <span data-ttu-id="30ac7-182">불연속 입력에 가능한 각 값은 테이블에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-182">For discrete inputs, each possible value is listed in the table.</span></span> <span data-ttu-id="30ac7-183">Age와 같은 연속 값 입력의 경우 전체를 나열하는 것이 가능하지 않으므로 입력이 평균값으로 불연속화됩니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-183">For continuous-value inputs such as Age, a complete listing is impossible, so the input is discretized as a mean.</span></span> <span data-ttu-id="30ac7-184">한계 통계 노드의 정보를 사용하는 방법에 대한 자세한 내용은 [로지스틱 회귀 분석 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-184">For more information about how to use the information in the marginal statistics node, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30ac7-185">이 결과는 보기 쉽도록 평면화되었지만 사용 중인 공급자가 계층적 행 집합을 지원하는 경우에는 중첩 테이블을 단일 열에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-185">The results have been flattened for easier viewing, but you can return the nested table in a single column if your provider supports hierarchical rowsets.</span></span>  
  
## <a name="prediction-queries-on-a-logistic-regression-model"></a><span data-ttu-id="30ac7-186">로지스틱 회귀 모델에 대한 예측 쿼리</span><span class="sxs-lookup"><span data-stu-id="30ac7-186">Prediction Queries on a Logistic Regression Model</span></span>  
 <span data-ttu-id="30ac7-187">모든 종류의 마이닝 모델에 [Predict&#40;DMX&#41;](/sql/dmx/predict-dmx) 함수를 사용하여 모델에 새 데이터를 제공하고 새 값을 기반으로 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-187">You can use the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function with every kind of mining model to provide new data to the model and make predictions based on the new values.</span></span> <span data-ttu-id="30ac7-188">함수를 사용하여 예측이 올바를 확률 등 예측에 대한 추가 정보를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-188">You can also use functions to return additional information about the prediction, such as the probability that a prediction is correct.</span></span> <span data-ttu-id="30ac7-189">이 섹션에서는 로지스틱 회귀 모델에 대한 예측 쿼리의 몇 가지 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-189">This section provides some examples of prediction queries on a logistic regression model.</span></span>  
  
###  <a name="sample-query-3-making-predictions-for-a-continuous-value"></a><a name="bkmk_Query3"></a><span data-ttu-id="30ac7-190">예제 쿼리 3: 연속 값에 대 한 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="30ac7-190">Sample Query 3: Making Predictions for a Continuous Value</span></span>  
 <span data-ttu-id="30ac7-191">로지스틱 회귀에서는 입력 및 예측 모두에 연속 특성을 사용할 수 있으므로 데이터에 포함된 다양한 요소와 상관 관계가 있는 모델을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-191">Because logistic regression supports the use of continuous attributes for both input and prediction, it is easy to create models that correlate various factors in your data.</span></span> <span data-ttu-id="30ac7-192">예측 쿼리를 사용하여 이러한 요소 간의 관계를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-192">You can use prediction queries to explore the relationship among these factors.</span></span>  
  
 <span data-ttu-id="30ac7-193">다음 예제 쿼리는 중급 자습서에서 만든 콜 센터 모델을 기반으로 하며 금요일 오전 근무조의 서비스 등급을 예측하는 단일 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-193">The following query sample is based on the Call Center model, from the Intermediate Tutorial, and creates a singleton query that predicts service grade for the Friday AM shift.</span></span> <span data-ttu-id="30ac7-194">[PredictHistogram(DMX)](/sql/dmx/predicthistogram-dmx) 함수는 예측 값의 유효성을 이해하는 데 관련된 통계를 제공하는 중첩 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-194">The [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) function returns a nested table that provides statistics relevant to understanding the validity of the predicted value.</span></span>  
  
```  
SELECT  
  Predict([Call Center_LR].[Service Grade]) as Predicted ServiceGrade,  
  PredictHistogram([Call Center_LR].[Service Grade]) as [Results],  
FROM  
  [Call Center_LR]  
NATURAL PREDICTION JOIN  
(SELECT 'Friday' AS [Day Of Week],  
  'AM' AS [Shift]) AS t  
```  
  
 <span data-ttu-id="30ac7-195">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="30ac7-195">Sample results:</span></span>  
  
 <span data-ttu-id="30ac7-196">**예측 된 서비스 등급**: 0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="30ac7-196">**Predicted Service Grade**: 0.102601830123659</span></span>  
  
 <span data-ttu-id="30ac7-197">**결과**</span><span class="sxs-lookup"><span data-stu-id="30ac7-197">**Results**</span></span>  
  
|<span data-ttu-id="30ac7-198">Service Grade</span><span class="sxs-lookup"><span data-stu-id="30ac7-198">Service Grade</span></span>|<span data-ttu-id="30ac7-199">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="30ac7-199">$SUPPORT</span></span>|<span data-ttu-id="30ac7-200">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="30ac7-200">$PROBABILITY</span></span>|<span data-ttu-id="30ac7-201">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="30ac7-201">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="30ac7-202">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="30ac7-202">$VARIANCE</span></span>|<span data-ttu-id="30ac7-203">$STDEV</span><span class="sxs-lookup"><span data-stu-id="30ac7-203">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="30ac7-204">0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="30ac7-204">0.102601830123659</span></span>|<span data-ttu-id="30ac7-205">83.0232558139535</span><span class="sxs-lookup"><span data-stu-id="30ac7-205">83.0232558139535</span></span>|<span data-ttu-id="30ac7-206">0.988372093023256</span><span class="sxs-lookup"><span data-stu-id="30ac7-206">0.988372093023256</span></span>|<span data-ttu-id="30ac7-207">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-207">0</span></span>|<span data-ttu-id="30ac7-208">0.00120552660600087</span><span class="sxs-lookup"><span data-stu-id="30ac7-208">0.00120552660600087</span></span>|<span data-ttu-id="30ac7-209">0.034720694203902</span><span class="sxs-lookup"><span data-stu-id="30ac7-209">0.034720694203902</span></span>|  
||<span data-ttu-id="30ac7-210">0.976744186046512</span><span class="sxs-lookup"><span data-stu-id="30ac7-210">0.976744186046512</span></span>|<span data-ttu-id="30ac7-211">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="30ac7-211">0.0116279069767442</span></span>|<span data-ttu-id="30ac7-212">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="30ac7-212">0.0116279069767442</span></span>|<span data-ttu-id="30ac7-213">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-213">0</span></span>|<span data-ttu-id="30ac7-214">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-214">0</span></span>|  
  
 <span data-ttu-id="30ac7-215">중첩 NODE_DISTRIBUTION 테이블의 확률, 지지도 및 표준 편차 값에 대한 자세한 내용은 [로지스틱 회귀 분석 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-215">For more information about the probability, support, and standard deviation values in the nested NODE_DISTRIBUTION table, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
###  <a name="sample-query-4-making-predictions-for-a-discrete-value"></a><a name="bkmk_Query4"></a><span data-ttu-id="30ac7-216">예제 쿼리 4: 불연속 값에 대 한 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="30ac7-216">Sample Query 4: Making Predictions for a Discrete Value</span></span>  
 <span data-ttu-id="30ac7-217">로지스틱 회귀는 일반적으로 이진 결과에 영향을 주는 요소를 분석하려는 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-217">Logistic regression is typically used in scenarios where you want to analyze the factors that contribute to a binary outcome.</span></span> <span data-ttu-id="30ac7-218">자습서에서 사용된 모델은 **ServiceGrade**라는 연속 값을 예측하지만, 실제 환경에서는 서비스 등급이 불연속화된 목표 값을 만족하는지 여부를 예측하도록 모델을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-218">Although the model used in the tutorial predicts a continuous value, **ServiceGrade**, in a real-life scenario you might want to set up the model to predict whether service grade met some discretized target value.</span></span> <span data-ttu-id="30ac7-219">또는 연속 값을 사용하여 예측을 출력한 후 나중에 예측된 출력을 **Good**, **Fair**또는 **Poor**로 그룹화하는 방법도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-219">Alternatively, you could output the predictions using a continuous value but later group the predicted outcomes into **Good**, **Fair**, or **Poor**.</span></span>  
  
 <span data-ttu-id="30ac7-220">다음 예제에서는 예측 가능한 특성의 그룹화 방식을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-220">The following sample illustrates how to change the way that the predictable attribute is grouped.</span></span> <span data-ttu-id="30ac7-221">이 작업은 마이닝 구조의 복사본을 만든 다음 값이 연속되는 대신 그룹화되도록 대상 열의 분할 방법을 변경하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-221">To do this, you create a copy of the mining structure and then change the discretization method of the target column so that the values are grouped rather than continuous.</span></span>  
  
 <span data-ttu-id="30ac7-222">다음 절차에서는 콜 센터 데이터에 있는 Service Grade 값의 그룹화를 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-222">The following procedure describes how to change the grouping of Service Grade values in the Call Center data.</span></span>  
  
##### <a name="to-create-a-discretized-version-of-the-call-center-mining-structure-and-models"></a><span data-ttu-id="30ac7-223">콜 센터 마이닝 구조 및 모델의 불연속 버전을 만들려면</span><span class="sxs-lookup"><span data-stu-id="30ac7-223">To create a discretized version of the Call Center mining structure and models</span></span>  
  
1.  <span data-ttu-id="30ac7-224">의 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 솔루션 탐색기에서 **마이닝 구조**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-224">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="30ac7-225">Call Center.dmm을 마우스 오른쪽 단추로 클릭하고 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-225">Right-click Call Center.dmm and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="30ac7-226">**마이닝 구조** 를 마우스 오른쪽 단추로 클릭하고 **붙여넣기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-226">Right click **Mining Structures** and select **Paste**.</span></span> <span data-ttu-id="30ac7-227">Call Center 1이라는 새 마이닝 구조가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-227">A new mining structure iss added, named Call Center 1.</span></span>  
  
4.  <span data-ttu-id="30ac7-228">새 마이닝 구조를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-228">Right-click the new mining structure and select **Rename**.</span></span> <span data-ttu-id="30ac7-229">**Call Center Discretized**라는 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-229">Type the new name, **Call Center Discretized**.</span></span>  
  
5.  <span data-ttu-id="30ac7-230">새 마이닝 구조를 두 번 클릭하여 디자이너에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-230">Double-click the new mining structure to open it in the designer.</span></span> <span data-ttu-id="30ac7-231">마이닝 모델까지 모두 복사되었으며 확장명은 모두 1입니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-231">Notice that the mining models have all been copied as well, and all have the extension 1.</span></span> <span data-ttu-id="30ac7-232">지금은 이름을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-232">Leave the names as is for now.</span></span>  
  
6.  <span data-ttu-id="30ac7-233">**마이닝 구조** 탭에서 Service Grade에 대한 열을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-233">In the **Mining Structure** tab, right-click the column for Service Grade, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="30ac7-234">속성을 `Content` **연속** 에서 **불연속화**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-234">Change the `Content` property from **Continuous** to **Discretized**.</span></span> <span data-ttu-id="30ac7-235">속성을 `DiscretizationMethod` **클러스터**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-235">Change the `DiscretizationMethod` property to **Clusters**.</span></span> <span data-ttu-id="30ac7-236">Discretization BucketCount에 **3**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-236">For Discretization BucketCount, type **3**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30ac7-237">이러한 매개 변수는 프로세스에 대한 이해를 돕기 위해 사용된 것일 뿐 이러한 매개 변수를 통해 유효한 모델이 반드시 생성되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-237">These parameters are just used for illustrating the process, and do not necessarily produce a valid model,</span></span>  
  
8.  <span data-ttu-id="30ac7-238">**마이닝 모델** 메뉴에서 **마이닝 구조 및 모든 모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-238">From the **Mining Model** menu, select **Process structure and all models**.</span></span>  
  
 <span data-ttu-id="30ac7-239">다음 예제 쿼리는 이 불연속 모델을 기반으로 하며 특정 요일의 서비스 등급 및 예측된 각 결과에 대한 확률을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-239">The following sample query is based on this discretized model, and predicts the service grade for the specified day of the week, together with the probabilities for each predicted outcome.</span></span>  
  
```  
SELECT  
  (PredictHistogram([Call Center_LR 1].[Service Grade])) as [Predictions]  
FROM  
  [Call Center_LR 1]  
NATURAL PREDICTION JOIN  
(SELECT 'Saturday' AS [Day Of Week]) AS t    
```  
  
 <span data-ttu-id="30ac7-240">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="30ac7-240">Expected results:</span></span>  
  
 <span data-ttu-id="30ac7-241">**예측**</span><span class="sxs-lookup"><span data-stu-id="30ac7-241">**Predictions**</span></span>  
  
|<span data-ttu-id="30ac7-242">Service Grade</span><span class="sxs-lookup"><span data-stu-id="30ac7-242">Service Grade</span></span>|<span data-ttu-id="30ac7-243">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="30ac7-243">$SUPPORT</span></span>|<span data-ttu-id="30ac7-244">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="30ac7-244">$PROBABILITY</span></span>|<span data-ttu-id="30ac7-245">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="30ac7-245">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="30ac7-246">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="30ac7-246">$VARIANCE</span></span>|<span data-ttu-id="30ac7-247">$STDEV</span><span class="sxs-lookup"><span data-stu-id="30ac7-247">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="30ac7-248">0.10872718383125</span><span class="sxs-lookup"><span data-stu-id="30ac7-248">0.10872718383125</span></span>|<span data-ttu-id="30ac7-249">35.7246504770641</span><span class="sxs-lookup"><span data-stu-id="30ac7-249">35.7246504770641</span></span>|<span data-ttu-id="30ac7-250">0.425293458060287</span><span class="sxs-lookup"><span data-stu-id="30ac7-250">0.425293458060287</span></span>|<span data-ttu-id="30ac7-251">0.0170168360030293</span><span class="sxs-lookup"><span data-stu-id="30ac7-251">0.0170168360030293</span></span>|<span data-ttu-id="30ac7-252">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-252">0</span></span>|<span data-ttu-id="30ac7-253">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-253">0</span></span>|  
|<span data-ttu-id="30ac7-254">0.05855769230625</span><span class="sxs-lookup"><span data-stu-id="30ac7-254">0.05855769230625</span></span>|<span data-ttu-id="30ac7-255">31.7098880800703</span><span class="sxs-lookup"><span data-stu-id="30ac7-255">31.7098880800703</span></span>|<span data-ttu-id="30ac7-256">0.377498667619885</span><span class="sxs-lookup"><span data-stu-id="30ac7-256">0.377498667619885</span></span>|<span data-ttu-id="30ac7-257">0.020882020060454</span><span class="sxs-lookup"><span data-stu-id="30ac7-257">0.020882020060454</span></span>|<span data-ttu-id="30ac7-258">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-258">0</span></span>|<span data-ttu-id="30ac7-259">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-259">0</span></span>|  
|<span data-ttu-id="30ac7-260">0.170169491525</span><span class="sxs-lookup"><span data-stu-id="30ac7-260">0.170169491525</span></span>|<span data-ttu-id="30ac7-261">15.6109159883202</span><span class="sxs-lookup"><span data-stu-id="30ac7-261">15.6109159883202</span></span>|<span data-ttu-id="30ac7-262">0.185844237956192</span><span class="sxs-lookup"><span data-stu-id="30ac7-262">0.185844237956192</span></span>|<span data-ttu-id="30ac7-263">0.0661386571386049</span><span class="sxs-lookup"><span data-stu-id="30ac7-263">0.0661386571386049</span></span>|<span data-ttu-id="30ac7-264">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-264">0</span></span>|<span data-ttu-id="30ac7-265">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-265">0</span></span>|  
||<span data-ttu-id="30ac7-266">0.954545454545455</span><span class="sxs-lookup"><span data-stu-id="30ac7-266">0.954545454545455</span></span>|<span data-ttu-id="30ac7-267">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="30ac7-267">0.0113636363636364</span></span>|<span data-ttu-id="30ac7-268">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="30ac7-268">0.0113636363636364</span></span>|<span data-ttu-id="30ac7-269">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-269">0</span></span>|<span data-ttu-id="30ac7-270">0</span><span class="sxs-lookup"><span data-stu-id="30ac7-270">0</span></span>|  
  
 <span data-ttu-id="30ac7-271">예측된 결과는 지정된 세 개의 범주별로 그룹화되었지만 이러한 그룹화는 사용자가 비즈니스 목표로 설정한 임의의 값이 아니라 데이터의 실제 값 집합을 기반으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-271">Note that the predicted outcomes have been grouped into three categories as specified; however, these groupings are based on the clustering of actual values in the data, not arbitrary values that you might set as business goals.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="30ac7-272">예측 함수 목록</span><span class="sxs-lookup"><span data-stu-id="30ac7-272">List of Prediction Functions</span></span>  
 <span data-ttu-id="30ac7-273">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-273">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="30ac7-274">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 로지스틱 회귀 알고리즘은 다음 표에 나열된 추가 함수도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-274">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30ac7-275">예측 함수</span><span class="sxs-lookup"><span data-stu-id="30ac7-275">Prediction Function</span></span>|<span data-ttu-id="30ac7-276">사용</span><span class="sxs-lookup"><span data-stu-id="30ac7-276">Usage</span></span>|  
|[<span data-ttu-id="30ac7-277">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-277">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="30ac7-278">한 노드가 모델에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-278">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="30ac7-279">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-279">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="30ac7-280">지정한 상태에 대한 조정된 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-280">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="30ac7-281">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-281">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="30ac7-282">지정한 열에 대한 예측 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-282">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="30ac7-283">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-283">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="30ac7-284">지정한 상태에 대한 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-284">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="30ac7-285">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-285">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="30ac7-286">예측 값의 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-286">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="30ac7-287">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-287">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="30ac7-288">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-288">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="30ac7-289">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-289">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="30ac7-290">지정한 열의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-290">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="30ac7-291">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘에 공통된 함수 목록은 [일반 예측 함수&#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-291">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="30ac7-292">특정 함수의 구문은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30ac7-292">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30ac7-293">신경망 및 로지스틱 회귀 모델의 경우 [PredictSupport&#40;DMX&#41;](/sql/dmx/predictsupport-dmx) 함수는 모델 전체에 대한 학습 집합의 크기를 나타내는 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30ac7-293">For neural network and logistic regression models, the [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) function returns a single value that represents the size of the training set for the entire model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ac7-294">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30ac7-294">See Also</span></span>  
 <span data-ttu-id="30ac7-295">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="30ac7-295">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="30ac7-296">[Microsoft 로지스틱 회귀 알고리즘](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="30ac7-296">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="30ac7-297">[Microsoft 로지스틱 회귀 알고리즘 기술 참조](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="30ac7-297">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="30ac7-298">[로지스틱 회귀 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="30ac7-298">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 [<span data-ttu-id="30ac7-299">5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="30ac7-299">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
