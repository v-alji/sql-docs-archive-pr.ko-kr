---
title: 한 열에 여러 검색 조건 지정 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a07322120bd3b3f543e6f54fa50cdf75aa32be59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650350"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a><span data-ttu-id="074d8-102">한 열에 여러 검색 조건 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="074d8-102">Specify Multiple Search Conditions for One Column (Visual Database Tools)</span></span>
  <span data-ttu-id="074d8-103">동일한 데이터 열에 여러 개의 검색 조건을 적용해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-103">In some instances, you might want to apply a number of search conditions to the same data column.</span></span> <span data-ttu-id="074d8-104">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="074d8-105">`employee` 테이블에서 여러 개의 다른 이름을 검색하는 경우 또는 급여가 서로 다른 직원을 검색하는 경우.</span><span class="sxs-lookup"><span data-stu-id="074d8-105">Search for several different names in an `employee` table or for employees who are in different salary ranges.</span></span> <span data-ttu-id="074d8-106">이런 형식의 검색에는 OR 조건이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-106">This type of search requires an OR condition.</span></span>  
  
-   <span data-ttu-id="074d8-107">"The"로 시작하며 "Cook"이라는 단어를 포함하는 책 제목을 검색하는 경우.</span><span class="sxs-lookup"><span data-stu-id="074d8-107">Search for a book title that both starts with the word "The" and contains the word "Cook."</span></span> <span data-ttu-id="074d8-108">이런 형식의 검색에는 AND 조건이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-108">This type of search requires an AND condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="074d8-109">이 항목의 정보는 쿼리에서 WHERE 절의 검색 조건과 HAVING 절의 검색 조건에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-109">The information in this topic applies to search conditions in both the WHERE and HAVING clauses of a query.</span></span> <span data-ttu-id="074d8-110">이 예제는 WHERE 절 만들기를 중점적으로 설명하지만 이 원칙은 두 형식의 검색 조건 모두에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-110">The examples focus on creating WHERE clauses, but the principles apply to both types of search conditions.</span></span>  
  
 <span data-ttu-id="074d8-111">동일한 데이터 열에서 하나의 조건만 만족해도 되는 값을 검색하려면 OR 조건을 지정하고</span><span class="sxs-lookup"><span data-stu-id="074d8-111">To search for alternative values in the same data column, you specify an OR condition.</span></span> <span data-ttu-id="074d8-112">여러 조건을 모두 만족하는 값을 검색하려면 AND 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-112">To search for values that meet several conditions, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="074d8-113">OR 조건 지정</span><span class="sxs-lookup"><span data-stu-id="074d8-113">Specifying an OR Condition</span></span>  
 <span data-ttu-id="074d8-114">OR 조건을 사용하면 하나의 열에 검색할 조건 값을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-114">Using an OR condition enables you to specify several alternative values to search for in a column.</span></span> <span data-ttu-id="074d8-115">이 옵션은 검색 범위를 넓히므로 단일 값을 검색하는 것보다 많은 행을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-115">This option expands the scope of the search and can return more rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="074d8-116">IN 연산자를 대신 사용하여 동일한 데이터 열에서 여러 개의 값을 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-116">You can often use the IN operator instead to search for multiple values in the same data column.</span></span>  
  
#### <a name="to-specify-an-or-condition"></a><span data-ttu-id="074d8-117">OR 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="074d8-117">To specify an OR condition</span></span>  
  
1.  <span data-ttu-id="074d8-118">[조건 창](visual-database-tools.md)에서 검색할 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-118">In the [Criteria Pane](visual-database-tools.md), add the column to search.</span></span>  
  
2.  <span data-ttu-id="074d8-119">방금 추가한 데이터 열의 **필터** 열에 첫째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-119">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="074d8-120">동일한 데이터 열의 **또는...** 열에 둘째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-120">In the **Or...** column for the same data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="074d8-121">쿼리 및 뷰 디자이너는 다음과 같이 OR 조건을 포함하는 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-121">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="074d8-122">AND 조건 지정</span><span class="sxs-lookup"><span data-stu-id="074d8-122">Specifying an AND Condition</span></span>  
 <span data-ttu-id="074d8-123">AND 조건을 사용하면 열에 있는 값 중 둘 이상의 조건을 모두 만족하는 행 값만 결과 집합에 포함되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-123">Using an AND condition enables you to specify that values in a column must meet two (or more) conditions for the row to be included in the result set.</span></span> <span data-ttu-id="074d8-124">이 옵션은 검색 범위를 좁히므로 일반적으로 단일 값을 검색하는 것보다 적은 수의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-124">This option narrows the scope of the search and usually returns fewer rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="074d8-125">값 범위를 검색 중인 경우 AND를 사용하여 두 조건을 연결하는 대신 BETWEEN 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-125">If you are searching for a range of values, you can use the BETWEEN operator instead of linking two conditions with AND.</span></span>  
  
#### <a name="to-specify-an-and-condition"></a><span data-ttu-id="074d8-126">AND 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="074d8-126">To specify an AND condition</span></span>  
  
1.  <span data-ttu-id="074d8-127">조건 창에서 검색할 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-127">In the Criteria pane, add the column to search.</span></span>  
  
2.  <span data-ttu-id="074d8-128">방금 추가한 데이터 열의 **필터** 열에 첫째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-128">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="074d8-129">동일한 데이터 열을 조건 창에 다시 추가하여 표의 빈 행에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-129">Add the same data column to the Criteria pane again, placing it in an empty row of the grid.</span></span>  
  
4.  <span data-ttu-id="074d8-130">데이터 열의 두 번째 인스턴스에 대한 **필터** 열에 둘째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-130">In the **Filter** column for the second instance of the data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="074d8-131">쿼리 디자이너는 다음과 같이 AND 조건을 포함하는 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-131">The Query Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a><span data-ttu-id="074d8-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="074d8-132">See Also</span></span>  
 <span data-ttu-id="074d8-133">[조건 창에서 검색 조건을 결합 하는 규칙 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="074d8-133">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="074d8-134">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="074d8-134">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
