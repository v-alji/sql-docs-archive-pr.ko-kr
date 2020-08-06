---
title: 추적과 Windows 성능 로그 데이터의 상관 관계 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], logs
ms.assetid: e1b3072c-8daf-49a7-9895-c8cccd2adb95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 34575cf4270d817ecfbb5b2d1824831cc99454fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651259"
---
# <a name="correlate-a-trace-with-windows-performance-log-data-sql-server-profiler"></a><span data-ttu-id="3a99e-102">추적과 Windows 성능 로그 데이터의 상관 관계 지정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="3a99e-102">Correlate a Trace with Windows Performance Log Data (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]<span data-ttu-id="3a99e-103">Microsoft Windows 시스템 모니터 카운터와 또는 이벤트의 상관 관계를 지정할 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a99e-103">can correlate Microsoft Windows System Monitor counters with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] events.</span></span> <span data-ttu-id="3a99e-104">Windows 시스템 모니터는 지정한 카운터에 대한 시스템 작업을 성능 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-104">Windows System Monitor logs system activity for specified counters in performance logs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a99e-105">다른 버전의 Windows 간 로그 공유에 대한 자세한 내용은 이 항목의 마지막 부분에 있는 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3a99e-105">For information about sharing logs among different versions of Windows, see the procedure at the end of this topic.</span></span>  
  
### <a name="to-correlate-a-trace-with-performance-log-data"></a><span data-ttu-id="3a99e-106">추적과 성능 로그 데이터의 상관 관계를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="3a99e-106">To correlate a trace with performance log data</span></span>  
  
1.  <span data-ttu-id="3a99e-107">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에서 저장된 추적 파일 또는 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-107">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], open a saved trace file or trace table.</span></span> <span data-ttu-id="3a99e-108">계속 이벤트 데이터를 수집하고 있는 실행 중인 추적의 경우 상관 관계를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-108">You cannot correlate a running trace that is still collecting event data.</span></span> <span data-ttu-id="3a99e-109">시스템 모니터 데이터와의 정확한 상관 관계를 위해 추적이 **StartTime** 과 **EndTime** 데이터 열을 모두 포함하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-109">For accurate correlation with System Monitor data, the trace must contain both **StartTime** and **EndTime** data columns.</span></span>  
  
2.  <span data-ttu-id="3a99e-110">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **파일** 메뉴에서 **성능 데이터 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-110">On the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu, click **Import Performance Data**.</span></span>  
  
3.  <span data-ttu-id="3a99e-111">**열기** 대화 상자에서 성능 로그가 들어 있는 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-111">In the **Open** dialog box, select a file that contains a performance log.</span></span> <span data-ttu-id="3a99e-112">추적 데이터가 캡처되는 기간 동안 성능 로그 데이터 역시 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-112">The performance log data must have been captured during the same time period in which the trace data is captured.</span></span>  
  
4.  <span data-ttu-id="3a99e-113">**성능 카운터 제한** 대화 상자에서 추적과 함께 표시하려는 시스템 모니터 개체와 카운터에 해당하는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-113">In the **Performance Counters Limit** dialog box, select the check boxes that correspond to the System Monitor objects and counters that you want to display alongside the trace.</span></span> <span data-ttu-id="3a99e-114">**확인.**</span><span class="sxs-lookup"><span data-stu-id="3a99e-114">Click **OK.**</span></span>  
  
5.  <span data-ttu-id="3a99e-115">추적 이벤트 창에서 이벤트를 선택하거나 화살표 키를 사용하여 추적 이벤트 창의 인접 행으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-115">Select an event in the trace events window, or navigate through several adjacent rows in the trace events window by using the arrow keys.</span></span> <span data-ttu-id="3a99e-116">**시스템 모니터 데이터** 창의 빨강 세로 막대는 선택한 추적 이벤트와 상관 관계에 있는 성능 로그 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-116">The vertical red bar in the **System Monitor data** window indicates the performance log data that is correlated with the selected trace event.</span></span>  
  
6.  <span data-ttu-id="3a99e-117">시스템 모니터 그래프에서 자세히 보고 싶은 시점을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-117">Click a point of interest in the System Monitor graph.</span></span> <span data-ttu-id="3a99e-118">선택한 시간에 가장 가까운 해당 추적 행이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-118">The corresponding trace row that is nearest in time is selected.</span></span> <span data-ttu-id="3a99e-119">시간 범위를 확대하려면 시스템 모니터 그래프에서 마우스 포인터를 누른 다음 끌어서 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-119">To zoom in on a time range, press and drag the mouse pointer in the System Monitor graph.</span></span>  
  
### <a name="to-create-performance-logs-that-can-be-shared-among-different-versions-of-windows"></a><span data-ttu-id="3a99e-120">다른 버전의 Windows와 공유할 수 있는 성능 로그를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3a99e-120">To create performance logs that can be shared among different versions of Windows</span></span>  
  
1.  <span data-ttu-id="3a99e-121">제어판에서 **관리 도구**를 연 다음 **성능**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-121">In Control Panel, open **Administrative Tools**, and then double click **Performance**.</span></span>  
  
2.  <span data-ttu-id="3a99e-122">**성능** 대화 상자에서 **성능 로그 및 경고**를 확장하고 **카운터 로그**를 마우스 오른쪽 단추로 클릭한 다음 **새 로그 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-122">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span>  
  
3.  <span data-ttu-id="3a99e-123">카운터 로그의 이름을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-123">Type a name for the counter log, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3a99e-124">**일반** 탭에서 **카운터 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-124">On the **General** tab, click **Add Counters**.</span></span>  
  
5.  <span data-ttu-id="3a99e-125">**성능 개체** 목록에서 모니터링하려는 성능 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-125">In the **Performance object** list, select a performance object you want to monitor.</span></span> <span data-ttu-id="3a99e-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기본 인스턴스에 대한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 성능 개체의 이름은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 으로 시작하고 명명된 인스턴스는 MSSQL$*instanceName*으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-126">The names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] performance objects for default instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] start with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and named instances start with MSSQL$*instanceName*.</span></span>  
  
6.  <span data-ttu-id="3a99e-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 및 기타 중요한 값(예: 프로세서 시간, 디스크 시간)에 대해 필요한 만큼의 카운터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-127">Add as many counters as necessary for your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and other important values, such as processor time and disk time.</span></span>  
  
7.  <span data-ttu-id="3a99e-128">카운터 추가가 완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-128">When you have finished adding counters, click **Close**.</span></span>  
  
8.  <span data-ttu-id="3a99e-129">**데이터 샘플 간격** 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-129">Set values for the **Sample data every** interval.</span></span> <span data-ttu-id="3a99e-130">샘플링 간격은 가장 적절한 간격(예를 들어 5분)에서 시작하여 필요에 따라 간격을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-130">Start with a modest sampling interval, such as 5 minutes, and then adjust the interval if necessary.</span></span>  
  
9. <span data-ttu-id="3a99e-131">**로그 파일** 탭의 **로그 파일 종류** 목록에서 **텍스트 파일(쉼표 구분 형식)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-131">On the **Log Files** tab, choose **TextFile (Comma delimited)** from the **Log file type** list.</span></span> <span data-ttu-id="3a99e-132">쉼표로 구분된 텍스트 로그 파일은 다른 버전의 Windows와 공유할 수 있으며 나중에 Microsoft Excel과 같은 보고서 도구에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-132">Comma-delimited text log files can be shared among different versions of Windows and can be viewed later in reporting tools such as Microsoft Excel.</span></span>  
  
10. <span data-ttu-id="3a99e-133">**일정** 탭에서 모니터링 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-133">On the **Schedule** tab, specify a monitoring schedule.</span></span>  
  
11. <span data-ttu-id="3a99e-134">**확인** 을 클릭하여 성능 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a99e-134">Click **OK** to create the performance log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a99e-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a99e-135">See Also</span></span>  
 <span data-ttu-id="3a99e-136">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="3a99e-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="3a99e-137">SQL Server Profiler 시작</span><span class="sxs-lookup"><span data-stu-id="3a99e-137">Start SQL Server Profiler</span></span>](../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
