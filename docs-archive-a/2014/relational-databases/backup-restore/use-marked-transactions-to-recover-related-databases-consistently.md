---
title: 표시 된 트랜잭션을 사용 하 여 관련 데이터베이스를 일관 되 게 복구 (전체 복구 모델) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction marks [SQL Server]
- marked transactions [SQL Server]
- database restores [SQL Server], inserting transaction marks for
- recovery [SQL Server], related databases
- restoring databases [SQL Server], related database recovery
- database restores [SQL Server], related databases
- marked transactions [SQL Server], creating
- BEGIN TRAN...WITH MARK statement
- two-phase commit
ms.assetid: 50a73574-1a69-448e-83dd-9abcc7cb7e1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8dd368ad14f6e521fb8d504bdea774e3088c2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736423"
---
# <a name="use-marked-transactions-to-recover-related-databases-consistently-full-recovery-model"></a><span data-ttu-id="0ee56-102">표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구(전체 복구 모델)</span><span class="sxs-lookup"><span data-stu-id="0ee56-102">Use Marked Transactions to Recover Related Databases Consistently (Full Recovery Model)</span></span>
  <span data-ttu-id="0ee56-103">이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="0ee56-104">두 개 이상의 데이터베이스, 즉 *관련 데이터베이스*에 관련 업데이트를 수행할 경우 트랜잭션 표시를 사용하여 해당 데이터베이스를 논리적으로 일치하는 지점으로 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-104">When you make related updates to two or more databases, *related databases*, you can use transaction marks to recover them to a logically consistent point.</span></span> <span data-ttu-id="0ee56-105">그러나 이러한 방법으로 복구를 수행하면 복구 지점으로 사용된 표시 뒤에 커밋된 모든 트랜잭션이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-105">However, this recovery loses any transaction that is committed after the mark that was used as the recovery point.</span></span> <span data-ttu-id="0ee56-106">트랜잭션 표시는 관련 데이터베이스를 테스트하거나 최근 커밋된 트랜잭션을 손실해도 상관없는 경우에만 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-106">Marking transactions is suitable only when you are testing related databases or when you are willing to lose recently committed transactions.</span></span>  
  
 <span data-ttu-id="0ee56-107">모든 관련 데이터베이스의 관련 트랜잭션을 정기적으로 표시하면 데이터베이스에 일련의 공통 복구 지점이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-107">Routinely marking related transactions in every related database establishes a series of common recovery points in the databases.</span></span> <span data-ttu-id="0ee56-108">트랜잭션 표시는 트랜잭션 로그에 기록되고 로그 백업에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-108">The transaction marks are recorded in the transaction log and included in log backups.</span></span> <span data-ttu-id="0ee56-109">재해가 발생할 경우 각 데이터베이스를 동일한 트랜잭션 표시로 복원하여 해당 데이터베이스를 일치하는 지점으로 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-109">In the event of a disaster, you can restore each of the databases to the same transaction mark to recover them to a consistent point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ee56-110">서로 다른 데이터베이스의 로그 백업은 개별적으로 만들 수 있으며 동시에 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-110">Log backups on the different databases can be created independently of each other and do not have to be simultaneous.</span></span>  
  
 <span data-ttu-id="0ee56-111">다음 시나리오에서 관련 데이터베이스를 복구하려면 모든 관련 데이터베이스의 트랜잭션에 이미 표시가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-111">Recovering related databases in the following scenarios requires that you have already marked transactions in every related database:</span></span>  
  
-   <span data-ttu-id="0ee56-112">하나 이상의 트랜잭션 로그가 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-112">One or more transaction logs are destroyed.</span></span> <span data-ttu-id="0ee56-113">마지막 로그 백업과 같은 상태로 데이터베이스 집합을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-113">You have to restore the set of databases to a consistent state at the time of your last log backup.</span></span>  
  
-   <span data-ttu-id="0ee56-114">이전 시점의 서로 일치하는 상태로 전체 데이터베이스 집합을 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-114">You have to restore the entire set of databases to a mutually consistent state at some earlier point in time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0ee56-115">표시된 트랜잭션에만 관련된 데이터베이스를 복구할 수 있으며 지정 시간과는 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-115">You can recover related databases only to a marked transaction, not to a specific point in time.</span></span>  
  
 <span data-ttu-id="0ee56-116">표시하는 트랜잭션을 만드는 방법은 이 항목의 뒷부분에 나오는 "표시된 트랜잭션 만들기"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ee56-116">For information about how to create marking transactions, see "Creating the Marked Transactions," later in this topic.</span></span>  
  
## <a name="typical-scenario-for-using-marked-transactions"></a><span data-ttu-id="0ee56-117">표시된 트랜잭션 사용에 대한 일반적인 시나리오</span><span class="sxs-lookup"><span data-stu-id="0ee56-117">Typical Scenario for Using Marked Transactions</span></span>  
 <span data-ttu-id="0ee56-118">표시된 트랜잭션 사용에 대한 일반적인 시나리오는 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-118">A typical scenario for using marked transactions includes the following steps:</span></span>  
  
1.  <span data-ttu-id="0ee56-119">각 관련 데이터베이스의 전체 또는 차등 데이터베이스 백업 만들기</span><span class="sxs-lookup"><span data-stu-id="0ee56-119">Create a full or differential database backup of each of the related databases.</span></span>  
  
2.  <span data-ttu-id="0ee56-120">모든 데이터베이스에서 트랜잭션 블록 표시</span><span class="sxs-lookup"><span data-stu-id="0ee56-120">Mark a transaction block in all the databases.</span></span>  
  
3.  <span data-ttu-id="0ee56-121">모든 데이터베이스의 트랜잭션 로그 백업</span><span class="sxs-lookup"><span data-stu-id="0ee56-121">Back up the transaction log for all the databases.</span></span>  
  
4.  <span data-ttu-id="0ee56-122">WITH NORECOVERY로 데이터베이스 백업 복원</span><span class="sxs-lookup"><span data-stu-id="0ee56-122">Restore database backups WITH NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="0ee56-123">WITH STOPATMARK로 로그 복원</span><span class="sxs-lookup"><span data-stu-id="0ee56-123">Restore logs WITH STOPATMARK.</span></span>  
  
## <a name="considerations-for-using-marked-transactions"></a><span data-ttu-id="0ee56-124">표시된 트랜잭션 사용에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="0ee56-124">Considerations for Using Marked Transactions</span></span>  
 <span data-ttu-id="0ee56-125">트랜잭션 로그에 명명된 표시를 삽입하기 전에 다음 사항을 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0ee56-125">Before inserting named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="0ee56-126">트랜잭션 표시는 로그 공간을 소비하므로 데이터베이스 복구 전략에서 중요한 역할을 하는 트랜잭션에 대해서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-126">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="0ee56-127">표시된 트랜잭션을 커밋한 후에 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 의 **logmarkhistory**테이블에 행이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-127">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="0ee56-128">표시된 트랜잭션이 같은 데이터베이스 서버 또는 다른 서버의 다중 데이터베이스에 걸쳐 있으면 영향 받은 모든 데이터베이스의 로그에 표시가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-128">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span>  
  
## <a name="creating-the-marked-transactions"></a><span data-ttu-id="0ee56-129">표시된 트랜잭션 만들기</span><span class="sxs-lookup"><span data-stu-id="0ee56-129">Creating the Marked Transactions</span></span>  
 <span data-ttu-id="0ee56-130">표시된 트랜잭션을 만들려면 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 문과 WITH MARK [*description*] 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-130">To create a marked transaction, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="0ee56-131">선택 요소인 *description* 은 표시의 텍스트 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-131">The optional *description* is a textual description of the mark.</span></span> <span data-ttu-id="0ee56-132">트랜잭션의 표시 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-132">A mark name for the transaction is required.</span></span> <span data-ttu-id="0ee56-133">표시 이름은 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-133">A mark name can be reused.</span></span> <span data-ttu-id="0ee56-134">트랜잭션 로그에는 표시 이름, 설명, 데이터베이스, 사용자, datetime 정보, LSN(로그 시퀀스 번호) 등이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-134">The transaction log records the mark name, description, database, user, datetime information, and the log sequence number (LSN).</span></span> <span data-ttu-id="0ee56-135">datetime 정보는 표시 이름과 함께 사용되어 표시를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-135">The datetime information is used along with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="0ee56-136">**데이터베이스 집합에 표시된 트랜잭션을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="0ee56-136">**To create marked transactions in a set of databases:**</span></span>  
  
1.  <span data-ttu-id="0ee56-137">BEGIN TRAN 문에서 트랜잭션 이름을 지정하고 WITH MARK 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-137">Name the transaction in the BEGIN TRAN statement and use the WITH MARK clause</span></span>  
  
     <span data-ttu-id="0ee56-138">BEGIN TRAN *new_mark_name* WITH MARK 문을 기존 트랜잭션 내에 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-138">You can nest the statement BEGIN TRAN *new_mark_name* WITH MARK within an existing transaction.</span></span> <span data-ttu-id="0ee56-139">*new_mark_name* 의 값은 트랜잭션에 트랜잭션 이름이 있더라도 트랜잭션의 표시 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-139">The value of *new_mark_name* is the mark name for the transaction, even if the transaction possesses a transaction name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ee56-140">두 번째로 중첩된 BEGIN TRAN...WITH MARK를 실행하면 해당 문은 건너뛰지만 경고 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-140">If you issue a second nested BEGIN TRAN...WITH MARK, that statement is skipped but causes a warning message.</span></span>  
  
2.  <span data-ttu-id="0ee56-141">집합의 모든 데이터베이스에 대해 업데이트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-141">Run an update against all of the databases in the set.</span></span>  
  
     <span data-ttu-id="0ee56-142">특정 트랜잭션에 대한 표시는 BEGIN TRAN...WITH MARK 문이 실행된 서버 인스턴스의 트랜잭션 로그에만 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-142">The mark for a specific transaction is inserted into transaction logs only on the server instance where the BEGIN TRAN...WITH MARK statement is executed.</span></span> <span data-ttu-id="0ee56-143">트랜잭션 표시는 해당 서버 인스턴스에서 표시된 트랜잭션이 업데이트한 모든 데이터베이스의 트랜잭션 로그에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-143">The transaction mark is placed in the transaction log of every database updated by the marked transaction on that server instance.</span></span> <span data-ttu-id="0ee56-144">데이터베이스가 서로 다른 서버 인스턴스에 있으면 각 서버 인스턴스에 동일한 표시를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-144">If the databases reside on different server instances, identical marks must be created on each of the server instances.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0ee56-145">예</span><span class="sxs-lookup"><span data-stu-id="0ee56-145">Examples</span></span>  
 <span data-ttu-id="0ee56-146">다음 예에서는 트랜잭션 로그를 복원하여 `ListPriceUpdate`라는 표시된 트랜잭션에 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-146">The following example restores the transaction log to the mark in the marked transaction named `ListPriceUpdate`.</span></span>  
  
```sql  
USE AdventureWorks  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master  
GO  
  
RESTORE DATABASE AdventureWorks  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'ListPriceUpdate';  
```  
  
## <a name="forcing-a-mark-to-spread-to-other-servers"></a><span data-ttu-id="0ee56-147">다른 서버에 표시 분산</span><span class="sxs-lookup"><span data-stu-id="0ee56-147">Forcing a Mark to Spread to Other Servers</span></span>  
 <span data-ttu-id="0ee56-148">트랜잭션 표시 이름은 트랜잭션이 다른 서버에 분산될 때 자동으로 그 서버에 분산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-148">A transaction mark name is not automatically distributed to another server as the transaction spreads there.</span></span> <span data-ttu-id="0ee56-149">표시를 다른 서버에 분산하려면 BEGIN TRAN *name* WITH MARK 문을 포함하는 저장 프로시저를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-149">To force the mark to spread to the other servers, a stored procedure must be written that contains a BEGIN TRAN *name* WITH MARK statement.</span></span> <span data-ttu-id="0ee56-150">그런 다음 그 저장 프로시저를 원래 서버의 트랜잭션 영역에 있는 원격 서버에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-150">That stored procedure must then be executed on the remote server under the scope of the transaction in the originating server.</span></span>  
  
 <span data-ttu-id="0ee56-151">예를 들어 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 있는 분할된 데이터베이스를 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-151">For example, consider a partitioned database that exists on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ee56-152">각 인스턴스에서 데이터베이스 이름은 `coyote`입니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-152">On each instance is a database named `coyote`.</span></span> <span data-ttu-id="0ee56-153">먼저 모든 데이터베이스에 저장 프로시저(예: `sp_SetMark`)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-153">First, in every database, create a stored procedure, for example, `sp_SetMark`.</span></span>  
  
```sql  
CREATE PROCEDURE sp_SetMark  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION @name WITH MARK  
UPDATE coyote.dbo.Marks SET one = 1  
COMMIT TRANSACTION;  
GO  
```  
  
 <span data-ttu-id="0ee56-154">그런 다음 모든 데이터베이스에 표시를 삽입하는 트랜잭션을 포함하는 `sp_MarkAll` 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-154">Next, create stored procedure `sp_MarkAll` containing a transaction that places a mark in every database.</span></span> <span data-ttu-id="0ee56-155">`sp_MarkAll` 을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-155">`sp_MarkAll` can be run from any of the instances.</span></span>  
  
```sql  
CREATE PROCEDURE sp_MarkAll  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION  
EXEC instance0.coyote.dbo.sp_SetMark @name  
EXEC instance1.coyote.dbo.sp_SetMark @name  
EXEC instance2.coyote.dbo.sp_SetMark @name  
COMMIT TRANSACTION;  
GO  
```  
  
### <a name="two-phase-commit"></a><span data-ttu-id="0ee56-156">2단계 커밋</span><span class="sxs-lookup"><span data-stu-id="0ee56-156">Two-Phase Commit</span></span>  
 <span data-ttu-id="0ee56-157">분산된 트랜잭션 커밋은 준비 및 커밋의 2단계로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-157">Committing a distributed transaction occurs in two phases: prepare and commit.</span></span> <span data-ttu-id="0ee56-158">표시된 트랜잭션이 커밋되면 표시된 트랜잭션의 각 데이터베이스에 대한 커밋 로그 레코드가 모든 로그에 의심되는 트랜잭션이 없을 때 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-158">When a marked transaction is committed, the commit log record for each database in the marked transaction is placed in the log at a point where there are no in-doubt transactions in any of the logs.</span></span> <span data-ttu-id="0ee56-159">이때 한 로그에서는 커밋된 것으로 다른 로그에서는 커밋되지 않은 것으로 나타나는 트랜잭션은 분명히 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-159">At this point, it is guaranteed that there are no transactions that appear as committed in one log, but not committed in another log.</span></span>  
  
 <span data-ttu-id="0ee56-160">표시된 트랜잭션을 커밋하는 동안 다음 단계를 수행하여 커밋되지 않은 트랜잭션이 나타나지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-160">The following steps accomplish this during the commit of a marked transaction:</span></span>  
  
1.  <span data-ttu-id="0ee56-161">표시하는 트랜잭션의 준비 단계는 모든 새 준비 및 커밋을 대기시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-161">Prepare phase of a marking transaction stalls all new prepares and commits.</span></span>  
  
2.  <span data-ttu-id="0ee56-162">이미 준비된 트랜잭션의 커밋만 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-162">Only commits of already prepared transactions are allowed to continue.</span></span>  
  
3.  <span data-ttu-id="0ee56-163">그런 다음 표시하는 트랜잭션은 준비된 모든 트랜잭션이 시간이 만료되어 빠져 나가기를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-163">Marking transaction then waits for all prepared transactions to drain (with time-out).</span></span>  
  
4.  <span data-ttu-id="0ee56-164">표시된 트랜잭션을 준비하고 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-164">Marked transaction is prepared and committed.</span></span>  
  
5.  <span data-ttu-id="0ee56-165">새 준비 및 커밋의 대기를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-165">The stall of new prepares and commits is removed.</span></span>  
  
 <span data-ttu-id="0ee56-166">다중 데이터베이스에 걸쳐 표시된 트랜잭션이 생성한 대기는 서버의 트랜잭션 처리 성능을 감소시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-166">The stalls generated by marked transactions that span multiple databases can reduce the transaction processing performance of the server.</span></span>  
  
 <span data-ttu-id="0ee56-167">표시된 트랜잭션을 동시에 실행하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-167">We recommend that you do not run concurrent marked transactions.</span></span> <span data-ttu-id="0ee56-168">드문 일이지만 분산 표시된 트랜잭션의 커밋이 동시에 커밋되는 다른 분산 표시된 트랜잭션과 교착 상태에 빠질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-168">It is rare but possible for the commit of a distributed marked transaction to deadlock with other distributed marked transactions that are committing at the same time.</span></span> <span data-ttu-id="0ee56-169">이 경우 표시하는 트랜잭션이 교착 상태에서 희생되어 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-169">When this happens, the marking transaction is chosen as the deadlock victim and is rolled back.</span></span> <span data-ttu-id="0ee56-170">이런 경우가 발생하면 애플리케이션이 표시된 트랜잭션을 다시 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-170">When this error occurs, the application can retry the marked transaction.</span></span> <span data-ttu-id="0ee56-171">여러 개의 표시된 트랜잭션이 동시에 커밋을 시도하면 교착 상태에 빠질 가능성이 더 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="0ee56-171">When multiple marked transactions try to commit concurrently, there is a higher probability of deadlock.</span></span>  
  
## <a name="recovering-to-a-marked-transaction"></a><span data-ttu-id="0ee56-172">표시된 트랜잭션으로 복구</span><span class="sxs-lookup"><span data-stu-id="0ee56-172">Recovering to a Marked Transaction</span></span>  
 <span data-ttu-id="0ee56-173">표시된 트랜잭션을 포함하는 데이터베이스를 특정 표시 또는 해당 표시 바로 앞으로 복구하는 방법은 [표시된 트랜잭션이 포함된 관련 데이터베이스 복구](recovery-of-related-databases-that-contain-marked-transaction.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ee56-173">For information about how to recover a database that contains marked transactions to or just before a particular mark, see [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee56-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ee56-174">See Also</span></span>  
 <span data-ttu-id="0ee56-175">[BEGIN DISTRIBUTED TRANSACTION&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ee56-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span></span>  
 <span data-ttu-id="0ee56-176">[시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ee56-176">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="0ee56-177">[BEGIN TRANSACTION&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ee56-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="0ee56-178">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ee56-178">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="0ee56-179">[전체 데이터베이스 백업&#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ee56-179">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="0ee56-180">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ee56-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="0ee56-181">표시된 트랜잭션이 포함된 관련 데이터베이스 복구</span><span class="sxs-lookup"><span data-stu-id="0ee56-181">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
  
