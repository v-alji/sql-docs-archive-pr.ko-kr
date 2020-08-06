---
title: 항목 집합 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b99b62b01b196fd62e1ef264e530487018f6a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647956"
---
# <a name="itemsets-tab-mining-model-viewer"></a><span data-ttu-id="552ff-102">항목 집합 탭(마이닝 모델 뷰어)</span><span class="sxs-lookup"><span data-stu-id="552ff-102">Itemsets Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="552ff-103">**항목 집합** 창을 사용하여 연결 규칙 마이닝 모델에 자주 포함되는 항목 집합을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-103">You can use the **Itemsets** pane to view the frequent itemsets that an association rules mining model contains.</span></span> <span data-ttu-id="552ff-104">연결 모델에 많은 항목 집합이 포함될 수 있기 때문에 뷰어에 표시되는 항목 집합을 필터링하는 데 도움이 되는 컨트롤이 뷰어에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-104">Because an association model can contain many itemsets, controls are provided in the viewer to help you filter the itemsets that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="552ff-105">**관련 항목:** [Microsoft 연결 알고리즘](data-mining/microsoft-association-algorithm.md), [Microsoft 연결 규칙 뷰어를 사용하여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="552ff-105">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="552ff-106">옵션</span><span class="sxs-lookup"><span data-stu-id="552ff-106">Options</span></span>  
 <span data-ttu-id="552ff-107">**뷰어 내용 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="552ff-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="552ff-108">뷰어에서 마이닝 모델을 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="552ff-109">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="552ff-109">**Mining Model**</span></span>  
 <span data-ttu-id="552ff-110">현재 마이닝 구조에서 볼 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="552ff-111">관련 뷰어에서 마이닝 모델이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="552ff-112">**뷰어**</span><span class="sxs-lookup"><span data-stu-id="552ff-112">**Viewer**</span></span>  
 <span data-ttu-id="552ff-113">선택한 마이닝 모델을 보는 데 사용할 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="552ff-114">연결 모델에 대한 사용자 지정 뷰어 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 일반 콘텐츠 트리 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-114">You can use either the custom viewer for association models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="552ff-115">또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="552ff-116">**최소 지지도**</span><span class="sxs-lookup"><span data-stu-id="552ff-116">**Minimum support**</span></span>  
 <span data-ttu-id="552ff-117">뷰어에 나타나기 위해 항목 집합이 포함해야 할 최소 지지도를 설정하려면 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-117">Change this value to set the minimum support that an itemset must contain to appear in the viewer.</span></span> <span data-ttu-id="552ff-118">처음에 모델을 열 때 표시되는 기본값은 모델에서 계산되지만 이 값을 변경하여 더 많거나 적은 항목 집합을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-118">The default value that is displayed when you first open the model is calculated by the model, but you can change it to see more or fewer itemsets.</span></span>  
  
 <span data-ttu-id="552ff-119">**최소 항목 집합 크기**</span><span class="sxs-lookup"><span data-stu-id="552ff-119">**Minimum itemset size**</span></span>  
 <span data-ttu-id="552ff-120">항목 집합이 뷰어에 표시되기 위해 항목 집합에 포함되어야 하는 최소 항목 수를 설정하려면 이 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-120">Change this value to set the minimum number of items that must be included in an itemset before the itemset can be displayed in the viewer.</span></span>  
  
 <span data-ttu-id="552ff-121">**항목 집합 필터**</span><span class="sxs-lookup"><span data-stu-id="552ff-121">**Filter Itemset**</span></span>  
 <span data-ttu-id="552ff-122">뷰어에 나타나는 항목 집합 수를 필터링할 문자열 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-122">Type a string value to filter the number of itemsets that appear in the viewer.</span></span>  
  
 <span data-ttu-id="552ff-123">.NET 정규식을 필터 조건으로 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-123">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="552ff-124">예를 들어 다음 식은 'Road Bottle Cage'가 포함된 모든 항목 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-124">For example, the following expression returns all itemsets that contain 'Road Bottle Cage':</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 <span data-ttu-id="552ff-125">필터 조건이 적용되는 것을 확인하려면 뷰를 새로 고쳐야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-125">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="552ff-126">**긴 이름 표시** 옵션을 설정하거나 해제하여 목록을 새로 고칠 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-126">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="552ff-127">기본적으로 필터 조건은 특성-값 조합의 전체 이름에 적용되므로 특성 이름만 보는 경우에는 필터 조건이 올바르게 적용되었는지가 명확하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-127">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="552ff-128">**표시** 드롭다운 목록을 사용하여 **특성 이름 및 값 표시**를 선택하고 항목 집합의 목록이 올바르게 필터링되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-128">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="552ff-129">**표시**</span><span class="sxs-lookup"><span data-stu-id="552ff-129">**Show**</span></span>  
 <span data-ttu-id="552ff-130">뷰어에 항목 집합이 표시되는 방법을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-130">Adjust how the itemset is displayed in the viewer.</span></span> <span data-ttu-id="552ff-131">다음 3가지 옵션 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-131">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="552ff-132">특성 이름 및 값 표시</span><span class="sxs-lookup"><span data-stu-id="552ff-132">Show attribute name and value</span></span>  
  
-   <span data-ttu-id="552ff-133">특성 값만 표시</span><span class="sxs-lookup"><span data-stu-id="552ff-133">Show attribute value only</span></span>  
  
-   <span data-ttu-id="552ff-134">특성 이름만 표시</span><span class="sxs-lookup"><span data-stu-id="552ff-134">Show attribute name only</span></span>  
  
 <span data-ttu-id="552ff-135">이 옵션은 모델을 다시 쿼리하지 않으며, 표시되는 특성 또는 값만 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-135">Note that this option does not requery the model; it only filters the attributes or values that are displayed.</span></span>  
  
 <span data-ttu-id="552ff-136">**긴 이름 표시**</span><span class="sxs-lookup"><span data-stu-id="552ff-136">**Show long name**</span></span>  
 <span data-ttu-id="552ff-137">마이닝 모델 콘텐츠에 나타나는 항목 집합의 전체 이름을 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-137">Select this option to display the full name of the itemset as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="552ff-138">**최대 행 수**</span><span class="sxs-lookup"><span data-stu-id="552ff-138">**Maximum rows**</span></span>  
 <span data-ttu-id="552ff-139">뷰어에 표시되는 항목 집합 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-139">Limit the number of itemsets that are displayed in the viewer.</span></span> <span data-ttu-id="552ff-140">기본적으로 항목 집합은 지지도를 기준으로 내림차순으로 정렬되므로 이 값을 낮추면 가장 일반적인 항목 집합으로 목록이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-140">By default, itemsets are ordered by support in descending order, so lowering this value restricts the list to the most common itemsets.</span></span>  
  
 <span data-ttu-id="552ff-141">**지원**</span><span class="sxs-lookup"><span data-stu-id="552ff-141">**Support**</span></span>  
 <span data-ttu-id="552ff-142">각 항목 집합에 대한 지지도를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-142">Displays the support for each itemset.</span></span>  
  
 <span data-ttu-id="552ff-143">**크기**</span><span class="sxs-lookup"><span data-stu-id="552ff-143">**Size**</span></span>  
 <span data-ttu-id="552ff-144">각 항목 집합에 있는 항목 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-144">Displays the number of items that exist in each itemset.</span></span>  
  
 <span data-ttu-id="552ff-145">**항목 집합**</span><span class="sxs-lookup"><span data-stu-id="552ff-145">**Itemset**</span></span>  
 <span data-ttu-id="552ff-146">각 항목 집합에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-146">Displays the description of each itemset.</span></span> <span data-ttu-id="552ff-147">기본적으로 항목 집합은 특성 및 값의 쉼표로 구분된 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-147">By default, itemsets are presented as a comma-delimited list of attributes and their values.</span></span> <span data-ttu-id="552ff-148">**표시** 옵션을 사용하여 이러한 항목이 표시되는 방법을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552ff-148">You can change the way they are displayed by using the **Show** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552ff-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="552ff-149">See Also</span></span>  
 <span data-ttu-id="552ff-150">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="552ff-150">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="552ff-151">[마이닝 모델 뷰어 &#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="552ff-151">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="552ff-152">데이터 마이닝 모델 뷰어</span><span class="sxs-lookup"><span data-stu-id="552ff-152">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
