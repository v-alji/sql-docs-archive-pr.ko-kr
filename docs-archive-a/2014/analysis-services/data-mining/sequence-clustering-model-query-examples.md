---
title: 시퀀스 클러스터링 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- sequence clustering algorithms [Analysis Services]
- content queries [DMX]
- sequence [Analysis Services]
ms.assetid: 64bebcdc-70ab-43fb-8d40-57672a126602
author: minewiskan
ms.author: owend
ms.openlocfilehash: d56924f27f7986861895cf4fff21fa758cc47070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639099"
---
# <a name="sequence-clustering-model-query-examples"></a><span data-ttu-id="6dbaa-102">시퀀스 클러스터링 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="6dbaa-102">Sequence Clustering Model Query Examples</span></span>
  <span data-ttu-id="6dbaa-103">데이터 마이닝 모델에 대한 쿼리를 만들 때 모델에 저장된 정보에 대한 세부 정보를 제공하는 내용 쿼리를 만들거나, 모델의 패턴을 사용하여 사용자가 제공한 새 데이터를 기반으로 예측을 만드는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-103">When you create a query against a data mining model, you can create either a content query, which provides details about the information stored in the model, or you can create a prediction query, which uses the patterns in the model to make predictions based on new data that you provide.</span></span> <span data-ttu-id="6dbaa-104">시퀀스 클러스터링 모델의 경우 내용 쿼리는 일반적으로 발견된 클러스터나 해당 클러스터 내의 전환에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-104">For a sequence clustering model, content queries typically provide additional details about the clusters that were found, or the transitions within those clusters.</span></span> <span data-ttu-id="6dbaa-105">쿼리를 사용하여 모델에 대한 메타데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="6dbaa-106">시퀀스 클러스터링 모델에 대한 예측 쿼리는 일반적으로 시퀀스와 전환, 모델에 포함된 비시퀀스 특성, 또는 시퀀스 특성과 비시퀀스 특성의 조합 중 하나에 따라 권장 구성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-106">Prediction queries on a sequence clustering model typically make recommendations based either on the sequences and transitions, on non-sequence attributes that were included in the model, or on a combination of sequence and non-sequence attributes.</span></span>  
  
 <span data-ttu-id="6dbaa-107">이 섹션에서는 Microsoft 시퀀스 클러스터링 알고리즘 기반의 모델에 대해 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-107">This section explains how to create queries for models that are based on the Microsoft Sequence Clustering algorithm.</span></span> <span data-ttu-id="6dbaa-108">쿼리를 만드는 방법에 대한 일반적인 내용은 [데이터 마이닝 쿼리](data-mining-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-108">For general information about creating queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="6dbaa-109">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="6dbaa-109">**Content Queries**</span></span>  
  
 [<span data-ttu-id="6dbaa-110">데이터 마이닝 스키마 행 집합을 사용하여 모델 매개 변수 반환</span><span class="sxs-lookup"><span data-stu-id="6dbaa-110">Using the Data Mining Schema Rowset to return model parameters</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="6dbaa-111">상태에 대한 시퀀스 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6dbaa-111">Getting a list of sequences for a state</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="6dbaa-112">시스템 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="6dbaa-112">Using system stored procedures</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="6dbaa-113">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="6dbaa-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="6dbaa-114">다음 상태 예측</span><span class="sxs-lookup"><span data-stu-id="6dbaa-114">Predict next state or states</span></span>](#bkmk_Query4)  
  
##  <a name="finding-information-about-the-sequence-clustering-model"></a><a name="bkmk_ContentQueries"></a><span data-ttu-id="6dbaa-115">시퀀스 클러스터링 모델에 대 한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="6dbaa-115">Finding Information about the Sequence Clustering Model</span></span>  
 <span data-ttu-id="6dbaa-116">마이닝 모델의 콘텐츠에 대한 의미 있는 쿼리를 만들려면 모델 콘텐츠의 구조와 노드 유형에 따라 저장되는 정보의 종류를 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-116">To create meaningful queries on the content of a mining model, you must understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="6dbaa-117">자세한 내용은 [시퀀스 클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-sequence-clustering-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-117">For more information, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-return-model-parameters"></a><a name="bkmk_Query1"></a><span data-ttu-id="6dbaa-118">예제 쿼리 1: 데이터 마이닝 스키마 행 집합을 사용 하 여 모델 매개 변수 반환</span><span class="sxs-lookup"><span data-stu-id="6dbaa-118">Sample Query 1: Using the Data Mining Schema Rowset to Return Model Parameters</span></span>  
 <span data-ttu-id="6dbaa-119">데이터 마이닝 스키마 행 집합을 쿼리하면 기본적인 메타데이터, 모델이 만들어진 날짜 및 시간, 모델이 마지막으로 처리된 날짜 및 시간, 모델의 기반이 되는 마이닝 구조의 이름, 예측 가능한 특성으로 사용된 열 등을 비롯하여 모델에 대한 다양한 종류의 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-119">By querying the data mining schema rowset, you can find various kinds of information about the model, including basic metadata, the date and time that the model was created and last processed, the name of the mining structure that the model is based on, and the column used as the predictable attribute.</span></span>  
  
 <span data-ttu-id="6dbaa-120">다음 쿼리는 `[Sequence Clustering]`모델의 작성 및 학습에 사용된 매개 변수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-120">The following query returns the parameters that were used to build and train the model, `[Sequence Clustering]`.</span></span> <span data-ttu-id="6dbaa-121">이 모델은 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)의 5단원에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-121">You can create this model in Lesson 5 of the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Sequence Clustering'  
```  
  
 <span data-ttu-id="6dbaa-122">결과 예:</span><span class="sxs-lookup"><span data-stu-id="6dbaa-122">Example results:</span></span>  
  
|<span data-ttu-id="6dbaa-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6dbaa-123">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="6dbaa-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span><span class="sxs-lookup"><span data-stu-id="6dbaa-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span></span>|  
  
 <span data-ttu-id="6dbaa-125">이 모델은 CLUSTER_COUNT에 기본값 10을 사용하여 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-125">Note that this model was built by using the default value of 10 for CLUSTER_COUNT.</span></span> <span data-ttu-id="6dbaa-126">CLUSTER_COUNT에 클러스터 수로 0이 아닌 숫자를 지정하면 알고리즘에서는 이 숫자를 찾을 클러스터의 대략적인 개수에 대한 힌트로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-126">When you specify a non-zero number of clusters for CLUSTER_COUNT, the algorithm treats this number as a hint for the approximate number of clusters to find.</span></span> <span data-ttu-id="6dbaa-127">그러나 분석 과정에서 알고리즘이 찾는 클러스터 수는 그보다 많을 수도 있고 적을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-127">However, in the process of analysis, the algorithm may find more or fewer clusters.</span></span> <span data-ttu-id="6dbaa-128">이 예의 경우에 알고리즘은 학습 데이터에 가장 적합한 클러스터를 15개 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-128">In this case, the algorithm found that 15 clusters best fit the training data.</span></span> <span data-ttu-id="6dbaa-129">따라서 완성된 모델의 매개 변수 값 목록에서는 모델을 만들 때 전달된 값이 아니라 알고리즘에 의해 결정된 클러스터 수가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-129">Therefore, the list of parameter values for the completed model reports the count of clusters as determined by the algorithm, not the value passed in when creating the model.</span></span>  
  
 <span data-ttu-id="6dbaa-130">단순히 알고리즘에서 최적의 클러스터 수를 결정하도록 하는 방법과 이 방법에는 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-130">How does this behavior differ from letting the algorithm determine the best number of clusters?</span></span> <span data-ttu-id="6dbaa-131">시험 삼아 이와 동일한 데이터를 사용하되 CLUSTER_COUNT는 0으로 설정하여 클러스터링 모델을 하나 더 만들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-131">As an experiment, you can create another clustering model that uses this same data, but set CLUSTER_COUNT to 0.</span></span> <span data-ttu-id="6dbaa-132">이 경우에는 알고리즘에서 찾는 클러스터 수가 32개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-132">When you do this, the algorithm detects 32 clusters.</span></span> <span data-ttu-id="6dbaa-133">따라서 CLUSTER_COUNT에 기본값 10을 사용하면 결과의 개수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-133">Therefore, by using the default value of 10 for CLUSTER_COUNT, you constrain the number of results.</span></span>  
  
 <span data-ttu-id="6dbaa-134">클러스터 수를 줄이면 대부분의 사용자가 데이터의 그룹화를 쉽게 찾아보고 이해할 수 있으므로 기본적으로 값 10이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-134">The value of 10 is used by default because reducing the number of clusters makes it easier for most people to browse and understand groupings in the data.</span></span> <span data-ttu-id="6dbaa-135">그러나 각 모델 및 데이터 집합은 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-135">However, each model and set of data is different.</span></span> <span data-ttu-id="6dbaa-136">클러스터 수를 다르게 하여 시험해 보면 어떤 매개 변수 값이 가장 정확한 모델을 생성하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-136">You may wish to experiment with different numbers of clusters to see which parameter value yields the most accurate model.</span></span>  
  
###  <a name="sample-query-2-getting-a-list-of-sequences-for-a-state"></a><a name="bkmk_Query2"></a><span data-ttu-id="6dbaa-137">예제 쿼리 2: 상태에 대 한 시퀀스 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6dbaa-137">Sample Query 2: Getting a List of Sequences for a State</span></span>  
 <span data-ttu-id="6dbaa-138">마이닝 모델 콘텐츠에는 학습 데이터에서 찾은 시퀀스가 첫 번째 상태에 관련된 모든 두 번째 상태의 목록이 결합되어 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-138">The mining model content stores the sequences that are found in the training data as a first state coupled with a list of all related second states.</span></span> <span data-ttu-id="6dbaa-139">첫 번째 상태는 시퀀스의 레이블로 사용되며, 관련된 두 번째 상태는 전환이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-139">The first state is used as the label for the sequence, and the related second states are called transitions.</span></span>  
  
 <span data-ttu-id="6dbaa-140">예를 들어 다음 쿼리는 시퀀스가 클러스터로 그룹화되기 전에 모델의 첫 번째 상태가 모두 들어 있는 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-140">For example, the following query returns the complete list of first states in the model, before the sequences are grouped into clusters.</span></span>  <span data-ttu-id="6dbaa-141">모델 루트 노드를 부모(PARENT_UNIQUE_NAME = 0)로 갖는 시퀀스(NODE_TYPE = 13) 목록을 반환하면 이 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-141">You can get this list by returning the list of sequences (NODE_TYPE = 13) that have the model root node as parent (PARENT_UNIQUE_NAME = 0).</span></span> <span data-ttu-id="6dbaa-142">FLATTENED 키워드는 결과를 읽기 쉽게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-142">The FLATTENED keyword makes the results easier to read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6dbaa-143">열 이름 PARENT_UNIQUE_NAME, Support 및 Probability는 대괄호로 묶어 동일한 이름의 예약 키워드와 구별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-143">The name of the columns, PARENT_UNIQUE_NAME, Support, and Probability must be enclosed in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME,  
(SELECT ATTRIBUTE_VALUE AS [Product 1],  
[Support] AS [Sequence Support],   
[Probability] AS [Sequence Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_TYPE = 13  
AND [PARENT_UNIQUE_NAME] = 0  
```  
  
 <span data-ttu-id="6dbaa-144">일부 결과:</span><span class="sxs-lookup"><span data-stu-id="6dbaa-144">Partial results:</span></span>  
  
|<span data-ttu-id="6dbaa-145">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="6dbaa-145">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="6dbaa-146">Product 1</span><span class="sxs-lookup"><span data-stu-id="6dbaa-146">Product 1</span></span>|<span data-ttu-id="6dbaa-147">시퀀스 지지도</span><span class="sxs-lookup"><span data-stu-id="6dbaa-147">Sequence Support</span></span>|<span data-ttu-id="6dbaa-148">시퀀스 확률</span><span class="sxs-lookup"><span data-stu-id="6dbaa-148">Sequence Probability</span></span>|  
|------------------------|---------------|----------------------|--------------------------|  
|<span data-ttu-id="6dbaa-149">1081327</span><span class="sxs-lookup"><span data-stu-id="6dbaa-149">1081327</span></span>|<span data-ttu-id="6dbaa-150">Missing</span><span class="sxs-lookup"><span data-stu-id="6dbaa-150">Missing</span></span>|<span data-ttu-id="6dbaa-151">0</span><span class="sxs-lookup"><span data-stu-id="6dbaa-151">0</span></span>|#######|  
|<span data-ttu-id="6dbaa-152">1081327</span><span class="sxs-lookup"><span data-stu-id="6dbaa-152">1081327</span></span>|<span data-ttu-id="6dbaa-153">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="6dbaa-153">All-Purpose Bike Stand</span></span>|<span data-ttu-id="6dbaa-154">17</span><span class="sxs-lookup"><span data-stu-id="6dbaa-154">17</span></span>|<span data-ttu-id="6dbaa-155">0.00111</span><span class="sxs-lookup"><span data-stu-id="6dbaa-155">0.00111</span></span>|  
|<span data-ttu-id="6dbaa-156">1081327</span><span class="sxs-lookup"><span data-stu-id="6dbaa-156">1081327</span></span>|<span data-ttu-id="6dbaa-157">Bike Wash</span><span class="sxs-lookup"><span data-stu-id="6dbaa-157">Bike Wash</span></span>|<span data-ttu-id="6dbaa-158">64</span><span class="sxs-lookup"><span data-stu-id="6dbaa-158">64</span></span>|<span data-ttu-id="6dbaa-159">0.00418</span><span class="sxs-lookup"><span data-stu-id="6dbaa-159">0.00418</span></span>|  
|<span data-ttu-id="6dbaa-160">1081327</span><span class="sxs-lookup"><span data-stu-id="6dbaa-160">1081327</span></span>|<span data-ttu-id="6dbaa-161">(4-36행 생략)</span><span class="sxs-lookup"><span data-stu-id="6dbaa-161">(rows 4-36 omitted)</span></span>|||  
|<span data-ttu-id="6dbaa-162">1081327</span><span class="sxs-lookup"><span data-stu-id="6dbaa-162">1081327</span></span>|<span data-ttu-id="6dbaa-163">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="6dbaa-163">Women's Mountain Shorts</span></span>|<span data-ttu-id="6dbaa-164">506</span><span class="sxs-lookup"><span data-stu-id="6dbaa-164">506</span></span>|<span data-ttu-id="6dbaa-165">0.03307</span><span class="sxs-lookup"><span data-stu-id="6dbaa-165">0.03307</span></span>|  
  
 <span data-ttu-id="6dbaa-166">모델의 시퀀스 목록은 항상 알파벳 오름차순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-166">The list of sequences in the model is always sorted alphabetically in ascending order.</span></span> <span data-ttu-id="6dbaa-167">시퀀스의 순서 번호를 보면 관련된 전환을 알 수 있으므로 시퀀스의 순서는 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-167">The ordering of the sequences is important because you can find the related transitions by looking at the order number of the sequence.</span></span> <span data-ttu-id="6dbaa-168">`Missing` 값은 항상 전환 0입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-168">The `Missing` value is always transition 0.</span></span>  
  
 <span data-ttu-id="6dbaa-169">예를 들어 앞의 결과에서 "Women's Mountain Shorts" 제품은 모델에서 시퀀스 번호 37에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-169">For example, in the previous results, the product "Women's Mountain Shorts" is the sequence number 37 in the model.</span></span> <span data-ttu-id="6dbaa-170">이 정보를 사용하여 "Women's Mountain Shorts" 다음에 구매된 모든 제품을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-170">You can use that information to view all of the products that were ever purchased after "Women's Mountain Shorts."</span></span>  
  
 <span data-ttu-id="6dbaa-171">이렇게 하려면 먼저 이전 쿼리에서 NODE_UNIQUE_NAME에 대해 반환된 값을 참조하여 해당 모델의 모든 시퀀스가 들어 있는 노드의 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-171">To do this, first, you reference the value returned for NODE_UNIQUE_NAME in the previous query, to get the ID of the node that contains all sequences for the model.</span></span> <span data-ttu-id="6dbaa-172">이 값을 쿼리에 부모 노드의 ID로 전달하여 이 노드에 포함된 전환만 가져옵니다. 여기에는 해당 모델의 전체 시퀀스 목록이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-172">You pass this value to the query as the ID of the parent node, to get only the transitions included in this node, which happens to contain a list of al sequences for the model.</span></span> <span data-ttu-id="6dbaa-173">그러나 특정 클러스터의 전환 목록을 보려면 클러스터 노드의 ID를 전달하고 해당 클러스터와 연결된 시퀀스만 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-173">However, if you wanted to see the list of transitions for a specific cluster, you could pass in the ID of the cluster node, and see only the sequences associated with that cluster.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_DESCRIPTION = 'Transition row for sequence state 37'  
AND [PARENT_UNIQUE_NAME] = '1081327'  
```  
  
 <span data-ttu-id="6dbaa-174">결과 예:</span><span class="sxs-lookup"><span data-stu-id="6dbaa-174">Example results:</span></span>  
  
|<span data-ttu-id="6dbaa-175">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="6dbaa-175">NODE_UNIQUE_NAME</span></span>|  
|------------------------|  
|<span data-ttu-id="6dbaa-176">1081365</span><span class="sxs-lookup"><span data-stu-id="6dbaa-176">1081365</span></span>|  
  
 <span data-ttu-id="6dbaa-177">이 ID가 나타내는 노드에는 "Women's Mountain Shorts" 제품 다음에 오는 시퀀스의 목록이 지지도 및 확률 값과 함께 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-177">The node represented by this ID contains a list of the sequences that follow the "Women's Mountain Shorts" product, together with the support and probability values.</span></span>  
  
```  
SELECT FLATTENED  
(SELECT ATTRIBUTE_VALUE AS Product2,  
[Support] AS [P2 Support],  
[Probability] AS [P2 Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_UNIQUE_NAME = '1081365'  
```  
  
 <span data-ttu-id="6dbaa-178">결과 예:</span><span class="sxs-lookup"><span data-stu-id="6dbaa-178">Example results:</span></span>  
  
|<span data-ttu-id="6dbaa-179">t.Product2</span><span class="sxs-lookup"><span data-stu-id="6dbaa-179">t.Product2</span></span>|<span data-ttu-id="6dbaa-180">t.P2 Support</span><span class="sxs-lookup"><span data-stu-id="6dbaa-180">t.P2 Support</span></span>|<span data-ttu-id="6dbaa-181">t.P2 Probability</span><span class="sxs-lookup"><span data-stu-id="6dbaa-181">t.P2 Probability</span></span>|  
|----------------|------------------|----------------------|  
|<span data-ttu-id="6dbaa-182">Missing</span><span class="sxs-lookup"><span data-stu-id="6dbaa-182">Missing</span></span>|<span data-ttu-id="6dbaa-183">230.7419</span><span class="sxs-lookup"><span data-stu-id="6dbaa-183">230.7419</span></span>|<span data-ttu-id="6dbaa-184">0.456012</span><span class="sxs-lookup"><span data-stu-id="6dbaa-184">0.456012</span></span>|  
|<span data-ttu-id="6dbaa-185">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="6dbaa-185">Classic Vest</span></span>|<span data-ttu-id="6dbaa-186">8.16129</span><span class="sxs-lookup"><span data-stu-id="6dbaa-186">8.16129</span></span>|<span data-ttu-id="6dbaa-187">0.016129</span><span class="sxs-lookup"><span data-stu-id="6dbaa-187">0.016129</span></span>|  
|<span data-ttu-id="6dbaa-188">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="6dbaa-188">Cycling Cap</span></span>|<span data-ttu-id="6dbaa-189">60.83871</span><span class="sxs-lookup"><span data-stu-id="6dbaa-189">60.83871</span></span>|<span data-ttu-id="6dbaa-190">0.120235</span><span class="sxs-lookup"><span data-stu-id="6dbaa-190">0.120235</span></span>|  
|<span data-ttu-id="6dbaa-191">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="6dbaa-191">Half-Finger Gloves</span></span>|<span data-ttu-id="6dbaa-192">30.41935</span><span class="sxs-lookup"><span data-stu-id="6dbaa-192">30.41935</span></span>|<span data-ttu-id="6dbaa-193">0.060117</span><span class="sxs-lookup"><span data-stu-id="6dbaa-193">0.060117</span></span>|  
|<span data-ttu-id="6dbaa-194">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="6dbaa-194">Long-Sleeve Logo Jersey</span></span>|<span data-ttu-id="6dbaa-195">86.80645</span><span class="sxs-lookup"><span data-stu-id="6dbaa-195">86.80645</span></span>|<span data-ttu-id="6dbaa-196">0.171554</span><span class="sxs-lookup"><span data-stu-id="6dbaa-196">0.171554</span></span>|  
|<span data-ttu-id="6dbaa-197">Racing Socks</span><span class="sxs-lookup"><span data-stu-id="6dbaa-197">Racing Socks</span></span>|<span data-ttu-id="6dbaa-198">28.93548</span><span class="sxs-lookup"><span data-stu-id="6dbaa-198">28.93548</span></span>|<span data-ttu-id="6dbaa-199">0.057185</span><span class="sxs-lookup"><span data-stu-id="6dbaa-199">0.057185</span></span>|  
|<span data-ttu-id="6dbaa-200">Short-Sleeve Classic Jersey</span><span class="sxs-lookup"><span data-stu-id="6dbaa-200">Short-Sleeve Classic Jersey</span></span>|<span data-ttu-id="6dbaa-201">60.09677</span><span class="sxs-lookup"><span data-stu-id="6dbaa-201">60.09677</span></span>|<span data-ttu-id="6dbaa-202">0.118768</span><span class="sxs-lookup"><span data-stu-id="6dbaa-202">0.118768</span></span>|  
  
 <span data-ttu-id="6dbaa-203">해당 모델에서 "Women's Mountain Shorts"와 관련된 다양한 시퀀스의 지지도는 506입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-203">Note that support for the various sequences related to Women's Mountain Shorts is 506 in the model.</span></span> <span data-ttu-id="6dbaa-204">전환의 지지도 값도 합이 506입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-204">The support values for the transitions also add up to 506.</span></span> <span data-ttu-id="6dbaa-205">그러나 이 숫자는 정수가 아니므로 지지도가 단순히 각 전환을 포함하는 사례 수를 나타낼 것으로 예상한 경우에는 이것이 약간 이상하게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-205">However, the numbers are not whole numbers, which seems a bit odd if you expect support to simply represent a count of cases that contain each transition.</span></span> <span data-ttu-id="6dbaa-206">그러나 클러스터 생성 방법에서는 부분 멤버 자격을 계산하므로 클러스터 내에 있는 모든 전환의 확률은 해당 클러스터에 속할 확률에 따라 가중치가 적용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-206">However, because the method for creating clusters calculates partial membership, the probability of any transition within a cluster must be weighted by its probability of belonging to that particular cluster.</span></span>  
  
 <span data-ttu-id="6dbaa-207">예를 들어 네 개의 클러스터가 있고 특정 시퀀스가 클러스터 1, 클러스터 2, 클러스터 3 및 클러스터 4에 속할 가능성이 각각 40%, 30%, 20% 및 10%라면</span><span class="sxs-lookup"><span data-stu-id="6dbaa-207">For example, if there are four clusters, a particular sequence might have a 40% chance of belonging to cluster 1, a 30% chance of belonging to cluster 2, a 20% chance of belonging to cluster 3, and a 10% chance of belonging to cluster 4.</span></span> <span data-ttu-id="6dbaa-208">알고리즘은 해당 전환이 속할 가능성이 가장 큰 클러스터를 확인한 후 클러스터의 이전 확률에 따라 클러스터 내의 확률에 가중치를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-208">After the algorithm determines the cluster that the transition is mostly likely to belong to, it weights the probabilities within the cluster by the cluster prior probability.</span></span>  
  
###  <a name="sample-query-3-using-system-stored-procedures"></a><a name="bkmk_Query3"></a><span data-ttu-id="6dbaa-209">예제 쿼리 3: 시스템 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="6dbaa-209">Sample Query 3: Using System Stored Procedures</span></span>  
 <span data-ttu-id="6dbaa-210">앞의 쿼리 예제에서는 모델에 저장된 정보가 복잡하며 필요한 정보를 얻으려면 여러 쿼리를 만들어야 할 수도 있다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-210">You can see from these query samples that the information stored in the model is complex, and that you might need to create multiple queries to get the information that you need.</span></span> <span data-ttu-id="6dbaa-211">그러나 Microsoft 시퀀스 클러스터링 뷰어에서는 시퀀스 클러스터링 모델에 들어 있는 정보를 그래픽 방식으로 찾아보기 위한 강력한 여러 도구를 제공하며, 이 뷰어를 사용하여 모델을 쿼리하고 드릴다운할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-211">However, the Microsoft Sequence Clustering viewer provides a powerful set of tools for graphically browsing the information contained in a sequence clustering model, and you can also use the viewer to query and drill down into the model.</span></span>  
  
 <span data-ttu-id="6dbaa-212">대부분의 경우 Microsoft 시퀀스 클러스터링 뷰어에서 보여 주는 정보는 Analysis Services 시스템 저장 프로시저를 사용하여 모델을 쿼리하는 방법으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-212">In most cases, the information that is presented in the Microsoft Sequence Clustering viewer is created by using Analysis Services system stored procedures to query the model.</span></span> <span data-ttu-id="6dbaa-213">모델 콘텐츠에 대한 DMX(Data Mining Extensions) 쿼리를 작성하여 동일한 정보를 검색할 수도 있지만 Analysis Services 시스템 저장 프로시저를 사용하면 모델을 보다 편리하게 탐색하거나 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-213">You can write Data Mining Extensions (DMX) queries against the model content to retrieve the same information, but the Analysis Services system stored procedures provide a convenient shortcut when for exploration or for testing models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6dbaa-214">시스템 저장 프로시저는 Analysis Services 서버와의 상호 작용을 위해 Microsoft에서 제공하는 클라이언트와 서버에서 내부 처리에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-214">System stored procedures are used for internal processing by the server and by the clients that Microsoft provides for interacting with the Analysis Services server.</span></span> <span data-ttu-id="6dbaa-215">따라서 Microsoft는 언제든지 시스템 저장 프로시저를 변경할 권리를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-215">Therefore, Microsoft reserves the right to change them at any time.</span></span> <span data-ttu-id="6dbaa-216">여기에서는 사용자의 편의를 위해 시스템 저장 프로시저에 대해 설명하지만 프로덕션 환경에서는 시스템 저장 프로시저가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-216">Although they are described here for your convenience, we do not support their use in a production environment.</span></span> <span data-ttu-id="6dbaa-217">프로덕션 환경의 안정성과 호환성을 보장하려면 항상 DMX를 사용하여 직접 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-217">To ensure stability and compatibility in a production environment, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="6dbaa-218">이 섹션에서는 시스템 저장 프로시저를 사용하여 시퀀스 클러스터링 모델에 대한 쿼리를 만드는 방법을 보여 주는 몇 가지 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-218">This section provides some samples of how to use the system stored procedures to create queries against a sequence clustering model:</span></span>  
  
#### <a name="cluster-profiles-and-sample-cases"></a><span data-ttu-id="6dbaa-219">클러스터 프로필 및 예제 사례</span><span class="sxs-lookup"><span data-stu-id="6dbaa-219">Cluster Profiles and Sample Cases</span></span>  
 <span data-ttu-id="6dbaa-220">클러스터 프로필 탭에서는 모델에 있는 클러스터의 목록과 각 클러스터의 크기, 그리고 클러스터에 포함된 상태를 나타내는 히스토그램을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-220">The Cluster Profiles tab shows you a list of the clusters in the model, the size of each cluster, and a histogram that indicates the states included in the cluster.</span></span> <span data-ttu-id="6dbaa-221">쿼리에서 비슷한 정보를 검색하는 데 사용할 수 있는 시스템 저장 프로시저는 다음 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-221">There are two system stored procedures that you can use in queries to retrieve similar information:</span></span>  
  
-   <span data-ttu-id="6dbaa-222">`GetClusterProfile` 은(는) 클러스터의 특성과 해당 클러스터의 NODE_DISTRIBUTION 테이블에서 찾은 모든 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-222">`GetClusterProfile` returns the characteristics of the cluster, with all the information that is found in the NODE_DISTRIBUTION table for the cluster.</span></span>  
  
-   <span data-ttu-id="6dbaa-223">`GetNodeGraph` - 시퀀스 클러스터링 보기의 첫 번째 탭에서 표시되는 내용에 해당하는 클러스터의 수학적 그래프 표현을 생성하는 데 사용할 수 있는 노드 및 가장자리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-223">`GetNodeGraph` returns nodes and edges that can be used to construct a mathematical graph representation of the clusters, corresponding to what you see on the first tab of the Sequence Clustering view.</span></span> <span data-ttu-id="6dbaa-224">노드는 클러스터이고 가장자리는 가중치 또는 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-224">The nodes are clusters, and the edges represent weights or strength.</span></span>  
  
 <span data-ttu-id="6dbaa-225">다음 예에서는 시스템 저장 프로시저인 `GetClusterProfiles`를 사용하여 각각의 프로필이 있는 모델 내의 모든 클러스터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-225">The following example illustrates how to use the system stored procedure, `GetClusterProfiles`, to return all of the clusters in the model, with their respective profiles.</span></span> <span data-ttu-id="6dbaa-226">이 저장 프로시저는 모델의 전체 프로필 집합을 반환하는 일련의 DMX 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-226">This stored procedure executes a series of DMX statements that return the complete set of profiles in the model.</span></span> <span data-ttu-id="6dbaa-227">그러나 이 저장 프로시저를 사용하려면 모델의 주소를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-227">However, to use this stored procedure you must know the address of the model.</span></span>  
  
 `CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('Sequence Clustering', 2147483647, 0)`  
  
 <span data-ttu-id="6dbaa-228">다음 예에서는 시스템 저장 프로시저 `GetNodeGraph`를 사용하고 클러스터 ID를 지정하여 특정 클러스터(클러스터 12)의 프로필을 검색하는 방법을 보여 줍니다. 클러스터 ID는 일반적으로 클러스터 이름의 숫자와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-228">The following example illustrates how to retrieve the profile for a specific cluster, Cluster 12, by using the system stored procedure `GetNodeGraph`, and specifying the cluster ID, which is usually the same as the number in the cluster name.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','12',0)  
```  
  
 <span data-ttu-id="6dbaa-229">다음 쿼리에서와 같이 클러스터 ID를 지정하지 않으면 `GetNodeGraph` 는 모든 클러스터 프로필의 정렬되고 결합된 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-229">If you omit the cluster ID, as shown in the following query, `GetNodeGraph` returns an ordered, flattened list of all cluster profiles:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','',0)  
```  
  
 <span data-ttu-id="6dbaa-230">**클러스터 프로필** 탭에는 모델 예제 사례의 히스토그램도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-230">The **Cluster Profile** tab also displays a histogram of model sample cases.</span></span> <span data-ttu-id="6dbaa-231">이러한 예제 사례는 모델의 이상적인 사례를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-231">These sample cases represent the idealized cases for the model.</span></span> <span data-ttu-id="6dbaa-232">이 사례는 모델에 학습 데이터와 동일한 방식으로 저장되지 않으므로 모델의 예제 사례를 검색하려면 특수한 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-232">These cases are not stored in the model the same way that the training data is; you must use a special syntax to retrieve the sample cases for the model.</span></span>  
  
```  
SELECT * FROM [Sequence Clustering].SAMPLE_CASES WHERE IsInNode('12')  
```  
  
 <span data-ttu-id="6dbaa-233">자세한 내용은 [SELECT FROM &#60;model&#62;.SAMPLE_CASES&#40;DMX&#41;](/sql/dmx/select-from-model-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-233">For more information, see [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](/sql/dmx/select-from-model-dmx).</span></span>  
  
#### <a name="cluster-characteristics-and-cluster-discrimination"></a><span data-ttu-id="6dbaa-234">클러스터 특징 및 클러스터 차원</span><span class="sxs-lookup"><span data-stu-id="6dbaa-234">Cluster Characteristics and Cluster Discrimination</span></span>  
 <span data-ttu-id="6dbaa-235">**클러스터 특징** 탭에는 각 클러스터의 주요 특성이 확률에 따라 순위가 지정되어 요약됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-235">The **Cluster Characteristics** tab summarizes the main attributes of each cluster, ranked by probability.</span></span> <span data-ttu-id="6dbaa-236">여기에서 클러스터에 속하는 사례의 수와 클러스터의 사례 분포를 확인할 수 있습니다. 각 특징에는 특정 지지도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-236">You can find out how many cases belong to a cluster, and what the distribution of cases is like in the cluster: Each characteristic has certain support.</span></span> <span data-ttu-id="6dbaa-237">특정 클러스터의 특징을 보려면 해당 클러스터의 ID를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-237">To see the characteristics of a particular cluster, you must know the ID of the cluster.</span></span>  
  
 <span data-ttu-id="6dbaa-238">다음 예에서는 시스템 저장 프로시저인 `GetClusterCharacteristics`를 사용하여 클러스터 12의 특징 중 확률 점수가 지정된 임계값 0.0005를 초과하는 모든 특징을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-238">The following examples uses the system stored procedure, `GetClusterCharacteristics`, to return all the characteristics of Cluster 12 that have a probability score over the specified threshold of 0.0005.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','12',0.0005)  
```  
  
 <span data-ttu-id="6dbaa-239">모든 클러스터의 특징을 반환하려면 클러스터 ID를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-239">To return the characteristics of all clusters, you can leave the cluster ID empty.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','',0.0005)  
```  
  
 <span data-ttu-id="6dbaa-240">다음 예에서는 시스템 저장 프로시저 `GetClusterDiscrimination` 을 호출하여 클러스터 1과 클러스터 12의 특징을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-240">The following example calls the system stored procedure `GetClusterDiscrimination` to compare the characteristics of Cluster 1 and Cluster 12.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('Sequence Clustering','1','12',0.0005,true)  
```  
  
 <span data-ttu-id="6dbaa-241">DMX로 직접 쿼리를 작성하여 두 클러스터를 비교하거나 클러스터를 나머지 클러스터와 비교하려면 먼저 특징 집합 하나를 검색한 다음 관심 있는 특정 클러스터에 대한 특징을 검색하고 두 집합을 비교해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-241">If you want to write your own query in DMX to compare two clusters, or compare a cluster with its complement, you must first retrieve one set of characteristics, and then retrieve the characteristics for the specific cluster that you are interested in, and compare the two sets.</span></span> <span data-ttu-id="6dbaa-242">이 시나리오는 보다 복잡하여 일반적으로 클라이언트 처리를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-242">This scenario is more complicated and typically requires some client processing.</span></span>  
  
#### <a name="states-and-transitions"></a><span data-ttu-id="6dbaa-243">상태 및 전환</span><span class="sxs-lookup"><span data-stu-id="6dbaa-243">States and Transitions</span></span>  
 <span data-ttu-id="6dbaa-244">Microsoft 시퀀스 클러스터링의 **상태 전환** 탭에서는 백 엔드에 대한 복잡한 쿼리를 수행하여 서로 다른 여러 클러스터의 통계를 검색하고 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-244">The **State Transitions** tab of the Microsoft Sequence Clustering performs complicated queries on the back end to retrieve and compare the statistics for different clusters.</span></span> <span data-ttu-id="6dbaa-245">이러한 결과를 다시 생성하려면 보다 복잡한 쿼리와 클라이언트 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-245">To reproduce these results requires a more complex query and some client processing.</span></span>  
  
 <span data-ttu-id="6dbaa-246">그러나 [내용 쿼리](#bkmk_ContentQueries)섹션의 예 2에 설명된 DMX 쿼리를 사용하면 시퀀스나 개별 전환에 대한 확률 및 상태를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-246">However, you can use the DMX queries described in Example 2 of the section, [Content Queries](#bkmk_ContentQueries), to retrieve probabilities and states for sequences or for individual transitions.</span></span>  
  
## <a name="using-the-model-to-make-predictions"></a><span data-ttu-id="6dbaa-247">모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="6dbaa-247">Using the Model to Make Predictions</span></span>  
 <span data-ttu-id="6dbaa-248">시퀀스 클러스터링 모델에 대한 예측 쿼리에서는 다른 클러스터링 모델에서 사용되는 예측 함수를 상당수 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-248">Prediction queries on a sequence clustering model can use many of the prediction functions that are used with other clustering models.</span></span> <span data-ttu-id="6dbaa-249">또한 특수한 예측 함수인 [PredictSequence&#40;DMX&#41;](/sql/dmx/predictsequence-dmx)를 사용하여 권장 구성을 생성하거나 다음 상태를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-249">In addition, you can use the special prediction function, [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx), to make recommendations or to predict next states.</span></span>  
  
###  <a name="sample-query-4-predict-next-state-or-states"></a><a name="bkmk_Query4"></a><span data-ttu-id="6dbaa-250">예제 쿼리 4: 다음 상태 예측</span><span class="sxs-lookup"><span data-stu-id="6dbaa-250">Sample Query 4: Predict Next State or States</span></span>  
 <span data-ttu-id="6dbaa-251">[PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) 함수를 사용하여 특정 값에 대해 다음으로 가능성이 높은 상태를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-251">You can use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function to predict the next most likely state, given a value.</span></span> <span data-ttu-id="6dbaa-252">여러 개의 다음 상태를 예측할 수도 있습니다. 예를 들어 고객이 구입할 가능성이 가장 높은 세 가지 제품의 목록을 반환하여 권장 제품 목록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-252">You can also predict multiple next states: for example, you can return a list of the top three products that a customer is likely to purchase, to present a list of recommendations.</span></span>  
  
 <span data-ttu-id="6dbaa-253">다음 예제 쿼리는 상위 5개의 예측과 해당 확률을 반환하는 단일 예측 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-253">The following sample query is a singleton prediction query that returns the top five predictions, together with their probability.</span></span> <span data-ttu-id="6dbaa-254">해당 모델에는 중첩 테이블이 포함되어 있으므로 예측을 만들 때는 중첩 테이블 `[v Assoc Seq Line Items]`를 열 참조로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-254">Because the model includes a nested table, you must use the nested table, `[v Assoc Seq Line Items]`, as the column reference when making predictions.</span></span> <span data-ttu-id="6dbaa-255">또한 입력 값을 지정할 때는 중첩된 SELECT 문에 표시된 것과 같이 사례 테이블 및 중첩 테이블 열을 모두 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-255">Also, when you supply values as input, you must join both the case table and the nested table columns, as shown by the nested SELECT statements.</span></span>  
  
```  
SELECT FLATTENED PredictSequence([v Assoc Seq Line Items], 7)  
FROM [Sequence Clustering]  
NATURAL PREDICTION JOIN  
(SELECT  (SELECT 1 as [Line Number],  
   'All-Purpose Bike Stand' as [Model]) AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="6dbaa-256">결과 예:</span><span class="sxs-lookup"><span data-stu-id="6dbaa-256">Example results:</span></span>  
  
|<span data-ttu-id="6dbaa-257">Expression.$Sequence</span><span class="sxs-lookup"><span data-stu-id="6dbaa-257">Expression.$Sequence</span></span>|<span data-ttu-id="6dbaa-258">Expression.Line Number</span><span class="sxs-lookup"><span data-stu-id="6dbaa-258">Expression.Line Number</span></span>|<span data-ttu-id="6dbaa-259">Expression.Model</span><span class="sxs-lookup"><span data-stu-id="6dbaa-259">Expression.Model</span></span>|  
|--------------------------|----------------------------|----------------------|  
|<span data-ttu-id="6dbaa-260">1</span><span class="sxs-lookup"><span data-stu-id="6dbaa-260">1</span></span>||<span data-ttu-id="6dbaa-261">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="6dbaa-261">Cycling Cap</span></span>|  
|<span data-ttu-id="6dbaa-262">2</span><span class="sxs-lookup"><span data-stu-id="6dbaa-262">2</span></span>||<span data-ttu-id="6dbaa-263">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="6dbaa-263">Cycling Cap</span></span>|  
|<span data-ttu-id="6dbaa-264">3</span><span class="sxs-lookup"><span data-stu-id="6dbaa-264">3</span></span>||<span data-ttu-id="6dbaa-265">Sport-100</span><span class="sxs-lookup"><span data-stu-id="6dbaa-265">Sport-100</span></span>|  
|<span data-ttu-id="6dbaa-266">4</span><span class="sxs-lookup"><span data-stu-id="6dbaa-266">4</span></span>||<span data-ttu-id="6dbaa-267">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="6dbaa-267">Long-Sleeve logo Jersey</span></span>|  
|<span data-ttu-id="6dbaa-268">5</span><span class="sxs-lookup"><span data-stu-id="6dbaa-268">5</span></span>||<span data-ttu-id="6dbaa-269">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="6dbaa-269">Half-Finger Gloves</span></span>|  
|<span data-ttu-id="6dbaa-270">6</span><span class="sxs-lookup"><span data-stu-id="6dbaa-270">6</span></span>||<span data-ttu-id="6dbaa-271">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="6dbaa-271">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6dbaa-272">7</span><span class="sxs-lookup"><span data-stu-id="6dbaa-272">7</span></span>||<span data-ttu-id="6dbaa-273">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="6dbaa-273">All-Purpose Bike Stand</span></span>|  
  
 <span data-ttu-id="6dbaa-274">한 열만 반환될 것으로 예상했을 수 있지만 이 쿼리는 항상 사례 테이블에 대한 열을 반환하므로 결과에는 세 개의 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-274">There are three columns in the results, even though you might only expect one column, because the query always returns a column for the case table.</span></span> <span data-ttu-id="6dbaa-275">이 경우 결과는 결합됩니다. 그렇지 않으면 쿼리에서는 두 개의 중첩된 테이블 열이 들어 있는 단일 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-275">Here the results are flattened; otherwise, the query would return a single column that contains two nested table columns.</span></span>  
  
 <span data-ttu-id="6dbaa-276">$sequence 열은 예측 결과를 정렬하기 위해 `PredictSequence` 함수에서 기본적으로 반환되는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-276">The column $sequence is a column returned by default by the `PredictSequence` function to order the prediction results.</span></span> <span data-ttu-id="6dbaa-277">`[Line Number]`열은 모델의 시퀀스 키와 일치시키는 데 필요하지만 키는 출력되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-277">The column, `[Line Number]`, is required to match the sequence keys in the model, but the keys are not output.</span></span>  
  
 <span data-ttu-id="6dbaa-278">흥미로운 점은 All-Purpose Bike Stand 이후의 예측된 최상위 시퀀스가 Cycling Cap과 Cycling Cap이라는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-278">Interestingly, the top predicted sequences after All-Purpose Bike Stand are Cycling Cap and Cycling Cap.</span></span> <span data-ttu-id="6dbaa-279">이는 오류가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-279">This is not an error.</span></span> <span data-ttu-id="6dbaa-280">고객에게 데이터가 제공되는 방식과 모델을 학습할 때 데이터가 그룹화되는 방식에 따라 이러한 종류의 시퀀스도 얼마든지 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-280">Depending on how the data is presented to the customer, and how it is grouped when training the model, it is very possible to have sequences of this kind.</span></span> <span data-ttu-id="6dbaa-281">예를 들어 고객이 빨간색 Cycling Cap을 구입한 뒤 파란색 Cycling Cap을 하나 더 구입했을 수도 있고, 수량을 지정할 방법이 없어서 두 개의 Cycling Cap을 연달아 구입했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-281">For example, a customer might purchase a cycling cap (red) and then another cycling cap (blue), or purchase two in a row if there were no way to specify quantity.</span></span>  
  
 <span data-ttu-id="6dbaa-282">6행과 7행의 값은 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-282">The values in rows 6 and 7 are placeholders.</span></span> <span data-ttu-id="6dbaa-283">가능한 전환의 체인 끝에 도달하면 예측 결과가 종료되는 것이 아니라 입력으로 전달된 값이 결과에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-283">When you reach the end of the chain of possible transitions, rather than terminating the prediction results, the value that was passed as an input is added to the results.</span></span> <span data-ttu-id="6dbaa-284">예를 들어 예측 수를 20개로 늘리면 6-20행의 값은 모두 동일하게 All-Purpose Bike Stand가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-284">For example, if you increased the number of predictions to 20, the values for rows 6-20 would all be the same, All-Purpose Bike Stand.</span></span>  
  
## <a name="function-list"></a><span data-ttu-id="6dbaa-285">함수 목록</span><span class="sxs-lookup"><span data-stu-id="6dbaa-285">Function List</span></span>  
 <span data-ttu-id="6dbaa-286">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-286">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="6dbaa-287">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘은 다음 표에 나열된 함수를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-287">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dbaa-288">예측 함수</span><span class="sxs-lookup"><span data-stu-id="6dbaa-288">Prediction Function</span></span>|<span data-ttu-id="6dbaa-289">사용</span><span class="sxs-lookup"><span data-stu-id="6dbaa-289">Usage</span></span>|  
|[<span data-ttu-id="6dbaa-290">Cluster&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-290">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="6dbaa-291">입력 사례가 포함되었을 가능성이 가장 높은 클러스터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-291">Returns the cluster that is most likely to contain the input case</span></span>|  
|[<span data-ttu-id="6dbaa-292">ClusterDistance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-292">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="6dbaa-293">입력 사례와 지정된 클러스터 사이의 거리를 반환합니다. 클러스터가 지정되지 않은 경우에는 입력 사례와 가장 가능성 있는 클러스터 사이의 거리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-293">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="6dbaa-294">이 함수는 EM과 K-Means를 비롯한 모든 종류의 클러스터링 모델과 함께 사용할 수 있지만 알고리즘에 따라 결과가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-294">This function can be used with any kind of clustering model (EM, K-Means, etc.), but the results differ depending on the algorithm.</span></span>|  
|[<span data-ttu-id="6dbaa-295">ClusterProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-295">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="6dbaa-296">입력 사례가 지정한 클러스터에 속할 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-296">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="6dbaa-297">IsInNode&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-297">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="6dbaa-298">지정한 노드에 현재 사례가 포함되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-298">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="6dbaa-299">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-299">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="6dbaa-300">지정한 상태에 대한 조정된 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-300">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="6dbaa-301">PredictAssociation&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-301">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="6dbaa-302">연관된 멤버 자격을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-302">Predicts associative membership.</span></span>|  
|[<span data-ttu-id="6dbaa-303">PredictCaseLikelihood&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-303">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="6dbaa-304">입력 사례가 기존 모델에 적합할 가능성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-304">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="6dbaa-305">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-305">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="6dbaa-306">지정된 열의 예측에 대한 히스토그램을 나타내는 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-306">Returns a table that represents a histogram for the prediction of a given column.</span></span>|  
|[<span data-ttu-id="6dbaa-307">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-307">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="6dbaa-308">사례가 분류되어 있는 노드의 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-308">Returns the Node_ID of the node to which the case is classified.</span></span>|  
|[<span data-ttu-id="6dbaa-309">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-309">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="6dbaa-310">지정한 상태에 대한 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-310">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="6dbaa-311">PredictSequence&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-311">PredictSequence &#40;DMX&#41;</span></span>](/sql/dmx/predictsequence-dmx)|<span data-ttu-id="6dbaa-312">지정한 시퀀스 데이터 집합에 대한 미래의 시퀀스 값을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-312">Predicts future sequence values for a specified set of sequence data.</span></span>|  
|[<span data-ttu-id="6dbaa-313">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-313">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="6dbaa-314">지정된 열의 예측 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-314">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="6dbaa-315">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-315">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="6dbaa-316">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-316">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="6dbaa-317">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-317">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="6dbaa-318">지정한 열의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-318">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="6dbaa-319">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘에 공통된 함수 목록은 [일반 예측 함수&#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-319">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="6dbaa-320">특정 함수의 구문은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dbaa-320">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbaa-321">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6dbaa-321">See Also</span></span>  
 <span data-ttu-id="6dbaa-322">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="6dbaa-322">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="6dbaa-323">[Microsoft 시퀀스 클러스터링 알고리즘 기술 참조](microsoft-sequence-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6dbaa-323">[Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="6dbaa-324">[Microsoft 시퀀스 클러스터링 알고리즘](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="6dbaa-324">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="6dbaa-325">시퀀스 클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="6dbaa-325">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
