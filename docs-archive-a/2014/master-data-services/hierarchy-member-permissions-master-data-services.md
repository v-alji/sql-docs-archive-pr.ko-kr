---
title: 계층 멤버 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81716dbd0ad08b6e92a2edb8f1d142b46bf3d24d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652177"
---
# <a name="hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="1977a-102">계층 멤버 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1977a-102">Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="1977a-103">계층 멤버 권한은 선택 사항이며 사용자에게 특정 멤버에 대한 제한된 액세스 권한을 부여하려는 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-103">Hierarchy member permissions are optional and should be used only when you want a user to have limited access to specific members.</span></span> <span data-ttu-id="1977a-104">**계층 멤버** 탭에서 아무 권한도 할당하지 않을 경우 사용자의 권한은 전적으로 **모델** 탭에서 할당한 권한을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-104">If you do not assign permissions on the **Hierarchy Members** tab, then the user's permissions are based solely on the permissions assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="1977a-105">계층 멤버 권한은 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI (사용자 인터페이스)의 **계층 멤버** 탭에 있는 **사용자 및 그룹 권한** 기능 영역에서 할당 됩니다. 이러한 사용 권한은 사용자가 UI의 **탐색기** 기능 영역에서 액세스할 수 있는 멤버를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-105">Hierarchy member permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Hierarchy Members** tab. These permissions determine which members a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="1977a-106">**계층 멤버** 탭에서 각 계층은 트리 구조로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-106">On the **Hierarchy Members** tab, each hierarchy is represented as a tree structure.</span></span> <span data-ttu-id="1977a-107">트리의 노드에 사용 권한을 할당하면 하위 수준에서 권한이 명시적으로 할당된 경우를 제외하고 모든 자식이 해당 권한을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-107">When you assign permission to a node in the tree, all children inherit that permission unless permission is explicitly assigned at a lower level.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1977a-108">계층의 노드에 사용 권한을 할당하면 같은 수준 이상의 다른 모든 노드에 있는 모든 멤버는 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-108">When you assign permission to a node in a hierarchy, all members in other nodes at the same level or higher are implicitly denied.</span></span>  
  
 <span data-ttu-id="1977a-109">**탐색기**에서는 멤버가 표시되는 모든 곳에 멤버 권한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-109">In **Explorer**, the member permissions are applied everywhere the member is displayed.</span></span> <span data-ttu-id="1977a-110">예를 들어 **읽기** 전용 권한이 있는 멤버는 자신이 속한 모든 엔터티, 계층 및 컬렉션에서 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-110">For example, a member with **Read-only** permission is read-only in any entities, hierarchies, and collections to which it belongs.</span></span>  
  
 <span data-ttu-id="1977a-111">계층 멤버 권한은 할당 대상 모델 버전과 해당 버전의 모든 이후 복사본에 적용되며,</span><span class="sxs-lookup"><span data-stu-id="1977a-111">Hierarchy member permissions apply to the model version you assign them to, and to any future copies of the version.</span></span> <span data-ttu-id="1977a-112">할당 대상 버전보다 이전 버전에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-112">They do not apply to versions earlier than the one you assign them to.</span></span>  
  
|<span data-ttu-id="1977a-113">사용 권한</span><span class="sxs-lookup"><span data-stu-id="1977a-113">Permission</span></span>|<span data-ttu-id="1977a-114">Description</span><span class="sxs-lookup"><span data-stu-id="1977a-114">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="1977a-115">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="1977a-115">**Read-only**</span></span>|<span data-ttu-id="1977a-116">멤버가 표시되지만 사용자가 멤버를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-116">The members are displayed but the user cannot change them.</span></span> <span data-ttu-id="1977a-117">또한 사용자는 멤버가 속한 모든 명시적 계층이나 컬렉션에서 멤버를 이동할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-117">The user also cannot move the members in any explicit hierarchies or collections that the members belong to.</span></span><br /><br /> <span data-ttu-id="1977a-118">참고: **루트**에 **읽기** 전용 권한을 할당 하면 **루트** 아래의 멤버는 읽기 전용이 됩니다. 그러나 명시적 계층 및 컬렉션에서는 사용자가 멤버를 **루트** 로 이동 하 고 **루트**에 새 멤버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-118">Note: If you assign **Read-only** permission to **Root**, the members under **Root** are read-only; however, in explicit hierarchies and collections, the user can move members to **Root** and can add new members to **Root**.</span></span>|  
|<span data-ttu-id="1977a-119">**Update**</span><span class="sxs-lookup"><span data-stu-id="1977a-119">**Update**</span></span>|<span data-ttu-id="1977a-120">멤버가 표시되며 사용자가 멤버를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-120">The members are displayed and the user can change them.</span></span> <span data-ttu-id="1977a-121">또한 사용자는 멤버가 속한 모든 명시적 계층이나 컬렉션에서 멤버를 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-121">The user can also move the members in any explicit hierarchies or collections the members belong to.</span></span>|  
|<span data-ttu-id="1977a-122">**Deny**</span><span class="sxs-lookup"><span data-stu-id="1977a-122">**Deny**</span></span>|<span data-ttu-id="1977a-123">멤버가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-123">The members are not displayed.</span></span>|  
  
 <span data-ttu-id="1977a-124">**계층 멤버** 탭에서 할당하는 사용 권한은 즉시 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-124">On the **Hierarchy Members** tab, the permissions you assign do not take effect immediately.</span></span> <span data-ttu-id="1977a-125">사용 권한이 적용되는 주기는 **데이터베이스의 시스템 설정 테이블에 지정된** 멤버 보안 처리 간격 설정 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-125">The frequency that the permissions are applied depends on the **Member security processing interval setting** in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="1977a-126">[멤버 권한 즉시 적용&#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)의 단계를 수행하여 멤버 권한을 즉시 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-126">You can apply member permissions immediately by following the steps in [Immediately Apply Member Permissions &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1977a-127">재귀 계층, 명시적 캡이 포함된 파생 계층 및 숨겨진 수준이 있는 파생 계층에는 계층 멤버 권한을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-127">You cannot assign hierarchy member permissions to recursive hierarchies, derived hierarchies with explicit caps, and derived hierarchies with hidden levels.</span></span>  
  
## <a name="possible-overlapping-permissions"></a><span data-ttu-id="1977a-128">겹칠 수 있는 사용 권한</span><span class="sxs-lookup"><span data-stu-id="1977a-128">Possible Overlapping Permissions</span></span>  
 <span data-ttu-id="1977a-129">멤버에 사용 권한을 할당할 때 겹치는 사용 권한을 확인해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-129">When assigning permission to members, you may have to resolve overlapping permissions.</span></span>  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a><span data-ttu-id="1977a-130">멤버가 여러 계층에 속한 경우</span><span class="sxs-lookup"><span data-stu-id="1977a-130">When a member belongs to multiple hierarchies</span></span>  
 <span data-ttu-id="1977a-131">둘 이상의 계층이 같은 멤버를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-131">Two or more hierarchies can contain the same member.</span></span>  
  
-   <span data-ttu-id="1977a-132">한 계층 노드에는 **업데이트** 권한이 할당 되 고 다른 노드에는 **읽기**전용 권한이 할당 된 경우 노드의 멤버는 **읽기 전용**입니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-132">If one hierarchy node is assigned **Update** permission and another is assigned **Read-only**, then the members in the node are **Read-only**.</span></span>  
  
-   <span data-ttu-id="1977a-133">한 계층 노드에는 **업데이트** 또는 **읽기 전용** 권한이 할당 되 고 다른 노드에는 **거부**권한이 할당 된 경우 노드의 멤버가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1977a-133">If one hierarchy node is assigned **Update** or **Read-only** permission and another node is assigned **Deny**, then the members in the node are not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1977a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1977a-134">See Also</span></span>  
 <span data-ttu-id="1977a-135">[계층 멤버 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1977a-135">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="1977a-136">[MDS(Master Data Services) &#40;사용 권한을 결정 하는 방법&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1977a-136">[How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span></span>  
 <span data-ttu-id="1977a-137">[멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1977a-137">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 <span data-ttu-id="1977a-138">[계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1977a-138">[Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="1977a-139">멤버 권한 즉시 적용&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1977a-139">Immediately Apply Member Permissions &#40;Master Data Services&#41;</span></span>](immediately-apply-member-permissions-master-data-services.md)  
  
  
