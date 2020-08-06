---
title: Microsoft Naive Bayes Viewer를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661451"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a><span data-ttu-id="82647-102">Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="82647-102">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>
  <span data-ttu-id="82647-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 Naive Bayes 뷰어는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Naive Bayes 알고리즘을 사용 하 여 작성 된 마이닝 모델을 표시 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="82647-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="82647-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 예측 모델링 태스크에 매우 적응력이 뛰어난 분류 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="82647-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm that is highly adaptable to predictive modeling tasks.</span></span> <span data-ttu-id="82647-105">이 알고리즘에 대한 자세한 내용은 [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="82647-105">For more information about this algorithm, see [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="82647-106">Naive Bayes 모델의 주 목적 중 하나는 데이터 세트의 데이터를 빨리 탐색하는 방법을 제공하는 것이기 때문에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 뷰어는 예측 가능한 특성과 입력 특성 간의 상호 작용을 표시하는 여러 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-106">Because one of the main purposes of a naive Bayes model is to provide a way to quickly explore the data in a dataset, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides several methods for displaying the interaction between predictable attributes and input attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82647-107">발견된 패턴 및 모델에 사용된 수식에 대한 자세한 정보를 보려는 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82647-107">If you want to view detailed information about the equations used in the model and the patterns that were discovered, you can switch to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="82647-108">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) 또는 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82647-108">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="82647-109">뷰어 탭</span><span class="sxs-lookup"><span data-stu-id="82647-109">Viewer Tabs</span></span>  
 <span data-ttu-id="82647-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 찾으면 해당 모델의 적절한 뷰어에서 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 해당 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-110">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="82647-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 뷰어는 데이터 탐색을 위해 다음과 같은 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-111">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for exploring data:</span></span>  
  
-   [<span data-ttu-id="82647-112">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="82647-112">Dependency Network</span></span>](#BKMK_Dependency)  
  
-   [<span data-ttu-id="82647-113">특성 프로필</span><span class="sxs-lookup"><span data-stu-id="82647-113">Attribute Profiles</span></span>](#BKMK_Profiles)  
  
-   [<span data-ttu-id="82647-114">특성 특징</span><span class="sxs-lookup"><span data-stu-id="82647-114">Attribute Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="82647-115">특성 판별</span><span class="sxs-lookup"><span data-stu-id="82647-115">Attribute Discrimination</span></span>](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="82647-116">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="82647-116">Dependency Network</span></span>  
 <span data-ttu-id="82647-117">**종속성 네트워크** 탭은 모델의 입력 특성과 예측 가능한 특성 간의 종속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-117">The **Dependency Network** tab displays the dependencies between the input attributes and the predictable attributes in a model.</span></span> <span data-ttu-id="82647-118">뷰어의 왼쪽에 있는 슬라이더는 종속성 수준에 연결된 필터 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-118">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="82647-119">슬라이더를 내리면 강력한 링크만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-119">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="82647-120">노드를 선택하면 뷰어는 해당 노드와 관련된 종속성을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-120">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="82647-121">예를 들어 예측 가능한 노드를 선택하면 뷰어는 예측 가능한 노드를 예측하는 데 도움을 주는 각 노드도 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-121">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="82647-122">뷰어의 아래쪽에 있는 범례는 색 코드를 그래프에 있는 종속성 유형에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-122">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="82647-123">예를 들어 예측 가능한 노드를 선택하면 예측 가능한 노드는 옥색으로 표시되며 선택한 노드를 예측하는 노드는 주황색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-123">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="82647-124">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="82647-124">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a> <span data-ttu-id="82647-125">특성 프로필</span><span class="sxs-lookup"><span data-stu-id="82647-125">Attribute Profiles</span></span>  
 <span data-ttu-id="82647-126">**특성 프로필** 탭은 히스토그램을 표로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-126">The **Attribute Profiles** tab displays histograms in a grid.</span></span> <span data-ttu-id="82647-127">이 표를 사용하여 **예측 가능** 상자에서 선택한 예측 가능한 특성을 모델의 다른 모든 특성과 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82647-127">You can use this grid to compare the predictable attribute that you select in the **Predictable** box to all other attributes that are in the model.</span></span> <span data-ttu-id="82647-128">이 탭에 있는 각 열은 예측 가능한 특성의 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="82647-128">Each column in the tab represents a state of the predictable attribute.</span></span> <span data-ttu-id="82647-129">예측 가능한 특성에 많은 상태가 있으면 **히스토그램 막대**를 조절하여 히스토그램에 나타나는 상태 수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82647-129">If the predictable attribute has many states, you can change the number of states that appear in the histogram by adjusting the **Histogram bars**.</span></span> <span data-ttu-id="82647-130">선택한 수가 특성의 전체 상태 수보다 적으면 지원 순서대로 상태가 나열되고 나머지 상태는 회색의 단일 버킷으로 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-130">If the number you choose is less than the total number of states in the attribute, the states are listed in order of support, with the remaining states collected into a single gray bucket.</span></span>  
  
 <span data-ttu-id="82647-131">히스토그램의 색을 특성 상태에 연결하는 마이닝 범례를 표시하려면 **범례 표시** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-131">To display a Mining Legend that relates the colors of the histogram to the states of an attribute, click the **Show Legend** check box.</span></span> <span data-ttu-id="82647-132">또한 마이닝 범례는 선택하는 각 특성 값 쌍에 대해 사례 배포를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-132">The Mining Legend also displays the distribution of cases for each attribute-value pair that you select.</span></span>  
  
 <span data-ttu-id="82647-133">표 내용을 클립보드에 HTML 테이블로 복사하려면 **특성 프로필** 탭을 마우스 오른쪽 단추로 클릭하고 **복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-133">To copy the contents of the grid to the Clipboard as an HTML table, right-click the **Attribute Profiles** tab and select **Copy**.</span></span>  
  
 [<span data-ttu-id="82647-134">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="82647-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="82647-135">특성 특징</span><span class="sxs-lookup"><span data-stu-id="82647-135">Attribute Characteristics</span></span>  
 <span data-ttu-id="82647-136">**특성 특징** 탭을 사용하려면 **특성** 목록에서 예측 가능한 특성을 선택하고 **값** 목록에서 선택한 특성의 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-136">To use the **Attribute Characteristics** tab, select a predictable attribute from the **Attribute** list and select a state of the selected attribute from the **Value** list.</span></span> <span data-ttu-id="82647-137">이러한 변수를 설정하면 **특성 특징** 탭에 선택한 특성의 선택한 사례와 연결된 특성의 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-137">When you set these variables, the **Attribute Characteristics** tab displays the states of the attributes that are associated with the selected case of the selected attribute.</span></span> <span data-ttu-id="82647-138">특성은 중요도 순서로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-138">The attributes are sorted by importance.</span></span>  
  
 [<span data-ttu-id="82647-139">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="82647-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a> <span data-ttu-id="82647-140">특성 판별</span><span class="sxs-lookup"><span data-stu-id="82647-140">Attribute Discrimination</span></span>  
 <span data-ttu-id="82647-141">**특성 판별** 탭을 사용하려면 **특성**, **값 1**및 **값 2** 목록에서 예측 가능한 특성과 두 가지 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-141">To use the **Attribute Discrimination** tab, select a predictable attribute and two of its states from the **Attribute**, **Value 1**, and **Value 2** lists.</span></span> <span data-ttu-id="82647-142">그러면 **특성 판별** 탭에 있는 표의 열에 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82647-142">The grid on the **Attribute Discrimination** tab then displays the following information in columns:</span></span>  
  
 <span data-ttu-id="82647-143">**특성**</span><span class="sxs-lookup"><span data-stu-id="82647-143">**Attribute**</span></span>  
 <span data-ttu-id="82647-144">예측 가능한 특성의 한 가지 상태와 유사성이 큰 상태가 포함된 데이터 세트의 다른 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-144">Lists other attributes in the dataset that contain a state that highly favors one state of the predictable attribute.</span></span>  
  
 <span data-ttu-id="82647-145">**값**</span><span class="sxs-lookup"><span data-stu-id="82647-145">**Values**</span></span>  
 <span data-ttu-id="82647-146">**특성** 열의 특성 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82647-146">Shows the value of the attribute in the **Attribute** column.</span></span>  
  
 <span data-ttu-id="82647-147">**우위\<value 1>**</span><span class="sxs-lookup"><span data-stu-id="82647-147">**Favors \<value 1>**</span></span>  
 <span data-ttu-id="82647-148">특성 값이 **값 1**에 표시된 예측 가능한 특성 값과 얼마나 유사한지 나타내는 색이 지정된 막대를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-148">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 1**.</span></span>  
  
 <span data-ttu-id="82647-149">**우위\<value 2>**</span><span class="sxs-lookup"><span data-stu-id="82647-149">**Favors \<value 2>**</span></span>  
 <span data-ttu-id="82647-150">특성 값이 **값 2**에 표시된 예측 가능한 특성 값과 얼마나 유사한지 나타내는 색이 지정된 막대를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82647-150">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 2**.</span></span>  
  
 [<span data-ttu-id="82647-151">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="82647-151">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="82647-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82647-152">See Also</span></span>  
 <span data-ttu-id="82647-153">[Microsoft Naive Bayes 알고리즘](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="82647-153">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="82647-154">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="82647-154">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="82647-155">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82647-155">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="82647-156">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="82647-156">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
