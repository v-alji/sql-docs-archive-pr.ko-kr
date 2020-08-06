---
title: 추적 필터 설정(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47d797c84a05f50da026280f6e197f965d804426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652532"
---
# <a name="set-a-trace-filter-transact-sql"></a><span data-ttu-id="248ef-102">추적 필터 설정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="248ef-102">Set a Trace Filter (Transact-SQL)</span></span>
  <span data-ttu-id="248ef-103">이 항목에서는 추적 중인 이벤트에 필요한 정보만 검색하도록 필터를 만드는 데 저장 프로시저를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="248ef-103">This topic describes how to use stored procedures to create a filter that retrieves only the information you need on an event being traced.</span></span>  
  
### <a name="to-set-a-trace-filter"></a><span data-ttu-id="248ef-104">추적 필터를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="248ef-104">To set a trace filter</span></span>  
  
1.  <span data-ttu-id="248ef-105">추적이 이미 실행 중이면 **@status = 0**을 지정하고 **sp_trace_setstatus**를 실행하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="248ef-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="248ef-106">**sp_trace_setfilter** 를 실행하여 추적할 이벤트에서 검색할 정보 유형을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="248ef-106">Execute **sp_trace_setfilter** to configure the type of information to retrieve for the event being traced.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="248ef-107">일반적인 저장 프로시저와 달리 모든 저장 프로시저의 매개 변수 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (<strong>sp_trace_*xx*</strong>)는 엄격 하 게 형식화 되며 자동 데이터 형식 변환을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="248ef-107">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="248ef-108">이러한 매개 변수가 정확한 입력 매개 변수 데이터 형식으로 호출되지 않으면 인수 설명에서 지정한 대로 저장 프로시저는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="248ef-108">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure will return an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248ef-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="248ef-109">See Also</span></span>  
 <span data-ttu-id="248ef-110">[추적 필터링](../../relational-databases/sql-trace/filter-a-trace.md) </span><span class="sxs-lookup"><span data-stu-id="248ef-110">[Filter a Trace](../../relational-databases/sql-trace/filter-a-trace.md) </span></span>  
 <span data-ttu-id="248ef-111">[Transact-sql&#41;sp_trace_setfilter &#40;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="248ef-111">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 <span data-ttu-id="248ef-112">[Transact-sql&#41;sp_trace_setstatus &#40;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="248ef-112">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="248ef-113">[Transact-sql&#41;&#40;시스템 저장 프로시저](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="248ef-113">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="248ef-114">SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="248ef-114">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
