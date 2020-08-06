---
title: SQL 추적 최적화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 831875218423bdb9106d7d84995af1e788da44db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646835"
---
# <a name="optimize-sql-trace"></a><span data-ttu-id="460b1-102">SQL 추적 최적화</span><span class="sxs-lookup"><span data-stu-id="460b1-102">Optimize SQL Trace</span></span>
  <span data-ttu-id="460b1-103">SQL 추적을 실행하면 데이터 수집을 위해 시스템 리소스가 사용되기 때문에 성능 비용이 발생하지만 여러 가지 방법으로 이 비용을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-103">Although running SQL Trace incurs a performance cost because it uses system resources to gather data, you can do many things to minimize it.</span></span> <span data-ttu-id="460b1-104">추적으로 인한 성능 비용을 최적화하려면 다음을 시도하십시오.</span><span class="sxs-lookup"><span data-stu-id="460b1-104">To minimize the performance cost incurred by a trace, try the following:</span></span>  
  
-   <span data-ttu-id="460b1-105">명령 프롬프트를 사용하여 추적을 실행해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-105">Consider using the command prompt to run traces.</span></span> <span data-ttu-id="460b1-106">그래픽 사용자 인터페이스를 사용하면 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-106">Using a graphical user interface hinders performance.</span></span> <span data-ttu-id="460b1-107">자세한 내용은 [sp_trace_create&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="460b1-107">For more information, see [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql).</span></span>  
  
-   <span data-ttu-id="460b1-108">자주 발생하는 이벤트를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-108">Avoid including events that occur frequently.</span></span> <span data-ttu-id="460b1-109">가능하면 특정 이벤트 클래스와 필터를 사용하여 추적 범위를 좁힙니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-109">If possible, narrow your trace by means of specific event classes and filters.</span></span> <span data-ttu-id="460b1-110">수집하는 추적 이벤트가 적을수록 추적 지원에 필요한 시스템 리소스가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-110">If fewer trace events are gathered, fewer system resources are required to support tracing.</span></span>  
  
-   <span data-ttu-id="460b1-111">추적에 포커스를 맞추어 관련 데이터를 제공하는 이벤트만 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-111">Focus the trace to collect only events that provide relevant data.</span></span> <span data-ttu-id="460b1-112">예를 들어 추적에서 교착 상태를 식별하려면 **Lock:Deadlock** 이벤트 클래스를 포함하고 **Lock:Acquired** 이벤트 클래스는 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-112">For example, if your trace is to identify deadlocks, include the **Lock:Deadlock** event class, but not the **Lock:Acquired** event class.</span></span> <span data-ttu-id="460b1-113">두 이벤트 클래스를 모두 포함하면 추적이 획득한 잠금에 모두 응답해야 하므로 실행 비용은 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-113">If you include both event classes, the trace has to respond to every lock that is acquired, and your execution cost is doubled.</span></span>  
  
-   <span data-ttu-id="460b1-114">중복 데이터를 수집하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-114">Avoid collecting duplicate data.</span></span> <span data-ttu-id="460b1-115">예를 들어 **SQL:BatchStarted** 와 **SQL:BatchCompleted**를 수집할 경우 **SQL:BatchStarted** 이벤트 클래스의 텍스트 데이터만 수집하여 결과 집합 크기를 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-115">For example, if you collect **SQL:BatchStarted** and the **SQL:BatchCompleted**, you can minimize the size of the results set by collecting text data for the **SQL:BatchStarted** event class only.</span></span>  
  
-   <span data-ttu-id="460b1-116">추적 정의에 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-116">Use filters in the trace definition.</span></span> <span data-ttu-id="460b1-117">예를 들어 특정 사용자가 임시 쿼리를 수행하는 동안 성능이 느려지면 **LoginName**에 필터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-117">For example, if you know that a certain user is reporting slow performance during ad hoc queries, create a filter on **LoginName**.</span></span> <span data-ttu-id="460b1-118">필터를 설정하여 **LoginName** 이 해당 사용자 이름과 일치하는 이벤트만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-118">Set the filter to include only events where the **LoginName** matches that user name.</span></span>  
  
 <span data-ttu-id="460b1-119">성능에 크게 영향을 미치는 이벤트를 추적해야 할 경우 다음 방법 중 하나를 사용하여 서버에 대한 성능 영향을 제한하십시오.</span><span class="sxs-lookup"><span data-stu-id="460b1-119">If you need to run a trace for events that create a significant impact on performance, consider limiting the performance impact on the server by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="460b1-120">단기간에 추적을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-120">Run traces for shorter periods of time.</span></span> <span data-ttu-id="460b1-121">중지 시간을 설정하여 추적이 실행되는 시간을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-121">You can control the length of time that a trace runs by enabling a stop time.</span></span> <span data-ttu-id="460b1-122">이벤트 클래스를 제한하거나 이벤트를 필터링할 수 없을 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-122">This is especially important if you cannot limit the event classes or filter an event.</span></span> <span data-ttu-id="460b1-123">중지 시간을 설정하면 성능 저하를 멈출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-123">Enabling a stop time ensures that the performance incurred does not last indefinitely.</span></span>  
  
-   <span data-ttu-id="460b1-124">추적 결과의 크기를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-124">Limit the size of the trace results.</span></span> <span data-ttu-id="460b1-125">추적 결과의 크기를 최대 파일 크기로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-125">You can limit the size of the trace results to a maximum file size.</span></span> <span data-ttu-id="460b1-126">이렇게 하면 파일 크기 제한에 도달했을 때 성능 비용이 중지됩니다(파일 롤오버를 사용하지 않는 경우).</span><span class="sxs-lookup"><span data-stu-id="460b1-126">This strategy ensures that the performance cost stops when the file-size limit is reached (if file rollover is not enabled).</span></span>  
  
-   <span data-ttu-id="460b1-127">반환되는 이벤트의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-127">Limit the number of events returned.</span></span> <span data-ttu-id="460b1-128">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 를 사용하면 추적을 테이블에 저장하고 최대 행 개수를 설정하여 반환되는 이벤트의 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-128">With [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] you can limit the number of events returned by saving the trace to a table and setting the maximum number of rows.</span></span> <span data-ttu-id="460b1-129">최대 행 개수에 도달한 후에도 추적 결과가 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 화면에 반환되지만 테이블에 결과를 기록하는 데 필요한 비용이 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="460b1-129">Trace results are still returned to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] screen after the maximum number of rows has been reached, but the cost of recording the results to a table is eliminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460b1-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="460b1-130">See Also</span></span>  
 [<span data-ttu-id="460b1-131">추적 필터링</span><span class="sxs-lookup"><span data-stu-id="460b1-131">Filter a Trace</span></span>](../sql-trace/filter-a-trace.md)  
  
  
