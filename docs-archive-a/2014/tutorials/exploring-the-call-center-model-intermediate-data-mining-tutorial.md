---
title: 콜 센터 모델 탐색 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734724"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="4e6b3-102">콜 센터 모델 탐색(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="4e6b3-102">Exploring the Call Center Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="4e6b3-103">지금까지 탐구 모델을 작성했으므로 이제 이 모델을 사용하여 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 제공되는 다음과 같은 도구로 데이터에 대해 보다 자세한 정보를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-103">Now that you have built the exploratory model, you can use it to learn more about your data by using the following tools provided in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="4e6b3-104">[Microsoft 신경망 뷰어](#bkmk_NNviewer) **:** 이 뷰어는 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에서 사용할 수 있으며 데이터의 상호 작용을 시험해 볼 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-104">[Microsoft Neural Network Viewer](#bkmk_NNviewer) **:** This viewer is available in the **Mining Model Viewer** tab of Data Mining Designer, and is designed to help you experiment with interactions in the data.</span></span>  
  
-   <span data-ttu-id="4e6b3-105">[Microsoft 일반 콘텐츠 트리 뷰어](#bkmk_genviewer) **:** 이 표준 뷰어에서는 모델을 생성할 때 알고리즘에서 발견 한 패턴 및 통계에 대 한 자세한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-105">[Microsoft Generic Content Tree Viewer](#bkmk_genviewer) **:** This standard viewer provides in-depth detail about the patterns and statistics discovered by the algorithm when it generated the model.</span></span>  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a><span data-ttu-id="4e6b3-106">Microsoft 신경망 뷰어</span><span class="sxs-lookup"><span data-stu-id="4e6b3-106">Microsoft Neural Network Viewer</span></span>  
 <span data-ttu-id="4e6b3-107">뷰어에는 **입력**, **출력**및 **변수**라는 세 개의 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-107">The viewer has three panes - **Input**, **Output**, and **Variables**.</span></span>  
  
 <span data-ttu-id="4e6b3-108">**출력** 창을 사용 하 여 예측 가능한 특성 또는 종속 변수에 대해 서로 다른 값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-108">By using the **Output** pane, you can select different values for the predictable attribute, or dependent variable.</span></span> <span data-ttu-id="4e6b3-109">모델에 예측 가능한 특성이 여러 개 있는 경우 **출력 특성** 목록에서 특성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-109">If your model contains multiple predictable attributes, you can select the attribute from the **Output Attribute** list.</span></span>  
  
 <span data-ttu-id="4e6b3-110">**변수** 창에서는 영향을 주는 특성 또는 변수 측면에서 선택한 두 결과를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-110">The **Variables** pane compares the two outcomes that you chose in terms of contributing attributes, or variables.</span></span> <span data-ttu-id="4e6b3-111">색이 지정된 막대는 변수가 대상 결과에 얼마나 많은 영향을 주는지를 시각적으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-111">The colored bars visually represent how strongly the variable affects the target outcomes.</span></span> <span data-ttu-id="4e6b3-112">변수에 대한 리프트 점수를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-112">You can also view lift scores for the variables.</span></span> <span data-ttu-id="4e6b3-113">리프트 점수는 사용하고 있는 마이닝 모델 유형에 따라 다르게 계산되지만 일반적으로 예측을 위해 이 특성을 사용할 때 모델의 향상률을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-113">A lift score is calculated differently depending on which mining model type you are using, but generally tells you the improvement in the model when using this attribute for prediction.</span></span>  
  
 <span data-ttu-id="4e6b3-114">**입력** 창에서는 모델에 영향 요인을 추가 하 여 다양 한 시나리오를 시험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-114">The **Input** pane lets you add influencers to the model to try out various what-if scenarios.</span></span>  
  
### <a name="using-the-output-pane"></a><span data-ttu-id="4e6b3-115">출력 창 사용</span><span class="sxs-lookup"><span data-stu-id="4e6b3-115">Using the Output Pane</span></span>  
 <span data-ttu-id="4e6b3-116">이 초기 모델에서는 얼마나 다양한 요인이 서비스 등급에 영향을 주는지 살펴보려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-116">In this initial model, you are interested in seeing how various factors affect the grade of service.</span></span> <span data-ttu-id="4e6b3-117">이렇게 하려면 출력 특성 목록에서 서비스 등급을 선택한 다음 **값 1** 및 **값 2**에 대 한 드롭다운 목록에서 범위를 선택 하 여 서로 다른 서비스 수준을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-117">To do this, you can select Service Grade from the list of output attributes, and then compare different levels of service by selecting ranges from the dropdown lists for **Value 1** and **Value 2**.</span></span>  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a><span data-ttu-id="4e6b3-118">가장 낮은 서비스 등급과 가장 높은 서비스 등급을 비교하려면</span><span class="sxs-lookup"><span data-stu-id="4e6b3-118">To compare lowest and highest service grades</span></span>  
  
1.  <span data-ttu-id="4e6b3-119">**값 1**에서 값이 가장 낮은 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-119">For **Value 1**, select the range with the lowest values.</span></span> <span data-ttu-id="4e6b3-120">예를 들어 0-0-0.7 범위는 가장 낮은 중단율을 나타내므로 결국 가장 높은 서비스 수준을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-120">For example, the range 0-0-0.7 represents the lowest abandon rates, and therefore the best level of service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e6b3-121">이 범위의 정확한 값은 모델 구성 방법에 따라 매우 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-121">The exact values in this range may vary depending on how you configured the model.</span></span>  
  
2.  <span data-ttu-id="4e6b3-122">**값 2**에서 가장 높은 값의 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-122">For **Value 2**, select the range with the highest values.</span></span> <span data-ttu-id="4e6b3-123">예를 들어 값이 >= 0.12 인 범위는 최고 중단 율을 나타내므로 최악의 서비스 등급을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-123">For example, the range with the value >=0.12 represents the highest abandon rates, and therefore the worst service grade.</span></span> <span data-ttu-id="4e6b3-124">즉 이 교대조 근무 시간 동안 전화를 건 고객 중 12%가 상담원과 연결하기 전에 전화를 끊었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-124">In other words, 12% of the customers who phoned during this shift hung up before speaking to a representative.</span></span>  
  
     <span data-ttu-id="4e6b3-125">**변수** 창의 내용이 결과 값에 영향을 주는 특성을 비교 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-125">The contents of the **Variables** pane are updated to compare attributes that contribute to the outcome values.</span></span> <span data-ttu-id="4e6b3-126">따라서 왼쪽 열에서는 가장 높은 서비스 등급과 연결된 특성을 보여 주고 오른쪽 열에서는 가장 낮은 서비스 등급과 연결된 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-126">Therefore, the left column shows you the attributes that are associated with the best grade of service, and the right column shows you the attributes associated with the worst grade of service.</span></span>  
  
### <a name="using-the-variables-pane"></a><span data-ttu-id="4e6b3-127">변수 창 사용</span><span class="sxs-lookup"><span data-stu-id="4e6b3-127">Using the Variables Pane</span></span>  
 <span data-ttu-id="4e6b3-128">이 모델에는 `Average Time Per Issue` 중요 한 요소 라고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-128">In this model, it appears that `Average Time Per Issue` is an important factor.</span></span> <span data-ttu-id="4e6b3-129">이 변수는 호출 유형에 상관없이 평균 호출 응답 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-129">This variable indicates the average time that it takes for a call to be answered, regardless of call type.</span></span>  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a><span data-ttu-id="4e6b3-130">특성에 대한 확률 및 리프트 점수를 보고 복사하려면</span><span class="sxs-lookup"><span data-stu-id="4e6b3-130">To view and copy probability and lift scores for an attribute</span></span>  
  
1.  <span data-ttu-id="4e6b3-131">**변수** 창에서 첫 번째 행의 색이 지정 된 막대 위에 마우스를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-131">In the **Variables** pane, pause the mouse over the colored bar in the first row.</span></span>  
  
     <span data-ttu-id="4e6b3-132">이 색이 지정 된 막대는 `Average Time Per Issue` 서비스 등급에 얼마나 강력한 기여를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-132">This colored bar shows you how strongly `Average Time Per Issue` contributes toward the service grade.</span></span> <span data-ttu-id="4e6b3-133">도구 설명은 변수와 대상 결과의 각 조합에 대한 총 점수, 확률 및 리프트 점수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-133">The tooltip shows an overall score, probabilities, and lift scores for each combination of a variable and a target outcome.</span></span>  
  
2.  <span data-ttu-id="4e6b3-134">**변수** 창에서 색이 지정 된 막대를 마우스 오른쪽 단추로 클릭 하 고 **복사**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-134">In the **Variables** pane, right-click any colored bar and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="4e6b3-135">Excel 워크시트에서 아무 셀 이나 마우스 오른쪽 단추로 클릭 하 고 **붙여넣기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-135">In an Excel worksheet, right-click any cell and select **Paste**.</span></span>  
  
     <span data-ttu-id="4e6b3-136">보고서가 HTML 테이블로 붙여 넣어지고 각 막대에 대한 점수만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-136">The report is pasted as an HTML table, and shows only the scores for each bar.</span></span>  
  
4.  <span data-ttu-id="4e6b3-137">다른 Excel 워크시트에서 셀을 마우스 오른쪽 단추로 클릭 하 고 선택 하 **여 붙여넣기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-137">In a different Excel worksheet, right-click any cell and select **Paste Special**.</span></span>  
  
     <span data-ttu-id="4e6b3-138">보고서가 텍스트 형식으로 붙여 넣어지고 다음 섹션에서 설명하는 관련 통계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-138">The report is pasted as text format, and includes the related statistics described in the next section.</span></span>  
  
### <a name="using-the-input-pane"></a><span data-ttu-id="4e6b3-139">입력 창 사용</span><span class="sxs-lookup"><span data-stu-id="4e6b3-139">Using the Input Pane</span></span>  
 <span data-ttu-id="4e6b3-140">교대조 또는 전화 상담원 수와 같은 특정 요인의 영향을 살펴보려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-140">Suppose that you are interested in looking at the effect of a particular factor, such as the shift, or number of operators.</span></span> <span data-ttu-id="4e6b3-141">**입력** 창을 사용 하 여 특정 변수를 선택할 수 있으며, **변수** 창이 자동으로 업데이트 되어 지정 된 변수와 함께 이전에 선택한 두 그룹을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-141">You can select a particular variable by using the **Input** pane, and the **Variables** pane is automatically updated to compare the two previously selected groups given the specified variable.</span></span>  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a><span data-ttu-id="4e6b3-142">입력 특성을 변경하여 서비스 등급에 대한 효과를 검토하려면</span><span class="sxs-lookup"><span data-stu-id="4e6b3-142">To review the effect on service grade by changing input attributes</span></span>  
  
1.  <span data-ttu-id="4e6b3-143">**입력** 창에서 **특성**에 대해 Shift를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-143">In the **Input** pane, for **attribute**, select Shift.</span></span>  
  
2.  <span data-ttu-id="4e6b3-144">**값**에 **AM**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-144">For **Value**, select **AM**.</span></span>  
  
     <span data-ttu-id="4e6b3-145">**변수** 창은 교대조가 **AM**일 때 모델에 미치는 영향을 표시 하도록 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-145">The **Variables** pane updates to show the impact on the model when the shift is **AM**.</span></span> <span data-ttu-id="4e6b3-146">다른 모든 선택 항목은 동일 하 게 유지 됩니다. 즉, 가장 낮은 서비스와 최고 등급을 비교 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-146">All other selections remain the same - you are still comparing the lowest and highest service grades.</span></span>  
  
3.  <span data-ttu-id="4e6b3-147">**값**에 대해 **오후 1**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-147">For **Value**, select **PM1**.</span></span>  
  
     <span data-ttu-id="4e6b3-148">**변수** 창은 이동이 변경 될 때 모델에 미치는 영향을 표시 하도록 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-148">The **Variables** pane updates to show the impact on the model when the shift changes.</span></span>  
  
4.  <span data-ttu-id="4e6b3-149">**입력** 창에서 **특성**아래에 있는 다음 빈 행을 클릭 하 고 호출을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-149">In the **Input** pane, click the next blank row under **Attribute**, and select Calls.</span></span> <span data-ttu-id="4e6b3-150">**값**에 대해 가장 많은 수의 호출을 나타내는 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-150">For **Value**, select the range that indicates the greatest number of calls.</span></span>  
  
     <span data-ttu-id="4e6b3-151">새 입력 조건이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-151">A new input condition is added to the list.</span></span> <span data-ttu-id="4e6b3-152">**변수** 창은 호출 볼륨이 가장 높을 때 특정 교대조에 대 한 모델의 영향을 표시 하도록 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-152">The **Variables** pane updates to show the impact on the model for a particular shift when the call volume is highest.</span></span>  
  
5.  <span data-ttu-id="4e6b3-153">계속 Shift 및 Calls에 대한 값을 변경하여 교대조, 호출량 및 서비스 등급 간의 흥미로운 상관 관계를 발견합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-153">Continue to change the values for Shift and Calls to find any interesting correlations between shift, call volume, and service grade.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e6b3-154">다른 특성을 사용할 수 있도록 **입력** 창을 지우려면 **뷰어 콘텐츠 새로 고침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-154">To clear the **Input** pane so that you can use different attributes, click **Refresh viewer content**.</span></span>  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a><span data-ttu-id="4e6b3-155">뷰어에서 제공하는 통계 해석</span><span class="sxs-lookup"><span data-stu-id="4e6b3-155">Interpreting the Statistics Provided in the Viewer</span></span>  
 <span data-ttu-id="4e6b3-156">오래 걸리는 대기 시간은 높은 중단율을 예측하는 강력한 요인으로, 낮은 서비스 등급을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-156">Longer waiting times are a strong predictor of a high abandon rate, meaning a poor service grade.</span></span> <span data-ttu-id="4e6b3-157">확실하게 이러한 결론을 내릴 수 있지만 마이닝 모델에서는 이러한 추세를 해석하는 데 유용한 몇 가지 추가 통계 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-157">This may seem an obvious conclusion; however, the mining model provides you with some additional statistical data to help you interpret these trends.</span></span>  
  
-   <span data-ttu-id="4e6b3-158">**점수**: 결과 간 판별에 대 한이 변수의 전반적인 중요도를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-158">**Score**: Value that indicates the overall importance of this variable for discriminating between outcomes.</span></span> <span data-ttu-id="4e6b3-159">점수가 높을수록 변수가 결과에 끼치는 영향도 큽니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-159">The higher the score, the stronger the effect the variable has on the outcome.</span></span>  
  
-   <span data-ttu-id="4e6b3-160">**값 1의 확률**:이 결과에 대 한이 값의 확률을 나타내는 백분율입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-160">**Probability of value 1**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="4e6b3-161">**값 2의 확률**:이 결과에 대 한이 값의 확률을 나타내는 백분율입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-161">**Probability of value 2**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="4e6b3-162">값 **1** 및 값 **2에**대 한 리프트: 값 1 및 값 2 결과를 예측 하기 위해이 특정 변수를 사용 하는 경우의 영향을 나타내는 점수입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-162">**Lift for Value 1** and **Lift for Value 2**: Scores that represents the impact of using this particular variable for predicting the Value 1 and Value 2 outcomes.</span></span> <span data-ttu-id="4e6b3-163">점수가 높을수록 변수가 결과를 보다 잘 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-163">The higher the score, the better the variable is at predicting the outcomes.</span></span>  
  
 <span data-ttu-id="4e6b3-164">다음 표에는 가장 많은 영향을 주는 요인에 대한 일부 값 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-164">The following table contains some example values for the top influencers.</span></span> <span data-ttu-id="4e6b3-165">예를 들어 **값 1의 확률** 은 60.6%이 고 **값 2의 확률** 은 8.30%입니다. 즉, 문제의 평균 시간이 44-70 분의 범위 내에 있고, 사례의 60.6%가 가장 높은 서비스 등급 (값 1 8.30)으로 전환 된 경우에는 서비스 등급이 더 심한 (값 2)이를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-165">For example, the **Probability of value 1** is 60.6% and **Probability of value 2** is 8.30%, meaning that when the Average Time Per Issue was in the range of 44-70 minutes, 60.6% of cases were in the shift with the highest service grades (Value 1), and 8.30% of cases were in the shift with the worse service grades (Value 2).</span></span>  
  
 <span data-ttu-id="4e6b3-166">이 정보를 사용하여 몇 가지 결론을 내릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-166">From this information, you can draw some conclusions.</span></span> <span data-ttu-id="4e6b3-167">보다 짧은 호출 응답 시간(44-70 범위)이 보다 높은 서비스 등급(0.00-0.07 범위)에 더 많은 영향을 끼칩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-167">Shorter call response time (the range of 44-70) strongly influences better service grade (the range 0.00-0.07).</span></span> <span data-ttu-id="4e6b3-168">점수(92.35)는 이 변수가 매우 중요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-168">The score (92.35) tells you that this variable is very important.</span></span>  
  
 <span data-ttu-id="4e6b3-169">그러나 영향을 주는 요인 목록을 살펴보면 보다 미묘하고 해석하기 더 어려운 영향을 가진 몇 가지 다른 요인을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-169">However, as you look down the list of contributing factors, you see some other factors with effects that are more subtle and more difficult to interpret.</span></span> <span data-ttu-id="4e6b3-170">예를 들어 교대조가 서비스에 영향을 주는 것 같지만 리프트 점수 및 상대 확률은 교대조가 주요 요인이 아님을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-170">For example, shift appears to influence service, but the lift scores and the relative probabilities indicate that shift is not a major factor.</span></span>  
  
|<span data-ttu-id="4e6b3-171">attribute</span><span class="sxs-lookup"><span data-stu-id="4e6b3-171">Attribute</span></span>|<span data-ttu-id="4e6b3-172">값</span><span class="sxs-lookup"><span data-stu-id="4e6b3-172">Value</span></span>|<span data-ttu-id="4e6b3-173">\<0.07 우위</span><span class="sxs-lookup"><span data-stu-id="4e6b3-173">Favors \< 0.07</span></span>|<span data-ttu-id="4e6b3-174">>= 0.12 우위</span><span class="sxs-lookup"><span data-stu-id="4e6b3-174">Favors >= 0.12</span></span>|  
|---------------|-----------|--------------------|----------------------|  
|<span data-ttu-id="4e6b3-175">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="4e6b3-175">Average Time Per Issue</span></span>|<span data-ttu-id="4e6b3-176">89.087-120.000</span><span class="sxs-lookup"><span data-stu-id="4e6b3-176">89.087 - 120.000</span></span>||<span data-ttu-id="4e6b3-177">점수: 100</span><span class="sxs-lookup"><span data-stu-id="4e6b3-177">Score:  100</span></span><br /><br /> <span data-ttu-id="4e6b3-178">Value1의 확률: 4.45%</span><span class="sxs-lookup"><span data-stu-id="4e6b3-178">Probability of Value1: 4.45 %</span></span><br /><br /> <span data-ttu-id="4e6b3-179">Value2의 확률: 51.94%</span><span class="sxs-lookup"><span data-stu-id="4e6b3-179">Probability of Value2: 51.94 %</span></span><br /><br /> <span data-ttu-id="4e6b3-180">Value1의 리프트: 0.19</span><span class="sxs-lookup"><span data-stu-id="4e6b3-180">Lift for Value1: 0.19</span></span><br /><br /> <span data-ttu-id="4e6b3-181">Value2의 리프트: 1.94</span><span class="sxs-lookup"><span data-stu-id="4e6b3-181">Lift for Value2: 1.94</span></span>|  
|<span data-ttu-id="4e6b3-182">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="4e6b3-182">Average Time Per Issue</span></span>|<span data-ttu-id="4e6b3-183">44.000-70.597</span><span class="sxs-lookup"><span data-stu-id="4e6b3-183">44.000 - 70.597</span></span>|<span data-ttu-id="4e6b3-184">점수: 92.35</span><span class="sxs-lookup"><span data-stu-id="4e6b3-184">Score: 92.35</span></span><br /><br /> <span data-ttu-id="4e6b3-185">값 1의 확률: 60.06%</span><span class="sxs-lookup"><span data-stu-id="4e6b3-185">Probability of Value1: 60.06 %</span></span><br /><br /> <span data-ttu-id="4e6b3-186">값 2의 확률: 8.30%</span><span class="sxs-lookup"><span data-stu-id="4e6b3-186">Probability of Value2: 8.30 %</span></span><br /><br /> <span data-ttu-id="4e6b3-187">값 1의 리프트: 2.61</span><span class="sxs-lookup"><span data-stu-id="4e6b3-187">Lift for Value1: 2.61</span></span><br /><br /> <span data-ttu-id="4e6b3-188">값 2의 리프트: 0.31</span><span class="sxs-lookup"><span data-stu-id="4e6b3-188">Lift for Value2: 0.31</span></span>||  
  
 [<span data-ttu-id="4e6b3-189">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="4e6b3-189">Back to Top</span></span>](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a><span data-ttu-id="4e6b3-190">Microsoft 일반 콘텐츠 트리 뷰어</span><span class="sxs-lookup"><span data-stu-id="4e6b3-190">Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="4e6b3-191">이 뷰어를 사용하면 모델을 처리할 때 알고리즘에서 만든 보다 자세한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-191">This viewer can be used to view even more detailed information created by the algorithm when the model is processed.</span></span> <span data-ttu-id="4e6b3-192">**MicrosoftGeneric 콘텐츠 트리 뷰어** 는 마이닝 모델을 일련의 노드로 나타내며 각 노드는 학습 데이터에 대 한 배운 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-192">The **MicrosoftGeneric Content Tree Viewer** represents the mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="4e6b3-193">이 뷰어는 모든 모델에서 사용할 수 있지만 노드 내용은 모델 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-193">This viewer can be used with all models, but the contents of the nodes are different depending in the model type.</span></span>  
  
 <span data-ttu-id="4e6b3-194">신경망 모델 또는 로지스틱 회귀 모델의 경우 특히 `marginal statistics node`가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-194">For neural network models or logistic regression models, you might find the `marginal statistics node` particularly useful.</span></span> <span data-ttu-id="4e6b3-195">이 노드에는 데이터의 값 분포에 대한 파생 통계가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-195">This node contains derived statistics about the distribution of values in your data.</span></span> <span data-ttu-id="4e6b3-196">많은 T-SQL 쿼리를 작성하지 않고 데이터 요약을 얻으려는 경우 이 정보가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-196">This information can be useful if you want to get a summary of the data without having to write many T-SQL queries.</span></span> <span data-ttu-id="4e6b3-197">이전 항목의 값 범주화에 대한 차트가 marginal statistics node에서 파생되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-197">The chart of binning values in the previous topic was derived from the marginal statistics node.</span></span>  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a><span data-ttu-id="4e6b3-198">마이닝 모델에서 데이터 값 요약을 얻으려면</span><span class="sxs-lookup"><span data-stu-id="4e6b3-198">To obtain a summary of data values from the mining model</span></span>  
  
1.  <span data-ttu-id="4e6b3-199">데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에서을 선택 \<mining model name> 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-199">In Data Mining Designer, in the **Mining Model Viewer** tab, select \<mining model name>.</span></span>  
  
2.  <span data-ttu-id="4e6b3-200">**뷰어** 목록에서 **Microsoft 일반 콘텐츠 트리 뷰어**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-200">From the **Viewer** list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="4e6b3-201">마이닝 모델 뷰가 새로 고쳐져 왼쪽 창에 노드 계층이 표시되고 오른쪽 창에 HTML 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-201">The view of the mining model refreshes to show a node hierarchy in the left-hand pane and an HTML table in the right-hand pane.</span></span>  
  
3.  <span data-ttu-id="4e6b3-202">**노드 캡션** 창에서 이름이 10000000000000000 인 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-202">In the **Node Caption** pane, click the node that has the name 10000000000000000.</span></span>  
  
     <span data-ttu-id="4e6b3-203">모델의 최상위 노드는 항상 모델 루트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-203">The topmost node in any model is always the model root node.</span></span> <span data-ttu-id="4e6b3-204">신경망 또는 로지스틱 회귀 모델에서 이 노드 바로 아래에 있는 노드가 marginal statistics node입니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-204">In a neural network or logistic regression model, the node immediately under that is the marginal statistics node.</span></span>  
  
4.  <span data-ttu-id="4e6b3-205">**노드 세부 정보** 창에서 행을 찾을 때까지 아래로 스크롤합니다 NODE_DISTRIBUTION 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-205">In the **Node Details** pane, scroll down until you find the row, NODE_DISTRIBUTION.</span></span>  
  
5.  <span data-ttu-id="4e6b3-206">NODE_DISTRIBUTION 테이블 아래로 스크롤하여 신경망 알고리즘에서 계산한 값 분포를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-206">Scroll down through the NODE_DISTRIBUTION table to view the distribution of values as calculated by the neural network algorithm.</span></span>  
  
 <span data-ttu-id="4e6b3-207">보고서에 이 값을 사용하려면 특정 행에 대한 정보를 선택한 다음 복사하거나 다음 DMX(Data Mining Extensions) 쿼리를 사용하여 노드의 전체 내용을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-207">To use this data in a report, you could select and then copy the information for specific rows, or you can use the following Data Mining Extensions (DMX) query to extract the complete contents of the node.</span></span>  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 <span data-ttu-id="4e6b3-208">또한 NODE_DISTRIBUTION 테이블의 노드 계층 및 정보를 사용하여 신경망의 개별 경로를 이동하고 숨겨진 계층의 통계를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-208">You can also use the node hierarchy and the details in the NODE_DISTRIBUTION table to traverse individual paths in the neural network and view statistics from the hidden layer.</span></span> <span data-ttu-id="4e6b3-209">자세한 내용은 [신경망 모델 쿼리 예제](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4e6b3-209">For more information, see [Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="4e6b3-210">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="4e6b3-210">Back to Top</span></span>](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4e6b3-211">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="4e6b3-211">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4e6b3-212">로지스틱 회귀 모델을 콜 센터 구조에 추가 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="4e6b3-212">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="4e6b3-213">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e6b3-213">See Also</span></span>  
 <span data-ttu-id="4e6b3-214">[신경망 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b3-214">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="4e6b3-215">[신경망 모델 쿼리 예제](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b3-215">[Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span></span>  
 <span data-ttu-id="4e6b3-216">[Microsoft 신경망 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4e6b3-216">[Microsoft Neural Network Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="4e6b3-217">마이닝 모델에서 열의 분할 변경</span><span class="sxs-lookup"><span data-stu-id="4e6b3-217">Change the Discretization of a Column in a Mining Model</span></span>](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
