---
title: 클러스터링 모델에 대 한 마이닝 모델 콘텐츠 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- mining model content, clustering models
- clustering algorithms [Analysis Services]
ms.assetid: aed1b7d3-8f20-4eeb-b156-0229f942cefd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 400575d5c6ce8094b67500d15a86137302282fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649833"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a><span data-ttu-id="8358c-102">클러스터링 모델에 대한 마이닝 모델 콘텐츠(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="8358c-102">Mining Model Content for Clustering Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="8358c-103">이 항목에서는 Microsoft 클러스터링 알고리즘을 사용하는 모델에만 적용되는 마이닝 모델 콘텐츠에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-103">This topic describes mining model content that is specific to models that use the Microsoft Clustering algorithm.</span></span> <span data-ttu-id="8358c-104">모든 모델 유형에 적용되는 마이닝 모델 콘텐츠에 대한 일반적인 설명은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8358c-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a><span data-ttu-id="8358c-105">클러스터링 모델 구조에 대한 이해</span><span class="sxs-lookup"><span data-stu-id="8358c-105">Understanding the Structure of a Clustering Model</span></span>  
 <span data-ttu-id="8358c-106">클러스터링 모델의 구조는 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-106">A clustering model has a simple structure.</span></span> <span data-ttu-id="8358c-107">각 모델에는 모델과 메타데이터를 나타내는 부모 노드가 한 개 있고 각 부모 노드에는 클러스터 기본 목록이 있습니다(NODE_TYPE = 5).</span><span class="sxs-lookup"><span data-stu-id="8358c-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of clusters (NODE_TYPE = 5).</span></span> <span data-ttu-id="8358c-108">이 구조는 다음 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-108">This organization is shown in the following image.</span></span>  
  
 <span data-ttu-id="8358c-109">![클러스터링에 대한 모델 콘텐츠 구조](../media/modelcontentstructure-clust.gif "클러스터링에 대한 모델 콘텐츠 구조")</span><span class="sxs-lookup"><span data-stu-id="8358c-109">![structure of model content for clustering](../media/modelcontentstructure-clust.gif "structure of model content for clustering")</span></span>  
  
 <span data-ttu-id="8358c-110">각 자식 노드는 단일 클러스터를 나타내며 해당 클러스터 내에 있는 사례의 특성에 대한 자세한 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-110">Each child node represents a single cluster and contains detailed statistics about the attributes of the cases in that cluster.</span></span> <span data-ttu-id="8358c-111">이러한 통계에는 클러스터 내 사례 수 및 해당 클러스터를 다른 클러스터와 구별하게 해주는 값의 분포가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-111">This includes a count of the number of cases in the cluster, and the distribution of values that distinguish the cluster from other clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8358c-112">클러스터 수 또는 클러스터에 대한 설명을 가져오기 위해 노드를 반복 처리할 필요는 없습니다. 모델 부모 노드도 클러스터 수를 계산하고 클러스터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-112">You do not need to iterate through the nodes to get a count or description of the clusters; the model parent node also counts and lists the clusters.</span></span>  
  
 <span data-ttu-id="8358c-113">부모 노드에는 모든 학습 사례에 대한 실제 분포를 설명하는 유용한 통계가 포함되어 있는데,</span><span class="sxs-lookup"><span data-stu-id="8358c-113">The parent node contains useful statistics that describe the actual distribution of all the training cases.</span></span> <span data-ttu-id="8358c-114">이러한 통계는 중첩 테이블 열 NODE_DISTRIBUTION에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-114">These statistics are found in the nested table column, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="8358c-115">예를 들어 다음 표는 `TM_Clustering`기본 데이터 마이닝 자습서 [에서 만든 클러스터링 모델](../../tutorials/basic-data-mining-tutorial.md)의 고객 인구 통계 분포를 설명하는 NODE_DISTRIBUTION 테이블의 몇 개 행을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-115">For example, the following table shows several rows from the NODE_DISTRIBUTION table that describe the distribution of customer demographics for the clustering model, `TM_Clustering`, that you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md):</span></span>  
  
|<span data-ttu-id="8358c-116">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-116">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="8358c-117">ATRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="8358c-117">ATRIBUTE_VALUE</span></span>|<span data-ttu-id="8358c-118">별칭</span><span class="sxs-lookup"><span data-stu-id="8358c-118">SUPPORT</span></span>|<span data-ttu-id="8358c-119">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8358c-119">PROBABILITY</span></span>|<span data-ttu-id="8358c-120">분산</span><span class="sxs-lookup"><span data-stu-id="8358c-120">VARIANCE</span></span>|<span data-ttu-id="8358c-121">VALUE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8358c-121">VALUE_TYPE</span></span>|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|<span data-ttu-id="8358c-122">연령</span><span class="sxs-lookup"><span data-stu-id="8358c-122">Age</span></span>|<span data-ttu-id="8358c-123">Missing</span><span class="sxs-lookup"><span data-stu-id="8358c-123">Missing</span></span>|<span data-ttu-id="8358c-124">0</span><span class="sxs-lookup"><span data-stu-id="8358c-124">0</span></span>|<span data-ttu-id="8358c-125">0</span><span class="sxs-lookup"><span data-stu-id="8358c-125">0</span></span>|<span data-ttu-id="8358c-126">0</span><span class="sxs-lookup"><span data-stu-id="8358c-126">0</span></span>|<span data-ttu-id="8358c-127">1(누락)</span><span class="sxs-lookup"><span data-stu-id="8358c-127">1 (Missing)</span></span>|  
|<span data-ttu-id="8358c-128">연령</span><span class="sxs-lookup"><span data-stu-id="8358c-128">Age</span></span>|<span data-ttu-id="8358c-129">44.9016152716593</span><span class="sxs-lookup"><span data-stu-id="8358c-129">44.9016152716593</span></span>|<span data-ttu-id="8358c-130">12939</span><span class="sxs-lookup"><span data-stu-id="8358c-130">12939</span></span>|<span data-ttu-id="8358c-131">1</span><span class="sxs-lookup"><span data-stu-id="8358c-131">1</span></span>|<span data-ttu-id="8358c-132">125.663453102554</span><span class="sxs-lookup"><span data-stu-id="8358c-132">125.663453102554</span></span>|<span data-ttu-id="8358c-133">3(연속)</span><span class="sxs-lookup"><span data-stu-id="8358c-133">3 (Continuous)</span></span>|  
|<span data-ttu-id="8358c-134">성별</span><span class="sxs-lookup"><span data-stu-id="8358c-134">Gender</span></span>|<span data-ttu-id="8358c-135">Missing</span><span class="sxs-lookup"><span data-stu-id="8358c-135">Missing</span></span>|<span data-ttu-id="8358c-136">0</span><span class="sxs-lookup"><span data-stu-id="8358c-136">0</span></span>|<span data-ttu-id="8358c-137">0</span><span class="sxs-lookup"><span data-stu-id="8358c-137">0</span></span>|<span data-ttu-id="8358c-138">0</span><span class="sxs-lookup"><span data-stu-id="8358c-138">0</span></span>|<span data-ttu-id="8358c-139">1(누락)</span><span class="sxs-lookup"><span data-stu-id="8358c-139">1 (Missing)</span></span>|  
|<span data-ttu-id="8358c-140">성별</span><span class="sxs-lookup"><span data-stu-id="8358c-140">Gender</span></span>|<span data-ttu-id="8358c-141">F</span><span class="sxs-lookup"><span data-stu-id="8358c-141">F</span></span>|<span data-ttu-id="8358c-142">6350</span><span class="sxs-lookup"><span data-stu-id="8358c-142">6350</span></span>|<span data-ttu-id="8358c-143">0.490764355823479</span><span class="sxs-lookup"><span data-stu-id="8358c-143">0.490764355823479</span></span>|<span data-ttu-id="8358c-144">0</span><span class="sxs-lookup"><span data-stu-id="8358c-144">0</span></span>|<span data-ttu-id="8358c-145">4 (Discrete)</span><span class="sxs-lookup"><span data-stu-id="8358c-145">4 (Discrete)</span></span>|  
|<span data-ttu-id="8358c-146">성별</span><span class="sxs-lookup"><span data-stu-id="8358c-146">Gender</span></span>|<span data-ttu-id="8358c-147">M</span><span class="sxs-lookup"><span data-stu-id="8358c-147">M</span></span>|<span data-ttu-id="8358c-148">6589</span><span class="sxs-lookup"><span data-stu-id="8358c-148">6589</span></span>|<span data-ttu-id="8358c-149">0.509235644176521</span><span class="sxs-lookup"><span data-stu-id="8358c-149">0.509235644176521</span></span>|<span data-ttu-id="8358c-150">0</span><span class="sxs-lookup"><span data-stu-id="8358c-150">0</span></span>|<span data-ttu-id="8358c-151">4 (Discrete)</span><span class="sxs-lookup"><span data-stu-id="8358c-151">4 (Discrete)</span></span>|  
  
 <span data-ttu-id="8358c-152">이 결과를 통해 모델 작성에 사용된 사례는 12939개이고 남성 대 여성의 비율은 50-50이며 평균 연령은 44세임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-152">From these results, you can see that there were 12939 cases used to build the model, that the ratio of males to females was about 50-50, and that the mean age was 44.</span></span> <span data-ttu-id="8358c-153">설명적 통계는 보고되는 특성이 연속 숫자 데이터 형식(예: 연령)인지 또는 불연속 값 유형(예: 성별)인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-153">The descriptive statistics vary depending on whether the attribute being reported is a continuous numeric data type, such as age, or a discrete value type, such as gender.</span></span> <span data-ttu-id="8358c-154">통계 측정값 *평균* 과 *분산* 은 연속 데이터 형식에 대해 계산되며, *확률* 과 *지지도* 는 불연속 데이터 형식에 대해 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-154">The statistical measures *mean* and *variance* are computed for continuous data types, whereas *probability* and *support* are computed for discrete data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8358c-155">분산은 클러스터에 대한 총 분산을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-155">The variance represents the total variance for the cluster.</span></span> <span data-ttu-id="8358c-156">분산 값이 작은 경우 이는 대부분의 열 값이 평균에 매우 근접해 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-156">When the value for variance is small, it indicates that most values in the column were fairly close to the mean.</span></span> <span data-ttu-id="8358c-157">표준 편차를 구하려면 분산의 제곱근을 계산하십시오.</span><span class="sxs-lookup"><span data-stu-id="8358c-157">To obtain the standard deviation, calculate the square root of the variance.</span></span>  
  
 <span data-ttu-id="8358c-158">각 특성마다 해당 특성에 대한 데이터가 없는 사례 수를 보여 주는 `Missing` 값 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-158">Note that for each of the attributes there is a `Missing` value type that tells you how many cases had no data for that attribute.</span></span> <span data-ttu-id="8358c-159">누락 데이터는 중요하며 데이터 형식에 따라 여러 가지 방식으로 계산에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-159">Missing data can be significant and affects calculations in different ways, depending on the data type.</span></span> <span data-ttu-id="8358c-160">자세한 내용은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)에서 미리 정의한 모델링 플래그 외에 다른 모델링 플래그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-160">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="model-content-for-a-clustering-model"></a><span data-ttu-id="8358c-161">클러스터링 모델에 대한 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="8358c-161">Model Content for a Clustering Model</span></span>  
 <span data-ttu-id="8358c-162">이 섹션에서는 클러스터링 모델과 관련된 마이닝 모델 콘텐츠 열에 대한 세부 정보와 예만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-162">This section provides detail and examples only for those columns in the mining model content that are relevant for clustering models.</span></span>  
  
 <span data-ttu-id="8358c-163">스키마 행 집합(예: MODEL_CATALOG 및 MODEL_NAME)의 범용 열에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8358c-163">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="8358c-164">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8358c-164">MODEL_CATALOG</span></span>  
 <span data-ttu-id="8358c-165">모델이 저장되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-165">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="8358c-166">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-166">MODEL_NAME</span></span>  
 <span data-ttu-id="8358c-167">모델의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-167">Name of the model.</span></span>  
  
 <span data-ttu-id="8358c-168">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-168">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="8358c-169">해당 모드에는 예측 가능한 특성이 없으므로 클러스터링 모델의 경우 항상 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-169">Always blank in clustering models because there is no predictable attribute in the mode.</span></span>  
  
 <span data-ttu-id="8358c-170">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-170">NODE_NAME</span></span>  
 <span data-ttu-id="8358c-171">항상 NODE_UNIQUE_NAME과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-171">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="8358c-172">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-172">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="8358c-173">모델 내의 노드에 대한 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-173">A unique identifier for the node within the model.</span></span> <span data-ttu-id="8358c-174">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-174">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="8358c-175">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8358c-175">NODE_TYPE</span></span>  
 <span data-ttu-id="8358c-176">클러스터링 모델이 출력하는 노드 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-176">A clustering model outputs the following node types:</span></span>  
  
|<span data-ttu-id="8358c-177">노드 ID 및 이름</span><span class="sxs-lookup"><span data-stu-id="8358c-177">Node ID and Name</span></span>|<span data-ttu-id="8358c-178">Description</span><span class="sxs-lookup"><span data-stu-id="8358c-178">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="8358c-179">1(모델)</span><span class="sxs-lookup"><span data-stu-id="8358c-179">1 (Model)</span></span>|<span data-ttu-id="8358c-180">모델의 루트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-180">Root node for model.</span></span>|  
|<span data-ttu-id="8358c-181">5(클러스터)</span><span class="sxs-lookup"><span data-stu-id="8358c-181">5 (Cluster)</span></span>|<span data-ttu-id="8358c-182">클러스터 내 사례 수, 클러스터 내 사례의 특징 및 클러스터의 값을 설명하는 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-182">Contains a count of cases in the cluster, the characteristics of cases in the cluster, and statistics that describe the values in the cluster.</span></span>|  
  
 <span data-ttu-id="8358c-183">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8358c-183">NODE_CAPTION</span></span>  
 <span data-ttu-id="8358c-184">표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-184">A friendly name for display purposes.</span></span> <span data-ttu-id="8358c-185">모델을 만들 때 NODE_UNIQUE_NAME의 값이 자동으로 캡션으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-185">When you create a model, the value of NODE_UNIQUE_NAME is automatically used as the caption.</span></span> <span data-ttu-id="8358c-186">그러나 NODE_CAPTION의 값을 변경하여 클러스터의 표시 이름을 프로그래밍 방식으로 업데이트하거나 뷰어를 통해 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-186">However, you can change the value for NODE_CAPTION to update the display name for the cluster, either programmatically or by using the viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8358c-187">모델을 다시 처리하면 모든 이름 변경 사항을 새 값으로 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-187">When you reprocess the model, all name changes will be overwritten by the new values.</span></span> <span data-ttu-id="8358c-188">버전이 다른 모델 간에는 모델의 이름을 유지하거나 클러스터 멤버 자격 변경 사항을 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-188">You cannot persist names in the model, or track changes in cluster membership between different versions of a model.</span></span>  
  
 <span data-ttu-id="8358c-189">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8358c-189">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="8358c-190">노드에 있는 예상 자식 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-190">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="8358c-191">**부모 노드** 모델에 있는 클러스터 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-191">**Parent node** Indicates the number of clusters in the model.</span></span>  
  
 <span data-ttu-id="8358c-192">**클러스터 노드** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-192">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="8358c-193">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="8358c-193">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="8358c-194">노드 부모의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-194">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="8358c-195">**부모 노드** 항상 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-195">**Parent node** Always NULL</span></span>  
  
 <span data-ttu-id="8358c-196">**클러스터 노드** 일반적으로 000입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-196">**Cluster nodes** Usually 000.</span></span>  
  
 <span data-ttu-id="8358c-197">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8358c-197">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="8358c-198">노드에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-198">A description of the node.</span></span>  
  
 <span data-ttu-id="8358c-199">**부모 노드** 항상 **(All)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-199">**Parent node** Always **(All)**.</span></span>  
  
 <span data-ttu-id="8358c-200">**클러스터 노드** 클러스터를 다른 클러스터와 구별하게 해주는 쉼표로 구분된 기본 특성 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-200">**Cluster nodes** A comma-separated list of the primary attributes that distinguish the cluster from other clusters.</span></span>  
  
 <span data-ttu-id="8358c-201">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="8358c-201">NODE_RULE</span></span>  
 <span data-ttu-id="8358c-202">클러스터링 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-202">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="8358c-203">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="8358c-203">MARGINAL_RULE</span></span>  
 <span data-ttu-id="8358c-204">클러스터링 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-204">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="8358c-205">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8358c-205">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="8358c-206">이 노드와 관련된 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-206">The probability associated with this node.</span></span> <span data-ttu-id="8358c-207">**부모 노드** 항상 1입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-207">**Parent node** Always 1.</span></span>  
  
 <span data-ttu-id="8358c-208">**클러스터 노드** 확률은 특성에 대한 복합 확률을 나타내며 클러스터링 모델을 만드는 데 사용된 알고리즘에 따라 약간씩 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-208">**Cluster nodes** The probability represents the compound probability of the attributes, with some adjustments depending on the algorithm used to create the clustering model.</span></span>  
  
 <span data-ttu-id="8358c-209">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8358c-209">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="8358c-210">부모 노드에서 해당 노드에 도달할 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-210">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="8358c-211">클러스터링 모델에서 한계 확률은 항상 노드 확률과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-211">In a clustering model, the marginal probability is always the same as the node probability.</span></span>  
  
 <span data-ttu-id="8358c-212">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="8358c-212">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="8358c-213">노드의 확률 히스토그램을 포함하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-213">A table that contains the probability histogram of the node.</span></span>  
  
 <span data-ttu-id="8358c-214">**부모 노드** 이 항목에 대한 소개 부분을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8358c-214">**Parent node** See the Introduction to this topic.</span></span>  
  
 <span data-ttu-id="8358c-215">**클러스터 노드** 이 클러스터에 포함되지 않은 사례의 특성 및 값 분포를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-215">**Cluster nodes** Represents the distribution of attributes and values for cases that are included in this cluster.</span></span>  
  
 <span data-ttu-id="8358c-216">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8358c-216">NODE_SUPPORT</span></span>  
 <span data-ttu-id="8358c-217">이 노드를 지지하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-217">The number of cases that support this node.</span></span> <span data-ttu-id="8358c-218">**부모 노드** 전체 모델의 학습 사례 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-218">**Parent node** Indicates the number of training cases for the entire model.</span></span>  
  
 <span data-ttu-id="8358c-219">**클러스터 노드** 클러스터 크기를 사례 수로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-219">**Cluster nodes** Indicates the size of the cluster as a number of cases.</span></span>  
  
 <span data-ttu-id="8358c-220">**참고** 모델이 K-Means 클러스터링을 사용하는 경우 각각의 사례는 한 개의 클러스터에만 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-220">**Note** If the model uses K-Means clustering, each case can belong to only one cluster.</span></span> <span data-ttu-id="8358c-221">그러나 모델이 EM 클러스터링을 사용하는 경우 각각의 사례가 서로 다른 클러스터에 속할 수 있으며 사례가 속해 있는 각 클러스터에 대해 가중치가 적용된 거리가 사례에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-221">However, if the model uses EM clustering, each case can belong to different cluster, and the case is assigned a weighted distance for each cluster to which it belongs.</span></span> <span data-ttu-id="8358c-222">따라서 EM 모델의 경우 개별 클러스터에 대한 지지도 합계가 전체 모델에 대한 지지도보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-222">Therefore, for EM models the sum of support for an individual cluster is greater than support for the overall model.</span></span>  
  
 <span data-ttu-id="8358c-223">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="8358c-223">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="8358c-224">클러스터링 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-224">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="8358c-225">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="8358c-225">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="8358c-226">노드와 연관된 점수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-226">Displays a score associated with the node.</span></span>  
  
 <span data-ttu-id="8358c-227">**부모 노드** 클러스터링 모델에 대한 BIC(Bayesian Information Criterion) 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-227">**Parent node** The Bayesian Information Criterion (BIC) score for the clustering model.</span></span>  
  
 <span data-ttu-id="8358c-228">**클러스터 노드** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-228">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="8358c-229">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8358c-229">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="8358c-230">표시용 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-230">A label used for display purposes.</span></span> <span data-ttu-id="8358c-231">이 캡션은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-231">You cannot change this caption.</span></span>  
  
 <span data-ttu-id="8358c-232">**부모 노드** 모델 유형: 클러스터 모델</span><span class="sxs-lookup"><span data-stu-id="8358c-232">**Parent node** The type of model: Cluster model</span></span>  
  
 <span data-ttu-id="8358c-233">**클러스터 노드** 클러스터의</span><span class="sxs-lookup"><span data-stu-id="8358c-233">**Cluster nodes** The name of the cluster.</span></span> <span data-ttu-id="8358c-234">예제: 클러스터 1.</span><span class="sxs-lookup"><span data-stu-id="8358c-234">Example: Cluster 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8358c-235">설명</span><span class="sxs-lookup"><span data-stu-id="8358c-235">Remarks</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8358c-236">는 클러스터링 모델을 만드는 여러 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-236">provides multiple methods for creating a clustering model.</span></span> <span data-ttu-id="8358c-237">작업 중인 모델이 어떤 방법으로 만들어졌는지 모르는 경우 ADOMD 클라이언트 또는 AMO를 사용하거나 데이터 마이닝 스키마 행 집합을 쿼리하여 모델 메타데이터를 프로그래밍 방식으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-237">If you do not know which method was used to create the model that you are working with, you can retrieve the model metadata programmatically, by using an ADOMD client or AMO, or by querying the data mining schema rowset.</span></span> <span data-ttu-id="8358c-238">자세한 내용은 [마이닝 모델을 만드는 데 사용한 매개 변수 쿼리](query-the-parameters-used-to-create-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8358c-238">For more information, see [Query the Parameters Used to Create a Mining Model](query-the-parameters-used-to-create-a-mining-model.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8358c-239">모델의 구조와 콘텐츠는 사용한 클러스터링 방법이나 매개 변수에 관계없이 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8358c-239">The structure and content of the model stay the same, regardless of which clustering method or parameters you use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8358c-240">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8358c-240">See Also</span></span>  
 <span data-ttu-id="8358c-241">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8358c-241">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8358c-242">[데이터 마이닝 모델 뷰어](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="8358c-242">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="8358c-243">[Microsoft 클러스터링 알고리즘](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="8358c-243">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="8358c-244">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="8358c-244">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
