---
title: 명시적 캡이 포함된 파생 계층(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647720"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a><span data-ttu-id="0ea09-102">명시적 캡이 포함된 파생 계층(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0ea09-102">Derived Hierarchies with Explicit Caps (Master Data Services)</span></span>
  <span data-ttu-id="0ea09-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 명시적 계층의 수준이 파생 계층의 최상위 수준으로 사용되는 경우 이를 명시적 캡이 포함된 파생 계층이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when the levels from an explicit hierarchy are used as the top levels of a derived hierarchy, this is called a derived hierarchy with an explicit cap.</span></span>

 <span data-ttu-id="0ea09-104">명시적 계층은 파생 계층의 최상위 엔터티와 동일한 엔터티를 기반으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-104">The explicit hierarchy must be based on the same entity as the entity at the top of the derived hierarchy.</span></span>

 <span data-ttu-id="0ea09-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI(사용자 인터페이스)에서는 명시적 계층을 파생 계층의 맨 위로 끌어와서 이 유형의 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-105">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), you create this type of hierarchy by dragging an explicit hierarchy to the top of a derived hierarchy.</span></span>

 <span data-ttu-id="0ea09-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="0ea09-106">![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")</span></span>

## <a name="derived-hierarchy-with-explicit-cap-example"></a><span data-ttu-id="0ea09-107">명시적 캡이 포함된 파생 계층 예제</span><span class="sxs-lookup"><span data-stu-id="0ea09-107">Derived Hierarchy with Explicit Cap Example</span></span>
 <span data-ttu-id="0ea09-108">이 예에서는 명시적 계층의 멤버를 Subcategory 엔터티에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-108">In this example, the members in the explicit hierarchy are from the Subcategory entity.</span></span> <span data-ttu-id="0ea09-109">파생 계층의 최상위 멤버 역시 Subcategory 엔터티에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-109">In the derived hierarchy, the top-level members are also from the Subcategory entity.</span></span>

 <span data-ttu-id="0ea09-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span><span class="sxs-lookup"><span data-stu-id="0ea09-110">![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")</span></span>

 <span data-ttu-id="0ea09-111">파생 계층의 맨 위에 명시적 계층을 사용하므로 파생 계층이 비정형 계층이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-111">By using the explicit hierarchy at the top of a derived hierarchy, the derived hierarchy becomes ragged.</span></span>

## <a name="rules"></a><span data-ttu-id="0ea09-112">규칙</span><span class="sxs-lookup"><span data-stu-id="0ea09-112">Rules</span></span>

-   <span data-ttu-id="0ea09-113">명시적 캡을 포함한 파생 계층에 두 개 이상의 명시적 계층이 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-113">You cannot have more than one explicit hierarchy in a derived hierarchy with explicit cap.</span></span>

-   <span data-ttu-id="0ea09-114">여러 파생 계층에 Cap과 동일한 명시적 계층을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-114">You can use the same explicit hierarchy as a cap for multiple derived hierarchies.</span></span>

-   <span data-ttu-id="0ea09-115">명시적 캡이 포함된 파생 계층에 계층 멤버 권한을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-115">You cannot assign hierarchy member permissions to derived hierarchies with explicit caps.</span></span> <span data-ttu-id="0ea09-116">명시적 계층이나 파생 계층에 개별적으로 사용 권한을 할당할 경우 해당 권한이 두 계층에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-116">If you assign permissions to either the explicit hierarchy or the derived hierarchy individually, the permissions affect both hierarchies.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="0ea09-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0ea09-117">Related Tasks</span></span>

|<span data-ttu-id="0ea09-118">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="0ea09-118">Task Description</span></span>|<span data-ttu-id="0ea09-119">항목</span><span class="sxs-lookup"><span data-stu-id="0ea09-119">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="0ea09-120">파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-120">Create a derived hierarchy.</span></span>|[<span data-ttu-id="0ea09-121">파생 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea09-121">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="0ea09-122">명시적 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-122">Create an explicit hierarchy.</span></span>|[<span data-ttu-id="0ea09-123">명시적 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea09-123">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="0ea09-124">기존 파생 계층을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0ea09-124">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="0ea09-125">파생 계층 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea09-125">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="0ea09-126">관련 내용</span><span class="sxs-lookup"><span data-stu-id="0ea09-126">Related Content</span></span>

-   [<span data-ttu-id="0ea09-127">파생 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea09-127">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="0ea09-128">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea09-128">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


