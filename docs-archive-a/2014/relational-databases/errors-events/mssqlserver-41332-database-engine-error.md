---
title: MSSQLSERVER_41332 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72a87838673f07f7a40596517ab54533d944e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652872"
---
# <a name="mssqlserver_41332"></a><span data-ttu-id="47ac3-102">MSSQLSERVER_41332</span><span class="sxs-lookup"><span data-stu-id="47ac3-102">MSSQLSERVER_41332</span></span>
    
## <a name="details"></a><span data-ttu-id="47ac3-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="47ac3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47ac3-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="47ac3-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="47ac3-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="47ac3-105">Event ID</span></span>|<span data-ttu-id="47ac3-106">41332</span><span class="sxs-lookup"><span data-stu-id="47ac3-106">41332</span></span>|  
|<span data-ttu-id="47ac3-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="47ac3-107">Event Source</span></span>|<span data-ttu-id="47ac3-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="47ac3-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="47ac3-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="47ac3-109">Component</span></span>|<span data-ttu-id="47ac3-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="47ac3-110">SQLEngine</span></span>|  
|<span data-ttu-id="47ac3-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="47ac3-111">Symbolic Name</span></span>|<span data-ttu-id="47ac3-112">SQL_SNAPSHOT_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="47ac3-112">SQL_SNAPSHOT_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="47ac3-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="47ac3-113">Message Text</span></span>|<span data-ttu-id="47ac3-114">TRANSACTION ISOLATION LEVEL 세션을 SNAPSHOT으로 설정하면 메모리 액세스에 최적화된 테이블과 고유하게 컴파일된 저장 프로시저에 액세스하거나 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47ac3-114">Memory optimized tables and natively compiled stored procedures cannot be accessed or created when the session TRANSACTION ISOLATION LEVEL is set to SNAPSHOT.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="47ac3-115">설명</span><span class="sxs-lookup"><span data-stu-id="47ac3-115">Explanation</span></span>  
 <span data-ttu-id="47ac3-116">트랜잭션이 스냅샷 격리 수준에서 시작된 다음 호환되지 않는 기능을 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="47ac3-116">The transaction was started in snapshot isolation level and then attempted to use an incompatible feature.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="47ac3-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="47ac3-117">User Action</span></span>  
 <span data-ttu-id="47ac3-118">다른 격리 수준으로 트랜잭션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47ac3-118">Start the transaction with a different isolation level.</span></span> <span data-ttu-id="47ac3-119">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47ac3-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ac3-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47ac3-120">See Also</span></span>  
 [<span data-ttu-id="47ac3-121">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="47ac3-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
