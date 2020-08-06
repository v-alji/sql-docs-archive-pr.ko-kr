---
title: 리소스 사용 모니터링(시스템 모니터) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], resource usage
- System Monitor [SQL Server], about Windows System Monitor
- resource usage monitoring [SQL Server]
- System Monitor [SQL Server]
- counters [SQL Server], resource usage subjects
- performance counters [SQL Server], resource usage subjects
- Windows System Monitor [SQL Server], about Windows System Monitor
- monitoring [SQL Server], server resource usage
- monitoring resource usage [SQL Server]
- Windows System Monitor [SQL Server]
- database monitoring [SQL Server], resource usage
- database performance [SQL Server], resource usage
- tuning databases [SQL Server], resource usage
- server performance [SQL Server], resource usage
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d691091a41e3161c733902824bf439b6788cc4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660510"
---
# <a name="monitor-resource-usage-system-monitor"></a><span data-ttu-id="ffe6b-102">리소스 사용 모니터링(시스템 모니터)</span><span class="sxs-lookup"><span data-stu-id="ffe6b-102">Monitor Resource Usage (System Monitor)</span></span>
  <span data-ttu-id="ffe6b-103">Microsoft Windows 서버 운영 체제를 실행 중인 경우 시스템 모니터 그래픽 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 성능을 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-103">If you are running Microsoft Windows server operating system, use the System Monitor graphical tool to measure the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ffe6b-104">이 도구에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 및 성능 카운터를 보거나 프로세서, 메모리, 캐시, 스레드 및 프로세스 등 다른 개체의 동작을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-104">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects, performance counters, and the behavior of other objects, such as processors, memory, cache, threads, and processes.</span></span> <span data-ttu-id="ffe6b-105">각 개체는 디바이스 사용, 큐 길이, 지연, 처리량 및 내부 정체의 기타 지표를 측정하는 관련 카운터 집합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-105">Each of these objects has an associated set of counters that measure device usage, queue lengths, delays, and other indicators of throughput and internal congestion.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffe6b-106">Windows NT 4.0 이후 버전에서는 성능 모니터가 시스템 모니터로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-106">System Monitor replaced Performance Monitor after Windows NT 4.0.</span></span>  
  
## <a name="benefits-of-system-monitor"></a><span data-ttu-id="ffe6b-107">시스템 모니터의 이점</span><span class="sxs-lookup"><span data-stu-id="ffe6b-107">Benefits of System Monitor</span></span>  
 <span data-ttu-id="ffe6b-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능과 Windows 성능 간의 상관 관계를 확인하려면 Windows 운영 체제 카운터와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 카운터를 동시에 모니터링하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-108">System Monitor can be useful to monitor Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters at the same time to determine any correlation between the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows.</span></span> <span data-ttu-id="ffe6b-109">예를 들어 Windows 디스크 입/출력(I/O) 카운터와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Manager 카운터를 동시에 모니터링하면 전체 시스템의 동작을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-109">For example, monitoring the Windows disk input/output (I/O) counters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Manager counters at the same time can reveal the behavior of the entire system.</span></span>  
  
 <span data-ttu-id="ffe6b-110">시스템 모니터를 사용하여 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업과 성능에 대한 통계를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-110">System Monitor allows you to obtain statistics on current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity and performance.</span></span> <span data-ttu-id="ffe6b-111">시스템 모니터를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-111">Using System Monitor, you can:</span></span>  
  
-   <span data-ttu-id="ffe6b-112">컴퓨터 수에 상관없이 동시에 데이터를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-112">View data simultaneously from any number of computers.</span></span>  
  
-   <span data-ttu-id="ffe6b-113">현재 작업을 반영한 차트를 보거나 변경하고 사용자가 정의한 빈도에 따라 업데이트된 카운터 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-113">View and change charts to reflect current activity, and show counter values that are updated at a frequency that the user defines.</span></span>  
  
-   <span data-ttu-id="ffe6b-114">추가 처리 및 인쇄를 위해 차트, 로그, 경고 로그, 보고서에서 스프레드시트나 데이터베이스 애플리케이션으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-114">Export data from charts, logs, alert logs, and reports to spreadsheet or database applications for further manipulation and printing.</span></span>  
  
-   <span data-ttu-id="ffe6b-115">경고 로그에 있는 이벤트를 나열하고 네트워크 경고를 발생시켜 사용자에게 알릴 수 있는 시스템 경고를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-115">Add system alerts that list an event in the alert log and can notify you by issuing a network alert.</span></span>  
  
-   <span data-ttu-id="ffe6b-116">처음으로 카운터 값이 사용자가 정의한 값보다 크거나 작게 될 때 또는 그럴 때마다 매번 미리 정의한 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-116">Run a predefined application the first time or every time a counter value goes over or under a user-defined value.</span></span>  
  
-   <span data-ttu-id="ffe6b-117">여러 컴퓨터의 다양한 개체에 대한 데이터를 포함한 로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-117">Create log files that contain data about various objects from different computers.</span></span>  
  
-   <span data-ttu-id="ffe6b-118">한 파일에 다른 기존 로그 파일에서 선택한 섹션을 추가하여 장기 보관 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-118">Append to one file selected sections from other existing log files to form a long-term archive.</span></span>  
  
-   <span data-ttu-id="ffe6b-119">현재 작업 보고서를 보거나 기존 로그 파일로부터 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-119">View current-activity reports, or create reports from existing log files.</span></span>  
  
-   <span data-ttu-id="ffe6b-120">개별 차트, 경고, 로그, 보고서 설정 또는 전체 작업 영역 설정을 다시 사용할 수 있도록 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-120">Save individual chart, alert, log, or report settings, or the entire workspace setup for reuse.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffe6b-121">Windows NT 4.0 이후로 시스템 모니터가 성능 모니터를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-121">System Monitor replaced the Performance Monitor after Windows NT 4.0.</span></span> <span data-ttu-id="ffe6b-122">시스템 모니터 또는 성능 모니터를 사용하여 이 태스크를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-122">You can use either the System Monitor or Performance Monitor to do these tasks.</span></span>  
  
## <a name="system-monitor-performance"></a><span data-ttu-id="ffe6b-123">시스템 모니터 성능</span><span class="sxs-lookup"><span data-stu-id="ffe6b-123">System Monitor Performance</span></span>  
 <span data-ttu-id="ffe6b-124">성능 관련 문제를 검사하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Microsoft Windows 운영 체제를 모니터링할 때 초기에는 다음 3개 주요 영역을 집중적으로 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-124">When you monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system to investigate performance-related issues, concentrate your initial efforts in three main areas:</span></span>  
  
-   <span data-ttu-id="ffe6b-125">디스크 작업</span><span class="sxs-lookup"><span data-stu-id="ffe6b-125">Disk activity</span></span>  
  
-   <span data-ttu-id="ffe6b-126">프로세서 사용률</span><span class="sxs-lookup"><span data-stu-id="ffe6b-126">Processor utilization</span></span>  
  
-   <span data-ttu-id="ffe6b-127">메모리 사용량</span><span class="sxs-lookup"><span data-stu-id="ffe6b-127">Memory usage</span></span>  
  
 <span data-ttu-id="ffe6b-128">시스템 모니터가 실행 중인 컴퓨터를 모니터링하면 컴퓨터 성능에 약간의 영향을 줄 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="ffe6b-128">Monitoring a computer on which System Monitor is running can affect computer performance slightly.</span></span> <span data-ttu-id="ffe6b-129">시스템 모니터 데이터를 다른 디스크나 컴퓨터에 기록해 모니터링하는 컴퓨터에 미치는 영향을 줄이거나 시스템 모니터를 원격 컴퓨터에서 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-129">Therefore, either log the System Monitor data to another disk (or computer) so that it reduces the effect on the computer being monitored, or run System Monitor from a remote computer.</span></span> <span data-ttu-id="ffe6b-130">또한 관심 있는 카운터만 모니터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-130">Monitor only the counters in which you are interested.</span></span> <span data-ttu-id="ffe6b-131">너무 많은 수의 카운터를 모니터링하면 모니터링 프로세스에 리소스 사용 오버헤드가 추가되고 모니터링하고 있는 컴퓨터의 성능에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-131">If you monitor too many counters, resource usage overhead is added to the monitoring process and affects the performance of the computer that is being monitored.</span></span>  
  
## <a name="system-monitor-tasks"></a><span data-ttu-id="ffe6b-132">시스템 모니터 태스크</span><span class="sxs-lookup"><span data-stu-id="ffe6b-132">System Monitor Tasks</span></span>  
  
|<span data-ttu-id="ffe6b-133">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="ffe6b-133">Task Description</span></span>|<span data-ttu-id="ffe6b-134">항목</span><span class="sxs-lookup"><span data-stu-id="ffe6b-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ffe6b-135">시스템 모니터를 사용하는 경우에 대해 설명하고 시스템 모니터를 사용하는 경우의 성능 오버헤드에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-135">Describes when to use System Monitor and discusses performance overhead when you use System Monitor.</span></span>|[<span data-ttu-id="ffe6b-136">시스템 모니터 실행</span><span class="sxs-lookup"><span data-stu-id="ffe6b-136">Run System Monitor</span></span>](run-system-monitor.md)|  
|<span data-ttu-id="ffe6b-137">디스크 카운터를 모니터링하여 SQL Server 구성 요소에서 생성된 I/O 양과 디스크 작업을 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-137">Describes how to monitor disk counters to determine disk activity and the amount of I/O generated by their SQL Server components.</span></span>|[<span data-ttu-id="ffe6b-138">디스크 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="ffe6b-138">Monitor Disk Usage</span></span>](monitor-disk-usage.md)|  
|<span data-ttu-id="ffe6b-139">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 모니터링하여 CPU 사용량이 정상 범위에 있는지를 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-139">Describes how to monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to determine whether CPU usage rates are within normal ranges.</span></span>|[<span data-ttu-id="ffe6b-140">CPU 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="ffe6b-140">Monitor CPU Usage</span></span>](monitor-cpu-usage.md)|  
|<span data-ttu-id="ffe6b-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 모니터링하여 메모리 사용이 일반적인 범위 이내에 있는지를 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-141">Describes how to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to confirm that memory usage is within typical ranges.</span></span>|[<span data-ttu-id="ffe6b-142">메모리 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="ffe6b-142">Monitor Memory Usage</span></span>](monitor-memory-usage.md)|  
|<span data-ttu-id="ffe6b-143">시스템 모니터 카운터의 임계값에 도달했을 때 발생하는 경고를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-143">Describes how to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span>|[<span data-ttu-id="ffe6b-144">SQL Server 데이터베이스 경고 만들기</span><span class="sxs-lookup"><span data-stu-id="ffe6b-144">Create a SQL Server Database Alert</span></span>](create-a-sql-server-database-alert.md)|  
|<span data-ttu-id="ffe6b-145">차트, 경고, 로그 및 보고서를 만들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 모니터링하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-145">Describes how to you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="ffe6b-146">차트, 경고, 로그 및 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="ffe6b-146">Create Charts, Alerts, Logs, and Reports</span></span>](create-charts-alerts-logs-and-reports.md)|  
|<span data-ttu-id="ffe6b-147">시스템 모니터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 실행 중인 컴퓨터에서 작업을 모니터링하는 데 사용하는 개체 및 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-147">Lists objects and counters that System Monitor uses to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="ffe6b-148">SQL Server 개체 사용</span><span class="sxs-lookup"><span data-stu-id="ffe6b-148">Use SQL Server Objects</span></span>](use-sql-server-objects.md)|  
|<span data-ttu-id="ffe6b-149">시스템 모니터에서 메모리 내 OLTP 작업을 모니터링하는 데 사용하는 개체 및 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe6b-149">Lists objects and counters that System Monitor uses to monitor In-Memory OLTP activity.</span></span>|[<span data-ttu-id="ffe6b-150">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="ffe6b-150">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)|  
  
  
