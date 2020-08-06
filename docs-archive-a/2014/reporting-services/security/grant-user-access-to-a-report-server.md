---
title: 사용자에 게 보고서 서버에 대 한 액세스 권한 부여 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730084"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a><span data-ttu-id="948a7-102">사용자에게 보고서 서버에 대한 액세스 권한 부여(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="948a7-102">Grant User Access to a Report Server (Report Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="948a7-103">는 역할 기반 보안을 사용하여 보고서 서버에 대한 액세스 권한을 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-103">uses role-based security to grant user access to a report server.</span></span> <span data-ttu-id="948a7-104">새 보고서 서버 설치에서는 로컬 관리자 그룹의 멤버인 사용자에게만 보고서 서버 내용 및 작업에 대한 사용 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-104">On a new report server installation, only users who are members of the local Administrators group have permissions to report server content and operations.</span></span> <span data-ttu-id="948a7-105">다른 사용자가 보고서 서버를 사용할 수 있게 하려면 태스크 모음을 지정하는 미리 정의된 역할에 사용자 또는 그룹 계정을 매핑하는 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-105">To make the report server available to other users, you must create role assignments that map  user or group accounts to a predefined role that specifies a collection of tasks.</span></span>  
  
 <span data-ttu-id="948a7-106">**SharePoint 모드 보고서 서버:** SharePoint 통합 모드로 구성된 보고서 서버의 경우 SharePoint 사이트에서 SharePoint 사용 권한을 사용하여 액세스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-106">**SharePoint mode report servers:** For a report server that is configured for SharePoint integrated mode, you configure access from a SharePoint site using SharePoint permissions.</span></span> <span data-ttu-id="948a7-107">SharePoint 사이트의 사용 권한 수준에 따라 보고서 서버 내용 및 작업에 대한 액세스 권한이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-107">Permission levels on the SharePoint site determine access to report server content and operations.</span></span> <span data-ttu-id="948a7-108">SharePoint 사이트에 대한 사용 권한을 부여하려면 사이트 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-108">You must be a site administrator to grant permissions on a SharePoint site.</span></span> <span data-ttu-id="948a7-109">자세한 내용은 [SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="948a7-109">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="948a7-110">**기본 모드 보고서 서버:** 이 항목에서는 기본 모드로 구성된 보고서 서버 및 보고서 관리자를 사용하여 역할에 사용자를 할당하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-110">**Native mode report servers:** This topic is focused on a report server that is configured for native mode and the use of Report Manager to assign users to a role.</span></span> <span data-ttu-id="948a7-111">역할에는 다음과 같은 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-111">There are two types of roles:</span></span>  
  
-   <span data-ttu-id="948a7-112">항목 수준 역할은 보고서 서버 내용, 구독, 보고서 처리 및 보고서 기록을 보고, 추가하고, 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-112">Item-level roles are used to view, add, and manage report server content, subscriptions, report processing, and report history.</span></span> <span data-ttu-id="948a7-113">항목 수준 역할 할당은 루트 노드(홈 폴더)에 정의되거나 계층의 하위 수준에 있는 특정 폴더 또는 항목에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-113">Item-level role assignments are defined on the root node (the Home folder) or on specific folders or items farther down the hierarchy.</span></span>  
  
-   <span data-ttu-id="948a7-114">시스템 수준 역할은 특정 항목으로 한정되지 않은 사이트 전체 작업에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-114">System-level roles grant access to site-wide operations that are not bound to any specific item.</span></span> <span data-ttu-id="948a7-115">보고서 작성기를 사용하는 작업과 공유 일정을 사용하는 작업을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-115">Examples include using Report Builder and using shared schedules.</span></span>  
  
     <span data-ttu-id="948a7-116">이러한 두 역할 유형은 상호 보완적이며 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-116">The two types of roles complement each other and should be used together.</span></span> <span data-ttu-id="948a7-117">따라서 보고서 서버에 사용자를 추가하는 작업은 두 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-117">For this reason, adding a user to a report server is a two-part operation.</span></span> <span data-ttu-id="948a7-118">즉, 사용자를 항목 수준 역할에 할당하는 경우 시스템 수준 역할에도 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-118">If you assign a user to an item-level role, you should also assign them to a system-level role.</span></span> <span data-ttu-id="948a7-119">사용자를 역할에 할당할 때는 이미 정의되어 있는 역할을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-119">When assigning a user to a role, you must select a role that is already defined.</span></span> <span data-ttu-id="948a7-120">역할을 생성, 수정 또는 삭제하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-120">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="948a7-121">자세한 내용은 [역할 만들기, 삭제 또는 수정&#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="948a7-121">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="before-you-start"></a><span data-ttu-id="948a7-122">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="948a7-122">Before you start</span></span>  
 <span data-ttu-id="948a7-123">기본 모드 보고서 서버에 사용자를 추가하기 전에 다음 목록을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-123">Review the following list before adding users to a native mode report server.</span></span>  
  
-   <span data-ttu-id="948a7-124">보고서 서버 컴퓨터에서 로컬 관리자 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-124">You must be a member of the local Administrators group on the report server computer.</span></span> <span data-ttu-id="948a7-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 또는 Windows Server 2008에서 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] 를 배포하는 경우 보고서 서버를 로컬로 관리하려면 추가 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-125">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] or Windows Server 2008, additional configuration is required before you can administer a report server locally.</span></span> <span data-ttu-id="948a7-126">자세한 내용은 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="948a7-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
-   <span data-ttu-id="948a7-127">이 태스크를 다른 사용자에게 위임하려면 사용자 계정을 내용 관리자 및 시스템 관리자 역할에 매핑하는 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-127">To delegate this task to other users, create role assignments that map user accounts to Content Manager and System Administrator roles.</span></span> <span data-ttu-id="948a7-128">내용 관리자 및 시스템 관리자 권한이 있는 사용자는 보고서 서버에 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-128">Users who have Content Manager and System Administrator permissions can add users to a report server.</span></span>  
  
-   <span data-ttu-id="948a7-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 각 역할의 작업 종류에 익숙해질 수 있도록 시스템 역할 및 사용자 역할에 대해 미리 정의된 역할을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], view the predefined roles for System Roles and User Roles so that you are familiar with the kinds of tasks in each role.</span></span> <span data-ttu-id="948a7-130">보고서 관리자에는 태스크 설명이 표시되지 않으므로 사용자를 추가하기 전에 역할에 익숙해지는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-130">Task descriptions are not visible in Report Manager, so you will want to be familiar with the roles before you begin adding users.</span></span>  
  
-   <span data-ttu-id="948a7-131">필요에 따라 필요한 태스크 모음을 포함하는 추가 역할을 정의하거나 역할을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-131">Optionally, customize the roles or define additional roles to include the collection of tasks that you require.</span></span> <span data-ttu-id="948a7-132">예를 들어 개별 항목에 대해 사용자 지정 보안 설정을 사용하려는 경우 폴더에 대한 보기 액세스 권한을 부여하는 새 역할 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-132">For example, if you plan to use custom security settings for individual items, you might want to create a new role definition that grants view-access to folders.</span></span>  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a><span data-ttu-id="948a7-133">시스템 역할에 사용자 또는 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="948a7-133">To add a user or group to a system role</span></span>  
  
1.  <span data-ttu-id="948a7-134">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="948a7-135">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-135">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="948a7-136">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-136">Click **Security**.</span></span>  
  
4.  <span data-ttu-id="948a7-137">**새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-137">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="948a7-138">**그룹 또는 사용자 이름**에 Windows 도메인 사용자 또는 그룹 계정을 \<domain> \\<계정 형식으로 입력 \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-138">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="948a7-139">폼 인증 또는 사용자 지정 보안을 사용하는 경우에는 해당 배포에 적절한 형식으로 사용자 또는 그룹 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-139">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="948a7-140">시스템 역할을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-140">Select a system role, and then click **OK**.</span></span>  
  
     <span data-ttu-id="948a7-141">역할은 누적되므로 시스템 관리자와 시스템 사용자를 모두 선택하면 사용자 또는 그룹이 두 역할 모두에서 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-141">Roles are cumulative, so if you select both System Administrator and System User, a user or group will be able to perform the tasks in both roles.</span></span>  
  
7.  <span data-ttu-id="948a7-142">위의 단계를 반복하여 추가 사용자 또는 그룹에 대한 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-142">Repeat to create assignments for additional users or groups.</span></span>  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a><span data-ttu-id="948a7-143">항목 역할에 사용자 또는 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="948a7-143">To add a user or group to an item role</span></span>  
  
1.  <span data-ttu-id="948a7-144">**보고서 관리자** 를 시작하고 사용자 또는 그룹을 추가할 보고서 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-144">Start **Report Manager** and locate the report item for which you want to add a user or group.</span></span>  
  
2.  <span data-ttu-id="948a7-145">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-145">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="948a7-146">드롭다운 메뉴에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-146">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="948a7-147">**새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-147">Click **New Role Assignment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="948a7-148"> 항목이 현재 부모 항목의 보안을 상속하는 경우에는 도구 모음에서 **항목 보안 편집** 을 클릭하여 보안 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-148">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span> <span data-ttu-id="948a7-149">그런 다음 **새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-149">Then click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="948a7-150">**그룹 또는 사용자 이름**에 Windows 도메인 사용자 또는 그룹 계정을 \<domain> \\<계정 형식으로 입력 \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-150">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="948a7-151">폼 인증 또는 사용자 지정 보안을 사용하는 경우에는 해당 배포에 적절한 형식으로 사용자 또는 그룹 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-151">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="948a7-152">사용자 또는 그룹에서 항목에 액세스하는 방법을 설명하는 역할 정의를 하나 이상 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-152">Select one or more role definitions that describe how the user or group should access the item, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="948a7-153">위의 단계를 반복하여 추가 사용자 또는 그룹에 대한 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="948a7-153">Repeat to create assignments for additional users or groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948a7-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="948a7-154">See Also</span></span>  
 <span data-ttu-id="948a7-155">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="948a7-155">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="948a7-156">[새 역할 할당: 역할 할당 편집 페이지 &#40;보고서 관리자&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="948a7-156">[New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span></span>  
 <span data-ttu-id="948a7-157">[보안 속성 페이지, 항목 &#40;보고서 관리자&#41;](../security-properties-page-items-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="948a7-157">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md) </span></span>  
 <span data-ttu-id="948a7-158">[역할 할당](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="948a7-158">[Role Assignments](role-assignments.md) </span></span>  
 [<span data-ttu-id="948a7-159">역할 정의</span><span class="sxs-lookup"><span data-stu-id="948a7-159">Role Definitions</span></span>](role-definitions.md)  
  
  
