---
title: '새 역할 할당: 역할 할당 편집 페이지 (보고서 관리자) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1640617dbf9836986597ee49d4ca1ddc37fd84ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738025"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a><span data-ttu-id="3efe2-102">새 역할 할당: 역할 할당 편집 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="3efe2-102">New Role Assignment: Edit Role Assignment Page (Report Manager)</span></span>
  <span data-ttu-id="3efe2-103">새 역할 할당 또는 역할 할당 편집 페이지를 사용하여 보고서 서버 항목 및 작업에 대한 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-103">Use the New Role Assignment or Edit Role Assignment page to grant permissions to report server items and operations.</span></span> <span data-ttu-id="3efe2-104">보고서 서버에 액세스해야 하는 각 사용자에게는 액세스의 수준을 정의하는 역할 할당이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-104">Each user who requires access to a report server must have a role assignment that defines the level of access.</span></span> <span data-ttu-id="3efe2-105">루트 노드 또는 특정 보고서, 모델, 폴더, 리소스 또는 공유 데이터 원본에 대해 역할 할당을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-105">You can create role assignments at the root node, or on a specific report, model, folder, resource, or shared data source.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="3efe2-106">보안은 항목에 적용하는 역할 할당을 통해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-106">security is enforced through role assignments that you apply to items.</span></span> <span data-ttu-id="3efe2-107">역할 할당에 따라 역할 정의가 그룹이나 사용자에 대응되며 각 역할 정의는 그룹이나 사용자가 특정 항목과 관련하여 수행할 수 있는 태스크를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-107">A role assignment matches a group or user to a role definition, where each role definition identifies the tasks that groups or users can perform with regards to a specific item.</span></span>  
  
 <span data-ttu-id="3efe2-108">항목 수준 역할 할당은 광범위한 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-108">Item-level role assignments can have a broad impact.</span></span> <span data-ttu-id="3efe2-109">이러한 할당은 단일 보고서나 폴더에 연결될 수도 있지만 폴더 계층 구조의 상위 수준에서 정의되어 트리의 하위 항목 및 폴더로 상속될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-109">Although they can be associated with a single report or folder, they can also be defined at a high level in the folder hierarchy and be inherited by folders and items that are lower in the tree.</span></span> <span data-ttu-id="3efe2-110">자세한 내용은 [사용자에 게 보고서 서버에 대 한 액세스 권한 부여 &#40;보고서 관리자&#41;](security/grant-user-access-to-a-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3efe2-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](security/grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="3efe2-111">탐색</span><span class="sxs-lookup"><span data-stu-id="3efe2-111">Navigation</span></span>  
 <span data-ttu-id="3efe2-112">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="3efe2-112">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a><span data-ttu-id="3efe2-113">새 역할 할당 또는 역할 할당 편집 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="3efe2-113">To open the New Role Assignment or Edit Role Assignment page</span></span>  
  
1.  <span data-ttu-id="3efe2-114">보고서 관리자를 열고 새 역할 할당을 추가하거나 역할 할당을 편집하려는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-114">Open Report Manager, and locate an item for which you want to add a new role assignment or edit a role assignment.</span></span>  
  
2.  <span data-ttu-id="3efe2-115">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-115">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="3efe2-116">드롭다운 메뉴에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-116">In the drop-down menu, click **Security**.</span></span> <span data-ttu-id="3efe2-117">항목의 보안 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-117">This opens the Security properties page for the item.</span></span>  
  
4.  <span data-ttu-id="3efe2-118">새 역할 할당을 추가하려면 도구 모음에서 **새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-118">If you want to add a new role assignment, in the toolbar, click **New Role Assignment**.</span></span> <span data-ttu-id="3efe2-119">역할 할당을 편집하려면 편집할 그룹이나 사용자 이름 옆에 있는 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-119">If you want to edit a role assignment, click **Edit** next to the group or user name you want to edit.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3efe2-120"> 항목이 현재 부모 항목의 보안을 상속하는 경우에는 도구 모음에서 **항목 보안 편집** 을 클릭하여 보안 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-120">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3efe2-121">옵션</span><span class="sxs-lookup"><span data-stu-id="3efe2-121">Options</span></span>  
 <span data-ttu-id="3efe2-122">**그룹 또는 사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="3efe2-122">**Group or User Name**</span></span>  
 <span data-ttu-id="3efe2-123">역할 할당을 만들 그룹 또는 사용자 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-123">Type the name of a group or user account for which the role assignment is being created.</span></span> <span data-ttu-id="3efe2-124">그룹 또는 사용자 이름은 올바른 Windows 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-124">The group or user name must be a valid Windows domain account.</span></span> <span data-ttu-id="3efe2-125">계정을<계정 형식으로 입력 \<domain> \\ \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-125">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3efe2-126">이 입력란은 새 역할 할당 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-126">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="3efe2-127">**역할**</span><span class="sxs-lookup"><span data-stu-id="3efe2-127">**Role**</span></span>  
 <span data-ttu-id="3efe2-128">항목의 보안을 정의하는 데 사용할 수 있는 보고서 서버에 정의된 모든 역할을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-128">Shows all roles defined on the report server that can be used to define security for items.</span></span> <span data-ttu-id="3efe2-129">보고서 또는 폴더에 대한 역할 할당을 만들거나 변경할 경우에는 하나 이상의 역할을 선택하면서 태스크 조합에 사용자가 수행할 수 있는 동작이 나타나도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-129">When you create or change a role assignment for a report or folder, select one or more roles until the combined set of tasks describe the actions that the user should be allowed to perform.</span></span> <span data-ttu-id="3efe2-130">각 역할이 지 원하는 태스크 집합을 보려면를 사용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-130">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="3efe2-131">보고서 관리자에서 역할을 확인, 작성, 수정 또는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-131">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="3efe2-132">지침은 [역할 만들기, 삭제 또는 수정 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3efe2-132">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="3efe2-133">**설명**</span><span class="sxs-lookup"><span data-stu-id="3efe2-133">**Description**</span></span>  
 <span data-ttu-id="3efe2-134">역할에 대한 추가 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-134">Shows additional information about the role.</span></span> <span data-ttu-id="3efe2-135">**브라우저** 또는 **내용 관리자**와 같은 미리 정의된 역할의 설명에는 각 역할이 지원하는 태스크가 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-135">For predefined roles such as **Browser** or **Content Manager**, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="3efe2-136">**역할 할당 삭제**</span><span class="sxs-lookup"><span data-stu-id="3efe2-136">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="3efe2-137">사용자나 그룹의 기존 역할 할당을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-137">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="3efe2-138">역할 할당이 하나만 남아 있는 경우 역할 할당을 삭제할 수 없습니다. 각 항목에는 역할 할당이 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-138">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3efe2-139">이 단추는 역할 할당 편집 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efe2-139">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efe2-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3efe2-140">See Also</span></span>  
 <span data-ttu-id="3efe2-141">[Management Studio &#40;역할을 만들거나, 삭제 하거나, 수정&#41;](security/role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="3efe2-141">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="3efe2-142">[기본 모드 보고서 서버에 대한 사용 권한 부여](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="3efe2-142">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="3efe2-143">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3efe2-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="3efe2-144">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3efe2-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="3efe2-145">[역할 할당](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="3efe2-145">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="3efe2-146">사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="3efe2-146">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](security/grant-user-access-to-a-report-server.md)  
  
  
