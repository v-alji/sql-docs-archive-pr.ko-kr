---
title: 서식 파일을 사용 하 여 대량 복사 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
author: rothja
ms.author: jroth
ms.openlocfilehash: 19959d5f1da7243275c60560963d577446f809b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741999"
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a><span data-ttu-id="73d4d-102">서식 파일을 사용하여 대량 복사(ODBC)</span><span class="sxs-lookup"><span data-stu-id="73d4d-102">Bulk Copy by Using a Format File (ODBC)</span></span>
  <span data-ttu-id="73d4d-103">이 예제에서는 ODBC bcp_init 함수를 서식 파일과 함께 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-103">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a><span data-ttu-id="73d4d-104">서식 파일을 사용하여 대량 복사하려면</span><span class="sxs-lookup"><span data-stu-id="73d4d-104">To bulk copy by using a format file</span></span>  
  
1.  <span data-ttu-id="73d4d-105">환경 핸들 및 연결 핸들을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-105">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="73d4d-106">대량 복사 작업을 사용하도록 SQL_COPT_SS_BCP 및 SQL_BCP_ON을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-106">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="73d4d-107">Microsoft SQL Server에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-107">Connect to Microsoft SQL Server.</span></span>  
  
4.  <span data-ttu-id="73d4d-108">[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) 를 호출하여 다음 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-108">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="73d4d-109">대량 복사를 수행할 원본 또는 대상 테이블/뷰의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-109">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="73d4d-110">데이터베이스로 복사할 데이터가 들어 있거나 데이터베이스에서 복사할 때 데이터를 받는 데이터 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-110">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="73d4d-111">대량 복사 오류 메시지를 받을 데이터 파일의 이름입니다. 메시지 파일이 필요하지 않으면 NULL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-111">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="73d4d-112">복사 방향을 지정합니다. DB_IN이면 파일에서 테이블 또는 뷰로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-112">The direction of the copy: DB_IN from the file to the table or view.</span></span>  
  
5.  <span data-ttu-id="73d4d-113">[bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) 를 호출하여 대량 복사 작업에 사용할 데이터 파일을 설명하는 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-113">Call [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) to read the format file describing the data file to be used by the bulk copy operation.</span></span>  
  
6.  <span data-ttu-id="73d4d-114">[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) 를 호출하여 대량 복사 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-114">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73d4d-115">예제</span><span class="sxs-lookup"><span data-stu-id="73d4d-115">Example</span></span>  
 <span data-ttu-id="73d4d-116">이 예제는 IA64에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="73d4d-117">AdventureWorks 예제 데이터베이스를 기본 데이터베이스로 사용하는 AdventureWorks라는 ODBC 데이터 원본이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="73d4d-118">AdventureWorks 샘플 데이터베이스는 [Microsoft SQL Server 샘플 및 커뮤니티 프로젝트](https://go.microsoft.com/fwlink/?LinkID=85384) 홈 페이지에서 다운로드할 수 있습니다. 이 데이터 원본은 운영 체제에서 제공 하는 ODBC 드라이버를 기반으로 해야 합니다. 드라이버 이름은 "SQL Server"입니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="73d4d-119">이 예제를 64비트 운영 체제에서 32비트 애플리케이션으로 작성하여 실행하려는 경우 %windir%\SysWOW64\odbcad32.exe에서 ODBC 관리자를 사용하여 ODBC 데이터 원본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="73d4d-120">이 예제는 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="73d4d-121">명명된 인스턴스에 연결하려면 ODBC 데이터 원본의 정의를 변경하여 server\namedinstance 형식으로 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="73d4d-122">기본적으로 [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 는 명명된 인스턴스에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-122">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="73d4d-123">첫 번째([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 코드 목록을 실행하여 예제에서 사용할 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-123">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="73d4d-124">두 번째 코드 목록을 복사하고 Bcpfmt.fmt라는 파일로 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-124">Copy the second code listing and paste it into a file called Bcpfmt.fmt.</span></span> <span data-ttu-id="73d4d-125">테이블의 각 열은 탭 문자로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-125">Each column in the table is separated by a tab character.</span></span>  
  
 <span data-ttu-id="73d4d-126">세 번째 코드 목록을 복사하고 Bcpodbc.bcp라는 파일로 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-126">Copy the third code listing and paste it into a file called Bcpodbc.bcp.</span></span> <span data-ttu-id="73d4d-127">파일에서 캐리지 리턴 앞에 탭 문자가 옵니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-127">A tab character precedes each carriage return in the file.</span></span>  
  
 <span data-ttu-id="73d4d-128">odbc32.lib 및 odbcbcp.lib를 사용하여 네 번째(C++) 코드 목록을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-128">Compile the fourth (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="73d4d-129">MSBuild.exe를 사용하여 빌드한 경우 먼저 Bcpfmt.fmt 및 Bcpodbc.bcp를 프로젝트 디렉터리에서 .exe가 있는 디렉터리에 복사한 다음 .exe를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-129">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="73d4d-130">다섯 번째([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 코드 목록을 실행하여 예제에서 사용한 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="73d4d-130">Execute the fifth ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```sql
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
```  
  
```cpp
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```sql
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="73d4d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73d4d-131">See Also</span></span>  
 <span data-ttu-id="73d4d-132">[SQL Server ODBC 드라이버를 사용 하 여 대량 복사 방법 도움말 항목 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="73d4d-132">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="73d4d-133">데이터 파일 및 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="73d4d-133">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
