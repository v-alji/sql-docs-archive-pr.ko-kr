---
title: 예제로 채우기 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69ff9f554c51240eb6f9151718d30677bfb57996
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732195"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a><span data-ttu-id="cadf7-102">예제로 채우기(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="cadf7-102">Fill From Example (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="cadf7-103">![테이블 분석 도구의 예제로 채우기 단추](media/tat-fillex.gif "테이블 분석 도구의 예제로 채우기 단추")</span><span class="sxs-lookup"><span data-stu-id="cadf7-103">![Fill From Example button in Table Analysis Tools](media/tat-fillex.gif "Fill From Example button in Table Analysis Tools")</span></span>  
  
 <span data-ttu-id="cadf7-104">**예제로 채우기** 도구를 사용 하면 기존 값을 기반으로 데이터의 새 열을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-104">The **Fill From Example** tool helps you build new columns of data based on existing values.</span></span>  
  
 <span data-ttu-id="cadf7-105">예를 들어 데이터에 **구매 금액** 열, **주문 수량** 열 및 다른 열을 사용 하는 일부 수식을 기반으로 하는 **프리미어 고객** 열이 포함 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-105">For example, suppose your data contains a **Purchase Amount** column, an **Orders Quantity** column, and a **Premier Customer** column that is based on some formula using the other columns.</span></span> <span data-ttu-id="cadf7-106">**프리미어 고객** 열에 빈 행이 여러 개 있는 경우 **구매 금액** 및 **주문 수량** 열을 입력으로 사용 하 여 누락 된 값을 유추할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-106">If the  **Premier Customer** column contains many blank rows, you could use the **Purchase Amount** and **Orders Quantity** columns as the inputs, to infer the missing values.</span></span> <span data-ttu-id="cadf7-107">이 도구는 입력 한 예제와 함께 데이터의 기존 패턴을 분석 하 고 각 고객에 게 할당할 범주를 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-107">The tool analyzes existing patterns in the data together with the examples you entered, and predicts which category to assign to each customer.</span></span>  
  
 <span data-ttu-id="cadf7-108">결과가 만족스럽지 않으면 예제를 더 제공하여 결과를 구체화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-108">If you are not satisfied with the results, you can refine the results by providing more examples.</span></span>  
  
## <a name="using-the-fill-from-example-tool"></a><span data-ttu-id="cadf7-109">예제로 채우기 도구 사용</span><span class="sxs-lookup"><span data-stu-id="cadf7-109">Using the Fill From Example Tool</span></span>  
  
1.  <span data-ttu-id="cadf7-110">**분석** 리본에서 **예제로 채우기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-110">In the **Analyze** ribbon, click **Fill From Example**.</span></span>  
  
2.  <span data-ttu-id="cadf7-111">도구는 데이터 분석을 기반으로 채울 열을 자동으로 선택하며 사용자는 이 제안을 수용하거나 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-111">The tool will automatically pick a column to fill based on analysis of the data, and you can either accept or override this suggestion.</span></span>  
  
3.  <span data-ttu-id="cadf7-112">새 데이터에 대한 열을 만들고 예측하려는 데이터의 예제를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-112">Create a column for the new data, and type in examples of the data that you want to predict.</span></span> <span data-ttu-id="cadf7-113">예측하려는 각 값마다 하나 이상의 예제가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-113">Make sure that there is at least one example for every value that you want to predict.</span></span> <span data-ttu-id="cadf7-114">기존 열에 데이터를 채우는 경우 누락된 값이 있는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-114">If you are filling in data in an existing column, select the column that has missing values.</span></span>  
  
4.  <span data-ttu-id="cadf7-115">필요에 따라 **분석에 사용할 열 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-115">Optionally, click **Choose columns to be used in analysis**.</span></span> <span data-ttu-id="cadf7-116">**고급 열 선택** 대화 상자에서 누락 된 데이터를 입력할 때 유용할 가능성이 가장 높은 열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-116">In the **Advanced Columns Selection** dialog box, specify the columns that are most likely to be useful when filling in the missing data.</span></span>  
  
     <span data-ttu-id="cadf7-117">예를 들어 한 열과 누락된 값을 가진 열 사이에 인과적 효과가 있다는 것을 경험상 알고 있는 경우 다른 열의 선택을 취소하면 더 나은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-117">For example, if you know from experience that there is a causal effect between one column and the column that has missing values, you can deselect other columns to get better results.</span></span>  
  
     <span data-ttu-id="cadf7-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="cadf7-119">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-119">Click **Run**.</span></span>  
  
     <span data-ttu-id="cadf7-120">분석이 완료 되 면이 도구는 분석 결과를 포함 하는 새 **패턴** 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-120">When analysis is complete, the tool creates a new **Patterns** worksheet that contains the results of analysis.</span></span> <span data-ttu-id="cadf7-121">보고서에는 발견된 규칙 또는 주요 영향 요인이 나열되고 각 규칙의 확률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-121">The report lists the rules, or key influencers, that were found, and shows the probability for each rule.</span></span>  
  
     <span data-ttu-id="cadf7-122">또한 원래 데이터 테이블에 새 값을 포함하는 열이 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-122">The tool also automatically adds a column that contains the new values to the original data table.</span></span> <span data-ttu-id="cadf7-123">그러면 이 값을 검토하고 원래 값과 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-123">You can review the values and compare them against the original.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="cadf7-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cadf7-124">Requirements</span></span>  
 <span data-ttu-id="cadf7-125">열에 있는 데이터만 사용하여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-125">You can only work with data in columns.</span></span> <span data-ttu-id="cadf7-126">채우려는 계열이 행에 저장되어 있는 경우 Excel의 붙여넣기, 바꾸기 기능을 사용하여 데이터를 열 형식으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-126">If the series that you want to fill is stored in a row, you can use the Paste, Transpose function in Excel to change the data to a columnar format.</span></span>  
  
## <a name="understanding-the-pattern-report"></a><span data-ttu-id="cadf7-127">패턴 보고서 이해</span><span class="sxs-lookup"><span data-stu-id="cadf7-127">Understanding the Pattern Report</span></span>  
 <span data-ttu-id="cadf7-128">**예제로 채우기** 도구를 실행 하면 검색 된 패턴에 대 한 자세한 정보를 제공 하는 보고서가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-128">When you run the **Fill From Example** tool, a report is created that provides more information about the patterns that were detected.</span></span> <span data-ttu-id="cadf7-129">이러한 패턴은 새 데이터 값을 추정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-129">These patterns are used for extrapolating new data values.</span></span>  
  
 <span data-ttu-id="cadf7-130">패턴 보고서는 각 예측 값에 대한 주요 영향 요인을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-130">The Pattern Report shows the key influencers for each value that was predicted.</span></span> <span data-ttu-id="cadf7-131">각 영향 요인 또는 규칙은 열, 해당 열의 값 및 예측에 대한 규칙의 상대적 영향의 조합으로 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-131">Each influencer or rule is described as a combination of a column, the value in that column, and the relative impact of the rule on the prediction.</span></span>  
  
 <span data-ttu-id="cadf7-132">예를 들어 주문에 대한 배송 거리를 보여 주는 워크시트를 채우려고 하는 경우 논리상 배송 거리에는 목적지가 강한 영향력을 미칠 것으로 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-132">For example, if you were trying to fill in a worksheet that shows the shipping distance for orders, you might logically expect the destination to have a strong impact on the value for shipping distance.</span></span> <span data-ttu-id="cadf7-133">이 경우 보고서에는 다음과 같은 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-133">In this case, the report might contain the following row:</span></span>  
  
|<span data-ttu-id="cadf7-134">열</span><span class="sxs-lookup"><span data-stu-id="cadf7-134">Column</span></span>|<span data-ttu-id="cadf7-135">값</span><span class="sxs-lookup"><span data-stu-id="cadf7-135">Value</span></span>|<span data-ttu-id="cadf7-136">유사성</span><span class="sxs-lookup"><span data-stu-id="cadf7-136">Favors</span></span>|<span data-ttu-id="cadf7-137">상대적 영향</span><span class="sxs-lookup"><span data-stu-id="cadf7-137">Relative Impact</span></span>|  
|------------|-----------|------------|---------------------|  
|<span data-ttu-id="cadf7-138">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="cadf7-138">StateProvinceCode</span></span>|<span data-ttu-id="cadf7-139">AB</span><span class="sxs-lookup"><span data-stu-id="cadf7-139">AB</span></span>|<span data-ttu-id="cadf7-140">>500 킬로미터</span><span class="sxs-lookup"><span data-stu-id="cadf7-140">>500 kilometers</span></span>|<span data-ttu-id="cadf7-141">80%</span><span class="sxs-lookup"><span data-stu-id="cadf7-141">80%</span></span>|  
  
 <span data-ttu-id="cadf7-142">즉, **StateProvinceCode** 열의 AB 값이 500 킬로미터 >배송 거리를 강력 하 게 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-142">This means that the value AB in the **StateProvinceCode** column strongly predicts a shipping distance of >500 kilometers.</span></span>  
  
 <span data-ttu-id="cadf7-143">일반적으로 예측은 이 예보다 훨씬 더 복잡한 패턴을 기반으로 수행되며, 보고서에는 각 예측에 대해 많은 규칙 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-143">Typically, predictions are based on patterns that are far more complex than this example, and the report may contain many rows of rules for each prediction.</span></span> <span data-ttu-id="cadf7-144">모든 규칙의 영향이 결합되어 예측 값을 도출합니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-144">The effect of all the rules are combined to derive the predicted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cadf7-145">**상대적 영향은** 음영이 있는 막대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-145">**Relative Impact** is shown as a shaded bar.</span></span> <span data-ttu-id="cadf7-146">막대가 길수록 해당 규칙이 채운 값을 예측할 확률이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-146">The longer the bar, the greater the probability that this rule is predictive of the filled-in value.</span></span>  
  
 <span data-ttu-id="cadf7-147">또한이 도구는 확장 이라는 원래 데이터 테이블에 새 열을 추가 합니다 \<column name> .</span><span class="sxs-lookup"><span data-stu-id="cadf7-147">The tool also adds a new column to the original data table, named \<column name> Extended.</span></span>  
  
 <span data-ttu-id="cadf7-148">원래 데이터 열에 값이 있으면 해당 값은 새 열에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-148">If the original data column contained a value, that value is copied into the new column.</span></span> <span data-ttu-id="cadf7-149">원래 열에 빈 셀이 있으면 새 열에는 마법사에서 예측한 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-149">However, if the original column contained a blank cell, the new column contains the value that was predicted by the wizard.</span></span>  
  
## <a name="related-tools-and-information"></a><span data-ttu-id="cadf7-150">관련 도구 및 정보</span><span class="sxs-lookup"><span data-stu-id="cadf7-150">Related Tools and Information</span></span>  
 <span data-ttu-id="cadf7-151">Excel 용 데이터 마이닝 클라이언트에서 사용할 수 있는 [데이터 탐색](explore-data-sql-server-data-mining-add-ins.md) 마법사를 사용 하 여 excel 열의 값 분포를 검사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cadf7-151">You can also use the [Explore Data](explore-data-sql-server-data-mining-add-ins.md) wizard, available in the Data Mining Client for Excel, to examine the distribution of values in an Excel column.</span></span> <span data-ttu-id="cadf7-152">자세한 내용은 [데이터 탐색 및 정리](exploring-and-cleaning-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cadf7-152">For more information, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadf7-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cadf7-153">See Also</span></span>  
 [<span data-ttu-id="cadf7-154">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="cadf7-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
