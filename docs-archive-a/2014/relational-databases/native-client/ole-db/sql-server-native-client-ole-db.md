---
title: SQL Server Native Client (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: rothja
ms.author: jroth
ms.openlocfilehash: 46b948eb1d075edc6000849dcb2d18ea372809d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649509"
---
# <a name="sql-server-native-client-ole-db"></a><span data-ttu-id="877bb-102">SQL Server Native Client(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="877bb-102">SQL Server Native Client (OLE DB)</span></span>
  <span data-ttu-id="877bb-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 데이터 액세스에 사용되는 낮은 수준의 COM API입니다.</span><span class="sxs-lookup"><span data-stu-id="877bb-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a low-level COM API that is used for accessing data.</span></span> <span data-ttu-id="877bb-104">고성능이 필요한 도구, 유틸리티 및 하위 수준 구성 요소 개발에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="877bb-104">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is recommended for developing tools, utilities, or low-level components that need high performance.</span></span> <span data-ttu-id="877bb-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] TDS(Tabular Data Stream) 프로토콜에 직접적으로 액세스하는 고성능 네이티브 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="877bb-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a native, high performance provider that accesses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabular Data Stream (TDS) protocol directly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="877bb-106">Native Client는 애플리케이션에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 수 있는 OLE DB 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="877bb-106">Native Client provides OLE DB support to applications connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="877bb-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 OLE DB 버전 2.0 호환 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="877bb-107">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is an OLE DB version 2.0-compliant provider.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="877bb-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="877bb-108">In This Section</span></span>  
  
-   [<span data-ttu-id="877bb-109">SQL Server Native Client OLE DB 공급자 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="877bb-109">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](../../native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [<span data-ttu-id="877bb-110">데이터 원본 개체 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-110">Data Source Objects &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [<span data-ttu-id="877bb-111">명령</span><span class="sxs-lookup"><span data-stu-id="877bb-111">Commands</span></span>](../../native-client-ole-db-commands/commands.md)  
  
-   [<span data-ttu-id="877bb-112">행 집합</span><span class="sxs-lookup"><span data-stu-id="877bb-112">Rowsets</span></span>](../../native-client-ole-db-rowsets/rowsets.md)  
  
-   [<span data-ttu-id="877bb-113">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="877bb-113">Stored Procedures</span></span>](stored-procedures.md)  
  
-   [<span data-ttu-id="877bb-114">BLOB 및 OLE 개체</span><span class="sxs-lookup"><span data-stu-id="877bb-114">BLOBs and OLE Objects</span></span>](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [<span data-ttu-id="877bb-115">테이블 및 인덱스</span><span class="sxs-lookup"><span data-stu-id="877bb-115">Tables and Indexes</span></span>](../../native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [<span data-ttu-id="877bb-116">데이터 형식&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-116">Data Types &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [<span data-ttu-id="877bb-117">스키마 행 집합 지원&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-117">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
-   [<span data-ttu-id="877bb-118">테이블 반환 매개 변수&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-118">Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [<span data-ttu-id="877bb-119">날짜 및 시간 기능 향상&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-119">Date and Time Improvements &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [<span data-ttu-id="877bb-120">큰 CLR 사용자 정의 형식&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-120">Large CLR User-Defined Types &#40;OLE DB&#41;</span></span>](large-clr-user-defined-types-ole-db.md)  
  
-   [<span data-ttu-id="877bb-121">FILESTREAM Support &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-121">FILESTREAM Support &#40;OLE DB&#41;</span></span>](filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="877bb-122">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="877bb-122">Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
  
-   [<span data-ttu-id="877bb-123">Errors</span><span class="sxs-lookup"><span data-stu-id="877bb-123">Errors</span></span>](../../native-client-ole-db-errors/errors.md)  
  
-   [<span data-ttu-id="877bb-124">클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41;&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-124">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;</span></span>](service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [<span data-ttu-id="877bb-125">스파스 열 지원&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="877bb-125">Sparse Columns Support &#40;OLE DB&#41;</span></span>](sparse-columns-support-ole-db.md)  
  
-   [<span data-ttu-id="877bb-126">SQL Server Native Client &#40;OLE DB&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="877bb-126">SQL Server Native Client &#40;OLE DB&#41; Reference</span></span>](../../native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [<span data-ttu-id="877bb-127">OLE DB 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="877bb-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="877bb-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="877bb-128">See Also</span></span>  
 [<span data-ttu-id="877bb-129">SQL Server Native Client 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="877bb-129">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
