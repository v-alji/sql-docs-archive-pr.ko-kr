---
title: 쿼리 및 뷰 디자이너 도구(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29bd3fa9e171551197927aae0d1bc00446df6e7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735831"
---
# <a name="query-and-view-designer-tools-visual-database-tools"></a><span data-ttu-id="916a6-102">쿼리 및 뷰 디자이너 도구(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="916a6-102">Query and View Designer Tools (Visual Database Tools)</span></span>
  <span data-ttu-id="916a6-103">쿼리, 뷰, 인라인 함수 또는 단일 문 저장 프로시저를 디자인할 때 사용하는 디자이너는 다이어그램 창, 조건 창, SQL 창 및 결과 창으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-103">When you design a query, view, in-line function, or single-statement stored procedure, the designer you use consists of four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span>  
  
 <span data-ttu-id="916a6-104">![쿼리 디자이너](../../database-engine/media//vs-queryviewdsgpanes.gif "쿼리 디자이너")</span><span class="sxs-lookup"><span data-stu-id="916a6-104">![Query Designer](../../database-engine/media//vs-queryviewdsgpanes.gif "Query Designer")</span></span>  
  
-   <span data-ttu-id="916a6-105">다이어그램 창은 쿼리하는 테이블과 기타 테이블 반환 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-105">The Diagram pane displays the tables and other table-valued objects that you are querying.</span></span> <span data-ttu-id="916a6-106">각 사각형은 테이블이나 테이블 반환 개체를 나타내며 사용 가능한 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-106">Each rectangle represents a table or table-valued object and shows the available data columns.</span></span> <span data-ttu-id="916a6-107">조인은 사각형 사이에 선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-107">Joins are indicated by lines between the rectangles.</span></span> <span data-ttu-id="916a6-108">자세한 내용은 [다이어그램 창&#40;Visual Database Tools&#41;](visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916a6-108">For more information, see [Diagram Pane &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="916a6-109">조건 창에는 표시할 데이터 열, 선택할 행, 행을 그룹화하는 방법 등의 옵션을 지정하는 스프레드시트 모양의 표가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-109">The Criteria pane contains a spreadsheet-like grid in which you specify options, such as which data columns to display, what rows to select, how to group rows, and so on.</span></span> <span data-ttu-id="916a6-110">자세한 내용은 [조건 창&#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916a6-110">For more information, see [Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="916a6-111">SQL 창은 쿼리 또는 뷰에 대한 SQL 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-111">The SQL pane displays the SQL statement for the query or view.</span></span> <span data-ttu-id="916a6-112">디자이너에서 만든 SQL 문을 편집하거나 사용자만의 SQL 문을 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-112">You can edit the SQL statement created by the Designer or you can enter your own SQL statement.</span></span> <span data-ttu-id="916a6-113">SQL 창은 통합 쿼리와 같이 다이어그램 창이나 조건 창을 통해 만들 수 없는 SQL 문을 입력하는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-113">It is particularly useful for entering SQL statements that cannot be created using the Diagram and Criteria panes, such as union queries.</span></span> <span data-ttu-id="916a6-114">자세한 내용은 [SQL 창&#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916a6-114">For more information, see [SQL Pane &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="916a6-115">결과 창은 쿼리 또는 뷰에서 검색한 데이터가 있는 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-115">The Results pane shows a grid with data retrieved by the query or view.</span></span> <span data-ttu-id="916a6-116">쿼리 및 뷰 디자이너의 결과 창에서는 가장 최근에 실행한 SELECT 쿼리의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-116">In the Query and View Designer, the pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="916a6-117">표의 셀에 들어 있는 값을 편집하여 데이터베이스를 수정할 수 있으며 행을 추가하거나 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-117">You can modify the database by editing values in the cells of the grid, and you can add or delete rows.</span></span> <span data-ttu-id="916a6-118">자세한 내용은 [결과 창&#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916a6-118">For more information, see [Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="916a6-119">다이어그램 창에서 열을 선택하여 표시하거나 조건 창에 해당 열을 입력하거나 SQL 창에서 SQL 문의 일부로 열을 만들어 지정하는 등 어느 창에서나 쿼리 또는 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-119">You can create a query or view by working in any of the panes: you can specify a column to display by choosing it in the Diagram pane, entering it into the Criteria pane, or making it part of the SQL statement in the SQL pane.</span></span>  
  
## <a name="displaying-and-hiding-panes"></a><span data-ttu-id="916a6-120">창 표시 및 숨기기</span><span class="sxs-lookup"><span data-stu-id="916a6-120">Displaying and Hiding Panes</span></span>  
 <span data-ttu-id="916a6-121">창을 숨기거나 보이지 않는 창을 표시하려면 디자인 화면을 마우스 오른쪽 단추로 클릭하고 **창**을 가리킨 다음 창 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-121">To hide a pane or display a pane that is not visible, right-click the design surface, point to **Pane**, and then click the name of the pane.</span></span> <span data-ttu-id="916a6-122">쿼리 및 뷰 디자이너가 쿼리 디자이너 모드로 열리면 **결과** 창을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="916a6-122">If the Query and View Designer is opened in Query Designer mode, the **Results** pane is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916a6-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="916a6-123">See Also</span></span>  
 <span data-ttu-id="916a6-124">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="916a6-124">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="916a6-125">[Visual Database Tools를 &#40;쿼리 및 뷰 디자이너를 엽니다&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="916a6-125">[Open the Query and View Designer &#40;Visual Database Tools&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="916a6-126">SQL 편집기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="916a6-126">SQL Editor &#40;Visual Database Tools&#41;</span></span>](sql-editor-visual-database-tools.md)  
  
  
