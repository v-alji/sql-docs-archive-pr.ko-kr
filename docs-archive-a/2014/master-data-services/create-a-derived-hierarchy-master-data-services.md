---
title: 파생 계층 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 20469ad30222e43a3104503cc32187c2e6512743
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732712"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="00d86-102">파생 계층 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="00d86-102">Create a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="00d86-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버가 올바른 수준으로 유지되는 수준 기반 계층을 원하는 경우 파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a derived hierarchy when you want a level-based hierarchy that ensures that members exist at the correct level.</span></span> <span data-ttu-id="00d86-104">파생 계층은 모델에 있는 도메인 기반 특성 관계를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-104">Derived hierarchies are based on the domain-based attribute relationships that exist in a model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00d86-105">멤버에 대한 도메인 기반 특성 값이 없으면 멤버가 파생 계층에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-105">If a domain-based attribute value doesn't exist for a member, the member is not included in the derived hierarchy.</span></span> <span data-ttu-id="00d86-106">모든 멤버에 대한 도메인 기반 특성 값을 요구하려면 [특성 값 요구&#40;Master Data Services&#41;](require-attribute-values-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00d86-106">See [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md) to require a domain-based attribute value for all members.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="00d86-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="00d86-107">Prerequisites</span></span>  
 <span data-ttu-id="00d86-108">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="00d86-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="00d86-109">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-109">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="00d86-110">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-110">You must be a model administrator.</span></span> <span data-ttu-id="00d86-111">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00d86-111">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-derived-hierarchy"></a><span data-ttu-id="00d86-112">파생 계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="00d86-112">To create a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="00d86-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="00d86-114">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **파생 계층**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="00d86-115">**파생 계층 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-115">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="00d86-116">**파생 계층 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-116">Click **Add derived hierarchy**.</span></span>  
  
5.  <span data-ttu-id="00d86-117">**파생 계층 추가** 페이지의 **파생 계층 이름** 상자에 계층의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-117">On the **Add Derived Hierarchy** page, in the **Derived hierarchy name** box, type a name for the hierarchy.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="00d86-118">**하위 범주로 범주화할 제품**과 같이 계층의 수준을 설명하는 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-118">Use a name that describes the levels in the hierarchy, for example **Product to Subcategory to Category**.</span></span>  
  
6.  <span data-ttu-id="00d86-119">**파생 계층 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-119">Click **Save derived hierarchy**.</span></span>  
  
7.  <span data-ttu-id="00d86-120">**파생 계층 편집** 페이지의 **사용 가능한 엔터티 및 계층** 창에서 엔터티나 계층을 클릭 하 고 **현재 수준** 창으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-120">On the **Edit Derived Hierarchy** page, in the **Available Entities and Hierarchies** pane, click an entity or hierarchy and drag it to the **Current Levels** pane.</span></span>  
  
8.  <span data-ttu-id="00d86-121">계층이 완성될 때까지 엔터티나 계층을 계속 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-121">Continue dragging entities or hierarchies until your hierarchy is complete.</span></span>  
  
9. <span data-ttu-id="00d86-122">**뒤로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00d86-122">Click **Back**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d86-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00d86-123">See Also</span></span>  
 <span data-ttu-id="00d86-124">[파생 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="00d86-124">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="00d86-125">[명시적 캡이 포함 된 파생 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="00d86-125">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="00d86-126">도메인 기반 특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00d86-126">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
