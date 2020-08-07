---
title: AND에 우선 순위가 있는 조건 조합(Visual Database Tools) | Microsoft 문서
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
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 917d5381bc83083ee1fa3c07375945c0908da521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727808"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a><span data-ttu-id="fda7b-102">AND에 우선 순위가 있는 조건 조합(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fda7b-102">Combine Conditions When AND Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="fda7b-103">AND를 사용하여 조건을 조합하려면 각 조건에 한 번씩, 즉 쿼리에 열을 두 번 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-103">To combine conditions with AND, you add the column to the query twice--once for each condition.</span></span> <span data-ttu-id="fda7b-104">조건을 OR와 조합하려면 첫째 조건은 필터 열에 지정하고 추가 조건은 **또는...** 열에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-104">To combine conditions with OR, you put the first one in the Filter column and additional conditions into an **Or...** column.</span></span>  
  
 <span data-ttu-id="fda7b-105">예를 들어, 근무 연수가 5년이 넘으면서 직급이 낮은 직원과 고용 날짜에 상관 없이 중간 직급인 직원을 찾는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-105">For example, imagine that you want to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs regardless of their hire date.</span></span> <span data-ttu-id="fda7b-106">이 쿼리에는 세 개의 조건이 필요하며 그 중 두 조건은 AND로 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-106">This query requires three conditions, two of them linked with AND:</span></span>  
  
-   <span data-ttu-id="fda7b-107">근무 연수가 5년이 넘으면서 직급이 100인 직원</span><span class="sxs-lookup"><span data-stu-id="fda7b-107">Employees with a hire date earlier than five years ago AND with a job level of 100.</span></span>  
  
     <span data-ttu-id="fda7b-108">또는</span><span class="sxs-lookup"><span data-stu-id="fda7b-108">-or-</span></span>  
  
-   <span data-ttu-id="fda7b-109">직급이 200인 직원</span><span class="sxs-lookup"><span data-stu-id="fda7b-109">Employees with a job level of 200.</span></span>  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a><span data-ttu-id="fda7b-110">AND에 우선 순위가 있는 경우 조건을 조합하려면</span><span class="sxs-lookup"><span data-stu-id="fda7b-110">To combine conditions when AND has precedence</span></span>  
  
1.  <span data-ttu-id="fda7b-111">[조건 창](visual-database-tools.md)에서 검색할 데이터 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-111">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="fda7b-112">AND로 연결된 둘 이상의 조건을 사용하여 동일한 열을 검색하려면 검색할 각 값에 대하여 한 번씩 데이터 열 이름을 표에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-112">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="fda7b-113">**필터** 열에 AND로 연결할 모든 조건을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-113">In the **Filter** column, enter all the conditions that you want to link with AND.</span></span> <span data-ttu-id="fda7b-114">예를 들어, `hire_date` 열과 `job_lvl` 열을 검색하는 조건을 AND로 연결하려면 필터 열에 각각 `< '1/1/91'` 값과 `= 100`값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-114">For example, to link conditions with AND that search the `hire_date` and `job_lvl` columns, enter the values `< '1/1/91'` and `= 100`, respectively, in the Filter column.</span></span>  
  
     <span data-ttu-id="fda7b-115">이런 표 형태 엔트리는 [SQL 창](sql-pane-visual-database-tools.md)에서 문에 다음과 같은 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-115">These grid entries produce the following WHERE clause in the statement in the [SQL Pane](sql-pane-visual-database-tools.md):</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  <span data-ttu-id="fda7b-116">표 형태의 **또는...** 열에 OR로 연결할 조건을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-116">In the **Or...** grid column, enter conditions that you want to link with OR.</span></span> <span data-ttu-id="fda7b-117">예를 들어 `job_lvl` 열에서 다른 값을 검색하는 조건을 추가하려면 **또는...** 열에 다른 값(예: `= 200`)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-117">For example, to add a condition that searches for another value in the `job_lvl` column, enter an additional value in the **Or...** column, such as `= 200`.</span></span>  
  
     <span data-ttu-id="fda7b-118">**또는...** 열에 값을 추가하면 SQL 창에 있는 문의 WHERE 절에 또 다른 조건이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fda7b-118">Adding a value in the **Or...** column adds another condition to the WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fda7b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fda7b-119">See Also</span></span>  
 <span data-ttu-id="fda7b-120">[OR에 우선 순위가 있는 조건을 조합 하 여 Visual Database Tools &#40;&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fda7b-120">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="fda7b-121">[조건 창에서 검색 조건을 결합 하는 규칙 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fda7b-121">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 <span data-ttu-id="fda7b-122">[Visual Database Tools&#41;&#40;검색 값을 입력 하는 규칙](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fda7b-122">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="fda7b-123">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fda7b-123">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
