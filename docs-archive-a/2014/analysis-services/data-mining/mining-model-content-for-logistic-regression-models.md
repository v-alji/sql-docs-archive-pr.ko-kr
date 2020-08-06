---
title: 로지스틱 회귀 모델에 대 한 마이닝 모델 콘텐츠 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- mining model content, logistic regression models
- regression algorithms [Analysis Services]
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84964c59a63d41f0985001a2ae384fa298096927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653666"
---
# <a name="mining-model-content-for-logistic-regression-models-analysis-services---data-mining"></a><span data-ttu-id="e260d-102">로지스틱 회귀 모델에 대한 마이닝 모델 콘텐츠(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="e260d-102">Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="e260d-103">이 항목에서는 Microsoft 로지스틱 회귀 알고리즘을 사용하는 모델만의 마이닝 모델 콘텐츠에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-103">This topic describes mining model content that is specific to models that use the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="e260d-104">모든 모델 유형에서 공유하는 통계 및 구조를 해석하는 방법에 대한 설명은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-logistic-regression-model"></a><span data-ttu-id="e260d-105">로지스틱 회귀 모델의 구조 이해</span><span class="sxs-lookup"><span data-stu-id="e260d-105">Understanding the Structure of a Logistic Regression Model</span></span>  
 <span data-ttu-id="e260d-106">로지스틱 회귀 모델은 Microsoft 신경망 알고리즘과 숨겨진 노드를 제거하도록 모델을 제한하는 매개 변수를 사용하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-106">A logistic regression model is created by using the Microsoft Neural Network algorithm with parameters that constrain the model to eliminate the hidden node.</span></span> <span data-ttu-id="e260d-107">따라서 로지스틱 회귀 모델의 전체 구조는 신경망 모델의 구조와 거의 동일합니다. 즉, 각 모델에는 모델 및 해당 메타데이터를 나타내는 단일 부모 노드와 모델에 사용된 입력에 대한 기술 통계를 제공하는 특수한 한계 통계 노드(NODE_TYPE = 24)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-107">Therefore, the overall structure of a logistic regression model is almost identical to that of a neural network: each model has a single parent node that represents the model and its metadata, and a special marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the inputs used in the model.</span></span>  
  
 <span data-ttu-id="e260d-108">또한 모델에는 예측 가능한 각 특성에 대한 하위 네트워크(NODE_TYPE = 17)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-108">Additionally, the model contains a subnetwork (NODE_TYPE = 17) for each predictable attribute.</span></span> <span data-ttu-id="e260d-109">신경망 모델에서와 마찬가지로 각 하위 네트워크에는 항상 두 개의 분기가 포함됩니다. 하나는 입력 계층에 대한 분기이고 숨겨진 계층(NODE_TYPE = 19) 및 출력 계층(NODE_TYPE = 20)이 포함된 다른 분기는 네트워크에 대한 분기입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-109">Just like in a neural network model, each subnetwork always contains two branches: one for the input layer, and another branch that contains the hidden layer (NODE_TYPE = 19) and the output layer (NODE_TYPE = 20) for the network.</span></span> <span data-ttu-id="e260d-110">여러 특성이 예측 전용으로 지정된 경우 이들 특성에 동일한 하위 네트워크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-110">The same subnetwork may be used for multiple attributes if they are specified as predict-only.</span></span> <span data-ttu-id="e260d-111">예측 가능한 특성이면서 동시에 입력 특성이기도 한 특성은 동일한 하위 네트워크에 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-111">Predictable attributes that are also inputs may not appear in the same subnetwork.</span></span>  
  
 <span data-ttu-id="e260d-112">그러나 로지스틱 회귀 모델에서는 숨겨진 계층을 나타내는 노드가 비어 있으며 자식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-112">However, in a logistic regression model, the node that represents the hidden layer is empty, and has no children.</span></span> <span data-ttu-id="e260d-113">따라서 모델에는 개별 출력(NODE_TYPE = 23) 및 개별 입력(NODE_TYPE = 21)을 나타내는 노드만 있고 숨겨진 개별 노드는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-113">Therefore the model contains nodes that represent individual outputs (NODE_TYPE = 23) and individual inputs (NODE_TYPE = 21) but no individual hidden nodes.</span></span>  
  
 <span data-ttu-id="e260d-114">![로지스틱 회귀 모델에 대한 콘텐츠 구조](../media/skt-modelcontentstructure-logregc.gif "로지스틱 회귀 모델에 대한 콘텐츠 구조")</span><span class="sxs-lookup"><span data-stu-id="e260d-114">![structure of content for logisitc regression model](../media/skt-modelcontentstructure-logregc.gif "structure of content for logisitc regression model")</span></span>  
  
 <span data-ttu-id="e260d-115">기본적으로 로지스틱 회귀 모델은 **Microsoft 신경망 뷰어**에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-115">By default, a logistic regression model is displayed in the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="e260d-116">이 사용자 지정 뷰어를 사용하면 입력 특성과 해당 값을 필터링하고 이러한 항목이 출력에 주는 영향을 그래픽으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-116">With this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="e260d-117">뷰어의 도구 설명에는 각 입력 및 출력 값 쌍과 연결된 확률 및 리프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-117">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="e260d-118">자세한 내용은 [Microsoft 신경망 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-neural-network-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-118">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="e260d-119">입력 및 하위 네트워크의 구조를 탐색하고 자세한 통계를 보려면 Microsoft 일반 콘텐츠 트리 뷰어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-119">To explore the structure of the inputs and subnetworks, and to see detailed statistics, you can use the Microsoft Generic Content Tree viewer.</span></span> <span data-ttu-id="e260d-120">임의의 노드를 클릭하여 확장한 후 자식 노드를 보거나 노드에 포함된 가중치 및 기타 통계를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-120">You can click on any node to expand it and see the child nodes, or view the weights and other statistics contained in the node.</span></span>  
  
## <a name="model-content-for-a-logistic-regression-model"></a><span data-ttu-id="e260d-121">로지스틱 회귀 모델에 대한 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-121">Model Content for a Logistic Regression Model</span></span>  
 <span data-ttu-id="e260d-122">이 섹션에서는 로지스틱 회귀와 특별히 관련된 마이닝 모델 콘텐츠 열에 대한 세부 정보 및 예만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-122">This section provides detail and examples only for those columns in the mining model content that have particular relevance for logistic regression.</span></span> <span data-ttu-id="e260d-123">로지스틱 회귀 모델 콘텐츠는 신경망 모델 콘텐츠와 거의 동일하지만 편의상 신경망 모델에 적용되는 설명이 이 표에서 반복될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-123">The model content is almost identical to that of a neural network model, but descriptions that apply to neural network models may be repeated in this table for convenience.</span></span>  
  
 <span data-ttu-id="e260d-124">MODEL_CATALOG와 MODEL_NAME을 비롯하여 여기에 설명되지 않은 스키마 행 집합의 범용 열에 대한 자세한 내용 또는 마이닝 모델 용어에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-124">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="e260d-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e260d-125">MODEL_CATALOG</span></span>  
 <span data-ttu-id="e260d-126">모델이 저장되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-126">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="e260d-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="e260d-127">MODEL_NAME</span></span>  
 <span data-ttu-id="e260d-128">모델의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-128">Name of the model.</span></span>  
  
 <span data-ttu-id="e260d-129">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="e260d-129">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="e260d-130">이 노드에 해당하는 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-130">The names of the attribute that corresponds to this node.</span></span>  
  
|<span data-ttu-id="e260d-131">노드</span><span class="sxs-lookup"><span data-stu-id="e260d-131">Node</span></span>|<span data-ttu-id="e260d-132">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-132">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e260d-133">모델 루트</span><span class="sxs-lookup"><span data-stu-id="e260d-133">Model root</span></span>|<span data-ttu-id="e260d-134">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-134">Blank</span></span>|  
|<span data-ttu-id="e260d-135">한계 통계</span><span class="sxs-lookup"><span data-stu-id="e260d-135">Marginal statistics</span></span>|<span data-ttu-id="e260d-136">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-136">Blank</span></span>|  
|<span data-ttu-id="e260d-137">입력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-137">Input layer</span></span>|<span data-ttu-id="e260d-138">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-138">Blank</span></span>|  
|<span data-ttu-id="e260d-139">입력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-139">Input node</span></span>|<span data-ttu-id="e260d-140">입력 특성 이름</span><span class="sxs-lookup"><span data-stu-id="e260d-140">Input attribute name</span></span>|  
|<span data-ttu-id="e260d-141">숨겨진 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-141">Hidden layer</span></span>|<span data-ttu-id="e260d-142">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-142">Blank</span></span>|  
|<span data-ttu-id="e260d-143">출력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-143">Output layer</span></span>|<span data-ttu-id="e260d-144">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-144">Blank</span></span>|  
|<span data-ttu-id="e260d-145">출력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-145">Output node</span></span>|<span data-ttu-id="e260d-146">출력 특성 이름</span><span class="sxs-lookup"><span data-stu-id="e260d-146">Output attribute name</span></span>|  
  
 <span data-ttu-id="e260d-147">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="e260d-147">NODE_NAME</span></span>  
 <span data-ttu-id="e260d-148">노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-148">The name of the node.</span></span> <span data-ttu-id="e260d-149">현재 이 열은 NODE_UNIQUE_NAME과 동일한 값을 포함하지만 이는 이후 릴리스에서 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-149">Currently, this column contains the same value as NODE_UNIQUE_NAME, though this may change in future releases.</span></span>  
  
 <span data-ttu-id="e260d-150">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="e260d-150">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="e260d-151">노드의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-151">The unique name of the node.</span></span>  
  
 <span data-ttu-id="e260d-152">이름과 ID가 모델에 대한 구조 정보를 반영하는 방식에 대한 자세한 내용은 [노드 이름 및 ID 사용](#bkmk_NodeIDs)섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-152">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="e260d-153">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e260d-153">NODE_TYPE</span></span>  
 <span data-ttu-id="e260d-154">로지스틱 회귀 모델이 출력하는 노드 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-154">A logistic regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="e260d-155">노드 유형 ID</span><span class="sxs-lookup"><span data-stu-id="e260d-155">Node Type ID</span></span>|<span data-ttu-id="e260d-156">Description</span><span class="sxs-lookup"><span data-stu-id="e260d-156">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="e260d-157">1</span><span class="sxs-lookup"><span data-stu-id="e260d-157">1</span></span>|<span data-ttu-id="e260d-158">모델</span><span class="sxs-lookup"><span data-stu-id="e260d-158">Model.</span></span>|  
|<span data-ttu-id="e260d-159">17</span><span class="sxs-lookup"><span data-stu-id="e260d-159">17</span></span>|<span data-ttu-id="e260d-160">하위 네트워크의 구성 도우미 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-160">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="e260d-161">18</span><span class="sxs-lookup"><span data-stu-id="e260d-161">18</span></span>|<span data-ttu-id="e260d-162">입력 계층의 구성 도우미 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-162">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="e260d-163">19</span><span class="sxs-lookup"><span data-stu-id="e260d-163">19</span></span>|<span data-ttu-id="e260d-164">숨겨진 계층의 구성 도우미 노드.</span><span class="sxs-lookup"><span data-stu-id="e260d-164">Organizer node for the hidden layer.</span></span> <span data-ttu-id="e260d-165">숨겨진 계층은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-165">The hidden layer is empty.</span></span>|  
|<span data-ttu-id="e260d-166">20</span><span class="sxs-lookup"><span data-stu-id="e260d-166">20</span></span>|<span data-ttu-id="e260d-167">출력 계층의 구성 도우미 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-167">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="e260d-168">21</span><span class="sxs-lookup"><span data-stu-id="e260d-168">21</span></span>|<span data-ttu-id="e260d-169">입력 특성 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-169">Input attribute node.</span></span>|  
|<span data-ttu-id="e260d-170">23</span><span class="sxs-lookup"><span data-stu-id="e260d-170">23</span></span>|<span data-ttu-id="e260d-171">출력 특성 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-171">Output attribute node.</span></span>|  
|<span data-ttu-id="e260d-172">24</span><span class="sxs-lookup"><span data-stu-id="e260d-172">24</span></span>|<span data-ttu-id="e260d-173">한계 통계 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-173">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="e260d-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e260d-174">NODE_CAPTION</span></span>  
 <span data-ttu-id="e260d-175">노드와 연결된 레이블 또는 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-175">A label or a caption associated with the node.</span></span> <span data-ttu-id="e260d-176">로지스틱 회귀 모델에서는 항상 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-176">In logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="e260d-177">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e260d-177">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="e260d-178">노드에 있는 예상 자식 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-178">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="e260d-179">노드</span><span class="sxs-lookup"><span data-stu-id="e260d-179">Node</span></span>|<span data-ttu-id="e260d-180">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-180">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e260d-181">모델 루트</span><span class="sxs-lookup"><span data-stu-id="e260d-181">Model root</span></span>|<span data-ttu-id="e260d-182">한 개 이상의 네트워크, 한 개의 필수 한계 노드 및 한 개의 필수 입력 계층을 포함하는 자식 노드의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-182">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="e260d-183">예를 들어 값이 5인 경우 3개의 하위 네트워크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-183">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="e260d-184">한계 통계</span><span class="sxs-lookup"><span data-stu-id="e260d-184">Marginal statistics</span></span>|<span data-ttu-id="e260d-185">항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-185">Always 0.</span></span>|  
|<span data-ttu-id="e260d-186">입력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-186">Input layer</span></span>|<span data-ttu-id="e260d-187">모델에 사용된 입력 특성-값 쌍의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-187">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="e260d-188">입력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-188">Input node</span></span>|<span data-ttu-id="e260d-189">항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-189">Always 0.</span></span>|  
|<span data-ttu-id="e260d-190">숨겨진 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-190">Hidden layer</span></span>|<span data-ttu-id="e260d-191">로지스틱 회귀 모델에서는 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-191">In a logistic regression model, always 0.</span></span>|  
|<span data-ttu-id="e260d-192">출력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-192">Output layer</span></span>|<span data-ttu-id="e260d-193">출력 값의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-193">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="e260d-194">출력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-194">Output node</span></span>|<span data-ttu-id="e260d-195">항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-195">Always 0.</span></span>|  
  
 <span data-ttu-id="e260d-196">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="e260d-196">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="e260d-197">노드 부모의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-197">The unique name of the node's parent.</span></span> <span data-ttu-id="e260d-198">루트 수준의 모든 노드에 대해서 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-198">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="e260d-199">이름과 ID가 모델에 대한 구조 정보를 반영하는 방식에 대한 자세한 내용은 [노드 이름 및 ID 사용](#bkmk_NodeIDs)섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-199">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="e260d-200">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e260d-200">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="e260d-201">노드에 대한 알기 쉬운 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-201">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="e260d-202">노드</span><span class="sxs-lookup"><span data-stu-id="e260d-202">Node</span></span>|<span data-ttu-id="e260d-203">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-203">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e260d-204">모델 루트</span><span class="sxs-lookup"><span data-stu-id="e260d-204">Model root</span></span>|<span data-ttu-id="e260d-205">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-205">Blank</span></span>|  
|<span data-ttu-id="e260d-206">한계 통계</span><span class="sxs-lookup"><span data-stu-id="e260d-206">Marginal statistics</span></span>|<span data-ttu-id="e260d-207">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-207">Blank</span></span>|  
|<span data-ttu-id="e260d-208">입력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-208">Input layer</span></span>|<span data-ttu-id="e260d-209">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-209">Blank</span></span>|  
|<span data-ttu-id="e260d-210">입력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-210">Input node</span></span>|<span data-ttu-id="e260d-211">입력 특성 이름</span><span class="sxs-lookup"><span data-stu-id="e260d-211">Input attribute name</span></span>|  
|<span data-ttu-id="e260d-212">숨겨진 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-212">Hidden layer</span></span>|<span data-ttu-id="e260d-213">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-213">Blank</span></span>|  
|<span data-ttu-id="e260d-214">출력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-214">Output layer</span></span>|<span data-ttu-id="e260d-215">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-215">Blank</span></span>|  
|<span data-ttu-id="e260d-216">출력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-216">Output node</span></span>|<span data-ttu-id="e260d-217">출력 특성이 연속 특성인 경우 출력 특성의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-217">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="e260d-218">출력 특성이 불연속 또는 불연속화된 특성인 경우 특성 이름 및 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-218">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="e260d-219">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="e260d-219">NODE_RULE</span></span>  
 <span data-ttu-id="e260d-220">노드에 포함된 규칙에 대한 XML 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-220">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="e260d-221">노드</span><span class="sxs-lookup"><span data-stu-id="e260d-221">Node</span></span>|<span data-ttu-id="e260d-222">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-222">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e260d-223">모델 루트</span><span class="sxs-lookup"><span data-stu-id="e260d-223">Model root</span></span>|<span data-ttu-id="e260d-224">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-224">Blank</span></span>|  
|<span data-ttu-id="e260d-225">한계 통계</span><span class="sxs-lookup"><span data-stu-id="e260d-225">Marginal statistics</span></span>|<span data-ttu-id="e260d-226">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-226">Blank</span></span>|  
|<span data-ttu-id="e260d-227">입력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-227">Input layer</span></span>|<span data-ttu-id="e260d-228">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-228">Blank</span></span>|  
|<span data-ttu-id="e260d-229">입력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-229">Input node</span></span>|<span data-ttu-id="e260d-230">NODE_DESCRIPTION 열과 동일한 정보가 들어 있는 XML 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-230">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="e260d-231">숨겨진 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-231">Hidden layer</span></span>|<span data-ttu-id="e260d-232">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-232">Blank</span></span>|  
|<span data-ttu-id="e260d-233">출력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-233">Output layer</span></span>|<span data-ttu-id="e260d-234">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-234">Blank</span></span>|  
|<span data-ttu-id="e260d-235">출력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-235">Output node</span></span>|<span data-ttu-id="e260d-236">NODE_DESCRIPTION 열과 동일한 정보가 들어 있는 XML 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-236">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="e260d-237">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="e260d-237">MARGINAL_RULE</span></span>  
 <span data-ttu-id="e260d-238">로지스틱 회귀 모델의 경우 항상 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-238">For logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="e260d-239">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e260d-239">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="e260d-240">이 노드와 관련된 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-240">The probability associated with this node.</span></span> <span data-ttu-id="e260d-241">로지스틱 회귀 모델의 경우 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-241">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="e260d-242">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e260d-242">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="e260d-243">부모 노드에서 해당 노드에 도달할 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-243">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="e260d-244">로지스틱 회귀 모델의 경우 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-244">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="e260d-245">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="e260d-245">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="e260d-246">노드에 대한 통계 정보가 들어 있는 중첩 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-246">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="e260d-247">각 노드 유형과 관련해서 이 테이블에 포함되는 내용에 대한 자세한 내용은 [신경망 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-247">For detailed information about the contents of this table for each node type, see the section, Understanding the NODE_DISTRIBUTION Table, in [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="e260d-248">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="e260d-248">NODE_SUPPORT</span></span>  
 <span data-ttu-id="e260d-249">로지스틱 회귀 모델의 경우 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-249">For logistic regression models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e260d-250">이 모델 유형의 출력은 확률적이 아니므로 지지도 확률은 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-250">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="e260d-251">이 알고리즘에 의미 있는 유일한 항목은 가중치이므로 이 알고리즘은 확률, 지지도 또는 분산을 컴퓨팅하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-251">The only thing that is meaningful for the algorithm is the weights; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="e260d-252">특정 값에 대한 학습 사례의 지지도에 관한 정보를 보려면 한계 통계 노드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e260d-252">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="e260d-253">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="e260d-253">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="e260d-254">노드</span><span class="sxs-lookup"><span data-stu-id="e260d-254">Node</span></span>|<span data-ttu-id="e260d-255">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="e260d-255">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="e260d-256">모델 루트</span><span class="sxs-lookup"><span data-stu-id="e260d-256">Model root</span></span>|<span data-ttu-id="e260d-257">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-257">Blank</span></span>|  
|<span data-ttu-id="e260d-258">한계 통계</span><span class="sxs-lookup"><span data-stu-id="e260d-258">Marginal statistics</span></span>|<span data-ttu-id="e260d-259">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-259">Blank</span></span>|  
|<span data-ttu-id="e260d-260">입력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-260">Input layer</span></span>|<span data-ttu-id="e260d-261">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-261">Blank</span></span>|  
|<span data-ttu-id="e260d-262">입력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-262">Input node</span></span>|<span data-ttu-id="e260d-263">입력 특성 이름</span><span class="sxs-lookup"><span data-stu-id="e260d-263">Input attribute name.</span></span>|  
|<span data-ttu-id="e260d-264">숨겨진 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-264">Hidden layer</span></span>|<span data-ttu-id="e260d-265">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-265">Blank</span></span>|  
|<span data-ttu-id="e260d-266">출력 계층</span><span class="sxs-lookup"><span data-stu-id="e260d-266">Output layer</span></span>|<span data-ttu-id="e260d-267">비어 있음</span><span class="sxs-lookup"><span data-stu-id="e260d-267">Blank</span></span>|  
|<span data-ttu-id="e260d-268">출력 노드</span><span class="sxs-lookup"><span data-stu-id="e260d-268">Output node</span></span>|<span data-ttu-id="e260d-269">입력 특성 이름</span><span class="sxs-lookup"><span data-stu-id="e260d-269">Input attribute name.</span></span>|  
  
 <span data-ttu-id="e260d-270">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="e260d-270">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="e260d-271">로지스틱 회귀 모델에서는 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-271">In logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="e260d-272">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e260d-272">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="e260d-273">로지스틱 회귀 모델에서는 항상 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-273">In logistic regression models, always blank.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a> <span data-ttu-id="e260d-274">노드 이름 및 ID 사용</span><span class="sxs-lookup"><span data-stu-id="e260d-274">Using Node Names and IDs</span></span>  
 <span data-ttu-id="e260d-275">로지스틱 회귀 모델의 노드 이름은 모델에 있는 노드 간의 관계에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-275">The naming of the nodes in a logistic regression model provides additional information about the relationships between nodes in the model.</span></span> <span data-ttu-id="e260d-276">다음 표에서는 각 계층의 노드에 할당되는 ID의 규칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-276">The following table shows the conventions for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="e260d-277">노드 유형</span><span class="sxs-lookup"><span data-stu-id="e260d-277">Node Type</span></span>|<span data-ttu-id="e260d-278">노드 ID의 규칙</span><span class="sxs-lookup"><span data-stu-id="e260d-278">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="e260d-279">모델 루트(1)</span><span class="sxs-lookup"><span data-stu-id="e260d-279">Model root (1)</span></span>|<span data-ttu-id="e260d-280">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="e260d-280">00000000000000000.</span></span>|  
|<span data-ttu-id="e260d-281">한계 통계 노드(24)</span><span class="sxs-lookup"><span data-stu-id="e260d-281">Marginal statistics node (24)</span></span>|<span data-ttu-id="e260d-282">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="e260d-282">10000000000000000</span></span>|  
|<span data-ttu-id="e260d-283">입력 계층(18)</span><span class="sxs-lookup"><span data-stu-id="e260d-283">Input layer (18)</span></span>|<span data-ttu-id="e260d-284">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="e260d-284">30000000000000000</span></span>|  
|<span data-ttu-id="e260d-285">입력 노드(21)</span><span class="sxs-lookup"><span data-stu-id="e260d-285">Input node (21)</span></span>|<span data-ttu-id="e260d-286">60000000000000000에서 시작</span><span class="sxs-lookup"><span data-stu-id="e260d-286">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="e260d-287">하위 네트워크(17)</span><span class="sxs-lookup"><span data-stu-id="e260d-287">Subnetwork (17)</span></span>|<span data-ttu-id="e260d-288">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="e260d-288">20000000000000000</span></span>|  
|<span data-ttu-id="e260d-289">숨겨진 계층(19)</span><span class="sxs-lookup"><span data-stu-id="e260d-289">Hidden layer (19)</span></span>|<span data-ttu-id="e260d-290">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="e260d-290">40000000000000000</span></span>|  
|<span data-ttu-id="e260d-291">출력 계층(20)</span><span class="sxs-lookup"><span data-stu-id="e260d-291">Output layer (20)</span></span>|<span data-ttu-id="e260d-292">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="e260d-292">50000000000000000</span></span>|  
|<span data-ttu-id="e260d-293">출력 노드(23)</span><span class="sxs-lookup"><span data-stu-id="e260d-293">Output node (23)</span></span>|<span data-ttu-id="e260d-294">80000000000000000에서 시작</span><span class="sxs-lookup"><span data-stu-id="e260d-294">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="e260d-295">이러한 ID를 통해 출력 노드의 NODE_DISTRIBUTION 테이블을 보고 출력 특성과 특정 입력 계층 특성 간의 관계를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-295">You can use these IDs to determine how output attributes are related to specific input layer attributes, by viewing the NODE_DISTRIBUTION table of the output node.</span></span> <span data-ttu-id="e260d-296">해당 테이블의 각 행에는 다시 특정 입력 특성 노드를 가리키는 ID가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-296">Each row in that table contains an ID that points back to a specific input attribute node.</span></span> <span data-ttu-id="e260d-297">NODE_DISTRIBUTION 테이블에는 해당 입력-출력 쌍에 대한 계수도 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e260d-297">The NODE_DISTRIBUTION table also contains the coefficient for that input-output pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e260d-298">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e260d-298">See Also</span></span>  
 <span data-ttu-id="e260d-299">[Microsoft 로지스틱 회귀 알고리즘](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="e260d-299">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="e260d-300">[신경망 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e260d-300">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e260d-301">[로지스틱 회귀 모델 쿼리 예제](logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="e260d-301">[Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md) </span></span>  
 [<span data-ttu-id="e260d-302">Microsoft 로지스틱 회귀 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="e260d-302">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)  
  
  
