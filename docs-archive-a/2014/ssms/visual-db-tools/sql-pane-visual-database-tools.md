---
title: SQL 창(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a87ec1d5517852fefb152e0ec7b3165fa32988b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727719"
---
# <a name="sql-pane-visual-database-tools"></a><span data-ttu-id="c0ad1-102">SQL Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c0ad1-102">SQL Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="c0ad1-103">SQL 창을 사용하여 고유한 SQL 문을 만들거나 조건 창 및 다이어그램 창을 사용하여 문을 만들 수 있습니다. 조건 창이나 다이어그램 창을 사용해도 SQL 문은 SQL 창에 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-103">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="c0ad1-104">쿼리를 작성할 때 SQL 창은 자동으로 업데이트되고 읽기 쉽도록 서식이 다시 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-104">As you build your query, the SQL pane automatically updates and reformats for easy readability.</span></span>  
  
 <span data-ttu-id="c0ad1-105">SQL 창을 열려면 먼저 **데이터베이스** 메뉴에서 **새 쿼리**를 클릭하여 서버 탐색기에서 데이터베이스 개체를 선택한 상태로 쿼리 및 뷰 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-105">To open the SQL pane, first open Query and View Designer (with a database object selected in Server Explorer, from the **Database** menu, click **New Query**).</span></span> <span data-ttu-id="c0ad1-106">그런 다음 **쿼리 디자이너** 메뉴에서 **창** 을 가리키고 **SQL**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-106">Then from the **Query Designer** menu point to **Pane** and click **SQL**.</span></span>  
  
 <span data-ttu-id="c0ad1-107">SQL 창에서 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-107">In the SQL pane you can:</span></span>  
  
-   <span data-ttu-id="c0ad1-108">SQL 문을 입력하여 새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-108">Create new queries by entering SQL statements.</span></span>  
  
-   <span data-ttu-id="c0ad1-109">다이어그램 창과 조건 창의 설정에 기반하여 쿼리 및 뷰 디자이너에서 만든 SQL 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-109">Modify the SQL statement created by the Query and View Designer based on settings you make in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="c0ad1-110">사용 중인 데이터베이스의 특정 기능을 활용할 수 있는 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-110">Enter statements that take advantage of features specific to the database you are using.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ad1-111">사용 중인 데이터베이스의 데이터베이스 개체 식별 규칙을 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-111">Be sure you know the rules for identifying database objects in the database you are using.</span></span> <span data-ttu-id="c0ad1-112">자세한 내용은 데이터베이스 관리 시스템의 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-112">For details, see the documentation for your database management system.</span></span>  
  
## <a name="statements-in-the-sql-pane"></a><span data-ttu-id="c0ad1-113">SQL 창의 문</span><span class="sxs-lookup"><span data-stu-id="c0ad1-113">Statements in the SQL Pane</span></span>  
 <span data-ttu-id="c0ad1-114">SQL 창에서 현재 쿼리를 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-114">You can edit the current query directly in the SQL pane.</span></span> <span data-ttu-id="c0ad1-115">다른 창으로 이동할 때 쿼리 및 뷰 디자이너는 문 서식을 자동으로 지정한 다음 다이어그램 창과 조건 창을 문과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-115">When you move to another pane, the Query and View Designer automatically formats your statement, and then changes the Diagram and Criteria panes to match your statement.</span></span>  
  
 <span data-ttu-id="c0ad1-116">다이어그램 창과 조건 창에 문을 나타낼 수 없고 해당 창들이 표시되는 경우 쿼리 및 뷰 디자이너는 오류를 표시한 후 다음과 같은 두 가지 선택을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-116">If your statement cannot be represented in the Diagram and Criteria panes, and if those panes are visible, Query and View Designer displays an error and then offers you two choices:</span></span>  
  
-   <span data-ttu-id="c0ad1-117">다이어그램 창과 조건 창에 문을 나타낼 수 없다는 사실을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-117">Ignore that the statement can not be represented in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="c0ad1-118">나타낼 수 없는 변경 내용을 취소하고 가장 최근 버전의 SQL 문으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-118">Undo the change that can not be represented and revert to the most recent version of the SQL statement.</span></span>  
  
 <span data-ttu-id="c0ad1-119">다이어그램 창과 조건 창에 문을 나타낼 수 없다는 사실을 무시하도록 선택하면 쿼리 및 뷰 디자이너에서 다른 창이 흐리게 표시됩니다. 이는 해당 창에 SQL 창의 내용이 더 이상 반영되지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-119">If you choose to ignore that the statement can not be represented in the Diagram and Criteria panes, the Query and View Designer dims the other panes to indicate that they no longer reflect the contents of the SQL pane.</span></span>  
  
 <span data-ttu-id="c0ad1-120">다른 SQL 문을 사용할 때와 같이 문을 계속 편집하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-120">You can continue to edit the statement and execute it as you would any SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ad1-121">SQL 문을 입력한 다음 다이어그램 창과 조건 창을 변경하여 쿼리를 추가로 변경하면 쿼리 및 뷰 디자이너는 SQL 문을 다시 작성하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-121">If you enter an SQL statement, but then make further changes to the query by changing the Diagram and Criteria panes, the Query and View Designer rebuilds and redisplays the SQL statement.</span></span> <span data-ttu-id="c0ad1-122">일부 경우 이 동작으로 인해 결과는 같지만 원래 입력한 내용과 다른 SQL 문이 만들어지기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-122">In some cases, this action results in an SQL statement that is constructed differently from the one you originally entered (though it will always yield the same results).</span></span> <span data-ttu-id="c0ad1-123">이러한 차이는 AND와 OR로 연결된 여러 절을 포함하는 검색 조건을 사용하여 작업할 때 특히 자주 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c0ad1-123">This difference is particularly likely when you are working with search conditions that involve several clauses linked with AND and OR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ad1-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0ad1-124">See Also</span></span>  
 <span data-ttu-id="c0ad1-125">[Visual Database Tools를 &#40;쿼리 만들기&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0ad1-125">[Create Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="c0ad1-126">[Visual Database Tools를 &#40;쿼리 실행&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0ad1-126">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="c0ad1-127">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0ad1-127">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="c0ad1-128">[다이어그램 창 &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0ad1-128">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="c0ad1-129">[조건 창 &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0ad1-129">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c0ad1-130">결과 창&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c0ad1-130">Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
