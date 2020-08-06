---
title: 시계열 모델에 대 한 수식 보기 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
ms.openlocfilehash: eff61c469d34f084e6a0eb11c49a1c37c7cc97c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639084"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a><span data-ttu-id="b8f41-102">시계열 모델에 대한 수식 보기(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="b8f41-102">View the Formula for a Time Series Model (Data Mining)</span></span>
  <span data-ttu-id="b8f41-103">시계열 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 뷰어 inData 마이닝 디자이너는 시계열 모델에 사용 되는 회귀 수식의 세부 정보를 보는 가장 쉬운 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series viewer inData Mining Designer provides the easiest way to view the details of the regression equation used in a time series model.</span></span>  
  
 <span data-ttu-id="b8f41-104">모델 콘텐츠를 쿼리하여 시계열 모델의 회귀 수식을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-104">You can extract the regression formula for a time series model by querying the model content.</span></span> <span data-ttu-id="b8f41-105">그러나 complete ARTXP 또는 ARIMA 수식을 보려면 모든 상수를 읽을 수 있는 형식으로 제공 하는 [Microsoft 시계열 뷰어](browse-a-model-using-the-microsoft-time-series-viewer.md)의 **마이닝 범례** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-105">However, to view the complete ARTXP or ARIMA formula, we recommend that you use the **Mining Legend** of the [Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md), which presents all the constants in a readable format.</span></span>  
  
 <span data-ttu-id="b8f41-106">혼합 모델을 만들 경우 ARIMA 및 ARTXP 분석이 개별 트리에 만들어지고 모델을 나타내는 루트 노드에서 조인됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-106">If you create a mixed model, the ARIMA and ARTXP analyses are created in separate trees, joined at the root node representing the model.</span></span> <span data-ttu-id="b8f41-107">ARIMA 트리와 ARTXP 트리는 구조가 아주 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-107">The structures of the ARIMA and ARTXP trees are very different.</span></span> <span data-ttu-id="b8f41-108">예를 들어 ARTXP 트리는 실제로 의사 결정 트리와 같은 트리 구조인 반면에 ARIMA 트리는 이동 평균의 계열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-108">For example, the ARTXP tree is in fact a tree structure, like a decision tree, whereas the ARIMA tree represents a series of moving averages.</span></span> <span data-ttu-id="b8f41-109">따라서 이러한 두 표현은 편의상 한 모델로 제공되지만 두 개의 독립적인 모델로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-109">Therefore, although the two representations are presented in one model for convenience, they should be treated as two independent models.</span></span> <span data-ttu-id="b8f41-110">수식도 완전히 다르며 조합하거나 비교할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-110">The equations are also completely different and cannot be combined or compared.</span></span>  
  
 <span data-ttu-id="b8f41-111">[Microsoft 일반 콘텐츠 트리 뷰어](../microsoft-generic-content-tree-viewer-data-mining.md)를 사용 하 여 시계열 모델을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-111">You can also view time series models by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="b8f41-112">시계열 모델의 내용에 대 한 자세한 내용은 [Analysis Services 데이터 마이닝&#41;&#40;시계열 모델에 대 한 마이닝 모델 콘텐츠 ](mining-model-content-for-time-series-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8f41-112">For more information about the content of a time series model, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a><span data-ttu-id="b8f41-113">시계열 모델의 ARTXP 회귀 수식을 보려면</span><span class="sxs-lookup"><span data-stu-id="b8f41-113">To view the ARTXP regression formula for a time series model</span></span>  
  
1.  <span data-ttu-id="b8f41-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 보려는 시계열 모델을 선택하고 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-114">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="b8f41-115">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="b8f41-115">-- or --</span></span>  
  
     <span data-ttu-id="b8f41-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 시계열 모델을 선택한 다음 **마이닝 모델 뷰어** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="b8f41-117">**모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-117">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="b8f41-118">모델에 여러 개의 트리가 있는 경우 **트리** 드롭다운 목록에서 단일 트리를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-118">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b8f41-119">데이터 계열이 둘 이상인 경우 모델에는 항상 여러 개의 트리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-119">A model will always have multiple trees if you have more than one data series.</span></span> <span data-ttu-id="b8f41-120">그러나 **시계열 뷰어** 에 표시되는 트리 수는 [Microsoft 일반 콘텐츠 트리 뷰어](../microsoft-generic-content-tree-viewer-data-mining.md)에 표시되는 트리 수와 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-120">However, you will not see as many trees in the **Time Series viewer** as you will see in the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="b8f41-121">시계열 뷰어에서는 각 데이터 계열의 ARIMA 및 ARTXP 정보를 단일 표현으로 조합하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-121">That is because the Time Series viewer combines the ARIMA and ARTXP information for each data series into a single representation.</span></span>  
  
4.  <span data-ttu-id="b8f41-122">트리의 리프 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-122">Click any leaf node in the tree.</span></span>  
  
     <span data-ttu-id="b8f41-123">**데이터 계열** 이라는 레이블이 붙는 노드는 항상 리프 노드이며 수식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-123">Nodes that are labeled as **Data Series** are always leaf nodes and can contain an equation.</span></span> <span data-ttu-id="b8f41-124">**(All)** 노드에 자식 노드가 없는 경우 이 노드도 수식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-124">If an **(All)** node has no child nodes, it can also contain an equation.</span></span>  
  
5.  <span data-ttu-id="b8f41-125">**마이닝 범례** 를 사용할 수 없는 경우 노드를 마우스 오른쪽 단추로 클릭하고 **범례 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-125">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="b8f41-126">ARTXP 수식은 **마이닝 범례**의 첫 번째 부분에 **트리 노드 수식**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-126">The ARTXP formula is displayed in the first half of the **Mining Legend**, as the **Tree node equation**.</span></span>  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a><span data-ttu-id="b8f41-127">시계열 모델의 ARIMA 수식을 보려면</span><span class="sxs-lookup"><span data-stu-id="b8f41-127">To view the ARIMA formula for a time series model</span></span>  
  
1.  <span data-ttu-id="b8f41-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 보려는 시계열 모델을 선택하고 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="b8f41-129">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="b8f41-129">-- or --</span></span>  
  
     <span data-ttu-id="b8f41-130">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 시계열 모델을 선택한 다음 **마이닝 모델 뷰어** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-130">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="b8f41-131">**모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-131">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="b8f41-132">모델에 여러 개의 트리가 있는 경우 **트리** 드롭다운 목록에서 단일 트리를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-132">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b8f41-133">데이터 계열이 둘 이상인 경우 모델에는 항상 여러 개의 트리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-133">The model will always have multiple trees if you include more than one data series.</span></span>  
  
4.  <span data-ttu-id="b8f41-134">트리의 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-134">Click any node in the tree.</span></span>  
  
     <span data-ttu-id="b8f41-135">ARIMA 수식은 **마이닝 범례**의 두 번째 부분에 **ARIMA 수식**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-135">The ARIMA formula is displayed in the second half of the **Mining Legend**, as the **ARIMA equation**.</span></span>  
  
5.  <span data-ttu-id="b8f41-136">**마이닝 범례** 를 사용할 수 없는 경우 노드를 마우스 오른쪽 단추로 클릭하고 **범례 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f41-136">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f41-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8f41-137">See Also</span></span>  
 <span data-ttu-id="b8f41-138">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b8f41-138">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="b8f41-139">[Microsoft 시계열 뷰어를 사용 하 여 모델 찾아보기](browse-a-model-using-the-microsoft-time-series-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="b8f41-139">[Browse a Model Using the Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md) </span></span>  
 [<span data-ttu-id="b8f41-140">시계열 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="b8f41-140">Time Series Model Query Examples</span></span>](time-series-model-query-examples.md)  
  
  
