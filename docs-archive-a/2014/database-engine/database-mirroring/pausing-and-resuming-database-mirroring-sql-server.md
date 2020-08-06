---
title: 데이터베이스 미러링 일시 중지 및 재개(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- resuming database mirroring
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: c67802c6-ee8c-4cbd-a6d4-f7b80413a4ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c231876b11303992e0e3300c9cb73c0cf53b3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733112"
---
# <a name="pausing-and-resuming-database-mirroring-sql-server"></a><span data-ttu-id="f353d-102">데이터베이스 미러링 일시 중지 및 재개(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f353d-102">Pausing and Resuming Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="f353d-103">데이터베이스 소유자는 데이터베이스 미러링 세션을 일시 중지하고 나중에 언제든지 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-103">The database owner can pause and later resume a database mirroring session at any time.</span></span> <span data-ttu-id="f353d-104">일시 중지하면 미러링을 일시 중지하는 동안 세션 상태가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-104">Pausing preserves the session state while suspending mirroring.</span></span> <span data-ttu-id="f353d-105">병목 상태에서 일시 중지는 주 서버의 성능을 높이는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-105">During bottlenecks, pausing might be useful to improve performance on the principal server.</span></span>  
  
 <span data-ttu-id="f353d-106">세션을 일시 중지한 상태에서도 주 데이터베이스는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-106">When a session is paused, the principal database remains available.</span></span> <span data-ttu-id="f353d-107">세션을 일시 중지하면 미러링 세션의 상태가 SUSPENDED로 설정되고 미러 데이터베이스가 주 데이터베이스보다 뒤쳐지므로 노출된 상태로 주 데이터베이스가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-107">Pausing sets the state of the mirroring session to SUSPENDED, and the mirror database no longer keeps up with the principal database, causing the principal database to run exposed.</span></span>  
  
 <span data-ttu-id="f353d-108">일시 중지된 세션을 빨리 재개하는 것이 좋습니다. 데이터베이스 미러링 세션이 일시 중지된 동안에는 트랜잭션 로그를 자를 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="f353d-108">We recommend that you resume a paused session quickly, because as long as a database mirroring session remains paused, the transaction log cannot be truncated.</span></span> <span data-ttu-id="f353d-109">데이터베이스 미러링 세션을 너무 오래 일시 중지하면 트랜잭션 로그가 꽉 차서 데이터베이스를 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-109">Therefore, if a database mirroring session is paused for too long, the transaction log fills up, making the database unavailable.</span></span> <span data-ttu-id="f353d-110">이렇게 되는 이유에 대한 자세한 내용은 뒤에 나오는 "로그 잘림에 대한 일시 중지 및 재개의 영향"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f353d-110">For an explanation of why this happens, see "How Pausing and Resuming Affect Log Truncation," later in this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f353d-111">강제 서비스에 따라 원래 주 서버가 다시 연결되면 미러링이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-111">Following a forced service, when the original principal server reconnects mirroring is suspended.</span></span> <span data-ttu-id="f353d-112">이 경우 미러링을 재개하면 원래 주 서버의 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-112">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="f353d-113">데이터 손실 위험을 관리하는 방법은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f353d-113">For information about managing the potential data loss, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="f353d-114">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="f353d-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="f353d-115">로그 잘림에 대한 일시 중지 및 재개의 영향</span><span class="sxs-lookup"><span data-stu-id="f353d-115">How Pausing and Resuming Affect Log Truncation</span></span>](#EffectOnLogTrunc)  
  
-   [<span data-ttu-id="f353d-116">꽉 찬 트랜잭션 로그 방지</span><span class="sxs-lookup"><span data-stu-id="f353d-116">Avoid a Full Transaction Log</span></span>](#AvoidFullLog)  
  
-   [<span data-ttu-id="f353d-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f353d-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="how-pausing-and-resuming-affect-log-truncation"></a><a name="EffectOnLogTrunc"></a> <span data-ttu-id="f353d-118">로그 잘림에 대한 일시 중지 및 재개의 영향</span><span class="sxs-lookup"><span data-stu-id="f353d-118">How Pausing and Resuming Affect Log Truncation</span></span>  
 <span data-ttu-id="f353d-119">일반적으로 데이터베이스에서 자동 검사점을 수행하면 다음 로그 백업 이후 해당 트랜잭션 로그가 이 검사점까지 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-119">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="f353d-120">데이터베이스 미러링 세션이 일시 중지된 동안에는 주 서버가 현재 로그 레코드를 미러 서버로 보내기 위해 대기 중이므로 모두 활성 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-120">While a database mirroring session remains paused, all of the current log records remain active because the principal server is waiting to send them to the mirror server.</span></span> <span data-ttu-id="f353d-121">보내지 않은 로그 레코드는 세션이 재개되어 주 서버에서 해당 로그 레코드를 미러 서버로 보낼 때까지 주 데이터베이스의 트랜잭션 로그에 누적됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-121">The unsent log records accumulate in the transaction log of the principal database until the session resumes and the principal server has sent the log records to the mirror server.</span></span>  
  
 <span data-ttu-id="f353d-122">세션이 재개되면 주 서버에서 즉시 누적된 로그 레코드를 미러 서버로 보내기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-122">When the session is resumed, the principal server immediately begins sending the accumulated log records to the mirror server.</span></span> <span data-ttu-id="f353d-123">미러 서버가 가장 오래된 자동 검사점에 해당하는 로그 레코드를 큐에 대기했음을 확인하면 주 서버에서 주 데이터베이스의 로그를 해당 검사점까지 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-123">After the mirror server confirms that it has queued the log record corresponding to the oldest automatic checkpoint, the principal server truncates the log of the principal database to that checkpoint.</span></span> <span data-ttu-id="f353d-124">미리 서버는 동일한 로그 레코드에서 Redo Queue를 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-124">The mirror server truncates the redo queue at the same log record.</span></span> <span data-ttu-id="f353d-125">연속된 각 검사점에 대해 이 프로세스가 반복되므로 로그는 검사점을 기준으로 단계별로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-125">As this process is repeated for each successive checkpoint, the log is truncated in stages, checkpoint by checkpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f353d-126">검사점 및 로그 잘림에 대한 자세한 내용은 [데이터베이스 검사점&#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f353d-126">For more information about the checkpoints and log truncation, see [Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md).</span></span>  
  
##  <a name="avoid-a-full-transaction-log"></a><a name="AvoidFullLog"></a> <span data-ttu-id="f353d-127">꽉 찬 트랜잭션 로그 방지</span><span class="sxs-lookup"><span data-stu-id="f353d-127">Avoid a Full Transaction Log</span></span>  
 <span data-ttu-id="f353d-128">서버 인스턴스의 공간이 부족하거나 최대 크기에 도달하여 로그가 가득 차면 데이터베이스는 더 이상 업데이트를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-128">If the log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span> <span data-ttu-id="f353d-129">이 문제를 피하는 방법은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-129">To avoid this problem, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="f353d-130">로그가 가득 차기 전에 데이터베이스 미러링 세션을 재개하거나 로그 공간을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-130">Resume the database mirroring session before the log fills up, or add more log space.</span></span> <span data-ttu-id="f353d-131">데이터베이스 미러링을 재개하면 주 서버는 누적된 활성 로그를 미러 서버로 전송하고 미러 데이터베이스는 SYNCHRONIZING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-131">Resuming database mirroring lets the principal server send its accumulated active log to the mirror server and puts the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="f353d-132">그러면 미러 서버에서 로그를 디스크에 확정하고 다시 실행을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-132">The mirror server can then harden the log to disk and start to redo it.</span></span>  
  
-   <span data-ttu-id="f353d-133">미러링을 제거하여 데이터베이스 미러링 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-133">Stop the database mirroring session by removing mirroring.</span></span>  
  
     <span data-ttu-id="f353d-134">일시 중지와는 달리 미러링을 제거하면 미러링 세션에 관한 모든 정보가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-134">Unlike pausing a session, removing mirroring drops all information about the mirroring session.</span></span> <span data-ttu-id="f353d-135">각 파트너 서버 인스턴스는 데이터베이스의 자체 복사본을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-135">Each partner server instance retains its own copy of the database.</span></span> <span data-ttu-id="f353d-136">이전 미러 복사본을 복구하면 이전 주 복사본과 달라져서 세션이 일시 중지된 후 경과한 시간만큼 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="f353d-136">If the former mirror copy is recovered, it will have diverged from the former principal copy and be behind by the amount of time that has elapsed since the session was paused.</span></span> <span data-ttu-id="f353d-137">자세한 내용은 [데이터베이스 미러링 제거&#40;SQL Server&#41;](database-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f353d-137">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f353d-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f353d-138">Related Tasks</span></span>  
 <span data-ttu-id="f353d-139">**데이터베이스 미러링을 일시 중지 또는 재개하려면**</span><span class="sxs-lookup"><span data-stu-id="f353d-139">**To pause or resume database mirroring**</span></span>  
  
-   [<span data-ttu-id="f353d-140">데이터베이스 미러링 세션 일시 중지 또는 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f353d-140">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
 <span data-ttu-id="f353d-141">**데이터베이스 미러링을 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="f353d-141">**To stop database mirroring**</span></span>  
  
-   [<span data-ttu-id="f353d-142">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f353d-142">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f353d-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f353d-143">See Also</span></span>  
 <span data-ttu-id="f353d-144">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f353d-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f353d-145">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f353d-145">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f353d-146">데이터베이스 미러링 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f353d-146">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
