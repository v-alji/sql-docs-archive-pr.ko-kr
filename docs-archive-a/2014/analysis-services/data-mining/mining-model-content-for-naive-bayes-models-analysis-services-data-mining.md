---
title: Naive Bayes 모델에 대 한 마이닝 모델 콘텐츠 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- mining model content, naive bayes models
ms.assetid: 63fa15b0-e00c-4aa3-aa49-335f5572ff7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 52e5da80e109828722d56fada19b019d1cfa51f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653661"
---
# <a name="mining-model-content-for-naive-bayes-models-analysis-services---data-mining"></a><span data-ttu-id="fc5ab-102">Naive Bayes 모델에 대한 마이닝 모델 콘텐츠(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-102">Mining Model Content for Naive Bayes Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="fc5ab-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘을 사용하는 모델만의 마이닝 모델 콘텐츠에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="fc5ab-104">모든 모델 유형에서 공유하는 통계 및 구조를 해석하는 방법에 대한 설명은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-naive-bayes-model"></a><span data-ttu-id="fc5ab-105">Naive Bayes 모델의 구조 이해</span><span class="sxs-lookup"><span data-stu-id="fc5ab-105">Understanding the Structure of a Naive Bayes Model</span></span>  
 <span data-ttu-id="fc5ab-106">Naive Bayes 모델에는 모델 및 해당 메타데이터를 나타내는 단일 부모 노드가 있으며 이 부모 노드 아래에는 사용자가 선택한 예측 가능 특성을 나타내는 여러 개의 독립적인 트리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-106">A Naive Bayes model has a single parent node that represents the model and its metadata, and underneath that parent node, any number of independent trees that represent the predictable attributes that you selected.</span></span> <span data-ttu-id="fc5ab-107">특성에 대한 트리 외에도 각 모델에는 학습 사례 집합에 대한 기술 통계를 제공하는 하나의 한계 통계 노드(NODE_TYPE = 26)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-107">In addition to trees for the attributes, each model contains one marginal statistics node (NODE_TYPE = 26) that provides descriptive statistics about the set of training cases.</span></span> <span data-ttu-id="fc5ab-108">자세한 내용은 [한계 통계 노드의 정보](#bkmk_margstats)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-108">For more information, see [Information in the Marginal Statistics Node](#bkmk_margstats).</span></span>  
  
 <span data-ttu-id="fc5ab-109">예측 가능한 각 특성 및 값에 대해 이 모델은 다양한 입력 열이 특정 예측 가능 항목의 결과에 미친 영향을 설명하는 정보가 들어 있는 트리를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-109">For each predictable attribute and value, the model outputs a tree that contains information describing how the various input columns affected the outcome of that particular predictable.</span></span> <span data-ttu-id="fc5ab-110">각 트리에는 예측 가능한 특성 및 해당 값이 포함된 다음(NODE_TYPE = 9) 입력 특성을 나타내는 일련의 노드가 포함됩니다(NODE_TYPE = 10).</span><span class="sxs-lookup"><span data-stu-id="fc5ab-110">Each tree contains the predictable attribute and its value (NODE_TYPE = 9), and then a series of nodes that represent the input attributes (NODE_TYPE = 10).</span></span> <span data-ttu-id="fc5ab-111">입력 특성에는 일반적으로 여러 개의 값이 있으므로 각 입력 특성(NODE_TYPE = 10)에는 각각 특성의 특정 상태를 나타내는 여러 개의 자식 노드(NODE_TYPE = 11)가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-111">Because the input attributes typically have multiple values, each input attribute (NODE_TYPE = 10) may have multiple child nodes (NODE_TYPE = 11), each for a specific state of the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc5ab-112">Naive Bayes 모델은 연속 데이터 형식을 허용하지 않으므로 입력 열의 모든 값은 불연속 또는 분할된 열로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-112">Because a Naive Bayes model does not permit continuous data types, all the values of the input columns are treated as discrete or discretized.</span></span> <span data-ttu-id="fc5ab-113">값이 분할되는 방식은 사용자가 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-113">You can specify how a value is discretized.</span></span> <span data-ttu-id="fc5ab-114">자세한 내용은 [마이닝 모델에서 열의 불연속화 변경](change-the-discretization-of-a-column-in-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-114">For more information, [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="fc5ab-115">![Naive Bayes에 대한 모델 콘텐츠 구조](../media/modelcontentstructure-nb.gif "Naive Bayes에 대한 모델 콘텐츠 구조")</span><span class="sxs-lookup"><span data-stu-id="fc5ab-115">![structure of model content for naive bayes](../media/modelcontentstructure-nb.gif "structure of model content for naive bayes")</span></span>  
  
## <a name="model-content-for-a-naive-bayes-model"></a><span data-ttu-id="fc5ab-116">Naive Bayes 모델에 대한 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="fc5ab-116">Model Content for a Naive Bayes Model</span></span>  
 <span data-ttu-id="fc5ab-117">이 섹션에서는 Naive Bayes 모델과 특별히 관련된 마이닝 모델 콘텐츠 열에 대한 세부 정보 및 예만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-117">This section provides detail and examples only for those columns in the mining model content that have particular relevance for Naive Bayes models.</span></span>  
  
 <span data-ttu-id="fc5ab-118">MODEL_CATALOG와 MODEL_NAME을 비롯하여 여기에 설명되지 않은 스키마 행 집합의 범용 열에 대한 자세한 내용 또는 마이닝 모델 용어에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-118">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="fc5ab-119">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="fc5ab-119">MODEL_CATALOG</span></span>  
 <span data-ttu-id="fc5ab-120">모델이 저장되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-120">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="fc5ab-121">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-121">MODEL_NAME</span></span>  
 <span data-ttu-id="fc5ab-122">모델의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-122">Name of the model.</span></span>  
  
 <span data-ttu-id="fc5ab-123">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-123">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="fc5ab-124">이 노드에 해당하는 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-124">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="fc5ab-125">**모델 루트** 예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-125">**Model root** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-126">**한계 통계** 해당 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-126">**Marginal statistics** Not applicable</span></span>  
  
 <span data-ttu-id="fc5ab-127">**예측 가능한 특성** 예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-127">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-128">**입력 특성** 입력 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-128">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-129">**입력 특성 상태** 입력 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-129">**Input attribute state** The name of the input attribute only.</span></span> <span data-ttu-id="fc5ab-130">상태를 가져오려면 MSOLAP_NODE_SHORT_CAPTION을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-130">To get the state, use MSOLAP_NODE_SHORT_CAPTION.</span></span>  
  
 <span data-ttu-id="fc5ab-131">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-131">NODE_NAME</span></span>  
 <span data-ttu-id="fc5ab-132">노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-132">The name of the node.</span></span>  
  
 <span data-ttu-id="fc5ab-133">이 열에는 NODE_UNIQUE_NAME과 동일한 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-133">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="fc5ab-134">노드 명명 규칙에 대한 자세한 내용은 [노드 이름 및 ID 사용](#bkmk_nodenames)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-134">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="fc5ab-135">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-135">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="fc5ab-136">노드의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-136">The unique name of the node.</span></span> <span data-ttu-id="fc5ab-137">고유한 이름은 노드 간의 관계에 대한 정보를 제공하는 규칙에 따라 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-137">The unique names are assigned according to a convention that provides information about the relationships among the nodes.</span></span> <span data-ttu-id="fc5ab-138">노드 명명 규칙에 대한 자세한 내용은 [노드 이름 및 ID 사용](#bkmk_nodenames)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-138">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="fc5ab-139">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-139">NODE_TYPE</span></span>  
 <span data-ttu-id="fc5ab-140">Naive Bayes 모델이 출력하는 노드 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-140">A Naive Bayes model outputs the following node types:</span></span>  
  
|<span data-ttu-id="fc5ab-141">노드 유형 ID</span><span class="sxs-lookup"><span data-stu-id="fc5ab-141">Node Type ID</span></span>|<span data-ttu-id="fc5ab-142">Description</span><span class="sxs-lookup"><span data-stu-id="fc5ab-142">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="fc5ab-143">26(NaiveBayesMarginalStatNode)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-143">26 (NaiveBayesMarginalStatNode)</span></span>|<span data-ttu-id="fc5ab-144">모델의 전체 학습 사례 집합을 설명하는 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-144">Contains statistics that describes the entire set of training cases for the model.</span></span>|  
|<span data-ttu-id="fc5ab-145">9(예측 가능한 특성)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-145">9 (Predictable attribute)</span></span>|<span data-ttu-id="fc5ab-146">예측 가능한 특성의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-146">Contains the name of the predictable-attribute.</span></span>|  
|<span data-ttu-id="fc5ab-147">10(입력 특성)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-147">10 (Input attribute)</span></span>|<span data-ttu-id="fc5ab-148">입력 특성 열의 이름을 포함하며 특성 값이 있는 자식 노드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-148">Contains the name of an input attribute column, and child nodes that contains the values for the attribute.</span></span>|  
|<span data-ttu-id="fc5ab-149">11(입력 특성 상태)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-149">11 (Input attribute state)</span></span>|<span data-ttu-id="fc5ab-150">특정 출력 특성과 연결된 모든 입력 특성의 값 또는 분할된 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-150">Contains the values or discretized values of all input attributes that were paired with a particular output attribute.</span></span>|  
  
 <span data-ttu-id="fc5ab-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-151">NODE_CAPTION</span></span>  
 <span data-ttu-id="fc5ab-152">노드와 연결된 레이블 또는 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-152">The label or a caption associated with the node.</span></span> <span data-ttu-id="fc5ab-153">이 속성은 주로 표시용으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-153">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="fc5ab-154">**모델 루트** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-154">**Model root** blank</span></span>  
  
 <span data-ttu-id="fc5ab-155">**한계 통계** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-155">**Marginal statistics** blank</span></span>  
  
 <span data-ttu-id="fc5ab-156">**예측 가능한 특성** 예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-156">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-157">**입력 특성** 예측 가능한 특성 및 현재 입력 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-157">**Input attribute** The name of the predictable attribute and the current input attribute.</span></span> <span data-ttu-id="fc5ab-158">예:</span><span class="sxs-lookup"><span data-stu-id="fc5ab-158">Ex:</span></span>  
  
 <span data-ttu-id="fc5ab-159">Bike Buyer -> Age</span><span class="sxs-lookup"><span data-stu-id="fc5ab-159">Bike Buyer -> Age</span></span>  
  
 <span data-ttu-id="fc5ab-160">**입력 특성 상태** 예측 가능한 특성 및 현재 입력 특성의 이름에 입력 값을 추가한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-160">**Input attribute state** The name of the predictable attribute and the current input attribute, plus the value of the input.</span></span> <span data-ttu-id="fc5ab-161">예:</span><span class="sxs-lookup"><span data-stu-id="fc5ab-161">Ex:</span></span>  
  
 <span data-ttu-id="fc5ab-162">Bike Buyer -> Age = Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-162">Bike Buyer -> Age = Missing</span></span>  
  
 <span data-ttu-id="fc5ab-163">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-163">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="fc5ab-164">노드에 있는 자식 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-164">The number of children that the node has.</span></span>  
  
 <span data-ttu-id="fc5ab-165">**모델 루트** 모델에 있는 예측 가능한 특성 수에 한계 통계 노드에 해당하는 1을 더한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-165">**Model root** Count of predictable attributes in the model plus 1 for the marginal statistics node.</span></span>  
  
 <span data-ttu-id="fc5ab-166">**한계 통계** 정의에 따르면 자식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-166">**Marginal statistics** By definition has no children.</span></span>  
  
 <span data-ttu-id="fc5ab-167">**예측 가능한 특성**  현재 예측 가능한 특성과 관련된 입력 특성의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-167">**Predictable attribute**  Count of the input attributes that were related to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-168">**입력 특성** 현재 입력 특성에 대한 불연속 또는 불연속화된 값의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-168">**Input attribute** Count of the discrete or discretized values for the current input attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-169">**입력 특성 상태** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-169">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-170">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-170">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="fc5ab-171">부모 노드의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-171">The unique name of the parent node.</span></span> <span data-ttu-id="fc5ab-172">관련 부모 및 자식 노드에 대한 자세한 내용은 [노드 이름 및 ID 사용](#bkmk_nodenames)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-172">For more information about relating parent and child nodes, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="fc5ab-173">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-173">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="fc5ab-174">노드 캡션과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-174">The same as the node caption.</span></span>  
  
 <span data-ttu-id="fc5ab-175">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-175">NODE_RULE</span></span>  
 <span data-ttu-id="fc5ab-176">노드 캡션의 XML 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-176">An XML representation of the node caption.</span></span>  
  
 <span data-ttu-id="fc5ab-177">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-177">MARGINAL_RULE</span></span>  
 <span data-ttu-id="fc5ab-178">노드 규칙과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-178">The same as the node rule.</span></span>  
  
 <span data-ttu-id="fc5ab-179">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-179">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="fc5ab-180">이 노드와 관련된 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-180">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="fc5ab-181">**모델 루트** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-181">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-182">**한계 통계** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-182">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-183">**예측 가능한 특성**  항상 1입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-183">**Predictable attribute**  Always 1.</span></span>  
  
 <span data-ttu-id="fc5ab-184">**입력 특성** 항상 1입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-184">**Input attribute** Always 1.</span></span>  
  
 <span data-ttu-id="fc5ab-185">**입력 특성 상태** 현재 값의 확률을 나타내는 10진수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-185">**Input attribute state** A decimal number that represents the probability of the current value.</span></span> <span data-ttu-id="fc5ab-186">부모 입력 특성 노드 아래에 있는 모든 입력 특성 상태의 값을 더하면 1이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-186">Values for all input attribute states under the parent input attribute node sum to 1.</span></span>  
  
 <span data-ttu-id="fc5ab-187">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-187">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="fc5ab-188">노드 확률과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-188">The same as the node probability.</span></span>  
  
 <span data-ttu-id="fc5ab-189">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-189">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="fc5ab-190">노드의 확률 히스토그램을 포함하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-190">A table that contains the probability histogram for the node.</span></span> <span data-ttu-id="fc5ab-191">자세한 내용은 [NODE_DISTRIBUTION 테이블](#bkmk_nodedist)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-191">For more information, see [NODE_DISTRIBUTION Table](#bkmk_nodedist).</span></span>  
  
 <span data-ttu-id="fc5ab-192">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fc5ab-192">NODE_SUPPORT</span></span>  
 <span data-ttu-id="fc5ab-193">이 노드를 지지하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-193">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="fc5ab-194">**모델 루트** 학습 데이터의 모든 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-194">**Model root** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="fc5ab-195">**한계 통계** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-195">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-196">**예측 가능한 특성** 학습 데이터의 모든 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-196">**Predictable attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="fc5ab-197">**입력 특성** 학습 데이터의 모든 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-197">**Input attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="fc5ab-198">**입력 특성 상태** 학습 데이터에서 이 특정 값만 포함된 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-198">**Input attribute state** Count of cases in training data that contain only this particular value.</span></span>  
  
 <span data-ttu-id="fc5ab-199">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="fc5ab-199">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="fc5ab-200">표시용 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-200">A label used for display purposes.</span></span> <span data-ttu-id="fc5ab-201">일반적으로 ATTRIBUTE_NAME과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-201">Usually the same as ATTRIBUTE_NAME.</span></span>  
  
 <span data-ttu-id="fc5ab-202">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-202">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="fc5ab-203">모델 내에 있는 특성 또는 값의 중요도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-203">Represents the importance of the attribute or value within the model.</span></span>  
  
 <span data-ttu-id="fc5ab-204">**모델 루트** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-204">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-205">**한계 통계** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-205">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-206">**예측 가능한 특성**  항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-206">**Predictable attribute**  Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-207">**입력 특성** 현재 예측 가능한 특성과 관련된 현재 입력 특성의 흥미도 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-207">**Input attribute** Interestingness score for the current input attribute in relation to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-208">**입력 특성 상태** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-208">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="fc5ab-209">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-209">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="fc5ab-210">열의 이름 또는 값을 나타내는 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-210">A text string that represents the name or the value of a column.</span></span>  
  
 <span data-ttu-id="fc5ab-211">**모델 루트** 공백을</span><span class="sxs-lookup"><span data-stu-id="fc5ab-211">**Model root** Blank</span></span>  
  
 <span data-ttu-id="fc5ab-212">**한계 통계** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-212">**Marginal statistics** Blank</span></span>  
  
 <span data-ttu-id="fc5ab-213">**예측 가능한 특성**  예측 가능한 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-213">**Predictable attribute**  The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-214">**입력 특성** 입력 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-214">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="fc5ab-215">**입력 특성 상태** 입력 특성의 값 또는 불연속화된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-215">**Input attribute state** The value or discretized value of the input attribute.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_nodenames"></a> <span data-ttu-id="fc5ab-216">노드 이름 및 ID 사용</span><span class="sxs-lookup"><span data-stu-id="fc5ab-216">Using Node Names and IDs</span></span>  
 <span data-ttu-id="fc5ab-217">Naive Bayes 모델의 노드 이름은 노드 유형에 대한 추가 정보를 제공하므로 이를 통해 모델에 있는 정보 간의 관계를 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-217">The naming of the nodes in a Naive Bayes model provides additional information about the type of node, to make it easier to understand the relationships among the information in the model.</span></span> <span data-ttu-id="fc5ab-218">다음 표에서는 다른 노드 유형에 할당되는 ID의 규칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-218">The following table shows the convention for the IDs that are assigned to different node types.</span></span>  
  
|<span data-ttu-id="fc5ab-219">노드 유형</span><span class="sxs-lookup"><span data-stu-id="fc5ab-219">Node Type</span></span>|<span data-ttu-id="fc5ab-220">노드 ID의 규칙</span><span class="sxs-lookup"><span data-stu-id="fc5ab-220">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="fc5ab-221">모델 루트(1)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-221">Model root (1)</span></span>|<span data-ttu-id="fc5ab-222">항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-222">Always 0.</span></span>|  
|<span data-ttu-id="fc5ab-223">한계 통계 노드(26)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-223">Marginal statistics node (26)</span></span>|<span data-ttu-id="fc5ab-224">임의의 ID 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-224">An arbitrary ID value.</span></span>|  
|<span data-ttu-id="fc5ab-225">예측 가능한 특성(9)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-225">Predictable attribute (9)</span></span>|<span data-ttu-id="fc5ab-226">10000000으로 시작하는 16진수입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-226">Hexadecimal number beginning with 10000000</span></span><br /><br /> <span data-ttu-id="fc5ab-227">예제: 100000001, 10000000b</span><span class="sxs-lookup"><span data-stu-id="fc5ab-227">Example: 100000001, 10000000b</span></span>|  
|<span data-ttu-id="fc5ab-228">입력 특성(10)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-228">Input attribute (10)</span></span>|<span data-ttu-id="fc5ab-229">두 부분으로 이루어진 16진수입니다. 첫 번째 부분은 항상 20000000이고, 두 번째 부분은 관련된 예측 가능한 특성의 16진수 식별자로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-229">A two-part hexadecimal number where the first part is always 20000000, and the second part starts with the hexadecimal identifier of the related predictable attribute.</span></span><br /><br /> <span data-ttu-id="fc5ab-230">예제: 20000000b00000000</span><span class="sxs-lookup"><span data-stu-id="fc5ab-230">Example: 20000000b00000000</span></span><br /><br /> <span data-ttu-id="fc5ab-231">이 경우 관련된 예측 가능한 특성은 10000000b입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-231">In this case, the related predictable attribute is 10000000b.</span></span>|  
|<span data-ttu-id="fc5ab-232">입력 특성 상태(11)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-232">Input attribute state (11)</span></span>|<span data-ttu-id="fc5ab-233">세 부분으로 이루어진 16진수입니다. 첫 번째 부분은 항상 30000000이고, 두 번째 부분은 관련된 예측 가능한 특성의 16진수 식별자로 시작하며, 세 번째 부분은 값의 식별자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-233">A three-part hexadecimal number where the first part is always 30000000, the second part starts with the hexadecimal identifier of the related predictable attribute, and the third part represents the identifier of the value.</span></span><br /><br /> <span data-ttu-id="fc5ab-234">예제: 30000000b00000000200000000</span><span class="sxs-lookup"><span data-stu-id="fc5ab-234">Example: 30000000b00000000200000000</span></span><br /><br /> <span data-ttu-id="fc5ab-235">이 경우 관련된 예측 가능한 특성은 10000000b입니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-235">In this case, the related predictable attribute is 10000000b.</span></span>|  
  
 <span data-ttu-id="fc5ab-236">ID를 사용하여 입력 특성 및 상태를 예측 가능한 특성과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-236">You can use the IDs to relate input attributes and states to a predictable attribute.</span></span> <span data-ttu-id="fc5ab-237">예를 들어 다음 쿼리는 `TM_NaiveBayes`모델에 대한 입력 특성과 예측 가능한 특성의 가능한 조합을 나타내는 노드의 이름과 캡션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-237">For example, the following query returns the names and captions for nodes that represent the possible combinations of input and predictable attributes for the model, `TM_NaiveBayes`.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
```  
  
 <span data-ttu-id="fc5ab-238">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="fc5ab-238">Expected results:</span></span>  
  
|<span data-ttu-id="fc5ab-239">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-239">NODE_NAME</span></span>|<span data-ttu-id="fc5ab-240">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-240">NODE_CAPTION</span></span>|  
|----------------|-------------------|  
|<span data-ttu-id="fc5ab-241">20000000000000001</span><span class="sxs-lookup"><span data-stu-id="fc5ab-241">20000000000000001</span></span>|<span data-ttu-id="fc5ab-242">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="fc5ab-242">Bike Buyer -> Commute Distance</span></span>|  
|<span data-ttu-id="fc5ab-243">20000000000000002</span><span class="sxs-lookup"><span data-stu-id="fc5ab-243">20000000000000002</span></span>|<span data-ttu-id="fc5ab-244">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="fc5ab-244">Bike Buyer -> English Education</span></span>|  
|<span data-ttu-id="fc5ab-245">20000000000000003</span><span class="sxs-lookup"><span data-stu-id="fc5ab-245">20000000000000003</span></span>|<span data-ttu-id="fc5ab-246">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="fc5ab-246">Bike Buyer -> English Occupation</span></span>|  
|<span data-ttu-id="fc5ab-247">20000000000000009</span><span class="sxs-lookup"><span data-stu-id="fc5ab-247">20000000000000009</span></span>|<span data-ttu-id="fc5ab-248">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="fc5ab-248">Bike Buyer -> Marital Status</span></span>|  
|<span data-ttu-id="fc5ab-249">2000000000000000a</span><span class="sxs-lookup"><span data-stu-id="fc5ab-249">2000000000000000a</span></span>|<span data-ttu-id="fc5ab-250">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="fc5ab-250">Bike Buyer -> Number Children At Home</span></span>|  
|<span data-ttu-id="fc5ab-251">2000000000000000b</span><span class="sxs-lookup"><span data-stu-id="fc5ab-251">2000000000000000b</span></span>|<span data-ttu-id="fc5ab-252">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="fc5ab-252">Bike Buyer -> Region</span></span>|  
|<span data-ttu-id="fc5ab-253">2000000000000000c</span><span class="sxs-lookup"><span data-stu-id="fc5ab-253">2000000000000000c</span></span>|<span data-ttu-id="fc5ab-254">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="fc5ab-254">Bike Buyer -> Total Children</span></span>|  
  
 <span data-ttu-id="fc5ab-255">그런 다음 부모 노드의 ID를 사용하여 자식 노드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-255">You can then use the IDs of the parent nodes to retrieve the child nodes.</span></span> <span data-ttu-id="fc5ab-256">다음 쿼리는 `Marital Status` 특성의 값이 포함된 노드를 각 노드의 확률과 함께 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-256">The following query retrieves the nodes that contain values for the `Marital Status` attribute, together with the probability of each node.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION, NODE_PROBABILITY  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 11  
AND [PARENT_UNIQUE_NAME] = '20000000000000009'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="fc5ab-257">PARENT_UNIQUE_NAME 열의 이름은 대괄호로 묶어 동일한 이름의 예약 키워드와 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-257">The name of the column, PARENT_UNIQUE_NAME, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="fc5ab-258">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="fc5ab-258">Expected results:</span></span>  
  
|<span data-ttu-id="fc5ab-259">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-259">NODE_NAME</span></span>|<span data-ttu-id="fc5ab-260">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-260">NODE_CAPTION</span></span>|<span data-ttu-id="fc5ab-261">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-261">NODE_PROBABILITY</span></span>|  
|----------------|-------------------|-----------------------|  
|<span data-ttu-id="fc5ab-262">3000000000000000900000000</span><span class="sxs-lookup"><span data-stu-id="fc5ab-262">3000000000000000900000000</span></span>|<span data-ttu-id="fc5ab-263">Bike Buyer -> Marital Status = Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-263">Bike Buyer -> Marital Status = Missing</span></span>|<span data-ttu-id="fc5ab-264">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-264">0</span></span>|  
|<span data-ttu-id="fc5ab-265">3000000000000000900000001</span><span class="sxs-lookup"><span data-stu-id="fc5ab-265">3000000000000000900000001</span></span>|<span data-ttu-id="fc5ab-266">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="fc5ab-266">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="fc5ab-267">0.457504004</span><span class="sxs-lookup"><span data-stu-id="fc5ab-267">0.457504004</span></span>|  
|<span data-ttu-id="fc5ab-268">3000000000000000900000002</span><span class="sxs-lookup"><span data-stu-id="fc5ab-268">3000000000000000900000002</span></span>|<span data-ttu-id="fc5ab-269">Bike Buyer -> Marital Status = M</span><span class="sxs-lookup"><span data-stu-id="fc5ab-269">Bike Buyer -> Marital Status = M</span></span>|<span data-ttu-id="fc5ab-270">0.542495996</span><span class="sxs-lookup"><span data-stu-id="fc5ab-270">0.542495996</span></span>|  
  
##  <a name="node_distribution-table"></a><a name="bkmk_nodedist"></a><span data-ttu-id="fc5ab-271">NODE_DISTRIBUTION 테이블</span><span class="sxs-lookup"><span data-stu-id="fc5ab-271">NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="fc5ab-272">중첩 테이블 열 NODE_DISTRIBUTION은 일반적으로 노드의 값 배포에 대한 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-272">The nested table column, NODE_DISTRIBUTION, typically contains statistics about the distribution of values in the node.</span></span> <span data-ttu-id="fc5ab-273">Naive Bayes 모델에서 이 테이블은 다음 노드에 대해서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-273">In a Naive Bayes model, this table is populated only for the following nodes:</span></span>  
  
|<span data-ttu-id="fc5ab-274">노드 유형</span><span class="sxs-lookup"><span data-stu-id="fc5ab-274">Node Type</span></span>|<span data-ttu-id="fc5ab-275">중첩 테이블의 내용</span><span class="sxs-lookup"><span data-stu-id="fc5ab-275">Content of nested table</span></span>|  
|---------------|-----------------------------|  
|<span data-ttu-id="fc5ab-276">모델 루트(1)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-276">Model root (1)</span></span>|<span data-ttu-id="fc5ab-277">비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-277">Blank.</span></span>|  
|<span data-ttu-id="fc5ab-278">한계 통계 노드(24)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-278">Marginal statistics node (24)</span></span>|<span data-ttu-id="fc5ab-279">전체 학습 데이터 집합에 대한 모든 예측 가능한 특성 및 입력 특성의 요약 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-279">Contains summary information for all predictable attributes and input attributes, for entire set of training data.</span></span>|  
|<span data-ttu-id="fc5ab-280">예측 가능한 특성(9)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-280">Predictable attribute (9)</span></span>|<span data-ttu-id="fc5ab-281">비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-281">Blank.</span></span>|  
|<span data-ttu-id="fc5ab-282">입력 특성(10)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-282">Input attribute (10)</span></span>|<span data-ttu-id="fc5ab-283">비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-283">Blank.</span></span>|  
|<span data-ttu-id="fc5ab-284">입력 특성 상태(11)</span><span class="sxs-lookup"><span data-stu-id="fc5ab-284">Input attribute state (11)</span></span>|<span data-ttu-id="fc5ab-285">예측 가능한 값 및 입력 특성 값의 이 특정 조합에 대해 학습 데이터의 값 분포를 설명하는 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-285">Contains statistics that describe the distribution of values in the training data for this particular combination of a predictable value and input attribute value.</span></span>|  
  
 <span data-ttu-id="fc5ab-286">노드 ID 또는 노드 캡션을 사용하여 높은 수준의 세부 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-286">You can use the node IDs or node captions to retrieve increasing levels of detail.</span></span> <span data-ttu-id="fc5ab-287">예를 들어 다음 쿼리는 NODE_DISTRIBUTION 테이블에서 `'Marital Status = S'`값과 관련된 입력 특성 노드에 대한 특정 열만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-287">For example, the following query retrieves specific columns from the NODE_DISTRIBUTION table for only those input attribute nodes that are related to the value, `'Marital Status = S'`.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM TM_NaiveBayes.content  
WHERE NODE_TYPE = 11  
AND NODE_CAPTION = 'Bike Buyer -> Marital Status = S'  
```  
  
 <span data-ttu-id="fc5ab-288">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="fc5ab-288">Expected results:</span></span>  
  
|<span data-ttu-id="fc5ab-289">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fc5ab-289">NODE_CAPTION</span></span>|<span data-ttu-id="fc5ab-290">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-290">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="fc5ab-291">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-291">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="fc5ab-292">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fc5ab-292">t.SUPPORT</span></span>|<span data-ttu-id="fc5ab-293">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-293">t.PROBABILITY</span></span>|<span data-ttu-id="fc5ab-294">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-294">t.VALUETYPE</span></span>|  
|-------------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="fc5ab-295">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="fc5ab-295">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="fc5ab-296">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-296">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-297">Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-297">Missing</span></span>|<span data-ttu-id="fc5ab-298">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-298">0</span></span>|<span data-ttu-id="fc5ab-299">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-299">0</span></span>|<span data-ttu-id="fc5ab-300">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-300">1</span></span>|  
|<span data-ttu-id="fc5ab-301">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="fc5ab-301">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="fc5ab-302">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-302">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-303">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-303">0</span></span>|<span data-ttu-id="fc5ab-304">3783</span><span class="sxs-lookup"><span data-stu-id="fc5ab-304">3783</span></span>|<span data-ttu-id="fc5ab-305">0.472934117</span><span class="sxs-lookup"><span data-stu-id="fc5ab-305">0.472934117</span></span>|<span data-ttu-id="fc5ab-306">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-306">4</span></span>|  
|<span data-ttu-id="fc5ab-307">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="fc5ab-307">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="fc5ab-308">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-308">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-309">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-309">1</span></span>|<span data-ttu-id="fc5ab-310">4216</span><span class="sxs-lookup"><span data-stu-id="fc5ab-310">4216</span></span>|<span data-ttu-id="fc5ab-311">0.527065883</span><span class="sxs-lookup"><span data-stu-id="fc5ab-311">0.527065883</span></span>|<span data-ttu-id="fc5ab-312">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-312">4</span></span>|  
  
 <span data-ttu-id="fc5ab-313">이러한 결과에서 SUPPORT 열의 값은 자전거를 구매한 고객 수를 결혼 여부와 함께 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-313">In these results, the value of the SUPPORT column tells you the count of customers with the specified marital status who purchased a bike.</span></span> <span data-ttu-id="fc5ab-314">PROBABILITY 열에는 이 노드에 대해서만 계산되는 각 특성 값의 확률이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-314">The PROBABILITY column contains the probability of each attribute value, as calculated for this node only.</span></span> <span data-ttu-id="fc5ab-315">NODE_DISTRIBUTION 테이블에서 사용되는 용어의 일반적인 정의는 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-315">For general definitions of terms used in the NODE_DISTRIBUTION table, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="information-in-the-marginal-statistics-node"></a><a name="bkmk_margstats"></a> <span data-ttu-id="fc5ab-316">한계 통계 노드의 정보</span><span class="sxs-lookup"><span data-stu-id="fc5ab-316">Information in the Marginal Statistics Node</span></span>  
 <span data-ttu-id="fc5ab-317">Naive Bayes 모델에서 한계 통계 노드의 중첩 테이블에는 전체 학습 데이터 집합의 값 분포가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-317">In a Naive Bayes model, the nested table for the marginal statistics node contains the distribution of values for the entire set of training data.</span></span> <span data-ttu-id="fc5ab-318">예를 들어 다음 표에서는 `TM_NaiveBayes`모델에 대한 NODE_DISTRIBUTION 중첩 테이블의 통계 목록을 일부 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-318">For example, the following table contains a partial list of the statistics in the nested NODE_DISTRIBUTION table for the model, `TM_NaiveBayes`:</span></span>  
  
|<span data-ttu-id="fc5ab-319">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fc5ab-319">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="fc5ab-320">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-320">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="fc5ab-321">별칭</span><span class="sxs-lookup"><span data-stu-id="fc5ab-321">SUPPORT</span></span>|<span data-ttu-id="fc5ab-322">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fc5ab-322">PROBABILITY</span></span>|<span data-ttu-id="fc5ab-323">분산</span><span class="sxs-lookup"><span data-stu-id="fc5ab-323">VARIANCE</span></span>|<span data-ttu-id="fc5ab-324">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="fc5ab-324">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="fc5ab-325">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-325">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-326">Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-326">Missing</span></span>|<span data-ttu-id="fc5ab-327">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-327">0</span></span>|<span data-ttu-id="fc5ab-328">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-328">0</span></span>|<span data-ttu-id="fc5ab-329">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-329">0</span></span>|<span data-ttu-id="fc5ab-330">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-330">1</span></span>|  
|<span data-ttu-id="fc5ab-331">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-331">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-332">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-332">0</span></span>|<span data-ttu-id="fc5ab-333">8869</span><span class="sxs-lookup"><span data-stu-id="fc5ab-333">8869</span></span>|<span data-ttu-id="fc5ab-334">0.507263784</span><span class="sxs-lookup"><span data-stu-id="fc5ab-334">0.507263784</span></span>|<span data-ttu-id="fc5ab-335">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-335">0</span></span>|<span data-ttu-id="fc5ab-336">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-336">4</span></span>|  
|<span data-ttu-id="fc5ab-337">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fc5ab-337">Bike Buyer</span></span>|<span data-ttu-id="fc5ab-338">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-338">1</span></span>|<span data-ttu-id="fc5ab-339">8615</span><span class="sxs-lookup"><span data-stu-id="fc5ab-339">8615</span></span>|<span data-ttu-id="fc5ab-340">0.492736216</span><span class="sxs-lookup"><span data-stu-id="fc5ab-340">0.492736216</span></span>|<span data-ttu-id="fc5ab-341">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-341">0</span></span>|<span data-ttu-id="fc5ab-342">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-342">4</span></span>|  
|<span data-ttu-id="fc5ab-343">Marital Status</span><span class="sxs-lookup"><span data-stu-id="fc5ab-343">Marital Status</span></span>|<span data-ttu-id="fc5ab-344">Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-344">Missing</span></span>|<span data-ttu-id="fc5ab-345">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-345">0</span></span>|<span data-ttu-id="fc5ab-346">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-346">0</span></span>|<span data-ttu-id="fc5ab-347">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-347">0</span></span>|<span data-ttu-id="fc5ab-348">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-348">1</span></span>|  
|<span data-ttu-id="fc5ab-349">Marital Status</span><span class="sxs-lookup"><span data-stu-id="fc5ab-349">Marital Status</span></span>|<span data-ttu-id="fc5ab-350">S</span><span class="sxs-lookup"><span data-stu-id="fc5ab-350">S</span></span>|<span data-ttu-id="fc5ab-351">7999</span><span class="sxs-lookup"><span data-stu-id="fc5ab-351">7999</span></span>|<span data-ttu-id="fc5ab-352">0.457504004</span><span class="sxs-lookup"><span data-stu-id="fc5ab-352">0.457504004</span></span>|<span data-ttu-id="fc5ab-353">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-353">0</span></span>|<span data-ttu-id="fc5ab-354">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-354">4</span></span>|  
|<span data-ttu-id="fc5ab-355">Marital Status</span><span class="sxs-lookup"><span data-stu-id="fc5ab-355">Marital Status</span></span>|<span data-ttu-id="fc5ab-356">M</span><span class="sxs-lookup"><span data-stu-id="fc5ab-356">M</span></span>|<span data-ttu-id="fc5ab-357">9485</span><span class="sxs-lookup"><span data-stu-id="fc5ab-357">9485</span></span>|<span data-ttu-id="fc5ab-358">0.542495996</span><span class="sxs-lookup"><span data-stu-id="fc5ab-358">0.542495996</span></span>|<span data-ttu-id="fc5ab-359">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-359">0</span></span>|<span data-ttu-id="fc5ab-360">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-360">4</span></span>|  
|<span data-ttu-id="fc5ab-361">Total Children</span><span class="sxs-lookup"><span data-stu-id="fc5ab-361">Total Children</span></span>|<span data-ttu-id="fc5ab-362">Missing</span><span class="sxs-lookup"><span data-stu-id="fc5ab-362">Missing</span></span>|<span data-ttu-id="fc5ab-363">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-363">0</span></span>|<span data-ttu-id="fc5ab-364">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-364">0</span></span>|<span data-ttu-id="fc5ab-365">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-365">0</span></span>|<span data-ttu-id="fc5ab-366">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-366">1</span></span>|  
|<span data-ttu-id="fc5ab-367">Total Children</span><span class="sxs-lookup"><span data-stu-id="fc5ab-367">Total Children</span></span>|<span data-ttu-id="fc5ab-368">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-368">0</span></span>|<span data-ttu-id="fc5ab-369">4865</span><span class="sxs-lookup"><span data-stu-id="fc5ab-369">4865</span></span>|<span data-ttu-id="fc5ab-370">0.278254404</span><span class="sxs-lookup"><span data-stu-id="fc5ab-370">0.278254404</span></span>|<span data-ttu-id="fc5ab-371">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-371">0</span></span>|<span data-ttu-id="fc5ab-372">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-372">4</span></span>|  
|<span data-ttu-id="fc5ab-373">Total Children</span><span class="sxs-lookup"><span data-stu-id="fc5ab-373">Total Children</span></span>|<span data-ttu-id="fc5ab-374">3</span><span class="sxs-lookup"><span data-stu-id="fc5ab-374">3</span></span>|<span data-ttu-id="fc5ab-375">2093</span><span class="sxs-lookup"><span data-stu-id="fc5ab-375">2093</span></span>|<span data-ttu-id="fc5ab-376">0.119709449</span><span class="sxs-lookup"><span data-stu-id="fc5ab-376">0.119709449</span></span>|<span data-ttu-id="fc5ab-377">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-377">0</span></span>|<span data-ttu-id="fc5ab-378">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-378">4</span></span>|  
|<span data-ttu-id="fc5ab-379">Total Children</span><span class="sxs-lookup"><span data-stu-id="fc5ab-379">Total Children</span></span>|<span data-ttu-id="fc5ab-380">1</span><span class="sxs-lookup"><span data-stu-id="fc5ab-380">1</span></span>|<span data-ttu-id="fc5ab-381">3406</span><span class="sxs-lookup"><span data-stu-id="fc5ab-381">3406</span></span>|<span data-ttu-id="fc5ab-382">0.19480668</span><span class="sxs-lookup"><span data-stu-id="fc5ab-382">0.19480668</span></span>|<span data-ttu-id="fc5ab-383">0</span><span class="sxs-lookup"><span data-stu-id="fc5ab-383">0</span></span>|<span data-ttu-id="fc5ab-384">4</span><span class="sxs-lookup"><span data-stu-id="fc5ab-384">4</span></span>|  
  
 <span data-ttu-id="fc5ab-385">한계 통계 노드는 항상 예측 가능한 특성 및 해당 특성의 가능한 값에 대한 설명을 포함하므로 `Bike Buyer` 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-385">The `Bike Buyer` column is included because the marginal statistics node always contains a description of the predictable attribute and its possible values.</span></span> <span data-ttu-id="fc5ab-386">나열된 다른 모든 열은 입력 특성을 모델에 사용된 값과 함께 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-386">All other columns that are listed represent input attributes, together with the values that were used in the model.</span></span> <span data-ttu-id="fc5ab-387">값은 Missing, Discrete 또는 Discretized만 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-387">Values can only be missing, discrete or discretized.</span></span>  
  
 <span data-ttu-id="fc5ab-388">Naive Bayes 모델에는 연속 특성이 있을 수 없으므로 모든 숫자 데이터는 Discrete(VALUE_TYPE = 4) 또는 Discretized(VALUE_TYPE = 5)로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-388">In a Naive Bayes model, there can be no continuous attributes; therefore, all numeric data is represented as either discrete (VALUE_TYPE = 4) or discretized (VALUE_TYPE = 5).</span></span>  
  
 <span data-ttu-id="fc5ab-389">`Missing` 값(VALUE_TYPE = 1)은 모든 입력 및 출력 특성에 추가되어 학습 데이터에 없었던 잠재적인 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-389">A `Missing` value (VALUE_TYPE = 1) is added to every input and output attribute to represent potential values that were not present in the training data.</span></span> <span data-ttu-id="fc5ab-390">문자열 "missing"과 기본 `Missing` 값을 주의해서 구별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-390">You must be careful to distinguish between "missing" as a string and the default `Missing` value.</span></span> <span data-ttu-id="fc5ab-391">자세한 내용은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)에서 미리 정의한 모델링 플래그 외에 다른 모델링 플래그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc5ab-391">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5ab-392">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc5ab-392">See Also</span></span>  
 <span data-ttu-id="fc5ab-393">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fc5ab-393">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="fc5ab-394">[데이터 마이닝 모델 뷰어](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="fc5ab-394">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="fc5ab-395">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="fc5ab-395">[Data Mining Queries](data-mining-queries.md) </span></span>  
 [<span data-ttu-id="fc5ab-396">Microsoft Naive Bayes Algorithm</span><span class="sxs-lookup"><span data-stu-id="fc5ab-396">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)  
  
  
