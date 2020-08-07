---
title: 계층 멤버 권한 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8b6e7fbfc4379733d5cb809ce4d46d2c12d05a48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731844"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="039a3-102">계층 멤버 권한 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="039a3-102">Delete Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="039a3-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 개체 사용 권한을 삭제하여 모든 할당을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="039a3-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="039a3-104">Prerequisites</span></span>  
 <span data-ttu-id="039a3-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="039a3-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="039a3-106">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="039a3-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-107">You must be a model administrator.</span></span> <span data-ttu-id="039a3-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="039a3-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-hierarchy-member-permissions"></a><span data-ttu-id="039a3-109">계층 멤버 권한을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="039a3-109">To delete hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="039a3-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="039a3-111">**사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="039a3-112">**선택한 사용자 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="039a3-113">**계층 멤버** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-113">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="039a3-114">**모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="039a3-115">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-115">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="039a3-116">**계층 멤버 권한 요약** 창에서 삭제 하려는 사용 권한의 행을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-116">In the **Hierarchy Member Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
8.  <span data-ttu-id="039a3-117">**선택한 사용 권한 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-117">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="039a3-118">사용 권한이 그룹에서 상속되는 경우에는 사용자로부터 사용 권한을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-118">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="039a3-119">대신 그룹에서 사용 권한을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="039a3-119">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039a3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="039a3-120">See Also</span></span>  
 <span data-ttu-id="039a3-121">[계층 멤버 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="039a3-121">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="039a3-122">계층 멤버 권한 할당&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="039a3-122">Assign Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
