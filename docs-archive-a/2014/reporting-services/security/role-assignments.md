---
title: 역할 할당 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f156a009dfce8d91c3d3c8460160a4fdad62b573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651479"
---
# <a name="role-assignments"></a><span data-ttu-id="e17f2-102">역할 할당</span><span class="sxs-lookup"><span data-stu-id="e17f2-102">Role Assignments</span></span>
  <span data-ttu-id="e17f2-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 *역할 할당* 은 저장된 항목 및 보고서 서버 자체에 대한 액세스 권한을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], *role assignments* determine access to stored items and to the report server itself.</span></span> <span data-ttu-id="e17f2-104">역할 할당은 다음과 같은 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-104">A role assignment has the following parts:</span></span>  
  
-   <span data-ttu-id="e17f2-105">액세스 권한을 제어하려는 보안 개체 항목.</span><span class="sxs-lookup"><span data-stu-id="e17f2-105">A securable item for which you want to control access.</span></span> <span data-ttu-id="e17f2-106">보안 개체 항목의 예로는 폴더, 보고서, 리소스 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-106">Examples of securable items include folders, reports, and resources.</span></span>  
  
-   <span data-ttu-id="e17f2-107">Windows 보안 또는 기타 인증 메커니즘을 통해 인증할 수 있는 사용자 또는 그룹 계정</span><span class="sxs-lookup"><span data-stu-id="e17f2-107">A user or group account that can be authenticated by Windows security or another authentication mechanism.</span></span>  
  
-   <span data-ttu-id="e17f2-108">태스크 집합을 정의하는 역할 정의.</span><span class="sxs-lookup"><span data-stu-id="e17f2-108">Role definitions that define a set of tasks.</span></span> <span data-ttu-id="e17f2-109">역할 정의의 예로는 **시스템 관리자**, **내용 관리자**, **게시자**등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-109">Examples of role definitions include **System Administrator**, **Content Manager**, and **Publisher**.</span></span>  
  
 <span data-ttu-id="e17f2-110">역할 할당은 폴더 계층에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-110">Role assignments are inherited within the folder hierarchy.</span></span> <span data-ttu-id="e17f2-111">폴더에 대해 정의된 역할 정의는 해당 폴더에 포함된 모든 보고서, 공유 데이터 원본, 리소스 및 하위 폴더로 자동으로 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-111">The role assignment that is defined for a folder is automatically inherited by all reports, shared data sources, resources, and subfolders contained within that folder.</span></span> <span data-ttu-id="e17f2-112">개별 항목에 대해 역할 할당을 정의하면 상속된 보안은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-112">You can override inherited security by defining role assignments for individual items.</span></span> <span data-ttu-id="e17f2-113">폴더 계층의 모든 부분에 대해 하나 이상의 역할 할당으로 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-113">All parts of the folder hierarchy must be secured by at least one role assignment.</span></span> <span data-ttu-id="e17f2-114">보안되지 않은 항목을 만들 수 없으며 보안되지 않은 항목을 생성하도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-114">You cannot create an unsecured item or manipulate settings in a way that produces an unsecured item.</span></span>  
  
 <span data-ttu-id="e17f2-115">다음 다이어그램에서는 B 폴더의 **게시자** 역할에 그룹 및 특정 사용자를 매핑하는 역할 할당을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-115">The following diagram illustrates a role assignment that maps a group and a specific user to the **Publisher** role for Folder B.</span></span>  
  
 <span data-ttu-id="e17f2-116">![역할 할당 다이어그램](../media/report-securityarch.gif "역할 할당 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="e17f2-116">![Role assignments diagram](../media/report-securityarch.gif "Role assignments diagram")</span></span>  
<span data-ttu-id="e17f2-117">역할 할당 다이어그램</span><span class="sxs-lookup"><span data-stu-id="e17f2-117">Role assignments diagram</span></span>  
  
## <a name="system-level-and-item-level-role-assignments"></a><span data-ttu-id="e17f2-118">시스템 수준 및 항목 수준 역할 할당</span><span class="sxs-lookup"><span data-stu-id="e17f2-118">System-Level and Item-Level Role Assignments</span></span>  
 <span data-ttu-id="e17f2-119">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 의 역할 기반 보안은 다음 수준으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-119">Role-based security in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is organized into the following levels:</span></span>  
  
-   <span data-ttu-id="e17f2-120">항목 수준 역할 할당은 보고서 서버 폴더 계층의 보고서, 폴더, 보고서 모델, 공유 데이터 원본 및 리소스에 대한 액세스를 제어하며</span><span class="sxs-lookup"><span data-stu-id="e17f2-120">Item-level role assignments control access to reports, folders, report models, shared data sources, and resources in the report server folder hierarchy.</span></span> <span data-ttu-id="e17f2-121">특정 항목이나 홈 폴더에 대한 역할 할당을 만들 때 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-121">Item-level role assignments are defined when create a role assignment on a specific item or on the Home folder.</span></span>  
  
-   <span data-ttu-id="e17f2-122">시스템 역할 할당은 서버 전체를 범위로 하는 작업 권한을 부여합니다. 예를 들어 작업 관리 기능은 시스템 수준 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-122">System role assignments authorize operations that are scoped to the server as a whole (for example, the ability to manage jobs is a system level operation).</span></span> <span data-ttu-id="e17f2-123">시스템 역할 할당은 시스템 관리자와 동등한 것은 아니며</span><span class="sxs-lookup"><span data-stu-id="e17f2-123">A system role assignment is not the equivalent of a system administrator.</span></span> <span data-ttu-id="e17f2-124">보고서 서버에 대한 모든 권한을 부여하는 고급 사용 권한을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-124">It does not confer advanced permissions that grant full control of a report server.</span></span>  
  
 <span data-ttu-id="e17f2-125">시스템 역할 할당은 폴더 계층의 항목에 대한 액세스 권한을 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-125">A system role assignment does not authorize access to items in the folder hierarchy.</span></span> <span data-ttu-id="e17f2-126">시스템 보안과 항목 보안은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-126">System and item security are mutually exclusive.</span></span> <span data-ttu-id="e17f2-127">지정한 사용자 또는 그룹에 대해 시스템 수준 및 항목 수준 역할 할당을 모두 만들어서 보고서 서버에 대한 충분한 액세스 권한을 제공해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-127">For any given user or group, you might need to create both a system-level and item-level role assignment to provide sufficient access to a report server.</span></span>  
  
## <a name="users-and-groups-in-role-assignments"></a><span data-ttu-id="e17f2-128">역할 할당의 사용자 및 그룹</span><span class="sxs-lookup"><span data-stu-id="e17f2-128">Users and Groups in Role Assignments</span></span>  
 <span data-ttu-id="e17f2-129">역할 할당에 지정된 사용자 계정 또는 그룹 계정은 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-129">The users or group accounts that you specify in role assignments are domain accounts.</span></span> <span data-ttu-id="e17f2-130">보고서 서버는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 도메인 또는 다른 보안 모델(사용자 지정 보안 확장 프로그램을 사용하는 경우)에서 사용자 및 그룹을 만들거나 관리하지 않고 참조하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-130">The report server references, but does not create or manage, users and groups from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows domain (or another security model if you are using a custom security extension).</span></span>  
  
 <span data-ttu-id="e17f2-131">지정된 항목에 적용되는 모든 역할 할당 중에서 두 개의 역할 할당이 동일한 사용자 또는 그룹을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-131">Of all the role assignments that apply to any given item, no two can specify the same user or group.</span></span> <span data-ttu-id="e17f2-132">사용자 계정이 그룹 계정의 멤버이고 두 계정 모두에 대한 역할 할당을 가지고 있는 경우 해당 사용자는 두 역할 할당에 대한 모든 태스크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-132">If a user account is also a member of a group account, and you have role assignments for both, the combined set of tasks for both role assignments are available to the user.</span></span>  
  
 <span data-ttu-id="e17f2-133">이미 역할 할당의 일부인 그룹에 사용자를 추가하는 경우 새 역할 할당이 사용자에게 적용되려면 인터넷 정보 서비스(IIS)를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-133">When you add a user to a group that is already part of a role assignment, you must reset Internet Information Services (IIS) for the new role assignment to take effect for that user.</span></span>  
  
## <a name="predefined-role-assignments"></a><span data-ttu-id="e17f2-134">미리 정의된 역할 할당</span><span class="sxs-lookup"><span data-stu-id="e17f2-134">Predefined Role Assignments</span></span>  
 <span data-ttu-id="e17f2-135">기본적으로 로컬 관리자가 보고서 서버를 관리할 수 있도록 미리 정의된 역할 할당이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-135">By default, predefined role assignments are implemented that allow local administrators to manage the report server.</span></span> <span data-ttu-id="e17f2-136">다른 사용자에게 액세스 권한을 부여하려면 역할 할당을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e17f2-136">You must add additional role assignments to grant access to other users.</span></span>  
  
 <span data-ttu-id="e17f2-137">기본 보안을 제공하는 미리 정의된 역할 할당에 대한 자세한 내용은 [미리 정의된 역할](role-definitions-predefined-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e17f2-137">For more information about the predefined role assignments that provide default security, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17f2-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e17f2-138">See Also</span></span>  
 <span data-ttu-id="e17f2-139">[Management Studio &#40;역할을 만들거나, 삭제 하거나, 수정&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="e17f2-139">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="e17f2-140">[보고서 관리자&#41;&#40;보고서 서버에 대 한 사용자 액세스 권한 부여](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e17f2-140">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="e17f2-141">[역할 할당을 수정 하거나 삭제 &#40;보고서 관리자&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="e17f2-141">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="e17f2-142">[Sharepoint 사이트의 보고서 서버 항목에 대 한 사용 권한은 SharePoint 통합 모드에서 Reporting Services &#40;설정&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="e17f2-142">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="e17f2-143">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="e17f2-143">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
