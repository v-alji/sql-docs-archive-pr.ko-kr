---
title: 커서 사용 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: rothja
ms.author: jroth
ms.openlocfilehash: e08156b03407c7a05d86278c11482a568d651f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638737"
---
# <a name="use-cursors-odbc"></a><span data-ttu-id="a9593-102">커서 사용(ODBC)</span><span class="sxs-lookup"><span data-stu-id="a9593-102">Use Cursors (ODBC)</span></span>
    
### <a name="to-use-cursors"></a><span data-ttu-id="a9593-103">커서를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="a9593-103">To use cursors</span></span>  
  
1.  <span data-ttu-id="a9593-104">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)을 호출하여 원하는 커서 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-104">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the desired cursor attributes:</span></span>  
  
     <span data-ttu-id="a9593-105">SQL_ATTR_CURSOR_TYPE 및 SQL_ATTR_CONCURRENCY 특성을 설정합니다(기본 옵션).</span><span class="sxs-lookup"><span data-stu-id="a9593-105">Set the SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY attributes (this is the preferred option).</span></span>  
  
     <span data-ttu-id="a9593-106">또는</span><span class="sxs-lookup"><span data-stu-id="a9593-106">Or</span></span>  
  
     <span data-ttu-id="a9593-107">SQL_CURSOR_SCROLLABLE 및 SQL_CURSOR_SENSITIVITY 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-107">Set the SQL_CURSOR_SCROLLABLE and SQL_CURSOR_SENSITIVITY attributes.</span></span>  
  
2.  <span data-ttu-id="a9593-108">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)을 호출하여 SQL_ATTR_ROW_ARRAY_SIZE 특성으로 행 집합 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the rowset size by using the SQL_ATTR_ROW_ARRAY_SIZE attribute.</span></span>  
  
3.  <span data-ttu-id="a9593-109">필요한 경우 WHERE CURRENT OF 절을 사용하여 위치 지정 업데이트를 수행하려면 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406)을 호출하여 커서 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-109">Optionally, call [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) to set a cursor name if positioned updates will be done by using the WHERE CURRENT OF clause.</span></span>  
  
4.  <span data-ttu-id="a9593-110">SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-110">Execute the SQL statement.</span></span>  
  
5.  <span data-ttu-id="a9593-111">필요한 경우 WHERE CURRENT OF 절을 사용하여 위치 지정 업데이트를 수행하려면 [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)을 호출하여 커서 이름을 가져옵니다(3단계에서 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406)을 사용하여 커서 이름을 지정하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="a9593-111">Optionally, call [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) to get the cursor name if positioned updates will be done by using the WHERE CURRENT OF clause and a cursor name was not supplied with [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) in Step 3.</span></span>  
  
6.  <span data-ttu-id="a9593-112">[SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)를 호출하여 행 집합의 열 수(C)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-112">Call [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns (C) in the rowset.</span></span>  
  
     <span data-ttu-id="a9593-113">열 단위 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-113">Use column-wise binding.</span></span>  
  
     <span data-ttu-id="a9593-114">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="a9593-114">\- or -</span></span>  
  
     <span data-ttu-id="a9593-115">행 단위 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-115">Use row-wise binding.</span></span>  
  
7.  <span data-ttu-id="a9593-116">커서에서 원하는 대로 행 집합을 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-116">Fetch rowsets from the cursor as desired.</span></span>  
  
8.  <span data-ttu-id="a9593-117">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)를 호출하여 다른 결과 집합이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-117">Call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="a9593-118">다른 결과 집합이 있으면 SQL_SUCCESS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-118">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="a9593-119">다른 결과 집합이 없으면 SQL_NO_DATA가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-119">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="a9593-120">SQL_SUCCESS_WITH_INFO 또는 SQL_ERROR가 반환되면 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402)를 호출하여 사용할 수 있는 PRINT 또는 RAISERROR 문 출력이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-120">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
     <span data-ttu-id="a9593-121">바인딩된 문 매개 변수가 출력 매개 변수 또는 저장 프로시저의 반환 값으로 사용될 경우 바인딩된 매개 변수 버퍼에서 현재 사용할 수 있는 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-121">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span>  
  
     <span data-ttu-id="a9593-122">바인딩된 매개 변수를 사용하면 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 또는 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)를 호출할 때마다 SQL 문이 S번 실행됩니다. 여기서 S는 바인딩된 매개 변수 배열에 포함된 요소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-122">When bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement S times, where S is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="a9593-123">이는 S개의 결과 집합을 처리해야 함을 의미하며, 각 결과 집합은 SQL 문을 한 번 실행했을 때 일반적으로 반환되는 모든 결과 집합, 출력 매개 변수 및 반환 코드 전체로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-123">This means that there will be S sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
     <span data-ttu-id="a9593-124">결과 집합에 컴퓨팅 행이 포함된 경우 각 컴퓨팅 행은 별도의 결과 집합으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-124">Note that when a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="a9593-125">이러한 컴퓨팅 결과 집합은 일반 행 내에 섞여 일반 행을 여러 개의 결과 집합으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-125">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
9. <span data-ttu-id="a9593-126">필요에 따라 SQL_UNBIND와 함께 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)를 호출하여 바인딩된 열 버퍼를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-126">Optionally, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
10. <span data-ttu-id="a9593-127">다른 결과 집합이 있으면 6단계부터 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-127">If another result set is available, go to Step 6.</span></span>  
  
     <span data-ttu-id="a9593-128">9단계에서 부분적으로 처리된 결과 집합에 대해 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)를 호출하면 나머지 결과 집합이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-128">In Step 9, calling [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) on a partially processed result set clears the remainder of the result set.</span></span> <span data-ttu-id="a9593-129">[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)를 호출하여 부분적으로 처리된 결과 집합을 지울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-129">Another way to clear a partially processed result set is to call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
     <span data-ttu-id="a9593-130">SQL_ATTR_CURSOR_TYPE 및 SQL_ATTR_CONCURRENCY를 설정하거나 SQL_ATTR_CURSOR_SENSITIVITY 및 SQL_ATTR_CURSOR_SCROLLABLE을 설정하여 사용되는 커서 유형을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-130">You can control the type of cursor used by setting either SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="a9593-131">커서 동작을 지정할 때 이 두 방법을 함께 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9593-131">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9593-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9593-132">See Also</span></span>  
 [<span data-ttu-id="a9593-133">커서 사용 방법 항목 ODBC&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="a9593-133">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
