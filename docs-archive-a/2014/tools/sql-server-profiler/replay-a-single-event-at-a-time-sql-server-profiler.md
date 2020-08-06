---
title: 단일 이벤트를 한 번에 하나씩 재생(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 457bc94d9d8eae470fb60b450d30441c07e676df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737263"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a><span data-ttu-id="a96bf-102">단일 이벤트를 한 번에 하나씩 재생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="a96bf-102">Replay a Single Event at a Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="a96bf-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생 추적 파일이나 테이블에서 한 번에 하나씩 이벤트를 재생하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-103">This topic describes how to replay one event at a time in a replay trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-replay-a-single-event-at-a-time"></a><span data-ttu-id="a96bf-104">한 번에 하나씩 단일 이벤트를 재생하려면</span><span class="sxs-lookup"><span data-stu-id="a96bf-104">To replay a single event at a time</span></span>  
  
1.  <span data-ttu-id="a96bf-105">재생할 추적 파일이나 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-105">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="a96bf-106">자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="a96bf-107">열려는 추적 파일이나 추적 테이블에 재생에 필요한 이벤트 클래스가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-107">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="a96bf-108">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a96bf-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="a96bf-109">**재생** 메뉴에서 **단계**를 클릭하고 추적을 재생하려는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-109">On the **Replay** menu, click **Step**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="a96bf-110">**재생 구성** 대화 상자에서 설정을 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span> <span data-ttu-id="a96bf-111">**재생 구성** 대화 상자에서 설정을 지정하는 방법은 [추적 파일 재생&#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 재생&#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a96bf-111">For more information about specifying settings on the **Replay Configuration** dialog box, see [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) or [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).</span></span>  
  
4.  <span data-ttu-id="a96bf-112">첫 번째 이벤트를 재생하려면 **재생 구성** 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-112">To replay the first event, click **OK** in the **Replay Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="a96bf-113">다음 이벤트를 재생하려면 **재생** 메뉴에서 **단계**를 클릭하거나 F10 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-113">To replay subsequent events, on the **Replay** menu, click **Step**, or press F10.</span></span> <span data-ttu-id="a96bf-114">**단계** 를 클릭하거나 F10 키를 누를 때마다 다음 이벤트가 순서대로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="a96bf-114">Repeat clicking **Step** or pressing F10 for each event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96bf-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a96bf-115">See Also</span></span>  
 <span data-ttu-id="a96bf-116">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="a96bf-116">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="a96bf-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="a96bf-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
