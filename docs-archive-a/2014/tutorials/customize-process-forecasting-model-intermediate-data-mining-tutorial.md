---
title: 예측 모델 사용자 지정 및 처리 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 03dc67907b22750eb1b8539feaddec58f61f702f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653082"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="ec728-102">예측 모델 사용자 지정 및 처리(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="ec728-102">Customizing and Processing the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="ec728-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘은 모델을 만들고 시간 데이터를 분석하는 방법에 영향을 주는 여러 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm provides parameters that affect how a model is created, and how time data is analyzed.</span></span> <span data-ttu-id="ec728-104">이러한 속성을 변경하면 마이닝 모델이 예측을 수행하는 방식에 큰 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-104">Changing these properties can significantly affect how the mining model makes predictions.</span></span>  
  
 <span data-ttu-id="ec728-105">자습서에서 이러한 태스크를 위해 다음 작업을 수행하여 모델을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-105">For this task in the tutorial, you will perform the following tasks to modify the model:</span></span>  
  
1.  <span data-ttu-id="ec728-106">*PERIODICITY_HINT* 매개 변수에 대 한 새 값을 추가 하 여 모델이 기간을 처리 하는 방식을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-106">You will customize the way your model handles time periods by adding a new value for the *PERIODICITY_HINT* parameter.</span></span>  
  
2.  <span data-ttu-id="ec728-107">Microsoft 시계열 알고리즘에 대 한 두 가지 중요 한 매개 변수, 즉 예측에 사용 되는 방법을 제어할 수 있는 FORECAST_METHOD 및 장기 및 단기 예측의 혼합을 사용자 지정할 수 있는 PREDICTION_SMOOTHING에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-107">You will learn about two other important parameters for the Microsoft Time Series algorithm: FORECAST_METHOD, which lets you control the method used for forecasting, and PREDICTION_SMOOTHING, which lets you customize the blend of long-term and short-term predictions.</span></span>  
  
3.  <span data-ttu-id="ec728-108">필요에 따라 귀속되는 누락된 값의 처리 방식을 알고리즘에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-108">Optionally, you will tell the algorithm how you want missing values to be imputed.</span></span>  
  
4.  <span data-ttu-id="ec728-109">모든 변경이 적용되면 모델을 배포하고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-109">After all the changes have been made, you will deploy and process the model.</span></span>  
  
## <a name="setting-time-series-parameters"></a><span data-ttu-id="ec728-110">시계열 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="ec728-110">Setting Time Series Parameters</span></span>  
 <span data-ttu-id="ec728-111">**주기성 힌트**</span><span class="sxs-lookup"><span data-stu-id="ec728-111">**Periodicity Hints**</span></span>  
  
 <span data-ttu-id="ec728-112">*PERIODICITY_HINT* 매개 변수는 데이터에 표시 되어야 하는 추가 기간에 대 한 정보를 알고리즘에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-112">The *PERIODICITY_HINT* parameter provides the algorithm with information about additional time periods that you expect to see in the data.</span></span> <span data-ttu-id="ec728-113">기본적으로 시계열 모델은 자동으로 데이터에서 패턴을 감지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-113">By default, time series models will try to automatically detect a pattern in the data.</span></span> <span data-ttu-id="ec728-114">그러나 예측 시간 주기를 이미 알고 있는 경우 주기성 힌트를 제공하여 잠재적으로 모델의 정확도를 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-114">However, if you already know the expected time cycle, providing a periodicity hint can potentially improve the accuracy of the model.</span></span> <span data-ttu-id="ec728-115">반면 잘못된 주기성 힌트를 제공한 경우 정확도를 떨어뜨릴 수 있으므로, 사용해야 할 값에 확신이 없는 경우 기본값을 사용하는 것이 최선입니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-115">However, if you provide the wrong periodicity hint, it can decrease accuracy; therefore, if you are not sure what value should be used, it is best to use the default.</span></span>  
  
 <span data-ttu-id="ec728-116">예를 들어, 이 모델에 사용된 뷰에서는 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]로부터 판매 데이터를 월별로 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-116">For example, the view used for this model aggregates sales data from [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] on a monthly basis.</span></span> <span data-ttu-id="ec728-117">따라서 모델에 사용된 각 시간 조각은 한 달을 나타내며 또한 모든 예측은 개월 수 기준입니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-117">Therefore each time slice used by the model represents one month, and all predictions will also be in terms of months.</span></span> <span data-ttu-id="ec728-118">1 년에 12 개월이 발생 하 고 해당 판매 패턴이 매년 반복 될 것으로 간주 되기 때문에 *PERIODICITY_HINT* 매개 변수를로 설정 하 여 `12` 12 개의 시간 조각 (months)이 전체 판매 주기를 구성 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-118">Since there are 12 months in a year and you expect that sales patterns more or less repeat on a yearly basis, you will set the *PERIODICITY_HINT* parameter to `12`, to indicate that 12 time slices (months) constitute one complete sales cycle.</span></span>  
  
 <span data-ttu-id="ec728-119">**예측 메서드**</span><span class="sxs-lookup"><span data-stu-id="ec728-119">**Forecasting Method**</span></span>  
  
 <span data-ttu-id="ec728-120">*FORECAST_METHOD* 매개 변수는 시계열 알고리즘이 단기 또는 장기 예측에 대해 최적화 되어 있는지 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-120">The *FORECAST_METHOD* parameter controls whether the time series algorithm is optimized for short-term or long-term predictions.</span></span> <span data-ttu-id="ec728-121">기본적으로 *FORECAST_METHOD* 매개 변수는 MIXED로 설정 됩니다. 즉, 단기 및 장기 예측 모두에 적합 한 결과를 제공 하기 위해 서로 다른 두 알고리즘을 혼합 하 고 분산 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-121">By default, the *FORECAST_METHOD* parameter is set to MIXED, which means that two different algorithms are blended and balanced to provide good results for both short-term and long-term prediction.</span></span>  
  
 <span data-ttu-id="ec728-122">그러나 특정 알고리즘을 사용하려는 경우 값을 ARIMA 또는 ARTXP로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-122">However, if you know that you want to use a particular algorithm, you can change the value to either ARIMA or ARTXP.</span></span>  
  
 <span data-ttu-id="ec728-123">**장기 조건 및 단기 예측**</span><span class="sxs-lookup"><span data-stu-id="ec728-123">**Weighting Long-Term vs. Short-Term Predictions**</span></span>  
  
 <span data-ttu-id="ec728-124">또한 PREDICTION_SMOOTHING 매개 변수를 사용하여 장기 및 단기 예측이 혼합되는 방식을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-124">You can also customize the way that long-term and short-term predictions are combined by using the PREDICTION_SMOOTHING parameter.</span></span> <span data-ttu-id="ec728-125">기본적으로 이 매개 변수는 0.5로 설정됩니다. 이 값은 전체적으로 적절한 정확도를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-125">By default, this parameter is set to 0.5, which generally provides the best balance for overall accuracy.</span></span>  
  
#### <a name="to-change-the-algorithm-parameters"></a><span data-ttu-id="ec728-126">알고리즘 매개 변수를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ec728-126">To change the algorithm parameters</span></span>  
  
1.  <span data-ttu-id="ec728-127">**마이닝 모델** 탭에서 **예측**을 마우스 오른쪽 단추로 클릭 하 고 **알고리즘 매개 변수 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-127">On the **Mining Models** tab, right-click **Forecasting**, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="ec728-128">`PERIODICITY_HINT` **알고리즘 매개 변수** 대화 상자의 행에서 **값** 열을 클릭 한 다음 중괄호를 포함 하 여을 입력 합니다 `{12}` .</span><span class="sxs-lookup"><span data-stu-id="ec728-128">In the `PERIODICITY_HINT` row of the **Algorithm Parameters** dialog box, click the **Value** column, then type `{12}`, including the braces.</span></span>  
  
     <span data-ttu-id="ec728-129">기본적으로 알고리즘에서도 값 {1}을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-129">By default, the algorithm will also add the value {1}.</span></span>  
  
3.  <span data-ttu-id="ec728-130">행에서 `FORECAST_METHOD` **값** 텍스트 상자가 비어 있거나로 설정 되었는지 확인 `MIXED` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-130">In the `FORECAST_METHOD` row, verify that the **Value** text box is either blank or set to `MIXED`.</span></span> <span data-ttu-id="ec728-131">다른 값을 입력 한 경우 `MIXED` 를 입력 하 여 매개 변수를 다시 기본값으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-131">If a different value has been entered, type `MIXED` to change the parameter back to the default value.</span></span>  
  
4.  <span data-ttu-id="ec728-132">**PREDICTION_SMOOTHING** 행에서 **값** 텍스트 상자가 비어 있거나 0.5로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-132">In the **PREDICTION_SMOOTHING** row, verify that the **Value** text box is either blank or set to 0.5.</span></span> <span data-ttu-id="ec728-133">다른 값을 입력 한 경우 **값** 을 클릭 하 고 `0.5` 를 입력 하 여 매개 변수를 다시 기본값으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-133">If a different value has been entered, click **Value** and type `0.5` to change the parameter back to the default value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec728-134">PREDICTION_SMOOTHING 매개 변수는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-134">The PREDICTION_SMOOTHING parameter is available only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="ec728-135">따라서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard에서 PREDICTION_SMOOTHING 매개 변수의 값을 보거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-135">Therefore, you cannot view or change the value of the PREDICTION_SMOOTHING parameter in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard.</span></span> <span data-ttu-id="ec728-136">하지만 기본 동작은 두 알고리즘을 모두 사용하고 두 알고리즘에 똑같은 가중치를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-136">However, the default behavior is to use both algorithms and weight them equally.</span></span>  
  
5.  <span data-ttu-id="ec728-137">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-137">Click **OK**.</span></span>  
  
## <a name="handling-missing-data-optional"></a><span data-ttu-id="ec728-138">누락된 데이터 처리(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="ec728-138">Handling Missing Data (Optional)</span></span>  
 <span data-ttu-id="ec728-139">대부분의 경우 매출 데이터는 Null로 채워지는 간격이 있거나 매장에서 보고 최종 기한을 충족하지 않아 계열의 끝에 빈 셀이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-139">In many cases, your sales data might have gaps that are filled with nulls, or a store might have failed to meet the reporting deadline, leaving an empty cell at the end of the series.</span></span> <span data-ttu-id="ec728-140">그러한 시나리오에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]가 다음 오류를 발생시키고 모델을 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-140">In such scenarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] raises the following error and will not process the model.</span></span>  
  
 <span data-ttu-id="ec728-141">"오류 (데이터 마이닝): 마이닝 모델의 시리즈부터 타임 스탬프가 동기화 되지 않았습니다 \<series name> \<model name> .</span><span class="sxs-lookup"><span data-stu-id="ec728-141">"Error (Data mining): Time stamps not synchronized starting with series \<series name>, of the mining model, \<model name>.</span></span> <span data-ttu-id="ec728-142">모든 시계열은 같은 시간 표식에서 끝나야 하며 임의의 누락 데이터 요소가 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-142">All time series must end at the same time mark and cannot have arbitrarily missing data points.</span></span> <span data-ttu-id="ec728-143">MISSING_VALUE_SUBSTITUTION 매개 변수를 Previous 또는 숫자 상수로 설정하면 누락 데이터 요소가 자동으로 패치됩니다."</span><span class="sxs-lookup"><span data-stu-id="ec728-143">Setting the MISSING_VALUE_SUBSTITUTION parameter to Previous or to a numeric constant will automatically patch missing data points where possible."</span></span>  
  
 <span data-ttu-id="ec728-144">이 오류가 발생하지 않도록 하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 다음 메서드 중 하나를 사용하여 간격을 채울 새 값을 자동으로 제공하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-144">To avoid this error, you can specify that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically provide new values to fill in the gaps by using any one of the following methods:</span></span>  
  
-   <span data-ttu-id="ec728-145">평균 값 사용.</span><span class="sxs-lookup"><span data-stu-id="ec728-145">Using an average value.</span></span> <span data-ttu-id="ec728-146">평균은 같은 데이터 계열의 유효한 모든 값을 사용하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-146">The mean is calculated by using all valid values in the same data series.</span></span>  
  
-   <span data-ttu-id="ec728-147">이전 값 사용.</span><span class="sxs-lookup"><span data-stu-id="ec728-147">Using the previous value.</span></span> <span data-ttu-id="ec728-148">누락된 여러 셀에 대해 이전 값을 대체할 수 있지만 시작 값을 채울 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-148">You can substitute previous values for multiple missing cells, but you cannot fill starting values.</span></span>  
  
-   <span data-ttu-id="ec728-149">제공한 상수 값 사용</span><span class="sxs-lookup"><span data-stu-id="ec728-149">Using a constant value that you supply.</span></span>  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a><span data-ttu-id="ec728-150">평균값을 계산하여 간격을 채우도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ec728-150">To specify that gaps be filled by averaging values</span></span>  
  
1.  <span data-ttu-id="ec728-151">**마이닝 모델** 탭에서 **예측** 열을 마우스 오른쪽 단추로 클릭 하 고 **알고리즘 매개 변수 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-151">On the **Mining Models** tab, right-click the **Forecasting** column, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="ec728-152">**알고리즘 매개 변수** 대화 상자의 **MISSING_VALUE_SUBSTITUTION** 행에서 **값** 열을 클릭 하 고을 입력 `Mean` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-152">In the **Algorithm Parameters** dialog box, in the **MISSING_VALUE_SUBSTITUTION** row, click the **Value** column, and type `Mean`.</span></span>  
  
## <a name="build-the-model"></a><span data-ttu-id="ec728-153">모델 작성</span><span class="sxs-lookup"><span data-stu-id="ec728-153">Build the Model</span></span>  
 <span data-ttu-id="ec728-154">모델을 사용하려면 모델을 서버에 배포하고 알고리즘을 통해 학습 데이터를 실행하여 모델을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-154">To use the model, you must deploy it to a server, and process the model by running the training data through the algorithm.</span></span>  
  
#### <a name="to-process-the-forecasting-model"></a><span data-ttu-id="ec728-155">예측 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="ec728-155">To process the forecasting model</span></span>  
  
1.  <span data-ttu-id="ec728-156">의 **마이닝 모델** 메뉴에서 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] **마이닝 구조 및 모든 모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-156">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="ec728-157">프로젝트를 빌드 및 배포할지를 요청 하는 경고에서 **예**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-157">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="ec728-158">**마이닝 구조 처리-예측** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-158">In the **Process Mining Structure - Forecasting** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="ec728-159">**처리 진행률** 대화 상자가 열리고 모델 처리에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-159">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="ec728-160">모델 처리는 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-160">Model processing may take some time.</span></span>  
  
4.  <span data-ttu-id="ec728-161">처리가 완료 되 면 **닫기** 를 클릭 하 여 처리 **진행률** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-161">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="ec728-162">**닫기** 를 다시 클릭 하 여 **마이닝 구조 처리-예측** 대화 상자를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec728-162">Click **Close** again to exit the **Process Mining Structure - Forecasting** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ec728-163">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ec728-163">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ec728-164">예측 모델 탐색 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="ec728-164">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec728-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec728-165">See Also</span></span>  
 <span data-ttu-id="ec728-166">[Microsoft 시계열 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ec728-166">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="ec728-167">[Microsoft 시계열 알고리즘](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ec728-167">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="ec728-168">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ec728-168">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
