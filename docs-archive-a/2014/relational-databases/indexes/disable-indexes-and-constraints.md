---
title: 인덱스 및 제약 조건 비활성화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.disableindexes.f1
helpviewer_keywords:
- disabled indexes [SQL Server], index operations
- nonclustered indexes [SQL Server], disabling
- disabled indexes [SQL Server], guidelines
- clustered indexes, disabling
- constraints [SQL Server], disabling
- disabled indexes [SQL Server], viewing
- FOREIGN KEY constraints, disabling
- statistical information [SQL Server], indexes
- index disabling [SQL Server]
- indexed views [SQL Server], disabled indexes
ms.assetid: 2198f1af-fa44-47e9-92df-f4fde322ba18
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 40f9de4108be4defeb2353a9e7835c289641a819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740924"
---
# <a name="disable-indexes-and-constraints"></a><span data-ttu-id="f3fee-102">인덱스 및 제약 조건 비활성화</span><span class="sxs-lookup"><span data-stu-id="f3fee-102">Disable Indexes and Constraints</span></span>
  <span data-ttu-id="f3fee-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱스 또는 제약 조건을 비활성화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-103">This topic describes how to disable an index or constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f3fee-104">인덱스를 비활성화하면 사용자가 인덱스에 액세스할 수 없으며 클러스터형 인덱스의 경우 기본 테이블 데이터에도 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-104">Disabling an index prevents user access to the index, and for clustered indexes to the underlying table data.</span></span> <span data-ttu-id="f3fee-105">인덱스 정의는 메타데이터에 보관되고 인덱스 통계는 비클러스터형 인덱스에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-105">The index definition remains in metadata, and index statistics are kept on nonclustered indexes.</span></span> <span data-ttu-id="f3fee-106">뷰의 비클러스터형 또는 클러스터형 인덱스를 비활성화하면 인덱스 데이터가 물리적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-106">Disabling a nonclustered or clustered index on a view physically deletes the index data.</span></span> <span data-ttu-id="f3fee-107">테이블의 클러스터형 인덱스를 비활성화하면 테이블 데이터에 액세스할 수 없습니다. 데이터는 테이블에 계속 남아 있지만 인덱스를 삭제하거나 다시 작성할 때까지 DML(데이터 조작 언어) 작업에 데이터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-107">Disabling a clustered index on a table prevents access to the data; the data still remains in the table, but is unavailable for data manipulation language (DML) operations until the index is dropped or rebuilt.</span></span>  
  
 <span data-ttu-id="f3fee-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f3fee-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f3fee-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f3fee-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f3fee-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f3fee-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f3fee-111">보안</span><span class="sxs-lookup"><span data-stu-id="f3fee-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f3fee-112">**인덱스를 비활성화하려면:**</span><span class="sxs-lookup"><span data-stu-id="f3fee-112">**To disable an index, using:**</span></span>  
  
     [<span data-ttu-id="f3fee-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f3fee-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f3fee-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f3fee-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f3fee-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f3fee-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f3fee-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f3fee-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f3fee-117">비활성화된 인덱스는 유지 관리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-117">The index is not maintained while it is disabled.</span></span>  
  
-   <span data-ttu-id="f3fee-118">쿼리 최적화 프로그램에서 쿼리 실행 계획을 만들 때 비활성화된 인덱스는 고려하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-118">The query optimizer does not consider the disabled index when creating query execution plans.</span></span> <span data-ttu-id="f3fee-119">또한 테이블 힌트로 비활성화된 인덱스를 참조하는 쿼리가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-119">Also, queries that reference the disabled index with a table hint fail.</span></span>  
  
-   <span data-ttu-id="f3fee-120">기존의 비활성화된 인덱스와 같은 이름을 사용하는 인덱스는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-120">You cannot create an index that uses the same name as an existing disabled index.</span></span>  
  
-   <span data-ttu-id="f3fee-121">비활성화된 인덱스는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-121">A disabled index can be dropped.</span></span>  
  
-   <span data-ttu-id="f3fee-122">고유 인덱스를 비활성화하면 다른 테이블에서 인덱싱된 열을 참조하는 모든 FOREIGN KEY 제약 조건과 PRIMARY KEY 또는 UNIQUE 제약 조건도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-122">When disabling a unique index, the PRIMARY KEY or UNIQUE constraint and all FOREIGN KEY constraints that reference the indexed columns from other tables are also disabled.</span></span> <span data-ttu-id="f3fee-123">클러스터형 인덱스를 비활성화하는 경우 기본 테이블에 대한 들어오는 FOREIGN KEY 제약 조건과 나가는 FOREIGN KEY 제약 조건도 모두 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-123">When disabling a clustered index, all incoming and outgoing FOREIGN KEY constraints on the underlying table are also disabled.</span></span> <span data-ttu-id="f3fee-124">인덱스가 비활성화되면 경고 메시지에 제약 조건 이름이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-124">The constraint names are listed in a warning message when the index is disabled.</span></span> <span data-ttu-id="f3fee-125">인덱스를 다시 작성한 후 ALTER TABLE CHECK CONSTRAINT 문을 사용하여 모든 제약 조건을 수동으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-125">After rebuilding the index, all constraints must be manually enabled by using the ALTER TABLE CHECK CONSTRAINT statement.</span></span>  
  
-   <span data-ttu-id="f3fee-126">비클러스터형 인덱스는 관련 클러스터형 인덱스를 비활성화할 경우 자동으로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-126">Nonclustered indexes are automatically disabled when the associated clustered index is disabled.</span></span> <span data-ttu-id="f3fee-127">이렇게 비활성화된 인덱스는 테이블이나 뷰의 클러스터형 인덱스를 활성화하거나 테이블의 클러스터형 인덱스를 삭제해야 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-127">They cannot be enabled until either the clustered index on the table or view is enabled or the clustered index on the table is dropped.</span></span> <span data-ttu-id="f3fee-128">ALTER INDEX ALL REBUILD 문을 사용하여 클러스터형 인덱스를 활성화하지 않는 한 비클러스터형 인덱스는 명시적으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-128">Nonclustered indexes must be explicitly enabled, unless the clustered index was enabled by using the ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="f3fee-129">ALTER INDEX ALL REBUILD 문은 테이블의 비활성화된 인덱스를 모두 작성하고 비활성화합니다. 뷰의 비활성화된 인덱스는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-129">The ALTER INDEX ALL REBUILD statement rebuilds and enables all disabled indexes on the table, except for disabled indexes on views.</span></span> <span data-ttu-id="f3fee-130">뷰의 인덱스는 별도의 ALTER INDEX ALL REBUILD 문으로 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-130">Indexes on views must be enabled in a separate ALTER INDEX ALL REBUILD statement.</span></span>  
  
-   <span data-ttu-id="f3fee-131">테이블에서 클러스터형 인덱스를 비활성화하면 해당 테이블을 참조하는 뷰의 모든 클러스터형 인덱스와 비클러스터형 인덱스도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-131">Disabling a clustered index on a table also disables all clustered and nonclustered indexes on views that reference that table.</span></span> <span data-ttu-id="f3fee-132">이러한 인덱스는 참조되는 테이블의 인덱스에 따라 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-132">These indexes must be rebuilt just as those on the referenced table.</span></span>  
  
-   <span data-ttu-id="f3fee-133">클러스터형 인덱스를 삭제하거나 다시 작성할 경우를 제외하고는 비활성화된 클러스터형 인덱스의 데이터 행에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-133">The data rows of the disabled clustered index cannot be accessed except to drop or rebuild the clustered index.</span></span>  
  
-   <span data-ttu-id="f3fee-134">테이블에 비활성화된 클러스터형 인덱스가 없으면 비활성화된 비클러스터형 인덱스를 온라인으로 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-134">You can rebuild a disabled nonclustered index online when the table does not have a disabled clustered index.</span></span> <span data-ttu-id="f3fee-135">그러나 ALTER INDEX REBUILD 또는 CREATE INDEX WITH DROP_EXISTING 문을 사용하는 경우에는 비활성화된 클러스터형 인덱스를 오프라인으로 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-135">However, you must always rebuild a disabled clustered index offline if you use either the ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING statement.</span></span> <span data-ttu-id="f3fee-136">온라인 인덱스 작업에 대한 자세한 내용은 [온라인으로 인덱스 작업 수행](perform-index-operations-online.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3fee-136">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="f3fee-137">비활성화된 클러스터형 인덱스가 있는 테이블에서는 CREATE STATISTICS 문을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-137">The CREATE STATISTICS statement cannot be successfully executed on a table that has a disabled clustered index.</span></span>  
  
-   <span data-ttu-id="f3fee-138">인덱스가 비활성화된 상태이고 다음 조건에 해당하면 AUTO_CREATE_STATISTICS 데이터베이스 옵션이 열에 대한 새 통계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-138">The AUTO_CREATE_STATISTICS database option creates new statistics on a column when the index is disabled and the following conditions exist:</span></span>  
  
    -   <span data-ttu-id="f3fee-139">AUTO_CREATE_STATISTICS가 ON으로 설정된 경우</span><span class="sxs-lookup"><span data-stu-id="f3fee-139">AUTO_CREATE_STATISTICS is set to ON</span></span>  
  
    -   <span data-ttu-id="f3fee-140">열에 대한 기존 통계가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="f3fee-140">There are no existing statistics for the column.</span></span>  
  
    -   <span data-ttu-id="f3fee-141">쿼리 최적화 동안 통계가 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="f3fee-141">Statistics are required during query optimization.</span></span>  
  
-   <span data-ttu-id="f3fee-142">클러스터형 인덱스가 비활성화되면 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 가 기본 테이블에 대한 정보를 반환할 수 없습니다. 대신 이 문은 클러스터형 인덱스가 비활성화되었다고 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-142">If a clustered index is disabled, [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) cannot return information about the underlying table; instead, the statement reports that the clustered index is disabled.</span></span> <span data-ttu-id="f3fee-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) 를 사용하여 비활성화된 인덱스의 조각 모음을 수행할 수 없습니다. 이 문은 실패하고 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-143">[DBCC INDEXDEFRAG](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql) cannot be used to defragment a disabled index; the statement fails with an error message.</span></span> <span data-ttu-id="f3fee-144">[DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) 를 사용하여 비활성화된 인덱스를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-144">You can use [DBCC DBREINDEX](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) to rebuild a disabled index.</span></span>  
  
-   <span data-ttu-id="f3fee-145">새 클러스터형 인덱스를 만들면 이전에 비활성화된 비클러스터형 인덱스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-145">Creating a new clustered index enables previously disabled nonclustered indexes.</span></span> <span data-ttu-id="f3fee-146">자세한 내용은 [Enable Indexes and Constraints](enable-indexes-and-constraints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3fee-146">For more information, see [Enable Indexes and Constraints](enable-indexes-and-constraints.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f3fee-147">보안</span><span class="sxs-lookup"><span data-stu-id="f3fee-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f3fee-148">권한</span><span class="sxs-lookup"><span data-stu-id="f3fee-148">Permissions</span></span>  
 <span data-ttu-id="f3fee-149">ALTER INDEX를 실행하려면 최소한 테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-149">To execute ALTER INDEX, at a minimum, ALTER permission on the table or view is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f3fee-150">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f3fee-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="f3fee-151">인덱스를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="f3fee-151">To disable an index</span></span>  
  
1.  <span data-ttu-id="f3fee-152">개체 탐색기에서 더하기 기호를 클릭하여 인덱스를 비활성화할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable an index.</span></span>  
  
2.  <span data-ttu-id="f3fee-153">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-153">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="f3fee-154">더하기 기호를 클릭하여 인덱스를 비활성화할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-154">Click the plus sign to expand the table on which you want to disable an index.</span></span>  
  
4.  <span data-ttu-id="f3fee-155">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-155">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="f3fee-156">비활성화할 인덱스를 마우스 오른쪽 단추로 클릭하고 **사용 안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-156">Right-click the index you want to disable and select **Disable**.</span></span>  
  
6.  <span data-ttu-id="f3fee-157">**인덱스 비활성화** 대화 상자에서 올바른 인덱스가 **비활성화할 인덱스** 표에 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-157">In the **Disable Indexes** dialog box, verify that the correct index is in the **Indexes to disable** grid and click **OK**.</span></span>  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="f3fee-158">테이블의 모든 인덱스를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="f3fee-158">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="f3fee-159">개체 탐색기에서 더하기 기호를 클릭하여 인덱스를 비활성화할 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-159">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to disable the indexes.</span></span>  
  
2.  <span data-ttu-id="f3fee-160">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-160">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="f3fee-161">더하기 기호를 클릭하여 인덱스를 비활성화할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-161">Click the plus sign to expand the table on which you want to disable the indexes.</span></span>  
  
4.  <span data-ttu-id="f3fee-162">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **모두 사용 안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-162">Right-click the **Indexes** folder and select **Disable All**.</span></span>  
  
5.  <span data-ttu-id="f3fee-163">**인덱스 비활성화** 대화 상자에서 올바른 인덱스가 **비활성화할 인덱스** 표에 있는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-163">In the **Disable Indexes** dialog box, verify that the correct indexes are in the **Indexes to disable** grid and click **OK**.</span></span> <span data-ttu-id="f3fee-164">**비활성화할 인덱스** 표에서 인덱스를 제거하려면 인덱스를 선택한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-164">To remove an index from the **Indexes to disable** grid, select the index and then press the Delete key.</span></span>  
  
 <span data-ttu-id="f3fee-165">**인덱스 비활성화** 대화 상자에는 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-165">The following information is available in the **Disable Indexes** dialog box:</span></span>  
  
 <span data-ttu-id="f3fee-166">**Index Name**</span><span class="sxs-lookup"><span data-stu-id="f3fee-166">**Index Name**</span></span>  
 <span data-ttu-id="f3fee-167">인덱스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-167">Displays the name of the index.</span></span> <span data-ttu-id="f3fee-168">실행하는 동안 이 열에는 상태를 나타내는 아이콘도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-168">During execution, this column also displays an icon representing the status.</span></span>  
  
 <span data-ttu-id="f3fee-169">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="f3fee-169">**Table Name**</span></span>  
 <span data-ttu-id="f3fee-170">인덱스가 생성된 테이블 또는 뷰의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-170">Displays the name of the table or view that the index was created on.</span></span>  
  
 <span data-ttu-id="f3fee-171">**인덱스 유형**</span><span class="sxs-lookup"><span data-stu-id="f3fee-171">**Index Type**</span></span>  
 <span data-ttu-id="f3fee-172">인덱스의 유형( **클러스터형**, **비클러스터형**, **공간**또는 **XML**)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-172">Displays the type of the index: **Clustered**, **Nonclustered**, **Spatial**, or **XML**.</span></span>  
  
 <span data-ttu-id="f3fee-173">**상태**</span><span class="sxs-lookup"><span data-stu-id="f3fee-173">**Status**</span></span>  
 <span data-ttu-id="f3fee-174">비활성화 작업의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-174">Displays the status of the disable operation.</span></span> <span data-ttu-id="f3fee-175">실행 후에 표시될 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-175">Possible values after execution are:</span></span>  
  
-   <span data-ttu-id="f3fee-176">비어 있음</span><span class="sxs-lookup"><span data-stu-id="f3fee-176">Blank</span></span>  
  
     <span data-ttu-id="f3fee-177">실행 전에 **상태** 가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-177">Prior to execution **Status** is blank.</span></span>  
  
-   <span data-ttu-id="f3fee-178">**진행 중**</span><span class="sxs-lookup"><span data-stu-id="f3fee-178">**In progress**</span></span>  
  
     <span data-ttu-id="f3fee-179">인덱스 비활성화가 시작되었지만 아직 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-179">Disabling of the indexes has been started but is not complete.</span></span>  
  
-   <span data-ttu-id="f3fee-180">**Success**</span><span class="sxs-lookup"><span data-stu-id="f3fee-180">**Success**</span></span>  
  
     <span data-ttu-id="f3fee-181">비활성화 작업이 성공적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-181">The disable operation completed successfully.</span></span>  
  
-   <span data-ttu-id="f3fee-182">**오류**</span><span class="sxs-lookup"><span data-stu-id="f3fee-182">**Error**</span></span>  
  
     <span data-ttu-id="f3fee-183">인덱스 비활성화 작업을 실행하는 동안 오류가 발생하여 작업을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-183">An error was encountered during the index disable operation, and the operation did not complete successfully.</span></span>  
  
-   <span data-ttu-id="f3fee-184">**중지됨**</span><span class="sxs-lookup"><span data-stu-id="f3fee-184">**Stopped**</span></span>  
  
     <span data-ttu-id="f3fee-185">사용자가 작업을 중지하여 인덱스 비활성화가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-185">The disable of the index was not completed successfully because the user stopped the operation.</span></span>  
  
 <span data-ttu-id="f3fee-186">**메시지**</span><span class="sxs-lookup"><span data-stu-id="f3fee-186">**Message**</span></span>  
 <span data-ttu-id="f3fee-187">비활성화 작업을 실행하는 동안 오류 메시지 텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-187">Provides the text of error messages during the disable operation.</span></span> <span data-ttu-id="f3fee-188">실행 중에는 오류 텍스트가 하이퍼링크로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-188">During execution, errors appear as hyperlinks.</span></span> <span data-ttu-id="f3fee-189">하이퍼링크에는 오류 내용을 설명하는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-189">The text of the hyperlinks describes the body of the error.</span></span> <span data-ttu-id="f3fee-190">대개의 경우 **메시지** 열에는 전체 메시지 텍스트의 일부만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-190">The **Message** column is rarely wide enough to read the full message text.</span></span> <span data-ttu-id="f3fee-191">다음과 같은 두 가지 방법으로 전체 텍스트를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-191">There are two ways to get the full text:</span></span>  
  
-   <span data-ttu-id="f3fee-192">마우스 포인터를 메시지 셀 위로 이동하여 오류 텍스트가 나타나는 도구 설명을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-192">Move the mouse pointer over the message cell to display a ToolTip with the error text.</span></span>  
  
-   <span data-ttu-id="f3fee-193">하이퍼링크를 클릭하여 전체 오류 메시지가 있는 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-193">Click the hyperlink to display a dialog box displaying the full error.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f3fee-194">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f3fee-194">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-an-index"></a><span data-ttu-id="f3fee-195">인덱스를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="f3fee-195">To disable an index</span></span>  
  
1.  <span data-ttu-id="f3fee-196">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-196">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f3fee-197">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-197">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f3fee-198">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-198">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- disables the IX_Employee_OrganizationLevel_OrganizationNode index  
    -- on the HumanResources.Employee table  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee  
    DISABLE;  
    ```  
  
#### <a name="to-disable-all-indexes-on-a-table"></a><span data-ttu-id="f3fee-199">테이블의 모든 인덱스를 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="f3fee-199">To disable all indexes on a table</span></span>  
  
1.  <span data-ttu-id="f3fee-200">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-200">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f3fee-201">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-201">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f3fee-202">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f3fee-202">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Disables all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    DISABLE;  
    ```  
  
 <span data-ttu-id="f3fee-203">자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3fee-203">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
