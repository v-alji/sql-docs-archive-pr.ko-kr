---
title: 예측 모델 탐색 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 86bd6371a8d32c53c68351aaff36a317f7433ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735643"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="13392-102">예측 모델 탐색(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="13392-102">Exploring the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="13392-103">이제 예측 마이닝 모델을 작성 했으므로 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭을 사용 하 여 결과를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-103">Now that you have built the forecasting mining model, you can explore the results by using the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="13392-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]시계열 뷰어에는 **차트** 와 **모델**의 두 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer contains two tabs: **Charts** and **Model**.</span></span>  
  
 <span data-ttu-id="13392-105">또한 모든 모델에 Microsoft 일반 트리 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-105">Additionally, you can use the Microsoft Generic Tree Viewer with all models.</span></span> <span data-ttu-id="13392-106">각 뷰에는 시계열 모델의 조금씩 다른 그림 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-106">Each view presents a slightly different picture of the information in the time series model.</span></span>  
  
-   [<span data-ttu-id="13392-107">차트 탭</span><span class="sxs-lookup"><span data-stu-id="13392-107">Charts Tab</span></span>](#bkmk_Charts)  
  
-   [<span data-ttu-id="13392-108">모델 탭</span><span class="sxs-lookup"><span data-stu-id="13392-108">Model Tab</span></span>](#bkmk_Model)  
  
-   [<span data-ttu-id="13392-109">Microsoft 일반 콘텐츠 뷰어</span><span class="sxs-lookup"><span data-stu-id="13392-109">Microsoft Generic Content Viewer</span></span>](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a><span data-ttu-id="13392-110">차트 탭</span><span class="sxs-lookup"><span data-stu-id="13392-110">Charts Tab</span></span>  
 <span data-ttu-id="13392-111">시계열 뷰어의 **차트** 탭은 [!INCLUDE[msCoName](../includes/msconame-md.md)] 기록 데이터 및 예측을 포함 하 여 각 계열을 그래픽으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-111">The **Charts** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer graphically shows you each of the series, including historical data and predictions.</span></span> <span data-ttu-id="13392-112">시계열 그래프의 각 선은 제품, 지역 및 예측 가능한 특성의 고유한 조합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13392-112">Each line in the time series graph represents a unique combination of product, region, and predictable attribute.</span></span>  
  
 <span data-ttu-id="13392-113">뷰어 오른쪽의 범례에는 드롭다운 목록에서 선택한 항목을 기준으로 사용 가능한 시계열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-113">The legend on the right side of the viewer lists the time series that available, based on the selections in the drop-down list.</span></span> <span data-ttu-id="13392-114">범례에서 확인란을 선택하거나 확인란의 선택을 취소하여 그래프에 표시되는 시계열을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-114">You can select and clear the check boxes in the legend to control which time series displays in the graph.</span></span>  
  
 <span data-ttu-id="13392-115">각 시계열에 사용된 색상이나 차트의 지점에 값이 표시되는지 여부와 같은 표시 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-115">You can also change the display options, such as the colors used for each time series, or whether values are displayed at points in the chart.</span></span>  
  
#### <a name="to-select-a-time-series"></a><span data-ttu-id="13392-116">시계열을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="13392-116">To select a time series</span></span>  
  
1.  <span data-ttu-id="13392-117">**마이닝 모델 뷰어** 탭의 **차트** 탭 (표시 되지 않는 경우)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-117">Click the **Charts** tab of the **Mining Model Viewer** tab, if it is not visible.</span></span>  
  
2.  <span data-ttu-id="13392-118">차트 뷰의 오른쪽에 있는 드롭다운 목록을 클릭한 다음 확인란을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-118">Click the drop-down list to the right of the chart view, and select all the check boxes.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="13392-119">이제 차트에는 24개의 다른 계열 선이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-119">The chart should now contain 24 different series lines.</span></span>  
  
3.  <span data-ttu-id="13392-120">차트 오른쪽에 있는 확인란에서 확인란의 선택을 취소하여 Amount를 기준으로 한 모든 계열에 대한 선을 임시로 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="13392-120">In the check boxes to the right of the chart, clear the boxes to temporarily hide the lines for all series that are based on Amount.</span></span>  
  
     <span data-ttu-id="13392-121">이제 R750 및 R250 자전거와 관련된 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-121">Now, clear the check boxes related to the R750 and R250 bicycles.</span></span>  
  
     <span data-ttu-id="13392-122">이제 차트에 다음 6개 계열 선이 포함되므로 M200 및 T1000 자전거에 대한 추세를 보다 쉽게 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-122">The chart now contains just the following six series lines, so that can you more easily compare trends for the M200 and T1000 bicycles.</span></span>  
  
    -   <span data-ttu-id="13392-123">**M200 유럽: 수량**</span><span class="sxs-lookup"><span data-stu-id="13392-123">**M200 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="13392-124">**M200 북아메리카: Quantity**</span><span class="sxs-lookup"><span data-stu-id="13392-124">**M200 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="13392-125">**M200 태평양: 수량**</span><span class="sxs-lookup"><span data-stu-id="13392-125">**M200 Pacific: Quantity**</span></span>  
  
    -   <span data-ttu-id="13392-126">**T1000 유럽: 수량**</span><span class="sxs-lookup"><span data-stu-id="13392-126">**T1000 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="13392-127">**T1000 북아메리카: Quantity**</span><span class="sxs-lookup"><span data-stu-id="13392-127">**T1000 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="13392-128">**T1000 Pacific:Quantity**</span><span class="sxs-lookup"><span data-stu-id="13392-128">**T1000 Pacific: Quantity**</span></span>  
  
 <span data-ttu-id="13392-129">![M200 및 T1000 수량을 예측하는 계열](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 및 T1000 수량을 예측하는 계열")</span><span class="sxs-lookup"><span data-stu-id="13392-129">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="13392-130">이 뷰어에 표시되는 차트에는 기록 데이터 및 예측 데이터가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-130">The chart that is displayed in this viewer includes both historical and predicted data.</span></span> <span data-ttu-id="13392-131">예측 데이터는 기록 데이터와 구분하기 위해 음영 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-131">Predicted data is shaded to differentiate it from historical data.</span></span> <span data-ttu-id="13392-132">다른 계열을 쉽게 비교하기 위해 그래프에서 각 선과 관련된 색상을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-132">To make it easier to compare different series, you can also change the colors associated with each line in the graph.</span></span> <span data-ttu-id="13392-133">자세한 내용은 [데이터 마이닝 뷰어에서 사용되는 색 변경](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13392-133">For more information, see [Change the Colors Used in the Data Mining Viewer](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).</span></span>  
  
 <span data-ttu-id="13392-134">추세 선으로부터 모든 지역의 총 판매액이 대개 12개월 간격으로 증가하여 12월에 최고를 기록하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-134">From the trend lines, you can see that total sales for all regions are generally increasing, with a peak every 12 months in December.</span></span> <span data-ttu-id="13392-135">또한 차트로부터 T1000 자전거에 대한 데이터가 다른 제품 계열의 데이터보다 훨씬 늦게 시작하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-135">From the chart, you can also see that the data for the T1000 bicycle starts much later than the data for the other product series.</span></span> <span data-ttu-id="13392-136">이는 제품이 새 제품이기 때문이지만 이 계열은 훨씬 적은 데이터를 기준으로 하고 있으므로 예측이 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-136">That is because it is a newer product, but because this series is based on much less data, the predictions might not be as accurate.</span></span>  
  
 <span data-ttu-id="13392-137">기본적으로 각 시계열에 대해 다섯 가지 예측 단계가 점선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-137">By default, five prediction steps are shown for each time series, displayed as dotted lines.</span></span> <span data-ttu-id="13392-138">이 값을 변경하여 더 많거나 적은 예측을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-138">You can change this value to view more or fewer predictions.</span></span> <span data-ttu-id="13392-139">오차 막대를 차트에 추가하여 예측에 대한 표준 편차를 그래픽으로 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-139">You can also graphically view the standard deviation for the predictions by adding error bars to the chart.</span></span>  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a><span data-ttu-id="13392-140">차트 뷰에서 예측 및 표시 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="13392-140">To change prediction and display options in the Chart view</span></span>  
  
1.  <span data-ttu-id="13392-141">**예측 단계** 에 대 한 값을 **5** 에서 **10**으로 늘리고 다시 **6**으로 변경해 보세요.</span><span class="sxs-lookup"><span data-stu-id="13392-141">Try changing the value for **Prediction Steps** gradually, increasing it from **5** to **10**, and then back to **6**.</span></span>  
  
     <span data-ttu-id="13392-142">기록 데이터에 큰 변동이 있는 경우 예측 수를 증가시키는 동안 변동은 대개 반복되거나 증폭됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-142">When the historical data has large fluctuations, the fluctuations tend to be repeated or even amplified as you increase the number of predictions.</span></span> <span data-ttu-id="13392-143">이때 기록 데이터가 크게 증가한 원인을 알아본 다음 이러한 결과를 허용할지 여부를 결정하거나 원본 데이터의 수정 사항을 찾거나 모델을 다듬기 위해 일부 조사가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-143">You probably need to do some research at this point, to understand the cause of the big increase in the historical data and then decide whether to accept these results, seek some kind of correction in the source data, or apply some kind of smoothing in the model.</span></span>  
  
2.  <span data-ttu-id="13392-144">**편차 표시** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-144">Select the **Show Deviations** check box.</span></span>  
  
     <span data-ttu-id="13392-145">이 옵션은 각 예측 값에 대한 예측 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-145">This option displays the estimated error for each predicted value.</span></span>  
  
3.  <span data-ttu-id="13392-146">X축 눈금을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-146">Note the scale of the X-axis.</span></span> <span data-ttu-id="13392-147">기록 데이터 및 예측 데이터의 변화는 모두 항상 백분율로 표시되지만 실제 값은 그래프 상의 모든 값에 맞춰 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-147">The changes over both historical and predicted data are always expressed as a percentage, but the actual values are adjusted automatically to fit all values onto the graph.</span></span> <span data-ttu-id="13392-148">따라서 모델을 비교할 때 시각적인 것에만 의존하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-148">Therefore you need to be careful when comparing models to not rely on visuals alone.</span></span> <span data-ttu-id="13392-149">정확한 값 이나 예측의 백분율 증가 및 값을 얻으려면 점선 또는 실선 위에 마우스를 놓습니다. 또는 선을 클릭 하 여 **마이닝 범례의**값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-149">To get the exact value, or the percentage increase and value for predictions, pause the mouse over the dotted line or solid lines, or click the lines to view the values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="13392-150">**팁**: **마이닝 범례가** 표시 되지 않는 경우 **모델** 뷰로 전환 하 고 노드를 마우스 오른쪽 단추로 클릭 한 다음 **범례 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-150">**Tip**: If the **Mining Legend** is not visible, switch to **Model** view, right-click any node, and select **Show Legend**.</span></span>  
  
 <span data-ttu-id="13392-151">이러한 추세를 확인한 뒤에 일부 계열의 데이터 부족이 우려되고 모델별 또는 지역별 판매의 평균을 구하여 보다 신뢰할 수 있는 예측 결과를 얻을 수 있는지 궁금해 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-151">From looking at these trends, you are concerned about the lack of data for some of the series, and wonder if you might get more reliable predictions by averaging sales by model, or perhaps averaging sales by region.</span></span> <span data-ttu-id="13392-152">이 자습서의 이후 단원에서 이 방법에 대해 알아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="13392-152">You will explore this approach in a later lesson in this tutorial.</span></span>  
  
 [<span data-ttu-id="13392-153">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="13392-153">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a><span data-ttu-id="13392-154">모델 탭</span><span class="sxs-lookup"><span data-stu-id="13392-154">Model Tab</span></span>  
 <span data-ttu-id="13392-155">**Model** [!INCLUDE[msCoName](../includes/msconame-md.md)] 데이터 마이닝 디자이너에서 시계열 뷰어의 모델 탭을 사용 하 여 예측 모델을 트리 그래프 형식으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-155">The **Model** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer in Data Mining Designer lets you view the forecasting model in the form of a tree graph.</span></span>  
  
 <span data-ttu-id="13392-156">우선 데이터는 유럽, 북미 및 태평양(Europe, North America, Pacific)의 세 지역에서 여러 제품 라인(T1000 등)의 판매에 대한 금액과 수량(Amount, Quantity)의 두 가지 측정값을 나타내므로, 구축한 모델에는 실제 24개의 서로 다른 트리가 포함되며 각 트리는 지역, 제품 및 예측 가능한 특성의 서로 다른 조합에 대한 판매 패턴 모델을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13392-156">First, notice that because your data describes two different measures (Amount and Quantity) for sales of multiple product lines (T1000, etc.) in three different regions (Europe, North America, and Pacific), the model that you built actually contains 24 different trees, each tree representing a model of the sales patterns for a different combination of region, product, and predictable attribute.</span></span>  
  
 <span data-ttu-id="13392-157">**모델** 탭의 **트리** 드롭다운 목록에서 계열을 선택 하 여 보려는 제품 라인, 지역 및 판매 메트릭의 조합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-157">You can choose which combination of product line, region, and sales metric you want to view by selecting a series from the **Tree** dropdown list on the **Model** tab.</span></span>  
  
 <span data-ttu-id="13392-158">모델을 트리로 표시함으로써 얻을 수 있는 정보를 알아보기 위해</span><span class="sxs-lookup"><span data-stu-id="13392-158">So what can you learn from viewing the model as a tree?</span></span> <span data-ttu-id="13392-159">예를 들어 트리에서 여러 수준을 포함 하는 모델과 단일 노드를 포함 하는 두 개의 모델을 비교 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-159">As an example, let's compare two models, one that has several levels in the tree, and one that has a single node.</span></span>  
  
-   <span data-ttu-id="13392-160">트리 그래프에 단일 노드가 포함된 경우 모델에서 확인된 추세가 시간에 따라 거의 같은 유형을 지님을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-160">When a tree graph contains a single node, it means the trend found in the model is mostly homogenous over time.</span></span> <span data-ttu-id="13392-161">**모두**레이블이 지정 된 단일 노드를 사용 하 여 입력 변수와 결과 간의 관계를 설명 하는 수식을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-161">You can use this single node, labeled **All**, to view the formula that describes the relationship between the input variables and the outcome.</span></span>  
  
-   <span data-ttu-id="13392-162">시계열의 트리 그래프에 여러 분기가 있는 경우 검색된 시계열이 너무 복잡하여 단일 수식으로 나타낼 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-162">When a tree graph for a time series has multiple branches, it means the time series that was detected is too complex to be represented as a single equation.</span></span> <span data-ttu-id="13392-163">대신 트리 그래프에는 트리의 *분할*을 일으킨 조건으로 레이블이 지정 된 분기가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-163">Instead, the tree graph might contain multiple branches, each branch labeled with the conditions that caused the tree to *split*.</span></span> <span data-ttu-id="13392-164">트리가 분할될 때 각 분기는 서로 다른 시간 세그먼트를 나타내며 내부의 추세는 단일 수식으로 표현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-164">When the tree splits, each branch represents a different segment of time, inside which the trend can be described as a single equation.</span></span>  
  
     <span data-ttu-id="13392-165">예를 들어 차트 그래프를 살펴보면 9 월에 시작 하 여 판매 볼륨에서 갑자기 이동 하는 것을 확인 하 고 연말 휴일을 계속 진행 하면 **모델** 뷰로 전환 하 여 추세가 변경 된 정확한 날짜를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-165">For example, if you look at the chart graph and see a sudden jump in sales volume starting sometime in September and continuing through a year-end holiday, you can switch to the **Model** view to see the exact date where the trend changed.</span></span> <span data-ttu-id="13392-166">"9 월 전" 및 "9 월 이후"를 나타내는 트리의 분기는 서로 다른 수식을 포함 합니다. 즉, 분할에 대 한 판매 추세를 수학적으로 설명 하는 수식과 년 9 월을 기준으로 9 월 판매 추세를 설명 하는 다른 수식이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-166">The branches in the tree that represent "before September" and "after September" would contain different formulas: one formula that mathematically describes the sales trends up to the split, and another formula that describes sales trends for September through the year-end holiday.</span></span>  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a><span data-ttu-id="13392-167">시계열 모델의 의사 결정 트리를 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="13392-167">To explore the decision tree for a time series model</span></span>  
  
1.  <span data-ttu-id="13392-168">뷰어의 **모델** 탭에 있는 **트리** 목록에서 **T1000 유럽: Amount** series를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-168">In the **Tree** list on the **Model** tab of the viewer, select the **T1000 Europe: Amount** series.</span></span>  
  
     <span data-ttu-id="13392-169">레이블이 **All**인 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-169">Click the node labeled **All**.</span></span>  
  
     <span data-ttu-id="13392-170">**All** 노드에 대해 표시 되는 도구 설명에는 전체 계열의 사례 수, 데이터 분석에서 파생 된 시계열 방정식 등의 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-170">For an **All** node, the ToolTip that appears includes information such as, the number of cases in the entire series, and time series equations derived from analysis of the data.</span></span>  
  
2.  <span data-ttu-id="13392-171">**마이닝 범례가** 표시 되지 않는 경우 노드를 마우스 오른쪽 단추로 클릭 하 고 **범례 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-171">If the **Mining Legend** is not visible, right-click the node and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="13392-172">**마이닝 범례** 는 도구 설명에 있는 것과 동일한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-172">The **Mining Legend** provides much the same information that is in the Tooltip.</span></span> <span data-ttu-id="13392-173">독립 변수 중 불연속인 변수가 있는 경우 노드의 변수 분포를 보여 주는 히스토그램도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-173">If any of your independent variables are discrete, you will also see a histogram that shows the distribution of variables in the node.</span></span>  
  
3.  <span data-ttu-id="13392-174">이제 표시할 다른 시계열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-174">Now select a different time series to view.</span></span> <span data-ttu-id="13392-175">뷰어의 **모델** 탭에 있는 **트리** 목록을 사용 하 여 **M200 북아메리카: Amount** series를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-175">Using the **Tree** list on the **Model** tab of the viewer, select the **M200 North America: Amount** series.</span></span>  
  
     <span data-ttu-id="13392-176">이제 트리 그래프에 **모든** 노드와 두 개의 자식 노드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-176">The tree graph now contains an **All** node and two child nodes.</span></span> <span data-ttu-id="13392-177">자식 노드의 레이블을 확인하여 추세 선의 어느 지점이 변경되었는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-177">By looking at the labels on the child nodes, you can understand at what point the trend line changed.</span></span>  
  
     <span data-ttu-id="13392-178">각 자식 노드에 대해 **마이닝 범례의** 설명에는 트리의 각 분기에 있는 사례 수도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-178">For each child node, the description in the **Mining Legend** also includes the count of cases in each branch of the tree.</span></span>  
  
 <span data-ttu-id="13392-179">다음 목록에서는 트리 뷰어의 일부 추가 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-179">The following list describes some additional features in the tree viewer:</span></span>  
  
-   <span data-ttu-id="13392-180">**배경** 컨트롤을 사용 하 여 차트에 표시 되는 변수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-180">You can change the variable that is represented in the chart by using the **Background** control.</span></span> <span data-ttu-id="13392-181">기본적으로 더 짙은 노드는 **Background** 값이 **채우기**로 설정 되어 있기 때문에 더 많은 사례를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-181">By default, nodes that are darker contain more cases, because the value of **Background** is set to **Population**.</span></span> <span data-ttu-id="13392-182">노드에 있는 사례 수를 확인 하려면 노드 위에 마우스를 놓고 표시 되는 도구 설명을 보거나 노드를 클릭 하 고 **노드 범례** 창에서 숫자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-182">To see just how many cases there are in a node, pause the mouse over a node and view the ToolTip that appears, or click the node and view the numbers in the **Node Legend** window.</span></span>  
  
-   <span data-ttu-id="13392-183">노드의 회귀 수식은 도구 모음에서 확인하거나 노드를 클릭하여 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-183">The regression formula for the node can also be viewed in the ToolTip, or by clicking the node.</span></span> <span data-ttu-id="13392-184">혼합 모델을 만든 경우 리프 노드의 ARTXP용 수식과 트리 루트 노드의 ARIMA용 수식 두 가지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-184">If you have created a mixed model, you can see two formulas, one for ARTXP (in the leaf nodes) and one for ARIMA (in the root node of the tree).</span></span>  
  
-   <span data-ttu-id="13392-185">작은 다이아몬드 모양은 연속적인 수를 나타내는 노드에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-185">The little diamonds are used in nodes that represent continuous numbers.</span></span> <span data-ttu-id="13392-186">특성의 범위는 다이아몬드가 놓인 막대에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-186">The range of the attributes is shown in the bar on which the diamond rests.</span></span> <span data-ttu-id="13392-187">다이아몬드는 노드의 평균에 있고 다이아몬드 너비는 해당 노드에서 특성의 분산을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13392-187">The diamond is centered on the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span>  
  
 [<span data-ttu-id="13392-188">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="13392-188">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a><span data-ttu-id="13392-189">필드 일반 콘텐츠 트리 뷰어</span><span class="sxs-lookup"><span data-stu-id="13392-189">(Optional) Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="13392-190">시계열에 대 한 사용자 지정 뷰어 외에도에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 모든 데이터 마이닝 모델에 사용할 수 있는 **MicrosoftGeneric 콘텐츠 트리 뷰어** 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-190">In addition to the custom viewer for time series, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides the **MicrosoftGeneric Content Tree Viewer** for use with all data mining models.</span></span> <span data-ttu-id="13392-191">이 뷰어는 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-191">This viewer provides some advantages:</span></span>  
  
-   <span data-ttu-id="13392-192">**Microsoft 시계열 뷰어**:이 보기는 두 알고리즘의 결과를 병합 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-192">**Microsoft Time Series Viewer**: This view merges the results of the two algorithms.</span></span> <span data-ttu-id="13392-193">각 계열을 개별적으로 볼 수는 있지만 각 알고리즘의 결과가 결합된 방법을 확인할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-193">Although you can view each series separately, you cannot determine how the results of each algorithm were combined.</span></span> <span data-ttu-id="13392-194">또한 이 뷰에서 도구 설명 및 마이닝 범례에는 가장 중요한 통계만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-194">Also, in this view, the Tooltips and Mining Legend show only the most important statistics.</span></span>  
  
-   <span data-ttu-id="13392-195">**일반 콘텐츠 트리 뷰어**: 모델에 사용 된 모든 데이터 계열을 한 번에 찾아보고 볼 수 있으며 혼합 모델을 만든 경우 ARIMA 및 ARTXP 트리가 동일한 그래프에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-195">**Generic Content Tree Viewer**: Lets you browse and view all of the data series that were used in the model at one time, and if you have created a mixed model, both the ARIMA and ARTXP trees are displayed in the same graph.</span></span>  
  
     <span data-ttu-id="13392-196">이 뷰어를 사용하여 두 가지 알고리즘으로부터 값의 분포는 물론 전체 통계를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-196">You can use this viewer to get all the statistics from both algorithms, as well as distributions of the values.</span></span>  
  
     <span data-ttu-id="13392-197">ARIMA 및 ARTXP 분석에 대해 더 자세히 알고자 하는 데이터 마이닝 전문가에게 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-197">Recommended for expert users of data mining who want to know more about the ARIMA and ARTXP analyses.</span></span>  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a><span data-ttu-id="13392-198">일반 콘텐츠 뷰어에서 특정 데이터 계열에 대한 세부 사항을 보려면</span><span class="sxs-lookup"><span data-stu-id="13392-198">To view details for a particular data series in the generic content viewer</span></span>  
  
1.  <span data-ttu-id="13392-199">**마이닝 모델 뷰어** 탭의 **뷰어** 드롭다운 목록에서 **Microsoft 일반 콘텐츠 트리 뷰어** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-199">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** drop-down list.</span></span>  
  
2.  <span data-ttu-id="13392-200">**노드 캡션** 창에서 최상위 (All) 노드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-200">In the **Node Caption** pane, click the topmost (All) node.</span></span>  
  
3.  <span data-ttu-id="13392-201">**노드 세부 정보** 창에서 ATTRIBUTE_NAME 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-201">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="13392-202">이 값은 이 노드에 포함된 제품 및 지역의 결합 또는 계열을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13392-202">This value shows you which series, or combination of product and region, is contained in this node.</span></span> <span data-ttu-id="13392-203">AdventureWorks 예제에서 최상위 노드는 M200 Europe 계열에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="13392-203">In the AdventureWorks example, the topmost node is for the M200 Europe series.</span></span>  
  
4.  <span data-ttu-id="13392-204">**노드 캡션** 창에서 자식 노드를 포함 하는 첫 번째 노드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-204">In the **Node Caption** pane, locate the first node that has child nodes.</span></span>  
  
     <span data-ttu-id="13392-205">계열 노드에 자식이 있으면 Microsoft 시계열 뷰어의 **모델** 탭에 표시 되는 트리 보기에도 분기 구조가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-205">If a series node has children, the tree view that appears on the **Model** tab of the Microsoft Time Series Viewer will also have a branching structure.</span></span>  
  
5.  <span data-ttu-id="13392-206">노드를 확장하고 자식 노드 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-206">Expand the node and click one of the child nodes.</span></span>  
  
     <span data-ttu-id="13392-207">스키마의 NODE_DESCRIPTION 열에는 트리를 분할한 조건이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="13392-207">The NODE_DESCRIPTION column of the schema contains the condition that caused the tree to split.</span></span>  
  
6.  <span data-ttu-id="13392-208">**노드 캡션** 창에서 최상위 ARIMA 노드를 클릭 하 고 모든 자식 노드가 표시 될 때까지 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-208">In the **Node Caption** pane, click the topmost ARIMA node, and expand the node until all child nodes are visible.</span></span>  
  
7.  <span data-ttu-id="13392-209">**노드 세부 정보** 창에서 ATTRIBUTE_NAME 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-209">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="13392-210">이 값은 이 노드에 포함된 시계열을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13392-210">This value tells you which time series is contained in this node.</span></span> <span data-ttu-id="13392-211">ARIMA 섹션의 최상위 노드는 (All) 섹션의 최상위 노드와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13392-211">The topmost node in the ARIMA section should match the topmost node in the (All) section.</span></span> <span data-ttu-id="13392-212">AdventureWorks 예제에서 이 노드에는 M200 Europe 계열에 대한 ARIMA 분석이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13392-212">In the AdventureWorks example, this node contains the ARIMA analysis for the series, M200 Europe.</span></span>  
  
 <span data-ttu-id="13392-213">자세한 내용은 [시계열 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13392-213">For more information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="13392-214">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="13392-214">Back to Top</span></span>](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="13392-215">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="13392-215">Next Task in Lesson</span></span>  
 [<span data-ttu-id="13392-216">&#40;중급 데이터 마이닝 자습서&#41;시계열 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="13392-216">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="13392-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13392-217">See Also</span></span>  
 <span data-ttu-id="13392-218">[시계열 모델 쿼리 예제](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="13392-218">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="13392-219">Microsoft Time Series 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="13392-219">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
