---
title: 사용자 및 그룹(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: efad65bf273d58b4f60b98d050a8b99705cb00ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743324"
---
# <a name="users-and-groups-master-data-services"></a><span data-ttu-id="bb334-102">사용자 및 그룹(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bb334-102">Users and Groups (Master Data Services)</span></span>
  <span data-ttu-id="bb334-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에 액세스하려면 사용자에게 Windows 도메인 계정이나 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 가 설치된 서버 컴퓨터의 계정이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-103">To access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application a user must have a Windows domain account or an account on the server computer where [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed.</span></span> <span data-ttu-id="bb334-104">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에 대한 액세스 권한을 부여하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-104">To grant access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] you can either:</span></span>  
  
-   <span data-ttu-id="bb334-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 도메인 또는 로컬 그룹에 사용자 계정을 추가한 다음 그룹 목록에 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-105">Add the user account to a domain or local group and then add the group to the list of groups in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="bb334-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 사용자 목록에 사용자 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-106">Add the user account to the list of users in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb334-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 대한 액세스 권한이 있는 그룹에 사용자가 속할 경우 사용자가 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 또는 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]에 처음 액세스할 때 사용자의 이름이 사용자 목록에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-107">When a user belongs to a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is automatically added to the list of users the first time the user accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="bb334-108">UI의 **탐색기** 기능 영역 내에서 동작을 수행하려면 **탐색기** 기능 영역에 대한 액세스 권한과 모델 개체에 대한 사용 권한이 그룹 또는 사용자에게 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-108">To take action within the **Explorer** functional area of the UI, the group or user must be assigned access to the **Explorer** functional area and assigned permission to model objects.</span></span>  
  
 <span data-ttu-id="bb334-109">사용자 또는 그룹이 다른 기능 영역에 액세스해야 하는 경우에는 사용자 또는 그룹이 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-109">If a user or group needs access to other functional areas, the user or group must be an administrator.</span></span> <span data-ttu-id="bb334-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb334-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="bb334-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="bb334-111">Best Practice</span></span>  
 <span data-ttu-id="bb334-112">관리를 간소화하려면 그룹을 만들고 각 그룹에 기능 영역 및 모델 개체에 대한 그룹 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-112">To simplify administration, create groups and assign each group permission to functional areas and model objects.</span></span> <span data-ttu-id="bb334-113">그러면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI에 액세스하지 않고 그룹에서 사용자를 추가하고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb334-113">You can then add and remove users from the groups without accessing the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI.</span></span>  
  
 <span data-ttu-id="bb334-114">개별 사용자에게는 추가 권한을 할당하지 말고 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 대한 액세스 권한이 있는 여러 그룹에 사용자를 포함하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bb334-114">Do not assign additional permissions to an individual user, and do not include a user in multiple groups that have access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="bb334-115">또한 그룹에서 특정 멤버에 대해 제한된 액세스 권한을 부여하려는 경우를 제외하고는 계층 멤버 권한을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bb334-115">In addition, do not use hierarchy member permissions unless you want a group to have limited access to specific members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb334-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb334-116">See Also</span></span>  
 <span data-ttu-id="bb334-117">[사용자 &#40;MDS(Master Data Services)에 추가&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="bb334-117">[Add a User &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span></span>  
 <span data-ttu-id="bb334-118">[그룹 &#40;MDS(Master Data Services) 추가&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="bb334-118">[Add a Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span></span>  
 <span data-ttu-id="bb334-119">[MDS(Master Data Services)&#41;&#40;사용자 또는 그룹 삭제](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="bb334-119">[Delete Users or Groups &#40;Master Data Services&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="bb334-120">사용자의 사용 권한 테스트&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb334-120">Test a User's Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
