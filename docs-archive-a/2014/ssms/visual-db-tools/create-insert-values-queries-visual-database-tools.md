---
title: 값 삽입 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fc71b0148ee8a7e92c517fe75b56c329b3c88f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731283"
---
# <a name="create-insert-values-queries-visual-database-tools"></a><span data-ttu-id="1040c-102">값 삽입 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1040c-102">Create Insert Values Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="1040c-103">값 삽입 쿼리를 사용하여 현재 테이블에 새 행을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-103">You can create a new row in the current table using an Insert Values query.</span></span> <span data-ttu-id="1040c-104">값 삽입 쿼리를 만들려면 다음 항목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-104">When you create an Insert Values query, you specify:</span></span>  
  
-   <span data-ttu-id="1040c-105">행을 추가할 데이터베이스 테이블</span><span class="sxs-lookup"><span data-stu-id="1040c-105">The database table to add the row to.</span></span>  
  
-   <span data-ttu-id="1040c-106">내용을 추가하려는 열</span><span class="sxs-lookup"><span data-stu-id="1040c-106">The columns whose contents you want to add.</span></span>  
  
-   <span data-ttu-id="1040c-107">개별 열에 삽입할 값이나 식</span><span class="sxs-lookup"><span data-stu-id="1040c-107">The value or expression to insert into the individual columns.</span></span>  
  
 <span data-ttu-id="1040c-108">예를 들어, 다음 쿼리는 제목, 종류, 출판사 및 가격 값을 지정하는 행을 `titles` 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-108">For example, the following query adds a row to the `titles` table, specifying values for the title, type, publisher, and price:</span></span>  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 <span data-ttu-id="1040c-109">값 삽입 쿼리를 만들면 삽입할 값과 열 이름 같이 새 행을 삽입하는 데 필요한 옵션만 반영하도록 조건 창이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-109">When you create an Insert Values query, the Criteria pane changes to reflect the only options available for inserting a new row: the column name and the value to insert.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1040c-110">값 삽입 쿼리의 실행 동작을 취소할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-110">You cannot undo the action of executing an Insert Values query.</span></span> <span data-ttu-id="1040c-111">문제가 발생할 경우에 대비하여 쿼리를 실행하기 전에 데이터를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-111">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-values-query"></a><span data-ttu-id="1040c-112">값 삽입 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1040c-112">To create an Insert Values query</span></span>  
  
1.  <span data-ttu-id="1040c-113">업데이트하려는 테이블을 다이어그램 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-113">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="1040c-114">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **값 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-114">From the **Query Designer** menu point to **Change Type**, and then click **Insert Values**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1040c-115">값 삽입 쿼리를 시작할 때 다이어그램 창에 두 개 이상의 테이블이 표시되어 있으면 업데이트할 테이블의 이름을 지정하라는 메시지가 쿼리 및 뷰 디자이너의 [값 삽입 대상 테이블 선택 대화 상자](visual-database-tools.md) 에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-115">If more than one table is displayed in the Diagram pane when you start the Insert Values query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="1040c-116">다이어그램 창에서 새 값을 입력하려는 각 열의 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-116">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="1040c-117">선택한 열이 조건 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-117">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="1040c-118">열을 쿼리에 추가한 경우에만 열이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-118">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="1040c-119">조건 창의 **새 값** 열에 열의 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-119">In the **New Value** column of the Criteria pane, enter the new value for the column.</span></span> <span data-ttu-id="1040c-120">리터럴 값, 열 이름 또는 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-120">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="1040c-121">이 값은 업데이트하려는 열의 데이터 형식과 일치하거나 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-121">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="1040c-122">쿼리 및 뷰 디자이너에서는 사용자가 입력한 값이 삽입하려는 열의 길이에 맞는지 여부를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-122">The Query and View Designer cannot check that a value fits within the length of the column you are inserting.</span></span> <span data-ttu-id="1040c-123">입력한 값이 너무 길면 아무런 경고 메시지 없이 값이 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-123">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="1040c-124">예를 들어, 20자까지 허용되는 `name` 열에 길이가 25자인 삽입 값을 지정하면 마지막 5자가 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-124">For example, if a `name` column is 20 characters long but you specify an insert value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
 <span data-ttu-id="1040c-125">값 삽입 쿼리를 실행해도 [결과 창](results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-125">When you execute an Insert Values query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="1040c-126">대신, 변경된 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1040c-126">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1040c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1040c-127">See Also</span></span>  
 <span data-ttu-id="1040c-128">[Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1040c-128">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="1040c-129">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1040c-129">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1040c-130">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1040c-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
