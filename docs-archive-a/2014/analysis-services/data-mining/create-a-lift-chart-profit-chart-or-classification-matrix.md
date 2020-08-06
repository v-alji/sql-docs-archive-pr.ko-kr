---
title: 리프트 차트, 수익 차트 또는 분류 행렬 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], mining structures
ms.assetid: aa3d052f-58a9-4417-8e7a-5e6feb562af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 932138b37b36269bed86df42786bd5d684f75ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728972"
---
# <a name="create-a-lift-chart-profit-chart-or-classification-matrix"></a><span data-ttu-id="3a53d-102">리프트 차트, 수익 차트 또는 분류표 만들기</span><span class="sxs-lookup"><span data-stu-id="3a53d-102">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>
  <span data-ttu-id="3a53d-103">다음과 같은 기본적인 다섯 단계로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 마이닝 모델에 대한 정확도 차트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-103">You can create an accuracy chart for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data mining model in five basic steps:</span></span>  
  
-   <span data-ttu-id="3a53d-104">비교할 마이닝 모델을 포함하는 마이닝 구조를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-104">Select the mining structure that contains the mining models that you want to compare.</span></span>  
  
-   <span data-ttu-id="3a53d-105">차트에 추가할 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-105">Select the mining models to add to the chart.</span></span>  
  
-   <span data-ttu-id="3a53d-106">차트를 생성하는 데 사용할 테스트 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-106">Specify a source of testing data to use in generating the chart.</span></span>  
  
-   <span data-ttu-id="3a53d-107">차트 종류를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-107">Choose the chart type.</span></span>  
  
-   <span data-ttu-id="3a53d-108">차트 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-108">Configure the chart options.</span></span>  
  
 <span data-ttu-id="3a53d-109">이러한 기본 단계는 리프트 차트, 수익 차트 및 분류표에도 동일하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-109">These basic steps are the same for the lift chart, profit chart, and classification matrix.</span></span> <span data-ttu-id="3a53d-110">다음 절차는 이러한 차트 종류에 대해 기본 차트 옵션을 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-110">The following procedures outline the steps to configure the basic chart options for these chart types.</span></span> <span data-ttu-id="3a53d-111">교차 유효성 검사 보고서를 만드는 방법에 대한 자세한 내용은 [교차 유효성 검사 보고서의 측정값](measures-in-the-cross-validation-report.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a53d-111">For information about how to create a cross-validation report, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
### <a name="open-the-mining-structure-in-the-accuracy-chart-designer"></a><span data-ttu-id="3a53d-112">정확도 차트 디자이너에서 마이닝 구조 열기</span><span class="sxs-lookup"><span data-stu-id="3a53d-112">Open the mining structure in the Accuracy Chart Designer</span></span>  
  
1.  <span data-ttu-id="3a53d-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 데이터 마이닝 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-113">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a53d-114">솔루션 탐색기에서 마이닝 모델이 포함된 구조를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-114">In Solution Explorer, double-click the structure that contains the mining model or models.</span></span>  
  
3.  <span data-ttu-id="3a53d-115">**마이닝 정확도 차트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-115">Click the **Mining Accuracy Chart** tab.</span></span>  
  
### <a name="select-mining-models-for-inclusion-in-the-chart"></a><span data-ttu-id="3a53d-116">차트에 포함될 마이닝 모델 선택</span><span class="sxs-lookup"><span data-stu-id="3a53d-116">Select mining models for inclusion in the chart</span></span>  
  
1.  <span data-ttu-id="3a53d-117">**데이터 마이닝 디자이너의** 마이닝 정확도 차트 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭에서 **입력 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-117">On the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Input Selection** tab.</span></span>  
  
     <span data-ttu-id="3a53d-118">현재 구조에서 동일한 예측 가능한 특성이 있는 모든 모델이 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-118">The list displays all models in the current structure that have the same predictable attribute.</span></span>  
  
2.  <span data-ttu-id="3a53d-119">차트에 포함시킬 각 모델의 **표시** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-119">Select the **Show box** for each model that you want to include in the chart.</span></span>  
  
3.  <span data-ttu-id="3a53d-120">**예측 가능한 열 이름** 입력란을 클릭하고 목록에서 예측 가능한 열의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-120">Click the **Predictable Column Name** text box, and select the name of a predictable column from the list.</span></span> <span data-ttu-id="3a53d-121">하나의 차트에 입력한 모든 모델은 같은 예측 가능한 열을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-121">All models that you put in one chart must have the same predictable column.</span></span>  
  
4.  <span data-ttu-id="3a53d-122">두 개의 모델을 비교하는데 예측 가능한 열의 값이나 데이터 형식이 서로 다를 경우 **예측 열과 값 동기화** 확인란의 선택을 취소하여 강제로 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-122">If you compare two models and the predictable columns have different values or different data types, clear the **Synchonize prediction columns and values** box to force a comparison.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a53d-123">**예측 열과 값 동기화** 확인란을 선택하면 Analysis Services는 모델의 예측 가능한 열 데이터를 분석하고 데이터를 테스트한 다음 가장 일치하는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-123">If the **Synchonize prediction columns and values** box is selected, Analysis Services analyzes the data in the predictable columns of the model and the test data, and attempts to find the best match.</span></span> <span data-ttu-id="3a53d-124">그러므로 부득이하게 열 비교를 강제로 수행해야 경우가 아니라면 이 확인란의 선택을 취소하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3a53d-124">Therefore, do not clear the box unless absolutely necessary to force a comparison of the columns.</span></span>  
  
5.  <span data-ttu-id="3a53d-125">**예측 값** 입력란을 클릭하고 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-125">Click the **Predict Value** text box, and select a value from the list.</span></span> <span data-ttu-id="3a53d-126">예측 가능한 열의 데이터 형식이 연속일 경우 입력란에 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-126">If the predictable column is a continuous data type, you must type a value in the text box.</span></span>  
  
     <span data-ttu-id="3a53d-127">자세한 내용은 [마이닝 모델 테스트에 사용할 열 선택](choose-the-column-to-use-for-testing-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a53d-127">For more information, see [Choose the Column to Use for Testing a Mining Model](choose-the-column-to-use-for-testing-a-mining-model.md).</span></span>  
  
### <a name="select-testing-data"></a><span data-ttu-id="3a53d-128">테스트 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="3a53d-128">Select testing data</span></span>  
  
1.  <span data-ttu-id="3a53d-129">**마이닝 정확도 차트** 탭의 **입력 선택** 탭에서 **정확도 차트에 사용할 데이터 집합을 선택하십시오.** 그룹의 옵션 중 하나를 선택하여 차트를 생성하는 데 사용할 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-129">On the **Input Selection** tab of the **Mining Accuracy Chart** tab, specify the source of the data that you will use to generate the chart by selecting one of the options in the group, **Select data set to be used for accuracy chart**.</span></span>  
  
    -   <span data-ttu-id="3a53d-130">모델을 만드는 동안 적용되었을 수 있는 필터와 마이닝 구조 테스트 사례의 교차에 의해 정의되는 사례의 하위 집합을 사용하려면 **마이닝 모델 테스트 사례 사용**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-130">Select the option, **Use Mining Model test cases**, if you want to use the subset of cases that is defined by the intersection of the mining structure test cases and any filters that may have been applied during model creation.</span></span>  
  
    -   <span data-ttu-id="3a53d-131">마이닝 구조 홀드아웃 데이터 집합의 일부로 정의된 전체 테스트 사례 집합을 사용하려면 **마이닝 구조 테스트 사례 사용**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-131">Select the option, **Use mining structure test cases**, to use the full set of testing cases that were defined as part of the mining structures holdout data set.</span></span>  
  
    -   <span data-ttu-id="3a53d-132">외부 데이터를 사용하려는 경우 **다른 데이터 집합 지정**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-132">Select the option, **Specify a different data set**, if you want to use external data.</span></span>  <span data-ttu-id="3a53d-133">데이터 집합을 데이터 원본 뷰로 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-133">The data set must be available as a data source view.</span></span>   <span data-ttu-id="3a53d-134">찾아보기 (**...**) 단추를 클릭 하 여 정확도 차트에 사용할 데이터 테이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-134">Click the browse (**...**) button to choose the data tables to use for the accuracy chart.</span></span> <span data-ttu-id="3a53d-135">자세한 내용은 [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a53d-135">For more information, see [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md).</span></span>  
  
         <span data-ttu-id="3a53d-136">외부 데이터 집합을 사용하고 있는 경우 선택적으로 입력 데이터 집합을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-136">If you are using an external data set, you can optionally filter the input data set.</span></span> <span data-ttu-id="3a53d-137">자세한 내용은 [모델 테스트 데이터에 필터 적용](apply-filters-to-model-testing-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a53d-137">For more information, see [Apply Filters to Model Testing Data](apply-filters-to-model-testing-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a53d-138">**입력 선택** 탭에서는 모델 테스트 사례 또는 마이닝 구조 테스트 사례에 대 한 필터를 만들 수 없습니다. 마이닝 모델에 대 한 필터를 만들려면 모델의 필터 속성을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-138">You cannot create a filter on the model test cases or the mining structure test cases on the **Input Selection** tab. To create a filter on the mining model, modify the Filter property of the model.</span></span> <span data-ttu-id="3a53d-139">자세한 내용은 [마이닝 모델에 필터 적용](apply-a-filter-to-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a53d-139">For more information, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
### <a name="configure-chart-settings-and-generate-the-chart"></a><span data-ttu-id="3a53d-140">차트 설정 구성 및 차트 생성</span><span class="sxs-lookup"><span data-stu-id="3a53d-140">Configure chart settings and generate the chart</span></span>  
  
1.  <span data-ttu-id="3a53d-141">**마이닝 정확도 차트** 탭에서 만들려는 차트 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-141">In the **Mining Accuracy Chart** tab, click the tab for the chart you want to create.</span></span>  
  
2.  <span data-ttu-id="3a53d-142">**리프트 차트**의 경우 **리프트 차트** 탭을 클릭 합니다. 차트는 방금 선택한 모델, 예측 가능한 특성 및 입력 데이터를 기반으로 자동 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-142">For a **lift chart**, click the **Lift Chart** tab. The chart is automatically generated based on the model, predictable attributes, and input data that you just selected.</span></span>  
  
3.  <span data-ttu-id="3a53d-143">**분류 행렬**의 경우 **분류표** 탭을 클릭 합니다. 추가 설정은 필요 하지 않습니다. 선택한 입력 데이터 및 모델을 기반으로 차트가 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-143">For a **classification matrix**, click the **Classification Matrix** tab. No further settings are needed; the chart is automatically generated based on the input data and model that you selected.</span></span>  
  
4.  <span data-ttu-id="3a53d-144">**수익 차트**의 경우 먼저 **리프트 차트** 탭을 클릭 합니다. 그런 다음 **차트 종류** 드롭다운 목록에서 **수익 차트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-144">For a **profit chart**, first click the **Lift Chart** tab. Then, from the **Chart type** drop-down list, select **Profit chart**.</span></span>  
  
     <span data-ttu-id="3a53d-145">**수익 차트 설정** 대화 상자에서 다음 설정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-145">Enter the following settings in the **Profit Chart Settings** dialog box.</span></span>  
  
     <span data-ttu-id="3a53d-146">**표본의**</span><span class="sxs-lookup"><span data-stu-id="3a53d-146">**Population**</span></span>  
     <span data-ttu-id="3a53d-147">리프트 차트를 만들 때 사용할 데이터 집합의 사례 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-147">The number of cases from the data set that you want to use when creating the lift chart.</span></span>  
  
     <span data-ttu-id="3a53d-148">모델은 항상 확률의 내림차순으로 사례를 선택합니다. 즉, 잠재 고객을 평가하는 중이고 고객 데이터베이스의 레코드 절반만 나타내는 수를 선택할 경우 사용자의 모델에 가장 적합한 사례의 하위 집합에 대한 정확도가 모델에서 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-148">The model always chooses the cases in order of decreasing probability; that is, if you are assessing potential customers and you choose a number that represents only half the records in your customer database, the model will measure accuracy on the subset of cases that best fit your model.</span></span>  
  
     <span data-ttu-id="3a53d-149">이 이유 때문에 모델을 사용하여 메일을 생성하거나 캠페인을 만들 때 긍정적으로 응답할 확률이 가장 높은 고객만 대상으로 삼기 위해 각 사례와 관련된 예측 확률을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-149">This is because when you use the model to generate a mailing or create a campaign, you will use the prediction probability associated with each case to target only the customers who have the highest probability of making a positive response.</span></span>  
  
     <span data-ttu-id="3a53d-150">**고정 비용**</span><span class="sxs-lookup"><span data-stu-id="3a53d-150">**Fixed Cost**</span></span>  
     <span data-ttu-id="3a53d-151">비즈니스상의 문제와 관련된 고정 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-151">The fixed cost that is associated with the business problem.</span></span>  
  
     <span data-ttu-id="3a53d-152">대상 메일 솔루션에 대한 것일 경우 고정 비용은 홍보 메일 준비를 위한 초기 비용을 포함한 프린터 설치 요금을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-152">If this were for a targeted mailing solution, the fixed cost might represent a printer setup fee that covers the initial cost of preparing the promotional mailing.</span></span>  
  
     <span data-ttu-id="3a53d-153">이 비용은 전체 대상 모집단에 한 번 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-153">This cost applies one time to the entire target population.</span></span>  
  
     <span data-ttu-id="3a53d-154">**개별 비용**</span><span class="sxs-lookup"><span data-stu-id="3a53d-154">**Individual Cost**</span></span>  
     <span data-ttu-id="3a53d-155">고정 비용 외에 각 고객에게 연락하는 데 드는 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-155">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="3a53d-156">예를 들어 홍보 메일에 대한 우편 비용이나 전화를 거는 데 드는 비용을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-156">For example, you might enter the postage cost for a promotional mailing or the cost of making telephone calls.</span></span>  
  
     <span data-ttu-id="3a53d-157">이 비용은 전체 대상 모집단에 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-157">This cost must be the same for the entire target population.</span></span> <span data-ttu-id="3a53d-158">대상이 되는 사례 수를 각 값에 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-158">Each value is multiplied by the number of cases that are targeted.</span></span>  
  
     <span data-ttu-id="3a53d-159">**개인 당 수익**</span><span class="sxs-lookup"><span data-stu-id="3a53d-159">**Revenue Per Individual**</span></span>  
     <span data-ttu-id="3a53d-160">성공적인 각 판매와 관련된 수익입니다.</span><span class="sxs-lookup"><span data-stu-id="3a53d-160">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a53d-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a53d-161">See Also</span></span>  
 <span data-ttu-id="3a53d-162">[리프트 차트 &#40;Analysis Services-데이터 마이닝&#41;](lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3a53d-162">[Lift Chart &#40;Analysis Services - Data Mining&#41;](lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="3a53d-163">분류표&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="3a53d-163">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)  
  
  
