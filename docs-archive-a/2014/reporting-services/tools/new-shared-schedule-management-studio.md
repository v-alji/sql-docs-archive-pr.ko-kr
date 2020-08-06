---
title: 새 공유 일정(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newschedule.f1
ms.assetid: b2c69586-d98e-4933-827d-f5e6c15c5203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6afd406730f815d3ab61e59cdebd21d564daa74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648793"
---
# <a name="new-shared-schedule-management-studio"></a><span data-ttu-id="3eb9f-102">새 공유 일정(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3eb9f-102">New Shared Schedule (Management Studio)</span></span>
  <span data-ttu-id="3eb9f-103">이 페이지를 사용하여 게시된 보고서 및 구독의 공유 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-103">Use this page to create a shared schedule to run published reports and subscriptions.</span></span> <span data-ttu-id="3eb9f-104">보고서별 일정 또는 구독별 일정 대신 공유 일정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="3eb9f-105">공유 일정이 항목별 일정과 구분되는 두 가지 주요 기능은 중앙화된 일정 정보, 그리고 예약된 작업을 일시 중지했다가 재개하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-105">Centralized schedule information and the ability to pause and resume scheduled operations are two key features that distinguish shared schedules from item-specific schedules.</span></span>  
  
 <span data-ttu-id="3eb9f-106">일부 빈도 조합은 단일 일정으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-106">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="3eb9f-107">예를 들어 매주 금요일 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="3eb9f-107">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="3eb9f-108">4시에</span><span class="sxs-lookup"><span data-stu-id="3eb9f-108">and 4:00 P.M.</span></span> <span data-ttu-id="3eb9f-109">보고서를 실행하려면 실행 날짜가 금요일, 시작 시간이 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="3eb9f-109">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="3eb9f-110">4시로 지정된 두 개의 일별 일정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-110">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="3eb9f-111">일정 처리는 일정을 호스팅하고 처리하는 보고서 서버의 현지 시간을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-111">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="3eb9f-112">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버에 연결한 다음 **공유 일정**을 마우스 오른쪽 단추로 클릭하고 **새 일정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Shared Schedule**, and select **New Schedule**.</span></span> <span data-ttu-id="3eb9f-113">일정을 저장하려면 SQL Server 에이전트 서비스가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-113">To save the schedule, SQL Server Agent service must be running.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3eb9f-114">이 기능은 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-114">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3eb9f-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2012 버전에서 지원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3eb9f-116">옵션</span><span class="sxs-lookup"><span data-stu-id="3eb9f-116">Options</span></span>  
 <span data-ttu-id="3eb9f-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-117">**Name**</span></span>  
 <span data-ttu-id="3eb9f-118">공유 일정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-118">Type a name for the shared schedule.</span></span> <span data-ttu-id="3eb9f-119">이 이름은 사용자가 보고서 및 구독에 대한 공유 일정을 선택할 때 드롭다운 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-119">This name appears in drop-down lists when users select a shared schedule for reports and subscriptions.</span></span> <span data-ttu-id="3eb9f-120">공유 일정의 이름은 목록에 넣기에 적합한 길이로, 알아보기 쉽고 서로 구분이 잘 되도록 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-120">Be sure to provide a descriptive name that fits easily within a list and that easily distinguishes one shared schedule from another.</span></span> <span data-ttu-id="3eb9f-121">이름은 하나 이상의 영숫자 문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="3eb9f-122">공백과 특정 기호도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="3eb9f-123">이름 지정 시에는 다음 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="3eb9f-124">; ?</span><span class="sxs-lookup"><span data-stu-id="3eb9f-124">; ?</span></span> <span data-ttu-id="3eb9f-125">: \@ & = +, $/\*\< ></span><span class="sxs-lookup"><span data-stu-id="3eb9f-125">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="3eb9f-126">" /</span><span class="sxs-lookup"><span data-stu-id="3eb9f-126">" /</span></span>  
  
 <span data-ttu-id="3eb9f-127">**일정 시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-127">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="3eb9f-128">이 일정의 시작 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-128">Specify a start date for this schedule.</span></span>  
  
 <span data-ttu-id="3eb9f-129">**일정 종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-129">**Stop this schedule on**</span></span>  
 <span data-ttu-id="3eb9f-130">이 일정의 만료 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-130">Specify an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="3eb9f-131">**형식**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-131">**Type**</span></span>  
 <span data-ttu-id="3eb9f-132">되풀이 패턴의 기준을 시간, 일, 주 또는 월로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-132">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, or months.</span></span>  
  
 <span data-ttu-id="3eb9f-133">**시(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-133">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="3eb9f-134">시간 간격으로 예약된 작업을 실행하려면(예: 6시간마다 보고서 실행) 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-134">Select options to run a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="3eb9f-135">시간 및 분 단위로 간격을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-135">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="3eb9f-136">**일(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-136">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="3eb9f-137">일 간격으로 예약된 작업을 실행하려면(예: 이틀마다 보고서 실행) 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-137">Select options to run a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="3eb9f-138">일, 시간 및 분 단위로 간격을 지정하여 일정을 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-138">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="3eb9f-139">**주(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-139">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="3eb9f-140">주 간격으로 예약된 작업을 실행하려는 경우 또는 반복할 패턴이 주를 기반으로 하는 경우(예: 격주로 보고서 실행) 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-140">Select options to run a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="3eb9f-141">주별 일정을 일, 시간 및 분 단위로 지정하여 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-141">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="3eb9f-142">**월(되풀이 패턴)**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-142">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="3eb9f-143">월 간격으로 예약된 작업을 실행하려는 경우 또는 반복할 패턴이 월을 기반으로 하는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-143">Select options to run a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="3eb9f-144">월별 일정을 일, 시간 및 분 단위로 지정하여 실행시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-144">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="3eb9f-145">일정에서 특정 월을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-145">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="3eb9f-146">**한 번**</span><span class="sxs-lookup"><span data-stu-id="3eb9f-146">**Once**</span></span>  
 <span data-ttu-id="3eb9f-147">특정 날짜 및 시간에 한 번만 실행되는 일정을 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3eb9f-147">Select this option to create a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb9f-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3eb9f-148">See Also</span></span>  
 <span data-ttu-id="3eb9f-149">[Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3eb9f-149">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="3eb9f-150">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3eb9f-150">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="3eb9f-151">[일정 만들기, 수정 및 삭제](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="3eb9f-151">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="3eb9f-152">[일정](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="3eb9f-152">[Schedules](../subscriptions/schedules.md) </span></span>  
 [<span data-ttu-id="3eb9f-153">Management Studio의 보고서 서버 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="3eb9f-153">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
