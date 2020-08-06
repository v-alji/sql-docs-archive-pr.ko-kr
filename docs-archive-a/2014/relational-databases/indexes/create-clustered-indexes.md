---
title: 클러스터형 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], clustered indexes
- clustered indexes, creating
- clustered indexes, PRIMARY KEY constraint
- clustered indexes, UNIQUE constraint
- indexes [SQL Server], clustered
ms.assetid: 47148383-c2c7-4f08-a9e4-7016bf2d1d13
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 567ff9a01bd93323149168b9e3aa0f34d78aee39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649994"
---
# <a name="create-clustered-indexes"></a><span data-ttu-id="a5661-102">클러스터형 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="a5661-102">Create Clustered Indexes</span></span>
  <span data-ttu-id="a5661-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블에 클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-103">You can create clustered indexes on tables in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a5661-104">몇 가지 경우를 제외하고 모든 테이블에는 클러스터형 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-104">With few exceptions, every table should have a clustered index.</span></span> <span data-ttu-id="a5661-105">쿼리 성능을 향상시키는 것 외에도 요청 시 클러스터형 인덱스를 다시 작성하거나 다시 구성하여 테이블 조각화를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-105">Besides improving query performance, a clustered index can be rebuilt or reorganized on demand to control table fragmentation.</span></span> <span data-ttu-id="a5661-106">뷰에서 클러스터형 인덱스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-106">A clustered index can also be created on a view.</span></span> <span data-ttu-id="a5661-107">클러스터형된 인덱스는 [클러스터형 및 비클러스터형 인덱스 소개](clustered-and-nonclustered-indexes-described.md)항목에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-107">(Clustered indexes are defined in the topic [Clustered and Nonclustered Indexes Described](clustered-and-nonclustered-indexes-described.md).)</span></span>  
  
 <span data-ttu-id="a5661-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a5661-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a5661-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a5661-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a5661-110">일반적인 구현 방법</span><span class="sxs-lookup"><span data-stu-id="a5661-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="a5661-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a5661-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a5661-112">보안</span><span class="sxs-lookup"><span data-stu-id="a5661-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a5661-113">**테이블에 클러스터형 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="a5661-113">**To create a clustered index on a table, using:**</span></span>  
  
     [<span data-ttu-id="a5661-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a5661-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a5661-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a5661-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a5661-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a5661-116">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="a5661-117">일반적인 구현 방법</span><span class="sxs-lookup"><span data-stu-id="a5661-117">Typical Implementations</span></span>  
 <span data-ttu-id="a5661-118">클러스터형 인덱스는 다음과 같은 방법으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-118">Clustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="a5661-119">**PRIMARY KEY 및 UNIQUE 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="a5661-119">**PRIMARY KEY and UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="a5661-120">PRIMARY KEY 제약 조건을 만들 때 테이블에 클러스터형 인덱스가 없으며 고유 비클러스터형 인덱스를 지정하지 않은 경우 열에 고유 클러스터형 인덱스가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-120">When you create a PRIMARY KEY constraint, a unique clustered index on the column or columns is automatically created if a clustered index on the table does not already exist and you do not specify a unique nonclustered index.</span></span> <span data-ttu-id="a5661-121">기본 키 열에는 NULL 값이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-121">The primary key column cannot allow NULL values.</span></span>  
  
     <span data-ttu-id="a5661-122">UNIQUE 제약 조건을 만들면 고유 비클러스터형 인덱스가 생성되어 기본적으로 UNIQUE 제약 조건을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-122">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="a5661-123">테이블에 클러스터형 인덱스가 없는 경우 고유 클러스터형 인덱스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-123">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span>  
  
     <span data-ttu-id="a5661-124">제약 조건의 일부로 생성된 인덱스에는 제약 조건 이름과 같은 이름이 자동으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-124">An index created as part of the constraint is automatically given the same name as the constraint name.</span></span> <span data-ttu-id="a5661-125">자세한 내용은 [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) 및 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5661-125">For more information, see [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) and [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="a5661-126">**제약 조건의 영향을 받지 않는 인덱스**</span><span class="sxs-lookup"><span data-stu-id="a5661-126">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="a5661-127">비클러스터형 PRIMARY KEY 제약 조건이 지정된 경우 기본 키 열이 아닌 열의 클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-127">You can create a clustered index on a column other than primary key column if a nonclustered primary key constraint was specified.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a5661-128">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a5661-128">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a5661-129">클러스터형 인덱스 구조를 만들 때는 각 파일과 파일 그룹에서 기존(원본) 구조와 새(대상) 구조를 위한 디스크 공간이 모두 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-129">When a clustered index structure is created, disk space for both the old (source) and new (target) structures is required in their respective files and filegroups.</span></span> <span data-ttu-id="a5661-130">기존 구조는 인덱스 생성 트랜잭션이 커밋된 후 할당 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-130">The old structure is not deallocated until the complete transaction commits.</span></span> <span data-ttu-id="a5661-131">정렬에 사용할 임시 디스크 공간이 추가로 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-131">Additional temporary disk space for sorting may also be required.</span></span> <span data-ttu-id="a5661-132">자세한 내용은 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5661-132">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
-   <span data-ttu-id="a5661-133">기존의 비클러스터형 인덱스를 여러 개 포함하는 힙에 클러스터형 인덱스를 만들 때는 RID(행 식별자) 대신 클러스터링 키 값을 포함하도록 모든 비클러스터형 인덱스를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-133">If a clustered index is created on a heap with several existing nonclustered indexes, all the nonclustered indexes must be rebuilt so that they contain the clustering key value instead of the row identifier (RID).</span></span> <span data-ttu-id="a5661-134">마찬가지로 비클러스터형 인덱스가 여러 개 있는 테이블에서 클러스터형 인덱스를 삭제하면 DROP 작업의 일부로 비클러스터형 인덱스가 모두 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-134">Similarly, if a clustered index is dropped on a table that has several nonclustered indexes, the nonclustered indexes are all rebuilt as part of the DROP operation.</span></span> <span data-ttu-id="a5661-135">대형 테이블에서는 이 작업을 수행하는 데 시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-135">This may take significant time on large tables.</span></span>  
  
     <span data-ttu-id="a5661-136">대형 테이블에 인덱스를 만들 경우 클러스터형 인덱스로 시작하고 비클러스터형 인덱스를 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-136">The preferred way to build indexes on large tables is to start with the clustered index and then build any nonclustered indexes.</span></span> <span data-ttu-id="a5661-137">기존 테이블에 인덱스를 만들 때는 ONLINE 옵션을 ON으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-137">Consider setting the ONLINE option to ON when you create indexes on existing tables.</span></span> <span data-ttu-id="a5661-138">이 옵션을 ON으로 설정하면 장기 테이블 잠금이 보유되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-138">When set to ON, long-term table locks are not held.</span></span> <span data-ttu-id="a5661-139">따라서 기본 테이블에 대한 쿼리나 업데이트를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-139">This enables queries or updates to the underlying table to continue.</span></span> <span data-ttu-id="a5661-140">자세한 내용은 [Perform Index Operations Online](perform-index-operations-online.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5661-140">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
-   <span data-ttu-id="a5661-141">클러스터형 인덱스의 인덱스 키는 ROW_OVERFLOW_DATA 할당 단위에 기존 데이터가 있는 `varchar` 열을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-141">The index key of a clustered index cannot contain `varchar` columns that have existing data in the ROW_OVERFLOW_DATA allocation unit.</span></span> <span data-ttu-id="a5661-142">`varchar` 열에 대한 클러스터형 인덱스를 만들고 기존 데이터가 IN_ROW_DATA 할당 단위에 있는 경우에는 데이터를 행 외부로 밀어넣는 열에 대한 후속 삽입 또는 업데이트 동작이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-142">If a clustered index is created on a `varchar` column and the existing data is in the IN_ROW_DATA allocation unit, subsequent insert or update actions on the column that would push the data off-row will fail.</span></span> <span data-ttu-id="a5661-143">행 오버플로 데이터가 포함될 수 있는 테이블에 대한 정보를 얻으려면 [sys.dm_db_index_physical_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) 동적 관리 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-143">To obtain information about tables that might contain row-overflow data, use the [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) dynamic management function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a5661-144">보안</span><span class="sxs-lookup"><span data-stu-id="a5661-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a5661-145">권한</span><span class="sxs-lookup"><span data-stu-id="a5661-145">Permissions</span></span>  
 <span data-ttu-id="a5661-146">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-146">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="a5661-147">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-147">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a5661-148">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a5661-148">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-object-explorer"></a><span data-ttu-id="a5661-149">개체 탐색기를 사용하여 클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a5661-149">To create a clustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="a5661-150">개체 탐색기에서 클러스터형 인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-150">In Object Explorer, expand the table on which you want to create a clustered index.</span></span>  
  
2.  <span data-ttu-id="a5661-151">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 가리킨 다음, **클러스터형 인덱스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-151">Right-click the **Indexes** folder, point to **New Index**, and select **Clustered Index...**.</span></span>  
  
3.  <span data-ttu-id="a5661-152">**새 인덱스** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 새 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-152">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
4.  <span data-ttu-id="a5661-153">**인덱스 키 열** 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-153">Under **Index key columns**, click **Add...**.</span></span>  
  
5.  <span data-ttu-id="a5661-154">_Table_name_ **에서 열 선택**대화 상자에서 클러스터형 인덱스에 추가할 테이블 열의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-154">In the **Select Columns from**_table_name_ dialog box, select the check box of the table column to be added to the clustered index.</span></span>  
  
6.  <span data-ttu-id="a5661-155">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-155">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a5661-156">**새 인덱스** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-156">In the **New Index** dialog box, click **OK**.</span></span>  
  
#### <a name="to-create-a-clustered-index-by-using-the-table-designer"></a><span data-ttu-id="a5661-157">테이블 디자이너를 사용하여 클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a5661-157">To create a clustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="a5661-158">개체 탐색기에서 클러스터형 인덱스를 사용하여 테이블을 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-158">In Object Explorer, expand the database on which you want to create a table with a clustered index.</span></span>  
  
2.  <span data-ttu-id="a5661-159">**테이블** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 테이블…** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-159">Right-click the **Tables** folder and click **New Table...**.</span></span>  
  
3.  <span data-ttu-id="a5661-160">늘 하던 방식대로 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-160">Create a new table as you normally would.</span></span> <span data-ttu-id="a5661-161">자세한 내용은 [테이블 만들기&#40;데이터베이스 엔진&#41;](../tables/create-tables-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5661-161">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span>  
  
4.  <span data-ttu-id="a5661-162">위에서 만든 새 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-162">Right-click the new table created above and click **Design**.</span></span>  
  
5.  <span data-ttu-id="a5661-163">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-163">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
6.  <span data-ttu-id="a5661-164">**인덱스/키** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-164">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
7.  <span data-ttu-id="a5661-165">**선택한 기본/고유 키 또는 인덱스** 입력란에서 새 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-165">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
8.  <span data-ttu-id="a5661-166">표에서 **CLUSTERED로 만들기**를 선택하고 속성 오른쪽에 있는 드롭다운 목록에서 **예** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-166">In the grid, select **Create as Clustered**, and choose **Yes** from the drop-down list to the right of the property.</span></span>  
  
9. <span data-ttu-id="a5661-167">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-167">Click **Close**.</span></span>  
  
10. <span data-ttu-id="a5661-168">**파일** 메뉴에서 _table name_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-168">On the **File** menu, click **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a5661-169">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a5661-169">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-clustered-index"></a><span data-ttu-id="a5661-170">클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a5661-170">To create a clustered index</span></span>  
  
1.  <span data-ttu-id="a5661-171">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-171">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5661-172">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-172">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a5661-173">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5661-173">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Create a new table with three columns.  
    CREATE TABLE dbo.TestTable  
        (TestCol1 int NOT NULL,  
         TestCol2 nchar(10) NULL,  
         TestCol3 nvarchar(50) NULL);  
    GO  
    -- Create a clustered index called IX_TestTable_TestCol1  
    -- on the dbo.TestTable table using the TestCol1 column.  
    CREATE CLUSTERED INDEX IX_TestTable_TestCol1   
        ON dbo.TestTable (TestCol1);   
    GO  
    ```  
  
 <span data-ttu-id="a5661-174">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5661-174">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5661-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5661-175">See Also</span></span>  
 <span data-ttu-id="a5661-176">[기본 키 만들기](../tables/create-primary-keys.md) </span><span class="sxs-lookup"><span data-stu-id="a5661-176">[Create Primary Keys](../tables/create-primary-keys.md) </span></span>  
 [<span data-ttu-id="a5661-177">UNIQUE 제약 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="a5661-177">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
