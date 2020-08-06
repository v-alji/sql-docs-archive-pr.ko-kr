---
title: '2 단원: 시계열 마이닝 구조에 마이닝 모델 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae0bb91fafb53c0c077a4e0d82558b550d0e6070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639186"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a><span data-ttu-id="79327-102">2단원: 시계열 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="79327-102">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>
  <span data-ttu-id="79327-103">이 단원에서는 [1 단원: 시계열 마이닝 모델 및 마이닝 구조 만들기](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)에서 방금 만든 마이닝 구조에 새 마이닝 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-103">In this lesson, you will add a new mining model to the mining structure that you just created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="79327-104">ALTER MINING STRUCTURE 문</span><span class="sxs-lookup"><span data-stu-id="79327-104">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="79327-105">기존 마이닝 구조에 새 마이닝 모델을 추가 하려면 [ALTER 마이닝 structure &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-105">In order to add a new mining model to an existing mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="79327-106">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-106">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="79327-107">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="79327-107">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="79327-108">마이닝 모델 이름 지정</span><span class="sxs-lookup"><span data-stu-id="79327-108">Naming the mining model</span></span>  
  
-   <span data-ttu-id="79327-109">키 열 정의</span><span class="sxs-lookup"><span data-stu-id="79327-109">Defining the key column</span></span>  
  
-   <span data-ttu-id="79327-110">예측 가능한 열 정의</span><span class="sxs-lookup"><span data-stu-id="79327-110">Defining the predictable columns</span></span>  
  
-   <span data-ttu-id="79327-111">알고리즘 및 매개 변수 변경 내용 지정</span><span class="sxs-lookup"><span data-stu-id="79327-111">Specifying the algorithm and any parameter changes</span></span>  
  
 <span data-ttu-id="79327-112">다음은 ALTER MINING STRUCTURE 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="79327-112">The following is a generic example of the ALTER MINING STRUCTURE statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 <span data-ttu-id="79327-113">코드의 첫 번째 줄에서는 마이닝 모델을 추가할 기존 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-113">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="79327-114">코드의 다음 줄에서는 마이닝 구조에 추가할 마이닝 모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-114">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="79327-115">DMX에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79327-115">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="79327-116">코드의 다음 줄에서는 마이닝 모델에서 사용할 마이닝 구조의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-116">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 <span data-ttu-id="79327-117">마이닝 구조에 이미 있는 열만 사용할 수 있으며 목록의 첫 번째 열은 마이닝 구조의 키 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-117">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="79327-118">코드의 다음 줄에서는 마이닝 모델을 생성하는 마이닝 알고리즘 및 이 알고리즘에 설정할 수 있는 알고리즘 매개 변수를 정의하고 마이닝 모델에서 드릴다운하여 학습 사례의 세부 데이터를 볼 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-118">The next lines of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm, and specify whether you can drill down from the mining model into view detailed data in the training cases:</span></span>  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="79327-119">조정할 수 있는 알고리즘 매개 변수에 대 한 자세한 내용은 [Microsoft 시계열 알고리즘 기술 참조](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79327-119">For more information about the algorithm parameters that you can adjust, see [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="79327-120">다음 구문을 사용하여 마이닝 모델의 열이 예측에 사용되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-120">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="79327-121">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="79327-121">Lesson Tasks</span></span>  
 <span data-ttu-id="79327-122">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-122">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="79327-123">구조에 새 시계열 마이닝 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-123">Add a new time series mining model to the structure.</span></span>  
  
-   <span data-ttu-id="79327-124">다른 분석 및 예측 방법을 사용하도록 알고리즘 매개 변수를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-124">Change the algorithm parameters to use a different method of analysis and prediction</span></span>  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a><span data-ttu-id="79327-125">구조에 ARIMA 시계열 모델 추가</span><span class="sxs-lookup"><span data-stu-id="79327-125">Adding an ARIMA Time Series Model to the Structure</span></span>  
 <span data-ttu-id="79327-126">첫 번째 단계는 기존 구조에 새 예측 마이닝 모델을 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="79327-126">The first step is to add a new forecasting mining model to the existing structure.</span></span> <span data-ttu-id="79327-127">기본적으로 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘은 ARIMA와 ARTXP라는 두 알고리즘을 사용하고 결과를 혼합하여 시계열 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79327-127">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates time series mining models by using two algorithms, ARIMA and ARTXP, and blending the results.</span></span> <span data-ttu-id="79327-128">그러나 사용할 단일 알고리즘을 지정하거나 정확한 알고리즘의 혼합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-128">However, you can specify a single algorithm to use, or you can specify the exact blend of algorithms.</span></span> <span data-ttu-id="79327-129">이 단계에서는 ARIMA 알고리즘만 사용하는 새 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-129">In this step, you will add a new model that uses only the ARIMA algorithm.</span></span> <span data-ttu-id="79327-130">이 알고리즘은 장기 예측에 대해 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-130">This algorithm is optimized for long-term prediction.</span></span>  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a><span data-ttu-id="79327-131">ARIMA 시계열 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="79327-131">To add an ARIMA time series mining model</span></span>  
  
1.  <span data-ttu-id="79327-132">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX** 를 클릭하여 쿼리 편집기와 비어 있는 새 쿼리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79327-132">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="79327-133">ALTER MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-133">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="79327-134">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="79327-134">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="79327-135">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="79327-135">with:</span></span>  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  <span data-ttu-id="79327-136">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="79327-136">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="79327-137">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="79327-137">with:</span></span>  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  <span data-ttu-id="79327-138">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="79327-138">Replace the following:</span></span>  
  
    ```  
    <key columns>,  
    ```  
  
     <span data-ttu-id="79327-139">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="79327-139">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     <span data-ttu-id="79327-140">CREATE MINING MODEL 문에 제공한 날짜 유형 또는 내용 유형 정보는 이미 마이닝 구조에 저장되어 있으므로 이러한 정보를 반복하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79327-140">Note that you do not need to repeat any of the date type or content type information that you provided in the CREATE MINING MODEL statement, because this information is already stored in the mining structure.</span></span>  
  
6.  <span data-ttu-id="79327-141">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="79327-141">Replace the following:</span></span>  
  
    ```  
    <mining model columns>  
    ```  
  
     <span data-ttu-id="79327-142">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="79327-142">with:</span></span>  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  <span data-ttu-id="79327-143">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="79327-143">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     <span data-ttu-id="79327-144">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="79327-144">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="79327-145">이제 결과 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-145">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  <span data-ttu-id="79327-146">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
9. <span data-ttu-id="79327-147">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Forecasting_ARIMA.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARIMA.dmx`.</span></span>  
  
10. <span data-ttu-id="79327-148">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-148">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a><span data-ttu-id="79327-149">구조에 ARTXP 시계열 모델 추가</span><span class="sxs-lookup"><span data-stu-id="79327-149">Adding an ARTXP Time Series Model to the Structure</span></span>  
 <span data-ttu-id="79327-150">ARTXP 알고리즘은 SQL Server 2005의 기본 시계열 알고리즘으로, 단기 예측에 대해 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-150">The ARTXP algorithm was the default time series algorithm in SQL Server 2005 and is optimized for short-term prediction.</span></span> <span data-ttu-id="79327-151">모든 세 시계열 알고리즘을 사용하여 예측을 비교하기 위해 ARTXP 알고리즘을 기반으로 하는 모델을 하나 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-151">To compare predictions by using all three time series algorithms, you will add one more model that is based on the ARTXP algorithm.</span></span>  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a><span data-ttu-id="79327-152">ARTXP 시계열 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="79327-152">To add an ARTXP time series mining model</span></span>  
  
1.  <span data-ttu-id="79327-153">다음 코드를 빈 쿼리 창에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-153">Copy the following code into a blank query window.</span></span>  
  
     <span data-ttu-id="79327-154">새 마이닝 모델의 이름과 FORECAST_METHOD 매개 변수의 값을 제외한 나머지는 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79327-154">Note that you do not need to change anything except the name of the new mining model, and the value of the FORECAST_METHOD parameter.</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  <span data-ttu-id="79327-155">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-155">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
3.  <span data-ttu-id="79327-156">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Forecasting_ARTXP.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-156">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_ARTXP.dmx`.</span></span>  
  
4.  <span data-ttu-id="79327-157">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-157">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="79327-158">다음 단원에서는 모든 모델과 마이닝 구조를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="79327-158">In the next lesson, you will process all of the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="79327-159">다음 단원</span><span class="sxs-lookup"><span data-stu-id="79327-159">Next Lesson</span></span>  
 [<span data-ttu-id="79327-160">3단원: 시계열 구조 및 모델 처리</span><span class="sxs-lookup"><span data-stu-id="79327-160">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="79327-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79327-161">See Also</span></span>  
 <span data-ttu-id="79327-162">[Microsoft 시계열 알고리즘](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="79327-162">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="79327-163">Microsoft Time Series 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="79327-163">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
