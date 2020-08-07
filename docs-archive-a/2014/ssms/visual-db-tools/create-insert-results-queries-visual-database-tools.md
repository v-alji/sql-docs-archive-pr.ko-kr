---
title: 결과 삽입 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- result sets [SQL Server], queries
- results [SQL Server], query
- Insert Results query
- queries [SQL Server], results
ms.assetid: 8770d630-09cc-47ec-a0e9-e9de2d7bbc89
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02643c2cf3295debe740a696941f8730d4417254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731287"
---
# <a name="create-insert-results-queries-visual-database-tools"></a><span data-ttu-id="52ba3-102">결과 삽입 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="52ba3-102">Create Insert Results Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="52ba3-103">결과 삽입 쿼리를 사용하여 테이블 내에서 또는 한 테이블에서 다른 테이블로 행을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-103">You can copy rows from one table to another or within a table using an Insert Results query.</span></span> <span data-ttu-id="52ba3-104">예를 들어 `titles` 테이블에서 결과 삽입 쿼리를 사용하여 한 출판사의 모든 도서 제목에 대한 정보를 두 번째 테이블로 복사하고 이 테이블을 해당 출판사에서 사용하도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-104">For example, in a `titles` table, you can use an Insert Results query to copy information about all the titles for one publisher to a second table that you can make available to that publisher.</span></span> <span data-ttu-id="52ba3-105">결과 삽입 쿼리는 테이블 만들기 쿼리와 비슷하지만 행을 기존 테이블에 복사한다는 점에서 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-105">An Insert Results query is similar to Make Table Queries, but copies rows into an existing table.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="52ba3-106">잘라내기와 붙여넣기를 사용하여 한 테이블에서 다른 테이블로 행을 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-106">You can also copy rows from one table to another using cut and paste.</span></span> <span data-ttu-id="52ba3-107">각 테이블에 대한 쿼리를 만들고 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-107">Create a query for each table and run the queries.</span></span> <span data-ttu-id="52ba3-108">한 결과 표에서 다른 결과 표로 행을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-108">Copy the rows you want from one results grid to the other.</span></span>  
  
 <span data-ttu-id="52ba3-109">결과 삽입 쿼리를 만들려면 다음 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-109">When you create an Insert Results query, you specify:</span></span>  
  
-   <span data-ttu-id="52ba3-110">행을 복사해 넣을 데이터베이스 테이블(대상 테이블)</span><span class="sxs-lookup"><span data-stu-id="52ba3-110">The database table to copy rows to (the destination table).</span></span>  
  
-   <span data-ttu-id="52ba3-111">행을 복사할 하나 이상의 원본 테이블.</span><span class="sxs-lookup"><span data-stu-id="52ba3-111">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="52ba3-112">원본 테이블은 하위 쿼리의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-112">The source table or tables become part of a subquery.</span></span> <span data-ttu-id="52ba3-113">테이블 내에서 복사하는 경우 원본 테이블은 대상 테이블과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-113">If you are copying within a table, the source table is the same as the destination table.</span></span>  
  
-   <span data-ttu-id="52ba3-114">해당 내용을 복사하려는 원본 테이블의 열</span><span class="sxs-lookup"><span data-stu-id="52ba3-114">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="52ba3-115">데이터를 복사해 넣을 대상 테이블의 대상 열</span><span class="sxs-lookup"><span data-stu-id="52ba3-115">The target columns in the destination table to copy the data to.</span></span>  
  
-   <span data-ttu-id="52ba3-116">복사할 행을 정의하는 검색 조건</span><span class="sxs-lookup"><span data-stu-id="52ba3-116">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="52ba3-117">행을 특정 순서에 따라 복사하려는 경우 정렬 순서</span><span class="sxs-lookup"><span data-stu-id="52ba3-117">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="52ba3-118">요약 정보만 복사하려는 경우 그룹화 방법 옵션</span><span class="sxs-lookup"><span data-stu-id="52ba3-118">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="52ba3-119">예를 들어, 다음 쿼리는 `titles` 테이블의 제목 정보를 `archivetitles`라는 보관 테이블로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-119">For example, the following query copies title information from the `titles` table to an archive table called `archivetitles`.</span></span> <span data-ttu-id="52ba3-120">이 쿼리는 특정 출판사에서 발행한 모든 도서 제목의 네 가지 열에 들어 있는 내용을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-120">The query copies the contents of four columns for all titles belonging to a particular publisher:</span></span>  
  
```  
INSERT INTO archivetitles   
   (title_id, title, type, pub_id)  
SELECT title_id, title, type, pub_id  
FROM titles  
WHERE (pub_id = '0766')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="52ba3-121">새 행에 값을 삽입하려면 값 삽입 쿼리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-121">To insert values into a new row, use an Insert Values query.</span></span>  
  
 <span data-ttu-id="52ba3-122">행의 열 전체 또는 선택한 열의 내용을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-122">You can copy the contents of selected columns or of all columns in a row.</span></span> <span data-ttu-id="52ba3-123">두 경우 모두 복사하는 데이터는 복사 대상 위치인 행의 열과 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-123">In either case, the data you are copying must be compatible with the columns in the rows you are copying to.</span></span> <span data-ttu-id="52ba3-124">예를 들어, `price`같은 열의 내용을 복사하는 경우 이 데이터를 복사해 넣을 행의 열에서 소수점이 포함된 숫자 데이터를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-124">For example, if you copy the contents of a column such as `price`, the column in the row you are copying to must accept numeric data with decimal places.</span></span> <span data-ttu-id="52ba3-125">행 전체를 복사하는 경우 대상 테이블에는 원본 테이블과 동일한 실제 위치에 원본 행과 호환되는 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-125">If you are copying an entire row, the destination table must have compatible columns in the same physical position as the source table.</span></span>  
  
 <span data-ttu-id="52ba3-126">결과 삽입 쿼리를 만들면 데이터를 복사하는 데 사용할 수 있는 옵션이 반영되도록 조건 창이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-126">When you create an Insert Results query, the Criteria pane changes to reflect options available for copying data.</span></span> <span data-ttu-id="52ba3-127">데이터를 복사해 넣을 대상 열을 지정하는 데 사용할 수 있는 추가 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-127">An Append column is added to allow you to specify the columns into which data should be copied.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="52ba3-128">결과 삽입 쿼리의 실행 동작을 취소할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-128">You cannot undo the action of executing an Insert Results query.</span></span> <span data-ttu-id="52ba3-129">문제가 발생할 경우에 대비하여 쿼리를 실행하기 전에 데이터를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-129">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-results-query"></a><span data-ttu-id="52ba3-130">결과 삽입 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="52ba3-130">To create an Insert Results query</span></span>  
  
1.  <span data-ttu-id="52ba3-131">새 쿼리를 만들고 행을 복사할 원본 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-131">Create a new query and add the table from which you want to copy rows (the source table).</span></span> <span data-ttu-id="52ba3-132">테이블 내에서 행을 복사하는 경우 원본 테이블을 대상 테이블로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-132">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
2.  <span data-ttu-id="52ba3-133">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **결과 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-133">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
3.  <span data-ttu-id="52ba3-134">[결과 삽입의 대상 테이블 선택 대화 상자](visual-database-tools.md)에서 행을 복사해 넣을 대상 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-134">In the [Choose Target Table for Insert Results Dialog Box](visual-database-tools.md), select the table to copy rows to (the destination table).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52ba3-135">쿼리 및 뷰 디자이너에서는 업데이트 가능한 테이블과 뷰를 미리 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-135">The Query and View Designer cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="52ba3-136">따라서 **결과 삽입의 대상 테이블 선택** 대화 상자의 **테이블 이름** 목록에는 쿼리하려는 데이터 연결에 사용 가능한 모든 테이블과 뷰가 표시됩니다. 여기에는 행을 복사해 넣을 수 없는 테이블이나 뷰도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-136">Therefore, the **Table Name** list in the **Choose Table for Insert From Query** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
4.  <span data-ttu-id="52ba3-137">테이블이나 테이블 반환 개체를 나타내는 사각형에서 복사하려는 내용이 들어 있는 열의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-137">In the rectangle representing the table or table-valued object, choose the names of the columns whose contents you want to copy.</span></span> <span data-ttu-id="52ba3-138">전체 행을 복사 하려면 \*\* \* (모든 열)\*\* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-138">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="52ba3-139">사용자가 선택한 열이 쿼리 및 뷰 디자이너에서 조건 창의 **열** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-139">The Query and View Designer adds the columns you choose to the **Column** column of the Criteriapane.</span></span>  
  
5.  <span data-ttu-id="52ba3-140">조건 창의 **추가** 열에서 복사하려는 각 열에 대한 대상 테이블의 대상 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-140">In the **Append** column of the Criteria pane, select a target column in the destination table for each column you are copying.</span></span> <span data-ttu-id="52ba3-141">전체 행을 복사 하는 경우 tablename을 선택 \*합니다. \* \*</span><span class="sxs-lookup"><span data-stu-id="52ba3-141">Choose *tablename.\** if you are copying entire rows.</span></span> <span data-ttu-id="52ba3-142">대상 테이블 열의 데이터 형식은 원본 테이블 열의 데이터 형식과 동일하거나 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-142">The columns in the destination table must have the same (or compatible) data types as the columns in the source table.</span></span>  
  
6.  <span data-ttu-id="52ba3-143">행을 특정 순서에 따라 복사하려면 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-143">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="52ba3-144">자세한 내용은 [쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52ba3-144">For details, see [Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).</span></span>  
  
7.  <span data-ttu-id="52ba3-145">**필터** 열에 검색 조건을 입력하여 복사할 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-145">Specify the rows to copy by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="52ba3-146">자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52ba3-146">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="52ba3-147">검색 조건을 지정하지 않으면 원본 테이블의 행 전체가 대상 테이블에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-147">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52ba3-148">검색할 열을 조건 창에 추가하면 쿼리 및 뷰 디자이너의 복사할 열 목록에도 이 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-148">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="52ba3-149">열을 검색만 하고 복사는 하지 않으려면 테이블 또는 테이블 반환 개체를 나타내는 사각형에서 열 이름 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-149">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
8.  <span data-ttu-id="52ba3-150">요약 정보를 복사하려면 그룹화 방법 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-150">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="52ba3-151">자세한 내용은 [쿼리 결과 요약&#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52ba3-151">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="52ba3-152">결과 삽입 쿼리를 실행해도 [결과 창](results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-152">When you execute an Insert Results query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="52ba3-153">대신, 복사한 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="52ba3-153">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ba3-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52ba3-154">See Also</span></span>  
 <span data-ttu-id="52ba3-155">[Visual Database Tools를 &#40;쿼리 유형&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="52ba3-155">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="52ba3-156">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="52ba3-156">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
