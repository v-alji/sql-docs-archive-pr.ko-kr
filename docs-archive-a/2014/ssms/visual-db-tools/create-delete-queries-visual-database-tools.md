---
title: 삭제 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: stevestein
ms.author: sstein
ms.openlocfilehash: a76c3aaef623365e419f40f3058308f6217d75d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660794"
---
# <a name="create-delete-queries-visual-database-tools"></a><span data-ttu-id="6ac8e-102">삭제 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6ac8e-102">Create Delete Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="6ac8e-103">삭제 쿼리를 사용하면 테이블에서 모든 행을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-103">You can delete all rows in a table by using a Delete query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ac8e-104">테이블에서 모든 행을 삭제하면 테이블에서 데이터가 지워지지만 테이블 자체가 삭제되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-104">Deleting all rows from a table clears the data in the table but does not delete the table itself.</span></span> <span data-ttu-id="6ac8e-105">데이터베이스에서 테이블을 삭제하려면 개체 탐색기에서 테이블을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-105">To delete a table from a database, right-click the table in Object Explorer and click **Delete**.</span></span>  
  
 <span data-ttu-id="6ac8e-106">삭제 쿼리를 만들면 행을 삭제하는 데 사용할 수 있는 옵션이 반영되도록 조건 창이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-106">When you create a Delete query, the Criteria pane changes to reflect the options available for deleting rows.</span></span> <span data-ttu-id="6ac8e-107">삭제 쿼리에는 데이터를 표시하지 않으므로 출력, 정렬 기준 및 정렬 순서 열이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-107">Because you do not display data in a Delete query, the Output, Sort By, and Sort Order columns are removed.</span></span> <span data-ttu-id="6ac8e-108">또한, 삭제할 개별 열을 지정할 수 없으므로 테이블이나 테이블 반환 개체를 나타내는 사각형의 열 이름 옆에 있는 확인란이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-108">In addition, the check boxes next to the column names in the rectangle representing the table or table-valued object are removed because you cannot specify individual columns to delete.</span></span>  
  
 <span data-ttu-id="6ac8e-109">쿼리 및 뷰 디자이너에서 행을 하나라도 삭제할 수 없으면 다른 행도 함께 삭제되지 않으며 데이터베이스에서 삭제할 수 없는 정보가 포함된 행을 알리는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-109">If the Query and View Designer can't delete one or more of the rows none of them will be deleted and you will receive a message telling you which row(s) contain information that can't be deleted from the database.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6ac8e-110">삭제 쿼리의 실행 동작을 취소할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-110">You cannot undo the action of executing a Delete query.</span></span> <span data-ttu-id="6ac8e-111">문제가 발생할 경우에 대비하여 삭제 쿼리를 실행하기 전에 데이터를 백업하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-111">As a precaution, back up your data before executing a Delete query.</span></span>  
  
### <a name="to-create-a-delete-query"></a><span data-ttu-id="6ac8e-112">삭제 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6ac8e-112">To create a Delete query</span></span>  
  
1.  <span data-ttu-id="6ac8e-113">행을 삭제하려는 테이블을 다이어그램 창에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-113">Add the table to delete rows from to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="6ac8e-114">**쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-114">From the **Query Designer** menu, point to **Change Type**, and then click **Delete**.</span></span> <span data-ttu-id="6ac8e-115">**참고** 삭제 쿼리를 시작할 때 다이어그램 창에 두 개 이상의 테이블이 표시되어 있으면 행을 삭제할 테이블의 이름을 지정하라는 메시지가 쿼리 및 뷰 디자이너의 [테이블 삭제 대화 상자](visual-database-tools.md) 에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-115">**Note** If more than one table is displayed in the Diagram pane when you start the Delete query, the Query and View Designer displays the [Delete Table Dialog Box](visual-database-tools.md) to prompt you for the name of the table to delete rows from.</span></span>  
  
 <span data-ttu-id="6ac8e-116">삭제 쿼리를 실행해도 [결과 창](results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-116">When you execute the Delete query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="6ac8e-117">대신, 삭제한 행의 수를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ac8e-117">Instead, a message appears indicating how many rows were deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac8e-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ac8e-118">See Also</span></span>  
 <span data-ttu-id="6ac8e-119">[Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6ac8e-119">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6ac8e-120">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6ac8e-120">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
