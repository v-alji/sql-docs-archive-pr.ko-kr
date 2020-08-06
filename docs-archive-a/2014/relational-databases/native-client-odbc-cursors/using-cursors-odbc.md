---
title: 커서 사용 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739886"
---
# <a name="using-cursors-odbc"></a><span data-ttu-id="026b8-102">커서 사용(ODBC)</span><span class="sxs-lookup"><span data-stu-id="026b8-102">Using Cursors (ODBC)</span></span>
  <span data-ttu-id="026b8-103">ODBC는 다음을 허용하는 커서 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-103">ODBC supports a cursor model that allows:</span></span>  
  
-   <span data-ttu-id="026b8-104">여러 커서 유형</span><span class="sxs-lookup"><span data-stu-id="026b8-104">Several types of cursors.</span></span>  
  
-   <span data-ttu-id="026b8-105">커서 내에서 스크롤 및 위치 지정</span><span class="sxs-lookup"><span data-stu-id="026b8-105">Scrolling and positioning within a cursor.</span></span>  
  
-   <span data-ttu-id="026b8-106">여러 동시성 옵션</span><span class="sxs-lookup"><span data-stu-id="026b8-106">Several concurrency options.</span></span>  
  
-   <span data-ttu-id="026b8-107">위치 지정 업데이트</span><span class="sxs-lookup"><span data-stu-id="026b8-107">Positioned updates.</span></span>  
  
 <span data-ttu-id="026b8-108">ODBC 애플리케이션은 거의 커서를 선언하여 열거나 커서 관련 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-108">ODBC applications rarely declare and open cursors or use any cursor-related [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="026b8-109">SQL 문에서 반환된 모든 결과 집합에 대해 ODBC에서 자동으로 커서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-109">ODBC automatically opens a cursor for every result set returned from an SQL statement.</span></span> <span data-ttu-id="026b8-110">커서의 특징은 SQL 문이 실행 되기 전에 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 로 설정 된 문 특성에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-110">The characteristics of the cursors are controlled by statement attributes set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) before the SQL statement is executed.</span></span> <span data-ttu-id="026b8-111">결과 집합 처리를 위한 ODBC API 함수는 인출, 스크롤 및 위치 지정 업데이트를 비롯한 모든 커서 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-111">The ODBC API functions for processing result sets support the full range of cursor functionality, including fetching, scrolling, and positioned updates.</span></span>  
  
 <span data-ttu-id="026b8-112">다음은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트와 ODBC 애플리케이션의 커서 작업 방법을 비교한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-112">This is a comparison of how [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and ODBC applications work with cursors.</span></span>  
  
|<span data-ttu-id="026b8-113">작업</span><span class="sxs-lookup"><span data-stu-id="026b8-113">Action</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)]|<span data-ttu-id="026b8-114">ODBC</span><span class="sxs-lookup"><span data-stu-id="026b8-114">ODBC</span></span>|  
|------------|------------------------|----------|  
|<span data-ttu-id="026b8-115">커서 동작 정의</span><span class="sxs-lookup"><span data-stu-id="026b8-115">Define cursor behavior</span></span>|<span data-ttu-id="026b8-116">DECLARE CURSOR 매개 변수를 통해 지정</span><span class="sxs-lookup"><span data-stu-id="026b8-116">Specify through DECLARE CURSOR parameters</span></span>|<span data-ttu-id="026b8-117">[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 를 사용 하 여 커서 특성 설정</span><span class="sxs-lookup"><span data-stu-id="026b8-117">Set cursor attributes by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)</span></span>|  
|<span data-ttu-id="026b8-118">커서 열기</span><span class="sxs-lookup"><span data-stu-id="026b8-118">Open a cursor</span></span>|<span data-ttu-id="026b8-119">커서 열기 *CURSOR_NAME* 선언</span><span class="sxs-lookup"><span data-stu-id="026b8-119">DECLARE CURSOR OPEN *cursor_name*</span></span>|<span data-ttu-id="026b8-120">**Sqlexecdirect** 또는 **sqlexecute**</span><span class="sxs-lookup"><span data-stu-id="026b8-120">**SQLExecDirect** or **SQLExecute**</span></span>|  
|<span data-ttu-id="026b8-121">행 인출</span><span class="sxs-lookup"><span data-stu-id="026b8-121">Fetch rows</span></span>|<span data-ttu-id="026b8-122">FETCH</span><span class="sxs-lookup"><span data-stu-id="026b8-122">FETCH</span></span>|<span data-ttu-id="026b8-123">**Sqlfetch** 또는 [sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)</span><span class="sxs-lookup"><span data-stu-id="026b8-123">**SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span></span>|  
|<span data-ttu-id="026b8-124">위치 지정 업데이트</span><span class="sxs-lookup"><span data-stu-id="026b8-124">Positioned update</span></span>|<span data-ttu-id="026b8-125">UPDATE 또는 DELETE의 WHERE CURRENT OF 절</span><span class="sxs-lookup"><span data-stu-id="026b8-125">WHERE CURRENT OF clause on UPDATE or DELETE</span></span>|<span data-ttu-id="026b8-126">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="026b8-126">**SQLSetPos**</span></span>|  
|<span data-ttu-id="026b8-127">커서 닫기</span><span class="sxs-lookup"><span data-stu-id="026b8-127">Close a cursor</span></span>|<span data-ttu-id="026b8-128">닫기 *cursor_name* 할당 취소</span><span class="sxs-lookup"><span data-stu-id="026b8-128">CLOSE *cursor_name* DEALLOCATE</span></span>|[<span data-ttu-id="026b8-129">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="026b8-129">SQLCloseCursor</span></span>](../native-client-odbc-api/sqlclosecursor.md)|  
  
 <span data-ttu-id="026b8-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 구현된 서버 커서는 ODBC 커서 모델의 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-130">The server cursors implemented in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support the functionality of the ODBC cursor model.</span></span> <span data-ttu-id="026b8-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 서버 커서를 사용하여 ODBC API의 커서 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="026b8-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client driver uses server cursors to support the cursor functionality of the ODBC API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="026b8-132">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="026b8-132">In This Section</span></span>  
  
-   [<span data-ttu-id="026b8-133">커서 구현 방법</span><span class="sxs-lookup"><span data-stu-id="026b8-133">How Cursors Are Implemented</span></span>](implementation/how-cursors-are-implemented.md)  
  
-   [<span data-ttu-id="026b8-134">커서 유형</span><span class="sxs-lookup"><span data-stu-id="026b8-134">Cursor Types</span></span>](cursor-types.md)  
  
-   [<span data-ttu-id="026b8-135">커서 동작</span><span class="sxs-lookup"><span data-stu-id="026b8-135">Cursor Behaviors</span></span>](cursor-behaviors.md)  
  
-   [<span data-ttu-id="026b8-136">커서 속성</span><span class="sxs-lookup"><span data-stu-id="026b8-136">Cursor Properties</span></span>](properties/cursor-properties.md)  
  
-   [<span data-ttu-id="026b8-137">ODBC&#41;&#40;커서 프로그래밍 정보</span><span class="sxs-lookup"><span data-stu-id="026b8-137">Cursor Programming Details &#40;ODBC&#41;</span></span>](programming/cursor-programming-details-odbc.md)  
  
-   [<span data-ttu-id="026b8-138">행 스크롤 및 페치</span><span class="sxs-lookup"><span data-stu-id="026b8-138">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [<span data-ttu-id="026b8-139">ODBC&#41;&#40;위치 지정 업데이트</span><span class="sxs-lookup"><span data-stu-id="026b8-139">Positioned Updates &#40;ODBC&#41;</span></span>](positioned-updates-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="026b8-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="026b8-140">See Also</span></span>  
 <span data-ttu-id="026b8-141">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="026b8-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="026b8-142">[&#40;Transact-sql&#41;를 닫습니다.](/sql/t-sql/language-elements/close-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="026b8-142">[CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql) </span></span>  
 <span data-ttu-id="026b8-143">[커서](../../relational-databases/cursors.md) </span><span class="sxs-lookup"><span data-stu-id="026b8-143">[Cursors](../../relational-databases/cursors.md) </span></span>  
 <span data-ttu-id="026b8-144">[Transact-sql&#41;&#40;할당 취소](/sql/t-sql/language-elements/deallocate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="026b8-144">[DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span></span>  
 <span data-ttu-id="026b8-145">[Transact-sql&#41;&#40;커서를 선언 합니다.](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="026b8-145">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="026b8-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="026b8-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span></span>  
 [<span data-ttu-id="026b8-147">OPEN&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="026b8-147">OPEN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/open-transact-sql)  
  
  
