---
title: 업데이트 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bbea575d544875dba73de923474cc11bbcb46a9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651986"
---
# <a name="create-update-queries-visual-database-tools"></a><span data-ttu-id="f0ed2-102">업데이트 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0ed2-102">Create Update Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="f0ed2-103">업데이트 쿼리를 사용하면 한 번의 작업으로 여러 행의 내용을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-103">You can change the contents of multiple rows in one operation by using an Update query.</span></span> <span data-ttu-id="f0ed2-104">예를 들어 `titles` 테이블에서 업데이트 쿼리를 사용하여 특정 출판사의 모든 책 가격에 10%를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-104">For example, in a `titles` table you can use an Update query to add 10% to the price of all books for a particular publisher.</span></span>  
  
 <span data-ttu-id="f0ed2-105">업데이트 쿼리를 만들려면 다음 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-105">When you create an Update query, you specify:</span></span>  
  
-   <span data-ttu-id="f0ed2-106">업데이트할 테이블</span><span class="sxs-lookup"><span data-stu-id="f0ed2-106">The table to update.</span></span>  
  
-   <span data-ttu-id="f0ed2-107">내용을 업데이트하려는 열</span><span class="sxs-lookup"><span data-stu-id="f0ed2-107">The columns whose contents you want to update.</span></span>  
  
-   <span data-ttu-id="f0ed2-108">개별 열을 업데이트하는 데 사용할 값이나 식</span><span class="sxs-lookup"><span data-stu-id="f0ed2-108">The value or expression to use to update the individual columns.</span></span>  
  
-   <span data-ttu-id="f0ed2-109">업데이트할 행을 정의하는 검색 조건</span><span class="sxs-lookup"><span data-stu-id="f0ed2-109">Search conditions to define the rows you want to update.</span></span>  
  
 <span data-ttu-id="f0ed2-110">예를 들어 다음 쿼리는 한 출판사의 모든 책 가격에 10%를 추가하여 `titles` 테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-110">For example, the following query updates the `titles` table by adding 10% to the price of all titles for one publisher:</span></span>  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="f0ed2-111">업데이트 쿼리의 실행 동작을 취소할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-111">You cannot undo the action of executing an Update query.</span></span> <span data-ttu-id="f0ed2-112">문제가 발생할 경우에 대비하여 쿼리를 실행하기 전에 데이터를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-112">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-update-query"></a><span data-ttu-id="f0ed2-113">업데이트 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0ed2-113">To create an Update query</span></span>  
  
1.  <span data-ttu-id="f0ed2-114">업데이트하려는 테이블을 다이어그램 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-114">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="f0ed2-115">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **업데이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-115">From the **Query Designer** menu point to **Change Type**, and then click **Update**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0ed2-116">업데이트 쿼리를 시작할 때 다이어그램 창에 두 개 이상의 테이블이 표시되어 있으면 쿼리 및 뷰 디자이너에서 [값 삽입의 대상 테이블 선택 대화 상자](visual-database-tools.md) 에 업데이트할 테이블의 이름을 지정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-116">If more than one table is displayed in the Diagram pane when you start the Update query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="f0ed2-117">다이어그램 창에서 새 값을 입력하려는 각 열의 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-117">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="f0ed2-118">선택한 열이 조건 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-118">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="f0ed2-119">열을 쿼리에 추가한 경우에만 열이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-119">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="f0ed2-120">조건 창의 **새 값** 열에 열의 업데이트 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-120">In the **New Value** column of the Criteria pane, enter the update value for the column.</span></span> <span data-ttu-id="f0ed2-121">리터럴 값, 열 이름 또는 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-121">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="f0ed2-122">이 값은 업데이트하려는 열의 데이터 형식과 일치하거나 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-122">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="f0ed2-123">쿼리 및 뷰 디자이너에서는 사용자가 입력한 값이 업데이트하려는 열의 길이에 맞는지 여부를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-123">The Query and View Designer cannot check that a value fits within the length of the column you are updating.</span></span> <span data-ttu-id="f0ed2-124">입력한 값이 너무 길면 아무런 경고 메시지 없이 값이 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-124">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="f0ed2-125">예를 들어 20자까지 허용되는 `name` 열에 길이가 25자인 업데이트 값을 지정하면 마지막 5자가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-125">For example, if a `name` column is 20 characters long but you specify an update value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
5.  <span data-ttu-id="f0ed2-126">**필터** 열에 검색 조건을 입력하여 업데이트할 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-126">Define the rows to update by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="f0ed2-127">자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-127">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="f0ed2-128">검색 조건을 지정하지 않으면 지정된 테이블의 행 전체가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-128">If you do not specify a search condition, all rows in the specified table will be updated.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0ed2-129">검색 조건에 사용할 열을 조건 창에 추가하면 쿼리 및 뷰 디자이너의 업데이트할 열 목록에도 이 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-129">When you add a column to the Criteria pane for use in a search condition, the Query and View Designer also adds it to the list of columns to be updated.</span></span> <span data-ttu-id="f0ed2-130">열을 검색 조건에만 사용하고 업데이트는 하지 않으려면 테이블 또는 테이블 반환 개체를 나타내는 사각형에서 열 이름 옆에 있는 확인란의 선택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-130">If you want to use a column for a search condition but not update it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
 <span data-ttu-id="f0ed2-131">업데이트 쿼리를 실행해도 [결과 창](results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-131">When you execute an Update query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="f0ed2-132">대신, 변경된 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ed2-132">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ed2-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0ed2-133">See Also</span></span>  
 <span data-ttu-id="f0ed2-134">[Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed2-134">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="f0ed2-135">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed2-135">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f0ed2-136">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f0ed2-136">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
