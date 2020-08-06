---
title: 쿼리에 테이블 추가(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 572002bc913cc9916a75ce2b16c12064452d250f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651430"
---
# <a name="add-tables-to-queries-visual-database-tools"></a><span data-ttu-id="4435b-102">쿼리에 테이블 추가(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4435b-102">Add Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="4435b-103">쿼리를 만들 때는 뷰와 특정 사용자 정의 함수 같은 테이블 구조의 다른 개체나 테이블에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-103">When you create a query, you are retrieving data from a table or other objects structured like tables - views and certain user-defined functions.</span></span> <span data-ttu-id="4435b-104">쿼리에서 이러한 개체를 사용하여 작업하려면 필요한 개체를 **다이어그램 창**에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-104">To work with any of these objects in your query, you add them to the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a><span data-ttu-id="4435b-105">테이블 또는 테이블 반환 개체를 쿼리에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="4435b-105">To add a table or table-valued object to a query</span></span>  
  
1.  <span data-ttu-id="4435b-106">쿼리 및 뷰 디자이너의 **다이어그램 창** 에서 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **테이블 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-106">In the **Diagram pane** of the Query and View Designer, right-click the background and choose **Add Table** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4435b-107">**테이블 추가** 대화 상자에서 쿼리에 추가할 개체 형식에 대한 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-107">In the **Add Table** dialog box, select the tab for the type of object you want to add to the query.</span></span>  
  
3.  <span data-ttu-id="4435b-108">항목의 목록에서 추가하려는 항목을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-108">In the list of items, double-click each item you want to add.</span></span>  
  
4.  <span data-ttu-id="4435b-109">항목 추가를 마치면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-109">When you finish adding items, click **Close**.</span></span>  
  
     <span data-ttu-id="4435b-110">쿼리 및 뷰 디자이너는 **다이어그램 창**, **조건 창**및 **SQL 창** 을 적절하게 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-110">The Query and View Designer updates the **Diagram Pane**, **Criteria Pane**, and **SQL Pane** accordingly.</span></span>  
  
 <span data-ttu-id="4435b-111">SQL 창에서 테이블이나 뷰를 문에 참조하면 참조된 테이블과 뷰가 쿼리에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-111">Tables and views are automatically added to the query when you reference them in the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="4435b-112">테이블 또는 테이블 구조 개체에 대한 충분한 액세스 권한이 없거나 드라이버가 이에 대한 정보를 반환하지 않으면 쿼리 및 뷰 디자이너에 데이터 열이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-112">The Query and View Designer will not display data columns for a table or table-structured object if you do not have sufficient access rights to it or if the provider cannot return information about it.</span></span> <span data-ttu-id="4435b-113">이러한 경우에는 테이블이나 테이블 반환 개체에 대해 제목 표시줄과 \* (모든 열) 확인란만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-113">In such cases, only a title bar and the \* (All Columns) check box are displayed for the table or table-valued object.</span></span>  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a><span data-ttu-id="4435b-114">새 쿼리에 기존 쿼리를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="4435b-114">To add an existing query to a new query</span></span>  
  
1.  <span data-ttu-id="4435b-115">만들려는 새 쿼리에 **SQL 창** 이 표시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-115">Make sure the **SQL Pane** is displayed in the new query you are creating.</span></span>  
  
2.  <span data-ttu-id="4435b-116">**SQL 창**에서 FROM이라는 단어 뒤에 여는 괄호와 닫는 괄호 ()를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-116">In the **SQL Pane**, type a right and left parentheses () after the word FROM.</span></span>  
  
3.  <span data-ttu-id="4435b-117">기존 쿼리에 대해 쿼리 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-117">Open the Query Designer for the existing query.</span></span> <span data-ttu-id="4435b-118">이제 두 개의 쿼리 디자이너가 열려 있는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-118">(You now have two Query Designers open.)</span></span>  
  
4.  <span data-ttu-id="4435b-119">새로운 외부 쿼리에 포함하려는 기존의 내부 쿼리에 대해 **SQL 창**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-119">Display the **SQL Pane** for the inner query - the existing query you are including in the new, outer query.</span></span>  
  
5.  <span data-ttu-id="4435b-120">**SQL 창**에서 텍스트 전체를 선택하여 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-120">Select all the text in the **SQL Pane**, and copy it to the Clipboard.</span></span>  
  
6.  <span data-ttu-id="4435b-121">새 쿼리의 **SQL 창** 을 클릭하고 앞서 추가했던 괄호 사이에 커서를 놓은 다음 클립보드 내용을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-121">Click in the **SQL Pane** of the new query, situate the cursor between the parentheses you added, and paste the contents of the Clipboard.</span></span>  
  
7.  <span data-ttu-id="4435b-122">**SQL 창**에서 닫는 괄호 뒤에 별칭을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4435b-122">Still in the **SQL Pane**, add an alias after the right parenthesis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4435b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4435b-123">See Also</span></span>  
 <span data-ttu-id="4435b-124">[Visual Database Tools&#41;&#40;테이블 별칭을 만듭니다.](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4435b-124">[Create Table Aliases &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="4435b-125">[쿼리에서 테이블 제거 &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4435b-125">[Remove Tables from Queries &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="4435b-126">[Visual Database Tools &#40;검색 조건을 지정&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4435b-126">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="4435b-127">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4435b-127">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4435b-128">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="4435b-128">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
