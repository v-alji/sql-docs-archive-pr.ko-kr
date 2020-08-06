---
title: 고유하게 컴파일된 저장 프로시저 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8fb7a379c0c08ca357baa1042ebcf51c512c9ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738379"
---
# <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="b5fc1-102">Natively Compiled Stored Procedures</span><span class="sxs-lookup"><span data-stu-id="b5fc1-102">Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="b5fc1-103">고유하게 컴파일된 저장 프로시저는 메모리 최적화 테이블에 액세스하는 네이티브 코드로 컴파일된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-103">Natively compiled stored procedures are [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures compiled to native code that access memory-optimized tables.</span></span> <span data-ttu-id="b5fc1-104">고유하게 컴파일된 저장 프로시저는 쿼리 및 비즈니스 논리가 저장 프로시저에서 효율적으로 실행되도록 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-104">Natively compiled stored procedures allow for efficient execution of queries and business logic in the stored procedure.</span></span> <span data-ttu-id="b5fc1-105">네이티브 컴파일 프로세스에 대한 자세한 내용은 [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-105">For more details about the native compilation process, see [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md).</span></span> <span data-ttu-id="b5fc1-106">디스크 기반 저장 프로시저를 고유하게 컴파일된 저장 프로시저로 마이그레이션하는 방법은 [고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-106">For more information about migrating disk-based stored procedures to natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fc1-107">해석된(디스크 기반) 저장 프로시저와 고유하게 컴파일된 저장 프로시저 간의 한 가지 차이점은 해석된 저장 프로시저가 처음 실행할 때 컴파일되는 반면 고유하게 컴파일된 저장 프로시저는 생성할 때 컴파일된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-107">One difference between interpreted (disk-based) stored procedures and natively compiled stored procedures is that an interpreted stored procedure is compiled at first execution whereas a natively compiled stored procedure is compiled when it is created.</span></span> <span data-ttu-id="b5fc1-108">고유하게 컴파일된 저장 프로시저를 사용하면 만들 때 많은 오류 조건(산술 오버플로, 형식 변환, 일부 0으로 나누기 조건)을 검색하여 고유하게 컴파일된 저장 프로시저 만들기가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-108">With natively compiled stored procedures, many error conditions (arithmetic overflow, type conversion, and some divide-by-zero conditions) can be detected at create time and will cause creation of the natively compiled stored procedure to fail.</span></span> <span data-ttu-id="b5fc1-109">해석된 저장된 프로시저를 사용하면 일반적으로 저장 프로시저를 만들 때 이러한 오류 조건으로 인해 오류가 발생하지 않지만 모든 실행이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fc1-109">With interpreted stored procedures, these error conditions will typically not cause a failure when the stored procedure is created, but all executions will fail.</span></span>  
  
 <span data-ttu-id="b5fc1-110">이 섹션의 항목:</span><span class="sxs-lookup"><span data-stu-id="b5fc1-110">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="b5fc1-111">고유하게 컴파일된 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="b5fc1-111">Creating Natively Compiled Stored Procedures</span></span>](creating-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="b5fc1-112">Atomic 블록</span><span class="sxs-lookup"><span data-stu-id="b5fc1-112">Atomic Blocks</span></span>](atomic-blocks-in-native-procedures.md)  
  
-   [<span data-ttu-id="b5fc1-113">고유하게 컴파일된 저장 프로시저에서 지원되는 구문</span><span class="sxs-lookup"><span data-stu-id="b5fc1-113">Supported Constructs in Natively Compiled Stored Procedures</span></span>](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="b5fc1-114">고유하게 컴파일된 저장 프로시저에서 Try..Catch 사용</span><span class="sxs-lookup"><span data-stu-id="b5fc1-114">Using Try..Catch in Natively Compiled Stored Procedures</span></span>](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="b5fc1-115">고유하게 컴파일된 저장 프로시저의 지원되는 구문</span><span class="sxs-lookup"><span data-stu-id="b5fc1-115">Supported Constructs on Natively Compiled Stored Procedures</span></span>](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="b5fc1-116">고유하게 컴파일된 저장 프로시저 및 Execution Set 옵션</span><span class="sxs-lookup"><span data-stu-id="b5fc1-116">Natively Compiled Stored Procedures and Execution Set Options</span></span>](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [<span data-ttu-id="b5fc1-117">고유하게 컴파일된 저장 프로시저를 호출하는 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="b5fc1-117">Best Practices for Calling Natively Compiled Stored Procedures</span></span>](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="b5fc1-118">고유하게 컴파일된 저장 프로시저의 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="b5fc1-118">Monitoring Performance of Natively Compiled Stored Procedures</span></span>](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="b5fc1-119">데이터 액세스 애플리케이션에서 고유하게 컴파일된 저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="b5fc1-119">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5fc1-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5fc1-120">See Also</span></span>  
 [<span data-ttu-id="b5fc1-121">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="b5fc1-121">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
