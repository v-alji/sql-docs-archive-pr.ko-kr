---
title: Microsoft 연결 규칙 뷰어를 사용 하 여 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75bcefde30cb81cc00d8ad971756c68dedf670ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660793"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a><span data-ttu-id="0ef99-102">Microsoft 연결 규칙 뷰어를 사용하여 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="0ef99-102">Browse a Model Using the Microsoft Association Rules Viewer</span></span>
  <span data-ttu-id="0ef99-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]의 연결 규칙 뷰어는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 알고리즘을 사용 하 여 작성 된 마이닝 모델을 표시 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0ef99-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span> <span data-ttu-id="0ef99-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 알고리즘은 장바구니 분석에 사용할 수 있는 데이터 마이닝 모델을 만드는 데 사용하는 연결 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm is an association algorithm for use in creating data mining models that you can use for market basket analysis.</span></span> <span data-ttu-id="0ef99-105">이 알고리즘에 대한 자세한 내용은 [Microsoft Association Algorithm](microsoft-association-algorithm.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ef99-105">For more information about this algorithm, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span>  
  
 <span data-ttu-id="0ef99-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 알고리즘을 사용하는 주된 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-106">Following are the primary reasons for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm:</span></span>  
  
-   <span data-ttu-id="0ef99-107">트랜잭션에서 일반적으로 함께 발견되는 항목을 설명하는 항목 집합 찾기</span><span class="sxs-lookup"><span data-stu-id="0ef99-107">To find itemsets that describe items that are typically found together in a transaction.</span></span>  
  
-   <span data-ttu-id="0ef99-108">기존 항목을 기반으로 트랜잭션에 다른 항목이 있는지 여부를 예측하는 규칙 발견</span><span class="sxs-lookup"><span data-stu-id="0ef99-108">To discover rules that predict the presence of other items in a transaction based on existing items.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ef99-109">발견된 패턴 및 모델에 사용된 수식에 대한 자세한 정보를 보려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ef99-109">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="0ef99-110">자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) 또는 [Microsoft 일반 콘텐츠 트리 뷰어&#40;데이터 마이닝&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ef99-110">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="0ef99-111">연결 마이닝 모델의 생성, 탐색, 사용 방법에 대한 연습은 [3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ef99-111">For a walkthrough of how to create, explore, and use an association mining model, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="0ef99-112">뷰어 탭</span><span class="sxs-lookup"><span data-stu-id="0ef99-112">Viewer Tabs</span></span>  
 <span data-ttu-id="0ef99-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 찾으면 해당 모델의 적절한 뷰어에서 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 해당 모델이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-113">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="0ef99-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 연결 규칙 뷰어에는 다음과 같은 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-114">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="0ef99-115">항목 집합</span><span class="sxs-lookup"><span data-stu-id="0ef99-115">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="0ef99-116">규칙.</span><span class="sxs-lookup"><span data-stu-id="0ef99-116">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="0ef99-117">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0ef99-117">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="0ef99-118">각 탭에는 **긴 이름 표시** 확인란이 있으며 이 확인란을 사용하여 규칙 또는 항목 집합에서 항목 집합이 만들어진 테이블을 표시 또는 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-118">Each tab contains the **Show long name** check box, which you can use to show or hide the table from which the itemset originates in the rule or itemset.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="0ef99-119">항목 집합</span><span class="sxs-lookup"><span data-stu-id="0ef99-119">Itemsets</span></span>  
 <span data-ttu-id="0ef99-120">**항목 집합** 탭에서는 함께 자주 발견되는 항목 집합 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-120">The **Itemsets** tab displays the list of itemsets that the model identified as frequently found together.</span></span> <span data-ttu-id="0ef99-121">이 탭에는 **지원**, **크기**및 **항목 집합**열로 구성된 표가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-121">The tab displays a grid with the following columns: **Support**, **Size**, and **Itemset**.</span></span> <span data-ttu-id="0ef99-122">지원에 대한 자세한 내용은 [Microsoft Association Algorithm](microsoft-association-algorithm.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ef99-122">For more information about support, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span> <span data-ttu-id="0ef99-123">**크기** 열에서는 항목 집합에 있는 항목 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-123">The **Size** column displays the number of items in the itemset.</span></span> <span data-ttu-id="0ef99-124">**항목 집합** 열에서는 모델이 검색한 실제 항목 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-124">The **Itemset** column displays the actual itemset that the model discovered.</span></span> <span data-ttu-id="0ef99-125">**표시** 목록에서 다음 옵션을 설정하여 항목 집합의 형식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-125">You can control the format of the itemset by using the **Show** list, which you can set to the following options:</span></span>  
  
-   <span data-ttu-id="0ef99-126">**특성 이름 및 값 표시**</span><span class="sxs-lookup"><span data-stu-id="0ef99-126">**Show attribute name and value**</span></span>  
  
-   <span data-ttu-id="0ef99-127">**특성 값만 표시**</span><span class="sxs-lookup"><span data-stu-id="0ef99-127">**Show attribute value only**</span></span>  
  
-   <span data-ttu-id="0ef99-128">**특성 이름만 표시**</span><span class="sxs-lookup"><span data-stu-id="0ef99-128">**Show attribute name only**</span></span>  
  
 <span data-ttu-id="0ef99-129">**최소 지원** 및 **최소 항목 집합 크기**를 사용하여 탭에 표시되는 항목 집합 수를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-129">You can filter the number of itemsets that are displayed in the tab by using **Minimum support** and **Minimum itemset size**.</span></span> <span data-ttu-id="0ef99-130">또한 **항목 집합 필터** 를 통해 필요한 항목 집합 특징을 입력하여 표시되는 항목 집합 수를 더욱 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-130">You can limit the number of displayed itemsets even more by using **Filter Itemset** and entering an itemset characteristic that must exist.</span></span> <span data-ttu-id="0ef99-131">예를 들어 "Water Bottle = existing"을 입력하면 항목 집합을 Water Bottle이 포함된 집합으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-131">For example, if you type "Water Bottle = existing", you can limit the itemsets to only those that contain a water bottle.</span></span> <span data-ttu-id="0ef99-132">**항목 집합 필터** 옵션에서는 이전에 사용한 필터 목록도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-132">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
 <span data-ttu-id="0ef99-133">열 제목을 클릭하여 표에서 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-133">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="0ef99-134">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0ef99-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="0ef99-135">역할</span><span class="sxs-lookup"><span data-stu-id="0ef99-135">Rules</span></span>  
 <span data-ttu-id="0ef99-136">**규칙** 탭에서는 연결 알고리즘이 검색한 규칙을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-136">The **Rules** tab displays the rules that the association algorithm discovered.</span></span> <span data-ttu-id="0ef99-137">**규칙** 탭에는 **확률**, **중요도**및 **규칙**열로 구성된 표가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-137">The **Rules** tab includes a grid that contains the following columns: **Probability**, **Importance**, and **Rule**.</span></span> <span data-ttu-id="0ef99-138">확률은 규칙의 결과가 발생할 가능성을 나타내고</span><span class="sxs-lookup"><span data-stu-id="0ef99-138">The probability describes how likely the result of a rule is to occur.</span></span> <span data-ttu-id="0ef99-139">중요도는 규칙의 유용성을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-139">The importance is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="0ef99-140">규칙이 발생할 확률은 높아도 규칙 자체의 유용성이 떨어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-140">Although the probability that a rule will occur may be high, the usefulness of the rule may in itself be unimportant.</span></span> <span data-ttu-id="0ef99-141">중요도 열에서는 이러한 측면을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-141">The importance column addresses this.</span></span> <span data-ttu-id="0ef99-142">예를 들어 모든 항목 집합에 특성 상태가 있으면 확률이 매우 높아도 상태를 예측하는 규칙이 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-142">For example, if every itemset contains a specific state of an attribute, a rule that predicts state is trivial, even though the probability is very high.</span></span> <span data-ttu-id="0ef99-143">중요도가 클수록 규칙이 보다 중요해 집니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-143">The greater the importance, the more important the rule is.</span></span>  
  
 <span data-ttu-id="0ef99-144">**항목 집합** 탭에서 수행할 수 있는 필터링과 유사한 방식으로 **최소 확률** 및 **최소 중요도** 를 사용 하 여 규칙을 필터링 할 수 있습니다. **필터 규칙** 을 사용 하 여 포함 된 특성의 상태를 기준으로 규칙을 필터링 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-144">You can use **Minimum probability** and **Minimum importance** to filter the rules, similar to the filtering you can do on the **Itemsets** tab. You can also use **Filter Rule** to filter a rule based on the states of the attributes that it contains.</span></span>  
  
 <span data-ttu-id="0ef99-145">열 제목을 클릭하여 표에서 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-145">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="0ef99-146">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0ef99-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-net"></a><a name="BKMK_Dependency"></a><span data-ttu-id="0ef99-147">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0ef99-147">Dependency Net</span></span>  
 <span data-ttu-id="0ef99-148">**종속성 네트워크** 탭에는 종속성 네트워크 뷰어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-148">The **Dependency Net** tab includes a dependency network viewer.</span></span> <span data-ttu-id="0ef99-149">뷰어의 각 노드는 "state = WA"와 같은 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-149">Each node in the viewer represents an item, such as "state = WA".</span></span> <span data-ttu-id="0ef99-150">노드 사이의 화살표는 항목 간의 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-150">The arrow between nodes represents the association between items.</span></span> <span data-ttu-id="0ef99-151">화살표 방향은 알고리즘이 검색한 규칙에 따른 항목 간의 연결을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-151">The direction of the arrow dictates the association between the items according to the rules that the algorithm discovered.</span></span> <span data-ttu-id="0ef99-152">예를 들어 뷰어에 A, B, C 라는 항목이 있고 C가 A와 B에 의해 예측 된 경우 노드 C를 선택 하면 두 개의 화살표가 노드 C-A에서 C로, B는 C로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-152">For example, if the viewer contains three items, A, B, and C, and C is predicted by A and B, if you select node C, two arrows point toward node C - A to C and B to C.</span></span>  
  
 <span data-ttu-id="0ef99-153">뷰어의 왼쪽에 있는 슬라이더는 규칙의 확률에 연결된 필터 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-153">The slider at the left of the viewer acts as a filter that is tied to the probability of the rules.</span></span> <span data-ttu-id="0ef99-154">슬라이더를 내리면 강력한 링크만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef99-154">Lowering the slider shows only the strongest links.</span></span>  
  
 [<span data-ttu-id="0ef99-155">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0ef99-155">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="0ef99-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ef99-156">See Also</span></span>  
 <span data-ttu-id="0ef99-157">[Microsoft 연결 알고리즘](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="0ef99-157">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="0ef99-158">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="0ef99-158">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="0ef99-159">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="0ef99-159">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="0ef99-160">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0ef99-160">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="0ef99-161">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="0ef99-161">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
