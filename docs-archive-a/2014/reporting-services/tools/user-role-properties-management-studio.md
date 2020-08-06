---
title: 사용자 역할 속성(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f79953abdf5e3d1cdb03de8c5feeb6b2de34ab7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732316"
---
# <a name="user-role-properties-management-studio"></a><span data-ttu-id="65bfa-102">사용자 역할 속성(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="65bfa-102">User Role Properties (Management Studio)</span></span>
  <span data-ttu-id="65bfa-103">이 페이지를 사용하여 항목 수준의 역할 정의에 포함된 태스크를 볼 수 있으며</span><span class="sxs-lookup"><span data-stu-id="65bfa-103">Use this page to view which tasks are included in an item-level role definition.</span></span> <span data-ttu-id="65bfa-104">태스크 목록을 변경하거나 역할 설명을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-104">You can also use this page to change the task list or modify a role description.</span></span>  
  
 <span data-ttu-id="65bfa-105">항목 수준 역할 정의는 특정 항목(폴더, 보고서, 리소스 또는 공유 데이터 원본)에 대해 사용자가 수행하는 태스크의 명명된 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-105">An item-level role definition is a named collection of tasks that users perform relative to a specific item (that is, a folder, report, resource, or shared data source).</span></span> <span data-ttu-id="65bfa-106">역할 정의는 보고서 관리자에서 역할 할당을 만들기 위해 사용자 또는 그룹에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-106">Role definitions are assigned to a user or group to create a role assignment in Report Manager.</span></span> <span data-ttu-id="65bfa-107">역할 정의의 태스크는 사용자나 그룹이 수행할 수 있는 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-107">The tasks in the role definition describe what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="65bfa-108">에는 사용 가능한 미리 정의된 항목 수준의 역할 정의가 다수 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-108">includes a number of predefined item-level role definitions that you can work with.</span></span> <span data-ttu-id="65bfa-109">각 정의의 태스크 목록을 변경하여 역할 정의를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-109">You can modify the role definitions by changing the task list of each one.</span></span> <span data-ttu-id="65bfa-110">역할 정의를 편집하면 역할 정의를 포함하는 모든 역할 할당에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-110">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65bfa-111">사용자 역할 할당은 기본 모드로 실행되는 보고서 서버에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-111">User role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="65bfa-112">보고서 서버가 SharePoint 통합용으로 구성된 경우 이 페이지에는 SharePoint 사이트에 정의된 역할 및 사용 권한 수준에 대한 읽기 전용 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-112">If the report server is configured for SharePoint integration, this page displays read-only information about the roles and permission levels that are defined on the SharePoint site.</span></span>  
  
## <a name="options"></a><span data-ttu-id="65bfa-113">옵션</span><span class="sxs-lookup"><span data-stu-id="65bfa-113">Options</span></span>  
 <span data-ttu-id="65bfa-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="65bfa-114">**Name**</span></span>  
 <span data-ttu-id="65bfa-115">역할 정의의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-115">Specifies the name of the role definition.</span></span>  
  
 <span data-ttu-id="65bfa-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="65bfa-116">**Description**</span></span>  
 <span data-ttu-id="65bfa-117">역할 정의에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-117">Shows a description of the role definition.</span></span> <span data-ttu-id="65bfa-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 설명은 이 페이지에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="65bfa-119">보고서 관리자에서 이 설명은 사용자가 역할 할당에 역할을 사용할지 여부를 지정하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-119">In Report Manager, this description helps users decide whether to use the role in a role assignment.</span></span>  
  
 <span data-ttu-id="65bfa-120">**Task**</span><span class="sxs-lookup"><span data-stu-id="65bfa-120">**Task**</span></span>  
 <span data-ttu-id="65bfa-121">이 역할 정의에 대해 선택할 수 있는 모든 항목 수준의 태스크를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-121">Lists all item-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="65bfa-122">미리 정의된 태스크 목록에서 항목을 추가 또는 제거하여 사용자가 이 역할을 통해 지정된 항목에 액세스하는 방법을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-122">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="65bfa-123">새 태스크를 만들거나 기존 작업을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-123">You cannot create new tasks, and you cannot modify existing tasks.</span></span> <span data-ttu-id="65bfa-124">역할 정의의 태스크 목록은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-124">The task list of a role definition appears only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="65bfa-125">**태스크 설명**</span><span class="sxs-lookup"><span data-stu-id="65bfa-125">**Task Description**</span></span>  
 <span data-ttu-id="65bfa-126">각 태스크에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-126">Provides information about each task.</span></span> <span data-ttu-id="65bfa-127">태스크 설명은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65bfa-127">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65bfa-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65bfa-128">See Also</span></span>  
 <span data-ttu-id="65bfa-129">[항목 수준의 태스크](../security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="65bfa-129">[Item-Level Tasks](../security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="65bfa-130">[역할 정의](../security/role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="65bfa-130">[Role Definitions](../security/role-definitions.md) </span></span>  
 <span data-ttu-id="65bfa-131">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="65bfa-131">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="65bfa-132">[태스크 및 권한](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="65bfa-132">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="65bfa-133">미리 정의된 역할</span><span class="sxs-lookup"><span data-stu-id="65bfa-133">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
