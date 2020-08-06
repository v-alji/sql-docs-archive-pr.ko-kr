---
title: Naive Bayes 모델 탐색 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a26fa972e1ed50e2f4107026210a5935fcb86d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734716"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a><span data-ttu-id="ec050-102">Naive Bayes 모델 탐색(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="ec050-102">Exploring the Naive Bayes Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="ec050-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes 알고리즘은 자전거 구매와 입력 특성 간의 상호 작용을 표시 하는 여러 가지 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm provides several methods for displaying the interaction between bike buying and the input attributes.</span></span>  
  
 <span data-ttu-id="ec050-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes 뷰어는 Naive Bayes 마이닝 모델 탐색에 사용할 다음 탭을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for use in exploring Naive Bayes mining models:</span></span>  
  
 
  
##  <a name="dependency-network"></a><a name="DependencyNetwork"></a><span data-ttu-id="ec050-105">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="ec050-105">Dependency Network</span></span>  
 <span data-ttu-id="ec050-106">**종속성 네트워크** 탭은 트리 뷰어의 **종속성 네트워크** 탭과 동일한 방식으로 작동 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ec050-106">The **Dependency Network** tab works in the same way as the **Dependency Network** tab for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="ec050-107">뷰어의 각 노드는 특성을, 노드 사이의 선은 관계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-107">Each node in the viewer represents an attribute, and the lines between nodes represent relationships.</span></span> <span data-ttu-id="ec050-108">뷰어에서 예측 가능한 특성인 Bike Buyer의 상태에 영향을 주는 특성을 모두 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-108">In the viewer, you can see all the attributes that affect the state of the predictable attribute, Bike Buyer.</span></span>  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="ec050-109">종속성 네트워크 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="ec050-109">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="ec050-110">**마이닝 모델 뷰어** 탭의 위쪽에 있는 **마이닝 모델** 목록을 사용 하 여 모델로 전환할 수 `TM_NaiveBayes` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-110">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_NaiveBayes` model.</span></span>  
  
2.  <span data-ttu-id="ec050-111">**뷰어** 목록을 사용 하 여 **Microsoft Naive Bayes Viewer**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-111">Use the **Viewer** list to switch to **Microsoft Naive Bayes Viewer**.</span></span>  
  
3.  <span data-ttu-id="ec050-112">노드를 클릭 `Bike Buyer` 하 여 해당 종속성을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-112">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="ec050-113">분홍색 음영은 모든 특성이 자전거 구매에 영향을 준다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-113">The pink shading indicates that all of the attributes have an effect on bike buying.</span></span>  
  
4.  <span data-ttu-id="ec050-114">슬라이더를 조정하여 가장 큰 영향을 주는 특성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-114">Adjust the slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="ec050-115">슬라이더를 내리면 [Bike Buyer] 열에 가장 큰 영향을 주는 특성만 남습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-115">As you lower the slider, only the attributes that have the greatest effect on the [Bike Buyer] column remain.</span></span> <span data-ttu-id="ec050-116">슬라이더를 조정하여 소유 차량 대수, 통근 거리 및 총 자녀 수가 가장 영향을 주는 특성 중 일부임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-116">By adjusting the slider, you can discover that a few of the most influential attributes are: number of cars owned, commute distance, and total number of children.</span></span>  
 
  
##  <a name="attribute-profiles"></a><a name="AttributeProfiles"></a> <span data-ttu-id="ec050-117">특성 프로필</span><span class="sxs-lookup"><span data-stu-id="ec050-117">Attribute Profiles</span></span>  
 <span data-ttu-id="ec050-118">**특성 프로필** 탭은 입력 특성의 여러 상태가 예측 가능한 특성의 결과에 미치는 영향을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-118">The **Attribute Profiles** tab describes how different states of the input attributes affect the outcome of the predictable attribute.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a><span data-ttu-id="ec050-119">특성 프로필 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="ec050-119">To explore the model in the Attribute Profiles tab</span></span>  
  
1.  <span data-ttu-id="ec050-120">**예측** 가능 상자에서 `Bike Buyer` 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-120">In the **Predictable** box, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="ec050-121">**마이닝 범례** 가 **특성 프로필**의 표시를 차단 하 고 있는 경우이를 밖으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-121">If the **Mining Legend** is blocking display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="ec050-122">**히스토그램** 막대 상자에서 **5**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-122">In the **Histogram** bars box, select **5**.</span></span>  
  
     <span data-ttu-id="ec050-123">이 모델에서 5는 어느 한 변수의 상태에 지정할 수 있는 최대값입니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-123">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
     <span data-ttu-id="ec050-124">입력 특성의 각 상태 값 및 해당 특성이 예측 가능한 특성의 각 상태에서 가지는 분포와 함께 이 예측 가능 특성의 상태에 영향을 주는 특성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-124">The attributes that affect the state of this predictable attribute are listed together with the values of each state of the input attributes and their distributions in each state of the predictable attribute.</span></span>  
  
4.  <span data-ttu-id="ec050-125">**특성** 열에서 **소유한 자동차 수**를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-125">In the **Attributes** column, find **Number Cars Owned**.</span></span>  <span data-ttu-id="ec050-126">히스토그램에서 자전거 구매자(레이블이 1인 열)와 비구매자(레이블이 0인 열) 간의 차이를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec050-126">Notice the differences in the histograms for bike buyers (column labeled 1) and non-buyers (column labeled 0).</span></span> <span data-ttu-id="ec050-127">차가 한 대 있거나 한 대도 없는 사람이 자전거를 구매할 확률이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-127">A person with zero or one car is much more likely to buy a bike.</span></span>  
  
5.  <span data-ttu-id="ec050-128">자전거 구매자 (레이블이 1 인 열) 열에서 **자동차가 소유한 셀 수** 를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-128">Double-click the **Number Cars Owned** cell in the bike buyer (column labeled 1) column.</span></span>  
  
     <span data-ttu-id="ec050-129">**마이닝 범례** 에 보다 자세한 보기가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-129">The **Mining Legend** displays a more detailed view.</span></span>  
  
  
##  <a name="attribute-characteristics"></a><a name="AttributeCharacteristics"></a> <span data-ttu-id="ec050-130">특성 특징</span><span class="sxs-lookup"><span data-stu-id="ec050-130">Attribute Characteristics</span></span>  
 <span data-ttu-id="ec050-131">**특성 특징** 탭을 사용 하 여 특성 및 값을 선택 하 여 선택한 값 사례에서 다른 특성의 값이 표시 되는 빈도를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-131">With the **Attribute Characteristics** tab, you can select an attribute and value to see how frequently values for other attributes appear in the selected value cases.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a><span data-ttu-id="ec050-132">특성 특징 탭에서 모델을 탐색하려면</span><span class="sxs-lookup"><span data-stu-id="ec050-132">To explore the model in the Attribute Characteristics tab</span></span>  
  
1.  <span data-ttu-id="ec050-133">**특성** 목록에서 `Bike Buyer` 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-133">In the **Attribute** list, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="ec050-134">**값** 을 **1**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-134">Set the **Value** to **1**.</span></span>  
  
     <span data-ttu-id="ec050-135">뷰어에서 자녀가 없고, 통근 거리가 짧고, 북아메리카 지역에 사는 고객이 자전거를 구매할 가능성이 더 많음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-135">In the viewer, you will see that customers who have no children at home, short commutes, and live in the North America region are more likely to buy a bike.</span></span>  
  
  
##  <a name="attribute-discrimination"></a><a name="AttributeDiscrimination"></a> <span data-ttu-id="ec050-136">특성 판별</span><span class="sxs-lookup"><span data-stu-id="ec050-136">Attribute Discrimination</span></span>  
 <span data-ttu-id="ec050-137">**특성 판별** 탭을 사용 하 여 자전거 구매 및 기타 특성 값의 두 불연속 값 간의 관계를 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-137">With the **Attribute Discrimination** tab, you can investigate the relationship between two discrete values of bike buying and other attribute values.</span></span> <span data-ttu-id="ec050-138">모델에는 `TM_NaiveBayes` 1과 0 이라는 두 가지 상태만 있으므로 뷰어를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-138">Because the `TM_NaiveBayes` model has only two states, 1 and 0, you do not have to make any changes to the viewer.</span></span>  
  
 <span data-ttu-id="ec050-139">뷰어에서 차량을 소유하지 않은 사람들이 자전거를 구매하고 두 대의 차량을 소유한 사람들이 자전거를 구매하지 않는 경향이 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec050-139">In the viewer, you can see that people who do not own cars tend to buy bicycles, and people who own two cars tend not to buy bicycles.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ec050-140">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ec050-140">Related Tasks</span></span>  
 <span data-ttu-id="ec050-141">다른 마이닝 모델을 탐색 하려면 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec050-141">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="ec050-142">기본 데이터 마이닝 자습서 &#40;의사 결정 트리 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="ec050-142">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="ec050-143">기본 데이터 마이닝 자습서 &#40;클러스터링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="ec050-143">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="ec050-144">다음 단원</span><span class="sxs-lookup"><span data-stu-id="ec050-144">Next Lesson</span></span>  
 [<span data-ttu-id="ec050-145">5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="ec050-145">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="ec050-146">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="ec050-146">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="ec050-147">기본 데이터 마이닝 자습서 &#40;클러스터링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="ec050-147">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec050-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec050-148">See Also</span></span>  
 <span data-ttu-id="ec050-149">[Microsoft Naive Bayes Viewer를 사용 하 여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="ec050-149">[Browse a Model Using the Microsoft Naive Bayes Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span></span>  
 <span data-ttu-id="ec050-150">[마이닝 모델 뷰어를 &#40;특성 판별 탭&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="ec050-150">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="ec050-151">[마이닝 모델 뷰어 &#40;특성 프로필 탭&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="ec050-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="ec050-152">[마이닝 모델 뷰어 &#40;특성 특징 탭&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="ec050-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="ec050-153">&#40;마이닝 모델 뷰어&#41;종속성 네트워크 탭</span><span class="sxs-lookup"><span data-stu-id="ec050-153">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
