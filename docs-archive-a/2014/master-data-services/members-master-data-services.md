---
title: 멤버(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89d2edb21b58575dffc21d9a6470171251889cc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730816"
---
# <a name="members-master-data-services"></a><span data-ttu-id="228d4-102">멤버(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="228d4-102">Members (Master Data Services)</span></span>
  <span data-ttu-id="228d4-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버는 실제 마스터 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], members are the physical master data.</span></span> <span data-ttu-id="228d4-104">예를 들어, 멤버는 Product 엔터티의 Road-150 bike이거나 Customer 엔터티의 특정 고객일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-104">For example, a member can be a Road-150 bike in a Product entity or a specific customer in a Customer entity.</span></span>

## <a name="how-members-relate-to-other-model-objects"></a><span data-ttu-id="228d4-105">다른 모델 개체와 멤버의 관계</span><span class="sxs-lookup"><span data-stu-id="228d4-105">How Members Relate to Other Model Objects</span></span>
 <span data-ttu-id="228d4-106">멤버는 테이블의 행으로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-106">You can think of members as rows in a table.</span></span> <span data-ttu-id="228d4-107">관련 멤버는 엔터티에 포함되며 특성 값으로 각 멤버가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-107">Related members are contained in an entity, and each member is defined by attribute values.</span></span>

 <span data-ttu-id="228d4-108">이 예에서 테이블은 엔터티를 나타내고, 테이블의 행은 멤버를 나타내며, 테이블의 열은 특성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-108">In this example, the table represents an entity, the rows in the table represent members, and the columns in the table represent attributes.</span></span> <span data-ttu-id="228d4-109">각 셀은 특정 멤버의 특성 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-109">Each cell represents an attribute value for a specific member.</span></span>

 <span data-ttu-id="228d4-110">![테이블로 표시된 MDS(Master Data Services) 엔터티](../../2014/master-data-services/media/mds-conc-entity-table.gif "테이블로 표시된 MDS(Master Data Services) 엔터티")</span><span class="sxs-lookup"><span data-stu-id="228d4-110">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>

## <a name="member-types"></a><span data-ttu-id="228d4-111">멤버 유형</span><span class="sxs-lookup"><span data-stu-id="228d4-111">Member Types</span></span>
 <span data-ttu-id="228d4-112">리프 멤버, 통합 멤버 및 컬렉션 멤버로 세 가지 멤버 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-112">There are three types of members: leaf members, consolidated members, and collection members.</span></span>

 <span data-ttu-id="228d4-113">리프 멤버는 엔터티의 기본 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-113">Leaf members are the default members in an entity.</span></span>

-   <span data-ttu-id="228d4-114">파생 계층에서 멤버 유형은 리프 멤버뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-114">In derived hierarchies, leaf members are the only type of member.</span></span> <span data-ttu-id="228d4-115">한 엔터티의 리프 멤버가 다른 엔터티의 리프 멤버 부모로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-115">Leaf members from one entity are used as parents of leaf members from another entity.</span></span>

-   <span data-ttu-id="228d4-116">명시적 계층에서 리프 멤버는 최하위 수준이므로 자식을 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-116">In explicit hierarchies, leaf members are the lowest level and cannot have children.</span></span>

 <span data-ttu-id="228d4-117">통합 멤버는 엔터티에 명시적 계층 및 컬렉션을 사용할 수 있는 경우에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-117">Consolidated members exist only when explicit hierarchies and collections are enabled for the entity.</span></span>

-   <span data-ttu-id="228d4-118">파생 계층에는 통합 멤버가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-118">Derived hierarchies do not contain consolidated members.</span></span>

-   <span data-ttu-id="228d4-119">명시적 계층에서 통합 멤버는 계층 내 다른 멤버의 부모가 되거나 자식이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-119">In explicit hierarchies, consolidated members can be parents of other members within the hierarchy, or they can be children.</span></span>

## <a name="use-hierarchies-and-collections-to-organize-members"></a><span data-ttu-id="228d4-120">계층 및 컬렉션을 사용하여 멤버 구성</span><span class="sxs-lookup"><span data-stu-id="228d4-120">Use Hierarchies and Collections to Organize Members</span></span>
 <span data-ttu-id="228d4-121">계층과 컬렉션을 사용하여 보고 또는 분석을 위한 멤버를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-121">Hierarchies and collections can be used to group members for reporting or analysis.</span></span> <span data-ttu-id="228d4-122">자세한 내용은 [계층&#40;Master Data Services&#41;](hierarchies-master-data-services.md) 및 [컬렉션&#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="228d4-122">For more information, see [Hierarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>

## <a name="member-example"></a><span data-ttu-id="228d4-123">멤버 예</span><span class="sxs-lookup"><span data-stu-id="228d4-123">Member Example</span></span>
 <span data-ttu-id="228d4-124">다음 예의 각 멤버는 Name, Code, Subcategory, StandardCost, ListPrice 및 FilePhoto 특성 값으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-124">In the following example, each member is made up of a Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto attribute value.</span></span>

 <span data-ttu-id="228d4-125">![Bike 제품 엔터티 테이블](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike 제품 엔터티 테이블")</span><span class="sxs-lookup"><span data-stu-id="228d4-125">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="228d4-126">관련 작업</span><span class="sxs-lookup"><span data-stu-id="228d4-126">Related Tasks</span></span>

|<span data-ttu-id="228d4-127">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="228d4-127">Task Description</span></span>|<span data-ttu-id="228d4-128">항목</span><span class="sxs-lookup"><span data-stu-id="228d4-128">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="228d4-129">새 리프 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-129">Create a new leaf member.</span></span>|[<span data-ttu-id="228d4-130">리프 멤버 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-130">Create a Leaf Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|
|<span data-ttu-id="228d4-131">새 통합 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-131">Create a new consolidated member.</span></span>|[<span data-ttu-id="228d4-132">통합 멤버 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-132">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)|
|<span data-ttu-id="228d4-133">기존 멤버 또는 컬렉션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-133">Delete an existing member or collection.</span></span>|[<span data-ttu-id="228d4-134">멤버 또는 컬렉션 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-134">Delete a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="228d4-135">삭제된 멤버 또는 컬렉션을 다시 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-135">Reactivate a deleted member or collection.</span></span>|[<span data-ttu-id="228d4-136">멤버 또는 컬렉션 다시 활성화&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-136">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="228d4-137">멤버의 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-137">Update the attribute values of a member.</span></span>|[<span data-ttu-id="228d4-138">특성 유형 변경&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-138">Change the Attribute Type &#40;MDS Add-in for Excel&#41;</span></span>](microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|
|<span data-ttu-id="228d4-139">계층 내에서 멤버를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="228d4-139">Move members within a hierarchy.</span></span>|[<span data-ttu-id="228d4-140">계층 내에서 멤버를 이동 하 여 MDS(Master Data Services) &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-140">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="228d4-141">관련 내용</span><span class="sxs-lookup"><span data-stu-id="228d4-141">Related Content</span></span>

-   [<span data-ttu-id="228d4-142">MDS(Master Data Services) 개요</span><span class="sxs-lookup"><span data-stu-id="228d4-142">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)

-   [<span data-ttu-id="228d4-143">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-143">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)

-   [<span data-ttu-id="228d4-144">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-144">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="228d4-145">계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-145">Hierarchies &#40;Master Data Services&#41;</span></span>](hierarchies-master-data-services.md)

-   [<span data-ttu-id="228d4-146">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-146">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)

-   [<span data-ttu-id="228d4-147">리프 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-147">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)

-   [<span data-ttu-id="228d4-148">MDS(Master Data Services)&#41;&#40;통합 된 사용 권한</span><span class="sxs-lookup"><span data-stu-id="228d4-148">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)

-   [<span data-ttu-id="228d4-149">필터 연산자&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="228d4-149">Filter Operators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/filter-operators-master-data-services.md)


