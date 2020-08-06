---
title: 추적 시작 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2b75519631269a1213077a4e295ac73fca1b950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734751"
---
# <a name="start-a-trace"></a><span data-ttu-id="b5286-102">추적 시작</span><span class="sxs-lookup"><span data-stu-id="b5286-102">Start a Trace</span></span>
  <span data-ttu-id="b5286-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 새 추적을 정의하거나 템플릿을 만든 후 새 추적 정의 또는 템플릿을 사용하여 데이터 캡처를 시작, 일시 중지 또는 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-103">After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.</span></span>  
  
## <a name="starting-a-trace"></a><span data-ttu-id="b5286-104">추적 시작</span><span class="sxs-lookup"><span data-stu-id="b5286-104">Starting a Trace</span></span>  
 <span data-ttu-id="b5286-105">추적을 시작하고 정의된 원본이 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 인스턴스인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 캡처된 서버 이벤트의 임시 보유 장소를 제공하는 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-105">When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates a queue that provides a temporary holding place for captured server events.</span></span>  
  
 <span data-ttu-id="b5286-106">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 SQL 추적에 액세스하는 경우 추적이 시작되면 새 추적 창이 열리면서(창이 열려 있지 않은 경우) 데이터가 즉시 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-106">When you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to access SQL Trace, a new trace window opens (if one is not already open) when a trace is started, and data is immediately captured.</span></span>  
  
 <span data-ttu-id="b5286-107">[!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 저장 프로시저를 사용하여 SQL 추적에 액세스하는 경우에는 데이터 캡처를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 시작될 때마다 추적을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-107">When you use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts for data to be captured.</span></span> <span data-ttu-id="b5286-108">추적이 시작되면 추적 이름만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-108">When a trace has been started, you can modify only the name of the trace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5286-109">기존의 추적으로 작업하면 속성을 볼 수는 있지만 수정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5286-109">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="b5286-110">속성을 수정하려면 추적을 시작하거나 일시 중지하십시오.</span><span class="sxs-lookup"><span data-stu-id="b5286-110">To modify the properties, stop or pause the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5286-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5286-111">See Also</span></span>  
 <span data-ttu-id="b5286-112">[서버에 연결한 후 추적을 자동으로 시작 &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5286-112">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b5286-113">[추적 &#40;SQL Server Profiler 일시 중지&#41;](pause-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5286-113">[Pause a Trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b5286-114">[SQL Server Profiler &#40;추적을 중지&#41;](stop-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5286-114">[Stop a Trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b5286-115">[SQL Server Profiler &#40;추적 창 지우기&#41;](clear-a-trace-window-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5286-115">[Clear a Trace Window &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="b5286-116">일시 중지 또는 중지 후 추적 실행&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="b5286-116">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
