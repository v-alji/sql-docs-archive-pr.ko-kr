---
title: SQL Server Native Client (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: rothja
ms.author: jroth
ms.openlocfilehash: 16c73966e318ed1e7d326fa77f56195ebbd830df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734027"
---
# <a name="sql-server-native-client-odbc"></a><span data-ttu-id="4ad2c-102">SQL Server Native Client(ODBC)</span><span class="sxs-lookup"><span data-stu-id="4ad2c-102">SQL Server Native Client (ODBC)</span></span>
  <span data-ttu-id="4ad2c-103">ODBC는 관계형 데이터베이스 또는 ISAM(Indexed Sequential Access Method) 데이터베이스의 데이터에 액세스하는 데 사용되는 API(응용 프로그래밍 인터페이스)의 표준 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-103">ODBC is a standard definition of an application programming interface (API) used to access data in relational or indexed sequential access method (ISAM) databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="4ad2c-104">는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]와 통신하는 C 및 C++ 애플리케이션을 작성하기 위한 네이티브 API 중 하나인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버를 통해 ODBC를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-104">supports ODBC, via the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, as one of the native APIs for writing C and C++ applications that communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4ad2c-105">Native Client ODBC 드라이버를 사용하여 작성한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로그램은 C 함수 호출을 통해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-105">programs that are written using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through C function calls.</span></span> <span data-ttu-id="4ad2c-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 관련 버전의 ODBC 함수는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에 구현되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-106">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific versions of the ODBC functions are implemented in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="4ad2c-107">드라이버는 SQL 문을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 전달하고 문의 결과를 애플리케이션에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-107">The driver passes SQL statements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and returns the results of the statements to the application.</span></span>  
  
 <span data-ttu-id="4ad2c-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 Microsoft Win32 ODBC 3.51 사양을 준수하며</span><span class="sxs-lookup"><span data-stu-id="4ad2c-108">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the Microsoft Win32 ODBC 3.51 specification.</span></span> <span data-ttu-id="4ad2c-109">이전 버전의 ODBC로 작성된 애플리케이션을 ODBC 3.51 사양에 정의된 방식에 따라 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad2c-109">The driver supports applications written using earlier versions of ODBC in the manner defined in the ODBC 3.51 specification.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ad2c-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4ad2c-110">In This Section</span></span>  
  
-   [<span data-ttu-id="4ad2c-111">데이터 원본 이름 및 64비트 운영 체제</span><span class="sxs-lookup"><span data-stu-id="4ad2c-111">Data Source Names and 64-Bit Operating Systems</span></span>](data-source-names-and-64-bit-operating-systems.md)  
  
-   [<span data-ttu-id="4ad2c-112">SQL Server Native Client ODBC 드라이버 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="4ad2c-112">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
-   [<span data-ttu-id="4ad2c-113">SQL Server &#40;ODBC&#41;와 통신</span><span class="sxs-lookup"><span data-stu-id="4ad2c-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-114">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="4ad2c-114">Executing Queries &#40;ODBC&#41;</span></span>](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-115">ODBC&#41;&#40;결과 처리</span><span class="sxs-lookup"><span data-stu-id="4ad2c-115">Processing Results &#40;ODBC&#41;</span></span>](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-116">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="4ad2c-116">Using Cursors &#40;ODBC&#41;</span></span>](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-117">ODBC&#41;&#40;트랜잭션 수행</span><span class="sxs-lookup"><span data-stu-id="4ad2c-117">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-118">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="4ad2c-118">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [<span data-ttu-id="4ad2c-119">저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="4ad2c-119">Running Stored Procedures</span></span>](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [<span data-ttu-id="4ad2c-120">카탈로그 함수 사용</span><span class="sxs-lookup"><span data-stu-id="4ad2c-120">Using Catalog Functions</span></span>](using-catalog-functions.md)  
  
-   [<span data-ttu-id="4ad2c-121">ODBC&#41;&#40;대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="4ad2c-121">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-122">text 및 image 열 관리</span><span class="sxs-lookup"><span data-stu-id="4ad2c-122">Managing Text and Image Columns</span></span>](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [<span data-ttu-id="4ad2c-123">ODBC 드라이버 성능 프로파일링</span><span class="sxs-lookup"><span data-stu-id="4ad2c-123">Profiling ODBC Driver Performance</span></span>](profiling-odbc-driver-performance.md)  
  
-   [<span data-ttu-id="4ad2c-124">ODBC&#41;&#40;테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4ad2c-124">Table-Valued Parameters &#40;ODBC&#41;</span></span>](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-125">ODBC&#41;&#40;날짜 및 시간 기능 향상</span><span class="sxs-lookup"><span data-stu-id="4ad2c-125">Date and Time Improvements &#40;ODBC&#41;</span></span>](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-126">ODBC&#41;&#40;많은 CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="4ad2c-126">Large CLR User-Defined Types &#40;ODBC&#41;</span></span>](large-clr-user-defined-types-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-127">ODBC&#41;&#40;FILESTREAM 지원</span><span class="sxs-lookup"><span data-stu-id="4ad2c-127">FILESTREAM Support &#40;ODBC&#41;</span></span>](filestream-support-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-128">클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41;&#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="4ad2c-128">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;</span></span>](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-129">스파스 열 &#40;ODBC&#41;지원</span><span class="sxs-lookup"><span data-stu-id="4ad2c-129">Sparse Columns Support &#40;ODBC&#41;</span></span>](sparse-columns-support-odbc.md)  
  
-   [<span data-ttu-id="4ad2c-130">ODBC&#41; 참조 &#40;SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="4ad2c-130">SQL Server Native Client &#40;ODBC&#41; Reference</span></span>](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [<span data-ttu-id="4ad2c-131">ODBC 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="4ad2c-131">ODBC How-to Topics</span></span>](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ad2c-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ad2c-132">See Also</span></span>  
 <span data-ttu-id="4ad2c-133">[SQL Server Native Client 프로그래밍](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="4ad2c-133">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 [<span data-ttu-id="4ad2c-134">SQL Server Native Client 설치</span><span class="sxs-lookup"><span data-stu-id="4ad2c-134">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
