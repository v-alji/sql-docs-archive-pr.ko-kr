---
title: 행 포함 또는 제외(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- included rows
- search conditions [SQL Server], HAVING clause
- search criteria [SQL Server], including rows
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- search conditions [SQL Server], WHERE clause
- row included in search [SQL Server]
- excluding rows
ms.assetid: ba4e1202-31a2-444d-8365-c68a530ef223
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b2d31c51296fa73a503e59a14adb60d79a61178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651962"
---
# <a name="include-or-exclude-rows-visual-database-tools"></a><span data-ttu-id="97ef5-102">행 포함 또는 제외(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="97ef5-102">Include or Exclude Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="97ef5-103">선택 쿼리가 반환할 행 수를 제한하려면 검색 조건 또는 필터링 기준을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-103">To restrict the number of rows a SELECT query should return, you create search conditions or filter criteria.</span></span> <span data-ttu-id="97ef5-104">SQL에서 검색 조건은 문의 WHERE 절에 나타나거나 집계 쿼리를 만들 경우 HAVING 절에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-104">In SQL, search conditions appear in the WHERE clause of the statement, or if you are creating an aggregate query, in the HAVING clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97ef5-105">검색 조건을 사용하여 업데이트, 결과 삽입, 값 삽입, 삭제 또는 테이블 만들기 쿼리의 영향을 받는 행을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-105">You can also use search conditions to indicate which rows are affected by an Update, Insert Results, Insert Values, Delete, or Make Table query.</span></span>  
  
 <span data-ttu-id="97ef5-106">쿼리를 실행할 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 검색 조건을 검사하여 검색할 테이블의 각 행에 검색 조건을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-106">When the query runs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines and applies the search condition to each row in the tables you are searching.</span></span> <span data-ttu-id="97ef5-107">행이 검색 조건에 맞으면 쿼리에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-107">If the row meets the condition, it is included in the query.</span></span> <span data-ttu-id="97ef5-108">예를 들어, 특정 지역에 있는 직원들을 모두 찾는 검색 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-108">For example, a search condition that would find all the employees in a particular region might be:</span></span>  
  
```  
region = 'UK'  
```  
  
 <span data-ttu-id="97ef5-109">여러 검색 조건을 사용하여 결과에 행을 포함시키는 기준을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-109">To establish the criteria for including a row in a result, you can use multiple search conditions.</span></span> <span data-ttu-id="97ef5-110">예를 들어, 다음 검색 조건은 두 개의 검색 조건으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-110">For example, the following search criterion consists of two search conditions.</span></span> <span data-ttu-id="97ef5-111">쿼리는 행이 두 조건을 모두 충족하는 경우에만 해당 행을 결과 집합에 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-111">The query includes a row in the result set only if that row satisfies both of the conditions.</span></span>  
  
```  
region = 'UK' AND product_line = 'Housewares'  
```  
  
 <span data-ttu-id="97ef5-112">이러한 조건을 AND 또는 OR를 사용하여 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-112">You can combine these conditions with AND or OR.</span></span> <span data-ttu-id="97ef5-113">위의 예에서는 AND를 사용하였으며</span><span class="sxs-lookup"><span data-stu-id="97ef5-113">The previous example uses AND.</span></span> <span data-ttu-id="97ef5-114">반대로 아래 조건에서는 OR를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-114">In contrast, the following criterion uses OR.</span></span> <span data-ttu-id="97ef5-115">결과 집합에는 검색 조건 중 한 개 또는 두 개를 모두 충족하는 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-115">The result set will include any row that satisfies either or both of the search conditions:</span></span>  
  
```  
region = 'UK' OR product_line = 'Housewares'  
```  
  
 <span data-ttu-id="97ef5-116">검색 조건을 단일 열에 결합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-116">You can even combine search conditions on a single column.</span></span> <span data-ttu-id="97ef5-117">예를 들어, 다음 조건은 region 열에 두 개의 조건을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-117">For example, the following criterion combines two conditions on the region column:</span></span>  
  
```  
region = 'UK' OR region = 'US'  
```  
  
 <span data-ttu-id="97ef5-118">검색 조건 결합에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="97ef5-118">For details about combining search conditions, see the following topics:</span></span>  
  
-   [<span data-ttu-id="97ef5-119">조건 창의 검색 조건 결합 규칙&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-119">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
  
-   [<span data-ttu-id="97ef5-120">한 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-120">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
-   [<span data-ttu-id="97ef5-121">여러 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-121">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
  
-   [<span data-ttu-id="97ef5-122">AND에 우선 순위가 있는 조건 조합&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-122">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
  
-   [<span data-ttu-id="97ef5-123">OR에 우선 순위가 있는 조건 조합&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-123">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
  
## <a name="examples"></a><span data-ttu-id="97ef5-124">예</span><span class="sxs-lookup"><span data-stu-id="97ef5-124">Examples</span></span>  
 <span data-ttu-id="97ef5-125">다음은 여러 가지 연산자와 행 조건을 사용한 쿼리의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-125">Here are some examples of queries using various operators and row criteria:</span></span>  
  
-   <span data-ttu-id="97ef5-126">**리터럴** 단일 텍스트, 숫자, 날짜 또는 논리 값입니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-126">**Literal** A single text, numeric, date, or logical value.</span></span> <span data-ttu-id="97ef5-127">아래 예에서는 리터럴을 사용하여 영국에 있는 직원에 대한 행을 모두 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-127">The following example uses a literal to find all rows for employees in the United Kingdom:</span></span>  
  
    ```  
    WHERE region = 'UK'  
    ```  
  
-   <span data-ttu-id="97ef5-128">**열 참조** 한 열의 값을 다른 열의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-128">**Column reference** Compares the values in one column with the values in another.</span></span> <span data-ttu-id="97ef5-129">아래 예에서는 `products` 테이블을 검색하여 운반 비용보다 생산 비용이 싼 행을 모두 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-129">The following example searches a `products` table for all rows in which the value of the production cost is lower than the shipping cost:</span></span>  
  
    ```  
    WHERE prod_cost < ship_cost  
    ```  
  
-   <span data-ttu-id="97ef5-130">**함수** 검색할 값을 계산하기 위해 데이터베이스 백 엔드가 사용할 수 있는 함수에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-130">**Function** A reference to a function that the database back-end can resolve to calculate a value for the search.</span></span> <span data-ttu-id="97ef5-131">함수는 데이터베이스 서버에서 정의한 함수 또는 스칼라 값을 반환하는 사용자 정의 함수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-131">The function can be a function defined by the database server or a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="97ef5-132">아래 예에서는 오늘 받은 주문을 검색하며 GETDATE( ) 함수는 현재 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-132">The following example searches for orders placed today (the GETDATE( ) function returns the current date):</span></span>  
  
    ```  
    WHERE order_date = GETDATE()  
    ```  
  
-   <span data-ttu-id="97ef5-133">**NULL** 아래 예에서는 `authors` 테이블을 검색하여 파일에 이름이 있는 모든 작성자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-133">**NULL** The following example searches an `authors` table for all authors who have a first name on file:</span></span>  
  
    ```  
    WHERE au_fname IS NOT NULL  
    ```  
  
-   <span data-ttu-id="97ef5-134">**계산** 리터럴, 열 참조 또는 다른 식을 포함할 수 있는 계산 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-134">**Calculation** The result of a calculation that can involve literals, column references, or other expressions.</span></span> <span data-ttu-id="97ef5-135">아래 예에서는 `products` 테이블을 검색하여 소매 가격이 생산 비용의 2배 이상인 행을 모두 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97ef5-135">The following example searches a `products` table to find all rows in which the retail sales price is more than twice the production cost:</span></span>  
  
    ```  
    WHERE sales_price > (prod_cost * 2)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97ef5-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97ef5-136">See Also</span></span>  
 <span data-ttu-id="97ef5-137">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="97ef5-137">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="97ef5-138">[Visual Database Tools &#40;검색 조건을 지정&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="97ef5-138">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="97ef5-139">매개 변수를 사용하여 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97ef5-139">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
