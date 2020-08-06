---
title: 외래 키 관계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0de3311eb6abffcdb71ab725d0650fe96b04c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661604"
---
# <a name="create-foreign-key-relationships"></a><span data-ttu-id="fb54a-102">외래 키 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="fb54a-102">Create Foreign Key Relationships</span></span>
  <span data-ttu-id="fb54a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 외래 키 관계를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-103">This topic describes how to create foreign key relationships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fb54a-104">한 테이블의 행을 다른 테이블의 행과 연결하려면 두 테이블 사이에 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-104">You create a relationship between two tables when you want to associate rows of one table with rows of another.</span></span>  
  
 <span data-ttu-id="fb54a-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fb54a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fb54a-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fb54a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fb54a-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fb54a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fb54a-108">보안</span><span class="sxs-lookup"><span data-stu-id="fb54a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fb54a-109">**외래 키 관계를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="fb54a-109">**To Create Foreign Key Relationships by using:**</span></span>  
  
     [<span data-ttu-id="fb54a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fb54a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fb54a-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fb54a-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb54a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fb54a-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fb54a-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fb54a-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fb54a-114">외래 키 제약 조건은 다른 테이블의 기본 키 제약 조건으로 연결될 수도 있고 다른 테이블에 있는 UNIQUE 제약 조건의 열을 참조하도록 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-114">A foreign key constraint does not have to be linked only to a primary key constraint in another table; it can also be defined to reference the columns of a UNIQUE constraint in another table.</span></span>  
  
-   <span data-ttu-id="fb54a-115">FOREIGN KEY 제약 조건의 열에 NULL 외의 다른 값을 입력한 경우에는 그 값이 참조되는 열에 있어야 합니다. 그렇지 않은 경우에는 외래 키 위반 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-115">When a value other than NULL is entered into the column of a FOREIGN KEY constraint, the value must exist in the referenced column; otherwise, a foreign key violation error message is returned.</span></span> <span data-ttu-id="fb54a-116">복합 외래 키 제약 조건의 모든 값에 대해 유효성을 검사하려면 관련된 모든 열에 NOT NULL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-116">To make sure that all values of a composite foreign key constraint are verified, specify NOT NULL on all the participating columns.</span></span>  
  
-   <span data-ttu-id="fb54a-117">FOREIGN KEY 제약 조건은 같은 서버의 같은 데이터베이스 내에 있는 테이블만 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-117">FOREIGN KEY constraints can reference only tables within the same database on the same server.</span></span> <span data-ttu-id="fb54a-118">상호 데이터베이스 참조 무결성은 트리거를 통해 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-118">Cross-database referential integrity must be implemented through triggers.</span></span> <span data-ttu-id="fb54a-119">자세한 내용은 [CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb54a-119">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
-   <span data-ttu-id="fb54a-120">FOREIGN KEY 제약 조건은 같은 테이블에 있는 다른 열을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-120">FOREIGN KEY constraints can reference another column in the same table.</span></span> <span data-ttu-id="fb54a-121">이것을 자체 참조라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-121">This is referred to as a self-reference.</span></span>  
  
-   <span data-ttu-id="fb54a-122">열 수준에서 지정된 외래 키 제약 조건은 참조 열을 하나만 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-122">A FOREIGN KEY constraint specified at the column level can list only one reference column.</span></span> <span data-ttu-id="fb54a-123">이 열의 데이터 형식은 제약 조건이 정의된 열의 데이터 형식과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-123">This column must have the same data type as the column on which the constraint is defined.</span></span>  
  
-   <span data-ttu-id="fb54a-124">테이블 수준에서 지정된 외래 키 제약 조건에는 제약 조건 열 목록의 열 개수와 같은 수의 참조 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-124">A FOREIGN KEY constraint specified at the table level must have the same number of reference columns as the number of columns in the constraint column list.</span></span> <span data-ttu-id="fb54a-125">각 참조 열의 데이터 형식도 열 목록의 해당 열과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-125">The data type of each reference column must also be the same as the corresponding column in the column list.</span></span>  
  
-   <span data-ttu-id="fb54a-126">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 테이블에 포함하여 다른 테이블을 참조하는 FOREIGN KEY 제약 조건의 수나 특정 테이블을 참조하는 다른 테이블 소유의 FOREIGN KEY 제약 조건의 수에 미리 한계를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-126">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not have a predefined limit on either the number of FOREIGN KEY constraints a table can contain that reference other tables, or the number of FOREIGN KEY constraints that are owned by other tables that reference a specific table.</span></span> <span data-ttu-id="fb54a-127">하지만 실제로 사용할 수 있는 FOREIGN KEY 제약 조건의 수는 하드웨어 구성 및 데이터베이스와 애플리케이션의 디자인에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-127">Nevertheless, the actual number of FOREIGN KEY constraints that can be used is limited by the hardware configuration and by the design of the database and application.</span></span> <span data-ttu-id="fb54a-128">테이블에 포함되거나 이 테이블을 참조하는 FOREIGN KEY 제약 조건의 수가 각각 253개를 넘지 않도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-128">We recommend that a table contain no more than 253 FOREIGN KEY constraints, and that it be referenced by no more than 253 FOREIGN KEY constraints.</span></span>  
  
-   <span data-ttu-id="fb54a-129">임시 테이블에는 FOREIGN KEY 제약 조건이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-129">FOREIGN KEY constraints are not enforced on temporary tables.</span></span>  
  
-   <span data-ttu-id="fb54a-130">CLR 사용자 정의 형식 열에 외래 키를 정의하는 경우 형식 구현이 이진 순서를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-130">If a foreign key is defined on a CLR user-defined type column, the implementation of the type must support binary ordering.</span></span> <span data-ttu-id="fb54a-131">자세한 내용은 [CLR 사용자 정의 형식](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb54a-131">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
-   <span data-ttu-id="fb54a-132">`varchar(max)` 유형의 열은 자신이 참조하는 기본 키도 `varchar(max)` 유형으로 정의된 경우에만 FOREIGN KEY 제약 조건에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-132">A column of type `varchar(max)` can participate in a FOREIGN KEY constraint only if the primary key it references is also defined as type `varchar(max)`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb54a-133">보안</span><span class="sxs-lookup"><span data-stu-id="fb54a-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb54a-134">권한</span><span class="sxs-lookup"><span data-stu-id="fb54a-134">Permissions</span></span>  
 <span data-ttu-id="fb54a-135">외래 키가 포함된 새 테이블을 만들려면 데이터베이스에서 CREATE TABLE 권한이 필요하고 테이블을 만들려는 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-135">Creating a new table with a foreign key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="fb54a-136">기존 테이블에서 외래 키를 만들려면 해당 테이블에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-136">Creating a foreign key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb54a-137">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fb54a-137">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a><span data-ttu-id="fb54a-138">테이블 디자이너에서 외래 키 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="fb54a-138">To create a foreign key relationship in Table Designer</span></span>  
  
1.  <span data-ttu-id="fb54a-139">개체 탐색기에서 관계의 외래 키 쪽에 표시할 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-139">In Object Explorer, right-click the table that will be on the foreign-key side of the relationship and click **Design**.</span></span>  
  
     <span data-ttu-id="fb54a-140">**테이블 디자이너**에서 테이블이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-140">The table opens in **Table Designer**.</span></span>  
  
2.  <span data-ttu-id="fb54a-141">**테이블 디자이너** 메뉴에서 **관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-141">From the **Table Designer** menu, click **Relationships**.</span></span>  
  
3.  <span data-ttu-id="fb54a-142">**외래 키 관계** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-142">In the **Foreign-key Relationships** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="fb54a-143">**선택한 관계** 목록에 FK_\<*tablename*>_\<*tablename*> 형식으로 자동 지정된 이름과 함께 관계가 표시됩니다. 여기에서 *tablename*은 외래 키 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-143">The relationship appears in the **Selected Relationship** list with a system-provided name in the format FK_\<*tablename*>_\<*tablename*>, where *tablename* is the name of the foreign key table.</span></span>  
  
4.  <span data-ttu-id="fb54a-144">**선택한 관계** 목록에서 관계를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-144">Click the relationship in the **Selected Relationship** list.</span></span>  
  
5.  <span data-ttu-id="fb54a-145">오른쪽에 있는 표에서 **테이블 및 열 사양**을 클릭한 다음, 속성의 오른쪽에 있는 줄임표( **…** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-145">Click **Tables and Columns Specification** in the grid to the right and click the ellipses (**...**) to the right of the property.</span></span>  
  
6.  <span data-ttu-id="fb54a-146">**테이블 및 열** 대화 상자의 **기본 키** 드롭다운 목록에서 관계의 기본 키 쪽에 사용할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-146">In the **Tables and Columns** dialog box, in the **Primary Key** drop-down list, choose the table that will be on the primary-key side of the relationship.</span></span>  
  
7.  <span data-ttu-id="fb54a-147">아래 표에서 테이블의 기본 키로 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-147">In the grid beneath, choose the columns contributing to the table's primary key.</span></span> <span data-ttu-id="fb54a-148">각 열 바로 왼쪽에 있는 표의 셀에서 외래 키 테이블의 상응하는 외래 키 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-148">In the adjacent grid cell to the left of each column, choose the corresponding foreign-key column of the foreign-key table.</span></span>  
  
     <span data-ttu-id="fb54a-149">**테이블 디자이너** 에서 관계의 이름이 자동으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-149">**Table Designer** suggests a name for the relationship.</span></span> <span data-ttu-id="fb54a-150">이 이름을 변경하려면 **관계 이름** 입력란의 내용을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-150">To change this name, edit the contents of the **Relationship Name** text box.</span></span>  
  
8.  <span data-ttu-id="fb54a-151">**확인** 을 선택하여 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-151">Choose **OK** to create the relationship.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fb54a-152">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fb54a-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a><span data-ttu-id="fb54a-153">새 테이블에 외래 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="fb54a-153">To create a foreign key in a new table</span></span>  
  
1.  <span data-ttu-id="fb54a-154">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fb54a-155">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fb54a-156">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-156">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fb54a-157">이 예에서는 테이블을 만들고 `TempID` 테이블의 `SalesReasonID` 열을 참조하는 `Sales.SalesReason` 열의 외래 키 제약 조건을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-157">The example creates a table and defines a foreign key constraint on the column `TempID` that references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span> <span data-ttu-id="fb54a-158">ON DELETE CASCADE 및 ON UPDATE CASCADE 절을 사용하면 `Sales.SalesReason` 테이블에 대한 변경 내용이 `Sales.TempSalesReason` 테이블에 자동으로 전파되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-158">The ON DELETE CASCADE and ON UPDATE CASCADE clauses are used to ensure that changes made to `Sales.SalesReason` table are automatically propagated to the `Sales.TempSalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a><span data-ttu-id="fb54a-159">기존 테이블에 외래 키를 만들려면</span><span class="sxs-lookup"><span data-stu-id="fb54a-159">To create a foreign key in an existing table</span></span>  
  
1.  <span data-ttu-id="fb54a-160">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fb54a-161">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fb54a-162">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-162">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fb54a-163">이 예에서는 `TempID` 열에 외래 키를 만들고 `SalesReasonID` 테이블의 `Sales.SalesReason` 열을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="fb54a-163">The example creates a foreign key on the column `TempID` and references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     <span data-ttu-id="fb54a-164">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 및 [table_constraint&#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb54a-164">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
  
