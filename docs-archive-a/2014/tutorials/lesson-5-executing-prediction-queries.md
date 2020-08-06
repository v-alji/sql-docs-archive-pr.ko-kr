---
title: '5 단원: 예측 쿼리 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734692"
---
# <a name="lesson-5-executing-prediction-queries"></a><span data-ttu-id="158a3-102">5단원: 예측 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="158a3-102">Lesson 5: Executing Prediction Queries</span></span>
  <span data-ttu-id="158a3-103">이 단원에서는 SELECT 문에서 [SELECT FROM \<model> 예측 조인 (DMX)](/sql/dmx/select-from-model-cases-dmx) 형식을 사용 하 여 [2 단원: 연결 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)에서 만든 의사 결정 트리 모델을 기반으로 두 가지 유형의 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-103">In this lesson, you will use the [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement to create two different types of predictions based on the decision tree model you created in [Lesson 2: Adding Mining Models to the Association Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="158a3-104">이러한 예측 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-104">These prediction types are defined below.</span></span>  
  
 <span data-ttu-id="158a3-105">단일 쿼리</span><span class="sxs-lookup"><span data-stu-id="158a3-105">Singleton Query</span></span>  
 <span data-ttu-id="158a3-106">예측을 만들 때는 단일 쿼리를 사용하여 임시 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-106">Use a singleton query to provide ad hoc values when making predictions.</span></span> <span data-ttu-id="158a3-107">예를 들어 한 고객의 통근 거리, 지역 번호 또는 자녀 수와 같은 입력을 쿼리에 전달하여 해당 고객이 자전거를 구입할 가능성이 있는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-107">For example, you can determine whether a single customer is likely to be a bike buyer, by passing inputs to the query such as the commute distance, the area code, or the number of children of the customer.</span></span> <span data-ttu-id="158a3-108">단일 쿼리는 이러한 입력을 기준으로 해당 고객이 자전거를 구입할 가능성을 나타내는 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-108">The singleton query returns a value that indicates how likely the person is to purchase a bicycle based on those inputs.</span></span>  
  
 <span data-ttu-id="158a3-109">일괄 처리 쿼리</span><span class="sxs-lookup"><span data-stu-id="158a3-109">Batch Query</span></span>  
 <span data-ttu-id="158a3-110">일괄 처리 쿼리를 사용하여 잠재 고객 테이블에서 자전거를 구입할 가능성이 있는 고객을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-110">Use a batch query to determine who in a table of potential customers is likely to purchase a bicycle.</span></span> <span data-ttu-id="158a3-111">예를 들어 마케팅 부서에서 고객 및 고객 특성 목록을 제공한 경우 일괄 처리 예측을 사용하여 해당 테이블에서 자전거를 구입할 가능성이 있는 고객을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-111">For example, if your marketing department provides you with a list of customers and customer attributes, then you can use a batch prediction to determine who from the table is likely to purchase a bicycle.</span></span>  
  
 <span data-ttu-id="158a3-112">SELECT [FROM \<model> 예측 조인 (DMX)](/sql/dmx/select-from-model-cases-dmx) 형식의 select 문은 다음 세 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-112">The [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement contains three parts:</span></span>  
  
-   <span data-ttu-id="158a3-113">결과에 반환된 마이닝 모델 열 및 예측 함수 목록.</span><span class="sxs-lookup"><span data-stu-id="158a3-113">A list of the mining model columns and prediction functions that are returned in the results.</span></span> <span data-ttu-id="158a3-114">결과에는 원본 데이터의 입력 열도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-114">The results can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="158a3-115">예측 생성에 사용되는 데이터를 정의하는 원본 쿼리.</span><span class="sxs-lookup"><span data-stu-id="158a3-115">The source query defining the data that is being used to create a prediction.</span></span> <span data-ttu-id="158a3-116">예를 들어 일괄 처리 쿼리에서는 고객 목록이 원본 쿼리가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-116">For example, in a batch query this could be a list of customers.</span></span>  
  
-   <span data-ttu-id="158a3-117">마이닝 모델 열과 원본 데이터 간의 매핑.</span><span class="sxs-lookup"><span data-stu-id="158a3-117">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="158a3-118">이름이 일치하는 경우 NATURAL 구문을 사용할 수 있으며 열 매핑을 수행하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-118">If these names match, then you can use NATURAL syntax and leave out the column mappings.</span></span>  
  
 <span data-ttu-id="158a3-119">예측 함수를 사용하여 쿼리의 질을 보다 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-119">You can further enhance the query by using prediction functions.</span></span> <span data-ttu-id="158a3-120">예측 함수는 예측 사항의 발생 확률과 같은 추가 정보를 제공하고 학습 데이터 세트의 예측에 대한 지지도를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-120">Prediction functions provide additional information, such as the probability of a prediction occurring, and provide support for the prediction in the training dataset.</span></span> <span data-ttu-id="158a3-121">예측 함수에 대 한 자세한 내용은 [함수 &#40;DMX&#41;](/sql/dmx/functions-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="158a3-121">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="158a3-122">이 자습서의 예측은 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 예제 데이터베이스의 ProspectiveBuyer 테이블을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-122">The predictions in this tutorial are based on the ProspectiveBuyer table in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database.</span></span> <span data-ttu-id="158a3-123">ProspectiveBuyer 테이블에는 잠재 고객 및 관련 특징 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-123">The ProspectiveBuyer table contains a list of potential customers and their associated characteristics.</span></span> <span data-ttu-id="158a3-124">이 테이블의 고객은 의사 결정 트리 마이닝 모델을 만드는 데 사용된 고객과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-124">The customers in this table are independent of the customers that were used to create the decision tree mining model.</span></span>  
  
 <span data-ttu-id="158a3-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 예측 쿼리 작성기를 사용하여 예측을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-125">You can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="158a3-126">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="158a3-126">Lesson Tasks</span></span>  
 <span data-ttu-id="158a3-127">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="158a3-128">단일 쿼리를 만들어 특정 고객이 자전거를 구입할 가능성이 있는지 여부 확인</span><span class="sxs-lookup"><span data-stu-id="158a3-128">Create a singleton query to determine whether a specific customer is likely to purchase a bicycle.</span></span>  
  
-   <span data-ttu-id="158a3-129">일괄 처리 쿼리를 사용하여 고객 테이블에서 자전거를 구입할 가능성이 있는 고객 확인</span><span class="sxs-lookup"><span data-stu-id="158a3-129">Create a batch query to determine which customers, listed in a table of customers, are likely to purchase a bicycle.</span></span>  
  
## <a name="singleton-query"></a><span data-ttu-id="158a3-130">단일 쿼리</span><span class="sxs-lookup"><span data-stu-id="158a3-130">Singleton Query</span></span>  
 <span data-ttu-id="158a3-131">첫 번째 단계는 단일 예측 쿼리에서 [SELECT FROM &#60;모델&#62; 예측 조인 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) 를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-131">The first step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a singleton prediction query.</span></span> <span data-ttu-id="158a3-132">다음은 단일 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-132">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 <span data-ttu-id="158a3-133">코드의 첫 번째 줄에서는 쿼리가 반환할 마이닝 모델의 열을 정의하고 예측을 생성하는 데 사용되는 마이닝 모델을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-133">The first line of the code defines the columns from the mining model that the query should return, and specifies the mining model that is used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 <span data-ttu-id="158a3-134">코드의 다음 줄에서는 예측 생성에 사용할 고객의 특징을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-134">The next lines of the code define the characteristics of the customer that you use to create a prediction:</span></span>  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="158a3-135">NATURAL PREDICTION JOIN을 지정하는 경우 서버에서는 열 이름을 기반으로 모델의 각 열을 입력 열에 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-135">If you specify NATURAL PREDICTION JOIN, the server matches each column from the model to a column from the input, based on column names.</span></span> <span data-ttu-id="158a3-136">열 이름이 일치하지 않는 경우에는 해당 열이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-136">If column names do not match, the columns are ignored.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query"></a><span data-ttu-id="158a3-137">단일 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="158a3-137">To create a singleton prediction query</span></span>  
  
1.  <span data-ttu-id="158a3-138">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="158a3-139">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-139">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="158a3-140">단일 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-140">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="158a3-141">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="158a3-141">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="158a3-142">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-142">with:</span></span>  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     <span data-ttu-id="158a3-143">AS 문은 쿼리에서 반환한 열의 별칭을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-143">The AS statement is used to alias columns returned by the query.</span></span> <span data-ttu-id="158a3-144">[PredictHistogram](/sql/dmx/predicthistogram-dmx) 함수는 확률 및 지원을 포함 하 여 예측에 대 한 통계를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-144">The [PredictHistogram](/sql/dmx/predicthistogram-dmx) function returns statistics about the prediction, including the probability and the support.</span></span> <span data-ttu-id="158a3-145">예측 문에 사용할 수 있는 함수에 대 한 자세한 내용은 [함수 &#40;DMX&#41;](/sql/dmx/functions-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="158a3-145">For more information about the functions that can be used in a prediction statement, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
4.  <span data-ttu-id="158a3-146">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="158a3-146">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="158a3-147">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-147">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="158a3-148">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="158a3-148">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     <span data-ttu-id="158a3-149">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-149">with:</span></span>  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     <span data-ttu-id="158a3-150">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-150">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  <span data-ttu-id="158a3-151">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-151">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="158a3-152">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Singleton_Query.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-152">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_Query.dmx`.</span></span>  
  
8.  <span data-ttu-id="158a3-153">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-153">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="158a3-154">쿼리가 지정 특징을 갖는 고객이 자전거를 구입할지 여부에 대한 예측과 이 예측에 대한 통계를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-154">The query returns a prediction about whether a customer with the specified characteristics will purchase a bicycle, as well as statistics about that prediction.</span></span>  
  
## <a name="batch-query"></a><span data-ttu-id="158a3-155">일괄 처리 쿼리</span><span class="sxs-lookup"><span data-stu-id="158a3-155">Batch Query</span></span>  
 <span data-ttu-id="158a3-156">다음 단계는 일괄 처리 예측 쿼리에서 [SELECT FROM &#60;model&#62; 예측 조인 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) 를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-156">The next step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a batch prediction query.</span></span> <span data-ttu-id="158a3-157">다음은 일괄 처리 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-157">The following is a generic example of a batch statement:</span></span>  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="158a3-158">단일 쿼리의 경우와 같이 코드의 처음 두 줄에서는 예측 생성에 사용할 마이닝 모델의 이름과 쿼리가 반환하는 마이닝 모델의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-158">As in the singleton query, the first two lines of the code define the columns from mining model that the query returns, as well as the name of the mining model that is used to generate the prediction.</span></span> <span data-ttu-id="158a3-159">TOP \<number> 문은 쿼리가에 지정 된 숫자나 결과만 반환 하도록 지정 합니다 \<number> .</span><span class="sxs-lookup"><span data-stu-id="158a3-159">The TOP \<number> statement specifies that the query will only return the number or the results specified by \<number>.</span></span>  
  
 <span data-ttu-id="158a3-160">코드의 다음 줄에서는 예측의 토대가 되는 원본 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-160">The next lines of the code define the source data that the predictions are based on:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 <span data-ttu-id="158a3-161">원본 데이터를 검색하는 방법에는 여러 가지가 있지만 이 자습서에서는 OPENQUERY를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-161">You have several options for the method of retrieving the source data, but in this tutorial, you will use OPENQUERY.</span></span> <span data-ttu-id="158a3-162">사용할 수 있는 옵션에 대 한 자세한 내용은 [&#60;원본 데이터 쿼리&#62;](/sql/dmx/source-data-query)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="158a3-162">For more information about the options available, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
 <span data-ttu-id="158a3-163">다음 줄에서는 마이닝 모델의 원본 열과 원본 데이터 열 간의 매핑을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-163">The next line defines the mapping between the source columns in the mining model and the columns in the source data:</span></span>  
  
```  
ON <column mappings>  
```  
  
 <span data-ttu-id="158a3-164">WHERE 절은 예측 쿼리가 반환하는 결과를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-164">The WHERE clause filters the results returned by the prediction query:</span></span>  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 <span data-ttu-id="158a3-165">선택 사항인 코드의 마지막 줄에서는 결과를 정렬할 기준 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-165">The last and optional line of the code specifies the column that the results will be ordered by:</span></span>  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 <span data-ttu-id="158a3-166">TOP 문과 함께 ORDER BY를 사용 하 여 반환 되는 \<number> 결과를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-166">Use ORDER BY in combination with the TOP \<number> statement, to filter the results that are returned.</span></span> <span data-ttu-id="158a3-167">예를 들어 이 예측에서는 예측의 정확도 예상률을 기준으로 정렬된 상위 10명의 자전거 구매자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-167">For example, in this prediction you will return the top ten bike buyers, ordered by the probability of the prediction being correct.</span></span> <span data-ttu-id="158a3-168">[DESC|ASC] 구문을 사용하여 결과 표시 순서를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-168">You can use [DESC|ASC] syntax to control the order in which the results are displayed.</span></span>  
  
#### <a name="to-create-a-batch-prediction-query"></a><span data-ttu-id="158a3-169">일괄 처리 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="158a3-169">To create a batch prediction query</span></span>  
  
1.  <span data-ttu-id="158a3-170">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-170">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="158a3-171">비어 있는 새 쿼리가 포함된 쿼리 편집기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-171">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="158a3-172">일괄 처리 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-172">Copy the generic example of the batch statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="158a3-173">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="158a3-173">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="158a3-174">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-174">with:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     <span data-ttu-id="158a3-175">TOP 10 절은 쿼리가 상위 10개의 결과만 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-175">The TOP 10 clause specifies that only the top ten results will be returned by the query.</span></span> <span data-ttu-id="158a3-176">이 쿼리의 ORDER BY 문은 예측의 정확도 예상률을 기준으로 결과를 정렬하여 가능성이 가장 높은 상위 10개의 결과만 반환되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-176">The ORDER BY statement in this query orders the results by the probability of the prediction being correct, so only the ten most likely results will be returned.</span></span>  
  
4.  <span data-ttu-id="158a3-177">다음 자리 표시자를</span><span class="sxs-lookup"><span data-stu-id="158a3-177">Replace the following placeholder:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="158a3-178">모델의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-178">With the name of the model:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="158a3-179">다음 제네릭 OPENQUERY 문을</span><span class="sxs-lookup"><span data-stu-id="158a3-179">Replace the following generic OPENQUERY statement:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="158a3-180">다음과 같은 현재 Adventureworks 데이터 웨어하우스를 참조하는 문으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-180">With a statement that references the current Adventureworks data warehouse, such as:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  <span data-ttu-id="158a3-181">다음 일반 구문을</span><span class="sxs-lookup"><span data-stu-id="158a3-181">Replace the following generic syntax:</span></span>  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     <span data-ttu-id="158a3-182">이 모델에 필요한 열 매핑과 입력 데이터 집합으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-182">With the column mappings needed for this model and input data set:</span></span>  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     <span data-ttu-id="158a3-183">확률이 가장 높은 결과가 먼저 나열되도록 하려면 `DESC`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-183">Specify `DESC` in order to list the results with the highest probability first.</span></span>  
  
     <span data-ttu-id="158a3-184">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-184">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  <span data-ttu-id="158a3-185">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-185">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="158a3-186">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Batch_Prediction.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-186">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Batch_Prediction.dmx`.</span></span>  
  
9. <span data-ttu-id="158a3-187">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-187">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="158a3-188">쿼리에서 고객 이름, 각 고객의 자전거 구입 여부 예측 및 예측 사항의 발생 확률을 포함하는 테이블이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-188">The query returns a table containing customer names, a prediction of whether each customer will purchase a bicycle, and the probability of the prediction.</span></span>  
  
 <span data-ttu-id="158a3-189">이 단원은 Bike Buyer 자습서의 마지막 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-189">This is the last step in the Bike Buyer tutorial.</span></span> <span data-ttu-id="158a3-190">이제 생성된 마이닝 모델 집합을 사용하여 고객 간 유사성을 조사하고 잠재 고객이 자전거를 구입할 것인지 여부를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="158a3-190">You now have a set of mining models that you can use to explore similarities between you customers and predict whether potential customers will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="158a3-191">시장 바구니 시나리오에서 DMX를 사용 하는 방법을 알아보려면 [시장 바구니 DMX 자습서](../../2014/tutorials/market-basket-dmx-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="158a3-191">To learn how to use DMX in a Market Basket scenario, see [Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md).</span></span>  
  
  
