---
title: 시스템 역할 속성(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b37ebb1cb95d6628884d81156c9c1bc29bff86fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648255"
---
# <a name="system-role-properties-management-studio"></a><span data-ttu-id="56f82-102">시스템 역할 속성(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="56f82-102">System Role Properties (Management Studio)</span></span>
  <span data-ttu-id="56f82-103">시스템 역할 페이지를 사용하여 보고서 서버에 현재 정의되어 있는 시스템 역할 정의를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-103">Use the System Roles page to view the system role definitions that are currently defined for the report server.</span></span> <span data-ttu-id="56f82-104">시스템 역할 정의에는 개별 항목이 아닌 전체 사이트에 대해 수행되는 태스크의 명명된 모음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-104">A system role definition contains a named collection of tasks that are performed relative to the entire site, instead of an individual item.</span></span> <span data-ttu-id="56f82-105">역할 정의는 사용자나 그룹에 할당되어 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-105">Role definitions are assigned to a user or groups to create a resulting role assignment.</span></span> <span data-ttu-id="56f82-106">역할 정의의 태스크는 사용자나 그룹이 수행할 수 있는 태스크를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-106">The tasks in the role definition specify what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="56f82-107">에는 **시스템 관리자** 및 **시스템 사용자**로 두 개의 미리 정의된 시스템 역할 정의가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-107">has two predefined system role definitions: **System Administrator** and **System User**.</span></span> <span data-ttu-id="56f82-108">태스크 목록을 변경하여 이러한 역할 정의를 수정하거나 다른 태스크 조합을 지원하는 새 시스템 역할을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-108">You can modify these role definitions by changing the task list, or you can create a new system role that supports a different combination of tasks.</span></span> <span data-ttu-id="56f82-109">역할 정의를 편집하면 역할 정의를 포함하는 모든 역할 할당에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-109">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56f82-110">시스템 역할 할당은 기본 모드로 실행되는 보고서 서버에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-110">System role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="56f82-111">보고서 서버가 SharePoint 통합 모드로 구성된 경우 이 페이지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-111">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56f82-112">옵션</span><span class="sxs-lookup"><span data-stu-id="56f82-112">Options</span></span>  
 <span data-ttu-id="56f82-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="56f82-113">**Name**</span></span>  
 <span data-ttu-id="56f82-114">시스템 역할 정의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-114">Specifies the name of the system role definition.</span></span>  
  
 <span data-ttu-id="56f82-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="56f82-115">**Description**</span></span>  
 <span data-ttu-id="56f82-116">시스템 역할 정의에 대한 설명을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-116">Shows a description of the system role definition.</span></span> <span data-ttu-id="56f82-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 해당 설명은 이 페이지에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="56f82-118">보고서 관리자를 통해 이 항목을 보는 사용자는 폴더 계층을 검색할 때 이 설명을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-118">Users who view this item through Report Manager may see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="56f82-119">**Task**</span><span class="sxs-lookup"><span data-stu-id="56f82-119">**Task**</span></span>  
 <span data-ttu-id="56f82-120">이 역할 정의에 대해 선택할 수 있는 시스템 수준 태스크를 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-120">Lists all system-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="56f82-121">미리 정의된 태스크 목록에서 항목을 추가 또는 제거하여 사용자가 이 역할을 통해 지정된 항목에 액세스하는 방법을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-121">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="56f82-122">새 태스크를 만들거나 기존 작업을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-122">You cannot create new tasks, and you cannot modify existing tasks.</span></span>  
  
 <span data-ttu-id="56f82-123">**설명**</span><span class="sxs-lookup"><span data-stu-id="56f82-123">**Description**</span></span>  
 <span data-ttu-id="56f82-124">각 태스크에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-124">Provides information about each task.</span></span> <span data-ttu-id="56f82-125">태스크 설명은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56f82-125">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f82-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56f82-126">See Also</span></span>  
 <span data-ttu-id="56f82-127">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="56f82-127">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="56f82-128">[시스템 수준 태스크](../security/tasks-and-permissions-system-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="56f82-128">[System-Level Tasks](../security/tasks-and-permissions-system-level-tasks.md) </span></span>  
 <span data-ttu-id="56f82-129">[태스크 및 권한](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="56f82-129">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="56f82-130">미리 정의된 역할</span><span class="sxs-lookup"><span data-stu-id="56f82-130">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
