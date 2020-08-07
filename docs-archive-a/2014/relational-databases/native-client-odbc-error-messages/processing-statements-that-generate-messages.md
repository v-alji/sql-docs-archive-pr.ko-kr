---
title: 메시지를 생성 하는 문 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: rothja
ms.author: jroth
ms.openlocfilehash: c26376eabb756d356dd71fb3bd8284a6b11dced7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730659"
---
# <a name="processing-statements-that-generate-messages"></a><span data-ttu-id="312a4-102">메시지를 생성하는 문 처리</span><span class="sxs-lookup"><span data-stu-id="312a4-102">Processing Statements That Generate Messages</span></span>
  <span data-ttu-id="312a4-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] SET 문 옵션 STATISTICS TIME 및 STATISTICS IO를 사용하여 장기 실행 쿼리를 진단하는 데 유용한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement options STATISTICS TIME and STATISTICS IO are used to get information that aids in diagnosing long-running queries.</span></span> <span data-ttu-id="312a4-104">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서도 쿼리 계획을 분석하는 SHOWPLAN 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-104">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also support the SHOWPLAN option for analyzing query plans.</span></span> <span data-ttu-id="312a4-105">ODBC 애플리케이션은 다음 문을 실행하여 이러한 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-105">An ODBC application can set these options by executing the following statements:</span></span>  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 <span data-ttu-id="312a4-106">SET STATISTICS TIME 또는 SET 실행 계획이 ON 인 경우 **Sqlexecute** 및 **sqlexecdirect** 는 SQL_SUCCESS_WITH_INFO을 반환 하 고,이 시점에서 응용 프로그램은 SQL_NO_DATA 반환 될 때까지 **SQLGetDiagRec** 를 호출 하 여 실행 계획 또는 통계 시간 출력을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-106">When SET STATISTICS TIME or SET SHOWPLAN are ON, **SQLExecute** and **SQLExecDirect** return SQL_SUCCESS_WITH_INFO, and, at that point, the application can retrieve the SHOWPLAN or STATISTICS TIME output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="312a4-107">각 SHOWPLAN 데이터 행은 다음과 같은 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-107">Each line of SHOWPLAN data comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="312a4-108">버전 7.0에서 SHOWPLAN 옵션은 출력을 메시지 집합이 아닌 결과 집합으로 반환하는 SHOWPLAN_ALL 및 SHOWPLAN_TEXT로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-108">version 7.0 replaced the SHOWPLAN option with SHOWPLAN_ALL and SHOWPLAN_TEXT, both of which return output as a result set, not a set of messages.</span></span>  
  
 <span data-ttu-id="312a4-109">각 STATISTICS TIME 행은 다음과 같은 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-109">Each line of STATISTICS TIME comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 <span data-ttu-id="312a4-110">SET STATISTICS IO의 출력은 결과 집합의 끝에 도달할 때까지 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-110">The output of SET STATISTICS IO is not available until the end of a result set.</span></span> <span data-ttu-id="312a4-111">통계 IO 출력을 가져오기 위해 응용 프로그램은 **Sqlfetch** 또는 [sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md) SQL_NO_DATA 반환 될 때 **SQLGetDiagRec** 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-111">To get STATISTICS IO output, the application calls **SQLGetDiagRec** at the time **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="312a4-112">STATISTICS IO 출력은 다음과 같은 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-112">The output of STATISTICS IO comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a><span data-ttu-id="312a4-113">DBCC 문 사용</span><span class="sxs-lookup"><span data-stu-id="312a4-113">Using DBCC Statements</span></span>  
 <span data-ttu-id="312a4-114">DBCC 문은 데이터를 결과 집합이 아닌 메시지로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-114">DBCC statements return their data as messages, not result sets.</span></span> <span data-ttu-id="312a4-115">**Sqlexecdirect** 또는 **sqlexecute** 는 SQL_SUCCESS_WITH_INFO 반환 하 고 SQL_NO_DATA 반환 될 때까지 응용 프로그램은 **SQLGetDiagRec** 를 호출 하 여 출력을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-115">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and the application retrieves the output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="312a4-116">예를 들어 다음 문은 SQL_SUCCESS_WITH_INFO를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-116">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 <span data-ttu-id="312a4-117">**SQLGetDiagRec** 에 대 한 호출은 다음을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-117">Calls to **SQLGetDiagRec** return:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a><span data-ttu-id="312a4-118">PRINT 및 RAISERROR 문 사용</span><span class="sxs-lookup"><span data-stu-id="312a4-118">Using PRINT and RAISERROR Statements</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="312a4-119">또한 PRINT 및 RAISERROR 문은 **SQLGetDiagRec**를 호출 하 여 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-119">PRINT and RAISERROR statements also return data by calling **SQLGetDiagRec**.</span></span> <span data-ttu-id="312a4-120">PRINT 문은 SQL 문 실행이 SQL_SUCCESS_WITH_INFO을 반환 하 고 **SQLGetDiagRec** 에 대 한 후속 호출에서는 *SQLState* 01000을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-120">PRINT statements cause the SQL statement execution to return SQL_SUCCESS_WITH_INFO, and a subsequent call to **SQLGetDiagRec** returns a *SQLState* of 01000.</span></span> <span data-ttu-id="312a4-121">심각도가 10 이하인 RAISERROR는 PRINT와 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-121">A RAISERROR with a severity of ten or lower behaves the same as PRINT.</span></span> <span data-ttu-id="312a4-122">심각도가 11 이상인 RAISERROR는 실행이 SQL_ERROR을 반환 하 고 **SQLGetDiagRec** 에 대 한 후속 호출은 *SQLState* 42000을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-122">A RAISERROR with a severity of 11 or higher causes the execute to return SQL_ERROR, and a subsequent call to **SQLGetDiagRec** returns *SQLState* 42000.</span></span> <span data-ttu-id="312a4-123">예를 들어 다음 문은 SQL_SUCCESS_WITH_INFO를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-123">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 <span data-ttu-id="312a4-124">**SQLGetDiagRec** 를 호출 하면 다음이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-124">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 <span data-ttu-id="312a4-125">다음 문은 SQL_SUCCESS_WITH_INFO를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-125">The following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 <span data-ttu-id="312a4-126">**SQLGetDiagRec** 를 호출 하면 다음이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-126">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 <span data-ttu-id="312a4-127">다음 문은 SQL_ERROR를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-127">The following statement returns SQL_ERROR:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 <span data-ttu-id="312a4-128">**SQLGetDiagRec** 를 호출 하면 다음이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-128">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 <span data-ttu-id="312a4-129">PRINT 또는 RAISERROR 문의 출력이 결과 집합에 포함 된 경우에는 **SQLGetDiagRec** 을 호출 하는 시간이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-129">The timing of calling **SQLGetDiagRec** is critical when output from PRINT or RAISERROR statements is included in a result set.</span></span> <span data-ttu-id="312a4-130">PRINT 또는 RAISERROR 출력을 검색 하는 **SQLGetDiagRec** 을 호출 하는 것은 SQL_ERROR 또는 SQL_SUCCESS_WITH_INFO를 수신 하는 문 바로 뒤에 생성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-130">The call to **SQLGetDiagRec** to retrieve the PRINT or RAISERROR output must be made immediately after the statement that receives SQL_ERROR or SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="312a4-131">위의 예에서와 같이 단일 SQL 문만 실행하는 경우에는 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-131">This is straightforward when only a single SQL statement is executed, as in the examples above.</span></span> <span data-ttu-id="312a4-132">이러한 경우 **Sqlexecdirect** 또는 **sqlexecute** 에 대 한 호출은 SQL_ERROR 또는 SQL_SUCCESS_WITH_INFO을 반환 하 고 **SQLGetDiagRec** 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-132">In these cases, the call to **SQLExecDirect** or **SQLExecute** returns SQL_ERROR or SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** can then be called.</span></span> <span data-ttu-id="312a4-133">하지만 SQL 문 일괄 처리의 출력을 처리하는 루프를 코딩할 때나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저를 실행할 때는 이보다 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-133">It is less straightforward when coding loops to handle the output of a batch of SQL statements or when executing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="312a4-134">이러한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 일괄 처리 또는 저장 프로시저에서 실행된 각 SELECT 문마다 결과 집합을 하나씩 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-134">In this case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns a result set for every SELECT statement executed in a batch or stored procedure.</span></span> <span data-ttu-id="312a4-135">일괄 처리 또는 프로시저에 PRINT 또는 RAISERROR 문이 포함된 경우 SELECT 문 결과 집합에 이러한 문의 출력이 인터리브됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-135">If the batch or procedure contains PRINT or RAISERROR statements, the output for these is interleaved with the SELECT statement result sets.</span></span> <span data-ttu-id="312a4-136">일괄 처리 또는 프로시저의 첫 번째 문이 PRINT 또는 RAISERROR 인 경우 **Sqlexecute** 또는 **sqlexecdirect** 는 SQL_SUCCESS_WITH_INFO 또는 SQL_ERROR를 반환 하며, 응용 프로그램은 PRINT 또는 RAISERROR 정보를 검색 하는 SQL_NO_DATA을 반환할 때까지 **SQLGetDiagRec** 를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-136">If the first statement in the batch or procedure is a PRINT or RAISERROR, the **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, and the application needs to call **SQLGetDiagRec** until it returns SQL_NO_DATA to retrieve the PRINT or RAISERROR information.</span></span>  
  
 <span data-ttu-id="312a4-137">PRINT 또는 RAISERROR 문이 SQL 문 (예: SELECT 문) 다음에 오는 경우에는 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)이 오류를 포함 하는 결과 집합에 배치 될 때 PRINT 또는 raiserror 정보가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-137">If the PRINT or RAISERROR statement comes after an SQL statement (such as a SELECT statement), then the PRINT or RAISERROR information is returned when [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)positions on the result set containing the error.</span></span> <span data-ttu-id="312a4-138">**SQLMoreResults** 는 메시지의 심각도에 따라 SQL_SUCCESS_WITH_INFO 또는 SQL_ERROR을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-138">**SQLMoreResults** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR depending on the severity of the message.</span></span> <span data-ttu-id="312a4-139">SQL_NO_DATA 반환 될 때까지 **SQLGetDiagRec** 를 호출 하 여 메시지를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-139">Messages are retrieved by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312a4-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="312a4-140">See Also</span></span>  
 [<span data-ttu-id="312a4-141">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="312a4-141">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
