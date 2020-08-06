---
title: 입력 선택 탭 (마이닝 정확도 차트 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c5e99e5be275dff6e218d172316c612b5ba0c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651401"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a><span data-ttu-id="f1e31-102">입력 선택 탭(마이닝 정확도 차트 뷰)</span><span class="sxs-lookup"><span data-stu-id="f1e31-102">Input Selection Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="f1e31-103">**마이닝 정확도 차트** 디자이너의 **입력 선택** 탭을 사용하여 모델을 테스트하고 정확도 차트를 작성하는 데 사용되는 데이터 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-103">Use the **Input Selection** tab of the **Mining Accuracy Chart** designer to specify the source of the data that is used to test the model and build the accuracy chart.</span></span>  
  
 <span data-ttu-id="f1e31-104">**자세한 내용:** [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="f1e31-104">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1e31-105">옵션</span><span class="sxs-lookup"><span data-stu-id="f1e31-105">Options</span></span>  
 <span data-ttu-id="f1e31-106">**예측 열과 값**  **동기화**</span><span class="sxs-lookup"><span data-stu-id="f1e31-106">**Synchronize Prediction**  **Columns and Values**</span></span>  
 <span data-ttu-id="f1e31-107">표의 예측 가능한 여러 특성을 통합하여 특성의 이름이 달라도 모델을 학습하는 동안 특성이 동일한 예측 가능한 마이닝 구조 열에서 파생되도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-107">Select to coordinate the predictable attributes in the grid so that, even if they have a different name, they are derived from the same predictable mining structure column during model training.</span></span>  
  
 <span data-ttu-id="f1e31-108">**참고** 이 옵션은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-108">**Note** This option is selected by default.</span></span> <span data-ttu-id="f1e31-109">두 마이닝 구조 열이 동일한 기본 관계형 또는 다차원 원본에서 파생되며 이 두 열이 동일한 상태를 포함하거나 동일한 방법으로 불연속화된 경우에만 이 확인란의 선택을 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-109">You should only clear this box for cases in which you know that two mining structure columns derive from the same underlying relational or multi-dimensional source, and that the columns contain the same states or have been discretized in the same way.</span></span>  
  
 <span data-ttu-id="f1e31-110">**리프트 차트에 표시할 예측 가능한 마이닝 모델 열 선택**</span><span class="sxs-lookup"><span data-stu-id="f1e31-110">**Select predictable mining model columns to show in the lift chart**</span></span>  
 <span data-ttu-id="f1e31-111">리프트 차트에 포함될 모델 및 리프트 차트에서 해당 모델이 사용되는 방법을 제어하는 열을 포함하는 표입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-111">A grid that contains columns to control which models are included in the lift chart and how they are used in the lift chart.</span></span>  
  
|<span data-ttu-id="f1e31-112">값</span><span class="sxs-lookup"><span data-stu-id="f1e31-112">Value</span></span>|<span data-ttu-id="f1e31-113">Description</span><span class="sxs-lookup"><span data-stu-id="f1e31-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1e31-114">**표시**</span><span class="sxs-lookup"><span data-stu-id="f1e31-114">**Show**</span></span>|<span data-ttu-id="f1e31-115">마이닝 모델의 예측 가능한 열 중 차트에 표시할 각 열의 이름 옆에 있는 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-115">Select the box next to the name of each predictable column in the mining model that you want to display in the chart.</span></span><br /><br /> <span data-ttu-id="f1e31-116">차트가 너무 복잡해서 보기 어려우면 하나 이상의 열 옆에 있는 상자의 선택을 취소하여 차트를 간단하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-116">If the chart is too complex to view easily, clear the box next to one or more columns to simplify the chart.</span></span><br /><br /> <span data-ttu-id="f1e31-117">참고: 하나 이상의 열을 선택하지 않으면 정확도 차트를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-117">Note: You cannot create an accuracy chart unless at least one column is selected.</span></span>|  
|<span data-ttu-id="f1e31-118">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="f1e31-118">**Mining Model**</span></span>|<span data-ttu-id="f1e31-119">마이닝 구조에 포함된 마이닝 모델을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-119">Lists the mining models that are contained in the mining structure.</span></span>|  
|<span data-ttu-id="f1e31-120">**예측 가능한 열 이름**</span><span class="sxs-lookup"><span data-stu-id="f1e31-120">**Predictable Column Name**</span></span>|<span data-ttu-id="f1e31-121">마이닝 모델에 포함된 예측 가능한 열 중 리프트 차트를 만드는 데 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-121">Select a predictable column that is contained in the mining models that are used to create the lift chart.</span></span>|  
|<span data-ttu-id="f1e31-122">**예측 값**</span><span class="sxs-lookup"><span data-stu-id="f1e31-122">**Predict Value**</span></span>|<span data-ttu-id="f1e31-123">예측 가능한 열의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-123">Select a value for the predictable column.</span></span> <span data-ttu-id="f1e31-124">이 필드를 비워 두면 리프트 차트에서는 예측 가능한 열의 모든 상태에 대한 모델의 성능을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-124">If you leave this blank, the lift chart predicts how well the model performs for all states of the predictable column.</span></span>|  
  
 <span data-ttu-id="f1e31-125">**정확도 차트에 사용할 데이터 집합을 선택하십시오.**</span><span class="sxs-lookup"><span data-stu-id="f1e31-125">**Select data set to be used for Accuracy Chart**</span></span>  
 <span data-ttu-id="f1e31-126">정확도 테스트 데이터를 지정하는 세 가지 옵션을 포함하는 옵션 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-126">An option group that contains three options for specifying accuracy test data.</span></span>  
  
|<span data-ttu-id="f1e31-127">값</span><span class="sxs-lookup"><span data-stu-id="f1e31-127">Value</span></span>|<span data-ttu-id="f1e31-128">Description</span><span class="sxs-lookup"><span data-stu-id="f1e31-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1e31-129">**마이닝 모델 테스트 사례 사용**</span><span class="sxs-lookup"><span data-stu-id="f1e31-129">**Use mining model test cases**</span></span>|<span data-ttu-id="f1e31-130">마이닝 구조를 분할할 때 만든 테스트 집합을 사용하고 모델에 정의된 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-130">Use the testing set that was created when you partitioned the mining structure, and apply the filter that is defined on the model.</span></span> <span data-ttu-id="f1e31-131">모델 필터에 대한 자세한 내용은 [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="f1e31-131">For information about model filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span></span>|  
|<span data-ttu-id="f1e31-132">**마이닝 구조 테스트 사례 사용**</span><span class="sxs-lookup"><span data-stu-id="f1e31-132">**Use mining structure test cases**</span></span>|<span data-ttu-id="f1e31-133">마이닝 구조를 분할할 때 만든 테스트 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-133">Use the testing set that was created when you partitioned the mining structure.</span></span>|  
|<span data-ttu-id="f1e31-134">**다른 데이터 집합 지정**</span><span class="sxs-lookup"><span data-stu-id="f1e31-134">**Specify a different data set**</span></span>|<span data-ttu-id="f1e31-135">기존 데이터 원본 뷰에서 테스트 데이터 집합으로 사용할 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-135">Specify a table from an existing data source view to use as a test data set.</span></span>|  
  
## <a name="filtering-options"></a><span data-ttu-id="f1e31-136">필터링 옵션</span><span class="sxs-lookup"><span data-stu-id="f1e31-136">Filtering Options</span></span>  
 <span data-ttu-id="f1e31-137">**다른 데이터 집합 지정**옵션을 선택하는 경우 데이터 원본 뷰를 정의하고 해당 데이터에 적용할 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-137">If you select the option **Specify a different data set**, you can define a data source view and create filters to apply to that data.</span></span> <span data-ttu-id="f1e31-138">필터를 만들 때는 데이터 원본 뷰에서 테스트 데이터를 반환하는 쿼리에 WHERE 절을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-138">When you create a filter, you are creating a WHERE clause in the query that returns the test data from the data source view.</span></span>  
  
 <span data-ttu-id="f1e31-139">**참고** **입력 선택** 탭을 사용 하 여 마이닝 모델에 필터를 지정할 수 없습니다. 모델 필터를 만들려면 **마이닝 모델** 탭을 클릭 하 고 모델 속성을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-139">**Note** You cannot specify a filter on the mining model by using the **Input Selection** tab. To create a model filter, click the **Mining Models** tab and edit the model properties.</span></span>  
  
 <span data-ttu-id="f1e31-140">마이닝 구조를 만들 때 테스트용 홀드아웃 집합을 만들지 않은 경우 이 옵션을 선택한 다음 원래 데이터 원본 뷰를 테스트 집합으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-140">If you did not create a holdout set for testing when you created the mining structure, you can select this option and then specify the original data source view as a test set.</span></span> <span data-ttu-id="f1e31-141">이 해결 방법을 사용하면 원래 데이터 집합에 필터를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-141">By using  this workaround, you can also set filters on the original data set.</span></span>  
  
 <span data-ttu-id="f1e31-142">**열 매핑 지정**</span><span class="sxs-lookup"><span data-stu-id="f1e31-142">**Specify Column Mapping**</span></span>  
 <span data-ttu-id="f1e31-143">데이터 원본을 선택하고, 사례 테이블과 중첩 테이블을 지정하고, 외부 데이터 열을 마이닝 구조 열에 매핑하는 **열 매핑 지정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-143">Opens the **Specify Column Mapping** dialog box, where you select the data source, specify case and nested tables, and map external data columns to the mining structure columns.</span></span>  
  
 <span data-ttu-id="f1e31-144">자세한 내용은 [열 매핑 지정 대화 상자&#40;마이닝 정확도 차트&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1e31-144">For more information, see [Specify Column Mapping Dialog Box &#40;Mining Accuracy Chart&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).</span></span>  
  
 <span data-ttu-id="f1e31-145">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="f1e31-145">**Filter Expression**</span></span>  
 <span data-ttu-id="f1e31-146">필터 편집기를 사용하여 작성하는 필터 조건을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-146">Displays the filter condition that you built by using the filter editors.</span></span>  
  
 <span data-ttu-id="f1e31-147">**필터 편집기 열기**</span><span class="sxs-lookup"><span data-stu-id="f1e31-147">**Open Filter Editor**</span></span>  
 <span data-ttu-id="f1e31-148">외부 테이블을 선택하고 사례 테이블 열에 조건을 설정할 수 있는 **데이터 집합 필터** 대화 상자와 선택한 테이블의 개별 열 또는 중첩 테이블의 열에 적용되는 조건을 작성할 수 있는 **필터** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1e31-148">Opens the **Data Set Filter** dialog box, which lets you select external tables, and set conditions on case table columns, and the **Filter** dialog box, which helps you build conditions that apply to individual columns in the selected table, or to columns in nested tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e31-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1e31-149">See Also</span></span>  
 <span data-ttu-id="f1e31-150">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f1e31-150">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 <span data-ttu-id="f1e31-151">[마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f1e31-151">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="f1e31-152">[마이닝 모델에 필터 적용](data-mining/apply-a-filter-to-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="f1e31-152">[Apply a Filter to a Mining Model](data-mining/apply-a-filter-to-a-mining-model.md) </span></span>  
 [<span data-ttu-id="f1e31-153">마이닝 모델에 대한 필터&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f1e31-153">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
