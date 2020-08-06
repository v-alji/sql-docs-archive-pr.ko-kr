---
title: 날짜 및 시간 기능 향상을 위한 OLE DB API 지원 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: rothja
ms.author: jroth
ms.openlocfilehash: cdb17f0d2104373ea797ff9403cc417dfaa3d868
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653847"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a><span data-ttu-id="8c031-102">날짜 및 시간 기능 향상을 위한 OLE DB API 지원</span><span class="sxs-lookup"><span data-stu-id="8c031-102">OLE DB API Support for Date and Time Enhancements</span></span>
  <span data-ttu-id="8c031-103">다음 OLE DB API는 향상된 날짜/시간 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8c031-103">The following OLE DB APIs support enhanced date/time features.</span></span>  
  
|<span data-ttu-id="8c031-104">기능</span><span class="sxs-lookup"><span data-stu-id="8c031-104">Function</span></span>|<span data-ttu-id="8c031-105">Description</span><span class="sxs-lookup"><span data-stu-id="8c031-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8c031-106">IAccessor::CreateAccessor</span><span class="sxs-lookup"><span data-stu-id="8c031-106">IAccessor::CreateAccessor</span></span>|<span data-ttu-id="8c031-107">애플리케이션에서 `datetime`, `datetime2` 및 `smalldatetime` 값을 구분할 수 있도록 DBBINDING 구조체에 플래그가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c031-107">A flag is added in the DBBINDING structure to enable applications to discriminate between `datetime`, `datetime2`, and `smalldatetime` values.</span></span> <span data-ttu-id="8c031-108">자세한 내용은 [매개 변수 및 행 집합 메타데이터](metadata-parameter-and-rowset.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-108">For more information, see [Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="8c031-109">IBCPSession::BCPColFmt</span><span class="sxs-lookup"><span data-stu-id="8c031-109">IBCPSession::BCPColFmt</span></span>|<span data-ttu-id="8c031-110">자세한 내용은 [향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 &#40;OLE DB 및 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-110">For more information, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>|  
|<span data-ttu-id="8c031-111">ICommandWithParameters::GetParameterInfo</span><span class="sxs-lookup"><span data-stu-id="8c031-111">ICommandWithParameters::GetParameterInfo</span></span>|<span data-ttu-id="8c031-112">자세한 내용은 [매개 변수 및 행 집합 메타데이터](metadata-parameter-and-rowset.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-112">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="8c031-113">ICommandWithParameters::SetParameterinfo</span><span class="sxs-lookup"><span data-stu-id="8c031-113">ICommandWithParameters::SetParameterinfo</span></span>|<span data-ttu-id="8c031-114">자세한 내용은 [매개 변수 및 행 집합 메타데이터](metadata-parameter-and-rowset.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-114">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="8c031-115">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="8c031-115">IColumnsRowset::GetColumnsRowset</span></span>|<span data-ttu-id="8c031-116">자세한 내용은 [매개 변수 및 행 집합 메타데이터](metadata-parameter-and-rowset.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-116">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="8c031-117">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="8c031-117">IColumnsInfo::GetColumnInfo</span></span>|<span data-ttu-id="8c031-118">자세한 내용은 [매개 변수 및 행 집합 메타데이터](metadata-parameter-and-rowset.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-118">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="8c031-119">IDBSchemaRowset::GetRowset</span><span class="sxs-lookup"><span data-stu-id="8c031-119">IDBSchemaRowset::GetRowset</span></span>|<span data-ttu-id="8c031-120">영향을 받는 스키마 행 집합에 대한 자세한 내용은 [날짜 및 시간과 스키마 행 집합](../native-client-ole-db-rowsets/rowsets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-120">For details of the affected schema rowsets, see[Date and Time and Schema Rowsets](../native-client-ole-db-rowsets/rowsets.md).</span></span>|  
|<span data-ttu-id="8c031-121">IRowsetFastLoad</span><span class="sxs-lookup"><span data-stu-id="8c031-121">IRowsetFastLoad</span></span>|<span data-ttu-id="8c031-122">이 인터페이스는 새 날짜/시간 형식을 지원하지만 인터페이스 변경 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c031-122">This interface supports the new date/time types, but there is no change to its interface.</span></span>|  
|<span data-ttu-id="8c031-123">ITableDefinition::CreateTable</span><span class="sxs-lookup"><span data-stu-id="8c031-123">ITableDefinition::CreateTable</span></span>|<span data-ttu-id="8c031-124">자세한 내용은 [OLE DB 날짜 및 시간 기능 향상을 위한 데이터 형식 지원](data-type-support-for-ole-db-date-and-time-improvements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c031-124">For more information, see [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c031-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c031-125">See Also</span></span>  
 [<span data-ttu-id="8c031-126">날짜 및 시간 기능 향상&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8c031-126">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
