---
title: 변경 내용 추적 관리(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tracking data changes [SQL Server]
- change tracking [SQL Server], overhead
- change tracking [SQL Server]
- change tracking [SQL Server], managing
ms.assetid: 94a8d361-e897-4d6d-9a8f-1bb652e7a850
author: rothja
ms.author: jroth
ms.openlocfilehash: 36409f2ce256325da1c9849e5bec7e7ce114cf25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650856"
---
# <a name="manage-change-tracking-sql-server"></a><span data-ttu-id="a8b5a-102">변경 내용 추적 관리(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a8b5a-102">Manage Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="a8b5a-103">이 항목에서는 변경 내용 추적을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-103">This topic describes how to manage change tracking.</span></span> <span data-ttu-id="a8b5a-104">또한 보안을 구성하는 방법과 변경 내용 추적을 사용할 때 스토리지 및 성능에 미치는 영향을 확인하는 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-104">It also describes how to configure security and determine the effects on storage and performance when change tracking is used.</span></span>  
  
## <a name="managing-change-tracking"></a><span data-ttu-id="a8b5a-105">변경 내용 추적 관리</span><span class="sxs-lookup"><span data-stu-id="a8b5a-105">Managing Change Tracking</span></span>  
 <span data-ttu-id="a8b5a-106">다음 섹션에서는 변경 내용 추적 관리와 관련된 카탈로그 뷰, 사용 권한 및 설정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-106">The following sections list catalog views, permissions, and settings that are relevant for managing change tracking.</span></span>  
  
### <a name="catalog-views"></a><span data-ttu-id="a8b5a-107">카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="a8b5a-107">Catalog Views</span></span>  
 <span data-ttu-id="a8b5a-108">다음 카탈로그 뷰를 사용하여 변경 내용 추적이 설정된 테이블 및 데이터베이스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-108">To determine which tables and databases have change tracking enabled, you can use the following catalog views:</span></span>  
  
-   [<span data-ttu-id="a8b5a-109">sys.change_tracking_databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8b5a-109">sys.change_tracking_databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases)  
  
-   [<span data-ttu-id="a8b5a-110">sys.change_tracking_tables&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8b5a-110">sys.change_tracking_tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables)  
  
 <span data-ttu-id="a8b5a-111">[sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 카탈로그 뷰는 사용자 테이블에 대한 변경 내용 추적을 설정할 때 만든 내부 테이블도 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-111">Also, the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view lists the internal tables that are created when change tracking is enabled for a user table.</span></span>  
  
### <a name="security"></a><span data-ttu-id="a8b5a-112">보안</span><span class="sxs-lookup"><span data-stu-id="a8b5a-112">Security</span></span>  
 <span data-ttu-id="a8b5a-113">[변경 내용 추적 함수](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)를 사용하여 변경 내용 추적 정보에 액세스하려면 보안 주체에 다음 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-113">To access change tracking information by using the [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql), the principal must have the following permissions:</span></span>  
  
-   <span data-ttu-id="a8b5a-114">변경 내용 추적이 설정된 쿼리하는 테이블에 있는 한 개 이상의 기본 키 열에 대한 SELECT 권한</span><span class="sxs-lookup"><span data-stu-id="a8b5a-114">SELECT permission on at least the primary key columns on the change-tracked table to the table that is being queried.</span></span>  
  
-   <span data-ttu-id="a8b5a-115">변경 내용을 가져오는 테이블에 대한 VIEW CHANGE TRACKING 권한.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-115">VIEW CHANGE TRACKING permission on the table for which changes are being obtained.</span></span> <span data-ttu-id="a8b5a-116">VIEW CHANGE TRACKING 권한이 필요한 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-116">The VIEW CHANGE TRACKING permission is required for the following reasons:</span></span>  
  
    -   <span data-ttu-id="a8b5a-117">변경 내용 추적 레코드에는 삭제된 행, 특히 삭제된 행의 기본 키 값에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-117">Change tracking records include information about rows that have been deleted, specifically the primary key values of the rows that have been deleted.</span></span> <span data-ttu-id="a8b5a-118">일부 중요한 데이터를 삭제한 후에 보안 주체에게 변경 내용 추적이 설정된 테이블에 대한 SELECT 권한이 부여되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-118">A principal could have been granted SELECT permission for a change tracked table after some sensitive data had been deleted.</span></span> <span data-ttu-id="a8b5a-119">이러한 경우 해당 보안 주체가 변경 내용 추적을 사용하여 삭제된 정보에 액세스하지 못하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-119">In this case, you would not want that principal to be able to access that deleted information by using change tracking.</span></span>  
  
    -   <span data-ttu-id="a8b5a-120">변경 내용 추적 정보는 업데이트 작업으로 변경된 열에 대한 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-120">Change tracking information can store information about which columns have been changed by update operations.</span></span> <span data-ttu-id="a8b5a-121">보안 주체는 중요한 정보가 포함된 열에 대한 권한이 거부될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-121">A principal could be denied permission to a column that contains sensitive information.</span></span> <span data-ttu-id="a8b5a-122">변경 내용 추적 정보를 사용할 수 있으므로 보안 주체는 열 값이 업데이트되었는지를 확인할 수 있지만 해당 열의 값은 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-122">However, because change tracking information is available, a principal can determine that a column value has been updated, but the principal cannot determine the value of the column.</span></span>  
  
## <a name="understanding-change-tracking-overhead"></a><span data-ttu-id="a8b5a-123">변경 내용 추적 오버헤드 이해</span><span class="sxs-lookup"><span data-stu-id="a8b5a-123">Understanding Change Tracking Overhead</span></span>  
 <span data-ttu-id="a8b5a-124">테이블에 변경 내용 추적이 설정되면 일부 관리 작업에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-124">When change tracking is enabled for a table, some administration operations are affected.</span></span> <span data-ttu-id="a8b5a-125">다음 표에서는 작업 및 고려해야 하는 영향에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-125">The following table lists the operations and the effects you should consider.</span></span>  
  
|<span data-ttu-id="a8b5a-126">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="a8b5a-126">Operation</span></span>|<span data-ttu-id="a8b5a-127">변경 내용 추적이 설정된 경우</span><span class="sxs-lookup"><span data-stu-id="a8b5a-127">When change tracking is enabled</span></span>|  
|---------------|-------------------------------------|  
|<span data-ttu-id="a8b5a-128">DROP TABLE</span><span class="sxs-lookup"><span data-stu-id="a8b5a-128">DROP TABLE</span></span>|<span data-ttu-id="a8b5a-129">삭제된 테이블에 대한 모든 변경 내용 추적 정보가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-129">All change tracking information for the dropped table is removed.</span></span>|  
|<span data-ttu-id="a8b5a-130">ALTER TABLE DROP CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="a8b5a-130">ALTER TABLE DROP CONSTRAINT</span></span>|<span data-ttu-id="a8b5a-131">PRIMARY KEY 제약 조건을 삭제하려는 시도가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-131">An attempt to drop the PRIMARY KEY constraint will fail.</span></span> <span data-ttu-id="a8b5a-132">변경 내용 추적을 해제해야 PRIMARY KEY 제약 조건을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-132">Change tracking must be disabled before a PRIMARY KEY constraint can be dropped.</span></span>|  
|<span data-ttu-id="a8b5a-133">ALTER TABLE DROP COLUMN</span><span class="sxs-lookup"><span data-stu-id="a8b5a-133">ALTER TABLE DROP COLUMN</span></span>|<span data-ttu-id="a8b5a-134">삭제된 열이 기본 키의 일부일 경우 변경 내용 추적과 관계없이 해당 열을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-134">If a column that is being dropped is part of the primary key, dropping the column is not allowed, regardless of change tracking.</span></span><br /><br /> <span data-ttu-id="a8b5a-135">삭제된 열이 기본 키의 일부가 아닐 경우 해당 열을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-135">If the column that is being dropped is not part of the primary key, dropping the column succeeds.</span></span> <span data-ttu-id="a8b5a-136">그러나 이 데이터를 동기화하는 애플리케이션에 미치는 영향에 대해 먼저 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-136">However, the effect on any application that is synchronizing this data should be understood first.</span></span> <span data-ttu-id="a8b5a-137">테이블에 열 변경 내용 추적이 설정되어 있을 경우 삭제된 열이 여전히 변경 내용 추적 정보의 일부로 반환될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-137">If column change tracking is enabled for the table, the dropped column might still be returned as part of the change tracking information.</span></span> <span data-ttu-id="a8b5a-138">삭제된 열은 애플리케이션에서 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-138">It is the responsibility of the application to handle the dropped column.</span></span>|  
|<span data-ttu-id="a8b5a-139">ALTER TABLE ADD COLUMN</span><span class="sxs-lookup"><span data-stu-id="a8b5a-139">ALTER TABLE ADD COLUMN</span></span>|<span data-ttu-id="a8b5a-140">변경 내용 추적이 설정된 테이블에 새 열이 추가될 경우 이 열 추가 작업은 추적되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-140">If a new column is added to the change tracked table, the addition of the column is not tracked.</span></span> <span data-ttu-id="a8b5a-141">새 열에 대해 수행된 업데이트 및 변경 내용만 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-141">Only the updates and changes that are made to the new column are tracked.</span></span>|  
|<span data-ttu-id="a8b5a-142">ALTER TABLE ALTER COLUMN</span><span class="sxs-lookup"><span data-stu-id="a8b5a-142">ALTER TABLE ALTER COLUMN</span></span>|<span data-ttu-id="a8b5a-143">기본 키가 아닌 열의 데이터 형식 변경 내용은 추적되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-143">Data type changes of a non-primary key columns are not tracked.</span></span>|  
|<span data-ttu-id="a8b5a-144">ALTER TABLE SWITCH</span><span class="sxs-lookup"><span data-stu-id="a8b5a-144">ALTER TABLE SWITCH</span></span>|<span data-ttu-id="a8b5a-145">테이블 중 하나 또는 둘 모두에 변경 내용 추적이 설정된 경우 파티션 전환에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-145">Switching a partition fails if one or both of the tables has change tracking enabled.</span></span>|  
|<span data-ttu-id="a8b5a-146">DROP INDEX 또는 ALTER INDEX DISABLE</span><span class="sxs-lookup"><span data-stu-id="a8b5a-146">DROP INDEX, or ALTER INDEX DISABLE</span></span>|<span data-ttu-id="a8b5a-147">기본 키를 강제 적용하는 인덱스는 삭제 또는 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-147">The index that enforces the primary key cannot be dropped or disabled.</span></span>|  
|<span data-ttu-id="a8b5a-148">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="a8b5a-148">TRUNCATE TABLE</span></span>|<span data-ttu-id="a8b5a-149">테이블 잘라내기는 변경 내용 추적이 설정된 테이블에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-149">Truncating a table can be performed on a table that has change tracking enabled.</span></span> <span data-ttu-id="a8b5a-150">그러나 이 작업으로 삭제된 행은 추적되지 않으며 유효한 최소 버전이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-150">However, the rows that are deleted by the operation are not tracked, and the minimum valid version is updated.</span></span> <span data-ttu-id="a8b5a-151">애플리케이션이 버전을 검사할 때 해당 버전이 너무 오래되어 다시 초기화해야 한다고 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-151">When an application checks its version, the check indicates that the version is too old and a reinitialization is required.</span></span> <span data-ttu-id="a8b5a-152">이는 해당 테이블의 변경 내용 추적이 해제된 다음 다시 설정되는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-152">This is the same as change tracking being disabled, and then reenabled for the table.</span></span>|  
  
 <span data-ttu-id="a8b5a-153">변경 내용 추적을 사용하더라도 변경 내용 추적 정보가 작업의 일부로 저장되므로 DML 작업에는 오버헤드가 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-153">Using change tracking does add some overhead to DML operations because of the change tracking information that is being stored as part of the operation.</span></span>  
  
### <a name="effects-on-dml"></a><span data-ttu-id="a8b5a-154">DML에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="a8b5a-154">Effects on DML</span></span>  
 <span data-ttu-id="a8b5a-155">변경 내용 추적은 DML 작업에 대한 성능 오버헤드를 최소화하도록 최적화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-155">Change tracking has been optimized to minimize the performance overhead on DML operations.</span></span> <span data-ttu-id="a8b5a-156">테이블에 변경 내용 추적을 사용하는 것과 연관된 증분 성능 오버헤드는 테이블에 대해 인덱스가 생성되어 유지 관리가 필요해질 때 발생하는 오버헤드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-156">The incremental performance overhead that is associated with using change tracking on a table is similar to the overhead incurred when an index is created for a table and needs to be maintained.</span></span>  
  
 <span data-ttu-id="a8b5a-157">DML 작업으로 변경된 각 행의 경우 내부 변경 내용 추적 테이블에 한 개의 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-157">For each row that is changed by a DML operation, a row is added to the internal change tracking table.</span></span> <span data-ttu-id="a8b5a-158">DML 작업과 관련한 이런 영향은 다음과 같은 다양한 요소에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-158">The effect of this relative to the DML operation depends on various factors, such as the following:</span></span>  
  
-   <span data-ttu-id="a8b5a-159">기본 키 열의 수</span><span class="sxs-lookup"><span data-stu-id="a8b5a-159">The number of primary key columns</span></span>  
  
-   <span data-ttu-id="a8b5a-160">사용자 테이블 행에서 변경되는 데이터의 양</span><span class="sxs-lookup"><span data-stu-id="a8b5a-160">The amount of data that is being changed in the user table row</span></span>  
  
-   <span data-ttu-id="a8b5a-161">트랜잭션에서 수행되는 작업의 수</span><span class="sxs-lookup"><span data-stu-id="a8b5a-161">The number of operations that are being performed in a transaction</span></span>  
  
 <span data-ttu-id="a8b5a-162">스냅샷 격리를 사용하는 경우에도 변경 내용 추적의 설정 여부와 관계없이 모든 DML 작업에 대한 성능에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-162">Snapshot isolation, if used, also has an effect on performance for all DML operations, whether change tracking is enabled or not.</span></span>  
  
### <a name="effects-on-storage"></a><span data-ttu-id="a8b5a-163">스토리지에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="a8b5a-163">Effects on Storage</span></span>  
 <span data-ttu-id="a8b5a-164">변경 내용 추적 데이터는 다음과 같은 유형의 내부 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-164">Change tracking data is stored in the following types of internal tables:</span></span>  
  
-   <span data-ttu-id="a8b5a-165">내부 변경 테이블</span><span class="sxs-lookup"><span data-stu-id="a8b5a-165">Internal change table</span></span>  
  
     <span data-ttu-id="a8b5a-166">변경 내용 추적을 설정한 각 사용자 테이블에 대해 하나의 내부 변경 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-166">There is one internal change table for each user table that has change tracking enabled.</span></span>  
  
-   <span data-ttu-id="a8b5a-167">내부 트랜잭션 테이블</span><span class="sxs-lookup"><span data-stu-id="a8b5a-167">Internal transaction table</span></span>  
  
     <span data-ttu-id="a8b5a-168">데이터베이스에 대해 하나의 내부 트랜잭션 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-168">There is one internal transaction table for the database.</span></span>  
  
 <span data-ttu-id="a8b5a-169">이러한 내부 테이블은 다음과 같은 방법으로 스토리지 요구 사항에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-169">These internal tables affect storage requirements in the following ways:</span></span>  
  
-   <span data-ttu-id="a8b5a-170">사용자 테이블에 있는 각 행에 대한 개별 변경 내용의 경우 내부 변경 내용 테이블에 한 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-170">For each change to each row in the user table, a row is added to the internal change table.</span></span> <span data-ttu-id="a8b5a-171">이 행에는 작은 고정 오버헤드와 기본 키 열의 크기와 같은 가변 오버헤드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-171">This row has a small fixed overhead plus a variable overhead equal to the size of the primary key columns.</span></span> <span data-ttu-id="a8b5a-172">이 행은 애플리케이션이 설정한 선택적 컨텍스트 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-172">The row can contain optional context information set by an application.</span></span> <span data-ttu-id="a8b5a-173">그리고 열 추적이 설정된 경우 변경된 각 열은 추적 테이블에 4바이트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-173">And, if column tracking is enabled, each changed column requires 4 bytes in the tracking table.</span></span>  
  
-   <span data-ttu-id="a8b5a-174">커밋된 각 트랜잭션에 대해 하나의 행이 내부 트랜잭션 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-174">For each committed transaction, a row is added to an internal transaction table.</span></span>  
  
 <span data-ttu-id="a8b5a-175">다른 내부 테이블을 사용할 때와 같이 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 저장 프로시저를 사용하여 변경 내용 추적 테이블에 사용되는 공간을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-175">As with other internal tables, you can determine the space used for the change tracking tables by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) stored procedure.</span></span> <span data-ttu-id="a8b5a-176">내부 테이블의 이름은 다음 예와 같이 [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) 카탈로그 뷰를 사용하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8b5a-176">The names of the internal tables can be obtained by using the [sys.internal_tables](/sql/relational-databases/system-catalog-views/sys-internal-tables-transact-sql) catalog view, as shown in the following example.</span></span>  
  
```sql  
sp_spaceused 'sys.change_tracking_309576141'  
sp_spaceused 'sys.syscommittab'  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8b5a-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8b5a-177">See Also</span></span>  
 <span data-ttu-id="a8b5a-178">[데이터 변경 내용 추적&#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-178">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="a8b5a-179">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-179">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="a8b5a-180">[데이터베이스 속성&#40;변경 내용 추적 페이지&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-180">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="a8b5a-181">[ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-181">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="a8b5a-182">[sys.change_tracking_databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-182">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="a8b5a-183">[sys.change_tracking_tables&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-183">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="a8b5a-184">[데이터 변경 내용 추적&#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-184">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="a8b5a-185">[변경 내용 추적 정보&#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8b5a-185">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="a8b5a-186">변경 데이터 작업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8b5a-186">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
