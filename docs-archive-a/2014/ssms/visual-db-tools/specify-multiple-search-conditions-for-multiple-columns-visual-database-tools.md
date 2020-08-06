---
title: 여러 열에 여러 검색 조건 지정 (Visual Database Tools) | Microsoft Docs
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
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccf08a98d39d4ab808b7c2df794164b341be363a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648735"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a><span data-ttu-id="622b2-102">여러 열에 여러 검색 조건 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="622b2-102">Specify Multiple Search Conditions for Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="622b2-103">여러 개의 데이터 열을 검색 조건의 일부로 포함하여 쿼리의 범위를 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-103">You can expand or narrow the scope of your query by including several data columns as part of your search condition.</span></span> <span data-ttu-id="622b2-104">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="622b2-105">근무 연수가 5년이 넘었거나 특정 작업을 담당하는 직원을 검색하는 경우</span><span class="sxs-lookup"><span data-stu-id="622b2-105">Search for employees who either have worked more than five years at the company or who hold certain jobs.</span></span>  
  
-   <span data-ttu-id="622b2-106">특정 출판사에서 출판한 요리 관련 서적을 검색하는 경우</span><span class="sxs-lookup"><span data-stu-id="622b2-106">Search for a book that is both published by a specific publisher and pertains to cooking.</span></span>  
  
 <span data-ttu-id="622b2-107">둘 이상의 열 중 하나에 들어 있는 값을 검색하는 쿼리를 만들려면 OR 조건을 지정하고</span><span class="sxs-lookup"><span data-stu-id="622b2-107">To create a query that searches for values in either of two (or more) columns, you specify an OR condition.</span></span> <span data-ttu-id="622b2-108">둘 이상의 열에 있는 모든 조건을 만족해야 하는 쿼리를 만들려면 AND 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-108">To create a query that must meet all conditions in two (or more) columns, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="622b2-109">OR 조건 지정</span><span class="sxs-lookup"><span data-stu-id="622b2-109">Specifying an OR Condition</span></span>  
 <span data-ttu-id="622b2-110">OR로 연결된 여러 개의 조건을 만들려면 조건 창에서 각 조건을 서로 다른 열에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-110">To create multiple conditions linked with OR, you put each separate condition in a different column of the Criteria pane.</span></span>  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a><span data-ttu-id="622b2-111">두 개의 서로 다른 열에 OR 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="622b2-111">To specify an OR condition for two different columns</span></span>  
  
1.  <span data-ttu-id="622b2-112">[조건 창](visual-database-tools.md)에서 검색할 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-112">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="622b2-113">검색할 첫 번째 열의 **필터** 열에서 첫째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-113">In the **Filter** column for the first column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="622b2-114">**필터** 열은 비워 두고 검색할 두 번째 데이터 열의 **또는...** 열에서 둘째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-114">In the **Or...** column for the second data column to search, specify the second condition, leaving the **Filter** column blank.</span></span>  
  
     <span data-ttu-id="622b2-115">쿼리 및 뷰 디자이너는 다음과 같이 OR 조건을 포함하는 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-115">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  <span data-ttu-id="622b2-116">추가할 각 조건에 대하여 2단계와 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-116">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span> <span data-ttu-id="622b2-117">각 새 조건에 서로 다른 **또는...** 열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-117">Use a different **Or...** column for each new condition.</span></span>  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="622b2-118">AND 조건 지정</span><span class="sxs-lookup"><span data-stu-id="622b2-118">Specifying an AND Condition</span></span>  
 <span data-ttu-id="622b2-119">AND로 연결된 조건을 사용하여 서로 다른 데이터 열을 검색하려면 표의 **필터** 열에 모든 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-119">To search different data columns using conditions linked with AND, you put all the conditions in the **Filter** column of the grid.</span></span>  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a><span data-ttu-id="622b2-120">두 개의 서로 다른 열에 AND 조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="622b2-120">To specify an AND condition for two different columns</span></span>  
  
1.  <span data-ttu-id="622b2-121">[조건 창](visual-database-tools.md)에서 검색할 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-121">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="622b2-122">검색할 첫 번째 데이터 열의 **필터** 열에서 첫째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-122">In the **Filter** column for the first data column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="622b2-123">두 번째 데이터 열의 **필터** 열에서 둘째 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-123">In the **Filter** column for the second data column, specify the second condition.</span></span>  
  
     <span data-ttu-id="622b2-124">쿼리 및 뷰 디자이너는 다음과 같이 AND 조건을 포함하는 WHERE 절을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-124">The Query and View Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  <span data-ttu-id="622b2-125">추가할 각 조건에 대하여 2단계와 3단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="622b2-125">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622b2-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="622b2-126">See Also</span></span>  
 <span data-ttu-id="622b2-127">[Visual Database Tools &#40;및에 우선 순위가 있는 조건 조합&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="622b2-127">[Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="622b2-128">[OR에 우선 순위가 있는 조건을 조합 하 여 Visual Database Tools &#40;&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="622b2-128">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="622b2-129">[조건 창에서 검색 조건을 결합 하는 규칙 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="622b2-129">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="622b2-130">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="622b2-130">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
