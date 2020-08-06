---
title: MSSQLSERVER_41359 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cf45a117dcda0827672c6072c603a1fc0866a33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659974"
---
# <a name="mssqlserver_41359"></a><span data-ttu-id="1eacf-102">MSSQLSERVER_41359</span><span class="sxs-lookup"><span data-stu-id="1eacf-102">MSSQLSERVER_41359</span></span>
    
## <a name="details"></a><span data-ttu-id="1eacf-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1eacf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1eacf-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1eacf-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="1eacf-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1eacf-105">Event ID</span></span>|<span data-ttu-id="1eacf-106">41359</span><span class="sxs-lookup"><span data-stu-id="1eacf-106">41359</span></span>|  
|<span data-ttu-id="1eacf-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1eacf-107">Event Source</span></span>|<span data-ttu-id="1eacf-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1eacf-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1eacf-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1eacf-109">Component</span></span>|<span data-ttu-id="1eacf-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1eacf-110">SQLEngine</span></span>|  
|<span data-ttu-id="1eacf-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1eacf-111">Symbolic Name</span></span>|<span data-ttu-id="1eacf-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="1eacf-112">SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="1eacf-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1eacf-113">Message Text</span></span>|<span data-ttu-id="1eacf-114">데이터베이스 옵션 READ_COMMITTED_SNAPSHOT이 ON으로 설정된 경우 READ COMMITTED 격리 수준을 사용하여 메모리 액세스에 최적화된 테이블에 액세스하는 쿼리가 디스크 기반 테이블에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1eacf-114">A query that accesses memory optimized tables using the READ COMMITTED isolation level, cannot access disk based tables when the database option READ_COMMITTED_SNAPSHOT is set to ON.</span></span> <span data-ttu-id="1eacf-115">WITH (SNAPSHOT) 같은 테이블 힌트를 사용하여 메모리 액세스에 최적화된 테이블에 대해 지원되는 격리 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1eacf-115">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1eacf-116">설명</span><span class="sxs-lookup"><span data-stu-id="1eacf-116">Explanation</span></span>  
 <span data-ttu-id="1eacf-117">READ_COMMITTED_SNAPSHOT이 ON으로 설정된 데이터베이스는 메모리 최적화 테이블과 디스크 기반 테이블에 모두 액세스하는 트랜잭션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1eacf-117">The database with READ_COMMITTED_SNAPSHOT=ON does not support the transactions that access both memory-optimized tables and disk based tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1eacf-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1eacf-118">User Action</span></span>  
 <span data-ttu-id="1eacf-119">READ_COMMITTED_SNAPSHOT을 OFF로 설정하거나 WITH (SNAPSHOT) 같은 테이블 수준 힌트를 사용하여 메모리 최적화 테이블에 대해 지원되는 격리 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1eacf-119">Set READ_COMMITTED_SNAPSHOT to OFF or supply a supported isolation level for the memory-optimized table using a table-level hint, such as WITH (SNAPSHOT).</span></span> <span data-ttu-id="1eacf-120">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1eacf-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eacf-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1eacf-121">See Also</span></span>  
 [<span data-ttu-id="1eacf-122">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="1eacf-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
