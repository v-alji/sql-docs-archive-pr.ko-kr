---
title: 선형 회귀 모델에 대 한 마이닝 모델 콘텐츠 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- mining model content, linear regression models
- regression algorithms [Analysis Services]
ms.assetid: a6abcb75-524e-4e0a-a375-c10475ac0a9d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cb41cf0053f236b4bda8d4520030603a391d1c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733335"
---
# <a name="mining-model-content-for-linear-regression-models-analysis-services---data-mining"></a><span data-ttu-id="22c8d-102">선형 회귀 모델에 대한 마이닝 모델 콘텐츠(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="22c8d-102">Mining Model Content for Linear Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="22c8d-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 선형 회귀 알고리즘을 사용하는 모델만의 마이닝 모델 콘텐츠에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="22c8d-104">모든 모델 유형에 적용되는 마이닝 모델 콘텐츠에 대한 일반적인 설명은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22c8d-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-linear-regression-model"></a><span data-ttu-id="22c8d-105">선형 회귀 모델의 구조 이해</span><span class="sxs-lookup"><span data-stu-id="22c8d-105">Understanding the Structure of a Linear Regression Model</span></span>  
 <span data-ttu-id="22c8d-106">선형 회귀 모델의 구조는 매우 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-106">A linear regression model has an extremely simple structure.</span></span> <span data-ttu-id="22c8d-107">각 모델에는 모델 및 해당 메타 데이터를 나타내는 단일 부모 노드와 예측 가능한 각 특성의 회귀 수식이 포함 된 회귀 트리 노드 (NODE_TYPE = 25)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-107">Each model has a single parent node that represents the model and its metadata, and a regression tree node (NODE_TYPE = 25) that contains the regression formula for each predictable attribute.</span></span>  
  
 <span data-ttu-id="22c8d-108">![선형 회귀에 대한 모델 구조](../media/modelcontentstructure-linreg.gif "선형 회귀에 대한 모델 구조")</span><span class="sxs-lookup"><span data-stu-id="22c8d-108">![Structure of model for linear regression](../media/modelcontentstructure-linreg.gif "Structure of model for linear regression")</span></span>  
  
 <span data-ttu-id="22c8d-109">선형 회귀 모델에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리와 동일한 알고리즘을 사용하지만 트리를 제한하는 데는 다른 매개 변수를 사용하며 입력으로는 연속 특성만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-109">Linear regression models use the same algorithm as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees, but different parameters are used to constrain the tree, and only continuous attributes are accepted as inputs.</span></span> <span data-ttu-id="22c8d-110">그러나 선형 회귀 모델은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 기반으로 하므로 선형 회귀 모델을 표시하는 데는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 뷰어가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-110">However, because linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, linear regression models are displayed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Tree Viewer.</span></span> <span data-ttu-id="22c8d-111">자세한 내용은 [Microsoft 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-tree-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22c8d-111">For information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="22c8d-112">다음 섹션에서는 회귀 수식 노드의 정보를 해석하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-112">The next section explains how to interpret information in the regression formula node.</span></span> <span data-ttu-id="22c8d-113">이 정보는 선형 회귀 모델뿐 아니라 트리의 일부분에 회귀가 포함된 의사 결정 트리 모델에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-113">This information applies not only to linear regression models, but also to decision trees models that contain regressions in a portion of the tree.</span></span>  
  
## <a name="model-content-for-a-linear-regression-model"></a><span data-ttu-id="22c8d-114">선형 회귀 모델에 대한 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="22c8d-114">Model Content for a Linear Regression Model</span></span>  
 <span data-ttu-id="22c8d-115">이 섹션에서는 선형 회귀와 특별히 관련된 마이닝 모델 콘텐츠 열에 대한 세부 정보 및 예만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-115">This section provides detail and examples only for those columns in the mining model content that have particular relevance for linear regression.</span></span>  
  
 <span data-ttu-id="22c8d-116">스키마 행 집합의 범용 열에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="22c8d-116">For information about general-purpose columns in the schema rowset, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="22c8d-117">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="22c8d-117">MODEL_CATALOG</span></span>  
 <span data-ttu-id="22c8d-118">모델이 저장되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-118">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="22c8d-119">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-119">MODEL_NAME</span></span>  
 <span data-ttu-id="22c8d-120">모델의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-120">Name of the model.</span></span>  
  
 <span data-ttu-id="22c8d-121">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-121">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="22c8d-122">**루트 노드:** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-122">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="22c8d-123">**회귀 노드:** 예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-123">**Regression node:** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="22c8d-124">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-124">NODE_NAME</span></span>  
 <span data-ttu-id="22c8d-125">항상 NODE_UNIQUE_NAME과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-125">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="22c8d-126">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-126">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="22c8d-127">모델 내의 노드에 대한 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-127">A unique identifier for the node within the model.</span></span> <span data-ttu-id="22c8d-128">이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-128">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="22c8d-129">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="22c8d-129">NODE_TYPE</span></span>  
 <span data-ttu-id="22c8d-130">선형 회귀 모델이 출력하는 노드 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-130">A linear regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="22c8d-131">노드 유형 ID</span><span class="sxs-lookup"><span data-stu-id="22c8d-131">Node Type ID</span></span>|<span data-ttu-id="22c8d-132">Type</span><span class="sxs-lookup"><span data-stu-id="22c8d-132">Type</span></span>|<span data-ttu-id="22c8d-133">설명</span><span class="sxs-lookup"><span data-stu-id="22c8d-133">Description</span></span>|  
|------------------|----------|-----------------|  
|<span data-ttu-id="22c8d-134">25</span><span class="sxs-lookup"><span data-stu-id="22c8d-134">25</span></span>|<span data-ttu-id="22c8d-135">회귀 트리 루트</span><span class="sxs-lookup"><span data-stu-id="22c8d-135">Regression tree root</span></span>|<span data-ttu-id="22c8d-136">입력 및 출력 변수 간의 관계를 설명하는 수식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-136">Contains the formula that describes the relationship between the input and output variable.</span></span>|  
  
 <span data-ttu-id="22c8d-137">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="22c8d-137">NODE_CAPTION</span></span>  
 <span data-ttu-id="22c8d-138">노드와 연결된 레이블 또는 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-138">A label or a caption associated with the node.</span></span> <span data-ttu-id="22c8d-139">이 속성은 주로 표시용으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-139">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="22c8d-140">**루트 노드:** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-140">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="22c8d-141">**회귀 노드:** 모든 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-141">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="22c8d-142">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="22c8d-142">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="22c8d-143">노드에 있는 예상 자식 수입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-143">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="22c8d-144">**루트 노드:** 회귀 노드의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-144">**Root node:** Indicates the number of regression nodes.</span></span> <span data-ttu-id="22c8d-145">모델의 예측 가능한 각 특성에 대해 하나씩의 회귀 노드가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-145">One regression node is created for each predictable attribute in the model.</span></span>  
  
 <span data-ttu-id="22c8d-146">**회귀 노드:** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-146">**Regression node:** Always 0.</span></span>  
  
 <span data-ttu-id="22c8d-147">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-147">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="22c8d-148">노드 부모의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-148">The unique name of the node's parent.</span></span> <span data-ttu-id="22c8d-149">루트 수준의 모든 노드에 대해서 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-149">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="22c8d-150">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="22c8d-150">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="22c8d-151">노드에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-151">A description of the node.</span></span>  
  
 <span data-ttu-id="22c8d-152">**루트 노드:** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-152">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="22c8d-153">**회귀 노드:** 모든 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-153">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="22c8d-154">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="22c8d-154">NODE_RULE</span></span>  
 <span data-ttu-id="22c8d-155">선형 회귀 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-155">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="22c8d-156">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="22c8d-156">MARGINAL_RULE</span></span>  
 <span data-ttu-id="22c8d-157">선형 회귀 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-157">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="22c8d-158">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="22c8d-158">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="22c8d-159">이 노드와 관련된 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-159">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="22c8d-160">**루트 노드:** 0입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-160">**Root node:** 0</span></span>  
  
 <span data-ttu-id="22c8d-161">**회귀 노드:** 1입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-161">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="22c8d-162">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="22c8d-162">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="22c8d-163">부모 노드에서 해당 노드에 도달할 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-163">The probability of reaching the node from the parent node.</span></span>  
  
 <span data-ttu-id="22c8d-164">**루트 노드:** 0입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-164">**Root node:** 0</span></span>  
  
 <span data-ttu-id="22c8d-165">**회귀 노드:** 1입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-165">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="22c8d-166">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="22c8d-166">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="22c8d-167">노드의 값에 대한 통계를 제공하는 중첩 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-167">A nested table that provides statistics about the values in the node.</span></span>  
  
 <span data-ttu-id="22c8d-168">**루트 노드:** 0입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-168">**Root node:** 0</span></span>  
  
 <span data-ttu-id="22c8d-169">**회귀 노드:** 회귀 수식을 작성하는 데 사용된 요소가 들어 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-169">**Regression node:** A table that contains the elements used to build the regression formula.</span></span> <span data-ttu-id="22c8d-170">회귀 노드에는 다음과 같은 값 유형이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-170">A regression node contains the following value types:</span></span>  
  
|<span data-ttu-id="22c8d-171">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="22c8d-171">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="22c8d-172">1(누락)</span><span class="sxs-lookup"><span data-stu-id="22c8d-172">1 (Missing)</span></span>|  
|<span data-ttu-id="22c8d-173">3(연속)</span><span class="sxs-lookup"><span data-stu-id="22c8d-173">3 (Continuous)</span></span>|  
|<span data-ttu-id="22c8d-174">7(계수)</span><span class="sxs-lookup"><span data-stu-id="22c8d-174">7 (Coefficient)</span></span>|  
|<span data-ttu-id="22c8d-175">8(득점)</span><span class="sxs-lookup"><span data-stu-id="22c8d-175">8 (Score Gain)</span></span>|  
|<span data-ttu-id="22c8d-176">9(통계)</span><span class="sxs-lookup"><span data-stu-id="22c8d-176">9 (Statistics)</span></span>|  
|<span data-ttu-id="22c8d-177">11(절편)</span><span class="sxs-lookup"><span data-stu-id="22c8d-177">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="22c8d-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="22c8d-178">NODE_SUPPORT</span></span>  
 <span data-ttu-id="22c8d-179">이 노드를 지지하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-179">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="22c8d-180">**루트 노드:** 0입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-180">**Root node:** 0</span></span>  
  
 <span data-ttu-id="22c8d-181">**회귀 노드:** 학습 사례의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-181">**Regression node:** Count of training cases.</span></span>  
  
 <span data-ttu-id="22c8d-182">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="22c8d-182">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="22c8d-183">예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-183">Name of predictable attribute.</span></span>  
  
 <span data-ttu-id="22c8d-184">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="22c8d-184">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="22c8d-185">NODE_PROBABILITY와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-185">Same as NODE_PROBABILITY</span></span>  
  
 <span data-ttu-id="22c8d-186">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="22c8d-186">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="22c8d-187">표시용 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-187">Label used for display purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22c8d-188">설명</span><span class="sxs-lookup"><span data-stu-id="22c8d-188">Remarks</span></span>  
 <span data-ttu-id="22c8d-189">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 선형 회귀 알고리즘을 사용하여 모델을 만드는 경우 데이터 마이닝 엔진은 의사 결정 트리 모델의 특수한 인스턴스를 만들고 단일 노드의 모든 학습 데이트를 포함하도록 트리를 제한하는 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-189">When you create a model by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, the data mining engine creates a special instance of a decision trees model and supplies parameters that constrain the tree to contain all the training data in a single node.</span></span> <span data-ttu-id="22c8d-190">모든 연속 입력은 잠재적인 회귀 변수로 플래그가 지정되고 계산되지만 최종 모델에서는 데이터에 맞는 회귀 변수만 회귀 변수로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-190">All continuous inputs are flagged and evaluated as potential regressors, but only those regressors that fit the data are retained as regressors in the final model.</span></span> <span data-ttu-id="22c8d-191">분석에서는 각 회귀 변수에 대해 회귀 수식이 하나씩 생성되거나 회귀 수식이 전혀 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-191">The analysis produces either a single regression formula for each regressor or no regression formula at all.</span></span>  
  
 <span data-ttu-id="22c8d-192">**Microsoft 트리 뷰어**의 **(All)** 노드를 클릭하여 [마이닝 범례](browse-a-model-using-the-microsoft-tree-viewer.md)에서 전체 회귀 수식을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-192">You can view the complete regression formula in the **Mining Legend**, by clicking the **(All)** node in the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="22c8d-193">또한 예측 가능한 연속 특성을 포함하는 의사 결정 트리 모델을 만들 때 일부 경우에는 트리에 회귀 트리 노드의 속성을 공유하는 회귀 노드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-193">Also, when you create a decision trees model that includes a continuous predictable attribute, sometimes the tree has regression nodes that share the properties of regression tree nodes.</span></span>  
  
##  <a name="node-distribution-for-continuous-attributes"></a><a name="NodeDist_Regression"></a><span data-ttu-id="22c8d-194">연속 특성에 대 한 노드 분포</span><span class="sxs-lookup"><span data-stu-id="22c8d-194">Node Distribution for Continuous Attributes</span></span>  
 <span data-ttu-id="22c8d-195">회귀 노드의 중요한 정보는 대부분 NODE_DISTRIBUTION 테이블에 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-195">Most of the important information in a regression node is contained in the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="22c8d-196">다음 예에서는 NODE_DISTRIBUTION 테이블의 레이아웃을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-196">The following example illustrates the layout of the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="22c8d-197">이 예에서 Targeted Mailing 마이닝 구조는 연령별 고객 수입을 예측하는 선형 회귀 모델을 만드는 데 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-197">In this example, the Targeted Mailing mining structure has been used to create a linear regression model that predicts customer income based on age.</span></span> <span data-ttu-id="22c8d-198">이 모델은 기존의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터 및 마이닝 구조를 사용하여 쉽게 작성할 수 있는 것으로, 여기에는 단지 설명을 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-198">The model is for the purpose of illustration only, because it can be built easily using the existing [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample data and mining structure.</span></span>  
  
|<span data-ttu-id="22c8d-199">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="22c8d-199">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="22c8d-200">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="22c8d-200">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="22c8d-201">별칭</span><span class="sxs-lookup"><span data-stu-id="22c8d-201">SUPPORT</span></span>|<span data-ttu-id="22c8d-202">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="22c8d-202">PROBABILITY</span></span>|<span data-ttu-id="22c8d-203">분산</span><span class="sxs-lookup"><span data-stu-id="22c8d-203">VARIANCE</span></span>|<span data-ttu-id="22c8d-204">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="22c8d-204">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="22c8d-205">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="22c8d-205">Yearly Income</span></span>|<span data-ttu-id="22c8d-206">Missing</span><span class="sxs-lookup"><span data-stu-id="22c8d-206">Missing</span></span>|<span data-ttu-id="22c8d-207">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-207">0</span></span>|<span data-ttu-id="22c8d-208">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="22c8d-208">0.000457142857142857</span></span>|<span data-ttu-id="22c8d-209">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-209">0</span></span>|<span data-ttu-id="22c8d-210">1</span><span class="sxs-lookup"><span data-stu-id="22c8d-210">1</span></span>|  
|<span data-ttu-id="22c8d-211">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="22c8d-211">Yearly Income</span></span>|<span data-ttu-id="22c8d-212">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="22c8d-212">57220.8876687257</span></span>|<span data-ttu-id="22c8d-213">17484</span><span class="sxs-lookup"><span data-stu-id="22c8d-213">17484</span></span>|<span data-ttu-id="22c8d-214">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="22c8d-214">0.999542857142857</span></span>|<span data-ttu-id="22c8d-215">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="22c8d-215">1041275619.52776</span></span>|<span data-ttu-id="22c8d-216">3</span><span class="sxs-lookup"><span data-stu-id="22c8d-216">3</span></span>|  
|<span data-ttu-id="22c8d-217">연령</span><span class="sxs-lookup"><span data-stu-id="22c8d-217">Age</span></span>|<span data-ttu-id="22c8d-218">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="22c8d-218">471.687717702463</span></span>|<span data-ttu-id="22c8d-219">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-219">0</span></span>|<span data-ttu-id="22c8d-220">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-220">0</span></span>|<span data-ttu-id="22c8d-221">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="22c8d-221">126.969442359327</span></span>|<span data-ttu-id="22c8d-222">7</span><span class="sxs-lookup"><span data-stu-id="22c8d-222">7</span></span>|  
|<span data-ttu-id="22c8d-223">연령</span><span class="sxs-lookup"><span data-stu-id="22c8d-223">Age</span></span>|<span data-ttu-id="22c8d-224">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="22c8d-224">234.680904692439</span></span>|<span data-ttu-id="22c8d-225">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-225">0</span></span>|<span data-ttu-id="22c8d-226">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-226">0</span></span>|<span data-ttu-id="22c8d-227">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-227">0</span></span>|<span data-ttu-id="22c8d-228">8</span><span class="sxs-lookup"><span data-stu-id="22c8d-228">8</span></span>|  
|<span data-ttu-id="22c8d-229">연령</span><span class="sxs-lookup"><span data-stu-id="22c8d-229">Age</span></span>|<span data-ttu-id="22c8d-230">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="22c8d-230">45.4269617936399</span></span>|<span data-ttu-id="22c8d-231">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-231">0</span></span>|<span data-ttu-id="22c8d-232">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-232">0</span></span>|<span data-ttu-id="22c8d-233">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="22c8d-233">126.969442359327</span></span>|<span data-ttu-id="22c8d-234">9</span><span class="sxs-lookup"><span data-stu-id="22c8d-234">9</span></span>|  
||<span data-ttu-id="22c8d-235">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="22c8d-235">35793.5477381267</span></span>|<span data-ttu-id="22c8d-236">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-236">0</span></span>|<span data-ttu-id="22c8d-237">0</span><span class="sxs-lookup"><span data-stu-id="22c8d-237">0</span></span>|<span data-ttu-id="22c8d-238">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="22c8d-238">1012968919.28372</span></span>|<span data-ttu-id="22c8d-239">11</span><span class="sxs-lookup"><span data-stu-id="22c8d-239">11</span></span>|  
  
 <span data-ttu-id="22c8d-240">NODE_DISTRIBUTION 테이블에는 여러 행이 각각 변수별로 그룹화되어 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-240">The NODE_DISTRIBUTION table contains multiple rows, each grouped by a variable.</span></span> <span data-ttu-id="22c8d-241">처음 두 개의 행은 값 유형이 항상 1과 3이며 대상 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-241">The first two rows are always value types 1 and 3, and describe the target attribute.</span></span> <span data-ttu-id="22c8d-242">그 이후 행은 특정 *회귀 변수*의 수식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-242">The succeeding rows provide details about the formula for a particular *regressor*.</span></span> <span data-ttu-id="22c8d-243">회귀 변수는 출력 변수와 선형 관계가 있는 입력 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-243">A regressor is an input variable that has a linear relationship with the output variable.</span></span> <span data-ttu-id="22c8d-244">여러 회귀 변수를 사용할 수 있으며 각 회귀 변수에는 계수(VALUETYPE = 7), 득점(VALUETYPE = 8) 및 통계(VALUETYPE = 9)에 대한 별도의 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-244">You can have multiple regressors, and each regressor will have a separate row for the coefficient (VALUETYPE = 7), score gain (VALUETYPE = 8), and statistics (VALUETYPE = 9).</span></span> <span data-ttu-id="22c8d-245">마지막으로 테이블에는 수식의 절편(VALUETYPE = 11)이 포함된 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-245">Finally, the table has a row that contains the intercept of the equation (VALUETYPE = 11).</span></span>  
  
### <a name="elements-of-the-regression-formula"></a><span data-ttu-id="22c8d-246">회귀 수식의 요소</span><span class="sxs-lookup"><span data-stu-id="22c8d-246">Elements of the Regression Formula</span></span>  
 <span data-ttu-id="22c8d-247">NODE_DISTRIBUTION 중첩 테이블의 개별 행에는 회귀 수식의 각 요소가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-247">The nested NODE_DISTRIBUTION table contains each element of the regression formula in a separate row.</span></span> <span data-ttu-id="22c8d-248">예의 결과에 있는 처음 두 개의 데이터 행에는 종속 변수를 모델링하는 예측 가능한 특성 **Yearly Income**에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-248">The first two rows of data in the example results contain information about the predictable attribute, **Yearly Income**, which models the dependent variable.</span></span> <span data-ttu-id="22c8d-249">SUPPORT 열에는 이 특성의 두 가지 상태( **Yearly Income** 값이 사용 가능함, 또는 **Yearly Income** 값이 누락됨)를 지원하는 사례 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-249">The SUPPORT column shows the count of cases in support of the two states of this attribute: either a **Yearly Income** value was available, or the **Yearly Income** value was missing.</span></span>  
  
 <span data-ttu-id="22c8d-250">VARIANCE 열은 예측 가능한 특성의 계산된 분산을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-250">The VARIANCE column tells you the computed variance of the predictable attribute.</span></span> <span data-ttu-id="22c8d-251">*분산* 은 샘플의 값이 예상 분포를 기준으로 얼마나 넓게 분산되어 있는지를 측정한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-251">*Variance* is a measure of how scattered the values are in a sample, given an expected distribution.</span></span> <span data-ttu-id="22c8d-252">분산은 평균과의 제곱 편차에 대한 평균을 사용하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-252">Variance here is calculated by taking the average of the squared deviation from the mean.</span></span> <span data-ttu-id="22c8d-253">분산의 제곱근을 표준 편차라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-253">The square root of the variance is also known as standard deviation.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="22c8d-254">에서는 표준 편차를 제공하지 않지만 표준 편차도 쉽게 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-254">does not provide the standard deviation but you can easily calculate it.</span></span>  
  
 <span data-ttu-id="22c8d-255">각 회귀 변수에 대해 세 개씩의 행이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-255">For each regressor, three rows are output.</span></span> <span data-ttu-id="22c8d-256">이 세 행에는 계수, 득점 및 회귀 변수 통계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-256">They contain the coefficient, score gain, and regressor statistics.</span></span>  
  
 <span data-ttu-id="22c8d-257">마지막으로 테이블에는 수식의 절편을 제공하는 행이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-257">Finally, the table contains a row that provides the intercept for the equation.</span></span>  
  
#### <a name="coefficient"></a><span data-ttu-id="22c8d-258">계수</span><span class="sxs-lookup"><span data-stu-id="22c8d-258">Coefficient</span></span>  
 <span data-ttu-id="22c8d-259">각 회귀 변수에 대해 계수(VALUETYPE = 7)가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-259">For each regressor, a coefficient (VALUETYPE = 7) is calculated.</span></span> <span data-ttu-id="22c8d-260">계수 자체는 ATTRIBUTE_VALUE 열에 나타나지만 VARIANCE 열은 계수의 분산을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-260">The coefficient itself appears in the ATTRIBUTE_VALUE column, whereas the VARIANCE column tells you the variance for the coefficient.</span></span> <span data-ttu-id="22c8d-261">계수는 선형성을 최대화하도록 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-261">The coefficients are calculated so as to maximize linearity.</span></span>  
  
#### <a name="score-gain"></a><span data-ttu-id="22c8d-262">득점</span><span class="sxs-lookup"><span data-stu-id="22c8d-262">Score Gain</span></span>  
 <span data-ttu-id="22c8d-263">각 회귀 변수의 득점(VALUETYPE = 8)은 특성의 흥미도 점수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-263">The score gain (VALUETYPE = 8) for each regressor represents the interestingness score of the attribute.</span></span> <span data-ttu-id="22c8d-264">이 값을 사용하여 여러 회귀 변수의 유용성을 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-264">You can use this value to estimate the usefulness of multiple regressors.</span></span>  
  
#### <a name="statistics"></a><span data-ttu-id="22c8d-265">통계</span><span class="sxs-lookup"><span data-stu-id="22c8d-265">Statistics</span></span>  
 <span data-ttu-id="22c8d-266">회귀 변수 통계(VALUETYPE = 9)는 값이 있는 사례의 특성에 대한 평균입니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-266">The regressor statistic (VALUETYPE = 9) is the mean for the attribute for cases that have a value.</span></span> <span data-ttu-id="22c8d-267">ATTRIBUTE_VALUE 열에는 평균 자체가 들어 있지만 VARIANCE 열에는 평균과의 편차에 대한 합계가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-267">The ATTRIBUTE_VALUE column contains the mean itself, whereas the VARIANCE column contains the sum of deviations from the mean.</span></span>  
  
#### <a name="intercept"></a><span data-ttu-id="22c8d-268">가로채기</span><span class="sxs-lookup"><span data-stu-id="22c8d-268">Intercept</span></span>  
 <span data-ttu-id="22c8d-269">일반적으로 회귀 수식의 *절편* (VALUETYPE = 11) 또는 *나머지* 는 입력 특성이 0인 지점의 예측 가능한 특성 값을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-269">Normally, the *intercept* (VALUETYPE = 11) or *residual* in a regression equation tells you the value of the predictable attribute, at the point where the input attribute, is 0.</span></span> <span data-ttu-id="22c8d-270">대부분의 경우 입력 특성은 0일 수 없으며 0일 경우에는 예상치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-270">In many cases, this might not happen, and could lead to counterintuitive results.</span></span>  
  
 <span data-ttu-id="22c8d-271">예를 들어 연령별 수입을 예측하는 모델에서 연령이 0일 때의 수입을 확인하는 것은 의미가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-271">For example, in a model that predicts income based on age, it is useless to learn the income at age 0.</span></span> <span data-ttu-id="22c8d-272">실제 상황에서는 대개 평균값을 기준으로 선의 동작에 대해 알아보는 것이 더욱 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-272">In real-life, it is typically more useful to know about the behavior of the line with respect to average values.</span></span> <span data-ttu-id="22c8d-273">따라서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 평균을 사용 하 여 각 회귀 변수를 표현 하도록 절편을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-273">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifies the intercept to express each regressor in a relationship with the mean.</span></span>  
  
 <span data-ttu-id="22c8d-274">이러한 조정은 마이닝 모델 콘텐츠에서는 보기 어렵지만 **Microsoft 트리 뷰어** 의 **마이닝 범례**에서 전체 수식을 볼 경우에는 분명하게 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-274">This adjustment is difficult to see in the mining model content, but is apparent if you view the completed equation in the **Mining Legend** of the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="22c8d-275">회귀 수식은 0 지점에서 평균을 나타내는 지점으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-275">The regression formula is shifted away from the 0 point to the point that represents the mean.</span></span> <span data-ttu-id="22c8d-276">이는 현재 데이터를 보다 직관적으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-276">This presents a view that is more intuitive given the current data.</span></span>  
  
 <span data-ttu-id="22c8d-277">따라서 평균 연령이 45세라고 간주하면 회귀 수식의 절편(VALUETYPE = 11)은 평균 수입을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22c8d-277">Therefore, assuming that the mean age is around 45, the intercept (VALUETYPE = 11) for the regression formula tells you the mean income.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c8d-278">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22c8d-278">See Also</span></span>  
 <span data-ttu-id="22c8d-279">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="22c8d-279">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="22c8d-280">[Microsoft 선형 회귀 알고리즘](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="22c8d-280">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="22c8d-281">[Microsoft 선형 회귀 알고리즘 기술 참조](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="22c8d-281">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="22c8d-282">선형 회귀 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="22c8d-282">Linear Regression Model Query Examples</span></span>](linear-regression-model-query-examples.md)  
  
  
