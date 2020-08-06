---
title: 보안 속성 페이지, 항목 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 297ae2ceefad89d64c59b5da25d51d541917c894
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649366"
---
# <a name="security-properties-page-items-report-manager"></a><span data-ttu-id="cbd6c-102">보안 속성 페이지, 항목(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="cbd6c-102">Security Properties Page, Items (Report Manager)</span></span>
  <span data-ttu-id="cbd6c-103">보안 속성 페이지를 사용하여 폴더, 보고서, 모델, 리소스 및 공유 데이터 원본에 대한 액세스를 지정하는 보안 설정을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-103">Use the Security properties page to view or modify the security settings that determine access to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="cbd6c-104">이 페이지는 보안 권한이 있는 항목에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-104">This page is available for items that you have permission to secure.</span></span>  
  
 <span data-ttu-id="cbd6c-105">항목에 대한 액세스는 그룹 또는 사용자가 수행할 수 있는 태스크를 지정하는 역할 할당을 통해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-105">Access to items is defined through role assignments that specify the tasks that a group or user can perform.</span></span> <span data-ttu-id="cbd6c-106">역할 할당은 하나의 사용자 또는 그룹 이름과 태스크 모음을 지정하는 하나 이상의 역할 정의로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-106">A role assignment consists of one user or group name and one or more role definitions that specify a collection of tasks.</span></span>  
  
 <span data-ttu-id="cbd6c-107">보안 설정은 루트 폴더의 하위 폴더 및 모든 항목으로 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-107">Security settings are inherited from the root folder down to subfolders and items within those folders.</span></span> <span data-ttu-id="cbd6c-108">상속된 보안을 명시적으로 해제하지 않는 한 하위 폴더와 항목은 부모 항목의 보안 컨텍스트를 상속 받습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-108">Unless you explicitly break inherited security, subfolders and items inherit the security context of a parent item.</span></span> <span data-ttu-id="cbd6c-109">계층의 가운데에 있는 폴더의 보안 정책을 다시 정의하면 하위 폴더를 포함한 모든 자식 항목에 새 보안 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-109">If you redefine a security policy for a folder in the middle of the hierarchy, all its child items, including subfolders, assume the new security settings.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="cbd6c-110">탐색</span><span class="sxs-lookup"><span data-stu-id="cbd6c-110">Navigation</span></span>  
 <span data-ttu-id="cbd6c-111">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-an-item"></a><span data-ttu-id="cbd6c-112">항목의 보안 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="cbd6c-112">To open the Security page for an item</span></span>  
  
1.  <span data-ttu-id="cbd6c-113">보고서 관리자를 열고 보안 설정을 구성하려는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-113">Open Report Manager, and locate the item for which you want to configure security settings.</span></span>  
  
2.  <span data-ttu-id="cbd6c-114">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-114">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="cbd6c-115">드롭다운 메뉴에서 다음 단계 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-115">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="cbd6c-116">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-116">Click **Security**.</span></span> <span data-ttu-id="cbd6c-117">항목의 보안 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-117">This opens the Security properties page for the item.</span></span>  
  
    -   <span data-ttu-id="cbd6c-118">**관리** 를 클릭하여 항목의 일반 속성 페이지를 연 다음</span><span class="sxs-lookup"><span data-stu-id="cbd6c-118">Click **Manage** to open the General properties page for the item.</span></span> <span data-ttu-id="cbd6c-119">**보안** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-119">Then select the **Security** tab.</span></span>  
  
 <span data-ttu-id="cbd6c-120">**항목 보안 편집**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-120">**Edit Item Security**</span></span>  
 <span data-ttu-id="cbd6c-121">현재 항목에 대한 보안 정의 방법을 변경하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-121">Click to change how security is defined for the current item.</span></span> <span data-ttu-id="cbd6c-122">폴더의 보안을 편집하면 변경 내용은 현재 폴더와 모든 하위 폴더의 내용에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-122">If you are editing security for a folder, your changes apply to the contents of the current folder and any subfolders.</span></span>  
  
 <span data-ttu-id="cbd6c-123">이 단추는 홈 폴더에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-123">This button is not available for the Home folder.</span></span>  
  
 <span data-ttu-id="cbd6c-124">항목 보안을 편집하는 경우 다음과 같은 단추를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-124">The following buttons become available when you edit item security.</span></span>  
  
 <span data-ttu-id="cbd6c-125">**삭제**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-125">**Delete**</span></span>  
 <span data-ttu-id="cbd6c-126">삭제할 그룹 또는 사용자 이름 옆의 확인란을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-126">Select the check box next to the group or user name that you want to delete and click **Delete**.</span></span> <span data-ttu-id="cbd6c-127">역할 할당이 하나뿐이거나 보고서 서버의 보안 기준을 정의하는 기본 제공 역할 할당(예: "Built-in\Administrators")인 경우에는 역할 할당을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-127">You cannot delete a role assignment if it is the only one remaining, or if it is a built-in role assignment (for example, "Built-in\Administrators") that defines the security baseline for the report server.</span></span> <span data-ttu-id="cbd6c-128">역할 할당을 삭제해도 그룹 또는 사용자 계정이나 역할 정의는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-128">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="cbd6c-129">**새 역할 할당**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-129">**New Role Assignment**</span></span>  
 <span data-ttu-id="cbd6c-130">현재 항목의 추가 역할 할당을 만드는 데 사용되는 새 역할 할당 페이지를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-130">Click to open the New Role Assignment page, which is used to create additional role assignments for the current item.</span></span> <span data-ttu-id="cbd6c-131">자세한 내용은 [새 역할 할당: 역할 할당 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-131">For more information, see [New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="cbd6c-132">**부모 보안으로 되돌리기**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-132">**Revert to Parent Security**</span></span>  
 <span data-ttu-id="cbd6c-133">보안 설정을 직속 부모 폴더의 보안 설정으로 되돌리려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-133">Click to reset the security settings to that of the immediate parent folder.</span></span> <span data-ttu-id="cbd6c-134">보고서 서버 폴더 계층 구조 전체에서 상속이 손상되지 않은 경우에는 최상위 폴더(홈)의 보안 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-134">If inheritance is unbroken throughout the report server folder hierarchy, the security settings of the top-level folder, Home, are used.</span></span>  
  
 <span data-ttu-id="cbd6c-135">**그룹 또는 사용자**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-135">**Group or User**</span></span>  
 <span data-ttu-id="cbd6c-136">현재 항목에 대한 기존 역할 할당의 일부인 그룹 및 사용자를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-136">Lists the groups and users that are part of an existing role assignment for the current item.</span></span> <span data-ttu-id="cbd6c-137">현재 폴더의 기존 역할 할당은 이 열에 표시되는 그룹과 사용자에 대해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-137">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="cbd6c-138">그룹 또는 사용자 이름을 클릭하여 역할 할당의 세부 사항을 보거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-138">You can click a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="cbd6c-139">**역할**</span><span class="sxs-lookup"><span data-stu-id="cbd6c-139">**Roles**</span></span>  
 <span data-ttu-id="cbd6c-140">기존 역할 할당에 속하는 하나 이상의 역할 정의를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-140">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="cbd6c-141">그룹 또는 사용자 계정에 여러 역할이 할당되어 있으면 해당 그룹 또는 사용자는 이러한 역할에 속한 모든 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-141">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to those roles.</span></span> <span data-ttu-id="cbd6c-142">역할에 연결되어 있는 태스크를 보려면 SQL Server Management Studio를 사용하여 각 역할 정의의 태스크를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cbd6c-142">To view the tasks that are associated with a role, use SQL Server Management Studio to view the tasks in each role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd6c-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbd6c-143">See Also</span></span>  
 <span data-ttu-id="cbd6c-144">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="cbd6c-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="cbd6c-145">[미리 정의 된 역할](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="cbd6c-145">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="cbd6c-146">[기본 모드 보고서 서버에 대한 사용 권한 부여](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="cbd6c-146">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="cbd6c-147">[역할 할당](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="cbd6c-147">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="cbd6c-148">역할 정의</span><span class="sxs-lookup"><span data-stu-id="cbd6c-148">Role Definitions</span></span>](security/role-definitions.md)  
  
  
