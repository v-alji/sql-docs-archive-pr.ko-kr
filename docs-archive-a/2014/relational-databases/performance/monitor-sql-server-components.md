---
title: SQL Server 구성 요소 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e8f1b16b-ea40-4e12-886c-967ebda4e6e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: baefe9aa1848bc3347a9a5a87c2ab81c382a6717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649016"
---
# <a name="monitor-sql-server-components"></a><span data-ttu-id="a1ff0-102">SQL Server 구성 요소 모니터링</span><span class="sxs-lookup"><span data-stu-id="a1ff0-102">Monitor SQL Server Components</span></span>
  <span data-ttu-id="a1ff0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 동적 환경에서 서비스를 제공하기 때문에 모니터링이 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-103">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="a1ff0-104">애플리케이션에 있는 데이터가 바뀌고,</span><span class="sxs-lookup"><span data-stu-id="a1ff0-104">The data in the application changes.</span></span> <span data-ttu-id="a1ff0-105">사용자가 필요로 하는 액세스 유형이 바뀌고,</span><span class="sxs-lookup"><span data-stu-id="a1ff0-105">The type of access that users require changes.</span></span> <span data-ttu-id="a1ff0-106">사용자가 연결하는 방법이 바뀔 뿐 아니라,</span><span class="sxs-lookup"><span data-stu-id="a1ff0-106">The way that users connect changes.</span></span> <span data-ttu-id="a1ff0-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 액세스하는 애플리케이션의 유형도 바뀔 수 있으나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 메모리나 디스크 공간 같은 시스템 수준의 리소스를 자동으로 관리하므로 시스템 수준의 상세한 수동 튜닝의 필요성은 최소한으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-107">The types of applications accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may even change, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically manages system-level resources, such as memory and disk space, to minimize the need for extensive system-level manual tuning.</span></span> <span data-ttu-id="a1ff0-108">모니터링을 통해 관리자는 성능 추세를 확인하여 변경이 필요한지 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-108">Monitoring lets administrators identify performance trends to determine if changes are necessary.</span></span>  
  
 <span data-ttu-id="a1ff0-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 구성 요소를 효과적으로 모니터링하려면</span><span class="sxs-lookup"><span data-stu-id="a1ff0-109">To monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively:</span></span>  
  
1.  <span data-ttu-id="a1ff0-110">모니터링 목표를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-110">Determine your monitoring goals.</span></span>  
  
2.  <span data-ttu-id="a1ff0-111">적절한 도구를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-111">Select the appropriate tool.</span></span>  
  
3.  <span data-ttu-id="a1ff0-112">모니터링할 구성 요소를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-112">Identify components to monitor.</span></span>  
  
4.  <span data-ttu-id="a1ff0-113">모니터링되는 구성 요소의 메트릭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-113">Select metrics for those components.</span></span>  
  
5.  <span data-ttu-id="a1ff0-114">서버를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-114">Monitor the server.</span></span>  
  
6.  <span data-ttu-id="a1ff0-115">데이터를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-115">Analyze the data.</span></span>  
  
 <span data-ttu-id="a1ff0-116">이러한 각 단계에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-116">These steps are discussed in turn below.</span></span>  
  
## <a name="determine-your-monitoring-goals"></a><span data-ttu-id="a1ff0-117">모니터링 목표 결정</span><span class="sxs-lookup"><span data-stu-id="a1ff0-117">Determine Your Monitoring Goals</span></span>  
 <span data-ttu-id="a1ff0-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 효과적으로 모니터링하려면 모니터링하는 이유를 분명하게 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-118">To monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively you should clearly identify your reason for monitoring.</span></span> <span data-ttu-id="a1ff0-119">다음과 같은 이유가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-119">Reasons can include the following:</span></span>  
  
-   <span data-ttu-id="a1ff0-120">성능에 대한 기준선을 마련합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-120">Establish a baseline for performance.</span></span>  
  
-   <span data-ttu-id="a1ff0-121">시간에 따라 성능이 어떻게 변하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-121">Identify performance changes over time.</span></span>  
  
-   <span data-ttu-id="a1ff0-122">특정 성능 문제를 진단합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-122">Diagnose specific performance problems.</span></span>  
  
-   <span data-ttu-id="a1ff0-123">최적화할 구성 요소나 프로세스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-123">Identify components or processes to optimize.</span></span>  
  
-   <span data-ttu-id="a1ff0-124">여러 클라이언트 애플리케이션의 성능에 대한 영향을 비교해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-124">Compare the effect of different client applications on performance.</span></span>  
  
-   <span data-ttu-id="a1ff0-125">사용자 작업을 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-125">Audit user activity.</span></span>  
  
-   <span data-ttu-id="a1ff0-126">서로 다른 부하 상태에서 서버를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-126">Test a server under different loads.</span></span>  
  
-   <span data-ttu-id="a1ff0-127">데이터베이스 아키텍처를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-127">Test database architecture.</span></span>  
  
-   <span data-ttu-id="a1ff0-128">유지 관리 일정을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-128">Test maintenance schedules.</span></span>  
  
-   <span data-ttu-id="a1ff0-129">백업 및 복원 계획을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-129">Test backup and restore plans.</span></span>  
  
-   <span data-ttu-id="a1ff0-130">하드웨어 구성을 수정할 시점을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-130">Determining when to modify your hardware configuration.</span></span>  
  
## <a name="select-the-appropriate-tool"></a><span data-ttu-id="a1ff0-131">적절한 도구 선택</span><span class="sxs-lookup"><span data-stu-id="a1ff0-131">Select the Appropriate Tool</span></span>  
 <span data-ttu-id="a1ff0-132">모니터링 이유를 결정했으면 해당 모니터링 유형에 적절한 도구를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-132">After determining why you are monitoring, you should select the appropriate tools for that type of monitoring.</span></span> <span data-ttu-id="a1ff0-133">Windows 운영 체제와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 트랜잭션이 많은 환경에서 서버를 모니터링할 수 있는 완전한 도구 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-133">The Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provide a complete set of tools to monitor servers in transaction-intensive environments.</span></span> <span data-ttu-id="a1ff0-134">이러한 도구를 통해 SQL Server 데이터베이스 엔진의 인스턴스나 SQL Server Analysis Services 인스턴스의 상태를 분명하게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-134">These tools clearly reveal the condition of an instance of the SQL Server Database Engine or an instance of SQL Server Analysis Services.</span></span>  
  
 <span data-ttu-id="a1ff0-135">Windows에서는 서버에서 실행되는 애플리케이션을 모니터링할 수 있는 다음과 같은 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-135">Windows provides the following tools for monitoring applications that are running on a server:</span></span>  
  
-   <span data-ttu-id="a1ff0-136">시스템 모니터. 이 도구를 사용하면 메모리, 디스크 및 프로세서 사용 등 작업에 대한 실시간 데이터를 수집하고 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-136">System Monitor, which lets you collect and view real-time data about activities such as memory, disk, and processor usage</span></span>  
  
-   <span data-ttu-id="a1ff0-137">성능 로그 및 경고</span><span class="sxs-lookup"><span data-stu-id="a1ff0-137">Performance logs and alerts</span></span>  
  
-   <span data-ttu-id="a1ff0-138">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="a1ff0-138">Task Manager</span></span>  
  
 <span data-ttu-id="a1ff0-139">Windows Server 또는 Windows 도구에 대한 자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-139">For more information about Windows Server or Windows tools, see the Windows documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a1ff0-140">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 구성 요소를 모니터링할 수 있는 다음과 같은 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-140">provides the following tools for monitoring components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="a1ff0-141">SQL 추적</span><span class="sxs-lookup"><span data-stu-id="a1ff0-141">SQL Trace</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="a1ff0-142">Distributed Replay Utility</span><span class="sxs-lookup"><span data-stu-id="a1ff0-142">Distributed Replay Utility</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a1ff0-143">작업 모니터</span><span class="sxs-lookup"><span data-stu-id="a1ff0-143">Activity Monitor</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a1ff0-144">그래픽 실행 계획</span><span class="sxs-lookup"><span data-stu-id="a1ff0-144">Graphical Showplan</span></span>  
  
-   <span data-ttu-id="a1ff0-145">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="a1ff0-145">Stored procedures</span></span>  
  
-   <span data-ttu-id="a1ff0-146">DBCC(데이터베이스 콘솔 명령)</span><span class="sxs-lookup"><span data-stu-id="a1ff0-146">Database Console Commands (DBCC)</span></span>  
  
-   <span data-ttu-id="a1ff0-147">기본 제공 함수</span><span class="sxs-lookup"><span data-stu-id="a1ff0-147">Built-in functions</span></span>  
  
-   <span data-ttu-id="a1ff0-148">추적 플래그</span><span class="sxs-lookup"><span data-stu-id="a1ff0-148">Trace flags</span></span>  
  
 <span data-ttu-id="a1ff0-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 모니터링 도구에 대한 자세한 내용은 [성능 모니터링 및 튜닝 도구](performance-monitoring-and-tuning-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-149">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring tools, see [Performance Monitoring and Tuning Tools](performance-monitoring-and-tuning-tools.md).</span></span>  
  
## <a name="identify-the-components-to-monitor"></a><span data-ttu-id="a1ff0-150">모니터링할 구성 요소 식별</span><span class="sxs-lookup"><span data-stu-id="a1ff0-150">Identify the Components to Monitor</span></span>  
 <span data-ttu-id="a1ff0-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 모니터링하기 위한 세 번째 단계는 모니터링할 구성 요소를 식별하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-151">The third step to monitoring an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is to identify the components that you monitor.</span></span> <span data-ttu-id="a1ff0-152">예를 들어 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 서버를 추적할 경우 추적을 정의하여 특정 이벤트에 대한 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-152">For example, if you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to trace a server you can define the trace to collect data about specific events.</span></span> <span data-ttu-id="a1ff0-153">해당 상황에 적용되지 않는 이벤트는 제외할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-153">You can also exclude events that do not apply to your situation.</span></span>  
  
## <a name="select-metrics-for-monitored-components"></a><span data-ttu-id="a1ff0-154">모니터링되는 구성 요소의 메트릭 선택</span><span class="sxs-lookup"><span data-stu-id="a1ff0-154">Select Metrics for Monitored Components</span></span>  
 <span data-ttu-id="a1ff0-155">모니터링할 구성 요소를 식별했으면 모니터링할 구성 요소의 메트릭을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-155">After identifying the components to monitor, determine the metrics for components you monitor.</span></span> <span data-ttu-id="a1ff0-156">예를 들어 추적에 포함할 이벤트를 선택한 후 이벤트에 대한 특정 데이터만 포함하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-156">For example, after selecting the events to include in a trace, you can choose to include only specific data about the events.</span></span> <span data-ttu-id="a1ff0-157">추적에 관련된 데이터로 추적을 제한하면 추적하는 데 필요한 시스템 리소스를 최소한으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-157">Limiting the trace to data that is relevant to the trace minimizes the system resources required to perform the tracing.</span></span>  
  
## <a name="monitor-the-server"></a><span data-ttu-id="a1ff0-158">서버 모니터링</span><span class="sxs-lookup"><span data-stu-id="a1ff0-158">Monitor the Server</span></span>  
 <span data-ttu-id="a1ff0-159">서버를 모니터링하려면 구성한 모니터링 도구를 실행하여 데이터를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-159">To monitor the server, run the monitoring tool that you have configured to gather data.</span></span> <span data-ttu-id="a1ff0-160">예를 들어 추적을 정의한 후에 추적을 실행하여 서버에서 발생한 이벤트에 대한 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-160">For example, after a trace is defined, you can run the trace to gather data about events raised in the server.</span></span>  
  
## <a name="analyze-the-data"></a><span data-ttu-id="a1ff0-161">데이터 분석</span><span class="sxs-lookup"><span data-stu-id="a1ff0-161">Analyze the Data</span></span>  
 <span data-ttu-id="a1ff0-162">추적을 마친 후에 데이터를 분석하여 모니터링 목표가 이루어졌는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-162">After the trace has finished, analyze the data to see if you have achieved your monitoring goal.</span></span> <span data-ttu-id="a1ff0-163">목표가 이루어지지 않았으면 서버를 모니터링하는 데 사용한 구성 요소나 메트릭을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-163">If you have not, modify the components or metrics that you used to monitor the server.</span></span>  
  
 <span data-ttu-id="a1ff0-164">다음은 이벤트 데이터를 캡처하고 사용하는 데 관련된 프로세스를 요약하여 설명한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-164">The following outlines the process for capturing event data and putting it to use.</span></span>  
  
1.  <span data-ttu-id="a1ff0-165">필터를 적용하여 수집한 이벤트 데이터를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-165">Apply filters to limit the event data collected.</span></span>  
  
     <span data-ttu-id="a1ff0-166">이벤트 데이터를 제한하면 모니터링 시나리오에 맞는 특정 이벤트에 시스템의 포커스를 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-166">Limiting the event data allows for the system to focus on the events pertinent to the monitoring scenario.</span></span> <span data-ttu-id="a1ff0-167">예를 들어 처리 속도가 느린 쿼리를 모니터링할 때는 애플리케이션에서 실행한 쿼리가 특정 데이터베이스에 대해 실행되는 데 30초 이상 걸리는 경우만 모니터링하는 필터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-167">For example, if you want to monitor slow queries, you can use a filter to monitor only those queries issued by the application that take more than 30 seconds to run against a particular database.</span></span> <span data-ttu-id="a1ff0-168">자세한 내용은 [추적 필터 설정&#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) 및 [추적에서의 이벤트 필터링&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-168">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) and [Filter Events in a Trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="a1ff0-169">이벤트를 모니터링(캡처)합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-169">Monitor (capture) events.</span></span>  
  
     <span data-ttu-id="a1ff0-170">모니터링을 설정하면 활성 모니터링은 지정한 애플리케이션, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 또는 운영 체제에서 데이터를 즉시 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-170">As soon as it is enabled, active monitoring captures data from the specified application, instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or operating system.</span></span> <span data-ttu-id="a1ff0-171">예를 들어 시스템 모니터를 사용하여 디스크 작업을 모니터링하면 디스크 읽기 및 쓰기 같은 이벤트 데이터가 캡처되고 해당 데이터가 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-171">For example, when disk activity is monitored using System Monitor, monitoring captures event data, such as disk reads and writes, and displays it on the screen.</span></span> <span data-ttu-id="a1ff0-172">자세한 내용은 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-172">For more information, see [Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md).</span></span>  
  
3.  <span data-ttu-id="a1ff0-173">캡처한 이벤트 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-173">Save captured event data.</span></span>  
  
     <span data-ttu-id="a1ff0-174">캡처한 이벤트 데이터를 저장하면 나중에 분석하거나 Distributed Replay Utility 또는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-174">Saving captured event data lets you analyze it later or even replay it using the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="a1ff0-175">캡처한 이벤트 데이터는 원래 분석용으로 만든 도구로 다시 로드할 수 있는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-175">Captured event data is saved to a file that can be loaded back into the tool that originally created it for analysis.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a1ff0-176">는 이벤트 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-176">permits event data to be saved to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="a1ff0-177">캡처한 이벤트 데이터를 저장하는 것은 성능 기준선을 만들 때 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-177">Saving captured event data is important when you are creating a performance baseline.</span></span> <span data-ttu-id="a1ff0-178">성능 기준선 데이터를 저장하면 최근 캡처한 이벤트 데이터와 비교하여 성능이 최적인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-178">The performance baseline data is saved and used, when comparing recently captured event data, to determine whether performance is optimal.</span></span> <span data-ttu-id="a1ff0-179">자세한 내용은 [SQL Server Profiler 템플릿 및 권한](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-179">For more information, see [SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md).</span></span>  
  
4.  <span data-ttu-id="a1ff0-180">이벤트를 캡처하도록 설정이 지정된 추적 템플릿을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-180">Create trace templates that contain the settings specified to capture the events.</span></span>  
  
     <span data-ttu-id="a1ff0-181">추적 템플릿에는 이벤트 자체, 이벤트 데이터 및 데이터를 캡처하는 데 사용하는 필터에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-181">Trace templates include specifications about the events themselves, event data, and filters that are used to capture data.</span></span> <span data-ttu-id="a1ff0-182">이 템플릿을 사용하면 나중에 특정 이벤트 집합을 모니터링할 때 이벤트, 이벤트 데이터 및 필터를 다시 정의할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-182">These templates can be used to monitor a specific set of events later without redefining the events, event data, and filters.</span></span> <span data-ttu-id="a1ff0-183">예를 들어 교착 상태 수와 교착 상태에 있는 사용자 수를 모니터링할 경우 해당 이벤트, 이벤트 데이터 및 이벤트 필터를 정의하는 템플릿을 만들어 저장해 두면 다음에 교착 상태를 모니터링할 때 해당 필터를 다시 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-183">For example, if you want to frequently monitor the number of deadlocks, and the users involved in those deadlocks, you can create a template defining those events, event data, and event filters; save the template; and reapply the filter the next time that you want to monitor deadlocks.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a1ff0-184">는 추적 템플릿을 이 용도로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-184">uses trace templates for this purpose.</span></span> <span data-ttu-id="a1ff0-185">자세한 내용은 [추적 정의 기본값 설정&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) 및 [추적 템플릿 만들기&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-185">For more information, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) and [Create a Trace Template &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md).</span></span>  
  
5.  <span data-ttu-id="a1ff0-186">캡처한 이벤트 데이터를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-186">Analyze captured event data.</span></span>  
  
     <span data-ttu-id="a1ff0-187">데이터 분석을 위해 캡처한 이벤트 데이터가 해당 데이터를 캡처한 애플리케이션으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-187">To be analyzed, the captured event data is loaded into the application that captured the data.</span></span> <span data-ttu-id="a1ff0-188">예를 들어 확인 및 분석을 위해 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서 캡처한 추적을 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 로 다시 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-188">For example, a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can be reloaded into [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] for viewing and analysis.</span></span> <span data-ttu-id="a1ff0-189">자세한 내용은 [SQL Server Profiler를 사용하여 추적 보기 및 분석](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-189">For more information, see [View and Analyze Traces with SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="a1ff0-190">이벤트 데이터를 분석하면 발생한 이벤트와 발생 원인을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-190">Analyzing event data involves determining what is occurring and why.</span></span> <span data-ttu-id="a1ff0-191">이 정보를 사용하면 수행된 분석 유형에 따라 메모리를 추가하거나 인덱스를 변경하거나 Transact-SQL 문 또는 저장 프로시저의 코딩 문제를 수정하는 등 성능 향상에 필요한 사항을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-191">This information lets you make changes that can improve performance, such as adding more memory, changing indexes, correcting coding problems with Transact-SQL statements or stored procedures, and so on, depending on the type of analysis performed.</span></span> <span data-ttu-id="a1ff0-192">예를 들어 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자를 사용하여 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서 캡처한 추적을 분석하고 결과에 따라 인덱스 권장 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-192">For example, you can use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor to analyze a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and make index recommendations based on the results.</span></span>  
  
6.  <span data-ttu-id="a1ff0-193">캡처한 이벤트 데이터를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-193">Replay captured event data.</span></span>  
  
     <span data-ttu-id="a1ff0-194">이벤트 재생을 사용하면 데이터를 캡처한 데이터베이스 환경의 테스트 복사본을 만들고 캡처한 이벤트를 실제 시스템에서 원래 발생했던 대로 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-194">Event replay lets you establish a test copy of the database environment from which the data was captured, and then repeat the captured events as they occurred originally on the real system.</span></span> <span data-ttu-id="a1ff0-195">이 기능은 Distributed Replay Utility나 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-195">This capability is only available with the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="a1ff0-196">이벤트 재생 속도는 이벤트가 원래 발생한 속도와 같게 하거나 최대한 빠르게 하거나 한 번에 한 단계씩 재생하여 각 이벤트가 발생한 후 시스템을 분석할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-196">You can replay the events at the same speed as they originally occurred, as fast as possible (to stress the system), or more likely, one step at a time (to analyze the system after each event has occurred).</span></span> <span data-ttu-id="a1ff0-197">같은 이벤트를 테스트 환경에서 분석하여 프로덕션 시스템에 발생할 수 있는 해로운 상황을 미리 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-197">By analyzing the exact events in a test environment, you can prevent harm to the production system.</span></span> <span data-ttu-id="a1ff0-198">자세한 내용은 [추적 재생](../../tools/sql-server-profiler/replay-traces.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ff0-198">For more information, see [Replay Traces](../../tools/sql-server-profiler/replay-traces.md).</span></span>  
  
  
