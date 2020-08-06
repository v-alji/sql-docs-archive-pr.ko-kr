---
title: SQL Server Profiler 도구-옵션 (일반 옵션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fad4d3529482835367898276a973bd7c8827b553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652981"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a><span data-ttu-id="22fe6-102">SQL Server Profiler - Tools-Options (General Options Page)</span><span class="sxs-lookup"><span data-stu-id="22fe6-102">SQL Server Profiler - Tools-Options (General Options Page)</span></span>
  <span data-ttu-id="22fe6-103">**일반 옵션** 대화 상자를 사용하여 다음 옵션을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-103">Use the **General Options** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22fe6-104">옵션</span><span class="sxs-lookup"><span data-stu-id="22fe6-104">Options</span></span>  
  
### <a name="display-options"></a><span data-ttu-id="22fe6-105">표시 옵션</span><span class="sxs-lookup"><span data-stu-id="22fe6-105">Display Options</span></span>  
 <span data-ttu-id="22fe6-106">**글꼴 이름**</span><span class="sxs-lookup"><span data-stu-id="22fe6-106">**Font name**</span></span>  
 <span data-ttu-id="22fe6-107">추적하는 동안 추적 결과 표에 사용되는 글꼴 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-107">Displays the name of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="22fe6-108">**글꼴 크기**</span><span class="sxs-lookup"><span data-stu-id="22fe6-108">**Font size**</span></span>  
 <span data-ttu-id="22fe6-109">추적하는 동안 추적 결과 표에 사용되는 글꼴 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-109">Displays the size of the font used in the trace results grid during traces.</span></span>  
  
 <span data-ttu-id="22fe6-110">**글꼴 선택**</span><span class="sxs-lookup"><span data-stu-id="22fe6-110">**Choose Font**</span></span>  
 <span data-ttu-id="22fe6-111">글꼴 설정을 변경할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-111">Opens a dialog to change the font settings.</span></span>  
  
 <span data-ttu-id="22fe6-112">**날짜 및 시간 값 표시에 국가별 설정 사용**</span><span class="sxs-lookup"><span data-stu-id="22fe6-112">**Use regional settings to display date and time values**</span></span>  
 <span data-ttu-id="22fe6-113">컴퓨터에 구성된 국가별 설정에 따라 날짜 및 시간 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-113">Displays date and time values in regional settings configured for your computer.</span></span> <span data-ttu-id="22fe6-114">이 옵션을 선택하지 않으면 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 사용하는 밀리초 단위까지 포함된 고정 형식으로 날짜 및 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-114">If you do not select this option, the date and time values are displayed in the fixed format used by Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], which includes milliseconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22fe6-115">이 확인란을 선택/선택 해제하면 **StartTime** 및 **EndTime**과 같은 시간 열 표시 형식이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-115">Toggling this checkbox changes the time columns display format such as **StartTime** and **EndTime**.</span></span> <span data-ttu-id="22fe6-116">하지만 언어 이벤트 또는 원격 프로시저 호출(RPC) 내의 **DateTime** 값 매개 변수는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-116">However, it does not change the **DateTime** value parameters inside the language events or remote procedure calls (RPCs).</span></span>  
  
 <span data-ttu-id="22fe6-117">**기간 열에 마이크로초 단위로 값 표시**</span><span class="sxs-lookup"><span data-stu-id="22fe6-117">**Show values in Duration column in microseconds**</span></span>  
 <span data-ttu-id="22fe6-118">추적에 대한 **기간** 데이터 열의 값을 마이크로초 단위로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-118">Displays the values in microseconds in the **Duration** data column of traces.</span></span> <span data-ttu-id="22fe6-119">기본적으로 **기간** 열의 값은 밀리초 단위로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-119">By default, the **Duration** column displays values in milliseconds.</span></span>  
  
### <a name="tracing-options"></a><span data-ttu-id="22fe6-120">추적 옵션</span><span class="sxs-lookup"><span data-stu-id="22fe6-120">Tracing Options</span></span>  
 <span data-ttu-id="22fe6-121">**연결한 후 즉시 추적 시작**</span><span class="sxs-lookup"><span data-stu-id="22fe6-121">**Start tracing immediately after making connection**</span></span>  
 <span data-ttu-id="22fe6-122">연결되면 기본 템플릿을 사용하여 즉시 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-122">Begin a trace using the default template as soon as a connection is made.</span></span>  
  
 <span data-ttu-id="22fe6-123">**공급자 버전 변경 시 추적 정의 업데이트**</span><span class="sxs-lookup"><span data-stu-id="22fe6-123">**Update trace definition when provider version changes**</span></span>  
 <span data-ttu-id="22fe6-124">공급자가 업데이트된 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 최신 추적 정의를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-124">Apply the most current trace definition to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when the provider is updated.</span></span> <span data-ttu-id="22fe6-125">이 옵션은 기본적으로 선택되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-125">This item is not checked by default.</span></span> <span data-ttu-id="22fe6-126">이 옵션을 선택하면 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 가 서버에서 추적 정의를 쿼리하여 정의가 있으면 디스크에 파일을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-126">This forces [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to query the server for the trace definition and re-create, if one exists, the file on disk.</span></span>  
  
### <a name="file-rollover-options"></a><span data-ttu-id="22fe6-127">파일 롤오버 옵션</span><span class="sxs-lookup"><span data-stu-id="22fe6-127">File Rollover Options</span></span>  
 <span data-ttu-id="22fe6-128">**확인하지 않고 모든 롤오버 파일을 순서대로 로드**</span><span class="sxs-lookup"><span data-stu-id="22fe6-128">**Load all rollover files in sequence without prompting**</span></span>  
 <span data-ttu-id="22fe6-129">추적 파일이 열리면 롤오버 파일을 자동으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-129">Load rollover files automatically when a trace file is opened.</span></span> <span data-ttu-id="22fe6-130">이 옵션을 선택하면 추적하는 동안 두 개 이상의 파일이 생성된 경우 자동으로 모든 롤오버 파일이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-130">If more than one file was created while tracing, selecting this option automatically loads all rollover files.</span></span>  
  
 <span data-ttu-id="22fe6-131">**롤오버 파일 로드 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="22fe6-131">**Prompt before loading rollover files**</span></span>  
 <span data-ttu-id="22fe6-132">추적 파일을 열면 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 가 롤오버 파일을 추가하기 전에 사용자에게 확인 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-132">Have [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] prompt you before adding a rollover file when a trace file is opened.</span></span>  
  
 <span data-ttu-id="22fe6-133">**다음 롤오버 파일 로드 안 함**</span><span class="sxs-lookup"><span data-stu-id="22fe6-133">**Never load subsequent rollover files**</span></span>  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="22fe6-134">에서 다음 롤오버 파일을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-134">never loads subsequent rollover files when a trace file is opened.</span></span>  
  
### <a name="replay-options"></a><span data-ttu-id="22fe6-135">재생 옵션</span><span class="sxs-lookup"><span data-stu-id="22fe6-135">Replay Options</span></span>  
 <span data-ttu-id="22fe6-136">**기본 재생 스레드 수**</span><span class="sxs-lookup"><span data-stu-id="22fe6-136">**Default number of replay threads**</span></span>  
 <span data-ttu-id="22fe6-137">동시에 사용할 재생 스레드 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-137">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="22fe6-138">이 값을 높게 설정할수록 재생하는 동안 리소스가 더 많이 사용되지만 재생 동시성은 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-138">A higher number consumes more resources during replay, but increases replay concurrency.</span></span>  
  
 <span data-ttu-id="22fe6-139">**기본 상태 모니터 대기 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="22fe6-139">**Default health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="22fe6-140">재생하기 전에 대기하는 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-140">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="22fe6-141">기본값은 3600초(1시간)입니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-141">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="22fe6-142">이 설정은 상태 모니터에서 스레드를 종료하기 전까지 스레드가 실행되는 시간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-142">This setting affects the amount of time a thread is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="22fe6-143">**기본 상태 모니터 폴링 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="22fe6-143">**Default health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="22fe6-144">재생 중 상태 모니터 폴링 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-144">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="22fe6-145">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-145">Default is 60 seconds.</span></span> <span data-ttu-id="22fe6-146">이 값을 사용하면 상태 모니터에서 종료 후보에 대해 폴링하는 주기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22fe6-146">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fe6-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22fe6-147">See Also</span></span>  
 <span data-ttu-id="22fe6-148">[서버에 연결한 후 추적을 자동으로 시작 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-148">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="22fe6-149">[추적 표시 기본값 설정 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-149">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="22fe6-150">[SQL Server Profiler &#40;추적 테이블 재생&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-150">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="22fe6-151">[SQL Server Profiler &#40;추적 파일 재생&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-151">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="22fe6-152">[재생 추적](../tools/sql-server-profiler/replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-152">[Replay Traces](../tools/sql-server-profiler/replay-traces.md) </span></span>  
 <span data-ttu-id="22fe6-153">[전역 추적 옵션 설정 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-153">[Set Global Trace Options &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="22fe6-154">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="22fe6-154">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="22fe6-155">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="22fe6-155">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
