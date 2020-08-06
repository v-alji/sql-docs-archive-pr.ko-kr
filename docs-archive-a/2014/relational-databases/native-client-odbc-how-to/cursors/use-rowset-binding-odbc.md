---
title: 행 집합 바인딩 사용 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: rothja
ms.author: jroth
ms.openlocfilehash: e2e0671fd1140e72005cd1a7532ea581f077382f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638734"
---
# <a name="use-rowset-binding-odbc"></a><span data-ttu-id="57e64-102">행 집합 바인딩 사용(ODBC)</span><span class="sxs-lookup"><span data-stu-id="57e64-102">Use Rowset Binding (ODBC)</span></span>
    
### <a name="to-use-column-wise-binding"></a><span data-ttu-id="57e64-103">열 단위 바인딩을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="57e64-103">To use column-wise binding</span></span>  
  
1.  <span data-ttu-id="57e64-104">바인딩된 각 열에 대해 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-104">For each bound column, do the following:</span></span>  
  
    -   <span data-ttu-id="57e64-105">데이터 값을 저장할 R개 이상의 열 버퍼 배열을 할당합니다. 여기서 R은 행 집합의 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-105">Allocate an array of R (or more) column buffers to store data values, where R is number of rows in the rowset.</span></span>  
  
    -   <span data-ttu-id="57e64-106">필요에 따라 데이터 길이를 저장할 R개 이상의 열 버퍼 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-106">Optionally, allocate an array of R (or more) column buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="57e64-107">[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) 을 호출하여 열의 데이터 값 및 데이터 길이 배열을 행 집합의 열에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-107">Call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to bind the column's data value and data length arrays to the column of the rowset.</span></span>  
  
2.  <span data-ttu-id="57e64-108">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="57e64-109">SQL_ATTR_ROW_ARRAY_SIZE를 행 집합의 행 수(R)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-109">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="57e64-110">SQL_ATTR_ROW_BIND_TYPE을 SQL_BIND_BY_COLUMN으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-110">Set SQL_ATTR_ROW_BIND_TYPE to SQL_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="57e64-111">SQL_ATTR_ROWS FETCHED_PTR 특성을 인출된 행 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-111">Set the SQL_ATTR_ROWS FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="57e64-112">SQL_ATTR_ROW_STATUS_PTR을 행 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[R]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-112">Set SQL_ATTR_ROW_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="57e64-113">해당 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-113">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="57e64-114">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 또는 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) 에 대한 각 호출에서 R개의 행을 검색하여 데이터를 바인딩된 열로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-114">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
### <a name="to-use-row-wise-binding"></a><span data-ttu-id="57e64-115">행 단위 바인딩을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="57e64-115">To use row-wise binding</span></span>  
  
1.  <span data-ttu-id="57e64-116">구조의 배열[R]을 할당합니다. 여기서 R은 행 집합의 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-116">Allocate an array[R] of structures, where R is the number of rows in the rowset.</span></span> <span data-ttu-id="57e64-117">구조에는 각 열에 대해 요소가 하나씩 포함되고 각 요소에는 두 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-117">The structure has one element for each column, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="57e64-118">첫 번째 부분은 열 데이터를 보유하는 적절한 데이터 형식의 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-118">The first part is a variable of the appropriate data type to hold the column data.</span></span>  
  
    -   <span data-ttu-id="57e64-119">두 번째 부분은 열 상태 표시를 보유하는 SQLINTEGER 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-119">The second part is a SQLINTEGER variable to hold the column status indicator.</span></span>  
  
2.  <span data-ttu-id="57e64-120">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-120">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="57e64-121">SQL_ATTR_ROW_ARRAY_SIZE를 행 집합의 행 수(R)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-121">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="57e64-122">SQL_ATTR_ROW_BIND_TYPE을 1단계에서 할당한 구조의 크기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-122">Set SQL_ATTR_ROW_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="57e64-123">SQL_ATTR_ROWS_FETCHED_PTR 특성을 인출된 행 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-123">Set the SQL_ATTR_ROWS_FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="57e64-124">SQL_ATTR_PARAMS_STATUS_PTR을 행 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[R]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-124">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="57e64-125">결과 집합의 각 열에 대해 [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) 을 호출하여 열의 데이터 값 및 데이터 길이 포인터가 1단계에서 할당한 구조 배열의 첫 번째 요소에 있는 해당 변수를 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-125">For each column in the result set, call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to point the data value and data length pointer of the column to their variables in the first element of the array of structures allocated in Step 1.</span></span>  
  
4.  <span data-ttu-id="57e64-126">해당 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-126">Execute the statement.</span></span>  
  
5.  <span data-ttu-id="57e64-127">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 또는 [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) 에 대한 각 호출에서 R개의 행을 검색하여 데이터를 바인딩된 열로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="57e64-127">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e64-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57e64-128">See Also</span></span>  
 <span data-ttu-id="57e64-129">[커서 사용 방법 항목 ODBC&#41;&#40;](using-cursors-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="57e64-129">[Using Cursors How-to Topics &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="57e64-130">[커서 구현 방법](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span><span class="sxs-lookup"><span data-stu-id="57e64-130">[How Cursors Are Implemented](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span></span>  
 [<span data-ttu-id="57e64-131">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="57e64-131">Use Cursors &#40;ODBC&#41;</span></span>](use-cursors-odbc.md)  
  
  
