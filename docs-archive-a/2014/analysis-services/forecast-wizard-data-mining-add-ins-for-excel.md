---
title: 예측 마법사 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c3fae97bf1c36154d8ae378840014f2fb997afd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647969"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="f51dd-102">예측 마법사(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="f51dd-102">Forecast Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="f51dd-103">![데이터 마이닝 리본의 연결 마법사](media/dmc-forecast.gif "데이터 마이닝 리본의 연결 마법사")</span><span class="sxs-lookup"><span data-stu-id="f51dd-103">![Associate wizard in Data Mining ribbon](media/dmc-forecast.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="f51dd-104">예측 마법사를 사용하면 시계열의 값을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-104">The Forecast wizard helps you predict values in a time series.</span></span> <span data-ttu-id="f51dd-105">예측 마법사는 제품 판매량과 같은 연속 열을 예측하기 위해 사용되는 회귀 알고리즘인 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-105">The Forecast wizard uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm, which is a regression algorithm for use in predicting continuous columns, such as product sales.</span></span>  
  
 <span data-ttu-id="f51dd-106">각 예측 모델은 시퀀스의 요소를 구분하는 열인 사례 계열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-106">Each forecasting model must contain a case series, which is the column that distinguishes between points in a sequence.</span></span> <span data-ttu-id="f51dd-107">예를 들어 여러 달 동안의 판매량을 예측하기 위해 기록 데이터를 사용하는 경우 날짜 계열이 포함된 열을 사례 계열로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-107">For example, if you are using historical data to forecast sales over a period of several months, you would use a column containing a series of dates as the case series.</span></span>  
  
 <span data-ttu-id="f51dd-108">새 입력 데이터를 제공하지 않아도 예측 모델로부터 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-108">You can create predictions from a forecasting model without providing new input data.</span></span>  
  
 <span data-ttu-id="f51dd-109">**분석** 리본에서 [예측 &#40;테이블 분석 도구&#41;](forecast-table-analysis-tools-for-excel.md) 도구를 사용 하 여 예측 모델을 만들 수도 있지만 사용자 지정이 더 적고 Excel 테이블의 데이터만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-109">The [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) tool, in the **Analyze** ribbon, also lets you create forecasting models, but it is less customizable and can only use data in Excel tables.</span></span>  
  
## <a name="using-the-forecast-wizard"></a><span data-ttu-id="f51dd-110">예측 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="f51dd-110">Using the Forecast Wizard</span></span>  
  
1.  <span data-ttu-id="f51dd-111">**데이터 마이닝** 리본에서 **예측**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-111">In the **Data Mining** ribbon, click **Forecast**.</span></span>  
  
2.  <span data-ttu-id="f51dd-112">**원본 데이터 선택**에서 입력으로 사용할 Excel 테이블, 범위 또는 외부 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-112">In the **Select Source Data**, choose the Excel table, range, or external data source to use as inputs.</span></span>  
  
     <span data-ttu-id="f51dd-113">외부 데이터 원본을 사용할 경우에는 사용자 지정 뷰 또는 쿼리를 정의하거나 데이터 원본을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-113">If you use an external data source, you can define custom view or queries and save it as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="f51dd-114">**예측** 페이지에서 **타임 스탬프**에 대해 사례 계열로 사용할 수 있는 고유 숫자 값 (날짜 및 시간 값 포함)이 포함 된 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-114">On the **Forecasting** page, for **Time stamp**, select a column that contains unique numeric value (this includes date and time values) that can be used as the case series.</span></span> <span data-ttu-id="f51dd-115">데이터 원본은 이 열을 기준으로 오름차순으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-115">The data source must be sorted in ascending order by this column.</span></span>  
  
     <span data-ttu-id="f51dd-116">데이터에 이러한 열이 없으면 옵션을 사용할 수 있습니다 \<no time stamp> .</span><span class="sxs-lookup"><span data-stu-id="f51dd-116">If your data does not have such a column, you can use the option \<no time stamp>.</span></span> <span data-ttu-id="f51dd-117">마법사는 입력 데이터에 대한 고유 순서 열을 추가합니다. 따라서 마법사를 실행하고 이 옵션을 선택하기 전에 데이터가 원하는 순서로 정렬되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-117">The wizard will add a unique order column for the input data; therefore, you must make sure that the data is sorted the way you want before running the wizard and choosing this option.</span></span>  
  
4.  <span data-ttu-id="f51dd-118">필요에 따라 **매개 변수** 를 클릭 하 고 마이닝 모델의 동작을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-118">Optionally, you can click **Parameters** and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="f51dd-119">예측 모델에는 여러 가지 알고리즘이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-119">Forecasting models support several different algorithms:</span></span>  
  
    -   <span data-ttu-id="f51dd-120">ARIMA</span><span class="sxs-lookup"><span data-stu-id="f51dd-120">ARIMA</span></span>  
  
    -   <span data-ttu-id="f51dd-121">ARTXP(회귀 모델 유형)</span><span class="sxs-lookup"><span data-stu-id="f51dd-121">ARTXP (a type of regression model)</span></span>  
  
    -   <span data-ttu-id="f51dd-122">ARTXP 및 ARIMA 조합</span><span class="sxs-lookup"><span data-stu-id="f51dd-122">ARTXP and ARIMA combined</span></span>  
  
     <span data-ttu-id="f51dd-123">차이점에 대 한 자세한 내용은 [Microsoft 시계열 알고리즘 기술 참조](data-mining/microsoft-time-series-algorithm-technical-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f51dd-123">For information about the differences, see [Microsoft Time Series Algorithm Technical Reference](data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
     <span data-ttu-id="f51dd-124">또한 모델에 대해 주기 힌트를 추가하고, 다듬기(smoothing) 옵션을 지정하고, 회귀 옵션을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-124">You can also add periodicity hints, specify smoothing options, and customize regression options for the model.</span></span>  
  
5.  <span data-ttu-id="f51dd-125">**마침** 페이지에서 데이터 집합 및 모델에 대 한 설명이 포함 된 이름을 입력 하 고 완성 된 모델을 사용 하는 방법을 제어 하는 다음 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-125">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="f51dd-126">**모델 찾아보기**.</span><span class="sxs-lookup"><span data-stu-id="f51dd-126">**Browse model**.</span></span> <span data-ttu-id="f51dd-127">이 옵션을 선택 하면 마법사가 모델 처리를 완료 하는 즉시 결과를 탐색 하는 데 도움이 되는 **찾아보기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-127">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="f51dd-128">뷰어 내용은 작성한 모델 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-128">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="f51dd-129">자세한 내용은 [예측 모델 찾아보기](browsing-a-forecasting-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f51dd-129">For more information, see [Browsing a Forecasting Model](browsing-a-forecasting-model.md).</span></span>  
  
    -   <span data-ttu-id="f51dd-130">**드릴스루를 사용 하도록 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-130">**Enable drillthrough**.</span></span> <span data-ttu-id="f51dd-131">완료된 모델에서 기본 데이터를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-131">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="f51dd-132">이 옵션은 의사 결정 트리 모델을 작성하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-132">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="f51dd-133">**임시 모델 사용**.</span><span class="sxs-lookup"><span data-stu-id="f51dd-133">**Use temporary model**.</span></span> <span data-ttu-id="f51dd-134">이 옵션을 선택하면 모델이 서버에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-134">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="f51dd-135">임시 모델은 Excel을 닫을 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-135">Temporary models are deleted when you close Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f51dd-136">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f51dd-136">Requirements</span></span>  
 <span data-ttu-id="f51dd-137">데이터에 시계열로 사용할 수 있는 열이 하나 이상 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-137">Your data should include at least one column that can be used as the time series.</span></span> <span data-ttu-id="f51dd-138">이 열의 값은 고유 하 고 연속 되어야 합니다. 즉, 간격이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-138">The values in this column should be unique and continuous - that is, there should be no gaps.</span></span> <span data-ttu-id="f51dd-139">마법사를 실행하기 전에 시계열 열을 기준으로 데이터를 오름차순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-139">Before running the wizard, sort the data by the time series column in ascending order.</span></span>  
  
 <span data-ttu-id="f51dd-140">데이터에 시간 또는 날짜 열이 포함되지 않은 경우 임의 숫자 계열을 지정하거나 마법사에서 자동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-140">If your data does not include a time or date column, you can assign an arbitrary numeric series, or let the wizard create one.</span></span> <span data-ttu-id="f51dd-141">마법사에서 계열 순서 열을 자동으로 만들 경우, 마법사를 시작하기 전에 다른 열이 원하는 순서로 정렬되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f51dd-141">F you let the wizard create the series order column, make sure the other columns are sorted in the worder you want them before starting the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51dd-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f51dd-142">See Also</span></span>  
 <span data-ttu-id="f51dd-143">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="f51dd-143">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="f51dd-144">[Excel 용 예측 &#40;테이블 분석 도구&#41;](forecast-table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f51dd-144">[Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="f51dd-145">예측 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f51dd-145">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
  
