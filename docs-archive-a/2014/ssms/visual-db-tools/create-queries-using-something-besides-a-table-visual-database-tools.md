---
title: 테이블 외의 항목을 사용 하 여 쿼리 만들기 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], queries
- queries [SQL Server], creating
ms.assetid: 8e4a1f0a-8a42-4733-be8d-e21d6dbddb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0444c20fe10080949930f23623d5699f7fd3712c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639210"
---
# <a name="create-queries-using-something-besides-a-table-visual-database-tools"></a><span data-ttu-id="ac244-102">테이블 외의 항목을 사용하여 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ac244-102">Create Queries using Something Besides a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="ac244-103">검색 쿼리를 작성할 때마다 원하는 열과 행, 쿼리 프로세서가 원래 데이터를 찾는 위치 등을 분명히 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-103">Whenever you write a retrieval query, you articulate what columns you want, what rows you want, and where the query processor should find the original data.</span></span> <span data-ttu-id="ac244-104">일반적으로 이 원래 데이터는 하나의 테이블 또는 함께 조인된 여러 테이블로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-104">Typically, this original data consists of a table or several tables joined together.</span></span> <span data-ttu-id="ac244-105">그러나 원래 데이터를 테이블 이외의 원본에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-105">But the original data can come from sources other than tables.</span></span> <span data-ttu-id="ac244-106">실제로 테이블을 반환하는 사용자 정의 함수나 뷰, 쿼리 또는 동의어에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-106">In fact, it can come from views, queries, synonyms, or user-defined functions that return a table.</span></span>  
  
## <a name="using-a-view-in-place-of-a-table"></a><span data-ttu-id="ac244-107">테이블 대신 뷰 사용</span><span class="sxs-lookup"><span data-stu-id="ac244-107">Using a View in Place of a Table</span></span>  
 <span data-ttu-id="ac244-108">뷰에서 행을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-108">You can select rows from a view.</span></span> <span data-ttu-id="ac244-109">예를 들어, 각 행에 가격이 $19.99가 넘는 책의 제목을 나타내는 "ExpensiveBooks"라는 뷰가 데이터베이스에 포함되어 있다고 가정하는 경우</span><span class="sxs-lookup"><span data-stu-id="ac244-109">For example, suppose the database includes a view called "ExpensiveBooks," in which each row describes a title whose price exceeds 19.99.</span></span> <span data-ttu-id="ac244-110">뷰 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-110">The view definition might look like this:</span></span>  
  
```  
SELECT *  
FROM titles  
WHERE price > 19.99  
  
```  
  
 <span data-ttu-id="ac244-111">ExpensiveBooks 뷰에서 심리학 책을 선택하면 가격이 비싼 심리학 책을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-111">You can select the expensive psychology books merely by selecting the psychology books from the ExpensiveBooks view.</span></span> <span data-ttu-id="ac244-112">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-112">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM ExpensiveBooks  
WHERE type = 'psychology'  
  
```  
  
 <span data-ttu-id="ac244-113">이와 마찬가지로 뷰가 JOIN 연산에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-113">Similarly, a view can participate in a JOIN operation.</span></span> <span data-ttu-id="ac244-114">예를 들어, ExpensiveBooks 뷰에 sales 테이블을 조인하면 판매되고 있는 비싼 책을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-114">For example, you can find the sales of expensive books merely by joining the sales table to the ExpensiveBooks view.</span></span> <span data-ttu-id="ac244-115">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-115">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM sales   
         INNER JOIN   
         ExpensiveBooks   
         ON sales.title_id   
         =  ExpensiveBooks.title_id  
  
```  
  
 <span data-ttu-id="ac244-116">쿼리에 뷰를 추가하는 방법에 대한 자세한 내용은 [쿼리에 테이블 추가&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac244-116">For more information about adding a view to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-query-in-place-of-a-table"></a><span data-ttu-id="ac244-117">테이블 대신 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="ac244-117">Using a Query in Place of a Table</span></span>  
 <span data-ttu-id="ac244-118">쿼리에서 행을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-118">You can select rows from a query.</span></span> <span data-ttu-id="ac244-119">예를 들어 공동으로 저술한 책(저자가 두 명 이상인 경우)의 제목과 ID를 검색하는 쿼리를 이미 작성했다고 가정하면</span><span class="sxs-lookup"><span data-stu-id="ac244-119">For example, suppose you have already written a query retrieving titles and identifiers of the coauthored books - the books with more than one author.</span></span> <span data-ttu-id="ac244-120">SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-120">The SQL might look like this:</span></span>  
  
```  
SELECT   
     titles.title_id, title, type  
FROM   
     titleauthor   
         INNER JOIN  
         titles   
         ON titleauthor.title_id   
         =  titles.title_id   
GROUP BY   
     titles.title_id, title, type  
HAVING COUNT(*) > 1  
  
```  
  
 <span data-ttu-id="ac244-121">그런 다음 이 결과에 작성되는 다른 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-121">You can then write another query that builds on this result.</span></span> <span data-ttu-id="ac244-122">예를 들어, 공동으로 저술한 심리학 책을 검색하는 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-122">For example, you can write a query that retrieves the coauthored psychology books.</span></span> <span data-ttu-id="ac244-123">이 새 쿼리를 작성하기 위해 기존 쿼리를 새 쿼리 데이터의 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-123">To write this new query, you can use the existing query as the source of the new query's data.</span></span> <span data-ttu-id="ac244-124">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-124">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    title  
FROM   
    (  
    SELECT   
        titles.title_id,   
        title,   
        type  
    FROM   
        titleauthor   
            INNER JOIN  
            titles   
            ON titleauthor.title_id   
            =  titles.title_id   
    GROUP BY   
        titles.title_id,   
        title,   
        type  
    HAVING COUNT(*) > 1  
    )   
    co_authored_books  
WHERE     type = 'psychology'  
  
```  
  
 <span data-ttu-id="ac244-125">강조 표시한 텍스트는 새 쿼리 데이터의 원본으로 사용하는 기존 쿼리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-125">The emphasized text shows the existing query used as the source of the new query's data.</span></span> <span data-ttu-id="ac244-126">새 쿼리에서는 기존 쿼리의 별칭("co_authored_books")을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-126">Note that the new query uses an alias ("co_authored_books") for the existing query.</span></span> <span data-ttu-id="ac244-127">별칭에 대한 자세한 내용은 [테이블 별칭 만들기&#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) 및 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac244-127">For more information about aliases, see [Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) and [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="ac244-128">마찬가지로 쿼리가 JOIN 연산에 참여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-128">Similarly, a query can participate in a JOIN operation.</span></span> <span data-ttu-id="ac244-129">예를 들어, ExpensiveBooks 뷰를 공동으로 저술한 책을 검색하는 쿼리에 조인하기만 하면 판매 중인 가격이 비싼 공동으로 저술한 책을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-129">For example, you can find the sales of expensive coauthored books merely by joining the ExpensiveBooks view to the query retrieving the coauthored books.</span></span> <span data-ttu-id="ac244-130">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-130">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    ExpensiveBooks.title  
FROM   
    ExpensiveBooks   
        INNER JOIN  
        (  
        SELECT   
            titles.title_id,   
            title,   
            type  
        FROM   
            titleauthor   
                INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
        GROUP BY   
            titles.title_id,   
            title,   
            type  
        HAVING COUNT(*) > 1  
        )  
```  
  
 <span data-ttu-id="ac244-131">쿼리에 쿼리를 추가하는 방법에 대한 자세한 내용은 [쿼리에 테이블 추가&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac244-131">For more information about adding a query to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-user-defined-function-in-place-of-a-table"></a><span data-ttu-id="ac244-132">테이블 대신 사용자 정의 함수 사용</span><span class="sxs-lookup"><span data-stu-id="ac244-132">Using a User-Defined Function in Place of a Table</span></span>  
 <span data-ttu-id="ac244-133">SQL Server 2000 이상에서는 테이블을 반환하는 사용자 정의 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-133">In SQL Server 2000 or higher, you can create a user-defined function that returns a table.</span></span> <span data-ttu-id="ac244-134">이러한 함수는 복잡하거나 절차적인 논리를 수행하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-134">Such functions are useful for performing complex or procedural logic.</span></span>  
  
 <span data-ttu-id="ac244-135">예를 들어, employee 테이블에 employee.manager_emp_id 추가 열이 있고 외래 키가 manager_emp_id 열에서 employee.emp_id 열까지 존재한다고 가정하면</span><span class="sxs-lookup"><span data-stu-id="ac244-135">For example, suppose the employee table contains an additional column, employee.manager_emp_id, and that a foreign key exists from manager_emp_id to employee.emp_id.</span></span> <span data-ttu-id="ac244-136">employee 테이블의 각 행에서 manager_emp_id 열은 직원의 상사를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-136">Within each row of the employee table, the manager_emp_id column indicates the employee's boss.</span></span> <span data-ttu-id="ac244-137">정확하게 말하자면 직원 상사의 emp_id를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-137">More precisely, it indicates the employee's boss's emp_id.</span></span> <span data-ttu-id="ac244-138">높은 수준의 특정 관리자 조직 계층 내에서 작업하는 각 직원의 행을 포함하는 테이블을 반환하는 사용자 정의 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-138">You can create a user-defined function that returns a table containing one row for each employee working within a particular high-level manager's organizational hierarchy.</span></span> <span data-ttu-id="ac244-139">이 함수 이름을 fn_GetWholeTeam이라 하고 검색하려는 팀의 관리자의 emp_id, 즉 입력 변수를 가져오도록 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-139">You might call the function fn_GetWholeTeam, and design it to take an input variable - the emp_id of the manager whose team you want to retrieve.</span></span>  
  
 <span data-ttu-id="ac244-140">fn_GetWholeTeam 함수를 데이터 원본으로 사용하는 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-140">You can write a query that uses the fn_GetWholeTeam function as a source of data.</span></span> <span data-ttu-id="ac244-141">결과 SQL은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-141">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *   
FROM   
     fn_GetWholeTeam ('VPA30890F')  
  
```  
  
 <span data-ttu-id="ac244-142">"VPA30890F"는 검색하려는 조직의 관리자의 emp_id입니다.</span><span class="sxs-lookup"><span data-stu-id="ac244-142">"VPA30890F" is the emp_id of the manager whose organization you want to retrieve.</span></span> <span data-ttu-id="ac244-143">쿼리에 사용자 정의 함수를 추가하는 방법에 대한 자세한 내용은 [쿼리에 테이블 추가&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac244-143">For more information about adding a user-defined function to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="ac244-144">사용자 정의 함수에 대한 자세한 내용은 [사용자 정의 함수](../../relational-databases/user-defined-functions/user-defined-functions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ac244-144">For a complete description of user-defined functions, see [User-Defined Functions](../../relational-databases/user-defined-functions/user-defined-functions.md).</span></span>  
  
  
