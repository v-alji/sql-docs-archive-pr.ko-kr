---
title: 수동으로 자체 조인 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- self-joins
- manual joins [SQL Server]
- joins [SQL Server], self
ms.assetid: 910ed516-cb84-481b-95d0-cba3e89afdba
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31e125fdfe0f7f285ea679cfe85356d1aa10353a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651991"
---
# <a name="create-self-joins-manually-visual-database-tools"></a><span data-ttu-id="d3c4b-102">수동으로 자체 조인 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d3c4b-102">Create Self-Joins Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="d3c4b-103">데이터베이스에서 테이블에 반사 관계가 없는 경우에도 테이블을 자체 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-103">You can join a table to itself even if the table does not have a reflexive relationship in the database.</span></span> <span data-ttu-id="d3c4b-104">예를 들어, 자체 조인을 사용하여 같은 도시에 살고 있는 만든 이 쌍을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-104">For example, you can use a self-join to find pairs of authors living in the same city.</span></span>  
  
 <span data-ttu-id="d3c4b-105">다른 조인과 마찬가지로 자체 조인에도 테이블이 두 개 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-105">As with any join, a self-join requires at least two tables.</span></span> <span data-ttu-id="d3c4b-106">차이점은 쿼리에 두 번째 테이블을 추가하지 않고 같은 테이블의 두 번째 인스턴스를 추가한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-106">The difference is that, instead of adding a second table to the query, you add a second instance of the same table.</span></span> <span data-ttu-id="d3c4b-107">이런 방식으로 테이블의 첫 번째 인스턴스의 열을 두 번째 인스턴스의 같은 열과 비교하여 열의 값을 서로 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-107">That way, you can compare a column in the first instance of the table to the same column in the second instance, which allows you to compare the values in a column to each other.</span></span> <span data-ttu-id="d3c4b-108">[쿼리 및 뷰 디자이너](visual-database-tools.md) 는 테이블의 두 번째 인스턴스에 별칭을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-108">The [Query and View Designer](visual-database-tools.md) assigns an alias to the second instance of the table.</span></span>  
  
 <span data-ttu-id="d3c4b-109">예를 들어, Berkeley 에 살고 있는 모든 만든 이 쌍을 찾는 자체 조인을 만드는 중인 경우 테이블의 첫 번째 인스턴스의 `city` 열과 두 번째 인스턴스의 `city` 열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-109">For example, if you are creating a self-join to find all pairs of authors within Berkeley, you compare the `city` column in the first instance of the table against the `city` column in the second instance.</span></span> <span data-ttu-id="d3c4b-110">완성된 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-110">The resulting query might look like the following:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="d3c4b-111">자체 조인을 만들 때 조인 조건이 여러 개 필요한 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-111">Creating a self-join often requires multiple join conditions.</span></span> <span data-ttu-id="d3c4b-112">이유를 알아보려면 이전 쿼리의 결과를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-112">To understand why, consider the result of the preceding query:</span></span>  
  
```  
Cheryl Carson       Cheryl Carson  
Abraham Bennet      Abraham Bennet  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="d3c4b-113">첫 번째 행은 Cheryl Carson이 Cheryl Carson과 같은 도시에 살고 있음을 나타내므로 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-113">The first row is useless; it indicates that Cheryl Carson lives in the same city as Cheryl Carson.</span></span> <span data-ttu-id="d3c4b-114">마찬가지로 두 번째 행도 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-114">The second row is equally useless.</span></span> <span data-ttu-id="d3c4b-115">이런 필요 없는 데이터를 제거하려면 두 개의 만든 이 이름이 서로 다른 만든 이를 나타내는 결과 행만 보유하는 다른 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-115">To eliminate this useless data, you add another condition retaining only those result rows in which the two author names describe different authors.</span></span> <span data-ttu-id="d3c4b-116">완성된 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-116">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             <> authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="d3c4b-117">결과 집합이 다음과 같이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-117">The result set is improved:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="d3c4b-118">하지만 두 결과 행이 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-118">But the two result rows are redundant.</span></span> <span data-ttu-id="d3c4b-119">첫 번째 행은 Carson이 Bennet과 같은 도시에 살고 있음을 나타내며 두 번째 행은 Bennet이 Carson과 같은 도시에 살고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-119">The first says Carson lives in the same city as Bennet, and the second says the Bennet lives in the same city as Carson.</span></span> <span data-ttu-id="d3c4b-120">이런 중복 결과를 제거하려면 두 번째 조인 조건을 "not equals"에서 "less than"으로 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-120">To eliminate this redundancy, you can alter the second join condition from "not equals" to "less than."</span></span> <span data-ttu-id="d3c4b-121">완성된 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-121">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             < authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="d3c4b-122">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-122">And the result set looks like this:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
```  
  
### <a name="to-create-a-self-join-manually"></a><span data-ttu-id="d3c4b-123">자체 조인을 수동으로 만들려면</span><span class="sxs-lookup"><span data-stu-id="d3c4b-123">To create a self-join manually</span></span>  
  
1.  <span data-ttu-id="d3c4b-124">작업할 테이블 또는 테이블 반환 개체를 [다이어그램 창](diagram-pane-visual-database-tools.md) 에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-124">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the table or table-valued object you want to work with.</span></span>  
  
2.  <span data-ttu-id="d3c4b-125">다이어그램 창에 같은 테이블 또는 테이블 반환 개체가 두 번 표시되도록 같은 테이블을 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-125">Add the same table again, so that the Diagram pane shows the same table or table-valued object twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="d3c4b-126">쿼리 및 뷰 디자이너는 테이블 이름에 일련 번호를 추가하여 두 번째 인스턴스에 별칭을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-126">The Query and View Designer assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="d3c4b-127">또한 쿼리 및 뷰 디자이너는 다이어그램 창 내에서 테이블 또는 테이블 반환 개체의 두 일치 항목 사이에 조인 선을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-127">In addition, the Query and View Designer creates a join line between the two occurrences of the table or table-valued object within the Diagram pane.</span></span>  
  
3.  <span data-ttu-id="d3c4b-128">조인 선을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-128">Right-click the join line and choose **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="d3c4b-129">속성 창에서 **조인 조건 및 형식**을 클릭하고 속성의 오른쪽에 있는 **줄임표(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-129">In the Properties window click **Join Condition and Type** and click the **ellipses (...)** to the right of the property.</span></span>  
  
5.  <span data-ttu-id="d3c4b-130">필요한 경우 [조인 대화 상자](join-dialog-box-visual-database-tools.md) 에서 기본 키 사이의 비교 연산자를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-130">In the [Join Dialog Box](join-dialog-box-visual-database-tools.md) change the comparison operator between the primary keys as required.</span></span> <span data-ttu-id="d3c4b-131">예를 들어, 연산자를 (<)보다 작음으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-131">For example, you might change the operator to less than (<).</span></span>  
  
6.  <span data-ttu-id="d3c4b-132">테이블 또는 테이블 반환 개체의 첫 번째 일치 항목에서 기본 조인 열의 이름을 끌어서 두 번째 일치 항목의 해당 열에 놓는 방법을 통해 추가 조인 조건(예: authors.zip = authors1.zip)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-132">Create the additional join condition (for example, authors.zip = authors1.zip) by dragging the name of the primary join column in the first occurrence of the table or table-valued object and dropping it on the corresponding column in the second occurrence.</span></span>  
  
7.  <span data-ttu-id="d3c4b-133">출력 열, 검색 조건, 정렬 순서 등의 기타 쿼리 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c4b-133">Specify other options for the query such as output columns, search conditions, and sort order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c4b-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3c4b-134">See Also</span></span>  
 <span data-ttu-id="d3c4b-135">[Visual Database Tools를 &#40;자동으로 자체 조인 만들기&#41;](create-self-joins-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3c4b-135">[Create Self-Joins Automatically &#40;Visual Database Tools&#41;](create-self-joins-automatically-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d3c4b-136">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="d3c4b-136">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
