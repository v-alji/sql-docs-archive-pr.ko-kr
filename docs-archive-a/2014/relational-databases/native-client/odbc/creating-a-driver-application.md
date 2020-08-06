---
title: SQL Server Native Client ODBC 드라이버 응용 프로그램 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c8a1719f8b60885810d9b2f8a1f1023a7ffe6e47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738223"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a><span data-ttu-id="0cf7c-102">SQL Server Native Client ODBC 드라이버 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="0cf7c-102">Creating a SQL Server Native Client ODBC Driver Application</span></span>
  <span data-ttu-id="0cf7c-103">ODBC 아키텍처에는 다음과 같은 기능을 수행하는 네 가지 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-103">ODBC architecture has four components that perform the following functions.</span></span>  
  
|<span data-ttu-id="0cf7c-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0cf7c-104">Component</span></span>|<span data-ttu-id="0cf7c-105">기능</span><span class="sxs-lookup"><span data-stu-id="0cf7c-105">Function</span></span>|  
|---------------|--------------|  
|<span data-ttu-id="0cf7c-106">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="0cf7c-106">Application</span></span>|<span data-ttu-id="0cf7c-107">ODBC 데이터 원본과 통신하는 ODBC 함수를 호출하고, SQL 문을 전송하고, 결과 집합을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-107">Calls ODBC functions to communicate with an ODBC data source, submits SQL statements, and processes result sets.</span></span>|  
|<span data-ttu-id="0cf7c-108">드라이버 관리자</span><span class="sxs-lookup"><span data-stu-id="0cf7c-108">Driver Manager</span></span>|<span data-ttu-id="0cf7c-109">애플리케이션과 애플리케이션에서 사용하는 모든 ODBC 드라이버 사이의 통신을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-109">Manages communication between an application and all ODBC drivers used by the application.</span></span>|  
|<span data-ttu-id="0cf7c-110">드라이버</span><span class="sxs-lookup"><span data-stu-id="0cf7c-110">Driver</span></span>|<span data-ttu-id="0cf7c-111">애플리케이션으로부터의 모든 ODBC 호출을 처리하고, 데이터 원본에 연결하고, 애플리케이션에서 데이터 원본으로 SQL 문을 전달하고, 애플리케이션에 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-111">Processes all ODBC function calls from the application, connects to a data source, passes SQL statements from the application to the data source, and returns results to the application.</span></span> <span data-ttu-id="0cf7c-112">필요한 경우 드라이버는 애플리케이션에서 전달된 ODBC SQL을 데이터 원본에서 사용하는 기본 SQL로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-112">If necessary, the driver translates ODBC SQL from the application to native SQL used by the data source.</span></span>|  
|<span data-ttu-id="0cf7c-113">데이터 원본</span><span class="sxs-lookup"><span data-stu-id="0cf7c-113">Data source</span></span>|<span data-ttu-id="0cf7c-114">드라이버가 DBMS의 특정 데이터 인스턴스에 액세스하는 데 필요한 모든 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-114">Contains all information a driver needs to access a specific instance of data in a DBMS.</span></span>|  
  
 <span data-ttu-id="0cf7c-115">Native Client ODBC 드라이버를 사용 하 여 인스턴스와 통신 하는 응용 프로그램은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-115">An application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to communicate with an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs the following tasks:</span></span>  
  
-   <span data-ttu-id="0cf7c-116">데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="0cf7c-116">Connects with a data source</span></span>  
  
-   <span data-ttu-id="0cf7c-117">데이터 원본에 SQL 문 전송</span><span class="sxs-lookup"><span data-stu-id="0cf7c-117">Sends SQL statements to the data source</span></span>  
  
-   <span data-ttu-id="0cf7c-118">데이터 원본에서 문의 결과 처리</span><span class="sxs-lookup"><span data-stu-id="0cf7c-118">Processes the results of statements from the data source</span></span>  
  
-   <span data-ttu-id="0cf7c-119">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="0cf7c-119">Processes errors and messages</span></span>  
  
-   <span data-ttu-id="0cf7c-120">데이터 원본에 대한 연결 종료</span><span class="sxs-lookup"><span data-stu-id="0cf7c-120">Terminates the connection to the data source</span></span>  
  
 <span data-ttu-id="0cf7c-121">Native Client ODBC 드라이버에 대해 작성 된 더 복잡 한 응용 프로그램은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 다음 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-121">A more complex application written for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver might also perform the following tasks:</span></span>  
  
-   <span data-ttu-id="0cf7c-122">커서를 사용하여 결과 집합에서 위치 제어</span><span class="sxs-lookup"><span data-stu-id="0cf7c-122">Use cursors to control location in a result set</span></span>  
  
-   <span data-ttu-id="0cf7c-123">트랜잭션 컨트롤에 대해 커밋 또는 롤백 작업 요청</span><span class="sxs-lookup"><span data-stu-id="0cf7c-123">Request commit or rollback operations for transaction control</span></span>  
  
-   <span data-ttu-id="0cf7c-124">둘 이상의 서버가 관련된 분산 트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="0cf7c-124">Perform distributed transactions involving two or more servers</span></span>  
  
-   <span data-ttu-id="0cf7c-125">원격 서버에서 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="0cf7c-125">Run stored procedures on the remote server</span></span>  
  
-   <span data-ttu-id="0cf7c-126">카탈로그 함수를 호출하여 결과 집합의 특성 조회</span><span class="sxs-lookup"><span data-stu-id="0cf7c-126">Call catalog functions to inquire about the attributes of a result set</span></span>  
  
-   <span data-ttu-id="0cf7c-127">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="0cf7c-127">Perform bulk copy operations</span></span>  
  
-   <span data-ttu-id="0cf7c-128">대량 데이터 관리 (**varchar (max)**, **nvarchar (max)** 및 **varbinary (max)** 열) 작업</span><span class="sxs-lookup"><span data-stu-id="0cf7c-128">Manage large data (**varchar(max)**, **nvarchar(max)**, and **varbinary(max)** columns) operations</span></span>  
  
-   <span data-ttu-id="0cf7c-129">데이터베이스 미러링이 구성되어 있는 경우 다시 연결 논리를 사용하여 효과적인 장애 조치(failover) 수행</span><span class="sxs-lookup"><span data-stu-id="0cf7c-129">Use reconnection logic to facilitate failover when database mirroring is configured</span></span>  
  
-   <span data-ttu-id="0cf7c-130">성능 데이터 및 장기 실행 쿼리 기록</span><span class="sxs-lookup"><span data-stu-id="0cf7c-130">Log performance data and long-running queries</span></span>  
  
 <span data-ttu-id="0cf7c-131">ODBC 함수를 호출하려면 C 또는 C++ 애플리케이션에 sql.h, sqlext.h 및 sqltypes.h 헤더 파일이 포함되어야 하며</span><span class="sxs-lookup"><span data-stu-id="0cf7c-131">To make ODBC function calls, a C or C++ application must include the sql.h, sqlext.h, and sqltypes.h header files.</span></span> <span data-ttu-id="0cf7c-132">ODBC 설치 관리자 API 함수를 호출하려면 애플리케이션에 odbcinst.h 헤더 파일이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-132">To make calls to the ODBC installer API functions, an application must include the odbcinst.h header file.</span></span> <span data-ttu-id="0cf7c-133">유니코드 ODBC 애플리케이션에는 sqlucode.h 헤더 파일이 반드시 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-133">A Unicode ODBC application must include the sqlucode.h header file.</span></span> <span data-ttu-id="0cf7c-134">ODBC 애플리케이션은 odbc32.lib 파일에 연결되어야 하고</span><span class="sxs-lookup"><span data-stu-id="0cf7c-134">ODBC applications must be linked with the odbc32.lib file.</span></span> <span data-ttu-id="0cf7c-135">ODBC 설치 관리자 API 함수를 호출하는 ODBC 애플리케이션은 odbccp32.lib 파일에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-135">ODBC applications that call the ODBC installer API functions must be linked with the odbccp32.lib file.</span></span> <span data-ttu-id="0cf7c-136">이러한 파일은 Windows Platform SDK에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-136">These files are included in the Windows Platform SDK.</span></span>  
  
 <span data-ttu-id="0cf7c-137">Native Client ODBC 드라이버를 비롯 한 많은 ODBC 드라이버는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 드라이버별 ODBC 확장을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-137">Many ODBC drivers, including the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, offer driver-specific ODBC extensions.</span></span> <span data-ttu-id="0cf7c-138">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버별 확장을 활용 하려면 응용 프로그램에 sqlncli 헤더 파일이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-138">To take advantage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific extensions, an application should include the sqlncli.h header file.</span></span> <span data-ttu-id="0cf7c-139">이 헤더 파일에는 다음과 같은 항목이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-139">This header file contains:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-140">Native Client ODBC 드라이버별 연결 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-140">Native Client ODBC driver-specific connection attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-141">Native Client ODBC 드라이버별 문 특성</span><span class="sxs-lookup"><span data-stu-id="0cf7c-141">Native Client ODBC driver-specific statement attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-142">Native Client ODBC 드라이버별 열 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-142">Native Client ODBC driver-specific column attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-143">별 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="0cf7c-143">-specific data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-144">별 사용자 정의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="0cf7c-144">-specific user-defined data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-145">Native Client ODBC 드라이버별 [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-145">Native Client ODBC driver-specific [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-146">Native Client ODBC 드라이버 진단 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-146">Native Client ODBC driver diagnostics fields.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0cf7c-147">별 진단 동적 함수 코드</span><span class="sxs-lookup"><span data-stu-id="0cf7c-147">-specific diagnostic dynamic function codes.</span></span>  
  
-   <span data-ttu-id="0cf7c-148">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]별 네이티브 C 데이터 형식용 C/C++ 형식 정의(C 데이터 형식 SQL_C_BINARY에 열이 바인딩된 경우 반환됨)</span><span class="sxs-lookup"><span data-stu-id="0cf7c-148">C/C++ type definitions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific native C data types (returned when columns bound to C data type SQL_C_BINARY).</span></span>  
  
-   <span data-ttu-id="0cf7c-149">SQLPERF 데이터 구조용 형식 정의</span><span class="sxs-lookup"><span data-stu-id="0cf7c-149">Type definition for the SQLPERF data structure.</span></span>  
  
-   <span data-ttu-id="0cf7c-150">ODBC 연결을 통한 대량 복사 API 사용을 지원하기 위한 대량 복사 매크로 및 프로토타입</span><span class="sxs-lookup"><span data-stu-id="0cf7c-150">Bulk copy macros and prototypes to support bulk copy API usage through an ODBC connection.</span></span>  
  
-   <span data-ttu-id="0cf7c-151">연결된 서버와 해당 카탈로그의 목록을 위해 분산 쿼리 메타데이터 API 함수 호출</span><span class="sxs-lookup"><span data-stu-id="0cf7c-151">Call the distributed query metadata API functions for lists of linked servers and their catalogs.</span></span>  
  
 <span data-ttu-id="0cf7c-152">Native Client ODBC 드라이버의 대량 복사 기능을 사용 하는 모든 C 또는 c + + ODBC 응용 프로그램은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sqlncli11 파일에 연결 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-152">Any C or C++ ODBC application that uses the bulk copy feature of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver must be linked with the sqlncli11.lib file.</span></span> <span data-ttu-id="0cf7c-153">또한 분산 쿼리 메타데이터 API 함수를 호출하는 애플리케이션도 sqlncli11.lib 파일에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-153">Applications calling the distributed query metadata API functions must also be linked with sqlncli11.lib.</span></span> <span data-ttu-id="0cf7c-154">Sqlncli 및 sqlncli11 파일은 개발자 도구의 일부로 배포 됩니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf7c-154">The sqlncli.h and sqlncli11.lib files are distributed as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developer's tools.</span></span> <span data-ttu-id="0cf7c-155">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include 및 Lib 디렉터리는 다음과 같이 컴파일러의 INCLUDE 및 LIB 경로에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-155">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include and Lib directories should be in the compiler's INCLUDE and LIB paths as in the following:</span></span>  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 <span data-ttu-id="0cf7c-156">애플리케이션을 빌드할 때는 애플리케이션에서 여러 개의 ODBC 호출을 동시에 유지해야 하는지 여부를 초기 단계에서 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-156">One design decision made early in the process of building an application is whether the application needs to have multiple ODBC calls outstanding at the same time.</span></span> <span data-ttu-id="0cf7c-157">여러 개의 동시 ODBC 호출을 지원하는 방법에는 두 가지가 있으며 이 섹션의 나머지 항목에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-157">There are two methods for supporting multiple concurrent ODBC calls, which are described in the remaining topics in this section.</span></span> <span data-ttu-id="0cf7c-158">자세한 내용은 [ODBC 프로그래머 참조](https://go.microsoft.com/fwlink/?LinkId=45250)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cf7c-158">For more information, see the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cf7c-159">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0cf7c-159">In This Section</span></span>  
  
-   [<span data-ttu-id="0cf7c-160">비동기 모드와 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="0cf7c-160">Asynchronous Mode and SQLCancel</span></span>](../../native-client-odbc-api/sqlcancel.md)  
  
-   [<span data-ttu-id="0cf7c-161">다중 스레드 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="0cf7c-161">Multithreaded Applications</span></span>](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="0cf7c-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cf7c-162">See Also</span></span>  
 [<span data-ttu-id="0cf7c-163">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="0cf7c-163">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
