---
title: 차트, 경고, 로그 및 보고서 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], charts and reports
- charts [SQL Server]
- reports [SQL Server]
- reports [SQL Server], creating
- Windows System Monitor [SQL Server], charts and reports
- logs [SQL Server], System Monitor
- System Monitor [SQL Server], logs
- Windows System Monitor [SQL Server], logs
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a0c95c3f483a8af3e3e68d9c5c7d3caf44350d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739753"
---
# <a name="create-charts-alerts-logs-and-reports"></a><span data-ttu-id="3e7f7-102">차트, 경고, 로그 및 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="3e7f7-102">Create Charts, Alerts, Logs, and Reports</span></span>
  <span data-ttu-id="3e7f7-103">시스템 모니터를 사용하면 차트, 경고, 로그 및 보고서를 만들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-103">System Monitor lets you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="charts"></a><span data-ttu-id="3e7f7-104">차트</span><span class="sxs-lookup"><span data-stu-id="3e7f7-104">Charts</span></span>  
 <span data-ttu-id="3e7f7-105">차트를 사용하면 선택된 개체 및 카운터의 현재 성능(CPU 사용량 또는 디스크 I/O)을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-105">Charts can monitor the current performance of selected objects and counters; for example, the CPU usage or disk I/O.</span></span> <span data-ttu-id="3e7f7-106">차트에 여러 가지 시스템 모니터 개체 및 카운터 조합을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-106">You can add to a chart various combinations of System Monitor objects and counters.</span></span> <span data-ttu-id="3e7f7-107">또한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 개체 및 카운터도 차트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-107">You also can add [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows objects and counters to a chart.</span></span>  
  
 <span data-ttu-id="3e7f7-108">각 차트는 모니터링하려는 정보의 하위 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-108">Each chart represents a subset of information you want to monitor.</span></span> <span data-ttu-id="3e7f7-109">예를 들어 어떤 차트는 메모리 사용량 통계를, 다른 차트는 디스크 I/O 통계를 추적하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-109">For example, one chart can track memory usage statistics and a second chart can track disk I/O statistics.</span></span>  
  
 <span data-ttu-id="3e7f7-110">차트 사용은 다음 태스크에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-110">Using a chart can be useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="3e7f7-111">컴퓨터 혹은 애플리케이션의 속도가 느려지는 원인 조사</span><span class="sxs-lookup"><span data-stu-id="3e7f7-111">Investigating why a computer or application is slow or inefficient.</span></span>  
  
-   <span data-ttu-id="3e7f7-112">작동이 중단되는 성능 문제를 찾아내기 위해 시스템을 지속적으로 모니터링</span><span class="sxs-lookup"><span data-stu-id="3e7f7-112">Continually monitoring systems to find intermittent performance problems.</span></span>  
  
-   <span data-ttu-id="3e7f7-113">용량을 늘려야 하는 이유 확인</span><span class="sxs-lookup"><span data-stu-id="3e7f7-113">Discovering why you need to increase capacity.</span></span>  
  
-   <span data-ttu-id="3e7f7-114">선형 차트로 추세 표시</span><span class="sxs-lookup"><span data-stu-id="3e7f7-114">Displaying a trend as a line chart.</span></span>  
  
-   <span data-ttu-id="3e7f7-115">히스토그램 차트로 비교 표시</span><span class="sxs-lookup"><span data-stu-id="3e7f7-115">Displaying a comparison as a histogram chart.</span></span>  
  
 <span data-ttu-id="3e7f7-116">차트는 이벤트가 발생할 때 모니터링하는 것과 같이 로컬 또는 원격 컴퓨터를 단기에 걸쳐 실시간으로 모니터링할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-116">Charts are useful for short-term, real-time monitoring of a local or remote computer (for example, when you want to monitor an event as it occurs).</span></span>  
  
## <a name="alerts"></a><span data-ttu-id="3e7f7-117">경고</span><span class="sxs-lookup"><span data-stu-id="3e7f7-117">Alerts</span></span>  
 <span data-ttu-id="3e7f7-118">경고를 사용하면 시스템 모니터는 특정 이벤트를 추적해 이 이벤트에 대해 사용자가 요청한 대로 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-118">Using alerts, System Monitor tracks specific events and notifies you of these events as requested.</span></span> <span data-ttu-id="3e7f7-119">경고 로그를 사용하면 선택된 카운터의 현재 성능 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]개체의 인스턴스를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-119">An alert log can monitor the current performance of selected counters and instances for objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3e7f7-120">카운터가 지정된 값을 넘어 가면 로그에 이벤트가 발생한 날짜와 시간이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-120">When a counter exceeds a given value, the log records the date and time of the event.</span></span> <span data-ttu-id="3e7f7-121">이벤트는 네트워크 경고도 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-121">An event can also generate a network alert.</span></span> <span data-ttu-id="3e7f7-122">특정 프로그램을 이벤트가 처음 발생할 때 실행되도록 하거나 이벤트가 발생할 때마다 실행되도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-122">You can have a specified program run the first time or every time an event occurs.</span></span> <span data-ttu-id="3e7f7-123">예를 들어 경고 기능을 사용하면 모든 시스템 관리자에게 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 디스크 공간이 부족하다는 네트워크 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-123">For example, an alert can send a network message to all system administrators that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is getting low on disk space.</span></span>  
  
## <a name="logs"></a><span data-ttu-id="3e7f7-124">로그</span><span class="sxs-lookup"><span data-stu-id="3e7f7-124">Logs</span></span>  
 <span data-ttu-id="3e7f7-125">로그를 사용하면 선택된 개체 및 컴퓨터의 현재 동작에 대한 정보를 기록해 나중에 검색하고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-125">Logs allow you to record information on the current activity of selected objects and computers for later viewing and analysis.</span></span> <span data-ttu-id="3e7f7-126">여러 시스템의 데이터를 모아 하나의 로그 파일에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-126">You can collect data from multiple systems into a single log file.</span></span> <span data-ttu-id="3e7f7-127">예를 들어 여러 컴퓨터에 있는 선택된 개체의 성능에 대한 정보를 축적하도록 로그를 여러 개 만들어 나중에 분석할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-127">For example, you can create different logs to accumulate information about the performance of selected objects on various computers for future analysis.</span></span> <span data-ttu-id="3e7f7-128">이렇게 모은 로그 파일에 이름을 지정해 저장하면 비슷한 정보의 다른 로그를 만들어 비교할 때 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-128">You can save these selections under a file name and reuse them when you want to create another log of similar information for comparison.</span></span>  
  
 <span data-ttu-id="3e7f7-129">로그 파일을 활용하면 문제 해결이나 계획 수립 단계에서 풍부한 정보를 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-129">Log files provide a wealth of information for troubleshooting or planning.</span></span> <span data-ttu-id="3e7f7-130">차트, 경고 및 보고서는 현재 작업에 대한 즉각적인 피드백을 제공하는 반면, 로그 파일을 사용하면 장기간에 걸쳐 카운터를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-130">Whereas charts, alerts, and reports on current activity provide instant feedback, log files enable you to track counters over a long period of time.</span></span> <span data-ttu-id="3e7f7-131">따라서 정보를 완벽하게 검사해 시스템 성능을 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-131">Thus, you can examine information more thoroughly and document system performance.</span></span>  
  
## <a name="reports"></a><span data-ttu-id="3e7f7-132">보고서</span><span class="sxs-lookup"><span data-stu-id="3e7f7-132">Reports</span></span>  
 <span data-ttu-id="3e7f7-133">보고서를 사용하면 계속 변경되는 선택된 개체의 카운터 및 인스턴스 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-133">Reports allow you to display constantly changing counter and instance values for selected objects.</span></span> <span data-ttu-id="3e7f7-134">각 인스턴스의 값은 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-134">Values appear in columns for each instance.</span></span> <span data-ttu-id="3e7f7-135">보고 간격, 인쇄 스냅샷 및 데이터 내보내기를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-135">You can adjust report intervals, print snapshots, and export data.</span></span> <span data-ttu-id="3e7f7-136">숫자를 그대로 표시하려면 보고서를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-136">Use reports when you need to display the raw numbers.</span></span>  
  
 <span data-ttu-id="3e7f7-137">차트, 경고, 로그, 보고서 작성 또는 Windows 개체 및 카운터에 대한 자세한 내용은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e7f7-137">For more information about creating charts, alerts, logs, and reports, or about Windows objects and counters, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7f7-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e7f7-138">See Also</span></span>  
 [<span data-ttu-id="3e7f7-139">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="3e7f7-139">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
