---
title: 지연된 트랜잭션(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- I/O [SQL Server], database recovery
- restoring pages [SQL Server]
- deferred transactions
- modifying transaction deferred state
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 188a0409fbad3f12283adacafbfcb5f176650b72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650136"
---
# <a name="deferred-transactions-sql-server"></a><span data-ttu-id="6887d-102">지연된 트랜잭션(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6887d-102">Deferred Transactions (SQL Server)</span></span>
  <span data-ttu-id="6887d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise에서는 손상된 트랜잭션이 롤백(실행 취소)에 필요한 데이터가 데이터베이스 시작 시 오프라인 상태인 경우에 지연될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise, a corrupted transaction can become deferred if data required by rollback (undo) is offline during database startup.</span></span> <span data-ttu-id="6887d-104">*지연된 트랜잭션* 은 롤포워드 단계가 완료될 때 커밋되지 않으며, 오류로 인해 롤백할 수 없는 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-104">A *deferred transaction* is a transaction that is uncommitted when the roll forward phase finishes and that has encountered an error that prevents it from being rolled back.</span></span> <span data-ttu-id="6887d-105">트랜잭션을 롤백할 수 없으므로 해당 트랜잭션은 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-105">Because the transaction cannot be rolled back, it is deferred.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6887d-106">손상된 트랜잭션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise에서만 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-106">Corrupted transactions are deferred only in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="6887d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 버전에서 트랜잭션이 손상되면 시작이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-107">In other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a corrupted transaction causes startup to fail.</span></span>  
  
 <span data-ttu-id="6887d-108">일반적으로 데이터베이스가 롤포워드되는 동안 I/O 오류로 인해 트랜잭션에 필요한 페이지를 읽을 수 없으므로 지연된 트랜잭션이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-108">Generally, a deferred transaction occurs because, while the database was being rolled forward, an I/O error prevented reading a page that was required by the transaction.</span></span> <span data-ttu-id="6887d-109">그러나 파일 수준에서의 오류로 인해 지연된 트랜잭션이 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-109">However, an error at the file level can also cause deferred transactions.</span></span> <span data-ttu-id="6887d-110">또한 트랜잭션 롤백이 필요한 시점에 부분 복원 시퀀스가 중지되고 오프라인 상태인 데이터가 트랜잭션에 필요하면 지연된 트랜잭션이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-110">A deferred transaction can also occur when a partial restore sequence stops at a point at which transaction rollback is necessary and a transaction requires data that is offline.</span></span>  
  
 <span data-ttu-id="6887d-111">롤백 중에 I/O 오류가 발생한 사용자 트랜잭션으로 인해 전체 데이터베이스가 오프라인 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-111">User transactions that are rolling back and hit an I/O error cause the whole database to go offline.</span></span> <span data-ttu-id="6887d-112">데이터베이스를 다시 온라인 상태로 만들면 다시 실행이 이전 잠금을 모두 다시 획득하며 커밋되지 않은 모든 트랜잭션을 롤백하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-112">When the database is brought back online, the redo reacquires all the locks it had and tries to roll back all the uncommitted transactions.</span></span> <span data-ttu-id="6887d-113">트랜잭션에 의해 수정된 모든 데이터는 해당 트랜잭션이 롤백될 때까지 적절하게 잠긴 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-113">All data modified by a transaction remains appropriately locked until the transaction can roll back.</span></span> <span data-ttu-id="6887d-114">롤백할 수 없는 트랜잭션은 손상이 복구되고 데이터베이스가 다시 시작되거나, 온라인 복원 후에 데이터베이스가 온라인 상태일 동안 지연된 트랜잭션이 해결될 때 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-114">Transactions that cannot be rolled back will give up their locks when the corruption is fixed and the database restarted or, after an online restore, when the deferred transactions are resolved while the database remains online.</span></span> <span data-ttu-id="6887d-115">그 전까지는 지연된 트랜잭션이 데이터베이스에서의 특정 작업 전체를 수행하지 못하게 하는 잠금을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-115">Until that point, a deferred transaction can hold locks that prevent certain operations on the database as a whole.</span></span> <span data-ttu-id="6887d-116">예를 들어 지연된 트랜잭션에 CREATE TABLE 명령이 있으면 지연된 트랜잭션이 해결될 때까지 어떤 사용자도 테이블을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-116">For example, if a deferred transaction contains a CREATE TABLE instruction, no user can create a table until the deferred transaction has been resolved.</span></span>  
  
 <span data-ttu-id="6887d-117">또한 증분 복원은 아직 복원되지 않고 현재 오프라인 상태인 파일 그룹에 영향을 주는 활성 트랜잭션이 하나 이상 있는 지점으로 데이터베이스를 복구하므로 지연된 트랜잭션이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-117">Deferred transaction can also occur because a piecemeal restore recovers a database to a point at which one or more active transactions are affecting a filegroup that has not yet been restored and is offline.</span></span> <span data-ttu-id="6887d-118">트랜잭션을 롤백할 수 없으므로 해당 트랜잭션은 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-118">Because the transactions cannot be rolled back, they become deferred.</span></span>  
  
 <span data-ttu-id="6887d-119">다음 표에서는 I/O 문제가 발생하는 경우 데이터베이스에서 복구를 수행하도록 하는 동작과 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-119">The following table lists the actions that cause a database to perform recovery and the outcome if an I/O problem occurs.</span></span>  
  
|<span data-ttu-id="6887d-120">작업</span><span class="sxs-lookup"><span data-stu-id="6887d-120">Action</span></span>|<span data-ttu-id="6887d-121">해결 방법(I/O 문제가 발생하거나 필요한 데이터가 오프라인 상태일 경우)</span><span class="sxs-lookup"><span data-stu-id="6887d-121">Resolution (if I/O problems occur or required data is offline)</span></span>|  
|------------|-----------------------------------------------------------------------|  
|<span data-ttu-id="6887d-122">서버 시작</span><span class="sxs-lookup"><span data-stu-id="6887d-122">Server start</span></span>|<span data-ttu-id="6887d-123">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6887d-123">Deferred transaction</span></span>|  
|<span data-ttu-id="6887d-124">복원</span><span class="sxs-lookup"><span data-stu-id="6887d-124">Restore</span></span>|<span data-ttu-id="6887d-125">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6887d-125">Deferred transaction</span></span>|  
|<span data-ttu-id="6887d-126">연결</span><span class="sxs-lookup"><span data-stu-id="6887d-126">Attach</span></span>|<span data-ttu-id="6887d-127">연결 실패</span><span class="sxs-lookup"><span data-stu-id="6887d-127">Attach fails</span></span>|  
|<span data-ttu-id="6887d-128">자동 재시작</span><span class="sxs-lookup"><span data-stu-id="6887d-128">Autorestart</span></span>|<span data-ttu-id="6887d-129">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6887d-129">Deferred transaction</span></span>|  
|<span data-ttu-id="6887d-130">데이터베이스 또는 데이터베이스 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="6887d-130">Create database or database snapshot</span></span>|<span data-ttu-id="6887d-131">만들기 실패</span><span class="sxs-lookup"><span data-stu-id="6887d-131">Creation fails</span></span>|  
|<span data-ttu-id="6887d-132">데이터베이스 미러링의 다시 실행</span><span class="sxs-lookup"><span data-stu-id="6887d-132">Redo on database mirroring</span></span>|<span data-ttu-id="6887d-133">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6887d-133">Deferred transaction</span></span>|  
|<span data-ttu-id="6887d-134">파일 그룹이 오프라인 상태</span><span class="sxs-lookup"><span data-stu-id="6887d-134">Filegroup is offline</span></span>|<span data-ttu-id="6887d-135">지연된 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="6887d-135">Deferred transaction</span></span>|  
  
## <a name="moving-a-transaction-out-of-the-deferred-state"></a><span data-ttu-id="6887d-136">지연된 상태 밖으로 트랜잭션 이동</span><span class="sxs-lookup"><span data-stu-id="6887d-136">Moving a Transaction Out of the DEFERRED State</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6887d-137">지연된 트랜잭션은 트랜잭션 로그를 활성 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-137">Deferred transactions keep the transaction log active.</span></span> <span data-ttu-id="6887d-138">지연된 트랜잭션을 포함하는 가상 로그 파일은 이러한 트랜잭션이 지연된 상태에서 벗어날 때까지는 잘릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-138">A virtual log file that contains any deferred transactions cannot be truncated until those transactions are moved out of the deferred state.</span></span> <span data-ttu-id="6887d-139">로그 잘림에 대한 자세한 내용은 [트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6887d-139">For more information about log truncation, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="6887d-140">트랜잭션을 지연된 상태에서 벗어나게 하려면 데이터베이스가 I/O 오류 없이 깨끗하게 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-140">To move the transaction out of the deferred state, the database must start cleanly without any I/O errors.</span></span> <span data-ttu-id="6887d-141">지연된 트랜잭션이 있으면 I/O 오류의 출처를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-141">If deferred transactions exist, you must fix the source of the I/O errors.</span></span> <span data-ttu-id="6887d-142">사용 가능한 해결 방법은 다음과 같으며 일반적으로 시도되는 순서대로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-142">The available solutions, listed in the order in which they are typically tried, are as follows:</span></span>  
  
-   <span data-ttu-id="6887d-143">데이터베이스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-143">Restart the database.</span></span> <span data-ttu-id="6887d-144">문제가 일시적인 경우에는 지연된 트랜잭션 없이 데이터베이스를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-144">If the problem was transient, the database should start without deferred transactions.</span></span>  
  
-   <span data-ttu-id="6887d-145">파일 그룹이 오프라인 상태이기 때문에 트랜잭션이 지연된 경우에는 해당 파일 그룹을 온라인 상태로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-145">If the transactions were deferred because a filegroup was offline, bring the filegroup back online.</span></span>  
  
     <span data-ttu-id="6887d-146">오프라인 상태의 파일 그룹을 다시 온라인 상태로 만들려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-146">To bring an offline filegroup back online, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   <span data-ttu-id="6887d-147">데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-147">Restore the database.</span></span> <span data-ttu-id="6887d-148">온라인 복원 후에 지연된 트랜잭션이 모두 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-148">After an online restore, any deferred transactions are resolved.</span></span>  
  
     <span data-ttu-id="6887d-149">전체 또는 대량 로그 복구 모델에서 몇 개의 손상된 페이지로 인해 지연된 트랜잭션이 발생한 경우 온라인 페이지 복원을 통해 오류를 해결할 수 있습니다(지원되는 경우).</span><span class="sxs-lookup"><span data-stu-id="6887d-149">Under the full or bulk-logged recovery model, if the deferred transactions were caused by only a few corrupted pages, an online page restore might resolve the errors (where supported).</span></span>  
  
-   <span data-ttu-id="6887d-150">지연된 트랜잭션을 발생하는 오프라인 상태인 파일 그룹이 더 이상 필요하지 않을 경우 오프라인 파일 그룹이 존재하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-150">If you are no longer require a filegroup whose offline status is causing deferred transactions, make the offline filegroup defunct.</span></span> <span data-ttu-id="6887d-151">파일 그룹이 오프라인 상태이므로 지연된 트랜잭션은 이 파일 그룹이 존재하지 않게 된 후에 지연된 상태에서 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-151">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6887d-152">존재하지 않는 파일 그룹은 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-152">A defunct filegroup can never be recovered.</span></span>  
  
     <span data-ttu-id="6887d-153">자세한 내용은 [존재하지 않는 파일 그룹 제거&#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6887d-153">For more information, see [Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6887d-154">잘못된 페이지 때문에 트랜잭션이 지연된 경우 및 올바른 데이터베이스 백업이 없는 경우 다음 프로세스에 따라 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-154">If transactions were deferred because of a bad page and if a good backup of the database does not exist, use the following process to repair the database:</span></span>  
  
    -   <span data-ttu-id="6887d-155">우선 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 데이터베이스를 응급 모드로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-155">First put the database into emergency mode by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         <span data-ttu-id="6887d-156">응급 모드에 대한 자세한 내용은 [Database States](../databases/database-states.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6887d-156">For information about emergency mode, see [Database States](../databases/database-states.md).</span></span>  
  
    -   <span data-ttu-id="6887d-157">그런 후에 DBCC 문인 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), [DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql), [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) 중 하나에 DBCC REPAIR_ALLOW_DATA_LOSS 옵션을 사용하여 데이터베이스를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-157">Then, repair the database by using the DBCC REPAIR_ALLOW_DATA_LOSS option in one of the following DBCC statements: [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), [DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql), or [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql).</span></span>  
  
         <span data-ttu-id="6887d-158">DBCC에서 잘못된 페이지가 발생하면 DBCC에서 할당을 취소하고 관련 오류를 모두 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-158">When DBCC encounters the bad page, DBCC deallocates it and repairs any related errors.</span></span> <span data-ttu-id="6887d-159">이 방법을 사용하면 물리적으로 일관된 상태로 데이터베이스를 다시 온라인 상태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-159">This approach enables the database to be brought back online in a physically consistent state.</span></span> <span data-ttu-id="6887d-160">그러나 추가 데이터가 손실될 수도 있으므로 이 방법은 마지막으로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6887d-160">However, additional data might also be lost; therefore, this approach should be used as a last resort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6887d-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6887d-161">See Also</span></span>  
 <span data-ttu-id="6887d-162">[복원 및 복구 개요&#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-162">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="6887d-163">[존재하지 않는 파일 그룹 제거&#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-163">[Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="6887d-164">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-164">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="6887d-165">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-165">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="6887d-166">[페이지 복원&#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-166">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="6887d-167">[증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6887d-167">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="6887d-168">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6887d-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="6887d-169">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6887d-169">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
