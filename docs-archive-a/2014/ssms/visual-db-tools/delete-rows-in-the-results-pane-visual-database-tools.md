---
title: 결과 창에서 행 삭제(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a82a7232559cd8761ae3af66a9accc0bc307552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648748"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="42d6b-102">결과 창에서 행 삭제(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="42d6b-102">Delete Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="42d6b-103">데이터베이스에서 레코드를 삭제하려면 결과 창에서 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-103">Delete rows in the Results pane if you want to delete records in the database.</span></span> <span data-ttu-id="42d6b-104">삭제 쿼리를 사용하면 행 전체를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-104">If you want to delete all of the rows you can use a Delete query.</span></span> <span data-ttu-id="42d6b-105">자세한 내용은 [삭제 쿼리 만들기&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42d6b-105">For more information see [Create Delete Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="42d6b-106">결과 창에서 행을 제거만 하려면 쿼리 조건을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-106">If you only want to remove rows from the Results pane, change the criteria for the query.</span></span> <span data-ttu-id="42d6b-107">자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42d6b-107">For more information see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
### <a name="to-delete-a-row-or-rows"></a><span data-ttu-id="42d6b-108">하나 이상의 행을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="42d6b-108">To delete a row or rows</span></span>  
  
1.  <span data-ttu-id="42d6b-109">결과 창에서 삭제할 행 왼쪽에 있는 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-109">Select the box to the left of the row or rows you want to delete in the Results pane.</span></span>  
  
2.  <span data-ttu-id="42d6b-110">Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-110">Press DELETE.</span></span>  
  
3.  <span data-ttu-id="42d6b-111">삭제 확인 메시지가 대화 상자에 나타나면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-111">In the message box asking for confirmation, click **Yes**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="42d6b-112">이런 방법으로 삭제하는 행은 데이터베이스에서 영구적으로 제거되므로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-112">Rows you delete in this way are permanently removed from the database and cannot be recalled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42d6b-113">데이터베이스에서 선택한 행 중 삭제할 수 없는 행이 하나라도 있으면 나머지 행도 삭제되지 않습니다. 이 경우 삭제할 수 없는 행에 대한 정보가 메시지로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42d6b-113">If any of the selected rows can't be deleted from the database, none of them will be deleted and you will receive a message telling you which rows can't be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d6b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42d6b-114">See Also</span></span>  
 <span data-ttu-id="42d6b-115">[Visual Database Tools&#41;&#40;삭제 쿼리를 만듭니다.](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="42d6b-115">[Create Delete Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="42d6b-116">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="42d6b-116">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
