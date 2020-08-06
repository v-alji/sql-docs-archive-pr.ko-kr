---
title: 모델링 플래그 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- data types [data mining]
- REGRESSOR flag
- MODEL_EXISTENCE_ONLY flag
- REGRESSOR column
- columns [data mining], modeling flags
- NOT NULL modeling flag
- modeling flags [data mining]
- null values [Analysis Services]
- MODEL_EXISTENCE_ONLY column
- coding [Data Mining]
ms.assetid: 8826d5ce-9ba8-4490-981b-39690ace40a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f1c802f6503b84ff4f6879c18d3bffebb46d7ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728968"
---
# <a name="modeling-flags-data-mining"></a><span data-ttu-id="59555-102">모델링 플래그(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="59555-102">Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="59555-103">에서 모델링 플래그를 사용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 하 여 사례 테이블에 정의 된 데이터에 대 한 추가 정보를 데이터 마이닝 알고리즘에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-103">You can use modeling flags in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide additional information to a data mining algorithm about the data that is defined in a case table.</span></span> <span data-ttu-id="59555-104">데이터 마이닝 알고리즘은 이 정보를 토대로 더욱 정확한 데이터 마이닝 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-104">The algorithm can use this information to build a more accurate data mining model.</span></span>  
  
 <span data-ttu-id="59555-105">마이닝 구조 수준에서 정의되는 모델링 플래그도 있고 마이닝 모델 열 수준에서 정의되는 모델링 플래그도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-105">Some modeling flags are defined at the level of the mining structure, whereas others are defined at the level of the mining model column.</span></span> <span data-ttu-id="59555-106">예를 들어 `NOT NULL` 모델링 플래그는 마이닝 구조 열에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-106">For example, the `NOT NULL` modeling flag is used with mining structure columns.</span></span> <span data-ttu-id="59555-107">모델을 만드는 데 사용하는 알고리즘에 따라 마이닝 모델 열에 추가 모델링 플래그를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-107">You can define additional modeling flags on the mining model columns, depending on the algorithm you use to create the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59555-108">타사 플러그 인의 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 미리 정의한 모델링 플래그 외에 다른 모델링 플래그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-108">Third-party plug-ins might have other modeling flags, in addition to those pre-defined by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="list-of-modeling-flags"></a><span data-ttu-id="59555-109">모델링 플래그 목록</span><span class="sxs-lookup"><span data-stu-id="59555-109">List of Modeling Flags</span></span>  
 <span data-ttu-id="59555-110">다음 목록에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 지원하는 모델링 플래그에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-110">The following list describes the modeling flags that are supported in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="59555-111">특정 알고리즘에서 지원하는 모델링 플래그에 대한 자세한 내용은 모델을 만드는 데 사용된 알고리즘의 기술 참조 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="59555-111">For information about modeling flags that are supported by specific algorithms, see the technical reference topic for the algorithm that was used to create the model.</span></span>  
  
 `NOT NULL`  
 <span data-ttu-id="59555-112">특성 열 값이 Null 값을 포함할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59555-112">Indicates that the values for the attribute column should never contain a null value.</span></span> <span data-ttu-id="59555-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 모델 학습 프로세스 중 이 특성 열에 Null 값이 있는 경우에는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-113">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null value for this attribute column during the model training process.</span></span>  
  
 <span data-ttu-id="59555-114">**MODEL_EXISTENCE_ONLY**</span><span class="sxs-lookup"><span data-stu-id="59555-114">**MODEL_EXISTENCE_ONLY**</span></span>  
 <span data-ttu-id="59555-115">열이 `Missing` 및 `Existing` 상태로 처리됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59555-115">Indicates that the column will be treated as having two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="59555-116">값이 `NULL`인 경우 Missing으로 간주됩니다</span><span class="sxs-lookup"><span data-stu-id="59555-116">If the value is `NULL`, it is treated as Missing.</span></span> <span data-ttu-id="59555-117">MODEL_EXISTENCE_ONLY 플래그는 예측 가능한 특성에 적용되며 대부분의 알고리즘에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-117">The MODEL_EXISTENCE_ONLY flag is applied to the predictable attribute and is supported by most algorithms.</span></span>  
  
 <span data-ttu-id="59555-118">실제로 MODEL_EXISTENCE_ONLY 플래그를 `True`로 설정하면 `Missing` 및 `Existing`과 같은 두 개의 문이 있는 경우 값을 다르게 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-118">In effect, setting the MODEL_EXISTENCE_ONLY flag to `True` changes the representation of the values such that there are only two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="59555-119">누락되지 않은 상태는 모두 단일 `Existing` 값으로 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-119">All the non-missing states are combined into a single `Existing` value.</span></span>  
  
 <span data-ttu-id="59555-120">이 모델링 플래그는 일반적으로 `NULL` 상태가 암시적인 의미를 갖는 특성을 나타내는 데 사용됩니다. 따라서 `NOT NULL` 상태의 명시적 값은 열이 값을 갖는다는 사실만큼이나 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-120">A typical use for this modeling flag would be in attributes for which the `NULL` state has an implicit meaning, and the explicit value of the `NOT NULL` state might not be as important as the fact that the column has any value.</span></span> <span data-ttu-id="59555-121">예를 들어 서명되지 않은 계약의 경우 [DateContractSigned] 열이 `NULL`이고 서명된 계약의 경우 `NOT NULL`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-121">For example, a [DateContractSigned] column might be `NULL` if a contract was never signed and `NOT NULL` if the contract was signed.</span></span> <span data-ttu-id="59555-122">따라서 모델의 목적이 계약에 서명할 것인지 여부를 예측하는 것이라면 MODEL_EXISTENCE_ONLY 플래그를 사용하여 `NOT NULL` 사례의 정확한 날짜 값은 무시하고 계약이 `Missing` 또는 `Existing`인 사례만 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-122">Therefore, if the purpose of the model is to predict whether a contract will be signed, you can use the MODEL_EXISTENCE_ONLY flag to ignore the exact date value in the `NOT NULL` cases and distinguish only between cases where a contract is `Missing` or `Existing`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59555-123">Missing은 알고리즘에서 사용하는 특수한 상태로 열의 텍스트 값인 "Missing"과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="59555-123">Missing is a special state used by the algorithm, and differs from the text value "Missing" in a column.</span></span> <span data-ttu-id="59555-124">자세한 내용은 [누락 값&#40;Analysis Services - 데이터 마이닝&#41;](missing-values-analysis-services-data-mining.md)에서 미리 정의한 모델링 플래그 외에 다른 모델링 플래그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-124">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="59555-125">열이 처리 중에 회귀 변수로 사용할 후보임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59555-125">Indicates that the column is a candidate for used as a regressor during processing.</span></span> <span data-ttu-id="59555-126">이 플래그는 마이닝 모델 열에서 정의되며 연속 숫자 데이터 형식이 있는 열에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-126">This flag is defined on a mining model column, and can only be applied to columns that have a continuous numeric data type.</span></span> <span data-ttu-id="59555-127">이 플래그를 사용 하는 방법에 대 한 자세한 내용은이 항목의 [회귀 변수 모델링 플래그 사용](#bkmk_UseRegressors)섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="59555-127">For more information about the use of this flag, see the section in this topic, [Uses of the REGRESSOR Modeling Flag](#bkmk_UseRegressors).</span></span>  
  
## <a name="viewing-and-changing-modeling-flags"></a><span data-ttu-id="59555-128">모델링 플래그 확인 및 변경</span><span class="sxs-lookup"><span data-stu-id="59555-128">Viewing and Changing Modeling Flags</span></span>  
 <span data-ttu-id="59555-129">데이터 마이닝 디자이너에서 구조 또는 모델의 속성을 확인하여 마이닝 구조 열 또는 모델 열과 관련된 모델링 플래그를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-129">You can view the modeling flags associated with a mining structure column or model column in Data Mining Designer by viewing the properties of the structure or model.</span></span>  
  
 <span data-ttu-id="59555-130">현재 마이닝 구조에 적용된 모델링 플래그를 확인하려면 다음과 같은 쿼리를 사용하여 데이터 마이닝 스키마 행 집합에 대해 구조 열의 모델링 플래그를 반환하는 쿼리를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-130">To determine which modeling flags have been applied to the current mining structure, you can create a query against the data mining schema rowset that returns the modeling flags for just the structure columns, by using a query like the following:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_STRUCTURE_COLUMNS  
WHERE STRUCTURE_NAME = '<structure name>'  
```  
  
 <span data-ttu-id="59555-131">데이터 마이닝 디자이너를 사용하거나 연관된 열의 속성을 편집하여 모델에 사용된 모델링 플래그를 추가하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-131">You can add or change the modeling flags used in a model by using the Data Mining Designer and editing the properties of the associated columns.</span></span> <span data-ttu-id="59555-132">이러한 변경 사항을 적용하려면 구조 또는 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-132">Such changes require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="59555-133">DMX를 사용하거나 AMO 또는 XMLA 스크립트를 사용하여 새 마이닝 구조 또는 마이닝 모델에서 모델링 플래그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-133">You can specify modeling flags in a new mining structure or mining model by using DMX, or by using AMO or XMLA scripts.</span></span> <span data-ttu-id="59555-134">그러나 기존 마이닝 모델과 구조에 사용된 모델링 플래그는 DMX를 사용하여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-134">However, you cannot change the modeling flags used in an existing mining model and structure by using DMX.</span></span> <span data-ttu-id="59555-135">`ALTER MINING STRUCTURE....ADD MINING MODEL`구문을 사용하여 새 마이닝 모델을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-135">You must create a new mining model by using the syntax, `ALTER MINING STRUCTURE....ADD MINING MODEL`.</span></span>  
  
##  <a name="uses-of-the-regressor-modeling-flag"></a><a name="bkmk_UseRegressors"></a><span data-ttu-id="59555-136">회귀 변수 모델링 플래그 사용</span><span class="sxs-lookup"><span data-stu-id="59555-136">Uses of the REGRESSOR Modeling Flag</span></span>  
 <span data-ttu-id="59555-137">열에 REGRESSOR 모델링 플래그를 설정하면 해당 열에 잠재적인 회귀 변수가 포함되어 있다는 사실이 알고리즘에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-137">When you set the REGRESSOR modeling flag on a column, you are indicating to the algorithm that the column contains potential regressors.</span></span> <span data-ttu-id="59555-138">모델에 사용되는 실제 회귀 변수는 알고리즘에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-138">The actual regressors that are used in the model are determined by the algorithm.</span></span> <span data-ttu-id="59555-139">잠재적인 회귀 변수가 예측 가능한 특성을 모델링하지 않는 경우 이를 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-139">A potential regressor can be discarded if it does not model the predictable attribute.</span></span>  
  
 <span data-ttu-id="59555-140">데이터 마이닝 마법사를 사용하여 모델을 작성하는 경우 연속 입력 열은 모두 가능한 회귀 변수로 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-140">When you build a model by using the Data Mining wizard, all continuous input columns are flagged as possible regressors.</span></span> <span data-ttu-id="59555-141">따라서 열에 REGRESSOR 플래그를 명시적으로 설정하지 않은 경우라도 모델에서 열을 회귀 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-141">Therefore, even if you do not explicitly set the REGRESSOR flag on a column, the column might be used as a regressor in the model.</span></span>  
  
 <span data-ttu-id="59555-142">처리된 모델에 실제로 사용된 회귀 변수를 확인하려면 다음 예에 표시된 것과 같이 마이닝 모델의 스키마 행 집합에 대해 쿼리를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="59555-142">You can determine the regressors that were actually used in the processed model by performing a query against the schema rowset for the mining model, as shown in the following example:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_COLUMNS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="59555-143">**참고** 마이닝 모델을 수정한 다음 열의 내용 유형을 Continuous에서 Discrete로 변경할 경우 마이닝 열의 플래그를 수동으로 변경한 다음 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-143">**Note** If you modify a mining model and change the content type of a column from continuous to discrete, you must manually change the flag on the mining column and then reprocess the model.</span></span>  
  
### <a name="regressors-in-linear-regression-models"></a><span data-ttu-id="59555-144">선형 회귀 모델의 회귀 변수</span><span class="sxs-lookup"><span data-stu-id="59555-144">Regressors in Linear Regression Models</span></span>  
 <span data-ttu-id="59555-145">선형 회귀 모델은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-145">Linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="59555-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 선형 회귀 알고리즘을 사용하지 않는 경우라도 연속 특성에 대한 회귀를 나타내는 트리나 노드가 의사 결정 트리에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-146">Even if you do not use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, any decision tree model can contain a tree or nodes that represents a regression on a continuous attribute.</span></span>  
  
 <span data-ttu-id="59555-147">따라서 이러한 모델에서는 연속 열이 회귀 변수를 나타내도록 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-147">Therefore, in these models you do not need to specify that a continuous column represents a regressor.</span></span> <span data-ttu-id="59555-148">열에 REGRESSOR 플래그를 설정하지 않더라도 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 알고리즘은 의미 있는 패턴을 포함하는 영역으로 데이터 세트를 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-148">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm will partition the dataset into regions with meaningful patterns even if you do not set the REGRESSOR flag on the column.</span></span> <span data-ttu-id="59555-149">단, 모델링 플래그를 설정할 때 알고리즘이 트리의 노드에 패턴을 맞추기 위해 다음 형식의 회귀 수식을 찾으려고 한다는 것이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="59555-149">The difference is that when you set the modeling flag, the algorithm will try to find regression equations of the following form to fit the patterns in the nodes of  the tree.</span></span>  
  
 <span data-ttu-id="59555-150">a\*C1 + b\*C2 + ...</span><span class="sxs-lookup"><span data-stu-id="59555-150">a\*C1 + b\*C2 + ...</span></span>  
  
 <span data-ttu-id="59555-151">그런 다음 잉여에 대한 합계가 계산되며 편차가 너무 클 경우 트리에서 강제로 분할이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-151">Then, the sum of the residuals is calculated, and if the deviation is too great, a split is forced in the tree.</span></span>  
  
 <span data-ttu-id="59555-152">예를 들어 **Income** 을 특성으로 사용하여 고객의 구매 행동을 예측하며 열에 REGRESSOR 모델링 플래그를 설정하는 경우 알고리즘은 먼저 표준 회귀 수식을 사용하여 **Income** 값을 맞추려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-152">For example, if you are predicting customer purchasing behavior using **Income** as an attribute, and set the REGRESSOR modeling flag on the column, the algorithm would first try to fit the **Income** values by using a standard regression formula.</span></span> <span data-ttu-id="59555-153">편차가 너무 클 경우 회귀 수식이 중단되고 다른 특성에 대해 트리가 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="59555-153">If the deviation is too great, the regression formula is abandoned and the tree would be split on some other attribute.</span></span> <span data-ttu-id="59555-154">분할 후 의사 결정 트리 알고리즘은 먼저 각 분기에서 Income에 대한 회귀 변수를 맞추려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="59555-154">The decision tree algorithm would then try fit a regressor for income in each of the branches after the split.</span></span>  
  
 <span data-ttu-id="59555-155">FORCE_REGRESSOR 매개 변수를 사용하여 알고리즘이 항상 특정 회귀 변수를 사용하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-155">You can use the FORCE_REGRESSOR parameter to guarantee that the algorithm will use a particular regressor.</span></span> <span data-ttu-id="59555-156">이 매개 변수는 의사 결정 트리 알고리즘과 선형 회귀 알고리즘에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59555-156">This parameter can be used with the Decision Trees algorithm and Linear Regression algorithm.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="59555-157">관련 작업</span><span class="sxs-lookup"><span data-stu-id="59555-157">Related Tasks</span></span>  
 <span data-ttu-id="59555-158">모델링 플래그 사용에 대해 자세히 알아보려면 다음 링크를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="59555-158">Use the following links to learn more about using modeling flags.</span></span>  
  
|<span data-ttu-id="59555-159">Task</span><span class="sxs-lookup"><span data-stu-id="59555-159">Task</span></span>|<span data-ttu-id="59555-160">항목</span><span class="sxs-lookup"><span data-stu-id="59555-160">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="59555-161">데이터 마이닝 디자이너를 사용하여 모델링 플래그 편집</span><span class="sxs-lookup"><span data-stu-id="59555-161">Edit modeling flags by using the Data Mining Designer</span></span>|[<span data-ttu-id="59555-162">모델링 플래그 확인 또는 변경&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="59555-162">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="59555-163">가능성이 높은 회귀 변수를 권장하기 위해 알고리즘에 대한 힌트 지정</span><span class="sxs-lookup"><span data-stu-id="59555-163">Specify a hint to the algorithm to recommend likely regressors</span></span>|[<span data-ttu-id="59555-164">모델에서 회귀 변수로 사용할 열 지정</span><span class="sxs-lookup"><span data-stu-id="59555-164">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)|  
|<span data-ttu-id="59555-165">특정 알고리즘에서 지원하는 모델링 플래그 확인(각 알고리즘 참조 항목의 모델링 플래그 섹션 참조)</span><span class="sxs-lookup"><span data-stu-id="59555-165">See the modeling flags supported by specific algorithms (in the Modeling Flags section for each algorithm reference topic)</span></span>|[<span data-ttu-id="59555-166">데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="59555-166">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)|  
|<span data-ttu-id="59555-167">마이닝 구조 열과 각 열에 설정할 수 있는 속성에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="59555-167">Learn more about mining structure columns and the properties that you can set on them</span></span>|[<span data-ttu-id="59555-168">마이닝 구조 열</span><span class="sxs-lookup"><span data-stu-id="59555-168">Mining Structure Columns</span></span>](mining-structure-columns.md)|  
|<span data-ttu-id="59555-169">마이닝 모델 열과 모델 수준에서 적용할 수 있는 모델링 플래그에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="59555-169">Learn about mining model columns and modeling flags that can be applied at the model level</span></span>|[<span data-ttu-id="59555-170">마이닝 모델 열</span><span class="sxs-lookup"><span data-stu-id="59555-170">Mining Model Columns</span></span>](mining-model-columns.md)|  
|<span data-ttu-id="59555-171">DMX 문에서 모델링 플래그 작업에 사용되는 구문 확인</span><span class="sxs-lookup"><span data-stu-id="59555-171">See syntax for  working with modeling  flags in DMX statements</span></span>|[<span data-ttu-id="59555-172">모델링 플래그&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="59555-172">Modeling Flags &#40;DMX&#41;</span></span>](/sql/dmx/modeling-flags-dmx)|  
|<span data-ttu-id="59555-173">누락된 값 및 이러한 값의 작업 방법 이해</span><span class="sxs-lookup"><span data-stu-id="59555-173">Understand missing values and how to work with  them</span></span>|[<span data-ttu-id="59555-174">누락 값&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="59555-174">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)|  
|<span data-ttu-id="59555-175">모델 및 구조 관리와 사용법 속성 설정에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="59555-175">Learn about managing models and structures and setting usage properties</span></span>|[<span data-ttu-id="59555-176">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="59555-176">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)|  
  
  
