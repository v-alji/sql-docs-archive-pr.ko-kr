---
title: 주요 영향 요인 분석 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
ms.openlocfilehash: f60eb5144059b0976d52eec2329f27553132146c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648180"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a><span data-ttu-id="b1209-102">주요 영향 요인 분석(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="b1209-102">Analyze Key Influencers (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="b1209-103">![리본 메뉴의 주요 영향 요인 분석 단추](media/tat-aki.gif "리본 메뉴의 주요 영향 요인 분석 단추")</span><span class="sxs-lookup"><span data-stu-id="b1209-103">![Analyze Key Influencers button in ribbon](media/tat-aki.gif "Analyze Key Influencers button in ribbon")</span></span>  
  
 <span data-ttu-id="b1209-104">주요 영향 **요인 분석** 도구를 사용 하 여 대상 결과가 포함 된 열을 선택 하면 알고리즘은 결과에 가장 강한 영향을 주는 요인을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-104">With the **Analyze Key Influencers** tool, you choose a column that contains a target outcome, and the algorithm determines which factors had the strongest influence on the outcome.</span></span>  
  
 <span data-ttu-id="b1209-105">도구는 각 결과와 관련된 요인을 보고하며 해당 관계의 확률을 그래픽으로 표시하는 새 데이터 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-105">The tool creates new data tables that report the factors associated with each outcome and graphically displays the probability of the relationship.</span></span> <span data-ttu-id="b1209-106">다양한 요인과 결과로 테이블을 필터링하여 결과를 더 심층적으로 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-106">You can filter the tables by different factors and outcomes to explore the results in more depth.</span></span>  
  
 <span data-ttu-id="b1209-107">또한 가능한 결과 쌍을 선택하고 비교할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-107">You can also select a pair of possible outcomes and compare them.</span></span> <span data-ttu-id="b1209-108">예를 들어, 여러 그룹의 소비자를 비교하여 가능한 의사 결정 요소를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-108">For example, you might compare different groups of consumers to determine possible decision-making factors.</span></span>  
  
## <a name="using-the-analyze-key-influencers-tool"></a><span data-ttu-id="b1209-109">주요 영향 요인 분석 도구 사용</span><span class="sxs-lookup"><span data-stu-id="b1209-109">Using the Analyze Key Influencers Tool</span></span>  
  
1.  <span data-ttu-id="b1209-110">Excel 데이터 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-110">Open an Excel data table.</span></span>  
  
2.  <span data-ttu-id="b1209-111">**테이블 도구**의 **분석** 리본에서 주요 영향 요인 분석을 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="b1209-111">In **Table Tools**, on the **Analyze** ribbon, click **Analyze Key Influencers.**</span></span>  
  
3.  <span data-ttu-id="b1209-112">분석 대상 열을 하나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-112">Select the single column that is the target of analysis.</span></span>  
  
4.  <span data-ttu-id="b1209-113">필요에 따라 **분석에 사용할 열 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-113">Optionally, click **Choose columns to be used for analysis**.</span></span> <span data-ttu-id="b1209-114">**고급 열 선택** 대화 상자에서 관련 데이터가 포함 될 가능성이 가장 높은 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-114">In the **Advanced Columns Selection** dialog box, choose the columns that are most likely to contain relevant data.</span></span> <span data-ttu-id="b1209-115">성능과 정확성을 향상시키려면 패턴 분석에 중요하지 않은 ID 또는 이름과 같은 열은 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-115">To improve performance and accuracy, deselect columns such as ID or name that are unimportant for pattern analysis.</span></span> <span data-ttu-id="b1209-116">**확인** 을 클릭 하 여 **고급 열 선택** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-116">Click **OK** to close the **Advanced Columns Selection** dialog box.</span></span>  
  
5.  <span data-ttu-id="b1209-117">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-117">Click **Run**.</span></span>  
  
     <span data-ttu-id="b1209-118">**주요 영향 요인 분석** 도구는 데이터에 대 한 분석을 수행 하 여 최적의 설정을 결정 하 고 모든 매개 변수를 자동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-118">The **Analyze Key Influencers** tool conducts an analysis of the data to determine the optimum settings, and sets all parameters automatically.</span></span>  
  
6.  <span data-ttu-id="b1209-119">패턴을 발견하지 못한 경우 마법사는 문제 설명이 포함된 새 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-119">If no patterns were detected, the wizard creates a new worksheet that contains a description of the problem.</span></span>  
  
7.  <span data-ttu-id="b1209-120">패턴을 발견할 경우 마법사가 해당 패턴을 보여 주는</span><span class="sxs-lookup"><span data-stu-id="b1209-120">If patterns are detected, the wizard creates a report on a new worksheet that shows the patterns.</span></span> <span data-ttu-id="b1209-121">보고서에는 \*\* \<column> 의 주요 영향 요인 \*\*이라는 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-121">The report is named **Key Influencers for \<column>**.</span></span> <span data-ttu-id="b1209-122">다음 절차에서 설명하는 대로 보고서를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-122">You can customize the report as described in the following procedure.</span></span>  
  
#### <a name="create-a-custom-report"></a><span data-ttu-id="b1209-123">사용자 지정 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="b1209-123">Create a custom report</span></span>  
  
1.  <span data-ttu-id="b1209-124">주요 영향 **요인을 기반으로** 하는 판별 대화 상자에서 **값 1** 및 **값 2** 드롭다운 목록에서 비교할 두 값을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-124">In the **Discrimination based on key influencers** dialog box, choose the two values that you want to compare by selecting them from the **Value 1** and **Value 2** dropdown lists.</span></span> <span data-ttu-id="b1209-125">예를 들어 구매자와 비구매자를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-125">For example, you might compare buyers to non-buyers.</span></span>  
  
2.  <span data-ttu-id="b1209-126">**보고서 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-126">Click **Add Report**.</span></span>  
  
     <span data-ttu-id="b1209-127">마법사는 새 워크시트를 만들고 각 주요 요인 비교 쌍에 대한 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-127">The wizard creates a new worksheet and adds a table for each pair of key factor comparisons.</span></span>  
  
3.  <span data-ttu-id="b1209-128">비교가 완료 되 면 **닫기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-128">When you are done making comparisons, click **Close**.</span></span>  
  
## <a name="understanding-the-key-influencers-report"></a><span data-ttu-id="b1209-129">주요 영향 요인 보고서 이해</span><span class="sxs-lookup"><span data-stu-id="b1209-129">Understanding the Key Influencers Report</span></span>  
 <span data-ttu-id="b1209-130">데이터 모델을 만든 후 **주요 영향 요인 분석** 도구는 주요 영향 요인을 탐색 하 고 비교 하는 데 도움이 되는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-130">After the data model has been created, the **Analyze Key Influencers** tool creates reports that help you explore and compare key influencers.</span></span>  
  
-   <span data-ttu-id="b1209-131">왼쪽의 보고서는 기본적으로 생성되며</span><span class="sxs-lookup"><span data-stu-id="b1209-131">The report on the left side is the one generated by default.</span></span> <span data-ttu-id="b1209-132">결과 열의 가장 강력한 예측 요인(종속 변수)을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-132">It shows the strongest predictors of the outcome column (the dependent variable).</span></span>  
  
-   <span data-ttu-id="b1209-133">오른쪽의 보고서는 선택 사항이며 두 가지 특정 결과 값을 비교하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-133">The report on the right side is optional, which you can create by comparing two specific outcome values.</span></span> <span data-ttu-id="b1209-134">이 보고서는 구매자와 비구매자를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-134">This report compares buyers and non-buyers.</span></span>  
  
-   <span data-ttu-id="b1209-135">만드는 보고서마다 새 워크시트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-135">Note that a new worksheet is added for each report that you create.</span></span> <span data-ttu-id="b1209-136">테이블을 만든 후 이동할 수 있습니다. 여기에서는 비교를 위해 나란히 배치했습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-136">You can move the tables after they are created; we placed them side by side for comparison.</span></span>  
  
 <span data-ttu-id="b1209-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span><span class="sxs-lookup"><span data-stu-id="b1209-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span></span>  
  
 <span data-ttu-id="b1209-138">**상대적 영향**</span><span class="sxs-lookup"><span data-stu-id="b1209-138">**Relative Impact**</span></span>  
 <span data-ttu-id="b1209-139">첫 번째 보고서의 음영 처리된 막대는 결과에 대한 이 특성의 연관성 강도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-139">The shaded bar in the first report indicates the strength of the association of this attribute with the outcome.</span></span>  
  
 <span data-ttu-id="b1209-140">막대의 길이는 해당 요인이 결과에 영향을 미칠 확률을 나타냅니다. 즉, 음영 처리된 막대의 길이가 길수록 연관성도 강해집니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-140">The length of the bar indicates the probability that the factor contributes to the outcome; therefore, the longer the shaded bar, the stronger the association.</span></span>  
  
 <span data-ttu-id="b1209-141">**유사성**</span><span class="sxs-lookup"><span data-stu-id="b1209-141">**Favors**</span></span>  
 <span data-ttu-id="b1209-142">두 번째 보고서에서 비교하는 대상 값은 두 열에 나열되며 관련 요인이 신뢰성의 내림차순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-142">In the second report, the target values that you compare are listed in two columns, with the related factors listed in order of descending confidence.</span></span>  
  
-   <span data-ttu-id="b1209-143">**파란색** 막대에는 "아니요" (= 구매 하지 않음) 결과에 영향을 주는 특성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-143">The **blue** bar shows attributes contributing to the outcome, "No" (=did not purchase).</span></span>  
  
-   <span data-ttu-id="b1209-144">**빨간색** 막대는 결과에 영향을 주는 특성을 표시 합니다. "예" (= 자전거 구매).</span><span class="sxs-lookup"><span data-stu-id="b1209-144">The **red** bar shows attributes contributing to the outcome, "Yes" (=purchased a bike).</span></span>  
  
 <span data-ttu-id="b1209-145">음영 처리된 막대의 색은 임의로 지정되므로</span><span class="sxs-lookup"><span data-stu-id="b1209-145">The colors in the shading bar are arbitrary.</span></span> <span data-ttu-id="b1209-146">Excel에서 테이블 디자인에 대한 옵션을 설정하여 색상을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-146">You can change these colors by setting the options for table design in Excel.</span></span>  
  
 <span data-ttu-id="b1209-147">두 값을 대조하는 보고서에서 두 번째 보고서는 대상 값에 미치는 영향에 따라 주요 영향 요인의 순위를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-147">In a report that contrasts two values, the second report ranks the key influencers by the amount of impact on the target values.</span></span>  
  
 <span data-ttu-id="b1209-148">모든 차트가 Excel 테이블을 기반으로 하기 때문에 필터링하고 정렬하여 특정 요인 또는 결과에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-148">Because all the charts are based on Excel tables, you can filter and sort to focus on specific factors or outcomes.</span></span>  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a><span data-ttu-id="b1209-149">주요 영향 요인 분석 도구에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="b1209-149">More About the Analyze Key Influencers Tool</span></span>  
 <span data-ttu-id="b1209-150">주요 영향 **요인 분석** 도구는 데이터를 분석 하는 경우 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-150">When the **Analyze Key Influencers** tool analyzes your data, it does the following:</span></span>  
  
-   <span data-ttu-id="b1209-151">데이터의 분포에 대한 주요 정보를 저장하는 데이터 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-151">Creates a data structure that stores key information about the distribution of your data.</span></span>  
  
-   <span data-ttu-id="b1209-152">Microsoft Naive Bayes 알고리즘을 사용하여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-152">Creates a model using the Microsoft Naïve Bayes algorithm.</span></span>  
  
-   <span data-ttu-id="b1209-153">각 데이터 열과 지정된 결과의 상관 관계를 나타내는 예측 인수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-153">Creates predictions that correlates each column of data with the specified outcome.</span></span>  
  
-   <span data-ttu-id="b1209-154">각 예측에 대한 신뢰성 점수를 사용하여 목표 결과를 도출하는 데 가장 큰 영향을 주는 요인을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-154">Uses the confidence score for each of the predictions to identify the factors that are the most influential in producing the targeted outcome.</span></span>  
  
-   <span data-ttu-id="b1209-155">신뢰성 점수를 기준으로 정렬된 주요 영향 요인을 설명하는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-155">Creates a report describing the key influencers, ordered by confidence scores.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="b1209-156">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b1209-156">Requirements</span></span>  
 <span data-ttu-id="b1209-157">대상 열에 연속 숫자 값이 포함된 경우 도구는 자동으로 숫자 값을 그룹으로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-157">If the target column contains continuous numeric values, the tool automatically segments the numeric values into groups.</span></span> <span data-ttu-id="b1209-158">이러한 그룹화는 특성이 비슷한 사례의 클러스터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-158">These groupings represent clusters of cases that have similar characteristics.</span></span> <span data-ttu-id="b1209-159">그러나 숫자 값은 사용자에게 친숙한 그룹으로 나눌 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-159">However, numeric values might not be divided into user-friendly groups.</span></span> <span data-ttu-id="b1209-160">예를 들어 보고서에는 "12.85701"과 같은 그룹화가 포함 되어 있을 수 있습니다 \< . 반면 보고서 사용자는 일반적으로 10-19, 20-29 등과 같이 정수를 사용 하는 그룹화를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-160">For example, the report might contain a grouping such as "\<12.85701", whereas report users typically like to see groupings that use whole numbers, such as 10-19, 20-29, and so on.</span></span>  
  
 <span data-ttu-id="b1209-161">숫자 데이터를 다른 방식으로 그룹화하려면 분석을 만들기 전에 지정한 방식으로 데이터를 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-161">If you want to group numeric data in a different way, you must segment the data the way you want before creating the analysis.</span></span> <span data-ttu-id="b1209-162">예를 들어 Excel 용 데이터 마이닝 클라이언트의 [레이블 재지정](relabel-sql-server-data-mining-add-ins.md) 도구를 사용 하 여 별도의 열에 새 그룹화 레이블을 만든 다음 분석에 해당 하는 새 열만을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-162">For example, you can use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool in the Data Mining Client for Excel to create a new grouping label in a separate column, and then use only that new column in analysis.</span></span>  
  
### <a name="related-tools"></a><span data-ttu-id="b1209-163">관련 도구</span><span class="sxs-lookup"><span data-stu-id="b1209-163">Related Tools</span></span>  
 <span data-ttu-id="b1209-164">데이터 **마이닝 리본은** 데이터 마이닝 모델을 사용자 지정 하는 기능을 포함 하 여 고급 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-164">The **Data Mining** ribbon provides more advanced tools, including the ability to customize data mining models</span></span>  
  
 <span data-ttu-id="b1209-165">**주요 영향 요인 분석** 도구를 사용 하 여 모델을 저장 하는 경우 데이터 마이닝 클라이언트를 사용 하 여 모델을 찾아보고 관계를 자세히 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-165">If you save your model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="b1209-166">자세한 내용은 [Excel에서 모델 찾아보기 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1209-166">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span> <span data-ttu-id="b1209-167">Microsoft Office Visio로도 클러스터 또는 종속성 네트워크로 관계를 보여 주는 차트 및 다이어그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-167">You can also use Microsoft Office Visio to create charts and diagrams that display the relationships as cluster or as dependency networks.</span></span> <span data-ttu-id="b1209-168">자세한 내용은 [데이터 마이닝 추가&#41;기능을 SQL Server &#40;Visio 데이터 마이닝 다이어그램 문제 해결 ](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1209-168">For more information, see [Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1209-169">워크시트를 닫거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버 연결을 종료하면 테이블 분석 도구를 사용할 때 만든 모델이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-169">The models that are created when you use the Table Analysis Tools are deleted when you close your worksheet or terminate the connection with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="b1209-170">따라서 Analysis Services 서버에 연결되어 있는 동안에만 모델을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-170">Therefore, you can only browse the models as long as the connection remains open.</span></span> <span data-ttu-id="b1209-171">연결을 종료하거나 워크시트를 닫으면 Visio에서 모델을 렌더링할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1209-171">You cannot render the models in Visio if you close the connection or close the worksheet.</span></span>  
  
 <span data-ttu-id="b1209-172">**주요 영향 요인 분석** 도구에서 사용 하는 알고리즘에 대 한 자세한 내용은 SQL Server 온라인 설명서의 "Microsoft Naive Bayes 알고리즘"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1209-172">For more information about the algorithm used by the **Analyze Key Influencers** tool, see "Microsoft Naïve Bayes Algorithm" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1209-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1209-173">See Also</span></span>  
 <span data-ttu-id="b1209-174">[Excel 용 테이블 분석 도구](table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b1209-174">[Table Analysis Tools for Excel](table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="b1209-175">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="b1209-175">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
