---
title: Errors and Warnings 이벤트 범주(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
ms.openlocfilehash: d55f37f5401f60ddfeec340af1ae6d532eb6ad01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735232"
---
# <a name="errors-and-warnings-event-category-database-engine"></a><span data-ttu-id="1fe74-102">Errors and Warnings 이벤트 범주(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="1fe74-102">Errors and Warnings Event Category (Database Engine)</span></span>
  <span data-ttu-id="1fe74-103">**Errors and Warnings** 이벤트 범주에는 일반적인 오류 및 경고 이벤트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-103">The **Errors and Warnings** event category contains general error and warning events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fe74-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1fe74-104">In This Section</span></span>  
  
|<span data-ttu-id="1fe74-105">항목</span><span class="sxs-lookup"><span data-stu-id="1fe74-105">Topic</span></span>|<span data-ttu-id="1fe74-106">Description</span><span class="sxs-lookup"><span data-stu-id="1fe74-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1fe74-107">Attention 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-107">Attention Event Class</span></span>](attention-event-class.md)|<span data-ttu-id="1fe74-108">**Attention** 이벤트가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-108">Indicates that an **Attention** event has occurred.</span></span>|  
|[<span data-ttu-id="1fe74-109">Background Job Error 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-109">Background Job Error Event Class</span></span>](background-job-error-event-class.md)|<span data-ttu-id="1fe74-110">백그라운드 작업이 비정상적으로 종료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-110">Indicates that a background job has terminated abnormally.</span></span>|  
|[<span data-ttu-id="1fe74-111">Bitmap Warning 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-111">Bitmap Warning Event Class</span></span>](bitmap-warning-event-class.md)|<span data-ttu-id="1fe74-112">쿼리에서 비트맵 필터링을 사용하지 않도록 설정했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-112">Indicates that bitmap filtering has been disabled in a query.</span></span>|  
|[<span data-ttu-id="1fe74-113">Blocked Process Report 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-113">Blocked Process Report Event Class</span></span>](blocked-process-report-event-class.md)|<span data-ttu-id="1fe74-114">지정된 기간보다 그 이상으로 태스크가 차단되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-114">Indicates that a task has been blocked for more than a specified amount of time.</span></span>|  
|[<span data-ttu-id="1fe74-115">CPU Threshold Exceeded 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-115">CPU Threshold Exceeded Event Class</span></span>](cpu-threshold-exceeded-event-class.md)|<span data-ttu-id="1fe74-116">리소스 관리자가 지정된 CPU 임계값을 초과하는 쿼리를 감지했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-116">Indicates that the Resource Governor detects a query that exceeds the specified CPU threshold.</span></span>|  
|[<span data-ttu-id="1fe74-117">ErrorLog 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-117">ErrorLog Event Class</span></span>](errorlog-event-class.md)|<span data-ttu-id="1fe74-118">오류 이벤트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 기록되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-118">Indicates that error events have been logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>|  
|[<span data-ttu-id="1fe74-119">EventLog 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-119">EventLog Event Class</span></span>](eventlog-event-class.md)|<span data-ttu-id="1fe74-120">이벤트가 Windows 이벤트 로그에 기록되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-120">Indicates that events have been logged in the Windows event log.</span></span>|  
|[<span data-ttu-id="1fe74-121">Exception 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-121">Exception Event Class</span></span>](exception-event-class.md)|<span data-ttu-id="1fe74-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 예외가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-122">Indicates that an exception has occurred in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="1fe74-123">Exchange Spill 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-123">Exchange Spill Event Class</span></span>](exchange-spill-event-class.md)|<span data-ttu-id="1fe74-124">병렬 쿼리 계획의 통신 버퍼가 tempdb 데이터베이스에 기록되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-124">Indicates that communication buffers in a parallel query plan have been written to the tempdb database.</span></span>|  
|[<span data-ttu-id="1fe74-125">Execution Warnings 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-125">Execution Warnings Event Class</span></span>](execution-warnings-event-class.md)|<span data-ttu-id="1fe74-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문이나 저장 프로시저 실행 중에 메모리 부여 경고가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-126">Indicates that memory grant warnings occurred during the execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statement or stored procedure.</span></span>|  
|[<span data-ttu-id="1fe74-127">Hash Warning 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-127">Hash Warning Event Class</span></span>](hash-warning-event-class.md)|<span data-ttu-id="1fe74-128">해시 연산 중 해시 재귀 또는 해시 재귀 한도 초과가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-128">Indicates that a hash recursion or hash bailout has occurred during a hashing operation.</span></span>|  
|[<span data-ttu-id="1fe74-129">Missing Column Statistics 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-129">Missing Column Statistics Event Class</span></span>](missing-column-statistics-event-class.md)|<span data-ttu-id="1fe74-130">최적화 프로그램에 유용한 열 통계를 사용할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-130">Indicates that column statistics that could have been useful for the optimizer are not available.</span></span>|  
|[<span data-ttu-id="1fe74-131">Missing Join Predicate 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-131">Missing Join Predicate Event Class</span></span>](missing-join-predicate-event-class.md)|<span data-ttu-id="1fe74-132">조인 조건자가 없는 쿼리가 실행되고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-132">Indicates that a query is being executed that has no join predicate.</span></span>|  
|[<span data-ttu-id="1fe74-133">Sort Warnings 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-133">Sort Warnings Event Class</span></span>](sort-warnings-event-class.md)|<span data-ttu-id="1fe74-134">정렬 작업이 메모리에 적합하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-134">Indicates that sort operations do not fit into memory.</span></span>|  
|[<span data-ttu-id="1fe74-135">User Error Message 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="1fe74-135">User Error Message Event Class</span></span>](user-error-message-event-class.md)|<span data-ttu-id="1fe74-136">사용자에게 표시되는 오류 메시지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1fe74-136">Displays error messages that are seen by the user.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fe74-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1fe74-137">See Also</span></span>  
 [<span data-ttu-id="1fe74-138">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fe74-138">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
