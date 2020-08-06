---
title: 표시된 트랜잭션이 포함된 관련 데이터베이스 복구 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], marks
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- transactions [SQL Server], recovering to a mark
- database recovery [SQL Server]
- marked transactions [SQL Server], restoring
- database restores [SQL Server], point in time
ms.assetid: 77a0d9c0-978a-4891-8b0d-a4256c81c3f8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b968322f92c7a135adb5fd0733b5774e7562bc39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736436"
---
# <a name="recovery-of-related--databases-that-contain-marked-transaction"></a><span data-ttu-id="35ee6-102">표시된 트랜잭션이 포함된 관련 데이터베이스 복구</span><span class="sxs-lookup"><span data-stu-id="35ee6-102">Recovery of Related  Databases That Contain Marked Transaction</span></span>
  <span data-ttu-id="35ee6-103">이 항목에서는 표시된 트랜잭션을 포함하며 전체 복구 모델 또는 대량 로그 복구 모델을 사용하는 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-103">This topic is relevant only for databases that contain marked transactions and that use the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="35ee6-104">특정 복구 지점으로 복원하기 위한 요구 사항에 대한 자세한 내용은 [SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ee6-104">For information about the requirements for restoring to a specific recovery point, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="35ee6-105">에서는 트랜잭션 로그에 명명된 표시를 삽입할 수 있으므로 특정 표시로의 복구가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-105">supports inserting named marks into the transaction log to allow recovery to that specific mark.</span></span> <span data-ttu-id="35ee6-106">로그 표시는 트랜잭션과 관련되어 있으므로 관련된 트랜잭션이 커밋될 경우에만 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-106">Log marks are transaction specific and are inserted only if their associated transaction commits.</span></span> <span data-ttu-id="35ee6-107">그러므로 표시는 특정한 작업에 연결될 수 있고 이 작업을 포함 또는 제외하는 지점으로 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-107">As a result, marks can be tied to specific work, and you can recover to a point that includes or excludes this work.</span></span>  
  
 <span data-ttu-id="35ee6-108">트랜잭션 로그에 명명된 표시를 삽입하기 전에 다음 사항을 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="35ee6-108">Before you insert named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="35ee6-109">트랜잭션 표시는 로그 공간을 소비하므로 데이터베이스 복구 전략에서 중요한 역할을 하는 트랜잭션에 대해서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-109">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="35ee6-110">표시된 트랜잭션을 커밋한 후에 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 의 **logmarkhistory**테이블에 행이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-110">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="35ee6-111">표시된 트랜잭션이 같은 데이터베이스 서버 또는 다른 서버의 다중 데이터베이스에 걸쳐 있으면 영향 받은 모든 데이터베이스의 로그에 표시가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-111">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span> <span data-ttu-id="35ee6-112">자세한 내용은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ee6-112">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35ee6-113">트랜잭션을 표시하는 방법은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ee6-113">For information about how to mark transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-inserting-named-marks-into-a-transaction-log"></a><span data-ttu-id="35ee6-114">명명된 표시를 트랜잭션 로그에 삽입하는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="35ee6-114">Transact-SQL Syntax for Inserting Named Marks into a Transaction Log</span></span>  
 <span data-ttu-id="35ee6-115">[BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 문과 WITH MARK [*description*] 절을 사용하여 표시를 트랜잭션 로그에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-115">To insert marks into the transaction logs, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="35ee6-116">표시 이름은 트랜잭션 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-116">The mark is named the same as the transaction.</span></span> <span data-ttu-id="35ee6-117">선택 요소인 *description* 은 표시의 이름이 아니라 표시의 텍스트 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-117">The optional *description* is a textual description of the mark, not the mark name.</span></span> <span data-ttu-id="35ee6-118">예를 들어 다음 `BEGIN TRANSACTION` 문에서 생성된 표시 및 트랜잭션의 이름은 `Tx1`입니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-118">For example, the name of both the transaction and the mark that is created in the following `BEGIN TRANSACTION` statement is `Tx1`:</span></span>  
  
```wmimof  
BEGIN TRANSACTION Tx1 WITH MARK 'not the mark name, just a description'    
```  
  
 <span data-ttu-id="35ee6-119">트랜잭션 로그는 표시 이름(트랜잭션 이름), 설명, 데이터베이스, 사용자, `datetime` 정보, LSN(로그 시퀀스 번호) 등을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-119">The transaction log records the mark name (transaction name), description, database, user, `datetime` information, and the log sequence number (LSN).</span></span> <span data-ttu-id="35ee6-120">`datetime` 정보는 표시를 고유하게 식별하는 표시 이름과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-120">The `datetime` information is used with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="35ee6-121">여러 데이터베이스에 걸쳐 있는 트랜잭션에 표시를 삽입하는 방법은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ee6-121">For information about how to insert a mark into a transaction that spans multiple databases, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-recovering-to-a-mark"></a><span data-ttu-id="35ee6-122">표시 지점으로 복구하는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="35ee6-122">Transact-SQL Syntax for Recovering to a Mark</span></span>  
 <span data-ttu-id="35ee6-123">[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)문을 사용하여 표시된 트랜잭션을 대상으로 지정할 때 중지된 곳이나 표시 바로 앞에 다음 절 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-123">When you target a marked transaction by using a[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)statement, you can use one the following clauses to stop at or immediately before the mark:</span></span>  
  
-   <span data-ttu-id="35ee6-124">WITH stopatmark = **' *`<mark_name>`* '** 절을 사용 하 여 표시 된 트랜잭션이 복구 지점 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-124">Use the WITH STOPATMARK = **'*`<mark_name>`*'** clause to specify that the marked transaction is the recovery point.</span></span>  
  
     <span data-ttu-id="35ee6-125">STOPATMARK는 표시로 롤포워드하고 표시된 트랜잭션을 롤포워드에 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-125">STOPATMARK rolls forward to the mark and includes the marked transaction in the roll forward.</span></span>  
  
-   <span data-ttu-id="35ee6-126">표시 바로 앞에 있는 로그 레코드가 복구 지점이 되도록 지정 하려면 WITH STOPBEFOREMARK = **' *`<mark_name>`* '** 절을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-126">Use the WITH STOPBEFOREMARK = **'*`<mark_name>`*'** clause to specify that the log record that is immediately before the mark is the recovery point.</span></span>  
  
     <span data-ttu-id="35ee6-127">STOPBEFOREMARK는 표시로 롤포워드하고 롤포워드에서 표시된 트랜잭션을 제외시킵니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-127">STOPBEFOREMARK rolls forward to the mark and excludes marked the transaction from the roll forward.</span></span>  
  
 <span data-ttu-id="35ee6-128">STOPATMARK 옵션과 STOPBEFOREMARK 옵션은 선택적으로 사용되는 AFTER *datetime* 절을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-128">The STOPATMARK and STOPBEFOREMARK options both support an optional AFTER *datetime* clause.</span></span> <span data-ttu-id="35ee6-129">*datetime* 을 사용할 경우 표시 이름은 고유하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-129">When *datetime* is used, mark names do not have to be unique.</span></span>  
  
 <span data-ttu-id="35ee6-130">AFTER *datetime* 이 생략되면 지정한 이름이 있는 첫 번째 표시 지점에서 복구가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-130">If AFTER *datetime* is omitted, roll forward stops at the first mark that has the specified name.</span></span> <span data-ttu-id="35ee6-131">AFTER *datetime* 이 지정되면 *datetime*에서 또는 이후에 지정한 이름이 있는 첫 번째 표시 지점에서 복구가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-131">If AFTER *datetime* is specified, roll forward stops at the first mark that has the specified name, exactly at or after *datetime*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35ee6-132">모든 지정 시간 복원 작업에서처럼 데이터베이스에서 대량 로그 작업이 진행되는 동안 표시 지점으로 복구되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-132">As in all point-in-time restore operations, recovering to a mark is disallowed when the database is undergoing operations that are bulk-logged.</span></span>  
  
 <span data-ttu-id="35ee6-133">**표시된 트랜잭션 지점으로 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="35ee6-133">**To restore to a marked transaction**</span></span>  
  
 [<span data-ttu-id="35ee6-134">데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="35ee6-134">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
 [<span data-ttu-id="35ee6-135">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="35ee6-135">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
### <a name="preparing-the-log-backups"></a><span data-ttu-id="35ee6-136">로그 백업 준비</span><span class="sxs-lookup"><span data-stu-id="35ee6-136">Preparing the Log Backups</span></span>  
 <span data-ttu-id="35ee6-137">이 예에서 이러한 관련된 데이터베이스에 대한 적절한 백업 전략은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-137">For this example, an appropriate backup strategy for these related databases would be the following:</span></span>  
  
1.  <span data-ttu-id="35ee6-138">두 데이터베이스 모두에 전체 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-138">Use the full recovery model for both databases.</span></span>  
  
2.  <span data-ttu-id="35ee6-139">각 데이터베이스의 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-139">Create a full backup of each database.</span></span>  
  
     <span data-ttu-id="35ee6-140">데이터베이스를 연속적으로 또는 동시에 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-140">The databases can be backed up sequentially or simultaneously.</span></span>  
  
3.  <span data-ttu-id="35ee6-141">트랜잭션 로그를 백업하기 전에 모든 데이터베이스에서 실행되는 트랜잭션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-141">Before backing up the transaction log, mark a transaction that executes in all databases.</span></span> <span data-ttu-id="35ee6-142">표시된 트랜잭션을 만드는 방법은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ee6-142">For information about how to create the marked transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
4.  <span data-ttu-id="35ee6-143">각 데이터베이스에서 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-143">Back up the transaction log on each database.</span></span>  
  
### <a name="recovering-the-database-to-a-marked-transaction"></a><span data-ttu-id="35ee6-144">데이터베이스를 표시된 트랜잭션으로 복구</span><span class="sxs-lookup"><span data-stu-id="35ee6-144">Recovering the Database to a Marked Transaction</span></span>  
 <span data-ttu-id="35ee6-145">**백업을 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="35ee6-145">**To restore the backup**</span></span>  
  
1.  <span data-ttu-id="35ee6-146">필요하면 손상되지 않은 데이터베이스의 [비상 로그 백업](tail-log-backups-sql-server.md) 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-146">Create [tail-log backups](tail-log-backups-sql-server.md) of the undamaged databases, if possible.</span></span>  
  
2.  <span data-ttu-id="35ee6-147">각 데이터베이스의 최신 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-147">Restore the most recent full database backup of each database.</span></span>  
  
3.  <span data-ttu-id="35ee6-148">모든 트랜잭션 로그 백업에서 가장 최근에 표시된 사용 가능한 트랜잭션을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-148">Identify the most recent marked transaction that is available in all of the transaction log backups.</span></span> <span data-ttu-id="35ee6-149">이 내용은 각 서버의 **msdb** 데이터베이스에 있는 **logmarkhistory** 테이블에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-149">This information is stored in the **logmarkhistory** table in the **msdb** database on each server.</span></span>  
  
4.  <span data-ttu-id="35ee6-150">이 표시가 들어 있는 관련된 모든 데이터베이스에 대한 로그 백업을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-150">Identify the log backups for all related databases that contain this mark.</span></span>  
  
5.  <span data-ttu-id="35ee6-151">표시된 트랜잭션에서 중지된 각 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-151">Restore each log backup, stopping at the marked transaction.</span></span>  
  
6.  <span data-ttu-id="35ee6-152">각 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="35ee6-152">Recover each database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ee6-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35ee6-153">See Also</span></span>  
 <span data-ttu-id="35ee6-154">[BEGIN TRANSACTION&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="35ee6-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="35ee6-155">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="35ee6-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="35ee6-156">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="35ee6-156">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="35ee6-157">[표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span><span class="sxs-lookup"><span data-stu-id="35ee6-157">[Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span></span>  
 <span data-ttu-id="35ee6-158">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="35ee6-158">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="35ee6-159">[SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="35ee6-159">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="35ee6-160">복원 시퀀스 계획 및 수행&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="35ee6-160">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
