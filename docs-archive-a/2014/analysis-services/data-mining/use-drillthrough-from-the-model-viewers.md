---
title: 모델 뷰어에서 드릴스루 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97bf20023009ec0e245126644d9fd38537182b2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735568"
---
# <a name="use-drillthrough-from-the-model-viewers"></a><span data-ttu-id="52f86-102">모델 뷰어에서 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="52f86-102">Use Drillthrough from the Model Viewers</span></span>
  <span data-ttu-id="52f86-103">모델 유형에 따라 데이터 마이닝 디자이너의 **마이닝 모델 뷰어** 탭에 있는 브라우저 뷰어에서 드릴스루를 사용하여 마이닝 모델에 사용된 사례를 탐색하거나 마이닝 구조의 추가 열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-103">Depending on the model type, you can use drillthrough from the browse viewers on the **Mining Model Viewer** tab of Data Mining Designer to explore the cases used in the mining model or to see additional columns in the mining structure.</span></span> <span data-ttu-id="52f86-104">모델의 패턴은 특정 사례에 직접 연결할 수 없으므로 대부분의 모델 유형에서 드릴스루를 지원하지 않지만 다음 모델 유형에서는 드릴스루를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-104">Although many model types do not support drillthrough because the patterns in the model cannot be directly linked to specific cases, the following model types do support drillthrough.</span></span>  
  
 <span data-ttu-id="52f86-105">모델에 드릴스루가 사용하도록 설정되어 있고 사용자에게 적절한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-105">Note that drillthrough must have been enabled on the model, and you must have the appropriate permissions.</span></span> <span data-ttu-id="52f86-106">또한 모델이 현재 처리되지 않은 상태인 경우에는 모델이 이전에 처리되었고 모델에 내용이 있는지 여부에 관계없이 드릴스루 옵션이 사용하지 않도록 설정될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-106">The drillthrough option might also be disabled if the model is in an unprocessed state, regardless of whether the model was previously processed and has content.</span></span> <span data-ttu-id="52f86-107">드릴스루를 사용하여 모델 사례 데이터를 검색하려면 구조 및 모델의 캐시가 최신 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-107">To retrieve model case data by using drillthrough, the cache of the structure and model must be current.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a><span data-ttu-id="52f86-108">Microsoft 트리 뷰어에서 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="52f86-108">Use drillthrough in the Microsoft Tree Viewer</span></span>  
  
1.  <span data-ttu-id="52f86-109">데이터 마이닝 디자이너에서 의사 결정 트리 모델을 선택하고 **모델 찾아보기** 를 선택하여 **Microsoft 트리 뷰어**에서 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-109">In Data Mining Designer, select a decision trees model, and select **Browse Model** to open the model in the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="52f86-110">SQL Server Management Studio에서 모델을 마우스 오른쪽 단추로 클릭하고 **찾아보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-110">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="52f86-111">트리 그래프에서 노드를 마우스 오른쪽 단추로 클릭하고 **드릴스루**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-111">Right-click any node in the tree graph, and select **Drill through**.</span></span>  
  
3.  <span data-ttu-id="52f86-112">**모델 열만** 또는 **모델 및 구조 열**옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-112">Select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="52f86-113">사용 권한이 없는 경우 옵션을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-113">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="52f86-114">**드릴스루** 대화 상자가 열리고 사례 데이터 및/또는 구조 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-114">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="52f86-115">또한 대화 상자의 제목 표시줄에 드릴스루 쿼리가 실행된 노드를 식별하는 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-115">The title bar of the dialog box also contains a description that identifies the node from which the drillthrough query was executed.</span></span>  
  
5.  <span data-ttu-id="52f86-116">결과의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모두 복사** 를 선택하여 결과를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-116">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a><span data-ttu-id="52f86-117">Microsoft 클러스터 뷰어에서 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="52f86-117">Use drillthrough in the Microsoft Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="52f86-118">데이터 마이닝 디자이너에서 클러스터링 모델을 선택하고 **모델 찾아보기** 를 선택하여 **Microsoft 클러스터 뷰어**에서 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-118">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="52f86-119">SQL Server Management Studio에서 모델을 마우스 오른쪽 단추로 클릭 하 고 **찾아보기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-119">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="52f86-120">**클러스터** 탭에서 노드를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-120">On the **Cluster** tab, right-click any node.</span></span>  
  
3.  <span data-ttu-id="52f86-121">**드릴스루**를 선택하고 **모델 열만** 또는 **모델 및 구조 열**옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-121">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="52f86-122">사용 권한이 없는 경우 옵션을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-122">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="52f86-123">**드릴스루** 대화 상자가 열리고 사례 데이터 및/또는 구조 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-123">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="52f86-124">또한 대화 상자의 제목 표시줄에 사례에 대한 클러스터를 식별하는 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-124">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="52f86-125">결과의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모두 복사** 를 선택하여 결과를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-125">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a><span data-ttu-id="52f86-126">Microsoft 연결 규칙 뷰어에서 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="52f86-126">Use drillthrough in the Microsoft Association Rules Viewer</span></span>  
  
1.  <span data-ttu-id="52f86-127">데이터 마이닝 디자이너에서 연결 모델을 선택하고 **모델 찾아보기** 를 선택하여 **Microsoft 연결 규칙 뷰어**에서 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-127">In Data Mining Designer, select an association model, and select **Browse Model** to open the model in the **Microsoft Association Rules Viewer**.</span></span> <span data-ttu-id="52f86-128">SQL Server Management Studio에서 모델을 마우스 오른쪽 단추로 클릭하고 **찾아보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-128">In SQL Server Management Studio, right-click the model, and select **Browse**</span></span>  
  
2.  <span data-ttu-id="52f86-129">**규칙** 탭에서 규칙을 나타내는 행을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-129">On the **Rules** tab, right-click any row that represents a rule.</span></span> <span data-ttu-id="52f86-130">**항목 집합** 탭에서 항목 집합이 포함된 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-130">On the **Itemsets** tab, click on any row that contains an itemset.</span></span>  
  
3.  <span data-ttu-id="52f86-131">**드릴스루**를 선택하고 **모델 열만** 또는 **모델 및 구조 열**옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-131">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="52f86-132">사용 권한이 없는 경우 옵션을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-132">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="52f86-133">**드릴스루** 대화 상자가 열리고 사례 데이터 및/또는 구조 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-133">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="52f86-134">또한 대화 상자의 제목 표시줄에 규칙 이름을 식별하는 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-134">The title bar of the dialog box also contains a description that identifies the rule name.</span></span>  
  
5.  <span data-ttu-id="52f86-135">결과의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모두 복사** 를 선택하여 전체 사례 결과를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-135">Right-click anywhere in the results and select **Copy All** to save the complete case results to the Clipboard.</span></span> <span data-ttu-id="52f86-136">**복사** 를 선택하여 선택한 사례만 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-136">You can also select **Copy** to copy just the selected case.</span></span> <span data-ttu-id="52f86-137">모델에 중첩 테이블 열이 포함되어 있는 경우 중첩 테이블 열의 이름만 붙여넣어지므로 각 사례의 중첩 테이블 열 내에 있는 데이터 값을 검색하려면 모델 콘텐츠에 대한 쿼리를 만들어야 합니다</span><span class="sxs-lookup"><span data-stu-id="52f86-137">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="52f86-138">Microsoft 시퀀스 클러스터 뷰어에서 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="52f86-138">Use drillthrough in the Microsoft Sequence Cluster Viewer</span></span>  
  
1.  <span data-ttu-id="52f86-139">데이터 마이닝 디자이너에서 클러스터링 모델을 선택하고 **모델 찾아보기** 를 선택하여 **Microsoft 클러스터 뷰어**에서 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-139">In Data Mining Designer, select a clustering model, and select **Browse Model** to open the model in the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="52f86-140">SQL Server Management Studio에서 모델을 마우스 오른쪽 단추로 클릭 하 고 **찾아보기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-140">In SQL Server Management Studio, right-click the model, and select **Browse**.</span></span>  
  
2.  <span data-ttu-id="52f86-141">**클러스터 다이어그램**탭에서 클러스터를 나타내는 노드를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-141">On the **Cluster Diagram tab**, right-click any node that represents a cluster.</span></span> <span data-ttu-id="52f86-142">**클러스터 프로필** 탭에서 클러스터 프로필 또는 전체 모델 모집단을 나타내는 클러스터의 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-142">From the **Cluster Profiles** tab, click anywhere in a cluster profile or in the cluster representing the total model population.</span></span>  
  
3.  <span data-ttu-id="52f86-143">**드릴스루**를 선택하고 **모델 열만** 또는 **모델 및 구조 열**옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-143">Select **Drill through**, and then select one of the following options: **Model Columns Only** or **Model and Structure Columns**.</span></span> <span data-ttu-id="52f86-144">사용 권한이 없는 경우 옵션을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-144">If you do not have permissions, an option might not be available.</span></span>  
  
4.  <span data-ttu-id="52f86-145">**드릴스루** 대화 상자가 열리고 사례 데이터 및/또는 구조 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-145">The **Drill Through** dialog box opens, displaying the case data and/or structure data.</span></span> <span data-ttu-id="52f86-146">또한 대화 상자의 제목 표시줄에 사례에 대한 클러스터를 식별하는 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-146">The title bar of the dialog box also contains a description that identifies the cluster for the cases.</span></span>  
  
5.  <span data-ttu-id="52f86-147">결과의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모두 복사** 를 선택하여 결과를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52f86-147">Right-click anywhere in the results and select **Copy All** to save the results to the Clipboard.</span></span> <span data-ttu-id="52f86-148">모델에 중첩 테이블 열이 포함되어 있는 경우 중첩 테이블 열의 이름만 붙여넣어지므로 각 사례의 중첩 테이블 열 내에 있는 데이터 값을 검색하려면 모델 콘텐츠에 대한 쿼리를 만들어야 합니다</span><span class="sxs-lookup"><span data-stu-id="52f86-148">If the model contains a nested table column, only the name of the nested table column is pasted; to retrieve the data values inside the nested table column for each case you must create a query on the model content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f86-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52f86-149">See Also</span></span>  
 <span data-ttu-id="52f86-150">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="52f86-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="52f86-151">[마이닝 모델에 대 한 드릴스루](drillthrough-on-mining-models.md) </span><span class="sxs-lookup"><span data-stu-id="52f86-151">[Drillthrough on Mining Models](drillthrough-on-mining-models.md) </span></span>  
 [<span data-ttu-id="52f86-152">마이닝 구조에서의 드릴스루</span><span class="sxs-lookup"><span data-stu-id="52f86-152">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
