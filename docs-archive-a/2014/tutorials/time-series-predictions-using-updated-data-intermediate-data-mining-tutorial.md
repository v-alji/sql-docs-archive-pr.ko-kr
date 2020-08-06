---
title: 업데이트 된 데이터를 사용한 시계열 예측 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639134"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="a37eb-102">업데이트된 데이터를 사용한 시계열 예측(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="a37eb-102">Time Series Predictions using Updated Data (Intermediate Data Mining Tutorial)</span></span>
    
## <a name="creating-predictions-using-the-extended-sales-data"></a><span data-ttu-id="a37eb-103">확장 판매 데이터를 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="a37eb-103">Creating Predictions using the Extended Sales Data</span></span>  
 <span data-ttu-id="a37eb-104">이 단원에서는 모델에 새 판매 데이터를 추가하는 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-104">In this lesson, you will create a prediction query that adds the new sales data to the model.</span></span> <span data-ttu-id="a37eb-105">새 데이터로 모델을 확장하여 최신 데이터 요소를 포함하는 최신 예측을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-105">By extending the model with new data, you can get up-to-date predictions that include the newest data points.</span></span>  
  
 <span data-ttu-id="a37eb-106">새 데이터를 사용 하는 시계열 예측을 만드는 것은 쉽습니다. [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) 함수에 매개 변수 EXTEND_MODEL_CASES을 추가 하 고, 새 데이터의 원본을 지정 하 고, 가져올 예측 수를 지정 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-106">Creating time series predictions that use new data is easy: you simply add the parameter EXTEND_MODEL_CASES to the [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) function, specify the source of the new data, and specify how many predictions you want to get.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a37eb-107">매개 변수 EXTEND_MODEL_CASES는 선택 사항입니다. 기본적으로 모델은 새 데이터를 입력으로 조인하여 시계열 예측 쿼리를 만드는 시간에 따라 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-107">The parameter EXTEND_MODEL_CASES is optional; by default the model is extended any time that you create a time series prediction query by joining new data as inputs.</span></span>  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a><span data-ttu-id="a37eb-108">예측 쿼리를 작성하고 새 데이터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a37eb-108">To build the prediction query and add new data</span></span>  
  
1.  <span data-ttu-id="a37eb-109">모델이 아직 열려 있지 않은 경우 예측 구조를 두 번 클릭 하 고 데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-109">If the model is not already open, double-click the Forecasting structure, and in Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="a37eb-110">**마이닝 모델** 창에서 모델 예측이 이미 선택 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-110">In the **Mining Model** pane, the model Forecasting should already be selected.</span></span> <span data-ttu-id="a37eb-111">선택 하지 않은 경우 **모델 선택**을 클릭 한 다음 예측 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-111">If it is not selected, click **Select Model**, and then select the model, Forecasting.</span></span>  
  
3.  <span data-ttu-id="a37eb-112">**입력 테이블 선택** 창에서 **사례 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-112">In the **Select Input Table(s)** pane, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="a37eb-113">**테이블 선택** 대화 상자에서 데이터 원본을 선택 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-113">In the **Select Table** dialog box, select the data source, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
     <span data-ttu-id="a37eb-114">데이터 원본 뷰 목록에서 NewSalesData를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-114">From the list of data source views, select NewSalesData and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a37eb-115">디자인 영역의 화면을 마우스 오른쪽 단추로 클릭 하 고 **연결 수정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-115">Right-click the surface of the design area and select **Modify Connections**.</span></span>  
  
6.  <span data-ttu-id="a37eb-116">**매핑 수정** 대화 상자를 사용 하 여 다음과 같이 모델의 열을 외부 데이터의 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-116">Using the **Modify Mapping** dialog box, map the columns in the model to the columns in the external data as follows:</span></span>  
  
    -   <span data-ttu-id="a37eb-117">마이닝 모델의 ReportingDate 열을 입력 데이터의 NewDate 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-117">Map the ReportingDate column in the mining model to the NewDate column in the input data.</span></span>  
  
    -   <span data-ttu-id="a37eb-118">마이닝 모델의 Amount 열을 입력 데이터의 NewAmount 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-118">Map the Amount column in the mining model to the NewAmount column in the input data.</span></span>  
  
    -   <span data-ttu-id="a37eb-119">마이닝 모델의 Quantity 열을 입력 데이터의 NewQty 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-119">Map the Quantity column in the mining model to the NewQty column in the input data.</span></span>  
  
    -   <span data-ttu-id="a37eb-120">마이닝 모델의 ModelRegion 열을 입력 데이터의 계열 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-120">Map the ModelRegion column in the mining model to the Series column in the input data.</span></span>  
  
7.  <span data-ttu-id="a37eb-121">이제 예측 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-121">Now you will build the prediction query.</span></span>  
  
     <span data-ttu-id="a37eb-122">우선, 예측이 적용되는 계열을 출력하기 위해 예측 쿼리에 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-122">First, add a column to the prediction query to output the series the prediction applies to.</span></span>  
  
    1.  <span data-ttu-id="a37eb-123">표에서 첫 번째 빈 행을 클릭 하 고 **원본**아래에서 예측을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-123">In the grid, click the first empty row, under **Source**, and then select Forecasting.</span></span>  
  
    2.  <span data-ttu-id="a37eb-124">**필드** 열에서 모델 영역을 선택 하 고 **별칭**에를 입력 `Model Region` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-124">In the **Field** column, select Model Region and for **Alias**, type `Model Region`.</span></span>  
  
8.  <span data-ttu-id="a37eb-125">다음으로 예측 함수를 추가하고 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-125">Next, add and edit the prediction function.</span></span>  
  
    1.  <span data-ttu-id="a37eb-126">빈 행을 클릭 하 고 **원본**아래에서 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-126">Click an empty row, and under **Source**, select **Prediction Function**.</span></span>  
  
    2.  <span data-ttu-id="a37eb-127">**필드**에 대해 **PredictTimeSeries**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-127">For **Field**, select **PredictTimeSeries**.</span></span>  
  
    3.  <span data-ttu-id="a37eb-128">**별칭**에 **예측 값**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-128">For **Alias**, type **Predicted Values**.</span></span>  
  
    4.  <span data-ttu-id="a37eb-129">**마이닝 모델** 창의 필드 수량을 **조건/인수** 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-129">Drag the field Quantity from the **Mining Model** pane into the **Criteria/Argument** column.</span></span>  
  
    5.  <span data-ttu-id="a37eb-130">**조건/인수** 열에서 필드 이름 뒤에 다음 텍스트를 입력 합니다. **5, EXTEND_MODEL_CASES**</span><span class="sxs-lookup"><span data-stu-id="a37eb-130">In the **Criteria/Argument** column, after the field name, type the following text:  **5,EXTEND_MODEL_CASES**</span></span>  
  
         <span data-ttu-id="a37eb-131">**조건/인수** 텍스트 상자의 전체 텍스트는 다음과 같아야 합니다.`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span><span class="sxs-lookup"><span data-stu-id="a37eb-131">The complete text of the **Criteria/Argument** text box should be as follows: `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span></span>  
  
9. <span data-ttu-id="a37eb-132">**결과** 를 클릭 하 고 결과를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-132">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="a37eb-133">예측은 7월(원래 데이터의 끝에서부터 첫 번째 시간 조각)에 시작되고 11월(원래 데이터 끝에서부터 다섯 번째 시간 조각)에 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-133">The predictions begin in July (the first time slice after the end of the original data) and end at November (the fifth time slice after the end of the original data).</span></span>  
  
 <span data-ttu-id="a37eb-134">이러한 유형의 예측 쿼리를 사용하려면 기존 데이터가 언제 끝나며 새 데이터에 시간 조각이 몇 개 있는지 알고 있어야 함을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-134">You can see that to use this type of prediction query effectively, you need to know when the old data ends, as well as how many time slices there are in the new data.</span></span>  
  
 <span data-ttu-id="a37eb-135">예를 들어 이 모델에서 원래 데이터 계열은 6월에 끝났고 데이터는 7, 8, 9월에 대한 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-135">For example, in this model, the original data series ended in June, and the data is for the months of July, August, and September.</span></span>  
  
 <span data-ttu-id="a37eb-136">EXTEND_MODEL_CASES를 사용하는 예측은 항상 원래 데이터 계열의 끝에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-136">Predictions that use EXTEND_MODEL_CASES always begin at the end of the original data series.</span></span> <span data-ttu-id="a37eb-137">따라서 결과를 알 수 없는 개월에 대한 예측만 구하려면 예측의 시작점과 끝점을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-137">Therefore, if you want to get only the predictions for the unknown months, you need to specify the starting point and the end point for prediction.</span></span> <span data-ttu-id="a37eb-138">양쪽 값 모두 기존 데이터의 끝에서 시작되는 시간 조각의 수로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-138">Both values are specified as a number of time slices starting at the end of the old data.</span></span>  
  
 <span data-ttu-id="a37eb-139">다음 절차에서는 이를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-139">The following procedure demonstrates how to do this.</span></span>  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a><span data-ttu-id="a37eb-140">예측의 시작점과 끝점 변경</span><span class="sxs-lookup"><span data-stu-id="a37eb-140">Change the start and end points of the predictions</span></span>  
  
1.  <span data-ttu-id="a37eb-141">예측 쿼리 작성기에서 **쿼리** 를 클릭 하 여 DMX 보기로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-141">In Prediction Query Builder, click **Query** to switch to DMX view.</span></span>  
  
2.  <span data-ttu-id="a37eb-142">PredictTimeSeries 함수가 포함된 DMX 문을 찾아 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-142">Locate the DMX statement that contains the PredictTimeSeries function and change it as follows:</span></span>  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  <span data-ttu-id="a37eb-143">**결과** 를 클릭 하 고 결과를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-143">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="a37eb-144">이제 예측은 10월(원래 데이터의 끝에서부터 네 번째 시간 조각)에 시작되고 12월(원래 데이터의 끝에서부터 여섯 번째 시간 조각)에 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="a37eb-144">Now the predictions begin at October (the fourth time slice, counting from the end of the original data) and end at December (the sixth time slice, counting from the end of the original data).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a37eb-145">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a37eb-145">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a37eb-146">대체 데이터를 사용한 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="a37eb-146">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="a37eb-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a37eb-147">See Also</span></span>  
 <span data-ttu-id="a37eb-148">[Microsoft 시계열 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a37eb-148">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="a37eb-149">시계열 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="a37eb-149">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
