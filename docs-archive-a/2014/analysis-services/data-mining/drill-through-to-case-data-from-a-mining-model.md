---
title: 마이닝 모델에서 사례 데이터로 드릴스루 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74129c44fc92984a767a79c579a495084ae68754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659728"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a><span data-ttu-id="161db-102">마이닝 모델에서 사례 데이터로 드릴스루</span><span class="sxs-lookup"><span data-stu-id="161db-102">Drill Through to Case Data from a Mining Model</span></span>
  <span data-ttu-id="161db-103">모델 사례로 드릴스루할 수 있도록 마이닝 모델을 구성한 경우 모델을 찾을 때 모델을 만드는 데 사용된 사례에 대한 세부 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-103">If a mining model has been configured to let you drill through to model cases, when you browse the model, you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="161db-104">또한 구조 사례로의 드릴스루를 허용하도록 기본 마이닝 구조를 구성했으며 적절한 권한이 있는 경우 마이닝 구조에서 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-104">Moreover, if the underlying mining structure has been configured to allow drillthrough to structure cases, and you have the appropriate permissions, you can return information from the mining structure.</span></span> <span data-ttu-id="161db-105">여기에는 마이닝 모델에 포함되지 않은 열이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-105">This can include columns that were not included in the mining model.</span></span>  
  
 <span data-ttu-id="161db-106">기본 데이터로의 드릴스루가 마이닝 구조에서는 허용되지 않지만 마이닝 모델에서는 허용되는 경우 마이닝 구조가 아닌 모델 사례에서 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-106">If the mining structure does not allow you to drill through to the underlying data, but the mining model does, you can view information from the model cases, but not from the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="161db-107">`AllowDrillthrough` 속성을 `True`로 설정하여 기존 마이닝 모델에 드릴스루 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-107">You can add the ability to drillthrough on an existing mining model by setting the property `AllowDrillthrough` to `True`.</span></span> <span data-ttu-id="161db-108">그러나 드릴스루를 사용하도록 설정한 후에는 모델을 다시 처리해야 사례 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-108">However, after you enable drillthrough, the model must be reprocessed before you can see the case data.</span></span> <span data-ttu-id="161db-109">자세한 내용은 [마이닝 모델에 드릴스루 사용](enable-drillthrough-for-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="161db-109">For more information, see [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="161db-110">사용하는 뷰어 유형에 따라 다음과 같은 방법으로 드릴스루할 노드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-110">Depending on the type of viewer you are using, you can select the node for drillthrough in the following ways:</span></span>  
  
|<span data-ttu-id="161db-111">뷰어 이름</span><span class="sxs-lookup"><span data-stu-id="161db-111">Viewer name</span></span>|<span data-ttu-id="161db-112">창 또는 탭 이름</span><span class="sxs-lookup"><span data-stu-id="161db-112">Pane or tab name</span></span>|<span data-ttu-id="161db-113">노드 선택</span><span class="sxs-lookup"><span data-stu-id="161db-113">Select node</span></span>|  
|-----------------|----------------------|-----------------|  
|<span data-ttu-id="161db-114">**Microsoft 트리 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-114">**Microsoft Tree Viewer**</span></span>|<span data-ttu-id="161db-115">**의사 결정 트리** 탭</span><span class="sxs-lookup"><span data-stu-id="161db-115">**Decision Tree** tab</span></span>|<span data-ttu-id="161db-116">트리 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-116">Click a tree node.</span></span><br /><br /> <span data-ttu-id="161db-117">**참고** `All`결과를 반환 하는 데 시간이 오래 걸릴 수 있으므로 노드에서 드릴스루를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="161db-117">**Note** Avoid using drillthrough on the `All` node, because it may take a very long time to return results.</span></span>|  
|<span data-ttu-id="161db-118">**Microsoft 클러스터 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-118">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="161db-119">**클러스터 다이어그램**</span><span class="sxs-lookup"><span data-stu-id="161db-119">**Cluster Diagram**</span></span>|<span data-ttu-id="161db-120">클러스터 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-120">Click a cluster node.</span></span>|  
|<span data-ttu-id="161db-121">**Microsoft 클러스터 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-121">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="161db-122">**클러스터 프로필**</span><span class="sxs-lookup"><span data-stu-id="161db-122">**Cluster Profiles**</span></span>|<span data-ttu-id="161db-123">클러스터 열의 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-123">Click anywhere in cluster column.</span></span>|  
|<span data-ttu-id="161db-124">**Microsoft 연결 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-124">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="161db-125">**규칙** 탭</span><span class="sxs-lookup"><span data-stu-id="161db-125">**Rules** tab</span></span>|<span data-ttu-id="161db-126">규칙 집합을 포함하는 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-126">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="161db-127">**Microsoft 연결 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-127">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="161db-128">**항목 집합** 탭</span><span class="sxs-lookup"><span data-stu-id="161db-128">**Itemsets** tab</span></span>|<span data-ttu-id="161db-129">항목 집합을 포함하는 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-129">Click a row that contains an itemset.</span></span>|  
|<span data-ttu-id="161db-130">**Microsoft 시퀀스 클러스터링 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-130">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="161db-131">**규칙** 탭</span><span class="sxs-lookup"><span data-stu-id="161db-131">**Rules** tab</span></span>|<span data-ttu-id="161db-132">규칙 집합을 포함하는 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-132">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="161db-133">**Microsoft 시퀀스 클러스터링 뷰어**</span><span class="sxs-lookup"><span data-stu-id="161db-133">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="161db-134">**항목 집합** 탭</span><span class="sxs-lookup"><span data-stu-id="161db-134">**Itemsets** tab</span></span>|<span data-ttu-id="161db-135">항목 집합을 포함하는 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-135">Click a row that contains an itemset.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="161db-136">일부 모델에서는 드릴스루를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-136">Some models cannot use drillthrough.</span></span> <span data-ttu-id="161db-137">드릴스루를 사용할 수 있는지 여부는 모델을 만드는 데 사용된 알고리즘에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="161db-137">The ability to use drillthrough depends on the algorithm that was used to create the model.</span></span> <span data-ttu-id="161db-138">드릴스루를 지원하는 마이닝 모델 유형 목록은 [드릴스루 쿼리&#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md)로 설정하여 기존 마이닝 모델에 드릴스루 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161db-138">For a list of the mining model types that support drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="161db-139">마이닝 모델에서 드릴스루 데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="161db-139">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="161db-140">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 마이닝 모델을 포함하는 마이닝 구조를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="161db-140">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the mining structure that contains the mining model you want.</span></span>  
  
2.  <span data-ttu-id="161db-141">데이터 마이닝 디자이너에서 **마이닝 모델 뷰어** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-141">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="161db-142">**마이닝 모델** 드롭다운 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-142">Select the model from the **Mining Model** drop-down list.</span></span>  
  
4.  <span data-ttu-id="161db-143">**뷰어** 드롭다운 목록에서 뷰어를 선택하고 특정 노드를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-143">Select a viewer from the **Viewer** drop-down list, and right-click the specific node.</span></span>  
  
5.  <span data-ttu-id="161db-144">**드릴스루**를 선택한 다음 **모델 열만**또는 **모델 및 구조 열** 을 선택하여 **드릴스루** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="161db-144">Select **Drill Through**, and then select either **Models Columns Only**, or **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="161db-145">데이터를 클립보드에 복사하려면 테이블에서 임의의 행을 마우스 오른쪽 단추로 클릭하고 **모두 복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161db-145">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161db-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="161db-146">See Also</span></span>  
 [<span data-ttu-id="161db-147">드릴스루 쿼리&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="161db-147">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
