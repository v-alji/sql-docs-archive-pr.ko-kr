---
title: Suspect_pages 테이블 관리(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dd7aea63ae85a16e23ff532c7e18ace3c376a707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661176"
---
# <a name="manage-the-suspect_pages-table-sql-server"></a><span data-ttu-id="f40d4-102">suspect_pages 테이블 관리(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f40d4-102">Manage the suspect_pages Table (SQL Server)</span></span>
  <span data-ttu-id="f40d4-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] suspect_pages [!INCLUDE[tsql](../../includes/tsql-md.md)]테이블을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-103">This topic describes how to manage the **suspect_pages** table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f40d4-104">주의 대상 페이지에 대한 정보를 유지 관리하는 데 사용되는 **suspect_pages** 테이블은 복원이 필요한지 여부를 결정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-104">The **suspect_pages** table is used for maintaining information about suspect pages, and is relevant in helping to decide whether a restore is necessary.</span></span> <span data-ttu-id="f40d4-105">[suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) 테이블은 [msdb 데이터베이스](../databases/msdb-database.md)에 상주합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-105">The [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) table resides in the [msdb database](../databases/msdb-database.md).</span></span>  
  
 <span data-ttu-id="f40d4-106">[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 에서 데이터 페이지를 읽으려고 할 때 다음 오류 중 하나가 발생하면 페이지가 "주의 대상"으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-106">A page is considered "suspect" when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] encounters one of the following errors when it tries to read a data page:</span></span>  
  
-   <span data-ttu-id="f40d4-107">디스크 오류 (특정 하드웨어 오류)와 같이 운영 체제에서 실행 되는 CRC (순환 중복 검사)로 인해 발생 한 [823 오류](../errors-events/mssqlserver-823-database-engine-error.md) 입니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-107">An [823 error](../errors-events/mssqlserver-823-database-engine-error.md) that was caused by a cyclic redundancy check (CRC) issued by the operating system, such as a disk error (certain hardware errors)</span></span>  
  
-   <span data-ttu-id="f40d4-108">조각난 페이지 (논리적 오류)와 같은 [824 오류](../errors-events/mssqlserver-824-database-engine-error.md)</span><span class="sxs-lookup"><span data-stu-id="f40d4-108">An [824 error](../errors-events/mssqlserver-824-database-engine-error.md), such as a torn page (any logical error)</span></span>  
  
 <span data-ttu-id="f40d4-109">모든 주의 대상 페이지의 페이지 ID는 **suspect_pages** 테이블에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-109">The page ID of every suspect page is recorded in the **suspect_pages** table.</span></span> <span data-ttu-id="f40d4-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 다음과 같은 정상적인 처리 중에 발생하는 모든 주의 대상 페이지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-110">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] records any suspect pages encountered during regular processing, such as the following:</span></span>  
  
-   <span data-ttu-id="f40d4-111">쿼리에서 페이지를 읽어야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="f40d4-111">A query has to read a page.</span></span>  
  
-   <span data-ttu-id="f40d4-112">DBCC CHECKDB 작업이 수행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="f40d4-112">During a DBCC CHECKDB operation.</span></span>  
  
-   <span data-ttu-id="f40d4-113">백업 작업이 수행 중인 경우</span><span class="sxs-lookup"><span data-stu-id="f40d4-113">During a backup operation.</span></span>  
  
 <span data-ttu-id="f40d4-114">또한 복원 작업, DBCC 복구 작업 또는 데이터베이스 삭제 작업 동안 필요한 경우 **suspect_pages** 테이블이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-114">The **suspect_pages** table is also updated as necessary during a restore operation, a DBCC repair operation, or a drop database operation.</span></span>  
  
 <span data-ttu-id="f40d4-115">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f40d4-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f40d4-116">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f40d4-116">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f40d4-117">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f40d4-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f40d4-118">보안</span><span class="sxs-lookup"><span data-stu-id="f40d4-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f40d4-119">**다음을 사용하여 suspect_pages 테이블을 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="f40d4-119">**To manage the suspect_pages table, using:**</span></span>  
  
     [<span data-ttu-id="f40d4-120">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f40d4-120">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f40d4-121">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f40d4-121">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f40d4-122">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f40d4-122">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f40d4-123">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f40d4-123">Recommendations</span></span>  
  
-   <span data-ttu-id="f40d4-124">**suspect_pages 테이블에 기록되는 오류**</span><span class="sxs-lookup"><span data-stu-id="f40d4-124">**Errors Recorded in suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f40d4-125">**suspect_pages** 테이블은 824 오류가 발생하여 실패한 페이지당 하나의 행을 포함합니다(최대 1,000개 행까지).</span><span class="sxs-lookup"><span data-stu-id="f40d4-125">The **suspect_pages** table contains one row per page that failed with an 824 error, up to a limit of 1,000 rows.</span></span> <span data-ttu-id="f40d4-126">다음 표에서는 **suspect_pages** 테이블의 **event_type** 열에 기록되는 오류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-126">The following table shows errors logged in the **event_type** column of the **suspect_pages** table.</span></span>  
  
    |<span data-ttu-id="f40d4-127">오류 설명</span><span class="sxs-lookup"><span data-stu-id="f40d4-127">Error description</span></span>|<span data-ttu-id="f40d4-128">**event_type** 값</span><span class="sxs-lookup"><span data-stu-id="f40d4-128">**event_type** value</span></span>|  
    |-----------------------|---------------------------|  
    |<span data-ttu-id="f40d4-129">운영 체제 CRC 오류로 인해 발생하는 823 오류 또는 잘못된 체크섬이나 조각난 페이지 이외의 824 오류(예: 잘못된 페이지 ID)</span><span class="sxs-lookup"><span data-stu-id="f40d4-129">823 error caused by an operating system CRC error  or 824 error other than a bad checksum or a torn page (for example, a bad page ID)</span></span>|<span data-ttu-id="f40d4-130">1</span><span class="sxs-lookup"><span data-stu-id="f40d4-130">1</span></span>|  
    |<span data-ttu-id="f40d4-131">잘못된 체크섬</span><span class="sxs-lookup"><span data-stu-id="f40d4-131">Bad checksum</span></span>|<span data-ttu-id="f40d4-132">2</span><span class="sxs-lookup"><span data-stu-id="f40d4-132">2</span></span>|  
    |<span data-ttu-id="f40d4-133">조각난 페이지</span><span class="sxs-lookup"><span data-stu-id="f40d4-133">Torn page</span></span>|<span data-ttu-id="f40d4-134">3</span><span class="sxs-lookup"><span data-stu-id="f40d4-134">3</span></span>|  
    |<span data-ttu-id="f40d4-135">복원됨(페이지가 잘못된 것으로 표시된 후 복원됨)</span><span class="sxs-lookup"><span data-stu-id="f40d4-135">Restored (The page was restored after it was marked bad)</span></span>|<span data-ttu-id="f40d4-136">4</span><span class="sxs-lookup"><span data-stu-id="f40d4-136">4</span></span>|  
    |<span data-ttu-id="f40d4-137">복구됨(DBCC, AlwaysOn, 또는 페이지를 미러링 복구함)</span><span class="sxs-lookup"><span data-stu-id="f40d4-137">Repaired (DBCC, AlwaysOn, or mirroring repaired the page)</span></span>|<span data-ttu-id="f40d4-138">5</span><span class="sxs-lookup"><span data-stu-id="f40d4-138">5</span></span>|  
    |<span data-ttu-id="f40d4-139">DBCC에 의해 할당 취소됨</span><span class="sxs-lookup"><span data-stu-id="f40d4-139">Deallocated by DBCC</span></span>|<span data-ttu-id="f40d4-140">7</span><span class="sxs-lookup"><span data-stu-id="f40d4-140">7</span></span>|  
  
     <span data-ttu-id="f40d4-141">또한 **suspect_pages** 테이블에서 일시적인 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-141">The **suspect_pages** table also records transient errors.</span></span> <span data-ttu-id="f40d4-142">일시적인 오류의 원인으로는 I/O 오류(예: 케이블 연결 끊김) 또는 일시적으로 반복 체크섬 테스트에 실패한 페이지 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-142">Sources of transient errors include an I/O error (for example, a cable was disconnected) or a page that temporarily fails a repeated checksum test.</span></span>  
  
-   <span data-ttu-id="f40d4-143">**데이터베이스 엔진의 suspect_pages 테이블 업데이트 방법**</span><span class="sxs-lookup"><span data-stu-id="f40d4-143">**How the Database Engine Updates the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f40d4-144">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 **suspect_pages** 테이블에 대해 다음 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-144">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes the following actions on the **suspect_pages** table:</span></span>  
  
    -   <span data-ttu-id="f40d4-145">테이블이 꽉 차지 않았다면 824 오류가 발생할 때마다 업데이트되어 오류 발생이 표시되고 오류 카운터가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-145">If the table is not full, it is updated for every 824 error, to indicate that an error has occurred, and the error counter is incremented.</span></span> <span data-ttu-id="f40d4-146">페이지를 복구, 복원 또는 할당 취소하여 수정한 후에도 오류가 있으면 **number_of_errors** 수가 증가하고 해당 **last_update** 열이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-146">If a page has an error after it is fixed by being repaired, restored, or deallocated, its **number_of_errors** count is incremented and its **last_update** column is updated</span></span>  
  
    -   <span data-ttu-id="f40d4-147">나열된 페이지를 복원 또는 복구 작업으로 수정하면 **suspect_pages** 행이 업데이트되어 페이지가 복구(**event_type** = 5) 또는 복원(**event_type** = 4)되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-147">After a listed page is fixed by a restore or a repair operation, the operation updates the **suspect_pages** row to indicate that the page is repaired (**event_type** = 5) or restored (**event_type** = 4).</span></span>  
  
    -   <span data-ttu-id="f40d4-148">DBCC Check를 실행하면 오류가 없는 페이지는 복구(**event_type** = 5) 또는 할당 취소(**event_type** = 7)된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-148">If a DBCC check is run, the check marks any error-free pages as repaired (**event_type** = 5) or deallocated (**event_type** = 7).</span></span>  
  
-   <span data-ttu-id="f40d4-149">**suspect_pages 테이블의 자동 업데이트**</span><span class="sxs-lookup"><span data-stu-id="f40d4-149">**Automatic Updates to the suspect_pages Table**</span></span>  
  
     <span data-ttu-id="f40d4-150">데이터 파일에서 페이지를 읽으려는 시도가 다음 이유 중 하나로 실패하면 데이터베이스 미러링 파트너 또는 AlwaysOn 가용성 복제본이 **suspect_pages** 테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-150">A database mirroring partner or AlwaysOn availability replica updates the **suspect_pages** table after an attempt to read a page from a data file fails for one of the following reasons.</span></span>  
  
    -   <span data-ttu-id="f40d4-151">운영 체제 CRC 오류로 인해 발생하는 823 오류</span><span class="sxs-lookup"><span data-stu-id="f40d4-151">An 823 error that is caused by an operating system CRC error.</span></span>  
  
    -   <span data-ttu-id="f40d4-152">824 오류(조각난 페이지와 같은 논리적 손상)</span><span class="sxs-lookup"><span data-stu-id="f40d4-152">An 824 error (logical corruption such as a torn page).</span></span>  
  
     <span data-ttu-id="f40d4-153">다음 동작을 수행하면 **suspect_pages** 테이블에서 행이 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-153">The following actions also automatically update rows in the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="f40d4-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS는 **suspect_pages** 테이블을 업데이트하여 할당 취소되었거나 복구된 각 페이지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-154">DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS updates the **suspect_pages** table to indicate each page that it has deallocated or repaired.</span></span>  
  
    -   <span data-ttu-id="f40d4-155">전체, 파일 또는 페이지 복원을 수행하면 페이지 항목이 복원된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-155">A full, file, or page RESTORE marks the page entries as restored.</span></span>  
  
     <span data-ttu-id="f40d4-156">다음 동작을 수행하면 **suspect_pages** 테이블에서 행이 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-156">The following actions automatically delete rows from the **suspect_pages** table.</span></span>  
  
    -   <span data-ttu-id="f40d4-157">ALTER DATABASE REMOVE FILE</span><span class="sxs-lookup"><span data-stu-id="f40d4-157">ALTER DATABASE REMOVE FILE</span></span>  
  
    -   <span data-ttu-id="f40d4-158">DROP DATABASE</span><span class="sxs-lookup"><span data-stu-id="f40d4-158">DROP DATABASE</span></span>  
  
-   <span data-ttu-id="f40d4-159">**데이터베이스 관리자의 유지 관리 역할**</span><span class="sxs-lookup"><span data-stu-id="f40d4-159">**Maintenance Role of the Database Administrator**</span></span>  
  
     <span data-ttu-id="f40d4-160">데이터베이스 관리자는 주로 오래된 행을 삭제함으로써 테이블을 관리할 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-160">Database administrators are responsible for managing the table, primarily by deleting old rows.</span></span> <span data-ttu-id="f40d4-161">**suspect_pages** 테이블은 크기에 제한이 있으며 모두 채워지면 더 이상 새로운 오류가 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-161">The **suspect_pages** table is limited in size, and if it fills, new errors are not logged.</span></span> <span data-ttu-id="f40d4-162">이 테이블이 꽉 차지 않게 하려면 데이터베이스 관리자나 시스템 관리자가 이 테이블에서 행을 삭제하여 오래된 항목을 수동으로 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-162">To prevent this table from filling up, the database administrator or system administrator must manually clear out old entries from this table by deleting rows.</span></span> <span data-ttu-id="f40d4-163">따라서 **event_type** 이 복원됨 또는 복구됨인 행이나 **last_update** 값이 오래된 행을 주기적으로 삭제하거나 보관하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-163">Therefore, we recommend that you periodically delete or archive rows that have an **event_type** of restored or repaired, or rows that have an old **last_update** value.</span></span>  
  
     <span data-ttu-id="f40d4-164">suspect_pages 테이블에서 작업을 모니터링하기 위해 [Database Suspect Data Page 이벤트 클래스](../event-classes/database-suspect-data-page-event-class.md)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-164">To monitor the activity on the suspect_pages table, you can use the [Database Suspect Data Page Event Class](../event-classes/database-suspect-data-page-event-class.md).</span></span> <span data-ttu-id="f40d4-165">일시적인 오류로 인해 행이 **suspect_pages** 테이블에 추가되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-165">Rows are sometimes added to the **suspect_pages** table because of transient errors.</span></span> <span data-ttu-id="f40d4-166">그러나 많은 행이 이 테이블에 추가되는 경우 I/O 하위 시스템에 문제가 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-166">If many rows are being added to the table, however, a problem probably exists with the I/O subsystem.</span></span> <span data-ttu-id="f40d4-167">이 테이블에 추가되는 행 수가 갑자기 증가하는 경우에는 I/O 하위 시스템에 발생한 문제가 있는지 조사해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-167">If you notice a sudden increase in the number of rows being added to the table, we recommend that you investigate possible problems in your I/O subsystem.</span></span>  
  
     <span data-ttu-id="f40d4-168">데이터베이스 관리자는 또한 레코드를 삽입하거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-168">A database administrator can also insert or update records.</span></span> <span data-ttu-id="f40d4-169">예를 들어 데이터베이스 관리자가 특정 주의 대상 페이지가 존재함을 알고 있지만 잠시 동안 해당 레코드를 보존하려는 경우 행 업데이트가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-169">For example, updating a row might useful when the database administrator knows that a particular suspect page is actually intact, but wants to preserve the record for a while.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f40d4-170">보안</span><span class="sxs-lookup"><span data-stu-id="f40d4-170">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f40d4-171">권한</span><span class="sxs-lookup"><span data-stu-id="f40d4-171">Permissions</span></span>  
 <span data-ttu-id="f40d4-172">**msdb** 에 대한 액세스 권한이 있는 사용자는 **suspect_pages** 테이블의 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-172">Anyone with access to **msdb** can read the data in the **suspect_pages** table.</span></span> <span data-ttu-id="f40d4-173">suspect_pages 테이블에 대한 UPDATE 권한이 있는 사용자는 레코드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-173">Anyone with UPDATE permission on the suspect_pages table can update its records.</span></span> <span data-ttu-id="f40d4-174">**msdb** 의 **db_owner** 고정 데이터베이스 역할 또는 **sysadmin** 고정 서버 역할의 멤버는 레코드를 삽입, 업데이트 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-174">Members the **db_owner** fixed database role on **msdb** or the **sysadmin** fixed server role can insert, update, and delete records.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f40d4-175">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f40d4-175">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="f40d4-176">suspect_pages 테이블을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="f40d4-176">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="f40d4-177">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하고 해당 인스턴스를 확장한 다음 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-177">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="f40d4-178">**시스템 데이터베이스**, **msdb**, **테이블**및 **시스템 테이블**을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-178">Expand **System Databases**, expand **msdb**, expand **Tables**, and then expand **System Tables**.</span></span>  
  
3.  <span data-ttu-id="f40d4-179">**dbo.suspect_pages** 를 확장하고 **상위 200개 행 편집**을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-179">Expand **dbo.suspect_pages** and right-click **Edit Top 200 Rows**.</span></span>  
  
4.  <span data-ttu-id="f40d4-180">쿼리 창에서 원하는 행을 편집, 업데이트 또는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-180">In the query window, edit, update, or delete the rows that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f40d4-181">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f40d4-181">Using Transact-SQL</span></span>  
  
#### <a name="to-manage-the-suspect_pages-table"></a><span data-ttu-id="f40d4-182">suspect_pages 테이블을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="f40d4-182">To manage the suspect_pages table</span></span>  
  
1.  <span data-ttu-id="f40d4-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-183">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f40d4-184">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-184">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f40d4-185">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-185">Copy and paste the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="f40d4-186">이 예에서는 `suspect_pages` 테이블에서 일부 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-186">This example deletes some of the rows from the `suspect_pages` table.</span></span>  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 <span data-ttu-id="f40d4-187">이 예에서는 `suspect_pages` 테이블에 있는 잘못된 페이지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f40d4-187">This example returns the bad pages in the `suspect_pages` table.</span></span>  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f40d4-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f40d4-188">See Also</span></span>  
 <span data-ttu-id="f40d4-189">[DROP DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f40d4-189">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 <span data-ttu-id="f40d4-190">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f40d4-190">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f40d4-191">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f40d4-191">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f40d4-192">[DBCC&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f40d4-192">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="f40d4-193">[페이지 복원&#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f40d4-193">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="f40d4-194">[Transact-sql&#41;suspect_pages &#40;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f40d4-194">[suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql) </span></span>  
 <span data-ttu-id="f40d4-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="f40d4-195">[MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md) </span></span>  
 [<span data-ttu-id="f40d4-196">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="f40d4-196">MSSQLSERVER_824</span></span>](../errors-events/mssqlserver-824-database-engine-error.md)  
  
  
