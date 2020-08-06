---
title: 시스템 수준 작업 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98f9390664064cd293b80d094d65c903869bc709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739159"
---
# <a name="system-level-tasks"></a><span data-ttu-id="4fb48-102">시스템 수준 태스크</span><span class="sxs-lookup"><span data-stu-id="4fb48-102">System-Level Tasks</span></span>
  <span data-ttu-id="4fb48-103">시스템 수준 태스크는 보고서 서버 사이트 전체에 적용되는 작업과 관련된 권한의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb48-103">A system-level task is a collection of permissions that relate to operations that apply to the report server site as a whole.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4fb48-104">에는 특정 항목에 적용되는 항목 수준의 태스크도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fb48-104">also includes item-level tasks that apply to specific items.</span></span> <span data-ttu-id="4fb48-105">자세한 내용은 [항목 수준의 태스크](tasks-and-permissions-item-level-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fb48-105">For more information, see [Item-Level Tasks](tasks-and-permissions-item-level-tasks.md).</span></span> <span data-ttu-id="4fb48-106">일반적인 태스크 및 사용 권한에 대한 자세한 내용은 [Tasks and Permissions](tasks-and-permissions.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fb48-106">For more information about tasks and permissions in general, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fb48-107">이러한 작업을 프로그래밍 방식으로 수행하는 경우 시스템 수준 태스크를 지원하는 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fb48-107">If you are working with these tasks programmatically, you must use methods that support system-level tasks.</span></span> <span data-ttu-id="4fb48-108">자세한 내용은 <xref:ReportService2010.ReportingService2010.ListTasks%2A> 및 <xref:ReportService2010.ReportingService2010.ListRoles%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fb48-108">For more information, see <xref:ReportService2010.ReportingService2010.ListTasks%2A> and <xref:ReportService2010.ReportingService2010.ListRoles%2A>.</span></span>  
  
## <a name="permissions-in-system-level-tasks"></a><span data-ttu-id="4fb48-109">시스템 수준 태스크 사용 권한</span><span class="sxs-lookup"><span data-stu-id="4fb48-109">Permissions in System-Level Tasks</span></span>  
 <span data-ttu-id="4fb48-110">다음 표에서는 각 시스템 태스크에 대한 사용 권한을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fb48-110">The following table identifies the collection of permissions for each system task.</span></span> <span data-ttu-id="4fb48-111">나열된 사용 권한은 각 태스크에서 사용 가능한 기능을 보다 정확하게 설명하기 위한 참고용입니다.</span><span class="sxs-lookup"><span data-stu-id="4fb48-111">Permissions are listed for informational purposes only, to provide a more exact description of the functionality available through each task.</span></span>  
  
|<span data-ttu-id="4fb48-112">Task</span><span class="sxs-lookup"><span data-stu-id="4fb48-112">Task</span></span>|<span data-ttu-id="4fb48-113">사용 권한</span><span class="sxs-lookup"><span data-stu-id="4fb48-113">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4fb48-114">보고서 정의 실행</span><span class="sxs-lookup"><span data-stu-id="4fb48-114">Execute report definitions</span></span>|<span data-ttu-id="4fb48-115">보고서 정의 실행(사용 권한과 태스크 이름이 같음)</span><span class="sxs-lookup"><span data-stu-id="4fb48-115">Execute Report Definitions (the permission and task name are the same)</span></span>|  
|<span data-ttu-id="4fb48-116">이벤트 생성</span><span class="sxs-lookup"><span data-stu-id="4fb48-116">Generate events</span></span>|<span data-ttu-id="4fb48-117">이벤트 생성</span><span class="sxs-lookup"><span data-stu-id="4fb48-117">Generate Events</span></span>|  
|<span data-ttu-id="4fb48-118">작업 관리</span><span class="sxs-lookup"><span data-stu-id="4fb48-118">Manage jobs</span></span>|<span data-ttu-id="4fb48-119">시스템 속성 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-119">Read System Properties</span></span><br /><br /> <span data-ttu-id="4fb48-120">시스템 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="4fb48-120">Update System Properties</span></span>|  
|<span data-ttu-id="4fb48-121">보고서 서버 속성 관리</span><span class="sxs-lookup"><span data-stu-id="4fb48-121">Manage report server properties</span></span>|<span data-ttu-id="4fb48-122">시스템 속성 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-122">Read System Properties</span></span><br /><br /> <span data-ttu-id="4fb48-123">시스템 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="4fb48-123">Update System Properties</span></span>|  
|<span data-ttu-id="4fb48-124">역할 관리</span><span class="sxs-lookup"><span data-stu-id="4fb48-124">Manage roles</span></span>|<span data-ttu-id="4fb48-125">역할 만들기</span><span class="sxs-lookup"><span data-stu-id="4fb48-125">Create Roles</span></span><br /><br /> <span data-ttu-id="4fb48-126">역할 삭제</span><span class="sxs-lookup"><span data-stu-id="4fb48-126">Delete Roles</span></span><br /><br /> <span data-ttu-id="4fb48-127">역할 속성 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-127">Read Role Properties</span></span><br /><br /> <span data-ttu-id="4fb48-128">역할 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="4fb48-128">Update Role Properties</span></span>|  
|<span data-ttu-id="4fb48-129">공유 일정 관리</span><span class="sxs-lookup"><span data-stu-id="4fb48-129">Manage shared schedules</span></span>|<span data-ttu-id="4fb48-130">일정 만들기</span><span class="sxs-lookup"><span data-stu-id="4fb48-130">Create Schedules</span></span>|  
|<span data-ttu-id="4fb48-131">보고서 서버 보안 관리</span><span class="sxs-lookup"><span data-stu-id="4fb48-131">Manage report server security</span></span>|<span data-ttu-id="4fb48-132">시스템 보안 정책 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-132">Read System Security Policies</span></span><br /><br /> <span data-ttu-id="4fb48-133">시스템 보안 정책 업데이트</span><span class="sxs-lookup"><span data-stu-id="4fb48-133">Update System Security Policies</span></span>|  
|<span data-ttu-id="4fb48-134">보고서 서버 속성 보기</span><span class="sxs-lookup"><span data-stu-id="4fb48-134">View report server properties</span></span>|<span data-ttu-id="4fb48-135">시스템 속성 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-135">Read System Properties</span></span>|  
|<span data-ttu-id="4fb48-136">공유 일정 보기</span><span class="sxs-lookup"><span data-stu-id="4fb48-136">View shared schedules</span></span>|<span data-ttu-id="4fb48-137">일정 읽기</span><span class="sxs-lookup"><span data-stu-id="4fb48-137">Read Schedules</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fb48-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fb48-138">See Also</span></span>  
 [<span data-ttu-id="4fb48-139">기본 모드 보고서 서버에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="4fb48-139">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
