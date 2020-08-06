---
title: 쿼리 결과 행 그룹화(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing table subsets
- grouping rows
- grouping query results
ms.assetid: b07082d5-4d55-4903-9af9-4c470554c6d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52de25c86425d95f5917d89c8a3f4fec8939fb16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651978"
---
# <a name="group-rows-in-query-results-visual-database-tools"></a><span data-ttu-id="00e8f-102">쿼리 결과 행 그룹화(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="00e8f-102">Group Rows in Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="00e8f-103">부분합을 계산하거나 테이블의 하위 집합에 대한 다른 요약 정보를 표시하려면 집계 쿼리를 사용하여 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-103">If you want to create subtotals or show other summary information for subsets of a table, you create groups using an aggregate query.</span></span> <span data-ttu-id="00e8f-104">각 그룹은 테이블에서 값이 동일한 모든 행의 데이터를 요약하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-104">Each group summarizes the data for all the rows in the table that have the same value.</span></span>  
  
 <span data-ttu-id="00e8f-105">예를 들어, `titles` 테이블에서 출판사별로 구분된 도서 평균 가격 결과를 확인해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-105">For example, you might want to see the average price of a book in the `titles` table, but break the results down by publisher.</span></span> <span data-ttu-id="00e8f-106">이 경우 출판사별로 쿼리를 그룹화할 수 있습니다(예: `pub_id`).</span><span class="sxs-lookup"><span data-stu-id="00e8f-106">To do so, you group the query by publisher (for example, `pub_id`).</span></span> <span data-ttu-id="00e8f-107">다음과 같은 쿼리 결과가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-107">The resulting query output might look like this:</span></span>  
  
 <span data-ttu-id="00e8f-108">![쿼리 결과: 게시자별로 그룹화된 평균 가격](../../database-engine/media//dv3w9e1.gif "쿼리 결과: 게시자별로 그룹화된 평균 가격")</span><span class="sxs-lookup"><span data-stu-id="00e8f-108">![Query results: average price grouped by publisher](../../database-engine/media//dv3w9e1.gif "Query results: average price grouped by publisher")</span></span>  
  
 <span data-ttu-id="00e8f-109">데이터를 그룹화하면 다음과 같이 요약 데이터나 그룹화된 데이터만 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-109">When you group data, you can display only summary or grouped data, such as:</span></span>  
  
-   <span data-ttu-id="00e8f-110">GROUP BY 절에 나타나는 그룹화된 열의 값.</span><span class="sxs-lookup"><span data-stu-id="00e8f-110">The values of the grouped columns (those that appear in the GROUP BY clause).</span></span> <span data-ttu-id="00e8f-111">위 예제에서 `pub_id` 는 그룹화된 열입니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-111">In the example above, `pub_id` is the grouped column.</span></span>  
  
-   <span data-ttu-id="00e8f-112">SUM( ) 및 AVG( ) 같은 집계 함수를 통해 얻은 값.</span><span class="sxs-lookup"><span data-stu-id="00e8f-112">Values produced by aggregate functions such as SUM( ) and AVG( ).</span></span> <span data-ttu-id="00e8f-113">위 예제에서 두 번째 열은 AVG( ) 함수를 `price` 열에 적용하여 얻은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-113">In the example above, the second column is produced by using the AVG( ) function with the `price` column.</span></span>  
  
 <span data-ttu-id="00e8f-114">개별 행의 값은 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-114">You cannot display values from individual rows.</span></span> <span data-ttu-id="00e8f-115">예를 들어, 출판사만을 기준으로 그룹화한 경우 쿼리의 개별 책 제목은 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-115">For example, if you group only by publisher, you cannot also display individual titles in the query.</span></span> <span data-ttu-id="00e8f-116">따라서 쿼리 결과에 열을 추가하면 [쿼리 및 뷰 디자이너](visual-database-tools.md) 의 [SQL 창](sql-pane-visual-database-tools.md)에서 이러한 열이 문의 GROUP BY 절에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-116">Therefore, if you add columns to the query output, the [Query and View Designer](visual-database-tools.md) automatically adds them to the GROUP BY clause of the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="00e8f-117">열에 대한 집계 함수를 지정하면 해당 열을 대신 집계할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-117">If you want a column to be aggregated instead, you can specify an aggregate function for that column.</span></span>  
  
 <span data-ttu-id="00e8f-118">두 개 이상의 열을 기준으로 그룹화하는 경우 쿼리의 각 그룹에는 전체 그룹 열의 집계 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-118">If you group by more than one column, each group in the query shows the aggregate values for all grouping columns.</span></span>  
  
 <span data-ttu-id="00e8f-119">예를 들어, `titles` 테이블에 대한 아래 쿼리에서는 출판사(`pub_id`)와 도서 종류(`type`)를 기준으로 결과를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-119">For example, the following query against the `titles` table groups by publisher (`pub_id`) and also by book type (`type`).</span></span> <span data-ttu-id="00e8f-120">쿼리 결과는 출판사 순으로 정렬되고 각 출판사에서 발생하는 서로 다른 도서 종류 각각에 대한 요약 정보가 결과에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-120">The query results are ordered by publisher and show summary information for each different type of book that the publisher produces:</span></span>  
  
```  
SELECT pub_id, type, SUM(price) Total_price  
FROM titles  
GROUP BY pub_id, type  
```  
  
 <span data-ttu-id="00e8f-121">출력 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-121">The resulting output might look like this:</span></span>  
  
 <span data-ttu-id="00e8f-122">![쿼리 결과: 게시자 및 유형별로 그룹화된 가격](../../database-engine/media//dv3w9e2.gif "쿼리 결과: 게시자 및 유형별로 그룹화된 가격")</span><span class="sxs-lookup"><span data-stu-id="00e8f-122">![Query results: price grouped by publisher and type](../../database-engine/media//dv3w9e2.gif "Query results: price grouped by publisher and type")</span></span>  
  
### <a name="to-group-rows"></a><span data-ttu-id="00e8f-123">행을 그룹화하려면</span><span class="sxs-lookup"><span data-stu-id="00e8f-123">To group rows</span></span>  
  
1.  <span data-ttu-id="00e8f-124">요약하려는 테이블을 다이어그램 창에 추가하여 쿼리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-124">Start the query by adding the tables you want to summarize to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="00e8f-125">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **그룹화 방법 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-125">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="00e8f-126">쿼리 및 뷰 디자이너에서 **그룹화 방법** 열이 조건 창의 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-126">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="00e8f-127">그룹화하려는 하나 이상의 열을 조건 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-127">Add the column or columns you want to group to the Criteria pane.</span></span> <span data-ttu-id="00e8f-128">쿼리 결과에 열을 표시하려면 해당 결과에 대해 **출력** 열을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-128">If you want the column to appear in the query output, be sure that the **Output** column is selected for output.</span></span>  
  
     <span data-ttu-id="00e8f-129">쿼리 및 뷰 디자이너의 SQL 창에서 GROUP BY 절이 문에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-129">The Query and View Designer adds a GROUP BY clause to the statement in the SQL pane.</span></span> <span data-ttu-id="00e8f-130">예를 들어, SQL 문은 다음과 같은 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-130">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT pub_id  
    FROM titles  
    GROUP BY pub_id  
    ```  
  
4.  <span data-ttu-id="00e8f-131">집계하려는 하나 이상의 열을 조건 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-131">Add the column or columns you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="00e8f-132">열을 출력하도록 선택되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-132">Be sure that the column is marked for output.</span></span>  
  
5.  <span data-ttu-id="00e8f-133">집계하려는 열에 대한 **그룹화 방법** 표 셀에서 적절한 집계 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-133">In the **Group By** grid cell for the column that is going to be aggregated, select the appropriate aggregate function.</span></span>  
  
     <span data-ttu-id="00e8f-134">쿼리 및 뷰 디자이너에서 요약 대상 열에 대한 열 별칭이 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-134">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="00e8f-135">자동으로 생성된 이 별칭을 좀 더 의미 있는 별칭으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-135">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="00e8f-136">자세한 내용은 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00e8f-136">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="00e8f-137">![쿼리 결과 집합에 열 별칭 추가](../../database-engine/media//dv3w9e3.gif "쿼리 결과 집합에 열 별칭 추가")</span><span class="sxs-lookup"><span data-stu-id="00e8f-137">![Adding a column alias to the query result set](../../database-engine/media//dv3w9e3.gif "Adding a column alias to the query result set")</span></span>  
  
     <span data-ttu-id="00e8f-138">해당 문이 **SQL** 창에 다음과 같은 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00e8f-138">The corresponding statement in the **SQL** pane might look like this:</span></span>  
  
    ```  
    SELECT   pub_id, SUM(price) AS Totalprice  
    FROM     titles  
    GROUP BY pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="00e8f-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00e8f-139">See Also</span></span>  
 [<span data-ttu-id="00e8f-140">쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="00e8f-140">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
