---
title: 추적 테이블 재생 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3c26858fa852686bc3d9ccf4a26d47e04852647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733387"
---
# <a name="replay-a-trace-table-sql-server-profiler"></a><span data-ttu-id="2b115-102">추적 테이블 재생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2b115-102">Replay a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="2b115-103">재생은 저장된 추적을 열고 나중에 재생하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-103">Replay is the ability to open a saved trace and replay it again.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="2b115-104">는 사용자 연결 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 시뮬레이션할 수 있는 다중 스레드 재생 엔진을 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-104">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="2b115-105">재생 기능은 애플리케이션이나 프로세스 문제 해결에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-105">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="2b115-106">문제를 파악하여 수정할 때 수정된 애플리케이션이나 프로세스에 대해 잠재적인 문제를 발견한 추적을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-106">When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="2b115-107">원래 추적을 재생한 다음 결과를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-107">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="2b115-108">모니터링하려는 다른 이벤트 클래스 외에도 재생 기능을 사용하려면 특정 이벤트 클래스를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-108">In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay.</span></span> <span data-ttu-id="2b115-109">**TSQL_Replay** 추적 템플릿을 사용할 경우 이러한 이벤트는 기본적으로 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-109">These events are captured by default if you use the **TSQL_Replay** trace template.</span></span> <span data-ttu-id="2b115-110">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b115-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
### <a name="to-replay-a-trace-table"></a><span data-ttu-id="2b115-111">추적 테이블을 재생하려면</span><span class="sxs-lookup"><span data-stu-id="2b115-111">To replay a trace table</span></span>  
  
1.  <span data-ttu-id="2b115-112">재생에 필요한 이벤트 클래스가 들어 있는 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-112">Open a trace table that contains the event classes necessary for replay.</span></span>  
  
2.  <span data-ttu-id="2b115-113">**재생** 메뉴에서 **시작**을 클릭하고 추적을 재생하려는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-113">On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="2b115-114">**재생 구성** 대화 상자의 **기본 재생 옵션** 탭에서 **서버 재생**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-114">In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify **Replay server**.</span></span> <span data-ttu-id="2b115-115">**서버 재생** 상자에 표시된 서버를 변경하려면 **변경** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-115">Click **Change** to change the server that is displayed in the **Replay server** box.</span></span>  
  
4.  <span data-ttu-id="2b115-116">또는 재생을 저장할 대상으로 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-116">Optionally, select one of the following destinations in which to save the replay:</span></span>  
  
    -   <span data-ttu-id="2b115-117">**파일에 저장,** 재생이 저장될 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-117">**Save to file,** which specifies a file in which to save the replay.</span></span>  
  
    -   <span data-ttu-id="2b115-118">**테이블에 저장**- 재생이 저장될 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-118">**Save to table**, which specifies a database table in which to save the replay.</span></span>  
  
5.  <span data-ttu-id="2b115-119">**추적한 순서대로 이벤트를 재생합니다.** 또는 **여러 스레드를 사용하여 이벤트를 재생합니다.** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-119">Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**.</span></span> <span data-ttu-id="2b115-120">다음 표에서는 이 두 설정 사이의 차이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-120">The following table explains the difference between these settings.</span></span>  
  
    |<span data-ttu-id="2b115-121">옵션</span><span class="sxs-lookup"><span data-stu-id="2b115-121">Option</span></span>|<span data-ttu-id="2b115-122">Description</span><span class="sxs-lookup"><span data-stu-id="2b115-122">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="2b115-123">**추적한 순서대로 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="2b115-123">**Replay events in the order they were traced**</span></span>|<span data-ttu-id="2b115-124">기록된 순서대로 이벤트를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-124">Replays events in the order they were recorded.</span></span> <span data-ttu-id="2b115-125">이 옵션을 사용하면 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-125">This option enables debugging.</span></span>|  
    |<span data-ttu-id="2b115-126">**여러 스레드를 사용하여 이벤트를 재생합니다.**</span><span class="sxs-lookup"><span data-stu-id="2b115-126">**Replay events using multiple threads**</span></span>|<span data-ttu-id="2b115-127">이 옵션은 여러 스레드를 사용하여 순서와 관계없이 각 이벤트를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-127">This option uses multiple threads to replay each event regardless of the sequence.</span></span> <span data-ttu-id="2b115-128">이 옵션을 사용하면 성능이 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-128">This option optimizes performance.</span></span>|  
  
6.  <span data-ttu-id="2b115-129">수행되는 재생을 확인하려면 **재생 결과 표시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-129">Select **Display replay results** to view the replay as it occurs.</span></span>  
  
7.  <span data-ttu-id="2b115-130">필요에 따라 **고급 재생 옵션**탭을 클릭하여 다음 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-130">Optionally, click the **Advanced Replay Options**tab to specify the following options:</span></span>  
  
    -   <span data-ttu-id="2b115-131">모든 SPID(서버 프로세스 ID)를 재생하려면 **시스템 SPID 재생**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-131">To replay all server process IDs (SPIDs), select **Replay system SPIDs**.</span></span>  
  
    -   <span data-ttu-id="2b115-132">재생을 특정 SPID에 속하는 프로세스로 제한하려면 **한 SPID만 재생**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-132">To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**.</span></span> <span data-ttu-id="2b115-133">**재생할 SPID**입력란에 SPID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-133">In the **SPID to replay**box, type the SPID.</span></span>  
  
    -   <span data-ttu-id="2b115-134">특정 시간 동안 발생된 이벤트를 재생하려면 **날짜 및 시간별 재생 제한**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-134">To replay events that occurred during a specific time period, select **Limit replay by date and time**.</span></span> <span data-ttu-id="2b115-135">**시작 시간**및 **종료 시간**에 날짜와 시간을 선택하여 재생에 포함될 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-135">Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.</span></span>  
  
    -   <span data-ttu-id="2b115-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 재생 중 프로세스를 관리하는 방법을 제어하려면 **상태 모니터 옵션**을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2b115-136">To control how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manages processes during replay, configure **Health Monitor Options**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b115-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b115-137">See Also</span></span>  
 <span data-ttu-id="2b115-138">[SQL Server 프로파일러 실행에 필요한 권한](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2b115-138">[Permissions Required to Run SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="2b115-139">[추적 재생](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="2b115-139">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="2b115-140">[추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2b115-140">[Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="2b115-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2b115-141">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
