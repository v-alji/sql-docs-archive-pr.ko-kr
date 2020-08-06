---
title: 메모리 내 OLTP로 마이그레이션 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 405cdac5-a0d4-47a4-9180-82876b773b82
author: rothja
ms.author: jroth
ms.openlocfilehash: ed764ce52d41d76667213b846cec51b26f634a27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742092"
---
# <a name="migrating-to-in-memory-oltp"></a><span data-ttu-id="f5570-102">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f5570-102">Migrating to In-Memory OLTP</span></span>
  <span data-ttu-id="f5570-103">이 섹션에서는 데이터베이스 개체를 마이그레이션하여 메모리 내 OLTP를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f5570-103">This section discusses how to migrate database objects to use In-Memory OLTP.</span></span>  
  
-   [<span data-ttu-id="f5570-104">메모리 내 OLTP에 테이블 또는 저장 프로시저를 이식해야 하는지 확인</span><span class="sxs-lookup"><span data-stu-id="f5570-104">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  
-   [<span data-ttu-id="f5570-105">메모리 최적화 관리자</span><span class="sxs-lookup"><span data-stu-id="f5570-105">Memory Optimization Advisor</span></span>](memory-optimization-advisor.md)  
  
-   [<span data-ttu-id="f5570-106">네이티브 컴파일 관리자</span><span class="sxs-lookup"><span data-stu-id="f5570-106">Native Compilation Advisor</span></span>](native-compilation-advisor.md)  
  
-   [<span data-ttu-id="f5570-107">메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="f5570-107">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
-   [<span data-ttu-id="f5570-108">메모리 액세스에 최적화된 테이블에서 LOB 열 구현</span><span class="sxs-lookup"><span data-stu-id="f5570-108">Implementing LOB Columns in a Memory-Optimized Table</span></span>](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="f5570-109">메모리 액세스에 최적화된 테이블에서 SQL_VARIANT 구현</span><span class="sxs-lookup"><span data-stu-id="f5570-109">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="f5570-110">고유하게 컴파일된 저장 프로시저의 마이그레이션 문제</span><span class="sxs-lookup"><span data-stu-id="f5570-110">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="f5570-111">계산 열 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f5570-111">Migrating Computed Columns</span></span>](migrating-computed-columns.md)  
  
-   [<span data-ttu-id="f5570-112">트리거 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f5570-112">Migrating Triggers</span></span>](migrating-triggers.md)  
  
-   [<span data-ttu-id="f5570-113">데이터베이스 간 쿼리</span><span class="sxs-lookup"><span data-stu-id="f5570-113">Cross-Database Queries</span></span>](cross-database-queries.md)  
  
-   [<span data-ttu-id="f5570-114">CHECK 및 FOREIGN KEY 제약 조건 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="f5570-114">Migrating Check and Foreign Key Constraints</span></span>](../../database-engine/migrating-check-and-foreign-key-constraints.md)  
  
-   [<span data-ttu-id="f5570-115">메모리 액세스에 최적화된 테이블에서 IDENTITY 구현</span><span class="sxs-lookup"><span data-stu-id="f5570-115">Implementing IDENTITY in a Memory-Optimized Table</span></span>](implementing-identity-in-a-memory-optimized-table.md)  
  
 <span data-ttu-id="f5570-116">마이그레이션 방법에 대한 자세한 내용은 [메모리 내 OLTP – 일반적인 작업 패턴 및 마이그레이션 고려 사항](https://msdn.microsoft.com/library/dn673538.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5570-116">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5570-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5570-117">See Also</span></span>  
 <span data-ttu-id="f5570-118">[메모리 내 OLTP&#40;메모리 내 최적화&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="f5570-118">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 [<span data-ttu-id="f5570-119">메모리 액세스에 최적화된 테이블에 필요한 메모리 예측</span><span class="sxs-lookup"><span data-stu-id="f5570-119">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
