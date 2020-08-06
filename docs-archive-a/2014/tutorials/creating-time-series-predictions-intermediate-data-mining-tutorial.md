---
title: 시계열 예측 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1175cdffd1512e0cb876b9565dd0727a9f094c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648240"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="0db0a-102">시계열 예측 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="0db0a-102">Creating Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="0db0a-103">이 단원의 이전 태스크에서는 시계열 모델을 만들고 결과를 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-103">In the previous tasks in this lesson, you created a time series model and explored the results.</span></span> <span data-ttu-id="0db0a-104">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 항상 시계열 모델에 대한 5개의 예측으로 구성된 집합을 만들고 예측 값을 예측 차트의 일부분으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-104">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] always creates a set of five (5) predictions for a time series model and displays the predicted values as part of the forecasting chart.</span></span> <span data-ttu-id="0db0a-105">그러나 DMX(Data Mining Extensions) 예측 쿼리를 작성하여 예측을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-105">However, you can also create forecasts by building Data Mining Extensions (DMX) prediction queries.</span></span>  
  
 <span data-ttu-id="0db0a-106">이 태스크에서는 뷰어에서 본 것과 같은 예측을 생성하는 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-106">In this task, you will create a prediction query that generates the same predictions that you saw in the viewer.</span></span> <span data-ttu-id="0db0a-107">이 태스크에서는 사용자가 이미 기본 데이터 마이닝 자습서의 단원을 마쳤으며 예측 쿼리 작성기를 사용하는 방법에 익숙하다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-107">This task assumes that you have already completed the lessons in the Basic Data Mining Tutorial and are familiar with how to use Prediction Query Builder.</span></span> <span data-ttu-id="0db0a-108">이제 시계열 모델과 관련된 쿼리를 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-108">You will now learn how to create queries specific to time series models.</span></span>  
  
## <a name="creating-time-series-predictions"></a><span data-ttu-id="0db0a-109">시계열 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="0db0a-109">Creating Time Series Predictions</span></span>  
 <span data-ttu-id="0db0a-110">일반적으로 예측 쿼리를 만드는 첫 번째 단계는 마이닝 모델과 입력 테이블을 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-110">Typically, the first step in creating a prediction query is to select a mining model and input table.</span></span> <span data-ttu-id="0db0a-111">그러나 시계열 모델에는 일반 예측을 위해 추가 입력이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-111">However, a time series model does not require additional input for a regular prediction.</span></span> <span data-ttu-id="0db0a-112">따라서 모델에 데이터를 추가하거나 데이터를 바꾸지 않는 한 예측을 만들 때 새로운 데이터 원본을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-112">Therefore, you do not need to specify a new source of data when making predictions, unless you are adding data to the model or replacing the data.</span></span>  
  
 <span data-ttu-id="0db0a-113">이 단원에서는 예측 단계 수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-113">For this lesson, you must specify the number of prediction steps.</span></span> <span data-ttu-id="0db0a-114">특정 제품 및 지역 조합에 대한 예측을 얻기 위해 계열 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-114">You can specify the series name, to get a prediction for a particular combination of a product and a region.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="0db0a-115">모델과 입력 테이블을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="0db0a-115">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="0db0a-116">데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에 있는 **마이닝 모델** 상자에서 **모델 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-116">On the **Mining Model Prediction** tab of the Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="0db0a-117">**마이닝 모델 선택** 대화 상자에서 예측 구조를 확장 하 고 목록에서 **예측** 모델을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-117">In the **Select Mining Model** dialog box, expand the Forecasting structure, select the **Forecasting** model from the list, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0db0a-118">**입력 테이블 선택** 상자를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-118">Ignore the **Select Input Table(s)** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0db0a-119">시계열 모델의 경우 교차 예측을 수행하지 않는 한 별도의 입력을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-119">For a time series model, you do not need to specify a separate input unless you are doing cross-prediction.</span></span>  
  
4.  <span data-ttu-id="0db0a-120">**마이닝 모델 예측** 탭의 표에 있는 **원본** 열에서 첫 번째 빈 행의 셀을 클릭 한 다음 **마이닝 모델 예측**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-120">In the **Source** column, in the grid on the **Mining Model Prediction** tab, click the cell in the first empty row, and then select **Forecasting mining model**.</span></span>  
  
5.  <span data-ttu-id="0db0a-121">**필드** 열에서 **모델 영역**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-121">In the **Field** column, select **Model Region**.</span></span>  
  
     <span data-ttu-id="0db0a-122">이렇게 하면 예측이 적용되는 모델 및 지역 조합을 나타내기 위해 예측 쿼리에 계열 식별자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-122">This action adds the series identifier to the prediction query to indicate the combination of model and region to which the prediction applies.</span></span>  
  
6.  <span data-ttu-id="0db0a-123">**원본** 열에서 다음 빈 행을 클릭 한 다음 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-123">Click the next empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
7.  <span data-ttu-id="0db0a-124">**필드** 열에서 **PredictTimeSeries**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-124">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0db0a-125">`Predict` 함수도 시계열 모델에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-125">You can also use the `Predict` function with time series models.</span></span> <span data-ttu-id="0db0a-126">그러나 기본적으로 Predict 함수는 각 계열에 대해 하나의 예측만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-126">However, by default, the Predict function creates only one prediction for each series.</span></span> <span data-ttu-id="0db0a-127">따라서 여러 예측 단계를 지정 하려면 **PredictTimeSeries** 함수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-127">Therefore, to specify multiple prediction steps, you must use the **PredictTimeSeries** function.</span></span>  
  
8.  <span data-ttu-id="0db0a-128">**마이닝 모델** 창에서 마이닝 모델 열 Amount를 선택 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="0db0a-128">In the **Mining Model** pane, select the mining model column, **Amount.**</span></span> <span data-ttu-id="0db0a-129">Amount를 이전에 추가한 **PredictTimeSeries** 함수에 대 한 **조건/인수** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-129">Drag Amount to the **Criteria/Arguments** box for the **PredictTimeSeries** function that you added earlier.</span></span>  
  
9. <span data-ttu-id="0db0a-130">**조건/인수** 상자를 클릭 하 고 필드 이름 다음에 쉼표와 **5**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-130">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="0db0a-131">이제 **조건/인수** 상자의 텍스트가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-131">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[Amount],5`  
  
10. <span data-ttu-id="0db0a-132">**별칭** 열에을 입력 `PredictAmount` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-132">In the **Alias** column, type `PredictAmount`.</span></span>  
  
11. <span data-ttu-id="0db0a-133">**원본** 열에서 다음 빈 행을 클릭 한 다음 **예측 함수** 를 다시 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-133">Click the next empty row in the **Source** column, and then select **Prediction Function** again.</span></span>  
  
12. <span data-ttu-id="0db0a-134">**필드** 열에서 **PredictTimeSeries**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-134">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
13. <span data-ttu-id="0db0a-135">**마이닝 모델** 창에서 열 수량을 선택한 다음 두 번째 **PredictTimeSeries** 함수에 대 한 **조건/인수** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-135">In the **Mining Model** pane, select the column Quantity, and then drag it into the **Criteria/Arguments** box for the second **PredictTimeSeries** function.</span></span>  
  
14. <span data-ttu-id="0db0a-136">**조건/인수** 상자를 클릭 하 고 필드 이름 다음에 쉼표와 **5**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-136">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="0db0a-137">이제 **조건/인수** 상자의 텍스트가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-137">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[ Quantity],5`  
  
15. <span data-ttu-id="0db0a-138">**별칭** 열에을 입력 `PredictQuantity` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-138">In the **Alias** column, type `PredictQuantity`.</span></span>  
  
16. <span data-ttu-id="0db0a-139">**쿼리 결과 뷰로 전환을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-139">Click **Switch to query result view**.</span></span>  
  
     <span data-ttu-id="0db0a-140">쿼리 결과가 테이블 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-140">The results of the query are displayed in tabular format.</span></span>  
  
 <span data-ttu-id="0db0a-141">열 값을 사용하는 결과 하나와 예측 함수에서 예측 값을 가져오는 결과 두 개를 합쳐 세 가지 유형의 결과를 쿼리 작성기에서 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-141">Remember that you created three different types of results in the query builder, one that uses values from a column, and two that get predicted values from a prediction function.</span></span> <span data-ttu-id="0db0a-142">따라서 쿼리 결과에 세 개의 다른 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-142">Therefore, the results of the query contain three separate columns.</span></span> <span data-ttu-id="0db0a-143">첫 번째 열에는 제품 및 지역 조합 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-143">The first column contains the list of product and region combinations.</span></span> <span data-ttu-id="0db0a-144">두 번째 및 세 번째 열에는 각각 예측 결과의 중첩 테이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-144">The second and third columns each contain a nested table of prediction results.</span></span> <span data-ttu-id="0db0a-145">각 중첩 테이블에는 다음 표와 같은 시간 단계 및 예측 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-145">Each nested table contains the time step and predicted values, such as the following table:</span></span>  
  
 <span data-ttu-id="0db0a-146">결과 예(금액은 소수점 두 자리로 잘림):</span><span class="sxs-lookup"><span data-stu-id="0db0a-146">Example results (amounts are truncated to two decimal places):</span></span>  
  
 <span data-ttu-id="0db0a-147">**M200 유럽 PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="0db0a-147">**M200 Europe PredictAmount**</span></span>  
  
|<span data-ttu-id="0db0a-148">$TIME</span><span class="sxs-lookup"><span data-stu-id="0db0a-148">$TIME</span></span>|<span data-ttu-id="0db0a-149">금액</span><span class="sxs-lookup"><span data-stu-id="0db0a-149">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="0db0a-150">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-150">7/25/2008</span></span>|<span data-ttu-id="0db0a-151">99978.00</span><span class="sxs-lookup"><span data-stu-id="0db0a-151">99978.00</span></span>|  
|<span data-ttu-id="0db0a-152">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-152">8/25/2008</span></span>|<span data-ttu-id="0db0a-153">145575.07</span><span class="sxs-lookup"><span data-stu-id="0db0a-153">145575.07</span></span>|  
|<span data-ttu-id="0db0a-154">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-154">9/25/2008</span></span>|<span data-ttu-id="0db0a-155">116835.19</span><span class="sxs-lookup"><span data-stu-id="0db0a-155">116835.19</span></span>|  
|<span data-ttu-id="0db0a-156">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-156">10/25/2008</span></span>|<span data-ttu-id="0db0a-157">116537.38</span><span class="sxs-lookup"><span data-stu-id="0db0a-157">116537.38</span></span>|  
|<span data-ttu-id="0db0a-158">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-158">11/25/2008</span></span>|<span data-ttu-id="0db0a-159">107760.55</span><span class="sxs-lookup"><span data-stu-id="0db0a-159">107760.55</span></span>|  
  
 <span data-ttu-id="0db0a-160">**M200 유럽 PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="0db0a-160">**M200 Europe PredictQuantity**</span></span>  
  
|<span data-ttu-id="0db0a-161">$TIME</span><span class="sxs-lookup"><span data-stu-id="0db0a-161">$TIME</span></span>|<span data-ttu-id="0db0a-162">수량</span><span class="sxs-lookup"><span data-stu-id="0db0a-162">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="0db0a-163">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-163">7/25/2008</span></span>|<span data-ttu-id="0db0a-164">52</span><span class="sxs-lookup"><span data-stu-id="0db0a-164">52</span></span>|  
|<span data-ttu-id="0db0a-165">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-165">8/25/2008</span></span>|<span data-ttu-id="0db0a-166">67</span><span class="sxs-lookup"><span data-stu-id="0db0a-166">67</span></span>|  
|<span data-ttu-id="0db0a-167">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-167">9/25/2008</span></span>|<span data-ttu-id="0db0a-168">58</span><span class="sxs-lookup"><span data-stu-id="0db0a-168">58</span></span>|  
|<span data-ttu-id="0db0a-169">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-169">10/25/2008</span></span>|<span data-ttu-id="0db0a-170">57</span><span class="sxs-lookup"><span data-stu-id="0db0a-170">57</span></span>|  
|<span data-ttu-id="0db0a-171">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-171">11/25/2008</span></span>|<span data-ttu-id="0db0a-172">54</span><span class="sxs-lookup"><span data-stu-id="0db0a-172">54</span></span>|  
  
 <span data-ttu-id="0db0a-173">**M200 북아메리카-PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="0db0a-173">**M200 North America - PredictAmount**</span></span>  
  
|<span data-ttu-id="0db0a-174">$TIME</span><span class="sxs-lookup"><span data-stu-id="0db0a-174">$TIME</span></span>|<span data-ttu-id="0db0a-175">금액</span><span class="sxs-lookup"><span data-stu-id="0db0a-175">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="0db0a-176">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-176">7/25/2008</span></span>|<span data-ttu-id="0db0a-177">348533.93</span><span class="sxs-lookup"><span data-stu-id="0db0a-177">348533.93</span></span>|  
|<span data-ttu-id="0db0a-178">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-178">8/25/2008</span></span>|<span data-ttu-id="0db0a-179">340097.98</span><span class="sxs-lookup"><span data-stu-id="0db0a-179">340097.98</span></span>|  
|<span data-ttu-id="0db0a-180">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-180">9/25/2008</span></span>|<span data-ttu-id="0db0a-181">257986.19</span><span class="sxs-lookup"><span data-stu-id="0db0a-181">257986.19</span></span>|  
|<span data-ttu-id="0db0a-182">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-182">10/25/2008</span></span>|<span data-ttu-id="0db0a-183">374658.24</span><span class="sxs-lookup"><span data-stu-id="0db0a-183">374658.24</span></span>|  
|<span data-ttu-id="0db0a-184">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-184">11/25/2008</span></span>|<span data-ttu-id="0db0a-185">379241.44</span><span class="sxs-lookup"><span data-stu-id="0db0a-185">379241.44</span></span>|  
  
 <span data-ttu-id="0db0a-186">**M200 북아메리카-PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="0db0a-186">**M200 North America - PredictQuantity**</span></span>  
  
|<span data-ttu-id="0db0a-187">$TIME</span><span class="sxs-lookup"><span data-stu-id="0db0a-187">$TIME</span></span>|<span data-ttu-id="0db0a-188">수량</span><span class="sxs-lookup"><span data-stu-id="0db0a-188">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="0db0a-189">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-189">7/25/2008</span></span>|<span data-ttu-id="0db0a-190">272</span><span class="sxs-lookup"><span data-stu-id="0db0a-190">272</span></span>|  
|<span data-ttu-id="0db0a-191">8/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-191">8/25/2008</span></span>|<span data-ttu-id="0db0a-192">152</span><span class="sxs-lookup"><span data-stu-id="0db0a-192">152</span></span>|  
|<span data-ttu-id="0db0a-193">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-193">9/25/2008</span></span>|<span data-ttu-id="0db0a-194">250</span><span class="sxs-lookup"><span data-stu-id="0db0a-194">250</span></span>|  
|<span data-ttu-id="0db0a-195">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-195">10/25/2008</span></span>|<span data-ttu-id="0db0a-196">181</span><span class="sxs-lookup"><span data-stu-id="0db0a-196">181</span></span>|  
|<span data-ttu-id="0db0a-197">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="0db0a-197">11/25/2008</span></span>|<span data-ttu-id="0db0a-198">290</span><span class="sxs-lookup"><span data-stu-id="0db0a-198">290</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="0db0a-199">예제 데이터베이스에 사용된 날짜가 이 릴리스에 맞게 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-199">The dates that are used in the sample database have changed for this release.</span></span> <span data-ttu-id="0db0a-200">이전 버전의 예제 데이터를 사용하는 경우에는 결과가 다르게 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-200">If you are using an earlier version of the sample data, you might see different results.</span></span>  
  
## <a name="saving-the-prediction-results"></a><span data-ttu-id="0db0a-201">예측 결과 저장</span><span class="sxs-lookup"><span data-stu-id="0db0a-201">Saving the Prediction Results</span></span>  
 <span data-ttu-id="0db0a-202">예측 결과를 사용하기 위한 여러 다른 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-202">You have several different options for using the prediction results.</span></span> <span data-ttu-id="0db0a-203">결과를 일반화하고 결과 뷰에서 데이터를 복사하여 Excel 워크시트 또는 다른 파일에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-203">You can flatten the results, copy the data from the Results view, and paste it into an Excel worksheet or other file.</span></span>  
  
 <span data-ttu-id="0db0a-204">결과 저장 프로세스를 간소화하기 위해 데이터 마이닝 디자이너에서도 데이터를 데이터 원본 뷰에 저장할 수 있는 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-204">To simplify the process of saving results, Data Mining Designer also provides the ability to save the data to a data source view.</span></span> <span data-ttu-id="0db0a-205">데이터 원본 뷰에 결과를 저장하는 기능은 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-205">The functionality for saving results to a data source view is available only in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0db0a-206">결과는 일반 형식으로만 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-206">The results can only be stored in a flattened format.</span></span>  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a><span data-ttu-id="0db0a-207">결과 창에서 결과를 평면화하려면</span><span class="sxs-lookup"><span data-stu-id="0db0a-207">To flatten the results in the Results pane</span></span>  
  
1.  <span data-ttu-id="0db0a-208">예측 쿼리 작성기에서 **쿼리 디자인 뷰로 전환을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-208">In the Prediction Query Builder, click **Switch to query design view**.</span></span>  
  
     <span data-ttu-id="0db0a-209">DMX 쿼리 텍스트를 수동으로 편집할 수 있도록 뷰가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-209">The view changes to allow manual editing of the DMX query text.</span></span>  
  
2.  <span data-ttu-id="0db0a-210">`FLATTENED` 키워드 다음에 `SELECT` 키워드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-210">Type the `FLATTENED` keyword after the `SELECT` keyword.</span></span> <span data-ttu-id="0db0a-211">전체 쿼리 텍스트가 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-211">The complete query text should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  <span data-ttu-id="0db0a-212">필요에 따라 다음 예와 같이 결과를 제한하는 절을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-212">Optionally, you can type a clause to restrict the results, such as the following example:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  <span data-ttu-id="0db0a-213">**쿼리 결과 뷰로 전환을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-213">Click **Switch to query result view**.</span></span>  
  
#### <a name="to-export-prediction-query-results"></a><span data-ttu-id="0db0a-214">예측 쿼리 결과를 내보내려면</span><span class="sxs-lookup"><span data-stu-id="0db0a-214">To export prediction query results</span></span>  
  
1.  <span data-ttu-id="0db0a-215">**쿼리 결과 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-215">Click **Save query results**.</span></span>  
  
2.  <span data-ttu-id="0db0a-216">데이터 **마이닝 쿼리 결과 저장** 대화 상자에서 **데이터 원본**에 대해를 선택 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-216">In the **Save Data Mining Query Result** dialog box, for **Data Source**, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="0db0a-217">데이터를 다른 관계형 데이터베이스에 저장하려는 경우 데이터 원본을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-217">You can also create a data source if you want to save the data to a different relational database.</span></span>  
  
3.  <span data-ttu-id="0db0a-218">**테이블 이름** 열에 **테스트 예측**등의 새 임시 테이블 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-218">In the **Table Name** column, type a new temporary table name, such as **Test Predictions**.</span></span>  
  
4.  <span data-ttu-id="0db0a-219">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-219">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0db0a-220">만든 테이블을 보려면 데이터를 저장한 인스턴스의 데이터베이스 엔진에 대한 연결을 만들고 쿼리를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="0db0a-220">To view the table that you created, create a connection to the database engine of the instance where you saved the data, and create a query.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="0db0a-221">결론</span><span class="sxs-lookup"><span data-stu-id="0db0a-221">Conclusion</span></span>  
 <span data-ttu-id="0db0a-222">기본 시계열 모델을 작성하고 예측을 해석 및 생성하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-222">You have learned how to build a basic time series model, interpret the forecasts, and create predictions.</span></span>  
  
 <span data-ttu-id="0db0a-223">이 자습서의 나머지 태스크는 선택 사항이며 고급 시계열 예측에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-223">The remaining tasks in this tutorial are optional, and describe advanced time series predictions.</span></span> <span data-ttu-id="0db0a-224">계속하기로 결정한 경우 새 데이터를 모델에 추가하고 확장된 계열에 대해 예측을 생성하는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-224">If you decide to go on, you will learn how to add new data to your model and create predictions on the extended series.</span></span> <span data-ttu-id="0db0a-225">또한 모델의 추세를 사용하되 데이터는 새 데이터 계열로 교체하여 교차 예측을 수행하는 방법도 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="0db0a-225">You will also learn how to perform cross-prediction, by using the trend in the model but replacing the data with a new series of data.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="0db0a-226">다음 단원</span><span class="sxs-lookup"><span data-stu-id="0db0a-226">Next Lesson</span></span>  
 [<span data-ttu-id="0db0a-227">고급 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="0db0a-227">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="0db0a-228">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0db0a-228">See Also</span></span>  
 [<span data-ttu-id="0db0a-229">시계열 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="0db0a-229">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
