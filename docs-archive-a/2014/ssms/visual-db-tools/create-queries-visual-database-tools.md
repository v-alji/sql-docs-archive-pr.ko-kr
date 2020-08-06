---
title: 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52392adff03b27e1c4c19f354bc62c350cccf17a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639209"
---
# <a name="create-queries-visual-database-tools"></a><span data-ttu-id="33792-102">쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="33792-102">Create Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="33792-103">쿼리를 사용하면 데이터베이스에서 테이블과 뷰의 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33792-103">Queries allow you to retrieve data from the tables and views in your database.</span></span> <span data-ttu-id="33792-104">쿼리는 **쿼리 및 뷰 디자이너**에서 만들고 사용합니다. 이 디자이너는 [다이어그램 창](visual-database-tools.md), [SQL 창](sql-pane-visual-database-tools.md), [조건 창](criteria-pane-visual-database-tools.md)및 [결과 창](results-pane-visual-database-tools.md)의 네 가지 창으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="33792-104">You create and work with queries in **Query and View Designer**, which is composed of four panes: the [Diagram Pane](visual-database-tools.md), the [SQL Pane](sql-pane-visual-database-tools.md), the [Criteria Pane](criteria-pane-visual-database-tools.md), and the [Results Pane](results-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-a-new-query"></a><span data-ttu-id="33792-105">새 쿼리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="33792-105">To create a new query</span></span>  
  
1.  <span data-ttu-id="33792-106">**개체 탐색기**에서 쿼리할 데이터베이스의 **테이블** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-106">In **Object Explorer**, expand the **Tables** node for the database you want to query.</span></span> <span data-ttu-id="33792-107">쿼리할 테이블을 마우스 오른쪽 단추로 클릭한 다음 **테이블 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-107">Right-click the table you want to query and click **Open Table**.</span></span>  
  
2.  <span data-ttu-id="33792-108">쿼리에 다른 테이블을 추가하려면 쿼리 디자이너 메뉴에서 **테이블 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-108">To add more tables to the query, on the Query Designer menu, select **Add Table**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="33792-109">**다이어그램**, **SQL**, **조건**또는 **결과** 창이 표시되지 않으면 쿼리 디자이너 메뉴에서 **창** 을 가리킨 다음 열려는 창을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-109">If you do not see the **Diagram**, **SQL**, **Criteria**, or **Results** panes, from the Query Designer menu, point to **Pane** and click the pane you want to open.</span></span>  
  
3.  <span data-ttu-id="33792-110">**테이블 추가** 대화 상자에서 쿼리하려는 테이블을 선택하고 각 테이블에 대해 **추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-110">In the **Add Table** dialog box, select the tables you want to query and click **Add** for each one.</span></span>  
  
4.  <span data-ttu-id="33792-111">쿼리하려는 테이블을 모두 추가한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-111">Once you have added all the tables you want to query, click **Close**.</span></span>  
  
     <span data-ttu-id="33792-112">나중에 테이블을 더 추가하려면 **다이어그램** 창에서 열려 있는 공간을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **테이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-112">To add more tables later, right-click the open space in the **Diagram** pane and from the shortcut menu click **Add Table**.</span></span>  
  
5.  <span data-ttu-id="33792-113">**다이어그램 창**에서 쿼리하려는 각 열에 대한 테이블 반환 개체의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-113">In the **Diagram Pane**, check the boxes in the table-valued objects for each column you want to query.</span></span>  
  
6.  <span data-ttu-id="33792-114">쿼리 디자이너 메뉴에서 **SQL 실행** 을 선택하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="33792-114">From the Query Designer menu, choose **Execute SQL** to run your query.</span></span>  
  
 <span data-ttu-id="33792-115">**SQL 창** 에서 SQL 코드를 변경하거나 **조건 창**에서 정렬 순서 및 열 별칭 등과 같은 옵션을 선택하여 쿼리를 더 구체화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33792-115">To further refine your query, you can change the SQL code in the **SQL Pane** or choose options such as sort order and column aliases in the **Criteria Pane.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33792-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33792-116">See Also</span></span>  
 <span data-ttu-id="33792-117">[Visual Database Tools를 &#40;쿼리 저장&#41;](save-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="33792-117">[Save Queries &#40;Visual Database Tools&#41;](save-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="33792-118">[Visual Database Tools를 &#40;쿼리 유형&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="33792-118">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="33792-119">[Visual Database Tools &#40;검색 조건을 지정&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="33792-119">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="33792-120">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="33792-120">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="33792-121">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="33792-121">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
