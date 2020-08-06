---
title: 특성 특징 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29ba482c21bb674a10bc4c9e6c6eccdf30905dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648173"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="f2567-102">특성 특징 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="f2567-102">Attribute Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="f2567-103">**특성 특징** 창을 사용하여 Naïve Bayes 모델의 입력 특성과 결과 간의 관계를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-103">Use the **Attribute Characteristics** pane to explore the relationships between outcomes and input attributes in a Naïve Bayes model.</span></span> <span data-ttu-id="f2567-104">대상 특성의 값을 선택한 다음 결과에 가장 강한 영향을 주는 입력 특성의 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-104">You can choose the value of the target attribute, and then see a list of the input attributes that have the strongest effect on the outcomes.</span></span>  
  
 <span data-ttu-id="f2567-105">**자세한 내용:** [Microsoft Naive Bayes 알고리즘](data-mining/microsoft-naive-bayes-algorithm.md), [Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="f2567-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2567-106">옵션</span><span class="sxs-lookup"><span data-stu-id="f2567-106">Options</span></span>  
 <span data-ttu-id="f2567-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="f2567-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="f2567-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="f2567-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="f2567-109">**Mining Model**</span></span>  
 <span data-ttu-id="f2567-110">현재 마이닝 구조의 모델에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-110">Choose a mining model to view, from the models in the current mining structure.</span></span> <span data-ttu-id="f2567-111">마이닝 모델은 선택한 특정 모델 유형에 가장 적합한 사용자 지정 뷰어에서 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-111">The mining model will automatically open in a custom viewer that is best for the particular type of model you chose.</span></span>  
  
 <span data-ttu-id="f2567-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="f2567-112">**Viewer**</span></span>  
 <span data-ttu-id="f2567-113">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="f2567-114">각 모델에 대해 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-114">For each model, you have the choice of a custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="f2567-115">또한 사용 가능한 경우 플러그 인 뷰어도 이 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-115">Plug-in viewers also appear in this list if available.</span></span>  
  
 <span data-ttu-id="f2567-116">**특성**</span><span class="sxs-lookup"><span data-stu-id="f2567-116">**Attribute**</span></span>  
 <span data-ttu-id="f2567-117">분석하려는 예측 가능한 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-117">Choose the predictable attribute that you want to analyze.</span></span>  
  
 <span data-ttu-id="f2567-118">**값**</span><span class="sxs-lookup"><span data-stu-id="f2567-118">**Value**</span></span>  
 <span data-ttu-id="f2567-119">**특성**에서 설정한 예측 가능한 특성의 상태를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-119">Choose a state for the predictable attribute that you set in **Attribute**.</span></span> <span data-ttu-id="f2567-120">Naïve Bayes 모델은 연속 변수를 지원하지 않으므로 모든 대상 특성에는 불연속 또는 불연속화된 결과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-120">Because Naïve Bayes models do not support continuous variables, all target attributes have discrete or discretized outcomes.</span></span> <span data-ttu-id="f2567-121">누락된 특성은 항상 자동으로 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-121">The Missing attribute is always automatically added to the list.</span></span>  
  
 <span data-ttu-id="f2567-122">**특성\<predictable state>**</span><span class="sxs-lookup"><span data-stu-id="f2567-122">**Characteristics for \<predictable state>**</span></span>  
 <span data-ttu-id="f2567-123">이 그래프에는 입력 특성의 상태와 선택한 예측 가능한 특성 상태 간의 관계를 설명하는 다음 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-123">The graph contains the following columns, which describe how states of the input attributes are related to the selected predictable attribute state.</span></span>  
  
|<span data-ttu-id="f2567-124">값</span><span class="sxs-lookup"><span data-stu-id="f2567-124">Value</span></span>|<span data-ttu-id="f2567-125">Description</span><span class="sxs-lookup"><span data-stu-id="f2567-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2567-126">**변수**</span><span class="sxs-lookup"><span data-stu-id="f2567-126">**Variable**</span></span>|<span data-ttu-id="f2567-127">마이닝 모델의 입력 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-127">Lists the input attributes in the mining model.</span></span>|  
|<span data-ttu-id="f2567-128">**값**</span><span class="sxs-lookup"><span data-stu-id="f2567-128">**Values**</span></span>|<span data-ttu-id="f2567-129">**변수**에 있는 입력 특성의 각 상태를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-129">Lists each state of the input attribute in **Variable**.</span></span>|  
|<span data-ttu-id="f2567-130">**Probability**</span><span class="sxs-lookup"><span data-stu-id="f2567-130">**Probability**</span></span>|<span data-ttu-id="f2567-131">이 막대는 행의 특성 및 값이 예측 가능한 특성의 선택한 상태와 관련되어 있을 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-131">The bar represents the probability that the attribute and value in that row are associated with the selected state of the predictable attribute.</span></span> <span data-ttu-id="f2567-132">이 막대를 마우스로 가리키면 백분율로 확률을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2567-132">Hover the mouse over the bar to view the probability as a percentage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2567-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2567-133">See Also</span></span>  
 <span data-ttu-id="f2567-134">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f2567-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="f2567-135">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f2567-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="f2567-136">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="f2567-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
