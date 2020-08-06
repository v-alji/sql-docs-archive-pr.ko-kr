---
title: 재생 추적 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c485317d1343958f9c430b73d858130097d44d75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737228"
---
# <a name="replay-traces"></a><span data-ttu-id="a633a-102">추적 재생</span><span class="sxs-lookup"><span data-stu-id="a633a-102">Replay Traces</span></span>
  <span data-ttu-id="a633a-103">재생은 추적에 캡처된 작업을 재현하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-103">Replay is the ability to reproduce activity that has been captured in a trace.</span></span> <span data-ttu-id="a633a-104">추적을 만들거나 편집할 때 추적을 파일에 저장하면 나중에 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-104">When you create or edit a trace, you can save the trace to a file and replay it later.</span></span> <span data-ttu-id="a633a-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하면 단일 컴퓨터의 추적 작업만 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-105">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay trace activity from a single computer.</span></span> <span data-ttu-id="a633a-106">대규모 작업의 경우 Distributed Replay Utility를 사용하면 여러 컴퓨터의 추적 데이터를 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-106">For large workloads, use the Distributed Replay Utility to replay trace data from multiple computers.</span></span>  
  
 <span data-ttu-id="a633a-107">이 섹션에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]의 재생 기능을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-107">This section describes how to use the replay features of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="a633a-108">Distributed Replay Utility에 대한 자세한 내용은 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a633a-108">For more information about the Distributed Replay Utility, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a633a-109">는 사용자 연결 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 시뮬레이션할 수 있는 다중 스레드 재생 엔진을 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-109">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="a633a-110">재생 기능은 애플리케이션이나 프로세스 문제 해결에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-110">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="a633a-111">문제를 파악하여 수정한 다음에는 수정된 애플리케이션이나 프로세스에 대해 잠재적인 문제가 발견된 추적을 실행하고</span><span class="sxs-lookup"><span data-stu-id="a633a-111">When you have identified the problem and implemented corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="a633a-112">원래 추적을 재생한 다음 결과를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-112">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="a633a-113">추적 재생은 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **재생** 메뉴에서 **중단점 설정/해제** 및 **커서까지 실행** 옵션을 사용하여 디버깅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-113">Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu.</span></span> <span data-ttu-id="a633a-114">이 옵션을 사용하면 추적 재생을 짧은 조각으로 분리하고 점차 큰 부분으로 분석 범위를 늘릴 수 있어 긴 스크립트를 분석할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-114">These options especially improve the analysis of long scripts because they can break the replay of the trace into short segments so they can be analyzed incrementally.</span></span>  
  
 <span data-ttu-id="a633a-115">추적 재생에 필요한 권한에 대한 자세한 내용은 [SQL Server 프로파일러 실행에 필요한 권한](permissions-required-to-run-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a633a-115">For information about the permissions required to replay traces, see [Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a633a-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a633a-116">In This Section</span></span>  
  
|<span data-ttu-id="a633a-117">항목</span><span class="sxs-lookup"><span data-stu-id="a633a-117">Topic</span></span>|<span data-ttu-id="a633a-118">Description</span><span class="sxs-lookup"><span data-stu-id="a633a-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a633a-119">재생 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a633a-119">Replay Requirements</span></span>](replay-requirements.md)|<span data-ttu-id="a633a-120">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생될 수 있도록 추적 정의에 꼭 포함되어야 하는 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-120">Describes the events that must be included in a trace definition so that it can be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="a633a-121">재생 옵션&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="a633a-121">Replay Options &#40;SQL Server Profiler&#41;</span></span>](replay-options-sql-server-profiler.md)|<span data-ttu-id="a633a-122">**의** 재생 구성 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]대화 상자에서 설정할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-122">Describes the options you can set in the **Replay Configuration** dialog box of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="a633a-123">추적 재생에 대한 고려 사항&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="a633a-123">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)|<span data-ttu-id="a633a-124">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 재생할 수 없는 추적 이벤트 및 추적 재생이 서버 성능에 미치는 영향에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a633a-124">Describes trace events that can not be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and the effects on server performance of replaying traces.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a633a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a633a-125">See Also</span></span>  
 [<span data-ttu-id="a633a-126">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="a633a-126">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
