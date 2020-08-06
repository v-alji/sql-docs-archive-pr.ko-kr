---
title: 외부 조인 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: stevestein
ms.author: sstein
ms.openlocfilehash: f02c0be049e2e75e1a657bb3c027d20430d562cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741528"
---
# <a name="create-outer-joins-visual-database-tools"></a><span data-ttu-id="ad114-102">외부 조인 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ad114-102">Create Outer Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="ad114-103">[쿼리 및 뷰 디자이너](visual-database-tools.md) 는 기본적으로 테이블 간에 내부 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-103">By default, the [Query and View Designer](visual-database-tools.md) creates an inner join between tables.</span></span> <span data-ttu-id="ad114-104">다른 테이블의 행과 일치하지 않는 행은 없앱니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-104">Inner joins eliminate the rows that do not match with a row from the other table.</span></span> <span data-ttu-id="ad114-105">그러나 외부 조인은 FROM 절에 지정된 하나 이상의 테이블이나 뷰에서 WHERE 또는 HAVING 검색 조건을 만족하는 모든 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-105">Outer joins, however, return all rows from at least one of the tables or views mentioned in the FROM clause, as long as those rows meet any WHERE or HAVING search conditions.</span></span> <span data-ttu-id="ad114-106">조인된 테이블에 일치 값이 없는 데이터 행을 결과 집합에 포함하려면 외부 조인을 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-106">If you want to include data rows in the result set that do not have a match in the joined table, you can create an outer join.</span></span>  
  
 <span data-ttu-id="ad114-107">외부 조인을 만들 때는 SQL 창의 SQL 문에 테이블이 표시되는 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-107">When you create an outer join, the order in which tables appear in the SQL statement (as reflected in the SQL pane) is significant.</span></span> <span data-ttu-id="ad114-108">첫 번째로 추가하는 테이블이 "왼쪽" 테이블이 되고 두 번째로 추가하는 테이블이 "오른쪽" 테이블이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-108">The first table you add becomes the "left" table and the second table becomes the "right" table.</span></span> <span data-ttu-id="ad114-109">[다이어그램 창](diagram-pane-visual-database-tools.md) 에 테이블이 실제로 표시되는 순서는 중요하지 않습니다. 왼쪽 또는 오른쪽 우선 외부 조인을 지정할 경우 쿼리에 테이블이 추가된 순서와 [SQL 창](sql-pane-visual-database-tools.md)의 SQL 문에 테이블이 표시되는 순서를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-109">(The actual order in which the tables appear in the [Diagram pane](diagram-pane-visual-database-tools.md) is not significant.) When you specify a left or right outer join, you are referring to the order in which the tables were added to the query and to the order in which they appear in the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-an-outer-join"></a><span data-ttu-id="ad114-110">외부 조인을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ad114-110">To create an outer join</span></span>  
  
1.  <span data-ttu-id="ad114-111">자동 또는 수동으로 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-111">Create the join, either automatically or manually.</span></span> <span data-ttu-id="ad114-112">자세한 내용은 [테이블 자동 조인&#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) 또는 [테이블 수동 조인&#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad114-112">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) or [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="ad114-113">다이어그램 창에서 조인 선을 선택한 다음 **쿼리 디자이너** 메뉴에서 **\<tablename>의 모든 행 선택**을 선택하여 포함하려는 여분의 행이 들어 있는 테이블을 포함하는 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-113">Select the join line in the Diagram pane, and then from the **Query Designer** menu, choose **Select All Rows from \<tablename>**, selecting the command that includes the table whose extra rows you want to include.</span></span>  
  
    -   <span data-ttu-id="ad114-114">첫 번째 테이블을 선택하여 왼쪽 우선 외부 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-114">Choose the first table to create a left outer join.</span></span>  
  
    -   <span data-ttu-id="ad114-115">두 번째 테이블을 선택하여 오른쪽 우선 외부 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-115">Choose the second table to create a right outer join.</span></span>  
  
    -   <span data-ttu-id="ad114-116">두 테이블을 모두 선택하여 완전 외부 조인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-116">Choose both tables to create a full outer join.</span></span>  
  
 <span data-ttu-id="ad114-117">외부 조인을 지정하면 쿼리 및 뷰 디자이너가 외부 조인을 나타내는 조인 선을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-117">When you specify an outer join, the Query and View Designer modifies the join line to indicate an outer join.</span></span>  
  
 <span data-ttu-id="ad114-118">또한 쿼리 및 뷰 디자이너는 SQL 창의 SQL 문을 다음과 같이 수정하여 조인 형식의 변경 사항을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-118">In addition, the Query and View Designer modifies the SQL statement in the SQL pane to reflect the change in join type, as shown in the following statement:</span></span>  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
 <span data-ttu-id="ad114-119">외부 조인은 일치하지 않는 행을 포함하므로 FOREIGN KEY 제약 조건을 위반하는 행을 찾는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-119">Because an outer join includes unmatched rows, you can use it to find rows that violate foreign key constraints.</span></span> <span data-ttu-id="ad114-120">이를 수행하려면 외부 조인을 만든 다음 검색 조건을 추가하여 가장 오른쪽 테이블의 기본 키 열이 null인 행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-120">To do so, you create an outer join and then add a search condition to find rows in which the primary key column of the rightmost table is null.</span></span> <span data-ttu-id="ad114-121">예를 들어 다음 외부 조인은 `employee` 테이블에서 `jobs` 테이블의 해당 행을 포함하지 않는 행을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ad114-121">For example, the following outer join finds rows in the `employee` table that do not have corresponding rows in the `jobs` table:</span></span>  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad114-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad114-122">See Also</span></span>  
 <span data-ttu-id="ad114-123">[Visual Database Tools를 &#40;조인을 사용 하 여 쿼리&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ad114-123">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ad114-124">조인 대화 상자&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ad114-124">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
