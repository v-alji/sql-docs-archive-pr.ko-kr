---
title: 리프 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738463"
---
# <a name="leaf-permissions-master-data-services"></a><span data-ttu-id="b3a55-102">리프 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b3a55-102">Leaf Permissions (Master Data Services)</span></span>
  <span data-ttu-id="b3a55-103">리프 권한은 엔터티의 모든 리프 멤버에 대한 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-103">Leaf permissions apply to the attribute values for all leaf members of an entity.</span></span>  
  
 <span data-ttu-id="b3a55-104">명시적 계층이 설정되지 않은 엔터티의 경우 **리프** 에 사용 권한을 할당하는 것은 엔터티에 사용 권한을 할당하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-104">For entities without explicit hierarchies enabled, assigning permission to **Leaf** is the same as assigning permission to the entity.</span></span>  
  
 <span data-ttu-id="b3a55-105">**참고:**</span><span class="sxs-lookup"><span data-stu-id="b3a55-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="b3a55-106">리프 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="b3a55-107">**이름** 및 **코드** 특성에 할당된 사용 권한은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="b3a55-108">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b3a55-108">Permission</span></span>|<span data-ttu-id="b3a55-109">설명</span><span class="sxs-lookup"><span data-stu-id="b3a55-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b3a55-110">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="b3a55-110">**Read-only**</span></span>|<span data-ttu-id="b3a55-111">리프 멤버가 표시되지만 사용자가 이를 추가, 제거 또는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-111">Leaf members are displayed but the user cannot add, remove, or change them.</span></span><br /><br /> <span data-ttu-id="b3a55-112">통합 멤버가 있는 경우 Name 및 Code가 표시되지만 사용자는 이를 추가, 제거 또는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-112">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="b3a55-113">**Update**</span><span class="sxs-lookup"><span data-stu-id="b3a55-113">**Update**</span></span>|<span data-ttu-id="b3a55-114">리프 멤버가 표시되고 사용자가 이를 추가, 제거 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-114">Leaf members are displayed and the user can add, remove, and change them.</span></span><br /><br /> <span data-ttu-id="b3a55-115">통합 멤버가 있는 경우 Name 및 Code가 표시되지만 사용자는 이를 추가, 제거 또는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-115">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="b3a55-116">**Deny**</span><span class="sxs-lookup"><span data-stu-id="b3a55-116">**Deny**</span></span>|<span data-ttu-id="b3a55-117">엔터티의 리프 멤버가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-117">Leaf members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="b3a55-118">특성 사용 권한</span><span class="sxs-lookup"><span data-stu-id="b3a55-118">Attribute Permissions</span></span>  
 <span data-ttu-id="b3a55-119">특성 사용 권한은 특정 엔터티의 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-119">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="b3a55-120">특성 사용 권한만 있는 사용자는 멤버를 추가하거나 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-120">Users with attribute permissions only cannot add or remove members.</span></span>  
  
|<span data-ttu-id="b3a55-121">사용 권한</span><span class="sxs-lookup"><span data-stu-id="b3a55-121">Permission</span></span>|<span data-ttu-id="b3a55-122">설명</span><span class="sxs-lookup"><span data-stu-id="b3a55-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b3a55-123">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="b3a55-123">**Read-only**</span></span>|<span data-ttu-id="b3a55-124">특성이 표시되지만 사용자가 특성 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-124">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="b3a55-125">**Update**</span><span class="sxs-lookup"><span data-stu-id="b3a55-125">**Update**</span></span>|<span data-ttu-id="b3a55-126">특성이 표시되고 사용자가 특성 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-126">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="b3a55-127">**Deny**</span><span class="sxs-lookup"><span data-stu-id="b3a55-127">**Deny**</span></span>|<span data-ttu-id="b3a55-128">특성이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-128">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="b3a55-129">참고: 이름 및 코드 특성에 대한 액세스를 명시적으로 거부할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-129">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="b3a55-130">예제</span><span class="sxs-lookup"><span data-stu-id="b3a55-130">Example</span></span>  
 <span data-ttu-id="b3a55-131">Product 엔터티에 대해 Subcategory 특성에 **업데이트** 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-131">For the Product entity, assign **Update** permission to Subcategory attribute.</span></span> <span data-ttu-id="b3a55-132">모든 다른 특성에 대한 사용 권한은 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-132">Deny permission to all other attributes.</span></span>  
  
|<span data-ttu-id="b3a55-133">이름</span><span class="sxs-lookup"><span data-stu-id="b3a55-133">Name</span></span>|<span data-ttu-id="b3a55-134">코드</span><span class="sxs-lookup"><span data-stu-id="b3a55-134">Code</span></span>|<span data-ttu-id="b3a55-135">Subcategory(업데이트)</span><span class="sxs-lookup"><span data-stu-id="b3a55-135">Subcategory (Update)</span></span>|  
|----------|----------|----------------------------|  
|<span data-ttu-id="b3a55-136">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="b3a55-136">Mountain-100</span></span>|<span data-ttu-id="b3a55-137">BK-M101</span><span class="sxs-lookup"><span data-stu-id="b3a55-137">BK-M101</span></span>|<span data-ttu-id="b3a55-138">{5}산악 자전거</span><span class="sxs-lookup"><span data-stu-id="b3a55-138">{5} Mountain Bikes</span></span>|  
|<span data-ttu-id="b3a55-139">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="b3a55-139">Mountain-100</span></span>|<span data-ttu-id="b3a55-140">BK-M201</span><span class="sxs-lookup"><span data-stu-id="b3a55-140">BK-M201</span></span>|<span data-ttu-id="b3a55-141">{5}산악 자전거</span><span class="sxs-lookup"><span data-stu-id="b3a55-141">{5} Mountain Bikes</span></span>|  
  
 <span data-ttu-id="b3a55-142">**탐색기**에서 Subcategory 열의 특성 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-142">In **Explorer**, you can update any attribute value in the Subcategory column.</span></span> <span data-ttu-id="b3a55-143">특성에 대한 사용 권한이 없는 경우에는 해당 특성이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-143">If you do not have permission to an attribute, the attribute is not displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3a55-144">이 예에서 Subcategory는 SubcategoryList 엔터티를 기반으로 하는 도메인 기반 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-144">In this example, Subcategory is a domain-based attribute, based on the SubcategoryList entity.</span></span> <span data-ttu-id="b3a55-145">Mountain-100에 대해 다른 Subcategory를 선택할 수 있지만 SubcategoryList 엔터티에서 멤버를 추가하거나 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3a55-145">You can select a different subcategory for Mountain-100 but you cannot add members to or delete members from the SubcategoryList entity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a55-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3a55-146">See Also</span></span>  
 <span data-ttu-id="b3a55-147">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b3a55-147">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="b3a55-148">[MDS(Master Data Services)&#41;&#40;통합 된 사용 권한](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b3a55-148">[Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="b3a55-149">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b3a55-149">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="b3a55-150">[멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b3a55-150">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="b3a55-151">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b3a55-151">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
