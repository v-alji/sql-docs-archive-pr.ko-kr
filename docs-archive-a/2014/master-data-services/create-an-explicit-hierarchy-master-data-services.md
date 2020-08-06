---
title: 명시적 계층 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aebf95e68f210fe5a573aed092231670c10fa188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652877"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="cbd9c-102">명시적 계층 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cbd9c-102">Create an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="cbd9c-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버가 임의의 수준에 존재할 수 있는 비정형 계층이 필요할 때 명시적 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an explicit hierarchy when you need a ragged hierarchy in which members can exist at any level.</span></span> <span data-ttu-id="cbd9c-104">명시적 계층에는 단일 엔터티의 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-104">Explicit hierarchies contain members from a single entity.</span></span>  
  
 <span data-ttu-id="cbd9c-105">명시적 계층을 만든 후에는 **탐색기** 기능 영역에서 해당 계층에 멤버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-105">After you create an explicit hierarchy, you can add members to it in the **Explorer** functional area.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbd9c-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cbd9c-106">Prerequisites</span></span>  
 <span data-ttu-id="cbd9c-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="cbd9c-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cbd9c-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="cbd9c-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-109">You must be a model administrator.</span></span> <span data-ttu-id="cbd9c-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="cbd9c-111">명시적 계층 및 컬렉션에 엔터티가 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-111">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="cbd9c-112">자세한 내용은 [&#41;MDS(Master Data Services) &#40;명시적 계층 및 컬렉션에 엔터티 사용 ](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-112">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-an-explicit-hierarchy"></a><span data-ttu-id="cbd9c-113">명시적 계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="cbd9c-113">To create an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="cbd9c-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="cbd9c-115">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="cbd9c-116">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="cbd9c-117">명시적 계층을 만들려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-117">Select the row for the entity that you want to create an explicit hierarchy for.</span></span>  
  
5.  <span data-ttu-id="cbd9c-118">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="cbd9c-119">**엔터티 편집** 페이지의 **명시적 계층** 창에서 **명시적 계층 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-119">On the **Edit Entity** page, in the **Explicit hierarchies** pane, click **Add explicit hierarchy**.</span></span>  
  
7.  <span data-ttu-id="cbd9c-120">**명시적 계층 추가** 페이지의 **명시적 계층 이름** 상자에 계층의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-120">On the **Add Explicit Hierarchy** page, in the **Explicit hierarchy name** box, type a name for the hierarchy.</span></span>  
  
8.  <span data-ttu-id="cbd9c-121">또는 **필수 계층** 확인란의 선택을 취소하여 계층을 필수가 아닌 계층으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-121">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span> <span data-ttu-id="cbd9c-122">계층 형식에 대한 자세한 내용은 [명시적 계층&#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-122">For more information about hierarchy types, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="cbd9c-123">**계층 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-123">Click **Save hierarchy**.</span></span>  
  
10. <span data-ttu-id="cbd9c-124">**엔터티 편집** 페이지에서 **엔터티 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-124">On the **Edit Entity** page, click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cbd9c-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="cbd9c-125">Next Steps</span></span>  
  
-   [<span data-ttu-id="cbd9c-126">통합 멤버 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cbd9c-126">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [<span data-ttu-id="cbd9c-127">계층 내에서 멤버를 이동 하 여 MDS(Master Data Services) &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="cbd9c-127">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbd9c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbd9c-128">See Also</span></span>  
 <span data-ttu-id="cbd9c-129">[명시적 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cbd9c-129">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="cbd9c-130">[명시적 캡이 포함 된 파생 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cbd9c-130">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="cbd9c-131">명시적 계층 이름 변경&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cbd9c-131">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
