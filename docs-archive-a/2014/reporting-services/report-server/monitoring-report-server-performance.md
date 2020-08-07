---
title: 보고서 서버 성능 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Reporting Services]
- report servers [Reporting Services], performance
- counters [Reporting Services]
- monitoring performance [Reporting Services]
- SQL Server Reporting Services, performance
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: c1bc13d4-8297-4daf-bb19-4c1e5ba292a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 133dfae978faa4ae8f494cf4a03b282985fae695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727927"
---
# <a name="monitoring-report-server-performance"></a><span data-ttu-id="f4b04-102">보고서 서버 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="f4b04-102">Monitoring Report Server Performance</span></span>
  <span data-ttu-id="f4b04-103">성능 모니터링 도구를 통해 보고서 서버 성능을 모니터링하여 서버 작업을 평가하고, 추세를 살피고, 시스템 병목 현상을 진단하고, 현재 시스템 구성이 충분한지 여부를 결정하는 데 도움이 되는 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-103">Use performance monitoring tools to monitor report server performance to evaluate server activity, watch trends, diagnose system bottlenecks, and gather data that can help you determine whether the current system configuration is sufficient.</span></span> <span data-ttu-id="f4b04-104">서버 성능을 튜닝하기 위해 보고서 서버 애플리케이션 도메인의 재활용 빈도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-104">To tune server performance, you can specify how often to recycle the report server application domain.</span></span> <span data-ttu-id="f4b04-105">자세한 내용은 [보고서 서버 애플리케이션을 위한 사용 가능한 메모리 구성](../report-server/configure-available-memory-for-report-server-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4b04-105">For more information, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="sources-of-performance-data"></a><span data-ttu-id="f4b04-106">성능 데이터의 원본</span><span class="sxs-lookup"><span data-stu-id="f4b04-106">Sources of Performance Data</span></span>  
 <span data-ttu-id="f4b04-107">기술과 도구를 함께 사용하여 시스템 수행 방법에 대한 포괄적인 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-107">Use a combination of technologies and tools to get comprehensive information about how the system is performing.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f4b04-108">Windows Server 운영 체제는 다음 도구를 통해 성능 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-108">Windows Server operating systems provide performance information through the following tools:</span></span>  
  
-   <span data-ttu-id="f4b04-109">작업 관리자</span><span class="sxs-lookup"><span data-stu-id="f4b04-109">Task Manager</span></span>  
  
-   <span data-ttu-id="f4b04-110">이벤트 뷰어</span><span class="sxs-lookup"><span data-stu-id="f4b04-110">Event Viewer</span></span>  
  
-   <span data-ttu-id="f4b04-111">성능 콘솔</span><span class="sxs-lookup"><span data-stu-id="f4b04-111">Performance Console</span></span>  
  
 <span data-ttu-id="f4b04-112">작업 관리자는 컴퓨터에서 실행되는 프로그램 및 프로세스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-112">Task Manager provides information about programs and processes running on your computer.</span></span> <span data-ttu-id="f4b04-113">작업 관리자를 사용하여 보고서 서버의 성능을 나타내는 주요 표시기를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-113">You can use Task Manager to monitor key indicators of your report server's performance.</span></span> <span data-ttu-id="f4b04-114">또한 실행 중인 프로세스의 활동을 평가하고 CPU 및 메모리 사용량에 대한 그래프와 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-114">You can also assess the activity of running processes and view graphs and data on CPU and memory usage.</span></span> <span data-ttu-id="f4b04-115">작업 관리자를 사용하는 방법은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b04-115">For information about using Task Manager, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows product documentation.</span></span>  
  
 <span data-ttu-id="f4b04-116">성능 콘솔과 이벤트 뷰어를 사용하여 보고서 처리 및 리소스 소비량에 대한 로그와 경고를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-116">You can use Performance Console and Event Viewer to create logs and alerts about report processing and resource consumption.</span></span> <span data-ttu-id="f4b04-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 생성된 Windows 이벤트에 대한 자세한 내용은 [Windows 애플리케이션 로그](windows-application-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4b04-117">For information about Windows events that are generated by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Windows Application Log](windows-application-log.md).</span></span> <span data-ttu-id="f4b04-118">성능 콘솔에 대한 자세한 내용은 이 항목 뒷부분에서 "Windows 성능 카운터"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b04-118">For information about Performance Console, see "Windows Performance Counters" later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4b04-119">유틸리티는 캐싱 및 세션 관리에 사용되는 보고서 서버 데이터베이스 및 임시 데이터베이스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-119">utilities also provide information about the report server database and temporary databases used for caching and session management.</span></span>  
  
## <a name="windows-performance-counters"></a><span data-ttu-id="f4b04-120">Windows 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f4b04-120">Windows Performance Counters</span></span>  
 <span data-ttu-id="f4b04-121">특정 성능 카운터를 모니터링하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-121">Monitoring specific performance counters enables you to:</span></span>  
  
-   <span data-ttu-id="f4b04-122">예측 작업을 지원하는 데 필요한 시스템 요구 사항을 추정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-122">Estimate system requirements needed to support a predicted workload.</span></span>  
  
-   <span data-ttu-id="f4b04-123">구성 변경 또는 애플리케이션 업그레이드의 영향을 측정하기 위한 성능 기준을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-123">Create a performance baseline to measure effect of configuration changes or application upgrades.</span></span>  
  
-   <span data-ttu-id="f4b04-124">실제 또는 인위적으로 생성된 특정 로드 하의 애플리케이션 성능을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-124">Monitor application performance under certain loads, whether real or artificially generated.</span></span>  
  
-   <span data-ttu-id="f4b04-125">하드웨어 업그레이드를 통해 원하는 성능 효과를 얻었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-125">Verify that hardware upgrades have the desired effect on performance.</span></span>  
  
-   <span data-ttu-id="f4b04-126">시스템 구성 변경을 통해 원하는 성능 효과를 얻었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-126">Validate changes that were made to the system configuration have the desired effect on performance.</span></span>  
  
## <a name="reporting-services-performance-objects"></a><span data-ttu-id="f4b04-127">Reporting Services 성능 개체</span><span class="sxs-lookup"><span data-stu-id="f4b04-127">Reporting Services Performance Objects</span></span>  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="f4b04-128">에는 다음과 같은 성능 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-128">includes the following performance objects:</span></span>  
  
-   <span data-ttu-id="f4b04-129">**MSRS 2011 웹 서비스** 및 `MSRS 2011 SharePoint Mode Web Service` 보고서 서버 성능을 모니터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-129">**MSRS 2011 Web Service** and `MSRS 2011 SharePoint Mode Web Service` to monitor report server performance.</span></span> <span data-ttu-id="f4b04-130">이러한 성능 개체에는 일반적으로 대화형 보고서 보기 작업을 통해 시작된 보고서 서버 처리를 추적하는 데 사용되는 카운터 모음이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-130">These performance objects include a collection of counters used to track report server processing typically initiated through interactive report viewing operations.</span></span> <span data-ttu-id="f4b04-131">이러한 카운터는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 이 보고서 서버 웹 서비스를 중지할 때마다 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-131">These counters are reset whenever [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] stops the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="f4b04-132">예약된 작업 및 보고서 배달을 모니터링하기 위한 `MSRS 2011 Windows Service` 및 `MSRS 2011 Windows Service SharePoint Mode`.</span><span class="sxs-lookup"><span data-stu-id="f4b04-132">`MSRS 2011 Windows Service` and `MSRS 2011 Windows Service SharePoint Mode` to monitor scheduled operations and report delivery.</span></span> <span data-ttu-id="f4b04-133">이러한 성능 개체에는 예약된 작업을 통해 시작된 보고서 처리를 추적하는 데 사용되는 카운터 모음이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-133">These performance objects include a collection of counters used to track report processing that is initiated through scheduled operations.</span></span> <span data-ttu-id="f4b04-134">예약된 작업에는 구독 및 배달, 보고서 실행 스냅샷 및 보고서 기록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-134">Scheduled operations include subscription and delivery, report execution snapshots, and report history.</span></span>  
  
-   <span data-ttu-id="f4b04-135">HTTP 관련 이벤트 및 메모리 관리를 모니터링하기 위한 `ReportServer:Service` 및 `ReportServerSharePoint:Service`.</span><span class="sxs-lookup"><span data-stu-id="f4b04-135">`ReportServer:Service` and `ReportServerSharePoint:Service` to monitor HTTP-related events and memory management.</span></span> <span data-ttu-id="f4b04-136">이러한 카운터는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 한정되며 요청, 연결 및 로그온 시도와 같은 보고서 서버에 대한 HTTP 관련 이벤트를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-136">These counters are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and they track HTTP-related events for the report server, such as requests, connections, and logon attempts.</span></span> <span data-ttu-id="f4b04-137">이 성능 개체에는 메모리 관리 관련 카운터도 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-137">This performance object also includes counters related to memory management.</span></span>  
  
 <span data-ttu-id="f4b04-138">한 시스템에 보고서 서버 인스턴스가 여러 개 있을 경우 인스턴스를 함께 모니터링하거나 별도로 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-138">If you have multiple report server instances on a single computer, you can monitor the instances together or separately.</span></span> <span data-ttu-id="f4b04-139">카운터 추가 시 포함할 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-139">Choose which instances to include when you add a counter.</span></span> <span data-ttu-id="f4b04-140">성능 콘솔(perfmon.msc) 사용 및 카운터를 추가하는 방법은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 제품 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4b04-140">For more information about using Performance Console (perfmon.msc) and adding counters, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows product documentation.</span></span>  
  
## <a name="other-performance-counters"></a><span data-ttu-id="f4b04-141">기타 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f4b04-141">Other Performance Counters</span></span>  
 <span data-ttu-id="f4b04-142">사용자 지정 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 성능 카운터는 `MSRS 2008 Web Service`, `MSRS 2008 Windows Service` 및 `ReportServer:Service`에 대해서만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-142">Custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] performance counters are provided only for `MSRS 2008 Web Service`, `MSRS 2008 Windows Service`, and `ReportServer:Service`.</span></span> <span data-ttu-id="f4b04-143">다음 성능 개체는 보고서 서버에 대한 추가 성능 모니터링 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-143">The following performance objects provide additional performance monitoring data for the report server.</span></span>  
  
|<span data-ttu-id="f4b04-144">성능 개체</span><span class="sxs-lookup"><span data-stu-id="f4b04-144">Performance object</span></span>|<span data-ttu-id="f4b04-145">메모</span><span class="sxs-lookup"><span data-stu-id="f4b04-145">Notes</span></span>|  
|------------------------|-----------|  
|<span data-ttu-id="f4b04-146">`.NET CLR Data` 및 `.NET CLR Memory`</span><span class="sxs-lookup"><span data-stu-id="f4b04-146">`.NET CLR Data` and `.NET CLR Memory`</span></span>|<span data-ttu-id="f4b04-147">보고서 관리자는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 성능 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-147">Report Manager uses [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] performance counters.</span></span> <span data-ttu-id="f4b04-148">자세한 내용은 MSDN에서 "Improving .NET Application Performance and Scalability"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f4b04-148">For more information, see "Improving .NET Application Performance and Scalability" on MSDN.</span></span>|  
|`Process`|<span data-ttu-id="f4b04-149">ReportingServicesService 인스턴스에 대한 `Elapsed Time` 및 `ID Process` 성능 카운터를 추가하여 프로세스 ID별로 프로세스 작동 시간을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-149">Add the `Elapsed Time` and `ID Process` performance counters for a ReportingServicesService instance to track process uptime by process ID.</span></span>|  
  
## <a name="sharepoint-events"></a><span data-ttu-id="f4b04-150">SharePoint 이벤트</span><span class="sxs-lookup"><span data-stu-id="f4b04-150">SharePoint Events</span></span>  
 <span data-ttu-id="f4b04-151">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 성능 개체 이외에도 SharePoint 통합 모드로 보고서 서버를 실행하고 SharePoint 제품을 사용하도록 보고 환경을 구성한 경우 SharePoint 이벤트를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-151">In addition to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] performance objects, you might also want to configure SharePoint events if you are running a report server in SharePoint integrated mode and have configured your reporting environment to use a SharePoint product.</span></span> <span data-ttu-id="f4b04-152">이 섹션에서는 SharePoint 통합 모드의 보고서 서버 이벤트를 사용하여 보고 환경이 SharePoint와 통합되는 경우에 유용한 정보를 제공할 수 있는 진단 이벤트를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-152">In this section, use the Events for a Report Server in SharePoint Integrated Mode to review diagnostic events that might provide useful information if your reporting environment is integrated with SharePoint.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4b04-153">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f4b04-153">In This Section</span></span>  
 [<span data-ttu-id="f4b04-154">MSRS 2014 웹 서비스 및 MSRS 2014 Windows 서비스 성능 개체에 대 한 성능 카운터는 기본 모드 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f4b04-154">Performance Counters for the MSRS 2014 Web Service and MSRS 2014 Windows Service Performance Objects &#40;Native Mode&#41;</span></span>](performance-counters-msrs-2011-web-service-performance-objects.md)  
 <span data-ttu-id="f4b04-155">보고서 서버 웹 서비스에 사용된 성능 카운터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-155">Describes the performance counters used by the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="f4b04-156">SharePoint 모드 &#40;MSRS 2014 웹 서비스 SharePoint 모드 및 MSRS 2014 Windows 서비스 SharePoint 모드 성능 개체에 대 한 성능 카운터&#41;</span><span class="sxs-lookup"><span data-stu-id="f4b04-156">Performance Counters for the MSRS 2014 Web Service SharePoint Mode and MSRS 2014 Windows Service SharePoint Mode Performance Objects &#40;SharePoint Mode&#41;</span></span>](performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
 <span data-ttu-id="f4b04-157">보고서 서버 Windows 서비스에 사용된 성능 카운터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-157">Describes the performance counters used by the Report Server Windows service.</span></span>  
  
 [<span data-ttu-id="f4b04-158">ReportServer:Service 및 ReportServerSharePoint:Service 성능 개체에 대한 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f4b04-158">Performance Counters for the ReportServer:Service  and ReportServerSharePoint:Service Performance Objects</span></span>](performance-counters-reportserver-service-performance-objects.md)  
 <span data-ttu-id="f4b04-159">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 HTTP 관련 성능 카운터 및 메모리 관련 성능 카운터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-159">Describes the HTTP-related and memory-related performance counters in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f4b04-160">SharePoint 통합 모드의 보고서 서버 이벤트</span><span class="sxs-lookup"><span data-stu-id="f4b04-160">Events for a Report Server in SharePoint Integrated Mode</span></span>  
 <span data-ttu-id="f4b04-161">SharePoint 제품을 사용하여 보고 환경을 실행할 때 기록할 유용한 진단 이벤트를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f4b04-161">Describes the useful diagnostic events to log when you run a reporting environment with a SharePoint product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b04-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4b04-162">See Also</span></span>  
 <span data-ttu-id="f4b04-163">[보고서 서버 애플리케이션을 위한 사용 가능한 메모리 구성](../report-server/configure-available-memory-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f4b04-163">[Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md) </span></span>  
 <span data-ttu-id="f4b04-164">[Reporting Services 보고서 서버&#40;기본 모드&#41;](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f4b04-164">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 [<span data-ttu-id="f4b04-165">Reporting Services 도구</span><span class="sxs-lookup"><span data-stu-id="f4b04-165">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
