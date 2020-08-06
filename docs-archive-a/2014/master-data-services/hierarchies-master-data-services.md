---
title: 계층(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 126a01c03134c6859426c09fda398408694795f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652179"
---
# <a name="hierarchies-master-data-services"></a><span data-ttu-id="cc8b6-102">계층(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cc8b6-102">Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="cc8b6-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 계층은 다음 작업에 사용할 수 있는 트리 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a hierarchy is a tree structure that you can use to:</span></span>

-   <span data-ttu-id="cc8b6-104">구성을 목적으로 유사한 멤버 그룹화</span><span class="sxs-lookup"><span data-stu-id="cc8b6-104">Group similar members for organizational purposes.</span></span>

-   <span data-ttu-id="cc8b6-105">보고 및 분석을 위해 멤버 통합 및 요약</span><span class="sxs-lookup"><span data-stu-id="cc8b6-105">Consolidate and summarize members for reporting and analysis.</span></span>

## <a name="what-hierarchies-contain"></a><span data-ttu-id="cc8b6-106">계층에 포함된 내용</span><span class="sxs-lookup"><span data-stu-id="cc8b6-106">What Hierarchies Contain</span></span>
 <span data-ttu-id="cc8b6-107">각 계층은 하나 이상의 엔터티에 속한 멤버를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-107">Each hierarchy contains members from one or more entities.</span></span> <span data-ttu-id="cc8b6-108">멤버가 추가, 변경 또는 삭제되면 모든 계층이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-108">When a member is added, changed, or deleted, all hierarchies are updated.</span></span> <span data-ttu-id="cc8b6-109">따라서 데이터가 모든 계층에서 정확하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-109">This ensures that the data is accurate in all hierarchies.</span></span> <span data-ttu-id="cc8b6-110">계층은 각 멤버가 한 번만 계산되도록 하는 데도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-110">Hierarchies also help ensure that each member is counted once and only once.</span></span>

 <span data-ttu-id="cc8b6-111">멤버의 하위 집합을 그룹화하려면 컬렉션 사용을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-111">If you want to create a grouping of a subset of members, consider using a collection.</span></span> <span data-ttu-id="cc8b6-112">자세한 내용은 [컬렉션&#40;Master Data Services&#41;](collections-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-112">For more information, see [Collections &#40;Master Data Services&#41;](collections-master-data-services.md).</span></span>

## <a name="kinds-of-hierarchies"></a><span data-ttu-id="cc8b6-113">계층의 종류</span><span class="sxs-lookup"><span data-stu-id="cc8b6-113">Kinds of Hierarchies</span></span>
 <span data-ttu-id="cc8b6-114">여러 계층을 만들어 다양한 방식으로 멤버를 보고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-114">You can create multiple hierarchies to view and organize your members in different ways.</span></span> <span data-ttu-id="cc8b6-115">다음을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-115">You can create:</span></span>

-   <span data-ttu-id="cc8b6-116">단일 엔터티에서 비정형 계층(명시적 계층이라고 함)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-116">Ragged hierarchies from a single entity, which are called explicit hierarchies.</span></span> <span data-ttu-id="cc8b6-117">자세한 내용은 [명시적 계층&#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-117">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>

-   <span data-ttu-id="cc8b6-118">엔터티와 해당 특성 간의 기존 관계를 기반으로 여러 엔터티에서 수준 기반 계층(파생 계층이라고 함)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-118">Level-based hierarchies from multiple entities, based on the existing relationships between entities and their attributes, which are called derived hierarchies.</span></span> <span data-ttu-id="cc8b6-119">자세한 내용은 [파생 계층&#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-119">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="cc8b6-120">계층의 모든 멤버는 같은 모델에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-120">All members in a hierarchy must be within the same model.</span></span>

## <a name="hierarchies-are-not-taxonomies"></a><span data-ttu-id="cc8b6-121">계층은 분류가 아님</span><span class="sxs-lookup"><span data-stu-id="cc8b6-121">Hierarchies Are Not Taxonomies</span></span>
 <span data-ttu-id="cc8b6-122">계층은 분류와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-122">A hierarchy is different from a taxonomy.</span></span> <span data-ttu-id="cc8b6-123">분류는 여러 특성을 동시에 사용하여 멤버를 구성하지만, 계층은 한 번에 하나의 특성을 사용하여 멤버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-123">A taxonomy organizes members by multiple attributes at the same time, while a hierarchy organizes members by one attribute at a time.</span></span> <span data-ttu-id="cc8b6-124">또한 분류는 같은 멤버를 여러 번 포함할 수 있지만, 계층은 멤버를 한 번만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-124">A taxonomy can include the same member multiple times, while a hierarchy includes a member only once.</span></span>

 <span data-ttu-id="cc8b6-125">예를 들어 분류에는 같은 자전거가 빨간색이기 때문에 한 번 포함되고 크기가 38이기 때문에 또 한 번 포함되는 식으로 분류에 두 번 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-125">For example, the same bike can be included in a taxonomy twice: once because it's red, and once because it's a size 38.</span></span> <span data-ttu-id="cc8b6-126">그러나 계층에서는 자전거가 한 번만 포함되므로 자전거를 색을 기준으로 표시할지 또는 크기를 기준으로 표시할지 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-126">In a hierarchy, the bike is included only once, so you must decide whether to show it in relation to its color or its size.</span></span>

## <a name="hierarchy-example"></a><span data-ttu-id="cc8b6-127">계층 예</span><span class="sxs-lookup"><span data-stu-id="cc8b6-127">Hierarchy Example</span></span>
 <span data-ttu-id="cc8b6-128">다음 예에서는 Product 멤버가 Subcategory 멤버로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-128">In the following example, product members are grouped by subcategory members.</span></span>

 <span data-ttu-id="cc8b6-129">![하위 범주로 그룹화된 계층 예제](../../2014/master-data-services/media/mds-conc-hierarchy.gif "하위 범주로 그룹화된 계층 예제")</span><span class="sxs-lookup"><span data-stu-id="cc8b6-129">![Hierarchy Grouped by Subcategory Example](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Hierarchy Grouped by Subcategory Example")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="cc8b6-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cc8b6-130">Related Tasks</span></span>

|<span data-ttu-id="cc8b6-131">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="cc8b6-131">Task Description</span></span>|<span data-ttu-id="cc8b6-132">항목</span><span class="sxs-lookup"><span data-stu-id="cc8b6-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="cc8b6-133">명시적 계층 및 컬렉션에 엔터티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-133">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="cc8b6-134">명시적 계층 및 컬렉션에 대해 엔터티를 사용 하도록 설정 &#40;MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-134">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="cc8b6-135">명시적 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-135">Create a explicit hierarchy.</span></span>|[<span data-ttu-id="cc8b6-136">명시적 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-136">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="cc8b6-137">파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-137">Create a derived hierarchy.</span></span>|[<span data-ttu-id="cc8b6-138">파생 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-138">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="cc8b6-139">기존 파생 계층의 수준을 숨기거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="cc8b6-139">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="cc8b6-140">파생 계층의 수준 숨기기 또는 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-140">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="cc8b6-141">관련 내용</span><span class="sxs-lookup"><span data-stu-id="cc8b6-141">Related Content</span></span>

-   [<span data-ttu-id="cc8b6-142">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-142">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="cc8b6-143">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-143">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="cc8b6-144">재귀 계층 구조&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-144">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="cc8b6-145">명시적 캡이 포함된 파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-145">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="cc8b6-146">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc8b6-146">Collections &#40;Master Data Services&#41;</span></span>](collections-master-data-services.md)


