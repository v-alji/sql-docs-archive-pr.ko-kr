---
title: 장기 실행 쿼리 기록 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
author: rothja
ms.author: jroth
ms.openlocfilehash: f73dbf6fe8fc4b3dfbbbc0012d14a58614b218dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740919"
---
# <a name="log-long-running-queries-odbc"></a><span data-ttu-id="51622-102">장기 실행 쿼리 기록(ODBC)</span><span class="sxs-lookup"><span data-stu-id="51622-102">Log Long-Running Queries (ODBC)</span></span>
  <span data-ttu-id="51622-103">이 예제에서는 장기 실행 쿼리를 로깅하기 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 드라이버 관련 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51622-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to log long-running queries.</span></span> <span data-ttu-id="51622-104">이 예제를 실행할 경우 애플리케이션에서 설정한 간격을 초과하여 실행되는 쿼리 목록이 포함된 Odbcqry.log가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="51622-104">When run, this sample creates Odbcqry.log, which contains a list of queries whose execution exceeds an interval set by the application.</span></span> <span data-ttu-id="51622-105">이 예제는 IA64에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51622-105">This sample is not supported on IA64.</span></span> <span data-ttu-id="51622-106">이 예제는 ODBC 버전 3.0 이상용으로 개발되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51622-106">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51622-107">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="51622-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="51622-108">Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="51622-109">자격 증명은 파일에 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="51622-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="51622-110">자격 증명을 유지 해야 하는 경우에는 [Win32 CRYPTO API](https://go.microsoft.com/fwlink/?LinkId=64532)를 사용 하 여 자격 증명을 암호화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-110">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a><span data-ttu-id="51622-111">ODBC 관리자를 사용하여 장기 실행 쿼리를 기록하려면</span><span class="sxs-lookup"><span data-stu-id="51622-111">To log long-running queries using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="51622-112">**제어판**에서 **관리 도구** 를 두 번 클릭 한 다음 **데이터 원본 (ODBC)** 을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-112">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="51622-113">또는 명령 프롬프트에서 odbcad32.exe를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51622-113">(Alternatively, you can run odbcad32.exe from the command prompt.)</span></span>  
  
2.  <span data-ttu-id="51622-114">**사용자 dsn**, **시스템 DSN**또는 **파일 dsn** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-114">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="51622-115">장기 실행 쿼리를 기록할 데이터 원본을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-115">Click the data source for which to log long-running queries.</span></span>  
  
4.  <span data-ttu-id="51622-116">**구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-116">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="51622-117">Microsoft SQL Server DSN 구성 마법사에서 **장기 실행 쿼리를 로그 파일에 저장**하는 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-117">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Save long-running queries to the log file**.</span></span>  
  
6.  <span data-ttu-id="51622-118">**장기 실행 쿼리를 로그 파일에 저장을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-118">Select **Save long-running queries to the log file**.</span></span> <span data-ttu-id="51622-119">상자에서 장기 실행 쿼리를 기록할 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-119">In the box, place the name of the file where the long-running queries should be logged.</span></span> <span data-ttu-id="51622-120">필요에 따라 **찾아보기** 를 클릭 하 여 파일 시스템에서 쿼리 로그를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="51622-120">Optionally, click **Browse** to browse the file system for the query log.</span></span>  
  
7.  <span data-ttu-id="51622-121">**장기 쿼리 시간 (밀리초)** 상자에 쿼리 제한 시간 간격 (밀리초)을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-121">Set a query time-out interval, in milliseconds, in the **Long query time (milliseconds)** box.</span></span>  
  
### <a name="to-log-long-running-queries-data-programmatically"></a><span data-ttu-id="51622-122">장기 실행 쿼리 데이터를 프로그래밍 방식으로 기록하려면</span><span class="sxs-lookup"><span data-stu-id="51622-122">To log long-running queries data programmatically</span></span>  
  
1.  <span data-ttu-id="51622-123">SQL_COPT_SS_PERF_QUERY_LOG와 장기 실행 쿼리 로그 파일의 전체 경로 및 파일 이름을 사용 하 여 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_LOG and the full path and file name of the long-running query log file.</span></span> <span data-ttu-id="51622-124">예:</span><span class="sxs-lookup"><span data-stu-id="51622-124">For example:</span></span>  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  <span data-ttu-id="51622-125">SQL_COPT_SS_PERF_QUERY_INTERVAL를 사용 하 여 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 하 고 시간 제한 간격 (밀리초)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-125">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_INTERVAL and set to the time-out interval, in milliseconds.</span></span>  
  
3.  <span data-ttu-id="51622-126">SQL_COPT_SS_PERF_QUERY 및 SQL_PERF_START를 사용 하 여 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 하 여 장기 실행 쿼리 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_START to start logging long-running queries.</span></span>  
  
4.  <span data-ttu-id="51622-127">SQL_COPT_SS_PERF_QUERY 및 SQL_PERF_STOP를 사용 하 여 장기 실행 쿼리 기록을 중지 하려면 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-127">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_STOP to stop logging long-running queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51622-128">예제</span><span class="sxs-lookup"><span data-stu-id="51622-128">Example</span></span>  
 <span data-ttu-id="51622-129">AdventureWorks 예제 데이터베이스를 기본 데이터베이스로 사용하는 AdventureWorks라는 ODBC 데이터 원본이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="51622-130">AdventureWorks 샘플 데이터베이스는 [Microsoft SQL Server 샘플 및 커뮤니티 프로젝트](https://go.microsoft.com/fwlink/?LinkID=85384) 홈 페이지에서 다운로드할 수 있습니다. 이 데이터 원본은 운영 체제에서 제공 하는 ODBC 드라이버를 기반으로 해야 합니다. 드라이버 이름은 "SQL Server"입니다.</span><span class="sxs-lookup"><span data-stu-id="51622-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="51622-131">이 예제를 64비트 운영 체제에서 32비트 애플리케이션으로 작성하여 실행하려는 경우 %windir%\SysWOW64\odbcad32.exe에서 ODBC 관리자를 사용하여 ODBC 데이터 원본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="51622-132">이 예제는 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="51622-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="51622-133">명명된 인스턴스에 연결하려면 ODBC 데이터 원본의 정의를 변경하여 server\namedinstance 형식으로 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="51622-134">기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 는 명명된 인스턴스에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="51622-134">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="51622-135">odbc32.lib를 사용하여 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="51622-135">Compile with odbc32.lib.</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="51622-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51622-136">See Also</span></span>  
 [<span data-ttu-id="51622-137">ODBC 드라이버 성능 프로 파일링 방법 항목 ODBC&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="51622-137">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
  
