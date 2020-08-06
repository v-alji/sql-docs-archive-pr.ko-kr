---
title: 선형 회귀 모델 쿼리 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02d4b7309d7b5ea3d6295089f0fb2e778b1c9b4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660775"
---
# <a name="linear-regression-model-query-examples"></a><span data-ttu-id="de38f-102">선형 회귀 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="de38f-102">Linear Regression Model Query Examples</span></span>
  <span data-ttu-id="de38f-103">데이터 마이닝 모델에 대한 쿼리를 만들 때 분석 중에 발견된 패턴에 대한 세부 정보를 제공하는 내용 쿼리를 만들거나, 모델의 패턴을 사용하여 새 데이터에 대한 예측을 수행하는 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="de38f-104">예를 들어 내용 쿼리는 회귀 수식에 대한 추가 정보를 제공하지만 예측 쿼리는 새 데이터 요소가 모델에 맞는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-104">For example, a content query might provide additional details about the regression formula, while a prediction query might tell you if a new data point fits the model.</span></span> <span data-ttu-id="de38f-105">쿼리를 사용하여 모델에 대한 메타데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="de38f-106">이 섹션에서는 Microsoft 선형 회귀 알고리즘을 기반으로 하는 모델에 대해 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-106">This section explains how to create queries for models that are based on the Microsoft Linear Regression algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de38f-107">선형 회귀는 Microsoft 의사 결정 트리 알고리즘의 특수한 사례를 기반으로 하므로 비슷한 점이 많으며, 예측 가능한 연속 특성을 사용하는 일부 의사 결정 트리 모델에는 회귀 수식이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-107">Because linear regression is based on a special case of the Microsoft Decision Trees algorithm, there are many similarities, and some decision tree models that use continuous predictable attributes can contain regression formulas.</span></span> <span data-ttu-id="de38f-108">자세한 내용은 [Microsoft 의사 결정 트리 알고리즘 기술 참조](microsoft-decision-trees-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de38f-108">For more information, see [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="de38f-109">**내용 쿼리**</span><span class="sxs-lookup"><span data-stu-id="de38f-109">**Content queries**</span></span>  
  
 [<span data-ttu-id="de38f-110">데이터 마이닝 스키마 행 집합을 사용하여 모델에 사용되는 매개 변수 확인</span><span class="sxs-lookup"><span data-stu-id="de38f-110">Using the Data Mining Schema Rowset to determine parameters used for a model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="de38f-111">DMX를 사용하여 모델의 회귀 수식 반환</span><span class="sxs-lookup"><span data-stu-id="de38f-111">Using DMX to return the regression formula for the model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="de38f-112">모델의 계수만 반환</span><span class="sxs-lookup"><span data-stu-id="de38f-112">Returning only the coefficient for the model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="de38f-113">**예측 쿼리**</span><span class="sxs-lookup"><span data-stu-id="de38f-113">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="de38f-114">단일 쿼리를 사용하여 수입 예측</span><span class="sxs-lookup"><span data-stu-id="de38f-114">Predicting income using a singleton query</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="de38f-115">회귀 모델에 예측 함수 사용</span><span class="sxs-lookup"><span data-stu-id="de38f-115">Using prediction functions with a regression model</span></span>](#bkmk_Query5)  
  
##  <a name="finding-information-about-the-linear-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="de38f-116">선형 회귀 모델에 대 한 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="de38f-116">Finding Information about the Linear Regression Model</span></span>  
 <span data-ttu-id="de38f-117">선형 회귀 모델의 구조는 매우 단순하여 마이닝 모델은 데이터를 단일 노드로 나타내고 이 노드는 회귀 수식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-117">The structure of a linear regression model is extremely simple: the mining model represents the data as a single node, which defines the regression formula.</span></span> <span data-ttu-id="de38f-118">자세한 내용은 [로지스틱 회귀 분석 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-logistic-regression-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de38f-118">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 [<span data-ttu-id="de38f-119">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-119">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-determine-parameters-used-for-a-model"></a><a name="bkmk_Query1"></a><span data-ttu-id="de38f-120">예제 쿼리 1: 데이터 마이닝 스키마 행 집합을 사용 하 여 모델에 사용 되는 매개 변수 확인</span><span class="sxs-lookup"><span data-stu-id="de38f-120">Sample Query 1: Using the Data Mining Schema Rowset to Determine Parameters Used for a Model</span></span>  
 <span data-ttu-id="de38f-121">데이터 마이닝 스키마 행 집합을 쿼리하면 모델에 대한 메타데이터를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-121">By querying the data mining schema rowset, you can find metadata about the model.</span></span> <span data-ttu-id="de38f-122">이러한 메타데이터로는 모델이 만들어진 시기, 모델이 마지막으로 처리된 시기, 모델의 기반이 되는 마이닝 구조의 이름, 예측 가능한 특성으로 지정된 열 이름 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-122">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column designated as the predictable attribute.</span></span> <span data-ttu-id="de38f-123">모델을 처음으로 만들 때 사용한 매개 변수를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-123">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 <span data-ttu-id="de38f-124">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="de38f-124">Sample results:</span></span>  
  
|<span data-ttu-id="de38f-125">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de38f-125">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="de38f-126">COMPLEXITY_PENALTY=0.9,</span><span class="sxs-lookup"><span data-stu-id="de38f-126">COMPLEXITY_PENALTY=0.9,</span></span><br /><br /> <span data-ttu-id="de38f-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="de38f-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="de38f-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="de38f-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="de38f-129">MINIMUM_SUPPORT=10,</span><span class="sxs-lookup"><span data-stu-id="de38f-129">MINIMUM_SUPPORT=10,</span></span><br /><br /> <span data-ttu-id="de38f-130">SCORE_METHOD=4,</span><span class="sxs-lookup"><span data-stu-id="de38f-130">SCORE_METHOD=4,</span></span><br /><br /> <span data-ttu-id="de38f-131">SPLIT_METHOD=3,</span><span class="sxs-lookup"><span data-stu-id="de38f-131">SPLIT_METHOD=3,</span></span><br /><br /> <span data-ttu-id="de38f-132">FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="de38f-132">FORCE_REGRESSOR=</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="de38f-133">매개 변수 설정 "`FORCE_REGRESSOR =` "는 FORCE_REGRESSOR 매개 변수의 현재 값이 Null임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-133">The parameter setting, "`FORCE_REGRESSOR =` ", indicates that the current value for the FORCE_REGRESSOR parameter is null.</span></span>  
  
 [<span data-ttu-id="de38f-134">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-134">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-2-retrieving-the-regression-formula-for-the-model"></a><a name="bkmk_Query2"></a><span data-ttu-id="de38f-135">예제 쿼리 2: 모델의 회귀 수식 검색</span><span class="sxs-lookup"><span data-stu-id="de38f-135">Sample Query 2: Retrieving the Regression Formula for the Model</span></span>  
 <span data-ttu-id="de38f-136">다음 쿼리는 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)에서 사용한 타겟 메일링 데이터 원본을 사용하여 작성한 선형 회귀 모델의 마이닝 모델 콘텐츠를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-136">The following query returns the mining model content for a linear regression model that was built by using the same Targeted Mailing data source that was used in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="de38f-137">이 모델은 나이에 따른 고객 수입을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-137">This model predicts customer income based on age.</span></span>  
  
 <span data-ttu-id="de38f-138">이 쿼리는 회귀 수식이 들어 있는 노드의 콘텐츠를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-138">The query returns the contents of the node that contains the regression formula.</span></span> <span data-ttu-id="de38f-139">각 변수 및 계수는 NODE_DISTRIBUTION 중첩 테이블의 개별 행에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-139">Each variable and coefficient is stored in a separate row of the nested NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="de38f-140">전체 회귀 수식을 보려면 [Microsoft 트리 뷰어](browse-a-model-using-the-microsoft-tree-viewer.md)에서 **(All)** 노드를 클릭하고 **마이닝 범례**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-140">If you want to view the complete regression formula, use the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md), click the **(All)** node, and open the **Mining Legend**.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  <span data-ttu-id="de38f-141">`SELECT <column name> from NODE_DISTRIBUTION`과 같은 쿼리를 사용하여 중첩 테이블의 개별 열을 참조하는 경우 **SUPPORT** 또는 **PROBABILITY**등의 일부 열은 대괄호로 묶어 동일한 이름의 예약 키워드와 구별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-141">If you reference individual columns of the nested table by using a query such as `SELECT <column name> from NODE_DISTRIBUTION`, some columns, such as **SUPPORT** or **PROBABILITY**, must be enclosed in brackets to distinguish them from reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="de38f-142">예상 결과:</span><span class="sxs-lookup"><span data-stu-id="de38f-142">Expected results:</span></span>  
  
|<span data-ttu-id="de38f-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="de38f-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="de38f-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="de38f-144">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="de38f-145">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="de38f-145">t.SUPPORT</span></span>|<span data-ttu-id="de38f-146">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="de38f-146">t.PROBABILITY</span></span>|<span data-ttu-id="de38f-147">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="de38f-147">t.VARIANCE</span></span>|<span data-ttu-id="de38f-148">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="de38f-148">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="de38f-149">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="de38f-149">Yearly Income</span></span>|<span data-ttu-id="de38f-150">Missing</span><span class="sxs-lookup"><span data-stu-id="de38f-150">Missing</span></span>|<span data-ttu-id="de38f-151">0</span><span class="sxs-lookup"><span data-stu-id="de38f-151">0</span></span>|<span data-ttu-id="de38f-152">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="de38f-152">0.000457142857142857</span></span>|<span data-ttu-id="de38f-153">0</span><span class="sxs-lookup"><span data-stu-id="de38f-153">0</span></span>|<span data-ttu-id="de38f-154">1</span><span class="sxs-lookup"><span data-stu-id="de38f-154">1</span></span>|  
|<span data-ttu-id="de38f-155">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="de38f-155">Yearly Income</span></span>|<span data-ttu-id="de38f-156">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="de38f-156">57220.8876687257</span></span>|<span data-ttu-id="de38f-157">17484</span><span class="sxs-lookup"><span data-stu-id="de38f-157">17484</span></span>|<span data-ttu-id="de38f-158">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="de38f-158">0.999542857142857</span></span>|<span data-ttu-id="de38f-159">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="de38f-159">1041275619.52776</span></span>|<span data-ttu-id="de38f-160">3</span><span class="sxs-lookup"><span data-stu-id="de38f-160">3</span></span>|  
|<span data-ttu-id="de38f-161">연령</span><span class="sxs-lookup"><span data-stu-id="de38f-161">Age</span></span>|<span data-ttu-id="de38f-162">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="de38f-162">471.687717702463</span></span>|<span data-ttu-id="de38f-163">0</span><span class="sxs-lookup"><span data-stu-id="de38f-163">0</span></span>|<span data-ttu-id="de38f-164">0</span><span class="sxs-lookup"><span data-stu-id="de38f-164">0</span></span>|<span data-ttu-id="de38f-165">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="de38f-165">126.969442359327</span></span>|<span data-ttu-id="de38f-166">7</span><span class="sxs-lookup"><span data-stu-id="de38f-166">7</span></span>|  
|<span data-ttu-id="de38f-167">연령</span><span class="sxs-lookup"><span data-stu-id="de38f-167">Age</span></span>|<span data-ttu-id="de38f-168">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="de38f-168">234.680904692439</span></span>|<span data-ttu-id="de38f-169">0</span><span class="sxs-lookup"><span data-stu-id="de38f-169">0</span></span>|<span data-ttu-id="de38f-170">0</span><span class="sxs-lookup"><span data-stu-id="de38f-170">0</span></span>|<span data-ttu-id="de38f-171">0</span><span class="sxs-lookup"><span data-stu-id="de38f-171">0</span></span>|<span data-ttu-id="de38f-172">8</span><span class="sxs-lookup"><span data-stu-id="de38f-172">8</span></span>|  
|<span data-ttu-id="de38f-173">연령</span><span class="sxs-lookup"><span data-stu-id="de38f-173">Age</span></span>|<span data-ttu-id="de38f-174">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="de38f-174">45.4269617936399</span></span>|<span data-ttu-id="de38f-175">0</span><span class="sxs-lookup"><span data-stu-id="de38f-175">0</span></span>|<span data-ttu-id="de38f-176">0</span><span class="sxs-lookup"><span data-stu-id="de38f-176">0</span></span>|<span data-ttu-id="de38f-177">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="de38f-177">126.969442359327</span></span>|<span data-ttu-id="de38f-178">9</span><span class="sxs-lookup"><span data-stu-id="de38f-178">9</span></span>|  
||<span data-ttu-id="de38f-179">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="de38f-179">35793.5477381267</span></span>|<span data-ttu-id="de38f-180">0</span><span class="sxs-lookup"><span data-stu-id="de38f-180">0</span></span>|<span data-ttu-id="de38f-181">0</span><span class="sxs-lookup"><span data-stu-id="de38f-181">0</span></span>|<span data-ttu-id="de38f-182">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="de38f-182">1012968919.28372</span></span>|<span data-ttu-id="de38f-183">11</span><span class="sxs-lookup"><span data-stu-id="de38f-183">11</span></span>|  
  
 <span data-ttu-id="de38f-184">반면 **마이닝 범례**에서 회귀 수식은 다음과 같이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-184">In comparison, in the **Mining Legend**, the regression formula appears as follows:</span></span>  
  
 <span data-ttu-id="de38f-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span><span class="sxs-lookup"><span data-stu-id="de38f-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span></span>  
  
 <span data-ttu-id="de38f-186">**마이닝 범례**에서는 일부 숫자가 반올림되는 것을 알 수 있지만 NODE_DISTRIBUTION 테이블과 **마이닝 범례** 에 들어 있는 값은 기본적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-186">You can see that in the **Mining Legend**, some numbers are rounded; however, the NODE_DISTRIBUTION table and the **Mining Legend** essentially contain the same values.</span></span>  
  
 <span data-ttu-id="de38f-187">VALUETYPE 열의 값은 각 행에 들어 있는 정보의 종류를 나타내며 이는 결과를 프로그래밍 방식으로 처리할 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-187">The values in the VALUETYPE column tell you what kind of information is contained in each row, which is useful if you are processing the results programmatically.</span></span> <span data-ttu-id="de38f-188">다음 표에서는 선형 회귀 수식에 대해 출력되는 값 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-188">The following table shows the value types that are output for a linear regression formula.</span></span>  
  
|<span data-ttu-id="de38f-189">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="de38f-189">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="de38f-190">1(누락)</span><span class="sxs-lookup"><span data-stu-id="de38f-190">1 (Missing)</span></span>|  
|<span data-ttu-id="de38f-191">3(연속)</span><span class="sxs-lookup"><span data-stu-id="de38f-191">3 (Continuous)</span></span>|  
|<span data-ttu-id="de38f-192">7(계수)</span><span class="sxs-lookup"><span data-stu-id="de38f-192">7 (Coefficient)</span></span>|  
|<span data-ttu-id="de38f-193">8(득점)</span><span class="sxs-lookup"><span data-stu-id="de38f-193">8 (Score Gain)</span></span>|  
|<span data-ttu-id="de38f-194">9(통계)</span><span class="sxs-lookup"><span data-stu-id="de38f-194">9 (Statistics)</span></span>|  
|<span data-ttu-id="de38f-195">7(계수)</span><span class="sxs-lookup"><span data-stu-id="de38f-195">7 (Coefficient)</span></span>|  
|<span data-ttu-id="de38f-196">8(득점)</span><span class="sxs-lookup"><span data-stu-id="de38f-196">8 (Score Gain)</span></span>|  
|<span data-ttu-id="de38f-197">9(통계)</span><span class="sxs-lookup"><span data-stu-id="de38f-197">9 (Statistics)</span></span>|  
|<span data-ttu-id="de38f-198">11(절편)</span><span class="sxs-lookup"><span data-stu-id="de38f-198">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="de38f-199">회귀 모델에 대한 각각의 값 형식의 의미는 [선형 회귀 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de38f-199">For more information about the meaning of each value type for regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="de38f-200">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-200">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-3-returning-only-the-coefficient-for-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="de38f-201">예제 쿼리 3: 모델에 대 한 계수 반환</span><span class="sxs-lookup"><span data-stu-id="de38f-201">Sample Query 3: Returning Only the Coefficient for the Model</span></span>  
 <span data-ttu-id="de38f-202">다음 쿼리와 같이 VALUETYPE 열거형을 사용하면 회귀 수식의 계수만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-202">By using the VALUETYPE enumeration, you can return only the coefficient for the regression equation, as shown in the following query:</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 <span data-ttu-id="de38f-203">이 쿼리는 두 개의 행을 반환합니다. 하나는 마이닝 모델 콘텐츠에서 가져온 것이고 다른 하나는 계수가 들어 있는 중첩 테이블의 행에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-203">This query returns two rows, one from the mining model content, and the row from the nested table that contains the coefficient.</span></span> <span data-ttu-id="de38f-204">계수의 경우 ATTRIBUTE_NAME 열은 항상 비어 있으므로 이 열은 여기에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-204">The ATTRIBUTE_NAME column is not included here because it is always blank for the coefficient.</span></span>  
  
|<span data-ttu-id="de38f-205">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="de38f-205">MODEL_NAME</span></span>|<span data-ttu-id="de38f-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="de38f-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="de38f-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="de38f-207">t.VALUETYPE</span></span>|  
|-----------------|------------------------|-----------------|  
|<span data-ttu-id="de38f-208">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="de38f-208">LR_PredictIncome</span></span>|||  
|<span data-ttu-id="de38f-209">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="de38f-209">LR_PredictIncome</span></span>|<span data-ttu-id="de38f-210">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="de38f-210">35793.5477381267</span></span>|<span data-ttu-id="de38f-211">11</span><span class="sxs-lookup"><span data-stu-id="de38f-211">11</span></span>|  
  
 [<span data-ttu-id="de38f-212">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-212">Return to Top</span></span>](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a><span data-ttu-id="de38f-213">선형 회귀 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="de38f-213">Making Predictions from a Linear Regression Model</span></span>  
 <span data-ttu-id="de38f-214">데이터 마이닝 디자이너의 마이닝 모델 예측 탭에서 선형 회귀 모델에 대한 예측 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-214">You can build prediction queries on linear regression models by using the Mining Model Prediction tab in Data Mining Designer.</span></span> <span data-ttu-id="de38f-215">예측 쿼리 작성기는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 와 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-215">The prediction query builder is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de38f-216">Excel용 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터 마이닝 추가 기능이나 Excel용 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 데이터 마이닝 추가 기능을 사용하여 회귀 모델에 대한 쿼리를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-216">You can also create queries on regression models by using the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Data Mining Add-ins for Excel or the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Data Mining Add-ins for Excel.</span></span> <span data-ttu-id="de38f-217">Excel용 데이터 마이닝 추가 기능은 회귀 모델을 만들지 않지만 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 인스턴스에 저장된 마이닝 모델을 찾아보고 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-217">Even though the Data Mining Add-ins for Excel do not create regression models, you can browse and query any mining model that is stored on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="de38f-218">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-218">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-4-predicting-income-using-a-singleton-query"></a><a name="bkmk_Query4"></a><span data-ttu-id="de38f-219">예제 쿼리 4: 단일 쿼리를 사용 하 여 수입 예측</span><span class="sxs-lookup"><span data-stu-id="de38f-219">Sample Query 4: Predicting Income using a Singleton Query</span></span>  
 <span data-ttu-id="de38f-220">회귀 모델에서 단일 쿼리를 만드는 가장 쉬운 방법은 **단일 쿼리 입력** 대화 상자를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-220">The easiest way to create a single query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="de38f-221">예를 들어 적절 한 회귀 모델을 선택 하 고 **단일 쿼리**를 선택한 다음 `20` **Age**값으로를 입력 하 여 다음과 같은 DMX 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-221">For example, you can build the following DMX query by selecting the appropriate regression model, choosing **Singleton Query**, and then typing `20` as the value for **Age**.</span></span>  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="de38f-222">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="de38f-222">Sample results:</span></span>  
  
|<span data-ttu-id="de38f-223">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="de38f-223">Yearly Income</span></span>|  
|-------------------|  
|<span data-ttu-id="de38f-224">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="de38f-224">45227.302092176</span></span>|  
  
 [<span data-ttu-id="de38f-225">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-225">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-5-using-prediction-functions-with-a-regression-model"></a><a name="bkmk_Query5"></a><span data-ttu-id="de38f-226">예제 쿼리 5: 회귀 모델에 예측 함수 사용</span><span class="sxs-lookup"><span data-stu-id="de38f-226">Sample Query 5: Using Prediction Functions with a Regression Model</span></span>  
 <span data-ttu-id="de38f-227">선형 회귀 모델에 여러 표준 예측 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-227">You can use many of the standard prediction functions with linear regression models.</span></span> <span data-ttu-id="de38f-228">다음 예에서는 예측 쿼리 결과에 기술 통계를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-228">The following example illustrates how to add some descriptive statistics to the prediction query results.</span></span> <span data-ttu-id="de38f-229">이러한 결과에서 이 모델의 평균과 상당한 편차가 있다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-229">From these results, you can see that there is considerable deviation from the mean for this model.</span></span>  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="de38f-230">예제 결과:</span><span class="sxs-lookup"><span data-stu-id="de38f-230">Sample results:</span></span>  
  
|<span data-ttu-id="de38f-231">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="de38f-231">Yearly Income</span></span>|<span data-ttu-id="de38f-232">StDev1</span><span class="sxs-lookup"><span data-stu-id="de38f-232">StDev1</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="de38f-233">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="de38f-233">45227.302092176</span></span>|<span data-ttu-id="de38f-234">31827.1726561396</span><span class="sxs-lookup"><span data-stu-id="de38f-234">31827.1726561396</span></span>|  
  
 [<span data-ttu-id="de38f-235">맨 위로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de38f-235">Return to Top</span></span>](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="de38f-236">예측 함수 목록</span><span class="sxs-lookup"><span data-stu-id="de38f-236">List of Prediction Functions</span></span>  
 <span data-ttu-id="de38f-237">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘은 공통 함수 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-237">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="de38f-238">그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 선형 회귀 알고리즘은 다음 표에 나열된 추가 함수도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-238">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de38f-239">예측 함수</span><span class="sxs-lookup"><span data-stu-id="de38f-239">Prediction Function</span></span>|<span data-ttu-id="de38f-240">사용</span><span class="sxs-lookup"><span data-stu-id="de38f-240">Usage</span></span>|  
|[<span data-ttu-id="de38f-241">IsDescendant&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-241">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="de38f-242">한 노드가 모델에서 다른 노드의 자식인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-242">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="de38f-243">IsInNode&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-243">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="de38f-244">지정한 노드에 현재 사례가 포함되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-244">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="de38f-245">PredictHistogram&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-245">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="de38f-246">지정한 열에 대한 예측 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-246">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="de38f-247">PredictNodeId&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-247">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="de38f-248">각 사례에 대한 Node_ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-248">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="de38f-249">PredictStdev&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-249">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="de38f-250">예측 값의 표준 편차를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-250">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="de38f-251">PredictSupport&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-251">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="de38f-252">지정한 상태에 대한 지원 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-252">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="de38f-253">PredictVariance&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-253">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="de38f-254">지정한 열의 분산을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="de38f-254">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="de38f-255">모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 알고리즘에 공통적인 함수 목록에 대해서는 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de38f-255">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span> <span data-ttu-id="de38f-256">이러한 함수를 사용하는 방법은 [DMX&#40;Data Mining Extensions&#41; 함수 참조](/sql/dmx/data-mining-extensions-dmx-function-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de38f-256">For more information about how to use these functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de38f-257">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de38f-257">See Also</span></span>  
 <span data-ttu-id="de38f-258">[Microsoft 선형 회귀 알고리즘](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="de38f-258">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="de38f-259">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="de38f-259">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="de38f-260">[Microsoft 선형 회귀 알고리즘 기술 참조](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="de38f-260">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="de38f-261">선형 회귀 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="de38f-261">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
