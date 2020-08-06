---
title: 통합 멤버 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c41673f6f3bf1f4de2a831ecd659321b273b6af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734208"
---
# <a name="create-a-consolidated-member-master-data-services"></a><span data-ttu-id="0ef5c-102">통합 멤버 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0ef5c-102">Create a Consolidated Member (Master Data Services)</span></span>
  <span data-ttu-id="0ef5c-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 명시적 계층에 대한 부모 노드가 필요한 경우 통합 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a consolidated member when you want a parent node for an explicit hierarchy.</span></span> <span data-ttu-id="0ef5c-104">통합된 멤버는 고유한 특성을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-104">Consolidated members can have their own attributes.</span></span> <span data-ttu-id="0ef5c-105">이러한 특성은 그룹화에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-105">They are used for grouping.</span></span> <span data-ttu-id="0ef5c-106">다음 예제와 같이 계정을 포함하는 계정 그룹에 통합된 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-106">As shown in the following example, consolidated members can be used for account groups that have accounts under them.</span></span>

 <span data-ttu-id="0ef5c-107">![MDS 통합 멤버](../../2014/master-data-services/media/mds-consolidated-members.png "MDS 통합 멤버")</span><span class="sxs-lookup"><span data-stu-id="0ef5c-107">![MDS Consolidated Members](../../2014/master-data-services/media/mds-consolidated-members.png "MDS Consolidated Members")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ef5c-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0ef5c-108">Prerequisites</span></span>
 <span data-ttu-id="0ef5c-109">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="0ef5c-109">To perform this procedure:</span></span>

-   <span data-ttu-id="0ef5c-110">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-110">You must have permission to access the **Explorer** functional area.</span></span>

-   <span data-ttu-id="0ef5c-111">멤버를 추가할 엔터티의 통합 모델 개체에 대한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-111">You must have a minimum of **Update** permission to the consolidated model object for the entity you are adding a member to.</span></span>

### <a name="to-create-a-consolidated-member"></a><span data-ttu-id="0ef5c-112">통합 멤버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="0ef5c-112">To create a consolidated member</span></span>

1.  <span data-ttu-id="0ef5c-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>

2.  <span data-ttu-id="0ef5c-114">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-114">From the **Version** list, select a version.</span></span>

3.  <span data-ttu-id="0ef5c-115">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-115">Click **Explorer**.</span></span>

4.  <span data-ttu-id="0ef5c-116">메뉴 모음에서 **계층** 을 가리키고 통합 멤버를 추가하려는 계층의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-116">From the menu bar, point to **Hierarchies** and click the name of the hierarchy you want to add a consolidated member to.</span></span>

5.  <span data-ttu-id="0ef5c-117">표 위에 있는 **통합 멤버** 또는 **계층의 모든 통합 멤버** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-117">Above the grid, select either the **Consolidated members** or the **All consolidated members in hierarchy** option.</span></span>

6.  <span data-ttu-id="0ef5c-118">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-118">Click **Add**.</span></span>

7.  <span data-ttu-id="0ef5c-119">오른쪽 창의 필드에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-119">In the pane on the right, complete the fields.</span></span>

8.  <span data-ttu-id="0ef5c-120">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-120">Optional.</span></span> <span data-ttu-id="0ef5c-121">**주석** 상자에 멤버를 추가한 이유에 대한 주석을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-121">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="0ef5c-122">멤버에 액세스할 수 있는 모든 사용자가 주석을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-122">All users who have access to the member can view the annotation.</span></span>

9. <span data-ttu-id="0ef5c-123">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ef5c-123">Click **OK**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ef5c-124">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0ef5c-124">Next Steps</span></span>

-   [<span data-ttu-id="0ef5c-125">계층 내에서 멤버를 이동 하 여 MDS(Master Data Services) &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="0ef5c-125">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a><span data-ttu-id="0ef5c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ef5c-126">See Also</span></span>
 <span data-ttu-id="0ef5c-127">[MDS(Master Data Services) &#40;명시적 계층을 만들어&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [Create a Leaf Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) [MDS(Master Data Services)&#41;](add-update-and-delete-data-master-data-services.md) [MDS(Master Data Services) &#40;MDS(Master Data Services)](../../2014/master-data-services/members-master-data-services.md)&#41;&#40;MDS(Master Data Services)&#41;[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) &#40;</span><span class="sxs-lookup"><span data-stu-id="0ef5c-127">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [Create a Leaf Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) [Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) [Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)</span></span>


