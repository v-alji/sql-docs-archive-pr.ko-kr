---
title: 고유하게 컴파일된 저장 프로시저를 호출하는 최선의 구현 방법 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d07d0e290d1fbd9b324235e64734a399bf7801d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647000"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a><span data-ttu-id="a9b43-102">고유하게 컴파일된 저장 프로시저를 호출하는 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="a9b43-102">Best Practices for Calling Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="a9b43-103">고유하게 컴파일된 저장 프로시저의 특징</span><span class="sxs-lookup"><span data-stu-id="a9b43-103">Natively compiled stored procedures are:</span></span>  
  
-   <span data-ttu-id="a9b43-104">애플리케이션에서 성능이 중요한 부분에 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-104">Used typically in performance-critical parts of an application.</span></span>  
  
-   <span data-ttu-id="a9b43-105">자주 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-105">Frequently executed.</span></span>  
  
-   <span data-ttu-id="a9b43-106">매우 빠를 것으로 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-106">Expected to be very fast.</span></span>  
  
 <span data-ttu-id="a9b43-107">고유하게 컴파일된 저장 프로시저를 사용하는 경우의 성능 이점은 행 수와 프로시저에서 처리하는 논리의 양이 많을수록 커집니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-107">The performance benefit of using a natively compiled stored procedure increases with the number of rows and the amount of logic that is processed by the procedure.</span></span> <span data-ttu-id="a9b43-108">예를 들어 고유하게 컴파일된 저장 프로시저는 다음 중 하나 이상을 사용하는 경우 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-108">For example, a natively compiled stored procedure will exhibit better performance if it uses one or more of the following:</span></span>  
  
-   <span data-ttu-id="a9b43-109">집계.</span><span class="sxs-lookup"><span data-stu-id="a9b43-109">Aggregation.</span></span>  
  
-   <span data-ttu-id="a9b43-110">중첩 루프 조인</span><span class="sxs-lookup"><span data-stu-id="a9b43-110">Nested-loops joins.</span></span>  
  
-   <span data-ttu-id="a9b43-111">다중 문 선택, 삽입, 업데이트 및 삭제 작업</span><span class="sxs-lookup"><span data-stu-id="a9b43-111">Multi-statement select, insert, update, and delete operations.</span></span>  
  
-   <span data-ttu-id="a9b43-112">복잡한 식</span><span class="sxs-lookup"><span data-stu-id="a9b43-112">Complex expressions.</span></span>  
  
-   <span data-ttu-id="a9b43-113">조건문, 루프 등의 절차적 논리</span><span class="sxs-lookup"><span data-stu-id="a9b43-113">Procedural logic, such as conditional statements and loops.</span></span>  
  
 <span data-ttu-id="a9b43-114">단일 행만 처리해야 하는 경우 고유하게 컴파일된 저장 프로시저를 사용하면 성능 이점이 제공되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-114">If you need to process only a single row, using a natively compiled stored procedure may not provide a performance benefit.</span></span>  
  
 <span data-ttu-id="a9b43-115">서버에서 매개 변수 이름을 매핑하고 형식을 변환하지 않아도 되도록 하려면 다음과 같이 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a9b43-115">To avoid the server having to map parameter names and convert types:</span></span>  
  
-   <span data-ttu-id="a9b43-116">프로시저에 전달된 매개 변수의 형식을 프로시저 정의에 있는 형식과 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-116">Match the types of the parameters passed to the procedure with the types in the procedure definition.</span></span>  
  
-   <span data-ttu-id="a9b43-117">고유하게 컴파일된 저장 프로시저를 호출하는 경우 이름이 없는 서수 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-117">Use ordinal (nameless) parameters when calling natively compiled stored procedures.</span></span> <span data-ttu-id="a9b43-118">가장 효율적으로 실행하려면 명명된 매개 변수를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="a9b43-118">For the most efficient execution, do not use named parameters.</span></span>  
  
 <span data-ttu-id="a9b43-119">XEvent `hekaton_slow_parameter_passing`에 `reason=named_parameters`을 사용하면 고유하게 컴파일된 저장 프로시저에 비효율적인 명명된 매개 변수가 사용되었는지 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-119">Use of (inefficient) named parameters with natively compiled stored procedures can be detected through the XEvent `hekaton_slow_parameter_passing`, with `reason=named_parameters`.</span></span>  
  
 <span data-ttu-id="a9b43-120">마찬가지로 동일한 XEvent `hekaton_slow_parameter_passing`에 `reason=parameter_conversion`을 사용하여 일치하지 않는 형식의 사용을 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-120">Similarly, you can detect use of mismatched types through the same XEvent `hekaton_slow_parameter_passing`, with `reason=parameter_conversion`.</span></span>  
  
 <span data-ttu-id="a9b43-121">메모리 최적화 테이블을 사용할 때 많은 시나리오에서 재시도 논리를 구현해야 하며 몇 가지 기능 제한에 대한 문제를 해결해야 하기 때문에 래퍼에서 해석된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저를 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9b43-121">Because you will need to implement retry logic when using memory-optimized tables (in many scenarios), and because you will need to work around certain feature limitations, you may want to create a wrapper interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.</span></span> <span data-ttu-id="a9b43-122">예를 보려면 [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](memory-optimized-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9b43-122">For an example, see [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b43-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9b43-123">See Also</span></span>  
 [<span data-ttu-id="a9b43-124">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="a9b43-124">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
