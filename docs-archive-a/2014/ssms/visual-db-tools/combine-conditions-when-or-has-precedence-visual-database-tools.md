---
title: OR에 우선 순위가 있는 조건 조합(Visual Database Tools) | Microsoft 문서
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
- OR operator
ms.assetid: b30f5ac9-25e7-4163-80ed-44e4bccb455d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8be0d2f783c28662eb01f6bf191dc24d339534f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727803"
---
# <a name="combine-conditions-when-or-has-precedence-visual-database-tools"></a><span data-ttu-id="9d73b-102">OR에 우선 순위가 있는 조건 조합(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9d73b-102">Combine Conditions When OR Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="9d73b-103">조건을 OR로 연결하고 AND로 연결된 조건보다 높은 우선 순위를 부여하려면 각 OR 조건에 대하여 AND 조건을 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-103">To link conditions with OR and give them precedence over conditions linked with AND, you must repeat the AND condition for each OR condition.</span></span>  
  
 <span data-ttu-id="9d73b-104">예를 들어, 근무 연수가 5년이 넘는 직원 중 직급이 낮거나 퇴직한 직원을 모두 찾는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-104">For example, imagine that you want to find all employees who have been with the company more than five years and have lower-level jobs or are retired.</span></span> <span data-ttu-id="9d73b-105">이 쿼리에는 세 개의 조건이 필요하며 하나의 조건이 두 개의 추가 조건과 AND로 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-105">This query requires three conditions, a single condition linked to two additional conditions with AND:</span></span>  
  
-   <span data-ttu-id="9d73b-106">근무 연수가 5년이 넘는 직원</span><span class="sxs-lookup"><span data-stu-id="9d73b-106">Employees with a hire date earlier than five years ago, and</span></span>  
  
-   <span data-ttu-id="9d73b-107">직급이 100이거나 상태가 "R"(퇴직)인 직원</span><span class="sxs-lookup"><span data-stu-id="9d73b-107">Employees with a job level of 100 or whose status is "R" (for retired).</span></span>  
  
 <span data-ttu-id="9d73b-108">다음 절차는 조건 창에서 이런 형식의 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-108">The following procedure illustrates how to create this type of query in the Criteria pane.</span></span>  
  
### <a name="to-combine-conditions-when-or-has-precedence"></a><span data-ttu-id="9d73b-109">OR에 우선 순위가 있는 경우 조건을 조합하려면</span><span class="sxs-lookup"><span data-stu-id="9d73b-109">To combine conditions when OR has precedence</span></span>  
  
1.  <span data-ttu-id="9d73b-110">[조건 창](visual-database-tools.md)에서 검색할 데이터 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-110">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="9d73b-111">AND로 연결된 둘 이상의 조건을 사용하여 동일한 열을 검색하려면 검색할 각 값에 대하여 한 번씩 데이터 열 이름을 표에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-111">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="9d73b-112">첫째 조건은 표 형태의 **필터** 열에 입력하고 둘째 및 이후의 조건은 별도의 **또는...** 열에 입력하여 OR로 연결할 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-112">Create the conditions to be linked with OR by entering the first one into the **Filter** grid column and the second (and subsequent ones) into separate **Or...** columns.</span></span> <span data-ttu-id="9d73b-113">예를 들어 `job_lvl` 열과 `status` 열을 검색하는 조건을 OR로 연결하려면 `= 100` 의 **필터** 열에는 `job_lvl` 을 입력하고 `= 'R'` 의 **또는...** 열에는 `status`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-113">For example, to link conditions with OR that search the `job_lvl` and `status` columns, enter `= 100` in the **Filter** column for `job_lvl` and `= 'R'` in the **Or...** column for `status`.</span></span>  
  
     <span data-ttu-id="9d73b-114">표 형태로 된 값을 입력하면 SQL 창의 문에 다음과 같은 WHERE 절이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-114">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) OR (status = 'R')  
    ```  
  
3.  <span data-ttu-id="9d73b-115">각 OR 조건에 대해 한 번씩 입력하여 AND 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-115">Create the AND condition by entering it once for each OR condition.</span></span> <span data-ttu-id="9d73b-116">해당 OR 조건과 동일한 표 형태 열에 각 엔트리를 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-116">Place each entry in the same grid column as the OR condition it corresponds to.</span></span> <span data-ttu-id="9d73b-117">예를 들어 `hire_date` 열을 검색하여 두 개의 OR 조건에 적용하는 AND 조건을 추가하려면 조건 열과 `< '1/1/91'` 또는... **열에 둘 다** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-117">For example, to add an AND condition that searches the `hire_date` column and applies to both OR conditions, enter `< '1/1/91'` in both the Criteria column and the **Or...** column.</span></span>  
  
     <span data-ttu-id="9d73b-118">표 형태로 된 값을 입력하면 SQL 창의 문에 다음과 같은 WHERE 절이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-118">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) AND   
      (hire_date < '01/01/91' ) OR  
      (status = 'R') AND   
      (hire_date < '01/01/91' )  
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="9d73b-119">AND 조건을 반복하려면 한 번 추가한 다음 **편집** 메뉴에서 **잘라내기** 와 **붙여넣기** 명령을 사용하여 다른 OR 조건에 대해 반복하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-119">You can repeat an AND condition by adding it once, and then using the **Cut** and **Paste** commands from the **Edit** menu to repeat it for other OR conditions.</span></span>  
  
 <span data-ttu-id="9d73b-120">쿼리 및 뷰 디자이너에서 만든 WHERE 절은 괄호를 사용하여 OR의 우선 순위를 AND의 우선 순위보다 높게 지정한 다음의 WHERE 절과 동등합니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-120">The WHERE clause created by the Query and View Designer is equivalent to the following WHERE clause, which uses parentheses to specify the precedence of OR over AND:</span></span>  
  
```  
WHERE (job_lvl = 100 OR status = 'R') AND  
   (hire_date < '01/01/91')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9d73b-121">[SQL 창](sql-pane-visual-database-tools.md)에서 위에 표시된 형식으로 검색 조건을 입력한 다음 다이어그램 창이나 조건 창에서 쿼리를 변경하면 쿼리 및 뷰 디자이너는 두 OR 조건 모두에 명시적으로 배포된 AND 조건과 형식이 일치하는 SQL 문을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d73b-121">If you enter the search conditions in the format shown immediately above in the [SQL Pane](sql-pane-visual-database-tools.md), but then make a change to the query in the Diagram or Criteria panes, the Query and View Designer recreates the SQL statement to match the form with the AND condition explicitly distributed to both OR conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d73b-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d73b-122">See Also</span></span>  
 <span data-ttu-id="9d73b-123">[조건 창에서 검색 조건을 결합 하는 규칙 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9d73b-123">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="9d73b-124">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="9d73b-124">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
