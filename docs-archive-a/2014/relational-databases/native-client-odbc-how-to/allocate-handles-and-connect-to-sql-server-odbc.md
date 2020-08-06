---
title: 핸들을 할당 하 고 SQL Server에 연결 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: rothja
ms.author: jroth
ms.openlocfilehash: 615a6dbe966b4c681e9cd4285ff55864d7a13370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742004"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a><span data-ttu-id="bc929-102">핸들 할당 및 SQL Server에 연결(ODBC)</span><span class="sxs-lookup"><span data-stu-id="bc929-102">Allocate Handles and Connect to SQL Server (ODBC)</span></span>
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a><span data-ttu-id="bc929-103">핸들을 할당하고 SQL Server에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="bc929-103">To allocate handles and connect to SQL Server</span></span>  
  
1.  <span data-ttu-id="bc929-104">ODBC 헤더 파일 Sql.h, Sqlext.h, Sqltypes.h을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-104">Include the ODBC header files Sql.h, Sqlext.h, Sqltypes.h.</span></span>  
  
2.  <span data-ttu-id="bc929-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 드라이버별 헤더 파일인 Odbcss.h를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-105">Include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver-specific header file, Odbcss.h.</span></span>  
  
3.  <span data-ttu-id="bc929-106">SQL_HANDLE_ENV를 사용 하 여 [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) 를 호출 `HandleType` 하 여 ODBC를 초기화 하 고 환경 핸들을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-106">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_ENV to initialize ODBC and allocate an environment handle.</span></span>  
  
4.  <span data-ttu-id="bc929-107">SQL_ATTR_ODBC_VERSION로 설정 된 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) 를 호출 하 고를 SQL_OV_ODBC3으로 설정 하 여 `Attribute` `ValuePtr` 응용 프로그램에서 ODBC 3. x 형식의 함수 호출을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-107">Call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with `Attribute` set to SQL_ATTR_ODBC_VERSION and `ValuePtr` set to SQL_OV_ODBC3 to indicate the application will use ODBC 3.x-format function calls.</span></span>  
  
5.  <span data-ttu-id="bc929-108">필요에 따라 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) 를 호출 하 여 다른 환경 옵션을 설정 하거나 [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) 를 호출 하 여 환경 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-108">Optionally, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) to set other environment options, or call [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) to get environment options.</span></span>  
  
6.  <span data-ttu-id="bc929-109">SQL_HANDLE_DBC의를 사용 하 여 [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) 를 호출 `HandleType` 하 여 연결 핸들을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-109">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_DBC to allocate a connection handle.</span></span>  
  
7.  <span data-ttu-id="bc929-110">필요에 따라 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 하 여 연결 옵션을 설정 하거나 [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) 를 호출 하 여 연결 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-110">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set connection options, or call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) to get connection options.</span></span>  
  
8.  <span data-ttu-id="bc929-111">SQLConnect를 호출 하 여 기존 데이터 원본을 사용 하 여에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-111">Call SQLConnect to use an existing data source to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="bc929-112">또는</span><span class="sxs-lookup"><span data-stu-id="bc929-112">Or</span></span>  
  
     <span data-ttu-id="bc929-113">[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 를 호출 하 여 연결 문자열을 사용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) to use a connection string to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="bc929-114">최소 전체 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 문자열은 다음 두 가지 형태 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-114">A minimum complete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection string has one of two forms:</span></span>  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     <span data-ttu-id="bc929-115">연결 문자열이 완료되지 않은 경우 `SQLDriverConnect`에서 필요한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-115">If the connection string is not complete, `SQLDriverConnect` can prompt for the required information.</span></span> <span data-ttu-id="bc929-116">*Drivercompletion* 매개 변수에 지정 된 값으로 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-116">This is controlled by the value specified for the *DriverCompletion* parameter.</span></span>  
  
     <span data-ttu-id="bc929-117">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="bc929-117">\- or -</span></span>  
  
     <span data-ttu-id="bc929-118">[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) 를 반복적으로 여러 번 호출 하 여 연결 문자열을 작성 하 고에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-118">Call [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) multiple times in an iterative fashion to build the connection string and connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="bc929-119">필요에 따라 [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) 를 호출 하 여 데이터 원본에 대 한 드라이버 특성 및 동작을 가져옵니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bc929-119">Optionally, call [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) to get driver attributes and behavior for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span>  
  
10. <span data-ttu-id="bc929-120">문을 할당하고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-120">Allocate and use statements.</span></span>  
  
11. <span data-ttu-id="bc929-121">SQLDisconnect를 호출 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결을 끊고 연결 핸들을 새 연결에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-121">Call SQLDisconnect to disconnect from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and make the connection handle available for a new connection.</span></span>  
  
12. <span data-ttu-id="bc929-122">SQL_HANDLE_DBC의를 사용 하 여 [Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md) `HandleType` 을 호출 하 여 연결 핸들을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-122">Call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) with a `HandleType` of SQL_HANDLE_DBC to free the connection handle.</span></span>  
  
13. <span data-ttu-id="bc929-123">SQL_HANDLE_ENV라는 `SQLFreeHandle`으로 `HandleType`을 호출하여 환경 핸들을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-123">Call `SQLFreeHandle` with a `HandleType` of SQL_HANDLE_ENV to free the environment handle.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc929-124">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="bc929-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="bc929-125">Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-125">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="bc929-126">자격 증명은 파일에 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-126">Avoid storing credentials in a file.</span></span> <span data-ttu-id="bc929-127">자격 증명을 유지 해야 하는 경우에는 [Win32 CRYPTO API](https://go.microsoft.com/fwlink/?LinkId=64532)를 사용 하 여 자격 증명을 암호화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-127">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc929-128">예제</span><span class="sxs-lookup"><span data-stu-id="bc929-128">Example</span></span>  
 <span data-ttu-id="bc929-129">이 예에서는 `SQLDriverConnect` 호출을 통해 ODBC 데이터 원본을 요구하지 않고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-129">This example shows a call to `SQLDriverConnect` to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without requiring an existing ODBC data source.</span></span> <span data-ttu-id="bc929-130">불완전한 연결 문자열을 `SQLDriverConnect`에 전달하면 ODBC 드라이버에서 누락된 정보를 입력하라는 메시지를 사용자에게 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bc929-130">By passing an incomplete connection string to `SQLDriverConnect`, it causes the ODBC driver to prompt the user to enter the missing information.</span></span>  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
