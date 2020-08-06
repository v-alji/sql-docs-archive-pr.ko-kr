---
title: 스키마 행 집합에서 분산 쿼리 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: rothja
ms.author: jroth
ms.openlocfilehash: 48b57bbf40590f8ad5c049268f25fe66d2f94357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647649"
---
# <a name="distributed-query-support-in-schema-rowsets"></a><span data-ttu-id="c7aa3-102">스키마 행 집합에서 분산 쿼리 지원</span><span class="sxs-lookup"><span data-stu-id="c7aa3-102">Distributed Query Support in Schema Rowsets</span></span>
  <span data-ttu-id="c7aa3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]분산 쿼리를 지원 하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset** 인터페이스는 연결 된 서버에 대 한 메타 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-103">To support [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset** interface returns metadata on linked servers.</span></span>  
  
 <span data-ttu-id="c7aa3-104">DBPROPSET_SQLSERVERSESSION 속성 SSPROP_QUOTEDCATALOGNAMES가 VARIANT_TRUE이면 카탈로그 이름에 따옴표 붙은 식별자(예: "my.catalog")를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-104">If the DBPROPSET_SQLSERVERSESSION property SSPROP_QUOTEDCATALOGNAMES is VARIANT_TRUE, a quoted identifier can be specified for the catalog name (for example "my.catalog").</span></span> <span data-ttu-id="c7aa3-105">Catalog에서 스키마 행 집합 출력을 제한할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 연결 된 서버 및 카탈로그 이름을 포함 하는 두 부분으로 구성 된 이름을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-105">When restricting schema rowset output by catalog, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes a two-part name containing the linked server and catalog name.</span></span> <span data-ttu-id="c7aa3-106">아래 표의 스키마 행 집합에 대해 두 부분으로 구성 된 카탈로그 이름을 _linked_server_로 지정 합니다 **.** _catalog_ 는 지정 된 연결 된 서버의 해당 카탈로그로 출력을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-106">For the schema rowsets in the table below, specifying a two-part catalog name as _linked_server_**.**_catalog_ restricts output to the applicable catalog of the named linked server.</span></span>  
  
|<span data-ttu-id="c7aa3-107">스키마 행 집합</span><span class="sxs-lookup"><span data-stu-id="c7aa3-107">Schema rowset</span></span>|<span data-ttu-id="c7aa3-108">카탈로그 제한</span><span class="sxs-lookup"><span data-stu-id="c7aa3-108">Catalog restriction</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="c7aa3-109">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="c7aa3-109">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="c7aa3-110">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="c7aa3-110">CATALOG_NAME</span></span>|  
|<span data-ttu-id="c7aa3-111">DBSCHEMA_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="c7aa3-111">DBSCHEMA_COLUMNS</span></span>|<span data-ttu-id="c7aa3-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-112">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-113">DBSCHEMA_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="c7aa3-113">DBSCHEMA_PRIMARY_KEYS</span></span>|<span data-ttu-id="c7aa3-114">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-114">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-115">DBSCHEMA_TABLES</span><span class="sxs-lookup"><span data-stu-id="c7aa3-115">DBSCHEMA_TABLES</span></span>|<span data-ttu-id="c7aa3-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-116">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-117">DBSCHEMA_FOREIGN_KEYS</span><span class="sxs-lookup"><span data-stu-id="c7aa3-117">DBSCHEMA_FOREIGN_KEYS</span></span>|<span data-ttu-id="c7aa3-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-119">DBSCHEMA_INDEXES</span><span class="sxs-lookup"><span data-stu-id="c7aa3-119">DBSCHEMA_INDEXES</span></span>|<span data-ttu-id="c7aa3-120">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-120">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-121">DBSCHEMA_COLUMN_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="c7aa3-121">DBSCHEMA_COLUMN_PRIVILEGES</span></span>|<span data-ttu-id="c7aa3-122">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-122">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="c7aa3-123">DBSCHEMA_TABLE_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="c7aa3-123">DBSCHEMA_TABLE_PRIVILEGES</span></span>|<span data-ttu-id="c7aa3-124">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c7aa3-124">TABLE_CATALOG</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c7aa3-125">스키마 행 집합을 연결된 서버의 모든 카탈로그로 제한하려면 구문 *linked_server*(여기서 마침표 구분 기호가 이름 사양에 포함됨)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-125">To restrict a schema rowset to all catalogs from a linked server, use the syntax *linked_server* (where the period separator is part of the name specification).</span></span> <span data-ttu-id="c7aa3-126">이 구문은 카탈로그 이름 제한에 NULL을 지정하는 것과 같으며 연결된 서버가 카탈로그를 지원하지 않는 데이터 원본을 나타내는 경우에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-126">This syntax is equivalent to specifying NULL for the catalog name restriction and is also used when the linked server indicates a data source that does not support catalogs.</span></span>  
  
 <span data-ttu-id="c7aa3-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 연결 된 서버로 등록 된 OLE DB 데이터 원본 목록을 반환 하는 스키마 행 집합 LINKEDSERVERS를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7aa3-127">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the schema rowset LINKEDSERVERS, returning a list of OLE DB data sources registered as linked servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7aa3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7aa3-128">See Also</span></span>  
 <span data-ttu-id="c7aa3-129">[스키마 행 집합 지원 &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="c7aa3-129">[Schema Rowset Support &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span></span>  
 [<span data-ttu-id="c7aa3-130">LINKEDSERVERS 행 집합&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c7aa3-130">LINKEDSERVERS Rowset &#40;OLE DB&#41;</span></span>](schema-rowsets-linkedservers-rowset.md)  
  
  
