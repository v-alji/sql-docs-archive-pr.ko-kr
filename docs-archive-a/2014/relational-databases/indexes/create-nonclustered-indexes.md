---
title: 비클러스터형 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index creation [SQL Server], nonclustered indexes
- nonclustered indexes [SQL Server], creating
- nonclustered indexes [SQL Server], UNIQUE constraint
- indexes [SQL Server], nonclustered
- nonclustered indexes [SQL Server], PRIMARY KEY constraint
ms.assetid: 9402029a-1227-46c4-93aa-c2122eb1b943
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fae0c06b1f562dc3fc518a319df1787b3384c0cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740936"
---
# <a name="create-nonclustered-indexes"></a><span data-ttu-id="cad16-102">비클러스터형 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="cad16-102">Create Nonclustered Indexes</span></span>
  <span data-ttu-id="cad16-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 비클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-103">You can create nonclustered indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cad16-104">비클러스터형 인덱스는 하나 이상의 선택된 열을 다시 정렬하는 테이블에 저장된 데이터와 구별되는 인덱스 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-104">A nonclustered index is an index structure separate from the data stored in a table that reorders one or more selected columns.</span></span> <span data-ttu-id="cad16-105">비클러스터형 인덱스는 기본 테이블을 검색할 때보다 빠르게 데이터를 찾는 데 도움이 될 수 있습니다. 비클러스터형 인덱스의 데이터가 쿼리에 대한 완전한 대답이 되는 경우도 있지만, 비클러스터형 인덱스에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 기본 테이블의 행으로 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-105">Nonclustered indexes can often help you find data more quickly than searching the underlying table; queries can sometimes be answered entirely by the data in the nonclustered index, or the nonclustered index can point the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to the rows in the underlying table.</span></span> <span data-ttu-id="cad16-106">일반적으로 비클러스터형 인덱스는 클러스터형 인덱스를 적용할 수 없고 자주 사용되는 쿼리의 성능을 개선하거나, 클러스터형 인덱스(힙이라고 함) 없이 테이블에서 행을 찾기 위해 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-106">Generally, nonclustered indexes are created to improve the performance of frequently used queries not covered by the clustered index or to locate rows in a table without a clustered index (called a heap).</span></span> <span data-ttu-id="cad16-107">테이블 또는 인덱싱된 뷰에 비클러스터형 인덱스를 여러 개 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-107">You can create multiple nonclustered indexes on a table or indexed view.</span></span>  
  
 <span data-ttu-id="cad16-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cad16-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cad16-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cad16-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cad16-110">일반적인 구현</span><span class="sxs-lookup"><span data-stu-id="cad16-110">Typical Implementations</span></span>](#Implementations)  
  
     [<span data-ttu-id="cad16-111">보안</span><span class="sxs-lookup"><span data-stu-id="cad16-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cad16-112">**비클러스터형 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="cad16-112">**To create a nonclustered index, using:**</span></span>  
  
     [<span data-ttu-id="cad16-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cad16-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cad16-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cad16-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cad16-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cad16-115">Before You Begin</span></span>  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> <span data-ttu-id="cad16-116">일반적인 구현 방법</span><span class="sxs-lookup"><span data-stu-id="cad16-116">Typical Implementations</span></span>  
 <span data-ttu-id="cad16-117">비클러스터형 인덱스는 다음 방법으로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-117">Nonclustered indexes are implemented in the following ways:</span></span>  
  
-   <span data-ttu-id="cad16-118">**UNIQUE 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="cad16-118">**UNIQUE constraints**</span></span>  
  
     <span data-ttu-id="cad16-119">UNIQUE 제약 조건을 만들면 고유 비클러스터형 인덱스가 생성되어 기본적으로 UNIQUE 제약 조건을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-119">When you create a UNIQUE constraint, a unique nonclustered index is created to enforce a UNIQUE constraint by default.</span></span> <span data-ttu-id="cad16-120">테이블에 클러스터형 인덱스가 없는 경우 고유 클러스터형 인덱스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-120">You can specify a unique clustered index if a clustered index on the table does not already exist.</span></span> <span data-ttu-id="cad16-121">자세한 내용은 [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cad16-121">For more information, see [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).</span></span>  
  
-   <span data-ttu-id="cad16-122">**제약 조건의 영향을 받지 않는 인덱스**</span><span class="sxs-lookup"><span data-stu-id="cad16-122">**Index independent of a constraint**</span></span>  
  
     <span data-ttu-id="cad16-123">기본적으로 클러스터링 옵션을 지정하지 않으면 비클러스터형 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-123">By default, a nonclustered index is created if clustered is not specified.</span></span> <span data-ttu-id="cad16-124">각 테이블에서 만들 수 있는 최대 비클러스터형 인덱스 수는 999개입니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-124">The maximum number of nonclustered indexes that can be created per table is 999.</span></span> <span data-ttu-id="cad16-125">여기에는 PRIMARY KEY 또는 UNIQUE 제약 조건을 사용하여 생성된 인덱스가 포함되지만 XML 인덱스는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-125">This includes any indexes created by PRIMARY KEY or UNIQUE constraints, but does not include XML indexes.</span></span>  
  
-   <span data-ttu-id="cad16-126">**인덱싱된 뷰의 비클러스터형 인덱스**</span><span class="sxs-lookup"><span data-stu-id="cad16-126">**Nonclustered index on an indexed view**</span></span>  
  
     <span data-ttu-id="cad16-127">뷰에 클러스터형 고유 인덱스를 만든 후 비클러스터형 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-127">After a unique clustered index has been created on a view, nonclustered indexes can be created.</span></span> <span data-ttu-id="cad16-128">자세한 내용은 [인덱싱된 뷰 만들기](../views/views.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cad16-128">For more information, see [Create Indexed Views](../views/views.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cad16-129">보안</span><span class="sxs-lookup"><span data-stu-id="cad16-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cad16-130">권한</span><span class="sxs-lookup"><span data-stu-id="cad16-130">Permissions</span></span>  
 <span data-ttu-id="cad16-131">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-131">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="cad16-132">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-132">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cad16-133">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cad16-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-the-table-designer"></a><span data-ttu-id="cad16-134">테이블 디자이너를 사용하여 비클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cad16-134">To create a nonclustered index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="cad16-135">개체 탐색기에서 비클러스터형 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-135">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="cad16-136">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-136">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="cad16-137">비클러스터형 인덱스를 만들 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-137">Right-click the table on which you want to create a nonclustered index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="cad16-138">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-138">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="cad16-139">**인덱스/키** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-139">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="cad16-140">**선택한 기본/고유 키 또는 인덱스** 입력란에서 새 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-140">Select the new index in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
7.  <span data-ttu-id="cad16-141">표에서 **CLUSTERED로 만들기**를 선택하고 속성 오른쪽에 있는 드롭다운 목록에서 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-141">In the grid, select **Create as Clustered**, and choose **No** from the drop-down list to the right of the property.</span></span>  
  
8.  <span data-ttu-id="cad16-142">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-142">Click **Close**.</span></span>  
  
9. <span data-ttu-id="cad16-143">**파일** 메뉴에서 _table name_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-143">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-create-a-nonclustered-index-by-using-object-explorer"></a><span data-ttu-id="cad16-144">개체 탐색기를 사용하여 비클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cad16-144">To create a nonclustered index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="cad16-145">개체 탐색기에서 비클러스터형 인덱스를 만들 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-145">In Object Explorer, expand the database that contains the table on which you want to create a nonclustered index.</span></span>  
  
2.  <span data-ttu-id="cad16-146">**테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-146">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="cad16-147">비클러스터형 인덱스를 만들 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-147">Expand the table on which you want to create a nonclustered index.</span></span>  
  
4.  <span data-ttu-id="cad16-148">**인덱스** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 인덱스**를 가리킨 다음, **비클러스터형 인덱스...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-148">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="cad16-149">**새 인덱스** 대화 상자의 **일반** 페이지에서 **인덱스 이름** 상자에 새 인덱스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-149">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="cad16-150">**인덱스 키 열** 아래에서 **추가...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-150">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="cad16-151">**table_name**_에서 열 선택_ 대화 상자에서 비클러스터형 인덱스에 추가할 테이블 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-151">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the nonclustered index.</span></span>  
  
8.  <span data-ttu-id="cad16-152">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="cad16-153">**새 인덱스** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-153">In the **New Index** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cad16-154">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cad16-154">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-nonclustered-index-on-a-table"></a><span data-ttu-id="cad16-155">테이블에 비클러스터형 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cad16-155">To create a nonclustered index on a table</span></span>  
  
1.  <span data-ttu-id="cad16-156">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-156">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cad16-157">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-157">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cad16-158">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cad16-158">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named IX_ProductVendor_VendorID and delete it if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
                WHERE name = N'IX_ProductVendor_VendorID')   
        DROP INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor;   
    GO  
    -- Create a nonclustered index called IX_ProductVendor_VendorID   
    -- on the Purchasing.ProductVendor table using the BusinessEntityID column.   
    CREATE NONCLUSTERED INDEX IX_ProductVendor_VendorID   
        ON Purchasing.ProductVendor (BusinessEntityID);   
    GO  
    ```  
  
 <span data-ttu-id="cad16-159">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cad16-159">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
