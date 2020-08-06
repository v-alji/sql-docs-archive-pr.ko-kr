---
title: 쿼리 및 뷰 디자이너 열기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- opening View Designer
- View Designer, opening
- Query Designer [SQL Server], opening
- opening Query Designer
ms.assetid: b473f258-d53c-41c0-9ad9-528a2ff141f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a36a0a9f014759269517a5774167f84c19b0b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651417"
---
# <a name="open-the-query-and-view-designer-visual-database-tools"></a><span data-ttu-id="63782-102">쿼리 및 뷰 디자이너 열기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="63782-102">Open the Query and View Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="63782-103">쿼리 및 뷰 디자이너는 뷰의 정의를 열거나, 쿼리 또는 뷰의 결과를 표시하거나, 쿼리를 만들거나 열 때 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="63782-103">The Query and View Designer opens when you open the definition of a view, show the results for a query or view, or create or open a query.</span></span> <span data-ttu-id="63782-104">이 디자이너는 네 개의 개별 창으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63782-104">It consists of four separate panes:</span></span>  
  
-   <span data-ttu-id="63782-105">다이어그램 창은 데이터 연결에서 선택한 테이블 또는 테이블 반환 개체를 그래픽으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="63782-105">The Diagram pane presents a graphic display of the tables or table-valued objects you have selected from the data connection.</span></span> <span data-ttu-id="63782-106">또한 이들 사이의 조인 관계도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63782-106">It also shows any join relationships among them.</span></span>  
  
-   <span data-ttu-id="63782-107">조건 창에서 스프레드시트 모양의 표 형태에 선택한 항목을 입력하여 표시할 데이터 열, 결과 정렬 방법, 선택할 행 등의 쿼리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63782-107">The Criteria pane allows you to specify query options - such as which data columns to display, how to order the results, and what rows to select - by entering your choices into a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="63782-108">SQL 창을 사용하여 고유한 SQL 문을 만들거나 조건 창 및 다이어그램 창을 사용하여 문을 만들 수 있습니다. 조건 창이나 다이어그램 창을 사용해도 SQL 문은 SQL 창에 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="63782-108">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="63782-109">쿼리를 작성할 때 SQL 창은 읽기 쉽도록 자동으로 업데이트되고 서식이 다시 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="63782-109">As you build your query, the SQL pane automatically updates and reformats to be easily read.</span></span>  
  
-   <span data-ttu-id="63782-110">결과 창은 가장 최근에 실행한 SELECT 쿼리의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63782-110">The Results pane shows the results of the most recently executed Select query.</span></span> <span data-ttu-id="63782-111">다른 쿼리 형식의 결과는 메시지 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63782-111">(The results of other query types are displayed in message boxes.)</span></span>  
  
-   <span data-ttu-id="63782-112">이러한 창은 쿼리와 뷰 작업에 모두 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63782-112">These panes are useful for working with both queries and views.</span></span>  
  
-   <span data-ttu-id="63782-113">뷰나 쿼리를 열면 창의 일부 또는 전체가 함께 열립니다.</span><span class="sxs-lookup"><span data-stu-id="63782-113">When you open a view or query some or all of the panes open with it.</span></span> <span data-ttu-id="63782-114">이때 열리는 창은 **옵션** 대화 상자의 설정과 현재 연결되어 있는 데이터베이스 관리 시스템에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="63782-114">Which ones open depend on the settings in the **Options** dialog box and what database management system you're connected to.</span></span> <span data-ttu-id="63782-115">기본적으로 네 개의 창이 모두 열립니다.</span><span class="sxs-lookup"><span data-stu-id="63782-115">The default is that all four open.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-a-view"></a><span data-ttu-id="63782-116">뷰의 쿼리 및 뷰 디자이너를 열려면</span><span class="sxs-lookup"><span data-stu-id="63782-116">To open the Query and View Designer for a view</span></span>  
  
1.  <span data-ttu-id="63782-117">개체 탐색기에서 열려는 뷰를 마우스 오른쪽 단추로 클릭한 다음 **디자인** 또는 **뷰 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63782-117">In Object Explorer, right-click the view you want to open and click **Design** or **Open View**.</span></span>  
  
     <span data-ttu-id="63782-118">**디자인**을 선택한 경우 **옵션** 대화 상자에서 선택한 옵션에 따라 쿼리 및 뷰 디자이너 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="63782-118">If you chose **Design**, the Query and View Designer panes open as dictated by the options selected in the **Options** dialog box.</span></span> <span data-ttu-id="63782-119">**뷰 열기**를 선택한 경우에는 기본적으로 결과 창만 열립니다.</span><span class="sxs-lookup"><span data-stu-id="63782-119">If you chose **Open View**, only the Results pane opens by default.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-an-existing-query"></a><span data-ttu-id="63782-120">기존 쿼리에 대해 쿼리 및 뷰 디자이너를 열려면</span><span class="sxs-lookup"><span data-stu-id="63782-120">To open the Query and View Designer for an existing query</span></span>  
  
1.  <span data-ttu-id="63782-121">솔루션 탐색기에서 **쿼리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="63782-121">In Solution Explorer, expand the **Queries** folder.</span></span>  
  
2.  <span data-ttu-id="63782-122">열려는 쿼리를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63782-122">Double-click the query you want to open.</span></span>  
  
3.  <span data-ttu-id="63782-123">해당 쿼리 문을 강조 표시하고 강조 표시된 영역을 마우스 오른쪽 단추로 클릭한 다음 **편집기에서 쿼리 디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="63782-123">Highlight the query statement(s), right-click the highlighted area and click **Design Query in Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63782-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63782-124">See Also</span></span>  
 <span data-ttu-id="63782-125">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="63782-125">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="63782-126">쿼리 및 뷰 디자이너 도구&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="63782-126">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](query-and-view-designer-tools-visual-database-tools.md)  
  
  
