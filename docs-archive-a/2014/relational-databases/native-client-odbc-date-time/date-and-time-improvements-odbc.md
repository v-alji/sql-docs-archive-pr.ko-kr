---
title: 날짜 및 시간 기능 향상 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ce8f906fc1949a80bfa8e5a541ecf1e83878775
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650936"
---
# <a name="date-and-time-improvements-odbc"></a><span data-ttu-id="e8c29-102">날짜 및 시간 기능 향상(ODBC)</span><span class="sxs-lookup"><span data-stu-id="e8c29-102">Date and Time Improvements (ODBC)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="e8c29-103">에는 새로운 날짜 및 시간 데이터 형식이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-103">introduced new date and time data types.</span></span> <span data-ttu-id="e8c29-104">이 섹션에서는 이러한 새로운 형식이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 확장에서 어떤 방식으로 나타나는지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="e8c29-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]새 날짜 및 시간 데이터 형식에 대 한 Native Client 지원에 대 한 개요는 [날짜 및 시간 기능 향상](../native-client/features/date-and-time-improvements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c29-105">For an overview of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="e8c29-106">ODBC 날짜/시간 지원을 보여 주는 예제는 [날짜 및 시간 형식 사용](../native-client-odbc-how-to/use-date-and-time-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c29-106">For a sample demonstrating ODBC date/time support, see [Use Date and Time Types](../native-client-odbc-how-to/use-date-and-time-types.md).</span></span>  
  
 <span data-ttu-id="e8c29-107">날짜 및 시간 데이터 형식에 대한 일반적인 정보는 [datetime&#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c29-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8c29-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e8c29-108">In This Section</span></span>  
 [<span data-ttu-id="e8c29-109">ODBC 날짜 및 시간 기능 향상을 위한 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="e8c29-109">Data Type Support for ODBC Date and Time Improvements</span></span>](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 <span data-ttu-id="e8c29-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 날짜 및 시간 데이터 형식을 지원하는 ODBC 형식에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-110">Provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="e8c29-111">ODBC&#41;&#40;메타 데이터</span><span class="sxs-lookup"><span data-stu-id="e8c29-111">Metadata &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/metadata-odbc.md)  
 <span data-ttu-id="e8c29-112">IPD(구현 매개 변수 설명자)와 IRD(구현 행 설명자) 필드에서 반환되는 정보와 `SQLColumns` 및 `SQLProcedureColumns`에서 반환되는 열 메타데이터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-112">Describes information returned in the implementation parameter descriptor (IPD) and implementation row descriptor (IRD) fields, as well as column metadata returned by `SQLColumns` and `SQLProcedureColumns`.</span></span> <span data-ttu-id="e8c29-113">또한 `SQLGetTypeInfo`에서 반환되는 데이터 형식 메타데이터에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-113">Also describes data type metadata returned by `SQLGetTypeInfo`.</span></span>  
  
 [<span data-ttu-id="e8c29-114">ODBC&#41;&#40;datetime 데이터 형식 변환</span><span class="sxs-lookup"><span data-stu-id="e8c29-114">datetime Data Type Conversions &#40;ODBC&#41;</span></span>](datetime-data-type-conversions-odbc.md)  
 <span data-ttu-id="e8c29-115">datetime 값과 datetimeoffset 값을 서로 변환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-115">Describes how to convert between datetime and datetimeoffset values.</span></span>  
  
 [<span data-ttu-id="e8c29-116">날짜 및 시간 형식에 대한 sql_variant 지원</span><span class="sxs-lookup"><span data-stu-id="e8c29-116">sql_variant Support for Date and Time Types</span></span>](sql-variant-support-for-date-and-time-types.md)  
 <span data-ttu-id="e8c29-117">향상된 날짜 및 시간 기능을 지원하는 SQL_VARIANT 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-117">Describes SQL_VARIANT function support for enhanced date and time functionality.</span></span>  
  
 [<span data-ttu-id="e8c29-118">향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 &#40;OLE DB 및 ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e8c29-118">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="e8c29-119">대량 복사 작업을 지원하는 날짜/시간 기능 향상에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-119">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="e8c29-120">이전 SQL Server 버전의 향상 된 날짜 및 시간 형식 동작 (ODBC&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="e8c29-120">Enhanced Date and Time Type Behavior with Previous SQL Server Versions &#40;ODBC&#41;</span></span>](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 <span data-ttu-id="e8c29-121">향상된 날짜 및 시간 기능을 사용하는 클라이언트 애플리케이션이 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 통신할 때, 그리고 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서 컴파일된 클라이언트가 향상된 날짜 및 시간 기능을 지원하는 서버에 명령을 전송할 때 예상되는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-121">Describes the expected behavior when a client application using enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
 [<span data-ttu-id="e8c29-122">향상된 날짜 및 시간 기능에 대한 ODBC API 지원</span><span class="sxs-lookup"><span data-stu-id="e8c29-122">ODBC API Support for Enhanced Date and Time Features</span></span>](odbc-api-support-for-enhanced-date-and-time-features.md)  
 <span data-ttu-id="e8c29-123">향상된 날짜 및 시간 기능을 지원하는 ODBC 함수를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c29-123">Lists the ODBC functions that support enhanced date and time functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c29-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8c29-124">See Also</span></span>  
 [<span data-ttu-id="e8c29-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e8c29-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
