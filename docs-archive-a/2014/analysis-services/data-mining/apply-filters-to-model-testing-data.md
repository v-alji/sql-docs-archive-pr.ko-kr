---
title: 모델 테스트 데이터에 필터 적용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input row filtering [SQL Server]
- filtering input rows [Analysis Services]
- Mining Accuracy Chart [Analysis Services], filtering input rows
ms.assetid: 9ccc9a23-5597-4b35-a05f-2fc8eb885147
author: minewiskan
ms.author: owend
ms.openlocfilehash: d1fd2b643ae4f7d831cab980ca45b7d43d8b58f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646728"
---
# <a name="apply-filters-to-model-testing-data"></a><span data-ttu-id="dc22f-102">모델 테스트 데이터에 필터 적용</span><span class="sxs-lookup"><span data-stu-id="dc22f-102">Apply Filters to Model Testing Data</span></span>
  <span data-ttu-id="dc22f-103">모델을 테스트하는 데 사용할 외부 데이터 원본을 지정할 경우 필요에 따라 입력 데이터를 제한하기 위한 필터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-103">When you specify an external data source to use in testing a model, you can optionally apply a filter to restrict the input data.</span></span> <span data-ttu-id="dc22f-104">예를 들어 특별히 특정 수입 범위 내의 고객에 대해 예측하기 위해 모델을 테스트하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-104">For example, you might want to test the model specifically for predictions on customers in a certain income range.</span></span>  
  
 <span data-ttu-id="dc22f-105">예를 들어 AdventureWorks 타겟 메일링 시나리오에서 테스트 데이터를 포함 하는 테이블인 ProspectiveBuyer에 다음과 같은 필터 식을 만들고 테스트 사례를 수입 범위로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-105">For example, in the AdventureWorks targeted mailing scenario, you can create a filter expression like the following one on ProspectiveBuyer, which is the table that contains the testing data, and restrict testing cases by income range:</span></span>  
  
 `[YearlyIncome] = '50000'`  
  
 <span data-ttu-id="dc22f-106">필터의 동작은 모델 학습 데이터를 필터링하는지 테스트 데이터 집합을 필터링하는지에 따라 크게 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-106">The behavior of filters is slightly different, depending on whether you are filtering model training data or a testing data set:</span></span>  
  
-   <span data-ttu-id="dc22f-107">테스트 데이터 집합에 대한 필터를 정의할 때는 들어오는 데이터에 대한 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-107">When you define a filter on a testing data set, you create a WHERE clause on the incoming data.</span></span> <span data-ttu-id="dc22f-108">모델을 평가하는 데 사용되는 입력 데이터 집합을 필터링할 경우 필터 식이 Transact-SQL 문으로 변환되고 차트 생성 시 입력 테이블에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-108">If you are filtering an input data set used for evaluating a model, the filter expression is translated to a Transact-SQL statement and applied to the input table when the chart is created.</span></span> <span data-ttu-id="dc22f-109">따라서 테스트 사례 수가 크게 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-109">As a result, the number of test cases can be greatly reduced.</span></span>  
  
-   <span data-ttu-id="dc22f-110">마이닝 모델에 필터를 적용할 때는 만드는 필터 식이 DMX(Data Mining Extensions) 문으로 변환되고 개별 모델에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-110">When you apply a filter to a mining model, the filter expression that you create is translated to a Data Mining Extensions (DMX) statement, and applied to the individual model.</span></span> <span data-ttu-id="dc22f-111">따라서 모델에 필터를 적용할 때는 모델 학습에 원래 데이터의 하위 집합만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-111">Therefore, when you apply a filter to a model, only a subset of the original data is used to train the model.</span></span> <span data-ttu-id="dc22f-112">이 경우 모델이 특정 데이터 집합으로 조정되도록 한 가지 조건 집합을 사용하여 학습 모델을 필터링한 다음 다른 조건 집합을 사용하여 모델을 테스트하면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-112">This can cause problems if you filter the training model with one set of criteria, so that the model is tuned to a certain set of data, and then test the model with another set of criteria.</span></span>  
  
-   <span data-ttu-id="dc22f-113">구조를 만들 때 테스트 데이터 집합을 정의한 경우 학습에 사용되는 모델 사례에는 마이닝 구조 학습 집합에 있으며 **또한** 필터 조건에 맞는 사례만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-113">If you defined a testing data set when you created the structure, the model cases used for training include only those cases that are in the mining structure training set **and** which meet the conditions of the filter.</span></span> <span data-ttu-id="dc22f-114">따라서 모델을 테스트할 때 **마이닝 모델 테스트 사례 사용**옵션을 선택하면 테스트 사례에는 마이닝 구조 테스트 집합에 있으며 필터 조건에 맞는 사례만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-114">Thus, when you are testing a model and select the option **Use mining model test cases**, the testing cases will include only the cases that are in the mining structure test set and which meet the conditions of the filter.</span></span> <span data-ttu-id="dc22f-115">그러나 홀드아웃 데이터 집합을 정의하지 않은 경우 테스트에 사용되는 모델 사례에는 필터 조건에 맞는 데이터 집합의 모든 사례가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-115">However, if you did not define a holdout data set, the model cases used for testing include all the cases in the data set that meet the filter conditions</span></span>  
  
-   <span data-ttu-id="dc22f-116">모델에 적용하는 필터 조건은 모델 사례에 대한 드릴스루 쿼리에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-116">Filter conditions that you apply on a model also affect drillthrough queries on the model cases.</span></span>  
  
 <span data-ttu-id="dc22f-117">요약하면, 여러 모델을 테스트할 때는 모든 모델이 동일한 마이닝 구조를 기반으로 하더라도 모델에 따라 학습 및 테스트에 다른 데이터 하위 집합이 사용될 수 있다는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-117">In summary, when you test multiple models, even if all the models are based on the same mining structure, you must be aware that the models potentially use different subsets of data for training and testing.</span></span> <span data-ttu-id="dc22f-118">이 경우 정확도 차트에 다음과 같은 영향이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-118">This can have the following effects on accuracy charts:</span></span>  
  
-   <span data-ttu-id="dc22f-119">테스트 집합의 총 사례 수는 테스트하는 모델에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-119">The total number of cases in the testing sets can vary among the models being tested.</span></span>  
  
-   <span data-ttu-id="dc22f-120">모델에서 서로 다른 학습 데이터 또는 테스트 데이터의 하위 집합이 사용되는 경우 차트에서 각 모델의 백분율이 정렬되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-120">The percentages for each model may not align in the chart, if the models use different subsets of training data or testing data.</span></span>  
  
 <span data-ttu-id="dc22f-121">결과에 영향을 줄 수 있는 미리 정의된 필터가 모델에 포함되어 있는지 확인하려면 **속성** 창에서 **Filter** 속성을 확인하거나 데이터 마이닝 스키마 행 집합을 사용하여 모델을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-121">To determine whether a model contains a predefined filter that might affect results, you can look for the **Filter** property in the **Property** pane, or you can query the model by using the data mining schema rowsets.</span></span> <span data-ttu-id="dc22f-122">예를 들어 다음 쿼리는 지정된 모델에 대한 필터 텍스트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-122">For example, the following query returns the filter text for the specified model:</span></span>  
  
 `SELECT [FILTER] FROM $system.DMSCHEMA_MINING_MODELS WHERE MODEL_NAME = 'name of model'`  
  
> [!WARNING]  
>  <span data-ttu-id="dc22f-123">기존 마이닝 모델에서 필터를 제거하거나 필터 조건을 변경하려는 경우에는 마이닝 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-123">If you want to remove the filter from an existing mining model, or change the filter conditions, you must reprocess the mining model.</span></span>  
  
 <span data-ttu-id="dc22f-124">적용할 수 있는 필터 종류에 대한 자세한 내용과 필터 식이 계산되는 방법은 [모델 필터 구문 및 예&#40;Analysis Services - 데이터 마이닝&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc22f-124">For more information about the kinds of filters you can apply, and how filter expressions are evaluated, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
### <a name="create-a-filter-on-external-testing-data"></a><span data-ttu-id="dc22f-125">외부 테스트 데이터에 대한 필터 만들기</span><span class="sxs-lookup"><span data-stu-id="dc22f-125">Create a filter on external testing data</span></span>  
  
1.  <span data-ttu-id="dc22f-126">테스트할 모델이 포함된 마이닝 구조를 두 번 클릭하여 데이터 마이닝 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-126">Double-click the mining structure that contains the model you want to test, to open Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="dc22f-127">**마이닝 정확도 차트** 탭을 선택한 다음 **입력 선택** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-127">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="dc22f-128">**입력 선택** 탭의 **정확도 차트에 사용할 데이터 집합을 선택하십시오.** 에서 **다른 데이터 집합 지정**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-128">On the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="dc22f-129">찾아보기 단추 **(...)** 를 클릭 하 여 대화 상자를 열고 외부 데이터 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-129">Click the browse button **(...)** to open a dialog box and choose the external data set.</span></span>  
  
5.  <span data-ttu-id="dc22f-130">사례 테이블을 선택하고, 필요한 경우 중첩된 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-130">Choose the case table, and add a nested table if necessary.</span></span> <span data-ttu-id="dc22f-131">필요한 경우 모델의 열을 외부 데이터 집합의 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-131">Map columns in the model to columns in the external data set as necessary.</span></span> <span data-ttu-id="dc22f-132">**열 매핑 지정** 대화 상자를 닫아 원본 테이블 정의를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-132">Close the **Specify Column Mapping** dialog box to save the source table definition.</span></span>  
  
6.  <span data-ttu-id="dc22f-133">**필터 편집기 열기** 를 클릭하여 데이터 집합에 대한 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-133">Click **Open Filter Editor** to define a filter for the data set.</span></span>  
  
     <span data-ttu-id="dc22f-134">**데이터 집합 필터** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-134">The **Data Set Filter** dialog box opens.</span></span> <span data-ttu-id="dc22f-135">구조에 중첩 테이블이 포함된 경우 두 부분으로 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-135">If the structure contains a nested table, you can create a filter in two parts.</span></span> <span data-ttu-id="dc22f-136">먼저 **데이터 집합 필터** 대화 상자를 사용하여 사례 테이블에 대한 조건을 설정한 다음 **필터** 대화 상자를 사용하여 중첩 행에 대한 조건을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-136">First, set conditions on the case table by using the **Data Set Filter** dialog box, and then set conditions on the nested rows by using the **Filter** dialog box.</span></span>  
  
7.  <span data-ttu-id="dc22f-137">**데이터 집합 필터** 대화 상자에서 **마이닝 구조 열**아래에 있는 표의 맨 위 행을 클릭하고 목록에서 테이블 또는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-137">In the **Data Set Filter** dialog box, click the top row in the grid, under **Mining Structure Column**, and select a table or column from the list.</span></span>  
  
     <span data-ttu-id="dc22f-138">데이터 원본 뷰에 여러 테이블이나 중첩 테이블이 포함된 경우에는 먼저 테이블 이름을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-138">If the data source view contains multiple tables, or a nested table, you must first select the table name.</span></span> <span data-ttu-id="dc22f-139">또는 사례 테이블에서 열을 직접 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-139">Otherwise, you can select columns from the case table directly.</span></span>  
  
     <span data-ttu-id="dc22f-140">필터링할 각 열에 대해 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-140">Add a new row for each column that you want to filter.</span></span>  
  
8.  <span data-ttu-id="dc22f-141">**연산자**및 **값** 열을 사용하여 열이 필터링되는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-141">Use **Operator**, and **Value** columns to define how the column is filtered.</span></span>  
  
     <span data-ttu-id="dc22f-142">**참고** 따옴표를 사용하지 않고 값을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc22f-142">**Note** Type values without using quotation marks.</span></span>  
  
9. <span data-ttu-id="dc22f-143">**및/또는** 입력란을 클릭하고 논리 연산자를 선택하여 여러 조건이 결합되는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-143">Click the **And/Or** text box and select a logical operator to define how multiple conditions are combine.</span></span>  
  
10. <span data-ttu-id="dc22f-144">필요에 따라 **값** 텍스트 상자의 오른쪽에 있는 찾아보기 단추 **(...)** 를 클릭 하 여 **필터** 대화 상자를 열고 중첩 테이블 또는 개별 사례 테이블 열에 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-144">Optionally, click the browse button **(...)** at the right of the **Value** text box to open the **Filter** dialog box and set conditions on the nested table or on the individual case table columns.</span></span>  
  
11. <span data-ttu-id="dc22f-145">**식** 창의 텍스트를 읽어 전체 필터 조건이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-145">Verify that the completed filter conditions are correct by viewing the text in the **Expression** pane.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="dc22f-146">필터 조건은 정확도 차트를 만들 때 데이터 원본에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc22f-146">The filter condition is applied to the data source when you create the accuracy chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc22f-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc22f-147">See Also</span></span>  
 <span data-ttu-id="dc22f-148">[모델 테스트 데이터 선택 및 매핑](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="dc22f-148">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 <span data-ttu-id="dc22f-149">[정확도 차트에 대 한 입력으로 중첩 테이블 데이터 사용](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span><span class="sxs-lookup"><span data-stu-id="dc22f-149">[Using Nested Table Data as an Input for an Accuracy Chart](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span></span>  
 [<span data-ttu-id="dc22f-150">정확도 차트 유형 선택 및 차트 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="dc22f-150">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
