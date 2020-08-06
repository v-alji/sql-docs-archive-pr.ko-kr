---
title: 가상 시나리오 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bb5c5e866c1320c297fb4f2760bca58623f6601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743468"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="a1a72-102">가상 시나리오(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="a1a72-102">What-If Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="a1a72-103">![테이블 분석 도구의 가정(What-If) 시나리오 단추](media/tat-whatif.gif "테이블 분석 도구의 가정(What-If) 시나리오 단추")</span><span class="sxs-lookup"><span data-stu-id="a1a72-103">![What If Scenario button in Table Analysis tools](media/tat-whatif.gif "What If Scenario button in Table Analysis tools")</span></span>

 <span data-ttu-id="a1a72-104">**가상** 시나리오 도구는 기존 데이터의 패턴을 분석 한 다음 한 열의 변경 내용이 다른 열의 값에 미치는 영향을 평가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-104">The **What-If** scenario tool analyzes patterns in existing data, and then enables you to evaluate the effect that changes in one column would have on the value of a different column.</span></span>

 <span data-ttu-id="a1a72-105">예를 들어 항목의 가격 상승이 총 판매량에 미치는 영향을 알아낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-105">For example, you could explore the effect of raising the price of an item on its total sales.</span></span>

 <span data-ttu-id="a1a72-106">도구로 만들 수 있는 예측 수는 조정이 가능하며</span><span class="sxs-lookup"><span data-stu-id="a1a72-106">The tool is flexible about the number of predictions you can create.</span></span> <span data-ttu-id="a1a72-107">초기 분석을 완료한 후 테이블의 모든 데이터에 대한 변경 내용을 예측할지 또는 한 번에 하나씩 테스트 값을 입력할지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-107">After the initial analysis is complete, you can either predict changes for all the data in the table, or enter test values one at a time.</span></span>

## <a name="using-the-what-if-scenario-tool"></a><span data-ttu-id="a1a72-108">가상 시나리오 도구 사용</span><span class="sxs-lookup"><span data-stu-id="a1a72-108">Using the What-If Scenario Tool</span></span>

1.  <span data-ttu-id="a1a72-109">Excel 데이터 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-109">Open an Excel data table.</span></span>

2.  <span data-ttu-id="a1a72-110">**시나리오**를 클릭 한 다음, **가상으로**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-110">Click **Scenarios**, and then select **What-If**.</span></span>

3.  <span data-ttu-id="a1a72-111">**시나리오** 상자에서 변경 하려는 값이 포함 된 열을 선택 하 고 현재 값에 대 한 변경 내용 (증가 또는 감소)을 특정 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-111">In the **Scenario** box, select the column that contains the value you will change, and specify the change either as a specific value or as a percentage of change (either increased or decreased) on the current values.</span></span>

4.  <span data-ttu-id="a1a72-112">**수행할 작업** 상자에 효과를 평가 하려는 열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-112">In the **What happens to** box, specify the column for which you want to assess the effect.</span></span>

5.  <span data-ttu-id="a1a72-113">필요에 따라 **분석에 사용할 열 선택** 을 클릭 하 여 예측을 만드는 데 유용할 수 있는 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-113">Optionally, click **Choose columns to be used for analysis** to select columns that are likely to be useful in making the prediction.</span></span> <span data-ttu-id="a1a72-114">또한 행 ID 또는 이름처럼 패턴을 검색하는 데 활용도가 적은 열은 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-114">You can also deselect columns that are likely to be of little use in detecting patterns, such as row IDs or names.</span></span>

6.  <span data-ttu-id="a1a72-115">**행 또는 테이블 지정** 상자에서 현재 선택 된 행에 대해서만 영향을 주는지 아니면 테이블의 전체 데이터 집합을 사용할지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-115">In the **Specify row or table** box, choose whether you want the impact assessed for the currently selected row only, or for the complete set of data in the table.</span></span>

7.  <span data-ttu-id="a1a72-116">**이 행**을 선택 하는 경우 도구는 대화 상자에 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-116">If you select **On this row**, the tool displays the result in the dialog box.</span></span> <span data-ttu-id="a1a72-117">대화 상자가 열려 있는 동안 선택 사항을 수정하여 다른 시나리오를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-117">While the dialog box remains open, you can modify your selections to test other scenarios.</span></span>

8.  <span data-ttu-id="a1a72-118">**전체 테이블**을 선택 하는 경우이 도구는 대화 상자에 상태 메시지를 표시 하 고 원래 데이터 테이블에 새 열 두 개를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-118">If you select **Entire table**, the tool displays a status message in the dialog box, and adds two new columns to the original data table.</span></span> <span data-ttu-id="a1a72-119">워크시트에서 전체 결과를 보려면 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-119">Click **Close** to view the complete results in the worksheet.</span></span>

### <a name="requirements"></a><span data-ttu-id="a1a72-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a1a72-120">Requirements</span></span>
 <span data-ttu-id="a1a72-121">이 도구에서는 숫자 값 또는 불연속 값의 예측을 지원하는 Microsoft 로지스틱 회귀 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-121">This tool uses the Microsoft Logistic Regression algorithm, which supports prediction of either numeric or discrete values.</span></span> <span data-ttu-id="a1a72-122">그러나 가장 좋은 결과를 얻으려면 다음 제안 사항을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a1a72-122">However, to achieve the best results, we suggest the following best practices:</span></span>

-   <span data-ttu-id="a1a72-123">유용한 정보를 포함하는 분석 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-123">Select columns for analysis that contain useful information.</span></span>

-   <span data-ttu-id="a1a72-124">열을 너무 적게 포함하면 결과를 얻기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-124">If you include too few columns it may be difficult to obtain a result.</span></span>

-   <span data-ttu-id="a1a72-125">**To value** 옵션을 사용 하는 경우 상자에 값을 입력 하거나 목록에서 값을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-125">If you use the **To value** option, you must type a value in the box or select a value from the list.</span></span>

-   <span data-ttu-id="a1a72-126">**백분율** 옵션을 사용 하는 경우 변경 내용을 백분율 증가 또는 감소로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-126">If you use the **Percentage** option, set the change as a percentage increase or decrease.</span></span> <span data-ttu-id="a1a72-127">기본값은 120%이며 현재 값보다 20% 증가한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-127">The default is 120%, meaning a 20% increase over the current value.</span></span>

> [!NOTE]
>  <span data-ttu-id="a1a72-128">값을 설정하지 않은 경우 오류 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-128">If you do not set a value, you might receive an error.</span></span>

## <a name="understanding-the-results-of-what-if-analysis"></a><span data-ttu-id="a1a72-129">가상 분석 결과 이해</span><span class="sxs-lookup"><span data-stu-id="a1a72-129">Understanding the Results of What-If Analysis</span></span>
 <span data-ttu-id="a1a72-130">**가상** 시나리오를 만들 때이 도구는 다음 세 가지 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-130">When you create a **What-If** scenario, the tool does three things:</span></span>

-   <span data-ttu-id="a1a72-131">테이블의 데이터에 대한 주요 요소를 저장하는 데이터 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="a1a72-131">Creates a data mining structure that stores key facts about the data in your table.</span></span>

-   <span data-ttu-id="a1a72-132">데이터 기반의 로지스틱 회귀 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="a1a72-132">Creates a logistic regression mining model based on the data.</span></span>

-   <span data-ttu-id="a1a72-133">지정한 각 값에 대한 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="a1a72-133">Creates a prediction query for each of the values you specify.</span></span>

 <span data-ttu-id="a1a72-134">**전체 테이블**을 지정 하 여 모든 예측을 한 번에 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-134">You can output all the predictions at one time by specifying **Entire table**.</span></span> <span data-ttu-id="a1a72-135">이렇게 하면 도구에서 원래 데이터 테이블에 새 열 두 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-135">The tool then creates two new columns in the original data table.</span></span>

 <span data-ttu-id="a1a72-136">테이블에 추가 되는 열에는 두 가지 유형의 정보가 포함 됩니다. 예측 값은 변경 된 것이 고 신뢰도는 확실 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-136">The columns that are added to the table contain two types of information: the predicted value given the change, and its confidence.</span></span> <span data-ttu-id="a1a72-137">신뢰도는 예측이 정확할 가능성을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-137">Confidence means the probability that the prediction is correct.</span></span>

 <span data-ttu-id="a1a72-138">대화 상자에서 변경 값을 하나씩 입력하고 대화형으로 예측을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-138">You can also enter change values one by one in the dialog box, and view the predictions interactively.</span></span> <span data-ttu-id="a1a72-139">이는 *단일 예측 쿼리*를 만드는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-139">This is the same as creating a *singleton prediction query*.</span></span> <span data-ttu-id="a1a72-140">예측 쿼리의 결과는 성공 또는 실패 예측, 예측 값 및 신뢰도 수준 정보와 함께 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-140">The results of the prediction query are output with the following information: the success or failure of prediction, the predicted value, and the confidence level.</span></span> <span data-ttu-id="a1a72-141">신뢰도 수준은 점선이 포함된 막대로 표시되며</span><span class="sxs-lookup"><span data-stu-id="a1a72-141">The confidence level is shown as a bar that contains a dotted line.</span></span> <span data-ttu-id="a1a72-142">점선이 길수록 결과의 신뢰도가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-142">The longer the dotted line, the higher the confidence in the result.</span></span>

 <span data-ttu-id="a1a72-143">예를 들어 고객의 열의 구매 기간을 늘리고 고객의 나이를 25로 늘리는 효과를 확인 하려는 경우 **가상** 도구는 데이터 마이닝 모델을 쿼리하고 다음 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-143">For example, if you are trying to determine the effect of increasing the customer's age on the customer's willingness to buy, and increase the customer's age to 25, the **What-If** tool queries the data mining model and returns the following result:</span></span>

 <span data-ttu-id="a1a72-144">**자전거 구입에 대한 가상 분석으로 솔루션을 찾았습니다.**</span><span class="sxs-lookup"><span data-stu-id="a1a72-144">**What-If Analysis for Purchases Bicycle has found a solution.**</span></span>

 <span data-ttu-id="a1a72-145">**'자전거 구입' = 예**</span><span class="sxs-lookup"><span data-stu-id="a1a72-145">**'Purchases Bicycle' = yes**</span></span>

 <span data-ttu-id="a1a72-146">**신뢰도: 양호**</span><span class="sxs-lookup"><span data-stu-id="a1a72-146">**Confidence: Fair**</span></span>

 <span data-ttu-id="a1a72-147">이 결과는 데이터 테이블의 기존 행에 기반을 두고 있으므로 특정 고객에 대해 그 밖의 모든 조건을 같게 유지하고 고객의 나이를 25세로 증가시키면 자전거를 구입할 가능성이 높아짐을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-147">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's age was increased to 25, the customer would likely buy a bicycle.</span></span>

 <span data-ttu-id="a1a72-148">원래 데이터 테이블에 예측을 출력하면 예측이 유용한지를 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-148">Outputting the predictions to the original data table might make it easier to determine whether the predictions are useful.</span></span>

## <a name="related-tools"></a><span data-ttu-id="a1a72-149">관련 도구</span><span class="sxs-lookup"><span data-stu-id="a1a72-149">Related Tools</span></span>
 <span data-ttu-id="a1a72-150">고급 데이터 마이닝 기능을 제공하는 별도의 추가 기능인 Excel용 데이터 마이닝 클라이언트에는 행위를 예측하는 데이터 마이닝 모델을 만들기 위한 마법사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1a72-150">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="a1a72-151">자세한 내용은 [데이터 마이닝 모델 만들기](creating-a-data-mining-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1a72-151">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="a1a72-152">**가상** 시나리오 도구에서 사용 하는 알고리즘에 대 한 자세한 내용은 SQL Server 온라인 설명서의 "Microsoft 로지스틱 회귀 알고리즘" 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a1a72-152">For more information about the algorithm used by the **What-If** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in SQL Server Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a72-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1a72-153">See Also</span></span>
 [<span data-ttu-id="a1a72-154">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="a1a72-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


