---
title: 콜 센터 모델에 대 한 예측 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2d402fb9f6509292442f31f85478b0612a45d56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648252"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="256ae-102">콜 센터 모델에 대한 예측 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="256ae-102">Creating Predictions for the Call Center Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="256ae-103">교대조, 전화 상담원 수, 호출 및 서비스 등급에 대한 몇 가지 사항을 배웠으므로 이제 비즈니스 분석 및 계획에 사용할 수 있는 일부 예측 쿼리를 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-103">Now that you have learned something about the interactions between shifts, the number of operators, calls, and service grade, you are ready to create some prediction queries that can be used in business analysis and planning.</span></span> <span data-ttu-id="256ae-104">먼저 탐구 모델에서 일부 예측을 만들어 몇 가지 가정을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-104">You will first create some predictions on the exploratory model to test some assumptions.</span></span> <span data-ttu-id="256ae-105">다음으로 로지스틱 회귀 모델을 사용하여 대량 예측을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-105">Next, you will create bulk predictions by using the logistic regression model.</span></span>  
  
 <span data-ttu-id="256ae-106">이 단원에서는 사용자가 예측 쿼리의 개념에 대해 이미 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-106">This lesson assumes that you are already familiar with the concept of prediction queries.</span></span>  
  
## <a name="creating-predictions-using-the-neural-network-model"></a><span data-ttu-id="256ae-107">신경망 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="256ae-107">Creating Predictions using the Neural Network Model</span></span>  
 <span data-ttu-id="256ae-108">다음 예에서는 탐색을 위해 만든 신경망 모델을 사용하여 단일 예측을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-108">The following example demonstrates how to make a singleton prediction using the neural network model that was created for exploration.</span></span> <span data-ttu-id="256ae-109">단일 예측은 모델에서 서로 다른 값을 사용하여 결과를 살펴볼 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-109">Singleton predictions are a good way to try out different values to see the effect in the model.</span></span> <span data-ttu-id="256ae-110">이 시나리오에서는 6명의 경력 전화 상담원이 근무하는 경우 요일을 지정하지 않고 자정 교대조에 대한 서비스 등급을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-110">In this scenario, you will predict the service grade for the midnight shift (no day of the week specified) if six experienced operators are on duty.</span></span>  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a><span data-ttu-id="256ae-111">신경망 모델을 사용하여 단일 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="256ae-111">To create a singleton query by using the neural network model</span></span>  
  
1.  <span data-ttu-id="256ae-112">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 사용할 모델이 들어 있는 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the model that you want to use.</span></span>  
  
2.  <span data-ttu-id="256ae-113">데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-113">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
3.  <span data-ttu-id="256ae-114">**마이닝 모델** 창에서 **모델 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-114">In the **Mining Model** pane, click **Select Model**.</span></span>  
  
4.  <span data-ttu-id="256ae-115">**마이닝 모델 선택** 대화 상자에는 마이닝 구조 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-115">The **Select Mining Model** dialog box shows a list of mining structures.</span></span> <span data-ttu-id="256ae-116">마이닝 구조를 확장하여 해당 구조와 연결된 마이닝 모델 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-116">Expand the mining structure to view a list of mining models associated with that structure.</span></span>  
  
5.  <span data-ttu-id="256ae-117">Call Center Default 마이닝 구조를 확장하고 신경망 모델 Call Center - LR을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-117">Expand the mining structure Call Center Default, and select the neural network model, Call Center - LR.</span></span>  
  
6.  <span data-ttu-id="256ae-118">**마이닝 모델** 메뉴에서 **단일 쿼리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-118">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="256ae-119">**단일 쿼리 입력** 대화 상자가 나타나고 열이 마이닝 모델의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-119">The **Singleton Query Input** dialog box appears, with columns mapped to the columns in the mining model.</span></span>  
  
7.  <span data-ttu-id="256ae-120">**단일 쿼리 입력** 대화 상자에서 Shift에 대 한 행을 클릭 한 다음 *자정*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-120">In the **Singleton Query Input** dialog box, click the row for Shift, and then select *midnight*.</span></span>  
  
8.  <span data-ttu-id="256ae-121">Lvl 2 연산자에 대 한 행을 클릭 하 고을 입력 `6` 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-121">Click the row for Lvl 2 Operators, and type `6`.</span></span>  
  
9. <span data-ttu-id="256ae-122">**마이닝 모델 예측** 탭의 아래쪽 절반에서 표의 첫 번째 행을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-122">In the bottom half of the **Mining Model Prediction** tab, click the first row in the grid.</span></span>  
  
10. <span data-ttu-id="256ae-123">**원본** 열에서 아래쪽 화살표를 클릭 하 고 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-123">In the **Source** column, click the down arrow, and select **Prediction function**.</span></span> <span data-ttu-id="256ae-124">**필드** 열에서 **PredictHistogram**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-124">In the **Field** column, select **PredictHistogram**.</span></span>  
  
     <span data-ttu-id="256ae-125">이 예측 함수와 함께 사용할 수 있는 인수 목록이 **조건/인수** 상자에 자동으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-125">A list of arguments that you can use with this prediction function automatically appears in the **Criteria/Arguments** box.</span></span>  
  
11. <span data-ttu-id="256ae-126">**마이닝 모델** 창의 열 목록에서 servicegrade 열을 **조건/인수** 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-126">Drag the ServiceGrade column from the list of columns in the **Mining Model** pane to the **Criteria/Arguments** box.</span></span>  
  
     <span data-ttu-id="256ae-127">열 이름이 자동으로 인수로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-127">The name of the column is automatically inserted as the argument.</span></span> <span data-ttu-id="256ae-128">이 입력란으로 끌어다 놓을 임의의 예측 가능한 특성 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-128">You can choose any predictable attribute column to drag into this text box.</span></span>  
  
12. <span data-ttu-id="256ae-129">예측 쿼리 작성기 위쪽 모퉁이에 있는 **쿼리 결과 뷰로 전환**단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-129">Click the button **Switch to query results view**, in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="256ae-130">예상 결과에는 각 예측에 대한 지지도 및 확률 값과 함께 이 입력에 따라 각 서비스 등급에 대해 가능한 예측 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-130">The expected results contain the possible predicted values for each service grade given these inputs, together with support and probability values for each prediction.</span></span> <span data-ttu-id="256ae-131">언제든지 디자인 뷰로 돌아가 입력을 변경하거나 더 많은 입력을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-131">You can return to design view at any time and change the inputs, or add more inputs.</span></span>  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a><span data-ttu-id="256ae-132">로지스틱 회귀 모델을 사용하여 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="256ae-132">Creating Predictions by using a Logistic Regression Model</span></span>  
 <span data-ttu-id="256ae-133">비즈니스 문제 관련 특성을 이미 알고 있는 경우 로지스틱 회귀 모델을 사용하여 일부 특성을 변경했을 때의 효과를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-133">If you already know the attributes that are relevant to the business problem, you can use a logistic regression model to predict the effect of making changes in some attributes.</span></span> <span data-ttu-id="256ae-134">로지스틱 회귀는 독립 변수의 변경 내용을 기반으로 예측을 수행 하는 데 일반적으로 사용 되는 통계 방법입니다. 예를 들어 고객 인구 통계를 기반으로 고객 행동을 예측 하기 위해 재무 점수 매기기에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-134">Logistic regression is a statistical method that is commonly used to make predictions based on changes in independent variables: for example, it is used in financial scoring, to predict customer behavior based on customer demographics.</span></span>  
  
 <span data-ttu-id="256ae-135">이 작업에서는 예측에 사용할 데이터 원본을 만든 다음 여러 가지 비즈니스 질문에 대답하는 데 유용한 예측을 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-135">In this task, you will learn how to create a data source that will be used for predictions, and then make predictions to help answer several business questions.</span></span>  
  
### <a name="generating-data-used-for-bulk-prediction"></a><span data-ttu-id="256ae-136">대량 예측에 사용할 데이터 생성</span><span class="sxs-lookup"><span data-stu-id="256ae-136">Generating Data used for Bulk Prediction</span></span>  
 <span data-ttu-id="256ae-137">입력 데이터를 제공 하는 방법에는 여러 가지가 있습니다. 예를 들어 스프레드시트에서 인력을 가져오고 모델을 통해 해당 데이터를 실행 하 여 다음 달의 서비스 품질을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-137">There are many ways to provide input data: for example, you might import staffing levels from a spreadsheet, and run that data through the model to predict service quality for the next month.</span></span>  
  
 <span data-ttu-id="256ae-138">이 단원에서는 데이터 원본 뷰 디자이너를 사용하여 명명된 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-138">In this lesson, you will use the Data Source View designer to create a named query.</span></span> <span data-ttu-id="256ae-139">이 명명된 쿼리는 직원 중 전화 상담원의 최대 수, 받은 최소 전화 수 및 발생한 평균 문제 수를 일정표의 각 교대조에 대해 계산하는 사용자 지정 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-139">This named query is a custom Transact-SQL statement that for each shift on the schedule calculates the maximum number of operators on staff, the minimum calls received, and the average number of issues that are generated.</span></span> <span data-ttu-id="256ae-140">그런 다음 해당 데이터를 마이닝 모델에 조인하여 다가올 날짜의 계열에 대한 예측을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-140">You will then join that data to a mining model to make predictions about a series of upcoming dates.</span></span>  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a><span data-ttu-id="256ae-141">대량 예측 쿼리에 대한 입력 데이터를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="256ae-141">To generate input data for a bulk prediction query</span></span>  
  
1.  <span data-ttu-id="256ae-142">솔루션 탐색기에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-142">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="256ae-143">데이터 원본 뷰 마법사에서를 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 데이터 원본으로 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-143">In the Data Source View wizard, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] as the data source, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="256ae-144">**테이블 및 뷰 선택** 페이지에서 테이블을 선택 하지 않고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-144">On the **Select Tables and Views** page, click **Next** without selecting any tables.</span></span>  
  
4.  <span data-ttu-id="256ae-145">**마법사 완료** 페이지에서 이름을 입력 `Shifts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-145">On the **Completing the Wizard** page, type the name, `Shifts`.</span></span>  
  
     <span data-ttu-id="256ae-146">이 이름은 솔루션 탐색기에서 데이터 원본 뷰의 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-146">This name will appear in Solution Explorer as the name of the data source view.</span></span>  
  
5.  <span data-ttu-id="256ae-147">빈 디자인 창을 마우스 오른쪽 단추로 클릭 한 다음 **새 명명 된 쿼리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-147">Right-click the empty design pane, then select **New Named Query**.</span></span>  
  
6.  <span data-ttu-id="256ae-148">**명명 된 쿼리 만들기** 대화 상자에서 **이름**에을 입력 `Shifts for Call Center` 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-148">In the **Create Named Query** dialog box, for **Name**, type `Shifts for Call Center`.</span></span>  
  
     <span data-ttu-id="256ae-149">이 이름은 데이터 원본 뷰 디자이너에 명명된 쿼리의 이름으로만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-149">This name will appear in Data Source View designer only as the name of the named query.</span></span>  
  
7.  <span data-ttu-id="256ae-150">다음 쿼리 문을 대화 상자의 아래쪽 중간에 있는 SQL 텍스트 창에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-150">Paste the following query statement into the SQL text pane in the lower half of the dialog box.</span></span>  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  <span data-ttu-id="256ae-151">디자인 창에서 표를 마우스 오른쪽 단추로 클릭 하 고, Call Center로 이동 하 고, **데이터 탐색** 을 선택 하 여 t-sql 쿼리에서 반환 된 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-151">In the design pane, right-click the table, Shifts for Call Center, and select **Explore Data** to preview the data as returned by the T-SQL query.</span></span>  
  
9. <span data-ttu-id="256ae-152">**Dsv (디자인)** 를 마우스 오른쪽 단추로 클릭 하 고 **저장** 을 클릭 하 여 새 데이터 원본 뷰 정의를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-152">Right-click the tab, **Shifts.dsv (Design),** and then click **Save** to save the new data source view definition.</span></span>  
  
### <a name="predicting-service-metrics-for-each-shift"></a><span data-ttu-id="256ae-153">각 교대조에 대한 서비스 메트릭 예측</span><span class="sxs-lookup"><span data-stu-id="256ae-153">Predicting Service Metrics for Each Shift</span></span>  
 <span data-ttu-id="256ae-154">지금까지 각 교대조에 대한 일부 값을 생성했으므로 이제는 이러한 값을 작성한 로지스틱 회귀 모델의 입력으로 사용하여 비즈니스 계획에 사용할 수 있는 일부 예측을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-154">Now that you have generated some values for each shift, you will use those values as input to the logistic regression model that you built, to generate some predictions that can be used in business planning.</span></span>  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a><span data-ttu-id="256ae-155">새 DSV를 예측 쿼리에 대한 입력으로 사용하려면</span><span class="sxs-lookup"><span data-stu-id="256ae-155">To use the new DSV as input to a prediction query</span></span>  
  
1.  <span data-ttu-id="256ae-156">데이터 마이닝 디자이너에서 **마이닝 모델 예측** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-156">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="256ae-157">**마이닝 모델** 창에서 **모델 선택**을 클릭 하 고 사용 가능한 모델 목록에서 Call Center-LR을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-157">In the **Mining Model** pane, click **Select Model**, and choose Call Center - LR from the list of available models.</span></span>  
  
3.  <span data-ttu-id="256ae-158">**마이닝 모델** 메뉴에서 **단일 쿼리**옵션의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-158">From the **Mining Model** menu, clear the option, **Singleton Query**.</span></span> <span data-ttu-id="256ae-159">단일 쿼리 입력이 손실된다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-159">A warning tells you that the singleton query inputs will be lost.</span></span> <span data-ttu-id="256ae-160">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-160">Click **OK**.</span></span>  
  
     <span data-ttu-id="256ae-161">**단일 쿼리 입력** 대화 상자는 **입력 테이블 선택** 대화 상자로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-161">The **Singleton Query Input** dialog box is replaced with the **Select Input Table(s)** dialog box.</span></span>  
  
4.  <span data-ttu-id="256ae-162">**사례 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-162">Click **Select Case Table**.</span></span>  
  
5.  <span data-ttu-id="256ae-163">**테이블 선택** 대화 상자에서 데이터 원본 목록에서 이동을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-163">In the **Select Table** dialog box, selectShifts from the list of data sources.</span></span> <span data-ttu-id="256ae-164">**테이블/뷰 이름** 목록에서 호출 센터 (자동으로 선택 될 수 있음)에 대해 이동을 선택 하 고 확인을 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="256ae-164">In the **Table/View name** list, select Shifts for Call Center (it might be automatically selected), and then click **OK.**</span></span>  
  
     <span data-ttu-id="256ae-165">**마이닝 모델 예측** 디자인 화면이 입력 데이터 및 모델의 열 이름 및 데이터 형식을 기반으로 생성 된 매핑을 표시 하도록 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-165">The **Mining Model Prediction** design surface is updated to show mappings that are created based on the names and data types of columns in the input data and in the model.</span></span>  
  
6.  <span data-ttu-id="256ae-166">조인 선 중 하나를 마우스 오른쪽 단추로 클릭 하 고 **연결 수정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-166">Right-click one of the join lines, and then select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="256ae-167">이 대화 상자에서는 매핑된 열과 매핑되지 않은 열을 정확하게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-167">In this dialog box, you can see exactly which columns are mapped and which are not.</span></span> <span data-ttu-id="256ae-168">마이닝 모델에는 Calls, Orders, IssuesRaised 및 LvlTwoOperators 열이 포함되어 있으므로 사용자가 원본 데이터의 이 열을 기반으로 만든 집계로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-168">The mining model contains columns for Calls, Orders, IssuesRaised, and LvlTwoOperators, which you can map to any of the aggregates that you created based on these columns in the source data.</span></span> <span data-ttu-id="256ae-169">이 시나리오에서는 평균으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-169">In this scenario, you will map to the averages.</span></span>  
  
7.  <span data-ttu-id="256ae-170">LevelTwoOperators 옆에 있는 빈 셀을 클릭 하 고 **Call Center. AvgOperators에 대해 이동**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-170">Click the empty cell next to LevelTwoOperators, and select **Shifts for Call Center.AvgOperators**.</span></span>  
  
8.  <span data-ttu-id="256ae-171">호출 옆에 있는 빈 셀을 클릭 하 고 **Call Center. AvgCalls에 대해 이동**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-171">Click the empty cell next to Calls, select **Shifts for Call Center.AvgCalls**.</span></span> <span data-ttu-id="256ae-172">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-172">and then click **OK**.</span></span>  
  
##### <a name="to-create-the-predictions-for-each-shift"></a><span data-ttu-id="256ae-173">각 교대조에 대한 예측을 만들려면</span><span class="sxs-lookup"><span data-stu-id="256ae-173">To create the predictions for each shift</span></span>  
  
1.  <span data-ttu-id="256ae-174">**예측 쿼리 작성기**의 아래쪽 절반에 있는 표에서 **원본** 아래의 빈 셀을 클릭 한 다음 Call Center에 대해 이동을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-174">In the grid at the bottom half of the **Prediction Query Builder**, click the empty cell under **Source,** and then select Shifts for Call Center.</span></span>  
  
2.  <span data-ttu-id="256ae-175">**필드**아래의 빈 셀에서 Shift를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-175">In the empty cell under **Field**, select Shift.</span></span>  
  
3.  <span data-ttu-id="256ae-176">표의 다음 빈 줄을 클릭하고 위에 설명한 절차를 반복하여 WageType에 대한 다른 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-176">Click the next empty line in the grid and repeat the procedure described above to add another row for WageType.</span></span>  
  
4.  <span data-ttu-id="256ae-177">표에서 다음 빈 줄을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-177">Click the next empty line in the grid.</span></span> <span data-ttu-id="256ae-178">**원본** 열에서 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-178">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="256ae-179">**필드** 열에서 **Predict**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-179">In the **Field** column, select **Predict**.</span></span>  
  
5.  <span data-ttu-id="256ae-180">**마이닝 모델** 창에서 표 아래로 servicegrade 열을 끌고 **조건/인수** 셀에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-180">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="256ae-181">**별칭** 필드에 **예측 된 서비스 등급**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-181">In the **Alias** field, type **Predicted Service Grade**.</span></span>  
  
6.  <span data-ttu-id="256ae-182">표에서 다음 빈 줄을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-182">Click the next empty line in the grid.</span></span> <span data-ttu-id="256ae-183">**원본** 열에서 **예측 함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-183">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="256ae-184">**필드** 열에서 **predictprobability**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-184">In the **Field** column, select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="256ae-185">**마이닝 모델** 창에서 표 아래로 servicegrade 열을 끌고 **조건/인수** 셀에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-185">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="256ae-186">**별칭** 필드에 **Probability**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-186">In the **Alias** field, type **Probability**.</span></span>  
  
8.  <span data-ttu-id="256ae-187">**쿼리 결과 뷰로 전환** 을 클릭 하 여 예측을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-187">Click **Switch to query result view** to view the predictions.</span></span>  
  
 <span data-ttu-id="256ae-188">다음 표에서는 각 교대조에 대한 결과 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-188">The following table shows sample results for each shift.</span></span>  
  
|<span data-ttu-id="256ae-189">Shift</span><span class="sxs-lookup"><span data-stu-id="256ae-189">Shift</span></span>|<span data-ttu-id="256ae-190">WageType</span><span class="sxs-lookup"><span data-stu-id="256ae-190">WageType</span></span>|<span data-ttu-id="256ae-191">Predicted Service Grade</span><span class="sxs-lookup"><span data-stu-id="256ae-191">Predicted Service Grade</span></span>|<span data-ttu-id="256ae-192">Probability</span><span class="sxs-lookup"><span data-stu-id="256ae-192">Probability</span></span>|  
|-----------|--------------|-----------------------------|-----------------|  
|<span data-ttu-id="256ae-193">AM</span><span class="sxs-lookup"><span data-stu-id="256ae-193">AM</span></span>|<span data-ttu-id="256ae-194">holiday</span><span class="sxs-lookup"><span data-stu-id="256ae-194">holiday</span></span>|<span data-ttu-id="256ae-195">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-195">0.165</span></span>|<span data-ttu-id="256ae-196">0.377520666</span><span class="sxs-lookup"><span data-stu-id="256ae-196">0.377520666</span></span>|  
|<span data-ttu-id="256ae-197">midnight</span><span class="sxs-lookup"><span data-stu-id="256ae-197">midnight</span></span>|<span data-ttu-id="256ae-198">holiday</span><span class="sxs-lookup"><span data-stu-id="256ae-198">holiday</span></span>|<span data-ttu-id="256ae-199">0.105</span><span class="sxs-lookup"><span data-stu-id="256ae-199">0.105</span></span>|<span data-ttu-id="256ae-200">0.364105573</span><span class="sxs-lookup"><span data-stu-id="256ae-200">0.364105573</span></span>|  
|<span data-ttu-id="256ae-201">PM1</span><span class="sxs-lookup"><span data-stu-id="256ae-201">PM1</span></span>|<span data-ttu-id="256ae-202">holiday</span><span class="sxs-lookup"><span data-stu-id="256ae-202">holiday</span></span>|<span data-ttu-id="256ae-203">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-203">0.165</span></span>|<span data-ttu-id="256ae-204">0.40056055</span><span class="sxs-lookup"><span data-stu-id="256ae-204">0.40056055</span></span>|  
|<span data-ttu-id="256ae-205">PM2</span><span class="sxs-lookup"><span data-stu-id="256ae-205">PM2</span></span>|<span data-ttu-id="256ae-206">holiday</span><span class="sxs-lookup"><span data-stu-id="256ae-206">holiday</span></span>|<span data-ttu-id="256ae-207">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-207">0.165</span></span>|<span data-ttu-id="256ae-208">0.338532973</span><span class="sxs-lookup"><span data-stu-id="256ae-208">0.338532973</span></span>|  
|<span data-ttu-id="256ae-209">AM</span><span class="sxs-lookup"><span data-stu-id="256ae-209">AM</span></span>|<span data-ttu-id="256ae-210">weekday</span><span class="sxs-lookup"><span data-stu-id="256ae-210">weekday</span></span>|<span data-ttu-id="256ae-211">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-211">0.165</span></span>|<span data-ttu-id="256ae-212">0.370847617</span><span class="sxs-lookup"><span data-stu-id="256ae-212">0.370847617</span></span>|  
|<span data-ttu-id="256ae-213">midnight</span><span class="sxs-lookup"><span data-stu-id="256ae-213">midnight</span></span>|<span data-ttu-id="256ae-214">weekday</span><span class="sxs-lookup"><span data-stu-id="256ae-214">weekday</span></span>|<span data-ttu-id="256ae-215">0.08</span><span class="sxs-lookup"><span data-stu-id="256ae-215">0.08</span></span>|<span data-ttu-id="256ae-216">0.352999173</span><span class="sxs-lookup"><span data-stu-id="256ae-216">0.352999173</span></span>|  
|<span data-ttu-id="256ae-217">PM1</span><span class="sxs-lookup"><span data-stu-id="256ae-217">PM1</span></span>|<span data-ttu-id="256ae-218">weekday</span><span class="sxs-lookup"><span data-stu-id="256ae-218">weekday</span></span>|<span data-ttu-id="256ae-219">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-219">0.165</span></span>|<span data-ttu-id="256ae-220">0.317419177</span><span class="sxs-lookup"><span data-stu-id="256ae-220">0.317419177</span></span>|  
|<span data-ttu-id="256ae-221">PM2</span><span class="sxs-lookup"><span data-stu-id="256ae-221">PM2</span></span>|<span data-ttu-id="256ae-222">weekday</span><span class="sxs-lookup"><span data-stu-id="256ae-222">weekday</span></span>|<span data-ttu-id="256ae-223">0.105</span><span class="sxs-lookup"><span data-stu-id="256ae-223">0.105</span></span>|<span data-ttu-id="256ae-224">0.311672027</span><span class="sxs-lookup"><span data-stu-id="256ae-224">0.311672027</span></span>|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a><span data-ttu-id="256ae-225">응답 시간 단축이 서비스 등급에 미치는 영향 예측</span><span class="sxs-lookup"><span data-stu-id="256ae-225">Predicting the Effect of Reduced Response Time on Service Grade</span></span>  
 <span data-ttu-id="256ae-226">지금까지 각 교대조에 대한 일부 평균 값을 생성하고 이러한 값을 로지스틱 회귀 모델의 입력으로 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-226">You generated some average values for each shift, and used those values as input to the logistic regression model.</span></span> <span data-ttu-id="256ae-227">그러나 중단율을 0.00-0.05 범위 내로 유지하려는 비즈니스 목표에는 이 결과가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-227">However, given that the business objective is to keep abandon rate within the range 0.00-0.05, the results are not encouraging.</span></span>  
  
 <span data-ttu-id="256ae-228">따라서 서비스 등급에 대한 응답 시간의 큰 영향력을 보여 준 원래 모델을 기반으로 하여 운영 팀에서는 호출에 응답하는 평균 시간을 줄이면 서비스 품질을 향상시킬 수 있는지를 평가하는 일부 예측을 실행하기로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-228">Therefore, based on the original model, which showed a strong influence of response time on service grade, the Operations team decides to run some predictions to assess whether reducing the average time for responding to calls might improve service quality.</span></span> <span data-ttu-id="256ae-229">예를 들어 현재 통화 응답 시간을 90% 또는 80%까지 줄이면 서비스 등급 값이 어떻게 될지 살펴 봅니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-229">For example, if you cut the call response time to 90 percent or even to 80 percent of the current call response time, what would happen to service grade values?</span></span>  
  
 <span data-ttu-id="256ae-230">각 교대조의 평균 응답 시간을 계산하는 DSV(데이터 원본 뷰)를 만드는 것은 간단합니다. 그런 다음에는 해당 평균 응답 시간의 80% 또는 90%를 계산하는 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-230">It is easy to create a data source view (DSV) that calculates the average response times for each shift, and then add columns that calculate 80% or 90% of the average response time.</span></span> <span data-ttu-id="256ae-231">그런 다음 DSV를 모델에 대한 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-231">You can then use the DSV as input to the model.</span></span>  
  
 <span data-ttu-id="256ae-232">정확한 단계를 여기에서 보여 주지는 않지만 다음 표에서 응답 시간을 현재 응답 시간의 80% 또는 90%까지 줄일 경우 서비스 등급에 대한 영향을 비교해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-232">Although the exact steps are not shown here, the following table compares the effects on service grade when you reduce response times to 80% or to 90% of current response times.</span></span>  
  
 <span data-ttu-id="256ae-233">이러한 결과를 통해 서비스 품질의 향상을 위해서는 대상 교대조에서 응답 시간을 현재 수준의 90%로 줄여야 한다는 결론을 내릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-233">From these results, you might conclude that on targeted shifts you should reduce the response time to 90 percent of the current rate in order to improve service quality.</span></span>  
  
|<span data-ttu-id="256ae-234">교대조, 임금 및 요일</span><span class="sxs-lookup"><span data-stu-id="256ae-234">Shift, wage, and day</span></span>|<span data-ttu-id="256ae-235">현재 평균 응답 시간으로 예측되는 서비스 품질</span><span class="sxs-lookup"><span data-stu-id="256ae-235">Predicted service quality with current average response time</span></span>|<span data-ttu-id="256ae-236">응답 시간을 90퍼센트 줄여 예측되는 서비스 품질</span><span class="sxs-lookup"><span data-stu-id="256ae-236">Predicted service quality with 90 percent reduction in response time</span></span>|<span data-ttu-id="256ae-237">응답 시간을 80% 감소 하는 예측 서비스 품질</span><span class="sxs-lookup"><span data-stu-id="256ae-237">Predicted service quality with 80 percent reduction in response time</span></span>|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|<span data-ttu-id="256ae-238">Holiday AM</span><span class="sxs-lookup"><span data-stu-id="256ae-238">Holiday AM</span></span>|<span data-ttu-id="256ae-239">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-239">0.165</span></span>|<span data-ttu-id="256ae-240">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-240">0.05</span></span>|<span data-ttu-id="256ae-241">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-241">0.05</span></span>|  
|<span data-ttu-id="256ae-242">Holiday PM1</span><span class="sxs-lookup"><span data-stu-id="256ae-242">Holiday PM1</span></span>|<span data-ttu-id="256ae-243">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-243">0.05</span></span>|<span data-ttu-id="256ae-244">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-244">0.05</span></span>|<span data-ttu-id="256ae-245">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-245">0.05</span></span>|  
|<span data-ttu-id="256ae-246">Holiday Midnight</span><span class="sxs-lookup"><span data-stu-id="256ae-246">Holiday Midnight</span></span>|<span data-ttu-id="256ae-247">0.165</span><span class="sxs-lookup"><span data-stu-id="256ae-247">0.165</span></span>|<span data-ttu-id="256ae-248">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-248">0.05</span></span>|<span data-ttu-id="256ae-249">0.05</span><span class="sxs-lookup"><span data-stu-id="256ae-249">0.05</span></span>|  
  
 <span data-ttu-id="256ae-250">모델에서 만들 수 있는 여러 가지 기타 예측 쿼리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-250">There are a variety of other prediction queries that you can create on this model.</span></span> <span data-ttu-id="256ae-251">예를 들어 특정 서비스 수준을 만족하기 위해 또는 특정 개수의 들어오는 호출에 응답하기 위해 필요한 전화 상담원 수를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-251">For example, you could predict how many operators are required to meet a certain service level or to respond to a certain number of incoming calls.</span></span> <span data-ttu-id="256ae-252">로지스틱 회귀 모델에 여러 출력을 포함할 수 있기 때문에 여러 개별 모델을 만들지 않아도 서로 다른 독립 변수 및 결과를 쉽게 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-252">Because you can include multiple outputs in a logistic regression model, it is easy to experiment with different independent variables and outcomes without having to create many separate models.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="256ae-253">설명</span><span class="sxs-lookup"><span data-stu-id="256ae-253">Remarks</span></span>  
 <span data-ttu-id="256ae-254">Excel 2007용 데이터 마이닝 추가 기능에서는 로지스틱 회귀 마법사를 제공하기 때문에 서비스 등급을 특정 교대조에 대한 대상 수준으로 개선하는 데 필요한 두 번째 수준의 전화 상담원의 수와 같은 복잡한 질문에 보다 쉽게 대답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-254">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be required to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="256ae-255">데이터 마이닝 추가 기능은 무료로 다운로드할 수 있으며 신경망 또는 로지스틱 회귀 알고리즘을 기반으로 하는 마법사를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-255">The data mining add-ins are a free download, and include wizards that are based on the neural network or logistic regression algorithms.</span></span> <span data-ttu-id="256ae-256">자세한 내용은 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="256ae-256">For more information, see the following links:</span></span>  
  
-   <span data-ttu-id="256ae-257">[SQL Server 2005 Office 2007 용 데이터 마이닝 추가 기능](https://www.microsoft.com/sql/technologies/dm/addins.mspx): 목표 검색 및 What If 시나리오 분석</span><span class="sxs-lookup"><span data-stu-id="256ae-257">[SQL Server 2005 Data Mining Add-Ins for Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): Goal Seek and What If Scenario Analysis</span></span>  
  
-   <span data-ttu-id="256ae-258">[SQL Server 2008 Office 2007 용 데이터 마이닝 추가 기능](https://go.microsoft.com/fwlink/?LinkID=117790): 목표 검색 시나리오 분석, What If 시나리오 분석 및 예측 계산기</span><span class="sxs-lookup"><span data-stu-id="256ae-258">[SQL Server 2008 Data Mining Add-Ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Goal Seek Scenario Analysis, What If Scenario Analysis, and Prediction Calculator</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="256ae-259">결론</span><span class="sxs-lookup"><span data-stu-id="256ae-259">Conclusion</span></span>  
 <span data-ttu-id="256ae-260">이 단원에서는 Microsoft 신경망 알고리즘 및 Microsoft 로지스틱 회귀 알고리즘을 기반으로 하는 마이닝 모델을 생성, 사용자 지정 및 해석하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-260">You have learned to create, customize, and interpret mining models that are based on the Microsoft Neural Network algorithm and the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="256ae-261">이러한 모델 유형은 복잡하고 거의 제한 없이 다양하게 분석될 수 있으므로 복잡하고 마스터하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-261">These model types are sophisticated and permit almost infinite variety in analysis, and therefore can be complex and difficult to master.</span></span>  
  
 <span data-ttu-id="256ae-262">그러나 이러한 알고리즘은 요인의 여러 조합을 통해 반복을 수행하고 가장 강력한 상관 관계를 자동으로 식별할 수 있습니다. 이를 통해 Transact-SQL이나 PowerPivot을 사용한 데이터의 수동 탐색을 통해서는 발견하기가 매우 어려운 통찰력에 대한 통계학적 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="256ae-262">However, these algorithms can iterate through many combinations of factors and automatically identify the strongest correlations, providing statistical support for insights that would be very difficult to discover through manual exploration of data using Transact-SQL or even PowerPivot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256ae-263">참고 항목</span><span class="sxs-lookup"><span data-stu-id="256ae-263">See Also</span></span>  
 <span data-ttu-id="256ae-264">[로지스틱 회귀 모델 쿼리 예제](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="256ae-264">[Logistic Regression Model Query Examples](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span></span>  
 <span data-ttu-id="256ae-265">[Microsoft 로지스틱 회귀 알고리즘](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="256ae-265">[Microsoft Logistic Regression Algorithm](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="256ae-266">[Microsoft 신경망 알고리즘](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="256ae-266">[Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span></span>  
 [<span data-ttu-id="256ae-267">신경망 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="256ae-267">Neural Network Model Query Examples</span></span>](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
