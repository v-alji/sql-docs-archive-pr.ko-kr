---
title: 기존 추적 수정(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55b8172ef8e6188059c484ab41f1a719e0e9f8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646838"
---
# <a name="modify-an-existing-trace-transact-sql"></a><span data-ttu-id="10f7d-102">기존 추적 수정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="10f7d-102">Modify an Existing Trace (Transact-SQL)</span></span>
  <span data-ttu-id="10f7d-103">이 항목에서는 저장 프로시저를 사용하여 기존 추적을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-103">This topic describes how to use stored procedures to modify an existing trace.</span></span>  
  
### <a name="to-modify-an-existing-trace"></a><span data-ttu-id="10f7d-104">기존 추적을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="10f7d-104">To modify an existing trace</span></span>  
  
1.  <span data-ttu-id="10f7d-105">추적이 이미 실행 중이면 **@status = 0**을 지정하고 **sp_trace_setstatus**를 실행하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-105">If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="10f7d-106">추적 이벤트를 수정하려면 매개 변수를 통해 변경 내용을 지정하는 **sp_trace_setevent** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-106">To modify trace events, execute **sp_trace_setevent** by specifying the changes through the parameters.</span></span> <span data-ttu-id="10f7d-107">순서대로 나열된 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-107">Listed in order, the parameters are:</span></span>  
  
    -   <span data-ttu-id="10f7d-108">**@traceid**(추적 ID)</span><span class="sxs-lookup"><span data-stu-id="10f7d-108">**@traceid** (Trace ID)</span></span>  
  
    -   <span data-ttu-id="10f7d-109">**@eventid**(이벤트 ID)</span><span class="sxs-lookup"><span data-stu-id="10f7d-109">**@eventid** (Event ID)</span></span>  
  
    -   <span data-ttu-id="10f7d-110">**@columnid**(열 ID)</span><span class="sxs-lookup"><span data-stu-id="10f7d-110">**@columnid** (Column ID)</span></span>  
  
    -   <span data-ttu-id="10f7d-111">**@on**SIGN-ON</span><span class="sxs-lookup"><span data-stu-id="10f7d-111">**@on** (ON)</span></span>  
  
     <span data-ttu-id="10f7d-112">매개 변수를 수정할 때 **@on** 매개 변수와의 상호 작용을 염두에 두어야 합니다 **@columnid** .</span><span class="sxs-lookup"><span data-stu-id="10f7d-112">When you modify the **@on** parameter, keep in mind its interaction with the **@columnid** parameter:</span></span>  
  
    |<span data-ttu-id="10f7d-113">켜기</span><span class="sxs-lookup"><span data-stu-id="10f7d-113">ON</span></span>|<span data-ttu-id="10f7d-114">열 ID</span><span class="sxs-lookup"><span data-stu-id="10f7d-114">Column ID</span></span>|<span data-ttu-id="10f7d-115">결과</span><span class="sxs-lookup"><span data-stu-id="10f7d-115">Result</span></span>|  
    |--------|---------------|------------|  
    |<span data-ttu-id="10f7d-116">ON(**1**)</span><span class="sxs-lookup"><span data-stu-id="10f7d-116">ON (**1**)</span></span>|<span data-ttu-id="10f7d-117">NULL</span><span class="sxs-lookup"><span data-stu-id="10f7d-117">NULL</span></span>|<span data-ttu-id="10f7d-118">이벤트가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-118">Event is turned on.</span></span> <span data-ttu-id="10f7d-119">모든 열이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-119">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="10f7d-120">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="10f7d-120">NOT NULL</span></span>|<span data-ttu-id="10f7d-121">지정된 이벤트에 대해 열이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-121">Column is turned on for the specified event.</span></span>|  
    |<span data-ttu-id="10f7d-122">OFF(**0**)</span><span class="sxs-lookup"><span data-stu-id="10f7d-122">OFF (**0**)</span></span>|<span data-ttu-id="10f7d-123">NULL</span><span class="sxs-lookup"><span data-stu-id="10f7d-123">NULL</span></span>|<span data-ttu-id="10f7d-124">이벤트가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-124">Event is turned off.</span></span> <span data-ttu-id="10f7d-125">모든 열이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-125">All columns are cleared.</span></span>|  
    ||<span data-ttu-id="10f7d-126">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="10f7d-126">NOT NULL</span></span>|<span data-ttu-id="10f7d-127">지정된 이벤트에 대해 열이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-127">Column is turned off for the specified event.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="10f7d-128">일반적인 저장 프로시저와 달리 모든 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 저장 프로시저의 매개 변수(<strong>sp_trace_*xx*</strong>)는 정확하게 입력해야 하며 데이터 형식 자동 변환을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-128">Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="10f7d-129">이러한 매개 변수를 인수 설명에 지정된 올바른 입력 매개 변수 데이터 형식으로 호출하지 않으면 저장 프로시저가 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="10f7d-129">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  

## <a name="see-also"></a><span data-ttu-id="10f7d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10f7d-130">See Also</span></span>  
 <span data-ttu-id="10f7d-131">[sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="10f7d-131">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="10f7d-132">[sp_trace_setstatus&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="10f7d-132">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="10f7d-133">[시스템 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="10f7d-133">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="10f7d-134">SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="10f7d-134">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
