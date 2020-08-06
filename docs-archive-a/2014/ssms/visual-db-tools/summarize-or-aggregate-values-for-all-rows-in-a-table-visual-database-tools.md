---
title: 테이블의 모든 행에 대 한 값 요약 또는 집계 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4d80c8ab2b811b8e796f0a37b2180a2866c332
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735795"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="b6676-102">테이블에 있는 모든 행의 값 요약 또는 집계(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b6676-102">Summarize or Aggregate Values for All Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="b6676-103">집계 함수를 사용하면 테이블의 모든 값을 요약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-103">Using an aggregate function, you can create a summary for all the values in a table.</span></span> <span data-ttu-id="b6676-104">예를 들어, `titles` 테이블의 책 전체에 대한 가격 합계를 표시하는 다음과 같은 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-104">For example, you can create a query such as the following to display the total price for all books in the `titles` table:</span></span>  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="b6676-105">집계 함수를 여러 열에 사용하면 동일한 쿼리에서 여러 집계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-105">You can create multiple aggregations in the same query by using aggregate functions with more than one column.</span></span> <span data-ttu-id="b6676-106">예를 들어, `price` 열의 합계와 `discount` 열의 평균을 계산하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-106">For example, you can create a query that calculates the total of the `price` column and the average of the `discount` column.</span></span>  
  
 <span data-ttu-id="b6676-107">동일한 쿼리에서 합계, 개수, 평균 등과 같이 서로 다른 방식으로 동일한 열을 집계할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-107">You can also aggregate the same column in different ways (such as totaling, counting, and averaging) in the same query.</span></span> <span data-ttu-id="b6676-108">예를 들어, 다음 쿼리는 `price` 테이블의 `titles` 열에 대한 평균과 합계를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-108">For example, the following query averages and summarizes the `price` column from the `titles` table:</span></span>  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="b6676-109">검색 조건을 추가하면 해당 조건에 맞는 행의 하위 집합을 집계할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-109">If you add a search condition, you can aggregate the subset of rows that meet that condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6676-110">테이블의 전체 행 수나 특정 조건에 맞는 행의 수를 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-110">You can also count all the rows in the table or the ones that meet a specific condition.</span></span> <span data-ttu-id="b6676-111">자세한 내용은 [테이블의 행 계산&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6676-111">For details, see [Count Rows in a Table &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="b6676-112">테이블의 모든 행에 대한 단일 집계 값을 만들면 집계 값 자체만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-112">When you create a single aggregation value for all rows in a table, you display only the aggregate values themselves.</span></span> <span data-ttu-id="b6676-113">예를 들어, `price` 테이블의 `titles` 열에 대한 값을 합산하는 경우 개별 제목, 출판사 이름 등은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-113">For example, if you are totaling the value of the `price` column of the `titles` table, you would not also display individual titles, publisher names, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6676-114">부분합을 계산하는 경우 즉, 그룹을 만드는 경우 각 그룹에 대한 열 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-114">If you are subtotaling - that is, creating groups - you can display column values for each group.</span></span> <span data-ttu-id="b6676-115">자세한 내용은 [쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6676-115">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
### <a name="to-aggregate-values-for-all-rows"></a><span data-ttu-id="b6676-116">모든 행의 값을 집계하려면</span><span class="sxs-lookup"><span data-stu-id="b6676-116">To aggregate values for all rows</span></span>  
  
1.  <span data-ttu-id="b6676-117">집계하려는 테이블이 다이어그램 창에 표시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-117">Be sure the table you want to aggregate is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="b6676-118">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **그룹화 방법** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-118">Right-click the background of the Diagram pane, then choose **Group By** from the shortcut menu.</span></span> <span data-ttu-id="b6676-119">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md) 에서 **그룹화** 방법 열이 조건 창의 표에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-119">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="b6676-120">집계하려는 열을 조건 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-120">Add the column you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="b6676-121">열을 출력하도록 선택되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-121">Be sure that the column is marked for output.</span></span>  
  
     <span data-ttu-id="b6676-122">쿼리 및 뷰 디자이너에서 요약 대상 열에 대한 열 별칭이 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-122">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="b6676-123">이 별칭을 좀 더 의미 있는 별칭으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-123">You can replace this alias with a more meaningful one.</span></span> <span data-ttu-id="b6676-124">자세한 내용은 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6676-124">For details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="b6676-125">표 형태의 **그룹화 방법** 열에서 **Sum**, **Avg**, **Min**, **Max**, **Count** 등 적절한 집계 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-125">In the **Group By** grid column, select the appropriate aggregate function, such as: **Sum**, **Avg**, **Min**, **Max**, **Count**.</span></span> <span data-ttu-id="b6676-126">결과 집합에서 고유 행만 집계하려면 집계 함수를 선택할 때 DISTINCT 옵션을 사용합니다(예: **Min Distinct**).</span><span class="sxs-lookup"><span data-stu-id="b6676-126">If you want to aggregate only unique rows in the result set, choose an aggregate function with the DISTINCT options, such as **Min Distinct**.</span></span> <span data-ttu-id="b6676-127">**Group By**, **Expression**또는 **Where**는 선택하지 말아야 합니다. 모든 행을 집계할 때는 이러한 옵션이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-127">Do not choose **Group By**, **Expression**, or **Where**, because those options do not apply when you are aggregating all rows.</span></span>  
  
     <span data-ttu-id="b6676-128">쿼리 및 뷰 디자이너에서 [SQL 창](sql-pane-visual-database-tools.md) 에 있는 문의 열 이름이 사용자가 지정한 집계 함수로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-128">The Query and View Designer replaces the column name in the statement in the [SQL pane](sql-pane-visual-database-tools.md) with the aggregate function that you specify.</span></span> <span data-ttu-id="b6676-129">예를 들어, SQL 문은 다음과 같은 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-129">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  <span data-ttu-id="b6676-130">쿼리에서 두 개 이상의 집계를 만들려면 3단계와 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-130">If you want to create more than one aggregation in the query, repeat steps 3 and 4.</span></span>  
  
     <span data-ttu-id="b6676-131">쿼리 결과 목록이나 정렬 기준 목록에 다른 열을 추가하면 쿼리 및 뷰 디자이너에서 표 형태의 **그룹화 방법** 열에 **Group By** 라는 용어가 자동으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-131">When you add another column to the query output list or order by list, the Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span> <span data-ttu-id="b6676-132">적절한 집계 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-132">Select the appropriate aggregate function.</span></span>  
  
6.  <span data-ttu-id="b6676-133">필요한 경우 검색 조건을 추가하여 요약하려는 행의 하위 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-133">Add search conditions, if any, to specify the subset of rows you want to summarize.</span></span>  
  
 <span data-ttu-id="b6676-134">쿼리를 실행하면 지정된 집계가 결과 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-134">When you execute the query, the Results pane displays the aggregations that you specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6676-135">그룹화 방법 모드를 명시적으로 종료하지 않는 한 쿼리 및 뷰 디자이너의 SQL 창에서 집계 함수가 SQL 문의 일부로 계속 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-135">The Query and View Designer maintains aggregate functions as part of the SQL statement in the SQL pane until you explicitly turn off Group By mode.</span></span> <span data-ttu-id="b6676-136">따라서, 다이어그램 창에 표시되는 테이블이나 테이블 반환 개체를 변경하거나 쿼리 형식을 변경하여 쿼리를 수정하면 결과 쿼리에 잘못된 집계 함수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6676-136">Therefore, if you modify your query by changing its type or by changing which tables or table-valued objects are present in the Diagram pane, the resulting query might include invalid aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6676-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6676-137">See Also</span></span>  
 <span data-ttu-id="b6676-138">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b6676-138">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b6676-139">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b6676-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
