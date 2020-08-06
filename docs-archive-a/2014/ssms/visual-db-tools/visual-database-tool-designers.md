---
title: Visual Database Tools 디자이너 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a307a0a82aa02e7197189ca6cfc9ba70a3fea33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647420"
---
# <a name="visual-database-tool-designers"></a><span data-ttu-id="b9579-102">Visual Database Tools 디자이너</span><span class="sxs-lookup"><span data-stu-id="b9579-102">Visual Database Tool Designers</span></span>
  <span data-ttu-id="b9579-103">Visual Database Tools는 데이터 원본 작업을 수행하는 데 사용할 수 있는 여러 가지 디자인 도구 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-103">The Visual Database Tools are a combination of design tools you can use to work with a data source.</span></span> <span data-ttu-id="b9579-104">이러한 도구를 사용하여 쿼리를 만들고, 데이터베이스 구조를 디자인하거나 수정하고, 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-104">You can use them to create queries, design or modify a database structure, or update data.</span></span> <span data-ttu-id="b9579-105">여기에 포함된 도구는 데이터베이스 다이어그램 디자이너, 테이블 디자이너, 쿼리 및 뷰 디자이너입니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-105">The tools are Database Diagram Designer, Table Designer, and Query and View Designer.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="b9579-106">속성 창</span><span class="sxs-lookup"><span data-stu-id="b9579-106">Properties Window</span></span>  
 <span data-ttu-id="b9579-107">속성 창은 Visual Database Tools에만 있는 특별한 기능은 아니지만 이 창을 통해 여러 가지 항목을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-107">The properties window is not specific to Visual Database Tools, but it is where many modifications can be made.</span></span> <span data-ttu-id="b9579-108">여기에는 테이블 등과 같이 현재 선택된 항목의 속성이 표시되고, 이 창을 사용하여 이러한 속성을 편집할 수 있습니다. 편집할 수 있는 내용은 속성 이름에서 열의 데이터 정렬에 이르기까지 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-108">It shows the properties for the item currently selected (like a table) and allows you to edit those properties (everything from the properties name to the collation of a column).</span></span> <span data-ttu-id="b9579-109">속성 창에는 표시되지만 다른 도구를 사용해야만 편집할 수 있는 속성도 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-109">Some properties can be seen in the properties window but must be modified in a different tool.</span></span>  
  
## <a name="database-diagram-designer"></a><span data-ttu-id="b9579-110">데이터베이스 다이어그램 디자이너</span><span class="sxs-lookup"><span data-stu-id="b9579-110">Database Diagram Designer</span></span>  
 <span data-ttu-id="b9579-111">데이터베이스 다이어그램 디자이너에는 데이터베이스의 테이블 및 관계를 시각적인 방식으로 만들고, 편집하고, 표시하는 데 사용할 수 있는 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-111">Database Diagram Designer provides a window where you can visually create, edit, and show the tables and relationships in a database.</span></span>  
  
 <span data-ttu-id="b9579-112">데이터베이스 다이어그램 디자이너를 표시하려면 기존 다이어그램을 열거나 개체 탐색기에서 데이터베이스 노드를 마우스 오른쪽 단추로 클릭한 다음 드롭다운 메뉴에서 **새 데이터베이스 다이어그램** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-112">To display Database Diagram Designer, open an existing diagram or right-click the Database node in Object Explorer and choose **New Database Diagram** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="b9579-113">이 디자이너를 열면 주 메뉴에 **데이터베이스 다이어그램** 메뉴가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-113">Once the designer is open, the **Database Diagram** menu appears in the main menu.</span></span> <span data-ttu-id="b9579-114">이 메뉴를 통해 디자이너의 특정 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-114">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9579-115">이 디자이너에는 Microsoft SQL Server 데이터베이스가 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-115">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="b9579-116">이 버전의 Visual Database Tools는 Microsoft SQL Server 버전 7 및 이전 버전을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-116">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="table-designer"></a><span data-ttu-id="b9579-117">테이블 디자이너</span><span class="sxs-lookup"><span data-stu-id="b9579-117">Table Designer</span></span>  
 <span data-ttu-id="b9579-118">테이블 디자이너는 연결된 Microsoft SQL Server 데이터베이스의 단일 테이블을 디자인하고 시각화할 수 있게 하는 비주얼 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-118">Table Designer is a visual tool allowing you to design and visualize a single table in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="b9579-119">테이블 디자이너에는 두 개의 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-119">Table Designer has two panes.</span></span> <span data-ttu-id="b9579-120">위쪽 영역에는 표 형태가 표시되고, 표 형태의 각 행에는 데이터베이스 열에 대한 설명이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-120">The upper area shows a grid; each row of the grid describes one database column.</span></span> <span data-ttu-id="b9579-121">각 데이터베이스 열의 표 형태에는 기본 특성인 열 이름, 데이터 형식 및 null 허용 설정이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-121">For each database column, the grid displays its fundamental attributes: column name, data type, and nulls-allowed setting.</span></span>  
  
 <span data-ttu-id="b9579-122">테이블 디자이너의 아래쪽 영역인 열 속성 탭에는 위쪽 영역에서 선택한 열에 대한 추가 특성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-122">The lower area of Table Designer, the Column Properties tab, shows additional attributes for whichever column is highlighted in the upper area.</span></span>  
  
 <span data-ttu-id="b9579-123">테이블 디자이너에서 표 형식 섹션을 마우스 오른쪽 단추로 클릭하여 대화 상자를 열고 이 대화 상자를 통해 테이블의 관계, 제약 조건, 인덱스, 키 등을 만들거나 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-123">From Table Designer, you can also right-click in the grid section to access dialog boxes through which you can create and modify relationships, constraints, indexes, and keys for the table.</span></span>  
  
 <span data-ttu-id="b9579-124">테이블 디자이너를 표시하려면 기존 테이블을 열거나 개체 탐색기에서 **테이블** 노드를 마우스 오른쪽 단추로 클릭한 다음 드롭다운 메뉴에서 **새 테이블 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-124">To display Table Designer, open an existing table, or right-click the **Tables** node in Object Explorer, and choose **Add New Table** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="b9579-125">이 디자이너를 열면 주 메뉴에 테이블 디자이너 메뉴가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-125">Once the designer is open, the Table Designer menu appears in the main menu.</span></span> <span data-ttu-id="b9579-126">이 메뉴를 통해 디자이너의 특정 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-126">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9579-127">이 디자이너에는 Microsoft SQL Server 데이터베이스가 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-127">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="b9579-128">이 버전의 Visual Database Tools는 Microsoft SQL Server 버전 7 및 이전 버전을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-128">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="query-and-view-designer"></a><span data-ttu-id="b9579-129">쿼리 및 뷰 디자이너</span><span class="sxs-lookup"><span data-stu-id="b9579-129">Query and View Designer</span></span>  
 <span data-ttu-id="b9579-130">쿼리 및 뷰 디자이너는 매우 비슷한 방식으로 작동하는 두 개의 도구로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-130">Query and View designer is actually two tools that work in very similar ways.</span></span> <span data-ttu-id="b9579-131">이 두 도구 사이의 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-131">Some of the major differences are:</span></span>  
  
-   <span data-ttu-id="b9579-132">뷰는 데이터베이스와 함께 저장되는 반면, 쿼리는 Visual Studio 데이터베이스 프로젝트와 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-132">Views are saved with the database while a query is saved with a Visual Studio database project.</span></span>  
  
-   <span data-ttu-id="b9579-133">쿼리 디자이너는 거의 모든 데이터 원본과 함께 사용할 수 있는 반면, 뷰 디자이너는 SQL Server에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-133">Query Designer works with nearly any data source, where View Designer works only with SQL Server.</span></span>  
  
-   <span data-ttu-id="b9579-134">쿼리 디자이너를 사용하면 SELECT, INSERT, UPDATE 및 DELETE DML 문을 디자인할 수 있는 반면, 뷰에는 SELECT 문만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-134">Query Designer allows you to design SELECT, INSERT, UPDATE and DELETE DML statements, while views can only contain SELECT statements.</span></span>  
  
### <a name="view-designer"></a><span data-ttu-id="b9579-135">뷰 디자이너</span><span class="sxs-lookup"><span data-stu-id="b9579-135">View Designer</span></span>  
 <span data-ttu-id="b9579-136">뷰 디자이너를 사용하면 현재 연결되어 있는 Microsoft SQL Server 데이터베이스에서 기존의 뷰를 디자인하고 시각화하거나 새 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-136">View Designer allows you to design and visualize an existing view or create a new one in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="b9579-137">뷰 디자이너에는 다이어그램 창, 조건 창, SQL 창, 결과 창이라는 네 가지 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-137">View Designer has four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span> <span data-ttu-id="b9579-138">이러한 개별 창에 대한 자세한 내용은 [쿼리 및 뷰 디자이너 도구&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9579-138">For more detailed information on each of these panes, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="b9579-139">뷰 디자이너를 표시하려면 기존 뷰를 열거나 개체 탐색기에서 **뷰** 노드를 마우스 오른쪽 단추로 클릭한 다음 드롭다운 메뉴에서 **새 뷰 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-139">To display View Designer, open an existing view or right-click the **View** node in Object Explorer and choose **Add New View** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="b9579-140">이 디자이너를 열면 주 메뉴에 **쿼리 디자이너** 메뉴가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-140">Once the designer is open, the **Query Designer** menu appears in the main menu.</span></span> <span data-ttu-id="b9579-141">이 메뉴를 통해 디자이너의 특정 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-141">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9579-142">이 디자이너에는 Microsoft SQL Server 데이터베이스가 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-142">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="b9579-143">이 버전의 Visual Database Tools는 Microsoft SQL Server 버전 7 및 이전 버전을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9579-143">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9579-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9579-144">See Also</span></span>  
 <span data-ttu-id="b9579-145">[Visual Database Tools를 &#40;데이터베이스 다이어그램 디자인&#41;](design-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b9579-145">[Design Database Diagrams &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="b9579-146">[Visual Database Tools를 &#40;테이블 디자인&#41;](design-tables-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b9579-146">[Design Tables &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b9579-147">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b9579-147">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
