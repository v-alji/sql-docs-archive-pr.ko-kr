---
title: 대량 복사 서식 파일 만들기 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC], data files
ms.assetid: 0572fef3-daf5-409e-b557-c2a632f9a06d
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d35342b2f6b25a129df968383d204931d64bfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646423"
---
# <a name="create-a-bulk-copy-format-file-odbc"></a><span data-ttu-id="e076b-102">대량 복사 서식 파일 만들기(ODBC)</span><span class="sxs-lookup"><span data-stu-id="e076b-102">Create a Bulk Copy Format File (ODBC)</span></span>
  <span data-ttu-id="e076b-103">이 예제에서는 대량 복사 함수를 사용하여 데이터 파일과 서식 파일을 모두 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-103">This sample shows how to use bulk copy functions to create both a data file and a format file.</span></span> <span data-ttu-id="e076b-104">이 예제는 ODBC 버전 3.0 이상용으로 개발되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e076b-105">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e076b-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="e076b-106">Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="e076b-107">자격 증명은 파일에 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="e076b-108">자격 증명을 유지 해야 하는 경우에는 [Win32 CRYPTO API](https://go.microsoft.com/fwlink/?LinkId=64532)를 사용 하 여 자격 증명을 암호화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-create-a-bulk-copy-format-file"></a><span data-ttu-id="e076b-109">대량 복사 서식 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e076b-109">To create a bulk copy format file</span></span>  
  
1.  <span data-ttu-id="e076b-110">환경 핸들 및 연결 핸들을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="e076b-111">대량 복사 작업을 사용하도록 SQL_COPT_SS_BCP 및 SQL_BCP_ON을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="e076b-112">SQL Server에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="e076b-113">[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) 를 호출하여 다음 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="e076b-114">대량 복사를 수행할 원본 또는 대상 테이블/뷰의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-114">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="e076b-115">데이터베이스로 복사할 데이터가 들어 있거나 데이터베이스에서 복사할 때 데이터를 받는 데이터 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-115">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="e076b-116">대량 복사 오류 메시지를 받을 데이터 파일의 이름입니다. 메시지 파일이 필요하지 않으면 NULL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="e076b-117">복사 방향: 테이블 또는 뷰에서 파일에 대 한 DB_OUT 합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-117">The direction of the copy: DB_OUT to the file from the table or view.</span></span>  
  
5.  <span data-ttu-id="e076b-118">[Bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) 를 호출 하 여 열 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-118">Call [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to set the number of columns.</span></span>  
  
6.  <span data-ttu-id="e076b-119">각 열에 대 한 [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) 를 호출 하 여 데이터 파일에서 해당 특성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-119">Call [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column to define its characteristics in the data file.</span></span>  
  
7.  <span data-ttu-id="e076b-120">[Bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) 를 호출 하 여 대량 복사 작업에 의해 생성 되는 데이터 파일을 설명 하는 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-120">Call [bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) to create a format file describing the data file to be created by the bulk copy operation.</span></span>  
  
8.  <span data-ttu-id="e076b-121">[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) 를 호출하여 대량 복사 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-121">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="e076b-122">이러한 방식으로 실행된 대량 복사 작업은 대량 복사된 데이터가 들어 있는 데이터 파일과 데이터 파일의 레이아웃을 설명하는 서식 파일을 모두 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-122">A bulk copy operation run in this way creates both a data file containing the bulk copied data and a format file describing the layout of the data file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e076b-123">예제</span><span class="sxs-lookup"><span data-stu-id="e076b-123">Example</span></span>  
 <span data-ttu-id="e076b-124">AdventureWorks 예제 데이터베이스를 기본 데이터베이스로 사용하는 AdventureWorks라는 ODBC 데이터 원본이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="e076b-125">AdventureWorks 샘플 데이터베이스는 [Microsoft SQL Server 샘플 및 커뮤니티 프로젝트](https://go.microsoft.com/fwlink/?LinkID=85384) 홈 페이지에서 다운로드할 수 있습니다. 이 데이터 원본은 운영 체제에서 제공 하는 ODBC 드라이버를 기반으로 해야 합니다. 드라이버 이름은 "SQL Server"입니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="e076b-126">이 예제를 64비트 운영 체제에서 32비트 애플리케이션으로 작성하여 실행하려는 경우 %windir%\SysWOW64\odbcad32.exe에서 ODBC 관리자를 사용하여 ODBC 데이터 원본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="e076b-127">이 예제는 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e076b-128">명명된 인스턴스에 연결하려면 ODBC 데이터 원본의 정의를 변경하여 server\namedinstance 형식으로 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="e076b-129">기본적으로 [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 는 명명된 인스턴스에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="e076b-130">첫 번째([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 코드 목록을 실행하여 예제에서 사용할 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-130">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="e076b-131">odbc32.lib 및 odbcbcp.lib를 사용하여 두 번째(C++) 코드 목록을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-131">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span>  
  
 <span data-ttu-id="e076b-132">세 번째([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 코드 목록을 실행하여 예제에서 사용한 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e076b-132">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```  
use AdventureWorks  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
  
CREATE TABLE BCPDate (cola int, colb datetime)  
insert BCPDate(cola) values(1)   
insert BCPDate(cola) values(2)   
insert BCPDate(cola) values(3)   
insert BCPDate(cola) values(4)  
```  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
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
  
   // BCP variables.  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_OUT);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the number of output columns.  
   retcode = bcp_columns(hdbc1, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 1 in the data file.  
   retcode = bcp_colfmt(hdbc1, 1, SQLCHARACTER, -1, 5, NULL, 0, 1);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 2 in the data file.  
   retcode = bcp_colfmt(hdbc1, 2, SQLCHARACTER, -1, 20, NULL, 0, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Create the format file.  
   retcode = bcp_writefmt(hdbc1, "c:\\BCPFMT.fmt");  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   return(0);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e076b-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e076b-133">See Also</span></span>  
 <span data-ttu-id="e076b-134">[SQL Server ODBC 드라이버를 사용 하 여 대량 복사 방법 도움말 항목 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="e076b-134">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="e076b-135">데이터 파일 및 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="e076b-135">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
