---
title: 결과 창에서 데이터 작업(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- queries [Visual Database Tools]
- result sets [SQL Server], queries
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- Visual Database Tools [SQL Server], queries
- queries [SQL Server], results
- Results pane
ms.assetid: 4f8a0080-91ef-4442-83ae-53be2f478c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c914b924ee477c3a59d78ae3ec114c88497726a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651414"
---
# <a name="work-with-data-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="2be9f-102">결과 창에서 데이터 작업(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2be9f-102">Work with Data in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="2be9f-103">쿼리나 뷰를 실행하면 결과 창에 그 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-103">After you run a query or view, the results are shown in the Results pane.</span></span> <span data-ttu-id="2be9f-104">이러한 결과를 사용하여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-104">You can then work with those results.</span></span> <span data-ttu-id="2be9f-105">예를 들어 행을 추가 및 삭제하고 데이터를 입력 또는 변경하며 수많은 결과 집합 사이를 쉽게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-105">For example, you can add and delete rows, input or change data, and easily navigate through large results sets.</span></span>  
  
 <span data-ttu-id="2be9f-106">다음은 결과 집합을 효율적으로 사용하고 문제를 방지하는 데 도움이 되는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-106">The following information can help you avoid problems and work effectively with your results sets.</span></span>  
  
## <a name="returning-the-results-set"></a><span data-ttu-id="2be9f-107">결과 집합 반환</span><span class="sxs-lookup"><span data-stu-id="2be9f-107">Returning the results set</span></span>  
 <span data-ttu-id="2be9f-108">쿼리나 뷰의 결과를 반환할 수 있고 결과 창만 열지 또는 모든 창을 열지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-108">You can return results from either a query or a view and can choose whether to open just the results pane or all panes.</span></span> <span data-ttu-id="2be9f-109">두 경우 모두 쿼리 및 뷰 디자이너에서 쿼리나 뷰가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-109">In either case the query or view will open in Query and View Designer.</span></span> <span data-ttu-id="2be9f-110">둘 사이의 차이점은 결과 창만 열리거나 아니면 옵션 대화 상자에서 선택한 모든 창이 열린다는 점뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-110">The difference is that one opens with only the Results pane showing and the other opens with all windows that have been selected in the Options dialog box.</span></span> <span data-ttu-id="2be9f-111">기본적으로는 네 개의 창(결과, SQL, 다이어그램 및 조건)이 모두 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-111">The default is all four panes (Results, SQL, Diagram, and Criteria).</span></span>  
  
 <span data-ttu-id="2be9f-112">자세한 내용은 [쿼리 열기&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2be9f-112">For more information see [Open Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="2be9f-113">다른 결과 집합을 반환하거나 다른 순서로 레코드를 반환하도록 쿼리나 뷰의 디자인을 변경하려면 [쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)에 나열된 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2be9f-113">To change the design of the query or view so it returns a different set of results or returns records in a different order see the topics listed in [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="2be9f-114">결과 집합을 모두 반환할지 아니면 일부만 반환할지 결정하는 데는 두 가지 방법을 사용할 수 있습니다. 즉, 실행 중인 쿼리를 중지하거나 반환할 결과의 양을 미리 선택한 다음 쿼리를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-114">You can also determine whether to return all or part of the results set in two ways--stop the query as it runs or choose how much of results to return before the query is run.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="2be9f-115">결과 창에서 탐색</span><span class="sxs-lookup"><span data-stu-id="2be9f-115">Navigating in the results pane</span></span>  
 <span data-ttu-id="2be9f-116">결과 창의 아래쪽에 있는 탐색 모음을 사용하면 레코드를 빠르게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-116">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="2be9f-117">이 탐색 모음에는 첫 번째 레코드와 마지막 레코드, 다음 레코드와 이전 레코드 또는 특정 레코드로 이동하기 위한 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-117">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="2be9f-118">특정 레코드로 이동하려면 탐색 모음의 입력란에 원하는 행 번호를 입력한 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-118">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="2be9f-119">쿼리 및 뷰 디자이너에서 바로 가기 키를 사용하는 방법에 대한 자세한 내용은 [쿼리 및 뷰 디자이너에서 탐색&#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2be9f-119">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](navigate-in-the-query-and-view-designer-visual-database-tools.md).</span></span>  
  
## <a name="committing-changes-to-the-database"></a><span data-ttu-id="2be9f-120">데이터베이스에 변경 내용 커밋</span><span class="sxs-lookup"><span data-stu-id="2be9f-120">Committing changes to the database</span></span>  
 <span data-ttu-id="2be9f-121">결과 창에는 낙관적 동시성 제어가 사용되므로 표에는 완전한 실시간 보기 대신 데이터베이스의 데이터 복사본이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-121">The Results pane uses optimistic concurrency control so the grid shows a copy of the data in the database rather than an entirely live view.</span></span> <span data-ttu-id="2be9f-122">따라서 사용자가 행에서 포커스를 옮긴 후에만 변경 내용이 데이터베이스에 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-122">This way changes are only committed to the database after you move off of a row.</span></span> <span data-ttu-id="2be9f-123">이와 같은 방식으로 여러 사용자가 동시에 데이터베이스를 사용하여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-123">This allows more than one user to work with the database at the same time.</span></span> <span data-ttu-id="2be9f-124">충돌이 발생하는 경우(예: 현재 사용자가 변경한 것과 동일한 행을 다른 사용자가 변경하고 현재 사용자가 커밋하기 전에 이를 먼저 데이터베이스에 커밋한 경우)에는 충돌 사실과 해결 방법을 제안하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-124">If there are conflicts (for example if another user changed the same row you changed and committed it to the database before you did) you will receive a message telling you of the conflict and offering resolutions.</span></span>  
  
## <a name="undo-changes-using-esc"></a><span data-ttu-id="2be9f-125">Esc 키를 사용하여 변경 취소</span><span class="sxs-lookup"><span data-stu-id="2be9f-125">Undo changes using ESC</span></span>  
 <span data-ttu-id="2be9f-126">변경 내용을 데이터베이스에 커밋하지 않은 경우에만 변경 내용을 실행 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-126">You can only undo a change if it hasn't yet been committed to the database.</span></span> <span data-ttu-id="2be9f-127">레코드에서 포커스를 옮기지 않았거나 레코드에서 포커스를 옮기려 했지만 변경 내용을 커밋할 수 없다는 오류 메시지가 표시되는 경우에는 데이터가 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-127">The data is not committed if you haven't moved off of the record or if once you do move off the record you get an error message indicating the change won't be committed.</span></span> <span data-ttu-id="2be9f-128">이와 같이 변경 내용이 커밋되지 않은 경우 Esc 키를 사용하여 변경 내용을 실행 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-128">If it hasn't been committed you can undo the change by using the ESC key.</span></span>  
  
 <span data-ttu-id="2be9f-129">한 행의 변경 내용을 모두 실행 취소하려면 해당 행에서 편집하지 않은 셀로 이동한 다음 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-129">To undo all changes in a row, move to a cell in that row that you have not edited and press the ESC key.</span></span>  
  
 <span data-ttu-id="2be9f-130">편집한 특정 셀의 변경 내용을 실행 취소하려면 해당 셀로 이동한 다음 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-130">To undo changes to a particular cell that you have edited, move to that cell press the ESC key.</span></span>  
  
## <a name="adding-or-deleting-data-in-the-database"></a><span data-ttu-id="2be9f-131">데이터베이스에서 데이터 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="2be9f-131">Adding or deleting data in the database</span></span>  
 <span data-ttu-id="2be9f-132">데이터베이스 디자인의 작동 방식을 확인하기 위해 데이터베이스에 샘플 데이터를 추가해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-132">To see how your database design is working you may need to add sample data to the database.</span></span> <span data-ttu-id="2be9f-133">이러한 샘플 데이터는 결과 창에 직접 입력하거나 메모장 또는 Excel 같은 다른 프로그램에서 복사하여 결과 창에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-133">You can enter it into the results pane directly or you can copy it from another program, such as notepad or Excel, and paste it into the results pane.</span></span>  
  
 <span data-ttu-id="2be9f-134">결과 창에 행을 복사하여 붙여넣을 수 있을 뿐만 아니라 새 레코드를 추가하거나 기존 레코드를 수정 또는 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-134">In addition to copying rows into the Results pane you can add new records or modify or delete existing ones.</span></span> <span data-ttu-id="2be9f-135">자세한 내용은 [결과 창에서 새 행 추가&#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md), [결과 창에서 행 삭제&#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md) 및 [결과 창에서 행 편집&#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2be9f-135">For more information see [Add New Rows in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md), [Delete Rows in the Results Pane &#40;Visual Database Tools&#41;](delete-rows-in-the-results-pane-visual-database-tools.md), and [Edit Rows in the Results Pane &#40;Visual Database Tools&#41;](edit-rows-in-the-results-pane-visual-database-tools.md).</span></span>  
  
## <a name="tips-for-working-with-null-values-and-empty-cells"></a><span data-ttu-id="2be9f-136">NULL 값 및 빈 셀 사용을 위한 팁</span><span class="sxs-lookup"><span data-stu-id="2be9f-136">Tips for working with NULL values and empty cells</span></span>  
 <span data-ttu-id="2be9f-137">빈 행을 클릭하여 새 레코드를 추가하는 경우 모든 열의 초기 값은 *NULL*입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-137">When you click on an empty row to add a new record, the initial value for all columns is *NULL*.</span></span> <span data-ttu-id="2be9f-138">열에 null 값이 허용되면 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-138">If a column allows null values you can leave it as is.</span></span>  
  
 <span data-ttu-id="2be9f-139">null 이외의 값을 null로 바꾸려면 대문자로 NULL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-139">If you want to replace a non-null value with null, type NULL in capital letters.</span></span> <span data-ttu-id="2be9f-140">그러면 이 단어가 결과 창에 기울임 글꼴로 표시됩니다. 이는 사용자가 입력한 값이 문자열이 아닌 null 값으로 인식됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-140">The Results pane will give the word italic formatting to indicate that it is to be recognized as a null value rather than as a string.</span></span>  
  
 <span data-ttu-id="2be9f-141">"null"이라는 문자열을 입력하려면 이 단어를 따옴표 없이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-141">To type in the string "null" type the letters without quotes.</span></span> <span data-ttu-id="2be9f-142">소문자가 하나라도 포함되어 있으면 그 값은 null 값이 아닌 문자열로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-142">As long as at least one of the letters is in lower case, the value will be treated as a string rather than a null value.</span></span>  
  
 <span data-ttu-id="2be9f-143">이진 데이터 형식의 열에 대한 값은 기본적으로 NULL 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-143">Values for columns with a binary data type will have NULL values by default.</span></span> <span data-ttu-id="2be9f-144">이러한 값은 결과 창에서 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-144">These values can't be changed in the Results pane.</span></span>  
  
 <span data-ttu-id="2be9f-145">null을 사용하는 대신 빈 공백을 입력하려면 기존 텍스트를 삭제하고 다른 셀로 포커스를 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-145">To input an empty space instead of using null, delete the existing text and move off of the cell.</span></span>  
  
## <a name="validating-data"></a><span data-ttu-id="2be9f-146">데이터 유효성 확인</span><span class="sxs-lookup"><span data-stu-id="2be9f-146">Validating data</span></span>  
 <span data-ttu-id="2be9f-147">쿼리 및 뷰 디자이너에서는 열 속성을 기준으로 몇 가지 종류의 데이터에 대한 유효성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-147">The Query and View Designer can validate some kinds of data against the columns properties.</span></span> <span data-ttu-id="2be9f-148">예를 들어, float 데이터 형식의 열에 "abc"를 입력하면 오류가 발생하고 변경 내용이 데이터베이스에 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-148">For example, if you enter "abc" into a column with a float data type, you will receive an error and the change will not be committed to the database.</span></span>  
  
 <span data-ttu-id="2be9f-149">결과 창에서 작업하는 동안 다이어그램 창을 열고 테이블 또는 테이블 반환 개체의 열 이름 위에 커서를 놓으면 열의 데이터 형식을 바로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-149">The quickest way to see the data type of a column when you're in the Results pane is to open the Diagram pane and hover over the name of the column in the table or table-valued object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2be9f-150">결과 창에 표시할 수 있는 텍스트 데이터 형식의 최대 길이는 2,147,483,647입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-150">The maximum length the Results pane can show for a text data type is 2,147,483,647.</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="2be9f-151">결과 집합과 쿼리 정의의 동기화 상태 유지</span><span class="sxs-lookup"><span data-stu-id="2be9f-151">Keeping the results set synchronized with the query definition</span></span>  
 <span data-ttu-id="2be9f-152">쿼리나 뷰의 결과에 대한 작업을 수행하는 동안 결과 창의 레코드가 쿼리 정의와 동기화되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-152">While you're working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the queries definition.</span></span> <span data-ttu-id="2be9f-153">예를 들어, 테이블에서 다섯 개의 열 중 네 개의 열에 대한 쿼리를 실행한 다음 다이어그램 창을 사용하여 다섯 번째 열을 쿼리 정의에 추가하는 경우 이 다섯 번째 열의 데이터는 결과 창에 자동으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-153">For example, if you ran a query for four out of five columns in a table, then used the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the results pane.</span></span> <span data-ttu-id="2be9f-154">결과 창에 새 쿼리 정의가 반영되도록 하려면 쿼리를 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-154">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="2be9f-155">결과 창의 오른쪽 아래 모퉁이에 경고 아이콘과 "쿼리가 변경되었습니다."라는 텍스트가 표시되고 이 창의 왼쪽 위 모퉁이에도 아이콘이 표시되므로 결과 집합과 쿼리 정의가 동기화되지 않은 경우 그 사실을 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-155">You can tell if this happens--an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane and the icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="reconciling-changes-made-by-multiple-users"></a><span data-ttu-id="2be9f-156">여러 사용자가 변경한 내용 조정</span><span class="sxs-lookup"><span data-stu-id="2be9f-156">Reconciling changes made by multiple users</span></span>  
 <span data-ttu-id="2be9f-157">쿼리나 뷰의 결과에 대한 작업을 수행하는 동안 동일한 데이터베이스를 사용하여 작업하는 다른 사용자가 해당 레코드를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-157">While you're working on the results of a query or view it is possible fore the records to be changed by a different user who is also working with the database.</span></span>  
  
 <span data-ttu-id="2be9f-158">이 경우 충돌이 발생한 셀에서 포커스를 옮길 때 해당 사실을 알리는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-158">If this happens you will receive a notice as soon as you move off of the cell with the conflict.</span></span> <span data-ttu-id="2be9f-159">그러면 다른 사용자의 변경 내용을 무시하거나, 다른 사용자의 변경 내용으로 내 결과 창을 업데이트하거나, 충돌하는 변경 내용을 조정하지 않은 채로 결과 창을 계속 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-159">You will then be able to override the other user's change, update your results pane with the other user's change, or keep editing your results pane without reconciling the differences.</span></span> <span data-ttu-id="2be9f-160">충돌하는 변경 내용을 조정하지 않으면 내가 변경한 내용을 데이터베이스에 커밋할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-160">If you choose not to reconcile the differences your changes will not be committed to the database.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="2be9f-161">결과 창의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="2be9f-161">Limitations in the Results pane</span></span>  
  
### <a name="what-can-not-be-updated"></a><span data-ttu-id="2be9f-162">업데이트할 수 없는 항목</span><span class="sxs-lookup"><span data-stu-id="2be9f-162">What can not be updated</span></span>  
 <span data-ttu-id="2be9f-163">다음은 결과 창의 데이터를 사용하여 작업을 성공적으로 수행하는 데 도움이 되는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-163">These tips may help you work successfully with data in the Results pane.</span></span>  
  
-   <span data-ttu-id="2be9f-164">두 개 이상의 테이블이나 뷰의 열이 포함된 쿼리는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-164">Queries that include columns from more than one table or view can't be updated.</span></span>  
  
-   <span data-ttu-id="2be9f-165">데이터베이스 제약 조건에서 허용하는 경우에만 뷰를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-165">Views can only be updated if the database constraints allow it.</span></span>  
  
-   <span data-ttu-id="2be9f-166">저장 프로시저를 통해 반환된 결과는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-166">Results returned by a stored procedure can't be updated.</span></span>  
  
-   <span data-ttu-id="2be9f-167">GROUP BY, DISTINCT 또는 TO XML 절을 사용하는 쿼리나 뷰는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-167">Queries or views using the GROUP BY, DISTINCT, or TO XML clauses are not updatable.</span></span>  
  
-   <span data-ttu-id="2be9f-168">테이블 반환 함수를 통해 반환되는 결과는 다음과 같은 몇 가지 경우에만 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-168">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="2be9f-169">쿼리 식의 결과인 열의 데이터</span><span class="sxs-lookup"><span data-stu-id="2be9f-169">Data in columns that result from an expression in the query.</span></span>  
  
-   <span data-ttu-id="2be9f-170">공급자가 성공적으로 변환하지 못한 데이터</span><span class="sxs-lookup"><span data-stu-id="2be9f-170">Data that was not successfully translated by the provider.</span></span>  
  
### <a name="what-can-not-be-represented-fully"></a><span data-ttu-id="2be9f-171">완전히 표현할 수 없는 항목</span><span class="sxs-lookup"><span data-stu-id="2be9f-171">What can not be represented fully</span></span>  
 <span data-ttu-id="2be9f-172">데이터베이스에서 결과 창으로 반환되는 내용은 현재 사용 중인 데이터 원본의 공급자를 통해 주로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-172">What is returned to the Results pane from the database is greatly controlled by the provider for the data source you are using.</span></span> <span data-ttu-id="2be9f-173">모든 데이터베이스 관리 시스템의 데이터를 결과 창에서 항상 변환할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-173">The Results pane can't always translate the data from all database management systems.</span></span> <span data-ttu-id="2be9f-174">이와 같은 예외적인 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-174">Here are come cases where this is so.</span></span>  
  
-   <span data-ttu-id="2be9f-175">결과 창에서 작업하는 대부분의 사용자에게는 일반적으로 이진 데이터 형식이 유용하지 않으며 이러한 데이터를 다운로드하는 데도 아주 많은 시간이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-175">Binary data types are often not useful for people working in the Results pane and they can take a very long time to download.</span></span> <span data-ttu-id="2be9f-176">따라서 이러한 데이터 형식은 *\<Binary data>* 또는 *Null*로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-176">So they are represented by *\<Binary data>* or *Null*.</span></span>  
  
-   <span data-ttu-id="2be9f-177">경우에 따라 전체 자릿수와 소수 자릿수가 유지되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-177">Precision and scale can not always be preserved.</span></span> <span data-ttu-id="2be9f-178">예를 들어 결과 창에서 전체 자릿수를 27까지 지원하는데</span><span class="sxs-lookup"><span data-stu-id="2be9f-178">For example, the Results pane supports a precision of 27.</span></span> <span data-ttu-id="2be9f-179">데이터의 전체 자릿수가 이보다 큰 형식인 경우 이 데이터는 초과 부분이 잘리거나 *\<Unable to read data>* 으로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2be9f-179">If data is of a data type with a greater precision, the data may be truncated or may be represented by *\<Unable to read data>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be9f-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2be9f-180">See Also</span></span>  
 <span data-ttu-id="2be9f-181">[Visual Database Tools를 &#40;쿼리를 사용 하 여 기본 작업을 수행&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2be9f-181">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2be9f-182">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="2be9f-182">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
