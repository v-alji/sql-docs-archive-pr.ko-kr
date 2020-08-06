---
title: 분류 마법사 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
ms.openlocfilehash: b82fc98df10ae2e6754a378dacea108f9f3379ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648067"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="46867-102">분류 마법사(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="46867-102">Classify Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="46867-103">![데이터 마이닝 리본의 분류 마법사](media/dmc-classify.gif "데이터 마이닝 리본의 분류 마법사")</span><span class="sxs-lookup"><span data-stu-id="46867-103">![Classify wizard in Data Mining ribbon](media/dmc-classify.gif "Classify wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="46867-104">**분류** 마법사를 사용하면 Excel 테이블, Excel 범위 또는 외부 데이터 원본의 기존 데이터를 기반으로 분류 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-104">The **Classify** wizard helps you build a classification model based on existing data in an Excel table, an Excel range, or an external data source.</span></span>  
  
 <span data-ttu-id="46867-105">분류 모델을 사용하면 유사성을 나타내는 데이터의 패턴을 추출하여 값 그룹에 따라 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-105">A classification model extracts patterns in your data that indicate similarities and helps you make predictions based on groupings of values.</span></span> <span data-ttu-id="46867-106">예를 들어 수입 또는 지출 패턴을 기반으로 위험을 예측하는 데 분류 모델을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-106">For example, a classification model might be used to predict risk based on income or spending patterns.</span></span>  
  
## <a name="using-the-classify-wizard"></a><span data-ttu-id="46867-107">분류 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="46867-107">Using the Classify Wizard</span></span>  
  
1.  <span data-ttu-id="46867-108">**데이터 마이닝** 리본에서 **분류**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-108">In the **Data Mining** ribbon, click **Classify**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="46867-109">**원본 데이터 선택** 페이지에서 분석할 데이터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-109">In the **Select Source Data** page, choose the data to analyze.</span></span>  
  
     <span data-ttu-id="46867-110">이 마법사는 Excel 테이블, Excel 범위 및 외부 데이터 원본 등 여러 종류의 데이터를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-110">This wizard supports multiple kinds of data: Excel tables, Excel ranges, and external data sources.</span></span> <span data-ttu-id="46867-111">외부 데이터의 경우 Excel에 추가하거나 Analysis Services 데이터 원본에서 테이블 또는 뷰 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-111">With external data, you can either add it into Excel, or choose a set of tables or views in an Analysis Services data source.</span></span> <span data-ttu-id="46867-112">또한 테이블을 추가하고 열을 변경해서 임시 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-112">You can also add tables and change columns to create ad hoc data sources.</span></span>  
  
3.  <span data-ttu-id="46867-113">**분류** 페이지에서 분류 하려는 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-113">On the **Classification** page, choose the column that you want to classify.</span></span>  
  
     <span data-ttu-id="46867-114">목록의 열과 **입력 열**을 검토 하 고 고유 값이 있는 열을 선택 취소 하 여 ID 번호, 고객 이름 등의 패턴을 만드는 데 유용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-114">Review the columns in the list, **Input columns**, and deselect any columns that have unique values and thus aren't useful for creating patterns, such as ID numbers, customer names, and so on.</span></span> <span data-ttu-id="46867-115">또한 본질적으로 분류 가능한 열이 중복되게 만드는 열도 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-115">You should also remove columns that essentially duplicate the classifiable column.</span></span>  
  
     <span data-ttu-id="46867-116">예를 들어 제품 범주 예측을 분류하는 경우, 알려진 비즈니스 규칙이 있으면 하위 범주 필드를 제외해야 합니다. 그렇지 않으면 해당 규칙의 강도로 인해 다른 상관 관계를 검색하는 데 방해가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-116">For example, if you are classifying predicting the category of a product, you should exclude the subcategory field if there is a known business rule, or else the strength of that rule might prevent you from discovering other correlations.</span></span>  
  
4.  <span data-ttu-id="46867-117">필요에 따라 **매개 변수** 를 클릭 하 여 알고리즘 매개 변수를 변경 하 고 클러스터링 모델의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-117">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="46867-118">**학습 및 테스트 집합으로 데이터 분할** 페이지에서 테스트를 위해 유지할 데이터 양을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-118">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="46867-119">나머지는 항상 모델 학습에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46867-119">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="46867-120">기본 설정은 테스트 데이터 30%와 학습 데이터 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="46867-120">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="46867-121">**마침** 페이지에서 데이터 집합 및 모델에 대 한 설명이 포함 된 이름을 입력 하 고 완성 된 모델을 사용 하는 방법을 제어 하는 다음 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-121">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="46867-122">**모델 찾아보기**.</span><span class="sxs-lookup"><span data-stu-id="46867-122">**Browse model**.</span></span> <span data-ttu-id="46867-123">이 옵션을 선택 하면 마법사가 모델 처리를 완료 하는 즉시 결과를 탐색 하는 데 도움이 되는 **찾아보기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="46867-123">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="46867-124">뷰어 내용은 작성한 모델 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="46867-124">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="46867-125">자세한 내용은 [의사 결정 트리 모델 탐색](browsing-a-decision-trees-model.md) 및 [신경망 모델 찾아보기](browsing-a-neural-network-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46867-125">For more information, see [Browsing a Decision Trees Model](browsing-a-decision-trees-model.md) and [Browsing a Neural Network Model](browsing-a-neural-network-model.md).</span></span>  
  
    -   <span data-ttu-id="46867-126">**드릴스루를 사용 하도록 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-126">**Enable drillthrough**.</span></span> <span data-ttu-id="46867-127">완료된 모델에서 기본 데이터를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46867-127">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="46867-128">이 옵션은 의사 결정 트리 모델을 작성하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-128">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="46867-129">**임시 모델 사용**.</span><span class="sxs-lookup"><span data-stu-id="46867-129">**Use temporary model**.</span></span> <span data-ttu-id="46867-130">이 옵션을 선택하면 모델이 서버에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-130">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="46867-131">임시 모델은 Excel을 닫을 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="46867-131">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-classification-models"></a><span data-ttu-id="46867-132">분류 모델에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="46867-132">More About Classification Models</span></span>  
 <span data-ttu-id="46867-133">**알고리즘 매개 변수** 대화 상자에서 Analysis Services에서 제공 하는 이러한 알고리즘 중에서 분류 방법을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-133">In the **Algorithm Parameters** dialog box, you can also choose the classification method from among these algorithms provided in Analysis Services:</span></span>  
  
-   <span data-ttu-id="46867-134">Microsoft 의사 결정 트리</span><span class="sxs-lookup"><span data-stu-id="46867-134">Microsoft Decision Tree</span></span>  
  
-   <span data-ttu-id="46867-135">Microsoft 로지스틱 회귀</span><span class="sxs-lookup"><span data-stu-id="46867-135">Microsoft Logistic Regression</span></span>  
  
-   <span data-ttu-id="46867-136">Microsoft Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="46867-136">Microsoft Naïve Bayes</span></span>  
  
-   <span data-ttu-id="46867-137">Microsoft 신경망</span><span class="sxs-lookup"><span data-stu-id="46867-137">Microsoft Neural Network</span></span>  
  
 <span data-ttu-id="46867-138">각 알고리즘이 비슷한 결과를 생성할 수 있지만 데이터의 분석 방법이 다르기 때문에 여러 알고리즘을 시도해보고 결과를 비교하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-138">Although the algorithms might yield similar results, they analyze the data differently, so we recommend trying several algorithms and comparing the results.</span></span> <span data-ttu-id="46867-139">기본 방법은 Microsoft 의사 결정 트리입니다.</span><span class="sxs-lookup"><span data-stu-id="46867-139">The default method is Microsoft Decision Trees.</span></span>  
  
 <span data-ttu-id="46867-140">**매개 변수** 목록에서 선택한 알고리즘 유형에 따라 달라 지는 고급 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-140">In the **Parameters** list, you can change advanced options, which depend on the type of algorithm you choose.</span></span> <span data-ttu-id="46867-141">각 알고리즘의 매개 변수에 대해서는 SQL Server 온라인 설명서에 보다 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46867-141">The parameters for each algorithm are described in more detail in SQL Server Books Online.</span></span>  
  
 [<span data-ttu-id="46867-142">Microsoft 의사 결정 트리 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="46867-142">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="46867-143">Microsoft 로지스틱 회귀 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="46867-143">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="46867-144">Microsoft Naive Bayes 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="46867-144">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="46867-145">Microsoft 신경망 알고리즘 기술 참조</span><span class="sxs-lookup"><span data-stu-id="46867-145">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="46867-146">요구 사항</span><span class="sxs-lookup"><span data-stu-id="46867-146">Requirements</span></span>  
 <span data-ttu-id="46867-147">**분류** 마법사를 사용 하려면 데이터베이스에 연결 해야 합니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="46867-147">To use the **Classify** wizard, you must be connected to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="46867-148">연결을 만드는 방법에 대 한 자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46867-148">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46867-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46867-149">See Also</span></span>  
 [<span data-ttu-id="46867-150">데이터 마이닝 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="46867-150">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
