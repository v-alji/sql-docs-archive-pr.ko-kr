---
title: 규칙 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0d86931865fd9352074669de93b14dacfc84537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647922"
---
# <a name="rules-tab-mining-model-viewer"></a><span data-ttu-id="1cf4f-102">규칙 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="1cf4f-102">Rules Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="1cf4f-103">연결 모델의 **규칙** 창을 사용하여 알고리즘이 데이터에서 추출한 규칙을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-103">Use the **Rules** pane in an association model to view the rules that the algorithm extracted from the data.</span></span> <span data-ttu-id="1cf4f-104">규칙은 항목이 어떻게 서로 관련되어 있는지를 설명하며 권장 항목을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-104">Rules describe how items are related to each other, and can be used to create recommendations.</span></span>  
  
 <span data-ttu-id="1cf4f-105">이 뷰어의 옵션을 사용하여 뷰어에 표시되는 규칙 수를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-105">You can use the options in the viewer to filter the number of rules that are displayed in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1cf4f-106">기본적으로 **최소 확률** 에 정의된 확률 임계값을 초과하는 규칙만 뷰어에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-106">By default, only the rules that are above the probability threshold defined in **Minimum probability** are displayed in the viewer.</span></span> <span data-ttu-id="1cf4f-107">규칙 출력의 확률 임계값은 모델이 만들어질 때 결정되기 때문에 뷰어를 사용하여 이 값을 작게 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-107">You cannot make this value any smaller by using the viewer, because the probability threshold for rule output is determined when the model is created.</span></span> <span data-ttu-id="1cf4f-108">자세한 내용은 [Microsoft 연결 알고리즘 기술 참조](data-mining/microsoft-association-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-108">For more information, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="1cf4f-109">**관련 항목:** [Microsoft 연결 알고리즘](data-mining/microsoft-association-algorithm.md), [Microsoft 연결 규칙 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="1cf4f-109">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="1cf4f-110">옵션</span><span class="sxs-lookup"><span data-stu-id="1cf4f-110">Options</span></span>  
 <span data-ttu-id="1cf4f-111">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-111">**Refresh viewer content**</span></span>  
 <span data-ttu-id="1cf4f-112">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-112">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="1cf4f-113">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-113">**Mining Model**</span></span>  
 <span data-ttu-id="1cf4f-114">현재 마이닝 구조에서 볼 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-114">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="1cf4f-115">관련 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-115">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="1cf4f-116">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-116">**Viewer**</span></span>  
 <span data-ttu-id="1cf4f-117">선택한 마이닝 모델을 보는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-117">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="1cf4f-118">각 마이닝 모델에 대한 사용자 지정 뷰어 또는 **Microsoft 일반 콘텐츠 트리 뷰어**를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-118">You can use the custom viewer for each mining model, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="1cf4f-119">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-119">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="1cf4f-120">**최소 확률**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-120">**Minimum probability**</span></span>  
 <span data-ttu-id="1cf4f-121">뷰어에 표시될 규칙에 필요한 최소 확률을 설정하려면 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-121">Change this value to set the minimum probability required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="1cf4f-122">확률 값을 늘리면 표시되는 규칙 수가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-122">Increasing the value for probability will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="1cf4f-123">**최소 중요도**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-123">**Minimum importance**</span></span>  
 <span data-ttu-id="1cf4f-124">뷰어에 표시될 규칙에 필요한 최소 중요도를 설정하려면 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-124">Change this value to set the minimum importance required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="1cf4f-125">중요도 값을 늘리면 표시되는 규칙 수가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-125">Increasing the value for importance will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="1cf4f-126">**규칙 필터**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-126">**Filter Rule**</span></span>  
 <span data-ttu-id="1cf4f-127">뷰어에 나타나는 규칙 수를 필터링할 문자열 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-127">Type a string value to filter the number of rules that appear in the viewer.</span></span>  
  
 <span data-ttu-id="1cf4f-128">.NET 정규식을 필터 조건으로 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-128">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="1cf4f-129">예를 들어 다음 식은 규칙의 왼쪽에 'Road Bottle Cage'가 포함된 모든 규칙을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-129">For example, the following expression returns all rules that contain 'Road Bottle Cage' on the left side of the rule:</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 <span data-ttu-id="1cf4f-130">필터 조건이 적용되는 것을 확인하려면 뷰를 새로 고쳐야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-130">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="1cf4f-131">**긴 이름 표시** 옵션을 설정하거나 해제하여 목록을 새로 고칠 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-131">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="1cf4f-132">기본적으로 필터 조건은 특성-값 조합의 전체 이름에 적용되므로 특성 이름만 보는 경우에는 필터 조건이 올바르게 적용되었는지가 명확하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-132">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="1cf4f-133">**표시** 드롭다운 목록을 사용하여 **특성 이름 및 값 표시**를 선택하고 항목 집합의 목록이 올바르게 필터링되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-133">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="1cf4f-134">**표시**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-134">**Show**</span></span>  
 <span data-ttu-id="1cf4f-135">규칙이 뷰어에 표시되는 방법을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-135">Adjust the way that the rule is displayed in the viewer.</span></span> <span data-ttu-id="1cf4f-136">다음 3가지 옵션 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-136">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="1cf4f-137">특성 이름 및 값 표시</span><span class="sxs-lookup"><span data-stu-id="1cf4f-137">Show the attribute name and value</span></span>  
  
-   <span data-ttu-id="1cf4f-138">특성 값만 표시</span><span class="sxs-lookup"><span data-stu-id="1cf4f-138">Show the attribute value only</span></span>  
  
-   <span data-ttu-id="1cf4f-139">특성 이름만 표시</span><span class="sxs-lookup"><span data-stu-id="1cf4f-139">Show the attribute name only</span></span>  
  
 <span data-ttu-id="1cf4f-140">**긴 이름 표시**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-140">**Show long name**</span></span>  
 <span data-ttu-id="1cf4f-141">마이닝 모델 콘텐츠에 나타나는 규칙의 전체 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-141">Show the full name of the rule as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="1cf4f-142">**최대 행 수**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-142">**Maximum rows**</span></span>  
 <span data-ttu-id="1cf4f-143">뷰어에 표시되는 규칙 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-143">Limit the number of rules that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="1cf4f-144">**Probability**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-144">**Probability**</span></span>  
 <span data-ttu-id="1cf4f-145">차트의 이 열에 각 규칙에 대한 확률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-145">This column in the chart displays the probability for each rule.</span></span>  
  
 <span data-ttu-id="1cf4f-146">열 머리글을 클릭하여 확률별로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-146">You can click the column heading to sort by probability.</span></span>  
  
 <span data-ttu-id="1cf4f-147">**중요도**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-147">**Importance**</span></span>  
 <span data-ttu-id="1cf4f-148">차트의 이 열에 각 규칙에 대한 중요도가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-148">This column in the chart displays the importance for each rule.</span></span>  
  
 <span data-ttu-id="1cf4f-149">열 머리글을 클릭하여 중요도별로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-149">You can click the column heading to sort by importance.</span></span>  
  
 <span data-ttu-id="1cf4f-150">**규칙**</span><span class="sxs-lookup"><span data-stu-id="1cf4f-150">**Rule**</span></span>  
 <span data-ttu-id="1cf4f-151">차트의 이 열에 **표시** 및 **긴 이름 표시**옵션을 사용하여 지정된 형식에 따라 각 규칙에 대한 텍스트 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-151">This column in the chart displays the text description for each rule, according to the format specified by using the options, **Show** and **Show long name**.</span></span>  
  
 <span data-ttu-id="1cf4f-152">열 머리글을 클릭하여 규칙의 텍스트별로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf4f-152">You can click the column heading to sort by the text of the rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf4f-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1cf4f-153">See Also</span></span>  
 <span data-ttu-id="1cf4f-154">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1cf4f-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="1cf4f-155">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="1cf4f-155">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="1cf4f-156">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="1cf4f-156">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
