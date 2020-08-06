---
title: 메모리 내 OLTP에 대한 Transact-SQL 지원 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
ms.openlocfilehash: bf3708a258e3bb97231e45b10bea2c59351a06a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740976"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a><span data-ttu-id="7986b-102">메모리 내 OLTP에 대한 Transact-SQL 지원</span><span class="sxs-lookup"><span data-stu-id="7986b-102">Transact-SQL Support for In-Memory OLTP</span></span>
  <span data-ttu-id="7986b-103">Transact-SQL 쿼리 또는 DML 문(SELECT, INSERT, UPDATE 또는 DELETE), 임시 문과, 저장 프로시저, 테이블 반환 함수, 스칼라 함수, 트리거, 뷰와 같은 SQL 모듈을 사용하여 메모리 최적화 테이블에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7986b-103">You can access memory-optimized tables using any Transact-SQL query or DML statement (SELECT, INSERT, UPDATE, or DELETE), ad hoc statement, and SQL module such as stored procedures, table-value functions, scalar functions, triggers, and views.</span></span> <span data-ttu-id="7986b-104">자세한 내용은 해석 된 [transact-sql을 사용 하 여 메모리 액세스에 최적화 된 테이블에 액세스](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7986b-104">For more information see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span>  
  
 <span data-ttu-id="7986b-105">메모리 최적화 테이블만 참조하는 저장 프로시저는 기계어 코드에 고유하게 컴파일될 수 있으며, 일반적으로 해석되는 (디스크 기반) 저장 프로시저에서 상당한 성능 향상을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7986b-105">Stored procedures that only reference memory-optimized tables can be natively compiled into machine code and typically provide significant performance gains over interpreted (disk-based) stored procedures.</span></span> <span data-ttu-id="7986b-106">메모리 최적화 테이블에 최적으로 액세스하려면 고유하게 컴파일된 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7986b-106">For optimized access to memory-optimized tables use natively compiled stored procedures.</span></span> <span data-ttu-id="7986b-107">자세한 내용은 [고유하게 컴파일된 저장 프로시저](natively-compiled-stored-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7986b-107">For more information, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="7986b-108">데이터베이스 개체(DDL 문)를 만들고 수정할 때 다음 문이 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7986b-108">When creating and modifying database objects (DDL statements), the following statements have been modified:</span></span>  
  
-   <span data-ttu-id="7986b-109">[ALTER Database 파일 및 파일 그룹 옵션 transact-sql&#41;&#40;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (참조 `MEMORY_OPTIMIZED_DATA` )</span><span class="sxs-lookup"><span data-stu-id="7986b-109">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="7986b-110">[Transact-sql&#41;SQL SERVER 데이터베이스 &#40;만들기](/sql/t-sql/statements/create-database-sql-server-transact-sql) (참조 `MEMORY_OPTIMIZED_DATA` )</span><span class="sxs-lookup"><span data-stu-id="7986b-110">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="7986b-111">[Transact-sql&#41;&#40;프로시저 만들기](/sql/t-sql/statements/create-procedure-transact-sql) (,, `NATIVE_COMPILATION` 및 참조 `SCHEMABINDING` `EXECUTE AS` `BEGIN ATOMIC` )</span><span class="sxs-lookup"><span data-stu-id="7986b-111">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (see `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, and `BEGIN ATOMIC`)</span></span>  
  
-   <span data-ttu-id="7986b-112">[Transact-sql&#41;&#40;CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) (,,, `MEMORY_OPTIMIZED` `DURABILITY` 및 참조 `BUCKET_COUNT` `INDEX` `HASH` )</span><span class="sxs-lookup"><span data-stu-id="7986b-112">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) (see `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="7986b-113">[Transact-sql&#41;형식 &#40;만듭니다](/sql/t-sql/statements/create-type-transact-sql) (,, `MEMORY_OPTIMIZED` 및 참조 `BUCKET_COUNT` `INDEX` `HASH` ).</span><span class="sxs-lookup"><span data-stu-id="7986b-113">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) (see `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="7986b-114">[ @local_variable Transact-sql&#41;&#40;선언](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (참조 `NULL`  |  `NOT NULL` )</span><span class="sxs-lookup"><span data-stu-id="7986b-114">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (see `NULL` | `NOT NULL`)</span></span>  
  
 <span data-ttu-id="7986b-115">메모리 액세스에 최적화된 테이블은 `PRIMARY KEY` 및 `NOT NULL` 제약 조건을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7986b-115">Memory-optimized tables support `PRIMARY KEY` and `NOT NULL` constraints.</span></span> <span data-ttu-id="7986b-116">지원 되지 않는 제약 조건 구현에 대 한 자세한 내용은 [Check 및 Foreign Key 제약 조건 마이그레이션](../../database-engine/migrating-check-and-foreign-key-constraints.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7986b-116">For information on implementing unsupported constraints, see [Migrating Check and Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="7986b-117">지원되지 않는 기능에 대한 자세한 내용은 [메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문](transact-sql-constructs-not-supported-by-in-memory-oltp.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7986b-117">For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7986b-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7986b-118">In This Section</span></span>  
  
-   [<span data-ttu-id="7986b-119">지원 되는 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="7986b-119">Supported Data Types</span></span>](supported-data-types-for-in-memory-oltp.md)  
  
-   [<span data-ttu-id="7986b-120">해석된 Transact-SQL을 사용하여 메모리 액세스에 최적화된 테이블에 액세스</span><span class="sxs-lookup"><span data-stu-id="7986b-120">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [<span data-ttu-id="7986b-121">메모리 내 OLTP에 대한 시스템 보기, 저장 프로시저, DMV 및 대기 형식</span><span class="sxs-lookup"><span data-stu-id="7986b-121">System Views, Stored Procedures, DMVs and Wait Types for In-Memory OLTP</span></span>](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a><span data-ttu-id="7986b-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7986b-122">See Also</span></span>  
 <span data-ttu-id="7986b-123">[메모리 내 OLTP&#40;메모리 내 최적화&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="7986b-123">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="7986b-124">[고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7986b-124">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="7986b-125">[지원 되는 SQL Server 기능](unsupported-sql-server-features-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="7986b-125">[Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="7986b-126">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="7986b-126">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
