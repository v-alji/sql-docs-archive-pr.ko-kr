---
title: 클러스터링 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- content queries [DMX]
- clustering algorithms [Analysis Services]
ms.assetid: bf2ba332-9bc6-411a-a3af-b919c52432c8
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe12b82ce2d237acd060b1e387e7a6dfbf958851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661441"
---
# <a name="clustering-model-query-examples"></a><span data-ttu-id="8ab2a-102">클러스터링 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="8ab2a-102">Clustering Model Query Examples</span></span>
  <span data-ttu-id="8ab2a-103">데이터 마이닝 모델에 대한 쿼리를 만들 때 모델에 대한 메타데이터를 검색하거나, 분석 시 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-103">When you create a query against a data mining model, you can retrieve metadata about the model, or create a content query that provides details about the patterns discovered in analysis.</span></span> <span data-ttu-id="8ab2a-104">또는 모델의 패턴을 사용하여 새 데이터에 대한 예측을 만드는 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-104">Alternatively, you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="8ab2a-105">각 유형의 쿼리는 서로 다른 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-105">Each type of query will provide different information.</span></span> <span data-ttu-id="8ab2a-106">예를 들어 내용 쿼리는 발견된 클러스터에 대한 추가 세부 정보를 제공하지만 예측 쿼리는 새 데이터 요소가 속해 있을 가능성이 가장 높은 클러스터를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-106">For example, a content query might provide additional details about the clusters that were found, whereas a prediction query might tell you in which cluster a new data point is most likely to belong.</span></span>  
  
 <span data-ttu-id="8ab2a-107">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터링 알고리즘을 기반으로 하는 모델에 대해 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 <span data-ttu-id="8ab2a-108">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="8ab2a-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="8ab2a-109">DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-109">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="8ab2a-110">스키마 행 집합에서 모델 메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="8ab2a-110">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="8ab2a-111">클러스터 또는 클러스터 목록 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-111">Returning a Cluster or a List of Clusters</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="8ab2a-112">클러스터에 대한 특성 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-112">Returning Attributes for a Cluster</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="8ab2a-113">시스템 저장 프로시저를 사용하여 클러스터 프로필 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-113">Returning a Cluster Profile Using System Stored Procedures</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="8ab2a-114">클러스터에 대한 판별 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-114">Finding Discriminating Factors for a Cluster</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="8ab2a-115">클러스터에 속한 사례 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-115">Returning Cases that Belong to a Cluster</span></span>](#bkmk_Query7)  
  
 <span data-ttu-id="8ab2a-116">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="8ab2a-116">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="8ab2a-117">클러스터링 모델에서 결과 예측</span><span class="sxs-lookup"><span data-stu-id="8ab2a-117">Predicting Outcomes from a Clustering Model</span></span>](#bkmk_Query8)  
  
 [<span data-ttu-id="8ab2a-118">클러스터 멤버 자격 결정</span><span class="sxs-lookup"><span data-stu-id="8ab2a-118">Determining Cluster Membership</span></span>](#bkmk_Query9)  
  
 [<span data-ttu-id="8ab2a-119">확률과 거리가 포함된 가능한 모든 클러스터 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-119">Returning All Possible Clusters with Probability and Distance</span></span>](#bkmk_Query10)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="8ab2a-120">모델 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-120">Finding Information about the Model</span></span>  
 <span data-ttu-id="8ab2a-121">모든 마이닝 모델은 마이닝 모델 스키마 행 집합이라고 하는 표준화된 스키마에 따라, 알고리즘을 통해 학습한 내용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-121">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="8ab2a-122">마이닝 모델 스키마 행 집합에 대한 쿼리는 DMX(Data Mining Extensions) 문을 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-122">You can create queries against the mining model schema rowset by using Data Mining Extension (DMX) statements.</span></span> <span data-ttu-id="8ab2a-123">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 스키마 행 집합을 직접 시스템 테이블로 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-123">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables.</span></span>  
  
 [<span data-ttu-id="8ab2a-124">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-124">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="8ab2a-125">예제 쿼리 1: DMX를 사용하여 모델 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-125">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="8ab2a-126">다음 쿼리는 기본 데이터 마이닝 자습서에서 만든 클러스터링 모델 `TM_Clustering`에 대한 기본 메타데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-126">The following query returns basic metadata about the clustering model, `TM_Clustering`, that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="8ab2a-127">클러스터링 모델의 부모 노드에서 사용할 수 있는 메타데이터에는 모델 이름, 모델이 저장된 데이터베이스, 모델의 자식 노드 수 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-127">The metadata available in the parent node of a clustering model includes the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="8ab2a-128">이 쿼리는 DMX 내용 쿼리를 사용하여 모델의 부모 노드에서 메타데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-128">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8ab2a-129">CHILDREN_CARDINALITY 열의 이름을 대괄호로 묶어 동일한 이름의 MDX(Multidimensional Expressions) 예약 키워드와 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-129">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the Multidimensional Expressions (MDX) reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="8ab2a-130">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-130">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ab2a-131">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8ab2a-131">MODEL_CATALOG</span></span>|<span data-ttu-id="8ab2a-132">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="8ab2a-132">TM_Clustering</span></span>|  
|<span data-ttu-id="8ab2a-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8ab2a-133">MODEL_NAME</span></span>|<span data-ttu-id="8ab2a-134">Adventure Works DW</span><span class="sxs-lookup"><span data-stu-id="8ab2a-134">Adventure Works DW</span></span>|  
|<span data-ttu-id="8ab2a-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8ab2a-135">NODE_CAPTION</span></span>|<span data-ttu-id="8ab2a-136">클러스터 모델</span><span class="sxs-lookup"><span data-stu-id="8ab2a-136">Cluster Model</span></span>|  
|<span data-ttu-id="8ab2a-137">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8ab2a-137">NODE_SUPPORT</span></span>|<span data-ttu-id="8ab2a-138">12939</span><span class="sxs-lookup"><span data-stu-id="8ab2a-138">12939</span></span>|  
|<span data-ttu-id="8ab2a-139">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8ab2a-139">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="8ab2a-140">10</span><span class="sxs-lookup"><span data-stu-id="8ab2a-140">10</span></span>|  
|<span data-ttu-id="8ab2a-141">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8ab2a-141">NODE_DESCRIPTION</span></span>|<span data-ttu-id="8ab2a-142">모두</span><span class="sxs-lookup"><span data-stu-id="8ab2a-142">All</span></span>|  
  
 <span data-ttu-id="8ab2a-143">클러스터링 모델에서 이러한 열의 의미에 대한 정의는 [클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-143">For a definition of what these columns mean in a clustering model, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="8ab2a-144">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-144">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="8ab2a-145">예제 쿼리 2: 스키마 행 집합에서 모델 메타 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="8ab2a-145">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="8ab2a-146">데이터 마이닝 스키마 행 집합을 쿼리하면 DMX 내용 쿼리에 반환되는 것과 동일한 정보를 찾을 수 있는데,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-146">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="8ab2a-147">스키마 행 집합은 몇 개의 열을 추가로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-147">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="8ab2a-148">여기에는 모델을 만들 때 사용했던 매개 변수, 모델이 마지막으로 처리된 날짜와 시간, 모델 소유자 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-148">These include the parameters that were used when the model was created, the date and time that the model was last processed, and the owner of the model.</span></span>  
  
 <span data-ttu-id="8ab2a-149">다음 예에서는 모델을 만든 날짜, 수정한 날짜 및 마지막으로 처리한 날짜와 함께 모델을 작성하는 데 사용한 클러스터링 매개 변수와 학습 집합의 크기를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-149">The following example returns the date the model was created, modified, and last processed, together with the clustering parameters that were used to build the model, and the size of the training set.</span></span> <span data-ttu-id="8ab2a-150">이 정보는 모델을 문서화하거나 기존 모델을 만들 때 사용했던 클러스터링 옵션을 확인하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-150">This information can be useful for documenting the model, or for determining which of the clustering options were used to create an existing model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Clustering'  
```  
  
 <span data-ttu-id="8ab2a-151">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-151">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ab2a-152">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8ab2a-152">MODEL_NAME</span></span>|<span data-ttu-id="8ab2a-153">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="8ab2a-153">TM_Clustering</span></span>|  
|<span data-ttu-id="8ab2a-154">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8ab2a-154">DATE_CREATED</span></span>|<span data-ttu-id="8ab2a-155">10/12/2007 7:42:51 PM</span><span class="sxs-lookup"><span data-stu-id="8ab2a-155">10/12/2007 7:42:51 PM</span></span>|  
|<span data-ttu-id="8ab2a-156">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="8ab2a-156">LAST_PROCESSED</span></span>|<span data-ttu-id="8ab2a-157">10/12/2007 8:09:54 PM</span><span class="sxs-lookup"><span data-stu-id="8ab2a-157">10/12/2007 8:09:54 PM</span></span>|  
|<span data-ttu-id="8ab2a-158">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="8ab2a-158">PREDICTION_ENTITY</span></span>|<span data-ttu-id="8ab2a-159">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="8ab2a-159">Bike Buyer</span></span>|  
|<span data-ttu-id="8ab2a-160">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ab2a-160">MINING_PARAMETERS</span></span>|<span data-ttu-id="8ab2a-161">CLUSTER_COUNT=10,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-161">CLUSTER_COUNT=10,</span></span><br /><br /> <span data-ttu-id="8ab2a-162">CLUSTER_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-162">CLUSTER_SEED=0,</span></span><br /><br /> <span data-ttu-id="8ab2a-163">CLUSTERING_METHOD=1,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-163">CLUSTERING_METHOD=1,</span></span><br /><br /> <span data-ttu-id="8ab2a-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="8ab2a-165">MAXIMUM_STATES=100,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-165">MAXIMUM_STATES=100,</span></span><br /><br /> <span data-ttu-id="8ab2a-166">MINIMUM_SUPPORT=1,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-166">MINIMUM_SUPPORT=1,</span></span><br /><br /> <span data-ttu-id="8ab2a-167">MODELLING_CARDINALITY=10,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-167">MODELLING_CARDINALITY=10,</span></span><br /><br /> <span data-ttu-id="8ab2a-168">SAMPLE_SIZE=50000,</span><span class="sxs-lookup"><span data-stu-id="8ab2a-168">SAMPLE_SIZE=50000,</span></span><br /><br /> <span data-ttu-id="8ab2a-169">STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="8ab2a-169">STOPPING_TOLERANCE=10</span></span>|  
  
 [<span data-ttu-id="8ab2a-170">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-170">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-clusters"></a><span data-ttu-id="8ab2a-171">클러스터 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-171">Finding Information about Clusters</span></span>  
 <span data-ttu-id="8ab2a-172">클러스터링 모델에 대한 가장 유용한 내용 쿼리는 일반적으로 **클러스터 뷰어**에서 찾아볼 수 있는 것과 동일한 유형의 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-172">The most useful content queries on clustering models generally return the same type of information that you can browse by using the **Cluster Viewer**.</span></span> <span data-ttu-id="8ab2a-173">여기에는 클러스터 프로필, 클러스터 특징 및 클러스터 판별 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-173">This includes cluster profiles, cluster characteristics, and cluster discrimination.</span></span> <span data-ttu-id="8ab2a-174">이 섹션에서는 이러한 정보를 검색하는 예제 쿼리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-174">This section provides examples of queries that retrieve this information.</span></span>  
  
###  <a name="sample-query-3-returning-a-cluster-or-list-of-clusters"></a><a name="bkmk_Query3"></a> <span data-ttu-id="8ab2a-175">예제 쿼리 3: 클러스터 또는 클러스터 목록 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-175">Sample Query 3: Returning a Cluster or List of Clusters</span></span>  
 <span data-ttu-id="8ab2a-176">모든 클러스터의 노드 유형이 5이므로 모델 콘텐츠에서 해당 유형의 노드만 쿼리하면 클러스터 목록을 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-176">Because all clusters have a node type of 5, you can easily retrieve a list of the clusters by querying the model content for only the nodes of that type.</span></span> <span data-ttu-id="8ab2a-177">이 예에서와 같이 확률 또는 지지도로 반환되는 노드를 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-177">You can also filter the nodes that are returned by probability or by support, as shown in this example.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION ,NODE_SUPPORT, NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 5 AND NODE_SUPPORT > 1000  
```  
  
 <span data-ttu-id="8ab2a-178">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-178">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ab2a-179">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8ab2a-179">NODE_NAME</span></span>|<span data-ttu-id="8ab2a-180">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-180">002</span></span>|  
|<span data-ttu-id="8ab2a-181">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8ab2a-181">NODE_CAPTION</span></span>|<span data-ttu-id="8ab2a-182">클러스터 2</span><span class="sxs-lookup"><span data-stu-id="8ab2a-182">Cluster 2</span></span>|  
|<span data-ttu-id="8ab2a-183">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8ab2a-183">NODE_SUPPORT</span></span>|<span data-ttu-id="8ab2a-184">1649</span><span class="sxs-lookup"><span data-stu-id="8ab2a-184">1649</span></span>|  
|<span data-ttu-id="8ab2a-185">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8ab2a-185">NODE_DESCRIPTION</span></span>|<span data-ttu-id="8ab2a-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span><span class="sxs-lookup"><span data-stu-id="8ab2a-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span></span>|  
  
 <span data-ttu-id="8ab2a-187">클러스터를 정의하는 특성은 데이터 마이닝 스키마 행 집합의 두 열에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-187">The attributes that define the cluster can be found in two columns in the data mining schema rowset.</span></span>  
  
-   <span data-ttu-id="8ab2a-188">NODE_DESCRIPTION 열에는 쉼표로 구분된 특성 목록이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-188">The NODE_DESCRIPTION column contains a comma-separated list of attributes.</span></span> <span data-ttu-id="8ab2a-189">특성 목록이 표시용으로 축약될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-189">Note that the list of attributes might be abbreviated for display purposes.</span></span>  
  
-   <span data-ttu-id="8ab2a-190">NODE_DISTRIBUTION 열의 중첩 테이블에는 클러스터에 대한 전체 특성 목록이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-190">The nested table in the NODE_DISTRIBUTION column contains the full list of attributes for the cluster.</span></span> <span data-ttu-id="8ab2a-191">클라이언트에서 계층적 행 집합을 지원하지 않는 경우 SELECT 열 목록 앞에 FLATTEN 키워드를 추가하여 중첩 테이블을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-191">If your client does not support hierarchical rowsets, you can return the nested table by adding the FLATTENED keyword before the SELECT column list.</span></span> <span data-ttu-id="8ab2a-192">FLATTENED 키워드 사용에 대한 자세한 내용은 [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-192">For more information about the use of the FLATTENED keyword, see [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx).</span></span>  
  
 [<span data-ttu-id="8ab2a-193">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-193">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-4-returning-attributes-for-a-cluster"></a><a name="bkmk_Query4"></a> <span data-ttu-id="8ab2a-194">예제 쿼리 4: 클러스터에 대한 특성 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-194">Sample Query 4: Returning Attributes for a Cluster</span></span>  
 <span data-ttu-id="8ab2a-195">**클러스터 뷰어** 에는 각 클러스터의 특성과 특성 값을 나열하는 프로필이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-195">For every cluster, the **Cluster Viewer** displays a profile that lists the attributes and their values.</span></span> <span data-ttu-id="8ab2a-196">또한 모델에 포함된 사례의 전체 모집단에 대한 값 분포를 보여 주는 히스토그램도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-196">The viewer also displays a histogram that shows the distribution of values for the whole population of cases in the model.</span></span> <span data-ttu-id="8ab2a-197">뷰어에서 모델을 검색하는 경우 마이닝 범례에서 히스토그램을 손쉽게 복사한 다음 Excel 또는 Word 문서에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-197">If you are browsing the model in the viewer, you can easily copy the histogram from the Mining Legend and then paste it to Excel or a Word document.</span></span> <span data-ttu-id="8ab2a-198">또한 뷰어의 클러스터 특징 창에서 다른 클러스터의 특성을 그래픽으로 비교할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-198">You can also use the Cluster Characteristics pane of the viewer to graphically compare the attributes of different clusters.</span></span>  
  
 <span data-ttu-id="8ab2a-199">그러나 한 번에 둘 이상의 클러스터에 대한 값을 구해야 하는 경우 모델을 쿼리하는 것이 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-199">However, if you must obtain values for more than one cluster at a time, it is easier to query the model.</span></span> <span data-ttu-id="8ab2a-200">예를 들어 모델을 검색할 때 `Number Cars Owned`특성과 관련하여 상위 두 클러스터가 서로 다를 경우</span><span class="sxs-lookup"><span data-stu-id="8ab2a-200">For example, when you browse the model, you might notice that the top two clusters differ with regard to one attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="8ab2a-201">각 클러스터에 대한 값을 추출하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-201">Therefore, you want to extract the values for each cluster.</span></span>  
  
```  
SELECT TOP 2 NODE_NAME,   
(SELECT ATTRIBUTE_VALUE, [PROBABILITY] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Number Cars Owned')  
AS t  
FROM [TM_Clustering].CONTENT  
WHERE NODE_TYPE = 5  
```  
  
 <span data-ttu-id="8ab2a-202">첫 번째 코드 줄에는 상위 두 클러스터만 사용하도록 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-202">The first line of the code specifies that you want only the top two clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ab2a-203">기본적으로 클러스터는 지지도 순으로 순서가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-203">By default, the clusters are ordered by support.</span></span> <span data-ttu-id="8ab2a-204">따라서 NODE_SUPPORT 열은 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-204">Therefore, the NODE_SUPPORT column can be omitted.</span></span>  
  
 <span data-ttu-id="8ab2a-205">두 번째 코드 줄에는 중첩 테이블 열에서 특정 열만 반환하는 하위 SELECT 문이 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-205">The second line of the code adds a sub-select statement that returns only certain columns from the nested table column.</span></span> <span data-ttu-id="8ab2a-206">또한 중첩 테이블의 행을 대상 특성 `Number Cars Owned`와 관련된 행으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-206">Furthermore, it restricts the rows from the nested table to those related to the target attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="8ab2a-207">간단하게 표시하기 위해 중첩 테이블은 별칭으로 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-207">To simplify the display, the nested table is aliased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ab2a-208">중첩 테이블 열 `PROBABILITY`는 MDX 예약어의 이름이기도 하므로 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-208">The nested table column, `PROBABILITY`, must be enclosed in brackets because it is also the name of a reserved MDX keyword.</span></span>  
>   
>  <span data-ttu-id="8ab2a-209">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-209">Example results:</span></span>  
  
|<span data-ttu-id="8ab2a-210">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8ab2a-210">NODE_NAME</span></span>|<span data-ttu-id="8ab2a-211">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="8ab2a-211">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="8ab2a-212">T.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8ab2a-212">T.PROBABILITY</span></span>|  
|----------------|------------------------|-------------------|  
|<span data-ttu-id="8ab2a-213">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-213">001</span></span>|<span data-ttu-id="8ab2a-214">2</span><span class="sxs-lookup"><span data-stu-id="8ab2a-214">2</span></span>|<span data-ttu-id="8ab2a-215">0.829207754</span><span class="sxs-lookup"><span data-stu-id="8ab2a-215">0.829207754</span></span>|  
|<span data-ttu-id="8ab2a-216">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-216">001</span></span>|<span data-ttu-id="8ab2a-217">1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-217">1</span></span>|<span data-ttu-id="8ab2a-218">0.109354156</span><span class="sxs-lookup"><span data-stu-id="8ab2a-218">0.109354156</span></span>|  
|<span data-ttu-id="8ab2a-219">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-219">001</span></span>|<span data-ttu-id="8ab2a-220">3</span><span class="sxs-lookup"><span data-stu-id="8ab2a-220">3</span></span>|<span data-ttu-id="8ab2a-221">0.034481552</span><span class="sxs-lookup"><span data-stu-id="8ab2a-221">0.034481552</span></span>|  
|<span data-ttu-id="8ab2a-222">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-222">001</span></span>|<span data-ttu-id="8ab2a-223">4</span><span class="sxs-lookup"><span data-stu-id="8ab2a-223">4</span></span>|<span data-ttu-id="8ab2a-224">0.013503302</span><span class="sxs-lookup"><span data-stu-id="8ab2a-224">0.013503302</span></span>|  
|<span data-ttu-id="8ab2a-225">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-225">001</span></span>|<span data-ttu-id="8ab2a-226">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-226">0</span></span>|<span data-ttu-id="8ab2a-227">0.013453236</span><span class="sxs-lookup"><span data-stu-id="8ab2a-227">0.013453236</span></span>|  
|<span data-ttu-id="8ab2a-228">001</span><span class="sxs-lookup"><span data-stu-id="8ab2a-228">001</span></span>|<span data-ttu-id="8ab2a-229">Missing</span><span class="sxs-lookup"><span data-stu-id="8ab2a-229">Missing</span></span>|<span data-ttu-id="8ab2a-230">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-230">0</span></span>|  
|<span data-ttu-id="8ab2a-231">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-231">002</span></span>|<span data-ttu-id="8ab2a-232">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-232">0</span></span>|<span data-ttu-id="8ab2a-233">0.576980023</span><span class="sxs-lookup"><span data-stu-id="8ab2a-233">0.576980023</span></span>|  
|<span data-ttu-id="8ab2a-234">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-234">002</span></span>|<span data-ttu-id="8ab2a-235">1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-235">1</span></span>|<span data-ttu-id="8ab2a-236">0.406623939</span><span class="sxs-lookup"><span data-stu-id="8ab2a-236">0.406623939</span></span>|  
|<span data-ttu-id="8ab2a-237">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-237">002</span></span>|<span data-ttu-id="8ab2a-238">2</span><span class="sxs-lookup"><span data-stu-id="8ab2a-238">2</span></span>|<span data-ttu-id="8ab2a-239">0.016380082</span><span class="sxs-lookup"><span data-stu-id="8ab2a-239">0.016380082</span></span>|  
|<span data-ttu-id="8ab2a-240">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-240">002</span></span>|<span data-ttu-id="8ab2a-241">3</span><span class="sxs-lookup"><span data-stu-id="8ab2a-241">3</span></span>|<span data-ttu-id="8ab2a-242">1.60E-05</span><span class="sxs-lookup"><span data-stu-id="8ab2a-242">1.60E-05</span></span>|  
|<span data-ttu-id="8ab2a-243">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-243">002</span></span>|<span data-ttu-id="8ab2a-244">4</span><span class="sxs-lookup"><span data-stu-id="8ab2a-244">4</span></span>|<span data-ttu-id="8ab2a-245">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-245">0</span></span>|  
|<span data-ttu-id="8ab2a-246">002</span><span class="sxs-lookup"><span data-stu-id="8ab2a-246">002</span></span>|<span data-ttu-id="8ab2a-247">Missing</span><span class="sxs-lookup"><span data-stu-id="8ab2a-247">Missing</span></span>|<span data-ttu-id="8ab2a-248">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-248">0</span></span>|  
  
 [<span data-ttu-id="8ab2a-249">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-249">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-return-a-cluster-profile-using-system-stored-procedures"></a><a name="bkmk_Query5"></a> <span data-ttu-id="8ab2a-250">예제 쿼리 5: 시스템 저장 프로시저를 사용하여 클러스터 프로필 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-250">Sample Query 5: Return a Cluster Profile Using System Stored Procedures</span></span>  
 <span data-ttu-id="8ab2a-251">DMX를 사용하여 직접 쿼리를 작성하는 것보다는 클러스터 작업을 위해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용하는 시스템 저장 프로시저를 호출하는 것이 더 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-251">As a shortcut, rather than writing your own queries by using DMX, you can also call the system stored procedures that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to work with clusters.</span></span> <span data-ttu-id="8ab2a-252">다음 예에서는 내부 저장 프로시저를 사용하여 ID가 002인 클러스터에 대한 프로필을 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-252">The following example illustrates how to use the internal stored procedures to return the profile for a cluster with the ID of 002.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('TM_Clustering", '002',0.0005  
```  
  
 <span data-ttu-id="8ab2a-253">마찬가지로 다음 예에서와 같이 시스템 저장 프로시저를 사용하여 특정 클러스터의 특징을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-253">Similarly, you can use a system stored procedure to return the characteristics of a specific cluster, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('TM_Clustering", '009',0.0005  
```  
  
 <span data-ttu-id="8ab2a-254">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-254">Example results:</span></span>  
  
|<span data-ttu-id="8ab2a-255">특성</span><span class="sxs-lookup"><span data-stu-id="8ab2a-255">Attributes</span></span>|<span data-ttu-id="8ab2a-256">값</span><span class="sxs-lookup"><span data-stu-id="8ab2a-256">Values</span></span>|<span data-ttu-id="8ab2a-257">빈도</span><span class="sxs-lookup"><span data-stu-id="8ab2a-257">Frequency</span></span>|<span data-ttu-id="8ab2a-258">지원</span><span class="sxs-lookup"><span data-stu-id="8ab2a-258">Support</span></span>|  
|----------------|------------|---------------|-------------|  
|<span data-ttu-id="8ab2a-259">Number Children at Home</span><span class="sxs-lookup"><span data-stu-id="8ab2a-259">Number Children at Home</span></span>|<span data-ttu-id="8ab2a-260">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-260">0</span></span>|<span data-ttu-id="8ab2a-261">0.999999829076798</span><span class="sxs-lookup"><span data-stu-id="8ab2a-261">0.999999829076798</span></span>|<span data-ttu-id="8ab2a-262">899</span><span class="sxs-lookup"><span data-stu-id="8ab2a-262">899</span></span>|  
|<span data-ttu-id="8ab2a-263">지역</span><span class="sxs-lookup"><span data-stu-id="8ab2a-263">Region</span></span>|<span data-ttu-id="8ab2a-264">북아메리카</span><span class="sxs-lookup"><span data-stu-id="8ab2a-264">North America</span></span>|<span data-ttu-id="8ab2a-265">0.999852875241508</span><span class="sxs-lookup"><span data-stu-id="8ab2a-265">0.999852875241508</span></span>|<span data-ttu-id="8ab2a-266">899</span><span class="sxs-lookup"><span data-stu-id="8ab2a-266">899</span></span>|  
|<span data-ttu-id="8ab2a-267">Total Children</span><span class="sxs-lookup"><span data-stu-id="8ab2a-267">Total Children</span></span>|<span data-ttu-id="8ab2a-268">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-268">0</span></span>|<span data-ttu-id="8ab2a-269">0.993860958572323</span><span class="sxs-lookup"><span data-stu-id="8ab2a-269">0.993860958572323</span></span>|<span data-ttu-id="8ab2a-270">893</span><span class="sxs-lookup"><span data-stu-id="8ab2a-270">893</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8ab2a-271">데이터 마이닝 시스템 저장 프로시저는 내부적으로만 사용할 수 있으며 필요에 따라 이 프로시저를 변경할 수 있는 권한은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-271">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="8ab2a-272">따라서 프로덕션 환경에서는 DMX, AMO 또는 XMLA를 사용하여 쿼리를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-272">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="8ab2a-273">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-273">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-6-find-discriminating-factors-for-a-cluster"></a><a name="bkmk_Query6"></a> <span data-ttu-id="8ab2a-274">예제 쿼리 6: 클러스터에 대한 판별 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-274">Sample Query 6: Find Discriminating Factors for a Cluster</span></span>  
 <span data-ttu-id="8ab2a-275">**클러스터 뷰어** 의 **클러스터 판별** 탭에서는 손쉽게 한 클러스터와 다른 클러스터를 비교하거나, 한 클러스터와 나머지 모든 사례(나머지 클러스터)를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-275">The **Cluster Discrimination** tab of the **Cluster Viewer** enables you to easily compare a cluster with another cluster, or compare a cluster with all remaining cases (the complement of the cluster).</span></span>  
  
 <span data-ttu-id="8ab2a-276">그러나 이러한 정보를 반환하는 쿼리를 만드는 것이 복잡할 수 있으며 임시 결과를 저장하고 둘 이상의 쿼리 결과를 비교하기 위해서는 클라이언트에서 약간의 추가 처리가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-276">However, creating queries to return this information can be complex, and you might need some additional processing on the client to store the temporary results and compare the results of two or more queries.</span></span> <span data-ttu-id="8ab2a-277">이 경우 간단하게 시스템 저장 프로시저를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-277">As a shortcut, you can use the system stored procedures.</span></span>  
  
 <span data-ttu-id="8ab2a-278">다음 쿼리는 노드 ID가 각각 009와 007인 두 클러스터 간의 주요 판별 요소를 나타내는 단일 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-278">The following query returns a single table that indicates the primary discriminating factors between the two clusters that have the node IDs of 009 and 007.</span></span> <span data-ttu-id="8ab2a-279">양수 값을 갖는 특성은 클러스터 009를 선호하며 음수 값을 갖는 특성은 클러스터 007을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-279">Attributes with positive values favor cluster 009, whereas attributes with negative values favor cluster 007.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','007',0.0005,true)  
```  
  
 <span data-ttu-id="8ab2a-280">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-280">Example results:</span></span>  
  
|<span data-ttu-id="8ab2a-281">특성</span><span class="sxs-lookup"><span data-stu-id="8ab2a-281">Attributes</span></span>|<span data-ttu-id="8ab2a-282">값</span><span class="sxs-lookup"><span data-stu-id="8ab2a-282">Values</span></span>|<span data-ttu-id="8ab2a-283">점수 매기기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-283">Score</span></span>|  
|----------------|------------|-----------|  
|<span data-ttu-id="8ab2a-284">지역</span><span class="sxs-lookup"><span data-stu-id="8ab2a-284">Region</span></span>|<span data-ttu-id="8ab2a-285">북아메리카</span><span class="sxs-lookup"><span data-stu-id="8ab2a-285">North America</span></span>|<span data-ttu-id="8ab2a-286">100</span><span class="sxs-lookup"><span data-stu-id="8ab2a-286">100</span></span>|  
|<span data-ttu-id="8ab2a-287">English Occupation</span><span class="sxs-lookup"><span data-stu-id="8ab2a-287">English Occupation</span></span>|<span data-ttu-id="8ab2a-288">Skilled Manual</span><span class="sxs-lookup"><span data-stu-id="8ab2a-288">Skilled Manual</span></span>|<span data-ttu-id="8ab2a-289">94.9003803898654</span><span class="sxs-lookup"><span data-stu-id="8ab2a-289">94.9003803898654</span></span>|  
|<span data-ttu-id="8ab2a-290">지역</span><span class="sxs-lookup"><span data-stu-id="8ab2a-290">Region</span></span>|<span data-ttu-id="8ab2a-291">유럽</span><span class="sxs-lookup"><span data-stu-id="8ab2a-291">Europe</span></span>|<span data-ttu-id="8ab2a-292">-72.5041051379789</span><span class="sxs-lookup"><span data-stu-id="8ab2a-292">-72.5041051379789</span></span>|  
|<span data-ttu-id="8ab2a-293">English Occupation</span><span class="sxs-lookup"><span data-stu-id="8ab2a-293">English Occupation</span></span>|<span data-ttu-id="8ab2a-294">설명서</span><span class="sxs-lookup"><span data-stu-id="8ab2a-294">Manual</span></span>|<span data-ttu-id="8ab2a-295">-69.6503163202722</span><span class="sxs-lookup"><span data-stu-id="8ab2a-295">-69.6503163202722</span></span>|  
  
 <span data-ttu-id="8ab2a-296">첫 번째 드롭다운 목록에서 클러스터 9를 선택하고 두 번째 드롭다운 목록에서 클러스터 7을 선택한 경우 이는 **클러스터 판별** 뷰어의 차트에 표시되는 정보와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-296">This is the same information that is presented in the chart of the **Cluster Discrimination** viewer if you select Cluster 9 from the first drop-down list and Cluster 7 from the second drop-down list.</span></span> <span data-ttu-id="8ab2a-297">클러스터 9를 나머지 클러스터와 비교하려면 다음 예에서와 같이 두 번째 매개 변수에 빈 문자열을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-297">To compare cluster 9 with its complement, you use the empty string in the second parameter, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','',0.0005,true)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8ab2a-298">데이터 마이닝 시스템 저장 프로시저는 내부적으로만 사용할 수 있으며 필요에 따라 이 프로시저를 변경할 수 있는 권한은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-298">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="8ab2a-299">따라서 프로덕션 환경에서는 DMX, AMO 또는 XMLA를 사용하여 쿼리를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-299">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="8ab2a-300">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-300">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-returning-cases-that-belong-to-a-cluster"></a><a name="bkmk_Query7"></a> <span data-ttu-id="8ab2a-301">예제 쿼리 7: 클러스터에 속한 사례 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-301">Sample Query 7: Returning Cases that Belong to a Cluster</span></span>  
 <span data-ttu-id="8ab2a-302">마이닝 모델에 드릴스루를 사용하도록 설정한 경우 모델에 사용된 사례에 대한 세부 정보를 반환하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-302">If drillthrough has been enabled on the mining model, you can create queries that return detailed information about the cases used in the model.</span></span> <span data-ttu-id="8ab2a-303">또한 마이닝 구조에도 드릴스루를 사용하도록 설정한 경우 [StructureColumn&#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 함수를 사용하여 기본 구조의 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-303">Moreover, if drillthrough has been enabled on the mining structure, you can include columns from the underlying structure by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="8ab2a-304">다음 예에서는 모델에 사용된 Age 및 Region 열과 모델에 사용되지 않은 First Name 열을 추가로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-304">The following example returns two columns that were used in the model, Age and Region, and one more column, First Name, that was not used in the model.</span></span> <span data-ttu-id="8ab2a-305">이 쿼리는 Cluster 1로 분류된 사례만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-305">The query returns only cases that were classified into Cluster 1.</span></span>  
  
```  
SELECT [Age], [Region], StructureColumn('First Name')  
FROM [TM_Clustering].CASES  
WHERE IsInNode('001')  
```  
  
 <span data-ttu-id="8ab2a-306">클러스터에 속한 사례를 반환하려면 클러스터 ID를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-306">To return the cases that belong to a cluster, you must know the ID of the cluster.</span></span> <span data-ttu-id="8ab2a-307">클러스터 ID는 뷰어 중 하나에서 모델을 탐색하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-307">You can obtain the ID of the cluster by browsing the model in one of the viewers.</span></span> <span data-ttu-id="8ab2a-308">또는 보다 쉬운 참조를 위해 클러스터의 이름을 바꾼 다음 ID 번호 대신 바꾼 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-308">Or, you can rename a cluster for easier reference, after which you could use the name in place of an ID number.</span></span> <span data-ttu-id="8ab2a-309">그러나 모델을 다시 처리하면 클러스터에 할당된 이름이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-309">However, know that the names that you assign to a cluster will be lost if the model is reprocessed.</span></span>  
  
 [<span data-ttu-id="8ab2a-310">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-310">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="8ab2a-311">모델을 사용하여 예측 수행</span><span class="sxs-lookup"><span data-stu-id="8ab2a-311">Making Predictions using the Model</span></span>  
 <span data-ttu-id="8ab2a-312">데이터를 설명하고 이해하는 데 클러스터링이 일반적으로 사용되지만 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 구현을 사용해도 클러스터 멤버 자격에 대한 예측을 만들고 예측과 연관된 확률을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-312">Although clustering is typically used for describing and understanding data, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation also lets you make prediction about cluster membership, and return probabilities associated with the prediction.</span></span> <span data-ttu-id="8ab2a-313">이 섹션에서는 클러스터링 모델에 대한 예측 쿼리를 만드는 방법에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-313">This section provides examples of how to create prediction queries on clustering models.</span></span> <span data-ttu-id="8ab2a-314">테이블 형식 데이터 원본을 지정하여 여러 사례에 대한 예측을 만들거나 단일 쿼리를 만들어 한 번에 새 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-314">You can make predictions for multiple cases, by specifying a tabular data source, or you can provide new values on at a time by creating a singleton query.</span></span> <span data-ttu-id="8ab2a-315">의미를 명확하게 전달하기 위해 이 섹션의 예는 모두 단일 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-315">For clarity the examples in this section are all singleton queries.</span></span>  
  
 <span data-ttu-id="8ab2a-316">DMX를 사용 하 여 예측 쿼리를 만드는 방법에 대 한 자세한 내용은 [데이터 마이닝 쿼리 인터페이스](data-mining-query-tools.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-316">For more information about how to create prediction queries using DMX, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
 [<span data-ttu-id="8ab2a-317">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-317">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-8-predicting-outcomes-from-a-clustering-model"></a><a name="bkmk_Query8"></a> <span data-ttu-id="8ab2a-318">예제 쿼리 8: 클러스터링 모델에서 결과 예측</span><span class="sxs-lookup"><span data-stu-id="8ab2a-318">Sample Query 8: Predicting Outcomes from a Clustering Model</span></span>  
 <span data-ttu-id="8ab2a-319">만든 클러스터링 모델에 예측 가능한 특성이 포함되어 있는 경우 이 모델을 사용하여 결과에 대한 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-319">If the clustering model you create contains a predictable attribute, you can use the model to make predictions about outcomes.</span></span> <span data-ttu-id="8ab2a-320">그러나 예측 가능한 열을 `Predict`로 설정했는지 또는 `PredictOnly`로 설정했는지에 따라 모델이 예측 가능한 특성을 다르게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-320">However, the model handles the predictable attribute differently depending on whether you set the predictable column to `Predict` or `PredictOnly`.</span></span> <span data-ttu-id="8ab2a-321">열 사용법을 `Predict`로 설정하면 해당 특성 값이 클러스터링 모델에 추가되고 완성된 모델에 특성으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-321">If you set the usage of the column to `Predict`, the values for that attribute are added to the clustering model and appear as attributes in the finished model.</span></span> <span data-ttu-id="8ab2a-322">그러나 열 사용법을 `PredictOnly`로 설정하면 해당 값이 클러스터를 만드는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-322">However, if you set the usage of the column to `PredictOnly`, the values are not used to create clusters.</span></span> <span data-ttu-id="8ab2a-323">대신 모델이 완성된 후 클러스터링 알고리즘이 각 사례가 속해 있는 클러스터를 기반으로 `PredictOnly` 특성에 대한 새 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-323">Instead, after the mode is completed, the clustering algorithm creates new values for the `PredictOnly` attribute based on the clusters to which each case belongs.</span></span>  
  
 <span data-ttu-id="8ab2a-324">다음 쿼리는 모델에 새로운 단일 사례를 제공하는데, 사례에 대한 유일한 정보는 연령과 성별입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-324">The following query provides a single new case to the model, where the only information about the case is the age and gender.</span></span> <span data-ttu-id="8ab2a-325">SELECT 문에 관심 있는 예측 가능한 특성/값 쌍을 지정하고 [PredictProbability&#40;DMX&#41;](/sql/dmx/predictprobability-dmx) 함수는 이러한 특성이 포함된 사례의 대상 결과 확률을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-325">The SELECT statement specifies the predictable attribute/value pair that you are interested in, and the [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) function tells you the probability that a case with those attributes will have the targeted outcome.</span></span>  
  
```  
SELECT  
  [TM_Clustering].[Bike Buyer], PredictProbability([Bike Buyer],1)  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="8ab2a-326">열 사용법이 `Predict`로 설정된 경우의 예제 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-326">Example of results when usage is set to `Predict`:</span></span>  
  
|<span data-ttu-id="8ab2a-327">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="8ab2a-327">Bike Buyer</span></span>|<span data-ttu-id="8ab2a-328">식</span><span class="sxs-lookup"><span data-stu-id="8ab2a-328">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="8ab2a-329">1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-329">1</span></span>|<span data-ttu-id="8ab2a-330">0.592924735740338</span><span class="sxs-lookup"><span data-stu-id="8ab2a-330">0.592924735740338</span></span>|  
  
 <span data-ttu-id="8ab2a-331">열 사용법이 `PredictOnly`로 설정되어 있고 모델이 다시 처리된 경우의 예제 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-331">Example of results when the usage is set to `PredictOnly` and the model is reprocessed:</span></span>  
  
|<span data-ttu-id="8ab2a-332">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="8ab2a-332">Bike Buyer</span></span>|<span data-ttu-id="8ab2a-333">식</span><span class="sxs-lookup"><span data-stu-id="8ab2a-333">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="8ab2a-334">1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-334">1</span></span>|<span data-ttu-id="8ab2a-335">0.55843544003102</span><span class="sxs-lookup"><span data-stu-id="8ab2a-335">0.55843544003102</span></span>|  
  
 <span data-ttu-id="8ab2a-336">이 예에서 모델의 차이는 그다지 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-336">In this example, the difference in the model is not significant.</span></span> <span data-ttu-id="8ab2a-337">그러나 실제 값 분포와 모델에서 예측하는 분포의 차이를 알아내는 것이 때로는 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-337">However, sometimes it can be important to detect differences between the actual distribution of values and what the model predicts.</span></span> <span data-ttu-id="8ab2a-338">[PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 함수는 해당 모델이 제공될 경우 사례가 나타날 가능성을 알려 주므로 이러한 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-338">The [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function is useful in this scenario, because it tells you how likely a case is, given the model.</span></span>  
  
 <span data-ttu-id="8ab2a-339">PredictCaseLikelihood 함수에 의해 반환되는 값은 확률이므로 항상 0과 1 사이이며 임의의 결과를 나타내는 경우 값이 .5입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-339">The number that is returned by the PredictCaseLikelihood function is a probability, and therefore is always between 0 and 1, with a value of .5 representing random outcome.</span></span> <span data-ttu-id="8ab2a-340">그러므로 점수가 .5 미만인 경우 해당 모델이 제공될 경우 예측 사례가 나타날 가능성이 별로 없음을 의미하고 점수가 .5 이상인 경우에는 예측 사례가 해당 모델에 적합하지 않은 경우보다 나타날 가능성이 높음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-340">Therefore, a score less than .5 means that the predicted case is unlikely, given the model, and a score over.5 indicates that the predicted case is more likely than not to fit the model.</span></span>  
  
 <span data-ttu-id="8ab2a-341">예를 들어 다음 쿼리는 새로운 샘플 사례가 나타날 가능성의 특징을 결정하는 두 개의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-341">For example, the following query returns two values that characterize the likelihood of a new sample case.</span></span> <span data-ttu-id="8ab2a-342">정규화되지 않은 값은 현재 모델이 제공될 경우의 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-342">The non-normalized value represents the probability given the current model.</span></span> <span data-ttu-id="8ab2a-343">NORMALIZED 키워드를 사용할 경우 함수에 의해 반환되는 유사도 점수는 "모델이 포함된 확률"을 "모델이 포함되지 않은 확률"로 나누어 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-343">When you use the NORMALIZED keyword, the likelihood score that is returned by the function is adjusted by dividing "probability with the model" by "probability without the model".</span></span>  
  
```  
SELECT  
PredictCaseLikelihood(NORMALIZED) AS [NormalizedValue], PredictCaseLikelihood(NONNORMALIZED) AS [NonNormalizedValue]  
FROM  
  [TM_Clustering_PredictOnly]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="8ab2a-344">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-344">Example results:</span></span>  
  
|<span data-ttu-id="8ab2a-345">NormalizedValue</span><span class="sxs-lookup"><span data-stu-id="8ab2a-345">NormalizedValue</span></span>|<span data-ttu-id="8ab2a-346">NonNormalizedValue</span><span class="sxs-lookup"><span data-stu-id="8ab2a-346">NonNormalizedValue</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="8ab2a-347">5.56438372679893E-11</span><span class="sxs-lookup"><span data-stu-id="8ab2a-347">5.56438372679893E-11</span></span>|<span data-ttu-id="8ab2a-348">8.65459953145182E-68</span><span class="sxs-lookup"><span data-stu-id="8ab2a-348">8.65459953145182E-68</span></span>|  
  
 <span data-ttu-id="8ab2a-349">이 결과 값은 과학적 표기법으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-349">Note that the numbers in these results are expressed in scientific notation.</span></span>  
  
 [<span data-ttu-id="8ab2a-350">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-350">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-9-determining-cluster-membership"></a><a name="bkmk_Query9"></a><span data-ttu-id="8ab2a-351">예제 쿼리 9: 클러스터 멤버 자격 확인</span><span class="sxs-lookup"><span data-stu-id="8ab2a-351">Sample Query 9: Determining Cluster Membership</span></span>  
 <span data-ttu-id="8ab2a-352">이 예에서는 [Cluster&#40;DMX&#41;](/sql/dmx/cluster-dmx) 함수를 사용하여 새로운 사례가 속해 있을 가능성이 가장 높은 클러스터를 반환하고, [ClusterProbability&#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) 함수를 사용하여 해당 클러스터의 멤버 자격에 대한 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-352">This example uses the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return the cluster to which the new case is most likely to belong, and uses the [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) function to return the probability for membership in that cluster.</span></span>  
  
```  
SELECT Cluster(), ClusterProbability()  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status]) AS t  
```  
  
 <span data-ttu-id="8ab2a-353">결과 예:</span><span class="sxs-lookup"><span data-stu-id="8ab2a-353">Example results:</span></span>  
  
|<span data-ttu-id="8ab2a-354">$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="8ab2a-354">$CLUSTER</span></span>|<span data-ttu-id="8ab2a-355">식</span><span class="sxs-lookup"><span data-stu-id="8ab2a-355">Expression</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="8ab2a-356">클러스터 2</span><span class="sxs-lookup"><span data-stu-id="8ab2a-356">Cluster 2</span></span>|<span data-ttu-id="8ab2a-357">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="8ab2a-357">0.397918596951617</span></span>|  
  
 <span data-ttu-id="8ab2a-358">**참고** 기본적으로이 `ClusterProbability` 함수는 가장 가능성이 높은 클러스터의 확률을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-358">**Note** By default, the `ClusterProbability` function returns the probability of the most likely cluster.</span></span> <span data-ttu-id="8ab2a-359">그러나 `ClusterProbability('cluster name')`구문을 사용하여 다른 클러스터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-359">However, you can specify a different cluster by using the syntax `ClusterProbability('cluster name')`.</span></span> <span data-ttu-id="8ab2a-360">이 경우 각 예측 함수의 결과는 다른 결과에 대해 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-360">If you do this, be aware that the results from each prediction function are independent of the other results.</span></span> <span data-ttu-id="8ab2a-361">따라서 두 번째 열의 확률 점수는 첫 번째 열에 명명된 클러스터가 아닌 다른 클러스터를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-361">Therefore, the probability score in the second column could refer to a different cluster than the cluster named in the first column.</span></span>  
  
 [<span data-ttu-id="8ab2a-362">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-362">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-10-returning-all-possible-clusters-with-probability-and-distance"></a><a name="bkmk_Query10"></a> <span data-ttu-id="8ab2a-363">예제 쿼리 10: 확률과 거리가 포함된 가능한 모든 클러스터 반환</span><span class="sxs-lookup"><span data-stu-id="8ab2a-363">Sample Query 10: Returning All Possible Clusters with Probability and Distance</span></span>  
 <span data-ttu-id="8ab2a-364">이전 예에서 확률 점수는 그리 높지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-364">In the previous example, the probability score was not very high.</span></span> <span data-ttu-id="8ab2a-365">보다 나은 클러스터가 있는지 확인하기 위해 [PredictHistogram&#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) 함수를 [Cluster&#40;DMX&#41;](/sql/dmx/cluster-dmx) 함수와 함께 사용하여 새로운 사례가 각 클러스터에 속해 있을 확률과 함께 가능한 모든 클러스터를 포함하는 중첩 테이블을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-365">To determine if there is a better cluster, you can use the [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) function together with the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return a nested table that includes all possible clusters, together with the probability that the new case that belongs to each cluster.</span></span> <span data-ttu-id="8ab2a-366">FLATTENED 키워드는 보다 쉽게 볼 수 있도록 계층적 행 집합을 플랫 테이블로 변경하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-366">The FLATTENED keyword is used to change the hierarchical rowset into a flat table for easier viewing.</span></span>  
  
```  
SELECT FLATTENED PredictHistogram(Cluster())  
From  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status])  
```  
  
|<span data-ttu-id="8ab2a-367">Expression.$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="8ab2a-367">Expression.$CLUSTER</span></span>|<span data-ttu-id="8ab2a-368">Expression.$DISTANCE</span><span class="sxs-lookup"><span data-stu-id="8ab2a-368">Expression.$DISTANCE</span></span>|<span data-ttu-id="8ab2a-369">Expression.$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8ab2a-369">Expression.$PROBABILITY</span></span>|  
|-------------------------|--------------------------|-----------------------------|  
|<span data-ttu-id="8ab2a-370">클러스터 2</span><span class="sxs-lookup"><span data-stu-id="8ab2a-370">Cluster 2</span></span>|<span data-ttu-id="8ab2a-371">0.602081403048383</span><span class="sxs-lookup"><span data-stu-id="8ab2a-371">0.602081403048383</span></span>|<span data-ttu-id="8ab2a-372">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="8ab2a-372">0.397918596951617</span></span>|  
|<span data-ttu-id="8ab2a-373">클러스터 10</span><span class="sxs-lookup"><span data-stu-id="8ab2a-373">Cluster 10</span></span>|<span data-ttu-id="8ab2a-374">0.719691686785675</span><span class="sxs-lookup"><span data-stu-id="8ab2a-374">0.719691686785675</span></span>|<span data-ttu-id="8ab2a-375">0.280308313214325</span><span class="sxs-lookup"><span data-stu-id="8ab2a-375">0.280308313214325</span></span>|  
|<span data-ttu-id="8ab2a-376">클러스터 4</span><span class="sxs-lookup"><span data-stu-id="8ab2a-376">Cluster 4</span></span>|<span data-ttu-id="8ab2a-377">0.867772590378791</span><span class="sxs-lookup"><span data-stu-id="8ab2a-377">0.867772590378791</span></span>|<span data-ttu-id="8ab2a-378">0.132227409621209</span><span class="sxs-lookup"><span data-stu-id="8ab2a-378">0.132227409621209</span></span>|  
|<span data-ttu-id="8ab2a-379">클러스터 5</span><span class="sxs-lookup"><span data-stu-id="8ab2a-379">Cluster 5</span></span>|<span data-ttu-id="8ab2a-380">0.931039872200985</span><span class="sxs-lookup"><span data-stu-id="8ab2a-380">0.931039872200985</span></span>|<span data-ttu-id="8ab2a-381">0.0689601277990149</span><span class="sxs-lookup"><span data-stu-id="8ab2a-381">0.0689601277990149</span></span>|  
|<span data-ttu-id="8ab2a-382">클러스터 3</span><span class="sxs-lookup"><span data-stu-id="8ab2a-382">Cluster 3</span></span>|<span data-ttu-id="8ab2a-383">0.942359230072167</span><span class="sxs-lookup"><span data-stu-id="8ab2a-383">0.942359230072167</span></span>|<span data-ttu-id="8ab2a-384">0.0576407699278328</span><span class="sxs-lookup"><span data-stu-id="8ab2a-384">0.0576407699278328</span></span>|  
|<span data-ttu-id="8ab2a-385">클러스터 6</span><span class="sxs-lookup"><span data-stu-id="8ab2a-385">Cluster 6</span></span>|<span data-ttu-id="8ab2a-386">0.958973668972756</span><span class="sxs-lookup"><span data-stu-id="8ab2a-386">0.958973668972756</span></span>|<span data-ttu-id="8ab2a-387">0.0410263310272437</span><span class="sxs-lookup"><span data-stu-id="8ab2a-387">0.0410263310272437</span></span>|  
|<span data-ttu-id="8ab2a-388">클러스터 7</span><span class="sxs-lookup"><span data-stu-id="8ab2a-388">Cluster 7</span></span>|<span data-ttu-id="8ab2a-389">0.979081275926724</span><span class="sxs-lookup"><span data-stu-id="8ab2a-389">0.979081275926724</span></span>|<span data-ttu-id="8ab2a-390">0.0209187240732763</span><span class="sxs-lookup"><span data-stu-id="8ab2a-390">0.0209187240732763</span></span>|  
|<span data-ttu-id="8ab2a-391">클러스터 1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-391">Cluster 1</span></span>|<span data-ttu-id="8ab2a-392">0.999169044818624</span><span class="sxs-lookup"><span data-stu-id="8ab2a-392">0.999169044818624</span></span>|<span data-ttu-id="8ab2a-393">0.000830955181376364</span><span class="sxs-lookup"><span data-stu-id="8ab2a-393">0.000830955181376364</span></span>|  
|<span data-ttu-id="8ab2a-394">클러스터 9</span><span class="sxs-lookup"><span data-stu-id="8ab2a-394">Cluster 9</span></span>|<span data-ttu-id="8ab2a-395">0.999831227795894</span><span class="sxs-lookup"><span data-stu-id="8ab2a-395">0.999831227795894</span></span>|<span data-ttu-id="8ab2a-396">0.000168772204105754</span><span class="sxs-lookup"><span data-stu-id="8ab2a-396">0.000168772204105754</span></span>|  
|<span data-ttu-id="8ab2a-397">클러스터 8</span><span class="sxs-lookup"><span data-stu-id="8ab2a-397">Cluster 8</span></span>|<span data-ttu-id="8ab2a-398">1</span><span class="sxs-lookup"><span data-stu-id="8ab2a-398">1</span></span>|<span data-ttu-id="8ab2a-399">0</span><span class="sxs-lookup"><span data-stu-id="8ab2a-399">0</span></span>|  
  
 <span data-ttu-id="8ab2a-400">기본적으로 결과는 확률 순으로 순위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-400">By default, the results are ranked by probability.</span></span> <span data-ttu-id="8ab2a-401">결과를 통해 Cluster 2의 확률이 매우 낮지만 그래도 Cluster 2가 새 데이터 요소에 가장 적합하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-401">The results tell you that, even though the probability for Cluster 2 is fairly low, Cluster 2 is still the best fit for the new data point.</span></span>  
  
 <span data-ttu-id="8ab2a-402">**참고** 추가 열 `$DISTANCE`는 데이터 요소에서 클러스터까지의 거리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-402">**Note** The additional column, `$DISTANCE`, represents the distance from the data point to the cluster.</span></span> <span data-ttu-id="8ab2a-403">기본적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터링 알고리즘은 Scalable EM 클러스터링을 사용하여 여러 개의 클러스터를 각 데이터 요소에 할당하고 가능한 클러스터의 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-403">By default, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering Algorithm uses scalable EM clustering, which assigns multiple clusters to each data point and ranks the possible clusters.</span></span>  <span data-ttu-id="8ab2a-404">그러나 K-Means 알고리즘을 사용하여 클러스터링 모델을 만드는 경우 각 데이터 요소에 한 개의 클러스터만 할당할 수 있으므로 이 쿼리는 한 개의 행만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-404">However, if you create your clustering model using the K-means algorithm, only one cluster can be assigned to each data point, and this query would return only one row.</span></span> <span data-ttu-id="8ab2a-405">[PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 함수를 사용하여 기본 구조의 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-405">Understanding these differences is necessary to interpret the results of the [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function.</span></span> <span data-ttu-id="8ab2a-406">EM 클러스터링과 K-means 클러스터링의 차이점에 대한 자세한 내용은 [Microsoft 클러스터링 알고리즘 기술 참조](microsoft-clustering-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-406">For more information about the differences between EM and K-means clustering, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 [<span data-ttu-id="8ab2a-407">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="8ab2a-407">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="8ab2a-408">함수 목록</span><span class="sxs-lookup"><span data-stu-id="8ab2a-408">Function List</span></span>  
 <span data-ttu-id="8ab2a-409">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-409">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="8ab2a-410">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 클러스터링 알고리즘을 사용하여 작성된 모델은 다음 표에 나열된 함수를 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-410">However, models that are built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm support the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ab2a-411">예측 함수</span><span class="sxs-lookup"><span data-stu-id="8ab2a-411">Prediction Function</span></span>|<span data-ttu-id="8ab2a-412">사용</span><span class="sxs-lookup"><span data-stu-id="8ab2a-412">Usage</span></span>|  
|[<span data-ttu-id="8ab2a-413">Cluster&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-413">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="8ab2a-414">입력 사례가 포함되었을 가능성이 가장 높은 클러스터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-414">Returns the cluster that is most likely to contain the input case.</span></span>|  
|[<span data-ttu-id="8ab2a-415">ClusterDistance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-415">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="8ab2a-416">입력 사례와 지정된 클러스터 사이의 거리를 반환합니다. 클러스터가 지정되지 않은 경우에는 입력 사례와 가장 가능성 있는 클러스터 사이의 거리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-416">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="8ab2a-417">입력 사례가 지정한 클러스터에 속할 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-417">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="8ab2a-418">ClusterProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-418">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="8ab2a-419">입력 사례가 지정한 클러스터에 속할 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-419">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="8ab2a-420">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-420">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="8ab2a-421">한 노드가 모델에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-421">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="8ab2a-422">IsInNode&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-422">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="8ab2a-423">지정한 노드에 현재 사례가 포함되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-423">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="8ab2a-424">PredictAdjustedProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-424">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="8ab2a-425">가중치 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-425">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="8ab2a-426">PredictAssociation&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-426">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="8ab2a-427">연관 데이터 세트에서의 멤버 자격을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-427">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="8ab2a-428">PredictCaseLikelihood&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-428">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="8ab2a-429">입력 사례가 기존 모델에 적합할 가능성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-429">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="8ab2a-430">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-430">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="8ab2a-431">현재 예측된 값과 관련 된 값의 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-431">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="8ab2a-432">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-432">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="8ab2a-433">각 사례에 대한 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-433">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="8ab2a-434">PredictProbability&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-434">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="8ab2a-435">예측 값의 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-435">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="8ab2a-436">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-436">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="8ab2a-437">지정된 열의 예측 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-437">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="8ab2a-438">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-438">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="8ab2a-439">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-439">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="8ab2a-440">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="8ab2a-440">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="8ab2a-441">지정한 열의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-441">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="8ab2a-442">특정 함수의 구문은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab2a-442">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab2a-443">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ab2a-443">See Also</span></span>  
 <span data-ttu-id="8ab2a-444">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="8ab2a-444">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="8ab2a-445">[Microsoft 클러스터링 알고리즘 기술 참조](microsoft-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8ab2a-445">[Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="8ab2a-446">Microsoft Clustering Algorithm</span><span class="sxs-lookup"><span data-stu-id="8ab2a-446">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)  
  
  
