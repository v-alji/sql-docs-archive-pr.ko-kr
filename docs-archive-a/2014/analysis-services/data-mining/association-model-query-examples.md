---
title: 연결 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- content queries [DMX]
ms.assetid: 68b39f5c-c439-44ac-8046-6f2d36649059
author: minewiskan
ms.author: owend
ms.openlocfilehash: a19eb2302639c7f13d48a8778969bbeca4fee18d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660215"
---
# <a name="association-model-query-examples"></a><span data-ttu-id="ea919-102">연결 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="ea919-102">Association Model Query Examples</span></span>
  <span data-ttu-id="ea919-103">데이터 마이닝 모델에 대한 쿼리를 만들 때 분석 중에 발견된 규칙과 항목 집합에 대한 세부 정보를 제공하는 내용 쿼리를 만들거나, 데이터에서 발견된 연결을 사용하여 예측을 수행하는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-103">When you create a query against a data mining model, you can create either a content query, which provides details about the rules and itemsets discovered during analysis, or you can create a prediction query, which uses the associations discovered in the data to make predictions.</span></span> <span data-ttu-id="ea919-104">연결 모델에서 예측은 일반적으로 규칙을 기반으로 하여 권장 구성을 생성하는 데 사용되고, 내용에 대한 쿼리는 일반적으로 항목 집합 간의 관계를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-104">For an association model, predictions typically are based on rules, and can be used to make recommendations, whereas queries on content typically explore the relationship among itemsets.</span></span> <span data-ttu-id="ea919-105">모델에 대한 메타데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-105">You can also retrieve metadata about the model.</span></span>  
  
 <span data-ttu-id="ea919-106">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘을 기반으로 하는 모델에 대해 이러한 종류의 쿼리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-106">This section explains how to create these kinds of queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="ea919-107">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="ea919-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="ea919-108">DMX를 사용하여 모델 메타데이터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea919-108">Getting model metadata data by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="ea919-109">스키마 행 집합에서 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea919-109">Getting metadata from the schema rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="ea919-110">모델의 원래 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="ea919-110">Retrieving the original parameters for the model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="ea919-111">항목 집합 및 제품 목록 검색</span><span class="sxs-lookup"><span data-stu-id="ea919-111">Retrieving a list of itemsets and products</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="ea919-112">상위 10개 항목 집합 반환</span><span class="sxs-lookup"><span data-stu-id="ea919-112">Returning the top 10 itemsets</span></span>](#bkmk_Query5)  
  
 <span data-ttu-id="ea919-113">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="ea919-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="ea919-114">연관된 항목 예측</span><span class="sxs-lookup"><span data-stu-id="ea919-114">Predicting associated items</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="ea919-115">관련 항목 집합에 대한 신뢰도 결정</span><span class="sxs-lookup"><span data-stu-id="ea919-115">Determining confidence for related itemsets</span></span>](#bkmk_Query7)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="ea919-116">모델 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="ea919-116">Finding Information about the Model</span></span>  
 <span data-ttu-id="ea919-117">모든 마이닝 모델은 마이닝 모델 스키마 행 집합이라고 하는 표준화된 스키마에 따라, 알고리즘을 통해 학습한 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-117">All mining models expose the content learned by the algorithm according to a standardized schema, which is named the mining model schema rowset.</span></span> <span data-ttu-id="ea919-118">마이닝 모델 스키마 행 집합에 대한 쿼리는 DMX(Data Mining Extensions) 문을 사용하거나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 저장 프로시저를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-118">You can create queries against the mining model schema rowset either by using Data Mining Extensions (DMX) statements, or by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="ea919-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 SQL과 유사한 구문을 사용하여 스키마 행 집합을 직접 시스템 테이블로 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-119">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables, by using a SQL-like syntax.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="ea919-120">예제 쿼리 1: DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea919-120">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="ea919-121">다음 쿼리는 연결 모델 `Association`에 대한 기본 메타데이터(예: 모델 이름, 모델이 저장된 데이터베이스, 모델의 자식 노드 수)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-121">The following query returns basic metadata about the association model, `Association`, such as the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="ea919-122">이 쿼리는 DMX 내용 쿼리를 사용하여 모델의 부모 노드에서 메타데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-122">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ea919-123">CHILDREN_CARDINALITY 열의 이름을 대괄호로 묶어 동일한 이름의 MDX 예약 키워드와 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-123">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="ea919-124">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-124">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea919-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ea919-125">MODEL_CATALOG</span></span>|<span data-ttu-id="ea919-126">Association Test</span><span class="sxs-lookup"><span data-stu-id="ea919-126">Association Test</span></span>|  
|<span data-ttu-id="ea919-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-127">MODEL_NAME</span></span>|<span data-ttu-id="ea919-128">연결</span><span class="sxs-lookup"><span data-stu-id="ea919-128">Association</span></span>|  
|<span data-ttu-id="ea919-129">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ea919-129">NODE_CAPTION</span></span>|<span data-ttu-id="ea919-130">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="ea919-130">Association Rules Model</span></span>|  
|<span data-ttu-id="ea919-131">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ea919-131">NODE_SUPPORT</span></span>|<span data-ttu-id="ea919-132">14879</span><span class="sxs-lookup"><span data-stu-id="ea919-132">14879</span></span>|  
|<span data-ttu-id="ea919-133">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="ea919-133">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="ea919-134">942</span><span class="sxs-lookup"><span data-stu-id="ea919-134">942</span></span>|  
|<span data-ttu-id="ea919-135">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ea919-135">NODE_DESCRIPTION</span></span>|<span data-ttu-id="ea919-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span><span class="sxs-lookup"><span data-stu-id="ea919-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span></span>|  
  
 <span data-ttu-id="ea919-137">연결 모델에서 이러한 열의 의미에 대한 정의는 [연결 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea919-137">For a definition of what these columns mean in an association model, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="ea919-138">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-138">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-getting-additional-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="ea919-139">예제 쿼리 2: 스키마 행 집합에서 추가 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea919-139">Sample Query 2: Getting Additional Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="ea919-140">데이터 마이닝 스키마 행 집합을 쿼리하면 DMX 내용 쿼리에 반환되는 것과 동일한 정보를 찾을 수 있는데,</span><span class="sxs-lookup"><span data-stu-id="ea919-140">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="ea919-141">스키마 행 집합은 모델이 마지막으로 처리된 날짜, 마이닝 구조, 예측 가능한 특성으로 사용된 열 이름 등 몇 개의 추가 열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-141">However, the schema rowset provides some additional columns, such as the date the model was last processed, the mining structure, and the name of the column used as the predictable attribute.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, SERVICE_NAME, PREDICTION_ENTITY,   
MINING_STRUCTURE, LAST_PROCESSED  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="ea919-142">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-142">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea919-143">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ea919-143">MODEL_CATALOG</span></span>|<span data-ttu-id="ea919-144">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="ea919-144">Adventure Works DW Multidimensional 2012</span></span>|  
|<span data-ttu-id="ea919-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-145">MODEL_NAME</span></span>|<span data-ttu-id="ea919-146">연결</span><span class="sxs-lookup"><span data-stu-id="ea919-146">Association</span></span>|  
|<span data-ttu-id="ea919-147">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-147">SERVICE_NAME</span></span>|<span data-ttu-id="ea919-148">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="ea919-148">Association Rules Model</span></span>|  
|<span data-ttu-id="ea919-149">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="ea919-149">PREDICTION_ENTITY</span></span>|<span data-ttu-id="ea919-150">v Assoc Seq Line Items</span><span class="sxs-lookup"><span data-stu-id="ea919-150">v Assoc Seq Line Items</span></span>|  
|<span data-ttu-id="ea919-151">MINING_STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="ea919-151">MINING_STRUCTURE</span></span>|<span data-ttu-id="ea919-152">연결</span><span class="sxs-lookup"><span data-stu-id="ea919-152">Association</span></span>|  
|<span data-ttu-id="ea919-153">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="ea919-153">LAST_PROCESSED</span></span>|<span data-ttu-id="ea919-154">9/29/2007 10:21:24 PM</span><span class="sxs-lookup"><span data-stu-id="ea919-154">9/29/2007 10:21:24 PM</span></span>|  
  
 [<span data-ttu-id="ea919-155">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-155">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-3-retrieving-original-parameters-for-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="ea919-156">예제 쿼리 3: 모델의 원래 매개 변수 검색</span><span class="sxs-lookup"><span data-stu-id="ea919-156">Sample Query 3: Retrieving Original Parameters for Model</span></span>  
 <span data-ttu-id="ea919-157">다음 쿼리는 모델을 만들 때 사용했던 매개 변수 설정에 대한 세부 정보가 포함된 단일 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-157">The following query returns a single column that contains details about the parameter settings that were used when the model was created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="ea919-158">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-158">Example results:</span></span>  
  
 <span data-ttu-id="ea919-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span><span class="sxs-lookup"><span data-stu-id="ea919-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span></span>  
  
 [<span data-ttu-id="ea919-160">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-160">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-rules-and-itemsets"></a><span data-ttu-id="ea919-161">규칙 및 항목 집합에 대한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="ea919-161">Finding Information about Rules and Itemsets</span></span>  
 <span data-ttu-id="ea919-162">연결 모델의 일반적인 용도는 자주 사용하는 항목 집합에 대한 정보를 검색하는 것과 특정 규칙과 항목 집합에 대한 세부 정보를 추출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-162">There are two common uses of an association model: to discover information about frequent itemsets, and to extract details about particular rules and itemsets.</span></span> <span data-ttu-id="ea919-163">예를 들어 특별히 관심 있는 항목으로 점수가 매겨진 규칙 목록을 추출하거나 가장 일반적인 항목 집합의 목록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-163">For example, you might want to extract a list of rules that were scored as being especially interesting, or create a list of the most common itemsets.</span></span> <span data-ttu-id="ea919-164">이러한 정보는 DMX 내용 쿼리를 사용하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-164">You retrieve such information by using a DMX content query.</span></span> <span data-ttu-id="ea919-165">**Microsoft 연결 뷰어**에서도 이러한 정보를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-165">You can also browse this information by using the **Microsoft Association Viewer**.</span></span>  
  
###  <a name="sample-query-4-retrieving-list-of-itemsets-and-products"></a><a name="bkmk_Query4"></a> <span data-ttu-id="ea919-166">예제 쿼리 4: 항목 집합 및 제품 목록 검색</span><span class="sxs-lookup"><span data-stu-id="ea919-166">Sample Query 4: Retrieving List of Itemsets and Products</span></span>  
 <span data-ttu-id="ea919-167">다음 쿼리는 모든 항목 집합과 각 항목 집합에 포함된 제품을 나열하는 중첩 테이블을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-167">The following query retrieves all of the itemsets, together with a nested table that lists the products included in each itemset.</span></span> <span data-ttu-id="ea919-168">NODE_NAME 열에는 모델 내에 있는 항목 집합의 고유 ID가 들어 있고, NODE_CAPTION에는 항목에 대한 텍스트 설명이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-168">The NODE_NAME column contains the unique ID of the itemset within the model, whereas the NODE_CAPTION provides a text description of the items.</span></span> <span data-ttu-id="ea919-169">이 예에서는 두 제품을 포함하는 항목 집합이 결과에 두 개의 행을 생성하도록 중첩 테이블이 평면화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-169">In this example, the nested table is flattened, so that an itemset that contains two products generates two rows in the results.</span></span> <span data-ttu-id="ea919-170">클라이언트에서 계층적 데이터를 지원하는 경우 FLATTENED 키워드를 생략해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-170">You can omit the FLATTENED keyword if your client supports hierarchical data.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
NODE_PROBABILITY, NODE_SUPPORT,  
(SELECT ATTRIBUTE_NAME FROM NODE_DISTRIBUTION) as PurchasedProducts  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="ea919-171">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-171">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea919-172">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-172">NODE_NAME</span></span>|<span data-ttu-id="ea919-173">37</span><span class="sxs-lookup"><span data-stu-id="ea919-173">37</span></span>|  
|<span data-ttu-id="ea919-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ea919-174">NODE_CAPTION</span></span>|<span data-ttu-id="ea919-175">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-175">Sport-100 = Existing</span></span>|  
|<span data-ttu-id="ea919-176">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ea919-176">NODE_PROBABILITY</span></span>|<span data-ttu-id="ea919-177">0.291283016331743</span><span class="sxs-lookup"><span data-stu-id="ea919-177">0.291283016331743</span></span>|  
|<span data-ttu-id="ea919-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ea919-178">NODE_SUPPORT</span></span>|<span data-ttu-id="ea919-179">4334</span><span class="sxs-lookup"><span data-stu-id="ea919-179">4334</span></span>|  
|<span data-ttu-id="ea919-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="ea919-181">v Assoc Seq Line Items(Sport-100)</span><span class="sxs-lookup"><span data-stu-id="ea919-181">v Assoc Seq Line Items(Sport-100)</span></span>|  
  
 [<span data-ttu-id="ea919-182">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-182">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-returning-top-10-itemsets"></a><a name="bkmk_Query5"></a> <span data-ttu-id="ea919-183">예제 쿼리 5: 상위 10개 항목 집합 반환</span><span class="sxs-lookup"><span data-stu-id="ea919-183">Sample Query 5: Returning Top 10 Itemsets</span></span>  
 <span data-ttu-id="ea919-184">이 예는 DMX에서 기본적으로 제공하는 몇 가지 그룹화 및 순서 지정 함수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-184">This example demonstrates how to use some of the grouping and ordering functions that DMX provides by default.</span></span> <span data-ttu-id="ea919-185">각 노드에 대한 지지도 순으로 정렬된 경우 이 쿼리는 상위 10개의 항목 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-185">The query returns the top 10 itemsets when ordered by the support for each node.</span></span> <span data-ttu-id="ea919-186">Transact-SQL을 사용하고 있으므로 결과를 명시적으로 그룹화할 필요는 없지만 각 쿼리에는 한 개의 집계 함수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-186">Note that you do not need to explicitly group the results, as you would in Transact-SQL; however, you can use only one aggregate function in each query.</span></span>  
  
```  
SELECT TOP 10 (NODE_SUPPORT),NODE_NAME, NODE_CAPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="ea919-187">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-187">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea919-188">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ea919-188">NODE_SUPPORT</span></span>|<span data-ttu-id="ea919-189">4334</span><span class="sxs-lookup"><span data-stu-id="ea919-189">4334</span></span>|  
|<span data-ttu-id="ea919-190">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-190">NODE_NAME</span></span>|<span data-ttu-id="ea919-191">37</span><span class="sxs-lookup"><span data-stu-id="ea919-191">37</span></span>|  
|<span data-ttu-id="ea919-192">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ea919-192">NODE_CAPTION</span></span>|<span data-ttu-id="ea919-193">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-193">Sport-100 = Existing</span></span>|  
  
 [<span data-ttu-id="ea919-194">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-194">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="ea919-195">모델을 사용하여 예측 수행</span><span class="sxs-lookup"><span data-stu-id="ea919-195">Making Predictions using the Model</span></span>  
 <span data-ttu-id="ea919-196">연결 규칙 모델은 항목 집합에서 발견된 상관 관계를 기반으로 하는 권장 구성을 생성하는 데 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-196">An association rules model is often used to generate recommendations, which are based on correlations discovered in the itemsets.</span></span> <span data-ttu-id="ea919-197">따라서 연결 규칙 모델을 기반으로 예측 쿼리를 만들 때 일반적으로 모델의 규칙을 사용하여 새로운 데이터를 토대로 예측을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-197">Therefore, when you create a prediction query based on an association rules model, you are typically using the rules in the model to make guesses based on new data.</span></span>  <span data-ttu-id="ea919-198">[PredictAssociation&#40;DMX&#41;](/sql/dmx/predictassociation-dmx) 은 권장 구성을 반환하는 함수로, 쿼리 결과를 사용자 지정하는 데 사용할 수 있는 몇 개의 인수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-198">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) is the function that returns recommendations, and has several arguments that you can use to customize the query results.</span></span>  
  
 <span data-ttu-id="ea919-199">서로 다른 교차 판매 전략의 효율성을 비교할 수 있도록 다양한 규칙과 항목 집합에 대한 신뢰도를 반환하려는 경우 연결 모델에 대한 쿼리가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-199">Another example of where queries on an association model might be useful is to return the confidence for various rules and itemsets so that you can compare the effectiveness of different cross-sell strategies.</span></span> <span data-ttu-id="ea919-200">다음 예에서는 이러한 쿼리를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-200">The following examples illustrate how to create such queries.</span></span>  
  
###  <a name="sample-query-6-predicting-associated-items"></a><a name="bkmk_Query6"></a> <span data-ttu-id="ea919-201">예제 쿼리 6: 관련 항목 예측</span><span class="sxs-lookup"><span data-stu-id="ea919-201">Sample Query 6: Predicting Associated Items</span></span>  
 <span data-ttu-id="ea919-202">다음 예제에서는 [중간 데이터 마이닝 자습서&#40;Analysis Services - 데이터 마이닝&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)에서 만든 연결 모델을 사용하며,</span><span class="sxs-lookup"><span data-stu-id="ea919-202">This example uses the Association model created in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="ea919-203">특정 제품을 구매한 고객에게 어떤 제품을 권장할 것인지를 알려 주는 예측 쿼리를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-203">It demonstrates how to create a prediction query that tells you what products to recommend to a customer who has purchased a particular product.</span></span> <span data-ttu-id="ea919-204">사용자가 `SELECT...UNION` 문에서 모델에 값을 제공하는 쿼리를 단일 쿼리라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-204">This type of query, where you provide values to the model in a `SELECT...UNION` statement, is called a singleton query.</span></span> <span data-ttu-id="ea919-205">새로운 값에 해당하는 예측 가능한 모델 열이 중첩 테이블이므로 `SELECT` 절을 하나 사용하여 새 값을 중첩 테이블 열 `[Model]`에 매핑하고, 또 다른 `SELECT` 절을 사용하여 중첩 테이블 열을 사례 수준 열 `[v Assoc Seq Line Items]`에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-205">Because the predictable model column that corresponds to the new values is a nested table, you must use one `SELECT` clause to map the new value to the nested table column, `[Model]`, and another `SELECT` clause to map the nested table column to the case-level column, `[v Assoc Seq Line Items]`.</span></span> <span data-ttu-id="ea919-206">INCLUDE-STATISTICS 키워드를 쿼리에 추가하면 권장 구성에 대한 확률과 지지도를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-206">Adding the keyword INCLUDE-STATISTICS to the query lets you see the probability and support for the recommendations.</span></span>  
  
```  
SELECT PredictAssociation([Association].[vAssocSeqLineItems],INCLUDE_STATISTICS, 3)  
FROM [Association]  
NATURAL PREDICTION JOIN   
(SELECT  
(SELECT 'Classic Vest' as [Model])  
AS [v Assoc Seq Line Items])  
AS t  
```  
  
 <span data-ttu-id="ea919-207">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-207">Example results:</span></span>  
  
|<span data-ttu-id="ea919-208">모델</span><span class="sxs-lookup"><span data-stu-id="ea919-208">Model</span></span>|<span data-ttu-id="ea919-209">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ea919-209">$SUPPORT</span></span>|<span data-ttu-id="ea919-210">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ea919-210">$PROBABILITY</span></span>|<span data-ttu-id="ea919-211">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ea919-211">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="ea919-212">Sport-100</span><span class="sxs-lookup"><span data-stu-id="ea919-212">Sport-100</span></span>|<span data-ttu-id="ea919-213">4334</span><span class="sxs-lookup"><span data-stu-id="ea919-213">4334</span></span>|<span data-ttu-id="ea919-214">0.291283</span><span class="sxs-lookup"><span data-stu-id="ea919-214">0.291283</span></span>|<span data-ttu-id="ea919-215">0.252696</span><span class="sxs-lookup"><span data-stu-id="ea919-215">0.252696</span></span>|  
|<span data-ttu-id="ea919-216">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="ea919-216">Water Bottle</span></span>|<span data-ttu-id="ea919-217">2866</span><span class="sxs-lookup"><span data-stu-id="ea919-217">2866</span></span>|<span data-ttu-id="ea919-218">0.19262</span><span class="sxs-lookup"><span data-stu-id="ea919-218">0.19262</span></span>|<span data-ttu-id="ea919-219">0.175205</span><span class="sxs-lookup"><span data-stu-id="ea919-219">0.175205</span></span>|  
|<span data-ttu-id="ea919-220">Patch kit</span><span class="sxs-lookup"><span data-stu-id="ea919-220">Patch kit</span></span>|<span data-ttu-id="ea919-221">2113</span><span class="sxs-lookup"><span data-stu-id="ea919-221">2113</span></span>|<span data-ttu-id="ea919-222">0.142012</span><span class="sxs-lookup"><span data-stu-id="ea919-222">0.142012</span></span>|<span data-ttu-id="ea919-223">0.132389</span><span class="sxs-lookup"><span data-stu-id="ea919-223">0.132389</span></span>|  
  
 [<span data-ttu-id="ea919-224">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-224">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-determining-confidence-for-related-itemsets"></a><a name="bkmk_Query7"></a> <span data-ttu-id="ea919-225">예제 쿼리 7: 관련 항목 집합에 대한 신뢰도 확인</span><span class="sxs-lookup"><span data-stu-id="ea919-225">Sample Query 7: Determining Confidence for Related Itemsets</span></span>  
 <span data-ttu-id="ea919-226">규칙은 권장 구성을 생성하는 데 유용한 반면 항목 집합은 데이터 집합의 패턴을 보다 상세하게 분석하는 데 더 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-226">Whereas rules are useful for generating recommendations, itemsets are more interesting for deeper analysis of the patterns in the data set.</span></span> <span data-ttu-id="ea919-227">예를 들어 이전 예제 쿼리에 의해 반환된 권장 구성이 만족스럽지 않을 경우 제품 A가 포함된 다른 항목 집합을 검사하여 제품 A가 고객이 다른 종류의 제품과 함께 구매하고자 하는 액세서리인지 여부 또는 제품 A가 특정 제품의 구매와 강한 상관 관계가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-227">For example, if you were not satisfied with the recommendation that are returned by the previous sample query, you could examine other itemsets that contain Product A, to can get a better idea of whether Product A is an accessory that people tend to buy with all kinds of products, or whether A is strongly correlated with purchases of particular products.</span></span> <span data-ttu-id="ea919-228">이러한 관계를 확인하는 가장 쉬운 방법은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 뷰어에서 항목 집합을 필터링하는 것이지만 쿼리를 통해 동일한 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-228">The easiest way to explore these relationships is by filtering the itemsets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Viewer; however, you can retrieve the same information with a query.</span></span>  
  
 <span data-ttu-id="ea919-229">다음 예제 쿼리는 단일 항목인 Water Bottle을 포함하여 Water Bottle 항목을 포함하는 모든 항목 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-229">The following sample query returns all itemsets that include the Water Bottle item, including the single item Water bottle.</span></span>  
  
```  
SELECT TOP 100 FROM   
(  
SELECT FLATTENED NODE_CAPTION, NODE_SUPPORT,   
(SELECT ATTRIBUTE_NAME from NODE_DISTRIBUTION  
WHERE ATTRIBUTE_NAME = 'v Assoc Seq Line Items(Water Bottle)') as D  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
) AS Items  
WHERE [D.ATTRIBUTE_NAME] <> NULL  
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="ea919-230">결과 예:</span><span class="sxs-lookup"><span data-stu-id="ea919-230">Example results:</span></span>  
  
|<span data-ttu-id="ea919-231">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ea919-231">NODE_CAPTION</span></span>|<span data-ttu-id="ea919-232">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ea919-232">NODE_SUPPORT</span></span>|<span data-ttu-id="ea919-233">D.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="ea919-233">D.ATTRIBUTE_NAME</span></span>|  
|-------------------|-------------------|-----------------------|  
|<span data-ttu-id="ea919-234">Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-234">Water Bottle = Existing</span></span>|<span data-ttu-id="ea919-235">2866</span><span class="sxs-lookup"><span data-stu-id="ea919-235">2866</span></span>|<span data-ttu-id="ea919-236">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ea919-236">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ea919-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="ea919-238">1136</span><span class="sxs-lookup"><span data-stu-id="ea919-238">1136</span></span>|<span data-ttu-id="ea919-239">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ea919-239">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ea919-240">Road Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-240">Road Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="ea919-241">1068</span><span class="sxs-lookup"><span data-stu-id="ea919-241">1068</span></span>|<span data-ttu-id="ea919-242">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ea919-242">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ea919-243">Water Bottle = Existing, Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ea919-243">Water Bottle = Existing, Sport-100 = Existing</span></span>|<span data-ttu-id="ea919-244">734</span><span class="sxs-lookup"><span data-stu-id="ea919-244">734</span></span>|<span data-ttu-id="ea919-245">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ea919-245">v Assoc Seq Line Items(Water Bottle)</span></span>|  
  
 <span data-ttu-id="ea919-246">이 쿼리는 조건과 일치하는 중첩 테이블의 행뿐만 아니라 외부 또는 사례 테이블의 모든 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-246">This query returns both the rows from the nested table that match the criteria, and all the rows from the outside or case table.</span></span> <span data-ttu-id="ea919-247">따라서 대상 특성 이름에 Null 값이 있는 사례 테이블 행을 제거하는 조건을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-247">Therefore, you must add a condition that eliminates the case table rows that have a null value for the target attribute name.</span></span>  
  
 [<span data-ttu-id="ea919-248">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ea919-248">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="ea919-249">함수 목록</span><span class="sxs-lookup"><span data-stu-id="ea919-249">Function List</span></span>  
 <span data-ttu-id="ea919-250">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-250">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="ea919-251">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 알고리즘은 다음 표에 나열된 함수를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-251">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea919-252">예측 함수</span><span class="sxs-lookup"><span data-stu-id="ea919-252">Prediction Function</span></span>|<span data-ttu-id="ea919-253">사용</span><span class="sxs-lookup"><span data-stu-id="ea919-253">Usage</span></span>|  
|[<span data-ttu-id="ea919-254">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-254">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="ea919-255">한 노드가 신경망 그래프에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-255">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="ea919-256">IsInNode&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-256">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="ea919-257">지정한 노드에 현재 사례가 포함되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-257">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="ea919-258">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-258">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="ea919-259">가중치 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-259">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="ea919-260">PredictAssociation&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-260">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="ea919-261">연관 데이터 세트에서의 멤버 자격을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-261">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="ea919-262">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-262">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="ea919-263">현재 예측된 값과 관련 된 값의 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-263">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="ea919-264">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-264">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="ea919-265">각 사례에 대한 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-265">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="ea919-266">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-266">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="ea919-267">예측 값의 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-267">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="ea919-268">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-268">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="ea919-269">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-269">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="ea919-270">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-270">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="ea919-271">예측 값의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ea919-271">Returns variance for the predicted value.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea919-272">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea919-272">See Also</span></span>  
 <span data-ttu-id="ea919-273">[Microsoft 연결 알고리즘](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ea919-273">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="ea919-274">[Microsoft 연결 알고리즘 기술 참조](microsoft-association-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ea919-274">[Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="ea919-275">연결 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ea919-275">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
