---
title: 날짜 및 시간 기능 향상(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: rothja
ms.author: jroth
ms.openlocfilehash: 16bb9e98691aea829eb71a16ddabddb371d7bcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739861"
---
# <a name="date-and-time-improvements-ole-db"></a><span data-ttu-id="69b6b-102">날짜 및 시간 기능 향상(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="69b6b-102">Date and Time Improvements (OLE DB)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="69b6b-103">에는 새로운 날짜 및 시간 데이터 형식이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-103">introduces new date and time data types.</span></span> <span data-ttu-id="69b6b-104">이 섹션에서는 이러한 새로운 형식이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 확장에서 어떤 방식으로 나타나는지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="69b6b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]새 날짜 및 시간 데이터 형식에 대 한 Native Client 지원의 개요는 [날짜 및 시간 기능 향상](../native-client/features/date-and-time-improvements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69b6b-105">For an overview of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="69b6b-106">샘플은 [향상된 날짜 및 시간 기능 사용&#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b6b-106">For a sample, see [Use Enhanced Date and Time Features &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).</span></span>  
  
 <span data-ttu-id="69b6b-107">날짜 및 시간 데이터 형식에 대한 일반적인 정보는 [datetime&#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69b6b-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69b6b-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="69b6b-108">In This Section</span></span>  
 [<span data-ttu-id="69b6b-109">OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="69b6b-109">Data Type Support for OLE DB Date and Time Improvements</span></span>](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 <span data-ttu-id="69b6b-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]날짜 및 시간 데이터 형식을 지 원하는 OLE DB (Native Client) 형식에 대 한 정보를 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-110">Provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="69b6b-111">메타데이터&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="69b6b-111">Metadata &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/metadata-ole-db.md)  
 <span data-ttu-id="69b6b-112">DBBINDING 구조체,,, 및 I에 대 한 정보를 포함 `ICommandWithParameters::GetParameterInfo` `ICommandWithParameters::SetParameterInfo` `IColumnsRowset::GetColumnsRowset` `ColumnsInfo::GetColumnInfo` 합니다. 또한 OLE DB 스키마 행 집합에 대 한 업데이트 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-112">Contains information about the DBBINDING structure, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset`, and I`ColumnsInfo::GetColumnInfo`. Also provides information about updates to OLE DB schema rowsets.</span></span>  
  
 [<span data-ttu-id="69b6b-113">바인딩 및 변환&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="69b6b-113">Bindings and Conversions &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 <span data-ttu-id="69b6b-114">기존 데이터 형식 및 새로운 데이터 형식에 대한 서버와 클라이언트 간 변환 규칙을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-114">Describes the rules for conversion between server and client for both existing and new date types.</span></span>  
  
 [<span data-ttu-id="69b6b-115">향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 &#40;OLE DB 및 ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="69b6b-115">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="69b6b-116">대량 복사 작업을 지원하는 날짜/시간 기능 향상에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-116">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="69b6b-117">날짜 및 시간 기능 향상을 위한 OLE DB API 지원</span><span class="sxs-lookup"><span data-stu-id="69b6b-117">OLE DB API Support for Date and Time Enhancements</span></span>](ole-db-api-support-for-date-and-time-enhancements.md)  
 <span data-ttu-id="69b6b-118">향상된 날짜/시간 기능을 지원하는 OLE DB API에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-118">Describes the OLE DB APIs that support enhanced date/time features.</span></span>  
  
 [<span data-ttu-id="69b6b-119">IRowsetFind 비교</span><span class="sxs-lookup"><span data-stu-id="69b6b-119">Comparability for IRowsetFind</span></span>](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 <span data-ttu-id="69b6b-120">날짜/시간 형식 및 `IRowsetFind`에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-120">Describes date/time types and `IRowsetFind`.</span></span>  
  
 [<span data-ttu-id="69b6b-121">이전 SQL Server 버전 &#40;OLE DB의 새로운 날짜 및 시간 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="69b6b-121">New Date and Time Features with Previous SQL Server Versions &#40;OLE DB&#41;</span></span>](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 <span data-ttu-id="69b6b-122">향상된 날짜 및 시간 기능을 사용하는 클라이언트 애플리케이션이 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 통신할 때, 그리고 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 사용하여 컴파일한 클라이언트가 향상된 날짜 및 시간 기능을 지원하는 서버에 명령을 전송할 때 예상되는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69b6b-122">Describes the expected behavior when a client application that uses enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b6b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69b6b-123">See Also</span></span>  
 [<span data-ttu-id="69b6b-124">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="69b6b-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
