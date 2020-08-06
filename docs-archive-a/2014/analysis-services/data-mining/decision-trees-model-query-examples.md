---
title: 의사 결정 트리 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- decision tree algorithms [Analysis Services]
- content queries [DMX]
- decision trees [Analysis Services]
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a6b158a42c9ca90bf2cfd2e9b981a1e2a735ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729967"
---
# <a name="decision-trees-model-query-examples"></a><span data-ttu-id="acd50-102">의사 결정 트리 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="acd50-102">Decision Trees Model Query Examples</span></span>
  <span data-ttu-id="acd50-103">데이터 마이닝 모델에 대한 쿼리를 만들 때 분석 중에 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 만들거나, 모델의 패턴을 사용하여 새 데이터에 대한 예측을 수행하는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="acd50-104">예를 들어 의사 결정 트리 모델에 대한 내용 쿼리는 각 트리 수준의 사례 수에 대한 통계를 제공하거나 사례를 구분하는 규칙을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-104">For example, a content query for a decision trees model might provide statistics about the number of cases at each level of the tree, or the rules that differentiate between cases.</span></span> <span data-ttu-id="acd50-105">또한 예측 쿼리는 권장 사항, 분류 등을 생성하기 위해 모델을 새 데이터에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-105">Alternatively, a prediction query maps the model to new data in order to generate recommendations, classifications, and so forth.</span></span> <span data-ttu-id="acd50-106">쿼리를 사용하여 모델에 대한 메타데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-106">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="acd50-107">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 기반으로 하는 모델에 대한 쿼리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 <span data-ttu-id="acd50-108">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="acd50-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="acd50-109">데이터 마이닝 스키마 행 집합에서 모델 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-109">Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="acd50-110">DMX를 사용하여 모델의 트리에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="acd50-110">Getting Details about Trees in the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="acd50-111">모델에서 하위 트리 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-111">Retrieving Subtrees from the Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="acd50-112">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="acd50-112">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="acd50-113">예측 및 확률 반환</span><span class="sxs-lookup"><span data-stu-id="acd50-113">Returning Predictions with Probabilities</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="acd50-114">의사 결정 트리 모델에서 연결 예측</span><span class="sxs-lookup"><span data-stu-id="acd50-114">Predicting Associations from a Decision Trees Model</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="acd50-115">의사 결정 트리 모델에서 회귀 수식 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-115">Retrieving a Regression Formula from a Decision Trees Model</span></span>](#bkmk_Query6)  
  
##  <a name="finding-information-about-a-decision-trees-model"></a><a name="bkmk_top2"></a><span data-ttu-id="acd50-116">의사 결정 트리 모델에 대 한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="acd50-116">Finding Information about a Decision Trees Model</span></span>  
 <span data-ttu-id="acd50-117">의사 결정 트리 모델의 내용에 대한 의미 있는 쿼리를 만들려면 모델 내용의 구조와 노드 유형에 따라 저장되는 정보의 종류를 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-117">To create meaningful queries on the content of a decision trees model, you should understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="acd50-118">자세한 내용은 [의사 결정 트리 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-118">For more information, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-1-retrieving-model-parameters-from-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="acd50-119">예제 쿼리 1: 데이터 마이닝 스키마 행 집합에서 모델 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-119">Sample Query 1: Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="acd50-120">데이터 마이닝 스키마 행 집합을 쿼리하면 모델이 만들어진 날짜, 모델이 마지막으로 처리된 날짜, 모델의 기반이 되는 마이닝 구조의 이름, 예측 가능한 특성으로 사용된 열 이름 등 모델에 대한 메타데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-120">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="acd50-121">모델을 처음으로 만들 때 사용한 매개 변수를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-121">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 <span data-ttu-id="acd50-122">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="acd50-122">Sample results:</span></span>  
  
 <span data-ttu-id="acd50-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="acd50-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="acd50-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="acd50-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span></span>  
  
###  <a name="sample-query-2-returning-details-about-the-model-content-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="acd50-125">예제 쿼리 2: DMX를 사용 하 여 모델 콘텐츠에 대 한 세부 정보 반환</span><span class="sxs-lookup"><span data-stu-id="acd50-125">Sample Query 2: Returning Details about the Model Content by Using DMX</span></span>  
 <span data-ttu-id="acd50-126">다음 쿼리는 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)에서 모델을 작성할 때 만들어진 의사 결정 트리에 대한 몇 가지 기본 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-126">The following query returns some basic information about the decision trees that were created when you built the model in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="acd50-127">각 트리 구조는 자체 노드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-127">Each tree structure is stored in its own node.</span></span> <span data-ttu-id="acd50-128">이 모델에는 예측 가능한 특성이 하나이므로 트리 노드가 한 개뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-128">Because this model contains a single predictable attribute, there is only one tree node.</span></span> <span data-ttu-id="acd50-129">그러나 의사 결정 트리 알고리즘을 사용하여 연결 모델을 만드는 경우 각 제품에 대해 하나씩 수백 개의 트리가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-129">However, if you create an association model by using the Decision Trees algorithm, there might be hundreds of trees, one for each product.</span></span>  
  
 <span data-ttu-id="acd50-130">이 쿼리는 예측 가능한 특정 특성을 나타내는 최상위 트리 노드인 유형 2 노드를 모두 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-130">This query returns all the nodes of type 2, which are the top level nodes of a tree that represents a particular predictable attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acd50-131">열 `CHILDREN_CARDINALITY`는 대괄호로 묶어 동일한 이름의 MDX 예약 키워드와 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-131">The column, `CHILDREN_CARDINALITY`, must be enclosed in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="acd50-132">결과 예:</span><span class="sxs-lookup"><span data-stu-id="acd50-132">Example results:</span></span>  
  
|<span data-ttu-id="acd50-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-133">MODEL_NAME</span></span>|<span data-ttu-id="acd50-134">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-134">NODE_NAME</span></span>|<span data-ttu-id="acd50-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="acd50-135">NODE_CAPTION</span></span>|<span data-ttu-id="acd50-136">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="acd50-136">NODE_SUPPORT</span></span>|<span data-ttu-id="acd50-137">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="acd50-137">CHILDREN_CARDINALITY</span></span>|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|<span data-ttu-id="acd50-138">TM_DecisionTree</span><span class="sxs-lookup"><span data-stu-id="acd50-138">TM_DecisionTree</span></span>|<span data-ttu-id="acd50-139">000000001</span><span class="sxs-lookup"><span data-stu-id="acd50-139">000000001</span></span>|<span data-ttu-id="acd50-140">모두</span><span class="sxs-lookup"><span data-stu-id="acd50-140">All</span></span>|<span data-ttu-id="acd50-141">12939</span><span class="sxs-lookup"><span data-stu-id="acd50-141">12939</span></span>|<span data-ttu-id="acd50-142">5</span><span class="sxs-lookup"><span data-stu-id="acd50-142">5</span></span>|  
  
 <span data-ttu-id="acd50-143">이러한 결과의 의미는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="acd50-143">What do these results tell you?</span></span> <span data-ttu-id="acd50-144">의사 결정 트리 모델에서 특정 노드의 카디널리티를 보면 해당 노드의 직접 자식 수를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-144">In a decision trees model, the cardinality of a particular node tells you how many immediate children that node has.</span></span> <span data-ttu-id="acd50-145">이 노드의 카디널리티는 5이므로 모델에서 잠재적 자전거 구매자의 대상 모집단이 5개의 하위 그룹으로 나뉘었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-145">The cardinality for this node is 5, meaning that the model divided the target population of potential bike buyers into 5 subgroups.</span></span>  
  
 <span data-ttu-id="acd50-146">다음 관련 쿼리는 이러한 5개 하위 그룹의 자식을 자식 노드의 특성 및 값 분포와 함께 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-146">The following related query returns the children for these five subgroups, together with the distribution of attributes and values in the child nodes.</span></span> <span data-ttu-id="acd50-147">지지도, 확률 및 분산과 같은 통계는 중첩 테이블 `NODE_DISTRIBUTION`에 저장되므로 이 예에서는 `FLATTENED` 키워드를 사용하여 중첩 테이블 열을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-147">Because statistics such as support, probability, and variance are stored in the nested table, `NODE_DISTRIBUTION`, this example uses the `FLATTENED` keyword to output the nested table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acd50-148">중첩 테이블 열 `SUPPORT`는 대괄호로 묶어 동일한 이름의 예약 키워드와 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-148">The nested table column, `SUPPORT`, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 <span data-ttu-id="acd50-149">결과 예:</span><span class="sxs-lookup"><span data-stu-id="acd50-149">Example results:</span></span>  
  
|<span data-ttu-id="acd50-150">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-150">NODE_NAME</span></span>|<span data-ttu-id="acd50-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="acd50-151">NODE_CAPTION</span></span>|<span data-ttu-id="acd50-152">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-152">T.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="acd50-153">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="acd50-153">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="acd50-154">별칭</span><span class="sxs-lookup"><span data-stu-id="acd50-154">SUPPORT</span></span>|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|<span data-ttu-id="acd50-155">00000000100</span><span class="sxs-lookup"><span data-stu-id="acd50-155">00000000100</span></span>|<span data-ttu-id="acd50-156">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="acd50-156">Number Cars Owned = 0</span></span>|<span data-ttu-id="acd50-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-157">Bike Buyer</span></span>|<span data-ttu-id="acd50-158">Missing</span><span class="sxs-lookup"><span data-stu-id="acd50-158">Missing</span></span>|<span data-ttu-id="acd50-159">0</span><span class="sxs-lookup"><span data-stu-id="acd50-159">0</span></span>|  
|<span data-ttu-id="acd50-160">00000000100</span><span class="sxs-lookup"><span data-stu-id="acd50-160">00000000100</span></span>|<span data-ttu-id="acd50-161">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="acd50-161">Number Cars Owned = 0</span></span>|<span data-ttu-id="acd50-162">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-162">Bike Buyer</span></span>|<span data-ttu-id="acd50-163">0</span><span class="sxs-lookup"><span data-stu-id="acd50-163">0</span></span>|<span data-ttu-id="acd50-164">1067</span><span class="sxs-lookup"><span data-stu-id="acd50-164">1067</span></span>|  
|<span data-ttu-id="acd50-165">00000000100</span><span class="sxs-lookup"><span data-stu-id="acd50-165">00000000100</span></span>|<span data-ttu-id="acd50-166">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="acd50-166">Number Cars Owned = 0</span></span>|<span data-ttu-id="acd50-167">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-167">Bike Buyer</span></span>|<span data-ttu-id="acd50-168">1</span><span class="sxs-lookup"><span data-stu-id="acd50-168">1</span></span>|<span data-ttu-id="acd50-169">1875</span><span class="sxs-lookup"><span data-stu-id="acd50-169">1875</span></span>|  
|<span data-ttu-id="acd50-170">00000000101</span><span class="sxs-lookup"><span data-stu-id="acd50-170">00000000101</span></span>|<span data-ttu-id="acd50-171">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="acd50-171">Number Cars Owned = 3</span></span>|<span data-ttu-id="acd50-172">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-172">Bike Buyer</span></span>|<span data-ttu-id="acd50-173">Missing</span><span class="sxs-lookup"><span data-stu-id="acd50-173">Missing</span></span>|<span data-ttu-id="acd50-174">0</span><span class="sxs-lookup"><span data-stu-id="acd50-174">0</span></span>|  
|<span data-ttu-id="acd50-175">00000000101</span><span class="sxs-lookup"><span data-stu-id="acd50-175">00000000101</span></span>|<span data-ttu-id="acd50-176">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="acd50-176">Number Cars Owned = 3</span></span>|<span data-ttu-id="acd50-177">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-177">Bike Buyer</span></span>|<span data-ttu-id="acd50-178">0</span><span class="sxs-lookup"><span data-stu-id="acd50-178">0</span></span>|<span data-ttu-id="acd50-179">678</span><span class="sxs-lookup"><span data-stu-id="acd50-179">678</span></span>|  
|<span data-ttu-id="acd50-180">00000000101</span><span class="sxs-lookup"><span data-stu-id="acd50-180">00000000101</span></span>|<span data-ttu-id="acd50-181">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="acd50-181">Number Cars Owned = 3</span></span>|<span data-ttu-id="acd50-182">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-182">Bike Buyer</span></span>|<span data-ttu-id="acd50-183">1</span><span class="sxs-lookup"><span data-stu-id="acd50-183">1</span></span>|<span data-ttu-id="acd50-184">473</span><span class="sxs-lookup"><span data-stu-id="acd50-184">473</span></span>|  
  
 <span data-ttu-id="acd50-185">이러한 결과를 통해 자전거를 구입한 고객(`[Bike Buyer]` = 1) 중 1067명이 차량을 소유하지 않았으며 473명은 3대의 차량을 소유했다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-185">From these results, you can tell that of the customers who bought a bike (`[Bike Buyer]` = 1), 1067 customers had 0 cars and 473 customers had 3 cars.</span></span>  
  
###  <a name="sample-query-3-retrieving-subtrees-from-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="acd50-186">예제 쿼리 3: 모델에서 하위 트리 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-186">Sample Query 3: Retrieving Subtrees from the Model</span></span>  
 <span data-ttu-id="acd50-187">자전거를 구입한 고객에 대한 추가 정보를 검색한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-187">Suppose you wanted to discover more about the customers who did buy a bike.</span></span> <span data-ttu-id="acd50-188">다음 예와 같이 쿼리에 [IsDescendant&#40;DMX&#41;](/sql/dmx/isdescendant-dmx) 함수를 사용하여 하위 트리에 대한 추가 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-188">You can view additional detail for any of the sub-trees by using the [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) function in the query, as shown in the following example.</span></span> <span data-ttu-id="acd50-189">이 쿼리는 트리에서 42세 이상인 고객을 포함하는 리프 노드(NODE_TYPE = 4)를 검색하여 자전거 구매자 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-189">The query returns the count of bike purchasers by retrieving leaf nodes (NODE_TYPE = 4) from the tree that contains customers who are over 42 years of age.</span></span> <span data-ttu-id="acd50-190">이 쿼리는 중첩 테이블의 행을 Bike Buyer = 1인 행으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-190">The query restricts rows from the nested table to those where Bike Buyer = 1.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 <span data-ttu-id="acd50-191">결과 예:</span><span class="sxs-lookup"><span data-stu-id="acd50-191">Example results:</span></span>  
  
|<span data-ttu-id="acd50-192">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-192">NODE_NAME</span></span>|<span data-ttu-id="acd50-193">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="acd50-193">NODE_CAPTION</span></span>|<span data-ttu-id="acd50-194">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="acd50-194">t.SUPPORT</span></span>|  
|----------------|-------------------|---------------|  
|<span data-ttu-id="acd50-195">000000001000100</span><span class="sxs-lookup"><span data-stu-id="acd50-195">000000001000100</span></span>|<span data-ttu-id="acd50-196">Yearly Income >= 26000 and < 42000</span><span class="sxs-lookup"><span data-stu-id="acd50-196">Yearly Income >= 26000 and < 42000</span></span>|<span data-ttu-id="acd50-197">266</span><span class="sxs-lookup"><span data-stu-id="acd50-197">266</span></span>|  
|<span data-ttu-id="acd50-198">00000000100010100</span><span class="sxs-lookup"><span data-stu-id="acd50-198">00000000100010100</span></span>|<span data-ttu-id="acd50-199">Total Children = 3</span><span class="sxs-lookup"><span data-stu-id="acd50-199">Total Children = 3</span></span>|<span data-ttu-id="acd50-200">75</span><span class="sxs-lookup"><span data-stu-id="acd50-200">75</span></span>|  
|<span data-ttu-id="acd50-201">0000000010001010100</span><span class="sxs-lookup"><span data-stu-id="acd50-201">0000000010001010100</span></span>|<span data-ttu-id="acd50-202">Number Children At Home = 1</span><span class="sxs-lookup"><span data-stu-id="acd50-202">Number Children At Home = 1</span></span>|<span data-ttu-id="acd50-203">75</span><span class="sxs-lookup"><span data-stu-id="acd50-203">75</span></span>|  
  
## <a name="making-predictions-using-a-decision-trees-model"></a><span data-ttu-id="acd50-204">의사 결정 트리 모델을 사용하여 예측 수행</span><span class="sxs-lookup"><span data-stu-id="acd50-204">Making Predictions using a Decision Trees Model</span></span>  
 <span data-ttu-id="acd50-205">의사 결정 트리는 분류, 회귀, 연결 등과 같은 다양한 태스크에 사용할 수 있으므로 의사 결정 트리 모델에 대한 예측 쿼리를 작성할 때 많은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-205">Because decision trees can be used for various tasks, including classification, regression, and even association, when you create a prediction query on a decision tree model you have many options available to you.</span></span> <span data-ttu-id="acd50-206">예측 결과를 이해하려면 모델을 만든 용도를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-206">You must understand the purpose for which the model was created to understand the results of prediction.</span></span> <span data-ttu-id="acd50-207">다음 쿼리 예제에서는 3가지 다른 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-207">The following query samples illustrate three different scenarios:</span></span>  
  
-   <span data-ttu-id="acd50-208">분류 모델에 대한 예측을 예측이 정확할 확률과 함께 반환한 다음 확률별로 결과 필터링</span><span class="sxs-lookup"><span data-stu-id="acd50-208">Returning a prediction for a classification model, together with the probability of the prediction being correct, and then filtering the results by the probability;</span></span>  
  
-   <span data-ttu-id="acd50-209">단일 쿼리를 만들어 연결 예측</span><span class="sxs-lookup"><span data-stu-id="acd50-209">Creating a singleton query to predict associations;</span></span>  
  
-   <span data-ttu-id="acd50-210">의사 결정 트리에서 입력과 출력 간의 관계가 선형인 부분에 대한 회귀 수식 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-210">Retrieving the regression formula for a part of a decision tree where the relationship between the input and output is linear.</span></span>  
  
###  <a name="sample-query-4-returning-predictions-with-probabilities"></a><a name="bkmk_Query4"></a><span data-ttu-id="acd50-211">예제 쿼리 4: 확률을 사용 하 여 예측 반환</span><span class="sxs-lookup"><span data-stu-id="acd50-211">Sample Query 4: Returning Predictions with Probabilities</span></span>  
 <span data-ttu-id="acd50-212">다음 예제 쿼리에서는 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)에서 만든 의사 결정 트리 모델을 사용하고</span><span class="sxs-lookup"><span data-stu-id="acd50-212">The following sample query uses the decision tree model that was created in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="acd50-213">[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW의 dbo.ProspectiveBuyers 테이블에서 예제 데이터의 새 집합을 전달하여 새 데이터 집합의 고객 중 자전거를 구입할 가능성이 있는 고객을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-213">The query passes in a new set of sample data, from the table dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW, to predict which of the customers in the new data set will purchase a bike.</span></span>  
  
 <span data-ttu-id="acd50-214">이 쿼리에서는 모델에서 발견한 확률에 대한 유용한 정보를 포함하는 중첩 테이블을 반환하는 예측 함수 [PredictHistogram&#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-214">The query uses the prediction function [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), which returns a nested table that contains useful information about the probabilities discovered by the model.</span></span> <span data-ttu-id="acd50-215">쿼리의 최종 WHERE 절은 결과를 필터링하여 자전거를 구매할 가능성이 있는 것으로 예측된 고객, 즉 확률이 0%를 초과하는 고객만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-215">The final WHERE clause of the query filters the results to return only those customers who are predicted as likely to buy a bike, with a probability greater than 0%.</span></span>  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 <span data-ttu-id="acd50-216">기본적으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 열 레이블 **Expression**을 사용하여 중첩 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-216">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns nested tables with the column label, **Expression**.</span></span> <span data-ttu-id="acd50-217">반환되는 열에 별칭을 지정하여 이 레이블을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-217">You can change this label by aliasing the column that is returned.</span></span> <span data-ttu-id="acd50-218">이렇게 하면 별칭(이 경우 **Results**)이 열 제목과 중첩 테이블의 값 모두로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-218">If you do this, the alias (in this case, **Results**) is used as both the column heading and as the value in the nested table.</span></span> <span data-ttu-id="acd50-219">결과를 보려면 중첩 테이블을 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-219">You must expand the nested table to see the results.</span></span>  
  
 <span data-ttu-id="acd50-220">자전거 구매자 = 1 인 예제 결과:</span><span class="sxs-lookup"><span data-stu-id="acd50-220">Example results where Bike Buyer = 1:</span></span>  
  
|<span data-ttu-id="acd50-221">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="acd50-221">Bike Buyer</span></span>|<span data-ttu-id="acd50-222">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="acd50-222">$SUPPORT</span></span>|<span data-ttu-id="acd50-223">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="acd50-223">$PROBABILITY</span></span>|<span data-ttu-id="acd50-224">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="acd50-224">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="acd50-225">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="acd50-225">$VARIANCE</span></span>|<span data-ttu-id="acd50-226">$STDEV</span><span class="sxs-lookup"><span data-stu-id="acd50-226">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="acd50-227">1</span><span class="sxs-lookup"><span data-stu-id="acd50-227">1</span></span>|<span data-ttu-id="acd50-228">2540</span><span class="sxs-lookup"><span data-stu-id="acd50-228">2540</span></span>|<span data-ttu-id="acd50-229">0.634849242045644</span><span class="sxs-lookup"><span data-stu-id="acd50-229">0.634849242045644</span></span>|<span data-ttu-id="acd50-230">0.013562168281562</span><span class="sxs-lookup"><span data-stu-id="acd50-230">0.013562168281562</span></span>|<span data-ttu-id="acd50-231">0</span><span class="sxs-lookup"><span data-stu-id="acd50-231">0</span></span>|<span data-ttu-id="acd50-232">0</span><span class="sxs-lookup"><span data-stu-id="acd50-232">0</span></span>|  
|<span data-ttu-id="acd50-233">0</span><span class="sxs-lookup"><span data-stu-id="acd50-233">0</span></span>|<span data-ttu-id="acd50-234">1460</span><span class="sxs-lookup"><span data-stu-id="acd50-234">1460</span></span>|<span data-ttu-id="acd50-235">0.364984174579377</span><span class="sxs-lookup"><span data-stu-id="acd50-235">0.364984174579377</span></span>|<span data-ttu-id="acd50-236">0.00661336932550915</span><span class="sxs-lookup"><span data-stu-id="acd50-236">0.00661336932550915</span></span>|<span data-ttu-id="acd50-237">0</span><span class="sxs-lookup"><span data-stu-id="acd50-237">0</span></span>|<span data-ttu-id="acd50-238">0</span><span class="sxs-lookup"><span data-stu-id="acd50-238">0</span></span>|  
||<span data-ttu-id="acd50-239">0</span><span class="sxs-lookup"><span data-stu-id="acd50-239">0</span></span>|<span data-ttu-id="acd50-240">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="acd50-240">0.000166583374979177</span></span>|<span data-ttu-id="acd50-241">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="acd50-241">0.000166583374979177</span></span>|<span data-ttu-id="acd50-242">0</span><span class="sxs-lookup"><span data-stu-id="acd50-242">0</span></span>|<span data-ttu-id="acd50-243">0</span><span class="sxs-lookup"><span data-stu-id="acd50-243">0</span></span>|  
  
 <span data-ttu-id="acd50-244">공급자가 여기에 표시된 것과 같은 계층적 행 집합을 지원하지 않는 경우 쿼리에 FLATTENED 키워드를 사용하여 반복되는 열 값 대신 Null을 포함하는 테이블로 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-244">If your provider does not support hierarchical rowsets, such as those shown here, you can use the FLATTENED keyword in the query to return the results as a table that contains nulls in place of the repeated column values.</span></span> <span data-ttu-id="acd50-245">자세한 내용은 [중첩 테이블&#40;Analysis Services - 데이터 마이닝&#41;](nested-tables-analysis-services-data-mining.md) 또는 [DMX Select 문 이해](/sql/dmx/understanding-the-dmx-select-statement)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-245">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md) or [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement).</span></span>  
  
###  <a name="sample-query-5-predicting-associations-from-a-decision-trees-model"></a><a name="bkmk_Query5"></a><span data-ttu-id="acd50-246">예제 쿼리 5: 의사 결정 트리 모델에서 연결 예측</span><span class="sxs-lookup"><span data-stu-id="acd50-246">Sample Query 5: Predicting Associations from a Decision Trees Model</span></span>  
 <span data-ttu-id="acd50-247">다음 예제 쿼리는 Association 마이닝 구조를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-247">The following sample query is based on the Association mining structure.</span></span> <span data-ttu-id="acd50-248">이 예제의 단계별 작업을 따라가려면 이 마이닝 구조에 새 모델을 추가하고 Microsoft 의사 결정 트리를 알고리즘으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-248">To follow along with this example, you can add a new model to this mining structure, and select Microsoft Decision Trees as the algorithm.</span></span> <span data-ttu-id="acd50-249">연결 마이닝 구조를 만드는 방법은 [3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-249">For more information on how to create the Association mining structure, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="acd50-250">다음 예제 쿼리는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 필드를 선택한 다음 드롭다운 목록에서 이러한 필드의 값을 선택하여 간단하게 만들 수 있는 단일 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-250">The following sample query is a singleton query, which you can create easily in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] by choosing fields and then selecting values for those fields from a drop-down list.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="acd50-251">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="acd50-251">Expected results:</span></span>  
  
|<span data-ttu-id="acd50-252">모델</span><span class="sxs-lookup"><span data-stu-id="acd50-252">Model</span></span>|  
|-----------|  
|<span data-ttu-id="acd50-253">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="acd50-253">Mountain-200</span></span>|  
|<span data-ttu-id="acd50-254">Mountain Tire Tube</span><span class="sxs-lookup"><span data-stu-id="acd50-254">Mountain Tire Tube</span></span>|  
|<span data-ttu-id="acd50-255">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="acd50-255">Touring Tire Tube</span></span>|  
  
 <span data-ttu-id="acd50-256">결과를 통해 Patch Kit 제품을 구매한 고객에게 권장하기에 가장 좋은 3가지 제품을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-256">The results tell you the three best products to recommend to customers who have purchased the Patch Kit product.</span></span> <span data-ttu-id="acd50-257">값을 입력하거나 **단일 쿼리 입력** 대화 상자에서 값을 추가 또는 제거하여 권장 사항을 결정할 때 여러 제품을 입력으로 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-257">You can also provide multiple products as input when you make recommendations, either by typing in values, or by using the **Singleton Query Input** dialog box and adding or removing values.</span></span> <span data-ttu-id="acd50-258">다음 예제 쿼리에서는 여러 값을 제공하여 이에 대해 예측을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-258">The following sample query shows how the multiple values are provided, upon which to make a prediction.</span></span> <span data-ttu-id="acd50-259">값은 입력 값을 정의하는 SELECT 문에서 UNION 절로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-259">Values are connected by a UNION clause in the SELECT statement that defines the input values.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="acd50-260">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="acd50-260">Expected results:</span></span>  
  
|<span data-ttu-id="acd50-261">모델</span><span class="sxs-lookup"><span data-stu-id="acd50-261">Model</span></span>|  
|-----------|  
|<span data-ttu-id="acd50-262">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="acd50-262">Long-Sleeve Logo Jersey</span></span>|  
|<span data-ttu-id="acd50-263">Mountain-400-W</span><span class="sxs-lookup"><span data-stu-id="acd50-263">Mountain-400-W</span></span>|  
|<span data-ttu-id="acd50-264">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="acd50-264">Classic Vest</span></span>|  
  
###  <a name="sample-query-6-retrieving-a-regression-formula-from-a-decision-trees-model"></a><a name="bkmk_Query6"></a><span data-ttu-id="acd50-265">예제 쿼리 6: 의사 결정 트리 모델에서 회귀 수식 검색</span><span class="sxs-lookup"><span data-stu-id="acd50-265">Sample Query 6: Retrieving a Regression Formula from a Decision Trees Model</span></span>  
 <span data-ttu-id="acd50-266">연속 특성에 대한 회귀를 포함하는 의사 결정 트리 모델을 만드는 경우 회귀 수식을 사용하여 예측을 수행하거나 회귀 수식에 대한 정보를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-266">When you create a decision tree model that contains a regression on a continuous attribute, you can use the regression formula to make predictions, or you can extract information about the regression formula.</span></span> <span data-ttu-id="acd50-267">회귀 모델 쿼리에 대한 자세한 내용은 [선형 회귀 모델 쿼리 예제](linear-regression-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-267">For more information about queries on regression models, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="acd50-268">의사 결정 트리 모델에 회귀 노드와 불연속 특성 또는 범위에 따라 분할되는 노드가 혼합되어 있는 경우 회귀 노드만 반환하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-268">If a decision trees model contains a mixture of regression nodes and nodes that split on discrete attributes or ranges, you can create a query that returns only the regression node.</span></span> <span data-ttu-id="acd50-269">NODE_DISTRIBUTION 테이블에는 회귀 수식에 대한 세부 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-269">The NODE_DISTRIBUTION table contains the details of the regression formula.</span></span> <span data-ttu-id="acd50-270">이 예에서는 쉽게 볼 수 있도록 열이 일반화되고 NODE_DISTRIBUTION 테이블에 별칭이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-270">In this example, the columns are flattened and the NODE_DISTRIBUTION table is aliased for easier viewing.</span></span> <span data-ttu-id="acd50-271">그러나 이 모델에는 Income을 다른 연속 특성과 연결하는 회귀 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-271">However, in this model, no regressors were found to relate Income with other continuous attributes.</span></span> <span data-ttu-id="acd50-272">이 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 특성의 평균 값과 해당 특성에 대한 모델의 총 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-272">In such cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the mean value of the attribute and the total variance in the model for that attribute.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 <span data-ttu-id="acd50-273">결과 예:</span><span class="sxs-lookup"><span data-stu-id="acd50-273">Example results:</span></span>  
  
|<span data-ttu-id="acd50-274">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd50-274">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="acd50-275">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="acd50-275">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="acd50-276">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="acd50-276">t.SUPPORT</span></span>|<span data-ttu-id="acd50-277">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="acd50-277">t.PROBABILITY</span></span>|<span data-ttu-id="acd50-278">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="acd50-278">t.VARIANCE</span></span>|<span data-ttu-id="acd50-279">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="acd50-279">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="acd50-280">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="acd50-280">Yearly Income</span></span>|<span data-ttu-id="acd50-281">Missing</span><span class="sxs-lookup"><span data-stu-id="acd50-281">Missing</span></span>|<span data-ttu-id="acd50-282">0</span><span class="sxs-lookup"><span data-stu-id="acd50-282">0</span></span>|<span data-ttu-id="acd50-283">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="acd50-283">0.000457142857142857</span></span>|<span data-ttu-id="acd50-284">0</span><span class="sxs-lookup"><span data-stu-id="acd50-284">0</span></span>|<span data-ttu-id="acd50-285">1</span><span class="sxs-lookup"><span data-stu-id="acd50-285">1</span></span>|  
|<span data-ttu-id="acd50-286">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="acd50-286">Yearly Income</span></span>|<span data-ttu-id="acd50-287">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="acd50-287">57220.8876687257</span></span>|<span data-ttu-id="acd50-288">17484</span><span class="sxs-lookup"><span data-stu-id="acd50-288">17484</span></span>|<span data-ttu-id="acd50-289">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="acd50-289">0.999542857142857</span></span>|<span data-ttu-id="acd50-290">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="acd50-290">1041275619.52776</span></span>|<span data-ttu-id="acd50-291">3</span><span class="sxs-lookup"><span data-stu-id="acd50-291">3</span></span>|  
||<span data-ttu-id="acd50-292">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="acd50-292">57220.8876687257</span></span>|<span data-ttu-id="acd50-293">0</span><span class="sxs-lookup"><span data-stu-id="acd50-293">0</span></span>|<span data-ttu-id="acd50-294">0</span><span class="sxs-lookup"><span data-stu-id="acd50-294">0</span></span>|<span data-ttu-id="acd50-295">1041216662.54387</span><span class="sxs-lookup"><span data-stu-id="acd50-295">1041216662.54387</span></span>|<span data-ttu-id="acd50-296">11</span><span class="sxs-lookup"><span data-stu-id="acd50-296">11</span></span>|  
  
 <span data-ttu-id="acd50-297">회귀 모델에 사용되는 값 형식 및 통계에 대한 자세한 내용은 [선형 회귀 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-297">For more information about the value types and the statistics used in regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="acd50-298">예측 함수 목록</span><span class="sxs-lookup"><span data-stu-id="acd50-298">List of Prediction Functions</span></span>  
 <span data-ttu-id="acd50-299">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-299">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="acd50-300">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘은 다음 표에 나열된 함수를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-300">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="acd50-301">예측 함수</span><span class="sxs-lookup"><span data-stu-id="acd50-301">Prediction Function</span></span>|<span data-ttu-id="acd50-302">사용</span><span class="sxs-lookup"><span data-stu-id="acd50-302">Usage</span></span>|  
|[<span data-ttu-id="acd50-303">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-303">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="acd50-304">한 노드가 모델에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-304">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="acd50-305">IsInNode&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-305">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="acd50-306">지정한 노드에 현재 사례가 포함되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-306">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="acd50-307">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-307">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="acd50-308">가중치 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-308">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="acd50-309">PredictAssociation&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-309">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="acd50-310">연관 데이터 세트에서의 멤버 자격을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-310">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="acd50-311">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-311">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="acd50-312">현재 예측된 값과 관련 된 값의 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-312">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="acd50-313">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-313">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="acd50-314">각 사례에 대한 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-314">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="acd50-315">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-315">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="acd50-316">예측 값의 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-316">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="acd50-317">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-317">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="acd50-318">지정된 열의 예측 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-318">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="acd50-319">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-319">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="acd50-320">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-320">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="acd50-321">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-321">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="acd50-322">지정한 열의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acd50-322">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="acd50-323">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘에 공통된 함수 목록은 [일반 예측 함수&#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-323">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="acd50-324">특정 함수의 구문은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="acd50-324">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd50-325">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acd50-325">See Also</span></span>  
 <span data-ttu-id="acd50-326">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="acd50-326">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="acd50-327">[Microsoft 의사 결정 트리 알고리즘](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="acd50-327">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="acd50-328">[Microsoft 의사 결정 트리 알고리즘 기술 참조](microsoft-decision-trees-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="acd50-328">[Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="acd50-329">의사 결정 트리 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="acd50-329">Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
