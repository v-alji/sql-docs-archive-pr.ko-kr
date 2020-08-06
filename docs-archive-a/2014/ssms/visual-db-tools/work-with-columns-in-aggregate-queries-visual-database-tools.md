---
title: 집계 쿼리에서 열 작업(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query summary results
- GROUP BY clause, query summary results
- aggregate queries [SQL Server]
- WHERE clause, query summary results
ms.assetid: 1b82681f-3d4f-4b9a-bb1d-2060e44f2577
author: stevestein
ms.author: sstein
ms.openlocfilehash: 880f7529cebd7f51951e62952e3b5f13190f99b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727715"
---
# <a name="work-with-columns-in-aggregate-queries-visual-database-tools"></a><span data-ttu-id="0a272-102">집계 쿼리에서 열 작업(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0a272-102">Work with Columns in Aggregate Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="0a272-103">집계 쿼리를 만드는 경우 [쿼리 및 뷰 디자이너](visual-database-tools.md) 에서는 특정 가정을 만들어 유효한 쿼리를 만들 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-103">When you create aggregate queries the [Query and View Designer](visual-database-tools.md) makes certain assumptions so that it can construct a valid query.</span></span> <span data-ttu-id="0a272-104">예를 들어 집계 쿼리를 만들 때 출력할 데이터 열을 표시하면 쿼리 및 뷰 디자이너가 이 열을 자동으로 GROUP BY 절의 일부로 만들기 때문에 요약에서 개별 행의 내용을 실수로 표시할 염려가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-104">For example, if you are creating an aggregate query and mark a data column for output, the Query and View Designer automatically makes the column part of the GROUP BY clause so that you do not inadvertently attempt to display the contents of an individual row in a summary.</span></span>  
  
## <a name="using-group-by"></a><span data-ttu-id="0a272-105">그룹화 방법 사용</span><span class="sxs-lookup"><span data-stu-id="0a272-105">Using Group By</span></span>  
 <span data-ttu-id="0a272-106">쿼리 및 뷰 디자이너는 아래 지침을 사용하여 열 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-106">The Query and View Designer uses the following guidelines for working with columns:</span></span>  
  
-   <span data-ttu-id="0a272-107">그룹화 방법 옵션을 선택하거나 쿼리에 집계 함수를 추가하면 출력용으로 표시되거나 정렬에 사용된 모든 열이 GROUP BY 절에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-107">When you choose the Group By option or add an aggregate function to a query, all columns marked for output or used for sorting are automatically added to the GROUP BY clause.</span></span> <span data-ttu-id="0a272-108">열이 이미 집계 함수의 일부인 경우 GROUP BY 절에 자동으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-108">Columns are not automatically added to the GROUP BY clause if they are already part of an aggregate function.</span></span>  
  
     <span data-ttu-id="0a272-109">특정 열을 GROUP BY 절의 일부로 포함하지 않으려면 조건 창의 그룹화 방법 열에서 다른 옵션을 선택하여 수동으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-109">If you do not want a particular column to be part of the GROUP BY clause, you must manually change it by selecting a different option in the Group By column of the Criteria pane.</span></span> <span data-ttu-id="0a272-110">그러나 이렇게 하면 쿼리 및 뷰 디자이너가 실행되지 않는 쿼리가 나타날 수 있는 옵션을 선택하는 것을 막을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-110">However, the Query and View Designer will not prevent you from choosing an option that can result in a query that will not run.</span></span>  
  
-   <span data-ttu-id="0a272-111">조건 창 또는 SQL 창에서 집계 함수에 쿼리 출력 열을 수동으로 추가하는 경우 쿼리 및 뷰 디자이너는 쿼리에서 다른 출력 열을 자동으로 삭제하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="0a272-111">If you manually add a query output column to an aggregate function in either the Criteria or SQL pane, the Query and View Designer does not automatically remove other output columns from the query.</span></span> <span data-ttu-id="0a272-112">쿼리 결과에서 나머지 열을 제거하거나 GROUP BY 절 또는 집계 함수의 일부로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-112">Therefore, you must remove the remaining columns from the query output or make them part of the GROUP BY clause or of an aggregate function.</span></span>  
  
 <span data-ttu-id="0a272-113">조건 창의 필터 열에 검색 조건을 입력하는 경우 쿼리 및 뷰 디자이너는 다음 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-113">When you enter a search condition into the Filter column of the Criteria pane, the Query and View Designer follows these rules:</span></span>  
  
-   <span data-ttu-id="0a272-114">집계 쿼리를 아직 지정하지 않아 표의 **그룹화 방법** 열이 표시되지 않는 경우 검색 조건이 WHERE 절에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-114">If the **Group By** column of the grid is not displayed (because you have not yet specified an aggregate query), the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="0a272-115">집계 쿼리에 있으면서 **그룹화 방법** 열에서 **위치** 옵션을 선택한 경우 검색 조건이 WHERE 절에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-115">If you are already in an aggregate query and have selected the option **Where** in the **Group By** column, the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="0a272-116">**그룹화 방법** 열에 **위치**이외의 다른 값이 있는 경우 검색 조건이 HAVING 절에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-116">If the **Group By** column contains any value other than **Where**, the search condition is placed in the HAVING clause.</span></span>  
  
## <a name="using-the-having-and-where-clauses"></a><span data-ttu-id="0a272-117">HAVING 및 WHERE 절 사용</span><span class="sxs-lookup"><span data-stu-id="0a272-117">Using the HAVING and WHERE Clauses</span></span>  
 <span data-ttu-id="0a272-118">아래 원칙은 검색 조건으로 집계 쿼리에서 열을 참조할 수 있는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-118">The following principles describe how you can reference columns in an aggregate query in search conditions.</span></span> <span data-ttu-id="0a272-119">일반적으로 검색 조건에 열을 사용하면 요약할 행을 필터링하거나(WHERE 절) 최종 출력에 나타날 그룹화된 결과를 결정할 수 있습니다(HAVING 절).</span><span class="sxs-lookup"><span data-stu-id="0a272-119">In general, you can use a column in a search condition to filter the rows that should be summarized (a WHERE clause) or to determine which grouped results appear in the final output (a HAVING clause).</span></span>  
  
-   <span data-ttu-id="0a272-120">개별 데이터 열은 쿼리에 사용되는 방법에 따라 WHERE 절 또는 HAVING 절에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-120">Individual data columns can appear in either the WHERE or HAVING clause, depending on how they are used elsewhere in the query.</span></span>  
  
-   <span data-ttu-id="0a272-121">WHERE 절은 요약 및 그룹화할 행의 하위 집합을 선택하는 데 사용되므로 그룹화하기 전에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-121">WHERE clauses are used to select a subset of rows for summarizing and grouping and are thus applied before any grouping is done.</span></span> <span data-ttu-id="0a272-122">따라서 데이터 열이 GROUP BY 절의 일부가 아니거나 집계 함수에 포함되어 있지 않더라도 WHERE 절에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-122">Therefore, you can use a data column in a WHERE clause even if it is not part of the GROUP BY clause or contained in an aggregate function.</span></span> <span data-ttu-id="0a272-123">예를 들어 다음 문은 가격이 $10.00가 넘는 책의 제목을 모두 선택하여 해당 가격의 평균을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-123">For example, the following statement selects all titles that cost more than $10.00 and averages the price:</span></span>  
  
    ```  
    SELECT AVG(price)  
    FROM titles  
    WHERE price > 10  
    ```  
  
-   <span data-ttu-id="0a272-124">GROUP BY 절 또는 집계 함수에서도 사용되는 열을 포함하는 검색 조건을 만들면 해당 검색 조건이 WHERE 절 또는 HAVING 절로 나타날 수 있으며, 이에 따라 사용자는 조건 작성 여부 및 시기를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-124">If you create a search condition that involves a column also used in a GROUP BY clause or aggregate function, the search condition can appear as either a WHERE clause or a HAVING clause - you can decide which when you create the condition.</span></span> <span data-ttu-id="0a272-125">예를 들어 다음 문은 각 출판사가 발행하는 책의 평균 가격을 계산한 다음 평균 가격이 $10.00가 넘는 출판사의 평균 가격을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-125">For example, the following statement creates an average price for the titles for each publisher, then displays the average for the publishers in which the average price is greater than $10.00:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
-   <span data-ttu-id="0a272-126">검색 조건으로 집계 함수를 사용하는 경우 조건에는 요약이 포함되며 따라서 HAVING 절의 일부가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a272-126">If you use an aggregate function in a search condition, the condition involves a summary and must therefore be part of the HAVING clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a272-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a272-127">See Also</span></span>  
 <span data-ttu-id="0a272-128">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0a272-128">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="0a272-129">쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="0a272-129">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
