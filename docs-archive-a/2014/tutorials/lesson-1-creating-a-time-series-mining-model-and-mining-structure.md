---
title: '1 단원: 시계열 마이닝 모델 및 마이닝 구조 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647392"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a><span data-ttu-id="c15b1-102">1단원: 시계열 마이닝 모델 및 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="c15b1-102">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>
  <span data-ttu-id="c15b1-103">이 단원에서는 기록 데이터를 기반으로 시간 경과에 따라 값을 예측할 수 있는 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-103">In this lesson, you will create a mining model that allows you to predict values over time, based on historical data.</span></span> <span data-ttu-id="c15b1-104">모델을 만들면 기본 구조가 자동으로 생성되고 추가 마이닝 모델에 대한 기초로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-104">When you create the model, the underlying structure will be generated automatically and can be used as the basis for additional mining models.</span></span>  
  
 <span data-ttu-id="c15b1-105">이 단원에서는 사용자가 예측 모델과 Microsoft Time Series 알고리즘의 요구 사항을 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-105">This lesson assumes that you are familiar with forecasting models and with the requirements of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="c15b1-106">자세한 내용은 [Microsoft Time Series 알고리즘](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c15b1-106">For more information, see [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).</span></span>  
  
## <a name="create-mining-model-statement"></a><span data-ttu-id="c15b1-107">CREATE MINING MODEL 문</span><span class="sxs-lookup"><span data-stu-id="c15b1-107">CREATE MINING MODEL Statement</span></span>  
 <span data-ttu-id="c15b1-108">마이닝 모델을 직접 만들고 기본 마이닝 구조를 자동으로 생성 하기 위해 [CREATE 마이닝 model &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-108">In order to create a mining model directly and automatically generate the underlying mining structure, you use the [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) statement.</span></span> <span data-ttu-id="c15b1-109">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="c15b1-110">모델 이름 지정</span><span class="sxs-lookup"><span data-stu-id="c15b1-110">Naming the model</span></span>  
  
-   <span data-ttu-id="c15b1-111">타임스탬프 정의</span><span class="sxs-lookup"><span data-stu-id="c15b1-111">Defining the time stamp</span></span>  
  
-   <span data-ttu-id="c15b1-112">선택적 계열 키 열 정의</span><span class="sxs-lookup"><span data-stu-id="c15b1-112">Defining the optional series key column</span></span>  
  
-   <span data-ttu-id="c15b1-113">예측 가능한 특성 정의</span><span class="sxs-lookup"><span data-stu-id="c15b1-113">Defining the predictable attribute or attributes</span></span>  
  
 <span data-ttu-id="c15b1-114">다음은 CREATE MINING MODEL 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-114">The following is a generic example of the CREATE MINING MODEL statement:</span></span>  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="c15b1-115">코드의 첫 번째 줄에서는 마이닝 모델의 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-115">The first line of the code defines the name of the mining model:</span></span>  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 <span data-ttu-id="c15b1-116">Analysis Services에서는 모델 이름에 "_structure"를 추가하여 기본 구조의 이름을 자동으로 생성하므로 구조 이름이 모델 이름과 달리 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-116">Analysis Services automatically generates a name for the underlying structure, by appending "_structure" to the model name, which ensures that the structure name is unique from the model name.</span></span> <span data-ttu-id="c15b1-117">DMX에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c15b1-117">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="c15b1-118">코드의 다음 줄에서는 시계열 모델의 경우 원본 데이터의 시간 단계를 고유하게 식별하는 마이닝 모델에 대한 키 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-118">The next line of the code defines the key column for the mining model, which in the case of a time series model uniquely identifies a time step in the source data.</span></span> <span data-ttu-id="c15b1-119">시간 단계는 열 이름과 데이터 형식 뒤에 `KEY TIME` 키워드로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-119">The time step is identified with the `KEY TIME` keywords after the column name and data types.</span></span> <span data-ttu-id="c15b1-120">시계열 모델에 별도의 계열 키가 있으면 `KEY` 키워드를 사용하여 해당 키를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-120">If the time series model has a separate series key, it is identified by using the `KEY` keyword.</span></span>  
  
```  
<key columns>  
```  
  
 <span data-ttu-id="c15b1-121">코드의 다음 줄은 예측할 모델의 열을 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-121">The next line of the code is used to define the columns in the model that will be predicted.</span></span> <span data-ttu-id="c15b1-122">단일 마이닝 모델에 예측 가능한 특성이 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-122">You can have multiple predictable attributes in a single mining model.</span></span> <span data-ttu-id="c15b1-123">예측 가능한 특성이 여러 개 있으면 Microsoft Time Series 알고리즘에서 각 계열에 대해 별도의 분석을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-123">When there are multiple predictable attributes, the Microsoft Time Series algorithm generates a separate analysis for each series:</span></span>  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="c15b1-124">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="c15b1-124">Lesson Tasks</span></span>  
 <span data-ttu-id="c15b1-125">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-125">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="c15b1-126">비어 있는 새 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="c15b1-126">Create a new blank query</span></span>  
  
-   <span data-ttu-id="c15b1-127">마이닝 모델을 만들기 위해 쿼리 변경</span><span class="sxs-lookup"><span data-stu-id="c15b1-127">Alter the query to create the mining model</span></span>  
  
-   <span data-ttu-id="c15b1-128">쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="c15b1-128">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="c15b1-129">쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="c15b1-129">Creating the Query</span></span>  
 <span data-ttu-id="c15b1-130">첫 번째 단계는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결하고 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 새 DNX 쿼리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-130">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="c15b1-131">SQL Server Management Studio에서 새 DMX 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="c15b1-131">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="c15b1-132">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-132">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c15b1-133">**서버에 연결** 대화 상자에서 **서버 유형**으로 **Analysis Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-133">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="c15b1-134">**서버 이름**,를 입력 `LocalHost` 하거나이 단원에서 연결할 인스턴스의 이름을 입력 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-134">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="c15b1-135">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-135">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c15b1-136">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-136">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="c15b1-137">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-137">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="c15b1-138">쿼리 변경</span><span class="sxs-lookup"><span data-stu-id="c15b1-138">Altering the Query</span></span>  
 <span data-ttu-id="c15b1-139">다음 단계는 예측을 위해 사용되는 마이닝 모델과 해당 기본 마이닝 구조를 함께 만들기 위해 CREATE MINING MODEL 문을 수정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-139">The next step is to modify the CREATE MINING MODEL statement to create the mining model used for forecasting, together with its underlying mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-model-statement"></a><span data-ttu-id="c15b1-140">CREATE MINING MODEL 문을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="c15b1-140">To customize the CREATE MINING MODEL statement</span></span>  
  
1.  <span data-ttu-id="c15b1-141">쿼리 편집기에서 CREATE MINING MODEL 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-141">In Query Editor, copy the generic example of the CREATE MINING MODEL statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="c15b1-142">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="c15b1-142">Replace the following:</span></span>  
  
    ```  
    [mining model name]   
    ```  
  
     <span data-ttu-id="c15b1-143">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-143">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  <span data-ttu-id="c15b1-144">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="c15b1-144">Replace the following:</span></span>  
  
    ```  
    <key columns>  
    ```  
  
     <span data-ttu-id="c15b1-145">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-145">with:</span></span>  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     <span data-ttu-id="c15b1-146">`TIME KEY` 키워드는 ReportingDate 열에 값을 정렬하는 데 사용되는 시간 단계 값이 포함되어 있는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-146">The `TIME KEY` keyword indicates that the ReportingDate column contains the time step values used to order the values.</span></span> <span data-ttu-id="c15b1-147">값이 고유하고 데이터가 정렬되어 있으면 시간 단계는 날짜 및 시간, 정수 또는 정렬된 모든 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-147">Time steps can be dates and times, integers, or any ordered data type, so long as the values are unique and the data is sorted.</span></span>  
  
     <span data-ttu-id="c15b1-148">`TEXT` 및 `KEY` 키워드는 ModelRegion 열에 추가 계열 값이 포함되어 있는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-148">The `TEXT` and `KEY` keywords indicate that the ModelRegion column contains an additional series key.</span></span> <span data-ttu-id="c15b1-149">하나의 계열 키만 포함할 수 있으며 열의 값은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-149">You can have only one series key, and the values in the column must be distinct.</span></span>  
  
4.  <span data-ttu-id="c15b1-150">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="c15b1-150">Replace the following:</span></span>  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     <span data-ttu-id="c15b1-151">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-151">with:</span></span>  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  <span data-ttu-id="c15b1-152">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="c15b1-152">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="c15b1-153">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-153">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="c15b1-154">알고리즘 매개 변수 `AUTO_DETECT_PERIODICITY` = 0.8은 사용자가 데이터의 주기를 검색하는 알고리즘을 원하는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-154">The algorithm parameter, `AUTO_DETECT_PERIODICITY` = 0.8, indicates that you want the algorithm to detect cycles in the data.</span></span> <span data-ttu-id="c15b1-155">이 값을 1에 가깝게 설정하면 많은 패턴을 검색하지만 처리 속도가 느릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-155">Setting this value closer to 1 favors the discovery of many patterns but can slow processing.</span></span>  
  
     <span data-ttu-id="c15b1-156">알고리즘 매개 변수 `FORECAST_METHOD`는 사용자가 ARTXP, ARIMA 또는 이 둘의 조합을 사용하여 분석할 데이터를 원하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-156">The algorithm parameter, `FORECAST_METHOD`, indicates whether you want the data to be analyzed using ARTXP, ARIMA, or a mixture of both.</span></span>  
  
     <span data-ttu-id="c15b1-157">`WITH DRILLTHROUGH` 키워드는 사용자가 모델이 완료된 후 원본 데이터의 자세한 통계를 볼 수 있는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-157">The keyword, `WITH DRILLTHROUGH`, specify that you want to be able to view detailed statistics in the source data after the model is complete.</span></span> <span data-ttu-id="c15b1-158">Microsoft 시계열 뷰어를 사용하여 모델을 찾아볼 경우 이 절을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-158">You must add this clause if you want to browse the model by using the Microsoft Time Series Viewer.</span></span> <span data-ttu-id="c15b1-159">예측에는 이 절이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-159">It is not required for prediction.</span></span>  
  
     <span data-ttu-id="c15b1-160">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  <span data-ttu-id="c15b1-161">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="c15b1-162">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Forecasting_MIXED.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_MIXED.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="c15b1-163">쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="c15b1-163">Executing the Query</span></span>  
 <span data-ttu-id="c15b1-164">마지막 단계는 쿼리를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-164">The final step is to execute the query.</span></span> <span data-ttu-id="c15b1-165">쿼리를 만들어 저장한 다음 서버에 마이닝 모델 및 해당 마이닝 구조를 만들려면 해당 쿼리를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-165">After a query is created and saved, it needs to be executed to create the mining model and its mining structure on the server.</span></span> <span data-ttu-id="c15b1-166">쿼리 편집기에서 쿼리를 실행 하는 방법에 대 한 자세한 내용은 [데이터베이스 엔진 쿼리 편집기 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c15b1-166">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="c15b1-167">쿼리를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="c15b1-167">To execute the query</span></span>  
  
-   <span data-ttu-id="c15b1-168">쿼리 편집기의 도구 모음에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-168">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="c15b1-169">문의 실행이 끝나면 쿼리 상태가 쿼리 편집기 아래쪽의 **메시지** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-169">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="c15b1-170">메시지는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-170">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="c15b1-171">이제 **Forecasting_MIXED_Structure** 라는 새 구조가 관련 마이닝 모델인 **Forecasting_MIXED**와 함께 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-171">A new structure named **Forecasting_MIXED_Structure** now exists on the server, together with the related mining model **Forecasting_MIXED**.</span></span>  
  
 <span data-ttu-id="c15b1-172">다음 단원에서는 방금 만든 **Forecasting_MIXED** 마이닝 구조에 마이닝 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c15b1-172">In the next lesson, you will add a mining model to the **Forecasting_MIXED** mining structure that you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c15b1-173">다음 단원</span><span class="sxs-lookup"><span data-stu-id="c15b1-173">Next Lesson</span></span>  
 [<span data-ttu-id="c15b1-174">2단원: 시계열 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="c15b1-174">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="c15b1-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c15b1-175">See Also</span></span>  
 <span data-ttu-id="c15b1-176">[시계열 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c15b1-176">[Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c15b1-177">Microsoft Time Series 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="c15b1-177">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
