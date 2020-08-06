---
title: 예측 모델에 대 한 예측 비교 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 63cf9c001298b0d2bfd2cf35ed42485a16817fd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735644"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="25cdc-102">예측 모델에 대한 예측 비교(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="25cdc-102">Comparing Predictions for Forecasting Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="25cdc-103">이 자습서의 이전 단계에서는 다음과 같은 여러 시계열 모델을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-103">In the previous steps of this tutorial, you created multiple time series models:</span></span>  
  
-   <span data-ttu-id="25cdc-104">개별 모델 및 지역 데이터만 기반으로 하는 각 지역 및 모델 조합에 대한 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-104">Predictions for each combination of region and model, based only on data for the individual model and region.</span></span>  
  
-   <span data-ttu-id="25cdc-105">업데이트된 데이터를 기반으로 하는 각 지역에 대한 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-105">Predictions for each region, based on updated data.</span></span>  
  
-   <span data-ttu-id="25cdc-106">집계 데이터를 기반으로 하는 전세계 기준의 모든 모델에 대한 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-106">Predictions for all models on a worldwide basis, based on aggregated data.</span></span>  
  
-   <span data-ttu-id="25cdc-107">집계 모델을 기반으로 하는 북아메리카 지역의 M200 모델에 대한 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-107">Predictions for the M200 model in the North America region, based on the aggregated model.</span></span>  
  
 <span data-ttu-id="25cdc-108">시계열 예측에 대한 특징을 요약하기 위해 변경 사항을 검토하여 데이터를 확장하거나 바꾸기 위해 옵션을 사용하는 것이 결과 예측에 어떤 영향을 미쳤는지 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-108">To summarize the features for time series predictions, you will review the changes to see how the use of the options to extend or replace data affected forecasting results.</span></span>  
  
 [<span data-ttu-id="25cdc-109">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="25cdc-109">EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="25cdc-110">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="25cdc-110">REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
##  <a name="comparing-the-original-results-with-results-after-adding-data"></a><a name="bkmk_EXTEND"></a><span data-ttu-id="25cdc-111">데이터를 추가한 후 결과와 원래 결과 비교</span><span class="sxs-lookup"><span data-stu-id="25cdc-111">Comparing the Original Results with Results after Adding Data</span></span>  
 <span data-ttu-id="25cdc-112">새 데이터로 모델을 업데이트 하면 결과에 어떤 영향을 주는지 확인 하려면 태평양 지역의 M200 제품 라인에 대 한 데이터를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-112">Let's look at the data for just the M200 product line in the Pacific region, to see how updating the model with new data affects the results.</span></span> <span data-ttu-id="25cdc-113">원래 데이터 계열은 2004년 6월에 끝나고 7, 8, 9월에 대한 새 데이터를 얻었음을 기억해 두십시오.</span><span class="sxs-lookup"><span data-stu-id="25cdc-113">Remember that the original data series ended in June 2004, and we obtained new data for July, August, and September.</span></span>  
  
-   <span data-ttu-id="25cdc-114">첫 번째 열에는 추가된 새 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-114">The first column shows the new data that was added.</span></span>  
  
-   <span data-ttu-id="25cdc-115">두 번째 열에는 원래 데이터 계열을 기반으로 한 7월 이후에 대한 예측이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-115">The second column shows the forecast for July and later based on the original data series.</span></span>  
  
-   <span data-ttu-id="25cdc-116">세 번째 열에는 확장 데이터를 기반으로 한 예측이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-116">The third column shows the forecast based on the extended data.</span></span>  
  
|<span data-ttu-id="25cdc-117">**M200 Pacific**</span><span class="sxs-lookup"><span data-stu-id="25cdc-117">**M200 Pacific**</span></span>|<span data-ttu-id="25cdc-118">업데이트된 실제 판매 데이터</span><span class="sxs-lookup"><span data-stu-id="25cdc-118">Updated real sales data</span></span>|<span data-ttu-id="25cdc-119">데이터 추가 전의 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-119">Forecast before data was added</span></span>|<span data-ttu-id="25cdc-120">확장된 예측</span><span class="sxs-lookup"><span data-stu-id="25cdc-120">Extended prediction</span></span>|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|<span data-ttu-id="25cdc-121">7-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-121">7-25-2008</span></span>|<span data-ttu-id="25cdc-122">**65**</span><span class="sxs-lookup"><span data-stu-id="25cdc-122">**65**</span></span>|<span data-ttu-id="25cdc-123">32</span><span class="sxs-lookup"><span data-stu-id="25cdc-123">32</span></span>|<span data-ttu-id="25cdc-124">**65**</span><span class="sxs-lookup"><span data-stu-id="25cdc-124">**65**</span></span>|  
|<span data-ttu-id="25cdc-125">8-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-125">8-25-2008</span></span>|<span data-ttu-id="25cdc-126">**54**</span><span class="sxs-lookup"><span data-stu-id="25cdc-126">**54**</span></span>|<span data-ttu-id="25cdc-127">37</span><span class="sxs-lookup"><span data-stu-id="25cdc-127">37</span></span>|<span data-ttu-id="25cdc-128">**54**</span><span class="sxs-lookup"><span data-stu-id="25cdc-128">**54**</span></span>|  
|<span data-ttu-id="25cdc-129">9-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-129">9-25-2008</span></span>|<span data-ttu-id="25cdc-130">**61**</span><span class="sxs-lookup"><span data-stu-id="25cdc-130">**61**</span></span>|<span data-ttu-id="25cdc-131">32</span><span class="sxs-lookup"><span data-stu-id="25cdc-131">32</span></span>|<span data-ttu-id="25cdc-132">**61**</span><span class="sxs-lookup"><span data-stu-id="25cdc-132">**61**</span></span>|  
|<span data-ttu-id="25cdc-133">10-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-133">10-25-2008</span></span>|<span data-ttu-id="25cdc-134">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="25cdc-134">No data</span></span>|<span data-ttu-id="25cdc-135">36</span><span class="sxs-lookup"><span data-stu-id="25cdc-135">36</span></span>|<span data-ttu-id="25cdc-136">32</span><span class="sxs-lookup"><span data-stu-id="25cdc-136">32</span></span>|  
|<span data-ttu-id="25cdc-137">11-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-137">11-25-2008</span></span>|<span data-ttu-id="25cdc-138">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="25cdc-138">No data</span></span>|<span data-ttu-id="25cdc-139">31</span><span class="sxs-lookup"><span data-stu-id="25cdc-139">31</span></span>|<span data-ttu-id="25cdc-140">41</span><span class="sxs-lookup"><span data-stu-id="25cdc-140">41</span></span>|  
|<span data-ttu-id="25cdc-141">12-25-2008</span><span class="sxs-lookup"><span data-stu-id="25cdc-141">12-25-2008</span></span>|<span data-ttu-id="25cdc-142">데이터 없음</span><span class="sxs-lookup"><span data-stu-id="25cdc-142">No data</span></span>|<span data-ttu-id="25cdc-143">34</span><span class="sxs-lookup"><span data-stu-id="25cdc-143">34</span></span>|<span data-ttu-id="25cdc-144">32</span><span class="sxs-lookup"><span data-stu-id="25cdc-144">32</span></span>|  
  
 <span data-ttu-id="25cdc-145">확장 데이터를 사용한 예측(여기에서 굵게 표시됨)이 실제 데이터 요소를 그대로 반복하고 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-145">You will note that the forecasts using the extended data (shown here in bold) repeat the real data points exactly.</span></span> <span data-ttu-id="25cdc-146">반복은 의도된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-146">The repetition is by design.</span></span> <span data-ttu-id="25cdc-147">사용할 실제 데이터 요소가 남아 있는 한, 예측 쿼리는 실제 값을 반환하며 새로운 실제 데이터 요소를 모두 사용한 후에만 새 예측 값을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-147">As long as there are real data points to use, the prediction query will return the actual values, and output new prediction values only after the new actual data points have been used up.</span></span>  
  
 <span data-ttu-id="25cdc-148">일반적으로 알고리즘은 모델 데이터의 시작 부분 데이터보다 새 데이터의 변경에 큰 가중치를 둡니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-148">In general, the algorithm weights the changes in the new data more strongly than data from the beginning of the model data.</span></span> <span data-ttu-id="25cdc-149">그러나 이 경우 새 판매 수치는 이전 기간에 비해 겨우 20~30퍼센트의 증가만 나타내므로, 예상 판매량에는 약간의 상승만 있었으며 이후에는 예상 판매량이 다시 떨어지고 새 데이터 이전 개월 동안의 추세와 더 비슷해집니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-149">However, in this case, the new sales figures represent an increase of only 20-30 percent over the previous period, so there only was a slight uptick in projected sales, after which the sales projections drop again, more in line with the trend in the months before the new data.</span></span>  
  
##  <a name="comparing-the-original-and-cross-prediction-results"></a><a name="bkmk_REPLACE"></a><span data-ttu-id="25cdc-150">원본 및 교차 예측 결과 비교</span><span class="sxs-lookup"><span data-stu-id="25cdc-150">Comparing the Original and Cross-Prediction Results</span></span>  
 <span data-ttu-id="25cdc-151">원래 마이닝 모델에서는 지역 간 및 제품 라인 간에 큰 차이를 보였음을 기억하십시오.</span><span class="sxs-lookup"><span data-stu-id="25cdc-151">Remember that the original mining model revealed big differences between regions and between product lines.</span></span> <span data-ttu-id="25cdc-152">예를 들어 M200 모델의 판매량이 매우 높았던 반면 T1000 모델의 판매량은 모든 지역에 걸쳐 상당히 낮았습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-152">For example, sales for the M200 model were very strong, while sales for the T1000 model were fairly low across all regions.</span></span> <span data-ttu-id="25cdc-153">또한 일부 계열에는 많은 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-153">Moreover, some series didn't have much data.</span></span> <span data-ttu-id="25cdc-154">계열이 비정형 것은 아닙니다. 즉, 동일한 시작점이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-154">Series were ragged, meaning they didn't have the same starting point.</span></span>  
  
 <span data-ttu-id="25cdc-155">![M200 및 T1000 수량을 예측하는 계열](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 및 T1000 수량을 예측하는 계열")</span><span class="sxs-lookup"><span data-stu-id="25cdc-155">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="25cdc-156">그렇다면 원래 데이터 집합 대신 전 세계 판매를 기반으로 하는 일반 모델 기반 예측 시에는 예측이 어떻게 바뀌었습니까?</span><span class="sxs-lookup"><span data-stu-id="25cdc-156">So how did the predictions change when you made your projections based on the general model, which was based on world-wide sales, rather than the original data sets?</span></span> <span data-ttu-id="25cdc-157">정보가 손실되거나 예측이 왜곡되지 않도록 하기 위해, 테이블에 결과를 저장하고 예측 테이블을 기록 데이터 테이블에 조인한 다음 기록 데이터 집합 및 예측 집합의 그래프를 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-157">To assure yourself that you have not lost any information or skewed the predictions, you can save the results to a table, join the table of predictions to the table of historical data, and then graph the two sets of historical data and predictions.</span></span>  
  
 <span data-ttu-id="25cdc-158">다음 다이어그램은 M200 제품 라인 하나만을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-158">The following diagram is based on just one product line, the M200.</span></span> <span data-ttu-id="25cdc-159">그래프에서는 집계 마이닝 모델을 사용하는 예측에 대해 초기 마이닝 모델의 예측을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-159">The graph compares the predictions from the initial mining model against the predictions using the aggregated mining model.</span></span>  
  
 <span data-ttu-id="25cdc-160">![예측을 비교하는 Excel 차트](../../2014/tutorials/media/m200-predictions-compared.gif "예측을 비교하는 Excel 차트")</span><span class="sxs-lookup"><span data-stu-id="25cdc-160">![Excel chart comparing predictions](../../2014/tutorials/media/m200-predictions-compared.gif "Excel chart comparing predictions")</span></span>  
  
 <span data-ttu-id="25cdc-161">이 다이어그램을 통해 집계 마이닝 모델에서 개별 데이터 계열의 변동폭을 최소화하면서 값의 전체 범위 및 추세가 유지됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-161">From this diagram, you can see that the aggregated mining model preserves the overall range and trends in values while minimizing the fluctuations in the individual data series.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="25cdc-162">결론</span><span class="sxs-lookup"><span data-stu-id="25cdc-162">Conclusion</span></span>  
 <span data-ttu-id="25cdc-163">예측에 사용할 수 있는 시계열 모델을 만들고 사용자 지정하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-163">You have learned how to create and to customize a time series model that can be used for forecasting.</span></span>  
  
 <span data-ttu-id="25cdc-164">EXTEND_MODEL_CASES 매개 변수를 사용하여 새 데이터를 추가하고 예측을 생성함으로써 시계열 모델을 다시 처리하지 않고 업데이트하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-164">You have learned to update your time series models without having to reprocess them, by adding new data and creating predictions using the parameter, EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="25cdc-165">REPLACE_MODEL_CASES 매개 변수를 사용하여 다른 데이터 계열에 모델을 적용함으로써 교차 예측에 사용할 수 있는 모델을 만드는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="25cdc-165">You have learned to create models that can be used for cross-prediction, by using the REPLACE_MODEL_CASES parameter and applying the model to a different data series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25cdc-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25cdc-166">See Also</span></span>  
 <span data-ttu-id="25cdc-167">[Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="25cdc-167">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="25cdc-168">시계열 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="25cdc-168">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
