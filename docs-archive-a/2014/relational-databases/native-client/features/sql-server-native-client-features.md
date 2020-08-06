---
title: SQL Server Native Client 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: rothja
ms.author: jroth
ms.openlocfilehash: bb4ba07f84848f754519f8f4fa1c3e56485e85a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648361"
---
# <a name="sql-server-native-client-features"></a><span data-ttu-id="83863-102">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="83863-102">SQL Server Native Client Features</span></span>
  <span data-ttu-id="83863-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client는 WDAC(Windows Data Access Component)(이전의 MDAC(Microsoft Data Access Component))의 기능을 제공할 뿐만 아니라 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능을 제공하는 다른 여러 기능도 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-103">In addition to exposing features of the Windows (formerly Microsoft) Data Access Components (WDAC), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client also implements many other features to expose [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83863-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="83863-104">In This Section</span></span>  
 [<span data-ttu-id="83863-105">문자 변환을 처리 시 ODBC 드라이버 동작 변경</span><span class="sxs-lookup"><span data-stu-id="83863-105">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 <span data-ttu-id="83863-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client부터 변경된 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-106">Discusses a change of behavior beginning in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span></span>  
  
 [<span data-ttu-id="83863-107">데이터베이스 미러링 사용</span><span class="sxs-lookup"><span data-stu-id="83863-107">Using Database Mirroring</span></span>](using-database-mirroring.md)  
 <span data-ttu-id="83863-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client가 미러된 데이터베이스의 사용을 지 원하는 방법에 대해 설명 합니다 .이는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 대기 서버에서 데이터베이스의 복사본 또는 미러를 보관 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="83863-108">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the use of mirrored databases, which is the ability to keep a copy, or mirror, of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database on a standby server.</span></span>  
  
 [<span data-ttu-id="83863-109">비동기 작업 수행</span><span class="sxs-lookup"><span data-stu-id="83863-109">Performing Asynchronous Operations</span></span>](performing-asynchronous-operations.md)  
 <span data-ttu-id="83863-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 비동기 작업을 지원하는 방법을 설명합니다. 비동기 작업은 호출 스레드를 차단하지 않고 즉시 반환할 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="83863-110">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports asynchronous operations, which is the ability to return immediately without blocking on the calling thread.</span></span>  
  
 [<span data-ttu-id="83863-111">MARS&#40;Multiple Active Result Sets&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="83863-111">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](using-multiple-active-result-sets-mars.md)  
 <span data-ttu-id="83863-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 MARS(Multiple Active Result Sets)를 지원하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-112">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports multiple active result sets (MARS).</span></span> <span data-ttu-id="83863-113">MARS를 사용하면 단일 데이터베이스 연결을 통해 여러 결과 집합을 실행 및 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83863-113">MARS enables you to execute and receive multiple result sets using a single database connection</span></span>  
  
 [<span data-ttu-id="83863-114">XML 데이터 형식 사용</span><span class="sxs-lookup"><span data-stu-id="83863-114">Using XML Data Types</span></span>](using-xml-data-types.md)  
 <span data-ttu-id="83863-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 XML 데이터 형식을 지원하는 방법을 설명합니다. XML 데이터 형식은 열 형식, 변수 형식, 매개 변수 형식 또는 함수 반환 형식에 사용할 수 있는 XML 기반 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="83863-115">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the XML data type, which is a XML-based data type that can be used as a column type, variable type, parameter type, or function return type.</span></span>  
  
 [<span data-ttu-id="83863-116">사용자 정의 형식 사용</span><span class="sxs-lookup"><span data-stu-id="83863-116">Using User-Defined Types</span></span>](using-user-defined-types.md)  
 <span data-ttu-id="83863-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client에서 UDT (사용자 정의 형식)를 지 원하는 방법에 대해 설명 합니다. 이러한 UDT는 데이터베이스에 개체 및 사용자 지정 데이터 구조를 저장할 수 있도록 하 여 SQL 형식 시스템을 확장 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="83863-117">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports User-Defined Types (UDT), which extends the SQL type system by allowing you to store objects and custom data structures in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="83863-118">큰 값 형식 사용</span><span class="sxs-lookup"><span data-stu-id="83863-118">Using Large Value Types</span></span>](using-large-value-types.md)  
 <span data-ttu-id="83863-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 큰 값 데이터 형식인 LOB(Large Object) 데이터 형식을 지원하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-119">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports large value data types, which are large object data types (LOB).</span></span>  
  
 [<span data-ttu-id="83863-120">프로그래밍 방식으로 암호 변경</span><span class="sxs-lookup"><span data-stu-id="83863-120">Changing Passwords Programmatically</span></span>](changing-passwords-programmatically.md)  
 <span data-ttu-id="83863-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 만료된 암호를 처리하는 방법을 설명합니다. 이제 관리자의 개입 없이도 클라이언트에서 암호를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83863-121">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the handling of expired passwords so that passwords can now be changed on the client without administrator involvement.</span></span>  
  
 [<span data-ttu-id="83863-122">스냅숏 격리 작업</span><span class="sxs-lookup"><span data-stu-id="83863-122">Working with Snapshot Isolation</span></span>](working-with-snapshot-isolation.md)  
 <span data-ttu-id="83863-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 읽기/쓰기 차단 시나리오를 방지하여 데이터베이스 성능을 개선하는 향상된 행 버전 관리 기능을 지원하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-123">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the enhancement to row versioning that improves database performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 [<span data-ttu-id="83863-124">쿼리 알림 작업</span><span class="sxs-lookup"><span data-stu-id="83863-124">Working with Query Notifications</span></span>](working-with-query-notifications.md)  
 <span data-ttu-id="83863-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 행 집합 수정에 대한 소비자 알림을 지원하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-125">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports consumer notification on rowset modification.</span></span>  
  
 [<span data-ttu-id="83863-126">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="83863-126">Performing Bulk Copy Operations</span></span>](performing-bulk-copy-operations.md)  
 <span data-ttu-id="83863-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client가 테이블 또는 뷰에서 많은 양의 데이터를 전송할 수 있도록 하는 대량 복사 작업을 지 원하는 방법에 대해 설명 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-127">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports bulk copy operations that allow the transfer of large amounts of data into or out of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 [<span data-ttu-id="83863-128">유효성 검사 없이 암호화 사용</span><span class="sxs-lookup"><span data-stu-id="83863-128">Using Encryption Without Validation</span></span>](using-encryption-without-validation.md)  
 <span data-ttu-id="83863-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 사용하여 인증서 유효성을 검사하지 않고 서버에 전송된 데이터를 암호화하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-129">Discusses how to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to encrypt data sent to the server without validating the certificate.</span></span>  
  
 [<span data-ttu-id="83863-130">테이블 반환 매개 변수 SQL Server Native Client &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="83863-130">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](table-valued-parameters-sql-server-native-client.md)  
 <span data-ttu-id="83863-131">테이블 반환 매개 변수에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client의 지원을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-131">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the table-valued parameters.</span></span>  
  
 [<span data-ttu-id="83863-132">큰 CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="83863-132">Large CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="83863-133">큰 CLR(공용 언어 런타임) UDT(사용자 정의 형식)에 대한 지원을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-133">Discusses support for large common language runtime (CLR) user-defined types (UDTs).</span></span>  
  
 [<span data-ttu-id="83863-134">FILESTREAM 지원</span><span class="sxs-lookup"><span data-stu-id="83863-134">FILESTREAM Support</span></span>](filestream-support.md)  
 <span data-ttu-id="83863-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]향상 된 FILESTREAM 기능에 대 한 Native Client 지원을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-135">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the enhanced FILESTREAM feature.</span></span>  
  
 [<span data-ttu-id="83863-136">클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41; 지원</span><span class="sxs-lookup"><span data-stu-id="83863-136">Service Principal Name &#40;SPN&#41; Support in Client Connections</span></span>](service-principal-name-spn-support-in-client-connections.md)  
 <span data-ttu-id="83863-137">모든 프로토콜에서 상호 인증을 지원하기 위해 SPN(서비스 사용자 이름)이 어떻게 확장되었는지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-137">Discusses how support for service principal names (SPNs) has been extended to enable mutual authentication across all protocols.</span></span>  
  
 [<span data-ttu-id="83863-138">SQL Server Native Client의 스파스 열 지원</span><span class="sxs-lookup"><span data-stu-id="83863-138">Sparse Columns Support in SQL Server Native Client</span></span>](sparse-columns-support-in-sql-server-native-client.md)  
 <span data-ttu-id="83863-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 스파스 열을 어떻게 지원하는지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-139">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for sparse columns.</span></span>  
  
 [<span data-ttu-id="83863-140">날짜 및 시간 기능 향상</span><span class="sxs-lookup"><span data-stu-id="83863-140">Date and Time Improvements</span></span>](date-and-time-improvements.md)  
 <span data-ttu-id="83863-141">날짜 및 시간 데이터 형식을 지원하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에 추가된 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-141">Discusses support added to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the date and time data types.</span></span>  
  
 [<span data-ttu-id="83863-142">메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="83863-142">Metadata Discovery</span></span>](metadata-discovery.md)  
 <span data-ttu-id="83863-143">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서의 메타데이터 검색 개선 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-143">Discusses metadata discovery improvements that were made in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="83863-144">SQL Server Native Client 11.0의 UTF-16 지원</span><span class="sxs-lookup"><span data-stu-id="83863-144">UTF-16 Support in SQL Server Native Client 11.0</span></span>](utf-16-support-in-sql-server-native-client-11-0.md)  
 <span data-ttu-id="83863-145">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 도입된 동작 변경 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-145">Discusses a behavior change introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="83863-146">열 결과 또는 출력 매개 변수를 바인딩할 때 고정 길이 버퍼를 제공하는 경우, 종결 문자 이전에 버퍼에 작성된 `wchar` 문자가 서로게이트 쌍의 상위 서로게이트 코드 포인트인 경우 및 다음 `wchar` 문자가 하위 서로게이트 코드 포인트인 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서 상위 서로게이트 코드 포인트를 버퍼에 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83863-146">If you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
 [<span data-ttu-id="83863-147">고가용성 재해 복구를 위한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="83863-147">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="83863-148">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에 추가된 고가용성의 재해 복구 기능을 활용하도록 애플리케이션을 구성할 수 있는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-148">Discusses how your application can be configured to take advantage of the high-availability, disaster recovery features added in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="83863-149">확장 이벤트 로그의 진단 정보 액세스</span><span class="sxs-lookup"><span data-stu-id="83863-149">Accessing Diagnostic Information in the Extended Events Log</span></span>](accessing-diagnostic-information-in-the-extended-events-log.md)  
 <span data-ttu-id="83863-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client의 향상된 기능과, 링 버퍼 및 XEvents 로그의 진단 정보에 액세스하는 데 사용되는 데이터 추적 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-150">Discusses enhancements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data tracing that gives you access to diagnostic information in the ring buffer and XEvents log.</span></span>  
  
 [<span data-ttu-id="83863-151">LocalDB에 대한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="83863-151">SQL Server Native Client Support for LocalDB</span></span>](sql-server-native-client-support-for-localdb.md)  
 <span data-ttu-id="83863-152">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서 지원하는 LocalDB 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="83863-152">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the LocalDB feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83863-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83863-153">See Also</span></span>  
 <span data-ttu-id="83863-154">[SQL Server Native Client 프로그래밍](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="83863-154">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="83863-155">[ODBC 방법 도움말 항목](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="83863-155">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 <span data-ttu-id="83863-156">[OLE DB 방법 도움말 항목](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="83863-156">[OLE DB How-to Topics](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span></span>  
 [<span data-ttu-id="83863-157">SQL Server Native Client 설치</span><span class="sxs-lookup"><span data-stu-id="83863-157">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
