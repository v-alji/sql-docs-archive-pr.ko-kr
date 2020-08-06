---
title: 행 스크롤 및 페치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739898"
---
# <a name="scrolling-and-fetching-rows"></a><span data-ttu-id="a8ecb-102">행 스크롤 및 인출</span><span class="sxs-lookup"><span data-stu-id="a8ecb-102">Scrolling and Fetching Rows</span></span>
  <span data-ttu-id="a8ecb-103">스크롤형 커서를 사용하려면 ODBC 애플리케이션에서 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-103">To use a scrollable cursor, an ODBC application must:</span></span>  
  
-   <span data-ttu-id="a8ecb-104">[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)를 사용 하 여 커서 기능을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-104">Set the cursor capabilities using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
-   <span data-ttu-id="a8ecb-105">**Sqlexecute** 또는 **sqlexecdirect**를 사용 하 여 커서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-105">Open the cursor using **SQLExecute** or **SQLExecDirect**.</span></span>  
  
-   <span data-ttu-id="a8ecb-106">**Sqlfetch** 또는 [sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)을 사용 하 여 행을 스크롤하고 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-106">Scroll and fetch rows using **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="a8ecb-107">**Sqlfetch** 와 **Sqlfetchsroll** 은 모두 한 번에 행 블록을 페치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-107">Both **SQLFetch** and **SQLFetchSroll** can fetch blocks of rows at a time.</span></span> <span data-ttu-id="a8ecb-108">반환 되는 행 수는 **SQLSetStmtAttr** 를 사용 하 여 SQL_ATTR_ROW_ARRAY_SIZE 매개 변수를 설정 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-108">The number of rows returned is specified by using **SQLSetStmtAttr** to set the SQL_ATTR_ROW_ARRAY_SIZE parameter.</span></span>  
  
 <span data-ttu-id="a8ecb-109">ODBC 응용 프로그램은 **Sqlfetch** 를 사용 하 여 앞 으로만 이동 가능한 커서를 통해 인출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-109">ODBC applications can use **SQLFetch** to fetch through a forward-only cursor.</span></span>  
  
 <span data-ttu-id="a8ecb-110">**Sqlfetchscroll** 은 커서 주위의 스크롤에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-110">**SQLFetchScroll** is used to scroll around a cursor.</span></span> <span data-ttu-id="a8ecb-111">**Sqlfetchscroll** 은 상대 인출 (현재 행 집합의 시작 부분에서 행 집합 *n* 행 인출) 및 절대 인출 (행 *n*에서 시작 하는 행 집합 인출) 외에도 다음, 이전, 첫 번째 및 마지막 행 집합을 인출 하는 것을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-111">**SQLFetchScroll** supports fetching the next, prior, first, and last rowsets in addition to relative fetching (fetch the rowset *n* rows from the start of the current rowset) and absolute fetching (fetch the rowset starting at row *n*).</span></span> <span data-ttu-id="a8ecb-112">절대 인출에서 *n* 이 음수 이면 결과 집합의 끝에서 행이 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-112">If *n* is negative in an absolute fetch, rows are counted from the end of the result set.</span></span> <span data-ttu-id="a8ecb-113">예를 들어 이 숫자가 -1이면 결과 집합의 마지막 행에서 시작하는 행 집합이 인출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-113">An absolute fetch of row -1 means to fetch the rowset that starts with the last row in the result set.</span></span>  
  
 <span data-ttu-id="a8ecb-114">보고서와 같은 블록 커서 기능에 대해서만 **Sqlfetchscroll** 을 사용 하는 응용 프로그램은 다음 행 집합을 인출 하는 옵션만 사용 하 여 결과 집합을 한 번에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-114">Applications that use **SQLFetchScroll** only for its block cursor capabilities, such as reports, are likely to pass through the result set a single time, using only the option to fetch the next rowset.</span></span> <span data-ttu-id="a8ecb-115">반면에 화면 기반 응용 프로그램은 **Sqlfetchscroll**의 모든 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-115">Screen-based applications, on the other hand, can take advantage of all the capabilities of **SQLFetchScroll**.</span></span> <span data-ttu-id="a8ecb-116">응용 프로그램에서 행 집합 크기를 화면에 표시 되는 행 수로 설정 하 고 화면 버퍼를 결과 집합에 바인딩하는 경우 스크롤 막대 작업을 **Sqlfetchscroll**에 대 한 호출로 직접 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ecb-116">If the application sets the rowset size to the number of rows displayed on the screen and binds the screen buffers to the result set, it can translate scroll bar operations directly to calls to **SQLFetchScroll**.</span></span>  
  
|<span data-ttu-id="a8ecb-117">스크롤 막대 작업</span><span class="sxs-lookup"><span data-stu-id="a8ecb-117">Scroll bar operation</span></span>|<span data-ttu-id="a8ecb-118">SQLFetchScroll 스크롤 옵션</span><span class="sxs-lookup"><span data-stu-id="a8ecb-118">SQLFetchScroll scrolling option</span></span>|  
|--------------------------|-------------------------------------|  
|<span data-ttu-id="a8ecb-119">페이지 위로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-119">Page up</span></span>|<span data-ttu-id="a8ecb-120">SQL_FETCH_PRIOR</span><span class="sxs-lookup"><span data-stu-id="a8ecb-120">SQL_FETCH_PRIOR</span></span>|  
|<span data-ttu-id="a8ecb-121">페이지 아래로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-121">Page down</span></span>|<span data-ttu-id="a8ecb-122">SQL_FETCH_NEXT</span><span class="sxs-lookup"><span data-stu-id="a8ecb-122">SQL_FETCH_NEXT</span></span>|  
|<span data-ttu-id="a8ecb-123">줄 위로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-123">Line up</span></span>|<span data-ttu-id="a8ecb-124">FetchOffset이-1과 같은 SQL_FETCH_RELATIVE</span><span class="sxs-lookup"><span data-stu-id="a8ecb-124">SQL_FETCH_RELATIVE with FetchOffset equal to -1</span></span>|  
|<span data-ttu-id="a8ecb-125">줄 아래로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-125">Line down</span></span>|<span data-ttu-id="a8ecb-126">FetchOffset이 1인 SQL_FETCH_RELATIVE</span><span class="sxs-lookup"><span data-stu-id="a8ecb-126">SQL_FETCH_RELATIVE with FetchOffset equal to 1</span></span>|  
|<span data-ttu-id="a8ecb-127">스크롤 상자 맨 위로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-127">Scroll box to top</span></span>|<span data-ttu-id="a8ecb-128">SQL_FETCH_FIRST</span><span class="sxs-lookup"><span data-stu-id="a8ecb-128">SQL_FETCH_FIRST</span></span>|  
|<span data-ttu-id="a8ecb-129">스크롤 상자 맨 아래로</span><span class="sxs-lookup"><span data-stu-id="a8ecb-129">Scroll box to bottom</span></span>|<span data-ttu-id="a8ecb-130">SQL_FETCH_LAST</span><span class="sxs-lookup"><span data-stu-id="a8ecb-130">SQL_FETCH_LAST</span></span>|  
|<span data-ttu-id="a8ecb-131">임의 스크롤 상자 위치</span><span class="sxs-lookup"><span data-stu-id="a8ecb-131">Random scroll box position</span></span>|<span data-ttu-id="a8ecb-132">SQL_FETCH_ABSOLUTE</span><span class="sxs-lookup"><span data-stu-id="a8ecb-132">SQL_FETCH_ABSOLUTE</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="a8ecb-133">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="a8ecb-133">In This Section</span></span>  
  
-   [<span data-ttu-id="a8ecb-134">ODBC의 행 집합에 책갈피 설정</span><span class="sxs-lookup"><span data-stu-id="a8ecb-134">Bookmarking Rows in ODBC</span></span>](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8ecb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8ecb-135">See Also</span></span>  
 [<span data-ttu-id="a8ecb-136">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="a8ecb-136">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
