---
title: 사용 권한이 결정되는 방식(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ea3306b772224bc8602659c7e17e8dc1634f0d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652175"
---
# <a name="how-permissions-are-determined-master-data-services"></a><span data-ttu-id="64fbd-102">사용 권한이 결정되는 방식(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="64fbd-102">How Permissions Are Determined (Master Data Services)</span></span>
  <span data-ttu-id="64fbd-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 보안을 구성하는 가장 손쉬운 방법은 사용자가 멤버로 속한 그룹에 모델 개체 사용 권한을 할당하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], the simplest way to configure security is to assign model object permissions to a group that the user is a member of.</span></span>

 <span data-ttu-id="64fbd-104">다음과 같은 경우에는 보안 구성이 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-104">Security becomes more complex when:</span></span>

-   <span data-ttu-id="64fbd-105">모델 개체 사용 권한 및 계층 멤버 권한이 모두 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-105">Both model object and hierarchy member permissions are assigned.</span></span>

-   <span data-ttu-id="64fbd-106">사용자가 그룹에 속하며 사용 권한이 사용자와 그룹에 모두 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-106">The user belongs to groups and permission is assigned to both the user and groups.</span></span>

-   <span data-ttu-id="64fbd-107">사용자가 그룹에 속하며 사용 권한이 여러 그룹에 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-107">The user belongs to groups and permission is assigned to multiple groups.</span></span>

## <a name="permissions-assigned-to-a-single-group-or-user"></a><span data-ttu-id="64fbd-108">사용 권한이 단일 그룹 또는 사용자에게 할당된 경우</span><span class="sxs-lookup"><span data-stu-id="64fbd-108">Permissions assigned to a single group or user</span></span>
 <span data-ttu-id="64fbd-109">사용 권한을 단일 그룹이나 사용자에게 할당하는 경우 다음 워크플로에 따라 사용 권한이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-109">If you assign permissions to a single group or user, permissions are determined based on the following workflow.</span></span>

 <span data-ttu-id="64fbd-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span><span class="sxs-lookup"><span data-stu-id="64fbd-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span></span>

### <a name="step-1-effective-attribute-permissions-are-determined"></a><span data-ttu-id="64fbd-111">1단계: 유효 특성 사용 권한이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-111">Step 1: Effective attribute permissions are determined.</span></span>
 <span data-ttu-id="64fbd-112">다음 목록에서는 유효 특성 사용 권한이 결정되는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-112">The following list describes how effective attribute permissions are determined:</span></span>

-   <span data-ttu-id="64fbd-113">모델 개체에 할당된 사용 권한에 따라 사용자가 액세스할 수 있는 특성이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-113">Permissions assigned to model objects determine which attributes a user can access.</span></span>

-   <span data-ttu-id="64fbd-114">모든 모델 개체는 모델 구조의 상위 수준에서 가장 가까이 있는 개체의 사용 권한을 자동으로 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-114">All model objects automatically inherit permission from the closest object at a higher level in the model structure.</span></span>

-   <span data-ttu-id="64fbd-115">엔터티와 동일한 수준에 있는 개체는 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-115">Any objects at the same level as the entity are implicitly denied.</span></span>

-   <span data-ttu-id="64fbd-116">상위 수준의 개체에는 탐색 액세스 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-116">Any objects at a higher level are given navigational access.</span></span> <span data-ttu-id="64fbd-117">탐색 액세스에 대 한 자세한 내용은 [탐색 액세스 &#40;MDS(Master Data Services)&#41;](navigational-access-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64fbd-117">For more information about navigational access, see [Navigational Access &#40;Master Data Services&#41;](navigational-access-master-data-services.md).</span></span>

 <span data-ttu-id="64fbd-118">이 예에서는 엔터티에 **읽기** 전용 권한이 할당 되 고 해당 사용 권한은 모델 구조에서 하위 수준에 있는 해당 특성에 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-118">In this example, **Read-only** permission is assigned to an entity and that permission is inherited by its attribute, which is at a lower level in the model structure.</span></span> <span data-ttu-id="64fbd-119">모델은 이 엔터티 및 해당 특성에 대한 탐색 액세스 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-119">The model provides navigational access to this entity and its attribute.</span></span> <span data-ttu-id="64fbd-120">모델의 다른 엔터티는 명시적 사용 권한이 할당되지 않았으며 어떠한 사용 권한도 상속하지 않으므로 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-120">The other entity in the model has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="64fbd-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="64fbd-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>

### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a><span data-ttu-id="64fbd-122">2단계: 계층 멤버 권한이 할당된 경우 유효 멤버 권한이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-122">Step 2: If hierarchy member permissions are assigned, effective member permissions are determined.</span></span>
 <span data-ttu-id="64fbd-123">다음 목록에서는 유효 계층 멤버 권한이 결정되는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-123">The following list describes how effective hierarchy member permissions are determined:</span></span>

-   <span data-ttu-id="64fbd-124">계층 노드에 할당된 사용 권한에 따라 사용자가 액세스할 수 있는 멤버가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-124">Permissions assigned to hierarchy nodes determine which members a user can access.</span></span>

-   <span data-ttu-id="64fbd-125">계층의 모든 노드는 계층 구조의 상위 수준에서 가장 가까이 있는 개체의 사용 권한을 자동으로 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-125">All nodes in a hierarchy automatically inherit permission from the closest object at a higher level in the hierarchy structure.</span></span>

-   <span data-ttu-id="64fbd-126">동일한 수준에 있는 노드는 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-126">Any nodes at the same level are implicitly denied.</span></span>

-   <span data-ttu-id="64fbd-127">사용 권한이 할당되지 않은 상위 수준의 노드는 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-127">Any nodes at higher levels that do not have permissions assigned are implicitly denied.</span></span>

 <span data-ttu-id="64fbd-128">이 예에서는 계층의 한 노드에 **읽기 전용** 권한이 할당 되 고 해당 사용 권한은 계층 구조의 하위 수준에 있는 노드에 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-128">In this example, **Read-only** permission is assigned to one node of the hierarchy and that permission is inherited by a node at a lower level in the hierarchy structure.</span></span> <span data-ttu-id="64fbd-129">루트는 사용 권한이 할당되지 않았으므로 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-129">The root has no permission assigned, so it is implicitly denied.</span></span> <span data-ttu-id="64fbd-130">계층 구조의 다른 노드는 명시적 사용 권한이 할당되지 않았으며 어떠한 사용 권한도 상속하지 않으므로 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-130">The other node in the hierarchy structure has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="64fbd-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="64fbd-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span></span>

### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a><span data-ttu-id="64fbd-132">3단계: 특성 사용 권한과 멤버 권한의 교집합이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-132">Step 3: The intersection of attribute and member permissions is determined.</span></span>
 <span data-ttu-id="64fbd-133">유효 특성 사용 권한이 유효 멤버 권한과 다른 경우 각각의 개별 특성 값에 대해 사용 권한이 결정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-133">If the effective attribute permissions are different than the effective member permissions, permissions must be determined for each individual attribute value.</span></span> <span data-ttu-id="64fbd-134">자세한 내용은 [겹치는 모델 및 멤버 권한&#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64fbd-134">For more information, see [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).</span></span>

## <a name="permissions-assigned-to-multiple-groups"></a><span data-ttu-id="64fbd-135">사용 권한이 여러 그룹에 할당된 경우</span><span class="sxs-lookup"><span data-stu-id="64fbd-135">Permissions assigned to multiple groups</span></span>
 <span data-ttu-id="64fbd-136">사용자가 하나 이상의 그룹에 속하고 사용 권한이 사용자와 그룹에 모두 할당된 경우 워크플로가 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-136">If a user belongs to one or more groups and permissions are assigned to both the user and the groups, the workflow becomes more complex.</span></span>

 <span data-ttu-id="64fbd-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span><span class="sxs-lookup"><span data-stu-id="64fbd-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span></span>

 <span data-ttu-id="64fbd-138">이 경우 모델 개체 사용 권한과 계층 멤버 권한을 비교하기 전에 겹치는 사용자 및 그룹 권한을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64fbd-138">In this case, overlapping user and group permissions must be resolved before model object and hierarchy member permissions can be compared.</span></span> <span data-ttu-id="64fbd-139">자세한 내용은 [겹치는 사용자 및 그룹 권한&#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64fbd-139">For more information, see [Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64fbd-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64fbd-140">See Also</span></span>
 <span data-ttu-id="64fbd-141">겹치는 [사용자 및 그룹 권한&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [겹치는 모델 및 멤버 권한 &#40;MDS(Master Data Services)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md) MDS(Master Data Services) &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="64fbd-141">[Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span></span>


