---
title: 트랜잭션 로그 백업(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 752447d6c38a2df0fcbdce72fbba12edd7a9eeb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734187"
---
# <a name="transaction-log-backups-sql-server"></a><span data-ttu-id="fd718-102">트랜잭션 로그 백업(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fd718-102">Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="fd718-103">이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="fd718-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 트랜잭션 로그를 백업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-104">This topic discusses backing up the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="fd718-105">로그 백업을 만들려면 최소한 하나의 전체 백업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-105">Minimally, you must have created at least one full backup before you can create any log backups.</span></span> <span data-ttu-id="fd718-106">그렇게 해야 로그가 백업 중일 때를 제외하고 언제든지 트랜잭션 로그를 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-106">After that, the transaction log can be backed up at any time unless the log is already being backed up.</span></span> <span data-ttu-id="fd718-107">로그 백업을 자주 수행하여 작업 손실 가능성을 최소화하고 트랜잭션 로그를 잘라내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-107">We recommend that you take log backups frequently, both to minimize work loss exposure and to truncate the transaction log.</span></span> <span data-ttu-id="fd718-108">데이터베이스 관리자는 보통 주기적(예: 매주)으로 전체 데이터베이스 백업을 만들고, 상황에 따라 더 짧은 간격(예: 매일)으로 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-108">Typically, a database administrator creates a full database backup occasionally, such as weekly, and, optionally, creates a series of differential database backup at a shorter interval, such as daily.</span></span> <span data-ttu-id="fd718-109">또한 데이터베이스 백업과 상관없이 더 자주(예: 매 10분) 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-109">Independently of the database backups, the database administrator backs up the transaction log at frequent intervals, such as every 10 minutes.</span></span> <span data-ttu-id="fd718-110">지정된 백업 유형의 최적 간격은 데이터의 중요도, 데이터베이스의 크기 및 서버의 작업과 같은 요소에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-110">For a given type of backup, the optimal interval depends on factors such as the importance of the data, the size of the database, and the workload of the server.</span></span>  
  
 <span data-ttu-id="fd718-111">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="fd718-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="fd718-112">로그 백업 시퀀스의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="fd718-112">How a Sequence of Log Backups Works</span></span>](#LogBackupSequence)  
  
-   [<span data-ttu-id="fd718-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fd718-113">Recommendations</span></span>](#Recommendations)  
  
-   [<span data-ttu-id="fd718-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fd718-114">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="fd718-115">관련 내용</span><span class="sxs-lookup"><span data-stu-id="fd718-115">Related Content</span></span>](#RelatedContent)  
  
##  <a name="how-a-sequence-of-log-backups-works"></a><a name="LogBackupSequence"></a><span data-ttu-id="fd718-116">로그 백업 시퀀스의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="fd718-116">How a Sequence of Log Backups Works</span></span>  
 <span data-ttu-id="fd718-117">트랜잭션 로그 백업 *로그 체인* 시퀀스는 데이터 백업과 독립되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-117">The sequence of transaction log backups *log chain* is independent of data backups.</span></span> <span data-ttu-id="fd718-118">예를 들어 이벤트가 다음과 같은 순서로 발생한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-118">For example, assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="fd718-119">Time</span><span class="sxs-lookup"><span data-stu-id="fd718-119">Time</span></span>|<span data-ttu-id="fd718-120">이벤트</span><span class="sxs-lookup"><span data-stu-id="fd718-120">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="fd718-121">8:00 A.M.</span><span class="sxs-lookup"><span data-stu-id="fd718-121">8:00 A.M.</span></span>|<span data-ttu-id="fd718-122">데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-122">Back up database.</span></span>|  
|<span data-ttu-id="fd718-123">정오</span><span class="sxs-lookup"><span data-stu-id="fd718-123">Noon</span></span>|<span data-ttu-id="fd718-124">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-124">Back up transaction log.</span></span>|  
|<span data-ttu-id="fd718-125">오후 4:00</span><span class="sxs-lookup"><span data-stu-id="fd718-125">4:00 P.M.</span></span>|<span data-ttu-id="fd718-126">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-126">Back up transaction log.</span></span>|  
|<span data-ttu-id="fd718-127">오후 6:00</span><span class="sxs-lookup"><span data-stu-id="fd718-127">6:00 P.M.</span></span>|<span data-ttu-id="fd718-128">데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-128">Back up database.</span></span>|  
|<span data-ttu-id="fd718-129">8:00 P.M.</span><span class="sxs-lookup"><span data-stu-id="fd718-129">8:00 P.M.</span></span>|<span data-ttu-id="fd718-130">트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-130">Back up transaction log.</span></span>|  
  
 <span data-ttu-id="fd718-131">저녁 8시에 만든 트랜잭션 로그 백업에는</span><span class="sxs-lookup"><span data-stu-id="fd718-131">The transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="fd718-132">오후 4시부터 저녁 8시까지 기록한 트랜잭션 로그 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-132">contains transaction log records from 4:00 P.M.</span></span> <span data-ttu-id="fd718-133">이 시간대에는 전체 데이터베이스 백업을 만든 오후 6시도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-133">through 8:00 P.M., spanning the time when the full database backup was created at 6:00 P.M.</span></span> <span data-ttu-id="fd718-134">트랜잭션 로그 백업의 시퀀스는 오전 8시에 만든 첫째 전체 데이터베이스 백업부터</span><span class="sxs-lookup"><span data-stu-id="fd718-134">The sequence of transaction log backups is continuous from the initial full database backup created at 8:00 A.M.</span></span> <span data-ttu-id="fd718-135">저녁 8시에 만든 마지막 트랜잭션 로그 백업까지 이어집니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-135">to the last transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="fd718-136">이러한 로그 백업을 적용하는 방법은 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md)의 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd718-136">For information about how to apply these log backups, see the example in [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fd718-137">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fd718-137">Recommendations</span></span>  
  
-   <span data-ttu-id="fd718-138">트랜잭션 로그가 손상되면 최근의 유효 백업 이후에 수행한 작업이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-138">If a transaction log is damaged, work that is performed since the most recent valid backup is lost.</span></span> <span data-ttu-id="fd718-139">따라서 내결함성이 있는 스토리지에 로그 파일을 보관하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-139">Therefore we strongly recommend that you put your log files on fault-tolerant storage.</span></span>  
  
-   <span data-ttu-id="fd718-140">데이터베이스가 손상되었거나 데이터베이스를 복원하려는 경우에는 데이터베이스를 현재의 지정 시간으로 복원할 수 있도록 [비상 로그 백업](tail-log-backups-sql-server.md) 을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-140">If a database is damaged or you are about to restore the database, we recommend that you create a [tail-log backup](tail-log-backups-sql-server.md) to enable you to restore the database to the current point in time.</span></span>  
  
-   <span data-ttu-id="fd718-141">기본적으로 백업 작업을 성공적으로 수행할 때마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 시스템 이벤트 로그에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-141">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="fd718-142">로그를 자주 백업하는 경우 이러한 성공 메시지는 바로 누적되므로 엄청난 오류 로그가 쌓여 다른 메시지를 찾기 힘들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-142">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="fd718-143">이 경우 스크립트가 이러한 로그 항목에 종속되지 않을 경우 추적 플래그 3226을 사용하여 이러한 항목을 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd718-143">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="fd718-144">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd718-144">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fd718-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fd718-145">Related Tasks</span></span>  
 <span data-ttu-id="fd718-146">**트랜잭션 로그 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="fd718-146">**To create a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="fd718-147">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd718-147">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="fd718-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="fd718-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="fd718-149">백업 작업을 예약하려면 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd718-149">To schedule backup jobs, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="fd718-150">관련 내용</span><span class="sxs-lookup"><span data-stu-id="fd718-150">Related Content</span></span>  
 <span data-ttu-id="fd718-151">없음</span><span class="sxs-lookup"><span data-stu-id="fd718-151">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd718-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd718-152">See Also</span></span>  
 <span data-ttu-id="fd718-153">[트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd718-153">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="fd718-154">[SQL Server 데이터베이스 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="fd718-154">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="fd718-155">[비상 로그 백업&#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd718-155">[Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="fd718-156">트랜잭션 로그 백업 적용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd718-156">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](transaction-log-backups-sql-server.md)  
  
  
