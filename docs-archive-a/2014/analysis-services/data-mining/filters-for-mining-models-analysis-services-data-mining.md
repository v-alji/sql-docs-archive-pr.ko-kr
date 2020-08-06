---
title: 마이닝 모델에 대 한 필터 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4e2c82c977f734948e107773e439ca154f6cfdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647318"
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a><span data-ttu-id="30df2-102">마이닝 모델에 대한 필터(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="30df2-102">Filters for Mining Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="30df2-103">데이터 기반 모델 필터링을 사용하면 마이닝 구조에서 데이터의 하위 집합을 사용하는 마이닝 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-103">Data-based model filtering helps you create mining models that use subsets of data in a mining structure.</span></span> <span data-ttu-id="30df2-104">포괄적인 데이터 원본 뷰를 기반으로 단일 마이닝 구조를 만들 수 있으므로 필터링을 사용하면 마이닝 구조 및 데이터 원본을 유연하게 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-104">Filtering gives you flexibility when you design your mining structures and data sources, because you can create a single mining structure, based on a comprehensive data source view.</span></span> <span data-ttu-id="30df2-105">그런 다음 데이터의 각 하위 집합에 대해 서로 다른 구조 및 관련 모델을 작성하는 대신 다양한 모델의 학습 및 테스트에 해당 데이터의 일부만 사용하기 위한 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-105">You can then create filters to use only a part of that data for training and testing a variety of models, instead of building a different structure and related model for each subset of data.</span></span>  
  
 <span data-ttu-id="30df2-106">예를 들어 Customers 테이블 및 관련 테이블에 대한 데이터 원본 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-106">For example, you define the data source view on the Customers table and related tables.</span></span> <span data-ttu-id="30df2-107">그런 다음 필요한 모든 필드를 포함하는 단일 마이닝 구조를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-107">Next, you define a single mining structure that includes all the fields you need.</span></span> <span data-ttu-id="30df2-108">마지막으로 Region과 같은 특정 고객 특성으로 필터링되는 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-108">Finally, you create a model that is filtered on a particular customer attribute, such as Region.</span></span> <span data-ttu-id="30df2-109">그러면 해당 모델의 복사본을 쉽게 만들고, 필터 조건만 변경하여 다른 지역을 기반으로 하는 새 모델을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-109">You can then easily make a copy of that model, and change just the filter condition to generate a new model based on a different region.</span></span>  
  
 <span data-ttu-id="30df2-110">이 기능이 유용할 수 있는 일부 실제 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-110">Some real-life scenarios where you might benefit from this feature include the following:</span></span>  
  
-   <span data-ttu-id="30df2-111">성별, 지역 등과 같은 불연속 값에 대한 별도의 모델 만들기.</span><span class="sxs-lookup"><span data-stu-id="30df2-111">Creating separate models for discrete values such as gender, regions, and so forth.</span></span> <span data-ttu-id="30df2-112">예를 들어 모든 고객에 대한 단일 데이터 원본에서 판매 데이터를 가져온 경우에도 의류점에서는 고객 인구 통계를 사용하여 성별에 따른 별도의 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-112">For example, a clothing store might use customer demographics to build separate models by gender, even though the sales data comes from a single data source for all customers.</span></span>  
  
-   <span data-ttu-id="30df2-113">20-30세, 20-40세, 20-25세 연령과 같이 동일한 데이터에 대한 여러 그룹화를 만든 다음 테스트하여 모델 시험</span><span class="sxs-lookup"><span data-stu-id="30df2-113">Experimenting with models by creating and then testing multiple groupings of the same data, such as ages 20-30 vs. ages 20-40 vs. ages 20-25.</span></span>  
  
-   <span data-ttu-id="30df2-114">고객이 특정 항목을 두 개 이상 구매한 경우에만 사례가 모델에 포함되도록 요구하는 경우에서와 같이 중첩 테이블 내용에 복잡한 필터 지정</span><span class="sxs-lookup"><span data-stu-id="30df2-114">Specifying complex filters on nested table contents, such as requiring that a case be included in the model only if the customer has purchased at least two of a particular item.</span></span>  
  
 <span data-ttu-id="30df2-115">이 섹션에서는 마이닝 모델에 대해 필터를 작성하고 사용하며 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-115">This section explains how to build, use, and manage filters on mining models.</span></span>  
  
## <a name="creating-model-filters"></a><span data-ttu-id="30df2-116">모델 필터 만들기</span><span class="sxs-lookup"><span data-stu-id="30df2-116">Creating Model Filters</span></span>  
 <span data-ttu-id="30df2-117">다음과 같은 방법으로 필터를 만들고 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-117">You can create and apply filters in the following ways:</span></span>  
  
-   <span data-ttu-id="30df2-118">데이터 마이닝 디자이너의 **마이닝 모델** 탭을 사용하여 필터 편집기 대화 상자를 통해 조건 작성</span><span class="sxs-lookup"><span data-stu-id="30df2-118">Using the **Mining Models** tab in Data Mining Designer to build conditions with the help of filter editor dialog boxes.</span></span>  
  
-   <span data-ttu-id="30df2-119">마이닝 모델의 속성에 필터 식 직접 입력 `Filter`</span><span class="sxs-lookup"><span data-stu-id="30df2-119">Typing a filter expression directly into the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="30df2-120">AMO를 사용하여 모델에 대한 필터 조건을 프로그래밍 방식으로 설정</span><span class="sxs-lookup"><span data-stu-id="30df2-120">Setting filter conditions on a model programmatically, by using AMO.</span></span>  
  
### <a name="creating-model-filters-using-data-mining-designer"></a><span data-ttu-id="30df2-121">데이터 마이닝 디자이너를 사용하여 모델 필터 만들기</span><span class="sxs-lookup"><span data-stu-id="30df2-121">Creating Model Filters using Data Mining Designer</span></span>  
 <span data-ttu-id="30df2-122">데이터 마이닝 디자이너에서 마이닝 모델의 `Filter` 속성을 변경하여 모델을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-122">You filter a model in Data Mining Designer by changing the `Filter` property of the mining model.</span></span> <span data-ttu-id="30df2-123">필터 식을 **속성** 창에 직접 입력하거나 필터 대화 상자를 열어 조건을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-123">You can either type a filter expression directly into the **Properties** pane, or you can open a filter dialog box to build conditions.</span></span>  
  
 <span data-ttu-id="30df2-124">두 개의 필터 대화 상자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-124">There are two filter dialog boxes.</span></span> <span data-ttu-id="30df2-125">첫 번째 대화 상자를 사용하면 사례 테이블에 적용되는 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-125">The first lets you create conditions that are applied to the case table.</span></span> <span data-ttu-id="30df2-126">데이터 원본에 여러 테이블이 포함되어 있는 경우 먼저 테이블을 선택한 다음 열을 선택하고 해당 열에 적용할 연산자와 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-126">If the data source contains multiple tables, first you select a table, and then you select a column and specify operators and conditions that apply to that column.</span></span> <span data-ttu-id="30df2-127">연산자를 사용 하 여 여러 조건을 연결할 수 있습니다 `AND` / `OR` .</span><span class="sxs-lookup"><span data-stu-id="30df2-127">You can link multiple conditions by using `AND`/`OR` operators.</span></span> <span data-ttu-id="30df2-128">값을 정의하는 데 사용할 수 있는 연산자는 열에 불연속 값이 포함되어 있는지, 아니면 연속 값이 포함되어 있는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-128">The operators that are available for defining values depend on whether the column contains discrete or continuous values.</span></span> <span data-ttu-id="30df2-129">예를 들어 연속 값의 경우 `greater than` 및 `less than` 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-129">For example, with continuous values, you can use `greater than` and `less than` operators.</span></span> <span data-ttu-id="30df2-130">그러나 불연속 값의 경우에는 `= (equal to)`, `!= (not equal to)` 및 `is null` 연산자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-130">However, for discrete values, you can only use `= (equal to)`, `!= (not equal to)`, and `is null` operators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30df2-131">`LIKE` 키워드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-131">The `LIKE` keyword is not supported.</span></span> <span data-ttu-id="30df2-132">여러 불연속 특성을 포함하려는 경우 별도의 조건을 만들고 `OR` 연산자를 사용하여 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-132">If you want to include multiple discrete attributes, you must create separate conditions and link them by using the `OR` operator.</span></span>  
  
 <span data-ttu-id="30df2-133">조건이 복잡한 경우 두 번째 필터 대화 상자를 사용하여 한 번에 한 테이블로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-133">If the conditions are complex, you can use the second filter dialog box to work with one table at a time.</span></span> <span data-ttu-id="30df2-134">두 번째 필터 대화 상자를 닫으면 식이 평가된 다음 사례 테이블의 다른 열에 설정된 필터 조건과 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-134">When you close the second filter dialog box, the expression is evaluated and then combined with filter conditions that have been set on other columns in the case table.</span></span>  
  
### <a name="creating-filters-on-nested-tables"></a><span data-ttu-id="30df2-135">중첩 테이블에 필터 만들기</span><span class="sxs-lookup"><span data-stu-id="30df2-135">Creating Filters on Nested Tables</span></span>  
 <span data-ttu-id="30df2-136">데이터 원본 뷰에 중첩 테이블이 포함되어 있는 경우 두 번째 필터 대화 상자를 사용하여 중첩 테이블의 행에 대한 조건을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-136">If the data source view contains nested tables, you can use the second filter dialog box to build conditions on the rows in the nested tables.</span></span>  
  
 <span data-ttu-id="30df2-137">예를 들어 사례 테이블이 고객과 관련되어 있고 중첩 테이블에 고객이 구매한 제품이 표시되는 경우 중첩 테이블 필터에 다음 `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`구문을 사용하여 특정 항목을 구매한 고객에 대한 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-137">For example, if your case table is related to customers, and the nested table shows the products that a customer has purchased, you can create a filter for customers who have purchased particular items by using the following syntax in the nested table filter: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span></span>  
  
 <span data-ttu-id="30df2-138">`EXISTS` 또는 `NOT EXISTS` 키워드 및 하위 쿼리를 사용하여 중첩 테이블에 특정 값이 있는지 여부를 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-138">You can also filter on the existence of a particular value in the nested table by using the `EXISTS` or `NOT EXISTS` keywords and a subquery.</span></span> <span data-ttu-id="30df2-139">이렇게 하면 `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`와 같은 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-139">This lets you create conditions such as `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span></span> <span data-ttu-id="30df2-140">중첩 테이블에 값 `EXISTS SELECT(<subquery>)`을 포함하는 하나 이상의 행이 포함되어 있는 경우 `Water Bottle`는 `true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-140">The `EXISTS SELECT(<subquery>)` returns `true` if the nested table contains at least one row that includes the value, `Water Bottle`.</span></span>  
  
 <span data-ttu-id="30df2-141">사례 테이블에 대한 조건을 중첩 테이블에 대한 조건과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-141">You can combine conditions on the case table with conditions on the nested table.</span></span> <span data-ttu-id="30df2-142">예를 들어 다음 구문에는 사례 테이블에 대한 조건(`Age > 30` ), 중첩 테이블에 대한 하위 쿼리(`EXISTS (SELECT * FROM Products)`) 및 중첩 테이블에 대한 여러 조건(`WHERE ProductName='Milk'  AND Quantity>2`)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-142">For example, the following syntax includes a condition on the case table (`Age > 30` ), a subquery on the nested table (`EXISTS (SELECT * FROM Products)`), and multiple conditions on the nested table (`WHERE ProductName='Milk'  AND Quantity>2`) ).</span></span>  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity>2) )  
```  
  
 <span data-ttu-id="30df2-143">필터 작성이 완료되면 필터 텍스트가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 평가되고 DMX 식으로 번역된 다음 모델과 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-143">When you have finished building the filter, the filter text is evaluated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], translated to a DMX expression, and then saved with the model.</span></span>  
  
 <span data-ttu-id="30df2-144">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 필터 대화 상자를 사용하는 방법에 대한 자세한 내용은 [마이닝 모델에 필터 적용](apply-a-filter-to-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30df2-144">For instructions on how to use the filter dialog boxes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
## <a name="managing-mining-model-filters"></a><span data-ttu-id="30df2-145">마이닝 모델 필터 관리</span><span class="sxs-lookup"><span data-stu-id="30df2-145">Managing Mining Model Filters</span></span>  
 <span data-ttu-id="30df2-146">같은 구조를 기반으로 하는 여러 모델을 쉽게 작성할 수 있으므로 데이터 기반 모델 필터링을 사용하면 마이닝 구조 및 마이닝 모델 관리 태스크가 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-146">Data-based model filtering greatly simplifies the task of managing mining structures and mining models, because you can easily create multiple models that are based on the same structure.</span></span> <span data-ttu-id="30df2-147">또한 기존 마이닝 모델의 복사본을 빠르게 만든 다음 필터 조건만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-147">You can also quickly make copies of existing mining models and then change only the filter condition.</span></span> <span data-ttu-id="30df2-148">그러나 필터로 인해 일부 혼란이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-148">However, filters can lead to some confusion.</span></span>  
  
 <span data-ttu-id="30df2-149">다음은 마이닝 모델에서 필터를 관리하고 해석하는 방법에 대한 질문과 대답입니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-149">Here are some frequently asked questions about how to manage and interpret filters on mining models:</span></span>  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a><span data-ttu-id="30df2-150">필터가 사용 중인지 여부를 어떻게 알 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="30df2-150">How can I tell whether a filter is being used?</span></span>  
 <span data-ttu-id="30df2-151">필터가 모델에 적용되어 있는지 여부를 판단하는 방법은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-151">There are multiple ways to determine whether a filter is applied to a model:</span></span>  
  
-   <span data-ttu-id="30df2-152">디자이너에서 **마이닝 모델** 탭을 클릭 하 고 **속성**을 연 다음 `Filter` 마이닝 모델의 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-152">In the designer, click the **Mining Models** tab, open **Properties**, and view the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="30df2-153">DMV, DMSCHEMA_MINING_MODELS는 필터의 텍스트를 포함하는 열을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-153">The DMV, DMSCHEMA_MINING_MODELS, outputs a column that contains the text of the filter.</span></span> <span data-ttu-id="30df2-154">DMV에서 다음 쿼리를 사용하여 모델 이름과 해당 필터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-154">You can use the following query on a DMV to return the names of models and their filters:</span></span>  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   <span data-ttu-id="30df2-155">AMO에서 MiningModel 개체의 Filter 속성 값을 가져오거나 XMLA의 Filter 요소를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-155">You can get the value of the Filter property of the MiningModel object in AMO, or inspect the Filter element in XMLA.</span></span>  
  
 <span data-ttu-id="30df2-156">모델에 대한 명명 규칙을 만들어 필터 내용을 반영할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-156">You might also establish a naming convention for models to reflect the contents of the filter.</span></span> <span data-ttu-id="30df2-157">이렇게 하면 관련 모델을 쉽게 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-157">This can make it easier to tell related models apart.</span></span>  
  
### <a name="how-can-i-save-a-filter"></a><span data-ttu-id="30df2-158">필터를 저장하려면 어떻게 합니까?</span><span class="sxs-lookup"><span data-stu-id="30df2-158">How can I save a filter?</span></span>  
 <span data-ttu-id="30df2-159">필터 식은 연결된 마이닝 모델 또는 중첩 테이블과 함께 저장되는 스크립트로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-159">The filter expression is saved as a script that is stored with the associated mining model or nested table.</span></span> <span data-ttu-id="30df2-160">필터 텍스트를 삭제하는 경우 필터 식을 수동으로 다시 만들어야만 해당 텍스트를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-160">If you delete the filter text, it can only be restored by manually re-creating the filter expression.</span></span> <span data-ttu-id="30df2-161">따라서 복잡한 필터 식을 만드는 경우 필터 텍스트의 백업 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-161">Therefore, if you create complex filter expressions, you should create a backup copy of the filter text.</span></span>  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a><span data-ttu-id="30df2-162">필터에서 효과를 볼 수 없는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="30df2-162">Why can't I see any effects from the filter?</span></span>  
 <span data-ttu-id="30df2-163">필터 식을 변경하거나 추가할 때마다 구조 및 모델을 다시 처리해야 필터 효과를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-163">Whenever you change or add a filter expression, you must reprocess the structure and model before you can view the effects of the filter.</span></span>  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a><span data-ttu-id="30df2-164">예측 쿼리 결과에 필터링된 특성이 나타나는 이유는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="30df2-164">Why do I see filtered attributes in prediction query results?</span></span>  
 <span data-ttu-id="30df2-165">모델에 필터를 적용할 때는 모델 학습에 사용된 선택한 클래스에만 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-165">When you apply a filter to a model, it affects only the selection of cases used for training the model.</span></span> <span data-ttu-id="30df2-166">필터는 모델에 알려진 특성에 영향을 미치지 않고 데이터 원본에 있는 데이터를 변경하거나 압축하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-166">The filter does not affect the attributes known to the model, or change or suppress data that is present in the data source.</span></span> <span data-ttu-id="30df2-167">따라서 모델에 대한 쿼리는 다른 사례 유형에 대한 예측을 반환하고 모델에서 사용한 값의 드롭다운 목록에 필터에서 제외된 특성 값이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-167">As a result, queries against the model can return predictions for other types of cases, and dropdown lists of values used by the model might show attribute values excluded by the filter.</span></span>  
  
 <span data-ttu-id="30df2-168">예를 들어 20-30세 사이의 여성과 관련된 경우만 사용하는 [Bike Buyer] 모델을 학습한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-168">For example, suppose you train the [Bike Buyer] model using only cases involving women aged 20-30.</span></span> <span data-ttu-id="30df2-169">자전거를 구입하는 남성의 확률을 예측하는 예측 쿼리를 여전히 실행하거나 30-40세 사이의 여성의 결과를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-169">You can still run a prediction query that predicts the probability of a man buying a bike, or predict the outcome for a woman aged 30-40.</span></span> <span data-ttu-id="30df2-170">이는 데이터 원본에 있는 특성 및 값이 이론상으로 가능한 내용을 정의하지만 사례는 학습에 사용된 발생 횟수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-170">That is because the attributes and values present in the data source define what is theoretically possible, while the cases define the occurrences used for training.</span></span> <span data-ttu-id="30df2-171">그러나 학습 데이터는 대상 값을 가진 사례를 포함하지 않으므로 이러한 쿼리는 매우 작은 확률을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-171">However, these queries would return very small probabilities, because the training data does not contain any cases with the target values.</span></span>  
  
 <span data-ttu-id="30df2-172">모델에서 특성 값을 완전히 숨기거나 익명화해야 하는 경우 다음과 같은 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-172">If you need to completely hide or anonymize attribute values in the model, there are various options:</span></span>  
  
-   <span data-ttu-id="30df2-173">데이터 원본 뷰 정의의 일부로 또는 관계형 데이터 원본에 있는 수신 데이터를 필터링</span><span class="sxs-lookup"><span data-stu-id="30df2-173">Filter the incoming data as part of the definition of the data source view, or in the relational data source.</span></span>  
  
-   <span data-ttu-id="30df2-174">특성 값을 마스킹 또는 인코딩</span><span class="sxs-lookup"><span data-stu-id="30df2-174">Mask or encode the attribute value.</span></span>  
  
-   <span data-ttu-id="30df2-175">마이닝 구조 정의의 일부로 제외된 값을 범주로 축소</span><span class="sxs-lookup"><span data-stu-id="30df2-175">Collapse excluded values into a category as part of the mining structure definition.</span></span>  
  
## <a name="related-resources"></a><span data-ttu-id="30df2-176">관련 리소스</span><span class="sxs-lookup"><span data-stu-id="30df2-176">Related Resources</span></span>  
 <span data-ttu-id="30df2-177">필터 구문에 대한 자세한 내용 및 필터 식의 예를 보려면 [모델 필터 구문 및 예&#40;Analysis Services - 데이터 마이닝&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md)구문을 사용하여 특정 항목을 구매한 고객에 대한 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30df2-177">For more information about filter syntax, and examples of filter expressions, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="30df2-178">마이닝 모델을 테스트할 때 모델 필터를 사용하는 방법에 대한 자세한 내용은 [정확도 차트 유형 선택 및 차트 옵션 설정](choose-an-accuracy-chart-type-and-set-chart-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30df2-178">For information about how to use model filters when you are testing a mining model, see [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30df2-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30df2-179">See Also</span></span>  
 <span data-ttu-id="30df2-180">[모델 필터 구문 및 예제 &#40;Analysis Services 데이터 마이닝&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="30df2-180">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="30df2-181">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="30df2-181">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
