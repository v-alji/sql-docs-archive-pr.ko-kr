---
title: 저장 프로시저를 사용하여 수동 추적 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652045"
---
# <a name="create-manual-traces-using-stored-procedures"></a><span data-ttu-id="8069f-102">저장 프로시저를 사용하여 수동 추적 만들기</span><span class="sxs-lookup"><span data-stu-id="8069f-102">Create Manual Traces using Stored Procedures</span></span>
  <span data-ttu-id="8069f-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 인스턴스에 대한 추적을 만들 수 있는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]시스템 저장 프로시저를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="8069f-104">이 시스템 저장 프로시저를 사용자의 애플리케이션에서 사용하면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하지 않고 추적을 수동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-104">These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="8069f-105">따라서 각 사용자 조직의 필요에 따라 사용자 지정 애플리케이션을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-105">This allows you to write custom applications specific to the needs of your enterprise.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8069f-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8069f-106">In This Section</span></span>  
 <span data-ttu-id="8069f-107">다음 표에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스 추적을 위한 시스템 저장 프로시저를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-107">The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
|<span data-ttu-id="8069f-108">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="8069f-108">Stored procedure</span></span>|<span data-ttu-id="8069f-109">수행된 태스크</span><span class="sxs-lookup"><span data-stu-id="8069f-109">Task performed</span></span>|  
|----------------------|--------------------|  
|[<span data-ttu-id="8069f-110">sys.fn_trace_geteventinfo&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|<span data-ttu-id="8069f-111">추적에 포함된 이벤트에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-111">Returns information about events included in a trace.</span></span>|  
|[<span data-ttu-id="8069f-112">sys.fn_trace_getinfo&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-112">sys.fn_trace_getinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|<span data-ttu-id="8069f-113">지정한 추적이나 모든 기존 추적에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-113">Returns information about a specified trace or all existing traces.</span></span>|  
|[<span data-ttu-id="8069f-114">sp_trace_create&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-114">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|<span data-ttu-id="8069f-115">추적 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-115">Creates a trace definition.</span></span> <span data-ttu-id="8069f-116">새 추적은 중지된 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-116">The new trace will be in a stopped state.</span></span>|  
|[<span data-ttu-id="8069f-117">sp_trace_generateevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|<span data-ttu-id="8069f-118">사용자 정의 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-118">Creates a user-defined event.</span></span>|  
|[<span data-ttu-id="8069f-119">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-119">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|<span data-ttu-id="8069f-120">추적에서 이벤트 클래스나 데이터 열을 추가 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-120">Adds an event class or data column to a trace, or removes one from it.</span></span>|  
|[<span data-ttu-id="8069f-121">sp_trace_setstatus&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|<span data-ttu-id="8069f-122">추적을 시작, 중지 또는 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-122">Starts, stops, or closes a trace.</span></span>|  
|[<span data-ttu-id="8069f-123">sys.fn_trace_getfilterinfo&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|<span data-ttu-id="8069f-124">추적에 적용되는 필터에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-124">Returns information about filters applied to a trace.</span></span>|  
|[<span data-ttu-id="8069f-125">sp_trace_setfilter&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8069f-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|<span data-ttu-id="8069f-126">추적에 새 필터 또는 수정된 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-126">Applies a new or modified filter to a trace.</span></span>|  
  
 <span data-ttu-id="8069f-127">**저장 프로시저를 사용하여 사용자가 소유한 추적을 정의하려면**</span><span class="sxs-lookup"><span data-stu-id="8069f-127">**To define your own trace using stored procedures**</span></span>  
  
1.  <span data-ttu-id="8069f-128">**sp_trace_setevent**로 캡처할 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-128">Specify the events to capture using **sp_trace_setevent**.</span></span>  
  
2.  <span data-ttu-id="8069f-129">이벤트 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-129">Specify any event filters.</span></span> <span data-ttu-id="8069f-130">자세한 내용은 [추적 필터 설정&#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8069f-130">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).</span></span>  
  
3.  <span data-ttu-id="8069f-131">**sp_trace_create**로 캡처된 이벤트 데이터에 대한 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8069f-131">Specify the destination for the captured event data using **sp_trace_create**.</span></span>  
  
 <span data-ttu-id="8069f-132">추적 저장 프로시저 사용에 대한 예는 [추적 만들기&#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8069f-132">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
 <span data-ttu-id="8069f-133">**추적 정의 기본값 설정**</span><span class="sxs-lookup"><span data-stu-id="8069f-133">**To set trace definition defaults**</span></span>  
  
 [<span data-ttu-id="8069f-134">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8069f-134">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 <span data-ttu-id="8069f-135">**추적 표시 기본값 설정**</span><span class="sxs-lookup"><span data-stu-id="8069f-135">**To set trace display defaults**</span></span>  
  
 [<span data-ttu-id="8069f-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8069f-136">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="8069f-137">**추적 만들기**</span><span class="sxs-lookup"><span data-stu-id="8069f-137">**To create a trace**</span></span>  
  
 [<span data-ttu-id="8069f-138">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8069f-138">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [<span data-ttu-id="8069f-139">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8069f-139">Transact-SQL</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
 <span data-ttu-id="8069f-140">**추적 템플릿에서 이벤트 추가 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="8069f-140">**To add or remove events from a trace template**</span></span>  
  
 [<span data-ttu-id="8069f-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8069f-141">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="8069f-142">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8069f-142">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
