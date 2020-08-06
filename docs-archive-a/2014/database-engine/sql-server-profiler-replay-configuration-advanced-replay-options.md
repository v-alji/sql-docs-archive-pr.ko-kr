---
title: SQL Server Profiler 재생 구성 (고급 재생 옵션) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95070d8defb5b7778859ce470aaa8cfc85955ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736693"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a><span data-ttu-id="19551-102">SQL Server 프로파일러 - 재생 구성(고급 재생 옵션)</span><span class="sxs-lookup"><span data-stu-id="19551-102">SQL Server Profiler - Replay Configuration (Advanced Replay Options)</span></span>
  <span data-ttu-id="19551-103">**재생 구성** 대화 상자에서 **고급 재생 옵션** 탭을 사용하여 추적 파일 재생 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19551-103">In the **Replay Configuration** dialog box, use the **Advanced Replay Options** tab to specify how to replay a trace file.</span></span>  
  
 <span data-ttu-id="19551-104">이 창을 보려면 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 사용하여 재생에 적합한 이벤트가 포함된 추적 파일 또는 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19551-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="19551-105">자세한 내용은 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19551-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="19551-106">추적 파일 또는 테이블이 열려 있는 상태로 **재생** 메뉴에서 **시작**을 클릭하고 추적을 재생할 SQL Server의 인스턴스에 연결한 다음 **고급 재생 옵션** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-106">While the trace file or table is open, on the **Replay** menu, click **Start**, connect to the instance of SQL Server where you want to replay the trace, and then click the **Advanced Replay Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="19551-107">옵션</span><span class="sxs-lookup"><span data-stu-id="19551-107">Options</span></span>  
 <span data-ttu-id="19551-108">**시스템 SPID 재생**</span><span class="sxs-lookup"><span data-stu-id="19551-108">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="19551-109">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 에서 SPID(시스템 프로세스 식별자)를 재생할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-109">Specifies whether [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] replays system process identifiers (SPIDs).</span></span>  
  
 <span data-ttu-id="19551-110">**한 SPID만 재생**</span><span class="sxs-lookup"><span data-stu-id="19551-110">**Replay one SPID only**</span></span>  
 <span data-ttu-id="19551-111">선택한 SPID와 관련된 원본 추적 파일의 작업만 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-111">Replays only the activity in the source trace file that is related to the selected SPID.</span></span>  
  
 <span data-ttu-id="19551-112">**재생할 SPID**</span><span class="sxs-lookup"><span data-stu-id="19551-112">**SPID to replay**</span></span>  
 <span data-ttu-id="19551-113">재생할 SPID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-113">Specify which SPID to replay.</span></span>  
  
 <span data-ttu-id="19551-114">**날짜 및 시간별 재생 제한**</span><span class="sxs-lookup"><span data-stu-id="19551-114">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="19551-115">원본 추적 파일의 일부만 재생하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-115">Check to replay only a portion of the source trace file.</span></span>  
  
 <span data-ttu-id="19551-116">**시작 시간**</span><span class="sxs-lookup"><span data-stu-id="19551-116">**Start time**</span></span>  
 <span data-ttu-id="19551-117">원본 추적 파일에 지정되어 있는 재생 시작 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="19551-117">Date and time in the source trace file where the replay should start.</span></span>  
  
 <span data-ttu-id="19551-118">**종료 시간**</span><span class="sxs-lookup"><span data-stu-id="19551-118">**End time**</span></span>  
 <span data-ttu-id="19551-119">원본 추적 파일에 지정되어 있는 재생 중지 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="19551-119">Date and time in the source trace file where the replay should stop.</span></span>  
  
 <span data-ttu-id="19551-120">**상태 모니터 대기 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="19551-120">**Health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="19551-121">재생하기 전에 대기하는 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-121">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="19551-122">기본값은 3600초(1시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="19551-122">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="19551-123">이 설정은 상태 모니터에서 프로세스를 종료하기 전의 프로세스 실행 시간에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19551-123">This setting affects the amount of time a process is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="19551-124">**상태 모니터 폴링 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="19551-124">**Health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="19551-125">재생 중 상태 모니터 폴링 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-125">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="19551-126">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="19551-126">Default is 60 seconds.</span></span> <span data-ttu-id="19551-127">이 값을 사용하면 상태 모니터에서 종료 후보에 대해 폴링하는 주기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19551-127">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
 <span data-ttu-id="19551-128">**SQL Server 차단된 프로세스 모니터 설정**</span><span class="sxs-lookup"><span data-stu-id="19551-128">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="19551-129">차단된 프로세스 또는 차단 프로세스를 검색하는 프로세스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-129">Enables a process that searches for blocked or blocking processes.</span></span>  
  
 <span data-ttu-id="19551-130">**차단된 프로세스 모니터 대기 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="19551-130">**Blocked processes monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="19551-131">차단된 프로세스 모니터에서 차단된 프로세스 또는 차단 프로세스를 검색하는 간격을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="19551-131">Configures how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19551-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19551-132">See Also</span></span>  
 <span data-ttu-id="19551-133">[SQL Server Profiler &#40;추적 테이블 재생&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="19551-133">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="19551-134">[SQL Server Profiler &#40;추적 파일 재생&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="19551-134">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="19551-135">추적 재생</span><span class="sxs-lookup"><span data-stu-id="19551-135">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
