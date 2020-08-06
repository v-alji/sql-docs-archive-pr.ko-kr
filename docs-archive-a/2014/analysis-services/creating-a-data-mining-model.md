---
title: 데이터 마이닝 모델 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e27739d3733c0b48dc6cff3e83e01f9cb12bce7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651941"
---
# <a name="creating-a-data-mining-model"></a><span data-ttu-id="b1502-102">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="b1502-102">Creating a Data Mining Model</span></span>
  <span data-ttu-id="b1502-103">데이터 모델링은 데이터에 *알고리즘* 을 적용 하 여 패턴 및 추세를 작성 하는 데이터 마이닝 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-103">Data modeling is the step of data mining where you build patterns and trends by applying *algorithms* to data.</span></span> <span data-ttu-id="b1502-104">이러한 패턴을 사용하여 나중에 분석하거나 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-104">Later you can use those patterns for analysis, or to make predictions.</span></span>  
  
 <span data-ttu-id="b1502-105">Office용 데이터 마이닝 추가 기능은 모델을 간단히 만들 수 있는 마법사를 통해 데이터 마이닝을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-105">The Data Mining Add-ins for Office support data mining through wizards that make it easy to create models.</span></span> <span data-ttu-id="b1502-106">이 마법사는 데이터를 분석하고 상관 관계를 식별하며 모든 변수의 통계적 의미를 계산하고 자동으로 최상의 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-106">The wizards analyze the data, identify correlations, compute statistical significance of all variables, and automatically select the best model.</span></span>  
  
 <span data-ttu-id="b1502-107">이 기능은 및에서 제공 하는 데이터 마이닝 도구 만큼 강력 하기는 하지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 마법사와 친숙 한 Excel 인터페이스를 함께 사용 하면 데이터 마이닝을 쉽게 만들고 수정 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-107">Although this functionality is every bit as powerful as the data mining tools provided by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the combination of wizards and the familiar Excel interface makes it easy to create, modify, and use data mining.</span></span>  
  
## <a name="advanced-data-mining"></a><span data-ttu-id="b1502-108">고급(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-108">Advanced (Data Mining)</span></span>  
 <span data-ttu-id="b1502-109">고급 마법사를 사용 하면의 데이터 마이닝 알고리즘 중 하나를 사용 하 여 Excel에 저장 된 데이터를 기반으로 새 데이터 마이닝 모델을 만들 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1502-109">The Advanced wizards let you create new data mining models, based on data stored in Excel, by using one of the data mining algorithms in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="create-mining-structure"></a><span data-ttu-id="b1502-110">마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="b1502-110">Create Mining Structure</span></span>  
 <span data-ttu-id="b1502-111">마이닝 구조 만들기 마법사를 사용하면 여러 마이닝 모델의 기반으로 사용할 수 있는 새로운 데이터 마이닝 구조를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-111">The Create Mining Structure wizard helps you build a new data mining structure, which you can use as the basis for multiple mining models.</span></span> <span data-ttu-id="b1502-112">마법사에는 테스트 집합으로 사용할 데이터 부분을 따로 지정할 수 있는 옵션이 있으므로 일관된 테스트 표준에 따라 같은 데이터를 사용하는 모든 모델을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-112">The wizard gives you the option to set aside a portion of the data to use as a testing set, so that you can evaluate all models that use the same data according to a consistent testing standard.</span></span>  
  
 [<span data-ttu-id="b1502-113">데이터 마이닝 추가 기능을 SQL Server &#40;마이닝 구조를 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-113">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a><span data-ttu-id="b1502-114">구조에 모델 추가</span><span class="sxs-lookup"><span data-stu-id="b1502-114">Add Model to Structure</span></span>  
 <span data-ttu-id="b1502-115">구조에 모델 추가 마법사를 사용하면 기존 데이터 마이닝 구조를 선택하여 이 구조에 대한 새 데이터 마이닝 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-115">The Add Model to Structure wizard lets you choose an existing data mining structure and create a new data mining model for it.</span></span> <span data-ttu-id="b1502-116">매개 변수를 변경하고 서로 다른 데이터 마이닝 알고리즘을 선택하여 다양한 마이닝 모델을 구조에 추가하고 출력을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-116">You can add multiple mining models to a structure, changing the parameters or choosing different data mining algorithms, and customize the output.</span></span>  
  
 [<span data-ttu-id="b1502-117">Excel 용 데이터 마이닝 추가 기능 &#40;구조에 모델 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-117">Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;</span></span>](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a><span data-ttu-id="b1502-118">주요 영향 요인 분석(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-118">Analyze Key Influencers (Analyze)</span></span>  
 <span data-ttu-id="b1502-119">관심 있는 열 또는 출력 값을 선택한 다음 알고리즘으로 모든 입력 데이터를 분석하여 대상에 가장 많은 영향을 미친 요소를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-119">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="b1502-120">필요한 경우 두 값을 비교하는 보고서를 만들어 영향 요인이 어떻게 변경되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-120">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="b1502-121">**주요 영향 요인 분석** 도구는 Microsoft naive Bayes 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-121">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-122">Excel 용 테이블 분석 도구 &#40;주요 영향 요인 분석&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-122">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a><span data-ttu-id="b1502-123">연결(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-123">Associate (Data Mining)</span></span>  
 <span data-ttu-id="b1502-124">**연결** 마법사는 여러 트랜잭션에 표시 되는 항목 간의 연결을 검색 하는 연결 모델을 작성 합니다 (예: 시장 바구니 분석).</span><span class="sxs-lookup"><span data-stu-id="b1502-124">The **Associate** wizard builds an association model that detects associations between items that appear in multiple transactions: for example, in market basket analysis.</span></span>  
  
 [<span data-ttu-id="b1502-125">Excel 용 데이터 마이닝 클라이언트 &#40;마법사 연결&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-125">Associate Wizard &#40;Data Mining Client for Excel&#41;</span></span>](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a><span data-ttu-id="b1502-126">분류(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-126">Classify (Data Mining)</span></span>  
 <span data-ttu-id="b1502-127">**분류** 마법사는 대상 결과에 적용 된 요인을 분석 하는 분류 모델을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-127">The  **Classify** wizard builds a classification model that analyzes the factors that contributed to a target outcome.</span></span> <span data-ttu-id="b1502-128">이 마법사에서는 의사 결정 트리, Naïve Bayes, 신경망을 포함하여 여러 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-128">You can use multiple algorithms with this wizard, including Decision Trees, Naïve Bayes, and Neural Networks.</span></span>  
  
 [<span data-ttu-id="b1502-129">분류 마법사 &#40;Excel 용 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-129">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a><span data-ttu-id="b1502-130">클러스터(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-130">Cluster (Data Mining)</span></span>  
 <span data-ttu-id="b1502-131">**클러스터** 마법사는 비슷한 특성을 공유 하는 행 그룹을 검색 하는 클러스터링 모델을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-131">The **Cluster** wizard builds a clustering model that detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="b1502-132">클러스터링 (종종 *조각화*라고도 함)은 패턴 및 새 데이터의 그룹화를 이해 하려고 할 때 매우 유용한 자율 학습 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-132">Clustering (sometimes called *segmentation*) is an unsupervised learning technique that is very useful when trying to understand patterns and groupings in new data.</span></span>  
  
 <span data-ttu-id="b1502-133">Microsoft 클러스터링 알고리즘은 K-means와 EM(Expectation maximization) 클러스터링의 다양한 변형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-133">The Microsoft Clustering algorithm supports several varieties of both K-means and Expectation maximization (EM) clustering</span></span>  
  
 <span data-ttu-id="b1502-134">[클러스터 마법사는 Excel 용 데이터 마이닝 추가 기능&#41;를 &#40;](cluster-wizard-data-mining-add-ins-for-excel.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-134">[Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="detect-categories-analyze"></a><span data-ttu-id="b1502-135">범주 검색(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-135">Detect Categories (Analyze)</span></span>  
 <span data-ttu-id="b1502-136">**범주 검색** 도구를 사용 하면 데이터 집합을 추가 하 고 클러스터링을 적용 하 여 데이터 그룹화를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-136">The **Detect Categories** tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="b1502-137">유사성을 찾고 추가 분석을 위해 그룹을 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-137">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="b1502-138">**범주 검색** 도구는 Microsoft 클러스터링 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-138">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-139">Excel 용 테이블 분석 도구 &#40;범주 검색&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-139">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a><span data-ttu-id="b1502-140">예상(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-140">Estimate (Data Mining)</span></span>  
 <span data-ttu-id="b1502-141">추정 마법사는 데이터 패턴을 추출하고 이 패턴을 사용하여 연속 숫자, 날짜 또는 시간 값을 예측하는 추정 모델을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-141">The Estimate wizard builds an estimation model that extracts data patterns and uses the patterns to predict continuous numeric, date, or time values.</span></span> <span data-ttu-id="b1502-142">이 마법사는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-142">It uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-143">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-143">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a><span data-ttu-id="b1502-144">예제로 채우기(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-144">Fill From Example (Analyze)</span></span>  
 <span data-ttu-id="b1502-145">**예제로 채우기** 도구를 사용 하 여 누락 된 값을 돌립니다 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-145">The **Fill From Example** tool helps you impute missing values.</span></span> <span data-ttu-id="b1502-146">사용자는 어떤 값이 누락되었는지에 대한 예를 제공하고 해당 도구에서 표의 모든 데이터를 기반으로 패턴을 작성한 다음 데이터의 패턴을 기반으로 한 새 값을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-146">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="b1502-147">**예제로 채우기** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-147">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-148">Excel 용 테이블 분석 도구 &#40;예제로 채우기&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-148">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a><span data-ttu-id="b1502-149">예측(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-149">Forecast (Analyze)</span></span>  
 <span data-ttu-id="b1502-150">**예측** 도구는 시간이 지남에 따라 변경 되는 데이터를 사용 하 여 미래 값을 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-150">The **Forecast** tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="b1502-151">**예측** 도구는 Microsoft 시계열 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-151">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-152">Excel 용 예측 &#40;테이블 분석 도구&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-152">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a><span data-ttu-id="b1502-153">예측(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b1502-153">Forecast (Data Mining)</span></span>  
 <span data-ttu-id="b1502-154">**예측** 마법사는 일련의 셀에서 패턴을 검색 한 다음 추가 값을 예측 하는 예측 모델을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-154">The **Forecast** wizard builds a forecasting model that detects patterns in a series of cells, and then forecasts additional values.</span></span>  
  
 [<span data-ttu-id="b1502-155">Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-155">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a><span data-ttu-id="b1502-156">예외 강조 표시(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-156">Highlight Exceptions (Analyze)</span></span>  
 <span data-ttu-id="b1502-157">**예외 강조 표시** 도구는 데이터 테이블의 패턴을 분석 하 고 패턴에 맞지 않는 행과 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-157">The **Highlight Exceptions** tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="b1502-158">그런 다음 모델을 검토하여 수정한 후 다시 실행하거나 향후 작업을 위해 값에 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-158">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="b1502-159">**예외 강조 표시** 도구는 Microsoft 클러스터링 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-159">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-160">Excel 용 테이블 분석 도구 &#40;예외 강조 표시&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-160">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a><span data-ttu-id="b1502-161">예측 계산기(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-161">Prediction Calculator (Analyze)</span></span>  
 <span data-ttu-id="b1502-162">이 도구는 대상 결과를 이끄는 요인을 분석하는 모델을 만든 다음 해당 패턴에서 유추한 기준을 기반으로 새로운 입력 결과를 예측합니다. 또한 새로운 입력 사항을 손쉽게 평가할 수 있는 대화형 의사 결정 워크시트도 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-162">This tool creates a model that analyzes the factors leading to target outcomes, and then predicts a result for any new input, based on criteria derived from these patterns It also generates an interactive decision making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="b1502-163">오프라인에서 사용할 수 있는 평가 워크시트 인쇄 버전도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-163">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="b1502-164">**예측 계산기** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-164">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-165">Excel 용 테이블 분석 도구&#41;예측 계산기 &#40;</span><span class="sxs-lookup"><span data-stu-id="b1502-165">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a><span data-ttu-id="b1502-166">시나리오: 목표 검색 (분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-166">Scenario: Goal Seek (Analyze)</span></span>  
 <span data-ttu-id="b1502-167">**목표 검색** 도구에서 대상 값을 지정 하면이 도구는 해당 대상을 충족 하기 위해 변경 해야 하는 기본 요소를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-167">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="b1502-168">예를 들어, 전화 만족도를 20% 증가시켜야 하는 경우 해당 모델을 통해 목표를 달성하기 위해 변경해야 하는 요소를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-168">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="b1502-169">**목표 검색** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-169">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="b1502-170">자세히</span><span class="sxs-lookup"><span data-stu-id="b1502-170">details</span></span>  
  
 [<span data-ttu-id="b1502-171">Excel 용 테이블 분석 도구 &#40;목표 검색 시나리오&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-171">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a><span data-ttu-id="b1502-172">시나리오: 가상 시나리오 (분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-172">Scenario: What-If Scenario (Analyze)</span></span>  
 <span data-ttu-id="b1502-173">**가상 분석** 도구는 **목표 검색** 도구를 보완 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-173">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="b1502-174">이 도구를 사용하여 변경하려는 값을 입력하면 모델에서 해당 변경을 통해 원하는 결과를 얻기에 충분한지 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-174">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="b1502-175">예를 들어, 모델을 통해 전화 상담원을 한 명 더 추가하면 해당 시점에서 고객 만족도를 높일 수 있는지 유추할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-175">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="b1502-176">**가상** 도구는 Microsoft 로지스틱 회귀 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-176">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-177">Excel 용 테이블 분석 도구 &#40;가상 시나리오&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-177">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a><span data-ttu-id="b1502-178">시장 바구니 분석(분석)</span><span class="sxs-lookup"><span data-stu-id="b1502-178">Shopping Basket Analysis (Analyze)</span></span>  
 <span data-ttu-id="b1502-179">시장 **바구니 분석** 도구는 자주 함께 구매 하는 제품 그룹을 만들어 교차 판매 또는 업 판매에 사용할 수 있는 패턴을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-179">The **Shopping Basket Analysis** tool creates groups of products that are frequently purchased together, to identify patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="b1502-180">또한 관련 제품 번들의 가격 및 비용을 기반으로 보고서를 생성하여 의사 결정을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-180">It also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="b1502-181">자주 함께 발생하는 이벤트, 진단 요소 또는 기타 일련의 잠재적 원인 및 결과에 대해서도 이 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-181">You can also use this tool for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="b1502-182">시장 **바구니 분석** 도구는 Microsoft 연결 알고리즘을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1502-182">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
 [<span data-ttu-id="b1502-183">시장 바구니 분석 &#40;Table AnalysisTools for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-183">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1502-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1502-184">See Also</span></span>  
 <span data-ttu-id="b1502-185">[데이터 탐색 및 정리](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="b1502-185">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="b1502-186">[Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b1502-186">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="b1502-187">Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="b1502-187">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
