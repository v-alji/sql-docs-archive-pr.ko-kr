---
title: 카탈로그 함수 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cac35e658343f606c1953f265c752335c70d81f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659945"
---
# <a name="using-catalog-functions"></a><span data-ttu-id="db208-102">카탈로그 함수 사용</span><span class="sxs-lookup"><span data-stu-id="db208-102">Using Catalog Functions</span></span>
  <span data-ttu-id="db208-103">모든 데이터베이스에는 데이터베이스에 저장된 데이터를 포함하는 구조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db208-103">All databases have a structure containing the data stored in the database.</span></span> <span data-ttu-id="db208-104">이 구조의 정의는 데이터 사전이라고도 하는 시스템 테이블의 집합으로 구현된 카탈로그에 사용 권한과 같은 다른 정보와 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-104">A definition of this structure, along with other information such as permissions, is stored in a catalog (implemented as a set of system tables), also known as a data dictionary.</span></span>  
  
 <span data-ttu-id="db208-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버를 사용 하면 응용 프로그램에서 odbc 카탈로그 함수를 호출 하 여 데이터베이스 구조를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db208-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to determine the database structure through calls to ODBC catalog functions.</span></span> <span data-ttu-id="db208-106">카탈로그 함수는 결과 집합에 정보를 반환하며 카탈로그의 시스템 테이블을 쿼리하는 카탈로그 저장 프로시저를 사용하여 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-106">Catalog functions return information in result sets and are implemented using catalog stored procedures to query the system tables in the catalog.</span></span> <span data-ttu-id="db208-107">예를 들어 애플리케이션은 시스템의 모든 테이블이나 특정 테이블의 모든 열에 대한 정보를 포함하는 결과 집합을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db208-107">For example, an application might request a result set containing information about all the tables on the system or all the columns in a particular table.</span></span> <span data-ttu-id="db208-108">표준 ODBC 카탈로그 함수는 애플리케이션이 연결된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 카탈로그 정보를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-108">The standard ODBC catalog functions are used to get catalog information from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the application connected.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="db208-109">는 단일 쿼리를 통해 여러 다른 유형의 OLE DB 데이터 원본에 있는 데이터에 액세스하는 분산 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-109">supports distributed queries in which data from multiple, heterogeneous OLE DB data sources is accessed in a single query.</span></span> <span data-ttu-id="db208-110">원격 OLE DB 데이터 원본에 액세스하는 방법 중 하나는 데이터 원본을 연결된 서버로 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db208-110">One of the methods of accessing a remote OLE DB data source is to define the data source as a linked server.</span></span> <span data-ttu-id="db208-111">[Sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)를 사용 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db208-111">This can be done by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="db208-112">연결된 서버를 정의하면 Transact-SQL 문에서 네 부분으로 된 이름을 사용하여 해당 서버의 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db208-112">After the linked server has been defined, objects in that server can be referenced in Transact-SQL statements by using a four-part name:</span></span>  
  
 <span data-ttu-id="db208-113">*linked_server_name. object_name*.</span><span class="sxs-lookup"><span data-stu-id="db208-113">*linked_server_name.catalog.schema.object_name*.</span></span>  
  
 <span data-ttu-id="db208-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 연결된 서버에서 카탈로그 정보를 얻는 데 도움이 되는 두 가지 드라이버별 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports two driver-specific functions that help get catalog information from linked servers:</span></span>  
  
-   <span data-ttu-id="db208-115">**SQLLinkedServers**</span><span class="sxs-lookup"><span data-stu-id="db208-115">**SQLLinkedServers**</span></span>  
  
     <span data-ttu-id="db208-116">로컬 서버에 대해 정의되어 있는 연결된 서버 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-116">Returns a list of the linked servers defined to the local server.</span></span>  
  
-   <span data-ttu-id="db208-117">**SQLLinkedCatalogs**</span><span class="sxs-lookup"><span data-stu-id="db208-117">**SQLLinkedCatalogs**</span></span>  
  
     <span data-ttu-id="db208-118">연결된 서버에 포함되어 있는 카탈로그 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-118">Returns a list of the catalogs contained in a linked server.</span></span>  
  
 <span data-ttu-id="db208-119">연결 된 서버 이름과 카탈로그 이름이 있으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 _linked_server_name_의 두 부분으로 된 이름을 사용 하 여 카탈로그에서 정보 가져오기를 지원 합니다 **.** 다음 ODBC 카탈로그 함수에서 *CatalogName* 에 대 한 _카탈로그_ :</span><span class="sxs-lookup"><span data-stu-id="db208-119">After you have a linked server name and a catalog name, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports getting information from the catalog by using a two-part name of _linked_server_name_**.**_catalog_ for *CatalogName* on the following ODBC catalog functions:</span></span>  
  
-   <span data-ttu-id="db208-120">**SQLColumnPrivileges**</span><span class="sxs-lookup"><span data-stu-id="db208-120">**SQLColumnPrivileges**</span></span>  
  
-   <span data-ttu-id="db208-121">**SQLColumns**</span><span class="sxs-lookup"><span data-stu-id="db208-121">**SQLColumns**</span></span>  
  
-   <span data-ttu-id="db208-122">**SQLPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="db208-122">**SQLPrimaryKeys**</span></span>  
  
-   <span data-ttu-id="db208-123">**SQLStatistics**</span><span class="sxs-lookup"><span data-stu-id="db208-123">**SQLStatistics**</span></span>  
  
-   <span data-ttu-id="db208-124">**SQLTablePrivileges**</span><span class="sxs-lookup"><span data-stu-id="db208-124">**SQLTablePrivileges**</span></span>  
  
-   <span data-ttu-id="db208-125">**SQLTables**</span><span class="sxs-lookup"><span data-stu-id="db208-125">**SQLTables**</span></span>  
  
 <span data-ttu-id="db208-126">두 부분으로 구성 된 _linked_server_name_**입니다.** _카탈로그_ 는 [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md)의 *FKCatalogName* 및 *PKCatalogName* 에 대해서도 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-126">The two-part _linked_server_name_**.**_catalog_ is also supported for *FKCatalogName* and *PKCatalogName* on [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md).</span></span>  
  
 <span data-ttu-id="db208-127">SQLLinkedServers 및 SQLLinkedCatalogs를 사용하려면 다음 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-127">Using SQLLinkedServers and SQLLinkedCatalogs requires the following files:</span></span>  
  
-   <span data-ttu-id="db208-128">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="db208-128">sqlncli.h</span></span>  
  
     <span data-ttu-id="db208-129">연결된 서버 카탈로그 함수를 위한 함수 프로토타입 및 상수 정의를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-129">Includes function prototypes and constant definitions for the linked server catalog functions.</span></span> <span data-ttu-id="db208-130">sqlncli.h는 ODBC 애플리케이션에 포함되어야 하며 애플리케이션을 컴파일할 때 포함 경로에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-130">sqlncli.h must be included in the ODBC application and must be in the include path when the application is compiled.</span></span>  
  
-   <span data-ttu-id="db208-131">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="db208-131">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="db208-132">링커의 라이브러리 경로에 있어야 하며 링크할 파일로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-132">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="db208-133">sqlncli11.lib는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-133">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="db208-134">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="db208-134">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="db208-135">실행 단계에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db208-135">Must be present at execution time.</span></span> <span data-ttu-id="db208-136">sqlncli11.dll은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="db208-136">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db208-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db208-137">See Also</span></span>  
 <span data-ttu-id="db208-138">[ODBC&#41;SQL Server Native Client &#40;](sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="db208-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="db208-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="db208-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span></span>  
 <span data-ttu-id="db208-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span><span class="sxs-lookup"><span data-stu-id="db208-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span></span>  
 <span data-ttu-id="db208-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span><span class="sxs-lookup"><span data-stu-id="db208-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span></span>  
 <span data-ttu-id="db208-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="db208-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span></span>  
 <span data-ttu-id="db208-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span><span class="sxs-lookup"><span data-stu-id="db208-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span></span>  
 [<span data-ttu-id="db208-144">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="db208-144">SQLStatistics</span></span>](../../statistics/statistics.md)  
  
  
