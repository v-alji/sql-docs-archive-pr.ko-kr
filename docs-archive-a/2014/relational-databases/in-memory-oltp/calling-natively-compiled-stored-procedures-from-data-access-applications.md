---
title: 데이터 액세스 애플리케이션에서 고유하게 컴파일된 저장 프로시저 호출 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 9cf6c5ff-4548-401a-b3ec-084f47ff0eb8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5583137d4c159756246938a83bf8c8e1fad6cdea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741019"
---
# <a name="calling-natively-compiled-stored-procedures-from-data-access-applications"></a><span data-ttu-id="faf36-102">데이터 액세스 애플리케이션에서 고유하게 컴파일된 저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="faf36-102">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>
  <span data-ttu-id="faf36-103">이 항목에서는 데이터 액세스 애플리케이션에서 고유하게 컴파일된 저장 프로시저를 호출하는 방법에 대한 지침을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-103">This topic discusses guidance on calling natively compiled stored procedures from data access applications.</span></span>  
  
 <span data-ttu-id="faf36-104">커서는 고유하게 컴파일된 저장 프로시저를 반복할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-104">Cursors cannot iterate over a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="faf36-105">컨텍스트 연결을 사용하여 CLR 모듈에서 고유하게 컴파일된 지정 프로시저를 호출하는 것은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-105">Calling natively compiled stored procedures from CLR modules using the context connection is not supported.</span></span>  
  
 <span data-ttu-id="faf36-106">SqlClient</span><span class="sxs-lookup"><span data-stu-id="faf36-106">SqlClient</span></span>  
 <span data-ttu-id="faf36-107">SqlClient의 경우 준비된 실행과 직접 실행 간에 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-107">For SqlClient there is no distinction between prepared and direct execution.</span></span> <span data-ttu-id="faf36-108">CommandType이 CommandType.StoredProcedure인 SqlCommand를 사용하여 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-108">Execute stored procedures with SqlCommand with CommandType = CommandType.StoredProcedure.</span></span>  
  
 <span data-ttu-id="faf36-109">SqlClient는 준비된 RPC 프로시저 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-109">SqlClient does not support prepared RPC procedure calls.</span></span>  
  
 <span data-ttu-id="faf36-110">SqlClient는 고유하게 컴파일된 저장 프로시저(CommandType.SchemaOnly)에서 반환되는 결과 집합에 대한 스키마 전용 정보 검색(메타데이터 검색)을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-110">SqlClient does not support retrieving schema-only information (metadata discovery) about the result sets returned by a natively compiled stored procedure (CommandType.SchemaOnly).</span></span> <span data-ttu-id="faf36-111">대신 [sp_describe_first_result_set&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="faf36-111">Instead, use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="faf36-112">Native Client</span><span class="sxs-lookup"><span data-stu-id="faf36-112">Native Client</span></span>  
 <span data-ttu-id="faf36-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 보다 이전 버전의 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client는 고유하게 컴파일된 저장 프로시저에서 반환되는 결과 집합에 대한 스키마 전용 정보 검색(메타데이터 검색)을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-113">Versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] do not support retrieving schema-only information (metadata discovery) about the result sets returned by a natively compiled stored procedure.</span></span> <span data-ttu-id="faf36-114">대신 [sp_describe_first_result_set&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="faf36-114">Instead, use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).</span></span>  
  
 <span data-ttu-id="faf36-115">다음은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서 ODBC 드라이버를 사용하여 고유하게 컴파일된 저장 프로시저를 호출할 때 적용되는 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-115">The following recommendations apply to calls of natively compiled stored procedure using the ODBC driver in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="faf36-116">저장 프로시저를 한 번 호출하는 가장 효율적인 방법은 `SQLExecDirect` 및 ODBC CALL 절을 사용하여 직접 RPC 호출을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-116">The most efficient way to call a stored procedure once is to issue a direct RPC call using `SQLExecDirect` and ODBC CALL clauses.</span></span> <span data-ttu-id="faf36-117">문을 사용 하지 마십시오 [!INCLUDE[tsql](../../../includes/tsql-md.md)] `EXECUTE` .</span><span class="sxs-lookup"><span data-stu-id="faf36-117">Do not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)]`EXECUTE` statement.</span></span> <span data-ttu-id="faf36-118">저장 프로시저를 두 번 이상 호출하는 경우에는 준비된 실행이 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-118">If a stored procedure is called more than once, prepared execution is more efficient.</span></span>  
  
 <span data-ttu-id="faf36-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장 프로시저를 두 번 이상 호출하는 가장 효율적인 방법은 준비된 RPC 프로시저 호출을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-119">The most efficient way to call a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedure more than once is through prepared RPC procedure calls.</span></span> <span data-ttu-id="faf36-120">다음은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서 ODBC 드라이버를 사용하여 준비된 RPC 호출을 수행하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-120">Prepared RPC calls are performed as follows using the ODBC driver in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="faf36-121">데이터베이스에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-121">Open a connection to the database.</span></span>  
  
-   <span data-ttu-id="faf36-122">`SQLBindParameter`를 사용하여 매개 변수를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-122">Bind the parameters using `SQLBindParameter`.</span></span>  
  
-   <span data-ttu-id="faf36-123">`SQLPrepare.`을 사용하여 프로시저 호출을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-123">Prepare the procedure call using `SQLPrepare.`</span></span>  
  
-   <span data-ttu-id="faf36-124">`SQLExecute`를 사용하여 저장 프로시저를 여러 번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-124">Execute the stored procedure multiple times using `SQLExecute`.</span></span>  
  
 <span data-ttu-id="faf36-125">다음 코드 조각에서는 주문에 품목을 추가하는 저장 프로시저의 준비된 실행을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-125">The following code fragment shows prepared execution of a stored procedure to add line items to an order.</span></span> <span data-ttu-id="faf36-126">`SQLPrepare`는 한 번만 호출되고 `SQLExecute`는 프로시저가 실행될 때마다 한 번씩 여러 번 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-126">`SQLPrepare` is called only once and `SQLExecute` is called multiple times, once for each procedure execution.</span></span>  
  
```  
// Bind parameters  
// 1 - OrdNo   
SQLRETURN returnCode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,   
                     &order.OrdNo, sizeof(SQLINTEGER), NULL);  
if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {  
   ODBCError(henv, hdbc, hstmt, NULL, true);   
   exit(-1);  
}  
  
// 2, 3, 4 - ItemNo, ProdCode, Qty  
...  
  
// Prepare stored procedure  
returnCode = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),SQL_NTS);  
  
for (unsigned int i = 0; i < order.ItemCount; i++) {  
   ItemNo = order.ItemNo[i];  
   ProdCode = order.ProdCode[i];  
   Qty = order.Qty[i];  
  
   // Execute stored procedure  
   returnCode = SQLExecute(hstmt);  
   if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
}  
```  
  
## <a name="using-odbc-to-execute-a-natively-complied-stored-procedure"></a><span data-ttu-id="faf36-127">ODBC를 사용하여 네이티브 컴파일 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="faf36-127">Using ODBC to Execute a Natively Complied Stored Procedure</span></span>  
 <span data-ttu-id="faf36-128">이 예제에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버를 사용하여 매개 변수를 바인딩하고 저장 프로시저를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-128">This sample shows how to bind parameters and execute stored procedures using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  <span data-ttu-id="faf36-129">이 예제에서는 직접 실행을 사용하여 단일 주문을 삽입하고 준비된 실행을 사용하여 주문 세부 정보를 삽입하는 콘솔 애플리케이션으로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-129">The sample compiles to a console application that inserts a single order using direct execution, and inserts the order details using prepared execution.</span></span>  
  
 <span data-ttu-id="faf36-130">이 예제를 실행하려면:</span><span class="sxs-lookup"><span data-stu-id="faf36-130">To run this sample:</span></span>  
  
1.  <span data-ttu-id="faf36-131">메모리 최적화 데이터 파일 그룹이 포함된 예제 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-131">Create a sample database with a memory-optimized data filegroup.</span></span> <span data-ttu-id="faf36-132">메모리 최적화 데이터 파일 그룹이 있는 데이터베이스를 만드는 방법은 [메모리 최적화 테이블 및 고유하게 컴파일된 저장 프로시저 만들기](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="faf36-132">For information on how to create a database with a memory-optimized data filegroup, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
2.  <span data-ttu-id="faf36-133">데이터베이스를 가리키는 PrepExecSample이라는 ODBC 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-133">Create an ODBC data source called PrepExecSample that points to the database.</span></span> <span data-ttu-id="faf36-134">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 드라이버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-134">Use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client driver.</span></span> <span data-ttu-id="faf36-135">예제를 수정하고 [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/jj730314.aspx)를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-135">You could also modify the sample and use the [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/jj730314.aspx).</span></span>  
  
3.  <span data-ttu-id="faf36-136">샘플 데이터베이스에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트(아래)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-136">Run the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script (below) on the sample database.</span></span>  
  
4.  <span data-ttu-id="faf36-137">예제를 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-137">Compile and run the sample.</span></span>  
  
5.  <span data-ttu-id="faf36-138">테이블 내용을 쿼리하여 프로그램이 성공적으로 실행되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-138">Verify successful execution of the program by querying the contents of the tables:</span></span>  
  
    ```  
    SELECT * FROM dbo.Ord  
    ```  
  
    ```  
    SELECT * FROM dbo.Item  
    ```  
  
 <span data-ttu-id="faf36-139">다음은 메모리 최적화 데이터베이스 개체를 만드는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-139">The following is the [!INCLUDE[tsql](../../../includes/tsql-md.md)] code listing that creates the memory-optimized database objects.</span></span>  
  
```  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.OrderInsert'))  
  DROP PROCEDURE dbo.OrderInsert  
go  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.ItemInsert'))  
  DROP PROCEDURE dbo.ItemInsert  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Ord'))  
  DROP TABLE dbo.Ord  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Item'))  
  DROP TABLE dbo.Item  
GO  
CREATE TABLE dbo.Ord  
(  
   OrdNo INTEGER NOT NULL PRIMARY KEY NONCLUSTERED,  
   OrdDate DATETIME NOT NULL,   
   CustCode VARCHAR(5) NOT NULL)   
 WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.Item  
(  
   OrdNo INTEGER NOT NULL,   
   ItemNo INTEGER NOT NULL,   
   ProdCode INTEGER NOT NULL,   
   Qty INTEGER NOT NULL,  
   CONSTRAINT PK_Item PRIMARY KEY NONCLUSTERED (OrdNo,ItemNo))  
   WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE PROCEDURE dbo.OrderInsert(@OrdNo INTEGER, @CustCode VARCHAR(5))  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = 'english')  
  
  DECLARE @OrdDate datetime = GETDATE();  
  INSERT INTO dbo.Ord (OrdNo, CustCode, OrdDate) VALUES (@OrdNo, @CustCode, @OrdDate);   
END  
GO  
  
CREATE PROCEDURE dbo.ItemInsert(@OrdNo INTEGER, @ItemNo INTEGER, @ProdCode INTEGER, @Qty INTEGER)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = N'us_english')  
  
  INSERT INTO dbo.Item (OrdNo, ItemNo, ProdCode, Qty) VALUES (@OrdNo, @ItemNo, @ProdCode, @Qty)  
END  
GO  
```  
  
 <span data-ttu-id="faf36-140">다음은 C 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="faf36-140">The following is the C code listing.</span></span>  
  
```  
// compile with: user32.lib odbc32.lib  
#pragma once  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
#include <windows.h>  
#include "sql.h"  
#include "sqlext.h"  
#include "sqlncli.h"  
  
// cardinality of order item related array variables  
#define ITEM_ARRAY_SIZE 20  
  
// struct to pass order entry data  
typedef struct OrdEntry_struct {  
   SQLINTEGER OrdNo;  
   SQLTCHAR CustCode[6];  
   SQLUINTEGER ItemCount;  
   SQLINTEGER ItemNo[ITEM_ARRAY_SIZE];  
   SQLINTEGER ProdCode[ITEM_ARRAY_SIZE];  
   SQLINTEGER Qty[ITEM_ARRAY_SIZE];  
} OrdEntryData;  
  
SQLHANDLE henv, hdbc, hstmt;  
  
void ODBCError(SQLHANDLE henv, SQLHANDLE hdbc, SQLHANDLE hstmt, SQLHANDLE hdesc, bool ShowError) {  
   SQLRETURN r = 0;  
   SQLTCHAR szSqlState[6] = {0};  
   SQLINTEGER fNativeError = 0;  
   SQLTCHAR szErrorMsg[256] = {0};  
   SQLSMALLINT cbErrorMsgMax = sizeof(szErrorMsg) - 1;  
   SQLSMALLINT cbErrorMsg = 0;  
   TCHAR text[1024] = {0}, title[256] = {0};  
  
   if (hdesc != NULL)  
      r = SQLGetDiagRec(SQL_HANDLE_DESC, hdesc, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
   else {  
      if (hstmt != NULL)  
         r = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
      else {  
         if (hdbc != NULL)  
            r = SQLGetDiagRec(SQL_HANDLE_DBC, hdbc, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
         else  
            r = SQLGetDiagRec(SQL_HANDLE_ENV, henv, 1, szSqlState, &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);  
      }  
   }  
  
   if (ShowError) {  
      _sntprintf_s(title, _countof(title), _TRUNCATE, _T("ODBC Error %i"), fNativeError);  
      _sntprintf_s(text, _countof(text), _TRUNCATE, _T("[%s] - %s"), szSqlState, szErrorMsg);  
  
      MessageBox(NULL, (LPCTSTR) text, (LPCTSTR) _T("ODBC Error"), MB_OK);  
   }  
}  
  
void connect() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &henv);  
  
   // This is an ODBC v3 application  
   r = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, 0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   r = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Run in ANSI/implicit transaction mode  
   r = SQLSetConnectAttr(hdbc, SQL_ATTR_AUTOCOMMIT, (SQLPOINTER) SQL_AUTOCOMMIT_OFF, SQL_IS_INTEGER);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=PrepExecSample");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, NULL, NULL, true);  
      exit(-1);  
   }  
}  
  
void setup_ODBC_basics() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);  
      exit(-1);  
   }  
}  
  
void OrdEntry(OrdEntryData& order) {  
   // Simple order entry  
   SQLRETURN r;  
  
   SQLINTEGER ItemNo, ProdCode, Qty;  
  
   // Bind parameters for the Order  
   // 1 - OrdNo input  
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &order.OrdNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - Custcode input  
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_C_TCHAR, SQL_VARCHAR, 5, 0, &order.CustCode, sizeof(order.CustCode), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Insert the order  
   r = SQLExecDirect(hstmt, (SQLTCHAR *) _T("{call OrderInsert(?, ?)}"),SQL_NTS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Bind parameters for the Items  
   // 1 - OrdNo   
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &order.OrdNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - ItemNo   
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &ItemNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 3 - ProdCode  
   r = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &ProdCode, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 4 - Qty  
   r = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0, &Qty, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Prepare to insert items one at a time  
   r = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),SQL_NTS);  
  
   for (unsigned int i = 0; i < order.ItemCount; i++) {  
  ItemNo = order.ItemNo[i];  
      ProdCode = order.ProdCode[i];  
      Qty = order.Qty[i];  
      r = SQLExecute(hstmt);  
      if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
         ODBCError(henv, hdbc, hstmt, NULL, true);   
         exit(-1);  
      }  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Commit the transaction  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
}  
  
void testOrderEntry() {  
  
   OrdEntryData order;  
  
   order.OrdNo = 1;  
   _tcscpy_s((TCHAR *) order.CustCode, _countof(order.CustCode), _T("CUST1"));  
   order.ItemNo[0] = 1;  
   order.ProdCode[0] = 10;  
   order.Qty[0] = 1;  
   order.ItemNo[1] = 2;  
   order.ProdCode[1] = 20;  
   order.Qty[1] = 2;  
   order.ItemNo[2] = 3;  
   order.ProdCode[2] = 30;  
   order.Qty[2] = 3;  
   order.ItemNo[3] = 4;  
   order.ProdCode[3] = 40;  
   order.Qty[3] = 4;  
   order.ItemCount = 4;  
  
   OrdEntry(order);  
}  
int _tmain() {  
   connect();  
   setup_ODBC_basics();  
  
   testOrderEntry();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="faf36-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="faf36-141">See Also</span></span>  
 [<span data-ttu-id="faf36-142">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="faf36-142">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
