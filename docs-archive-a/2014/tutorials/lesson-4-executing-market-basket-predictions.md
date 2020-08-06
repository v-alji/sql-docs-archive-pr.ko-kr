---
title: '4 단원: 시장 바구니 예측 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649871"
---
# <a name="lesson-4-executing-market-basket-predictions"></a><span data-ttu-id="bb911-102">4단원: Market Basket 예측 실행</span><span class="sxs-lookup"><span data-stu-id="bb911-102">Lesson 4: Executing Market Basket Predictions</span></span>
  <span data-ttu-id="bb911-103">이 단원에서는 DMX 문을 사용 하 여 `SELECT` [2 단원: 시장 바구니 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)에서 만든 연결 모델을 기반으로 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-103">In this lesson, you will use the DMX `SELECT` statement to create predictions based on the association models you created in [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="bb911-104">예측 쿼리는 DMX `SELECT` 문을 사용하고 `PREDICTION JOIN` 절을 추가하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-104">A prediction query is created by using the DMX `SELECT` statement and adding a `PREDICTION JOIN` clause.</span></span> <span data-ttu-id="bb911-105">예측 조인 구문에 대 한 자세한 내용은 [SELECT FROM &#60;model&#62; 예측 조인 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb911-105">For more information about the syntax of a prediction join, see [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).</span></span>  
  
 <span data-ttu-id="bb911-106">문의 **SELECT FROM \<model> 예측 조인은** 다음 `SELECT` 세 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-106">The **SELECT FROM \<model> PREDICTION JOIN** form of the `SELECT` statement contains three parts:</span></span>  
  
-   <span data-ttu-id="bb911-107">결과 집합에 반환된 마이닝 모델 열 및 예측 함수 목록.</span><span class="sxs-lookup"><span data-stu-id="bb911-107">A list of the mining model columns and prediction functions that are returned in the result set.</span></span> <span data-ttu-id="bb911-108">이 목록에는 원본 데이터의 입력 열도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-108">This list can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="bb911-109">예측을 만드는 데 사용되는 데이터를 정의하는 원본 쿼리.</span><span class="sxs-lookup"><span data-stu-id="bb911-109">A source query that defines the data that is being used to create a prediction.</span></span> <span data-ttu-id="bb911-110">예를 들어 일괄 처리로 많은 예측을 만드는 경우 원본 쿼리가 고객 목록을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-110">For example, if you are creating many predictions in a batch, the source query could retrieve a list of customers.</span></span>  
  
-   <span data-ttu-id="bb911-111">마이닝 모델 열과 원본 데이터 간의 매핑.</span><span class="sxs-lookup"><span data-stu-id="bb911-111">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="bb911-112">열 이름이 일치하는 경우 `NATURAL PREDICTION JOIN` 구문을 사용할 수 있으며 열 매핑을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-112">If the columns names match, you can use the `NATURAL PREDICTION JOIN` syntax and omit the column mappings.</span></span>  
  
 <span data-ttu-id="bb911-113">예측 함수를 사용하여 쿼리를 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-113">You can enhance the query by using prediction functions.</span></span> <span data-ttu-id="bb911-114">예측 함수는 예측 사항의 발생 확률과 같은 추가 정보를 제공하거나 학습 데이터 세트의 예측에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-114">Prediction functions provide additional information, such as the probability of a prediction occurring, or the support for a prediction in the training dataset.</span></span> <span data-ttu-id="bb911-115">예측 함수에 대 한 자세한 내용은 [함수 &#40;DMX&#41;](/sql/dmx/functions-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb911-115">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="bb911-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 예측 쿼리 작성기를 사용하여 예측 쿼리를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-116">You can also use the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create prediction queries.</span></span>  
  
## <a name="singleton-prediction-join-statement"></a><span data-ttu-id="bb911-117">단일 PREDICTION JOIN 문</span><span class="sxs-lookup"><span data-stu-id="bb911-117">Singleton PREDICTION JOIN Statement</span></span>  
 <span data-ttu-id="bb911-118">첫 번째 단계는 **SELECT FROM \<model> 예측 조인** 구문을 사용 하 고 단일 값 집합을 입력으로 제공 하 여 단일 쿼리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-118">The first step is to create a singleton query, by using the **SELECT FROM \<model> PREDICTION JOIN** syntax and supplying a single set of values as input.</span></span> <span data-ttu-id="bb911-119">다음은 단일 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-119">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 <span data-ttu-id="bb911-120">코드의 첫 번째 줄에서는 쿼리가 반환하는 마이닝 모델의 열을 정의하고 예측을 생성하는 데 사용되는 마이닝 모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-120">The first line of the code defines the columns from the mining model that the query returns, and specifies the name of the mining model used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 <span data-ttu-id="bb911-121">코드의 다음 줄은 수행할 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-121">The next line of the code indicates the operation to perform.</span></span> <span data-ttu-id="bb911-122">각각의 열에 값을 지정하고 해당 모델과 일치하도록 정확한 열 이름을 입력할 것이기 때문에 `NATURAL PREDICTION JOIN` 구문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-122">Because you will specify values for each of the columns and type the column names exactly so as to match the model, you can use the `NATURAL PREDICTION JOIN` syntax.</span></span> <span data-ttu-id="bb911-123">그러나 열 이름이 서로 다른 경우 `ON` 절을 추가하여 모델 열과 새 데이터 열 사이의 매핑을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-123">However, if the column names were different, you would have to specify mappings between the columns in the model and the columns in the new data by adding an `ON` clause.</span></span>  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 <span data-ttu-id="bb911-124">코드의 다음 줄에서는 고객이 추가할 추가 제품 예측에 사용할 시장 바구니 제품을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-124">The next lines of the code define the products in the shopping cart that will be used to predict additional products that a customer will add:</span></span>  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="bb911-125">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="bb911-125">Lesson Tasks</span></span>  
 <span data-ttu-id="bb911-126">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-126">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="bb911-127">시장 바구니에 이미 있는 항목을 기반으로 고객이 구매할 가능성이 높은 다른 항목을 예측하는 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-127">Create a query that predicts what other items a customer will likely purchase, based on items already existing in their shopping cart.</span></span> <span data-ttu-id="bb911-128">기본 *MINIMUM_PROBABILITY*와 함께 마이닝 모델을 사용 하 여이 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-128">You will create this query by using the mining model with the default *MINIMUM_PROBABILITY*.</span></span>  
  
-   <span data-ttu-id="bb911-129">시장 바구니에 이미 있는 항목을 기반으로 고객이 구매할 가능성이 높은 다른 항목을 예측하는 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-129">Create a query that predicts what other items a customer will likely purchase based on items already existing in their shopping cart.</span></span> <span data-ttu-id="bb911-130">이 쿼리는 *MINIMUM_PROBABILITY* 0.01으로 설정 된 다른 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-130">This query is based on a different model, in which *MINIMUM_PROBABILITY* has been set to 0.01.</span></span> <span data-ttu-id="bb911-131">연결 모델에서 *MINIMUM_PROBABILITY* 의 기본값은 0.3 이므로이 모델에 대 한 쿼리는 기본 모델의 쿼리 보다 가능한 많은 항목을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-131">Because the default value for *MINIMUM_PROBABILITY* in association models is 0.3, the query on this model should return more possible items than the query on the default model.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a><span data-ttu-id="bb911-132">MINIMUM_PROBABILITY가 기본값인 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="bb911-132">Create a Prediction by Using a Model with the Default MINIMUM_PROBABILITY</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="bb911-133">연결 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bb911-133">To create an association query</span></span>  
  
1.  <span data-ttu-id="bb911-134">**개체 탐색기**에서 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **새 쿼리**를 가리킨 다음 **DMX** 를 클릭 하 여 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-134">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="bb911-135">`PREDICTION JOIN` 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-135">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="bb911-136">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-136">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="bb911-137">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-137">with:</span></span>  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     <span data-ttu-id="bb911-138">열 이름 [Products]만 포함할 수 있지만 [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) 함수를 사용 하 여 알고리즘에서 반환 되는 제품 수를 3으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-138">You could just include the column name [Products], but by using the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function, you can limit the number of products that are returned by the algorithm to three.</span></span> <span data-ttu-id="bb911-139">또한 각 제품에 대한 지원, 확률 및 조정된 확률을 반환하는 `INCLUDE_STATISTICS`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-139">You can also use `INCLUDE_STATISTICS`, which returns the support, probability, and adjusted probability for each product.</span></span> <span data-ttu-id="bb911-140">이러한 통계를 사용하면 예측 정확도의 등급을 매길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-140">These statistics help you rate the accuracy of the prediction.</span></span>  
  
4.  <span data-ttu-id="bb911-141">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="bb911-142">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-142">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="bb911-143">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-143">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="bb911-144">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-144">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="bb911-145">이 문은 `UNION` 문을 사용하여 예측된 제품과 함께 시장 바구니에 포함되어야 하는 세 가지 제품을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-145">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="bb911-146">`SELECT` 문의 Model 열은 중첩된 제품 테이블에 포함된 모델 열에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-146">The Model column in the `SELECT` statement corresponds to the model column that is contained in the nested products table.</span></span>  
  
     <span data-ttu-id="bb911-147">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-147">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="bb911-148">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-148">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="bb911-149">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Association Prediction.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-149">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="bb911-150">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-150">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="bb911-151">이 쿼리는 HL 산악용 타이어, Fender 집합-산지 및 ML 산지 타이어의 세 가지 제품을 포함 하는 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-151">The query returns a table that contains three products: HL Mountain Tire, Fender Set - Mountain, and ML Mountain Tire.</span></span> <span data-ttu-id="bb911-152">테이블에는 반환된 이러한 제품이 확률 순서대로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-152">The table lists these returned products in order of probability.</span></span> <span data-ttu-id="bb911-153">반환된 제품 중 쿼리에 지정된 세 개의 제품과 동일한 시장 바구니에 포함될 가능성이 가장 높은 제품이 테이블 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-153">The returned product that is most likely to be included in the same shopping cart as the three products specified in the query appears at the top of the table.</span></span> <span data-ttu-id="bb911-154">그 다음에 오는 두 개의 제품은 시장 바구니에 포함될 가능성이 다음으로 높은 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-154">The two products that follow are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="bb911-155">이 테이블은 예측의 정확도를 설명하는 통계도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-155">The table also contains statistics describing the accuracy of the prediction.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a><span data-ttu-id="bb911-156">MINIMUM_PROBABILITY가 0.01인 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="bb911-156">Create a Prediction by Using a Model with a MINIMUM_PROBABILITY of 0.01</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="bb911-157">연결 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bb911-157">To create an association query</span></span>  
  
1.  <span data-ttu-id="bb911-158">**개체 탐색기**에서 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **새 쿼리**를 가리킨 다음 **DMX** 를 클릭 하 여 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-158">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="bb911-159">`PREDICTION JOIN` 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-159">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="bb911-160">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-160">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="bb911-161">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-161">with:</span></span>  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  <span data-ttu-id="bb911-162">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-162">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="bb911-163">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-163">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="bb911-164">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="bb911-164">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="bb911-165">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-165">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="bb911-166">이 문은 `UNION` 문을 사용하여 예측된 제품과 함께 시장 바구니에 포함되어야 하는 세 가지 제품을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-166">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="bb911-167">`SELECT` 문의 `[Model]` 열은 중첩된 제품 테이블의 열에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-167">The `[Model]` column in the `SELECT` statement corresponds to the column in the nested products table.</span></span>  
  
     <span data-ttu-id="bb911-168">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="bb911-169">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="bb911-170">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Modified Association Prediction.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="bb911-171">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-171">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="bb911-172">이 쿼리는 HL 산 타이어, 해상 병 및 Fender 설정-산지의 세 가지 제품을 포함 하는 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-172">The query returns a table that contains three products: HL Mountain Tire, Water Bottle, and Fender Set - Mountain.</span></span> <span data-ttu-id="bb911-173">테이블에는 이러한 제품이 확률 순서대로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-173">The table lists these products in order of probability.</span></span> <span data-ttu-id="bb911-174">테이블 맨 위에 나타나는 제품은 쿼리에 지정된 세 개의 제품과 동일한 시장 바구니에 포함될 가능성이 가장 높은 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-174">The product that appears at the top of the table is the product that is most likely to be included in the same shopping cart as the three products specified in the query.</span></span> <span data-ttu-id="bb911-175">나머지 제품은 시장 바구니에 포함될 가능성이 다음으로 높은 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-175">The remaining products are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="bb911-176">이 테이블은 예측의 정확도를 설명하는 통계도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-176">The table also contains statistics that describe the accuracy of the prediction.</span></span>  
  
     <span data-ttu-id="bb911-177">이 쿼리의 결과에서 *MINIMUM_PROBABILITY* 매개 변수의 값이 쿼리에서 반환 되는 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-177">You can see from the results of this query that the value of the *MINIMUM_PROBABILITY* parameter affects the results returned by the query.</span></span>  
  
 <span data-ttu-id="bb911-178">이 단원은 Market Basket 자습서의 마지막 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-178">This is the last step in the Market Basket tutorial.</span></span> <span data-ttu-id="bb911-179">이제 고객이 동시에 구매할 수 있는 제품을 예측하는 데 사용할 수 있는 모델 집합이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb911-179">You now have a set of models that you can use to predict the products that customers might purchase at the same time.</span></span>  
  
 <span data-ttu-id="bb911-180">다른 예측 시나리오에서 DMX를 사용 하는 방법을 알아보려면 [자전거 구매자 DMX 자습서](../../2014/tutorials/bike-buyer-dmx-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb911-180">To learn how to use DMX in another predictive scenario, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb911-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb911-181">See Also</span></span>  
 <span data-ttu-id="bb911-182">[연결 모델 쿼리 예제](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="bb911-182">[Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="bb911-183">데이터 마이닝 쿼리 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bb911-183">Data Mining Query Interfaces</span></span>](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
