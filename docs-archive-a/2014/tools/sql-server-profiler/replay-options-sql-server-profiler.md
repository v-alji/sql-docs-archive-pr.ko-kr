---
title: 재생 옵션 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
- health monitor [SQL Server]
- Replay Configuration dialog box
ms.assetid: 58761a25-a84f-4a90-9c61-97700bc5ad9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 695a1431145813f0a7829626a380e510d0e602e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737240"
---
# <a name="replay-options-sql-server-profiler"></a><span data-ttu-id="9afa9-102">재생 옵션(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="9afa9-102">Replay Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="9afa9-103">캡처된 추적을 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생하기 전에 **재생 구성** 대화 상자에서 재생 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-103">Before replaying a captured trace with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], specify replay options in the **Replay Configuration** dialog box.</span></span> <span data-ttu-id="9afa9-104">이 대화 상자를 열려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에서 추적 파일이나 테이블을 연 다음 **재생** 메뉴에서 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-104">To launch this dialog box, open the replay trace file or table in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and on the **Replay** menu, click **Start**.</span></span> <span data-ttu-id="9afa9-105">추적 재생에 필요한 권한에 대한 자세한 내용은 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9afa9-105">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="9afa9-106">이 항목에서는 **재생 구성** 대화 상자에서 지정할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-106">This topic describes the options specified with the **Replay Configuration** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9afa9-107">리소스를 많이 사용하는 OLTP 애플리케이션(활성 동시 연결 수가 많거나 처리량이 많음)을 재생하는 데는 Distributed Replay Utility를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-107">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="9afa9-108">Distributed Replay Utility는 여러 컴퓨터의 추적 데이터를 재생할 수 있으므로 중요한 작업을 효율적으로 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-108">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="9afa9-109">자세한 내용은 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9afa9-109">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="basic-replay-options"></a><span data-ttu-id="9afa9-110">기본 재생 옵션</span><span class="sxs-lookup"><span data-stu-id="9afa9-110">Basic Replay Options</span></span>  
 <span data-ttu-id="9afa9-111">**서버 재생**</span><span class="sxs-lookup"><span data-stu-id="9afa9-111">**Replay server**</span></span>  
 <span data-ttu-id="9afa9-112">서버는 추적을 재생할 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-112">The server is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] against which you want to replay the trace.</span></span> <span data-ttu-id="9afa9-113">서버는 [Replay Requirements](replay-requirements.md)에서 설명하는 재생 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-113">The server must adhere to the replay requirements described in [Replay Requirements](replay-requirements.md)."</span></span>  
  
 <span data-ttu-id="9afa9-114">**파일에 저장**</span><span class="sxs-lookup"><span data-stu-id="9afa9-114">**Save to file**</span></span>  
 <span data-ttu-id="9afa9-115">나중에 볼 수 있도록 추적 재생의 결과가 기록되는 출력 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-115">The output file where the result of replaying the trace is written for later viewing.</span></span> <span data-ttu-id="9afa9-116">기본적으로 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 추적 재생의 결과만 화면에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-116">By default, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] displays only the results of replaying the trace on the screen.</span></span>  
  
 <span data-ttu-id="9afa9-117">**테이블에 저장**</span><span class="sxs-lookup"><span data-stu-id="9afa9-117">**Save to table**</span></span>  
 <span data-ttu-id="9afa9-118">나중에 볼 수 있도록 추적 재생의 결과가 기록되는 데이터베이스 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-118">The database table where the result of replaying the trace is written for later viewing.</span></span>  
  
 <span data-ttu-id="9afa9-119">**재생 스레드 수**</span><span class="sxs-lookup"><span data-stu-id="9afa9-119">**Number of replay threads**</span></span>  
 <span data-ttu-id="9afa9-120">동시에 사용할 재생 스레드 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-120">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="9afa9-121">지정한 수가 클수록 재생 중에 리소스가 많이 사용되지만 재생은 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-121">A higher number consumes more resources during replay, but replay is faster.</span></span> <span data-ttu-id="9afa9-122">여러 스레드를 사용하면 이벤트 순서가 유지되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-122">Event ordering is not fully maintained when multiple threads are used.</span></span>  
  
 <span data-ttu-id="9afa9-123">**추적한 순서대로 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="9afa9-123">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="9afa9-124">각 추적을 단계별로 실행하는 것과 같은 디버깅 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-124">Allows you to use debugging methods such as stepping through each trace.</span></span> <span data-ttu-id="9afa9-125">이 옵션을 선택하지 않으면 이벤트가 원래 캡처된 순서와 일치하는 순서로 재생되도록 보장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-125">If this option is not selected, replay does not guarantee that events are replayed in an order that is consistent with the order in which events were originally captured.</span></span>  
  
 <span data-ttu-id="9afa9-126">**여러 스레드를 사용하여 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="9afa9-126">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="9afa9-127">성능을 최적화하고 디버깅할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-127">Optimizes performance and disables debugging.</span></span> <span data-ttu-id="9afa9-128">이벤트는 특정 서버 프로세스 ID(SPID)에 기록된 순서로 재생되지만 SPID의 순서는 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-128">Events are replayed in the order they were recorded for a particular server process ID (SPID), but ordering of SPIDs is not guaranteed.</span></span>  
  
 <span data-ttu-id="9afa9-129">**재생 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="9afa9-129">**Display replay results**</span></span>  
 <span data-ttu-id="9afa9-130">재생 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-130">Display the results of the replay.</span></span> <span data-ttu-id="9afa9-131">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-131">This is the default option.</span></span> <span data-ttu-id="9afa9-132">재생 중인 추적의 용량이 클 경우에는 이 옵션을 해제하여 디스크 공간을 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-132">If the trace you are replaying is very large, you may want to disable this to save disk space.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9afa9-133">최고의 재생 성능을 위해 여러 스레드를 사용하여 이벤트를 재생하고 재생 결과는 표시하지 않도록 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-133">For best replay performance, we recommend that you select to replay events using multiple threads, and do not select to display the replay results.</span></span>  
  
## <a name="advanced-replay-options"></a><span data-ttu-id="9afa9-134">고급 재생 옵션</span><span class="sxs-lookup"><span data-stu-id="9afa9-134">Advanced Replay Options</span></span>  
 <span data-ttu-id="9afa9-135">**시스템 SPID 재생**</span><span class="sxs-lookup"><span data-stu-id="9afa9-135">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="9afa9-136">모든 SPID를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-136">Replay all SPIDs.</span></span> <span data-ttu-id="9afa9-137">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-137">This is the default option.</span></span>  
  
 <span data-ttu-id="9afa9-138">**한 SPID만 재생**</span><span class="sxs-lookup"><span data-stu-id="9afa9-138">**Replay one SPID only**</span></span>  
 <span data-ttu-id="9afa9-139">목록에서 선택한 SPID 번호만 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-139">Replays the SPID number you choose from the list.</span></span>  
  
 <span data-ttu-id="9afa9-140">**날짜 및 시간별 재생 제한**</span><span class="sxs-lookup"><span data-stu-id="9afa9-140">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="9afa9-141">지정된 **시작 시간** 과 **종료 시간**에 대한 추적을 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-141">Replays the trace for the specified **Start time** and **End time**.</span></span>  
  
 <span data-ttu-id="9afa9-142">**상태 모니터 대기 간격**</span><span class="sxs-lookup"><span data-stu-id="9afa9-142">**Health monitor wait interval**</span></span>  
 <span data-ttu-id="9afa9-143">상태 모니터에서 프로세스를 종료하기 전에 프로세스가 실행될 수 있는 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-143">Sets the amount of time a process is allowed to run before the health monitor terminates it.</span></span>  
  
 <span data-ttu-id="9afa9-144">**상태 모니터 폴링 간격**</span><span class="sxs-lookup"><span data-stu-id="9afa9-144">**Health monitor poll interval**</span></span>  
 <span data-ttu-id="9afa9-145">상태 모니터에서 종료 후보에 대해 폴링하는 간격을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-145">Sets how often the health monitor polls candidates for termination.</span></span>  
  
 <span data-ttu-id="9afa9-146">**SQL Server 차단된 프로세스 모니터 설정**</span><span class="sxs-lookup"><span data-stu-id="9afa9-146">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="9afa9-147">차단된 프로세스 모니터에서 차단되었거나 차단 중인 프로세스를 검색하는 빈도를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-147">Sets how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="about-the-health-monitor"></a><span data-ttu-id="9afa9-148">상태 모니터 정보</span><span class="sxs-lookup"><span data-stu-id="9afa9-148">About the Health Monitor</span></span>  
 <span data-ttu-id="9afa9-149">상태 모니터는 추적 재생의 시뮬레이션된 프로세스를 모니터링하고 재생 내에서 차단된 프로세스를 종료하는 애플리케이션 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-149">The health monitor is an application thread that monitors the simulated processes involved in replaying a trace, and ends those processes that are blocked within the replay.</span></span> <span data-ttu-id="9afa9-150">**재생 구성** 대화 상자의 **고급 재생 옵션** 탭에서 차단된 프로세스를 끝내기 전에 상태 모니터가 대기해야 하는 시간(**상태 모니터 대기 간격**)을 초 단위로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-150">In the **Advanced Replay Options** tab of the **Replay Configuration** dialog box, you can specify how long the health monitor should wait in seconds before ending a blocked process (**Health monitor wait interval**).</span></span> <span data-ttu-id="9afa9-151">이 간격을 0으로 설정하면 상태 모니터가 재생 추적에서 시뮬레이션된 차단 프로세스를 종료하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9afa9-151">If you set this interval to 0, the health monitor never ends simulated blocking processes in the replaying trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9afa9-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9afa9-152">See Also</span></span>  
 <span data-ttu-id="9afa9-153">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="9afa9-153">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="9afa9-154">[재생 요구 사항](replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="9afa9-154">[Replay Requirements](replay-requirements.md) </span></span>  
 [<span data-ttu-id="9afa9-155">추적 재생에 대한 고려 사항&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="9afa9-155">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)  
  
  
