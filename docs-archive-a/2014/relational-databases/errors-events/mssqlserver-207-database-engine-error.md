---
title: MSSQLSERVER_207 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 207 (Database Engine error)
ms.assetid: d1ab00c7-0331-437a-84fe-bae53b82feec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd6044c08ecd5a73f539bfbc1139d6257c2db9d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730715"
---
# <a name="mssqlserver_207"></a><span data-ttu-id="76f4b-102">MSSQLSERVER_207</span><span class="sxs-lookup"><span data-stu-id="76f4b-102">MSSQLSERVER_207</span></span>
    
## <a name="details"></a><span data-ttu-id="76f4b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="76f4b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76f4b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="76f4b-104">Product Name</span></span>|<span data-ttu-id="76f4b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="76f4b-105">SQL Server</span></span>|  
|<span data-ttu-id="76f4b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="76f4b-106">Event ID</span></span>|<span data-ttu-id="76f4b-107">207</span><span class="sxs-lookup"><span data-stu-id="76f4b-107">207</span></span>|  
|<span data-ttu-id="76f4b-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="76f4b-108">Event Source</span></span>|<span data-ttu-id="76f4b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="76f4b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="76f4b-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="76f4b-110">Component</span></span>|<span data-ttu-id="76f4b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="76f4b-111">SQLEngine</span></span>|  
|<span data-ttu-id="76f4b-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="76f4b-112">Symbolic Name</span></span>|<span data-ttu-id="76f4b-113">SQ_BADCOL</span><span class="sxs-lookup"><span data-stu-id="76f4b-113">SQ_BADCOL</span></span>|  
|<span data-ttu-id="76f4b-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="76f4b-114">Message Text</span></span>|<span data-ttu-id="76f4b-115">열 이름 '%.\*ls'이(가) 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-115">Invalid column name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="76f4b-116">설명</span><span class="sxs-lookup"><span data-stu-id="76f4b-116">Explanation</span></span>  
 <span data-ttu-id="76f4b-117">이 쿼리 오류는 다음과 같은 문제로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-117">This query error can be caused by one of the following problems.</span></span>  
  
-   <span data-ttu-id="76f4b-118">열 이름의 철자가 잘못되었거나 지정한 테이블 어디에도 해당 열이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-118">The column name is misspelled or the column does not exist in any of the specified tables.</span></span>  
  
-   <span data-ttu-id="76f4b-119">데이터베이스에서 데이터를 정렬하는 데 대/소문자를 구분하고 있으며 쿼리에 지정한 열 이름의 대/소문자가 테이블에 정의된 열의 대/소문자와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-119">The collation of the database is case-sensitive and the case of the column name specified in the query does not match the case of the column defined in the table.</span></span> <span data-ttu-id="76f4b-120">예를 들어 테이블에서 열을 **LastName**으로 정의하고 데이터베이스에서 대/소문자 구분 데이터 정렬을 사용하는 경우 쿼리에 지정한 열이 **Lastname** 또는 **lastname**이면 열 이름이 일치하지 않으므로 207 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-120">For example, when a column is defined in a table as **LastName** and the database uses a case-sensitive collation, queries that refer to the column as **Lastname** or **lastname** will cause error 207 to return because the column name does not match.</span></span>  
  
-   <span data-ttu-id="76f4b-121">SELECT 절에 정의한 열 별칭을 WHERE 또는 GROUP BY 등의 다른 절에서 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-121">A column alias, defined in the SELECT clause, is referenced in another clause such as a WHERE or GROUP BY clause.</span></span> <span data-ttu-id="76f4b-122">예를 들어 다음 쿼리의 경우 SELECT 절에 열 별칭 `Year`를 정의하고 GROUP BY 절에서 이 별칭을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-122">For example, the following query defines the column alias `Year` in the SELECT clause and refers to it in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year, SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY Year;  
    ```  
  
     <span data-ttu-id="76f4b-123">쿼리 절의 논리적인 처리 순서 때문에 이 예제에서는 207 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-123">Due to the order in which query clauses are logically processed, the example returns error 207.</span></span> <span data-ttu-id="76f4b-124">처리 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-124">The processing order is as follows:</span></span>  
  
    1.  <span data-ttu-id="76f4b-125">FROM</span><span class="sxs-lookup"><span data-stu-id="76f4b-125">FROM</span></span>  
  
    2.  <span data-ttu-id="76f4b-126">켜기</span><span class="sxs-lookup"><span data-stu-id="76f4b-126">ON</span></span>  
  
    3.  <span data-ttu-id="76f4b-127">JOIN</span><span class="sxs-lookup"><span data-stu-id="76f4b-127">JOIN</span></span>  
  
    4.  <span data-ttu-id="76f4b-128">WHERE</span><span class="sxs-lookup"><span data-stu-id="76f4b-128">WHERE</span></span>  
  
    5.  <span data-ttu-id="76f4b-129">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="76f4b-129">GROUP BY</span></span>  
  
    6.  <span data-ttu-id="76f4b-130">WITH CUBE 또는 WITH ROLLUP</span><span class="sxs-lookup"><span data-stu-id="76f4b-130">WITH CUBE or WITH ROLLUP</span></span>  
  
    7.  <span data-ttu-id="76f4b-131">HAVING</span><span class="sxs-lookup"><span data-stu-id="76f4b-131">HAVING</span></span>  
  
    8.  <span data-ttu-id="76f4b-132">SELECT</span><span class="sxs-lookup"><span data-stu-id="76f4b-132">SELECT</span></span>  
  
    9. <span data-ttu-id="76f4b-133">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="76f4b-133">DISTINCT</span></span>  
  
    10. <span data-ttu-id="76f4b-134">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="76f4b-134">ORDER BY</span></span>  
  
    11. <span data-ttu-id="76f4b-135">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="76f4b-135">TOP</span></span>  
  
     <span data-ttu-id="76f4b-136">SELECT 절을 처리할 때까지는 열 별칭이 정의되지 않은 상태이므로 GROUP BY 절을 처리하는 단계에서는 별칭 이름을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-136">Because a column alias is not defined until the SELECT clause is processed, the alias name is unknown when the GROUP BY clause is processed.</span></span>  
  
-   <span data-ttu-id="76f4b-137">*<merge_matched>* 절에서 원본 테이블의 열을 참조하고 있지만 WHEN NOT MATCHED BY SOURCE 절의 원본 테이블에서 아무 행도 반환하지 않는 경우 MERGE 문을 통해 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-137">The MERGE statement raises this error when the *<merge_matched>* clause references columns in the source table but no rows are returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="76f4b-138">쿼리에 아무 행도 반환되지 않으면 원본 테이블의 열에 액세스할 수 없으므로 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-138">The error occurs because the columns in the source table cannot be accessed when no rows are returned to the query.</span></span> <span data-ttu-id="76f4b-139">예를 들어 원본 테이블의 `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1`에 액세스할 수 없는 경우 `Col1` 절을 지정하면 이 문이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-139">For example, the clause `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` may cause the statement to fail if `Col1` in the source table is inaccessible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="76f4b-140">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="76f4b-140">User Action</span></span>  
 <span data-ttu-id="76f4b-141">다음 정보를 확인하고 적절하게 문을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="76f4b-141">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="76f4b-142">열 이름이 테이블에 있는지 확인하고 이름의 철자가 올바른지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="76f4b-142">The column name exists in the table and is spelled correctly.</span></span> <span data-ttu-id="76f4b-143">다음 예제에서는 **sys.columns** 카탈로그 뷰를 쿼리하여 지정된 테이블의 열 이름을 모두 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-143">The following example queries the **sys.columns** catalog view to return all column names for a given table.</span></span>  
  
    ```  
    SELECT name FROM sys.columns WHERE object_id = OBJECT_ID('schema_name.table_name');  
    ```  
  
-   <span data-ttu-id="76f4b-144">데이터베이스 데이터 정렬의 대/소문자 구분.</span><span class="sxs-lookup"><span data-stu-id="76f4b-144">The case sensitivity of the database collation.</span></span> <span data-ttu-id="76f4b-145">다음 문은 지정된 데이터베이스의 데이터 정렬을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-145">The following statement returns the collation of the specified database.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="76f4b-146">데이터 정렬 이름의 약어 CS는 해당 데이터 정렬에서 대/소문자를 구분한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-146">The abbreviation CS in the collation name indicates the collation is case-sensitive.</span></span> <span data-ttu-id="76f4b-147">예를 들어 Latin1_General_CS_AS는 대/소문자와 악센트를 구분하는 데이터 정렬입니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-147">For example, Latin1_General_CS_AS is a case-sensitive and accent-sensitive collation.</span></span> <span data-ttu-id="76f4b-148">열 이름의 대/소문자가 테이블에 정의된 것과 일치하도록 열 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-148">Modify the column name to match the case of the column name as it is defined in the table.</span></span>  
  
-   <span data-ttu-id="76f4b-149">열 별칭을 올바르게 참조했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="76f4b-149">A column alias is referenced incorrectly.</span></span> <span data-ttu-id="76f4b-150">올바른 절에 별칭을 정의하는 식을 반복하거나 파생 테이블을 사용하여 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-150">Modify the statement by repeating the expression that defines the alias in the appropriate clause or by using a derived table.</span></span> <span data-ttu-id="76f4b-151">다음 예에서는 GROUP BY 절에 `Year` 별칭을 정의하는 식을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-151">The following example repeats the expressions that define the `Year` alias in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year ,SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY DATEPART(yyyy,OrderDate);  
    ```  
  
     <span data-ttu-id="76f4b-152">다음 예에서는 파생 테이블을 사용하여 별칭 이름을 쿼리의 다른 절에 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-152">The following example uses a derived table to make the alias name available to other clauses in the query.</span></span> <span data-ttu-id="76f4b-153">별칭 `Year`가 FROM 절에 정의되어 있고 이 절이 제일 먼저 처리되므로 쿼리의 다른 절에서도 이 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-153">Notice that the alias `Year` is defined in the FROM clause, which is processed first, and so makes the alias available for use in other clauses in the query.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT d.Year, SUM(TotalDue) AS Total  
    FROM (SELECT DATEPART(yyyy,OrderDate) AS Year, TotalDue  
          FROM Sales.SalesOrderHeader)AS d  
    GROUP BY Year;  
    ```  
  
-   <span data-ttu-id="76f4b-154">MERGE 문의 WHEN NOT MATCHED BY SOURCE 절이 참조하는 값에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-154">The WHEN NOT MATCHED BY SOURCE clause in the MERGE statement refers to a value that can be accessed.</span></span> <span data-ttu-id="76f4b-155">WHEN NOT MATCHED BY SOURCE 절의 원본 테이블에서 하나 이상의 행을 반환하도록 MERGE 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-155">Modify the MERGE statement so that at least one row is returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="76f4b-156">예를 들어 이 절에 지정된 검색 조건을 추가하거나 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-156">For example, you might need to add or revise the search condition specified for the clause.</span></span> <span data-ttu-id="76f4b-157">또는 절을 수정하여 원본 테이블을 참조하지 않는 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-157">Alternatively, you can modify the clause to specify a value that does not reference the source table.</span></span> <span data-ttu-id="76f4b-158">예들 들어 `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`입니다.</span><span class="sxs-lookup"><span data-stu-id="76f4b-158">For example, `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f4b-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76f4b-159">See Also</span></span>  
 <span data-ttu-id="76f4b-160">[MERGE&#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76f4b-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span></span>  
 <span data-ttu-id="76f4b-161">[FROM&#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76f4b-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="76f4b-162">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76f4b-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="76f4b-163">UPDATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="76f4b-163">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
