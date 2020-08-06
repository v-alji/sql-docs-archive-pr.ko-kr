---
title: Microsoft 신경망 뷰어를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 77e08955d09b7995e34ac94b75f809a303ca0d2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661448"
---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a><span data-ttu-id="15832-102">Microsoft 신경망 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="15832-102">Browse a Model Using the Microsoft Neural Network Viewer</span></span>
  <span data-ttu-id="15832-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 신경망 뷰어는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 신경망 알고리즘을 사용 하 여 작성 된 마이닝 모델을 표시 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="15832-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="15832-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 개방형 분석 및 탐색에 유용하고 여러 입력 및 출력을 분석할 수 있는 분류 및 회귀 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15832-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates classification and regression mining models that can analyze multiple inputs and outputs, and is very useful for open-ended analyses and exploration.</span></span> <span data-ttu-id="15832-105">이 알고리즘에 대한 자세한 내용은 [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15832-105">For more information about this algorithm, see [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md).</span></span>  
  
 <span data-ttu-id="15832-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 뷰어를 사용하여 모델을 탐색할 때는 일반적으로 대상 특성 및 상태를 선택한 다음 뷰어를 사용하여 입력 특성이 출력에 영향을 주는 방식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-106">When you explore a model using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer, you typically pick some target attribute and state, and then use the viewer to see how input attributes affect the outcome</span></span>  
  
 <span data-ttu-id="15832-107">예를 들어 잠재 고객 클래스에 대해 다음과 같은 사실을 알고 있다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="15832-107">For example, suppose you know these facts about a class of potential customers:</span></span>  
  
-   <span data-ttu-id="15832-108">중년(40~50세)</span><span class="sxs-lookup"><span data-stu-id="15832-108">Middle aged (40 to 50 years old).</span></span>  
  
-   <span data-ttu-id="15832-109">주택 소유</span><span class="sxs-lookup"><span data-stu-id="15832-109">Owns a home.</span></span>  
  
-   <span data-ttu-id="15832-110">집에 두 아이도 함께 살고 있음</span><span class="sxs-lookup"><span data-stu-id="15832-110">Has two children who still live at home.</span></span>  
  
 <span data-ttu-id="15832-111">고객이 구매할 가능성과 이러한 특성 간에 어떻게 상관 관계를 지정할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="15832-111">How can you correlate these attributes with the likelihood that the customer will make a purchase?</span></span>  
  
 <span data-ttu-id="15832-112">구매 행동을 대상 결과로 사용하여 신경망 모델을 작성함으로써 높은 수입과 같은 고객 특성에 대한 여러 조합을 탐색하고 어떤 조합이 구매 행동에 가장 영향을 많이 주는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-112">By building a neural network model using purchasing behavior as the target outcome, you can explore multiple combinations on customer attributes, such as high income, and discover which combination of attributes is most likely to influence purchasing behavior.</span></span> <span data-ttu-id="15832-113">예를 들어 결정 요소가 고객의 통근 거리라는 사실을 발견할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-113">For example, you might discover that the determining factor is the distance that they commute to work.</span></span>  
  
 <span data-ttu-id="15832-114">발견된 각 패턴을 나타내는 수식과 같은 자세한 정보를 보려는 경우 뷰로 전환하고 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-114">If you need to more view detailed information, such as the equations that represent each pattern that was discovered, you can switch views and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="15832-115">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) 또는 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15832-115">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="15832-116">뷰어 탭</span><span class="sxs-lookup"><span data-stu-id="15832-116">Viewer Tabs</span></span>  
 <span data-ttu-id="15832-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 찾으면 해당 모델의 적절한 뷰어에서 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 해당 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-117">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="15832-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 뷰어는 신경망 마이닝 모델 탐색 시 사용할 수 있는 다음과 같은 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer provides the following tabs for use in exploring neural network mining models:</span></span>  
  
-   [<span data-ttu-id="15832-119">입력</span><span class="sxs-lookup"><span data-stu-id="15832-119">Inputs</span></span>](#BKMK_Inputs)  
  
-   [<span data-ttu-id="15832-120">outputs</span><span class="sxs-lookup"><span data-stu-id="15832-120">Outputs</span></span>](#BKMK_Outputs)  
  
-   [<span data-ttu-id="15832-121">변수</span><span class="sxs-lookup"><span data-stu-id="15832-121">Variables</span></span>](#BKMK_Characteristics)  
  
###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="15832-122">내용</span><span class="sxs-lookup"><span data-stu-id="15832-122">Inputs</span></span>  
 <span data-ttu-id="15832-123">**입력** 탭을 사용하여 모델에서 입력으로 사용한 특성 및 특성 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-123">Use the **Inputs** tab to choose the attributes and values that the model used as inputs.</span></span> <span data-ttu-id="15832-124">뷰어를 열면 기본적으로 모든 특성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-124">By default, the viewer opens with all attributes included.</span></span> <span data-ttu-id="15832-125">이 기본 뷰에서 모델은 표시할 가장 중요한 특성 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-125">In this default view, the model chooses which attribute values are the most important to display.</span></span>  
  
 <span data-ttu-id="15832-126">입력 특성을 선택하려면 **입력** 표의 **특성** 열 내부를 클릭하고 드롭다운 목록에서 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-126">To select an input attribute, click inside the **Attribute** column of the **Input** grid, and select an attribute from the drop-down list.</span></span> <span data-ttu-id="15832-127">모델에 있는 특성만 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-127">(Only attributes that are included in the model are included in the list.)</span></span>  
  
 <span data-ttu-id="15832-128">**값** 열에 첫 번째 고유 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-128">The first distinct value appears under the **Value** column.</span></span> <span data-ttu-id="15832-129">기본값을 클릭하면 관련 특성의 모든 가능한 상태가 포함된 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-129">Clicking the default value reveals a list that contains all the possible states of the associated attribute.</span></span> <span data-ttu-id="15832-130">조사할 상태를 선택할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="15832-130">You can select the state that you want to investigate.</span></span> <span data-ttu-id="15832-131">원하는 만큼 특성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-131">You can select as many attributes as you want.</span></span>  
  
 [<span data-ttu-id="15832-132">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="15832-132">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="15832-133">출력</span><span class="sxs-lookup"><span data-stu-id="15832-133">Outputs</span></span>  
 <span data-ttu-id="15832-134">**출력** 탭을 사용하여 조사할 결과 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-134">Use the **Outputs** tab to choose the outcome attribute to investigate.</span></span> <span data-ttu-id="15832-135">비교할 두 결과 상태를 선택할 수 있습니다. 열은 모델을 작성할 때 예측 가능한 특성으로 정의되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="15832-135">You can choose any two outcome states to compare, assuming the columns were defined as predictable attributes when the model was created.</span></span>  
  
 <span data-ttu-id="15832-136">**출력 특성** 목록을 사용하여 특성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-136">Use the **OutputAttribute** list to select an attribute.</span></span> <span data-ttu-id="15832-137">그런 다음 **값 1** 목록과 **값 2** 목록에서 해당 특성과 연결된 두 개의 상태를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-137">You can then select two states that are associated with the attribute from the **Value 1** and **Value 2** lists.</span></span> <span data-ttu-id="15832-138">출력 특성의 이러한 두 가지 상태는 **변수** 창에서 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-138">These two states of the output attribute will be compared in the **Variables** pane.</span></span>  
  
 [<span data-ttu-id="15832-139">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="15832-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="variables"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="15832-140">변수</span><span class="sxs-lookup"><span data-stu-id="15832-140">Variables</span></span>  
 <span data-ttu-id="15832-141">**변수** 탭의 표에는 **특성**, **값**, **[값 1]과(와)의 유사성**및 **[값 2]과(와)의 유사성**열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15832-141">The grid in the **Variables** tab contains the following columns: **Attribute**, **Value**, **Favors [value 1]**, and **Favors [value 2]**.</span></span> <span data-ttu-id="15832-142">기본적으로 열은 **[값 1]과(와)의 유사성**수준에 따라 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-142">By default, the columns are sorted by the strength of **Favors [value 1]**.</span></span> <span data-ttu-id="15832-143">열 제목을 클릭하면 선택한 열의 정렬 순서가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="15832-143">Clicking a column heading changes the sort order to the selected column.</span></span>  
  
 <span data-ttu-id="15832-144">특성의 오른쪽에 있는 막대는 지정된 입력 특성 상태가 유사한 출력 특성 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15832-144">A bar to the right of the attribute shows which state of the output attribute the specified input attribute state favors.</span></span> <span data-ttu-id="15832-145">막대의 크기는 출력 상태와 입력 상태의 유사한 정도를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15832-145">The size of the bar shows how strongly the output state favors the input state.</span></span>  
  
 [<span data-ttu-id="15832-146">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="15832-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="15832-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15832-147">See Also</span></span>  
 <span data-ttu-id="15832-148">[Microsoft 신경망 알고리즘](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="15832-148">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="15832-149">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="15832-149">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="15832-150">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="15832-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="15832-151">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15832-151">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="15832-152">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="15832-152">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
