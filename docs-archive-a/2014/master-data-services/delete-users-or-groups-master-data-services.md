---
title: 사용자 또는 그룹 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: be302bc974994d0f4f17a8e61244065c76fa93ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660012"
---
# <a name="delete-users-or-groups-master-data-services"></a><span data-ttu-id="76c1d-102">사용자 또는 그룹 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="76c1d-102">Delete Users or Groups (Master Data Services)</span></span>
  <span data-ttu-id="76c1d-103">사용자나 그룹이 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 액세스할 수 없게 하려면 해당 사용자나 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-103">Delete users or groups when you no longer want them to access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="76c1d-104">사용자와 그룹을 삭제할 때 다음 동작에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="76c1d-104">Note the following behavior when deleting users and groups:</span></span>  
  
-   <span data-ttu-id="76c1d-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 대한 액세스 권한이 있는 그룹의 멤버인 사용자를 삭제하는 경우 Active Directory 또는 로컬 그룹에서 제거할 때까지는 해당 사용자가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-105">If you delete a user who is a member of a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], then the user can still access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] until you remove the user from the Active Directory or local group.</span></span>  
  
-   <span data-ttu-id="76c1d-106">그룹을 삭제하는 경우 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에 액세스한 그룹의 모든 사용자를 삭제할 때까지 **사용자** 목록에 해당 사용자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-106">If you delete a group, all users from the group who have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] are displayed in the **Users** list until you delete them.</span></span>  
  
-   <span data-ttu-id="76c1d-107">보안에 대한 변경 내용은 20분 동안 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 에 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-107">Changes to security are not propagated to the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] for 20 minutes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76c1d-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="76c1d-108">Prerequisites</span></span>  
 <span data-ttu-id="76c1d-109">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="76c1d-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="76c1d-110">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-110">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="76c1d-111">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-111">You must be a model administrator.</span></span> <span data-ttu-id="76c1d-112">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76c1d-112">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-users-or-groups"></a><span data-ttu-id="76c1d-113">사용자나 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="76c1d-113">To delete users or groups</span></span>  
  
1.  <span data-ttu-id="76c1d-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="76c1d-115">사용자를 삭제하려면 **사용자** 페이지에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-115">To delete a user, remain on the **Users** page.</span></span> <span data-ttu-id="76c1d-116">그룹을 삭제하려면 메뉴 모음에서 **그룹 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-116">To delete a group, from the menu bar, click **ManageGroups.**</span></span>  
  
3.  <span data-ttu-id="76c1d-117">표에서 삭제하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-117">In the grid,select the row for the user or group that you want to delete.</span></span>  
  
4.  <span data-ttu-id="76c1d-118">**선택한 사용자 삭제** 또는 **선택한 그룹 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-118">Click **Delete selected user** or **Delete selected group**.</span></span>  
  
5.  <span data-ttu-id="76c1d-119">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76c1d-119">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c1d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76c1d-120">See Also</span></span>  
 [<span data-ttu-id="76c1d-121">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76c1d-121">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
