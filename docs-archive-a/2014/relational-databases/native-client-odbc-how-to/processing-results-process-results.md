---
title: 결과 처리 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a22e9d7280f88de7799c31d2d0611e5299043d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738295"
---
# <a name="process-results-odbc"></a><span data-ttu-id="9d85c-102">결과 처리(ODBC)</span><span class="sxs-lookup"><span data-stu-id="9d85c-102">Process Results (ODBC)</span></span>
    
### <a name="to-process-results"></a><span data-ttu-id="9d85c-103">결과를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="9d85c-103">To process results</span></span>  
  
1.  <span data-ttu-id="9d85c-104">결과 집합 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-104">Retrieve result set information.</span></span>  
  
2.  <span data-ttu-id="9d85c-105">바인딩된 열을 사용하는 경우 바인딩할 각 열에 대해 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)을 호출하여 프로그램 버퍼를 열에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-105">If bound columns are used, for each column you want to bind to, call [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) to bind a program buffer to the column.</span></span>  
  
3.  <span data-ttu-id="9d85c-106">결과 집합의 각 행에 대해 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-106">For each row in the result set:</span></span>  
  
    -   <span data-ttu-id="9d85c-107">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)를 호출하여 다음 행을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-107">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) to get the next row.</span></span>  
  
    -   <span data-ttu-id="9d85c-108">바인딩된 열을 사용하는 경우 이제 바인딩된 열 버퍼에서 사용할 수 있는 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-108">If bound columns are used, use the data now available in the bound column buffers.</span></span>  
  
    -   <span data-ttu-id="9d85c-109">바인딩되지 않은 열을 사용하는 경우 [SQLGetData](../native-client-odbc-api/sqlgetdata.md)를 한 번 이상 호출하여 바인딩된 마지막 열 다음의 바인딩되지 않은 열 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-109">If unbound columns are used, call [SQLGetData](../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column.</span></span> <span data-ttu-id="9d85c-110">`SQLGetData`는 번호가 가장 작은 열부터 차례로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-110">Calls to `SQLGetData` should be in increasing order of column number.</span></span>  
  
    -   <span data-ttu-id="9d85c-111">`SQLGetData`를 여러 번 호출하여 텍스트나 이미지 열에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-111">Call `SQLGetData` multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="9d85c-112">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)에서 SQL_NO_DATA를 반환하여 결과 집합의 끝을 알리면 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)를 호출하여 다른 결과 집합을 사용할 수 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-112">When [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signals the end of the result set by returning SQL_NO_DATA, call [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="9d85c-113">다른 결과 집합이 있으면 SQL_SUCCESS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-113">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="9d85c-114">다른 결과 집합이 없으면 SQL_NO_DATA가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-114">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="9d85c-115">SQL_SUCCESS_WITH_INFO 또는 SQL_ERROR가 반환되면 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402)를 호출하여 사용할 수 있는 PRINT 또는 RAISERROR 문 출력이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-115">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
         <span data-ttu-id="9d85c-116">바인딩된 문 매개 변수가 출력 매개 변수 또는 저장 프로시저의 반환 값으로 사용될 경우 바인딩된 매개 변수 버퍼에서 현재 사용할 수 있는 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-116">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span> <span data-ttu-id="9d85c-117">또한 바인딩된 매개 변수를 사용하면 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 또는 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)를 호출할 때마다 SQL 문이 *S*번 실행됩니다. 여기서 *S*는 바인딩된 매개 변수 배열에 포함된 요소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-117">Also, when bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement *S* times, where *S* is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="9d85c-118">즉, 각 결과 집합은 SQL 문을 한 번 실행 했을 때 일반적으로 반환 되는 모든 결과 집합, 출력 매개 변수 및 반환 코드를 구성 하는 결과 집합을 *처리할 수 있습니다* .</span><span class="sxs-lookup"><span data-stu-id="9d85c-118">This means that there will be *S* sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d85c-119">결과 집합에 컴퓨팅 행이 포함된 경우 각 컴퓨팅 행은 별도의 결과 집합으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-119">When a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="9d85c-120">이러한 컴퓨팅 결과 집합은 일반 행 내에 섞여 일반 행을 여러 개의 결과 집합으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-120">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
5.  <span data-ttu-id="9d85c-121">필요에 따라 SQL_UNBIND와 함께 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)를 호출하여 바인딩된 열 버퍼를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-121">Optionally, call [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
6.  <span data-ttu-id="9d85c-122">다른 결과 집합을 사용할 수 있는 경우 1단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-122">If another result set is available, go to Step 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d85c-123">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)에서 SQL_NO_DATA를 반환하기 전에 결과 집합 처리를 취소하려면 [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9d85c-123">To cancel processing a result set before [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) returns SQL_NO_DATA, call [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d85c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d85c-124">See Also</span></span>  
 [<span data-ttu-id="9d85c-125">결과 처리 방법 도움말 항목 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="9d85c-125">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
