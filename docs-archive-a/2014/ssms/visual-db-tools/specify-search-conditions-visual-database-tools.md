---
title: 검색 조건 지정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa5dab8326de079c385a3a508bc1b01b1ee1247d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650348"
---
# <a name="specify-search-conditions-visual-database-tools"></a><span data-ttu-id="b759a-102">검색 조건 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b759a-102">Specify Search Conditions (Visual Database Tools)</span></span>
  <span data-ttu-id="b759a-103">검색 조건을 지정하여 쿼리에 표시할 데이터 행을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-103">You can specify the data rows that appear in your query by specifying search conditions.</span></span> <span data-ttu-id="b759a-104">예를 들어 `employee` 테이블을 쿼리 중인 경우 특정 지역에 근무하는 직원만 찾도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-104">For example, if you are querying an `employee` table, you can specify that you want to find only the employees who work in a particular region.</span></span>  
  
 <span data-ttu-id="b759a-105">식을 사용하여 검색 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-105">You specify search conditions using an expression.</span></span> <span data-ttu-id="b759a-106">가장 일반적으로 사용하는 식은 연산자와 검색 값으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-106">Most commonly the expression consists of an operator and a search value.</span></span> <span data-ttu-id="b759a-107">예를 들어 특정 영업 지역에 근무하는 직원을 찾으려면 `region` 열에 다음 검색 조건을 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-107">For example, to find employees in a particular sales region, you might specify the following search criterion for the `region` column:</span></span>  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="b759a-108">여러 테이블을 사용하여 작업 중인 경우 쿼리 및 뷰 디자이너는 각 검색 조건을 검사하여 사용자가 만든 비교를 조인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-108">If you are working with multiple tables, the Query and View Designer examines each search condition to determine whether the comparison you are making results in a join.</span></span> <span data-ttu-id="b759a-109">조인하도록 결정하면 쿼리 및 뷰 디자이너가 검색 조건을 조인으로 자동 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-109">If so, the Query and View Designer automatically converts the search condition into a join.</span></span> <span data-ttu-id="b759a-110">자세한 내용은 [테이블 자동 조인&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b759a-110">For more information, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-specify-search-conditions"></a><span data-ttu-id="b759a-111">검색 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="b759a-111">To specify search conditions</span></span>  
  
1.  <span data-ttu-id="b759a-112">검색 조건 내에 사용할 열이나 식을 조건 창에 아직 추가하지 않았다면 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-112">If you have not done so already, add the columns or expressions that you want to use within your search condition to the Criteria pane.</span></span>  
  
     <span data-ttu-id="b759a-113">선택 쿼리를 만드는 중이며 쿼리 결과에 검색 열이나 식을 표시하지 않으려면 각 검색 열이나 식에 대해 **출력** 열의 선택을 취소하여 출력 열에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-113">If you are creating a Select query and do not want the search columns or expressions to appear in the query output, clear the **Output** column for each search column or expression to remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="b759a-114">검색할 데이터 열이나 식을 포함하는 행을 찾은 다음 **필터** 열에 검색 조건을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-114">Locate the row containing the data column or expression to search, and then in the **Filter** column, enter a search condition.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b759a-115">연산자를 입력하지 않으면 쿼리 및 뷰 디자이너에서 자동으로 등가 연산자 "="를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-115">If you do not enter an operator, the Query and View Designer automatically inserts the equality operator "=".</span></span>  
  
 <span data-ttu-id="b759a-116">쿼리 및 뷰 디자이너는 WHERE 절을 추가하거나 수정하여 [SQL 창](sql-pane-visual-database-tools.md) 에서 SQL 문을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b759a-116">The Query and View Designer updates the SQL statement in the [SQL Pane](sql-pane-visual-database-tools.md) by adding or modifying the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b759a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b759a-117">See Also</span></span>  
 <span data-ttu-id="b759a-118">[Visual Database Tools&#41;&#40;검색 값을 입력 하는 규칙](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b759a-118">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b759a-119">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b759a-119">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
