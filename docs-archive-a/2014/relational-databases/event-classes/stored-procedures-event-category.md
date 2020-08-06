---
title: Stored Procedures 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
ms.openlocfilehash: df2e0d9a4c077ff16eba09bc5ebb6447d5d27595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743287"
---
# <a name="stored-procedures-event-category"></a><span data-ttu-id="5b8b3-102">Stored Procedures 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="5b8b3-102">Stored Procedures Event Category</span></span>
  <span data-ttu-id="5b8b3-103">**Stored Procedures** 이벤트 범주는 일반 저장 프로시저 이벤트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-103">The **Stored Procedures** event category contains general stored procedure events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b8b3-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5b8b3-104">In This Section</span></span>  
  
|<span data-ttu-id="5b8b3-105">항목</span><span class="sxs-lookup"><span data-stu-id="5b8b3-105">Topic</span></span>|<span data-ttu-id="5b8b3-106">Description</span><span class="sxs-lookup"><span data-stu-id="5b8b3-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5b8b3-107">RPC:Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-107">RPC:Completed Event Class</span></span>](rpc-completed-event-class.md)|<span data-ttu-id="5b8b3-108">RPC(원격 프로시저 호출)가 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-108">Indicates that a remote procedure call (RPC) has been completed.</span></span>|  
|[<span data-ttu-id="5b8b3-109">PreConnect:Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-109">PreConnect:Completed Event Class</span></span>](preconnect-completed-event-class.md)|<span data-ttu-id="5b8b3-110">리소스 관리자의 분류자 함수가 실행을 완료하는 때를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-110">Indicates when the Resource Governor classifier function finishes execution.</span></span>|  
|[<span data-ttu-id="5b8b3-111">PreConnect:Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-111">PreConnect:Starting Event Class</span></span>](preconnect-starting-event-class.md)|<span data-ttu-id="5b8b3-112">리소스 관리자의 분류자 함수가 실행을 시작하는 때를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-112">Indicates when the Resource Governor classifier function starts execution.</span></span>|  
|[<span data-ttu-id="5b8b3-113">RPC Output Parameter 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-113">RPC Output Parameter Event Class</span></span>](rpc-output-parameter-event-class.md)|<span data-ttu-id="5b8b3-114">실행 후 원격 프로시저 호출의 출력 매개 변수 값을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-114">Traces the output parameter values of remote procedure calls after execution.</span></span>|  
|[<span data-ttu-id="5b8b3-115">RPC:Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-115">RPC:Starting Event Class</span></span>](rpc-starting-event-class.md)|<span data-ttu-id="5b8b3-116">원격 프로시저 호출을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-116">Indicates that a remote procedure call is starting.</span></span>|  
|[<span data-ttu-id="5b8b3-117">SP:CacheHit 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-117">SP:CacheHit Event Class</span></span>](sp-cachehit-event-class.md)|<span data-ttu-id="5b8b3-118">저장 프로시저가 캐시에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-118">Indicates that the stored procedure is in the cache.</span></span>|  
|[<span data-ttu-id="5b8b3-119">SP:CacheInsert 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-119">SP:CacheInsert Event Class</span></span>](sp-cacheinsert-event-class.md)|<span data-ttu-id="5b8b3-120">저장 프로시저를 캐시로 가져왔음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-120">Indicates that the stored procedure has been brought into the cache.</span></span>|  
|[<span data-ttu-id="5b8b3-121">SP:CacheMiss 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-121">SP:CacheMiss Event Class</span></span>](sp-cachemiss-event-class.md)|<span data-ttu-id="5b8b3-122">저장 프로시저가 캐시에 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-122">Indicates that the stored procedure was not found in the cache.</span></span>|  
|[<span data-ttu-id="5b8b3-123">SP:CacheRemove 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-123">SP:CacheRemove Event Class</span></span>](sp-cacheremove-event-class.md)|<span data-ttu-id="5b8b3-124">저장 프로시저가 캐시에서 제거되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-124">Indicates that the stored procedure has been removed from the cache.</span></span>|  
|[<span data-ttu-id="5b8b3-125">SP:Completed 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-125">SP:Completed Event Class</span></span>](sp-completed-event-class.md)|<span data-ttu-id="5b8b3-126">저장 프로시저 실행이 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-126">Indicates that execution of the stored procedure has completed.</span></span>|  
|[<span data-ttu-id="5b8b3-127">SP:Recompile 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-127">SP:Recompile Event Class</span></span>](sp-recompile-event-class.md)|<span data-ttu-id="5b8b3-128">저장 프로시저가 다시 컴파일되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-128">Indicates that the stored procedure has been recompiled.</span></span>|  
|[<span data-ttu-id="5b8b3-129">SP:Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-129">SP:Starting Event Class</span></span>](sp-starting-event-class.md)|<span data-ttu-id="5b8b3-130">저장 프로시저 실행을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-130">Indicates that execution of the stored procedure is starting.</span></span>|  
|[<span data-ttu-id="5b8b3-131">SP:StmtCompleted 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-131">SP:StmtCompleted Event Class</span></span>](sp-stmtcompleted-event-class.md)|<span data-ttu-id="5b8b3-132">저장 프로시저 내의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 완료했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-132">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has completed.</span></span>|  
|[<span data-ttu-id="5b8b3-133">SP:StmtStarting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="5b8b3-133">SP:StmtStarting Event Class</span></span>](sp-stmtstarting-event-class.md)|<span data-ttu-id="5b8b3-134">저장 프로시저 내의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b8b3-134">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has started.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b8b3-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b8b3-135">See Also</span></span>  
 <span data-ttu-id="5b8b3-136">[확장 이벤트](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="5b8b3-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="5b8b3-137">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b8b3-137">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
