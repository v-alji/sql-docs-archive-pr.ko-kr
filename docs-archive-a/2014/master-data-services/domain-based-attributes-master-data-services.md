---
title: 도메인 기반 특성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9182974923848d49ed3e9ecfb58a14949784a2c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661682"
---
# <a name="domain-based-attributes-master-data-services"></a><span data-ttu-id="51ebe-102">도메인 기반 특성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="51ebe-102">Domain-Based Attributes (Master Data Services)</span></span>
  <span data-ttu-id="51ebe-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 도메인 기반 특성은 다른 엔터티의 멤버로 값이 채워지는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a domain-based attribute is an attribute with values that are populated by members from another entity.</span></span> <span data-ttu-id="51ebe-104">도메인 기반 특성은 제한된 목록으로 생각할 수 있습니다. 도메인 기반 특성을 사용하면 사용자가 유효하지 않은 특성 값을 입력하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-104">You can think of a domain-based attribute as a constrained list; domain-based attributes prevent users from entering attribute values that are not valid.</span></span> <span data-ttu-id="51ebe-105">특성 값을 선택하려면 사용자가 목록에서 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-105">To select an attribute value, the user must pick from a list.</span></span>

## <a name="domain-based-attribute-example"></a><span data-ttu-id="51ebe-106">도메인 기반 특성 예</span><span class="sxs-lookup"><span data-stu-id="51ebe-106">Domain-Based Attribute Example</span></span>
 <span data-ttu-id="51ebe-107">다음 이미지의 Product 엔터티에는 Subcategory라는 도메인 기반 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-107">In the following image, the Product entity has a domain-based attribute called Subcategory.</span></span> <span data-ttu-id="51ebe-108">Subcategory 특성은 Subcategory 엔터티의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-108">The Subcategory attribute is populated by values from the Subcategory entity.</span></span>

 <span data-ttu-id="51ebe-109">Subcategory 엔터티에는 Category라는 도메인 기반 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-109">The Subcategory entity has a domain-based attribute called Category.</span></span> <span data-ttu-id="51ebe-110">Category 특성은 Category 엔터티의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-110">The Category attribute is populated by values from the Category entity.</span></span>

 <span data-ttu-id="51ebe-111">![엔터티의 도메인 기반 특성](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "엔터티의 도메인 기반 특성")</span><span class="sxs-lookup"><span data-stu-id="51ebe-111">![Domain-Based Attributes in an Entity](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Domain-Based Attributes in an Entity")</span></span>

## <a name="use-same-entity-for-multiple-domain-based-attributes"></a><span data-ttu-id="51ebe-112">여러 도메인 기반 특성에 동일한 엔터티 사용</span><span class="sxs-lookup"><span data-stu-id="51ebe-112">Use Same Entity for Multiple Domain-Based Attributes</span></span>
 <span data-ttu-id="51ebe-113">동일한 엔터티를 여러 엔터티의 도메인 기반 특성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-113">You can use the same entity as a domain-based attribute of multiple entities.</span></span> <span data-ttu-id="51ebe-114">예를 들어, Yes, No 및 Maybe라는 멤버를 포함하는 YesNoIndicator라는 엔터티를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-114">For example, you can create an entity called YesNoIndicator with the members: Yes, No, and Maybe.</span></span> <span data-ttu-id="51ebe-115">또한 InStock이라는 도메인 기반 특성을 만들고 YesNoIndicator 엔터티를 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-115">You can create a domain-based attribute named InStock and use the YesNoIndicator entity as the source.</span></span> <span data-ttu-id="51ebe-116">Approved라는 또 다른 도메인 기반 특성을 만들고 YesNoIndicator 엔터티를 원본으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-116">You can also create another domain-based attribute named Approved and use the YesNoIndicator entity as a source.</span></span> <span data-ttu-id="51ebe-117">사용자가 YesNoIndicator 엔터티의 멤버 목록에서 선택할 수 있도록 하려는 경우 엔터티를 도메인 기반 특성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-117">Any time you want users to choose from a list of the YesNoIndicator entity's members, you can use the entity as a domain-based attribute.</span></span>

## <a name="domain-based-attributes-form-derived-hierarchies"></a><span data-ttu-id="51ebe-118">도메인 기반 특성으로 파생 계층 형성</span><span class="sxs-lookup"><span data-stu-id="51ebe-118">Domain-Based Attributes Form Derived Hierarchies</span></span>
 <span data-ttu-id="51ebe-119">도메인 기반 특성 관계는 파생 계층의 기반이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-119">Domain-based attribute relationships are the basis for derived hierarchies.</span></span> <span data-ttu-id="51ebe-120">자세한 내용은 [파생 계층&#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51ebe-120">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="51ebe-121">관련 작업</span><span class="sxs-lookup"><span data-stu-id="51ebe-121">Related Tasks</span></span>

|<span data-ttu-id="51ebe-122">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="51ebe-122">Task Description</span></span>|<span data-ttu-id="51ebe-123">항목</span><span class="sxs-lookup"><span data-stu-id="51ebe-123">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="51ebe-124">기존 엔터티를 원본으로 이용하여 새 도메인 기반 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-124">Create a new domain-based attribute that is sourced from an existing entity.</span></span>|[<span data-ttu-id="51ebe-125">도메인 기반 특성 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51ebe-125">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|<span data-ttu-id="51ebe-126">새 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51ebe-126">Create a new entity.</span></span>|[<span data-ttu-id="51ebe-127">엔터티 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51ebe-127">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="51ebe-128">관련 내용</span><span class="sxs-lookup"><span data-stu-id="51ebe-128">Related Content</span></span>

-   [<span data-ttu-id="51ebe-129">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51ebe-129">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="51ebe-130">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51ebe-130">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="51ebe-131">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51ebe-131">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)


