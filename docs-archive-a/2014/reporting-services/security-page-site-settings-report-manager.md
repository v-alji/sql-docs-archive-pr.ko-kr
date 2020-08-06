---
title: 보안 페이지(사이트 설정. 보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 997806b8bba92d210a8d108a7101e086f21abb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649371"
---
# <a name="security-page-site-settings-report-manager"></a><span data-ttu-id="c49d3-103">보안 페이지(사이트 설정.</span><span class="sxs-lookup"><span data-stu-id="c49d3-103">Security Page (Site Settings.</span></span> <span data-ttu-id="c49d3-104">보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="c49d3-104">Report Manager)</span></span>
  <span data-ttu-id="c49d3-105">보안 페이지를 사용하여 보고서 서버 사이트에 대한 액세스를 제어하는 시스템 역할 할당을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-105">Use the Security page to view the system role assignments that control access to the report server site.</span></span> <span data-ttu-id="c49d3-106">시스템 역할 할당은 보고서 서버 네임스페이스나 폴더 계층 구조의 범위 밖에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-106">System role assignments exist outside of the scope of the report server namespace or folder hierarchy.</span></span> <span data-ttu-id="c49d3-107">시스템 역할 할당은 전역적이므로 특정 항목별로 다를 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-107">System role assignments are global and cannot vary for specific items.</span></span> <span data-ttu-id="c49d3-108">시스템 역할 할당을 통해 지원되는 작업에는 공유 일정 작성 및 사용, 보고서 작성기 사용, 일부 서버 기능에 대한 기본값 설정 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-108">Operations that are supported through system role assignments include creating and using shared schedules, using Report Builder, and setting default values for some server features.</span></span>  
  
 <span data-ttu-id="c49d3-109">기본 시스템 역할 할당은 보고서 서버를 설치할 때 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-109">A default system role assignment is created when the report server is installed.</span></span> <span data-ttu-id="c49d3-110">이 시스템 역할 할당은 로컬 시스템 관리자에게 보고서 서버 환경 관리 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-110">This system role assignment grants permissions to local system administrators to manage the report server environment.</span></span> <span data-ttu-id="c49d3-111">로컬 시스템 관리자는 시스템 역할 할당이 삭제되어도 항상 로컬 보고서 서버의 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-111">A local system administrator can always set security for a local report server, even if system role assignments are deleted.</span></span>  
  
 <span data-ttu-id="c49d3-112">보고서 작성기 또는 공유 일정에 액세스해야 하는 다른 모든 사용자는 시스템 역할 할당에 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-112">All other users who require access to Report Builder or shared schedules must be assigned to a system role assignment.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c49d3-113">탐색</span><span class="sxs-lookup"><span data-stu-id="c49d3-113">Navigation</span></span>  
 <span data-ttu-id="c49d3-114">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="c49d3-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-site-settings"></a><span data-ttu-id="c49d3-115">사이트 설정의 보안 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="c49d3-115">To open the Security page for Site Settings</span></span>  
  
1.  <span data-ttu-id="c49d3-116">보고서 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="c49d3-117">페이지의 맨 위에서 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-117">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="c49d3-118">사이트의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-118">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="c49d3-119">**보안** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-119">Select the **Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c49d3-120">옵션</span><span class="sxs-lookup"><span data-stu-id="c49d3-120">Options</span></span>  
 <span data-ttu-id="c49d3-121">**삭제**</span><span class="sxs-lookup"><span data-stu-id="c49d3-121">**Delete**</span></span>  
 <span data-ttu-id="c49d3-122">기존 역할 할당을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-122">Click to delete an existing role assignment.</span></span> <span data-ttu-id="c49d3-123">제거할 그룹 또는 사용자 이름 옆의 확인란을 선택한 다음에 **삭제**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="c49d3-123">Before clicking **Delete**, select the check box next to the group or user name that you want to remove.</span></span> <span data-ttu-id="c49d3-124">유일하게 남은 역할 할당은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-124">You cannot delete a role assignment if it is the only one remaining.</span></span> <span data-ttu-id="c49d3-125">역할 할당을 삭제해도 그룹 또는 사용자 계정이나 역할 정의는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-125">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="c49d3-126">**새 역할 할당**</span><span class="sxs-lookup"><span data-stu-id="c49d3-126">**New Role Assignment**</span></span>  
 <span data-ttu-id="c49d3-127">보고서 서버 사이트에 대한 추가 시스템 역할 할당을 만드는 데 사용되는 새 시스템 역할 할당 페이지를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-127">Click to open the New System Role Assignments page, which is used to create additional system role assignments for the report server site.</span></span> <span data-ttu-id="c49d3-128">자세한 내용은 [새 시스템 역할 할당: 시스템 역할 할당 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c49d3-128">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="c49d3-129">**편집**</span><span class="sxs-lookup"><span data-stu-id="c49d3-129">**Edit**</span></span>  
 <span data-ttu-id="c49d3-130">보고서 서버 사이트에 대한 개별 시스템 역할 할당을 편집하는 데 사용되는 시스템 역할 할당 편집 페이지를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-130">Click to open the Edit System Role Assignments page, which is used to edit individual system role assignments for the report server site.</span></span> <span data-ttu-id="c49d3-131">자세한 내용은 [새 시스템 역할 할당: 시스템 역할 할당 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c49d3-131">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="c49d3-132">**그룹 또는 사용자**</span><span class="sxs-lookup"><span data-stu-id="c49d3-132">**Group or User**</span></span>  
 <span data-ttu-id="c49d3-133">기존 역할 할당의 일부인 그룹 및 사용자를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-133">Lists the groups and users that are part of an existing role assignment.</span></span> <span data-ttu-id="c49d3-134">현재 폴더의 기존 역할 할당은 이 열에 표시되는 그룹과 사용자에 대해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-134">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="c49d3-135">역할 할당 정보를 보거나 편집하려면 그룹 또는 사용자 이름 옆에 있는 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-135">Click **Edit** next to a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="c49d3-136">**역할**</span><span class="sxs-lookup"><span data-stu-id="c49d3-136">**Roles**</span></span>  
 <span data-ttu-id="c49d3-137">기존 역할 할당에 속하는 하나 이상의 역할 정의를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-137">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="c49d3-138">그룹 또는 사용자 계정에 여러 역할이 할당되어 있으면 해당 그룹 또는 사용자는 모든 역할에 속한 모든 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-138">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to all roles.</span></span> <span data-ttu-id="c49d3-139">각 역할이 지 원하는 태스크 집합을 보려면를 사용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-139">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c49d3-140">보고서 관리자에서 역할을 확인, 작성, 수정 또는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c49d3-140">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="c49d3-141">지침은 [역할 만들기, 삭제 또는 수정 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c49d3-141">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49d3-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c49d3-142">See Also</span></span>  
 <span data-ttu-id="c49d3-143">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c49d3-143">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="c49d3-144">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="c49d3-144">Granting Permissions on a Native Mode Report Server</span></span>](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
