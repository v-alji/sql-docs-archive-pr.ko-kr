---
title: 재귀 계층 구조(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- recursive hierarchies [Master Data Services]
- hierarchies [Master Data Services], recursive hierarchies
ms.assetid: 9408c6ea-d9c4-4a0b-8a1b-1457fb6944af
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3c149d500ce1499ad36247d5e32bb6f2d55b4250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660004"
---
# <a name="recursive-hierarchies-master-data-services"></a><span data-ttu-id="c5490-102">재귀 계층 구조(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c5490-102">Recursive Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="c5490-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 재귀 계층 구조는 재귀 관계를 포함하는 파생 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a recursive hierarchy is a derived hierarchy that includes a recursive relationship.</span></span> <span data-ttu-id="c5490-104">재귀 관계는 엔터티에 엔터티 자체를 기반으로 하는 도메인 기반 특성이 있는 경우에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-104">A recursive relationship exists when an entity has a domain-based attribute based on the entity itself.</span></span>

## <a name="recursive-hierarchy-example"></a><span data-ttu-id="c5490-105">재귀 계층 예</span><span class="sxs-lookup"><span data-stu-id="c5490-105">Recursive Hierarchy Example</span></span>
 <span data-ttu-id="c5490-106">일반적인 재귀 계층 예는 조직 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-106">A typical recursive hierarchy example is an organizational structure.</span></span> <span data-ttu-id="c5490-107">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 Manager라는 도메인 기반 특성을 가진 Employee 엔터티를 만들어서 이를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-107">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you would do this by creating an Employee entity with a domain-based attribute called Manager.</span></span> <span data-ttu-id="c5490-108">Manager 특성은 직원 목록으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-108">The Manager attribute is populated from the list of employees.</span></span> <span data-ttu-id="c5490-109">이 샘플 조직에서 모든 직원은 관리자가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-109">In this sample organization, all employees can be managers.</span></span>

 <span data-ttu-id="c5490-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span><span class="sxs-lookup"><span data-stu-id="c5490-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span></span>

 <span data-ttu-id="c5490-111">Employee 엔터티와 Manager 도메인 기반 특성 간의 관계를 강조하는 파생 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-111">You can create a derived hierarchy that highlights the relationship between the Employee entity and the Manager domain-based attribute.</span></span>

 <span data-ttu-id="c5490-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="c5490-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span></span>

 <span data-ttu-id="c5490-113">계층에 각 멤버를 한 번만 포함하려면 Null 관계에 앵커를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-113">To include each member in the hierarchy only once, you can anchor null relationships.</span></span> <span data-ttu-id="c5490-114">Null 관계에 앵커를 지정하는 경우 빈 도메인 기반 특성 값을 가진 멤버가 계층의 최상위 수준에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-114">When you do, members with blank domain-based attribute values are displayed at the top level of the hierarchy.</span></span>

 <span data-ttu-id="c5490-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span><span class="sxs-lookup"><span data-stu-id="c5490-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span></span>

 <span data-ttu-id="c5490-116">Null 관계에 앵커를 지정하지 않을 경우 멤버가 여러 번 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-116">If you do not anchor null relationships, members are included multiple times.</span></span> <span data-ttu-id="c5490-117">모든 멤버가 최상위 수준에 표시되며,</span><span class="sxs-lookup"><span data-stu-id="c5490-117">All members are displayed at the top level.</span></span> <span data-ttu-id="c5490-118">자신이 특성으로 사용되는 멤버 아래에도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-118">They are also displayed under members of which they are attributes.</span></span>

 <span data-ttu-id="c5490-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span><span class="sxs-lookup"><span data-stu-id="c5490-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span></span>

 <span data-ttu-id="c5490-120">이 예에서 Marcia는 최상위 수준에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-120">In this example, Marcia is at the top level.</span></span> <span data-ttu-id="c5490-121">그녀는 다른 Employee 멤버의 도메인 기반 특성 값으로 사용되지 않으므로 어느 직원의 관리자도 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-121">She is not the manager of any employees because she is not used as a domain-based attribute value for any other Employee members.</span></span> <span data-ttu-id="c5490-122">이와 달리 Marcia에게는 Robert가 Manager 특성 값으로 지정되어 있으므로 Robert 아래에 한 수준이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-122">Robert, in contrast, has a level beneath him because Marcia has Robert as her Manager attribute value.</span></span>

## <a name="rules"></a><span data-ttu-id="c5490-123">규칙</span><span class="sxs-lookup"><span data-stu-id="c5490-123">Rules</span></span>

-   <span data-ttu-id="c5490-124">파생 계층에는 두 개 이상의 재귀적 관계가 포함될 수 없지만</span><span class="sxs-lookup"><span data-stu-id="c5490-124">A derived hierarchy cannot contain more than one recursive relationship.</span></span> <span data-ttu-id="c5490-125">다른 파생 관계는 포함될 수 있습니다. 예를 들어 재귀적 Manager to Employee 관계가 포함된 파생 계층에 Country to Manager 및 Employee to Store 관계가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-125">It can, however, have other derived relationships (for example, a derived hierarchy that contains a recursive Manager to Employee relationship can also have Country to Manager and Employee to Store relationships).</span></span>

-   <span data-ttu-id="c5490-126">**계층 멤버** 탭에서 멤버 권한을 재귀 계층 구조의 멤버에 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-126">You cannot assign member permissions (on the **Hierarchy Members** tab) to members in a recursive hierarchy.</span></span>

-   <span data-ttu-id="c5490-127">재귀 계층 구조는 순환 관계를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-127">Recursive hierarchies cannot include circular relationships.</span></span> <span data-ttu-id="c5490-128">예를 들어, Sandeep이 Katherine의 관리자인 경우 Katherine은 Sandeep의 관리자일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-128">For example, Katherine cannot be Sandeep's manager if Sandeep is her manager.</span></span> <span data-ttu-id="c5490-129">또한 Katherine은 자신을 관리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-129">Also, Katherine cannot manage herself.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="c5490-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c5490-130">Related Tasks</span></span>

|<span data-ttu-id="c5490-131">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="c5490-131">Task Description</span></span>|<span data-ttu-id="c5490-132">항목</span><span class="sxs-lookup"><span data-stu-id="c5490-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="c5490-133">파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-133">Create a derived hierarchy.</span></span>|[<span data-ttu-id="c5490-134">파생 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c5490-134">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="c5490-135">기존 파생 계층의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-135">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="c5490-136">파생 계층 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c5490-136">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="c5490-137">기존 파생 계층을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c5490-137">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="c5490-138">파생 계층 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c5490-138">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="c5490-139">관련 내용</span><span class="sxs-lookup"><span data-stu-id="c5490-139">Related Content</span></span>

-   [<span data-ttu-id="c5490-140">도메인 기반 특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c5490-140">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="c5490-141">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c5490-141">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)


