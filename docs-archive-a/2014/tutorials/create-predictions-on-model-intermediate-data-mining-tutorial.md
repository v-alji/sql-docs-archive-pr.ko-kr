---
title: 시퀀스 클러스터링 모델에 대 한 예측 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 2402c28a564502df9ce12c5e3f97b9d19590cfea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638477"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="4f49d-102">시퀀스 클러스터링 모델에서 예측 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="4f49d-102">Creating Predictions on a Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="4f49d-103">뷰어에서 시퀀스 클러스터링 모델을 탐색 하 여 더 잘 이해 한 후에는 데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에서 예측 쿼리 작성기를 사용 하 여 예측 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-103">After you understand the sequence clustering model better by browsing it in the viewer, you can create prediction queries by using Prediction Query Builder on the **Mining Model Prediction** tab in Data Mining Designer.</span></span> <span data-ttu-id="4f49d-104">예측을 만들려면 먼저 시퀀스 클러스터링 모델을 선택한 다음 입력 데이터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-104">To create a prediction, you first select the sequence clustering model, and then select the input data.</span></span> <span data-ttu-id="4f49d-105">입력의 경우 외부 데이터 원본을 사용하거나 단일 쿼리를 작성하고 대화 상자에 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-105">For inputs, you can use either an external data source, or you can build a singleton query and provide values in a dialog box.</span></span>  
  
 <span data-ttu-id="4f49d-106">이 단원에서는 사용자가 예측 쿼리 작성기를 사용하는 방법에 이미 익숙하고 시퀀스 클러스터링 모델과 관련된 쿼리를 작성하는 방법을 알아보려고 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-106">This lesson assumes that you are already familiar with how to use the prediction query builder and want to learn how to build queries that are specific to a sequence clustering model.</span></span> <span data-ttu-id="4f49d-107">예측 쿼리 작성기를 사용 하는 방법에 대 한 일반적인 내용은 [데이터 마이닝 쿼리 인터페이스](../../2014/analysis-services/data-mining/data-mining-query-tools.md) 또는 기본 데이터 마이닝 자습서, [예측 만들기 &#40;기본 데이터 마이닝 자습서 ](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)의 섹션을 참조 하세요&#41;.</span><span class="sxs-lookup"><span data-stu-id="4f49d-107">For general information about how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md) or the section of the Basic Data Mining tutorial, [Creating Predictions &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).</span></span>  
  
## <a name="creating-predictions-on-the-regional-model"></a><span data-ttu-id="4f49d-108">지역 모델에서 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="4f49d-108">Creating Predictions on the Regional Model</span></span>  
 <span data-ttu-id="4f49d-109">이 시나리오의 경우 지역별로 예측이 어떻게 다른지를 알아보기 위해 먼저 몇 가지 단일 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-109">For this scenario, you will first create some singleton prediction queries, to get an idea of how predictions might be different by region.</span></span>  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a><span data-ttu-id="4f49d-110">시퀀스 클러스터링 모델에서 단일 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-110">To create a singleton query on a sequence clustering model</span></span>  
  
1.  <span data-ttu-id="4f49d-111">데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-111">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="4f49d-112">**마이닝 모델** 열 메뉴에서 **단일 쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-112">In the **Mining Model** column menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="4f49d-113">**마이닝 모델** 창과 **단일 쿼리 입력** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-113">The **Mining Model** pane and **Singleton Query Input** pane appear.</span></span>  
  
3.  <span data-ttu-id="4f49d-114">**마이닝 모델** 창에서 **모델 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-114">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="4f49d-115">시퀀스 클러스터링 모드가 이미 선택되어 있는 경우 이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-115">(You can skip this step if the sequence clustering mode is already selected.)</span></span>  
  
     <span data-ttu-id="4f49d-116">**마이닝 모델 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-116">The **Select Mining Model** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="4f49d-117">영역을 사용 하 여 마이닝 구조 **시퀀스 클러스터링**을 나타내는 노드를 확장 하 고 영역을 사용 하 여 모델 **시퀀스 클러스터링**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-117">Expand the node that represents the mining structure **Sequence Clustering with Region**, and select the model **Sequence Clustering with Region**.</span></span> <span data-ttu-id="4f49d-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-118">Click **OK**.</span></span> <span data-ttu-id="4f49d-119">여기서는 입력 창을 무시하겠습니다. 예측 함수를 설정한 후 입력을 지정할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-119">For now, ignore the input pane; you will specify the inputs after you have set up the prediction functions.</span></span>  
  
5.  <span data-ttu-id="4f49d-120">표에서 **원본** 아래의 빈 셀을 클릭 하 고 **예측 함수를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="4f49d-120">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="4f49d-121">**필드**아래의 셀에서 **PredictSequence**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-121">In the cell under **Field**, select **PredictSequence**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f49d-122">**Predict** 함수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-122">You can also use the **Predict** function.</span></span> <span data-ttu-id="4f49d-123">이 경우 테이블 열을 인수로 사용 하는 **Predict** 함수 버전을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-123">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument..</span></span>  
  
6.  <span data-ttu-id="4f49d-124">**마이닝 모델** 창에서 중첩 테이블을 선택 하 `v Assoc Seq Line Items` 고 표 형태의 **PredictSequence** 함수에 대 한 **조건/인수** 상자로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-124">In the **Mining Model** pane, select the nested table `v Assoc Seq Line Items`, and drag it into the grid, to the **Criteria/Argument** box for the **PredictSequence** function.</span></span>  
  
     <span data-ttu-id="4f49d-125">테이블 및 열 이름을 끌어서 놓으면 구문 오류 없이 복잡한 문을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-125">Dragging and dropping table and column names enables you to build complex statements without syntax errors.</span></span> <span data-ttu-id="4f49d-126">그러나 **PredictSequence** 함수에 대 한 다른 선택적 인수를 포함 하는 셀의 현재 내용을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-126">However, it replaces the current contents of the cell, which include other optional arguments for the **PredictSequence** function.</span></span> <span data-ttu-id="4f49d-127">다른 인수를 보려면 참조를 위해 임시로 함수의 두 번째 인스턴스를 표에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-127">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
7.  <span data-ttu-id="4f49d-128">예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-128">Click the **Result** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="4f49d-129">예상 결과에는 머리글 **식이**포함 된 단일 열이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-129">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="4f49d-130">**식** 열에는 다음과 같은 세 개의 열이 있는 중첩 테이블이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-130">The **Expression** column contains a nested table with three columns as follows:</span></span>  
  
|<span data-ttu-id="4f49d-131">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="4f49d-131">$SEQUENCE</span></span>|<span data-ttu-id="4f49d-132">Line Number</span><span class="sxs-lookup"><span data-stu-id="4f49d-132">Line Number</span></span>|<span data-ttu-id="4f49d-133">모델</span><span class="sxs-lookup"><span data-stu-id="4f49d-133">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="4f49d-134">1</span><span class="sxs-lookup"><span data-stu-id="4f49d-134">1</span></span>||<span data-ttu-id="4f49d-135">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="4f49d-135">Mountain-200</span></span>|  
  
 <span data-ttu-id="4f49d-136">이러한 결과의 의미는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="4f49d-136">What do these results mean?</span></span> <span data-ttu-id="4f49d-137">어떤 입력도 지정하지 않았으므로</span><span class="sxs-lookup"><span data-stu-id="4f49d-137">Remember that you did not specify any inputs.</span></span> <span data-ttu-id="4f49d-138">사례의 전체 모집단에 대한 예측이 수행되고 Analysis Services에서 가능성이 가장 높은 전체 예측을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-138">Therefore, the prediction is made against the entire population of cases, and Analysis Services returns the most likely prediction overall.</span></span>  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a><span data-ttu-id="4f49d-139">단일 예측 쿼리에 입력 추가</span><span class="sxs-lookup"><span data-stu-id="4f49d-139">Adding Inputs to a Singleton Prediction Query</span></span>  
 <span data-ttu-id="4f49d-140">지금까지 어떤 입력도 지정하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-140">Until now, you have not specified any inputs.</span></span> <span data-ttu-id="4f49d-141">다음 태스크에서는 **단일 쿼리 입력** 창을 사용 하 여 쿼리에 대 한 일부 입력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-141">In the next task, you will use the **Singleton Query Input** pane to specify some inputs to the query.</span></span> <span data-ttu-id="4f49d-142">먼저 [Region]을 지역별 시퀀스 클러스터링 모델에 대한 입력으로 사용하여 예측된 시퀀스가 모든 지역에 대해 동일한지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-142">First, you will use [Region] as an input to the regional sequence clustering model, to determine whether the predicted sequences are the same for all regions.</span></span> <span data-ttu-id="4f49d-143">그리고 나서 쿼리를 수정하여 각 예측에 대한 확률을 추가하고 결과를 보다 쉽게 볼 수 있도록 평면화하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-143">You will then learn how to modify the query to add the probability for each prediction, and flatten the results to make them easier to view.</span></span>  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a><span data-ttu-id="4f49d-144">특정 고객 그룹에 대한 예측을 생성하려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-144">To generate predictions for a specific customer group</span></span>  
  
1.  <span data-ttu-id="4f49d-145">예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-145">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="4f49d-146">**단일 쿼리 입력** 대화 상자에서의 **값** 상자를 클릭 `Region` 하 고 **유럽**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-146">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **Europe**.</span></span>  
  
3.  <span data-ttu-id="4f49d-147">**결과** 단추를 클릭 하 여 유럽 고객에 대 한 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-147">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
4.  <span data-ttu-id="4f49d-148">예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-148">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
5.  <span data-ttu-id="4f49d-149">**단일 쿼리 입력** 대화 상자에서의 **값** 상자를 클릭 `Region` 하 고 **북아메리카**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-149">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **North America**.</span></span>  
  
6.  <span data-ttu-id="4f49d-150">**결과** 단추를 클릭 하 여 북아메리카 고객에 대 한 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-150">Click the **Result** button to view predictions for customers in North America.</span></span>  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a><span data-ttu-id="4f49d-151">사용자 지정 식을 사용하여 확률 추가</span><span class="sxs-lookup"><span data-stu-id="4f49d-151">Adding Probabilities by Using a Custom Expression</span></span>  
 <span data-ttu-id="4f49d-152">확률은 예측의 특성이며 중첩 테이블로 출력되기 때문에 각 예측에 대한 확률을 출력하는 작업은 다소 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-152">To output the probability for each prediction is slightly more complicated, because the probability is an attribute of the prediction and is output as a nested table.</span></span> <span data-ttu-id="4f49d-153">DMX(Data Mining Extensions)에 익숙하면 중첩 테이블에 하위 SELECT 문을 추가하도록 쿼리를 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-153">If you are familiar with Data Mining Extensions (DMX), you can easily alter the query to add a sub-select statement on the nested table.</span></span> <span data-ttu-id="4f49d-154">그러나 사용자 지정 식을 추가하여 예측 쿼리 작성기에서 하위 SELECT 문을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-154">However, you can also create a sub-select statement in the Prediction Query Builder by adding a custom expression.</span></span>  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a><span data-ttu-id="4f49d-155">사용자 지정 식을 사용하여 예측된 시퀀스에 대한 확률을 출력하려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-155">To output probabilities for a predicted sequence by using a custom expression</span></span>  
  
1.  <span data-ttu-id="4f49d-156">예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-156">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="4f49d-157">표의 **원본**에서 새 행을 클릭 하 고 **사용자 지정 식**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-157">In the grid, under **Source**, click a new row, and select **Custom Expression**.</span></span>  
  
3.  <span data-ttu-id="4f49d-158">**필드** 아래에 있는 상자를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-158">Leave the box under **Field** blank.</span></span>  
  
4.  <span data-ttu-id="4f49d-159">**별칭**에를 입력 `t` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-159">For **Alias**, type `t`.</span></span>  
  
5.  <span data-ttu-id="4f49d-160">**조건/인수** 상자에 다음 코드 샘플과 같이 전체 하위 select 문을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-160">In the **Criteria/Argument** box, type the complete sub-select statement as shown in the following code sample.</span></span> <span data-ttu-id="4f49d-161">시작 괄호와 끝 괄호를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-161">Be sure to include the starting and ending parentheses.</span></span>  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  <span data-ttu-id="4f49d-162">**결과** 단추를 클릭 하 여 유럽 고객에 대 한 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-162">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
 <span data-ttu-id="4f49d-163">이제 결과에 두 개의 중첩 테이블인 예측이 있는 테이블과 예측에 대한 확률이 있는 테이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-163">The results now contain two nested tables, one with the prediction, and one with the probability for the prediction.</span></span> <span data-ttu-id="4f49d-164">쿼리가 작동하지 않는 경우 쿼리 디자인 뷰로 전환하고 다음과 같은 전체 쿼리 문을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-164">If the query does not work, you can switch to query design view and review the complete query statement, which should be as follows:</span></span>  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a><span data-ttu-id="4f49d-165">결과 작업</span><span class="sxs-lookup"><span data-stu-id="4f49d-165">Working with Results</span></span>  
 <span data-ttu-id="4f49d-166">결과에 중첩 테이블이 많이 있는 경우 결과를 보다 쉽게 볼 수 있도록 평면화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-166">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="4f49d-167">이렇게 하려면 수동으로 쿼리를 수정하고 `FLATTENED` 키워드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-167">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="4f49d-168">예측 쿼리에서 중첩 행 집합을 평면화하려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-168">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="4f49d-169">예측 쿼리 작성기의 모서리에 있는 **쿼리** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-169">Click the **Query** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="4f49d-170">표가 열린 창으로 변경됩니다. 이 창에서는 예측 쿼리 작성기에서 만든 DMX 문을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-170">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="4f49d-171">`SELECT` 키워드 다음에 `FLATTENED`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-171">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="4f49d-172">쿼리의 전체 텍스트는 다음과 같은 형태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-172">The complete text of the query should be similar to the following:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  <span data-ttu-id="4f49d-173">예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-173">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="4f49d-174">쿼리를 수동으로 편집한 경우에는 변경 내용 손실 없이 디자인 뷰로 다시 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-174">After you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="4f49d-175">그러나 수동으로 만든 DMX 문을 텍스트 파일로 저장한 다음 디자인 뷰로 다시 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-175">You can, however, save the DMX statement that you created manually to a text file, and then change back to Design view.</span></span> <span data-ttu-id="4f49d-176">이렇게 하면 쿼리가 디자인 뷰에서 유효했던 마지막 버전으로 되돌려집니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-176">When you do so, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-predictions-on-the-related-model"></a><span data-ttu-id="4f49d-177">관련 모델에서 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="4f49d-177">Creating Predictions on the Related Model</span></span>  
 <span data-ttu-id="4f49d-178">이전 예에서는 사용자가 모델에서 지역 간의 차이점을 발견했는지 여부를 알려고 했으므로 Region이라고 하는 사례 테이블 열을 단일 예측 쿼리에 대한 입력으로 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-178">The previous examples used a case table column, Region, as the input to the singleton prediction query, because you were interested in knowing whether the model had found any differences between regions.</span></span> <span data-ttu-id="4f49d-179">그러나 모델을 탐색한 결과 차이점이 그리 크지 않아 지역별 제품 권장 사항의 사용자 지정을 정당화하기 어렵다고 판단했습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-179">However, after exploring the model, you decided that the differences are not strong enough to justify customizing product recommendations by region.</span></span> <span data-ttu-id="4f49d-180">실제로 예측하려고 하는 것은 고객이 선택하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-180">What you are really interested in predicting is the items that customers select.</span></span> <span data-ttu-id="4f49d-181">따라서 다음 쿼리에서는 Region을 포함하지 않는 시퀀스 클러스터링 모델을 사용하여 모든 고객에 대한 권장 사항을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-181">Therefore, in the queries that follow, you will use the sequence clustering model that does not include Region, to generate recommendations for all customers.</span></span>  
  
### <a name="using-nested-table-columns-as-input"></a><span data-ttu-id="4f49d-182">중첩 테이블 열을 입력으로 사용</span><span class="sxs-lookup"><span data-stu-id="4f49d-182">Using Nested Table Columns as Input</span></span>  
 <span data-ttu-id="4f49d-183">먼저 단일 항목을 입력으로 사용하고 다음으로 가능성이 가장 높은 항목을 반환하는 단일 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-183">First you will create a singleton prediction query that takes a single item as input and returns the next most likely item.</span></span> <span data-ttu-id="4f49d-184">이러한 종류의 예측을 가져오려면 중첩 테이블 열을 입력 값으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-184">To get a prediction of this kind, you have to use a nested table column as the input value.</span></span> <span data-ttu-id="4f49d-185">이는 예측하는 특성인 Model이 중첩 테이블의 일부분이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-185">This is because the attribute that you are predicting, Model, is part of a nested table.</span></span> <span data-ttu-id="4f49d-186">Analysis Services는 예측 쿼리 작성기를 사용 하 여 중첩 테이블 특성에 대 한 예측 쿼리를 쉽게 만들 수 있도록 하는 **중첩 테이블 입력** 대화 상자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-186">Analysis Services provides the **Nested Table Input** dialog box to help you easily create prediction queries on nested table attributes, by using the Prediction Query Builder.</span></span>  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a><span data-ttu-id="4f49d-187">중첩 테이블을 예측에 대한 입력으로 사용하려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-187">To use a nested table as input to a prediction</span></span>  
  
1.  <span data-ttu-id="4f49d-188">예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-188">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="4f49d-189">**단일 쿼리 입력** 대화 상자에서의 **값** 상자를 클릭 하 `Region` 고 빈 행을 선택 하 여이 필드에 대 한 입력을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-189">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select the empty row to clear the input for this field.</span></span>  
  
3.  <span data-ttu-id="4f49d-190">**단일 쿼리 입력** 대화 상자에서의 **값** 상자를 클릭 한 `vAssocSeqLineItems` 다음 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-190">In the **Singleton Query Input** dialog box, click the **Value** box for `vAssocSeqLineItems`, and then click the (...) button.</span></span>  
  
4.  <span data-ttu-id="4f49d-191">**중첩 테이블 입력** 대화 상자에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-191">In the **Nested Table Input** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="4f49d-192">새 행에서 아래의 상자를 클릭 `Model` 하 고 목록에서 여행용 타이어를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-192">In the new row, click the box under `Model`, and select Touring Tire from the list.</span></span> <span data-ttu-id="4f49d-193">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-193">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="4f49d-194">**결과** 단추를 클릭 하 여 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-194">Click the **Result** button to view the predictions.</span></span>  
  
 <span data-ttu-id="4f49d-195">모델은 Touring Tire를 첫 번째 항목으로 선택한 모든 고객에 대해 아래와 같이 다음 항목을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-195">The model recommends the following next items for all customers who choose the Touring Tire as the first item.</span></span> <span data-ttu-id="4f49d-196">모델을 탐색한 결과 고객이 Touring Tire 제품과 Touring Tire Tube 제품을 함께 구매하는 경우가 많음을 알게되었으므로 이러한 권장 사항은 적합한 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-196">You already know from exploring the model that customers frequently purchase the products Touring Tire and Touring Tire Tube together, so these recommendations look good.</span></span>  
  
|<span data-ttu-id="4f49d-197">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="4f49d-197">$SEQUENCE</span></span>|<span data-ttu-id="4f49d-198">Line Number</span><span class="sxs-lookup"><span data-stu-id="4f49d-198">Line Number</span></span>|<span data-ttu-id="4f49d-199">모델</span><span class="sxs-lookup"><span data-stu-id="4f49d-199">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="4f49d-200">1</span><span class="sxs-lookup"><span data-stu-id="4f49d-200">1</span></span>||<span data-ttu-id="4f49d-201">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="4f49d-201">Touring Tire Tube</span></span>|  
|<span data-ttu-id="4f49d-202">2</span><span class="sxs-lookup"><span data-stu-id="4f49d-202">2</span></span>||<span data-ttu-id="4f49d-203">Sport-100</span><span class="sxs-lookup"><span data-stu-id="4f49d-203">Sport-100</span></span>|  
|<span data-ttu-id="4f49d-204">3</span><span class="sxs-lookup"><span data-stu-id="4f49d-204">3</span></span>||<span data-ttu-id="4f49d-205">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="4f49d-205">Long-Sleeve Logo Jersey</span></span>|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="4f49d-206">중첩 테이블 입력을 사용하여 대량 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="4f49d-206">Creating a Bulk Prediction Query using Nested Table Inputs</span></span>  
 <span data-ttu-id="4f49d-207">이제 권장 사항을 만들 때 사용할 수 있는 예측 종류를 모델에서 만들 수 있음을 확인했으므로 외부 데이터 원본에 매핑되는 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-207">Now that you are satisfied that the model creates the kind of predictions that you can use in making recommendations, you will create a prediction query that is mapped to an external data source.</span></span> <span data-ttu-id="4f49d-208">해당 데이터 원본은 현재 제품을 나타내는 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-208">That data source will provide values representing current products.</span></span> <span data-ttu-id="4f49d-209">고객 ID 및 제품 목록을 입력으로 제공하는 예측 쿼리를 만들려고 하기 때문에 고객 테이블을 사례 테이블로 추가하고 구매 테이블은 중첩 테이블로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-209">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="4f49d-210">그리고 나서 권장 사항을 만들기 위해 이전에 한 대로 예측 함수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-210">Then you will add prediction functions as you did previously to create recommendations.</span></span>  
  
 <span data-ttu-id="4f49d-211">이는 3단원에서 시장 바구니 시나리오에 대한 예측을 만드는 데 사용하는 절차와 동일하지만 시퀀스 클러스터링 모델에서는 예측도 주문을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-211">This is the same procedure that you use to create predictions for the market basket scenario in Lesson 3; however, in a sequence clustering model predictions also need the order as input.</span></span>  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="4f49d-212">중첩 테이블 입력을 사용하여 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="4f49d-212">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="4f49d-213">**마이닝 모델** 창에서 시퀀스 클러스터링 모델을 선택 합니다 (아직 선택 하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="4f49d-213">In the **Mining Model** pane, select the Sequence Clustering model, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="4f49d-214">**입력 테이블 선택** 대화 상자에서 **사례 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-214">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="4f49d-215">**테이블 선택** 대화 상자에서 데이터 원본에 대해 Orders를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-215">In the **Select Table** dialog box, for Data Source, select Orders.</span></span> <span data-ttu-id="4f49d-216">**테이블/뷰 이름** 목록에서 vAssocSeqOrders를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-216">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="4f49d-217">**입력 테이블 선택** 대화 상자에서 **중첩 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-217">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="4f49d-218">**테이블 선택** 대화 상자에서 **데이터 원본**에 대해 Orders를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-218">In the **Select Table** dialog box, for **Data Source**, select Orders.</span></span> <span data-ttu-id="4f49d-219">**테이블/뷰 이름** 목록에서 vAssocSeqLineItems를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-219">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4f49d-220">Analysis Services에서는 데이터 형식이 일치하고 열 이름이 유사한 경우 자동으로 관계를 검색하고 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-220">Analysis Services will try to detect relationships and create them automatically if the data types match and the column names are similar.</span></span> <span data-ttu-id="4f49d-221">만든 관계가 잘못 된 경우 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **연결 수정** 을 선택 하 여 열 매핑을 편집 하거나 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 하 여 관계를 완전히 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-221">If the relationships that it creates are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span> <span data-ttu-id="4f49d-222">이 경우 테이블 원본 뷰에 테이블이 이미 조인되어 있기 때문에 이러한 관계는 자동으로 디자인 창에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-222">In this case, because the tables were already joined in the data source view, those relationships are automatically added to the design pane.</span></span>  
  
6.  <span data-ttu-id="4f49d-223">표에 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-223">Add a new row to the grid.</span></span> <span data-ttu-id="4f49d-224">**원본**에 대해 vAssocSeqOrders를 선택 하 고 **필드**에 대해 customerkey를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-224">For **Source**, select vAssocSeqOrders, and for **Field**, select CustomerKey.</span></span>  
  
7.  <span data-ttu-id="4f49d-225">표에 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-225">Add a new row to the grid.</span></span> <span data-ttu-id="4f49d-226">**원본**에 대해 **예측 함수**를 선택 하 고 **필드**에 대해 **PredictSequence**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-226">For **Source**, select **Prediction Function**, and for **Field**, select **PredictSequence**.</span></span>  
  
8.  <span data-ttu-id="4f49d-227">VAssocSeqLineItems을 **조건/인수** 상자로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-227">Drag vAssocSeqLineItems, into the **Criteria/Argument** box.</span></span> <span data-ttu-id="4f49d-228">**조건/인수** 상자의 끝을 클릭 하 고 다음 인수를 입력 `2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-228">Click at the end of the **Criteria/Argument** box and then type the following arguments: `2`.</span></span>  
  
     <span data-ttu-id="4f49d-229">**조건/인수** 상자의 전체 텍스트는 다음과 같아야 합니다.`[Sequence Clustering].[v Assoc Seq Line Items],2`</span><span class="sxs-lookup"><span data-stu-id="4f49d-229">The complete text in the **Criteria/Argument** box should be: `[Sequence Clustering].[v Assoc Seq Line Items],2`</span></span>  
  
9. <span data-ttu-id="4f49d-230">**결과** 단추를 클릭 하 여 각 고객에 대 한 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-230">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="4f49d-231">시퀀스 클러스터링 모델에 대한 자습서를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-231">You have completed the tutorial on sequence clustering models.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4f49d-232">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4f49d-232">Next Steps</span></span>  
 <span data-ttu-id="4f49d-233">중간 데이터 마이닝 자습서의 모든 섹션을 완료 하 여 [Analysis Services 데이터 마이닝&#41;&#40;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)하는 경우 다음 단계를 통해 DMX (Data 마이닝 확장) 문을 사용 하 여 모델을 작성 하 고 예측을 생성 하는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-233">If you have finished all the sections in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), the next step might be to learn to use Data Mining Extensions (DMX) statements to build models and generate predictions.</span></span> <span data-ttu-id="4f49d-234">자세한 내용은 [DMX를 사용 하 여 데이터 마이닝 모델 만들기 및 쿼리: 자습서 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f49d-234">For more information, see [Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).</span></span>  
  
 <span data-ttu-id="4f49d-235">프로그래밍 개념에 익숙한 경우 AMO(Analysis Management Objects)를 사용하여 프로그래밍 방식으로 데이터 마이닝 개체를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f49d-235">If you are familiar with programming concepts, you can also use Analysis Management Objects (AMO) to programmatically work with data mining objects.</span></span> <span data-ttu-id="4f49d-236">자세한 내용은 [AMO 데이터 마이닝 클래스](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f49d-236">For more information, see [AMO Data Mining Classes](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f49d-237">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f49d-237">See Also</span></span>  
 <span data-ttu-id="4f49d-238">[시퀀스 클러스터링 모델 쿼리 예제](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="4f49d-238">[Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="4f49d-239">시퀀스 클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="4f49d-239">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
