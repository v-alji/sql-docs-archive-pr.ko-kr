---
title: SQL Server Profiler 재생 구성 (기본 재생 옵션) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cbf433c3108294909d91f7860136c0755b39b46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736687"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a><span data-ttu-id="56542-102">SQL Server 프로파일러 - 재생 구성(기본 재생 옵션)</span><span class="sxs-lookup"><span data-stu-id="56542-102">SQL Server Profiler - Replay Configuration (Basic Replay Options)</span></span>
  <span data-ttu-id="56542-103">**재생 구성** 대화 상자에서 **기본 재생 옵션** 페이지를 사용하여 추적 파일 또는 테이블을 재생하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56542-103">In the **Replay Configuration** dialog box, use the **Basic Replay Options** page to specify how to replay a trace file or table.</span></span>  
  
 <span data-ttu-id="56542-104">이 창을 보려면 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 사용하여 재생에 적합한 이벤트가 포함된 추적 파일 또는 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="56542-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="56542-105">자세한 내용은 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56542-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="56542-106">추적 파일이나 테이블을 연 상태에서 **재생** 메뉴의 **시작**을 클릭한 다음 추적을 재생할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-106">While the trace file or table is open, on the **Replay** menu, click **Start**, and then connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where you want to replay the trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56542-107">옵션</span><span class="sxs-lookup"><span data-stu-id="56542-107">Options</span></span>  
 <span data-ttu-id="56542-108">**서버 재생**</span><span class="sxs-lookup"><span data-stu-id="56542-108">**Replay server**</span></span>  
 <span data-ttu-id="56542-109">재생을 위해 연결할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-109">Displays the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to for the replay.</span></span>  
  
 <span data-ttu-id="56542-110">**변경 ...**</span><span class="sxs-lookup"><span data-stu-id="56542-110">**Change...**</span></span>  
 <span data-ttu-id="56542-111">다른 서버에 연결하려면 **서버에 연결** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-111">Launches the **Connect to Server** dialog box to connect to another server.</span></span>  
  
 <span data-ttu-id="56542-112">**파일에 저장**</span><span class="sxs-lookup"><span data-stu-id="56542-112">**Save to file**</span></span>  
 <span data-ttu-id="56542-113">재생 결과를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-113">Save the replay results to a file.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="56542-114">에서 위치를 지정하여 파일을 저장할 수 있는 표준 파일 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56542-114">displays the standard file dialog, where you can specify the location to save the file.</span></span>  
  
 <span data-ttu-id="56542-115">**테이블에 저장**</span><span class="sxs-lookup"><span data-stu-id="56542-115">**Save to table**</span></span>  
 <span data-ttu-id="56542-116">재생 결과를 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-116">Save the replay results to a table.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="56542-117">에서 위치를 지정하여 테이블을 저장할 수 있는 테이블 선택 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56542-117">displays the table selection dialog, where you can specify the location to save the table.</span></span>  
  
 <span data-ttu-id="56542-118">**재생 스레드 수**</span><span class="sxs-lookup"><span data-stu-id="56542-118">**Number of replay threads**</span></span>  
 <span data-ttu-id="56542-119">동시에 사용할 재생 스레드 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-119">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="56542-120">숫자가 높을수록 재생 중 소비되는 리소스가 늘어나지만 재생 속도가 빨라지고 동시성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="56542-120">A higher number consumes more resources during replay, but replay is faster and more concurrent.</span></span>  
  
 <span data-ttu-id="56542-121">**추적한 순서대로 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="56542-121">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="56542-122">순차적으로 이벤트를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-122">Replay events sequentially.</span></span> <span data-ttu-id="56542-123">디버깅을 위해 추적을 재생할 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-123">Use this option if you are replaying a trace for debugging.</span></span>  
  
 <span data-ttu-id="56542-124">**여러 스레드를 사용하여 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="56542-124">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="56542-125">동시에 이벤트를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-125">Replay events concurrently.</span></span> <span data-ttu-id="56542-126">이 옵션을 사용하면 순차적으로 이벤트를 재생하는 것보다 속도가 빨라지지만 디버깅이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="56542-126">This option is faster than replaying events sequentially, but disables debugging.</span></span> <span data-ttu-id="56542-127">이벤트는 해당 SPID(시스템 프로세스 ID) 내에서 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="56542-127">The events are ordered within their system process identifiers (SPID).</span></span>  
  
 <span data-ttu-id="56542-128">**재생 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="56542-128">**Display replay results**</span></span>  
 <span data-ttu-id="56542-129">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에 재생 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56542-129">Display replay results in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56542-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56542-130">See Also</span></span>  
 <span data-ttu-id="56542-131">[SQL Server Profiler &#40;추적 테이블 재생&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="56542-131">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="56542-132">[SQL Server Profiler &#40;추적 파일 재생&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="56542-132">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="56542-133">추적 재생</span><span class="sxs-lookup"><span data-stu-id="56542-133">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
