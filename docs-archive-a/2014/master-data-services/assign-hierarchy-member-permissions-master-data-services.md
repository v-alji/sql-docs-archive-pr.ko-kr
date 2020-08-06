---
title: 계층 멤버 권한 할당(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4a1602f9fe351f826b63d4447f90dcf02a10f49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651776"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="e5965-102">계층 멤버 권한 할당(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e5965-102">Assign Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="e5965-103">계층 멤버에 사용 권한을 할당하여 사용자나 그룹에 **의** 탐색기 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]기능 영역에서 데이터를 볼 수 있는 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-103">Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="e5965-104">계층 멤버 권한은 선택 사항으로서</span><span class="sxs-lookup"><span data-stu-id="e5965-104">Hierarchy member permissions are optional.</span></span> <span data-ttu-id="e5965-105">필수 모델 개체 사용 권한을 보다 세부적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-105">They provide added granularity to model object permissions, which are required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e5965-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e5965-106">Prerequisites</span></span>  
 <span data-ttu-id="e5965-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="e5965-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e5965-108">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="e5965-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-109">You must be a model administrator.</span></span> <span data-ttu-id="e5965-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e5965-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-hierarchy-member-permissions"></a><span data-ttu-id="e5965-111">계층 멤버 권한을 할당하려면</span><span class="sxs-lookup"><span data-stu-id="e5965-111">To assign hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="e5965-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="e5965-113">**사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="e5965-114">**선택한 사용자 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="e5965-115">**계층 멤버** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-115">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="e5965-116">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-116">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="e5965-117">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-117">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="e5965-118">**계층** 목록에서 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-118">From the **Hierarchy** list, select a hierarchy.</span></span>  
  
8.  <span data-ttu-id="e5965-119">**편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-119">Click **Edit**.</span></span>  
  
9. <span data-ttu-id="e5965-120">트리를 확장하고 사용 권한을 할당할 계층 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-120">Expand the tree, and click the hierarchy node you want to assign permissions to.</span></span>  
  
10. <span data-ttu-id="e5965-121">메뉴에서 **읽기**전용, **업데이트**또는 **거부**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-121">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
11. <span data-ttu-id="e5965-122">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-122">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5965-123">계층 멤버 권한은 즉시 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5965-123">Hierarchy member permissions do not take effect immediately.</span></span> <span data-ttu-id="e5965-124">자세한 내용은 [멤버 권한 즉시 적용&#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5965-124">See [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5965-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5965-125">See Also</span></span>  
 <span data-ttu-id="e5965-126">[MDS(Master Data Services)&#41;&#40;계층 멤버 권한 삭제](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e5965-126">[Delete Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="e5965-127">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e5965-127">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="e5965-128">계층 멤버 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e5965-128">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
