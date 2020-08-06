---
title: TRANSACT-SQL 저장 프로시저를 사용하여 추적 만들기 및 실행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2905ce2822598502ef6337d1a083fb6fde001c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652047"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a><span data-ttu-id="8de8a-102">TRANSACT-SQL 저장 프로시저를 사용하여 추적 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="8de8a-102">Create and Run Traces Using Transact-SQL Stored Procedures</span></span>
  <span data-ttu-id="8de8a-103">SQL 추적을 사용한 추적 프로세스는 추적을 만들고 실행하는 데 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용할지 아니면 시스템 저장 프로시저를 사용할지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-103">The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using system stored procedures.</span></span>  
  
 <span data-ttu-id="8de8a-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]대신 [!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 저장 프로시저를 사용하여 추적을 만들고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-104">As an alternative to [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create and run traces.</span></span> <span data-ttu-id="8de8a-105">시스템 저장 프로시저를 사용한 추적 프로세스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-105">The process of tracing by using system stored procedures is as follows:</span></span>  
  
1.  <span data-ttu-id="8de8a-106">**sp_trace_create**를 사용하여 추적을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-106">Create a trace by using **sp_trace_create**.</span></span>  
  
2.  <span data-ttu-id="8de8a-107">**sp_trace_setevent**를 사용하여 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-107">Add events with **sp_trace_setevent**.</span></span>  
  
3.  <span data-ttu-id="8de8a-108">(옵션) **sp_trace_setfilter**를 사용하여 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-108">(Optional) Set a filter with **sp_trace_setfilter**.</span></span>  
  
4.  <span data-ttu-id="8de8a-109">**sp_trace_setstatus**를 사용하여 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-109">Start the trace with **sp_trace_setstatus**.</span></span>  
  
5.  <span data-ttu-id="8de8a-110">**sp_trace_setstatus**를 사용하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-110">Stop the trace with **sp_trace_setstatus**.</span></span>  
  
6.  <span data-ttu-id="8de8a-111">**sp_trace_setstatus**를 사용하여 추적을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-111">Close the trace with **sp_trace_setstatus**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8de8a-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 저장 프로시저를 사용하여 서버 쪽 추적을 만들 경우 디스크에 공간이 있고 쓰기 오류가 발생하지 않는 한 이벤트가 손실되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-112">Using [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures creates a server-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur.</span></span> <span data-ttu-id="8de8a-113">디스크가 꽉 차거나 실패하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 계속 실행되지만 추적은 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-113">If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance continues to run, but tracing stops.</span></span> <span data-ttu-id="8de8a-114">**c2 audit mode** 가 설정되고 쓰기가 실패하는 경우 추적이 중지되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-114">If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span> <span data-ttu-id="8de8a-115">**c2 audit mode** 설정에 대한 자세한 내용은 [c2 audit mode 서버 구성 옵션](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8de8a-115">For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8de8a-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8de8a-116">In This Section</span></span>  
  
|<span data-ttu-id="8de8a-117">항목</span><span class="sxs-lookup"><span data-stu-id="8de8a-117">Topic</span></span>|<span data-ttu-id="8de8a-118">Description</span><span class="sxs-lookup"><span data-stu-id="8de8a-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8de8a-119">SQL 추적 최적화</span><span class="sxs-lookup"><span data-stu-id="8de8a-119">Optimize SQL Trace</span></span>](sql-trace.md)|<span data-ttu-id="8de8a-120">추적이 시스템 성능에 미치는 영향을 줄이는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-120">Contains information about ways you can reduce the effects of tracing on system performance.</span></span>|  
|[<span data-ttu-id="8de8a-121">추적 필터링</span><span class="sxs-lookup"><span data-stu-id="8de8a-121">Filter a Trace</span></span>](filter-a-trace.md)|<span data-ttu-id="8de8a-122">추적에 필터를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-122">Contains information about using filters for tracing.</span></span>|  
|[<span data-ttu-id="8de8a-123">추적 파일 및 테이블 크기 제한</span><span class="sxs-lookup"><span data-stu-id="8de8a-123">Limit Trace File and Table Sizes</span></span>](limit-trace-file-and-table-sizes.md)|<span data-ttu-id="8de8a-124">추적 데이터가 기록되는 파일 및 테이블의 크기를 제한하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-124">Contains information about how to limit the size of files and tables where trace data is written.</span></span> <span data-ttu-id="8de8a-125">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서만 테이블에 추적 정보를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-125">Note that only [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can write trace information to tables.</span></span>|  
|[<span data-ttu-id="8de8a-126">예약된 추적</span><span class="sxs-lookup"><span data-stu-id="8de8a-126">Schedule Traces</span></span>](schedule-traces.md)|<span data-ttu-id="8de8a-127">추적 시작 시간 및 종료 시간을 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8de8a-127">Contains information about how to set the start time and the end time for tracing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8de8a-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8de8a-128">See Also</span></span>  
 <span data-ttu-id="8de8a-129">[sp_trace_create&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8de8a-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="8de8a-130">[sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8de8a-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="8de8a-131">[sp_trace_setfilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8de8a-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 [<span data-ttu-id="8de8a-132">sp_trace_setstatus&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8de8a-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
  
