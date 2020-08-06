---
title: 특성 판별 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: a8b0d4bc99b1c8f1c5de0269312f02eeb09df022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648168"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="0a303-102">특성 판별 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="0a303-102">Attribute Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="0a303-103">**특성 판별** 탭을 사용하여 입력 특성의 상태를 비교하고 결과 특성과의 관련성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-103">Use the **Attribute Discrimination** tab to compare the states of the input attributes and see how they are related to the outcome attribute.</span></span> <span data-ttu-id="0a303-104">선택한 두 예측 가능한 특성 간의 가장 큰 차이를 나타내는 특성 값이 먼저 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-104">The attribute values that make the most difference between the two selected predictable attribute states are listed first.</span></span>  
  
 <span data-ttu-id="0a303-105">**자세한 내용:** [Microsoft Naive Bayes 알고리즘](data-mining/microsoft-naive-bayes-algorithm.md), [Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="0a303-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a303-106">옵션</span><span class="sxs-lookup"><span data-stu-id="0a303-106">Options</span></span>  
 <span data-ttu-id="0a303-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="0a303-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="0a303-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="0a303-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="0a303-109">**Mining Model**</span></span>  
 <span data-ttu-id="0a303-110">현재 마이닝 구조에서 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="0a303-111">마이닝 모델이 올바른 사용자 지정 뷰어에서 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-111">The mining model automatically opens in the correct custom viewer.</span></span>  
  
 <span data-ttu-id="0a303-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="0a303-112">**Viewer**</span></span>  
 <span data-ttu-id="0a303-113">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="0a303-114">각 모델에 대해 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-114">For each model, you can choose either the custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="0a303-115">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="0a303-116">**특성**</span><span class="sxs-lookup"><span data-stu-id="0a303-116">**Attribute**</span></span>  
 <span data-ttu-id="0a303-117">예측 가능한 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-117">Choose a predictable attribute.</span></span>  
  
 <span data-ttu-id="0a303-118">**값 1**</span><span class="sxs-lookup"><span data-stu-id="0a303-118">**Value 1**</span></span>  
 <span data-ttu-id="0a303-119">**값 2**에 포함된 상태와 비교할 예측 가능한 특성의 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-119">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span>  
  
 <span data-ttu-id="0a303-120">**값 2**</span><span class="sxs-lookup"><span data-stu-id="0a303-120">**Value 2**</span></span>  
 <span data-ttu-id="0a303-121">**값 1**에 포함된 상태와 비교할 예측 가능한 특성의 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-121">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span> <span data-ttu-id="0a303-122">**다른 모든 상태** 를 선택 하 여 **값 1** 의 값을 보수, 즉 값 1을 제외한 다른 모든 값과 비교할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-122">You can also select **All Other States** to compare the value in **Value 1** with its complement-that is, all other values except Value 1.</span></span>  
  
 <span data-ttu-id="0a303-123">**및에 대 한 판별 점수 \<Value 1>\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="0a303-123">**Discrimination scores for \<Value 1> and \<Value 2>**</span></span>  
 <span data-ttu-id="0a303-124">그래프에는 대상 특성이 입력 특성의 특정 상태와 어떠한 관련이 있는지를 설명하는 다음 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-124">The graph contains the following columns, which describe how the target attribute is related to specific states of the input attribute.</span></span>  
  
|<span data-ttu-id="0a303-125">값</span><span class="sxs-lookup"><span data-stu-id="0a303-125">Value</span></span>|<span data-ttu-id="0a303-126">Description</span><span class="sxs-lookup"><span data-stu-id="0a303-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a303-127">**특성**</span><span class="sxs-lookup"><span data-stu-id="0a303-127">**Attributes**</span></span>|<span data-ttu-id="0a303-128">마이닝 모델의 입력 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-128">An input attribute in the mining model.</span></span>|  
|<span data-ttu-id="0a303-129">**값**</span><span class="sxs-lookup"><span data-stu-id="0a303-129">**Values**</span></span>|<span data-ttu-id="0a303-130">**특성**에 나열된 특성의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-130">A state of the attribute that is listed in **Attributes**.</span></span>|  
|<span data-ttu-id="0a303-131">**우위\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="0a303-131">**Favors \<Value 1>**</span></span>|<span data-ttu-id="0a303-132">막대는 현재 특성과 값이 **값 1**에서 선택한 대상 결과와 유사한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-132">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 1**.</span></span>|  
|<span data-ttu-id="0a303-133">**우위\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="0a303-133">**Favors \<Value 2>**</span></span>|<span data-ttu-id="0a303-134">막대는 현재 특성과 값이 **값 2**에서 선택한 대상 결과와 유사한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a303-134">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a303-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a303-135">See Also</span></span>  
 <span data-ttu-id="0a303-136">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0a303-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0a303-137">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="0a303-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="0a303-138">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="0a303-138">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
