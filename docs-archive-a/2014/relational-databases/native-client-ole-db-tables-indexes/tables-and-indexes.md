---
title: 테이블 및 인덱스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: rothja
ms.author: jroth
ms.openlocfilehash: abc7c314e433eb9f107bd191738d951706f1b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652077"
---
# <a name="tables-and-indexes"></a><span data-ttu-id="20234-102">테이블 및 인덱스</span><span class="sxs-lookup"><span data-stu-id="20234-102">Tables and Indexes</span></span>
  <span data-ttu-id="20234-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 소비자가 테이블과 인덱스를 생성, 변경 및 삭제할 수 있도록 **Iindexdefinition** 및 **itabledefinition** 인터페이스를 제공 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="20234-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition** and **ITableDefinition** interfaces, allowing consumers to create, alter, and drop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and indexes.</span></span> <span data-ttu-id="20234-104">올바른 테이블 및 인덱스 정의는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="20234-104">Valid table and index definitions depend on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="20234-105">테이블과 인덱스를 만들거나 삭제하는 기능은 소비자 애플리케이션 사용자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 액세스 권한에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="20234-105">The ability to create or drop tables and indexes depends on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access rights of the consumer-application user.</span></span> <span data-ttu-id="20234-106">테이블 삭제는 선언적 참조 무결성 제약 조건이나 다른 요인이 있는지 여부에 따라 더욱 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20234-106">Dropping a table can be further constrained by the presence of declarative referential integrity constraints or other factors.</span></span>  
  
 <span data-ttu-id="20234-107">을 대상으로 하는 대부분의 응용 프로그램은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이러한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 인터페이스 대신 sql-dmo를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="20234-107">Most applications targeting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use SQL-DMO instead of these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interfaces.</span></span> <span data-ttu-id="20234-108">SQL-DMO는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 모든 관리 기능을 지원하는 OLE Automation 개체 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="20234-108">SQL-DMO is a collection of OLE Automation objects that support all the administrative functions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="20234-109">여러 OLE DB 공급자를 대상으로 하는 애플리케이션은 다양한 OLE DB 공급자가 지원하는 일반 OLE DB 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20234-109">Applications targeting multiple OLE DB providers use these generic OLE DB interfaces that are supported by the various OLE DB providers.</span></span>  
  
 <span data-ttu-id="20234-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 공급자별 속성 집합 DBPROPSET_SQLSERVERCOLUMN에 다음과 같은 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="20234-110">In the provider-specific property set DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defines the following property.</span></span>  
  
|<span data-ttu-id="20234-111">속성 ID</span><span class="sxs-lookup"><span data-stu-id="20234-111">Property ID</span></span>|<span data-ttu-id="20234-112">Description</span><span class="sxs-lookup"><span data-stu-id="20234-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="20234-113">SSPROP_COL_COLLATIONNAME</span><span class="sxs-lookup"><span data-stu-id="20234-113">SSPROP_COL_COLLATIONNAME</span></span>|<span data-ttu-id="20234-114">유형: VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="20234-114">Type: VT_BSTR</span></span><br /><br /> <span data-ttu-id="20234-115">R/W: 쓰기</span><span class="sxs-lookup"><span data-stu-id="20234-115">R/W: Write</span></span><br /><br /> <span data-ttu-id="20234-116">기본값: Null</span><span class="sxs-lookup"><span data-stu-id="20234-116">Default: Null</span></span><br /><br /> <span data-ttu-id="20234-117">설명: 이 속성은 **ITableDefinition**에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20234-117">Description: This property is used only in **ITableDefinition**.</span></span> <span data-ttu-id="20234-118">이 속성에 지정된 문자열은 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)을 생성할 때 사용됨</span><span class="sxs-lookup"><span data-stu-id="20234-118">The string specified in this property is used when creating a [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)</span></span><br /><br /> <span data-ttu-id="20234-119">문을 만들 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20234-119">statement.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="20234-120">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="20234-120">In This Section</span></span>  
  
-   [<span data-ttu-id="20234-121">SQL Server 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="20234-121">Creating SQL Server Tables</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [<span data-ttu-id="20234-122">SQL Server 테이블에 열 추가</span><span class="sxs-lookup"><span data-stu-id="20234-122">Adding a Column to a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [<span data-ttu-id="20234-123">SQL Server 테이블에서 열 제거</span><span class="sxs-lookup"><span data-stu-id="20234-123">Removing a Column from a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [<span data-ttu-id="20234-124">SQL Server 테이블 삭제</span><span class="sxs-lookup"><span data-stu-id="20234-124">Dropping a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [<span data-ttu-id="20234-125">SQL Server 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="20234-125">Creating SQL Server Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
-   [<span data-ttu-id="20234-126">SQL Server 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="20234-126">Dropping a SQL Server Index</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a><span data-ttu-id="20234-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20234-127">See Also</span></span>  
 <span data-ttu-id="20234-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="20234-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 <span data-ttu-id="20234-129">[DROP TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20234-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 <span data-ttu-id="20234-130">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20234-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="20234-131">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="20234-131">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
