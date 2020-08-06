---
title: 리프트 차트를 사용 하 여 정확도 테스트 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a3dcdd1d1b78911f5ffd37a383532abdd4814c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734636"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a><span data-ttu-id="a2d46-102">리프트 차트를 사용하여 정확도 테스트(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="a2d46-102">Testing Accuracy with Lift Charts (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="a2d46-103">데이터 마이닝 디자이너의 **마이닝 정확도 차트** 탭에서 각 모델이 얼마나 잘 예측 하는지 계산 하 고 각 모델의 결과를 다른 모델의 결과와 직접 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-103">On the **Mining Accuracy Chart** tab of Data Mining Designer, you can calculate how well each of your models makes predictions, and compare the results of each model directly against the results of the other models.</span></span> <span data-ttu-id="a2d46-104">이 비교 방법을 *리프트 차트*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-104">This method of comparison is referred to as a *lift chart*.</span></span> <span data-ttu-id="a2d46-105">일반적으로 마이닝 모델의 예측 정확도는 리프트 또는 분류 정확도를 통해 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-105">Typically, the predictive accuracy of a mining model is measured by either lift or classification accuracy.</span></span> <span data-ttu-id="a2d46-106">이 자습서에서는 리프트 차트만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-106">For this tutorial we will use the lift chart only.</span></span>  
  
 <span data-ttu-id="a2d46-107">이 항목에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-107">In this topic, you will perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="a2d46-108">입력 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="a2d46-108">Choose the Input Data</span></span>](#BKMK_InputData)  
  
-   [<span data-ttu-id="a2d46-109">정확도 차트 매개 변수 구성</span><span class="sxs-lookup"><span data-stu-id="a2d46-109">Configure Accuracy Chart Parameters</span></span>](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a><span data-ttu-id="a2d46-110">입력 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="a2d46-110">Choosing the Input Data</span></span>  
 <span data-ttu-id="a2d46-111">마이닝 모델의 정확도를 테스트하는 첫 번째 단계는 테스트에 사용할 데이터 원본을 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-111">The first step in testing the accuracy of your mining models is to select the data source that you will use for testing.</span></span> <span data-ttu-id="a2d46-112">모델이 데이터 테스트를 얼마나 잘 수행하는지 테스트한 다음 외부 데이터에 이 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-112">You will test how well the models perform against your testing data and then you will use them with external data.</span></span>  
  
#### <a name="to-select-the-data-set"></a><span data-ttu-id="a2d46-113">데이터 집합을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="a2d46-113">To select the data set</span></span>  
  
1.  <span data-ttu-id="a2d46-114">의 데이터 마이닝 디자이너에서 **마이닝 정확도 차트** 탭으로 전환 하 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 고 **입력 선택** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-114">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="a2d46-115">**정확도 차트에 사용할 데이터 집합을 선택** 하십시오. 그룹 상자에서 **마이닝 구조 테스트 사례 사용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-115">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span> <span data-ttu-id="a2d46-116">이는 마이닝 구조를 만들 때 따로 설정 하는 테스트 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-116">This is the testing data that you set aside when you created the mining structure.</span></span>  
  
     <span data-ttu-id="a2d46-117">다른 옵션에 대 한 자세한 내용은 [정확도 차트 유형 선택 및 차트 옵션 설정](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2d46-117">For more information on the other options, see [Choose an Accuracy Chart Type and Set Chart Options](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a><span data-ttu-id="a2d46-118">정확도 차트 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="a2d46-118">Setting Accuracy Chart Parameters</span></span>  
 <span data-ttu-id="a2d46-119">정확도 차트를 만들려면 다음 세 가지를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-119">To create an accuracy chart, you must define three things:</span></span>  
  
-   <span data-ttu-id="a2d46-120">정확도 차트에 포함 해야 하는 모델은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="a2d46-120">Which models should you include in the accuracy chart?</span></span>  
  
-   <span data-ttu-id="a2d46-121">측정할 예측 가능한 특성을 선택 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a2d46-121">Which predictable attribute do you want to measure?</span></span> <span data-ttu-id="a2d46-122">일부 모델에는 대상이 여러 개 있을 수 있지만 각 차트는 한 번에 하나의 결과를 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-122">Some models might have multiple targets, but each chart can measure only one outcome at a time.</span></span>  
  
     <span data-ttu-id="a2d46-123">정확도 차트에서 열을 **예측 가능한 열 이름** 으로 사용 하려면 열이 또는의 사용 유형 이어야 합니다 `Predict` `Predict Only` .</span><span class="sxs-lookup"><span data-stu-id="a2d46-123">To use a column as the **Predictable Column Name** in an accuracy chart, the columns must have the usage type of `Predict` or `Predict Only`.</span></span> <span data-ttu-id="a2d46-124">또한 대상 열의 콘텐츠 형식은 또는 이어야 합니다 `Discrete` `Discretized` .</span><span class="sxs-lookup"><span data-stu-id="a2d46-124">Also, the content type of the target column must be either `Discrete` or `Discretized`.</span></span> <span data-ttu-id="a2d46-125">즉, 리프트 차트를 사용 하 여 연속 숫자 출력에 대 한 정확도를 측정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-125">In other words, you cannot measure accuracy against continuous numeric outputs using the lift chart.</span></span>  
  
-   <span data-ttu-id="a2d46-126">모델의 일반 정확도를 측정 하거나 특정 값 (예: [자전거 구매자] = ' 예 ')을 예측할 때 정확도를 측정 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="a2d46-126">Do you want to measure the model's general accuracy, or its accuracy  in predicting a particular value (such as [Bike Buyer] = 'Yes')</span></span>  
  
#### <a name="to-generate-the-lift-chart"></a><span data-ttu-id="a2d46-127">리프트 차트를 생성 하려면</span><span class="sxs-lookup"><span data-stu-id="a2d46-127">To generate the lift chart</span></span>  
  
1.  <span data-ttu-id="a2d46-128">데이터 마이닝 디자이너의 **입력 선택** 탭에 있는 **리프트 차트에 표시할 예측 가능한 마이닝 모델 열을 선택**하십시오 .에서 **예측 열과 값 동기화**에 대 한 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-128">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
2.  <span data-ttu-id="a2d46-129">**예측 가능한 열 이름** 열에서 각 모델에 대해 **자전거 구매자** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-129">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
3.  <span data-ttu-id="a2d46-130">**표시** 열에서 각 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-130">In the **Show** column, select each of the models.</span></span>  
  
     <span data-ttu-id="a2d46-131">기본적으로 마이닝 구조에 있는 모델이 모두 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-131">By default, all the models in the mining structure are selected.</span></span> <span data-ttu-id="a2d46-132">모델을 포함하지 않을 수도 있지만 이 자습서에서는 모든 모델을 선택된 채로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-132">You can decide not to include a model, but for this tutorial leave all the models selected.</span></span>  
  
4.  <span data-ttu-id="a2d46-133">**예측 값** 열에서 **1**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-133">In the **Predict Value** column, select **1**.</span></span> <span data-ttu-id="a2d46-134">예측 가능한 해당 열이 포함된 각 모델에 대해 같은 값이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-134">The same value is automatically filled in for each model that has the same predictable column.</span></span>  
  
5.  <span data-ttu-id="a2d46-135">**리프트 차트** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-135">Select the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="a2d46-136">탭을 클릭 하면 예측 쿼리가 실행 되어 테스트 데이터에 대 한 예측을 가져오고 결과를 알려진 값과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-136">When you click the tab, a prediction query is executed to get predictions for the test data, and the results are compared against the known values.</span></span> <span data-ttu-id="a2d46-137">결과가 그래프에 점으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-137">The results are plotted on the graph.</span></span>  
  
     <span data-ttu-id="a2d46-138">**Predict 값** 옵션을 사용 하 여 특정 대상 결과를 지정한 경우 리프트 차트는 임의 추측 결과와 이상적인 모델의 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-138">If you specified a particular target outcome using the **Predict Value** option, the lift chart plots the results of random guesses and the results of an ideal model.</span></span>  
  
    -   <span data-ttu-id="a2d46-139">임의 추측 선은 데이터를 사용 하 여 예측에 알리지 않는 모델의 정확도를 표시 합니다. 즉, 두 결과 사이에 50-50을 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-139">The random guess line shows how accurate the model would be without using any data to inform its predictions: that is, a 50-50 split between two outcomes.</span></span> <span data-ttu-id="a2d46-140">리프트 차트를 사용 하면 임의 추측과 비교 하 여 모델의 성능을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-140">The lift chart helps you visualize how much better your model performs in comparison to a random guess.</span></span>  
  
    -   <span data-ttu-id="a2d46-141">이상적인 모델 선은 정확도의 상한을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-141">The ideal model line represents the upper bound of accuracy.</span></span> <span data-ttu-id="a2d46-142">모델이 항상 정확 하 게 예측 되는 경우 달성할 수 있는 최대한의 이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-142">It shows you the maximum possible benefit you could achieve if your model always predicted accurately.</span></span>  
  
     <span data-ttu-id="a2d46-143">만든 마이닝 모델은 일반적으로 이러한 두 극단 사이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-143">The mining models you created will usually fall between these two extremes.</span></span> <span data-ttu-id="a2d46-144">임의 추측의 향상 률은 *리프트*로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-144">Any improvement from the random guess is considered to be *lift*.</span></span>  
  
6.  <span data-ttu-id="a2d46-145">범례를 사용하여 이상적인 모델과 임의 추측 모델을 나타내는 색이 지정된 선을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-145">Use the legend to locate the colored lines representing the Ideal Model and the Random Guess Model.</span></span>  
  
     <span data-ttu-id="a2d46-146">`TM_Decision_Tree`모델은 클러스터링 및 Naive Bayes 모델을 모두 수행 하는 가장 큰 리프트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d46-146">You'll notice that the `TM_Decision_Tree` model provides the greatest lift,  outperforming both the Clustering and Naive Bayes models.</span></span>  
  
 <span data-ttu-id="a2d46-147">이 단원에서 만든 리프트 차트와 비슷한 리프트 차트에 대 한 자세한 설명은 [차트 &#40;Analysis Services-데이터 마이닝&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2d46-147">For an in-depth explanation of a lift chart similar to the one created in this lesson, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a2d46-148">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a2d46-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a2d46-149">기본 데이터 마이닝 자습서를 &#40;필터링 된 모델 테스트&#41;</span><span class="sxs-lookup"><span data-stu-id="a2d46-149">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2d46-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2d46-150">See Also</span></span>  
 <span data-ttu-id="a2d46-151">[리프트 차트 &#40;Analysis Services-데이터 마이닝&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a2d46-151">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="a2d46-152">리프트 차트 탭 &#40;마이닝 정확도 차트 뷰&#41;</span><span class="sxs-lookup"><span data-stu-id="a2d46-152">Lift Chart Tab &#40;Mining Accuracy Chart View&#41;</span></span>](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
