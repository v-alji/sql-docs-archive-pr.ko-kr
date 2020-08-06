---
title: 중단점까지 재생 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f33b6862847b042a2613d8c2aa035dd5805493ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737234"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a><span data-ttu-id="3ba62-102">중단점까지 재생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="3ba62-102">Replay to a Breakpoint (SQL Server Profiler)</span></span>
  <span data-ttu-id="3ba62-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생할 추적 파일이나 테이블에 중단점을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-103">This topic describes how to set breakpoints in a trace file or table that you want to replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="3ba62-104">추적 재생을 시작하기 전에 추적 파일이나 테이블에 중단점을 설정하면 특정 이벤트에서 추적 재생을 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-104">Setting breakpoints in a trace file or table before you start to replay the trace, enables you to pause replay of the trace at specific events.</span></span> <span data-ttu-id="3ba62-105">추적을 재생하는 동안 중단점을 사용하면 긴 추적 스크립트 재생을 증분 방식으로 분석할 수 있는 짧은 세그먼트로 나눌 수 있으므로 디버깅이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-105">Using breakpoints while replaying a trace supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-a-breakpoint"></a><span data-ttu-id="3ba62-106">중단점까지 재생하려면</span><span class="sxs-lookup"><span data-stu-id="3ba62-106">To replay to a breakpoint</span></span>  
  
1.  <span data-ttu-id="3ba62-107">재생할 추적 파일이나 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-107">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="3ba62-108">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-108">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="3ba62-109">열려는 추적 파일이나 추적 테이블에 재생에 필요한 이벤트 클래스가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-109">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="3ba62-110">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ba62-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="3ba62-111">추적 창에서 중단점으로 사용할 이벤트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-111">In the trace window, click an event that you want to use as a breakpoint.</span></span> <span data-ttu-id="3ba62-112">다음 세 가지 방법 중 하나를 사용하여 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-112">Use one of the following three methods to set a breakpoint:</span></span>  
  
    -   <span data-ttu-id="3ba62-113">F9 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-113">Press F9.</span></span>  
  
    -   <span data-ttu-id="3ba62-114">**재생** 메뉴에서 **중단점 설정/해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-114">On the **Replay** menu, click **Toggle Breakpoint**.</span></span>  
  
    -   <span data-ttu-id="3ba62-115">이벤트를 마우스 오른쪽 단추로 클릭한 다음 **중단점 설정/해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-115">Right-click the event, and then click **Toggle Breakpoint**.</span></span>  
  
     <span data-ttu-id="3ba62-116">선택한 추적 이벤트 옆에 빨간색 글머리 기호가 나타나 이 이벤트가 추적 중단점임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-116">A red bullet appears next to the selected trace event, indicating that it is the trace breakpoint.</span></span>  
  
     <span data-ttu-id="3ba62-117">중단점을 여러 개 설정하려면 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-117">Repeat this step to set several breakpoints.</span></span>  
  
3.  <span data-ttu-id="3ba62-118">**재생** 메뉴에서 **시작**을 클릭하고 추적을 재생하려는 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-118">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="3ba62-119">**재생 구성** 대화 상자에서 설정을 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-119">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3ba62-120">재생이 시작되고 중단점에 도달하면 재생이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-120">The replay starts, pausing when the breakpoint is reached.</span></span>  
  
5.  <span data-ttu-id="3ba62-121">F5 키를 눌러 재생을 재개하고 다음 중단점으로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-121">Press F5 to resume the replay and proceed to the next breakpoint.</span></span>  
  
6.  <span data-ttu-id="3ba62-122">추적이 끝날 때까지 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="3ba62-122">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba62-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ba62-123">See Also</span></span>  
 <span data-ttu-id="3ba62-124">[커서까지 재생&#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="3ba62-124">[Replay to a Cursor &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="3ba62-125">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="3ba62-125">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="3ba62-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="3ba62-126">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
