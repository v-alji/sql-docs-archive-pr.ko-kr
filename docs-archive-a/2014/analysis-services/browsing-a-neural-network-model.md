---
title: 신경망 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab2673d5b1881f74c2bc146b084d2efc7b06d69b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648102"
---
# <a name="browsing-a-neural-network-model"></a><span data-ttu-id="ae378-102">신경망 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="ae378-102">Browsing a Neural Network Model</span></span>
  <span data-ttu-id="ae378-103">**찾아보기**를 사용하여 신경망 또는 로지스틱 회귀 모델을 열면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 신경망 모델 뷰어와 비슷한 대화형 뷰어에 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-103">When you open a neural network or logistic regression model using **Browse**, the model is displayed in an interactive viewer, similar to the neural network model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ae378-104">이 뷰어에서는 상관 관계를 탐색하고 모델 및 기본 데이터의 패턴에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-104">The viewer helps you explore correlations, and get information about the patterns in the model and the underlying data.</span></span>

##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="ae378-105">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="ae378-105">Explore the Model</span></span>
 <span data-ttu-id="ae378-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] 신경망 또는 로지스틱 회귀 알고리즘을 기반으로 하는 모델은 알려진 입력과 출력 간의 연결 집합으로 데이터를 분석한다는 점에서 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-106">Models that are based on [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network or Logistic Regression algorithms are similar in that they analyze data as a set of connections among known inputs and outputs.</span></span> <span data-ttu-id="ae378-107">**찾아보기** 뷰어에서 다음과 같은 컨트롤을 사용하여 이러한 연결을 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-107">The **Browse** viewer helps you to explore those connections, using the following controls:</span></span>

-   [<span data-ttu-id="ae378-108">변수</span><span class="sxs-lookup"><span data-stu-id="ae378-108">Variables</span></span>](#BKMK_Variables)

-   [<span data-ttu-id="ae378-109">입력</span><span class="sxs-lookup"><span data-stu-id="ae378-109">Inputs</span></span>](#BKMK_Inputs)

-   [<span data-ttu-id="ae378-110">outputs</span><span class="sxs-lookup"><span data-stu-id="ae378-110">Outputs</span></span>](#BKMK_Outputs)

 <span data-ttu-id="ae378-111">이 뷰어를 시험해 보려는 경우 [분류 마법사&#40;Excel용 데이터 마이닝 추가 기능&#41;](classify-wizard-data-mining-add-ins-for-excel.md) 마법사를 사용하여 모델을 만들고 **고급** 옵션을 사용하여 **알고리즘 매개 변수** 대화 상자에서 Microsoft 로지스틱 회귀로 알고리즘을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-111">If you want to experiment with this viewer, you can create a model using the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard, and use the **Advanced** option to change the algorithm to Microsoft Logistic Regression in the **Algorithm Parameters** dialog box.</span></span>

###  <a name="variables"></a><a name="BKMK_Variables"></a><span data-ttu-id="ae378-112">변수</span><span class="sxs-lookup"><span data-stu-id="ae378-112">Variables</span></span>
 <span data-ttu-id="ae378-113">**변수** 창에는 모델에 미치는 영향의 순서로 입력 변수의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-113">The **Variables** pane displays a list of input variables in order of their effect on the model.</span></span> <span data-ttu-id="ae378-114">**입력** 및 **출력** 컨트롤을 통해 모델을 필터링하여 표시되는 변수와 그 순서에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-114">You use the **Input** and **Output** controls to filter the model, affecting the variables that are displayed, as well as their order.</span></span>

 <span data-ttu-id="ae378-115">이 뷰어를 사용하면 고객이 자전거 구매자 범주와 비구매자 범주 중에서 어디에 속할 가능성이 큰지를 결정하는 데 가장 중요한 요인을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-115">Using this viewer, you can explore the factors that are most important in determining whether a customer more likely belongs to the bike buyer category or the non-buyer category.</span></span>

 <span data-ttu-id="ae378-116">![선택한 특성의 결과에 미치는 영향 테스트](media/dm13-neuralnet-agebuyer1.gif "선택한 특성의 결과에 미치는 영향 테스트")</span><span class="sxs-lookup"><span data-stu-id="ae378-116">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer1.gif "Testing effect on outcome of selected attributes")</span></span>

##### <a name="explore-variables"></a><span data-ttu-id="ae378-117">변수 탐색</span><span class="sxs-lookup"><span data-stu-id="ae378-117">Explore variables</span></span>

1.  <span data-ttu-id="ae378-118">처음에 **변수** 창은 현재 필터에 따라 가장 중요한 특성의 순서대로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-118">Initially, the **Variables** pane is sorted in order of the most important attributes, given the current filters.</span></span> <span data-ttu-id="ae378-119">막대의 길이는 요인의 강도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-119">The length of the bar indicates the strength of the factor.</span></span>

     <span data-ttu-id="ae378-120">이 예에서는 소득이 가장 영향력 있는 요인이고 지역이 그 다음 요인임을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-120">In the example, you can see that income is the most influential factor, followed by region.</span></span> <span data-ttu-id="ae378-121">반면에 자동차를 여러 대 소유하고 자녀가 많은 고객은 자전거를 구입할 확률이 매우 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-121">On the other hand, customers with many cars and many children are highly unlikely to buy a bike.</span></span>

2.  <span data-ttu-id="ae378-122">**변수** 창에서 **특성**의 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-122">In the **Variables** pane, click the column heading for **Attribute**.</span></span>

     <span data-ttu-id="ae378-123">특성을 기준으로 정렬하면 각 입력 열에 대해 만들어진 bin을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-123">By sorting on attribute, you can see the bins that were created for each of the input columns.</span></span> <span data-ttu-id="ae378-124">직업과 같은 불연속 값이 포함된 열은 리터럴 값에 따라 *범주화*됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-124">Columns with discrete values, such as occupation, are *binned* by the literal values.</span></span>

3.  <span data-ttu-id="ae378-125">**Age** 및 **Income**에 대해 발견된 값의 범위를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-125">Notice the ranges of values that were found for **Age** and **Income**.</span></span>

     <span data-ttu-id="ae378-126">숫자인 입력 열이 있는 경우(즉, 데이터의 전체 열이 연속 숫자 데이터 형식임) 숫자가 불연속 범위로 버킷팅 또는 범주화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-126">If any of your input columns are numbers (that is, the entire column of data is a continuous numeric data type), the numbers are bucketed, or binned, into discrete ranges.</span></span>

     <span data-ttu-id="ae378-127">소득의 경우 78.4-154.06(가장 높은 소득 범위의 경우)과 같은 그룹으로 열이 세분화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-127">For Income, the column has been subdivided into groupings such as 78.4-154.06 (for the uppermost income range).</span></span>

     <span data-ttu-id="ae378-128">![변수가 범주화되는 방식을 보기 위한 정렬](media/dm13-nn-bucketing-variables.gif "변수가 범주화되는 방식을 보기 위한 정렬")</span><span class="sxs-lookup"><span data-stu-id="ae378-128">![sort to view how variables were binned](media/dm13-nn-bucketing-variables.gif "sort to view how variables were binned")</span></span>

     <span data-ttu-id="ae378-129">다른 그룹화를 원하는 경우 모델을 작성하기 전에 [레이블 재지정&#40;SQL Server 데이터 마이닝 추가 기능&#41;](relabel-sql-server-data-mining-add-ins.md) 도구나 Excel 함수를 사용하여 새로운 소득 범주를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-129">If you want different groupings, you should use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool, or Excel functions, to create new income categories before building the model.</span></span>

4.  <span data-ttu-id="ae378-130">**유사성 있음**을 클릭하여 그래프를 기본 뷰로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-130">Click **Favors Yes** to restore the graph to the default view.</span></span>

     <span data-ttu-id="ae378-131">기본적으로 뷰는 첫 번째 결과 값에 대한 **유사성** 값을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-131">By default, the view is sorted by the value of **Favors** for the first outcome value.</span></span> <span data-ttu-id="ae378-132">**출력**에서 **값 1**과 **값 2**에 대한 새 값을 선택하여 첫 번째 및 두 번째 열에 할당되는 결과를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-132">You can change which outcomes are assigned to the first and second columns by choosing a new value for **Value 1** and **Value 2** in **Output**.</span></span>

5.  <span data-ttu-id="ae378-133">차트에서 맨 위에 있는 색이 지정된 막대 위에 마우스를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-133">Pause the mouse over the topmost colored bar in the chart.</span></span>

     <span data-ttu-id="ae378-134">*중요도* 점수, *확률* 점수 쌍 및 *리프트* 값 쌍이 포함된 도구 설명이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-134">A ToolTip appears that includes an *importance* score, a pair of *probability* scores, and a pair of *lift* values.</span></span>

    -   <span data-ttu-id="ae378-135">**중요도**는 전체 데이터 세트에서 계산되고 모든 입력이 제공된 경우에 대상 결과와 상관 관계가 가장 높은 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-135">**Importance** is calculated across the entire dataset, and identifies the attribute that, given all inputs, is most correlated with the target outcome.</span></span> <span data-ttu-id="ae378-136">뷰어에서 중요도 점수를 기준으로 차트의 값이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-136">The viewer sorts the values in the chart by the importance scores.</span></span>

    -   <span data-ttu-id="ae378-137">**확률**은 전체 데이터 집합에서 대상 결과에 대한 특성-값 쌍의 각 집합에 대해 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-137">**Probability** is calculated for each set of attribute-value pairs, for the target outcomes, across the entire data set.</span></span>

    -   <span data-ttu-id="ae378-138">**리프트**는 이 특정한 특성-값 쌍이 한 결과나 다른 결과를 촉진하는 데 얼마나 유용한지를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-138">**Lift** tells you how useful this particular attribute-value pair is for promoting one outcome or another.</span></span>

     <span data-ttu-id="ae378-139">참고: 마우스를 어느 열에 놓든 간에 도구 설명에는 동일한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-139">Note: The ToolTip contains the same information no matter whether you position the mouse over one column or the other.</span></span>

 [<span data-ttu-id="ae378-140">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ae378-140">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="ae378-141">내용</span><span class="sxs-lookup"><span data-stu-id="ae378-141">Inputs</span></span>
 <span data-ttu-id="ae378-142">**입력** 창에서 일련의 입력을 선택하여 모델에 필터로 적용할 수 있으며, 이를 통해 학습 데이터를 기반으로 결과에 대한 해당 선택의 영향을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-142">The **Inputs** pane lets you choose a set of inputs and apply that as a filter to the model, which lets you see the influence of those choices on the outcome, based on the training data</span></span>

##### <a name="explore-inputs"></a><span data-ttu-id="ae378-143">입력 탐색</span><span class="sxs-lookup"><span data-stu-id="ae378-143">Explore inputs</span></span>

1.  <span data-ttu-id="ae378-144">특정 그룹을 대상으로 한다고 가정하고 해당 그룹에서 구매에 가장 큰 영향을 미치는 요인을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-144">Suppose you want to target a particular group, and see the factors that most influence purchasing in that group.</span></span>

     <span data-ttu-id="ae378-145">**입력** 창에서 **\<All>** **특성**아래의 셀을 클릭 하 고 **Age**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-145">In the **Input** pane, click the **\<All>** cell under **Attribute**, and select **Age**.</span></span>

     <span data-ttu-id="ae378-146">**값**에 대해 가장 어린 연령 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-146">For **Value**, select the youngest age category.</span></span>

2.  <span data-ttu-id="ae378-147">특정 연령 그룹에 대해 필터링하는 경우에도 태평양 지역은 목록 위쪽에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-147">Notice that even when you filter on a particular age group, the Pacific region comes to near the top of the list.</span></span> <span data-ttu-id="ae378-148">이는 태평양 지역의 고객이 다른 지역의 고객보다 자전거를 구매할 확률이 훨씬 크기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-148">This is because customers in the Pacific region are far more likely to buy a bike than customers in other regions.</span></span>

     <span data-ttu-id="ae378-149">지역이 영향을 미칠 수 있는 요인이 아니므로 이 변수를 고려 대상에서 제거하고 다른 요인을 보기 위해 입력을 다시 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-149">Since region is not something you can influence, to remove this variable from consideration and see other factors, you can change the inputs again.</span></span>

     <span data-ttu-id="ae378-150">**입력** 창에서 **Age** 아래의 빈 셀을 클릭하고 **Region**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-150">In the **Input** pane, click the empty cell under **Age**, and select **Region**.</span></span>

     <span data-ttu-id="ae378-151">**값**에 대해 **Europe**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-151">For **Value**, select **Europe**.</span></span>

3.  <span data-ttu-id="ae378-152">입력 필터를 계속 추가하여 관심이 있는 그룹에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-152">Continue adding input filters to focus on a group of particular interest.</span></span>

     <span data-ttu-id="ae378-153">예를 들어 입력 특성에 대해 **Gender**를 추가하고 **Female**을 값으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-153">For example, for the input attribute, add **Gender**, and select **Female** as the value.</span></span>

     <span data-ttu-id="ae378-154">![선택한 특성의 결과에 미치는 영향 테스트](media/dm13-neuralnet-agebuyer2.gif "선택한 특성의 결과에 미치는 영향 테스트")</span><span class="sxs-lookup"><span data-stu-id="ae378-154">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer2.gif "Testing effect on outcome of selected attributes")</span></span>

     <span data-ttu-id="ae378-155">변수 목록이 어떻게 변경되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-155">Notice how the list of variables changes.</span></span> <span data-ttu-id="ae378-156">이제 **Income**이 대상 결과를 예측하는 데 가장 중요한 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-156">Now **Income** is the variable that is most important in predicting the target outcome.</span></span>

     <span data-ttu-id="ae378-157">입력 필터를 적용하는 순서는 결과에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-157">The order in which you apply the input filters does not affect the results.</span></span>

 [<span data-ttu-id="ae378-158">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ae378-158">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="ae378-159">출력</span><span class="sxs-lookup"><span data-stu-id="ae378-159">Outputs</span></span>
 <span data-ttu-id="ae378-160">**출력** 창에서 관심이 있는 결과를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-160">In the **Outputs** pane, you can choose the outcome that you are interested in.</span></span> <span data-ttu-id="ae378-161">신경망을 사용하면 결과 열을 원하는 만큼 지정할 수 있지만, 결과를 더 추가하면 모델이 복잡해지고 처리 시간이 훨씬 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-161">Neural networks let you specify as many outcome columns as you like, although adding more outputs adds to the complexity of the model and may require a much longer time to process.</span></span>

 <span data-ttu-id="ae378-162">두 출력을 비교하려면 해당 출력이 **예측** 또는 **예측만** 열로 지정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-162">To compare two outputs, they must have been designated as **Predict** or **Predict Only** columns.</span></span>

##### <a name="explore-outputs"></a><span data-ttu-id="ae378-163">출력 탐색</span><span class="sxs-lookup"><span data-stu-id="ae378-163">Explore outputs</span></span>

1.  <span data-ttu-id="ae378-164">**출력 특성** 목록을 사용하여 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-164">Use the **Output Attribute** list to select an attribute.</span></span>

2.  <span data-ttu-id="ae378-165">값 1 및 값 2 목록에서 두 결과를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-165">Select two outcomes from the Value 1 and Value 2 lists.</span></span> <span data-ttu-id="ae378-166">출력 특성의 이러한 두 가지 상태는 **변수** 창에서 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-166">These two states of the output attribute will be compared in the **Variables** pane.</span></span>

 [<span data-ttu-id="ae378-167">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="ae378-167">Back To Top</span></span>](#BKMK_Tabs)

## <a name="more-about-neural-network-models"></a><span data-ttu-id="ae378-168">신경망 모델에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="ae378-168">More About Neural Network Models</span></span>
 <span data-ttu-id="ae378-169">뷰어의 정보는 이 모델 유형과 관련된 저장 프로시저인 System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores를 사용하여 서버에서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-169">The information in the viewer is retrieved from the server using a stored procedure specific to this model type: System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.</span></span>

 <span data-ttu-id="ae378-170">추가 기능을 사용하여 예측 가능한 여러 특성으로 모델을 만들려면 **고급** 모델링 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ae378-170">If you want to create a model with multiple predictable attributes using the add-ins, use the **Advanced** modeling options.</span></span>

 <span data-ttu-id="ae378-171">자세한 내용은 [마이닝 구조 만들기&#40;SQL Server 데이터 마이닝 추가 기능&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) 및 [구조에 모델 추가&#40;Excel용 데이터 마이닝 추가 기능&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae378-171">For more information, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) and [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae378-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae378-172">See Also</span></span>
 [<span data-ttu-id="ae378-173">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="ae378-173">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)


