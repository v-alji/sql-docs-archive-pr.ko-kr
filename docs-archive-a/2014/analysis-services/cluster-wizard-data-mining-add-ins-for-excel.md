---
title: 클러스터 마법사 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90500ae627bcafd1ca5ce17114dac9df9939691d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648683"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="9d21b-102">클러스터 마법사(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="9d21b-102">Cluster Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="9d21b-103">![데이터 마이닝 리본의 클러스터 마법사](media/dmc-cluster.gif "데이터 마이닝 리본의 클러스터 마법사")</span><span class="sxs-lookup"><span data-stu-id="9d21b-103">![Cluster wizard in Data Mining ribbon](media/dmc-cluster.gif "Cluster wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="9d21b-104">클러스터 마법사에서는 비슷한 특성을 공유하는 행을 검색하고 이를 그룹화 하여 그룹 간의 거리를 최대화하는 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-104">The Cluster wizard helps you build a model that detects rows that share similar characteristics and groups them to maximize the distance between groups.</span></span> <span data-ttu-id="9d21b-105">이 마법사는 모든 종류의 데이터에서 패턴을 찾는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-105">This wizard is useful for finding patterns in all kinds of data.</span></span>  
  
 <span data-ttu-id="9d21b-106">클러스터 마법사는 Microsoft 클러스터링 알고리즘을 사용하며 다양한 방식으로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-106">The Cluster wizard uses the Microsoft Clustering algorithm and can be extensively customized.</span></span> <span data-ttu-id="9d21b-107">이 마법사에는 Excel 테이블, Excel 범위 또는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 쿼리의 기존 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-107">It works on existing data from an Excel table, an Excel range, or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] query.</span></span> <span data-ttu-id="9d21b-108">Excel 용 테이블 분석 도구에 제공 되는 [범주 검색](detect-categories-table-analysis-tools-for-excel.md) 도구에서 비슷한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-108">Similar functionality is provided by the [Detect Categories](detect-categories-table-analysis-tools-for-excel.md) tool, provided in the Table Analysis Tools for Excel.</span></span> <span data-ttu-id="9d21b-109">하지만 범주 검색 도구는 사용자 지정할 수 없으며 Excel 테이블의 데이터를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-109">However, the Detect Categories tool cannot be customized and must use data in Excel tables.</span></span>  
  
## <a name="using-the-cluster-wizard"></a><span data-ttu-id="9d21b-110">클러스터 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="9d21b-110">Using the Cluster Wizard</span></span>  
  
1.  <span data-ttu-id="9d21b-111">데이터 마이닝 리본에서 **클러스터**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-111">In the Data Mining ribbon, click **Cluster**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="9d21b-112">**원본 데이터 선택** 페이지에서 Excel 테이블 또는 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-112">In the **Select Source Data** page, select an Excel table or range.</span></span> <span data-ttu-id="9d21b-113">또는 외부 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-113">Or specify and external data source.</span></span>  
  
     <span data-ttu-id="9d21b-114">외부 데이터 원본을 사용할 경우에는 사용자 지정 뷰를 만들거나 사용자 지정 쿼리 텍스트에 붙여 넣고 데이터 집합을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-114">If you use an external data source, you can create custom views or paste in custom query text, and save the data set as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="9d21b-115">**클러스터링** 페이지에서 모델이 빌드되는 방식을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-115">On the **Clustering** page, you can customize the way the model is built.</span></span>  
  
    -   <span data-ttu-id="9d21b-116">**세그먼트 수**의 경우 마법사에 고정 된 수의 범주를 만들도록 지시 하거나 최적의 그룹화 수를 자동으로 검색 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-116">For **Number of segments**, you can tell the wizard to create a fixed number of categories, or let it automatically detect the optimum number of groupings.</span></span>  
  
    -   <span data-ttu-id="9d21b-117">**입력 열** 목록에서 열 목록을 검토 하 고 패턴을 만드는 데 유용 하지 않은 열을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-117">Review the list of columns in the **Input columns** list, and deselect any columns that are not useful in creating patterns.</span></span> <span data-ttu-id="9d21b-118">제외해야 하는 열에는 ID 번호, 고객 이름 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-118">Columns you should exclude include ID numbers, customer names, and so on.</span></span>  
  
4.  <span data-ttu-id="9d21b-119">필요에 따라 **매개 변수** 를 클릭 하 여 알고리즘 매개 변수를 변경 하 고 클러스터링 모델의 동작을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-119">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="9d21b-120">**학습 및 테스트 집합으로 데이터 분할** 페이지에서 테스트를 위해 유지할 데이터 양을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-120">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="9d21b-121">나머지는 항상 모델 학습에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-121">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="9d21b-122">기본 설정은 테스트 데이터 30%와 학습 데이터 70%입니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-122">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="9d21b-123">**마침** 페이지에서 데이터 집합 및 모델에 대 한 설명이 포함 된 이름을 입력 하 고 완성 된 모델을 사용 하는 방법을 제어 하는 다음 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-123">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="9d21b-124">**모델 찾아보기**.</span><span class="sxs-lookup"><span data-stu-id="9d21b-124">**Browse model**.</span></span> <span data-ttu-id="9d21b-125">이 옵션을 선택 하면 마법사가 모델 처리를 완료 하는 즉시 결과를 탐색 하는 데 도움이 되는 **찾아보기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-125">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="9d21b-126">뷰어 내용은 작성한 모델 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-126">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="9d21b-127">자세한 내용은 [클러스터링 모델 찾아보기](browsing-a-clustering-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d21b-127">For more information, see [Browsing a Clustering Model](browsing-a-clustering-model.md).</span></span>  
  
    -   <span data-ttu-id="9d21b-128">**드릴스루를 사용 하도록 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-128">**Enable drillthrough**.</span></span> <span data-ttu-id="9d21b-129">완료된 모델에서 기본 데이터를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-129">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="9d21b-130">이 옵션은 의사 결정 트리 모델을 작성하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-130">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="9d21b-131">**임시 모델 사용**.</span><span class="sxs-lookup"><span data-stu-id="9d21b-131">**Use temporary model**.</span></span> <span data-ttu-id="9d21b-132">이 옵션을 선택하면 모델이 서버에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-132">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="9d21b-133">임시 모델은 Excel을 닫을 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-133">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-clustering-models"></a><span data-ttu-id="9d21b-134">클러스터링 모델에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="9d21b-134">More about Clustering Models</span></span>  
 <span data-ttu-id="9d21b-135">**고급** 을 클릭 하 고 **알고리즘 매개 변수** 대화 상자를 사용 하 여이 마법사에서 사용 하는 클러스터링 알고리즘을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-135">You can change the clustering algorithm used by this wizard by clicking **Advanced** and using the **Algorithm Parameters** dialog box.</span></span>  
  
 <span data-ttu-id="9d21b-136">Microsoft 클러스터링 알고리즘은 다음과 같은 클러스터링 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-136">The Microsoft Clustering algorithm provides these clustering methods:</span></span>  
  
-   <span data-ttu-id="9d21b-137">Scalable 또는 Non-scalable K-Means</span><span class="sxs-lookup"><span data-stu-id="9d21b-137">K-means -  scalable or non-scaling.</span></span>  
  
-   <span data-ttu-id="9d21b-138">Scalable 또는 Non-scalable EM(Expectation Maximization)</span><span class="sxs-lookup"><span data-stu-id="9d21b-138">Expectation Maximization (EM) - scalable or non-scaling.</span></span>  
  
 <span data-ttu-id="9d21b-139">또한 CLUSTER_SEED 매개 변수를 사용하여 시작 값을 제어하고 동일한 데이터 집합을 사용하는 반복되는 모델의 결과가 동일하도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-139">You can also use the CLUSTER_SEED parameter to control the starting value and ensure that repeated models using the same data set have the same results.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="9d21b-140">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9d21b-140">Requirements</span></span>  
 <span data-ttu-id="9d21b-141">클러스터 마법사를 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d21b-141">To use the Cluster wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="9d21b-142">자세한 내용은 [Excel 용 데이터 마이닝 클라이언트&#41;&#40;원본 데이터에 연결 ](connect-to-source-data-data-mining-client-for-excel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d21b-142">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d21b-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d21b-143">See Also</span></span>  
 <span data-ttu-id="9d21b-144">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="9d21b-144">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="9d21b-145">Excel 용 테이블 분석 도구 &#40;범주 검색&#41;</span><span class="sxs-lookup"><span data-stu-id="9d21b-145">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
