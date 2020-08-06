---
title: 특성 프로필 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61c81b95f030bf1a69aed165bd64e58ff9af8339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648163"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a><span data-ttu-id="ab39e-102">특성 프로필 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="ab39e-102">Attribute Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="ab39e-103">**특성 프로필** 탭을 사용하여 Naive Bayes 모델 상태의 입력 값 분포가 결과 특성의 각 상태에 주는 영향을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-103">Use the **Attribute Profiles** tab to see how the distribution of input values in a Naive Bayes model state contribute to each state of the outcome attribute.</span></span> <span data-ttu-id="ab39e-104">값의 분포는 색이 지정된 히스토그램으로 표시되고 모든 분포가 표 형식으로 제공되므로 보다 쉽게 값을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-104">The distribution of values is shown as a colored histogram, all distributions presented in a tabular format, to make it easier to compare values.</span></span>  
  
 <span data-ttu-id="ab39e-105">**자세한 내용:** [Microsoft Naive Bayes 알고리즘](data-mining/microsoft-naive-bayes-algorithm.md), [Microsoft Naive Bayes 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="ab39e-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab39e-106">옵션</span><span class="sxs-lookup"><span data-stu-id="ab39e-106">Options</span></span>  
 <span data-ttu-id="ab39e-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="ab39e-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="ab39e-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="ab39e-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="ab39e-109">**Mining Model**</span></span>  
 <span data-ttu-id="ab39e-110">현재 마이닝 구조에서 보려는 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-110">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="ab39e-111">관련 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="ab39e-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="ab39e-112">**Viewer**</span></span>  
 <span data-ttu-id="ab39e-113">선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="ab39e-114">각 마이닝 모델에 대해 제공되는 사용자 지정 뷰어나 [!INCLUDE[msCoName](../includes/msconame-md.md)] 마이닝 콘텐츠 뷰어를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-114">You can choose the custom viewer provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="ab39e-115">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-115">You can also use plug-in viewers if they are available.</span></span>  
  
 <span data-ttu-id="ab39e-116">**범례 표시**</span><span class="sxs-lookup"><span data-stu-id="ab39e-116">**Show Legend**</span></span>  
 <span data-ttu-id="ab39e-117">**상태** 의 각 값을 분포 차트에서 사용된 색 중 하나와 일치시키는 키를 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-117">Select this option to display a key that matches each value in **States** to one of the colors used in the distribution chart.</span></span>  
  
 <span data-ttu-id="ab39e-118">**히스토그램 막대**</span><span class="sxs-lookup"><span data-stu-id="ab39e-118">**Histogram bars**</span></span>  
 <span data-ttu-id="ab39e-119">히스토그램에 포함할 막대 수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-119">Select how many bars to include in the histogram.</span></span> <span data-ttu-id="ab39e-120">선택한 것보다 더 많은 막대가 있는 경우 가장 중요한 막대만 유지되고 나머지 막대는 모두 **기타**로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-120">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="ab39e-121">**예측 가능**</span><span class="sxs-lookup"><span data-stu-id="ab39e-121">**Predictable**</span></span>  
 <span data-ttu-id="ab39e-122">마이닝 모델에서 예측 가능한 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-122">Select a predictable column from the mining model.</span></span>  
  
 <span data-ttu-id="ab39e-123">**특성 프로필**</span><span class="sxs-lookup"><span data-stu-id="ab39e-123">**Attribute Profiles**</span></span>  
 <span data-ttu-id="ab39e-124">표에는 다음 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-124">The table contains the following columns:</span></span>  
  
|<span data-ttu-id="ab39e-125">값</span><span class="sxs-lookup"><span data-stu-id="ab39e-125">Value</span></span>|<span data-ttu-id="ab39e-126">Description</span><span class="sxs-lookup"><span data-stu-id="ab39e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab39e-127">**특성**</span><span class="sxs-lookup"><span data-stu-id="ab39e-127">**Attributes**</span></span>|<span data-ttu-id="ab39e-128">마이닝 모델에 포함된 마이닝 모델 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-128">Lists the mining model columns contained within the mining model.</span></span>|  
|<span data-ttu-id="ab39e-129">**상태**</span><span class="sxs-lookup"><span data-stu-id="ab39e-129">**States**</span></span>|<span data-ttu-id="ab39e-130">필요에 따라 특성의 해당 행에 있는 색이 나타내는 상태를 설명하는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-130">An optional column that describes what state the color in the corresponding row of attributes represents.</span></span> <span data-ttu-id="ab39e-131">**범례 표시** 확인란을 사용하여 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-131">Add or remove by using the **Show Legend** check box.</span></span>|  
|<span data-ttu-id="ab39e-132">**표본의**</span><span class="sxs-lookup"><span data-stu-id="ab39e-132">**Population**</span></span>|<span data-ttu-id="ab39e-133">전체 데이터 세트의 특성 배포를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-133">Displays the distribution of the attribute across the whole dataset.</span></span>|  
|<span data-ttu-id="ab39e-134">**예측 가능한 특성의 상태 열**</span><span class="sxs-lookup"><span data-stu-id="ab39e-134">**Column for states of predictable attribute**</span></span>|<span data-ttu-id="ab39e-135">각 행이 모델의 입력 특성에 해당하는 예측 가능한 열의 각 상태에 대한 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ab39e-135">Displays a column for each state of the predictable column, with each row corresponding to an input attribute in the model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab39e-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab39e-136">See Also</span></span>  
 <span data-ttu-id="ab39e-137">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ab39e-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="ab39e-138">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ab39e-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="ab39e-139">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="ab39e-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
