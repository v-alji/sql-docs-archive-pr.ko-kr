---
title: 목표 검색 시나리오 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b3b4df4f78a2d3652b1dac3c566e66507b523ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649257"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="e2564-102">목표 검색 시나리오(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="e2564-102">Goal Seek Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="e2564-103">![테이블 분석 도구의 목표 검색 단추](media/tat-goalseek.gif "테이블 분석 도구의 목표 검색 단추")</span><span class="sxs-lookup"><span data-stu-id="e2564-103">![Goal Seek button in Table Analysis tools](media/tat-goalseek.gif "Goal Seek button in Table Analysis tools")</span></span>  
  
 <span data-ttu-id="e2564-104">**목표 검색** 시나리오 도구는 [What If](what-if-scenario-table-analysis-tools-for-excel.md) 시나리오 도구를 보완 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-104">The **Goal Seek** scenario tool is complementary to the [What If](what-if-scenario-table-analysis-tools-for-excel.md) scenario tool.</span></span> <span data-ttu-id="e2564-105">**가상** 도구는 변경을 수행 하는 영향을 알려 주지만 **목표 검색** 도구는 원하는 결과를 얻기 위해 변경 해야 하는 기본 요소를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-105">The **What-If** tool tells you the impact of making a change, whereas the **Goal Seek** tool tells you the underlying factors that must change to achieve a desired result.</span></span>  
  
 <span data-ttu-id="e2564-106">예를 들어 고객 만족도를 높이는 것이 목표 라고 가정 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-106">For example, let's say your goal is to increase customer satisfaction.</span></span> <span data-ttu-id="e2564-107">**목표 검색** 분석을 사용 하 여 고객 만족도를 높일 가능성이 가장 높은 요소를 확인 하 고 이러한 변경 내용이 비용 효율적인 지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-107">You can use **Goal Seek** analysis to determine which factors would be most likely to increase customer satisfaction, and decide whether those changes are cost-effective.</span></span>  
  
 <span data-ttu-id="e2564-108">도구에서는 분석을 완료하면 원본 데이터 테이블에 두 개의 열을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-108">When the tool finishes its analysis, it creates two new columns in the source data table.</span></span> <span data-ttu-id="e2564-109">이러한 열은 대상 결과를 달성할 수 있는 *가능성* 및 권장 되는 변경 내용 (있는 경우)을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-109">These columns show the *likelihood* that the targeted outcome can be achieved, and the recommended change, if any.</span></span>  
  
 <span data-ttu-id="e2564-110">이 도구에서는 데이터 집합을 분석하고 전체 집합에 대한 예측을 수행할 수도 있고 분석을 만든 다음 시나리오를 한 번에 하나씩 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-110">The tool can analyze a set of data and make predictions for the entire set, or you can create the analysis and then test scenarios one at a time.</span></span>  
  
## <a name="using-the-goal-seek-scenario-tool"></a><span data-ttu-id="e2564-111">목표 검색 시나리오 도구 사용</span><span class="sxs-lookup"><span data-stu-id="e2564-111">Using the Goal Seek Scenario Tool</span></span>  
  
1.  <span data-ttu-id="e2564-112">Excel 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-112">Open an Excel table.</span></span>  
  
2.  <span data-ttu-id="e2564-113">**시나리오**를 클릭 하 고 **목표 검색**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-113">Click **Scenarios**, and select **Goal Seek**.</span></span>  
  
3.  <span data-ttu-id="e2564-114">**시나리오 분석: 목표 검색** 대화 상자의 목록에서 대상 값을 포함 하는 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-114">In the **Scenario Analysis: Goal Seek** dialog box, select the column that contains the target value from the list.</span></span>  
  
4.  <span data-ttu-id="e2564-115">달성할 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-115">Specify the value that you want to achieve.</span></span>  
  
     <span data-ttu-id="e2564-116">열 목표에 연속 숫자 값이 들어 있으면 원하는 값 증감분을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-116">If the column goal contains continuous numeric values, you can also specify a desired increase or decrease in the value.</span></span> <span data-ttu-id="e2564-117">예를 들어 **Sales** 를 열로 선택 하 고 목표를 120% 증가 하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-117">For example, you might choose **Sales** as the column and specify that the target is an increase of 120%.</span></span>  
  
     <span data-ttu-id="e2564-118">목표를 값 범위로 지정하고 하한과 상한을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-118">Or, you can specify the goal as a range of values, by typing a lower and upper limit.</span></span>  
  
5.  <span data-ttu-id="e2564-119">변경할 값이 들어 있는 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-119">Specify the column that contains the values you will change.</span></span> <span data-ttu-id="e2564-120">즉 원하는 결과를 얻기 위해 조정할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-120">In other words, pick the column that will be manipulated to produce the desired result.</span></span>  
  
6.  <span data-ttu-id="e2564-121">필요에 따라 **분석에 사용할 열 선택**을 클릭 하 고 유용한 정보가 포함 된 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-121">Optionally, click **Choose columns to be used for analysis**, and select columns that contain useful information.</span></span> <span data-ttu-id="e2564-122">분석에 도움이 되지 않는 열은 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-122">Deselect columns that will not contribute to the analysis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2564-123">목표 또는 변경을 위해 사용할 열의 선택은 취소하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="e2564-123">Do not deselect columns that you will use for either the goal or the change.</span></span> <span data-ttu-id="e2564-124">이러한 열은 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-124">These columns are required.</span></span>  
  
7.  <span data-ttu-id="e2564-125">전체 테이블에 대해 예측할지 선택한 행에 대해서만 예측할지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-125">Specify whether you want to make predictions for the entire table, or for only the selected row.</span></span>  
  
8.  <span data-ttu-id="e2564-126">**전체 테이블** 옵션을 선택한 경우이 도구는 두 개의 새 열에서 원본 테이블에 대 한 예측을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-126">If you selected the **Entire table** option, the tool adds the predictions to the source table in two new columns.</span></span>  
  
9. <span data-ttu-id="e2564-127">**이 행에서**옵션을 선택 하면 분석 결과가 검토를 위해 대화 상자에 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-127">If you selected the option **On this row**, the results of analysis are output to the dialog box for review.</span></span> <span data-ttu-id="e2564-128">이 대화 상자는 여러 가지 값과 목표를 계속 시도해 볼 수 있도록 열린 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-128">The dialog box stays open so that you can continue trying out different values and goals.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="e2564-129">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e2564-129">Requirements</span></span>  
 <span data-ttu-id="e2564-130">이 도구에서는 숫자 값 또는 불연속 값을 처리할 수 있는 Microsoft 로지스틱 회귀 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-130">This tool uses the Microsoft Logistic Regression algorithm, which can process either numeric or discrete values.</span></span>  
  
 <span data-ttu-id="e2564-131">예측을 여러 번 실행하고 나중에 여러 열을 선택할 수 있지만 각 목표 및 변경의 조합은 별도로 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-131">You can run the prediction multiple times, and select different columns later, but each combination of a goal and a change must be calculated separately.</span></span>  
  
 <span data-ttu-id="e2564-132">유용한 정보가 있는 열을 분석에 사용하도록 선택하면 더 좋은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-132">You can achieve better results if you select columns for analysis that contain useful information.</span></span> <span data-ttu-id="e2564-133">하지만 포함되는 열이 너무 적으면 결과를 얻기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-133">However, if you include too few columns, it might be difficult to obtain a result.</span></span>  
  
 <span data-ttu-id="e2564-134">한 번에 하나씩 예측을 만드는 경우 원하는 결과가 이미 들어 있는 행을 선택하지 않아야 합니다. 그렇지 않으면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-134">When you create predictions one at a time, be sure to select a row that does not already contain the desired result, or you may get an error.</span></span> <span data-ttu-id="e2564-135">즉 목표 검색의 목적이 자전거 구매를 촉진하는 요인을 파악하는 것이라면 자전거를 구매하지 않은 고객만 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-135">In other words, if the purpose of goal seeking is to determine factors that encourage bike purchases, you should only include customers who did not purchase a bike.</span></span>  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a><span data-ttu-id="e2564-136">목표 검색 분석 결과 이해</span><span class="sxs-lookup"><span data-stu-id="e2564-136">Understanding the Results of Goal Seek Analysis</span></span>  
 <span data-ttu-id="e2564-137">목표 검색 시나리오를 만들 때 도구에서는 다음과 같은 3가지 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-137">When you create a goal seeking scenario, the tool does three things:</span></span>  
  
-   <span data-ttu-id="e2564-138">테이블의 데이터에 대한 주요 요소를 저장하는 데이터 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="e2564-138">Creates a data mining structure that stores key facts about the data in your table.</span></span>  
  
-   <span data-ttu-id="e2564-139">데이터 기반의 로지스틱 회귀 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="e2564-139">Creates a logistic regression mining model based on the data.</span></span>  
  
-   <span data-ttu-id="e2564-140">지정한 각 값에 대한 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="e2564-140">Creates a prediction for each value that you specify.</span></span>  
  
 <span data-ttu-id="e2564-141">목표 검색 시나리오를 한 번에 하나씩 테스트하는 경우 결과를 대화형으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-141">If you test goal-seeking scenarios one at a time, you can view the results interactively.</span></span> <span data-ttu-id="e2564-142">이는 *단일 예측 쿼리*를 만드는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-142">This is the same as creating a *singleton prediction query*.</span></span>  
  
 <span data-ttu-id="e2564-143">이 도구는 원하는 목표를 달성 하는 시나리오를 찾기가 성공 했는지 여부를 대화 상자의 **결과** 창에 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-143">The tool reports in the **Results** pane of the dialog box whether it was successful in finding a scenario that achieves the desired goal.</span></span> <span data-ttu-id="e2564-144">성공적인 솔루션을 찾은 경우에는 필요한 변경에 대한 권장 사항도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-144">If a successful solution was found, the tool also generates a recommendation that tells you the required change.</span></span> <span data-ttu-id="e2564-145">예를 들어 **목표 검색** 도구는 통근 이나 출장 거리가 5 마일 미만인 지를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-145">For example, the **Goal Seek** tool might tell you that the commuting distance should be less than 5 miles.</span></span>  
  
 <span data-ttu-id="e2564-146">결과 예:</span><span class="sxs-lookup"><span data-stu-id="e2564-146">Example results:</span></span>  
  
 <span data-ttu-id="e2564-147">**구매 관심도에 대한 목표 검색으로 솔루션을 찾았습니다.**</span><span class="sxs-lookup"><span data-stu-id="e2564-147">**Goal Seeking for Interest in Buying has found a solution.**</span></span>  
  
 <span data-ttu-id="e2564-148">**'통근 거리'를 '2-5마일'로 변경하여 가장 근접하게 일치하는 항목을 얻었습니다.**</span><span class="sxs-lookup"><span data-stu-id="e2564-148">**Closest match obtained by changing 'Commute distance' to '2-5 miles'.**</span></span>  
  
 <span data-ttu-id="e2564-149">이 결과는 데이터 테이블의 기존 행을 기반으로 합니다. 이는 특정 고객에 대해 다른 모든 요소는 그대로 두고 통근 거리만 2-5마일로 줄이는 경우 고객이 자전거를 구매할 가능성이 다소 높아짐을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-149">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's commute was reduced to 2-5 miles, the customer would be somewhat more likely buy a bicycle.</span></span>  
  
 <span data-ttu-id="e2564-150">**전체 테이블**을 지정 하 여 Excel 테이블의 모든 행에 대 한 목표 검색 예측을 만드는 경우 thetool는 원래 데이터 테이블에 새 열 두 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-150">If you create goal-seeking predictions for all the rows in the Excel table by specifying **Entire table**, thetool creates two new columns in the original data table.</span></span> <span data-ttu-id="e2564-151">테이블에 추가된 첫 번째 열은 목표 충족이 가능함을 나타내는 녹색 원 내의 체크 표시를 포함하거나, 목표 달성이 가능하도록 변경할 수 없음을 나타내는 빨강 원 내의 X표를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-151">The first column that is added to the table contains either a check mark in a green circle, to indicate that the goal can be met, or an X mark in a red circle, to indicate that no changes can be made that will enable the goal.</span></span>  
  
 <span data-ttu-id="e2564-152">두 번째 열에는 권장 변경 사항이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-152">The second column contains the recommended change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2564-153">권장 및 성공에 대한 신뢰도 수준은 알고리즘으로 미리 결정되며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-153">The confidence level for the recommendation and its success are predetermined by the algorithm and cannot be changed.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="e2564-154">관련 도구</span><span class="sxs-lookup"><span data-stu-id="e2564-154">Related Tools</span></span>  
 <span data-ttu-id="e2564-155">고급 데이터 마이닝 기능을 제공하는 별도의 추가 기능인 Excel용 데이터 마이닝 클라이언트에는 행위를 예측하는 데이터 마이닝 모델을 만들기 위한 마법사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2564-155">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="e2564-156">자세한 내용은 [데이터 마이닝 모델 만들기](creating-a-data-mining-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2564-156">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
 <span data-ttu-id="e2564-157">**목표 검색** 시나리오 도구에서 사용 하는 알고리즘에 대 한 자세한 내용은 온라인 설명서의 "Microsoft 로지스틱 회귀 알고리즘" 항목을 참조 하십시오 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2564-157">For more information about the algorithm used by the **Goal Seek** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2564-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2564-158">See Also</span></span>  
 [<span data-ttu-id="e2564-159">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="e2564-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
