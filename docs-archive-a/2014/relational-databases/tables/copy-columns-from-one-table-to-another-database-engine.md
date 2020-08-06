---
title: 한 테이블에서 다른 테이블로 열 복사(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying columns
- columns [SQL Server], copying
ms.assetid: 5f5e70dc-69f9-44b8-bc48-b5d51ac20d77
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37b98bf0910cbbb4c2a1d7fe01f11d52703ec88c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661612"
---
# <a name="copy-columns-from-one-table-to-another-database-engine"></a><span data-ttu-id="0282e-102">한 테이블에서 다른 테이블로 열 복사(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="0282e-102">Copy Columns from One Table to Another (Database Engine)</span></span>
  <span data-ttu-id="0282e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 열 정의만 복사하거나 열 정의와 데이터를 모두 복사하여 테이블 간에 열을 복사하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-103">This topic describes how to copy columns from one table to another, copying either just the column definition, or the definition and data in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0282e-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0282e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0282e-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0282e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0282e-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0282e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0282e-107">보안</span><span class="sxs-lookup"><span data-stu-id="0282e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0282e-108">**다음을 사용하여 열을 복사하려면:**</span><span class="sxs-lookup"><span data-stu-id="0282e-108">**To coy columns, using:**</span></span>  
  
     [<span data-ttu-id="0282e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0282e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0282e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0282e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0282e-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0282e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0282e-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="0282e-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0282e-113">별칭 데이터 형식의 열을 데이터베이스 간에 복사하면 대상 데이터베이스에서 별칭 데이터 형식을 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-113">When you copy a column that has an alias data type from one database to another, the alias data type may not be available in the destination database.</span></span> <span data-ttu-id="0282e-114">이 경우 해당 열에는 대상 데이터베이스에서 사용할 수 있는 가장 비슷한 기본 데이터 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-114">In such a case, the column will be assigned the nearest matching base data type available in that database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0282e-115">보안</span><span class="sxs-lookup"><span data-stu-id="0282e-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0282e-116">권한</span><span class="sxs-lookup"><span data-stu-id="0282e-116">Permissions</span></span>  
 <span data-ttu-id="0282e-117">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0282e-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0282e-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="0282e-119">한 테이블에서 다른 테이블로 열 정의를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0282e-119">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="0282e-120">테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭하여 복사할 열이 있는 테이블과 이 열을 붙여 넣을 대상 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-120">Open the table with columns you want to copy and the one you want to copy into by right-clicking the tables, and then clicking **Design**.</span></span>  
  
2.  <span data-ttu-id="0282e-121">복사하려는 열이 포함된 테이블에 해당하는 탭을 클릭하고 복사할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-121">Click the tab for the table with the columns you want to copy and select those columns.</span></span>  
  
3.  <span data-ttu-id="0282e-122">**편집** 메뉴에서 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-122">From the **Edit** menu, click **Copy**.</span></span>  
  
4.  <span data-ttu-id="0282e-123">열을 복사하여 넣으려는 대상 테이블에 해당하는 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-123">Click the tab for the table into which you want to copy the columns.</span></span>  
  
5.  <span data-ttu-id="0282e-124">열을 삽입하려는 위치 바로 앞의 열을 선택하고 **편집** 메뉴에서 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-124">Select the column you want to follow the inserted columns and, from the **Edit** menu, click **Paste**.</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="0282e-125">테이블 간에 데이터를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0282e-125">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="0282e-126">위에서 설명한 열 정의 복사 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-126">Follow the directions for copying column definitions above.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0282e-127">한 테이블에 다른 테이블로 데이터를 복사하려면 먼저 대상 열의 데이터 형식이 원본 열의 데이터 형식과 호환되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-127">Before you begin to copy data from one table to another, make sure that the data types in the destination columns are compatible with the data types of the source columns</span></span>  
  
2.  <span data-ttu-id="0282e-128">개체 탐색기에서 **뷰** 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 뷰**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-128">In Object Explorer, right-click the **Views** node, and then click **New View**.</span></span>  
  
3.  <span data-ttu-id="0282e-129">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **결과 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-129">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
4.  <span data-ttu-id="0282e-130">**결과 삽입의 대상 테이블 선택** 대화 상자에서 데이터를 복사해 넣을 대상 테이블을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-130">In the **Choose Target Table for Insert Results** dialog box, select the table into which you want to copy the data, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0282e-131">테이블 내에서 행을 복사하는 경우 원본 테이블을 대상 테이블로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-131">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0282e-132">**쿼리 디자이너** 에서는 업데이트 가능한 테이블과 뷰를 미리 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-132">**Query Designer** cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="0282e-133">따라서, **결과 삽입의 대상 테이블 선택** 대화 상자의 테이블 목록에는 쿼리하려는 데이터 연결에 사용 가능한 모든 테이블과 뷰가 표시됩니다. 여기에는 행을 복사해 넣을 수 없는 테이블이나 뷰도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-133">Therefore, the list of tables in the **Choose Target Table for Insert Results** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
5.  <span data-ttu-id="0282e-134">다이어그램 창의 본문을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **다이어그램에 테이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-134">Right-click in the body of the diagram pane and, from the shortcut menu, click **Add Table to Diagram**.</span></span>  
  
6.  <span data-ttu-id="0282e-135">**테이블 추가** 대화 상자에서 데이터를 복사하려는 각 원본 테이블을 선택하고 **추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-135">In the **Add Table** dialog box, select each table from which you want to copy data, click **Add**, and then click **Close**.</span></span>  
  
     <span data-ttu-id="0282e-136">다이어그램 창에 테이블이 간략한 형태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-136">The tables, in an abbreviated form, appear in the diagram pane.</span></span>  
  
7.  <span data-ttu-id="0282e-137">간략한 테이블에서 데이터를 복사하려는 원본 열의 확인란을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-137">In the abbreviated tables, check the boxes for any columns from which you want to copy data.</span></span>  
  
8.  <span data-ttu-id="0282e-138">조건 창의 **추가** 열에서 각 대상 열에 대해 데이터를 복사할 원본 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-138">In the criteria pane, in the **Append** column, for each target column choose a column from which you want to copy data.</span></span>  
  
9. <span data-ttu-id="0282e-139">조건 창에 검색 조건을 입력하여 복사할 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-139">Specify the rows to copy by entering search conditions in the criteria pane.</span></span> <span data-ttu-id="0282e-140">자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0282e-140">For details, see [Specify Search Conditions &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="0282e-141">검색 조건을 지정하지 않으면 원본 테이블의 행 전체가 대상 테이블에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-141">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
10. <span data-ttu-id="0282e-142">요약 정보를 복사하려면 **그룹화 방법** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-142">If you want to copy summary information, specify **Group By** options.</span></span> <span data-ttu-id="0282e-143">자세한 내용은 [테이블에 있는 모든 행의 값 요약 또는 집계&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0282e-143">For details, see [Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md).</span></span>  
  
11. <span data-ttu-id="0282e-144">쿼리를 실행하려면 **SQL 실행** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-144">Click the **Execute SQL button** to run the query.</span></span>  
  
     <span data-ttu-id="0282e-145">결과 삽입 쿼리를 실행해도 [결과 창](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-145">When you execute an insert results query, no results are reported in the [Results Pane](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="0282e-146">대신, 복사한 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-146">Instead, a message appears indicating how many rows were copied.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0282e-147">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0282e-147">Using Transact-SQL</span></span>  
  
#### <a name="to-copy-column-definitions-from-one-table-to-another"></a><span data-ttu-id="0282e-148">한 테이블에서 다른 테이블로 열 정의를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0282e-148">To copy column definitions from one table to another</span></span>  
  
1.  <span data-ttu-id="0282e-149">Transact-SQL 문을 사용하여 한 테이블에서 다른 기존 테이블로 개별 열을 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-149">You cannot copy individual columns from one table to another existing table by using Transact-SQL statements.</span></span> <span data-ttu-id="0282e-150">하지만 SELECT INTO를 사용하여 기본 파일 그룹에 새 테이블을 만들고 쿼리의 결과 행을 이 테이블에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-150">However, you can create a new table in the default filegroup and inserts the resulting rows from the query into it by using SELECT INTO.</span></span> <span data-ttu-id="0282e-151">자세한 내용은 [INTO 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0282e-151">For more information, see [INTO Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-into-clause-transact-sql).</span></span>  
  
#### <a name="to-copy-data-from-one-table-to-another"></a><span data-ttu-id="0282e-152">테이블 간에 데이터를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="0282e-152">To copy data from one table to another</span></span>  
  
1.  <span data-ttu-id="0282e-153">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-153">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0282e-154">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-154">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0282e-155">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0282e-155">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.EmployeeSales  
    ( BusinessEntityID   varchar(11) NOT NULL,  
      SalesYTD money NOT NULL  
    );  
    GO  
    INSERT INTO dbo.EmployeeSales  
        SELECT BusinessEntityID, SalesYTD   
        FROM Sales.SalesPerson;  
    GO  
    ```  
  
  
