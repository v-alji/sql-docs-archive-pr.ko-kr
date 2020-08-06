---
title: SQL Server Native Client의 새로운 기능&#39;| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: rothja
ms.author: jroth
ms.openlocfilehash: f7a8fdd6716f7ba571ed8d1d8b5f959666961aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661086"
---
# <a name="what39s-new-in-sql-server-native-client"></a><span data-ttu-id="9d30b-102">SQL Server Native Client의 새로운 기능&#39;</span><span class="sxs-lookup"><span data-stu-id="9d30b-102">What&#39;s New in SQL Server Native Client</span></span>
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]<span data-ttu-id="9d30b-103">는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client를 설치하며,</span><span class="sxs-lookup"><span data-stu-id="9d30b-103">installs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span> <span data-ttu-id="9d30b-104">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-104">There is no [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="9d30b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서 ODBC 드라이버에 대한 업데이트는 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-105">There will be no more updates to the ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="9d30b-106">Windows에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Driver 11 for [!INCLUDE[msCoName](../../includes/msconame-md.md)]이라 불리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client의 후속 ODBC 드라이버는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]와 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-106">The successor to the ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, which is called the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Windows, is installed with [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="9d30b-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows 기반 Odbc driver 11 for에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Microsoft odbc driver 11 For SQL Server-Windows](https://www.microsoft.com/download/details.aspx?id=36434)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d30b-107">For more information about the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Windows, see [Microsoft ODBC Driver 11 for SQL Server - Windows](https://www.microsoft.com/download/details.aspx?id=36434).</span></span>  
  
 <span data-ttu-id="9d30b-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client의 OLE DB 공급자는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client에서 마지막으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-108">The OLE DB Provider in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client was last updated in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span> <span data-ttu-id="9d30b-109">OLE DB 공급자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 최신 버전에 연결하려는 개발자는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client에서 제공되는 OLE DB 공급자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-109">Developers who wish to use an OLE DB provider to connect to the latest version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must use the OLE DB provider that shipped in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="9d30b-110">다음 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 새로운 주요 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-110">The following topics describe significant new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client features in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
-   [<span data-ttu-id="9d30b-111">LocalDB에 대한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="9d30b-111">SQL Server Native Client Support for LocalDB</span></span>](features/sql-server-native-client-support-for-localdb.md)  
  
-   [<span data-ttu-id="9d30b-112">메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="9d30b-112">Metadata Discovery</span></span>](features/metadata-discovery.md)  
  
-   [<span data-ttu-id="9d30b-113">SQL Server Native Client 11.0의 UTF-16 지원</span><span class="sxs-lookup"><span data-stu-id="9d30b-113">UTF-16 Support in SQL Server Native Client 11.0</span></span>](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [<span data-ttu-id="9d30b-114">고가용성 재해 복구를 위한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="9d30b-114">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="9d30b-115">확장 이벤트 로그의 진단 정보 액세스</span><span class="sxs-lookup"><span data-stu-id="9d30b-115">Accessing Diagnostic Information in the Extended Events Log</span></span>](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 <span data-ttu-id="9d30b-116">또한 이제 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client의 ODBC에서는 Windows 7 SDK의 표준 ODBC에 추가된 다음과 같은 3가지 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-116">In addition, ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client now supports three features that were added to standard ODBC in the Windows 7 SDK:</span></span>  
  
-   <span data-ttu-id="9d30b-117">연결 관련 작업에 대한 비동기 실행.</span><span class="sxs-lookup"><span data-stu-id="9d30b-117">Asynchronous execution on connection-related operations.</span></span> <span data-ttu-id="9d30b-118">자세한 내용은 [비동기 실행](https://go.microsoft.com/fwlink/?LinkID=191493)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-118">For more information, see [Asynchronous Execution](https://go.microsoft.com/fwlink/?LinkID=191493).</span></span>  
  
-   <span data-ttu-id="9d30b-119">C 데이터 형식 확장성.</span><span class="sxs-lookup"><span data-stu-id="9d30b-119">C Data Type Extensibility.</span></span> <span data-ttu-id="9d30b-120">자세한 내용은 [ODBC의 C 데이터 형식](https://go.microsoft.com/fwlink/?LinkID=191495)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-120">For more information, see [C Data Types in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).</span></span>  
  
     <span data-ttu-id="9d30b-121">Native Client에서이 기능을 지원 하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLGetDescField는 `SQL_C_SS_TIME2` `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` 응용 프로그램에서 ODBC 3.8를 사용 하는 경우 대신 (형식) 또는 (의 경우)를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-121">To support this feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, SQLGetDescField can return `SQL_C_SS_TIME2` (for `time` types) or `SQL_C_SS_TIMESTAMPOFFSET` (for `datetimeoffset`) instead of `SQL_C_BINARY`, if your application uses ODBC 3.8.</span></span> <span data-ttu-id="9d30b-122">자세한 내용은 [ODBC 날짜 및 시간 향상을 위한 데이터 형식 지원](features/date-and-time-improvements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-122">For more information, see [Data Type Support for ODBC Date and Time Improvements](features/date-and-time-improvements.md).</span></span>  
  
-   <span data-ttu-id="9d30b-123">큰 매개 변수 값을 검색하기 위해 작은 버퍼로 여러 번 `SQLGetData` 호출.</span><span class="sxs-lookup"><span data-stu-id="9d30b-123">Calling `SQLGetData` with a small buffer multiple times to retrieve a large parameter value.</span></span> <span data-ttu-id="9d30b-124">자세한 내용은 [SQLGetData를 사용 하 여 출력 매개 변수 검색](https://go.microsoft.com/fwlink/?LinkID=191494)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-124">For more information, see [Retrieving Output Parameters Using SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).</span></span>  
  
 <span data-ttu-id="9d30b-125">다음 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서의 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 동작 변경에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-125">The following topics describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client behavior changes in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
-   <span data-ttu-id="9d30b-126">를 호출 하는 경우 `ICommandWithParameters::SetParameterInfo` *pwszName* 매개 변수에 전달 된 값은 올바른 식별자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-126">When calling `ICommandWithParameters::SetParameterInfo`, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="9d30b-127">자세한 내용은 [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-127">For more information, see [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md).</span></span>  
  
-   <span data-ttu-id="9d30b-128">`SQLDescribeParam`은 이제 ODBC 사양을 따르는 값을 일관성 있게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9d30b-128">`SQLDescribeParam` will now consistently return a value that conforms to the ODBC specification.</span></span> <span data-ttu-id="9d30b-129">자세한 내용은 [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d30b-129">For more information, see [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md).</span></span>  
  
-   [<span data-ttu-id="9d30b-130">문자 변환을 처리 시 ODBC 드라이버 동작 변경</span><span class="sxs-lookup"><span data-stu-id="9d30b-130">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a><span data-ttu-id="9d30b-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d30b-131">See Also</span></span>  
 [<span data-ttu-id="9d30b-132">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="9d30b-132">SQL Server Native Client Features</span></span>](features/sql-server-native-client-features.md)  
  
  
