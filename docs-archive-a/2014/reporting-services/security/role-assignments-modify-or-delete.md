---
title: 역할 할당 수정 또는 삭제(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d67c5cdb7647d50008f72890e4ac3e3c7eed456e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732392"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a><span data-ttu-id="5ea56-102">역할 할당 수정 또는 삭제(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="5ea56-102">Modify or Delete a Role Assignment (Report Manager)</span></span>
  <span data-ttu-id="5ea56-103">역할 할당은 수행할 수 있는 태스크를 포함하는 미리 정의된 역할 정의에 그룹 또는 사용자 계정을 매핑하며</span><span class="sxs-lookup"><span data-stu-id="5ea56-103">A role assignment maps a group or user account to a predefined role definition that includes tasks that can be performed.</span></span> <span data-ttu-id="5ea56-104">폴더, 보고서, 모델 또는 기타 내용 유형에 상대적으로 수행할 수 있는 작업 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-104">It determines the types of operations that a user can perform relative to a folder, report, model, or other content type.</span></span> <span data-ttu-id="5ea56-105">역할 할당을 만들거나 수정하거나 삭제하려면 보고서 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-105">To create, modify, or delete role assignments, you use Report Manager.</span></span> <span data-ttu-id="5ea56-106">특정 사용자 또는 그룹에 대한 역할 할당을 만든 후에는 나중에 다른 역할을 선택하여 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-106">After you create a role assignment for a particular user or group, you can modify it later by selecting a different role.</span></span> <span data-ttu-id="5ea56-107">보고서 서버에 대한 사용 권한을 취소하려면 보고서 서버에서 역할 할당을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-107">If you want to revoke permissions to a report server, you can delete a role assignment from the report server.</span></span>  
  
 <span data-ttu-id="5ea56-108">목적에 따라 적합한 방법이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-108">Depending on your objective, alternative approaches might be more appropriate.</span></span> <span data-ttu-id="5ea56-109">새 역할 정의 사용자 지정 또는 만들기, Active Directory에서 그룹 계정의 멤버 자격 수정 등의 목적이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-109">Examples include customizing or creating a new role definition, or modifying the membership of a group account in Active Directory.</span></span>  
  
 <span data-ttu-id="5ea56-110">예를 들어 자신이 작성한 내용을 완전히 관리해야 하지만 내용 관리자와 관련된 전체 권한 집합을 가져서는 안 되는 사용자 그룹이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-110">For example, suppose you have a group of users who need to fully manage their content, but should not have the full set of permissions associated with Content Manager.</span></span> <span data-ttu-id="5ea56-111">이 경우 내용 관리자에서 **항목의 보안 정책 설정**을 제외한 모든 태스크를 포함하는 부서 내용 관리자라고 하는 새 역할 정의를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-111">In this case, you could create a new role definition called Department Content Manager that includes all of the tasks in Content Manager except **Set security policies for items**.</span></span>  
  
 <span data-ttu-id="5ea56-112">마찬가지로 시스템 또는 네트워크 관리자가 보고서 관리자의 역할 할당보다 Active Directory 그룹 계정을 관리하기가 더 쉬운 경우 그룹 계정에 대한 단일 역할 할당을 만들어 역할 할당 관리로 발생하는 오버헤드를 줄이고 사용자가 보고서에 더 이상 액세스하지 않아도 되는 경우 그룹 멤버 자격을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-112">Similarly, if you are a system or network administrator and it is easier for you to manage Active Directory group accounts than role assignments in Report Manager, you could reduce the overhead of managing role assignments by creating a single role assignment for a group account, and then adjust group membership when users no longer require access to reports.</span></span>  
  
 <span data-ttu-id="5ea56-113">역할 할당을 수정하거나 삭제하는 것이 적합하다고 판단되면 시스템 역할 할당과 항목 역할 할당을 모두 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ea56-113">If you determine that modifying or deleting a role assignment is the best approach, remember to check for both system role assignments and item role assignments.</span></span> <span data-ttu-id="5ea56-114">각 유형의 역할 할당은 보고서 관리자의 서로 다른 페이지에서 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-114">Each type of role assignment is configured through different pages in Report Manager.</span></span>  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a><span data-ttu-id="5ea56-115">시스템 역할 할당을 수정하거나 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="5ea56-115">To modify or delete a system role assignment</span></span>  
  
1.  <span data-ttu-id="5ea56-116">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="5ea56-117">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-117">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="5ea56-118">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-118">Click **Security**.</span></span> <span data-ttu-id="5ea56-119">서버 또는 스케일 아웃 배포에 대해 현재 정의된 모든 시스템 수준 역할 할당이 계정 이름별로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-119">All system-level role assignments currently defined for the server or scale-out deployment are listed by account name.</span></span>  
  
4.  <span data-ttu-id="5ea56-120">수정하거나 삭제할 역할 할당을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-120">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="5ea56-121">특정 사용자 또는 그룹에 대한 역할을 추가하거나 제거하려면 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-121">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="5ea56-122">역할 할당을 삭제하려면 사용자 또는 그룹 이름 옆의 확인란을 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-122">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a><span data-ttu-id="5ea56-123">항목 역할 할당을 수정하거나 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="5ea56-123">To modify or delete an item role assignment</span></span>  
  
1.  <span data-ttu-id="5ea56-124">**보고서 관리자** 를 시작하고 역할 할당을 편집하거나 삭제하려는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-124">Start **Report Manager** and locate the item for which you want to edit or delete a role assignment.</span></span>  
  
2.  <span data-ttu-id="5ea56-125">항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-125">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="5ea56-126">드롭다운 메뉴에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-126">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="5ea56-127">수정하거나 삭제할 역할 할당을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-127">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="5ea56-128">특정 사용자 또는 그룹에 대한 역할을 추가하거나 제거하려면 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-128">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="5ea56-129">역할 할당을 삭제하려면 사용자 또는 그룹 이름 옆의 확인란을 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-129">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea56-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ea56-130">See Also</span></span>  
 <span data-ttu-id="5ea56-131">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="5ea56-131">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="5ea56-132">[역할 할당](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="5ea56-132">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="5ea56-133">[사이트 설정 페이지 &#40;보고서 관리자&#41;](../site-settings-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5ea56-133">[Site Settings Page &#40;Report Manager&#41;](../site-settings-page-report-manager.md) </span></span>  
 [<span data-ttu-id="5ea56-134">새 시스템 역할 할당: 시스템 역할 할당 편집 페이지&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="5ea56-134">New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;</span></span>](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)  
  
  
