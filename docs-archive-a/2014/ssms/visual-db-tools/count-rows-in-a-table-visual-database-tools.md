---
title: 테이블의 행 계산(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732216"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="89707-102">테이블의 행 계산(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="89707-102">Count Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="89707-103">테이블의 행을 계산하여 다음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-103">You can count rows in a table to determine:</span></span>  
  
-   <span data-ttu-id="89707-104">테이블의 전체 행 수. 예를 들어, `titles` 테이블의 전체 책 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-104">The total number of rows in a table, for example, a count of all the books in a `titles` table.</span></span>  
  
-   <span data-ttu-id="89707-105">테이블에서 특정 조건에 맞는 행의 수. 예를 들어, `titles` 테이블에서 한 출판사가 발행한 책 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-105">The number of rows in a table that meet a specific condition, for example, the number of books by one publisher in a `titles` table.</span></span>  
  
-   <span data-ttu-id="89707-106">특정 열의 값 수</span><span class="sxs-lookup"><span data-stu-id="89707-106">The number of values in a particular column.</span></span>  
  
 <span data-ttu-id="89707-107">열의 값 수를 계산할 때 null 값은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-107">When you count values in a column, nulls are not included in the count.</span></span> <span data-ttu-id="89707-108">예를 들어, `titles` 열에 값이 있는 `advance` 테이블에서 책 수를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-108">For example, you might count the number of books in a `titles` table that have values in the `advance` column.</span></span> <span data-ttu-id="89707-109">기본적으로 모든 값이 계산에 포함되며 여기에는 중복된 값도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-109">By default, the count includes all values, not just unique values.</span></span>  
  
 <span data-ttu-id="89707-110">이와 같은 세 가지 종류의 계산 절차는 모두 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-110">The procedures for all three types of counts are similar.</span></span>  
  
### <a name="to-count-all-the-rows-in-a-table"></a><span data-ttu-id="89707-111">테이블의 전체 행 수를 계산하려면</span><span class="sxs-lookup"><span data-stu-id="89707-111">To count all the rows in a table</span></span>  
  
1.  <span data-ttu-id="89707-112">요약하려는 테이블이 다이어그램 창에 표시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-112">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="89707-113">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **그룹화 방법 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-113">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="89707-114">[쿼리 및 뷰 디자이너](visual-database-tools.md) 에서 **그룹화 방법** 열이 조건 창의 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-114">The [Query and View Designer](visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="89707-115">테이블이 나 테이블 반환 개체를 나타내는 사각형에서 \*\* \* (모든 열)\*\* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-115">Select **\* (All Columns)** in the rectangle representing the table or table-valued object.</span></span>  
  
     <span data-ttu-id="89707-116">쿼리 및 뷰 디자이너의 조건 창에서 **그룹화 방법** 열에 **Count**라는 단어가 자동으로 입력되고 요약하려는 열에 대한 열 별칭이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-116">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="89707-117">자동으로 생성된 이 별칭을 좀 더 의미 있는 별칭으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89707-117">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="89707-118">자세한 내용은 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89707-118">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="89707-119">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-119">Run the query.</span></span>  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a><span data-ttu-id="89707-120">조건을 충족하는 모든 행을 계산하려면</span><span class="sxs-lookup"><span data-stu-id="89707-120">To count all the rows that meet a condition</span></span>  
  
1.  <span data-ttu-id="89707-121">요약하려는 테이블이 다이어그램 창에 표시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-121">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="89707-122">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **그룹화 방법 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-122">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="89707-123">쿼리 및 뷰 디자이너에서 **그룹화 방법** 열이 조건 창의 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-123">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="89707-124">테이블이 나 테이블 구조 개체를 나타내는 사각형에서 \*\* \* (모든 열)\*\* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-124">Select **\*(All Columns)** in the rectangle representing the table or table-structured object.</span></span>  
  
     <span data-ttu-id="89707-125">쿼리 및 뷰 디자이너의 조건 창에서 **그룹화 방법** 열에 **Count**라는 단어가 자동으로 입력되고 요약하려는 열에 대한 열 별칭이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-125">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="89707-126">쿼리 결과에 더 유용한 열 머리글을 만들려면 [열 별칭 만들기&#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89707-126">To create a more useful column heading in query output, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="89707-127">검색하려는 데이터 열을 추가한 다음 **출력** 열의 확인란 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-127">Add the data column that you want to search, and then clear the check box in the **Output** column.</span></span>  
  
     <span data-ttu-id="89707-128">쿼리 및 뷰 디자이너에서 표의 **그룹화 방법** 열에 **Group By** 라는 단어가 자동으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-128">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
5.  <span data-ttu-id="89707-129">**그룹화 방법** 열에서 **Group By** 를 **Where**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-129">Change **Group By** in the **Group By** column to **Where**.</span></span>  
  
6.  <span data-ttu-id="89707-130">검색할 데이터 열의 **필터** 열에 검색 조건을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-130">In the **Filter** column for the data column to search, enter the search condition.</span></span>  
  
7.  <span data-ttu-id="89707-131">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-131">Run the query.</span></span>  
  
### <a name="to-count-the-values-in-a-column"></a><span data-ttu-id="89707-132">열에 있는 값의 수를 계산하려면</span><span class="sxs-lookup"><span data-stu-id="89707-132">To count the values in a column</span></span>  
  
1.  <span data-ttu-id="89707-133">요약하려는 테이블이 다이어그램 창에 표시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-133">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="89707-134">다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **그룹화 방법 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-134">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="89707-135">쿼리 및 뷰 디자이너에서 **그룹화 방법** 열이 조건 창의 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-135">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="89707-136">계산하려는 열을 조건 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-136">Add the column that you want to count to the Criteria pane.</span></span>  
  
     <span data-ttu-id="89707-137">쿼리 및 뷰 디자이너에서 표의 **그룹화 방법** 열에 **Group By** 라는 단어가 자동으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="89707-137">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
4.  <span data-ttu-id="89707-138">**그룹화 방법** 열에서 **Group By** 를 **Count**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-138">Change **Group By** in the **Group By** column to **Count**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89707-139">중복된 값은 모두 하나로 간주하여 계산하려면 **Count Distinct**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-139">To count only unique values, choose **Count Distinct**.</span></span>  
  
5.  <span data-ttu-id="89707-140">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="89707-140">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89707-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89707-141">See Also</span></span>  
 <span data-ttu-id="89707-142">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="89707-142">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="89707-143">쿼리 결과 요약&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="89707-143">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
