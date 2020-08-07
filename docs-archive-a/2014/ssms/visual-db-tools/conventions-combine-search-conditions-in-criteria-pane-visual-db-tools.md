---
title: 조건 창의 검색 조건 결합 규칙 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- multiple OR clauses
- combining search conditions
- OR operator
- AND, Criteria pane
- multiple AND clauses
ms.assetid: d4859be5-ff5b-48b2-a101-ad40c6dbcc68
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684521baa87d5325366a0e18296cd35342a0e947
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727807"
---
# <a name="conventions-for-combining-search-conditions-in-the-criteria-pane-visual-database-tools"></a><span data-ttu-id="0fb53-102">조건 창의 검색 조건 결합 규칙(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0fb53-102">Conventions for Combining Search Conditions in the Criteria Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="0fb53-103">AND와 OR 연산자를 여러 개 연결하여 다수의 검색 조건을 포함하는 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-103">You can create queries that include any number of search conditions, linked with any number of AND and OR operators.</span></span> <span data-ttu-id="0fb53-104">AND 절과 OR 절을 조합하여 만든 쿼리는 복잡할 수 있으므로 쿼리 실행 시 쿼리를 해석하는 방법 및 [조건 창](visual-database-tools.md)과 [SQL 창](sql-pane-visual-database-tools.md)에서 쿼리를 나타내는 방법을 이해하면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-104">A query with a combination of AND and OR clauses can become complex, so it is helpful to understand how such a query is interpreted when you execute it, and how such a query is represented in the [Criteria Pane](visual-database-tools.md) and [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fb53-105">AND 또는 OR 연산자가 하나만 포함된 검색 조건에 대한 자세한 내용은 [한 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) 및 [여러 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fb53-105">For details about search conditions that contain only one AND or OR operator, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) and [Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="0fb53-106">아래에서 다음에 대한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-106">Below you will find information about:</span></span>  
  
-   <span data-ttu-id="0fb53-107">AND와 OR를 모두 포함하는 쿼리에서 AND와 OR의 우선 순위</span><span class="sxs-lookup"><span data-stu-id="0fb53-107">The precedence of AND and OR in queries that contain both.</span></span>  
  
-   <span data-ttu-id="0fb53-108">AND 절과 OR 절에 있는 조건들이 논리적으로 서로 연관되는 방법</span><span class="sxs-lookup"><span data-stu-id="0fb53-108">How the conditions in AND and OR clauses relate logically to one another.</span></span>  
  
-   <span data-ttu-id="0fb53-109">쿼리 및 뷰 디자이너가 AND와 OR를 모두 포함하는 쿼리를 조건 창에 나타내는 방법</span><span class="sxs-lookup"><span data-stu-id="0fb53-109">How the Query and View Designer represents in the Criteria Pane queries that contain both AND and OR.</span></span>  
  
 <span data-ttu-id="0fb53-110">아래의 설명을 쉽게 이해하기 위해 `employee` , `hire_date`및 `job_lvl`열을 포함하는 `status`테이블을 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-110">To help you understand the discussion below, imagine that you are working with an `employee` table containing the columns `hire_date`, `job_lvl`, and `status`.</span></span> <span data-ttu-id="0fb53-111">이 예제에서는 사용자가 직원의 근무 연수(입사 날짜), 업무 유형(직급), 상태(예: 퇴직) 등의 정보를 알고 있어야 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-111">The examples assume that you need to know information such as how long an employee has worked with the company (that is, what the employee's hire date is), what type of job the employee performs (what the job level is), and the employee's status (for example, retired).</span></span>  
  
## <a name="precedence-of-and-and-or"></a><span data-ttu-id="0fb53-112">AND와 OR의 우선 순위</span><span class="sxs-lookup"><span data-stu-id="0fb53-112">Precedence of AND and OR</span></span>  
 <span data-ttu-id="0fb53-113">쿼리를 실행하면 AND로 연결된 절을 먼저 계산한 다음 OR로 연결된 절을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-113">When a query is executed, it evaluates first the clauses linked with AND, and then those linked with OR.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fb53-114">NOT 연산자는 AND와 OR보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-114">The NOT operator takes precedence over both AND and OR.</span></span>  
  
 <span data-ttu-id="0fb53-115">예를 들어, 직급이 낮은 직원 중에서 근무 연수가 5년이 넘는 직원 또는 입사 날짜에 관계없이 중간 직급의 직원을 찾기 위해 WHERE 절을 다음과 같이 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-115">For example, to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs without regard for their hire date, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   job_lvl = 100 OR  
   job_lvl = 200  
  
```  
  
 <span data-ttu-id="0fb53-116">OR보다 AND가 우선하는 기본 우선 순위를 무시하려면 SQL 창에서 특정 조건을 괄호로 묶으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-116">To override the default precedence of AND over OR, you can put parentheses around specific conditions in the SQL pane.</span></span> <span data-ttu-id="0fb53-117">괄호 안의 조건은 항상 가장 먼저 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-117">Conditions in parentheses are always evaluated first.</span></span> <span data-ttu-id="0fb53-118">예를 들어, 직급이 낮거나 중간인 직원 중에서 근무 연수가 5년이 넘는 직원을 모두 찾으려면 WHERE 절을 다음과 같이 구성하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-118">For example, to find all employees who have been with the company more than five years in either lower or middle-level jobs, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
> [!TIP]  
>  <span data-ttu-id="0fb53-119">AND 절과 OR 절을 결합할 때에는 기본 우선 순위에 의존하지 않고 항상 괄호를 사용하여 명확하게 나타내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-119">It is recommended that, for clarity, you always include parentheses when combining AND and OR clauses instead of relying on the default precedence.</span></span>  
  
## <a name="how-and-works-with-multiple-or-clauses"></a><span data-ttu-id="0fb53-120">OR 절이 여러 개 있는 경우 AND가 적용되는 방법</span><span class="sxs-lookup"><span data-stu-id="0fb53-120">How AND Works with Multiple OR Clauses</span></span>  
 <span data-ttu-id="0fb53-121">AND 절과 OR 절을 결합할 때 이 절들이 서로 연관되는 방식을 이해하면 쿼리 및 뷰 디자이너에서 복잡한 쿼리를 구성하고 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-121">Understanding how AND and OR clauses are related when combined can help you construct and understand complex queries in the Query and View Designer.</span></span>  
  
 <span data-ttu-id="0fb53-122">AND를 사용하여 여러 개의 조건을 연결하는 경우 AND로 연결된 첫째 조건 집합이 둘째 집합의 모든 조건에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-122">If you link multiple conditions using AND, the first set of conditions linked with AND applies to all the conditions in the second set.</span></span> <span data-ttu-id="0fb53-123">즉 다른 조건에 AND로 연결된 조건은 둘째 집합에 있는 모든 조건에 분배됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-123">In other words, a condition linked with AND to another condition is distributed to all the conditions in the second set.</span></span> <span data-ttu-id="0fb53-124">예를 들어, 아래의 표현식은 AND 조건이 OR 조건 집합에 연결된 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-124">For example, the following schematic representation shows an AND condition linked to a set of OR conditions:</span></span>  
  
```  
A AND (B OR C)  
```  
  
 <span data-ttu-id="0fb53-125">위의 표현은 둘째 조건 집합에 AND 조건이 분배되는 방법을 보여 주는 아래 표현식과 논리적으로 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-125">The representation above is logically equivalent to the following schematic representation, which shows how the AND condition is distributed to the second set of conditions:</span></span>  
  
```  
(A AND B) OR (A AND C)  
```  
  
 <span data-ttu-id="0fb53-126">분배 법칙은 쿼리 및 뷰 디자이너를 사용하는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-126">This distributive principle affects how you use the Query and View Designer.</span></span> <span data-ttu-id="0fb53-127">예를 들어, 직급이 낮거나 중간인 직원 중에서 근무 연수가 5년이 넘는 직원을 모두 찾는다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-127">For example, imagine that you are looking for all employees who have been with the company more than five years in either lower or middle-level jobs.</span></span> <span data-ttu-id="0fb53-128">SQL 창에서 다음 WHERE 절을 문에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-128">You enter the following WHERE clause into the statement in the SQL pane:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
 <span data-ttu-id="0fb53-129">AND로 연결된 절은 OR로 연결된 두 절에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-129">The clause linked with AND applies to both clauses linked with OR.</span></span> <span data-ttu-id="0fb53-130">OR 절에 있는 각 조건에 대해 AND 조건을 한 번씩 반복하면 이를 더 분명하게 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-130">An explicit way to express this is to repeat the AND condition once for each condition in the OR clause.</span></span> <span data-ttu-id="0fb53-131">다음 문은 앞의 문보다 더 분명하고 길지만 논리적으로는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-131">The following statement is more explicit (and longer) than the previous statement, but is logically equivalent to it:</span></span>  
  
```  
WHERE    (hire_date < '01/01/95' ) AND  
  (job_lvl = 100) OR   
  (hire_date < '01/01/95' ) AND   
  (job_lvl = 200)  
```  
  
 <span data-ttu-id="0fb53-132">AND 절을 연결된 OR절에 분배하는 원칙은 포함된 개별 조건의 수에 관계없이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-132">The principle of distributing AND clauses to linked OR clauses applies no matter how many individual conditions are involved.</span></span> <span data-ttu-id="0fb53-133">예를 들어, 근무 연수가 5년이 넘거나 현재 퇴직한 직원 중에서 직급이 높거나 중간인 직원을 찾는다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-133">For example, imagine that you want to find higher or middle-level employees who have been with the company more than five years or are retired.</span></span> <span data-ttu-id="0fb53-134">이 경우 WHERE 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-134">The WHERE clause might look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 OR job_lvl = 300) AND  
   (hire_date < '01/01/95' ) OR (status = 'R')  
```  
  
 <span data-ttu-id="0fb53-135">AND로 연결된 조건이 분배된 후 WHERE 절은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-135">After the conditions linked with AND have been distributed, the WHERE clause will look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 200 AND status = 'R') OR  
   (job_lvl = 300 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 300 AND status = 'R')   
```  
  
## <a name="how-multiple-and-and-or-clauses-are-represented-in-the-criteria-pane"></a><span data-ttu-id="0fb53-136">다수의 AND 절과 OR 절을 조건 창에 나타내는 방법</span><span class="sxs-lookup"><span data-stu-id="0fb53-136">How Multiple AND and OR Clauses Are Represented in the Criteria Pane</span></span>  
 <span data-ttu-id="0fb53-137">쿼리 및 뷰 디자이너는 검색 조건을 [조건 창](visual-database-tools.md)에 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-137">The Query and View Designer represents your search conditions in the [Criteria Pane](visual-database-tools.md).</span></span> <span data-ttu-id="0fb53-138">그러나 AND와 OR로 연결된 여러 개의 절을 포함하는 경우 조건 창에 나타내는 방법이 예상과 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-138">However, in some cases that involve multiple clauses linked with AND and OR, the representation in the Criteria Pane might not be what you expect.</span></span> <span data-ttu-id="0fb53-139">또한 조건 창이나 [다이어그램 창](diagram-pane-visual-database-tools.md)에서 쿼리를 수정하면 SQL 문이 입력한 것과 다르게 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-139">In addition, if you modify your query in the Criteria Pane or [Diagram Pane](diagram-pane-visual-database-tools.md), you might find that your SQL statement has been changed from what you entered.</span></span>  
  
 <span data-ttu-id="0fb53-140">일반적으로 다음 규칙에 따라 조건 창에서 AND 절과 OR 절이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-140">In general, these rules dictate how AND and OR clauses appear in the Criteria Pane:</span></span>  
  
-   <span data-ttu-id="0fb53-141">AND로 연결된 모든 조건은 표 형태의 **필터** 열 또는 동일한 **또는...** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-141">All conditions linked with AND appear in the **Filter** grid column or in the same **Or...** column.</span></span>  
  
-   <span data-ttu-id="0fb53-142">OR로 연결된 모든 조건은 별도의 **또는...** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-142">All conditions linked with OR appear in separate **Or...** columns.</span></span>  
  
-   <span data-ttu-id="0fb53-143">AND 및 OR 절 조합의 논리적 결과가 AND가 여러 개의 OR 절에 분배되는 것이면 조건 창은 AND 절을 필요한 만큼 반복하여 이것을 명시적으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-143">If the logical result of a combination of AND and OR clauses is that the AND is distributed into several OR clauses, the Criteria Pane represents this explicitly by repeating the AND clause as many times as necessary.</span></span>  
  
 <span data-ttu-id="0fb53-144">예를 들어, SQL 창에 다음과 같은 검색 조건을 만들 수 있습니다. 이 경우 AND로 연결된 두 절은 OR로 연결된 셋째 절보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-144">For example, in the SQL pane you might create a search condition such as the following, in which two clauses linked with AND take precedence over a third one linked with OR:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  (job_lvl = 100) OR   
  (status = 'R')  
```  
  
 <span data-ttu-id="0fb53-145">쿼리 및 뷰 디자이너는 아래와 같이 조건 창에 이 WHERE 문을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-145">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="0fb53-146">![조건 창의 OR 절 우선 순위](../../database-engine/media//vs-criteriapane1.gif "조건 창의 OR 절 우선 순위")</span><span class="sxs-lookup"><span data-stu-id="0fb53-146">![OR clause precedence in the Criteria Pane](../../database-engine/media//vs-criteriapane1.gif "OR clause precedence in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="0fb53-147">그러나 연결된 OR 절이 AND 절보다 우선 순위가 높으면 AND 절은 각 OR 절에 대해 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-147">However, if the linked OR clauses take precedence over an AND clause, the AND clause is repeated for each OR clause.</span></span> <span data-ttu-id="0fb53-148">이렇게 하면 AND 절이 각 OR 절에 분배됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-148">This causes the AND clause to be distributed to each OR clause.</span></span> <span data-ttu-id="0fb53-149">예를 들어, SQL 창에서 다음과 같은 WHERE 절을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-149">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ( (job_lvl = 100) OR   
  (status = 'R') )  
```  
  
 <span data-ttu-id="0fb53-150">쿼리 및 뷰 디자이너는 아래와 같이 조건 창에 이 WHERE 문을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-150">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="0fb53-151">![조건 창의 여러 AND 및 OR 절](../../database-engine/media//vs-criteriapane2.gif "조건 창의 여러 AND 및 OR 절")</span><span class="sxs-lookup"><span data-stu-id="0fb53-151">![Multiple AND and OR clauses in the Criteria Pane](../../database-engine/media//vs-criteriapane2.gif "Multiple AND and OR clauses in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="0fb53-152">연결된 OR 절에 데이터 열이 단 하나 포함되어 있는 경우 쿼리 및 뷰 디자이너는 AND 절을 반복할 필요가 없도록 전체 OR 절을 표 형태의 단일 셀에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-152">If the linked OR clauses involve only one data column, the Query and View Designer can place the entire OR clause into a single cell of the grid, avoiding the need to repeat the AND clause.</span></span> <span data-ttu-id="0fb53-153">예를 들어, SQL 창에서 다음과 같은 WHERE 절을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-153">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ((status = 'R') OR (status = 'A'))  
```  
  
 <span data-ttu-id="0fb53-154">쿼리 및 뷰 디자이너는 아래와 같이 조건 창에 이 WHERE 문을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-154">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="0fb53-155">![조건 창에 정의된 링크된 OR 절](../../database-engine/media//vs-criteriapane3.gif "조건 창에 정의된 링크된 OR 절")</span><span class="sxs-lookup"><span data-stu-id="0fb53-155">![Linked OR clauses defined in the Criteria Pane](../../database-engine/media//vs-criteriapane3.gif "Linked OR clauses defined in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="0fb53-156">쿼리를 변경하면(예: 조건 창에서 값 하나를 변경) 쿼리 및 뷰 디자이너는 SQL 창에 SQL 문을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-156">If you make a change to the query (such as changing one of the values in the Criteria Pane), the Query and View Designer recreates the SQL statement in the SQL pane.</span></span> <span data-ttu-id="0fb53-157">다시 만들어진 SQL 문은 원래 문보다는 조건 창에 표시되는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-157">The recreated SQL statement will resemble the Criteria Pane display rather than your original statement.</span></span> <span data-ttu-id="0fb53-158">예를 들어, 분배된 AND 절이 조건 창에 있는 경우 SQL 창에는 명시적으로 분배된 AND 절로 문이 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0fb53-158">For example, if the Criteria Pane contains distributed AND clauses, the resulting statement in the SQL pane will be recreated with explicit distributed AND clauses.</span></span> <span data-ttu-id="0fb53-159">자세한 내용은 이 항목의 앞부분에서 설명한 "OR 절이 여러 개 있는 경우 AND가 적용되는 방법"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0fb53-159">For details, see "How AND Works with Multiple OR Clauses" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb53-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fb53-160">See Also</span></span>  
 [<span data-ttu-id="0fb53-161">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="0fb53-161">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
