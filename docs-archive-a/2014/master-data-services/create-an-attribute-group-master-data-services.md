---
title: 특성 그룹 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fbd95869082ea0a73f3abea092163c4705e4da5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736471"
---
# <a name="create-an-attribute-group-master-data-services"></a><span data-ttu-id="f50a2-102">특성 그룹 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f50a2-102">Create an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="f50a2-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 **탐색기** 표의 개별 탭에 특성을 표시하려는 경우 특성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create attribute groups when you want to display attributes on individual tabs in the **Explorer** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f50a2-104">특성 그룹을 만들면 특성 그룹은 해당 그룹을 만든 사람을 제외한 모든 사용자로부터 자동으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="f50a2-105">그룹을 표시하는 방법에 대한 자세한 내용은 [특성 그룹을 사용자에게 표시되도록 설정&#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)기능 영역의 표 위에 탭으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-105">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f50a2-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="f50a2-106">Prerequisites</span></span>  
 <span data-ttu-id="f50a2-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f50a2-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f50a2-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f50a2-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-109">You must be a model administrator.</span></span> <span data-ttu-id="f50a2-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f50a2-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f50a2-111">하나 이상의 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-111">At least one attribute must exist.</span></span> <span data-ttu-id="f50a2-112">자세한 내용은 [텍스트 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f50a2-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-create-an-attribute-group"></a><span data-ttu-id="f50a2-113">특성 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f50a2-113">To create an attribute group</span></span>  
  
1.  <span data-ttu-id="f50a2-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f50a2-115">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **특성 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="f50a2-116">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-116">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f50a2-117">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="f50a2-118">**리프 그룹**, **통합 그룹**또는 **컬렉션 그룹** 을 클릭하여 각각 리프 멤버, 통합 멤버 또는 컬렉션의 특성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-118">Click **Leaf Groups**, **Consolidated Groups**, or **Collection Groups** to create an attribute group of leaf members, consolidated members, or collections respectively.</span></span>  
  
6.  <span data-ttu-id="f50a2-119">**특성 그룹 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-119">Click **Add attribute group**.</span></span>  
  
7.  <span data-ttu-id="f50a2-120">**리프 그룹 이름** 상자에 그룹의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-120">In the **Leaf group name** box, type a name for the group.</span></span> <span data-ttu-id="f50a2-121">**탐색기**의 탭에 표시 되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-121">This is the name displayed on the tab in **Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f50a2-122">5 단계에서 **통합 그룹** 또는 **컬렉션 그룹** 을 선택한 경우이 상자는 각각 **통합 그룹 이름** 또는 **컬렉션 그룹 이름**입니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-122">If you selected **Consolidated Groups** or **Collection Groups** in step 5, this box is **Consolidated group name** or **Collection group name**, respectively.</span></span>  
  
8.  <span data-ttu-id="f50a2-123">**그룹 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-123">Click **Save group**.</span></span>  
  
9. <span data-ttu-id="f50a2-124">그룹에 해당하는 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-124">Expand the folder for the group.</span></span>  
  
10. <span data-ttu-id="f50a2-125">**특성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-125">Click **Attributes**.</span></span>  
  
11. <span data-ttu-id="f50a2-126">**선택한 항목 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-126">Click **Edit selected item**.</span></span>  
  
12. <span data-ttu-id="f50a2-127">**사용 가능한** 상자에서 특성을 클릭 하 고 **추가** 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-127">Click attributes in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="f50a2-128">모두 추가하려면 **모두 추가** 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-128">To add all, click the **Add All** arrow.</span></span>  
  
13. <span data-ttu-id="f50a2-129">필요에 따라 **위쪽** 및 **아래쪽** 화살표를 클릭 하 여 특성의 왼쪽에서 오른쪽 순서를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-129">Optionally, click the **Up** and **Down** arrows to change the left-to-right order of the attributes.</span></span>  
  
14. <span data-ttu-id="f50a2-130">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a2-130">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f50a2-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f50a2-131">Next Steps</span></span>  
  
-   [<span data-ttu-id="f50a2-132">특성 그룹을 사용자에게 표시되도록 설정&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f50a2-132">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f50a2-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f50a2-133">See Also</span></span>  
 <span data-ttu-id="f50a2-134">[특성 그룹 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f50a2-134">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 <span data-ttu-id="f50a2-135">[특성 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f50a2-135">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="f50a2-136">[특성 그룹 이름을 변경 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f50a2-136">[Change an Attribute Group Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span></span>  
 <span data-ttu-id="f50a2-137">[특성 그룹 &#40;MDS(Master Data Services) 삭제&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f50a2-137">[Delete an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span></span>  
 <span data-ttu-id="f50a2-138">[리프 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f50a2-138">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="f50a2-139">MDS(Master Data Services)&#41;&#40;통합 된 사용 권한</span><span class="sxs-lookup"><span data-stu-id="f50a2-139">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
