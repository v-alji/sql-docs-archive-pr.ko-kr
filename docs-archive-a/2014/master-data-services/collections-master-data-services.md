---
title: 컬렉션(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce49c57aad5da52dabba32a0f3fb9b6f4f45b209
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731872"
---
# <a name="collections-master-data-services"></a><span data-ttu-id="12c11-102">컬렉션(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="12c11-102">Collections (Master Data Services)</span></span>
  <span data-ttu-id="12c11-103">컬렉션은 단일 엔터티의 리프 멤버와 통합 멤버의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-103">A collection is a group of leaf and consolidated members from a single entity.</span></span> <span data-ttu-id="12c11-104">전체 계층이 필요 없고 보고나 분석을 위해 멤버의 다른 그룹을 보려는 경우 또는 분류를 만들어야 할 경우 컬렉션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-104">Use collections when you do not need a complete hierarchy and you want to view different groupings of members for reporting or analysis, or when you need to create a taxonomy.</span></span>  
  
## <a name="what-collections-contain"></a><span data-ttu-id="12c11-105">컬렉션에 포함되는 내용</span><span class="sxs-lookup"><span data-stu-id="12c11-105">What Collections Contain</span></span>  
 <span data-ttu-id="12c11-106">컬렉션에는 포함할 수 있는 멤버의 개수나 유형에 대한 제한이 없습니다. 해당 멤버가 같은 엔터티 내에 있기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-106">Collections do not limit the number or type of members you can include, as long as the members are within the same entity.</span></span> <span data-ttu-id="12c11-107">컬렉션은 여러 필수 및 필수가 아닌 명시적 계층의 리프 및 통합 멤버를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-107">A collection can contain leaf and consolidated members from multiple mandatory and non-mandatory explicit hierarchies.</span></span>  
  
 <span data-ttu-id="12c11-108">컬렉션을 만들 때 계층적 구조를 만들지 않고 멤버의 기본 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-108">When you create a collection, you are not creating a hierarchical structure; you are creating a flat list of members.</span></span> <span data-ttu-id="12c11-109">계층에서 노드를 선택하여 이를 컬렉션에 추가할 경우 선택한 통합 멤버만 컬렉션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-109">When you select a node from a hierarchy and add it to the collection, the consolidated member you selected is the only member added to the collection.</span></span>  
  
 <span data-ttu-id="12c11-110">또한 컬렉션은 다른 컬렉션을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-110">A collection can also contain other collections.</span></span> <span data-ttu-id="12c11-111">컬렉션으로 구성된 컬렉션을 사용하여 분류를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-111">You can use collections of collections to create taxonomies.</span></span>  
  
 <span data-ttu-id="12c11-112">컬렉션을 만들면 사용자는 자동으로 소유자로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-112">When you create a collection you are automatically listed as the owner.</span></span> <span data-ttu-id="12c11-113">관리자인 경우 필요에 따라 자신의 컬렉션에 대한 다른 특성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-113">If you are an administrator, you can create other attributes for your collection as needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12c11-114">컬렉션을 만들려면 먼저 엔터티가 명시적 계층을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-114">Before you can create a collection, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="12c11-115">자세한 내용은 [&#41;MDS(Master Data Services) &#40;명시적 계층 및 컬렉션에 엔터티 사용 ](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12c11-115">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
## <a name="subscription-views-for-collections"></a><span data-ttu-id="12c11-116">컬렉션의 구독 뷰</span><span class="sxs-lookup"><span data-stu-id="12c11-116">Subscription Views for Collections</span></span>  
 <span data-ttu-id="12c11-117">컬렉션을 표시하는 두 가지 유형의 구독 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-117">There are two types of subscription views that show collections.</span></span> <span data-ttu-id="12c11-118">**컬렉션 특성** 형식은 컬렉션 목록 및 컬렉션과 관련된 모든 특성(설명 또는 소유자 등)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-118">The **Collection attributes** format shows a list of collections and any attributes related to the collections (like description or owner).</span></span> <span data-ttu-id="12c11-119">**컬렉션** 형식은 모든 컬렉션의 모든 멤버와 각 멤버의 가중치 및 정렬 순서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-119">The **Collections** format shows all members in all collections, as well as each members weight and sort order.</span></span> <span data-ttu-id="12c11-120">자세한 내용은 [데이터 내보내기 &#40;MDS(Master Data Services)&#41;](overview-exporting-data-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12c11-120">For more information, see [Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).</span></span>  
  
 <span data-ttu-id="12c11-121">컬렉션의 특정 멤버에 대해 가중치를 설정하는 경우 이러한 값을 관련 구독 뷰에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-121">If you set weight values for specific members in a collection, these values are available in related subscription views.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="12c11-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="12c11-122">Related Tasks</span></span>  
  
|<span data-ttu-id="12c11-123">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="12c11-123">Task Description</span></span>|<span data-ttu-id="12c11-124">항목</span><span class="sxs-lookup"><span data-stu-id="12c11-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="12c11-125">명시적 계층 및 컬렉션에 엔터티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-125">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="12c11-126">명시적 계층 및 컬렉션에 대해 엔터티를 사용 하도록 설정 &#40;MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="12c11-126">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="12c11-127">새 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-127">Create a new collection.</span></span>|[<span data-ttu-id="12c11-128">컬렉션 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="12c11-128">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|<span data-ttu-id="12c11-129">기존 컬렉션에 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="12c11-129">Add members to an existing collection.</span></span>|[<span data-ttu-id="12c11-130">컬렉션에 멤버 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="12c11-130">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="12c11-131">관련 내용</span><span class="sxs-lookup"><span data-stu-id="12c11-131">Related Content</span></span>  
  
-   [<span data-ttu-id="12c11-132">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="12c11-132">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [<span data-ttu-id="12c11-133">데이터 &#40;MDS(Master Data Services)&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="12c11-133">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
