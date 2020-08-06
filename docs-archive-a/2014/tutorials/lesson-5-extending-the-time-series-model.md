---
title: '5 단원: 시계열 모델 확장 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648715"
---
# <a name="lesson-5-extending-the-time-series-model"></a><span data-ttu-id="44956-102">5단원: 시계열 모델 확장</span><span class="sxs-lookup"><span data-stu-id="44956-102">Lesson 5: Extending the Time Series Model</span></span>
  <span data-ttu-id="44956-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise에서는 시계열 모델에 새 데이터를 추가하고 새 데이터를 모델에 자동으로 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-103">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise, you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="44956-104">다음 두 가지 방법 중 하나를 사용하여 시계열 마이닝 모델에 새 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-104">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="44956-105">PREDICTION JOIN을 사용하여 외부 원본의 데이터를 학습 데이터에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-105">Use a PREDICTION JOIN to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="44956-106">단일 예측 쿼리를 사용하여 한 번에 한 조각씩 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-106">Use a singleton prediction query to provide data one slice at a time.</span></span>  
  
 <span data-ttu-id="44956-107">예를 들어 몇 개월 전에 기존 판매 데이터에 대해 마이닝 모델을 학습했다고 가정할 때</span><span class="sxs-lookup"><span data-stu-id="44956-107">For example, assume that you trained the mining model on existing sales data some months ago.</span></span> <span data-ttu-id="44956-108">새로운 판매 데이터를 얻어 판매 예측 업데이트를 통해 새 데이터를 통합하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-108">When you get new sales, you might want to update the sales predictions to incorporate the new data.</span></span> <span data-ttu-id="44956-109">이 작업은 새 매출 수치를 입력 데이터로 제공하고 복합 데이터 집합을 기반으로 새 예측을 생성하여 간단하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-109">You can do this in one step, by supplying the new sales figures as input data and generating new predictions based on the composite data set.</span></span>  
  
## <a name="making-predictions-with-extend_model_cases"></a><span data-ttu-id="44956-110">EXTEND_MODEL_CASES로 예측 수행</span><span class="sxs-lookup"><span data-stu-id="44956-110">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="44956-111">다음은 EXTEND_MODEL_CASES를 사용한 일반적인 시계열 예측 예입니다.</span><span class="sxs-lookup"><span data-stu-id="44956-111">The following are generic examples of a time series prediction using EXTEND_MODEL_CASES.</span></span> <span data-ttu-id="44956-112">첫 번째 예를 사용하면 원래 모델의 마지막 시간 단계에서 시작되는 예측 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-112">The first example enables you to specify the number of predictions starting from the last time step of the original model:</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 <span data-ttu-id="44956-113">두 번째 예를 사용하면 예측을 시작하고 종료할 시간 단계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-113">The second example enables you to specify the time step where predictions should start, and where they should end.</span></span> <span data-ttu-id="44956-114">기본적으로 예측 쿼리에 사용되는 시간 단계는 항상 원래 계열의 끝에서 시작되므로 모델 사례를 확장할 때 이 옵션이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-114">This option is important when you extend the model cases because, by default, the time steps used for prediction queries always start at the end of the original series.</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 <span data-ttu-id="44956-115">이 자습서에서는 두 종류 모두의 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44956-115">In this tutorial, you will create both kinds of queries.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a><span data-ttu-id="44956-116">시계열 모델에 대한 단일 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="44956-116">To create a singleton prediction query on a time series model</span></span>  
  
1.  <span data-ttu-id="44956-117">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-117">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="44956-118">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="44956-118">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="44956-119">단일 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-119">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="44956-120">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="44956-120">Replace the following:</span></span>  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     <span data-ttu-id="44956-121">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="44956-121">with:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     <span data-ttu-id="44956-122">첫 번째 줄에서는 모델에서 계열을 식별하는 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-122">The first line retrieves a value from the model that identifies the series.</span></span>  
  
     <span data-ttu-id="44956-123">두 번째 줄에는 Quantity에 대한 6개의 예측을 가져오는 예측 함수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-123">The second line contains the prediction function, which gets 6 predictions for Quantity.</span></span> <span data-ttu-id="44956-124">결과를 보다 쉽게 이해할 수 있도록 예측 결과 열에 별칭 `PredictQty`가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="44956-124">An alias, `PredictQty`, is assigned to the prediction result column to make it easier to understand the results.</span></span>  
  
4.  <span data-ttu-id="44956-125">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="44956-125">Replace the following:</span></span>  
  
    ```  
    FROM <mining model>  
    ```  
  
     <span data-ttu-id="44956-126">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="44956-126">with:</span></span>  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="44956-127">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="44956-127">Replace the following:</span></span>  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     <span data-ttu-id="44956-128">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="44956-128">with:</span></span>  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  <span data-ttu-id="44956-129">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="44956-129">Replace the following:</span></span>  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     <span data-ttu-id="44956-130">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="44956-130">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="44956-131">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-131">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  <span data-ttu-id="44956-132">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-132">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="44956-133">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Singleton_TimeSeries_Query.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-133">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_TimeSeries_Query.dmx`.</span></span>  
  
9. <span data-ttu-id="44956-134">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-134">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="44956-135">쿼리가 Europe 및 Pacific 지역에서의 M200 자전거 판매 수량 예측 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-135">The query returns predictions of sales quantity for the M200 bicycle in the Europe and Pacific regions.</span></span>  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a><span data-ttu-id="44956-136">EXTEND_MODEL_CASES로 예측 시작 지점 이해</span><span class="sxs-lookup"><span data-stu-id="44956-136">Understanding Prediction Start with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="44956-137">원래 모델을 기반으로 예측을 만들었으므로 이제 새 데이터로 결과를 비교하여, 판매 데이터를 업데이트할 경우 예측에 어떠한 영향이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-137">Now that you have created predictions based on the original model, and with new data, you can compare the results to see how updating the sales data affects the predictions.</span></span> <span data-ttu-id="44956-138">이렇게 하기 전에 방금 만든 코드를 검토하고 다음 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-138">Before you do so, review the code that you just created, and notice the following:</span></span>  
  
-   <span data-ttu-id="44956-139">Europe 지역에 대해서만 새 데이터를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-139">You supplied new data for only the Europe region.</span></span>  
  
-   <span data-ttu-id="44956-140">2개월에 상당하는 새 데이터만 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-140">You supplied only two months' worth of new data.</span></span>  
  
 <span data-ttu-id="44956-141">다음 표에서는 M200 Europe에 대해 제공된 새 값이 예측에 어떠한 영향을 주는지 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44956-141">The following table shows how the new values supplied for M200 Europe affect predictions.</span></span> <span data-ttu-id="44956-142">Pacific 지역의 M200 제품에 대해서는 새 데이터를 제공하지 않았지만 이 계열은 비교용으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="44956-142">You did not provide any new data for the M200 product in the Pacific region, but this series is presented for comparison:</span></span>  
  
 <span data-ttu-id="44956-143">**제품 및 지역: 유럽 M200**</span><span class="sxs-lookup"><span data-stu-id="44956-143">**Product and Region: M200 Europe**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="44956-144">기존 모델(`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="44956-144">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="44956-145">판매 데이터가 업데이트된 모델(`PredictTimeSeries`가 있는 `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="44956-145">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="44956-146">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-146">M200 Europe</span></span>|<span data-ttu-id="44956-147">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-147">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-148">77</span><span class="sxs-lookup"><span data-stu-id="44956-148">77</span></span>|<span data-ttu-id="44956-149">10</span><span class="sxs-lookup"><span data-stu-id="44956-149">10</span></span>|  
|<span data-ttu-id="44956-150">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-150">M200 Europe</span></span>|<span data-ttu-id="44956-151">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-151">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-152">64</span><span class="sxs-lookup"><span data-stu-id="44956-152">64</span></span>|<span data-ttu-id="44956-153">15</span><span class="sxs-lookup"><span data-stu-id="44956-153">15</span></span>|  
|<span data-ttu-id="44956-154">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-154">M200 Europe</span></span>|<span data-ttu-id="44956-155">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-155">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-156">59</span><span class="sxs-lookup"><span data-stu-id="44956-156">59</span></span>|<span data-ttu-id="44956-157">72</span><span class="sxs-lookup"><span data-stu-id="44956-157">72</span></span>|  
|<span data-ttu-id="44956-158">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-158">M200 Europe</span></span>|<span data-ttu-id="44956-159">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-159">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-160">56</span><span class="sxs-lookup"><span data-stu-id="44956-160">56</span></span>|<span data-ttu-id="44956-161">69</span><span class="sxs-lookup"><span data-stu-id="44956-161">69</span></span>|  
|<span data-ttu-id="44956-162">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-162">M200 Europe</span></span>|<span data-ttu-id="44956-163">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-163">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-164">56</span><span class="sxs-lookup"><span data-stu-id="44956-164">56</span></span>|<span data-ttu-id="44956-165">68</span><span class="sxs-lookup"><span data-stu-id="44956-165">68</span></span>|  
|<span data-ttu-id="44956-166">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-166">M200 Europe</span></span>|<span data-ttu-id="44956-167">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-167">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-168">74</span><span class="sxs-lookup"><span data-stu-id="44956-168">74</span></span>|<span data-ttu-id="44956-169">89</span><span class="sxs-lookup"><span data-stu-id="44956-169">89</span></span>|  
  
 <span data-ttu-id="44956-170">**제품 및 지역: M200 태평양**</span><span class="sxs-lookup"><span data-stu-id="44956-170">**Product and Region: M200 Pacific**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="44956-171">기존 모델(`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="44956-171">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="44956-172">판매 데이터가 업데이트된 모델(`PredictTimeSeries`가 있는 `EXTEND_MODEL_CASES`)</span><span class="sxs-lookup"><span data-stu-id="44956-172">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="44956-173">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-173">M200 Pacific</span></span>|<span data-ttu-id="44956-174">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-174">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-175">41</span><span class="sxs-lookup"><span data-stu-id="44956-175">41</span></span>|<span data-ttu-id="44956-176">41</span><span class="sxs-lookup"><span data-stu-id="44956-176">41</span></span>|  
|<span data-ttu-id="44956-177">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-177">M200 Pacific</span></span>|<span data-ttu-id="44956-178">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-178">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-179">44</span><span class="sxs-lookup"><span data-stu-id="44956-179">44</span></span>|<span data-ttu-id="44956-180">44</span><span class="sxs-lookup"><span data-stu-id="44956-180">44</span></span>|  
|<span data-ttu-id="44956-181">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-181">M200 Pacific</span></span>|<span data-ttu-id="44956-182">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-182">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-183">38</span><span class="sxs-lookup"><span data-stu-id="44956-183">38</span></span>|<span data-ttu-id="44956-184">38</span><span class="sxs-lookup"><span data-stu-id="44956-184">38</span></span>|  
|<span data-ttu-id="44956-185">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-185">M200 Pacific</span></span>|<span data-ttu-id="44956-186">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-186">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-187">41</span><span class="sxs-lookup"><span data-stu-id="44956-187">41</span></span>|<span data-ttu-id="44956-188">41</span><span class="sxs-lookup"><span data-stu-id="44956-188">41</span></span>|  
|<span data-ttu-id="44956-189">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-189">M200 Pacific</span></span>|<span data-ttu-id="44956-190">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-190">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-191">36</span><span class="sxs-lookup"><span data-stu-id="44956-191">36</span></span>|<span data-ttu-id="44956-192">36</span><span class="sxs-lookup"><span data-stu-id="44956-192">36</span></span>|  
|<span data-ttu-id="44956-193">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="44956-193">M200 Pacific</span></span>|<span data-ttu-id="44956-194">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-194">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-195">39</span><span class="sxs-lookup"><span data-stu-id="44956-195">39</span></span>|<span data-ttu-id="44956-196">39</span><span class="sxs-lookup"><span data-stu-id="44956-196">39</span></span>|  
  
 <span data-ttu-id="44956-197">이러한 결과를 통해 다음 두 가지 사실을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-197">From these results, you can see two things:</span></span>  
  
-   <span data-ttu-id="44956-198">M200 Europe 계열에 대한 처음 두 예측은 사용자가 제공한 새 데이터와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-198">The first two predictions for the M200 Europe series are exactly the same as the new data you supplied.</span></span> <span data-ttu-id="44956-199">기본적으로 Analysis Services에서는 예측을 만들지 않고 실제 새 데이터 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-199">By design, Analysis Services returns the actual new data points instead of making a prediction.</span></span> <span data-ttu-id="44956-200">이는 모델 사례를 확장할 때 예측 쿼리에 사용되는 시간 단계가 항상 원래 계열의 끝에서 시작되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="44956-200">That is because when you extend the model cases, the time steps used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="44956-201">따라서 두 개의 새 데이터 요소를 추가하면 반환되는 처음 두 예측이 새 데이터와 겹치게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44956-201">Therefore, if you add two new data points, the first two predictions returned overlap with the new data.</span></span>  
  
-   <span data-ttu-id="44956-202">새 데이터 요소가 모두 사용된 후 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 업데이트된 모델을 기반으로 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="44956-202">After all the new data points are used up, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] makes predictions based on the updated model.</span></span> <span data-ttu-id="44956-203">따라서 2005년 9월부터 왼쪽 열에 있는 원래 모델의 M200 Europe에 대한 예측과 오른쪽 열에 있는 EXTEND_MODEL_CASES 사용 모델의 M200 Europe에 대한 예측이 달라지는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-203">Therefore, starting in September 2005, you can see the difference between predictions for M200 Europe from the original model, in the left-hand column, and the model that uses EXTEND_MODEL_CASES, in the right-hand column.</span></span> <span data-ttu-id="44956-204">모델이 새 데이터로 업데이트되었기 때문에 예측이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="44956-204">The predictions are different because the model has been updated with the new data.</span></span>  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a><span data-ttu-id="44956-205">시작 및 종료 시간 단계를 사용하여 예측 제어</span><span class="sxs-lookup"><span data-stu-id="44956-205">Using Start and End Time Steps to Control Predictions</span></span>  
 <span data-ttu-id="44956-206">모델을 확장하면 새 데이터가 항상 계열의 끝에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="44956-206">When you extend a model, the new data is always attached to the end of the series.</span></span> <span data-ttu-id="44956-207">그러나 예측을 위해 예측 쿼리에 사용되는 시간 조각은 원래 계열의 끝에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="44956-207">However, for the purpose of prediction, the time slices used for prediction queries start at the end of the original series.</span></span> <span data-ttu-id="44956-208">새 데이터를 추가할 때 새 예측만 얻으려면 시작 지점을 시간 조각 수로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-208">If you want to obtain only the new predictions when you add the new data, you must specify the starting point as a number of time slices.</span></span> <span data-ttu-id="44956-209">예를 들어 두 개의 새 데이터 요소를 추가하고 네 개의 새 예측을 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-209">For example, if you are adding two new data points and want to make four new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="44956-210">시계열 모델에 대해 PREDICTION JOIN을 만들고 2개월에 상당하는 새 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-210">Create a PREDICTION JOIN on a time series model, and specify two months of new data.</span></span>  
  
-   <span data-ttu-id="44956-211">네 개의 시간 조각에 대한 예측을 요청합니다. 여기에서 시작 지점은 3, 종료 지점은 시간 조각 6입니다.</span><span class="sxs-lookup"><span data-stu-id="44956-211">Request predictions for four time slices, where the starting point is 3, and the ending point is time slice 6.</span></span>  
  
 <span data-ttu-id="44956-212">즉, 새 데이터에 n 개의 시간 조각이 포함 되어 있는 상태에서 시간 단계 1부터 n까지에 대 한 예측을 요청 하면 예측은 새 데이터와 동일한 기간에 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-212">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data.</span></span> <span data-ttu-id="44956-213">가지고 있는 데이터의 범위를 벗어나는 기간에 대한 새 예측을 구하려면 새 데이터 계열 다음의 n+1 시간 조각에서 예측을 시작하거나 추가 시간 조각을 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-213">To get new predictions for a time periods not covered by your data, you must either start predictions at the time slice n+1 after the new data series, or make sure that you request additional time slices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44956-214">새 데이터를 추가할 때에는 기록 예측을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44956-214">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="44956-215">다음 예에서는 이전 예의 두 계열에 대해 새 예측만 얻을 수 있도록 하는 DMX 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44956-215">The following example shows the DMX statement that lets you get only the new predictions for the two series in the previous example.</span></span>  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 <span data-ttu-id="44956-216">예측 결과는 시간 조각 3에서 시작되며 이는 사용자가 제공한 2개월에 상당하는 새 데이터 다음입니다.</span><span class="sxs-lookup"><span data-stu-id="44956-216">The prediction results start at time slice 3, which is after the 2 months of new data that you supplied.</span></span>  
  
 <span data-ttu-id="44956-217">**제품 및 지역: 유럽 M200**</span><span class="sxs-lookup"><span data-stu-id="44956-217">**Product and Region: M200 Europe**</span></span>  
  
 <span data-ttu-id="44956-218">데이터가 업데이트된 모델(EXTEND_MODEL_CASES가 있는 PredictTimeSeries)</span><span class="sxs-lookup"><span data-stu-id="44956-218">Model with updated data (PredictTimeSeries with EXTEND_MODEL_CASES)</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="44956-219">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-219">M200 Europe</span></span>|<span data-ttu-id="44956-220">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-220">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-221">72</span><span class="sxs-lookup"><span data-stu-id="44956-221">72</span></span>|  
|<span data-ttu-id="44956-222">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-222">M200 Europe</span></span>|<span data-ttu-id="44956-223">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-223">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-224">69</span><span class="sxs-lookup"><span data-stu-id="44956-224">69</span></span>|  
|<span data-ttu-id="44956-225">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-225">M200 Europe</span></span>|<span data-ttu-id="44956-226">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-226">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-227">68</span><span class="sxs-lookup"><span data-stu-id="44956-227">68</span></span>|  
|<span data-ttu-id="44956-228">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="44956-228">M200 Europe</span></span>|<span data-ttu-id="44956-229">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44956-229">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="44956-230">89</span><span class="sxs-lookup"><span data-stu-id="44956-230">89</span></span>|  
  
## <a name="making-predictions-with-replace_model_cases"></a><span data-ttu-id="44956-231">REPLACE_MODEL_CASES로 예측 수행</span><span class="sxs-lookup"><span data-stu-id="44956-231">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="44956-232">모델 사례 대체는 하나의 사례 집합을 학습시킨 다음 이 모델을 다른 데이터 계열에 적용하려는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="44956-232">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span> <span data-ttu-id="44956-233">이 시나리오에 대 한 자세한 연습은 [2 단원: &#40;중급 데이터 마이닝 자습서&#41;예측 시나리오 빌드를 ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="44956-233">A detailed walkthrough of this scenario is presented in [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44956-234">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44956-234">See Also</span></span>  
 <span data-ttu-id="44956-235">[시계열 모델 쿼리 예제](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="44956-235">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="44956-236">PredictTimeSeries&#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="44956-236">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)  
  
  
