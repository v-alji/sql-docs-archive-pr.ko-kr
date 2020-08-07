---
title: 겹치는 사용자 및 그룹 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7044bf6260170cbc598719ec204ddb6f861f6301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730780"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a><span data-ttu-id="2ac45-102">겹치는 사용자 및 그룹 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2ac45-102">Overlapping User and Group Permissions (Master Data Services)</span></span>
  <span data-ttu-id="2ac45-103">사용자의 사용 권한은 다음 요소에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-103">A user's permissions are based on:</span></span>  
  
-   <span data-ttu-id="2ac45-104">그룹 멤버 자격의 사용 권한</span><span class="sxs-lookup"><span data-stu-id="2ac45-104">Permissions from group memberships.</span></span>  
  
-   <span data-ttu-id="2ac45-105">사용자에게 명시적으로 할당된 사용 권한</span><span class="sxs-lookup"><span data-stu-id="2ac45-105">Permissions assigned explicitly to the user.</span></span>  
  
 <span data-ttu-id="2ac45-106">사용자가 여러 그룹의 멤버이며 이러한 그룹에 마스터 데이터 관리자에 대한 액세스 권한이 있는 경우 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-106">If a user is a member of multiple groups, and those groups have access to Master Data Manager, the following rules apply:</span></span>  
  
-   <span data-ttu-id="2ac45-107">**거부** 는 다른 모든 사용 권한을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-107">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="2ac45-108">**업데이트** 는 **읽기**전용을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-108">**Update** overrides **Read-only**.</span></span>  
  
 <span data-ttu-id="2ac45-109">이러한 규칙은 **모델** 탭과 **계층 멤버** 탭 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-109">These rules apply to both the **Models** and **Hierarchy Members** tabs.</span></span> <span data-ttu-id="2ac45-110">각 탭의 사용 권한이 확인된 후 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-110">Permissions are resolved for each tab and then combined.</span></span> <span data-ttu-id="2ac45-111">자세한 내용은 [사용 권한이 결정되는 방식&#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ac45-111">For more information, see [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ac45-112">겹치는 사용자 및 그룹 권한은 사용자 인터페이스에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-112">You can view the resolution of user and group overlapping permissions in the user interface.</span></span> <span data-ttu-id="2ac45-113">**모델** 탭과 **계층 멤버** 탭 둘 다에 **유효** 를 선택하여 유효 사용 권한을 볼 수 있는 드롭다운 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-113">Both the **Models** and **Hierarchy Members** tab have a drop-down list from which you can choose **Effective** to view effective permissions.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2ac45-114">예 1</span><span class="sxs-lookup"><span data-stu-id="2ac45-114">Example 1</span></span>  
 <span data-ttu-id="2ac45-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span><span class="sxs-lookup"><span data-stu-id="2ac45-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span></span>  
  
 <span data-ttu-id="2ac45-116">사용자가 그룹 1 및 그룹 2에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-116">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="2ac45-117">사용자에 게 Product 엔터티에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-117">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-118">그룹 1은 Product 엔터티에 대한 **업데이트** 권한을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-118">Group 1 has **Update** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-119">그룹 2는 Product 엔터티에 대 한 **읽기 전용** 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-119">Group 2 has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-120">결과: Product 엔터티에 대한 사용자의 유효 권한은 **업데이트** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-120">Result: The user's effective permission is **Update** to the Product entity.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="2ac45-121">예제 2</span><span class="sxs-lookup"><span data-stu-id="2ac45-121">Example 2</span></span>  
 <span data-ttu-id="2ac45-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span><span class="sxs-lookup"><span data-stu-id="2ac45-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span></span>  
  
 <span data-ttu-id="2ac45-123">사용자가 그룹 1 및 그룹 2에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-123">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="2ac45-124">사용자에 게 Product 엔터티에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-124">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-125">그룹 1은 Product 엔터티에 대한 **업데이트** 권한을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-125">Group 1 has **Update** permission to Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-126">그룹 2는 Product 엔터티에 대한 **거부** 권한을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-126">Group 2 has **Deny** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="2ac45-127">결과: Product 엔터티에 대한 사용자의 유효 권한은 **거부** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-127">Result: The user's effective permission is **Deny** to the Product entity.</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="2ac45-128">예제 3</span><span class="sxs-lookup"><span data-stu-id="2ac45-128">Example 3</span></span>  
 <span data-ttu-id="2ac45-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span><span class="sxs-lookup"><span data-stu-id="2ac45-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span></span>  
  
 <span data-ttu-id="2ac45-130">사용자가 그룹 1 및 그룹 2에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-130">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="2ac45-131">사용자가 계층 노드의 멤버 그룹에 대한 **업데이트** 권한을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-131">The user has **Update** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="2ac45-132">그룹 1에 계층 노드의 멤버 그룹에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-132">Group 1 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="2ac45-133">그룹 2에 계층 노드의 멤버 그룹에 대 한 **읽기 전용** 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-133">Group 2 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="2ac45-134">결과: 멤버에 대한 사용자의 유효 권한은 **업데이트** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2ac45-134">Result: The user's effective permission is **Update** to the members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac45-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ac45-135">See Also</span></span>  
 <span data-ttu-id="2ac45-136">[MDS(Master Data Services) &#40;사용 권한을 결정 하는 방법&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2ac45-136">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="2ac45-137">겹치는 모델 및 멤버 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2ac45-137">Overlapping Model and Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
