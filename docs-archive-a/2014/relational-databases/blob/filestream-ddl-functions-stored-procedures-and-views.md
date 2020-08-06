---
title: FILESTREAM DDL, 함수, 저장 프로시저 및 뷰 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dffcc454d21a0a8dea0e98c4db2c19a4af29e948
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638844"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="49679-102">FILESTREAM DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="49679-102">FILESTREAM DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="49679-103">FILESTREAM을 지원하는 Transact-SQL 문 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="49679-103">Lists the Transact-SQL statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that support FILESTREAM.</span></span>  
  
 <span data-ttu-id="49679-104">FileTable 기능을 지원하는 데이터베이스 개체 목록은 [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49679-104">For the list of database objects that support the FileTable feature, see [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="49679-105">Transact-SQL DDL(데이터 정의 언어) 문</span><span class="sxs-lookup"><span data-stu-id="49679-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
-   [<span data-ttu-id="49679-106">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-106">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="49679-107">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-107">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="49679-108">CREATE TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-108">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [<span data-ttu-id="49679-109">ALTER TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-109">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [<span data-ttu-id="49679-110">CREATE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-110">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   <span data-ttu-id="49679-111">[DROP INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="49679-111">[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX</span></span>  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="49679-112">시스템 함수</span><span class="sxs-lookup"><span data-stu-id="49679-112">System Functions</span></span>  
  
-   [<span data-ttu-id="49679-113">GET_FILESTREAM_TRANSACTION_CONTEXT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-113">GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [<span data-ttu-id="49679-114">PathName&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-114">PathName &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> <span data-ttu-id="49679-115">시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="49679-115">System Stored Procedures</span></span>  
  
-   [<span data-ttu-id="49679-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="49679-117">sp_filestream_force_garbage_collection&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-117">sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> <span data-ttu-id="49679-118">시스템 뷰 - 카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="49679-118">System Views - Catalog Views</span></span>  
  
-   [<span data-ttu-id="49679-119">sys.database_filestream_options&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-119">sys.database_filestream_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="49679-120">시스템 뷰 - 동적 관리 뷰</span><span class="sxs-lookup"><span data-stu-id="49679-120">System Views - Dynamic Management Views</span></span>  
  
-   [<span data-ttu-id="49679-121">sys.dm_filestream_file_io_handles&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-121">sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [<span data-ttu-id="49679-122">sys.dm_filestream_file_io_requests&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49679-122">sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="programming-apis"></a><a name="api"></a> <span data-ttu-id="49679-123">프로그래밍 API</span><span class="sxs-lookup"><span data-stu-id="49679-123">Programming APIs</span></span>  
  
-   [<span data-ttu-id="49679-124">OpenSqlFilestream을 사용하여 FILESTREAM 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="49679-124">Access FILESTREAM Data with OpenSqlFilestream</span></span>](access-filestream-data-with-opensqlfilestream.md)  
  
-   [<span data-ttu-id="49679-125">관리되는 API - SqlFileStream 클래스</span><span class="sxs-lookup"><span data-stu-id="49679-125">Managed API - SqlFileStream Class</span></span>](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
