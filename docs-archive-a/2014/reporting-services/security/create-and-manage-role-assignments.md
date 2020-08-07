---
title: 역할 할당 생성 및 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2064e2a6d4dda99ed6b8b61de363b84d073d8ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731404"
---
# <a name="create-and-manage-role-assignments"></a><span data-ttu-id="57345-102">역할 할당 생성 및 관리</span><span class="sxs-lookup"><span data-stu-id="57345-102">Create and Manage Role Assignments</span></span>
  <span data-ttu-id="57345-103">*역할 할당* 은 사용자 또는 그룹이 특정 보고서 서버 항목에 액세스하거나 작업을 수행할 수 있는지 여부를 결정하는 보안 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="57345-103">A *role assignment* is a security policy that determines whether a user or group can access a specific report server item or perform an operation.</span></span> <span data-ttu-id="57345-104">역할 할당은 단일 사용자 또는 그룹 계정 이름과 하나 이상의 역할 정의로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="57345-104">A role assignment consists of a single user or group account name and one or more role definitions.</span></span>  
  
 <span data-ttu-id="57345-105">역할 할당의 범위는 *항목 수준* 또는 *시스템 수준*입니다.</span><span class="sxs-lookup"><span data-stu-id="57345-105">Role assignments are scoped to the *item level* or *system level*.</span></span>  
  
-   <span data-ttu-id="57345-106">항목 수준 역할 할당은 항상 보고서 서버 폴더 계층에 있는 특정 항목 또는 분기의 컨텍스트에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="57345-106">An item-level role assignment is always created in the context of a specific item or branch in the report server folder hierarchy.</span></span> <span data-ttu-id="57345-107">특정 폴더 또는 항목으로 이동하여 해당 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="57345-107">You navigate to a specific folder or item to create a role assignment for it.</span></span>  
  
-   <span data-ttu-id="57345-108">시스템 수준 역할 할당은 보고서 서버 사이트 전체에 영향을 주는 태스크를 수행할 수 있는 기능을 선택한 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-108">System-level role assignments give selected users the capability to perform tasks that affect the report server site as a whole.</span></span> <span data-ttu-id="57345-109">이러한 태스크에는 공유 일정 만들기, 작업 관리, 보고서 작성기에서 보고서 처리, 속성 설정 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-109">These tasks include creating shared schedules, managing jobs, processing reports in Report Builder, and setting properties.</span></span> <span data-ttu-id="57345-110">시스템 수준 보안은 보고서 서버 폴더 계층에 있는 항목에 대한 액세스를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-110">System-level security does not convey access to items in the report server folder hierarchy.</span></span>  
  
## <a name="creating-an-item-level-role-assignment"></a><span data-ttu-id="57345-111">항목 수준 역할 할당 만들기</span><span class="sxs-lookup"><span data-stu-id="57345-111">Creating an Item-level Role Assignment</span></span>  
 <span data-ttu-id="57345-112">역할 할당을 만들거나 관리하려면 보고서 관리자를 사용하여 보안을 설정할 항목의 보안 속성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57345-112">To create or manage role assignments, use Report Manager and open the Security property pages of the item that you want to secure.</span></span>  
  
 <span data-ttu-id="57345-113">보고서 서버에 액세스해야 하는 각 사용자 또는 그룹 계정에 대해 별도의 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-113">You must create a separate role assignment for each user or group account that requires access to the report server.</span></span> <span data-ttu-id="57345-114">계정이 보고서 서버를 포함하지 않는 도메인에 있는 경우 해당 도메인 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-114">If the account is on a domain other than the one that contains the report server, include the domain name.</span></span> <span data-ttu-id="57345-115">계정을 지정한 후 하나 이상의 역할 정의를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-115">After you specify an account, you can choose one or more role definitions.</span></span> <span data-ttu-id="57345-116">역할 정의는 계속 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-116">The role definitions are additive.</span></span> <span data-ttu-id="57345-117">특정 사용자 또는 그룹에 대한 할당에서는 모든 정의에 포함되어 있는 태스크를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-117">The combined set of all tasks from all definitions are supported in the assignment for a particular user or group.</span></span>  
  
 <span data-ttu-id="57345-118">광범위한 액세스 권한을 설정하려면 폴더 계층에서 높은 수준의 항목(예: 루트 노드 홈)을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-118">To enable widespread access, you should choose an item that is high in the folder hierarchy (for example, the root node Home).</span></span> <span data-ttu-id="57345-119">그런 다음 후속 역할 할당을 만들어 폴더 계층의 특정 영역을 잠글 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-119">You can then create subsequent role assignments to lock down specific areas of the folder hierarchy.</span></span>  
  
 <span data-ttu-id="57345-120">역할 할당을 만들려면 보고서 서버 컴퓨터에서 사용자가 로컬 관리자 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-120">You must be a member of the local Administrator's group on the report server computer to create a role assignment.</span></span> <span data-ttu-id="57345-121">다른 사용자를 **내용 관리자** 역할에 할당하여 책임을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-121">You can delegate that responsibility by assigning other users to the **Content Manager** role.</span></span>  
  
 <span data-ttu-id="57345-122">자세한 내용은 [사용자에 게 보고서 서버에 대 한 액세스 권한 부여 &#40;보고서 관리자&#41;](grant-user-access-to-a-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57345-122">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="creating-a-system-level-role-assignment"></a><span data-ttu-id="57345-123">시스템 수준 역할 할당 만들기</span><span class="sxs-lookup"><span data-stu-id="57345-123">Creating a System-level Role Assignment</span></span>  
 <span data-ttu-id="57345-124">시스템 수준 역할 할당을 만들거나 관리하려면 보고서 관리자를 사용하여 사이트 설정 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57345-124">To create or manage a system-level role assignment, use Report Manager and open the Site Settings page.</span></span>  
  
 <span data-ttu-id="57345-125">시스템 수준 역할 할당과 항목 수준 역할 할당은 함께 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-125">System-level and item-level role assignments go together.</span></span> <span data-ttu-id="57345-126">즉, 항목 수준 역할 할당이 있는 각 사용자 또는 그룹에 대해 시스템 수준 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-126">You should create a system-level role assignment for each user or group that has an item-level role assignment.</span></span>  
  
 <span data-ttu-id="57345-127">시스템 수준 역할 할당에는 다양한 범위의 사용 권한이 포함되지만 항목 수준 역할 할당의 일부인 사용 권한은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-127">System-level role assignments include a wide range of permissions, but they do not include permissions that are part of an item-level role assignment.</span></span> <span data-ttu-id="57345-128">컴퓨터의 시스템 사용 권한과는 반대로 보고 서버의 시스템 역할은 사용 가능한 모든 작업 집합을 포함하는 가장 중요한 사용 권한을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-128">In contrast with system permissions on a computer, system roles in Reporting Servers do not convey overarching permissions that include the full set of all possible operations.</span></span> <span data-ttu-id="57345-129">대신 시스템 수준 역할 할당은 범위가 보고서 서버 사이트로 제한되는 태스크 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="57345-129">Instead, system-level role assignments are simply a set of tasks that are scoped to the report server site.</span></span> <span data-ttu-id="57345-130">시스템 역할 할당을 통해 제공되는 사용 권한은 사용자가 홈 페이지의 이미지 또는 제목과 같은 애플리케이션 속성을 볼 수 있는지 여부, 공유 일정을 보거나 관리할 수 있는지 여부 또는 보고서 작성기를 사용할 수 있는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-130">Permissions that are conveyed through system role assignments determine whether users can view application properties (such as the image or title of the Home page), view or manage shared schedules, or use Report Builder.</span></span>  
  
 <span data-ttu-id="57345-131">자세한 내용은 [사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;](grant-user-access-to-a-report-server.md) 및 [미리 정의된 역할](role-definitions-predefined-roles.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="57345-131">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) and [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="modifying-a-role-assignment"></a><span data-ttu-id="57345-132">역할 할당 수정</span><span class="sxs-lookup"><span data-stu-id="57345-132">Modifying a Role Assignment</span></span>  
 <span data-ttu-id="57345-133">언제든지 역할 할당을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-133">You can modify a role assignment at any time.</span></span> <span data-ttu-id="57345-134">역할 할당을 저장하면 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="57345-134">Your changes take effect when you save the role assignment.</span></span> <span data-ttu-id="57345-135">사용자 세션에는 역할 할당 변경 사항이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-135">User sessions are not affected by role assignment changes.</span></span> <span data-ttu-id="57345-136">한 사용자가 보고서를 열어 둔 상태에서 액세스를 거부하도록 역할 할당을 수정한 경우에도 해당 사용자는 세션이 열려 있는 동안에는 보고서를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-136">If a user has a report open, and you modify a role assignment to deny access, the user can continue using the report as long as the session is active.</span></span>  
  
 <span data-ttu-id="57345-137">이미 역할 할당의 일부인 그룹에 사용자 계정을 추가하면 해당 사용자 계정이 그룹 계정 정책을 통해 항목에 액세스할 수 있을 때까지 지연이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-137">If you add a user account to a group that is already part of a role assignment, there will be a delay before the user account is able to access items through the group account policies.</span></span> <span data-ttu-id="57345-138">이러한 지연은 인터넷 정보 서비스(IIS)의 인증 토큰 캐싱으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="57345-138">This delay is caused by Internet Information Services (IIS) caching of authentication tokens.</span></span> <span data-ttu-id="57345-139">토큰을 새로 고칠 때까지 기다리거나(일반적으로 대기 시간은 15분) IIS를 다시 설정하여 캐시를 즉시 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-139">You can either wait for the tokens to refresh (typically, the wait period is fifteen minutes) or you can reset IIS to update the cache immediately.</span></span>  
  
 <span data-ttu-id="57345-140">역할 할당은 한 번에 하나씩만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-140">You can only modify one role assignment at a time.</span></span> <span data-ttu-id="57345-141">전역 찾기 및 바꾸기 작업을 수행하여 역할 정의 이름 또는 역할 할당 설정을 변경하거나 특정 사용자 또는 그룹이 포함된 모든 역할 할당을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-141">You cannot perform a global search-and-replace operation to change role definition names or role assignment settings, or to find all the role assignments that include a specific user or group.</span></span>  
  
## <a name="deleting-a-role-assignment"></a><span data-ttu-id="57345-142">역할 할당 삭제</span><span class="sxs-lookup"><span data-stu-id="57345-142">Deleting a Role Assignment</span></span>  
 <span data-ttu-id="57345-143">삭제할 각 할당에 해당하는 확인란을 선택한 다음 **삭제**를 클릭하여 역할 할당을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-143">You can delete role assignments by selecting the checkbox by each assignment you want to delete, and then clicking **Delete**.</span></span> <span data-ttu-id="57345-144">**부모 보안으로 되돌리기**를 클릭하여 역할 할당을 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57345-144">You can also delete role assignments by clicking **Revert to Parent Security**.</span></span> <span data-ttu-id="57345-145">이 단추를 클릭하면 항목에 대한 기존 역할 할당이 삭제되고 부모 항목을 통해 제공되는 역할 할당이 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="57345-145">When you click this button, the existing role assignments for the item are deleted, and those that are provided through a parent item are used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57345-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57345-146">See Also</span></span>  
 <span data-ttu-id="57345-147">[보고서 관리자&#41;&#40;보고서 서버에 대 한 사용자 액세스 권한 부여](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="57345-147">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="57345-148">[역할 할당을 수정 하거나 삭제 &#40;보고서 관리자&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="57345-148">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="57345-149">[역할 할당](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="57345-149">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="57345-150">[역할 정의](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="57345-150">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="57345-151">[미리 정의 된 역할](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="57345-151">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="57345-152">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="57345-152">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
