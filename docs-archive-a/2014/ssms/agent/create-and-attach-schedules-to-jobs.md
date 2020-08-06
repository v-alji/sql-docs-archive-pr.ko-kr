---
title: 일정을 만들고 작업에 연결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ced47013b6552725e6350b113a3722b066016a6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731380"
---
# <a name="create-and-attach-schedules-to-jobs"></a><span data-ttu-id="89b68-102">일정을 만들고 작업에 연결</span><span class="sxs-lookup"><span data-stu-id="89b68-102">Create and Attach Schedules to Jobs</span></span>
  <span data-ttu-id="89b68-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 일정 예약이란 사용자 개입 없이 작업을 실행할 조건을 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-103">Scheduling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs means defining the condition or conditions that cause the job to begin running without user interaction.</span></span> <span data-ttu-id="89b68-104">작업에 대한 새로운 일정을 만들거나 기존 일정을 작업에 연결하여 작업이 자동으로 실행되도록 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-104">You can schedule a job to run automatically by creating a new schedule for the job, or by attaching an existing schedule to the job.</span></span>  
  
 <span data-ttu-id="89b68-105">일정을 만드는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-105">There are two ways to create a schedule:</span></span>  
  
-   <span data-ttu-id="89b68-106">작업을 만드는 동안 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-106">Create the schedule while you are creating a job.</span></span>  
  
-   <span data-ttu-id="89b68-107">개체 탐색기에서 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-107">Create the schedule in Object Explorer.</span></span>  
  
 <span data-ttu-id="89b68-108">일정을 만든 후에는 특정 작업을 위해 만든 일정이더라도 여러 작업에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-108">After a schedule has been created, you can attach that schedule to multiple jobs, even if the schedule was created for a specific job.</span></span> <span data-ttu-id="89b68-109">또한 작업에 연결된 일정을 분리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-109">You can also detach schedules from jobs.</span></span>  
  
 <span data-ttu-id="89b68-110">일정은 시간 또는 이벤트에 기반을 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-110">A schedule can be based upon time or an event.</span></span> <span data-ttu-id="89b68-111">예를 들어 다음과 같은 시간에 작업이 실행되도록 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-111">For example, you can schedule a job to run at the following times:</span></span>  
  
-   <span data-ttu-id="89b68-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 시작할 때마다</span><span class="sxs-lookup"><span data-stu-id="89b68-112">Whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts.</span></span>  
  
-   <span data-ttu-id="89b68-113">컴퓨터의 CPU 사용률이 유휴로 정의한 수준에 있을 때마다</span><span class="sxs-lookup"><span data-stu-id="89b68-113">Whenever CPU utilization of the computer is at a level you have defined as idle.</span></span>  
  
-   <span data-ttu-id="89b68-114">특정 날짜와 특정 시간에 한 번</span><span class="sxs-lookup"><span data-stu-id="89b68-114">One time, at a specific date and time.</span></span>  
  
-   <span data-ttu-id="89b68-115">되풀이 일정.</span><span class="sxs-lookup"><span data-stu-id="89b68-115">On a recurring schedule.</span></span>  
  
 <span data-ttu-id="89b68-116">작업을 실행하여 이벤트에 응답하는 경고를 만들어 작업 일정을 대체할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-116">As an alternative to job schedules, you can also create an alert that responds to an event by running a job.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89b68-117">하나의 작업 인스턴스만 동시에 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-117">Only one instance of the job can be run at a time.</span></span> <span data-ttu-id="89b68-118">일정대로 작업이 실행될 때 작업을 수동으로 실행하려고 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 요청을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-118">If you try to run a job manually while it is running as scheduled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refuses the request.</span></span>  
  
 <span data-ttu-id="89b68-119">예약된 작업이 실행되지 않도록 하려면 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-119">To prevent a scheduled job from running, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="89b68-120">일정을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-120">Disable the schedule.</span></span>  
  
-   <span data-ttu-id="89b68-121">작업을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-121">Disable the job.</span></span>  
  
-   <span data-ttu-id="89b68-122">작업에 연결된 일정을 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-122">Detach the schedule from the job.</span></span>  
  
-   <span data-ttu-id="89b68-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
-   <span data-ttu-id="89b68-124">일정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-124">Delete the schedule.</span></span>  
  
 <span data-ttu-id="89b68-125">일정이 활성화되어 있지 않은 경우 경고에 응답하거나 사용자가 작업을 수동으로 실행할 때도 작업을 계속 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-125">If the schedule is not enabled, the job can still run in response to an alert or when a user runs the job manually.</span></span> <span data-ttu-id="89b68-126">작업 일정이 활성화되어 있지 않으면 해당 일정을 사용하는 모든 작업의 일정이 활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-126">When a job schedule is not enabled, the schedule is not enabled for any job that uses the schedule.</span></span>  
  
 <span data-ttu-id="89b68-127">일정이 해제되었으면 명시적으로 다시 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-127">You must explicitly re-enable a schedule that has been disabled.</span></span> <span data-ttu-id="89b68-128">일정을 편집해도 일정이 자동으로 다시 활성화되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-128">Editing the schedule does not automatically re-enable the schedule.</span></span>  
  
## <a name="scheduling-start-dates"></a><span data-ttu-id="89b68-129">시작 날짜 예약</span><span class="sxs-lookup"><span data-stu-id="89b68-129">Scheduling Start Dates</span></span>  
 <span data-ttu-id="89b68-130">일정의 시작 날짜는 19900101 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-130">The start date of a schedule must be greater than or equal to 19900101.</span></span>  
  
 <span data-ttu-id="89b68-131">일정을 작업에 연결할 때는 일정이 처음으로 작업을 실행할 시작 날짜를 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-131">When you are attaching a schedule to a job, you should review the start date that the schedule uses to run the job for the first time.</span></span> <span data-ttu-id="89b68-132">시작 날짜는 일정을 작업에 연결한 날짜 및 시간에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-132">The start date depends upon the day and time when you attach the schedule to the job.</span></span> <span data-ttu-id="89b68-133">예를 들어 격주로 월요일 오전 8:00시에 실행되는 일정을 만들고</span><span class="sxs-lookup"><span data-stu-id="89b68-133">For example, you create a schedule that runs every other Monday at 8:00 A.M.</span></span> <span data-ttu-id="89b68-134">2008년 3월 3일 월요일 오전 10:00시에 작업을 만드는 경우</span><span class="sxs-lookup"><span data-stu-id="89b68-134">If you create a job at 10:00 A.M.</span></span> <span data-ttu-id="89b68-135">일정 시작 날짜는 2008년 3월 17일 월요일입니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-135">on Monday, March 3, 2008, the schedule start date is Monday, March 17, 2008.</span></span> <span data-ttu-id="89b68-136">다른 작업을 2008년 3월 4일 화요일에 만드는 경우에는 일정 시작 날짜가 2008년 3월 10일 월요일입니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-136">If you create another job on Tuesday, March 4, 2008, the schedule start date is Monday, March 10, 2008.</span></span>  
  
 <span data-ttu-id="89b68-137">일정을 작업에 연결한 후에 일정 시작 날짜를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-137">You can change the schedule start date after you attach the schedule to a job.</span></span>  
  
## <a name="cpu-idle-schedules"></a><span data-ttu-id="89b68-138">CPU 유휴 일정</span><span class="sxs-lookup"><span data-stu-id="89b68-138">CPU Idle Schedules</span></span>  
 <span data-ttu-id="89b68-139">CPU 리소스를 최대화하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 대해 CPU 유휴 상태를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-139">To maximize CPU resources, you can define a CPU idle condition for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="89b68-140">에이전트는 CPU 유휴 상태 설정을 사용하여 작업 실행의 최적 시기를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-140">Agent uses the CPU idle condition setting to determine the best time to run jobs.</span></span> <span data-ttu-id="89b68-141">예를 들어 CPU 유휴 시간과 프로덕션 속도가 느린 시간에 인덱스를 다시 구축하도록 작업을 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-141">For example, you can schedule a job to rebuild indexes during CPU idle time and slow production periods.</span></span>  
  
 <span data-ttu-id="89b68-142">CPU 유휴 시간 동안 작업이 실행되도록 정의하기 전에 정상적인 처리 동안 CPU의 로드를 결정하십시오.</span><span class="sxs-lookup"><span data-stu-id="89b68-142">Before you define jobs to run during CPU idle time, determine the load on the CPU during normal processing.</span></span> <span data-ttu-id="89b68-143">이렇게 하려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 또는 성능 모니터를 사용하여 서버 트래픽을 모니터링하고 통계 자료를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-143">To do this, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor server traffic and collect statistics.</span></span> <span data-ttu-id="89b68-144">수집한 정보를 사용하여 CPU 유휴 시간 백분율과 지속 시간을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-144">You can then use the information you gather to set the CPU idle time percentage and duration.</span></span>  
  
 <span data-ttu-id="89b68-145">CPU 유휴 조건을 CPU 사용이 지정된 시간 동안 그 이하로 유지되어야 하는 백분율로 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="89b68-145">Define the CPU idle condition as a percentage below which CPU usage must remain for a specified time.</span></span> <span data-ttu-id="89b68-146">그런 다음 시간을 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="89b68-146">Next, set the amount of time.</span></span> <span data-ttu-id="89b68-147">CPU 사용률이 지정한 시간에 대해 지정한 백분율 미만이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 CPU 유휴 시간 일정이 예정된 모든 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-147">When the CPU usage is below the specified percentage for the specified amount of time, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts all jobs that have a CPU idle time schedule.</span></span> <span data-ttu-id="89b68-148">또는 성능 모니터를 사용 하 여 CPU 사용량을 모니터링 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Cpu 사용량 모니터링](../../relational-databases/performance-monitor/monitor-cpu-usage.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89b68-148">For more information on using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor CPU usage, see [Monitor CPU Usage](../../relational-databases/performance-monitor/monitor-cpu-usage.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="89b68-149">관련 작업</span><span class="sxs-lookup"><span data-stu-id="89b68-149">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89b68-150">**설명**</span><span class="sxs-lookup"><span data-stu-id="89b68-150">**Description**</span></span>|<span data-ttu-id="89b68-151">**항목**</span><span class="sxs-lookup"><span data-stu-id="89b68-151">**Topic**</span></span>|  
|<span data-ttu-id="89b68-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 대한 예약을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-152">Describes how to create a schedule for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="89b68-153">일정 만들기</span><span class="sxs-lookup"><span data-stu-id="89b68-153">Create a Schedule</span></span>](create-a-schedule.md)|  
|<span data-ttu-id="89b68-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 예약하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-154">Describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="89b68-155">작업 예약</span><span class="sxs-lookup"><span data-stu-id="89b68-155">Schedule a Job</span></span>](schedule-a-job.md)|  
|<span data-ttu-id="89b68-156">서버의 CPU 유휴 상태 판단 기준을 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89b68-156">Explains how to define the CPU idle condition for your server.</span></span>|[<span data-ttu-id="89b68-157">CPU 유휴 시간 및 기간 설정&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="89b68-157">Set CPU Idle Time and Duration &#40;SQL Server Management Studio&#41;</span></span>](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="89b68-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89b68-158">See Also</span></span>  
 <span data-ttu-id="89b68-159">[Transact-sql&#41;sp_help_jobschedule &#40;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89b68-159">[sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span></span>  
 [<span data-ttu-id="89b68-160">Transact-sql&#41;&#40;dbo.sysjobschedules</span><span class="sxs-lookup"><span data-stu-id="89b68-160">dbo.sysjobschedules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
