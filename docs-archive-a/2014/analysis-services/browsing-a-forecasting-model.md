---
title: 예측 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d0b188c4ed6fba9bc5b1082725b17c99081c1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648110"
---
# <a name="browsing-a-forecasting-model"></a><span data-ttu-id="fe82e-102">예측 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="fe82e-102">Browsing a Forecasting Model</span></span>
  <span data-ttu-id="fe82e-103">**찾아보기**를 사용 하 여 예측 모델을 열면의 시계열 모델 뷰어와 비슷한 대화형 뷰어에 모델이 표시 됩니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fe82e-103">When you open a forecasting model using **Browse**, the model is displayed in an interactive viewer, similar to the time series model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fe82e-104">이 뷰어에서는 추세를 살펴보고, 계열을 비교하고, 예측을 만들고, 모델 및 기본 데이터에 대한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-104">The viewer helps you explore trends, compare series, create predictions, and get information about the model and the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="fe82e-105">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="fe82e-105">Explore the Model</span></span>  
 <span data-ttu-id="fe82e-106">예측 모델에 대 한 **찾아보기** 뷰어는 시간에 따른 추세를 표시 하 고 예측을 만들 수 있도록 하는 차트 뷰와 시계열을 의사 결정 트리 또는 회귀 트리로 나타내는 모델 뷰를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-106">The **Browse** viewer for forecasting models provides a chart view, which shows the trends over time and lets you create predictions, and a model view, which represents the time series as a decision tree or a regression tree.</span></span>  
  
-   [<span data-ttu-id="fe82e-107">차트 보기</span><span class="sxs-lookup"><span data-stu-id="fe82e-107">Chart view</span></span>](#bkmk_charts)  
  
-   [<span data-ttu-id="fe82e-108">모델 뷰</span><span class="sxs-lookup"><span data-stu-id="fe82e-108">Model view</span></span>](#bkmk_Model)  
  
 <span data-ttu-id="fe82e-109">예측 모델을 시험해 보려면 샘플 데이터 통합 문서의 예측 탭에서 예제 데이터를 사용 하 고, 예측 마법사를 사용 하 여 데이터 **마이닝** 리본의 [&#41;Excel 용 데이터 마이닝 추가 기능을 &#40;](forecast-wizard-data-mining-add-ins-for-excel.md) 하 고, **분석** 리본에서 [&#41;excel 용 &#40;테이블 분석 도구](forecast-table-analysis-tools-for-excel.md) 를 사용 하 여 시계열 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-109">To experiment with a forecasting model, you can use the sample data on the Forecast tab of the sample data workbook, and build a time series model using the [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) in the **Data Mining** ribbon, or [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) in the **Analyze** ribbon.</span></span>  
  
###  <a name="chart"></a><a name="bkmk_charts"></a><span data-ttu-id="fe82e-110">차트</span><span class="sxs-lookup"><span data-stu-id="fe82e-110">Chart</span></span>  
 <span data-ttu-id="fe82e-111">**차트** 탭에서는 시간에 따른 데이터 계열의 추세를 예측 값과 함께 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-111">The **Chart** tab displays the trend in your data series over time, together with the predicted values.</span></span> <span data-ttu-id="fe82e-112">차트의 세로 축은 계열 값을 나타내고 가로 축은 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-112">The vertical axis of the chart represents the values of the series, and the horizontal axis represents time.</span></span>  
  
##### <a name="explore-the-forecasting-chart"></a><span data-ttu-id="fe82e-113">예측 차트 탐색</span><span class="sxs-lookup"><span data-stu-id="fe82e-113">Explore the forecasting chart</span></span>  
  
1.  <span data-ttu-id="fe82e-114">이 모델에는 여러 시계열이 포함되지만 차트를 단순화하기 위해 단일 계열이나 몇몇 관련 계열만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-114">This model contains multiple time series, but to simplify the chart, you can display a single series, or just a few related series.</span></span>  
  
     <span data-ttu-id="fe82e-115">![예측 모델의 기록 예측](media/dm13-forecast-chart-historicpredictions.gif "예측 모델의 기록 예측")</span><span class="sxs-lookup"><span data-stu-id="fe82e-115">![historical predictions in the forecasting model](media/dm13-forecast-chart-historicpredictions.gif "historical predictions in the forecasting model")</span></span>  
  
     <span data-ttu-id="fe82e-116">확인란을 사용해서 북아메리카 지역 및 판매 금액에 대한 예측만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-116">Use the check boxes to select the forecast for just North America, and just for sales Amount.</span></span>  
  
2.  <span data-ttu-id="fe82e-117">**예측 단계** 를 클릭 하 고 새 값을 입력 하 여 차트에 표시할 이후 시간 값의 수를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-117">Click **Prediction Steps** and type a new value to control how many future time values you want to see in the chart.</span></span>  
  
     <span data-ttu-id="fe82e-118">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-118">The default is 5.</span></span>  
  
3.  <span data-ttu-id="fe82e-119">**마이닝 범례**에 표시 되는 특정 시점에 대 한 정확한 값을 확인 하려면 해당 줄에서 기록 또는 미래를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-119">Click any point in the line, either historical or future, to see the exact values for that point in time, displayed in the **Mining Legend**.</span></span>  
  
4.  <span data-ttu-id="fe82e-120">차트에는 기록 데이터와 예측 데이터가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-120">The chart displays both historical and future data.</span></span> <span data-ttu-id="fe82e-121">회색 배경의 점선에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe82e-121">Note the dotted line, with a shaded background.</span></span> <span data-ttu-id="fe82e-122">이러한 값은 모델을 기반으로 하는 미래 예측입니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-122">These values are the future predictions, based on the model.</span></span>  
  
     <span data-ttu-id="fe82e-123">기록 데이터(모델을 작성할 때 사용)는 차트의 왼쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-123">The historical data (which you used to build the model) is shown in the left side of the chart.</span></span>  
  
5.  <span data-ttu-id="fe82e-124">**기록 예측 표시** 옵션을 선택 하 여 시계열의 안정성을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-124">Select the **Show historic predictions** option to get a sense for the stability of the time series.</span></span>  
  
     <span data-ttu-id="fe82e-125">![모델의 단일 계열에 대한 예측](media/dm13-forecast-chart-singleseries.gif "모델의 단일 계열에 대한 예측")</span><span class="sxs-lookup"><span data-stu-id="fe82e-125">![forecasts for a single series in the model](media/dm13-forecast-chart-singleseries.gif "forecasts for a single series in the model")</span></span>  
  
     <span data-ttu-id="fe82e-126">기록 예측은 실제 기록 값과 달리 해당 지점까지의 계열을 기반으로 예측된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-126">Historical predictions are values predicted based on the series to that point, which are compared to actual historical values.</span></span> <span data-ttu-id="fe82e-127">점선(예측 값)이 실선(실제 값)에서 너무 멀리 떨어져 있으면 계열의 첫 부분에서 이후 값을 정확하게 예측할 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-127">If the dotted line (with the predicted values) is far apart from the solid line (the actual values), it means the first part of the series perhaps does not accurately predict the later values.</span></span> <span data-ttu-id="fe82e-128">이 경우는 더 많은 데이터가 필요할 수 있거나 또는 단순히 해당 주기의 변동성에 대한 지표일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-128">You might need more data, or it might simply be an indicator of volatility in the cycle.</span></span>  
  
6.  <span data-ttu-id="fe82e-129">**편차 표시** 옵션을 선택 하 여 차트에 오차 막대를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-129">Select the **Show Deviations** option to display error bars in the chart.</span></span>  
  
     <span data-ttu-id="fe82e-130">오차 막대를 보면 예측의 가변성을 시각적으로 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-130">The error bars let you visually assess the variability of the predictions.</span></span> <span data-ttu-id="fe82e-131">예측 품질은 원본 데이터에 따라 달라지지만 예측 단계 수를 늘릴수록 편차가 꾸준히 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-131">The quality of predictions varies depending on your source data, but as you increase the number of prediction steps, you should see the deviations steadily increase.</span></span>  
  
 <span data-ttu-id="fe82e-132">**팁**</span><span class="sxs-lookup"><span data-stu-id="fe82e-132">**Tips**</span></span>  
  
-   <span data-ttu-id="fe82e-133">**마이닝 범례의**표시를 전환 하려면 차트에서 임의의 점을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-133">To toggle display of the **Mining Legend**, right-click any point in the chart.</span></span>  
  
     <span data-ttu-id="fe82e-134">차트를 클릭하고 선택한 시간 영역을 차트에서 끈 다음 다시 클릭하여 선택한 범위를 확대하면 특정 시간 범위를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-134">You can view a specific time range by clicking the chart, dragging a time selection across the chart, and then clicking again to zoom in on the selected range.</span></span>  
  
-   <span data-ttu-id="fe82e-135">현재 차트의 복사본을 가져오려면 **excel로 복사**를 클릭 한 다음 excel에서 워크시트를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-135">To get a copy of the current chart, click **Copy to Excel**, then click a worksheet in Excel.</span></span> <span data-ttu-id="fe82e-136">그래픽은 범례를 포함해서 사용자가 설정한 모든 옵션을 사용해서 시트에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-136">A graphic is inserted in the sheet using all the options you had set, including a legend.</span></span>  
  
     <span data-ttu-id="fe82e-137">그러나이 그래픽은 정적 이므로 범례를 편집 하거나 기본 데이터를 볼 수 없습니다. 좀 더 대화형 차트 뷰가 필요한 경우 [Visio viewer](viewing-data-mining-models-in-visio-data-mining-add-ins.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-137">However, this graphic is static so you cannot edit the legend or view the underlying data; if you need a more interactive chart view, use the [Visio viewers](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
-   <span data-ttu-id="fe82e-138">뷰어 메뉴 모음에서 **Abs** 를 클릭 하 여 절대 곡선과 상대 곡선을 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-138">Click **Abs** in the viewer menu bar to toggle between absolute and relative curves.</span></span>  
  
     <span data-ttu-id="fe82e-139">이 옵션은 차트에 여러 모델이 포함되었지만 각 모델에 대한 데이터의 배율이 크게 다를 수 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-139">This option is useful if your chart contains multiple models, but the scale of the data for each model is very different.</span></span>  
  
     <span data-ttu-id="fe82e-140">예를 들어 태평양 지역의 매장이 신규 입점되어 매출이 낮은데 차트에서 절대값이 사용되었다면 태평양 지역 판매를 표시하는 선이 바닥에 표시되어 실제 변동 사항을 확인하기 어려울 수 있습니다. 반면에 다른 모델은 보다 일반적인 배율로 표시될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-140">For example, if the Pacific region stores were new and sales were low, and if absolute values are used, the line showing Pacific sales might appear flat, making it difficult to see actual changes, whereas the other models would be displayed at a more normal scale.</span></span>  
  
     <span data-ttu-id="fe82e-141">상대 값을 사용하도록 뷰를 전환하면 여러 모델의 배율을 정규화해서 차이를 변동 비율로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-141">By switching the view to use relative values, you can normalize the scale of different models, and display differences as a percent of change.</span></span> <span data-ttu-id="fe82e-142">변동이 각 모델에 대해 상대적인 경우에는 큰 왜곡 없이 동일한 그래프에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-142">When change is relative to each model, they can be displayed in the same graph without significant distortion.</span></span>  
  
 [<span data-ttu-id="fe82e-143">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="fe82e-143">Explore the Model</span></span>](#bkmk_Top)  
  
###  <a name="model"></a><a name="bkmk_Model"></a><span data-ttu-id="fe82e-144">모델링</span><span class="sxs-lookup"><span data-stu-id="fe82e-144">Model</span></span>  
 <span data-ttu-id="fe82e-145">예측 모델은 또한 의사 결정 트리로 나타내거나, 계열이 대부분 선형인 경우 회귀 모델로 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-145">A forecasting model can also be represented as a decision tree, or, if the series is mostly linear, a regression model.</span></span>  
  
 <span data-ttu-id="fe82e-146">예를 들어 이 모델에서는 특정 조건에 따라 회귀 수식에 차이가 있으므로 트리가 서로 다른 회귀 수식을 포함하는 두 개의 분기로 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-146">For example, in this model, there is a difference in the regression formula based on a certain condition, so the tree splits into two branches, each with a different regression formula.</span></span>  
  
 <span data-ttu-id="fe82e-147">![예측 모델의 단일 계열 필터링](media/dm13-forecast-model-northamerica.gif "예측 모델의 단일 계열 필터링")</span><span class="sxs-lookup"><span data-stu-id="fe82e-147">![Filter single series in the forecasting model](media/dm13-forecast-model-northamerica.gif "Filter single series in the forecasting model")</span></span>  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a><span data-ttu-id="fe82e-148">트리로 예측 모델 탐색</span><span class="sxs-lookup"><span data-stu-id="fe82e-148">Explore the forecasting model as a tree</span></span>  
  
1.  <span data-ttu-id="fe82e-149">**트리** 드롭다운 목록을 클릭 하 고 표시할 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-149">Click the **Tree** dropdown list and choose a model to display.</span></span>  
  
     <span data-ttu-id="fe82e-150">각 예측 가능한 특성에 대해 별도의 트리 또는 회귀 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-150">A separate tree or regression node is displayed for each predictable attribute.</span></span> <span data-ttu-id="fe82e-151">예를 들어 데이터에 유럽, 북아메리카 및 태평양 지역의 판매가 포함된 경우, 각 데이터 계열당 하나씩 세 개의 서로 다른 모델이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-151">For example, if your data contains sales for Europe, North America, and the Pacific, there would three different models, one for each data series.</span></span>  
  
2.  <span data-ttu-id="fe82e-152">**수준 표시** 슬라이더를 끌어 트리의 하위 수준을 필터링 하 고 가장 중요 한 분할에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-152">Drag the **Show Level** slider to filter out lower levels of the tree, and focus on the most important splits.</span></span>  
  
3.  <span data-ttu-id="fe82e-153">각 노드를 클릭 하 여 **마이닝 범례**에 설명 통계를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-153">Click each node to view some descriptive statistics in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="fe82e-154">마우스를 노드 위에 놓아도 도구 설명에 해당 노드를 기술하는 전체 수식뿐만 아니라 동일한 통계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-154">As you pause over a node with the mouse, a ToolTip also displays the same statistics, as well as the full formula describing that node.</span></span>  
  
4.  <span data-ttu-id="fe82e-155">**마이닝 범례의**정보를 복사 하려면 **마이닝 범례**를 마우스 오른쪽 단추로 클릭 하 고 **복사**를 선택한 다음 Excel 워크시트 내부를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-155">If you want to copy the information in the **Mining Legend**, right-click the **Mining Legend**, select **Copy**, and click inside your Excel worksheet.</span></span> <span data-ttu-id="fe82e-156">**Excel로 복사** 옵션은 통계가 아니라 그래프를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe82e-156">The **Copy to Excel** option copies the graph, not the statistics.</span></span>  
  
 [<span data-ttu-id="fe82e-157">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="fe82e-157">Explore the Model</span></span>](#bkmk_Top)  
  
## <a name="see-also"></a><span data-ttu-id="fe82e-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe82e-158">See Also</span></span>  
 [<span data-ttu-id="fe82e-159">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="fe82e-159">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
