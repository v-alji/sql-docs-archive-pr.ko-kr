---
title: 재생 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65546f6820765286b558d2043e0155a79a07eb58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737239"
---
# <a name="replay-requirements"></a><span data-ttu-id="047c2-102">Replay Requirements</span><span class="sxs-lookup"><span data-stu-id="047c2-102">Replay Requirements</span></span>
  <span data-ttu-id="047c2-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 나 Distributed Replay Utility를 사용하여 추적 데이터를 재생하려면 특정 이벤트 클래스 및 열 집합이 추적에 캡처되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-103">In order to replay trace data with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or the Distributed Replay Utility, a specific set of event classes and columns must be captured in the trace.</span></span> <span data-ttu-id="047c2-104">**TSQL_Replay** 추적 템플릿을 사용하여 나중에 재생에 사용되도록 추적을 구성한 경우 이러한 설정이 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-104">These settings are enabled by default if the **TSQL_Replay** trace template is used to configure a trace that is later used for replay.</span></span> <span data-ttu-id="047c2-105">이 항목에서는 이러한 설정 및 기타 재생 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-105">This topic describes these settings and other replay requirements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="047c2-106">리소스를 많이 사용하는 OLTP 애플리케이션(활성 동시 연결 수가 많거나 처리량이 많음)을 재생하는 데는 Distributed Replay Utility를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-106">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="047c2-107">Distributed Replay Utility는 여러 컴퓨터의 추적 데이터를 재생할 수 있으므로 중요한 작업을 효율적으로 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-107">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="047c2-108">자세한 내용은 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="047c2-108">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="event-classes-required-for-replay"></a><span data-ttu-id="047c2-109">재생에 필요한 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="047c2-109">Event Classes Required for Replay</span></span>  
 <span data-ttu-id="047c2-110">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]가 데이터를 재생하려면 다음 이벤트 클래스 집합 및 모니터링하려는 기타 다른 이벤트 클래스가 추적에 캡처되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-110">To be replayed by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the following set of event classes, in addition to any other event classes you want to monitor, must be captured in the trace:</span></span>  
  
-   <span data-ttu-id="047c2-111">**CursorClose**(서버 쪽 커서를 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-111">**CursorClose (** only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="047c2-112">**CursorExecute** (서버 쪽 커서를 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-112">**CursorExecute** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="047c2-113">**CursorOpen** (서버 쪽 커서를 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-113">**CursorOpen** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="047c2-114">**CursorPrepare** (서버 쪽 커서를 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-114">**CursorPrepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="047c2-115">**CursorUnprepare** (서버 쪽 커서를 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-115">**CursorUnprepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="047c2-116">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="047c2-116">**Audit Login**</span></span>  
  
-   <span data-ttu-id="047c2-117">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="047c2-117">**Audit Logout**</span></span>  
  
-   <span data-ttu-id="047c2-118">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="047c2-118">**ExistingConnection**</span></span>  
  
-   <span data-ttu-id="047c2-119">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="047c2-119">**RPC Output Parameter**</span></span>  
  
-   <span data-ttu-id="047c2-120">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="047c2-120">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="047c2-121">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="047c2-121">**RPC:Starting**</span></span>  
  
-   <span data-ttu-id="047c2-122">**Exec Prepared SQL** (서버 쪽에서 준비한 SQL 문을 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-122">**Exec Prepared SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="047c2-123">**Prepare SQL** (서버 쪽에서 준비한 SQL 문을 재생할 때만 필요)</span><span class="sxs-lookup"><span data-stu-id="047c2-123">**Prepare SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="047c2-124">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="047c2-124">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="047c2-125">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="047c2-125">**SQL:BatchStarting**</span></span>  
  
## <a name="data-columns-required-for-replay"></a><span data-ttu-id="047c2-126">재생에 필요한 데이터 열</span><span class="sxs-lookup"><span data-stu-id="047c2-126">Data Columns Required for Replay</span></span>  
 <span data-ttu-id="047c2-127">추적을 재생하려면 캡처할 다른 데이터 열 외에도 다음 데이터 열을 추적에 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-127">In addition to any other data columns you want to capture, the following data columns must be captured in a trace to allow the trace to be replayed:</span></span>  
  
-   <span data-ttu-id="047c2-128">**Event Class**</span><span class="sxs-lookup"><span data-stu-id="047c2-128">**Event Class**</span></span>  
  
-   <span data-ttu-id="047c2-129">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="047c2-129">**EventSequence**</span></span>  
  
-   <span data-ttu-id="047c2-130">**TextData**</span><span class="sxs-lookup"><span data-stu-id="047c2-130">**TextData**</span></span>  
  
-   <span data-ttu-id="047c2-131">**애플리케이션 이름**</span><span class="sxs-lookup"><span data-stu-id="047c2-131">**Application Name**</span></span>  
  
-   <span data-ttu-id="047c2-132">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="047c2-132">**LoginName**</span></span>  
  
-   <span data-ttu-id="047c2-133">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="047c2-133">**DatabaseName**</span></span>  
  
-   <span data-ttu-id="047c2-134">**데이터베이스 ID**</span><span class="sxs-lookup"><span data-stu-id="047c2-134">**Database ID**</span></span>  
  
-   <span data-ttu-id="047c2-135">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="047c2-135">**ClientProcessID**</span></span>  
  
-   <span data-ttu-id="047c2-136">**HostName**</span><span class="sxs-lookup"><span data-stu-id="047c2-136">**HostName**</span></span>  
  
-   <span data-ttu-id="047c2-137">**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**</span><span class="sxs-lookup"><span data-stu-id="047c2-137">**ServerName**</span></span>  
  
-   <span data-ttu-id="047c2-138">**Binary Data**</span><span class="sxs-lookup"><span data-stu-id="047c2-138">**Binary Data**</span></span>  
  
-   <span data-ttu-id="047c2-139">**SPID**</span><span class="sxs-lookup"><span data-stu-id="047c2-139">**SPID**</span></span>  
  
-   <span data-ttu-id="047c2-140">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="047c2-140">**Start Time**</span></span>  
  
-   <span data-ttu-id="047c2-141">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="047c2-141">**EndTime**</span></span>  
  
-   <span data-ttu-id="047c2-142">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="047c2-142">**IsSystem**</span></span>  
  
-   <span data-ttu-id="047c2-143">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="047c2-143">**NTDomainName**</span></span>  
  
-   <span data-ttu-id="047c2-144">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="047c2-144">**NTUserName**</span></span>  
  
-   <span data-ttu-id="047c2-145">**오류**</span><span class="sxs-lookup"><span data-stu-id="047c2-145">**Error**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="047c2-146">재생용 데이터를 캡처하는 추적에는 **TSQL_Replay** 추적 템플릿을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="047c2-146">Use the trace template **TSQL_Replay** for traces that capture data for replay.</span></span>  
  
## <a name="other-replay-requirements"></a><span data-ttu-id="047c2-147">기타 재생 요구 사항</span><span class="sxs-lookup"><span data-stu-id="047c2-147">Other Replay Requirements</span></span>  
 <span data-ttu-id="047c2-148">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 재생할 때 필수 이벤트 및 열이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-148">In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], replay checks for the presence of required events and columns.</span></span> <span data-ttu-id="047c2-149">이와 같이 변경된 기능은 재생의 정확도를 높이고 필수 데이터가 누락된 경우 재생 문제 해결 과정에서 추측을 통해 작업을 수행하지 않도록 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-149">This change helps improve the accuracy of replay and takes the guesswork out of troubleshooting replay when required data is missing.</span></span> <span data-ttu-id="047c2-150">필수 데이터가 추적에 없을 경우 재생 시 오류가 반환되고 파일 재생이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-150">Replay returns an error and stops replaying a file when required data is missing from a trace.</span></span>  
  
 <span data-ttu-id="047c2-151">원래 추적한 서버(원본)가 아니라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되고 있는 서버(대상)에 대해 추적을 재생하려면 다음 조건이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-151">To replay a trace against a server (the target) on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running other than the server originally traced (the source), make sure the following has been done:</span></span>  
  
-   <span data-ttu-id="047c2-152">추적에 포함된 모든 로그인 및 사용자가 대상 및 원본과 같은 데이터베이스에서 이미 만들어져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-152">All logins and users contained in the trace must be created already on the target and in the same database as the source.</span></span>  
  
-   <span data-ttu-id="047c2-153">대상에 있는 모든 로그인 및 사용자는 원본에서 가진 권한과 같은 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-153">All logins and users in the target must have the same permissions they had in the source.</span></span>  
  
-   <span data-ttu-id="047c2-154">모든 로그인 암호는 재생을 실행하는 사용자의 로그인 암호와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-154">All login passwords must be the same as those of the user that executes the replay.</span></span>  
  
-   <span data-ttu-id="047c2-155">대상에 있는 데이터베이스 ID가 원본에 있는 데이터베이스 ID와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-155">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="047c2-156">그러나 두 ID가 서로 다르다면 **DatabaseName** 이 추적에 있을 경우 이를 기준으로 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-156">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="047c2-157">추적에 포함된 각 로그인의 기본 데이터베이스가 대상에서 로그인의 각 대상 데이터베이스로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-157">The default database for each login contained in the trace must be set (on the target) to the respective target database of the login.</span></span> <span data-ttu-id="047c2-158">예를 들어 재생할 추적은 원본에 있는 **Fred_Db**데이터베이스의 **Fred** 라는 로그인에 대한 동작을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-158">For example, the trace to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the source.</span></span> <span data-ttu-id="047c2-159">그러므로 대상에서 **Fred**로그인에 대한 기본 데이터베이스는 **Fred_Db** 와 일치하는 데이터베이스로 설정되어야 합니다. 데이터베이스 이름이 다르더라도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-159">Therefore, on the target, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="047c2-160">로그인의 기본 데이터베이스를 설정하려면 **sp_defaultdb** 시스템 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-160">To set the default database of the login, use the **sp_defaultdb** system stored procedure.</span></span>  
  
 <span data-ttu-id="047c2-161">누락되거나 잘못된 로그인과 연관된 이벤트를 재생하면 재생 오류가 발생하지만 재생 작업은 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="047c2-161">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
 <span data-ttu-id="047c2-162">추적 재생에 필요한 권한에 대한 자세한 내용은 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="047c2-162">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047c2-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="047c2-163">See Also</span></span>  
 <span data-ttu-id="047c2-164">[추적 테이블 재생&#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="047c2-164">[Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="047c2-165">[추적 파일 재생&#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="047c2-165">[Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="047c2-166">[SQL Server 이벤트 클래스 참조](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="047c2-166">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="047c2-167">[sp_defaultdb&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="047c2-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span></span>  
 [<span data-ttu-id="047c2-168">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="047c2-168">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
