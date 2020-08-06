---
title: '3 단원: 시계열 구조 및 모델 처리 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733368"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a><span data-ttu-id="e1eff-102">3단원: 시계열 구조 및 모델 처리</span><span class="sxs-lookup"><span data-stu-id="e1eff-102">Lesson 3: Processing the Time Series Structure and Models</span></span>
  <span data-ttu-id="e1eff-103">이 단원에서는 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) 문을 사용 하 여 만든 시계열 마이닝 구조 및 마이닝 모델을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement to process the time series mining structures and mining models that you created.</span></span>  
  
 <span data-ttu-id="e1eff-104">마이닝 구조를 처리하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 원본 데이터를 읽은 다음 마이닝 모델을 지원하는 구조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="e1eff-105">처음 마이닝 모델 및 구조를 만들면 해당 마이닝 모델 및 구조를 항상 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-105">You always have to process a mining model and structure when you first create it.</span></span> <span data-ttu-id="e1eff-106">INSERT INTO를 사용하여 마이닝 구조를 지정하는 경우 이 문은 마이닝 구조 및 연결된 모든 마이닝 모델을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-106">If you specify the mining structure when using INSERT INTO, the statement processes the mining structure and all its associated mining models.</span></span>  
  
 <span data-ttu-id="e1eff-107">이미 처리된 마이닝 구조에 마이닝 모델을 추가하는 경우에는 `INSERT INTO MINING MODEL` 문을 사용하여 기존 데이터를 기반으로 새 마이닝 모델만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-107">When you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to process just the new mining model by using the existing data.</span></span>  
  
 <span data-ttu-id="e1eff-108">마이닝 모델 처리에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;처리 요구 사항 및 고려 ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1eff-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="e1eff-109">INSERT INTO 문</span><span class="sxs-lookup"><span data-stu-id="e1eff-109">INSERT INTO Statement</span></span>  
 <span data-ttu-id="e1eff-110">시계열 마이닝 구조 및 연결 된 모든 마이닝 모델을 학습 하려면 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-110">In order to train the time series mining structure and all its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="e1eff-111">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-111">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="e1eff-112">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="e1eff-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="e1eff-113">마이닝 구조의 열 나열</span><span class="sxs-lookup"><span data-stu-id="e1eff-113">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="e1eff-114">학습 데이터 정의</span><span class="sxs-lookup"><span data-stu-id="e1eff-114">Defining the training data</span></span>  
  
 <span data-ttu-id="e1eff-115">다음은 `INSERT INTO` 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-115">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="e1eff-116">코드의 첫 번째 줄에서는 학습할 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-116">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="e1eff-117">코드의 다음 줄에서는 마이닝 구조에서 정의한 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-117">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="e1eff-118">마이닝 구조의 각 열을 나열해야 하며 각 열을 원본 쿼리 데이터 내에 포함된 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-118">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="e1eff-119">코드의 마지막 줄에서는 마이닝 구조의 학습에 사용할 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-119">The final lines of the code define the data that will be used to train the mining structure.</span></span>  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="e1eff-120">이 단원에서는 `OPENQUERY`를 사용하여 원본 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-120">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="e1eff-121">원본 데이터에 대 한 쿼리를 정의 하는 다른 방법에 대 한 자세한 내용은 [&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1eff-121">For more information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="e1eff-122">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="e1eff-122">Lesson Tasks</span></span>  
 <span data-ttu-id="e1eff-123">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-123">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="e1eff-124">Forecasting_MIXED_Structure 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="e1eff-124">Process the mining structure Forecasting_MIXED_Structure</span></span>  
  
-   <span data-ttu-id="e1eff-125">관련 마이닝 모델 Forecasting_MIXED, Forecasting_ARIMA 및 Forecasting_ARTXP 처리</span><span class="sxs-lookup"><span data-stu-id="e1eff-125">Process the related mining models Forecasting_MIXED, Forecasting_ARIMA, and Forecasting_ARTXP</span></span>  
  
## <a name="processing-the-time-series-mining-structure"></a><span data-ttu-id="e1eff-126">시계열 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="e1eff-126">Processing the Time Series Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a><span data-ttu-id="e1eff-127">INSERT INTO를 사용하여 마이닝 구조 및 관련 마이닝 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="e1eff-127">To process the mining structure and related mining models by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="e1eff-128">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-128">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="e1eff-129">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-129">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="e1eff-130">INSERT INTO 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-130">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="e1eff-131">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="e1eff-131">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="e1eff-132">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-132">with:</span></span>  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  <span data-ttu-id="e1eff-133">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="e1eff-133">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="e1eff-134">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-134">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  <span data-ttu-id="e1eff-135">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="e1eff-135">Replace the following:</span></span>  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     <span data-ttu-id="e1eff-136">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-136">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     <span data-ttu-id="e1eff-137">원본 쿼리는 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] IntermediateTutorial 샘플 프로젝트에 정의 된 데이터 원본을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-137">The source query references the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the IntermediateTutorial sample project.</span></span> <span data-ttu-id="e1eff-138">원본 쿼리는 이 데이터 원본을 사용하여 vTimeSeries 뷰에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-138">It uses this data source to access the view vTimeSeries.</span></span> <span data-ttu-id="e1eff-139">이 뷰에는 마이닝 모델의 학습에 사용할 원본 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-139">This view contains the source data that will be used to train the mining model.</span></span> <span data-ttu-id="e1eff-140">이 프로젝트 또는이 뷰에 익숙하지 않은 경우[2 단원: &#40;중급 데이터 마이닝 자습서를&#41;예측 시나리오 빌드 ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1eff-140">If you are not familiar with this project or this views, see[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="e1eff-141">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-141">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  <span data-ttu-id="e1eff-142">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-142">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="e1eff-143">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `ProcessForecastingAll.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-143">In the **Save As** dialog box, browse to the appropriate folder, and name the file `ProcessForecastingAll.dmx`.</span></span>  
  
8.  <span data-ttu-id="e1eff-144">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-144">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="e1eff-145">쿼리 실행이 끝나면 처리된 마이닝 모델을 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-145">After the query has finished running, you can create predictions by using the processed mining models.</span></span> <span data-ttu-id="e1eff-146">다음 단원에서는 만들어진 마이닝 모델을 기반으로 여러 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e1eff-146">In the next lesson, you will create several predictions based on the mining models that you created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="e1eff-147">다음 단원</span><span class="sxs-lookup"><span data-stu-id="e1eff-147">Next Lesson</span></span>  
 [<span data-ttu-id="e1eff-148">4단원: DMX를 사용하여 시계열 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="e1eff-148">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a><span data-ttu-id="e1eff-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1eff-149">See Also</span></span>  
 <span data-ttu-id="e1eff-150">[데이터 마이닝&#41;&#40;처리 요구 사항 및 고려 사항](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e1eff-150">[Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span></span>  
 <span data-ttu-id="e1eff-151">[&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query) </span><span class="sxs-lookup"><span data-stu-id="e1eff-151">[&#60;source data query&#62;](/sql/dmx/source-data-query) </span></span>  
 [<span data-ttu-id="e1eff-152">OPENQUERY &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="e1eff-152">OPENQUERY &#40;DMX&#41;</span></span>](/sql/dmx/source-data-query-openquery)  
  
  
