---
title: 예약된 추적 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a698d88db35c84f7611293cf45807203c883865a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652756"
---
# <a name="schedule-traces"></a><span data-ttu-id="af38f-102">예약된 추적</span><span class="sxs-lookup"><span data-stu-id="af38f-102">Schedule Traces</span></span>
  <span data-ttu-id="af38f-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에는 추적을 예약하는 두 가지 방법이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-103">There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af38f-104">다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-104">You can:</span></span>  
  
-   <span data-ttu-id="af38f-105">추적 중지 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-105">Enable a trace stop time.</span></span>  
  
-   <span data-ttu-id="af38f-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 추적을 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to schedule a trace.</span></span>  
  
## <a name="specifying-a-stop-time"></a><span data-ttu-id="af38f-107">중지 시간 지정</span><span class="sxs-lookup"><span data-stu-id="af38f-107">Specifying a Stop Time</span></span>  
 <span data-ttu-id="af38f-108">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저나 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하는 경우에는 추적 중지 시간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-108">You can specify a trace stop time if you use [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="af38f-109">추적이 원래 구성되어 있는 경우에는 중지 시간을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-109">The stop time must be set when the trace is originally configured.</span></span>  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a><span data-ttu-id="af38f-110">SQL Server 에이전트를 사용하여 추적 예약</span><span class="sxs-lookup"><span data-stu-id="af38f-110">Scheduling Traces by Using SQL Server Agent</span></span>  
 <span data-ttu-id="af38f-111">추적을 예약하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 추적을 시작한 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저인 **sp_trace_setstatus**나 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 중지 시간을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="af38f-111">The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="af38f-112">**추적 종료 시간 필터를 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="af38f-112">**To set an end time filter for a trace**</span></span>  
  
 [<span data-ttu-id="af38f-113">이벤트 종료 시간 기반의 이벤트 필터링&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="af38f-113">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [<span data-ttu-id="af38f-114">sp_trace_setstatus&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af38f-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="af38f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af38f-115">See Also</span></span>  
 [<span data-ttu-id="af38f-116">관리 태스크 자동화&#40;SQL Server 에이전트&#41;</span><span class="sxs-lookup"><span data-stu-id="af38f-116">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../../ssms/agent/sql-server-agent.md)  
  
  
