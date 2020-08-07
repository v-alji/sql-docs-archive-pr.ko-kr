---
title: MSSQLSERVER_41325 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a512d7db6529876259d889d04aabf3d07747cafe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732692"
---
# <a name="mssqlserver_41325"></a><span data-ttu-id="7d449-102">MSSQLSERVER_41325</span><span class="sxs-lookup"><span data-stu-id="7d449-102">MSSQLSERVER_41325</span></span>
    
## <a name="details"></a><span data-ttu-id="7d449-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7d449-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d449-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7d449-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="7d449-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7d449-105">Event ID</span></span>|<span data-ttu-id="7d449-106">41325</span><span class="sxs-lookup"><span data-stu-id="7d449-106">41325</span></span>|  
|<span data-ttu-id="7d449-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7d449-107">Event Source</span></span>|<span data-ttu-id="7d449-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7d449-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7d449-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7d449-109">Component</span></span>|<span data-ttu-id="7d449-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7d449-110">SQLEngine</span></span>|  
|<span data-ttu-id="7d449-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7d449-111">Symbolic Name</span></span>|<span data-ttu-id="7d449-112">HK_TX_COMMIT_SR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="7d449-112">HK_TX_COMMIT_SR_VALIDATION</span></span>|  
|<span data-ttu-id="7d449-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7d449-113">Message Text</span></span>|<span data-ttu-id="7d449-114">직렬화 유효성 검사 실패로 인해 현재 트랜잭션을 커밋하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7d449-114">The current transaction failed to commit due to a serializable validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7d449-115">설명</span><span class="sxs-lookup"><span data-stu-id="7d449-115">Explanation</span></span>  
 <span data-ttu-id="7d449-116">유효성 검사 오류가 발생하여 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7d449-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7d449-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7d449-117">User Action</span></span>  
 <span data-ttu-id="7d449-118">실패한 트랜잭션을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="7d449-118">Retry the failed transaction.</span></span> <span data-ttu-id="7d449-119">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d449-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d449-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d449-120">See Also</span></span>  
 [<span data-ttu-id="7d449-121">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="7d449-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
