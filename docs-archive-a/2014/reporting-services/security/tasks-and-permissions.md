---
title: 태스크 및 권한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01cbf00850c5dd57e7ca1575a1a0cb826c009714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739147"
---
# <a name="tasks-and-permissions"></a><span data-ttu-id="36492-102">태스크 및 권한</span><span class="sxs-lookup"><span data-stu-id="36492-102">Tasks and Permissions</span></span>
  <span data-ttu-id="36492-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 *태스크* 는 사용자 또는 관리자가 수행할 수 있는 동작을 말하며</span><span class="sxs-lookup"><span data-stu-id="36492-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], *tasks* are actions that a user or administrator can perform.</span></span> <span data-ttu-id="36492-104">태스크는 미리 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-104">Tasks are predefined.</span></span> <span data-ttu-id="36492-105">태스크는 사용자 지정할 수 없으며 프로그래밍 방식이나 도구를 통해 제공된 태스크를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-105">You cannot create custom tasks or modify the ones provided either programmatically or through a tool.</span></span> <span data-ttu-id="36492-106">모두 25가지의 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-106">There are twenty-five tasks in all.</span></span> <span data-ttu-id="36492-107">이러한 태스크는 역할 기반 보안에서 사용할 수 있는 전체 작업 집합을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="36492-107">These tasks comprise the entire set of operations that are available in role-based security.</span></span> <span data-ttu-id="36492-108">"보고서 보기", "보고서 관리", "보고서 서버 속성 관리" 등과 같은 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-108">Some examples of tasks include "View reports," "Manage reports," and "Manage report server properties."</span></span>  
  
 <span data-ttu-id="36492-109">각 태스크는 미리 정의되는 권한 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-109">Each task consists of a set of permissions, which are also predefined.</span></span> <span data-ttu-id="36492-110">예를 들어 "폴더 관리" 태스크는 폴더 만들기 및 삭제 권한과 폴더 속성 보기 및 업데이트 권한을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="36492-110">For example, the "Manage folders" task contains permissions to create and delete folders and view and update folder properties.</span></span> <span data-ttu-id="36492-111">각 태스크에 대한 사용 권한은 문서화되어 각 작업에 대해 보다 정확한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36492-111">Permissions for each task are documented to provide a more exact description of each task.</span></span> <span data-ttu-id="36492-112">사용 권한과 직접 상호 작용하거나 역할 할당에 사용 권한을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-112">It is not possible to interact with permissions directly or to specify them in role assignments.</span></span> <span data-ttu-id="36492-113">사용 권한은 역할 정의에 포함된 태스크를 통해 사용자에게 간접적으로 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-113">Users are granted permissions indirectly through the tasks that are included in role definitions.</span></span>  
  
 <span data-ttu-id="36492-114">태스크는 역할의 일부이고 해당 역할이 역할 할당에 포함되어 있는 경우에만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-114">Tasks can be performed only if they are part of a role and that role is included in a role assignment.</span></span> <span data-ttu-id="36492-115">따라서 모델 보기 태스크가 역할에 포함되어 있지 않거나 해당 역할이 역할 할당에 포함되어 있지 않은 경우 사용자는 보고서 모델을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-115">Thus, if the View Models task is not included in a role, or that role is not included in a role assignment, users cannot view report models.</span></span> <span data-ttu-id="36492-116">다음 다이어그램에서는 사용 권한이 태스크에 결합되는 방법과 특정 역할 할당에 사용할 수 있는 역할에 태스크가 결합되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36492-116">The following diagram shows how permissions are combined into tasks, and how tasks are combined into roles that can be used for specific role assignments.</span></span>  
  
 <span data-ttu-id="36492-117">![사용 권한 및 태스크 다이어그램](../media/report-securityobjects.gif "사용 권한 및 태스크 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="36492-117">![Permissions and task diagram](../media/report-securityobjects.gif "Permissions and task diagram")</span></span>  
<span data-ttu-id="36492-118">사용 권한 및 태스크 다이어그램</span><span class="sxs-lookup"><span data-stu-id="36492-118">Permissions and task diagram</span></span>  
  
## <a name="system-and-item-level-tasks"></a><span data-ttu-id="36492-119">시스템 및 항목 수준 태스크</span><span class="sxs-lookup"><span data-stu-id="36492-119">System and Item Level Tasks</span></span>  
 <span data-ttu-id="36492-120">태스크는 시스템 수준 아니면 항목 수준 범주에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="36492-120">Tasks fall into two categories: system level and item level.</span></span> <span data-ttu-id="36492-121">역할은 단일 범주의 태스크만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36492-121">A role can include tasks only from a single category.</span></span> <span data-ttu-id="36492-122">다음 표에서는 각 태스크 범주를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36492-122">The following table describes each category of tasks.</span></span>  
  
|<span data-ttu-id="36492-123">Category</span><span class="sxs-lookup"><span data-stu-id="36492-123">Category</span></span>|<span data-ttu-id="36492-124">Description</span><span class="sxs-lookup"><span data-stu-id="36492-124">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="36492-125">항목 수준의 태스크</span><span class="sxs-lookup"><span data-stu-id="36492-125">Item-Level Tasks</span></span>](tasks-and-permissions-item-level-tasks.md)|<span data-ttu-id="36492-126">폴더, 보고서, 보고서 모델, 리소스 등 보고서 서버에서 관리되는 항목에 대해 수행하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="36492-126">Actions that are performed on items managed by a report server, such as folders, reports, report models, and resources.</span></span><br /><br /> <span data-ttu-id="36492-127">항목 수준 태스크의 범위는 보고서 서버 폴더 네임스페이스로 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-127">Item-level tasks are scoped to the report server folder namespace.</span></span> <span data-ttu-id="36492-128">보고서 서버의 폴더 또는 URL 액세스를 통해 액세스하는 모든 항목의 보안은 항목 수준 태스크를 포함하는 역할 할당에 의해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-128">All items that you access through the folders on a report server or through URL access are secured by role assignments that include item-level tasks.</span></span>|  
|[<span data-ttu-id="36492-129">시스템 수준 태스크</span><span class="sxs-lookup"><span data-stu-id="36492-129">System-Level Tasks</span></span>](tasks-and-permissions-system-level-tasks.md)|<span data-ttu-id="36492-130">많은 항목에 사용할 수 있는 작업 또는 공유 일정 관리와 같이 시스템 수준에서 수행하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="36492-130">Actions that are performed at the system level, such as managing jobs or shared schedules that can be used with many items.</span></span> <span data-ttu-id="36492-131">시스템 수준 태스크의 범위는 보고서 서버 폴더 네임스페이스 외부로 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="36492-131">System-level tasks are scoped outside of the report server folder namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36492-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36492-132">See Also</span></span>  
 <span data-ttu-id="36492-133">[역할 정의](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="36492-133">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="36492-134">[미리 정의된 역할](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="36492-134">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="36492-135">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="36492-135">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
