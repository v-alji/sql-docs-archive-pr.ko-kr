---
title: Naive Bayes Model 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- naive bayes algorithms [Analysis Services]
- content queries [DMX]
ms.assetid: e642bd7d-5afa-4dfb-8cca-4f84aadf61b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9694826bf2f74daef7b6d024e51e31d4ee448671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728959"
---
# <a name="naive-bayes-model-query-examples"></a><span data-ttu-id="4e3fb-102">Naive Bayes 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="4e3fb-102">Naive Bayes Model Query Examples</span></span>
  <span data-ttu-id="4e3fb-103">데이터 마이닝 모델에 대한 쿼리를 작성할 때 분석 중에 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 작성하거나, 모델의 패턴을 사용하여 새 데이터에 대한 예측을 만드는 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="4e3fb-104">데이터 마이닝 스키마 행 집합에 대한 쿼리를 사용하여 모델에 대한 메타데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-104">You can also retrieve metadata about the model by using a query against the data mining schema rowset.</span></span> <span data-ttu-id="4e3fb-105">이 섹션에서는 Microsoft Naive Bayes 알고리즘을 기반으로 하는 모델에 대해 이러한 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-105">This section explains how to create these queries for models that are based on the Microsoft Naive Bayes algorithm.</span></span>  
  
 <span data-ttu-id="4e3fb-106">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="4e3fb-106">**Content Queries**</span></span>  
  
 [<span data-ttu-id="4e3fb-107">DMX를 사용 하 여 모델 메타 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-107">Getting model metadata by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="4e3fb-108">학습 데이터의 요약 검색</span><span class="sxs-lookup"><span data-stu-id="4e3fb-108">Retrieving a summary of training data</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="4e3fb-109">특성에 대한 추가 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-109">Finding more information about attributes</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="4e3fb-110">시스템 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="4e3fb-110">Using system stored procedures</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="4e3fb-111">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="4e3fb-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="4e3fb-112">단일 쿼리를 사용하여 결과 예측</span><span class="sxs-lookup"><span data-stu-id="4e3fb-112">Predicting outcomes using a singleton query</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="4e3fb-113">확률 및 지지도 값과 함께 예측 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-113">Getting predictions with probability and support values</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="4e3fb-114">연결 예측</span><span class="sxs-lookup"><span data-stu-id="4e3fb-114">Predicting associations</span></span>](#bkmk_Query7)  
  
## <a name="finding-information-about-a-naive-bayes-model"></a><span data-ttu-id="4e3fb-115">Naive Bayes 모델에 대한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-115">Finding Information about a Naive Bayes Model</span></span>  
 <span data-ttu-id="4e3fb-116">Naive Bayes 모델의 모델 콘텐츠는 학습 데이터의 값 분포에 대한 집계 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-116">The model content of a Naive Bayes model provides aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="4e3fb-117">데이터 마이닝 스키마 행 집합에 대한 쿼리를 만들어 모델의 메타데이터에 대한 정보를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-117">You can also retrieve information about the metadata of the model by creating queries against the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="4e3fb-118">예제 쿼리 1: DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="4e3fb-119">데이터 마이닝 스키마 행 집합을 쿼리하면 모델에 대한 메타데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-119">By querying the data mining schema rowset, you can find metadata for the model.</span></span> <span data-ttu-id="4e3fb-120">이러한 메타데이터로는 모델이 만들어진 시기, 모델이 마지막으로 처리된 시기, 모델의 기반이 되는 마이닝 구조의 이름, 예측 가능한 특성으로 사용된 열 이름 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-120">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the columns used as the predictable attribute.</span></span> <span data-ttu-id="4e3fb-121">모델을 만들 때 사용된 매개 변수를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-121">You can also return the parameters that were used when the model was created.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, DATE_CREATED, LAST_PROCESSED,  
SERVICE_NAME, PREDICTION_ENTITY, FILTER  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_NaiveBayes_Filtered'  
```  
  
 <span data-ttu-id="4e3fb-122">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-122">Sample results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e3fb-123">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4e3fb-123">MODEL_CATALOG</span></span>|<span data-ttu-id="4e3fb-124">AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="4e3fb-124">AdventureWorks</span></span>|  
|<span data-ttu-id="4e3fb-125">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-125">MODEL_NAME</span></span>|<span data-ttu-id="4e3fb-126">TM_NaiveBayes_Filtered</span><span class="sxs-lookup"><span data-stu-id="4e3fb-126">TM_NaiveBayes_Filtered</span></span>|  
|<span data-ttu-id="4e3fb-127">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4e3fb-127">DATE_CREATED</span></span>|<span data-ttu-id="4e3fb-128">3/1/2008 19:15</span><span class="sxs-lookup"><span data-stu-id="4e3fb-128">3/1/2008 19:15</span></span>|  
|<span data-ttu-id="4e3fb-129">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="4e3fb-129">LAST_PROCESSED</span></span>|<span data-ttu-id="4e3fb-130">3/2/2008 20:00</span><span class="sxs-lookup"><span data-stu-id="4e3fb-130">3/2/2008 20:00</span></span>|  
|<span data-ttu-id="4e3fb-131">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-131">SERVICE_NAME</span></span>|<span data-ttu-id="4e3fb-132">Microsoft_Naive_Bayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-132">Microsoft_Naive_Bayes</span></span>|  
|<span data-ttu-id="4e3fb-133">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="4e3fb-133">PREDICTION_ENTITY</span></span>|<span data-ttu-id="4e3fb-134">Bike Buyer,Yearly Income</span><span class="sxs-lookup"><span data-stu-id="4e3fb-134">Bike Buyer,Yearly Income</span></span>|  
|<span data-ttu-id="4e3fb-135">FILTER</span><span class="sxs-lookup"><span data-stu-id="4e3fb-135">FILTER</span></span>|<span data-ttu-id="4e3fb-136">[Region] = 'Europe' OR [Region] = 'North America'</span><span class="sxs-lookup"><span data-stu-id="4e3fb-136">[Region] = 'Europe' OR [Region] = 'North America'</span></span>|  
  
 <span data-ttu-id="4e3fb-137">이 예에 사용된 모델은 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)에서 만드는 Naive Bayes 모델을 기반으로 하되 여기에 두 번째 예측 가능한 특성을 추가하고 학습 데이터에 필터를 적용하여 수정한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-137">The model used for this example is based on the Naive Bayes model you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md), but was modified by adding a second predictable attribute and applying a filter to the training data.</span></span>  
  
###  <a name="sample-query-2-retrieving-a-summary-of-training-data"></a><a name="bkmk_Query2"></a> <span data-ttu-id="4e3fb-138">예제 쿼리 2: 학습 데이터의 요약 검색</span><span class="sxs-lookup"><span data-stu-id="4e3fb-138">Sample Query 2: Retrieving a Summary of Training Data</span></span>  
 <span data-ttu-id="4e3fb-139">Naive Bayes 모델에서 한계 통계 노드에는 학습 데이터의 값 분포에 대한 집계 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-139">In a Naive Bayes model, the marginal statistics node stores aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="4e3fb-140">따라서 이와 같은 요약 정보를 찾기 위해 학습 데이터에 대한 SQL 쿼리를 만들지 않아도 되므로 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-140">This summary is convenient and saves you from having to create SQL queries against the training data to find the same information.</span></span>  
  
 <span data-ttu-id="4e3fb-141">다음 예에서는 DMX 내용 쿼리를 사용하여 노드(NODE_TYPE = 24)에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-141">The following example uses a DMX content query to retrieve the data from the node (NODE_TYPE = 24).</span></span> <span data-ttu-id="4e3fb-142">통계는 중첩 테이블에 저장되어 있으므로 결과를 보기 쉽게 만들기 위해 FLATTENED 키워드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-142">Because the statistics are stored in a nested table, the FLATTENED keyword is used to make the results easier to view.</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE FROM NODE_DISTRIBUTION) AS t  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4e3fb-143">SUPPORT 및 PROBABILITY 열의 이름을 대괄호로 묶어 동일한 이름의 MDX(Multidimensional Expressions) 예약 키워드와 구별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-143">You must enclose the name of the columns, SUPPORT and PROBABILITY, in brackets to distinguish them from the Multidimensional Expressions (MDX) reserved keywords of the same names.</span></span>  
  
 <span data-ttu-id="4e3fb-144">일부 결과:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-144">Partial results:</span></span>  
  
|<span data-ttu-id="4e3fb-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-145">MODEL_NAME</span></span>|<span data-ttu-id="4e3fb-146">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-146">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="4e3fb-147">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-147">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="4e3fb-148">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="4e3fb-148">t.SUPPORT</span></span>|<span data-ttu-id="4e3fb-149">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4e3fb-149">t.PROBABILITY</span></span>|<span data-ttu-id="4e3fb-150">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-150">t.VALUETYPE</span></span>|  
|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="4e3fb-151">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-151">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-152">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4e3fb-152">Bike Buyer</span></span>|<span data-ttu-id="4e3fb-153">Missing</span><span class="sxs-lookup"><span data-stu-id="4e3fb-153">Missing</span></span>|<span data-ttu-id="4e3fb-154">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-154">0</span></span>|<span data-ttu-id="4e3fb-155">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-155">0</span></span>|<span data-ttu-id="4e3fb-156">1</span><span class="sxs-lookup"><span data-stu-id="4e3fb-156">1</span></span>|  
|<span data-ttu-id="4e3fb-157">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-157">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-158">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4e3fb-158">Bike Buyer</span></span>|<span data-ttu-id="4e3fb-159">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-159">0</span></span>|<span data-ttu-id="4e3fb-160">8869</span><span class="sxs-lookup"><span data-stu-id="4e3fb-160">8869</span></span>|<span data-ttu-id="4e3fb-161">0.507263784</span><span class="sxs-lookup"><span data-stu-id="4e3fb-161">0.507263784</span></span>|<span data-ttu-id="4e3fb-162">4</span><span class="sxs-lookup"><span data-stu-id="4e3fb-162">4</span></span>|  
|<span data-ttu-id="4e3fb-163">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-163">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-164">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4e3fb-164">Bike Buyer</span></span>|<span data-ttu-id="4e3fb-165">1</span><span class="sxs-lookup"><span data-stu-id="4e3fb-165">1</span></span>|<span data-ttu-id="4e3fb-166">8615</span><span class="sxs-lookup"><span data-stu-id="4e3fb-166">8615</span></span>|<span data-ttu-id="4e3fb-167">0.492736216</span><span class="sxs-lookup"><span data-stu-id="4e3fb-167">0.492736216</span></span>|<span data-ttu-id="4e3fb-168">4</span><span class="sxs-lookup"><span data-stu-id="4e3fb-168">4</span></span>|  
|<span data-ttu-id="4e3fb-169">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-169">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-170">성별</span><span class="sxs-lookup"><span data-stu-id="4e3fb-170">Gender</span></span>|<span data-ttu-id="4e3fb-171">Missing</span><span class="sxs-lookup"><span data-stu-id="4e3fb-171">Missing</span></span>|<span data-ttu-id="4e3fb-172">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-172">0</span></span>|<span data-ttu-id="4e3fb-173">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-173">0</span></span>|<span data-ttu-id="4e3fb-174">1</span><span class="sxs-lookup"><span data-stu-id="4e3fb-174">1</span></span>|  
|<span data-ttu-id="4e3fb-175">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-175">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-176">성별</span><span class="sxs-lookup"><span data-stu-id="4e3fb-176">Gender</span></span>|<span data-ttu-id="4e3fb-177">F</span><span class="sxs-lookup"><span data-stu-id="4e3fb-177">F</span></span>|<span data-ttu-id="4e3fb-178">8656</span><span class="sxs-lookup"><span data-stu-id="4e3fb-178">8656</span></span>|<span data-ttu-id="4e3fb-179">0.495081217</span><span class="sxs-lookup"><span data-stu-id="4e3fb-179">0.495081217</span></span>|<span data-ttu-id="4e3fb-180">4</span><span class="sxs-lookup"><span data-stu-id="4e3fb-180">4</span></span>|  
|<span data-ttu-id="4e3fb-181">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="4e3fb-181">TM_NaiveBayes</span></span>|<span data-ttu-id="4e3fb-182">성별</span><span class="sxs-lookup"><span data-stu-id="4e3fb-182">Gender</span></span>|<span data-ttu-id="4e3fb-183">M</span><span class="sxs-lookup"><span data-stu-id="4e3fb-183">M</span></span>|<span data-ttu-id="4e3fb-184">8828</span><span class="sxs-lookup"><span data-stu-id="4e3fb-184">8828</span></span>|<span data-ttu-id="4e3fb-185">0.504918783</span><span class="sxs-lookup"><span data-stu-id="4e3fb-185">0.504918783</span></span>|<span data-ttu-id="4e3fb-186">4</span><span class="sxs-lookup"><span data-stu-id="4e3fb-186">4</span></span>|  
  
 <span data-ttu-id="4e3fb-187">예를 들어 이러한 결과는 누락 값(VALUETYPE = 1)에 대해 조정된 계산된 확률과 함께 각 불연속 값(VALUETYPE = 4)의 학습 사례 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-187">For example, these results tell you the number of training cases for each discrete value (VALUETYPE = 4), together with the computed probability, adjusted for missing values (VALUETYPE = 1).</span></span>  
  
 <span data-ttu-id="4e3fb-188">Naive Bayes 모델의 NODE_DISTRIBUTION 테이블에 제공되는 값에 대한 정의는 [Naive Bayes 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-188">For a definition of the values provided in the NODE_DISTRIBUTION table in a Naive Bayes model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span> <span data-ttu-id="4e3fb-189">누락 값이 지지도 및 확률 계산에 주는 영향에 대한 자세한 내용은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-189">For more information about how support and probability calculations are affected by missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-finding-more-information-about-attributes"></a><a name="bkmk_Query3"></a> <span data-ttu-id="4e3fb-190">예제 쿼리 3: 특성에 대한 추가 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-190">Sample Query 3: Finding More Information about Attributes</span></span>  
 <span data-ttu-id="4e3fb-191">Naive Bayes 모델에는 서로 다른 특성 간의 관계에 대한 복잡한 정보가 들어 있는 경우도 있으므로 이러한 관계를 가장 쉽게 보는 방법은 [Microsoft Naive Bayes 뷰어](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-191">Because a Naive Bayes model often contains complex information about the relationships among different attributes, the easiest way to view these relationships is to use the [Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span> <span data-ttu-id="4e3fb-192">그러나 DMX 쿼리를 만들어 데이터를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-192">However, you can create DMX queries to return the data.</span></span>  
  
 <span data-ttu-id="4e3fb-193">다음 예에서는 모델에서 특정 특성 `Region`에 대한 정보를 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-193">The following example shows how to return information from the model about a particular attribute, `Region`.</span></span>  
  
```  
SELECT NODE_TYPE, NODE_CAPTION,   
NODE_PROBABILITY, NODE_SUPPORT, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE ATTRIBUTE_NAME = 'Region'  
```  
  
 <span data-ttu-id="4e3fb-194">이 쿼리는 두 가지 유형의 노드를 반환합니다. 한 노드(NODE_TYPE = 10)는 입력 특성을 나타내고 다른 노드(NODE_TYPE = 11)는 특성의 각 값에 대한 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-194">This query returns two types of nodes: the node that represents the input attribute (NODE_TYPE = 10), and nodes for each value of the attribute (NODE_TYPE = 11).</span></span> <span data-ttu-id="4e3fb-195">노드 캡션에는 특성 이름과 특성 값이 모두 표시되므로 노드 이름 대신 노드 캡션이 노드를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-195">The node caption is used to identify the node, rather than the node name, because the caption shows both the attribute name and attribute value.</span></span>  
  
|<span data-ttu-id="4e3fb-196">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-196">NODE_TYPE</span></span>|<span data-ttu-id="4e3fb-197">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="4e3fb-197">NODE_CAPTION</span></span>|<span data-ttu-id="4e3fb-198">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4e3fb-198">NODE_PROBABILITY</span></span>|<span data-ttu-id="4e3fb-199">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="4e3fb-199">NODE_SUPPORT</span></span>|<span data-ttu-id="4e3fb-200">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-200">MSOLAP_NODE_SCORE</span></span>|<span data-ttu-id="4e3fb-201">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-201">NODE_TYPE</span></span>|  
|----------------|-------------------|-----------------------|-------------------|-------------------------|----------------|  
|<span data-ttu-id="4e3fb-202">10</span><span class="sxs-lookup"><span data-stu-id="4e3fb-202">10</span></span>|<span data-ttu-id="4e3fb-203">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="4e3fb-203">Bike Buyer -> Region</span></span>|<span data-ttu-id="4e3fb-204">1</span><span class="sxs-lookup"><span data-stu-id="4e3fb-204">1</span></span>|<span data-ttu-id="4e3fb-205">17484</span><span class="sxs-lookup"><span data-stu-id="4e3fb-205">17484</span></span>|<span data-ttu-id="4e3fb-206">84.51555875</span><span class="sxs-lookup"><span data-stu-id="4e3fb-206">84.51555875</span></span>|<span data-ttu-id="4e3fb-207">10</span><span class="sxs-lookup"><span data-stu-id="4e3fb-207">10</span></span>|  
|<span data-ttu-id="4e3fb-208">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-208">11</span></span>|<span data-ttu-id="4e3fb-209">Bike Buyer -> Region = Missing</span><span class="sxs-lookup"><span data-stu-id="4e3fb-209">Bike Buyer -> Region = Missing</span></span>|<span data-ttu-id="4e3fb-210">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-210">0</span></span>|<span data-ttu-id="4e3fb-211">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-211">0</span></span>|<span data-ttu-id="4e3fb-212">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-212">0</span></span>|<span data-ttu-id="4e3fb-213">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-213">11</span></span>|  
|<span data-ttu-id="4e3fb-214">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-214">11</span></span>|<span data-ttu-id="4e3fb-215">Bike Buyer -> Region = North America</span><span class="sxs-lookup"><span data-stu-id="4e3fb-215">Bike Buyer -> Region = North America</span></span>|<span data-ttu-id="4e3fb-216">0.508236102</span><span class="sxs-lookup"><span data-stu-id="4e3fb-216">0.508236102</span></span>|<span data-ttu-id="4e3fb-217">8886</span><span class="sxs-lookup"><span data-stu-id="4e3fb-217">8886</span></span>|<span data-ttu-id="4e3fb-218">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-218">0</span></span>|<span data-ttu-id="4e3fb-219">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-219">11</span></span>|  
|<span data-ttu-id="4e3fb-220">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-220">11</span></span>|<span data-ttu-id="4e3fb-221">Bike Buyer -> Region = Pacific</span><span class="sxs-lookup"><span data-stu-id="4e3fb-221">Bike Buyer -> Region = Pacific</span></span>|<span data-ttu-id="4e3fb-222">0.193891558</span><span class="sxs-lookup"><span data-stu-id="4e3fb-222">0.193891558</span></span>|<span data-ttu-id="4e3fb-223">3390</span><span class="sxs-lookup"><span data-stu-id="4e3fb-223">3390</span></span>|<span data-ttu-id="4e3fb-224">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-224">0</span></span>|<span data-ttu-id="4e3fb-225">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-225">11</span></span>|  
|<span data-ttu-id="4e3fb-226">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-226">11</span></span>|<span data-ttu-id="4e3fb-227">Bike Buyer -> Region = Europe</span><span class="sxs-lookup"><span data-stu-id="4e3fb-227">Bike Buyer -> Region = Europe</span></span>|<span data-ttu-id="4e3fb-228">0.29787234</span><span class="sxs-lookup"><span data-stu-id="4e3fb-228">0.29787234</span></span>|<span data-ttu-id="4e3fb-229">5208</span><span class="sxs-lookup"><span data-stu-id="4e3fb-229">5208</span></span>|<span data-ttu-id="4e3fb-230">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-230">0</span></span>|<span data-ttu-id="4e3fb-231">11</span><span class="sxs-lookup"><span data-stu-id="4e3fb-231">11</span></span>|  
  
 <span data-ttu-id="4e3fb-232">노드에 저장된 노드 확률 점수 및 노드 지지도 값 등의 일부 열은 한계 통계 노드에서 가져올 수 있는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-232">Some of the columns stored in the nodes are the same that you can get from the marginal statistics nodes, such as the node probability score and the node support values.</span></span> <span data-ttu-id="4e3fb-233">그러나 MSOLAP_NODE_SCORE는 입력 특성 노드에 대해서만 제공되는 특수 값이며 모델에서 이 특성의 상대적 중요도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-233">However, the MSOLAP_NODE_SCORE is a special value provided only for the input attribute nodes, and indicates the relative importance of this attribute in the model.</span></span> <span data-ttu-id="4e3fb-234">뷰어의 종속성 네트워크 창에서도 동일한 정보를 볼 수 있지만 뷰어에는 점수가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-234">You can see much the same information in the Dependency Network pane of the viewer; however, the viewer does not provide scores.</span></span>  
  
 <span data-ttu-id="4e3fb-235">다음 쿼리는 모델에 있는 모든 특성의 중요도 점수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-235">The following query returns the importance scores of all attributes in the model:</span></span>  
  
```  
SELECT NODE_CAPTION, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
ORDER BY MSOLAP_NODE_SCORE DESC  
```  
  
 <span data-ttu-id="4e3fb-236">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-236">Sample results:</span></span>  
  
|<span data-ttu-id="4e3fb-237">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="4e3fb-237">NODE_CAPTION</span></span>|<span data-ttu-id="4e3fb-238">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-238">MSOLAP_NODE_SCORE</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="4e3fb-239">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="4e3fb-239">Bike Buyer -> Total Children</span></span>|<span data-ttu-id="4e3fb-240">181.3654836</span><span class="sxs-lookup"><span data-stu-id="4e3fb-240">181.3654836</span></span>|  
|<span data-ttu-id="4e3fb-241">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="4e3fb-241">Bike Buyer -> Commute Distance</span></span>|<span data-ttu-id="4e3fb-242">179.8419482</span><span class="sxs-lookup"><span data-stu-id="4e3fb-242">179.8419482</span></span>|  
|<span data-ttu-id="4e3fb-243">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="4e3fb-243">Bike Buyer -> English Education</span></span>|<span data-ttu-id="4e3fb-244">156.9841928</span><span class="sxs-lookup"><span data-stu-id="4e3fb-244">156.9841928</span></span>|  
|<span data-ttu-id="4e3fb-245">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="4e3fb-245">Bike Buyer -> Number Children At Home</span></span>|<span data-ttu-id="4e3fb-246">111.8122599</span><span class="sxs-lookup"><span data-stu-id="4e3fb-246">111.8122599</span></span>|  
|<span data-ttu-id="4e3fb-247">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="4e3fb-247">Bike Buyer -> Region</span></span>|<span data-ttu-id="4e3fb-248">84.51555875</span><span class="sxs-lookup"><span data-stu-id="4e3fb-248">84.51555875</span></span>|  
|<span data-ttu-id="4e3fb-249">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="4e3fb-249">Bike Buyer -> Marital Status</span></span>|<span data-ttu-id="4e3fb-250">23.13297354</span><span class="sxs-lookup"><span data-stu-id="4e3fb-250">23.13297354</span></span>|  
|<span data-ttu-id="4e3fb-251">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="4e3fb-251">Bike Buyer -> English Occupation</span></span>|<span data-ttu-id="4e3fb-252">2.832069191</span><span class="sxs-lookup"><span data-stu-id="4e3fb-252">2.832069191</span></span>|  
  
 <span data-ttu-id="4e3fb-253">[Microsoft 일반 콘텐츠 트리 뷰어](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)에서 모델 콘텐츠를 찾아보면 주목할 만한 통계를 보다 잘 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-253">By browsing the model content in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md), you will get a better idea of what statistics might be interesting.</span></span> <span data-ttu-id="4e3fb-254">여기에서는 몇 개의 간단한 예를 보여 주지만 여러 쿼리를 실행하거나 결과를 저장하고 클라이언트에서 처리해야 하는 경우는 보다 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-254">Some simple examples were demonstrated here; more often you may need to execute multiple queries or store the results and process them on the client.</span></span>  
  
###  <a name="sample-query-4-using-system-stored-procedures"></a><a name="bkmk_Query4"></a> <span data-ttu-id="4e3fb-255">예제 쿼리 4: 시스템 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="4e3fb-255">Sample Query 4: Using System Stored Procedures</span></span>  
 <span data-ttu-id="4e3fb-256">사용자가 직접 내용 쿼리를 작성할 수 있을 뿐 아니라 몇 가지 Analysis Services 시스템 저장 프로시저를 사용하여 결과를 탐색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-256">In addition to writing your own content queries, you can use some Analysis Services system stored procedures to explore the results.</span></span> <span data-ttu-id="4e3fb-257">시스템 저장 프로시저를 사용하려면 저장 프로시저 이름 앞에 CALL 키워드를 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-257">To use a system stored procedure, prefix the stored procedure name with the CALL keyword:</span></span>  
  
```  
CALL GetPredictableAttributes ('TM_NaiveBayes')  
```  
  
 <span data-ttu-id="4e3fb-258">일부 결과:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-258">Partial results:</span></span>  
  
|<span data-ttu-id="4e3fb-259">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-259">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="4e3fb-260">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="4e3fb-260">NODE_UNIQUE_NAME</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="4e3fb-261">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4e3fb-261">Bike Buyer</span></span>|<span data-ttu-id="4e3fb-262">100000001</span><span class="sxs-lookup"><span data-stu-id="4e3fb-262">100000001</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4e3fb-263">이러한 시스템 저장 프로시저는 Analysis Services 서버와 클라이언트 간의 내부 통신을 위한 것으로서, 마이닝 모델을 개발하고 테스트할 때 편의를 위해서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-263">These system stored procedures are for internal communication between the Analysis Services server and the client and should only be used for convenience when developing and testing mining models.</span></span> <span data-ttu-id="4e3fb-264">프로덕션 시스템에 대한 쿼리를 만들 때는 항상 DMX를 사용하여 사용자가 직접 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-264">When you create queries for a production system, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="4e3fb-265">Analysis Services 시스템 저장 프로시저에 대한 자세한 내용은 [데이터 마이닝 저장 프로시저&#40;Analysis Services - 데이터 마이닝&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-265">For more information about Analysis Services system stored procedures, see [Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).</span></span>  
  
## <a name="using-a-naive-bayes-model-to-make-predictions"></a><span data-ttu-id="4e3fb-266">Naive Bayes 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-266">Using a Naive Bayes Model to Make Predictions</span></span>  
 <span data-ttu-id="4e3fb-267">Microsoft Naive Bayes 알고리즘은 일반적으로 예측에 사용되는 경우보다 입력 및 예측 가능한 특성 간의 관계를 탐색하는 데 사용되는 경우가 더 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-267">The Microsoft Naive Bayes algorithm is typically used less for prediction than it is for exploration of relationships among the input and predictable attributes.</span></span> <span data-ttu-id="4e3fb-268">그러나 이 모델에서는 예측 및 연결 모두에 대해 예측 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-268">However, the model supports the use of prediction functions for both prediction and association.</span></span>  
  
###  <a name="sample-query-5-predicting-outcomes-using-a-singleton-query"></a><a name="bkmk_Query5"></a> <span data-ttu-id="4e3fb-269">예제 쿼리 5: 단일 쿼리를 사용하여 결과 예측</span><span class="sxs-lookup"><span data-stu-id="4e3fb-269">Sample Query 5: Predicting Outcomes using a Singleton Query</span></span>  
 <span data-ttu-id="4e3fb-270">다음 쿼리에서는 단일 쿼리를 사용하여 새 값을 제공하고 모델을 기반으로 해당 특성을 갖는 고객이 자전거를 구입할 가능성이 있는지를 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-270">The following query uses a singleton query to provide a new value and predict, based on the model, whether a customer with these characteristics is likely to buy a bike.</span></span> <span data-ttu-id="4e3fb-271">회귀 모델에서 단일 쿼리를 만드는 가장 쉬운 방법은 **단일 쿼리 입력** 대화 상자를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-271">The easiest way to create a singleton query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="4e3fb-272">예를 들어 `TM_NaiveBayes` 모델을 선택하고 **단일 쿼리**를 선택한 다음 드롭다운 목록에서 `[Commute Distance]` 및 `Gender`의 값을 선택하여 다음과 같은 DMX 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-272">For example, you can build the following DMX query by selecting the `TM_NaiveBayes` model, choosing **Singleton Query**, and selecting values from the dropdown lists for `[Commute Distance]` and `Gender`.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="4e3fb-273">결과 예:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-273">Example results:</span></span>  
  
|<span data-ttu-id="4e3fb-274">식</span><span class="sxs-lookup"><span data-stu-id="4e3fb-274">Expression</span></span>|  
|----------------|  
|<span data-ttu-id="4e3fb-275">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-275">0</span></span>|  
  
 <span data-ttu-id="4e3fb-276">이 예측 함수는 가장 가능성이 높은 값(이 경우 0)을 반환합니다. 이 값은 이 유형의 고객이 자전거를 구입할 가능성이 없다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-276">The prediction function returns the most likely value, in this case, 0, which means this type of customer is unlikely to purchase a bike.</span></span>  
  
###  <a name="sample-query-6-getting-predictions-with-probability-and-support-values"></a><a name="bkmk_Query6"></a><span data-ttu-id="4e3fb-277">예제 쿼리 6: 확률 및 지원 값으로 예측 가져오기</span><span class="sxs-lookup"><span data-stu-id="4e3fb-277">Sample Query 6: Getting Predictions with Probability and Support Values</span></span>  
 <span data-ttu-id="4e3fb-278">결과를 예측하는 것 외에도 예측의 정확도를 알고 싶은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-278">In addition to predicting an outcome, you often want to know how strong the prediction is.</span></span> <span data-ttu-id="4e3fb-279">다음 쿼리에서는 앞의 예와 동일한 단일 쿼리를 사용하되 예측 함수 [PredictHistogram&#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)을 추가하여 해당 예측을 지원하는 통계가 들어 있는 중첩 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-279">The following query uses the same singleton query as the previous example, but adds the prediction function, [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), to return a nested table that contains statistics in support of the prediction.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer]),  
  PredictHistogram([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="4e3fb-280">결과 예:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-280">Example results:</span></span>  
  
|<span data-ttu-id="4e3fb-281">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4e3fb-281">Bike Buyer</span></span>|<span data-ttu-id="4e3fb-282">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="4e3fb-282">$SUPPORT</span></span>|<span data-ttu-id="4e3fb-283">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4e3fb-283">$PROBABILITY</span></span>|<span data-ttu-id="4e3fb-284">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4e3fb-284">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="4e3fb-285">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="4e3fb-285">$VARIANCE</span></span>|<span data-ttu-id="4e3fb-286">$STDEV</span><span class="sxs-lookup"><span data-stu-id="4e3fb-286">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="4e3fb-287">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-287">0</span></span>|<span data-ttu-id="4e3fb-288">10161.5714</span><span class="sxs-lookup"><span data-stu-id="4e3fb-288">10161.5714</span></span>|<span data-ttu-id="4e3fb-289">0.581192599</span><span class="sxs-lookup"><span data-stu-id="4e3fb-289">0.581192599</span></span>|<span data-ttu-id="4e3fb-290">0.010530981</span><span class="sxs-lookup"><span data-stu-id="4e3fb-290">0.010530981</span></span>|<span data-ttu-id="4e3fb-291">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-291">0</span></span>|<span data-ttu-id="4e3fb-292">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-292">0</span></span>|  
|<span data-ttu-id="4e3fb-293">1</span><span class="sxs-lookup"><span data-stu-id="4e3fb-293">1</span></span>|<span data-ttu-id="4e3fb-294">7321.428768</span><span class="sxs-lookup"><span data-stu-id="4e3fb-294">7321.428768</span></span>|<span data-ttu-id="4e3fb-295">0.418750215</span><span class="sxs-lookup"><span data-stu-id="4e3fb-295">0.418750215</span></span>|<span data-ttu-id="4e3fb-296">0.008945684</span><span class="sxs-lookup"><span data-stu-id="4e3fb-296">0.008945684</span></span>|<span data-ttu-id="4e3fb-297">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-297">0</span></span>|<span data-ttu-id="4e3fb-298">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-298">0</span></span>|  
||<span data-ttu-id="4e3fb-299">0.999828444</span><span class="sxs-lookup"><span data-stu-id="4e3fb-299">0.999828444</span></span>|<span data-ttu-id="4e3fb-300">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="4e3fb-300">5.72E-05</span></span>|<span data-ttu-id="4e3fb-301">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="4e3fb-301">5.72E-05</span></span>|<span data-ttu-id="4e3fb-302">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-302">0</span></span>|<span data-ttu-id="4e3fb-303">0</span><span class="sxs-lookup"><span data-stu-id="4e3fb-303">0</span></span>|  
  
 <span data-ttu-id="4e3fb-304">표의 마지막 행에서는 누락 값의 지지도 및 확률에 대한 조정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-304">The final row in the table shows the adjustments to support and probability for the missing value.</span></span> <span data-ttu-id="4e3fb-305">분산 및 표준 편차 값은 항상 0이지만 Naive Bayes 모델에서는 연속 값을 모델링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-305">Variance and standard deviation values are always 0, because Naive Bayes models cannot model continuous values.</span></span>  
  
###  <a name="sample-query-7-predicting-associations"></a><a name="bkmk_Query7"></a><span data-ttu-id="4e3fb-306">예제 쿼리 7: 연결 예측</span><span class="sxs-lookup"><span data-stu-id="4e3fb-306">Sample Query 7: Predicting Associations</span></span>  
 <span data-ttu-id="4e3fb-307">마이닝 구조에 예측 가능한 특성을 키로 사용하는 중첩 테이블이 들어 있는 경우 연결 분석에 Microsoft Naive Bayes 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-307">The Microsoft Naive Bayes algorithm can be used for association analysis, if the mining structure contains a nested table with the predictable attribute as the key.</span></span> <span data-ttu-id="4e3fb-308">예를 들어 데이터 마이닝 자습서의 [3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)에서 만든 마이닝 구조를 사용하여 Naive Bayes 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-308">For example, you could build a Naive Bayes model by using the mining structure created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) of the data mining tutorial.</span></span> <span data-ttu-id="4e3fb-309">이 예에 사용된 모델을 수정하여 사례 테이블에 수입 및 고객 지역에 대한 정보를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-309">The model used in this example was modified to add information about income and customer region in the case table.</span></span>  
  
 <span data-ttu-id="4e3fb-310">다음 쿼리 예에서는 `'Road Tire Tube'`제품의 구매와 관련된 제품을 예측하는 단일 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-310">The following query example shows a singleton query that predicts products that are related to purchases of the product, `'Road Tire Tube'`.</span></span> <span data-ttu-id="4e3fb-311">이 정보를 사용하여 특정 유형의 고객에게 제품을 추천할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-311">You might use this information to recommend products to a specific type of customer.</span></span>  
  
```  
SELECT   PredictAssociation([Association].[v Assoc Seq Line Items])  
FROM [Association_NB]  
NATURAL PREDICTION JOIN  
(SELECT 'High' AS [Income Group],  
  'Europe' AS [Region],  
  (SELECT 'Road Tire Tube' AS [Model])   
AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="4e3fb-312">일부 결과:</span><span class="sxs-lookup"><span data-stu-id="4e3fb-312">Partial results:</span></span>  
  
|<span data-ttu-id="4e3fb-313">모델</span><span class="sxs-lookup"><span data-stu-id="4e3fb-313">Model</span></span>|  
|-----------|  
|<span data-ttu-id="4e3fb-314">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="4e3fb-314">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="4e3fb-315">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="4e3fb-315">Water Bottle</span></span>|  
|<span data-ttu-id="4e3fb-316">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="4e3fb-316">Touring-3000</span></span>|  
|<span data-ttu-id="4e3fb-317">Touring-2000</span><span class="sxs-lookup"><span data-stu-id="4e3fb-317">Touring-2000</span></span>|  
|<span data-ttu-id="4e3fb-318">Touring-1000</span><span class="sxs-lookup"><span data-stu-id="4e3fb-318">Touring-1000</span></span>|  
  
## <a name="function-list"></a><span data-ttu-id="4e3fb-319">함수 목록</span><span class="sxs-lookup"><span data-stu-id="4e3fb-319">Function List</span></span>  
 <span data-ttu-id="4e3fb-320">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-320">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="4e3fb-321">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 다음 표에 나열된 추가 함수도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-321">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e3fb-322">예측 함수</span><span class="sxs-lookup"><span data-stu-id="4e3fb-322">Prediction Function</span></span>|<span data-ttu-id="4e3fb-323">사용</span><span class="sxs-lookup"><span data-stu-id="4e3fb-323">Usage</span></span>|  
|[<span data-ttu-id="4e3fb-324">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-324">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="4e3fb-325">한 노드가 모델에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-325">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="4e3fb-326">예측&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-326">Predict &#40;DMX&#41;</span></span>](/sql/dmx/predict-dmx)|<span data-ttu-id="4e3fb-327">지정한 열에 대한 예측 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-327">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="4e3fb-328">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-328">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="4e3fb-329">가중치 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-329">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="4e3fb-330">PredictAssociation&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-330">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="4e3fb-331">연관 데이터 세트에서의 멤버 자격을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-331">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="4e3fb-332">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-332">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="4e3fb-333">각 사례에 대한 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-333">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="4e3fb-334">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-334">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="4e3fb-335">예측 값의 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-335">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="4e3fb-336">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-336">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="4e3fb-337">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-337">Returns the support value for a specified state.</span></span>|  
  
 <span data-ttu-id="4e3fb-338">특정 함수의 구문을 보려면 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e3fb-338">To see  the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3fb-339">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e3fb-339">See Also</span></span>  
 <span data-ttu-id="4e3fb-340">[Microsoft Naive Bayes 알고리즘 기술 참조](microsoft-naive-bayes-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4e3fb-340">[Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="4e3fb-341">[Microsoft Naive Bayes 알고리즘](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="4e3fb-341">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 [<span data-ttu-id="4e3fb-342">Naive Bayes 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="4e3fb-342">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
