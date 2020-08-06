---
title: 메모리 액세스에 최적화 된 테이블 | Microsoft 문서
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
author: rothja
ms.author: jroth
ms.openlocfilehash: 73430505e55230daf31c492d882eadeb6d35d29f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740999"
---
# <a name="memory-optimized-tables"></a><span data-ttu-id="15a66-102">메모리 액세스에 최적화된 테이블</span><span class="sxs-lookup"><span data-stu-id="15a66-102">Memory-Optimized Tables</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="15a66-103">메모리 내 OLTP는 효율적이고 메모리 최적화 데이터 액세스, 비즈니스 논리의 고유 컴파일, 잠금 및 래치 없는 알고리즘을 통해 OLTP 애플리케이션의 성능을 향상하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-103">In-Memory OLTP helps improve performance of OLTP applications through efficient, memory-optimized data access, native compilation of business logic, and lock- and latch free algorithms.</span></span> <span data-ttu-id="15a66-104">메모리 내 OLTP 기능에는 메모리 최적화 테이블 및 테이블 형식뿐 아니라 이 테이블에 효율적으로 액세스하기 위한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저의 고유 컴파일도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-104">The In-Memory OLTP feature includes memory-optimized tables and table types, as well as native compilation of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures for efficient access to these tables.</span></span>  
  
 <span data-ttu-id="15a66-105">메모리 최적화 테이블에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15a66-105">For more information about memory-optimized tables, see:</span></span>  
  
-   [<span data-ttu-id="15a66-106">메모리 액세스에 최적화된 테이블 소개</span><span class="sxs-lookup"><span data-stu-id="15a66-106">Introduction to Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-107">메모리 최적화 테이블에 대해 자세히 설명하고 데이터 내구성, 메모리 최적화 테이블의 데이터에 대한 액세스, 성능 및 확장성에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-107">Details what memory-optimized tables are and provides information about data durability, accessing data in memory-optimized tables, and performance and scalability.</span></span>  
  
-   [<span data-ttu-id="15a66-108">테이블과 저장 프로시저의 네이티브 컴파일</span><span class="sxs-lookup"><span data-stu-id="15a66-108">Native Compilation of Tables and Stored Procedures</span></span>](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     <span data-ttu-id="15a66-109">메모리 최적화 테이블과 고유하게 컴파일된 저장 프로시저가 DLL에 컴파일되는 방법을 자세히 설명하며 관련 보안 고려 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-109">Details how memory-optimized tables and natively compiled stored procedures are compiled into DLLs, and provides related security considerations.</span></span>  
  
-   [<span data-ttu-id="15a66-110">메모리 액세스에 최적화된 테이블 변경</span><span class="sxs-lookup"><span data-stu-id="15a66-110">Altering Memory-Optimized Tables</span></span>](altering-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-111">메모리 최적화 테이블 업데이트에 대한 지침입니다(테이블 열, 인덱스 및 bucket_count 변경 포함).</span><span class="sxs-lookup"><span data-stu-id="15a66-111">Guidelines for updating memory-optimized tables (including changing table columns, indexes, and bucket_count).</span></span>  
  
-   [<span data-ttu-id="15a66-112">메모리 액세스에 최적화된 테이블의 트랜잭션 이해</span><span class="sxs-lookup"><span data-stu-id="15a66-112">Understanding Transactions on Memory-Optimized Tables</span></span>](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-113">이 섹션에서는 트랜잭션 격리 수준, 크로스 컨테이너 트랜잭션을 비롯하여 메모리 최적화 테이블에서 트랜잭션 수행과 관련된 여러 가지 항목을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-113">This section provides several topics related to performing transactions on memory-optimized tables including transaction isolation levels, and cross-container transactions.</span></span>  
  
-   [<span data-ttu-id="15a66-114">메모리 액세스에 최적화된 테이블 분할을 위한 애플리케이션 패턴</span><span class="sxs-lookup"><span data-stu-id="15a66-114">Application Pattern for Partitioning Memory-Optimized Tables</span></span>](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-115">메모리 최적화 테이블을 사용할 때 분할된 테이블을 에뮬레이트하는 방법을 보여 주는 자세한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-115">Detailed code sample that shows how to emulate partitioned tables when using memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="15a66-116">메모리 액세스에 최적화된 테이블에 대한 통계</span><span class="sxs-lookup"><span data-stu-id="15a66-116">Statistics for Memory-Optimized Tables</span></span>](statistics-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-117">메모리 최적화 테이블에 대해 통계를 컴파일하는 방법과 메모리 최적화 테이블을 유지 관리하고 수동으로 업데이트하는 방법에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-117">Details how statistics are compiled for memory-optimized tables and how to maintain and manually update statistics for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="15a66-118">데이터 정렬 및 코드 페이지</span><span class="sxs-lookup"><span data-stu-id="15a66-118">Collations and Code Pages</span></span>](../../database-engine/collations-and-code-pages.md)  
  
     <span data-ttu-id="15a66-119">메모리 최적화 테이블에 대해 지원되는 데이터 정렬 및 코드 페이지 제한에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-119">Details the restrictions on supported collations and code pages for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="15a66-120">메모리 액세스에 최적화된 테이블의 테이블 및 행 크기</span><span class="sxs-lookup"><span data-stu-id="15a66-120">Table and Row Size in Memory-Optimized Tables</span></span>](table-and-row-size-in-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-121">메모리 최적화 테이블 행의 8060바이트 제한에 대해 자세히 설명하고 테이블 및 행 크기 계산 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-121">Details the 8060 byte limit on memory-optimized table rows, and provides an example for calculating table and row sizes.</span></span>  
  
-   [<span data-ttu-id="15a66-122">메모리 액세스에 최적화된 테이블에 대한 쿼리 처리 가이드</span><span class="sxs-lookup"><span data-stu-id="15a66-122">A Guide to Query Processing for Memory-Optimized Tables</span></span>](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="15a66-123">메모리 최적화 테이블 및 고유하게 컴파일된 저장 프로시저 모두의 쿼리 처리에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-123">Provides an overview of query processing for both memory-optimized tables, and natively compiled stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a66-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15a66-124">See Also</span></span>  
 [<span data-ttu-id="15a66-125">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="15a66-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
