---
title: 로그 시퀀스 번호로 복구(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4df55c3468fc009d86cffd58a837d6935f5ce14b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653469"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a><span data-ttu-id="cfebb-102">로그 시퀀스 번호로 복구(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cfebb-102">Recover to a Log Sequence Number (SQL Server)</span></span>
  <span data-ttu-id="cfebb-103">이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 데이터베이스와 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-103">This topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="cfebb-104">LSN(로그 시퀀스 번호)을 사용하여 복원 작업에 대한 복구 지점을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-104">You can use a log sequence number (LSN) to define the recovery point for a restore operation.</span></span> <span data-ttu-id="cfebb-105">그러나 이 기능은 도구 공급업체를 위해 특별히 제작된 기능으로 일반적으로 유용한 기능은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-105">However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.</span></span>  
  
##  <a name="overview-of-log-sequence-numbers"></a><a name="LSNs"></a> <span data-ttu-id="cfebb-106">로그 시퀀스 번호 개요</span><span class="sxs-lookup"><span data-stu-id="cfebb-106">Overview of Log Sequence Numbers</span></span>  
 <span data-ttu-id="cfebb-107">LSN은 RESTORE 순서 중에 내부적으로 사용되어 데이터가 복원될 지정 시간을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-107">LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored.</span></span> <span data-ttu-id="cfebb-108">백업을 복구할 때 데이터는 백업이 이루어진 지정 시간에 해당하는 LSN으로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-108">When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken.</span></span> <span data-ttu-id="cfebb-109">차등 및 로그 백업의 경우 데이터베이스는 보다 나중의 것으로 복원되며 이는 더 높은 LSN에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-109">Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.</span></span>  
  
 <span data-ttu-id="cfebb-110">트랜잭션 로그의 모든 레코드는 LSN(로그 시퀀스 번호)으로 고유하게 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-110">Every record in the transaction log is uniquely identified by a log sequence number (LSN).</span></span> <span data-ttu-id="cfebb-111">LSN은 변경이 발생한 순서에 따라 번호가 매겨집니다. 예를 들어 LSN2가 LSN1보다 큰 경우 로그 레코드 LSN1에 해당하는 변경이 먼저 발생하고 로그 레코드 LSN2에 해당하는 변경이 이후에 발생한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-111">LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.</span></span>  
  
 <span data-ttu-id="cfebb-112">중요한 이벤트가 발생한 로그 레코드의 LSN은 올바른 복원 시퀀스를 생성하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-112">The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences.</span></span> <span data-ttu-id="cfebb-113">Lsn은 정렬 되기 때문에 같음 및 같지 않음을 비교할 수 있습니다 (즉,,, **\<**, **>** **=** **\<=**, **>=** ).</span><span class="sxs-lookup"><span data-stu-id="cfebb-113">Because LSNs are ordered, they can be compared for equality and inequality (that is, **\<**, **>**, **=**, **\<=**, **>=**).</span></span> <span data-ttu-id="cfebb-114">이러한 비교 방식은 복원 시퀀스를 만들 때 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-114">Such comparisons are useful when constructing restore sequences.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cfebb-115">LSN은 `numeric`(25,0) 데이터 형식의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-115">LSNs are values of data type `numeric`(25,0).</span></span> <span data-ttu-id="cfebb-116">더하기나 빼기와 같은 산술 연산은 의미가 없으며 LSN과 함께 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-116">Arithmetic operations (for example, addition or subtraction) are not meaningful and must not be used with LSNs.</span></span>  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a><span data-ttu-id="cfebb-117">백업과 복원에 사용된 LSN 보기</span><span class="sxs-lookup"><span data-stu-id="cfebb-117">Viewing LSNs Used by Backup and Restore</span></span>  
 <span data-ttu-id="cfebb-118">다음 중 하나 이상의 방법을 사용하여 지정된 백업 및 복원 이벤트가 발생했을 때의 로그 레코드 LSN을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-118">The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:</span></span>  
  
-   [<span data-ttu-id="cfebb-119">backupset</span><span class="sxs-lookup"><span data-stu-id="cfebb-119">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [<span data-ttu-id="cfebb-120">backupfile</span><span class="sxs-lookup"><span data-stu-id="cfebb-120">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   <span data-ttu-id="cfebb-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="cfebb-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span></span>  
  
-   [<span data-ttu-id="cfebb-122">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="cfebb-122">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="cfebb-123">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="cfebb-123">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="cfebb-124">LSN은 일부 메시지 텍스트에도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-124">LSNs also appear in some message texts.</span></span>  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a><span data-ttu-id="cfebb-125">LSN으로 복원하기 위한 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="cfebb-125">Transact-SQL Syntax for Restoring to an LSN</span></span>  
 <span data-ttu-id="cfebb-126">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용하여 다음과 같은 LSN에서 또는 이전에 즉시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-126">By using a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, you can stop at or immediately before the LSN, as follows:</span></span>  
  
-   <span data-ttu-id="cfebb-127">WITH STOPATMARK **='** lsn: _<lsn_number>_ **'** 절을 사용합니다. 여기서 lsn: *\<lsnNumber>* 는 지정한 LSN이 포함된 로그 레코드가 복구 지점이 되도록 지정하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-127">Use the WITH STOPATMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record that contains the specified LSN is the recovery point.</span></span>  
  
     <span data-ttu-id="cfebb-128">STOPATMARK는 복구 중지 지점을 나타내며 지정된 로그 레코드를 포함하는 지점까지 롤포워드됩니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-128">STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.</span></span>  
  
-   <span data-ttu-id="cfebb-129">WITH STOPBEFOREMARK **='** lsn: _<lsn_number>_ **'** 절을 사용합니다. 여기서 lsn: *\<lsnNumber>* 는 지정한 LSN이 포함된 로그 레코드가 복구 지점이 되도록 지정하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-129">Use the WITH STOPBEFOREMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.</span></span>  
  
     <span data-ttu-id="cfebb-130">STOPBEFOREMARK는 LSN에 롤포워드하고 롤포워드의 해당 로그 레코드를 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-130">STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.</span></span>  
  
 <span data-ttu-id="cfebb-131">일반적으로 특정 트랜잭션을 포함하거나 제외하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-131">Typically, a specific transaction is selected to be included or excluded.</span></span> <span data-ttu-id="cfebb-132">필수는 아니지만 대개 지정된 로그 레코드는 트랜잭션 커밋 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-132">Although not required, in practice, the specified log record is a transaction-commit record.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cfebb-133">예</span><span class="sxs-lookup"><span data-stu-id="cfebb-133">Examples</span></span>  
 <span data-ttu-id="cfebb-134">다음 예에서는 `AdventureWorks` 데이터베이스가 전체 복구 모델을 사용하도록 변경되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cfebb-134">The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.</span></span>  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cfebb-135">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cfebb-135">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cfebb-136">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-136">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="cfebb-137">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-137">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="cfebb-138">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-138">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="cfebb-139">전체 복구 모델에서 특정 오류 지점으로 데이터베이스 복원&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-139">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="cfebb-140">데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-140">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cfebb-141">SQL Server 데이터베이스를 지정 시간으로 복원&#40;전체 복구 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-141">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="cfebb-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfebb-142">See Also</span></span>  
 <span data-ttu-id="cfebb-143">[트랜잭션 로그 백업 적용&#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cfebb-143">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="cfebb-144">[트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cfebb-144">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="cfebb-145">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cfebb-145">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
