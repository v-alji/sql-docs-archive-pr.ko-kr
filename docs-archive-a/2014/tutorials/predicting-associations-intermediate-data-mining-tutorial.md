---
title: 연결 예측 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639166"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a><span data-ttu-id="5c4d8-102">연결 예측(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="5c4d8-102">Predicting Associations (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="5c4d8-103">모델이 처리되면 모델에 저장된 연결 정보를 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-103">After the models have been processed, you can use the information about associations stored in the model to create predictions.</span></span> <span data-ttu-id="5c4d8-104">이 단원의 마지막 태스크에서는 만든 연결 모델에 대해 예측 쿼리를 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-104">In the final task of this lesson, you learn how to build prediction queries against the association models that you created.</span></span> <span data-ttu-id="5c4d8-105">이 단원에서는 사용자가 예측 쿼리 작성기를 사용하는 방법에 익숙하며 연결 모델에 대해 예측 쿼리를 작성하는 방법을 알아보려 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-105">This lesson assumes that you are familiar with how to use the Prediction Query Builder and want to learn how to build prediction queries against association models.</span></span> <span data-ttu-id="5c4d8-106">예측 쿼리 작성기를 사용 하는 방법에 대 한 자세한 내용은 [데이터 마이닝 쿼리 인터페이스](../../2014/analysis-services/data-mining/data-mining-query-tools.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-106">For more information how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md).</span></span>  
  
## <a name="creating-a-singleton-prediction-query"></a><span data-ttu-id="5c4d8-107">단일 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="5c4d8-107">Creating a Singleton Prediction Query</span></span>  
 <span data-ttu-id="5c4d8-108">연결 모델에 대한 예측 쿼리는 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-108">Prediction queries on an association model can be very useful:</span></span>  
  
-   <span data-ttu-id="5c4d8-109">이전 또는 관련 구매에 따라 고객에게 항목을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-109">Recommend items to a customer, based on prior or related purchases</span></span>  
  
-   <span data-ttu-id="5c4d8-110">관련된 이벤트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-110">Find related events.</span></span>  
  
-   <span data-ttu-id="5c4d8-111">트랜잭션 집합에서 관계를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-111">Identify relationships in or across sets of transactions.</span></span>  
  
 <span data-ttu-id="5c4d8-112">예측 쿼리를 작성하려면 먼저 사용하려는 연결 모델을 선택한 다음 입력 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-112">To build a prediction query, you first select the association model you want to use, and then you specify the input data.</span></span> <span data-ttu-id="5c4d8-113">값 목록과 같은 외부 데이터 원본에서 입력 값을 가져오거나, 단일 쿼리를 작성하여 필요할 때마다 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-113">Inputs can come from an external data source, such as a list of values, or you can build a singleton query and provide values as you go.</span></span>  
  
 <span data-ttu-id="5c4d8-114">이 시나리오에서는 예측의 동작 방식을 알아보기 위해 먼저 몇 가지 단일 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-114">For this scenario, you will first create some singleton prediction queries, to get an idea of how prediction works.</span></span> <span data-ttu-id="5c4d8-115">그런 다음 고객의 현재 구매 항목을 기반으로 권장 사항을 만드는 데 사용할 수 있는 일괄 처리 예측을 위한 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-115">Then you will create a query for batch predictions that you could use for making recommendations based on a customer's current purchases.</span></span>  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a><span data-ttu-id="5c4d8-116">연결 모델에 대한 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-116">To create a prediction query on an association model</span></span>  
  
1.  <span data-ttu-id="5c4d8-117">데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-117">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="5c4d8-118">**마이닝 모델** 창에서 **모델 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-118">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="5c4d8-119">올바른 모델이 이미 선택되어 있는 경우 이 단계와 다음 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-119">(You can skip this step and the next step if the correct model is already selected.)</span></span>  
  
3.  <span data-ttu-id="5c4d8-120">**마이닝 모델 선택** 대화 상자에서 마이닝 구조 **연결**을 나타내는 노드를 확장 하 고 모델 **연결**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-120">In the **Select Mining Model** dialog box, expand the node that represents the mining structure **Association**, and select the model **Association**.</span></span> <span data-ttu-id="5c4d8-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="5c4d8-122">여기서는 입력 창을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-122">For now, you can ignore the input pane.</span></span>  
  
4.  <span data-ttu-id="5c4d8-123">표에서 **원본** 아래의 빈 셀을 클릭 하 고 **예측 함수를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5c4d8-123">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="5c4d8-124">**필드**아래의 셀에서를 선택 `PredictAssociation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-124">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
     <span data-ttu-id="5c4d8-125">또한 **predict** 함수를 사용 하 여 연결을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-125">You can also use the **Predict** function to predict associations.</span></span> <span data-ttu-id="5c4d8-126">이 경우 테이블 열을 인수로 사용 하는 **Predict** 함수 버전을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-126">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument.</span></span>  
  
5.  <span data-ttu-id="5c4d8-127">**마이닝 모델** 창에서 중첩 테이블을 선택 하 여 `vAssocSeqLineItems` 표 형태의 함수에 대 한 **조건/인수** 상자로 끌어다 놓습니다 `PredictAssociation` .</span><span class="sxs-lookup"><span data-stu-id="5c4d8-127">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span>  
  
     <span data-ttu-id="5c4d8-128">테이블 및 열 이름을 끌어다 놓으면 구문 오류 없이 복잡한 문을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-128">Dragging and dropping table and column names lets you build complex statements without syntax errors.</span></span> <span data-ttu-id="5c4d8-129">그러나이 함수는 함수에 대 한 다른 선택적 인수를 포함 하는 셀의 현재 내용을 대체 합니다 `PredictAssociation` .</span><span class="sxs-lookup"><span data-stu-id="5c4d8-129">However, it replaces the current contents of the cell, which include other optional arguments for the `PredictAssociation` function.</span></span> <span data-ttu-id="5c4d8-130">다른 인수를 보려면 참조를 위해 임시로 함수의 두 번째 인스턴스를 표에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-130">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
6.  <span data-ttu-id="5c4d8-131">**조건/인수** 상자를 클릭 하 고 테이블 이름 뒤에 다음 텍스트를 입력 합니다.`,3`</span><span class="sxs-lookup"><span data-stu-id="5c4d8-131">Click the **Criteria/Argument** box and type the following text after the table name: `,3`</span></span>  
  
     <span data-ttu-id="5c4d8-132">**조건/인수** 상자의 전체 텍스트는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-132">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  <span data-ttu-id="5c4d8-133">예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-133">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="5c4d8-134">예상 결과에는 머리글 **식이**포함 된 단일 열이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-134">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="5c4d8-135">**식** 열에는 단일 열이 있는 중첩 테이블 및 다음 세 개의 행이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-135">The **Expression** column contains a nested table with a single column and the following three rows.</span></span> <span data-ttu-id="5c4d8-136">입력 값을 지정하지 않았으므로 이러한 예측은 전체 모델에 대해 가능성이 가장 높은 제품 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-136">Because you did not specify an input value, these predictions represent the most likely product associations for the model as a whole.</span></span>  
  
|<span data-ttu-id="5c4d8-137">모델</span><span class="sxs-lookup"><span data-stu-id="5c4d8-137">Model</span></span>|  
|-----------|  
|<span data-ttu-id="5c4d8-138">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="5c4d8-138">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="5c4d8-139">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="5c4d8-139">Water Bottle</span></span>|  
|<span data-ttu-id="5c4d8-140">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="5c4d8-140">Touring-3000</span></span>|  
  
 <span data-ttu-id="5c4d8-141">다음에는 **단일 쿼리 입력** 창을 사용 하 여 제품을 쿼리에 대 한 입력으로 지정 하 고 해당 항목과 연결 될 가능성이 가장 높은 제품을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-141">Next, you will use the **Singleton Query Input** pane to specify a product as input to the query, and view the products that are most likely associated with that item.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a><span data-ttu-id="5c4d8-142">중첩 테이블 입력을 사용하여 단일 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-142">To create a singleton prediction query with nested table inputs</span></span>  
  
1.  <span data-ttu-id="5c4d8-143">예측 쿼리 작성기의 모퉁이에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-143">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="5c4d8-144">**마이닝 모델** 메뉴에서 **단일 쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-144">On the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
3.  <span data-ttu-id="5c4d8-145">**마이닝 모델** 대화 상자에서 **연결** 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-145">In the **Mining Model** dialog box, select the **Association** model.</span></span>  
  
4.  <span data-ttu-id="5c4d8-146">표에서 **원본** 아래의 빈 셀을 클릭 하 고 **예측 함수를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5c4d8-146">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="5c4d8-147">**필드**아래의 셀에서를 선택 `PredictAssociation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-147">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="5c4d8-148">**마이닝 모델** 창에서 중첩 테이블을 선택 하 여 `vAssocSeqLineItems` 표 형태의 함수에 대 한 **조건/인수** 상자로 끌어다 놓습니다 `PredictAssociation` .</span><span class="sxs-lookup"><span data-stu-id="5c4d8-148">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="5c4d8-149">`,3`이전 절차에서와 같이 중첩 테이블 이름 뒤에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-149">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="5c4d8-150">**단일 쿼리 입력** 대화 상자에서 **vassoc Seq Line Items**옆의 **값** 상자를 클릭 한 다음 **(...)** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-150">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
7.  <span data-ttu-id="5c4d8-151">**중첩 테이블 입력** 대화 상자의 `Touring Tire` **키 열** 창에서를 선택한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-151">In the **Nested Table Input** dialog box, select `Touring Tire` in the **Key column** pane, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="5c4d8-152">**결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-152">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="5c4d8-153">이제 결과에 Touring Tire와 연결될 가능성이 가장 높은 제품에 대한 예측이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-153">The results now show the predictions for products that are most likely associated with the Touring Tire.</span></span>  
  
|<span data-ttu-id="5c4d8-154">모델</span><span class="sxs-lookup"><span data-stu-id="5c4d8-154">Model</span></span>|  
|-----------|  
|<span data-ttu-id="5c4d8-155">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="5c4d8-155">Touring Tire Tube</span></span>|  
|<span data-ttu-id="5c4d8-156">Sport-100</span><span class="sxs-lookup"><span data-stu-id="5c4d8-156">Sport-100</span></span>|  
|<span data-ttu-id="5c4d8-157">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="5c4d8-157">Water Bottle</span></span>|  
  
 <span data-ttu-id="5c4d8-158">그러나 모델 탐색을 통해 Touring Tire와 함께 Touring Tire Tube가 구매되는 경우가 많음을 이미 알고 있으므로 이러한 항목을 함께 구매하는 고객에게 권장할 수 있는 제품을 확인할 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-158">However, you already know from exploring the model that the Touring Tire Tube is frequently purchased with the Touring Tire; you are more interested in knowing what products you can recommend to customers who purchase these items together.</span></span> <span data-ttu-id="5c4d8-159">이에 따라 바구니에 있는 두 항목을 기반으로 관련 제품이 예측되도록 쿼리를 변경하고</span><span class="sxs-lookup"><span data-stu-id="5c4d8-159">You will change the query so that it predicts related products based on two items in the basket.</span></span> <span data-ttu-id="5c4d8-160">예측된 각 제품에 대한 확률이 추가되도록 쿼리를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-160">You will also modify the query to add the probability for each predicted product.</span></span>  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a><span data-ttu-id="5c4d8-161">단일 예측 쿼리에 입력 및 확률을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-161">To add inputs and probabilities to the singleton prediction query</span></span>  
  
1.  <span data-ttu-id="5c4d8-162">예측 쿼리 작성기의 모퉁이에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-162">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="5c4d8-163">**단일 쿼리 입력** 대화 상자에서 **vassoc Seq Line Items**옆의 **값** 상자를 클릭 한 다음 **(...)** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-163">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
3.  <span data-ttu-id="5c4d8-164">**키 열** 창에서 `Touring Tire` 을 선택 하 고 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-164">In the **Key column** pane, select `Touring Tire`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="5c4d8-165">표에서 **원본** 아래의 빈 셀을 클릭 하 고 **예측 함수를 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5c4d8-165">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="5c4d8-166">**필드**아래의 셀에서를 선택 `PredictAssociation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-166">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="5c4d8-167">**마이닝 모델** 창에서 중첩 테이블을 선택 하 여 `vAssocSeqLineItems` 표 형태의 함수에 대 한 **조건/인수** 상자로 끌어다 놓습니다 `PredictAssociation` .</span><span class="sxs-lookup"><span data-stu-id="5c4d8-167">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="5c4d8-168">`,3`이전 절차에서와 같이 중첩 테이블 이름 뒤에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-168">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="5c4d8-169">**중첩 테이블 입력** 대화 상자의 `Touring Tire Tube` **키 열** 창에서를 선택한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-169">In the **Nested Table Input** dialog box, select `Touring Tire Tube` in the **Key column** pane, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="5c4d8-170">표의 함수 행에서 `PredictAssociation` **조건/인수** 상자를 클릭 하 고 인수를 변경 하 여 INCLUDE_STATISTICS 인수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-170">In the grid, in the row for the `PredictAssociation` function, click the **Criteria/Argument** box, and change the arguments to add the argument, INCLUDE_STATISTICS.</span></span>  
  
     <span data-ttu-id="5c4d8-171">**조건/인수** 상자의 전체 텍스트는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-171">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  <span data-ttu-id="5c4d8-172">**결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-172">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="5c4d8-173">이제 중첩 테이블의 결과가 변경되어 예측과 함께 지원 및 확률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-173">The results in the nested table now change to show the predictions, together with support and probability.</span></span> <span data-ttu-id="5c4d8-174">이러한 값을 해석 하는 방법에 대 한 자세한 내용은 [연결 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-174">For more information about how to interpret these values, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
|<span data-ttu-id="5c4d8-175">모델</span><span class="sxs-lookup"><span data-stu-id="5c4d8-175">Model</span></span>|<span data-ttu-id="5c4d8-176">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="5c4d8-176">$SUPPORT</span></span>|<span data-ttu-id="5c4d8-177">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="5c4d8-177">$PROBABILITY</span></span>|<span data-ttu-id="5c4d8-178">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="5c4d8-178">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="5c4d8-179">Sport-100</span><span class="sxs-lookup"><span data-stu-id="5c4d8-179">Sport-100</span></span>|<span data-ttu-id="5c4d8-180">4334</span><span class="sxs-lookup"><span data-stu-id="5c4d8-180">4334</span></span>|<span data-ttu-id="5c4d8-181">0.291 ...</span><span class="sxs-lookup"><span data-stu-id="5c4d8-181">0.291...</span></span>|<span data-ttu-id="5c4d8-182">0.252 ...</span><span class="sxs-lookup"><span data-stu-id="5c4d8-182">0.252...</span></span>|  
|<span data-ttu-id="5c4d8-183">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="5c4d8-183">Water Bottle</span></span>|<span data-ttu-id="5c4d8-184">2866</span><span class="sxs-lookup"><span data-stu-id="5c4d8-184">2866</span></span>|<span data-ttu-id="5c4d8-185">0.192 ...</span><span class="sxs-lookup"><span data-stu-id="5c4d8-185">0.192...</span></span>|<span data-ttu-id="5c4d8-186">0.175 ...</span><span class="sxs-lookup"><span data-stu-id="5c4d8-186">0.175...</span></span>|  
|<span data-ttu-id="5c4d8-187">Patch Kit</span><span class="sxs-lookup"><span data-stu-id="5c4d8-187">Patch Kit</span></span>|<span data-ttu-id="5c4d8-188">2113</span><span class="sxs-lookup"><span data-stu-id="5c4d8-188">2113</span></span>|<span data-ttu-id="5c4d8-189">0.142 ...</span><span class="sxs-lookup"><span data-stu-id="5c4d8-189">0.142...</span></span>|<span data-ttu-id="5c4d8-190">0.132</span><span class="sxs-lookup"><span data-stu-id="5c4d8-190">0.132</span></span>|  
  
## <a name="working-with-results"></a><span data-ttu-id="5c4d8-191">결과 작업</span><span class="sxs-lookup"><span data-stu-id="5c4d8-191">Working with Results</span></span>  
 <span data-ttu-id="5c4d8-192">결과에 중첩 테이블이 많이 있는 경우 결과를 보다 쉽게 볼 수 있도록 평면화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-192">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="5c4d8-193">이렇게 하려면 수동으로 쿼리를 수정하고 `FLATTENED` 키워드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-193">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="5c4d8-194">예측 쿼리에서 중첩 행 집합을 평면화하려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-194">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="5c4d8-195">예측 쿼리 작성기의 모서리에 있는 **SQL** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-195">Click the **SQL** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="5c4d8-196">표가 열린 창으로 변경됩니다. 이 창에서는 예측 쿼리 작성기에서 만든 DMX 문을 보고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-196">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="5c4d8-197">`SELECT` 키워드 다음에 `FLATTENED`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-197">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="5c4d8-198">쿼리의 전체 텍스트가 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-198">The complete text of the query should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  <span data-ttu-id="5c4d8-199">예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-199">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="5c4d8-200">수동으로 쿼리를 편집한 후에는 디자인 뷰로 다시 전환하면 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-200">Note that after you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="5c4d8-201">쿼리를 저장하려면 수동으로 만든 DMX 문을 텍스트 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-201">If you wish to save the query, you can copy the DMX statement that you created manually to a text file.</span></span> <span data-ttu-id="5c4d8-202">디자인 뷰로 다시 변경하면 쿼리가 디자인 뷰에서 유효했던 마지막 버전으로 되돌려집니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-202">When you change back to Design view, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-multiple-predictions"></a><span data-ttu-id="5c4d8-203">여러 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="5c4d8-203">Creating Multiple Predictions</span></span>  
 <span data-ttu-id="5c4d8-204">이전 구매 항목을 기반으로 개별 고객에 대한 최상의 예측 정보를 얻으려 한다고 가정하면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-204">Suppose you want to know the best predictions for individual customers, based on past purchases.</span></span> <span data-ttu-id="5c4d8-205">고객 ID 및 가장 최근 구매한 제품을 포함하는 테이블과 같은 외부 데이터를 예측 쿼리에 대한 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-205">You can use external data as input to the prediction query, such as tables containing the customer ID and the most recent product purchases.</span></span> <span data-ttu-id="5c4d8-206">이때 데이터 테이블은 이미 Analysis Services 데이터 원본 뷰로 정의되어 있어야 하며 입력 데이터에 모델에 사용된 것과 같은 사례 및 중첩 테이블이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-206">The requirements are that the data tables be already defined as an Analysis Services data source view; moreover, the input data must contain case and nested tables like those used in the model.</span></span> <span data-ttu-id="5c4d8-207">이름은 같을 필요가 없지만 구조는 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-207">They need not have the same names, but the structure must be similar.</span></span> <span data-ttu-id="5c4d8-208">이 자습서에서는 모델이 학습된 원래 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-208">For the purpose of this tutorial, you will use the original tables on which the model was trained.</span></span>  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a><span data-ttu-id="5c4d8-209">예측 쿼리에 대한 입력 방법을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-209">To change the input method for the prediction query</span></span>  
  
1.  <span data-ttu-id="5c4d8-210">**마이닝 모델** 메뉴에서 **단일 쿼리** 를 다시 선택 하 여 확인 표시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-210">In the **Mining Model** menu, select **Singleton Query** again, to clear the check mark.</span></span>  
  
2.  <span data-ttu-id="5c4d8-211">단일 쿼리가 손실된다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-211">An error message appears warning that your singleton query will be lost.</span></span> <span data-ttu-id="5c4d8-212">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-212">Click **Yes**.</span></span>  
  
     <span data-ttu-id="5c4d8-213">입력 대화 상자의 이름이 **입력 테이블 선택**으로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-213">The name of the input dialog box changes to **Select Input Table(s)**.</span></span>  
  
 <span data-ttu-id="5c4d8-214">고객 ID 및 제품 목록을 입력으로 제공하는 예측 쿼리를 만들려고 하기 때문에 고객 테이블을 사례 테이블로 추가하고 구매 테이블은 중첩 테이블로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-214">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="5c4d8-215">그런 다음 권장 사항을 만드는 예측 함수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-215">Then you will add prediction functions to create recommendations.</span></span>  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="5c4d8-216">중첩 테이블 입력을 사용하여 예측 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5c4d8-216">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="5c4d8-217">마이닝 모델 창에서 Association Filtered 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-217">In the Mining Model pane, select the Association Filtered model.</span></span>  
  
2.  <span data-ttu-id="5c4d8-218">**입력 테이블 선택** 대화 상자에서 **사례 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-218">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="5c4d8-219">**테이블 선택** 대화 상자에서 **데이터 원본**에 대해 AdventureWorksDW2008를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-219">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="5c4d8-220">**테이블/뷰 이름** 목록에서 vAssocSeqOrders를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-220">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5c4d8-221">창에 vAssocSeqOrders 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-221">The table vAssocSeqOrders is added to the pane.</span></span>  
  
4.  <span data-ttu-id="5c4d8-222">**입력 테이블 선택** 대화 상자에서 **중첩 테이블 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-222">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="5c4d8-223">**테이블 선택** 대화 상자에서 **데이터 원본**에 대해 AdventureWorksDW2008를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-223">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="5c4d8-224">**테이블/뷰 이름** 목록에서 vAssocSeqLineItems를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-224">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5c4d8-225">창에 vAssocSeqLineItems 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-225">The table vAssocSeqLineItems is added to the pane.</span></span>  
  
6.  <span data-ttu-id="5c4d8-226">**중첩 조인 지정** 대화 상자에서 ordernumber 필드를 사례 테이블에서 끌어 중첩 테이블의 ordernumber 필드에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-226">In the **Specify Nested Join** dialog box, drag the OrderNumber field from the case table and drop it onto the OrderNumber field in the nested table.</span></span>  
  
     <span data-ttu-id="5c4d8-227">**관계 추가** 를 클릭 하 고 목록에서 열을 선택 하 여 관계를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-227">You can also click **Add Relationship** and create the relationship by selecting columns from a list.</span></span>  
  
7.  <span data-ttu-id="5c4d8-228">**관계 지정** 대화 상자에서 ordernumber 필드가 올바르게 매핑되는지 확인 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-228">In the **Specify Relationship** dialog box, verify that the OrderNumber fields are mapped correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="5c4d8-229">**확인** 을 클릭 하 여 **중첩 조인 지정** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-229">Click **OK** to close the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="5c4d8-230">디자인 창에서 사례 및 중첩 테이블이 업데이트되어 모델의 열과 외부 데이터 열을 연결하는 조인이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-230">The case and nested tables are updated in the design pane to show the joins connecting the external data columns to the columns in the model.</span></span> <span data-ttu-id="5c4d8-231">관계가 잘못 된 경우 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **연결 수정** 을 선택 하 여 열 매핑을 편집 하거나 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 하 여 관계를 완전히 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-231">If the relationships are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span>  
  
9. <span data-ttu-id="5c4d8-232">표에 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-232">Add a new row to the grid.</span></span> <span data-ttu-id="5c4d8-233">**원본**에 대해 **vAssocSeqOrders 테이블**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-233">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="5c4d8-234">**필드**에 대해 customerkey를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-234">For **Field**, select CustomerKey.</span></span>  
  
10. <span data-ttu-id="5c4d8-235">표에 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-235">Add a new row to the grid.</span></span> <span data-ttu-id="5c4d8-236">**원본**에 대해 **vAssocSeqOrders 테이블**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-236">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="5c4d8-237">**필드**에 대해 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-237">For **Field**, select Region.</span></span>  
  
11. <span data-ttu-id="5c4d8-238">표에 새 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-238">Add a new row to the grid.</span></span> <span data-ttu-id="5c4d8-239">**원본**에 대해 **예측 함수**를 선택 하 고 **필드**에 대해를 선택 `PredictAssociation` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-239">For **Source**, select **Prediction Function**, and for **Field**, select `PredictAssociation`.</span></span>  
  
12. <span data-ttu-id="5c4d8-240">VAssocSeqLineItems을 행의 **조건/인수** 상자로 끕니다 `PredictAssociation` .</span><span class="sxs-lookup"><span data-stu-id="5c4d8-240">Drag vAssocSeqLineItems, into the **Criteria/Argument** box of the `PredictAssociation` row.</span></span> <span data-ttu-id="5c4d8-241">**조건/인수** 상자의 끝을 클릭 하 고 다음 텍스트를 입력 합니다.`INCLUDE_STATISTICS,3`</span><span class="sxs-lookup"><span data-stu-id="5c4d8-241">Click at the end of the **Criteria/Argument** box and then type the following text: `INCLUDE_STATISTICS,3`</span></span>  
  
     <span data-ttu-id="5c4d8-242">**조건/인수** 상자의 전체 텍스트는 다음과 같아야 합니다.`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span><span class="sxs-lookup"><span data-stu-id="5c4d8-242">The complete text in the **Criteria/Argument** box should be: `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span></span>  
  
13. <span data-ttu-id="5c4d8-243">**결과** 단추를 클릭 하 여 각 고객에 대 한 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-243">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="5c4d8-244">여러 모델에 대해 비슷한 예측 쿼리를 만들어 필터링으로 예측 결과가 변경되는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-244">You might try creating a similar prediction query on the multiple models, to see whether filtering changes the prediction results.</span></span> <span data-ttu-id="5c4d8-245">예측 및 다른 쿼리 유형을 만드는 방법에 대 한 자세한 내용은 [연결 모델 쿼리 예제](../../2014/analysis-services/data-mining/association-model-query-examples.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c4d8-245">For more information about creating predictions and other types of queries, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4d8-246">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c4d8-246">See Also</span></span>  
 <span data-ttu-id="5c4d8-247">[연결 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5c4d8-247">[Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="5c4d8-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span><span class="sxs-lookup"><span data-stu-id="5c4d8-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span></span>  
 [<span data-ttu-id="5c4d8-249">예측 쿼리 작성기를 사용하여 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="5c4d8-249">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
