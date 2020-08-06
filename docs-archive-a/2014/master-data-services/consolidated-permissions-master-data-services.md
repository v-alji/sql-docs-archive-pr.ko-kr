---
title: 통합 사용 권한 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4c93e74acc84d6e742139263bedc011c4028efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661705"
---
# <a name="consolidated-permissions-master-data-services"></a><span data-ttu-id="d2f10-102">통합 사용 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d2f10-102">Consolidated Permissions (Master Data Services)</span></span>
  <span data-ttu-id="d2f10-103">통합 사용 권한은 엔터티의 모든 통합 멤버에 대한 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-103">Consolidated permissions apply to the attribute values for all consolidated members of an entity.</span></span>  
  
 <span data-ttu-id="d2f10-104">통합 사용 권한은 명시적 계층 및 컬렉션을 사용할 수 있는 엔터티에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-104">Consolidated permissions apply only to entities that are enabled for explicit hierarchies and collections.</span></span>  
  
 <span data-ttu-id="d2f10-105">**참고:**</span><span class="sxs-lookup"><span data-stu-id="d2f10-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="d2f10-106">리프 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="d2f10-107">**이름** 및 **코드** 특성에 할당된 사용 권한은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="d2f10-108">사용 권한</span><span class="sxs-lookup"><span data-stu-id="d2f10-108">Permission</span></span>|<span data-ttu-id="d2f10-109">Description</span><span class="sxs-lookup"><span data-stu-id="d2f10-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d2f10-110">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="d2f10-110">**Read-only**</span></span>|<span data-ttu-id="d2f10-111">통합 멤버가 표시되지만 사용자가 이를 추가, 제거 또는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-111">Consolidated members are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="d2f10-112">**Update**</span><span class="sxs-lookup"><span data-stu-id="d2f10-112">**Update**</span></span>|<span data-ttu-id="d2f10-113">통합 멤버가 표시되고 사용자가 이를 추가, 제거 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-113">Consolidated members are displayed and the user can add, remove, and change them.</span></span>|  
|<span data-ttu-id="d2f10-114">**Deny**</span><span class="sxs-lookup"><span data-stu-id="d2f10-114">**Deny**</span></span>|<span data-ttu-id="d2f10-115">엔터티의 통합 멤버가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-115">Consolidated members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="d2f10-116">특성 사용 권한</span><span class="sxs-lookup"><span data-stu-id="d2f10-116">Attribute Permissions</span></span>  
 <span data-ttu-id="d2f10-117">특성 사용 권한은 특정 엔터티의 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-117">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="d2f10-118">특성 사용 권한만 있는 사용자는 멤버를 추가하거나 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-118">Users with only attribute permissions cannot add or remove members.</span></span>  
  
|<span data-ttu-id="d2f10-119">사용 권한</span><span class="sxs-lookup"><span data-stu-id="d2f10-119">Permission</span></span>|<span data-ttu-id="d2f10-120">Description</span><span class="sxs-lookup"><span data-stu-id="d2f10-120">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d2f10-121">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="d2f10-121">**Read-only**</span></span>|<span data-ttu-id="d2f10-122">특성이 표시되지만 사용자가 특성 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-122">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="d2f10-123">**Update**</span><span class="sxs-lookup"><span data-stu-id="d2f10-123">**Update**</span></span>|<span data-ttu-id="d2f10-124">특성이 표시되고 사용자가 특성 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-124">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="d2f10-125">**Deny**</span><span class="sxs-lookup"><span data-stu-id="d2f10-125">**Deny**</span></span>|<span data-ttu-id="d2f10-126">특성이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-126">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="d2f10-127">참고: 이름 및 코드 특성에 대한 액세스를 명시적으로 거부할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2f10-127">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2f10-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2f10-128">See Also</span></span>  
 <span data-ttu-id="d2f10-129">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f10-129">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d2f10-130">[리프 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f10-130">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d2f10-131">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f10-131">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d2f10-132">[멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f10-132">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="d2f10-133">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d2f10-133">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
