---
title: 정확도 차트 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 45ca5b4d3944948b257b5fa063ebce5583701157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647348"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="34418-102">정확도 차트(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="34418-102">Accuracy Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="34418-103">![데이터 마이닝 리본 메뉴의 정확도 차트 단추](media/dmc-accchart.gif "데이터 마이닝 리본 메뉴의 정확도 차트 단추")</span><span class="sxs-lookup"><span data-stu-id="34418-103">![Accuracy Chart button in Data Mining ribbon](media/dmc-accchart.gif "Accuracy Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="34418-104">정확도 차트를 사용하면 모델을 새로운 데이터 집합에 적용하고 모델이 얼마나 잘 작동하는지 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-104">An accuracy chart enables you to apply a model to a new set of data and then evaluate how well the model performs.</span></span> <span data-ttu-id="34418-105">이 마법사로 만든 정확도 차트는 데이터 마이닝 모델의 정확도를 측정 하는 데 자주 사용 되는 차트의 유형인 *리프트 차트*입니다.</span><span class="sxs-lookup"><span data-stu-id="34418-105">The accuracy chart created by this wizard is a *lift chart*, which is a type of chart that is frequently used to measure the accuracy of a data mining model.</span></span> <span data-ttu-id="34418-106">이 유형의 정확도 차트는 지정된 데이터 마이닝 모델을 사용함으로써 얻을 수 있는 기능 향상을 무작위 예측 및 예측이 100% 정확한 이상적인 사례와 비교하여 그래픽 표현으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34418-106">This type of accuracy chart displays a graphical representation of the improvement that you obtain from using the specified data mining model, as compared to random predictions, and to the ideal case where 100 percent of predictions are accurate.</span></span> <span data-ttu-id="34418-107">하나의 차트 내에서 여러 모델을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-107">You can compare multiple models within a single chart.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34418-108">예제</span><span class="sxs-lookup"><span data-stu-id="34418-108">Example</span></span>  
 <span data-ttu-id="34418-109">Adventure Works Cycles의 마케팅 부서에서 타겟 메일링 캠페인을 만들려고 한다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="34418-109">Consider the case in which the Marketing department at Adventure Works Cycles wants to create a targeted mailing campaign.</span></span> <span data-ttu-id="34418-110">과거 캠페인을 통해 응답률이 일반적으로 10%임을 알아냈습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-110">From past campaigns, they know that a 10 percent response rate is typical.</span></span> <span data-ttu-id="34418-111">이 부서의 데이터베이스에는 10,000명의 잠재적인 고객 목록이 테이블에 저장되어 있는데</span><span class="sxs-lookup"><span data-stu-id="34418-111">They have a list of 10,000 potential customers stored in a table in the database.</span></span> <span data-ttu-id="34418-112">일반 응답률을 기준으로 이 중 1,000명의 고객이 응답하리라는 것을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-112">Based on the typical response rate, they can expect 1,000 customers to respond.</span></span>  
  
 <span data-ttu-id="34418-113">그러나 5,000명의 고객에게만 광고 메일을 전송할 수 있는 경우 마케팅 부서에서는 마이닝 모델을 사용하여 응답 가능성이 가장 높은 5,000명의 고객을 대상으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-113">However, because they can afford to mail an advertisement to only 5,000 customers, the Marketing department uses a mining model to target the 5,000 customers who are most likely to respond.</span></span>  
  
 <span data-ttu-id="34418-114">회사에서 5,000명의 고객을 임의로 선택하는 경우 일반적으로 대상 고객의 10%만 응답하므로 500개의 응답만 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-114">If the company randomly selects 5,000 customers, they can expect to receive only 500 positive responses, because only 10 percent of those who are targeted typically respond.</span></span> <span data-ttu-id="34418-115">이 시나리오는 리프트 차트에서 임의 선으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="34418-115">This scenario is what the random line in the lift chart represents.</span></span>  
  
 <span data-ttu-id="34418-116">그러나 마케팅 부서에서 마이닝 모델을 사용하여 메일 전송 대상을 결정하며 이러한 모델이 완벽한 경우에는 모델에서 권장하는 잠재 고객 1,000명에게 광고 메일을 전송하여 1,000개의 응답을 모두 받을 것으로 기대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-116">However, if the Marketing department uses a mining model to target their mailing, and if the model were perfect, the company could expect to receive 1,000 responses by mailing an advertisement to the 1,000 potential customers recommended by the model.</span></span> <span data-ttu-id="34418-117">이 시나리오는 리프트 차트에서 이상적인 선으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="34418-117">This scenario is represented by the ideal line in the lift chart.</span></span>  
  
## <a name="using-the-accuracy-chart-wizard"></a><span data-ttu-id="34418-118">정확도 차트 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="34418-118">Using the Accuracy Chart Wizard</span></span>  
 <span data-ttu-id="34418-119">정확도 차트를 만들려면 기존 데이터 마이닝 구조를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-119">To create an accuracy chart, you must reference an existing data mining structure.</span></span> <span data-ttu-id="34418-120">해당 구조를 기반으로 같은 내용을 예측하는 여러 모델의 정확도를 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-120">You can measure the accuracy of multiple models that are based on that structure, as long as they predict the same thing.</span></span>  
  
 <span data-ttu-id="34418-121">구조를 사용할 수 있는지 잘 모르는 경우 서버를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-121">If you are not sure which structures are available, you can browse the server.</span></span> <span data-ttu-id="34418-122">자세한 내용은 [데이터 마이닝 추가 기능&#41;SQL Server Excel에서 모델 찾아보기 &#40;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34418-122">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-an-accuracy-chart"></a><span data-ttu-id="34418-123">정확도 차트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="34418-123">To create an accuracy chart</span></span>  
  
1.  <span data-ttu-id="34418-124">**데이터 마이닝 클라이언트** 리본을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-124">Click the **Data Mining Client** ribbon.</span></span>  
  
2.  <span data-ttu-id="34418-125">**정확도 및 유효성 검사** 그룹에서 **정확도 차트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-125">In the **Accuracy and Validation** group, click **Accuracy Chart**.</span></span>  
  
3.  <span data-ttu-id="34418-126">**구조 또는 모델 선택** 대화 상자에서 평가 하려는 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-126">In the **Select Structure or Model** dialog box, choose the model that you want to evaluate.</span></span> <span data-ttu-id="34418-127">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-127">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34418-128">테스트하려는 데이터와 가장 일치하는 모델을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-128">You must choose a model that closely matches the data you intend to test.</span></span>  
  
4.  <span data-ttu-id="34418-129">**예측할 열과 예측할 값 지정** 대화 상자에서 예측할 열과 대상 값 (해당 하는 경우)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-129">In the **Specify Column to Predict and Value to Predict** dialog box, choose the column that you want to predict, and a target value, if appropriate.</span></span> <span data-ttu-id="34418-130">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-130">Click **Next**.</span></span>  
  
     <span data-ttu-id="34418-131">예를 들어 위 예에서는 고객 응답을 모델링하는 열을 선택하고 대상 값을 "구입 가능성 있음"으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-131">For example, in the example above, you might choose the column that models the customer response, and specify the target value as "Probably Will Buy".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34418-132">연속 값은 예측할 수 없지만</span><span class="sxs-lookup"><span data-stu-id="34418-132">You cannot predict a continuous value.</span></span> <span data-ttu-id="34418-133">값을 불연속 범위로 분리하여 해당 열을 불연속화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-133">However, you can discretize the column by separating the values into discrete ranges.</span></span> <span data-ttu-id="34418-134">열 불연속화는 데이터 마이닝 모델을 만들기 전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-134">You must do this before creating the data mining model.</span></span>  
  
5.  <span data-ttu-id="34418-135">**원본 데이터 선택** 대화 상자에서 예측을 만들기 위해 모델을 통해 전달 되는 데이터의 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-135">In the **Select Source Data** dialog box, specify the source of the data that you will pass through the model in order to create a prediction.</span></span>  
  
6.  <span data-ttu-id="34418-136">모델에 저장 된 테스트 데이터가 아닌 외부 데이터 원본을 사용 하는 경우 **관계 지정** 대화 상자에서 새 원본 데이터의 열을 데이터 마이닝 모델에 사용 된 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-136">If you are using an external source of data, and not the test data that is stored with the model, in the **Specify Relationships** dialog box, map the columns in the new source data to the columns used in the data mining model.</span></span>  
  
     <span data-ttu-id="34418-137">열 이름이 비슷한 경우 마법사가 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-137">If the column names are similar, the wizard will automatically map them.</span></span> <span data-ttu-id="34418-138">입력 데이터에 분석과 관계없는 무시할 수 있는 열이 일부 포함되어 있는 경우에도 데이터 마이닝 모델이 입력을 처리하려면 해당 열이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-138">Although some columns in your input data may be irrelevant to analysis and can be ignored, some columns are required for the data mining model to process the input.</span></span> <span data-ttu-id="34418-139">이러한 열에는 트랜잭션 ID, 대상 값 또는 예측에 사용된 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-139">Such columns might include a transaction ID, the target value, or columns used for prediction.</span></span> <span data-ttu-id="34418-140">필요한 열을 매핑하지 못하면 마법사가 경고 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-140">If you fail to map a column that is required, the wizard will provide a warning message.</span></span>  
  
7.  <span data-ttu-id="34418-141">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-141">Click **Finish**.</span></span>  
  
     <span data-ttu-id="34418-142">마법사에서 리프트 차트 및 기본 데이터를 포함하는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34418-142">The wizard creates a report that includes the lift chart and underlying data.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="34418-143">요구 사항</span><span class="sxs-lookup"><span data-stu-id="34418-143">Requirements</span></span>  
 <span data-ttu-id="34418-144">불연속 값을 예측하는 경우 예측할 대상 값을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-144">If you are predicting a discrete value, you must select the target value that you want to predict.</span></span> <span data-ttu-id="34418-145">예를 들어 데이터가 "예: 구입"을 1로 분류 하 고 응답을 "아니요: 구매 하지 않음"으로 2로 분류 하는 경우에는 1 또는 2를 예측 값으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-145">For example, if your data is categorized with a response "Yes: Buy" as 1 and the response "No: Do Not Buy" as 2, you must specify either 1 or 2 as the prediction values.</span></span> <span data-ttu-id="34418-146">그러나 값 범위를 예측하는 경우 값을 한 번에 두 개만 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-146">However, if you want to predict a range of values, you can compare only two values at a time.</span></span> <span data-ttu-id="34418-147">예를 들어 5 보다 큰 점수를 예측 하려는 경우 원본 데이터를 레이블 재지정 하 고 결과를 두 개의 집합으로 구분 하는 새 모델을 만들어야 합니다. 5 보다 크고 5 보다 작은 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="34418-147">For example, if you want to predict a score above 5, you might have to relabel your source data and create a new model that separates the results into two sets: those greater than 5 and those less than 5.</span></span> <span data-ttu-id="34418-148">그런 다음 이러한 두 그룹의 정확도 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-148">You can then compare the accuracy of those two groups.</span></span>  
  
## <a name="understanding-accuracy"></a><span data-ttu-id="34418-149">정확도 이해</span><span class="sxs-lookup"><span data-stu-id="34418-149">Understanding Accuracy</span></span>  
 <span data-ttu-id="34418-150">예측 가능한 열의 상태를 지정하는 차트 종류와 상태를 지정하지 않는 차트 종류를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34418-150">You can create two types of charts, one in which you specify a state of the predictable column, and one in which you do not specify the state.</span></span>  
  
 <span data-ttu-id="34418-151">예측 가능한 열의 상태를 지정하는 경우 차트의 X축은 예측을 비교하는 데 사용되는 테스트 데이터 세트의 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34418-151">If you specify the state of the predictable column, the x-axis of the chart represents the percentage of the test dataset that is used to compare the predictions.</span></span> <span data-ttu-id="34418-152">차트의 Y축은 지정한 상태로 예측되는 값의 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34418-152">The y-axis of the chart represents the percentage of values that are predicted to be the specified state.</span></span>  
  
 <span data-ttu-id="34418-153">예측 가능한 열의 상태를 지정하지 않는 경우에는 가능한 모든 예측에 대해 모델의 정확도가 차트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34418-153">If you do not specify the state of the predictable column, the chart shows the accuracy of the model for all possible predictions.</span></span>  
  
 <span data-ttu-id="34418-154">리프트 차트 작업 방법과 무작위 및 이상적인 예측 선을 기반으로 정확도를 계산하는 방법은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 "리프트 차트" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="34418-154">For more information about how a lift chart works, and how accuracy is calculated based on the random and ideal prediction lines, see the topic "Lift Chart" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34418-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34418-155">See Also</span></span>  
 [<span data-ttu-id="34418-156">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;</span><span class="sxs-lookup"><span data-stu-id="34418-156">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
