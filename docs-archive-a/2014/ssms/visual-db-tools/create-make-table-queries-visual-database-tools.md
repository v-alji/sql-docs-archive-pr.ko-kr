---
title: 테이블 만들기 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- table creation [SQL Server], Make Table query
- inserting tables
- Make Table query
- adding tables
ms.assetid: 4493cffa-7b2d-4c24-8ef0-d49329198972
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91c4a3bf45935053789d6e884b1af5b338b4c7c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731284"
---
# <a name="create-make-table-queries-visual-database-tools"></a><span data-ttu-id="b6724-102">테이블 만들기 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b6724-102">Create Make Table Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="b6724-103">테이블 만들기 쿼리를 사용하여 행을 새 테이블에 복사할 수 있습니다. 이 방법은 작업에 사용할 데이터의 하위 집합을 만들거나 한 데이터베이스에서 다른 데이터베이스로 테이블 내용을 복사하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-103">You can copy rows into a new table using a Make Table query, which is useful for creating subsets of data to work with or copying the contents of a table from one database to another.</span></span> <span data-ttu-id="b6724-104">테이블 만들기 쿼리는 결과 삽입 쿼리와 비슷하지만 행을 복사해 넣을 새 테이블을 만든다는 점에서 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-104">A Make Table query is similar to an Insert Results query but creates a new table to copy rows into.</span></span>  
  
 <span data-ttu-id="b6724-105">테이블 만들기 쿼리를 만들려면 다음 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-105">When you create a Make Table query, you specify:</span></span>  
  
-   <span data-ttu-id="b6724-106">새 데이터베이스 테이블(대상 테이블)의 이름</span><span class="sxs-lookup"><span data-stu-id="b6724-106">The name of the new database table (the destination table).</span></span>  
  
-   <span data-ttu-id="b6724-107">행을 복사할 하나 이상의 원본 테이블.</span><span class="sxs-lookup"><span data-stu-id="b6724-107">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="b6724-108">단일 테이블이나 조인된 테이블에서 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-108">You can copy from a single table or from joined tables.</span></span>  
  
-   <span data-ttu-id="b6724-109">해당 내용을 복사하려는 원본 테이블의 열</span><span class="sxs-lookup"><span data-stu-id="b6724-109">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="b6724-110">행을 특정 순서에 따라 복사하려는 경우 정렬 순서</span><span class="sxs-lookup"><span data-stu-id="b6724-110">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="b6724-111">복사할 행을 정의하는 검색 조건</span><span class="sxs-lookup"><span data-stu-id="b6724-111">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="b6724-112">요약 정보만 복사하려는 경우 그룹화 방법 옵션</span><span class="sxs-lookup"><span data-stu-id="b6724-112">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="b6724-113">예를 들어, 다음 쿼리에서는 `uk`_`customers` 라는 새 테이블을 만들고 `customers` 테이블에서 이 테이블로 정보를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-113">For example, the following query creates a new table called `uk`_`customers` and copies information from the `customers` table to it:</span></span>  
  
```  
SELECT *   
INTO uk_customers  
FROM customers  
WHERE country = 'UK'  
```  
  
 <span data-ttu-id="b6724-114">테이블 만들기 쿼리를 성공적으로 사용하려면</span><span class="sxs-lookup"><span data-stu-id="b6724-114">In order to use a Make Table query successfully:</span></span>  
  
-   <span data-ttu-id="b6724-115">데이터베이스에서 SELECT...INTO 구문을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-115">Your database must support the SELECT...INTO syntax.</span></span>  
  
-   <span data-ttu-id="b6724-116">대상 데이터베이스에 테이블을 만들 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-116">You must have permission to create a table in the target database.</span></span>  
  
### <a name="to-create-a-make-table-query"></a><span data-ttu-id="b6724-117">테이블 만들기 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b6724-117">To create a Make Table query</span></span>  
  
1.  <span data-ttu-id="b6724-118">하나 이상의 원본 테이블을 다이어그램 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-118">Add the source table or tables to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="b6724-119">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **테이블 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-119">From the **Query Designer** menu, point to **Change Type**, and then click **Make Table**.</span></span>  
  
3.  <span data-ttu-id="b6724-120">**테이블 만들기** 대화 상자에서 대상 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-120">In the **Make Table** dialog box, type the name of the destination table.</span></span> <span data-ttu-id="b6724-121">쿼리 및 뷰 디자이너는 이 이름이 이미 사용되고 있는지와 사용자에게 테이블을 만들 수 있는 권한이 있는지를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-121">The Query and View Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
     <span data-ttu-id="b6724-122">다른 데이터베이스에 대상 테이블을 만들려면 대상 데이터베이스의 이름, 소유자(필요한 경우) 및 테이블의 이름을 포함하는 정규화된 테이블 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-122">To create a destination table in another database, specify a fully qualified table name including the name of the target database, the owner (if required), and the name of the table.</span></span>  
  
4.  <span data-ttu-id="b6724-123">쿼리에 열을 추가하여 복사할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-123">Specify the columns to copy by adding them to the query.</span></span> <span data-ttu-id="b6724-124">자세한 내용은 [쿼리에 열 추가&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6724-124">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="b6724-125">열을 쿼리에 추가한 경우에만 열이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-125">Columns will be copied only if you add them to the query.</span></span> <span data-ttu-id="b6724-126">전체 행을 복사 하려면 \*\* \* (모든 열)\*\* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-126">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="b6724-127">사용자가 선택한 열이 쿼리 및 뷰 디자이너에서 조건 창의 **열** 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-127">The Query and View Designer adds the columns you choose to the **Column** column of the Criteria pane.</span></span>  
  
5.  <span data-ttu-id="b6724-128">행을 특정 순서에 따라 복사하려면 정렬 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-128">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="b6724-129">자세한 내용은 **쿼리 결과 정렬 및 그룹화**를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6724-129">For details, see **Sorting and Grouping Query Results**.</span></span>  
  
6.  <span data-ttu-id="b6724-130">검색 조건을 입력하여 복사할 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-130">Specify the rows to copy by entering search conditions.</span></span> <span data-ttu-id="b6724-131">자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6724-131">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="b6724-132">검색 조건을 지정하지 않으면 원본 테이블의 행 전체가 대상 테이블에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-132">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6724-133">검색할 열을 조건 창에 추가하면 쿼리 및 뷰 디자이너의 복사할 열 목록에도 이 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-133">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="b6724-134">열을 검색만 하고 복사는 하지 않으려면 테이블 또는 테이블 구조 개체를 나타내는 사각형에서 열 이름 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-134">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-structured object.</span></span>  
  
7.  <span data-ttu-id="b6724-135">요약 정보를 복사하려면 그룹화 방법 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-135">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="b6724-136">자세한 내용은 [쿼리 결과 요약&#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6724-136">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="b6724-137">테이블 만들기 쿼리를 실행해도 [결과 창](results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-137">When you execute a Make Table query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="b6724-138">대신, 복사한 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6724-138">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6724-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6724-139">See Also</span></span>  
 <span data-ttu-id="b6724-140">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b6724-140">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b6724-141">쿼리 형식&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b6724-141">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
