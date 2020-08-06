---
title: 데이터베이스의 복구 모델 보기 또는 변경(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889080301109938f0514bd6b81265c100237ab60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734180"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a><span data-ttu-id="2c00e-102">데이터베이스 복구 모델 보기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="2c00e-102">View or Change the Recovery Model of a Database (SQL Server)</span></span>
  <span data-ttu-id="2c00e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스의 복구 모델을 보거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-103">This topic describes how to view or change the recovery model of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2c00e-104">*복구 모델* 은 트랜잭션이 로깅되는 방법, 트랜잭션 로그에 백업이 필요하며 허용되는지 여부 및 사용 가능한 복원 작업의 종류를 제어하는 데이터베이스 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-104">A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires (and allows) backing up, and what kinds of restore operations are available.</span></span> <span data-ttu-id="2c00e-105">사용할 수 있는 복구 모델은 3가지로 단순, 전체 및 대량 로그 복구 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-105">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="2c00e-106">일반적으로 데이터베이스는 전체 복구 모델이나 단순 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-106">Typically, a database uses the full recovery model or simple recovery model.</span></span> <span data-ttu-id="2c00e-107">데이터베이스는 언제든지 다른 복구 모델로 전환이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-107">A database can be switched to another recovery model at any time.</span></span> <span data-ttu-id="2c00e-108">**model** 데이터베이스는 새 데이터베이스의 기본 복구 모델을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-108">The **model** database sets the default recovery model of new databases.</span></span>  
  
 <span data-ttu-id="2c00e-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2c00e-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2c00e-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2c00e-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2c00e-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="2c00e-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2c00e-112">보안</span><span class="sxs-lookup"><span data-stu-id="2c00e-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2c00e-113">**다음을 사용하여 데이터베이스의 복구 모델을 보거나 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="2c00e-113">**To view or change the recovery model of a database, using:**</span></span>  
  
     [<span data-ttu-id="2c00e-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2c00e-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2c00e-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c00e-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2c00e-116">**후속 권장 사항:**  [복구 모델을 변경한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2c00e-116">**Follow Up Recommendations:**  [After You Change the Recovery Model](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="2c00e-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2c00e-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2c00e-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2c00e-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2c00e-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="2c00e-119">Recommendations</span></span>  
  
-   <span data-ttu-id="2c00e-120">전체 복구 모델 또는 대량 로그 복구 모델에서 전환하기 전에 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-120">Before switching from the full recovery or bulk-logged recovery model, back up the transaction log.</span></span>  
  
-   <span data-ttu-id="2c00e-121">대량 로그 모델에서는 지정 시간 복구를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-121">Point-in-time recovery is not possible with bulk-logged model.</span></span> <span data-ttu-id="2c00e-122">따라서 트랜잭션 로그 복원이 필요할 수 있는 대량 로그 모델에서 트랜잭션을 실행하는 경우 이러한 트랜잭션이 데이터 손실에 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-122">Therefore, if you run transactions under the bulk-logged recovery model that might require a transaction log restore, these transactions could be exposed to data loss.</span></span> <span data-ttu-id="2c00e-123">재해 복구 시나리오에서 데이터 복구 기능을 최대화하기 위해 다음 조건에서만 대량 로그 복구 모델로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-123">To maximize data recoverability in a disaster-recovery scenario, we recommend that you switch to the bulk-logged recovery model only under the following conditions:</span></span>  
  
    -   <span data-ttu-id="2c00e-124">사용자가 현재 데이터베이스에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-124">Users are currently not allowed in the database.</span></span>  
  
    -   <span data-ttu-id="2c00e-125">대량 프로세스 중 수정된 모든 내용은 로그 백업을 수행하지 않고 대량 프로세스를 다시 실행하는 등의 방법으로 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-125">All modifications made during bulk processing are recoverable without depending on taking a log backup; for example, by re-running the bulk processes.</span></span>  
  
     <span data-ttu-id="2c00e-126">이러한 두 조건을 충족하면 대량 로그 복구 모델에서 백업된 트랜잭션 로그를 복원하는 동안 데이터 손실에 노출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-126">If you satisfy these two conditions, you will not be exposed to any data loss while restoring a transaction log that was backed up under the bulk-logged recovery model..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c00e-127">대량 작업 중에 전체 복구 모델로 전환하면 대량 작업의 로깅이 최소 로깅에서 전체 로깅으로 바뀌며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-127">If you switch to the full recovery model during a bulk operation, the logging of the bulk operation changes from minimal logging to full logging, and vice versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2c00e-128">보안</span><span class="sxs-lookup"><span data-stu-id="2c00e-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2c00e-129">권한</span><span class="sxs-lookup"><span data-stu-id="2c00e-129">Permissions</span></span>  
 <span data-ttu-id="2c00e-130">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-130">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2c00e-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2c00e-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-recovery-model"></a><span data-ttu-id="2c00e-132">복구 모델을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2c00e-132">To view or change the recovery model</span></span>  
  
1.  <span data-ttu-id="2c00e-133">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-133">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="2c00e-134">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-134">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="2c00e-135">데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하면 **데이터베이스 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-135">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="2c00e-136">**페이지 선택** 창에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-136">In the **Select a page** pane, click **Options**.</span></span>  
  
5.  <span data-ttu-id="2c00e-137">현재 복구 모델이 **복구 모델** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-137">The current recovery model is displayed in the **Recovery model** list box.</span></span>  
  
6.  <span data-ttu-id="2c00e-138">필요에 따라 복구 모델을 변경하려면 다른 모델 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-138">Optionally, to change the recovery model select a different model list.</span></span> <span data-ttu-id="2c00e-139">**전체**, **대량 로그**또는 **단순**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-139">The choices are **Full**, **Bulk-logged**, or **Simple**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2c00e-140">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="2c00e-140">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-recovery-model"></a><span data-ttu-id="2c00e-141">복구 모델을 보려면</span><span class="sxs-lookup"><span data-stu-id="2c00e-141">To view the recovery model</span></span>  
  
1.  <span data-ttu-id="2c00e-142">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-142">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c00e-143">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c00e-144">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2c00e-145">이 예에서는 [모델](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 데이터베이스의 복구 모델을 배우기 위해 **sys.databases** 카탈로그 뷰를 쿼리하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-145">This example shows how to query the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to learn the recovery model of the **model** database.</span></span>  
  
```sql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a><span data-ttu-id="2c00e-146">복구 모델을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="2c00e-146">To change the recovery model</span></span>  
  
1.  <span data-ttu-id="2c00e-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c00e-148">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c00e-149">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2c00e-150">이 예에서는 `model` ALTER DATABASE `FULL` 문의 `SET RECOVERY` 옵션을 사용하여 [데이터베이스의 복구 모델을](/sql/t-sql/statements/alter-database-transact-sql-set-options) 로 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-150">This example shows how to change the recovery model in the `model` database to `FULL` by using the `SET RECOVERY` option of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement.</span></span>  
  
```sql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="follow-up-recommendations-after-you-change-the-recovery-model"></a><a name="FollowUp"></a><span data-ttu-id="2c00e-151">후속 권장 사항: 복구 모델을 변경한 후</span><span class="sxs-lookup"><span data-stu-id="2c00e-151">Follow Up Recommendations: After You Change the Recovery Model</span></span>  
  
-   <span data-ttu-id="2c00e-152">**전체 및 대량 로그 복구 모델 간에 전환한 후**</span><span class="sxs-lookup"><span data-stu-id="2c00e-152">**After switching between the full and bulk-logged recovery models**</span></span>  
  
    -   <span data-ttu-id="2c00e-153">대량 작업을 완료한 후에는 즉시 전체 복구 모드로 다시 전환하세요.</span><span class="sxs-lookup"><span data-stu-id="2c00e-153">After completing the bulk operations, immediately switch back to full recovery mode.</span></span>  
  
    -   <span data-ttu-id="2c00e-154">대량 로그 복구 모델에서 다시 전체 복구 모델로 전환한 후 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-154">After switching from the bulk-logged recovery model back to the full recovery model, back up the log.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2c00e-155">백업 전략에 따라 계속해서 주기적인 데이터베이스, 로그 및 차등 백업 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-155">Your backup strategy remains the same: continue performing periodic database, log, and differential backups.</span></span>  
  
-   <span data-ttu-id="2c00e-156">**단순 복구 모델에서 전환한 후**</span><span class="sxs-lookup"><span data-stu-id="2c00e-156">**After switching from the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="2c00e-157">전체 복구 모델이나 대량 로그 복구 모델로 전환한 후 즉시 전체 또는 차등 데이터베이스 백업을 수행하여 로그 체인을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-157">Immediately after switching to the full recovery model or bulk-logged recovery model, take a full or differential database backup to start the log chain.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2c00e-158">전체 로그 복구 모델이나 대량 로그 복구 모델로의 전환은 첫 번째 데이터 백업 후에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-158">The switch to the full or bulk-logged recovery model takes effect only after the first data backup.</span></span>  
  
    -   <span data-ttu-id="2c00e-159">정기적인 로그 백업을 예약하고 해당 일정에 따라 복원 계획을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-159">Schedule regular log backups, and update your restore plan accordingly.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="2c00e-160">로그를 자주 백업하지 않으면 트랜잭션 로그가 확장되어 디스크 공간이 부족해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-160">If you do not back up the log frequently enough, the transaction log can expand until it runs out of disk space.</span></span>  
  
-   <span data-ttu-id="2c00e-161">**단순 복구 모델로 전환한 후**</span><span class="sxs-lookup"><span data-stu-id="2c00e-161">**After switching to the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="2c00e-162">트랜잭션 로그 백업에 대한 모든 예약된 작업을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-162">Discontinue any scheduled jobs for backing up the transaction log.</span></span>  
  
    -   <span data-ttu-id="2c00e-163">정기적 데이터베이스 백업이 예약 되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-163">Ensure periodic database backups are scheduled.</span></span> <span data-ttu-id="2c00e-164">데이터베이스를 백업하는 것은 데이터를 보호하고 트랜잭션 로그의 비활성 부분을 자르는 데 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="2c00e-164">Backing up your database is essential both to protect your data and to truncate the inactive portion of the transaction log.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2c00e-165">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2c00e-165">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2c00e-166">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2c00e-166">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="2c00e-167">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2c00e-167">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="2c00e-168">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="2c00e-168">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="2c00e-169">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="2c00e-169">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="2c00e-170">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2c00e-170">Related Content</span></span>  
  
-   <span data-ttu-id="2c00e-171">[데이터베이스 유지 관리 계획](../maintenance-plans/maintenance-plans.md) ( [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 온라인 설명서)</span><span class="sxs-lookup"><span data-stu-id="2c00e-171">[Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) (in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c00e-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c00e-172">See Also</span></span>  
 <span data-ttu-id="2c00e-173">[복구 모델&#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2c00e-173">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="2c00e-174">[트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2c00e-174">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="2c00e-175">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c00e-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="2c00e-176">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c00e-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="2c00e-177">복구 모델&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2c00e-177">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
