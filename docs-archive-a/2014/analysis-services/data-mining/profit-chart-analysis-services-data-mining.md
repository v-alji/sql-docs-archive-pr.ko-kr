---
title: 수익 차트 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
author: minewiskan
ms.author: owend
ms.openlocfilehash: a38a1d5062f53de4be9129c2305d8d3c84593f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734596"
---
# <a name="profit-chart-analysis-services---data-mining"></a><span data-ttu-id="f624f-102">수익 차트(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="f624f-102">Profit Chart (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="f624f-103">수익 차트는 마이닝 모델 사용과 관련된 예상 수익성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-103">A profit chart displays the estimated profitability associated with using a mining model.</span></span> <span data-ttu-id="f624f-104">예를 들어 비즈니스 시나리오에서 회사가 연락 해야 하는 고객을 모델에서 예측 하는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-104">For example, let's assume your model predicts which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="f624f-105">이 경우 수익 차트 정보에 타겟 메일링 캠페인 수행 비용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-105">In that case, you would add to the profit chart information about the cost of conducting the targeted mailing campaign.</span></span> <span data-ttu-id="f624f-106">그런 다음 완성된 차트에서 고객에게 무작위로 연락하는 시나리오와 비교하여 고객을 올바르게 타게팅할 때 예상되는 수익을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-106">Then, in the completed chart, you can see the estimated profit if customers are correctly targeted, as compared to randomly contacting customers.</span></span>  
  
## <a name="build-a-profit-chart"></a><span data-ttu-id="f624f-107">수익 차트 작성</span><span class="sxs-lookup"><span data-stu-id="f624f-107">Build a Profit Chart</span></span>  
 <span data-ttu-id="f624f-108">수익 차트는 리프트 차트와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-108">A profit chart is similar to a lift chart.</span></span> <span data-ttu-id="f624f-109">가장 먼저 리프트 차트를 만든 다음 비용 및 수익 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-109">You start by creating a lift chart, and then add in the cost and profit information.</span></span>  
  
 <span data-ttu-id="f624f-110">수익 차트를 추가하려면 기존 모델이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-110">To build a profit chart, you must have an existing model.</span></span>  
  
 <span data-ttu-id="f624f-111">이 예제에서는 타겟 메일링 의사 결정 트리 모델을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-111">For this example, we used the Targeted Mailing decision tree model.</span></span> <span data-ttu-id="f624f-112">이 모델은 자전거를 구매할 가능성이 높은 고객을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-112">The model identifies customers who are likely to buy a bike.</span></span> <span data-ttu-id="f624f-113">수익 극대화를 위해 몇 명의 고객을 타게팅해야 하는지 파악하기 위해 **수익 차트** 를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-113">You can apply the **Profit Chart** to determine how many of your customers to target to maximize your profit.</span></span>  
  
 <span data-ttu-id="f624f-114">예제 모델이 없는 경우 [기본 데이터 마이닝 자습서](../../tutorials/basic-data-mining-tutorial.md)를 사용 하 여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-114">If you don't have the sample model, you can create it using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
1.  <span data-ttu-id="f624f-115">마이닝 정확도 차트 작성기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-115">Open the mining accuracy chart builder.</span></span>  
  
    -   <span data-ttu-id="f624f-116">SQL Server Management Studio에서 모델을 마우스 오른쪽 단추로 클릭하고 **리프트 차트 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-116">In SQL Server Management Studio, right-click the model, and select **View Lift Chart**.</span></span>  
  
    -   <span data-ttu-id="f624f-117">SQL Server Data Tools에서 모델을 만든 프로젝트를 열고 **마이닝 정확도 차트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-117">In SQL Server Data Tools, open the project in which you created the model, and click the **Mining Accuracy Chart** tab.</span></span>  
  
2.  <span data-ttu-id="f624f-118">**입력 선택** 탭에서 모델을 선택하고 예측 가능한 특성 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-118">In **the Input Selection** tab, select the model and choose the predictable attribute value.</span></span>  
  
     <span data-ttu-id="f624f-119">이 시나리오에서는 한 가지 값, 즉, [Bike Buyer] =1에 대한 정확한 예측 확률에만 관심이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-119">For this particular scenario, you are interested only in the profitability of accurately predicting one value: [Bike Buyer] =1.</span></span>  
  
     <span data-ttu-id="f624f-120">하지만 다른 시나리오에서는 거짓 값도 정확하게 예측해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-120">However, there are other scenarios in which you are equally interested in predicting false values correctly.</span></span> <span data-ttu-id="f624f-121">예를 들어 의료 진단 테스트의 경우 거짓 긍정의 비용이 매우 크기 때문에 예측 확률에 거짓 긍정과 거짓 부정을 동등하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-121">For example, the cost of a false positive on a medical diagnostic test can be significant and needs to be factored into the profitability of the prediction, as does the cost of false negatives.</span></span> <span data-ttu-id="f624f-122">이러한 시나리오에서는 모든 결과를 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-122">In such scenarios, you would measure all outcomes.</span></span>  
  
3.  <span data-ttu-id="f624f-123">테스트할 데이터 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-123">Select a data set for testing.</span></span> <span data-ttu-id="f624f-124">이 예에서는 테스트 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-124">For this example, select the testing data set.</span></span>  
  
4.  <span data-ttu-id="f624f-125">이제 **리프트 차트** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-125">Now click the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="f624f-126">리프트 차트가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-126">A lift chart is automatically generated.</span></span>  
  
5.  <span data-ttu-id="f624f-127">이 차트를 수익 차트로 변경하려면 **차트 종류** 목록에서 **수익 차트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-127">To change this to a profit chart, select **Profit Chart** from the **Chart type** list.</span></span>  
  
6.  <span data-ttu-id="f624f-128">차트 종류로 수익 차트로 선택하면 **수익 차트 설정** 대화 상자가 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-128">As soon as you choose profit chart as the chart type, the **Profit Chart Setting** dialog box automatically opens.</span></span>  
  
     <span data-ttu-id="f624f-129">이 대화 상자에서 타겟 메일링 캠페인과 연관된 비용 및 이익을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-129">This dialog box helps you specify the costs and benefits associated with a targeted mailing campaign.</span></span> <span data-ttu-id="f624f-130">이러한 예제의 차트에는 다음 값을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-130">For the chart shown in these examples, we used the following values:</span></span>  
  
    |<span data-ttu-id="f624f-131">설정</span><span class="sxs-lookup"><span data-stu-id="f624f-131">Setting</span></span>|<span data-ttu-id="f624f-132">값</span><span class="sxs-lookup"><span data-stu-id="f624f-132">Value</span></span>|<span data-ttu-id="f624f-133">주석</span><span class="sxs-lookup"><span data-stu-id="f624f-133">Comments</span></span>|  
    |-------------|-----------|--------------|  
    |<span data-ttu-id="f624f-134">**표본의**</span><span class="sxs-lookup"><span data-stu-id="f624f-134">**Population**</span></span>|<span data-ttu-id="f624f-135">20,000</span><span class="sxs-lookup"><span data-stu-id="f624f-135">20,000</span></span>|<span data-ttu-id="f624f-136">총 대상 모집단에 대한 값 설정</span><span class="sxs-lookup"><span data-stu-id="f624f-136">Set the value for the total target population</span></span><br /><br /> <span data-ttu-id="f624f-137">데이터베이스에 많은 고객이 있을 수 있지만 발송 비용을 절약하려면 응답할 가능성이 가장 높은 고객 20,000명만 타게팅해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-137">Your database might contain many customers, but to save on mailing expenses you might choose to target only the 20,000 customers who are most likely to respond.</span></span> <span data-ttu-id="f624f-138">이 목록은 예측 쿼리를 실행하고 예측 모델별로 확률 결과를 정렬하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-138">You can get this list by running a prediction query and sorting by the probability output by the predictive model.</span></span>|  
    |<span data-ttu-id="f624f-139">**고정 비용**</span><span class="sxs-lookup"><span data-stu-id="f624f-139">**Fixed cost**</span></span>|<span data-ttu-id="f624f-140">500</span><span class="sxs-lookup"><span data-stu-id="f624f-140">500</span></span>|<span data-ttu-id="f624f-141">20,000명의 고객들에게 타겟 메일링 캠페인을 한 번 제공할 때 드는 비용을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-141">Enter the one-time cost of setting up a targeted mailing campaign for 20,000 people.</span></span> <span data-ttu-id="f624f-142">여기에는 인쇄 또는 전자 메일 캠페인 설정 비용이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-142">This might include printing, or the cost of setting up an e-mail campaign.</span></span>|  
    |<span data-ttu-id="f624f-143">**개별 비용**</span><span class="sxs-lookup"><span data-stu-id="f624f-143">**Individual cost**</span></span>|<span data-ttu-id="f624f-144">3</span><span class="sxs-lookup"><span data-stu-id="f624f-144">3</span></span>|<span data-ttu-id="f624f-145">타겟 메일링 캠페인의 단위 비용을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-145">Enter the per-unit cost for the targeted mailing campaign.</span></span><br /><br /> <span data-ttu-id="f624f-146">모델에서 예측한 적절한 잠재 고객 수에 따라 20,000 이하의 숫자를 이 금액에 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-146">This amount will be multiplied by a number equal to or less than 20000, depending on how many customers the model predicts are good prospects.</span></span>|  
    |<span data-ttu-id="f624f-147">**개인 당 수익**</span><span class="sxs-lookup"><span data-stu-id="f624f-147">**Revenue per individual**</span></span>|<span data-ttu-id="f624f-148">400</span><span class="sxs-lookup"><span data-stu-id="f624f-148">400</span></span>|<span data-ttu-id="f624f-149">성공적인 결과에서 예상할 수 있는 수익 또는 수입 금액을 나타내는 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-149">Enter a value that represents the amount of profit or income that can be expected from a successful result.</span></span> <span data-ttu-id="f624f-150">이 경우 카탈로그를 메일로 보내는 경우에는 액세서리 또는 자전거 $400 평균을 구입 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-150">In this case, we'll assume that mailing a catalog results in purchase of accessories or bikes averaging $400.</span></span><br /><br /> <span data-ttu-id="f624f-151">이 금액은 높은 확률 사례와 관련된 총 수익을 산출하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-151">This amount will be used to project the total profit associated with high probability cases.</span></span>|  
  
7.  <span data-ttu-id="f624f-152">필요한 매개 변수를 설정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-152">After you have set the required parameters, click **OK**.</span></span>  
  
8.  <span data-ttu-id="f624f-153">차트가 업데이트되면서 수익 곡선이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-153">The chart updates to show the profit curve.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="f624f-154">수익 차트 이해</span><span class="sxs-lookup"><span data-stu-id="f624f-154">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="f624f-155">다음 다이어그램에서는 이러한 매개 변수에 기반한 차트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-155">The following diagram shows the chart that was based on these parameters.</span></span> <span data-ttu-id="f624f-156">차트의 Y축은 수익을 나타내고 X축은 회사에서 타겟 메일링 캠페인으로 연락한 고객의 백분율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-156">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the customers who were contacted by the targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="f624f-157">여기서 볼 수 있듯이, 수익 차트가 동일한 불연속 특성을 예측하는 경우 수익 차트를 사용하여 여러 모델을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-157">As shown here, you can use a profit chart to compare multiple models, as long as they all predict the same discrete attribute.</span></span>  
  
 <span data-ttu-id="f624f-158">![3개의 모델을 비교하는 수익 차트](../media/dm14-profitchartupdated.gif "3개의 모델을 비교하는 수익 차트")</span><span class="sxs-lookup"><span data-stu-id="f624f-158">![a profit chart comparing three models](../media/dm14-profitchartupdated.gif "a profit chart comparing three models")</span></span>  
  
 <span data-ttu-id="f624f-159">차트의 회색 수직선을 보십시오.</span><span class="sxs-lookup"><span data-stu-id="f624f-159">Notice the gray vertical line in the chart.</span></span> <span data-ttu-id="f624f-160">선을 클릭하고 끌면 도구 설명에 해당 지점에 포함된 타겟 모집단의 비율이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-160">As you click and drag the line, the ToolTip display the percentage of the target population that is included under the curve at that point.</span></span>  
  
 <span data-ttu-id="f624f-161">이 선을 끌면 **마이닝 범례** 가 업데이트되면서 세로 회색 선의 모집단 비율과 관련된 백분율 값, 수익 점수, 예측 확률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-161">The **Mining Legend** is also updated as you drag the line, to display the percentage value, a profit score, and the predict probability that is associated with the population percentage at the vertical gray line.</span></span>  
  
 <span data-ttu-id="f624f-162">예를 들어 이 모델을 사용하여 프로모션 자료를 발송할 대상을 결정하려는 경우 예측 확률을 기준으로 모집단의 25%만 타게팅할 것을 결정할 수 있습니다. 하지만 차트의 수익 곡선 아래의 영역이 40~70%에서 가장 높다는 것은 더 많은 사람들에게 발송할 경우 수익을 극대화할 수 있음을 나타내며, 전체 응답자 비율이 작을 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-162">For example, if you were using this model to decide who to send your promotional material to, you might decide to target 25% of the population, based on the predict probabilities, However, the area under the profit curve of the chart is greatest between 40 and 70 percent, indicating that by mailing to more people, you can maximize your return, even if a smaller overall percentage responds.</span></span>  
  
## <a name="saving-charts"></a><span data-ttu-id="f624f-163">차트 저장</span><span class="sxs-lookup"><span data-stu-id="f624f-163">Saving Charts</span></span>  
 <span data-ttu-id="f624f-164">정확도 차트 또는 수익 차트를 만들 경우 서버에 개체가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-164">When you create an accuracy chart or profit chart, no objects are created on the server.</span></span> <span data-ttu-id="f624f-165">대신, 기존 모델에 쿼리가 실행되고 뷰어에 결과가 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-165">Instead, queries are executed against an existing model and the results are rendered in the viewer.</span></span> <span data-ttu-id="f624f-166">결과를 저장해야 할 경우 차트 또는 결과를 Excel 또는 다른 파일로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-166">If you need to save the results, you must copy either the chart or the results to Excel or another file.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f624f-167">관련 내용</span><span class="sxs-lookup"><span data-stu-id="f624f-167">Related Content</span></span>  
 <span data-ttu-id="f624f-168">다음 항목에는 정확도 차트를 만들고 사용하는 방법에 대해 보다 자세한 내용이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-168">The following topics contain more information about how you can build and use accuracy charts.</span></span>  
  
|<span data-ttu-id="f624f-169">토픽</span><span class="sxs-lookup"><span data-stu-id="f624f-169">Topics</span></span>|<span data-ttu-id="f624f-170">링크</span><span class="sxs-lookup"><span data-stu-id="f624f-170">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="f624f-171">타겟 메일링 모델에 대한 리프트 차트를 만드는 방법을 보여 주는 연습을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-171">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="f624f-172">기본 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="f624f-172">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="f624f-173">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-173">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|<span data-ttu-id="f624f-174">관련 차트 종류에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-174">Explains related chart types.</span></span>|[<span data-ttu-id="f624f-175">리프트 차트&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-175">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="f624f-176">분류표&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-176">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="f624f-177">산점도&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-177">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="f624f-178">마이닝 모델 및 마이닝 구조에 대한 교차 유효성 검사를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-178">Describes cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="f624f-179">교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-179">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="f624f-180">리프트 차트 및 기타 정확도 차트를 만드는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f624f-180">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="f624f-181">테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-181">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f624f-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f624f-182">See Also</span></span>  
 <span data-ttu-id="f624f-183">[데이터 마이닝&#41;&#40;테스트 및 유효성 검사](testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f624f-183">[Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md) </span></span>  
 [<span data-ttu-id="f624f-184">리프트 차트를 사용하여 정확도 테스트&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="f624f-184">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
  
