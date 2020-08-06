---
title: 예측 마법사 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace9fa3a62690061677312d4f7dbb6b8a1d0ea5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734563"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="517e9-102">추정 마법사(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="517e9-102">Estimate Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="517e9-103">![데이터 마이닝 리본의 추정 마법사](media/dmc-estimate.gif "데이터 마이닝 리본의 추정 마법사")</span><span class="sxs-lookup"><span data-stu-id="517e9-103">![Estimate wizard in Data Mining ribbon](media/dmc-estimate.gif "Estimate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="517e9-104">**추정** 마법사로 추정 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-104">The **Estimate** wizard helps you create an estimation model.</span></span> <span data-ttu-id="517e9-105">추정 모델은 데이터에서 패턴을 추출하고 패턴을 사용하여 결과에 영향을 주는 요인을 예측합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-105">An estimation model extracts patterns from data and uses the patterns to predict the factors that affect outcomes.</span></span>  
  
 <span data-ttu-id="517e9-106">추정은 숫자 결과를 예측하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-106">Estimation is used for predicting numeric outcomes.</span></span> <span data-ttu-id="517e9-107">예를 들어 대상 열에 백분율로 표현된 학교 졸업률이 포함되어 있는 경우 학교별 학생 수, 학생과 교사 비율, 교사 수 등 졸업률을 높이거나 낮출 수 있는 요인을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-107">For example, if your target column contains graduation rates for schools, with graduation rates expressed as percentages, you could analyze factors that potentially increase or decrease graduation rates, such as the number of students per school, the student-teacher ratio, and the number of teachers.</span></span>  
  
## <a name="using-the-estimate-data-wizard"></a><span data-ttu-id="517e9-108">데이터 추정 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="517e9-108">Using the Estimate Data Wizard</span></span>  
  
1.  <span data-ttu-id="517e9-109">**데이터 마이닝** 리본에서 **추정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-109">On the **Data Mining** ribbon, click **Estimate**.</span></span>  
  
2.  <span data-ttu-id="517e9-110">**원본 데이터 선택** 대화 상자에서 사용할 원본 데이터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-110">In the **Select Source Data** dialog box, select the source data to use.</span></span> <span data-ttu-id="517e9-111">Excel **테이블**, Excel **데이터 범위**또는 **외부 데이터 원본**의 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-111">You can use data in an Excel **Table**, an Excel **Data Range**, or from an **External data source**.</span></span>  
  
     <span data-ttu-id="517e9-112">외부 데이터 원본을 사용할 경우에는 사용자 지정 뷰 또는 쿼리를 만들고 이를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-112">If you use an external data source, you can create custom views or queries and save them as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="517e9-113">**추정** 대화 상자에서 **분석할 열**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-113">In the **Estimation** dialog box, select the **Column to analyze**.</span></span>  
  
     <span data-ttu-id="517e9-114">대상 열에는 연속 숫자 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-114">The target column must contain continuous numeric data.</span></span>  
  
4.  <span data-ttu-id="517e9-115">**입력 열** 확인란을 선택하여 입력으로 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-115">Select columns to use as input by checking the **Input columns** checkbox.</span></span>  
  
     <span data-ttu-id="517e9-116">이러한 열은 패턴을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-116">These columns will be used to create the patterns.</span></span> <span data-ttu-id="517e9-117">ID 번호 또는 관련이 없는 데이터가 포함된 열과 같이 필요하지 않은 열은 분석에서 제외해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-117">You should eliminate from analysis any columns that are not likely to help, such as ID numbers, or columns that contain irrelevant data.</span></span>  
  
5.  <span data-ttu-id="517e9-118">**추정** 마법사는 데이터 집합에 가장 적합한 알고리즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-118">The **Estimate** wizard selects the optimum algorithm for your data set.</span></span> <span data-ttu-id="517e9-119">그러나 **매개 변수** 를 클릭하여 **알고리즘 매개 변수** 대화 상자를 열고 고급 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-119">However, you can click **Parameters** to open the **Algorithm Parameters** dialog box and set advanced options.</span></span>  
  
6.  <span data-ttu-id="517e9-120">데이터가 숫자이고 Microsoft 선형 회귀 방법을 사용할 수 있으면 **회귀 변수** 상자에서 예측 가능한 값과 상관될 수 있는 것으로 알려진(또는 그러한 가능성이 매우 높은) 숫자 열을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-120">If your data is numeric and you can use the Microsoft Linear Regression method, you can check the **Regressor** box for any numeric columns that you know (or strongly suspect) to be correlated with the predictable value.</span></span>  
  
     <span data-ttu-id="517e9-121">이 알고리즘은 그런 다음 해당 열의 값을 테스트해서 결과에 영향을 주는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-121">The algorithm will then test the values in that column to determine if they affect the outcomes.</span></span> <span data-ttu-id="517e9-122">확실하지 않으면 **제안** 을 클릭합니다. 그러면 알고리즘이 모든 열을 테스트하고 회귀 변수로 사용하기에 가장 적합한 값을 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-122">If you are unsure, click **Suggest** and the algorithm will test all column and automatically detect the best values to use as regressors.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="517e9-123">추정을 만들려면 회귀 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-123">A regressor is required to create an estimate.</span></span> <span data-ttu-id="517e9-124">데이터 초기 패스를 기반으로 마법사가 항상 최상의 회귀 변수를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-124">The wizard always recommends the best regressor, based on an initial pass over the data.</span></span> <span data-ttu-id="517e9-125">따라서 잘 모르는 경우에는 제안된 선택 항목을 받아들이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-125">Therefore, if you are not sure, it is best to accept the recommended selections.</span></span>  
  
7.  <span data-ttu-id="517e9-126">**학습 및 테스트 집합으로 데이터 분할** 페이지에서 테스트용 데이터 하위 집합을 만들지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-126">On the **Split data into training and testing sets** page, specify whether you want to create a small subset of the data for testing.</span></span>  
  
8.  <span data-ttu-id="517e9-127">**마침** 페이지에서 새 마이닝 구조 및 마이닝 모델의 이름을 지정하거나 기본으로 제공되는 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-127">On the **Finish** page, provide names for the new mining structure and mining mode, or accept the default names that are provided.</span></span>  
  
9. <span data-ttu-id="517e9-128">모델 사용 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-128">Set options for using the model.</span></span>  
  
    -   <span data-ttu-id="517e9-129">모델을 뷰어에서 바로 열려면 **찾아보기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-129">Select **Browse** to immediately open the model in a viewer.</span></span>  
  
         <span data-ttu-id="517e9-130">이 그래픽 뷰어에는 종속성 네트워크 그래프 및 알고리즘에서 생성된 의사 결정 트리가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-130">This graphical viewer displays a dependency network graph and the decision tree generated by the algorithm.</span></span> <span data-ttu-id="517e9-131">이 정보를 검토하면 추정 값에 영향을 주는 요인을 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-131">By exploring this information, you can better understand the factors that contribute to the estimated values.</span></span>  
  
    -   <span data-ttu-id="517e9-132">분석 사용자가 기본 데이터를 볼 수 있도록 하려면 **드릴스루 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-132">Select **Enable drillthrough** to let users of your analysis view the underlying data.</span></span>  
  
         <span data-ttu-id="517e9-133">이 옵션은 의사 결정 트리 또는 선형 회귀 알고리즘을 사용하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-133">This option is available only if you use the Decision Trees opr Linear Regression algorithms.</span></span>  
  
    -   <span data-ttu-id="517e9-134">**임시 모델 사용**.</span><span class="sxs-lookup"><span data-stu-id="517e9-134">**Use temporary model**.</span></span> <span data-ttu-id="517e9-135">이 옵션을 선택하면 모델이 서버에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-135">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="517e9-136">임시 모델은 Excel을 닫을 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-136">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-estimation-models"></a><span data-ttu-id="517e9-137">추정 모델에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="517e9-137">More About Estimation Models</span></span>  
 <span data-ttu-id="517e9-138">**추정** 마법사는 다음 알고리즘의 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-138">The **Estimate** wizard supports the use of any of the following algorithms:</span></span>  
  
-   <span data-ttu-id="517e9-139">Microsoft 의사 결정 트리 알고리즘</span><span class="sxs-lookup"><span data-stu-id="517e9-139">Microsoft Decision Tree algorithm</span></span>  
  
-   <span data-ttu-id="517e9-140">Microsoft 선형 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="517e9-140">Microsoft Linear Regression algorithm</span></span>  
  
-   <span data-ttu-id="517e9-141">Microsoft 로지스틱 회귀 알고리즘</span><span class="sxs-lookup"><span data-stu-id="517e9-141">Microsoft Logistic Regression algorithm</span></span>  
  
-   <span data-ttu-id="517e9-142">Microsoft 신경망 알고리즘</span><span class="sxs-lookup"><span data-stu-id="517e9-142">Microsoft Neural network algorithm</span></span>  
  
 <span data-ttu-id="517e9-143">**알고리즘 매개 변수** 대화 상자에서는 선택한 알고리즘에 따라 고급 옵션을 추가로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-143">In the **Algorithm Parameters** dialog box, you can set additional advanced options, depending on which algorithm you chose.</span></span> <span data-ttu-id="517e9-144">각 알고리즘의 옵션에 대한 자세한 내용은 SQL Server 온라인 설명서에서 다음 항목들을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="517e9-144">For information on the options for each algorithm see these topics in SQL Server Books Online:</span></span>  
  
 [<span data-ttu-id="517e9-145">Microsoft 의사 결정 트리 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="517e9-145">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="517e9-146">Microsoft 선형 회귀 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="517e9-146">Microsoft Linear Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="517e9-147">Microsoft 로지스틱 회귀 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="517e9-147">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="517e9-148">Microsoft 신경망 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="517e9-148">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="517e9-149">요구 사항</span><span class="sxs-lookup"><span data-stu-id="517e9-149">Requirements</span></span>  
 <span data-ttu-id="517e9-150">데이터 추정 마법사를 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-150">To use the Estimate Data Wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="517e9-151">연결을 만드는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517e9-151">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="517e9-152">추정 알고리즘을 사용하려면 예측하려는 결과가 통화, 판매 금액, 날짜 또는 시간과 같은 숫자 값으로 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e9-152">To use the estimation algorithm, the outcome that you are trying to predict must be expressed as a numeric value, such as a currency, sales amount, date, or time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517e9-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="517e9-153">See Also</span></span>  
 <span data-ttu-id="517e9-154">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="517e9-154">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="517e9-155">의사 결정 트리 다이어그램 연습 &#40;데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="517e9-155">Decision Tree Diagram Walkthrough  &#40;Data Mining Add-ins&#41;</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
