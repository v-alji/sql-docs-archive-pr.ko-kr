---
title: 신경망 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- neural network algorithms [Analysis Services]
- content queries [DMX]
- neural network model [Analysis Services]
ms.assetid: 81b06183-620f-4e0c-bc10-532e6a1f0829
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7154ce0ad66346634225734fe829c36e7bf3ad58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734635"
---
# <a name="neural-network-model-query-examples"></a><span data-ttu-id="a6caf-102">신경망 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="a6caf-102">Neural Network Model Query Examples</span></span>
  <span data-ttu-id="a6caf-103">데이터 마이닝 모델에 대한 쿼리를 작성할 때 분석 중에 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 작성하거나, 모델의 패턴을 사용하여 새 데이터에 대한 예측을 만드는 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="a6caf-104">예를 들어 신경망 모델에 대한 내용 쿼리에서는 숨겨진 계층 수와 같은 모델 메타데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-104">For example, a content query for a neural network model might retrieve model metadata such as the number of hidden layers.</span></span> <span data-ttu-id="a6caf-105">또한 예측 쿼리는 입력에 따른 분류를 제안하고 선택적으로 각 분류에 대한 확률을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-105">Alternatively, a prediction query might suggest classifications based on an input and optionally provide probabilities for each classification.</span></span>  
  
 <span data-ttu-id="a6caf-106">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 기반으로 하는 모델에 대해 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-106">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="a6caf-107">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="a6caf-107">**Content queries**</span></span>  
  
 [<span data-ttu-id="a6caf-108">DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a6caf-108">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="a6caf-109">스키마 행 집합에서 모델 메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-109">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="a6caf-110">모델에 대한 입력 특성 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-110">Retrieving the Input Attributes for the Model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="a6caf-111">숨겨진 계층에서 가중치 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-111">Retrieving Weights from the Hidden Layer</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="a6caf-112">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="a6caf-112">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="a6caf-113">단일 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="a6caf-113">Creating a Singleton Prediction</span></span>](#bkmk_Query5)  
  
## <a name="finding-information-about-a-neural-network-model"></a><span data-ttu-id="a6caf-114">신경망 모델에 대한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="a6caf-114">Finding Information about a Neural Network Model</span></span>  
 <span data-ttu-id="a6caf-115">모든 마이닝 모델은 마이닝 모델 스키마 행 집합이라고 하는 표준화된 스키마에 따라, 알고리즘을 통해 학습한 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-115">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="a6caf-116">이 정보는 기본 메타데이터, 분석 시 발견된 구조 및 처리할 때 사용된 매개 변수를 포함하여 모델에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-116">This information provides details about the model and includes the basic metadata, structures discovered in analysis, and parameters that are used when processing.</span></span> <span data-ttu-id="a6caf-117">모델 콘텐츠에 대한 쿼리는 DMX(Data Mining Extensions) 문을 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-117">You can create queries against the model content by using Data Mining Extension (DMX) statements.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="a6caf-118">예제 쿼리 1: DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a6caf-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="a6caf-119">다음 쿼리는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하여 작성한 모델에 대한 몇 가지 기본 메타데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-119">The following query returns some basic metadata about a model that was built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="a6caf-120">신경망 모델에서 모델의 부모 노드에는 모델의 이름, 모델이 저장된 데이터베이스의 이름 및 자식 노드의 수만 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-120">In a neural network model, the parent node of the model contains only the name of the model, the name of the database where the model is stored, and the number of child nodes.</span></span> <span data-ttu-id="a6caf-121">그러나 marginal statistics node(NODE_TYPE = 24)는 이 기본 메타데이터와 모델에 사용된 입력 열에 대한 몇 가지 파생된 통계를 모두 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-121">However, the marginal statistics node (NODE_TYPE = 24) provides both this basic metadata and some derived statistics about the input columns used in the model.</span></span>  
  
 <span data-ttu-id="a6caf-122">다음 예제 쿼리는 [중급 데이터 마이닝 자습서](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)에서 만든 `Call Center Default NN`이라고 하는 마이닝 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-122">The following sample query is based on the mining model that you create in the [Intermediate Data Mining Tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md), named `Call Center Default NN`.</span></span> <span data-ttu-id="a6caf-123">이 모델은 콜 센터의 데이터를 사용하여 직원 배치, 호출 수, 주문 수 및 문제 수 간의 가능한 상관 관계를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-123">The model uses data from a call center to explore possible correlations between staffing and the number of calls, orders, and issues.</span></span> <span data-ttu-id="a6caf-124">DMX 문은 신경망 모델의 marginal statistics node에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-124">The DMX statement retrieves data from the marginal statistics node of the neural network model.</span></span> <span data-ttu-id="a6caf-125">관심 있는 입력 특성 통계가 NODE_DISTRIBUTION 중첩 테이블에 저장되어 있으므로 이 쿼리에는 FLATTENED 키워드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-125">The query includes the FLATTENED keyword, because the input attribute statistics of interest are stored in a nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="a6caf-126">그러나 쿼리 공급자가 계층적 행 집합을 지원하는 경우에는 FLATTENED 키워드를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-126">However, if your query provider supports hierarchical rowsets you do not need to use the FLATTENED keyword.</span></span>  
  
```  
SELECT FLATTENED MODEL_CATALOG, MODEL_NAME,   
(    SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
     [SUPPORT], [PROBABILITY], VALUETYPE   
     FROM NODE_DISTRIBUTION  
) AS t  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 24  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a6caf-127">중첩 테이블 열 이름인 `[SUPPORT]` 및 `[PROBABILITY]`는 대괄호로 묶어 동일한 이름의 예약 키워드와 구별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-127">You must enclose the name of the nested table columns `[SUPPORT]` and `[PROBABILITY]` in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="a6caf-128">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-128">Example results:</span></span>  
  
|<span data-ttu-id="a6caf-129">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a6caf-129">MODEL_CATALOG</span></span>|<span data-ttu-id="a6caf-130">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-130">MODEL_NAME</span></span>|<span data-ttu-id="a6caf-131">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-131">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a6caf-132">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a6caf-132">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a6caf-133">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a6caf-133">t.SUPPORT</span></span>|<span data-ttu-id="a6caf-134">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a6caf-134">t.PROBABILITY</span></span>|<span data-ttu-id="a6caf-135">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a6caf-135">t.VALUETYPE</span></span>|  
|--------------------|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="a6caf-136">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="a6caf-136">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="a6caf-137">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="a6caf-137">Call Center NN</span></span>|<span data-ttu-id="a6caf-138">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="a6caf-138">Average Time Per Issue</span></span>|<span data-ttu-id="a6caf-139">Missing</span><span class="sxs-lookup"><span data-stu-id="a6caf-139">Missing</span></span>|<span data-ttu-id="a6caf-140">0</span><span class="sxs-lookup"><span data-stu-id="a6caf-140">0</span></span>|<span data-ttu-id="a6caf-141">0</span><span class="sxs-lookup"><span data-stu-id="a6caf-141">0</span></span>|<span data-ttu-id="a6caf-142">1</span><span class="sxs-lookup"><span data-stu-id="a6caf-142">1</span></span>|  
|<span data-ttu-id="a6caf-143">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="a6caf-143">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="a6caf-144">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="a6caf-144">Call Center NN</span></span>|<span data-ttu-id="a6caf-145">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="a6caf-145">Average Time Per Issue</span></span>|<span data-ttu-id="a6caf-146">< 64.7094100096</span><span class="sxs-lookup"><span data-stu-id="a6caf-146">< 64.7094100096</span></span>|<span data-ttu-id="a6caf-147">11</span><span class="sxs-lookup"><span data-stu-id="a6caf-147">11</span></span>|<span data-ttu-id="a6caf-148">0.407407407</span><span class="sxs-lookup"><span data-stu-id="a6caf-148">0.407407407</span></span>|<span data-ttu-id="a6caf-149">5</span><span class="sxs-lookup"><span data-stu-id="a6caf-149">5</span></span>|  
  
 <span data-ttu-id="a6caf-150">신경망 모델의 컨텍스트에서 스키마 행 집합 열의 의미에 대한 정의는 [신경망 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)이라고 하는 마이닝 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-150">For a definition of what the columns in the schema rowset mean in the context of a neural network model, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="a6caf-151">예제 쿼리 2: 스키마 행 집합에서 모델 메타 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-151">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="a6caf-152">데이터 마이닝 스키마 행 집합을 쿼리하여 DMX 내용 쿼리에 반환되는 것과 동일한 정보를 찾을 수 있는데,</span><span class="sxs-lookup"><span data-stu-id="a6caf-152">You can find the same information that is returned in a DMX content query by querying the data mining schema rowset.</span></span> <span data-ttu-id="a6caf-153">스키마 행 집합은 몇 개의 열을 추가로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-153">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="a6caf-154">다음 예제 쿼리에서는 모델이 생성되고 수정되고 마지막으로 처리된 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-154">The following sample query returns the date that the model was created, the date it was modified, and the date that the model was last processed.</span></span> <span data-ttu-id="a6caf-155">또한 이 쿼리에서는 모델 콘텐츠에서 쉽게 사용할 수 없는 예측 가능한 열과 모델을 작성하는 데 사용된 매개 변수에 대한 세부 정보도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-155">The query also returns the predictable columns, which are not easily available from the model content, and the parameters that were used to build the model.</span></span> <span data-ttu-id="a6caf-156">이 정보는 모델을 문서화하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-156">This information can be useful for documenting the model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center Default NN'  
```  
  
 <span data-ttu-id="a6caf-157">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-157">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6caf-158">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-158">MODEL_NAME</span></span>|<span data-ttu-id="a6caf-159">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="a6caf-159">Call Center Default NN</span></span>|  
|<span data-ttu-id="a6caf-160">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a6caf-160">DATE_CREATED</span></span>|<span data-ttu-id="a6caf-161">1/10/2008 5:07:38 PM</span><span class="sxs-lookup"><span data-stu-id="a6caf-161">1/10/2008 5:07:38 PM</span></span>|  
|<span data-ttu-id="a6caf-162">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="a6caf-162">LAST_PROCESSED</span></span>|<span data-ttu-id="a6caf-163">1/10/2008 5:24:02 PM</span><span class="sxs-lookup"><span data-stu-id="a6caf-163">1/10/2008 5:24:02 PM</span></span>|  
|<span data-ttu-id="a6caf-164">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="a6caf-164">PREDICTION_ENTITY</span></span>|<span data-ttu-id="a6caf-165">Average Time Per Issue,</span><span class="sxs-lookup"><span data-stu-id="a6caf-165">Average Time Per Issue,</span></span><br /><br /> <span data-ttu-id="a6caf-166">Grade Of Service,</span><span class="sxs-lookup"><span data-stu-id="a6caf-166">Grade Of Service,</span></span><br /><br /> <span data-ttu-id="a6caf-167">Number Of Orders</span><span class="sxs-lookup"><span data-stu-id="a6caf-167">Number Of Orders</span></span>|  
|<span data-ttu-id="a6caf-168">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6caf-168">MINING_PARAMETERS</span></span>|<span data-ttu-id="a6caf-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="a6caf-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span></span><br /><br /> <span data-ttu-id="a6caf-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="a6caf-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="a6caf-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span><span class="sxs-lookup"><span data-stu-id="a6caf-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span></span>|  
  
###  <a name="sample-query-3-retrieving-the-input-attributes-for-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="a6caf-172">예제 쿼리 3: 모델에 대 한 입력 특성 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-172">Sample Query 3: Retrieving the Input Attributes for the Model</span></span>  
 <span data-ttu-id="a6caf-173">입력 계층(NODE_TYPE = 18)의 자식 노드(NODE_TYPE = 20)를 쿼리하여 모델을 만드는 데 사용된 정확한 입력 특성-값 쌍을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-173">You can retrieve the input attribute-value pairs that were used to create the model by querying the child nodes (NODE_TYPE = 20) of the input layer (NODE_TYPE = 18).</span></span> <span data-ttu-id="a6caf-174">다음 쿼리는 노드 설명에서 입력 특성 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-174">The following query returns a list of input attributes from the node descriptions.</span></span>  
  
```  
SELECT NODE_DESCRIPTION  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="a6caf-175">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-175">Example results:</span></span>  
  
|<span data-ttu-id="a6caf-176">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a6caf-176">NODE_DESCRIPTION</span></span>|  
|-----------------------|  
|<span data-ttu-id="a6caf-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="a6caf-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="a6caf-178">Day Of Week=Fri.</span><span class="sxs-lookup"><span data-stu-id="a6caf-178">Day Of Week=Fri.</span></span>|  
|<span data-ttu-id="a6caf-179">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="a6caf-179">Level 1 Operators</span></span>|  
  
 <span data-ttu-id="a6caf-180">여기에는 결과에 포함된 행 중 일부 대표 행만 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-180">Only a few representative rows from the results are shown here.</span></span> <span data-ttu-id="a6caf-181">그러나 NODE_DESCRIPTION이 입력 특성의 데이터 형식에 따라 약간씩 다른 정보를 제공한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-181">However, you can see that the NODE_DESCRIPTION provides slightly different information depending on the data type of the input attribute.</span></span>  
  
-   <span data-ttu-id="a6caf-182">특성이 불연속 값 또는 불연속화된 값인 경우 특성과 해당 값 또는 불연속화된 범위가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-182">If the attribute is a discrete or discretized value, the attribute and either its value or its discretized range are returned.</span></span>  
  
-   <span data-ttu-id="a6caf-183">특성이 연속 숫자 데이터 형식일 경우에는 NODE_DESCRIPTION에 특성 이름만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-183">If the attribute is a continuous numeric data type, the NODE_DESCRIPTION contains only the attribute name.</span></span> <span data-ttu-id="a6caf-184">그러나 NODE_DISTRIBUTION 중첩 테이블을 검색하여 평균을 가져오거나 NODE_RULE을 반환하여 숫자 범위의 최소값 및 최대값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-184">However, you can retrieve the nested NODE_DISTRIBUTION table to obtain the mean, or return the NODE_RULE to obtain the minimum and maximum values of the numeric range.</span></span>  
  
 <span data-ttu-id="a6caf-185">다음 쿼리에서는 NODE_DISTRIBUTION 중첩 테이블을 쿼리하여 한 열에 있는 특성과 다른 열에 있는 해당 특성의 값을 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-185">The following query shows how to query the nested NODE_DISTRIBUTION table to return the attributes in one column, and their values in another column.</span></span> <span data-ttu-id="a6caf-186">연속 특성의 경우에는 특성 값은 특성 평균으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-186">For continuous attributes, the value of the attribute is represented by its mean.</span></span>  
  
```  
SELECT FLATTENED   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) as t  
FROM [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 21  
```  
  
 <span data-ttu-id="a6caf-187">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-187">Example results:</span></span>  
  
|<span data-ttu-id="a6caf-188">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-188">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a6caf-189">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a6caf-189">t.ATTRIBUTE_VALUE</span></span>|  
|-----------------------|------------------------|  
|<span data-ttu-id="a6caf-190">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="a6caf-190">Average Time Per Issue</span></span>|<span data-ttu-id="a6caf-191">64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="a6caf-191">64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="a6caf-192">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="a6caf-192">Day Of Week</span></span>|<span data-ttu-id="a6caf-193">Fri.</span><span class="sxs-lookup"><span data-stu-id="a6caf-193">Fri.</span></span>|  
|<span data-ttu-id="a6caf-194">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="a6caf-194">Level 1 Operators</span></span>|<span data-ttu-id="a6caf-195">3.2962962962963</span><span class="sxs-lookup"><span data-stu-id="a6caf-195">3.2962962962963</span></span>|  
  
 <span data-ttu-id="a6caf-196">최소 및 최대 범위 값은 NODE_RULE 열에 저장되어 있으며 다음 예에 표시된 것과 같이 XML 조각으로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-196">The minimum and maximum range values are stored in the NODE_RULE column, and are represented as an XML fragment, as shown in the following example:</span></span>  
  
```  
<NormContinuous field="Level 1 Operators">    
  <LinearNorm orig="2.83967303681711" norm="-1" />    
  <LinearNorm orig="3.75291955577548" norm="1" />    
</NormContinuous>    
```  
  
###  <a name="sample-query-4-retrieving-weights-from-the-hidden-layer"></a><a name="bkmk_Query4"></a><span data-ttu-id="a6caf-197">예제 쿼리 4: 숨겨진 계층에서 가중치 검색</span><span class="sxs-lookup"><span data-stu-id="a6caf-197">Sample Query 4: Retrieving Weights from the Hidden Layer</span></span>  
 <span data-ttu-id="a6caf-198">신경망 모델의 모델 콘텐츠는 네트워크의 모든 노드에 대한 세부 정보를 쉽게 가져올 수 있도록 구조화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-198">The model content of a neural network model is structured in a way that makes it easy to retrieve details about any node in the network.</span></span> <span data-ttu-id="a6caf-199">또한 노드의 ID 번호는 노드 유형 간의 관계를 파악하는 데 도움이 되는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-199">Moreover, the ID numbers of the nodes provide information that helps you identify relationships among the node types.</span></span>  
  
 <span data-ttu-id="a6caf-200">다음 쿼리에서는 숨겨진 계층의 특정 노드에 저장된 계수를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-200">The following query demonstrates how to retrieve the coefficients that are stored under a particular node of the hidden layer.</span></span> <span data-ttu-id="a6caf-201">숨겨진 계층은 메타데이터만 포함하는 구성 도우미 노드(NODE_TYPE = 19)와 특성 및 값의 다양한 조합에 대한 계수를 포함하는 여러 자식 노드(NODE_TYPE = 22)로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-201">The hidden layer consists of an organizer node (NODE_TYPE = 19), which contains only metadata, and multiple child nodes (NODE_TYPE = 22), which contain the coefficients for the various combinations of attributes and values.</span></span> <span data-ttu-id="a6caf-202">이 쿼리에서는 계수 노드만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-202">This query returns only the coefficient nodes.</span></span>  
  
```  
SELECT FLATTENED TOP 1 NODE_UNIQUE_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM  [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 22  
AND [PARENT_UNIQUE_NAME] = '40000000200000000' FROM [Call Center Default NN].CONTENT  
```  
  
 <span data-ttu-id="a6caf-203">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-203">Example results:</span></span>  
  
|<span data-ttu-id="a6caf-204">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-204">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="a6caf-205">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a6caf-205">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a6caf-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a6caf-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a6caf-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a6caf-207">t.VALUETYPE</span></span>|  
|------------------------|-----------------------|------------------------|-----------------|  
|<span data-ttu-id="a6caf-208">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-208">70000000200000000</span></span>|<span data-ttu-id="a6caf-209">6000000000000000a</span><span class="sxs-lookup"><span data-stu-id="a6caf-209">6000000000000000a</span></span>|<span data-ttu-id="a6caf-210">-0.178616518</span><span class="sxs-lookup"><span data-stu-id="a6caf-210">-0.178616518</span></span>|<span data-ttu-id="a6caf-211">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-211">7</span></span>|  
|<span data-ttu-id="a6caf-212">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-212">70000000200000000</span></span>|<span data-ttu-id="a6caf-213">6000000000000000b</span><span class="sxs-lookup"><span data-stu-id="a6caf-213">6000000000000000b</span></span>|<span data-ttu-id="a6caf-214">-0.267561918</span><span class="sxs-lookup"><span data-stu-id="a6caf-214">-0.267561918</span></span>|<span data-ttu-id="a6caf-215">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-215">7</span></span>|  
|<span data-ttu-id="a6caf-216">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-216">70000000200000000</span></span>|<span data-ttu-id="a6caf-217">6000000000000000c</span><span class="sxs-lookup"><span data-stu-id="a6caf-217">6000000000000000c</span></span>|<span data-ttu-id="a6caf-218">0.11069497</span><span class="sxs-lookup"><span data-stu-id="a6caf-218">0.11069497</span></span>|<span data-ttu-id="a6caf-219">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-219">7</span></span>|  
|<span data-ttu-id="a6caf-220">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-220">70000000200000000</span></span>|<span data-ttu-id="a6caf-221">6000000000000000d</span><span class="sxs-lookup"><span data-stu-id="a6caf-221">6000000000000000d</span></span>|<span data-ttu-id="a6caf-222">0.123757712</span><span class="sxs-lookup"><span data-stu-id="a6caf-222">0.123757712</span></span>|<span data-ttu-id="a6caf-223">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-223">7</span></span>|  
|<span data-ttu-id="a6caf-224">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-224">70000000200000000</span></span>|<span data-ttu-id="a6caf-225">6000000000000000e</span><span class="sxs-lookup"><span data-stu-id="a6caf-225">6000000000000000e</span></span>|<span data-ttu-id="a6caf-226">0.294565343</span><span class="sxs-lookup"><span data-stu-id="a6caf-226">0.294565343</span></span>|<span data-ttu-id="a6caf-227">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-227">7</span></span>|  
|<span data-ttu-id="a6caf-228">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-228">70000000200000000</span></span>|<span data-ttu-id="a6caf-229">6000000000000000f</span><span class="sxs-lookup"><span data-stu-id="a6caf-229">6000000000000000f</span></span>|<span data-ttu-id="a6caf-230">0.22245318</span><span class="sxs-lookup"><span data-stu-id="a6caf-230">0.22245318</span></span>|<span data-ttu-id="a6caf-231">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-231">7</span></span>|  
|<span data-ttu-id="a6caf-232">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a6caf-232">70000000200000000</span></span>||<span data-ttu-id="a6caf-233">0.188805045</span><span class="sxs-lookup"><span data-stu-id="a6caf-233">0.188805045</span></span>|<span data-ttu-id="a6caf-234">7</span><span class="sxs-lookup"><span data-stu-id="a6caf-234">7</span></span>|  
  
 <span data-ttu-id="a6caf-235">여기에 표시된 일부 결과는 신경망 모델 콘텐츠에서 숨겨진 노드가 입력 노드에 관련되는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-235">The partial results shown here demonstrate how the neural network model content relates the hidden node to the input nodes.</span></span>  
  
-   <span data-ttu-id="a6caf-236">숨겨진 계층에 있는 노드의 고유 이름은 항상 70000000으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-236">The unique names of nodes in the hidden layer always begin with 70000000.</span></span>  
  
-   <span data-ttu-id="a6caf-237">입력 계층에 있는 노드의 고유 이름은 항상 60000000으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-237">The unique names of nodes in the input layer always begin with 60000000.</span></span>  
  
 <span data-ttu-id="a6caf-238">따라서 이러한 결과를 보면 ID 70000000200000000으로 표시된 노드에는 6개의 다른 계수(VALUETYPE = 7)가 전달되었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-238">Thus, these results tell you that the node denoted by the ID 70000000200000000 had six different coefficients (VALUETYPE = 7) passed to it.</span></span> <span data-ttu-id="a6caf-239">계수 값은 ATTRIBUTE_VALUE 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-239">The values of the coefficients are in the ATTRIBUTE_VALUE column.</span></span> <span data-ttu-id="a6caf-240">ATTRIBUTE_NAME 열의 노드 ID를 사용하면 해당 계수가 어떤 입력 특성에 대한 계수인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-240">You can determine exactly which input attribute the coefficient is for by using the node ID in the ATTRIBUTE_NAME column.</span></span> <span data-ttu-id="a6caf-241">예를 들어 노드 ID 6000000000000000a는 입력 특성 및 값 `Day of Week = 'Tue.'` 를 참조합니다. 이 노드 ID를 사용하여 쿼리를 만들거나, [Microsoft 일반 콘텐츠 트리 뷰어](../microsoft-generic-content-tree-viewer-data-mining.md)를 사용하여 이 노드를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-241">For example, the node ID 6000000000000000a refers to input attribute and value, `Day of Week = 'Tue.'` You can use the node ID to create a query, or you can browse to the node by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="a6caf-242">마찬가지로 출력 계층(NODE_TYPE = 23)에 있는 노드의 NODE_DISTRIBUTION 테이블을 쿼리하면 각 출력 값의 계수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-242">Similarly, if you query the NODE_DISTRIBUTION table of the nodes in the output layer (NODE_TYPE = 23), you can see the coefficients for each output value.</span></span> <span data-ttu-id="a6caf-243">그러나 출력 계층에서 포인터는 다시 숨겨진 계층의 노드를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-243">However, in the output layer, the pointers refer back to the nodes of the hidden layer.</span></span> <span data-ttu-id="a6caf-244">자세한 내용은 [신경망 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)이라고 하는 마이닝 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-244">For more information, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="using-a-neural-network-model-to-make-predictions"></a><span data-ttu-id="a6caf-245">신경망 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="a6caf-245">Using a Neural Network Model to Make Predictions</span></span>  
 <span data-ttu-id="a6caf-246">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 분류와 회귀를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-246">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm supports both classification and regression.</span></span> <span data-ttu-id="a6caf-247">이러한 모델에서 예측 함수를 사용하여 새 데이터를 제공하고 단일 또는 일괄 처리 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-247">You can use prediction functions with these models to provide new data and create either singleton or batch predictions.</span></span>  
  
###  <a name="sample-query-5-creating-a-singleton-prediction"></a><a name="bkmk_Query5"></a><span data-ttu-id="a6caf-248">예제 쿼리 5: 단일 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="a6caf-248">Sample Query 5: Creating a Singleton Prediction</span></span>  
 <span data-ttu-id="a6caf-249">신경망 모델에 대한 예측 쿼리를 작성하는 가장 쉬운 방법은 **와** 의 데이터 마이닝 디자이너에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 마이닝 모델 예측 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭에 제공되는 예측 쿼리 작성기를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-249">The easiest way to build a prediction query on a neural network model is to use the Prediction Query Builder, available on the **Mining Prediction** tab of Data Mining Designer in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a6caf-250">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 뷰어에서 모델을 찾아서 관심 있는 특성을 필터링하고 추세를 확인한 다음 **마이닝 모델 예측** 탭으로 전환하여 쿼리를 만들고 해당 추세에 대한 새 값을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-250">You can browse the model in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer to filter attributes of interest and view trends, and then switch to the **Mining Prediction** tab to create a query and predict new values for those trends.</span></span>  
  
 <span data-ttu-id="a6caf-251">예를 들어 콜 센터 모델을 찾아서 주문량과 다른 특성 간의 상관 관계를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-251">For example, you can browse the call center model to view correlations between the order volumes and other attributes.</span></span> <span data-ttu-id="a6caf-252">이렇게 하려면 뷰어에서 모델을 열고 **입력**에 대해를 선택 **\<All>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-252">To do this, open the model in the viewer, and for **Input**, select **\<All>**.</span></span>  <span data-ttu-id="a6caf-253">그런 다음 **출력**에서 **Number of Orders**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-253">Next, for **Output**, select **Number of Orders**.</span></span> <span data-ttu-id="a6caf-254">**값 1**에서 가장 많은 주문 횟수를 나타내는 범위를 선택하고 **값 2**에서 가장 적은 주문 횟수를 나타내는 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-254">For **Value 1**, select the range that represents the most orders, and for **Value 2**, select the range that represents the fewest orders.</span></span> <span data-ttu-id="a6caf-255">그러면 해당 모델에서 주문량과 상관 관계가 있는 모든 특성을 한눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-255">You can then see at a glance all the attributes that the model correlates with order volume.</span></span>  
  
 <span data-ttu-id="a6caf-256">뷰어에서 결과를 보면 특정 요일에 주문량이 적고 운영자의 수를 늘릴수록 판매량이 많아지는 상관 관계가 있다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-256">By browsing the results in the viewer, you find that certain days of the week have low order volumes, and that an increase in the number of operators seems to be correlated with higher sales.</span></span> <span data-ttu-id="a6caf-257">그런 다음 모델에 대한 예측 쿼리를 사용하여 "가상 분석" 가설을 테스트하고 주문량이 적은 요일의 수준 2 운영자 수를 늘리면 주문이 늘어날지 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-257">You could then use a prediction query on the model to test a "what if" hypothesis and ask if increasing the number of level 2 operators on a low-volume day would increase orders.</span></span> <span data-ttu-id="a6caf-258">이렇게 하려면 다음과 같은 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-258">To do this, create a query such as the following:</span></span>  
  
```  
SELECT Predict([Call Center Default NN].[Number of Orders]) AS [Predicted Orders],  
PredictProbability([Call Center Default NN].[Number of Orders]) AS [Probability]  
FROM [Call Center Default NN]  
NATURAL PREDICTION JOIN   
(SELECT 'Tue.' AS [Day of Week],  
13 AS [Level 2 Operators]) AS t  
```  
  
 <span data-ttu-id="a6caf-259">결과 예:</span><span class="sxs-lookup"><span data-stu-id="a6caf-259">Example results:</span></span>  
  
|<span data-ttu-id="a6caf-260">Predicted Orders</span><span class="sxs-lookup"><span data-stu-id="a6caf-260">Predicted Orders</span></span>|<span data-ttu-id="a6caf-261">Probability</span><span class="sxs-lookup"><span data-stu-id="a6caf-261">Probability</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a6caf-262">364</span><span class="sxs-lookup"><span data-stu-id="a6caf-262">364</span></span>|<span data-ttu-id="a6caf-263">0.9532 ...</span><span class="sxs-lookup"><span data-stu-id="a6caf-263">0.9532...</span></span>|  
  
 <span data-ttu-id="a6caf-264">예측된 판매량은 화요일의 현재 판매량 범위보다 높으며 예측 확률은 매우 높습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-264">The predicted sales volume is higher than the current range of sales for Tuesday, and the probability of the prediction is very high.</span></span> <span data-ttu-id="a6caf-265">그러나 일괄 처리를 통해 여러 개의 예측을 만들어 모델에 대한 다양한 가설을 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-265">However, you might want to create multiple predictions by using a batch process to test a variety of hypotheses on the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6caf-266">Excel 2007용 데이터 마이닝 추가 기능에서는 로지스틱 회귀 마법사를 제공하기 때문에 서비스 등급을 특정 교대조에 대한 대상 수준으로 개선하는 데 필요한 두 번째 수준의 전화 상담원의 수와 같은 복잡한 질문에 보다 쉽게 대답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-266">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be needed to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="a6caf-267">데이터 마이닝 추가 기능은 무료로 다운로드할 수 있으며 신경망 및/또는 로지스틱 회귀 알고리즘을 기반으로 하는 마법사를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-267">The data mining add-ins are a free download, and include wizards that are based on the neural network and/or logistic regression algorithms.</span></span> <span data-ttu-id="a6caf-268">자세한 내용은 [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) (Office 2007용 데이터 마이닝 추가 기능) 웹 사이트를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6caf-268">For more information, see the [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) Web site.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="a6caf-269">예측 함수 목록</span><span class="sxs-lookup"><span data-stu-id="a6caf-269">List of Prediction Functions</span></span>  
 <span data-ttu-id="a6caf-270">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-270">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="a6caf-271">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘에만 사용되는 예측 함수는 없지만 이 알고리즘은 다음 표에 나열된 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-271">There are no prediction functions that are specific to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm; however, the algorithm supports the functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6caf-272">예측 함수</span><span class="sxs-lookup"><span data-stu-id="a6caf-272">Prediction Function</span></span>|<span data-ttu-id="a6caf-273">사용</span><span class="sxs-lookup"><span data-stu-id="a6caf-273">Usage</span></span>|  
|[<span data-ttu-id="a6caf-274">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-274">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="a6caf-275">한 노드가 신경망 그래프에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-275">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="a6caf-276">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-276">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="a6caf-277">가중치 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-277">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="a6caf-278">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-278">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="a6caf-279">현재 예측된 값과 관련 된 값의 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-279">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="a6caf-280">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-280">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="a6caf-281">예측 값의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-281">Returns variance for the predicted value.</span></span>|  
|[<span data-ttu-id="a6caf-282">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-282">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="a6caf-283">예측 값의 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-283">Returns probability  for the predicted value.</span></span>|  
|[<span data-ttu-id="a6caf-284">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-284">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="a6caf-285">예측 값의 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-285">Returns the standard deviance for the predicted value.</span></span>|  
|[<span data-ttu-id="a6caf-286">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-286">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="a6caf-287">신경망 및 로지스틱 회귀 모델의 경우에는 모델 전체에 대한 학습 집합의 크기를 나타내는 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a6caf-287">For neural network and logistic regression models, returns a single value that represents the size of the training set for the entire model.</span></span>|  
  
 <span data-ttu-id="a6caf-288">특정 함수의 구문은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6caf-288">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6caf-289">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6caf-289">See Also</span></span>  
 <span data-ttu-id="a6caf-290">[Microsoft 신경망 알고리즘](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a6caf-290">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="a6caf-291">[Microsoft 신경망 알고리즘 기술 참조](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a6caf-291">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="a6caf-292">[신경망 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a6caf-292">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="a6caf-293">5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="a6caf-293">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
