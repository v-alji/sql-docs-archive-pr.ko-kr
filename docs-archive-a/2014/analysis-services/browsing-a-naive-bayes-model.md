---
title: Naive Bayes 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3b0d18cd74e71f1ef18bffd6b0998e0b326e887a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648106"
---
# <a name="browsing-a-naive-bayes-model"></a><span data-ttu-id="f0e19-102">Naive Bayes 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f0e19-102">Browsing a Naive Bayes Model</span></span>
  <span data-ttu-id="f0e19-103">**찾아보기**를 사용 하 여 naive Bayes 모델을 열면 4 개의 창이 있는 대화형 뷰어에 모델이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-103">When you open a Naïve Bayes model using **Browse**, the model is displayed in an interactive viewer with four different panes.</span></span> <span data-ttu-id="f0e19-104">이 뷰어를 사용하여 상관 관계를 탐색하고 모델 및 기본 데이터에 대한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-104">Use the viewer to explore correlations, and get information about the model and the underlying data.</span></span>  
  
-   [<span data-ttu-id="f0e19-105">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="f0e19-105">Dependency Network</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="f0e19-106">특성 프로필</span><span class="sxs-lookup"><span data-stu-id="f0e19-106">Attribute Profiles</span></span>](#bkmk_AttProf)  
  
-   [<span data-ttu-id="f0e19-107">특성 특징</span><span class="sxs-lookup"><span data-stu-id="f0e19-107">Attribute Characteristics</span></span>](#bkmk_AttChar)  
  
-   [<span data-ttu-id="f0e19-108">특성 판별</span><span class="sxs-lookup"><span data-stu-id="f0e19-108">Attribute Discrimination</span></span>](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="f0e19-109">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="f0e19-109">Explore the Model</span></span>  
 <span data-ttu-id="f0e19-110">뷰어는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 모델에서 발견된 입력 특성과 출력 특성(입력과 종속 변수) 간의 상호 작용을 탐색하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-110">The purpose of the viewer is to help you explore the interaction between input and output attributes (inputs and dependent variables) that were discovered by the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes model.</span></span>  
  
 <span data-ttu-id="f0e19-111">Naive Bayes viewer를 사용 하 여 실험 하려는 경우 데이터 마이닝 리본에서 [&#41;Excel 용 데이터 마이닝 추가 기능 마법사 &#40;분류 마법사](classify-wizard-data-mining-add-ins-for-excel.md) 를 사용 하 고 **고급** 옵션을 클릭 한 다음 naive Bayes 알고리즘을 사용 하도록 알고리즘을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-111">If you want to experiment with the Naïve Bayes viewer, use the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard in the Data Mining ribbon, click the **Advanced** option, and change the algorithm to use the Naïve Bayes algorithm</span></span>  
  
 <span data-ttu-id="f0e19-112">이러한 예에서는 샘플 통합 문서에서 원본 데이터를 사용 하 고 **연간 소득**열을 **매우 낮은** 수준에서 **매우 높은 수준**으로 5 개의 수입 그룹으로 그룹화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-112">For these examples, we used the Source data in the sample workbook, and grouped the column, **Yearly Income**, into five income groups, from **Very Low** to **Very High**.</span></span> <span data-ttu-id="f0e19-113">그런 다음 Naïve Bayes 모델을 통해 각 소득 범주와 상관 관계가 있는 요인을 분석했습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-113">The Naïve Bayes model then analyzed the factors correlated with each income category.</span></span>  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a><span data-ttu-id="f0e19-114">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="f0e19-114">Dependency Network</span></span>  
 <span data-ttu-id="f0e19-115">사용할 첫 번째 창은 **종속성 네트워크**입니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-115">The first window you'll use is the **Dependency Network**.</span></span> <span data-ttu-id="f0e19-116">이 창에서는 선택한 결과와 밀접한 상관 관계가 있는 입력을 한눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-116">It shows you at a glance which inputs are closely correlated to the selected outcome.</span></span>  
  
 <span data-ttu-id="f0e19-117">![Naive Bayes 뷰어의 종속성 네트워크](media/dm13-nb.gif "Naive Bayes 뷰어의 종속성 네트워크")</span><span class="sxs-lookup"><span data-stu-id="f0e19-117">![dependency network in Naive Bayes viewer](media/dm13-nb.gif "dependency network in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="f0e19-118">종속성 네트워크 탐색</span><span class="sxs-lookup"><span data-stu-id="f0e19-118">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="f0e19-119">먼저 그래프에서 노드로 표시 되는 대상 결과 **연간 수입**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-119">First, click the target outcome, **Yearly Income**, which is represented as a node in the graph.</span></span>  
  
     <span data-ttu-id="f0e19-120">대상 변수 주위의 강조 표시된 노드는 이 결과와 통계적으로 상관 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-120">The highlighted nodes surrounding the target variable are those that are statistically correlated with this outcome.</span></span> <span data-ttu-id="f0e19-121">뷰어의 아래쪽에 있는 범례를 사용하여 관계의 특성을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-121">Use the legend at the bottom of the viewer to understand the nature of the relationship.</span></span>  
  
2.  <span data-ttu-id="f0e19-122">뷰어 왼쪽에서 슬라이더를 클릭하여 아래로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-122">Click the slider at the left of the viewer and drag it downward.</span></span>  
  
     <span data-ttu-id="f0e19-123">이 컨트롤은 종속성 수준에 따라 독립 변수를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-123">This control filters the independent variables, based on the strengths of the dependencies.</span></span> <span data-ttu-id="f0e19-124">슬라이더를 아래로 끌면 가장 강력한 링크만 그래프에 남습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-124">When you drag the slider down, only the strongest links remain in the graph.</span></span>  
  
3.  <span data-ttu-id="f0e19-125">그래프를 필터링 한 후 **그래프 뷰 복사**단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-125">After you have filtered the graph, click the button, **Copy Graph View**.</span></span> <span data-ttu-id="f0e19-126">그런 다음 Excel에서 워크시트를 선택하고 Ctrl+V를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-126">Then select a worksheet in Excel, and press Ctrl+V.</span></span>  
  
     <span data-ttu-id="f0e19-127">필터와 강조 표시를 비롯하여 선택한 뷰가 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-127">This option copies the view that you have selected, including filters and highlighting.</span></span>  
  
 [<span data-ttu-id="f0e19-128">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="f0e19-128">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a> <span data-ttu-id="f0e19-129">특성 프로필</span><span class="sxs-lookup"><span data-stu-id="f0e19-129">Attribute Profiles</span></span>  
 <span data-ttu-id="f0e19-130">**특성 프로필** 창에서는 다른 모든 변수가 개별 결과와 관련 되는 방식을 시각적으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-130">The **Attribute Profiles** windows gives you a visual indication of how all other variables are related to the individual outcomes.</span></span>  
  
##### <a name="explore-the-profiles"></a><span data-ttu-id="f0e19-131">프로필 탐색</span><span class="sxs-lookup"><span data-stu-id="f0e19-131">Explore the profiles</span></span>  
  
1.  <span data-ttu-id="f0e19-132">결과를 보다 쉽게 비교할 수 있도록 일부 값을 숨기려면 열 머리글을 클릭하고 다른 열 아래로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-132">To hide some values so that you can more easily compare outcomes, click the column heading and drag it under another column.</span></span>  
  
     <span data-ttu-id="f0e19-133">![Naive Bayes 뷰어의 특성 프로필](media/dm13-nb-attprof.gif "Naive Bayes 뷰어의 특성 프로필")</span><span class="sxs-lookup"><span data-stu-id="f0e19-133">![attribute profiles in Naive Bayes viewer](media/dm13-nb-attprof.gif "attribute profiles in Naive Bayes viewer")</span></span>  
  
2.  <span data-ttu-id="f0e19-134">임의의 셀을 클릭 하 여 **마이닝 범례의**값 분포를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-134">Click in any cell to view the distribution of values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="f0e19-135">다른 결과와 연결된 특성이 시각적으로 표시되기 때문에 소득의 지역별 분포와 같은 흥미로운 상관 관계를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-135">Because the attributes associated with different outcomes are displayed visually, it is easy to spot interesting correlations, such as how incomes are distributed by region.</span></span>  
  
3.  <span data-ttu-id="f0e19-136">이 보기의 기반이 되는 데이터를 가져오려면 **Excel로 복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-136">To obtain the data underlying this view, click **Copy to Excel**.</span></span> <span data-ttu-id="f0e19-137">개별 특성 및 결과 간의 상관 관계를 보여 주는 테이블이 새 워크시트에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-137">A table is generated in a new worksheet that shows the correlations among individual attributes and outcomes.</span></span> <span data-ttu-id="f0e19-138">이 Excel 테이블에서 열을 쉽게 숨기거나 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-138">In this Excel table you can easily hide or filter columns.</span></span>  
  
 [<span data-ttu-id="f0e19-139">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="f0e19-139">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a> <span data-ttu-id="f0e19-140">특성 특징</span><span class="sxs-lookup"><span data-stu-id="f0e19-140">Attribute Characteristics</span></span>  
 <span data-ttu-id="f0e19-141">**특성 특징** 보기는 특정 결과 변수와 영향 요인을 자세히 검사 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-141">The **Attribute Characteristics** view is useful for in-depth examination of a particular outcome variable and the contributing factors.</span></span>  
  
 <span data-ttu-id="f0e19-142">![Naive Bayes 뷰어의 특성 특징](media/dm13-nb-viewer.gif "Naive Bayes 뷰어의 특성 특징")</span><span class="sxs-lookup"><span data-stu-id="f0e19-142">![attribute characteristics in Naive Bayes viewer](media/dm13-nb-viewer.gif "attribute characteristics in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-attribute-characteristics"></a><span data-ttu-id="f0e19-143">특성 특징 탐색</span><span class="sxs-lookup"><span data-stu-id="f0e19-143">Explore the attribute characteristics</span></span>  
  
1.  <span data-ttu-id="f0e19-144">**값** 을 클릭 하 고 **값**에서 항목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-144">Click **Value** and select an item from the **Value**.</span></span>  
  
     <span data-ttu-id="f0e19-145">대상 결과를 선택하면 그래프가 업데이트되어 결과와 가장 밀접하게 관련된 요인이 중요도순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-145">As you select a target outcome, the graph updates to show the factors that are most strongly associated with the outcome, sorted by importance.</span></span>  
  
     <span data-ttu-id="f0e19-146">[주요 영향 요인 분석 &#40;테이블 분석 도구&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) 옵션을 사용 하 여 모델을 만드는 경우 예측 가능한 특성이 두 개 이상 포함 된 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-146">Note that if you create a model using the [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) option, you can create models that have more than one predictable attribute.</span></span> <span data-ttu-id="f0e19-147">그러나 데이터 마이닝 추가 기능의 다른 모든 마법사는 예측 가능한 특성을 하나로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-147">However, all other wizards in the Data Mining add-ins limit you to one predictable attribute.</span></span>  
  
2.  <span data-ttu-id="f0e19-148">**Excel로 복사** 를 클릭 하 여 새 워크시트에 선택한 대상 결과와 관련 된 모든 특성의 점수를 나열 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-148">Click **Copy to Excel** to create a table, in a new worksheet, listing the scores for all attributes that are related to the selected target outcome.</span></span>  
  
 [<span data-ttu-id="f0e19-149">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="f0e19-149">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a> <span data-ttu-id="f0e19-150">특성 판별</span><span class="sxs-lookup"><span data-stu-id="f0e19-150">Attribute Discrimination</span></span>  
 <span data-ttu-id="f0e19-151">**특성 판별** 뷰를 사용 하 여 두 결과 또는 한 결과와 다른 결과를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-151">The **Attribute Discrimination** view helps compare two outcomes, or one outcome vs. all other outcomes.</span></span>  
  
 <span data-ttu-id="f0e19-152">![Naive Bayes 뷰어의 특성 판별](media/dm13-nb-attdisc.gif "Naive Bayes 뷰어의 특성 판별")</span><span class="sxs-lookup"><span data-stu-id="f0e19-152">![attribute discrimination in Naive Bayes viewer](media/dm13-nb-attdisc.gif "attribute discrimination in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-attribute-discrimination"></a><span data-ttu-id="f0e19-153">특성 판별 탐색</span><span class="sxs-lookup"><span data-stu-id="f0e19-153">Explore attribute discrimination</span></span>  
  
1.  <span data-ttu-id="f0e19-154">**값 1** 및 **값 2**컨트롤을 사용 하 여 비교할 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-154">Use the controls, **Value 1** and **Value 2**, to select the outcomes that you want to compare.</span></span>  
  
     <span data-ttu-id="f0e19-155">예를 들어이 모델에서는 낮은 소득 그룹에 몇 가지 흥미로운 특성이 있으므로 첫 번째 드롭다운 목록에서 최저 소득 그룹을 선택 하 고 두 번째 드롭다운 목록에서 **다른 모든 상태** 를 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-155">For example, in this model there were some interesting attributes in the low income group, so we chose the lowest income group in the first dropdown list, and chose **All other states** in the second dropdown list.</span></span>  
  
     <span data-ttu-id="f0e19-156">특성은 학습 데이터를 기반으로 계산된 중요도순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-156">The attributes are sorted by order of importance (calculated based on the training data).</span></span> <span data-ttu-id="f0e19-157">따라서 직업은 소득과 가장 밀접한 상관 관계가 있는 요인입니다(적어도 이 대상 그룹의 경우).</span><span class="sxs-lookup"><span data-stu-id="f0e19-157">Therefore, occupation is the factor most closely correlated with income (for this target group, at least),</span></span>  
  
     <span data-ttu-id="f0e19-158">정확한 수치를 보려면 색이 지정 된 막대를 클릭 하 고 **마이닝 범례**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-158">To see the exact figures, click the colored bar and view the **Mining Legend**.</span></span>  
  
2.  <span data-ttu-id="f0e19-159">낮은 소득은 유럽 지역과도 상관 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-159">Note that lower incomes are also correlated with the Europe region.</span></span>  
  
     <span data-ttu-id="f0e19-160">Naïve Bayes 모델은 드릴다운을 지원하지 않습니다. 이 결과 그룹과 관련된 사례를 조사하려면 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e19-160">The Naïve Bayes model does not support drilldown; however, if you wanted to investigate the cases associated with this outcome group, you could use a query.</span></span> <span data-ttu-id="f0e19-161">이러한 유형의 모델에 대 한 쿼리에 대 한 자세한 내용은 [Naive Bayes Model 쿼리 예제](data-mining/naive-bayes-model-query-examples.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0e19-161">For information about queries on this type of model, see [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="f0e19-162">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="f0e19-162">Back To Top</span></span>](#BKMK_Tabs)  
  
## <a name="see-also"></a><span data-ttu-id="f0e19-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0e19-163">See Also</span></span>  
 [<span data-ttu-id="f0e19-164">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="f0e19-164">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
