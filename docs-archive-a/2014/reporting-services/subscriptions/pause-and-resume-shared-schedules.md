---
title: 공유 일정 일시 중지 및 다시 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f525a15b07b79b5c0d37f9a88ed9483b351af326
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651459"
---
# <a name="pause-and-resume-shared-schedules"></a><span data-ttu-id="f3a2f-102">공유 일정 일시 중지 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="f3a2f-102">Pause and Resume Shared Schedules</span></span>
  <span data-ttu-id="f3a2f-103">사용 중인 공유 일정을 일시 중지하고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-103">You can pause and resume a shared schedule that is in use.</span></span> <span data-ttu-id="f3a2f-104">공유 일정을 일시 중지하여 보고서 처리 및 구독을 트리거하는 데 사용되는 일정을 일시적으로 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-104">Pausing a shared schedule provides a way to temporarily freeze a schedule that is used to trigger report processing and subscriptions.</span></span> <span data-ttu-id="f3a2f-105">공유 일정만 일시 중지하고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-105">Only shared schedules can be paused and resumed.</span></span> <span data-ttu-id="f3a2f-106">보고서별 일정은 일시 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-106">You cannot pause report-specific schedules.</span></span>  
  
 <span data-ttu-id="f3a2f-107">진행 중인 보고서의 처리는 일시 중지하고 다시 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-107">You cannot pause and resume report processing that is in progress.</span></span> <span data-ttu-id="f3a2f-108">SQL Server 에이전트 서비스의 일정 큐에 있는 일정만 일시 중지하고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-108">You can only pause and resume schedules that are in the scheduling queue of SQL Server Agent service.</span></span> <span data-ttu-id="f3a2f-109">처리 중인 작업은 일정 예약 엔진 범위 밖에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-109">A job that is in progress is outside the scope of the scheduling engine.</span></span> <span data-ttu-id="f3a2f-110">자세한 내용은 [실행 중인 프로세스 관리](manage-a-running-process.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-110">For more information, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="f3a2f-111">공유 일정이 일시 중지된 동안 수행되었어야 하는 모든 작업은 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-111">While a shared schedule is paused, any operations that would have occurred are allowed to lapse.</span></span> <span data-ttu-id="f3a2f-112">공유 일정을 다시 시작하면 서버의 현지 시간을 사용하여 다음 예약된 시간에 보고서 및 구독 처리가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-112">After you resume a shared schedule, report and subscription processing occurs at the next scheduled time, using the local time of the server.</span></span> <span data-ttu-id="f3a2f-113">기본 모드 보고서 서버 또는 SharePoint 서비스 애플리케이션은 일정을 일시 중지하지 않았으면 수행되었을 예약된 작업을 만회하려고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-113">The native mode report server or SharePoint service applications, do not make up scheduled operations that would have occurred had the schedule not been paused.</span></span>  
  
 <span data-ttu-id="f3a2f-114">항목 내용</span><span class="sxs-lookup"><span data-stu-id="f3a2f-114">In this Topic:</span></span>  
  
-   [<span data-ttu-id="f3a2f-115">공유 일정 일시 중지 및 다시 시작(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="f3a2f-115">Pause and Resume Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="f3a2f-116">공유 일정 일시 중지 및 다시 시작(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="f3a2f-116">Pause and Resume Shared Schedules (SharePoint mode)</span></span>](#bkmk_sharepoint)  
  
##  <a name="pause-and-resume-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="f3a2f-117">공유 일정 일시 중지 및 다시 시작(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="f3a2f-117">Pause and Resume Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="f3a2f-118">공유 일정을 일시 중지하고 다시 시작하려면 보고서 관리자에서 일정 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-118">To pause and resume a shared schedule, use the Schedules page in Report Manager.</span></span> <span data-ttu-id="f3a2f-119">여기에는 일정을 일시 중지하고 다시 시작하는 옵션이 없으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-119">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]; it does not provide options for pausing and resuming schedules.</span></span> <span data-ttu-id="f3a2f-120">자세한 내용은 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-120">For more information, see [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md).</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="f3a2f-121">공유 일정을 일시 중지 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f3a2f-121">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="f3a2f-122">보고서 관리자에서 **사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-122">From Report Manager Click, **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="f3a2f-123">**일정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-123">Click **Schedules**.</span></span>  
  
3.  <span data-ttu-id="f3a2f-124">일정을 선택하고 리본에서 **일시 중지** 를 클릭하거나 **재개** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-124">Select the schedule, and click **Pause** or **Resume** in the ribbon.</span></span> <span data-ttu-id="f3a2f-125">일정이 현재 일시 중지된 경우 **상태** 열에 **일시 중지됨**이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-125">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
##  <a name="pause-and-resume-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="f3a2f-126">공유 일정 일시 중지 및 다시 시작(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="f3a2f-126">Pause and Resume Shared Schedules (SharePoint mode)</span></span>  
 <span data-ttu-id="f3a2f-127">공유 일정을 일시 중지하고 재개하려면 사이트 설정 페이지 또는 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-127">To pause and resume a shared schedule, use the Site Settings page or PowerShell.</span></span> <span data-ttu-id="f3a2f-128">일정은 SharePoint 사이트에 따라 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-128">Schedules are managed per SharePoint site.</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="f3a2f-129">공유 일정을 일시 중지 또는 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f3a2f-129">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="f3a2f-130">**사이트 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-130">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="f3a2f-131">**사이트 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-131">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="f3a2f-132">Reporting Services 섹션에서 **공유 일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-132">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="f3a2f-133">일정을 선택하고 **선택한 일정 일시 중지** 또는 **선택한 일정 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-133">Select the schedule, and click **Pause Selected Schedules** or **Run Selected Schedules**.</span></span> <span data-ttu-id="f3a2f-134">일정이 현재 일시 중지된 경우 **상태** 열에 **일시 중지됨**이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3a2f-134">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a2f-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3a2f-135">See Also</span></span>  
 <span data-ttu-id="f3a2f-136">[일정](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="f3a2f-136">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="f3a2f-137">[일정 만들기, 수정 및 삭제](create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="f3a2f-137">[Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="f3a2f-138">[보고서 서버에서 표준 시간대 및 시계 설정 변경](change-time-zones-and-clock-settings-on-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f3a2f-138">[Change Time Zones and Clock Settings on a Report Server](change-time-zones-and-clock-settings-on-a-report-server.md) </span></span>  
 [<span data-ttu-id="f3a2f-139">실행 중인 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="f3a2f-139">Manage a Running Process</span></span>](manage-a-running-process.md)  
  
  
