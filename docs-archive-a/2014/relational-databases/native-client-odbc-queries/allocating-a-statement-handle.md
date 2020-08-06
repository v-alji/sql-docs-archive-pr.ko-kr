---
title: 문 핸들 할당 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741984"
---
# <a name="allocating-a-statement-handle"></a><span data-ttu-id="0af9e-102">문 핸들 할당</span><span class="sxs-lookup"><span data-stu-id="0af9e-102">Allocating a Statement Handle</span></span>
  <span data-ttu-id="0af9e-103">애플리케이션에서 문을 실행하려면 먼저 문 핸들을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-103">Before an application can execute a statement, it must allocate a statement handle.</span></span> <span data-ttu-id="0af9e-104">*HandleType* 매개 변수가 SQL_HANDLE_STMT로 설정 되 고 연결 핸들을 가리키는 *InputHandle* **를 호출 하 여이** 를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-104">It does this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_STMT and *InputHandle* pointing to a connection handle.</span></span>  
  
 <span data-ttu-id="0af9e-105">문 특성은 문 핸들의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-105">Statement attributes are characteristics of the statement handle.</span></span> <span data-ttu-id="0af9e-106">문 특성의 예로는 책갈피 사용 여부 및 문의 결과 집합에 사용할 커서의 종류를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-106">Sample statement attributes can include using bookmarks and the kind of cursor to use with the statement's result set.</span></span> <span data-ttu-id="0af9e-107">[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)를 사용 하 여 문 특성을 설정 하 고 [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)를 사용 하 여 현재 설정을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-107">Statement attributes are set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), and their current settings are retrieved by using [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md).</span></span> <span data-ttu-id="0af9e-108">애플리케이션에서 반드시 문 특성을 설정할 필요는 없습니다. 모든 문 특성에는 기본값이 있으며 일부 문 특성은 드라이버에 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-108">There is no requirement that an application set any statement attributes; all statement attributes have defaults, and some are driver specific.</span></span>  
  
 <span data-ttu-id="0af9e-109">몇 가지 ODBC 문 및 연결 옵션을 사용할 때는 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-109">Use caution in the use of several ODBC statement and connection options.</span></span> <span data-ttu-id="0af9e-110">*Foption* 을 SQL_ATTR_LOGIN_TIMEOUT로 설정 하 여 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출 하면 연결을 설정 하려고 대기 하는 동안 응용 프로그램에서 시간 초과가 발생 하기 전까지 대기 하는 시간을 제어 합니다 (0은 무한 대기를 지정 합니다).</span><span class="sxs-lookup"><span data-stu-id="0af9e-110">Calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with *fOption* set to SQL_ATTR_LOGIN_TIMEOUT controls the time that an application waits for a connection attempt to time-out while waiting to establish a connection (0 specifies an infinite wait).</span></span> <span data-ttu-id="0af9e-111">응답 시간이 느린 사이트의 경우 이 값을 높게 설정하여 연결을 완료하는 데 충분한 시간을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-111">Sites that have slow response times can set this value high to make sure that connections have sufficient time to be completed.</span></span> <span data-ttu-id="0af9e-112">그러나 드라이버에서 연결할 수 없는 경우 사용자에게 적절한 시간 내에 응답되도록 간격을 항상 적절하게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-112">However, the interval should always be low enough to give the user a response in a reasonable time if the driver cannot connect.</span></span>  
  
 <span data-ttu-id="0af9e-113">*Foption* 을 SQL_ATTR_QUERY_TIMEOUT로 설정 하 여 **SQLSetStmtAttr** 를 호출 하면 서버 및 사용자가 장기 실행 쿼리를 보호 하는 데 도움이 되는 쿼리 시간 제한 간격이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-113">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_QUERY_TIMEOUT sets a query time-out interval to help protect the server and the user from long-running queries.</span></span>  
  
 <span data-ttu-id="0af9e-114">*Foption* 을 SQL_ATTR_MAX_LENGTH로 설정 하 여 **SQLSetStmtAttr** 를 호출 하면 개별 문이 검색할 수 있는 **텍스트** 및 **이미지** 데이터의 양이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-114">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_LENGTH limits the amount of **text** and **image** data that an individual statement can retrieve.</span></span> <span data-ttu-id="0af9e-115">*Foption* 을 SQL_ATTR_MAX_ROWS로 설정 하 여 **SQLSetStmtAttr** 를 호출 하면 모든 응용 프로그램에 필요한 경우 행 집합을 처음 *n 개* 행으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-115">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_ROWS also limits a rowset to the first *n* rows if that is all the application requires.</span></span> <span data-ttu-id="0af9e-116">SQL_ATTR_MAX_ROWS를 설정하면 드라이버가 서버에 대해 SET ROWCOUNT 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-116">Note that setting SQL_ATTR_MAX_ROWS causes the driver to issue a SET ROWCOUNT statement to the server.</span></span> <span data-ttu-id="0af9e-117">이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 트리거와 업데이트를 포함 하 여 모든 문에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-117">This affects all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements, including triggers and updates.</span></span>  
  
 <span data-ttu-id="0af9e-118">따라서 이러한 옵션을 설정할 때는 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-118">Use caution when you are setting these options.</span></span> <span data-ttu-id="0af9e-119">연결 핸들의 모든 문 핸들에 대한 SQL_ATTR_MAX_LENGTH 및 SQL_ATTR_MAX_ROWS 설정을 동일하게 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-119">It is best if all statement handles on a connection handle have the same settings for SQL_ATTR_MAX_LENGTH and SQL_ATTR_MAX_ROWS.</span></span> <span data-ttu-id="0af9e-120">드라이버가 특정 문 핸들에서 이들 옵션 값이 다르게 설정된 다른 핸들로 전환하는 경우 설정을 변경하려면 드라이버가 적절한 SET TEXTSIZE 및 SET ROWCOUNT 문을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-120">If the driver switches from a statement handle to another with different values for these options, the driver must generate the appropriate SET TEXTSIZE and SET ROWCOUNT statements to change the settings.</span></span> <span data-ttu-id="0af9e-121">사용자 SQL 문은 일괄 처리의 첫 번째 문을 포함할 수 있으므로 드라이버는 이러한 문을 사용자 SQL 문과 동일한 일괄 처리에 배치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-121">The driver cannot put these statements in the same batch as the user SQL statement because the user SQL statement can contain a statement that must be the first statement in a batch.</span></span> <span data-ttu-id="0af9e-122">드라이버는 SET TEXTSIZE 문과 SET ROWCOUNT 문을 별개의 일괄 처리로 보내야 하며 이 경우 추가 서버 왕복이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0af9e-122">The driver must send the SET TEXTSIZE and SET ROWCOUNT statements in a separate batch, which automatically generates an additional roundtrip to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af9e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0af9e-123">See Also</span></span>  
 [<span data-ttu-id="0af9e-124">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="0af9e-124">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
