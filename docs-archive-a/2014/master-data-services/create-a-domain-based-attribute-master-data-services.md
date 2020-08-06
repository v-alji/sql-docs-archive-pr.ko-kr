---
title: 도메인 기반 특성 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 51c0f44bb76ae2ad4c25987ed5e5ee144a18c739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647730"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a><span data-ttu-id="2b640-102">도메인 기반 특성 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2b640-102">Create a Domain-Based Attribute (Master Data Services)</span></span>
  <span data-ttu-id="2b640-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 도메인 기반 특성을 만들어서 엔터티의 멤버로 특성 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a domain-based attribute to populate an attribute's values with members from an entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2b640-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="2b640-104">Prerequisites</span></span>  
 <span data-ttu-id="2b640-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="2b640-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2b640-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2b640-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-107">You must be a model administrator.</span></span> <span data-ttu-id="2b640-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b640-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="2b640-109">특성 값의 원본으로 사용할 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-109">An entity must exist to use as the source of the attribute values.</span></span> <span data-ttu-id="2b640-110">예를 들어 Color 엔터티를 기반으로 하는 도메인 기반 특성을 만들려면 먼저 Color 엔터티를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-110">For example, to create a domain-based attribute based on the Color entity, you must first create the Color entity.</span></span> <span data-ttu-id="2b640-111">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b640-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="2b640-112">해당 특성을 만들 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-112">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="2b640-113">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b640-113">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-domain-based-attribute"></a><span data-ttu-id="2b640-114">도메인 기반 특성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="2b640-114">To create a domain-based attribute</span></span>  
  
1.  <span data-ttu-id="2b640-115">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2b640-116">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-116">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="2b640-117">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-117">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2b640-118">해당 특성을 만들려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-118">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="2b640-119">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-119">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="2b640-120">**엔터티 편집** 페이지에서</span><span class="sxs-lookup"><span data-stu-id="2b640-120">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="2b640-121">리프 멤버에 대한 특성일 경우 **리프 멤버 특성** 창에서 **리프 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-121">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="2b640-122">통합 멤버에 대한 특성일 경우 **통합 멤버 특성** 창에서 **통합 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-122">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="2b640-123">컬렉션에 대한 특성일 경우 **컬렉션 특성** 창에서 **컬렉션 특성 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-123">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="2b640-124">**특성 추가** 페이지에서 **도메인 기반** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-124">On the **Add Attribute** page, select the **Domain-based** option.</span></span>  
  
8.  <span data-ttu-id="2b640-125">**이름** 상자에 특성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-125">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="2b640-126">이름이 특성 값의 원본으로 사용할 엔터티와 동일할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-126">It does not have to be the same name as the entity that you use for the source of the attribute values.</span></span>  
  
9. <span data-ttu-id="2b640-127">**탐색기** 표에 표시할 특성 열의 너비를 **표시 픽셀 폭** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-127">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="2b640-128">**엔터티** 목록에서 특성 값을 채우는 데 사용할 엔터티를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-128">From the **Entity** list, choose the entity to be used to populate the attribute values.</span></span>  
  
11. <span data-ttu-id="2b640-129">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-129">Optional.</span></span> <span data-ttu-id="2b640-130">특성 그룹의 변경 내용을 추적하려면 **Enable change tracking** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-130">Select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="2b640-131">자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b640-131">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="2b640-132">**특성 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-132">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="2b640-133">**엔터티 유지 관리** 페이지에서 **엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b640-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b640-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b640-134">See Also</span></span>  
 <span data-ttu-id="2b640-135">[도메인 기반 특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2b640-135">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="2b640-136">[파생 계층 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2b640-136">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 <span data-ttu-id="2b640-137">[특성 이름을 MDS(Master Data Services) &#40;변경&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2b640-137">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 [<span data-ttu-id="2b640-138">특성 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2b640-138">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)  
  
  
