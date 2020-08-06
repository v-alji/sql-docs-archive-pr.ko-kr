---
title: '2 단원: 자전거 구매자 마이닝 구조에 마이닝 모델 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733380"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a><span data-ttu-id="456c9-102">2단원: Bike Buyer 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="456c9-102">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="456c9-103">이 단원에서는 [1 단원: 자전거 구매자 마이닝 구조 만들기](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)에서 만든 자전거 구매자 마이닝 구조에 두 개의 마이닝 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-103">In this lesson, you will add two mining models to the Bike Buyer mining structure that you created [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md).</span></span> <span data-ttu-id="456c9-104">이러한 마이닝 모델을 추가하면 한 모델을 사용하여 데이터를 탐색하고 다른 모델을 사용하여 예측을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-104">These mining models will allow you to explore the data using one model, and to create predictions using another.</span></span>  
  
 <span data-ttu-id="456c9-105">잠재적 고객이 해당 특성으로 분류 될 수 있는 방법을 살펴보려면 [Microsoft 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)을 기반으로 하는 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-105">To explore how potential customers can be categorized by their characteristics, you will create a mining model based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span> <span data-ttu-id="456c9-106">이후 단원에서는 이 알고리즘에서 비슷한 특징을 공유하는 고객 집단을 찾는 방법을 알아 봅니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-106">In a later lesson, you will explore how this algorithm finds clusters of customers who share similar characteristics.</span></span> <span data-ttu-id="456c9-107">예를 들어 여러 특정 고객이 서로 근처에 살고 자전거로 출퇴근하며 비슷한 학력을 갖는 경향이 있음을 알게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-107">For example, you might find that certain customers tend to live close to each other, commute by bicycle, and have similar education backgrounds.</span></span> <span data-ttu-id="456c9-108">이러한 집단을 사용하여 고객 간의 상호 연관성을 보다 잘 파악할 수 있으며 이러한 정보를 사용하여 특정 고객을 대상으로 하는 마케팅 전략을 세울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-108">You can use these clusters to better understand how different customers are related, and to use the information to create a marketing strategy that targets specific customers.</span></span>  
  
 <span data-ttu-id="456c9-109">잠재 고객이 자전거를 구입할 가능성이 있는지 여부를 예측 하기 위해 [Microsoft 의사 결정 트리 알고리즘](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)을 기반으로 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-109">To predict whether a potential customer is likely to buy a bicycle, you will create a mining model based on the [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="456c9-110">이 알고리즘에서는 각 잠재 고객과 관련된 정보를 조사하여 해당 고객이 자전거를 구입할 지 여부를 예측하는 데 유용한 특징을 찾아냅니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-110">This algorithm looks through the information that is associated with each potential customer, and finds characteristics that are useful in predicting if they will buy a bicycle.</span></span> <span data-ttu-id="456c9-111">그런 다음 이전 자전거 구매자의 특징 값과 새 잠재 고객의 특징 값을 비교하여 새 잠재 고객이 자전거를 구입할 가능성이 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-111">It then compares the values of the characteristics of previous bike buyers against new potential customers to determine whether the new potential customers are likely to buy a bicycle.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="456c9-112">ALTER MINING STRUCTURE 문</span><span class="sxs-lookup"><span data-stu-id="456c9-112">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="456c9-113">마이닝 구조에 마이닝 모델을 추가 하려면 [ALTER 마이닝 structure &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-113">In order to add a mining model to the mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="456c9-114">이 문의 코드는 다음 부분으로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-114">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="456c9-115">마이닝 구조 식별</span><span class="sxs-lookup"><span data-stu-id="456c9-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="456c9-116">마이닝 모델 이름 지정</span><span class="sxs-lookup"><span data-stu-id="456c9-116">Naming the mining model</span></span>  
  
-   <span data-ttu-id="456c9-117">키 열 정의</span><span class="sxs-lookup"><span data-stu-id="456c9-117">Defining the key column</span></span>  
  
-   <span data-ttu-id="456c9-118">입력 및 예측 가능한 열 정의</span><span class="sxs-lookup"><span data-stu-id="456c9-118">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="456c9-119">알고리즘 및 매개 변수 변경 내용 식별</span><span class="sxs-lookup"><span data-stu-id="456c9-119">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="456c9-120">다음은 ALTER MINING MODEL 문의 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-120">The following is a generic example of the ALTER MINING MODEL statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 <span data-ttu-id="456c9-121">코드의 첫 번째 줄에서는 마이닝 모델을 추가할 기존 마이닝 구조를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-121">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="456c9-122">코드의 다음 줄에서는 마이닝 구조에 추가할 마이닝 모델의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-122">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="456c9-123">DMX에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="456c9-123">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="456c9-124">코드의 다음 줄에서는 마이닝 모델에서 사용할 마이닝 구조의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-124">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 <span data-ttu-id="456c9-125">마이닝 구조에 이미 있는 열만 사용할 수 있으며 목록의 첫 번째 열은 마이닝 구조의 키 열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-125">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="456c9-126">코드의 다음 줄에서는 마이닝 모델을 생성하는 마이닝 알고리즘과 알고리즘에 설정할 수 있는 알고리즘 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-126">The next line of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm:</span></span>  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="456c9-127">조정할 수 있는 알고리즘 매개 변수에 대 한 자세한 내용은 [Microsoft 의사 결정 트리 알고리즘](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) 및 [microsoft 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="456c9-127">For more information about the algorithm parameters that you can adjust, see [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span>  
  
 <span data-ttu-id="456c9-128">다음 구문을 사용하여 마이닝 모델의 열이 예측에 사용되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-128">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
 <span data-ttu-id="456c9-129">선택 사항인 코드의 마지막 줄에서는 모델을 학습하고 테스트할 때 적용되는 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-129">The final line of the code, which is optional, defines a filter that is applied when training and testing the model.</span></span> <span data-ttu-id="456c9-130">마이닝 모델에 필터를 적용 하는 방법에 대 한 자세한 내용은 [마이닝 모델에 대 한 필터 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="456c9-130">For more information about how to apply filters to mining models, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="456c9-131">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="456c9-131">Lesson Tasks</span></span>  
 <span data-ttu-id="456c9-132">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-132">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="456c9-133">[!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 사용하여 Bike Buyer 구조에 의사 결정 트리 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="456c9-133">Add a decision tree mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm</span></span>  
  
-   <span data-ttu-id="456c9-134">[!INCLUDE[msCoName](../includes/msconame-md.md)] 클러스터링 알고리즘을 사용하여 Bike Buyer 구조에 클러스터링 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="456c9-134">Add a clustering mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm</span></span>  
  
-   <span data-ttu-id="456c9-135">모든 경우에 대한 결과를 보기 위해 두 모델에 아직 필터를 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-135">Because you want to see results for all cases, you will not yet add a filter to either model.</span></span>  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a><span data-ttu-id="456c9-136">구조에 의사 결정 트리 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="456c9-136">Adding a Decision Tree Mining Model to the Structure</span></span>  
 <span data-ttu-id="456c9-137">첫 번째 단계는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 기반으로 마이닝 모델을 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-137">The first step is to add a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
#### <a name="to-add-a-decision-tree-mining-model"></a><span data-ttu-id="456c9-138">의사 결정 트리 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="456c9-138">To add a decision tree mining model</span></span>  
  
1.  <span data-ttu-id="456c9-139">**개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리**를 가리킨 다음 **DMX** 를 클릭하여 쿼리 편집기와 비어 있는 새 쿼리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-139">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="456c9-140">ALTER MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-140">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="456c9-141">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-141">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="456c9-142">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-142">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="456c9-143">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-143">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="456c9-144">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-144">with:</span></span>  
  
    ```  
    Decision Tree  
    ```  
  
5.  <span data-ttu-id="456c9-145">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-145">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    ```  
  
     <span data-ttu-id="456c9-146">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-146">with:</span></span>  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     <span data-ttu-id="456c9-147">이 경우 `[Bike Buyer]` 열을 PREDICT 열로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-147">In this case, the `[Bike Buyer]` column has been designated as the PREDICT column.</span></span>  
  
6.  <span data-ttu-id="456c9-148">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-148">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     <span data-ttu-id="456c9-149">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-149">with:</span></span>  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="456c9-150">WITH DRILLTHROUGH 문을 사용하면 마이닝 모델을 작성하는 데 사용된 사례를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-150">The WITH DRILLTHROUGH statement allows you to explore the cases that were used to build the mining model.</span></span>  
  
     <span data-ttu-id="456c9-151">이제 결과 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-151">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  <span data-ttu-id="456c9-152">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="456c9-153">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `DT_Model.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `DT_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="456c9-154">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-154">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a><span data-ttu-id="456c9-155">구조에 클러스터링 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="456c9-155">Adding a Clustering Mining Model to the Structure</span></span>  
 <span data-ttu-id="456c9-156">이제 [!INCLUDE[msCoName](../includes/msconame-md.md)] 클러스터링 알고리즘을 기반으로 Bike Buyer 마이닝 구조에 마이닝 모델을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-156">You can now add a mining model to the Bike Buyer mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="456c9-157">클러스터링 마이닝 모델은 마이닝 구조에 정의된 모든 열을 사용하기 때문에 바로 가기를 사용하여 마이닝 열 정의를 생략하여 구조에 모델을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-157">Because the clustering mining model will use all the columns defined in the mining structure, you can use a shortcut to add the model to the structure by omitting the definition of the mining columns.</span></span>  
  
#### <a name="to-add-a-clustering-mining-model"></a><span data-ttu-id="456c9-158">클러스터링 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="456c9-158">To add a Clustering mining model</span></span>  
  
1.  <span data-ttu-id="456c9-159">**개체 탐색기**에서 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **새 쿼리**를 가리킨 다음 **DMX** 를 클릭 하 여 쿼리 편집기 열기와 비어 있는 새 쿼리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-159">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor opens and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="456c9-160">ALTER MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-160">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="456c9-161">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-161">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="456c9-162">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-162">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="456c9-163">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-163">Replace the following:</span></span>  
  
    ```  
    <mining model>   
    ```  
  
     <span data-ttu-id="456c9-164">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-164">with:</span></span>  
  
    ```  
    Clustering Model  
    ```  
  
5.  <span data-ttu-id="456c9-165">다음 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-165">Delete the following:</span></span>  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  <span data-ttu-id="456c9-166">다음 내용을</span><span class="sxs-lookup"><span data-stu-id="456c9-166">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="456c9-167">다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-167">with:</span></span>  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     <span data-ttu-id="456c9-168">이제 전체 문이 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  <span data-ttu-id="456c9-169">**파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="456c9-170">다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 이름을로 `Clustering_Model.dmx` 합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Clustering_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="456c9-171">도구 모음에서 **실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-171">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="456c9-172">다음 단원에서는 모델과 마이닝 구조를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="456c9-172">In the next lesson, you will process the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="456c9-173">다음 단원</span><span class="sxs-lookup"><span data-stu-id="456c9-173">Next Lesson</span></span>  
 [<span data-ttu-id="456c9-174">3단원: Bike Buyer 마이닝 구조 처리</span><span class="sxs-lookup"><span data-stu-id="456c9-174">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
