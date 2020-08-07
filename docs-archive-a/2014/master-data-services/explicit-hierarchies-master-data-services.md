---
title: 명시적 계층(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, about explicit hierarchies
- hierarchies [Master Data Services], explicit hierarchies
- explicit hierarchies
ms.assetid: e6f44e37-e1f0-4c38-a816-1935a856d5a4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f37f341dc2c003683e696f2767a6b644047d5a0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731835"
---
# <a name="explicit-hierarchies-master-data-services"></a><span data-ttu-id="bad11-102">명시적 계층(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bad11-102">Explicit Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="bad11-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 명시적 계층은 지정한 방법으로 단일 엔터티의 멤버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], an explicit hierarchy organizes members from a single entity in any way you specify.</span></span> <span data-ttu-id="bad11-104">구조는 비정형일 수 있으며 파생 계층과 달리 명시적 계층은 도메인 기반 특성 관계를 기반으로 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-104">The structure can be ragged and unlike derived hierarchies, explicit hierarchies are not based on domain-based attribute relationships.</span></span>

## <a name="consolidated-members-group-other-members"></a><span data-ttu-id="bad11-105">통합 멤버가 다른 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="bad11-105">Consolidated Members Group Other Members</span></span>
 <span data-ttu-id="bad11-106">명시적 계층에서는 다른 멤버의 그룹화를 위해 만든 통합 멤버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-106">An explicit hierarchy uses consolidated members that you create for the purpose of grouping other members.</span></span> <span data-ttu-id="bad11-107">이러한 통합 멤버는 한 번에 하나의 명시적 계층에만 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-107">These consolidated members can belong to only one explicit hierarchy at a time.</span></span> <span data-ttu-id="bad11-108">명시적 계층에는 연결된 엔터티의 모든 리프 멤버도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-108">An explicit hierarchy also includes all of the leaf members from the associated entity.</span></span>

 <span data-ttu-id="bad11-109">명시적 계층은 비정형일 수 있습니다. 즉, 계층이 동시에 다른 수준에서 끝날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-109">An explicit hierarchy can be ragged, which means that the hierarchy can end at different levels simultaneously.</span></span> <span data-ttu-id="bad11-110">각 통합 멤버는 통합 및 리프 멤버를 무제한 포함할 수도 있고 하나도 포함하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-110">Each consolidated member can have an unlimited number of consolidated and leaf members underneath, or can have none.</span></span> <span data-ttu-id="bad11-111">또한 리프 멤버는 단일 통합 멤버에 속할 수도 있고 여러 수준의 통합 멤버에 속할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-111">The leaf members can be under a single consolidated member or under multiple levels of consolidated members.</span></span>

> [!NOTE]
>  <span data-ttu-id="bad11-112">명시적 계층을 만들려면 먼저 엔터티가 명시적 계층을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-112">Before you can create an explicit hierarchy, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="bad11-113">자세한 내용은 [&#41;MDS(Master Data Services) &#40;명시적 계층 및 컬렉션에 엔터티 사용 ](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bad11-113">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>

## <a name="types-of-explicit-hierarchies"></a><span data-ttu-id="bad11-114">명시적 계층 유형</span><span class="sxs-lookup"><span data-stu-id="bad11-114">Types of Explicit Hierarchies</span></span>
 <span data-ttu-id="bad11-115">명시적 계층에는 필수 계층과 필수가 아닌 계층의 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-115">There are two types of explicit hierarchies: mandatory and non-mandatory.</span></span>

### <a name="mandatory-explicit-hierarchy"></a><span data-ttu-id="bad11-116">필수 명시적 계층</span><span class="sxs-lookup"><span data-stu-id="bad11-116">Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="bad11-117">필수 명시적 계층은 계층 트리의 모든 리프 멤버를 포함해야 하는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-117">A mandatory explicit hierarchy is a hierarchy in which all leaf members must be included in the hierarchy tree.</span></span> <span data-ttu-id="bad11-118">기본적으로 모든 멤버는 트리의 루트에 포함되지만</span><span class="sxs-lookup"><span data-stu-id="bad11-118">By default, all members are included at the root of the tree.</span></span> <span data-ttu-id="bad11-119">필요에 따라 멤버를 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-119">You can rearrange the members as needed.</span></span>

### <a name="non-mandatory-explicit-hierarchy"></a><span data-ttu-id="bad11-120">필수가 아닌 명시적 계층</span><span class="sxs-lookup"><span data-stu-id="bad11-120">Non-Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="bad11-121">필수가 아닌 명시적 계층은 모든 리프 멤버가 시스템에서 만든 **사용 안 함** 노드에 있는 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-121">A non-mandatory explicit hierarchy is a hierarchy in which all leaf members are in a system-created **Unused** node.</span></span> <span data-ttu-id="bad11-122">필요에 따라 이 노드에서 멤버를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-122">You can move members out of this node as you need them.</span></span> <span data-ttu-id="bad11-123">나머지 멤버는 **사용 안 함** 노드에 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-123">The rest of the members can remain in the **Unused** node.</span></span>

 <span data-ttu-id="bad11-124">필수가 아닌 명시적 계층을 사용하는 경우 이 계층에서 수행된 보고나 분석은 필수 계층에서 수행된 보고나 분석과 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-124">When you use non-mandatory explicit hierarchies, any reporting or analysis done on the hierarchy may not match reporting or analysis done on mandatory hierarchies.</span></span>

## <a name="rules"></a><span data-ttu-id="bad11-125">규칙</span><span class="sxs-lookup"><span data-stu-id="bad11-125">Rules</span></span>
 <span data-ttu-id="bad11-126">필수 명시적 계층과 필수가 아닌 명시적 계층 모두에 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-126">The following rules apply to explicit hierarchies (both mandatory and non-mandatory).</span></span>

-   <span data-ttu-id="bad11-127">각 리프 멤버는 계층에 한 번만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-127">Each leaf member can be included in the hierarchy only once.</span></span>

-   <span data-ttu-id="bad11-128">통합 멤버는 모두 계층에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-128">All consolidated members must be included in a hierarchy.</span></span>

-   <span data-ttu-id="bad11-129">통합 멤버는 둘 이상의 명시적 계층에 속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-129">Consolidated members cannot be in more than one explicit hierarchy.</span></span>

-   <span data-ttu-id="bad11-130">계층 트리의 통합 멤버 아래에는 리프 멤버가 없어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-130">Consolidated members in the hierarchy tree do not have to contain leaf members underneath them.</span></span>

-   <span data-ttu-id="bad11-131">명시적 계층을 삭제하면 해당 계층에 사용된 모든 통합 멤버가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-131">If you delete an explicit hierarchy, all consolidated members that were used in the hierarchy are deleted.</span></span>

-   <span data-ttu-id="bad11-132">명시적 계층에 속한 통합 멤버를 삭제하면 해당 통합 멤버로 그룹화된 모든 리프 멤버가 루트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-132">If you delete a consolidated member that was in an explicit hierarchy, all leaf members that were grouped by that consolidated member are moved to the root.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="bad11-133">명시적 계층과 파생 계층</span><span class="sxs-lookup"><span data-stu-id="bad11-133">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="bad11-134">다음 표에서는 명시적 계층과 파생 계층의 몇 가지 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-134">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="bad11-135">명시적 계층</span><span class="sxs-lookup"><span data-stu-id="bad11-135">Explicit Hierarchies</span></span>|<span data-ttu-id="bad11-136">파생 계층</span><span class="sxs-lookup"><span data-stu-id="bad11-136">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="bad11-137">구조가 사용자에 의해 정의됨</span><span class="sxs-lookup"><span data-stu-id="bad11-137">Structure is defined by the user</span></span>|<span data-ttu-id="bad11-138">구조가 도메인 기반 특성 간의 관계에서 파생됨</span><span class="sxs-lookup"><span data-stu-id="bad11-138">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="bad11-139">단일 엔터티 멤버 포함</span><span class="sxs-lookup"><span data-stu-id="bad11-139">Contains members from a single entity</span></span>|<span data-ttu-id="bad11-140">여러 엔터티 멤버 포함</span><span class="sxs-lookup"><span data-stu-id="bad11-140">Contains members from multiple entities</span></span>|
|<span data-ttu-id="bad11-141">통합 멤버를 사용하여 다른 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="bad11-141">Uses consolidated members to group other members</span></span>|<span data-ttu-id="bad11-142">한 엔터티의 리프 멤버를 사용하여 다른 엔터티의 리프 멤버를 그룹화함</span><span class="sxs-lookup"><span data-stu-id="bad11-142">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="bad11-143">비정형 가능</span><span class="sxs-lookup"><span data-stu-id="bad11-143">Can be ragged</span></span>|<span data-ttu-id="bad11-144">항상 일관된 수의 수준 포함</span><span class="sxs-lookup"><span data-stu-id="bad11-144">Always contains a consistent number of levels</span></span>|

## <a name="explicit-hierarchy-example"></a><span data-ttu-id="bad11-145">명시적 계층 예</span><span class="sxs-lookup"><span data-stu-id="bad11-145">Explicit Hierarchy Example</span></span>
 <span data-ttu-id="bad11-146">다음 예의 Product 엔터티에는 BK-M101 {Mountain-100}, BK-M201 {Mountain-200}, BK-M301 {Mountain-300}, BK-R150 {Road-150}, BK-R450 {Road-450} 및 BK-R650 {Road-650} 리프 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-146">In the following example, the Product entity contains these leaf members: BK-M101 {Mountain-100}, BK-M201 {Mountain-200}, BK-M301 {Mountain-300}, BK-R150 {Road-150}, BK-R450 {Road-450}, and BK-R650 {Road-650}.</span></span>

 <span data-ttu-id="bad11-147">이러한 리프 멤버를 특정 통합 지점에서 요약하려면 Product 엔터티 내에 통합 멤버를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-147">To summarize these leaf members at specific consolidation points, you can create consolidated members in the Product entity.</span></span> <span data-ttu-id="bad11-148">계층 트리에서 리프 멤버를 요약할 수준에 통합 멤버를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-148">Insert the consolidated members at levels in the hierarchy tree where you want to summarize the leaf members.</span></span> <span data-ttu-id="bad11-149">통합 멤버를 삽입할 수 있는 위치에 대한 제한은 없지만 각 멤버(리프 또는 통합)를 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-149">There is no limitation on where you insert your consolidated members; however, each member (leaf or consolidated) can be used only once.</span></span>

 <span data-ttu-id="bad11-150">![Mountain Bike 명시적 계층 예제](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "Mountain Bike 명시적 계층 예제")</span><span class="sxs-lookup"><span data-stu-id="bad11-150">![Mountain Bike Explicit Hierarchy Example](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "Mountain Bike Explicit Hierarchy Example")</span></span>

 <span data-ttu-id="bad11-151">통합 멤버를 사용하여 원하는 수준에서 멤버를 그룹화하고, 리프 및 통합 멤버를 원하는 순서대로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-151">Consolidated members can be used to group members at any level, and leaf and consolidated members are sorted in the order you determine.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="bad11-152">관련 작업</span><span class="sxs-lookup"><span data-stu-id="bad11-152">Related Tasks</span></span>

|<span data-ttu-id="bad11-153">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="bad11-153">Task Description</span></span>|<span data-ttu-id="bad11-154">항목</span><span class="sxs-lookup"><span data-stu-id="bad11-154">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="bad11-155">명시적 계층 및 컬렉션에 엔터티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-155">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="bad11-156">명시적 계층 및 컬렉션에 대해 엔터티를 사용 하도록 설정 &#40;MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-156">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="bad11-157">새 명시적 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-157">Create a new explicit hierarchy.</span></span>|[<span data-ttu-id="bad11-158">명시적 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-158">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="bad11-159">기존 명시적 계층의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-159">Change the name of an existing explicity hierarchy.</span></span>|[<span data-ttu-id="bad11-160">명시적 계층 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-160">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="bad11-161">기존 명시적 계층을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bad11-161">Delete an existing explicit hierarchy.</span></span>|[<span data-ttu-id="bad11-162">명시적 계층 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-162">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="bad11-163">관련 내용</span><span class="sxs-lookup"><span data-stu-id="bad11-163">Related Content</span></span>

-   [<span data-ttu-id="bad11-164">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-164">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="bad11-165">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bad11-165">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


