---
title: 결과 창에서 새 행 추가(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3137da106279e09305261c6c7cb7fd06d254b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648760"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="2e409-102">결과 창에서 새 행 추가(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2e409-102">Add New Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="2e409-103">데이터를 직접 입력하거나 메모장 또는 Excel 같은 다른 프로그램에서 복사하여 붙여넣는 방식으로 새 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-103">You can add new data either by typing it in or by pasting it from another program such as Notepad or Excel.</span></span> <span data-ttu-id="2e409-104">붙여넣을 행은 행이 들어갈 테이블과 열 수 및 형식이 똑같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-104">A row to be pasted must have exactly the same number and types of columns as the table into which you are pasting.</span></span> <span data-ttu-id="2e409-105">결과 창에 여러 행을 한 번에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-105">You can paste multiple rows into the Results pane at once.</span></span>  
  
 <span data-ttu-id="2e409-106">데이터를 입력하는 방법에 대한 자세한 내용은 [결과 업데이트 규칙&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e409-106">For information about how to enter data see [Rules for Updating Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-add-a-new-data-row"></a><span data-ttu-id="2e409-107">새 데이터 행을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2e409-107">To add a new data row</span></span>  
  
1.  <span data-ttu-id="2e409-108">결과 창의 아래쪽에 새 데이터 행을 추가할 수 있는 빈 행으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-108">Navigate to the bottom of the Results pane, where a blank row is available for adding a new data row.</span></span>  
  
     <span data-ttu-id="2e409-109">모든 열의 초기 값은 *NULL*입니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-109">The initial values for all columns will be *NULL*.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="2e409-110">결과 창의 아래쪽에 있는 탐색 모음을 사용하면 비어 있는 첫째 행으로 직접 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-110">To go directly to the first empty row use the navigation bar at the bottom of the Results pane.</span></span>  
  
2.  <span data-ttu-id="2e409-111">클립보드에서 행을 붙여넣는 경우 왼쪽에 있는 단추를 클릭하여 새 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-111">If you are pasting rows from the Clipboard, select the new row by clicking the button to its left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e409-112">붙여넣을 행이 데이터베이스에 하나 이상 커밋되지 않으면 커밋할 수 없는 행에 대한 정보가 메시지로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-112">If one or more of the rows you're pasting can't be committed to the database you will receive a message telling you which row(s) couldn't be committed.</span></span>  
  
3.  <span data-ttu-id="2e409-113">새 행에 데이터를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-113">Enter the data for the new row.</span></span> <span data-ttu-id="2e409-114">붙여 넣으려면 **편집** 메뉴에서 **붙여넣기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-114">If you are pasting, choose **Paste** from the **Edit** menu.</span></span>  
  
4.  <span data-ttu-id="2e409-115">해당 행에서 포커스를 옮기면 행이 데이터베이스에 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-115">Leave that row to commit it to the database.</span></span>  
  
 <span data-ttu-id="2e409-116">행을 저장할 때 오류가 발생하면 쿼리 및 뷰 디자이너에 오류 메시지가 나타나고 편집 중이던 행으로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-116">If an error occurs when you save the row the Query and View Designer displays a message and then returns you to the row you were editing.</span></span> <span data-ttu-id="2e409-117">그런 다음 아래의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-117">You can then:</span></span>  
  
-   <span data-ttu-id="2e409-118">해당 행을 다시 편집하여 오류를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-118">Resolve the error by making further edits in the row.</span></span>  
  
-   <span data-ttu-id="2e409-119">Esc 키를 눌러 편집을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-119">Cancel the edit by pressing ESC.</span></span> <span data-ttu-id="2e409-120">변경한 셀에서 Esc 키를 누르면 해당 셀에 대한 변경이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-120">If you press ESC while in a cell that you changed, the changes for that cell are canceled.</span></span> <span data-ttu-id="2e409-121">변경하지 않은 셀에서 Esc 키를 누르면 행 전체에 대한 변경이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e409-121">If you press ESC while in a cell you have not changed, the changes for the entire row are canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e409-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e409-122">See Also</span></span>  
 <span data-ttu-id="2e409-123">[결과 창에서 데이터 작업 &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2e409-123">[Work with Data in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2e409-124">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="2e409-124">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
