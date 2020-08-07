---
title: 오류 및 메시지 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: rothja
ms.author: jroth
ms.openlocfilehash: 4701b3224b87e7d19f1121f193d4be20f9d4c441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730664"
---
# <a name="handling-errors-and-messages"></a><span data-ttu-id="15d1d-102">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="15d1d-102">Handling Errors and Messages</span></span>
  <span data-ttu-id="15d1d-103">애플리케이션이 ODBC 함수를 호출하면 드라이버가 함수를 실행하고 반환 코드와 진단 레코드라는 두 가지 방법으로 진단 정보를 반환합니다. 반환 코드는 ODBC 함수의 전반적인 성공 또는 실패를 나타내고, 진단 레코드는 함수에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-103">When an application calls an ODBC function, the driver executes the function and returns diagnostic information in two ways: A return code indicates the overall success or failure of an ODBC function, and diagnostic records provide detailed information about the function.</span></span> <span data-ttu-id="15d1d-104">진단 레코드에는 헤더 레코드 및 상태 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-104">Diagnostic records include a header record and status records.</span></span> <span data-ttu-id="15d1d-105">함수가 성공하더라도 한 개 이상의 진단 레코드, 즉 헤더 레코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-105">At least one diagnostic record, the header record, is returned even if the function succeeds.</span></span>  
  
 <span data-ttu-id="15d1d-106">진단 정보는 개발 과정에서 잘못된 핸들이나 하드 코딩된 SQL 문의 구문 오류와 같은 프로그래밍 오류를 파악하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-106">Diagnostic information is used at development time to catch programming errors, such as invalid handles and syntax errors in hard-coded SQL statements.</span></span> <span data-ttu-id="15d1d-107">이 밖에도 런타임에 데이터 잘림, 규칙 위반 및 사용자가 입력한 SQL 문의 구문 오류와 같은 런타임 오류 및 경고를 파악하는 데도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-107">It is also used at run time to catch run-time errors and warnings, such as data truncation, rule violations, and syntax errors in SQL statements entered by the user.</span></span> <span data-ttu-id="15d1d-108">프로그램 논리는 일반적으로 반환 코드에 기반을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-108">Program logic is generally based on return codes.</span></span>  
  
 <span data-ttu-id="15d1d-109">예를 들어 응용 프로그램이 **Sqlfetch** 를 호출 하 여 결과 집합의 행을 검색 한 후 반환 코드는 결과 집합의 끝에 도달 했는지 (SQL_NO_DATA), 정보 메시지가 반환 되었는지 (SQL_SUCCESS_WITH_INFO) 또는 오류가 발생 한 경우 (SQL_ERROR)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-109">For example, after an application calls **SQLFetch** to retrieve the rows in a result set, the return code indicates whether the end of the result set was reached (SQL_NO_DATA), if any informational messages were returned (SQL_SUCCESS_WITH_INFO), or if an error occurred (SQL_ERROR).</span></span>  
  
 <span data-ttu-id="15d1d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버가 SQL_SUCCESS 이외의 값을 반환 하는 경우 응용 프로그램은 **SQLGetDiagRec** 를 호출 하 여 정보 또는 오류 메시지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-110">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns anything other than SQL_SUCCESS, the application can call **SQLGetDiagRec** to retrieve any informational or error messages.</span></span> <span data-ttu-id="15d1d-111">둘 이상의 메시지가 있는 경우 **SQLGetDiagRec** 를 사용 하 여 메시지 집합을 위아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-111">Use **SQLGetDiagRec** to scroll up and down the message set if there is more than one message.</span></span>  
  
 <span data-ttu-id="15d1d-112">반환 코드 SQL_INVALID_HANDLE은 항상 프로그래밍 오류를 나타내며 런타임에 발생하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-112">The return code SQL_INVALID_HANDLE always indicates a programming error and should never be encountered at run time.</span></span> <span data-ttu-id="15d1d-113">다른 모든 반환 코드는 런타임 정보를 나타내며 SQL_ERROR는 프로그래밍 오류를 나타내는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-113">All other return codes provide run-time information, although SQL_ERROR may indicate a programming error.</span></span>  
  
 <span data-ttu-id="15d1d-114">원래 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네이티브 API 인 C 용 db-library를 사용 하면 응용 프로그램에서 오류 또는 메시지를 반환 하는 콜백 오류 처리 및 메시지 처리 함수를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-114">The original [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native API, DB-Library for C, allows an application to install callback error-handling and message-handling functions that return errors or messages.</span></span> <span data-ttu-id="15d1d-115">PRINT, RAISERROR, DBCC 및 SET과 같은 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 결과를 결과 집합이 아닌 DB-Library 메시지 처리기 함수로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-115">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, such as PRINT, RAISERROR, DBCC, and SET, return their results to the DB-Library message handler function instead of to a result set.</span></span> <span data-ttu-id="15d1d-116">그러나 ODBC API에는 이러한 콜백 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-116">However, the ODBC API has no such callback capability.</span></span> <span data-ttu-id="15d1d-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버가에서 반환 된 메시지를 검색 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] odbc 반환 코드를 SQL_SUCCESS_WITH_INFO 또는 SQL_ERROR로 설정 하 고 메시지를 하나 이상의 진단 레코드로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver detects messages coming back from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it sets the ODBC return code to SQL_SUCCESS_WITH_INFO or SQL_ERROR and returns the message as one or more diagnostic records.</span></span> <span data-ttu-id="15d1d-118">따라서 ODBC 응용 프로그램은 이러한 반환 코드를 신중 하 게 테스트 하 고 **SQLGetDiagRec** 를 호출 하 여 메시지 데이터를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15d1d-118">Therefore, an ODBC application must carefully test for these return codes and call **SQLGetDiagRec** to retrieve message data.</span></span>  
  
 <span data-ttu-id="15d1d-119">오류 추적에 대한 자세한 내용은 [데이터 액세스 추적](https://go.microsoft.com/fwlink/?LinkId=125805)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15d1d-119">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="15d1d-120">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에 추가된 오류 추적의 향상된 기능에 대한 자세한 내용은 [확장 이벤트 로그의 진단 정보 액세스](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15d1d-120">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15d1d-121">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="15d1d-121">In This Section</span></span>  
  
-   [<span data-ttu-id="15d1d-122">메시지를 생성하는 문 처리</span><span class="sxs-lookup"><span data-stu-id="15d1d-122">Processing Statements That Generate Messages</span></span>](processing-statements-that-generate-messages.md)  
  
-   [<span data-ttu-id="15d1d-123">진단 레코드 및 필드</span><span class="sxs-lookup"><span data-stu-id="15d1d-123">Diagnostic Records and Fields</span></span>](diagnostic-records-and-fields.md)  
  
-   [<span data-ttu-id="15d1d-124">원시 오류 번호</span><span class="sxs-lookup"><span data-stu-id="15d1d-124">Native Error Numbers</span></span>](native-error-numbers.md)  
  
-   [<span data-ttu-id="15d1d-125">SQLSTATE &#40;ODBC 오류 코드&#41;</span><span class="sxs-lookup"><span data-stu-id="15d1d-125">SQLSTATE &#40;ODBC Error Codes&#41;</span></span>](sqlstate-odbc-error-codes.md)  
  
-   [<span data-ttu-id="15d1d-126">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="15d1d-126">Error Messages</span></span>](error-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="15d1d-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15d1d-127">See Also</span></span>  
 [<span data-ttu-id="15d1d-128">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="15d1d-128">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
