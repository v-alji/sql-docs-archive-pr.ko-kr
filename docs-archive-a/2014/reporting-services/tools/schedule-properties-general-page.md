---
title: 일정 속성(일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649363"
---
# <a name="schedule-properties-general-page"></a><span data-ttu-id="298ba-102">일정 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="298ba-102">Schedule Properties (General Page)</span></span>
  <span data-ttu-id="298ba-103">이 페이지를 사용하여 공유 일정을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-103">Use this page to view or modify a shared schedule.</span></span> <span data-ttu-id="298ba-104">보고서별 일정 또는 구독별 일정 대신 공유 일정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="298ba-105">일정에 대한 변경 내용은 일정을 저장한 후에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-105">Changes to the schedule are applied after you save the schedule.</span></span> <span data-ttu-id="298ba-106">일정을 편집해도 현재 진행 중인 작업은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-106">Editing a schedule has no effect on jobs that are currently in progress.</span></span> <span data-ttu-id="298ba-107">사용 중인 일정을 편집할 경우 해당 일정에서 트리거된 현재 처리 중인 모든 보고서 및 구독을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-107">If you edit a schedule while it is being used, all currently processing reports and subscriptions triggered from that schedule will be allowed to finish.</span></span>  
  
 <span data-ttu-id="298ba-108">일부 빈도 조합은 단일 일정으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-108">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="298ba-109">예를 들어 매주 금요일 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="298ba-109">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="298ba-110">4시에</span><span class="sxs-lookup"><span data-stu-id="298ba-110">and 4:00 P.M.</span></span> <span data-ttu-id="298ba-111">보고서를 실행하려면 실행 날짜가 금요일, 시작 시간이 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="298ba-111">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="298ba-112">4시로 지정된 두 개의 일별 일정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-112">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="298ba-113">일정 처리는 일정을 호스팅하고 처리하는 보고서 서버의 현지 시간을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-113">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="298ba-114">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버에 연결한 다음 **공유 일정** 폴더를 열고 공유 일정을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-114">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="298ba-115">이 기능은 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서는 사용할 수 없으며 이 페이지는 이 기능이 포함되지 않은 버전을 실행할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-115">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and this page does not appear when you are running an edition which does not have this feature.</span></span> <span data-ttu-id="298ba-116">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) 을 참조 하세요 https://go.microsoft.com/fwlink/?linkid=232473) .</span><span class="sxs-lookup"><span data-stu-id="298ba-116">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="298ba-117">옵션</span><span class="sxs-lookup"><span data-stu-id="298ba-117">Options</span></span>  
 <span data-ttu-id="298ba-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="298ba-118">**Name**</span></span>  
 <span data-ttu-id="298ba-119">공유 일정의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-119">Specifies the name for the shared schedule.</span></span>  
  
 <span data-ttu-id="298ba-120">**일정 시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="298ba-120">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="298ba-121">이 일정의 시작 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-121">Specifies a start date for this schedule.</span></span>  
  
 <span data-ttu-id="298ba-122">**일정 종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="298ba-122">**Stop this schedule on**</span></span>  
 <span data-ttu-id="298ba-123">이 일정의 만료 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-123">Specifies an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="298ba-124">**형식**</span><span class="sxs-lookup"><span data-stu-id="298ba-124">**Type**</span></span>  
 <span data-ttu-id="298ba-125">되풀이 패턴의 기준을 시간, 일, 주 또는 월로 지정하거나 한 번만 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-125">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, months, or only runs once.</span></span>  
  
 <span data-ttu-id="298ba-126">**시(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="298ba-126">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="298ba-127">시간 간격으로 예약된 작업을 실행하려면(예: 6시간마다 보고서 실행) 이 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-127">Specifies options for running a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="298ba-128">시간 및 분 단위로 간격을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-128">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="298ba-129">**일(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="298ba-129">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="298ba-130">일 간격으로 예약된 작업을 실행하려면(예: 이틀마다 보고서 실행) 이 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-130">Specifies options for running a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="298ba-131">일, 시간 및 분 단위로 간격을 지정하여 일정을 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-131">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="298ba-132">**주(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="298ba-132">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="298ba-133">주 간격으로 예약된 작업을 실행하려는 경우 또는 반복할 패턴이 주를 기반으로 하는 경우(예: 격주로 보고서 실행) 이 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-133">Specifies options for running a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="298ba-134">주별 일정을 일, 시간 및 분 단위로 지정하여 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-134">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="298ba-135">**월(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="298ba-135">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="298ba-136">월 간격으로 예약된 작업을 실행하려는 경우 또는 반복할 패턴이 월을 기반으로 하는 경우 이 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-136">Specifies options for running a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="298ba-137">월별 일정을 일, 시간 및 분 단위로 지정하여 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-137">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="298ba-138">일정에서 특정 월을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-138">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="298ba-139">**한 번**</span><span class="sxs-lookup"><span data-stu-id="298ba-139">**Once**</span></span>  
 <span data-ttu-id="298ba-140">특정 날짜 및 시간에 한 번만 실행되는 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="298ba-140">Specifies a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298ba-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="298ba-141">See Also</span></span>  
 <span data-ttu-id="298ba-142">[Management Studio F1 도움말의 보고서 서버](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="298ba-142">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="298ba-143">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="298ba-143">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="298ba-144">[일정 만들기, 수정 및 삭제](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="298ba-144">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="298ba-145">일정</span><span class="sxs-lookup"><span data-stu-id="298ba-145">Schedules</span></span>](../subscriptions/schedules.md)  
  
  
