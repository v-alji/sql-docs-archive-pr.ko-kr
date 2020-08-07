---
title: Windows 성능 로그 데이터와 추적의 상관 관계 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 879441c948f0ad04b971159a37ec0dcec90e3ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727600"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a><span data-ttu-id="d4d23-102">Windows 성능 로그 데이터와 추적의 상관 관계 지정</span><span class="sxs-lookup"><span data-stu-id="d4d23-102">Correlate a Trace with Windows Performance Log Data</span></span>
  <span data-ttu-id="d4d23-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 Microsoft Windows 성능 로그를 열고 추적과의 상관 관계를 지정할 카운터를 선택한 다음 선택한 성능 카운터를 추적과 함께 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 그래픽 사용자 인터페이스에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d23-103">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can open a Microsoft Windows performance log, choose the counters you want to correlate with a trace, and display the selected performance counters alongside the trace in the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface.</span></span> <span data-ttu-id="d4d23-104">추적 창에서 이벤트를 선택하면 선택한 추적 이벤트와 상관 관계가 있는 성능 로그 데이터가 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 의 시스템 모니터 데이터 창에서 빨간 세로 막대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d23-104">When you select an event in the trace window, a vertical red bar in the System Monitor data window pane of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indicates the performance log data that correlates with the selected trace event.</span></span>  
  
 <span data-ttu-id="d4d23-105">추적과 성능 카운터의 상관 관계를 지정하려면 **StartTime** 및 **EndTime** 데이터 열을 포함하는 추적 파일이나 테이블을 연 다음, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **파일** 메뉴에서 **성능 데이터 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d23-105">To correlate a trace with performance counters, open a trace file or table that contains the **StartTime** and **EndTime** data columns, and then click **Import Performance Data** on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="d4d23-106">그러면 성능 로그를 열고 추적과의 상관 관계를 지정할 시스템 모니터 개체와 카운터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d23-106">You can then open a performance log, and select the System Monitor objects and counters that you want to correlate with the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d23-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d23-107">See Also</span></span>  
 [<span data-ttu-id="d4d23-108">추적과 Windows 성능 로그 데이터의 상관 관계 지정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d23-108">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
