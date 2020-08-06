---
title: 연결 모델에 대 한 마이닝 모델 콘텐츠 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8904ce155526aee595db19094fd2bad48770e83e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649831"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a><span data-ttu-id="ccdc1-102">연결 모델에 대한 마이닝 모델 콘텐츠(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="ccdc1-102">Mining Model Content for Association Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="ccdc1-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 알고리즘을 사용하는 모델에만 적용되는 마이닝 모델 콘텐츠에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="ccdc1-104">모든 모델 유형에 적용되는 마이닝 모델 콘텐츠와 관련된 일반 용어 및 통계 용어에 대한 설명은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-104">For an explanation of general and statistical terminology related to mining model content that applies to all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-an-association-model"></a><span data-ttu-id="ccdc1-105">연결 모델의 구조 이해</span><span class="sxs-lookup"><span data-stu-id="ccdc1-105">Understanding the Structure of an Association Model</span></span>  
 <span data-ttu-id="ccdc1-106">연결 모델의 구조는 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-106">An association model has a simple structure.</span></span> <span data-ttu-id="ccdc1-107">각 모델에는 모델과 메타데이터를 나타내는 부모 노드가 한 개 있고 각 부모 노드에는 항목 집합과 규칙에 대한 기본 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of itemsets and rules.</span></span> <span data-ttu-id="ccdc1-108">항목 집합과 규칙은 트리로 구성되어 있지 않으며 다음 다이어그램에서와 같이 항목 집합 및 규칙 순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-108">The itemsets and rules are not organized in trees, they are ordered with itemsets first and rules next as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="ccdc1-109">![연결 모델에 대한 모델 콘텐츠 구조](../media/modelcontentstructure-assoc.gif "연결 모델에 대한 모델 콘텐츠 구조")</span><span class="sxs-lookup"><span data-stu-id="ccdc1-109">![structure of model content for association models](../media/modelcontentstructure-assoc.gif "structure of model content for association models")</span></span>  
  
 <span data-ttu-id="ccdc1-110">각 항목 집합은 자체 노드(NODE_TYPE = 7)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-110">Each itemset is contained in its own node (NODE_TYPE = 7).</span></span> <span data-ttu-id="ccdc1-111">*노드* 에는 항목 집합의 정의, 이 항목 집합을 포함하는 사례 수 및 기타 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-111">The *node* includes the definition of the itemset, the number of cases that contain this itemset, and other information.</span></span>  
  
 <span data-ttu-id="ccdc1-112">각 규칙도 자체 노드(NODE_TYPE = 8)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-112">Each rule is also contained in its own node (NODE_TYPE = 8).</span></span> <span data-ttu-id="ccdc1-113">*규칙* 은 항목이 연결되는 일반적인 패턴에 대해 설명하며</span><span class="sxs-lookup"><span data-stu-id="ccdc1-113">A *rule* describes a general pattern for how items are associated.</span></span> <span data-ttu-id="ccdc1-114">IF-THEN 문과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-114">A rule is like an IF-THEN statement.</span></span> <span data-ttu-id="ccdc1-115">규칙의 왼쪽에는 기존 조건 또는 조건 집합이 표시되고</span><span class="sxs-lookup"><span data-stu-id="ccdc1-115">The left-hand side of the rule shows an existing condition or set of conditions.</span></span> <span data-ttu-id="ccdc1-116">규칙의 오른쪽에는 일반적으로 왼쪽에 있는 조건과 연결되는 데이터 집합의 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-116">The right-hand side of the rule shows the item in your data set that is usually associated with the conditions on the left side.</span></span>  
  
 <span data-ttu-id="ccdc1-117">**참고** 규칙 또는 항목 집합을 추출하려는 경우 쿼리를 사용하여 원하는 노드 유형만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-117">**Note** If you want to extract either the rules or the itemsets, you can use a query to return only the node types that you want.</span></span> <span data-ttu-id="ccdc1-118">자세한 내용은 [연결 모델 쿼리 예제](association-model-query-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-118">For more information, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
## <a name="model-content-for-an-association-model"></a><span data-ttu-id="ccdc1-119">연결 모델에 대한 모델 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="ccdc1-119">Model Content for an Association Model</span></span>  
 <span data-ttu-id="ccdc1-120">이 섹션에서는 연결 모델과 관련된 마이닝 모델 콘텐츠 열에 대한 세부 정보와 예만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-120">This section provides detail and examples only for those columns in the mining model content that are relevant for association models.</span></span>  
  
 <span data-ttu-id="ccdc1-121">스키마 행 집합(예: MODEL_CATALOG 및 MODEL_NAME)의 범용 열에 대한 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-121">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="ccdc1-122">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ccdc1-122">MODEL_CATALOG</span></span>  
 <span data-ttu-id="ccdc1-123">모델이 저장되는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-123">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="ccdc1-124">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="ccdc1-124">MODEL_NAME</span></span>  
 <span data-ttu-id="ccdc1-125">모델의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-125">Name of the model.</span></span>  
  
 <span data-ttu-id="ccdc1-126">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="ccdc1-126">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="ccdc1-127">이 노드에 해당하는 특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-127">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="ccdc1-128">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="ccdc1-128">NODE_NAME</span></span>  
 <span data-ttu-id="ccdc1-129">노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-129">The name of the node.</span></span> <span data-ttu-id="ccdc1-130">연결 모델의 경우 이 열은 NODE_UNIQUE_NAME과 동일한 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-130">For an association model, this column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="ccdc1-131">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="ccdc1-131">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="ccdc1-132">노드의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-132">The unique name of the node.</span></span>  
  
 <span data-ttu-id="ccdc1-133">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-133">NODE_TYPE</span></span>  
 <span data-ttu-id="ccdc1-134">연결 모델이 출력하는 노드 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-134">A association model outputs only the following node types:</span></span>  
  
|<span data-ttu-id="ccdc1-135">노드 유형 ID</span><span class="sxs-lookup"><span data-stu-id="ccdc1-135">Node Type ID</span></span>|<span data-ttu-id="ccdc1-136">Type</span><span class="sxs-lookup"><span data-stu-id="ccdc1-136">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="ccdc1-137">1(모델)</span><span class="sxs-lookup"><span data-stu-id="ccdc1-137">1 (Model)</span></span>|<span data-ttu-id="ccdc1-138">루트 또는 부모 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-138">Root or parent node.</span></span>|  
|<span data-ttu-id="ccdc1-139">7(항목 집합)</span><span class="sxs-lookup"><span data-stu-id="ccdc1-139">7 (Itemset)</span></span>|<span data-ttu-id="ccdc1-140">항목 집합 또는 특성-값 쌍 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-140">An itemset, or collection of attribute-value pairs.</span></span> <span data-ttu-id="ccdc1-141">예제:</span><span class="sxs-lookup"><span data-stu-id="ccdc1-141">Examples:</span></span><br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> <span data-ttu-id="ccdc1-142">를 실행하거나</span><span class="sxs-lookup"><span data-stu-id="ccdc1-142">or</span></span><br /><br /> <span data-ttu-id="ccdc1-143">`Gender = Male`.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-143">`Gender = Male`.</span></span>|  
|<span data-ttu-id="ccdc1-144">8(규칙)</span><span class="sxs-lookup"><span data-stu-id="ccdc1-144">8 (Rule)</span></span>|<span data-ttu-id="ccdc1-145">항목 간의 관련 방식을 정의하는 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-145">A rule defining how items relate to each other.</span></span><br /><br /> <span data-ttu-id="ccdc1-146">예:</span><span class="sxs-lookup"><span data-stu-id="ccdc1-146">Example:</span></span><br /><br /> <span data-ttu-id="ccdc1-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span></span>|  
  
 <span data-ttu-id="ccdc1-148">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ccdc1-148">NODE_CAPTION</span></span>  
 <span data-ttu-id="ccdc1-149">노드와 연결된 레이블 또는 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-149">A label or a caption associated with the node.</span></span>  
  
 <span data-ttu-id="ccdc1-150">**항목 집합 노드** 쉼표로 구분된 항목 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-150">**Itemset node** A comma-separated list of items.</span></span>  
  
 <span data-ttu-id="ccdc1-151">**규칙 노드** 규칙의 왼쪽과 오른쪽을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-151">**Rule node** Contains the left and right-hand sides of the rule.</span></span>  
  
 <span data-ttu-id="ccdc1-152">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="ccdc1-152">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="ccdc1-153">현재 노드의 자식 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-153">Indicates the number of children of the current node.</span></span>  
  
 <span data-ttu-id="ccdc1-154">**부모 노드** 항목 집합 수에 규칙 수를 더한 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-154">**Parent node** Indicates the total number of itemsets plus rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccdc1-155">항목 집합 및 규칙 수에 대한 세부 분류를 보려면 모델 루트 노드의 NODE_DESCRIPTION을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-155">To get a breakdown of the count for itemsets and rules, see the NODE_DESCRIPTION for the root node of the model.</span></span>  
  
 <span data-ttu-id="ccdc1-156">**항목 집합 또는 규칙 노드** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-156">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="ccdc1-157">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="ccdc1-157">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="ccdc1-158">노드 부모의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-158">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="ccdc1-159">**부모 노드** 항상 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-159">**Parent node** Always NULL.</span></span>  
  
 <span data-ttu-id="ccdc1-160">**항목 집합 또는 규칙 노드** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-160">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="ccdc1-161">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ccdc1-161">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="ccdc1-162">노드 콘텐츠에 대한 알기 쉬운 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-162">A user-friendly description of the contents of the node.</span></span>  
  
 <span data-ttu-id="ccdc1-163">**부모 노드** 다음과 같은 모델 정보 목록을 쉼표로 구분하여 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-163">**Parent node** Includes a comma-separated list of the following information about the model:</span></span>  
  
|<span data-ttu-id="ccdc1-164">항목</span><span class="sxs-lookup"><span data-stu-id="ccdc1-164">Item</span></span>|<span data-ttu-id="ccdc1-165">Description</span><span class="sxs-lookup"><span data-stu-id="ccdc1-165">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ccdc1-166">ITEMSET_COUNT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-166">ITEMSET_COUNT</span></span>|<span data-ttu-id="ccdc1-167">모델에 있는 모든 항목 집합 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-167">Count of all itemsets in model.</span></span>|  
|<span data-ttu-id="ccdc1-168">RULE_COUNT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-168">RULE_COUNT</span></span>|<span data-ttu-id="ccdc1-169">모델에 있는 모든 규칙 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-169">Count of all rules in model.</span></span>|  
|<span data-ttu-id="ccdc1-170">MIN_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-170">MIN_SUPPORT</span></span>|<span data-ttu-id="ccdc1-171">단일 항목 집합에 대해 발견된 최소 지지도입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-171">The minimum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="ccdc1-172">**참고** 이 값은 *MINIMUM _SUPPORT* 매개 변수에 설정한 값과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-172">**Note** This value might differ from the value that you set for the *MINIMUM _SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="ccdc1-173">MAX_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-173">MAX_SUPPORT</span></span>|<span data-ttu-id="ccdc1-174">단일 항목 집합에 대해 발견된 최대 지지도입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-174">The maximum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="ccdc1-175">**참고** 이 값은 *MAXIMUM_SUPPORT* 매개 변수에 설정한 값과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-175">**Note** This value might differ from the value that you set for the *MAXIMUM_SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="ccdc1-176">MIN_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-176">MIN_ITEMSET_SIZE</span></span>|<span data-ttu-id="ccdc1-177">최소 항목 집합의 크기이며 항목 수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-177">The size of the smallest itemset, represented as a count of items.</span></span><br /><br /> <span data-ttu-id="ccdc1-178">값 0은 `Missing` 상태가 개별 항목으로 처리되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-178">A value of 0 indicates that the `Missing` state was treated as an independent item.</span></span><br /><br /> <span data-ttu-id="ccdc1-179">\**참고\*\*\*MINIMUM_ITEMSET_SIZE* 매개 변수의 기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-179">**Note** The default value of the *MINIMUM_ITEMSET_SIZE* parameter is 1.</span></span>|  
|<span data-ttu-id="ccdc1-180">MAX_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-180">MAX_ITEMSET_SIZE</span></span>|<span data-ttu-id="ccdc1-181">발견된 가장 큰 항목 집합의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-181">Indicates the size of the largest itemset that was found.</span></span><br /><br /> <span data-ttu-id="ccdc1-182">**참고** 이 값은 모델을 만들 때 *MAX_ITEMSET_SIZE* 매개 변수에 설정한 값에 따라 제약을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-182">**Note** This value is constrained by the value that you set for the *MAX_ITEMSET_SIZE* parameter when you created the model.</span></span> <span data-ttu-id="ccdc1-183">즉, 해당 매개 변수 값보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-183">This value can never exceed that value; however, it can be less.</span></span> <span data-ttu-id="ccdc1-184">기본값은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-184">The default value is 3.</span></span>|  
|<span data-ttu-id="ccdc1-185">MIN_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ccdc1-185">MIN_PROBABILITY</span></span>|<span data-ttu-id="ccdc1-186">모델에 있는 단일 항목 집합 또는 규칙에 대해 발견된 최소 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-186">The minimum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="ccdc1-187">예: 0.400390625</span><span class="sxs-lookup"><span data-stu-id="ccdc1-187">Example: 0.400390625</span></span><br /><br /> <span data-ttu-id="ccdc1-188">**참고** 항목 집합의 경우 이 값은 모델을 만들 때 *MINIMUM_PROBABILITY* 매개 변수에 설정한 값보다 항상 큽니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-188">**Note** For itemsets, this value is always greater than the value that you set for the *MINIMUM_PROBABILITY* parameter when you created the model.</span></span>|  
|<span data-ttu-id="ccdc1-189">MAX_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ccdc1-189">MAX_PROBABILITY</span></span>|<span data-ttu-id="ccdc1-190">모델에 있는 단일 항목 집합 또는 규칙에 대해 발견된 최대 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-190">The maximum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="ccdc1-191">예: 1</span><span class="sxs-lookup"><span data-stu-id="ccdc1-191">Example: 1</span></span><br /><br /> <span data-ttu-id="ccdc1-192">**참고** 항목 집합의 최대 확률을 제약하는 매개 변수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-192">**Note** There is no parameter to constrain maximum probability of itemsets.</span></span> <span data-ttu-id="ccdc1-193">너무 자주 사용되는 항목을 제거하려면 *MAXIMUM_SUPPORT* 매개 변수를 대신 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-193">If you want to eliminate items that are too frequent, use the *MAXIMUM_SUPPORT* parameter instead.</span></span>|  
|<span data-ttu-id="ccdc1-194">MIN_LIFT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-194">MIN_LIFT</span></span>|<span data-ttu-id="ccdc1-195">모델이 항목 집합에 제공하는 최소 리프트 양입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-195">The minimum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="ccdc1-196">예: 0.14309369632511</span><span class="sxs-lookup"><span data-stu-id="ccdc1-196">Example: 0.14309369632511</span></span><br /><br /> <span data-ttu-id="ccdc1-197">참고: 최소 리프트를 알면 한 항목 집합에 대한 리프트가 중요한지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-197">Note: Knowing the minimum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
|<span data-ttu-id="ccdc1-198">MAX_LIFT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-198">MAX_LIFT</span></span>|<span data-ttu-id="ccdc1-199">모델이 항목 집합에 제공하는 최대 리프트 양입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-199">The maximum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="ccdc1-200">예: 1.95758227647523 **참고** 최대 리프트를 알면 한 항목 집합에 대한 리프트가 중요한지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-200">Example: 1.95758227647523 **Note** Knowing the maximum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
  
 <span data-ttu-id="ccdc1-201">**항목 집합 노드** 항목 집합 노드는 항목 목록을 포함하며 쉼표로 구분된 텍스트 문자열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-201">**Itemset node** Itemset nodes contain a list of the items, displayed as a comma-separated text string.</span></span>  
  
 <span data-ttu-id="ccdc1-202">예:</span><span class="sxs-lookup"><span data-stu-id="ccdc1-202">Example:</span></span>  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 <span data-ttu-id="ccdc1-203">이는 Touring Tire와 Water Bottle을 함께 구매했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-203">This means touring tires and water bottles were purchased together.</span></span>  
  
 <span data-ttu-id="ccdc1-204">**규칙 노드** 규칙 노드는 화살표로 구분된 규칙의 왼쪽과 오른쪽을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-204">**Rule node** Rule nodes contains a left-hand and right-hand side of the rule, separated by an arrow.</span></span>  
  
 <span data-ttu-id="ccdc1-205">예: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span><span class="sxs-lookup"><span data-stu-id="ccdc1-205">Example: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span></span>  
  
 <span data-ttu-id="ccdc1-206">이는 누군가가 Touring Tire와 Water Bottle을 구매했는데 이 사람이 Cycling cap을 구매했을 가능성도 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-206">This means that if someone bought a touring tire and a water bottle, they were also likely to buy a cycling cap.</span></span>  
  
 <span data-ttu-id="ccdc1-207">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-207">NODE_RULE</span></span>  
 <span data-ttu-id="ccdc1-208">노드에 포함된 규칙 또는 항목 집합을 설명하는 XML 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-208">An XML fragment that describes the rule or itemset that is embedded in the node.</span></span>  
  
 <span data-ttu-id="ccdc1-209">**부모 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-209">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-210">**항목 집합 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-210">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-211">**규칙 노드** XML 조각은 지지도, 신뢰성, 항목 수, 규칙의 왼쪽을 나타내는 노드의 ID 등과 같은 유용한 추가 규칙 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-211">**Rule node** The XML fragment includes additional useful information about the rule, such as support, confidence, and the number of items, and the ID of the node that represents the left-hand side of the rule.</span></span>  
  
 <span data-ttu-id="ccdc1-212">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-212">MARGINAL_RULE</span></span>  
 <span data-ttu-id="ccdc1-213">비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-213">Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-214">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ccdc1-214">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="ccdc1-215">항목 집합 또는 규칙과 관련된 확률 또는 신뢰성 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-215">A probability or confidence score associated with the itemset or rule.</span></span>  
  
 <span data-ttu-id="ccdc1-216">**부모 노드** 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-216">**Parent node** Always 0.</span></span>  
  
 <span data-ttu-id="ccdc1-217">**항목 집합 노드** 항목 집합의 확률입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-217">**Itemset node** Probability of the itemset.</span></span>  
  
 <span data-ttu-id="ccdc1-218">**규칙 노드** 규칙에 대한 신뢰성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-218">**Rule node** Confidence value for the rule.</span></span>  
  
 <span data-ttu-id="ccdc1-219">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ccdc1-219">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="ccdc1-220">NODE_PROBABILITY와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-220">Same as NODE_PROBABILITY.</span></span>  
  
 <span data-ttu-id="ccdc1-221">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="ccdc1-221">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="ccdc1-222">이 테이블은 노드가 항목 집합인지 또는 규칙인지에 따라 매우 다른 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-222">The table contains very different information, depending on whether the node is an itemset or a rule.</span></span>  
  
 <span data-ttu-id="ccdc1-223">**부모 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-223">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-224">**항목 집합 노드** 항목 집합에 포함된 각 항목을 확률 및 지지도 값과 함께 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-224">**Itemset node** Lists each item in the itemset together with a probability and support value.</span></span> <span data-ttu-id="ccdc1-225">예를 들어 항목 집합이 두 개의 제품을 포함할 경우 각 제품의 이름이 이 제품에 포함된 사례 수와 함께 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-225">For example, if the itemset contains two products, the name of each product is listed, together with the count of cases that include each product.</span></span>  
  
 <span data-ttu-id="ccdc1-226">**규칙 노드** 두 개의 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-226">**Rule node** Contains two rows.</span></span> <span data-ttu-id="ccdc1-227">첫 번째 행은 규칙의 오른쪽에 있는 특성 즉, 예상 항목을 신뢰성 점수와 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-227">The first row shows the attribute from the right-hand side of the rule, which is the predicted item, together with a confidence score.</span></span>  
  
 <span data-ttu-id="ccdc1-228">두 번째 행은 연결 모델에만 해당되며 규칙 오른쪽에 있는 항목 집합에 대한 포인터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-228">The second row is unique to association models; it contains a pointer to the itemset on the right-hand side of the rule.</span></span> <span data-ttu-id="ccdc1-229">이 포인터는 ATTRIBUTE_VALUE 열에 오른쪽 항목만 포함하는 항목 집합의 ID로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-229">The pointer is represented in the ATTRIBUTE_VALUE column as the ID of the itemset that contains only the right-hand item.</span></span>  
  
 <span data-ttu-id="ccdc1-230">예를 들어 규칙이 `If {A,B} Then {C}`일 경우 테이블은 항목 `{C}`의 이름 및 항목 C에 대한 항목 집합을 포함하는 노드의 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-230">For example, if the rule is `If {A,B} Then {C}`, the table contains the name of the item `{C}`, and the ID of the node that contains the itemset for item C.</span></span>  
  
 <span data-ttu-id="ccdc1-231">이 포인터는 항목 집합 노드에서 오른쪽 제품을 포함하는 모든 사례 수를 확인할 수 있으므로 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-231">This pointer is useful because you can determine from the itemset node how many cases in all include the right-hand side product.</span></span> <span data-ttu-id="ccdc1-232">`If {A,B} Then {C}` 규칙의 영향을 받는 사례는 `{C}`에 대한 항목 집합에 나열된 사례의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-232">The cases that are subject to the rule `If {A,B} Then {C}` are a subset of the cases listed in the itemset for `{C}`.</span></span>  
  
 <span data-ttu-id="ccdc1-233">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ccdc1-233">NODE_SUPPORT</span></span>  
 <span data-ttu-id="ccdc1-234">이 노드를 지지하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-234">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="ccdc1-235">**부모 노드** 모델에 포함된 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-235">**Parent node** Number of cases in the model.</span></span>  
  
 <span data-ttu-id="ccdc1-236">**항목 집합 노드** 항목 집합의 모든 항목을 포함하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-236">**Itemset node** Number of cases that contains all items in the itemset.</span></span>  
  
 <span data-ttu-id="ccdc1-237">**규칙 노드** 규칙에 포함된 모든 항목을 포함하는 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-237">**Rule node** The number of cases that contain all items included in the rule.</span></span>  
  
 <span data-ttu-id="ccdc1-238">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="ccdc1-238">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="ccdc1-239">노드가 항목 집합인지 또는 규칙인지에 따라 다른 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-239">Contains different information depending on whether the node is an itemset or rule.</span></span>  
  
 <span data-ttu-id="ccdc1-240">**부모 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-240">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-241">**항목 집합 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-241">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-242">**규칙 노드** 규칙의 왼쪽에 있는 항목을 포함하는 항목 집합의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-242">**Rule node** The ID of the itemset that contains the items in the left-hand side of the rule.</span></span> <span data-ttu-id="ccdc1-243">예를 들어 규칙이 `If {A,B} Then {C}`일 경우 이 열은 항목 `{A,B}`만 포함하는 항목 집합의 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-243">For example, if the rule is `If {A,B} Then {C}`, this column contains the ID of the itemset that contains only `{A,B}`.</span></span>  
  
 <span data-ttu-id="ccdc1-244">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="ccdc1-244">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="ccdc1-245">**부모 노드** 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-245">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="ccdc1-246">**항목 집합 노드** 항목 집합의 중요도 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-246">**Itemset node** Importance score for the itemset.</span></span>  
  
 <span data-ttu-id="ccdc1-247">**규칙 노드** 규칙의 중요도 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-247">**Rule node** Importance score for the rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccdc1-248">중요도는 항목 집합 및 규칙에 대해 서로 다르게 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-248">Importance is calculated differently for itemsets and rules.</span></span> <span data-ttu-id="ccdc1-249">자세한 내용은 [Microsoft 연결 알고리즘 기술 참조](microsoft-association-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-249">For more information, see [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="ccdc1-250">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ccdc1-250">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="ccdc1-251">비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccdc1-251">Blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdc1-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccdc1-252">See Also</span></span>  
 <span data-ttu-id="ccdc1-253">[마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ccdc1-253">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ccdc1-254">[Microsoft 연결 알고리즘](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ccdc1-254">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="ccdc1-255">연결 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="ccdc1-255">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
  
