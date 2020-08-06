---
title: 결과 창(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- synchronization [SQL Server], query results with definition
- displaying query results in grid
- grid showing query results [SQL Server]
- showing query results in grid
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- viewing query results
- queries [SQL Server], results
- Results pane
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: f0db32336931f74777be56befcde9501dc484b69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639202"
---
# <a name="results-pane-visual-database-tools"></a><span data-ttu-id="6fa0c-102">결과 창(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6fa0c-102">Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="6fa0c-103">결과 창은 가장 최근에 실행한 SELECT 쿼리의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-103">The Results pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="6fa0c-104">다른 쿼리 형식의 결과는 메시지 상자에 표시됩니다. 결과 창을 열려면 쿼리를 열거나 만듭니다. 테이블의 데이터를 반환해도 결과 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-104">(The results of other query types are displayed in message boxes.) To open the results pane, open or create a query or view or return a table's data.</span></span> <span data-ttu-id="6fa0c-105">결과 창이 기본적으로 표시되지 않으면 **쿼리 디자이너** 메뉴에서 **창**을 가리킨 다음 **결과**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-105">If the results pane doesn't show by default, from the **Query Designer** menu, point to **Pane**, and then click **Results**.</span></span>  
  
## <a name="what-you-can-do-in-the-results-pane"></a><span data-ttu-id="6fa0c-106">결과 창에서 수행할 수 있는 작업</span><span class="sxs-lookup"><span data-stu-id="6fa0c-106">What You Can Do in the Results Pane</span></span>  
  
-   <span data-ttu-id="6fa0c-107">가장 최근에 실행한 SELECT 쿼리에 대한 결과 집합을 스프레드시트 모양의 표 형태로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-107">View the result set for the most recently executed SELECT query in a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="6fa0c-108">단일 테이블이나 뷰의 데이터를 표시하는 쿼리 또는 뷰에 대해 결과 집합의 개별 열에 있는 값을 편집하거나, 새 행을 추가하거나, 기존 행을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-108">For queries or views that show data from a single table or view, you can edit the values in individual columns in the result set, add new rows, and delete existing rows.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="6fa0c-109">결과 창의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="6fa0c-109">Limitations in the Results Pane</span></span>  
  
-   <span data-ttu-id="6fa0c-110">테이블 반환 함수를 통해 반환되는 결과는 다음과 같은 몇 가지 경우에만 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-110">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="6fa0c-111">두 개 이상의 테이블 또는 뷰의 열이 포함된 쿼리나 뷰는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-111">Queries or views that include columns from more than one table or view cannot be updated.</span></span>  
  
-   <span data-ttu-id="6fa0c-112">저장 프로시저를 통해 반환된 결과는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-112">Results returned by a stored procedure cannot be updated.</span></span>  
  
-   <span data-ttu-id="6fa0c-113">GROUP BY 또는 DISTINCT 절을 사용하는 쿼리나 뷰는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-113">Queries or views using the GROUP BY or DISTINCT clauses are not updatable.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="6fa0c-114">결과 창에서 탐색</span><span class="sxs-lookup"><span data-stu-id="6fa0c-114">Navigating in the Results Pane</span></span>  
 <span data-ttu-id="6fa0c-115">결과 창의 아래쪽에 있는 탐색 모음을 사용하면 레코드를 빠르게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-115">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="6fa0c-116">이 탐색 모음에는 첫 번째 레코드와 마지막 레코드, 다음 레코드와 이전 레코드 또는 특정 레코드로 이동하기 위한 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-116">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="6fa0c-117">특정 레코드로 이동하려면 탐색 모음의 입력란에 원하는 행 번호를 입력한 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-117">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="6fa0c-118">쿼리 및 뷰 디자이너에서 바로 가기 키를 사용하는 방법에 대한 자세한 내용은 [쿼리 및 뷰 디자이너에서 탐색&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-118">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="6fa0c-119">결과 집합과 쿼리 정의의 동기화 상태 유지</span><span class="sxs-lookup"><span data-stu-id="6fa0c-119">Keeping the Results Set Synchronized with the Query Definition</span></span>  
 <span data-ttu-id="6fa0c-120">쿼리나 뷰의 결과에 대한 작업을 수행하는 동안 결과 창의 레코드가 쿼리 정의와 동기화되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-120">While you are working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the query's definition.</span></span> <span data-ttu-id="6fa0c-121">예를 들어, 테이블에서 다섯 개의 열 중 네 개의 열에 대한 쿼리를 실행한 다음 다이어그램 창을 사용하여 다섯 번째 열을 쿼리 정의에 추가하는 경우 이 다섯 번째 열의 데이터는 결과 창에 자동으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-121">For example, if you run a query for four out of five columns in a table, and then use the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the Results pane.</span></span> <span data-ttu-id="6fa0c-122">결과 창에 새 쿼리 정의가 반영되도록 하려면 쿼리를 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-122">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="6fa0c-123">쿼리를 변경하면 결과 창의 오른쪽 아래에 경고 아이콘과 "쿼리가 변경되었습니다."라는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-123">If a query changes, an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane.</span></span> <span data-ttu-id="6fa0c-124">이 창의 왼쪽 위에도 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-124">The icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa0c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6fa0c-125">See Also</span></span>  
 <span data-ttu-id="6fa0c-126">[Visual Database Tools를 &#40;쿼리 만들기&#41;](create-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fa0c-126">[Create Queries &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fa0c-127">[Visual Database Tools를 &#40;쿼리 실행&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fa0c-127">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fa0c-128">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fa0c-128">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fa0c-129">[다이어그램 창 &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fa0c-129">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fa0c-130">[조건 창 &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fa0c-130">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6fa0c-131">결과 창에서 데이터 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6fa0c-131">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
