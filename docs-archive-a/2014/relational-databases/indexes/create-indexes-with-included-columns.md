---
title: 포괄 열을 사용하여 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index size [SQL Server]
- index keys [SQL Server]
- index columns [SQL Server]
- size [SQL Server], indexes
- key columns [SQL Server]
- included columns
- nonclustered indexes [SQL Server], included columns
- designing indexes [SQL Server], included columns
- nonkey columns
ms.assetid: d198648d-fea5-416d-9f30-f9d4aebbf4ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5a464f9791ea635236069555647229bf1f0d79e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740951"
---
# <a name="create-indexes-with-included-columns"></a><span data-ttu-id="33eeb-102">포괄 열을 사용하여 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="33eeb-102">Create Indexes with Included Columns</span></span>
  <span data-ttu-id="33eeb-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 비클러스터형 인덱스의 기능을 확장하도록 포괄 열 또는 키가 아닌 열을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-103">This topic describes how to add included (or nonkey) columns to extend the functionality of nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="33eeb-104">키가 아닌 열을 포함하여 여러 쿼리를 처리하는 비클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-104">By including nonkey columns, you can create nonclustered indexes that cover more queries.</span></span> <span data-ttu-id="33eeb-105">이는 키가 아닌 열에 다음과 같은 장점이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-105">This is because the nonkey columns have the following benefits:</span></span>  
  
-   <span data-ttu-id="33eeb-106">키가 아닌 열은 인덱스 키 열로 사용할 수 없는 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-106">They can be data types not allowed as index key columns.</span></span>  
  
-   <span data-ttu-id="33eeb-107">인덱스 키 열의 수 또는 인덱스 키 크기를 계산할 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 키가 아닌 열을 고려하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-107">They are not considered by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="33eeb-108">쿼리의 모든 열이 키 열 또는 키가 아닌 열로 인덱스에 포함되면 키가 아닌 열이 있는 인덱스는 쿼리 성능을 상당히 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-108">An index with nonkey columns can significantly improve query performance when all columns in the query are included in the index either as key or nonkey columns.</span></span> <span data-ttu-id="33eeb-109">성능이 향상되는 이유는 쿼리 최적화 프로그램이 테이블 또는 클러스터형 인덱스 데이터에 액세스하지 않고 인덱스 내에서 모든 열 값을 찾을 수 있으므로 디스크 I/O 작업을 줄어들기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-109">Performance gains are achieved because the query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33eeb-110">인덱스에 쿼리가 참조하는 모든 열이 들어 있으면 일반적으로 이 인덱스는 *쿼리를 포함*한다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-110">When an index contains all the columns referenced by a query it is typically referred to as *covering the query*.</span></span>  
  
 <span data-ttu-id="33eeb-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="33eeb-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="33eeb-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="33eeb-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="33eeb-113">디자인 권장 사항</span><span class="sxs-lookup"><span data-stu-id="33eeb-113">Design Recommendations</span></span>](#DesignRecs)  
  
     [<span data-ttu-id="33eeb-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="33eeb-114">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="33eeb-115">보안</span><span class="sxs-lookup"><span data-stu-id="33eeb-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="33eeb-116">**키가 아닌 열이 있는 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="33eeb-116">**To create an index with nonkey columns, using:**</span></span>  
  
     [<span data-ttu-id="33eeb-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33eeb-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="33eeb-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33eeb-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="33eeb-119">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="33eeb-119">Before You Begin</span></span>  
  
###  <a name="design-recommendations"></a><a name="DesignRecs"></a> <span data-ttu-id="33eeb-120">디자인 권장 구성</span><span class="sxs-lookup"><span data-stu-id="33eeb-120">Design Recommendations</span></span>  
  
-   <span data-ttu-id="33eeb-121">검색 및 조회에 사용된 열만 키 열이 되도록 인덱스 키 크기가 큰 비클러스터형 인덱스를 다시 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-121">Redesign nonclustered indexes with a large index key size so that only columns used for searching and lookups are key columns.</span></span> <span data-ttu-id="33eeb-122">쿼리를 포함한 다른 모든 열을 키가 아닌 열로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-122">Make all other columns that cover the query into nonkey columns.</span></span> <span data-ttu-id="33eeb-123">이 방법을 통해 쿼리를 포함하는 데 필요한 모든 열을 가지게 되지만 인덱스 키 자체는 작으며 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-123">In this way, you will have all columns needed to cover the query, but the index key itself is small and efficient.</span></span>  
  
-   <span data-ttu-id="33eeb-124">비클러스터형 인덱스에 키가 아닌 열을 포함하여 현재 인덱스 크기 제한인 최대 16개의 키 열 및 최대 900바이트의 인덱스 키 크기를 초과하지 않게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-124">Include nonkey columns in a nonclustered index to avoid exceeding the current index size limitations of a maximum of 16 key columns and a maximum index key size of 900 bytes.</span></span> <span data-ttu-id="33eeb-125">인덱스 키 열의 수 또는 인덱스 키 크기를 계산할 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 키가 아닌 열은 계산하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not consider nonkey columns when calculating the number of index key columns or index key size.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="33eeb-126">제한 사항</span><span class="sxs-lookup"><span data-stu-id="33eeb-126">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="33eeb-127">키가 아닌 열은 비클러스터형 인덱스에 대해서만 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-127">Nonkey columns can only be defined on nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="33eeb-128">`text`, `ntext` 및 `image`를 제외한 모든 데이터 형식을 키가 아닌 열로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-128">All data types except `text`, `ntext`, and `image` can be used as nonkey columns.</span></span>  
  
-   <span data-ttu-id="33eeb-129">결정적이면서 정확하거나 정확하지 않은 계산 열은 키가 아닌 열이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-129">Computed columns that are deterministic and either precise or imprecise can be nonkey columns.</span></span> <span data-ttu-id="33eeb-130">자세한 내용은 [Indexes on Computed Columns](indexes-on-computed-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33eeb-130">For more information, see [Indexes on Computed Columns](indexes-on-computed-columns.md).</span></span>  
  
-   <span data-ttu-id="33eeb-131">`image`, `ntext` 및 `text` 데이터 형식에서 파생된 계산 열은 계산 열 데이터 형식이 키가 아닌 인덱스 열로 허용되는 한 키가 아닌 열이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-131">Computed columns derived from `image`, `ntext`, and `text` data types can be nonkey columns as long as the computed column data type is allowed as a nonkey index column.</span></span>  
  
-   <span data-ttu-id="33eeb-132">해당 테이블의 인덱스를 먼저 삭제하지 않는 경우 키가 아닌 열을 테이블에서 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-132">Nonkey columns cannot be dropped from a table unless that table's index is dropped first.</span></span>  
  
-   <span data-ttu-id="33eeb-133">다음 경우를 제외하고 키가 아닌 열은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-133">Nonkey columns cannot be changed, except to do the following:</span></span>  
  
    -   <span data-ttu-id="33eeb-134">열의 Null 허용 여부를 NOT NULL에서 NULL로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-134">Change the nullability of the column from NOT NULL to NULL.</span></span>  
  
    -   <span data-ttu-id="33eeb-135">`varchar`, `nvarchar` 또는 `varbinary` 열의 길이를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-135">Increase the length of `varchar`, `nvarchar`, or `varbinary` columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="33eeb-136">보안</span><span class="sxs-lookup"><span data-stu-id="33eeb-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="33eeb-137">권한</span><span class="sxs-lookup"><span data-stu-id="33eeb-137">Permissions</span></span>  
 <span data-ttu-id="33eeb-138">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-138">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="33eeb-139">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-139">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33eeb-140">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="33eeb-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="33eeb-141">키가 아닌 열이 있는 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="33eeb-141">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="33eeb-142">개체 탐색기에서 더하기 기호를 클릭하여 키가 아닌 열이 있는 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-142">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create an index with nonkey columns.</span></span>  
  
2.  <span data-ttu-id="33eeb-143">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-143">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="33eeb-144">더하기 기호를 클릭하여 키가 아닌 열이 있는 인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-144">Click the plus sign to expand the table on which you want to create an index with nonkey columns.</span></span>  
  
4.  <span data-ttu-id="33eeb-145">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 가리킨 다음, **비클러스터형 인덱스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-145">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="33eeb-146">**새 인덱스** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 새 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-146">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="33eeb-147">**인덱스 키 열** 탭 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-147">Under the **Index key columns** tab, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="33eeb-148">_Table_name_ **에서 열 선택**대화 상자에서 인덱스에 추가할 테이블 열에 대 한 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-148">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index.</span></span>  
  
8.  <span data-ttu-id="33eeb-149">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-149">Click **OK**.</span></span>  
  
9. <span data-ttu-id="33eeb-150">**포괄 열** 탭 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-150">Under the **Included columns** tab, click **Add...**.</span></span>  
  
10. <span data-ttu-id="33eeb-151">_Table_name_ **에서 열 선택**대화 상자에서 키가 아닌 열로 인덱스에 추가할 테이블 열의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the index as nonkey columns.</span></span>  
  
11. <span data-ttu-id="33eeb-152">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-152">Click **OK**.</span></span>  
  
12. <span data-ttu-id="33eeb-153">**새 인덱스** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33eeb-154">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="33eeb-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-index-with-nonkey-columns"></a><span data-ttu-id="33eeb-155">키가 아닌 열이 있는 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="33eeb-155">To create an index with nonkey columns</span></span>  
  
1.  <span data-ttu-id="33eeb-156">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="33eeb-157">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="33eeb-158">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33eeb-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates a nonclustered index on the Person.Address table with four included (nonkey) columns.   
    -- index key column is PostalCode and the nonkey columns are  
    -- AddressLine1, AddressLine2, City, and StateProvinceID.  
    CREATE NONCLUSTERED INDEX IX_Address_PostalCode  
    ON Person.Address (PostalCode)  
    INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
    GO  
    ```  
  
 <span data-ttu-id="33eeb-159">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33eeb-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
