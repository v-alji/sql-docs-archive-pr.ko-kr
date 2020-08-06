---
title: 일정 만들기, 수정 및 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ec235126caee5acd0d5c79958528565d917bf522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653725"
---
# <a name="create-modify-and-delete-schedules"></a><span data-ttu-id="77151-102">일정 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="77151-102">Create, Modify, and Delete Schedules</span></span>
  <span data-ttu-id="77151-103">이 항목에서는 일정을 만들고 수정하고 삭제하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-103">Use this topic to learn about how to create, modify, and delete schedules.</span></span>  
  
 <span data-ttu-id="77151-104">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="77151-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="77151-105">공유 일정 관리 개요</span><span class="sxs-lookup"><span data-stu-id="77151-105">Overview of Managing Shared Schedules</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="77151-106">공유 일정 만들기 및 관리 (SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="77151-106">Create and Manage Shared Schedules (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="77151-107">공유 일정 만들기 및 관리(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="77151-107">Create and Manage Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
##  <a name="overview-of-managing-shared-schedules"></a><a name="bkmk_overview"></a><span data-ttu-id="77151-108">공유 일정 관리 개요</span><span class="sxs-lookup"><span data-stu-id="77151-108">Overview of Managing Shared Schedules</span></span>  
 <span data-ttu-id="77151-109">기본 모드에 대한 공유 일정을 관리하려면 보고서 관리자의 일정 페이지나 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 공유 일정 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-109">To manage shared schedules for native mode, use the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="77151-110">SharePoint 모드의 경우에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 위한 관리 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-110">For SharePoint mode use, the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="77151-111">보고서 서버에 대해 정의된 모든 공유 일정을 보고, 일정을 일시 중지 및 재개하고(보고서 관리자에만 해당), 수정 또는 삭제할 일정을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-111">You can view all the shared schedules that are defined for the report server, pause and resume schedules (on Report Manager only), and select schedules to modify or delete.</span></span> <span data-ttu-id="77151-112">공유 일정 페이지에는 각 일정에 대한 정보, 즉 빈도, 소유자, 만료 날짜 및 상태 정보가 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-112">The Shared Schedules page summarizes the following information about the state of each schedule: frequency, owner, expiration date, and status.</span></span>  
  
 <span data-ttu-id="77151-113">다음 작업을 통해 공유 일정이 현재 사용 중인지 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-113">You can tell whether a shared schedule is actively used by:</span></span>  
  
-   <span data-ttu-id="77151-114">공유 일정 페이지에서 마지막 실행 날짜, 다음 실행 날짜 및 상태 필드의 값을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-114">Inspecting the values in the Last Run date, Next Run date, and Status fields on the Shared Schedules page.</span></span> <span data-ttu-id="77151-115">일정이 만료되어 더 이상 실행되지 않으면 상태 필드에 만료 날짜가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="77151-115">If a schedule no longer runs because it has expired, the expiration date appears in the Status field.</span></span>  
  
-   <span data-ttu-id="77151-116">지정한 공유 일정의 보고서 페이지를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-116">Viewing the Reports page of a given Shared Schedule.</span></span> <span data-ttu-id="77151-117">이 페이지에는 공유 일정을 사용하는 모든 보고서 및 공유 데이터 세트의 목록이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-117">This page lists all reports and shared datasets that use the shared schedule.</span></span>  
  
-   <span data-ttu-id="77151-118">보고서 실행 로그 파일 또는 추적 로그에서 보고서가 일정에 지정된 시간에 실행되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-118">Viewing the report execution log files or trace logs to determine whether reports have been run at the times specified by the schedule.</span></span> <span data-ttu-id="77151-119">자세한 내용은 [Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77151-119">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
##  <a name="create-and-manage-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a><span data-ttu-id="77151-120">공유 일정 만들기 및 관리 (SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="77151-120">Create and Manage Shared Schedules (SharePoint Mode)</span></span>  
 <span data-ttu-id="77151-121">공유 일정은 원하는 수의 보고서나 구독에 즉시 사용 가능한 일정 정보를 제공하는 다목적 일정입니다.</span><span class="sxs-lookup"><span data-stu-id="77151-121">A shared schedule is a multipurpose schedule that provides ready-to-use schedule information to any number of reports or subscriptions.</span></span> <span data-ttu-id="77151-122">한 번 공유 일정을 만들어 놓으면 일정 정보가 필요할 때 구독 또는 속성 페이지에서 해당 일정을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-122">You create a shared schedule once, and then reference it in a subscription or property page when you need schedule information.</span></span> <span data-ttu-id="77151-123">공유 일정은 중앙에서 관리하고, 일시 중지하고, 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-123">Shared schedules can be centrally managed, paused, and resumed.</span></span> <span data-ttu-id="77151-124">이와 달리 보고서나 구독이 실행되지 않도록 하려면 수동으로 사용자 지정 일정을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-124">In contrast, you must edit a custom schedule manually to prevent a report or subscription from running.</span></span>  
  
 <span data-ttu-id="77151-125">SharePoint 사이트에서 공유 일정을 만들거나, 수정하거나, 삭제하려면 사이트 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-125">You must be a site administrator to create, modify, or delete shared schedules on a SharePoint site.</span></span>  
  
 <span data-ttu-id="77151-126">설명이 포함된 이름으로 특정 일정을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-126">You can identify a specific schedule by its descriptive name.</span></span> <span data-ttu-id="77151-127">이름이 지정되어 있지 않으면 되풀이 패턴이나 실행 날짜 및 시간과 같은 일정 정보를 기반으로 기본 이름이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-127">If a name is not specified, a default name is created based on facts about the schedule, such as its recurrence pattern or dates and times when it runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77151-128">공유 일정을 만들려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-128">Creating shared schedules requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
### <a name="create-shared-schedules-sharepoint"></a><span data-ttu-id="77151-129">공유 일정 만들기(SharePoint)</span><span class="sxs-lookup"><span data-stu-id="77151-129">Create Shared Schedules (SharePoint)</span></span>  
  
##### <a name="to-create-shared-schedules"></a><span data-ttu-id="77151-130">공유 일정을 만들려면</span><span class="sxs-lookup"><span data-stu-id="77151-130">To create shared schedules</span></span>  
  
1.  <span data-ttu-id="77151-131">**사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-131">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="77151-132">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-132">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="77151-133">Reporting Services 섹션에서 **공유 일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-133">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="77151-134">**일정 추가** 를 클릭하여 일정 속성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="77151-134">Click **Add Schedule** to open the Schedule Properties page.</span></span>  
  
5.  <span data-ttu-id="77151-135">일정에 대한 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-135">Enter a descriptive name for the schedule.</span></span> <span data-ttu-id="77151-136">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 작업에 사용되는 애플리케이션 페이지에서 이 이름은 사이트 전반에서 일정 정의 페이지의 드롭다운 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="77151-136">On the application pages used to work with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports, this name will appear in drop-down lists in schedule definition pages throughout the site.</span></span> <span data-ttu-id="77151-137">읽기 어려운 긴 이름은 사용하지 말고</span><span class="sxs-lookup"><span data-stu-id="77151-137">Avoid long names that are hard to read.</span></span> <span data-ttu-id="77151-138">이름 시작 부분에 가장 중요한 정보를 포함하는 명명 규칙을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="77151-138">Do follow a naming convention that puts the most description information at the beginning of the name.</span></span>  
  
6.  <span data-ttu-id="77151-139">빈도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-139">Choose a frequency.</span></span> <span data-ttu-id="77151-140">선택하는 빈도에 따라 해당 빈도를 지원하기 위해 페이지에 나타나는 일정 옵션이 변경될 수 있습니다. 예를 들어 **월**을 선택하면 각 월의 이름이 페이지에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="77151-140">Depending on the frequency you choose, the schedule options that appear on the page might change to support that frequency (for example, if you choose **Month**, the name of each month will appear on the page).</span></span>  
  
7.  <span data-ttu-id="77151-141">일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-141">Define the schedule.</span></span> <span data-ttu-id="77151-142">일부 일정 조합은 단일 일정으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-142">Not all schedule combinations can be supported in a single schedule.</span></span>  
  
8.  <span data-ttu-id="77151-143">시작 날짜와 종료 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-143">Set a start and end date.</span></span>  
  
9. <span data-ttu-id="77151-144">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-144">Click **OK**.</span></span>  
  
### <a name="delete-shared-schedules-sharepoint"></a><span data-ttu-id="77151-145">공유 일정 삭제(SharePoint)</span><span class="sxs-lookup"><span data-stu-id="77151-145">Delete Shared Schedules (SharePoint)</span></span>  
 <span data-ttu-id="77151-146">공유 일정이나 보고서별 일정 모두 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-146">All schedules, whether shared or report specific, must be deleted manually.</span></span> <span data-ttu-id="77151-147">사용 중인 공유 일정을 삭제하면 해당 일정에 대한 모든 참조가 지정되지 않은 사용자 지정 일정, 즉 날짜 또는 시간 정보가 없는 사용자 지정 일정으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="77151-147">If you delete a shared schedule that is in use, all references to it are replaced with unspecified custom schedules (that is, a custom schedule that does not have date or time information).</span></span>  
  
 <span data-ttu-id="77151-148">일정을 삭제하는 것과 만료시키는 것은 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-148">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="77151-149">만료 날짜를 사용하여 일정을 중지할 수 있지만 일정이 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-149">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="77151-150">일정은 보고서 서버 작업을 자동화하는 데 사용되기 때문에 자동으로 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-150">Because schedules are used to automate report server operations, they are never deleted automatically.</span></span> <span data-ttu-id="77151-151">만료된 일정은 보고서 서버 관리자에게 자동화된 처리가 갑자기 중지된 이유에 대한 근거를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-151">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="77151-152">만료된 일정이 없으면 보고서 서버 관리자가 문제를 잘못 진단하거나 제대로 작동하는 프로세스의 문제를 해결하기 위해 시간을 낭비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-152">Without the presence of the expired schedule, a report server administrator might misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="77151-153">만료된 사용자 지정 일정은 보고서에 연결된 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-153">A custom schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="77151-154">종료 날짜를 확인하면 일정이 만료되었는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-154">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="77151-155">만료된 공유 일정은 공유 일정 목록에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-155">An expired shared schedule remains in the Shared Schedules list.</span></span> <span data-ttu-id="77151-156">상태 필드는 일정이 만료되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-156">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="77151-157">종료 날짜를 연장하여 일정을 복원할 수 있으며 더 이상 필요 없는 경우 일정 참조를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-157">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
##### <a name="to-delete-a-shared-schedule"></a><span data-ttu-id="77151-158">공유 일정을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="77151-158">To delete a shared schedule</span></span>  
  
1.  <span data-ttu-id="77151-159">**사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-159">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="77151-160">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-160">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="77151-161">Reporting Services 섹션에서 **공유 일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-161">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="77151-162">일정을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-162">Select the schedule, and click **Delete**.</span></span>  
  
##  <a name="create-and-manage-shared-schedules-native-mode"></a><a name="bkmk_native"></a><span data-ttu-id="77151-163">공유 일정 만들기 및 관리 (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="77151-163">Create and Manage Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="77151-164">공유 일정은 보고서 관리자의 일정 페이지나 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 공유 일정 폴더를 사용하여 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-164">Shared schedules must be deleted manually using the Schedules page in Report Manager or the Shared Schedules folder in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="77151-165">사용 중인 공유 일정을 삭제하면 공유 일정에 대한 모든 참조가 보고서별 일정으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="77151-165">If you delete a shared schedule that is in use, all references to it are replaced with report-specific schedules.</span></span>  
  
 <span data-ttu-id="77151-166">보고서 일정과 구독별 일정은 보고서 또는 구독을 삭제하거나 다른 방법을 선택하여 보고서 또는 구독을 실행하는 경우 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-166">Report and subscription-specific schedules are deleted when you delete the report or subscription, or when you choose a different approach to run the report or subscription.</span></span> <span data-ttu-id="77151-167">예를 들어 **항상 최신 데이터로 이 보고서 실행** 을 선택하면 만든 보고서별 일정이 삭제되고 보고서가 보고서 실행 스냅샷으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-167">For example, choosing **Always run this report with the most recent data** will delete a report-specific schedule that you created to run a report as a report execution snapshot.</span></span>  
  
 <span data-ttu-id="77151-168">일정을 삭제하는 것과 만료시키는 것은 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-168">Deleting a schedule and causing it to expire are different.</span></span> <span data-ttu-id="77151-169">만료 날짜를 사용하여 일정을 중지할 수 있지만 일정이 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-169">An expiration date is used to stop a schedule but does not delete it.</span></span> <span data-ttu-id="77151-170">일정은 여러 가지 기능을 자동화하는 데 사용되기 때문에 자동으로 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-170">Because schedules are used to automate so many features, they are never deleted automatically.</span></span> <span data-ttu-id="77151-171">만료된 일정은 보고서 서버 관리자에게 자동화된 처리가 갑자기 중지된 이유에 대한 근거를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-171">Expired schedules provide evidence to report server administrators as to why an automated process has suddenly stopped.</span></span> <span data-ttu-id="77151-172">만료된 일정이 없으면 보고서 서버 관리자가 문제를 잘못 진단하거나 기능적인 과정 전체의 문제 해결을 위해 불필요한 시간을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-172">Without the presence of the expired schedule, a report server administrator can misdiagnose the problem or spend unnecessary time trying to troubleshoot a fully functional process.</span></span>  
  
 <span data-ttu-id="77151-173">만료된 보고서별 일정은 보고서에 연결된 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-173">A report-specific schedule that has expired remains attached to the report.</span></span> <span data-ttu-id="77151-174">종료 날짜를 확인하면 일정이 만료되었는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-174">You can determine if a schedule has expired by checking its end date.</span></span> <span data-ttu-id="77151-175">만료된 공유 일정은 공유 일정 목록에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-175">An expired shared schedules remains in the Shared Schedules list.</span></span> <span data-ttu-id="77151-176">상태 필드는 일정이 만료되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="77151-176">The Status field indicates whether the schedule has expired.</span></span> <span data-ttu-id="77151-177">종료 날짜를 연장하여 일정을 복원할 수 있으며 더 이상 필요 없는 경우 일정 참조를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-177">You can reinstate the schedule by extending the end date, or you can remove the schedule reference if you no longer need it.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="77151-178">공유 일정 만들기, 삭제 또는 수정(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="77151-178">Create, Delete, or Modify a Shared Schedule (Report Manager)</span></span>  
 <span data-ttu-id="77151-179">일정을 만들고 수정할 때는 일정 실행 시기를 결정하는 빈도 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-179">Creating and modifying a schedule consists of setting frequency options that determine when the schedule runs.</span></span>  
  
-   <span data-ttu-id="77151-180">공유 일정은 별도의 항목으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-180">Shared schedules are created as separate items.</span></span> <span data-ttu-id="77151-181">구독이나 예약된 다른 작업을 정의할 때 이렇게 생성된 공유 일정을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-181">After they are created, you reference them when defining a subscription or some other scheduled operation.</span></span>  
  
-   <span data-ttu-id="77151-182">보고서별 일정은 구독을 정의하거나 보고서 실행 속성을 설정할 때 생성됩니다. 일정 정보를 작성하는 것은 구독 정의 또는 속성 설정의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="77151-182">Report-specific schedules are created when you define a subscription or set report execution properties; filling out schedule information is part of defining a subscription or setting properties.</span></span> <span data-ttu-id="77151-183">보고서별 일정을 정의하려면 일정을 사용하는 보고서나 구독을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="77151-183">To define a report-specific schedule, you open the report or subscription that uses it.</span></span>  
  
 <span data-ttu-id="77151-184">공유 일정에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에서 실행되는 게시된 여러 보고서 및 구독에 사용할 수 있는 일정 및 되풀이 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-184">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="77151-185">동시에 실행되는 보고서와 구독이 여러 개 있을 경우 이러한 작업에 대한 공유 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-185">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="77151-186">이후에 되풀이 패턴 또는 종료 날짜를 변경하려는 경우 단일 위치에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-186">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="77151-187">공유 일정은 관리하기가 더 쉬우므로 예약된 작업을 보다 유연하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-187">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="77151-188">예를 들어 공유 일정을 일시 중지하고 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-188">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="77151-189">또한 예약된 작업이 동시에 너무 많이 실행되는 경우에는 서로 다른 시간에 실행되는 공유 일정을 여러 개 만든 다음 처리 부하가 보고서 서버에서 균등하게 분포될 때까지 일정 정보를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-189">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
 <span data-ttu-id="77151-190">일정은 언제든지 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-190">You can create or modify a schedule at any time.</span></span> <span data-ttu-id="77151-191">그러나 수정을 마치기 전에 일정이 실행되기 시작하면 이전 버전의 일정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-191">However, if a schedule starts to run before you have completed your modifications, the earlier version of the schedule is used.</span></span> <span data-ttu-id="77151-192">수정된 일정을 저장해야 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-192">The revised schedule does not take effect until you save it.</span></span>  
  
 <span data-ttu-id="77151-193">공유 일정을 수정하는 경우 변경하기 전에 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-193">If you are modifying a shared schedule, you can pause it before you make changes.</span></span> <span data-ttu-id="77151-194">변경 내용은 일정을 다시 시작할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-194">The changes take effect when you resume the schedule.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a><span data-ttu-id="77151-195">공유 일정을 만들거나 수정하려면(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="77151-195">To create or modify a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="77151-196">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-196">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="77151-197">보고서 관리자의 일반 도구 모음에서 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-197">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
3.  <span data-ttu-id="77151-198">**일정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-198">Click **schedules**.</span></span>  
  
4.  <span data-ttu-id="77151-199">**새 일정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-199">Click **New Schedule**.</span></span> <span data-ttu-id="77151-200">기존 일정을 수정하려면 일정 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-200">To modify an existing schedule, click the name of the schedule.</span></span>  
  
5.  <span data-ttu-id="77151-201">일정에 대한 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-201">Type a descriptive name for the schedule.</span></span>  
  
6.  <span data-ttu-id="77151-202">**시간**, **일**, **주**또는 **월**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-202">Select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="77151-203">한 번만 실행되는 일정을 만들려면 **한 번** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-203">Click **Once** to create a schedule that runs one time only.</span></span> <span data-ttu-id="77151-204">일정의 기준을 지정하면 다른 옵션이 추가로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-204">Additional options appear when you specify the basis of your schedule.</span></span>  
  
7.  <span data-ttu-id="77151-205">일정을 시작할 날짜를 선택합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="77151-205">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="77151-206">기본값은 현재 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="77151-206">The default is the current day.</span></span> <span data-ttu-id="77151-207">현재 이후의 날짜를 선택하여 일정 시작 시간을 연기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-207">You can postpone the schedule start time by choosing a later date.</span></span>  
  
8.  <span data-ttu-id="77151-208">일정을 종료할 날짜를 선택합니다(선택 사항).</span><span class="sxs-lookup"><span data-stu-id="77151-208">Optionally, select a date to end the schedule.</span></span> <span data-ttu-id="77151-209">이 날짜에 일정 실행이 중지되지만 일정이 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-209">The schedule stops running on this date, but is not deleted.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a><span data-ttu-id="77151-210">공유 일정을 삭제하려면(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="77151-210">To delete a shared schedule (Report Manager)</span></span>  
  
1.  <span data-ttu-id="77151-211">보고서 관리자의 일반 도구 모음에서 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-211">In Report Manager, click **Site Settings**on the global toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77151-212">**사이트 설정** 을 사용할 수 없으면 사이트 설정에 액세스할 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="77151-212">If **Site Settings** is not available, you do not have permission to access site settings.</span></span>  
  
2.  <span data-ttu-id="77151-213">페이지의 **기타** 섹션에서 **공유 일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-213">In the **Other** section on the page, click **Manage shared schedules**.</span></span>  
  
3.  <span data-ttu-id="77151-214">삭제할 일정 옆의 확인란을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-214">Select the check box next to the schedule you want to delete, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="77151-215">여러 보고서 및 구독에 사용되는 공유 일정을 삭제하면 보고서 서버는 공유 일정을 사용하던 각 보고서 및 구독에 대해 개별적인 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="77151-215">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="77151-216">각 개별 일정에는 공유 일정에 지정되었던 날짜, 시간 및 되풀이 패턴이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-216">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="77151-217">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 개별 일정을 중앙에서 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-217">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="77151-218">공유 일정을 삭제하면 개별 항목에 대해 일정 정보를 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-218">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span>  
  
 <span data-ttu-id="77151-219">공유 일정 사용 여부를 모를 경우에는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-219">If you are not sure whether a shared schedule is used, consider deleting it in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] instead.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="77151-220">에서는 보고서 관리자와 동일한 공유 일정 관리 기능을 제공하지만 일정을 사용하는 각 보고서의 이름을 표시한 추가 보고서 페이지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-220">provides the same shared schedule management features as Report Manager, but it provides an additional Reports page that shows you the name of each report that uses the schedule.</span></span>  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="77151-221">공유 일정 만들기, 삭제 또는 수정(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="77151-221">Create, Delete, or Modify a Shared Schedule (Management Studio)</span></span>  
 <span data-ttu-id="77151-222">공유 일정에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에서 실행되는 게시된 여러 보고서 및 구독에 사용할 수 있는 일정 및 되풀이 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-222">A shared schedule contains schedule and recurrence information that can be used by any number of published reports and subscriptions that run on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="77151-223">동시에 실행되는 보고서와 구독이 여러 개 있을 경우 이러한 작업에 대한 공유 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-223">If you have many reports and subscriptions that run at the same time, you can create a shared schedule for those jobs.</span></span> <span data-ttu-id="77151-224">이후에 되풀이 패턴 또는 종료 날짜를 변경하려는 경우 단일 위치에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-224">If you want to subsequently change the recurrence pattern or the end date, you can make the change in one place.</span></span>  
  
 <span data-ttu-id="77151-225">공유 일정은 관리하기가 더 쉬우므로 예약된 작업을 보다 유연하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-225">Shared schedules are easier to maintain and give you more flexibility in managing scheduled operations.</span></span> <span data-ttu-id="77151-226">예를 들어 공유 일정을 일시 중지하고 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-226">For example, you can pause and resume shared schedules.</span></span> <span data-ttu-id="77151-227">또한 예약된 작업이 동시에 너무 많이 실행되는 경우에는 서로 다른 시간에 실행되는 공유 일정을 여러 개 만든 다음 처리 부하가 보고서 서버에서 균등하게 분포될 때까지 일정 정보를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-227">Also, if you find that too many scheduled operations are running at the same time, you can create multiple shared schedules that run at different times and then adjust the schedule information until the processing load evens out across the report server.</span></span>  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a><span data-ttu-id="77151-228">공유 일정을 만들거나 수정하려면(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="77151-228">To create or modify a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="77151-229">SQL Server Management Studio를 시작하고 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-229">Start SQL Server Management Studio and connect to a report server instance.</span></span>  
  
2.  <span data-ttu-id="77151-230">개체 탐색기에서 보고서 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-230">In Object Explorer, expand a report server node.</span></span>  
  
3.  <span data-ttu-id="77151-231">공유 일정 폴더를 마우스 오른쪽 단추로 클릭하고 **새 일정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-231">Right-click the Shared Schedules folder, and then click **New Schedule**.</span></span> <span data-ttu-id="77151-232">**새 공유 일정** 대화 상자의 일반 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-232">The General page of the **New Shared Schedule** dialog box is displayed.</span></span>  
  
     <span data-ttu-id="77151-233">기존 공유 일정을 수정하려면 공유 일정 폴더를 확장하고 수정할 일정을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-233">To modify an existing shared schedule, expand the Shared Schedules folder, right-click the schedule you want to modify, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="77151-234">일정에 대한 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-234">Type a descriptive name for the schedule.</span></span>  
  
5.  <span data-ttu-id="77151-235">일정을 시작할 날짜를 선택합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="77151-235">Optionally select a date to start the schedule.</span></span> <span data-ttu-id="77151-236">기본값은 현재 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="77151-236">The default is the current day.</span></span>  
  
6.  <span data-ttu-id="77151-237">일정을 종료할 날짜를 선택합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="77151-237">Optionally select a date to end the schedule.</span></span> <span data-ttu-id="77151-238">이 날짜에 일정 실행이 중지되지만 일정이 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-238">The schedule stops running on this date, but is not deleted.</span></span>  
  
7.  <span data-ttu-id="77151-239">되풀이 일정을 구성하려면 **시간**, **일**, **주**또는 **월**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-239">To configure a recurring schedule, select **Hour**, **Day**, **Week**, or **Month**.</span></span> <span data-ttu-id="77151-240">추가 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-240">Additional options are displayed.</span></span> <span data-ttu-id="77151-241">이러한 추가 일정을 사용하여 원하는 시간, 일, 주 또는 월을 기준으로 일정 빈도를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-241">Use these additional options to configure schedule frequency, based on your preferred hour, day, week, or month.</span></span>  
  
     <span data-ttu-id="77151-242">또는 일회 일정 즉, 되풀이되지 않는 일정을 지정하려면 **한 번**을 선택하고 **시작 시간**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-242">Or, to specify a one-time (non-recurring) schedule, select **Once**, and then specify a **Start time**.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a><span data-ttu-id="77151-243">공유 일정을 삭제하려면(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="77151-243">To delete a shared schedule (Management Studio)</span></span>  
  
1.  <span data-ttu-id="77151-244">개체 탐색기에서 보고서 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-244">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="77151-245">공유 일정 폴더를 확장하고 삭제할 일정을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-245">Expand the Shared Schedules folder, right-click the schedule you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="77151-246">**카탈로그 항목 삭제** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="77151-246">The **Delete Catalog Items** dialog box appears.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="77151-247">여러 보고서 및 구독에 사용되는 공유 일정을 삭제하면 보고서 서버는 공유 일정을 사용하던 각 보고서 및 구독에 대해 개별적인 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="77151-247">If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule.</span></span> <span data-ttu-id="77151-248">각 개별 일정에는 공유 일정에 지정되었던 날짜, 시간 및 되풀이 패턴이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="77151-248">Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule.</span></span> <span data-ttu-id="77151-249">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 개별 일정을 중앙에서 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77151-249">Note that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not provide central management of individual schedules.</span></span> <span data-ttu-id="77151-250">공유 일정을 삭제하면 개별 항목에 대해 일정 정보를 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-250">If you delete a shared schedule, you will now have to maintain the schedule information for each individual item.</span></span> <span data-ttu-id="77151-251">공유 일정을 삭제 하기 전에 [보고서 페이지](../tools/schedule-properties-reports-page.md) 를 사용 하 여 현재 공유 일정을 사용 하 고 있는 보고서를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="77151-251">Before deleting a shared schedule, use the [Reports Page](../tools/schedule-properties-reports-page.md) to determine which reports are currently using the shared schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77151-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77151-252">See Also</span></span>  
 <span data-ttu-id="77151-253">[일정](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="77151-253">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="77151-254">[공유 일정 일시 중지 및 다시 시작](pause-and-resume-shared-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="77151-254">[Pause and Resume Shared Schedules](pause-and-resume-shared-schedules.md) </span></span>  
 <span data-ttu-id="77151-255">[보고서 &#40;보고서 관리자 캐시&#41;](../report-server/cache-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="77151-255">[Cache a Report &#40;Report Manager&#41;](../report-server/cache-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="77151-256">보고서 기록에 스냅샷 추가&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="77151-256">Add a Snapshot to Report History &#40;Report Manager&#41;</span></span>](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
