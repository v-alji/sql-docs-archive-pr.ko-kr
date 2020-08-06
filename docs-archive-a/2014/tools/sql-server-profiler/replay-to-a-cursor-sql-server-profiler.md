---
title: 커서까지 재생 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc5ba06b60100bf8ecc8d04909371021a5b00e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737233"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a><span data-ttu-id="f3504-102">커서까지 재생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="f3504-102">Replay to a Cursor (SQL Server Profiler)</span></span>
  <span data-ttu-id="f3504-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 커서에 도달했을 때 일시 중지된 추적 파일이나 테이블을 재생하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-103">This topic describes how to replay trace files or tables that pause when a cursor is reached by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f3504-104">커서에서 추적을 일시 중지하면 긴 추적 스크립트 재생을 증분 분석이 가능한 짧은 세그먼트로 나눌 수 있기 때문에 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-104">Pausing traces at cursors supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-the-cursor"></a><span data-ttu-id="f3504-105">커서까지 재생하려면</span><span class="sxs-lookup"><span data-stu-id="f3504-105">To replay to the cursor</span></span>  
  
1.  <span data-ttu-id="f3504-106">재생할 추적 파일이나 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-106">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="f3504-107">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-107">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="f3504-108">열려는 추적 파일이나 추적 테이블에 재생에 필요한 이벤트 클래스가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-108">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="f3504-109">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3504-109">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="f3504-110">추적 창에서 이벤트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-110">In the trace window, click an event.</span></span>  
  
3.  <span data-ttu-id="f3504-111">**재생** 메뉴에서 **커서까지 실행**을 클릭한 다음 추적을 재생할 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-111">On the **Replay** menu, click **Run to Cursor**, and then connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="f3504-112">**재생 구성** 대화 상자에서 설정을 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-112">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f3504-113">재생이 시작되며 첫 번째 커서에서 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-113">The replay starts, pausing when the first cursor is reached.</span></span>  
  
5.  <span data-ttu-id="f3504-114">추적을 다시 시작하려면 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-114">Press F5 to resume the trace.</span></span>  
  
6.  <span data-ttu-id="f3504-115">추적이 끝날 때까지 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="f3504-115">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3504-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3504-116">See Also</span></span>  
 <span data-ttu-id="f3504-117">[중단점까지 재생&#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f3504-117">[Replay to a Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="f3504-118">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="f3504-118">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="f3504-119">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="f3504-119">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
