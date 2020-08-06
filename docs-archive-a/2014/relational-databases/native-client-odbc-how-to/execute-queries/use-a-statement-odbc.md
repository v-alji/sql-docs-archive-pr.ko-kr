---
title: 문 사용 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ff3bc8c545cc9b55f0da3bb31d68d1ecbb5b547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739874"
---
# <a name="use-a-statement-odbc"></a><span data-ttu-id="5e5a0-102">문 사용(ODBC)</span><span class="sxs-lookup"><span data-stu-id="5e5a0-102">Use a Statement (ODBC)</span></span>
    
### <a name="to-use-a-statement"></a><span data-ttu-id="5e5a0-103">문을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5e5a0-103">To use a statement</span></span>  
  
1.  <span data-ttu-id="5e5a0-104">SQL_HANDLE_STMT의 *HandleType*으로 [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)을 호출하여 문 핸들을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-104">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a *HandleType* of SQL_HANDLE_STMT to allocate a statement handle.</span></span>  
  
2.  <span data-ttu-id="5e5a0-105">필요에 따라 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)을 호출하여 문 옵션을 설정하거나 [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)을 호출하여 문 특성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-105">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set statement options or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get statement attributes.</span></span>  
  
     <span data-ttu-id="5e5a0-106">서버 커서를 사용하려면 커서 특성을 기본값 이외의 값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-106">To use server cursors, you must set cursor attributes to values other than their defaults.</span></span>  
  
3.  <span data-ttu-id="5e5a0-107">문이 여러 번 실행되는 경우 필요에 따라 [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360)(SQLPrepare 함수)을 사용하여 문 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-107">Optionally, if the statement will be executed several times, prepare the statement for execution with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span>  
  
4.  <span data-ttu-id="5e5a0-108">문에 바인딩된 매개 변수 표식이 있으면 필요에 따라 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)를 사용하여 프로그램 변수에 매개 변수 표식을 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-108">Optionally, if the statement has bound parameter markers, bind the parameter markers to program variables by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="5e5a0-109">문이 준비되어 있으면 [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) 및 [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)을 호출하여 매개 변수의 수와 특징을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-109">If the statement was prepared, you can call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) and [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number and characteristics of the parameters.</span></span>  
  
5.  <span data-ttu-id="5e5a0-110">SQLExecDirect를 사용하여 문을 직접 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-110">Execute a statement directly by using SQLExecDirect.</span></span>  
  
     <span data-ttu-id="5e5a0-111">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e5a0-111">\- or -</span></span>  
  
     <span data-ttu-id="5e5a0-112">문이 준비되어 있는 경우 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)를 사용하여 여러 번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-112">If the statement was prepared, execute it multiple times by using [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400).</span></span>  
  
     <span data-ttu-id="5e5a0-113">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e5a0-113">\- or -</span></span>  
  
     <span data-ttu-id="5e5a0-114">카탈로그 함수를 호출하여 결과가 반환되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-114">Call a catalog function, which returns results.</span></span>  
  
6.  <span data-ttu-id="5e5a0-115">결과 집합 열을 프로그램 변수에 바인딩하거나 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)를 사용하여 결과 집합 열에서 프로그램 변수로 데이터를 이동하거나 이 두 방법을 함께 사용하여 결과를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-115">Process the results by binding the result set columns to program variables, by moving data from the result set columns to program variables by using [SQLGetData](../../native-client-odbc-api/sqlgetdata.md), or a combination of the two methods.</span></span>  
  
     <span data-ttu-id="5e5a0-116">문의 결과 집합을 한 번에 한 행씩 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-116">Fetch through the result set of a statement one row at a time.</span></span>  
  
     <span data-ttu-id="5e5a0-117">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e5a0-117">\- or -</span></span>  
  
     <span data-ttu-id="5e5a0-118">블록 커서를 사용하여 결과 집합을 한 번에 여러 행씩 인출합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-118">Fetch through the result set several rows at a time by using a block cursor.</span></span>  
  
     <span data-ttu-id="5e5a0-119">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="5e5a0-119">\- or -</span></span>  
  
     <span data-ttu-id="5e5a0-120">[SQLRowCount](../../native-client-odbc-api/sqlrowcount.md)를 호출하여 INSERT, UPDATE 또는 DELETE 문의 영향을 받는 행 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-120">Call [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) to determine the number of rows affected by an INSERT, UPDATE, or DELETE statement.</span></span>  
  
     <span data-ttu-id="5e5a0-121">SQL 문의 결과 집합이 여러 개이면 각 결과 집합의 끝에서 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)를 호출하여 추가로 처리할 결과 집합이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-121">If the SQL statement can have multiple result sets, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) at the end of each result set to see if there are additional result sets to process.</span></span>  
  
7.  <span data-ttu-id="5e5a0-122">결과 집합이 처리된 후에는 새 문을 실행하는 데 문 핸들을 사용할 수 있도록 하기 위해 다음 동작을 수행해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-122">After results are processed, the following actions may be necessary to make the statement handle available to execute a new statement:</span></span>  
  
    -   <span data-ttu-id="5e5a0-123">SQL_NO_DATA가 반환될 때까지 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)를 호출하지 않은 경우 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)를 호출하여 커서를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-123">If you did not call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) until it returned SQL_NO_DATA, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) to close the cursor.</span></span>  
  
    -   <span data-ttu-id="5e5a0-124">매개 변수 표식을 프로그램 변수에 바인딩한 경우 *Option*을 SQL_RESET_PARAMS로 설정한 상태로 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)를 호출하여 바인딩된 매개 변수를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-124">If you bound parameter markers to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_RESET_PARAMS to free the bound parameters.</span></span>  
  
    -   <span data-ttu-id="5e5a0-125">결과 집합 열을 프로그램 변수에 바인딩한 경우 *Option*을 SQL_UNBIND로 설정한 상태로 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)를 호출하여 바인딩된 열을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-125">If you bound result set columns to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_UNBIND to free the bound columns.</span></span>  
  
    -   <span data-ttu-id="5e5a0-126">문 핸들을 다시 사용하려면 2단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-126">To reuse the statement handle, go to Step 2.</span></span>  
  
8.  <span data-ttu-id="5e5a0-127">SQL_HANDLE_STMT의 *HandleType*으로 [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md)을 호출하여 문 핸들을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5a0-127">Call [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) with a *HandleType* of SQL_HANDLE_STMT to free the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5a0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e5a0-128">See Also</span></span>  
 [<span data-ttu-id="5e5a0-129">쿼리 실행 방법 도움말 항목 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="5e5a0-129">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
