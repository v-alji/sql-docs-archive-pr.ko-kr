---
title: 특성 그룹(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 390b402489799639e66a44992da1e20b0d0c1bbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651759"
---
# <a name="attribute-groups-master-data-services"></a><span data-ttu-id="b480e-102">특성 그룹(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b480e-102">Attribute Groups (Master Data Services)</span></span>
  <span data-ttu-id="b480e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 특성 그룹은 엔터티의 특성을 구성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], attribute groups help organize attributes in an entity.</span></span> <span data-ttu-id="b480e-104">엔터티에 있는 특성이 여러 개인 경우 특성 그룹을 사용하면 엔터티가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에 표시되는 방식이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-104">When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
## <a name="how-attribute-groups-change-the-display"></a><span data-ttu-id="b480e-105">특성 그룹 표시를 변경하는 방법</span><span class="sxs-lookup"><span data-stu-id="b480e-105">How Attribute Groups Change the Display</span></span>  
 <span data-ttu-id="b480e-106">특성 그룹은 **에서** 탐색기 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]기능 영역의 표 위에 탭으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-106">Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="b480e-107">엔터티에 특성이 많이 있고 **탐색기**의 표에서 해당 엔터티를 볼 경우 모든 특성을 보려면 오른쪽으로 스크롤해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-107">When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes.</span></span> <span data-ttu-id="b480e-108">이렇게 스크롤하지 않고 모든 특성을 보려면 특성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-108">To prevent this scrolling, you can create attribute groups.</span></span>  
  
-   <span data-ttu-id="b480e-109">특성 그룹에는 Name 및 Code 특성이 항상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-109">Attribute groups always include the Name and Code attributes.</span></span>  
  
-   <span data-ttu-id="b480e-110">엔터티의 각 특성은 하나 이상의 특성 그룹에 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-110">Each attribute for an entity can belong to one or more attribute groups.</span></span>  
  
-   <span data-ttu-id="b480e-111">모든 특성은 **탐색기** 의 **모든 특성**탭에 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-111">All attributes are automatically included on the **All Attributes** tab in **Explorer**.</span></span>  
  
-   <span data-ttu-id="b480e-112">**모든 특성** 탭을 숨길 수 있는 방법은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-112">There is no way to hide the **All Attributes** tab.</span></span>  
  
 <span data-ttu-id="b480e-113">특성 그룹은 **의** 시스템 관리 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]기능 영역에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-113">Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="show-or-hide-attribute-groups"></a><span data-ttu-id="b480e-114">특성 그룹 표시 또는 숨기기</span><span class="sxs-lookup"><span data-stu-id="b480e-114">Show or Hide Attribute Groups</span></span>  
 <span data-ttu-id="b480e-115">특성 그룹을 만들면 특성 그룹은 해당 그룹을 만든 사람을 제외한 모든 사용자로부터 자동으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-115">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="b480e-116">그룹을 표시하는 방법에 대한 자세한 내용은 [특성 그룹을 사용자에게 표시되도록 설정&#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)기능 영역의 표 위에 탭으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-116">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
 <span data-ttu-id="b480e-117">그룹 내의 특정 특성을 숨기려면 해당 특성에 **거부** 권한을 할당하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-117">If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute.</span></span> <span data-ttu-id="b480e-118">자세한 내용은 [리프 권한&#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) 또는 [통합 사용 권한&#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b480e-118">For more information, see [Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) or [Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b480e-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b480e-119">Related Tasks</span></span>  
  
|<span data-ttu-id="b480e-120">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="b480e-120">Task Description</span></span>|<span data-ttu-id="b480e-121">항목</span><span class="sxs-lookup"><span data-stu-id="b480e-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="b480e-122">새 특성 그룹을 만들고 이 그룹에 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-122">Create a new attribute group and add attributes to it.</span></span>|[<span data-ttu-id="b480e-123">특성 그룹 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b480e-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|<span data-ttu-id="b480e-124">특성 그룹을 사용자가 볼 수 있도록 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-124">Make an attribute group visible to users.</span></span>|[<span data-ttu-id="b480e-125">특성 그룹을 사용자에게 표시되도록 설정&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b480e-125">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|<span data-ttu-id="b480e-126">기존 특성 그룹의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-126">Change the name of an existing attribute group.</span></span>|[<span data-ttu-id="b480e-127">특성 그룹 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b480e-127">Change an Attribute Group Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|<span data-ttu-id="b480e-128">기존 특성 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b480e-128">Delete an existing attribute group.</span></span>|[<span data-ttu-id="b480e-129">특성 그룹 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b480e-129">Delete an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="b480e-130">관련 내용</span><span class="sxs-lookup"><span data-stu-id="b480e-130">Related Content</span></span>  
  
-   [<span data-ttu-id="b480e-131">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b480e-131">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
