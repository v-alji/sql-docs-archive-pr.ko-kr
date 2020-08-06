---
title: SQLDriverConnect | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 40691dfb381883b59155607fb56f4933820e3e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736310"
---
# <a name="sqldriverconnect"></a><span data-ttu-id="8e923-102">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="8e923-102">SQLDriverConnect</span></span>
  <span data-ttu-id="8e923-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 연결 문자열 키워드를 대체하거나 개선하는 연결 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines connection attributes that either replace or enhance connection-string keywords.</span></span> <span data-ttu-id="8e923-104">몇 가지 연결 문자열 키워드에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버가 지정한 기본값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-104">Several connection-string keywords have default values specified by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="8e923-105">Native Client ODBC 드라이버에서 사용할 수 있는 키워드 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server Native Client와 연결 문자열 키워드 사용](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e923-105">For a list of the keywords available in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="8e923-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결 특성 및 드라이버 기본 동작에 대 한 자세한 내용은 [SQLSetConnectAttr](sqlsetconnectattr.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e923-106">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection attributes and driver default behaviors, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="8e923-107">Native Client에 유효한 연결 문자열 키워드에 대 한 설명은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server Native Client 연결 문자열 키워드 사용](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e923-107">For a discussion of connection string keywords that are valid for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="8e923-108">`SQLDriverConnect` *Drivercompletion* 매개 변수 값이 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE 또는 SQL_DRIVER_COMPLETE_REQUIRED 인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 표시 된 대화 상자에서 키워드 값을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-108">When the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, or SQL_DRIVER_COMPLETE_REQUIRED, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver retrieves keyword values from the displayed dialog box.</span></span> <span data-ttu-id="8e923-109">키워드 값이 연결 문자열에서 전달되었고 사용자가 대화 상자에서 키워드 값을 변경하지 않은 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 연결 문자열의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-109">If the keyword value is passed in the connection string and the user does not alter the value for the keyword in the dialog box, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses the value from the connection string.</span></span> <span data-ttu-id="8e923-110">키워드 값이 연결 문자열에서 설정되지 않았고 사용자가 대화 상자에서 키워드 값을 지정하지 않은 경우 드라이버는 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-110">If the value is not set in the connection string and the user makes no assignment in the dialog box, the driver uses the default.</span></span>  
  
 <span data-ttu-id="8e923-111">`SQLDriverConnect`*Drivercompletion* 값에는 드라이버의 연결 대화 상자를 표시 해야 하거나 필요한 경우 올바른 *WindowHandle* 를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-111">`SQLDriverConnect` must be given a valid *WindowHandle* when any *DriverCompletion* value requires (or could require) the display of the driver's connection dialog box.</span></span> <span data-ttu-id="8e923-112">잘못된 핸들을 지정하면 SQL_ERROR가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-112">An invalid handle returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="8e923-113">DRIVER 또는 DSN 키워드 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-113">Specify either the DRIVER or DSN keywords.</span></span> <span data-ttu-id="8e923-114">둘 모두 지정한 경우 ODBC 드라이버는 이 두 키워드 중 왼쪽의 키워드를 사용하고 다른 하나는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-114">ODBC states that a driver uses the leftmost of these two keywords and ignores the other if both are specified.</span></span> <span data-ttu-id="8e923-115">드라이버가 지정 된 경우 또는이 둘 중 가장 왼쪽 이며 `SQLDriverConnect` *drivercompletion* 매개 변수 값이 SQL_DRIVER_NOPROMPT 이면 서버 키워드와 적절 한 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-115">If DRIVER is specified, or is the leftmost of the two, and the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT, the SERVER keyword and an appropriate value are required.</span></span>  
  
 <span data-ttu-id="8e923-116">SQL_DRIVER_NOPROMPT를 지정하는 경우에는 사용자 인증 키워드를 값과 함께 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-116">When SQL_DRIVER_NOPROMPT is specified, user authentication keywords must be present with values.</span></span> <span data-ttu-id="8e923-117">드라이버는 문자열 "Trusted_Connection=yes" 또는 UID와 PWD 키워드가 제공되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-117">The driver ensures that either the string "Trusted_Connection=yes" or both the UID and PWD keywords are present.</span></span>  
  
 <span data-ttu-id="8e923-118">*Drivercompletion* 매개 변수 값이 SQL_DRIVER_NOPROMPT 또는 SQL_DRIVER_COMPLETE_REQUIRED이 고 언어 또는 데이터베이스가 연결 문자열에서 제공 되 고가 유효 하지 않은 경우는 `SQLDriverConnect` SQL_ERROR을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-118">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the connection string and either is invalid, `SQLDriverConnect` returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="8e923-119">*Drivercompletion* 매개 변수 값이 SQL_DRIVER_NOPROMPT 또는 SQL_DRIVER_COMPLETE_REQUIRED이 고 언어나 데이터베이스가 ODBC 데이터 원본 정의에서 제공 되 고 잘못 된 경우는 지정 된 `SQLDriverConnect` 사용자 ID에 대해 기본 언어나 데이터베이스를 사용 하 고 SQL_SUCCESS_WITH_INFO을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-119">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the ODBC data source definitions and either is invalid, `SQLDriverConnect` uses the default language or database for the specified user ID and returns SQL_SUCCESS_WITH_INFO.</span></span>  
  
 <span data-ttu-id="8e923-120">*Drivercompletion* 매개 변수 값이 SQL_DRIVER_COMPLETE 또는 SQL_DRIVER_PROMPT이 고 언어나 데이터베이스가 잘못 된 경우 대화 상자를 더 합니다 `SQLDriverConnect` .</span><span class="sxs-lookup"><span data-stu-id="8e923-120">If the *DriverCompletion* parameter value is SQL_DRIVER_COMPLETE or SQL_DRIVER_PROMPT and if the language or database is invalid, `SQLDriverConnect` redisplays the dialog box.</span></span>  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="8e923-121">고가용성 재해 복구를 위한 SQLDriverConnect 지원</span><span class="sxs-lookup"><span data-stu-id="8e923-121">SQLDriverConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="8e923-122">를 사용 하 여 클러스터에 연결 하는 방법에 대 한 자세한 내용은 `SQLDriverConnect` [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] [고가용성, 재해 복구를 위한 SQL Server Native Client 지원](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e923-122">For more information about using `SQLDriverConnect` to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a><span data-ttu-id="8e923-123">SPN(서비스 사용자 이름)에 대한 SQLDriverConnect 지원</span><span class="sxs-lookup"><span data-stu-id="8e923-123">SQLDriverConnect Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="8e923-124">SQLDDriverConnect는 프롬프트를 사용 하도록 설정 하면 ODBC 로그인 대화 상자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-124">SQLDDriverConnect will use the ODBC Login dialog boxwhen prompting is enabled.</span></span> <span data-ttu-id="8e923-125">이를 통해 주 서버 및 해당 장애 조치(Failover) 파트너 모두에 대한 SPN이 입력되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-125">This allows SPNs to be entered for both the principal server and its failover partner.</span></span>  
  
 <span data-ttu-id="8e923-126">SQLDriverConnect는 새 연결 문자열 키워드 및를 수락 하 고 `ServerSPN` `FailoverPartnerSPN` SQL_COPT_SS_SERVER_SPN SQL_COPT_SS_FAILOVER_PARTNER_SPN 새 연결 특성을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-126">SQLDriverConnect will accept the new connection string keywords `ServerSPN` and `FailoverPartnerSPN`, and will recognize the new connection attributes SQL_COPT_SS_SERVER_SPN and SQL_COPT_SS_FAILOVER_PARTNER_SPN.</span></span>  
  
 <span data-ttu-id="8e923-127">연결 특성 값이 두 번 이상 지정된 경우 프로그래밍 방식으로 설정된 값이 DSN의 값 및 연결 문자열의 값보다 우선 순위가 높고</span><span class="sxs-lookup"><span data-stu-id="8e923-127">When a connection attribute value is specified more than once, a value that is set programmatically takes precedence over the value in a DSN and a value in a connection string.</span></span> <span data-ttu-id="8e923-128">DSN의 값이 연결 문자열의 값보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-128">A value in a DSN takes precedence over a value in a connection string.</span></span>  
  
 <span data-ttu-id="8e923-129">연결이 열릴 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 및 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD를 연결을 여는 데 사용하는 인증 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-129">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span>  
  
 <span data-ttu-id="8e923-130">Spn에 대 한 자세한 내용은 [클라이언트 연결 &#40;ODBC&#41;에서 spn&#41; &#40;서비스 사용자 이름 ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e923-130">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8e923-131">예</span><span class="sxs-lookup"><span data-stu-id="8e923-131">Examples</span></span>  
 <span data-ttu-id="8e923-132">다음 호출에서는에 필요한 최소한의 데이터를 보여 줍니다 `SQLDriverConnect` .</span><span class="sxs-lookup"><span data-stu-id="8e923-132">The following call illustrates the least amount of data required for `SQLDriverConnect`:</span></span>  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 <span data-ttu-id="8e923-133">다음 연결 문자열은 *Drivercompletion* 매개 변수 값이 SQL_DRIVER_NOPROMPT 경우 필요한 최소 데이터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e923-133">The following connection strings illustrate minimum required data when the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT:</span></span>  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e923-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e923-134">See Also</span></span>  
 <span data-ttu-id="8e923-135">[SQLDriverConnect 함수](https://go.microsoft.com/fwlink/?LinkId=59340) </span><span class="sxs-lookup"><span data-stu-id="8e923-135">[SQLDriverConnect Function](https://go.microsoft.com/fwlink/?LinkId=59340) </span></span>  
 <span data-ttu-id="8e923-136">[ODBC API 구현 세부 정보](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="8e923-136">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="8e923-137">[SET ANSI_NULLS&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e923-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="8e923-138">[SET ANSI_PADDING&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8e923-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="8e923-139">SET ANSI_WARNINGS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8e923-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
