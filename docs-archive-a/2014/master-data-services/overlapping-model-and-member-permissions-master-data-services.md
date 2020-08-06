---
title: 겹치는 모델 및 멤버 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec5f4019f25a777e4c70433bd9a7e72fca2277e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647079"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a><span data-ttu-id="e3dd8-102">겹치는 모델 및 멤버 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e3dd8-102">Overlapping Model and Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="e3dd8-103">멤버에 할당된 사용 권한과 모델 개체에 할당된 사용 권한이 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-103">Permission assigned to a member can overlap with permission assigned to a model object.</span></span> <span data-ttu-id="e3dd8-104">사용 권한이 겹치면 보다 제한적인 사용 권한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-104">When overlaps occur, the more restrictive permission takes effect.</span></span>  
  
 <span data-ttu-id="e3dd8-105">멤버의 사용 권한이 해당 모델 개체와 다른 경우 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-105">If a member has permission that is different than its corresponding model object, the following rules apply:</span></span>  
  
-   <span data-ttu-id="e3dd8-106">**거부** 는 다른 모든 사용 권한을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-106">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="e3dd8-107">**읽기 전용은** **업데이트**를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-107">**Read-only** overrides **Update**.</span></span>  
  
 <span data-ttu-id="e3dd8-108">다음 이미지는 특성 사용 권한이 멤버 권한과 다를 경우 개별 특성 값에 적용되는 사용 권한을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-108">The following image shows which permissions take effect on an individual attribute value when attribute permissions are different than member permissions.</span></span>  
  
 <span data-ttu-id="e3dd8-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e3dd8-110">예 1</span><span class="sxs-lookup"><span data-stu-id="e3dd8-110">Example 1</span></span>  
 <span data-ttu-id="e3dd8-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span></span>  
  
 <span data-ttu-id="e3dd8-112">**모델** 탭의 Product 엔터티에는 **업데이트** 권한이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-112">On the **Models** tab, the Product entity has **Update** permission assigned.</span></span> <span data-ttu-id="e3dd8-113">엔터티의 모든 특성은 해당 사용 권한을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-113">All attributes in the entity inherit that permission.</span></span>  
  
 <span data-ttu-id="e3dd8-114">**계층 멤버** 탭의 파생 계층에 있는 Mountain Bikes 하위 범주 노드에는 **업데이트** 권한이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-114">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="e3dd8-115">결과: **탐색기**에서 사용자에게는 Mountain Bikes 노드에 있는 모든 멤버의 모든 특성 값에 대한 **업데이트** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-115">Result: In **Explorer**, the user has **Update** permission to all attribute values for all members in the Mountain Bikes node.</span></span> <span data-ttu-id="e3dd8-116">모든 다른 멤버와 특성은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-116">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="e3dd8-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="e3dd8-118">예제 2</span><span class="sxs-lookup"><span data-stu-id="e3dd8-118">Example 2</span></span>  
 <span data-ttu-id="e3dd8-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span></span>  
  
 <span data-ttu-id="e3dd8-120">**모델** 탭의 하위 범주 특성에는 **업데이트** 권한이 할당되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-120">On the **Models** tab, the Subcategory attribute has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="e3dd8-121">**계층 멤버** 탭의 파생 계층에 있는 산악 자전거 하위 범주 노드에는 **읽기** 전용 권한이 명시적으로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-121">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy is explicitly assigned **Read-only** permission.</span></span>  
  
 <span data-ttu-id="e3dd8-122">결과: **탐색기**에서 사용자에 게 산악 자전거 노드의 멤버에 대 한 하위 범주 특성 값에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-122">Result: In **Explorer**, the user has **Read-only** permission to the Subcategory attribute values for the members in the Mountain Bikes node.</span></span> <span data-ttu-id="e3dd8-123">모든 다른 멤버와 특성은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-123">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="e3dd8-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="e3dd8-125">예제 3</span><span class="sxs-lookup"><span data-stu-id="e3dd8-125">Example 3</span></span>  
 <span data-ttu-id="e3dd8-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span></span>  
  
 <span data-ttu-id="e3dd8-127">**모델** 탭의 하위 범주 특성에는 **읽기** 전용 권한이 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-127">On the **Models** tab, the Subcategory attribute has **Read-only** permission assigned.</span></span>  
  
 <span data-ttu-id="e3dd8-128">**계층 멤버** 탭의 파생 계층에 있는 Mountain Bikes 하위 범주 노드에는 **업데이트** 권한이 명시적으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-128">On the **Hierarchy Members** tab, the Mountain Bikes subcategory in a derived hierarchy is explicitly assigned **Update** permission.</span></span>  
  
 <span data-ttu-id="e3dd8-129">결과: **탐색기**에서 사용자에 게는 특성 값에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-129">Result: In **Explorer**, the user has **Read-only** permission to the attribute values.</span></span> <span data-ttu-id="e3dd8-130">모든 다른 멤버와 특성은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="e3dd8-130">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="e3dd8-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="e3dd8-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3dd8-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3dd8-132">See Also</span></span>  
 <span data-ttu-id="e3dd8-133">[MDS(Master Data Services) &#40;사용 권한을 결정 하는 방법&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e3dd8-133">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="e3dd8-134">겹치는 사용자 및 그룹 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e3dd8-134">Overlapping User and Group Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
