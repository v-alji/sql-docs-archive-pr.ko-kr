---
title: 비동기 모드 및 SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9071c6821e6edeb577b639223e42899d2927bced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653297"
---
# <a name="asynchronous-mode-and-sqlcancel"></a><span data-ttu-id="75bed-102">비동기 모드와 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="75bed-102">Asynchronous Mode and SQLCancel</span></span>
  <span data-ttu-id="75bed-103">일부 ODBC 함수는 동기적 또는 비동기적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-103">Some ODBC functions can operate either synchronously or asynchronously.</span></span> <span data-ttu-id="75bed-104">애플리케이션에서는 문 핸들이나 연결 핸들에 대해 비동기 작업을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-104">The application can enable asynchronous operations for either a statement handle or a connection handle.</span></span> <span data-ttu-id="75bed-105">연결 핸들에 대해 비동기 작업 옵션을 설정하면 연결 핸들의 모든 문 핸들에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-105">If the option is set for a connection handle, it affects all statement handles on the connection handle.</span></span> <span data-ttu-id="75bed-106">애플리케이션에서는 다음 문을 사용하여 비동기 작업을 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-106">The application uses the following statements to enable or disable asynchronous operations:</span></span>  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="75bed-107">애플리케이션에서 ODBC 함수를 동기 모드로 호출하면 서버가 명령을 완료했다는 알림을 받을 때까지 드라이버가 애플리케이션에 제어를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-107">When an application calls an ODBC function in synchronous mode, the driver does not return control to the application until it is notified that the server has completed the command.</span></span>  
  
 <span data-ttu-id="75bed-108">반면 비동기로 작업을 수행하는 경우 드라이버는 서버에 명령을 보내기 전이라도 즉시 애플리케이션에 제어를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-108">When operating asynchronously, the driver immediately returns control to the application, even before sending the command to the server.</span></span> <span data-ttu-id="75bed-109">드라이버가 반환 코드를 SQL_STILL_EXECUTING으로 설정하여</span><span class="sxs-lookup"><span data-stu-id="75bed-109">The driver sets the return code to SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="75bed-110">애플리케이션이 다른 작업을 수행할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-110">The application can then perform other work.</span></span>  
  
 <span data-ttu-id="75bed-111">명령 실행이 완료되었는지 테스트할 때 애플리케이션은 드라이버에 대해 동일한 매개 변수를 사용하여 동일한 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-111">When the application tests for completion of the command, it makes the same function call with the same parameters to the driver.</span></span> <span data-ttu-id="75bed-112">드라이버는 서버로부터 아직 응답을 받지 않은 경우 다시 SQL_STILL_EXECUTING을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-112">If the driver has not yet received an answer from the server, it will again return SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="75bed-113">애플리케이션은 SQL_STILL_EXECUTING 이외의 코드가 반환될 때까지 명령을 주기적으로 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-113">The application must test the command periodically until the return code is something other than SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="75bed-114">애플리케이션은 다른 반환 코드(SQL_ERROR 포함)가 수신되면 명령이 완료된 것으로 판단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-114">When the application gets some other return code, even SQL_ERROR, it can determine that the command has completed.</span></span>  
  
 <span data-ttu-id="75bed-115">명령이 오랫동안 보류되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-115">Sometimes a command is outstanding for a long time.</span></span> <span data-ttu-id="75bed-116">응용 프로그램이 응답을 기다리지 않고 명령을 취소 해야 하는 경우에는 처리 되지 않은 명령과 동일한 문 핸들을 사용 하 여 **Sqlcancel** 을 호출 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-116">If the application needs to cancel the command without waiting for a reply, it can do so by calling **SQLCancel** with the same statement handle as the outstanding command.</span></span> <span data-ttu-id="75bed-117">이 경우에만 **Sqlcancel** 을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-117">This is the only time **SQLCancel** should be used.</span></span> <span data-ttu-id="75bed-118">일부 프로그래머는 결과 집합을 통해 파트 방법을 처리 하 고 나머지 결과 집합을 취소 하려는 경우 **Sqlcancel** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-118">Some programmers use **SQLCancel** when they have processed part way through a result set and want to cancel the rest of the result set.</span></span> <span data-ttu-id="75bed-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 또는 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 는 **sqlcancel**이 아닌 미해결 결과 집합의 나머지를 취소 하는 데 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75bed-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) should be used to cancel the remainder of an outstanding result set, not **SQLCancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bed-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75bed-120">See Also</span></span>  
 [<span data-ttu-id="75bed-121">SQL Server Native Client ODBC 드라이버 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="75bed-121">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
