---
title: 고급 시계열 예측 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70ebf856ba0782cbf44969aba30602818015582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735668"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="74c8a-102">고급 시계열 예측(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="74c8a-102">Advanced Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="74c8a-103">예측 모델 탐색을 통해 대부분 지역의 판매는 유사한 패턴을 따르지만 태평양 지역의 M200 모델과 같이 특정 지역 및 모델은 서로 매우 다른 추세를 보여 준다는 사실을 알았습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-103">You saw from exploring the forecasting model that although sales in most of the regions follow a similar pattern, some regions and some models, such as the M200 model in the Pacific region, exhibit very different trends.</span></span> <span data-ttu-id="74c8a-104">이는 놀라운 일이 아니고 알려진 바와 같이 지역 간 차이는 일반적인 것이며 마케팅 홍보, 정확하지 않은 보고 또는 지정학적 사건과 같은 많은 요인으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-104">This does not surprise you, as you know that differences among regions are common and can be caused by many factors, including marketing promotions, inaccurate reporting, or geopolitical events.</span></span>  
  
 <span data-ttu-id="74c8a-105">그러나 사용자가 전 세계에 적용될 수 있는 모델을 요청할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-105">However, your users are asking for a model that can be applied worldwide.</span></span> <span data-ttu-id="74c8a-106">따라서 개별적인 요인이 예측에 끼치는 영향을 최소화하기 위해 전 세계 판매의 집계 측정값을 기반으로 하는 모델을 작성하기로 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-106">Therefore, to minimize the effect of individual factors on projections, you decide to build a model that is based on aggregated measures of worldwide sales.</span></span> <span data-ttu-id="74c8a-107">그런 다음 이 모델을 사용하여 각 개별 지역에 대해 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-107">You can then use this model to make predictions for each individual region.</span></span>  
  
 <span data-ttu-id="74c8a-108">이 태스크에서는 고급 예측 태스크를 수행하는 데 필요한 모든 데이터 원본을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-108">In this task, you will build all the data sources that you need to perform the advanced prediction tasks.</span></span> <span data-ttu-id="74c8a-109">예측 쿼리에 대한 입력으로 사용할 데이터 원본 뷰 두 개와 새 모델을 만드는 데 사용할 데이터 원본 뷰 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-109">You will create two data source views for use as inputs to the prediction query, and one data source view to use in building a new model.</span></span>  
  
 <span data-ttu-id="74c8a-110">**단계**</span><span class="sxs-lookup"><span data-stu-id="74c8a-110">**Steps**</span></span>  
  
1.  [<span data-ttu-id="74c8a-111">확장 판매 데이터 준비(예측용)</span><span class="sxs-lookup"><span data-stu-id="74c8a-111">Prepare the extended sales data (for prediction)</span></span>](#bkmk_newExtendData)  
  
2.  [<span data-ttu-id="74c8a-112">집계된 데이터 준비(모델 작성용)</span><span class="sxs-lookup"><span data-stu-id="74c8a-112">Prepare the aggregated data (for building the model)</span></span>](#bkmk_newReplaceData)  
  
3.  [<span data-ttu-id="74c8a-113">계열 데이터 준비(교차 예측용)</span><span class="sxs-lookup"><span data-stu-id="74c8a-113">Prepare the series data (for cross-prediction)</span></span>](#bkmk_CrossData2)  
  
4.  [<span data-ttu-id="74c8a-114">EXTEND를 사용한 예측</span><span class="sxs-lookup"><span data-stu-id="74c8a-114">Predict using EXTEND</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [<span data-ttu-id="74c8a-115">교차 예측 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="74c8a-115">Create the cross-prediction model</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [<span data-ttu-id="74c8a-116">REPLACE를 사용한 예측</span><span class="sxs-lookup"><span data-stu-id="74c8a-116">Predict using REPLACE</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [<span data-ttu-id="74c8a-117">새 예측 검토</span><span class="sxs-lookup"><span data-stu-id="74c8a-117">Review the new predictions</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a><span data-ttu-id="74c8a-118">새 확장 판매 데이터 만들기</span><span class="sxs-lookup"><span data-stu-id="74c8a-118">Creating the New Extended Sales Data</span></span>  
 <span data-ttu-id="74c8a-119">판매 데이터를 업데이트하려면 최신 판매 수치가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-119">To update your sales data, you will need to get the latest sales figures.</span></span> <span data-ttu-id="74c8a-120">신규 매장에 대한 관심을 불러일으키고 해당 제품의 인지도를 높이기 위해 지역 판매 홍보를 실시한 태평양 지역 내 데이터는 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-120">Of particular interest are the data just in from the Pacific region, which launched a regional sales promotion to call attention to the new stores and raise awareness of their products.</span></span>  
  
 <span data-ttu-id="74c8a-121">이 시나리오에서는 두 지역에 대 한 새 데이터의 3 개월이 포함 된 Excel 통합 문서에서 데이터를 가져온 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-121">For this scenario, we'll assume that the data has been imported from an Excel workbook that contains just three months of new data for a couple of regions.</span></span> <span data-ttu-id="74c8a-122">Transact-sql 스크립트를 사용 하 여 데이터에 대 한 테이블을 만든 다음 예측에 사용할 데이터 원본 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-122">You'll create a table for the data using a Transact-SQL script, and then define a data source view to use for prediction.</span></span>  
  
#### <a name="create-the-table-with-new-sales-data"></a><span data-ttu-id="74c8a-123">새 판매 데이터가 있는 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="74c8a-123">Create the table with new sales data</span></span>  
  
1.  <span data-ttu-id="74c8a-124">Transact-SQL 쿼리 창에서 다음 문을 실행하여 판매 데이터를 AdventureWorksDW 데이터베이스 또는 기타 데이터베이스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-124">In a Transact-SQL query window, execute the following statement to add the sales data to the AdventureWorksDW database (or any other database).</span></span>  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  <span data-ttu-id="74c8a-125">다음 스크립트를 사용하여 새 값을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-125">Insert the new values using the following script.</span></span>  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  <span data-ttu-id="74c8a-126">쉼표 구분 기호 및 통화 기호 사용 시 발생하는 문제를 방지하기 위해 따옴표가 통화 값에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-126">The quotation marks are used with the currency values to prevent problems with the comma separator and the currency symbol.</span></span> <span data-ttu-id="74c8a-127">또한 다음과 같은 서식에 통화 값을 전달할 수 있습니다. `130170.22`</span><span class="sxs-lookup"><span data-stu-id="74c8a-127">You could also pass in the currency values in this format: `130170.22`</span></span>  
    >   
    >  <span data-ttu-id="74c8a-128">예제 데이터베이스에 사용된 날짜가 이 릴리스에 맞게 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-128">Note that the dates used in the sample database have changed for this release.</span></span> <span data-ttu-id="74c8a-129">이전 버전의 AdventureWorks를 사용하는 경우에는 이에 따라 삽입된 날짜를 조정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-129">If you are using an earlier edition of AdventureWorks, you might need to adjust the inserted dates accordingly.</span></span>  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a><span data-ttu-id="74c8a-130">새 판매 데이터를 사용 하 여 데이터 원본 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="74c8a-130">Create a data source view using the new sales data</span></span>  
  
1.  <span data-ttu-id="74c8a-131">**솔루션 탐색기**에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-131">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="74c8a-132">데이터 원본 뷰 마법사에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-132">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="74c8a-133">**데이터 원본**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c8a-133">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="74c8a-134">**테이블 및 뷰 선택**: 방금 만든 테이블 (NewSalesData)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-134">**Select Tables and Views**: Select the table that you just created, NewSalesData.</span></span>  
  
3.  <span data-ttu-id="74c8a-135">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-135">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="74c8a-136">데이터 원본 뷰 디자인 화면에서 NewSalesData를 마우스 오른쪽 단추로 클릭 한 다음 **데이터 탐색** 을 선택 하 여 데이터를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-136">In the Data Source View design surface, right-click NewSalesData, and then select **Explore Data** to verify the data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="74c8a-137">이 데이터는 예측에만 사용하므로 데이터는 불완전해도 상관없습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-137">You will use this data for prediction only, so it does not matter that the data is incomplete.</span></span>  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a><span data-ttu-id="74c8a-138">교차 예측 모델에 대 한 데이터 만들기</span><span class="sxs-lookup"><span data-stu-id="74c8a-138">Creating the Data for the Cross-Prediction Model</span></span>  
 <span data-ttu-id="74c8a-139">여러 자전거 모델이 더 적은 수의 범주로 축소되고 개별 국가의 결과가 지역별로 병합되는 등, 원래 예측 모델에 사용된 데이터는 vTimeSeries 뷰에 의해 이미 일부 그룹화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-139">The data that was used in the original forecasting model was already grouped somewhat by the view vTimeSeries, which collapsed several bike models into a smaller number of categories, and merged results from individual countries into regions.</span></span> <span data-ttu-id="74c8a-140">전 세계 예측에 사용할 수 있는 모델을 만들기 위해 데이터 원본 뷰 디자이너에서 직접 추가 단순 집계를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-140">To create a model that can be used for world-wide projections, you will create some additional simple aggregations directly in the Data Source View Designer.</span></span> <span data-ttu-id="74c8a-141">새 데이터 원본 뷰에는 전 지역의 모든 제품 판매에 대한 합계와 평균만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-141">The new data source view will contain just a sum and an average of the sales of all products for all regions.</span></span>  
  
 <span data-ttu-id="74c8a-142">모델에 사용할 데이터 원본을 만든 후에는 예측에 사용할 새 데이터 원본 뷰를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-142">After you have created the data source used for the model, you must create a new data source view to use for prediction.</span></span> <span data-ttu-id="74c8a-143">예를 들어, 새로운 전 세계 모델을 사용하여 유럽 지역의 판매를 예측하려는 경우 유럽 지역의 데이터만 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-143">For example, if you want to predict sales for Europe using the new worldwide model, you must feed in data for the Europe region only.</span></span> <span data-ttu-id="74c8a-144">따라서 원래 데이터를 필터링하는 새 데이터 원본 뷰를 설정하고 각 예측 쿼리 집합에 대한 필터 조건을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-144">So you will set up a new data source view that filters the original data, and change the filter condition for each set of prediction queries.</span></span>  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a><span data-ttu-id="74c8a-145">사용자 지정 데이터 원본 뷰를 사용하여 모델 데이터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="74c8a-145">To create the model data using a custom data source view</span></span>  
  
1.  <span data-ttu-id="74c8a-146">**솔루션 탐색기**에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-146">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="74c8a-147">마법사 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-147">On the welcome page of the wizard, click **Next**.</span></span>  
  
3.  <span data-ttu-id="74c8a-148">**데이터 원본 선택** 페이지에서 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-148">On the **Select Data Source** page, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="74c8a-149">**테이블 및 뷰 선택**페이지에서 테이블을 추가 하지 않습니다. **다음**을 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-149">In the page, **Select Tables and Views**, do not add any tables-just click **Next**.</span></span>  
  
5.  <span data-ttu-id="74c8a-150">**마법사 완료**페이지에서 이름을 입력 한 `AllRegions` 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-150">On the page, **Completing the Wizard**, type the name `AllRegions`, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="74c8a-151">다음으로 빈 데이터 원본 뷰 디자인 화면을 마우스 오른쪽 단추로 클릭 한 다음 **새 명명 된 쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-151">Next, right-click the blank data source view design surface, and then select **New Named Query**.</span></span>  
  
7.  <span data-ttu-id="74c8a-152">**명명 된 쿼리 만들기** 대화 상자에서 **이름**에 `AllRegions` 를 입력 하 고 **설명**에 **모든 모델 및 지역에 대 한 매출 합계 및 평균**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-152">In the **Create Named Query** dialog box, for **Name**, type `AllRegions`, and for **Description**, type **Sum and average of sales for all models and regions**.</span></span>  
  
8.  <span data-ttu-id="74c8a-153">SQL 텍스트 창에 다음 문을 입력한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-153">In the SQL text pane, type the following statement and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. <span data-ttu-id="74c8a-154">테이블을 마우스 오른쪽 단추로 클릭 한 `AllRegions` 다음 **데이터 탐색**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-154">Right-click the `AllRegions` table, and then select **Explore Data**.</span></span>  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a><span data-ttu-id="74c8a-155">교차 예측을 위한 계열 데이터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="74c8a-155">To create the series data for cross-prediction</span></span>  
  
1.  <span data-ttu-id="74c8a-156">**솔루션 탐색기**에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-156">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="74c8a-157">데이터 원본 뷰 마법사에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-157">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="74c8a-158">**데이터 원본**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c8a-158">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="74c8a-159">**테이블 및 뷰 선택**: 어떤 테이블도 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-159">**Select Tables and Views**: Do not select any tables</span></span>  
  
     <span data-ttu-id="74c8a-160">**이름**: `T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="74c8a-160">**Name**: `T1000 Pacific Region`</span></span>  
  
3.  <span data-ttu-id="74c8a-161">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-161">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="74c8a-162">**T1000 태평양 지역**에 대 한 빈 디자인 화면을 마우스 오른쪽 단추로 클릭 한 다음 **새 명명 된 쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-162">Right-click the empty design surface for **T1000 Pacific Region.dsv**, and then select **New Named Query**.</span></span>  
  
     <span data-ttu-id="74c8a-163">**명명된 쿼리 만들기** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-163">The **Create Named Query** dialog box appears.</span></span> <span data-ttu-id="74c8a-164">이름을 다시 입력한 후 설명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-164">Retype the name, and then add the following description:</span></span>  
  
     <span data-ttu-id="74c8a-165">**이름**: `T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="74c8a-165">**Name**: `T1000 Pacific Region`</span></span>  
  
     <span data-ttu-id="74c8a-166">**설명**: \*\* `vTimeSeries` 영역 및 모델로 필터링\*\*</span><span class="sxs-lookup"><span data-stu-id="74c8a-166">**Description**: **Filter`vTimeSeries`by region and model**</span></span>  
  
5.  <span data-ttu-id="74c8a-167">텍스트 창에 다음 쿼리를 입력한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-167">In the text pane, type the following query, and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="74c8a-168">각 계열에 대한 예측을 개별적으로 생성해야 할 수 있으므로 다른 데이터 계열에 다시 사용할 수 있도록 쿼리 텍스트를 복사하고 텍스트 파일에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-168">Since you will need to create predictions for each series separately, you might want to copy the query text and save it to a text file so that you can re-use it for the other data series.</span></span>  
  
6.  <span data-ttu-id="74c8a-169">데이터 원본 뷰 디자인 화면에서 T1000 태평양를 마우스 오른쪽 단추로 클릭 한 다음 **데이터 탐색** 을 선택 하 여 데이터가 올바르게 필터링 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-169">In the Data Source View design surface, right-click T1000 Pacific, and then select **Explore Data** to verify that the data is filtered correctly.</span></span>  
  
     <span data-ttu-id="74c8a-170">교차 예측 쿼리를 생성할 때 이 데이터를 모델에 대한 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="74c8a-170">You will use this data as the input to the model when creating cross-prediction queries.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="74c8a-171">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="74c8a-171">Next Task in Lesson</span></span>  
 [<span data-ttu-id="74c8a-172">업데이트 된 데이터를 사용한 시계열 예측 &#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="74c8a-172">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="74c8a-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74c8a-173">See Also</span></span>  
 <span data-ttu-id="74c8a-174">[Microsoft 시계열 알고리즘](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="74c8a-174">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="74c8a-175">[Microsoft 시계열 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="74c8a-175">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="74c8a-176">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="74c8a-176">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
