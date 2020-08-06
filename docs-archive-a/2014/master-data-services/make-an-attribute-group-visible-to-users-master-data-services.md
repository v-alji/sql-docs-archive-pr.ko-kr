---
title: 특성 그룹을 사용자에게 표시되도록 설정(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 309ad0392cd717d4a8a11470621144ef9e604fd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638885"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a><span data-ttu-id="45d9c-102">특성 그룹을 사용자에게 표시되도록 설정(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="45d9c-102">Make an Attribute Group Visible to Users (Master Data Services)</span></span>
  <span data-ttu-id="45d9c-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 특성 그룹이 사용자나 그룹에 표시되도록 설정하여 **탐색기** 기능 영역의 표 위에 탭이 나타나도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], make an attribute group visible to users or groups when you want users to have tabs above the grid in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="45d9c-104">특성 그룹을 만들면 특성 그룹은 해당 그룹을 만든 사람을 제외한 모든 사용자로부터 자동으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="45d9c-105">전제 조건</span><span class="sxs-lookup"><span data-stu-id="45d9c-105">Prerequisites</span></span>  
 <span data-ttu-id="45d9c-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="45d9c-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="45d9c-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="45d9c-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-108">You must be a model administrator.</span></span> <span data-ttu-id="45d9c-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45d9c-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="45d9c-110">하나 이상의 특성 그룹이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-110">At least one attribute group must exist.</span></span> <span data-ttu-id="45d9c-111">자세한 내용은 [특성 그룹 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45d9c-111">For more information, see [Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md).</span></span>  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a><span data-ttu-id="45d9c-112">특성 그룹이 사용자에게 표시되도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="45d9c-112">To make an attribute group visible to users</span></span>  
  
1.  <span data-ttu-id="45d9c-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="45d9c-114">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **특성 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="45d9c-115">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-115">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="45d9c-116">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="45d9c-117">표시되도록 설정할 그룹 유형에 따라 더하기 기호를 클릭하여 **리프 그룹**, **통합 그룹**또는 **컬렉션 그룹**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-117">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to make visible.</span></span>  
  
6.  <span data-ttu-id="45d9c-118">더하기 기호를 클릭하여 표시되도록 설정할 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-118">Click the plus sign to expand the group you want to make visible.</span></span>  
  
7.  <span data-ttu-id="45d9c-119">그룹을 사용자에게 표시할지 그룹에 표시할지 여부에 따라 **사용자** 또는 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-119">Click either **Users** or **Groups**, depending on whether you are making the group visible to a user or a group.</span></span>  
  
8.  <span data-ttu-id="45d9c-120">**선택한 항목 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-120">Click **Edit selected item**.</span></span>  
  
9. <span data-ttu-id="45d9c-121">**사용 가능** 상자에서 사용자나 그룹을 클릭하고 **추가** 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-121">Click users or groups in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="45d9c-122">모두 추가하려면 **모두 추가** 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-122">To add all, click the **Add All** arrow.</span></span>  
  
10. <span data-ttu-id="45d9c-123">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45d9c-123">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d9c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45d9c-124">See Also</span></span>  
 <span data-ttu-id="45d9c-125">[특성 그룹 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="45d9c-125">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="45d9c-126">특성 그룹 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="45d9c-126">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
