---
title: MSSQLSERVER_41333 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ba3cfc9627b4b44c3c9eccc620fb16bb94b861b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732695"
---
# <a name="mssqlserver_41333"></a><span data-ttu-id="d7b1b-102">MSSQLSERVER_41333</span><span class="sxs-lookup"><span data-stu-id="d7b1b-102">MSSQLSERVER_41333</span></span>
    
## <a name="details"></a><span data-ttu-id="d7b1b-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d7b1b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7b1b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d7b1b-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d7b1b-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d7b1b-105">Event ID</span></span>|<span data-ttu-id="d7b1b-106">41333</span><span class="sxs-lookup"><span data-stu-id="d7b1b-106">41333</span></span>|  
|<span data-ttu-id="d7b1b-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d7b1b-107">Event Source</span></span>|<span data-ttu-id="d7b1b-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7b1b-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7b1b-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d7b1b-109">Component</span></span>|<span data-ttu-id="d7b1b-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7b1b-110">SQLEngine</span></span>|  
|<span data-ttu-id="d7b1b-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d7b1b-111">Symbolic Name</span></span>|<span data-ttu-id="d7b1b-112">CROSS_CONTAINER_ISOLATION_FAILURE</span><span class="sxs-lookup"><span data-stu-id="d7b1b-112">CROSS_CONTAINER_ISOLATION_FAILURE</span></span>|  
|<span data-ttu-id="d7b1b-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d7b1b-113">Message Text</span></span>|<span data-ttu-id="d7b1b-114">다음 트랜잭션은 스냅샷 격리에서 메모리 액세스에 최적화된 테이블과 고유하게 컴파일된 저장 프로시저에 액세스해야 합니다. RepeatableRead 트랜잭션, 직렬화 가능 트랜잭션, RepeatableRead 또는 직렬화 가능 격리에서 메모리 액세스에 최적화되지 않은 테이블에 액세스하는 트랜잭션.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-114">The following transactions must access memory optimized tables and natively compiled stored procedures under snapshot isolation: RepeatableRead transactions, Serializable transactions, and transactions that access tables that are not memory optimized in RepeatableRead or Serializable isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7b1b-115">설명</span><span class="sxs-lookup"><span data-stu-id="d7b1b-115">Explanation</span></span>  
 <span data-ttu-id="d7b1b-116">디스크 기반 트랜잭션과 XTP 트랜잭션 간에는 높은 격리 수준의 사용자에 대한 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-116">There are restrictions against the user of the higher isolation levels between disk based transactions and XTP transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7b1b-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d7b1b-117">User Action</span></span>  
 <span data-ttu-id="d7b1b-118">메모리 최적화 테이블(및 고유하게 컴파일된 프로시저) 및 디스크 기반 테이블에서는 높은 수준의 격리 작업을 시도하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-118">Don't attempt high level isolation operations on memory-optimized tables (and natively compiled procedures) and disk based tables.</span></span>  
  
 <span data-ttu-id="d7b1b-119">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b1b-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7b1b-120">See Also</span></span>  
 [<span data-ttu-id="d7b1b-121">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="d7b1b-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
