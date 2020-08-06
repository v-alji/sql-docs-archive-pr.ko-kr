---
title: 동일한 쿼리에서 HAVING 및 WHERE 절 사용 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- search conditions [SQL Server], HAVING clause
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- HAVING clause, search criteria
- search conditions [SQL Server], WHERE clause
- WHERE clause, search criteria
- excluding rows
ms.assetid: 1e07cf56-b4b7-4c49-8ddd-c276812a7148
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f6b471a60bf225ee61bdbbf0ecec30f21a92cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729007"
---
# <a name="use-having-and-where-clauses-in-the-same-query-visual-database-tools"></a><span data-ttu-id="f7930-102">동일한 쿼리에서 HAVING 및 WHERE 절 사용(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f7930-102">Use HAVING and WHERE Clauses in the Same Query (Visual Database Tools)</span></span>
  <span data-ttu-id="f7930-103">경우에 따라서는 HAVING 절을 사용하여 그룹 전체에 조건을 적용하기 전에 WHERE 절을 사용하여 그룹에서 개별 행을 제외해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-103">In some instances, you might want to exclude individual rows from groups (using a WHERE clause) before applying a condition to groups as a whole (using a HAVING clause).</span></span>  
  
 <span data-ttu-id="f7930-104">HAVING 절은 WHERE 절과 비슷하지만 그룹 전체 즉, 그룹을 나타내는 결과 집합의 행에만 적용된다는 점에서 차이가 있습니다. 반면, WHERE 절은 개별 행에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-104">A HAVING clause is like a WHERE clause, but applies only to groups as a whole (that is, to the rows in the result set representing groups), whereas the WHERE clause applies to individual rows.</span></span> <span data-ttu-id="f7930-105">쿼리에는 WHERE 절과 HAVING 절이 모두 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-105">A query can contain both a WHERE clause and a HAVING clause.</span></span> <span data-ttu-id="f7930-106">이 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-106">In that case:</span></span>  
  
-   <span data-ttu-id="f7930-107">다이어그램 창에서 테이블이나 테이블 반환 개체의 개별 행에 WHERE 절이 먼저 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-107">The WHERE clause is applied first to the individual rows in the tables or table-valued objects in the Diagram pane.</span></span> <span data-ttu-id="f7930-108">WHERE 절의 조건에 맞는 행만 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-108">Only the rows that meet the conditions in the WHERE clause are grouped.</span></span>  
  
-   <span data-ttu-id="f7930-109">그런 다음 결과 집합의 행에 HAVING 절이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-109">The HAVING clause is then applied to the rows in the result set.</span></span> <span data-ttu-id="f7930-110">HAVING 조건에 맞는 그룹만 쿼리 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-110">Only the groups that meet the HAVING conditions appear in the query output.</span></span> <span data-ttu-id="f7930-111">집계 함수나 GROUP BY 절에도 나타나는 열에만 HAVING 절을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-111">You can apply a HAVING clause only to columns that also appear in the GROUP BY clause or in an aggregate function.</span></span>  
  
 <span data-ttu-id="f7930-112">예를 들어 `titles` 및 `publishers` 테이블을 조인하여 여러 출판사의 평균 도서 가격을 표시하는 쿼리를 만드는 경우를 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-112">For example, imagine that you are joining the `titles` and `publishers` tables to create a query showing the average book price for a set of publishers.</span></span> <span data-ttu-id="f7930-113">캘리포니아 주에 있는 출판사 등과 같이 특정 출판사 세트에 대해서만 평균 가격을 표시하려는 경우</span><span class="sxs-lookup"><span data-stu-id="f7930-113">You want to see the average price for only a specific set of publishers - perhaps only the publishers in the state of California.</span></span> <span data-ttu-id="f7930-114">그 중에서도 평균 가격이 $10.00 이상인 경우로만 결과를 제한하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-114">And even then, you want to see the average price only if it is over $10.00.</span></span>  
  
 <span data-ttu-id="f7930-115">평균 가격을 계산하기 전에 캘리포니아에 있지 않은 출판사는 모두 제외하도록 WHERE 절을 사용하여 첫 번째 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-115">You can establish the first condition by including a WHERE clause, which discards any publishers that are not in California, before calculating average prices.</span></span> <span data-ttu-id="f7930-116">두 번째 조건은 데이터를 그룹화하고 요약한 결과를 기반으로 해야 하므로 이 조건에는 HAVING 절이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-116">The second condition requires a HAVING clause, because the condition is based on the results of grouping and summarizing the data.</span></span> <span data-ttu-id="f7930-117">결과 SQL 문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-117">The resulting SQL statement might look like this:</span></span>  
  
```  
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10  
```  
  
 <span data-ttu-id="f7930-118">HAVING 절과 WHERE 절을 모두 조건 창에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-118">You can create both HAVING and WHERE clauses in the Criteria pane.</span></span> <span data-ttu-id="f7930-119">기본적으로 열에 대한 검색 조건을 지정하면 이 조건이 HAVING 절의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-119">By default, if you specify a search condition for a column, the condition becomes part of the HAVING clause.</span></span> <span data-ttu-id="f7930-120">그러나 이 조건이 WHERE 절에 사용되도록 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-120">However, you can change the condition to be a WHERE clause.</span></span>  
  
 <span data-ttu-id="f7930-121">동일한 열을 대상으로 WHERE 절과 HAVING 절을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-121">You can create a WHERE clause and HAVING clause involving the same column.</span></span> <span data-ttu-id="f7930-122">이렇게 하려면 조건 창에 열을 두 번 추가한 다음 한 인스턴스는 HAVING 절의 일부로 지정하고 다른 인스턴스는 WHERE 절의 일부로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-122">To do so, you must add the column twice to the Criteria pane, then specify one instance as part of the HAVING clause and the other instance as part of the WHERE clause.</span></span>  
  
### <a name="to-specify-a-where-condition-in-an-aggregate-query"></a><span data-ttu-id="f7930-123">집계 쿼리에서 WHERE 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f7930-123">To specify a WHERE condition in an aggregate query</span></span>  
  
1.  <span data-ttu-id="f7930-124">쿼리의 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-124">Specify the groups for your query.</span></span> <span data-ttu-id="f7930-125">자세한 내용은 [쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7930-125">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="f7930-126">WHERE 조건의 기반으로 삼을 열이 아직 조건 창에 없으면 이 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-126">If it is not already in the Criteria pane, add the column on which you want to base the WHERE condition.</span></span>  
  
3.  <span data-ttu-id="f7930-127">데이터 열이 GROUP BY 절의 일부가 아니거나 집계 함수에 포함되지 않은 경우 **출력** 열을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-127">Clear the **Output** column unless the data column is part of the GROUP BY clause or included in an aggregate function.</span></span>  
  
4.  <span data-ttu-id="f7930-128">**필터** 열에서 WHERE 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-128">In the **Filter** column, specify the WHERE condition.</span></span> <span data-ttu-id="f7930-129">쿼리 및 뷰 디자이너에서 SQL 문의 HAVING 절에 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-129">The Query and View Designer adds the condition to the HAVING clause of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7930-130">이 절차의 예제로 나와 있는 쿼리에서는 `titles` 테이블과 `publishers`테이블을 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-130">The query shown in the example for this procedure joins two tables, `titles` and `publishers`.</span></span>  
  
     <span data-ttu-id="f7930-131">HAVING 절은 쿼리의 다음 지점에서 SQL 문에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-131">At this point in the query, the SQL statement contains a HAVING clause:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    GROUP BY titles.pub_id  
    HAVING publishers.state = 'CA'  
    ```  
  
5.  <span data-ttu-id="f7930-132">**그룹화 방법** 열의 그룹 및 요약 옵션 목록에서 **Where** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-132">In the **Group By** column, select **Where** from the list of group and summary options.</span></span> <span data-ttu-id="f7930-133">쿼리 및 뷰 디자이너에서 SQL 문의 HAVING 절에 있던 조건이 제거되고 WHERE 절에 조건이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-133">The Query and View Designer removes the condition from the HAVING clause in the SQL statement and adds it to the WHERE clause.</span></span>  
  
     <span data-ttu-id="f7930-134">다음과 같이 WHERE 절이 대신 포함되도록 SQL 문이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7930-134">The SQL statement changes to include a WHERE clause instead:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    WHERE publishers.state = 'CA'  
    GROUP BY titles.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f7930-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7930-135">See Also</span></span>  
 <span data-ttu-id="f7930-136">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f7930-136">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f7930-137">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f7930-137">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
