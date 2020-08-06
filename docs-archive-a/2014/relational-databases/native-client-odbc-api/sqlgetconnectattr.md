---
title: SQLGetConnectAttr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: rothja
ms.author: jroth
ms.openlocfilehash: f82a0fb71103e811b36280f9722c160791023e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638759"
---
# <a name="sqlgetconnectattr"></a><span data-ttu-id="6b075-102">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="6b075-102">SQLGetConnectAttr</span></span>
  <span data-ttu-id="6b075-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 드라이버별 연결 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines driver-specific connection attributes.</span></span> <span data-ttu-id="6b075-104">일부 특성은에 사용할 수 `SQLGetConnectAttr` 있으며 함수는 현재 설정을 보고 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-104">Some of the attributes are available to `SQLGetConnectAttr`, and the function is used to report their current settings.</span></span> <span data-ttu-id="6b075-105">이러한 특성에 대해 보고되는 값은 연결을 설정하거나 [SQLSetConnectAttr](sqlsetconnectattr.md)을 사용하여 특성을 설정할 때까지 보장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-105">The values reported for these attributes are not guaranteed until after a connection has been made or the attribute has been set using [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="6b075-106">이 항목에서는 읽기 전용 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-106">This topic lists the read only attributes.</span></span> <span data-ttu-id="6b075-107">다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버별 연결 특성에 대 한 자세한 내용은 [SQLSetConnectAttr](sqlsetconnectattr.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b075-107">For information about the other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific connection attributes, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="sql_copt_ss_connection_dead"></a><span data-ttu-id="6b075-108">SQL_COPT_SS_CONNECTION_DEAD</span><span class="sxs-lookup"><span data-stu-id="6b075-108">SQL_COPT_SS_CONNECTION_DEAD</span></span>  
 <span data-ttu-id="6b075-109">SQL_COPT_SS_CONNECTION_DEAD 특성은 서버에 대한 연결 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-109">The SQL_COPT_SS_CONNECTION_DEAD attribute reports the state of a connection to a server.</span></span> <span data-ttu-id="6b075-110">드라이버는 현재 연결 상태에 대해 네트워크를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-110">The driver queries the network for the current state of the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b075-111">표준 ODBC 연결 특성 SQL_ATTR_CONNECTION_DEAD는 가장 최근 연결 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-111">The standard ODBC connection attribute SQL_ATTR_CONNECTION_DEAD returns the most recent state of the connection.</span></span> <span data-ttu-id="6b075-112">이 상태는 현재 연결 상태가 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-112">This might not be the current connection state.</span></span>  
  
|<span data-ttu-id="6b075-113">값</span><span class="sxs-lookup"><span data-stu-id="6b075-113">Value</span></span>|<span data-ttu-id="6b075-114">Description</span><span class="sxs-lookup"><span data-stu-id="6b075-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b075-115">SQL_CD_TRUE</span><span class="sxs-lookup"><span data-stu-id="6b075-115">SQL_CD_TRUE</span></span>|<span data-ttu-id="6b075-116">서버에 대한 연결이 손실되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-116">The connection to the server has been lost.</span></span>|  
|<span data-ttu-id="6b075-117">SQL_CD_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b075-117">SQL_CD_FALSE</span></span>|<span data-ttu-id="6b075-118">연결이 열려 있으며 문 처리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-118">The connection is open and available for statement processing.</span></span>|  
  
## <a name="sql_copt_ss_client_connection_id"></a><span data-ttu-id="6b075-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span><span class="sxs-lookup"><span data-stu-id="6b075-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span></span>  
 <span data-ttu-id="6b075-120">SQL_COPT_SS_CLIENT_CONNECTION_ID 특성은 클라이언트 연결 ID를 검색하며, 이 ID를 사용하여 다음을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-120">The SQL_COPT_SS_CLIENT_CONNECTION_ID attribute retrieves the client connection ID, which can then be used to locate:</span></span>  
  
-   <span data-ttu-id="6b075-121">설정할 경우 XEvents 로그의 진단 정보</span><span class="sxs-lookup"><span data-stu-id="6b075-121">Diagnostic information in the XEvents log, when enabled.</span></span>  
  
-   <span data-ttu-id="6b075-122">연결 링 버퍼의 연결 오류 정보</span><span class="sxs-lookup"><span data-stu-id="6b075-122">Connection error information in the connection ring buffer.</span></span>  
  
-   <span data-ttu-id="6b075-123">설정할 경우 데이터 액세스 추적 로그의 진단 정보</span><span class="sxs-lookup"><span data-stu-id="6b075-123">Diagnostic information in the data access tracing logs, when enabled.</span></span>  
  
 <span data-ttu-id="6b075-124">자세한 내용은 [확장 이벤트 로그에서 진단 정보에 액세스](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b075-124">For more information, see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
|<span data-ttu-id="6b075-125">값</span><span class="sxs-lookup"><span data-stu-id="6b075-125">Value</span></span>|<span data-ttu-id="6b075-126">Description</span><span class="sxs-lookup"><span data-stu-id="6b075-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b075-127">SQL_ERROR</span><span class="sxs-lookup"><span data-stu-id="6b075-127">SQL_ERROR</span></span>|<span data-ttu-id="6b075-128">연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-128">The connection failed.</span></span>|  
|<span data-ttu-id="6b075-129">SQL_SUCCESS</span><span class="sxs-lookup"><span data-stu-id="6b075-129">SQL_SUCCESS</span></span>|<span data-ttu-id="6b075-130">연결이 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-130">The connection succeeded.</span></span> <span data-ttu-id="6b075-131">출력 버퍼에서 클라이언트 연결 ID를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-131">The client connection ID will be found in the output buffer.</span></span>|  
  
## <a name="sql_copt_ss_perf_data"></a><span data-ttu-id="6b075-132">SQL_COPT_SS_PERF_DATA</span><span class="sxs-lookup"><span data-stu-id="6b075-132">SQL_COPT_SS_PERF_DATA</span></span>  
 <span data-ttu-id="6b075-133">SQL_COPT_SS_PERF_DATA 특성은 현재 드라이버 성능 통계가 포함된 SQLPERF 구조에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-133">The SQL_COPT_SS_PERF_DATA attribute returns a pointer to a SQLPERF structure containing the current driver performance statistics.</span></span> <span data-ttu-id="6b075-134">`SQLGetConnectAttr`성능 로깅이 사용 되지 않는 경우 NULL을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-134">`SQLGetConnectAttr` will return NULL if performance logging is not enabled.</span></span> <span data-ttu-id="6b075-135">SQLPERF 구조의 통계는 드라이버에서 동적으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-135">The statistics in the SQLPERF structure are not dynamically updated by the driver.</span></span> <span data-ttu-id="6b075-136">`SQLGetConnectAttr`성능 통계를 새로 고쳐야 할 때마다를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-136">Call `SQLGetConnectAttr` each time the performance statistics need to be refreshed.</span></span>  
  
|<span data-ttu-id="6b075-137">값</span><span class="sxs-lookup"><span data-stu-id="6b075-137">Value</span></span>|<span data-ttu-id="6b075-138">Description</span><span class="sxs-lookup"><span data-stu-id="6b075-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b075-139">NULL</span><span class="sxs-lookup"><span data-stu-id="6b075-139">NULL</span></span>|<span data-ttu-id="6b075-140">성능 로깅이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-140">Performance logging is not enabled.</span></span>|  
|<span data-ttu-id="6b075-141">다른 모든 값</span><span class="sxs-lookup"><span data-stu-id="6b075-141">Any other value</span></span>|<span data-ttu-id="6b075-142">SQLPERF 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-142">A pointer to a SQLPERF structure.</span></span>|  
  
## <a name="sql_copt_ss_perf_query"></a><span data-ttu-id="6b075-143">SQL_COPT_SS_PERF_QUERY</span><span class="sxs-lookup"><span data-stu-id="6b075-143">SQL_COPT_SS_PERF_QUERY</span></span>  
 <span data-ttu-id="6b075-144">장기 실행 쿼리 로깅이 사용되는 경우 SQL_COPT_SS_PERF_QUERY 특성에서 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-144">The SQL_COPT_SS_PERF_QUERY attribute returns TRUE if logging of long running queries is enabled.</span></span> <span data-ttu-id="6b075-145">쿼리 로깅이 활성화되지 않은 경우 요청에서 FALSE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-145">The request returns FALSE if query logging is not active.</span></span>  
  
## <a name="sql_copt_ss_user_data"></a><span data-ttu-id="6b075-146">SQL_COPT_SS_USER_DATA</span><span class="sxs-lookup"><span data-stu-id="6b075-146">SQL_COPT_SS_USER_DATA</span></span>  
 <span data-ttu-id="6b075-147">SQL_COPT_SS_USER_DATA 특성은 사용자 데이터 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-147">The SQL_COPT_SS_USER_DATA attribute retrieves the user-data pointer.</span></span> <span data-ttu-id="6b075-148">사용자 데이터는 클라이언트 소유의 메모리에 저장되고 연결별로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-148">User data is stored in client-owned memory and recorded per connection.</span></span> <span data-ttu-id="6b075-149">사용자 데이터 포인터가 설정되지 않은 경우 NULL 포인터인 SQL_UD_NOTSET가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-149">If the user-data pointer has not been set, SQL_UD_NOTSET, a NULL pointer, is returned.</span></span>  
  
|<span data-ttu-id="6b075-150">값</span><span class="sxs-lookup"><span data-stu-id="6b075-150">Value</span></span>|<span data-ttu-id="6b075-151">Description</span><span class="sxs-lookup"><span data-stu-id="6b075-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b075-152">SQL_UD_NOTSET</span><span class="sxs-lookup"><span data-stu-id="6b075-152">SQL_UD_NOTSET</span></span>|<span data-ttu-id="6b075-153">사용자 데이터 포인터가 설정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-153">No user-data pointer is set.</span></span>|  
|<span data-ttu-id="6b075-154">다른 모든 값</span><span class="sxs-lookup"><span data-stu-id="6b075-154">Any other value</span></span>|<span data-ttu-id="6b075-155">사용자 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-155">A pointer to the user data.</span></span>|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a><span data-ttu-id="6b075-156">SPN(서비스 사용자 이름)에 대한 SQLGetConnectAttr 지원</span><span class="sxs-lookup"><span data-stu-id="6b075-156">SQLGetConnectAttr Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="6b075-157">SQLGetConnectAttr SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED 및 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 새 연결 특성의 값을 쿼리 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-157">SQLGetConnectAttr can be used to query the value of the new connection attributes SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED, and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD.</span></span> <span data-ttu-id="6b075-158">(SQLGetConnectOption를 사용 하 여 이러한 값을 쿼리할 수도 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="6b075-158">(SQLGetConnectOption can also be used to query these values.)</span></span>  
  
 <span data-ttu-id="6b075-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD는 Windows 인증을 사용하는 열린 연결에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD is only available for open connections that use Windows Authentication.</span></span>  
  
 <span data-ttu-id="6b075-160">SQL_COPT_SS_SERVER_SPN 또는 SQL_COPT_SS_FAILOVER_PARTNER가 설정되지 않은 경우 기본값(빈 문자열)이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b075-160">If SQL_COPT_SS_SERVER_SPN or SQL_COPT_SS_FAILOVER_PARTNER has not been set, the default value (an empty string) is returned.</span></span>  
  
 <span data-ttu-id="6b075-161">Spn에 대 한 자세한 내용은 [클라이언트 연결 &#40;ODBC&#41;에서 spn&#41; &#40;서비스 사용자 이름 ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b075-161">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b075-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b075-162">See Also</span></span>  
 <span data-ttu-id="6b075-163">[SQLGetConnectAttr 함수](https://go.microsoft.com/fwlink/?LinkId=59347) </span><span class="sxs-lookup"><span data-stu-id="6b075-163">[SQLGetConnectAttr Function](https://go.microsoft.com/fwlink/?LinkId=59347) </span></span>  
 <span data-ttu-id="6b075-164">[ODBC API 구현 세부 정보](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="6b075-164">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="6b075-165">[Transact-sql&#41;&#40;QUOTED_IDENTIFIER 설정](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6b075-165">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="6b075-166">[SET ANSI_NULLS&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6b075-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="6b075-167">[SET ANSI_PADDING&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6b075-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="6b075-168">SET ANSI_WARNINGS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b075-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
