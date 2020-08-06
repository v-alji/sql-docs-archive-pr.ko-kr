---
title: '새 시스템 역할 할당: 시스템 역할 할당 편집 페이지 (보고서 관리자) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e04ec18b8ee27c5897156753c1e4f7991991eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647497"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a><span data-ttu-id="70e20-102">새 시스템 역할 할당: 시스템 역할 할당 편집 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="70e20-102">New System Role Assignments: Edit System Role Assignments Page (Report Manager)</span></span>
  <span data-ttu-id="70e20-103">새 시스템 역할 할당 또는 시스템 역할 할당 편집 페이지를 사용하여 보고서 서버의 보안을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-103">Use the New System Role Assignments or Edit System Role Assignments page to define security for the report server.</span></span> <span data-ttu-id="70e20-104">모든 보안은 특정 사용자나 그룹을 각기 수행 가능한 태스크에 매핑하는 역할 할당을 통해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-104">All security is defined through role assignments that map specific users or groups to the tasks that they can perform.</span></span> <span data-ttu-id="70e20-105">태스크 목록은 역할 할당을 만들 때 선택하는 역할 정의로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-105">The task list is represented as a role definition that you select when making the role assignment.</span></span>  
  
 <span data-ttu-id="70e20-106">시스템 수준에서 만들거나 수정하는 역할 할당은 보고서 서버 전체에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-106">At the system level, the role assignments that you create or modify apply to the report server as a whole.</span></span> <span data-ttu-id="70e20-107">예를 들어 공유 일정은 시스템 전체에서 사용되므로 공유 일정을 만드는 기능은 시스템 수준에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-107">For example, the ability to create shared schedules is specified at the system level because shared schedules are used throughout the system.</span></span>  
  
 <span data-ttu-id="70e20-108">기본적으로 Reporting Services는 다음과 같은 두 개의 미리 정의된 시스템 수준 역할을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-108">By default, Reporting Services provides two predefined system level roles:</span></span>  
  
-   <span data-ttu-id="70e20-109">시스템 사용자에는 사용자가 보고서 서버 속성과 공유 일정을 보도록 허용하는 태스크와 사용자가 보고서 서버에 게시된 클릭 광고 보고서를 보도록 허용하는 보고서 정의 실행 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-109">System User includes tasks that allow users to view report server properties and shared schedules, and to execute report definitions, which allows users to view clickthrough reports that have been published to the report server.</span></span> <span data-ttu-id="70e20-110">대부분의 사용자는 이 역할에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-110">Most users should be assigned to this role.</span></span>  
  
-   <span data-ttu-id="70e20-111">시스템 관리자에는 공유 일정 작성 및 관리, 서버 속성 설정, 다른 사용자에 대한 시스템 수준 역할 할당 생성을 위한 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-111">System Administrator includes tasks for creating and managing shared schedules, setting server properties, and creating system-level role assignments for other users.</span></span> <span data-ttu-id="70e20-112">이 수준의 권한이 필요한 사용자는 극소수입니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-112">Few users require permissions at this level.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="70e20-113">탐색</span><span class="sxs-lookup"><span data-stu-id="70e20-113">Navigation</span></span>  
 <span data-ttu-id="70e20-114">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="70e20-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a><span data-ttu-id="70e20-115">새 시스템 역할 할당 또는 시스템 역할 할당 편집 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="70e20-115">To open the New System Role Assignments or Edit System Role Assignments page</span></span>  
  
1.  <span data-ttu-id="70e20-116">보고서 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="70e20-117">페이지 맨 위에서 오른쪽 모퉁이에 있는 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-117">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="70e20-118">사이트의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-118">This opens the General properties page for the site.</span></span>  
  
3.  <span data-ttu-id="70e20-119">**보안** 탭을 선택 합니다. 이 페이지에 액세스 하려면 내용 관리자 및 시스템 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-119">Select the **Security** tab. You must have Content Manager and System Administrator permissions to access this page.</span></span>  
  
4.  <span data-ttu-id="70e20-120">새 역할 할당을 만들려면 도구 모음에서 **새 역할 할당** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-120">To create a new role assignment, click **New Role Assignment** in the toolbar.</span></span> <span data-ttu-id="70e20-121">기존 역할 할당을 편집하려면 보안 속성 페이지에서 그룹이나 사용자 옆에 있는 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-121">To edit an existing role assignment, click **Edit** next to a group or user on the Security properties page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70e20-122">옵션</span><span class="sxs-lookup"><span data-stu-id="70e20-122">Options</span></span>  
 <span data-ttu-id="70e20-123">**그룹 또는 사용자**</span><span class="sxs-lookup"><span data-stu-id="70e20-123">**Group or User**</span></span>  
 <span data-ttu-id="70e20-124">사용자 도메인의 그룹 또는 사용자 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-124">Type the name of a group or user account in your domain.</span></span> <span data-ttu-id="70e20-125">보고서 서버가 로컬 계정으로 실행되고 있는 경우에는 로컬 그룹 또는 사용자를 지정해야 하고,</span><span class="sxs-lookup"><span data-stu-id="70e20-125">If the report server is running under a local account, you must specify local groups or users.</span></span> <span data-ttu-id="70e20-126">보고서 서버가 도메인 계정으로 실행되고 있는 경우에는 도메인 그룹 또는 사용자를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-126">If the report server is running under a domain account, you must specify domain groups or users.</span></span> <span data-ttu-id="70e20-127">계정을<계정 형식으로 입력 \<domain> \\ \> 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-127">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70e20-128">이 입력란은 새 역할 할당 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-128">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="70e20-129">**역할**</span><span class="sxs-lookup"><span data-stu-id="70e20-129">**Roles**</span></span>  
 <span data-ttu-id="70e20-130">다른 사용자에게 할당할 수 있는 시스템 수준 역할의 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-130">Provides a list of system-level roles that you can assign to other users.</span></span> <span data-ttu-id="70e20-131">하나의 역할 할당에 대해 여러 역할을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-131">You can specify multiple roles for a single role assignment.</span></span>  
  
 <span data-ttu-id="70e20-132">보고서 관리자는 각 역할의 태스크를 표시하지 않으며 태스크를 추가 또는 수정하는 방법을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-132">Report Manager does not display the tasks in each role or provide a way to add or modify the tasks.</span></span> <span data-ttu-id="70e20-133">정의된 그대로 역할을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-133">You must use the roles as they are defined.</span></span> <span data-ttu-id="70e20-134">역할을 만들거나, 수정 하거나, 삭제 하려면를 사용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-134">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="70e20-135">자세한 내용은 [역할 만들기, 삭제 또는 수정&#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70e20-135">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="70e20-136">[!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services를 사용하는 경우에는 제공된 기본 역할을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-136">Note that if you are using [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, you must use the default roles that are provided.</span></span>  
  
 <span data-ttu-id="70e20-137">**설명**</span><span class="sxs-lookup"><span data-stu-id="70e20-137">**Descriptions**</span></span>  
 <span data-ttu-id="70e20-138">역할에 대한 추가 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-138">Shows additional information about the role.</span></span> <span data-ttu-id="70e20-139">시스템 사용자 또는 시스템 관리자와 같은 미리 정의된 역할의 경우 설명에는 각 역할이 지원하는 태스크가 요약되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-139">For predefined roles such as System User or System Administrator, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="70e20-140">**역할 할당 삭제**</span><span class="sxs-lookup"><span data-stu-id="70e20-140">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="70e20-141">사용자나 그룹의 기존 역할 할당을 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-141">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="70e20-142">역할 할당이 하나만 남아 있는 경우 역할 할당을 삭제할 수 없습니다. 각 항목에는 역할 할당이 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-142">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70e20-143">이 단추는 역할 할당 편집 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e20-143">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e20-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70e20-144">See Also</span></span>  
 <span data-ttu-id="70e20-145">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="70e20-145">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="70e20-146">[역할 할당](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="70e20-146">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="70e20-147">역할 정의</span><span class="sxs-lookup"><span data-stu-id="70e20-147">Role Definitions</span></span>](security/role-definitions.md)  
  
  
