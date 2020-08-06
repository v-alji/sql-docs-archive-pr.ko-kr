---
title: 파생 계층(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies
- hierarchies [Master Data Services], derived hierarchies
- derived hierarchies, about derived hierarchies
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92867f225a8f14e59cb9a519f174902d0739773a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661697"
---
# <a name="derived-hierarchies-master-data-services"></a><span data-ttu-id="4a9a9-102">파생 계층(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="4a9a9-102">Derived Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="4a9a9-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 파생 계층은 모델의 엔터티 간에 이미 있는 도메인 기반 특성 관계에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-103">A [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.</span></span>

 <span data-ttu-id="4a9a9-104">파생 계층을 만들어 모델의 기존 도메인 기반 특성 관계를 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-104">You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.</span></span>

## <a name="leaf-members-group-other-leaf-members"></a><span data-ttu-id="4a9a9-105">리프 멤버가 다른 리프 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-105">Leaf Members Group Other Leaf Members</span></span>
 <span data-ttu-id="4a9a9-106">파생 계층에서 한 엔터티의 리프 멤버가 다른 엔터티의 리프 멤버를 그룹화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-106">In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity.</span></span> <span data-ttu-id="4a9a9-107">파생 계층은 이러한 엔터티 간의 관계를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-107">A derived hierarchy is based on the relationship between these entities.</span></span> <span data-ttu-id="4a9a9-108">반면, 명시적 계층은 단일 엔터티만의 멤버를 기반으로 하며 지정하는 방법으로 구조화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-108">An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.</span></span>

 <span data-ttu-id="4a9a9-109">기본 데이터에 영향을 주지 않고 파생 계층의 구조를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-109">You can change the structure of a derived hierarchy without affecting the underlying data.</span></span> <span data-ttu-id="4a9a9-110">모델에 관계가 존재하는 한 파생 계층을 삭제해도 마스터 데이터에는 아무 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-110">As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="4a9a9-111">명시적 계층과 파생 계층</span><span class="sxs-lookup"><span data-stu-id="4a9a9-111">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="4a9a9-112">다음 표에서는 명시적 계층과 파생 계층의 몇 가지 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-112">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="4a9a9-113">명시적 계층</span><span class="sxs-lookup"><span data-stu-id="4a9a9-113">Explicit Hierarchies</span></span>|<span data-ttu-id="4a9a9-114">파생 계층</span><span class="sxs-lookup"><span data-stu-id="4a9a9-114">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="4a9a9-115">구조가 사용자에 의해 정의됨</span><span class="sxs-lookup"><span data-stu-id="4a9a9-115">Structure is defined by the user</span></span>|<span data-ttu-id="4a9a9-116">구조가 도메인 기반 특성 간의 관계에서 파생됨</span><span class="sxs-lookup"><span data-stu-id="4a9a9-116">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="4a9a9-117">단일 엔터티 멤버 포함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-117">Contains members from a single entity</span></span>|<span data-ttu-id="4a9a9-118">여러 엔터티 멤버 포함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-118">Contains members from multiple entities</span></span>|
|<span data-ttu-id="4a9a9-119">통합 멤버를 사용하여 다른 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-119">Uses consolidated members to group other members</span></span>|<span data-ttu-id="4a9a9-120">한 엔터티의 리프 멤버를 사용하여 다른 엔터티의 리프 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-120">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="4a9a9-121">비정형 가능</span><span class="sxs-lookup"><span data-stu-id="4a9a9-121">Can be ragged</span></span>|<span data-ttu-id="4a9a9-122">항상 일관된 수의 수준 포함</span><span class="sxs-lookup"><span data-stu-id="4a9a9-122">Always contains a consistent number of levels</span></span>|

## <a name="creating-a-variable-depth-hierarchy"></a><span data-ttu-id="4a9a9-123">가변 깊이 계층 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="4a9a9-123">Creating a Variable-Depth Hierarchy</span></span>
 <span data-ttu-id="4a9a9-124">가변 깊이 계층 구조를 만드는 두 가지 권장 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-124">There are two recommended ways to create a variable-depth hierarchy:</span></span>

-   <span data-ttu-id="4a9a9-125">모든 수준에 동일한 특성을 지정해야 하는 경우, 단일 엔터티를 만든 후 이 엔터티를 기반으로 하는 도메인 기반 특성을 사용해서 이 엔터티에 대해 재귀적 계층 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-125">If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.</span></span>

-   <span data-ttu-id="4a9a9-126">상위 수준에 리프 멤버에 대한 특성 집합 하나와 다른 특성 집합 하나를 설정해야 할 경우, 파생된 계층 구조에 대해 두 개의 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-126">If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy.</span></span> <span data-ttu-id="4a9a9-127">리프 엔터티에 대해 부모 엔터티를 기반으로 하는 도메인 기반 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-127">For the leaf entity, use a domain-based attribute that is based upon the parent entity.</span></span> <span data-ttu-id="4a9a9-128">부모 엔터티에 대해서는 해당 엔터티 자체를 기반으로 하는 도메인 기반 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-128">For the parent entity, use a domain-based attribute that is based upon itself.</span></span>

## <a name="derived-hierarchy-example"></a><span data-ttu-id="4a9a9-129">파생 계층 예</span><span class="sxs-lookup"><span data-stu-id="4a9a9-129">Derived Hierarchy Example</span></span>
 <span data-ttu-id="4a9a9-130">다음 예에서는 Product 엔터티의 리프 멤버가 Subcategory 엔터티의 리프 멤버로 그룹화된 후 Subcategory 엔터티의 리프 멤버가 Category 엔터티의 리프 멤버로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-130">In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity.</span></span> <span data-ttu-id="4a9a9-131">이 계층은 Product 엔터티에 Subcategory라는 도메인 기반 특성이 있고 Subcategory 엔터티에 Category라는 도메인 기반 특성이 있기 때문에 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-131">This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.</span></span>

 <span data-ttu-id="4a9a9-132">계층 구조는 멤버가 어떻게 그룹화되는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-132">The hierarchy structure shows how the members are grouped.</span></span> <span data-ttu-id="4a9a9-133">멤버 수가 가장 많은 엔터티가 맨 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-133">The entity with the most members is at the bottom.</span></span>

 <span data-ttu-id="4a9a9-134">![모델 구조에서 파생된 계층](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "모델 구조에서 파생된 계층")</span><span class="sxs-lookup"><span data-stu-id="4a9a9-134">![Hierarchy Derived from Model Structure](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hierarchy Derived from Model Structure")</span></span>

 <span data-ttu-id="4a9a9-135">파생 계층에서 Product와 Subcategory 간의 관계를 강조 표시한 다음 Subcategory와 Category 간의 관계를 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-135">In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category.</span></span> <span data-ttu-id="4a9a9-136">이 계층의 멤버를 보면 트리의 각 수준에 같은 엔터티의 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-136">When you view the members in this hierarchy, each level in the tree contains members from the same entity.</span></span>

 <span data-ttu-id="4a9a9-137">![Mountain Bike 파생 계층 예제](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike 파생 계층 예제")</span><span class="sxs-lookup"><span data-stu-id="4a9a9-137">![Mountain Bike Derived Hierarchy Example](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike Derived Hierarchy Example")</span></span>

 <span data-ttu-id="4a9a9-138">이 유형의 계층에서는 유효하지 않은 수준으로 멤버를 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-138">This type of hierarchy prevents you from moving a member to a level that is not valid.</span></span> <span data-ttu-id="4a9a9-139">예들 들어 하나의 Subcategory, Road Bikes에서 다른 Subcategory, Mountain Bikes로 Road-650 bike를 이동할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="4a9a9-139">For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes.</span></span> <span data-ttu-id="4a9a9-140">1 {Bikes}와 같은 Category 바로 아래로 Road-650을 이동할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-140">You cannot move Road-650 directly under a category, like 1 {Bikes}.</span></span> <span data-ttu-id="4a9a9-141">계층 트리에서 멤버를 이동할 때마다 이를 반영하여 해당 멤버의 도메인 기반 특성 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-141">Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.</span></span>

## <a name="notes"></a><span data-ttu-id="4a9a9-142">메모</span><span class="sxs-lookup"><span data-stu-id="4a9a9-142">Notes</span></span>
 <span data-ttu-id="4a9a9-143">파생 계층 트리의 모든 멤버가 코드순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-143">All members in a derived hierarchy tree are sorted by code.</span></span> <span data-ttu-id="4a9a9-144">정렬 순서는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-144">You cannot change the sort order.</span></span>

 <span data-ttu-id="4a9a9-145">멤버의 도메인 기반 특성이 비어 있거나 특성이 파생 계층에 사용되는 경우 해당 멤버는 계층에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-145">If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy.</span></span> <span data-ttu-id="4a9a9-146">특성을 채워야 하는 비즈니스 규칙을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-146">Create business rules to require attributes to be populated.</span></span> <span data-ttu-id="4a9a9-147">자세한 내용은 [특성 값 요구&#40;Master Data Services&#41;](require-attribute-values-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-147">For more information, see [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="4a9a9-148">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4a9a9-148">Related Tasks</span></span>

|<span data-ttu-id="4a9a9-149">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="4a9a9-149">Task Description</span></span>|<span data-ttu-id="4a9a9-150">항목</span><span class="sxs-lookup"><span data-stu-id="4a9a9-150">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="4a9a9-151">새 파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-151">Create a new derived hierarchy.</span></span>|[<span data-ttu-id="4a9a9-152">파생 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-152">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="4a9a9-153">기존 파생 계층의 수준을 숨기거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-153">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="4a9a9-154">파생 계층의 수준 숨기기 또는 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-154">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="4a9a9-155">기존 파생 계층의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-155">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="4a9a9-156">파생 계층 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-156">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="4a9a9-157">기존 파생 계층을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4a9a9-157">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="4a9a9-158">파생 계층 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-158">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="4a9a9-159">관련 내용</span><span class="sxs-lookup"><span data-stu-id="4a9a9-159">Related Content</span></span>

-   [<span data-ttu-id="4a9a9-160">도메인 기반 특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-160">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="4a9a9-161">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-161">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="4a9a9-162">재귀 계층 구조&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-162">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="4a9a9-163">명시적 캡이 포함된 파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-163">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="4a9a9-164">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4a9a9-164">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


